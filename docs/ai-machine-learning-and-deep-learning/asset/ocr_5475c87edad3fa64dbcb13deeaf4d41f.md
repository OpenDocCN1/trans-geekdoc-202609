Rather than random label flipping, an attacker can also utilize label flip attacks that are model dependent. For instance, in subsection 1.2.2, we showed that SVM constructs a decision hyperplane using only the support vectors. Existing studies presented a few label flipping attacks based on this characteristic. For example, a Farfirst attack [46] is such a label flipping attack, where a training instance far away from the margin of an SVM is flipped. This attack effectively changes many nonsupport vector training instances (training instances that are far from the margin and are correctly classified by an untainted SVM) to support vectors and significantly alter the decision boundary consequently.

Formally, an optimal label flipping attack can be considered a bilevel optimization problem defined as follows.

# **Definition 15 (Optimal Label Flipping Attack):**

Suppose that training set and a test set where andLet I be the number of training labels that an attacker has the ability to modify, and let be an indicator vector such that its ith element is equal to −1 if the ith training label is flipped and 1 otherwise. Then and the poisoned training set where It is called an optimal label flipping attack if an attacker can find an optimal I by solving the following optimization problem:

where O is an objective function specified by the attacker. (1.5.1) A common objective function is to maximize the test error rate, in which case where J is an indicator function such that

(1.5.2)

However, solving such a bilevel optimization problem is NP-hard. Here, we introduce a simple greedy algorithm that is suboptimal but tractable. At iteration an attacker initially flips the label of the first training instance to obtain a poisoned training set Then the attacker trains an ML model using and evaluates the performance of the poisoned model. Next, the attacker flips the label of the second training instance while keeping other labels untainted. Similarly, the attacker trains the ML model using the poisoned dataset and evaluates its performance on the test set. The attacker repeats this process for each training label to obtain Now, the attacker can