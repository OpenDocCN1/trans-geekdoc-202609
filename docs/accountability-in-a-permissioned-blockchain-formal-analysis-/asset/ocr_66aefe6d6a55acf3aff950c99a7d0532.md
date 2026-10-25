# Accountability in a Permissioned Blockchain:
Formal Analysis of Hyperledger Fabric

Mike Graf
Institute of Information Security
University of Stuttgart
Stuttgart, Germany
mike.graf@sec.uni-stuttgart.de

Ralf Küsters
Institute of Information Security
University of Stuttgart
Stuttgart, Germany
ralf.kuesters@sec.uni-stuttgart.de

Daniel Rausch
Institute of Information Security
University of Stuttgart
Stuttgart, Germany
daniel.rausch@sec.uni-stuttgart.de

Abstract—While accountability is a well-known concept in distributed systems and cryptography, in the literature on blockchains (and, more generally, distributed ledgers) the formal treatment of accountability has been a blind spot: there does not exist a formalization yet alone a formal proof of accountability for any blockchain yet. Therefore, in this work we put forward and propose a formal treatment of accountability in this domain. Our goal is to formally state and prove that if in a run of a blockchain a central security property, such as consistency, is not satisfied, then misbehaving parties can be identified and held accountable. Accountability is particularly useful for permissioned blockchains where all parties know each other, and hence, accountability incentivizes all parties to behave honestly. We exemplify our approach for one of the most prominent permissioned blockchains: Hyperledger Fabric in its most common instantiation.

Index Terms—Accountability, Blockchain, Distributed Ledger, Distributed Systems, Security, Hyperledger Fabric

# 1. Introduction

Since the invention of the blockchain in 2008 [51], interest in this concept in particular and distributed ledger technology in general has grown rapidly. Initially proposed as a solution for payment systems without a central authority, blockchains and distributed ledgers have evolved into multi-purpose distributed systems with strong security promises.

While there exists a wide range of established security notions and formal security analyses for blockchains [8], [9], [11], [19], [24], [35], [36], [53], there is an important blind spot in the formal security analysis of blockchains and distributed ledgers: accountability [43]. On a high level, accountability requires that if certain security goals of a protocol are violated, then misbehaving parties can be identified and held accountable for their misbehavior via undeniable cryptographic evidence, which incentivizes honest behavior.

Accountability itself is a well-known concept in distributed systems and cryptography that has already been applied to a wide variety of settings (see, e.g., [6], [10], [28], [39], [40], [42]-[45], [48], [49], [61]).

In the context of blockchains, accountability is often mentioned as a desirable property [12], [18], [22], [33],

[54] and some research papers on blockchains use the concept of accountability on an informal level [14], [34]. However, there does not exist a formalization let alone a formal proof of accountability for any blockchain or distributed ledger yet (see also Section 7).

Therefore, in this work we put forward and propose a formal treatment of accountability for blockchains, which we exemplify by a very prominent permissioned blockchain (see below). With this, we provide a new formal approach for designing and analyzing blockchains.

This approach is in fact orthogonal to established security notions for blockchains, such as consistency: these security notions [24], [53] require that security goals are always fulfilled under certain assumptions. For example, blockchains should always converge to a consistent state, typically under the assumption of a round-based network model with eventual message delivery and an honest majority of participants. In this sense, security (e.g., consistency) cannot be broken as long as certain assumptions are fulfilled. We call such security notions strict in what follows. In contrast, our accountability-based approach accepts that security goals can be violated. However, in such a case it is guaranteed that misbehaving parties can be identified and rightly blamed for their misbehavior. Our approach can be used in two ways:

**Accountability as a stand-alone property.** On the one hand, accountability is an interesting stand-alone property that can be used instead of strict security notions to obtain (different) security guarantees. Particularly for permissioned blockchains, where parties know each other and often collaborate on a contractual basis, having the guarantee that if some central security goal breaks down, then misbehaving parties can be identified and held accountable will in many cases be considered a sufficiently strong property. As demonstrated in this paper and further detailed below, using accountability as a stand-alone property allows for new constructions of secure blockchains which can leverage one or more of the following features: _(i)_ Accountability might already be achievable with weaker but more efficient components compared to what is needed for strict goals. For example, as illustrated in our case study, accountable blockchains can be built from efficient crash-fault tolerant consensus protocols instead of more complex Byzantine-fault tolerant consensus protocols in order to provide accountability w.r.t. consistency. That is, while a misbehaving party can break consistency,