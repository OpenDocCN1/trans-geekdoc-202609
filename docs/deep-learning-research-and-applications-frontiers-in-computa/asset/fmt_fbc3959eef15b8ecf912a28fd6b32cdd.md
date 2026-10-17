
Figure 1.13: Rectified linear unit activation function.

#### 1.4.2.4 Softmax activation function

Softmax function is a type of sigmoid function, which can handle multiple classes in the classification problem. The output of the softmax function is equivalent to a probability distribution. It can be defined as

(1.5)$f(x)|_{j = 1}^{k} = \frac{e^{x_{j}}}{\sum_{k = 1}^{k}e^{x_{k}}}$

### 1.4.3 Popular DL architectures

There are many DL architectures available in the literature. Few of them become very popular and offer high accuracy with better performance [[12](#bodymatter-001.xhtml#b_9783110670905-001_ref_012)].

#### 1.4.3.1 Restricted Boltzmann machine

RBMs are extensively used in DL networks because of their historical importance and comparative straightforwardness. It was invented by Geoff Hinton and is used for dimensionality reduction, classification, regression, collaborative filtering, feature learning, and topic modeling. Boltzmann machines (BMs) are the primary building blocks of RBMs. BMs can be designed as NNs with bidirectionally associated stochastic processing components. RBMs are shallow, two-layer NNs that establish the DBN. As shown in [Figure 1.14](#bodymatter-001.xhtml#b_9783110670905-001_fig_014), It has just two layers – visible layer (or input layer) and hidden layer. Each node of visible layer is connected to each of the hidden layer, but there is no connection between any node of any particular layer. This is the restriction in RBM network.

![Figure 1.14: Structure of RBM.](graphic/converted/b_9783110670905-001_fig_014.png)

Figure 1.14: Structure of RBM.

In recent years, few modified RBMs introduced by different researchers are discriminative RBM, conditional RBM, and temperature-based RBM.

#### 1.4.3.2 Deep belief network

DBN also falls under the same stack of RBM, because here also the nodes of any single layer do not interconnect. DBNs, constructed by Hinton in 2006, are used to recognize, cluster, and generate images, video sequences, and motion-capture data.

To maximize the flexibility of DBNs, a novel prototype of convolutional DBN was presented by Arel in 2010. It can extract the features of high-dimensional images. The structure of DBN has been demonstrated in [Figure 1.15](#bodymatter-001.xhtml#b_9783110670905-001_fig_015).

![Figure 1.15: Structure of deep belief network.](graphic/converted/b_9783110670905-001_fig_015.png)

Figure 1.15: Structure of deep belief network.

#### 1.4.3.3 Autoencoder

An AE is comprised of two symmetrical DBNs, as illustrated in [Figure 1.16](#bodymatter-001.xhtml#b_9783110670905-001_fig_016). The first DBN does the encoding operation and the second one does the decoding. It has been successfully used in image search, data compression, information retrieval, and so on.

![Figure 1.16: Structure of autoencoder.](graphic/converted/b_9783110670905-001_fig_016.png)

Figure 1.16: Structure of autoencoder.

As a practical example, 28 × 28 pixel (i.e., 784 pixels) image dataset can be taken as input to an AE. The first layer of the encoding-half is generally kept a slightly larger set of parameters. In essence, the encoder will contain the below set of parameters:

784 (input) ----> 1000 ----> 500 ----> 250 ----> 100 ----> 30 (compressed vector)

Similarly, the decoder will contain the below set of parameters:

30 (compressed vector) ----> 100 ----> 250 ----> 500 ----> 1000 ----> 784 (output)

To improve the ability of AE, there exist various types of AE, such as denoising autoencoder, sparse autoencoder, variational autoencoder, and contractive autoencoder.

#### 1.4.3.4 Convolutional neural network

The convolution operator of two functions `f(t)` and `g(t)` can be defined as follows:

(1.6)$f(t) \ast g(t)\overset{\Delta}{=}\int_{-\infty}^{\infty}{f(\tau)g(t - \tau)d\tau =}\int_{-\infty}^{\infty}{f(t - \tau)g(\tau)d\tau}$

where `τ` is a dummy variable representing time.

This mathematical operation has been used in CNNs and has suitable performance in processing 2D data with grid-like topology. The primary use of CNN is in the areas of image classification, clustering, object recognition, behavior recognition, sound representation over spectrogram, and natural language processing on hand-written documents. Image recognition functionality of CNN is majorly being applied in self-driving cars, robotics, drones, security, medical diagnoses, and treatments for the visually impaired.

Convolutional nets analyze images in a different way than RBMs. While RBMs acquire to recreate and recognize the features of each image entirely, convolutional nets analyze images in pieces. A convolutional network receives a normal color image as a rectangular box whose width and height are measured by the number of pixels and whose depth is three layers deep, one for each letter in red–green–blue. In other words, a convolutional net treats an image as a 3D object.

There are few modified versions of CNN available in the literature, which was shown to have better performance while comparing with conventional CNN. Combination of RBM and CNN, termed as convolutional RBMs, provides an advanced convergence rate with a reduced value of the negative likelihood function.

## 1.5 ML platforms of multiple organizations

| Company | ML platform | URL |
| --- | --- | --- |
| IBM | IBM Watson Studio (formerly, Data Science Experience) | [https://www.ibm.com/cloud/watson-studio](https://www.ibm.com/cloud/watson-studio) |
| Amazon | SageMaker | [https://aws.amazon.com/sagemaker/](https://aws.amazon.com/sagemaker/) |
| Microsoft | Azure Machine Learning Studio | [https://studio.azureml.net/](https://studio.azureml.net/) |
| SKIL | Skymind Intelligence Layer | [https://docs.skymind.ai/docs](https://docs.skymind.ai/docs) |
| Google | Cloud AI | [https://cloud.google.com/products/machine-learning/](https://cloud.google.com/products/machine-learning/) |
| Cloudera | Data Science Workbench | [https://www.cloudera.com/products/data-science-and-engineering/data-science-workbench.html](https://www.cloudera.com/products/data-science-and-engineering/data-science-workbench.html) |
| Databricks | MLlib | [https://docs.databricks.com/spark/latest/mllib/index.html](https://docs.databricks.com/spark/latest/mllib/index.html) |
| Dataiku | Collaborative Data Science Platform | [https://www.dataiku.com/](https://www.dataiku.com/) |

## 1.6 IBM Watson Studio (formerly, Data Science Experience)

In 2016, IBM launched DSX [[13](#bodymatter-001.xhtml#b_9783110670905-001_ref_013)], which is modified as Watson Studio, to address each stage of the data science lifecycle, offering notebooks, collaboration spaces, tutorials, and ML models by provisioning Spark, R, Python, Scala, and other ML languages. DSX also helps data scientists by providing support to their familiar tools such as Jupyter, RStudio, Notebooks, and Apache Spark to create complex ML models and deploy these models to production. [Figure 1.17](#bodymatter-001.xhtml#b_9783110670905-001_fig_017) shows few snapshots from IBM Watson Studio on projects and services subsections. A project is used to organize resources to achieve a precise goal. It can include data, collaborators, and analytical assets like notebooks and models. An admin can associate any number of services with the project. The types of services that can be associated are

* IBM Apache Spark compute service
* Amazon Elastic MapReduce compute service
* IBM Analytics Engine compute service
* Cognos Dashboard Embedded
* IBM Watson Machine Learning
* IBM Streaming Analytics
* Watson Natural Language Classifier
* Visual Recognition
* Watson Assistant
* Watson Discovery
* Watson Knowledge Studio
* Watson Language Translator
* Natural Language Understanding
* Watson Personality Insights
* Watson Speech to Text
* Watson Text to Speech
* Watson Tone Analyzer
