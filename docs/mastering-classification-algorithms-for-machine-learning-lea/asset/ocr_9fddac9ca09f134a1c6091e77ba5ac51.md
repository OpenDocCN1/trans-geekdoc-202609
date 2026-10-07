# Mastering Classification Algorithms for Machine Learning

also assign a label as to whether the email is benign or spam. The variable we refer to the label is also called the dependent variable in machine learning parlance.

In Supervised learning, the machine would find patterns from the independent variables considering the associated dependent variable. From the pattern would emerge a rule that the machine will use when given new values for the independent variables.

The preceding example is a Classification problem where the machine needs to decide whether an email is benign or spam. This type of Classification problem is called a Binary classification problem, as the machine must decide between two options or classes.

There are classification problems where the machine needs to choose between more two classes. Such classification problems are called Multi-class classification problems.

Implementation of classification on the example data provided in Table 1.1 is as follows:

```
import pandas as pd
f = pd.DataFrame([['NO', 'NO', 'NO', 'YES', 'Benign'],
    ['NO', 'NO', 'NO', 'NO', 'Benign'],
    ['YES', 'NO', 'YES', 'NO', 'Spam'],
    ['NO', 'YES', 'YES', 'YES', 'Spam'],
    ['YES', 'NO', 'NO', 'YES', 'Benign'],
    ['YES', 'YES', 'YES', 'YES', 'Spam']
], columns=['ContainsSpellingMistakes', 'ContainsUrgent', 'ContainsASAP', 'ContainsLink', 'Label'])
```

```
ContainsSpellingMistakes ContainsUrgent ContainsASAP ContainsLink Label
0 NO NO NO YES Benign
1 NO NO NO NO Benign
2 YES NO NO YES Spam
3 NO YES YES YES Spam
4 YES NO NO YES Benign
5 YES YES YES YES Spam
```