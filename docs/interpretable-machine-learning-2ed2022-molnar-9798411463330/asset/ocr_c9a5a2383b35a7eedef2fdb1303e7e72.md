# 28 CHAPTER 2 INTERPRETABILITY

additional questions, otherwise the probability of passing depends on the student's level of preparation and the resulting probability of answering the questions correctly.

Scenario 1: The teacher usually asks the students additional questions (e.g. 95 out of 100 times). A student who did not study (10% chance to pass the question) was not one of the lucky ones and gets additional questions that he fails to answer correctly. Why did the student fail the course? I would say that it was the student's fault to not study.

Scenario 2: The teacher rarely asks additional questions (e.g. 2 out of 100 times). For a student who has not studied for the questions, we would predict a high probability of passing the course because questions are unlikely. Of course, one of the students did not prepare for the questions, which gives him a 10% chance of passing them. He is unlucky and the teacher asks additional questions that the student cannot answer and fails the course. What is the reason for the failure? I would argue that, the better explanation is “because” the teacher tested the student. It was unlikely that the teacher would test, so the teacher behaved abnormally.

What it means for interpretable machine learning: If one of the features for a prediction was abnormal in any sense (like a rare of a categorical feature) and the feature influenced the prediction, it should be included in an explanation, even if ‘normal’ features have the same influence on the prediction as others. An abnormal feature in our price prediction example might be that a more expensive house has two balconies. Even if some attribution method shows that the balconies contribute to the price difference as the above average house size, the neighborhood or the recent renovation, the abnormal feature “two balconies” might be the best explanation for why the house is expensive.

Explanations are truthful. Good explanations prove to be true in reality (i.e. in other situations). But disturbingly, this seems to be more important than truthfulness. An explanation that selects one or two possible cases rarely covers the entire list of relevant cases. Selectivity omit part of the truth. It is not true that one or two factors, for example, have caused a stock market crash, but the truth is that there are millions of cases that influence people to act in such a way that the crash was caused.

What it means for interpretable machine learning: The explanation should predict the event as truthfully, which in machine learning is sometimes called fidelity. If we say that a balcony increases the price of a house, then that should also apply to other houses (or at least to similar houses). For humans, fidelity of an explanation is not as important as its selectivity, and its social aspect.

What it means for interpretable machine learning: Good explanations are consistent

> ¹²Nickerson, Raymond S. “Confirmation Bias: A ubiquitous phenomenon in many guises.” Review of General Psychology 2 (2). Educational Publishing: 175, (1998).