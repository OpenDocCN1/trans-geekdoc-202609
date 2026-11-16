
![](img/617e854c2620a5a4bed0116cef33155a_196_0.png)

Figure 7.2 Various key components of a typical smart city

Big data and cloud computing technology involved in the smart city so that the sensor devices embedded in various smart applications. Besides this, other devices are connected to the cloud computing infrastructure that exchanges information to create large numbers of structured data. This large amount of unsolicited data is collected and stored in the cloud. Therefore, the programming model to process large data sets with parallel algorithms can be used for data analysis to obtain values from the stored data.

In order to handle these enormous amounts of data, the ML approach can be a good choice because ML can work with high-volume data reliably and without exhaustion [1, 19]. The major challenges associated with these tasks need efficient and relevant feature extraction from the data. The surge of data and its type and quantity for all the tasks are not the same and therefore the implementation of ML requires specialized algorithms for deploying in different types of data.

The big data can contain labeled data, unlabeled data, or a mixture of both. Based on the type and availability of data, network researchers have to train an algorithm with a specific learning model [2]. In the supervised way of learning, the algorithm learns with labeled data [4, 27]. More specifically, in the supervised learning model, both the input and the output are provided. Based on the labeled data, the algorithm predicts future data. In contrast, the unsupervised model [15] is when an algorithm is provided only the input data, without corresponding output data, as a training dataset. The unsupervised algorithms would be able to function freely to learn more from the data and explore the findings as there present no output values or the teachers. On the other hand, the semi-supervised model learns with the combination of both labeled and unlabeled data. Typically, this combination contains a small amount of labeled data and a large amount of unlabeled data.

The rest of the chapter is organized as follows. Machine learning frameworks are described in Section 2. Section 3 discusses ML approaches to solve problems. Section 4 presents the smart city infrastructure. The key challenges of designing a smart city are highlighted in Section 5. The implications of machine learning models in the design of smart cities are illustrated in Section 6 and a brief conclusion in Section 7 ends the chapter.

## 7.2 MACHINE LEARNING FRAMEWORKS

The question may arise about the principle of operation of machine learning (ML) approaches for SC management [6]. A good understanding of the ML technique is required for the efficient design and implementation of SC. This section describes the general ML approaches and different ML algorithms with their applications to design a smart city.

### 7.2.1 MACHINE LEARNING APPROACHES

One of the simple approaches in ML algorithm is to train it from the labeled or unlabeled data set to produce a model. New input data is introduced to a ML algorithm and it makes a prediction based on the model. These approaches are evaluated for accuracy and when the system reaches an acceptable level of accuracy, it is treated as a successful model [29]. On the other hand, if the desired response is not obtained from the system, then it is trained again and again by feeding more input data until the response of the system reaches a satisfactory level. Figure 7.3 shows a simple process of ML techniques. However, there are various factors and steps involved in producing a successful model.

### 7.2.2 MACHINE LEARNING MODELS

To work independently with the big sensor data, machines need to be learned from the various labeled or unlabeled and different structures of data by engaging mathematical and statistical approaches. These ML models are consisting of four separate families of techniques that are briefly discussed next.

- Supervised Learning
- Unsupervised Learning
- Semi-supervised Learning
- Reinforcement Learning

![](img/617e854c2620a5a4bed0116cef33155a_198_0.png)

Figure 7.3 A pictorial representation of machine learning process

In this section, machine learning purposes are being explored and when and where the specific techniques are adopted are also discussed with proper examples. Some of the specific algorithms are also considered in the discussion.

### 7.2.2.1 Supervised Learning Models

The key idea of a supervised model is that a supervisor is engaged to train a machine like a caregiver/teacher to teach a child to recognize colors, fruits, and numbers. In this method, the teacher checks every step of the child and the child has to learn from the results he/she produces [14].

In supervised ML models, there are two variables, namely x and y. Let us suppose, x be the input and y is the output; we can write a function like y = f(x). The goal is to do a mapping so well that whenever it has a new input data x it could predict the output of y.

In other words, supervised ML methods, where each instance of a training data set is composed of different input attributes and an extracted output. The input attributes of the training data set can be any kind of data set. For example, it can be a pixel of an image, value of a database, or even be a frequency histogram. For each input instant, an extracted output level is associated. The value can be discrete (presenting a category) or can be a real continuous value. In either case, the algorithm learns the input patterns that generate the extracted output. Now, once the algorithm is trained, it can be used to predict the correct output of a never seen input.

To clarify the above statement, let us consider an example. Figure 7.4 shows a model training for a supervised learning system. One can observe how a model can be developed from the raw input (feeding) to algorithm (apply). For example, a supervisor keeps on correcting the machine or keeps on telling the machine that this is an apple. Hence, this process keeps repeating until we get a final train model. Once the model is ready, it can easily predict the correct output. For instance, after giving

![](img/617e854c2620a5a4bed0116cef33155a_199_0.png)

Figure 7.4 Model training for supervised learning

a green apple as an input to the machine, and the machine can easily identify it and gives the correct output/result (Figure 7.4).

Some applications of supervised learning applications are given below:

- **Speech Automation**: Speech automation software like “Cortana” trains using a voice. Once trained, it starts working based on training. This is one application of supervised learning. If someone says “Hey Google, Call Rocky” it automatically calls Rocky from phones detecting the voice note.
- **Weather Forecast**: Considering some prior knowledge like when it is sunny, the temperature is higher and when it is cloudy, the humidity is higher. It can predict the parameters in a given time.
- **Biometric Attendance**: After training the machine with a couple of inputs of biometric identity, once trained, the machine can identify the future input of any specific person.
- **Bank Sectors**: In the banking sector, supervised learning is used to predict the creditworthiness of a credit card holder by building a machine learning model to look for a faulty attribute like providing data on delinquent and non-delinquent customers.
- **Healthcare Sector**: In the healthcare center it is used to predict the patient readmission rate by building a regression model by providing data on the patient treatment administration and readmission to show variables that best correlate with the admission.
- **Retail Shops**: In the retail sector, it is used to analyze the products that customers buy together. It does this by building a supervised model to identify frequent item sets and association rules from transactional data.

Some of the main supervised learning algorithms are discussed next.
