Tangent Sigmoid = \(\frac{1}{1 + e^{-x}}\) (9.1)

# ## 9.4 Experimental Database Gathering

A comprehensive database is needed to use machine learning models. A database is actually a collection of input and output data in a system. In this research, the design parameters of the masonry shear wall are considered as input. In Table 9.1, the inputs are introduced along with their units. An experimental dataset totaling 255 PG masonry shear walls was compiled from 22 independent studies (Table 9.2) [12]. The collected samples are divided into 5 categories from A to E. This division is given in Table 9.3. The range of parameters used in ANN modeling is given in Table 9.4. All input and output variables in the database are normalized on a -1, 1 scale, following this formula:

\( Norm x_i = \left[ \frac{x_i - min(x)}{max(x) - min(x)} \times 2 \right] - 1 \) (9.2)

where x is the input or output variable to be normalized, \(x_i\) is its corresponding value, and \(Norm x_i\) is the calculated value. The correlation matrix related to the data values is shown in Fig. 9.3.

The frequency distribution of the experimental data to express the parameters of the samples, including \(A_{scaled}\), \(M / VL\), \(A_{net} / A_{gross}\), \(f'_{m,eff,corrected}\), \(\rho_l f_{yv}\), \(\rho_h f_{yh}\), \(\sigma_{gross}\), \(V_{avg}\) is shown in Fig. 9.4. As can be seen, the empirical data collected covers a wide range. Therefore, these parameters can be suitable inputs for model development.

**Table 9.1** Input variables adopted in the study

| Type | Number | Symbol | Unit |
| :--- | :--- | :--- | :--- |
| Wall geometry | 1 | \(A_{scaled}\) | mm\(^2\) |
| | 2 | \(M / VL\) | - |
| Partial grouting | 3 | \(A_{net} / A_{gross}\) | - |
| Masonry materials | 4 | \(f'_{mcor, eff}\) | MPa |
| Vertical reinforcement | 5 | \(\rho_l f_{yv}\) | MPa |
| Horizontal reinforcement | 6 | \(\rho_h f_{yh}\) | MPa |
| Axial stress | 7 | \(\sigma_{gross}\) | MPa |
| Experimental shear capacity | 8 | \(V_{avg}\) | kN |