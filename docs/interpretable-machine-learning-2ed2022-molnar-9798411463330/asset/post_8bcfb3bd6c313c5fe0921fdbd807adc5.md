
from a “new” region removed from the distribution of training data? In such cases, the model may be inaccurate and the explanation may be useless. The concept of novelty is related to the concept of certainty. The higher the novelty, the more likely it is that the model will have low certainty due to lack of data.

- Representativeness: How many instances do an explanation cover? Explanations can cover the entire model (e.g. interpretation of weights in a linear regression model) or represent only an individual prediction (e.g. Shapley Values).

## 2.6 Human-friendly Explanations

Let us dig deeper and discover what humans see as “good” explanations and what the implications are for interpretable machine learning. Humanities research can help find out. Miller (2017) has constructed a huge survey of publications on explanations, and this chapter bounds on its summary.

In this chapter, I want to convince you of the following: As an explanation for an event, humans prefer short explanations (only 1 or 2 causes) that contrast the current situation with a situation in which the event would not have occurred. Especially abnormal cases provide good explanations. Explanations are social interactions between the explainer and the explainee (recipient of the explanation) and therefore the social context has great influence on the actual content of the explanation.

When you need explanations with ALL factors for a particular prediction or behavior, you do not want a human-friendly explanation, but a complete causal attribution. You probably want a causal attribution if you are legally required to specify all influencing features or debug the machine learning model. In this case, ignore the following points. In all other cases, where lay people or people with little time are the recipients of the explanation, the following sections should be interesting to you.

### 2.6.1 What Is an Explanation?

An explanation is the answer to a why-question (Miller 2017).

- Why did the doctor not treat the patient with medicine?
- Why was my loan rejected?
- Why have we not been contacted by alien life yet?

The first two questions can be answered with an “everyday”–explanation, while the third one comes from the category “More general scientific phenomena and philosophical questions”. We focus on the “everyday”–type explanations, because those are relevant to interpretable machine learning. Questions that start with “how” can usually be rephrased as “why” questions: “How was my loan rejected?” can be turned into “Why was my loan rejected?”.

In the following, the term “explanation” refers to the social and cognitive process of explaining, but also to the product of these processes. The explainer can be a human being or a machine.

### 2.6.2 What Is a Good Explanation?

This section further condenses Miller’s summary on “good” explanations and adds concrete implications for interpretable machine learning.

Explanations are contrastive (Lipton 1990). Humans do not ask why a prediction was made, but why this prediction was *instead of another prediction*. We tend to think in counterfactual cases, i.e. “How would the prediction have been if X were different?” For a house price prediction, the house owner might be interested in why the predicted price contrasts to the lower price they expected. If my loan application is rejected, I do not care about all the factors that generally speak for against a rejection. I am interested in the factors in my application that would want to change or I want to know the difference between the application and the would-accepted version of my application. The recognition that contrasting explanations matters is an important finding for explainable machine learning. From most interpretable models, you can extract an explanation that matches the prediction of an instance with an artificial data source or an average of instances. Physicians might ask: “Why did the drug not work for my patient?” And they want an explanation that contrasts the patient with whom the drug worked and is similar to the non-responding patient. Contrastive explanations are easier to understand than complete explanations. A complete explanation of the physician’s reason why the drug does not work might include: The patient has had the disease for 10 years, 11 genes are over-expressed, the body is very quick in breaking the drug down into ineffective chemicals. A contrastive explanation might be much simpler: In contrast to the responding patient, the non-responding patient has a certain combination of genes that makes the drug less effective. The best explanation is one that highlights the greatest difference between the object of interest and the reference object.

**What it means for interpretable machine learning:** Humans do not want a complete explanation for a prediction, but want to compare what they were to another instance’s prediction (can be an artificial one). Creating contrastive explanations is application-dependent because it requires a point of reference for comparison. This thus may depend on the data point to be explained, but also on the user receiving the explanation. A user of a house price website might want to have an explanation of a house price contrastive to their own house or may want to have another house on the website or maybe to an average house in the neighborhood. The solution for the automated creation of contrastive explanations might also involve finding prototypes or archetypes in the data.

**Explanations are selected.** People do not expect explanations that cover the actual and complete list of causes of an event. We are used to selecting one or two cases from a variety of possible cases as THE explanation. As proof, turn to TV news: “The decline in stock prices is blamed on a growing backlash against the company’s product due to problems with the latest software update.”

“Tsubasa and his team lost the match because of a weak defense: they gave their opponents too much room to play out their strategy.”

“The increasing distrust of established institutions and our government are the main factors that have reduced voter turnout.”

The fact that an event can be explained by various causes is the Rashomon Effect. Rashomon is a Japanese movie that tells alternative, contradictory stories (explanations) about the death of a samurai. For machine learning models, it is advantageous to make prediction from different features. Ensemble methods that combine multiple models with different features (different explanations) usually perform well because averaging over those “stories” makes the predictions more robust and accurate. But it also means there is more than one selective explanation why a certain prediction was made.

**What it means for interpretable learning:** Make the explanation, give only 1 to 3 reasons, even if the world is more complex. The LIME method does a good job with this.

Explanations are social. They are part of a conversation or interaction between the explainer and the receiver of the explanation. The social context determines the content and nature of explanations. If I wanted to explain to a technical person why digital cryptocur are so much, I would say things like “The decentralized, distributed, blockchain-based ledger, which could be controlled by a central authority, resonates with people who want to secure their wealth, which explains the high demand and price.” But my grandmother would say: “Look, Grandma: Cryptocurrencies are a bit like computer gold. People like and pay a lot for gold, and young people pay a lot for computer gold.”

**What it means for interpretable learning:** Pay attention to the social environment of your machine learning application and the target audience. The part of the machine learning model depends entirely on your specific application. Experts from the humanities (e.g. psychologists and sociologists) to help you.

Explanations focus on the abnormal. These are cases that have a small probability but are nevertheless important. The elimination of these abnormal cases would have greatly changed the outcome (counterfactual explanation). Humans consider these of “abnormal” cases as good explanations. As from Strumbel and Kononenko is: We have a dataset of test situations between teachers and students. Students attend a pass directly after successfully giving a presentation. The teacher has the option to additionally ask the student questions to test their knowledge. Students who cannot answer these questions will fail the course. Students can have different levels of preparation, which translates into different probabilities for correctly answering the teacher’ questions (if they decide to test the student). We want to predict whether a student will pass the course and explain our prediction. The chance of passing is 100% if the teacher does not ask you
