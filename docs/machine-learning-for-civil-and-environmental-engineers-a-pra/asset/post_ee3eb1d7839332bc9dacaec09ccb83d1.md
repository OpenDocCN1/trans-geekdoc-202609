
## 10 Recommendations, Suggestions, and Best Practices

> What would a mistake here be like?
> Ludwig Wittgenstein

### Synopsis

Now that we are inching toward the end of this textbook, I find it timely to list and talk about some recommendations, suggestions, and best practices that can come in handy in an ML-based investigation. These are not meant to be followed to the teeth but rather are presented herein as I have found them to be of aid in some, if not most, of my group's work, as well as those I had the pleasure to meeting/reading their works.¹

Before we dive into this chapter, let us start by distinguishing between what this chapter refers to as recommendations, suggestions, and best practices:²

- A recommendation is an advice that has been duly noted in the open literature. Often, a recommendation comprises a general statement.
- A suggestion is a proposition of opinion (and may largely stem from personal experiences).
- A best practice is a trend that has been commonly accepted by publications in our domain. The origin of a best practice could have been arrived at systematically, such as through a sensitivity study or empirical analysis or via heuristics (rules of thumb). Best practices tend to vary across timeframes and groups.

### 10.1 Recommendations

The following is a list of recommendations that could be of aid to civil and environmental engineers interested in adopting ML.

#### 10.1.1 Continue to Learn

My favorite recommendation revolves around learning. At a fundamental level, we are public servants wherein our role is to maintain the well-being of our society. To stay up to date with the latest advancement, we ought to continue to learn. In a way, we have a duty for lifelong education – especially one that stretches beyond the award of our degrees. This continued learning ensures that we are aware of new methods, building code provisions, and the latest advancements in our areas. The above is notably true given that a civil and environmental engineering course plan does not and cannot cover every facet an engineer is expected to know and learn.

The rise of digitalization and automation³ has opened the door to developing new methods and procedures that could benefit us. While some might say that the rise of such modern technologies is disturbing the calmness of our domain, I tend to disagree. I view these as an opportunity to modernize and transform civil and environmental engineering. Think of it this way. If a form of technology already exists (say, drones) and has been shown to be more affordable and productive than existing (surveying) methods, then engineers will use it whether it is covered in a curriculum or not. By comparison, the notion that because ML is not an integrated component of current course plans, therefore, we do not need to learn ML, is simply flawed.

#### 10.1.2 Understand the Difference between Statistics and ML

Up to this point, most of the previous pages covered ideas and concepts of ML, and it has been a while since we visited Chapter 3, so let me switch gears and talk a bit about statistics. Statistical methods are “mathematical formulas, models, and techniques that are used in statistical analysis of raw research data” [1]. The primary goal of applying such methods is to extract insights from data and/or provide means to assess the robustness of research outputs. In a statistical analysis, a statistical model often assumes a pre-determined distribution to fit the input parameters to the result of a phenomenon [2]. In the event that the number of involved parameters increases or the relationship between them is evidently intricate, or the data does not satisfy assumptions/conditions tied with statistical methods, such methods become less effective – and possibly inapplicable [3].

Unlike statistical methods, ML makes minimal assumptions about the type and quality of data. ML looks for hidden patterns within data points and hence becomes effective when applied to unstandardized data or those with highly nonlinear interactions. A unique distinction between statistical methods and ML is that the former aims to satisfy a set of rules and assumptions, while the latter pursues to satisfy a penalization function [4]. Both statistical methods and ML can be used in predictions. However, it will take a much deeper analysis to explain predictions or arrive at causal effects.

#### 10.1.3 Know the Difference between Prediction via ML and Carrying Out Tests and Numerical Simulations

The goal of carrying out an experiment is to investigate a hypothesis or research question (say, what is the influence of X on Y?) [5, 6]. It is unfortunate that testing is a costly endeavor and continues to limit our capacity to fully explore phenomena.

So, we resort to a more affordable approach by augmenting our tests via numerical models [7]. First, a model is developed. This model is created based on first principles (i.e., those implemented into FE software) and then validated against the outcome of benchmarked tests [8, 9]. Since such a model satisfies first principles as well as matches well with our tests, then we can declare it valid and use it to understand the cause and effect governing the phenomenon on hand [10].

However, let us not forget that a FE model is a shell skeleton. Say, a model for a rectangular beam contains the geometrical model that describes the geometrical component and a material model that conveys the behavior of the material(s) within this beam. Thus, for the same geometry, a modeler can observe different responses (say, deflection) if the material model is varied between concrete, steel, and timber. In a way, the FE model does not recognize that we are trying to simulate a beam, but rather it solves the developed skeleton for deflection. While the same is also true for ML models, FE models solve our problems by first solving principles. This is not the case for the majority of ML models.

The procedure for creating traditional ML models comprises a three-step linear procedure: 1) collect data on a phenomenon, 2) apply an algorithm, and 3) declare that such an algorithm can predict the phenomenon on hand via fitness tests. As mentioned earlier, a traditional ML model is a Blackbox that we do not know why it predicts the way it does, nor how it ties the parameters to the outcome of the phenomenon! However, we know that the data drive the decision of such an algorithm, and we know that despite the model's fitness and robustness of data, a traditional ML model may not still agree with physics principles.⁵ This is critical to remember.

#### 10.1.4 Ask if You Need ML to Address the Phenomenon on Hand

It can be tempting to follow the latest trends in scholarly works. Trying new trends can be an exciting learning experience. However, blindly assuming such trends to be applicable to a phenomenon you happen to be interested in can be detrimental. The existence of a technology (in this case, ML) does not justify the need to favor it over other existing and well-established methods. We ought to learn, investigate, and explore where and how ML can help us.⁶

Another view to leveraging ML is to answer the following question: did we fully examine the data in our tests and simulations? It is quite plausible that we did not – especially since we know that traditional methods are constrained to certain assumptions and hence suffer from limitations [11, 12]. It is due to these assumptions and limitations that we may need to explore other means of investigation. This can be apparent in the evidence of many works that showcased how predictions from ML outperform those obtained from building code provisions and statistical methods [13, 14].

By noting how many of our problems resemble a closed-loop system wherein a number of parameters are associated with a response. Then, one can form a hypothesis that if we are to collect enough data on parameters and responses, we could potentially better understand our problems and create/optimize novel solutions to overcome such problems.⁷

#### 10.1.5 Establish a Crystal Clear Understanding of Model Assumptions, Outcomes, and Limitations

Data-driven approaches can be tremendously helpful for cases where we have plenty of data, such as the compressive strength of concrete as a function of its mixture proportions, water quality as a function of its chemical characteristics, etc.

A key assumption of data-driven ML is the availability of comprehensive and healthy datasets. This is a valid assumption and one that is commonly adopted whenever statistical methods are applied.⁸ Despite being blackboxes, ML models have been shown to perform well. However, we do not know how such models were able to arrive at such good predictions [15]. So, this leaves us with a tool that seems to work well on our assumed-to-be comprehensive datasets. Again, we may not know how this tool works. How can we trust it?⁹

Here is where one draws a line. A decision is to be made as to how the ML model is expected to be used. Are you looking for a blackbox prediction model? An explainable model? Or a causal model? While many of our problems will greatly benefit from any of the above three models, we are tasked to align our interpretations of the model outcomes to the model assumptions and limitations.¹⁰

#### 10.1.6 Remember that an Explainable Model Is Not a Causal Model

Poorly prepared databases (i.e., with incomplete/loose/confounding features) can deceive explainability tools into mistakenly labeling poor features as important [16]. This may also mislead the engineer into thinking that such features are

1 Also, I must acknowledge the many new things I learned from the anonymous reviewers and journal editors too. There are many quick stories that I remember that could fit into the theme of this chapter. On one occasion, one reviewer requested the addition of a short section toward the end of an article that outlines the limitations, and range of applicability of a developed model that my co-authors and I built. This chapter is inspired by such a request.

2 Some of the presented items builds up some of my recently co-authored publications [37, 38] while others were adopted from Google's Rules of Machine Learning [39].

5 Just like in other methods of investigation, you ought to check and verify your data and assumptions.

6 I would like to take the following lines to reminisce a bit on this recommendation. As engineers, we tend to favor some methods over others. Such preference stems from an engineer’s competence, training, past experience, and established professional practices. As such, opting to adopt ML to solve a given problem could be a result of inherent favoritism toward ML. I cannot remember how many times I reviewed manuscripts where the authors developed a highly complex ML model to solve a simple problem that could have been easily solved via reviewing mechanics principles. I also fell into the same trap as well. I do not think that this is a good practice, just like I do not believe that we need to conduct experiments for every problem we have. We have a toolbox (shout out to Brandon Ross as I am borrowing his analogy) of methods and we can pick and choose which method is likely to be more suitable than others.

7 Please note that I am carefully using the terms “could potentially”, as well as “better understand our problems and create/optimize novel solutions.” These should not be confused with establishing causality.

8 Please refer to [40] for a detailed discussion on some of the limitations of statistical methods.

9 The same can also be said to trusting an unknown version of a codal equation or an untested FE model.

10 I tend to favor properly developed explainable and causal models. My argument is simple, once we identify the driving mechanism(s) governing a phenomenon, then we know all the ins and outs of such a phenomenon and unlock valuable knowledge. Yet, I would also like to re-iterate the fact that there is a time and place for each and all ML approaches.
