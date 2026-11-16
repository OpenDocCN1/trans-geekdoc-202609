![](bbox=[0.34, 0.115, 0.69, 0.345])

**Figure 4.10:** Information bottleneck capacity C during training of DAVA for different datasets. Depending on the complexity and structure of the dataset as well as random initialization of the model, a different schedule of C is necessary to achieve best performance. The shaded area denotes one standard deviation across 5 random seeds.

and increase the weight of the adversarial loss to ensure that the model does not learn any new factors of variation while helping it to disentangle the ones it has picked up into individual dimensions. As can be seen in Figure 4.10, this results in dataset-specific schedules of C over the course of the training. Algorithm 2.18 in Appendix B.3.1 describes the training of DAVA in more detail.

# ### 4.5.1 Experiments

To quantify the performance of DAVA, we perform an extensive study including multiple model architectures and datasets. As a baseline, we include the best disentangling models according to [176], namely the \(\beta\)-TCVAE [40] and FactorVAE [143]. We also include AnnealedVAE [31] and ControlVAE [239]. As discussed earlier, the performance of each of these approaches is highly dependent on the regularization strength. For this reason, we perform a grid-search over a range of values curated by roughly following the work of Locatello et al. [176] and adjusting where necessary to ensure best possible performance. The exact hyperparameters considered can be found in