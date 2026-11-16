![](bbox=[0.18, 0.07, 0.79, 0.21])

# Figure 1. Comparison of model indicator.

# Table 3. Examples of unrelated comments.

| Comment User ID | Comments | Describe |
|---|---|---|
| 6094950087 | What do these slanderers think? | Not expressing views on fake news, It’s just a critique of those who spread rumors |
| 3896912225 | Israel may already be on the way | Mentioned not related to current fake news |
| 5133431256 | An Iraqi in China is talking about IraqLack | Mentions, not current fake cancellations news, but other fake news |

is model training. Based on the corpus and the pre-trained word2vec model, SnowNLP Bayesian classifier, SVM and LSTM are used to train the sentiment binary classification model. The index comparison of the training model is shown in Figure 1.

Before the official analysis of Weibo comments, since Weibo comments contain content that is not very relevant to the original Weibo content, it is necessary to clean up the comments that are not related to Weibo content and then conduct sentiment analysis (Yanagi et al. 2020). One thousand medical teams were dispatched to some irrelevant comments under Weibo of “Wuhan” Examples of unrelated comments are shown in Table 3.

Use word2vec to generate word vectors because compared with the classic vector space model, word2vec considers the semantic information of the context and maps high-dimensional information to low-dimensional details to solve the dimensional disaster problem (Kumar, Jagota and Shabaz 2021). The steps are as follows. 1) Corpus processing and word2vec model training: Perform data preprocessing on the obtained epidemic comment data set; 2) Text vector construction: Use the open-source python library Jieba to segment the text and weight the word vector to obtain the text vector v(d).

```
v(d) = \frac{v(t_1)w_1 + v(t_2)w_2 + v(t_3)w_3 + \cdots + v(t_n)w_n}{w_1 + w_2 + w_3 + \cdots + w_n}
```

In the formula: \(t_i\) represents the word, \(w_i\) is the corresponding weight of the word, \(\mathbf{v}(t_i)\) is the word vector of \(t_i\).

3) Similarity calculation: use cosine distance to calculate between vectors’ similarity of:

```
sim(d_i, d_j) = \frac{\sum_{k=1}^n x_{ki}x_{kj}}{\sqrt{\sum_{k=1}^n x_{ki}^2} \sqrt{\sum_{k=1}^n x_{kj}^2}}
```

Where: \(\chi_{ki}\) is a text vector \(\mathbf{v}(d_i)\) Bk dimension corresponding to the value. After cleaning irrelevant comments, use Bayesian SnowNLP for sentiment classification; the flowchart. Detailed steps are as follows. 1) Comment on impurity cleaning: remove English, numbers,