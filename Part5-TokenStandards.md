# Part 5: Token Standards – ERC-20, ERC-721, ERC-1155

## Topics

* Introduction to token standards
* ERC-20 fungible tokens
* ERC-721 non-fungible tokens (NFTs)
* ERC-1155 multi-token standard
* Building and interacting with tokens

## What Are Token Standards?

Token standards are Ethereum Improvement Proposals (EIPs) that define how tokens behave and interact with the network.

### Common Use Cases

* Fungible currencies (e.g., USDC, DAI)
* Non-fungible assets (e.g., NFTs, game items)
* Multi-token contracts (e.g., games and marketplaces)

## ERC-20: Fungible Token Standard

Fungible tokens are interchangeable and divisible.

### Key Functions:

* `totalSupply()`
* `balanceOf(address)`
* `transfer(to, amount)`
* `approve(spender, amount)`
* `transferFrom(from, to, amount)`

### Basic ERC-20 Implementation:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract MyToken is ERC20 {
    constructor() ERC20("MyToken", "MTK") {
        _mint(msg.sender, 1000 * 10 ** decimals());
    }
}
```

### Tools

* OpenZeppelin contracts: [https://github.com/OpenZeppelin/openzeppelin-contracts](https://github.com/OpenZeppelin/openzeppelin-contracts)
* ERC-20 reference: [https://eips.ethereum.org/EIPS/eip-20](https://eips.ethereum.org/EIPS/eip-20)

## ERC-721: Non-Fungible Token (NFT)

NFTs are unique and non-interchangeable tokens.

### Key Functions:

* `ownerOf(tokenId)`
* `safeTransferFrom(from, to, tokenId)`
* `approve(to, tokenId)`
* `tokenURI(tokenId)`

### Basic ERC-721 Implementation:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC721/ERC721.sol";

contract MyNFT is ERC721 {
    uint public nextTokenId;
    address public admin;

    constructor() ERC721("MyNFT", "MNFT") {
        admin = msg.sender;
    }

    function mint(address to) external {
        require(msg.sender == admin, "only admin");
        _safeMint(to, nextTokenId);
        nextTokenId++;
    }
}
```

### Metadata

Metadata typically stored off-chain via IPFS or services like Pinata.

### Tools

* OpenZeppelin ERC-721: [https://docs.openzeppelin.com/contracts/4.x/erc721](https://docs.openzeppelin.com/contracts/4.x/erc721)
* ERC-721 spec: [https://eips.ethereum.org/EIPS/eip-721](https://eips.ethereum.org/EIPS/eip-721)

## ERC-1155: Multi-Token Standard

Supports fungible, semi-fungible, and non-fungible tokens in one contract.

### Key Features:

* Batch operations
* Gas efficient
* Inventory-based systems (e.g., gaming items)

### Basic Use:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC1155/ERC1155.sol";

contract MyGameAssets is ERC1155 {
    constructor() ERC1155("https://game.example/api/item/{id}.json") {}

    function mint(address account, uint256 id, uint256 amount) external {
        _mint(account, id, amount, "");
    }
}
```

### Tools

* OpenZeppelin ERC-1155: [https://docs.openzeppelin.com/contracts/4.x/erc1155](https://docs.openzeppelin.com/contracts/4.x/erc1155)
* ERC-1155 spec: [https://eips.ethereum.org/EIPS/eip-1155](https://eips.ethereum.org/EIPS/eip-1155)

## Exercises

1. Deploy an ERC-20 token with custom name and supply.
2. Build and mint an NFT with ERC-721.
3. Create a simple ERC-1155 contract for two types of in-game items.
4. Explore OpenSea’s testnet by minting and viewing NFTs.

## Resources

* Ethereum Token Standards: [https://ethereum.org/en/developers/docs/standards/tokens/](https://ethereum.org/en/developers/docs/standards/tokens/)
* OpenSea Developer Docs: [https://docs.opensea.io](https://docs.opensea.io)
* IPFS: [https://ipfs.io](https://ipfs.io)
* Pinata: [https://www.pinata.cloud](https://www.pinata.cloud)
