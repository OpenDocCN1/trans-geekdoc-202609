
This shows that an AI can reliably evaluate colonoscopy biopsies at a rate that is on par with a practicing pathologist. The progress of AI applications in the medical arena suggests that AI will eventually be employed for the diagnostic of CRC despite the dearth of systematic research.

## IV. Related work

Significant advances have been made by AI techniques in the health arena to demonstrate clinical application potential. As a result, ([Davri et al., 2022](#ch16.xhtml#ref16_5)) used histopathology images to review existing research on AI in CRC. According to the authors, DL algorithms in histopathology are capable of diagnosing, identifying the features of histological images related to prognosis, predicting clinical-based molecular phenotypes, and evaluating the specific components of the tumor.

Similarly, ([Mitsala et al., 2021](#ch16.xhtml#ref16_19)) investigated the usefulness of AI systems in medical therapy and diagnosis by yielding numerous outstanding outcomes. They stated that AI-assisted procedures in routine screening are a critical step in lowering CRC incidence rates. In this approach, many researchers have used AI algorithms to identify and diagnose CRC, but they also confront significant challenges, as shown in [Table 16.2](#ch16.xhtml#tab16_2). This section covers the work done by the researchers to detect CRC using various ML and DL techniques along with the research gaps.

[Table 16.2 Comparative analysis of CRC](#ch16.xhtml#R_tab16_2)

| Author’s name || Year of publication || Dataset || Techniques || Outcome || Limitation |
| --- | --- | --- | --- | --- | --- |
| Zhang et al. || 2019 || 1104 endoscopic non-polyp images, 826 polyp images || CNN || Accuracy: 86% AUC: 1 || Class imbalance |
| Yamada et al. || 2019 || ImageNet dataset || CNN || Sensitivity: 97% AUC: 0.98% || The system performed weak in order to detect lesions in the different areas of the medical image |
| Misawa et al. || 2016 || 1079 narrow band imaging images || CNN || Specificity: 63.3% Accuracy: 76.5% || Unable to classify correctly because of the limited dataset |
| Geetha et al. || 2016 || 703 images || Hand crafted LBP || Sensitivity: 95% Specificity: 97% || Model trained with limited dataset |
| Ito et al. || 2018 || 41 cases of colon endoscopies yielded 190 pictures of colon lesions || CNN using machine learning algorithms || Accuracy: 81.2% || High cost, low efficiency |
| Yu et al. || 2016 || 18 colonoscopy videos || CNN || Sensitivity: 71% || Limited GPU memory, specific length of video clips were used |
| Figueiredo et al. || 2019 || 1680 cases of polyps and 1360 frames of healthy mucosa || SVM || Sensitivity: 99% Specificity: 85% Accuracy: 91% || The model failed to evaluate the dimension of colorectal polyp |
| Billah et al. || 2017 || 14,000 still images || CNN || Prediction rate: 98.6% || Consumes more processing time |
| Ozawa et al. || 2020 || 16,418 images || CNN || Sensitivity: 92% Accuracy: 83% || Less number of training images were used |
| Urban et al. || 2018 || 8,641 hand-labeled images || CNN || Sensitivity: 90% || The model failed to indicate the histology of polyps |
| Tsai et al. || 2009 || CRC-VAL-HE-7K || ResNet101 || Accuracy: 98.81% || Class imbalance issue |
| Ho et al. || 2022 || 66,191 images || AI learning models || Sensitivity: 97.4% Specificity: 60.3% Accuracy: 79.3% AUC: 91.7% || Small dataset |

## V. Research methodology

The study of AI is becoming more interested in areas such as algorithms and gadgets that enable people to tackle technically challenging issues. Researchers also use AI to identify epidemics’ environmental and epidemiological patterns to anticipate outbreaks. This is being done to prevent epidemics from occurring. Mathematical models and DL can analyze vast amounts of data to offer insight into the next likely source of illness. Ecologists can protect and monitor prospective host species more effectively with the help of these projections, which ultimately helps them prevent future outbreaks. In epidemiology, AI is currently being utilized to help with disease prevention and management and tracking and forecasting ([Koul et al., 2023](#ch16.xhtml#ref16_14)). New situations, such as the current coronavirus pandemic, provide opportunities for AI to have the most impact. We should have high hopes that international cooperation will improve due to the increased use of AI in medical systems. This will allow us to battle epidemics better. Medical practitioners can employ AI techniques to aid them in making more accurate and simpler judgments based on patients’ experiences and historical facts ([Koul et al., 2022](#ch16.xhtml#ref16_15); [Kumar et al., 2023](#ch16.xhtml#ref16_16)).

The research methodology for the proposal is mentioned as under:

*   The research primarily focuses on a literature review, in which the datasets, approaches, and outcomes of various researchers working on predicting CRC using multiple AI techniques are presented.

*   Various current techniques to reduce the use of the limited dataset, modeling errors, dereliction of models, and class imbalance will be examined to find new possible outcomes.

*   As illustrated in [Figure 16.1](#ch16.xhtml#fig16_1), an open-source dataset of different types of CRC such as tumors, stroma, complex, lymph, debris, mucosa, and adipose can be used for implementation.

    ![Figure 16.1 System design for CRC detection](images/fig16_1_C.jpg)

    [Figure 16.1 System design for CRC detection](#ch16.xhtml#R_fig16_1)

*   Initially, the data can pre-process to eliminate noisy signals, missing values, NAN values, etc., thereby enhancing the data quality.

*   Later, exploratory data analysis can be performed to classify the types of CRC to aid us in a better understanding of the data.

*   Cancerous features can be extracted from the CRC dataset using various feature extraction and scaling strategies.

*   To identify and classify different types of CRC, multiple learning models can be used, and their performance will be assessed.

*   Later, propose a novel hybrid deep learning model for the early prediction of different types of CRC.

*   In the end, accuracy, loss, recall, precision, Fscore, performance testing, etc., can be used to validate the proposed model’s implemented results during both the training and testing phase.

## VI. Conclusion

The study assists readers (physicians, analysts, doctors, and so on) in identifying previously utilized strategies or algorithms used by the researchers to detect CRC. In this research, we first focus on the limitations of the researchers’ work, such as optimizing the model and loss function and examine its ability on the significant histopathological dataset. Later, an AI-based model can be designed to assist end users in detecting anomalies such as polyps to enhance the diagnosis of CRC in a short period. The suggested models can be verified further for real-time images to test its efficacy.

## References

*   [American Cancer Society](#ch16.xhtml#R_ref16_1). (2020). Colorectal cancer facts & figures 2020–2022. Published Online, 48.

*   Billah, Mustain, Sajjad Waheed, and Mohammad Motiur Rahman. (2017). An automatic gastrointestinal polyp detection system in video endoscopy using fusion of color wavelet and convolutional neural network features. International journal of biomedical imaging. vol. 2017. 1–9. [https://doi.org/10.1155/2017/9545920](http://dx.doi.org/10.1155/2017/9545920)

*   [Chaplot, N., Dhiraj, P., Yogesh, K., and Pushpendra Singh, S.](#ch16.xhtml#R_ref16_3) (2023). A comprehensive analysis of artificial intelligence techniques for the prediction and prognosis of genetic disorders using various gene disorders. Arch. Computat. Method Engg., 30(5), 3301–3323.

*   [Cui, M. and David, Y. Z.](#ch16.xhtml#R_ref16_4) (2021). Artificial intelligence and computational pathology. Lab. Invest., 101(4), 412–422.
