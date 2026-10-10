
```solidity
uint8 decimalUnits
) public {
    balanceOf[msg.sender] = initialSupply; // 给创建者所有初始代币
    name = tokenName; // 设置显示的名称
    symbol = tokenSymbol; // 设置显示的符号
    decimals = decimalUnits; // 设置显示的小位数
}

/* 发送代币 */
function transfer(address _to, uint256 _value)
returns (bool success) {
    require(balanceOf[msg.sender] >= _value); // 检查发送者余额是否足够
    require(balanceOf[_to] + _value >= balanceOf[_to]);
    // 检查溢出
    balanceOf[msg.sender] -= _value;
    // 从发送者处扣除
    balanceOf[_to] += _value;
    // 向接收者加上相同金额
    return true;
}
```
