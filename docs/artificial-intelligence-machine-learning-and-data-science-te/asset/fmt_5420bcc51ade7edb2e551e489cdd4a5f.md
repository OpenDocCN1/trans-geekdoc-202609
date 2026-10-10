
## Figure 12.4 The traditional C & W model and proposed neural-networks (SSWEh and SSWEu) for learning sentiment-specific word embedding ([Ghosh et al. 2017](#ch20.xhtml#r458))

In the `SSWEh` model, the cross-entropy error of the Softmax layer is:

```
$loss_{h}\left( t \right) = - \sum\limits_{k = \{{0,1}\}}f_{k}^{g}\left( t \right) \cdot log\left( {f_{k}^{h}\left( t \right)} \right)$ (12.5)
```

Where `f^g(t)` shows the distribution of sentiment while the `f^h(t)` shows the predicted sentiment distribution.

The loss function `SSWEu` is the sequential blend of two hinge reductions in the `SSWEu` combined model.

```
$loss_u(t,t^{(\tau)}) = \alpha \cdot loss_{c\omega}(t,t^{(\tau)}) + (1-\alpha) \cdot loss_{us}(t,t^{(\tau)})$ (12.6)
```

Where `loss_{c\omega}(t,t^{(\tau)})` is the syntactic loss, `loss_{us}(t,t^{(\tau)})` is the sentiment loss as described in Equation 12.7. The hyper-parameter `α` weighs the two parts.

```
$loss_{us}(t,t^{(\tau)}) = max(0,1-\delta[s](t)f[1]^{(u)}(t)+\delta[s](t)f[1]^{(u)}(t^{(\tau)}))$ (12.7)
```

With the identical NN and the similar parameter setting, the embedding of unigrams, bigrams and trigrams are performed distinctly.

The unigrams (bigram/trigram) contexts are the surrounding unigrams (bigrams/trigrams), respectively.

The introduced approach represents a similar vector demonstration through refining vector space representation as of semantic lexicons ([Gonçalves et al. 2013](#ch20.xhtml#r459)). The extensive experiments validate the effectiveness tested on numerous languages and also attained enhancement of word vector models. The proposed method outperforms compared to the prevalent method.

The easy and efficient unsupervised method for embedding a sentence is grounded on the discourse vectors in the random walk prototypical designed for engendering text ([Graves et al. 2014](#ch20.xhtml#r460)). The proposed method was superior to the baseline task arranged with the same tasks, and outperformed compared with the supervised approach, named as RNN, LSTM etc. sentence embedding, a feature achieved through downstream supervised scheme, and had superior performance to other advanced techniques.

The learning of the word representation is enhanced through the affect lexical from an amount of data ([Howard & Ruder 2018](#ch20.xhtml#r461)). Using a `Word2Vec SkipGram`, the fine-grained data were extracted, i.e. a word's psycholinguistic and expressive positioning during a training period. For accumulated learning both the `Word2Vec CBOW` and `GloVe` approach were used. Unlabeled data control by Warriner's affect lexicon was used to regularize the vector representations learning. The extensive research showed the suggested methods' efficiency and the suggested method was superior on sentiment detection.

The authors have developed a Skipgram technique for each word denoted by a bag of character n-grams ([Kim 2014](#ch20.xhtml#r462)). As generated in this design, each letter n-gram integrates with the vector and word connected with it. The proposed method is fast and delivers fast access to data during training, and permits word depictions. The authors tested the proposed approach on nine different languages for similarity and an analogous scheme. The proposed method outperformed, compared to recently proposed morphological word representation approaches.

The fast, easy and efficient method for learning the word embedding data on contextual text through the different platform has been given by the authors ([Kiperwasser & Goldberg 2016](#ch20.xhtml#r463)). The extensive research showed the efficiency of the proposed approach on numerous down-stream NLP tasks.

The suggested scheme worked as follows:

First, let us describe the intent of the skipgram framework.

```
$L_{\mathcal{D}} = \sum\limits_{({\omega,c}) \in \mathcal{D}}\#\left( {\omega,c} \right)\left( {\left( {log\,\sigma(\omega \cdot c} \right) + \sum\limits_{i = 1}^{k}E_{{c^{\prime}}_{i}^{}\sim P{(\omega)}}\left. \left\lbrack {\log\sigma\left( {- \omega \cdot {c^{\prime}}_{i}^{}} \right)} \right\rbrack \right)} \right)$ (12.8)
```

Where `𝒟` refers to the complete text corpus through which we learn the word embeddings. The word `w` is the recent word, `c` is the context word, and `#(ω, c)` is the number of times they co-occur in `𝒟`. We use `ω` and `c` to designate the vector representations for `ω` and `c`, respectively. The symbol `σ(⋅)` denotes the sigmoid-function. The word `c'[i]` is a "negative sample" sampled from the distribution `P(ω)` – typically selected as the unigram distribution `U(ω)` raised to the 3/4^(rd) power.

The authors first learn for each word `ω` an embedding `ws` via the origin domain `𝒟[s]`. Next, we learn the objective area embeddings as follows:

```
${L'}_{\mathcal{D}_{t}}^{} = L_{\mathcal{D}_{t}} + \sum\limits_{\omega \in \mathcal{D}_{t} \cap \mathcal{D}_{s}}\alpha_{\omega} \cdot \left\| {\omega_{t} - \omega_{s}} \right\|^{2}$ (12.9)
```

Where `𝒟[t]` refers to the target area, and `ω[t]` is the target area representation for `ω`. Such a regularized objective can still be optimized using standard stochastic gradient descent.

```
$\alpha[\omega] = \sigma(\lambda \cdot \varnothing(\omega))$ (12.10)
```

Where `λ` is a hyper-parameter to decide the scaling factor of the significance function `⌀(⋅)`. Define the normalized frequency for the word `ω` as follows-

```
$\mathcal{F}_{\mathcal{D}}\left( \omega \right) = \frac{f_{\mathcal{D}}\left( \omega \right)}{\max\limits_{\omega'\epsilon\mathcal{D}_{k}}f_{\mathcal{D}}\left( \omega' \right)}$ (12.11)
```

Function `⌀(⋅)` based on the following metric that is motivated by the well-known Sørensen-Dice coefficient calculated as:

```
$\varnothing\left( \omega \right) = \frac{2 \cdot \mathcal{F}_{\mathcal{D}_{s}}\left( \omega \right) \cdot \mathcal{F}_{\mathcal{D}_{t}}\left( \omega \right)}{\mathcal{F}_{\mathcal{D}_{s}}\left( \omega \right) + \mathcal{F}_{\mathcal{D}_{t}}\left( \omega \right)}$ (12.12)
```

Note that the value of `φ(w)` would be high only if both `ℱ[𝒟[s]](ω)` and `ℱ[𝒟[t]](ω)` are high.

### 12.2.3 NLP-Machine Reading

The long short-term memory construction is encompassed by a memory net instead of a solitary memory lockup. The presented m/c reading is based on a simulator that was used to test L-to-R and executed shallow-reasoning by memory and attention (Li et al. 2016a). The proposed method allowed adaptive cell usage throughout the recurrence via NN. They contributed a route to weekly induce relation midst tokens. It was used for a single sequence but also accumulated through the encode–decode framework (see [Figure 12.5](#ch20.xhtml#f106)). The extensive studies showed the efficiency of the proposed approach.

**Modeling Two Sequences with LSTMN**, merge the LSTMN, which focuses on intra-relation reasoning, with the encoder–decoder network whose attention module learns the inter-alignment between two sequences.

![Figure 12.5 The encoder utilizes the intra attention and the decoder utilizes intra as well as inter attention scheme. The above mentioned structure demonstrates the two approaches for merging the intra and inter attention in the decoder (Li et al. 2016a).](html/images/9780367720919_C012_005.jpg)

Figure 12.5 The encoder utilizes the intra attention and the decoder utilizes intra as well as inter attention scheme. The above mentioned structure demonstrates the two approaches for merging the intra and inter attention in the decoder ([Li et al. 2016a](#ch20.xhtml#r465)).

The figure represents the two kinds of combinations.

> **Shallow Attention Fusion**, Instead of a standard RNN or LSTM, shallow combination basically handles the LSTMN as a distinct part that can be simply used in an encoder and decoder design.
