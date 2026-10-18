error-generic evasion attack. In this attack, the attacker misclassifies an input sample to be a diamond rather than a circle.

# ### 6.3.1.2  Poisoning Attack

An attacker injects poisoning samples into training data in the training phase. The attacks can also be classified into error-generic and error-specific. Error-generic poisoning attacks aim to increase the probability of other classes with the same input data and to make the learning model unable to return the correct class. In error-specific poisoning attacks, an attacker aims to cause specific misclassifications (see Figure 6.3).

![](bbox=[0.117, 0.353, 0.823, 0.627])

**FIGURE 6.3** Example of the backdoor poison attack. Left: A typical training dataset for binary classification of squares and diamonds, two classes. Right: Training dataset poisoned with perturbed squares (*x* depicted in the squares).

# ### 6.3.2  Adversarial Attack on Deep Learning

Adversarial ML is an extensive study topic. We can narrow it down to be more specific DL. DL is applied in supervised learning. It has correct answers for its dataset during the training phase. Therefore, it has evasion attacks and poisoning attacks in deep neural network (DNN). The attacker