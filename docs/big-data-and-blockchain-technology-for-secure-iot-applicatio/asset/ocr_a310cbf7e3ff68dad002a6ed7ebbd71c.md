ciphertexts of a fixed size. Introduced a strategy for CP-ABE and KP-ABE that utilizes ciphertexts of constant size. We refer to these as schemes 1 and 2, respectively.

# 5.3.2 Security of BLS and Boneh-Gentry-Lynn-Shacham (BGLS) signature

An aggregate signature system is a cryptographic method that allows for the combination of several signatures on multiple messages from multiple users into a single concise signature.

Regrettably, there are currently no aggregate signature methods that are completely non-interactive, even when relying on the random oracle heuristic. This means that signers are need to exchange messages with each other, either in a sequential or alternative manner, in order to create the signature. Interacting with some intriguing apps might be too expensive.

Aggregate signatures, as defined by S. Ilakiya et al. [17], are a kind of digital signature that allows any party to consolidate many signatures on multiple messages from multiple users into a single concise signature. This basic element is valuable in several scenarios when there is limited storage or bandwidth capacity, and thus, there is a need to minimize the overall cryptographic burden.

Basic BGLS aggregate signature scheme [17]:

|  |  |
|---|---|
| Set up | $G_1 = \langle g_1 \rangle, G_2 = \langle g_2 \rangle, G_T$, prime order $p$  
$\mathbf{H}: \{0,1\}^* \to G_1$, full domain  
$e : G_1 \times G_2 \to G_T$, bilinear |
| KeyGen | $x \leftarrow_s \mathbb{Z}_p$  
$sk = x \in \mathbb{Z}_p$  
$pk = (y_1, y_2) = (g_1^x, g_2^x) \in G_1 \times G_2$ |
| Sign $(sk, m)$ | $\sigma = \mathbf{H}(m)^{sk} \in G_1$ |
| Agg $(\sigma_1, ..., \sigma_k)$ | $\sigma_A = \prod_{i=1}^k \sigma_i \in G_1$ |
| AggVer $(\sigma_A, (pk_1, m_1), ..., (pk_k, m_k))$ | $\prod_{i=1}^k e(\mathbf{H}(m_i), y_{2,i}) = e(\sigma_A, g_2)$ |

# 5.4 ENCRYPTION AND HEALTHCARE

The first factor that guarantees the unity and strength of a healthcare system is the protection of personal health information (PHI). The introduction of digital technology in healthcare allows for convenient access to this data, which facilitates the provision of more efficient and impactful health services and therapy. Presently, healthcare professionals widely use EHR