MetaCoin.deployed().then(function(instance) { return
instance.sendCoin(web3.eth.accounts[1], 1000, {from:
web3.eth.accounts[0]});
});

The output is as shown in Figure 19.14.

```
PROBLEM DEBUG CONSOLE TERMINAL .node
1000
truffle(deploy)> MetaCoin. deployed().then(function(instance) { return instance sendCoin(w
from: web3.eth.accounts[0]);});

receipt {
  transactionHash: '0x...',
  transactionIndex: 0,
  blockHash: '0x...',
  blockNumber: 11,
  gas: 5107,
  gasUsed: 5107,
  contractAddress: null
}
```

Figure 19.14

The check whether the transaction is successful , we can check
t balance of both accounts. (Note that this is the MetaCoin
balance, not the ETH balance)

MetaCoin.deployed().then(function(instance){return
instance.getBalance.call(web3.eth.accounts[0]});).then(fu
ction(value){return value.toNumber()});
The output is as shown in Figure 19.15.

```
truffle(deploy)> MetaCoin.deployed().then(function(instance){return
instance.getBalance.call(web3.eth.accounts[0])});
).then(function(value){return value.toNumber()});

1000
truffle(deploy)>
```

Figure 19.15

To convert MetaCoin to Ether, use the following code:

MetaCoin.deployed().then(function(instance){return
instance.getBalanceInEth.call(web3.eth.accounts[n]}).th
en(function(value){return value.toNumber()});