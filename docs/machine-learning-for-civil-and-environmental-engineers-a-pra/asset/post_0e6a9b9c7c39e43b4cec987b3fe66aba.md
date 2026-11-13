
- 22 ggplot2. (2022). Create elegant data visualisations using the grammar of graphics • ggplot2. https://ggplot2.tidyverse.org (accessed 7 July 2022).

- 23 tidyr. (2022). Tidy messy data • tidyr. https://tidyr.tidyverse.org (accessed 7 July 2022).

- 24 dplyr. (2022). A grammar of data manipulation • dplyr. https://dplyr.tidyverse.org (accessed 7 July 2022).

- 25 Shiny. (2022). Shiny. https://shiny.rstudio.com (accessed 7 July 2022).

- 26 RapidMiner. (2022). RapidMiner for academics - RapidMiner. https://rapidminer.com/platform/educational (accessed 7 July 2022).

- 27 Weka. (2022). Weka 3 - machine learning software in java. https://www.cs.waikato.ac.nz/ml/weka (accessed 7 July 2022).

- 28 KNIME. (2022). Downloads | KNIME. https://www.knime.com/downloads (accessed 7 July 2022).

- 29 Naser, M.Z. (2021). An engineer's guide to eXplainable artificial intelligence and interpretable machine learning: navigating causality, forced goodness, and the false perception of inference. Autom. Constr 129: 103821. doi: 10.1016/J. AUTOCON.2021.103821.

- 30 Naser, M.Z. (2020). Machine Learning Assessment of Fiber-Reinforced Polymer-Strengthened and Reinforced Concrete Members. ACI Struct. J. doi: 10.14359/51728073.

- 31 Young, B.A., Hall, A., Pilon, L. et al. (2019). Can the compressive strength of concrete be estimated from knowledge of the mixture proportions?: new insights from statistical analysis and machine learning methods. Cem. Concr. Res. 115: 379–388. doi: 10.1016/j.cemconres.2018.09.006.

- 32 Naser, M.Z. (2022). Digital twin for next gen concretes: on-demand tuning of vulnerable mixtures through explainable and anomalous machine learning. Cem. Concr. Compos. 132: 104640. doi: 10.1016/J.CEMCONCOMP.2022.104640.

- 33 DataRobot. (2020). Anomaly detection: dataRobot docs. https://docs.datarobot.com/en/docs/modeling/special-workflows/unsupervised/anomaly-detection.html (accessed 5 July 2022).

- 34 Dataiku. (2014). Pronouncing dataiku. https://blog.dataiku.com/2014/08/07/pronouncing-dataiku (accessed 27 July 2022).

- 35 Sadhwani, J. (2022). GitHub - JatinSadhwani02/water-quality-prediction-using-ML-technique. https://github.com/JatinSadhwani02/Water-Quality-Prediction-using-ML-technique (accessed 16 June 2022).

- 36 Tsanas, A. and Xifara, A. (2022). UCI machine learning repository: energy efficiency data set. https://archive.ics.uci.edu/ml/datasets/Energy+efficiency# (accessed 6 July 2022).

- 37 Chandavale, A. (2022). Carbon emission India | kaggle. https://www.kaggle.com/datasets/adityachandavale/carbon-emission-india?resource=download (accessed 6 July 2022).

- 38 Sathishkumar, V., Lee, M., Lim, J. et al. (2022). Steel industry energy consumption | kaggle. https://www.kaggle.com/datasets/csafrit2/steel-industry-energy-consumption (accessed 6 July 2022).

- 39 Tilley, A. (2017). Every AI powerhouse wanted this whiz kid. He's taking them on instead. Forbes. https://www.forbes.com/sites/aarontilley/2017/07/13/clairifai-ai-image-recognition/?sh=2b55ef2dfe42 (accessed 9 July 2022).

- 40 Lutz, M. (2015). Learning Python, 5e. O'Reilly Media.

- 41 Wickham, H. and Grolemund, G. (2011). R for data science. Interact. Cardiovasc. Thorac. Surg...

- 42 Microsoft. (2022). GitHub - microsoft/data-science-for-beginners. https://github.com/microsoft/Data-Science-For-Beginners (accessed 1 August 2022).

- 43 Python. (2022). General python FAQ — python 3.10.5 documentation. https://docs.python.org/3/faq/general.html (accessed 5 July 2022).

- 44 Anaconda. (2022). Anaconda | the World's most popular data science platform. https://www.anaconda.com (accessed 5 July 2022).

- 45 Google. (2022). Welcome to collaboratory - collaboratory. https://colab.research.google.com/?utm_source=scs-index (accessed 7 July 2022).

- 46 Özyüksel Çiftçioğlu, A. and Naser, M.Z. (2022). Hiding in plain sight: what can interpretable unsupervised machine learning and clustering analysis tell us about the fire behavior of reinforced concrete columns? Structures 40: 920–935. doi: 10.1016/J.ISTRUC.2022.04.076.

## 7 Explainability and Interpretability

> > Translucent does not even mean invisible – it means semi-transparent.
> 
> Billy Butcher (The Boys, 2019)

### Synopsis

So far, we have learned about a variety of ML types and algorithms. We have also learned how to build ML models, examine such models, and deploy them. Collectively, we learned all about developing data-driven ML models. What we do not know *yet* is how to explain (or interpret) model predictions.<sup>1</sup> For example, given a set of features, if a model predicts a certain outcome (i.e., a phenomenon will occur<sup>2</sup>), then the following question may arise: why does the model predict that the combination of these features will yield to this particular outcome?

This chapter hopes to shed some light on answers that can help us address the aforementioned question. In this pursuit, this chapter will introduce principles and associated methods for establishing explainability and interpretability<sup>3</sup> from the lens of ML.

### 7.1 The Need for Explainability

As we know, a ML model maps a group of features to an outcome (e.g., tie concrete mix ingredients to the compressive strength property<sup>4</sup>). In our process, a properly validated model is one that attains a certain level of goodness; and thereby is declared proper and to have a permissible prediction capability.

- 1 Quick story: I was working with Moe al-Bashiti on a paper in which we built a ML model to predict failure in concrete specimens under fire conditions (I will showcase an analysis in Example no. 3 in this chapter). The developed model was pretty decent as in it was able to predict the failure of specimens with such high accuracy that matched, if not exceeded that available in the literature (at the time of this particular work). From then, our goal has shifted to the following. We were intrigued to know why and how this model was capable of realizing such accuracy. Was there something in the data that model can see that we could not? Was there something about this model that made it very accurate? I hope you are getting at what I am alluding to... If the answer to one or both of the questions is, yes, then maybe, just maybe, we could arrive at a glimpse for a possible theory for failure of such specimens! Simply, we needed to know the why and the how. This chapter is about finding answers to these questions from a *data perspective*.

- 2 Or, for a regression-type problem, the concentration of dissolved oxygen is 12 ppm.

- 3 At this point in time, there seem to be some differences between explainability and interpretability. Inherently, explainability is tied to systems that fall under AI (i.e., eXplainable AI (XAI)), while interpretability describes ML models. I would like to avoid such debate and hence will be adopting explainability throughout this chapter. Also, please note that other terminology also exists for explainable models such as whitebox, glass, and transparent models.

- 4 Or tie road and weather conditions to the expected number of vehicle accidents. Another example would be to tie emission regulations in a particular region to the air quality in that region.

Let us think about this for a minute. Surely, satisfying selected performance metrics and error indicators is a quantifiable measure that we can attach to the goodness of a model. This is the same procedure we would also follow when deriving mathematical and empirical models. But there seems to be something missing. How do performance metrics/indicators relate to the physics (or mechanics) of the engineering problems we are interested in? The short answer is that they rarely do<sup>5</sup>

If you remember our discussion on PFIE, then you would also remember that satisfying a group of selected performance metrics does not effectively imply that the ML model captures the physics behind a phenomenon. Rather, this infers the suitability of such a model to predict the outcome as described in our dataset [1].

This brings me to this chapter. Our objective in this chapter is to understand the reasoning behind a ML model's predictions. In other words, what has led<sup>6</sup> the model to arrive at a specific outcome and not some other outcome? One might say, how is knowing the above relevant? A ML model is based on an algorithm/ensemble that is driven by the data. This implies that the data, together with the way the algorithm was trained to tie<sup>7</sup> this data together, are the reasons behind such model predictions.<sup>8</sup> I am hoping the next section may change your mind.

#### 7.1.1 Explainability and Interpretability

As mentioned earlier, explainability and interpretability are often used interchangeably nowadays [2]. However, subtle differences between the two exist. For example, explainability is reserved for “models that are able to summarize the reasons for neural network behavior, gain the trust of users, or produce insights about the causes of their decisions.” [3]. In addition, explainability entails relating the inner mechanisms of a model and their influence on the model's prediction. An explainable model embodies a complex function that may not be understood on its own and hence is likely to require us to augment such function with additional methods/techniques to be able to understand it.

On the other hand, interpretability is “loosely defined as the science of comprehending what a model did (or might have done)” [3]. In other words, interpretability is humanly understandable without aid<sup>9</sup>. The degree of explainability or interpretability depends on a number of items such as user expectations, problem complexity, algorithmic architecture, etc. Table 7.1 compares commonly used ML algorithms in terms of how understandable they can be.

Adopting explainable models or understanding why a model predicts its outcomes can open exciting doors for civil and environmental engineers. Let me revisit our earlier example of tying concrete mix ingredients to the property of compressive strength.<sup>10</sup> If we were able to develop a ML model that can truly capture this property as well as explain the inferred hidden relation(s) between the ingredients and the strength property, then it is possible that we would arrive at a new piece of information (aka. knowledge<sup>11</sup>) that we did not have before. The same concept of explainable models could help our engineers discover new mechanics or new hypotheses for some of the common problems they seem to continue to struggle with<sup>12</sup> [5].

The above brings in the important question of how to infer a model’s understanding of a phenomenon? After all, this chapter hopes to address this question.

Well, there are a number of explainability methods that we can augment ML models with. These methods open the blackbox for us to get to see how and why the model predicts the way it does. These methods vary in terms of their:
