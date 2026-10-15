# TABLE 7.4

# Summary of customized deep learning algorithm evaluation methods for COVID-19 detection using CT-scan image [5]

| Authors | He et al. [72] | Zheng et al. [73] | Singh et al. [74] | Farid et al. [75] |
|---|---|---|---|---|
| Techniques | CRNet | DeCoVNet | MODE-CNN | CNN |
| Data Source | Italian Society of Medical and Interventional Radiology COVID-19 Database COvid-CT | Union Hospital Tongji Medical College Huazhong University of Science and Technology | Covid-19 patient chest CT images | Kaggle benchmark dataset |
| Number of samples (Images) | Total-746
COVID-19-349
Non-COVID-397 | 630 | Total-150
COVID-19-75
Non-COVID-75 | Total-102
COVID-19-51
SARS-51 |
| Data partitioning | Training-60%
Validation-15%
Testing-25% | Training-80%
Testing-20% | Various portions of training and testing dataset | 10-fold-cross-validation |
| Performance Evaluation (%) | Accuracy-95.2
Sensitivity-93.3
Specificity-100
Precision-100 | Accuracy-95.2
Sensitivity-93.3
Specificity-100
Precision-100 | Accuracy-95.2
Sensitivity-93.3
Specificity-100
Precision-100 | Accuracy-95.2
Sensitivity-93.3
Specificity-100
Precision-100 |

solutions for COVID-19, yet the detection of the patients by means of processes other than RT-PCR is still within research. The detection process using X-ray and CT-scan images is still referred to as an additional measure to the RT-PCR test. This chapter reviews the AI application in the area of deep learning algorithms with the stress into the rapidly explored method ResNet for COVID-19 analysis. The robustness of ResNet provides promising results, but still there is room for improvements. The chapter review provides discussion based on the taxonomy considered for the classification of the methods. The methods are primarily classified into the pretrained model, where the already -trained models with the similar type of the disease are retrained with the addition of COVID-19 data. The second method is the customized deep learning method to train the systems from scratch. The review also provides insights into the databases, which are publicly available for evaluation, and it is expected to be of great help for the researchers working in the area. The limitations in the present study are also outlined with respect to non-uniform valid databases and the hazards caused due to the lack of real-time COVID-19 data, which are a high necessity for the deep learning methods. The nonavailability of gold standards for evaluation is also reported. Further, the probable solutions and outcomes were also discussed. Although the deep learning algorithms on medical images for COVID-19 can be considered an additional measure of identification, in recent times they may also provide highly efficient and faster solution to the conventional RT-PCR screening. If not then, at least with early detection with AI, they may be helpful in reducing the spread of the virus.