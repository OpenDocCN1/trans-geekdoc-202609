```
pragma solidity ^0.5.0;
contract Multiply {
    uint mul;
    function getAnswer(uint x, uint y) public {
        mul = x * y;
    }
}
```

FIGURE 8.14 Function parameters.

In the previous example, we have assigned variable mul as a product of x and y. Now, what if we want to return its value? We can do so by writing a return statement at the end of the function. Refer to the example shown in Figure 8.15.

# 8.7.5 FUNCTION MODIFIERS

The function modifier enables us to control the behavior of a function. It is used for a condition check before the function execution. It reduces the amount of duplicate code or logic. The special symbol “_” is mandatory for a modifier definition. At “_,” the function source is merged with the modifier code.

Let’s understand with the example in Figure 8.16.

```
pragma solidity ^0.5.0;
contract Multiply {
    uint mul;
    function getAnswer(uint x, uint y) public {
        mul = x * y;
        return mul;
    }
}
```

FIGURE 8.15 Return statement.

```
contract Owner {
    address ownerAddress;
    constructor() {
        ownerAddress = msg.sender;
    }
    // Can only be called by the owner
    function test() public onlyOwner {
    }
    // Check if the function is called by the owner of the contract
    modifier onlyOwner() {
        require(msg.sender == ownerAddress);
        _;
    }
}
```

FIGURE 8.16 Function modifiers.