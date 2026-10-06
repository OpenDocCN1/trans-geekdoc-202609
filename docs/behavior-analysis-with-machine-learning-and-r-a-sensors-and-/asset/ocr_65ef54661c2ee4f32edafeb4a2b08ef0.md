# CHAPTER 3. PREDICTING BEHAVIOR WITH ENSEMBLE LEARNING

New train set D'

![](bbox=[0.191, 0.149, 0.8, 0.315])

Figure 3.5: Process to generate the new train set D' for the meta-learner by column-binding predictions of the first-level learners and adding the true labels.

In the next section, I will introduce Multi-view Stacking which basically is the same as Generalized Stacking but each first-level learner is trained with features from a different view.

# 3.4 Multi-view Stacking for Home Tasks Recognition

```
stacking_algorithms.R stacking_activities.R
```

Multi-view learning refers to the case when an instance can be characterized by two or more independent ‘views’. For example, one can extract features for webpage classification from a webpage’s text also from the links pointing to it. Usually, there is the assumption that the views are independent and each is sufficient to solve the problem. Then, why combine them? In many cases, each view provides additional and complementary information, thus, allowing to train better models.

The simplest thing one can do is to extract features from each view, aggregate them, and train a single model. This approach usually works well but it has some limitations. Each view may have different statistical properties, thus different types of models may be needed for each view. When aggregating features from all views, variable correlations may be introduced which could impact the performance. Another limitation is that features need to be in the same format (feature vectors, images, etc.), so they can be aggregated.

For video classification, we could have two views. One represented by sequences of images, and the other one by the corresponding audio. For the video part, we could encode the