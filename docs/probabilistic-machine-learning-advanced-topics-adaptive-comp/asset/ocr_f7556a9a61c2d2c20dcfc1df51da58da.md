possible to attach small "adversarial stickers" to traffic signs to classify stop signs as speed limit signs.

Below we briefly discuss how to create adversarial attacks, why they occur, and how we can try to defend against them. We focus on the case of deep neural nets for images, although it is important to note that many other kinds of models (including logistic regression and generative models) can also suffer from adversarial attacks. Furthermore, this is not restricted to the image domain, but occurs with many kinds of high dimensional inputs. For example, [Li+19] contains an audio attack and [Dal+04; Jia+19] contains a text attack. More details on adversarial examples can be found in e.g., [Wiy+19; Yua+19].

# 19.8.1 Whitebox (gradient-based) attacks

To create an adversarial example, we must find a "small" perturbation \(\boldsymbol{\delta}\) to add to the input \(\boldsymbol{x}\) to create \(\boldsymbol{x}_{\text{adv}} = \boldsymbol{x} + \boldsymbol{\delta}\) so that \(f(\boldsymbol{x}_{\text{adv}}) = y'\), where \(f()\) is the classifier, and \(y'\) is the label we want to force the system to output. This is known as a **targeted attack**. Alternatively, we may just want to find a perturbation that causes the current predicted label to change from its current value to any other value, so that \(f(\boldsymbol{x} + \boldsymbol{\delta}) \neq f(\boldsymbol{x})\), which is known as **untargeted attack**.

In general, we define the objective for the adversary as *maximizing* the following loss:

```
\boldsymbol{x}_{\text{adv}} = \argmax_{\boldsymbol{x}' \in \Delta(\boldsymbol{x})} \mathcal{L}(\boldsymbol{x}', y; \boldsymbol{\theta})
```

where y is the true label. For the untargeted case, we can define \(\mathcal{L}(\boldsymbol{x}', y; \boldsymbol{\theta}) = -\log p(y|\boldsymbol{x}')\), so we minimize the probability of the true label; and for the targeted case, we can define \(\mathcal{L}(\boldsymbol{x}', y; \boldsymbol{\theta}) = \log p(y'|\boldsymbol{x}')\), where we maximize the probability of the desired label \(y' \neq y\).

To define what we mean by "small" perturbation, we impose the constraint that \(\boldsymbol{x}_{\text{adv}} \in \Delta(\boldsymbol{x})\), which is the set of "perceptually similar" images to the input \(\boldsymbol{x}\). Most of the literature has focused on a simplistic setting in which the adversary is restricted to making bounded \(l_p\) perturbations of a clean input \(\boldsymbol{x}\), that is

```
\Delta(\boldsymbol{x}) = \{ \boldsymbol{x}' : ||\boldsymbol{x}' - \boldsymbol{x}||_p < \epsilon \}
```

Typically people assume p = 1 or p = 0. We will discuss more realistic threat models in Section 19.8.3.

In this section, we assume that the attacker knows the model parameters \(\boldsymbol{\theta}\); this is called a **whitebox attack**, and lets us use gradient based optimization methods. We relax this assumption in Section 19.8.2.)

To solve the optimization problem in Equation (19.47), we can use any kind of constrained optimization method. In [Sze+14] they used bound-constrained BFGS. [GSS15] proposed the more efficient **fast gradient sign (FGS)** method, which performs iterative updates of the form

```
\boldsymbol{x}_{t+1} = \boldsymbol{x}_t + \boldsymbol{\delta}_t
\boldsymbol{\delta}_t = \epsilon \text{sign}(\nabla_{\boldsymbol{x}} \log p(y'|\boldsymbol{x}, \boldsymbol{\theta})|_{\boldsymbol{x}_t})
```

where \(\epsilon > 0\) is a small learning rate. (Note that this gradient is with respect to the input pixels, not the model parameters.) Figure 19.23 gives an example of this process.

More recently, [Mad+18] proposed the more powerful **projected gradient descent (PGD)** attack; this can be thought of as an iterated version of FGS. There is no "best" variant of PGD for