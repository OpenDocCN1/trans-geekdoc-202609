cases \(\bar{D}_{\dot{\gamma}}\), such that

\(\underline{a}^{\text{min}}(\underline{\lambda}) = \underset{\underline{a} \in S_{\text{min}}}{\text{argmin}} \underset{\bar{\mathbf{D}} \in \bar{\mathcal{D}}_{\dot{\gamma}}}{\text{max}} \mathcal{L}(\bar{\mathbf{D}}, \underline{\lambda}, \underline{a}).\) (4.42)

The minimizing parameters \(\underline{a}^{\text{min}}\) are only available on the given discretization points \(\underline{\lambda}\) where homogenization data is available as well. Yet, in accordance with requirement (IV), we are interested in generalizing a given model for fiber orientation states \(\underline{\lambda}\) where no minimizing parameters \(\underline{a}^{\text{min}}\) are available. For this purpose, we follow Köbler et al. (2018) and use a convex linear combination to interpolate stresses as follows. Suppose the nodes \(\underline{\lambda}_1, \underline{\lambda}_2,\) and \(\underline{\lambda}_3\) form a triangle and the minimizing parameters \(\underline{a}^{\text{min}}\) are known in those nodes. Then we compute the effective stresses \(\bar{\tau}^{\text{C}}\) at some point \(\underline{\lambda}\)

\(\bar{\tau}^{\text{C}}(\bar{\mathbf{D}}, \underline{\lambda}) = \sum_{i=1}^{3} s_i \bar{\tau}^{\text{model}}(\bar{\mathbf{D}}, \underline{\lambda}_i, \underline{a}^{\text{min}}(\underline{\lambda}_i)),\) (4.43)

\(\underline{\lambda} = s_1 \underline{\lambda}_1 + s_2 \underline{\lambda}_2 + s_3 \underline{\lambda}_3, \quad s_i \ge 0, i \in 1, 2, 3, \sum_{i=1}^{3} s_i = 1,\) (4.44)

through interpolation of the model stresses \(\bar{\tau}^{\text{model}}\) at the points \(\underline{\lambda}_1, \underline{\lambda}_2,\) and \(\underline{\lambda}_3\). In addition to generalizing the models over the entire fiber orientation triangle \(S_{\text{T}}\), we use equation (4.43) to validate the models against the data obtained with FFT-based computational homogenization. For this purpose, we define the validation error \(e_{\text{V}}\) similarly to the loss \(\mathcal{L}\), i.e., we define

\(e_{\text{V}}(\bar{\mathbf{D}}, \underline{\lambda}) = \frac{\| \bar{\tau}^{\text{FFT}}(\bar{\mathbf{D}}, \underline{\lambda}) - \bar{\tau}^{\text{C}}(\bar{\mathbf{D}}, \underline{\lambda}) \|_2}{\| \bar{\tau}^{\text{FFT}}(\bar{\mathbf{D}}, \underline{\lambda}) \|_2},\) (4.45)

for each considered model. Of the 109 triangulation points \(\underline{\lambda}\) contained in the set \(S_{\text{T}}^{109}\) we designate 45 points as the set \(S_{\text{T}}^{\text{F}} \subset S_{\text{T}}^{109}\) of fitting points \(\underline{\lambda}^{\text{F}}\), see Figure 4.5. For validation purposes, we designate the