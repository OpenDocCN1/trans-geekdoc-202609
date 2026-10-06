# CHAPTER 7. ENCODING BEHAVIORAL DATA

202

![](bbox=[0.163, 0.101, 0.836, 0.35])

Figure 7.2: Example of some raw data encoded into different representations.

# 7.1 Feature Vectors

From previous chapters, we have already seen how the data can be represented as feature vectors. For example when classifying physical activities (section 2.3.1) or clustering questionnaire answers (section 6.1.1). Feature vectors are compact representations of some real-world phenomenon or usually, they are modeled in a computer as numeric arrays. Most machine learning algorithms work with feature vectors. Generating feature vectors requires knowledge of the application domain. Ideally, one wants to have feature vectors that represent the real-world situation as accurately as possible. We could achieve a good mapping by having feature vectors of infinite size, unfortunately, that is infeasible. In practice, small feature vectors are desired because that reduces storage requirements and computational time.

The process of generating feature vectors from raw data is known as feature engineering which also involves the process of deciding which features to extract. This requires domain knowledge as the features should capture the information needed to solve the problem. Suppose we want to classify if a person is ‘tired’ or ‘not tired’. We have access to some details about the person like height, the activities performed during the last 30 minutes, and so on. For simplicity, let’s assume we can generate feature vectors of size 2 and we have two options:

+   **Option 1.** Feature vectors where the first element is age and the second element is height.
- **Option 2.** Feature vectors where the first element is the number of squats done by