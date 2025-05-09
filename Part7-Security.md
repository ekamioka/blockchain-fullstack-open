# Part 7: Security – Best Practices and Common Vulnerabilities

## Topics

* Why smart contract security matters
* Common vulnerabilities in Solidity
* Security tools and auditing
* Best practices

## Importance of Smart Contract Security

Smart contracts are immutable once deployed. Any bugs or vulnerabilities can lead to loss of funds or abuse.

### Notable Exploits

* **The DAO hack (2016)**: Reentrancy bug led to \~\$60M loss
* **Parity Multisig Wallet (2017)**: Self-destruct vulnerability froze \$150M+
* **Wormhole bridge hack (2022)**: \$320M stolen due to unchecked validation

## Common Vulnerabilities

### 1. Reentrancy

Occurs when a contract calls another contract that in turn calls back into the first contract before it has completed execution.

#### Mitigation:

* Use `checks-effects-interactions` pattern
* Use `reentrancyGuard` modifier from OpenZeppelin

### 2. Integer Overflow/Underflow

Results in unexpected wrapping behavior.

#### Mitigation:

* Use Solidity >= 0.8.0 which has built-in overflow checks
* Use `SafeMath` library if working with older versions

### 3. Denial of Service (DoS)

Gas limits can be exploited to block contract functionality, e.g., in looping or fallback mechanisms.

#### Mitigation:

* Avoid unbounded loops
* Fail gracefully in fallback functions

### 4. Front-running

Attackers can manipulate transaction ordering for profit.

#### Mitigation:

* Use commit-reveal schemes
* Include randomness or encryption

### 5. Access Control Issues

Missing or faulty access restrictions can expose critical functions.

#### Mitigation:

* Use `onlyOwner` or `role-based` access
* Follow the principle of least privilege

## Tools for Auditing and Analysis

* **Slither**: Static analyzer by Trail of Bits
* **MythX**: Security analysis API
* **Remix Analyzer Plugin**: Built-in security hints
* **Echidna**: Property-based fuzz testing

### Example: Using Slither

```bash
pip install slither-analyzer
slither contracts/MyContract.sol
```

## Best Practices

1. **Write tests for all edge cases**
2. **Review logic and role assignments thoroughly**
3. **Use libraries like OpenZeppelin**
4. **Minimize on-chain storage and trust assumptions**
5. **Document expected behavior and limitations**
6. **Conduct internal and external audits**
7. **Use bug bounty programs for public testing**

## Exercises

1. Identify vulnerabilities in a flawed smart contract using Remix.
2. Install and run Slither on a project.
3. Refactor a contract to include reentrancy protection.
4. Implement access control using `Ownable` from OpenZeppelin.

## Resources

* SWC Registry: [https://swcregistry.io](https://swcregistry.io)
* OpenZeppelin Contracts: [https://docs.openzeppelin.com/contracts](https://docs.openzeppelin.com/contracts)
* Slither: [https://github.com/crytic/slither](https://github.com/crytic/slither)
* Smart Contract Best Practices: [https://consensys.github.io/smart-contract-best-practices](https://consensys.github.io/smart-contract-best-practices)
