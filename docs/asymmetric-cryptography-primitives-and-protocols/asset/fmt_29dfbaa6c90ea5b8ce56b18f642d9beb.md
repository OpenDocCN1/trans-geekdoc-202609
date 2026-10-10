
# Phan, D., Safavi-Naini, R., Tonien, D. (2006). Generic construction of hybrid public key traitor tracing with full-public-traceability. In *ICALP 2006, Part II*, vol. 4052 of *LNCS*, Bugliesi, M., Preneel, B., Sassone, V., Wegener, I. (eds). Springer, Heidelberg.

# Phan, D.H., Pointcheval, D., Shahandashti, S.F., Strefler, M. (2013). Adaptive CCA broadcast encryption with constant-size secret keys and ciphertexts. *International Journal of Information Security*, 12(4), 251–265.

# Regev, O. (2005). On lattices, learning with errors, random linear codes, and cryptography. In *37th ACM STOC*, Gabow, H.N., Fagin, R. (eds). ACM Press.

# Regev, O. (2010). On the complexity of lattice problems with polynomial approximation factors. In *The LLL Algorithm – Survey and Applications*, Nguyen, P.Q., Vallée, B. (eds). Information Security and Cryptography, Springer, Heidelberg.

# Rivest, R.L. (1997). All-or-nothing encryption and the package transform. In *FSE’97*, vol. 1267 of *LNCS*, Biham, E. (ed.). Springer, Heidelberg.

# Safavi-Naini, R. and Wang, Y. (2003a). Sequential traitor tracing. *IEEE Transactions on Information Theory*, 49(5), 1319–1326.

# Safavi-Naini, R. and Wang, Y. (2003b). Traitor tracing for shortened and corrupted fingerprints. In *DRM 2003*, vol. 2696 of *LNCS*, Feigenbaum, J. (ed.). Springer, Heidelberg.

# Sahai, A. and Waters, B.R. (2005). Fuzzy identity-based encryption. In *EUROCRYPT 2005*, vol. 3494 of *LNCS*, Cramer, R. (ed.). Springer, Heidelberg.

# Sakai, R., Ohgishi, K., Kasahara, M. (2000). Cryptosystems based on pairing. In *SCIS 2000*, Okinawa, Japan.

# Silverberg, A., Staddon, J., Walker, J.L. (2001). Efficient traitor tracing algorithms using list decoding. In *ASIACRYPT 2001*, vol. 2248 of *LNCS*, Boyd, C. (ed.). Springer, Heidelberg.

# Sirvent, T. (2007). Traitor tracing scheme with constant ciphertext rate against powerful pirates. In *Proceedings of the Workshop on Coding and Cryptography (WCC’07)*, Versailles, France.

# Stinson, D.R. and Wei, R. (1998). Combinatorial properties and constructions of traceability schemes and frameproof codes. *SIAM Journal on Discrete Mathematics*, 11(1), 41–53.

# Stinson, D.R. and Wei, R. (1999). Key preassigned traceability schemes for broadcast encryption. In *SAC 1998*, vol. 1556 of *LNCS*, Tavares, S.E., Meijer, H. (eds). Springer, Heidelberg.

# Tardos, G. (2003). Optimal probabilistic fingerprint codes. In *35th ACM STOC*. ACM Press.

# Tô, V.D., Safavi-Naini, R., Zhang, F. (2003). New traitor tracing schemes using bilinear map. In *Digital Rights Management – DRM ‘03*, Feigenbaum, J., Sander, T., Yung, M. (eds). ACM Press.

# Trung, T.V. and Martirosyan, S. (2005). New constructions for IPP codes. *Designs, Codes and Cryptography*, 35(2), 227–239.

# Tzeng, W.-G. and Tzeng, Z.-J. (2001). A public-key traitor tracing scheme with revocation using dynamic shares. In *PKC 2001*, vol. 1992 of *LNCS*, Kim, K. (ed.). Springer, Heidelberg.

# Watanabe, Y., Hanaoka, G., Imai, H. (2001). Efficient asymmetric public-key traitor tracing without trusted agents. In *CT-RSA 2001*, vol. 2020 of *LNCS*, Naccache, D. (ed.). Springer, Heidelberg.

# Waters, B. (2009). Dual system encryption: Realizing fully secure IBE and HIBE under simple assumptions. In *CRYPTO 2009*, vol. 5677 of *LNCS*, Halevi, S. (ed.). Springer, Heidelberg.

# Zhandry, M. (2020). New techniques for traitor tracing: Size *N*^(1*/*3) and more from pairings. In *CRYPTO 2020, Part I*, vol. 12170 of *LNCS*, Micciancio, D., Ristenpart, T. (eds). Springer, Heidelberg.

# 7 Attribute-Based Encryption

**Romain GAY**

*IBM Research Zurich, Switzerland*

## 7.1 Introduction

In this chapter, we present encryption schemes with fine-grained access to the encrypted plaintext, as opposed to the all-or-nothing access achieved by traditional public-key encryption schemes. These are referred to as attribute-based encryption schemes (ABE). Namely, in an ABE scheme, the setup generates a public key and a so-called master secret key. The public key can be used by anyone to encrypt a plaintext associated with a policy access that can be represented for instance as a Boolean formula. There is an additional algorithm that given as input the master secret key and an attribute generates a user secret key (for that specific attribute). Decryption takes a ciphertext and a user secret key, and succeeds in recovering the plaintext if and only if the attribute of the user secret key satisfies the formula embedded in the ciphertext. If an adversary gets hold of some user secret keys, where none which is supposed to decrypt, then the confidentiality of the encrypted plaintext is preserved.

We present here ABE schemes from pairing groups (which are described at length in [Chapter 5](#c05.xhtml)). We follow a modular approach, where the ABE is obtained starting with a simple statistical primitive called predicate encoding that only satisfies a weak notion of security (only secure when one user secret key is corrupted), which is then generically transformed into a secret-key ABE, that is, an ABE where the encryption algorithm requires the master-secret key (and not just the public key). Finally, this secret-key ABE itself is turned into an ABE, where the encryption is public-key. [Figure 7.1](#c07.xhtml#c7-fig-1) describes this two-step approach. When instantiated with existing predicate encodings, this generic construction yields ABE for different classes of access polices, such as Boolean formulae or identity-based encryption (IBE). We also provide such predicate encodings for completeness and to illustrate the versatility of the modular approach.

*Organization of the chapter*: In the first section, we recall some basics about pairing groups and the computational assumptions of use (more details are provided in [Chapter 5](#c05.xhtml)). In the second section, we give the definition of predicate encodings and give some concrete constructions for IBE and Boolean formulae. In the third section, we show how to generically convert a predicate encoding into a secret-key ABE, then into an ABE (where the encryption algorithm is public-key). We conclude by a brief historical note on ABE.

## 7.2 Pairing groups

Here, we recall some definitions from [Chapter 5](#c05.xhtml) but with our notations. Throughout this chapter, we write column vectors as (*x*[1]*,..., x[n]*) ∈ ![image](images/z1.jpg)^(*n*) and row vectors as (*u*[1]|··· |*u[n]*) ∈ ![image](images/z1.jpg)^(1×*n*).

### 7.2.1 Cyclic groups

We use a PPT algorithm `GGen`(1^(*λ*)) that on input the security parameter (in unary) *λ* ∈ ![image](images/n1.jpg) generates a cyclic group ![image](images/g1.jpg) of order *p*, where *p* is a 2*λ*\-bit prime. We use additive bracket notations, where *P* is a generator of ![image](images/g1.jpg), and for all *a* ∈ ![image](images/z1.jpg)[*p*], we write \[*a*\] = *aP* ∈ ![image](images/g1.jpg). Similarly for any matrix ![image](images/i123.jpg) we write \[**A**\] = **A***P* ∈ ![image](images/g1.jpg)^(*m*×*n*), where the multiplication is performed component-wise. This choice of notations implies that for all matrices ![image](images/i124.jpg)

We say the DDH assumption holds with respect to `GGen` if for all PPT adversaries ![image](images/a.jpg), there exists a negligible function *ν* such that for all ![image](images/i125.jpg) where the advantage ![image](images/i126.jpg) is defined as follows:

![image](images/p152-1.jpg)

### 7.2.2 Pairing groups
