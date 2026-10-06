148

Blockchain Technology

the blocks. The computing nodes return the result as well as the proof of comput-, and they are also packed into the blocks by the producer. Validity of the block is determined by other nodes, just by verifying the proof, which reduces the complex, redundant computations on each node, and hence the block verification time. A new block is added to the chain once the verification process is completed.

# 9.2.2 OFF-LINE PHASE

The off-line phase or the off-chain computations carry out the complex multiparty computation protocol. Yao's GC construction (Lindel and Pinkas, 2009); Innocent and Sangeeta, 2014a; 2014b) plays a vital role in multiparty computation protocols. The underlying computation is implemented in a Boolean circuit, divided into multiple subcircuits, and are then sent to computing nodes and executed in parallel. Each circuit is sent to computing nodes to maintain certain level of redundancy and availability guarantee. The garbled circuit selects tokens for each wire in the Boolean, encrypts the output token with that input tokens for each gate, the encrypted tokens are garbled by gate, and the garbled circuit is generated (Lindell and Pinkas, 2009); Innocent and Sangeeta, 2014a, 2014b; Bellare et al., 2012). The garbled circuit evaluator uses oblivious protocol and deciphers the garbled circuit to obtain the required result (Lindell and Pinkas, 2009). The components of off-line phase are described in the following sections.

# 9.2.2.1 Garbled Circuit Construction Using FastGarble with Universal Gates

The garbled circuit construction here uses the FastGarble with universal gates framework (Innocent et al., 2019a). Here, instead of different types of gates, any one of the universal gates (NAND/NOR) is used for Boolean circuit generation, and hence for garbled circuit construction. Also the batch-key cipher optimization for garbled circuit construction is used along with point-and-merge (Noar et al., 1999), garbled-reduction (Pinkas et al., 2009), dual-key cipher with fixed-key block cipher with Advanced Encryption Standards-New Instructions (AES-NI) and Simple Circuit Description (SCD) (Bellare et al., 2013) optimizations. The FastGarble with universal gates is proved to be more efficient in terms of time complexity by execution of protocol, and also requires only two ciphertexts per gate for communications (Innocent et al., 2019a). Overall, the use of FastGarble with universal gates framework improves the efficiency of multiparty computation application.

# 9.2.2.1 Universal Gates on Garbled Circuit Construction

The NOR and NAND gates are called the universal gates as the other gates namely, AND, OR, XOR, and NOT can be derived from these gates. FastGarble with universal gates framework is built on FastGarble framework and uses only the universal gates for Boolean circuit construction. Circuit construction with one universal gate comes with the advantage that a single type of gate is used for the circuit construction. This eliminates the need for gate array G in SCD. FastGarble with universal gates framework is built on FastGarble framework and uses only the