
![img/058011bdc8fc3d3d77199bfcbf721be0_128_0.png](img/058011bdc8fc3d3d77199bfcbf721be0_128_0.png)

Figure 6.1 The Process of Data Collection and Analytics of Healthcare Data.

rather than the narrative process of the text. The historic insufficiency of structured data and standardization in the healthcare industry today causes a problem when sharing the content between providers.

Unstructured data in healthcare is a kind of information that typically requires a human touch to read, capture, and interpret properly. This kind of capturing includes machine-written and handwritten information on unstructured paper forms, audio voice dictations, email messages and attachments, and typed transactions.

![img/058011bdc8fc3d3d77199bfcbf721be0_128_1.png](img/058011bdc8fc3d3d77199bfcbf721be0_128_1.png)

Figure 6.2 The Data Representation of EHR in the Healthcare System.

Any kind of unstructured data in healthcare will be brought into the EHR flow using the technical components of electronic document management systems (EDMS), including:

- The automated forms of classification and data capture systems
- Document management systems for version control, check-in/check-out, and security
- Maintaining eForms for online data entry and data collection
- Using records management technology to get controlled access to records and retain or destroy records in accordance with state regulations

In addition to the structured and unstructured EHR, ICD (International Classification of Disease) codes are also going to generate a huge volume of data.

## 6.3.1 The Role of ICD Codes in the Generation of Big Healthcare Data

ICD is a hierarchical terminology of diseases, signs, symptoms, and procedure codes maintained by the World Health Organization (WHO). In the United States most of the people are using ICD-9 and the rest of the world uses ICD-10. And also the rise of EMRs has led to the propagation of observational studies which are helpful to examine the preoperative period in terms of huge numbers; this is also one of the main reasons to produce Big Data. The work of Thomas et al. [4] falls short of invalidating codes for toxemia, since the authors did not investigate the exactness of coding, but rather looked at their use over time. Thus, it is unclear what is responsible for the discrepancy that they discovered, and it could be that coding for sepsis became more accurate over time.

## 6.3.2 Analyzing the ICD Codes and EHR Data

In general the term Big Data is not subjected to MeSH (Medical Subject Heading) – it is embodied by the MeSH in terms of “automatic data processing,” “electronic data processing,” “data mining,” and “EHRs”. However, it’s very important to do some analytics on such type of data. Table 6.1 gives an idea about the terms associated with healthcare and how to query the results from Big Data.

Table 6.1 Frequent Terms Used in the Statistical Model of Data Analytics in Healthcare

| CATEGORY | QUERY TERMS | CATEGORY | QUERY TERMS |
| :--- | :--- | :--- | :--- |
| EHR | Electronic Health Records | Privacy and Security | Access Control* |
| | Electronic Medical Records* | | Confidentiality |
| | Personal Health Records | | Consent |
| | | | Patient Data Privacy |
| | | | Data Sharing |
| | | | Privacy |
| | | | Privacy Mechanism* |
| | | | Computer Security |
| Data Analysis | Artificial Intelligence | NLP | Controlled Vocabulary |
| | Big Data* | | De-Identification* |
| | Cloud Computing* | | Information Extraction |
| | Data Mining | | Information Storage and Retrieval |
| | Data Interpretation | | Knowledge Representation |
| | Computer Simulation | | Natural Language Processing |
| | Predictive Model* | | Text Mining |
| | Statistical Model | | |
| | Visualization | | |
| Health Information Technology | Clinical Decision Support System | Translational Informatics | Surveillance |
| | Monitoring* | | Pharmacovigilance |
| | Quality Improvement | | Phenotyping* |
| | Social Media | | |

In general, a predictive model is a widely used buzzword in healthcare data analytics, which is applicable for “data visualization.” Data visualization is critical for interpreting study outcomes, and this technique helps clinicians accept new methods. Visualization monitoring is also a broad concept, which also includes drug monitoring, patient monitoring, etc. “Access control” is also one of the new and popular topics in patient data privacy research. From Table 6.1, we have to specifically mention a technique called natural language processing (NLP), which is one of the core technologies employed in biomedical informatics. NLP can be used to analyze a large amount of data which consist of discharge summaries in an unstructured format. Therefore, using a technique like NLP can lead to extracting and structuring this descriptive information. This procedure can be treated as an important step in many EHR data secondary-use studies. By augmenting the amount of computable data, NLP can also help to address some aspects of incomplete data.

NLP starts with extracting the information from trivial data sources, namely ADEs from EHR data. Information extraction (IE) is a traditional area in which NLP is used to identify and classify name entities and relations from narrative text, like discharge summaries and prescriptions. Identifying the relations (relation identification) is the most promising field in IE, though we have many obstacles. In IE and RI we focus on

- Co-reference identification and
- Temporal relation extraction

The role of co-reference resolution is to recognize two mentions that refer to the same entity in a sentence or across sentences. Present co-reference resolution studies use the rule-based machine learning and hybrid systems to identify noun phrases, including person, pronoun, and concepts such as medical tests. In this method, the data quality will decide the performance of the systems.

Temporal relation extraction is also one of the methods in the information extraction process; it focuses on research direction because it is used to identify the complications, patient outcome predictions, and ADE detection. Previously, temporal relation was also utilized in the abstraction of emergency department (ED) computed tomography (CT) imaging reports. In addition to the NLP, we also using the data application and integration mechanism in EHR data to utilize and retrospectively assess treatment effectiveness in real-world settings, quality of care, and cost. A clinical decision support system (CDSS) helps to do multitasking on healthcare Big Data to make quick decisions.

A conceptual model for analyzing the Big Data in standard platforms is shown in Figure 6.3.

![img/058011bdc8fc3d3d77199bfcbf721be0_132_0.png](img/058011bdc8fc3d3d77199bfcbf721be0_132_0.png)

Figure 6.3 An Applied Conceptual Model for Big Data Analytics.

The same can be applied to the healthcare data by dividing it into the following two categories: basic analytics and advanced analytics. The different platforms we used in the earlier architecture will be helpful to migrate the healthcare data into a general structured format to understand quickly. Now we will start the actual analytics part of the healthcare data with the basic analytics section.

## 6.3.3 Basic Analytics on Healthcare Data

It seems that the cost of healthcare has been consistently rising, at the same time the quality of care provided to the patients in some countries has not seen considerable improvements. In this section, we’ll try to focus on the quality improvements in healthcare data by doing some basic analytics using sources available. Generally, the different forms of patient data can be stored in EHRs and biomedical images, which we discussed earlier. Here the basic analytics includes the techniques for mining the various sensor data and also biomedical signal analysis. In this part, we are specifically going to be brief about in-hospital clinical data, biomedical literature, and the behavioral data captured through social mediums. The list of analytics is as follows:

- Biomedical image analysis
- Sensor data analysis
- Biomedical signal analysis
