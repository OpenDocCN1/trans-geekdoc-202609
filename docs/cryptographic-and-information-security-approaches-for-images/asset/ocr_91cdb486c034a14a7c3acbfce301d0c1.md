+   - Set $C := \Gamma_3 = g^c$, $m := \text{SE-Enc}(\text{KDF}(Z \| W_e^* \| W_s^*), msg_{\mu}^*)$, for each $i \in W_e^*$, $C_i := (\Gamma_3)^{\dots}$ and $ct^* := [m, C, \{C_i : i \in W_e^*\}]$
+   - Choose a signing attribute set $A_s \subset U_s$ and a threshold $\delta_s \in \mathbb{N}$ such that $W_s^* \subset A_s$ and $|W_s^*| \ge \delta_s$, and generate a signing key $\mathcal{SK}_{A_s,\delta_s} := [\delta_s, \{S_i, i \in A_s\}]$ by running a SignKey query on $[A_s, \delta_s]$.
+   - For each $i \in W_s^*$, set $\sigma_i := S_i \cdot (\Gamma_3)^{\dots}$ where $\theta := (\theta_1,\dots,\theta_t) = H_1(m \| W_e^* \| W_s^* \| \delta_s)$, $\sigma^* := \{\sigma_i : i \in W_s^*\}$
+   - Compute $\beta^* = H_2(ct^* \| \sigma^* \| W_e^* \| W_s^* \| \delta_s)$ and $\gamma^* = -(\beta^* + \tau_3)/\tau_2$, and set $C_c := (\Gamma_3)^{\beta^* + \gamma^* \dots}$

Then $\mathcal{B}$ gives $\mathcal{CT}^* := [W_e^*, ct^*, \sigma^*, C_c, \gamma^*, \delta_s]$ as a challenge ciphertext to $\mathcal{A}$.

It can be seen that if $Z = e(g, g)^{abc}$, then the challenge ciphertext $\mathcal{CT}^*$ is a valid signcryption of the message $msg_{\mu}^*$ under the encryption attribute set $W_e^*$ and signature attribute set $W_s^*$. If $Z$ is a random element in $\mathbb{G}_T$, then $\mathcal{CT}^*$ is independent of $\mu$ in $\mathcal{A}$'s view.

**Query Phase 2.** Again $\mathcal{A}$ issues a second series of queries, and $\mathcal{B}$ responds to these queries as in query phase 1. But, in this phase, $\mathcal{A}$ cannot ask an Unsigncrypt query $[\mathcal{CT}^*, W_s^*, A_d, \delta_d]$ satisfying $|A_d \cap W_e^*| \ge \delta_d$.

**Guess.** $\mathcal{A}$ outputs its guess $\mu' \in \{0,1\}$ for $\mu$.

If $\mu' = \mu$ then $\mathcal{B}$ outputs 1, indicating that $Z = e(g, g)^{abc}$. Otherwise, $\mathcal{B}$ outputs 0, indicating that $Z$ is a random element of $\mathbb{G}_T$. The calculation of $\mathcal{B}$'s advantage in breaking the DBDH assumption follows from arguments analogous to those of the proof of Theorem 2 in [9]. Hence, $\mathcal{B}$ can break the DBDH assumption with advantage $\epsilon(c/2)(1 - (q/\rho))$.

# **Theorem 9.2.** Assume $H_1$ and $H_2$ are collision-resistant hash functions. Suppose the one-time symmetric-key encryption scheme $\Pi_{SE}$ is semantically secure and the key derivation function KDF is secure. If a PPT adversary is able to break EUF-sSA-CMA security of our tABSC scheme with advantage $\epsilon$ in standard model, then there is a PPT algorithm $\mathcal{B}$ that can break the CDH assumption with advantage $\epsilon / (8(\ell + 1)q)$, where $q$ is the number of signcryption queries requested by the adversary in the game $\text{Game}_{tABSC}^{EUF-sSA-CMA}$ and $\ell$ is the size of the output of the hash function $H_1$.

We can prove Theorem 9.1 stated above following the same line of proving Theorem 3.31 in [16] and the ideas in proof of Theorem 9.2, and so we omit the details.