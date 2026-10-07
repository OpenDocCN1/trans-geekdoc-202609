From Table Annexure 8.6, we see that for all the data points, the value of y is 1. So, we have a leaf node with the decision y = 1.

So, our final decision tree looks as shown in Figure Annexure 8.7:

![](bbox=[0.335, 0.187, 0.503, 0.276])

![](bbox=[0.203, 0.311, 0.368, 0.399])

![](bbox=[0.478, 0.311, 0.653, 0.399])

![](bbox=[0.343, 0.442, 0.513, 0.531])

![](bbox=[0.623, 0.442, 0.793, 0.531])

Decision: y = 1

Decision: y = 0

Decision: y = 1

Figure Annexure 8.7: Final decision tree for the dataset in Table A8.1.

# Using Scikit-Learn to build Decision Tree using Entropy

Using the Scikit-Learn library, it is easy to build decision trees without going through many calculations. The code sample is provided below. Notice that the decision tree created by Scikit-Learn is the same as the one created manually.

```
import warnings
warnings.filterwarnings('ignore')
```

```
!pip install pydot
!pip install pydotplus
!pip install graphviz
```