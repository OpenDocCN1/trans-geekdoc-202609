![](bbox=[0.133, 0.096, 0.888, 0.385])

is the average of the word vectors in the window of size $H$ around word $w_t$. Thus we try to predict each word given its context. The model is called CBOW because it uses a bag of words assumption for the context, and represents each word by a continuous embedding.

# 19.5.2.2 Word2vec Skip-gram model

In CBOW, each word is predicted from its context. A variant of this is to predict the context (surrounding words) given each word. This yields the following objective:

$$\log p(\mathbf{w}) \approx \sum_{t=1}^{T}\left[\sum_{h=1}^{H_t}\log p(w_{t-h}\mid w_t)+\log p(w_{t+h}\mid w_t)\right] \tag{19.20}$$

$$=\sum_{t=1}^{T}\left[\sum_{h=1}^{H_t}\mathbf{u}_{w_{t-h}}^{\mathsf{T}}\mathbf{v}_{w_t}+\mathbf{u}_{w_{t+h}}^{\mathsf{T}}\mathbf{v}_{w_t}-2\log\sum_{w'}\exp\left(\mathbf{v}_{w_t}^{\mathsf{T}}\mathbf{u}_{w'}\right)\right] \tag{19.21}$$

where $H_t$ is a randomly sampled window length for location $t$, and $\mathbf{u}_w$ is the embedding vector of word $w$ when used as a context word as opposed to a predicted word. See Fig. 19.10(b) for an illustration.

We can approximate this objective by sampling a single context word $c_t$ for each $w_t$, instead of summing over all words $w_{t-h},\ldots,w_{t+h}$ in the window:

$$\log p(\mathbf{w}) \approx \sum_t \log p(c_t\mid w_t)=\sum_t\left[\mathbf{u}_{c_t}^{\mathsf{T}}\mathbf{v}_{w_t}-\log\sum_{w'}\exp\left(\mathbf{v}_{w_t}^{\mathsf{T}}\mathbf{u}_{w'}\right)\right] \tag{19.22}$$

This model is known as the **skipgram model**, since we are working with $H$-gram models, but skipping most of the terms.