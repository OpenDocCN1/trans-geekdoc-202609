
link PII in public IMDb profiles with anonymized users in the Netflix data, thereby re-identifying users in the competition dataset. The sexual orientation of one Netflix user became public. Netflix lost a class-action lawsuit launched as a result of the de-anonymization, with one stipulation being the cancellation of the sequel Netflix Prize II competition.

### 7.1.4 Deanonymizing Twitter Pseudonyms

A year after Narayanan & Shmatikov re-identified Netflix users, the same researchers demonstrated the inherent difficulty of anonymizing social network data (Narayanan & Shmatikov 2009).

Privacy is a serious concern in social networks. For example, Twitter played a crucial role in the Arab Spring uprising, with political dissidents taking to the online site to coordinate peaceful protest and document government abuses. Pseudonyms in online profiles promote anonymity, but are not foolproof. And while companies like Twitter may attempt to keep user privacy protected, they have competing drives for profit (sharing data with advertisers) and complying with legal warrants for information. Narayanan & Shmatikov showed that even in the absence of any profile information, network connections alone can identify many users. Linking nodes in the Twitter social graph with nodes in the Flickr photo-sharing website's social graph, they were able to re-identify a third of the users verified to have accounts on both Twitter and Flickr with 88% accuracy.

We have extended the approach, with Narayanan and Shi, to recover test labels in a social network link prediction challenge (Narayanan, Shi, & Rubinstein 2011): effectively a privacy attack applied to cheating at a machine learning competition. Where Narayanan & Shmatikov linked different graphs from two sites crawled at the same time, our result demonstrates that even over a six-month period graph evolution is insufficient to mitigate linkage attacks.

### 7.1.5 Genome-Wide Association Studies

Genome-wide Association Studies (GWAS) are an important statistical tool for analyzing medical assay data, in which the nucleotide frequencies at specific loci on the genome are compared between a control group of healthy subjects and a case group of individuals with a particular disease. Significant differences in occurrence frequencies imply an association between the disease and genetic markers. Homer et al. (2008) demonstrated the possibility of detecting whether a target individual participated in a GWAS case group—characterized as a mixture of participant genetic data—from the target DNA sequence information. This opened the possibility that participants of previously published GWAS data could be identified and led the National Institutes of Health to control the publication of study statistics.

Several other avenues exist for breaching “genetic privacy” (Erlich & Narayanan 2014) such as triangulating genealogical data to determine a study participant’s surname (Gymrek, McGuire, Golan, Halperin, & Erlich 2013).

### 7.1.6 Ad Microtargeting

Sharing personal data such as demographics and browsing history with online advertisers has long led to objections from privacy advocates. But what if no directly identifying information is shared with advertisers? What if no information is directly shared at all? Even in this seemingly innocuous setting, user privacy may be breached. Korolova (2011) showed that ad microtargeting on Facebook can be exploited to infer private information on users. The basic attack aims to infer some unknown private attribute (such as sexual orientation) of a selected target, for whom some identifying information is known already, such as age, location, workplace, or education. The attacker launches two ad campaigns on the social network, both targeting the fine details of the target user: one targeting users having the private attribute and the other targeting users without the attribute. Even though Facebook does not directly share the details of users viewing the ad, the attacker can determine this information depending on which ad campaign’s dollar balance changes. By examining the PII that is provided by Facebook, both campaigns can target the specific user, and an ad from exactly one of the two campaigns will be presented and be charged back to the attacker. This reveals which attribute value is possessed by the target user.

### 7.1.7 Lessons Learned

A number of patterns recur within the above case studies:

- It is dangerous to dismiss privacy breaches as trivially unlikely or requiring too much work on the part of the attacker. Time and time again, highly sophisticated attacks have been demonstrated. They were publicized to highlight misuses of sensitive data (due to initial data releases) and advance privacy research. In reality, much more valuable incentives exist to breach privacy without disclosure.

- Many breaches are accomplished via linkage attack: Records of an “anonymized” dataset are linked with an external data source that is easily obtained or even public. The combined data ties sensitive information (from the released private data) to re-identified individuals (from public records).

- It is exceedingly difficult to identify attributes that constitute PII, a necessary condition of employing syntactic measures such as k-anonymity and its derivatives. Many attributes can act like fingerprints: a curse of dimensionality exists in private data analysis in which high-dimensional data associated with individuals is likely to be unique.

## 7.2 Problem Setting: Privacy-Preserving Learning

Our goal in this chapter is to release aggregate information about a dataset while maintaining the privacy of each individual datum. These two goals of utility and privacy are inherently discordant. However, we will see that an effective balance can be achieved with practical release mechanisms.

For a release mechanism to be useful, its responses must closely resemble some target statistic of the data. In particular since we will be releasing classifiers learned on training data, our formal measure of utility will compare the released classifiers with a desired nonprivate classifier trained on the same data. In this case, our target classifier is the support vector machine (SVM), one of the most widely used supervised learners in practice.

Within the context of the previous section, any claim of data confidentiality must be backed up by a semantic guarantee of privacy: Time and time again weakly anonymized data has been re-identified. To this end, it is necessary for the mechanism's response to be “smoothed out”: the mechanism must be randomized to reduce any individual datum’s influence on this distribution. This is exactly the approach when establishing a property due to Dwork et al. (2006) known as differential privacy. We adopt this strong guarantee on privacy.

Those in the area of statistical databases, studied by the databases and theory communities, hope to understand when the goals of utility and privacy can be efficiently achieved simultaneously (Dinur & Nissim 2003; Barak et al. 2007; Blum et al. 2008; Chaudhuri & Monteleoni 2009; Kasiviswanathan et al. 2008; Duchi et al. 2013; Dwork & Roth 2014; Aldà & Rubinstein 2017). We will thus adopt their terminology while examining their approaches. While this chapter’s discussion involves theoretical analyses, the mechanisms presented here—developed in our past work (Rubinstein, Bartlett, Huang, & Taft 2009; Rubinstein et al. 2012)—are easily implemented and efficient, and release classifiers that are close to the corresponding nonprivate SVM under the \(\ell_\infty\)-norm, with high probability. In our setting this notion of utility is stronger than closeness of risk.

### 7.2.1 Differential Privacy

We now cover background on differential privacy. Given access to database \(\mathbb{D}\), a *mechanism* \(M\) must release aggregate information about \(\mathbb{D}\) while maintaining the privacy of individual entries. We assume that the *response* \(M(\mathbb{D})\), belonging to range space \(\mathcal{T}_M\), is the only information released by the mechanism. The statistical databases terminology we adopt should be understood to have analogs in machine learning, where for example database corresponds to dataset, record or item corresponds to datum, mechanism to learning algorithm, and the released quantity as the learned classifier.

We say that a pair of databases \(\mathbb{D}^{(1)}, \mathbb{D}^{(2)}\) are neighbors if they differ on exactly one entry; in other words the two datasets are separated by Hamming (or \(\ell_1\)) distance 1. We adopt the following strong notion of privacy due to Dwork et al. (2006).

DEFINITION 7.1 For any \(\beta > 0\), a randomized mechanism \(M\) provides \(\beta\)-*differential privacy*, if, for all neighboring databases \(\mathbb{D}^{(1)}, \mathbb{D}^{(2)}\) and all responses \(t \in \mathcal{T}_M\), the mechanism satisfies

```
\log \left( \frac{\Pr \left( M \left( \mathbb{D}^{(1)} \right) = t \right)}{\Pr \left( M \left( \mathbb{D}^{(2)} \right) = t \right)} \right) \le \beta.
```
