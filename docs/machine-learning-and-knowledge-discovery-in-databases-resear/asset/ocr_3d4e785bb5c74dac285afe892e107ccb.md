learning gets worse results than MIP as it mixes the invariant and variant prompts together for the absence of invariant learning.

# 5.4 Parameter Sensitivity Analysis

**Intervention Rate :** The intervention rate is closely related to the ability to separate the invariant and variant features. We set this parameter from 0.05 to 0.95 with an interval of 0.1, and evaluate our model on both datasets. In Fig. 5, we record the RMSE of the final horizon. The MIP demonstrates insensitivity to varying intervention rates, as evidenced by the small fluctuating RMSE across different levels of intervention. In the spatial-temporal model, the intervened variant prompts will propagate to all the nodes in an urban graph, even a small intervention rate will make all the nodes contain variant patterns before the prediction layer. Thus, the change in intervention rate does not influence the prediction RMSE.

**Number of Nodes in Memory Bank:** We investigate the sensitivity of the number of nodes in the memory bank and show the results in Fig. 6. The MIP performs well on all the datasets with 30 nodes in the memory bank. With a small number of nodes, MIP cannot extract high-quality invariant features due to the limited diversity. On the contrary, with more nodes in the memory bank, diverse invariant features lead to the increasing training difficulty of both the prediction model and the invariant learning backbone model.

**The Weight Coefficients in The Loss Function:** In Eq.(19), the loss function consists of task loss, invariant loss, and auxiliary loss. The composition ratio of the last two losses is controlled by hyperparameters \(\lambda_1\) and \(\lambda_2\), and we implement an experiment to investigate which one works better. Firstly, we

![](bbox=[0.112, 0.586, 0.912, 0.676])

(a) METR-LA dataset. (b) NYC Bike1 dataset(In). (c) NYC Bike1 dataset(Out).

# Fig. 7. RMSE of MIP with different settings of \(\lambda_1\).

![](bbox=[0.112, 0.752, 0.912, 0.842])

(a) METR-LA dataset. (b) NYC Bike1 dataset(In). (c) NYC Bike1 dataset(Out).

# Fig. 8. RMSE of MIP with different settings of \(\lambda_2\).