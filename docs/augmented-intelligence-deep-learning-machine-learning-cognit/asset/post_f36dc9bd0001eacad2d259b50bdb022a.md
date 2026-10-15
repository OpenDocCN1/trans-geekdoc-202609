
Artificial neural networks can be used for regression or classification modelling for prediction and automatic control. A large number of simulation data uses limited data sets. This structure is the foundation of deep learning, which is good at representation learning. Accordingly, artificial neural networks process and learn information from data via distributed information processing systems. One of the crucial properties of artificial neural networks is fault tolerance, which is approximately modelled on how the human brain operates. Neural networks have been widely applied to data analytics, clustering, classification, and automatic control engineering based on these characteristics. In real-world applications, such methods aim to analyse and classify medical data, recognize human faces, detect computer fraud, and deal with the nonlinearity of a system for better process control.

### 8.3.2.3. Evolutionary Computing (EC)

Evolutionary computation (EC) is a global optimization technique inspired by biological evolution and the subfield of artificial intelligence and soft computing studying these algorithms [29]. EC systems solve problems by inheritance, mutation, and selection, meta-heuristics, or stochastic optimization. An initial set of candidate solutions is generated and updated iteratively, such as removing less-desired solutions and including the noise. A population of individuals is subject to natural selection or artificial selection and alteration and hence progresses and adapts—i.e., raises fitness. EC is popular in computational intelligence as its outcomes in near-optimal solutions in a comprehensive range of frameworks [30] where there are numerous options and additions for specific data structures and problems.

### 8.3.2.4. Swarm Intelligence (SI)

COVID-19 pandemic is a dynamical complex system with swarm intelligence, and swarm intelligence (SI) is a part of the computational intelligence. It is collective behaviour exhibited by entities, mainly animals. Swarm intelligence is the collective behaviour of decentralized, self-organized systems. The idea is employed in work on artificial intelligence.

### 8.3.2.5. Artificial Immune Systems (AIS)

Artificial Immune Systems (AIS) are a class of computationally intelligent, rule-based machine learning systems inspired by the principles and processes of the vertebrate immune system. The artificial immune systems (AIS) area has grown dramatically in the last 10 years. AIS algorithms are computer programs modeled on different aspects of the human immune system and used to tackle various problems, from computer virus detection to data mining to robot control.

## 8.4. COVID-19 DIAGNOSIS TOOLS

Presently, the reverse transcription-polymerase chain reaction (RT-PCR)-based epidemiologic nucleic acid tests are used as the reference standard method to check COVID-19 infection [31]. Still, that research laboratory test is time-intensive, and the supply of test kits may have restricted access for a rapidly increasing suspicious population even for many developed countries such as the US, UK, USSR, Germany, etc... Most significantly, early false-negative or weakly positive RT–PCR test results were found in several later-confirmed cases, whereas extremely suspicious ‘Computed Tomography’ (CT) imaging features were extant [32, 33]. The treatment and screening of COVID-19 can be more effective when the deep learning method, CT features, and real-time RT–PCR results are integrated [34]. AI and deep learning can help in developing diagnostic tools and decide on treatment [35, 36]. Consequently, various diagnostic tools were developed based on the machine learning algorithm to fight COVID-19. For example, Apostolopoulos and Mpesiana (2020) applied transfer learning with CNN to identify COVID-19 from X-ray images covering community bacterial pneumonia, normal instances, and well-known COVID-19 infection. Transfer learning CNN was used to diagnose COVID-19 cases from X-ray datasets. The results indicated that VGG19 diagnosed COVID-19 confirmed cases with better accuracy on two- and three-classification problems than MobileNet v2, Inception, Xception, and Inception ResNet v2. The proposed approach can help develop a cost-effective, fast, and automatic COVID-19 diagnostic tool and reduce the exposure of medical workers to COVID-19. Similarly, [37] developed an automated ‘Computer-Aided Diagnosis’ (CAD) system for the detection of COVID-19 samples from healthy cases and cases with pneumonia via chest X-ray (CXR) images. Their study demonstrated the effectiveness of applying deep transfer learning techniques to identify COVID-19 cases with CXR images.

## 8.5. DATA SOURCE AND METHODOLOGY

According to the sources of data, the status of the Computational Intelligence for Diagnosis or Treatment of COVID-19 domain can be described, including the growth of publications, document types of publications, preferred journals, Most prolific countries and institutions, highly prolific authors, and their affiliations, co-occurrence network of categories and most preferred keywords in this section.

Web of Science (WOS) is the source database for our bibliometric analysis. This database provides access to over 75 million scientific works of literature from more than 5000 publishers around the world. It also provides a profile of more than 16 million authors and 70,000 institutions [38]. We retrieved the publications from the Web of Science database using a set of keywords related to Computational intelligence, Diagnosis, and COVID-19 (Table 1). A total of 61 papers were retrieved to meet our study. The database search happened on 17th November 2020. After extracting the available literature, we studied the titles and abstracts of those publications to evaluate their eligibility for bibliometric analysis. Publications were excluded if they did not refer to any CI-related keywords or did not focus on COVID-19. Due to a limited number of publications, articles irrespective of their study design were included in this study with no language restrictions. The study period was restricted to 2016 to 2020, whereas the COVID-19 epidemic started in December 2019; hence all the articles related to our search query were published in 2020.

### Table 1. Sample Data Description.

| Description | Results |
|---|---|
| Documents (NP) | 61 |
| Preferred Sources (Journals, Books, etc) | 40 |
| Keywords Plus (ID) | 117 |
| Author's Keywords (DE) | 241 |
| Timespan | 2020-2020 |
| Average citations per documents | 1.852 |
| Authors | 371 |
| Author Appearances | 384 |
| Authors of single-authored documents | 1 |
| Authors of multi-authored documents | 370 |
| Single authored documents | 1 |
| Documents per Author | 0.164 |
| Authors per Document | 6.08 |
| Co-Authors per Documents | 6.3 |
| Collaboration Index | 6.17 |

### Search Query.

| Sl No | Search Query | Results |
|---|---|---|
| # 1 | TS=(Computational Intelligence or Neural Networks or Fuzzy Systems or Evolutionary Computation) Indexes=SCI-EXPANDED, SSCI, A&HCI Timespan=2016-2020 | 137,313 |
| # 2 | TS=(Diagnosis or Treatment) Indexes=SCI-EXPANDED, SSCI, A&HCI Timespan=2016-2020 | 1,637,172 |
| # 3 | TS=(Coronavirus or Corona Virus or COVID-19) Indexes=SCI-EXPANDED, SSCI, A&HCI Timespan=2016-2020 | 49,835 |
| # 4 | #3 AND #2 AND #1 Indexes=SCI-EXPANDED, SSCI, A&HCI Timespan=2016-2020 | 61 |

In this study, we used the ‘Bibliometrix’ package [39] (http://www.bibliometrix.org) developed by [40] Aria & Cuccurullo (2017) in R (an open-source statistical application) to perform the analysis. Bibliometrix package is well-known for its broad features and is used in a growing number of publications [41, 42].

Visualization software called VOSviewer was used to conduct a bibliometric study on Computational intelligence, Diagnosis, and COVID-19. VOSviewer software is a tool for creating and visualizing bibliometric maps, such as journals, research, or individual publications. These networks can be created based on citations, co-citation, bibliographic coupling, or co-authorship relations [43]. This VOSviewer software also offers text mining functionality that can be used to construct and visualize co-occurrence networks of important terms extracted from a body of scientific literature (www.vosviewer.com). We only used 49,835 publications with the keyword “Coronavirus or Corona Virus or COVID-19” (# 3), 1,637,172 publications with the keyword “Diagnosis or Treatment” (# 2) and 137,313 publications with the keyword “Computational Intelligence or Neural Networks or Fuzzy Systems or Evolutionary Computation” (# 1) that were retrieved from Web of Science database for the bibliometric analysis presented in this study. Only 61 document results were extracted using the keyword set # 4 (#3 AND #2 AND #1) from the web of science database. We did not consider papers from other sources since most of these publications have not been peer-reviewed and are not available online in the form of preprint publications. Excel 2019 was used to preprocess the data of the clustering table, to draw the geographic density distribution maps.

## 8.6. RESULTS ANALYSIS AND DISCUSSION

As we are involved in the chronological nature of research and publications, we have considered the key phrases like ‘Computational Intelligence’ ‘Neural Networks’ ‘Fuzzy Systems’ ‘Evolutionary Computation’ ‘Diagnosis’ ‘Treatment’ ‘Coronavirus’ ‘Corona Virus’ and ‘COVID-19’ to get a more extensive coverage and to find out potential areas for future research on COVID-19. Besides, we have included the keywords like ‘SARS,’ ‘MERS,’ ‘severe acute respiratory syndrome,’ and ‘Middle East Respiratory Syndrome’ to represent the historical alliance with COVID-19. Moreover, we refine our query results with the ‘SCI-EXPANDED, SSCI, A&HCI’ category of WoS, which allows us to preserve the focus to the publications which consider different aspects. Table 1 reviews the search results:
