
### 4.5.4.1 Histogram Loss and Masking Task

(4.41) 
$$
\mathcal{l}_{h}\left( {s^{+},s^{-}} \right) = \frac{1}{m^{2}}\sum\limits_{r = 1}^{R}\sum\limits_{r^{\prime} = 1}^{r}\left( {\sum\limits_{i = 1}^{m}\delta_{r}\left\lbrack s_{i}^{-} \right\rbrack} \right)\left( {\sum\limits_{i = 1}^{m}\delta_{r^{\prime}}\left\lbrack s_{i}^{+} \right\rbrack} \right)
$$

where instead of hard assignments, we use the triangular kernel

$$
\delta_{r}\lbrack s\rbrack = \left\{ \begin{array}{l} {\left( {s - t_{r - 1}} \right)/\text{Δ if }s \in \left\lbrack {t_{r - 1},t_{r}} \right\rbrack} \\ {\left( {t_{r - 1} - s} \right)/\text{Δ if }s \in \left\lbrack {t_{r},t_{r + 1}} \right\rbrack} \\ {0\text{ otherwise}} \\ \end{array} \right.
$$

to put similarities into bins. This way we obtain a differentiable loss function. We hope that histogram loss is more robust with regard to the massive noise in our labels as each positive example is contrasted with all negative examples.

#### Masking Task

We propose extending the contextual similarity task by another task and optimizing the sum of both tasks for training our embedding models. The main idea of our second task is that the symbols in mathematical expressions do not appear independent from each other, but have strong dependencies. Thus if we hide a fraction of the symbols in an equation, we should be able to approximately reconstruct the hidden symbols from the remaining symbols. This task is reminiscent of masked language modeling tasks made popular by BERT [173] for natural language processing. In order to successfully solve this task, a model has to learn about the frequencies of symbols and their dependencies from the data, as is illustrated in Figure 4.24.

![Fig. 4.24 Example of the masking task with fictional values.](graphic/b_9783110785944-004_fig_024.png)

**Fig. 4.24** Example of the masking task with fictional values.

More formally, we proceed as follows. For each input graph `x` with features `X`, we randomly set the feature vector of 15% of the nodes to all zero obtaining the graph `x[■]`. Then we compute `ϕ(x[■]) ∈ ℝ^(|x|)×512`. Now for each masked node, we solve a classification task: given `ϕ[i](x[■])`, predict the right token, i.e. the combination of XML-tag, XML-attributes, and character. This classification task is solved using a single linear layer of dimensionality 256 with softmax-activation and cross-entropy-loss.

```
𝓁[i] = 𝓁(softmax(W)ϕ[i](x[◼])+b, X[i])
```

The loss is only evaluated for the masked tokens and we compute the mean over all masked tokens to obtain a loss value for `x[■]`.

Adding this task to the contextual similarity task has the additional advantage that we now learn a representation that not only captures context information, but also preserves information about the raw input symbols.

#### 4.5.4.2 Data Augmentation

Data augmentation eases the generalization of machine learning models and is particularly popular for image classification tasks where we can augment images by randomly rotating, scaling, padding, etc. For mathematical expressions, we propose the following random data augmentation. Since we know that a renaming of symbols in equations rarely changes the semantic, we propose randomly permuting the character features of all nodes that correspond to a math identifier, encoded in `<mi>` tags according to the MathML standard. For each equation we process, we sample a number of flips from a Poisson distribution with an expected value of 32. Then starting with the identity permutation that does not change the order of our 192 features, we construct a permutation with the desired number of flips by incrementally exchanging two random characters.

### 4.5.5 Experimental Results

In this section we perform an experimental evaluation of our embedding model. In particular, we focus on the use-case of a search engine for mathematical expressions. We begin by investigating the effects of the individual components of our model on a small, closed subset of the data. Then we investigate the effectiveness of our method on all 29.9 million equations.

#### 4.5.5.1 Analysis on the Machine Learning Subset

We begin our analysis only on arXiv publications where the primary subject classification is machine learning (cs.LG). This is a natural choice, as we have some expertise to judge the quality of our results, a task which we are in no way equipped for across all subject fields.

Of these 9936 publications, we sample two subsets, train and test sizes of 7949 and 1987, respectively, and a total number of equations of 237,335 and 54,767, respectively. We use the train-set for building our embedding models and use the test-set to investigate generalization properties.

For training, we sample 1 million triplets (`x`, `x⁺`, `x⁻`). Of these triples, 45.9% have a positive pair from the same section, 42.2% from the same paper, and 13.9% along an edge in the citation graph. We sample 100k triplets for testing with similarly distributed positive examples.

We perform an ablation study on our proposed embedding model and compare it with prior work. This section investigates the influence of our design choices. We decided (a) to use the histogram loss instead of the triplet loss, and (b) to add a masking task, (c) to data augmentation.

We measure the ranking score, i.e. the fraction of all triples in the training data where same-class pairs of equations have higher similarities than across-class pairs. As we see in Table 4.6, our evaluations indicate that all of our design choices contribute favorably to the overall performance on hold-out data, as deactivating any component decreases the score. We note that the biggest gain is achieved by switching from triplet-loss to histogram-loss. We believe that this is due to the massive noise in our labels.

We also compare with our previous model [564] and see that we beat it by a small margin. However, this comparison is not entirely fair, as their model was trained on a larger dataset of around 25,000 papers, probably including some of the papers in our test set. We use their code to re-train on our subset of equations and yield a substantial margin of 6.5 percentage points.

**Tab. 4.6** Ablation Study.

| Influence factor | Ranking hold-out | Ranking eval | Accuracy eval |
| :--- | :--- | :--- | :--- |
| Full model | 76.5 (±0.0) | 57.7 (±0.0) | 60.6 (±0.0) |
| No histogram loss | 72.5 (−4.0) | 49.6 (−8.1) | 30.9 (−29.7) |
| No masking | 75.2 (−1.3) | 54.3 (−3.4) | 50.0 (−10.6) |
| No augmentation | 75.3 (−1.2) | 53.6 (−4.1) | 50.0 (−10.6) |
| Bitmap CNN original [564] | 76.2 (−0.3) | 71.9 (+14.2) | 68.3 (+7.7) |
| Bitmap CNN retrained | 70.0 (−6.5) | 50.0 (−7.7) | 52.9 (−7.7) |
