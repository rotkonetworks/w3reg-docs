# FAQ

## Q: Why are we facing `M_UNKNOWN` error 500 from the Matrix Synapse server?

### Error Details
```
2025-01-11T03:47:38.385306Z ERROR w3registrar::matrix: 178: can't sync duo to Http(
    Api(
        Server(
            ClientApi(
                Error {
                    status_code: 500,
                    body: Standard {
                        kind: Unknown,
                        message: "synapse sync failed with status 400 Bad Request: internal error generating sync response",
                    },
                },
            ),
        ),
    ),
)
```

### Answer
This error can occur if your account has exceeded the usual limit of **20 active
Device IDs**. When this happens, the server may fail to handle `/sync` requests
due to the overhead of managing too many devices.

### How to Check for Too Many Devices
Use the following `curl` command to list all Device IDs associated with your account:

```bash
curl -v "https://matrix.beeper.com/_matrix/client/v3/devices" \
-H "Authorization: Bearer <your_access_token>"
```

Example response:

```json
{
  "devices": [
    {"device_id": "AEQJNOWHXG", "display_name": "Beeper Desktop (Linux)", "last_seen_ip": "", "last_seen_ts": 1730201177000},
    {"device_id": "BGKCFSZTRN", "display_name": "Beeper Desktop (Linux)", "last_seen_ip": "", "last_seen_ts": 1733668251000},
    {"device_id": "BVKAPCXANW", "display_name": "w3r", "last_seen_ip": "", "last_seen_ts": 1736377586000},
    ...
  ]
}
```

### Solution: Remove Unnecessary Devices
Identify and remove devices that are no longer in use. Focus on devices with:
- A `last_seen_ts` of `0` or very old timestamps.
- Duplicate or generic display names.

#### Example Cleanup
To remove specific devices, use the `/delete_devices` endpoint:

```bash
curl -X POST "https://matrix.beeper.com/_matrix/client/v3/delete_devices" \
-H "Authorization: Bearer <your_access_token>" \
-H "Content-Type: application/json" \
-d '{
  "devices": ["FJHQEVOVOD", "KSQHECIAAA", "KZIRBZPAHB"]
}'
```

If required, include authentication:

```bash
curl -X POST "https://matrix.beeper.com/_matrix/client/v3/delete_devices" \
-H "Authorization: Bearer <your_access_token>" \
-H "Content-Type: application/json" \
-d '{
  "devices": ["FJHQEVOVOD", "KSQHECIAAA", "KZIRBZPAHB"],
  "auth": {
    "type": "m.login.password",
    "user": "@w3r:beeper.com",
    "password": "your_password"
  }
}'
```

### Verify Cleanup
After removing devices, verify the remaining devices:

```bash
curl -v "https://matrix.beeper.com/_matrix/client/v3/devices" \
-H "Authorization: Bearer <your_access_token>"
```

### Prevent Future Issues
1. **Reuse Existing Tokens**: Avoid logging into the same account unnecessarily.
2. **Logout Unused Sessions**: Regularly clean up old sessions.
3. **Monitor Active Devices**: Periodically review the list of active devices to ensure it stays manageable.

By keeping the number of active Device IDs below the limit, you can avoid these
errors and ensure smoother synchronization with the Matrix server.
