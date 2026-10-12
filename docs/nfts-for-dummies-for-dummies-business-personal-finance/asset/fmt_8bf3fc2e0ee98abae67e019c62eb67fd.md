
#### Scenario 1: Successful transaction execution

At the outset, `437,603 (gas limit) * 0.000000018 ETH (gas price) = 0.007876854 ETH` is collected from the originating account, in anticipation of paying for the computing power required to execute this transaction.

Based on the actual gas consumed by the transaction, the miner is compensated a transaction fee in the amount of `0.005540472 ETH`.

The originating account is refunded the unused portion: `0.007876854 - 0.005540472 = 0.002336382 ETH`.

Because the transaction has been successfully executed, the state of the EVM has been altered and is rebroadcast to the network.

#### Scenario 2: Transaction runs out of gas

Consider another transaction submitted with the following inputs:

*   **Gas price:** `0.000025 ETH`
*   **Gas limit:** `25,000`

In this case, during execution, the miner discovers that the transaction’s computational complexity exceeds its designated gas limit of `25,000`, and the transaction runs out of gas (see [Figure 6-10](#c06.xhtml#c06-fig-0010)). The transaction won’t be executed, but the total transaction fee incurred is:

> `25,000 (gas limit) * 0.000025 ETH (gas price) = 0.625 ETH`

![FIGURE 6-10: Gas consumption and the fee for an unsuccessful transaction.](images/9781119843313-fg0610.png)

[FIGURE 6-10:](#c06.xhtml#rc06-fig-0010) Gas consumption and the fee for an unsuccessful transaction.

Although this transaction failed to execute, the miner must still be compensated for the computing work provided:

*   At the outset, `25,000 (gas limit) * 0.000025 ETH (gas price) = 0.625 ETH` is collected from the originating account.
*   Based on the computing power used by the miner in its (unsuccessful) efforts to execute this transaction, the miner is compensated a transaction fee in the amount of `0.625 ETH`.
*   Because the transaction wasn’t executed, the state of the EVM remains as it was before the attempted execution.
*   No funds remain to be transferred back to the originating account.

What a shame to pay `0.625 ETH` for nothing to happen!

![Remember](images/remember.png) The total amount you can be charged for your transaction is capped by the gas price times the gas limit you designate. If your transaction is executed at a lower cost, the gas price times unused gas is returned to your account.

## The Blockchain: Where It’s All Stored and Secured

All confirmed transactions on the EVM are forever memorialized on the Ethereum blockchain — a blockchain-based distributed ledger that acts as a permissionless and shared database synchronized across multiple nodes. Any of the nodes can access the ledger, and updates are copied to all nodes (nearly) simultaneously. The blockchain entails a recordkeeping system that organizes information into chronological blocks of data — in other words, transaction records are grouped into blocks that are regularly confirmed and appended to the existing chain.

Each block is linked to the block preceding it by including a hash of the prior block’s information, forming a *blockchain*. Blocks are often referenced by block height, which represents a block’s location in the blockchain — or, equivalently, the number of blocks preceding it. The *genesis* block is referenced as block `0`.

Each newly formed block requires network consensus before it can be added to the ever-growing chain of confirmed blocks. As always, miners furiously race to solve a computationally taxing puzzle to earn the right to append their block to the existing blockchain. The solution to this puzzle, known as proof of work, is difficult to produce but easy to confirm. For instance, guessing someone’s phone number is an onerous task, but you can easily confirm that you have the correct solution when the phone number is given to you.

When miners reach a solution, they close out the pending block and broadcast the results to the rest of the network, the blockchain is updated, and then a new speed race begins to confirm the next block.

### Ethash and proof of work: What makes Ethereum tamper-proof?

Public blockchains, such as those of Ethereum and Bitcoin, require a consensus mechanism to ensure that the system is:

*   **Fault tolerant:** The system should continue to operate, even in the presence of faulty, failed, or malicious nodes.
*   **Secure:** The rules governing how the network collectively confirms and agrees on the status of the ledger should ensure that, even if there exists a group of dishonest nodes, the records remain tamper-proof.

The consensus mechanism securing the Ethereum blockchain is predicated on a proof-of-work algorithm known as `Ethash` (though developers are working to move the system to a proof-of-stake consensus mechanism). Because proof of work requires solving a long and onerous problem to confirm and execute transactions, closed blocks of information are difficult to alter, because a dishonest node must laboriously and painstakingly find a solution to a new puzzle based on the altered information.

Because proof-of-work systems are, by design, computationally cumbersome, participants have expressed mounting concerns over the energy consumption and environmental unfriendliness of cryptocurrencies whose security protocols depend on proof of work. Companies (see [Figure 6-11](#c06.xhtml#c06-fig-0011)) as well as countries (see [Figure 6-12](#c06.xhtml#c06-fig-0012)) are changing attitudes about cryptocurrency payments and cryptomining. In response, consensus mechanisms based on proof-of-stake (PoS) protocols are increasingly popular. In contrast to proof of work, *proof of stake* requires sufficient stake — measured by factors such as account balance or account age — in the system to confirm transactions.

![FIGURE 6-11: Elon Musk tweets concerns about the sustainability of crypto-mining.](images/9781119843313-fg0611.png)

[FIGURE 6-11:](#c06.xhtml#rc06-fig-0011) Elon Musk tweets concerns about the sustainability of crypto-mining.

![FIGURE 6-12: Crackdowns on crypto-mining activity in the news.](images/9781119843313-fg0612.png)

[FIGURE 6-12:](#c06.xhtml#rc06-fig-0012) Crackdowns on crypto-mining activity in the news.

For years, the Ethereum community has been anticipating Ethereum 2.0, a shift from the current system based on proof of work to one that’s based on proof of stake. Although plenty of speculation takes place around a possible move to Ethereum 2.0 in the near future, as of this writing, proof of work remains the prevailing authority.

### Miners and nonces and bears — oh, my!

The “proof” of a successful miner’s proof of work lies in the block nonce included in the block header. (The block header contains important information about each confirmed block.)

The curiously named *block nonce* is a number that can be found only by way of a computationally intense process of trial-and-error. In this process, miners continually try arbitrary values until they find the special number — the nonce — that, when combined with other important elements of the current block, satisfies a mathematical condition required by the `Ethash` protocol. Thus, this nonce is difficult to find but easy to verify after a solution is announced.

The required mathematical condition is a moving target based on the current block’s difficulty level. Block difficulty is dynamically adjusted based on the previous block’s difficulty level and recent block times. The new difficulty level could be greater than or less than the previous block’s level, a dynamic adjustment ensuring that blocks aren’t formed too quickly or too slowly for a prolonged period as miners enter and exit the network.

![Warning](images/warning.png) Don’t confuse the block nonce with the *transaction nonce*, a number denoting a chronological ordering of transactions sent from a given account.

### How many “confirmations” until I’m actually confirmed?
