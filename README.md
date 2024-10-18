# MyToken

This Solidity program is a simple program that is able to mint and burn tokens. It is a course project that demonstrates the basic syntax and functionality of the Solidity programming language.

## Description

This program is a simple contract written in Solidity, a programming language used for developing smart contracts on the Ethereum blockchain. 
The contract called "MyToken" has two variables to hold the name and abbreviated name of the token, a variable to hold the supply value of the token, 
and a mapping variable to hold the balance value linked to a user given address argument. 
The contract also has two functions that is able to mint and burn tokens after a user provides an address and value argument. 


## Getting Started

### Executing program

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., MyToken.sol). Copy and paste the following code into the file:

```javascript
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.18;

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
    string public tokenName = "GOLDFISH";
    string public tokenAbbrv = "GDF";
    uint public tokenSupply = 0;

    // mapping variable here
    mapping (address => uint) public balances;

    // mint function
    function mint(address _address, uint _value) public {
        tokenSupply += _value;
        balances[_address] += _value;
    }

    // burn function
    function burn(address _address, uint _value) public {
        if(balances[_address] >= _value) {
            tokenSupply -= _value;
            balances[_address] -= _value;
        }
    }
}

```

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.18" (or another compatible version), and then click on the "Compile MyToken.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "MyToken" contract from the dropdown menu, and then click on the "Deploy" button.

Once the contract is deployed, you can interact with it by clicking on the tokenName and tokenAbbrv variables to show the name and abbreviated name of the token. 
Click on the "mint" function to add a value amount to the token, but first you will need an address (you can copy the address string in the "ACCOUNT" segment within the same tab). 

After providing an amount and clicking "transact", clicking the "tokenSupply" variable will show the amount you added using the "mint" function.
Similarly, the "balances" variable will show the added amount to the token but will first require the same address argument provided in the "mint" function.

The "burn" function will be used to deduct an amount to the value held within the token. The same process done with the "mint" function is also done with the "burn" function. 
Providing the same address means you will be deducting an amount to the token linked to that address. After clicking "transact", the value in the "tokenSupply" and "balances" variables are now reduced. 
But if the value provided in the "burn" function is greater than the remaining value held within the token, both the value in the "tokenSupply" and "balances" variables will not be reduced.



## Authors

Rylan Torres 
* Email: 202111443@fit.edu.ph


## License

This project is licensed under the MIT License - see the LICENSE.md file for details
