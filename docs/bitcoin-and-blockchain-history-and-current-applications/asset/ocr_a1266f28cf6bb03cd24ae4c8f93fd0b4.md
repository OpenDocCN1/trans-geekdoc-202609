the number of peers required to sign a transaction. When deploying the chaincode, this endorsement policy is defined. Therefore, different channels can have different endorsement policies.

# Transaction Flow (Step 3): Ordering

After receiving endorsed transactions and signed RW sets, the client application submits the endorsed transaction and RW sets to the ordering service. Ordering service collects all the transactions made in a particular time interval, orders all the transactions of that particular channel, and groups them all into a block. The ordering service can be a group of orderers, does not process transactions or maintains a shared ledger. The ordering service only specifies the order in which the transactions will be committed to the ledger.

Figure 12.6 depicts how a user/client sends endorsed transactions received from endorsing peers and sends them to ordering service.

# Transaction Flow (Step 4): Broadcasting

The ordering system takes the accepted transactions and RW sets, ordering this information into a block, and distributing the block to all peers who commit.

The ordering system, which consists of a group of orderers, does not process transactions, smart contracts, or the distributed ledger is maintained. The ordering system recognizes the transactions that have been approved and determines the order in which those transactions must be appended ledger and world state in upcoming steps.

Figure 12.7 depicts how an ordering service orders transactions into a block and broadcasts the block to the other peers in the network.

# Step 5: Committing and Ledger Updating

Committing peers validate every transaction in the block separately. Considering the Read Write sets, the peer's checks if the current world state and the read set are same as shown in Figure 12.8. Then validates the transaction by verifying all the endorsements required to satisfy the endorsement policy.

After the validation process, shown in Figure 12.8, the ledger is updated. Ledger updating by appending the block is done synchronously by all the peers. Invalid transactions detected are marked as invalid, still present in the block but do not affect the world state. Committing peers are the one updating and maintaining the shared ledger. They also notify the client application about the success or failure of

![](bbox=[0.13, 0.75, 0.85, 0.9])

FIGURE 12.6 Application SDK to ordering service.