# XRPL Secure Self Check-in (Hackathon Project)

🏆 **3rd Place Winner** at Italian XRPL Hackathon 2024 (Prize: 500€)  

A proof-of-concept decentralized self check-in system built on the XRPL (XRP Ledger) during the Italian XRPL Hackathon 2024. Developed by the University of Trento team, where I served as Team Leader, this project demonstrates how XRPL's native features like digital signatures and NFTs can be used for secure authentication and access control. 

## Problem Statement

The goal is to replace fragile one time code, key boxes, NFC cards, QR-based check-in systems with cryptographically verifiable, tamper-proof authentication using blockchain-native tools. 

## Features

- **Secure Authentication**: Utilizes XRPL's cryptographic functions for secure message signing
- **NFT-based Access Control**: Uses XRPL NFTs to manage and verify access rights
- **Decentralized Verification**: No central authority required for verification
- **Time-bound Access**: Supports time-limited access through NFT metadata
- **Service-specific Authorization**: Fine-grained access control for different services

## Prerequisites

- Python 3.7+
- Basic understanding of XRPL and blockchain concepts
- XRPL Testnet/Devnet account (there are hardcoded credentials in the demo for the sake of simplicity)

### Installation

1. Clone this repository
2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

### Components
- **`app.py`**: Client-side application that handles user authentication and interaction with the XRPL.
  - `Application` class manages the user's wallet and authentication process
  - Handles cryptographic signing of authentication requests
  - Manages local wallet and keypair for secure message signing

- **`verifier.py`**: Server-side verification logic for access control.
  - `Verifier` class validates NFT ownership and access rights
  - Implements time-based verification to prevent replay attacks
  - Validates cryptographic signatures and service-specific permissions
  - Checks NFT metadata for access rules and validity periods

- **`interaction.py`**: XRPL interaction utilities and helper functions.
  - Manages XRPL account operations
  - Handles NFT operations (nft mint, nft send, query nft held by an account, nft accept offer)
  - Implements secure transaction submission and status checking

- **`server.py`**: Server implementation for guest registration and NFT issuance.
  - `Server` class manages guest registration and NFT creation
  - Handles the initial setup of access credentials
  - Manages the relationship between guests and their access tokens

### Demo
- **`demo.py`**: Interactive demo application with GUI.
  - Provides a user-friendly interface to demonstrate the system
  - Shows registration, authentication, and service access flows
  - Includes test scenarios for different access control cases
- **`self_check-in.pdf`**: Presentation done during the hackathon.

### Configuration and Dependencies
- **`requirements.txt`**: Lists all Python package dependencies
- **`.env`**: Environment configuration, in the demo these are hardcoded for the sake of simplicity, in a production environment these should be stored in a secure environment variable, like:
  - `RIPPLE_URL`: XRPL network endpoint (defaults to testnet)
  - `HOST_SEED`: Seed phrase for the host/organization wallet

### Acknowledgments
- My team
- Organizers: XRPL Commons, De Componendis Cifris, Roma Tre University

## Note
This is a hackathon project created within 18 hours marathon for the competition, and is intended for demonstration purposes only. It has not undergone security audits and should not be used in production environments without significant review and modification.
