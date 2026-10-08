Besides that, you need to install Visual Studio 2019. I shall skip the technical details as this is a book written for non-technical guys.

# ### 3.2.3 The Smart Contract Code

A smart contract is a collection of code (its functions) and data (its state) that resides at a specific address on the Ethereum blockchain. Let us begin with the most basic basic example. It is fine if you do not understand everything here. However, if you are keen to test it out, you can enter the following code in the Remix IDE and save the file as MyStorage.sol.

```
pragma solidity ^0.5.0;
contract MyStorage {
    uint storedData;
    function set(uint x) public {
        storedData = x;
    }
    function get() public view returns (uint) {
        return storedData;
    }
}
```

# ### 3.2.4 Understanding the Code

The first line simply states that the source code is written for Solidity version 0.5.0 or anything newer that does not break functionality. This is to ensure that the contract does not suddenly behave differently with a new compiler version. The keyword pragma is called that way because, in general, pragmas