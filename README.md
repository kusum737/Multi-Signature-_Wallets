# Multi-Signature Wallet 🔐

A secure and simple multi-signature wallet implementation in Solidity that requires multiple confirmations for transactions.

![Solidity](https://img.shields.io/badge/Solidity-^0.8.19-363636?style=flat-square&logo=solidity)
![Hardhat](https://img.shields.io/badge/Hardhat-2.14.0-yellow?style=flat-square&logo=ethereum)
![License](https://img.shields.io/badge/License-MIT-blue?style=flat-square)

## 🌟 Features

- **Multi-Owner Security**: 3 hardcoded owners with 2-of-3 confirmation requirement
- **Zero Input Deployment**: Deploy instantly without any constructor parameters
- **Transaction Management**: Submit, confirm, execute, and revoke transactions
- **ETH & Token Support**: Handle both ETH transfers and smart contract interactions
- **Event Logging**: Comprehensive event emission for transparency
- **Gas Optimized**: Efficient storage and execution patterns

## 📋 Table of Contents

- [Quick Start](#-quick-start)
- [Installation](#-installation)
- [Usage](#-usage)
- [Smart Contract Details](#-smart-contract-details)
- [Testing](#-testing)
- [Deployment](#-deployment)
- [Security Features](#-security-features)
- [Contributing](#-contributing)
- [License](#-license)

## ⚡ Quick Start

```bash
# Clone and setup
git clone <your-repo-url>
cd multisig-wallet
npm install

# Compile contracts
npm run compile

# Run tests
npm run test

# Deploy locally
npm run node          # In terminal 1
npm run deploy:localhost  # In terminal 2
```

## 🛠 Installation

### Prerequisites

- Node.js (v14 or higher)
- npm or yarn
- Git

### Setup

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd multisig-wallet
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Environment setup** (Optional for testnets)
   ```bash
   cp .env.example .env
   # Edit .env with your API keys and private key
   ```

4. **Compile contracts**
   ```bash
   npm run compile
   ```

## 🚀 Usage

### Deployment

#### Local Deployment
```bash
# Start local Hardhat node
npm run node

# Deploy to local network
npm run deploy:localhost
```

#### Testnet Deployment
```bash
# Deploy to Goerli
npx hardhat run scripts/deploy.js --network goerli

# Deploy to Sepolia
npx hardhat run scripts/deploy.js --network sepolia
```

### Interacting with the Wallet

#### Basic Transaction Flow

1. **Submit Transaction**
   ```javascript
   await multiSig.submit(recipientAddress, ethAmount, "0x");
   ```

2. **Confirm Transaction** (Need 2 confirmations)
   ```javascript
   await multiSig.connect(owner1).confirm(0);
   await multiSig.connect(owner2).confirm(0);
   ```

3. **Execute Transaction**
   ```javascript
   await multiSig.execute(0);
   ```

#### Using the Interaction Script

```bash
# Edit scripts/interact.js with your deployed contract address
npm run interact
```

### Smart Contract Interactions

#### Send ETH
```javascript
// Submit ETH transfer
await multiSig.submit(
    "0x742d35Cc6634C0532925a3b8D4f3F2E", 
    ethers.utils.parseEther("1.0"), 
    "0x"
);
```

#### Interact with Other Contracts
```javascript
// ERC20 token transfer
const data = tokenContract.interface.encodeFunctionData(
    "transfer", 
    [recipient, amount]
);

await multiSig.submit(tokenContractAddress, 0, data);
```

## 📚 Smart Contract Details

### Contract Architecture

```
MultiSigWallet
├── owners[]              // Array of owner addresses
├── is

contract : 0xEFa8B94C22e30715c4E491Dd0F4239EFD017084e

<img width="1862" height="1015" alt="image" src="https://github.com/user-attachments/assets/59ac963d-c269-4d99-9dac-c563e507301b" />
