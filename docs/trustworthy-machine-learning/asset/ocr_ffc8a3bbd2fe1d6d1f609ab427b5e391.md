It is critical not to take any shortcuts in value alignment because it forms the foundation for the other parts of the lifecycle. By going through the value alignment process, you arrive at problem specifications that data scientists try to satisfy using machine learning models, bias mitigation algorithms, explainability algorithms, adversarial defenses, etc. during the modeling phase of the lifecycle.

One thing to be wary of is underspecification that allows machine learning models to take shortcuts (also known as specification gaming and reward hacking in the value alignment literature).5 This concept was covered in detail in Chapter 9, but is worth repeating. Any values that are left unsaid are free dimensions for machine learning algorithms to use as they please. So for example, even if the values you provide to the machine don’t prioritize fairness, you might still be opposed to an extremely extremely unfair model in spirit. If you don’t include at least some specification for a minimal level of fairness, the model may very well learn to be extremely unfair if it helps achieve specified values in accuracy, uncertainty quantification, and privacy.

In the remainder of the chapter, you will go through the problem specification phase for selecting Alma Meadow’s fellows using supervised machine learning, insisting on value alignment. By the end, you’ll have a better handle on the following questions.

+   - What are the different levels of consequentialist values that you should consider?
+   - How should these values be elicited from individual people and fused together when elicited from a group of people?
+   - How do you put together elicited values with transparent documentation covered in Chapter 13 to govern machine learning systems?

# 14.1 Four Levels of Values in Trustworthy Machine Learning

When you were first starting to think about improving Alma Meadow’s process for winnowing and selecting applications using machine learning, you had some rough idea why you wanted to do it (improving efficiency and transparency). However, you didn’t have a progression of questions to work through as you figured out whether and in which parts of the selection process you should use machine learning, which pillars of trustworthy machine learning you should worry about, and how to make your worries quantitative. Let’s list a series of four questions to help you gain clarity. (You’ll be aided in answering them in the next section.)

+   1. Should you work on this problem?
+   2. Which pillars of trustworthiness are of concern?
+   3. What are the appropriate metrics for those pillars of trustworthiness?
+   4. What are acceptable ranges of the metric values?

The first question you should ask is whether you should even work on a problem. The answer may be no. If you stop and think for a minute, many problems are not problems to be solved. At face value,