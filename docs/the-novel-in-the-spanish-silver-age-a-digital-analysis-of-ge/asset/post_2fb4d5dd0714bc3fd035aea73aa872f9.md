
Figure 111: One-mode projection graph of subgenres

![](img/98c86d70e9e43286af05120dbff29113_389_0.png)

One-mode projection gives a very similar result with a strong negative correlation (r = -0.61 ***). Not only the eigenvector centrality, but also other basic operationalizations of centralities, such as degree, show very similar results in this case. Furthermore, the eigenvector centrality of the tripartite graph are very similar to the degrees and eigenvector values from the one-mode projection (with very strong correlations; for more details see the Jupyter Notebook).

These results are important because they support the interpretation of the centrality of the graph model. The central genres tend to obtain low classification results, while the peripheral ones are those with very high scores. In addition, the tripartite graph plots the major reason for the variance of results in the classification, as obtained in Chapter 7.2: the specificity of the features. The subgenres with high results in the classification tasks (the easy genres such as greguerias, dialogue, or the erotic novel, the ones that already yield perfect results with ten features, see Section 6.1.4) are peripheral in the graph because they have many distinctive features which pull them out. The subgenres with lower results (the difficult subgenres such as the educational and social novel) are more central because they share many features with the other categories.

Because the evaluation of the centrality is crucial, I run two further experiments trying to falsify it. First, I generate a statistical null-model of the graph using the same components, structure, and parameters. However, in this null-model, the weights of the edges are replaced with random values within the range of the graph analyzed up to this point. As expected, the centrality of the null-model does not correlate with the classification results.

In a further test, I analyze whether the composition of the corpus leads to these results. Perhaps the use of other texts could lead to opposite results. To test this, I sample the corpus 20 times, each time randomly selecting half of the texts in the CoNSSA. With each sample, the same correlation between the centrality and the classification results is. The results of the various samples show strong correlations (Pearson's r between -0.62 and -0.7, p-value < 0.001) to the above reported r -0.65.

In any case, for now this sampling process is being run with the texts of the same corpus. It is necessary to test this on other corpora and languages. This question leads to a general problem in the DH: the lack of standard corpora with rich metadata published without restrictions to which different algorithms and models can be applied. In a recent paper I have applied the tripartite graph model to other well-known corpora with information (Calvo Tello 2020): on the one side, to classical French drama; on the other side, to texts of the Bible as letters, gospel, and prophetic and historical texts. The correlations between the centrality and the classification are similar to the ones reported for the Spanish literature of the period analyzed here.

The positive results of the different tests allow for the use of concepts such as central and peripheral for genre categories in an innovative and very specific way. This is not limited to the genres. As observed in Section 7.2.5, there is a moderate correlation between the genre and the results in the classification. This suggests the hypothesis that the position on the graph does not only a meaning for the categories, but also for the texts. More canonical texts should be in the center, popular genres that are difficult to classify. To evaluate this, I run a correlation between the canonicity (in pages of the MdLE) and its eigenvector centrality, which results in a strong positive correlation (r=0.74***), i.e. the more important to literary history a text is, the more central it is in the graph.

These correlations are strong, but not very, nor perfect. Some exceptional subgenres, such as the bucolic genre, are very well classified. Based on this, this category should be peripheral in the network, yet it is rarer central. Likewise, the spiritual novels are in the periphery of the network, but are considered one of the hardest subgenres to classify. For this reason, the actual data of canonic and classification genres are used as the size of the textual and genre nodes in Figure 108. This means that the size and the positions are to a certain extent redundant. The sizes of the difficult subgenres in the center to be small due to their FI-scores while the sizes of canonical texts in the center are greater. The position and size correct the exact results. Although the centrality of the bucolic subgenre gives us to understand that its classification should be low, the size of the node corrects that.

## 8.5.2 Evaluation of Distance

An important aspect that can be evaluated is whether the similarity of two genres is represented through their distance on the graph. Are similar genres closer on the visualization of the graph? As in the case for centrality, there are several ways to formalize the distance between nodes in a network. One of the most intuitive and basic ways is to simply count the number of common neighbors, number of shared nodes. In my case, this translates to the intuitive idea of how many features and texts two genres share.

To formally evaluate this, it would be necessary to possess information about the perceived similarity between genres from annotators, literary scholars, or institutions. Sadly, I was not able to find such information, and the process of annotating such abstract information was not feasible.

Rather, I have observed some subgenres that are traditionally treated by literary scholars (as described in Chapter 2.1), such as the realist and naturalist novel; the historical novel, adventure novel and war novel; or autobiographies, memoirs, and educational novels. In addition, the hypothetical subgenres obtained by the clustering analysis in Chapter 6.2 are compared to the subgenres that overlapped to a greater extent (see Section 6.2.5): on the one side are the mono-dialogue and dialogue novels, and on the other bucolic and modernist novels.

When observing the common neighbors, all subgenres are indeed among the five closest categories to the others. In many cases, they are the closest, and if not, then prototypical subgenres occupy the first position, but they are clearly similar. For example, the naturalist novel is the third category with the larger number of common neighbors (shared features and texts) with the realistic novel. Ahead of this, is the social novel and literary fiction, which are arguably very similar to the realistic novel.

Although a more formal evaluation could be possible, the relations do not satisfy the hypothesis, and the distance (formalized as the number of common neighbors, shared texts and features) can be interpreted as similarity across subgenres has not been properly formalized in computational works until now due to the flat macro-model that the labels are transformed into multi-label tasks (see Sections 2.3.3.2 and 7.1.3). However, this model offers a way of measuring it as a proportion, and allows the identification of the exact features and texts that are shared (or not) by each pair of genres.

## 8.5.3 Summary of Evaluation and Interpretation

In concluding the evaluation, it has been shown that there are four aspects that can be interpreted from the model:

- Central genres (measured through the eigenvector centrality) achieve low classification results in contrast to the peripheral genres.
- Central texts are more canonical in contrast to the peripheral texts.
- As a consequence, central genres are more canonical, with less canonical categories in the periphery.
- The distance between genres (measured through common neighbors, shared nodes) corresponds to a similarity between genres.

## 8.6 Further Properties of the Tripartite Graph Model

I have already used two mathematical properties of the graphs to evaluate the model for genres: the centrality and the common neighbors of the nodes. But there are at least two further possibilities.

The first is that the tripartite graph model is able to accommodate cases of texts without being assigned to any analyzed subgenre – genreless texts in
