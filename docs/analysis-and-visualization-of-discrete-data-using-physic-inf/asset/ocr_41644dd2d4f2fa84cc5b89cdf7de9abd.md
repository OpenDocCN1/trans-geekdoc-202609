The method to find a solution to PDE using NN can be classified as a collocation method. Here, in domain $v$, in the NN model, the unknown function $u(t, x, y, z)$ is approximated using the known activation function sequence $\sigma_{i_{j+1}}^{j}(x)$, $j = 0, L$ as follows:

```
$$u(t, x, y, z) = u_{1}^{L+1} = \sigma_{1}^{L}\left(\sum_{i_{L}=1}^{n_{L}} u_{i_{L}, i_{L+1}}^{L}\sigma_{i_{L}}^{L-1}\left(\sum_{i_{L-1}=1}^{n_{L-1}} w_{i_{L-1}, i_{L}}^{L-1}\cdots \times \sigma_{i_{1}}^{0}\left(\sum_{i_{0}=1}^{n_{0}} w_{i_{0}, i}^{0}u_{i_{0}}^{0}\right)\cdots\right)\right)\quad(4.50)$
```

The $n_{0}$ represents the number of explanatory variables, which is $\begin{array}{r} t = u_{0}^{0} \\ x = u_{0}^{0} \\ y = u_{3}^{0} \\ z = u_{4}^{0} \end{array}$.

In order to construct the NN model, the weights $w_{i_{j}, i_{j+1}}^{j}$, $j = 0, L$ are determined so that the residuals become zero in the average sense at points inside the target domain and on the boundary. This function is appropriately named the global collocation method (GCM) because, unlike FEM, it is determined for the whole domain at once.

# ### 4.3.2.1. *Finite element method (FEM)*

The Galerkin method, one of the key techniques of FEM, is the best known of the weighted residuals and was proposed by the Russian engineer Galerkin. In this method, the weight function $w_{i}$ is made the same as the trial function $T_{i}$, that is, $w_{i} = T_{i}$. This method is closely related to the variational direct method and in that sense is important in FEM.

In order to obtain an approximate solution to the PDE, it is important to know how the evaluation of the partial differential term is realized. FDM employs a method of replacing partial derivatives with differences, as already discussed, and basically uses information from adjacent grids to compute the differences. To further improve accuracy, not only information from adjacent grids but also information from beyond adjacent grids is used. In FEM, the degree of the test function is increased in the elements to improve the approximation capability. In the particle method, the radius of influence is increased to improve the approximation capability. These methods are local interpolation. In contrast, GCM is a global approximation.

The sample code to perform the finite element solution method of the steady-state heat transfer equation in Colab is shown in the following: