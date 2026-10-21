![](bbox=[0.06, 0.13, 0.93, 0.27])

Figure 7: Flexibility prediction results for NYSERDA S44 dataset using indoor temperature threshold of 0.5°C (left) compared with adjustment strategy RMSE/2 (center) and increased temperature threshold of 1.0°C (right)

# Table 3: Total flexible energy (kWh) and EPFR percentage of best performing models

|  | NIST |  | NYSERDA S40 |  | NYSERDA S44 |  |
|---|---|---|---|---|---|---|
|  | mode = Off | mode = ForcedOn | mode = Off | mode = ForcedOn | mode = Off | mode = ForcedOn |
| Flexible Energy ($E_{mode}$) | 1166 kWh | 430 kWh | 1087 kWh | 714 kWh | 1855 kWh | 785 kWh |
| EPFR | 98.70% | 87.20% | 97.30% | 86.20% | 87.40% | 95.40% |

be used in cases where previous adjustment for error strategies do not yield satisfactory results. Widening the comfort bounds has a two-fold effect: it potentially reduces the flexibility prediction error and increases the total amount of potential heat pump flexibility. As seen in Figure 7, the widening of the user comfort bounds by 0.5°C decreased MAFE by 85% on average. The widening of bounds also yielded an over 41% increase in potential flexibility for modes Off and ForcedOn.

Evaluation of the amounts of predicted flexible energy. After all experiments were completed, flexibility prediction results were aggregated and the total amount of flexible energy was calculated. To calculate flexible energy for mode ∈ {ForcedOn, Off}, the average power consumptions of the heat pump were calculated in both normal operation P̅_normal and in the given mode P̅_mode and then the absolute difference was multiplied the predicted flexibility amount F̂_mode divided by 4 to normalize to hours (one time step every 15 minutes).

```
E_mode = (P̅_mode - P̅_normal) * F̂_mode / 4  (15)
```

The comfort bound of 0.5°C was used across all datasets for flexibility prediction. As seen in Table 3 all of the heat pump deployments provide over 1.5MWh of combined flexible energy, with the NYSERDA S44 providing 2.64MWh. The results indicate that the majority (over 68%) of total potential flexible energy can be utilized with scenario Off. On average, the flexibility prediction models managed to predict over 90% of available flexibility (EPFR) from all three datasets between both modes. Notably, all of the monitored heat pumps used in this study were not configured to maximize flexible energy and were operating to maintain a set temperature.

# 9 CONCLUSIONS AND FUTURE WORK

This paper proposes HeatFlex, a novel data-driven method for predicting flexibility from smart heat pumps. HeatFlex, utilizing modern machine learning models, LSTM and GRU recurrent neural networks, can accurately predict flexibility from heat pump devices

without requiring knowledge about deployed heat pump parameters, building layout or environment details or manual development of physical models. Furthermore, HeatFlex only uses three, widely available monitored variables, making it applicable in a majority of use cases. The paper also proposes new metrics for heat pump flexibility, enabling quantitative evaluation of flexibility prediction performance. Conducted experiments on 3 open access datasets show that machine learning based indoor temperature forecasting models can be trained in a scalable, data-driven way and be effective at predicting energy flexibility from individual smart heat pump devices. Quantitative and qualitative performance evaluation shows that HeatFlex, utilizing recurrent neural networks, has over 32% lower indoor temperature forecasting error than the model baselines linear regression and SARIMAX, while also having more consistent performance throughout different seasons. Experimental results show that HeatFlex can be effective in different deployments, with different building sizes and heat pump types, predicting over 90% of potential heat pump flexibility.

In future work, we will develop data-driven predictive models that could predict flexibility from other types of devices (e.g. air conditioners, electric vehicle chargers). We will perform experiments using additional data from real smart heat pump deployments as well as simulations to verify HeatFlex robustness in various flexible operation conditions. Additionally, we will explore developing predictive models that optimize directly on flexibility prediction error, thus maximizing utility. Finally, we will develop novel probabilistic models which will enable evaluating potential prediction accuracy during inference.

# ACKNOWLEDGMENTS

This work was supported by the FEVER (Flexible Energy Production, Demand and Storage-based Virtual Power Plants for Electricity Markets and Resilient DSO Operation) project under the Horizon 2020 programme.