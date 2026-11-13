# 7

# Explainability and Interpretability

> > Translucent does not even mean invisible – it means semi-transparent.
> 
> Billy Butcher (The Boys, 2019)

# Synopsis

So far, we have learned about a variety of ML types and algorithms. We have also learned how to build ML models, examine such models, and deploy them. Collectively, we learned all about developing data-driven ML models. What we do not know *yet* is how to explain (or interpret) model predictions.<sup>1</sup> For example, given a set of features, if a model predicts a certain outcome (i.e., a phenomenon will occur<sup>2</sup>), then the following question may arise: why does the model predict that the combination of these features will yield to this particular outcome?

This chapter hopes to shed some light on answers that can help us address the aforementioned question. In this pursuit, this chapter will introduce principles and associated methods for establishing explainability and interpretability<sup>3</sup> from the lens of ML.

# 7.1 The Need for Explainability

As we know, a ML model maps a group of features to an outcome (e.g., tie concrete mix ingredients to the compressive strength property<sup>4</sup>). In our process, a properly validated model is one that attains a certain level of goodness; and thereby is declared proper and to have a permissible prediction capability.

+   1 Quick story: I was working with Moe al-Bashiti on a paper in which we built a ML model to predict failure in concrete specimens under fire conditions (I will showcase an analysis in Example no. 3 in this chapter). The developed model was pretty decent as in it was able to predict the failure of specimens with such high accuracy that matched, if not exceeded that available in the literature (at the time of this particular work). From then, our goal has shifted to the following. We were intrigued to know why and how this model was capable of realizing such accuracy. Was there something in the data that model can see that we could not? Was there something about this model that made it very accurate? I hope you are getting at what I am alluding to... If the answer to one or both of the questions is, yes, then maybe, just maybe, we could arrive at a glimpse for a possible theory for failure of such specimens! Simply, we needed to know the why and the how. This chapter is about finding answers to these questions from a *data perspective*.
+   
+   2 Or, for a regression-type problem, the concentration of dissolved oxygen is 12 ppm.
+   
+   3 At this point in time, there seem to be some differences between explainability and interpretability. Inherently, explainability is tied to systems that fall under AI (i.e., eXplainable AI (XAI)), while interpretability describes ML models. I would like to avoid such debate and hence will be adopting explainability throughout this chapter. Also, please note that other terminology also exists for explainable models such as whitebox, glass, and transparent models.
+   
+   4 Or tie road and weather conditions to the expected number of vehicle accidents. Another example would be to tie emission regulations in a particular region to the air quality in that region.