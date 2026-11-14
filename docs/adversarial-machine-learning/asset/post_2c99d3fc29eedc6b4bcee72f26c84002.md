

| Truth | ham | spam | unsure |
|---|---|---|---|
| ham | 97% | 0.0% | 2.5% |
| spam | 2.6% | 80% | 18% |

| Truth | ham | spam | unsure |
|---|---|---|---|
| ham | 95% | 0.3% | 4.6% |
| spam | 2.0% | 87% | 11% |

Figure 5.8 Effect of the RONI defense on the accuracy of SpamBayes in the absence of attacks. Each confusion matrix shows the breakdown of SpamBayes's predicted labels for both ham and spam messages. Left: The average performance of SpamBayes on training inboxes of about 1,000 messages (50% spam). Right: The average performance of SpamBayes after the training inbox is censored using RONI. On average, RONI removes 2.8% of ham and 3.1% of spam from the training sets. (Numbers may not add up to 100% because of rounding error.)

dictionary attack from any of the dictionaries (optimal, Aspell, and Usenet). In fact, the degree of change in misclassification rates for each dictionary message is greater than five standard deviations from the median, suggesting that these attacks are easily eliminated with only minor impact on the performance of the filter (see Figure 5.9).

A similar experiment with attack emails from the focused attack shows that the RONI defense is much less effective against focused attack messages. The likely explanation is simple: Indiscriminate dictionary attacks broadly affect many different messages with their wide scope of tokens, so its consequences are likely to be seen in the quiz sets. The focused attack is instead targeted at a single *future* email, which may not bear any significant similarity to the messages in the quiz sets. However, as the fraction of tokens correctly guessed by the attacker increases, the RONI defense identifies increasingly many attack messages: Only 7% are removed when the attacker guesses 10% of the tokens, but 25% of the attacks are removed when the attacker guesses 100% of the tokens.

| | ham | spam | unsure |
|---|---|---|---|
| Optimal | | | |
| True Label ham | 4.6% | 83% | 12% |
| True Label spam | 0.0% | 100% | 0.0% |
| Aspell | | | |
| True Label ham | 66% | 12% | 23% |
| True Label spam | 0.0% | 98% | 1.6% |
| Usenet | | | |
| True Label ham | 47% | 24% | 29% |
| True Label spam | 0.0% | 99% | 0.9% |

| | ham | spam | unsure |
|---|---|---|---|
| Optimal | | | |
| True Label ham | 95% | 0.3% | 4.6% |
| True Label spam | 2.0% | 87% | 11% |
| Aspell | | | |
| True Label ham | 95% | 0.3% | 4.6% |
| True Label spam | 2.0% | 87% | 11% |
| Usenet | | | |
| True Label ham | 95% | 0.3% | 4.6% |
| True Label spam | 2.0% | 87% | 11% |

Figure 5.9 We apply the RONI defense to dictionary attacks with 1% contamination of training inboxes of about 1,000 messages (50% spam) each. Left: The average effect of optimal, Usenet, and Aspell attacks on the SpamBayes filter's classification accuracy. The confusion matrix shows the breakdown of SpamBayes's predicted labels for both ham and spam messages after the filter is contaminated by each dictionary attack. Right: The average effect of the dictionary attacks on their targets after application of the RONI defense. By using RONI, all of these dictionary attacks are caught and removed from the training set, which dramatically improves the accuracy of the filter.

### Focused Attacks (Before RONI)

| | ham | spam | unsure |
|---|---|---|---|
| 10% guessed | 78% | 0.0% | 22% |
| 30% guessed | 30% | 5.2% | 65% |
| 50% guessed | 5.8% | 23% | 71% |
| 90% guessed | 0.0% | 79% | 21% |
| 100% guessed | 0.0% | 86% | 14% |

### Focused Attacks (After RONI)

| | ham | spam | unsure |
|---|---|---|---|
| 10% guessed | 79% | 2.7% | 21% |
| 30% guessed | 36% | 4.8% | 59% |
| 50% guessed | 19% | 20% | 61% |
| 90% guessed | 20% | 62% | 19% |
| 100% guessed | 21% | 66% | 13% |

Figure 5.10 The effectiveness of the RONI defense on focused attacks with 1% contamination of training inboxes of about 1,000 messages (50% spam) each. Left: The average effect of 35 focused attacks on their targets when the attacker correctly guesses 10, 30, 50, 90, and 100% of the target’s tokens. Right: The average effect of the focused attacks on their targets after application of RONI. By using RONI, more of the target messages are correctly classified as ham, but the focused attacks largely still succeed at misclassifying most targeted messages.

This is likely due to the fact that with more correctly guessed tokens, the overlap with other messages increases sufficiently to trigger RONI more frequently. However, the attack is still successful in spite of the increased number of detections (see Figure 5.10).

## 5.6 Summary

Motivated by the taxonomy of attacks against learners, we designed real-world Causative attacks against SpamBayes’ learner and demonstrated the effectiveness of these attacks using realistic adversarial control over the training process of SpamBayes. Optimal attacks against SpamBayes caused unusually high false-positive rates using only a small amount of control of the training process (more than 95% misclassification of ham messages when only 1% of the training data is contaminated). Usenet dictionary attacks also effectively use a more realistically limited attack message to cause misclassification of 19% of ham messages with only 1% control over the training messages, rendering SpamBayes unusable in practice. We also show that an informed adversary can successfully target messages. The focused attack changes the classification of the target message virtually 100% of the time with knowledge of only 30% of the target’s tokens. Similarly, the pseudospam attack is able to cause nearly 90% of the target spam messages to be labeled as either unsure or ham with control of less than 10% of the training data.

To combat attacks against SpamBayes, we designed a data sanitization technique called the reject on negative impact (RONI) defense that expunges any message from the training set if it has an undue negative impact on a calibrated test filter. RONI is a successful mechanism that thwarts a broad range of dictionary attacks—or more generally Indiscriminate Causative Availability attacks. However, the RONI defense also has costs. First, this defense yields a slight decrease in ham classification (from 98% to 95%). Second, RONI requires a substantial amount of computation—testing each message in D(suspect) requires us to train and compare the performance of several classifiers. Finally, RONI may slow the learning process. For instance, when a user correctly labels a new type of spam for training, RONI may reject those instances because the new spam may be very different from spam previously seen and more similar to some non-spam messages in the training set.

Date: Sat, 28 Oct 2006
Subj: favorites Opera

options building authors users. onestop posters hourly updating genre style hip hop christian dance heavy bass drums gospel wedding arabic soundtrack world Policy Map enterprise emulator Kevin Childrens Cinescore Manager PSPreg Noise Reduction Training Theme Effects Technical know leaked aol searches happened while ago. Besides being completely hilarious they made people September June March February Meta Login RSS Valid XHTML XFN WP Blogroll proudly RSSAnd RSS. LoveSoft Love Soft food flowers Weeks Feature Casual Elegance Coaching California Home

Date: Mon, 16 Jul 2007
Subj: commodious delouse corpsman

brocade crown bethought chimney. angelo asphyxiate brad abase decompression codecbreak. crankcase big conjuncture chit contention acorn cpa bladderwort chick. cinematic agleam chemisorb brothel choir conformance airfield.

Date: Thu, Apr 29, 2010
Subj: my deal much the

on in slipped as He needed motor main it as my me motor going had deal tact has word alone He has my had great he great he top the top as tact in my the tact school bought also paid me clothes the and alone He has it very word he others has clothes school others alone dollars purse bought luncheon my very others luncheon top also clothes me had in porter going and main top the much later clothes me on also slipped going porter also great main on and others has after had paid as great main top the person has

Date: Sun, 22 Jul 2007
Subj: bradshaw deride countryside

calvert dawson blockage card. coercion choreograph asparagine bonnet contrast bloop. coexistive bodybuild bastion chalkboard denominate claire churchgo compote act. childhood ardent brethren commercial complain concerto depressor

Figure 5.11 Real email messages that are suspiciously similar to dictionary or focused attacks. Messages (a), (b), and (c) all contain many unique rare words, and training on these messages would probably make these words into spam tokens. As with the other three emails, message (d) contains no spam payload, but has fewer rare words and more repeated words. Perhaps repetition of words is used to circumvent rules that filter messages with too many unique words (e.g., the UNIQUE_WORDS rule of Apache SpamAssassin (Apna n.d.)).

In presenting attacks against real-world token-based spam filtering, there is a danger that spammers may use these attacks against real-world spam filters. Indeed, there is strong evidence that some emails sent to our colleagues may be attacks on their filter. Examples of the contents of such messages are included in Figure 5.11 (all personal information in these messages has been removed to protect the privacy of the message recipients).

