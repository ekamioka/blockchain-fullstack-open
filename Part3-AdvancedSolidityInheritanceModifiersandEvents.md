# Part 3: Advanced Solidity – Inheritance, Modifiers, and Events

## Topics

* Contract inheritance and overriding
* Function modifiers and access control
* Using and emitting events
* Abstract contracts and interfaces

## Contract Inheritance

Solidity supports object-oriented inheritance. Contracts can inherit from other contracts using the `is` keyword.

### Example:

```solidity
contract Parent {
    uint public value;

    function setValue(uint _val) public {
        value = _val;
    }
}

contract Child is Parent {
    function doubleValue() public {
        value *= 2;
    }
}
```

### Key Points:

* Inheritance promotes reusability and modular design
* Functions can be overridden with `virtual` and `override`

```solidity
contract A {
    function foo() public virtual returns (string memory) {
        return "A";
    }
}

contract B is A {
    function foo() public override returns (string memory) {
        return "B";
    }
}
```

## Function Modifiers

Modifiers are used to change the behavior of functions, often for access control and validation.

### Example:

```solidity
contract OwnerRestricted {
    address public owner;

    constructor() {
        owner = msg.sender;
    }

    modifier onlyOwner() {
        require(msg.sender == owner, "Not the owner");
        _;
    }

    function privilegedAction() public onlyOwner {
        // only the owner can do this
    }
}
```

## Events and Logging

Events provide a logging mechanism clients can use to subscribe to and react to changes.

### Example:

```solidity
event ValueChanged(address indexed user, uint newValue);

function changeValue(uint _new) public {
    storedData = _new;
    emit ValueChanged(msg.sender, _new);
}
```

### Notes:

* Use `indexed` for up to 3 searchable parameters
* Events help off-chain apps track contract activity

## Abstract Contracts and Interfaces

### Abstract Contracts

Contain at least one unimplemented function.

```solidity
abstract contract Shape {
    function area() public view virtual returns (uint);
}

contract Square is Shape {
    uint side;

    constructor(uint _side) {
        side = _side;
    }

    function area() public view override returns (uint) {
        return side * side;
    }
}
```

### Interfaces

Define required external functions with no implementation.

```solidity
interface IERC20 {
    function totalSupply() external view returns (uint);
    function balanceOf(address account) external view returns (uint);
    function transfer(address recipient, uint amount) external returns (bool);
}
```

## Exercises

1. Create a base contract with a function and inherit from it to override the function.
2. Add a `onlyOwner` modifier to your contract from Part 1.
3. Add and emit an event whenever a value changes in a contract.
4. Write an abstract contract and implement it.
5. Create a minimal interface for a voting contract.

## Resources

* Solidity Docs: [https://soliditylang.org/docs](https://soliditylang.org/docs)
* Inheritance: [https://soliditylang.org/docs/inheritance.html](https://soliditylang.org/docs/inheritance.html)
* Events and Logging: [https://soliditylang.org/docs/events.html](https://soliditylang.org/docs/events.html)
