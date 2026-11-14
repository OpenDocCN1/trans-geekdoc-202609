
The first axis describes the capability of the attacker: whether (a) the attacker has the ability to influence the training data that is used to construct the classifier (a *Causative* attack) or (b) the attacker does not influence the learned classifier, but can send new instances to the classifier and possibly observe its decisions on these carefully crafted instances (an *Exploratory* attack).

The second axis indicates the type of security violation the attacker causes: either (a) allowing harmful instances to slip through the filter as false negatives (an *Integrity* violation); (b) creating a denial-of-service event in which benign instances are incorrectly filtered as false positives (an *Availability* violation); or (c) using the filter's responses to infer confidential information used in the learning process (a *Privacy* violation).

The third axis refers to how specific the attacker's intention is: whether (a) the attack is highly *Targeted* to degrade the classifier's performance on one particular instance or to violate the privacy of one particular training instance or (b) the attack aims to cause the classifier to fail in an *Indiscriminate* fashion on a broad class of attacks. Each axis, especially this one, can actually be a spectrum of choices, but for simplicity, we will categorize attacks and defenses into these groupings.

These axes define the space of attacks against learners and aid in identifying unconventional threats. By qualifying where an attack lies in this space, one can begin to quantify the adversary's capabilities and assess the risk posed by this threat. Laskov & Kloft (2009) have since extended these basic principles to propose a framework for quantitatively evaluating security threats.

In Table 3.1, we use our taxonomy to classify past work on adversarial learning with goals relating to misclassifications—*Integrity* and *Availability* attacks, but not *Privacy* attacks. As we discuss in Section 3.7 while the taxonomy provides a useful classification of possible privacy attacks on machine learning systems, past work (with a few exceptions) tends to fall in most bins simultaneously.

### Table 3.1 Selected related work on misclassification attacks in the taxonomy

| | Integrity | Availability |
|---|---|---|
| Causative: Targeted | Kearns & Li (1993); Newsome et al. (2006) | Kearns & Li (1993); Newsome et al. (2006); Chung & Mok (2007); Nelson, Barreno, Chi, Joseph, Rubinstein, Saini, Sutton, Tygar, & Xia (2008) |
| Indiscriminate | Kearns & Li (1993); Newsome et al. (2006) | Kearns & Li (1993); Newsome et al. (2006); Chung & Mok (2007); Nelson et al. (2008) |
| Exploratory: Targeted | Tan et al. (2002); Lowd & Meek (2005a, 2005b); Wittel & Wu (2004) | Moore, Shannon, Brown, Voelker, & Savage (2006) |
| Indiscriminate | Fogla & Lee (2006); Lowd & Meek (2005b); Wittel & Wu (2004) | Moore et al. (2006) |

## 3.3.2 The Adversarial Learning Game

We model the task of constructing a secure learning system as a game between an attacker and a defender—the attacker manipulates data to mistrain or evade or violate privacy of a learning algorithm chosen by the defender to thwart the attacker's objective. The characteristics specified by the taxonomy's axes also designate some aspects of this game. The INFLUENCE axis determines the structure of the game and the legal moves that each player can make. The SPECIFICITY and SECURITY VIOLATION axes of the taxonomy determine the general shape of the cost function: an Integrity attack benefits the attacker on false negatives, and therefore focuses high cost (to the defender) on false negatives; an Availability attack focuses high cost on false positives; and a Privacy attack focuses high cost on leaking information about training instances. Similarly a Targeted attack focuses high cost only on a small number of specific instances, while an Indiscriminate attack spreads high cost over a broad range of instances.

We formalize the game as a series of moves, or steps. Each move either is a strategic choice by one of the players or is a neutral move not controlled by either player. The choices and computations in a move depend on information produced by previous moves (when a game is repeated, this includes previous iterations) and on domain-dependent constraints that we highlight in discussing prior work. Generally, though, in an Exploratory attack, the attacker chooses a procedure A^(eval) that affects the evaluation data D^(eval), and in a Causative attack, the attacker also chooses a procedure A^(train) to manipulate the training data D^(train). In either setting, the defender chooses a learning algorithm H^(N). This formulation gives us a theoretical basis for analyzing the interactions between attacker and defender.

## 3.3.3 Characteristics of Adversarial Capabilities

In this section we introduce three essential properties for constructing a model of an attack against a learning algorithm that refine the game played between the learner and the adversary as described by the taxonomy. These properties define a set of common domain-specific adversarial limitations that allow a security analyst to formally describe the capabilities of the adversary.

### 3.3.3.1 Corruption Models

The most important aspect of the adversary is how it can alter data to mislead or evade the classifier, or reveal information about the training data. As previously stated, learning against an unlimited adversary is futile. Instead, the security analysis we propose focuses on a limited adversary, but to do so, one must model the restrictions on the adversary and justify these restrictions for a particular domain. We outline two common models for adversarial corruption, and we describe how the adversary is limited within each.

### Data Insertion Model

The first model assumes the adversary has unlimited control of a small fraction of the data; i.e., the adversary is restricted to only modifying a limited amount of data, but can alter those data points arbitrarily. We call this an insertion model because, in this scenario, the adversary crafts a small number of attack instances and inserts them into the dataset for training or evaluation (or perhaps replaces existing data points). For example, in the case of a spam filter, the adversary (spammer) can create any arbitrary message for their attack, but it is limited in the number of attack messages it can inject: the spammer does not have control over innocuous email messages sent by third parties. The spammer's attack on the spam filter can be analyzed in terms of how many messages are required for the attack to be effective. For this reason, we use this model of corruption in analyzing attacks on the SpamBayes spam filter in Chapter 5 and show that, even with a relatively small number of attack messages, the adversarial spammer can significantly mislead the filter.

### Data Alteration Model

The second corruption model instead assumes that the adversary can alter any (or all) of the data points in the dataset, but is limited in the degree of alteration; i.e., an alteration model. For example, to attack a detector that is monitoring network traffic volumes over windows of time, the adversary can add or remove traffic within the network, but only can make a limited degree of alteration. Such an adversary cannot insert new data since each data point corresponds to a time slice and the adversary cannot arbitrarily control any single data point because other actors are also creating traffic in the network. Here the adversary is restricted by the total amount it can alter, and so the effectiveness of its attack can be analyzed in terms of the size of alteration required to achieve the attacker's objective. This is the model we use for analyzing attacks on a PCA-subspace detector for network anomaly detection in Chapter 6, and again we show that, with a relatively small degree of control, the adversary can dramatically degrade the effectiveness of this detector using data alterations.

### 3.3.3.2 Class Limitations

A second limitation on attackers involves which parts of the data the adversary is allowed to alter—the positive (malicious) class, the negative (benign) class, or both. Usually in settings where the adversary aims to affect misclassifications, attackers external to the system are only able to create malicious data and so they are limited to only manipulating positive instances. This is the model we use throughout this text. However, there is also an alternative threat that insiders could attack a learning system by altering negative instances. We do not analyze this threat in this book but return to the issue in the discussion in Chapter 9. In the setting of Privacy attacks, the learner may not necessarily be classifying instances as malicious or benign so there may not be any natural class limitation on the attacker's influence.
