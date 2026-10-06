H(6,6) = 1

thus, the information gain for Price is:

```
infoGain(Price) = 1 - meanH(Price) = 1 - 0.459 = 0.541
```

For the rest of the variables the information gain is:

+   - infoGain(Tired) = 0

+   - infoGain(Rain) = 0.020

+   - infoGain(Comedy) = 0

The highest information gain is produced by Price, thus, it is selected as the root node. Since branches Then, the process continues recursively for each branch excluding Price. Since branches with values low and high are already done, we only need to split medium. Sometimes it is not possible to have completely pure nodes excluding low and high. This can happen for example, when there are no more attributes left or when two more instances have the same feature values but different labels. In those situations the final prediction is the most common label (majority vote).

There exist many implementations of decision trees. Some implementations compute variable importance using the entropy (as shown here) but others use the Gini index, for example. Each implementation also treats numeric variables in different ways. Pruning the tree using different techniques is also common in order to reduce its size.

Some of the most common implementations are C4.5 trees (Quinlan, 2014) and CART (Steinberg and Colla, 2009). The later is implemented in the rpart package (Therneau and Atkinson, 2019) which will be used in the following section to build a model that predicts physical activities from smartphones sensor data.

# 2.3.1 Activity Recognition with Smartphones

```
smartphone_activities.R
```

As mentioned in the introduction, behavior can be an observable activity in a human. We can easily infer what physical activity someone is doing by looking at her/his body movements. Observing physical activities can provide useful behavioral and contextual information about

![](bbox=[0.081, 0.777, 0.142, 0.811])