
# Uniqueness in resolving multivariate chemical data 155

reach a better understanding of duality and its application in SMCR, mathematical formulae and geometrical visualization based on PCA are implemented.

A bilinear data can be decomposed by singular value decomposition (SVD) to the left eigenvectors (U), right eigenvectors (V), and a diagonal matrix of singular values (S). Therefore, if U and orthonormal V matrices define the basis of the column and row spaces, respectively, according to duality, for any point in the considered space (e.g., V-space), there is a corresponding hyperplane in the dual space (U-space). Consequently, if the information is available to define a specific hyperplane, determination of the dual point is possible. Because of that, the conditions for achieving the unique solution can be studied simply based on this general principle.

Undoubtedly, the necessary condition to get the unique solution is the definition of the directed hyperplane in the dual space. Herein, based on the duality concept, we explore specifically how information the presence of components can lead to a unique concentration or profile for systems of any number. For obtaining the concentration profile of the analyte uniquely, the spectral subspace of the other components should be defined. This subspace dual to the point in U-space, which results in the concentration profile of the analyte. An example is when there is a sub-matrix of M whose rows have information of all interfering compounds (the related presence window of all interfering compounds will not contain the analyte). By performing SVD, estimated loading vectors of M' case, as as is depicted in Fig. 7.7, when the concentration feasible solutions of the green (gray in the printed version) and blue (light gray in the printed version) components are restricted to a plane, the red (dark gray in the printed version) one hyperplane in V-space is uniquely resolvable. However, the reader should note that the zero concentration windows of the components should be known here. Moreover, it is worth to notice that the interfer hyperplane can be achieved when their pure profiles are given as well. Otherwise, one should estimate the zero concentration windows using local-rank information of the data matrix; however, the risk of this progress is discussed in an accompanying paper (Akbari Lakeh et al., 2017).

In the following section, zero-region information is implemented based on duality using a simulated HPLC-DAD data set. It gives an easy way for finding how to use zero concentration region information based on duality in special cases to obtain unique solutions using SMCR methods.

# 156 Machine learning and pattern recognition methods in chemistry

![](img/1aed977a858463e62fc6af1793e4677c_163_0.png)

**Fig. 7.7** Duality relation between the spectra of the red (dark gray) component in V-space (A) the plane of green (gray in the printed version) and blue (light gray in the printed version) components in U-spaces (B).

Fig. 7.7 shows a typical HPLC-DAD data example. For this way, an clarifying the use of partial information in this, the simulations and equations are presented for a three-component system. In this way, an appropriate HPLC-DAD data set is simulated by Gaussian functions. Fig. 7.8A–C displays the concentration profiles, spectral profiles, and the built-up data sets, respectively. The simulated data set is considered to be noise free to avoid complexity.

![](img/1aed977a858463e62fc6af1793e4677c_164_0.png)

Fig. 7.8 Plots of (A) concentration profiles, (B) spectra profiles, (C) simulated data matrix.

# 158 Machine learning and pattern recognition methods in chemistry

# A

![](img/1aed977a858463e62fc6af1793e4677c_165_0.png)

# B

# C

![](img/1aed977a858463e62fc6af1793e4677c_165_1.png)

**Fig. 7.9 (A)** Depiction of concentration window of components. The solid line rectangle shows the concentration window of the blue (light gray in the printed version) component (analyte), and the dashed line rectangle shows its absence. (B) Score plot of data matrix (pink gray in the printed version) and the spectral subspace of the green (gray in the printed version) and red (dark gray in the printed version) components (interferents shown with blue (light gray in the printed version) stars). (C) Calculated concentration profile for the blue (light gray in the printed version) component.

For obtaining the concentration profile of the analyte uniquely, the spectral subspace of the other components should be defined by the duality relation. Here, an example of such conditions is depicted for the simulated three-component system. Fig. 7.9A displays the concentration window of the components by horizontal lines along the time axis, each line has the same color as the corresponding component in Fig. 7.8A. The blue (light gray in the printed version) component is considered as the analyte, and two others are chosen as interferents (green (gray in the printed version) and red (dark gray in the printed version)). The solid line rectangle shows the concentration window of the blue (light gray in the printed version), and the dashed line rectangle shows its absence. So in the simulated example, M' is a sub-matrix of M associated with the dashed rectangle whose rows have information of the green (gray in the printed version) and red (dark gray in the printed version) components. For calculating the requested plane, the loading vectors of M' have to be calculated by performing SVD:

$$M'_{ij} = U'_{i \times 2} S'_{2 \times 2} V'_{2 \times j} \quad (18)$$

where $i$ is the number of elution times of the green (gray in the printed version) and red (dark gray in the printed version) components (excluding the blue (light gray in the printed version) one) and:

$$P_{2 \times 3} = V'_{2 \times j}^T V_{j \times 3} \quad (19)$$

The null space of matrix P is a vector, $n_v$, which will yield the coefficients of the demanded hyperplane:

$$n_{v1} + n_{v2} + n_{v3} = 0 \quad (20)$$

where $z_v$ is general variable which represents the coordinates of an arbitrary point in V-space. Based on Eq. (20), the spectral subspace of the green (gray in the printed version) and red (dark gray in the printed version) components is fixed in V-space (shown with cyan (gray in the printed version) color in Fig. 7.8B and the data points associated with these components lie on it). These points are shown with blue (light gray in the printed version) stars in the score plot of the data. coefficients of the calculated plane correspond to a point in U-space. In fact, this point defines the coordinates related to the concentration profile of the blue (light gray in the printed version) component.

Since the elements of vector $n_v$ are the coefficients of the plane equation, $n_v$ can be transformed to the concentration profile of the blue (light gray in the printed version) component. Note that before transforming the coefficients of the plane, they have to be weighted by the corresponding singular values, i.e., the diagonal elements of the singular matrix of data.

$$n_{w(1 \times 3)} = n_{v(1 \times 3)} S_{(3 \times 3)} \quad (21)$$

$$c_{(blue)(1 \times 3)} = U_{(1 \times 3)} n_{v(3 \times 1)}^T \quad (22)$$

The geometric visualization presented here would help understand how the definition of the subspace related to the interfering compounds leads to the unique concentration profile of the analyte. The correct detection of the subspace (with the described features), which can specify the spectral subspace of the interferents (green (gray in the printed version) and red (dark gray in the printed version)), leads to the unique analyte concentration profile (Fig. 7.9C). Also, the first Manne's theorem suggests these conditions for the unique resolution of the concentration profile. In the described example, these conditions are validated for the blue (light gray in the printed version) component, so it is possible to calculate its concentration profile uniquely. Therefore, it can be said that if the necessary conditions are satisfied, the spectral subspace of the interferents are determined, and by using the duality principle, the concentration profile of the analyte is uniquely resolvable. However, the reader should note again that we have to know the zero concentration of the blue (light gray in the printed version) component, and if it is unknown, estimating the zero concentration window using local-rank information of the data matrix would be risky (Akbari Lakhh et al., 2017).

Now it is clear which conditions using zero concentration information of components lead to the unique solution in concentration and spectral spaces. As mentioned before, applying zero concentration information as selectivity or local-rank constraints can reduce the rotational ambiguity, but they do not necessarily result in the unique solution. For providing a unique solution, the available zero region information has to define a hyperplane of all interfering components in the dual space. In the cases when unique solution is not provided, information is not enough to construct the hyperplane of interfering components.

Agreed, we mention here as well that we have prior information about the green (gray in the printed version) component: in both its concentration windows, only one interferant can be present and the other should be absent. Otherwise, we should estimate these concentration windows using local-rank information of the data matrix; however as mentioned above, the risk of this treatment can be emerged.

# 5. Equality constraint

Equality is one of the most important constraints to restrict the feasible solutions and reach unique solutions in SMCR methods. Imposing equality constraint, in the form of information about a known specific profile, results in a fixed subspace for the complementary components in the dual space. The implementation of the knowledge of a known profile as an equality constraint and its significant effects on the rotational ambiguity has been investigated by considering theoretical and practical aspects of the constraint (Beyramysoltan, Abdollahi, & Rajkó, 2014; Ghaffari & Abdollahi, 2018; Sawall, Fischer, Heller, & Neymeer, 2012). Equality is a powerful
