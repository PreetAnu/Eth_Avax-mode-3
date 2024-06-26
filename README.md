# Eth_Avax: Intermediate module-3
## MetaToken
This Solidity program is a simple smart contract for creating and managing an ERC20 token. It demonstrates the basic syntax and functionality of the Solidity programming language while using the OpenZeppelin library for secure and robust contract development. The purpose of this contract is to serve as a practical example for creating, minting, burning, and transferring ERC20 tokens on the blockchain.
## Description
The MetaToken contract allows the owner to mint tokens to a provided address and enables any user to burn and transfer tokens. It includes functions to mint new tokens, burn existing tokens, transfer tokens to another address, and check the balance of an address.
## Getting Started
### Executing Program
* To run this program, I used Remix, an online Solidity IDE. To get started, go to the Remix website at Remix Ethereum.
* Create a New File:
Click on the "+" icon in the left-hand sidebar.
Save the file with a .sol extension (e.g., MetaToken.sol).
* Copy and Paste the Code: Copy the following code and paste it into the newly created file:
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
### Compile the Code
* Click on the "Solidity Compiler" tab in the left-hand sidebar.
* Make sure the "Compiler" option is set to "0.8.20" (or another compatible version).
* Click on the "Compile METAtoken.sol" button or use the shortcut key (Ctrl+s).
  ### Deploy the Contract
  * Click on the "Deploy & Run Transactions" tab in the left-hand sidebar.
  * Select the "METAtoken" contract from the dropdown menu.
  * Enter the initial owner address in the constructor arguments.
  * Click on the "Deploy" button and confirm the transaction in your Ethereum wallet (e.g., MetaMask).
 ### Interact with the Contract
* Mint Tokens (Only Owner): Call the MintTokens function with the recipient address and the amount of tokens to mint.
* Burn Tokens: Uncomment the BurnTokens function in the contract, compile and deploy it again, then call the BurnTokens function with the amount of tokens to burn.
* Transfer Tokens: Uncomment the sendTokens function in the contract, compile and deploy it again, then call the sendTokens function with the recipient address and the amount of tokens to transfer.
* Get Balance: Uncomment the getBalance function in the contract, compile and deploy it again, then call the getBalance function with the address to check the balance.
## Author
* Anupreet Kaur
* anupreetk159@gmail.com

## License
This project is licensed under the MIT License - see the LICENSE.md file for details.
