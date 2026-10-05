
# Transforming Healthcare

Radiation Therapy: Radiation therapy, primarily for treating cancer types, refers to applying energetic particles or waves to irradiate or destroy neoplastic cells. Depending on the details and the development of the stage, the therapy may be performed on the patient from the outside, or body radiation treatment may be performed. Immunotherapy: When treating cancer, the disease is attacked, and the immune system is also utilised to fight; that is what immunotherapy is in a nutshell. Chemotherapies that were originally thought to be very difficult to treat have recently showed tremendous improvement with the use of tools such as antibodies that are monoclonal, CAR-T cell therapy, and inhibitors of checkpoint.

Gene Therapy and Personalized Medicine: Fundamental advancements in knowledge of genomics and cell biology bring us to the era of personalised medicine in which treatment is based on the genetic characteristics of the individual patient. Gene therapy is the treatment of disease by curing or altering the disease-causing genes, which may result in the eradication of diseases such as cystic fibrosis or some types of cancer, which have been deemed impossible to cure in the past.

## 3.3 MACHINE LEARNING AND DEEP LEARNING

### 3.3.1 Machine learning

ML represents a machine's ability to improve on a specific task without programming, it as flies under the broader concept termed AI. The essence of this has been to construct systems that can accomplish various tasks, such as understanding data, categorising it, and acting upon it, with little or no assistance from a human being. Supervised learning is trained on labelled data with a known input–output relation. The intention is to find a function that outputs for the new inputs that have never been seen. Linear regression, support vector machines, and decision trees are some examples.

The regression technique is usually used to determine the continuous result based on various independent features provided. For instance, a house price would be estimated in a linear regression example, several independent variables like number of bedrooms, location, etc. Examples include polynomial regression, a more complex regression, and ridge regression. Support Vector Machines (SVM) are another learning method used in different fields of study for classification and regression problems. By locating the feature field hyperplane that precisely divides the categories. In this case, the hyperplane separates different classes and makes a maximum margin for them. Regarding regression, SVM is concerned with allowing as many instances as possible within a certain margin.

## Applications of AI & ML in diagnostics and disease treatment

Decision tree models are the graph-like representations of decisions made and the possible outcomes of such decisions. They sequentially divide the more extensive data into smaller ones about the different feature values to decide the tree's nodes. The objective is to build a model to predict the target variable based on rules created from the observed data. It is important to note that in terms of outcome, decision trees have applications in both classification and regression. unsupervised learning has no inputs or outputs, as all features are embedded in the data. There is no supervision, and the goal is to learn the inherent structures of the data. Some well-known applications of unsupervised training involve techniques for reducing dimensionality like PCA and clustering methods like k-means and pyramidal clustering.

K-Means Clustering divides the sample of data into k clusters, or a predetermined clusters where each data sample is allocated to the closest center. The centroids of the clusters are recalculated the average of points belonging to that cluster, and is repeated until a stable result is achieved. It is ideal in situations with a lot of data, but it has the problem that number of clusters has to be predetermined. The results are commonly summarised in a dendrogram, which allows total control over determining the number of clusters at every sublevel of the hierarchy. Reinforcement Learning is based on the principles of behaviourism and utilises exploratory trial-and-error practice. The agents launch into an environment to maximise their rewards through actions. Such applications have been made famous by game playing and control of robots.

### 3.3.2 Deep learning

Deep learning is a subfield of ML that specifically exploits the engineering of artificial neural networks (ANNs), a prairie of deeply layered ANNs. This architecture features nodes connecting with each other on multiple layers, which are referred to as neurons in simple terms. The architecture in question affords affords model to pick up compound patterns and interrelationships among complex data. Neural networks have existed since the 1940s, yet this term became popular only in the 2000s. There are several reasons for this evolution of DL. The advent of powerful GPUs made possible to train deep networks within a reasonable time. The big data boom created sufficient data to train DL models that require a lot of data to work efficiently. We introduced backpropagation, dropout algorithms for regularisation, and various activation functions, such as ReLu rectified linear unit, which made deep learning eatable from the head market.

What is most important about deep learning networks is such that networks are constructed with many hidden layers between the input and output nodes. This depth enables deep learning models to: One significant difference distinguishing deep learning models from classical ML is the feature extraction process. Traditional ML models require hand-crafted features, while deep learning one builds the features from data. including real-life images, audio, and text. Some of the noticeable architecture present in deep learning are: CNNs, which are mainly used in image processing, and Computer vision, which are generalised by convolutional layers that reuse the parameters in each Conv layer to perform feature mappings on the given images. Recurrent neural networks are artificial neural networks that introduce recurrent connections into the data. This type of architecture is used on sequential objects like time series and language data since there is past information in the previous steps. Generative models are a field where deep learning has also been applied, with the development of GANs (Generative Adversarial Networks) and VAEs (Variational Autoencoders) capable of generating new data points that resemble the input data.

## 3.4 MACHINE LEARNING AND DEEP LEARNING IN DISEASE DIAGNOSIS AND TREATMENT

### 3.4.1 Autoencoder

An autoencoder is a neural network used for unsupervised learning. In the context of skin detection, the encoder maps the input to a latent space $Z \in R^m$, where $m$ is the dimensionality of the input. The decoder then maps $Z$ back to the input $\hat{X}$. The goal of training the autoencoder is to minimize the reconstruction error, typically using Mean Squared Error (MSE) between $X$ and $\hat{X}$:

$$L(X, \hat{X}) = \frac{1}{n} \sum_{i=1}^{n} (X_i - \hat{X}_i)^2$$

### 3.4.2 Autism prediction using a convolutional network

Autism prediction with a convolutional network (CNN) in deep learning can be represented through several key steps, including convolution operations, activation functions, and loss calculations. The input is a 2D image or signal, which we can represent as a matrix $X \in R^{m \times n}$. Each filter $F_k \in R^{f \times f}$ (where $f$ is the filter size) slides over the input with a stride of $s$, and the convolution is given by:

$$Y_k^{(l)}(i, j) = \sum_{p=1}^{f} \sum_{q=1}^{f} X^{(l)}(i+ps, j+qs, r) F_k^{(l)}(p, q, r)$$

where $Y_k^{(l)}$ is the output of the $k$-th filter applied to the location $(i, j)$. After the convolution, ReLU is applied:

$$A_k^{(l)}((i, j) = ReLU(Y_k^{(l)}(i, j)) = max(0, Y_k^{(l)}(i, j))$$

Pooling layers reduce the spatial dimensions (downsampling). Max pooling is commonly used, and it can be represented as:

$$P^{(l)}(i, j) = max_{p,q} (A^{(l)}(i+p, j+q))$$

where $i, j$ represents the location in the pooled matrix, and the max operation taken over a pooling window of size (e.g., $2 \times 2$). The next feature maps undergoes a series of pooling and convolutional layers before being transformed into a 1D vector and sent through a series of fully connected layers. Let $Z^{(l)} \in R^n$ be the input vector to the fully connected layer, and then the output is:
