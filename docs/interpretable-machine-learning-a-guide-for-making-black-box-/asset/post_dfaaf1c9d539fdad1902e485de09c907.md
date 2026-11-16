
FIGURE 5.38: The anchors algorithm's components and their interrelations (simplified)

The approach is a seemingly perfect recipe for efficiently deriving statistically sound information about why any system classified an instance the way it did. It systematically experiments with the model's input and concludes by observing respective outputs. It relies on well established and researched Machine Learning methods (MABs) to reduce the number of calls made to the model. This, in turn, drastically reduces the algorithm's runtime.

## 5.8.2 Complexity and Runtime

Knowing the anchors approach's asymptotic runtime behavior helps to evaluate how well it is expected to perform on specific problems. Let (B) denote the beam width and (p) the number of all features. Then the anchors algorithm is subject to:

```
\mathcal{O}(B \cdot p^2 + p^2)
```

This boundary abstracts from problem-independent hyperparameters, such as the statistical confidence (\delta). Ignoring hyperparameters helps reduce the boundary's complexity (see original paper for more info). Since the MAB extracts the (B) best out of (B \cdot p) candidates in each round, most MABs and their runtimes multiply the (p^2) factor more than any other parameter.

It thus becomes apparent: the algorithm's efficiency decreases with feature abundant problems.

## 5.8.3 Tabular Data Example

Tabular data is structured data represented by tables, wherein columns embody features and rows instances. For instance, we use the bike rental data to demonstrate the anchors approach's potential to explain ML predictions for selected instances. For this, we turn the regression into a classification problem and train a random forest as our black-box model. It is to classify whether the number of rented bicycles lies above or below the trend line.

Before creating anchor explanations, one needs to define a perturbation function. An easy way to do so is to use an intuitive default perturbation space for tabular explanation cases which can be built by sampling from, e.g., the training data. When perturbing an instance, this default approach maintains the features' values that are subject to the anchors' predicates, while replacing the non-fixed features with values taken from another randomly sampled instance with a specified probability. This process yields new instances that are similar to the explained one but have adopted some values from other random instances. Thus, they resemble neighbors.

| Group | Label | Value | Annotation |
| :--- | :--- | :--- | :--- |
| 'below' cases | | 700 | |
| 'below' cases | | 106 | IN [7,14) = BAD |
| 'below' cases | | 40 | |
| 'above' cases | | 200 | IN >= |
| 'above' cases | | 610 | IN [21, |
| 'above' cases | | 475 | IN [14 |

**X-Axis:** Precision (0.0 - 0.9)
**Legend:** base, temp, weathersit

FIGURE 5.39: Anchors explaining six instances of the bike rental dataset. Each row represents one explanation or anchor, and each bar depicts the feature predicates contained by it. The x-axis displays a rule's precision, and a bar's thickness corresponds to its coverage. The 'base' rule contains no predicates. These anchors show that the model mainly considers the temperature for predictions.

The results are instinctively interpretable and show for each explained instance, which features are most important for the model's prediction. As the anchors only have a few predicates, they additionally have high coverage and hence apply to other cases. The rules shown above were generated with (\tau = 0.9). Thus, we ask for anchors whose evaluated perturbations faithfully support the label with an accuracy of at least (90\%). Also, discretization was used to increase the expressiveness and applicability of numerical features.

All of the previous rules were generated for instances where the model decides confidently based on a few features. However, other instances are not as distinctly classified by the model as more features are of importance. In such cases, anchors get more specific, comprise more features, and apply to fewer instances.

' above ' cases
452
= SUMMER
= 451
= MAR

' below ' cases
300
Precision
0.0 0.1 0.2 0.3 0.4 0.5 0.6 0.7 0.8 0.9
= 299 l
= 81.2917
= MISTY
= NO...
= 13.2...

| base | hum | temp |
| :--- | :--- | :--- |
| season | yr | windspeed |
| days_since_2011 | weekday | holiday |
| mnth | weathersit | |

FIGURE 5.40: Explaining instances near decision boundaries leads to specific rules comprising a higher number of feature predicates and lower coverage. Also, the empty rule, i.e., the base feature, gets less important. This can be interpreted as a signal for a decision boundary, as the instance is located in a volatile neighborhood.

While choosing the default perturbation space is a comfortable choice to make, it may have a great impact on the algorithm and can thus lead to biased results. For example, if the train set is unbalanced (there is an unequal number of instances of each class), the perturbation space is as well. This condition further affects the rule-finding and the result's precision.

The cervical cancer data set is an excellent example of this situation Applying the anchors algorithm leads to one of the following situations:

- Explaining instances labeled *healthy* yields empty rules as all generated neighbors evaluate to *healthy*.
- Explanations for instances labeled *cancer* are overly specific, i.e., comprise many feature predicates, since the perturbation space mostly covers values from *healthy* instances.

'Healthy' cases
1

'Cancer' cases
7

= 34 = 51 = 7 = 6 = 1 = 17

0.0 0.1 0.2 0.3 0.4 0.5 0.6 0.7 0.8 0.9

Precision

- base
- STDs..Time.since.first.diagnosis
- Smokes..years.
- Age
- IUD..years.
- Num.of.pregnancies
- IUD
- First.sexual.intercourse
- Hormonal.Contraceptives

FIGURE 5.41: Constructing anchors within unbalanced perturbation spaces leads to unexpressive results.

This outcome may be unwanted and can be approached in multiple ways. For example, a custom perturbation space can be defined that samples differently, e.g., from an unbalanced data set or a normal distribution. This, however, comes with a side-effect: the sampled neighbors are not representative and change the coverage's scope. Alternatively, we could modify the MAB's confidence (\delta) and error parameter values (\varepsilon). This would cause the MAB to draw more samples, ultimately leading to the minority being sampled more often in absolute terms.

For this example, we use a subset of the cervical cancer set in which the majority of cases are labeled cancer. We then have the framework to create a corresponding perturbation space from it. Perturbations are now more likely to lead to varying predictions, and the anchors algorithm can identify important features. However, one needs to take the coverage's definition into account: it is only defined within the perturbation space. In the previous examples, we used the train set as the perturbation space's basis. Since we only use a subset here, a high coverage does not necessarily indicate globally high rule importance.

![](img/9328bf422a53c0f374079f63527c081f_161_0.png)

FIGURE 5.42: Balancing the data set before constructing anchors shows the model's reasoning for decisions in minority cases.

## 5.8.4 Advantages

The anchors approach offers multiple advantages over LIME. First, the algorithm's output is easier to understand, as rules are easy to interpret (even for laypersons).

Furthermore, anchors are subsettable and even state a measure of importance by including the notion of coverage. Second, the anchors approach works when model predictions are non-linear or complex in an instance's neighborhood. As the approach deploys reinforcement learning techniques instead of fitting surrogate models, it is less likely to underfit the model.

Apart from that, the algorithm is model-agnostic and thus applicable to any model.

Furthermore, it is highly efficient as it can be parallelized by making use of MABs that support batch sampling (e.g., BatchSAR).

## 5.8.5 Disadvantages

The algorithm suffers from a highly configurable and impactful setup, just like most perturbation-based explainers. Not only do hyperparameters such as the beam width or precision threshold need to be tuned to yield meaningful results but also does the perturbation function need to be explicitly designed for one domain/use-case. Think of how tabular data gets perturbed and think of how to apply the same concepts to image data (Hint: these cannot be applied). Luckily, default approaches may be used in some domains (e.g., tabular), facilitating an initial explanation setup.

Also, many scenarios require discretization as otherwise results are too specific, have low coverage, and do not contribute to understanding the model. While discretization can help, it may also blur decision boundaries if used carelessly and thus have the exact opposite effect. Since there is no best discretization technique, users need to be aware of the data before deciding on how to discretize data not to obtain poor results.

Constructing anchors requires many calls to the ML model, just like all perturbation-based explainers. While the algorithm deploys MABs to minimize the number of calls, its runtime still very much depends on the model's performance and is therefore highly variable.

Lastly, the notion of coverage is undefined in some domains. For example, there is no obvious or universal definition of how superpixels in one image compare to such in other images.

## 5.8.6 Software and Alternatives

There currently are two implementations available: anchor, a Python package (also integrated by Alibi) and a Java implementation. The former is the anchors algorithm's authors' reference and the latter a high-performance implementation which comes with an R interface, called anchors, which was used for the examples in this chapter. As of now, anchors supports tabular data only. However, anchors may theoretically be constructed for any domain or type of data.

- 40. Marco Tulio Ribeiro, Sameer Singh, Carlos Guestrin. "Anchors: High-Precision Model-Agnostic Explanations." AAAI Conference on Artificial Intelligence (AAAI), 2018
- 41. Emilie Kaufmann and Shivaram Kalyanakrishnan. "Information Complexity in Bandit Subset Selection". Proceedings of Machine Learning Research (2013).
