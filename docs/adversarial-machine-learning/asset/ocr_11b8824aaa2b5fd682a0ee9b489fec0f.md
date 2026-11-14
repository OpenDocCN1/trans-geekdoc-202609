messages with tokens drawn from a broad distribution, essentially including every token with equal probability. The focused attack focuses the distribution specifically on a single message or a narrow class of messages. If the attacker has the additional ability to send messages that will be trained as ham, a pseudospam attack can cause spam messages to reach the user's inbox.

# 5.3.1 Causative Availability Attacks

We first focus on Causative Availability attacks, which manipulate the filter's training data to increase the number of ham messages misclassified. We consider both Indiscriminate and Targeted attacks. In Indiscriminate attacks, too many false positives force the victim to disable the filter or frequently search in spam/unsure folders for legitimate messages that have been erroneously filtered away. Hence, the victim is forced to view more spam. In a Targeted attack, the attack is not designed to disable the filter, but instead it surreptitiously prevents the victim from receiving certain messages.

Without loss of generality, consider the construction of a single attack message A. The victim adds it to the training set, (re-)trains on the contaminated data, and subsequently uses the tainted model to classify a new message X̂. The attacker also has some (perhaps limited) knowledge of the next email the victim will receive. This knowledge can be represented as a distribution p—the vector of probabilities that each token will appear in the next message.

The goal of the attacker is to choose the tokens for the attack message a to maximize the expected spam score:

```
\max_{\mathbf{a}} E_{\mathbf{X} \sim p} [I_a (\hat{\mathbf{x}})] ; (5.7)
```

that is, the attack's goal is to maximize the expectation of I_a (x̂) (Equation (5.4) with the attack message a added to the spam training set of the next legitimate email x̂ drawn from distribution p. However, in analyzing this objective, it is shown in Appendix C.2 that the attacker can generally maximize the expected spam score of any future message by including all possible tokens (words, symbols, misspellings, etc.) in attack emails, causing SpamBayes to learn that all tokens are indicative of spam—we call this an Optimal attack. 2

To describe the optimal attack under this criterion, we make two observations, which we detail in Appendix C.2. First, for most tokens, I_a ( · ) is monotonically nondecreasing in q_i. Therefore, increasing the score of any token in the attack message will generally increase I_a (x̂). Second, the token scores of distinct tokens do not interact; that is, adding the i^th token to the attack does not change the score q_j of some different token j ≠ i. Hence, the attacker can simply choose which tokens will be most beneficial for its purpose. From this, we motivate two attacks, the dictionary and focused attacks, as instances of a common attack in which the attacker has different amounts of knowledge about the victim's email.

2 As discussed in Appendix C.2 these attacks are optimal for a relaxed version of the optimization problem. Generally, optimizing the problem given by Equation 5.7 requires exact knowledge about future messages x̂ and is a difficult combinatorial problem to solve.