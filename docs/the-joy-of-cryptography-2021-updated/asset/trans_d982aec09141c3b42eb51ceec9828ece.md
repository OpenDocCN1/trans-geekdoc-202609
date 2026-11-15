

## 公钥加密的 CPA 安全性 (定义 15.1):

L^\Sigma_{pk-cpa-L}
(pk, sk) <- Sigma.KeyGen
GETPK():
return pk
CHALLENGE(m_L, m_R \in Sigma.M):
return Sigma.Enc(pk, m_L)

L^\Sigma_{pk-cpa-R}
(pk, sk) <- Sigma.KeyGen
GETPK():
return pk
CHALLENGE(m_L, m_R \in Sigma.M):
return Sigma.Enc(pk, m_R)

## 公钥加密的 CPA$ 安全性 (定义 15.2):

L^\Sigma_{pk-cpa$-real}
(pk, sk) <- Sigma.KeyGen
GETPK():
return pk
CHALLENGE(m \in Sigma.M):
return Sigma.Enc(pk, m)

L^\Sigma_{pk-cpa$-rand}
(pk, sk) <- Sigma.KeyGen
GETPK():
return pk
CHALLENGE(m \in Sigma.M):
c <- Sigma.C
return c

## 公钥加密的一次性保密性 (定义 15.4):

L^\Sigma_{pk-ots-L}
(pk, sk) <- Sigma.KeyGen
count := 0
GETPK():
return pk
CHALLENGE(m_L, m_R \in Sigma.M):
count := count + 1
if count > 1: return null
return Sigma.Enc(pk, m_L)

L^\Sigma_{pk-ots-R}
(pk, sk) <- Sigma.KeyGen
count := 0
GETPK():
return pk
CHALLENGE(m_L, m_R \in Sigma.M):
count := count + 1
if count > 1: return null
return Sigma.Enc(pk, m_R)

