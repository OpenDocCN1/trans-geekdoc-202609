# FGUGChain: Blockchain Application Framework

universal gates for Boolean circuit construction. For an example, AND circuit suitable for SCD construction built with only Gar is shown in Appendix 9.2, and an illustrated example is given by Innocent et al. (2019a). The gate-type G in the SCD format of FastGarble (Bellare et al., 2013) $f_{iG}=(n,q,A,B,G)$ can be removed to form the SCD construction of FastGarble with universal gates 5-tuples as $f=\{n,q,A,B\}$. The storage size required for the application reduces as the gate need not be stored; a constant value corresponding to the gate type used in protocol. Also, checking of respective gate type is not needed for every gate during garbling, which contributes marginally for the improvement of time complexity. FastGarble with universal gates uses the point-and-amble, garbled row reduction of two rows per gate (GRR-2), AES-NI, and BKC. Fast-XOR technique is negated as there are no XOR gates available in the circuit. As batch-key cipher is used, it requires only two complex encryption/decryption calls per batch of gates. Use of the gate type (either NAND and OR) always ensures the encryption of every first gate of the batch with dual-key cipher, and thus new encryption per batch is applied. Also, even though representing the Boolean circuit with universal gates increases the number of gates, usage of batch-key cipher and GRR-2 design makes it approximately 66% faster than the protocols for garbled construction. This makes it a better choice to be used in FGUGChain framework.

# 9.2.2.2 Interlinked Computing Nodes/Parties with Private Data

Interlinked computing nodes are the parties involved in multiparty computation with their private data. With FGUGChain framework, they are able to compute on their private data without revealing it to a trusted third party on a decentralized environment.

# 9.3 CONCLUSION

The FGUGChain framework discussed in this chapter gives a theoretical exposure to the framework, and it can be used to develop various decentralized applications with privacy. The FastGarble with universal gates framework incorporated to include privacy by the use of secure communication is 66% faster than the existing practical implementations on secure computation. As well, it uses only two ciphertexts per gate and is proven to be secure. The blockchain technology provides better decentralization and allows only the honest parties to be part of the computing environment. Thus, we can say that FGUGChain acts as a platform for generating distributed decentralized applications with privacy by intertwining secure computation with blockchain technology.

# APPENDIX 9.1

# YAO's Garbled Circuit Construction

The first step in YAO's 2PC design under computational model of security is the construction of GC, followed by OT. While Boolean circuits, the underlying computation function f(x,y) is represented in circuit form by the first party Alice.