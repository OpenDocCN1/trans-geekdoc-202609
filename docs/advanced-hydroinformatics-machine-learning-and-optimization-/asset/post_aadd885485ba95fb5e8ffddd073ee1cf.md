
![](img/dd2f1e467aed0a84f984e6e656b2cc0f_409_0.png)

Figure 14.10 PDFs of storage area damage under certain downstream risk.

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_412_0.png)

Figure 14.12 Test of robust strategies with enlarged hydrographs.

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_414_0.png)

Figure 14.14 Comparison of Pareto fronts of tested and similar hydrographs.

to identify the same hydrograph as the most similar one in different cases. The definition of NSE includes sensitivity to large values of discharge, and wRMSE also gives high weight to large discharges, which leads to the fact that these two criteria give similar and quite reasonable results in terms of similarity of hydrographs. Lastly, the criterion of peak and duration results in selection of a more severe similar hydrograph. The reason for this is that the sampled hydrographs with same peak and duration have larger flood volume on the upper part of the hydrographs because of their round peak shape (largely affecting the usage of storage areas and downstream risk level), compared with the enlarged hydrographs, which have rather sharp shape (see Fig. 14.13). In conclusion, the NSE and wRMSE are more recommended criteria in the aspect of accuracy. Meanwhile, for the sake of safety, the peak and duration method can also be considered for usage.

From the Pareto fronts of the identified similar hydrographs, one point was selected by fixing the downstream risk at value of 11. Similarly, the results of these selected strategies that can be considered for real-time operation are depicted in Figure 14.15.

By observing the testing results (Fig. 14.15) and the Pareto fronts (Fig. 14.14), it can be seen that with a fixed downstream risk level, the strategies leading to small downstream risk (safer for Bengbu City) are selected from the upper cluster of potential strategies (in Fig. 14.14). However, these safe strategies would cause larger storage area damage, obviously. Therefore, in order to ensure Bengbu City not to be flooded, it is better to choose a strategy with larger possibility to flood storage areas. Furthermore, if encountering an extreme condition, such as the year of 1954, another effective way is to fix a smaller downstream risk (e.g., 9 or 10) when making real-time decisions.

Finally, it is worth mentioning again that the proposed real-time operation is all based on the assumption that enough lead time (approximately 20 days) is available before implementation. The possibility of practical use of the proposed methodology still needs to be investigated. Further study is necessary, for example, by either increasing the lead time or making decision with reliable knowledge of a smaller part of the hydrograph top.

## 14.3.4. Comparison of Strategies From ROPAR and From Similarity Selection

The comparison of the two sets of strategies (Fig. 14.16) shows that the strategies from the similarity selection method are more effective to reduce downstream risk in most cases. Especially for HG1954, one of the real-time strategies results in smaller flood risk as well as less storage area damage.

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_416_0.png)

Figure 14.15 Test of real-time strategies with three enlarged hydrographs.

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_417_0.png)

### Test with HG1954
### Test with HG2003
### Test with HG2007

Figure 14.16 Comparison of robust strategies and similarity selection method.

However, although the similarity selection performs better, it would still produce larger storage area damage in most cases while the robust strategies can also prevent Bengbu City from flooding (the peak stage is much less than safeguard level) without compromising the land and properties of storage areas. In that sense, the robust strategies are good enough in most flooding situations; when the inflow is highly likely to cause flooding in Bengbu City (such as some extreme inflow), similarity selection is better to use. It should be again noted that neither the robust nor the similarity selection method is able to protect Bengbu City in case of HG1954. This means that under extreme conditions, these two methods are unsuitable for use. One reason for this is that the sampled hydrographs are less diverse because the parameters setting for Gamma-like function limits the possibility to produce extreme flood events like HG1954. Therefore, further study may enlarge the spectrum of sampled hydrographs, for example, by modifying the parameters of synthetic hydrographs, or by choosing another method that does not need to take the restriction that the sampled hydrographs have same flood volume. However, in any case, extreme conditions may still lead to flooding because of limits of the existing infrastructure, no matter what optimal strategies would be identified.

## 14.4. Conclusions

A conflicting problem exists in the middle of the Huai River between protecting Bengbu City from flooding and reducing loss in flood protection storage areas. Previous studies developed a simulation-optimization method for developing strategies of operating storage area gates but without considering uncertainty. Based on the model of previous studies, this study analyzed the uncertainty of inflow hydrographs and proposed robust optimal strategies and a similarity-based selection method for potential real-time operation. For robust optimization, the newly developed ROPAR method was used. The method for consideration in real-time operation is to choose similar inflow conditions from the database of possible hydrographs as well as their optimal strategies. The conclusions are as follows:

- 1. The distribution of optimal strategies results when considering the uncertainty of inflow shows that when a smaller downstream risk is expected, the possibility of large storage area damage would be higher even with optimal strategies. The robust strategies developed by ROPAR perform differently under three enlarged hydrographs of different return periods. Strategy S40 is good to minimize storage area damage in most cases but for safety of Bengbu City, S93 is recommended to be used.

- 2. The criteria NSE and wRMSE can estimate similarity between hydrographs most accurately, so they are recommended to be used when making real-time decision. From another aspect, the peak and duration criteria can also be used, as they often provides safer strategies for downstream, even though they may cause larger storage area damage in some cases. After determining similar hydrographs, a strategy with larger storage area damage can be chosen for implementation, given that it is more efficient to reduce downstream risk.

- 3. With the same upstream inflow hydrograph, the strategies from similarity selection often lead to less downstream flood risk, but larger storage area damage compared with robust strategies, which are better for the safety of Bengbu especially when encountering extreme floods. However, in most cases, the robust strategies are also effective to protect Bengbu City.

In this study, the uncertainty analysis is somewhat restricted as the flood volume of sampled hydrographs is kept almost the same. However, different severities can still be identified among them, in which case the strategies developed using either robust strategies or similarity selection strategies are effective to protect Bengbu City in most cases, except under extreme conditions (e.g., the return period of 60 yr). In order to improve the analysis and development of optimal strategies, further studies can experiment with more diverse sampled hydrographs by setting different parameter values or without restriction to flood volume variations. In any case, the shape of the sampled hydrographs should be realistic. Another issue that should be noted is that the proposed real-time operation is based on the assumption that sufficient lead time is available before implementation. One of the recommendations here is to integrate the current hydraulic model with a hydrological forecasting scheme in upstream Huai River, which is under development by Cheng (2019), so that the lead time can be largely prolonged. A second suggestion is that a data-driven model may be built in the future, which can produce downstream flood risk and storage area damage quickly, given input of strategies and parameters of the inflow hydrograph. This model development is attainable, given the huge amount of data that is already generated in the process of robust strategies development. With a data-driven model, the elapsed time of optimization can be largely shortened (the hydrodynamic model will not be necessary any more), in which case the optimal strategies could be identified in real-time.
