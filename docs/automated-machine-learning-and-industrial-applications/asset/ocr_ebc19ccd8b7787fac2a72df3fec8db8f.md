![](bbox=[0.12, 0.1, 0.94, 0.37])

# Figure 10.7 Schematic representation of E-Net.

have distinct shapes, and they also differ in terms of their overall health. With the goals of clear leaves, minimal watermarks, and simple labeling, 189 pictures are eliminated as leaf images in the intricate setting. The RPnv2 algorithm is trained on this dataset to find and locate leaves in an environment that is complicated. Then, XML files in PASCAL VOC format are generated, and images are promptly annotated employing LabelImg. The target detection neural network can be directly input as training data. In the final stage, a diseased leaves dataset in a controlled environment is essential for this research. The study acquires four types of images—537 images (black rot), 1,032 (bacterial plaque disease) images, 293 images (rust), and 2,852 images (healthy leaves) from the Question-and-Answer Forum of PlantVillage Agricultural. These images serve as training data for an E-ENet model, specifically the E-ENet model, which undergoes training using this diverse dataset.

# 10.5.2 The Parameter Setup

# 10.5.2.1 The Configuration of Parameters for Leaf Localization

The PlantVillage Agricultural Question-and-Answer Forum provided the dataset used in this study, which included four different image types: 537 black rot, 1,032 bacterial plaque disease, 293 rust, and 2,852 healthy leaves. To improve its performance, the E-ENet model is trained on this varied dataset that covers a range of plant conditions.