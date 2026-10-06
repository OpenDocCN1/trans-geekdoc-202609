# CellPress

# Neuron

# ### Event times given (known support)

# ### Event times not given (unknown support)

Figure 5 Characterizing the structure of neural activity in unstructured, naturalistic experiments

(A) Structured experiment with known events: doers delivered randomly to a gamma distribution in a task for recording neurons
(B) Raster of post-neuron events. Red dots represent 50 neurons. Black dots indicate spikes.
(C) Schematic of input for DUNL.
(D) Kernel characterization of single neurons. Normalized kernels are shown for four clusters. K-means results with 5 clusters.
(E) Cosine similarity matrix for the kernel clusters
(F) Visualization of the four clusters using principal component analysis (PC1 and PC2). Clustering is based on zero-mean kernels. PC is for visualization only. See supplementary information for details.
(G) Structured experiment with various events: Mouse was exposed to various events and periods during recording. Calcium fluorescence signals recorded across regions (left). Fluorescence in dopamine neurons accumbens shell (right)
(H) Left: 50-slice from 5 regions. Gray: fluorescence and DUNL's rate estimation. Color overlays are on the reconstructed signal. Right: Estimated kernels for each cluster, including full width in mACC olfactory nucleus; INAcSh, lateral accumbens shell; dorsostriatum; dorsolateral stri; TS, tail of the cortex; lateral control path neuron for reporting activity.

![](bbox=[0.108, 0.115, 0.305, 0.203])

![](bbox=[0.332, 0.115, 0.628, 0.203])

![](bbox=[0.108, 0.213, 0.305, 0.303])

![](bbox=[0.332, 0.213, 0.628, 0.303])

![](bbox=[0.108, 0.313, 0.305, 0.403])

![](bbox=[0.332, 0.313, 0.628, 0.403])

![](bbox=[0.108, 0.413, 0.305, 0.503])

![](bbox=[0.332, 0.413, 0.628, 0.503])

![](bbox=[0.108, 0.513, 0.305, 0.603])

![](bbox=[0.332, 0.513, 0.628, 0.603])

![](bbox=[0.108, 0.613, 0.305, 0.703])

![](bbox=[0.332, 0.613, 0.628, 0.703])

seventy-78 DUNL is stable and able to find all patterns Figures S7 and S9, exploring different kernel functions for decomposition. In datasets with alignments and no clear structure across trials, global-dimensional methods like LFDS^38 TCA^36 and SCF^33 fail to detect latent factors Figures J7 and 7k. Additionally, path-finding algorithms differ between event types in this experiment. For more details and the unrolling of iterations, DUNL's performance varies, see supplementary materials and Figures S5–S7.

Comparison with other decomposition methods

DUNL is a versatile decomposition method that extracts interpretable representations from time series data. Its strength is learning multiple scales within single tracks (locality), effectiveness in limited datasets, and scalability. To address gaps in functionality left by other methods, we evaluate DUNL's performance against them, with each comparison focusing on a specific aspect.

DUNL's ability to learn local features was demonstrated using a synthetic dataset. While LFDS performs population-level analysis of recorded neurons, DUNL decomposes asynchronously, local activity within strings of individual neurons. To illustrate this, we conducted a simulation with experiment-trained trials, clustering containing two non-overlapping pairs to recover local activity. We used DUNL to decompose neural activity into two tracks corresponding to an event type. Trials were generated for both training and test data (Figure 8).

Both DUNL and LFDS successfully estimated the similarity of rates (Figures 8A–8B), DUNL also recovered the hidden kernels (Figure 8). However, LFDS identifies factors spanning the trial duration, lacking DUNL's locality (2) and fails to deconvolve neural activities from different event types (Figure 8E). Unlike

1160 Neuron 173, 1151–1168, April 16, 2023