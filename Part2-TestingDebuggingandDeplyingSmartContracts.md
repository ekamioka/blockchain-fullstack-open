# Part 2: Testing, Debugging, and Deploying Smart Contracts

## Topics

* Writing automated tests for smart contracts
* Debugging with Truffle and Remix
* Local deployment with Ganache
* Testnets and deploying to Ethereum

## Testing Smart Contracts

Testing ensures the correctness of your contracts and helps prevent costly bugs in production.

### Using Truffle for Testing

Truffle uses Mocha and Chai under the hood for JavaScript-based testing.

```bash
npm install -g truffle
mkdir test-project && cd test-project
truffle init
```

Example test (`test/SimpleContract.test.js`):

```javascript
const SimpleContract = artifacts.require("SimpleContract");

contract("SimpleContract", accounts => {
  it("should store the value 89.", async () => {
    const instance = await SimpleContract.deployed();
    await instance.set(89, { from: accounts[0] });
    const result = await instance.get();
    assert.equal(result, 89, "The value 89 was not stored.");
  });
});
```

Run tests with:

```bash
truffle test
```

## Debugging with Remix and Truffle

### Remix Debugger

* Use the **Debugger** tab in Remix to step through transactions
* Inspect stack, memory, and storage
* Useful for runtime errors like reverts

### Truffle Debugger

```bash
truffle develop
truffle debug <tx_hash>
```

## Local Deployment with Ganache

Ganache provides a personal Ethereum blockchain for development and testing.

### GUI or CLI

* GUI: Download from [https://trufflesuite.com/ganache/](https://trufflesuite.com/ganache/)
* CLI: `npm install -g ganache`

Configure `truffle-config.js`:

```javascript
module.exports = {
  networks: {
    development: {
      host: "127.0.0.1",
      port: 7545,
      network_id: "*",
    },
  },
};
```

Then deploy:

```bash
truffle migrate --network development
```

## Deployment to Ethereum Testnets

Use Infura or Alchemy for access to public testnets.

### Steps:

1. Create an Infura/Alchemy project
2. Configure `.env` and `truffle-config.js`
3. Fund your MetaMask wallet on Goerli or Sepolia testnet
4. Deploy with Truffle:

```bash
truffle migrate --network goerli
```

Sample network config:

```javascript
const HDWalletProvider = require("@truffle/hdwallet-provider");
require('dotenv').config();

module.exports = {
  networks: {
    goerli: {
      provider: () => new HDWalletProvider(process.env.MNEMONIC, `https://goerli.infura.io/v3/${process.env.INFURA_API_KEY}`),
      network_id: 5,
      gas: 5500000,
    },
  },
};
```

## Exercises

1. Write a test for a contract that increments a counter.
2. Use Remix to deploy and trigger a failing transaction, then debug it.
3. Deploy a smart contract on Ganache using Truffle.
4. Set up and deploy to Goerli or Sepolia using Infura/Alchemy.

## Resources

* Truffle Docs: [https://trufflesuite.com/docs](https://trufflesuite.com/docs)
* Ganache: [https://trufflesuite.com/ganache](https://trufflesuite.com/ganache)
* Infura: [https://infura.io](https://infura.io)
* Alchemy: [https://www.alchemy.com](https://www.alchemy.com)
* Ethereum Faucet (Goerli): [https://goerlifaucet.com](https://goerlifaucet.com)
