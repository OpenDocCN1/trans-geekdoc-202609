```
truffle(develop) = web3.from(web3.eth.getBalance(web3.eth.accounts[0],'ether').toNumber());
100
truffle(develop) =
```

Figure 19.12

To check the balance of Web3.eth.accounts[0] in MetaCoin(not ether), use the following command:

```
MetaCoin.deployed().then(function(instance){return instance.getBalance.call(web3.eth.accounts[0]);}).then(function(value){return value.toNumber()});
```

The output is as shown in Figure 19.13.

```
truffle(develop) > MetaCoin.deployed().then(function(instance){return instance.getBalance.call(web3.eth.accounts[0]);}).then(function(value){return value.toNumber()});
1000
truffle(develop) =
```

Figure 19.13

# Send Coin with the sendCoin Function

To send metcoin from account[0] to account[1], use the following command

MetaCoin.deployed().then(function(instance){return instance.sendCoin(web3.eth.accounts[1], 100));});

To send metcoin from account[m] to account[n], use the following command

MetaCoin.deployed().then(function(instance) { return instance.sendCoin(web3.eth.accounts[n], 10, {from:web3.eth.accounts[m]});});

Example