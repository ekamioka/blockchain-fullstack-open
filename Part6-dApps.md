# Part 6: dApps – Frontend Integration with Web3.js and Ethers.js

## Topics

* Introduction to dApps
* Connecting to Ethereum with MetaMask
* Using Web3.js
* Using Ethers.js
* Building a simple dApp

## Introduction to dApps

Decentralized applications (dApps) interact with smart contracts through web frontends. They typically include:

* A smart contract on Ethereum
* A frontend (HTML/JS) interacting via Web3 providers

### Example Use Cases:

* Token wallets
* NFT marketplaces
* Decentralized finance (DeFi)

## Connecting with MetaMask

MetaMask is a browser extension that acts as a bridge between the dApp and the Ethereum network.

### Steps:

1. Install MetaMask from [https://metamask.io](https://metamask.io)
2. Create/import a wallet
3. Switch to testnet (e.g., Sepolia)
4. Use `window.ethereum` to request access:

```javascript
await window.ethereum.request({ method: 'eth_requestAccounts' });
```

## Web3.js Basics

Web3.js is a JavaScript library for interacting with Ethereum.

### Install:

```bash
npm install web3
```

### Connect and Interact:

```javascript
import Web3 from 'web3';

const web3 = new Web3(window.ethereum);
const contract = new web3.eth.Contract(ABI, CONTRACT_ADDRESS);

const value = await contract.methods.get().call();
await contract.methods.set(123).send({ from: account });
```

## Ethers.js Basics

Ethers.js is a lightweight alternative to Web3.js, widely used in modern dApps.

### Install:

```bash
npm install ethers
```

### Connect and Interact:

```javascript
import { ethers } from 'ethers';

const provider = new ethers.BrowserProvider(window.ethereum);
await provider.send("eth_requestAccounts", []);
const signer = await provider.getSigner();
const contract = new ethers.Contract(CONTRACT_ADDRESS, ABI, signer);

const value = await contract.get();
await contract.set(123);
```

### Differences Between Web3.js and Ethers.js:

| Feature    | Web3.js         | Ethers.js         |
| ---------- | --------------- | ----------------- |
| Size       | Large           | Lightweight       |
| Promises   | Partially async | Fully async/await |
| Popularity | Older, stable   | Modern, preferred |

## Building a Simple dApp

Let’s build a counter dApp with React + Ethers.js.

### Example Structure:

```plaintext
src/
├── App.js
├── CounterContract.js
└── abi.json
```

### CounterContract.js:

```javascript
import { ethers } from 'ethers';
import ABI from './abi.json';

const CONTRACT_ADDRESS = "0x...";

export async function getValue() {
  const provider = new ethers.BrowserProvider(window.ethereum);
  const contract = new ethers.Contract(CONTRACT_ADDRESS, ABI, provider);
  return await contract.get();
}

export async function increment() {
  const provider = new ethers.BrowserProvider(window.ethereum);
  const signer = await provider.getSigner();
  const contract = new ethers.Contract(CONTRACT_ADDRESS, ABI, signer);
  return await contract.increment();
}
```

## Exercises

1. Connect a simple webpage to MetaMask and display the current account.
2. Build a minimal dApp using Web3.js that reads/writes to a smart contract.
3. Rebuild the same dApp using Ethers.js.
4. Compare gas usage when interacting with the contract via Remix vs dApp.

## Resources

* MetaMask Docs: [https://docs.metamask.io](https://docs.metamask.io)
* Web3.js Docs: [https://web3js.readthedocs.io](https://web3js.readthedocs.io)
* Ethers.js Docs: [https://docs.ethers.io](https://docs.ethers.io)
* Scaffold-ETH: [https://github.com/scaffold-eth/scaffold-eth](https://github.com/scaffold-eth/scaffold-eth)
