
## 3

The game-based BPR security definition can be re-stated in terms of `A`’s distinguishing advantage between two games: the real-world game with real session key(s), and the real-world game with random session key(s). In the BMP notion, the second game is not a real-world game with some modified values, but a *simulated* game, in which messages are created by algorithm `A*` interacting with an idealized PAKE functionality `F` that defines what `A*` learns about `P[i]`’s inputs and how `A*` can influence `P[i]`’s outputs.

## 4

*Explanations*: Case (a) says that if `A*` attacks `P[i]` with a *correct* password then `A*` determines `P[i]`’s output `sk[i]`; case (b) says that if `A*` connects `P[i]` and `P[j]`, they use the same passwords, they are intended counterparties, and `P[j]` is the first-to-complete, then `P[i]` gets the same session key as `P[j]`; case (c) covers the case of `A*` attacking `P[i]` with an *incorrect* password, and the case of `P[i]` which is `fresh`, that is, not actively attacked, but it is either first-to-complete, or it is “connected” to a wrong counterparty. The `dangling` state corresponds to a “last minute active attack” by the adversary: If the session is so marked, then it is no longer `fresh` so `F_Pake` will not copy its output to any other honest session, as in case (b), but a session so marked is open to a *future* `TestPwd` queries, see item (2) above.

## 5

Kobara-Imai (Kobara and Imai 2002) claimed almost the same protocol BPR-secure in the standard model except in their version `M = N`, the protocol is followed by a key confirmation round, see [Figure 10.2](#c10.xhtml#c10-fig-2), and the session key and the key confirmation messages `τ, γ` are derived by PRF/MAC applied directly to the DH secret `g^(xy)` instead of `sk` derived from `g^(xy)` by an RO hash. However, Kobara and Imai (2002) relied on a strong and non-standard notion of MAC security which seems hard to implement in the standard model.

# 11

Verifiable Computation and Succinct Arguments for NP

**Dario FIORE**

*IMDEA Software Institute, Madrid, Spain*

## 11.1 Introduction

Verifiable computation (VC) is a cryptographic notion that enables a client to delegate a computation to an untrusted server in a *secure* and *efficient* way.

In this context, “security” means that the client can be assured that the result received from the untrusted machine is correct; “efficiency” means that the computational resources needed by the client to run this protocol (including being convinced of the result’s correctness) are significantly lower than those needed to execute the computation. In other words, efficiency ensures that delegating the computation using VC is cost effective for the client. In fact, if the efficiency requirement is dropped, then it is trivial to design a secure VC protocol: the client checks the result by simply re-executing the computation locally.

The simultaneous achievement of security and efficiency makes VC an intriguing notion that attracts interest from both the theory and the practice sides of computer science.

From a practical perspective, VC is particularly attractive for the potential of bringing security to Cloud computing, a paradigm in which clients rent computing resources from powerful external entities and that is widely adopted in the modern IT infrastructures. From a theoretical perspective, VC goes hand in hand with the notions of interactive (and non-interactive) proofs and arguments (see [Chapter 3](#c03.xhtml)), which are fundamental in theoretical computer science.

The goal of this chapter is to present the definition of VC, and to describe a construction of VC for computations expressible as polynomial-size arithmetic circuits.

Before turning to the details of VC, in the next section we provide background on VC and related notions, as well as a brief overview of the milestones in the literature about this notion.

### 11.1.1 Background

*Interactive proofs* (Goldwasser et al. 1985) are protocols in which a powerful prover can convince (in a probabilistic way) a weak verifier that a statement is true. In traditional interactive proofs (e.g. proving that IP=PSPACE (Lund et al. 1990; Shamir 1990)), this unbalance of computational resources considers superpolynomial-time provers and polynomial-time verifiers, which can be unsuitable in real-world scenarios where provers are supposed to be real machines that should run in polynomial time. Goldwasser et al. (2008) proposed an interactive proof (known as GKR in the literature) that works for polynomial-time provers and polylogarithmic verifiers, but that achieves this complexity only for specific classes of computations (e.g. those computable by a log-space-uniform NC boolean circuit).

*Probabilistically checkable proofs* (PCPs) (Arora and Safra 1992) are an evolution of interactive proofs in which a polynomial-time prover can produce a polynomial-size proof string that the verifier can check in only a few positions in order to be (probabilistically) convinced. However, PCPs do not, by themselves, constitute a VC protocol, as the verifier must receive the proof string, which may be too long to keep the verifier low cost.

To address this problem, Kilian proposed a protocol to turn PCPs into *succinct interactive arguments* that are secure against polynomial-time provers (Kilian 1992). The idea of Kilian’s protocol is that the prover first sends a commitment of the PCP string using a Merkle tree (or, more generally, using a vector commitment (Catalano and Fiore 2013; Lai and Malavolta 2019)) and then opens only the positions of the proof selected by the verifier and proves (by giving Merkle tree authentication paths) that they are indeed the values at the requested positions in the committed string. This approach can also be made non-interactive in the random oracle model by using Micali’s computationally sound (CS) proofs (Micali 1994).

A completely different approach to VC was proposed by Gennaro et al. (2010) who defined the notion of *non-interactive VC* and proposed a construction based on fully homomorphic encryption (Gentry 2009) and garbled circuits (Yao 1982). Notably, the scheme of Gennaro et al. can also ensure the confidentiality of the computation’s inputs against the server and, in contrast to CS proofs and the GKR protocol, is non-interactive without the need of random oracles. The VC of Gennaro et al. (2010) works in a model where the client who delegates and verifies computations uses a secret key. Parno et al. (2012) introduced a model where, after a trusted preprocessing, everyone can delegate and verify using only public information. This notion is called *public VC*, and Parno et al. (2012) proposed a construction of it based on attribute-based encryption.

Finally, another approach to (non-interactive) VC is that based on succinct non-interactive arguments (SNARGs) for `NP` (e.g. Parno et al. 2013). SNARGs for `NP` are essentially VC protocols for non-deterministic computation, that is, to prove that ∃`w` : `C(x, w) = y`, and basically further formalize the notion of CS proofs proposed by Micali. However, while Micali’s construction was specifically relying on the random oracle heuristic by using the Fiat–Shamir transform, SNARGs may be secure in the standard model, albeit under strong cryptographic assumptions. Indeed, in a celebrated work, Gentry and Wichs (2011) proved that SNARGs are likely to require non-falsifiable assumptions, namely assumptions in which it may not be efficient to decide whether an adversary won or not.
