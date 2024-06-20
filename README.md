# MyToken Smart Contract
: A Simple ERC20-like Token Implementation on Ethereum


## Description

MyToken is a simple implementation of an ERC20-like token on the Ethereum blockchain. This smart contract includes basic functionalities such as minting new tokens, burning existing tokens, and keeping track of balances. It provides a foundational example for learning about blockchain technology and smart contract development using Solidity.

## Getting Started

Token Details: Public variables to store token name, abbreviation, and total supply.
Balances Mapping: Mapping of addresses to their respective token balances.
Mint Function: Allows increasing the total supply and the balance of a specified address.
Burn Function: Allows decreasing the total supply and the balance of a specified address, with checks to ensure sufficient balance.

### Installing
1.Search the remix.ethereum.org
2. Create a file 
3. Name the file


### Executing program

1.Open Remix:
Go to Remix.
Create a New File:

2. On the left panel, under the "File Explorer" tab, click on the "New File" button.
3. Name your file MyToken.sol.
4. Copy the Contract Code:

Copy and paste your Solidity contract code into the new file MyToken.sol.
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

/*
       REQUIREMENTS
    1. Your contract will have public variables that store the details about your coin (Token Name, Token Abbrv., Total Supply)
    2. Your contract will have a mapping of addresses to balances (address => uint)
    3. You will have a mint function that takes two parameters: an address and a value. 
       The function then increases the total supply by that number and increases the balance 
       of the “sender” address by that amount
    4. Your contract will have a burn function, which works the opposite of the mint function, as it will destroy tokens. 
       It will take an address and value just like the mint functions. It will then deduct the value from the total supply 
       and from the balance of the “sender”.
    5. Lastly, your burn function should have conditionals to make sure the balance of "sender" is greater than or equal 
       to the amount that is supposed to be burned.
*/

contract MyToken {

    // public variables here
    string public tokenname = "META";
    string public tokenAbbrv = "MTA";
    uint public totalSupply = 0;


    // mapping variable here
    mapping(address => uint)  public balances;

    // mint function
    function mint (address _address, uint _value) public {
        totalSupply += _value;
        balances[_address] += _value;
    }


    // burn function
    function burn (address _address, uint _value) public {
        if (balances[_address] >= _value) {
            totalSupply -= _value;
            balances[_address] -= _value;

        }
    }

}

5.Compile the Contract:

Click on the "Solidity Compiler" tab (looks like a "S" in the left sidebar).
Ensure the compiler version is set to 0.8.18.
Click the "Compile MyToken.sol" button.
6.Deploy the Contract:

Click on the "Deploy & Run Transactions" tab (looks like a "rocket" in the left sidebar).
Ensure the "Environment" is set to "JavaScript VM (London)" for local testing.
Click the "Deploy" button.

7.Interact with the Contract:

After deploying, your contract will appear under "Deployed Contracts" in the same tab.
You can expand it to see the available functions and variables.

8.Test the Contract:

Check Initial State:
Click on tokenname, tokenAbbrv, and totalSupply to see their initial values.
Click on balances and enter your address to see the initial balance (should be 0).
Mint Tokens:

9.Use the mint function.
The mint function allows creating new tokens by increasing the total supply and the recipient's balance. An event is emitted to log this action.
   
    function mint(address recipient, uint256 amount) public {
        require(amount > 0, "Mint amount must be greater than zero");
        totalTokens += amount;
        accountBalances[recipient] += amount;
        emit TokenTransfer(address(0), recipient, amount);
    }

10.Use the burn function.
The burn function allows destroying tokens by decreasing the total supply and the holder's balance, ensuring the holder has sufficient tokens. An event is emitted to log this action.
    
    function burn(address holder, uint256 amount) public {
        require(amount > 0, "Burn amount must be greater than zero");
        require(accountBalances[holder] >= amount, "Insufficient balance to burn");
        totalTokens -= amount;
        accountBalances[holder] -= amount;
        emit TokenTransfer(holder, address(0), amount);
    }


## OUTPUT

Upon deploying and interacting with the CustomToken contract, the following outputs can be observed:

Deployment: The contract is deployed with the specified token name and symbol. Initial total supply is zero.

Minting Tokens: Tokens are minted to the specified address, increasing the total supply and updating the recipient's balance.

Burning Tokens: Tokens are burned from the specified address, decreasing the total supply and updating the holder's balance.

Event Logs: TokenTransfer events are emitted for both minting and burning actions, providing a transparent log of these actions.

## Help

Focus on coding part and syntax so that chances of error are less.

## Authors

Contributors names and contact info

Divij Shukla
divij.shukla2003@gmail.com

## License

This project is licensed under the Notharley License - see the LICENSE.md file for details
