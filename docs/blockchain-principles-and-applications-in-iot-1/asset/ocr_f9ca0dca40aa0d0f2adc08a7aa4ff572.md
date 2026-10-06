# Blockchain

![](bbox=[0.248, 0.115, 0.751, 0.43])

FIGURE 1.5
Blockchain components.

block with its position in the chain, the header hash and block height both are maintained. For a thorough understanding of blockchain, these fields will be shown in Figure 1.6 in detail.

# 1.8.1.1 Block Header

1.8.1.1 Header hash

A header hash is used to recognize the block with a cryptographic digest method and it is also used as an input variable. Each entire node computes a new block when it is received. Then it stores it in a separate database as part of the block metadata.

1.8.1.1.2 Height

The blocks are added to the chain in a chronological order. Using this order, one number is issued to each new block [35]. The height is the difference between the numbers of the last and first blocks. In this case, a fork in the chain happens.

1.8.1.1.3 Hash of the previous block

The previous block's hash is given in the header to allow the block to connect to the one before it.

1.8.1.1.4 Nonce

A nonce is an integer value to adjust the header hash's output. The header hash starts with a series of 0's, the miner will iterate the nonce until it meets its requirement. When completed, the process of nodes gets a new block. They will only calculate the header hash once to determine if the nonce is valid.