# Systemic Lupus Erythematosus: How Machine Learning Can Help Distinguish between Infections and Flares

Iciar Usategui 1, Yoel Arroyo 2, Ana María Torres 3,4, Julia Barbado 5 and Jorge Mateo 3,4,*

+   1 Department of Internal Medicine, Hospital Clínico Universitario, 47005 Valladolid, Spain
+   2 Department of Technologies and Information Systems, Faculty of Social Sciences and Information Technologies, Universidad de Castilla-La Mancha (UCLM), 45600 Talavera de la Reina, Spain
+   3 Medical Analysis Expert Group, Institute of Technology, Universidad de Castilla-La Mancha (UCLM), 16071 Cuenca, Spain
+   4 Medical Analysis Expert Group, Instituto de Investigación Sanitaria de Castilla-La Mancha (IDISCAM), 45071 Toledo, Spain
+   5 Department of Internal Medicine, Hospital Universitario Río Hortega, 47012 Valladolid, Spain
+   * Correspondence: jorge.mateo@uclm.es

Abstract: Systemic Lupus Erythematosus (SLE) is a multifaceted autoimmune ailment that impacts multiple bodily systems and manifests with varied clinical manifestations. Early detection is considered the most effective way to save patients’ lives, but detecting severe SLE activity in its early stages is proving to be a formidable challenge. Consequently, this work advocates the use of Machine Learning (ML) algorithms for the diagnosis of SLE flares in the context of infections. In the pursuit of this research, the Random Forest (RF) method has been employed due to its performance attributes. With RF, our objective is to uncover patterns within the patient data. Multiple ML techniques have been scrutinized within this investigation. The proposed system exhibited around a 7.49% enhancement in accuracy when compared to k-Nearest Neighbors (KNN) algorithm. In contrast, the Support Vector Machine (SVM), Binary Linear Discriminant Analysis (BLDA), Decision Trees (DT) and Linear Regression (LR) methods demonstrated inferior performance, with respective values around 81%, 78%, 84% and 69%. It is noteworthy that the proposed method displayed a superior area under the curve (AUC) and balanced accuracy (both around 94%) in comparison to other ML approaches. These outcomes underscore the feasibility of crafting an automated diagnostic support method for SLE patients grounded in ML systems.

Keywords: Systemic Lupus Erythematosus; medical treatment; machine learning; artificial intelligence

# 1. Introduction

Systemic Lupus Erythematosus (SLE) is a chronic autoimmune affliction that affects various physiological systems. It serves as an exemplary autoimmune disorder, and its intricate nature poses significant challenges. The varied clinical presentations of SLE, coupled with distinct complexities in both diagnosis and treatment, present a formidable task for healthcare professionals. The emergence of multiple mechanisms results in the breakdown of self-tolerance and subsequent organ dysfunction. Progress in elucidating the molecular and cellular foundations of this condition, in conjunction with the identification of genetic variations, contributes to a more profound comprehension of its pathogenesis, offering promise for therapeutic advancements in the near future.

Commonly known as lupus, it varies in prevalence depending on geographic location, ethnicity, and research study design. In the United States, an estimated 241 cases per 100,000 adults have been reported, while in Spain, the updated figure is 210 cases per 100,000 inhabitants [1]. The Lupus Foundation of America estimates that approximately 161,000 to 322,000 individuals in the U.S. are affected by SLE, translating to a prevalence