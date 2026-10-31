
Google has provided different tools in the form of products and services that change the business world drastically. Google has offered many services such as Google search (fast communication, tracking, and captures the location in real-time), robotics, Google cars, artificial intelligence, smart messaging, weather information in real-time, and many more. (For some examples of Google products, see the following figure). These services and products are elements that will impact the current businesses. These elements are not only giving a new direction to modern-day innovation but also increasing the competition in the market, which will push other companies to perform better:

![](OEBPS/images/4.10.jpg)

**Figure 4.10:** Google DL and other products

## Google AutoML

`AutoML Vision` of Google is a new service that helps developers with limited machine learning expertise to build a custom image recognition model. Human-machine learning experts to perform the following tasks:
* Preprocessing and cleaning of the data.
* Selection and construction of appropriate features.
* Selection of an appropriate model family.
* Optimization of model hyperparameters.
* Post processing of machine learning models.
* Analyzing the obtained results.

The original idea of `AutoML` is to allow anybody to bring their images virtually, upload them, and then Google’s systems automatically create a custom machine learning model for them. The whole process, from importing data to tagging and training the model, is done through a drag and drop interface.

With the use of `AutoML`, the accuracy of the model increases and results in faster turn around time:
* **Increased accuracy:** Cloud `AutoML Vision` is built on image recognition approaches that include machine learning and neural architecture technologies. This means `AutoML` helps to get a more accurate model.
* **Faster turnaround time:** With Cloud `AutoML`, the developer can create a model in minutes to sense AI-enabled application, or able to build the production-ready model in very less time.
* **Easy to use:** `AutoML Vision` provides a simple graphical user interface that helps to specify data and turns that data into a high-quality model customized according to the specific needs.

## DeepLab-v3+

`DeepLab-v3+` is Google’s open-source Semantic Image Segmentation model. It is a deep learning model for semantic image segmentation to assign semantic labels (for example, cat, dog, person, and so on) to each pixel in the input image. The following figure is an illustrated view of the flow chart of `DeepLab-v3+`:

![](OEBPS/images/4.11.jpg)

**Figure 4.11:** Flow chart of `DeepLab-v3+`

`DeepLab-v3+` is implemented in `TensorFlow` and its models are built on the top of a convolutional neural network backbone architecture, which is intended for server-side deployment for the most accurate results. It is the extension of the `DeepLab-v3` model. The `DeepLab-v3` model consists of the convolution layer to extract the features by deep learning neural networks at an arbitrary resolution.

An estrous convolutional layer is a tool to control the features computed by deep learning models explicitly and to capture multi-scale information; it adjusts the filter field of view. It also generalizes the standard convolution operation.

For the development of the `DeepLab-v3+` model, a simple and active decoder module is added in the `DeepLab-v3` model. It is performed to refine the segmentation results along the object boundaries. Depth-wise separable convolution is also applied to both estrous spatial pyramid pooling and decoder modules. It helps to increase the speed and accuracy of the encoder-decoder module for semantic segmentation.

For the improvement along the object boundaries, morphological dilation is applied on a void annotation label on the validation set around the object boundaries. After that, mean IOU is computed of pixels that are associated with the dilated band of void labels. More significant improvement is observed when the narrow dilated band is used.

`DeepLab-v3+` has improved the `Xception` model. The following improvements have been made:
* The number of layers has been introduced.
* All the max-pooling layers are replaced with the depth-wise convolutions with striding.
* Extra batch normalization and `ReLU` activation function are added after each `3X3` depth wise convolution.

`DeepLab-v3+` correctly recognizes the subject in the foreground in the picture. In this way, the depth of field and the blurring effect are compatible and perfectly non-artificial. It also improves the method of tagging the pixels using semantics. It can also be used for the segmentation of real-time mobile videos.

## DeepMind

`DeepMind` builds systems that learn automatically. The models are not pre-programmed and the features are not handcrafted. The system is provided with a large number of raw datasets so that the operation can learn from the best representation. In this way, the order is able to operate across a wide range of tasks.

Reinforcement learning architecture is used to develop the systems. The agents generated interact with some environment. The agent takes the actions in the given situation and receives feedback from the environment in the form of observations and further uses those observations to update the behavior of the model.

In the medical field, `DeepMind` could help clinicians with more accurate analyses and ultimately patients can get faster treatment. The immediate potential analysis helps physicians provide better, faster, and safer care to the patient. The security of patient data is a top priority. Data of patients remain under the full control and direction of the hospital. All information is stored securely and encrypted with the highest standards.

## WaveNet

Google `DeepMind` is developing `WaveNet` — an algorithm that can transform the input text into raw audio. It can show outstanding results as compared to previous attempts.

It is one of the fully convolutional neural networks that contain various dilation factors that allow its respective corresponding field to grow exponentially with depth and cover thousands of steps.

At the time of training, input sequences are original waveforms obtained by recording human speakers. After training, the sampling of data is used to generate synthetic utterances. During the sampling process, the value is extracted from the probability distribution computed by the network. After that, the obtained value is fed back into the input and a process of new prediction is done. The following diagram illustrates the different layers:

![](OEBPS/images/4.12.jpg)

**Figure 4.12:** Represent ation of different layers

Google also made an algorithm with `DeepMind`, which is able to read the lips movement of humans.

## Tensor Processing Unit (TPU)

Google has made a specialized chip meant to accelerate machine learning applications, that is, `Tensor Processing Unit (TPU)`. It supports training machine learning algorithms along with the processing of results from existing models. Cloud `TPUs` are hardware designed to speed up and scale up Machine Learning workloads programmed with `TensorFlow`. Every chip can provide 180 teraflops of processing. Google is also able to network the chips together in sets called `TPU Pods` that allow higher computational gains.

The new chips are helpful in businesses and they’ll be able to use them through Google’s Cloud Platform. Also, the company is launching a new `TensorFlow Research Cloud` that will provide researchers with free access to that hardware.
