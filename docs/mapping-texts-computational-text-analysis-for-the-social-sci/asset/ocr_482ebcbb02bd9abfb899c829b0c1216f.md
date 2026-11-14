Figure 6.1: Visualizing Zipf's and Herdan-Heaps' Laws.

![](bbox=[0.33, 0.12, 0.91, 0.32])

![](bbox=[0.33, 0.33, 0.91, 0.53])

However, there is an established relationship between raw counts of types, on one hand, and the total number of tokens in a collection, on the other. The more total words, the more likely we encounter a new type of word—Herdan-Heaps' Law! Therefore, it is common practice to re-weight the DTM to shift the importance we place on different features of our DTM.

# Relative Term Frequency

The most common DTM weighting scheme is to norm the DTM by dividing these raw counts by the document lengths (i.e., the row sums of our matrix).27 This is extremely common and is often called relative frequency, or rf. To show how, we'll weight our DTM by each document's length. Let's use Europarl again, but this time only use the English sentences.

27 As term frequencies are necessarily vectors of positive integers, this is, in effect, the L1-norm (see Math Basics).