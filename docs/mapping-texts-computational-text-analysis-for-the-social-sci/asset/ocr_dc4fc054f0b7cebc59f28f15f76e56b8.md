author asked the kid where he would like to eat, he says “Five Guys” — a popular hamburger restaurant. The author’s sister stated they were “out of line to change his diet without their permission.” The scores were:

+   • 631: the sister is in the wrong.
+   • 276: the author is.
+   • 229: nobody is.
+   • 26: everyone is.
+   • 7: more information is needed.

So, the majority sided with the author that the “other” party is in the wrong. Let’s see how our model did.

```
df aita |> filter(title == "AITA for feeding my vegan nephew meat?") |> select(AUTHOR:INFO)
```

| AUTHOR | OTHER | NOBODY | EVERYBODY | INFO |
|---|---|---|---|---|
| 0.7772692 | 0.9145786 | 0.5613233 | 0.3398936 | 0.07852602 |

That tracks the vote tally pretty closely!

Suppose our research calls for sorting documents into multiple categories, and the methods discussed in **Core Deductive** are not producing desired results; then using pretrained embeddings with neural networks is a good choice. However, at least some documents must be labeled. What if we don’t have labeled data? We’ll discuss one classification strategy for unlabeled documents next.

# THIS SECTION NEEDS:

+   • tidyverse
+   • textclean
+   • text2map
+   • text2map.pretrained
+   • stringi
+   • gutenbergr

# Concept Mover’s Distance with Pretrained Embeddings

Recall that supervision means we’re using labels to train the classifier. They are not optional. A strength of dictionary methods is that they do not require labeling.

Could we augment dictionary methods with pretrained models? Specifically, could we use word embeddings to account for the semantic similarities between terms? Good news everybody! We can with **Concept Mover’s Distance** (CMD) (Stoltz and Taylor 2019a; Taylor and Stoltz 2021). This method extends dictionary methods as we’ll need one or more “anchor” terms. We’ll then use pretrained word embeddings to augment this process by weighting each word in our documents by its cosine to these anchors.21

> 21 To do this, CMD relies on Word Mover’s Distance; see Extended Inductive.

Our anchor list defines a location in the embedding space. In the simplest scenario, this is a single word—say “death.” We then associate each word in our DTM with a location in the embedding space. Documents,