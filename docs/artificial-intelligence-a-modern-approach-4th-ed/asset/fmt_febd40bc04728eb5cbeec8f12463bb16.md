
Within AI, `AUTOCLASS`(Cheeseman et al., 1988; Cheeseman and Stutz, 1996) was the first successful system that used `EM` for mixture modeling. `AUTOCLASS` was applied to a number of real-world scientific classification tasks, including the discovery of new types of stars from spectral data (Goebel et al., 1989) and new classes of proteins and introns in DNA/protein sequence databases (Hunter and States, 1992).

For maximum-likelihood parameter learning in Bayes nets with hidden variables, `EM` and gradient-based methods were introduced around the same time by Lauritzen (1995) and Russell et al. (1995). The structural `EM` algorithm was developed by Friedman (1998) and applied to maximum-likelihood learning of Bayes net structures with latent variables. Friedman and Koller (2003) describe Bayesian structure learning. Daly et al. (2011) review the field of Bayes net learning, providing extensive citations to the literature.

The ability to learn the structure of Bayesian networks is closely connected to the issue of recovering causal information from data. That is, is it possible to learn Bayes nets in such a way that the recovered network structure indicates real causal influences? For many years, statisticians avoided this question, believing that observational data (as opposed to data generated from experimental trials) could yield only correlational information—after all, any two variables that appear related might in fact be influenced by a third, unknown causal factor rather than influencing each other directly. Pearl (2000) has presented convincing arguments to the contrary, showing that there are in fact many cases where causality can be ascertained and developing the causal network formalism to express causes and the effects of intervention as well as ordinary conditional probabilities.

Nonparametric density estimation, also called Parzen window density estimation, was investigated initially by Rosenblatt (1956) and Parzen (1962). Since that time, a huge literature has developed investigating the properties of various estimators. Devroye (1987) gives a thorough introduction. There is also a rapidly growing literature on nonparametric Bayesian methods, originating with the seminal work of Ferguson (1973) on the `Dirichlet process`, which can be thought of as a distribution over Dirichlet distributions. These methods are particularly useful for mixtures with unknown numbers of components. Ghahramani (2005) and Jordan (2005) provide useful tutorials on the many applications of these ideas to statistical learning. The text by Rasmussen and Williams (2006) covers the `Gaussian process`, which gives a way of defining prior distributions over the space of continuous functions.

`Dirichlet process`
`Gaussian process`

The material in this chapter brings together work from the fields of statistics and pattern recognition, so the story has been told many times in many ways. Good texts on Bayesian statistics include those by DeGroot (1970), Berger (1985), and Gelman et al. (1995). Bishop (2007), Hastie et al. (2009), Barber (2012), and Murphy (2012) provide excellent introductions to statistical machine learning. For pattern classification, the classic text for many years has been Duda and Hart (1973), now updated (Duda et al., 2001). The annual NeurIPS (Neural Information Processing Systems, formerly NIPS) conference, whose proceedings are published as the series Advances in Neural Information Processing Systems, includes many Bayesian learning papers, as does the annual conference on Artificial Intelligence and Statistics. Specifically Bayesian venues include the Valencia International Meetings on Bayesian Statistics and the journal Bayesian Analysis.

[1](#Chapter21-01.xhtml#sup21_1)Statistically sophisticated readers will recognize this scenario as a variant of the urn-and-ball setup. We find urns and balls less compelling than candy.

[2](#Chapter21-01.xhtml#sup21_2)We stated earlier that the bags of candy are very large; otherwise, the `i.i.d.` assumption fails to hold. Technically, it is more correct (but less hygienic) to rewrap each candy after inspection and return it to the bag.

[3](#Chapter21-02.xhtml#sup21_3)They are called hyperparameters because they parameterize a distribution over `θ`, which is itself a parameter.

[4](#Chapter21-02.xhtml#sup21_4)Other conjugate priors include the Dirichlet family for the parameters of a discrete multivalued distribution and the `Normal–Wishart` family for the parameters of a Gaussian distribution. See Bernardo and Smith (1994).

[5](#Chapter21-03.xhtml#sup21_5)It is better in practice to choose them randomly, to avoid local maxima due to symmetry.

# CHAPTER 22
## DEEP LEARNING

In which gradient descent learns multistep programs, with significant implications for the major subfields of artificial intelligence.

Deep learning is a broad family of techniques for machine learning in which hypotheses take the form of complex algebraic circuits with tunable connection strengths. The word “deep” refers to the fact that the circuits are typically organized into many layers, which means that computation paths from inputs to outputs have many steps. Deep learning is currently the most widely used approach for applications such as visual object recognition, machine translation, speech recognition, speech synthesis, and image synthesis; it also plays a significant role in reinforcement learning applications (see [Chapter 23](#Chapter23-00.xhtml)).

`Deep learning`
`Layer`

Deep learning has its origins in early work that tried to model networks of neurons in the brain (McCulloch and Pitts, 1943) with computational circuits. For this reason, the networks trained by deep learning methods are often called neural networks, even though the resemblance to real neural cells and structures is superficial.

`Neural network`

While the true reasons for the success of deep learning have yet to be fully elucidated, it has self-evident advantages over some of the methods covered in [Chapter 19](#Chapter19-00.xhtml)—particularly for high-dimensional data such as images. For example, although methods such as linear and logistic regression can handle a large number of input variables, the computation path from each input to the output is very short: multiplication by a single weight, then adding into the aggregate output. Moreover, the different input variables contribute independently to the output, without interacting with each other ([Figure 22.1(a)](#Chapter22-00.xhtml#fig22-1)). This significantly limits the expressive power of such models. They can represent only linear functions and boundaries in the input space, whereas most real-world concepts are far more complex.

Description
A grid with four columns and three rows is shown. The columns are numbered 1 to 4 from left to right. The rows are labeled 1 to 3 from bottom to top. Each cell depicts a state. The actions inside each state are as follows. State (1, 1): Upward arrow. State (1, 2): Upward arrow. State (1, 3): Right-headed arrow. State (2, 1): left-headed arrow. State (2, 2): Highlighted in blue. State (2, 3): Right-headed arrow. State (3, 1): left-headed arrow and an upward arrow. State (3, 2): upward arrow. State (3, 3): Right-headed arrow. State (4, 1): left-headed arrow. State (4, 2): A block labeled negative 1. State (4, 3): A block labeled positive 1.

×![](images/Fig-320.jpg)

Figure 22.1(a) A shallow model, such as linear regression, has short computation paths between inputs and output. (b) A decision list network ([page 692](#Chapter19-05.xhtml#page_692)) has some long paths for some possible input values, but most paths are short. (c) A deep learning network has longer computation paths, allowing each variable to interact with all the others.
