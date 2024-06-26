# Eth_Avax-mode-3
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/token/ERC20/extensions/ERC20Burnable.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

//the contract owner should be able to mint tokens to a provided address 
//and any user should be able to burn and transfer tokens.
contract METAtoken is ERC20, ERC20Burnable, Ownable {
    uint public totalTokenSupply;

    constructor(address initialOwner) ERC20("MetaToken", "MTK") Ownable(initialOwner){
        uint initialTokenSupply = 1000 * 10**18; // Initialize and declare the variable
        _mint(initialOwner, initialTokenSupply);  
    }
    function MintTokens(address recipient, uint amount) public onlyOwner {
        _mint(recipient, amount);
        totalTokenSupply += amount;
    }
/*
    function BurnTokens(uint amount) public {
        _burn(msg.sender, amount);
        totalTokenSupply -= amount;
    }

    function sendTokens(address recipient, uint amount) public {
        _transfer(msg.sender, recipient, amount);
    }
*/
}
```
