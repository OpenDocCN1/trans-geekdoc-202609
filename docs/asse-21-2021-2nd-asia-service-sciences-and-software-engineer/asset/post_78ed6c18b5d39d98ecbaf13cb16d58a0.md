
- The structure of $B_f$ is correct, and the structure will be defined in 4.1;
- The timestamp in the fast block consists with the value of slot;
- For each fast block $B_p$ in Parents[$B_f$], |Slot[$B_f$]-Slot[$B_p$]| ≤ 2 · Δ, where Δ is the maximum network delay.

### DEFINITION 3.3. Pending fast block set pendingSet[Ĝ]

We define that the pending fast block set consists of all the valid fast blocks whose reception time are later than the maximum delay, and we denote this set as pendingSet[Ĝ].

### DEFINITION 3.4. Candidate fast block set candidateSet[Ĝ]

We define that the candidate fast block set consists of all the valid fast blocks that are received in Δ slots, and we denote this set as candidateSet[Ĝ].

### DEFINITION 3.5. Confirmed fast block set confirmedSet[Ĝ]

If the number of Density[$B_f$, Slot[$B_f$] + Δ, Slot[$B_f$] + Δ + T)] is larger than Th, where Th and T are systemic parameters that will be discussed in section 5. We regard the valid block as a confirmed fast block. All the confirmed fast blocks constitute the confirmed fast block set denoted as confirmedSet[Ĝ]. And the sorting is only for the fast blocks in confirmedSet.

### DEFINITION 3.6. Fast block sequence Seq[Ĝ]

Once getting the confirmed fast block set, we need to order these fast blocks to get a fast block sequence denoted $S = \text{Seq}[\hat{G}]$. In the sequence, every fast block $B_f$ has a unique sequence number, that is Index[$B_f$]. And a DAG structure corresponds to a fast block sequence that would extend with the DAG grows, but the earlier part of the sequence will not change. And we use len[S] to denote the number of fast blocks in S. Like slow chains, the notation $S^{[\kappa]}$ denotes the entire sequence S except the trailing κ fast blocks, and symbol $\preceq$ denotes the prefix relationship.

### DEFINITION 3.7. Finality state

If a fast block $B_f$ gets its sequence number Index[$B_f$] of in sequence Seq[Ĝ], this block has reached its finality state.

Here, the finality means the block can be reverted with negligible probability.

**Security definitions.** We assume that there is a DAG structure Ĝ in every party’s view, and accordingly, there is a fast block sequence Seq[Ĝ]. A fast blockchain protocol should satisfy unique sequence number, stable finality state, sequence growth, sequence quality and sequence common prefix. Intuitively, unique sequence number requires that a fast block in Seq[Ĝ] must have a unique sequence number. Stable finality state requires the sequence number of a fast block cannot be changed. The remaining three properties are similar to the three security properties for slow blockchain. We will formally define these properties below.

- **Unique sequence number:** For any two different fast blocks $B^1_f$ and $B^2_f$ in a Seq[Ĝ], Index[$B^1_f$] ≠ Index[$B^2_f$]. And if Slot[$B^1_f$] < Slot[$B^2_f$], Index[$B^1_f$] must be less than Index[$B^2_f$].
- **Stable finality state:** For any fast block $B_f$ in Seq[Ĝ], the possibility that Index[$B_f$] changes is negligible.
- **Sequence growth:** The property needs a parameter $g \in \mathbb{R}$ that is the minimum growth rate. For any two honest parties P1 with local $\mathbf{S}_1 = \text{Seq}[\hat{\mathcal{G}}_1]$ at slot $s_1$ and P2 with local $\mathbf{S}_2 = \text{Seq}[\hat{\mathcal{G}}_2]$ at slot $s_2$, where $s_1 < s_2$, len[$\mathbf{S}_2$] − len[$\mathbf{S}_1$] ≥ g · (s2 − s1).
- **Sequence quality:** The property needs parameter $\mu \in \mathbb{R}$ that is the proportion of honest parties, and parameter $\ell \in \mathbb{N}$. For any honest party P with local $\mathbf{S} = \text{Seq}[\hat{\mathcal{G}}]$ at slot $s_1$, it holds that for large enough ℓ consecutive fast blocks of $\mathbf{S}$, the ratio of honest fast blocks is at least $\mu$.
- **Sequence common prefix:** For any honest player P1 with local $\mathbf{S}_1 = \text{Seq}[\hat{\mathcal{G}}_1]$ at slot s1 and P2 with local $\mathbf{S}_2 = \text{Seq}[\hat{\mathcal{G}}_2]$ at slot s2, where $s_1 < s_2$, it holds that $\mathbf{S}_1^{[\ell]} \preceq \mathbf{S}_2$.

# 4 THE DETAILS OF OUR PROTOCOL

The basic idea of our protocol called Plume is showed in Fig.1. Plume is a combination of traditional single-chain consensus protocol and DAG structure. There are two kinds of blocks in Plume. One is the traditional block denoted as $B_R$ that needs more time to generate in order to guarantee the integrated security. Another is the DAG block denoted as $B_f$ that can be generated fast. Plume is mainly divided into four parts, those are (1) generating randomness from slow blockchain and electing committee to generate fast blocks, (2) receiving fast blocks and ordering them, (3) generating fast blocks and organizing them into DAG structure, (4) storing the current state of DAG in slow blocks to speed up synchronization of new parties. Next, we will describe what the parts do.

## 4.1 The structure of a fast block

In this section, we will define the structure of fast blocks. We denote the blocks generated by committee as fast blocks, because these blocks can be generated in every slot without considering the maximum network delay. The header structure of fast block is showed in Table 7. We can see that the structure is different with the traditional blocks except the merkle root. The “(y, π)” can be equated with the “nonce” in traditional block which is defined in table 7 explicitly. Both of them are used for proving the party is qualified to generate these block. And the “slot” is utilized to verify the randomness r used to compute $B_f$ is correct. “reference number” is to declare how many fast blocks are referenced by this block, and the values need to match the content of “reference hash”. It should be noted that “reference” corresponds to the directed edges of DAG, and every fast block corresponds to a vertex in DAG. txlist is the list of transactions in the fast block that would be consistent with the merkle root. σ is a signature on the fast block, in order to prevent adversaries from using the (y, π) on other fast blocks.

## 4.2 Getting randomness from slow blockchain and elect committee

There are many researches on extracting randomness from blockchain, such as [4] and [3]. These research used the inherent randomness of the mining process itself. [4] proposed there are sufficient entropy in a block header so that an extractor can get an unbiased randomness from a block header. But malicious miners have the ability of selecting preferable blocks to broadcast, then there will be biases on the whole.

![](img/0ee32e7d194c7c0bdee0ce0091187b7c_3_0.png)

**Figure 1: Overview of our protocol.**

**Table 1: The structure of a fast block.**

| Item | Description |
|---|---|
| $(y, \pi)$ | A proof that the party is qualified to generate this fast block. |
| $r$ | The randomness used for election. |
| slot | The slot when the fast block generated. |
| merkle_root | The merkle root of transactions. |
| reference_number | The number of fast blocks that are referenced by this block. |
| reference_hash | The hash of fast blocks that are referenced by this block. |
| txlist | The list of transactions. |
| $\sigma$ | A signature on the fast block. |

From the previous researches, we can see that it is necessary to use sufficient blocks to generate an unbiased randomness. But in Plume, we do not need an unbiased randomness, we just need a randomness that has sufficient entropy so that adversaries cannot manipulate the randomness to let the proportion of the adversaries in committee above threshold. We get our randomness from a confirmed slow block by computing the hash of the block, i.e., $r_i = H(B_i^s)$. And we switch to the next slow block to generate the next confirmed randomness a certain interval that is $E$ slots, where $E$ is a systemic parameter. More precisely, we get our first randomness $r_0$ from the genesis block $B_0^s$ of a confirmed slow blockchain, after $E$ slots where $E$ is larger than the interval of generating a slow block, we get the second randomness $r_1$ from the block $B_1^s$, and so on.

Every party in the network can become a committee in $slot_j$ by computing $(y, \pi) = \text{VRF}_{s,k}(slot_j || r_i)$, as long as his public key is registered in block $B_j^s$ or the blocks before it, where VRF (Verifiable Random Functions)[11] is firstly proposed by Miceli in 1986. If $y < D$ where $D$ is the difficulty, the party can generate a fast block in $slot_j$, and how to generate it will be described in section 4.4.

## 4.3 Receiving fast blocks and ordering them

For a party that is always online, he will receive the fast blocks generated by others, and he needs to order them according to the *slot* recorded in the block. Once he receives a fast block $B_F$, the first thing he needs to do is to check the validity of the block according to definition 3.2. If the fast block is valid, he will decide which set the fast block belongs to. Because of network delay, there is the possibility that a party receives a fast block before receiving its ancestors. It is necessary to check if the ancestors have been received. If every block in Ancestor[$B_F$] and $B_F$ are all received in $\Delta$ slots, the party will add $B_F$ and blocks which is in Ancestor[$B_F$] that received in time but have not been in candidateSet, to candidateSet. If every block in Ancestor[$B_F$] are received in $\Delta$ slots but $B_F$ is
