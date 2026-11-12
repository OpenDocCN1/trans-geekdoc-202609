![](bbox=[0.13, 0.08, 0.83, 0.28])

Fig. 3. Comparison of noise model variants across GNN architectures. A cluster is for an architecture, and coloured bars show the accuracy of the corresponding noise type.

![](bbox=[0.13, 0.36, 0.83, 0.55])

Fig. 4. Comparison of noise model variants across graph label noise-robust algorithms. A cluster is for an algorithm, and coloured bars show the accuracy of a noise type.

Q3. How does the Existing Label Noise Robust Algorithm Perform in the Presence of EDN? Next, we evaluate noise-robust algorithms DGNN [6], PIGNN [7], RNCGLN [8], NRGNN [9], RTGNN [10], CRGNN [11], CGNN [5], and DeGLIF [14] under different noise variants of EDN, as well as SLN and CCN. Graphical representation of the result for the Citeseer dataset with 40% noise is in Fig. 4. For all datasets at 5%, 25%, and 45% noise level, result is presented in Tables 3 and 4. Detailed results for all datasets are in Tables 10,11,12 in the supplementary material. At low noise levels, these algorithms give comparable results across all noise models. At higher noise levels, most algorithms (Fig. 4) show trends similar to GCN. Performance under the majority vote variant is comparable to or better than SLN or CCN. However, under the Veto Power and sequential variants, almost all algorithms struggle to learn as robustly as they do with SLN or CCN.