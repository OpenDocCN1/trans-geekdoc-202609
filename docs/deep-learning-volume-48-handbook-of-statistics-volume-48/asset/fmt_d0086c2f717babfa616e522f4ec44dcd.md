
As explained above, `context2vec` is trained as an unsupervised model which efficiently learns the context embedding of the wide sentential contexts. This uses bidirectional LSTM as the underlying model. The goal of the model is to learn a generic task-independent embedding for a target word, given sentence of any length. In a vanilla embedding CBOW architecture ([Mikolov et al., 2013b](#Ch002_9-27_S0169716122000591.xhtml#bb0140)), the naive context modeling is done by averaging word embedding in a fixed window. But in our model, we learn the context using a bidirectional LSTM, which is a much powerful neural network model. We follow the setup as mentioned by [Melamud et al. (2016)](#Ch002_9-27_S0169716122000591.xhtml#bb0130). To learn the parameter for the network, CBOW's negative sampling objective function is used. With this approach, both the context embedding network parameters and the target word embedding are learned.

For our implementation, we use the one-hot embedding as the input layer for all the terms. Then we have two fully connected LSTM layers followed by two linear layers (a.k.a. fully connected layer). We did the hyperparameter tuning for min word count, dropout, batch size to minimize the error. The final configuration used had output layer size of 300 and minimum frequency of 8 gave the best result. With mini-batch of 1000 sentences, the model training on a Nvidia GEForce RTX2080 took 36 h to train 5 iterations. As a next step, we should try to train the model on a more powerful GPU machine.

###  5.3: Quantitative evaluation

For the quantitative evaluation, we perform both the intrinsic and extrinsic evaluations. This section is divided into two based on subtasks: similarity measurement task and downstream application task.

####  5.3.1: Term similarity task

[Table 2](#Ch002_9-27_S0169716122000591.xhtml#t0015) presents the Spearman's (*ρ*) coefficient values obtained after applying the proposed model on the UMNSRS-Rel and UMNSRS-Sim datasets. The Spearman's (*ρ*) coefficient is calculated between the cosine similarity between the terms using the individual embeddings against the human judgments. As shown in [Table 2](#Ch002_9-27_S0169716122000591.xhtml#t0015), the proposed model (`Context2Vec + BioWordVec PCA—200`) outperforms existing techniques and achieves the highest correlation with human judgments on both the datasets. For comparison of our results with previous methods, we downloaded the ([Pyysalo et al., 2013](#Ch002_9-27_S0169716122000591.xhtml#bb0170)) word embedding model and executed it against all the term pairs. For BioWordVec ([Zhang et al., 2019](#Ch002_9-27_S0169716122000591.xhtml#bb0240)), we downloaded the published pretrained embedding. We report the [Mikolov et al. (2013a)](#Ch002_9-27_S0169716122000591.xhtml#bb0135) and [Chiu et al. (2016)](#Ch002_9-27_S0169716122000591.xhtml#bb0045) as mentioned in [Zhang et al. (2019)](#Ch002_9-27_S0169716122000591.xhtml#bb0240).

[Chiu et al. (2016)](#Ch002_9-27_S0169716122000591.xhtml#bb0045) show that the window size does not have a lot of impact on the intrinsic evaluation of word embedding ([Chiu et al., 2016](#Ch002_9-27_S0169716122000591.xhtml#bb0045)). Hence, increasing the window size of vanilla Word2Vec model would not be functionally equivalent to the contextual embedding model. We further do an experiment by combining our Context2vec model with [Pyysalo et al. (2013)](#Ch002_9-27_S0169716122000591.xhtml#bb0170) model. As we can see from [Table 3](#Ch002_9-27_S0169716122000591.xhtml#t0020) that the multiscale embedding performed a lot better than the individual models. Based on these, we can conclude that the proposed composite model is better at capturing the true intent than those that focus only one aspect. Context model can be easily plugged to any existing embedding model to make the individual model better.

[Table 3](#Ch002_9-27_S0169716122000591.xhtml#B-t0020)

 Evaluation results on UMNSRS Rel datasets. 

| Method  || Corpus || UMNSRS-Rel |

| --- | --- | --- |

| Pearson || Spearman || # |

| Mikolov et al. || Google news || 0.359 || 0.347 || 329 |

| --- | --- | --- | --- | --- |

| [Pyysalo et al. (2013)](#Ch002_9-27_S0169716122000591.xhtml#bb0170) || PubMed + PMC || 0.495 || 0.488 || 496 |

| Chiu et al. || PubMed || 0.600 || 0.601 || 467 |

| BioWordVec (win20) || PubMed + MeSH || 0.619 || 0.617 || **532** |

| Context2Vec || PubMed || 0.482 || 0.481 || 484 |

| Context2Vec + [Pyysalo et al. (2013)](#Ch002_9-27_S0169716122000591.xhtml#bb0170) || PubMed + MeSH || 0.524 || 0.524 || 484 |

| Context2Vec + BioWordVec Concat || PubMed + PMC || 0.565 || 0.561 || 484 |

| Context2Vec + BioWordVec PCA—200 || PubMed + MeSH || **0.647** || **0.642** || 484 |

“#” denotes the number of pairs for which the embedding was available. “Pearson” denotes the Pearson correlation score and “Spearman” denotes the Spearman correlation score. The highest values are shown in bold. The multiscale embedding performs better than the individual embedding.

####  5.3.2: Downstream application task

There are multiple applications where this embedding can be directly used. One of the common use cases of word embedding is to calculate the sentence pair similarity. The SemEval STS tasks have been organized for five years to evaluate the sentence similarity performance. One of the most common baselines used for this task is the averaged word embedding. We average the word vectors for each word in the sentence. Then cosine or euclidean similarity measure is used to calculate the similarity between the sentence pairs. We use this simple technique to prove how the embedding is performing on its own. [Table 4](#Ch002_9-27_S0169716122000591.xhtml#t0025) shows the Pearson correlation between calculated similarity (cosine or euclidean) and gold standard labels. The proposed composite embedding performs the best.

[Table 4](#Ch002_9-27_S0169716122000591.xhtml#B-t0025)

Sentence pair similarity result on BioCreative/OHNLP STS dataset ([Wang et al., 2018a](#Ch002_9-27_S0169716122000591.xhtml#bb0210)) and BIOSSES ([Soğancıoğlu et al., 2017](#Ch002_9-27_S0169716122000591.xhtml#bb0195)).

| Dataset || Similarity measures || Bio-WordVec ([Zhang et al., 2019](#Ch002_9-27_S0169716122000591.xhtml#bb0240)) || Composite embedding |

| --- | --- | --- | --- |

| BioCreative/OHNLP STS dataset ([Wang et al., 2018a](#Ch002_9-27_S0169716122000591.xhtml#bb0210)) || Cosine || 0.606 || **0.619** |

| BIOSSES ([Soğancıoğlu et al., 2017](#Ch002_9-27_S0169716122000591.xhtml#bb0195)) || Cosine || 0.476 || **0.497** |

Composite embedding refers to “Context2Vec + BioWordVec PCA—200” composite model. Pearson correlation between calculated similarity and gold standard labels.
