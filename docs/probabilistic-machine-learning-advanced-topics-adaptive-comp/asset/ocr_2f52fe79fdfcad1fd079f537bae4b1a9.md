![](bbox=[0.25, 0.1, 0.75, 0.33])

Figure 4.30: A CRF for joint part of speech tagging and noun phrase segmentation. From Figure 4.E.1 of [KF09a]. Used with kind permission of Daphne Koller.

where \(\psi(y_t, x_t; \theta)\) are the node potentials and \(\psi(y_t, y_{t+1}; \theta)\) are the edge potentials. (We have assumed that the edge potentials are independent of the input \(x\), but this assumption is not required.)

Note that one could also consider an alternative way to define this conditional distribution, by using a discriminative directed Markov chain:

```
\(p(y_{1:T}|x, \theta) = p(y_1|x_1; \theta) \prod_{t=2}^T p(y_t|y_{t-1}, x_t; \theta)\) (4.139)
```

This is called a maximum entropy Markov model [MFP00]. However, it suffers from a subtle flaw compared to the CRF. In particular, in the directed model, each conditional \(p(y_t|y_{t-1}, x_t; \theta)\), is **locally normalized**, whereas in the CRF, the model is **globally normalized** due to the \(Z(x, \theta)\) term. The latter allows information to propagate through the entire sequence, as we discuss in more detail in Section 4.5.3.

CRFs were widely used in the natural language processing (NLP) community in the 1980s-2010s (see e.g., [Smi11]), although recently they have been mostly replaced by RNNs and transformers (see e.g., [Gol17]). Fortunately, we can get the best of both worlds by combining CRFs with DNNs, which allows us to combine data driven techniques with prior knowledge about constraints on the label space. We give some examples below.

# 4.4.1.1 Noun phrase chunking

A common task in NLP is **information extraction**, in which we try to parse a sentence into **noun phrases** (NP), such as names and addresses of people or businesses, as well as **verb phrases**, which describe who is doing what to whom (e.g., “British Airways rose”). In order to tackle this task, we can assign a **part of speech** tag to each word, where the tags correspond to Noun, Verb, Adjective, etc. In addition, to extract the span of each noun phrase, we can annotate words as being at the beginning (B) or inside (I) of a noun phrase, or outside (O) of one. See Figure 4.30 for an example.

The connections between adjacent labels can encode constraints such as the fact that B (begin) must precede I (inside). For example, the sequences `OBIIO` and `OBIOBIO` are valid (corresponding to