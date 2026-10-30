![](bbox=[0.3, 0.13, 0.7, 0.42])

Figure 1.3 Two-level MSVD structure.

E = {Φ_L, {Ψ_i^V, Ψ_i^H, Ψ_i^D}_{i=1}^L, {M_i}_{i=1}^L }  (1.10)

Here, ‘L’ denotes the decomposition level.

The MSVD coefficients of an input image with two decomposition levels are shown in Figure 1.3 [27].

# 1.4 PROPOSED METHOD

The suggested fusion-based watermarking method is implemented in three segments: a) Fusion of medical images, b) Transform-based embedding and recovery of fused image, and c) Security of marked image using encryption (see Figure 1.4). Each segment is elaborated in Algorithms 1–3. Table 1.1 describes the notations used in our algorithms.

In the pre-processing segment, the CT scan image ‘in_CT’ and MRI image, ‘in_MRI’ are fused using the NSCT-based fusing method. It uses phase congruity and local Laplacian fusion rules to fuse the high-pass and low-pass NSCT components of the input images, respectively. The detailed process of generating the fused image is provided in Algorithm 1.

For embedding of the fused image, ‘out_Fus’, the sub-component of the cover image with highest entropy value is decomposed using hybrid of NSCT, HD, and MSVD. Further, MSVD is applied on ‘out_Fus’, resulting in the following coefficients: ‘wLL’, ‘wHL’, ‘wLH’, and ‘wHH’. Further, singular matrix of cover image, ‘in_Cov’, is altered using gain factor and ‘wHL’. Finally, inverse MSVD, inverse HD, and inverse NSCT are applied to generate