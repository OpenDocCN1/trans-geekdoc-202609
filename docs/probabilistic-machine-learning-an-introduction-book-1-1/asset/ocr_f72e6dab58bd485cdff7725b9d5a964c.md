Computing the regularization term over all possible nodes pairs is computationally challenging in practice, so the Graph Auto Encoders (GAE) model uses negative sampling to overcome this challenge.

Whereas GAE is a deterministic model, the authors also introduce variational graph auto-encoders (VGAE), which relies on variational auto-encoders (as in Sec. 20.3.5) to encode and decode the graph structure. In VGAE, the embedding Z is modelled as a latent variable with a standard multivariate normal prior p(Z)=N(Z|0,I) and a graph convolution is used as the amortized inference network, q_Φ(Z|W,X). The model is trained by minimizing the corresponding negative evidence lower bound:

NELBO(W,X;Θ)= -E_{q_Φ(Z|W,X)}[log p(W|Z)] + KL(q_Φ(Z|W,X)||p(Z)) (23.32)
= L_{G,RECON}(W,Ŵ;Θ) + KL(q_Φ(Z|W,X)||p(Z)). (23.33)

# 23.5.1.3 Iterative generative modelling of graphs (Graphite)

The graphite model of [GZE19] extends GAE and VGAE by introducing a more complex decoder. This decoder iterates between pairwise decoding functions and graph convolutions, as follows:

Ŵ^{(k)} = Z^{(k)}Z^{(k)⊤} / ||Z^{(k)}||_2^2 + 11^⊤ / N

Z^{(k+1)} = GCN(Ŵ^{(k)}, Z^{(k)})

where Z^{(0)} is initialized using the output of the encoder network. This process allows Graphite to learn more expressive decoders. Finally, similar to GAE, Graphite can be deterministic or variational.

# 23.5.1.4 Methods based on contrastive losses

The deep graph infomax method of [Vel+19] is a GAN-like method for creating graph-level embeddings. Given one or more real (positive) graphs, each with its adjacency matrix W ∈ R^{N×N} and node features X ∈ R^{N×D}, this method creates fake (negative) adjacency matrices W^- ∈ R^{N^-×N^-} and their features X^- ∈ R^{N^-×D}. It trains (i) an encoder that processes both real and fake samples, respectively giving Z = ENC(X,W;Θ^E) ∈ R^{N×L} and Z^- = ENC(X^-,W^-;Θ^E) ∈ R^{N^-×L}, (ii) a (readout) graph pooling function R: R^{N×L} → R^L, and (iii) a descriminator function D: R^L × R^L → [0,1] which is trained to output D(Z_i,R(Z)) ≈ 1 and D(Z_j^-,R(Z^-)) ≈ 0, respectively, for nodes corresponding to given graph i ∈ V and fake graph j ∈ V^-. Specifically, DGI optimizes:

min_Θ - E_{X,W} Σ_{i=1}^N log D(Z_i,R(Z)) - E_{X^-,W^-} Σ_{j=1}^{N^-} log(1 - D(Z_j^-,R(Z^-))), (23.34)

where Θ contains Θ^E and the parameters of R,D. In the first expectation, DGI samples from the real (positive) graphs. If only one graph is given, it could sample some subgraphs from it (e.g. connected components). The second expectation samples fake (negative) graphs. In DGI, fake samples use the real adjacency W^- := W but fake features X^- are a row-wise random permutation of real X. The ENC used in DGI is a graph convolutional network, though any GNN can be used. The