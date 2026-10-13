
# BB84 Protocol

## Key Features

*   Makes use of quantum mechanical properties, in particular the no-cloning theorem and quantum superposition concepts.
*   The protocol entails the transmission of qubits (quantum bits) using two non-orthogonal states in a different basis (usually represented as “+” and “×”) and two additional non-orthogonal states in the standard basis (typically represented as “0” and “1”).
*   Alice, the sender, encrypts each bit using a random combination of the two bases.
*   Additionally, Bob, the receiver, selects a basis for measurement at random.
*   An eavesdropper's attempt to intercept the qubits introduces errors that the legitimate parties can detect because of the non-orthogonality of the states.

## Security Basis

*   The fundamental ideas of quantum mechanics, such as the impossibility of cloning an unknown quantum state and the disturbance brought on by measurements, are what underpin the security of BB84.

## Key Exchange Process

| Figure 4. BBM92 Protocol |
| --- |
| ![Figure979-8-3693-1642-9.ch007.f04](i/ch007.f04.png) |

1.  **Qubit Preparation**: Alice gets a series of qubits ready in two of the four possible states—the standard basis and the Hadamard basis.
2.  **Quantum Transmission**: Bob receives Alice's qubits via a quantum channel.
3.  **Basis Measurement**: Bob selects a basis at random for each qubit that is received.
4.  **Key Reconciliation**: Alice and Bob interact freely to contrast their measurement bases and eliminate data that was measured using a different basis.
5.  **Error Detection**: Alice and Bob look for mistakes in their critical information that might point to the existence of an illegal listener.
6.  **Privacy Amplification**: By processing the final shared key, privacy amplification techniques are applied to improve its security.

The BB84 protocol proved that secure key exchange utilizing quantum principles was feasible and established the groundwork for quantum key distribution. In the realm of quantum cryptography, it continues to be an essential protocol (Ciesla, 2020).

# E91 Protocol (Entanglement-Based QKD)

Artur Ekert proposed the Entanglement-based Quantum Key Distribution (QKD) protocol, or E91 protocol, in 1991. This protocol allows for the safe exchange of keys between two remote parties by taking advantage of the phenomenon known as quantum entanglement. This is a summary of the E91 protocol:

## E91 Protocol Overview

| Figure 5. E91 Protocol (Entanglement-based QKD) |
| --- |
| ![Figure979-8-3693-1642-9.ch007.f05](i/ch007.f05.png) |

## Entanglement Generation

*   In an entangled state, Alice produces pairs of entangled particles, usually photons. Regardless of their distance from one another, entanglement indicates that the states of the two particles are directly correlated.

## Quantum Measurement

*   Alice measures her particles in a variety of bases, selecting the basis at random for each measurement. Selecting a basis is essential for security.

## Quantum Communication

*   Alice sends one particle to Bob, who is located far away, from each entangled pair. The usual medium for this communication is a quantum channel.

## Quantum Measurement at Bob's End

*   For every particle received, Bob selects at random a measurement basis and conducts measurements in accordance with that basis.

## Correlation Check

*   Alice and Bob exchange information regarding the bases they used for their measurements following the quantum communication phase. They keep only the measurements made with the same foundation.

## Error Estimation

*   Bob and Alice calculate the measurement error rate. Elevated mistake rates could suggest the existence of a listener.

## Privacy Amplification

*   Alice and Bob use privacy amplification techniques to distil a shorter, but more secure, final shared key if the error rate is judged acceptable.

## Key Verification

*   Alice and Bob take extra precautions to make sure their key is secure against possible eavesdropping and to confirm that it is correct.

## Security Basis

*   Entanglement provides non-local correlations that are essential to the security of the E91 protocol.
*   Any attempt to eavesdrop would cause the entangled particles to become disoriented, which would result in observable mistakes in the key generation process.

## Significance

*   The E91 protocol highlighted the non-local and quantum nature of the security features by demonstrating the potential to use entanglement for secure key distribution.
*   Even though the E91 protocol may not be as useful in practice, it has sparked additional study and the creation of more sophisticated entanglement-based QKD protocols.

In the search for workable quantum communication systems, several entanglement-based protocols have been put forth and investigated. Quantum entanglement offers a special resource for secure key distribution.

# SARG04 Protocol (Six-state QKD): Six-State Quantum Key Distribution

| Figure 6. SARG04 Protocol (Six-state QKD) |
| --- |
| ![Figure979-8-3693-1642-9.ch007.f06](i/ch007.f06.png) |

## Qubit Preparation

*   Like BB84, Alice prepares qubits in one of six non-orthogonal states. These states are often represented as `|0⟩`, `|1⟩`, `|+⟩`, `|−⟩`, `|i⟩`, and `|−i⟩`, where `|+⟩` and `|−⟩` are superpositions of `|0⟩` and `|1⟩`, and `|i⟩` and `|−i⟩` are superpositions of `|0⟩` and `|1⟩` with a phase factor.

## Quantum Transmission

*   Alice sends the qubits to Bob over a quantum channel.

## Basis Measurement

*   Bob randomly chooses a basis for measuring each received qubit.

## Key Reconciliation

*   Alice and Bob communicate openly to compare their measurement bases and discard bits measured in different bases.

## Error Detection

*   Alice and Bob check for errors in their key bits, which would indicate the presence of an eavesdropper.

## Privacy Amplification

*   The final shared key is processed to enhance its security through privacy amplification techniques.

The Six-State Protocol provides an improvement over the BB84 protocol by using additional non-orthogonal states, which can increase the efficiency of quantum key distribution in certain scenarios.

# QDS (Quantum Digital Signatures)

A subfield of quantum cryptography known as “quantum digital signatures” (QDS) uses quantum computing and quantum key distribution (QKD) to create secure digital signatures. To guarantee the integrity and authenticity of electronic messages or data, digital signatures are essential. Utilizing the special qualities of quantum mechanics, quantum digital signatures provide higher levels of security (Bykovsky, 2018).

This is a basic introduction to quantum digital signatures:

## Key Concepts

### Quantum Key Distribution (QKD)

*   By utilizing the ideas of quantum mechanics, two parties can safely establish a secret key through QKD protocols like BB84 and E91. After that, this key can be utilized for traditional cryptography operations.

### Quantum Superposition and Entanglement

*   To create quantum states that are vulnerable to manipulation or eavesdropping attempts, quantum digital signatures frequently take advantage of the concepts of quantum superposition and entanglement.

## Quantum Digital Signature Process

| Figure 7. Quantum Digital Signature Process |
| --- |
| ![Figure979-8-3693-1642-9.ch007.f07](i/ch007.f07.png) |

## Key Generation

*   Using a QKD protocol, two parties—referred to as the signer and the verifier—establish a shared secret key.
