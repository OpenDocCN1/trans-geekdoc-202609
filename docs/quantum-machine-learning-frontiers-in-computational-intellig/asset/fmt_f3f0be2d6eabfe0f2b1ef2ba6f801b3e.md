
| `#94079` || 0.280010 || 0.048452 || 0.009336 || 0.335100 || 0.052379 || 0.006150 |
| `#97017` || 0.322167 || 0.062244 || 0.008253 || 0.374516 || 0.074216 || 0.012001 |
| `couple` || 0.156938 || 0.056512 || 0.012636 || 0.214296 || 0.069995 || 0.017591 |
| `clown` || 0.259843 || 0.034047 || 0.009269 || 0.276215 || 0.045183 || 0.013615 |

Table 5.4: Mean value of fitness (`ℱ[*μ*]`), Standard deviation of fitness (`ℱ[*σ*]`) and Standard error of fitness (`𝒮[ℰ]`) for `QIBA` and `CBA`.

| Dataset || `QIBA` || `CBA` |
| --- | --- | --- |
|  || `ℱ[*μ*]` || `ℱ[*σ*]` || `𝒮[ℰ]` || `ℱ[*μ*]` || `ℱ[*σ*]` || `𝒮[ℰ]` |
| `#86000` || 0.217982 || 0.022745 || 0.006546 || 0.287976 || 0.027456 || 0.007126 |
| --- | --- | --- | --- | --- | --- | --- |
| `#92059` || 0.221745 || 0.025513 || 0.008571 || 0.293700 || 0.036889 || 0.009193 |
| `#94079` || 0.228774 || 0.045474 || 0.007238 || 0.277012 || 0.064098 || 0.010117 |
| `#97017` || 0.315692 || 0.038725 || 0.007321 || 0.371454 || 0.047451 || 0.009676 |
| `couple` || 0.116231 || 0.043081 || 0.009347 || 0.165203 || 0.048741 || 0.014862 |
| `clown` || 0.199537 || 0.024239 || 0.005364 || 0.214552 || 0.025914 || 0.006518 |

Table 5.5: Result of unpaired `t-test` (`𝒫-value`) between `QIGA` and `CGA` and between `QIBA` and `CBA`.

| Dataset || `QIGA` & `CGA` || `QIBA` & `CBA` |
| --- | --- | --- |
|  || `𝒫-value` || Significant Level || `𝒫-value` || Significant Level |
| `#86000` || <0.0001 || 1 || <0.0001 || 1 |
| --- | --- | --- | --- | --- |
| `#92059` || 0.0002 || 2 || 0.0451 || 3 |
| `#94079` || 0.0001 || 2 || 0.0001 || 2 |
| `#97017` || <0.0001 || 1 || <0.0001 || 1 |
| `couple` || 0.0016 || 2 || <0.0001 || 1 |
| `clown` || <0.0001 || 1 || <0.0001 || 1 |
| Level of Significance: 1 – Extremely Significant, 2 – Very Significant, 3 – Significant |

Table 5.6: Result of Friedman test for `QIGA`, `CGA`, `QIBA` and `CBA`. The rank for each procedure is shown within the parenthesis.

| Dataset || `QIGA` || `CGA` || `QIBA` || `CBA` |
| --- | --- | --- | --- | --- |
| `#86000` || 0.24 (3) || 0.31 (4) || 0.20 (1) || 0.23 (2) |
| --- | --- | --- | --- | --- |
| `#92059` || 0.22 (2.5) || 0.29 (4) || 0.19 (1) || 0.22 (2.5) |
| `#94079` || 0.25 (3) || 0.31 (4) || 0.20 (1) || 0.24 (2) |
| `#97017` || 0.30 (1.5) || 0.35 (4) || 0.30 (1.5) || 0.33 (3) |
| `couple` || 0.14 (2.5) || 0.19 (4) || 0.10 (1) || 0.14 (2.5) |
| `clown` || 0.24 (3.5) || 0.24 (3.5) || 0.18 (1) || 0.20 (2) |
| `Average Rank` || 2.66 || 3.91 || 1.08 || 2.33 |

### 5.8.3 Simulation of work

`Python` environment was used to carry out the experimental process. The experiment was done on four Berkeley images, two of dimensions 80 × 120 and other two of dimensions 120 × 80 and two real life images of dimensions 512 × 512. The development environment was consisting of Windows 7 with the configuration facility of DELL Intel(R) Core(TM) i3, 2.00 GHz and 4.00 GB RAM.

The efficiency of the suggested methods over their classical counterparts was proved depending upon computed mean fitness value, standard deviation, standard error and smallest computation time. Moreover, the competence of the quantum inspired algorithms over their classical algorithms was justified by performing the `t-test` (statistical superiority test). The optimal number of cluster (`𝒪_𝒩[𝒞]`) and its associated optimal fitness value (`𝒪_ℱ[𝒯]`) for all the algorithms (`QIGA`, `CGA`, `QIBA` and `CBA`) were reported in [Table 5.1](#bodymatter-005.xhtml#b_9783110670707-005_tab_001). The optimal execution time (`𝒪_𝒯[ℰ]`) in second for all the algorithms (`QIGA`, `CGA`, `QIBA` and `CBA`) were shown in [Table 5.2](#bodymatter-005.xhtml#b_9783110670707-005_tab_002). The mean fitness value (`ℱ[*μ*]`), standard deviation (`ℱ[*σ*]`) and standard error (`𝒮[ℰ]`) of the algorithms `QIGA` and `CGA` and were demonstrated in [Table 5.3](#bodymatter-005.xhtml#b_9783110670707-005_tab_003) and the same things for the algorithms `QIBA` and `CBA` were demonstrated in [Table 5.4](#bodymatter-005.xhtml#b_9783110670707-005_tab_004). Finally, the result of `t-test` [[37](#bodymatter-005.xhtml#b_9783110670707-005_ref_037)] was presented in [Table 5.5](#bodymatter-005.xhtml#b_9783110670707-005_tab_005) which was performed with 95% confidence level. During the test, the `𝒫-value` is checked. If it is less than 0.05 then null hypotheses is considered for rejection against the alternative hypothesis. Finally, Friedman test [[38](#bodymatter-005.xhtml#b_9783110670707-005_ref_038), [39](#bodymatter-005.xhtml#b_9783110670707-005_ref_039)] was performed among the participating procedure and was enlisted in [Table 5.6](#bodymatter-005.xhtml#b_9783110670707-005_tab_006). The obtained rank from the proposed algorithms `QIGA`, `CGA`, `QIBA` and `CBA` are 2.66, 3.91, 1.08 and 2.33 respectively. According to the rank value, `QIBA` can be considered as the superior algorithm as it has the minimum rank value.

### 5.8.4 Dataset used

The following images ([Figure 5.2](#bodymatter-005.xhtml#b_9783110670707-005_fig_002)) were used during the experiment and during the accomplishment of the process the normalized values between (0,1) were considered for the images.

![Figure 5.2: Test Images: (a) #86000 of size 80 × 120, (b) #92059 of size 80 × 120, (c) #94079 of size 120 × 80, (d) #97017 of size 120 × 80, (e) couple of size 512 × 512, (f) clown of size 512 × 512.](graphic/converted/b_9783110670707-005_fig_002.png)

Figure 5.2: Test Images: (a) `#86000` of size 80 × 120, (b) `#92059` of size 80 × 120, (c) `#94079` of size 120 × 80, (d) `#97017` of size 120 × 80, (e) `couple` of size 512 × 512, (f) `clown` of size 512 × 512.

## 5.9 Conclusion

This article is envisaged an automatic clustering technique to recognize the optimal number of cluster points present in an image dataset, which shows a new way to combine the features of quantum computing with two different meta-heuristic algorithms, viz., Genetic algorithm and Bat algorithm. These proposed techniques were found superior over their classical counterparts as they out performed over corresponding classical counterparts for automatically identifying the optimal number of cluster points present in an image dataset within a significantly small time frame. Also the effectiveness of the quantum inspired algorithms were judged and presented depending upon the computed value of optimal fitness, mean fitness value, standard deviation of the fitness, standard error of the fitness and more over the computed `p-value` from the statistical superiority test `t-test`. Finally, Friedman test were performed to identify the superior technique between the quantum inspired versions with their classical version. Moreover, it was seen that the quantum inspired Bat algorithm was the best performing procedure among the others. All the computed results were presented in the previous tables in order to proof the effectiveness of the quantum inspired methods over their classical counterparts as well as prove the superiority of `QIBA`. So far, only gray level images were used for experimental purpose and the proposed techniques were developed to satisfy only one objective at a time.

Currently authors are involved to explore the realm of quantum computing to resolve the concerned multi objective optimization problems effectively and efficiently within a smaller time frame and also trying to take care of the true colour images for this direction of the research.

## References

[1]Jain, A., & Dubes, R. Algorithms for Clustering Data. Prentice Hall, 1988. [→](#bodymatter-005.xhtml#xref_d6256e51083)

[2]Jain, A. K., Murty, M. N., & Flynn, P. J. Data clustering: A review. ACM Computing Surveys. 1999, 31(3),264–323. [→](#bodymatter-005.xhtml#xref_d6256e51086)
