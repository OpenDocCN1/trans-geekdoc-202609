
# Ethereum: The World Computer

For full transparency, all information (code, transactions, and token holdings, for example) is forever memorialized and accessible to all. To uphold the integrity of the state of this computer, each member of the community separately and continuously maintains updated copies of the system.

In the Ethereum universe, this computer is the `Ethereum Virtual Machine` (EVM), and the leaderless community is a network of computers operated by (literally!) anyone who wishes to participate. Each of these computers (also known as `nodes`) stores updated duplicates of the EVM. Anyone may additionally choose to participate as a `mining node`, or `miner`, who is compensated to validate and process computing requests for execution. The software itself is open source and free, though the necessary hardware and electricity are not.

To initiate a computing request, referred to as a `transaction`, you need an account that can receive, store, and send ether (`ETH`), the native cryptocurrency of Ethereum. (These accounts can also deploy and interact with deployed smart contracts.) On Ethereum, this type of account is officially known as an `externally owned account`. When you hear someone mention accounts, they're likely referring to externally owned accounts.

In [Chapter 7](#c07.xhtml), we explain account types, account creation, and account management in greater detail.

![Remember](images/remember.png) All transactions on the EVM must be paid for with ETH. Transactions can entail operations such as:

*   Transferring ETH from one account to another
*   Storing data on the EVM
*   Manipulating existing data

After a requested transaction has been validated and executed — a process that requires network consensus — the new state of the EVM is broadcast and duplicated across the network of nodes. The entire history of transactions is secured on a blockchain-based distributed ledger for anyone to access.

To see how this public ledger works in practice, carry out the following steps to view all transactions data on the EVM since the genesis of the Ethereum blockchain:

1.  **Go to** [`https://etherscan.io`](https://etherscan.io)**.**
2.  **Select the View Txns option from the Blockchain drop-down menu, as shown in** [**Figure 6-1**](#c06.xhtml#c06-fig-0001)**.**

    There, for all the world to see, are all transactions data on the EVM since time immemorial.

    ![Technicalstuff](images/technicalstuff.png) `Txns` is Ethereum's bizarre way of referring to transactions.

![FIGURE 6-1: Viewing transactions data on the Ethereum blockchain.](images/9781119843313-fg0601.png)

[FIGURE 6-1:](#c06.xhtml#rc06-fig-0001) Viewing transactions data on the Ethereum blockchain.

## Ether: The Gas That Fuels Your Transactions

In Ethereum, `gas` is the unit of measurement used to denote the amount of computational work required to process a transaction on the EVM.

When you submit a transaction to the Ethereum network, you must designate two cost-related inputs:

*   **Gas price:** The price, in ETH, that you're willing to pay per unit of gas consumed by your transaction. Higher gas prices make your transaction more attractive to miners, who are compensated to validate and execute transactions.
*   **Gas limit:** The maximum total units of gas you're willing to consume to fully execute your transaction. Higher gas limits ensure that your transaction's computational needs are sufficiently covered for completion.

In general, the speed and successful execution of your request depends on the gas price and gas limit that you designate.

![Technicalstuff](images/technicalstuff.png) Depending on your wallet service and settings, you may notice that gas is denoted in `gwei`, where 1 million gwei is equal to 1 ETH.

### The Journey of a Transaction

To help you better understand the overall likelihood of, and costs associated with, executing a transaction, here's a look at what happens when you initiate a request from your account:

1.  Your transaction is assigned a unique code known as the transaction hash (and abbreviated as `TxnHash`, `TxHash`, or `TXID`).

    For illustrative purposes, here's an example of a `TxnHash`:

    ```
    0x7b91d4f49ccafdb93f2ca89fd57649301331bd691cfe26478822afb468ac9589
    ```

2.  The transaction is broadcast to the greater Ethereum network of nodes.
3.  If valid, the transaction is added to a pool of other pending transactions awaiting execution.

    This pool (shown in [Figure 6-2](#c06.xhtml#c06-fig-0002)) is called the `mempool`. To see the details of a pending transaction, click the `TxnHash`. (See [Figure 6-3](#c06.xhtml#c06-fig-0003).)

    ![FIGURE 6-2: Unconfirmed transactions waiting in the mempool.](images/9781119843313-fg0602.png)

    [FIGURE 6-2:](#c06.xhtml#rc06-fig-0002) Unconfirmed transactions waiting in the mempool.

    ![FIGURE 6-3: A pending transaction, awaiting confirmation and execution.](images/9781119843313-fg0603.png)

    [FIGURE 6-3:](#c06.xhtml#rc06-fig-0003) A pending transaction, awaiting confirmation and execution.

4.  Mining nodes select pending transactions from this pool to form a (not-yet-confirmed) block of transactions.

    (For reasons we discuss further below, miners tend to select pending transactions with higher gas prices.)

5.  Miners race to solve a complex equation — a `proof-of-work (PoW) puzzle`, which requires vast computing power — to earn the right to add and confirm a new block to the Ethereum blockchain.
6.  After a solution is found, the winning miner, who is compensated a block reward, broadcasts its block to the network, the transactions selected for this block are executed (as long as they don't exhaust their respective gas limits), and a new mining race begins.

    [Figure 6-4](#c06.xhtml#c06-fig-0004) shows the earlier pending transaction (introduced above in Step 1), with its corresponding block number, that has been successfully confirmed. This transaction is now a permanent part of the Ethereum blockchain.

    ![FIGURE 6-4: Confirmation of the pending transaction from Figure 6-3.](images/9781119843313-fg0604.png)

    [FIGURE 6-4:](#c06.xhtml#rc06-fig-0004) Confirmation of the pending transaction from [Figure 6-3](#c06.xhtml#c06-fig-0003).

Overall, successful completion of your transaction requires the following conditions:

*   **Your transaction must be valid.** For example, you must have sufficient funds and the appropriate permissions to execute the transaction.
*   **Your transaction must be confirmed and queued for execution.** Your transaction must be selected by a successful mining node that earns the right to append and confirm a new block to the Ethereum blockchain.
*   **Your transaction's total computational complexity must not exceed its designated gas limit.** (You, as the person requesting the transaction, set the gas limit.)

### Compensating the (Proof-of-) Workers: What's in It for the Miners?

For each new block added, the winning miner is paid a block reward, which comes in two parts:

*   **Fixed payment:** At the time of this writing, this fixed portion was 2 ETH.
*   **Individual fees:** These fees are attached to each transaction selected for the block in question.

For instance, the miner of Block #12546760 (see [Figure 6-5](#c06.xhtml#c06-fig-0005)) was compensated approximately 2.32175 ETH. This total block reward is broken down like this:

*   **2 ETH:** The fixed portion of the block reward
*   **0.32175 ETH:** The sum of the individual fees for each of the 236 transactions selected for this block

![FIGURE 6-5: Metadata for Block #12546760.](images/9781119843313-fg0605.png)

[FIGURE 6-5:](#c06.xhtml#rc06-fig-0005) Metadata for Block #12546760.

Naturally, miners want to maximize their potential compensation for a given amount of work: namely, the computing power they expend attempting to solve computationally taxing proof-of-work puzzles.
