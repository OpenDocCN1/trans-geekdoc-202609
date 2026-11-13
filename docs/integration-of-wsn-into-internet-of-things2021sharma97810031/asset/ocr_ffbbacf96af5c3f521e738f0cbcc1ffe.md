TABLE 2.5 (Continued)
Summary of WSN Attacks, Strategies, Effects, and Countermeasures

| Attacks | Strategy | Effects | Affected Layer | Solution |
| :--- | :--- | :--- | :--- | :--- |
| Route alteration | Routes are altered | Creating routing loops attract or repel network traffic, creates fragments in the network, extends or shortens the routes, and creates fake messages | Network layer | MAC protocol; encrypted and authenticated message transmissions |
| Flooding | Repetitive connection creation requests | Resources are exhausted; power drain; bandwidth waste | Transport layer | Client-side puzzle; limit of connections |
| Desynchronization attacks | Transmitting missed frames | Communication between nodes is hampered | Transport layer | Synchronization between nodes; packet encryption; packet-wise authentication |
| Overwhelm attack | Passes large amounts of data | Bandwidth and energy drain enormous false traffic | Application layer | Rate limiter; data aggregators; node tuning |
| Path-based DoS attack | Replayed packet injection into the leaf node DoS | Path unavailable; connection unavailable | Application layer | Combine packet authentication and antireplay prediction |
| Deluge attack | Reprogramming attacks; attacks programming codes and changes | Gain access; illicit advantages | Application layers | Administrative authentication; secure communication protocols |

# 2.4 ROLE OF CRYPTOGRAPHY IN WIRELESS SENSOR NETWORKS

Cryptography plays a crucial role in protecting data integrity, confidentiality, and authenticity. The study of cryptography suggests that it can be distinguished as symmetric-key cryptography (SKC) and public-key cryptography (PKC)[72,73].

Public-Key Cryptography vs. Symmetric-Key Cryptography: In SKC, the sender and receiver will share a secret key between them. In contrast, PKC uses two keys— a secret key and a public key. Any operation done with the secret key can only be