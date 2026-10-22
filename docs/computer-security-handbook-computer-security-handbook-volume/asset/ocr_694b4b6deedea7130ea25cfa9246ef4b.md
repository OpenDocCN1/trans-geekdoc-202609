# 95 Percent Confidence Limits for Percentages

**95 Percent Confidence Limits for Percentages**

| Percentage | Sample size 100 | Sample size 500 | Sample size 1000 |
|---|---|---|---|
| 0 | 0-3.0% | 0-0.6% | 0-0.3% |
| 10 | 4.9-17.6% | 7.5-13.0% | 8.2-12.0% |
| 20 | 12.7-29.1% | 16.6-23.8% | 17.6-22.6% |
| 50 | 40.0-60.1% | 45.5-54.5% | 46.9-53.1% |
| 80 | 70.9-87.3% | 76.2-83.4% | 77.4-82.4% |
| 90 | 82.4-95.1% | 87.0-92.5% | 88.0-91.8% |
| 100 | 97.0-100% | 99.4-100% | 99.7-100% |

# 10.2.1.6 Contingency Tables.

One of the most frequent errors in reporting results of studies is to provide only part of the story. For example, one can read statements such as “Over 70 percent of the systems without firewalls were penetrated last year.” Such a statement may be true, but it cannot be interpreted correctly as meaning that systems with firewalls were necessarily more or less vulnerable to penetration than systems without firewalls. The statement is incomplete; to make sense of it, we need the other part of the implied contingency table—the percentage of systems with firewalls that were penetrated last year—before making any assertions about the relationship between firewalls and penetrations. Compare, for example, these two hypothetical tables:

| | Without Firewalls | With Firewalls in Default Configuration |
|---|---|---|
| Penetrated | 70% | 70% |
| Not Penetrated | 30% | 30% |

| | Without Firewalls | With Firewalls Properly Configured |
|---|---|---|
| Penetrated | 70% | 10% |
| Not Penetrated | 30% | 90% |

In both cases, someone could say that “70 percent of the systems without firewalls were penetrated,” but the implications would be radically different in the two data sets. Without knowing the right-hand column, the original assertion would be meaningless.

# 10.2.1.7 Association versus Causality.

Continuing our example with rates of penetration, another error that untrained people often make when studying statistical information is to mistake association for causality. Imagine that a study showed that a lower percentage of systems with fire extinguishers was penetrated than systems without fire extinguishers and that this difference was statistically highly significant. Would such a result necessarily mean that fire extinguishers caused the reduction in penetration? No. We know that it is far more reasonable to suppose that the fire extinguishers were installed in organizations whose security awareness and security policies were more highly developed than in the organizations where no fire extinguishers were installed. In this imaginary example, the fire extinguishers might actually have no causal effect whatever on resistance to penetration. This result would illustrate the effect of