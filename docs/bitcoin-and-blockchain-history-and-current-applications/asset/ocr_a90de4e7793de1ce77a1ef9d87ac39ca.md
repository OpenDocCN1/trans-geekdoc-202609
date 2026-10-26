```
```javascript
accounts=await web3.eth.getAccounts();
});
describe('contract_name', () => {
it('deploys a contract', () => {
console.log(accounts); }); });
```
```

# 9.6  METAMASK EXTENSION

To deploy a smart contract, an account in Ethereum client like Metamask [15] or Mist Browser is required with some amount of ether. Metamask is a crome extension that permits common people to interconnect with Ethereum network. It can be used as Ethereum client. Metamask setup on the machine can be done by installing it from crome web store.

Metamask accounts have three distinct features associated with it. Figure 9.8 depicts the basic structure of Metamask with three distinct features.

Account address is something similar to username or email address that can be shared with anyone. Public key and private key together get combined to form password of the source and authorized the sending of funds from user’s account to other account. All the three entities, namely account address, public key, and private key, are stored as hexadecimal number. When that hexadecimal number is copied to a JavaScript console, it automatically gets converted to base ten number, which is incomprehensively very large. This generated number uniquely constituent the private key. Private Key is not to be shared with anyone because if anyone ever gets to know it, then they can easily take all the funds that are in our contract.

Suppose we have to login into g-mail and yahoo mail, for the network we need different email accounts. But in Ethereum, one account is used for multiple networks

![](bbox=[0.376, 0.603, 0.621, 0.885])

**FIGURE 9.8**  Metamask features.