![](bbox=[0.17, 0.1, 0.82, 0.43])

Figure 8.7: Mathematical representation of GAN

Here is a list of symbols used in figure 8.7:

+   - G → Generator
+   - D → Discriminator
+   - D(x) → Discriminator’s output for real samples
+   - G(z) → Generator’s output
+   - D(G(x)) → Discriminator’s output for generated samples
+   - θ₁ → Parameters of Generator (weights and bias, and so on)
+   - θ₂ → Parameters of Discriminator (weights and bias, and so on)
+   - p_data(x) → Distribution of real data
+   - x → Samples from p_data(x) distribution p_z(z) distribution of input to the generator
+   - z → Sample from P_z(z) that is, latent space
+   - p_g(x) → Generated sample’s distribution

The training process of the GAN begins with an input (z) (random noise vector), a sample taken from a latent space having a normal probability distribution p_z(z)