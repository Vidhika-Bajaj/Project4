# Create and mint Toekn
This token contract programme describes token transactions via minting, burning, transferring, adding, or using various functions and events like Total_Supply, balanceOf, and so on.
## Description

This programme is a straightforward contract for producing and minting tokens. It asks for information about the token, such as its name, total supply, and balance, and returns results in accordance. It has three events: Mint (for adding tokens), Burn (for burning tokens), and Transfer (for transferring tokens). OwnToken and VTotalSupply, which are stored in my_own_token and V_Token_total_Supply and whose value is likewise saved in balances, are the constructor's next two parameters. Six functions are then available: V_Total_Supply() for returning the V_Token_total_Supply value, balanceOf for returning the account balance, transfer for transferring tokens, burn for burning the specified amount of tokens from the account and updating the current value afterwards, and mint for adding new tokens.

## Getting Started
### Executing program
       
```javascript
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Token_by_Vids {
    string public V_token;
    uint256 private V_total_Supply;
    mapping(address => uint256) private _balances;
    
    event Transfer(address indexed from, address indexed to, uint256 value);
    event Burn(address indexed account, uint256 amount);
    event Mint(address indexed account, uint256 amount);

    constructor(string memory Vids_Token, uint256 VTotalSupply) {
        V_token = Vids_Token
        V_total_Supply = VTotalSupply;
        _balances[msg.sender] = V_total_Supply;
        emit Transfer(address(0), msg.sender, V_total_Supply);
    }

    function Total_Supply() external view returns (uint256) {
        return V_total_Supply;
    }

    function balanceOf(address account) external view returns (uint256) {
        return _balances[account];
    }

    function transfer(address recipient, uint256 amount) external returns (bool) {
        _transfer(msg.sender, recipient, amount);
        return true;
    }

    function burn(uint256 amount) external returns (bool) {
        require(amount <= _balances[msg.sender], "Asked balance not present");
        _balances[msg.sender] -= amount;
        V_total_Supply -= amount;
        emit Burn(msg.sender, amount);
        emit Transfer(msg.sender, address(0), amount);
        return true;
    }

    function mint(address account, uint256 amount) external returns (bool) {
        require(account!= address(0), "Account address incorrect");
        V_total_Supply += amount;
        _balances[account] += amount;
        emit Mint(account, amount);
        emit Transfer(address(0), account, amount);
        return true;
    }

    function _transfer(address sender, address recipient, uint256 amount) internal {
        require(amount <= _balances[sender], "Balance not present to transfer");

        _balances[sender] -= amount;
        _balances[recipient] += amount;
        emit Transfer(sender, recipient, amount);
    }
}               
```
To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.4" (or another compatible version), and then click on the "Compile Vids_project_M3.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "Create_and_mint_Token_by_Vids" contract from the dropdown menu, and then click on the "Deploy" button. 

Once the contract is deployed, you can interact with it by clicking on various functions. Click on the "Create_and_mint_Token_by_Vids" contract in the left-hand sidebar, and then click on the functions for transactions, getting the results accordingly as burning or adding of tokens.

## Authors
Vidhika Bajaj

## License
This project is licensed under the MIT License
