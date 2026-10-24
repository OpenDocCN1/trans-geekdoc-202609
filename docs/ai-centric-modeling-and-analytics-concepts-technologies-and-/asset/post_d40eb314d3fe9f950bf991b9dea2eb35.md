
## 11.3 TECHNICAL APPROACH

### 11.3.1 Dataset Description

The following are the publicly available datasets considered for this work:

- **ACRIMA** (Fan et al., 2020) is a public dataset of fundus images that contains annotations of glaucoma made by two experts. The dataset contains 705 images, with 396 images labelled as glaucomatous and 309 images labelled as normal. It is crucial to remember that no additional clinical information was taken into account; the comments were made simply on the basis of how the fundus pictures appeared.
- **The Drishti-GS** (Sivaswamy et al., 2014) dataset is a publicly accessible dataset for glaucoma evaluation that contains 101 monocular fundus pictures, 70 of which are glaucoma images and 31 are normal images. It is split into two sets: testing and training. Four professional segmentations of an optic disc and cup are included in the training package.
- **The High-Resolution Fundus (HRF) Image Database** is a collection of images of the retina, or the inner lining of the eye, which are used for research and medical purposes (Li et al., 2019). The images in the database are high resolution, meaning that they have a high level of detail and clarity. The HRF Image Database is often used by researchers and medical professionals to study the structure and function of the retina and to develop and evaluate new technologies and methods for diagnosing and treating eye conditions. The HRF dataset, consisting of 45 images that were split into three groups and labelled as diabetic retinopathy, glaucomatous, and healthy, is a dataset for segmenting retinal vessels. In the present study, only glaucomatous and healthy subjects were considered (Khang et al., 2022).
- **ORIGA** is an online repository of retinal fundus photographs developed for glaucoma examinations and studies. Photographs of the retina, optic disc, and blood vessels at the back of the eye are called retinal fundus images. Glaucoma is a group of eye conditions that can damage the optic nerve and cause vision loss (Zhuo et al., 2010). The ORIGA-light dataset is anticipated to be a helpful resource for researchers looking into the underlying biological reasons for the condition, as well as academics and clinicians focusing on glaucoma diagnosis and treatment. ORIGA30 includes 168 photographs of glaucoma patients and 482 photographs of healthy people, in addition to disc and cup segments.
- **Multi Eye Disease Dataset** is a collection of eye-related medical photographs that were divided into four groups: normal, cataract, glaucoma, and retinal disease. The dataset was developed in an Indian hospital and has 500 photographs in total, with 100 images for each of the three illness groups and 300 photographs for the healthy category. Because the data have been anonymised, it is unlikely that the dataset contains any private information about the people in the photographs. The dataset appears to have been built using the data fusion procedure, and it was developed for research on selecting features based on optimization. Only healthy and glaucomatous individuals were included in this study.

### 11.3.2 EfficientNetV2 Models

Evolution of TL:

- **Early TL:** In the early days of artificial intelligence (AI) research, TL was proposed as the concept of “learning to learn,” where a system could learn from one task and transfer the acquired knowledge to improve performance on a different task. However, the field of AI was still in its infancy and the computational resources are limited, so the idea of TL remained theoretical (Rana et al., 2021).
- **Transfer learning with feedforward neural networks:** As computational resources improved and large datasets became available, researchers began to explore practical applications of TL. Early works in this area focused on transferring knowledge between different but related tasks, such as between different languages or between different image classification tasks. These TL approaches are mainly based on feedforward neural networks, which are simple and efficient architectures that are well-suited for the limited computational resources of the time.
- **Convolutional neural networks and TL:** With the introduction of CNNs, TL has received considerable attention. Convolutional neural networks can learn feature representations from images and have been used in various image-related tasks, such as object detection, semantic segmentation, and image classification (Khang et al., 2023a).
- **Transfer learning using pre-trained DNNs:** As deep learning has gained popularity, TL has also gained popularity. Deep neural networks that have already been trained on big datasets can perform better after being fine-tuned on small, task-specific datasets. This approach, known as fine-tuning, has become a popular method for TL in various applications, such as natural language processing, computer vision, and speech recognition.
- **Transfer learning with EfficientNetV2 models:** EfficientNetV2 models represent the latest evolution of TL. EfficientNetV2 is an improved version of the original EfficientNet model, which is a family of CNNs designed to be more efficient in terms of computational resources while maintaining high accuracy. EfficientNetV2 models were trained using a combination of TL and machine learning techniques. They are based on the EfficientNet architecture and are pre-trained on a large dataset, allowing them to be fine-tuned on specific tasks with smaller datasets (Khang et al., 2023b).

The evolution of TL has progressed from early theoretical proposals to the practical application of feedforward neural networks, CNNs, pre-trained DNNs, and finally to the latest EfficientNetV2 models. With each step, the models become more complex and powerful, capable of learning from larger and more diverse datasets, and can fine-tune specific tasks to achieve improved performance.

## 11.4 WHY EFFICIENTNETV2?

The architecture of EfficientNetV2 is based on the idea of scaling up CNNs in a “smart” way (Luke et al., 2023). This is achieved using a compound scaling method, which scales up the dimensions of the network in a more structured manner than simple scaling. The compound scaling method adjusts the following network dimensions:

- **Width:** The number of channels in the convolutional layers is increased.
- **Depth:** The number of layers in the network is increased.
- **Resolution:** The input image resolution is increased.

In addition to the compound scaling method, EfficientNetV2 also uses several other techniques to improve efficiency, such as lightweight convolutional layers, global depth-wise convolution, and a linear bottleneck structure.

Overall, the goal of the EfficientNetV2 architecture was to achieve the best performance with the smallest number of parameters and computational resources.

The main differences between EfficientNetV2 and the original EfficientNet architecture are as follows:

- EfficientNetV2 adjusts the model dimensions (depth, width, and resolution) in a more balanced manner using a different technique termed compound scaling.
- EfficientNetV2 introduces a new version of the Swish activation function, called memory-efficient Swish, which is more memory efficient than the original Swish activation function.
- EfficientNetV2 introduces a new version of the bottleneck building block, called the EfficientNetV2 block, which is more efficient than the original bottleneck block used in EfficientNet.

The models considered under EfficientNetV2 series are as follows.

### 11.4.1 EFFICIENTNETV2B0

EfficientNet-V2B0 is a variant of the EfficientNet-B0 architecture that is designed to be efficient and scalable. The architecture is based on MobileNetV2 architecture and is trained using a combination of manual and automated methods.

The EfficientNet-V2B0 architecture is characterized by its use of depth-wise separable convolutions and a lightweight residual block called mobile inverted residual bottleneck.

It also uses a compound scaling method that scales the dimensions of the network, along with the number of channels and the resolution of the input images. This
