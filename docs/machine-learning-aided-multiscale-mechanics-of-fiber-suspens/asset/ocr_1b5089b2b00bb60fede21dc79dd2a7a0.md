for both the fiber and the matrix materials, as suggested by Liu et al. (2019b) and Liu and Wu (2019). To reduce the computational cost of sampling even further for the considered case of fiber suspension, we only generate sample viscosities for the matrix material and consider the suspended fibers to be rigid in all computations. To generate samples for the matrix material, we follow Gajek et al. (2021) and choose the sample viscosity $\mathbb{V}^s$ pertaining to the $s$-th sample to be transversely isotropic, such that

```
$$\mathbb{V}^s = 2\eta_2 \left( \mathbb{P}_2 - g \boldsymbol{A}'(\underline{a}) \otimes \boldsymbol{A}'(\underline{a}) \right) ,$$
```

where the scalar $g \in [0, 1)$ defines the magnitude of the perturbation by the unitary and deviatoric tensor $\boldsymbol{A}'(\underline{a}) \in \text{Sym}_0(3)$, the vector $\underline{a} \in \mathbb{R}^4$ collects four angles, and we consider the scalar viscosities

```
$$\eta_2 = 10^p \text{GPa}, \quad p \in [-3, 3].$$
```

For a fiber reinforced polyamide, Gajek et al. (2021) employed an ansatz of the form (5.54) to sample the material tangents of a J2-elastoplastic matrix material. Similarly, with the objective of applying FDMNs to fiber suspensions with a shear-thinning polyamide matrix as detailed in section 5.4.1, we use equation (5.54) to sample the material tangents of a Cross-type (3.2) matrix material. The tensor function $\boldsymbol{A}'$ is defined by an eigenvalue decomposition (Gajek et al., 2021)

```
$$\boldsymbol{A}' : \mathbb{R}^4 \to \text{Sym}_0(3),$$
```

```
$$(a_1, a_2, a_3, a_4)^\top \mapsto \boldsymbol{Q}(a_2, a_3, a_4) \boldsymbol{A}(a_1) \boldsymbol{Q}(a_2, a_3, a_4)^\top ,$$
```

into the orthogonal tensor $\boldsymbol{Q}(a_2, a_3, a_4)$ and a diagonal tensor $\boldsymbol{A}(a_1)$ in terms of the vector $\underline{a} = (a_1, a_2, a_3, a_4)^\top$. The tensor $\boldsymbol{A}(a_1)$ is constructed