
Marcos, A. P., Rodovalho, N. L. S., & Backes, A. R. (2019). Coffee leaf rust detection using convolutional neural network. 2019 XV Workshop de Visão Computacional (WVC), 38–42. 10.1109/WVC.2019.8876931

McQueen, R. J., Garner, S. R., Nevill-Manning, C. G., & Witten, I. H. (1995). Applying machine learning to agricultural data. Computers and Electronics in Agriculture, 12(4), 275–293. doi:10.1016/0168-1699(95)98601-9

Mengistu, A. D., Mengistu, S. G., & Alemayehu, D. M. (2016). Image analysis for ethiopian coffee plant diseases identification. IJBB, 10(1).

Moat, Williams, Baena, Wilkinson, Demissew, Challa, Gole, & Davis. (2017). Coffee farming and climate change in ethiopia: impacts, forecasts, resilience and opportunities-summary. Academic Press.

Mohapatra, Prasad, & Nayak. (2021). Wheat Rust Disease Detection Using Deep Learning. Data Science and Data Analytics: Opportunities and Challenges, 191.

Nanda, Mohapatra, & Satpathy. (2023). Wheat Rust Disease Detection Using Convolutional Neural Network. Journal of Harbin Engineering University, 44(6), 253-259.

Pinto, C., Furukawa, J., Fukai, H., & Tamura, S. (2017). Classification of green coffee bean images based on defect types using convolutional neural network (CNN). 2017 International Conference on Advanced Informatics, Concepts, Theory, and Applications (ICAICTA), 1–5. 10.1109/ICAICTA.2017.8090980

Prakash, R. M., Saraswathy, G., Ramalakshmi, G., Mangaleswari, K., & Kaviya, T. (2017). Detection of leaf diseases and classification using digital image processing. In 2017 international conference on innovations in information, embedded and communication systems (ICIIECS). IEEE.

Sinshaw, N. T., Assefa, B. G., & Mohapatra, S. K. (2021). Transfer Learning and Data Augmentation Based CNN Model for Potato Late Blight Disease Detection. 2021 International Conference on Information and Communication Technology for Development for Africa (ICT4DA), 30-35. 10.1109/ICT4DA53266.2021.9672243

Sinshaw, N. T., Assefa, B. G., Mohapatra, S. K., & Beyene, A. M. (2022). Applications of Computer Vision on Automatic Potato Plant Disease Detection: A Systematic Literature Review. Computational Intelligence and Neuroscience, 2022, 7186687. doi:10.1155/2022/7186687 PMID:36419507

Sorte, L. X. B., Ferraz, C. T., Fambrini, F., dos Reis Goulart, R., & Saito, J. H. (2019). Coffee leaf disease recognition based on deep learning and texture attributes. Procedia Computer Science, 159, 135–144. doi:10.1016/j.procs.2019.09.168

Suhartono. (2013). Expert system in detecting coffee plant diseases. Int. J. Electr. Energy, 1(3), 156–162.

Varshney, S., & Dalal, T. (2016). Plant disease prediction using image processing techniques-a review. International Journal of Computer Science and Mobile Computing, 5(5), 394–398.

Vínuesa, R., Azizpour, H., Leite, I., Balaam, M., Dignum, V., Domisch, S., Felländer, A., Langhans, S. D., Tegmark, M., & Fuso Nerini, F. (2020). The role of artificial intelligence in achieving the sustainable development goals. Nature Communications, 11(1), 1–10. doi:10.1038/s41467-019-14108-y PMID:31932590

Welteji, D. (2018). A critical review of rural development policy of ethiopia: Access, utilization and coverage. Agriculture & Food Security, 7(1), 1–6. doi:10.1186/s40066-018-0208-y

Yadessa, A., Burkhardt, J., Bekele, E., Hunderra, K., & Goldbach, H. (2020). The major factors influencing coffee quality in ethiopia: The case of wild arabica coffee (coffea arabica l.) from its natural habitat of southwest and southeast afromontane rainforests. African Journal of Plant Science, 14(6), 213–230. doi:10.5897/AJPS2020.1976

Zeru, A. (2006). Diversity of arabica coffee populations in afromontane rainforests of Ethiopia in relation to colleotrichum kahawae and gibberella xylarioides [Ph.D. dissertation]. Addis Ababa University.

## Chapter 6

## COVID-19 Classification With Healthcare Images Based on ML–DL Methods

Shreeharsha Dash
Odisha University of Technology and Research, India

Subhalaxmi Das
Odisha University of Technology and Research, India

### ABSTRACT

COVID-19 is the contagious ailment caused by Sars-Cov-2. This causative 2019-nCoV is a communication to the lines of millions of people. This study employs ML and DL epitomes to determine sickness along with predicting if a person is afflicted with the virus as the previous reports can examine the data pre-processing, feature extraction, classification, evaluation of experimental results to find advanced fact-finding directions around COVID-19 classification employing machine-deep approaches. The comparison shows that chest x-rays and CT are the most frequently used data in the diagnosis of COVID-19 rather than RT-PCR, and that the most-used test techniques were found to be insensitive and less beneficial after changing the limited number of datasets. This study suggests image preprocessing, exploratory data analysis, feature extraction (LBP), and other ML as well as DL classification methods. It attempts to minimise some of the issues that have been addressed for early identification for future work and studies.

### 1. INTRODUCTION

### 1.1. Coronavirus

Coronavirus is a broad family of infectious agents spreading out incurable health problems to heavy-handed sickness namely MERS-CoV and SARS-CoV. On December 31, 2019, Wuhan, in the Hubei province of China, reported to the World Health Organization (WHO) that instances of pneumonia with an unknown chronic infection had been found. This slow-moving illness is characterized by a protracted incubation

### Figure 1. Comparisons of RT-PCR, CXR images, and CT scan images used for COVID-19 detection

![](img/20813928ec98c7f6fbdbab0d52bde2f1_132_0.png)

period and progressive disease. On 11 March 2020, the WHO declared the COVID as an epidemic as it spread out all over the world with a very quick manner in a very short period. This pandemic is not only a health emergency; it is also a socioeconomic emergency of unprecedented proportions. It has the potential to have devastating social, economic, and political repercussions that will leave permanent wounds, stressing every nation it touches. Under the direction of the UN Resident Coordinators, the WHO and the Global Humanitarian Response Plan lead the health response, while UNDP (United Nations Development Programme) is in charge of the technical lead for the UN's socioeconomic recovery.

As soon as possible, anyone who fear they may have COVID-19 should find out whether they are infected so they may get the right care, isolate themselves, and let those they have had close contact with known (Benmalek et al., 2021). RT-PCR (Real-Time Reverse Transcription - Polymerase Chain) is a method of collecting samples from a individual's nasal or gullet, two areas of the body where the coronavirus is presumably to cluster. The material is extracted, during which genetic information is separated from potential viruses. A specific chemical is used in conjunction with PCR (polymerase chain reaction) equipment (thermal cycler) to start a process that produces millions of facsimiles of the SARS-CoV-2 virus and its transcriptome. One of the chemicals produces a laser beam when the sample contains SARS-COV-2. The PCR machine tracks the light beam, which demonstrates a cocksure test result for the presence of COVID (Shah et al., 2021).

Although RT-PCR can clearly detect coronavirus disease, it has a significant false negative rate, which occurs when the model prognosticates a negative sequel but the result is positive (false negative). In addition, RT-PCR is not widely available in many parts of the world. As a result, medical imaging such as computed tomography (CT) and chest x-rays (CXR), which are available in most medical or hospital settings, may be the best option for detecting this infection. If RT-PCR is not available, CT scan or X-ray are readily available. In addition, RT-PCR is extravagant and tedious for diagnosis. This requires the use of special equipment and takes at least 24 hours. Chest imaging has been shown to be useful in the progression of this lung disease (Benmalek et al., 2021). In addition, healthcare workers need adequate training to collect samples for PCR, whereas CT and X-ray pictures are comparatively convenient and create (Zhao et al., 2020) shown in Figure 1.

Surprisingly, research has demonstrated that a chest X-ray and a CT can detect COVID-19-related lung abnormalities. A radiologist's services are required for this assessment. Because radiologists are in short supply and there are many COVID-19 patients, system is needed to assist radiologists and medical
