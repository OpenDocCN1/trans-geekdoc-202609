
[**Figure 4.7**](#c04.xhtml#R_c04-fig-0016): Coefficient curves for rocks versus mines classification problem solved by converting to labels

Another approach is to formulate the problem in terms of the likelihoods of the two outcomes in the problem. That leads to what's called *logistic regression*. The `glmnet` algorithm can be cast in that framework, and Friedman's original paper goes through the development of the logistic regression version of `glmnet` and of its extension to multiclass problems—problems with more than two discrete outcomes. You'll see the use of the binary and multiclass versions of the algorithm in [Chapter 5](#c05.xhtml).

### Working with Classification Problems Having More Than Two Outcomes

Some problems require deciding among several alternatives. For example, say you show a visitor to your website several links. The visitor may click any one of the several links, click the back button, or exit the site entirely. There are several alternatives that aren't ordered like the integer wine taste scores are. A taste score of 4 naturally fits between 3 and 5, and if changing an attribute (like alcohol) makes the score go from 3 to 4, changing it some more seems likely to move the score further in the same direction. Alternative actions a site visitor will take have no such order. This is called a multiclass classification problem.

You can always handle a multiclass problem with an algorithm for binary classification. The technique is called *one versus all* or *one versus the rest*, and the names give you some idea of how the approach works. Basically you pose your multiclass problem as several binary problems. For the example, you could predict whether the visitor would leave the site or choose another option. Another binary classification problem is to predict whether the user would click the back button or take any of the rest of the options available. You'll wind up with as many binary classification problems as you have alternative outcomes. The binary classifiers all give numeric values, like the LARS classifier in [Listing 4.4](#c04.xhtml#c04-fea-0005). The outcome that has the largest one-versus-all value is the winner. [Chapter 5](#c05.xhtml) implements this method for the glass data set, where there are six different possible outcomes.

### Understanding Basis Expansion: Using Linear Methods on Nonlinear Problems

By their nature, linear methods assume classification and regression predictions can be expressed as a linear combination of the attributes that are available to the designer. What if you have reason to suspect that a linear model isn't enough? You can get a linear model to work with strong nonlinearities by using what's called basis expansion. The basic idea behind basis expansion is that the nonlinearities in your problem can be approximated as polynomials of the attributes (or sum of other nonlinear functions of the attributes); then you can add attributes that are powers of the original attributes and let a linear method determine the best set of coefficients for the polynomial.

To get a concrete idea of how this would work, look at the code in [Listing 4.5](#c04.xhtml#c04-fea-0006). [Listing 4.5](#c04.xhtml#c04-fea-0006) starts with the wine taste data set. If you recall, the linear models that were produced earlier in this chapter both found that alcohol was the most important attribute in determining wine taste. It occurs to you that the relationship might not be a straight line, but might roll off for really high alcohol content and for really low alcohol content.

[Listing 4.5](#c04.xhtml#c04-fea-0006) shows you how to test this notion.

#### [Listing 4.5](#c04.xhtml#R_c04-fea-0006): Basis Expansion for Wine Taste Prediction—wineBasisExpansion.py

```
__author__ = 'mike-bowles'

from Read_Fcns import list_read_wine
import matplotlib.pyplot as plt
from math import sqrt, cos, log

#read wine data
names, xList, labels = list_read_wine()

#extend the alcohol variable - the last column in that attribute matrix
xExtended = []
alchCol = len(xList[1])


for row in xList:
    newRow = list(row)
    alch = row[alchCol - 1]
    newRow.append((alch - 7) * (alch - 7)/10)
    newRow.append(5 * log(alch - 7))
    newRow.append(cos(alch))
    xExtended.append(newRow)

nrow = len(xList)
v1 = [xExtended[j][alchCol - 1] for j in range(nrow)]

for i in range(4):
    v2 = [xExtended[j][alchCol - 1 + i] for j in range(nrow)]
    plt.scatter(v1,v2)

plt.xlabel("Alcohol")
plt.ylabel(("Extension Functions of Alcohol"))
plt.show()
```

The code reads in the data as before. Right after reading in the data (and before it is normalized), the code runs through the rows of data that it's read, adds a few new elements to the row, and then appends the new expanded row to a new set of attributes. The new elements that are appended are all functions of the alcohol attribute in the original data. For example, the first new attribute is `((alch - 7) * (alch - 7)/10)`, where `alch` is the alcohol level in the row. The constants `7` and `10` were introduced so that the resulting new attributes would all plot nicely on one plot. Basically, the new attribute is alcohol squared.

The next step in the process is to take the expanded set of attributes and build a linear model using the tools already developed in this chapter (or another of the methods available for building linear models). Whatever algorithm is used for building a linear model, the model will consist of multipliers (or coefficients) for each of the attributes, including the new ones. If the functions used in the expansion are all powers of the original variable, the linear model yields coefficients in a polynomial function of the original variable. By choosing different functions for the expansion, other function series can be constructed.

[Figure 4.8](#c04.xhtml#c04-fig-0017) illustrates the functional dependence of the new attributes (and the original attribute) on the original attribute. You can see the squared, logarithmic, and sinusoidal behavior of the selection of functions in the expansion.

![Figure 4.8: Functions generated to expand wine attribute session](images/c04f008.png)

[**Figure 4.8**](#c04.xhtml#R_c04-fig-0017): Functions generated to expand wine attribute session

### Incorporating Non-Numeric Attributes into Linear Methods
