# W3Registrar Setup Guide

## Prerequisites
- Redis server (not needed for Docker setup)
- `config.toml` (copy from `config.example.toml`)
- Matrix account credentials

## 1. Docker Setup

1. Create configuration:
```bash
cp config.example.toml config.toml
# Edit config.toml with your settings
# Important: use "redis" as host in [redis] section
```

2. Run services:
```bash
docker compose up -d
```

## 2. Binary Installation

1. Create service user:
```bash
sudo useradd -r -s /bin/false w3r
sudo mkdir -p /etc/w3registrar
sudo chown -R w3r:w3r /etc/w3registrar
```

2. Install binary:
```bash
# Download from releases page
sudo cp w3registrar-* /usr/local/bin/w3registrar
sudo chown w3r:w3r /usr/local/bin/w3registrar
sudo chmod 755 /usr/local/bin/w3registrar
```

3. Configure:
```bash
sudo cp config.toml /etc/w3registrar/
sudo chown w3r:w3r /etc/w3registrar/config.toml
sudo chmod 600 /etc/w3registrar/config.toml
```

4. Create systemd service:
```bash
sudo tee /etc/systemd/system/w3registrar.service << EOF
[Unit]
Description=W3 Registrar Service
After=network.target redis.service

[Service]
Type=simple
User=w3r
Group=w3r
ExecStart=/usr/local/bin/w3registrar
Restart=on-failure
Environment=RUST_LOG=info

[Install]
WantedBy=multi-user.target
EOF

sudo systemctl enable --now w3registrar
```

## 3. Building from Source

```bash
# Install dependencies
sudo apt install -y build-essential pkg-config libssl-dev git

# Build
git clone https://github.com/your-repo/w3registrar.git
cd w3registrar
cargo build --release

# Follow binary installation steps 1-4 above
```

## Configuration Example

```toml
[watcher]
endpoint = "wss://dev.rotko.net/people-rococo/"
registrar_index = 0
keystore_path = "./keyfile"

[websocket]
host = "127.0.0.1"
port = 8080

[redis]
host = "redis"  # Use "redis" for Docker, "127.0.0.1" otherwise
port = 6379

[matrix]
homeserver = "https://matrix.org"
username = "regbot"
password = "your-password"
security_key = "your-security-key"
admins = ["@admin:matrix.org"]
```

## Common Issues

- **Redis Connection**: Check if Redis is running and host configuration
- **Matrix Login**: Verify credentials and security key
- **Permissions**: Ensure proper file ownership and permissions under w3r user
