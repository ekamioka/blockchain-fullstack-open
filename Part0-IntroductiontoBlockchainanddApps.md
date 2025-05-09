# Blockchain Full Stack Open Course

A modular, open-source course inspired by the structure of the [Full Stack Open](https://fullstackopen.com/en/), focused on decentralized application (dApp) development using Solidity and related blockchain technologies.

---

## Part 0: Introduction to Blockchain and dApps

### Topics

* History and fundamentals of blockchain technology
* Key differences between centralized and decentralized systems
* What is Ethereum?
* What is a decentralized application (dApp)?
* Overview of the Ethereum ecosystem: smart contracts, tokens, wallets

### Tools & Setup

* Node.js and npm
* Installing Truffle and Ganache
* Using MetaMask
* Introduction to Git and GitHub

### Content

#### History and Fundamentals of Blockchain

Blockchain technology was introduced in 2008 with the release of the Bitcoin whitepaper by Satoshi Nakamoto. It provides a decentralized, immutable ledger for recording transactions in a secure and transparent way. Blocks are linked using cryptographic hashes, ensuring data integrity.

Key characteristics:

* **Decentralization**: No central authority controls the network.
* **Immutability**: Once recorded, data cannot be changed.
* **Transparency**: Transactions are publicly accessible.
* **Security**: Cryptographic algorithms secure the data.

#### Centralized vs Decentralized Systems

In centralized systems, a single entity controls data and operations (e.g., banks, social media platforms). In contrast, decentralized systems distribute control among multiple nodes, increasing resilience and user autonomy.

| Aspect        | Centralized System | Decentralized System       |
| ------------- | ------------------ | -------------------------- |
| Control       | Single authority   | Multiple participants      |
| Failure Point | Single point       | No single point of failure |
| Transparency  | Low                | High                       |
| Trust Model   | Trusted authority  | Trustless (via consensus)  |

#### What is Ethereum?

Ethereum is a programmable blockchain that supports smart contracts and decentralized applications (dApps). It was proposed in 2013 by Vitalik Buterin and launched in 2015. Ethereum enables developers to deploy Turing-complete scripts called **smart contracts** that run on the Ethereum Virtual Machine (EVM).

Key components:

* **Ether (ETH)**: Native cryptocurrency
* **Smart Contracts**: Self-executing programs
* **dApps**: Decentralized applications
* **EVM**: The runtime environment

#### What is a dApp?

dApps are applications that run on a decentralized network. Unlike traditional apps, dApps:

* Are open-source
* Use blockchain for backend logic
* Store data immutably
* Rely on tokens for access or governance

Examples: Uniswap, Aave, OpenSea

#### Ethereum Ecosystem Overview

* **Smart Contracts**: Code stored and executed on the blockchain
* **Tokens**: Digital assets (ERC-20, ERC-721)
* **Wallets**: Tools like MetaMask that allow users to interact with dApps
* **Networks**: Mainnet and testnets (Goerli, Sepolia)

### Tools & Setup

#### Node.js and npm

Install Node.js from [nodejs.org](https://nodejs.org/) and verify installation with:

```bash
node -v
npm -v
```

#### Installing Truffle and Ganache

Truffle is a popular smart contract development framework:

```bash
npm install -g truffle
```

Ganache is a local Ethereum emulator:

* Download Ganache from [trufflesuite.com/ganache](https://trufflesuite.com/ganache/)
* Use it to run a personal Ethereum blockchain

#### Using MetaMask

MetaMask is a browser extension that acts as a crypto wallet:

* Install from [metamask.io](https://metamask.io/)
* Create an account and connect it to Ganache/testnet

#### Git and GitHub

Version control using Git is essential:

```bash
sudo apt install git # or brew install git on macOS
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

### Exercises

1. Install Node.js, Truffle, Ganache, and MetaMask
2. Clone the starter project:

```bash
git clone https://github.com/YOUR_USERNAME/blockchain-starter.git
cd blockchain-starter
```

3. Launch Ganache and connect MetaMask to the local network
4. Open [Remix IDE](https://remix.ethereum.org/) and paste this smart contract:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract HelloBlockchain {
    string public message = "Hello, Blockchain!";
}
```

5. Compile and deploy the contract on Remix using JavaScript VM or injected Web3
6. Interact with the deployed contract using the Remix UI

---

## Part 1: Smart Contract Basics with Solidity

### Topics

* What is Solidity?
* Contract structure, functions, and state variables
* Deploying and testing simple contracts
* Data types and visibility specifiers

### Tools

* Remix IDE for Solidity development
* Ganache for local testing
* MetaMask for testnet interaction

### Exercises

* Write a simple storage contract
* Compile and deploy with Remix
* Interact with deployed contract via Remix UI
