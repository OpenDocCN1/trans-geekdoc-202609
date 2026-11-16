# Machine learning-based approaches for automated hypertension detection

Simranjit Kaur
Research Scholar, Desh Bhagat University, Mandi Gobindgarh, Punjab, India

Khushboo Bansal
Department of CSE, Desh Bhagat University, Mandi Gobindgarh, Punjab, India

Yogesh Kumar
Department of CSE, School of Technology, Pandit Deendayal Energy University, Gandhinagar, Gujarat, India

ABSTRACT: Early detection and timely intervention of hypertension is critical to mitigate its adverse effects as it is a leading cause of heart disease. Traditionally, to detect hypertension depends upon various clinical factors such as measuring blood pressure, assessment of medical history, etc but they also have certain limitations such as human error, time consuming, as well as chances of missed diagnosis. Hence, using AI techniques allows identifying complex relationships within the data as well as surpassing the limitations of traditional diagnostic methods. The aim of the paper is to create a model which is capable of identifying individuals with hypertension and those without by using various AI learning models. With a dataset of 14 attributes, preprocessing identifies missing data while as visualization and correlation analysis has been used for detecting outliers and feature selection respectively. Further, seven different classifiers are applied such as gradient boosting, voting classifier, light gradient boosting machine, multilayer perceptron, Catboost, eXtreme gradient boosting classifier, and Adaboost. The performance of these classifiers has been evaluated it appears that CatBoost, XGBoost, and LGBM perform with a remarkable accuracy of 100% as well as outstanding recall, precision, along with the F1 score of 1.00. It demonstrates the capability of AI-driven models to revolutionize hypertension detection.

# 1 INTRODUCTION

In this era of advanced technology, the fusion of AI learning models and healthcare holds great promise to revolutionize the medical sector. By coupling the power of data-driven insights, healthcare professionals have the capability to make informed decisions which improves the patient outcomes and reduces healthcare costs for a healthier population. In fact, exploring this technique for detecting diseases marks a significant step towards a future where healthcare is not just reactive but proactive, personalized, and highly effective to address any most prevalent health challenges of world (Bohr and Memarzadeh 2020).

Hypertension is a life-threatening medical condition which is caused due to elevated blood pressure levels in the arteries. It causes various cardiovascular diseases which includes heart attacks/strokes, and kidney problems. Early detection as well as management of hypertension is crucial to prevent complications and improve overall health outcomes for individuals who are affected by this (Raji et al. 2017). In recent years, artificial intelligence techniques are emerging as a powerful tool in healthcare and efficiently detects as well as diagnosis hypertension. AI based algorithms such as machine learning and deep learning are able to analyze large volume of data, identify the patterns in them, and make predictions or