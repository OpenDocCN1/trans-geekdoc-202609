# Table 4

Comparisons of models for predicting ML-based tunneling-induced ground settlement with small datasets.

| Item | MLR | BPNN | PI-BPNN | SVR | DT | RF | GB |
|---|---|---|---|---|---|---|---|
| Approximation | Linear | Nonlinear | Nonlinear | Nonlinear with RBF kernel | Nonlinear | Nonlinear | Nonlinear |
| Learner | Single | Single | Single | Single | Single | Ensemble | Ensemble |
| Effectiveness Applicability Prediction R² accuracy | No Failed | Yes Poor (<60%) | Yes Medium (60%–80%) | Yes Poor (<60%) | Yes Medium (60%–80%) | Yes Good (>80%) | Yes Good (>80%) |
| QE | Failed | Poor (>1) | Poor (>1) | Poor (>1) | Medium (0.5–1) | Good (<0.5) | Good (<0.5) |
| Model stability (learning variance) | Good (≈0) | Poor (5.76) | Poor (3.58) | Good (≈0) | Medium (1.06) | Good (≈0) | Good (≈0) |
| Pros (+) and cons (−) in small dataset application | − Unable to solve complex problems | + Good at processing complex nonlinear problems − Complicated architecture design with many hyperparameters | + Work better than BPNN for small dataset | + Few parameters needed to be determined − Tricky kernel selection | + Good balance between prediction accuracy and calculation speed − Weaker compared with ensemble tree-based learners | + Good prediction accuracy and stability − Relatively low computation speed |

penetrating rate and thrust force. Variables such as tunnel depth and ACM are determined by tunnel design and geological conditions. Thus, the ground settlements can be further controlled by TBM operations. Three TBM operations, i.e., grouting pressure, penetrating rate, and thrust force, should be paid much attention to during the tunnel excavation.

It should be noticed that our conclusions are only suitable and applicable for small dataset cases, such as those tunneling cases listed in Table 1. They are not valid for tunneling cases with big datasets which are out of the scope of this research.

# Declaration of competing interest

The authors declare that they have no known competing financial interests or personal relationships that could have appeared to influence the work reported in this paper.

# Acknowledgments

This research was funded by the University Transportation Center for Underground Transportation Infrastructure (UTC-UTI) at the Colorado School of Mines under Grant No. 69A3551747118 from the US Department of Transportation (DOT). The opinions expressed in this paper are those of the authors and not of the DOT.

# References

Ahangari, K., Moeinossadat, S.R., Behnia, D., 2015. Estimation of tunneling-induced settlement by modern intelligent methods. Soils Found. 55 (4), 737–748.
Altmann, A., Toloşi, L., Sander, O., Lengauer, T., 2010. Permutation importance: a corrected feature importance measure. Bioinformatics 26 (10), 1340–1347.
Ates, U., Bilgin, N., Copur, H., 2014. Estimating torque, thrust and other design parameters of different type TBMs with some criticism to TBMs used in Turkish tunneling projects. Tunn. Undergr. Space Technol. 40, 46–63.
Bouyad, D., Emeriault, F., 2017. Modeling the relationship between ground surface settlements induced by shield tunneling and the operational and geological parameters based on the hybrid PCA/ANFIS method. Tunn. Undergr. Space Technol. 68, 142–152.
Boubou, R., Emeriault, F., Kastner, R., 2010. Artificial neural network application for the prediction of ground surface movements induced by shield tunneling. Can. Geotech. J. 47 (11), 1214–1233.
Breiman, L., 2001. Random forests. Mach. Learn. 45, 5–32.
Bsaibes, A., Courault, D., Baret, F., et al., 2009. Albedo and LAI estimates from FORMOSAT-2 data for crop monitoring. Remote Sens. Environ. 113 (4), 716–729.
Callens, A., Morichon, D., Abadie, S., Delpey, M., Liquet, B., 2020. Using random forest and gradient boosting trees to improve wave forecast at a specific location. Appl. Ocean Res. 104, 102339.
Chao, G.Y., Tsai, T.L., Lu, J., et al., 2011. A new approach to prediction of radiotherapy of bladder cancer cells in small dataset analysis. Expert Syst. Appl. 38 (7), 7963–7969.

Chen, R., Zhang, P., Wu, H., Wang, Z., Zhong, Z., 2019. Prediction of shield tunneling-induced ground settlement using machine learning techniques. Front. Struct. Civ. Eng. 13, 1363–1378.
Clough, G.W., Leca, E., 1993. EPB shield tunneling in mixed face conditions. J. Geotech. Eng. 119 (10), 1640–1656.
Darabi, A., Ahangari, K., Noorzad, A., Arab, A., 2012. Subsidence estimation utilizing various approaches – a case study: tehran No. 3 subway line. Tunn. Undergr. Space Technol. 31, 117–127.
Ding, L., Wang, F., Luo, H., Yu, M., Wu, X., 2013. Feedforward analysis for shield-ground system. J. Comput. Civ. Eng. 27 (3), 231–242.
Elish, M., Helmy, T., Hussain, M., 2013. Empirical study of homogeneous and heterogeneous ensemble models for software development effort estimation. Math. Probl. Eng. 2013, 312067.
Feng, S., Chen, Z., Luo, H., et al., 2021. Tunnel boring machines (TBM) performance prediction: a case study using big data and deep learning. Tunn. Undergr. Space Technol. 110, 103636.
Goh, A.T.C., Hefney, A.M., 2010. Reliability assessment of EPB tunnel-related settlement. Geomech. Eng. 2 (1), 57–69.
Hasanipanah, M., Noorian-Bidgoli, M., Jahed Armaghani, D., Khamesi, H., 2016. Feasibility of PSO-ANN model for predicting surface settlement caused by tunneling. Eng. Comput. 32, 705–715.
Heaton, J., 2015. Artificial Intelligence for Humans. In: Deep Learning and Neural Networks, ume 1. Heaton Research, Inc., St. Louis, MO, USA.
Hegazy, T., Fazio, P., Moselhi, O., 1994. Developing practical neural network applications using back-propagation. Comput. Aided Civ. Infrastruct. Eng. 9 (2), 145–159.
Kim, C.Y., Bae, G.J., Hong, S.W., Park, C.H., Moon, H.K., Shin, H.S., 2001. Neural network based prediction of ground surface settlements due to tunneling. Comput. Geotech. 28 (6–7), 517–547.
Kitchin, R., Lauriault, T.P., 2015. Small data in the era of big data. GeoJournal 80, 463–475.
Kitchin, R., 2013. Big data and human geography: opportunities, challenges and risks. Dialogues Hum. Geogr. 3 (3), 262–267.
Kohestani, V.R., Bazargan-Lari, M.R., Asgari-Marnani, J., 2017. Prediction of maximum surface settlement caused by earth pressure balance shield tunneling using random forest. J. AI Data Min. 5 (1), 127–135.
Lyashevska, O., Harma, C., Minto, C., Clarke, M., Brophy, D., 2020. Long-term trends in herring growth primarily linked to temperature by gradient boosting regression trees. Ecol. Inf. 60, 101154.
Mahmoodzadeh, A., Mohammadi, M., Darai, A., Farid Hama Ali, H., Kameran Al-Salih, N., Mohammed Dier Omer, R., 2020. Forecasting maximum surface settlement caused by urban tunneling. Autom. ConStruct. 120, 103375.
Marto, A., Hajihassani, M., Kalatehjari, R., Namazi, E., Sohaei, H., 2012. Simulation of longitudinal surface settlement due to tunneling using artificial neural network. Int. Rev. Mod. Simul. 5 (2), 1024–1031.
Moghaddasi, M.R., Noorian-Bidgoli, M., 2018. ICA-ANN, ANN and multiple regression models for prediction of surface settlement caused by tunneling. Tunn. Undergr. Space Technol. 79, 197–209.
Mooney, M., Grasmick, J., Kennelly, B., Fang, Y., 2016. The role of slurry TBM parameters on ground deformation: field results and computational modeling. Tunn. Undergr. Space Technol. 57, 257–264.
Mukherjee, I., Routroy, S., 2012. Comparing the performance of neural networks developed by using Levenberg–Marquardt and quasi–Newton with the gradient descent algorithm for modeling a multiple response grinding process. Expert Syst. Appl. 39 (3), 2397–2407.
Mutanga, O., Adam, E., Cho, M.A., 2012. High density biomass estimation for wetland vegetation using WorldView-2 imagery and random forest regression algorithm. Int. J. Appl. Earth Obs. Geoinf. 18, 399–406.