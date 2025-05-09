# Part 1: Smart Contract Basics with Solidity

## Topics

* What is Solidity?
* Contract structure, functions, and state variables
* Deploying and testing simple contracts
* Data types and visibility specifiers

## What is Solidity?

Solidity is a statically typed, contract-oriented programming language designed for writing smart contracts on Ethereum. Inspired by JavaScript, Python, and C++, it compiles to bytecode that runs on the Ethereum Virtual Machine (EVM).

### Key Features:

* Static typing
* Inheritance and libraries
* Interface and contract abstraction
* Event logging and modifiers

Official site: [soliditylang.org](https://soliditylang.org/)

## Basic Contract Structure

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract SimpleContract {
    uint public storedData;

    function set(uint x) public {
        storedData = x;
    }

    function get() public view returns (uint) {
        return storedData;
    }
}
```

### Explanation:

* `pragma`: Compiler version declaration
* `contract`: Defines a contract (like a class)
* `storedData`: A state variable stored on-chain
* `set()`: A public function to update `storedData`
* `get()`: A public view function to read `storedData`

## Data Types and Visibility

### Common Data Types:

* `uint`, `int`: Unsigned/signed integers
* `address`: Ethereum address type
* `bool`: Boolean
* `string`, `bytes`: Text and raw byte data
* `mapping`, `struct`, `array`: Custom types

### Visibility Keywords:

* `public`: Accessible externally and internally
* `private`: Only inside the contract
* `internal`: In the contract and derived contracts
* `external`: Can only be called from other contracts or transactions

## Testing and Deployment

### Tools:

* **Remix IDE**: A browser-based IDE for Solidity
* **Ganache**: Local blockchain emulator
* **MetaMask**: Browser wallet for Ethereum

### Deployment with Remix:

1. Open [Remix](https://remix.ethereum.org/)
2. Create a new file `SimpleContract.sol`
3. Paste the contract code
4. Compile the contract
5. Deploy using JavaScript VM or Injected Web3 (MetaMask)
6. Interact with the functions from the Remix interface

## Exercises

1. Create a contract that stores and retrieves a `string`.
2. Add an event to the setter function and emit it.
3. Add a `bool` variable `isActive`, and write a function to toggle it.
4. Use Remix to compile and test the contract using both JavaScript VM and MetaMask.
5. Add comments and experiment with visibility keywords.

## Resources

* Solidity Docs: [https://soliditylang.org/docs](https://soliditylang.org/docs)
* Remix: [https://remix.ethereum.org](https://remix.ethereum.org)
* OpenZeppelin Learn: [https://docs.openzeppelin.com/learn/](https://docs.openzeppelin.com/learn/)
* Ethernaut (security wargame): [https://ethernaut.openzeppelin.com/](https://ethernaut.openzeppelin.com/)
