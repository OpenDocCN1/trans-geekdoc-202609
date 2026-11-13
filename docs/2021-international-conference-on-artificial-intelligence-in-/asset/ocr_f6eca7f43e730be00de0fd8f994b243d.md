- 42). To get the scores of the repsondents, each subscale is assigned to a unique subset of the 21 questions.

Lastly, to assess the participants' distress caused by the apparent traumatic event [14], they were asked to answer the Impact of Event Scale - Revised (IES-R). The questionnaire is composed of three subscales and aims to measure the mean avoidance, intrusion and hyperarousal. The total IES-R score will be divided as normal (0-23), mild (24-32), moderate (33-36), and severe (37).

+   2) Target Variables: The presence of the aforementioned measurements of Stress (S), Anxiety (A), Depression (D), and Impact of event (P) are the target variables in this research. They have a common initial set of predictor variables, which is the data collected under the 8 parts of the created survey. The additional predictors for each target variable are the measurements for their fellow target variables. This means that measurements for A, D, P are also predictors for S. Measurements for S, D, P are also predictors for A. Measurements for S, A, P are also predictors for D, and measurements for S, A, D are also predictors for P.

+   3) Data preparation: Data preparation is an essential step in the machine learning (ML) process. Raw data is not enough for ML models to analyze, they must be restructed and cleaned to be able to give the models a representation of the data that best reveals the prediction problems [15].

There were a total of 2652 participants who accomplished the survey, but only 2119 were considered in the research. The other 533( 20%) participants were disregarded due to their incomplete or total lack of answers for the DASS-21 or the IES-R surveys.

Data imputation was performed on the dataset when encountering missing values for numerical and categorical variables. Only ExtraHoursHome had missing values among the numerical variables, and these missing were replaced with the mean [16] of the present values. The categorical variables that had missing values are as follows:

The mode [16] of the answers for each categorical variable was computed and it replaced the missing values that were found in the dataset.

For the dependent variables Stress, Anxiety, and Depression, participants were initially classified based on severity, namely: normal, mild, moderate, severe, and extremely severe. Instead of this, this research represented mild, moderate, severe, and extremely severe as "Possible", while Normal remained unchanged. Similarly, for the dependent variable Impact of Event, participants were initially classified as normal, mild psychological impact, moderate psychological impact, and severe psychological impact. The category Normal remained unchanged, while the rest was represented as "Possible".

# B. Flow of the Study

After gathering all of the answers to the questions from the questionnaire and the survey, they were used as the independent variables in the research and used as the initial feature set with each question considered as one feature.

# TABLE I: Categorical variables with missing values

| Categorical predictor variables | |
| :--- | :--- |
| SelfRateHealthStatus | ConcernsChild |
| MedicalInsurance | FeelingDiscriminated |
| ChronicIllness | CoverMouth |
| ContactedPatients | AvoidSharingUtensils |
| CloseContact | WashingHandsSoapWater |
| IndirectContact | WashingHandsCoughNoseSneeze |
| ContactSuspected | WearingMask |
| ContactInfectedMaterials | WashingHandsContaminatedObjects |
| DropletsKnowledge | UnnecessaryWorry |
| ContactViaContaminatedObjectsKnowledge | ReceiveAdditionalInformation |
| AirborneKnowledge | DetailsOnSymptoms |
| HealthInformationSatisfaction | AdviceOnPrevention |
| HeardNumberOfInfected | AdviceOnTreatment |
| HeardNumberOfDeaths | RegularUpdatesLatestInformation |
| HeardNumberOfRecovered | RegularUpdatesOutbreaks |
| HowObtainHealthInformation | AdviceForPeople |
| PreXNeuropsychiatricCondition | AvailabilityEffectivenessMedicine |
| ConfidenceInDoctorDiagnosis | HowManyPeopleAffected |
| ContractingCovidLikelihood | TravelAdvice |
| SurvivingCovidInfected | HowCovidSpread |
| ConcernsOtherFamily | OtherCountryDoing |

Next, these variables underwent feature selection, which is the process of picking certain features from the initial set while disregarding the rest to be able to predict the dependent variables better. To do this, feature selection algorithms were applied.

These algorithms are divided into two parts, the Attribute Evaluator and the Search Method. The attribute evaluators used were CfsSubsetEval and InformationGain. The search methods used were BestFirst and Ranker. In this particular case, CfsSubsetEval and BestFirst were paired with each other, while InformationGain and Ranker were paired since the latter is a requirement.

Afterwards, the features were run through machine learning classifiers to build models for the predictions. The classifiers Random Forest, Naive Bayes, Support Vector Machines, and Logistic Regression were used. The vectors' performances were assessed using three obtained metrics: accuracy, precision, and recall. Accuracy is the percentage of correct predictions the models have made. Precision is the metric where it shows how many of the positive identifications were truly correct. Lastly, recall is the proportion of actual positives that were identified correctly. The application WEKA was used to execute the aforementioned process.

There were three approaches taken in the research, A, B, and C. They were similar in nature, but used different combinations of feature selection algorithms and independent variables to find the best results

+   1) Feature selection: Feature selection is an important part in the process of machine learning because it removes irrelevant and redundant variables from the initial set of predictors [17]. There are several methods that can be used, but there is no one way that is suited for all applications [18]. The feature selection algorithms used for each approach are seen in Table II.

The data gathered had a large amount, initially having 2652 rows of participants. However, due to a significant amount of