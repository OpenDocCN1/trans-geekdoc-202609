
## New interpretation of GNRB® knee arthrometer results for ACL injury diagnosis support using machine learning

Jean Mouchotte a,*, Matthieu LeBerre a, Théo Cojean b, Henri Robert c

a Learn Data & Robotics Laboratory (LDR), ESIEA, LAVAL, 53 000, France  
b Univ Lyon, Univ Gustave Eiffel, Univ Claude Bernard Lyon 1, LBMC UMRT 9406, Lyon, F-69622, France  
c Centre Hospitalier du Haut Anjou, Château-Gontier-Sur-Mayenne, 53 200, France

## ARTICLE INFO

- ACL tears  
- AI medical diagnosis  
- Arthrometry  
- GNRB®  
- Machine learning  
- Diagnostic accuracy  
- Knee anterior laxity  

## ABSTRACT

Purpose: GNRB is an arthrometer and alternative diagnostic method less expensive than MRI and more accurate than KT-1000 in Anterior Cruciate Ligament (ACL) tears detection. Dynamic knee laxity tests are more complex to analyze and will require a new solution of universal interpretation. The hypothesis is that using a solution based on Artificial Intelligence (AI) will allow us to obtain a more accurate and robust non-invasive diagnostic method than the current solution with three laxity thresholds.

Method: AI can enhance the reliability of this analysis by utilizing advanced algorithms and incorporating a wide range of additional parameters, leading to more precise diagnostics. The existing process solely rely on laxity differences obtained from the device, overlooking influential factors like clamping force. By considering a broader set of parameters and employing well-calibrated models a comparative study was performed between different Machine Learning (ML) models and Ensemble Learning to get the best compromise. The correction process will leverage statistical analysis of the current solutions.

Results: Association of Voting, Stacking and threshold laxity methods results report a 6% increase in accuracy and approximately 13% improvement in tear detection compared to the current solution with 1384 GNRB® measurements. Predicted diagnoses are also more prone to new data from patients unknown to the model and confirmed using a validation database.

Conclusion: A first ML model was introduced in ACL tears detection using GNRB device. GNRB coupled with ML was encouraging with better results than the current static diagnostic method. It could be integrated and recommended as a complementary solution to MRI.

## 1. Introduction

Anterior cruciate ligament (ACL) rupture is a common knee injury that involves complex movements such as cutting and pivoting. The diagnosis of this pathology is a public health issue because a patient must consult an average of three doctors to obtain a result (Micheo et al., 2010). The reliability of ACL tear diagnosis is currently dependent on the experience of the healthcare professional conducting the clinical examination, which includes Lachman test (Branch et al., 2010; Torg et al., 1976). However, in many cases, further examinations such as MRI may be required to confirm the diagnosis. MRI is the most commonly used non-invasive examination for diagnosing ACL tears, although partial rupture, scanning technique, or knee pain impacts its accuracy (Chang et al., 2013; Crawford et al., 2007; Ebrahimpour et al., 2014; Phelan et al., 2016). Less expensive and easier solutions without radiation exposure have therefore been developed. Moreover,

it cannot directly assess knee laxity and is mainly used to assess the associated tears.

In the 1980s, Americans introduced the KT1000 with dynamic laxity (Balasch et al., 1999). It measures the relative anterior tibial drawer movement to the femur, providing an objective measurement of tibial translation using an arthrometer. The Rolimeter (Schuster et al., 2004), developed by Roland Jacob, and stress radiography via Telos (Pässler & März, 1986) have been introduced as complementary diagnostic methods. However, many factors can affect the quality of the results, such as examiner experience, clamping force, positioning, or leg rotation. As a result, a large body of literature reports the inherent inaccuracy and poor reproducibility of these devices, resulting in subjective and unreliable results (Bouguennec et al., 2015; Collette et al., 2012; Jenny et al., 2017; Lefevre et al., 2014). Therefore, a new arthrometer, the GNRB®, has been developed.

| | GNRB® | | | | MRI | | | |
|---|---|---|---|---|---|---|---|---|
| | Complete | | Partial | | Complete | | Partial | |
| | Sn | Sp | Sn | Sp | Sn | Sp | Sn | Sp |
| Robert et al. (2009) | 70% | 99% | 80% | 87% | | | | |
| Klouche et al. (2015) | 92% | 96% | 92% | 98% | | | | |
| Di Iorio et al. (2014) | | | 72% | | 84% | 92% | | |
| Beauraain (2020) | 73% | | 62% | | 76% | | 30% | |
| Lefevre N | 84% | 81% | 87% | 87% | | | | |
| Beldame J | 62% | 75% | | | | | | |
| Phelan et al. (2016) | | | | | 87% | 93% | | |
| Bohu et al. (2012) | | | | | | | 32% | |

The GNRB® device (Genourob, Laval, France) represents the pioneering automated dynamic laximetry (ADL) system. It is one of the most effective non-invasive methods with superior accuracy and reproducibility than other devices. Saravia et al. (2020). However, the diagnosis is solely based on the absolute difference in laxity measured at 134 N between the healthy knee and the pathological knee according to three thresholds suggested by the manufacturer (Genourob, Laval) : 0 to 1.5 mm (healthy) ; 1.5 to 3.0 mm : (partial tear) and above 3 mm (total tear)

This static approach is not universal and explains the large differences in sensitivity and specificity obtained in different studies that can reach more than 20% (Beauraain, 2020). Others question the relevance of the thresholds and ask that they be re-evaluated (Mouarbes et al., 2018).

The hypothesis is that relying solely on the difference in laxity measured at 134 N may not be sufficient to achieve reliable results for patients worldwide, considering the recommended thresholds. Therefore, a new method is proposed in this study, which using a Machine Learning (ML) model to incorporate a broader range of parameters such as age, gender, height, weight, tightness, compliance, and other relevant data to enhance the accuracy of the diagnosis. The following problem can thus arise : Would the set of measurements performed by the GNRB® and the patient's data allow us to obtain a more accurate and universal solution using Machine Learning? The study assembled the largest database with 1384 GNRB® measurements from healthy and injured patients to address this scientific lock.

Firstly, GNRB® limitations will be discussed to explain the contribution of the proposed solution to the field of medicine. For this purpose, complementary approaches based on Machine Learning will suggest, each with improvements to reach an optimal ratio of sensitivity and specificity. Finally, the best solution will be confirmed through cross-validation using a new database collected at the Brest Hospital (France) to affirm or refute the hypothesis.

Intelligent decision algorithms for ACL tear detection will, to our knowledge, be a first in the literature. It could then allow obtaining a complementary diagnosis more reliable than the existing solutions thanks to the consideration of a large number of data and parameters. The decision to explore AI is based on its remarkable ability to “grasp general medical principles and apply them to new patients” (Obermeyer & Emanuel, 2016).

## 2. Materials and methods

Accurate clinical detection using non-invasive methods is crucial for determining the most effective treatment approach. Hence, this article primarily focuses on the GNRB® as an attempt to enhance the accuracy of its diagnosis. Nonetheless, arthroscopy is considered as the “gold standard” in numerous studies due to its high reliability, as it allows direct observation of the condition of the ACL by the surgeon (Crawford et al., 2007). Operative reports will serve as the basis for comparison throughout the study and provide the targets for ML models.

### 2.1. GNRB® and results limitations

The GNRB® is based on the Lachman (Torg et al., 1976) test but in an automated way to guarantee a high reproducibility and optimal knee flexion of 20° (Collette et al., 2012). While this explains the high reproducibility and accuracy, the universality of GNRB® diagnostics can be questioned. Table 1 shows a significant heterogeneity of results which can be explained by :

- an apparent lack of transparency especially for the clamping force which impacts the Laxity measurement (Alqahtani et al., 2018; Bouguennec et al., 2015). The GNRB® documentation recommends a maximum difference of 20 N between two measurements;
- the fact that the difference in laxity measured at 134 N is not universal and uses their own thresholds. Studies suggest a re-evaluation, especially for the 1.5 mm threshold (Mouarbes et al., 2018);
- the GNRB® allows for multiple measurements from 67 N to 200 N (Robert et al., 2009), but not all of the data are exploited. Other factors could also be considered, including patient gender, which has not been reported;

Due to more consistent and accurate results (Table 1), MRI remains the best method to date. On the other hand, dynamic laximetry, which allows economic and societal benefits while avoiding radiation, needs to be improved to be recommended in the same way as MRI (Gustafsson et al., 2020).

### 2.2. Database design

The first step is to obtain a balanced and realistic database because all the models proposed afterward will depend on the choices made.

#### 2.2.1. GNRB® data selection

A GNRB® database of 30,000 measurements performed on 1840 patients over a period of 2 ± 7 months after injury between 2008 and 2019 with an average of 30 ± 12 years old. MRI scans are also and have been performed in several centers using a Siemens or Philips 1.5 T MRI scanner according to a standard protocol for the knee: sagittal fat-suppressed (FS) T2-weighted, sagittal proton density (PD)-weighted, axial FS PD-weighted, coronal T2 and PD-weighted images. No sagittal or coronal oblique planes were performed in this series.

They have allowed us to prepare a batch of 5000 healthy patients and 869 with arthroscopically confirmed ACL rupture. Each consists of a unique set of measurements at diverse forces (between 67 N and 250 N) on one healthy and injured knee (or two healthy knees) of the same patient. They had to be made the same day under similar conditions (clamping force less than 20N). This choice explains why the number of exploitable data is voluntarily reduced.

The training and test base contains 85% of patients against 33% in the ideal because there are three classes. A model with the dominance
