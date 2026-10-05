from a “new” region removed from the distribution of training data? In such cases,
t model may be inaccurate and the explanation may be useless. The concept of
novality is related to the concept of certainty. The higher the novelty, the more likely it
is that the model will have low certainty due to lack of data.

+   - Representativeness: How many instances do an explanation cover? Explanations
can cover the entire model (e.g. interpretation of weights in a linear regression model)
or represent only an individual prediction (e.g. Shapley Values).

# 2.6 Human-friendly Explanations

Let us dig deeper and discover what humans see as “good” explanations and what the
implications are for interpretable machine learning. Humanities research can help find out.
Miller (2017) has constructed a huge survey of publications on explanations, and this chapter
bounds on its summary.

In this chapter, I want to convince you of the following: As an explanation for an event,
humans prefer short explanations (only 1 or 2 causes) that contrast the current situation
a situation in which the event would not have occurred. Especially abnormal cases
provide good explanations. Explanations are social interactions between the explainer and the
explainee (recipient of the explanation) and therefore the social context has great influence
 the actual content of the explanation.

When you need explanations with ALL factors for a particular prediction or behavior, you
do not want a human-friendly explanation, but a complete causal attribution. You probably\want a causal attribution if you are legally required to specify all influencing features or
y debug the machine learning model. In this case, ignore the following points. In all other
cases, where lay people or people with little time are the recipients of the explanation, the
following sections should be interesting to you.

# 2.6.1 What Is an Explanation?

An explanation is the answer to a why-question (Miller 2017).

+   - Why did not treat the treatment on the patient?
- Why was my loan rejected?
- Why have we not been contacted by alien life yet?

The first two questions can be answered with an “everyday”–explanation, while the three one
comes from the category “More general scientific phenomena and philosophical questions”. We
focus on the “everyday”–type explanations, because those are relevant to interpretable ma-
chine learning. Questions that start with “how” can usually be rephrased as “why” questions:
“How was my loan rejected?” can be turned into “Why was my loan rejected?”.