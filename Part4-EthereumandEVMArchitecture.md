# Part 4: Ethereum and EVM Architecture

## Topics

* Overview of Ethereum
* Ethereum Virtual Machine (EVM)
* Accounts and gas
* Transactions and state changes
* Blockchain structure

## Overview of Ethereum

Ethereum is a decentralized, open-source blockchain platform that enables smart contracts and decentralized applications (dApps).

### Key Components:

* **Smart Contracts**: Self-executing code
* **dApps**: Apps built on smart contracts
* **Ether (ETH)**: Native currency used for gas fees

## Ethereum Virtual Machine (EVM)

The EVM is a sandboxed runtime that executes smart contracts.

### Properties:

* Stack-based virtual machine
* Executes bytecode compiled from Solidity or Vyper
* Deterministic: same input = same output across nodes

### EVM Opcodes

Contracts are compiled into low-level opcodes such as `PUSH`, `JUMP`, and `SSTORE`. Tools like [evm.codes](https://www.evm.codes/) provide opcode documentation.

## Accounts

There are two types of accounts:

1. **Externally Owned Accounts (EOAs)**:

   * Controlled by private keys
   * Can send transactions

2. **Contract Accounts**:

   * Controlled by code
   * Can’t initiate transactions, only react

### Account Structure:

* **nonce**: transaction counter
* **balance**: amount of ETH
* **codeHash**: contract code identifier
* **storageRoot**: root of Merkle Patricia Trie storing variables

## Gas

Gas measures the computational effort required to execute operations.

### Important Points:

* Each operation has a cost (e.g., `ADD` is 3 gas, `SSTORE` is 20,000 gas)
* Prevents infinite loops and spam
* Unused gas is refunded

### Gas Limit & Price

* **Gas Limit**: Max gas you’re willing to spend
* **Gas Price**: ETH per gas unit (set in Gwei)

### Example:

```solidity
function store(uint x) public {
    stored = x; // incurs SSTORE cost
}
```

## Transactions

A transaction is a message sent from an EOA that can:

* Transfer ETH
* Deploy a contract
* Interact with a contract

### Lifecycle:

1. Created and signed by EOA
2. Propagated to network
3. Mined into a block
4. Changes global state

### Structure:

* `nonce`, `gasPrice`, `gasLimit`
* `to`, `value`, `data`, `v`, `r`, `s`

## Blockchain Structure

Ethereum uses a chain of blocks, each containing:

* Block header (timestamp, parent hash, difficulty)
* List of transactions
* State root hash (Merkle root)

### State Trie

A Merkle Patricia Trie stores the global state (balances, storage). Efficient and tamper-proof.

## Exercises

1. Compare EOAs and Contract Accounts – give two use cases for each.
2. Use Remix to inspect gas usage of different operations.
3. Explain what happens during a transaction that calls a contract function.
4. Research the role of Merkle Patricia Tries in Ethereum.

## Resources

* Ethereum Yellow Paper: [https://ethereum.github.io/yellowpaper/paper.pdf](https://ethereum.github.io/yellowpaper/paper.pdf)
* EVM Opcodes: [https://www.evm.codes](https://www.evm.codes)
* Solidity Gas Costs: [https://docs.soliditylang.org/en/latest/units-and-global-variables.html#gas-related](https://docs.soliditylang.org/en/latest/units-and-global-variables.html#gas-related)
* Ethereum.org: [https://ethereum.org/en/developers/docs/evm/](https://ethereum.org/en/developers/docs/evm/)
