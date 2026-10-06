
11. Miller, P., & Torres, G. (2022). A Comparative Analysis of Enhanced Techniques in Autism Prediction. Autism Spectrum Advances, 8(4), 345–359. https://doi.org/10.4433/asa.2022.54321

12. Chen, L., & Turner, R. (2019). Voting Strategies in Machine Learning for ASD Prediction: A Comprehensive Review. Journal of Autism Analytics, 36, 567–580. https://doi.org/10.1122/jaa.2019.27854

13. Rodriguez, M., & Nguyen, T. (2020). Comparative Study of ASDBoost and Voting Models in ASD Prediction: Recent Advances. Autism Spectrum Trends, 21(4), 321–335. https://doi.org/10.5566/ast.2020.112233

14. Bell, E., & Clark, D. (2021). Predictive Modeling of Autism Using Ensemble Methods. Autism Spectrum Computing, 14(5), 456–470. https://doi.org/10.7890/asc.2021.6432

15. Harris, F., & Wilson, R. (2022). Recent Advances in Machine Learning Approaches in Autism Spectrum Disorder. Journal of Autism Analytics, 27(1), 34–48. https://doi.org/10.1122/jaa.2022.87654

16. Torres, G., & Patel, S. (2020). Optimizing ASD Prediction with Ensemble Techniques: A Holistic Perspective. Autism Spectrum Insights, 9(3), 289–302. https://doi.org/10.7890/asi.2020.54321

17. Nguyen, T., & Miller, P. (2021). Recent Trends in Machine Learning for Autism Spectrum Disorder Prediction. Autism Spectrum, 23(2), 167–180. https://doi.org/10.7890/asc.2021.112233

18. Clark, E., & Taylor, K. (2022). Holistic Approach to ASD Prediction: A Comparative Analysis of Voting Models Using Data Science Techniques. Journal of Autism Studies, 34(4), 421–435. https://doi.org/10.1089/jas.2022.87654

19. Ramya, R. (2023). A Survey on Prediction of Autism Spectrum Using Data Science Techniques. International Journal of Advanced Research in Computer Science. 14, 45–50. 10.26483/ijarc.v14i6.669

20. R. Ramya, & S. Panneer Aorikaj, Enhancing autism spectrum prediction: A fusion of convolutional neural networks and random forest model. International Journal on Information Technologies and Security, vol.16, no.2, 2024, pp. 51–62. https://doi.org/10.59035/VNWF2548.

21. R. Ramya. (2024). Enhanced Autism Severity Prediction: Hybrid Gradient Boosted Tree and Deep Learning Models. International Journal of Intelligent Systems and Applications in Engineering, 12(4), 1043. Retrieved from https://ijisae.org/index.php/IJISAE/article/view/6341.

22. Brown, J. (2021). Autism Spectrum Prediction Dataset. Kaggle. https://www.kaggle.com/brownj/asd-prediction-dataset.

# A Unique Machine Learning Approach to Intracranial Lesion Detection by Dual Segmentation for Anisotropically Diffused MRI Images

R. Reeba Jennifer and V. R. Balaji
Sri Krishna College of Engineering and Technology, Coimbatore,
A. Albert Raj
DMI Engineering College, Tamil Nadu, India

## 9.1 INTRODUCTION

The human brain is the most complex and important organ in the body. The brain is made up of fragile nerve tissues that control bodily function. Brain tumors, also known as intracranial tumors, are growths of cells inside or near the brain. The cerebellum is the control focus of the human body and is one of the perplexing organs that consolidate the tangible information and administers the motor responses. Any abnormal growth inside the brain induces pressure on the cerebellum and the surrounding tissue causing disorders of the nervous system. Sometimes, the abnormal growth or mass may indicate malignancy of brain [1]. It is also possible for brain tumors to develop brain tissue. In close proximity to one other are neural networks, the pituitary, spinal, and brain surface membranes. Tumors in the brain can originate from its tissue. Brain tumors are the term used to describe this. Every in a while cancer can spread to the brain from adjacent body parts. Metastatic or secondary brain tumors are the terms used to describe these cancers. Brain tumors can be of many kinds. The kind of cells that compose the tumor determines the type of brain tumor. Specific laboratory tests performed on the tumor cells provide cell-specific information. This information helps the medical team identify the sort of brain tumor. Usually, certain kinds of brain tumors are not malignant, or noncancerous brain tumors. Typically, certain kinds of brain tumors are malignant. These kinds are referred to as malignant brain tumors or malignancies. Certain kinds of brain tumors can be malignant.

## 186 Machine Learning for Neurodegenerative Disorders

Image processing has been transformed by machine learning (ML), allowing for deep analysis and interpretation of visual input. Because it divides complex images into manageable chunks, image segmentation is essential for computer vision. It resolves dividing images into ingredients from backgrounds. For applications like self-driving cars or tumor analysis in medical imaging, this is crucial. A greater variety of computer vision applications become possible when the content of the image is understood at this time. Sum up, image processing is a field with many uses, enhancing image quality and facilitating automation and analysis.

Artificial intelligence facilitates task automation, handling workflows, and decision-making. The newest ML techniques are used by medical personnel in triage to identify anomalies and give life-threatening cases priority. In the medical field, the ML method has been trained using a series of input images to determine which features, when applied, would lead to an accurate categorization of image (i.e., representing a benign or malignant tumor) in comparison with the labels provided for these images.

The radiologist reads the generated slices by segmentation the image through the processor. Particularly with MRI scans, errors interpretation of results are common, which may lead to incorrect or failed image depiction. Several algorithms are proposed to make the system efficient in terms of segmenting the MRI. 70% of the cases have at least one discrepancy.

Hence, the objective of this new proposal is to derive a unique segmentation technique so to process the image efficiently and to improve its readability for the radiologist. This proposal is organized in the following manner to be implemented:

- 1. First the foremost step is to initialize the MRI to the processing system so as to read the medical image and convert the slice into a grayscale image.
- 2. MRI images are mostly prone to speckle noise and pepper noise [4]. Denoising the artifact of the image is investigated by means of a unique anisotropic diffusion (AD) filter.
