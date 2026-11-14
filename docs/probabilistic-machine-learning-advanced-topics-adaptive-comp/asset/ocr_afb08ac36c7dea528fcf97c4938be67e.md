![](bbox=[0.295, 0.095, 0.71, 0.205])

Figure 19.23: Example of an adversarial attack on an image classifier. Left column: original image which is correctly classified. Middle column: small amount of structured noise which is added to the input (magnitude of noise is magnified by 10x). Right column: new image, which is confidently misclassified as a "gibbon", even though it looks just like the original "panda" image. Here \(\epsilon = 0.007\). From Figure 1 of [GSS15]. Used with kind permission of Ian Goodfellow.

data per task is large, whereas online learning is more concerned with fast adaptation to slowly (or piecewise continuously) changing distributions using small amounts of data per time step.

# 19.8 Adversarial examples

*This section is coauthored with Justin Gilmer.*

In Section 19.2, we discussed what happens to a predictive model when the input distribution shifts for some reason. In this section, we consider the case where an adversary deliberately chooses inputs to minimize the performance of a predictive model. That is, suppose an input \(\mathbf{x}\) is classified as belonging to class \(c\). We then choose a new input \(\mathbf{x}_{adv}\) which minimizes the probability of this label, subject to the constraint that \(\mathbf{x}_{adv}\) is "perceptually similar" to the original input \(\mathbf{x}\). This gives rise to the following objective:

```
\(\mathbf{x}_{adv} = \underset{\mathbf{x}' \in \Delta(\mathbf{x})}{\text{argmin}} \log p(y=c|\mathbf{x}') \qquad (19.46)\)
```

where \(\Delta(\mathbf{x})\) is the set of images that are "similar" to \(\mathbf{x}\) (we discuss different notions of similarity below).

Equation (19.46) is an example of an **adversarial attack**. We illustrate this in Figure 19.23. The input image \(\mathbf{x}\) is on the left, and is predicted to be a panda with probability 57%. By adding a tiny amount of carefully chosen noise (shown in the middle) to the input, we generate the **adversarial image** \(\mathbf{x}_{adv}\) on the right: this "looks like" the input, but is now classified as a gibbon with probability 99%.

The ability to create adversarial images was first noted in [Sze+14]. It is suprisingly easy to create such examples, which seems paradoxical, given the fact that modern classifiers seem to work so well on normal inputs, and the perturbed images "look" the same to humans. We explain this paradox in Section 19.8.5.

The existence of adversarial images also raises security concerns. For example, [Sha+16] showed they could force a face recognition system to misclassify person A as person B, merely by asking person A to wear a pair of sunglasses with a special pattern on them, and [Eyk+18] show that is