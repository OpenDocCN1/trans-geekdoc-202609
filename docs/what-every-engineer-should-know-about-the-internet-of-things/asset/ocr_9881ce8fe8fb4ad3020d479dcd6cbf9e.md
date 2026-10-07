# What Every Engineer Should Know About IoT

There are general permission type distinctions for current blockchain architectures:

+   - Permissionless, public or open refers to blockchains where access is not restricted to a specific set of vetted participants. In these types of blockchain, participants do not know and trust each other
- "Permissioned", "private" or "closed" refers to blockchains where access is restricted to a specific set of vetted participants (Hileman & Rauchs, 2017). These blockchains operate in an environment where participants are already known, and there is a level of trust among them; this removes the need for a native token to incentivize good behavior. Participants are held liable through off-chain legal contracts and agreements and are incentivized to behave honestly by the threat of legal prosecution in the case of misbehavior (Hileman & Rauchs, 2017)
- "Consortium" refers to a blockchain where the architecture could be private or hybrid (public and private). This type of blockchain uses features such as permission restriction, multiple controlling authorities; they allow easy, yet controlled information sharing between various stakeholders and more.

# 11.2 THE IDEA OF CRYPTURRENCIES

The first application on a blockchain is Bitcoin, the most famous cryptocurrency. The basic ideas on which Bitcoin (and the other cryptocurrencies) are based on the following:

+   - The coin is a registration in a public register (the blockchain), shared on the Internet by thousands of nodes which create a P2P network, without any centralized controller.
- Each record has a public address (derived from a public cryptographic key).
- The owner of the coin owns the associated private key.
- The currency can be transferred only using this private key to another address.
- This transfer (transaction) is validated and registered in the blockchain.

Verifying transactions and creating blocks is a computational cost which must be remunerated. For each transaction, it is necessary to verify that (1) the entity which activates it is really the owner, (2) the relative currency has already been spent, and (3) there are no other errors.

The network is democratic and anonymous, and the nodes do not get information about their identity; anyone able to access the network can validate blocks.
an attacker could create many nodes (thousands or millions) seemingly independent nodes and take control of the network. This attack is called “Sibling Attack”, and a fundamental constraint is that the system must be able to work even in the presence of attacks and fraud attempts. Trusting all the participants in the network is not a requirement for the system to work.