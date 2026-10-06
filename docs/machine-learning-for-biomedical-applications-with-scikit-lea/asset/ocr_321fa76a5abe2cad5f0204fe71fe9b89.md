# Decision trees and ensemble learning 159

Child node 2
11 instances
4 0 and 7+

![](bbox=[0.278, 0.083, 0.643, 0.273])

Child node 1
12 instances
10 0 and 2+

Parent node:
23 instances: 14 0 and 9+

Figure 7.7 Decision stump classifier example.

# Example

Let's work through the simple example shown in Fig. 7.7. Here, a parent node with 14 circles and 9 plus signs (23 instances in total) is split into two child nodes, with the first containing 10 circles and 2 plus signs, and the second containing 4 circles and 7 signs.

Before calculating information gain, we need to calculate the entropy of the parent and children using Eq. (7.1). This returns the entropy for the parent as

$H(S_j) = -\left(\frac{14}{23}\log_2\frac{14}{23} + \frac{9}{23}\log_2\frac{9}{23}ight) = 0.966,$$

(7.5)

for child 1 as

$H(S'_j) = -\left(\frac{10}{12}\log_2\frac{10}{12} + \frac{2}{12}\log_2\frac{2}{12}ight) = 0.650,$

(7.6)

and child 2 as

$H(S''_j) = -\left(\frac{4}{11}\log_2\frac{4}{11} + \frac{7}{11}\log_2\frac{7}{11}ight) = 0.946,$

(7.7)

Applying Eq. (7.2), and inserting these values, returns an information gain of

$I_{IG}(S_j) = 0.966 - \left(\frac{12}{23} 	imes 0.650 + \frac{11}{23} 	imes 0.946ight) = 0.174.$

(7.8)

Here, $|S_j| = 23, |S'_j| = 12$ and $|S''_j| = 11$. Doing the same for Gini impurity instead implements

$I_{gini}(S_j) = \frac{12}{23} 	imes Gini_1 + \frac{11}{23} 	imes Gini_2,$

(7.9)