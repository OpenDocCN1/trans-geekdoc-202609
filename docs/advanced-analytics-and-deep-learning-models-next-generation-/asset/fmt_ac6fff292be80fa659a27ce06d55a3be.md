
| 2017\_CCA \[27\] || 0.6618 || 0.6015 || 0.799 || 0.5343 ||   || 2017\_CCA \[27\] || 0.6691 || 0.6042 || 0.6971 || 0.5641 |

| 2017\_CIC \[27\] || 0.6719 || 0.6542 || 0.7743 || 0.5327 ||   || 2017\_CIC \[27\] || 0.7029 || 0.6218 || 0.7064 || 0.5677 |

| Extended\_SAE\_3 || 0.5783 || 0.487 || **0.6501** || 0.7113 ||   || Extended\_SAE\_3 || 0.5906 || 0.4959 || 0.6523 || 0.7973 |

| Extended\_SAE\_5 || **0.564** || **0.4842** || 0.6503 || **0.7939** ||   || Extended\_SAE\_5 || **0.5798** || **0.4834** || **0.6306** || **0.807** |

**Result = TA 5-5**

**Result = YM 5-5**

| **Technique** || **MAE** || **GIMAE** || **GPIMAE** || **F1** ||   || **Technique** || **MAE** || **GIMAE** || **GPIMAE** || **F1** |

| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

| MF \[10\] || 1.2077 || 1.3055 || 0.8079 || 0.4491 ||   || MF \[10\] || 1.2961 || 1.2755 || 0.6204 || 0.4882 |

| 2016\_Hybrid AE \[23\] || 0.6531 || 0.6022 || 0.8406 || 0.6789 ||   || 2016\_Hybrid AE \[23\] || 0.7691 || 0.6314 || 0.8244 || 0.6798 |

| 2011\_Liwei Liu \[13\] || 0.772 || 0.5262 || 0.6282 || 0.6102 ||   || 2011\_Liwei Liu \[13\] || 0.7233 || 0.575 || 0.7232 || 0.6706 |

| 2017\_Learning \[22\] || 0.6204 || 0.5907 || 0.6103 || 0.6907 ||   || 2017\_Learning \[22\] || 0.6514 || 0.5019 || 0.5824 || 0.7107 |

| 2017\_CCC \[27\] || 0.6737 || 0.5878 || 0.5901 || 0.4497 ||   || 2017\_CCC \[27\] || 0.6888 || 0.6242 || 0.7577 || 0.538 |

| 2017\_CCA \[27\] || 0.6914 || 0.6124 || 0.6095 || 0.4826 ||   || 2017\_CCA \[27\] || 0.6891 || 0.5417 || 0.5972 || 0.564 |

| 2017\_CIC \[27\] || 0.7129 || 0.6536 || 0.6814 || 0.4636 ||   || 2017\_CIC \[27\] || 0.7012 || 0.642 || 0.7439 || 0.537 |

| Extended\_SAE\_3 || 0.5674 || 0.521 || **0.5379** || **0.7458** ||   || Extended\_SAE\_3 || 0.608 || 0.4636 || 0.5673 || **0.7109** |

| Extended\_SAE\_5 || **0.5593** || **0.5075** || 0.549 || 0.7384 ||   || Extended\_SAE\_5 || **0.5854** || **0.4633** || **0.5592** || 0.6073 |

#### 3.4.2.2 Training Setting

Here, they trained their stacked autoencoder with the three-hidden layers and five-hidden layers, and also, they applied sigmoid and hyperbolic tangents. In sigmoid transfer function, the data are transformed in between 0 and 1. In hyperbolic tangents, the data are transformed in between −1 and 1. They used mini batch GD Optimizer and Adam Optimizer for regularization. Dropout regularization is added to each hidden layer with probability `p = 0.5`. Research was done for dissimilar parameters. Finest parameter values are shown in the research work. In this proposed approach, 90% of data are utilized for training purposes along with the rest samples for testing purposes \[4\].

#### 3.4.2.3 Result

To compare this approach with single- as well as multi-criteria rating systems, they implemented the approach with some different research result proposed by different researchers. Those are MF, 2016 Hybrid AE \[23\] and multi-criteria recommendation techniques: 2011 Liwei Liu \[13\], 2017 Learning \[22\], three approaches from \[27\] (2017 CCC, 2017 CCA, and 2017 CIC). Certain procedures are used on all the functioning datasets. The results are shown in [Tables 3.1](#c03.xhtml#tab3-1) to [3.3](#c03.xhtml#tab3-3). Conventional matrix factorization got the most ever loss in terms of MAE, GIMAE, and GPIMAE with values 1.2077, 1.3055, and 0.8079, respectively, as shown in [Table 3.1](#c03.xhtml#tab3-1). In terms of mean absolute error and F1, 2017 Pref Learning carry out superior to existing single and multi-criteria rating techniques. However, this method performs well in all the existing methods. It can be seen that MF got the maximum loss and least F1. Their preferred extended stacked autoencoder approach went beyond all the methods sufficiently in various evaluation metrics, as shown in [Table 3.2](#c03.xhtml#tab3-2). Similar trends are also found on the other datasets, YM 10-10 and YM 20-20 in [Tables 3.3](#c03.xhtml#tab3-3) and [3.4](#c03.xhtml#tab3-4), respectively \[4\].

### 3.4.3 Situation-Aware Multi-Criteria Recommender System: Using Criteria Preferences as Contexts by Zheng

Inside this research activity, they tried to implement the new methods which manage criteria likings as contextual situations. To be specific, they trust that one portion of multi-criteria preferences may be observed as contexts and the other part managed in the conventional way in MCRS. They differentiate the suggestion efficiency between three settings. First one is applying every criteria rating in the conventional way. Second setting that they used is managing every criteria preference as contexts and the last one issuing preferred criteria ratings as contexts. Their demonstrations are depending on two practical rating datasets. It reveals that managing criteria priorities as contexts can upgrade the efficiency of module recommendations if those are being selected very carefully. They have used a hybrid model which selects criteria preference as contexts and solve remaining part in traditional way. They have illustrated this proposed model and got very efficient result and the model becomes the winner of their experiment \[19\].

Now, we will see its experimental evaluation and result to ensure its efficiency.

#### 3.4.3.1 Evaluation Setting

They have very limited datasets which have multiple-criteria ratings for experiment. For this research, they use two popular real-world datasets: TripAdvisor dataset and Yahoo! Movies dataset. Successively, they used 80% of rated moves or hotels for training purposes and rest 20% for the testing purpose. They evaluated and compared the algorithms which are declared placed to calculate the prediction of rating. They predicted in general ratings mentioned by users on every item for test set, along with calculate efficiency by the very popular mean absolute error method \[19\].

#### 3.4.3.2 Experimental Result

The outputs are revealed in [Figure 3.4](#c03.xhtml#fig3-4). If we take a sincere look, then we will find that the data tags on above of every bar present the rate of development by HCM in correspondence with other methods. In association with algorithms, biased MF represented the outcomes that are generated by the biased MF algorithm. The present results formed on the aggregation-based approach that takes benefits of multiple-criteria ratings. The aggregation is the hybrid model that merges user-specific aggregation models with item-specific aggregation models. In this paper, the proposed models are FCM, PCM, and HCM. In PCM, they choose the most authoritative criteria as contexts using information gain. They tried many selections and combinations here and represented the best selections in this research work \[19\].

First, biased MF does not require more details like multi-criteria ratings or contexts. So, for this reason, it is the worst model here. As FCM carries outpour efficiency than the Agg method in the TripAdvisor dataset, so applying contexts as criteria preference will not be inadequate choice every time. Choosing the most influential criteria, PCM performs better Agg in those two datasets. Eventually, they observed, HCM is the finest predictive model with the shortest mean absolute error. It has enough to provide remarkable improvements compared with other models and depends on the statistical paired t-test. To be more specific, it is fit to acquire 4.7% and 8.7% improvements in balancing with the aggregation model, 6.7% and 6.9% improvements compared with the FCM, in the TripAdvisor and Yahoo! Movies datasets, respectively. They have proved that HCM performs better than PCM in this experiment \[19\].

![Figure 3.4 Result comparison.](images/fig3-4.jpg)

[**Figure 3.4**](#c03.xhtml#rfig3-4) Result comparison.

### 3.4.4 Utility-Based Multi-Criteria Recommender Systems by Zheng
