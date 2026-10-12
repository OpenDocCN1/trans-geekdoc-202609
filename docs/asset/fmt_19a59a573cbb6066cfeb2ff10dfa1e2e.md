
形式上，转换后方案的密钥生成算法因此为底层方案生成签名密钥对 `(sk, pk)`，为变色龙哈希函数生成两个独立的密钥对 `(sk_ch, pk_ch)` 和 `(sk'_ch, pk'_ch)`，丢弃秘钥 `sk'_ch`，并输出密钥对 `sk_strong = (sk, sk_ch, pk_ch, pk'_ch)` 和 `pk^strong = (pk, pk^ch, pk'_ch)`。验证过程包含重新计算哈希值，并验证第二个哈希值的最终签名。

直观上，转换后的签名方案之所以具有强不可伪造性，是因为最终签名 `σ_strong` 中对 `σ`、`r` 或 `r'` 的任何修改，都要求在变色龙哈希函数中找到碰撞，或者在底层签名方案下为新的哈希值伪造签名。我们注意到，证明中需要两个嵌套的变色龙哈希，以便在不同的变色龙陷门之间切换。原则上，它们可以合并为一个支持多个秘钥的单一变色龙哈希。

## 2.4 总结

我们定义了签名方案的常见安全概念 EUF-CMA 和 SEUF-CMA。前者保证对手无法为先前未签名的消息生成有效伪造。后者确保也无法为已签名消息找到新的签名。随后我们描述了如何通过变色龙哈希将 EUF-CMA 安全方案转化为强安全方案。该转换相当高效，尽管增加了一些开销。

我们还讨论了两个实用签名方案（EC）DSA 和 Schnorr 的安全性。尽管 Schnorr 方案在随机预言机模型下，基于离散对数假设提供 SEUF-CMA 安全性——但安全界限较松——（EC）DSA 的安全性目前仍是开放问题。唯一有保证的事实是 ECDSA 不具备强不可伪造性。

## 2.5 参考文献

Aumasson, J.-P., Bernstein, D.J., Beullens, W., Dobraunig, C., Eichlseder, M., Fluhrer, S., Gazdag, S.-L., Hülsing, A., Kampanakis, P., Kölbl, S., et al. (2020). Shincs^+: Algorithm specifications and supporting documentation [Online]. Available at: [`sphincs.org/data/sphincs+-round3-specification.pdf`](https://sphincs.org/data/sphincs+-round3-specification.pdf)

Bai, S., Ducas, L., Kiltz, E., Lepoint, T., Lyubashevsky, V., Schwabe, P., Seiler, G., Stehle, D. (2020). Crystals-dilithium: Algorithm specifications and supporting documentation [Online]. Available at: [`pq-crystals.org/dilithium/data/dilithium-specification-round3.pdf`](https://pq-crystals.org/dilithium/data/dilithium-specification-round3.pdf)

Bellare, M. and Neven, G. (2006). Multi-signatures in the plain public-key model and a general forking lemma. In *ACM CCS 2006*, Juels, A., Wright, R.N., De Capitani di Vimercati, S. (eds). ACM Press.

Bellare, M. and Rogaway, P. (1993). Random oracles are practical: A paradigm for designing efficient protocols. In *ACM CCS 93*, Denning, D.E., Pyle, R., Ganesan, R., Sandhu, R.S., Ashby, V. (eds). ACM Press.

Brown, D.R.L. (2005). Generic groups, collision resistance, and ECDSA. *Designs, Codes and Cryptography*, 35(1), 119–152.

Brown, D.R.L. (2015a). A flaw in a theorem about Schnorr signatures. Cryptology ePrint Archive, Report 2015/509 [Online]. Available at: [`eprint.iacr.org/2015/509`](https://eprint.iacr.org/2015/509).

Brown, D.R.L. (2015b). Short Schnorr signatures require a hash function with more than just random-prefix resistance. Cryptology ePrint Archive, Report 2015/169 [Online]. Available at: [`eprint.iacr.org/2015/169`](https://eprint.iacr.org/2015/169).

Canetti, R., Halevi, S., Katz, J. (2004). Chosen-ciphertext security from identity-based encryption. In *EUROCRYPT 2004*, vol. 3027 of *LNCS*, Cachin, C., Camenisch, J. (eds). Springer, Heidelberg.

Decker, C. and Wattenhofer, R. (2014). Bitcoin transaction malleability and MtGox. In *ESORICS 2014, Part II*, vol. 8713 of *LNCS*, Kutylowski, M., Vaidya, J. (eds). Springer, Heidelberg.

Even, S., Goldreich, O., Micali, S. (1996). On-line/off-line digital signatures. *Journal of Cryptology*, 9(1), 35–67.

Fersch, M., Kiltz, E., Poettering, B. (2016). On the provable security of (EC)DSA signatures. In *ACM CCS 2016*, Weippl, E.R., Katzenbeisser, S., Kruegel, C., Myers, A.C., Halevi, S. (eds). ACM Press.

Fiat, A. and Shamir, A. (1987). How to prove yourself: Practical solutions to identification and signature problems. In *CRYPTO’86*, vol. 263 of *LNCS*, Odlyzko, A.M. (ed.). Springer, Heidelberg.

Fischlin, M. and Fleischhacker, N. (2013). Limitations of the meta-reduction technique: The case of Schnorr signatures. In *EUROCRYPT 2013*, vol. 7881 of *LNCS*, Johansson, T., Nguyen, P.Q. (eds). Springer, Heidelberg.

Fleischhacker, N., Jager, T., Schröder, D. (2019). On tight security proofs for Schnorr signatures. *Journal of Cryptology*, 32(2), 566–599.

Goldreich, O. (2004). *Foundations of Cryptography: Basic Applications*, volume 2. Cambridge University Press, Cambridge, UK.

Goldwasser, S., Micali, S., Rivest, R.L. (1984). A “paradoxical” solution to the signature problem (extended abstract). In *25th FOCS*. IEEE Computer Society Press.

Goldwasser, S., Micali, S., Rivest, R.L. (1988). A digital signature scheme secure against adaptive chosen-message attacks. *SIAM Journal on Computing*, 17(2), 281–308.

Krawczyk, H. and Rabin, T. (2000). Chameleon signatures. In *NDSS 2000*. The Internet Society, Reston, VA.

Lamport, L. (1979). Constructing digital signatures from a one-way function. Technical Report SRI-CSL-98, SRI International Computer Science Laboratory.

Merkle, R.C. (1988). A digital signature based on a conventional encryption function. In *CRYPTO’87*, vol. 293 of *LNCS*, Pomerance, C. (ed.). Springer, Heidelberg.

Merkle, R.C. (1990). A certified digital signature. In *CRYPTO’89*, vol. 435 of *LNCS*, Brassard, G. (ed.). Springer, Heidelberg.

National Institute of Standards and Technology (1994). Digital signature standard (DSS). FIPS PUB 186, Federal Information Processing Standards Publication.

National Institute of Standards and Technology (2013). Digital signature standard (DSS). FIPS PUB 186-4, Federal Information Processing Standards Publication.

National Institute of Standards and Technology (2015). Secure hash standard (SHS). FIPS PUB 180-4, Federal Information Processing Standards Publication.

Neven, G., Smart, N.P., Warinschi, B. (2009). Hash function requirements for Schnorr signatures. *Journal of Mathematical Cryptology*, 3(1), 69–87.

Paillier, P. and Vergnaud, D. (2005). Discrete-log-based signatures may not be equivalent to discrete log. In *ASIACRYPT 2005*, vol. 3788 of *LNCS*, Roy, B.K. (ed.). Springer, Heidelberg.

Pointcheval, D. and Stern, J. (1996). Security proofs for signature schemes. In *EUROCRYPT’96*, vol. 1070 of *LNCS*, Maurer, U.M. (ed.). Springer, Heidelberg.

Pointcheval, D. and Stern, J. (2000). Security arguments for digital signatures and blind signatures. *Journal of Cryptology*, 13(3), 361–396.

Sahai, A. (1999). Non-malleable non-interactive zero knowledge and adaptive chosen-ciphertext security. In *40th FOCS*. IEEE Computer Society Press.

Schnorr, C.-P. (1990). Efficient identification and signatures for smart cards. In *CRYPTO’89*, vol. 435 of *LNCS*, Brassard, G. (ed.). Springer, Heidelberg.

Schnorr, C.-P. (1991). Efficient signature generation by smart cards. *Journal of Cryptology*, 4(3), 161–174.

Seurin, Y. (2012). On the exact security of Schnorr-type signatures in the random oracle model. In *EUROCRYPT 2012*, vol. 7237 of *LNCS*, Pointcheval, D., Johansson, T. (eds). Springer, Heidelberg.

Steinfeld, R., Pieprzyk, J., Wang, H. (2007). How to strengthen any weakly unforgeable signature into a strongly unforgeable signature. In *CT-RSA 2007*, vol. 4377 of *LNCS*, Abe, M. (ed.). Springer, Heidelberg.

Stern, J., Pointcheval, D., Malone-Lee, J., Smart, N.P. (2002). Flaws in applying proof methodologies to signature schemes. In *CRYPTO 2002*, vol. 2442 of *LNCS*, Yung, M. (ed.). Springer, Heidelberg.

Vaudenay, S. (2003). The security of DSA and ECDSA. In *PKC 2003*, vol. 2567 of *LNCS*, Desmedt, Y. (ed.). Springer, Heidelberg.

# 3 零知识证明

**Ivan VISCONTI**

*意大利萨莱诺大学*

## 3.1 简介

考虑以下典型场景：Peggy 声称某事，然后告诉 Victor：“这是真的，相信我”。Victor 希望获得证据证明该声称是真实的，因为他并不完全信任 Peggy。与此同时，Peggy 不想透露一些能证明她声称真实性的机密信息。如果 Peggy 和 Victor 都完全信任的第三方 Trinity 愿意提供帮助，那么 Peggy 可以将她关于该声称所知的一切透露给 Trinity，一旦 Trinity 确信该声称是真的，就可以告知 Victor 该声称的真实性，同时遗忘从 Peggy 那里收到的信息。然而，Peggy 和 Victor 希望在不涉及他人的情况下解决他们的争端，因此他们想知道，在没有可信第三方的情况下，Victor 如何能在保护 Peggy 隐私的前提下被说服某个声称的真实性。

1985 年，Goldwasser 等人将上述双方博弈形式化，引入了“交互式零知识证明系统”的概念。在上述场景中，Peggy 扮演证明者 `P` 的角色，而 Victor 扮演验证者 `V` 的角色。该声称被形式化为一个实例 `x`，声称其属于语言 `L`。`P` 和 `V` 都知道 `x` 和 `L` 的描述，并进行某种定义明确的消息交换，以便最终 `P` 能说服 `V` 相信 `x ∈ L`。这是一个基本的正确性属性，称为“完备性”，对应于当 Peggy 的声称为真时，她能够说服 Victor。如果 Peggy 恶意地试图证明一个虚假的声称，对 Victor 的保护称为“可靠性”，要求 `V` 在交互结束时被说服相信一个虚假声称的真实性（即 `x ∉ L` 但 `V` 被说服 `x ∈ L`）的概率很低，即使与对手 `P^⋆` 交互也是如此。如果对手 Victor 对获取某些机密信息感兴趣，对 Peggy 的保护称为“零知识”（ZK）。为了恰当地定义机密信息不泄露，Goldwasser 等人引入了模拟范式：对手 `V^⋆` 在与 `P` 交换消息期间学到的信息，本质上是 `V^⋆` 已经知道的信息，意思是 `V^⋆` 无需与 `P` 交互，仅运行一个称为模拟器的特殊高效算法就能生成相同的信息。
