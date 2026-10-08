![](bbox=[0.078, 0.203, 0.655, 0.428])

Figure 6.2 Transaction Flow

# Phase 2 Transactions Simulation

At this phase, the endorsers will simulate the proposed transactions, without updating the ledger. The endorsers must hold smart contracts to simulate the transaction proposals. In the simulation process, the endorsing peers will capture the set of Read and Written data, known as **RW Sets.

RW sets contain data that that was read from the current world state while simulating the transaction, as well as data that would have been written to the world state had the transaction been executed. The endorsing peers then sign these RW sets and send them back to the client application for use in the next phase of the transaction flow, as shown below: