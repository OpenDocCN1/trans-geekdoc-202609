**Focused Attacks (Before RONI)**

| | ham | spam | unsure |
|---|---|---|---|
| 10% guessed | 78% | 0.0% | 22% |
| 30% guessed | 30% | 5.2% | 65% |
| 50% guessed | 5.8% | 23% | 71% |
| 90% guessed | 0.0% | 79% | 21% |
| 100% guessed | 0.0% | 86% | 14% |

**Focused Attacks (After RONI)**

| | ham | spam | unsure |
|---|---|---|---|
| 10% guessed | 79% | 2.7% | 21% |
| 30% guessed | 36% | 4.8% | 59% |
| 50% guessed | 19% | 20% | 61% |
| 90% guessed | 20% | 62% | 19% |
| 100% guessed | 21% | 66% | 13% |

Figure 5.10 The effectiveness of the RONI defense on focused attacks with 1% contamination of training inboxes of about 1,000 messages (50% spam) each. Left: The average effect of 35 focused attacks on their targets when the attacker correctly guesses 10, 30, 50, 90, and 100% of the target’s tokens. Right: The average effect of the focused attacks on their targets after application of RONI. By using RONI, more of the target messages are correctly classified as ham, but the focused attacks largely still succeed at misclassifying most targeted messages.

is likely due to the fact that with more correctly guessed tokens, the overlap with other messages increases sufficiently to trigger RONI more frequently. However, the attack is still successful in spite of the increased number of detections (see Figure 5.10).

# 5.6 Summary

Motivated by the taxonomy of attacks against learners, we designed real-world Causative attacks against SpamBayes’ learner and demonstrated the effectiveness of these attacks using realistic adversarial control over the training process of SpamBayes. Optimal attacks against SpamBayes caused unusually high false-positive rates using only a small amount of control of the training process (more than 95% misclassification of ham messages when only 1% of the training data is contaminated). Usenet dictionary attacks also effectively use a more realistically limited attack message to cause misclassification of 19% of ham messages with only 1% control over the training messages, rendering SpamBayes unusable in practice. We also show that an informed adversary can successfully target messages. The focused attack changes the classification of the target message virtually 100% of the time with knowledge of only 30% of the target’s tokens. Similarly, the pseudospam attack is able to cause nearly 90% of the target spam messages to be labeled as either unsure or ham with control of less than 10% of the training data.

To combat attacks against SpamBayes, we designed a data sanitization technique called the reject on negative impact (RONI) defense that expunges any message from the training set if it has an undue negative impact on a calibrated test filter. RONI is a successful mechanism that thwarts a broad range of dictionary attacks—or more generally Indiscriminate Causative Availability attacks. However, the RONI defense also has costs. First, this defense yields a slight decrease in ham classification (from 98% to 95%). Second, RONI requires a substantial amount of computation—testing each message in D(suspect) requires us to train and compare the performance of several classifiers. Finally, RONI may slow the learning process. For instance, when a user correctly labels