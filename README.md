# Foundry NFT Project

A comprehensive NFT project built with Foundry, featuring two distinct NFT implementations: a basic NFT with IPFS integration and an advanced dynamic mood-based NFT with on-chain SVG storage.

## Table of Contents

- [About](#about)
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Smart Contracts](#smart-contracts)
- [Testing](#testing)
- [Deployment](#deployment)
- [Technologies](#technologies)

## About

This project demonstrates two different approaches to NFT development on Ethereum:

1. **BasicNft**: A simple ERC721 implementation with IPFS metadata storage
2. **MoodNft**: A dynamic NFT that stores SVG images on-chain and allows owners to flip between happy and sad moods

## Features

- Two NFT contract implementations (Basic & Mood)
- Complete deployment scripts for both contracts
- Comprehensive unit and integration tests
- On-chain SVG storage for MoodNft
- Dynamic NFT metadata generation
- IPFS integration for BasicNft
- Deployed to Sepolia testnet
- Makefile for easy command execution

## Prerequisites

- [Foundry](https://book.getfoundry.sh/getting-started/installation)
- [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
- [Make](https://www.gnu.org/software/make/) (optional, for using Makefile commands)

## Installation

1. Clone the repository:
```bash
git clone https://github.com/GN25/Foundry-NFT.git
cd Foundry-NFT
```

2. Install dependencies:
```bash
forge install
```

3. Build the project:
```bash
forge build
```

## Usage

### Build

```bash
forge build
```

### Test

Run all tests:
```bash
forge test
```

Run tests with verbosity:
```bash
forge test -vvv
```

### Test Coverage

```bash
forge coverage
```

### Format Code

```bash
forge fmt
```

### Gas Snapshots

```bash
forge snapshot
```

### Start Local Node

```bash
anvil
```

## Smart Contracts

### BasicNft

A straightforward ERC721 implementation with the following features:
- Mint NFTs with custom token URIs
- Token metadata stored on IPFS
- Simple and gas-efficient

**Key Functions:**
- `mintNft(string memory tokenUri)`: Mint a new NFT with a specified token URI

### MoodNft

An advanced dynamic NFT with on-chain storage:
- Stores SVG images directly on the blockchain
- Owners can flip between HAPPY and SAD moods
- Base64-encoded metadata
- Fully decentralized (no IPFS dependency)

**Key Functions:**
- `mintNft()`: Mint a new Mood NFT (starts as HAPPY)
- `flipmod(uint256 tokenId)`: Toggle between HAPPY and SAD mood (owner only)
- `tokenURI(uint256 tokenId)`: Returns Base64-encoded JSON metadata with SVG image

## Testing

The project includes comprehensive tests:

- **Unit Tests**: Located in `test/unit/`
  - `DeployMoodNftTest.t.sol`: Tests for MoodNft deployment
  - `MoodNftTest.t.sol`: Tests for MoodNft functionality

- **Integration Tests**: Located in `test/integrations/`
  - `BastcNftTest.t.sol`: Integration tests for BasicNft
  - `MoodNftIntegrationTest.t.sol`: Integration tests for MoodNft

Run specific test files:
```bash
forge test --match-path test/unit/MoodNftTest.t.sol
```

## Deployment

### Deploy BasicNft

To local node:
```bash
forge script script/DeployBasicNft.s.sol --rpc-url http://localhost:8545 --broadcast
```

To Sepolia testnet:
```bash
forge script script/DeployBasicNft.s.sol --rpc-url $SEPOLIA_RPC_URL --private-key $PRIVATE_KEY --broadcast --verify
```

### Deploy MoodNft

To local node:
```bash
forge script script/DeployMoodNft.s.sol --rpc-url http://localhost:8545 --broadcast
```

To Sepolia testnet:
```bash
forge script script/DeployMoodNft.s.sol --rpc-url $SEPOLIA_RPC_URL --private-key $PRIVATE_KEY --broadcast --verify
```

### Environment Variables

Create a `.env` file in the root directory:
```
SEPOLIA_RPC_URL=your_sepolia_rpc_url
PRIVATE_KEY=your_private_key
ETHERSCAN_API_KEY=your_etherscan_api_key
```

## Technologies

- **Foundry**: Ethereum development toolkit used for building, testing, and deploying
- **Solidity**: Smart contract programming language (^0.8.19)
- **OpenZeppelin**: Industry-standard smart contract libraries
  - ERC721 implementation
  - Base64 encoding utilities
- **Foundry DevOps**: Utilities for Foundry deployments
- **SVG**: On-chain image storage for MoodNft

## Project Structure

```
foundry-nft/
├── src/
│   ├── BasicNft.sol         # Simple NFT with IPFS
│   └── MoodNft.sol          # Dynamic mood NFT with on-chain SVGs
├── script/
│   ├── DeployBasicNft.s.sol # BasicNft deployment script
│   ├── DeployMoodNft.s.sol  # MoodNft deployment script
│   └── Interactions.s.sol   # Interaction scripts
├── test/
│   ├── unit/                # Unit tests
│   └── integrations/        # Integration tests
├── img/                     # SVG images for MoodNft
├── lib/                     # Dependencies
└── foundry.toml            # Foundry configuration
```

## License

This project is licensed under the MIT License.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Contact

For questions or feedback, please open an issue on GitHub.

---

Built with [Foundry](https://book.getfoundry.sh/)
