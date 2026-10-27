
understands. It goes beyond NLP by its ability to understand incomplete sentences, rhetorical question-answer system, etc.

**Keyword Extraction:** Keywords are the shortest units of content that can be used to summarize the document. Keyword extraction technique is used to extract important information from text. Keyword represents concise information about the data. Basic idea of keyword extraction system is to extract the handful of keywords from continuous bag of words, thus representing small word set from full list of words.

**Recurrent Neural Network:** RNNs are a variant of neural networks that take input from previous outputs. Traditional neural networks don’t have connection between the inputs. However, sometimes there is connection between the inputs. RNNs contain a hidden layer which stores the information about the previous sequence in order to predict the output of the current input. RNNs transform independent activations to dependent activations and thus give same weights and biases input to all the layers. Thus, current output depends upon the previous computations. It contains “memory” to capture information captured so far, i.e. capture slots filled so far. RNNs remember each and every information at every timestamp.

**Gated Recurrent Unit:** RNNs suffer from vanishing gradient problem. Gated Recurrent Units aims to help vanishing gradient problem. GRUs decide what information to be passed ahead instead of passing all the information. Thus, they are trained to keep information from long time with washing away important irrelevant information from past.

**Slot Filling Technique:** A major task in NLP is to define semantic concepts by filling in slots or set of arguments in order to achieve its goal. Thus, it is sequence classification problem in which each word is tagged with a slot or label. Thus, the input is collection of word in the form of sentence and generates output as sequence of labels for those words.

**Content-Based Recommender System:** This system is used to predict user’s performance rating for a particular item [5]. Content-based recommender system predicts an item based on previous similar item. Thus, basic idea is if a person likes a particular item, person will also like similar item. Thus, it makes predictions based on past user predictions. Content-based recommender system relies on similarity of the items.

## 15.4 OBJECTIVES

### 15.4.1 To Develop a Video-Calling Web Application

Friendly interface is required to understand the need of users and interpret their perspectives and build an environment where they can easily make use of the available features. The novice need not learn any tool or technique to use the application of this interface in their daily life routine. The attributes to be used would be very common and friendly enough for anyone to handle.

### 15.4.2 To Develop a Video-Calling Web Application

This module aims to convert the information collected from the video call into a required format so that the information can be further processed and made understandable by the machine. It should be able to extract the audio from the video call conversation and then convert that audio into simple text in real time. This simple text is to be then converted into dialogues that are to be grouped with each other in such way that it could be provided as an input in vector form for the neural network model to understand.

### 15.4.3 To Implement Feature Extraction so as to Extract the Patient’s Details to Develop a Video-Calling Web Application

It is very essential to understand the conversations between the doctors and the patients if the aim is to finally generate a medical report based just on the conversations. The objective is to create a module that will understand the dialogues generated and then create a report extracting necessary information from these dialogues. For this purpose, it needs to understand various features of NLP that would help it to extract just the relevant information and discard the other. It needs to learn to identify which of the words are of importance and what does that particular word depicts. This would help it to provide meaning to the sentences in the dialogue. Once it figures out the meanings of the sentences, now the final task is to generate the report taking into consideration information that has been extracted yet.

### 15.4.4 To Build a Recommender System Similar for Patients Based on the Features Extracted

The ultimate objective is to display the profiles of the patients that are similar to the one that the doctor has been currently working on. The aim is basically to create a content-based recommender system to provide recommendations to the doctor.

First of all, the model must understand the features of the current patient. Then, it must be able to compare those features with the history of all other previous patients and then display the cases that have the most similarity score.

## 15.5 PROPOSED METHOD/ALGORITHM

This work aims in making a doctor-patient conversation to be easily and conveniently carried out. The idea is to create a video-calling web application between the doctor and the patient so that they can communicate with each other from where ever they are and at a time that is feasible to both. It also helps to generate a medical report automatically understanding the conversation between them and retaining required documents whenever necessary.

Consider a patient is having a medical emergency and he/she has to visit the doctor but the doctor is out of town. This is one of the cases where the patient can contact the doctor through video call and the report of their conversation will be automatically generated. Slot filling, a technique to understand spoken language and particularly the dialogue, has been used for the generation of the report by understanding and extracting important keywords from the conversations. The term spoken language processing for semantic analysis is understanding of human speech directed

![](img/56cfba5af06305175d6488aec4d55ab0_292_0.png)

**FIGURE 15.3** Technologies used.

organization to integrate with their database and achieve the optimal results without any ambiguity in the system and its data stored. Expected errors and anomalies have been considered and handled in case of exceptions which make it robust enough for any layman to use it without a second thought.

Hardware support is not much of a cause of concern as any system able to carry out a video call can launch this system and there are no such system configurations required as the data size has been handled using the server and the compatibility of the interface would not be an issue. Scalability and reliability are the most important features which make this implementation an effective outcome.

**Technological Requirements** (Figure 15.3):

**System Requirements:**

1. Web camera
2. Microphone
3. Browser

**Use Case Diagram** (Figure 15.4):

### 15.6.3 DESIGN AND TEST STEPS

1. Connecting video call between doctor and patient and carrying out the conversation
2. Extracting the audio from the video call and converting it into text in real time
3. Applying NLP on that extracted text to extract essential keywords for understanding the conversation
4. Generating and displaying a medical report using the extracted keywords
5. Storing the report in the database for future
6. Implementation of a content-based recommender system to recommend the doctor with similar patient’s cases

**FIGURE 15.6** Architecture of the model.

![](img/56cfba5af06305175d6488aec4d55ab0_297_0.png)

**Embedding Layer:** The indexes are assigned completely random. Semantic relation between the words is not portrayed by the index assigned to them. For this problem, first the embedding layer is used which according to the vector of each word assigns new vector with updated indexes. This makes similar words have closer vectors. In short, this layer groups the words according to the meaning of the word.

**Convolution Layer:** Bidirectional RNNs are challenging to deploy in online low latency settings. To counter this, a lookahead convolution layer is used which gets information from future subsequence in efficient manner to improve unidirectional RNNs.

**Gated Recurrent Unit:** GRU is an extension of Long Short-Term Memory (LSTM) which is an extension of a simple RNN.

GRU works on two gates, update gate and reset gate. In update gate, which information is discarded and which information is kept is decided while reset gate decides point in past up to which information should be kept. Since the created dataset is limited, the use of LSTM is not advisable which needs larger dataset. For this reason, a layer of gated recurrent units is used. Also, due to lesser tensor operations, GRUs are faster to train.

**Time Distributed Dense Layer:** This layer is used for each word to determine the appropriate label for the word. Time distributed dense layer is used because it needs to apply fully connected dense on each time step and get output separately by time steps which helps us to keep one-to-one relations on input and output. The softmax function calculates probability of each label for the word and label with the highest probability is chosen. The type of gradient descent used for the model is Adam and loss function used is categorical cross-entropy. Adam is an optimization algorithm that is extension of the classical stochastic gradient descent procedure to update
