training the DL model for segmentation, 2428 CT images were used, out of which 2242 images were from the public database and 186 images were from KMC, Manipal. The training and test sets for classification comprised 400 and 100 CT images, respectively. The training dataset had 200 images in each normal and abnormal conditions. The test set had 100 CT images with 50 images from each category. The abnormal images had with different lesions like cysts, hepatocellular carcinoma, hemangioma.

# 3.2 Liver segmentation

Liver segmentation was done using DeepLabv3 + network. Its architecture comprises an encoder and a decoder as depicted in Figure 2. The encoder employs ResNet-50 as the backbone network and Atrous Spatial Pyramid Pooling (ASPP). ResNet-50 performs feature extraction and the ASPP block applies atrous convolutions at multiple scales to capture multiple contextual information. The decoder reconstructs the output with dimension same as the input [11]. ResNet-50 is a CNN with fifty layers (Figure 5). It skip connections to overcome the problem of vanishing gradients.

![](bbox=[0.301, 0.353, 0.715, 0.506])

Figure 2. Architecture of the DeepLabv3 + network.

![](bbox=[0.296, 0.574, 0.703, 0.773])

Figure 3. Structure of ResNet-50 network.

For training the DL model 2428 CT images and their ground truths were considered. ITK-SNAP tool [12] was used for ground truth delineation under the supervision of an expert radiologist. The model was trained with Stochastic Descent with Momentum (SGDM) optimizer for 100 epochs. The momentum chosen was 0.9 and a constant learning rate of 0.001 was considered.