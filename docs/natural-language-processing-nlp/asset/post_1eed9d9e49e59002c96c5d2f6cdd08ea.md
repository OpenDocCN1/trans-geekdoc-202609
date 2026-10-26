
- 16.2.3 *Formal semantics beyond the sentence level* 384
- 16.3 Relations 385
  - 16.3.1 Shallow discourse relations 385
  - 16.3.2 Hierarchical discourse relations 389
  - 16.3.3 Argumentation 392
  - 16.3.4 Applications of discourse relations 393
- IV Applications 401
  - 17 Information extraction 403
    - 17.1 Entities 405
      - 17.1.1 Entity linking by learning to rank 406
      - 17.1.2 Collective entity linking 408
      - 17.1.3 *Pairwise ranking loss functions 409
    - 17.2 Relations 411
      - 17.2.1 Pattern-based relation extraction 412
      - 17.2.2 Relation extraction as a classification task 413
      - 17.2.3 Knowledge base population 416
      - 17.2.4 Open information extraction 419
    - 17.3 Events 420
    - 17.4 Hedges, denials, and hypotheticals 422
    - 17.5 Question answering and machine reading 424
      - 17.5.1 Formal semantics 424
      - 17.5.2 Machine reading 425
  - 18 Machine translation 431
    - 18.1 Machine translation as a task 431
      - 18.1.1 Evaluating translations 433
      - 18.1.2 Data 435
    - 18.2 Statistical machine translation 436
      - 18.2.1 Statistical translation modeling 437
      - 18.2.2 Estimation 438
      - 18.2.3 Phrase-based translation 439
      - 18.2.4 *Syntax-based translation 441
    - 18.3 Neural machine translation 442
      - 18.3.1 Neural attention 444
      - 18.3.2 *Neural machine translation without recurrence 446
      - 18.3.3 Out-of-vocabulary words 448
    - 18.4 Decoding 449
    - 18.5 Training towards the evaluation metric 451
  - 19 Text generation 457
    - 19.1 Data-to-text generation 457
      - 19.1.1 Latent data-to-text alignment 459
      - 19.1.2 Neural data-to-text generation 460
    - 19.2 Text-to-text generation 464
      - 19.2.1 Neural abstractive summarization 464
      - 19.2.2 Sentence fusion for multi-document summarization 465
    - 19.3 Dialogue 466
      - 19.3.1 Finite-state and agenda-based dialogue systems 467
      - 19.3.2 Markov decision processes 468
      - 19.3.3 Neural chatbots 470
- A Probability 475
  - A.1 Probabilities of event combinations 475
    - A.1.1 Probabilities of disjoint events 476
    - A.1.2 Law of total probability 477
  - A.2 Conditional probability and Bayes’ rule 477
  - A.3 Independence 479
  - A.4 Random variables 480
  - A.5 Expectations 481
  - A.6 Modeling and estimation 482
- B Numerical optimization 485
  - B.1 Gradient descent 486
  - B.2 Constrained optimization 486
  - B.3 Example: Passive-aggressive online learning 487
- Bibliography 489

## Preface

The goal of this text is to focus on a core subset of natural language processing, unified by the concepts of learning and search. A remarkable number of problems in natural language processing can be solved by a compact set of methods:

**Search.** Viterbi, CKY, minimum spanning tree, shift-reduce, integer linear programming, beam search.

**Learning.** Maximum-likelihood estimation, logistic regression, perceptron, expectation-maximization, matrix factorization, backpropagation.

This text explains how these methods work, and how they can be applied to a wide range of tasks: document classification, word sense disambiguation, part-of-speech tagging, named entity recognition, parsing, coreference resolution, relation extraction, discourse analysis, language modeling, and machine translation.

## Background

Because natural language processing draws on many different intellectual traditions, almost everyone who approaches it feels underprepared in one way or another. Here is a summary of what is expected, and where you can learn more:

**Mathematics and machine learning.** The text assumes a background in multivariate calculus and linear algebra: vectors, matrices, derivatives, and partial derivatives. You should also be familiar with probability and statistics. A review of basic probability is found in Appendix A, and a minimal review of numerical optimization is found in Appendix B. For linear algebra, the online course and textbook from Strang (2016) provide an excellent review. Deisenroth et al. (2018) are currently preparing a textbook on *Mathematics for Machine Learning*, a draft can be found online.¹ For an introduction to probabilistic modeling and estimation, see James et al. (2013); for

¹https://mml-book.github.io/

### Text datasets

| Symbol | Meaning |
| --- | --- |
| \(w_m\) | word token at position \(m\) |
| \(N\) | number of training instances |
| \(M\) | length of a sequence (of words or tags) |
| \(V\) | number of words in vocabulary |
| \(y^{(i)}\) | the true label for instance \(i\) |
| \(\hat{y}\) | a predicted label |
| \(\mathcal{Y}\) | the set of all possible labels |
| \(K\) | number of possible labels \(K = \lvert \mathcal{Y} \rvert\) |
| □ | the start token |
| ■ | the stop token |
| \(\mathbf{y}^{(i)}\) | a structured label for instance \(i\), such as a tag sequence |
| \(\mathcal{Y}(w)\) | the set of possible labelings for the word sequence \(w\) |
| ◇ | the start tag |
| ◆ | the stop tag |

### Probabilities

| Symbol | Meaning |
| --- | --- |
| \(\Pr(A)\) | probability of event \(A\) |
| \(\Pr(A \mid B)\) | probability of event \(A\), conditioned on event \(B\) |
| \(p_B(b)\) | the marginal probability of random variable \(B\) taking value \(b\); written \(p(b)\) when the choice of random variable is clear from context |
| \(p_{B\mid A}(b \mid a)\) | the probability of random variable \(B\) taking value \(b\), conditioned on \(A\) taking value \(a\); written \(p(b \mid a)\) when clear from context |
| \(A \sim p\) | the random variable \(A\) is distributed according to distribution \(p\). For example, \(X \sim \mathcal{N}(0,1)\) states that the random variable \(X\) is drawn from a normal distribution with zero mean and unit variance. |
| \(A \mid B \sim p\) | conditioned on the random variable \(B\), \(A\) is distributed according to \(p\). |

### Machine learning

| Symbol | Meaning |
| --- | --- |
| \(\Psi(x^{(i)}, y)\) | the score for assigning label \(y\) to instance \(i\) |
| \(f(x^{(i)}, y)\) | the feature vector for instance \(i\) with label \(y\) |
| \(\theta\) | a (column) vector of weights |
| \(\ell^{(i)}\) | loss on an individual instance \(i\) |
| \(L\) | objective function for an entire dataset |
| \(\mathcal{L}\) | log-likelihood of a dataset |
| \(\lambda\) | the amount of regularization |
