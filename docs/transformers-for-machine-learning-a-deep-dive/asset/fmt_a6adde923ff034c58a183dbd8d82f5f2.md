
For graphs that have attributes on the edges, (6.21)–(6.25) are modified and expanded to account for the edge embeddings. The node embeddings are updated in mostly the way. The only change is that the attention weights that go into the softmax operation now have a contribution from the edge embeddings:

$$\\begin{array}{ll} \\mathbf{\\widetilde{h}}\_{i}^{(l + 1)} & {= \\lbrack{\\mathbf{Attn}(1,l,i);\\ldots;\\mathbf{Attn}(H,l,i)}\\rbrack\\mathbf{O}^{(l)}} \\\\ \\end{array}$$  

(6.26)

$$\\begin{array}{ll} \\mathbf{\\widetilde{e}}\_{ij}^{(l + 1)} & {= \\lbrack{{\\widetilde{w}}\_{ij}^{(1,l)};\\ldots,{\\widetilde{w}}\_{ij}^{(H,l)}}\\rbrack\\mathbf{O}\_{edge}^{(l)}} \\\\ \\end{array}$$  

(6.27)

$$\\begin{array}{ll} {\\mathbf{Attn}(m,l,i)} & {= {\\sum\\limits\_{j \\in S\_{i}}w\_{ij}^{(m,l)}}\\mathbf{V}^{(m,l)}\\mathbf{h}\_{j}^{(l)}} \\\\ \\end{array}$$  

(6.28)

$$\\begin{array}{ll} w\_{ij}^{(m,l)} & {= \\text{softmax}\_{\\text{j}}\\left( {\\widetilde{\\text{w}}}\_{\\text{ij}}^{(\\text{m},\\text{l})} \\right)} \\\\ \\end{array}$$  

(6.29)

$$\\begin{array}{ll} {\\widetilde{w}}\_{ij}^{(m,l)} & {= \\left( \\frac{\\mathbf{W}\_{q}^{(m,l)}\\mathbf{h}\_{i}^{(l)} \\cdot \\mathbf{W}\_{k}^{(m,l)}\\mathbf{h}\_{j}^{(l)}}{\\sqrt{d\_{k}}} \\right) \\cdot \\mathbf{W}\_{E}^{(m,l)}\\mathbf{e}\_{ij}^{(l)},} \\\\ \\end{array}$$  

(6.30)

where, again, *S*[*i*] is the set of key positions that query *i* attends to, *m* indexes the attention head, **W**[*q*]^((*m*, *l*)), **W**[*k*]^((*m*, *l*)), **W**[*v*]^((*m*, *l*)), **W**[*E*]^((*m*, *l*)) ∈ ℝ^(*d*[*k*] × *d*), *d*[*k*] is the key-value dimension. The **W**[*E*]^((*m*, *l*)) are the weights for a value layer for the edges; it transforms the edge embeddings analogous to how **W**[*v*]^((*m*, *l*)) transforms the node embeddings.

Note that while there is a single multi-head attention mechanism when there are edge attributes, that there is a separate linear layer for combining the final attention for nodes and the final attention for edges. This can be seen from the existence of **O**^((*l*)), **O**[*e**d**g**e*]^((*l*)) ∈ ℝ^(*d* × *d*). As in the case without edge attributes, the exponents in the softmax calculation above are clamped to \[ − 5, 5\] for numerical stability.

`h̃`[*i*]^((*l* + 1)) is passed into the remainder of the Transformer layer as follows, resulting in two outputs for the Transformer layer, **h**[*i*]^((*l* + 1)) for nodes (as shown in (6.31)) and **e**[*i**j*]^((*l* + 1)) for edges:

$$\\begin{array}{ll} \\mathbf{h}\_{i}^{(l + 1)} & {= Norm(\\mathbf{h}^{\\prime}\\ \_{i}^{(l + 1)} + \\mathbf{h}^{\\prime\\prime}\\ \_{i}^{(l + 1)})} \\\\ \\end{array}$$  

(6.31)

$$\\begin{array}{ll} {\\mathbf{h}^{\\prime}\\ \_{i}^{(l + 1)}} & {= Norm(\\mathbf{h}\_{i}^{(l)} + \\mathbf{\\widetilde{h}}\_{i}^{(l + 1)})} \\\\ \\end{array}$$  

(6.32)

$$\\begin{array}{ll} {\\mathbf{h}^{\\prime\\prime}\\ \_{i}^{(l + 1)}} & {= \\mathbf{W}\_{n,2}^{(l)}\\text{ReLU}\\left( {\\mathbf{W}\_{\\text{n},\\text{1}}^{(\\text{l})}\\mathbf{h}^{\\prime}\\ \_{\\text{i}}^{(\\text{l+1})}} \\right)} \\\\ \\end{array}$$  

(6.33)

$$\\begin{array}{ll} \\mathbf{e}\_{ij}^{(l + 1)} & {= Norm(\\mathbf{e}^{\\prime}\\ \_{ij}^{(l + 1)} + \\mathbf{e}^{\\prime\\prime}\\ \_{ij}^{(l + 1)})} \\\\ \\end{array}$$  

(6.34)

$$\\begin{array}{ll} {\\mathbf{e}^{\\prime}\\ \_{ij}^{(l + 1)}} & {= Norm(\\mathbf{e}\_{ij}^{(l)} + \\mathbf{\\widetilde{e}}\_{ij}^{(l + 1)})} \\\\ \\end{array}$$  

(6.35)

$$\\begin{array}{ll} {\\mathbf{e}^{\\prime\\prime}\\ \_{ij}^{(l + 1)}} & {= \\mathbf{W}\_{e,2}^{(l)}\\text{ReLU}\\left( {\\mathbf{W}\_{\\text{e},\\text{1}}^{(\\text{l})}\\mathbf{e}^{\\prime}\\ \_{\\text{ij}}^{(\\text{l+1})}} \\right)} \\\\ \\end{array}$$  

(6.36)

where **W**[*n*, 1]^((*l*)), **W**[*e*, 1]^((*l*)) ∈ ℝ^(2*d* × *d*), **W**[*n*, 2]^((*l*)), **W**[*e*, 2]^((*l*)) ∈ ℝ^(*d* × 2*d*), and *Norm* can be layer normalization or batch normalization. Subscripts *n* and *e* are for nodes and edges, respectively. This is shown schematically in [Fig. 6.4](#ch6.xhtml#ch6_xhtml#fig6_4).

![Figure 6.4 Diagram of the Graph Transformer encoder, with edge attributes. The encoder structure is shown on the left. The multi-head attention mechanism is shown on the right. As described in section 6.6.1.1, Laplacian embeddings are only applied to the input layer, l = 0.](images/fig6_4.jpg)

[Figure 6.4](#ch6.xhtml#ch6_xhtml#b6fig6_4) Diagram of the Graph Transformer encoder, with edge attributes. The encoder structure is shown on the left. The multi-head attention mechanism is shown on the right. As described in [section 6.6.1.1](#ch6.xhtml#ch6_xhtml#sec6_6_1_1), Laplacian embeddings are only applied to the input layer, *l* = 0.

## 6.7 Reinforcement Learning

Reinforcement Learning (RL) is a machine learning method that uses rewards to train an autonomous agent that can choose its next action so that it gets the best cumulative reward, given its current state.

To understand the process of reinforcement learning, we can start with a finite Markov decision process \[[239](#refbib.xhtml#refbib_239)\], which is a formal way of looking at a sequence of decisions that an agent which interacts with an environment can take. The agent and the environment interact at a sequence of time steps *t* = 0, …, *T*. At each *t*, the agent gets the environment's state *s*[*t*] ∈ 𝒮 and then chooses an action *a*[*t*] ∈ 𝒜(*s*). At time *t* + 1, the agent receives a reward from the environment *r*[*t* + 1] ∈ ℝ and the environment's state is updated to *s*[*t* + 1]. This simple idea is illustrated in [Fig. 6.5](#ch6.xhtml#fig6_5). Note that generally speaking, the reward will be a function of the state and action, *r*[*t*] = *R*(*s*[*t*], *a*[*t*]). As time progresses, a sequence of states, actions, and rewards accumulates: (*s*[0], *a*[0], *r*[1], *s*[1], *a*[1], *r*[2], *s*[2], *a*[2], *r*[3], …). This sequence can be called a trajectory.

![Figure 6.5 Depiction of the interaction between the agent and environment in reinforcement learning. At time t, the state observed by the agent is st. The agent then selects an action at. In the next time step, t + 1, the environment updates it state to s\_{t + 1} and issues a reward to the agent, r\_{t + 1}. After this, the cycle can repeat.](images/fig6_5.jpg)

[Figure 6.5](#ch6.xhtml#b6fig6_5) Depiction of the interaction between the agent and environment in reinforcement learning. At time *t*, the state observed by the agent is *s*[*t*]. The agent then selects an action *a*[*t*]. In the next time step, *t* + 1, the environment updates it state to *s*[*t* + 1] and issues a reward to the agent, *r*[*t* + 1]. After this, the cycle can repeat.

In practice, *r*[*t*] and *s*[*t*] are random variables with probability distributions. The probability of moving to state *s*^′ and earning reward *r*, given that action *a* was taken in state *s* is given by

$$\\begin{array}{ll} {p(s^{\\prime},r|s,a)} & {= Prob({s\_{t} = s^{\\prime},r\_{t} = r|s\_{t - 1} = s,a\_{t - 1} = a})} \\\\ {{\\sum\\limits\_{s^{\\prime} \\in \\mathcal{S}}{\\sum\\limits\_{r \\in \\mathcal{R}}p}}(s^{\\prime},r|s,a)} & {= 1,\\,\\,\\forall s \\in \\mathcal{S},\\, a \\in \\mathcal{A}(s)} \\\\ \\end{array}$$  

(6.37)

The transition probabilities *p* fully characterize the dynamics of the environment and the agent does not know the set of rewards or the transition probabilities.

The task of RL is to learn the probability that the agent chooses action *a* while in state *s*. This probability distribution is called a policy.

### 6.7.1 Decision Transformer

Decision Transformer \[[41](#refbib.xhtml#refbib_41)\] is the result of an attempt to replace reinforcement learning (RL) methods with a transformer that models the sequence of states, actions, and rewards that is used to train an autonomous agent. This application is far from the language modeling tasks to which most transformers are applied.
