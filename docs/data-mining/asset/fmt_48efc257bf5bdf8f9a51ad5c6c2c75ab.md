
The `K2` algorithm for learning Bayesian networks was introduced by [Cooper and Herskovits (1992)](#References_705-736_B978044315888900025X.xhtml#fur111). Bayesian scoring metrics are covered by [Heckerman et al. (1995)](#References_705-736_B978044315888900025X.xhtml#fur259). [Friedman, Geiger, and Goldszmidt (1997)](#References_705-736_B978044315888900025X.xhtml#fur198) introduced the tree augmented Naïve Bayes algorithm and also describe multinets. [Grossman and Domingos (2004)](#References_705-736_B978044315888900025X.xhtml#fur236) show how to use the conditional likelihood for scoring networks. [Guo and Greiner (2004)](#References_705-736_B978044315888900025X.xhtml#fur239) present an extensive comparison of scoring metrics for Bayesian network classifiers. [Bouckaert (1995)](#References_705-736_B978044315888900025X.xhtml#fur55) describes averaging over subnetworks. `AODEs` are described by [Webb, Boughton, and Wang (2005)](#References_705-736_B978044315888900025X.xhtml#fur555) and `AnDEs` by [Webb et al. (2012)](#References_705-736_B978044315888900025X.xhtml#fur556). `AD trees` were introduced and analyzed by [Moore and Lee (1998)](#References_705-736_B978044315888900025X.xhtml#fur403)—the same Andrew Moore whose work on `kD-trees` and ball trees was mentioned in [Section 4.10](#Ch004_91-164_B9780443158889000054_a.xhtml#s0200). [Komarek and Moore (2000)](#References_705-736_B978044315888900025X.xhtml#fur326) introduce `AD trees` for incremental learning that are also more efficient for data sets with many attributes.

The `AutoClass` program is described by [Cheeseman and Stutz (1995)](#References_705-736_B978044315888900025X.xhtml#fur91). Two implementations have been produced: the original research implementation, written in the `LISP` (“list processing”) programming language, and a follow-up public implementation in `C` that is 10 or 20 times faster but somewhat more restricted—only the normal distribution model is implemented for numeric attributes. `DensiTrees` were developed by [Bouckaert (2010)](#References_705-736_B978044315888900025X.xhtml#fur57).

Kernel density estimation is an effective and conceptually simple probabilistic model. [Epanechnikov (1969)](#References_705-736_B978044315888900025X.xhtml#fur160) showed the optimality of the `Epanechnikov` kernel under the mean-squared error metric. [Jones, Marron, and Sheather (1996)](#References_705-736_B978044315888900025X.xhtml#fur297) recommend using a so-called “plug-in” estimate to select the kernel bandwidth. [Duda and Hart (1973)](#References_705-736_B978044315888900025X.xhtml#fur148) and [Bishop (2006)](#References_705-736_B978044315888900025X.xhtml#fur44) show theoretically that kernel density estimation converges to the true distribution as the amount of data grows.

## 13.5 Exercises

*   13.1 Maximum likelihood estimation maximizes the likelihood function `L`(`θ`; `x[1]`, `x[2]`, …, `x[n]`)<mml:math><mml:mi>L</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mi>&#952;</mml:mi><mml:mi>;</mml:mi><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mn>1</mml:mn></mml:mrow></mml:msub><mml:mo>,</mml:mo><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msub><mml:mo>,</mml:mo><mml:mo>&#8230;</mml:mo><mml:mo>,</mml:mo><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mi>n</mml:mi></mml:mrow></mml:msub><mml:mo stretchy="false">)</mml:mo></mml:math>![Equation](images/F000145si87.png) with respect to _____.

    1.  A. the data `x[1]`, `x[2]`, …, `x[n]`<mml:math><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mn>1</mml:mn></mml:mrow></mml:msub><mml:mo>,</mml:mo><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msub><mml:mo>,</mml:mo><mml:mo>&#8230;</mml:mo><mml:mo>,</mml:mo><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mi>n</mml:mi></mml:mrow></mml:msub></mml:math>![Equation](images/F000145si88.png)

    2.  B. the parameters `θ`<mml:math><mml:mi mathvariant="normal">&#952;</mml:mi></mml:math>![Equation](images/F000145si89.png)

*   13.2 Maximizing the likelihood function is equivalent to minimizing the log-likelihood function.

    1.  A. True

    2.  B. False

*   13.3 A Bayesian network is drawn as a network of nodes, one for each attribute, where the network is a _____.

    1.  A. bipartite graph

    2.  B. complete graph

    3.  C. directed acyclic graph

    4.  D. minimum weight spanning tree

*   13.4 Consider the graph in [Fig. 13.3](#Ch014_485-514_B9780443158889000145.xhtml#f0020). (Ignore the box, which indicates the Markov blanket of node `x[6]`<mml:math><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mn>6</mml:mn></mml:mrow></mml:msub></mml:math>![Equation](images/F000145si90.png).)

    1.  1. Write down the joint distribution of this Bayesian network model.(Recall that $P(A_{1},A_{2},\\ldots,A_{n}) = \\prod\\limits_{i = 1}^{n}{P(A_{i}\\text{∣}{Parents}(A_{i}))},$<mml:math><mml:mi>P</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:msub><mml:mrow><mml:mi>A</mml:mi></mml:mrow><mml:mrow><mml:mn>1</mml:mn></mml:mrow></mml:msub><mml:mo>,</mml:mo><mml:msub><mml:mrow><mml:mi>A</mml:mi></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msub><mml:mo>,</mml:mo><mml:mo>&#8230;</mml:mo><mml:mo>,</mml:mo><mml:msub><mml:mrow><mml:mi>A</mml:mi></mml:mrow><mml:mrow><mml:mi>n</mml:mi></mml:mrow></mml:msub><mml:mo stretchy="false">)</mml:mo><mml:mo>=</mml:mo><mml:munderover><mml:mo>&#8719;</mml:mo><mml:mrow><mml:mi>i</mml:mi><mml:mo>=</mml:mo><mml:mn>1</mml:mn></mml:mrow><mml:mrow><mml:mi>n</mml:mi></mml:mrow></mml:munderover><mml:mrow><mml:mi>P</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:msub><mml:mrow><mml:mi>A</mml:mi></mml:mrow><mml:mrow><mml:mi>i</mml:mi></mml:mrow></mml:msub><mml:mtext mathvariant="normal">&#8739;</mml:mtext><mml:mi mathvariant="normal">Parents</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:msub><mml:mrow><mml:mi>A</mml:mi></mml:mrow><mml:mrow><mml:mi>i</mml:mi></mml:mrow></mml:msub><mml:mo stretchy="false">)</mml:mo><mml:mo stretchy="false">)</mml:mo></mml:mrow><mml:mo>,</mml:mo></mml:math>![Equation](images/F000145si91.png) for all Bayesian networks.)

    2.  2. How many rows are there in the conditional probability table for node `x[9]`<mml:math><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mn>9</mml:mn></mml:mrow></mml:msub></mml:math>![Equation](images/F000145si92.png)? Assume all variables are binary and take on values in {0, 1}<mml:math><mml:mo stretchy="false">{</mml:mo><mml:mn>0,1</mml:mn><mml:mo stretchy="false">}</mml:mo></mml:math>![Equation](images/F000145si93.png).

    3.  3. Which nodes are in the Markov blanket of `x[3]`<mml:math><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mn>3</mml:mn></mml:mrow></mml:msub></mml:math>![Equation](images/F000145si94.png)?

    4.  4. Which nodes are in the Markov blanket of `x[5]`<mml:math><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mn>5</mml:mn></mml:mrow></mml:msub></mml:math>![Equation](images/F000145si95.png)?

*   13.5 Come up with a Bayesian network for the grade a student gets in a Data Mining course.

    1.  1. What are the nodes/variables in your model?

    2.  2. What is the DAG structure?

    3.  3. Do the conditional independencies in your DAG match your intuitions about the world?

*   13.6 In a dice game I made up the goal is to get a high total from several rolls of a die. First, the player rolls a die. If the die roll is even and/or the player is at most 7 years old, they roll the die again. If they are older than 7 years of age, and the first two rolls were both even, the player rolls the die a third time. The player’s score is the total of all die rolls. We will suppose that 10% of the population is at most 7 years of age. The die is standard, that is, it is six-sided and unbiased.
