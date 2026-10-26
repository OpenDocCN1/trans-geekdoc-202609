**TABLE 9.1**  
**Properties of a Transaction in Ethereum Platform**

| Property | Description |
|---|---|
| Nonce | Number of many times the sender has sent a transaction |
| To | Address of the account the money is transferring to |
| Value | Amount of the ether to be send to the desired address |
| gasPrice | Amount of ether the sender is willing to pay per unit gas for handling a particular transaction |
| startGas/gasLimit | Unit of gas that a transaction can consume |

There are three types of transactions that can be executed in Ethereum platform:

+   1. Transfer of ether from one account to other accounts.
+   2. Deployment of a smart contract.
+   3. Invoking a function within a contract.

A transaction has some important properties related to it, as illustrated in Table 9.1. The v, r, and s account properties relate to cryptographic [1] pieces of data that can be used to generate the sender’s account address.

# 9.3  SMART CONTRACT ACCOUNT

Smart contracts can be considered as a way to automate some of the conditions and obligations described in the contract. Every smart contract has its own address and is useful while sending or receiving the ether. Smart contracts can identify the person who calls it, by this we can impose the privileged access to the contract.

Every smart contract account has four properties associated with it. These three properties are field, balance, storage, and code. Table 9.2 gives the description of each of these properties.

# 9.3.1  SMART CONTRACT STRUCTURE

The code shown in Figure 9.1 depicts the basic structure of smart contract.

The following are the features of above written smart contract:

+   1. The first line simply specifies that the source code is written for Solidity version 0.5.2. This is to make sure that the contract does not behave abnormally with a new compiler version. The keyword pragma can be used

**TABLE 9.2**  
**Properties of Smart Contract account**

| Field | Description |
|---|---|
| Balance | Number of ether any particular account possess |
| Storage | Data storage for the contract |
| Code | Raw machine code for the contract |