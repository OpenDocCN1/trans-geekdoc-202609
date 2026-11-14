![](bbox=[0.12, 0.09, 0.88, 0.29])

Figure 21.16: VQ-VAE architecture. From Figure 1 of [OVK17]. Used with kind permission of Aäron van den Oord.

When reconstructing the input we replace each discrete code index by the corresponding real-valued codebook vector:

\((z_q)_{ij} = e_k \text{ where } z_{ij} = k\) (21.77)

These values are then passed to the decoder, \(p(\boldsymbol{x}|\boldsymbol{z}_q)\), as usual. See Figure 21.16 for an illustration of the overall architecture. Note that although \(\boldsymbol{z}_q\) is generated from a discrete combination of codebook vectors, the use of a distributed code makes the model very expressive. For example, if we use a grid of \(32 \times 32\), with \(K = 512\), then we can make \(512^{32 \times 32} = 2^{9216}\) distinct images, which is astronomically large.

To fit this model, we can minimize the negative log likelihood (reconstruction error) using the straight-through estimator, as before. This amounts to passing the gradients from the decoder input \(\boldsymbol{z}_q(\boldsymbol{x})\) to the encoder output \(\boldsymbol{z}_e(\boldsymbol{x})\), bypassing Equation (21.76), as shown by the red arrow in Figure 21.16. Unfortunately this means that the codebook entries will not get any learning signal. To solve this, the authors proposed to add an extra term to the loss, known as the **codebook loss**, that encourages the codebook entries \(\boldsymbol{e}\) to match the output of the encoder. We treat the encoder \(\boldsymbol{z}_e(\boldsymbol{x})\) as a fixed target, by adding a **stop gradient** operator to it; this ensures \(\boldsymbol{z}_e\) is treated normally in the forwards pass, but has zero gradient in the backwards pass. The modified loss (dropping the spatial indices \(i, j\)) becomes

\(\mathcal{L} = -\log p(\boldsymbol{x}|\boldsymbol{z}_q(\boldsymbol{x})) + ||\text{sg}(\boldsymbol{z}_e(\boldsymbol{x})) - \boldsymbol{e}||_2^2\) (21.78)

where \(\boldsymbol{e}\) refers to the codebook vector assigned to \(\boldsymbol{z}_e(\boldsymbol{x})\), and sg is the stop gradient operator.

An alternative way to update the codebook vectors is to use moving averages. To see how this works, first consider the batch setting. Let \(\{\boldsymbol{z}_{i,1}, \dots, \boldsymbol{z}_{i,n_i}\}\) be the set of \(n_i\) outputs from the encoder that are closest to the dictionary item \(\boldsymbol{e}_i\). We can update \(\boldsymbol{e}_i\) to minimize the MSE

\(\sum_{j=1}^{n_i} ||\boldsymbol{z}_{i,j} - \boldsymbol{e}_i||_2^2\) (21.79)