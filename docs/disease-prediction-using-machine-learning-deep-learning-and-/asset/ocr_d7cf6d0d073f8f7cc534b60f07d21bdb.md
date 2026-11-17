practiced, we are more likely to find scenarios of such distribution of classes. For testing the model accuracies, a dataset consisting of 300 total images was used which included 66 COVID, 126 Pneumonia, and 108 Normal CXR images.

# EXPERIMENTS

In this section, let us understand the approach undertaken by the researchers. This research presents a pragmatic and comprehensive comparative study. Here, the deep learning models used to detect the abnormalities of the lungs are: VGG-16, AlexNet, ResNet101, and DenseNet121. In the first step of the process, all the models are foremost run individually on each of the silos, i.e, the individual clients. In this study, the researchers have assumed 3 clients each with the data distribution as shown in Tables 1, 2, 3 and 4. The images used as input for the experiments are all scaled to the size of 255x255. When the individual client completes training of their dataset on the selected model, the parameters of the saved model are saved. These parameters obtained from respective local centers are then transmitted to the central server model for aggregation. And hence in lieu of sharing raw data for further training, only the parameters obtained from the respective clients are forwarded. The individual clients can revise the parameters time and again as and when the data might keep getting updated. The overview of the approach is demonstrated in Fig. (1).

Table 1. Distribution of training dataset.

| Dataset Distribution | Client 1 | Client 2 | Client 3 |
|---|---|---|---|
| Normal | 1400 | 1350 | 1250 |
| COVID-19 | 500 | 700 | 798 |
| Pneumonia | 1100 | 900 | 1000 |

Table 2. Client-wise distribution of dataset.

| Client-wise Distribution | Client 1 | Client 2 | Client 3 |
|---|---|---|---|
| Total CXR images | 3000 | 2950 | 3048 |

Table 3. Class-wise Distribution of Dataset.

| Class-wise distribution | Normal | COVID-19 | Pneumonia |
|---|---|---|---|
| Total CXR images | 4000 | 1998 | 3000 |