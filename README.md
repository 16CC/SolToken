# MyToken Smart Contract

MyToken is a simple smart contract for a custom token on the Ethereum blockchain. The contract allows for minting and burning tokens, and it keeps track of balances for each address.

## Description

The MyToken contract includes the following features:

1. **Public Variables**:
   - `tokenName`: The name of the token, which is "Meta".
   - `tokenAbbrv`: The abbreviation of the token, which is "MTA".
   - `totalSupply`: The total supply of the tokens.

2. **Mapping**:
   - `balances`: A mapping from addresses to their token balances.

3. **Functions**:
   - `mint(address _address, uint _value)`: Mints new tokens to the specified address and increases the total supply by the specified value.
   - `burn(address _address, uint _value)`: Burns tokens from the specified address and decreases the total supply by the specified value. The burn function ensures that the balance of the sender is greater than or equal to the amount to be burned.

## Contract Code

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.19;

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
    string public tokenName = "Meta";
    string public tokenAbbrv = "MTA";
    uint public totalSupply = 0;

    // mapping variable here
    mapping(address => uint) public balances;

    // Constructor to initialize the token details
    function mint (address _address, uint _value) public{
        totalSupply += _value;
        balances[_address]+= _value;
    }

    // burn function
    function burn(address _address, uint _value) public {
       if (balances[_address] >= _value) {
        totalSupply -= _value;
        balances[_address] -= _value;
       }
    }
}

