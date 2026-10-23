# # 3.8. Probabilistic graphical models

word triples. If we use $M = 1$, we get a **bigram model**, which models the distribution over word pairs.

For large vocabulary sizes, the number of parameters needed to estimate the conditional distributions for $M$-gram models for large $M$ can become prohibitive. In this case, we need to make additional assumptions beyond conditional independence. For example, we can assume that $p(y_t|y_{t-M:t-1})$ can be represented as a low-rank matrix, or in terms of some kind of neural network. This is called a **neural language model**. See Chapter 15 for details.



A PGM defines a joint probability distribution. We can therefore use the rules of marginalization and conditioning to compute $p(Y_i|Y_j = y_j)$ for any sets of variables $i$ and $j$.



For example, consider the water sprinkler example in Fig. 3.20. We can compute our prior belief that it has rained as follows:

```
$$p(R = 1) = \sum_{c=0}^{1} p(C = c)p(R = 1|C = c) = 0.5$$
```

If we see that the grass is wet, then our (posterior) belief that it has rained changes to $p(R = 1|W = 1) = 0.7079$. Now suppose we also notice the water sprinkler was turned on: our belief that it rained goes down to $p(R = 1|W = 1, S = 1) = 0.3204$. This negative mutual interaction between multiple causes of some observations is called the **explaining away effect**, also known as **Berkson’s paradox**.



Let us now give a more interesting example. We will consider a hypothetical model proposed in [LS88]; this is known as the “Asia network”, since it was designed to model various lung diseases in Western patients who may have recently visited Asia. (Note: this purely for pedagogical purposes, and it is not a realistic model. Also, it should be apparent that we could, in principle, create a similar model for COVID-19 diagnosis.)

Fig. 3.22a shows the model, as well as the prior marginal distributions over each node (assumed to be binary). Now suppose the patient reports that they have Dyspnea, aka shortness of breath. We can represent this fact by “shading” that node a dark color, and then clamping the distribution to be 100% probability that Dyspnea=1, and 0% probability that Dyspnea=0. We then propagate this new information through the network to get the updated marginal distributions shown in Fig. 3.22b. We see that the probability of bronchitis has gone up, from 45% to 83.4%, since this is the most likely cause or explanation of the evidence. However, there is some probability that the symptom (Dyspnea) was caused by TB or Lung Cancer.

Now suppose the doctor asks the patient if they have recently been to Asia, and they say yes. Fig. 3.22c shows the new belief state of each node. We see that the probability of TB has increased from 2% to 9%. However, Bronchitis remains the most likely explanation, so the doctor asks if the patient smokes, and they say yes. Fig. 3.22c shows the new belief state of each node. We see that