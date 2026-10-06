# CHAPTER 16 HOW'D WE DO? MEASURING THE PERFORMANCE OF ML TECHNIQUES

very costly and a FN isn't bad, so we'd rather err on the side of missing a positive than unnecessarily labeling something positive that isn't. For instance, in product recommendation, no one is really hurt if they like (FN), but if too many products don't like are recommended (FP), they will lose faith in the recommendations. Other cases where high FPs are sentenced to the death penalty (executing someone who's not guilty is worse than not executing someone who is guilty) and spam detection (getting a few spammy messages (FNs) is better than missing an important email (FP)).

The confusion matrix is a great starting point in binary classification, but it doesn't give us much tangible on its. Instead, we use a variety of measures calculated based on the values holds.

# Confusion Matrix–Based Metrics

The metric everyone first thinks of accuracy, a term that is often used in the generic sense of "how well the model did," but it is also the name of a simple and specific metric. Accuracy is simply all the correctly labeled counts by the total number of records. This can be a skewed metric, however, especially in the case of an imbalanced dataset where the total count of actual positives differs from the total count of actual negatives. In extremely imbalanced datasets, we can have very high accuracy while misclassifying every positive value. For instance, if we have 10,000 credit card transaction instances where only 50 are fraudulent, if the classifier simply every single one as negative (not fraudulent), the classifier would have a 99.5% accuracy. This obviously is absurdly misleading and useless.

Precision is another important measure, and it looks how well the classifier did with its positive labels, or what portion of its labeled predictions are actually positive. It focuses on FPs. This is an important metric when FPs are expensive and FNs aren't bad, like in a recommendation system. But it's not the best metric when FNs are dangerous.

575