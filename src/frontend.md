# Frontend

Frontend application for managing identity operations on polkadot-sdk chains.
The application enables users to submit `setIdentity` and `requestJudgement` operations using polkadot-api.

## Features

- Identity registration on polkadot-sdk chains
- Integration with W3 Registrar backend
- Real-time verification status updates
- Support for multiple social account verifications

## Development Setup

### Prerequisites

Install required versions to ensure compatibility:

```sh
# Install Bun 1.1.35
curl -fsSL https://bun.sh/install | bash -s "bun-v1.1.35"

# Install NVM and Node 22
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.0/install.sh | bash
nvm install 22
```

### Installation

1. Clone the repository:
```sh
git clone https://github.com/rotkoneworks/w3registrar-www
cd w3registrar-www
```

2. Install dependencies:
```sh
bun install
```

3. Set up environment:
```sh
cp .env.example .env
# Edit .env with your endpoints
```

4. Update scale metadata:
```sh
bunx polkadot-api@1.8.0 update
# or
bun metadata
```

### Development Server

Start the development server:
```sh
bun dev
```
Visit http://localhost:3333 in your browser. The server will automatically reload on file changes.

## Building

Create production build:
```sh
bun build
```

## Chain Documentation

- Access documentation at [docs link]
- Generate fresh documentation:
  ```sh
  bunx papi-generate-docs --config .papi/polkadot-api.json --output docs/
  ```

## Environment Configuration

Copy `.env.example` to `.env` and configure the following variables:

```env
# WalletConnect Project ID
VITE_APP_WALLET_CONNECT_PROJECT_ID=rotko-w3-registrar

# Chain WebSocket Endpoints
VITE_APP_DEFAULT_WS_URL=wss://dev.rotko.net/people-rococo
VITE_APP_DEFAULT_WS_URL_RELAY=wss://dev.rotko.net/rococo

# Registrar Indices for Different Networks
VITE_APP_REGISTRAR_INDEX__PEOPLE_POLKADOT=19
VITE_APP_REGISTRAR_INDEX__PEOPLE_KUSAMA=17
VITE_APP_REGISTRAR_INDEX__PEOPLE_WESTEND=18
VITE_APP_REGISTRAR_INDEX__PEOPLE_PASEO=16
VITE_APP_REGISTRAR_INDEX__PEOPLE_ROCOCO=0

# API Configuration
VITE_APP_CHALLENGES_API_URL=wss://dev.rotko.net/api

# Chain Configuration
VITE_APP_AVAILABLE_CHAINS=polkadot_people,ksmcc3_people,paseo_people,rococo_people
VITE_APP_DEFAULT_CHAIN=rococo_people  # Optional
```

## Available Scripts

- `bun dev`: Start development server
- `bun build`: Create production build
- `bun metadata`: Update scale metadata
- `bun docs`: Generate chain documentation

## Integration with Backend

The frontend expects a W3 Registrar backend instance running. Configure the WebSocket endpoint in your `.env` file:
```env
VITE_BACKEND_URL="wss://your-backend:8080"
```
