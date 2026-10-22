Qobs & Qsim, α measures the variability in the data α = σ_Qsim / σ_Qobs, and β = mean(Qsim) / mean(Qobs).

# 4.4. Results and Discussion

The conceptual representation of the catchment responses in the HBV model does not allow for simultaneous optimal representation of various behaviors of the catchment response. Therefore, the committee model approach is used to capture simultaneously different aspects of the catchment behavior

For the lake subcatchment, two specialized models have been built and used for the whole study without change, while for the Jiboa subcatchment, different spatial discretization (lumped and distributed) were modeled using four different cell resolutions (4 km, 2 km, 1 km, and 500 m)(see Fig. 4.7 and section 4.3.4 Model Setup).

For the lumped representation of the Jiboa subcatchment, two specialized models have been built for each subcatchment (two models for lake subcatchment and two models for Jiboa subcatchment). The Table 4.2 shows a summary of the performance of a different combination of committee models.

The values of both gamma and delta in Table 4.1 are further visualized in Figure 4.8 to analyze the interaction between the weighting scheme, the membership function, and the power value N. Gamma and delta are values of discharge threshold that determine how much both specialized models are working together. Figure 4.8 shows that MF-A makes specialized models work together more as it goes from WS-I to WS-IV (the length of the lines increase from WS-I to WS-IV). On the other side, MF-B and N = 2 for both WS-I and II specialized models are almost working individually (models works together only in the range of Q/Qmax between γ of 0.24 to δ of 0.27), while MF-B with WS-I, WS-II (N = 3), WS-III and IV make models work together most of the time (in the range of Q/Qmax between γ = 0.06 to δ = 0.88).

More comprehensive studying on the relation between membership function, weighting scheme, and power value (N) shows that MF-B tends to make specialized models either to work together all the time or to work almost individually, as shown in Figure 4.8, which gives higher values of errors as shown in Figure 4.9 (points with bigger size). MF-A makes specialized models work individually and together almost equal times (the difference between delta and gamma around 0.5), which gives better results for committee model performance.