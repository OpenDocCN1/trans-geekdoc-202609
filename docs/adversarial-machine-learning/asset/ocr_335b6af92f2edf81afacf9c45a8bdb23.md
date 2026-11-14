Control over data used for training opens up new strategies to the attacker. Cost is based on the interaction of _f_ and D<sup>(eval)</sup>. In the _Exploratory_ game the attacker chooses D<sup>(eval)</sup> while the defender controls _f_; in the _Causative_ game the attacker also has influence on _f_. With this influence, the attacker can proactively cause the learner to produce bad classifiers.

# _Contamination in PAC Learning_

Kearns & Li (1993) extend Valiant's _probably approximately correct_ (PAC) learning framework (cf. Valiant 1984, 1985) to prove bounds for maliciously chosen errors in the training data. In PAC learning, an algorithm succeeds if it can, with probability at least \(1 - \delta\), learn a hypothesis that has at most probability \(\epsilon\) of making an incorrect prediction on an example drawn from the same distribution. Kearns & Li examine the case where an attacker has arbitrary control over some fraction \(\beta\) of the training examples (this specifies the form that _A_<sup>(train)</sup> takes in our _Causative_ game). They prove that in general the attacker can prevent the learner from succeeding if \(\beta \ge \epsilon/(1 + \epsilon)\), and for some classes of learners they show this bound is tight.

This work provides important limits on the ability to succeed at PAC learning in a particular adversarial setting. The analysis broadly concerns both _Integrity_ and _Availability_ attacks as well as both _Targeted_ and _Indiscriminate_ variants. However, not all learning systems fall into the PAC learning model.

# 3.5.2 Causative Integrity Attacks

In these attacks, the adversary actively attempts to corrupt the learning mechanism so that miscreant activities can take place that would be otherwise disallowed. In a _Causative Integrity_ attack, the attacker uses control over training to cause intrusions to slip past the classifier as false negatives.

# EXAMPLE 3.3 (The Intrusion Foretold)

An attacker wants the defender’s IDS not to flag a novel virus. The defender trains periodically on network traffic, so the attacker sends non-intrusion traffic that is carefully chosen to look like the virus and mis-train the learner to fail to block it. This example would be _Targeted_ if the attacker already has a particular virus executable to send and needs to cause the learner to miss that particular instance. It would be _Indiscriminate_, on the other hand, if the attacker has a certain payload but could use any of a large number of existing exploit mechanisms to transmit the payload, in which case the attack need only fool the learner on any one of the malicious executables.

# _Red Herring Attack_

Newsome et al. (2006) present _Causative Integrity_ and _Causative Availability_ attacks against Polygraph (Newsome et al. 2005), a polymorphic-virus detector that learns virus signatures using both a conjunction learner and a naive-Bayes-like learner. Their _red herring_ attacks against conjunction learners exploit certain weaknesses not generally present in other learning algorithms. The attack introduces