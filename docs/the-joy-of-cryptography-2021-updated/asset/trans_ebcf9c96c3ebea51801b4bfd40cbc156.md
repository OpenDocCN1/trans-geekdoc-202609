
以这种方式进行分解是：

```
(pk, sk) ← Σ_pub.KeyGen
GETPK():
  return pk
CHALLENGE(m_L, m_R):
  tk' ← Σ_sym.KeyGen
  c_pub ← Σ_pub.Enc(pk, tk')
  c_sym ← CHALLENGE'(m_L, m_R)
  return (c_pub, c_sym)
◇
L^{Σ_sym}_{ots-L}
CHALLENGE'(m_L, m_R):
  tk ← Σ_sym.KeyGen
  return Σ_sym.Enc(tk, m_L)
```

此时，我们可以用 L_ots-R 替换 L_ots-L。做出此更改后，Σ_sym 密文加密的是 m_R 而不是 m_L。这是证明的“中点”，其余步骤是之前步骤的镜像。总结：我们先内联 L_ots-R，然后应用 CPA 安全性将 tk' 的 Σ_pub 加密替换为 tk。结果正是 L_pk-cpa-R，如所期望。

## 练习

- 15.1. 证明主张 15.3。

- 15.2. 证明存在双消息密钥协议当且仅当存在 CPA 安全的公钥加密。

  换句话说，请展示如何从任意双消息 KA 协议构造 CPA 安全的加密方案，反之亦然。证明你的构造的安全性。

- 15.3. (a) 假设给定未知明文 M ∈ G 的 ElGamal 加密，请展示如何构造另一个也能解密为相同 M 的密文。

  (b) 假设给定两个 ElGamal 加密，分别对应未知明文 M1, M2 ∈ G，请展示如何构造一个解密为它们乘积 M1 · M2 的密文。

- 15.4. 假设你得到两个加密未知明文 M1 和 M2 的 ElGamal 密文 (B1, C1)、(B2, C2)。假设你还知道公钥 A 和循环群生成元 g。

  (a) 如果观察到 B1 = B2，你可以推断出关于 M1 和 M2 的哪些信息？

  (b) 如果观察到 B1 = g · B2，你可以推断出关于 M1 和 M2 的哪些信息？

  ★ (c) 如果观察到 B1 = (B2)^2，你可以推断出关于 M1 和 M2 的哪些信息？

## 安全定义索引

### 对称密钥加密的一次性统一密文（定义 2.5）:

```
L^Σ_ots$-real
CTXT(m ∈ Σ.M):
  k ← Σ.KeyGen
  c ← Σ.Enc(k, m)
  return c
```

```
L^Σ_ots$-rand
CTXT(m ∈ Σ.M):
  c ← Σ.C
  return c
```

### 对称密钥加密的一次性保密性（定义 2.6）:

```
L^Σ_ots-L
EAVESDROP(m_L, m_R ∈ Σ.M):
  k ← Σ.KeyGen
  c ← Σ.Enc(k, m_L)
  return c
```

```
L^Σ_ots-R
EAVESDROP(m_L, m_R ∈ Σ.M):
  k ← Σ.KeyGen
  c ← Σ.Enc(k, m_R)
  return c
```

### t-out-of-n 秘密共享（定义 3.3）:

```
L^Σ_tsss-L
SHARE(m_L, m_R ∈ Σ.M, U):
  if |U| ≥ Σ.t: return err
  s ← Σ.Share(m_L)
  return {s_i | i ∈ U}
```

```
L^Σ_tsss-R
SHARE(m_L, m_R ∈ Σ.M, U):
  if |U| ≥ Σ.t: return err
  s ← Σ.Share(m_R)
  return {s_i | i ∈ U}
```

### 伪随机生成器（定义 5.1）:

```
L^G_prg-real
QUERY():
  s ← {0, 1}^λ
  return G(s)
```

```
L^G_prg-rand
QUERY():
  r ← {0, 1}^{λ+ℓ}
  return r
```

### 伪随机函数（定义 6.1）:

```
L^F_prf-real
k ← {0, 1}^λ
LOOKUP(x ∈ {0, 1}^in):
  return F(k, x)
```

```
L^F_prf-rand
T := empty assoc. array
LOOKUP(x ∈ {0, 1}^in):
  if T[x] undefined:
    T[x] ← {0, 1}^out
  return T[x]
```

### 伪随机置换（定义 6.6）:

```
L_prp-real^F

k ← {0, 1}^λ

LOOKUP(x ∈ {0, 1}^blen):
  return F(k, x)
```

```
L_prp-rand^F

T := empty assoc. array

LOOKUP(x ∈ {0, 1}^blen):
  if T[x] undefined:
    T[x] ← {0, 1}^blen \ T.values
  return T[x]
```

### 强伪随机置换（定义 6.13）:

```
L_sprp-real^F

k ← {0, 1}^λ

LOOKUP(x ∈ {0, 1}^blen):
  return F(k, x)

INVLOOKUP(y ∈ {0, 1}^blen):
  return F⁻¹(k, y)
```

```
L_sprp-rand^F

T, T_inv := empty assoc. arrays

LOOKUP(x ∈ {0, 1}^blen):
  if T[x] undefined:
    y ← {0, 1}^blen \ T.values
    T[x] := y; T_inv[y] := x
  return T[x]

INVLOOKUP(y ∈ {0, 1}^blen):
  if T_inv[y] undefined:
    x ← {0, 1}^blen \ T_inv.values
    T_inv[y] := x; T[x] := y
  return T_inv[y]
```

### 对称密钥加密的 CPA 安全性（定义 7.1，第 8.2 节）:

```
L_cpa-L^Σ

k ← Σ.KeyGen

EAVESDROP(m_L, m_R ∈ Σ.M):
  if |m_L| ≠ |m_R| return err
  c := Σ.Enc(k, m_L)
  return c
```

```
L_cpa-R^Σ

k ← Σ.KeyGen

EAVESDROP(m_L, m_R ∈ Σ.M):
  if |m_L| ≠ |m_R| return err
  c := Σ.Enc(k, m_R)
  return c
```

### 对称密钥加密的 CPA$ 安全性（定义 7.2，第 8.2 节）:

```
L_cpa$-real^Σ

k ← Σ.KeyGen

CHALLENGE(m ∈ Σ.M):
  c := Σ.Enc(k, m)
  return c
```

```
L_cpa$-rand^Σ

CHALLENGE(m ∈ Σ.M):
  c ← Σ.C(|m|)
  return c
```

### 对称密钥加密的 CCA 安全性（定义 9.1）:

$\mathcal{L}_{\text{cca-L}}^{\Sigma}$
\(k \leftarrow \Sigma.\text{KeyGen}\)
\(\mathcal{S} := \emptyset\)
\(\underline{\text{EAVESDROP}(m_L, m_R \in \Sigma.\mathcal{M}):}\)
if \(|m_L| \neq |m_R|\) return err
\(c := \Sigma.\text{Enc}(k, m_L)\)
\(\mathcal{S} := \mathcal{S} \cup \{c\}\)
return \(c\)
\(\underline{\text{DECRYPT}(c \in \Sigma.\mathcal{C}):}\)
if \(c \in \mathcal{S}\) return err
return \(\Sigma.\text{Dec}(k, c)\)

$\mathcal{L}_{\text{cca-R}}^{\Sigma}$
\(k \leftarrow \Sigma.\text{KeyGen}\)
\(\mathcal{S} := \emptyset\)
\(\underline{\text{EAVESDROP}(m_L, m_R \in \Sigma.\mathcal{M}):}\)
if \(|m_L| \neq |m_R|\) return err
\(c := \Sigma.\text{Enc}(k, m_R)\)
\(\mathcal{S} := \mathcal{S} \cup \{c\}\)
return \(c\)
\(\underline{\text{DECRYPT}(c \in \Sigma.\mathcal{C}):}\)
if \(c \in \mathcal{S}\) return err
return \(\Sigma.\text{Dec}(k, c)\)

### 对称密钥加密的 CCA$ 安全性（定义 9.2）:

$\mathcal{L}_{\text{cca\$-real}}^{\Sigma}$
\(k \leftarrow \Sigma.\text{KeyGen}\)
\(\mathcal{S} := \emptyset\)
\(\underline{\text{CTXT}(m \in \Sigma.\mathcal{M}):}\)
\(c := \Sigma.\text{Enc}(k, m)\)
\(\mathcal{S} := \mathcal{S} \cup \{c\}\)
return \(c\)
\(\underline{\text{DECRYPT}(c \in \Sigma.\mathcal{C}):}\)
if \(c \in \mathcal{S}\) return err
return \(\Sigma.\text{Dec}(k, c)\)

$\mathcal{L}_{\text{cca\$-rand}}^{\Sigma}$
\(k \leftarrow \Sigma.\text{KeyGen}\)
\(\mathcal{S} := \emptyset\)
\(\underline{\text{CTXT}(m \in \Sigma.\mathcal{M}):}\)
\(c \leftarrow \Sigma.\mathcal{C}(|m|)\)
\(\mathcal{S} := \mathcal{S} \cup \{c\}\)
return \(c\)
\(\underline{\text{DECRYPT}(c \in \Sigma.\mathcal{C}):}\)
if \(c \in \mathcal{S}\) return err
return \(\Sigma.\text{Dec}(k, c)\)

### MAC（定义 10.2）:

$\mathcal{L}_{\text{mac-real}}^{\Sigma}$
\(k \leftarrow \Sigma.\text{KeyGen}\)
\(\underline{\text{GETTAG}(m \in \Sigma.\mathcal{M}):}\)
return \(\Sigma.\text{MAC}(k, m)\)
\(\underline{\text{CHECKTAG}(m \in \Sigma.\mathcal{M}, t):}\)
return \(t \stackrel{?}{=} \Sigma.\text{MAC}(k, m)\)

$\mathcal{L}_{\text{mac-fake}}^{\Sigma}$
\(k \leftarrow \Sigma.\text{KeyGen}\)
\(\mathcal{T} := \emptyset\)
\(\underline{\text{GETTAG}(m \in \Sigma.\mathcal{M}):}\)
\(t := \Sigma.\text{MAC}(k, m)\)
\(\mathcal{T} := \mathcal{T} \cup \{(m, t)\}\)
return \(t\)
\(\underline{\text{CHECKTAG}(m \in \Sigma.\mathcal{M}, t):}\)
return \((m, t) \stackrel{?}{\in} \mathcal{T}\)

### 抗碰撞性（定义 11.1）:

```
L^H_cr-real
s ← {0, 1}^λ
GETSALT():
  return s
TEST(x, x' ∈ {0, 1}*):
  if x != x' and H(s, x) = H(s, x'): return true
  return false
```

```
L^H_cr-fake
s ← {0, 1}^λ
GETSALT():
  return s
TEST(x, x' ∈ {0, 1}*):
  return false
```

### 数字签名（定义 13.6）:

```
L^Σ_sig-real
(vk, sk) ← Σ.KeyGen
GETVK():
  return vk
GETSIG(m):
  return Σ.Sign(sk, m)
VERSIG(m, sigma):
  return Σ.Ver(vk, m, sigma)
```

```
L^Σ_sig-fake
(vk, sk) ← Σ.KeyGen
S := ∅
GETVK():
  return vk
GETSIG(m):
  sigma := Σ.Sign(sk, m)
  S := S ∪ {(m, sigma)}
  return sigma
VERSIG(m, sigma):
  return (m, sigma) ∈ S
```

### 密钥协议（定义 14.4）:

```
L^Σ_ka-real
QUERY():
  (t, K) ← EXECPROT(Σ)
  return (t, K)
```

```
L^Σ_ka-rand
QUERY():
  (t, K) ← EXECPROT(Σ)
  K' ← Σ.K
  return (t, K')
```

### 决策性 Diffie-Hellman 假设（定义 14.5）:

```
L^G_dh-real
QUERY():
  a, b ← Z_n
  return (g^a, g^b, g^{ab})
```

```
L^G_dh-rand
QUERY():
  a, b, c ← Z_n
  return (g^a, g^b, g^c)
```
