
# 88 Big data recommender systems, volume 1

building a Fuzzy-Ontology. Each phase and its associated produces and activities are elaborated in the following subsections.

## 5.11 Real-world project: hypertension-specific diagnosis based on HIDAS

This section describes the applicability and interoperability of the proposed HIDAs. This is a simple hypothetical use real-world hypertension diagnosis which aimed to explore the specific Fuzzy-Ontology hypertension architecture. Hypertension diagnosis can get information about the different stage of blood pressure ranges such as optimal stage, normal stage, high normal stage, Stage 1 (mid), Stage 2 (moderate) and Stage 3 (severe). Input parameters for Fuzzy-Ontology decision-making systems are age, body mass index (BMI), systolic and diastolic and one output parameter is hypertension risk. The intention of generating the hypertension diagnosis is to help providers characterize and identify the exact hypertension level to make better decisions for their patients. The diagnosis result will clearly identify the specific hypertension risk level which is to be overlooked. It will represent a formal input and output (risk level and stage) parameters which will provide clinicians to acquire a general understanding hypertension diagnosis.

Hypertension is defined as blood pressure measurement takes to account how much blood is passing through veins and the amount of resistance the blood meets while it's pumping. Although hypertension has been associated with factors such as alcohol consumption, smoking, high BMI and inadequate exercise, research has suggested that the degree of association between socioeconomic status and hypertension varies between males and females. Data on hypertension prevalence for the country are available from the following 1998 South African DHS, which has a prevalence of 21% for both males and females using the 140/90 mmHg threshold.

> N.B.: The archiving case project has considered only the hypertension remains instead of coated EHRs.

### 5.11.1 Data collection

This sub-step is to prepare for the formalisation of proposed HIDAs. A hypertension diagnosis risk-level specific Fuzzy-Ontology will formalise in the following steps. The set of data collection divided into two groups: male and female. All patients between 18 and 60 years old. The parameter subsets were considered as gender, age, BMI, heart rate and blood pressure. Some other information was also undertaken into account like patient's lifestyle, working background and medical history. This additional information was included in the parameter subjects that knowledge gained from the distributed questionnaire.

To collect the BMI information, traditional scale and tools were used to measure the weights and heights. BMI is defined as the patient's individual body weight divided by the patient's height squared. This is a universal method and widely used globally. The unit of measure is considered as international standard Three BMI category ranges were considered: (1) first category range between 19 to 25 is considered a healthy weight, (2) second category range between 16 to 18 are considered as underweight and (3) third category range between 25 to 30 are considered as overweight (Tables 5.1–5.4).

Table 5.1 According to various BMI category range around adult South African males (18–60 years) distribution of blood pressure (systolic and diastolic)

| Blood Pressure | Male | Female |
|---|---|---|---|
| | SBP (mmHg) | DBP (mmHg) | SBP (mmHg) | DBP (mmHg) |
| | Percentage | Number | Percentage | Number | Percentage | Number | Percentage | Number |
| Normal | 17.25 | 250 | 23.12 | 272 | 60.25 | 750 | 45.05 | 584 |
| Prehypertension | 81.2 | 950 | 49.45 | 584 | 38.25 | 256 | 45.24 | 560 |
| Hypertension | 2.56 | 300 | 30.01 | 352 | 2.49 | 320 | 8.97 | 120 |

SBP and gender chi-square = 49.44*** (p < 0.001); DBP and gender chi-square = 23.23*** (p < 0.001).

Table 5.2 According to various BMI category range around adult South African female (18–60 years) distribution of blood pressure (systolic and diastolic)

| BMI | SBP | DBP |
|---|---|---|---|---|---|---|---|
| | Prehypertension Stage Stage Normal Prehypertension Stage Stage |
| | 1 2 | 1 2 1 2 |
| Underweight | 73.1 | 26.9 | 0 | 0 | 65.4 | 26.9 | 7.7 | 0 |
| Normal | 54.4 | 43.4 | 0 | 2.2 | 45.6 | 41.2 | 13.2 | 0 |
| Overweight | 73.6 | 0.9 | 1.8 | 17.3 | 52.7 | 27.3 | 2.7 |

SBP chi-square = 43.24*** (p < 0.001) and DBP chi-square = 45.44*** (p < 0.001).

Table 5.3 South African male's (18–60 years) distribution of blood pressure (systolic and diastolic) where BMI is the risk factor

| BMI | Odds SBP | Odds DBP |
|---|---|---|---|---|---|
| Classification | Prehypertension Stage 1 Stage 2 | Prehypertension Stage 1 Stage 2 |
| Underweight | 0.45 | 0.59 | 1.15 | 0.53 | 0.42 | 0.53 |
| Normal | NC | NC | NC | NC | NC | NC |
| Overweight | 1.77 | | 1.48 | 2.82 | 2.65 | 8.98 |

NC = reference category/normal category.

Table 5.4 Adult African female's (18–60 years) distribution blood pressure (systolic and diastolic) where BMI is the risk factor

| Classification | Odds ratio SBP Pretreatment | Stage 1 | Stage 2 | Odds ratio DBP Pretreatment | Stage 1 | Stage 2 |
|---|---|---|---|---|---|---|
| Underweight | 0.56 | 0.61 | 0.54 | 0.63 | 1.1 | |
| Normal | NC | NC | NC | NC | NC | |
| Overweight | 0.56 | 2.28 | 0.98 | 2.75 | 3.74 | 8.8 |

NC = reference category/normal category.

### 5.11.2 Step 1: HIDAs contrivance and excellence

To ontology description as the target domain, the dictation is to formalise different properties of a hypertension risk level to demonstrate a semantically efficient diagnosis for clinicians and providers. This approach will also enable to use a hypertension alert execution treatment service and carry out into machine learning database to reuse in knowledge base approaches. The effective indication, a list of indicators has been delineated. Answer of these indications has used to delimit the proposed HIDAs contrivance and excellence in our close-bodied process.

- * Question: What type of outcome is expected from the HIDAs?
  Answer: Hypertension risk level that is going to be inspected are different SBP (systolic blood pressure), DBP (diastolic blood pressure), age and BMI (BMI) as major factors which affect the blood pressure.
- * Question: Are the HIDAs used as an appropriate solution technology upon other approaches empt gratia principle solution?
  Answer: This specific HIDAs conceptualisation is one of the most promising solution architectures for machine learning technology. The HIDAs is dictated to achieve efficient hypertension diagnosis by using formulated linguistic variable for specific hypertension and measure its interoperability.
- * Question: What architect ramifications will be the desired HIDAs?
  Answer: Due to the motivated contestants, the aim of the desired HIDAs architecture will limit to specific hypertension diagnosis only instead of EHR systems. The hypertension diagnosis ramification model contrivance logic will store into machine learning technology database to reuse or inherit related hypertension diagnosis applications, so that semantic hypertension diagnosis will be generalised as a domain-specific HIDA.
- * Question: Who will be the stakeholders and what will be their roles during the HIDAs development process?
  Answer: Professional professional while clinicians and providers will provide their knowledge and patients will be the participants as data sources.
- 5. Question: How to ensure the successful HIDAs development and implementation?
  Answer: The HIDAs development process will be controlled, managed by only HIDAs professionals and they will collect knowledge and data from secondary (clinicians and providers) and third party (patients) stakeholders. The conceptualisation knowledge will be used to build the model architecture and data will use to test the approach. All stakeholders will actively engage during the development process, such as refinement and correction, to ensure the interoperability.

### 5.11.3 Step 2: determine and ascertain the necessity for fuzziness in hypertension diagnosis

Fuzzy-Ontology is defined as handle vagueness, uncertainty and imprecisen. The objective of this section is to determine and ascertain the necessity for fuzziness in hypertension diagnosis. The eventual destination of this section is to ascertain what kind of approach is needed to build: Fuzzy-Ontology or crisp ontology. In this step, the primary and secondary stakeholders should decide to ascertain if there are any needs of fuzziness. To delineate the proper decision, a list of operations needs to perform:

- Understand the data: It's needed to provide a proper investigation over the target domain. First of all, there is need to analyse raw hypertension data to gain complete understanding of the data and all types of incidents and ascertain if there are any needs of fuzziness. Determine and not any fuzzy or similar incident presents.
- Implement the fuzziness when needed: The secondary stakeholders will decide whether fuzziness will include into the HIDAs architecture, before the appearance of the Fuzzy-Ontology approaches. The crisp ontology is capable to handle general vague data and is widely implemented. But, crisp ontology often fails in case of complex vague data and inaccurate, uncertain and inconsistent data. The crisp ontology is unable to deal when the expectation is high according to the degree of vagueness and its complexity.
- Determine the type of fuzziness: According to Fuzzy-Ontology definition, the fuzziness might already present in the ontology elements. So, it is important to determine if any fuzziness exists and if it exists what kind of fuzziness in individual or blurry concept.

The determination of each and the specific fuzzy element may not be possible but should be sufficient enough in the fuzzy set. Once the necessity of fuzziness can be determined and
