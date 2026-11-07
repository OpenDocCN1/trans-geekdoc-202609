
In recent years, deep neural networks have got considerable performance as in [Figure 5.2](#ch05.xhtml#f5_2) among many NLP tasks like sentiment analysis \[[45](#ch05.xhtml#r5_45), [46](#ch05.xhtml#r5_46) and [47](#ch05.xhtml#r5_47)\], syntactic analysis \[[48](#ch05.xhtml#r5_48),[49](#ch05.xhtml#r5_49)\], and machine translation \[[50](#ch05.xhtml#r5_50),[51](#ch05.xhtml#r5_51)\]. Different deep neural networks are applied for various tasks in the NLP field. For example, in tasks of dialogue system, Zhou et al. \[[52](#ch05.xhtml#r5_52)\] used the `LSTM` encoder on the top of `CNN` for multi-turn human-computer conversation which takes utterance into consideration to catch utterance-level relations in the text. For `POS` tagging, Andor et al. \[[53](#ch05.xhtml#r5_53)\] proposed a transition-based approach combined with feed-forward neural network, and Huang, Xu, and Yu \[[54](#ch05.xhtml#r5_54)\] also used `Bi-LSTM` to predict POStags. Various deep models have become the new state-of-the-art methods in the NLP field.

![FIGURE 5.2 Stages of NLP in the deep learning era.](images/Fig05_02.jpg)

[`FIGURE 5.2`](#ch05.xhtml#f5_2b) Stages of NLP in the deep learning era.

## 5.3.1 Word Embeddings

In the most recent decade, word embeddings \[[48](#ch05.xhtml#r5_48),[49](#ch05.xhtml#r5_49)\] have set up themselves as a center component of numerous NLP frameworks. Without a doubt, NLP techniques manage characteristic language, which frequently shows up as text. This content is itself made out of more modest units like words and characters, which are not straightforwardly justifiable by computer in any human sense. Subsequently, word embeddings are expected to mathematically speak to literary information which can be perused, perceived, and prepared by computer programs. This need was underlined with the new blast of deep realizing, which demonstrated to tackle a tremendous measure of issues in different fields.

NLP analysts \[[55](#ch05.xhtml#r5_55)\] who needed to utilize promising deep learning models on content information needed to think of a mathematical method to speak to words. This brought about a broad examination for best speaking to printed information with the end goal that the portrayals catch both semantic and syntactic implications of words. Practically speaking, there are a few different ways to speak to a word by a vector. The easiest one is presumably one-hot encoding.

### 5.3.1.1 Word2vec

The `Word2vec` model was presented by Mikolov et al. \[[56](#ch05.xhtml#r5_56)\]. The thought is to change a word into a ceaseless vector, which additionally speaks to the word’s neighborhood setting. Embeddings of `Word2vec` don’t have the inadequacy of one-hot encoded word vectors, which can just perceive if a word is actually the equivalent. `Word2vec` \[[57](#ch05.xhtml#r5_57)\] makes these diﬀerentiations more particular by including a word’s precursors and replacements.

The word portrayals incorporate semantic and syntactic data, which are recovered from the setting words. [Figure 5.3](#ch05.xhtml#f5_3) delineates the situation of word vectors with two measurements. The bolts show a numerical distance between two words. For instance, the cosine distance is an appropriate capacity for figuring the diﬀerence between word vectors. In an installing space, it is conceivable that equivalent relations between words can be spoken to by a comparative distance and heading. For instance, the English words “man” and “woman” do have a comparable distance to “king” and “queen.” This implies that the logical diﬀerence among “man” and “woman” is equivalent to “king” and “queen.” Words that relate to the male sexual orientation are utilized with regard to “man” and “king,” though “woman” and “queen” are encircled by more female word structures. Along these lines, the language structure and semantic of a word is consolidated into a word portrayal. This is the genuine strength of word embeddings or `Word2vec`. It makes it simpler to ﬁnd equivalents and concentrate a speaker’s proposed meaning all the more without any problem.

![FIGURE 5.3 Arrows showing the distances between two-word embeddings in a two-dimensional space.](images/Fig05_03.jpg)

[`FIGURE 5.3`](#ch05.xhtml#f5_3b) Arrows showing the distances between two-word embeddings in a two-dimensional space.

The underlying paper of `Word2vec` proposes two diﬀerent ways to deal with learn word vectors out of text corpora with the jargon of `N`. The ﬁrst approach is the Continuous Bag-of-Words (`CBOW`), which predicts a word dependent on its unique situation. The subsequent methodology is called `Skip-gram` \[[58](#ch05.xhtml#r5_58)\] and estimates a word’s unique situation. The two endeavors limit computational intricacy and depend on `FNN`s, which are shown in [Figure 5.4](#ch05.xhtml#f5_4), portraying the two models in more detail.

![FIGURE 5.4 FNN architecture of the CBOW and skip-gram model.](images/Fig05_04.jpg)

[`FIGURE 5.4`](#ch05.xhtml#f5_4b) FNN architecture of the CBOW and skip-gram model.

To compute a word’s vector portrayal, the neural network of `CBOW` takes the setting terms to one side `wt−2`, `wt−1` and right `wt+1`, `wt+2` of the word `wt` as info. This word window can be acclimated to increment or reduction of the size of the neighborhood setting related with the word inserting `vt`. Practically speaking, a setting window of 5 for `CBOW` and 10 for `Skip-gram` is favored1. `CBOW` takes the one-hot encoding of each information word and passes them to the organization to anticipate the one-hot-encoding of the objective word `wt`. The `FNN` models the spot of 1 in the yield vector, which can be viewed as a classiﬁcation task.

The organization that is utilized in `Skip-gram` trades the in-and yield. The objective word is presently the info, and the `FNN` predicts the word’s unique situation. `Skip-gram` prompts better outcomes for little corpora, while `CBOW` is more eﬃcient and recommendable for bigger content sets. For preparing the word vectors \[[57](#ch05.xhtml#r5_57),[58](#ch05.xhtml#r5_58)\], the two methodologies utilize a multilayer perceptron with one shrouded layer. Consequently, the organization has two weight lattices. The ﬁrst one `W (1)` is between the info layer and shrouded layer. `W (2)` is the subsequent network, which associates covered up and yield layer. The quantity of neurons in the shrouded layer is set to 300, and softmax initiation in the yield layer is utilized in the two methodologies.

## 5.3.2 Global Vectors for Word Representation

`Global Vectors for Word Representation` (`GloVe`) do have another methodology for building word vectors. They were at first proposed in Pennington et al. \[[59](#ch05.xhtml#r5_59)\]; furthermore, they put their emphasis not exclusively on the word’s neighborhood setting. The preparation of the `GloVe` vectors is done depending on a worldwide word-to-word co-event network `Xij`. This grid stores the recurrence with which two words `wi` and `wj` happen in a similar setting inside a corpus.

Accordingly, not just the neighborhood setting, which is dictated by the co-event network, is considered, yet additionally factual viewpoints from the corpus. To start with, the grid is developed in an introduction stage in which every content is seen once. Because the co-event architecture takes a portion of memory to parse down massive quantities of data, only word blends containing at least one co-event are saved.

## 5.3.3 Convolutional Neural Networks
