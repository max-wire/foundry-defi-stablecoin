# 🪙 Decentralized Stablecoin (DSC)

This project is a decentralized, overcollateralized stablecoin system built with Solidity and Foundry.

It is inspired by DeFi lending protocols and demonstrates how to mint a USD-pegged stablecoin using crypto collateral such as WETH and WBTC.

## Overview

## The DSC (Decentralized Stablecoin) system allows users to:

Deposit collateral (WETH / WBTC)
Mint a USD-pegged stablecoin (DSC)
Maintain overcollateralization to ensure system stability
Redeem collateral by burning DSC

## The system is designed to be:

Fully decentralized
Algorithmically collateralized
Liquidation-aware (based on health factor logic)

## Architecture

### Core components:

DSCEngine.sol → Main protocol logic (minting, collateral, liquidation)
DecentralizedStableCoin.sol → ERC20 stablecoin implementation
Oracle (price feeds) → Determines collateral value in USD
Collateral system → WETH, WBTC support

## Getting Started
### Requirements

Make sure you have installed:

git → git --version
Foundry → forge --version

Install Foundry:

```javascript
    curl -L https://foundry.paradigm.xyz | bash
    foundryup
```

## Quickstart

Clone the repo:

```javascript
    git clone https://github.com/max-wire/decentralized-stablecoin
    cd decentralized-stablecoin
    forge build
```

## Testing

This project includes:

Unit tests
Fuzz tests
Integration tests

Run tests:

```javascript
    forge test
```

Run with gas reporting:

```javascript
    forge test --gas-report
```

Check coverage:

```javascript
    forge coverage
```    

## Local Development

Start a local blockchain:

```javascript
    anvil
```    

Deploy contracts:

```javascript
    make deploy
```    

## Deployment (Testnet / Mainnet)
Environment Setup

Create a .env file:

```javascript
PRIVATE_KEY=your_private_key_here
SEPOLIA_RPC_URL=https://sepolia.infura.io/v3/your_key
ETHERSCAN_API_KEY=your_key
```

⚠️ Never use a wallet with real funds for development.

Deploy to Sepolia
```javascript
    make deploy ARGS="--network sepolia"
```

## Interacting with the Protocol
Deposit WETH
```javascript
    cast send <WETH_ADDRESS> "deposit()" --value 0.1ether --rpc-url $SEPOLIA_RPC_URL --private-key $PRIVATE_KEY
```    

Approve Collateral
```javascript
    cast send <WETH_ADDRESS> "approve(address,uint256)" <DSC_ENGINE_ADDRESS> 1000000000000000000 --rpc-url $SEPOLIA_RPC_URL --private-key $PRIVATE_KEY
```

Mint DSC
```javascript
    cast send <DSC_ENGINE_ADDRESS> "depositCollateralAndMintDsc(address,uint256,uint256)" \<WETH_ADDRESS> 100000000000000000 10000000000000000 --rpc-url $SEPOLIA_RPC_URL --private-key $PRIVATE_KEY
```

## Gas Analysis

Estimate gas usage:

```javascript
    forge snapshot
```    

Output:

```javascript
    .gas-snapshot
```    

## Code Formatting

Format Solidity code:

```javascript
    forge fmt
```

## Security Notes

This protocol includes:

Overcollateralization checks
Health factor enforcement
Liquidation mechanisms (if implemented)
Price feed dependency (Chainlink-style oracles)

⚠️ This is an educational DeFi system and not audited for production use.

### Key Concepts Demonstrated
Collateralized debt positions (CDPs)
Stablecoin mint/burn mechanics
Liquidation logic
Oracle-based pricing
DeFi risk management

### Future Improvements
Add liquidation bots
Add interest rate model
Multi-collateral expansion
Governance module (DAO control)
Cross-chain collateral support

### Built With
Solidity
Foundry
OpenZeppelin Contracts
Chainlink Price Feeds (or mock equivalents)

### Acknowledgements
Inspired by the Cyfrin Foundry DeFi Stablecoin course and real-world DeFi protocols like MakerDAO.