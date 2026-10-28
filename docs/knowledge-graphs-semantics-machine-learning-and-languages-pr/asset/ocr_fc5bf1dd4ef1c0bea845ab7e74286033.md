# **Table 4.** Results of the GERBIL QA evaluation performed on QALD-9-ES: a Spanish Dataset for Question Answering Systems over Wikidata. GERBIL performs four sub-experiments: Question Answering (QA), identification of relevant resources (C2KB), identification of relevant properties (P2KB), and matching of expected triples (RE2KB).

| Dataset | Sub-experiment | Micro F1 | Macro F1 |
|---|---|---:|---:|
| **QALD-9 test** | QA | 0.1077 | 0.1522 |
|  | C2KB | 0.3798 | 0.3408 |
|  | P2KB | 0.4183 | 0.4069 |
|  | RE2KB | 0.1141 | 0.1691 |
| **QALD-9 train** | QA | 0.1588 | 0.2486 |
|  | C2KB | 0.3682 | 0.3538 |
|  | P2KB | 0.4082 | 0.4106 |
|  | RE2KB | 0.1703 | 0.2276 |

# **Table 5.** Results of the GERBIL QA evaluation performed on QALD-9-ES using the QAnswer annotator over Wikidata. GERBIL performed four sub-experiments: Question Answering (QA), identification of relevant resources (C2KB), identification of relevant properties (P2KB), and matching of expected triples (RE2KB). We see improvements in most of the scores when using QALD-9-ES.

| Dataset | Sub-experiment | Micro F1 | Macro F1 |
|---|---|---:|---:|
| **QALD-9-ES test** | QA | 0.1142 | 0.1680 |
|  | C2KB | 0.3893 | 0.3593 |
|  | P2KB | 0.4093 | 0.3951 |
|  | RE2KB | 0.1236 | 0.1863 |
| **QALD-9-ES train** | QA | 0.1775 | 0.2639 |
|  | C2KB | 0.3623 | 0.3471 |
|  | P2KB | 0.3804 | 0.3887 |
|  | RE2KB | 0.1874 | 0.2419 |

The F1 score is the harmonic mean between the system’s precision and recall presented in Eq. (1). This metric is applied over one class; in this case, we have several classes; therefore, the micro and macro average aggregation methods are applied. Macro F1 is the unweighted mean of the F1 scores obtained per class presented in Eq. (2). The Micro F1 method calculates the F1 score using the normal F1 equation but using the total number of True Positive (TP), False Positive (FP), and False Negative (FN) values instead of the values of a single class and it is presented in Eq. (3). The main difference between the micro and macro metrics is that Micro F1 gives equal importance to each observation; consequently, some classes will significantly impact the results for imbalanced datasets. On the other hand, Macro F1 gives equal importance to the class F1 score, allowing it to return objective results even on imbalanced datasets.

$$F1 = \frac{TP}{TP + \frac{1}{2} \times (FP + FN)} \tag{1}$$

$$Macro\ F1 = \frac{\sum F1\ scores}{Number\ of\ classes} \tag{2}$$

$$Micro\ F1 = \frac{\sum TP}{\sum TP + \frac{1}{2} \times (\sum FP + \sum FN)} \tag{3}$$