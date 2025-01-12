# Redis

We use Redis as a cache to maintain application statelessness in our Kubernetes
setup. This allows us to scale horizontally while keeping track of ongoing
verification challenges. If Redis data is lost, users simply need to restart
their verification challenges.

## Architecture Overview

The application uses Redis to temporarily store verification states and
challenge tokens. This eliminates the need for local state management in
application instances, making them stateless and easily scalable.

## Data Structure

We use hash maps (HSET/HGETALL) with composite keys to store verification states
and challenge data.

### Key Structure

- Main verification state: `{network}:{account_address}`
- Media-specific state: `{network}:{account_address}:{media_type}`

### Main Verification State

```redis
HGETALL "polkadot:5GrwvaEF5zXb26Fz9rcQpDWS57CtERHpNehXCPcNoHGKutQY"
```

Fields:
- `status`: Overall verification status (Done/Pending)
- `created_at`: Timestamp when verification process started
- `updated_at`: Timestamp of last status change
- `media_types`: Comma-separated list of media accounts being verified

Example:
```redis
{
    "status": "Pending",
    "created_at": "2024-01-11T22:25:36",
    "updated_at": "2024-01-11T22:26:36",
    "media_types": "discord,twitter,matrix"
}
```

### Media-Specific State

```redis
HGETALL "polkadot:5GrwvaEF5zXb26Fz9rcQpDWS57CtERHpNehXCPcNoHGKutQY:discord"
```

Fields:
- `name`: Username on the platform
- `status`: Verification status for this specific media
- `token`: Verification token

Example:
```redis
{
    "name": "patchwinner",
    "status": "Pending",
    "token": "Q8KGYC7P"
}
```

## Examples

### Storing New Verification State

```python
# Create main verification state
redis_client.hmset(f"{network}:{address}", {
    "status": "Pending",
    "created_at": datetime.utcnow().isoformat(),
    "updated_at": datetime.utcnow().isoformat(),
    "media_types": ",".join(media_types)
})

# Create media-specific state
redis_client.hmset(f"{network}:{address}:discord", {
    "name": username,
    "status": "Pending",
    "token": generate_token()
})
```

### Retrieving Verification State

```python
# Get main verification state
state = redis_client.hgetall(f"{network}:{address}")

# Get media-specific state
discord_state = redis_client.hgetall(f"{network}:{address}:discord")
```
