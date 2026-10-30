![](bbox=[0.22, 0.12, 0.8, 0.36])

Figure 3.8 BB84 setting. (Image credit: Lahiru Madushanka [40].)

# 3.6.2.2 Basic principle

The basic principle behind BB84 is the fact that measuring a qubit alters its state. In the quantum channel, the act of measuring the photon will alter its polarization state. Therefore, if Eve tries to snoop on the communication through the quantum channel, Bob will know someone has tried to look at his communication and may decide to alter the key.

If Alice encodes 0 as | + ⟩ and Bob measures it in x-basis, he will measure the 0 with 100% probability, but if Bob measures it in z-basis, he will measure the 0 with 50% probability and 1 with 50% probability.

The BB84 is basically making sure that the eavesdropper has negligible probability of getting the true value of the qubit state being sent.

+   Step 1: Alice to choose a random binary string '00 11 10 11 00 10'.
+   Step 2: Alice to choose a random sequence of basis 'XZ XX ZX ZX XZ XX'.
+   Step 3: Alice to encode the binary string on the basis of random sequence of basis. The output of this string would be: | − ⟩|0⟩| − ⟩| + ⟩| + ⟩|1⟩| − ⟩|1⟩| + ⟩| − ⟩| − ⟩|0⟩| + ⟩|1⟩. This is the sequence Alice sent to Bob.
+   Step 4: Bob measures the sequence of qubits received in a random choice of basis such as 'ZX XZ XZ XX ZZ ZX'.
+   Step 5: Alice shares in the classical channel, which basis she used to encode and measure the qubits respectively.
+   Step 6: Bob compares his result with the basis shared by Alice and keeps only those bits that match with the basis shared by Alice. This becomes part of the secret key with Bob.
+   Step 7: Bob and Alice share a sample from the sequence they have. If both match, it means the key exchange has taken place.

# 3.6.3 Analysis

Despite its numerous advantages, however, quantum key distribution isn't without its challenges when it comes to practical implementation; namely