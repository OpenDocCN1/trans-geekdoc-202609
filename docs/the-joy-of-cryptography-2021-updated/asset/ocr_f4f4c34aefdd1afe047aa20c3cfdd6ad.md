# 9.3 Defining CCA Security

Our goal now is to develop a new security definition — one that considers an adversary that can construct malicious ciphertexts and observe the effects caused by their decryption. We will start with the basic approach of CPA security, with left and right libraries that differ only in which of two plaintexts they encrypt.

In a typical system, an adversary might be able to learn only some specific *partial information* about the Dec process. In the padding oracle attack, the adversary was able to learn only whether the result of decryption had valid padding.

However, we are trying to come up with a security definition that is useful *no matter* how the encryption scheme is deployed. How can we possibly anticipate every kind of partial information that might make its way to the adversary in every possible usage of the encryption scheme? The safest choice is to be as pessimistic as possible, as long as we end up with a security notion that we can actually achieve in the end. So **let’s just allow the adversary to totally decrypt arbitrary ciphertexts of its choice.** In other words, if we can guarantee security when the adversary has *full information* about decrypted ciphertexts, then we certainly have security when the adversary learns only *partial information* about decrypted ciphertexts (as in a typical real-world system).

But this presents a significant problem. An adversary can do \(c^* := \text{EAVESDROP}(m_L, m_R)\) to challenge ciphertext, and then immediately ask for that ciphertext \(c^*\) to be decrypted. This will obviously reveal to the adversary whether it is linked to the left or right library.

So, simply providing unrestricted Dec access to the adversary cannot lead to a reasonable security definition (it is a security definition that can never be satisfied). The simplest way to patch this obvious problem with the definition is to allow the adversary to ask for the decryption of **any ciphertext, except those produced in response to EAVESDROP queries**. In doing so, we arrive at the final security definition: security against chosen-ciphertext attacks, or CCA-security:

# Definition 9.1 (CCA security) Let \(\Sigma\) be an encryption scheme. We say that \(\Sigma\) has **security against chosen-ciphertext attacks (CCA security)** if \(\mathcal{L}^{\Sigma}_{\text{cca-L}} \approx \mathcal{L}^{\Sigma}_{\text{cca-R}}\), where:

| \(\mathcal{L}^{\Sigma}_{\text{cca-L}}\) |
| :--- |
| \(k \leftarrow \Sigma.\text{KeyGen}\) |
| \(\mathcal{S} := \emptyset\) |
| \(\text{EAVESDROP}(m_L, m_R \in \Sigma.\mathcal{M})\): |
| if \(|m_L| \neq |m_R|\) return err |
| \(c := \Sigma.\text{Enc}(k, m_L)\) |
| \(\mathcal{S} := \mathcal{S} \cup \{c\}\) |
| return \(c\) |
| \(\text{DECRYPT}(c \in \Sigma.\mathcal{C})\): |
| if \(c \in \mathcal{S}\) return err |
| return \(\Sigma.\text{Dec}(k, c)\) |

| \(\mathcal{L}^{\Sigma}_{\text{cca-R}}\) |
| :--- |
| \(k \leftarrow \Sigma.\text{KeyGen}\) |
| \(\mathcal{S} := \emptyset\) |
| \(\text{EAVESDROP}(m_L, m_R \in \Sigma.\mathcal{M})\): |
| if \(|m_L| \neq |m_R|\) return err |
| \(c := \Sigma.\text{Enc}(k, m_R)\) |
| \(\mathcal{S} := \mathcal{S} \cup \{c\}\) |
| return \(c\) |
| \(\text{DECRYPT}(c \in \Sigma.\mathcal{C})\): |
| if \(c \in \mathcal{S}\) return err |
| return \(\Sigma.\text{Dec}(k, c)\) |