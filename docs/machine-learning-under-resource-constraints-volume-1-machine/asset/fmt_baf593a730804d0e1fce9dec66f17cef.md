
This is based on git commit hash `7b2ad66e4a89229f6be392e73c1bda21e2b01434`.[↩](#fnref5)

6.

[http://sfb876.tu-dortmund.de/mobidata](http://sfb876.tu-dortmund.de/mobidata).[↩](#fnref6)

7.

The number of passes is often relaxed to a small constant or logarithmic amount for problems where single pass algorithms are impossible to obtain or where a multi pass algorithm allows significantly improved results over what is possible in a single pass.[↩](#fnref7)

8.

The code for these experiments is available under <https://github.com/sbuschjaeger/SubmodularStreamingMaximization/>.[↩](#fnref8)

9.

Here, `a ∝ b` means that there exists a constant `c` > 0 such that `a` = `cb`.[↩](#fnref9)

10.

In general, one may consider indicator functions not only for nodes and edges, but for all cliques (fully connected subgraphs) in `G`. Our description still applies to higher order models, since we can convert them into models using only nodes and edges [692, Appendix E].[↩](#fnref10)

11.

Notice that when the underlying state space `𝒳` is discrete, then `ν` is the counting measure and we may identify the density `p` with the measure `P`.[↩](#fnref11)

12.

An unitriangular matrix is triangular and all entries on its main diagonal are 1.[↩](#fnref12)

13.

An implementation is part of the Python package `pxpy` which is available at <https://pypi.org/project/pxpy>.[↩](#fnref13)

14.

Depending on the context, slightly different definitions are used in the literature. Often, they require that `a` and `b` be distributions.[↩](#fnref14)

15.

For clarity of presentation we omit biases.[↩](#fnref15)

16.

For clarity of presentation we omit biases.[↩](#fnref16)

17.

GitHub repository: <https://github.com/rusty1s/pytorch_geometric>.[↩](#fnref17)

18.

<https://www.lido.tu-dortmund.de/cms/de/LiDO3/9783110785944-011>, accessed June 9, 2022.[↩](#fnref18)

19.

<http://pizzachili.dcc.uchile.cl/>, accessed June 9, 2022.[↩](#fnref19)

20.

<http://pizzachili.dcc.uchile.cl/>, accessed June 9, 2022.[↩](#fnref20)

21.

<https://www.w3.org/TR/MathML3/>.[↩](#fnref21)

22.

<https://arxiv.org/help/bulk_data_s3>.[↩](#fnref22)

23.

<http://katex.org>.[↩](#fnref23)

24.

You can find the datasets used in this study at <http://github.com/Whadup/arxiv-learning>. We also share our citation graph, which might be interesting in other applications.[↩](#fnref24)

25.

Crowd-sourced evaluation data can be accessed and edited here: <https://www.overleaf.com/8721648589nrjxgwmtzfvm>.[↩](#fnref25)

26.

An ambient space is the space surrounding an object, e.g. here `R^d`.[↩](#fnref26)

27.

It may be that such a matching exists in the limit only. This technicality is removed using a slight perturbation of the function. See a proof in the paper by Buchin et al. [[97]](#backmatter-001.xhtml#b_9783110785944-010_ref_097).[↩](#fnref27)

28.

The continuous Fréchet distance is a pseudo-metric, since two different functions can be at the distance 0. This can be easily repaired by observing the equivalence classes of functions, and thus we say that the Fréchet distance is also a metric.[↩](#fnref28)

29.

The Strong Exponential Time Hypothesis (SETH) claims that there is no `η` > 0, such that there is an algorithm for all `k`, that answers if a formula in conjunctive normal form with `N` variables, and whose claims have at most `k` literals, is satisfiable, in time `O` ((2 − `η`)^`N`). SETH is a fruitful tool for showing conditional lower bounds. It was used to show similar claims for the DTW distance as well.[↩](#fnref29)

30.

For each of these problems the discrete version of the problem can be observed. There the set of centers `C` needs to be a subset of `P`. In particular, the discrete `k`-median is known as the `k`-medoid problem.[↩](#fnref30)

31.

The doubling dimension of a metric space is the smallest positive integer `d` such that every ball of the metric space can be covered by 2^`d` balls of half the radius, cf. [[281]](#backmatter-001.xhtml#b_9783110785944-010_ref_281).[↩](#fnref31)

32.

The tilde-notation `Õ(X)` hides polylogarithmic factors in `X`, i.e. `Õ(X)` = `O` (`X` polylog(`X`)).[↩](#fnref32)

33.

A sequence `S'` is a supersequence of the sequence `S''` if `S''` is a subsequence of `S'`.[↩](#fnref33)

34.

This is because the array size reaches the 2^(31) array length limit of Java.[↩](#fnref34)

35.

The matrix `U[·ℛ]` contains all columns of `U` whose index is in the set `ℛ`.[↩](#fnref35)

36.

<http://hpc.isti.cnr.it/~claudio/web/archives/20131113/9783110785944-011>.[↩](#fnref36)

37.

<http://qwone.com/~jason/20Newsgroups/>.[↩](#fnref37)

38.

<https://github.com/Henning1/dogqc>.[↩](#fnref38)

39.

See e.g. Bartlett, Jordan, and McAuliffe [[44]](#backmatter-001.xhtml#b_9783110785944-010_ref_044). Intuitively, this means that a classifier that minimizes `ℓ[BC]` also minimizes the binary 0-1 loss.[↩](#fnref39)

40.

The margin of an instance denotes how far its score is from the classification boundary. An instance with a margin of 0 is classified correctly, but the slightest perturbation of its features or the classifier's weights could change the classification.[↩](#fnref40)

41.

Computational resources provided by CSC – IT Center for Science, Finland.[↩](#fnref41)

42.

Given that the computations are memory-bound, even when running with 128 cores the execution ports of the CPU will be idle for a significant amount of time. Only moderate downclocking to ≈ 3.18 GHz occurred in our setup.[↩](#fnref42)

43.

ARM big.LITTLE Technology: <https://developer.arm.com/technologies/big-little> (accessed Feb. 22nd, 2022).[↩](#fnref43)

44.

<https://towardsdatascience.com/teslas-deep-learning-at-scale-7eed85b235d3>.[↩](#fnref44)

45.

<https://www.kdnuggets.com/2016/01/anthony-goldbloom-secret-winning-kaggle-competitions.html>.[↩](#fnref45)

46.

Please note that the problem is not limited to BFS. Here we point out the demand of considering the access pattern when allocating nodes to memory.[↩](#fnref46)

47.

We adopted GNU C++ (g++) compiler version 4.8.3 for ARM, version 4.9.2 for PPC, and version 5.4.0 for Intel with `-O0` option.[↩](#fnref47)

48.

Although the instructions generated by the compiler may differ due to aggressive compiler optimization (O3) compared with the presented node sizes (O0 optimization) in Table 7.7, the code generator at the end selects the O3 option to accelerate the realizations as much as possible.[↩](#fnref48)

49.

We use the term `scratchpad memory` to disambiguate `shared memory` for CUDA and `local memory` for OpenCL.[↩](#fnref49)

50.

We measured 146.1 GB/s GPU global memory bandwidth in a host system with 16 GB/s bidirectional PCIe bandwidth.[↩](#fnref50)

51.

We could not process SSB Query 2.2 as we do not yet support range predicates on dictionary compressed columns.[↩](#fnref51)

52.

A clique corresponds to a fully connected subgraph.[↩](#fnref52)

53.

It is assumed that every training instance in `𝒟` is fully observed.[↩](#fnref53)

54.

<https://pypi.org/project/pxpy>.[↩](#fnref54)
