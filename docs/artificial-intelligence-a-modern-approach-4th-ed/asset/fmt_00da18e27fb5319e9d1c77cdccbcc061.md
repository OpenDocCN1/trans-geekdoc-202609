
It is conceptually straightforward to convert any OUPM into a corresponding generative program. This generative program makes random choices for each number statement and for the value of each basic random variable whose existence is implied by the number statements. The main extra work that the generative program needs to do is to create data structures that represent the objects, functions, and relations of the possible worlds in the OUPM. These data structures are created automatically by the OUPM inference engine because the OUPM assumes that every possible world is a first-order model structure, whereas a typical PPL makes no such assumption.

The images in [Figure 18.12](#Chapter18-04.xhtml#fig18-12) can be used to get an intuitive understanding of the probability distribution `P(Ω)`: we see varying levels of noise, and in the less noisy images, we also see sequences of letters of varying lengths. Let `ω1` be the trace corresponding to the image in the top right corner of this figure, containing the letters ocflwe. If we unrolled this trace `ω1` into a Bayesian network, it would have 4,104 nodes: 1 node for the variable `n`; 6 nodes for the variables `letters[i]`; 1 node for the `noise-variance`; and 4,096 nodes for the pixels in `noisy-image`. We thus see that this generative program defines an open-universe probability model: the number of random choices it makes is not bounded a priori, but instead depends on the value of the random variable `n`.

## 18.4.3 Inference results

Let’s apply this model to interpret images of letters that have been degraded with additive noise. [Figure 18.13](#Chapter18-04.xhtml#fig18-13) shows a degraded image, along with results from three independent MCMC runs. For each run, we show a rendering of the letters contained in the trace after stopping the Markov chain. In all three cases the result is the letter sequence uncertainty, suggesting that the posterior distribution is highly concentrated on the correct interpretation.

×![](images/Fig-260.jpg)

Figure 18.13Noisy input image (top) and inference results (bottom) produced by three runs, each of 25 MCMC iterations, with the model from [Figure 18.11](#Chapter18-04.xhtml#fig18-11). Note that the inference process correctly identifies the sequence of letters.

Now let’s degrade the text further, blurring it enough that it is difficult for people to read. [Figure 18.14](#Chapter18-04.xhtml#fig18-14) shows the inference results on this more challenging input. This time, although MCMC inference appears to have converged on (what we know to be) the correct number of letters, the first letter is misidentified as a q and there is uncertainty about five of the ten following letters.

×![](images/Fig-261.jpg)

Figure 18.14Top: extremely noisy input image. Bottom left: with three inference results from 25 MCMC iterations with the independent-letter model from [Figure 18.11](#Chapter18-04.xhtml#fig18-11). Bottom right: three inference results with the letter bigram model from [Figure 18.15](#Chapter18-04.xhtml#fig18-15). Both models exhibit ambiguity in the results, but the latter model’s results reflect prior knowledge of plausible letter sequences.

At this point, there are many possible ways to interpret the results. It could be that MCMC inference has mixed well and the results are a good reflection of the true posterior given the model and the image; in that case, the uncertainty in some of the letters and the error in the first letter are unavoidable. To get better results, we might need to improve the text model or reduce the noise level. It could also be that MCMC inference has not mixed properly: if we ran 300 chains for 25 thousand or 25 million iterations, we might find a quite different distribution of results, perhaps indicating that the first letter is probably u rather than q.

Running more inference could be costly in terms of dollars and waiting time. Moreover, there is no foolproof test for convergence of Monte Carlo inference methods. We could try to improve the inference algorithm, perhaps by designing a better proposal distribution for MCMC or using bottom-up clues from the image to suggest better initial hypotheses. These improvements require additional thought, implementation, and debugging. The third alternative is to improve the model. For example, we could incorporate knowledge about English words, such as the probabilities of letter pairs. We now consider this option.

## 18.4.4 Improving the generative program to incorporate a Markov model

Probabilistic programming languages are modular in a way that makes it easy to explore improvements to the underlying model. [Figure 18.15](#Chapter18-04.xhtml#fig18-15) shows the generative program for an improved model that generates letters sequentially rather than independently. This generative program uses a Markov model that draws each letter given the previous letter, with transition probabilities estimated from a reference list of English words.

×![](images/Fig-262.jpg)

Figure 18.15Generative program for an improved optical character recognition model that generates letters according to a letter bigram model whose pairwise letter frequencies are estimated from a list of English words.

[Figure 18.12](#Chapter18-04.xhtml#fig18-12) shows twelve sampled images produced by this generative program. Notice that the letter sequences are significantly more English-like than those generated from the program in [Figure 18.11](#Chapter18-04.xhtml#fig18-11). The right-hand panel in [Figure 18.14](#Chapter18-04.xhtml#fig18-14) shows inference results from this Markov model applied to the high-noise image. The interpretations more closely match the generating trace, though there is still some uncertainty.

## 18.4.5 Inference in generative programs

As with OUPMs, exact inference in generative programs is usually prohibitively expensive or impossible. On the other hand, it is easy to see how to perform rejection sampling: run the program, keep just the traces that agree with the evidence, and count the different query answers found in those traces. Likelihood weighting is also straightforward: for each generated trace, keep track of the weight of the trace by multiplying all the probabilities of the values observed along the way.

Likelihood weighting works well only when the data are reasonably likely according to the model. In more difficult cases, MCMC is usually the method of choice. MCMC applied to probabilistic programs involves sampling and modifying execution traces. Many of the considerations arising with OUPMs also apply here; in addition, the algorithm has to be careful about modifications to an execution trace, such as changing the outcome of an if-statement, that may invalidate the remainder of the trace.

Further improvements in inference come from several lines of work. Some improvements can produce fundamental shifts in the class of problems that are tractable with a given PPL, even in principle; lifted inference, described earlier for RPMs, can have this effect. In many cases, generic MCMC is too slow, and special-purpose proposals are needed to enable the inference process to mix quickly.

An important focus of recent work in PPLs has been to make it easy for users to define and use such proposals so that the efficiency of PPL inference matches that of custom inference algorithms devised for specific models.

Many promising approaches are aimed at reducing the overhead of probabilistic inference. The compilation idea described for Bayes nets in [Section 13.4.3](#Chapter13-04.xhtml#sec13-4-3) can be applied to inference in OUPMs and PPLs, and typically yields speedups of two to three orders of magnitude. There have also been proposals for special-purpose hardware for algorithms such as message-passing and MCMC. For example, Monte Carlo hardware exploits low-precision probability representations and massive fine-grained parallelism to deliver 100-10,000x improvements in speed and energy efficiency.
