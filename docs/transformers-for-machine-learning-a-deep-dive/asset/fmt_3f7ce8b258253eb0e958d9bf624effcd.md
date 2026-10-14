
Sentence level representations are constructed in the same manner as XCLO except for the negative sampling where instead of collecting samples from {*y*[*j*]}[*j* = 1, *j* ≠ *i*]^(*N*) smoothed linear interpolation \[[31](#refbib.xhtml#refbib_31), [300](#refbib.xhtml#refbib_300)\] between sentence representations is used to construct hard negative samples.

For world-level representations, the contrastive loss similarity score is computed between a parallel sentence (*x*[*i*], *y*[*i*]) \[CLS\] token representation and other words representations. For each parallel sentence pair input (*x*[*i*], *y*[*i*]) , a bag of words 𝒲 is maintained, where all words in 𝒲 are considered positive samples and all other words in the vocabulary are negative samples. For efficient negative words sampling, HICTL does not sample from the entire vocabulary but rather constructs a set of negative words that very close to parallel sentence (*x*[*i*], *y*[*i*]) \[CLS\] token representation.

### 4.1.3 Dual-Encoder Multilingual NLU

#### 4.1.3.1 Language-agnostic BERT Sentence Embedding (LaBSE)

Language-agnostic BERT Sentence Embedding (LaBSE) \[[88](#refbib.xhtml#refbib_88)\] is an architecture for training cross-lingual sentence representations which combines Masked Language Model (MLM) and Translation Language Model (TLM) pre-training tasks from XLM \[[146](#refbib.xhtml#refbib_146)\] with a translation ranking task using bi-directional dual-encoders with additive margin softmax loss\[[283](#refbib.xhtml#refbib_283)\]. The dual-encoders, as shown in [Fig. 4.6](#ch4.xhtml#fig4_6), consist of two paired mBERT encoders. The \[CLS\] token sentence representation from both encoders are fed to a scoring function. [Fig. 4.6](#ch4.xhtml#fig4_6) provide an illustration of the LaBSE architecture.

![Figure 4.6 Illustration of Language-agnostic BERT Sentence Embedding (LaBSE) architecture \[88\].](images/fig4_6.jpg)

[Figure 4.6](#ch4.xhtml#b4fig4_6) Illustration of Language-agnostic BERT Sentence Embedding (LaBSE) architecture \[[88](#refbib.xhtml#refbib_88)\].

**Bidirectional Dual Encoder with Additive Margin Softmax** The dual-encoder architecture \[[283](#refbib.xhtml#refbib_283)\] has proven to be very effective for ranking tasks such as the translation retrieval task employed by LaBSE for cross-lingual embedding. Formally, for a parallel sentence pair (*x*[*i*], *y*[*i*]), translation retrieval is a ranking problem that aims to place *y*[*i*], the true translation of *x*[*i*], higher than all sentences in the space of translations 𝒴. *P*(*y*[*i*] ∣ *x*[*i*]) is formulated as:

$$\\begin{array}{l} {P({y\_{i}\\mid x\_{i}}) = \\frac{e^{\\phi({x\_{i},y\_{i}})}}{\\sum\\limits\_{\\overline{y} \\in \\mathcal{Y}}e^{\\phi({x\_{i},\\overline{y}})}}} \\\\ \\end{array}$$  

(4.11)

where *ϕ* is the scoring function of the similarity between the representations of *x*[*i*] and *y*[*i*]

During training *P*(*y*[*i*] ∣ *x*[*i*]) is approximated by sampling negatives, *y*[*n*], from translation pairs in the same batch:

$$\\begin{array}{l} {P\_{\\text{approx~}}({y\_{i}\\mid x\_{i}}) = \\frac{e^{\\phi({x\_{i},y\_{i}})}}{e^{\\phi({x\_{i},y\_{i}})} + {\\sum\\limits\_{n = 1,n \\neq i}^{N}e^{\\phi({x\_{i},y\_{n}})}}}} \\\\ \\end{array}$$  

(4.12)

Therefore, for parallel source and target pairs (*x*[*i*], *y*[*i*]), the model can be optimized using the log-likelihood objective \[[283](#refbib.xhtml#refbib_283)\]:

$$\\begin{array}{l} {\\mathcal{L}\_{s} = - \\frac{1}{N}{\\sum\\limits\_{i = 1}^{N}\\frac{e^{\\phi({x\_{i},y\_{i}})}}{e^{\\phi({x\_{i},y\_{i}})} + {\\sum\\limits\_{n = 1,n \\neq i}^{N}e^{\\phi({x\_{i},y\_{n}})}}}} \\\\ \\end{array}$$  

(4.13)

For each *x*[*i*], the loss ℒ[*s*] aims to identify the correct *y*[*i*]. This means that using ℒ[*s*] will result in an asymmetric relationship between *x*[*i*] and *y*[*i*] representations. To overcome this issue, Yand et al. \[[283](#refbib.xhtml#refbib_283)\] introduced the bidirectional learning objective, ${\\overline{\\mathcal{L}}}\_{s}$ that explicitly optimizes both forward and backward ranking of the parallel pair (*x*[*i*], *y*[*i*]):

$$\\begin{matrix} {{\\mathcal{L}^{\\prime}}\_{s} = - \\frac{1}{N}{\\sum\\limits\_{i = 1}^{N}\\frac{e\\phi(yi,xi)}{e\\phi(yi,xi) + \\sum\_{n = 1,n \\neq i}^{N}e^{\\phi}(yi.x\_{n})}}} \\\\ {{\\overline{\\mathcal{L}}}\_{\\mathcal{S}} = \\mathcal{L}\_{\\mathcal{S}} + {\\mathcal{L}^{\\prime}}\_{\\mathcal{S}}} \\\\ \\end{matrix}$$  

(4.14)

For added separation between the correct translations the closest non-translations that are very close, the scoring function *ϕ* is extended with additive margin softmax, which introduces a margin *m* around the positive parallel pairs (*x*[*i*], *y*[*i*]).

$$\\phi^{\\prime}(x\_{i},y\_{j}) = \\begin{cases} {\\phi(x\_{i},y\_{j}) - m} & {~if~i = j} \\\\ {\\phi(x\_{i},y\_{j})} & {~if~i \\neq j} \\\\ \\end{cases}$$  

(4.15)

Applying *ϕ*^′(*x*[*i*], *y*[*j*]) to the bidirectional loss ${\\overline{\\mathcal{L}}}\_{s}$, the additive margin bidirectional loss becomes as follows \[[283](#refbib.xhtml#refbib_283)\]:

$$\\begin{array}{ll} {\\mathcal{L}\_{ams} = - \\frac{1}{N}} & {\\sum\\limits\_{i = 1}^{N}\\frac{e^{\\phi({x\_{i},y\_{i}}) - m}}{e^{\\phi({x\_{i},y\_{i}}) - m} + {\\sum\\limits\_{n = 1,n \\neq i}^{N}e^{\\phi({x\_{i},y\_{n}})}}}} \\\\ \\ & {{\\overline{\\mathcal{L}}}\_{ams} = \\mathcal{L}\_{ams} + \\mathcal{L}\_{ams}^{\\prime}} \\\\ \\end{array}$$  

(4.16)

As mentioned earlier, LaBSE pre-trains its BERT based encoders with Masked Language Model (MLM) and Translation Language Model (TLM) pre-training tasks using monolingual and parallel corpora, respectively. LaBSE trains transformer encoders using a three-stage progressive stacking approach. For a *L* layer encoder, it first learning a model of *fracL*4 layers, then *fracL*2 layers, and lastly all *L* layers. During successive training steps, the parameters of the earlier steps models are copied to the subsequent ones.

#### 4.1.3.2 Multilingual Universal Sentence Encoders (mUSE)

Multilingual Universal Sentence Encoders (mUSE) \[[49](#refbib.xhtml#refbib_49), [284](#refbib.xhtml#refbib_284)\] proposes an approach for cross-lingual sentence embedding learning by combining multitask learning of monolingual sentence representations, and dual-encoders for multilingual sentence embeddings learning for parallel text retrieval. By combining the two approaches, mUSE transfers the strong performance learned on monolingual tasks to zero-shot learning in other languages. Basically, for a certain language pair, source and target language, the model uses a multitask architecture to learn across (i) source language monolingual tasks, (ii) monolingual target language tasks, and (iii) a source-to-target language translation task that serves as a bridging task to encourage cross-lingual representation alignment across all the trained tasks. [Fig. 4.7](#ch4.xhtml#fig4_7) provides an illustration of the architecture for QA, NLI and the bridging translation tasks.

![Figure 4.7 Illustration of mUSE architecture for QA, NLI and the bridging translation tasks \[284\].](images/fig4_7.jpg)

[Figure 4.7](#ch4.xhtml#b4fig4_7) Illustration of mUSE architecture for QA, NLI and the bridging translation tasks \[[284](#refbib.xhtml#refbib_284)\].

mUSE uses dual-encoders to perform multitask learning on tasks that can be represented as ranking input-response sentence pairs. Some tasks fall naturally within this framework such as QA and translation tasks. Other tasks might need a special reformulation such as NLI. Input-response ranking can be formally described as follows: For an input-response pair (*s*[*i*]^(*I*), *s*[*i*]^(*R*)), the goal is to get *s*[*i*]^(*R*) to higher than all possible responses *s*[*j*]^(*R*) ∈ 𝒮^(*R*). In other words, the conditional probability *P*(*s*[*i*]^(*R*) ∣ *s*[*i*]^(*I*)) should be defined as:
