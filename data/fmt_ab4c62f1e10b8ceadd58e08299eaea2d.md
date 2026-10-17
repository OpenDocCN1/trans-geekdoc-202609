
```solidity
function kill() public onlyOwner { // onlyOwner 是自定义修饰符
    selfdestruct(owner); // owner 是所有者的地址
}
```
