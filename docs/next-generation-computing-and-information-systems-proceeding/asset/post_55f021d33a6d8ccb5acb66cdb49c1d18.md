
## Supervised context-aware Latent Dirichlet allocation-based drug recommendation model

Gopaldas H. Waghmare
Mechanical Engineering Department YCCE Nagpur, Maharashtra, India

Bhargavi Posinasetty
Masters in Public Health, The University of Southern Mississippi, Hattiesburg, MS, USA

Mohammad Shabaz
Model Institute of Engineering and Technology, Jammu, J&K, India

Saima Ahmed Rahin
United International University, Dhaka, Bangladesh

Abhishek Choudhary
Department of Political Science, University of Delhi, India

Seena K.
St. Marys College Thrissur, India

## ABSTRACT

The simplicity of electronic medical records and the ambiguity of patient symptom descriptions make the diagnosis model vulnerable to the interference of high-incidence diseases and joint symptoms. At the same time, much contextual information other than the description of the condition, such as the patient’s gender, age and additional personal information, the diagnosis and treatment process, examination results and the local weather, temperature difference and other external information, etc., are also helpful in refining the diagnosis of the patient. Based on effectively integrating multi-source heterogeneous context information, it provides an interpretable basis for disease diagnosis and drug recommendation. Then a contextual topic model Medicine-LDA based on the LDA model, was designed to solve the problem of contextual information combination explosion. The effectiveness and robustness of the method are proved by the comparative experiments based on the electronic medical record data set of a large tertiary hospital.

## 1 INTRODUCTION

The demand for high-quality medical services is on the rise, and the strain on the medical system is growing as a result of population expansion and the acceleration of the ageing process. According to the national medical and health statistics released by the National Health Commission, from January to November 2018, there were 3.23 billion people in hospitals across the country, a year-on-year increase of 5.3%. Correspondingly, as of 2019, the number of doctors per 1,000 population was 2.592, which is still a big gap compared with developed countries, which also leads to a heavy burden on medical staff and a massive hole in medical resources. On this basis, scholars in related fields have carried out a series of studies and achieved good results in competent guidance, medical image analysis and chronic disease follow-up (Al-Saffar and Baice 2022; Murad et al. 2022; Wang et al. 2013). Firstly, the promotion of electronic medical records is relatively late, resulting in fewer reliable medical data sources and other problems such as less data accumulation and inability to correlate the data of various departments. Secondly, the drug recommendation problem is more sensitive to the data quality, and mainly reflected in three aspects:

- 1) Most patients have only one visit record, and it is impossible to use the conventional personalized recommendation technology to model.
- 2) The distribution of diseases is seriously uneven, common diseases occupy most medical records, while niche groups and rare diseases are seriously sparse, and it is difficult to ensure the quality of their recommendations.
- 3) There is a high proportion of overlap between the symptoms of the disease. Taking this outbreak of new corona pneumonia as an example, its early signs have many similarities with other pneumonia and even common flu, and even experienced doctors are at risk of misjudgment.

However, these data also bring new difficulties: comprehensively considering this contextual information to achieve effective diagnosis and treatment. To solve the above problems, this paper proposes a drug recommendation method named as medicine-LDA (MLDA), based on multi-source contextual co-awareness. This paper modeled the process of diagnosing a patient by simulating a doctor in reality. Inspired by this, this paper model this process through four steps:

- 1) Extract the patient’s chief complaint text and check abnormality in the data, use the bag-of-words model to synthesize it into a document, and use this document to represent the patient, which is called the disease document;
- 2) Use the topic model to model the disease document, assuming that the paper has a potential topic, the possible topic represents the patient’s disease, and has the corresponding drug distribution and word distribution;
- 3) Integrate all the contextual information corresponding to the patient into one document, called the contextual document, and use the LDA model to model it to obtain the patient’s contextual topic distribution;
- 4) Assuming that the context topic will impact the patient’s disease and the medicines suitable for the patient, a unified probabilistic model framework is used to integrate the drug topically and the context topic to comprehensively model the context information and disease and drug information.

## 2 RELATED WORK

This section introduces the related work of this paper from three aspects: a drug recommendation system, a context-aware recommendation system and a topic model.

### 2.1 Drug recommendation system

Presently, the research on drug recommendation is not very extensive, and most drug recommendations mainly use the interaction records between users and drugs to make recommendations based on collaborative filtering technology. For example, (Zitouni et al. 2020) proposed a drug recommendation algorithm based on user similarity and trust to solve the problem of low recommendation accuracy of collaborative filtering. The method reduces the time complexity by clustering drugs, introduces a standard.

### 2.2 Context-aware recommender system

Traditional recommendation systems, such as content-based recommendation and collaborative filtering, ignore that users have different preference behaviors in different situations (Dwivedi and Rawat 2016). Therefore, researchers have proposed “context-aware” data mining technology to improve the recommendation effect. Since the same user often has different preferences in different contexts, the context-aware recommendation system can give more relevant recommendation results according to the user’s specific situation.

### 2.3 Topic model

A topic model is a statistical model for clustering implicit semantic structure in the corpus, which is widely used in semantic analysis and text mining in natural language processing. Latent Dirichlet allocation (LDA) is the most common topic model, which assumes that the document selects a potential topic with a certain probability and then selects a word from the topic with a certain chance to generate the entire corpus (Bose and Sohi 2006; Kluckner et al. 2013; Yu 2021). LDA can be extended in various ways by introducing external label information.

The essence of the topic obtained by the LDA model is to learn the co-occurrence relationship between words implicitly. When counting short texts, such methods often do not work well because the words in the short texts do not co-occur frequently enough. Some works have studied this problem.

### 2.4 Data preprocessing

First, the problem is described by simulating a doctor's diagnosing of a patient in reality. In the actual process of diagnosis and treatment, doctors often record the patient's chief complaint in the patient's medical text, as well as the doctor's physical examination of the patient (Jawarneh et al. 2023). The basis of segmentation includes the following:

- 1) Common sense of life, such as gender is divided into male and female, the season is divided into spring, summer, autumn and winter;
- 2) Data characteristics, such as the types of anesthesia are divided into general anesthesia, local anesthesia and no anesthesia;
- 3) External knowledge, such as age segmentation according to standard age segmentation methods, insurance status segmentation according to insurance amount and conditions;
- 4) For temperature difference, temperature and other situations without reference knowledge, based on the common sense of life and data distribution, the data distribution in different segments is relatively uniform, and the segmentation method is close to people's cognition of life.

### 2.5 Formal description

In this sub-section, we formally describe the problem studied in this paper as follows: In the context-aware drug recommendation task, the training set contains the disease document V<sub>i</sub> = {v<sub>i,1</sub>, v<sub>i,2</sub>, v<sub>i,p</sub>}, where v<sub>i</sub> are the words obtained from the segmentation of the medical text or a single abnormal item. Correspondingly, we have context documents U<sub>i</sub> = {u<sub>i,1</sub>, u<sub>i,2</sub>,...,u<sub>i,q</sub>}, where U<sub>i</sub>, is a single context word. In addition, we have a set of medicines E<sub>i</sub> = {e<sub>i,1</sub>,e<sub>i,2</sub>,...,e<sub>i,s</sub>}, where e<sub>i</sub>, is one of all the medicines prescribed by the doctor for the patient (Ahmed et al. 2022; Iqbal et al. 2022; Khan et al. 2020).

## 3 CONTEXT-AWARE DRUG RECOMMENDATION METHOD

### 3.1 Model overview

The general steps of the model proposed in this paper are:

- 1) The model needs to process the context information. Although the value of context information has been segmented in the data preprocessing part, if it is assumed that there are K kinds of context information, and each context has N value segments, there will be NK combinations, resulting in the model (Rida et al. 2015).
- 2) This paper uses a probabilistic framework to jointly model context information, disease documents, and patient medicines. The idea of modeling comes from the diagnosis and treatment process in actual medical places; that is, the doctor first determines the disease that the patient may suffer from according to the patient's symptoms, physical
