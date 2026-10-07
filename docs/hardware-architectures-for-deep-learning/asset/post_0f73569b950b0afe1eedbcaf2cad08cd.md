
# Acknowledgments

First and foremost, we would like to thank all the contributing authors of this book who shared their knowledge and experience in their respective chapters.

We also acknowledge the financial support from the Swedish Foundation for International Cooperation in Research and Higher Education (STINT). The STINT's Initiation Grant program supported the mobility between our research groups and facilitated managing and developing this book.

Finally, we would like to thank the IET editors and production team for their continued assistance in managing the process of editing the book during this project.

## Part I

## Deep learning and neural networks: concepts and models

## Chapter 1

## An introduction to artificial neural networks

Ahmad Kalhor¹

In this chapter, an introduction to neural networks (NNs) with an emphasis on classification and regression applications is presented. In this chapter, some preliminaries about natural and artificial neural networks (ANNs) are explained. Then, by giving initial concepts about classification and regression problems, appropriate overall structures of ANNs for such applications are explained. The simple structures of NNs and their limitations as well as more powerful multilayer and deep learning models are introduced in the next part of this chapter. Finally, convolutional NNs and some of their well-known developments are briefly explained.

### 1.1 Introduction

A conventional computing paradigm solves a problem by an algorithmic way, in which programs provide every step that had to be taken, in the form of deterministic algorithms, to carry out the tasks. In some domains, however, designing an explicit algorithm is not always possible (or is very difficult), particularly when system has to deal with situations and data that did not fit within the explicit parameters provided by the programmers (e.g., for recognizing emotions or answering new questions). Machine learning is a subset of artificial intelligence actually takes the way in which our brain solves these problems: learn to solve a problem by analyzing training examples. It trains a machine to perform a particular task using large amounts of data and routines that provide the ability to learn from the data. Deep learning is a subset of machine learning that uses DNNs to solve complex problems.

A NN is a set of simple processing units, called neurons, that are arranged in multiple layers, through which a desired output result is generated from exogenous or stimulating inputs. Figure 1.1 shows a simple diagram of a NN.

### 1.1.1 Natural NNs

NNs have been emerged naturally in the body of animals to provide their perception from the environment and learn to take appropriate reactions against stimuli.

> ¹School of Electrical and Computer Engineering, University of Tehran, Tehran, Iran

![](img/e6e752b99eb1621488c89445a57e2a86_29_0.png)

![](img/e6e752b99eb1621488c89445a57e2a86_29_1.png)

Such networks are the source of the intelligence, through which creatures can understand the outside world, make their habitation, and take suitable reactions in the environment. To answer an important question that how such intelligence emerges, biologists and scientists have discovered, and still exploring, the brain, nervous system, and spinal cord (Figure 1.2).

They have continuously developed their knowledge about the nervous systems. Neuroscientists currently research about the structure and function of the brain to find out how the human brain models and learns the real world. Figure 1.3 shows the structure of a nerve cell, or neuron, which includes dendrites, cell body, axon, cell nucleus, and synaptic gaps [1].

![](img/e6e752b99eb1621488c89445a57e2a86_30_0.png)

Figure 1.3 Structure of a nerve cell (neuron) including dendrites, cell body, axon, cell nucleus and synaptic gap

A certain neuron includes plenty of dendrites that absorb the incoming electro-chemical signals from adjacent neurons and accumulate them within its cell body. In the kernel of the cell, the accumulated signal will be compared with a threshold and if it is bigger than the threshold, it will activate. By neuron activation, it spikes and sends a chemical signal to adjacent neurons through the axon. A synaptic gap plays an important role in giving weights to the transformed signal between the axons and dendrites of connected neurons.

There are three types of neurons in the nervous system. Sensory neurons get information about what is going inside and outside of the body and bring that information into the central nervous system (CNS), so as to be processed by the neural system. Interneurons connect one neuron to another and are found only in the CNS. Most of the interneurons are in the brain. Motor neurons get information from other neurons and convey commands to the muscles, organs, and glands.

We can consider an input-output layer-based structure between the input data (stimulus) received by the input sensory neurons (input layer) and the data generated by motor neurons (output layer), the set of interneurons from the hidden layers. Figure 1.4 shows a simplified input-output scheme of a nervous system.

The NN is the source of some imperative learning capabilities in the human body. The humankind can learn to classify all types of signals received from their senses including visual (seeing), auditory (hearing), tactile (touch), gustatory (taste), olfactory (smell), vestibular (movement), and proprioceptive (body awareness). They can make long and short memories about different events and senses they have experienced or learned in the past. They can provide skills to do more complicated tasks and actions, which they have learned or experienced.

Perhaps the computational intelligence, including logic, mathematics, and inference, is the most significant exclusive capability of the human’s NN.

![](img/e6e752b99eb1621488c89445a57e2a86_31_0.png)

There are some interesting facts about the brain. There are about 100 billion neurons in a normal human brain with about 100 trillion total connections that give 1,000 connections for each neuron, on average. The learning processes and the inter-connections among neurons are mainly due to the functionality of synaptic gaps. The communication speed (electrochemical signal transition) for each neuron is low but since the communications are done massively and in parallel, the total processing speed of the brain is high. The robustness of the natural NNs is high in learning and even if some parts of the brain damaged, the learning and inference processes will proceed. Due to high-level abstraction and inference in the brain, its generalization is high.

### 1.1.2 Artificial neural networks

Inspired by natural NNs, from the beginning of the twentieth century, scientists and engineers have intended to design ANNs in order to provide solutions for challenging and real-world problems in the same way as the human brain operates. These efforts led to the emergence of ANNs.

The range of engineering or noneg problems solved by ANNs has been continually increased through time. Among different applications, classification and regression are more investigated by ANNs. Classification and categorizing different objects, images, texts, speeches, signatures, videos, and so far are performed appropriately by ANNs. Fault detection in industrial systems and fraud and anomaly detection in social and finance systems are critical examples of classification problems that are efficiently solved by ANNs. In regression problems, function approximation, simulation of natural and cosmic phenomena, time series prediction, signal recovery and repair are some examples that can be solved by NNs.

Some applications are developed through memory NNs: identification by biometric signals, character recognition, machine translation, word prediction in a writing or speech process, walking and moving modeling, training social robots to interact with the environment, image captioning, and enriching video or image with descriptions. Besides supervised applications, there are some unsupervised
