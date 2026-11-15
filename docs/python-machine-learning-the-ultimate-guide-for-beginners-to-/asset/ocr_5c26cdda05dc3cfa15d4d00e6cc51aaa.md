complex decision trees that can’t perform accurately on
general data. However, the issue of overfitting isn’t only
found in this case. Many algorithms have to deal with it.
The easiest solution you can deploy to limit the risk of
overfitting is the application of parameter limitations.

+   2. Categorization: When your data set has a large number of
+   continuous numerical variables, decision trees will
+   encounter difficulty when it comes to categorizing them.
+   Information is often lost during this process. Take note that
+   continuous variables are considered to be anything with a
+   value that is specifically defined between a certain
+   minimum and maximum. For instance, let’s say that we
+   have some data which specifies that only people between
+   21 and 45 can join the military. The age variable is
+   considered to be continuous because we have set limits.

+   3. Picky algorithms: The algorithm doesn’t always choose the
+   most accurate and efficient decision tree from which you
+   draw your conclusion. This is simply the nature of the
+   technique. However, the solution is simple. All you need to
+   do is train multiple trees in order to sample a larger number
+   of features randomly and find the most accurate solution.

You learned earlier in this section that decision trees are used to
perform regression tasks, as well as classification tasks. However,
this doesn’t mean that you use the identical method for both tasks.
You need to split the decision trees into two different categories,
namely the regression trees and classification trees. The basics are
still the same for both categories, however, there are a number of
differences you should be aware of:

+   1. Regression trees are specifically applied for tasks that
+   involve continuous dependent variables. At the same time
+   classification trees are needed when dealing with
+   categorical dependent variables.

+   2. The values that we extract as the result from the training
+   data are determined differently for each category of
+   decision trees. In the case of classification trees the value