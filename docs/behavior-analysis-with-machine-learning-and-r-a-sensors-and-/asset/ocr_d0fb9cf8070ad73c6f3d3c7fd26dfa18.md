# CHAPTER 5. PREPROCESSING BEHAVIORAL DATA

```
# sweep : 94 Mean :0.4569 Mean :0.582 Mean :0.603
# type_on_keyboard: 85 3rd Qu.:0.5967 3rd Qu.:0.728 3rd Qu.:0.724
# wash_hands : 78 Max. :0.9801 Max. :1.000 Max. :1.000
# watch_tv : 107
```

Now the variables on the train set are exactly between 0 and 1 for all numeric variables. For the test set, but not min values will be 0 or a bit higher. Conversely, some max values will be lower than 1. This is because the test set may have a min value that is greater than the min value of the train set and a max value that is smaller than the max value of the train set. However, after normalization, all values are guaranteed to be within 0 and 1.

# 5.4 Imbalanced Classes

Ideally, classes will be uniformly distributed, that is, there is approximately the same number of instances per class. In real-life (as always), this is not the case. And in many situations (more than you may think), class counts are heavily skewed. When this happens the dataset is set to be imbalanced. Take as an example, bank transactions. Most of them will be normal when a small percent be fraudulent. In the medical field this is very common. It is easier to collect samples from healthy individuals compared to samples from individuals with rare conditions. For example, a database may have thousands of images from healthy tissue but with signs of cancer. Of course, having a few cases with diseases is a good thing for the world! but not for machine learning methods. This is because predictive models will try to learn their parameters such that the error is reduced and most of the time this error is based on accuracy, the models will be biased towards making correct predictions for the majority classes (the ones with higher counts) while paying attention to minority classes. This can be a problem because some applications we may be more interested in detecting the minority classes (illegal transactions, cancer cases, etc.).

Suppose a given database has 998 instances with class 'no cancer' and only 2 instances with class 'cancer'. A trivial classifier that always predicts 'no cancer' will have an accuracy of 98.8% will not be able to detect any of the 'cancer' cases! So, what can we do?

+   - Collect more data from the minority class. In practice, this can be difficult, expensive, etc. or just impossible because the study was conducted a long time ago and it is no longer possible to replicate the context.