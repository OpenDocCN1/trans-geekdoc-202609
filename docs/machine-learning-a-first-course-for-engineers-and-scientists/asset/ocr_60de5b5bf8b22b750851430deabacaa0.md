# 11.3 What if we cannot collect more data?

also called inter-rater reliability. It is wise to check this metric on a subset of data by assigning multiple labelers for that data. If the inter-rater reliability is low, you might want to consider addressing this issue. This can be done by assigning multiple labelers to all data points in the validation and test data, and if you can afford the extra labeling cost, also to the training data. For the samples where labelers do not agree, the majority vote can be used for these labels.

# Mismatched training and validation/test data

As pointed out in Chapter 4, we should strive for letting the training data come from the same distribution as the validation and test data. However, there are situations where, for different reasons, we can accept the training data from a slightly different distribution than the validation and test data. One reason was presented in the previous section where we chose mislabeled data in validation and test data, but not necessarily invest the time to do the same correction to the training data.

Another reason for between training and validation/test data is that we have access to substantially larger dataset which comes from a slightly different distribution than the data we care about, but similar enough that the advantage of a larger training data overcomes the disadvantage of that data mismatch. This scenario is further described in Section 11.3.

If we have a mismatch between training data and validation/test data, that mismatch contributes to yet another error of the final validation error $E_{out}$ that we care about. We want to estimate the magnitude of that error. This can be done by revising the training-validation-test split. From the training data we can carve a separate training-validation dataset, see Figure 11.4. That dataset is neither used for training nor validation. However, we evaluate the performance of our model on that dataset as well. As before, the remaining part of the training data is used for training, the validation is used for comparing different model structures, and test data is for evaluating the final performance of the model

This modified split also allows us to revisit the decomposition in (11.1) to include this error source

> $$E_{out} = E_{train} + (E_{val} - E_{train}) + (E_{out} - E_{val}),\quad (11.2)$
$\quad= generalization gap \quad= train-validation mismatch$$

where $E_{train}$ is the performance of the model on the new training-validation data and where, as $E_{out}$ and $E_{train}$ are the performances on validation and training respectively. With this new decomposition, the term $E_{val} - E_{train}$ is an approximation of the generalization gap, that is, how well the model generalizes to unseen of the same distribution as the training data, whereas the $E_{out} - E_{val}$ is the error related to the training-validation data mismatch. If the training-validation data mismatch is not small in comparison to the other two, it is likely that the training-validation mismatch is a big problem and that it is worth focus on reducing the other error and the generalization gap we talked about. On the other hand, if $E_{out} - E_{val}$ is significant, the data mismatch has impact and it might be worth investing time that term. For example, if the mismatch is caused by the fact that we only corrected labels in the validation and test data, we might want to consider correcting labels for the training data as well

# 11.3 What if we cannot collect more data?

We have seen in Section 11.2 that collecting more data is a good strategy to reduce the generalization gap and hence reduce overfitting. However, collecting labeled data is expensive and sometimes not possible. What can we do if we cannot afford to collect more data but still want to benefit from the advantages of a larger dataset we use? In this section we few approaches