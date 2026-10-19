communications path (e.g., a satellite link, telephone circuit, or T-1 line). Because link encryption also encrypts routing data, communications nodes need to decrypt the data to continue routing. The data packet is decrypted and re-encrypted at each point in the communications channel. It is theoretically possible that an attacker compromising a node in the network may see the message in the clear. Because link encryption also encrypts the routing information, it provides traffic confidentiality better than end-to-end encryption. Traffic confidentiality hides the addressing information from an observer, preventing an inference attack based on the existence of traffic between two parties.

# End-to-End Encryption

End-to-end encryption is generally performed by the end-user within an organization. The data are encrypted at the start of the communications channel or before and remain encrypted until they are decrypted at the remote end. Although data remain encrypted when passed through a network, routing information remains visible. It is possible to combine both types of encryption. See Figure 2.1.

# Comparison of Link and
End-to-End Encryption

![](bbox=[0.12, 0.52, 0.85, 0.92])

End-to-End
Encryption Device

Link Encryption Device

Figure 2.1 — Comparaison of Link and End-to-End encryption