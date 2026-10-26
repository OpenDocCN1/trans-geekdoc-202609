```
```solidity
pragma solidity ^0.5.0;

contract AccountBalance {
    mapping(address => uint) public balance;

    function updateBal(uint newBal) public {
        balance[msg.sender] = newBal;
    }
}
contract Update {
    function updateBal() public returns (uint) {
        AccountBalance accountBalance = new AccountBalance();
        accountBalance.updateBal(15);
        return accountBalance.balance(address(this));
    }
}
```
```

**FIGURE 8.7**  Mappings in Solidity.

# ### 8.6.3  Struct

A struct is a collection of key-value pairs that can hold different value types. It is generally used to represent a singular entity.

Syntax for struct:

```
```solidity
struct structName {
        type1 typeName_1;
        type2 typeName_2;
        type3 typeName_3;
}
```
```

Let us understand with an example.

```
```solidity
struct Car {
        string make;
        string model;
uint value;
    }
```
```

Here in this example, we have designed a struct, car, which contains three attributes make, model, and value.

At this point, you might notice some resemblance between struct and mappings, although there is a difference. Mapping is used to represent a collection of things, whereas a struct is used to represent a singular thing. For instance, in mapping, we can store a collection of cars rather than just a singular car [1].

Notice the code in Figure 8.8 to understand the functioning of structs in solidity.

# ### 8.6.4  Enum

Enum is a user-defined data type in solidity. It contains a restricted set of constants from which the value is assigned to a variable. Enum limits the variable to hold any unspecified value, thus reducing bugs. Suppose you are creating a clothing