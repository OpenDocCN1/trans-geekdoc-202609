# Figure 10.6: 10-Topic Solution (first 4 topics).

![](bbox=[0.3, 0.12, 0.9, 0.32])

43 Specifically, weighting a term's topic-specific probability by some scalar (call it λ) and weight the topic-specific lift for that same term by the one minus that weight (1 − λ). We then add these two weighted values to get our term's relevance score.

(Sievert and Shirley 2014:65). It is the ratio of the term's probability in a topic to the term's probability across all the documents.

Lift can give terms that are idiosyncratic to specific documents. Luckily, term relevance means that we do not have to think about high probability and high lift separately from one another. With term relevance, Sievert and Shirley (Sievert and Shirley 2014:66) provide a way to blend the two metrics.43

Of course, we should also read the documents with high probabilities on these topics to ensure they engage the topics in ways we expect. If they do not, then we need to adjust our interpretations. Our document-topic probability matrix is stored in @gamma, which we can extract and then relabel the columns (topics) and rows (speeches).

```
df_doc_topics <- tidy(
  lda_sotu_10,
  matrix = "gamma",
  document_names = rownames(dtm_sotu_sub)
)
```

And now we can quickly visualize which speeches are engaging with which topics using a heatmap.

```
df_doc_topics |>
  mutate(topic = as.factor(topic)) |>
  ggplot(aes(topic, document, fill = gamma,
             label = round(gamma, 2))) +
  geom_tile(show.legend = FALSE, color = "white", alpha = 0.55) +
  geom_text() +
  labs(x = "Topics", y = "Speeches")
```

In contrast to clustering, here LDA is a fuzzy clustering method, which allows documents to be categorized gradationally. For instance, in Figure 10.7, Obama's 2012 speech mostly engages topic #7 and has some engagement with topic #4. We can also see that a speaker may