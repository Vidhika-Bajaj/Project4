# Create and mint Token
This token contract programme describes token transactions via minting, burning, transferring, adding, or using various functions and events like Total_Supply, balanceOf, and so on.
## Description

This programme is a straightforward contract for producing and minting tokens. It asks for information about the token, such as its name, total supply, and balance, and returns results in accordance. It has three events: Mint (for adding tokens), Burn (for burning tokens), and Transfer (for transferring tokens). OwnToken and VTotalSupply, which are stored in my_own_token and V_Token_total_Supply and whose value is likewise saved in balances, are the constructor's next two parameters. Six functions are then available: V_Total_Supply() for returning the V_Token_total_Supply value, balanceOf for returning the account balance, transfer for transferring tokens, burn for burning the specified amount of tokens from the account and updating the current value afterwards, and mint for adding new tokens.

## Getting Started
### Executing program
       
```javascript
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract Vids_Token is ERC20 {
    address public owner;

    constructor(string memory name, string memory symbol) ERC20(name, symbol) {
        owner = msg.sender;
        _mint(msg.sender, 1000000 * 10 ** decimals());
    }

    modifier onlyOwner() {
        require(msg.sender == owner, "Only the owner can call this function");
        _;
    }

    function mint(address to, uint256 amount) external onlyOwner {
        _mint(to, amount);
    }

    function burn(uint256 amount) external {
        _burn(msg.sender, amount);
    }
}
               
```
To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.4" (or another compatible version), and then click on the "Compile Vids_project_M3.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "Vids_Token" contract from the dropdown menu, and then click on the "Deploy" button. 

Once the contract is deployed, you can interact with it by clicking on various functions. Click on the "Vids_Token" contract in the left-hand sidebar, and then click on the functions for transactions, getting the results accordingly as burning or adding of tokens.

## Authors
Vidhika Bajaj

## License
This project is licensed under the MIT License
