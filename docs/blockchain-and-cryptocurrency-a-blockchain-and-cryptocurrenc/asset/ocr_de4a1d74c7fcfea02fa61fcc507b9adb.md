# Deploy to Popsten

Run a node connected to Popsten and specify the address of the default (first) account to unlock. You will be prompted for a passphrase.

```
geth --unlock <account> --testnet --rpc --rpcapi
eth,net,web3
```

Configuration for the Popsten network:

```
module.exports = {
  networks: {
    popsten: {
      host: "127.0.0.1",
      port: 8545,
      network_id: 3,
      gas: 4700000
    }
  }
}
```

Deploy to the Popsten network:

```
truffle migrate --network popsten
```

# Deploy to Rinkeby

Rinkeby network is available only using geth client.

```
geth --unlock <account> --rinkeby --rpc --rpcapi
eth,net,web3
```

Configuration for the Rinkeby network:

```
module.exports = {
  networks: {
```