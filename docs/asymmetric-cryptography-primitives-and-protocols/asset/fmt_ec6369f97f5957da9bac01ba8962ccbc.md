
# Selective-Opening (SO) Security

Selective-opening (SO) security considers attack scenarios in multi-user settings where the adversary can adaptively corrupt some users and learn (i.e. “open”) all the information of corrupted users including randomness, while the security concerns those ciphertexts created by or sent to uncorrupted users (depending on the flavor of SO security, namely, sender security and receiver security, respectively). This attack scenario first arose in the context of adaptively secure multi-party computation (Canetti et al. 1996), where the adversary can corrupt some encrypted channels. SO security can be considered for both the sender corruption case and the receiver corruption case.

Bellare et al. (2009) are the first to formalize selective-opening security for sender (sender SO security, for short), who gave simulation-based and indistinguishability-based definitions. The case of receiver corruption (receiver SO security) was formalized and studied by Bellare et al. (2012a); Hazay et al. (2015). A series of works (Bellare et al. 2009, 2012a; Böhl et al. 2012; Hofheinz and Rupp 2014; Hazay et al. 2015; Hofheinz et al. 2016b) showed that a standard security notion such as `IND-CPA` (or even `IND-CCA`) does not imply sender or receiver SO security. Note that hybrid arguments do not help to bridge standard notions to the multi-user setting considered here, since in this case, in particular, the randomness is required to be opened (and standard notions do not allow so). (The work of Fuchsbauer et al. (2016), on the other hand, showed that `IND-CPA` security implies SO security under a certain condition on the corruption.) Sender SO secure PKE schemes were constructed in many works (Bellare et al. 2009; Fehr et al. 2010; Hemenway et al. 2011; Hofheinz 2012; Huang et al. 2013; Liu and Paterson 2015; Heuer et al. 2015; Hofheinz et al. 2016a; Heuer and Poettering 2016; Hoang et al. 2016; Libert et al. 2017; Lyu et al. 2018). Receiver SO secure PKE schemes were constructed in, for example, Hazay et al. (2015); Jia et al. (2016, 2017); Hara et al. (2018); Huang et al. (2019); Yang et al. (2020).

## 1.5. References

Abdalla, M., Bellare, M., Rogaway, P. (2001). The oracle Diffie–Hellman assumptions and an analysis of DHIES. In *CT-RSA 2001*, vol. 2020 of *LNCS*, Naccache, D. (ed.). Springer, Heidelberg.

Abe, M., Gennaro, R., Kurosawa, K., Shoup, V. (2005). Tag-KEM/DEM: A new framework for hybrid encryption and a new analysis of Kurosawa-Desmedt KEM. In *EUROCRYPT 2005*, vol. 3494 of *LNCS*, Cramer, R. (ed.). Springer, Heidelberg.

Abe, M., Kiltz, E., Okamoto, T. (2008). Chosen ciphertext security with optimal ciphertext overhead. In *ASIACRYPT 2008*, vol. 5350 of *LNCS*, Pieprzyk, J. (ed.). Springer, Heidelberg.

Abe, M., David, B., Kohlweiss, M., Nishimaki, R., Ohkubo, M. (2013). Tagged one-time signatures: Tight security and optimal tag size. In *PKC 2013*, vol. 7778 of *LNCS*, Kurosawa, K., Hanaoka, G. (eds). Springer, Heidelberg.

Acar, T., Belenkiy, M., Bellare, M., Cash, D. (2010). Cryptographic agility and its relation to circular encryption. In *EUROCRYPT 2010*, vol. 6110 of *LNCS*, Gilbert, H. (ed.). Springer, Heidelberg.

Acar, A., Aksu, H., Uluagac, A.S., Conti, M. (2019). A survey on homomorphic encryption schemes: Theory and implementation. *ACM Computing Surveys*, 51(4), 79, 1–35 \[Online\]. Available at: [https://doi.org/10.1145/3214303](https://doi.org/10.1145/3214303).

Akavia, A., Goldwasser, S., Vaikuntanathan, V. (2009), Simultaneous hardcore bits and cryptography against memory attacks. In *TCC 2009*, vol. 5444 of *LNCS*, Reingold, O. (ed.). Springer, Heidelberg.

Alwen, J., Dodis, Y., Wichs, D. (2010). Survey: Leakage resilience and the bounded retrieval model. In *ICITS 09*, vol. 5973 of *LNCS*, Kurosawa, K. (ed.). Springer, Heidelberg.

Ambainis, A., Hamburg, M., Unruh, D. (2019). Quantum security proofs using semi-classical oracles. In *CRYPTO 2019, Part II*, vol. 11693 of *LNCS*, Boldyreva, A., Micciancio, D. (eds). Springer, Heidelberg.

An, J.H., Dodis, Y., Rabin, T. (2002). On the security of joint signature and encryption. In *EUROCRYPT 2002*, vol. 2332 of *LNCS*, Knudsen, L.R. (ed.). Springer, Heidelberg.

Applebaum, B. (2011). Key-dependent message security: Generic amplification and completeness. In *EUROCRYPT 2011*, vol. 6632 of *LNCS*, Paterson, K.G. (ed.). Springer, Heidelberg.

Applebaum, B., Cash, D., Peikert, C., Sahai, A. (2009). Fast cryptographic primitives and circular-secure encryption based on hard learning problems. In *CRYPTO 2009*, vol. 5677 of *LNCS*, Halevi, S. (ed.). Springer, Heidelberg.

Attrapadung, N., Hanaoka, G., Yamada, S. (2015). A framework for identity-based encryption with almost tight security. In *ASIACRYPT 2015, Part I*, vol. 9452 of *LNCS*, Iwata, T., Cheon, J.H. (eds). Springer, Heidelberg.

Backes, M., Dürmuth, M., Unruh, D. (2008). OAEP is secure under key-dependent messages. In *ASIACRYPT 2008*, vol. 5350 of *LNCS*, Pieprzyk, J. (ed.). Springer, Heidelberg.

Badertscher, C., Maurer, U., Portmann, C., Rito, G. (2021). Revisiting (R)CCA security and replay protection. In *PKC 2021, Part II*, vol. 12711 of *LNCS*, Garay, J. (ed.). Springer, Heidelberg.

Baecher, P., Brzuska, C., Fischlin, M. (2013). Notions of black-box reductions, revisited. In *ASIACRYPT 2013, Part I*, vol. 8269 of *LNCS*, Sako, K., Sarkar, P. (eds). Springer, Heidelberg.

Barak, B., Goldreich, O., Impagliazzo, R., Rudich, S., Sahai, A., Vadhan, S.P., Yang, K. (2001). On the (im)possibility of obfuscating programs. In *CRYPTO 2001*, vol. 2139 of *LNCS*, Kilian, J. (ed.). Springer, Heidelberg.

Barak, B., Haitner, I., Hofheinz, D., Ishai, Y. (2010). Bounded key-dependent message security. In *EUROCRYPT 2010*, vol. 6110 of *LNCS*, Gilbert, H. (ed.). Springer, Heidelberg, 423–444.

Bellare, M. and Namprempre, C. (2000). Authenticated encryption: Relations among notions and analysis of the generic composition paradigm. In *ASIACRYPT 2000*, vol. 1976 of *LNCS*, Okamoto, T. (ed.). Springer, Heidelberg.

Bellare, M. and Palacio, A. (2004). Towards plaintext-aware public-key encryption without random oracles. In *ASIACRYPT 2004*, vol. 3329 of *LNCS*, Lee, P.J. (ed.). Springer, Heidelberg.

Bellare, M. and Rogaway, P. (1993). Random oracles are practical: A paradigm for designing efficient protocols. In *ACM CCS 93*, Denning, D.E., Pyle, R., Ganesan, R., Sandhu, R.S., Ashby, V. (eds). ACM Press.

Bellare, M. and Rogaway, P. (1995). Optimal asymmetric encryption. In *EUROCRYPT’94*, vol. 950 of *LNCS*, Santis, A.D. (ed.). Springer, Heidelberg.

Bellare, M. and Rogaway, P. (2006). The security of triple encryption and a framework for code-based game-playing proofs. In *EUROCRYPT 2006*, vol. 4004 of *LNCS*, Vaudenay, S. (ed.). Springer, Heidelberg.

Bellare, M. and Sahai, A. (1999). Non-malleable encryption: Equivalence between two notions, and an indistinguishability-based characterization. In *CRYPTO’99*, vol. 1666 of *LNCS*, Wiener, M.J. (ed.). Springer, Heidelberg.

Bellare, M. and Sahai, A. (2006). Non-malleable encryption: Equivalence between two notions, and an indistinguishability-based characterization. Cryptology ePrint Archive, Report 2006/228 \[Online\]. Available at: [https://eprint.iacr.org/2006/228](https://eprint.iacr.org/2006/228).

Bellare, M., Desai, A., Pointcheval, D., Rogaway, P. (1998). Relations among notions of security for public-key encryption schemes. In *CRYPTO’98*, vol. 1462 of *LNCS*, Krawczyk, H. (ed.). Springer, Heidelberg.

Bellare, M., Boldyreva, A., Micali, S. (2000). Public-key encryption in a multi-user setting: Security proofs and improvements. In *EUROCRYPT 2000*, vol. 1807 of *LNCS*, Preneel, B. (ed.). Springer, Heidelberg.

Bellare, M., Hofheinz, D., Yilek, S. (2009). Possibility and impossibility results for encryption and commitment secure under selective opening. In *EUROCRYPT 2009*, vol. 5479 of *LNCS*, Joux, A. (ed.). Springer, Heidelberg.
