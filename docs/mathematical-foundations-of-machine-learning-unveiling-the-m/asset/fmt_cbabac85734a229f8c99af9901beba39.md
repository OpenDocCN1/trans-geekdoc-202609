
# Hyperparameter of ANN

A “hyperparameter” is a parameter established before the initiation of the learning process. These values are determined through the learning process itself, such as the learning rate, batch size, and number of concealed layers. Certain hyperparameter values may be interdependent; for example, the size of specific layers might depend on the total number of layers.

The learning rate signifies the magnitude of corrective measures needed for the model to rectify errors in each observation. A higher learning rate shortens training time but sacrifices accuracy, while a lower rate extends training time for potentially higher accuracy. Optimization techniques like `Quickprop` aim to hasten error minimization, while other enhancements focus on increasing output reliability. These refinements employ an `adaptive learning rate` that adjusts to prevent oscillation and enhance convergence.

![](image-hxgv2mu8.png)

The momentum principle balances the gradient and the previous alteration, with the weight adjustment influenced by the prior alteration. A momentum value close to `0` emphasizes the gradient, while a value near `1` emphasizes the last change.

# Neural Network Training with Data Pipeline

A neural network, defined as a function learning expected output from training datasets, features a single neuron or `perceptron`. Unlike traditional programming, neural networks autonomously determine parameters (weights and biases) through learning from provided training datasets, using algorithms like `backpropagation` and `gradient descent`.

Programmers establish a data pipeline, a cyclical and iterative process where each stage utilizes data from the preceding stage. Development environments like `Python` and `R` enable efficient training and testing of models in a sandboxed environment, facilitating interactive prototype development.

The goal of constructing a machine learning pipeline includes:
Reduction of system latency.
Integration with other model components with loose coupling.
Horizontal and vertical scalability.
Message-driven communication through asynchronous, non-blocking messages.
Effective calculations for dataset management.
Resilience to system errors and recovery with minimal supervision.
Support for both batch and real-time processing of input data.

Traditional data pipelines involve overnight batch processing, but in machine learning models, batch processing doesn’t always suffice. The image below illustrates a machine learning data pipeline applied to real-time business problems, including applications in product recommendations, estimated time of arrival, new link recommendations, and search engines.

![](image-srcln3y1.jpg)

The swim lane diagram above comprises two explicitly specified components:

Online Model
In the top swim lane of the picture, the elements of the application required for operation are depicted. It shows where the model is used to make real-time decisions.

Offline Data
The bottom swim lane illustrates the learning element of the model, used to analyze historical data and generate the machine learning model using the `batch processing` method.

There are eight fundamental stages in the creation of a data pipeline, which are shown in the picture below and explained in detail here:

## Problem
In this stage, the business problem requiring resolution using a machine learning model will be identified and documented with all pertinent details.

## Data
The first stage of any machine learning workflow is to channel input data into a database server. It’s crucial to remember that the data is ingested raw and without modification to maintain an invariable record of the original dataset. Data may be supplied from various sources, acquired either through requests or transmitted from other systems.

`NoSQL document databases` are best suited to store a huge amount of defined and labeled as well as unorganized raw data, rapidly evolving as they don’t need to adhere to a predefined scheme. They even provide a `distributed, scalable, and replicated data storage`.

Data flows into the `offline` layer to the raw data storage through an `Ingestion Service`, a composite orchestration service capable of encapsulating data sourcing and persistence. A repository model internally communicates with a data service, interacting with the data storage in exchange. When saving data in the database, a unique batch ID is given to the dataset, allowing effective query, end-to-end tracking, and monitoring.

To be computationally efficient, data ingestion is distributed into two folds. The first is a specific pipeline for every dataset to process each simultaneously. The second aspect is that within each pipeline, data can be divided to make the best use of various server cores, processors, and perhaps even the entire server. Distributing data preparation across several vertical and horizontal pipelines reduces the total time required.

The `ingestion service` runs at regular intervals based on a predefined schedule (one or more times a day) or upon encountering a trigger. A subject decouples producers (data source) from processors, the data pipeline for this example. When source data is collected, the `producer system` notifies the `broker`, and the `embedded notification service` responds by inducing data ingestion. The `notification service` also informs the `broker` that processing of the original dataset was completed successfully, and the dataset is now stored in the database.

The `Online Ingestion Service` forms the entrance to the `streaming architecture` of the online layer, decoupling and managing data flow from source to processing and storage components. It offers consistent, high-performance, low-latency functionalities and serves as an enterprise-level `Data Bus`. Data is stored on long-term `Raw Data Storage`, also serving as a mediating layer to the subsequent online streaming service for further real-time processing. Techniques used may include `Apache Kafka (pub/sub messaging system)` and `Apache Flume (data collection to the long-term database)`. Various other similar techniques can be selectively applied based on the business’s technology stack.

## Data
After ingesting information, a centralized pipeline evaluates data conditions, searching for format variations, outliers, patterns, inaccurate, incomplete, or distorted information, correcting any abnormalities. The `feature engineering process` is also included in this stage. The three primary characters of a feature pipeline are `extraction, transformation, and selection`.

Since this is often the most complicated component of any machine learning project, introducing appropriate design patterns is essential. In the context of coding, it implies the use of a factory technique to produce features based on certain shared abstract function behavior and a strategy pattern for selecting the correct features at the time of execution. It’s important to consider the composition and reusability of the pipeline when structuring `feature extractors` and `transformers`.

The selection of functionalities could be attributed to the caller or automated. For instance, a `chi-square statistical test` can be applied to classify the impact of each function on the concept label, discarding low-impact features before starting to train the model. To accomplish this, some `selector APIs` can be identified. In any case, a unique ID must be allocated to each feature set to ensure consistency in model inputs and impact scoring. Overall, it’s necessary to assemble a data preparation pipeline into a set of unalterable transformations, readily combinable. Now, the importance of `testing and high code coverage` becomes a critical factor in the model’s success.

## Data
The primary goal of the machine learning model is to develop a high-accuracy model based on the quality of its forecasts and predictions for information derived from new input data, not part of the training dataset. Therefore, the available labeled dataset will be utilized as a `proxy` for future unknown input data by dividing the data into training and testing datasets. Many approaches are available to split the dataset, and some of the most widely used techniques include using either the default or customized ratio to sequentially divide the dataset into two subsets to ensure no overlap in the sequence in which the data appears from the source. For example, you could select the first 75% of data to train the model and the subsequent 25% of data to test the model’s accuracy.

![](image-xoa5q2gc.jpg)

Splitting the dataset into training and testing subsets using a default or custom ratio with a random seed. For example, you could choose a random 75% of the dataset to train the model and the remaining 25% of the random dataset to test the model.

Utilizing either of these techniques (`sequential vs. random`) and then also mixing the data within each data subset.

Employing a customized injected approach for splitting the data when extensive control over the segregation of the data is required.

Technically, the data segregation stage is not considered an independent machine learning pipeline; however, an `API` or tool has to be provided to support this stage. To return the required datasets, the next two stages (`model training` and `model assessment`) must be able to call this `API`. Concerning the organization of the code, a `strategy pattern` is required so that the `caller service` can select the appropriate algorithm during execution, and the capability to inject the percentage or random seed is required. The `API` must also be prepared to return the information with or without labels to train and test the model, respectively. A warning can be created and passed along with the dataset to secure the `caller service` from defining parameters that could trigger uneven distribution of the data.

## Model Training

The model pipelines are always `offline`, and their schedule will vary from a matter of a few hours to just one run per day, based entirely on the complexity of the application. The training can also be initiated by time and event, not just by the system schedulers. It includes many libraries of machine learning algorithms such as `linear regression, ARIMA, k-means, decision trees`, and many more, designed to make provisions for the rapid production of new model types as well as making the models interchangeable. Containment is also important for the integration of `third-Party APIs` using the `facade pattern` (at this stage, the `Python Jupyter notebook` can also be called).

You have several choices for `parallelization`:

A specialized pipeline for individual models tends to be the easiest method, which means all the models can be operated at the same time.

Another approach would be to duplicate the training dataset; i.e., the dataset can be divided, and each dataset will contain a replica of the model. This approach is favored for the models that require all fields of an instance for performing the computations, for example, `LDA`, `MF`.

Another approach can be to parallelize the entire model, meaning the model can be separated, and every partition can be responsible for the maintenance of a fraction of the variables. This approach is best suited for linear machine learning models like `Linear Regression`, `Support Vector Machine`.

Lastly, a hybrid strategy could also be utilized by leveraging a combination of one or more of the approaches mentioned above.

It is important to implement training the model while taking error tolerance into consideration. The data checkpoints and failures on training partitions must also be taken into account, for example, if every partition fails due to some transient problem like timeout, then every partition could be trained again.

## Training approaches for Neural Network

Similar to most traditional machine learning models, Neural Networks can be trained using supervised and unsupervised learning algorithms as described below:

### Supervised Training

Both inputs and outputs are supplied to the machine as part of the supervised training effort. Then the network will process the inputs and compare the outputs it generated to the expected outputs. Errors will then be propagated back through the model, resulting in the model adjusting the weights that regulate the network. This cycle is repeated time and again with the weights constantly changing. The dataset enabling the learning is called the `training set`. The same dataset is processed several times while the weights of a relationship are constantly improved through the course of training of a network.

Current business network development packages supply resources for monitoring the convergence of an artificial neural network on its capacity to forecast the correct result. These resources enable the training routine to continue for days only until the model reaches the required statistical level or precision. Some networks, however, are incapable of learning. This could be due to the lack of concrete information in the input data from which the expected output is obtained. Networks will also fail to converge if a sufficient quantity and quality of the data are not available to confer complete learning. In order to keep a portion of the dataset for testing, a sufficient volume of the dataset must be available. Most multi-node layered networks can memorize and store large volumes of data. To monitor the network to determine whether the system merely retains the training data in a manner that has no significance, supervised learning requires a set of data to be saved and used to evaluate the system once it has been trained.

To avoid insignificant memorization, the number of processing elements should be reduced. If a network cannot simply resolve the issue, the developer needs to evaluate the inputs and outputs, the number of layers and its elements, the links between these layers, the data transfer and training functionalities, and even the original input weights. These modifications that are needed to develop an effective network comprise the approach in which the `art` of neural networking plays out. Several algorithms are required to provide the iterative feedback needed for weight adjustments through the course of the training. The most popular technique used is `backward-error propagation`, more frequently referred to as `back-propagation`. To ensure that the network is not `overtrained`, supervised training must incorporate an intuitive and deliberate analysis of the model. An artificial neural network is initially configured with current statistical data trends. Subsequently, it needs to continue to learn other data aspects that could be erroneous from a general point of view. If the model is properly trained and no additional learning is required, weights may be `frozen`, if needed. In some models, this completed network is converted into hardware to increase the processing speed of the model. Certain machines do not lock in but continue learning through its use in the production environment.
