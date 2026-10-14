than the minimum amount will get richer and below this threshold, poor remain poor. After a period of time, this gap between poor and rich will get bigger and only rich nodes will get to control the network.

# 25.6.3 Smart Contracts

A smart contract is an important part of blockchain technology. A smart contract is a digital contract that can execute itself. It may consist of a transaction that is triggered by a certain event. The main purpose of smart contracts is to eliminate the requirement of any third party completely. Before these smart contracts were included, the traditional way to send or receive funds was to approach a third party. With the inclusion of smart contracts, the transactions are programmed to be executed once a certain condition is met without any human intervention. Below is an extract code of a smart contract.

```
function payOut(address _recipient, uint _amount) returns (bool) {
    if (msg.sender != owner || msg.value > 0 || (payOwnerOnly &&
    _recipient != owner))
    throw;
    if (_recipient.call.value(_amount)()) {
    PayOut(_recipient, _amount);
    return true;
    } else {
    return false;
    }
}
```

These smart contracts contain a certain set of instructions which may further be directed to perform some calculations, store information or make the transaction from one account to another.

Smart contract code acts like terms and conditions which, once uploaded to blockchain, cannot be altered. This gives you the assurance that the code will do exactly what it has been programmed for. Smart contracts give strength to blockchain, for example, instead of creating a different blockchain for every application, it can be done by creating one blockchain with different smart contracts for every application. Smart contracts also allow you to create smaller subcontracts. Suppose you have two smart contracts, one contains the ownership of your actual currency (let's say INR) and another contains the ownership of real estate. You can create a new smart contract which acts as an escrow for the two previous contracts. You can program the third contract in a way which allows it to purchase real estate without any third intermediate agency.