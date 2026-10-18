The model predicts that the poisoned bottle came from vineyard 1. Time to go make an arrest!

# **SIDEBAR**  
**Ronald Fisher**

You may be happy to know that, in the real world, Ronald Fisher wasn’t poisoned at a dinner party! This is, perhaps, fortunate for you, because Sir Ronald Fisher (1890 - 1962) was a famous biostatistician who went on to be called the father of statistics. Fisher developed many statistical tools and concepts we use today, including discriminant analysis! In fact, linear discriminant analysis is commonly confused with *Fisher’s discriminant analysis*, the original form of discriminant analysis Fisher developed (but which is slightly different).

Fisher was also, however, a proponent of eugenics, the belief that some races are superior to others. In fact, he shared his opinions in a 1952 UNESCO statement called *The Race Question* in which he said that “the groups of mankind differ profoundly in their innate capacity for intellectual and emotional development” (https://unesdoc.unesco.org/ark:/48223/pf0000073351). Perhaps now you don’t feel so sorry for our murder mystery victim!

# 5.3 *Strengths and weaknesses of LDA and QDA*

While it often isn’t easy to tell which algorithms will perform well for a given task, here are some strengths and weaknesses that will help you decide whether LDA and QDA will perform well for your task.

The strengths of the LDA and QDA algorithms are:

+   - They can reduce a high-dimensional feature space into a much more manageable number
+   - Can be used for classification or as a preprocessing (dimension reduction) technique to other classification algorithms that may perform better on the dataset
+   - QDA can learn curved decision boundaries between classes (this isn’t the case for LDA)

The weaknesses of the LDA and QDA algorithms are:

+   - They can only handle continuous predictors (although recoding a categorical variable as numeric *may* help in some cases)
+   - They assume the data are normally distributed across the predictors. If the data are not, performance will suffer
+   - LDA can only learn linear decision boundaries between classes (this isn’t the case for QDA)
+   - LDA assumes equal covariances of the classes and performance will suffer if this isn’t the case (this isn’t the case for QDA)
+   - QDA is more flexible than LDA, and so can be more prone to overfitting