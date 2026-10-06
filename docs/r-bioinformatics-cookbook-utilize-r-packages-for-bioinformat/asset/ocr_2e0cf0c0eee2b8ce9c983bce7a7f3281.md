# 3D structure protein alignment in bio3d

step. You can use the whole sequence as well. The getPredictionProfile() function needs the kernel and model objects to work.

In step 6, we plot () the prediction profile. This profile shows the contribution of each amino acid to the overall decision and adds to the interpretability of the learning results. Here, the fourth residue, D, makes a strong contribution to the decision made for this profile. By examining this across many sequences, the patterns contributing to the decision can be elucidated. It's worth noting that you may get a slightly different picture to that in Figure 8.9 – because of random parts of this recipe and algorithm – so you should build into your analysis: make sure that any differences aren't due to random choices while running the code. The strongest contribution should still come from D in this example:

![](bbox=[0.118, 0.313, 0.828, 0.516])

This prediction profile is a simple but effective display of the most important amino acids.

# 3D structure protein alignment in bio3d

Three-dimensional structural alignments between two molecular models can reveal structural properties that are common or unique to either of the proteins. These can suggest evolutionary or functional commonalities. In this recipe, we'll look at how to get the alignment of two protein sequences in dimensions and view them in 3D.

# Getting ready

For this recipe, we need to install a sequence aligner. We'll take advantage of the fact that the msa package comes with a version of MUSCLE and install that. You can also use conda to install it separately.

We will also need to install a viewer. We will use PyMOL, which can be installed into a conda environment as follows:

```
conda install -c conda-forge -c schrodinger pymol-bundle
```