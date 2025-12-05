# SimpleBaseNFT.sol
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

// Importing OpenZeppelin standards directly for Remix compatibility
import "@openzeppelin/contracts/token/ERC721/ERC721.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract BaseBuilderNFT is ERC721, Ownable {
    uint256 public tokenCounter;

    constructor() ERC721("Base Builder NFT", "BBNFT") Ownable(msg.sender) {
        tokenCounter = 0;
    }

    function safeMint(address to) public onlyOwner {
        uint256 tokenId = tokenCounter;
        _safeMint(to, tokenId);
        tokenCounter++;
    }
}
