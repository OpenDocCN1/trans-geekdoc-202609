
Point Selection Method, accounting for 67% of the total. Two were statistically significant improvements, and none exhibited significant deterioration. When using MDD as the filtering criterion, 19 performance indicators outperformed the Best Point Selection Method, constituting 42% of the total. Two showed statistically significant improvements, while one exhibited significant deterioration. With MAR as the filtering criterion, 38 performance indicators outperformed the Best Point Selection Method, representing 84% of the total. Among these, eight exhibited statistically significant improvements, and none showed significant deterioration. Furthermore, in the comparison of in-sample and out-of-sample performance for the Island Area Selection Method, 10 WFE outperformed the Best Point Selection Method when using net profit as the filtering criterion, accounting for 67% of the total. When using MDD as the filtering criterion, 12 WFE outperformed the Best Point Selection Method, constituting 80% of the total. Lastly, when using MAR as the filtering criterion, 10 WFE outperformed the Best Point Selection Method, representing 67% of the total.

### 4.4. Island Volume Parameter Selection Method

The out-of-sample performance for the Island Volume Selection Method with net profit as the filtering criterion showed that 32 performance indicators outperformed the Best Point Selection Method, accounting for 71% of the total. Among them, four were statistically significant improvements, and one exhibited significant deterioration. When using MDD as the filtering criterion, 24 performance indicators outperformed the Best Point Selection Method, constituting 53% of the total. One showed statistically significant improvements, and none exhibited significant deterioration. With MAR as the filtering criterion, 30 performance indicators outperformed the Best Point Selection Method, representing 67% of the total. Nine exhibited statistically significant improvements, and one showed significant deterioration.

When comparing in-sample and out-of-sample performance for the Island Volume Selection Method, 11 WFE outperformed the Best Point Selection Method, accounting for 73% of the total when using net profit as the filtering criterion. When using MDD as the filtering criterion, six WFE outperformed the Best Point Selection Method, constituting 40% of the total. Lastly, when using MAR as the filtering criterion, 10 WFE outperformed the Best Point Selection Method, representing 67% of the total.

## 5. Conclusions

We proposed using the Point Selection Method, Standard Deviation Selection Method, Island Area Selection Method, and Island Volume Selection Method in the Walk-Forward system backtesting approach. These methods identified appropriate parameter combinations within the in-sample data. These combinations were validated for the out-of-sample data using a trading strategy constructed based on the moving average indicator and applied to Taiwan Stock Index Futures from 1 January 2000 to 31 December 2022. The performance of the proposed parameter selection methods was compared with that of the traditional single-point selection method. Furthermore, the relationship between various parameters within each selection method (window ratio, extension cycles, or benchmark PR) and the MAR performance indicator was analyzed.

The performance indicators of the proposed four parameter selection methods exceeded those of the traditional single-point selection method by more than 50%. Therefore, compared to the traditional single-point selection method, the parameter selection methods proposed are effective in selecting robust out-of-sample strategy parameter combinations. Based on the relationship between the various parameters (window ratio, extension cycles, or benchmark PR) of each selection method and the MAR performance indicator, it was observed that superior performance tended to cluster around specific windows or extension cycles when combined with specific parameter selection methods. This phenomenon suggests that users can consider appropriately expanding the parameters (window ratio, extension cycles, or benchmark PR) of the selection methods in future research.

**Author Contributions:** Conceptualization, C.-Y.C. and H.-Y.L.; methodology, C.-Y.C. and H.-Y.L.; software, H.-W.T.; validation, C.-Y.C., H.-Y.L. and H.-W.T.; resources, C.-Y.C. All authors have read and agreed to the published version of the manuscript.

**Funding:** This research received no external funding.

**Data Availability Statement:** Data are contained within the article.

**Conflicts of Interest:** The authors declare no conflict of interest.

## References

- 1. Yan, M.-C. Modeling and Design and Implementation of Profitability Evaluation of Automated Trading Strategies Using Data Mining. Master's Thesis, National Central University, Taoyuan, Taiwan, 2017.
- 2. Cheng, H. Design and Verification of an Automated Platform for Analyzing the Optimal Suitability of Multi-Commodity Primary and Secondary Strategies Using Distributed Computing. Master's Thesis, National Central University, Taoyuan, Taiwan, 2018.
- 3. Lee, H.-Y. Design and Implementation of an Automated Platform for Evaluating and Comparing Risk and Profitability in Multi-Commodity Multi-Strategy Trading. Master's Thesis, National Central University, Taoyuan, Taiwan, 2019.
- 4. Lin, H.-Z. Analysis and Comparison of Profit Stability in Multi-Commodity Correlations. Master's Thesis, National Central University, Taoyuan, Taiwan, 2020.
- 5. Tsai, Y.-L. Machine Learning—Overfitting and Underfitting That Cannot Be Ignored. IT Help. Available online: https://ithelp.ithome.com.tw/articles/10278254 (accessed on 3 September 2023).
- 6. Pardo, R. The Evaluation and Optimization of Trading Strategies, 2nd ed.; John Wiley & Sons Inc.: Hoboken, NJ, USA, 2008.
- 7. Lee, J.-W. Design and Implementation of a Multi-Dimensional Analysis Platform for Trading Program Optimization. Master's Thesis, National Central University, Taoyuan, Taiwan, 2015.
- 8. Ruggiero, R. Can Your System Do the Walk? Futuresmag, 2010. Available online: http://www.futuresmag.com/2010/03/31/can-your-system-do-walk (accessed on 10 September 2023).
- 9. Fernando, J. Moving Average (MA): Purpose, Uses, Formula, and Examples. Investopedia. Available online: https://www.investopedia.com/terms/m/movingaverage.asp (accessed on 23 September 2023).

**Disclaimer/Publisher's Note:** The statements, opinions and data contained in all publications are solely those of the individual author(s) and contributor(s) and not of MDPI and/or the editor(s). MDPI and/or the editor(s) disclaim responsibility for any injury to people or property resulting from any ideas, methods, instructions or products referred to in the content.

Proceeding Paper

## Online and Offline Hybrid Teaching System Based on Virtual Reality †

Hou Yu 1,*, Nurul Nadwa Zulkifli 1,* and Nozieana Khairuddin 2

1 Department of Science and Technology, Faculty of Humanities, Management and Science, Universiti Putra Malaysia Bintulu Sarawak Campus, Bintulu 97008, Malaysia
2 Institut Ekosains Borneo, Universiti Putra Malaysia Bintulu Sarawak Campus, Bintulu 97008, Malaysia; nozieana@upm.edu.my
* Correspondence: houyu0123@126.com (H.Y.); nurulnadwa@upm.edu.my (N.N.Z.)
† Presented at the 2024 IEEE 4th International Conference on Electronic Communications, Internet of Things and Big Data, Taipei, Taiwan, 19–21 April 2024.

**Abstract:** We describe in this article the current development status of virtual reality (VR) technology and its application prospects in education, and we describe the design and implementation process for a hybrid online and offline teaching system. This system utilizes VR devices and software to bring students into a virtual learning environment, to interact with virtual objects, and to perform practical operations. At the same time, the system provides online courses, learning resources, and social platforms to promote cooperation and communication among students. Compared with traditional teaching, this online and offline hybrid teaching system significantly improves students’ learning interest and induces active participation. Students have positive experiences of using VR technology for learning and believe that the system provides rich and practical learning resources.

**Keywords:** online; offline; hybrid teaching system; virtual reality

### 1. Introduction

The application of virtual reality (VR) technology in teaching has been developing rapidly [1]. In teaching, VR technology has been widely applied in teaching English. By creating a simulated three-dimensional environment, VR technology enables students to gain experience and participate in the learning process [2] as shown in Figure 1. In English learning, VR technology provides an immersive language environment, enabling students to engage in dialogue and communication with virtual characters, thereby enhancing their oral expression and listening comprehension abilities [3,4].

**Citation:** Yu, H.; Zulkifli, N.N.; Khairuddin, N. Online and Offline Hybrid Teaching System Based on Virtual Reality. *Eng. Proc.* 2024, 74, 57. https://doi.org/10.3390/engproc2024074057

Academic Editors: Shu-Han Liao, Teen-Hang Meen and Cheang-Fu Yang

Published: 9 September 2024

Copyright: © 2024 by the authors. Licensee MDPI, Basel, Switzerland. This article is an open access article distributed under the terms and conditions of the Creative Commons Attribution (CC BY) license (https://creativecommons.org/licenses/by/4.0/).

![](img/8c60744401b2d3c0d4f32428cc43626b_453_0.png)

**Figure 1.** Example of a VR classroom.
