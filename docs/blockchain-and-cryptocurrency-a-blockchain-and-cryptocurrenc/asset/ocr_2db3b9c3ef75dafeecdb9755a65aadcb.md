The Chi Token is an ERC20 token minted using a smart contract based on the Solidity programming language. The code shown here is the intellectual property of Chi Management Ltd. Prior consent is required to adapt the code.

```
pragma solidity ^0.5.0;
contract ChiToken {
  /* This creates an array with all balances *
  mapping(address => uint256) public balanceOf;
  string public name;
  string public symbol;
  uint8 public decimals;

  /* Initializes contract with initial supply tokens
  to the creator of the contract */
  constructor(
    uint256 initialSupply,
    string tokenName,
    string tokenSymbol,
    uint8 decimalUnits
  ) public {
    balanceOf[msg.sender] = initialSupply; // Give the creator all initial tokens
    name = tokenName; // Set the name for display purposes
    symbol = tokenSymbol; // Set the symbol for display purposes
    decimals = decimalUnits; // Amount of decimals for display purposes
  }

  /* Send coins */
  function transfer(address _to, uint256 _value)
  returns (bool success) {
    require(balanceOf[msg.sender] >= _value); // Check if the sender has enough
    require(balanceOf[_to] + _value >= balanceOf[_to]);
```