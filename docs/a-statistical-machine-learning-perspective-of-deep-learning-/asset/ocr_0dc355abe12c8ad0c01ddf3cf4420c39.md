# GANs vs. Wake-sleep

+   - Wake sleep algorithm
+     Wake : max_θ E_{q_λ(h|x)p_data(x)} [log p_θ(x|h)]
+     Sleep : max_λ E_{p_θ(x|h)p(h)} [log q_λ(h|x)]
+   - Let h be y, and λ be φ
+     ⇒ max_φ E_{p_θ(x|y)p(y)} [log q_φ(y|x)], recovers GAN objective of optimizing φ
+   - GANs extend sleep phase by also learning the generative model (θ)
+     - Directly extending sleep phase: max_φ L_φ = E_{p_θ(x|y)p(y)} [log q_φ(y|x)]
+     - GANs: max_θ L_θ = E_{p_θ(x|y)p(y)} [log q_φ^r(y|x)]
+     - The only difference is replacing q_φ with q_φ^r
+     - This is where adversarial mechanism come about !
+     - GANs stick to minimizing the sleep-phase KLD
+     - Do not involve wake-phase objective