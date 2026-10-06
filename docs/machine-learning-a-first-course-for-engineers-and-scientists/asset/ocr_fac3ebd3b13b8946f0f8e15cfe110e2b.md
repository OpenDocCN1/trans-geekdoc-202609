# 12 Ethics in machine learning

In practice such a balance may be difficult to achieve, but our purpose is to show that limitations exist even when we control our model in this. Similarly, let's assume we can specify that the model has the same true positive rate (recall) for all categories.

```
$t_1 = \frac{p_1t_2}{p_2}, \quad (12.2)$
```

Equal precision of the model for both categories is determined by $t_1/(t_1+f_1) = t_2/(t_2+f_2)$. Substituting (12.1) and (12.2) in this equality:

```
$t_2 + \frac{p_1f_2}{n_1} = \frac{t_2}{t_2+f_2}$
```

which holds only if $f_1 = f_2 = 0$ or if

```
$\frac{p_1}{n_1} = \frac{p_2}{n_2} \quad (12.3)$
```

In words, Equation (12.3) implies that we can achieve equal precision when the classifier is on the positive class or rate of people in the positive and negative classes for both categories is equal. Both of these conditions are beyond our control as modelers. In particular, the number in each category is, as we stated, determined by the real world. Men and women suffer different medical conditions at rates; young and old people have different interests in advertised products; ethnicities experience different levels of systemic racism. These differences cannot be eliminated by a model.

In general, our analysis shows that it is possible to achieve equality in precision, true positive and false rate. If we set our parameters so our model is fair for two of these classes, then we can satisfy the condition of (12.3) as a consequence of the third. Unless the positive and negative classes occur at the same rate for both then achieving fairness in all three is impossible. The result above has been refined by Kleinberg and colleagues, who include properties of the classifier, f(x) in their derivation (Kleinberg et al. 2018).

Various methods have been suggested by researchers to achieve results as close as possible to all three criteria. We do not, discuss them here, for one simple reason: We wish to emphas that 'fairness' is not primarily a technical problem. The ethics through awareness paradigm empowers our responsibility to be aware of these limitations and explain them to clients and a joint decision should be made to navigate the pitfalls.

# 12.2 Misleading claims about performance

Machine learning is one of the most rapidly growing fields of research and has led to many new applications. With this rapid development hyperbolic claims about what the techniques can achieve. Much of the research in machine learning is conducted by large companies like Google, Microsoft and Facebook. The day to day of these companies' research departments is independent of commercial operations, they also have public relations departments whose goal is to engage the wider public in the research conducted. As a result, research is (part) a form of advertising for these companies. In 2017, Google DeepMind found a new way, using convolutional networks, of scaling up reinforcement learning approach previously successful in producing unbiased strategies for backgaming to the Go and Chess. The breakthrough was highly promoted by the company as a game-changer in Artificial Intelligence. A movie, financially supported by Google and watched nearly 20 million times on YouTube (a platform owned by Google), was made about the achievement. Regardless of the merit of the technical development, the point here is that research

Tesla is an engineer and at time of writing the richest man in the world, has made multiple claims about machine learning that simply do not get up closer. In May 2020 he met that Tesla