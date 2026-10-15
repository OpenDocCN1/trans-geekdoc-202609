# TABLE 7.2
Method, Dataset, Lesion, Model, Results, and Future Work of the Selected Studies for Detection and Segmentation of DR-Associated Retinal Lesions

| Method, Year | Dataset | Lesion Detection | Classifier | Results | Future Work |
|---|---|---|---|---|---|
| Akram et al. [10], 2012 | DRIVE, STARE, DIARETDB0, and DIARETDB1 | MA, HE, CWS, and EX | Hybrid fuzzy classifier | DRIVE: Accuracy = 96.14% for dark lesions and 96.23% for bright lesions
STARE: Accuracy = 95.98% for dark lesions and 95.71% for bright lesions
DIARETDB0: Accuracy = 91.26% for dark lesions and 93.89% for bright lesions
DIARETDB1: Accuracy = 91.60% for dark lesions and 93.10% for bright lesions | DNN-based models can be explored for improved lesion detection accuracy |
| Yu et al. [41], 2017 | e-Ophtha-EX | EX | CNN | Sensitivity = 88.85%, Specificity = 96%, Accuracy = 91.92%, F-Score = 92.61% | More benchmark datasets should be used for model validation |
| Lam et al. [42], 2018 | e-Ophtha and Kaggle | MA, HE, EX, and CWS | GoogLeNet | Five-class Accuracy = 95%
Binary Accuracy = 98% | Model can be modified to detect neovascularization |
| Chudzik et al. [43], 2018 | ROC and DIARETDB1 | MA | CNN | For ROC: FROC score = 0.355
For DIARETDB1: FROC score = 0.392 | Forward propagation step can be parallelized across multiple devices to reduce time |
|  |  |  |  |  | (Continued) |