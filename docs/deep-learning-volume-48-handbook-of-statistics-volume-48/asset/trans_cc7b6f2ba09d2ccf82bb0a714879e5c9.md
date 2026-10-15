
| AT \[PGD-5\] || 19.76 || 46.39 || 50.32 || 50.43 || 10.23 || 41.98 || 21.21 |

| OM-AT \[OM-FGSM\] || 11.12 || 13.82 || 34.07 || 1.50 || 0.26 || 2.27 || 8.59 |

| OM-AT \[OM-PGD-5\] || 22.39 || 28.38 || 48.74 || 5.19 || 0.49 || 5.92 || 14.67 |

| DMAT \[PGD-5, OM-PGD-5\] **(Ours)** || **31.78** || **51.19** || **56.09** || **51.61** || **14.31** || **51.36** || **29.68** |

####  3.2.6: TRADES for DMAT

The proposed DMAT framework is general and can be extended to other adversarial training approaches such as TRADES ([Zhang et al., 2019b](#Ch003_29-58_S0169716123000019.xhtml#bb0495)). TRADES is one of the state-of-the-art methods that achieves better trade-off between standard accuracy and robustness compared to standard AT ([5](#Ch003_29-58_S0169716123000019.xhtml#fo0030)). TRADES is integrated into DMAT by considering the following loss function:

``` 
$\\begin{array}{r} {\\min\\limits\\_{\\theta}\\sum\\limits_{i}\\mathcal{L}(f\\_{\\theta}(x_{i}),y_{true}) + \\beta\\max\\limits_{\\delta}\\mathcal{L}(f\\_{\\theta}(x_{i}),f\\_{\\theta}(x_{i} + \\delta)) + \\beta\\max\\limits_{\\lambda}\\mathcal{L}(f\\_{\\theta}(x_{i}),f\\_{\\theta}(g(w_{i} + \\lambda))),} \\\\ \\end{array}$
```

![si38_e](images/S0169716123000019/si38_e.png)  (9)

where *x*[*i*] = *g*(*w*[*i*]). The first two terms in ([9](#Ch003_29-58_S0169716123000019.xhtml#fo0050)) are the original TRADES in the image space, and the third term is the counterpart in the latent space. To solve for the two maximization problems in ([9](#Ch003_29-58_S0169716123000019.xhtml#fo0050)), PGD-5 and OM-PGD-5 with the same parameter settings are used. Results are presented in [Table 3](#Ch003_29-58_S0169716123000019.xhtml#t0020).

[Table 3](#Ch003_29-58_S0169716123000019.xhtml#B-t0020)

Classification accuracy against known (PGD-50 and OM-PGD-50) and unseen attacks applied to OM-ImageNet test set.

| Method || Standard || PGD-50 || OM-PGD-50 || Fog || Snow || Elastic || Gabor || JPEG || *L*[2] |

| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

| Normal training || 74.72 || 0.00 || 0.26 || 0.03 || 0.06 || 1.20 || 0.03 || 0.00 || 1.70 |

| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

| TRADES || 69.88 || **46.06** || 8.92 || 1.14 || **47.63** || 53.32 || **54.33** || 14.06 || 46.36 |

| DMAT + TRADES || 73.17 || 42.57 || **26.82** || **30.64** || 46.62 || **56.38** || 53.43 || **23.62** || **55.09** |

Even for TRADES, the benefit of using manifold information can also be observed.

##  4: Knowledge distillation-based defenses

Adversarial training ([Madry et al., 2017](#Ch003_29-58_S0169716123000019.xhtml#bb0255)) is considered to be one of the most effective algorithms for adversarial defenses. There have been many works for improving adversarial training by using different loss functions, such as ALP ([Kannan et al., 2018](#Ch003_29-58_S0169716123000019.xhtml#bb0180)), TRADES ([Zhang et al., 2019a](#Ch003_29-58_S0169716123000019.xhtml#bb0490)), and MART ([Wang et al., 2019](#Ch003_29-58_S0169716123000019.xhtml#bb0425)). However, they only train one model without considering the synergy of a network cohort. In addition, most defense methods focus on a single perturbation type, which can be vulnerable to unseen perturbation types ([Maini et al., 2020](#Ch003_29-58_S0169716123000019.xhtml#bb0260); [Tramèr and Boneh, 2019](#Ch003_29-58_S0169716123000019.xhtml#bb0385)). For example, models adversarially trained on *l*[*∞*]\-bounded adversarial examples make them vulnerable to *l*[1] and *l*[2]\-bounded attacks.

Knowledge distillation (KD) ([Hinton et al., 2015](#Ch003_29-58_S0169716123000019.xhtml#bb0155)) is a well-known method for transferring knowledge learned by one model to another. There are many forms of KD ([Wang and Yoon, 2020](#Ch003_29-58_S0169716123000019.xhtml#bb0415)) including *offline* KD, where the teacher models are pretrained and the students learns from static teachers ([Hinton et al., 2015](#Ch003_29-58_S0169716123000019.xhtml#bb0155)), and *online* KD, where a group of student models learn from peers’ predictions ([Guo et al., 2020](#Ch003_29-58_S0169716123000019.xhtml#bb0140); [Song and Chai, 2018](#Ch003_29-58_S0169716123000019.xhtml#bb0355); [Zhang et al., 2018b](#Ch003_29-58_S0169716123000019.xhtml#bb0485)). Several techniques based on KD have been proposed for adversarial defenses ([Arani et al., 2020](#Ch003_29-58_S0169716123000019.xhtml#bb0015); [Chen et al., 2021b](#Ch003_29-58_S0169716123000019.xhtml#bb0060); [Goldblum et al., 2019](#Ch003_29-58_S0169716123000019.xhtml#bb0125); [Liu et al., 2021a](#Ch003_29-58_S0169716123000019.xhtml#bb0245); [Papernot et al., 2016b](#Ch003_29-58_S0169716123000019.xhtml#bb0295)). [Goldblum et al. (2019)](#Ch003_29-58_S0169716123000019.xhtml#bb0125) demonstrate that robustness can be transferred among models through KD, and [Chen et al. (2021b)](#Ch003_29-58_S0169716123000019.xhtml#bb0060) show that KD can help mitigate robust overfitting.

[Table 4](#Ch003_29-58_S0169716123000019.xhtml#t0030) summarizes the differences among KD-based defenses. Defensive distillation (DD) trains a natural model, i.e., model trained with natural examples, with another natural model as the teacher, which cannot provide strong robustness as both the teacher and student are not adversarially trained; DD was broken by [Carlini and Wagner (2016)](#Ch003_29-58_S0169716123000019.xhtml#bb0025). Adversarially robust distillation (ARD) ([Goldblum et al., 2019](#Ch003_29-58_S0169716123000019.xhtml#bb0125)) trains a robust model, i.e., model trained with adversarial examples, with another robust model as the teacher to distill the robustness of a large network onto a smaller student. This strategy relies on the existence of strong teacher models, and the improvement of the student model is limited as the teacher is static. Adversarial concurrent training (ACT) ([Arani et al., 2020](#Ch003_29-58_S0169716123000019.xhtml#bb0015)) trains a natural model and a robust model jointly in an online KD manner to align the feature space of both. However, since natural and robust models learn fundamentally different features ([Tsipras et al., 2019](#Ch003_29-58_S0169716123000019.xhtml#bb0395)), aligning the feature space of a robust model with a natural model may result in degraded robustness.

[Table 4](#Ch003_29-58_S0169716123000019.xhtml#B-t0030)

Comparisons of KD-based defenses.

| Method || Teacher model || Student model || Form of KD || Multiperturbations |

| --- | --- | --- | --- | --- |

| DD ([Papernot et al., 2016b](#Ch003_29-58_S0169716123000019.xhtml#bb0295)) || Natural || Natural || Offline || × |

| --- | --- | --- | --- | --- |

| ARD ([Goldblum et al., 2019](#Ch003_29-58_S0169716123000019.xhtml#bb0125)) || Robust || Robust || Offline || × |

| ACT ([Arani et al., 2020](#Ch003_29-58_S0169716123000019.xhtml#bb0015)) || Natural || Robust || Online || × |

| MAT ([Liu et al., 2021a](#Ch003_29-58_S0169716123000019.xhtml#bb0245)) || Robust || Robust || Online || ✓ |

“Robust” means the model is trained with adversarial examples and “Natural” means the model is trained with natural examples.

[Liu et al. (2021a)](#Ch003_29-58_S0169716123000019.xhtml#bb0245) proposed MAT that allows models to share their knowledge of adversarial robustness and teach each other to be more robust. Unlike previous KD-based defenses, MAT trains a group of robust models simultaneously, and each network not only learns from ground-truth labels as in standard AT, but also the soft labels from peer networks that encode peers’ knowledge for defending adversarial attacks to achieve stronger robustness. The architecture of MAT is shown in [Fig. 5](#Ch003_29-58_S0169716123000019.xhtml#f0030).

![Fig. 5 Mutual adversarial training (MAT) architecture. x is a clean image, \\mathbf{x}\_{\\mathbf{adv}}^{\\mathbf{\\theta}\_{\\mathbf{1}}}si1\_e is the adversarial image of network h1, and xadvθ2 is the adversarial image of network h2.](images/S0169716123000019/f03-05-9780443184307.jpg)
