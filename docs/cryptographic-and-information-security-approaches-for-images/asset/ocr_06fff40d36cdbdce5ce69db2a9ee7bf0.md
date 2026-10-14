```
C : Input PW_i & B_i where B_i is the biohash of the client.
SB_i = h(PW_i) ⊕ B_i
y_i = E_x {B_i ⊕ ID_i}
CID_i = ID_i ⊕ N_u
C → S: E_Pk {h(PW_i), SB_i, CID_i, S_ID, y_i}
S : D_Sk (E_Pk {h(PW_i), SB_i, CID_i, S_ID, y_i})
N_U = CID_i ⊕ ID_i
Check h(PW_i) and SB_i
D_x (y_i) = (B_i ⊕ ID_i)
Compare stored B_i with received B_i
SED = N_s ⊕ S_ID
S → C: E_NU {SED, h(K_s), K_s}
C : D_NU (E_NU {SED, h(K_s), K_s})
N_s = SED ⊕ S_ID
From K_s, h(K_s) is calculated and compared.
Generate nonce value N_p
C → S: E_Ns {sign(previous received messages), N_p}
S : D_Ns (E_Ns {sign(previous received messages), N_p})
Check signed data
ID_P = ((ID_A ⊕ ID_B)||K_P)
S → C: E_Np {ID_P, CT_init}
```

# Figure 31.3 Login and mutual authentication of the biometric based authentication scheme.

key is transmitted in encrypted form along with a hashed value of the key. The client decrypts the data sent by the server and confirms that the data has been sent by the server by computing the nonce value N_s.

The client proves its validity by sending a signed message of the hello message along with a nonce N_p. Once the signed message is validated, the AS sends the client proxy credentials for service access. In the biometric based authentication scheme, the dynamic identifier CID_i is used to generate a proxy for the service requested by the client. The monitor server keeps a check on the operations of the AS and the user.