+   • **Defect Classification:** Images of defects are sorted by type, size, shape, and how bad they are. This helps makers focus on the most important ways to fix defects and make their processes better to stop similar defects from happening again.

# 4. Metadata Annotation

+   • **Semantic Annotation:** Along with marking defects on images, extra info like the type of defect, its size, where it is, and how bad it is gets added to the image data. This provides more background information when looking at the defects.

+   • **Database Integration:** Annotated defect images and related info go into central databases or data management systems. This helps people find, analyse, and make decisions about data during chipmaking.

# 5.8 DATA PREPROCESSING

Getting semiconductor pictures ready for machine learning analysis is key. People often use these methods to make image data more accurate and useful:

+   1. **Normalization:** Normalization converts the value of each pixel of images to a common scale, usually [0, 1] or [-1, 1]. It keeps all pixel intensities the same across images, so the machine learning model can spot more patterns and features in the data.

+   2. **Augmentation:** Image augmentation techniques create more training examples from source images by making changes like rotating, flipping, scaling, or cropping. This process has an impact on the range and strength of training data, reducing the risk of overfitting, and improving the model's ability to generalize.

+   3. **Noise Reduction:** Noise reduction methods clean up or lessen unwanted elements and distortions in images, which can happen because of things like sensor noise, dust, or image compression. Common approaches include smoothing filters such as Gaussian blur or median filtering, which help keep important image features while cutting down on noise.

Using these preprocessing methods has an impact on how well semiconductor images are prepared to analyse with machine learning models. This ensures that the models can learn and pick out meaningful patterns and features from the data accurately, which leads to more reliable and efficient systems for inspecting semiconductors.

# 5.9 MODEL ARCHITECTURE

+   1. **LeNet:** Yann LeCun and his team came up with the LeNet in the 1990s. It's one of the first CNN designs. LeNet has different layers, like convolutional layers, max-pooling layers, and fully connected layers. It's not as complex as newer designs, but LeNet still does a great job with basic picture sorting tasks, like those in semiconductor checks. Its straightforward layout opened doors for more advanced CNNs. This showed how powerful deep learning can be for working with images.