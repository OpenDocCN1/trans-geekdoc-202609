# Machine Learning with Applications (2022) 100406

Mehrabi et al. (2021) review types of bias and fairness definitions.

Consider two aspects of detecting bias in machine learning: data and bias. When training a model that is biased, using an unbiased or biased data set, it is important to put into place techniques to challenge and identify the bias. Secondly, in instances where the data set does not contain bias, the training process may introduce features, such as gender or race. Catan and Hao (2020) review the importance of these features for detecting bias, as well as increasing fairness; we used this as a starting point to explore possible techniques in both data and model.

Besides techniques for global interpretability that produce feature weights or rankings, or deliver rules determining the behaviour, this is also the approach of interactive visualisation to capture the model. The What if? allows users to probe, visualise and analyse systems without much coding (Wchsler et al., 2020). Now, users can inspect behaviour in different contexts, and build their own understanding of global behaviour.

# 2.2. Relevant techniques

Based on reviewed papers in the previous section, we have compiled a short-list of promising techniques focusing the business context and requirements.

# 2.2.1. Techniques for local interpretability

Local Model-agnostic Explanations (LIME) (Ribeiro et al., 2016) is one of local techniques. LIME learns to interpret each specific prediction. LIME is a linear model, which approximates the importance of each feature and whether the feature has a positive or negative impact on the final prediction. Non-linear (or rule-based) approaches can also take into account the combined effects of features in individual predictions. It is also possible that these techniques do not work well in the case of a binary prediction, but a focus of features together. An example of such a technique is SHAP (Ribeiro et al., 2018). An explanation is an analysis that explains a local prediction, so that changes can be made accordingly. Since SHAP uses rules, it is possible to combine features and is much powerful compared to LIME, also with some stems from the comparison of features as to a single angle.

Aquitas (Salinas et al., 2018) focuses on data exploration as output and make it attractive to both data scientists and decision makers. General, it explores exploration of the system and its role in facilitating and understanding data dependencies. Aquitas focuses on bias and visualisation based on specific demographic groups. The library does not directly interact with the model, but with the results of with the model, correct classification of cases. Fairness measures, for example false positive rate, are calculated and visualised in detail, showing the groups with their respective fairness and performance scores.

It is possible, even when a feature is not used in the training of the model, such as race, is present in the training data, the results may be biased against those groups (Okamoto et al., 2018), which has been discussed in the subsection on global interpretability, but also be used to see in rules with regards to ‘predictions’. By observing predicted features, it is possible to determine whether the predicted features are used in the model.

# 2.2.2. Techniques for bias detection

Besides exploring for global and local interpretability, we also investigate techniques to determine bias in a model. For us, we must look at both bias in the data and the results of training a model with biased data also usually yields a biased result.

# 2.2.3. Techniques for global interpretability

SHAP (Lundberg & Lee, 2017) can be used to test the explainability, and also be used to estimate global interpretability. With local interpretability, it is possible to see that features have a global impact on the model with a different enter. An instance where secondary features impact the global model by iteratively observing the features in the data set to get certain and assess the impact on the test set. This technique, called BlackBoxAuditing (Adler et al., 2018), can be used for global interpretability by identifying the importance of features in the data set, as well as determine whether a prediction is still impacting the model through its secondary features, monitoring the error rate achieved by the model.

One of the known techniques for explaining machine models is SHAP (Lundberg & Lee, 2017) which uses a cooperative game theory to explain the prediction of a specific instance by how much each feature contributed to the prediction, in the presence of combinations. All predictions result in a matrix of values, which can be compared for the entire model, thus providing global interpretability (Lundberg & Lee, 2017; Molnar).

# 2.3. Ethical considerations

There are several ethical issues in this research, stemming from the industry which the operation operates as well as the deployment of a machine learning model in any industry. The deployment of machine learning models brings with it ethical, specifically concerning housing and the potential impact on an applicant who is a customer of a machine learning model.

# 2.3.1. Automated machine learning detection

The organisation handles many applications in a day. This case of wanting efficiency in service has many applications, which may cause an automated machine learning application to receive a rejection that is not true. In this case, a model might reject the requester because the time required is so short to inspect all documents. In search for efficiency, organizations and industries are to use automated machine learning models for classification tasks. In this paper, the classification of machine learning model in the organisation judges incoming mortgage applicant. The evaluation of the applicant is the right way. In the case of a fraudulent applicant slipping through the machine learning model, an offer may be extended to the recipient, potentially resulting in financial losses for the organisation. The importance of an applicant who is biased and rejected by the machine learning model, the applicant will not receive a mortgage offer. The result of an evaluation by the machine learning model has a better impact for the applicant than for the organisation.