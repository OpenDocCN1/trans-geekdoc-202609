
## 7.4. Attribute-based encryption

### 7.4.1. Definition

**DEFINITION 7.3 (ABE).** Let *s* be a polynomial, and ![image](images/i177.jpg) be a family such that for all *λ* ∈ ![image](images/n1.jpg), ![image](images/p.jpg)[*λ*] is a set of predicates on *s*(*λ*)-bits inputs, that is, ![image](images/p.jpg)[*λ*] ⊆ *P* : {0, 1}^(*s*(*λ*)) → {0, 1}. An ABE for ![image](images/i178.jpg) is a tuple of PPT algorithms (`Setup`, `Enc`, `KeyGen`, `Dec`) that fulfills the syntax, correctness and security properties described below.

#### 7.4.1.1. Syntax

- `Setup`(1^(*λ*)) → (`mpk`, `msk`). Given as input the security parameter *λ* ∈ ![image](images/n1.jpg) (in unary), it outputs a master public key `mpk` and a master secret key `msk`.
- `Enc`(`mpk`, *P*) → (`ct`, `kem`). Given as input the master public key `mpk` and a predicate *P* ∈ ![image](images/p.jpg)[*λ*], it outputs a ciphertext `ct` and a symmetric key `kem` in a key space ![image](images/k1.jpg)[*λ*].
- `KeyGen`(`msk`, `att`) → `usk`. Given as input the master secret key `msk` and an attribute `att` ∈ {0, 1}^(*s*(*λ*)), it outputs a user secret key `usk`.
- `Dec`(`mpk`, `ct`, `usk`) → `kem`. Given as input the master public key `mpk`, a ciphertext `ct` and a user secret key `usk`, it outputs a symmetric key `kem`.

#### 7.4.1.2. Correctness

For all *λ* ∈ ![image](images/n1.jpg), all (`mpk`, `msk`) in the support of `Setup`(1^(*λ*)), all *P* ∈ ![image](images/p.jpg)[*λ*], all (`ct`, `kem`) in the support of `Enc`(`mpk`, *P*), all attributes `att` ∈ {0, 1}^(*s*(*λ*)) such that *P*(`att`) = 1, all `usk` in the support of `KeyGen`(`msk`, `att`), we have: `Dec`(`mpk`, `ct`, `usk`) = `kem`.

#### 7.4.1.3. Security

For all PPT stateful adversaries ![image](images/a.jpg) and all ![image](images/abe.jpg) = (`Setup`, `Enc`, `KeyGen`, `Dec`), we define the following advantage function:

![image](images/p157-1.jpg)

where the oracle ![image](images/o.jpg)`KeyGen`, when given as input an attribute `att` ∈ {0, 1}^(*s*(*λ*)), outputs `KeyGen`(`msk`, `att`). We say ![image](images/a.jpg) is an *admissible* adversary if it chooses a predicate *P* and queries its oracle ![image](images/o.jpg)`KeyGen` on inputs `att`[1], ..., `att`[*q*] such that *P*(`att`[*i*]) = 0 for all *i* = 1, ..., *q*. That is, none of the queried user secret keys decrypt the challenge ciphertext. We say ![image](images/abe.jpg) is secure if for all PPT admissible adversaries ![image](images/a.jpg), there exists a negligible function *ν* such that for all ![image](images/i179.jpg).

#### 7.4.1.4. Secret-key ABE

We say an ABE is secret-key if the encryption algorithm takes as an additional input the master secret key. Note that security is defined above for an adversary that receives a single ct-kem pair, whereas real-world attacks involve many such pairs. For a (public-key) ABE, security with many ct-kem pairs is implied by security with one ct-kem pair straightforwardly. However, this implication does not hold for secret-key ABE. Otherwise said, the security definition given above is weak for secret-key ABE. This is not an issue since secret-key ABE will only be used as a building block for public-key ABE.

### 7.4.2. A modular construction

In this section, we show how to transform generically predicate encodings into secret-key ABE, then into ABE (see [Figure 7.1](#c07.xhtml#c7-fig-1)).

![Figure 7.1. Security features of predicate encoding, secret-key ABE and ABE](images/fig7-1.jpg)

[**Figure 7.1.**](#c07.xhtml#rc7-fig-1) *Security features of predicate encoding, secret-key ABE and ABE*

#### 7.4.2.1. From predicate encodings to secret-key ABE

Let *s* be a polynomial and ![image](images/i180.jpg) be a family of predicates. Assume there exists a PPT algorithm `GGen` such that for all *λ* ∈ ![image](images/n1.jpg), `GGen`(1^(*λ*)) outputs a group ![image](images/g1.jpg)[*λ*] of prime order *p*[*λ*], and such that the DDH assumption holds with respect to `GGen`. Assume there exist polynomials |`ct`|, |`usk`|, *n* such that for all *λ* ∈ ![image](images/n1.jpg), there exists a predicate encoding (`EncCt`[*λ*], `EncKey`^(*λ*), `Decode`[*λ*]) with respect to (*p*[*λ*], |`ct`|(*λ*), |`usk`|(*λ*), *n*(*λ*), *P*[*λ*]). Then, the construction presented below is a secret-key ABE. Note that to keep notations light, we do not explicitly write the dependency on *λ* from here on. We describe informally the transformation from predicate encodings to secret-key ABE in [Figure 7.2](#c07.xhtml#c7-fig-2).

![Figure 7.2. Transformation from predicate encoding to secret-key ABE. Here, C = EncCt(P) for a predicate P and K = EncKey(att) for attribute att ∈ {0, 1}s](images/fig7-2.jpg)

[**Figure 7.2.**](#c07.xhtml#rc7-fig-2) *Transformation from predicate encoding to secret-key ABE. Here,* C = `EncCt`(*P*) *for a predicate P and* K = `EncKey`(`att`) *for attribute* `att` ∈ {0, 1}[*s*]

- `Setup`(1^(*λ*)): `GGen`(1^(*λ*)) → ![image](images/g1.jpg) of order ![image](images/i181.jpg) `msk` = (**U**, *α*, [**a**], [**Ua**]), `mpk` = ![image](images/g1.jpg). It outputs (`mpk`, `msk`).
- `Enc`(`msk`, `mpk`, *P*): `EncCt`(*P*) → ![image](images/i182.jpg) `ct` = **U**^⊤**C**, *P*, `kem` = [*α*] ∈ ![image](images/g1.jpg). It outputs (`ct`, `kem`).
- `KeyGen`(`msk`, `att`): `EncKey`(`att`) → ![image](images/i183.jpg) *r* ← ![image](images/z1.jpg)[*p*], `usk` = ![image](images/i184.jpg) It outputs `usk`.
- `Dec`(`mpk`, `ct`, `usk`): Parse `ct` = (**V**, *P*) with ![image](images/i185.jpg) ([**w**^⊤], [**z**], `att`) with [**w**^⊤] ∈ ![image](images/g1.jpg)^(1×|`usk`|), [**z**] ∈ ![image](images/g1.jpg)². `Decode`(*P*, `att`) → ![image](images/i186.jpg) It outputs [**z**]^⊤**V** | [**w**^⊤] **d** ∈ ![image](images/g1.jpg).

**Correctness**: Let *P* and `att` such that *P*(`att`) = 1. The encryption `Enc`(`msk`, `mpk`, *P*) outputs `ct` = (**U**^⊤**C**, *P*) where **C** = `EncCt`(*P*). The user secret key generation `KeyGen`(`msk`, `att`) outputs `usk` = ([*α*, **Ua** *r*]^⊤**K**, [**a** *r*], `att`) where **K** = `EncKey`(`att`). Decryption computes ![image](images/i187.jpg) ![image](images/i188.jpg) where the last equality follows from the correctness of the predicate encoding.
