
tedium of an attack if they have a clear objective. It should also be clear that adversarial attacks can be successfully deployed after days or weeks of effort (usually in training a pseudo-model) rather than the millennia necessary to crack cryptographic security. Security against adversarial machine learning should not rely entirely on the assumption that an attacker would not devote enough effort to break the system.

Barring any attack on the model itself, an adversary could focus on attacking the data used to train a model—a process known as poisoning. In a poisoning attack, the adversary exerts control over the learning process by inserting carefully crafted samples into the training dataset. These samples are designed to artificially skew the training data distribution and thus degrade the performance of the model. Poisoning attacks are effective against models that are frequently re-trained with real-world data. Given the data gathered to train one model will be shared with all of its counterparts, it is relatively straightforward to poison hundreds, if not thousands, of products such as cars and facial recognition security cameras by infecting the data collected by a single product.

As an example, malicious email campaigns are constantly evolving to circumvent spam filters. Anti-spam systems need to collect data from recent spam campaigns to stay up to date. Manually labeling this data is infeasible, so the system relies on automated training data collection. For example, it might store a list of email addresses known to regularly send spam and automatically mark emails sent from this blacklisted address as “spam” in the training data. The group in control of these addresses might be aware that they are flagged and choose to instead send out emails that are not characteristic of spam emails, and the system would learn to identify them as “spam-like.” If the automatic labeling system mislabels a significant number of these emails, the trained spam detection model will learn the wrong class distributions, identifying spam as legitimate, and then classify regular emails as spam.

One potential defense against poisoning attacks is to thoroughly sanitize the training data. Practically, this amounts to detecting and removing suspicious points and outliers, and only using data from trusted data repositories. Although large volumes of data are often necessary to produce good machine learning models, untrustworthy or unverified data repositories can similarly hamper machine learning models. Another sanitation method is to use a “reject on negative impact” analysis on new data. In this setup, the system compares model performance before and after training on the suspect samples. If the new data significantly decreases test accuracy on legitimate examples, the system discards the new training samples.

As the field progresses, it seems as if adversaries shatter adversarial defenses as soon as they are constructed. However, there are several promising research directions. The first is model ensembling: combining information from multiple “base” models to make a single classification. Ensembling tends to accentuate the strengths of base models when they perform well, and mask the weaknesses of base models when they perform poorly. One variant of this approach seems to lessen the susceptibility of adversarially trained models to white box attacks [16]. By consulting multiple sources before making a decision, this method smooths the error surface, rendering the model robust to adversarial attacks as seen in section “Attacks Against a Model.”

We may also see improved robustness to adversarial examples as large research groups (such as Google and Facebook) train models on gigantic datasets. By encompassing a greater range of input possibilities, these models trained on large datasets may learn smoother error surfaces, and thus greater robustness to adversarial attacks. However, this still only solves the subset of problems where large amounts of data are available.

## Conclusion

Adversarial attacks and defenses constantly evolve alongside artificial intelligence. Currently, it seems that most attacks are very difficult to defend against. However, some defenses do show promise in scenarios where the attacker only has access to limited information about the model. When considering this arms race in adversarial learning, it seems as though the adversary currently has the upper hand. In order to be truly robust against any attack, a model would need to learn and retain all the possible knowledge/information about a learning problem, whether that involves pro-actively (and impractically) training on all the possible training samples, an infinite space, or reactively somehow catching and sanitizing any and all adversarial attacks.

One thing is certain: before relying on and integrating machine learning models into safety-critical systems such as self-driving cars, more research needs to be conducted to ensure their integrity. Developing robust defenses is critical as unsafe applications could come at the cost of human life.

## References

- 1. Dept. of Statistics 2016. “NSC motor vehicle fatality estimates.”
- 2. N. Papernot, P. McDaniel, S. Jha, M. Fredrikson, Z. B. Celik, & A. Swami 2016. “The limitations of deep learning in adversarial settings.” In 2016 IEEE European Symposium on Security and Privacy (EuroS&P), pp. 372–387. IEEE, Saarbrücken, Germany.
- 3. N. Papernot, P. McDaniel, I. Goodfellow, S. Jha, Z. B. Celik, & A. Swami 2017. “Practical black-box attacks against machine learning.” In Proceedings of the 2017 ACM on Asia Conference on Computer and Communications Security, pp. 506–519. ACM, Abu Dhabi, UAE.
- 4. N. Papernot, P. McDaniel, & I. Goodfellow 2016. “Transferability in machine learning: from phenomena to black-box attacks using adversarial samples.” arXiv preprint arXiv:1605.07277.
- 5. I. J. Goodfellow, J. Shlens, & C. Szegedy 2014. “Explaining and harnessing adversarial examples.” arXiv preprint arXiv:1412.6572.
- 6. A. Kurakin, I. Goodfellow, & S. Bengio 2016. “Adversarial machine learning at scale.” arXiv preprint arXiv:1611.01236.
- 7. N. Papernot, P. McDaniel, X. Wu, S. Jha, & A. Swami 2015. “Distillation as a defense to adversarial perturbations against deep neural networks.” In Proceedings of the 37th IEEE Symposium on Security and Privacy, pp. 582–597. IEEE, San Jose, California.
- 8. G. Hinton, O. Vinyals, & J. Dean 2015. “Distilling the knowledge in a neural network.” arXiv preprint arXiv:1503.02531.
- 9. N. Papernot, P. McDaniel, A. Sinha, & M. Wellman 2016. “Towards the Science of Security and Privacy in Machine Learning.” arXiv e-prints.
- 10. N. Carlini & D. A. Wagner 2016. “Defensive distillation is not robust to adversarial examples.” CoRR abs/1607.04311. http://arxiv.org/abs/1607.04311.
- 11. W. Xu, D. Evans, & Y. Qi 2017. “Feature squeezing: Detecting adversarial examples in deep neural networks.” arXiv preprint arXiv:1704.01155.
- 12. W. He, J. Wei, X. Chen, N. Carlini, & D. Song 2017. “Adversarial example defenses: Ensembles of weak defenses are not strong.” arXiv preprint arXiv:1706.04701.
- 13. D. Meng & H. Chen 2017. “Magnet: a two-pronged defense against adversarial examples.” arXiv preprint arXiv:1705.09064.
- 14. P. Baldi 2012. “Autoencoders, unsupervised learning, and deep architectures.” In Proceedings of ICML Workshop on Unsupervised and Transfer Learning, Bellevue, Washington, pp. 37–49.
- 15. K. Grosse, N. Papernot, P. Manoharan, M. Backes, & P. McDaniel 2016. “Adversarial perturbations against deep neural networks for malware classification.” arXiv preprint arXiv:1606.04435.
- 16. F. Tramèr, A. Kurakin, N. Papernot, D. Boneh, & P. McDaniel 2017. “Ensemble adversarial training: Attacks and defenses.” arXiv preprint arXiv:1705.07204.

## 18 Value Alignment via Tractable Preference Distance

Andrea Loreggia, Nicholas Mattei, Francesca Rossi, and K. Brent Venable

### Contents

| Section | Page |
|---|---|
| Introduction | 249 |
| Background: CP-Nets | 251 |
| Using CP-Nets to Model Ethics | 252 |
| Notions of Distance between CP-Nets | 255 |
| Using CP-Nets to Support Ethical Decisions | 256 |
| Empirical Analysis | 257 |
| Conclusions | 259 |
| Acknowledgments | 260 |
| References | 260 |

### Introduction

Preferences are ubiquitous in everyday life: we use our own subjective preferences whenever we want to make a decision to choose our most preferred alternative. Hence, the study of preferences in computer science and AI has been very active for a number of years with important theoretical and practical results [13,21] as well as libraries and datasets [20]. In many scenarios including multi-agent systems [25] and recommender systems [22], user preferences play a key role in driving the decisions the system makes. Thus it is important to have preference modeling frameworks that allow for expressive and compact representations, effective elicitation techniques, and efficient reasoning and aggregation.

If we want people to trust AI systems, we need to provide these systems with the ability to discriminate between what one would broadly call “good” and “bad” decisions. In many instances, the quality of a decision should not be based only on the preferences or optimization criteria of the decision makers, but also on properties related to the impact of the decision such as whether or not it is ethical or legal according to constraints or priorities given by any number of exogenous sources [5,24,26]. Indeed, there may be specific ethical principles, depending on the context, that could and should override the subjective preferences of the decision maker.

For the subjective preferences, they may apply to one or more of the individual components of a complex decision, rather than to the whole thing. For example, if we need to choose a car, we may prefer certain colors over others, and we may prefer certain brands over others. We may also have conditional preferences, such as in preferring red cars if the car is a convertible. For these scenarios, the CP-net formalism [6] is a convenient and expressive way to model preferences that has been used widely in the preference handling community [8,12,15,23]. CP-nets provide an effective, compact
