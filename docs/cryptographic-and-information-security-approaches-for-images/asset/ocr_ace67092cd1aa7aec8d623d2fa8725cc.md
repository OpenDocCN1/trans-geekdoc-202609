```
A |≡ φ((ID_A ⊕ ID_B)||K_P, CT_init), A |≡ (N_P), A ⊳ N_P
--------------------------------------------------------
B |≡ #{(ID_A ⊕ ID_B)||K_P, CT_init}_N_P (F7)
```

If A considers that the formula ID_A and ID_B is identifiable and has the key N_P and considers that it is new, then A is entitled to believe that the encrypted equation {(ID_A ⊕ ID_B)||K_P, CT_init}_N_P, of which ID_A and ID_B are parts which are new. Therefore, it is proven that A can identify the message in the fourth flow of the proposed scheme is new.

```
A ◁ *{(ID_A ⊕ ID_B)||K_P, CT_init}_N_P, A ⊳ N_P,
A ≡ A ↔^N_P B, A |≡ φ((ID_A ⊕ ID_B)||K_P, CT_init),
B |≡ #((ID_A ⊕ ID_B)||K_P, CT_init)
--------------------------------------------------------
≡ B |~ ((ID_A ⊕ ID_B)||K_P, CT_init),
A | A |≡ B |~ {(ID_A ⊕ ID_B)||K_P, CT_init}_N_P, A |≡ B ⊳ N_P (I1)
```

If all of the conditions hold: (1) A receives the formula ((ID_A ⊕ ID_B)||K_P, CT_init) encrypted with the key N_P and marked with a non-originated mark; (2) A possesses N_P; (3) A considers that N_P is an apt secret between A and B; (4) A considers that the formula ((ID_A ⊕ ID_B)||K_P, CT_init) is identifiable because ID_B is identifiable and (5) A considers that N_P is new, A considers that B once informed {(ID_A ⊕ ID_B)||K_P, CT_init}_N_P and that B possesses N_P.

Therefore, it is confirmed that: (1) A considers that the fourth flow message of the proposed scheme is from B and (2) A considers that the B has the temporal key N_P.

Therefore, it is proven that there exists a newness value included in all of the messages. Due to this newness of data, man-in-the-middle attack, snooping attack, which can lead to replay attack, and modification attack can be avoided.

# 31.10 Performance Analysis

# 31.10.1 Communication Cost Comparison

For comparison of communication cost between the authentication schemes, only the dominant communication costs in bytes are considered. Such costs include cost incurred due to the certificate generation, encryption and signing of messages. The comparison of the biometric based authentication scheme is with the Secure Socket Layer (SSL) (Freier et al. 1996) based authentication since the cloud computing authentication basis is the SSL protocol and ID based authentication scheme for