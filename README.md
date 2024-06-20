# MyToken Solidity Contract

This repository contains a Solidity smart contract called "MyToken" that implements a basic ERC20-like token with minting and burning functionalities.

## 📜 Contract Details

### Public Variables

- **tokenName**: Name of the token.
- **tokenAbbrv**: Abbreviation of the token.
- **totalSupply**: Total supply of the token.

### Mapping

- **balances**: A mapping of addresses to their respective token balances.

### Functions

#### Mint

The `mint` function allows the creation of new tokens.

```solidity
function mint(address _address, uint _value) public {
    totalSupply += _value;
    balances[_address] += _value;
}
```

- **Parameters**:
  - `_address`: The address to receive the new tokens.
  - `_value`: The number of tokens to be minted.

#### Burn

The `burn` function allows the destruction of tokens.

```solidity
function burn(address _address, uint _value) public {
    require(balances[_address] >= _value, "Insufficient balance to burn");
    totalSupply -= _value;
    balances[_address] -= _value;
}
```

- **Parameters**:
  - `_address`: The address from which tokens will be burned.
  - `_value`: The number of tokens to be burned.
- **Conditions**:
  - The balance of `_address` must be greater than or equal to `_value`.

## 📚 Usage

1. **Deploy the Contract**: Deploy the `MyToken` contract on an Ethereum-compatible blockchain.
2. **Mint Tokens**: Call the `mint` function with the recipient's address and the number of tokens to be minted.
3. **Burn Tokens**: Call the `burn` function with the address from which tokens will be burned and the number of tokens to be burned.

## 🛠️ Development

### Prerequisites

- Solidity ^0.8.0
- Ethereum-compatible blockchain

### Compiling and Deploying

Use your preferred Solidity development tools, such as Remix, Truffle, or Hardhat, to compile and deploy the contract.

### Example

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract MyToken {
    string public tokenName = "META";
    string public tokenAbbrv = "MTA";
    uint public totalSupply = 0;

    mapping (address => uint) public balances;

    function mint(address _address, uint _value) public {
        totalSupply += _value;
        balances[_address] += _value;
    }

    function burn(address _address, uint _value) public {
        require(balances[_address] >= _value, "Insufficient balance to burn");
        totalSupply -= _value;
        balances[_address] -= _value;
    }
}
