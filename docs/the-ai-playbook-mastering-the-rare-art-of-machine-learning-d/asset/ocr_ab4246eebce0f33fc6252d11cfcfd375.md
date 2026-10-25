and how often it lets a fraudulent transaction slip by. Here's the breakdown:

+   Transactions blocked: 200,000 (two per 1,000)
+   Percentage blocked that are fraud: 30 percent
+   (Lift × overall fraud rate = 300 × 0.1 percent)
+   Fraudulent transactions blocked: 60,000 (30 percent × 200,000)
+   FPs—legitimate transactions blocked: 140,000 (200,000 – 60,000)
+   FNs—fraudulent transactions allowed: 40,000 (100,000 – 60,000)

This model is often wrong, but extremely valuable. When it blocks a transaction, it's usually wrong—only 30 percent of the blocked transactions are fraud. This isn't unusual. Since fraud is so infrequent, it would be very difficult to correctly detect some cases without also incorrectly flagging legit transactions even more often. With legitimate transactions—that is, negative cases—so prevalent, even misclassifying a small portion of them means a lot of FPs.

So the best we can hope for from a model is that it provides an advantageous trade-off between FPs (less costly) and FNs (more costly). To calculate the bottom line, we add up the costs. We've already established the cost for individual errors:

+   Cost of a FP: $100 (inconvenience to a customer)
+   Cost of a FN: $500 (fraudster gets away with it)

So we need only multiply these costs by how often they're incurred:

+   Aggregate FP cost: $14 million (140,000 at $100 each)
+   Aggregate FN cost: $20 million (40,000 at $500 each)
+   Total cost with fraud detection: $34 million

We've cut fraud losses by $30 million (from $50 million to $20 million), but introduced $14 million in new costs resulting from FPs. Clearly, this is a worthy trade-off.

Overall cost savings: $16 million ($50 million – $34 million)

If you would like to access a spreadsheet with these calculations and try out different scenarios—such as varying the model lift, the number of transactions held, or the cost of each FP and FN—see the notes for this chapter at www.bizML.com.