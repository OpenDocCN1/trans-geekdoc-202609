The literature reviewed the evolving nature of data science models, particularly AdaBoost and ensemble learning models, in the model of ASD prediction. These studies provide valuable insights into the challenges, opportunities, and recent advancements, contributing to the ongoing endeavors to enhance the accuracy and efficiency of ASD diagnosis through data science approaches.

# 8.3 METHODOLOGY

# 8.3.1 DATA COLLECTION

A collection of data on ASD created especially for predictive modeling is called the Kaggle Autism Child Dataset [22]. A number of characteristics, including age, gender, ethnicity, and a family history of pervasive developmental disorder (PDD), as well as the type of screening method and the answers to certain questions utilized during the screening process, are explained in Table 8.1. The dataset contains ranges of attributes related to individuals undergoing ASD screening. Key demographic information includes the individual's age and gender, along with their ethnicity, provided in text format. Health-related data are also captured, such whether the individual was born with jaundice and if they have a member with PDD, represented as binary responses ("yes" or "no"). The country of residence and whether the individual has used screening before are also noted. The dataset records the screening method type, categorized by age (t, child, adolescent), with responses to specific screening questions, each scored and cumulatively into the screening score. Additional context is provided by noting the relationship of the person completing the test (e.g., parent, self, healthcare professional), as well as the age category. Finally, the dataset includes a target variable, class/ASD, indicating the presence or absence of ASD, which is essential for analysis and predicting the likelihood of ASD in the individuals assessed. The dataset intends to aid in the study and creation of improved models for the prediction of ASD through the use of data science models, especially ensemble techniques such as AdaBoost and voting.

# TABLE 8.1

# Attributes of the Autism Dataset

| Attributes | Description |
| --- | --- |
| Age | Individual's age in years |
| Gender | Gender of the individual (male or female) |
| Ethnicity | List of common ethnicities presented in text format |
| Born with jaundice | Whether the individual was born with jaundice (yes or no) |
| Family member with PDD | Whether any family member has a PDD (yes or no) |
| Who is completing the test | Person completing the ASD screening test (parent, self, healthcare staff, clinician, etc.) |
| Country of residence | Country of residence provided in text format |
| Using the screening before | Whether the user has used a screening before (yes or no) |
| Screening method type | The chosen screening method type based on age category (0 = toddler, 1 = child, 2 = adolescent, 3 = adult) |
| Question 1 to 10 answer | Binary responses (0 or 1) to specific questions aligned with the screening method employed |
| Screening score | The final score achieved using the scoring algorithm of the chosen screening method, computed automatically |
| A1_score, ..., A10_score | Individual scores for each of the ten questions |
| Age description | Description of the age category (e.g., "18 and more") |
| relation | Relationship of the person completing the test (e.g., parent, self, healthcare professional) |
| Class/ASD | The target variable indicating the presence or absence of ASD (e.g., yes or no) |