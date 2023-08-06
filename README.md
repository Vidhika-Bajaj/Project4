# Create and mint Toekn
This token contract program tells about the transaction of tokens by burning, adding or transferring tokens using various functions and events like mint, burn, transfer, Total_Supply, balanceOf, etc.
## Description

This program is a simple contract for cricket matches, providing the details of match scheduling and injuries during the match, getting the results accordingly. It contains four functions that are: First Match, that is responsible for the finalCall value using assert statement means if there will be a match then the finalCall value will get incremented by 3 and if not then it will remain the same and print one message too along with the calling of Matchtoday(public variable) using require technique, Second CancelledMatch, is responsible for reverting the match schedule using Matchtoday variable, Third getCal, for returning finalCall value, Fourth InjuryHappened for returning the result of the Medical variable if it is needed or not using revert technique.

## Getting Started
### Executing program
       
```javascript
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Create_and_mint_Token_by_Vids {
    string public my_own_token;
    uint256 private V_Token_total_Supply;
    mapping(address => uint256) private _balances;
    
    event Transfer(address indexed from, address indexed to, uint256 value);
    event Burn(address indexed account, uint256 amount);
    event Mint(address indexed account, uint256 amount);

    constructor(string memory OwnToken, uint256 VTotalSupply) {
        my_own_token = OwnToken;
        V_Token_total_Supply = VTotalSupply;
        _balances[msg.sender] = V_Token_total_Supply;
        emit Transfer(address(0), msg.sender, V_Token_total_Supply);
    }

    function V_Total_Supply() external view returns (uint256) {
        return V_Token_total_Supply;
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
        V_Token_total_Supply -= amount;
        emit Burn(msg.sender, amount);
        emit Transfer(msg.sender, address(0), amount);
        return true;
    }

    function mint(address account, uint256 amount) external returns (bool) {
        V_Token_total_Supply += amount;
        _balances[account] += amount;
        emit Mint(account, amount);
        emit Transfer(address(0), account, amount);
        return true;
    }

    function _transfer(address sender, address recipient, uint256 amount) internal {
        require(amount <= _balances[sender], "Balance not present");

        _balances[sender] -= amount;
        _balances[recipient] += amount;
        emit Transfer(sender, recipient, amount);
    }
}               
```
To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.4" (or another compatible version), and then click on the "Compile M_m3p3.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "Niks_Token" contract from the dropdown menu, and then click on the "Deploy" button. 

Once the contract is deployed, you can interact with it by clicking on various functions. Click on the "Niks_Token" contract in the left-hand sidebar, and then click on the functions for transactions, getting the results accordingly as burning or adding of tokens.

## Authors
Vidhika Bajaj

## License
This project is licensed under the MIT License
