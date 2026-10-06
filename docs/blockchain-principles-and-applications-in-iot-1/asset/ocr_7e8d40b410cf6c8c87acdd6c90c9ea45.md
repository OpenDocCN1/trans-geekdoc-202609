146

Blockchain

![](bbox=[0.105, 0.115, 0.854, 0.396])

**FIGURE 9.5
Transaction proposal.

![](bbox=[0.105, 0.476, 0.854, 0.735])

**FIGURE 9.6
Transaction execution.

# 9.3.3.4 Step 4: Order Transaction

After receiving the sufficient responses from the endorsers that satisfy the endorsement policy, it will send the transaction that contains responses to the order. In our case, if the application receives responses from E1, E2, and E3, it will submit those responses in the form of a transaction to the ordering service. These submissions of transactions to the ordering service will be happening from multiple client applications and users simultaneously across the network. The ordering service will order these transactions and it will make sure