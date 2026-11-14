
22. Doma, M. K., Padmanandam, K., Tambvekar, S., Kumar, K., Abdulgalil, B., Thakur, R. N., Artificial intelligence-based breast cancer detection using WPSO. Int. J. Oper. Res. Inf. Syst. (IJORIS), 13, 2, 1–16, 2022.

23. Batool, M., Ahmad, B., Choi, S., A structure-based drug discovery paradigm. Int. J. Mol. Sci., 20, 11, 2783, 2019.

24. Ramesh, S., Vallinayagam, S., Rajendran, K., Rajendran, S., Rathinam, V., Ramesh, S., Computer-aided drug designing–modality of diagnostic system, in: Biomedical Signal Processing for Healthcare Applications, pp. 195–218, CRC Press, United States, 2021.

25. Mahapatra, M.K. and Karuppasamy, M., Fundamental considerations in drug design, in: Computer Aided Drug Design (CADD): From Ligand-Based Methods to Structure-Based Approaches, vol. pp. 17–55, Elsevier, The Netherlands, 2022.

26. Imudeen, A. and Nayyar, A., Novel designs of smart healthcare systems: Technologies, architecture, and applications, in: Machine Learning for Critical Internet of Medical Things: Applications and Use Cases, pp. 125–151, Springer International Publishing, Cham, Germany, New York City, 2022.

27. Jadala, V.C., Pasupuleti, S.K., Yellamma, P., Deep Learning analysis using ResNet for early detection of cerebellar ataxia disease, in: 2022 International Conference on Advancements in Smart, Secure and Intelligent Computing (ASSIC), pp. 1–6, IEEE, 2022, November.

28. Yazhini, A., Chakraborti, S., Srinivasan, N., Protein structure, dynamics and assembly: Implications for drug discovery, in: Innovations and Implementations of Computer Aided Drug Discovery Strategies in Rational Drug Design, pp. 91–122, 2021.

29. Fischer, A., Smiesko, M., Sellner, M., Lill, M.A., Decision making in structure-based drug discovery: Visual inspection of docking results. J. Med. Chem., 64, 5, 2489–2500, 2021.

30. Padmanandam, K., Rajes, M. V., Upadhyaya, A. N., Chandrashek, B., Sah, S., Artificial intelligence biosensing system on hand gesture recognition for the hearing impaired. Int. J. Oper. Res. Inf. Syst. (IJORIS), 13, 2, 1–13, 2022.

## AI Models for Biopharmaceutical Property Prediction

Bancha Yingngam

Department of Pharmaceutical Chemistry and Technology, Faculty of Pharmaceutical Sciences, Ubon Ratchathani University, Ubon Ratchathani, Thailand

### Abstract

Accurate and reliable prediction of drug properties is crucial in the biopharmaceutical industry because they directly impact drug efficacy and safety. However, the traditional experimental methods used to determine these properties are often expensive, time-consuming, and impractical, hindering efficient drug discovery and development. In recent years, machine learning (ML) and artificial intelligence (AI) techniques have gained popularity for predicting biopharmaceutical properties. This chapter aims to provide a comprehensive overview of AI models in biopharmaceutical property prediction. It covers key areas such as the critical importance of accurate prediction, traditional challenges, introduction to AI models, their underlying principles, advantages, challenges, recent advances, and future directions. The chapter consolidates the latest advancements in AI models tailored for predicting biopharmaceutical properties and explores alternative approaches, integrates AI techniques, and offers a focused and comprehensive overview. It discusses recent advances in ML and AI models, including deep learning and ensemble models, and their potential applications in drug discovery and development. Additionally, it addresses future directions and challenges in developing and implementing AI models for biopharmaceutical property prediction. In summary, this chapter presents a novel contribution by consolidating the latest advancements in AI models specifically designed for predicting biopharmaceutical properties.

**Keywords:** Artificial intelligence, machine learning, biopharmaceuticals, property prediction, validation, big data

### List of Abbreviations

- ADME: absorption, distribution, metabolism, and excretion
- AI: artificial intelligence
- CNNs: convolutional neural networks
- DDIs: drug-drug interactions
- GPCRs: G protein-coupled receptors

Email: bancha.y@ubu.ac.th

- HTS high-throughput screening
- LSTM long short-term memory
- MD molecular dynamics
- ML machine learning
- MLP multilayer perceptron
- PBD Protein Data Bank
- PCA principal component analysis
- QM/MM quantum mechanics/molecular mechanics
- ReLU rectified linear unit
- RNNs recurrent neural networks
- SVMs support vector machines

### 13.1 Introduction

The discovery and development of drugs play a critical role in modern healthcare by providing essential treatments for various diseases [1, 2]. One of the important strategies is biopharmaceutical property prediction. Biopharmaceuticals are a class of drugs that are produced using living organisms, such as bacteria, yeast, or mammalian cells [3]. These drugs are also sometimes called biologics. Unlike traditional small-molecule drugs that are chemically synthesized, biopharmaceuticals are produced using recombinant DNA technology, which involves inserting the genetic material that codes for the desired therapeutic protein into the cells of a living organism [4]. Biopharmaceuticals can be used to treat a wide range of diseases, including cancer, autoimmune disorders, and infectious diseases. They can be designed to target specific proteins or cells in the body, making them highly targeted and often more effective than traditional small-molecule drugs. Biopharmaceuticals can also be modified to improve their stability and reduce their immunogenicity or the likelihood of triggering an immune response in the body [5]. Examples of biopharmaceuticals include monoclonal antibodies, which are used to treat cancer and autoimmune disorders, and therapeutic proteins, such as insulin and growth hormone, which are used to treat diabetes and growth disorders. Other examples include vaccines, which are used to prevent infectious diseases, and gene therapies, which are used to treat genetic disorders (Figure 13.1). Biopharmaceuticals are a rapidly growing segment of the pharmaceutical industry, and they represent a major area of innovation in drug development [3]. They offer the potential for more effective and targeted treatments for a wide range of diseases, and they are likely to play an increasingly important role in the future of medicine [4].

There are various biopharmaceutical products available in the market and under development to treat various diseases and conditions. Some examples of biopharmaceutical products currently being used are Humira (adalimumab), a drug that treats rheumatoid arthritis, psoriasis, Crohn’s disease, and other inflammatory conditions, manufactured by AbbVie Inc.; Rituxan (rituximab), used to treat non-Hodgkin’s lymphoma and other cancers, manufactured by Genentech, Inc.; Avastin (bevacizumab), which inhibits the growth of blood vessels that supply tumors and treats cancer, manufactured by Genentech, Inc.; Herceptin (trastuzumab) targets the HER2 protein that is overexpressed in some types of

### Biopharmaceuticals

| **Monoclonal antibodies** | Antibodies produced from a single type of immune cell and are designed to bind to specific proteins on cancer cells, autoimmune disorders, and other diseases. |
| **Recombinant proteins** | Proteins that are produced by genetic engineering techniques, are used to replace or supplement defective or supplemental proteins in the body. |
| **Cell therapy** | The use of living cells as therapeutic agents to treat or prevent disease. |
| **Vaccines** | Substances used to stimulate an individual's immune system to produce an immune response to a specific disease-causing organism, such as bacteria or viruses. |
| **Gene therapy** | A type of treatment that involves the delivery of genetic material to a patient's cells to treat or prevent disease. |
| **Small molecules** | Organic compounds with a low molecular weight, are typically used as drugs that interact with specific target molecules in the body. |

Figure 13.1 Categories of biopharmaceuticals.

breast cancer and is manufactured by Genentech, Inc.; and Keytruda (pembrolizumab), which blocks PD-1, a protein that suppresses the immune system's ability to attack cancer cells and is manufactured by Merck & Co., Inc. In addition, there are some upcoming biopharmaceutical products, such as aducanumab, currently under development by Biogen, Inc. for the treatment of Alzheimer's disease by targeting beta-amyloid protein, tanezumab, currently under development by Pfizer Inc. and Eli Lilly and Company for the treatment of chronic pain by targeting nerve growth factor, and erenumab, a drug approved for migraine prevention that targets calcitonin gene-related peptide, being developed by Amgen Inc. and Novartis AG.

Biopharmaceutical properties encompass the physical, chemical, and biological traits of drugs or biopharmaceutical products that dictate their pharmacological and therapeutic effects. These properties comprise factors such as solubility, permeability, stability, bioavailability, absorption, distribution, metabolism, excretion, toxicity, and efficacy [2]. Biopharmaceutical properties can significantly impact drug pharmacokinetics and pharmacodynamics and ultimately determine the therapeutic efficacy and safety profile of drugs. Precise prediction of biopharmaceutical properties is crucial in drug discovery and development, as it can help identify promising drug candidates, optimize drug design, and reduce the time and cost of clinical trials.

Despite its importance, predicting the biopharmaceutical properties of drug candidates remains a primary obstacle in drug development. Traditional experimental approaches to determining these properties are expensive, time-consuming, and sometimes impractical, creating a need for accurate and reliable predictive methods [6]. The emergence of machine learning (ML) and artificial intelligence (AI) techniques, however, has revolutionized the field of drug discovery and development by enabling the rapid and accurate prediction of biopharmaceutical properties [7, 8]. AI refers to the ability of machines or computer systems to perform tasks that typically require human intelligence, such as learning, reasoning, problem solving, and decision making [2]. AI systems are designed to process vast amounts
