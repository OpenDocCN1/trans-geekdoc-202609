

## 双服务器 PAKE (2-PAKE)

当 (*t*, *n*) = (1, 2) 时的 T-PAKE 称为双服务器 PAKE 或 *2-PAKE*。在 PKI 模型中，测试已注册的秘密共享密码与客户端 `C` 提交的秘密共享密码之间的相等性，等同于秘密共享数据的相等性测试。这催生了 Brainard 等人 (2003) 和 Szydlo 与 Kaliski Jr. (2005) 的 PKI 模型 2-PAKE，两者均仅使用两台服务器之间交换的三条消息。Katz 等人 (2005) 在仅密码设置下（带 CRS）给出了一种高效的 2-PAKE，仅需 5 个消息流，在标准模型下基于 DDH 假设安全，即非 ROM。（Katz 等人 (2005) 的 2-PAKE 推广由 Kiefer 和 Manulis (2014) 给出。）Camenisch 等人 (2012) 在仅密码设置下展示了一种双服务器 TPASS，这意味着一种 2-PAKE，但他们的协议在 ROM 中基于 DDH 假设需要 6 个消息流。Camenisch 等人 (2015a) 展示了具有*主动安全性*的双服务器 TPASS，即针对瞬态故障的安全性 (Ostrovsky 和 Yung 1991; Herzberg 等人 1995)，这意味着 2-PAKE 具有同等级别的安全性。Yang 等人 (2006) 和 Jin 等人 (2008) 给出了其他 2-PAKE，与 Katz 等人 (2005) 相比消息数量略有减少，但其基于 DDH 的安全性论证仅略显非正式。2-PAKE 的概念也在 UC 设置中由 Zhang 等人 (2016) 和 Kiefer 与 Manulis (2016) 进行了形式化。

## 分布式密码验证

Camenisch 等人 (2015b) 给出了*分布式密码验证* (DPV) 协议的 UC 定义。DPV 协议类似于 PKI 模型中的 T-PAKE，但指定的一台服务器（例如 `S[1]`）在登录时能以明文形式获取客户端的密码，DPV 协议允许 `S[1]` 和其余的 `S[i]` 确认该密码是否与密码注册期间秘密共享的密码（或加盐密码哈希，见[第 10.8 节](#c10.xhtml#sec10-8)）相对应。因此，DPV 协议专门定制用于允许使用密码传输 TLS 方法（见[第 10.8 节](#c10.xhtml#sec10-8)）认证客户端的服务器对用户的密码数据进行秘密共享，同时仍能高效地对其进行认证。Camenisch 等人 (2015b) 的 DPV 协议仅支持 *t* = *n* - 1 的情况，`S[1]` 仅使用 3 次指数运算，每个其他 `S[i]` 仅使用 1 次指数运算，支持主动更新，并在 ROM 中基于 OM-DH 假设安全。

Everspaugh 等人 (2015) 利用*部分无感 PRF* (POPRF) 的阈值实现，构建了通用 (*t*, *n*) 阈值情况下的 DPV。其思路类似于 Ford-Kaliski 密码强化 (Ford 和 Kaliski Jr. 2000)，但与 Boyen (2009a) 和 Jarecki 等人 (2018) 的 saPAKE 不同，POPRF 客户端的角色由服务器 `S[1]` 扮演，而非远程用户。他们的计算成本略高于 (Camenisch 等人 2015b)，因为他们的方案使用了双线性映射群，并且他们仅给出了基于游戏的安全性分析，在 ROM 中基于 OM-DH 假设。Schneider 等人 (2016) 和 Lai 等人 (2017) 给出了针对 *n* = 2 台服务器特定情况的其他 DPV 方案，但他们通过包含仅更新每台服务器存储密钥的主动更新扩展了 DPV 功能，因此具有 *O*(1) 带宽，然后仅服务器 `S[1]` 在本地执行 *O*(*m*) 工作量来更新 *m* 个用户的（加密）密码数据。

## 10.10. 参考文献

Abdalla, M. and Pointcheval, D. (2005). Simple password-based encrypted key exchange protocols, In *CT-RSA 2005*, vol. 3376 of *LNCS*, Menezes, A. (ed.). Springer, Heidelberg.

Abdalla, M., Chevassut, O., Fouque, P.-A., Pointcheval, D. (2005a). A simple threshold authenticated key exchange from short secrets. In *ASIACRYPT 2005*, vol. 3788 of *LNCS*, Roy, B.K. (ed.). Springer, Heidelberg.

Abdalla, M., Fouque, P.-A., Pointcheval, D. (2005b). Password-based authenticated key exchange in the three-party setting. In *PKC 2005*, vol. 3386 of *LNCS*, Vaudenay, S. (ed.). Springer, Heidelberg.

Abdalla, M., Catalano, D., Chevalier, C., Pointcheval, D. (2008). Efficient two-party password-based key exchange protocols in the UC framework. In *CT-RSA 2008*, vol. 4964 of *LNCS*, Malkin, T. (ed.). Springer, Heidelberg.

Abdalla, M., Chevalier, C., Pointcheval, D. (2009). Smooth projective hashing for conditionally extractable commitments. In *CRYPTO 2009*, vol. 5677 of *LNCS*, Halevi, S. (ed.). Springer, Heidelberg.

Abdalla, M., Bellare, M., Neven, G. (2010). Robust encryption. In *TCC 2010*, vol. 5978 of *LNCS*, Micciancio, D. (ed.). Springer, Heidelberg.

Abdalla, M., Benhamouda, F., Blazy, O., Chevalier, C., Pointcheval, D. (2013). SPHF-friendly non-interactive commitments. In *ASIACRYPT 2013, Part I*, vol. 8269 of *LNCS*, Sako, K., Sarkar, P. (eds). Springer, Heidelberg.

Abdalla, M., Benhamouda, F., MacKenzie, P.D. (2015a). Security of the J-PAKE password-authenticated key exchange protocol. In *2015 IEEE Symposium on Security and Privacy*. IEEE Computer Society Press.

Abdalla, M., Benhamouda, F., Pointcheval, D. (2015b). Public-key encryption indistinguishable under plaintext-checkable attacks. In *PKC 2015*, vol. 9020 of *LNCS*, Katz, J. (ed.). Springer, Heidelberg.

Abdalla, M., Cornejo, M., Nitulescu, A., Pointcheval, D. (2016). Robust password-protected secret sharing. In *ESORICS 2016, Part II*, vol. 9879 of *LNCS*, Askoxylakis, I.G., Ioannidis, S., Katsikas, S.K., Meadows, C.A. (eds). Springer, Heidelberg.

Abdalla, M., Barbosa, M., Bradley, T., Jarecki, S., Katz, J., Xu, J. (2020). Universally composable relaxed password authenticated key exchange. In *CRYPTO 2020, Part I*, vol. 12170 of *LNCS*., Micciancio, D., Ristenpart, T. (eds). Springer, Heidelberg.

Bagherzandi, A., Jarecki, S., Saxena, N., Lu, Y. (2011). Password-protected secret sharing. In *ACM CCS 2011*, Chen, Y., Danezis, G., Shmatikov, V. (eds). ACM Press.

Barak, B., Canetti, R., Lindell, Y., Pass, R., Rabin, T. (2005). Secure computation without authentication. In *CRYPTO 2005*, vol. 3621 of *LNCS*, Shoup, V. (ed.). Springer, Heidelberg.

Beaver, D. (1991). Secure multiparty protocols and zero-knowledge proof systems tolerating a faulty minority. *Journal of Cryptology*, 4(2), 75–122.

Bellare, M. and Rogaway, P. (1993). Random oracles are practical: A paradigm for designing efficient protocols. In *ACM CCS 93*, Denning, D.E., Pyle, R., Ganesan, R., Sandhu, R.S., Ashby, V. (eds), ACM Press.

Bellare, M. and Rogaway, P. (1994). Entity authentication and key distribution. In *CRYPTO’93*, vol. 773 of *LNCS*, Stinson, D.R. (ed.). Springer, Heidelberg.

Bellare, M. and Rogaway, P. (2000). The AuthA protocol for password-based authenticated key exchange. IEEE P1363, 14 March.

Bellare, M., Canetti, R., Krawczyk, H. (1998). A modular approach to the design and analysis of authentication and key exchange protocols (extended abstract). In *30th ACM STOC*. ACM Press.

Bellare, M., Pointcheval, D., Rogaway, P. (2000). Authenticated key exchange secure against dictionary attacks. In *EUROCRYPT 2000*, vol. 1807 of *LNCS*, Preneel, B. (ed.). Springer, Heidelberg.

Bellare, M., Boldyreva, A., Desai, A., Pointcheval, D. (2001). Key-privacy in public-key encryption. In *ASIACRYPT 2001*, vol. 2248 of *LNCS*, Boyd, C. (ed.). Springer, Heidelberg.

Bellovin, S.M. and Merritt, M. (1992). Encrypted key exchange: Password-based protocols secure against dictionary attacks. In *1992 IEEE Symposium on Research in Security and Privacy*, May.

Bellovin, S.M. and Merritt, M. (1993). Augmented encrypted key exchange: A password-based protocol secure against dictionary attacks and password file compromise. In *ACM CCS 93*, Denning, D.E., Pyle, R., Ganesan, R., Sandhu, R.S., Ashby, V. (eds). ACM Press.

Ben-Or, M., Goldwasser, S., Wigderson, A. (1988). Completeness theorems for non-cryptographic fault-tolerant distributed computation (extended abstract). In *20th ACM STOC*. ACM Press.

