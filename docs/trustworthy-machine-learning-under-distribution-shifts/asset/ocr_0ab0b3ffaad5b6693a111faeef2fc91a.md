# 2 UNDERSTANDING AND HARNESSING OOD DATA

we have $P(C, S) = P(C)P(S)$. Moreover, we can also know that $Y$ is not conditioned on $S$, and $D$ is not conditioned on $C$. Hence, we can further derive $P(Y, D \mid C, S) = P(Y \mid C)D \mid S).

However, the aforementioned spurious correlation frequently appears when facing OOD examples [69]. As a consequence, when variational inference is based on the factorization in Equation (2.1), the approximated content $\hat{C}$ and style $\hat{S}$ could directly influence $Y$ and $D$, i.e., $Y \leftarrow \hat{C} 	o D$ and $Y \leftarrow \hat{S} 	o D$, leading to inaccurate approximations. However, the desired condition is $Y \leftarrow C \leftarrow D$ and $Y \leftarrow S 	o D$. We can see that the unwanted correlations $	ilde{C} 	o D$ and $\hat{S} 	o Y$ in Figure 2.1 (b) is caused by erroneous posteriors $P(D \mid 	ilde{C})$ and $P(Y \mid \hat{S})$ which are correspondingly approximated by $\phi_s$ and $\phi_c$ which can be used as denominators to $q_{\phi_c}(Y \mid C)$ and $q_{\phi_s}(D \mid S)$, respectively. In this way, we can successfully disentangle content $C$ and style $S$ and ensure the decoding process of $Y$ and $D$ would not be influenced by spurious features from $S$ and $C$, respectively. To this end, our factorization in Equation (2.1) can be approximated as:

```
$$\hat{P}(X, Y, D, C, S) := \frac{P(C)P(S)P(Y \mid C)P(D \mid S)P(X \mid C, S)}{q_{\phi_o}(D \mid C)q_{\phi_s}(Y \mid S)} \quad (2.2)$
```

Then, we maximize the log-likelihood of the distribution $p(x, y, d)$ of each data point $(\mathbf{x}, y, d)$:

```
$log p(\mathbf{x}, y, d) := \log \int \int \hat{p}(\mathbf{x}, y, d, c, s) dcds \quad (2.3)$
```

in which we use lower to denote the values of corresponding variables. Due to the integration of latents $C$ and $S$ is intractable, we follow variational inference [63] to obtain an