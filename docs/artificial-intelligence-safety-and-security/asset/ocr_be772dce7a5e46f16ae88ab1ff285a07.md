![](bbox=[0.1, 0.13, 0.9, 0.38])

FIGURE 17.5 Defensive distillation uses two models. The first network produces very smooth probability outputs, which has good defensive properties (its loss surface is naturally less jagged). The second network uses those probabilities to generate highly nonuniform probabilities, which are used for confident class predictions.

adversarial training regime still ensures that the defender can efficiently generate a sufficiently sizable adversarial example dataset and use it to smooth out much of the model's error surface.

# DEFENSIVE DISTILLATION

Another defense method proposed by Papernot et al. is known as defensive distillation [7]. This method is based on a knowledge transfer technique developed by Hinton et al. [8]. This method originally used the knowledge from complicated neural networks (or ensembles of neural networks) to train simple neural networks that were able to perform approximately as well as their source networks.

Normally, a model maps from input examples to highly confident predictions. For example, a model is more likely to classify an image of a dog with a distribution of 98% dog and 2% cat (highly nonuniform probabilities) rather than 54% dog and 46% cat (highly uniform probabilities). A nonuniform probability output allows for confident predictions, but a uniform probability output is more useful for classification purposes as it is less biased toward choosing one class over another. Distillation encourages a neural network to make more uniform predictions, reducing the potential for random noise to affect the network’s prediction. From an adversarial defense perspective, this means that an adversary would have more difficulty finding such noise that also remains imperceptible to humans (Figure 17.5).

In essence, the goal of defensive distillation is to incorporate the advantages of both the defensive properties of uniform probability outputs and the confidence benefits of nonuniform probability outputs. For a formal description of how defensive distillation uses this two-stage process, we refer the reader to Papernot et al.’s paper on defensive distillation [7].

# Gradient Blocking Defenses

A promising defense is to directly hide the feedback signals that adversaries rely on to construct adversarial attacks. As explained in the self-driving car case study attackers find ways to trick models by perturbing the input slightly and observing how that perturbation affects the model’s confidence in its classification of the input. The perturbation is best performed by following the direction of the gradient. As such, by hiding information about the gradient from the attacker, the defender can effectively prevent these attacks from happening. This process is known as gradient masking (Figure 17.6).