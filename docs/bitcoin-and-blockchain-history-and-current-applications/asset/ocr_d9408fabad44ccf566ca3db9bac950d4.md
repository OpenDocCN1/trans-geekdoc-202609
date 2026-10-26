![](bbox=[0.139, 0.094, 0.858, 0.523])

**FIGURE 12.19**  Crypto-config folder structure.

# ### 12.4.4.1 Configtx.yaml Configuration

Configtx.yaml configuration is used to generate the channel transactions, which are the metadata about the channel rather than the ledgers state data. Both the channel transactions and the normal transactions are stored on the same blockchain. The difference is that each channel transaction is stored in a special block that contains not only the incremental configuration update but the entire configuration as well. When a peer or client needs to know the channel’s configuration, it only needs to get the latest channel transaction block.

Configtx.yaml defines which elements to use with your network and is passed to configtxgen in order to create genesis block and channel artifacts.

We can split the configtx.yaml file into five different blocks:

+   - Organizations block.
+   - Capabilities block.
+   - Applications block.
+   - Ordererblock.
+   - Profiles block.

Figure 12.20 depicts the defining organization configuration in configtx.yaml