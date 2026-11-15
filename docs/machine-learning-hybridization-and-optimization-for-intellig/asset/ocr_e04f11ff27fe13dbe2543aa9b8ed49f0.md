processes, will lead to an increase in the detection of pneumonia cases, which can then be treated early, thereby preventing any permanent damage to the individual and loss of life.

Our findings were that for the task of classification of images into normal or pneumonia, a CNN-based deep learning model is ideal. This concept can be extended to other use cases in the healthcare industry such as for cataract detection in eye disorders. We found out that applying the following preprocessing techniques yielded good results: rescaling, width shift, height shift, shearing, zooming, horizontal flipping, and rotation.

Future work includes experimenting with other deep learning models such as VGG19, ResNet50, and InceptionV3 and checking if they provide better performance for the task at hand. A continuous learning approach can be applied to constantly improve the model with every input. This will help increase the accuracy of the model over time and help correct wrongly learned features using reinforcement learning. An approach of ensemble learning can also be applied where multiple models are applied to the image, and the results are combined using an aggregation method, such as majority voting, to finally classify the image. This can help counter overfitting and missing corner cases but is a computationally expensive approach.

# 13.9 DISCLAIMER

The work done as part of the chapter is for research purposes and has not been used in practice in the medical field. While the results obtained are feasible, care shall be taken and results shall be verified with medical professionals before putting the proposed solution into practice.

# REFERENCES

+   1. Rajpurkar, Pranav, et al. “Chexnet: Radiologist-level pneumonia detection on chest X-rays with deep learning,” arXiv preprint arXiv:1711.05225 (2017).
+   2. Ge, Yanqiu, et al. “Predicting post-stroke pneumonia using deep neural network approaches,” International Journal of Medical Informatics 132 (2019): 103986.
+   3. Sirazitdinov, Ilyas, et al. “Deep neural network ensemble for pneumonia localization from a large-scale chest x-ray database,” Computers & Electrical Engineering 78 (2019): 388–399.