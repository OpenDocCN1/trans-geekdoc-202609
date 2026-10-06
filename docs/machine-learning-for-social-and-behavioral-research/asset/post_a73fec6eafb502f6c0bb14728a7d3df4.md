
# Machine Learning for Social and Behavioral Research

with the whole. However, in some cases this does not work. For instance, Saucier and Iurino (2020) derived a high-dimensional personality structure of a natural-language lexicon. From this high-dimensional structure they were able to identify the Big Five from within this structure, but the converse did not hold, as they were unable to zoom out and expand from the Big Five structure to the high-dimensional structure.

## 2.5.2 Level of Hypothesis

Most researchers describe a hypothesis as a specific, well-formulated statement. The part of the motivation for this stems from the philosophy of science’s fixation on hard sciences, such as physics, where general laws take mathematical forms. In reality, particularly in social and behavioral research, “a pure emotion — nothing but an outpouring of alternative ideas and a consuming curiosity about a certain aspect of the world” (Cattell, 1966). A further problem with the term is its generalization from an introduction to statistics formulation (i.e., $H_0 = \text{no effect}$) to match theoretical formulations. A hypothesis taking the form of a single sentence necessarily demands some form of reductionism from theory, whereas a hypothesis matching the degree of theoretical complexity would require at the very least a paragraph of formulation. Even with the more recent calls to match mathematical structures in the areas of computational modeling (e.g., Fried & Robinaugh, 2020), the degree of complexity necessitates some degree of simplification (DeYoung & Kruger, 2020).

In more traditional social and behavioral research, stating hypotheses takes the form of whether or not an effect is zero. This typically refers to the influence of a single variable, often a grouping resulting from an experimental manipulation. Other times, nonexperimental research may report hypotheses that refer to whether a regression coefficient is nonzero, which can become more complex in the presence of more than one predictor. In research settings such as these, where the number of variables is small, it is relatively straightforward to state and test hypotheses. Factors in more contemporary research make this process more complex: larger numbers of variables and the ease of specifying models with complex relationships. Simply put, the more variables in an analysis, the more complicated it is to test a purely confirmatory model. This process is eased if the majority of the variables are included as *confounders*; however, controlling for these variables is more complex than researchers assume (Westfall & Yankoni, 2016).

Next, we discuss complications in the use of hypothesis testing with large numbers of variables. The most common way which this occurs is with the specification of theoretically informed models, often through the use of a SEM.

# The Principles of Machine Learning Research

## FIGURE 2.5. Figures depicting two different mediation models.

![](img/5047f0f064e22688ceb5d0cdfaf3e964_47_0.png)

In contrast to a model that includes paths between all variables, thus fitting covariance (correlation) matrix perfectly, one often involves the placement of constraints in the model based on theory, often taking the forming of removing paths between variables (i.e., setting these parameters to 0). One of the most common models is a mediation model, examples of which are displayed in Figure 2.5.

In this figure, the left panel depicts a full mediation model. More, though, is that this is a saturated model — every variable has a relationship (without worry about the direction of the arrows) with every other variable. Saturated models have no misfit. In contrast, the right panel has one arrow removed between X and Y, representing a constraint that the direct relationship between X and Y is 0. There can still be an indirect relationship between X and Y, although an indirect path through M. Our purpose in describing both models is that they represent different theoretical ideas, which can be generalized to models containing more variables, and different forms of relationships (e.g., nonlinear).

This forming of modeling requires a higher degree of specification because each path needs to have a justification, and the model as a whole must relate to a specific hypothesis. However, a large number of variables can be related to a specific hypothesis. This increased flexibility allows not only for the input of theory, but also for balancing the specification of theoretical relationships with uncertainty as the types of relationships in other parts of the model. The default label assigned to the statistical analysis of numbers of variables is exploration, as inputting theory into the model is rarely in practice. We discuss this in Chapter 8, but first demonstrate it with the model depicted in Figure 2.6.

## 2.5.3 Example

To make our perspective more clear as it relates to larger models, we work with the model depicted in Figure 2.6. Part of the issue is that recent papers or books on the application of machine learning for social and behavioral research make little to no mention of the role of theory. For instance, Dwyer et al. (2018) only mention the role of theory in making decisions regarding outcomes.

# The Principles of Machine Learning Research

**FIGURE 2.7.** Relatively simple example depicting two different models with uncertainty with respect to specific parameters.

![](img/5047f0f064e22688ceb5d0cdfaf3e964_49_0.png)

While a number of articles discuss the role of machine learning in theory building or refinement (e.g., Chapman, Weiss, Duberstein, 2016), very little detail is given with regard to how this is achieved. In fact, a large amount of research acknowledges that theory generation, refinement, and any form of acceptance/confirmation is a long process; very little detail is given regarding the intermediate stages, and what types of methods are most appropriate for refining a nascent theory. This stage of theory refinement does not fit neatly into being described as inductive, hypothetic-deductive, or abductive, or to the concepts of exploration and confirmation. The closest parallel is that of Bayesian updating; however, most applications in reality deal with simple forms of modeling (for counters, see Gelman, 2004). To address this, some recent publications have characterized their proposed methods that do not fit into any of these boxes as semi-confirmatory (Huang, Chen, & Wen, 2017). The question is whether refining makes sense. To confirm, one would use hypothetical-deductive reasoning to appraise a theoretical model. To translate from strict confirmation to something that is not fully exploratory, there are two possible routes. The first is that the theoretical model evidences a significant level of misfit and therefore discounts the theory. Second, one could acknowledge uncertainty with respect to part of the model at the outset, and include this as part of the theoretical specification.

A more simplistic example than is depicted in Figure 2.6 is displayed in Figure 2.7.

The left panel depicts a simplistic timepoint model, where each variable has an autoregressive relationship within, with uncertainty regarding the coupling relationship from $X_{i-1}$ to $Y_i$, and from $Y_{i-1}$ to $X_i$. However, this degree of uncertainty as manifested in two paths is something that relates to what a hypothesis would address, as in the simplest case

# Machine Learning for Social and Behavioral Research

regarding a nonpresence of a relationship for both paths. The left panel of 2.7 is contrasted with the right panel, where a mediation model is specified, and there is uncertainty regarding the influence of a large number of covariates. Modeling of this nature could progress in two ways, either as a one-step or two-step process, with the distinction relying on whether the mediation component needs to be assessed. In practice, it is likely that the mediation model already has support, and researchers wish to expand the theory to include potential confounding into account, or variables could possibly account for heterogeneity. As such, this example is better conceptualized as confirmatory, with a less specific hypothesis. To specify this model, one would first have to posit the potential for heterogeneity, collect these variables as part of the study design, and include these effects in the statistical model.

We view a more productive way to think about modeling in general, and more specifically, the role of machine learning in social and behavioral research is to eschew the labels of exploratory and confirmatory, and instead describe the goals of research as either following theory generation, development, or appraisal (see Haig, 2014). Further, these three phases of theory construction are clearly aligned with the goal of explanation, of which there is less of a clear footing for the underlying goals when
