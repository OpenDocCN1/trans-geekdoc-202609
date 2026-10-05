# 2.7 Digital Signatures with Encryption

Another scheme uses Trent after the fact [209]. After receiving a signed message, Bob can send a copy to Trent for verification. Trent can attest to the validity of Alice's signature.

# Applications of Digital Signatures

One of the earliest proposed applications of digital signatures was to facilitate the verification of nuclear test bans [1454,1467]. The United States and the Soviet Union (anyone remember the Soviet Union?) permitted each other to put seismometers on the other to monitor nuclear tests. The problem was that each country needed to assure that the host nation was not tampering with the data from the monitoring seismometers. Simultaneously, the host nation needed to assure that the monitoring was signed only the specific information needed for monitoring.

Conventional authentication techniques can solve the first problem, but only digital signatures can solve both problems. The host nation can read, but not alter, data from the seismometer, and the monitoring nation knows that the data has not been tampered with.

# 2.7 DIGITAL SIGNATURES WITH ENCRYPTION

By combining digital signatures with public-key cryptography, we develop a protocol that combines the security of encryption with the authenticity of digital signatures. Think of a letter from your mother. The signature provides proof of authorship and the envelope provides privacy.

+   (1) Alice signs the message with her private key.
$S_A(M)$

+   (2) Alice encrypts the signed message with Bob's public key and sends it to Bob.
$E_B(S_A(M))$

+   (3) Bob decrypts the message with his private key.
$D_B(E_B(S_A(M))) = S_A(M)$

+   (4) Bob verifies with Alice's public key and recovers the message.
$V_A(S_A(M)) = M$

Signing before encrypting seems natural. When Alice writes a letter, she signs it and puts it in an envelope. If she put the letter in the envelope unsigned and signed the envelope, then Bob might worry if the letter hadn't been covered replaced. If Bob should show Carol Alice's letter and envelope, Carol might accuse Bob of lying about which letter arrived in which envelope.

In electronic correspondence as well, signing before encrypting is a prudent practice [48]. Not only is it more secure—an adversary can't remove a signature from an encrypted message and add his own—but there are legal considerations: If the text