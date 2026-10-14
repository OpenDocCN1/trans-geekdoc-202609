
6. Since BERT, many flavors of pre-trained models have been made available across different domains, providing models that can be fine-tuned to domain-specific data across science, medicine, and finance. In addition, language-specific pre-trained models offer increasingly competitive results on downstream language specific tasks. In [`Chapter 6`](#ch6.xhtml), we discuss the pre-trained models that are available, showing their benefits and applications to specific domains such as computer vision, speech, time series, and text. This chapter includes a case study that compares the performance of three transformer-based automatic speech recognition models.

7. There is a need to understand the models from an explainability standpoint in many critical applications and given the black-box nature of transformers-based models. In [`Chapter 7`](#ch7.xhtml), we will cover the traits of the models that address explainability, related areas that impact explainability, the taxonomy of explainable methods applied to the transformer-based and attention-based systems, and finally, a detailed case study in the electronic health record systems using transformers with different explainable techniques to become more practical.

# Authors

`Uday Kamath` has spent more than two decades developing analytics products and combines this experience with learning in statistics, optimization, machine learning, bioinformatics, and evolutionary computing. He has contributed to many journals, conferences, and books, is the author of [`XAI: An Introduction to Interpretable XAI, Deep Learning for NLP and Speech Recognition, Mastering Java Machine Learning, and Machine Learning: End-to-End Guide for Java Developers`](#). He held many senior roles: chief analytics officer for Digital Reasoning, advisor for Falkonry, and chief data scientist for BAE Systems Applied Intelligence. Dr. Kamath has many patents and has built commercial products using AI in domains such as compliance, cybersecurity, financial crime, and bioinformatics. He currently works as the chief analytics officer for Smarsh. He is responsible for data science, research of analytical products employing deep learning, transformers, explainable AI, and modern techniques in speech and text for the financial domain and healthcare.

`Kenneth L. Graham` has two decades experience solving quantitative problems in multiple domains, including Monte Carlo simulation, NLP, anomaly detection, cybersecurity, and behavioral profiling. For the past ten years, he has focused on building scalable solutions in NLP for government and industry, including entity coreference resolution, text classification, active learning, automatic speech recognition, and temporal normalization. He currently works at AppFolio as a senior machine learning engineer. Dr. Graham has five patents for his work in natural language processing, seven research publications, and a PhD in condensed matter physics.

`Wael Emara` has two decades of experience in academia and industry. He has a PhD in computer engineering and computer science with emphasis on machine learning and artificial intelligence. His technical background and research spans signal and image processing, computer vision, medical imaging, social media analytics, machine learning, and natural language processing. Dr. Emara has contributed to many peer-reviewed publications in various machine learning topics and he is active in the technical community in the greater New York area. He currently works as a principal data scientist at Smarsh, Inc. for Digital Reasoning where he is doing research on state-of-the-art artificial intelligence NLP systems.

# Contributors

**Krishna Choppella**

BAE Systems AI

Toronto, Canada

**Mitch Naylor**

Smarsh, Inc.

Nashville, Tennessee

**Vedant Vajre**

Stone Bridge High School

Ashburn, Virginia

# CHAPTER 1Deep Learning and Transformers: An Introduction

DOI: [`10.1201/9781003170082-1`](https://doi.org/10.1201/9781003170082-1)

`TRANSFORMERS` are deep learning models that have achieved state-of-the-art performance in several fields such as natural language processing, computer vision, and speech recognition. Indeed, the massive surge of recently proposed transformer model variants has meant researchers and practitioners alike find it challenging to keep pace. In this chapter, we provide a brief history of diverse research directly or indirectly connected to the innovation of transformers. Next, we discuss a taxonomy based on changes in the architecture for efficiency in computation, memory, applications, etc., which can help navigate the complex innovation space. Finally, we provide resources in tools, libraries, books, and online courses that the readers can benefit from in their pursuit.

## 1.1 Deep Learning: A Historic Perspective

In the early 1940s, S. McCulloch and W. Pitts, using a simple electrical circuit called a “threshold logic unit”, simulated intelligent behavior by emulating how the brain works \[[179](#refbib.xhtml#refbib_179)\]. The simple model had the first neuron with inputs and outputs that would generate an output 0 when the “weighted sum” was below a threshold and 1 otherwise, which later became the basis of all the neural architectures. The weights were not learned but adjusted. In his book *The Organization of Behaviour* (1949), Donald Hebb laid the foundation of complex neural processing by proposing how neural pathways can have multiple neurons firing and strengthening over time \[[108](#refbib.xhtml#refbib_108)\]. Frank Rosenblatt, in his seminal work, extended the McCulloch–Pitts neuron, referring to it as the “Mark I Perceptron”; given the inputs, it generated outputs using linear thresholding logic \[[212](#refbib.xhtml#refbib_212)\].

The weights in the perceptron were “learned” by repeatedly passing the inputs and reducing the difference between the predicted output and the desired output, thus giving birth to the basic neural learning algorithm. Marvin Minsky and Seymour Papert later published the book *Perceptrons* which revealed the limitations of perceptrons in learning the simple exclusive-or function (XOR) and thus prompting the so-called The First AI Winter \[[186](#refbib.xhtml#refbib_186)\].

John Hopfield introduced “Hopfield Networks”, one of the first recurrent neural networks (RNNs) that serve as a content-addressable memory system \[[117](#refbib.xhtml#refbib_117)\].

In 1986, David Rumelhart, Geoff Hinton, and Ronald Williams published the seminal work “Learning representations by back-propagating errors” \[[217](#refbib.xhtml#refbib_217)\]. Their work confirms how a multi-layered neural network using many “hidden” layers can overcome the weakness of perceptrons in learning complex patterns with relatively simple training procedures. The building blocks for this work had been laid down by various research over the years by S. Linnainmaa, P. Werbos, K. Fukushima, D. Parker, and Y. LeCun \[[91](#refbib.xhtml#refbib_91), [149](#refbib.xhtml#refbib_149), [164](#refbib.xhtml#refbib_164), [196](#refbib.xhtml#refbib_196), [267](#refbib.xhtml#refbib_267)\].

LeCun et al., through their research and implementation, led to the first widespread application of neural networks to recognize the hand-written digits used by the U.S. Postal Service \[[150](#refbib.xhtml#refbib_150)\]. This work is a critical milestone in deep learning history, proving the utility of convolution operations and weight sharing in learning the features in computer vision.

Backpropagation, the key optimization technique, encountered a number of issues such as vanishing gradients, exploding gradients, and the inability to learn long-term information, to name a few \[[115](#refbib.xhtml#refbib_115)\]. Hochreiter and Schmidhuber, in their work,“Long short-term memory (LSTM)” architecture, demonstrated how issues with long-term dependencies could overcome shortcomings of backpropagation over time \[[116](#refbib.xhtml#refbib_116)\].
