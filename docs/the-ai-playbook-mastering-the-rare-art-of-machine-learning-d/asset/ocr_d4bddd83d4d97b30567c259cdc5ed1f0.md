down how often it's wrong for positive cases and how often it's wrong for negative cases. Accuracy doesn't do that (nor does the pairing test).

That's what FNs and FPs are for. A FP is when the model says “positive” but is wrong. It's a negative case that's been wrongly flagged by the model as positive. This is also called a *false alarm*. The story about the boy who cried wolf is about him intentionally generating false positives. A FN is when the model wrongly says “negative.” It has overlooked a positive case.

# Calculating Savings Based on Misclassification Costs

So how do we assign a cost to each of these kinds of misclassification? That comes down to how much each kind of error matters. For almost all projects, it matters a different amount for a FP versus a FN.

Take fraud detection. When your bank's model wrongly blocks your legitimate credit card transaction as if it were fraudulent, you're inconvenienced. That's a FP. This could cost the bank $100 on average, given that you may turn to another card in your wallet—not only for the current purchase, but in general.

The other kind of error is worse. When the bank's model wrongly allows a fraudulent credit card charge to go through, that could cost the bank $500 on average, as the criminal gets away with the contraband. That's a FN.

These costs are no small deal. Global payment card fraud losses have surpassed $28 billion annually. The cardholder or an eagle-eyed auditor may notice the bogus charge later, but for card purchases, if it isn't caught by a model on the fly, it's in the wind. In the United States, the bank is usually liable for this loss.

By determining the two misclassification costs, we establish a cost-benefit analysis not only for the entire project but for each individual decision about whether to hold or authorize a transaction. Next, we'll add those individual costs up to calculate a KPI for the overall project: *cost savings*.