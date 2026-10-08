In this plot, the classification accuracy reported for a number of training subjects p is the average of many trials as subjects as there are in the dataset. In each trial, a different subject was considered, and all his/her samples were included in the test set. The training set was composed of all samples p subjects other than the test subject, chosen at random but maintained across the different algorithms to allow for a fair comparison.

Both the proposed and the subject-based max-min scaling used in [33,65] showed better results when more subjects were used for learning. On, the z-score normalization did not seem to benefit from data transformation when the number of training subjects increased. The higher performance of the proposed data transformation can easily be observed in all databases. This shows as a positive trend that increases reliability as more users are incorporated into the model, and further supports the validity of inter-subject models when they are combined with a suitable transformation function that takes individual traits into consideration.

![](bbox=[0.133, 0.303, 0.866, 0.804])

Figure 5. Classification accuracy as the number of training users is increased: (a) DEAP; (b) MAHNB-HCI; and (c) DREAMER.

# 6. Conclusions

Subject-independent models fail to consider that the appraisal of one’s emotional state is strongly related to personal factors, such as one’s circumstances [39]. Subject-dependent models aim to tackle