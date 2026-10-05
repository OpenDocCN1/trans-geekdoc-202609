
# 274 Big data recommender systems, volume 1

## 12.3.5.2 l-Diversity

$l$-Diversity is a method that can lessen the risks in k-anonymity regarding the revelation of sensitive information [61]. It guarantees that the values of sensitive parameters are dissimilar in each equivalence class. $l$-diversity enhances the privacy preservation compared with $k$-anonymity and helps to mitigate the risks that may occur when using $k$-anonymity; it is still likely that an adversary infers sensitive information. This can happen if the distribution of a sensitive record in a cluster is very different from the distribution of identical attributes in that class.

Li *et al.* [70] showed possible attacks on $l$-diversity including skewness and attack intensity indicating that the $l$-diversity method cannot safeguard against these sorts of attacks. Table 12.6 shows that sensitive information needs to be “diverse” in $QI$ equivalence class. As each sensitive attribute (disease) is diverse within each quotient space, no individual may be reidentified.

Manavajhalala *et al.* [61] describes a variety of $l$-diversity techniques, including the following:

- 1. Distinct l-diversity: avoiding the occurrence of the most frequent value by 1/l in an equivalence class.
- 2. Entropy $l$-diversity: $\log(l)$ is the least acceptable entropy of the sensitive information distribution in each equivalence class.
- 3. Recursive $(c,l)$-diversity: the most common value does not appear regularly.

## 12.3.5.3 T-Closeness

In order to solve the problems of previous methods for preventing the privacy, Li *et al.* [64,70] proposed an intuitive preserving model named $t$-closeness. They indicate that the sensitive information distribution within each $QI$ compared with its distribution in the original dataset should be. They also proposed an $(n, t)$-closeness privacy method which is more flexible [64]. In this case, the method bounds the number of released sensitive attributes that an adversary or an observer can gain from the table.

> Table 12.6 An example of l-diversity table

| Nationality | Zip code | Disease |
|---|---|---|
| Asian | 878XX | Acne |
| Asian | 878XX | Flu |
| Asian | 878XX | Acne |
| Asian | 878XX | Shingles |
| Asian | 878XX | Flu |
| Asian | 878XX | Flu |
| American | 878XX | Flu |
| American | 878XX | Acne |
| American | 878XX | Flu |
| American | 878XX | Flu |
| American | 878XX | Acme |
| American | 878XX | Shingles |

## 12.3.5.4 Differential privacy

The concept of differential privacy was initially proposed by Dwork [71] which safeguards private distinguishable data at the strictest probable level. It addresses the situation when a reliable custodian desires to publish statistics over its data, devoid of disclosing information about a specific value itself. This is done by adding noise to a small sample of user usage pattern. Dwork defined differential privacy as “A randomized algorithm $M$ is $\epsilon$-differential private for all pairs of adjacent databases $x,y$, and for all sets $S \subseteq \text{Range}(M(x)) \cup \text{Range}(M(y))$”:

$Pr(M(x) \in S) \le e^{\epsilon} \cdot Pr(M(y) \in S)$

where the probabilities are over algorithm $M$, $e$ stands for and “..” indicates that the transformation is stable in at most $\epsilon$-times of the hamming distance between two datasets.

Table 12.7 summarizes the most common methods of preserving privacy for data publishing.

## Table 12.7 An overview of common privacy preserving techniques

| Presented model | Applied technique | Author(s) | Year |
|---|---|---|---|
| $k$-Minimal generalization | Domain generalization hierarchies of the QI | Samarati [72] | 2001 |
| Simple-anonymity model | Mapping information to no, $k$ or incorrect entries | Sweeney [63] | 2002 |
| Bottom-up generalization | Masking and hiding information instead of learn patterns | Wang et al. [73] | 2004 |
| Top-down specialization | Specifying the level of information in a top-down way the least privacy condition is disrupted | Fung et al. [74] | 2005 |
| Enhanced-anonymity model | Protecting both identifications and relationships to sensitive information in data | Wong et al. [75] | 2006 |
| $k$-Anonymity in classification issues | Suppression and progressive disclosure algorithm | Fung et al. [58] | 2007 |
| Differential privacy | Adding properly random noise in data | Dwork [71] | 2008 |
| $p$-Sensitive-anonymity privacy model | Modifying the initial $QI$ attributes values | Sun et al. [76] | 2008 |
| Enhanced $(L_{\alpha})$-diversity | Controlling the weight of sensitive information in a given quasi identifier cluster | Sun et al. [77] | 2011 |
| Slicing | Slicing the dataset in a vertical and horizontal manner | Li et al. [68] | 2012 |
| Concentrated differential privacy | Adding properly random noise in data | Dwork [78] | 2016 |

## 12.4. Privacy in recommender systems

## 276 Big data recommender systems, volume 1

## 12.5 Conclusion and future directions

The growing use of recommender systems in online social networks presents a privacy risk for many users. The risks can be considered from two perspectives: measuring user's information disclosure and techniques to preserve users. The general objective of the first perspective is to understand both dichotomous and polytous approaches and the differences between them. From the privacy-preservation perspective, the challenges in online social networks are to propose new methods in the near future that can deal with different data. Then, we discussed privacy-preservation models (anonymization techniques and encryption) for users.

## Table 12.8 An overview of common privacy techniques

| Applied technique | Author(s) | Year |
|---|---|---|
| Privacy-preserving models | Hofmann et al. | 2005 |
| Distributed aggregation | Shokri et al. | 2009 |
| Link analysis | Manavajala *et al.* | 2011 |
| Matrix factorization | Nikolaenko *et al.* | 2013 |
| Differential privacy | Casio et al. | 2015 |
| Homomorphic encryption | Badsha *et al.* | 2016 |

As users' participation in different types of online social and recommender systems is increasing rapidly, there is a need to propose novel privacy models that take into account. Another consideration is resource consumption. As providing privacy requires substantial computation, factors that impact computation time should be studied to identify whether mechanisms are required that are less intensive. Modeling attacks is another significant issue that should be taken into account. While different types of attacks occur on anonymized datasets, modeling attacks on datasets with complicated features should be a priority so that vulnerabilities can be uncovered. Finally, there is a need to propose novel methods to help organizations preserve the privacy of users while these organizations are storing, analyzing and mining individuals' data.

# References

- [1] Gross R, Acquisti A. Information revelation and privacy in online social networks. In: Proceedings of the 2005 ACM Workshop on Privacy in the Electronic Society. ACM; 2005, p. 71–80.
- [2] Azahmadadesh E, Aghashian T, Taheri HP, et al. An automated model to detect fake profiles and botnets in online social networks using steganography-technology. IOSR Journal of Computer Engineering (IOSR-JCE). 2015;17:65–77.
- [3] Eckmans AJ, Bye M, Erkin Z, et al. Privacy in Recommender Systems. In: Social Media Retrieval. Tween, NL: Springer; 2013, p. 263–281.
- [4] Backstrom L, Dwork C, Kleinberg J. Where art thou r3579x?: Anonymized social networks, hidden patterns, and structural steganography. In: Proceedings of the 16th International Conference on World Wide Web. ACM; 2007. p. 181–190.
