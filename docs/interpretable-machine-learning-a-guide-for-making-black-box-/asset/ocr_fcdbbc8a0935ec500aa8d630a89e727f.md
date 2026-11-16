# # 2.6 Human-friendly Explanations

Let us dig deeper and discover what we humans see as "good" explanations and what the implications are for interpretable machine learning. Humanities research can help us find out. Miller (2017) has conducted a huge survey of publications on explanations, and this chapter builds on his summary.

In this chapter, I want to convince you of the following: As an explanation for an event, humans prefer short explanations (only 1 or 2 causes) that contrast the current situation with a situation in which the event would not have occurred. Especially abnormal causes provide good explanations. Explanations are social interactions between the explainer and the explainee (recipient of the explanation) and therefore the social context has a great influence on the actual content of the explanation.

When you need explanations with ALL factors for a particular prediction or behavior, you do not want a human-friendly explanation, but a complete causal attribution. You probably want a causal attribution if you are legally required to specify all influencing features or if you debug the machine learning model. In this case, ignore the following points. In all other cases, where lay people or people with little time are the recipients of the explanation, the following sections should be interesting to you.

# ## 2.6.1 What Is an Explanation?

An explanation is the **answer to a why-question** (Miller 2017).

+   - Why did not the treatment work on the patient?
+   - Why was my loan rejected?
+   - Why have we not been contacted by alien life yet?

The first two questions can be answered with an "everyday"-explanation, while the third one comes from the category "More general scientific phenomena and philosophical questions". We focus on the "everyday"-type explanations, because those are relevant to interpretable machine learning. Questions that start with "how" can usually be rephrased as "why" questions: "How was my loan rejected?" can be turned into "Why was my loan rejected?".

In the following, the term "explanation" refers to the social and cognitive process of explaining, but also to the product of these processes. The explainer can be a human being or a machine.

# ## 2.6.2 What Is a Good Explanation?

This section further condenses Miller's summary on "good" explanations and adds concrete implications for interpretable machine learning.

**Explanations are contrastive** (Lipton 1990²). Humans usually do not ask why a certain prediction was made, but why this prediction was made _instead of another prediction_. We tend to think in counterfactual cases, i.e. "How would the prediction have been if input X had been different?". For a house price prediction, the house owner might be interested in why the predicted price was high compared to the lower price they had expected. If my loan application is rejected, I do not care to hear all the factors that generally speak for or against a rejection. I am interested in the factors in my application that would need to change to get the loan. I want to know the contrast between my application and the would-be-accepted version of my application. The recognition that contrasting explanations matter is an important finding for explainable machine learning. From most interpretable models, you can extract an explanation that implicitly contrasts a prediction of an instance with the prediction of an artificial data instance or an average of instances. Physicians might ask: "Why did the drug not work for my patient?". And they might want an explanation that contrasts their patient with a patient for whom the drug worked and who is similar to the non-responding patient. Contrastive explanations are easier to understand than complete explanations. A complete explanation of the physician's question why the drug does not work might include: The patient has had the disease for 10 years, 11 genes are over-expressed, the patients body is very quick in breaking the drug down into ineffective chemicals, ... A contrastive explanation might be much simpler: In contrast to the responding patient, the