# Intro

## Overview

W3 Registrar is a specialized software system designed for blockchain identity
registrars who need to verify and validate user identities across multiple
platforms. It provides an automated solution for managing identity verification
requests, handling cross-platform validation, and issuing blockchain-based
identity judgements.

## Purpose

The primary purpose of W3 Registrar is to streamline the identity verification
process for blockchain networks, particularly focusing on:

- Automated verification of user identities across multiple platforms (Discord, Twitter, Matrix, etc.)
- Management of verification challenges and responses
- Integration with blockchain networks for identity judgement issuance
- Real-time status tracking of verification processes
- Secure storage and handling of verification data

## Who Should Use This?

This software is specifically designed for:

### Primary Users: Identity Registrars
- Blockchain network registrars who need to verify user identities
- Organizations providing identity verification services
- Entities responsible for issuing identity judgements on blockchain networks

## Core Features

### 1. Multi-Platform Verification
- Supports verification across multiple platforms:
  - Discord
  - Twitter
  - Matrix
  - Email
  - Display names
  - Legal identities(out of scope)
  - Web presence(tbd)
  - GitHub accounts(tbd)
  - PGP keys(tbd)

### 2. Automated Challenge-Response System
- Generates unique verification challenges
- Handles automated response validation
- Manages verification status tracking

### 3. Blockchain Integration
- Direct integration with substrate-based blockchain networks
- Automated judgement issuance
- Support for multiple verification states (Pending, Done)

### 4. Real-Time Communication
- WebSocket-based real-time status updates
- Matrix bot integration for automated verification
- Redis-based state management

### 5. Security Features
- Secure token generation and validation
- Encrypted storage of verification data
- State persistence and recovery mechanisms

## Technical Architecture

The system consists of several key components:

1. **WebSocket Server**: Handles real-time communication with clients
2. **Matrix Bot**: Manages automated verification through Matrix
3. **Node Listener**: Monitors blockchain events and handles registration requests
4. **Redis Backend**: Manages state and verification data
5. **Blockchain Interface**: Handles interaction with the substrate network

## Benefits

### For Registrars:
- Reduced manual verification workload
- Automated cross-platform validation
- Streamlined verification workflow
- Real-time status monitoring
- Secure and compliant verification process

### For the Network:
- Improved identity verification reliability
- Faster verification processing
- Reduced verification errors
- Enhanced security and trust
