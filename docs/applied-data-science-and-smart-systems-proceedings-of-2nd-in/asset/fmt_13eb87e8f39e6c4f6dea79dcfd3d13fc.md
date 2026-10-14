
[Table 13.4](#ch13.xhtml#tab13_4) shows that the CNN model achieved an accuracy of 83% on the training dataset with a corresponding loss of 0.35. On the testing dataset, the model performed even better, with an accuracy of 88% and a lower loss of 0.25. This indicates that the CNN model has been able to generalize well from the training data to the testing data, demonstrating its effectiveness in classifying the eye images correctly.

The performance of the model has been also analyzed graphically on the basis of their curves as shown in [Figure 13.9](#ch13.xhtml#fig13_9).

![Figure 13.9 Learning curves of CNN model](images/fig13_9_C.jpg)

[Figure 13.9 Learning curves of CNN model](#ch13.xhtml#R_fig13_9)

[Table 13.5](#ch13.xhtml#tab13_5) provides a summary of performance metrics related to precision, recall, and the F1 score for a specific model.

[Table 13.5 Performance summary.](#ch13.xhtml#R_tab13_5)

| Model || Recall || Precision || F1 score |

| --- | --- | --- | --- |

| CNN || 0.50 || 0.50 || 0.50 |

| --- | --- | --- | --- |

Similarly, the model has been also evaluated for binary class of the dataset i.e., for healthy eye and pink eye on the basis of precision, recall, and F1 score in [Table 13.6](#ch13.xhtml#tab13_6).

[Table 13.6 Class-wise performance metrics for eye classification.](#ch13.xhtml#R_tab13_6)

| Class || Precision || Recall || F1 Score |

| --- | --- | --- | --- |

| Healthy eye || 0.33 || 0.38 || 0.35 |

| --- | --- | --- | --- |

| Pink eye || 0.67 || 0.64 || 0.62 |

## V. Discussion

Conjunctivitis is a condition that has the potential to affect individuals across all age groups. However, it is observed that this phenomenon is more prevalent among the pediatric population and individuals in the young adult age group. This can be attributed to the fact that children and young adults often gather in educational institutions and workplaces, where they engage in close physical proximity and frequent bodily contact with one another. The exponential proliferation of the contagion is the primary factor contributing to the nearly two-fold increase in the afflicted population within the current calendar year (Hashmi, 2022).

According to the available sources, there has been a notable increase in conjunctivitis cases, with a rise of approximately 50–60%. The demographic primarily impacted by this phenomenon consists predominantly of individuals in their childhood stage of development. According to our research findings, it has been observed that approximately one out of every three children exhibits symptoms of red eyes or conjunctivitis (PTI, 2023). The observed data indicates a significant rise in the incidence of conjunctivitis cases, ranging from 10% to 15%, when compared to previous seasonal patterns. According to expert analysis, it has been determined that a significant proportion, potentially reaching up to 40%, of those impacted by the situation in question are children (Debroy, 2023).

In this paper, the study aims to contribute to the early and accurate detection of conjunctivitis, a contagious eye condition affecting millions worldwide. The obtained results demonstrate the CNN model’s performance in terms of accuracy, precision, loss, recall, and F1 score. The model showcases a notable accuracy level, particularly in distinguishing between healthy and conjunctivitis-affected eyes.

The CNN model demonstrated a precision, recall, and F1 score of 0.50. These results indicate that the model strikes a balance between correctly identifying positive instances (true positives) and minimizing false negatives. Nonetheless, it’s worth noting that an F1 score of 0.50 suggests there is potential for enhancing the model’s overall performance since higher precision, recall, and F1 score values are typically preferred for more accurate and dependable predictions. Likewise, the class-wise metrics indicate balanced performance for both healthy and conjunctivitis classes. However, certain limitations warrant consideration. The model’s performance may vary with factors like dataset size, diversity, and quality. Over fitting remains a concern, especially if the dataset is small or imbalanced.

## VI. Conclusion

The paper highlights the significance of the proposed CNN model for automating the detection of conjunctivitis using eye images. The model’s accuracy of 88.80% and efficiency in distinguishing between healthy and conjunctivitis-affected eyes offer a promising solution for aiding medical professionals in early diagnoses. This advancement in automated detection holds potential to enhance eye health management by enabling timely interventions and reducing transmission rates. In future, the work can be extended by increasing the dataset and developing an automated learning model which can perform multi-class classification of different types of conjunctivitis.

Overall, the paper underscores the valuable role of AI-powered diagnostic tools in improving conjunctivitis detection and overall eye health care.

## References

*   Azari, Amir A., and Amir Arabi. (2020). Conjunctivitis: a systematic review. Journal of ophthalmic & vision research. 15(3): 372–395. doi: [10.18502/jovr.v15i3.7456](http://dx.doi.org/10.18502/jovr.v15i3.7456)

*   Manjumdar, Pulak. (2010). Preliminary phytochemical and wound healing activity of zyziphus oenoplia (l) mill. PhD diss., Rajiv Gandhi University of Health Sciences (India), 1–24.

*   Erdin, Muh. and Patel, L. (2023). Early detection of eye disease using CNN. Int. J. Res. Appl. Sci. Engg. Technol. 11(4), 2683–2690.

*   Melih, G., Goceri, E., and Danisman, T. (2015). Automated detection of adenoviral conjunctivitis disease from facial images using machine learning. 2015 IEEE 14th Int. Conf. Mach. Learn. Appl. (ICMLA), 1204–1209.

*   Jae-Ho, H. (2022). Artificial intelligence in eye disease: Recent developments, applications, and surveys. Diagnostics, 12(8), 1927.

*   Hashmi MF, Gurnani B, Benson S, Price KL. Conjunctivitis (Nursing). (2022). Dec 6. In: StatPearls \[Internet\]. Treasure Island (FL): StatPearls Publishing; 2023 Jan–. PMID: 33760572.

*   [Kaggle](#ch13.xhtml#R_ref13_7). (2020). Eye diseases virus dateset vol 1. October 26.

*   Apeksha, K., Bawa, R. K., and Kumar, Y. (2023). Artificial intelligence techniques to predict the airway disorders illness: A systematic review. Arch. Comput. Method Engg., 30(2), 831–864.

*   Ajitesh, K. (2023). Different types of CNN architectures explained: Examples - Data analytics. Data Analyt., August 23.

*   Yogesh, K., Koul, A., and Mahajan, S. (2022). A deep learning approaches and fastai text classification to predict 25 medical diseases from medical speech utterances, transcription and intent. Soft Comput., 26(17), 8253–8272.

*   [Singh, Jaiteg, and Nandini Modi](#ch13.xhtml#R_ref13_11). (2019). Use of information modelling techniques to understand research trends in eye gaze estimation methods: An automated review. Heliyon, 5(12), 1–12.

*   Debrowski, Adam. (2022). Types of conjunctivitis: Bacterial, viral, allergic and others. Available at https://www.allaboutvision.com/en-in/conditions/conjunctivitistypes/ \[Accessed on Dec 10, 2023\]

*   Prateeti, M., Bhattacharyya, I., Mullick, M., Kumar, R., Roy, N. D., and Mahmud, M. (2021). iConDet: An intelligent portable healthcare app for the detection of conjunctivitis. Int. Conf. Appl. Intel. Informat., 29–42. Cham: Springer International Publishing.

*   Nangia, Aarti. (2023). Cases of conjunctivitis, other eye infection on rise in Delhi: Doctors. Available at [https://economictimes.indiatimes.com/news/india/cases-ofconjunctivitis-other-eye-infection-on-rise-in-delhidoctors/articleshow/102085752.cms](https://economictimes.indiatimes.com/news/india/cases-ofconjunctivitis-other-eye-infection-on-rise-in-delhidoctors/articleshow/102085752.cms) \[Accessed on Dec 9, 2023]
