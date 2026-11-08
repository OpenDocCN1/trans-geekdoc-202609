
Running a Gibbs sampler for a Boltzmann machine often requires many iterations, and a technique called “contrastive divergence” is a popular alternative that initializes the sampler to the observed data instead of randomly and performs a limited number of Gibbs updates. In an `RBM` a sample ${\\overset{\\hat{}}{\\mathbf{h}}}^{(0)}$![Equation](images/F000248si103.png) can be generated from the distribution $p(\\mathbf{h}|{\\overset{\\hat{}}{\\mathbf{v}}}^{(0)} = \\widetilde{\\mathbf{v}})$![Equation](images/F000248si104.png) followed by a sample for ${\\overset{\\hat{}}{\\mathbf{v}}}^{(1)}$![Equation](images/F000248si105.png) from $p(\\mathbf{v}|{\\overset{\\hat{}}{\\mathbf{h}}}^{(1)})$![Equation](images/F000248si106.png). This single step often works well in practice, although the process of alternating the sampling of hidden and visible units can be continued for multiple steps.

### Categorical and Continuous Variables

The `RBM`s discussed so far have been composed of binary variables. However, they can be extended to categorical or continuous attributes by encoding `r` = 1![Equation](images/F000248si107.png), …, `R` visible categorical variables using one-hot vectors `v[(r)]`![Equation](images/F000248si108.png) and defining hidden binary variables `h` with the following energy function
$E\\left( {\\mathbf{v},\\mathbf{h};\\theta} \\right) = - \\sum\\limits\_{r = 1}^{R}\\left\\lbrack {\\mathbf{v}\_{(r)}^{T}\\mathbf{W}\_{(r)}\\mathbf{h} + \\mathbf{a}\_{(r)}^{T}\\mathbf{v}\_{(r)}} \\right\\rbrack - \\mathbf{b}^{T}\\mathbf{h}.$
![Equation](images/F000248si109.png)
The joint distribution defined by this model is complex but as for binary `RBM`s the conditional distributions under the model for one layer given the other have simple forms:
