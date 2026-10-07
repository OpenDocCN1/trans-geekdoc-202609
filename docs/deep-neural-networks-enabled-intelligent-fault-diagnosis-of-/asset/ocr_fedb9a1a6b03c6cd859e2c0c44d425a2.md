# Neural Architecture Search for Intelligent Fault Diagnosis ■ 149

![](bbox=[0.193, 0.096, 0.781, 0.417])

FIGURE 8.6 The degradation of model performance with the increase of noise.

to enhance the competitiveness of the parametric operators and path-dropout is used to alleviate the co-adaptation problem. In the One-shot method, only path-dropout is used to train the hyper-network. The baseline DARTS takes no strategy in the pre-training phase. These three strategies are respectively used to train the hyper-network for baseline 150 epochs, among which the dropout ratio of both BDAS and One-shot is set to 0.2. Especially, BDAS will warm up the $OP_{3-8}$ separately for 20 epochs, and One-shot and DARTS will train the

![](bbox=[0.135, 0.63, 0.86, 0.848])

FIGURE 8.7 The boxplots of the testing accuracy of the set searched by BDAS. The hollow circles represent the outliers of the boxplots. The red pentacles are the result searched by BDAS. The green squares represent the result of DARTS.