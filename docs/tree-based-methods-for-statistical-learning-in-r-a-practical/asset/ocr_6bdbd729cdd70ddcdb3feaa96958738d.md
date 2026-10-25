Class | Number | Posterior
---|---|---
no | 16354 | 0.7788E+00
yes | 4646 | 0.2212E+00

Number of training cases misclassified = 4646
Predicted class is no

Node 2: Terminal node

Class | Number | Posterior
---|---|---
no | 15686 | 0.8331E+00
yes | 3143 | 0.1669E+00

Number of training cases misclassified = 3143
Predicted class is no

Node 3: Terminal node

Class | Number | Posterior
---|---|---
no | 668 | 0.3077E+00
yes | 1503 | 0.6923E+00

Number of training cases misclassified = 668
Predicted class is yes

Classification matrix for training sample:

Predicted class | True class no | yes
---|---|---
no | 15686 | 3143
yes | 668 | 1503
Total | 16354 | 4646

Number of cases used for tree construction: 21000
Number misclassified: 3811
Resubstitution estimate of mean misclassification cost: 0.18147619

The train and test set accuracies for this tree are 81.85% and 82.21%, respectively (I had to use the R function produced by GUIDE to compute the test accuracy). Despite the reasonably high accuracy, we have a big problem! If you didn't first notice when initially exploring the data on your own, then hopefully you see it now...the model is biased towards predicting yes since the data are imbalanced (and naturally so, since we'd hope that most people are not defaulting on their credit card payments).

The original goal was to build a model to predict the probability of defaulting (default = "yes"), but the train and test accuracy within that specific class are 32.35% and 33.87%, respectively. By default, GUIDE (and many other algorithms) treat the misclassification for both types of error (i.e., predicting a yes as a no and vice versa) as equal. Fortunately, like CART, GUIDE can incorporate a matrix of misclassification costs into the tree construction (see Section 2.2.4).