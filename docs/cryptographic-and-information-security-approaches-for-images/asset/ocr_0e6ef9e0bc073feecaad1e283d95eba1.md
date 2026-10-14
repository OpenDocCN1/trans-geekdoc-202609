B ◁ *{[{h(K_S)},K_S,h(PW_A),(N_S ⊕ ID_B),CID_A(h(PW_A) ⊕ B_A), ID_B}]_{sign}, N_P} N_S, B ⊳ N_S,

B ≡ A ↔_{N_U} B, B |≡ φ(signedmessage, N_P), A |≡ #((signedmessage, N_P))
B |≡ A ∼ (signedmessage, N_P), (I3)

B ≡ A | ∼ {[{h(K_S)},K_S,h(PW_A),(N_S ⊕ ID_B),CID_A(h(PW_A) ⊕ B_A), ID_B}]_{sign}, N_P} N_S, B |≡ A ⊳ N_S

If all of the conditions hold: (1) B receives the formula ({h(K_S)},K_S,h(PW_A), (N_S ⊕ ID_B),CID_A(h(PW_A) ⊕ B_A),ID_B]_{sign},N_P) encrypted with the key N_S and marked with a non-originated mark; (2) B possesses N_S; (3) B considers that N_S is an apt secret between A and B; (4) B considers that the formula ({h(K_S)},K_S,h(PW_A),(N_S ⊕ ID_B),CID_A(h(PW_A) ⊕ B_A),ID_B]_{sign},N_P) is identifiable because ID_B is identifiable and (5) B considers that N_S is new, A considers that B once informed [{h(K_S)},K_S,h(PW_A),(N_S ⊕ ID_B),CID_A(h(PW_A) ⊕ B_A),ID_B]_{sign},N_P}]_{N_S} and that B possesses N_S.

Therefore, it is proven that: (1) B considers that the third flow message of the proposed scheme is from the A and (2) B considers that the A has the temporal key N_S.

# 31.9.4 The Fourth Flow

A ◁∼{((ID_A ⊕ ID_B)||K_P),CT_init}_{N_P}, A ⊳ N_P
------------------------------------------------
A ◁(((ID_A ⊕ ID_B)||K_P),CT_init) (T3)

If A is told the formula ((ID_A ⊕ ID_B)||K_P),CT_init) encrypted with the key N_P that it possesses, then A is considered to have also been told the decrypted contents of the encrypted equation.

A |≡ φ((ID_A,ID_B)A ⊳ N_P)
---------------------------------------- (R1,R2)
A |≡ φ({((ID_A ⊕ ID_B)||K_P,CT_init)}_{N_P})

If A considers that the formula ID_A and ID_B is identifiable and has the key N_P, then A is entitled to believe that the formula {((ID_A ⊕ ID_B)||K_P,CT_init)}_{N_P}, of which ID_A and ID_B are parts which are identifiable. Therefore, it is proven that A can identify the message in the fourth flow of the proposed scheme.