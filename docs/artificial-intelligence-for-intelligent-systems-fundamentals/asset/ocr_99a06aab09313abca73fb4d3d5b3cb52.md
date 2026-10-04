# A step toward the detection of alzheimer's disease 263

# 13.3 METHODOLOGY

We integrated the probability forecast or numerical prediction of four machine learning models, combining them or utilizing the most common observation between models to arrive at a final prediction. A model ensemble is created by fitting four models, making predictions using each of them, and merging the results. It uses the test data performance to produce an ideal weighted average of the models, which is referred to as an ensemble. We fit an ensemble model by simply adding algorithms to the existing models.

# 13.3.1 Dataset

The dataset is separated into two files: training and testing, each of which contains approximately 5,000 photos, each of which is classified according to the severity of Alzheimer's illness. The training and testing dataset consists of four classes that indicate four stages of AD, as depicted in Table 13.1.

# 13.3.2 Ensemble method

Assembling is a term that is frequently seen in machine learning. This method serves as the foundation for a variety of algorithms. To name a few of the most well-known, random forests utilize a technique where a variable number of decision trees are integrated into one operation. An ensemble can be thought of as a learning strategy in which numerous models are combined in instruction to solve a problem of interest. Because an ensemble tends to perform better than a single individual, this is complete to recover simplification ability. The variety of ways in which an ensemble can be performed knows no bounds. The same can be said for the number of models evaluated as well the sorts of models analyzed. Keep in mind that choosing components with low bias and high variance is a good habit to develop. This is achieved by simply selecting models with a diverse structure and format. We demonstrate how the ensemble process is used in the neural network area. For greater clarity, we demonstrate alternative approaches to efficiently combining DL architectures. A good example is the image classification domain, where it is typical to encounter models with extremely deep learning capabilities. The same thinking and approach can be pragmatic to a variety of other applications with relative ease. Figure 13.1 highlights the complete overview of the ensemble method used for this.

Table 13.1 Dataset description

| AD Stages | Training | Testing |
|---|---||}{
| Mild Dement | 717 | 179 |
| Moderate Dement | 52 | 12 |
| Non-dement | 2,560 | 640 |
| Very Mild Dement | 1,792 | 448 |