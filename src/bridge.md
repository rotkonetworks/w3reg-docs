# Setting Up Bridges via Matrix

This guide explains how to set up messaging bridges to connect different adapters through Matrix.

## Quick Setup with Beeper (Easies)t

The easiest way to set up bridges is using Beeper's client, which includes built-in bridge functionality
and is hosted by Beeper. Even bridge is not self-hosted, all messages are e2ee,
so messaging data on the server side is encrypted.

### Initial Setup

1. Create an account at [beeper.com](https://beeper.com)
2. After registration, you'll receive a secret key - make sure to save this securely
3. Log in to [app.element.io](https://app.element.io) using your Beeper account
4. Set up a password for your account (required for bridging):
   - Use Element web client to set/reset your account password
   - Store this password securely - you'll need it for bridge connections

### Bridge Configuration

#### Discord Bridge
1. Connect your Discord account through Beeper
2. Important Discord-specific steps:
   - Ensure you're in the same channels as people who need to message you
   - Configure your Discord privacy settings to allow direct messages 

#### Twitter Bridge
1. Connect your Discord account through Beeper
2. Important Discord-specific steps:
   - Ensure you're in the same channels as people who need to message you
   - Configure your Discord privacy settings to allow direct messages 

## Advanced Self-Hosting Options

For registrars interested in self-hosting, these options are available:

* Setting up your own [Synapse server](https://github.com/element-hq/synapse) with [mau.fi bridges](https://docs.mau.fi/bridges/)

* Using [beeper/bridge-manager](https://github.com/beeper/bridge-manager) with your own [Matrix](https://matrix.org/) [Synapse](https://github.com/element-hq/synapse) server

Both options require:

* Setting up and maintaining your own [Matrix](https://matrix.org/) [Synapse](https://github.com/element-hq/synapse) server

* More technical expertise in [Matrix](https://spec.matrix.org/latest/server-server-api/) server administration
