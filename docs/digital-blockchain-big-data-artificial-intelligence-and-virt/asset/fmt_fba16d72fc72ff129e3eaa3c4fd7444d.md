
# Chapter 6 Drug development and clinical trial via artificial intelligence

## Abstract

Clinical trials and medication development have been profoundly impacted by artificial intelligence (AI), with deep learning techniques outperforming traditional machine learning tactics. Though its potential and accessibility are limited, high-throughput virtual screening (HTVS) has been proposed as an alternative to expensive and time-consuming methods. The chapter overviews computational drug development techniques that identify drug targets, validate drugs, and conduct clinical trials using artificial intelligence (AI). Additionally, by simply acquiring the governing equations from data, a novel deep learning technique has been described that is designed to build `PK/PD` models that can forecast patient response times and simulate the impact of unknown dosage regimens. The technique keeps the dose-concentration effect pharmacologically sound while enabling the model to predict treatment outcomes and replicate the patient's dosage schedule. Drug target interactions (DTIs) are essential for locating possible drugs and offering information on side effects and drug mechanisms. Additionally, ethical issues about social gaps, security of data, informed consent, medical consultation, empathy, as well as sympathy, are raised in the last section and affect AI-enabled clinical trials in the healthcare industry.

**Keywords:** drug target interactions, `PK/PD` models, high-throughput virtual screening, validation, ethical issues

## 6.1 Introduction

The application of machine learning (ML) methodologies in computer-aided drug development has increased markedly in recent years. The ability of deep learning methods, such as artificial neural networks with numerous hidden layers, to autonomously extract features from input data and model nonlinear input-output relationships has recently garnered heightened interest [[1]](#9783111573861_008368.xhtml#b_9783111574288-006_ref_001), [[2]](#9783111573861_008368.xhtml#b_9783111574288-006_ref_002), [[3]](#9783111573861_008368.xhtml#b_9783111574288-006_ref_003), [[4]](#9783111573861_008368.xhtml#b_9783111574288-006_ref_004), [[5]](#9783111573861_008368.xhtml#b_9783111574288-006_ref_005), [[6]](#9783111573861_008368.xhtml#b_9783111574288-006_ref_006). The characteristics of deep learning methods supplement conventional machine-learning methods that use molecular descriptors created by humans. Deep learning has made a somewhat tardy comeback to the drug discovery space, but in the interim, it has yielded an unprecedented wave of novel modeling techniques and applications. The continued advances in deep learning have proven beneficial to many domains within the chemical field [[7]](#9783111573861_008368.xhtml#b_9783111574288-006_ref_007), [[8]](#9783111573861_008368.xhtml#b_9783111574288-006_ref_008), [[9]](#9783111573861_008368.xhtml#b_9783111574288-006_ref_009), [[10]](#9783111573861_008368.xhtml#b_9783111574288-006_ref_010).

## References

[115] Dias R, Torkamani A. Artificial intelligence in clinical and genomic diagnostics. *Genome Medicine*. 2019 Nov 19;11(1):70.

[116] Jeblick K, Schachtner B, Dexl J, Mittermeier A, Stüber AT, Topalis J, Weber T, Wesp P, Sabel BO, Ricke J, Ingrisch M. ChatGPT makes medicine easy to swallow: An exploratory case study on simplified radiology reports. *European Radiology*. 2024 May;34(5):2817–25.

[117] Chen S, Kann BH, Foote MB, Aerts HJ, Savova GK, Mak RH, Bitterman DS. Use of artificial intelligence chatbots for cancer treatment information. *JAMA Oncology*. 2023 Oct 1;9(10):1459–62.

[118] Lee DG, Seo YS. Improving bug report triage performance using artificial intelligence based document generation model. *Human-centric Computing and Information Sciences*. 2020 Jun 16;10(1):26.

[119] Tsai SC. Using google translate in EFL drafts: A preliminary investigation. *Computer Assisted Language Learning*. 2019 Jul 4;32(5–6):510–26.

[120] Zhao H. Design of Intelligent Proofreading System Based on Artificial Intelligence. In *2021 3rd International Conference on Artificial Intelligence and Advanced Manufacture (AIAM)*. 2021 Oct 23 (pp. 159–62). IEEE.

[121] Buolamwini J, Gebru T. Gender shades: Intersectional accuracy disparities in commercial gender classification. In *Conference on fairness, accountability and transparency*. 2018 Jan 21 (pp. 77–91). PMLR.

[122] Gerlings J, Shollo A, Constantiou I. Reviewing the need for explainable artificial intelligence (xAI). *arXiv preprint arXiv:2012.01007*. 2020 Dec 2.

[123] Arrieta AB, Díaz-Rodríguez N, Del Ser J, Bennetot A, Tabik S, Barbado A, García S, Gil-López S, Molina D, Benjamins R, Chatila R. Explainable Artificial Intelligence (XAI): Concepts, taxonomies, opportunities and challenges toward responsible AI. *Information Fusion*. 2020 Jun 1;58:82–115.

[124] Adadi A, Berrada M. Peeking inside the black-box: A survey on explainable artificial intelligence (XAI). *IEEE Access*. 2018 Sep 16;6:52138–60.

[125] Meske C, Bunde E, Schneider J, Gersch M. Explainable artificial intelligence: Objectives, stakeholders, and future research opportunities. *Information Systems Management*. 2022 Jan 2;39(1):53–63.
