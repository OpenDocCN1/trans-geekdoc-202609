214

Blockchain

![](bbox=[0.109, 0.091, 0.89, 0.513])

FIGURE 12.4
Smart contact based access management.

If the details get matched, then the edge device allows the user to access the restricted resource. In the admin part, the admin will be responsible for registering users by their identity attribute (ID) and biometric details, updating the required fields e.g ID or biometric details, moder the permission giving access to someone or revoking access and deleting someone's account could be performed by admin using only the web or other interfaces connected using available open-source Ethereum client. Web3 js is a secure Ethereum client to connect with a local or remote Ethereum blockchain. Figure 12.4 shows the layout of our proposed model.

Now we will look into the core code, which has been written using Solidity version 0.8.4. At first, we need to define the data structure for storage, as shown below.

```
contract SecureStore {
  struct User {
    uint id;
    string name;
    string passwd_biometric;
  }
```

For the admin management, we have to define many CRUD operation functions, to modify the behavior of the smart contract residing inside the Ethereum blockchain.