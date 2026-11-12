generalized approach, using the elbow method on the generated posterior probabilities, which is inspired by work on finding the reject threshold in pattern recognition [7].

The elbow method selects a probability threshold t by first ordering all examples based on their probability, in descending order. More formally, we use E to denote a set of examples, M to denote a probabilistic circuit, and p(e) to denote the probability of e ∈ E according to M. Let L = [e1, ..., en] be the examples in E, ordered according to probability p(e), such that e1 has the highest probability and en the lowest. The elbow method then finds threshold t by searching for a sudden sharper decrease in probability. I.e., find example ei such that

```
i = \arg \min_{x=1..|\mathcal{E}|} (x \mid \frac{p(e_{x+1}) - p(e_x)}{p(e_x) - p(e_{x-1})} \ge 0.3), (8)
```

after which the threshold is defined as t = p(ei). The value of 0.3 in the elbow method is a user-specified parameter. We decided this value by analysing the results of the music use case in collaboration with a music expert of Tunify. Since there is no expert for the open-source datasets, we reuse the same threshold t throughout the experiments (Fig. 6).

![](bbox=[0.3, 0.44, 0.65, 0.64])

**Fig. 6.** The elbow method selects threshold t, identifying high probability regions.

Using this threshold t, we determine the high probability region examples E_HPR ⊆ E. Afterwards, we apply PUTPUT to prune M, leading to the discriminative formula ψ.

# 6.2 Datasets

+   - Tunify provided real-world data, 360 000 songs, annotated with 14 categorical features having 7 to 120 possible values, and a set of intended playlist concepts. From this private data 15 classes where constructed, each representing a different playlist concept that has to be learned. We consider two types of concepts, based on the playlists used by customers from Tunify.