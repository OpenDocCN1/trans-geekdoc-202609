![](images/cover.jpg)

![image](images/cover.jpg)

# Essentials of  
Deep Learning and  
AI

![](images/line.jpg)

# *Experience Unsupervised Learning,  
Autoencoders, Feature Engineering and  
Time Series Analysis with TensorFlow,  
Keras, and scikit-learn*

![](images/line.jpg)

# Shashidhar Soppin

# Dr. Manjunath Ramachandra

# B N Chandrashekar

![](images/logo.jpg)

[www.bpbonline.com](http://www.bpbonline.com)

**FIRST EDITION 2022**

**Copyright © BPB Publications, India**

**ISBN: 978-93-91030-353**

All Rights Reserved. No part of this publication may be reproduced, distributed or transmitted in any form or by any means or stored in a database or retrieval system, without the prior written permission of the publisher with the exception to the program listings which may be entered, stored and executed in a computer system, but they can not be reproduced by the means of publication, photocopy, recording, or by any electronic and mechanical means.

**LIMITS OF LIABILITY AND DISCLAIMER OF WARRANTY**

The information contained in this book is true to correct and the best of author’s and publisher’s knowledge. The author has made every effort to ensure the accuracy of these publications, but publisher cannot be held responsible for any loss or damage arising from any information in this book.

All trademarks referred to in the book are acknowledged as properties of their respective owners but BPB Publications cannot guarantee the accuracy of this information.

![](images/logo1.jpg)

[www.bpbonline.com](http://www.bpbonline.com/)

# Foreword

Machine learning (ML) and artificial intelligence (AI) are revolutionizing almost every aspect of the business. From self-driven cars to predicting inventory to diagnosing cancer, AI is set to impact nearly every domain and industry vertical.

While it is evident that AI is the most important technology of our times, there is not enough talent in the market. It is partly due to the complexity involved in learning and mastering the concepts of ML and AI. Many budding professionals and existing software developers aspiring to become AI engineers are often overwhelmed by the breadth and depth of the available tools and technologies.

This book, Essentials of Deep Learning and AI, by Shashidhar Soppin, Dr. Manjunath Ramachandra, and B N Chandrashekar, takes a unique approach in introducing the fundamental concepts of AI and ML. It will appeal to novices and experienced ML engineers due to the breadth and depth of the topics covered. It’s one of the most comprehensive books on AI available in the market.

What I like about this book is the balance it strikes between the theoretical and practical aspects of AI. It doesn’t intimidate those whose background is not mathematics or statistics. It also has the right balance between classical machine learning and deep learning, current and emerging techniques of AI. It is relevant to developers, business managers, technology decision-makers, and IT leaders.

The book has all the attributes to become an authoritative guide or textbook for teaching and learning ML and AI. Each chapter has a summary that acts as a quick reference. The multiple-choice questions at the end of each chapter enable the readers to assess themselves.

If you want to learn everything from the evolution of AI to advanced concepts such as ensemble methods and model optimization, look no further. This book has it all.

*—Mr Janakiram MSV*

# Dedicated to

*All the "Covid Warriors" who fought the war against the pandemic and A big thank you to all the corona warriors for all the selfless service offered.*

# About the Authors

**Shashidhar Soppin** has two decades of experience in IT industry. At present he is working as **Enterprise Architect in Zeta**. Earlier, he has worked as **DMTS** (Distinguished Member of Technical Staff) with progressive history of defining vision, strategy, and technical roadmap, architecting solutions, recommending new approaches via technology enablement and managing large-scale & complex IT projects as part of Wipro. He has worked on, Multi-Cloud (OpenStack, Azure/AWS), Cloud Native Technologies, AIX-OS, HCI (Hyper Converged Infra), Docker Containers and Kubernetes for microservices-based architectures and in Virtualization domains. His areas of interest include AI/ML, Deep Learning and IoT. **He has several granted and filed patents on various technologies on his name.** He is an avid Author for the OSFY Magazine, Written Articles on Micro-services and Kubernetes, Docker, OpenStack, Storage, Node Red, ML & DL to name few {**[https://opensourceforu.com/author/shashidharsoppin/](https://opensourceforu.com/author/shashidharsoppin/)**}. He has also written articles for **Medium.com** and **Research-gate** and also a blogger for “**Linux-techi**”. He has presented papers in conferences and panel speaker in industry forums. He has worked for various organizations including IBM-ISL, Ness Technologies before joining Wipro. He got certified from Great Learning Institute on Deep Learning Technology, Deep Learning Specialization from Coursera and has various Cloud certifications.

**[linkedin.com/in/shashidhar-soppin-8264282](http://linkedin.com/in/shashidhar-soppin-8264282)**

**[https://www.linuxtechi.com/author/shashidhar/](https://www.linuxtechi.com/author/shashidhar/)**

**Dr. Manjunath Ramachandra** has a blend of experience over twenty five years in the verticals of Healthcare, Telecom and consumer electronics spanning the technologies such as signal & Image processing, Artificial intelligence, cloud computing, IoT, wireless communication and quantum computing. He worked for the companies such as Tata Consultancy Services, Royal Philips and was placed in Wipro Limited as principal consultant. He has filed about 90 patents, authored 210 Research papers in international conferences and journals and a book. He was a member of the embedded systems special interest group at NASSCOM. He represented the industry in international standardization bodies such as Wi-Fi Alliance, served as the editor for the regional profiles standard in Digital living network alliance (DLNA) and as the industry liaison officer for the CE-Linux Forum. He has delivered over 24 keynote speeches and conducted over 21 workshop and tutorial sessions. He figures in Marquis Who’s Who 2008 & “2000 outstanding intellectuals of the 21st century”, International Biographical Center, UK. His areas of interest include Deep Learning/ Artificial intelligence, Signal & Image processing and wireless communications.

**B N Chandrashekar**, a principal consultant by designation is a veteran of Wipro Technologies Limited and has industry experience of around 20 years. He is a post graduate from Indian Institute of Science and has toned his credibility by owning and getting moulded in the roles of Researcher, Data Science Consultant, Technical Director and Full Stack AI Consultant. He has handled multiple cross-domain projects starting from infrastructure setup to scoping, development, delivery and with support and maintenance. He has work experience in cutting edge technologies and adapts to any new technology in a short time. He has experience in writing proposals, hands-on in multiple high-level programming and scripting languages. He has contributed to programs and tools to open source, co-authored journals and conference papers. He has co-authored publications to online portals like **medium.com, researchgate.net**, and **OSFY.com**. He has pioneered the webinars to university professors at Wipro Tech Bootcamp and seminars at engineering colleges on explainable AI framework. He has co-authored multiple patents and has got certified from Great Learning Institute on Deep Learning Technology and Quantum Learning from Coursera.

**[https://www.linkedin.com/in/](https://www.linkedin.com/in/)**

**[https://github.com/chandru4ni/](https://github.com/chandru4ni/)**

# About the Reviewer

**Sethuraman U.,** is at present working as Technical lead in Panasonic Automotive, in Frankfurt, Main, Hesse, Germany. He has decades of experience in various areas like Computer Vision, Deep learning, Machine Learning, AR/VR, ADAS, Computer vision, Embedded Systems, Video Codecs, ADAS, Computer vision areas. He has done Master of Technology - MTech Software Systems (Specialisation in Data Analytics), from Birla Institute of Technology and Science, Pilani. He has done his Bachelor of Engineering (ECE)Electronics and Communications Engineering from Bharathidasan University. He has decades of IT industry experience in various areas and also he has many patents on his name and authored papers. He is working for Wipro R&D, Toshiba India Pvt. Ltd and GDA Technologies Inc (now an L&T InfoTech company) before Panasonic stint.

# Acknowledgement

We are grateful to BPB Publications, who came forward to publish this book and their entire team of BPB Publications were always kind, cooperative and understanding. Mr Sethuraman and Raju (from Wipro CTO team) who reviewed this book with abundant patience and helped us say what we had wanted to, improvising each and every page of this book with care. Their patience and guidance were invaluable.

The journey through learning conceptual technologies brought to next level by using modern methods and with the use of artificial intelligence and machine learning in the field, has been very rewarding, as it has given us the opportunity to work for some of the customers and solving their critical problems.

A special thank you goes to BPB design, technical and manuscription team for their patience in coming with beautiful cover design and **Mr Janakiram MSV** who is a analyst, advisor and architect for writing foreword given a short notice.

**Chandrashekar B N:** Also, I would like to call out my wife, parents and daughter, family and relatives, who they realized it or not supported me in all front to shape this book. I am thankful to my manager, friends and all sources of information media that helped me to build the knowledge of this book.

**Shashidhar Soppin:** Special and Big thanks also go to my Wife, Daughter, Mom & Mother-in-law the "4 ladies" who constantly supported me with delicious food and constant support and my brother and late father for their motivation and guidance while writing this book. I am also thankful to my family, relatives, manager, friends and all sources that helped me to build the knowledge for this book.

**Manjunath Ramachandra Iyer:** I am deeply indebted to the tech giants who made the AI/ML technologies popular and accessible. Also thankful for My wife, Mother, children, aunt, family, relatives and cats who were understanding and supportive throughout the project.

We are thankful to our Wipro colleagues, CTO team, ER&D team and leaders, without the help of their understanding this book would have not come out.

We are thankful to our Zeta colleagues, CTO and leaders, without the help of their understanding this book would have not come out.

# Preface

Artificial intelligence has proliferated deep in to all verticals of the industry. It has enabled the business solutions for the existing problems apart from providing new opportunities and avenues. As a result, technical community with varied degree of expertise and exposure to the underlying technologies will be interested to learn the state of the art quickly and adopt the same solutions. While the content available in public domain provides them with the required information to an extent, it also gives a lot more information. The user loses the focus and finally may not get the precise information. There is no single stop solution for the problem today. This book is written to reduce the burden on the user to a great extent by directly providing the required information. Accordingly, all sections are organised to be self-contained as far as possible and provide the precise content the reader is looking for. Organisation of the book is divided into several self-contained modules to make it more readable.

In each chapter, adequate examples and code snippets are provided for the reader to try out. The programs may be executed directly on the indicated platforms to observe the results. Source of the required data to develop the models, pre-trained models and the settings of the configurable parameters to get optimal output are detailed. The case studies provided in the chapters indicate the contemporary business problems and the solution approaches are also detailed in the book. The book contains overall 14 chapters. The details covered in each chapter are provided below.

**Who is this book for?**

This book is most relevant to readers working in various IT positions like developers, managers, business leaders, data scientists, machine learning engineers, and alike. Even the experienced AI/ML experts/users can make use of valuable material from this book. It also touches upon advanced topics in AI/ML and DL technologies.

**What questions does this book answer?**

In coming up with this book, we authors spoke to many academic and industry experts from all walks of life. Below are some of the questions we wanted to highlight,

*   Basic understanding of neural network building, AI concepts explained as simple as possible.
*   We would like to highlight why one should invest time in learning these technologies.
*   Multiple ways of learning concepts and technologies are detailed out in simplified manner.

**[Chapter 1](#c01.xhtml),** This chapter provides overview and historical evolution of AI technologies used in different industry verticals. It considers the user preferences as well as dynamic emotional state. It briefs about the broad classification of AI, ML and DL. This chapter covers AI usage in different industry domains and sectors. End to end tools and frameworks used in the lifecycle of AI are covered. The various datasets used to build ML and DL models have been described.

**[Chapter 2](#c02.xhtml),** This chapter describes one of the most popular class of algorithms used in supervised machine learning. This chapter details the various methods for data extraction, data annotation and better prediction. Optical character recognition used widely in industry has been described. The libraries, and packages for supervised learning algorithms are detailed in this chapter. Depiction of performance metrics and computation techniques used for optimization and loss methods are covered.

**[Chapter 3](#c03.xhtml),** This chapter describes most popular and challenging class of algorithms used when labelled data is not available. This chapter describes various clustering techniques and data pre-processing methods. Selection of significant input features and dimensionality reduction using various PCA techniques and Singular Value Decomposition (SVD) are explained. The libraries and packages for the various techniques explained are provided. Depiction of performance metrics and computation techniques used for optimization and loss methods are covered.

**[Chapter 4](#c04.xhtml),** This chapter describes the process of transforming raw data into set of useful features. It gives details of feature extraction, feature selection and hardening features. It helps in building robust and flexible models by better feature selection. It describes various techniques on feature encoding, data preparation and feature engineering.

**[Chapter 5](#c05.xhtml),** This chapter provides in-depth understanding of advanced classification techniques, data association, clustering and regression. This chapter explains techniques to handle any kind of data involving simple to complex characteristics and small to huge data size. Use case of recommendations in retail industry is provided.

**[Chapter 6](#c06.xhtml),** This chapter explains the various methods for handling time series data. It deals with various time series models and related algorithms. It describes categories of time series algorithms along with examples. Usage of time series data for predictive models is described.

**[Chapter 7](#c07.xhtml),** This chapter provides various techniques for data clean-up before it is consumed by models. The various pre-processing techniques such as data formatting and normalization are described. The effect of bias and variance on the models is analysed. Different techniques for handling overfitting and underfitting of models are provided. Use case and examples for data formatting and normalization are provided.

**[Chapter 8](#c08.xhtml),** This chapter covers mechanism for combining weak models to develop strong models using ensemble of algorithms. It describes systematic approach, hyper parameter tuning and optimal parameter selection for industry grade models. Latest trends in ensemble methods like boosting and genetic algorithm are explained.

**[Chapter 9](#c09.xhtml),** This chapter explains one of the most complex and difficult human like data handling using deep learning techniques. This technique helps to solve problems which cannot be handled by machine learning algorithms. The training mechanism and the architecture of CNN are detailed in this chapter.

**[Chapter 10](#c10.xhtml),** This chapter focuses on multi-layer perceptron (MLP) starting from simple perceptron and activation functions. It explains the architecture of simple perceptron model. It provides the latest trends in MLP like knowledge distillation and with a programming example.

**[Chapter 11](#c11.xhtml),** This chapter deals with long short-term memory models which are mainly used for handling sequential data. The architectures of RNN, GRU and LSTM are explained. The analytical details of the architecture of the gates are described. The variants of LSTM such as bidirectional LSTM, and attention-based LSTM are elaborated.

**[Chapter 12](#c12.xhtml),** This chapter deal with automatic generation of features for the given input data. Autoencoders deal with encoders and decoders and are connected with feed-forward neural networks. The features generation example for MNIST dataset is provided and architecture of autoencoders and its variants are discussed. Usage of autoencoders for denoising, and sparse representation are detailed in this chapter.

**[Chapter 13](#c13.xhtml),** This chapter covers the industrial applications of deep learning and machine learning algorithms. The different hardware and software approaches are detailed. The business use case belonging to telecom, IoT, healthcare and cloud are described. This chapter explains how multiple algorithms of AI/ML are incorporated in working systems.

**[Chapter 14](#c14.xhtml),** The final chapter discusses potential usage of AI, ML and DL along with future and emerging technologies. These technologies enrich AI/ML algorithms providing faster and secure methods for their execution. The technologies include quantum computing, cloud computing, 5G and neuromorphic computing. The AI/ML enables widespread usage of these technologies.

# Downloading the code bundle  
and coloured images:

Please follow the link to download the  
***Code Bundle*** and the ***Coloured Images*** of the book:

# [https://rebrand.ly/a49452](https://rebrand.ly/a49452)

# Errata

We take immense pride in our work at BPB Publications and follow best practices to ensure the accuracy of our content to provide with an indulging reading experience to our subscribers. Our readers are our mirrors, and we use their inputs to reflect and improve upon human errors, if any, that may have occurred during the publishing processes involved. To let us maintain the quality and help us reach out to any readers who might be having difficulties due to any unforeseen errors, please write to us at :

**[errata@bpbonline.com](mailto:errata@bpbonline.com)**

Your support, suggestions and feedbacks are highly appreciated by the BPB Publications’ Family.

Did you know that BPB offers eBook versions of every book published, with PDF and ePub files available? You can upgrade to the eBook version at **[www.bpbonline.com](http://www.bpbonline.com)** and as a print book customer, you are entitled to a discount on the eBook copy. Get in touch with us at **[business@bpbonline.com](mailto:business@bpbonline.com)** for more details.

At **[www.bpbonline.com](http://www.bpbonline.com)**, you can also read a collection of free technical articles, sign up for a range of free newsletters, and receive exclusive discounts and offers on BPB books and eBooks.

# BPB is searching for authors like you

If you're interested in becoming an author for BPB, please visit [**www.bpbonline.com**](http://www.bpbonline.com/) and apply today. We have worked with thousands of developers and tech professionals, just like you, to help them share their insight with the global tech community. You can make a general application, apply for a specific hot topic that we are recruiting an author for, or submit your own idea.

The code bundle for the book is also hosted on GitHub at **[https://github.com/bpbpublications/Essentials-of-Deep-Learning-and-AI](https://github.com/bpbpublications/Essentials-of-Deep-Learning-and-AI)**. In case there's an update to the code, it will be updated on the existing GitHub repository.

We also have other code bundles from our rich catalog of books and videos available at **[https://github.com/bpbpublications](https://github.com/bpbpublications)**. Check them out!

# PIRACY

If you come across any illegal copies of our works in any form on the internet, we would be grateful if you would provide us with the location address or website name. Please contact us at [**business@bpbonline.com**](mailto:business@bpbonline.com) with a link to the material.

# If you are interested in becoming an author

If there is a topic that you have expertise in, and you are interested in either writing or contributing to a book, please visit [**www.bpbonline.com**.](http://www.bpbonline.com/)

# REVIEWS

Please leave a review. Once you have read and used this book, why not leave a review on the site that you purchased it from? Potential readers can then see and use your unbiased opinion to make purchase decisions, we at BPB can understand what you think about our products, and our authors can see your feedback on their book. Thank you!

For more information about BPB, please visit [**www.bpbonline.com**.](http://www.bpbonline.com/)

# [CHAPTER 1](#toc.xhtml#c01)

# [Introduction](#toc.xhtml#c01)

The usage of different instruments and equipment by mankind to run the day-to-day activities dates back to the *Stone Age*. Since then, tens of thousands of devices have evolved to cater for household activities, infrastructure, healthcare, entertainment, communication, transportation, and the like. While most of these devices are dumb, smart devices such as personal assist has started to hit the market. The vision of such devices is not new and have found their place in the stories and legends. The magic lamp of *Aladdin* to the robots of *Isaac Asimov* has led to several inventions. Over a period of time, the “*dumb*” devices have been infused with the required intelligence to understand the surroundings and act accordingly. For example, a fan gets switched on when the ambient temperature exceeds 35 degree Celsius. Today, the expectation of people has increased several folds. The devices are required to understand not only the surroundings but also the end-user! They need to consider the static preferences of the users as well as the dynamic emotional state. This requirement led to large-scale research in data processing and the related fields under the term **Artificial Intelligence** and resulted in a massive proliferation of smart devices.

# [Structure](#toc.xhtml#s1a)

In this chapter, we will discuss the following topics:

*   Artificial intelligence 
    *   What is Artificial Intelligence?
    *   Definitions of AI
    *   Applications of AI
    *   Use cases of AI
    *   Broad classification of what is AI, ML, FL, and DL?
*   Machine learning 
    *   History and definitions of ML
    *   ML and its applications
    *   Classification of ML algorithms
*   Deep Learning 
    *   Prerequisite to understand deep learning
    *   Difference between machine learning & deep learning
*   Tools and frameworks for AI, ML, and DL
*   Languages used for AI, ML, and DL
*   Datasets for AI, ML, and DL development

# [Objectives](#toc.xhtml#s2a)

After studying this chapter, you should be able to:

*   Understand the concepts of AI, ML, DL and their components
*   History of AI, ML, and DL
*   Defined AI, ML, DL along with some examples and applications
*   Benefits of using AI, ML, and DL in overall
*   Programming languages used for ML & DL
*   Standard tools used for ML & DL
*   Reference database used for model development

# [1.1 Artificial intelligence](#toc.xhtml#s3a)

Making computers to “*think like humans*” was the main motivation behind the development of Artificial Intelligence. With this goal in mind, many pioneers as described later in this chapter, have contributed to AI and its advancement. Many advancements in the field of computer science also helped AI indirectly. All these put together, AI prospered over a period of years.

# [1.1.1 What is Artificial Intelligence?](#toc.xhtml#s4a)

**Artificial Intelligence** (**AI**) is the interdisciplinary umbrella term that spans the tools and techniques required to incorporate human-like intelligence into a system. The system can be a piece of software such as a dialog system and a hardware component such as a smart **Internet of Things** (**IoT**) or a machine such as a robotic arm. *Alan Turing* has defined the test criteria for a device or a program to be called as intelligent, to indicate how closely they can imitate human beings.

We are in the era of the “*information age*” (also sometimes called as “*Computer age*”, “*Digital Age*” or “*New media age*”), this is the golden age of modern human history. From taking selfies to storing files in the cloud, the growth of IoT based devices, and social media usage, we deal with quintillion bytes of data each day. The amount of data each individual produces in the 20th century is mind-boggling and this will be a whopping number. As of late 2019, it is estimated that human beings along generated approximately 2.5 quintillion bytes of data.

This sudden rise of data, which the human brain has to deal with, will be quite challenging and cumbersome. Most of the data analytics now is done by artificial intelligence-based machines/systems, because of this huge data gathering and lots of insights are generated which assist humans in many predictive trends that are arising in the business and software industry.

# [1.1.2 Definitions of Artificial Intelligence](#toc.xhtml#s5a)

AI has evolved from the 1950 of Alan Turing days to date. So many definitions of AI came up all these years. To make things simpler and easier, all the standard definitions are captured of AI from the pioneers of this industry. The following table explains the evolution of AI, the people who coined/defined the AI definition terminology during which year is described and when along with links.

 
| **Index** || **Year** || **AI definition** || **Defined By** || **Ref: Link** |
| --- | --- | --- | --- | --- |
| **1** || **1950** || Alan Turing didn't define what is AI. But while carrying out the so popularly called "*The Turing Test*" he came up with the question "*whether machines can think?*" || **Alan Turing** || **[https://plato.stanford.edu/entries/turing-test/](https://plato.stanford.edu/entries/turing-test/)****[https://www.csee.umbc.edu/courses/471/papers/turing.pdf](https://www.csee.umbc.edu/courses/471/papers/turing.pdf)** |
| **2** || **1978** || “*The automation of activities that we associate with human thinking, activities such as decision-making problem-solving learning*” || **Bellman** || **[https://archive.org/details/](https://archive.org/details/)****AnIntroductionToArtificialIntelligence/page****/n11/mode/2up** |
| **3** || **1985** || “*The exciting new effort to make computers think…machines with minds, in the full and literal sense.*” || **Haugeland** || **[https://mitpress.mit.edu/books/artificial-intelligence-1](https://mitpress.mit.edu/books/artificial-intelligence-1)** |
| **4** || **1985** || “*The study of mental faculties through the use of computational models*” || **Charniak &McDermott** || **[https://dl.acm.org/doi/book/10.5555/30426](https://dl.acm.org/doi/book/10.5555/30426)** |
| **5** || **1990** || “*The art of creating machines that perform functions that require intelligence when performed by people*” || **Kurzweil** ||  |
| **6** || **1992** || “*The study of the computations that make it possible to perceive, reason and act*” || **Winston** ||  |
| **7** || **1998** || “*Computational Intelligence is the study of the design intelligent agents*”“*AI….is concerned with intelligent behavior in artifacts”* || **Poole et.al****Nilsson** ||  |

**Table 1.1**

When we say artificial intelligence, immediately a question comes to our mind, “*Can computers think like human beings?*” Many of the above definitions try to answer this question briefly. But one more pair of recent year’s pioneers of the AI industry, *Peter Norvig* and *Stuart J Russel*, made it simpler to understand than defining it. What they say is that with the combinations of “*Thinking like humans*” and “*Thinking Rationally*” one can come to a conclusion about how AI works. They went on to say that

“*A computer agent is able to act autonomously, perceive its environment, and persist for an extended period of time, adapt to change, and adopt goals*.”

“*A rational agent is an agent that is able to act to achieve the expected best outcome (e.g., to persist or reach a goal)*.”

With the above definitions, it is clear that the computer not only works autonomously but also works with the rational agent which gives the best outcome.

# [1.1.3 Applications of Artificial Intelligence](#toc.xhtml#s6a)

Today machines can play brain-demanding games such as *Pogo Atari*, chess and defeat the champions in the fields. After the Second World War, the changing geopolitical landscape and the available technologies resulted in a revolution in all kinds of industries including healthcare and manufacturing. Large volumes of data started to pour in resulting in the development of machines with large computing power, built with intelligence. Smart algorithms were developed in languages such as Prolog and Lisp to process the data for robots and satellites. The AI systems took their origin there and continued the journey, undergoing metamorphism to reach the Python or Java-driven deep learning algorithms over the cloud supporting the data from the mobile phone or a gaming box. The availability of computing power and the development of new and revolutionary algorithms have made it move out of the industries, space exploration, and laboratories and reach out to the masses.

The AI systems are often modeled after human beings both, structurally and functionally. The information is organized into hierarchies with varying abstractions, clustered, classified, interpolated, and predicted as it happens in the brain. Several disciplines within AI such as convolutional neural networks, neuromorphic chips **Self-organizing Map** (**SoM**) have striking similarities with the human brain. The various functionalities of an AI system fall into the abstraction levels of an AI system indicated in *[Figure 1.1](#c01.xhtml#fig1_1)*:

![](images/Figure-1.1.jpg)

**Figure 1.1:** Abstraction levels of AI system

Let AI span several disciplines including machine learning, robotics, cognitive computing, neuroscience, computer vision, natural language processing, feature engineering, data science, and so on. Also, there is a certain degree of overlap among these disciplines. Some of the technologies overlapping with the AI are indicated in *[Figure 1.2](#c01.xhtml#fig1_2)*:

![](images/Figure-1.2.jpg)

**Figure 1.2:** Abstraction levels of the AI system

While the anticipation is that the machines are to think (and act) on behalf of the user, it is still fiction. However, the inventions happening in hardware architecture and algorithms are taking it closer. Today, devices are in a position to operate based on the context of the user and “*personal assist*” can provide in-time advice based on the large chunks of data they are able to mine and extract the information relevant to the user. They are able to provide in-time guidance to the user. For example, when the user is in a car in a by lane, provides an exit path or advice the user to take an umbrella when it is likely to rain in a few hours. One of the requirements to build an AI system is the availability of a large data corpus. While it is good to have more data, it leads to overfitting of the models where they are overexposed to specific examples and results in a poor show when alien data is ingested. To ensure that the devices or applications learn with adequate data, the discipline of machine learning is developed within AI.

*[Figure 1.3](#c01.xhtml#fig1_3)* provides differentiation between AI, ML, FL, and DL. This onion-layered diagram clearly explains what is what and with dependency on each other. The right side of the diagram lightly explains the definition of each:

![](images/Figure-1.3.jpg)

**Figure 1.3:** Difference between AI, ML, FL, and DL

The above diagram explains how AI, ML, FL, and DL are differentiated. All these mechanisms are dependent on each other, or to say they are like in an onion structure.

# [1.1.4 Industry domains and sectors along with sample use cases](#toc.xhtml#s7a)

The concepts introduced in the next sections are used in a variety of real-life solutions. It spans the domains such as finance, healthcare, automation, automotive, energy, consumers, telecom, and the technologies such as IoT, 5G, cloud computing, big data, chatbot, brain computing interface, augmented reality, virtual reality, and drones.

The applications can be categorized as real-time and offline. This difference has a say on the execution platform. The real-time applications require the algorithms to be executed and render the results in a stipulated time. For example, in threat detection, the images from a surveillance camera are to be analyzed in real-time. Based on the inference, the user needs to be alarmed of potential threats. This is in contrast with the example of credit card allocation based on user data. The model can work offline and throw out the decision of allocate/not allocate based on the data supplied.

In the categorization based on data size, two types of applications exist - one heavily making use of the data and the other one working with lesser data.

*   For example, face detection or optical character detection models require a large database for training and rigorous validation. Since such databases are available and accessible, AI models with a high degree of accuracy can be built.
*   On the other hand, the (image) data available for the identification of a bacteria is very few. This is partly because a single view of the bacteria is available and there is a limited variation across the images.

The applications are also classified based on the features required for inferencing.

*   For example, in the staging of a malignant tumor, the **region of interest** (**RoI**) is well defined and the relevant features are searched within those boundaries.
*   On the other hand, in the classification of an apple into good or bad, such boundaries on the apple are not known apriori. Also, the nature of the damage is not known in advance making it difficult to develop the model.

The applications are also grouped based on the nature of the data - sequential or parallel. The model architecture changes accordingly. For example, natural language processing problems increasingly make use of the sequential models because of the interdependency between the consecutive words and sentences. In contrast, image data gets processed better in a model with parallel architecture.

Some of the applications require continuous learning from the environment. For example, in brain-teasing games such as *Pogo Atari*, *Chess*, the model needs to learn the playing style of the opponent. This data from the game environment is used to fine-tune the model for better predictions. This is in contrast with the fully-trained models, for example, used for differentiating a cat from a dog.

The emerging applications such as 5G communications require prediction of the traffic patterns for effective and dynamic allocation of resources to meet the agreed **Quality of Service** (**QoS**). Here, the model needs to handle huge volumes of data that changes dynamically as the topography of the network itself gets hazy. On the other hand, applications such as fingerprint identifiers work better with static data collected apriori. Some of the common applications used in different business domains are indicated in *example 1.4*. The different applications and the models to realize the same is detailed in the rest of the chapters of this book.

![](images/Figure-1.4.jpg)

**Figure 1.4:** Use Cases of AI system

*[Figure 1.4](#c01.xhtml#fig1_4)* points out the various use cases of AI from a broader perspective. Domain-specific use cases are listed accordingly.

# [1.1.5 Broad classification of what is AI, ML, FL, and DL?](#toc.xhtml#s8a)

*[Figure 1.4](#c01.xhtml#fig1_4)* explains in detail the various applications of AI, ML, and DL in various domains and industry sectors.

Following is a detailed explanation of each of these applications:

*   **Finance**: AI/ML-based algorithms can be used for credit card fraud detection and while approving loans based on credit history, and so on. Also, the most advanced and latest ML/DL algorithms can be used for stock prediction, by feeding in lots of training data from the stock market.
*   **Telecom**: AI/ML-based algorithms can be used for call quality and to predict customer churn.
*   **Automation**: Many of the challenges in an interviewing system, track detection using robots based on AI/ML algorithms find their application in automation.
*   Similarly, healthcare, automotive, and retail industries are extensively using AI, ML, and DL-based algorithms for solving many challenging problems.
*   Applications like machine translation and signature verification needs advanced AI and ML-based algorithms.

As you peel the layers one-by-one, they open up. AI is the broader classification of all these mechanisms put together.

Since AI has a long history, it has seen something called “*AI winter*”, which is a downward trend in an AI application and development, during that period of time and after a certain number of years, it has again seen an upward trend. This is represented by a curve from the period 1950 onwards as shown in *figure 1.5*.

“*AI Winter cycle*” as it was called, is downward and then a sudden spike in AI development/research activities over a period of 10 years cycle has been observed. This cycle clearly indicates the various phases of research and developmental activities that were seen in AI, ML, and DL over a period of last 60-70 years of time:

![](images/Figure-1.5.jpg)

**Figure 1.5:** AI Winter Cycle

**Note:** There is a wafer-thin difference between the terminologies in Artificial Intelligence. The terms machine learning, deep learning, etc. share many things in common but differ fundamentally in the execution architecture.

Deep Learning is a subset of the broader family of machine learning methods. It was introduced with the objective of moving machine learning closer to its main goal—that of artificial intelligence. Similarly, representation learning or feature learning is the subset of the machine learning mechanism that deals with extracting features or understanding the representation of a provided dataset.

# [1.2 Machine learning](#toc.xhtml#s9a)

Machine Learning as explained earlier is a subset of Artificial Intelligence.

In 1959, *Arthur Samuel* defined Machine learning as, “*The field of study that gives computers the ability to learn without being explicitly programmed*.” This opened up lots of studies for a few years but later was stalled.

In recent times, ML is considered an integral part of data science, which can be used to build predictive models. In any machine learning mechanism or system, computers are taught to solve certain problems with massive datasets and are provided with models.

Machine learning is also defined as one of the branches of computer science in which algorithms (running inside computers) learn from data or datasets available to them. With this learning mechanism, the output of these various mechanisms will be used to build predictive models.

# [1.2.1 History and definition of ML](#toc.xhtml#s10a)

Historically, machine learning has been defined and developed by many industry experts. Various machine learning definitions/explanations by industry stalwarts are in the following tabular form:

 
| **Index** || **Defined by Whom** || **During when** || **Definition** |
| --- | --- | --- | --- |
| **1** || *Arthur Samuel* || 1959 || “ML is the field of study that gives computers the ability to learn without being explicitly programmed”. |
| **2** || *Tom Mitchell* || 1997 || “A Computer program is said to learn from experience E with respect to some task T and some performance measure P, if its performance on T, as measured by P, improves with experience E.” |
| **3** || *Drew Conway***Note: -** He created so-called **“Data Science Venn Diagram”.** || 2010 || Drew created a nice Venn Diagram during September 2010 and in which, his explanation, he says: *Machine Learning = Hacking + Math & Statistics* |
| **4** || General definition by developers’ community || 2014 || Machine Learning is the training of a model from data that generalizes a decision against a performance measure. |
| **5** || *Stephen Marsland* || 2009-10 || “Machine Learning, then, is about making computers modify or adapt their actions (whether these actions are making predictions, or controlling a robot) so that these actions get more accurate, where accuracy is measured by how well the chosen actions reflect the correct ones.” |
| **6** || *Aurélien Géron* **(author)** || 2014-17 || “Machine learning is the science (and art) of programming computers so they can learn from data,”. |

**Table 1.2**

# [1.2.2 Machine learning and its applications](#toc.xhtml#s11a)

Many times, machine learning is depicted as an intersection between math & statistics, hacking skills and substantive expertise. *Drew Conway* popularly depicted this with a venn diagram. This is known as “*The Data Science Venn Diagram*”.

The attached figure clearly shows how machine learning is intersected with various aspects. Therefore, it is challenging to put across a standard definition for machine learning. So, one can easily say that machine learning is an amalgamation of "*Hacking Skills*” and “*Math and Statistics*”. Data Science in a broader perspective, cuts across all the three aspects, “*Hacking Skills*”, " *Math and Statistics*" and “*Domain Expertise*”. So, there is a narrow difference between ML and DS. The following figure explains this beautifully:

![](images/Figure-1.6.jpg)

**Figure 1.6:** Data Science and Machine Learning Venn Diagram

*[Figure 1.6](#c01.xhtml#fig1_6)* is some sort of a venn diagram that shows how data science and machine learning is dependent on “*statistics*” and “*hacking skills*”.

One of the most common applications of the machine learning-based algorithm is used for spam email classification. Some of the commonly used terms in spam emails are used as labels to train the model to learn and classify the emails as “*spam*” and “*non-spam*” (sometimes called “*ham*”) emails. The common keywords used are for example, “*Subject lines with all capital letters*”, “*Loan approved*”, “*Won Lottery*”, etc. There is a huge dataset itself created using these commonly found *keywords* by *UC-Berkley*, which can be found in the following link.

*Ref:* ***[http://archive.ics.uci.edu/ml/datasets/spambase](http://archive.ics.uci.edu/ml/datasets/spambase)***

*Creators: Mark Hopkins, Erik Reeber, George Forman, Jaap Suermondt*

Using this dataset, the email engine can be trained (keyword-based learning), and all the emails that are received by an email address are first fed into this engine, which will classify them as “*Spam*” or “*Non-spam*”. If there is any new type of spam found, this can be fed into the dataset and this entire model can be re-trained.

Compared to traditional programming where only a “*set of predefined Rules*” are used, which are static and the rule engine works based on these set of instructions only. Whenever there is any change in the keyword, then changing the rules is cumbersome and challenging. It takes a lot of energy and maintaining this will be difficult.

In the case of machine learning models, only this dataset has to be updated and no need to change the rules unless there is a huge change that has been observed.

Similarly, machine learning methods or mechanisms are used for various applications in and across various industry domains. Some of the examples are as follows:

*   Speech recognition
*   Language translation
*   Financial services and applications 
    *   Trading algorithms
    *   Management of portfolios
    *   Fraud detection and alerting
*   Transport services and applications 
    *   Driverless vehicles
    *   Safety monitoring and alerting
    *   Air-traffic controlling
    *   Smart navigation systems
*   Healthcare 
    *   Discovery of new drugs
    *   Analysis and diagnosis of diseases
    *   Advanced robotic precision surgeries
*   E-commerce OR Retail shopping assistants
*   IoT 
    *   Prediction and correction of sensor behavior
    *   Prediction and correction of gateways and network servers
    *   Helps in building smart homes and smart cities
*   Social media 
    *   Sentiment analysis
    *   Fake news classification
    *   Anomaly detection

There is no limit to machine learning applications. They are found in every industry domain and sector. Based on the collaboration of both academia and industry, they are evolving day by day. It is pretty hard to find an area where their application is limited. In the last decade alone, ML models are being used across the industry.

# [1.2.3 Classification of ML algorithms](#toc.xhtml#s12a)

The machine learning systems (or **algorithms**) can be broadly classified into many categories, based on various factors and methods. The most popular of these are as follows:

*   Supervised learning
*   Unsupervised learning
*   Semi-supervised learning
*   Reinforcement learning
*   Online/batch learning

Each of these machine learning systems types is explained in detail in the upcoming chapters. But lighter definition and explanation is provided here to make sure that the reader has basic knowledge of them.

1.  **Supervised Learning**: These algorithms are typically trained by human “*supervision*”. That is the reason these are called “*supervised learning algorithms*”. Most of the training data that is used in supervised learning algorithms are “*labeled*” data. One can say that there is a “*teacher*” involved in training the model.
    
    “*Labeled data*” here means which have been tagged with one more name associated with it. For example, an image is labeled as it is a cat's photo and it's a dog's photo based on the character and features of that photo.
    
    This helps in later classifying and training the “*unlabeled data*” with further classification and categorization.
    
    Based on certain features, these labels are predicted/guessed. Once predicted, that sample group is labeled with that name. By continuously providing input, the output is generated, these outputs are nothing but “*labels*”. The training involved various types of datasets and model building. These will be explained in detail in later chapters.
    
    Some of the well-known and popularly used supervised learning algorithms are as follows:
    
    *   Regression (continuous target variables) 
        *   Linear Regression
        *   Logistic Regression
        *   Ensemble Methods
        *   Decision Trees and Random Forests
        *   Support Vector Regression (SVR)
        *   Gaussian Process Regression (GPR)
    *   Classification (categorical target variables) 
        *   Support Vector Machines (SVMs)
        *   Naïve Bayes
        *   K-nearest Neighbors (KNN)
    *   Common neural networks 
        *   Multi-Layer Perceptron (MLP)
2.  **Unsupervised Learning**: These algorithms as the name suggests are not supervised by humans. What this means is that the training data is “*unlabeled*”.
    
    In unsupervised learning, there is no teacher involved at all. What the system or computer learns is different patterns/structures in data. Based on these patterns the data can be grouped into with pattern as output category. Based on these patterns one can come across a set of rules, which can be later used in deriving meaningful insights. These algorithms also can be used for building descriptive modeling.
    
    These algorithms unlike supervised don’t predict or find anything specific to the data set.
    
    Some of the well-known and popularly used unsupervised learning algorithms are as follows:
    
    *   Clustering (continuous) and Dimensionality 
        *   K-means
        *   K-medoids
        *   Hierarchical Clustering Analysis (HCA)
        *   Expectation Maximization
        *   Hidden Markov Model
        *   Neural Networks
        *   PCA (Principal Component Analysis)
        *   SVD
        *   Kernel PCA
        *   t-Distributed Stochastic Neighbour Embedding (t-SNE)
        *   Locally Linear Embedding (LLE)
    *   Association Analysis (categorical) 
        *   Apriori
        *   Eclat
        *   FP-Growth
3.  **Semi-Supervised Learning**: Frankly speaking this is not a type of algorithm. But to categorize some of the algorithms which fall either as supervised algorithms OR unsupervised algorithms OR both, this mechanism is used. So, one can put it like this, either there are no labels for the observation in the data sets or labels are present only for certain observations.
    
    In some cases, where data labelling is a costly affair but needs a combination of both partial data labeling and partial non-labeling these algorithms can be used.
    
    Some of the well-known and popularly used unsupervised learning algorithms are as follows:
    
    *   Uclassify
    *   GATE
4.  **Reinforcement Learning**: This is nowadays one of the popular type algorithm learning mechanisms. Many complex models are being built using the combination of supervised learning or unsupervised learning along with reinforcement algorithms.
    
    This is a different category itself where so-called **agent** observes the environment, select and perform various actions and generate rewards or penalties accordingly.
    
    *   **Q-Learning**: Q-Learning is a model-free RL algorithm, "Q" in Q-Learning stands for quality, which is used to determine how useful a given action is in gaining some future reward.
    *   **Temporal Difference** (**TD**): TD is an approach to learning how to predict a quantity that may be dependent on future values of a given signal.
    *   **Deep Adversarial Networks**: Deep Adversarial Belief Networks also sometimes called DBN, are highly parallelizable numerical algorithms.
    *   **Markov decision process (MDP):** MDP works using the methodology involving agent, environment, state and action, each depending on the other.
    *   **Monte Carlo Tree Search**: this is a heuristic search algorithm used for decision-making processes.
    *   **Asynchronous Actor-Critic Agents** (**AAAC**): this algorithm is beneficial in experiments that involve some global network optimization with different environments in parallel for generalization purposes.

# [1.3 Deep Learning](#toc.xhtml#s13a)

Before jumping on to defining deep learning, let us first learn how the human brain works? How the central neuron system of humans is wired together with billions of neurons communicating with each other?

There is some analogy between the human neuron system and deep learning networks.

The human brain is made up of billions of nerve cells or neurons. These neurons have a great ability in transmitting electrochemical signals using “*synapse*” which is found as a connection between any two neuron cells. These are also sometimes thought of as similar to gates and wires in the computer world.

Each of our daily experiences, senses and various normal functions trigger a lot of neurons-based activity which is then converted to so-called reaction/communication channels.

The first-ever neuron (nerve cell) from the human brain was extracted and peering through the microscope "*Santiago Ramon y Cajal (1852-1934)*", he saw neurons — individual cells and he went to establish that the neurons communicate using what is well known as "*synapse*". He was awarded the Nobel Prize in 1906 in the field of physiology or medicine for this discovery.

Ref: - ***[https://www.nobelprize.org/prizes/medicine/1906/cajal/facts/](https://www.nobelprize.org/prizes/medicine/1906/cajal/facts/)***

Please refer to the figure as mentioned in the reference link which shows the first-ever drawings of neurons by *Santiago Ramon*. This picture is one of the greatest discoveries, as it has led medical science to a new path.

Ref: - ***[https://www.quantamagazine.org/why-the-first-drawings-of-neurons-were-defaced-20170928/](https://www.quantamagazine.org/why-the-first-drawings-of-neurons-were-defaced-20170928/)***

*Santiago Ramon* also extracted individual neurons from his experiments and he came out with the first-ever drawing of an individual neuron along with explaining functions of all subparts of this neuron cell. The figure as in the reference link is the first neuron cell extracted and drawn by him. This neuron cell consists of a cell body, nucleus, axon, and so on. They are explained in the more recent diagram.

Ref: - ***[https://www.brainfacts.org/brain-anatomy-and-function/cells-and-circuits/2018/santiago-ramon-y-cajal-the-first-modern-neuroscientist](https://www.brainfacts.org/brain-anatomy-and-function/cells-and-circuits/2018/santiago-ramon-y-cajal-the-first-modern-neuroscientist)***

This discovery broadly opened up many pieces of research for nearly a century on the human brain, cognitive abilities, human perception, human reaction to senses, human memory and types, human thinking, and so on.

For the last several years, the extensive research focus was on the human brain and its internal neural network. This research along with advancements in the computer industry has helped in the development of AI and ML technologies. Many researchers in both the computer industry and academia have a long dream of building intelligent machines similar to human brains. Hope this will be achieved one day.

*[Figure 1.7](#c01.xhtml#fig1_7)* explains the single neuron, how it looks, what are the various parts and functionalities are depicted as follows:

![](images/Figure-1.7.jpg)

**Figure 1.7:** Single Neuron Cell

In 1958, *Frank Rosenblatt* who is an American psychologist attempted to build “*a machine which senses, recognizes, remembers, and responds like the human mind*”. He went to call this machine a **Perceptron**.

During the same time around 1956, *Hubel* and *Wiesel* carried out what is popularly known experiment as the “*Cat Experiment*”. In this experiment, they recorded neuron readings of the visual cortex of a cat, based on bright object movement in front of its retina. This resulted in finding out that how complex information is extracted from the visual pathways by the movement of bright objects.

By seeing all these events, majorly there are “*six things that helped deep learning to prosper*”. The following listing and figure explain these turn of events clearly:

1.  **1906:** *Santiago Ramon* finding out how human neuron cell looks like
2.  **1950:** All Turing's popularly known “*Turing experiment*”
3.  **1961-1980:** *Geoffrey Hinton* & Team coming up with feedforward ANN using MLP, backpropagation and Boltzmann’s machine
4.  **1988-1996:** *Yann Lecun*, working on hand-written character identification and development of **Convolutional neural network** (**CNN**)
5.  **1996-2005:** *Yoshua Bengio* and team came up with probabilistic models of sequences, word embeddings, and generative adversarial networks, among others.
6.  **2010-2020:** Availability of data, compute (CPU) and GPU's and affordability
    
    ![](images/Figure-1.8.jpg)
    
    **Figure 1.8:** Six Things Helped DL to Prosper
    

*[Figure 1.8](#c01.xhtml#fig1_8)* clearly explains how these six events helped deep learning to prosper. Anyone new to the field of deep learning can easily make out, what led to the advancement and development of deep learning. Each of these events even though is independent but have occurred during a significant period.

# [1.3.1 What are the prerequisites to understand deep learning?](#toc.xhtml#s14a)

These days anyone can find several discussion forums and blogs on learning deep learning. But whether one has to know advanced mathematics (calculus) to understand deep learning? Or whether one has to be an expert in all machine learning concepts?

There are plenty of discussion forums and blogs nowadays on deep learning and its study. But it will always be a challenge in choosing the appropriate forum or content before start learning deep learning. It was assumed earlier only ML experts can learn deep learning; this was just an assumption. Now, anybody can jump-start learning deep learning from scratch.

But in our view, this should be evaluated on a case-to-case basis. Having said that, it is better to know the following if you want to understand deep learning directly without any prerequisites and serious about it:

*   The basic functions of neural networks
*   An understanding of the basics of advanced calculus
*   An understanding of matrices, vectors and linear algebra
*   Algorithms (supervised, unsupervised, gradient descent, online, batch, and so on)
*   Python/R programming
*   Case-to-case basis mathematical equations or formulae

The simulation of human brain-like activities is becoming more plausible nowadays.

The following is a simple artificial neural network. This has a simple architecture with few *inputs (x1, x2…Xn)*, *weights (w1, w2,…Wn)* which are fed to the function “*f*” and output “*y*” is the outcome of this. If you compare this simple ANN, it clearly shows some of the characters of the real neuron that is shown in *[figure 1.9](#c01.xhtml#fig1_9)*:

![](images/Figure-1.9.jpg)

**Figure 1.9:** Artificial Neural Network

Multiple factors have led to this development, the following are the prime factors:

*   Amount and large scale of data available to us to build large neural networks
*   Availability of higher compute power
*   Availability of GPU
*   Lesser cost of CPU and GPU and combination of both
*   Advancement of machine learning
*   Improvement of Performance

During 2009-10 ImageNet challenge became popular. Both industry experts and academia participated and contributed to these challenges.

The **ImageNet Large Scale Visual Recognition Challenge** (**ILSVRC**) is a body that evaluates algorithms for object detection and image classification at a large scale.

One high-level motivation is to allow researchers to compare progress in detection across a wider variety of objects (this is done by taking advantage of the quite expensive labeling effort). Another motivation is to measure the progress of computer vision for large scale image indexing for retrieval and annotation. Various challenges of these are as follows:

Ref: ***[http://www.image-net.org/challenges/LSVRC/](http://www.image-net.org/challenges/LSVRC/)***

*   ILSVRC 2017
*   ILSVRC 2016
*   ILSVRC 2015
*   ILSVRC 2014
*   ILSVRC 2013
*   ILSVRC 2012
*   ILSVRC 2011
*   ILSVRC 2010

The outcome of these challenges is various image-based deep learning architectures. Also, ImageNet (Ref: ***[https://www.image-net.org](https://www.image-net.org)***) is one such body where it maintains a huge image database. This contains approximately 22K categories and 14 million images. These images range around animals, plants, structures, and so on, including various subcategories.

Many deep learning architectures are built using fully connected layers.

A fully connected network transforms a list of inputs into a list of outputs (which is also called as predicted outputs).

Following are many deep learning mechanisms:

*   **Convolutional neural network** (**CNN**) layer
*   **Recurrent neural networks** (**RNN**) layers
*   **Long Short-Term Memory** (**LSTM**) cells
*   **Gated Recurrent Unit** (**GRU**)
*   **Deep Belief Network** (**DBN**)
*   **Deep Stacking Network** (**DSN**)
*   Auto Encoders

Following are many deep learning architectures:

*   LeNet
*   ImageNet
*   AlexNet
*   ResNet
*   Google-NMT (Neural Machine Translation)
*   Self-organized maps
*   **Restricted Boltzmann Machines** (**RBM**)
*   Network in network
*   SqueezeNet
*   GoogleNet and Inception

Deep learning frameworks:

*   Caffe
*   TensorFlow
*   Keras
*   Torch
*   MxNet
*   PyTorch
*   Glon
*   DL4J
*   Chainer

A lot of advancements in deep learning was seen off late. For example, the development of a very robust and advanced algorithm known as “*Deep Mind*” by *Demis Hassabis*, during 2014-15 (later this company was acquired by Google), which developed a very complex game “*AlphaGo*”, which has beaten the human champion by continuous learning. In this algorithm, ideas like “*deep value network*” and “*deep policy network*” were used to solve and beat humans.

Very recently in **General Adversarial Networks** (**GAN’s**), which are deep networks have seen a lot of newer algorithms are getting added. The ideas used are called “*discriminators*” and “*generators*” inside GAN’s.

# [1.3.2 Difference between machine learning and deep learning](#toc.xhtml#s15a)

The following table clearly explains what is the major difference between machine learning and deep learning:

 
| **Index** || **Machine Learning** || **Deep Learning** |
| --- | --- | --- |
| **1** || These models can learn using lesser data || Needs larger data sets. |
| **2** || Generally training is done using CPU || Training is done either using CPU or GPU, or both. |
| **3** || Hyperparameter tuning is limited || Hyperparameter tuning can be done in multiple ways. |
| **4** || Takes lesser time to train || Generally, takes more time to train as bigger networks and data sets are used for training. |
| **5** || Lesser accurate || More and high accuracy rate. |

**Table 1.3**

# [1.3.3 Applications of deep learning](#toc.xhtml#s16a)

Deep learning finds its way in many of the real-time industry applications and day-to-day activities that we come across. Deep learning uses large datasets, which are available now which makes building DL modeling easier. Deep learning models are used where it is difficult to identify the features manually.

Following are some of the well-known deep learning applications:

*   Autonomous cars
*   X-RAY classification in healthcare (CNN)
*   Advanced facial recognition (CNN)
*   Share market (ML)
*   Visual QA (Question & Answer) (CNN/ML)
*   Advanced voice and voice-assisted tools and devices (RNN, LSTM, Language Translation)
*   Automatic machine translation (RNN, LSTM)
*   Image recognition, image captioning (CNN, RNN)
*   Anomaly detection and classification (ML, DL algorithms)
*   Predicting earthquakes (Advanced DL, ML)
*   Financial market analysis
*   Automatic game playing
*   Language translations (NLP, RNN)
*   Pixel restoration (CNN, GAN)
*   Photo descriptions (CNN, GAN)
*   Demographic and election predictions

# [1.4 Tools and frameworks for AI, ML and DL](#toc.xhtml#s17a)

As discussed in previous sections AI, ML and DL are interconnected, one is a subset of the other or they overlap each other. With more awareness of these technologies and an enormous amount of data being available, the world started huge development in these areas to accomplish tasks using AI, ML, and DL as indicated in previous sections. To support this development, several tools and frameworks were built by various communities allowing advancement in these technologies. There are various tools and frameworks to support developers, data scientists, and non-programmers, to support different platforms like cloud, desktop, edge devices, and mobile to support interaction between multiple frameworks. A few of them are listed as follows:

Some tools can be used by managers and non-technical people with no programming knowledge.

*   **DataRobot** is an automated machine learning platform, provides model optimization, parallel processing, and model deployment.
*   **Tableau** and **Datawrapper** are popular visualization tools that allow the creation of charts, maps, and graphs with minimum effort by using clicks.
*   **Rapid Miner** is the best data mining tool that allows data preparation, data validation, modeling, and deployment. It supports team collaboration, eases project management, and model deployment.
*   **BigML** is a machine learning platform that allows classification, clustering, regression, and ensembles.

There are a lot of open-source tools and frameworks that will be used by researchers and many enterprises to develop AI, ML, and DL based applications.

*   **Caffe** (Convolutional Architecture for Fast Feature Embedding) developed by Berkeley AI Research is an open-source deep learning framework. It is written in C++ programming and provides a Python interface.
*   **Deeplearning4j** is developed for Java Virtual Machine, is an open-source deep learning framework developed under Apace License 2.0 by a group of researchers in AI-based out of Tokyo and San Francisco.
*   **H2O** is a deep learning framework designed by H2O.ai that is used to work with data and draw data insights.
*   **OpenNN** written in C++ programming language is a library used mainly for machine learning research.
*   **TensorFlow** developed by researchers and engineers of Google is a deep learning framework that is available in many programming languages C++, Java and Python.
*   **Keras** developed by Francois Chollet in 2015 is a high-level interface for deep learning framework.
*   **Apple’s CoreML** is an open-source framework for use on Apple systems and devices. It allows integration of the machine learning models into iOS, Apple TV, Mac OS, Apple Watch applications.
*   **Distributed Machine Learning Toolkit** by Microsoft is a deep learning framework useful for implementing machine learning tasks, natural language processing and perform distributed implementation.
*   **MLlib** developed by Apache Spark works on platforms like Kubernetes, Hadoop or Cloud, uses multiple languages Python, R, Java and Scala.
*   **PyTorch** is a popular open-source deep learning framework that supports data parallelism, flexibility and contains many pre-trained models.

There are a few frameworks and tools which are useful for specific applications.

*   **ONNX** was developed from the collaboration of Microsoft and Facebook which allows working on models on different frameworks. It allows models to be trained in one framework and to be transferred to another for inference.
*   **MXNet** and **Gluon** are deep learning frameworks that support multiple languages like,
*   C++
*   Perl
*   R
*   Python
*   Scala
*   Javascript
*   Go
*   Julia

They can be used with the AWS cloud platform.

The following are some deep learning frameworks mainly developed to work on mobile, embedded, and edge devices.

*   **Caffe2** (Andriod)
*   **CoreML** (Apple’s iOS)
*   **DeepLearningKit** (Apple’s iOS)
*   **Mobile AI Compute Engine** (Andriod, Apple’s iOS)
*   **PyTorch Mobile** (Android, Apple’s iOS)
*   **TensorFlow Lite** (Andriod, Apple’s iOS)
*   **Oryx2** is used to perform machine learning tasks on a real-time basis. It is built on Apache Kafka and Apache Spark.
*   **Accord.Net** is a .net based machine learning framework written in C#.
*   **Amazon Machine learning** integrates data from multiple sources like RDS, S3 or Redshift. In AWS, there is a service called "Sage Maker" (Amazon SageMaker is a cloud machine-learning platform), which helps in building various ML application models.
*   **Google Cloud ML Engine** is a deep learning cloud hosted platform for building machine learning and deep learning models.

**Note:** A single tool or framework may not provide all the benefits required for a purpose, it can be selected based on flexibility, open-source support, speed, platform support, language support, device support and environment support.

# [1.5 Languages used for AI, ML, and DL](#toc.xhtml#s18a)

The previous section listed various tools and frameworks which are contributed by different companies and research communities. They have been written in various languages, the language selection is based on project, environment, platform, purpose, and flexibility. Development in AI, ML, and DL can be performed using multiple languages. The programming languages for Artificial Intelligence as listed in public domains are:

**List of programming languages**

*   IPL
*   Lisp
*   Smalltak
*   Prolog
*   STRIPS
*   Planner
*   POP-1
*   R
*   Perl
*   Haskell
*   Wolfram
*   C++
*   MATLAB
*   Python
*   Julia

Few additions include *Java, JavaScript, Scala, Typescript, Shell, C#,* and *C*. Each language would have some benefits enabling the data scientist and developers to use that language based on the project requirements. Discussing all the reasons behind the selection of the language would be cumbersome and hence, below are given few most popular languages used for AI, ML, and DL development.

*Python, Java, C++, Prolog, Lisp,* and *R* are the most popular machine learning languages used, followed by other languages. Python was developed by *Guido van Rossum* and released in 1991. It is a powerful language with large community support and has an enormous set of libraries and allows flexibility in usage. It provides platform independence and has extensive frameworks for deep learning and machine learning. Java was developed by *James Gosling* at *Sun Micro Systems* and released in 1995. Java is a popular and fastest-growing programming language. Java is secure, object-oriented and platform-independent and with write once, run anywhere support and is extensively used in AI development. R was first created by *Robert Gentlemen* and *Ross Ihaka* and released in 1995. It is the implementation of S programming language and is used for statistical computing, analysis, visualizations, predictive analysis. C++ is the fastest programming language, developed by *Bjarne Stroustrup* in 1983. It is generally used for time-critical AI projects, has lots of machine learning algorithms, statistical techniques and gives high performance and efficiency. Prolog was developed in 1972 by *Alain Colmerauer* with *Phillippe Roussel* in Marseille, France. It is one of the oldest programming languages which is a rule-based and declarative language. It is suitable for programming AI, supports pattern matching, tree-based data structuring, automatic backtracking, and works best for creating chatbots. Lisp was developed in 1958 by *John McCarthy* at the **Massachusetts Institute of Technology** (**MIT**). It is also one of the oldest programming languages and is a family of computer programming languages. It supports fast prototyping, dynamic object creation, suitable for inductive logic projects, machine learning, symbolic AI. It has a unique macro system that creates a domain-specific level of abstraction.

# [1.6 Sample datasets for AI, ML, and DL development](#toc.xhtml#s19a)

Earlier it was difficult to find datasets for AI projects since everyone was worried about sharing the data because it may be used for the wrong purpose. In recent years, lots of communities and organizations have made datasets available online which is free is used by anyone. Datasets play a key role in AI, ML and DL projects. As lots of datasets are available now, finding the right dataset is a difficult task. You can look for a dataset using a dataset finder. **Kaggle** which started in 2010 is a subsidiary of Google LLC is one of the popular dataset locations, with each dataset having a small community to discuss the specifics of data and code if available. A search box with options to search on size, file types, licenses, tags, last update will make it easy to find required datasets. **UCI machine learning repository**, created by the University of California, School of Information and Computer Science. It is one of the oldest sources of datasets available online and has some interesting datasets. **Kdnuggets** was started as a newsletter in 1993 by *Gregory Piatetsky-Shapiro*. It is a trusted site in business and scientific communities. It has datasets from government agencies, exchanges, and research centres. **Google Datasets** was created in 2018 to bring around 25 million datasets with a toolbox to search the datasets by name and find links to where the data is located. Microsoft Datasets created by Microsoft and the external research community has lots of curated datasets that can be used for research studies. **VisualData** contains datasets for building computer vision models and allows to search datasets by category. You can search by using computer vision-related model patterns like segmentation, image captioning, image generation, object detection, face recognition, and so on.

**Note:** Depending on the AI, ML and DL framework and project, any suitable language can be selected. If you are a novice and want to get started with AI, ML and DL, picking Python frameworks would be a good choice because of ease of learning and flexibility.

The datasets selected should be clean and they should have huge amounts of data and relevant data. **ImageNet** is one of the popular datasets for image processing, it has around 1 million images with around 1000 images for each class of images. **Breast Cancer Wisconsin (Diagnostic) Dataset** is a breast cancer diagnostic dataset that can be used for classifier models. It contains digitized images of a fine needle aspirate of a breast mass. **Twitter Sentiment Analysis Dataset**, is a popular dataset for natural language processing models. **MNIST Dataset** is the best dataset for binary images of handwritten digits with around 70,000 images. **Spam SMS Classifier Dataset** which is a dataset of around 5000 SMS can be used for spam detection, spam classification, and spam analysis. **YouTube Dataset**, provided by Google has around 8M classified YouTube videos and its IDs. This can be used for video classification and analysis. **Boston Housing Price Dataset** has around 506 cases with 14 attributes in each case based on Boston real estate and ideal for the regression problem. **Pima Indians Diabetics Dataset** contains details of diabetics of female patients who are at least 21 years old. It has around 768 data points with several medical predictor variables like a number of pregnancies, BMI, insulin level and age. **MS-COCO Dataset**, has 330K images, 80 object categories, 5 captions per image, with around 25GB of data. It can be used for building image captioning, objection detection and segmentation models. **VisualQA Dataset** has around 265K images, 3 questions per image, 10 ground-truth answers per image. This can be used for building visual Q & A models to answer open-ended questions about images. **Fashion-MNIST Dataset** has around 70K images with 10 classes which can be used similar to MNIST for building fashion-related models. I**MDB Reviews Dataset** has around 50K highly polar movie reviews which can be used for sentiment classification and analysis. **The Wikipedia Corpus Dataset** has around 0.4 M articles with 1.9 million words which is a huge dataset that can be used for natural language processing related problems. **Free Music Archive (FMA)** has around 100K tracks and **Million Song Dataset** has around a million songs that are good datasets for building audio analysis models.

Following are various links for the above datasets:

*   **[https://www.kaggle.com/datasets](https://www.kaggle.com/datasets)**
*   **[http://yann.lecun.com/exdb/mnist/](http://yann.lecun.com/exdb/mnist/)**
*   **[https://archive.ics.uci.edu/ml/datasets.php](https://archive.ics.uci.edu/ml/datasets.php)**
*   **[https://www.kdnuggets.com/datasets/index.html](https://www.kdnuggets.com/datasets/index.html)**
*   **[https://datasetsearch.research.google.com/](https://datasetsearch.research.google.com/)**
*   **[https://www.kaggle.com/uciml/breast-cancer-wisconsin-data](https://www.kaggle.com/uciml/breast-cancer-wisconsin-data)**
*   **[https://www.kaggle.com/kazanova/sentiment140](https://www.kaggle.com/kazanova/sentiment140)**
*   **[https://www.kaggle.com/uciml/sms-spam-collection-dataset](https://www.kaggle.com/uciml/sms-spam-collection-dataset)**
*   **[https://www.kaggle.com/datasnaek/youtube-new](https://www.kaggle.com/datasnaek/youtube-new)**
*   **[https://www.kaggle.com/kumargh/pimaindiansdiabetescsv](https://www.kaggle.com/kumargh/pimaindiansdiabetescsv)**
*   **[https://visualqa.org/](https://visualqa.org/)**

**Note:** There is a flood of datasets available for use by the public, the relevant dataset should be chosen after analysis so that a good model can be built with high accuracy and valid data.

# [Conclusion](#toc.xhtml#s20a)

Artificial intelligence spans various emerging technologies and applications. The advancements in hardware platforms, research in numerous algorithms, and availability of portable programming languages have accelerated the proliferation of the technologies into the solutions of every domain of the business. Machine learning finds its applications in various fields as explained earlier. Many of the algorithms in ML work with smaller datasets. This is an advantage as well as a disadvantage based on the context and situation where we apply ML techniques.

DL finds its applications where larger datasets are used and also when we don’t have any clue about the features, then also DL techniques can be used. Many of the complex real-world problems can be solved by using DL methods and algorithms. The tools and frameworks allow to build and use AI, ML and DL applications. The availability of various datasets enables us to explore, experiment, and research in AI, ML, and DL technologies. This is all we studied in this chapter. In the next chapter, we will be learning about the topics of ML models, applications, and algorithms in detail.

# [Points to remember](#toc.xhtml#s21a)

*   AI evolved from the early 1950s
*   AI has something known as AI winter which is a downturn
*   Machine learning is used in all most all industry sectors and domains
*   Machine learning picked up very well in the last decade
*   Many advanced algorithms were developed in machine learning
*   Deep learning is one of the fast-evolving technologies
*   Deep learning is fascinating to learn
*   Deep learning techniques helped in recent years to solve complex problems.
*   Deep learning has found its applications in the medical field, facial recognition, and image recognition
*   Most of the R & D is happening in deep learning nowadays

# [Questions](#toc.xhtml#s22a)

1.  What is artificial intelligence? What is its significance?
2.  What is machine learning?
3.  By whom and how machine learning has been defined in various ways?
4.  What are the various applications of machine learning?
5.  List the industry domains and sectors where machine learning can be used/applied?
6.  What are the algorithms in machine learning?
7.  What is labeled data?
8.  What are the categories of machine learning algorithms?
9.  What are the six things that lead to the development of deep learning?
10.  What are the most recent developments in deep learning?
11.  What are the various popular architectures in deep learning?
12.  Who are the pioneers of deep learning development? Name those three persons?
13.  How does the term deep learning differ from machine learning?
14.  Which tools or frameworks are generally used for research work?
15.  Name the tools or frameworks which can be used for mobile devices?
16.  How are tools, frameworks, and languages related in terms of AI, ML, and DL development?
17.  List five most popular dataset finder and public datasets?

# [Multiple choice questions](#toc.xhtml#s23a)

1.  **Choose the correct Answer** 
    1.  AI is a part of machine learning
    2.  Machine learning is a part of AI
    3.  Goal of AI is to replace human beings
    4.  AI is the study of self-replicating machines
2.  **Choose the correct answer** 
    1.  Deep Learning is a subset of AI
    2.  Deep Learning is a subset of ML
    3.  Deep Learning is not a subset of ML
    4.  None of the above
3.  **Choose the correct answer** 
    1.  TensorFlow and Keras are frameworks of Deep Learning
    2.  PyTorch and Keras are not the frameworks of Deep Learning
    3.  Many tools and Python libraries are used as DL frameworks
    4.  None of the above
4.  **Choose the correct answer** 
    1.  Deep Learning and Machine learning both need CPU/GPU
    2.  Deep Learning only needs both CPU/GPU
    3.  ML needs only GPU
    4.  None of the above
5.  **Choose the correct answer** 
    1.  Perceptron was developed by Hinton
    2.  Perceptron was developed by Yann Lecun
    3.  Yann Lecun devised is a mechanism for reading first handwritten digits
    4.  Hinton devised NLP
6.  **Choose the correct answer** 
    1.  TensorFlow is developed by Microsoft
    2.  Keras is an open-source deep learning framework
    3.  All tools and frameworks provide the same benefits
    4.  PyTorch is the only popular deep learning framework
7.  **Choose the correct answer** 
    1.  Kaggle and Kdnuggets have websites for online competitions.
    2.  MS-COCO dataset is best suitable for natural language processing applications
    3.  Visual Data is a dataset that can be used for building visual Q&A models
    4.  The Wikipedia Corpus Dataset is best suitable for natural language processing applications.
8.  **Choose the correct answer** 
    1.  C and C++ are used for time-critical AI applications
    2.  Python is best suitable for building chatbots
    3.  Prolog and Lisp are scripting languages
    4.  There is no .NET-based machine learning frameworks

# [Answers](#toc.xhtml#s24a)

1.  **b**
2.  **b**
3.  **a**
4.  **a**
5.  **c**
6.  **b**
7.  **d**
8.  **a**

# [CHAPTER 2](#toc.xhtml#c02)

# [Supervised Machine Learning](#toc.xhtml#c02)

As indicated in the previous section, machine learning is defined as one of the branches of computer science in which algorithms learn from the data or data sets available to them. With this learning mechanism, the output of these mechanisms will be predictive models. Among many learning mechanisms that exist in machine learning, this chapter focuses on what is supervised machine learning, the data preparation, cleanup, and a few learning mechanisms of supervised machine learning. It later delves into the specifics of classification, regression, optimization, and loss methods in supervised learning. It then moves on with the discussion on the performance of learning mechanisms and closes by giving a few examples or use cases of supervised machine learning in the practical and industry areas.

The three main things that need to be considered while adopting supervised machine learning is collecting data, labeling data, and predicting data. Supervised learning helps organizations to understand the unwanted outcomes and how to avoid them. In case of expected outcomes, it can work on adopting techniques to improve them. Industries can use supervised machine learning for applications like allocating human resources, forecasting sales, and detecting fraud. Supervised machine learning models have to be built with new input data changes to make sure they make proper predictions for the current changed input data.

# [Structure](#toc.xhtml#s25a)

In this chapter, the following topics will be discussed:

*   Introduction to supervised machine learning
*   Data preparation
*   Data cleanup
*   Classification and regression
*   Architecture and realization 
    *   Linear regression
    *   Support vector machine (SVM)
    *   Decision trees
    *   Random forest
*   Optimization and loss methods
*   Performance of methods
*   Examples or use cases

# [Objectives](#toc.xhtml#s26a)

After studying this chapter, one should be able to:

*   Understand the mechanism of supervised machine learning.
*   Data preparation and cleanup steps used for data sets.
*   Details of classification and regression.
*   Understand few learning mechanisms in supervised machine learning.
*   Optimization and loss methods.
*   Performance of the learning mechanisms.
*   Examples or use cases of using supervised machine learning.

# [2.1 Introduction to Supervised Machine Learning](#toc.xhtml#s27a)

Supervised machine learning is a type of machine learning where the raw input and its corresponding results are known for the learning mechanism. That means you have the input variables (x) and an output variable (y) and use a learning mechanism to infer a function f. Ideally, the learning algorithm is used to learn the mapping function from the given input (x) and output (y).

*y = f(x)*

With this mapping function inferred from the given input and output using the learning mechanism, this function can now be used to map a new set of examples. The function will be deemed optimal when it will correctly determine the output (y) for unseen instances (x). It is called **supervised learning** because the method of learning during the process of inferring the mapping function is similar to an expert or teacher supervising the teaching or learning process. The algorithm knows the correct answers and hence, it makes predictions on the input and if found incorrect, it will be corrected by the teacher or expert. The procedure or learning can be stopped when the expected level of performance is reached.

Many of the learning algorithms in machine learning requires the data to be in some format. Hence, the data set available has to go through some cleanup and preparation steps before it can be used for learning algorithms. The topics of data cleanup and data preparation will be discussed in later chapters.

There are many supervised learning techniques or methods that are generally used and all of them use the learning mechanism indicated previously. To get a better understanding of the learning process, few learning algorithms will be detailed out in the ‘*Architecture and Realization*’ section.

Supervised machine learning is further divided into two types based on the type of output variable. If the output variable is real-valued then such problems are categorized as regression problems. If the output variable is categorical then such problems are categorized as classification problems. Each of these types of learning will be discussed in detail in the further section of this chapter.

As a part of the learning process, once the mechanism is capable of predicting the unseen instances with correct labels or output variables the learning process will be stopped. This will be the optimal solution and in general, the loss functions will be used to achieve this. Section 2.7 will give more details on this. The performance of any learning mechanism needs to be measured to make it the right selection for a problem under consideration. The performance metrics used for measuring the learning mechanism will be discussed in the ‘*Performance Statistics*’ section.

As of today, supervised machine learning is being used in almost all the industry domains – retail, energy, banking, finance, insurance, securities, e-commerce, manufacturing, oil and gas, and education. In the section ‘*Examples and Use Cases*’, few examples or use cases will be discussed to get insights on how supervised learning is applicable for a scenario under consideration.

Advantages of supervised learning:

*   The number of classes for the learning can be decided.
*   The learning method is simple to understand.
*   The training data after the training can be removed and only the decision boundaries can be retained.
*   The learning mechanism can be made to learn perfect decision boundaries based on the number of examples used for training.
*   It helps to solve various real-world problems like fraud detection, image classification, and medical image classification for diseases.

Disadvantages of supervised learning:

*   The algorithm may over-fit easily with more examples.
*   If training samples have unwanted data, it will affect the accuracy.
*   Lots of time is required for computations during training.
*   Lots of data, data cleaning, and data preparations is required.
*   The learning does not give new information from the training data.
*   The training data should have good examples to get good accuracy.
*   Often leads to biased models.

# [2.2 Data Cleanup](#toc.xhtml#s28a)

The available data cannot be used directly for the learning mechanisms. It has to be verified for correctness, missing data, the existence of outliers, the correctness of format, amount of data, sparsity, duplicates, and bias in data. This section talks more about data cleaning and the next section details out data preparation.

Data cleaning includes the following activities:

*   Missing values handling
*   Handling of outliers
*   Checking sparsity of data
*   Removing duplicates
*   Handling inconsistent or non-standardized values

Many times, there may be records or instances of data that will have empty data or missing values for a few fields or attributes of input. If there is enough amount of data for training, then the records with these missing values are excluded and only those records that are not missing any values can be considered for training. Domain or subject matter expert needs to be consulted in case there is not enough data and if records with missing values need to be retained. Alternatively, missing values can be filled using the mean, median, and mode of respective attribute values. A label name such as missing or unknown can be filled in case of categorical attribute values. If missing values are deemed to be important for learning mechanisms, then complex solutions like stochastic regression imputation, multiply-stochastic regression imputation, regression imputation, **K-Nearest Neighbors** (**KNN**), or **Multivariate Imputation by Chained Equation** (**MICE**) can be used to replace them with appropriate values. The book “*Applied Missing Data Analysis with SPSS and ‘R’ Studio*” by *Martijn W Heymans* and *Iris Eekhout* provides details on these methods.

Outliers mostly will be erroneous to the learning mechanism, so in general, they need to be replaced or removed. Sometimes the techniques to replace the missing data can be used to replace outliers, for example, replace them with mean, median, or mode of the attribute values. Alternatively, techniques like replacing with maximum and minimum percentiles (Winsorizing OR Winsorization) is the transformation of statistics by limiting extreme values in the statistical data to reduce the effect of possibly spurious outliers, dividing the real values into discrete groups (binning) can be used. There are univariate, multivariate, and Minkowski methods (refer to ***[https://www.neuraldesigner.com/blog/3\_methods\_to\_deal\_with\_outliers](https://www.neuraldesigner.com/blog/3_methods_to_deal_with_outliers)***) that can be applied. The outliers can also be removed using Z-score and IQR score calculations.

For categorical data, the number of distinct categories plays a key role in machine learning. The data can have either a high frequency of categories or a low frequency. If the number of categories is high then the number of dimensions also increases which would pose a problem for the learning mechanism. To cater for problems like this, techniques like grouping similar values of two or more categories, taking advice from subject matter experts can be applicable. Alternatively, for typos, uppercase or lowercase inconsistencies fuzzy, or pattern matching tools can be used.

Duplicate data can appear in the data. The duplication can appear in the attributes or across the attributes. Proper care should be taken to judge if the data is duplicate or not. An attribute value can be duplicate but its corresponding values across other attributes may be distinct. And some machine learning algorithms may perform better with duplicate values. So, it is always better to experiment with the data with the learning mechanism with and without the duplicates. Or try augmenting the data set with the selected set of duplicates and experiment with the learning mechanism. Based on the performance difference with and without the duplicates, the decision can arrive. If the subject matter expert is available, then they can be removed or retained based on his/her advice.

Data can have inconsistent or non-standardized values due to multiple reasons. Suppose the data is collected from multiple sources that follow different standards of representation then the data with the same meaning would appear different and may not be trained correctly. The data has to be parsed and the inconsistencies have to be removed by correctly standardizing it.

# [2.3 Data preparation](#toc.xhtml#s29a)

Once the data is cleaned, it needs to be prepared for learning mechanisms using suitable data operations and techniques. The data may not be formatted, sampled, scaled, and encoded correctly. There may be bias in data, skewed data, and the data may require aggregation or integration with other data. All these activities come under the umbrella of data preparation for the learning mechanism.

The activities are listed as follows:

*   Data integration
*   Data transformation
*   Data formatting
*   Data reduction

Many times, the data from a single source may not be sufficient for the learning mechanism due to the smaller number of instances. During those scenarios, the data from multiple sources can be integrated or combined to form a collection that provides a sufficient number of instances for the learning mechanism. In few cases, the features appear less relevant when taken independently but if they are aggregated or combined with two or more features, they give more meaning and help the learning mechanism to improve performance. This is called data integration or aggregation. On the contrary, sometimes the feature has to be split into two or more independent features to improve performance which is called **data decomposition**.

The data used for the learning mechanism would have numerical values with very low and high values for a given attribute. In those cases, the learning mechanism may give different weightage for high and low values appearing for the same attribute. In some cases, the attribute though represents a common entity (example money), their numerical values may represent different currency values (for example, Dollar, Rupees, and Pound) which may result in wrong predictions by the learning mechanism. These kinds of problems in data need to be corrected using data transformation techniques. Scaling can be used to transform the data into a particular range that is the values are set to a common scale for a given attribute. Methods like normalization and z-score standardization can be used for this purpose. If bias is detected in the data, then the following techniques can be used for bias mitigation:

*   **Pre-processing Algorithms**: Reweighing, Optimized Pre-processing, Learning Fair Representations, and Disparate Impact Remover
*   **In-processing Algorithms**: Adversarial Debiasing and Prejudice Remover
*   **Post-processing Algorithms**: Equalized Odds Pre-processing, Calibrated Equalized Odds Pre-processing and Reject Option Classification

If there is skewed data, then a better symmetric data distribution for square root, cube roots, logarithms, reciprocals, and box-cox transformations can be used.

The data for the learning mechanism should be of a suitable format for processing. The required format depends on the mechanism used and the data need to be formatted accordingly to consider it for processing. The database file format, date format, structured or unstructured format, type of database, text file format, image file format, nested file format, array-based format, hierarchical data format, model file format, and compression format are some of the formats of data attributes which has to be transformed to the required format during data preparation.

The data will have features, but selecting the right features is crucial for any learning mechanism. Sometimes a few features have to be dropped or removed which are identified to contribute less information for improving the performance. Features can be selected by working with the subject matter expert or gaining more knowledge on data. Alternatively, feature extraction techniques can be applied to reduce the number of features which is also called feature reduction. There are many techniques available - **Principal Component Analysis** (**PCA**), Random Forest, Backward Feature Elimination, Factor Analysis, **t-Distributed Stochastic Neighbor Embedding** (**t-SNE**), and Independent Component Analysis.

Data cleanup and data preparation are the pre-processing steps that are carried out before the data is processed by the learning algorithms. In addition to the preceding steps, there may be specific or special purpose processing of data that may have to be done before data is handed over to training. Understanding the data with descriptive statistics and understanding the data with data visualizations are two key activities that are a part of the pre-processing steps most of the time. Using descriptive statistics, the following are the ways how to analyze the data.

Looking at the raw data to understand the problem:

*   Understand the size of the data.
*   Check if there are any missing data.
*   Understand the type of the data.
*   Summarize the descriptive statistics of data to get the insights of data.
*   Understand the relations between the attributes with correlation.

**Note:** The data cleaning and data preparation are the pre-processing steps that are performed before the learning method is applied to the data set. Depending on the type and distribution of data set, one has to carefully use the appropriate pre-processing steps.

# [2.4 Classification and regression](#toc.xhtml#s30a)

There are two types of supervised learning algorithms, regression and classification as given in *[figure 2.1](#c02.xhtml#fig2_1)*. The figure also gives the list of algorithms for each type:

![](images/Figure-2.1.jpg)

**Figure 2.1:** Types of Supervised Learning Algorithms

Regression is used for predicting continuous variables and when there is a relationship between the input and output variable. For example, predicting the cost of a house based on many parameters and weather forecasting. The algorithms which belong to this category are listed as follows:

*   Linear regression
*   Regression trees
*   Polynomial regression
*   Bayesian linear regression
*   Non-linear regression

Classification is used for predicting the output variables which are discrete or categorical and which can be classified into two (binary) or more classes (multiple). So, classification learns from the labeled data set and maps the input to one of the classes in the output. The list of algorithms that belong to this category is given as follows. For example, predicting if the image belongs to dogs or cats and sun or moon:

*   Logistic regression
*   Decision trees
*   Support vector machines (SVM)
*   Random forest
*   Naive Bayes Classifier

Among the mentioned algorithms, a few of them will be discussed in the next section detailing the architecture and implementation of the algorithm.

# [2.5 Architecture and realization of algorithms](#toc.xhtml#s31a)

In this section, the details of the linear regression, support vector machines, decision trees, and random forest algorithms will be discussed with respect to the architecture and implementation.

# [2.5.1 Linear Regression](#toc.xhtml#s32a)

Regression analysis is a type of predictive modeling technique that analyzes the relationship between the independent and dependent variables. The independent variables are called the **predictors** and the dependent variables are called **targets**. The techniques allow one to find relationships between the dependent and independent variables and the impact of the single or multiple independent variables on dependent variables.

**Linear Regression**: It is a predictive modeling technique that determines the relationship between the independent variable (y) and single or multiple dependent variables (X) using a best fit straight line (also called regression line). The variables can be continuous or discrete. It is represented by the following equation:

*Y = aX + b + e*

Here, *a* is the slope of the line, *b* is the intercept, and *e* is the error term. This is the equation of the straight line which can be used to determine the best fit line or regression line which allows predicting the dependent variable values (Y) based on the independent variable values (X).

The following table gives the types of linear regression:

 
| **Type** || **Description** |
| --- | --- |
| Simple linear regression || To predict one independent variable given one dependent variable. |
| Multiple linear regression || To predict one independent variable given two or more dependent variables. |
| Logistic regression || To predict one independent variable (discrete values) given two or more dependent variables. |
| Ordinal regression || To predict one independent variable (ordinal values) given one or more dependent variables. |
| Multinomial regression || To predict one independent variable (nominal values) given one or more dependent variables. |

**Table 2.1:** Table of Regression Types

Let us now get into the details of the simple linear regression. Consider the data set of points (x, y) whose scatter plot is given in *[figure 2.2](#c02.xhtml#fig2_2)*. The figure shows the plot in which the y variable is the dependent variable and the x variable is the independent variable:

![](images/Figure-2.2.jpg)

**Figure 2.2:** Data set points for simple linear regression

As it can be observed, there seems to be a linear relationship between x and y from the plot. A straight line probably from the origin to the top which is diagonal to the x and y axis would describe the relationship between the x and y variables. This analogy gives a good indication that this data set is suitable for linear regression. Hence, the data can be modeled using the equation of the linear regression given earlier:

*Y = aX + b + e*

This is the equation of the line and ‘a’ and ‘b’ are the coefficients which make the line move around. The ‘b’ gives the values where the line intercepts the y-axis for a given value of x and y. It is used to offset all the predictions that are made and is called bias in machine learning terminology. The ‘a’ defines the slope of the line and defines how x translates into a y value before the bias ‘b’ is added. It is called weight in the machine learning terminology. The ‘e’ is the error term that acts as a regularization for the model. The objective is to find the best estimates for a and b given the values of x and y. As it can be seen in *[figure 2.3](#c02.xhtml#fig2_3)*, the ‘n’ number of lines can be estimated for the given values of x and y but the goal is to find the best or optimal line which best estimates the value of y given x. The optimal line will be the best estimate which allows finding the most approximate values of y given a value of x, it may not be the exact value of y but very close to the value of y. This kind of estimation works for many business applications and hence, linear regression and its types are popular.

![](images/Figure-2.3.jpg)

**Figure 2.3:** Estimated lines of simple linear regression

Since ‘n’ number of lines can be estimated, the method starts with an initial line with some random values for ‘a’ and ‘b’ (say 1). The line needs to be evaluated to find if it is the best or optimal line. If yes, then the method ends otherwise a new line need to be estimated by making changes to the ‘a’ and ‘b’ values. So, a way needs to be devised to evaluate if the given line is the optimal line and to update the values of ‘a’ and ‘b’ values to estimate a new line that is closer to the optimal line. The former is known as the **cost function** and later the update function in machine learning terminology.

Let the value of y for any given value of ‘a’ and ‘b’ be represented as *h(y)*. Then if there are ‘m’ data points in the data set then there will be ‘m’ *h(y)* values for all x. The *h(y)* is the estimated y and ‘y’ is the actual value. So, the value *(h(y) – y)* indicates how close is the estimated value of y from the actual y. This value needs to be minimized to find the optimal line. This can be achieved by using the following equation and it will be the cost function:

![](images/c02eq-1.jpg)

Now that the cost function is ready, the update function needs to be identified. Each time an estimated line is found that it is not the optimal line, a new line needs to be estimated by updating the values of ‘a’ and ‘b’. Since ‘a’ and ‘b’ values have different effects on the line being updated, they need to be updated independently. That means the update function need to be devised to determine ‘a’ and ‘b’ independently. A good possibility is to use the partial derivative of the cost function as the update function. The partial derivative of the cost function with respect to ‘b’ will be:

![](images/c02eq-2.jpg)

The partial derivative of the cost function with respect to ‘a’ will be:

![](images/c02eq-3.jpg)

Now that the update function is ready for updating the ‘a’ and ‘b’ values, but by how much the value needs to be updated will be given by the following equation:

![](images/c02eq-4.jpg)

Here, alpha is called the **learning quotient** in machine learning terminology and is usually set to a small value like 0.01 and it is configurable based on the data set being used. If it is too large, the training will diverge, while it is too small, overfitting can occur, hence it needs to be configured appropriately. The specialty of the preceding update functions is that they will not only give the new values to be updated for ‘a’ and ‘b’ but the values also tell if the new line is moving up or down from the previously estimated line. For example, if new ‘a’ decreases from the previous value, then the line moves down. If the new ‘a’ increases from the previous value, then the line moves up.

Using the cost function and update functions, the model is trained for multiple iterations till the optimal line is found or if the best line estimated is not improving. For the preceding data set the model stops when the red line is estimated and it is found to be optimal as shown in *[figure 2.4](#c02.xhtml#fig2_4)*. The red line shown in the following figure shows the optimal line estimated by the algorithm:

![](images/Figure-2.4.jpg)

**Figure 2.4:** Optimal line of simple linear regression

The prototype of the linear regression class from sklearn package is given as follows:

*   `class sklearn.linear_model.LinearRegression(*, fit_intercept=True, normalize=False, copy_X=True, n_jobs=None)`
*   `fit_intercept`: If set to True the intercept will be used in calculations, if False the intercept is not used in calculations and data is expected to be centered.

The methods of the class are given in the following table:

 
| **Method Name** || **Description** |
| --- | --- |
| `fit(self, X, y)` || Takes the training samples X and target values y and returns self after fitting the model according to the given training data. |
| `get_params(self)` || This function gets the parameters for the estimator and contained sub objects that are estimators. |
| `predict(self, X)` || The function takes the input samples X and returns the predicted class labels for the samples in X. |
| `score(self, X, y)` || The function takes the samples X as input, corresponding target values y and returns the coefficient of determination R2 of the prediction. Return the coefficient of determination R2 of the prediction.The coefficient R2 is defined as (1 - u/v), where u is the residual sum of squares `((y_true - y_pred) ** 2).sum()` and v are the total sum of squares `((y_true - y_true.mean()) ** 2).sum()`. The best possible score is 1.0 and it can be negative (because the model can be arbitrarily worse). A constant model that always predicts the expected value of y, disregarding the input features, would get an R2 score of 0.0. |
| `set_params(self, **params)` || This function sets the parameters for the estimator. |

**Table 2.2:** Methods of the Linear Regression class

# [2.5.2 Support vector machine (SVM)](#toc.xhtml#s33a)

A support vector machine is a supervised machine learning algorithm that is used mainly for classification. The main goal of SVM is to segregate the given data into two classes in the best possible way. It does this by finding a line (or hyperplane) between the data of the two classes. Let us take the following example where the task is to find a decision boundary (line) that separates the given data of black boxes from white circles:

![](images/Figure-2.5.jpg)

**Figure 2.5:** Data set points with black boxes and white circles

As it can be seen in *[figure 2.6](#c02.xhtml#fig2_6)*, there are multiple lines that are possible which separates the given data into two classes, but the task is to find the line which best separates the given data into two classes.

![](images/Figure-2.6.jpg)

**Figure 2.6:** Lines that separate the data of two classes

The SVM algorithm solves this problem by finding the optimal line. It starts by picking a line and the points which are closest to the line from both the classes. These points are called **support vectors**. It then computes the distance between the support vectors and the line, the distance is called the **margin**. The objective of the algorithm is to maximize the margin for the line. The line or the hyperplane for which the margin is the maximum will be the optimal line or hyperplane as shown in *[figure 2.7](#c02.xhtml#fig2_7)*. *[Figure 2.7](#c02.xhtml#fig2_7)* also shows the support vectors (box and circle with star) and optimal line with maximum margin:

![](images/Figure-2.7.jpg)

**Figure 2.7:** Optimal line for the data set

Consider the data in *[figure 2.8](#c02.xhtml#fig2_8)* for two classes, it can be seen the data is linearly non-separable. A line cannot be used to separate this data linearly but it can be made linearly separable in the higher dimension using SVM.

![](images/Figure-2.8.jpg)

**Figure 2.8:** Non-linear separable data set

Let us assume the following data is in the x and y axes. Now consider z-axis which is built on the constraint given by the following equation, which tells that the new data point on the z-axis will be the sum of squares of the distance of the present data point from the origin on the x-axis and y-axis:

*z = x² + y²*

*[Figure 2.9](#c02.xhtml#fig2_9)* shows the distribution of data in the z axis which is a higher dimension compared to the x and y axes:

![](images/Figure-2.9.jpg)

**Figure 2.9:** Decision boundary in higher dimension

The dashed line represents the decision boundary in the higher dimension. As it can be seen, the equation for the dashed line (decision boundary) is given by z = n, where n is constant. So, the equation x² + y² = z will now become x² + y² = n which is an equation of a circle. If this line separator is projected back to the original dimensions using this transformation the decision boundary will be obtained in original dimensions as shown in *[figure 2.10](#c02.xhtml#fig2_10)*. The figure shows how the data gets distributed in the original dimensions and with a separable boundary:

![](images/Figure-2.10.jpg)

**Figure 2.10:** Decision boundary in the original dimension

The function z is called the **kernel function** which is used to find the decision boundary in the higher dimensions for non-separable data in the original dimensions.

The SVM algorithm can be implemented with all the features using the `libsvm` library from the `sklearn` package. The class for SVM with default parameters is given as follows:

`class sklearn.svm.SVC(C=1.0, kernal=’rbf’, degree=3, gamma=0.0, shrinking=True, probability=False, tol=0.001, cache_size=200, class_weight=None, verbose=False, max_iter=-1, random_state=None)`

The details of a few important parameters are given as follows:

**Kernel**: It can be either ‘linear’, ‘poly’, ‘rbf’, ‘sigmoid’, ‘precomputed’, or callable. It specifies the kernel type to be used in the algorithm. If none is given, ‘rbf’ will be the default. If set to callable, the kernel matrix is precomputed.

**Degree**: It is the degree of the polynomial kernel function (‘poly’) and is ignored for all other kernels.

**Gamma**: Kernel coefficient for ‘rbf’, ‘poly’, and ‘sigmoid’, if it 0.0 then 1/n\_features will be used.

Methods of the class are given in the following table:

 
| **Method name** || **Description** |
| --- | --- |
| `decision_function(X)` || The function takes the input samples X and returns the decision function of the sample for each class in the model. |
| `fit(X, y, sample_weight=None)` || Takes the training samples X and target values y and returns self after fitting the model according to the given training data. |
| `predict(X)` || The function takes the input samples X and returns the class labels for the samples in X. |
| `predict_log_proba(X)` || The function takes the samples X as input and returns the log of probabilities of the samples for each class in the model. |
| `predict_proba(X)` || The function takes the samples X as input and returns the probability of the samples for each class in the model. |
| `score(X, y, sample_weight=None)` || The function takes the samples X as input, corresponding target values y and returns the mean accuracy of prediction. |
| `get_params(deep=True)` || This function gets the parameters for the estimator. |
| `set_params(**params)` || This function sets the parameters for the estimator. |

**Table 2.3:** Methods of the class SVC

# [2.5.3 Decision trees](#toc.xhtml#s34a)

Decision trees are the non-parametric supervised learning mechanism that can be used for both classification and regression problems. The objective of the algorithm is to learn the decision rules based on the input data features and predict the target value of the output variable. Intuitively, from the public source, it can be defined as, “*A decision tree is a decision support tool that uses a tree-like model of decisions and their possible consequences, including chance event outcomes, resource costs, and utility. It is one of the ways to display an algorithm that only contains conditional control statements*.” Simply put, a decision tree uses a tree-like data structure (typically, a binary tree) to make a model of the data (creating a sense of the data provided) using a bunch of if-else conditions at every node of the tree.

Consider an example where *John* wants to play badminton on a particular day, say Sunday. The decision is whether John can play badminton on Sunday or not. John needs to check if the weather (rainy, sunny or cloudy), temperature (hot, mild, cool), wind (high, low), and if the court is occupied (yes, no) to decide if he can play or not on Sunday. If the following *[table 2.2](#c02.xhtml#tab2_2)* is given to John with all the features he wanted to check for the past 11 days, it makes it easy for him to decide. But if none of the rows in the following table matches the conditions of the weather, temperature, and other features then is as required by *John*, then it becomes difficult for him to make a decision. In these and similar kind of scenarios, the decision tree algorithm comes as a savior which uses a decision tree to represent the data as a tree as shown in *[figure 2.11](#c02.xhtml#fig2_11)* which analyzes all the possible paths and make a final decision by following a tree-like structure.

The following table gives the list of features for 11 days which John can use to decide if he can play badminton or not on Sunday:

 
| **Day** || **Weather** || **Humidity** || **Windy** || **Occupied** || **Play Football** |
| --- | --- | --- | --- | --- | --- |
| **1** || Rainy || Hot || High || False || No |
| **2** || Rainy || Hot || High || True || No |
| **3** || Sunny || Mild || Low || False || Yes |
| **4** || Sunny || Cool || Low || False || Yes |
| **5** || Sunny || Cool || High || False || Yes |
| **6** || Sunny || Cool || High || True || No |
| **7** || Rainy || Mild || High || False || No |
| **8** || Rainy || Cool || Low || False || Yes |
| **9** || Cloudy || Hot || Low || False || Yes |
| **10** || Cloudy || Cool || High || False || Yes |
| **11** || Cloudy || Hot || Low || True || No |

**Table 2.4:** Input data and target values for the problem of playing badminton

When the decision tree algorithm is allowed to learn the features and build a decision tree, it will be as shown in *[figure 2.11](#c02.xhtml#fig2_11)*. The figure gives a decision tree using which John can decide if he can play badminton on Sunday or not:

![](images/Figure-2.11.jpg)

**Figure 2.11:** A decision tree for the problem of playing badminton

If the features in the preceding table were continuous values, then the internal nodes in the decision tree will test the value against a threshold value as shown in *[figure 2.12](#c02.xhtml#fig2_12)*. The figure gives the decision tree with the same set of features but the values of some of these features are not discrete:

![](images/Figure-2.12.jpg)

**Figure 2.12:** A decision tree (with continuous-valued features) for the problem of playing badminton

The following table gives the terminologies related to decision trees which will be used in general to know about the decision trees:

 
| **Terminology** || **Description** |
| --- | --- |
| **Root Node** || It represents the entire training set or sample. It further gets divided into two or more subsets (homogeneous sets). |
| **Decision Node or Sub Node** || When a root node or internal node gets split into other internal nodes then it is called a decision node or sub-node. It represents the attributes or features of the data set. |
| **Leaf Node or Terminal Node** || Nodes which cannot be further split or divided are called terminal or leaf nodes. Leaf nodes represent the target values or class labels of the data set. |
| **Dividing or Splitting** || The process of dividing a root node or sub-node into two or more sub-nodes is called dividing or splitting. |
| **Pruning or Removing** || The process of removing a sub-node of the decision node is called pruning which is the reverse of splitting. |
| **Branch or Sub Tree** || A sub-section of the entire tree (root, sub-set of sub-nodes and leaf nodes) is called the branch or sub-tree. |
| **Parent Node** || A node that gets divided into two or more sub-nodes is called the parent of those sub-nodes. |
| **Child Node** || The sub-nodes of the parent node are called child nodes. |

**Table 2.5:** Terminologies of a Decision Tree

The steps in the decision tree algorithm are given as follows:

1.  Understanding and charting the problem area for which decision making is required.
2.  At the start of the process, the whole training sample is set as the root node. If the feature values are not categorical, they are made categorical based on the threshold value of the variables.
3.  Pick the best attribute or feature which best splits or separates the data which will now be set as the root node.
4.  Based on the attribute values, the records are distributed recursively.
5.  Now statistical methods are used for selecting attributes based on a certain criterion as the internal or decision nodes.

As seen in the preceding steps, the major challenge in the decision tree process determining the attribute for the root node or internal node at each level which is called the attribution selection. The most common attribution selection measures used are information gain and the Gini index.

# Information gain

Information gain is the statistical property that measures how well an attribute splits that data into groups based on classification. Information gain is measured using entropy. Entropy is the measure of the randomness or uncertainty of a random variable X. It characterizes the impurity of an arbitrary collection of examples. The more the information content, the higher the entropy value for that. Alternatively, the purer the collection is the less entropy it has and less will be the information content. For a binary classification data set, if the sample is heterogeneous with an equal share of samples for both classes then entropy is one, if the samples are homogeneous then entropy is zero. This shows the lower the entropy it is easier to define the class. Entropy is calculated using the following formula:

*Entropy = -p[1] log(p[1]1) - p[2] log(p[2])-…-p[n] log(p[n])*

Here, ‘n’ is the number of classes, pi is the probability of class i. Higher the information gain, lower the entropy. Information gain is inversely proportional to entropy. Hence, the attribute with the lowest entropy or highest information gain will define the samples better. The information gain for a particular node is given by the following formula:

*Information gain = Entropy of parent – sum (weighted average \* entropy of child node)*

*Weighted average = number of observations in particular child/sum of observations in all child node*

While doing the split using information gain, first calculate the entropy of the parent node of the split and then calculate the entropy of the individual node of the split and calculate the weighted average of all the sub-nodes available in the split, then calculate the information gain using the preceding formula. This step is repeated for all splits and the split with the highest information gain value will be chosen.

# Gini index

It is the measure of how often a randomly selected sample would be incorrectly identified. The Gini index is calculated using the following formula. It is also known as **Gini impurity**:

![](images/c02eq-5.jpg)

Here, ‘n’ is the number of classes and pi is the probability of class ‘i’.

The higher the Gini index for an attribute, it defines the samples better. Hence, the attribute with the highest Gini index will be selected for the split. While doing the split using the Gini index for sub-nodes using the preceding formula, the Gini index for the split is given by the weighted sum of the Gini index score of each node of that split. This step is repeated for all the splits and the split with the highest Gini index score will be selected.

The Gini index varies between the values 0 and 1. If all the elements are linked with a single class, then it is called pure and is represented by 0. When all the elements are randomly distributed across classes, it is impure and is represented by 1. The value of 0.5 shows that the elements are equally distributed across the classes.

The decision tree algorithm can be implemented with all the features using the class `DecisionTreeClassifier` from `sklearn`. The class prototype for the decision tree from sklearn package is given as follows:

`class sklearn.tree.DecisionTreeClassifier(*, criterion='gini', splitter='best', max_depth=None, min_samples_split=2, min_samples_leaf=1, min_weight_fraction_leaf=0.0, max_features=None, random_state=None, max_leaf_nodes=None, min_impurity_decrease=0.0, min_impurity_split=None, class_weight=None, presort='deprecated', ccp_alpha=0.0)`

The important input parameters of the class and their purpose are given as follows:

**Criterion**: The function to measure the quality of a split. Supported criteria are “*gini*” for the Gini impurity and “*entropy*” for the information gain.

**Splitter**: The strategy used to choose the split at each node. Supported strategies are “*best*” to choose the best split and “*random*” to choose the best random split.

`max_features`: The number of features to consider when looking for the best split.

*   If int, then considers `max_features` feature at each split.
*   If float, then `max_features` is a fraction and `int(max_features * n_features)` features are considered at each split.
*   If “auto”, then `max_features=sqrt(n_features)`.
*   If “sqrt”, then `max_features=sqrt(n_features)`.
*   If “log2”, then `max_features=log2(n_features)`.
*   If None, then `max_features=n_features`.

The following table gives the details of the methods of the class of the previously mentioned decision tree:

 
| **Method Name** || **Description** |
| --- | --- |
| `apply(self, X)` || Takes the input training samples X and returns for each data point x in X the index of leaf x ends up in. |
| `cost_complexity_pruning_path(self, X, y)` || Takes the input training samples X, the target values y and sample weights and computes the pruning path during minimal cost-complexity pruning. |
| `decision_path(self, X)` || Takes the input training samples X and returns the decision path as a matrix. |
| `fit(self, X, y)` || Takes the training samples X and target values y and returns self after fitting the model according to the given training data. |
| `get_depth(self)` || Returns the depth of the decision tree. |
| `get_n_leaves(self)` || Returns the number of leaves of the decision tree. |
| `get_params(self)` || This function gets the parameters for the estimator. |
| `predict(self, X)` || The function takes the input samples X and returns the class labels for the samples in X. |
| `predict_log_proba(self, X)` || The function takes the samples X as input and returns the log of probabilities of the samples for each class in the model. |
| `predict_proba(self, X)` || The function takes the samples X as input and returns the probability of the samples for each class in the model. |
| `score(self, X, y)` || The function takes the samples X as input, corresponding target values y and returns the mean accuracy of prediction. |
| `set_params(self, **params)` || This function sets the parameters for the estimator. |

**Table 2.6:** Methods of the class DecisionTreeClassifier

# [2.5.4 Random forest](#toc.xhtml#s35a)

As seen in the previous section, decision trees are easier to understand as the decision-making process is similar to how humans make decisions. Decisions make perfect classifiers but the main problem with them is that they perform badly with the unseen data. This is because they get trained perfectly on trained data and classify the data by overfitting them. So, the better way is to take this advantage of the perfectness of classification on the training data. That is build decision trees by randomly selecting the input samples and create a forest of decision trees and use an ensemble method to make a decision. This is called **Random Forest**.

Creating a decision tree with perfection will have a model with a high variance flexible model which does not generalize on the unseen data. An inflexible model will have a high bias since it gets trained by making assumptions on the training data. So, a good model will be one with the proper trade-off between variance and bias. This is how the random forest is built with decision trees to get a good trade-off on variance and bias. The trees are built using random sampling of data during training and while splitting nodes the subset of features is selected at random. Due to this randomness, this method is called random forest.

Each tree starts with a random sample of data points during training. The samples are selected using bootstrapping which means some samples will be used many times in a single tree. By this, each individual tree (decision tree) will have high variance and normal bias for the data set it is trained but the forest of decision trees will have less variance and good bias, so proper trade-off is achieved by random forest. Using bootstrapping for random selection of samples, the decision is obtained by averaging the predictions of the forest of trees with **bagging** or **bootstrap aggregating**. Random forest uses feature bagging also. That means while at each split in the decision tree only a random subset of features is selected.

Thus, a random forest aggregates the many decision trees, trains each decision tree using the random samples of input data, splitting nodes using a limited number of features selected randomly. Then by averaging the predictions from each individual tree, the final prediction is determined.

The random forest will be discussed in detail in *section 2.8* ‘*Use Cases and Examples*’ with a suitable example implementation.

The prototype of the random forest class from the `sklearn` package is given as follows:

`class sklearn.ensemble.RandomForestClassifier(n_estimators=100, *, criterion='gini', max_depth=None, min_samples_split=2, min_samples_leaf=1, min_weight_fraction_leaf=0.0, max_features='auto', max_leaf_nodes=None, min_impurity_decrease=0.0, min_impurity_split=None, bootstrap=True, oob_score=False, n_jobs=None, random_state=None, verbose=0, warm_start=False, class_weight=None, ccp_alpha=0.0, max_samples=None)`

The important input parameters of the class and their purpose are given as follows:

`n_estimators`: It specifies the number of trees that needs to be built in the forest.

**Criterion**: The function to measure the quality of a split. Supported criteria are “*gini*” for the Gini impurity and “*entropy*” for the information gain.

**Splitter**: The strategy used to choose the split at each node. Supported strategies are “*best*” to choose the best split and “*random*” to choose the best random split.

**max\_features**: The number of features to consider when looking for the best split.

*   If int, then consider `max_features` feature at each split.
*   If float, then `max_features` is a fraction and `int(max_features * n_features)` features are considered at each split.
*   If “auto”, then `max_features=sqrt(n_features)`.
*   If “sqrt”, then `max_features=sqrt(n_features)`.
*   If “log2”, then `max_features=log2(n_features)`.
*   If None, then `max_features=n_features`.

**Bootstrap**: If set to True, data considers bootstrap samples for building trees, if False the whole data set is used to build each tree.

The following table gives the details of the methods of the random forest classifier class given earlier:

 
| **Method Name** || **Description** |
| --- | --- |
| `apply(self, X)` || Takes the input training samples X and returns for each data point x in X the index of leaf x ends up in. |
| `decision_path(self, X)` || Takes the input training samples X and returns the decision path as a matrix. |
| `fit(self, X, y)` || Takes the training samples X and target values y and returns self after fitting the model according to the given training data. |
| `get_params(self)` || This function gets the parameters for the estimator and contained sub objects that are estimators. |
| `predict(self, X)` || The function takes the input samples X and returns the predicted class labels for the samples in X. The class label is predicted based on the vote by the trees in the forest, which is weighted by their corresponding probability estimates. The final predicted class will be one with the highest mean probability estimate found across the trees. |
| `predict_log_proba(self, X)` || The function takes the samples X as input and returns the log of probabilities of the samples for each class in the model. |
| `predict_proba(self, X)` || The function takes the samples X as input and returns the probability of the samples for each class in the model. |
| `score(self, X, y)` || The function takes the samples X as input, corresponding target values y and returns the mean accuracy of prediction. |
| `set_params(self, **params)` || This function sets the parameters for the estimator. |

**Table 2.7:** Methods of the class RandomForestClassifier

# [2.6 Performance statistics](#toc.xhtml#s36a)

The performance of machine learning algorithms is evaluated against the metrics. There are various metrics against which the supervised machine learning algorithms can be evaluated, for example, classification accuracy, F1 score, confusion matrix, mean absolute error, mean squared error, and logarithmic loss. Picking metrics for evaluation is very important since it judges the performance of the model. And it also provides the importance of various characteristics of the results which are being influenced by the selected metrics. There are various metrics that can be used to measure the performance of the regression and classification problems.

# [2.6.1 Performance metrics of regression problems](#toc.xhtml#s37a)

Regression is the type of supervised machine learning in which the predicted dependent variable will be a continuous variable. There are different metrics to evaluate the performance of the regression models. A few of them are given in detail as follows:

*   **Mean absolute error**
    
    Mean absolute error is the measure of the average difference between the actual target value and the predicted value by the regression model. It is given by the following equation:
    
    *MAE = 1/n Σ |y - y’|*
    
    As it can be seen, it is a linear score and differences are weighted equally for all the values. Hence, it is not a good measure for various applications and not good for data set with outliers. It is not differential and hence is suitable for some optimization techniques.
    
*   **Mean squared error**
    
    Mean squared error is a measure in which the average squared difference of the target (or actual) value and predicted value by the regression model is used to evaluate the performance. It is given in the following equation:
    
    *MSE = 1/n Σ (y - y’)²*
    
    Here, ‘n’ is the total number of samples and y is the actual value and y’ is the predicted value by the regression model. It is the most preferred metric since it takes the squared difference of error, and hence it penalizes even the smallest error. And the equation is differential and hence it can be optimized better. It is a better metric as compared to the mean absolute error.
    
*   **Root mean squared error**
    
    Root mean squared error is a measure in which the square root of the mean or average of the squared difference of the actual or target values and the predicted values by the regression model is used to evaluate the performance. It is given by the following equation:
    
    *RMSE = √ (1/n Σ (y – y’)²)*
    
    The difference between the actual or target values and the predicted values is called the **residuals**. Root mean squared error is the variance of the residuals. It shows how accurately the model predicts the response. The lower the RMSE, the better is the model performance. Hence, RMSE will be more suitable for problems where large errors are undesired. RMSE gives higher weightage to large errors and penalizes them as compared to MSE and MAE. It is differential and useful for many optimization techniques.
    
*   **R-squared or R2 or Co-efficient of determination**
    
    The coefficient of determination is the measure in which the proportion of variance in the dependent variable (target or actual values) is determined by using the explanation of the independent variables (features or input values). It is the measurement of how close the data is from the regression line. It is given by the equation as follows:
    
    *R² = SSR / SST*
    
    Here,
    
    **Sum of the square of residuals** (**SSR**): Residual in this case is the difference between the predicted value and the mean value of y (target value) and SSR is given by,
    
    *SSR =* Σ *(y’ - ya)²*
    
    y’ is the predicted value by the regression model and ya is the average or mean value of y.
    
    **Sum of the square of error** (**SSE**): It is the sum of the square of the difference between the actual target value (y) and predicted value (y’) by the regression model:
    
    *SSE =* Σ *(y - y’)²*
    
    **Total sum of squares** (**SST**): It is the sum of squares of the difference between the actual value or target value (y) and mean or average value of y (ya):
    
    *SST =* Σ *(y – ya)²*
    
    From the preceding equations, it can be observed that SST is the sum of SSR and SSE which is given by:
    
    *SST = SSR + SSE*
    
*   The value of R-squared will be in the range of 0 and 1. A value of 0 indicates the regression model dependent variable cannot be explained by the independent variable at all. A value of 1 indicates that the regression model dependent variable can be perfectly explained by the independent variable. In general, the value of R-squared will be between 0 and 1. Hence, the value of R-squared is closer to the value of 1 means, the model is better.
    
    When a new variable or feature is added to the data set, the R-squared value increases always. The model performance may or may not improve due to the addition of a new variable but the R-squared value increases which is the pitfall of using this metric.
    
*   **Adjusted R-squared**
    
    It is the same as R-squared but overcomes the pitfall of R-squared is given earlier. It is given by the following equation:
    
    *R²a = 1 – (1 – R²) (n – 1) / (n – p - 1)*
    

Here, ‘n’ is the total number of samples and ‘p’ is the total number of features. As it can be seen from the equation when the new independent variable is added it increases the value of R-squared and it increases the value of *(n – p – 1)*. As (n – p – 1) increases, it decreases the value of the adjusted R-squared. Hence, the adjusted R-squared can determine the performance of the model better when new variables are added. Adjusted R-squared metric can thus be useful for problems with larger features and the most effective features need to be selected for the model to be trained.

# [2.6.2 Performance metrics of classification problems](#toc.xhtml#s38a)

A few metrics of classification problems are discussed starting with the confusion matrix as follows:

*   **Confusion matrix**
    
    It is the metric used to measure the correctness and accuracy of the model. It can be used for binary or multi-class classification problems. Though it is not a direct measure of performance, many metrics are measured using the measures of the confusion matrix.
    
    For a binary classification problem, the target variable will have two values which are called **actual values**. It can be represented as 0 and 1, or True or False. Here, 0 and 1 are used. The predictions of the model are called predicted values. A confusion matrix is a two-dimensional matrix with two rows and two columns where rows are represented with the predicted values and columns with actual values as shown in *[figure 2.13](#c02.xhtml#fig2_13)*:
    
    ![](images/Figure-2.13.jpg)
    
    **Figure 2.13:** Confusion Matrix
    

Terminologies used in *[figure 2.13](#c02.xhtml#fig2_13)* are given as follows:

1.  **True Positives (TP)**: True Positives gives the count of cases of those data samples whose actual value will be 1 and the predicted value will also be 1.
2.  **True Negatives (TN)**: True Negatives gives the count of cases of those data samples whose actual value will be 0 and the predicted value will also be 0.
3.  **False Positives (FP)**: False Positives gives the count of cases of those data samples whose actual value will be 0 and the predicted value will be 1.
4.  **False Negatives (FN)**: False Negatives gives the count of cases of those data samples whose actual value will be 1 and the predicted value will be 0.

From the meaning of the preceding terminologies, it is clear that the model’s performance will be good with higher values of TP and TN and lower values of FP and FN. The model should be trained to achieve a higher value of TP and TN and minimize the values of FP and FN. Among FP and FN which of these or both need to be minimized depends on the needs of the classification problem. Minimizing False Negatives will be important predominately in the medical domain. For example, if the classification problem is to detect if the patient is having some critical disease like cancer or HIV or not. Let us take if the patient is having cancer is represented as 1 and by 0 if not. In this case, it is always good to reduce False Positives than False Negatives. That means, if the patient has cancer (1) and the model predicts negative (0) – False Negatives, this would have serious implications on the patient and diagnosis. Hence FN needs to minimize as much as possible. On the other hand, if the patient does not have cancer (0) and the model predicts has had cancer (1) – False Positives, this would have fewer implications because generally, secondary tests will always be performed for critical diseases before confirming the disease as positive. Hence, False Positives is better than False Negatives in this problem.

*   **Accuracy**
    
    Accuracy of the model measures the correctness property of the model, that means it is given by the number of correct predictions made given the total number of predicts made by the model. From the confusion matrix it is equal to the following equation:
    
    ***Accuracy = (TP + TN) / (TP + TN+ FP + FN)***
    
                    = *Right predictions / Right and Wrong Predictions*
    
                    = *Right predictions / Total count of predictions*
    
    When the number of target variables in the data set is balanced for each of the classes then accuracy is a good measure because the right and wrong predictions of the class will be equally shared across each of the classes. In the case of unbalanced data set with one class having more data samples compared to other classes, accuracy would be the right evaluation metric to measure the model’s performance.
    
*   **Precision**
    
    The precision of the model is the proportion of the count of correct positive results predicted by the model to the total count of positive results predicted by the model. From the confusion matrix the equation for precision is given as follows:
    
    *Precision = TP / (TP + FP)*
    
    So, the precision metric of the model tells us the number of positive results the model was right in predicting given the total positive results predicted by the model. In the case of the pneumonia detection model, if the model is able to detect five pneumonia cases and it was able to predict all of them correctly then the model has the precision of 100%.
    
*   **Recall or Sensitivity**
    
    Recall or Sensitivity of the model is the proportion of the count of correct positive results predicted by the model to the actual correct results in the data set. From the confusion matrix the equation for recall or sensitivity is given as follows:
    
    *Recall = TP / (TP + FN)*
    
    So, the recall metric of the model tells us the number of the positive results the model was right in predicting when compared to actual positive results given the data set. With this explanation, the recall will be 100% if the model predicts 1 for all samples in the data set.
    
*   **Specificity**
    
    Specificity of the model is the proportion of the count of correct negative results predicted by the model to the actual negative results in the data set. From the confusion matrix the equation for specificity is given as follows:
    
    *Specificity = TN / (TN + FP)*
    
    Suppose 10 people have pneumonia among the data set of 100 persons. And let us assume the model predicts all 10 people having pneumonia correctly. In this case, the *TN + FP* will be 90 and TN (model predicting normal person as normal) will be 0. TN is 0 since the model predicted all the pneumonia cases correctly. So the specificity for this model will be 0%.
    
    Proper handling of the precision and recall metrics has been done to draw a trade-off of their utilization to measure the performance of the model. As seen previously, high precision or high recall gives different implications for the model’s performance. Hence, this gave the way for metric F1 score which is defined as follows:
    
*   **F1 Score**
    
    Before the F1 Score is defined, it is good to understand the harmonic mean. The harmonic mean of two numbers x and y are given by the following equation:
    
    *Harmonic mean = 2xy / (x + y)*
    
    As seen from the equation, the harmonic mean will be equal to the average of x and y when both are equal. It will be closer to a smaller number when x and y are different as compared to a bigger number.
    
    With the definition of harmonic mean, the F1 Score is the harmonic mean of precision and recall metrics as defined previously. Hence, the F1 Score will be given by the following equation:
    
    *F1 Score = 2 \* Precision \* Recall / (Precision + Recall)*
    
    From the preceding equation, it can be seen that the F1 Score metric tells us how precise (a measure of instances it predicted correctly) the model is and how robust or recall the model is (not missing the significant number of instances which are difficult to classify).
    
    In many classification problems, the F1 Score metric will be a better metric as compared to the accuracy metric because accuracy will be mostly contributed by TN. For many problems, TN may not be so important but FN and FP would be. In many problems, FN and FP will help to handle business costs better as compared to TN. In those scenarios, the F1 Score will give better results as it takes care of both FN and FP and it is seen to work better for unbalanced class distribution also.
    
*   **Area Under The Curve (AUC) –Region of Operating Characteristics (ROC)**
    
    AUC ROC is a measure that indicates how the probabilities from the positive classes are clearly separated from the negative classes. AUC is the probability that the model will rank the randomly chosen positive class sample higher than the randomly chosen negative class sample. So, in a way, AUC represents the degree of separability of two classes while ROC gives the probability curve of separation of two classes. The following terms are required to define AUC-ROC:
    
*   **True Positive Rate (TPR or Sensitivity)**: This is defined previously.
*   **True Negative Rate (TNR or Specificity)**: This is defined previously.
*   **False Positive Rate (FPR)**: This is the measure of the proportion of count of the negative data samples that are predicted as positive, with respect to all the negative data samples. It is given by the following equation:
    
    *False Positive Rate = FP / TN + FP*
    

Now, the graph is plotted with FPR as the x-axis and TPR as the y-axis. The values of FPR and TPR will be in the range of 0 to 1. The FPR and TPR are computed for various threshold values and are plotted accordingly. The curve thus obtained is called the ROC and the area under the ROC is called AUC. The model which has a larger AUC is said to perform better as compared to the one with a smaller AUC. In *[figure 2.14](#c02.xhtml#fig2_14)*, three ROC – C1, C2, and C3 are shown. AUC of C1 is larger than C2 and C3, AUC C2 is larger than C3. The model with AUC for ROC C1 performs better as compared to the model with AUC with ROC C2 and the model with AUC with ROC C3 is the worst performing model:

![](images/Figure-2.14.jpg)

**Figure 2.14:** AUC-ROC Comparison

*   **Log Loss**
    
    Log Loss is the measure that is used to quantify the accuracy metric by working on penalizing the false classifications. To calculate the log loss, the classifier has to output the probability of each class rather than merely giving the result as the most likely class label. With this, the equation of the log loss is given by the following equation:
    

![](images/c02eq-6.jpg)

Here, *yi=1* for positive class and 0 is for negative class. These are the actual target values. p(yi) is the predicted probability of positive class and *1 – p(yi)* is the probability of negative class. As it can be seen from the formula, the lower the log loss the better is the model’s performance and the accuracy will be more and higher the log loss the performance of the model will be bad and the accuracy will be low.

As it can be seen for binary classification, the AUC is computed with varying decision thresholds whereas the log loss is computed based on the certainty of classification.

# [2.7 Optimization and loss methods](#toc.xhtml#s39a)

The difference between the actual or target values and the predicted values is called the **error**. The function used to determine the error is called the loss function. There are different loss functions that are used to compute the error and each gives different error computations and has a considerable effect on determining the performance of the model. Since the learning mechanism and output is different for regression and classification problems, each type has their loss functions. The loss function when considered for the entire data set is called the cost function.

The loss function computes the error and this error needs to be minimized for the model to perform better. As seen in the definitions of regression and classification problems the dependent variable is predicted based on the independent variables. The loss function will be defined in terms of weights, bias and independent variables. From *section 2.6.1* for linear regression, the output Y is given by:

*Y = aX + b + e*

Here ‘a’ is called weights and ‘b’ is called the bias and ‘e’ is the error term. The loss function is given by *(h(y) – y)* and the cost function is given by:

![](images/c02eq-7.jpg)

The weights and bias need to be updated during training so that the error is minimized. The weights are modified using a function called the **optimization function**. One of the common optimization techniques is gradient descent. In this technique, the partial derivative of the loss function is taken with respect to weights and weights are modified in the opposite direction of the calculated gradient. These steps are repeated till the loss function finds that the error is minimum, in other words, the minima of the cost function is reached. From *section 2.6.1*, the partial derivative of the cost function with respect to ‘b’ will be:

![](images/c02eq-8.jpg)

The partial derivative of the cost function with respect to ‘a’ will be:

![](images/c02eq-9.jpg)

Now that the update function is ready for updating the ‘a’ and ‘b’ values, but by how much the value need to be updated will be given by the following equation:

![](images/c02eq-10.jpg)

Here, alpha is called the learning quotient in machine learning terminology and is usually set to a small value like 0.01 and it is configurable based on the data set being used.

With this background, the loss functions for the regression and classification problems are listed as follows. Firstly, the most common regression loss functions are given, followed by the most common classification loss functions:

*   **L2 Loss or Mean Squared Error or Quadratic Loss (MSE)**
    
    The most commonly used loss function is MSE which is given as follows, which also is the metric for measuring the model’s performance:
    
    *MSE = 1/n Σ (y – y’)*²
    
    As the loss function is easily derivable it is best suited for gradient descent-based optimization techniques.
    
*   **L1 Loss or Mean Absolute Error (MAE)**
    
    This loss function given by the following equation measures the magnitude of errors without considering its direction. This loss function is mainly useful when there are more outliers in the data set. For outliers, the MAE will perform better as compared to MSE:
    
    *MAE = 1/n* Σ *|y - y’|*
    
    As seen from the equation, the L1 loss function will have a constant derivative. It is not best suited for gradient descent-based optimization techniques.
    
*   **Smooth mean absolute error or huber loss**
    
    This loss function is the mean absolute error which becomes the mean squared error when the error becomes small. The threshold for error to make this function from absolute to squared error is given by the parameter delta in the equation. For models which use this loss function, delta will be the hyperparameter. The function is easily differentiated and hence, the gradient descent optimization techniques can be used. It is a better loss function that works as a trade-off between MAE and MSE with the penalty of additional hyperparameter being used during training:
    
    ![](images/c02eq-11.jpg)
*   **Log-cosh loss**
    
    The log-cosh function is the logarithm of hyperbolic cosine of the predicted value by the model and actual target value:
    
    *LCh = Σ log (cosh(y’ - y))*
    
    As it can be seen from the equation, LCh is equal to *abs(x) – log(2)* for large errors and approximately equal to x² / 2 for small errors. So, it mostly works like MSE and it is easily differentiated.
    

The following list is the most common loss functions that are generally used in classification problems in machine learning:

*   **Cross entropy loss or binary cross entropy loss or log loss or negative log likelihood loss**
    
    This is the most common loss function used for classification problems and is given by the following equation:
    
    *Cross Entropy Loss = - y log (p) + (1 – y) log (1 - p)*
    
    Here, *y = 1*, if the actual target value is 1 that is positive class, otherwise *y = 0*, for negative class. And ‘p’ is the predicted probability of the observation that it belongs to class y. If the predicted probability of the target is not equal to the actual or target value then this loss increases. So, it penalizes the wrong predictions heavily and treats the correct predictions. It is easily differentiable and so can be used along with gradient decent optimization techniques.
    
*   **Categorical cross entropy or multiclass cross entropy**
    
    This loss function is used when there are multiple classes and is given by the following equation:
    
    ![](images/c02eq-12.jpg)
    
    Here, M is the total number of classes, *y = 1*, if c is the correct class label for sample ‘o’ and y = 0 otherwise. The po, c is the predicted probability; that observation ‘o’ is of class ‘c’.
    
    It is similar to cross entropy but it is applicable for multiclass classification. It is easily differentiable and so can be used along with the gradient decent optimization techniques.
    
*   **Hinge loss or multiclass SVM loss**
    
    The hinge loss is commonly used for classification problems solved using SVM and it is given by the following equation.
    
    Here, y is the actual or target value between -1 and 1 and y’ is the predicted value by the model between -1 and 1. As can be seen, it simply takes the maximum of 0 or value of (1 – y’ \* y). When the predicted value is not equal to the actual or target value than the loss increases while the y = y’ (actual target value is equal to predicted value) the loss will be equal to zero. It tries to find the most optimum decision boundary by doing **Hinge Loss = max(0, (1 – y’ \* y))** the maximum margin operation.
    
    Hence, it is most suitable for the SVM learning methods. Since it is not differentiable, it is not suitable for the gradient decent optimization methods.
    
*   **Squared hinge loss**
    
    This loss function is similar to hinge loss except that the output of the max function will be squared and it is given by the following equation:
    
    *Squared Hinge Loss = (max(0, (1 – y’ \* y)))²*
    
    The advantage of squaring the hinge loss is that it will handle the outliers better compared to hinge loss. Secondly, it will be easily differentiable and can be used in gradient decent optimization methods.
    
    At the beginning of this section, the optimization technique called gradient descent was briefly defined. The dependent variable, independent variables, the loss function, the cost function, the weights and bias, and the update function for the weights and bias were all defined earlier. Now, the problems with gradient descent are discussed.
    
    Gradient descents are applicable for problems in which the loss function defined show convex surfaces. It does not work for non-convex surfaces and this is the pitfall for some problems. Gradient descent aims to find the global minima of the convex error surface. If there are many local minima in the error surface, it becomes difficult to find global minima using the gradient descent method. The gradient descent method does not perform better when there are saddle points in the error surface. Saddle points are those points where the gradient or slope will be zero but they are optimal points on the surface.
    
    When the gradients are too large or too small the gradient descent method of optimization suffers from vanishing gradient and exploding gradient problems. This would take a long time for the method to converge and at times may not converge to the global minima. The gradient descent optimization method requires more memory and needs floating-point representations to be used. The following are the different types of gradient descent methods that are used to overcome the pitfalls of basic or vanilla gradient descent:
    
*   **Vanilla or batch gradient descent**
    
    Let the cost function be represented by J(θ). So, the following equation is obtained for J(θ):
    
    ![](images/c02eq-13.jpg)
    
    Here, θ is the function of weights ‘a’ and bias ‘b’. The update functions for weights and bias are given as follows:
    
    ![](images/c02eq-14.jpg)
    
    The preceding update functions can be generalized using the following generic steps:
    
    *Update Function = Learning Rate \* Gradient of Parameters*
    
    `update_func = learn_rate * grad_params`
    
    *current parameters = previous parameters – update function*
    
    `curr_params = prev_params – update_func`
    
    In this gradient descent method, the gradient for the cost function is computed for the entire data set.
    
    `curr_params = prev_params – update_func (for all samples in data set)`
    
    Though the advantage of this method is that it always converges to a global minimum but it needs the entire data set to be in memory and each update step is costly since it is computed for the entire data set.
    
*   **Stochastic Gradient Descent (SGD)**
    
    In this method, instead of computing the gradient for the entire data set, the gradient is computed for each sample. This reduces the requirement of memory and computations required. The disadvantage though is that SGD may sometimes converge to local minima rather than global minima. The update function for SGD is given as follows:
    
    `curr_params = prev_params – update_func (for each sample)`
    
*   **Mini-batch gradient descent**
    
    This method uses the best of batch gradient descent and stochastic gradient descent methods and it performs the update operation for the batch of input samples each time and the update function are given as follows:
    
    `curr_params = prev_params – update_func (for each batch of samples)`
    
    Since the operations are performed on batches of samples, it can use the matrix operations for efficient computations. It also achieves a stable convergence as compared to the batch gradient descent and SGD.
    
*   **Gradient descent with momentum**
    
    When there are ravines in the error convex surface that are the curves that are steep in one dimension than in others, the SGD oscillates across the slopes of ravines and makes smaller updates and hence takes more time to reach the local or global minima. To overcome these kinds of problems, this method tries to accelerate in the relevant direction and reduces the oscillations on the ravines. The pseudo equations for the update function are given as follows:
    
    `update_func = learn_rate * grad_params`
    
    `velocity = prev_update * momentum`
    
    `curr_params = prev_params + velocity – update_func`
    
*   **Adaptive gradient or AdaGrad**
    
    This method is useful for sparse data set with a huge variance in the features. The advantage of this method is that it auto-tunes the learning rate based on the frequency of the occurrence of features in the data set. For frequently occurring features, it uses low learning rates and high learning rates otherwise. The pseudo equations for the update function are given as follows:
    
    *gradient = previous gradient + (current gradient \* current gradient)*
    
    *adaptive gradient = √(gradient) + correction parameter (ε)*
    
    *adaptive learning rate = learning rate / adaptive gradient*
    
    `update_func = adaptive learning rate * current gradient`
    
    `curr_params = prev_params – update_func`
    
    It adapts the learning rate by dividing the learning rate by the square root of the adaptive gradient which is the cumulative sum of the past and current squared gradients up to a specific time.
    
*   **Root mean square prop or RMSProp**
    
    This method is an improvement over AdaGrad to overcome the diminishing learning rates in AdaGrad. It adapts the learning rate by dividing the learning rate by the exponential average of the adaptive gradient which is the cumulative sum of the past and current squared gradients up to a specific time. The pseudo equation for this method is given as follows:
    
    *gradient = previous gradient + (current gradient \* current gradient)*
    
    *adaptive gradient = exp(√(gradient)) + correction parameter (ε)*
    
    *adaptive learning rate = learning rate / adaptive gradient*
    
    `update_func = adaptive learning rate * current gradient`
    
    `curr_params = prev_params – update_func`
    
*   **Adaptive moment estimation (Adam)**
    
    This method is similar to AdaGrad and RMSProp that computes the adaptive learning rate. It actually uses two factors to adapt the learning rate, firstly it uses the exponential decaying average of the past squared gradients but it also uses the exponential decaying of the average of past gradients, similar to momentum. While the momentum defined earlier behaves like a ball running down the slope and tries to prevent oscillation around the ravines, Adam behaves like a heavy ball with friction and tries to drive to achieve the minima in the right direction. The pseudo equation for the Adam optimizer is given as follows:
    
    *momentum = exp((gradient)) + correction parameter (ε)*
    
    *adaptive\_momentum = prev\_update \* momentum*
    
    *gradient = previous gradient + (current gradient \* current gradient)*
    
    *adaptive gradient = exp(√(gradient)) + correction parameter (ε)*
    
    *adaptive learning rate = learning rate / adaptive gradient*
    
    `update_func = adaptive learning rate * adaptive momentum`
    
    `curr_params = prev_params – update_func`
    

# [2.8 Use cases and examples](#toc.xhtml#s40a)

Let us consider the recognition of handwritten digits which is a common problem in optical character recognition. This problem includes both locating and identifying the digit in the image. The following is the example code that uses the Random Forest class of the sklearn package to classify the digits to one of the 10 classes (0 to 9). The code gives the programming steps to achieve this and finally reports the evaluation metrics as discussed previously:

`from sklearn.datasets import load_digits`

`handw_digits = load_digits()`

`print (handw_digits.images.shape)`

`→`

`(1797, 8, 8)`

The preceding lines load the pre-loaded digits data set from the `sklearn` package. It then prints the shape of the data set.

From the shape, it is clear that the size of each sample is 8 \* 8 and there are 1797 samples in the data set.

`import matplotlib.pyplot as plt`

`fig, axes = plt.subplots(1, 10, figsize=(8, 8),`

`subplot_kw={‘xticks’:[], ‘yticks’:[]},`

`gridspec_kw=dict(hspace=0.1, wspace=0.1))`

`for I, ax in enumerate(axes.flat):`

`ax.imshow(handw_digits.images[i], cmap’'binar’', interpolation’'neares’')`

`ax.text(0.05, 0.05, str(handw_digits.target[i]),`

`transform=ax.transAxes, color’'green’')`

`plt.show()`

*[Figure 2.15](#c02.xhtml#fig2_15)* is the MNIST dataset applied to the model input. These are 0-9 digits depicted in the pixel format in a matrix:

![](images/Figure-2.15.jpg)

**Figure 2.15:** MNIST Data input

The preceding lines show the first 10 digits from the data set. Since for the random forest, each pixel is treated as a feature, the 8 \* 8 size sample needs to be flattened to a single dimensional array with each pixel representing a feature. And for each sample, the corresponding target value needs to be mapped which is also the class label for each digit image. These two requirements are already resolved in sklearn and available to the user in the data and target variables of the data set. The following lines of code display the input and output shapes:

`X = handw_digits.data`

`print ("The input shape is: ", X.shape)`

`y = handw_digits.target`

`print ("The output shape is: ", y.shape)`

`→`

`The input shape is: (1797, 64)`

`The output shape is: (1797,)`

Now, the data set can be trained and evaluated using the Random Forest classifier of sklearn. The prototype of the class and its method is given in *section 2.5.4*.

`from sklearn.model_selection import train_test_split`

`from sklearn.ensemble import RandomForestClassifier`

`Xtrain, Xtest, ytrain, ytest = train_test_split(handw_digits.data, handw_digits.target, random_state=0)`

`print ("The training input data shape is: ", Xtrain.shape)`

`print ("The training target data shape is: ", ytrain.shape)`

`print ("The testing input data shape is: ", Xtest.shape)`

`print ("The testing target data shape is: ", ytest.shape)`

`model = RandomForestClassifier(n_estimators=1000)`

`model.fit(Xtrain, ytrain)`

`print (model.get_params())`

`ypred = model.predict(Xtest)`

The training input data, target data shape, testing input, target data shape, and the Random Forest Classifier parameters are displayed by the preceding lines.

`→`

`The training input data shape is: (1347, 64)`

`The training target data shape is: (1347,)`

`The testing input data shape is: (450, 64)`

`The testing target data shape is: (450,)`

`{'bootstrap': True, 'class_weight': None, 'criterion': 'gini', 'max_depth': None, 'max_features': 'auto', 'max_leaf_nodes': None, 'min_impurity_decrease': 0.0, 'min_impurity_split': None, 'min_samples_leaf': 1, 'min_samples_split': 2, 'min_weight_fraction_leaf': 0.0, 'n_estimators': 1000, 'n_jobs': None, 'oob_score': False, 'random_state': None, 'verbose': 0, 'warm_start': False}`

Now, the performance metrics of the classifier can be observed for evaluation. The following lines display the classification report:

`from sklearn import metrics`

`print ("\nThe classifier performance metrics are given as follows:")`

`print(metrics.classification_report(ypred, ytest))`

`→`

The classifier performance metrics are given as follows:

`           precision     recall   f1-score   support`

`           0        1.00       0.97      0.99        38`

`           1        1.00       0.96      0.98        45`

`           2        0.95      1.00      0.98        42`

`           3        0.98       0.98      0.98        45`

`           4        0.97       1.00      0.99        37`

`           5        0.98       0.96      0.97        49`

`           6        1.00       1.00      1.00        52`

`           7        1.00       0.96      0.98        50`

`           8        0.94       0.98      0.96        46`

`           9      0.96       0.98      0.97        46`

`   micro avg       0.98       0.98      0.98       450`

`  macro avg       0.98       0.98      0.98       450`

`weighted avg       0.98       0.98      0.98       450`

From the preceding report, the precision, recall, F1 score, and support values are displayed. The support value is the number of samples of true responses that lie in that class. The result shows that the model’s performance is good from the report. To get a better analysis, the confusion matrix can be printed. The following lines of code prints the confusion matrix for the classifier:

`import seaborn as sns; sns.set()`

`from sklearn.metrics import confusion_matrix`

`mat = confusion_matrix(ytest, ypred)`

`sns.heatmap(mat.T, square=False, annot=True, fmt='d', cbar=False)`

`plt.xlabel('target or actual label')`

`plt.ylabel('predicted label');`

`plt.show()`

*[Figure 2.16](#c02.xhtml#fig2_16)* is depicting the plot against the actual label versus predicted labels for Random Forest Classifier model:

![](images/Figure-2.16.jpg)

**Figure 2.16:** Confusion Matrix

# [2.9 Conclusion](#toc.xhtml#s41a)

Supervised learning is an important technique in artificial intelligence. It allows the system to learn from the examples which are annotated or labeled. When an example that is not seen during training is given to the system, it will be able to take the right decision based on the learning. The supervised learning algorithms can be applied to many applications from regression to classification problems. It is very popular among data architects due to the high accuracy achievable using supervised learning algorithms and its vast applicability to the different set of problems. It is used in almost all domains like people analysis, time series market forecasting, marketing and sales, fault diagnosis, healthcare, social media services, and so on. Though very popular, these algorithms cannot be applied to unlabeled data. Another type of machine learning is called unsupervised machine learning that deals with these kinds of problems will be discussed in detail in the next chapter.

# [Points to remember](#toc.xhtml#s42a)

*   Supervised learning algorithms can be applied to annotated data only.
*   Data cleanup and data preparation for the training for pre-processing steps which is important during model development. They allow the model to be built with good accuracy and the right data set.
*   Most of the problems in supervised learning can be mapped to either regression or classification problems.
*   While selecting the supervised learning algorithm one has to carefully look at both advantages and disadvantages of using the algorithm.
*   Among many packages available for machine learning, sklearn is the most popular and widely used package.
*   SVM has a number of applications in the real world. The kernel trick selection is the most important for the performance of SVM.
*   The decision tree algorithm works on the possible outcomes of the decision and finds each path to a conclusion. It is used for specific problems. Random Forest works on multiple single trees and a random sample of training data and provides more accurate results as compared to decision trees.
*   Information Gain and Gini Index are among much available selection criteria for decision trees. One has to choose them based on the application and problem.
*   Performance metrics are a way to benchmark a model and tell how good is it performing.
*   Gradient descent is the most popular optimization technique used in supervised machine learning. A lot of the variants of gradient descent have evolved and each of them serves a unique purpose and has their shortcomings.
*   Loss functions are crucial for the model’s design. A loss function is a measure of how good the model performs to predict the required output.

# [Questions](#toc.xhtml#s43a)

1.  What are the criteria for selecting the kernels in SVM?
2.  Name the different regression and classification-based supervised learning algorithms.
3.  Explain the concepts of the qcost function, loss function, and backpropagation in supervised machine learning?
4.  What are the techniques used for synthesizing the missing data in the given data set?
5.  List the main advantages and disadvantages of supervised machine learning.
6.  Mention the steps involved in data cleanup and data preparation process during modeling of a given problem.
7.  Describe any one classification and regression learning method in detail.
8.  Describe SVM and its applications.
9.  Explain information gain selection criteria in the decision tree algorithm with an example.
10.  List the performance metrics for regression-based supervised machine learning. Explain one of them.
11.  List the performance metrics for classification-based supervised machine learning. Explain one of them.
12.  What is a loss function? Name different types of loss functions.
13.  Describe the confusion matrix. Explain with an example.
14.  Describe AUC-ROC. Explain with a diagram.
15.  Write the pseudo-code for the Random Forest Algorithm.

# [Multiple choice questions](#toc.xhtml#s44a)

1.  **Choose the correct answer** 
    1.  SVM always separates feature space with straight lines.
    2.  More data often leads to the overfitting of the model.
    3.  Regression always uses a linear kernel.
    4.  Backpropagation always gives global minima.
2.  **Choose the correct answer** 
    1.  Handwritten characters can be classified using Random Forest.
    2.  SVM uses kernel trick as the loss function.
    3.  Missing data in the data set is always generated by linear interpolation.
    4.  Cross entropy loss always results in local minima.
3.  **Choose the right answer** 
    1.  Cross entropy can be used for binary and multi-class classification problems.
    2.  F1 Score is best for both balanced and unbalanced class distribution data sets.
    3.  F1 Score is not based on the harmonic mean.
    4.  The specificity of the model is based on precision and recall.
4.  **Choose the right answer** 
    1.  F1 Score considers both False Positives and False Negatives to obtain the score.
    2.  A recall is also called as F1 Score.
    3.  The precision of the model is based on the count of correct positive results predicted by the model to the actual correct results in the data set.
    4.  Accuracy is the metric used to measure the performance of the model.
5.  **Choose the correct answer** 
    1.  The confusion matrix is a matrix of features in the data set.
    2.  Adjusted R-squared is used to determine the performance of the model when new variables are added.
    3.  The R-squared performance metric is better than the Adjusted R-squared performance metric.
    4.  Mean Absolute Error, Mean Square Error, and Root Mean Square Error are the loss functions
6.  **Choose the correct answer** 
    1.  Decision Trees perform better than Random Forest.
    2.  Random Forest uses a forest of decision trees and uses an ensemble method to make a decision.
    3.  Information Index and Gini Index are decision criteria in the decision tree algorithm.
    4.  The depth of the decision tree cannot be controlled, it depends on the algorithm.
7.  **Choose the correct answer** 
    1.  Simple Linear Regression, Multiple Linear Regression, and Logistic Regression are used to predict one independent variable given one or more dependent variables.
    2.  Non-linear Regression is not a type of regression method in supervised machine learning.
    3.  Classification problems do not handle the categorical values in the data set.
    4.  Regression techniques are used to solve data sets with discrete values only.
8.  **Choose the correct answer** 
    1.  The size of the data set is not an important factor during the modeling of any supervised machine learning problem.
    2.  The relation between the features in the data set does not matter during the modeling of any supervised machine learning problem.
    3.  SVM is used to solve both the regression and classification problems.
    4.  Adversarial Debiasing and Prejudice Remover are error mitigation algorithms.
9.  **Choose the correct answer** 
    1.  Supervised machine learning is only applicable to problems in the medical domain.
    2.  Regression imputation and K-Nearest Neighbors (KNN) are used to remove the duplicates in the data set during data cleanup.
    3.  Outliers are beneficial during the learning mechanism.
    4.  Data Integration, Data Transformation, Data Formatting, and Data Reduction methods are applied during data preparation during modeling of supervised machine learning problems.

# [Answers](#toc.xhtml#s45a)

1.  **B**
2.  **a**
3.  **a**
4.  **a**
5.  **b**
6.  **b**
7.  **a**
8.  **c**
9.  **d**

# [CHAPTER 3](#toc.xhtml#c03)

# [System Analysis with Machine Learning/Un-Supervised Learning](#toc.xhtml#c03)

We might have encountered questions such as “*why unsupervised learning?*”, “*what is it all about?*”, and “*how different it is as compared to the supervised learning algorithms and methods?*”.

In real-world scenarios, many times labeled data may not be available. Data patterns and data format is also not well defined and available to us. In these cases, we go for the unsupervised learning mechanisms and algorithms to solve the mystery.

The Fashion-MNIST dataset is an example mapped to the labeled classes and can easily be a reference for the supervised learning algorithms. But this same data set can be used without the “*labels*” for unsupervised learning mechanisms and algorithms.

As explained in the earlier section, machine learning is defined as one of the branches of computer science in which the algorithms learn from the data or data sets available to them. Most of the machine learning algorithms are designed based on these algorithms and data sets. These predominant algorithms work on labeled data. But there are some algorithms that work without the labeled data. Using unlabeled data, the system can extract the patterns and use them for interpretation. Using unlabeled data is a bit challenging and tricky as compared to simply labeled data sets. Classifying these into groups of similar character or similar nature without the labels is one of the methods used.

# [Structure](#toc.xhtml#s46a)

In this chapter, we will discuss the following topics:

*   Introduction and architecture of unsupervised machine learning
*   Methods and steps of data preparation 
    *   StandardScaler
    *   MinMaxScaler
    *   RobustScaler
    *   Normalizer
*   Clustering algorithms and techniques 
    *   K-means
    *   Hierarchical clustering
    *   DBSCAN
    *   HDBSCAN
*   Other algorithms 
    *   **Dimensionality Reduction** 
        *   Principal component analysis (PCA)
        *   Singular value decomposition (SVD)
        *   Independent component analysis (ICA)
        *   T-distributed stochastic neighbor embedding (t-SNE)
        *   Dictionary learning
*   Error minimization 
    *   Distance computing
    *   Threshold limit
    *   Log loss
    *   Euclidian distance
*   Examples and samples 
    *   Some samples with examples

# [Objectives](#toc.xhtml#s47a)

After studying this chapter, you should be able to:

*   Understand the mechanism of unsupervised machine learning.
*   Various algorithms in unsupervised learning including the clustering mechanisms.
*   Various steps of error minimization.
*   Understand few learning mechanisms in unsupervised machine learning.
*   Threshold selection mechanisms and methods.
*   Performance of the learning mechanisms.
*   Examples or use cases of unsupervised machine learning.

# [3.1 Introduction and architecture of unsupervised machine learning](#toc.xhtml#s48a)

In unsupervised learning, the training data is “*unlabeled*”. The analogy we can draw here can be that of “*any system which learns without a teacher*”. We have to also keep in mind that this doesn’t mean that it is a self-learning model.

Most of the unsupervised algorithms use different clustering techniques which will be described in the later section of the chapter. The mechanism for error minimization would also be provided.

*Yann LeCun,* one of the pioneers in the area of deep learning, has beautifully explained what is unsupervised learning. He states that “*most of the daily human learning activities and animal learning*” are based on unsupervised learning. In these learnings, there is no predetermined or labeled data.

As compared to supervised learning, unsupervised learning has its advantages, especially where large unlabeled data sets are involved. In such cases, unsupervised learning stands out. As we know that instead of working on the labeled datasets, unsupervised learning works by learning the underlying structure of the data and how it has been trained on. By either using representation-based learning or by a smaller set of parameters, unsupervised learning can identify and classify a set of patterns in the data set. With these identified patterns, one can easily classify the clusters/groups with similar characteristics:

![](images/Figure-3.1.jpg)

**Figure 3.1:** Architecture of sample unsupervised learning

The preceding diagram is a simple architecture of the unsupervised learning mechanism. This diagram explains the various components that are required to build and carry out the execution of the unsupervised learning algorithm. Input data is unlabeled as we are dealing with unsupervised learning. Data preprocessing is the step where we clean out the data for any out-of-bound values. Once a particular algorithm is selected, it is fed with the input data, the output is compared with the actual output using the loss functions, weights are adjusted so that data post-processing doesn’t have any malicious data feedback. Once all these are run multiple times (with a number of epochs) the output is compared for accurate results. The better the accuracy, the good the algorithm is performing.

A generic example where unsupervised clustering algorithms are used: Assume that you are running your online shopping website. The website is recently launched and has a few thousand customers. You want to do a study of the customers who are only purchasing apparel, the ones who are purchasing only books, and the ones who are purchasing only stationery items, and so on. In such a situation, with all the user’s historical data (making sure the privacy is not revealed), the unsupervised algorithms can be used to create each cluster for each purchase type. For example, there are several clusters based on purchases of apparel, books, stationery, and so on. Based on this, the user buying pattern can be observed over a period of time.

With this kind of approach, many of the problems which were not solvable earlier will be solved. Unsupervised learning provides with the identification of similarities in both historical data and future data. This helps in solving many of the earlier complex problems and challenges in the data science category.

Some of the algorithms that will be described and discussed in detail in the later sections of this chapter are as follows:

*   Various clustering techniques and algorithms.
*   Other algorithms and methodologies including dimensionality reduction methods.

Advantages of unsupervised learning:

*   Works on large datasets.
*   Complex machine learning problems can be solved using unsupervised learning.
*   Using the dimensionality reduction technique, the high-dimensional representations help in reducing a large number of features into only a few, by summarizing only the essential characteristics.
*   Using unsupervised learning, topic extraction from large text-based data sets can be achieved easily.
*   These algorithms are best suited for the exploratory type of setting, for example, a better understanding of the data.

Disadvantages of unsupervised learning:

*   Unsupervised learning is not suitable for simple tasks and smaller datasets.
*   Evaluating the algorithm whether any learning happened or not is difficult.
*   Since no labeled data is used, we are unsure of what will be the output.
*   Sometimes it is a challenge to predict whether the model did well or not.
*   Since this space is still evolving, it takes some time to come up with new algorithms.

# [3.2 Data preparation methods and steps](#toc.xhtml#s49a)

We need to have correlated data. Data should have commonalities and patterns to proceed further. In most of the data samples, the data may contain outliers of out-of-range values, out of bounds data patterns and mismatched data, and so on. This will have constraints on the data length, and also will have some constraints on “*outliers*”. In many cases, instead of taking data directly as it is, we may have to do some clustering beforehand. In unsupervised learning, transformation in the data is important along with the right hyperparameter tuning.

# [3.2.2 Data preprocessing and scaling](#toc.xhtml#s50a)

It is always a best practice to adjust the features in unsupervised learning so that the data representation is suitable for such algorithms. The `sklearn.preprocessing` package is the most predominantly used utility for such.

Generally, most of the learning algorithms get the advantage of standardization of the data set. With standardization, the outliers in the data set will be highlighted if any.

The usage and application of various scalers, transformers and normalizers on a data set containing such outliers is a common and standard practice by any ML practitioner. Sometimes the unsupervised algorithms are used as preprocessing steps for learning a new representation of data. This not only helps the supervised algorithms but also helps in the improvement of the accuracy of supervised algorithms along with less time consumption and reduced memory for holding the data.

The original data can be plotted by making use of the following:

*   StandardScaler
*   MinMaxScaler
*   RobustScaler
*   Normalizer

# [3.2.2.1 StandardScaler](#toc.xhtml#s51a)

The following is the scikit library function for `StandardScaler` along with the class definition and various sample parameters:

`sklearn.preprocessing.StandardScaler`

`class sklearn.preprocessing.StandardScaler(*, copy=True, with_mean=True, with_std=True)`

Using this preprocessing technique/function, one can standardize the features by removing the mean and scaling to unite the variance values. The standard score of any sample x is calculated as follows:

*z = (x - u) / s*

Where, u = Mean of the training samples

x = Sample

s = Standard deviation of the training sample

Sometimes the relevant statistical methods are applied to the sample on the training set. It can be as simple a technique as **centering** or sometimes **scaling** as explained here. These techniques should be applied independently to each feature and should not be combined.

The following are the various math formulae used for standardization, mean, and standard deviation calculations:

![](images/Figure-3.2.jpg)

**Figure 3.2:** Formulae for Standardization, Mean, and Standard Deviation

In the preceding example, following are the various variables used:

μ = Mean of any dataset

σ = Standard deviation of the dataset

N = Number of samples or sample size

x = X = Matrix containing data values (row/column)

z = Standardization

The core idea is to standardize or normalize the features/variables/columns of X, individually and before applying any machine learning model such that where values of μ = ٠ and σ = ١. What this means is by applying `StandardScaler()`, this function will normalize the features of each column of the X values individually so that each column/feature/variable will have μ = ٠ and σ = ١.

Standardization of any data set is the most commonly used requirement and technique in any ML estimator.

# [Code sample](#toc.xhtml#s52a)

The following code is a simple explanation and steps to carry out and apply the standard scaler method. In this method, the sample data in the array or matrix form is taken and applied with the standard scaler method to transform this into a normalized data format:

![](images/Figure-3.3.jpg)

**Figure 3.3:** Code sample for StandardScaler

# [3.2.2.2 MinMaxScaler](#toc.xhtml#s53a)

The `MinMaxScaler()` Scikit library function can be applied to any data set directly to normalize the input variables. `MinMaxScaler` instance is defined with some of the well-known default hyperparameters. Once this is done, the `scaler.transform()` function can be applied to the dataset to create the final transformed version of the dataset.

The `minmaxscaler()` shifts the data such that all the features are exactly between the range of 0 and 1. When MinMaxScaler is applied such that for each value in a feature, MinMaxScaler subtracts the minimum value in the feature and then divides by the range. This range is the difference between the original maximum and original minimum. MinMaxScaler preserves the original shape of the distribution intact.

For any two-dimensional data set, the whole data set is created by the x-axis between 0 and 1 and the y axis between 0 and 1. Finally, the normalizer can be applied for rescaling so that scaling of the data points for the feature vector can be done.

The following are the scikit library functions for MinMaxScaler along with a class definition and various sample parameters:

`sklearn.preprocessing.MinMaxScaler`

`class sklearn.preprocessing.MinMaxScaler(feature_range=(0, 1), *, copy=True)`

The following formula is used to depict the Xnorm value. Xnorm can be calculated as the difference between:

![](images/Figure-3.4.jpg)

**Figure 3.4:** Formula for Min-Max Scaling

The following is the code sample explaining the MinMaxScaler Scikit library in detail:

![](images/Figure-3.5.jpg)

**Figure 3.5:** Code sample for MinMaxScaler

# [3.2.2.3 RobustScaler](#toc.xhtml#s54a)

`RobustScaler` transforms the feature or feature vectors by subtracting the median and then dividing it by the interquartile range (approx. 75% value to 25% value). RobustScaler does not scale the data into a pre-determined interval like how MinMaxScaler did earlier. Generally, the range of values for the Robust scaler after applying on each feature will be larger as compared to the MinMaxScaler.

The following are the scikit library function for RobustScaler along with a class definition and various sample parameters:

`sklearn.preprocessing.RobustScaler`

`class sklearn.preprocessing.RobustScaler(*, with_centering=True, with_scaling=True, quantile_range=(25.0, 75.0), copy=True)`

The following is the code sample explaining the RobustScaler Scikit library in detail:

![](images/Figure-3.6.jpg)

**Figure 3.6:** Code sample for RobustScaler

RobustScaler removes the median and scales the data according to the quantile range and sometimes defaults to **Interquartile Range** (**IQR**). This IQR is a measure of where the "*middle fifty*" is in a data set. Also, sometimes this is the IQR range between the 1st quartile (25th Quantile) and the 3rd quartile (75th Quantile). This measure is also, where the bulk of values lie. This is one of the reasons why it is preferred over many other measures of spread especially for performance and score measures:

![](images/Figure-3.7.jpg)

**Figure 3.7:** Sample range of values for Robust Scaler example

The preceding figure shows the sample range of values that fall under the IQR with Q1 and Q3 values. This can be assumed to be for *n=10* value samples as depicted previously.

The interquartile formula can be defined as the “*difference between the third quartile and first quartile*”. In simple terms, this can be computed as follows:

**IQR = Q3 – Q1. (In the preceding example, 77 – 64 = 13)**

Various value ranges can be defined as from Q1 to Q3.

Where, Q1 is the "*center or middle*" value in the first half of the ordered data set.

Q2 can be the median value in the set (assuming you have considered mean/median/mode).

Finally, Q3 is the "*middle*" value in the second half of the ordered data set.

# [3.2.2.4 Normalizer](#toc.xhtml#s55a)

The following are the scikit library function for Normalizer along with a class definition and various sample parameters:

`sklearn.preprocessing.Normalizer`

`class sklearn.preprocessing.Normalizer(norm='l2', *, copy=True)`

Normalization works on the rows of the matrix and not on columns.

Normalization is done in such a way that each sample row of the data matrix with at least one non-zero component is rescaled independently of other samples so that its norm equals one. Generally, either L1 or L2 normalization is used. All these norms are defined for clarity in the following note:

**Note: L1 Norm:** This is also known as the Manhattan Distance or Taxicab norm. The L1 norm is calculated as the sum of the absolute values of the vector. (It is assumed that these vector values are in space). This L1 norm is the most natural way of measuring the distance between vectors, which is the sum of the absolute difference of the components of the vectors. It is also made sure in this norm that all the components of the vector are weighted equally.

**L2 Norm:** This is one of the most popular norms that is used in practice. This is also known as the Euclidean norm. This is measured as the shortest distance to go from one point to another. The L2 norm is calculated as the square root of the sum of the squared vector values.

**Manhattan Distance:** This is a distance metric between two points in an N-dimensional vector space. It is the sum of the lengths of the projections of the line segment between the points onto the coordinate axes. In very simple terms, this is the absolute difference between the measures in all dimensions of two points in space.

The L1 norm can be calculated and is depicted in *[figure 3.8](#c03.xhtml#fig3_8)*.

The following diagram explains X, Y coordinates where X and Y values are plotted in a graph. In this graph, the X value is assumed to be ‘5’ and the Y value is assumed to be ‘7’.

![](images/Figure-3.8.jpg)

**Figure 3.8:** L1 Norm calculation using two vector values

The preceding equation signifies that L1 Norm can be calculated as an absolute value of the X and Y values as plotted previously. “X” and “Y” are the feature values respectively.

![](images/Figure-3.9.jpg)

**Figure 3.9:** L2 Norm calculation using two vector values

The preceding equation signifies the square root of the absolute value of the L2 norm. Here, the “X” and “Y” axis represents the feature variables. L2 norm is calculated as the square root of the sum of the squared vector values.

**Note:** Explanation of the other norms like L0 and L∞:

**L0 Norm:** This is not a norm. As this doesn’t satisfy the conditions that a norm should have. This is used to depict the number of non-zero elements in a vector.

**L∞ Norm:** This norm gives the largest magnitude among each element of a vector. But it is rarely used.

The following is the code sample explaining the NormalizerScaler Scikit library in detail:

![](images/Figure-3.10.jpg)

**Figure 3.10:** Code sample for normalizer

# [3.3 Clustering techniques](#toc.xhtml#s56a)

This can be defined as a task of grouping or partitioning the data set into groups called “clusters”. The main aim of this data partitioning or splitting is such that similar data points are grouped into one cluster and different points into different clusters. This grouping is also called “*cluster analysis*”. As explained earlier, the same characteristic objects/points are grouped into one cluster and others into other clusters based on how similar they are. These numbers of groups are decided by the algorithms we choose. These clustering methods are used in data mining and statistical data analysis techniques.

There are two types of clustering as follows:

1.  Flat clustering
2.  Hierarchical clustering

The following are sub-divided into, Hard and Soft clustering as explained:

1.  **Hard Clustering**: In a complete sense, either a data point belongs to a cluster or not. There is no in-between state or step to further classify this.
2.  **Soft Clustering**: Each data point will be placed in a separate cluster, based on the probability or likelihood of that data point that the respective cluster is assigned.

The main requirements that a clustering algorithm should satisfy are as follows:

*   Scalability aspects.
*   How to deal with the different types of attributes.
*   How to discover clusters with arbitrary shapes and sizes.
*   No need for complete domain-based knowledge is required while choosing the clustering techniques or methods.
*   One has to have the knowledge and ability to deal with noise and outliers if any.

In statistical terms, clustering is defined as the task of dividing the population or various data points into a number of groups or clusters such that these data points in the same group are similar to the other data points in the same group and dissimilar as compared to the other data points in other groups.

Some of the well-known clustering use cases are as follows:

*   Clustering of similar documents.
*   Cluster customers based on various features and characteristics.
*   Market segmentation for ease of analysis.
*   Identify similar physical groups.
*   Classifying playing groups into clusters based on their values, goals, and scores.

| **Algorithm/Method Name** || **Parameters** || **Scalability** || **Use cases** || **SciKit Library** || **Metric Used** |
| --- | --- | --- | --- | --- | --- |
| **K-Means** || Number of clusters || Very large n\_samples, medium n\_clusters with Minbatch || Used for general purposes || *from sklearn.cluster import K-Means* || Distance between the points |
| **Hierarchical clustering (also called ward clustering)** || Number of clusters or distance as a threshold value || Large n\_samples and n\_clusters || Many clusters ||  || Distance between the points |
| **DBSCAN** || Neighborhood size || Very large n\_samples, medium n\_clusters || Non-flat geometry or uneven cluster sizes ||  || Distance between the nearest points |
| **t-SNE** || Generally, it is categorized as the clustering algorithm. But in some cases, it is used as the conversion mechanism for similarities between data points to joint probabilities and is also used for minimizing the divergence values (defined by *Kullback-Leibler*) between the joint probability values of the low-dimensional data and the high-dimensional data. |

**Table 3.1:** Table for clustering comparison

# [3.3.1 K-Means](#toc.xhtml#s57a)

K-Means is one of the most popularly used unsupervised algorithms. This algorithm is used to classify the unlabeled training data into distinct groups. As explained earlier, these are clusters with similar or near similar characters:

![](images/c03eq-1.jpg)

In the preceding equation, the K-Means algorithm divides a set of N samples X into K disjoint cluster C. Where, Xi-µj is the Euclidean distance between Xi and µj.

*“||” indicates the “Square of values”.*

*'µj’ is the mean of the samples in the cluster.*

*‘i’ is the number of data points in the ith cluster.*

*‘n’ is the number of cluster centers.*

Following is the prototype of the K-Means algorithm and class from the sklearn package with a code sample. The following is the library function along with its parameters:

**Scikit Learn K Means Clustering**

 
| **The class defined** || **from sklearn.cluster import K-Means** |
| --- | --- |
| Various parameters of the method/function passed to this class || *KMeans(copy\_x = True, init='K-means', max\_iter=300, n\_cluster=6, n\_init=10, n\_jobs=1, precompute\_distance='auto', random\_state=None, tol=0.0001, verbose=0)* |

**Table 3.2:** K-Means library function

`kmeans = KMeans (n_cluster=6)`

`Kmeans.fit(data[0])`

To print the centroids of the cluster:

`kmeans.cluster_centers_`

The following table provides the various functionalities for the K-Means algorithm along with parameter descriptions:

 
| **Method Name** || **Description** |
| --- | --- |
| KMeans || First, this library method has to be imported from the Scikit learn library using the following code:*from sklearn.cluster import KMeans* |
| KMeans(n\_cluster = <Numeric Value>) || This function is used to initialize the number of clusters and can also be referred to as the “K” value. |
| KMeans.fit(data\[0\]) || The function takes the input as “data” and fits the model according to the given training data. |
| *KMeans(copy\_x = True, init='K-means', max\_iter=300, n\_cluster=6, n\_init=10, n\_jobs=1, precompute\_distance='auto', random\_state=None, tol=0.0001, verbose=0)* || The K-Means takes various input values as explained in the function itself. The main key point to remember is that this function has to be initialized with init=’K-means’ and maximum iterations can be in the range of 100-300. “n\_cluster = <number of clusters>”. |
| *kmeans.cluster\_centers\_* || kmeans.cluster\_centers\_ is an attribute of the class sklearn.cluster.KMeans and not a function. |

**Table 3.3:** Table for the methods for K-Means

The following pointers provide some steps and tips on how to select the best parameter values for the “*K-Means*” algorithm:

*   Choose a number of clusters "K" value before kick-starting the algorithm execution. This step is further explained in detail later in this section.
*   In the beginning, randomly assign each point to a cluster.
*   If you observe that the clusters stops changing or until the cluster stop changing then repeat the following sub-steps: 
    *   Cluster centroid can be computed by taking the mean vector of points from each cluster.
    *   Now data points can be assigned based on how close they are to the centroid of each cluster.
    *   The points can be assigned initially to the nearest centroid and later modified accordingly.

**Choosing the "K" value**: Selecting the “K” value is not an easy task and there is no easy way to do so. This is one of the crucial steps and general practice is to use the "**Elbow**" method:

1.  Compute the sum of squared for some values of "K". (for example, 2,4,6,8, etc.)
2.  With SSE calculated with the trial-error method, try to use the value either by comparing with the Elbow method or with the least “K” value.

**The Elbow method explained:**

This method is used to select the number of clusters by fitting the model with a range of values for K. This is called as “**Elbow**” method because in the line chart that is drawn, which is the point of inflection on the curve resembles an arm in the elbow shape. If the curve is in this shape, it is a good indication that the underlying model fits the best at that point of indication.

The following table provides the Elbow method along with the description of various parameter values and examples:

 
| **Method Name** || **Description** |
| --- | --- |
| **Elbow method** || Import the two library functions:`from sklearn.cluster import KMeans``from sklearn.datasets import make_blobs``# Import and KMeans and make_blobs``(Generate isotropic Gaussian blobs for clustering)``# Import KElbowVisualizer for selecting``# the best elbow value i.e., optimal``# (continued) number of clusters for K-means clustering``from yellowbrick.cluster import KElbowVisualizer` |
| Generate Synthetic Data using the “make\_blobs()” method || `# Generate simple synthetic dataset with 6 random clusters``X, y = make_blobs(n_samples=1000, n_features=12,`` centers=6, random_state=42)``#This function takes various inputs like number of #samples, “n_samples”, number of features as #“n_features”, number of centers as “centers” and # #finally “random_state” variable.` |
| KMeans and KElbowVisualiser instantiation || `Now instantiate the following:``model = KMeans()``visualizer = KElbowVisualizer(model, k=(4,12))` |
| Fitment and Visualizing of the final outcome. || `# Instantiate the clustering model and visualizer``# for the final curve``visualizer.fit(X)``# Fit the data to the visualizer``visualizer.show() # render and display the graph` |

**Table 3.4:** Table for the Elbow method in K-Means

In the following graph, the "elbow" is as highlighted. The following graph output is what is depicted for “centers=6”:

![](images/Figure-3.11.jpg)

**Figure 3.11:** Elbow method graph showing “centers=6”

# [3.3.2 Hierarchical clustering](#toc.xhtml#s58a)

Hierarchical clustering is one of the algorithms which works on building the hierarchy of clusters.

This algorithm builds nested clusters by merging or splitting them successively. This hierarchy of clusters is represented as a tree (or sometimes known as a dendrogram). Once this is represented, the root of the tree which is unique in nature is a cluster that gathers all the samples including the leaves of the clusters which will have only one sample. This algorithm starts with all the data points assigned to a cluster belonging to their own. Then the two nearest clusters are merged into the same cluster. Finally, this algorithm terminates when there is only a single cluster left.

The main idea of hierarchical clustering is to make the dendrogram. With a single cluster, work your way down such that to see the different combinations of clusters until having a number of clusters equal to the number of observations. Finally, the dendrogram itself helps in finding the best clustering configuration.

This clustering technique can be divided into two types:

1.  **Agglomerative**
    
    ` sklearn.cluster.AgglomerativeClustering`
    
    The following table provides the various parameters and default values for `AgglomerativeClustering` class and scikit library function:
    
     
    | **The class defined** || **class sklearn.cluster.AgglomerativeClustering** |
    | --- | --- |
    | **Various parameters of the method/function passed to this class** || `class sklearn.cluster.AgglomerativeClustering(n_clusters=2, *, affinity='euclidean', memory=None, connectivity=None, compute_full_tree='auto', linkage='ward', distance_threshold=None)` |
    
    **Table 3.5:** Table for Agglomerative Clustering
    
    The following table explains the various options and a detailed description of the various parameter values along with the default values that can be passed onto `AgglomertiveClustering`:
    
     
    | **Method Name** || **Description** |
    | --- | --- |
    | **Agglomerative Clustering method** || This method recursively merges the pair of clusters that minimally increases a given linkage distance.`sklearn.cluster.AgglomerativeClustering`This function has various parameters like the number of clusters as “`n_cluster`”, affinity to choose “`Euclidean`”, memory, connectivity, `compute_full_tree,` and linkage along with `distance_threshold`. |
    | `fit_predict(self, X, y=None)` || This method is used to fit the hierarchical clustering from features or distance matrix and then return the cluster labels. |
    | `get_params(self, deep=True)` || This function is used to get parameters for this estimator. |
    | `set_params(self, **params)` || This function is used to set the parameters of this estimator. |
    
    **Table 3.6:** Table for methods of Agglomerative Clustering
    
2.  **Divisive (**This is used in the **Dendrogram** method**)**
    
    This is a top-down approach where all the observations are started in one cluster and then iteratively split as we move down the hierarchy. This method is quite slow and statistically inaccurate (may have more than one solution), as a large number of clusters are split recursively constantly. The following are the various SciPy and Scikit learn library modules used to plot the dendrograms:
    
    `from matplotlib import pyplot as plt`
    
    `from scipy.cluster.hierarchy import dendrogram`
    
    `from sklearn.datasets import load_iris`
    
    `from sklearn.cluster import AgglomerativeClustering`
    

In the common practice, first, the dimensionality reduction methods like PCA are applied and then clustering is performed for best results. For larger data sets where maximum accuracy is not the main factor and only the faster computation is expected, then PCA and dendrogram methods are applied alternatively.

Dendrograms are plotted using `matplotlib` library and using `Agglomerative Clustering` method:

![](images/Figure-3.12.jpg)

**Figure 3.12:** Sample dendrogram plotted for Iris data set with three levels.

# [3.3.3 Density-based spatial clustering of applications (DBSCAN)](#toc.xhtml#s59a)

The DBSCAN algorithm is used for separating the clusters based on the density values, especially by separating the clusters of high-density by areas of low-density clusters. For this algorithm, clusters of any shape can be used for analysis (as limited to K-Means, where only the convex-shaped clusters are used). The samples from the high-density areas are chosen for DBSCAN as core samples. Any cluster is a group of core samples (using distance measure criteria). There are two main parameters used in this algorithm, "`min_samples`" and "`eps`", which are used for defining density. These two parameters can (`min_samples` or `eps`) define the density necessary to form a cluster based on the higher or lower values.

`sklearn.cluster.DBSCAN`

The following table provides the class and scikit library function for DBSCAN:

 
| **The class defined** || **class sklearn.cluster.DBSCAN** |
| --- | --- |
| **Various parameters of the method/function passed to this class** || `class sklearn.cluster.DBSCAN(eps=0.5, *, min_samples=5, metric='euclidean', metric_params=None, algorithm='auto', leaf_size=30, p=None, n_jobs=None)` |

**Table 3.7:** Table for DBSCAN

The following table provides the various parameters along with default values of DBSCAN:

 
| **Method Name** || **Description** |
| --- | --- |
| DBSCAN method || This method or function is used to perform clustering from vector array or distance matrix.*‘eps’* default value is 0.5 and is the maximum distance between two samples.*‘min\_samples’ default is 5*.*‘metric’* default is ‘euclidean’ and is used for calculating the distance between instances in a feature array.*'metric\_params'* default=None*algorithm{‘auto’, ‘ball\_tree’, ‘kd\_tree’, ‘brute’}, default=’auto’.* This is used to compute the point-wise distances and find the nearest neighbors.*‘leaf\_size’*, default=30Leaf size passed to BallTree or cKDTree.*‘p’*, default=NoneMinkowski metric is used to calculate the distance between points.*‘n\_job’*, default=None |
| `fit(self, X,y,sample_weight)` || Takes the training samples X and target values y and returns self after fitting the model according to the given training data. |
| `fit_predict(self, X,y,sample_weight)` || The function is used to perform the DBSCAN clustering from features or distance matrix and finally return the cluster labels. |
| `get_params(self, deep=True)` || The function is used to get parameters for this estimator. |
| `set_params(self, **params)` || This function is used to set the parameters of this estimator. |

**Table 3.8:** Table for methods for DBSCAN

# [3.4 Other algorithms and methodologies](#toc.xhtml#s60a)

# [(Dimensionality reduction techniques)](#toc.xhtml#s61a)

The curse of dimensionality is one of the most common and known problems in machine learning. With these problems, the algorithms cannot train efficiently and effectively on the data. The other major reason is the sheer amount of data size in these examples. With this large set of data, huge compute power will be invested in training. Instead of this, data dimension can be intelligently reduced without losing the original intention. This approach or method is the “*Dimensionality Reduction*” technique. Over a period of last several years, this space has seen a lot of algorithms and methods. The most popular and various dimensionality reduction techniques are discussed and explained in the upcoming sections of this chapter.

# [3.4.1 t-Distributed stochastic neighbor embedding (t-SNE)](#toc.xhtml#s62a)

`sklearn.manifold.TSNE`

The preceding function is a class method for TSNE.

The following table describes the various parameters passed on to the class TSNE along with the default values:

 
| **The class defined** || **class sklearn.manifold.TSNE** |
| --- | --- |
| **Various parameters of the method/function passed to this class** || `class sklearn.manifold.TSNE(n_components=2, *, perplexity=30.0, early_exaggeration=12.0, learning_rate=200.0, n_iter=1000, n_iter_without_progress=300, min_grad_norm=1e-07, metric='euclidean', init='random', verbose=0, random_state=None, method='barnes_hut', angle=0.5, n_jobs=None)` |

**Table 3.9:** Table for manifold.t-SNE

t-SNE is a non-linear dimensionality reduction technique used for visualizing high-dimensional data. The data dimensionality reduction can be achieved by modeling all the high-dimensional data points into 2- or 3-dimensional space by placing the similar points closer and dissimilar points farther away. This is possible by using the probability distributions, one in the higher dimensional space and the other in the lower dimensional space. Again, the similar probabilities are in the higher dimensional space and dissimilar points are in the lower dimensional space. In some cases, t-SNE can be considered as a tool to visualize the high-dimensional data.

A better practice is to apply PCA before applying t-SNE to reduce the number of dimensions to a reasonable amount, especially if the number of features is very high. This method helps in suppressing the noise and increase the speed of computation of the pair-based distances between the samples.

 
| **Method Name** || **Description** |
| --- | --- |
| `Sklearn.mainfold.TSNE` || This library or class function is used to visualize the high dimensional data.`n_components`*,* optional (default: 2)This is used for the dimension of the embedded space.`perplexity, optional (default: 30)`The general practice is to use a value between 5 and 50.`early_exaggeration, optional (default: 12.0)`This value is used to control how the tight natural clusters are in the original space.`learning_rate, optional (default: 200.0)`This value of t-SNE will be usually in the range \[10.0 to 1000.0\]. Better to have an optimal value and refrain from using too high or too low values.`n_iter, optional (default: 1000)`This indicates the maximum number of iterations for the optimization.`n_iter_without_progress, optional (default: 300), Use this value in terms of multiples of 50.``min_grad_norm, optional (default: 1e-7)`This value is used to check if the gradient norm is below this or not, if it is below, the optimization will be stopped.**Other options used are***metricstring or callable, optional*`initstring or numpy array, optional (default: “random”)``verboseint, optional (default: 0)`Verbosity level.`random_state, RandomState instance, default=None``method (default: ‘barnes_hut’)``angle (default: 0.5)``n_jobs or None, optional (default=None)` |
| `fit(self, X, y, sample_weight)` || Takes the training samples X and target values y and returns self after fitting (in the embedded space) the model according to the given training data. |
| `fit_transform(self, X, y=None)` || The function is used to fit X into an embedded space and return the transformed output. |
| `get_params(self, deep=True)` || The function is used to get the parameters for this estimator. |
| `set_params(self, **params)` || This function is used to set the parameters of this estimator. |

**Table 3.10:** Table for Methods for t-SNE

# [3.4.2 Principal Component Analysis (PCA)](#toc.xhtml#s63a)

PCA is one of the dimensionality reduction techniques.

The main purpose of the PCA is to decrease the complexity of the given model. While simplifying the model, all the relevance and performance should be retained, PCA helps in achieving this. In many cases where huge data sets are involved, these data sets will have hundreds of variables and features, but by extracting only a few of the independent variables we were in a position to explain most of the variance using PCA.

PCA helps in the analysis and extraction of linear composites of the observed variables. Sometimes using factor analysis which is based on the formal model by predicting the observed variables from the theoretical knowledge and latent factors, these extractions can be achieved. In distinguishable patterns and factor analysis, PCA helps in achieving the maximum variance and maximum-shared variance while constructing the latent variables.

**Advantages of PCA:**

*   Maximization of variance.
*   Helps in determining the direction of the maximal variance closely.
*   Independent variable variance in accordance with the change in the other dependent variables.

The following are the various scikit library functions for PCA. Each of these library functions is explained in detail along with the parameters passed and default values in the following sections:

`sklearn.decomposition.IncrementalPCA`

`sklearn.decomposition.KernelPCA`

`sklearn.decomposition.MiniBatchSparsePCA`

`sklearn.decomposition.PCA`

`sklearn.decomposition.SparsePCA`

# [3.4.2.1 Decomposition incremental PCA](#toc.xhtml#s64a)

The following is the IncrementalPCA scikit library function, the tables explain in detail what are the parameters passed, subsequently:

`sklearn.decomposition.IncrementalPCA`

The following table shows the IncrementalPCA library function with various parameters passed along with the default values:

 
| **The class defined** || **class sklearn.decomposition.IncrementalPCA** |
| --- | --- |
| **Various parameters of the method/function passed to this class** || `class sklearn.decomposition.IncrementalPCA(n_components=None, *, whiten=False, copy=True, batch_size=None)` |

**Table 3.11:** Table for IncrementalPCA

This is the linear dimensionality reduction method which uses singular value decomposition of the data. Only the most significant singular vectors are kept to project the data to a lower-dimensional space (**Singular value decomposition** (**SVD**)).

This algorithm allows to sparse the input and is much more memory efficient as compared to PCA.

The following table explains the method along with default values for IncrementalPCA library function:

 
| **Method Name** || **Description** |
| --- | --- |
| *IncrementalPCA* || First, this library method has to be imported from the Scikit learn library as mentioned. Various parameters are as follows:*n\_componentsint or None, (default=None),* Number of components to have.*whitenbool, optional,* The default value is ‘*False’.**copybool, (default=True),* If false, the X value will be overwritten.*batch\_sizeint or None, (default=None),* The number of samples to use for each batch. |
| fit(self, X, y) || Takes the training samples X and target values y and returns self after fitting the model according to the given training data. (Using mini-batches of size batch size) |
| `fit_transform(self, X, y=None)` || Fit to data, then transform it. |
| `get_covariance(self)` || Compute data covariance with the generative model. |
| `get_params(self, deep=True)` || Get parameters for this estimator. |
| `get_precision(self)` || Compute data precision matrix with the generative model. |
| `inverse_transform(self, X)` || Transform data back to its original space. |
| `partial_fit(self, X[, y, check_input])` || Incremental fit with X. |
| `set_params(self, **params)` || Set the parameters of this estimator. |
| `transform(self, X)` || Apply dimensionality reduction to X. |

**Table 3.12:** Table for methods for IncrementalPCA

# [3.4.2.2 Decomposition kernel PCA](#toc.xhtml#s65a)

The following is the decomposition Kernel PCA scikit library function. This is one of the PCA algorithms:

`sklearn.decomposition.KernelPCA`

The following table explains the various parameters and default values that are passed to the decomposition Kernel PCA method:

 
| **The class defined** || **sklearn.decomposition.KernelPCA** |
| --- | --- |
| **Various parameters of the method/function passed to this class** || `class sklearn.decomposition.KernelPCA(n_components=None, *, kernel='linear', gamma=None, degree=3, coef0=1, kernel_params=None, alpha=1.0, fit_inverse_transform=False, eigen_solver='auto', tol=0, max_iter=None, remove_zero_eig=False, random_state=None, copy_X=True, n_jobs=None)` |

**Table 3.13:** Table for decompositionKernelPCA

The following table explains the various default values and parameters that are passed on to the decomposition Kernel PCA method:

 
| **Method Name** || **Description** |
| --- | --- |
| *KernelPCA* || First, this library method has to be imported from the Scikit learn library as mentioned. The various parameters are as follows:*n\_components, default=None,* Number of components.*Kernel:“linear” | “poly” | “rbf” | “sigmoid” | “cosine” | “precomputed”,* Default=”linear”.*gamma, default=1/n\_features (*Kernel coefficient for rbf, poly and sigmoid kernels). This can be ignored for the other kernels.*degree, default=3,* Degree for poly kernels. Ignored by the other kernels.*coef0, default=1,* Independent term in poly and sigmoid kernels. Ignored by the other kernels.*kernel\_param:* This is mapping of a string to any, *default=None**alpha, default=1.0,* Hyperparameter of the ridge regression.*fit\_inverse\_transform, default=False,* Learn the inverse transform for non-precomputed kernels. (i.e., learn to find the pre-image of a point).*eigen\_solver\[‘auto’|’dense’|’arpack’\], default=’auto’*tol, default=0, Convergence tolerance for arpack. If 0, the optimal value will be chosen by arpack.*max\_iter, default=None,* Maximum number of iterations for arpack.*remove\_zero\_eig, default=False**random\_state,* RandomState instance, default=None*copy\_X, default=True**n\_jobsint or None, optional (default=None)* |
| `fit(self, X, y)` || Takes the training samples X and target values y and returns self after fitting the model according to the given training data. |
| `fit_transform(self, X, y=None)` || Fit model from data in X and transform X. |
| `get_params(self, deep=True)` || Get parameters for this estimator. |
| `inverse_transform(self, X)` || Transform data X back to its original space. |
| `set_params(self, **params)` || Set the parameters of this estimator. |
| `transform(self, X)` || Transform data X. |

**Table 3.14:** Table for Methods for KernelPCA

# [3.4.2.3 Decomposition MiniBatchSparse PCA](#toc.xhtml#s66a)

The following is the scikit library function used for `MiniBatchSparsePCA`.

`sklearn.decomposition.MiniBatchSparsePCA`

The following table explains the various parameters and default values that passed on to the `MiniBatchSparsePCA` method:

 
| **The class defined** || **class sklearn.decomposition.MiniBatchSparsePCA** |
| --- | --- |
| **Various parameters of the method/function passed to this class** || `class sklearn.decomposition.MiniBatchSparsePCA(n_components=None, *, alpha=1, ridge_alpha=0.01, n_iter=100, callback=None, batch_size=3, verbose=False, shuffle=True, n_jobs=None, method='lars', random_state=None, normalize_components='deprecated')` |

**Table 3.15:** Table MiniBatchSparse PCA

This algorithm finds the set of sparse components that can optimally reconstruct the data. With parameter alpha and the coefficient of the L1 penalty, the sparseness is controlled.

 
| **Method Name** || **Description** |
| --- | --- |
| `MiniBatchSparsePCA` || First, this library method has to be imported from the Scikit learn library as mentioned. Various parameters are as follows:`n_components`*,* number of sparse atoms to extract *alpha,* sparsity controlling parameter. (Higher values lead to sparser components.)`ridge_alpha`*,* amount of ridge shrinkage to apply to improve the conditioning when calling the transform method.`n_iter`*,* number of iterations to perform for each mini-batch.*callback callable or None*, optional *(default: None)* callable that gets invoked every five iterations.`batch_size`*,* the number of features to take in each mini-batch.*verbose,* Controls the verbosity; the higher the value, the more the messages. Defaults to 0.*shuffle,* whether to shuffle the data before splitting it into batches.`n_jobs` *or None, optional (default=None),* Number of parallel jobs to run. None means 1 unless in a joblib.parallel\_backend context. “-1” means using all processors.*method{‘lars’, ‘cd’},* lars: uses the least angle regression method to solve the lasso problem (`linear_model.lars_path`) cd: uses the coordinate descent method to compute the Lasso solution (linear_model.Lasso). Lars will be faster if the estimated components are sparse.`random_state`*,* `RandomState instance`*,* `default=None`Used for random shuffling when the shuffle is set to True, during online dictionary learning. |
| `fit(self, X, y)` || Takes the training samples X and target values y and returns self after fitting the model according to the given training data. |
| `fit_transform(self, X, y=None)` || Fit to data and then transform it. |
| `get_params(self, deep=True)` || Get parameters for this estimator. |
| `set_params(self, **params)` || Set the parameters of this estimator. |
| `transform(self, X)` || Least squares projection of the data onto the sparse components. |

**Table 3.16:** Table for methods for MinBatchSparsePCA

# [3.4.2.4 Decomposition PCA](#toc.xhtml#s67a)

This is one of the most common linear dimensionality reduction techniques. This algorithm finds a low-dimensional representation of the data while retaining as much of the variation as possible. Linear dimensionality reduction is achieved using the **singular value decomposition** (**SVD**) of the data to project across to a lower-dimensional space as explained earlier.

The following is the scikit library function used for decomposition PCA:

`sklearn.decomposition. PCA`

 
| **The class defined** || **class sklearn.decomposition.PCA** |
| --- | --- |
| **Various parameters of the method/function passed to this class** || `class sklearn.decomposition.PCA(n_components=None, *, copy=True, whiten=False, svd_solver='auto', tol=0.0, iterated_power='auto', random_state=None)` |

**Table 3.17:** Table for decomposition.PCA

# [3.4.2.5 Decomposition sparse PCA](#toc.xhtml#s68a)

The algorithm “*Sparse Principal Components Analysis*” or “*SparsePCA*” helps in finding the sparse components that can reconstruct the data optimally. Sparseness here is controlled by the coefficients of the L1 penalty which can be given by parameter “*alpha*”:

`sklearn.decomposition.SparsePCA`

 
| **The class defined** || **class sklearn.decomposition.SparsePCA** |
| --- | --- |
| **Various parameters of the method/function passed to this class** || `class sklearn.decomposition.SparsePCA(n_components=None, *, alpha=1, ridge_alpha=0.01, max_iter=1000, tol=1e-08, method='lars', n_jobs=None, U_init=None, V_init=None, verbose=False, random_state=None, normalize_components='deprecated')` |

**Table 3.18:** Table for decomposition.SparsePCA

The following table explains the various parameters and default values that are passed on to the SparsePCA method:

 
| **Method Name** || **Description** |
| --- | --- |
| SparsePCA || First, this library method has to be imported from the Scikit learn library as mentioned. Various parameters are as follows:`n_components`*,* number of sparse atoms to extract.*alpha,* sparsity controlling parameter.`ridge_alpha`*,* amount of ridge shrinkage to apply in order to improve conditioning when calling the transform method.`max_iter`*,* maximum number of iterations to perform.`tol`*,* tolerance for the stopping condition.`method{‘lars’, ‘cd’}`, lars: uses the least angle regression method to solve the lasso problem (`linear_model.lars_path`) cd: uses the coordinate descent method to compute the Lasso solution (`linear_model.Lasso`).`n_jobs` *or* `None`*,* `optional (default=None)`*,* Number of parallel jobs to run. None means 1 unless in a `joblib.parallel_backend` context. -1 means using all processors.`U_init of shape (n_samples, n_components)`*,* Initial values for the loadings for warm restart scenarios.`V_init of shape (n_components, n_features)`*,* Initial values for the components for warm restart scenarios.*verbose,* Controls the verbosity; the higher, the more messages. Defaults to 0.`random_state, RandomState instance`*,* `default=None`*,* Used during dictionary learning. Pass an int for the reproducible results across multiple function calls.`normalize_components‘deprecated’`*,* this parameter does not have any effect. |
| `fit(self, X, y)` || Takes the training samples X and target values y and returns self after fitting the model according to the given training data. |
| `fit_transform(self, X, y=None)` || Fit to data and then transform it. |
| `get_params(self, deep=True)` || Get parameters for this estimator. |
| `set_params(self, **params)` || Set the parameters of this estimator. |
| `transform(self, X)` || Least squares projection of the data onto the sparse components. |

**Table 3.19:** Table for Methods for SparsePCA

# [3.4.3 Singular value decomposition (SVD)](#toc.xhtml#s69a)

Singular Value Decomposition or SVD is a linear dimensionality reduction that is used to perform the truncated singular value decomposition. As compared to the PCA algorithm, this doesn’t center the data before computing the SVD; this means this works efficiently on sparse matrices:

`sklearn.decomposition.TruncatedSVD`

 
| **The class defined** || **class sklearn.decomposition. *TruncatedSVD*** |
| --- | --- |
| **Various parameters of the method/function passed to this class** || `class sklearn.decomposition.TruncatedSVD(n_components=2, *, algorithm='randomized', n_iter=5, random_state=None, tol=0.0)` |

**Table 3.20:** Table for TruncatedSVD

This SVD estimator mainly supports two algorithms:

1.  A fast randomized SVD solver.
2.  “Naïve” algorithm which uses ARPACK as an eigen solver.

 
| **Method Name** || **Description** |
| --- | --- |
| `TruncatedSVD` || First, this library method has to be imported from the Scikit learn library using the following code:`n_components`, `default = 2`, desired dimensionality of output data.`algorithm, default = “randomized``”`, SVD solver to use.`n_iter`, `optional (default 5)`, number of iterations for randomized SVD solver. Not used by ARPACK.`random_state`, `RandomState` *instance,* `default=None`, used during randomized SVD.`tol, optional`, tolerance for ARPACK. 0 means machine precision. |
| `fit(self, X, y)` || Takes the training samples X and target values y and returns self after fitting the model according to the given training data. |
| `fit_transform(self, X, y=None)` || Fit to data and then transform it. |
| `get_params(self, deep=True)` || Get parameters for this estimator. |
| `inverse_transform(self, X[, copy])` || Transform the sources back to the mixed data (apply mixing matrix). |
| `set_params(self, **params)` || Set the parameters of this estimator. |
| `transform(self, X)` || Perform dimensionality reduction on X. |

**Table 3.21:** Table for methods for TruncatedSVD

# [3.4.4 Independent component analysis (ICA)](#toc.xhtml#s70a)

One of the key challenges in unlabeled data is that there are many hidden information or signals together in the features that we are provided with. Separation of these so-called signals or information is crucial and is achieved by using the ICA. By using the ICA, these components are independently separated. ICA is implemented in scikit-learn using the Fast ICA algorithm. Typically speaking, ICA is not used for dimensionality reduction but for separating the superimposed signals.

So, ICA finds if its application is signal processing tasks such as identification of individual voice from an audio clip of any busy noise. Since this model doesn’t have any noise term in it, the “*whiten*” parameter is used:

`sklearn.decomposition.FastICA`

 
| **The class defined** || **sklearn.decomposition.FastICA** |
| --- | --- |
| **Various parameters of the method/function passed to this class** || `class sklearn.decomposition.FastICA(n_components=None, *, algorithm='parallel', whiten=True, fun='logcosh', fun_args=None, max_iter=200, tol=0.0001, w_init=None, random_state=None)` |

**Table 3.22:** Table for FastICA

 
| **Method Name** || **Description** |
| --- | --- |
| `FastICA` || First, this library method has to be imported from Scikit learn using the following function:`sklearn.decomposition.FastICA`Following are the various parameters used in this method:`n_components, optional`Number of components to use.*algorithm{‘parallel’, ‘deflation’}*Apply parallel or deflational algorithm for FastICA.*whiten, optional,* if whiten is false, the data is already considered to be whitened, and no whitening is performed.*funstring or function, optional. Default: ‘logcosh’,*`fun_argsdictionary`, `optional`, arguments to send to the functional form.`max_iter`, `optional`, maximum number of iterations during fit.`tol`, `optional`, tolerance on update at each iteration.`w_init`*, None of a (*`n_components`, `n_components`*)* `ndarray`, the mixing matrix is to be used to initialize the algorithm.`random_state`, `RandomState` *instance,* `default=None`, used to initialize `w_init` when not specified, with a normal distribution. Pass an `int,` for reproducible results across multiple function calls. |
| `fit(self, X, y)` || Takes the training samples X and target values y and returns self after fitting the model according to the given training data. |
| `fit_transform(self, X, y=None)` || Fit to data and then transform it. |
| `get_params(self, deep=True)` || Get parameters for this estimator. |
| `inverse_transform(self, X[, copy])` || Transform the sources back to the mixed data (apply mixing matrix). |
| `set_params(self, **params)` || Set the parameters of this estimator. |
| `transform(self, X)` || Recover the sources from X (apply the unmixing matrix). |

**Table 3.23:** Table for methods for FastICA

# [3.4.5 Dictionary learning](#toc.xhtml#s71a)

This is one of the dimensionality reduction algorithms, which learns the sparse representation of the original data. The outcome or resulting matrix is known as the “*dictionary*” vectors inside this dictionary are known as “*atoms*”. These atoms are the binary vectors which are populated by zeros and ones:

`sklearn.decomposition.DictionaryLearning`

 
| **The class defined** || **sklearn.decomposition.DictionaryLearning** |
| --- | --- |
| **Various parameters of the method/function passed to this class** || `class sklearn.decomposition.DictionaryLearning(n_components=None, *, alpha=1, max_iter=1000, tol=1e-08, fit_algorithm='lars', transform_algorithm='omp', transform_n_nonzero_coefs=None, transform_alpha=None, n_jobs=None, code_init=None, dict_init=None, verbose=False, split_sign=False, random_state=None, positive_code=False, positive_dict=False, transform_max_iter=1000)` |

**Table 3.24:** Table for DictionaryLearning

 
| **Method Name** || **Description** |
| --- | --- |
| `MiniBatch SparsePCA` || Class name is `sklearn.decomposition.DictionaryLearning`First, this library method has to be imported from Scikit learn library as mentioned. Various parameters are as follows:`n_components`, `default=n_features`, number of dictionary elements to extract.`alpha`, `default=1.0`, sparsity controlling parameter.`max_iterint`, `default=1000`, maximum number of iterations to perform.`tol`, `default=1e-8`, tolerance for numerical error.`fit_algorithm{‘lars’, ‘cd’}`, `default=’lars’`, lars: uses the least angle regression method to solve the lasso problem (`linear_model.lars_path`) cd: uses the coordinate descent method to compute the Lasso solution (`linear_model.Lasso`). Lars will be faster if the estimated components are sparse.`transform_algorithm{‘lasso_lars’, ‘lasso_cd’, ‘lars’, ‘omp’, ‘threshold’}, default=’omp’`The algorithm used to transform the data lars: uses the least angle regression method (`linear_model.lars_path`) `lasso_lars`:`transform_n_nonzero_coefs`, `default=0.1*n_features`, number of nonzero coefficients to target in each column of the solution. This is only used by algorithm='lars' and algorithm='omp' and is overridden by alpha in the omp case.`transform_alpha`, `default=1.0`, if algorithm='lasso_lars' or algorithm='lasso_cd', alpha is the penalty applied to the L1 norm.`n_jobsint` *or* `None`, `default=None`, Number of parallel jobs to run. None means 1 unless in a `joblib.parallel_backend` context. -1 means using all processors.`code_init` *array of shape (*`n_samples`, `n_components`*),* `default=None`, initial value for the code, for warm restart.`dict_initarray` *of shape (*`n_components`, `n_features`*),* `default=None`, initial values for the dictionary, for warm restart.`verbosebool`, `default=False`To control the verbosity of the procedure.`split_signbool`, `default=False`Whether to split the sparse feature vector into the concatenation of its negative part and its positive part. This can improve the performance of downstream classifiers.`random_stateint`, `RandomState` *instance or* `None`, `optional` *(*`default`*\=*`None`*),* used for initializing the dictionary when dict\_init is not specified, randomly shuffling the data when shuffle is set to True, and updating the dictionary.`positive`*\_*`codebool`, `default`*\=*`False`, whether to enforce positivity when finding the code.`positive`*\_*`dictbool`, `default`*\=*`False`, whether to enforce positivity when finding the dictionary.`transform`*\_*`max`*\_*`iterint`, `default`*\=*`1000`, Maximum number of iterations to perform if algorithm='lasso_cd' or lasso_lars. |
| `fit(self, X, y)` || Takes the training samples X and target values y and returns self after fitting the model according to the given training data. |
| `fit_transform (self, X, y=None)` || Fit to data and then transform it. |
| `get_params(self, deep=True)` || Get parameters for this estimator. |
| `set_params(self, **params)` || Set the parameters of this estimator. |
| `transform(self, X)` || Encode the data as a sparse combination of the dictionary atoms. |

**Table 3.25:** Table for methods for DictionaryLearning

`sklearn.decomposition.MiniBatchDictionaryLearning`

 
| **The class defined** || **sklearn.decomposition.MiniBatchDictionaryLearning** |
| --- | --- |
| **Various parameters of the method/function passed to this class** || `class sklearn.decomposition.MiniBatchDictionaryLearning(n_components=None, *, alpha=1, n_iter=1000, fit_algorithm='lars', n_jobs=None, batch_size=3, shuffle=True, dict_init=None, transform_algorithm='omp', transform_n_nonzero_coefs=None, transform_alpha=None, verbose=False, split_sign=False, random_state=None, positive_code=False, positive_dict=False, transform_max_iter=1000)` |

**Table 3.26:** Table for MiniBatchDictionaryLearning

The `MiniBatchDictionaryLearning` method is the same as `DictionaryLearning` which was described earlier. This algorithm finds a dictionary (a set of atoms) that can be used to represent data using a sparse code.

Only the extra method is used as described in the following as compared to the `DictionaryLearning` method.

`partial_fit(self, X[, y, iter_offset])`, which is used to update the model using the data in X as a mini-batch.

# [3.5 Error minimization](#toc.xhtml#s72a)

Error in any machine learning or AI terms is the difference between the actual output to the expected output. This is also called the **Loss Function**. To avoid confusion, henceforth this will be referred as Error only.

The linear equation is described as,

*Y = WX + b* (where, Y is the actual output, ‘W’ is weight, ‘X’ is input, and ‘b’ is bias).

Ŷ is represented as the expected output. Now the error can be computed as follows:

*Error = Y - Ŷ*

To improve the accuracy of any model, the error has to be as minimal as possible. The lesser the error the better the model. Theoretically, this should be zero, but in practical terms, it is possible to achieve the zero value.

So, any loss function or cost function can be defined as a function that measures the performance of the machine learning model for the provided data. This function helps in quantifying the error value between the predicted output values and the expected output values. This will be presented as a single real value number.

There are various methods and steps which are used to reduce this error value such that the model provides better accuracy at the end of the day. The following are a few methodologies and techniques to reduce this error or error rate:

# [3.5.1 Distance computing](#toc.xhtml#s73a)

By applying plain geometry or with respect to the geometric perspective, this error can be represented as a distance between two points using the coordinate system.

This is one of the straight-forward ideas and uses simple subtraction of both the values so the error value can be determined.

The distance here is:

![](images/Figure-3.13.jpg)

**Figure 3.13:** Input ‘X’ versus Output ‘Y’ plotted and along with actual to predicted value comparison

In the preceding diagram, the X values are input values, Y values are output values that are plotted. For X values of 1, 2, and 3 actual output Y values are 1, 2, and 3 (which is indicated with the dotted lines). But the expected values of Y are 3, 5, and 7 which is indicated with the thick line. The distance can be computed as the difference between the expected and the actual values as described earlier. ”d1”, “d2”, and “d3” are the various distances which can be computed as follows:

*d1= 1 – 3 = – 3*

*d2= 2 – 5 = – 2*

*d3= 3 – 7 = – 4*

Now the loss function is *1/3* × *\[–3+ (–2) + (–4)\] = –9/3 = –3*

We will consider the absolute value of this which is value “3”, which is our error distance or cost value.

# [3.5.2 Threshold limit](#toc.xhtml#s74a)

This is not a loss function that can be termed as an optimization method or technique. This is used to maximize the F1 score for each value and will be in the range of 0 to 0.5. This is computed with various probability mechanisms and steps. With the threshold limit set, one can get the maximum F1 score and build the model accordingly. Note: Details of the “*F1 Score*” are provided in *[Chapter 2 (Supervised Machine Learning)](#c02.xhtml).*

# [3.5.3 Log loss](#toc.xhtml#s75a)

This is covered in detail in the performance metrics section in the context of model performance in *[Chapter 2 (Supervised Machine Learning)](#c02.xhtml)*.

# [3.5.4 Euclidian distance](#toc.xhtml#s76a)

This is the mean squared error and it is covered in detail in the performance metrics section in the context of model performance in *[Chapter 2, Supervised Machine Learning](#c02.xhtml).*

The other loss functions which are used across the machine learning algorithms and models are as follows:

![](images/Figure-3.14.jpg)

**Figure 3.14:** Various loss functions with formula

Where ‘L’ is the loss function,

‘y’ is the actual output and ‘f(x)’ is the expected output function.

# [3.5.5 Examples and samples](#toc.xhtml#s77a)

As explained in detail, the unsupervised learning algorithms and dimensionality reduction techniques are very popular where we have large data sets which had unlabeled data. These algorithms help in analyzing the various techniques and optimize the computations required. Some of these algorithms can be used for visualizations required like clustering and anomaly detection like credit card fraud detection where various PCA dimensionality reduction steps can be applied. t-SNE and a combination of SparsePCA can be applied where there are huge features set and multi-dimensional data sets. Applications requiring clustering techniques are some of the common areas where unsupervised algorithms are applied unprecedently.

Recently, association mining (frequently occurring) has been predominantly used by retailers for basket analysis, goods identification, and so on.

Reducing the number of features is one of the big challenges that unsupervised learning algorithms and techniques solve in today’s complex world.

# [Conclusion](#toc.xhtml#s78a)

It is still believed that unsupervised learning has the most complex machine learning algorithms. But this is not true, in this chapter, we have made these algorithms easy to understand and explained how powerful they are to be used once understood from the basic level. Also, we have made sure that all the aspects related to unsupervised learning are covered along with details about the important algorithms and libraries required along with methods and steps. While unsupervised learning does not require labeled data, supervised learning covered in subsequent chapters needs large training data sets as a golden reference.

In the upcoming chapter, the “*Feature Engineering*” topic will be covered.

# [Points to remember](#toc.xhtml#s79a)

*   Unsupervised learning does not require labeled data for training.
*   The K-means clustering algorithm supports only convex-shaped clusters.
*   All the algorithms and dimensionality reduction techniques are referenced from the SciKit Library.
*   Principal component analysis is used to reduce the dimensions of the input data.
*   t-SNE provides dimensionality reduction while visualizing the high-dimensional data.
*   The DBSCAN algorithm separates the clusters of high density from the regions of low-density clusters.
*   In the independent component analysis, the superposed information from multiple independent sources is separated.
*   Various loss functions are covered which are used to reduce the error or loss value for better accuracy and prediction.

# [Questions](#toc.xhtml#s80a)

1.  What is unsupervised learning? What is its significance?
2.  What are the differences between supervised and unsupervised learning?
3.  What is the dimensionality reduction technique all about?
4.  What are the popular unsupervised machine learning algorithms?
5.  What are the dimensionality reduction techniques described in this chapter?
6.  What are the applications of unsupervised algorithms?
7.  What is PCA?
8.  What is t-SNE?
9.  What is SVD?
10.  What is a dendrogram?
11.  What is ICA?
12.  List some of the well-known algorithms and various dimensionality reduction methods.
13.  What are the various loss functions described in this chapter?
14.  What is the loss and cost function?
15.  What are the advantages of unsupervised learning?

# [Multiple choice questions](#toc.xhtml#s81a)

1.  **Choose the correct answer** 
    1.  Unsupervised learning is based on labeled data.
    2.  Unsupervised learning works on unlabeled data.
    3.  Unsupervised learning is very fast.
    4.  Unsupervised learning works on any data.
2.  **Choose the correct answer** 
    1.  t-SNE is a dimensionality reduction technique.
    2.  t-SNE is a supervised algorithm.
    3.  t-SNE works on any data.
    4.  None of the above
3.  **Choose the correct answer** 
    1.  SciKit Learn is the library used for unsupervised learning algorithms.
    2.  Any library can be used to define any algorithm.
    3.  Most of the algorithms are not included in SciKit library.
    4.  None of the above
4.  **Choose the correct answer** 
    1.  PCA stands for nothing.
    2.  PCA cannot be expanded.
    3.  PCA stands for Principal Component Analysis.
    4.  None of the above
5.  **Choose the correct answer** 
    1.  ICA stands for Independent Component Analysis.
    2.  ICA cannot be expanded.
    3.  ICA is Immigration and Checkpoints Authority.
    4.  None of the above
6.  **Choose the correct answer** 
    1.  SVD is Singular Value Decomposition.
    2.  SVD cannot be expanded.
    3.  SVD is not found in SciKit learn.
    4.  None of the above
7.  **Choose the correct answer** 
    1.  SVD is a fast unsupervised learning algorithm.
    2.  SVD is a supervised algorithm.
    3.  Singular Value Decomposition (SVD) is a dimensionality reduction technique.
    4.  None of the above
8.  **Choose the correct answer** 
    1.  Loss function and error function cannot be the same.
    2.  Loss function works on loss and error function works on error rate.
    3.  Both cannot be related to each other.
    4.  Loss function and error function are the same.

# [Answers](#toc.xhtml#s82a)

1.  **b**
2.  **a**
3.  **a**
4.  **c**
5.  **a**
6.  **a**
7.  **c**
8.  **d**

# [CHAPTER 4](#toc.xhtml#c04)

# [Feature Engineering](#toc.xhtml#c04)

Feature engineering is the process of transforming raw data into features that represent the underlying problem to the predictive models in a better way, resulting in improved model accuracy on unseen data. Therefore, you have to extract the features from the raw data set that you have collected before training your data on machine learning algorithms. Otherwise, it will be hard to gain good insights into your data.

Feature engineering is not a directly involved topic in machine learning but has huge importance in building models and constructing algorithms around various data sets.

# [Why is feature engineering needed?](#toc.xhtml#s83a)

For building the best possible predictive model, having good and selective features is an important task. Also, the selection of the best possible features is important, which may impact higher accuracy. The influence of certain features on the model, the impact they have on the outcome or results, and their selection with the available data in hand is called **feature engineering**.

It is a known fact that better features from better data lead to better outcomes and results. Thus, curating data in advance is crucial. Sometimes after the data is curated, the outcome and the prepared data may be misleading, if we have not selected the right feature set. Thus, great features are required for better outcomes or results.

However, this may not be the best for the models which could help them run faster, make them easier to understand and maintain.

**Advantages of better features are explained as follows:**

*   Better features lead to better flexibility
*   Better features help in building simple and robust models
*   Better features lead to better results
*   Better features help in better predictive models and thus, resulting in an improved model accuracy
*   Better features help the model to work better on unseen data

# [Structure](#toc.xhtml#s84a)

In this chapter, we will discuss the following topics:

*   Introduction to feature engineering
*   Methods and steps for better feature selection 
    *   Baselining model
    *   Categorical encodings
    *   Feature generation
    *   Feature selection
    *   Collecting and refining data
    *   Cleaning and organizing data
    *   Data preparation
    *   Mining data for pattern selection

*   Other popular techniques of feature engineering 
    *   Imputation
    *   Handling outliers
    *   Binning
    *   One-hot encoding
    *   Feature split
    *   Scaling
    *   Log transform
    *   Grouping operations

*   Examples and samples 
    *   Few samples with examples

# [Objectives](#toc.xhtml#s85a)

After studying this chapter, you should be able to:

*   Understand the mechanism and methods of feature engineering and feature selection.
*   Various techniques used for encoding and feature selection.
*   Best methods and steps for feature selection.
*   How feature selection helps in choosing the best model and thus, help in the improvement of the model’s accuracy.
*   Examples or use cases of feature engineering.

# [4.1 Introducing feature engineering](#toc.xhtml#s86a)

Let us explain what is a feature before jumping on to “*Feature Engineering*”. In any data format be it Tabular or .CSV file, which is the representation of various observations consisting of instances (maybe rows of data) and attributes (maybe columns of data). In these representations, an attribute could be treated as a “*Feature*”. So, a column containing one specific type of data is representing a feature. While collecting or building these data models, one may encounter wrong, out of bound, malicious, and irrelevant data. The overall art of handling or ignoring such features may also be called **Feature Engineering**. For example, there is a data set consisting of people’s ages living in Hawaii Island, in that case, the data set may have ages from 0-120 years. But no human can live beyond 140 years. Assume if the data column consists of a person’s age as 1000 years. So obviously, it appears that it is out of bounds. But knowing how to average it out or ignore it is important. You cannot just delete that column consisting of this data value, as by doing this you are avoiding all the people. The following diagram explains how feature engineering can be performed and its steps. The process of FE contains data processing and wrangling, extraction, scaling, modeling, and so on:

![](images/Figure-4.1.jpg)

**Figure 4.1:** Various steps involved and workflow of Feature Engineering

The need for feature engineering arises while preparing the data set which is machine learning compatible and meets all the learning requirements of the ML algorithms.

If better feature engineering is done on the data, it helps in building better models and improving their performance. It is also observed that most data scientists spend 80% or more of their time on data preparation. Following are the various tasks that data scientists spend the most of their time on (these are approximate percentages):

1.  Building and preparing the training set: ~3-5%
2.  Cleaning and neatly organizing the data: ~50-60%
3.  Collecting data sets from various sources: ~15-20%
4.  Mining data for patterns: ~8-12%
5.  Refining the data algorithms: ~4-6%
6.  Other data-related activities: ~5-7%

Many of the preceding techniques and methods explain *why feature engineering is important* and helps in having better data preparation.

The result that we achieve from the machine learning model depends on how feature engineering has been done on the data, what features have been picked up, what are the inherent qualities of the data that we have considered, and so on.

Following are some of the advantages of selecting better features:

*   Flexibility of the model
*   It makes the building of the simpler models easier
*   Picks up wrong parameters (which are yielding less than the optimal values), which helps in ending up with better results
*   Better representation of the context of the underlying problem
*   Build better models with a good understanding of data

Becoming a master in feature engineering techniques helps in coming up with faster and better ML models.

# [4.2 What is Feature selection?](#toc.xhtml#s87a)

Feature selection is the process where you automatically or manually select the features that contribute the most to your prediction variable or output.

Various methods and steps have evolved over a period of time for better feature selection. Some models are traditional and some have technical steps involved in them. But whatever may be the model, they help in better feature extraction or selection. Once we have selected the better feature, building a model will be a lot easier. Some of the algorithms also perform well when the best feature is selected.

Following are some of the well-known, industry-wide used methods and steps for better feature selection:

**Reasons to use feature selection:**

*   It enables the machine learning algorithm to train faster.
*   It reduces the complexity of a model and makes it easier to interpret.
*   It improves the accuracy of a model if the right subset is chosen.
*   It reduces overfitting.

# [4.2.1 Baselining model](#toc.xhtml#s88a)

This is one of the initial methods that is used for feature engineering. First of all it is better to select important features and then the predictive model is built around this. It identifies the existing input variables, columns of data, data attributes, or features that provide us with the required baseline accuracy. Based on these the respective features are selected. Once this is decided, the model and algorithm to be used is decided and the training is started accordingly.

# [4.2.2 Categorical encodings](#toc.xhtml#s89a)

In any of the known machine learning or data science activities where data is involved, they will predominantly contain categorical variables. Typically, these variables will be stored as "*text values*". For example, a column containing country names like France, India, UK, USA, Spain, Italy, and so on. The computer algorithm will not understand what is a country. So, these country names will be converted into numbers that can be understood by the machines. For example, each country name may be assigned with a number to it. For example, France=1, India=2, USA=3, and so on. Whenever the feature column involving these countries is referenced, these numbers will represent the respective countries.

Most of the machine learning algorithms support categorical values without any further manipulation in those cases.

There are various encoding techniques and methodologies that are used. The following are described on the basis of standard practice and general use. The major classifications are “*Nominal Encoding*” (One Hot Encoding, One Hot Encoding with Many Categories, and Mean Encoding) and “*Ordinal Encoding*” (Label Encoding and Target Guided Ordinal Encoding). Some of the well-known methods and techniques are described here.

# [Nominal encoding types](#toc.xhtml#s90a)

The features where their categories are only labeled without any order of precedence are called **nominal features** or **encodings**. Following are some of the nominal encoding types that are explained in detail:

# [4.2.2.1 One Hot Encoding](#toc.xhtml#s91a)

Using this method, each category is represented with a vector of values containing "1" and "0". The number of vectors used depends on the categories that we want to keep for feature engineering. For features involving cardinality (represented as many numbers), this technique may produce a huge number of columns. Generally, the data scientist or the person deciding the machine learning algorithm has to cautiously choose the correct technique. In some cases, it is advisable to use dummy encoding as well:

![](images/Figure-4.2.jpg)

**Figure 4.2:** Normal data and data after applying One Hot Encoding

# [4.2.2.2 Mean encoding](#toc.xhtml#s92a)

Mean Encoding is one of the popular encoding approaches that is used and followed by Kagglers. Mean encoding is similar to label encoding. In this, the feature label is decided with the mean value of the target variable on training data.

The main advantage of mean encoding is that it does not affect the overall volume of the data and helps in faster learning.

Mean encoding has both advantages and disadvantages.

**Advantage**: Mean encoding helps in capturing information within the label, rendering more predictive features.

**Disadvantage**: In some cases, it may cause overfitting in the model.

# [4.2.2.3 One hot encoding with many categories](#toc.xhtml#s93a)

There are some cases where the large categorical values or features need more categories while applying One Hot Encoding. This may be a challenge and has to proceed with careful steps in such situations. First, the categories which need to apply One Hot Encoding has to be decided, else this may end up with thousands of new features.

# [Ordinal encoding types](#toc.xhtml#s94a)

There are various ordinal types as explained further, each of these will be assigned with a unique category value (integer).

# [4.2.2.4 Label encoding](#toc.xhtml#s95a)

In this technique, each category is assigned a value from 1 to "N" (where "N" is represented as the number of categories for the feature). After applying this technique, if some categories have a close association or relationship with other categories, this information may be lost:

![](images/Figure-4.3.jpg)

**Figure 4.3:** Normal data and data after applying Label Encoding

# [4.2.2.5 Target guided ordinal encoding](#toc.xhtml#s96a)

Target encoding is similar to mean encoding. Here, the mean is calculated from the target variable for each category and replaced with the category variable with the mean value. In some mechanisms, Bayesian encoders are used for the posterior probability of the target replaced with each category.

# [4.2.2.6 Frequency encoding](#toc.xhtml#s97a)

This technique uses the frequencies of the categories as labels. In some cases, where the frequency is assumed to be related, in such models it helps to understand and assign weight in direct and inverse proportion. The following three-step approach is used to apply this technique:

1.  Select the categorical variable that you would like to transform or change.
2.  Group them into categorical variables and get the count of each category.
3.  Join them back with the training data set that was used.

![](images/Figure-4.4.jpg)

**Figure 4.4:** Frequency encoding representation of data

The various classes and parameters used for the same are depicted in *[figure 4.4](#c04.xhtml#fig4_4)*:

# [4.2.2.7 Other Encoding techniques](#toc.xhtml#s98a)

Let us understand some other encoding techniques in this section.

# [Hash encoder](#toc.xhtml#s99a)

Hash encoding is a one-way process and cannot be reversed. Thus, one cannot generate the original input from the hash representation. Arbitrary size input data is transformed into fixed-size values using the hashing mechanism. Various hashing algorithms are used to carry out the hash operation.

# [Effect encoding](#toc.xhtml#s100a)

This is almost similar to dummy encoding with a minute difference. It is also known as **deviation** or **sum encoding**. Here, three values “0”, “-1”, and “1” are used to build encoding and to represent data.

# [Dummy encoding](#toc.xhtml#s101a)

Dummy encoding is one-hot encoding. This is a categorical encoding where the categorical variables are converted into a set of binary values representing “0” and “1”. As compared to One Hot Encoding, we use values from 1 to “N” categories, here only two values are used.

# [Binary encoding](#toc.xhtml#s102a)

This is the combination of hash and one hot encoding technique. Here, the categorical feature is first converted into a numerical form using the ordinal encoder and then the numbers are transformed into a binary number, which is later split into different columns:

![](images/Table-4.1.jpg)

**Table 4.1:** Scikit Learn Libraries for encoding techniques

# [4.2.3 Feature generation](#toc.xhtml#s103a)

Feature generation is the process of generating new features. Creating new features from the raw data is an art and is one of the best ways to improve the model.

These newly generated features are not the results of feature transformation. For example, we can generate new features for images and pixels of the images.

New features can be generated in various methods and ways. When building new features, it is important to keep the following points in mind:

*   How important and applicable are the newly generated features for model building?
*   Whether they will help in improving the accuracy?
*   Is there any domain-specific knowledge to be included in the new features?
*   After building new features, how impactful would they be in model construction?
*   Finally, how useful the newly-built features are to the overall model accuracy improvement that needs to be validated.

One of the easiest and heavily used methods of feature generation is combining the categorical variables. For example, we have one record of country names "*Country*" and category as "*Flag*", then we can create a new value called "`Country_Flag`". This is a new categorical feature that can provide information about the correlation between the two categorical variables.

# [4.2.4 Feature Selection](#toc.xhtml#s104a)

Correct feature selection is one of the most important aspects of machine learning.

It is a common observation to see hundreds or thousands of features coming from the data sets after applying various encodings after which feature generation takes place.

The huge number of features can lead to multiple challenges. The more the number of features, there are more chances of overfitting the training and validation sets. This will hamper the model and the model may perform worse at generalizing the new data that it gets exposed to.

Also, the training time taken will be longer for the model if a huge number of features are present and along with that the optimization of hyperparameters or tuning of hyperparameters will take much longer. Any inference or outcome if expected faster, may not happen. Thus, using a selective and lesser number of features is crucial. Again, there are many feature selection techniques and methods which can be used to overcome the preceding problems. Following are some of the feature selection techniques and methods.

It is important to select a subset of features that are important and will help in building a better model. There are various feature selection algorithms that may be used along with the scoring method to rank and choose certain features.

Some of the well-known methods are as follows:

*   Correlation
*   Feature importance methods
*   Univariate feature selection

Over a period of time, advanced methods have evolved which are the combinations of one or more methods. Some models can be built using trial and error, frequent evaluation, and so on. This is an art that can be developed over a period of time.

# [Correlation](#toc.xhtml#s105a)

This is a statistical term that is used to define how close two variables are to having a linear relationship with each other. For example, two variables “a” and “b” are related linearly as “a=5b”. So, when the two features have a higher correlation then we can drop one of the two variables. As both variables have almost the same effect on the dependent variable. This helps in reducing the number of features to a great extent.

# [Feature importance methods](#toc.xhtml#s106a)

**Feature importance** is a technique that is decided on the basis of the score assigned to the input feature values. This score is decided based on how useful these features are and how they help in predicting the target variables. This is a score generated technique that uses scikit learn library modules. The most important feature will get the highest score. This is an inbuilt class that comes along with “*tree-based classifiers*”, which helps in listing out the best features with the corresponding scores.

# [Univariate feature selection](#toc.xhtml#s107a)

This method is one of the simplest and most adopted of all the other methods. For each of the features, this measures how strongly the target depends on the features using a statistical test like “χ2” or “*ANOVA*”.

While using the scikit-learn feature selection module, “*feature\_selection.SelectKBest*” can be used to get “K” best features along with the scoring function. For classification models, this provides three different scoring functions as “χ2”, “ANOVA”, and “F-value” along with mutual information score for each. The mutual information provided here is non-parametric and can also capture non-linear relationships. There are other techniques and methods which can be used case-to-case:

*   Kendall’s Rank Coefficient (non-linear)
*   Pearson’s Correlation Coefficient: `f_regression()`
*   ANOVA: `f_classif()`
*   Chi-Squared: `chi2()`
*   Mutual Information: `mutual_info_classif()` and `mutual_info_regression()`

For feature selection, any of the best-suited methods can be used on a trial and error basis, before building the model.

# [4.2.5 Collecting and refining data](#toc.xhtml#s108a)

Data collection is one of the important aspects of data science. It is better to build a checklist for collecting data and verify if the collected data is feasible and good for building a model. Along with that, data navigation for identifying any anomalies or discrepancies in advance is a good practice. The following set of questions can be asked to make sure we have the correct format and usable data:

*   Where the data is stored and what is the size of the data?
*   What quantity of data is needed to build the model?
*   What should be the quality of the data?
*   Whether the data that has been collected is up-to-date and in good format?
*   Whether the data that has been collected is relevant to the model which is being planned to build?

# [4.2.6 Cleaning and organizing data](#toc.xhtml#s109a)

Having high-quality data is always a good practice. Any of the world-class Kaggle Grandmasters who have won the competition are aware of this fact and they invest much of their time and money on having a cleaned data. The better the cleaned data one has, the better the model’s outcome and performance will be.

Cleaning data is nothing but to know which is the relevant and irrelevant data.

Following are some of the best practices, steps, and methodologies that can be used for cleaning and organizing the data:

*   It is always better to keep those data features which will provide us more insights.
*   Better to decide the pre-processing and feature engineering techniques in advance.
*   Better to have the proper data querying techniques in place before building the model.
*   Keep a watch on when the data would be ready to move to a high-quality or high-quantity state so that one can move to the next level.
*   Storing data is also important. Once the data is refined, it should be decided where and how will it be stored.
*   Finally, what testing is to be done once the data is refined and validated for consistent performance and model outcome.

# [4.2.7 Data preparation](#toc.xhtml#s110a)

Once the data refining and cleaning are done, preparing the data for feeding into the algorithm is also important. There are various aspects that one has to keep in mind in data preparation like who is controlling the data access, who is generating more and new data, and how to have high-quality data. Following are some questions that are to be asked for having a better-prepared data set:

*   Why do we need to include more features to improve the model’s performance?
*   How and why is the relevant data section is decided?
*   What analytics and insights were applied to the data set?
*   For which model/algorithm this data is to be fed?

The preceding set of questions helps in considering the compute, storage, and machine learning frameworks that are to be used. Once the successful benchmarking of the data is done, it is good to go.

# [4.2.8 Mining data for pattern selection](#toc.xhtml#s111a)

Data quality reduces over a period of time. The results are to be verified constantly to check the quality of data. It is a good practice to have better mining techniques for pattern selection and identification at hand.

As mentioned in the earlier sections, accurate feature selection improves the quality of the model and makes the process of the overall modeling efficient.

If unwanted columns or features are selected while building the model, more compute power (CPU) and memory will be consumed along with more storage space. These unwanted columns or features may lead to noisy or redundant data which makes it difficult to identify the large data sets that are present.

It becomes challenging to identify a pattern in noisy or redundant data. Also, if the data set is high-dimensional, most of the data mining and pattern-based search of features will become challenging.

There are various algorithms and methods to select these patterns and identify the correct features. Following are some of the well-known techniques:

*   **The interestingness score**: This is a scoring technique that is used to rank and sort attributes in columns that contain non-binary continuous numeric data.
*   **Shannon's entropy**: This can be applied to column features that contain discrete and discretized data.
*   **Bayesian scores (Bayesian with K2 Prior or Bayesian Dirichlet with a uniform prior (default))**: These scores can be used to identify the column features that contain discrete and discretized data. If the data contains continuous columns, then the preceding method, “*the interestingness score*” can be applied.

However, there are various methods and mechanisms in practice today.

It depends on the machine learning algorithm we are using to build our model and the kind of data set we have at hand. Based on these, some of the scoring techniques can be applied and used.

# [4.3 Other popular techniques of feature engineering](#toc.xhtml#s112a)

This section is an overall recap of all the topics that we have discussed related to feature engineering. This section provides some insights and the missing techniques in the previous section. One can build a better model or improve their model’s performance if any of these steps are used thoroughly while using data.

# [4.3.1 Imputation](#toc.xhtml#s113a)

As discussed earlier, handling the missing values is one of the common problems in machine learning data handling. When the data is generated due to human errors or interruptions while collecting the data flow or due to privacy laws and concerns, these missing values may pop up.

There are various techniques as described earlier, dropping the rows containing the missing values and dropping the columns if too many missing values are present in certain columns. Instead of directly dropping the rows and columns, imputation can be used as it preserves the data instead of completely dropping it.

Again, there are two ways of using imputation which is described as follows:

1.  **Numerical Imputation**: These are the numerical values that are represented and handled with mean, standard deviation, or such. In some cases, if “*NA*” is present in the data set, it will be replaced with the value zero (“0”). If there are too many missing values in a particular feature set, then the mean of other values are taken and replaced in the place of the missing values.
2.  **Categorical Imputation**: These values are categorical and it is better to replace the missing values with the “*maximum occurred value*” in a particular column/feature.

# [4.3.2 Handling outliers](#toc.xhtml#s114a)

This is also one of the crucial steps in data model building. Many visual techniques like clustering (K-means) can be used to identify the outliers or other statistical methods like “*standard deviation*”, with percentiles, a technique called “*Drop or Cap*” can be used. Outliers are sometimes easily visible but otherwise, not. We have to cautiously apply the techniques that we have planned. Techniques like “*Box Plotting*” can be used to box plot the features and check if there are values that are out of bounds or not. If there are, then they are called **outliers**. The outlier value will be a single data point and will be a box plot when plotted.

# [4.3.3 Binning](#toc.xhtml#s115a)

Binning is any data value within the range that is made to fit into the bin. It is important in the data exploration activity. We typically use it to convert continuous variables into discrete ones.

Sometimes, this is called **quantization** as well. Binning helps in the mitigation of bias and have a uniform distribution of data. Binning helps in making the model robust and also helps in preventing overfitting. But it is observed that binning will take a hit on the performance of the model. We can use regularization techniques to overcome this hit.

# [4.3.4 One-hot encoding](#toc.xhtml#s116a)

As already explained in the earlier section, this is one of the most common encoding techniques used today. In this technique, data columns are spread and assigned with values “1” and “0” based on their presence. *For more details refer to section 4.2.2.1.*

# [4.3.5 Feature split](#toc.xhtml#s117a)

Sometimes, it is better to split the features instead of building new ones. As most of the data sets contain string values in their columns, they have some identifiable patterns, these can be split into two or more columns. But before this, the whole data has to be observed and the decision is to be taken accordingly.

# [4.3.6 Scaling](#toc.xhtml#s118a)

For the data having various ranges, the scaling technique can be applied. Especially the numerical data will have different ranges or out of range values. Using algorithms like K-NN or K-means, distance calculations will help in identifying the scaled continuous features. Following are two popular techniques in scaling:

1.  Normalization
2.  Standardization

*For more details refer to [chapter 3](#c03.xhtml) and section 3.2.2.*

# [4.4 Examples and samples](#toc.xhtml#s119a)

Feature engineering plays an important role in building a model or predicting the outcome for a model. Some of the observations which can be drawn early, help in saving the unnecessary compute power. Building a feature-ready model is always intuitive and easy to explain. Having a careful and thorough feature analysis and engineering helps in having better domain knowledge. This is useful for the exploratory analysis of data.

After performing multiple iterations of feature engineering, one will build the art of ignoring the not-needed features or just creating the features for the sake of creating them can be avoided.

Feature engineering plays an important role in building the models starting from the MNIST kind of data set to more complex models. There are various industry domains where feature engineering finds its importance and is a must. The popular applications which can be used are as follows:

*   Image reproduction
*   Conversion of raw data into understandable data
*   Dimensionality reduction
*   Feature extraction
*   Reduction of processing and computation power
*   Misclassification detection based on the patterns
*   Explain the ability of methods
*   Avoidance of vague feature sets
*   Robust model for better prediction and outcome

Best models or best feature engineering practices can be built with this domain expertise. The application which needs a thorough understanding of the feature engineering is pre-cautiously built and made stable and predictive over a period of time.

# [Conclusion](#toc.xhtml#s120a)

Feature engineering is one of the most important steps for the ML/DL models. If the right feature engineering is done in advance, the model performs better and faster. Also, feature engineering helps in building more robust and best-performing models. The right choice of features either by the model as in deep learning or by a human expert as in traditional machine learning determines the accuracy of the system. Redundant features often lead to the confusion of the model.

Finally, feature engineering helps in building a better representation of the problem, sample data to learn a solution quickly and depict the context of the problem. As mentioned earlier, feature engineering is an art and technique, which has gained popularity in the last decade.

In the next chapter, the “*classification, clustering, association, and regression*” topic will be covered. The importance of feature inferencing in each of the AI systems will be discussed in detail.

# [Points to remember](#toc.xhtml#s121a)

*   Feature engineering is one of the most important steps in machine learning.
*   Data is the new oil in the current world, all the models we build are dependent on data, so it is a better practice to have better data at hand.
*   Feature engineering helps in having better data and thus, builds a more robust and better-performing model.
*   As the field of machine learning has evolved, many techniques and methodologies are coming into prominence.
*   Some techniques and methods can be applied on a trial and error basis.
*   Some of the feature engineering techniques can be combined for better results.
*   There is no hard and fast rule that if some combination of techniques worked better for a certain domain, it will work the same for other models in that domain as well.

# [Questions](#toc.xhtml#s122a)

1.  What is feature engineering? What is its significance?
2.  What is “baselining” and “encoding” in feature engineering?
3.  What are the various techniques used in feature engineering?
4.  What are the applications and models where feature engineering is used?
5.  What is imputation and why is it used?
6.  What are the various imputation techniques?
7.  What is one hot encoding and how is it different from categorical encoding?
8.  What is binning?
9.  What is data cleaning and refining?

# [Multiple choice questions](#toc.xhtml#s123a)

1.  **Choose the correct answer:** 
    1.  Feature engineering is the selection of the best features based on certain patterns.
    2.  Feature engineering is building new features.
    3.  Feature engineering is imputation.
    4.  All of the above
2.  **Choose the correct answer:** 
    1.  Imputation is the preservation of data with some numerical replacement.
    2.  Imputation is the removal of columns.
    3.  Imputation is the removal of data sets.
    4.  None of the above
3.  **Choose the correct answer:** 
    1.  One hot encoding uses values from 10, 20, 30, …, 1000.
    2.  One hot encoding uses values “0” and “1”.
    3.  One hot encoding uses algebraic equations.
    4.  None of the above
4.  **Choose the correct answer:** 
    1.  There is a library function in Scikit called “OneHotEncoder”.
    2.  There is no such library in Scikit.
    3.  A is True.
    4.  B is True.
5.  **Choose the correct answer:** 
    1.  In feature engineering, features can be split.
    2.  ”a” cannot be done.
    3.  Features cannot be split or joined.
    4.  None of the above

# [Answers](#toc.xhtml#s124a)

1.  **d**
2.  **a**
3.  **b**
4.  **c**
5.  **a**

# [CHAPTER 5](#toc.xhtml#c05)

# [Classification, Clustering, Association Rules, and Regression](#toc.xhtml#c05)

As discussed in *[Chapter 2, “Supervised Machine Learning”](#c02.xhtml)*, and *[Chapter 3, “System Analysis with Machine Learning / Un-Supervised Learning”](#c03.xhtml)*, a few of the popular classification methods of supervised and unsupervised machine learning or deep learning techniques were discussed. In this chapter, in the first few sections, the methods of classification other than those not covered in the previous chapters would be discussed to have a wider coverage of the topics on classification, regression, clustering and its types. A section on associate rules talks about the method of classification specifically used in data mining. Finally, a section with use case/s or a programming example with code would be given and to no surprise, the conclusion would bring down the curtains of this chapter.

# [Structure](#toc.xhtml#s125a)

In this chapter, the following topics will be discussed:

*   Introduction
*   Classification techniques
*   Clustering techniques
*   Association rules techniques
*   Regression techniques
*   Examples and samples

# [Objectives](#toc.xhtml#s126a)

After studying this chapter, one should be able to understand:

*   Various classification techniques and when and where to apply them.
*   Different types of clustering techniques and their applicability to data.
*   What are the association rules and why are they important? Terms and concepts of association rules technique.
*   Types of regression, their purpose and usage.
*   Programming example detailing out the use of association rules in the online retail recommendation use case.

# [5.1 Introduction](#toc.xhtml#s127a)

In deep learning and machine learning technologies, there are various classifications, regression, and clustering techniques. Each of these techniques is designed to be used based on the data set, size of data set, type of data set, properties of the data set, the purpose and objective of the problem, and outcome of the problem. Most often each of these techniques has different purposes and are applied independently based on the problem to be solved. Sometimes, a combination of these techniques will be used for a problem, the reason would be the complex data set and it cannot be solved by using one technique independently. Though each of them attempts to solve specific problems and their approach to solve a problem is distinct, there exists an overlap between them. Hence, many times the problem is attempted to solve using a combination of these techniques as applicable based on the characteristics of the data set and problem at hand. Details on classification, regression, and clustering techniques have been covered predominately in *[Chapter 2, “Supervised Machine Learning”](#c02.xhtml)*, and *[Chapter 3, “System Analysis with Machine Learning / Un-Supervised Learning”](#c03.xhtml)* and in bits and pieces in the rest of the chapters. However, in this chapter, details on those topics are covered so that the contents appear as an extension giving additional information on the types of algorithms in each technique. As there exists a large number of algorithms in each of these techniques, the chapter discusses the important and popular algorithms only. The association rules technique, its concepts, purpose, and usage along with the Apriori algorithm will be discussed in detail.

# [5.2 Classification Techniques](#toc.xhtml#s128a)

Many classification algorithms can be used to classify the data. Following are a few of the classification methods used as applicable to the use case/s of interest. Each method has its advantages and disadvantages and one has to carefully choose them based on the multiple parameters given as follows:

1.  Size of the data set
2.  Number of features of the training samples
3.  The expected performance or accuracy of the model
4.  Training time
5.  Type of data set, if the features are linearly separable or not
6.  Quality and nature of data (numerical, categorical, missing data, image data, or mixed data)
7.  The purpose and expected output of classification and how to interpret the output
8.  The environment or platform dependency if any

# [5.3 One-Class Classification](#toc.xhtml#s129a)

The one-class classification was introduced by *Moya* and *Hush* in 1996. Generally, *in one class classification, there will be two classes that have a special meaning and are usually named a target class and an outlier class*. They are commonly used for outlier detection and anomaly detection problems. For example, if the problem is to find if the machine is working in normal operating condition or is faulty. In this case, the samples of the machine working in the normal operating conditions can be easily generated but those of faulty ones is difficult. Since it is difficult to prepare a data set for these kinds of examples that is balanced, it would enable one to use the one-class classification. Other examples include monitoring of helicopter gearboxes and novelty detection.

*[Figure 5.1](#c05.xhtml#fig5_1)* shows an example of the one-class classification with ellipse objects as the target class and square objects belonging to an unknown class. The dashed boundary shows the decision boundary for the classification:

![](images/Figure-5.1.jpg)

**Figure 5.1:** An example of the one-class classification

In situations where the classification problem is to classify (decide) whether it belongs to a particular class or not. For example, if there is a classifier that can classify the given objects to either plants or animals. If a book is given as input, the classifier would classify it to either belonging to the plants class or animals class which is not correct. In this case, a classifier needs to be built which can decide if the given object belongs to the plants class, animals’ class, or some other class. Hence, in one-class classification samples of one of the classes will be well-defined (samples of the machine in normal working condition in the preceding example) and will be called **target class**, and the other class has a few or no samples (samples for faulty machine operation in the preceding example) will be called the **negative** or **outlier** class. The negative class samples do not form the statistically representative sample of the class.

Based on the research explorations, one-class classification can broadly be built based on the following categories:

1.  Learning with target class samples only.
2.  Learning with target class samples and some amount of weakly sampled negative or outlier class samples. In some situations, these samples can be artificially generated.
3.  Learning with target class samples and data samples of negative classes which are not labeled.

# [5.4 Zero-Shot Learning](#toc.xhtml#s130a)

Generally, the classification model can detect the classes for which it is trained. Suppose there is a problem wherein the classifier has to be built for the data set which has few samples belonging to a class/es which are not labeled. The normal classifier models are not fit for these kinds of problems. *Zero-shot learning is a solution, which aims to classify the given samples into a new class for which the classifier is not trained*. So, zero-shot learning is a learning method in which the learner during the test time, observes the classes which were seen during the training and makes a prediction as to which category it belongs to.

A domain adaptation is a learning algorithm that is trained for the given data distribution (source) and allowed to perform on different data distribution (target). In that way, zero-shot learning can be thought of as the worst-case of domain adaptation. In zero-shot learning the training data consists of the following categories:

1.  The data samples of classes (source classes) for which the class labels exist.
2.  The data samples of classes (target classes) for which the class labels don’t exist.
3.  Support data that contains the information about the semantics or word embeddings or descriptions of both the source and target classes available at train time. It is important data that has data embedded in both the source and target classes.

Different types of zero-shot learnings are as follows:

*   Transductive Zero-Shot Learning, in which data samples for both source and target classes exist and support data exists for both source and target classes.
*   Inductive Zero-Shot Learning, in which data samples for source classes exist and support data for both source and target classes exists.
*   Generalized Zero-Shot Learning, in which the test data contain samples that belong to both source and target classes.
*   Conventional Zero-Shot Learning, in which the test data contain samples that belong to only target classes.

*[Figure 5.2](#c05.xhtml#fig5_2)* shows how the unseen class features are described by their attributes and the zero-shot learning model predicts it by using the trained features:

![](images/Figure-5.2.jpg)

**Figure 5.2:** Zero-Shot Learning

Applications of Zero-Shot Learning:

1.  Multimedia information retrieval
2.  Multi-task reinforcement learning
3.  Natural language processing
4.  Image classification
5.  Semantic segmentation

# [5.5 One Shot, Few Shot, K-Shot, or N-Shot Learning](#toc.xhtml#s131a)

In the one-shot learning mechanism, the system learns about the object categories from one or only a few training images or samples. This situation occurs when there are object categories that have unlabeled images or few samples to be used for training. For example, in the face recognition problem, to recognize a person’s face, the model has to be trained with a lot of images. When an image of a new person for which the model is not trained is used, it fails to recognize the face of the person. The main theme behind the one-shot learning algorithm is to build models which learn the differences between the class of images. So, when an image is given to the model, it returns a value closer to zero if the difference between the images is less than a threshold and returns a value more than the threshold otherwise. Siamese networks are based on the one-shot learning mechanism.

One-shot learning involves three main challenges:

1.  Firstly, representation of objects and categories or how one should model objects and categories.
2.  Secondly, building or learning of models for such purpose.
3.  Thirdly, recognition and detection of known object or category in different scenarios like when it is not clear due to lighting changes, some part/s are not displayed or covered by other objects.

One-shot learning can be broadly categorized based on how it learns or transfer knowledge from the given minimal set of examples using the prior knowledge of the learnt categories.

Knowledge transfer by contextual information learns the differences between the new classes and previously learned classes based on the global knowledge of the scene in which the object is placed. For example, the algorithm by *D. Hoiem et al*., to prune object detection uses contextual information from scene geometry and camera height.

Knowledge transfer by sharing features uses sharing of parts or features of objects across classes for knowledge transfer.

Knowledge transfer by model parameters gains knowledge transfer by reusing the model parameters and using the similarity between the previously and newly learned classes.

Few applications of one-shot learning are given as follows:

*   Face recognition
*   Low data drug discovery
*   Custom object detection tasks

Classification of data samples into binary or multiclass can be achieved using Convolutional Neural Networks and LSTM models also. The details of these networks are covered in *[chapter-9 “Design with Deep Learning”](#c09.xhtml)* and *[Chapter-11 “Long Short Term Memory”](#c11.xhtml)* respectively. Many other classification techniques exist based on the characteristics of the data set, purpose or objective, expected outcome, and properties of the data set. A few of them are listed as follows:

# [5.6 Clustering techniques](#toc.xhtml#s132a)

The main aim of the clustering techniques is to separate groups of data with similar properties and assign them to the clusters. It is one of the unsupervised learning methods in which the input data is not labeled and still inferences are drawn on them. In the next few sections, some of the popular clustering techniques are discussed and their types or algorithms are listed:

# [5.7 Distribution-Based Clustering](#toc.xhtml#s133a)

These clustering algorithms are based on statistics. *Clustering is performed based on the distribution in the data such as Gaussian, Bernoulli, Poisson, and Log-normal type distribution*. Generally, Gaussian distribution is used and Gaussian Mixture Models are an example of that. Clusters are defined based on how likely the sample included in a cluster belongs to the same distribution. In this technique, the data set is modeled using a limited set of Gaussian distributions which are randomly initialized and by iterative process the optimization of the clusters will be performed. The complexity of the model increases to achieve better performance of clustering. These models use correlation and dependency among attributes and hence, the complexity increases and it becomes difficult to use them on a real data set. These models do not perform or work if there is no distribution within the data set or a mathematical model cannot be fit on the data set. For these models to work, it is assumed that the data set has inherent distributions that are stated previously. The clusters formed will have Gaussian distribution with the samples within them.

During the clustering process, as the distance of the sample from a particular distribution increases, the probability that a point belongs to that cluster decreases. If the distribution within the data is not known, it is advisable not to use the distribution-based clustering technique. Examples of this kind of clustering technique include:

*   Gaussian mixture models
*   Expectation-maximization algorithm
*   Auto-class clustering algorithm

# [5.7.1 Density-Based Clustering](#toc.xhtml#s134a)

Another category of clustering algorithms is density-based clustering algorithm which finds non-linear shapes structure based on the density. It also avoids outliers and noise in the data. In this method of clustering, various clusters are formed based on the different densities of the data in the data space. They identify regions of varying densities and place the data points in the appropriate regions to form clusters. There are different types of density-based clustering algorithms based on how the densities are determined:

1.  **Density-Based Spatial Clustering of Applications with Noise** (**DBSCAN**): Clusters are formed based on the density of data points in the neighbourhood. It can be used in applications like anomaly detection in temperature data and clustering images of the satellite.
2.  **DENsity-based CLUstEring** (**DENCLUE**): Clusters are formed based on the density function. It can be used for clustering geo-locating tweets following natural hazards or terror attacks, then based on the size and the location of the clusters found, rescue and evacuation needs can be informed.
3.  **Ordering Points To Identify the Clustering Structure** (**OPTICS**): Clusters are formed similar to DBSCAN but vary in the way that it stores the order in which the data points are processed while clustering. It can be used for cluster analysis in Atom Probe Tomography Data.

In density-based clustering algorithms, the shape of the clusters need not be concave, oval, or spherical, but it can be in different shapes other than these.

# [5.7.2 Fuzzy Clustering](#toc.xhtml#s135a)

Generally, clustering is a technique that allows the data points to be grouped into regions based on how similar each of the data points is to one another. Most of the clustering algorithms work to find patterns or similarities between data points in the set. This tells that the data points within the cluster will be more similar as compared to those data points outside the cluster. In fuzzy clustering, the data points belong to more than one cluster at a given point in time. The fuzziness is created in this technique because it uses least-squares solutions to find the optimal location for a given data point. This allows the optimal location of the data point to be in the probability space between two or more clusters. Generally, they are used in applications like data analysis of Metabolomics, color image segmentation, and text document categorization and annotation.

The fuzzy clustering is broadly classified into two categories given as follows:

*   Classical fuzzy clustering
*   Shape-based fuzzy clustering

Classical fuzzy clustering has varieties of algorithms given as follows:

1.  Fuzzy C-Means Algorithm (FCM)
2.  Gustafson-Kessel (GK) Algorithm
3.  Gath-Geva Algorithm

Shape-based fussy clustering has varieties of algorithms given as follows:

1.  Generic shaped
2.  Elliptical shaped
3.  Circular shaped

# [5.7.3 Grid-Based Clustering](#toc.xhtml#s136a)

Grid-based clustering is generally used for massive data sets. The basic idea in this technique is to organise the data set with grid representation and to merge the grid cells to generate clusters. In this technique, the clustering is not based on the data points but on the value space that surrounds the data points.

Different types of grid-based clustering are given as follows:

1.  CLIQUE (CLustering In QUEst)
2.  STING (STatistical INformation Grid)
3.  MAFIA (Merging of Adaptive Intervals Approach to Spatial Data Mining)
4.  Wave Cluster
5.  O-CLUSTER (Orthogonal partitioning CLUSTERing)
6.  Axis shifted grid clustering algorithm
7.  Adaptive mesh refinement

# [5.8 Association Rules Techniques](#toc.xhtml#s137a)

In data mining, finding frequent patterns is a common task. By patterns, it means how often two or more items co-occur. In application domains, various examples require this kind of mining to be performed. For example:

*   When the users are visiting a particular website, which webpages they may visit in the same session?
*   When a customer buys product A, which other products he/she may buy together?
*   During medical diagnosis, if a person has got disease A, what new symptoms or side effects could occur?
*   Using census data, if specific public services or public businesses are set up what other services or businesses will be affected or need to be set up?
*   During the synthesis of artificial proteins, if amino acid A is used then which other amino acids need to be considered since different amino acids are associated together?
*   The banks try to identify the preference of different customer groups, products based on their interest and liking using association rules as part of **Customer Relationship Management** (**CRM**).

Association rules are a technique that discovers interesting associations among variables in the data sets. Association rules can also be thought of as simple if-then-else statements which discover association or relationships among variables in relational databases or specific data repositories. Association rule mining can be thought of as a technique that aims to find frequent patterns, associations or relationships, and correlations among independent variables in the data sets. These association rules are generally called **positive association rules**. While the association rules which builds the relationship based on infrequence patterns is called **negative association rules** which are gaining interest in recent days. These rules make an impact in the medical domain where infrequent patterns during the diagnosis of a disease may give insights on new diseases or side effects of the current disease.

The association rule has two parts:

*   An antecedent (if) and
*   A consequent (then)

An antecedent is an independent variable that is found in data and a consequent is a variable that is found in combination with the antecedent. In other words, an antecedent is a combination of independent variables which are studied or analyzed to determine which other combinations of variables are implied by this combination.

**For example:**

If a customer buys a pen (cartridge pen) then he/she is 70% likely to buy cartridges.

In the preceding example, the pen is the antecedent and the cartridges are the consequent.

*[Figure 5.3](#c05.xhtml#fig5_3)* shows the shopping carts of different customers and association rule learning aims to discover the buying patterns which gives interesting associations between the variables in the data set:

![](images/Figure-5.3.jpg)

**Figure 5.3:** Association Rules Learning

Some of the common terms which are used in associated rules mining are given as follows:

*   **Support**: This measure gives the frequency of a variable in all the transactions. The measure applies to the combination of variables, hence the support of (A, B) will be the frequency of transactions in which X and Y will appear together. It is given by the following equation:
    
    *Support (A, B) = Transactions containing A and B / Total number of transactions*
    
    The value of support for a variable or combination of variables will help to decide which of them can be helpful for the discovery of association rules. The variables with a higher value of support will be generally considered for building association rules.
    
*   **Confidence**: This measure gives the likelihood of the consequent given the selection of antecedent. Mathematically, it is the conditional probability of the consequent given the antecedent. It is given by the following equation:
    
    *Confidence (A, B) = Transactions containing both A and B / Transactions containing A*
    
*   **Lift**: This measure determines the probability of having a consequent with the knowledge of the antecedent over the probability of having a consequent without the knowledge of the antecedent. It is given by the following equation:
    
    *Lift (A, B) = (Transactions containing both A and B / Transactions containing X) / Fraction of transactions containing Y*
    

For all cases where A leads to having B in the transactions, the value of lift will be greater than 1.

Association rules are generally built to satisfy the given minimum support and minimum confidence at a specific time and are generated by first applying the minimum support to all frequent transactions in a data set. Then these frequent transactions and constraints of minimum confidence are used to generate the rules.

It is a tedious method to find the frequent transactions in a data set because it requires studying all the possible transactions in the data set. And it requires a lot of computations to be performed to find them. There are various algorithms that exist to find frequent transactions and the most popular algorithm among them is the Apriori algorithm.

Given a superset S of item sets then all the possible item sets will be a power set over S and will have size 2n-1 (the empty set is not included as it is not a valid item set) where n is the number of items in S. The size of the power set grows exponentially in ‘n’, but there exists an efficient search using the anti-monotonicity property which is also called the downward-closure property of support. This property guarantees that for an infrequent itemset, all of its supersets must also be infrequent and hence, for a frequent item set, all of its supersets must also be frequent.

The Apriori algorithm is based on the level-wise search algorithm mentioned previously. Let Tk be the set of frequent item sets of size k and their corresponding candidates be D. The algorithm first starts scanning the database and the frequent item sets of size 1 are searched by counting the occurrence of each item and then it collects those items that satisfy the minimum support requirement. The following steps are repeated till all the frequent item sets are extracted:

1.  From the frequent item sets of size k, generate Tk, candidates of frequent item sets of size k+1
2.  Calculate the support of each candidate of frequent item sets by scanning the entire database.
3.  Determine Tk+1 by adding those item sets that satisfy the minimum support requirement.

The Apriori algorithm has the advantage of easy implementation and good performance by reducing the size of candidate sets but it also has the following disadvantages:

*   It scans the entire database multiple times to determine the support.
*   It uses more time, space, and memory for the candidate generation process.
*   It is more suitable for small databases which have large support factors.

For example, suppose if it is required to generate 260 candidate item sets to obtain item sets of size 60 which is not efficient in terms of time, space, and memory requirements.

There are different types of association rules techniques given as follows:

*   Multi-level association rules
*   Multi-dimensional association rules
*   Weighted association rules
*   Multi-relational association rules
*   Fuzzy association rules

# [5.9 Regression Techniques](#toc.xhtml#s138a)

The *[Chapter-2, Supervised Machine Learning](#c02.xhtml)* covered the details on linear regression, discussing the learning method and the kinds of problems it is used to solve. This section tries to uncover the details of other regression methods.

**Note:** Association rules technique have been extended to big data. Apriori algorithm tries to find frequent items sets or association rules. It finds the positive association rules. There are algorithms which are used to find the negative association rules.

# [5.10 Logistic Regression](#toc.xhtml#s139a)

Logistic regression is a statistical model of regression which uses the logistic function to model a binary dependent variable. The binary dependent variable takes two values like pass/fail, yes/no, sick/non-sick, which are mapped to two values 0 and 1. Logistic regression can be expressed using the logit function which is given as follows:

*log (p(X) / (1 – p(X)) = b + aX*

The left-hand side of the preceding expression is called the logit function and it takes the values between 0 and 1. It is also called the log-odds function and expression, *(p(X) / (1 – p(X))* is called the **odds**. X is the independent variable and b is the bias term. If we take the inverse of the preceding function, it gives the following equation:

*p(X) = eb +a X / (1 + eb + aX)*

The right-hand side of the equation is the sigmoid function and is represented by the S-shaped curve. The following figure gives the graphical representation of the logistic regression and that it gives the value between the range 0 and 1, hence they can be mapped to probabilities of an outcome (p(X):

![](images/Figure-5.4.jpg)

**Figure 5.4:** Logistic Regression

The logistic regression has different types based on the properties of dependent and independent variables. They are given as follows:

Types of logistic regression:

*   **Binary Logistic Regression**, the dependent variable (Y) takes only two values for an independent variable (X). For example, identification of email to be spam or not, detecting if the person is healthy or infected.
*   **Multinomial Logistic Regression**, the dependent variable takes more than two categorical values which are not ordered for an independent variable (X). For example, if the problem is to find the most-used car type in some years, then the car type will be more than two.
*   **Ordinal Logistic Regression**, the dependent variable takes more than two categorical values which are ordered for an independent variable (X). For example, answers in an opinion poll (agree/disagree/neutral) and scores on a test (poor/average/good).

Logistic regression works good for binary classification and different kinds of data but it has its disadvantages which are listed as follows:

Disadvantages of logistic regression:

1.  Logistic regression assumes a linear separation between independent and dependent variables.
2.  It will not perform better for smaller data sets.
3.  It expects the outcome to be categorical and does not work on continuous values.

# [5.11 Ridge Regression](#toc.xhtml#s140a)

The cost function for the linear regression as discussed in the *[Chapter-2 “Supervised Machine Learning”](#c02.xhtml)* is given by the following equation, where m is the number of data samples, *h(y)* is the estimated value of y for a given sample, and y is the actual value corresponding to that sample. The value (*h(y) – y)2*, gives how far or close is the estimated value from the actual value. This value needs to be minimized to find the optimal line that fits the given samples:

*|| h(y) – y² || = || h(y) – (aX)² ||*

Where a is the vector of co-efficient that is determined by the learning method to minimize the cost function. But when the data samples suffer from multicollinearity, the least-squares estimate will be unbiased, but their predictor variables will have variances so large that they may be far from the true value. In that scenario, a few coefficients of ‘a’ will predominately drive the outcome of the data samples. That means the magnitude of a few co-efficient will be higher than the rest and hence, the outcomes will be unevenly driven by these predictor parameters. So, a regularization mechanism needs to be used which can reduce the value of this co-efficient so that the outcome is not biased by a few coefficient. Ridge regression does this by penalizing the coefficient so that the magnitude of the coefficient is reduced if they are far from zero. The cost function of the ridge regression is given by the following equation:

*|| h(y) – y² || + λ ||a²|| = || h(y) – y² || + λ*

Where λ is the regularization penalty term, it is used to control the penalty coefficient. By changing the values of λ, the penalty co-efficient is controlled so that the coefficient of magnitudes are adjusted and the estimates are determined with minimum error. The λ is a hyperparameter, it is not learnt but it is set to a value that minimizes the cost function of the ridge regression. The λ is called the L2 penalty since it applies to squared co-efficient.

Ridge regression can be used in place of linear regression when:

*   A high correlation exists among the predictor coefficient (‘a’).
*   The number of predictor co-efficient are comparatively more which makes the variance approach infinity (when ‘m’, the number of data samples approaches ‘n’, the number of predictor co-efficient (‘a’)).

# [5.12 Lasso Regression](#toc.xhtml#s141a)

Lasso regression is conceptually similar to the ridge regression defined previously except that the λ, the penalty term is applied to the sum of the absolute value of the coefficient, hence is also called the L1 penalty term. The cost function for the Lasso regression is given by the following equation:

*|| h(y) – y² ||2 + λ |a| = || h(y) – y² || + λ*

Using the L1 penalty as the preceding equation allows that many coefficient is exactly zeroed in Lasso regression but this would not happen in the ridge regression.

# [5.13 ElasticNet Regression](#toc.xhtml#s142a)

Lasso regression tends to do well when there are a small number of important predictor parameters and the remaining are close to zero. This means only a few predictor parameters influence the outcome. Ridge regression works well when there are many large parameters and are of almost the same value, hence most predictor parameters influence the outcome. ElasticNet regression tries to get the best of the ridge regression and Lasso regression by using both the penalty terms given as follows:

*|| h(y) – y² || + λ |a| = || h(y) – y² || + λ ((1 – α) / 2) + α*

Now there are two penalty parameters to tune, λ & α which allows more control over the performance.

More regression techniques are available and each of them is used based on the type of data set, the properties of the data set, the predictor coefficient, and the expected outcomes. A few of them are listed as follows:

*   Stepwise Regression
*   Quantile Regression
*   Ordinal Regression
*   Poisson Regression
*   Bayesian Linear Regression.
*   Support Vector Regression
*   Negative Binomial Regression
*   Principal Components Regression (PCR)
*   Partial Least Square (PLS) Regression
*   Quasi Poisson Regression, its types are given as follows: 
    *   Cox Regression
    *   Tobit Regression

# [5.14 Factors for selecting the right regression model](#toc.xhtml#s143a)

It is often difficult to decide which is the right regression technique for the given dataset and the use case. It depends on the characteristics of the independent and dependent variables, the relationship and impact of the variables of the dataset, and other factors. Following are a few of these factors that can help to decide the type of regression models:

*   If a single dependent variable is predicted using a set of independent (predictor) variables, then a multiple regression model is used.
*   If there is a linear relationship between the independent and dependent variables, then a linear regression model is used.
*   If the problem is to classify the given data set into two classes, predict the probabilities of the two classes, or the data set follows the binomial distribution of the dependent variable then a logistic regression model is used.
*   Use the metrics like adjusted R-squared, residual or error terms, and P-values for the independent variables to select the right regression model.
*   Use stepwise regression and best subsets regression which are automated tools that help to select the right model during the exploratory phase by providing statistics that balance the trade-off between precision and bias.

**Note:** Ridge, Lasso, and ElasticNet regression techniques are closely related in terms of cost function which is defined on the properties of the data set. Better understanding of the characteristics of the data set enables one to decide which technique is most appropriate for the given problem.

# [5.15 Use Cases and Examples](#toc.xhtml#s144a)

Let us consider a programming example to illustrate the use of the Apriori algorithm of the association rules technique, which has an application of market basket analysis. The “*Beer and Diapers*” case is the most commonly used example in market basket analysis. This case was seen by a large retailer who found an unusual pattern of purchase by customers who were buying beer and baby diapers at the same time. These patterns of purchase were found out by mining the transaction data of all the customers. Similar kinds of insights can be obtained by mining the large transaction data of purchases. Using these insights, the large retailers were able to set up recommendations for the customers which would enable them to make more sales. The following program uses the Apriori algorithm of the association rules technique and applies it to the online retail data set to identify the interesting purchase combinations. The Apriori algorithm is used to find the frequent item sets required for association rules:

`import pandas as pd`

`from mlxtend.frequent_patterns import apriori`

`from mlxtend.frequent_patterns import association_rules`

The library ‘`mlxtend`’ needs to be installed using ‘`pip install mlxtend`’.

`# Read the online retail transaction data of purchases`

`df = pd.read_excel('./OnlineRetailData.xlsx')`

`print ("Completed reading the xlsx file")`

`print (df.head())`

The `OnlineRetailData.xlsx` is downloaded from the link ***[http://archive.ics.uci.edu/ml/machine-learning-databases/00352/Online%20Retailxlsx](http://archive.ics.uci.edu/ml/machine-learning-databases/00352/Online%20Retailxlsx)***. *[Table 5.1](#c05.xhtml#tab5_1)* gives the transaction data of purchases of few products by customers for different countries in Europe:

![](images/p193.jpg)

**Table 5.1:** Transactions of purchases of products

The following lines of code do the initial pre-processing of data:

`df.dropna(axis=0, subset=['InvoiceNo'], inplace=True)`

`df['InvoiceNo'] = df['InvoiceNo'].astype('str')`

`df['Description'] = df['Description'].str.strip()`

After checking the data values for the transactions, it was seen that the transactions need to be pre-processed. The preceding lines of code do the pre-processing for the following clean up:

*   Few descriptions have spaces and they need to be removed to be clean.
*   Few transactions do not have invoice numbers and these need to be removed or dropped from the data set.

The following lines of code allow to see each transaction as a row where the products are listed in columns for an invoice number and they are one-hot encoded. For the sake of visualization, only few transactions for the country ‘*Finland’* are considered and listed for only five products purchased but the actual list contains around 288 invoice numbers:

`basket = (df[df['Country'] =="Finland"]`

`.groupby(['InvoiceNo', 'Description'])['Quantity']`

`.sum().unstack().reset_index().fillna(0)`

`.set_index('InvoiceNo'))`

`print (basket.head())`

 
| **Invoice No** || **10 COLOUR SPACEBOY PEN** || **12 COLOURED PARTY BALLOONS** || **12 DAISY PEGS IN WOOD BOX** || **BLUE PUDDING SPOON** || **CHOCOLATE THIS WAY METAL SIGN** |
| --- | --- | --- | --- | --- | --- |
| 536540 || 0 || 0 || 0 || 0 || 0 |
| 539421 || 24 || 0 || 0 || 0 || 0 |
| 548664 || 0 || 0 || 12 || 0 || 0 |
| 548718 || 0 || 0 || 0 || 0 || 144 |
| 548858 || 0 || 0 || 0 || 0 || 0 |
| 549118 || 0 || 0 || 12 || 48 || 0 |
| 549196 || 0 || 0 || 12 || 0 || 0 |

**Table 5.2:** Values of quantities purchased

As seen in *[Table 5.2](#c05.xhtml#tab5_2)*, there are a lot of zeros and a few are positives which indicate the value of quantities purchased. To transform those values to one hot encoding, any value less than zero is made zero and anything more than zero is made 1 which is achieved by the following code:

`def normalize_units(x):`

`if x <= 0:`

`return 0`

`if x >= 1:`

`return 1`

`basket_sets = basket.applymap(normalize_units)`

`mostused_itemsets = apriori(basket_sets, min_support=0.06, use_colnames =True)`

The `mostused_itemsets` contains the frequent itemset that has the support of 6% and it was easier to get since the data is organized. The number 6% was chosen so that enough useful examples can be observed. The function is given by the apriori library.

Now let us generate rules using the association rules function for the most frequent items generated before with their corresponding support, lift, and confidence. Following is the display of the top five rows of the rules data frame where the header of columns is given in bold. Few of the columns are dropped to fit into the rows for visualization purposes and only the significant columns are retained:

`rules = association_rules(frequent_itemsets, metric="lift", min_threshold=1)`

`print ("The rules are given below: ")`

`print (rules.head())`

`Antecedents, Consequents, Support, Confidence, Lift`

`frozenset({'GREEN REGENCY TEACUP AND SAUCER'}),frozenset({'PINK REGENCY TEACUP AND SAUCER'}),0.09027777777777778,0.7222222222222222,7.428571428571428`

`frozenset({'PINK REGENCY TEACUP AND SAUCER'}),frozenset({'GREEN REGENCY TEACUP AND SAUCER'}),0.09027777777777778,0.9285714285714285,7.428571428571428`

`frozenset({'GREEN REGENCY TEACUP AND SAUCER'}),frozenset({'REGENCY CAKESTAND 3 TIER'}),0.08680555555555555,0.6944444444444444,2.816901408450704`

`frozenset({'REGENCY CAKESTAND 3 TIER'}),frozenset({'GREEN REGENCY TEACUP AND SAUCER'}),0.08680555555555555,0.352112676056338,2.816901408450704`

`frozenset({'ROSES REGENCY TEACUP AND SAUCER'}),frozenset({'GREEN REGENCY TEACUP AND SAUCER'}),0.11458333333333333,0.6875,5.5`

`frozenset({'GREEN REGENCY TEACUP AND SAUCER'}),frozenset({'ROSES REGENCY TEACUP AND SAUCER'}),.11458333333333333,0.9166666666666666,5.5`

From the preceding rules, many insights can be drawn. First of all, the higher value of lift indicates that the product combinations for a given number of transactions are more frequent than expected. With the domain knowledge, better insights can be drawn based on the combination of values of confidence and lift. For illustration purposes, let us consider the results for a specific combination of lift and confidence values with lift:

`print (rules[(rules['lift'] >= 6) &`

`(rules['confidence'] >= 0.8)])`

`Antecedents, Consequents, Support, Confidence, Lift`

`frozenset({'PINK REGENCY TEACUP AND SAUCER'}),frozenset({'GREEN REGENCY TEACUP AND SAUCER'}), 0.09027777777777778,0.9285714285714285,7.428571428571428`

`"frozenset({'ROSES REGENCY TEACUP AND SAUCER', 'PINK REGENCY TEACUP AND SAUCER'})",frozenset({'GREEN REGENCY TEACUP AND SAUCER'}), 0.08680555555555555,0.9259259259259259,7.407407407407407`

`frozenset({'PINK REGENCY TEACUP AND SAUCER'}),"frozenset({'ROSES REGENCY TEACUP AND SAUCER', 'GREEN REGENCY TEACUP AND SAUCER'})", 0.08680555555555555,0.8928571428571428,7.792207792207792`

`"frozenset({'GREEN REGENCY TEACUP AND SAUCER', 'REGENCY CAKESTAND 3 TIER'})",frozenset({'ROSES REGENCY TEACUP AND SAUCER'}), 0.08680555555555555,1.0,6.0`

From the preceding results, it can be observed based on the confidence and lift values that PINK REGENCY TEACUP AND SAUCER and GREEN REGENCY TEACUP are purchased together with high probability and PINK REGENCY TEACUP AND SAUCER, GREEN REGENCY TEACUP AND SAUCER, and ROSES REGENCY TEACUP AND SAUCER are purchased together with high probability.

So, with this insight, the sales of one product can be used to provide recommendations for the other product to increase the sales for that product. For example, the following is the total sales for the PINK REGENCY TEACUP AND SAUCER and GREEN REGENCY TEACUP. Based on the sales result, the recommendation for PINK REGENCY TEACUP AND SAUCER should be done to increase the sales since it is found that PINK REGENCY TEACUP AND SAUCER and GREEN REGENCY TEACUP are purchased together by the customers:

`print (basket['PINK REGENCY TEACUP AND SAUCER'].sum())`

`print (basket['GREEN REGENCY TEACUP AND SAUCER'].sum())`

`print (basket['ROSES REGENCY TEACUP AND SAUCER'].sum())`

`363.0`

`471.0`

`984.0`

# [Conclusion](#toc.xhtml#s145a)

In recent times, the data is growing enormously large beyond imagination. The data needs to be structured and organized to extract the right information and store only the required information. This brings the problem to discover more and more insights from the data to extract implicit and explicit knowledge from the data, build intelligent relationships, and make predictive and descriptive analytics that would allow intuitive decision making. Classification, clustering, regression, and association rules techniques are a few of the algorithms which supports one to extract those insights in a more practical and statistical approach and enable the big data era to be more significant rather than a problem at hand. The chapter has listed a lot of these techniques and many more do exist which were recent during the time this book is written. A look at these techniques would be interesting and proves that these can handle any kind of data involving simple to complex characteristics, small size to huge size, and new data that has been never seen before.

In the next chapter, techniques that analyze the data points or series from the past and predict the data points of the current and forecasting outcomes ahead of time are discussed. Yes, the chapter “*Time Series*” discusses the techniques which forecast data and predict time series accordingly.

# [Points to remember](#toc.xhtml#s146a)

*   The one-class algorithm helps to classify the data into two classes, in which the data for one of the classes can be easily generated or made available while for the other it is difficult to generate or they are not available.
*   The zero-shot classifier is trained to classify the given samples into a new class for which the classifier is not trained.
*   The one-shot, few shot, or K-shot classifier is used to classify the images which have a few training samples for each class or object categories that have unlabeled data.
*   The association rules mining is used to find recommendations using the relationships among the data categories.
*   The Apriori algorithm finds frequent transactions which can be used to derive useful insights.
*   Ridge, Lasso and ElasticNet have similar cost functions but different penalty terms, L1 penalty, and L2 penalty.
*   Fuzzy clustering technique allows data points to belong to more than one cluster at any given point of time.
*   If the given data set is huge, then grid-based clustering would be the right choice to start with.

# [Questions](#toc.xhtml#s147a)

1.  Mention any six classification algorithms in the supervised learning method?
2.  Given a data set and problem to classify, among classification, regression, and clustering techniques which one will apply to the given problem? Explain.
3.  State three differences between the classification, clustering, and regression techniques.
4.  What are association rules? Give its applications with two examples.
5.  Explain the Apriori algorithm with its method steps.
6.  Name any five regression algorithms.
7.  Bring out the differences between Ridge, Lasso, and ElasticNet regression algorithms with respect to the cost function.
8.  Explain briefly the density and distribution-based clustering techniques.
9.  List the different types of clustering algorithms in fuzzy and grid-based clustering techniques.
10.  A problem is given to design a recommendation system for the retail application. Among classification, regression, clustering, and association rule techniques, which technique would you use and why?

# [Multiple Choice Questions](#toc.xhtml#s148a)

1.  **Choose the correct answer** 
    1.  One-class classification is a supervised learning algorithm.
    2.  One-class classification is an unsupervised learning algorithm.
    3.  One-class classification is a semi-supervised learning algorithm.
    4.  One-class classification is a clustering algorithm.
2.  **Choose the correct answer** 
    1.  Zero-shot and one-shot classification are used for data mining.
    2.  Zero-shot learning is used to classify images into a new class for which the classifier is not trained.
    3.  Zero-shot learning is used when there are sufficient samples for the object categories to be classified.
    4.  Zero-shot learning is a regression algorithm.
3.  **Choose the correct answer** 
    1.  One-shot, few-shot and K-shot learning are trained to classify images into a new class for which the classifier is not trained.
    2.  Few-shot learning is a clustering algorithm.
    3.  One-shot, few-shot and K-shot learning are used to classify samples of the object categories that have unlabeled samples or few samples.
    4.  One-shot learning is a mining algorithm.
4.  **Choose the correct answer** 
    1.  Fuzzy clustering is used to cluster data points that always belong to a specific cluster.
    2.  Density-based clustering is based on the distribution of data points.
    3.  Distribution-based clustering is based on the density function of the data points.
    4.  Grid-based clustering is generally used when massive data points are involved.
5.  **Choose the correct answer** 
    1.  Distribution-based clustering perform clustering based on the data distribution such as Gaussian, Bernoulli, Poisson, and Log-normal type distribution.
    2.  AUTOCLASS is a density-based clustering algorithm.
    3.  DBSCAN is a density-based clustering algorithm.
    4.  STING is a distribution-based clustering algorithm.
6.  **Choose the correct answer** 
    1.  CLIQUE is a grid-based clustering algorithm.
    2.  Fuzzy C-Means Algorithm (FCM), Gustafson-Kessel (GK) Algorithm, Gath-Geva Algorithm are shape-based fuzzy clustering algorithms.
    3.  Gaussian Mixture Models are distribution-based clustering algorithms.
    4.  AUTOCLASS is a density-based clustering algorithm.
7.  **Choose the correct answer** 
    1.  DENCLUE and OPTICS are density-based clustering algorithms.
    2.  Multi-level association rules, Multidimensional association rules, and Weighted association rules are negative mining association rules techniques.
    3.  Multi-relational association rules, Fuzzy association rules are negative mining association rules techniques.
    4.  DBSCAN is a distribution-based clustering algorithm.
8.  **Choose the correct answer** 
    1.  Apriori Algorithm scans the entire database multiple times to determine the support.
    2.  Apriori Algorithm uses less time, space, and memory for the candidate generation process.
    3.  Apriori Algorithm is more suitable for large databases which have less support factor.
    4.  STING is a distribution-based clustering algorithm.
9.  **Choose the correct answer** 
    1.  Support is a measure that gives the frequency of the variable in all the transactions.
    2.  Confidence is a measure that gives the likelihood of the consequent given the selection of antecedent.
    3.  DBSCAN is a distribution-based clustering algorithm.
    4.  Lift is a measure that determines the probability of having a consequent with the knowledge of the antecedent over the probability of having a consequent without the knowledge of the antecedent.

# [Answers](#toc.xhtml#s149a)

1.  **a**
2.  **b**
3.  **d**
4.  **d**
5.  **a**
6.  **a**
7.  **a**
8.  **a**
9.  **a**

# [CHAPTER 6](#toc.xhtml#c06)

# [Time Series Analysis](#toc.xhtml#c06)

Time is an important factor while considering certain model predictions. The models considered in this chapter are based on temporal variations of the data based on time. It helps in many applications like weather forecasting, data dependency, stock market prediction, long and short-term temporal dependencies, correlation and so on., these are called **time-series data**. In simple terms, time series is a series of data points that are ordered based on time. Time is considered as the independent variable and is used for future predictions.

# [Structure](#toc.xhtml#s150a)

In this chapter, we will discuss the following topics:

*   Introduction to time series
*   Various types of time series data
*   Univariate and multivariate time series models
*   Time domain and frequency domain models
*   Linear and non-linear time series models
*   Time series models 
    *   Autoregression (AR)
    *   Moving Average (MA)
    *   Autoregressive Moving Average (ARMA)
    *   Autoregressive Integrated Moving Average (ARIMA)
    *   Vector Autoregression (VAR)
    *   Vector Autoregression Moving Average (VARMA)
    *   Fourier Transform (FFT)
*   Correlation extraction
*   Seasonal variations
*   Advanced time series methods
*   Examples and samples

# [Objectives](#toc.xhtml#s151a)

After studying this chapter, you should be able to:

*   Understand the time series data
*   Various types of time series
*   What is time series and why is it required?
*   How time series models can be used for prediction?
*   Examples or use cases of time series.

# [6.1 Introduction to time series](#toc.xhtml#s152a)

As explained earlier, time series data points are taken over time and will generally have their internal structures which will be explained in detail later in this chapter. In traditional ways, “*univariate time series*” refers to the time series that consists of single observations which are recorded sequentially over equal time increments. Later, many time series models and their different types came into the limelight. These models are used and built based on the industry type and sector. These can be simple data sets as the emission of carbon dioxide in a particular city over the period of one week and every 15 minutes are taken as data points. These data points may vary based on seasons, time of the day, nature of environment or surroundings, and so on.

Similarly, electricity fluctuations in the periodic interval are one of the data sets of time series. Analyzing and predicting various outcomes using these data sets has helped in building various time series-based models.

# [6.2 Various types of time series](#toc.xhtml#s153a)

Before jumping on to the types of time series data, let us understand the aspects which come into play while working on time series data sets:

*   **Auto-Correlation**: This is the similarity between observations as a function of the time lag between them. Some of the values will be repeated after some interval of time, these values are called **correlated**. If this automatically happens on a regular and repeated interval, this is called Auto-Correlation. For example, sinusoidal patterns are observed for the time series data types.
*   **Stationarity**: If the statistical properties don’t change over time; these values are called **stationary**. Statistical properties are the constant mean and variance values. For example, share prices of certain stocks remaining stationary over a period of time.
*   **Seasonality**: Some of the periodic fluctuations are seasonality values. For example, electricity consumption, share market values, online sales peaking values in certain festive seasons, and so on.

Following are some of the examples of stock price indications over a period of time. The “*plotly*” library is used to draw these graphs in Jupyter notebooks. If this library is not present, it can be installed using:

`!pip install plotly`

![](images/Figure-6.1.jpg)

**Figure 6.1:** Installation of the “plotly” library in the jupyter notebook

Following steps are the examples for importing the plotly library and initializing the data frame “df” with the stocks data set:

![](images/Figure-6.2.jpg)

**Figure 6.2:** Importing the “stocks” data set and displaying a few examples

![](images/Figure-6.3.jpg)

**Figure 6.3:** Importing the “stocks” data set and displaying a few examples with the time series graph

Following code is used to display the various companies’ plotted stock values versus date (2018-2019):

`# Various company stock value versus date (2018-2019)`

`import plotly.express as px`

`df = px.data.stocks()`

`fig = px.line(df, x="date", y=df.columns,`

`hover_data={"date": "|%B %d, %Y"},`

`title='Customized labels')`

`fig.update_xaxes(`

`dtick="M1",`

`tickformat="%b\n%Y")`

`fig.show()`

![](images/Figure-6.4.jpg)

**Figure 6.4:** Stock prices versus date (2018-2019)

Time series models are generally created with various aspects, these aspects can be “*trends*”, “*seasonal*” or “*cyclic*” in nature. These are described in detail as follows:

*   **Trend**: Based on changing directions of the data that is generated. This change can either be increasing or decreasing in nature. There is no need for this to be linear in nature; this can be of any form. For example, variation of heartbeats of adults based on age can be a trend. People with diabetes generally will have variations in blood pressure, this can be a trend based on age and food habits in a certain period.
*   **Season**: Time series data is affected by seasonal factors which can be weather, time of the year, or a particular day of the month. Seasonality as explained previously is one of the important factors and is assumed to be constant over a certain time period.
*   **Cycle**: When the data rises and falls in a certain period of time, not with any fixed frequency, it is termed as a cycle. These variations or fluctuations can be due to various aspects like economic conditions, weather, environment, business trends, and so on. It is assumed that these cycles repeat at finite time intervals.

# [6.3 Univariate and multivariate time series models](#toc.xhtml#s154a)

Univariate time series data contains “*Only One*” variable and this is the only variable that varies over time.

**Example**: Data collected from a sensor measuring the intensity of light (Lumens), or a sensor measuring the temperature of a room, and so on.

Univariate variables will be single or one-dimensional and will not have any dependency:

![](images/Table-6.1.jpg)

**Table 6.1:** Table depicting the Univariate Variable

**Multivariate time series** data contains multiple variables and many or all of them vary over time.

**Example**: Data collected from various sensors measuring temperature, humidity, wind speed, moisture, and so on., in a place.

Multivariate variables will be more than one-dimensional and will have dependency over other variables:

![](images/Table-6.2.jpg)

**Table 6.2:** Table depicting the Multivariate Variables

# [6.4 Time domain and frequency domain time series models](#toc.xhtml#s155a)

**Time Domain Series**: In this time series, the examination or analysis is typically done for amplitude versus time characteristics of a measure of a signal.

**Frequency Domain Series**: These are typically sinusoidal waveforms and may contain amplitudes, frequencies, and various phases of the sinusoidal wavelets.

The following table explains in detail the differences between “*Time Domain Series*” and “*Frequency Domain Series*”:

![](images/Table-6.3.jpg)

**Table 6.3:** Difference b/w time and frequency domain series

# [6.5 Linear and non-linear time series models](#toc.xhtml#s156a)

The linear time series is generally modeled with ARMA and ARIMA, but non-linear time series requires the output to be passed through the non-linear transfer functions such as sigmoid or Tanh. (Refer to *[Chapter-10, Design with Deep learning/MLP](#c10.xhtml)*, for the non-linear functions)

In most of the general linear systems, an output “y” is that of a linear function of external inputs “x” and if any previous outputs.

# [6.6 Time series models](#toc.xhtml#s157a)

There are various popular time series models which are used for making different predictions.

# [6.6.1 Autoregression (AR)](#toc.xhtml#s158a)

This method is generally used for “*univariate time series*” and doesn’t include trend and seasonal components. In this method, forecasting of the variable as a linear combination of the observations/predictors at various prior time steps (past values) is modeled.

These models are flexible at handling a wide variety of different time series patterns. In the autoregression time series models, observations from the previous time steps are used as input to the regression equation and in the subsequent steps, these are used to predict values. AR is a simple and random process that is used to describe time-varying processes.

Many times autoregressive models are used on stationary data and the application of AR can be found in business-related models, economics, and so on.

# [6.6.2 Moving average (MA)](#toc.xhtml#s159a)

This method is generally used for time sequence steps involving residual errors as a linear function from mean processes. In simple terms, this is a calculation that takes the arithmetic mean of a given series of data. For example, this series of data can be price values or certain days of a month, and so on.

This method is also suitable for “*univariate time series*” without involving trends and seasonal components. Moving average model uses past forecast errors in a regression-like model instead of using the past values of the forecast variable in the regression. MA is used for stock price prediction or returns of certain traded-stock values.

# [6.6.3 Autoregression Moving Average (ARMA)](#toc.xhtml#s160a)

This model is built by combining the AR and MA models. This is a linear function of observations and residual errors at the prior time steps. This method is suitable for the “*univariate time series*” without involving the trend and seasonal components.

ARMA model is a tool used for understanding and predicting the future values in the time series. The AR part of the ARMA model is used for regressing the variable and the MA part is used for an error that has occurred various times in the past.

ARMA models find their applications in many areas including stock price trend analysis, market fluctuation observation, and so on.

# [6.6.4 Autoregressive Integrated Moving Average (ARIMA)](#toc.xhtml#s161a)

The Autoregressive Integrated Moving Average technique are used to build models using the sequence of a linear function of differenced observations and residual errors. This is one of the widely used models in time series forecasting. Especially the ARIMA models and exponential smoothing models are the most widely used and they provide complementary approaches to each other.

When we talk about ARIMA models, the main thing that comes to our mind is “*Stationarity*” and “*differencing*”. Stationarity time series as explained earlier is nothing but whose properties don’t depend on time.

Many times, the time series with cyclic behaviors is stationary. These cycles are not fixed in length, we cannot guarantee the peaks and troughs of the cycles as they are occurring at constant intervals, thus making these models a little confusing.

When we make consecutive observations, for example, about some company stock prices over a period of one month or one year, we compute the differences between these observations, this is called differencing. Both stationarity and differencing go hand-in-hand in the ARIMA models.

Logarithms is a kind of transformation that helps in stabilizing the variance of time series. As explained earlier, differencing help in stabilizing the mean of a time series (this is possible by removing the changes in the level of time series) and eliminates trend and seasonality.

# [6.6.5 Vector Autoregression (VAR)](#toc.xhtml#s162a)

The Vector Autoregression method models generally use AR in the model. This is a generalization of AR to multiple parallel time series. These are the “*multivariate*” time series.

VAR is used to capture the relationship between multiple quantities which change over time. The variables present in the VAR models contain past values, values of other variables, and error values. This is the reason why it is stated as multivariate in nature.

These kinds of models are used in business predictions, economics, and natural sciences.

# [6.6.6 Vector Autoregression Moving Average (VARMA)](#toc.xhtml#s163a)

Vector Autoregression Moving Average is the combination of VAR and VMA models along with the generalized ARMA model. This supports the multivariate stationary time series data. Generally speaking, this model is not used much as the combinations of other models are readily available at our disposal.

This model is sometimes used as an extension of the ARMA model with parallel values of the time series data.

# [6.6.7 Fourier Transforms (FT)](#toc.xhtml#s164a)

Fourier Transform is one of the well-known and traditional time series data. This can be described as a combination of fast-changing and slow-changing things. This is generally an array that describes the time series as a combination of oscillations.

FT is a method for expressing a linear function as the sum of periodic components. There are various sub-methods of Fourier Transforms described as follows:

*   **Discrete Fourier Transform** (**DFT**): This is numerical computing and is nothing but both the function and its Fourier transform are replaced by the discretized counterparts.
*   **Fast Fourier Transform** (**FFT**): This was found by Gauss (1805) and made to the limelight by Cooley and Tukey. When the DFT computation is done fast, it is called FFT.

The combination of **Numpy** and **SciPy** libraries are used to compute and analyze the DFT and FFT series. There are various other series like 2-D FFT, IFFT, and so on., which are not within the scope to be described here:

![](images/Figure-6.5.jpg)

**Figure 6.5:** Sample of Fast Fourier Transform simulated data

# [6.7 Examples and samples](#toc.xhtml#s165a)

There are various applications of the time series models. Major applications of time series data analysis help in the stock value prediction using various models as described in the earlier section of the chapter. Along with stock value prediction, other major applications of time series are as follows:

*   Weather forecasting and analysis.
*   Natural science studies and analysis.
*   Price indicator studies and analysis.
*   Certain event prediction of the time of the day and month.
*   Based on past value, feature value prediction, and analysis.
*   Anomaly detection in the sensor data can be used for a variety of applications such as preventive maintenance, intrusion detection, traffic congestion control, etc.
*   Prediction of seasonal variations such as floods, sun spots, and so on.
*   Demand-supply mismatch forecast.

# [Conclusion](#toc.xhtml#s166a)

Time series analysis is crucial for the ML/DL models. Such a model is predominantly predictive where a certain sample of data is predicted based on the previous samples. The model learns the inherent relations, temporal or spatial, among the samples and uses the same to predict the next values. Prediction accuracy can be improved with the right choice of the order of the model which in turn dictates the number of lags or previous samples to be used for the prediction. Another method to improve the accuracy is to use several models and weigh their results appropriately to get the correct results as discussed in detail in the next chapters.

# [Points to remember](#toc.xhtml#s167a)

*   Time series analysis is predominantly used for forecasting.
*   The main advantage and usage of time series are in stock market analysis and weather forecasting.
*   There are various types of models in time series analysis and only the important ones are described here.
*   Many applications will find the usage of time series analysis helpful.
*   Many predictive models can be built using the time series models or a combination of these models.
*   Forecast error, moving average, and vector autoregressive methods are popular in building the time series models.
*   Many machine learning algorithms like linear regression and decision trees can be used along with time series analysis for better model building.

# [Questions](#toc.xhtml#s168a)

1.  What is time series analysis? What is its significance?
2.  How many types of time series methods are discussed in this chapter?
3.  What are the applications and models where time series can be used?
4.  What are the most popular time series methods/models that were discussed here?
5.  Explain in simple terms, what are the components of time series data?

# [Multiple choice questions](#toc.xhtml#s169a)

1.  **Choose the correct answer** 
    1.  Time series analysis is used for prediction.
    2.  Time series is not used for dimensionality reduction.
    3.  Time series models are easy to learn.
    4.  All of the above
2.  **Choose the correct answer** 
    1.  Time series contains complex models.
    2.  Time series contains time, day, or month in the series mapped to a certain variable.
    3.  Time series contains unwanted variables.
    4.  None of the above
3.  **Choose the correct answer** 
    1.  ARIMA stands for “Autoregressive Integrated Moving Average”.
    2.  ARIMA stands for “Automated Regression Integration Model Average”.
    3.  ARIMA doesn’t have expansion.
    4.  None of the above
4.  **Choose the correct answer** 
    1.  ARMA is not a time series.
    2.  ARMA (Autoregression Moving Average) contains both AR (Autoregression) and MA (Moving Average).
    3.  ARMA (Autoregression Moving Average) doesn’t contain anything.
    4.  None of the above
5.  **Choose the correct answer** 
    1.  Stock market prediction is an application of time series data.
    2.  Weather forecasting is an application of time series data.
    3.  Nature analysis using a certain model is an application of time series data.
    4.  All the options are correct.

# [Answers](#toc.xhtml#s170a)

1.  **d**
2.  **b**
3.  **a**
4.  **b**
5.  **d**

# [CHAPTER 7](#toc.xhtml#c07)

# [Data Cleanup, Characteristics and Feature Selection](#toc.xhtml#c07)

In [Chapters 1](#c01.xhtml)\-[6](#c06.xhtml), many concepts of deep learning and machine learning were discussed. The data preparation, data pre-processing, data clean up, and different modes and types of data were detailed out. Supervised and unsupervised learning methods and various learning algorithms of both methods were given. The properties of data, the importance of features of data, and feature extraction techniques were discussed. Few untold information on these topics were discussed in this chapter, though the section names look similar and familiar to certain sections of the earlier discussed chapters; it has been made sure that the content is not repeated and the reader is given additional details in the sections and new information is covered. The chapter covers details on the different formats of data, how input data set should be split into training data set and test data set, and the necessity for the same. It gives detailed information on the methods used to split the input data set into training data set and test set. It brings out the properties of bias and variance in data, their purpose, and the effects it has on the learning method.

# [Structure](#toc.xhtml#s171a)

In this chapter, the following topics will be discussed:

*   Introduction
*   Data formatting
*   Normalization
*   Training/test data splitting
*   Bias-variance trade-off
*   Model overfitting and underfitting
*   Cross validation
*   Feature reduction
*   Examples and samples

# [Objectives](#toc.xhtml#s172a)

After studying this chapter, one should be able to:

*   Understand the different formats of data, the purpose they are used for, and how to change the format suitable for models.
*   Basics of normalization and its techniques.
*   Need for the splitting of data set into training data set and test data set.
*   Bias and variance of data and why they are important for building a high performing model.
*   Reasons for overfitting and underfitting of models and why they should be avoided.
*   Cross validation technique, its requirement, and the different types of cross validation techniques.

# [7.1 Introduction](#toc.xhtml#s173a)

The data formats used for building the model has a lot of significance on the performance of the model. Hence, understanding the data format, properties, types and size of data, and how they affect the performance of the model is important. Given the generic data set with enough sample’s representative of the problem and an efficient learning algorithm, the model built using those can either perform excellent or poor. Why? There are other parameters that need to be taken care of while building the model. These include the parameters which cause the model to overfit or underfit. The details of these are covered in the later sections of the chapter and the methods to avoid them are also mentioned. The key properties of the input data set, bias and variance are elaborated so that one knows how to decide the trade-off between bias and variance of the data set. The chapter is going to be a fun ride with detailed topics and a conclusion at the end.

# [7.2 Data formatting](#toc.xhtml#s174a)

Data is necessary for machine learning or deep learning problems. Given the data, it will have a ‘n’ number of attributes. Appropriate features need to be selected for the problem to derive insights. The data considered will have attributes or features which are related and unrelated. In the case of supervised learning, these features need to be checked for correlation with output. Based on the correlation, the right set of attributes should be chosen and the rest should be dropped. A sample data after formatting is shown in *[figure 7.1](#c07.xhtml#fig7_1)*.

The data is further classified into two different types based on how the data is formatted, stored, collected, and organized:

*   Structured
*   Unstructured

![](images/Figure-7.1.jpg)

**Figure 7.1:** Data after formatting

Structured data consists of:

*   **Nominal Data** consists of numbers, texts, labels and represents an object category. It is also called categorical data.
    
    **For example**:
    
    1.  Male and Female, either as M and F or 0 and 1.
    2.  Plants and Animals, either as P and A or 0 and 1.
*   **Ordinal Data** has all the properties of nominal data and can be ranked based on preferences and order.
    
    **For example**:
    
    1.  Height of people can be high, average, or low based on the height measurement.
    2.  Income of salaried persons can be high, medium, or low based on the earnings.

Unstructured data consists of all the data which is not structured or organized.

**For example:**

*   Texts, videos, images, and audios belong to unstructured data.

The data type of the attributes will generally be of two types given as follows:

*   **Quantitative data** consists of numbers only. There are two types: 
    *   **Continuous data** is generally represented using decimal or float and takes a range of values. 
        *   **For example**: 1.99, 2.55, etc.
    *   **Discrete data**, generally represented using whole numbers or discrete values and cannot be further divided. 
        *   **For example**: Count of apples and numbers 10, 20, 22, 34, etc.
*   **Qualitative data** consists of data that is not numbers: 
    *   **Interval data** does not have an origin or a base (absolute zero) and has the characteristics of nominal and ordinal data. So, interval data allows the negative values and supports only the addition and subtraction operations (because of the absence of an origin or a base). For example, the temperature values are in Celsius and Fahrenheit but not in Kelvin (Kelvin has absolute zero).
    *   **Ratio data** has the characteristics of nominal, ordinal, and interval data and in addition, it has an origin or a base. So, it allows all four operations – addition, subtraction, multiplication, and division. For example, the temperature values in Kelvin.

In the field of data science, it is also found that the data is categorized into four basic types:

*   **Numerical data** 
    1.  Numerical data represent values that are numbers and it is further divided into continuous and discrete data which have the same meaning described as earlier.
*   **Categorical data** 
    1.  Categorical data represents the characteristics of nominal and ordinal data as described earlier.
*   **Time series data** 
    1.  Time series data represents the sequence of numbers collected over some interval or period of time at specific or regular intervals of time. For example, an average number of homes sold (sales) for some years.
    2.  Time series data is not just a collection of numbers (numerical data) but they are ordered over time.
*   **Text** 
    1.  Generally, the text data is just words. For machine learning and deep learning, the words are usually converted into numbers using different approaches.

# [7.3 Normalization](#toc.xhtml#s175a)

Generally, for classification algorithms, it is required that the attributes that have different values and are in various ranges and intervals, need to be scaled so that it falls into a smaller and standard range such as -1 to 1.0 or 0.0 to 1.0. This process of transforming values from original to normalized values is called **normalization**. Normalization is important because if the attribute values are in different ranges and scales, the classification algorithms would consider a few attributes in the higher range and ignore the attributes on a lower scale. In a way, the attribute values in the lower range or scale will get diluted during the learning process and may lead to weak performing models. More details on normalization are covered in *[Chapter 3, System Analysis with Machine Learning / Un-Supervised Learning](#c03.xhtml)*.

The dynamic range of the two attributes is shown in *[figure 7.2](#c07.xhtml#fig7_2)*. It requires normalization:

![](images/Figure-7.2.jpg)

**Figure 7.2:** Sample dynamic range of attributes

There are many ways of performing normalization, a few of them are given as follows:

*   Min-Max normalization
*   Z-Score normalization
*   Box-Cox transformation
*   Decimal scaling

# [Min-Max normalization](#toc.xhtml#s176a)

In this method of normalization, each value in the attribute K that needs to be normalized will be determined using the following expression:

*new\_value = (((old\_value) – min(K)) / (max(K) – min(K)) \* (new\_max(K) – new\_min(K))) + new\_min(K)*

Where, `new_value` is the new value of the original value (`old_value`) in K. The values min(K), `max(K)`, `new_min(K)`, `new_max(K)` are the minimum and maximum values of the range of values in K for existing and newly determined values, respectively. The normalized years of experience in an organization and salary in kilo dollars are shown in *[figure 7.3](#c07.xhtml#fig7_3)*:

![](images/Figure-7.3.jpg)

**Figure 7.3:** Min-max normalization

# [Z-Score Normalization or Standardization](#toc.xhtml#s177a)

In this method of normalization, the new values for the attribute values of K are determined based on the following equation:

*new\_value = old\_value – mean(K)/σK*

Where, `new_value` and `old_value` are the new value and original value of an element in K. The mean (K) and σK are the mean and standard deviation of K.

# [Box-Cox Transformation](#toc.xhtml#s178a)

In this method of normalization, if the dependent variables do not have a normal distribution, then they are transformed into one with normal distribution. Having the data with normal distribution will help to benefit from many statistical methods based on it. It was named after *George Box* and *Sir David Roxbee Cox*. It is given by the following expression:

*Y = (X + δ)λ*

The δ (delta) is the correction factor added to X in case it is zero or negative. X is the vector of the dependent variables and Y is the vector of the new transformed values. The main thing is to find the right value of λ (lambda) to get the normal distribution. If it is zero, then the expression takes the following form:

*Y = ln(X + δ)*

Generally, λ takes the values like -1.5, -1.0, -0.5, 0, 0.5, 1.0, 1.5, etc.

# [Decimal Scaling](#toc.xhtml#s179a)

In this technique of normalization, the decimal point of the attribute values is moved to normalize. The number of decimal points to move is dependent on the maximum value of all the attribute values. It is given by the following expression:

*Normalized value of attribute = value/10j*

Where ‘j’ is the number of digits in the largest number of the attribute values.

# [7.4 Model Training and Test Splitting](#toc.xhtml#s180a)

Training and test data splitting is used for evaluating the model performance in machine learning and deep learning algorithms. This procedure involves splitting the data set into two subsets, training data set and test data set. The training data set is used during the training of the model and the test data set is used during validation or testing of the model. Why is it necessary to split the data set into two subsets?

Firstly, the developed model for a given problem and data set is expected to make predictions correctly on the unseen or new examples. For this to happen, the data set should be a good representation of the problem domain. The data set should cover all the common and uncommon cases in the domain. To achieve this, the data set should be sufficiently large and hence, the training and test splitting method are not applicable for the small data set. If the data set is small then alternative evaluation procedures like the k-fold cross validation procedure are used which will be discussed in the later section. Hence, to evaluate the performance of the model, it is required to split the data set into training and test data set so that it predicts correctly for the real-world examples.

Secondly, some models will be costly to train and in those cases, train and test evaluation procedures will be used which reduces the cost.

Thirdly, some models would have enough data set and has good performance but they need to have the evaluation of the performance of the model to be done in a short time, in those cases, train and test split evaluation procedure will be beneficial.

What is the optimal split percentage for train and split data set? The following are a few options that would be considered to choose a split percentage and they can be chosen based on the problem and data set. One can define a custom split percentage if it is specific to the problem being solved based on the availability of data. If more data is available, more portions of the data can be set aside for testing.

# [7.5 Bias and Variance Trade-off](#toc.xhtml#s181a)

Given a machine learning or deep learning algorithm, it is always required to build a model with high accuracy. The high accuracy for the model will always come at a cost, by striking out the balance between bias and variance. These terms are a part of the prediction error and an appropriate trade-off strategy that need to be worked out to balance the error percentage from prediction error terms so as to get the best of the learning algorithm to model the purpose of the problem with the given data set. The bias and variance for different data distributions are shown in *[figure 7.4](#c07.xhtml#fig7_4):*

![](images/Figure-7.4.jpg)

**Figure 7.4:** Variance and Bias combinations

The prediction error is cumulative of three types of errors which are given as follows:

*Prediction Error = Bias + Variance + Noise*

*   The bias and variance are computed using the “*golden refence*” values.
*   By making use of the formula as mentioned previously.

Noise is special as it cannot be reduced by the choice of the learning algorithm which will be inherited in the data set. The remaining error terms, bias and variance can be reduced or controlled by using the appropriate regularization terms. Bias and variance need to be controlled to avoid the overfitting and underfitting of the data set while training the learning algorithm.

Bias is the difference between the ground truth value and the predicted value by the model. The high bias would result in the underfitting of the model with large errors in the training and test data set. Hence, the low bias would result in avoiding this problem.

Variance gives the spread of the data set or variability of the model prediction for the given data point. A high variance model would result in overfitting and perfect working of the training data and would not perform better on the test data set. Hence, low variance would result in avoiding this problem.

To summarize the terms, bias and variance for the models:

*   A high bias model underfits data and makes simplistic assumptions on it.
*   A high variance model overfits the data and learns a lot from it.
*   A balanced bias and variance model would be the best fit for the data.

From the preceding definitions of bias and variance, it is seen that bias and variance need to be reduced to have a good performing model which is neither overfitting nor underfitting. So, what is the optimal trade-off between bias and variance?

As seen in the *[Chapter 2, System Analysis with Machine Learning/Supervised Machine Learning](#c02.xhtml)* and *[Chapter 3, System Analysis with Machine Learning / Un-Supervised Learning](#c03.xhtml)*, the models are generally trained using the following cost function with the objective of minimizing it:

*Y = f(X) + e*

Where Y is the ground truth value, X is the input sample, f is the function that maps input to output, and e is the error term.

Using supervised learning or unsupervised learning, the model aims to learn the function f\`(X) so that the predicted outcome Y\` is closest to Y and the prediction error is minimized.

Bias of the model is given by:

*Bias(X) = E\[f(X) – f(X)\]*

Variance of the model is given by:

*Variance(f(X)) = E\[(f (X))²\] - (E\[f\`(X)\])²*

As specified earlier, the prediction error is given by:

*Prediction error = Bias + Variance + Noise or Irreducible Error*

The expected square error for any input sample x or X is given by:

*Error(x) = E \[(Y – Y\`)²\]*

*\= E \[(Y – f\`(x))²\]*

The *error(x)* can be further written as:

*Error (x) = (E\[f\`(x)\] – f(x))² + E \[(f’(x) – E \[f\`(x)\])²\] + σe²*

*\= \[Bias\]² + Variance + Irreducible Error*

*[Figure 7.5](#c07.xhtml#fig7_5)* shows the graphs of how the model complexity changes as error vary from low to high for a given data set:

![](images/Figure-7.5.jpg)

**Figure 7.5:** Model Complexity versus Error

It also explains the under-fitting zone, over-fitting zone, training error and testing error, and irreducible error in detail. The optimal trade-off region for bias and variance is clearly depicted in the figure and maps to the discussion of bias and variance trade-off at the beginning of this section.

# [7.6 Model Overfitting and Underfitting](#toc.xhtml#s182a)

Underfitting occurs when the learning algorithm does not generalize or fit the function for the data points during training. This would be because of the high bias and less variance in the data points or an insufficient number of data points. It occurs when the model error on the training set is larger than the expected error for an ideal model. Sometimes it can occur when the model is regularized too much with regularization parameters during training.

Insufficient data means the data points used for training does not reflect or represent the problem completely. So, the model will not be able to capture the relationships among the features and hence, will not perform better and be deemed to be underfit. The following are a few methods to overcome the underfitting of a model:

*   Add more data to the data set.
*   Add more parameters to the model.
*   Increase the complexity of the model by adding different layers.
*   Increase the training time till the cost function is minimized.

Overfitting occurs when the learning algorithm generalizes or fits the function by learning the relationship among data to the fullest including noise and random fluctuations in data if any and hence, it performs excellently. This excellent performance during training negatively impacts the performance on the test data or new data as it makes wrong predictions even for small changes in the test data. Normally, overfitting is very common in machine learning or deep learning models whose learning function is non-parametric and the cost function is non-linear as the model’s learning algorithm will have enough flexibility to learn the target function. Hence, they need to apply methods or techniques to restrict, limit, or constrain the learning flexibility so that model is not overfitted.

Overfitting also happens when the data has many features but fewer examples and the model trained is too complex for the data used for training. Models tend to overfit when there is low bias and high variance in the data points. The models may tend to overfit even when the model is trained for a long time to achieve high accuracy. The following are a few methods that are generally used to avoid overfitting:

*   **Maintain a test set for validation**
    
    Split the data set into training and testing set in the appropriate proportions like 80:20, 67:33, or 50:50 so that the test set can be used for testing the model. Based on the performance of the model on the test set, it can be retrained with suitable improvements.
    
*   **Feature Selection**
    
    As too many features also lead to overfitting, it is always better to retain a few good features only rather than use all of them. Few methods that are used to select the required or relevant features are given as follows:
    
    *   **Variance Thresholds**
        
        Remove those features which are not changing from one sample to another within a certain threshold. This means their variance is not within the required threshold and hence, can be removed since they don’t add much value for the model training.
        
    *   **Co-relation Thresholds**
        
        Remove those features which are related to each other. If one value changes, the other also either decreases or increases each time. These features do not add much value to the model training and one would suffice to build the relationship with other features. For this to happen, the correlation coefficient between each pair of the features are calculated and the one which has the maximum mean of an absolute coefficient is marked for removal. Instead of maximum mean, it is compared against a coefficient threshold and those more than the threshold will be removed.
        
    *   **Genetic Algorithms**
        
        These are supervised feature selection algorithms. In this method of feature selection, the “*organism*” is represented as the candidate set of features and genes represent the individual features. The organisms are marked fit or unfit to survive based on the fitness score. Each organism is given a fitness score based on a fitness function. The organisms which are selected fit are allowed to survive and reproduce and generate a new set of organisms that are supposed to be more fit than the previous population. The best population with maximum fitness score will give the selected features to be used for training.
        
    *   **Stepwise Search-Based Selection**
        
        These are also supervised feature selection algorithms. It has two methods, forward stepwise search and backward stepwise search. In the former method, the model is trained using only one feature. And gradually, features are added and retrained. If the model performance improves, the added features are kept and the process is continued for all the features. In the latter method, the model is trained with all the features. And gradually, features are removed and retrained. If the model performance does not improve, the removed feature/s are kept and the process is continued for all the features.
        
*   **Feature Extraction**
    
    Feature extraction is a method in which a new set of reduced features is extracted from the existing features which in essence depict all the properties or relations of the original set of features. The methods of feature extraction are discussed in detail in *[Chapter 3, System Analysis with Machine Learning / Un-Supervised Learning](#c03.xhtml)* and some of the methods of feature extraction are given as follows:
    
    *   Principal Component Analysis (PCA)
    *   Linear Discriminant Analysis (LDA)
    *   Singular Discriminant Analysis (SDA)
    *   Autoencoders
*   **Early Stopping**
    
    In the case of model training using the iterative method, it is better to stop early in case the required threshold of error is met rather than continuing the training till the final iteration so that the model generalizes the data set to the fullest.
    
*   **Dropout**
    
    In some deep learning models, new layers like pooling and dropout are added so that some random or selected neurons are dropped during training. This will enable the model not to generalize too much to the relationship and properties of the data points used during training.
    
*   **Cross Validation**
    
    In this method, the input data set is divided to generate multiple train-test splits. These splits are used to tune the model. This method of splitting and tuning the model is called **cross validation** and is discussed in detail in the next section.
    
    **Regularization**: These are the techniques that are used to limit, constrain, or restrict the model flexibility to get trained to become complex. They introduce penalties to the training method and reduce the complexity of the models. These techniques are discussed in detail in the *[Chapter 2, System Analysis with Machine Learning/Supervised Learning](#c02.xhtml)* and *[Chapter 3, System Analysis with Machine Learning/Unsupervised Learning](#c03.xhtml)*.
    
*   **Ensembling**
    
    In this method, the outcomes of multiple models are combined using a mechanism like max voting and averaging to predict the final prediction of the input sample. These methods train many models parallelly and combine them to avoid overfitting. Bagging and boosting the ensemble methods are the most common techniques that are used for this purpose.
    

# [7.7 Cross Validation](#toc.xhtml#s183a)

In a classification model or prediction model in general, it is being modeled on a known data set and it is expected to perform the same on the unknown data samples. How can one guarantee this? This is achieved to a great extent using the method of cross validation.

In the earlier section “*Train and Test Split*”, the given data set is split into train and test data set accordingly. The training data set is used for training the model and the test data set is used for validation. Is this enough for a model to be generic to perform for any random data or new samples? The cross validation proves this wrong by allowing multiple training data sets and test data sets. There are some main categories of cross validation and they are given as follows:

*   **Exhaustive cross validation**
    
    In this method, the original data set is divided into train and test data set in different possible ways and the testing for all the possible ways of split. In this method, there are two types:
    
    *   Leave-p-out cross validation
    *   Leave-one-out cross validation
*   **Non-exhaustive cross validation**
    
    In this method, the original data set is divided into training data set and test data set in a set of possible ways only and does not include all the possible ways of split. So, these methods will be the approximations of the leave-p-out method for the different values of p. There are various types of this method which are given as follows:
    
    *   K-fold cross validation
    *   Stratified K-fold cross validation
    *   Holdout method
    *   Monte Carlo cross validation
*   **Rolling Cross Validation**
    
    This method of cross validation is used for time series data.
    

Each of the preceding methods is given here with brief descriptions and their purpose.

*   **Leave-p-out Cross Validation**
    
    In this method, a random set ‘p’ is selected as the test set among the set of observations. The remaining will be treated as a training set. All such possible combinations of train and test split are used and verified. It is an exhaustive method as it takes enough computational time.
    
*   **Leave-one-out Cross Validation**
    
    This method is similar to the leave-p-out cross validation except that the ‘p’ is set to 1. The number of combinations is less in this method and hence, it is less computationally intensive compared to the leave-p-out cross validation method.
    
*   **K-fold Cross Validation**
    
    In this method, the input data set is divided into ‘k’ equal-sized subsets. Take one subset and set it aside as the test data set and remaining as the training data set and perform the training. Repeat this step, picking different subset from ‘k’ subsets as test data set and remaining as training data set. The average of ‘k’ results will be the final performance of the model. The advantage of this method is that each subset is used for validation and in a way each sample from the input data set is used both for testing and training. What is the value of ‘k’ to be used for optimal performance? There is no standard value that works for all models, generally, the values 5 or 10 are used but it is not mandatory.
    
*   **Stratified Cross Validation**
    
    Sometimes the number of positive samples and negative samples in the input data set may not be equal. Or in regression problems, a few samples might have some values distinct from others which is a representative of the whole data set being used. For example, in predicting the house price regression problem, there will be a few sets of samples in which the housing price will be high compared to other samples. In these cases, it is required that the train and test set split need to be proportionately divided in such a way that it is similar to the input data set. This is a modified version of the K-fold cross validation method. When the input data set is divided into ‘k’ subsets, it is seen that the mean response value is approximately equal in all the ‘k’ folds or the same percentage of samples of the target class exists in each of the ‘k’ subsets.
    
*   **Holdout Cross Validation**
    
    In this method, the input data set is split into two data sets, training data and test data set in the ratio of 70:30, 60:30 or 50:50. The data is first shuffled before splitting each time. The training and validation are carried out on each of the split and final estimation based on the average outcomes of all the splits. This method does the split without checking if the split is a representative of the whole data set or not. If the input data set is huge, it may be possible that test data set or training data set may contain some important information that is not there in the other set. Hence, this method is generally used when performance is not important but time is critical. If you have less time and want to check the working of the model for a large data set, the method can be used effectively.
    
*   **Monte-Carlo Cross Validation**
    
    In this method, the input data set is split into training and test data set in the ratio of 70:30, 60:30, or 50:50. Each sample in the training set and test set are randomly selected. This process is repeated multiple times and the estimation is averaged over all the outcomes. Since the data samples are randomly selected, it is possible that a sample can appear multiple times in the test data set or training data set and some samples may not be selected at all.
    
*   **Rolling Cross Validation**
    
    This method applies to specific types of data sets like time series data. Firstly, for this type of data set, the previous cross validation methods cannot be used because the splitting of data set into training data set and test data set will not consider the time events and hence, the split will not be valid in a time interval and the order of events which is the representative of the original data set will be lost.
    
    Secondly, it may happen that the training data set has the present data samples and future data samples and the past samples are not there and a similar test data set may have only the future data samples. This will again give wrong results and is not the right split for the time series problem. In such cases, rolling cross validation is used. In this method, split should be carried out in a forward-chaining pattern. This means when the samples are selected for training or test data set, the training data set should have events of the past and test data set should have events in the future and these events need to be dependent on the events in the training set only. For example, if there is weather forecasting for ‘n’ weeks of the year. Then the data is split into the training and test data set in such a way that if the training data set contains the data of the first, second and third weeks, then the test data should have data of the fourth week. If the training data set consists of second, third, fourth, fifth and sixth weeks, then the test data should have data of the seventh week only.
    

# [7.8 Feature Reduction Techniques](#toc.xhtml#s184a)

These techniques are used to extract the reduced features from the original set of features based on the mathematical properties of data points. The extracted features represent most of the information of the original data set and hence, they can be used for model training without the loss of information. There are many techniques of feature extraction which are discussed in detail in *[Chapter 3, System Analysis with Machine Learning / Un-Supervised Learning](#c03.xhtml)* of this book.

# [7.9 Use Cases and Examples](#toc.xhtml#s185a)

Now, the steps are given for data processing that needs to be followed while handling the data set for building the machine learning or deep learning models. The pseudo-code is given for illustration purposes:

*   **Re-scaling Data**
    
    If for a given data set the attribute values are on a varying scale, then they need to be re-scaled to bring them on the same scale. The function `MinMax Scaler` of scikit-learn can be used for this purpose. The pseudo-code for using MinMaxScaler for any data set in general is given as follows:
    
    `from sklearn.preprocessing import MinMaxScaler`
    
    `# Read the data set using pandas and store in df`
    
    `df=pandas.read_csv(‘data set file name', sep=',')`
    
    `array=df.values`
    
    `# Read the input features from array into x`
    
    `# Read the output features from the array into y`
    
    `scaler=MinMaxScaler(feature_range=(0,1))`
    
    `rescaledX=scaler.fit_transform(x)`
    
    `rescaledX contains the input features with attribute values which are rescaled in the range of 0 and 1.`
    
*   **Normalizing data**
    
    The attribute values can be normalized or re-scaled to different norms like L1 norm and L2 norm. The function Normalizer of scikit-learn can be used for this purpose and the pseudo-code of using this function is given here.
    
    The following lines of code are used to normalize the input array ‘x’ into L1 norm or unit norm:
    
    `from sklearn.preprocessing import Normalizer`
    
    `normscaler=Normalizer().fit(x)`
    
    `normX=normscaler.transform(x)`
    
*   **Standardizing data**
    
    If the data set values need to be transformed into Gaussian distribution with a mean of 0 and standard deviation of 1, then the function StandardScaler of scikit-learn can be used. This standardization transformation technique is used when the given data set has Gaussian distribution and with different means and standard deviations. The following lines of code do the transformation using `StandardScaler` for input array ‘x’:
    
    `from sklearn.preprocessing import StandardScaler`
    
    `standardScaler=StandardScaler().fit(x)`
    
    `rescaledX=standardScaler.transform(x)`
    
*   **Binarizing data**
    
    This transformation technique is used while standardizing the attribute values 0 and 1 based on the threshold. All the values above the threshold will be marked 1 and those below will be marked 0. The function Binarizer of scikit-learn is used for this purpose and below lines of code transforms the input array ‘x’ using Binarizer. The values of input array ‘x’ which are above 0.2 are marked 1 and those below are marked 0 in the following code snippet. Generally, this transformation can be used to transform the probability values into specific values:
    
    `from sklearn.preprocessing import Binarizer`
    
    `binarizerScalar=Binarizer(threshold=0.2).fit(x)`
    
    `binaryX=binarizerScalar.transform(x)`
    
*   **Label encoding**
    
    This transformation is used to attribute values with words into numbers so that it will become easier to handle during processing. The function `LabelEncoder` of scikit-learn can be used for this purpose and the following code snippet shows its usage:
    
    `from sklearn.preprocessing import LabelEncoder`
    
    `labelencoderInstance =LabelEncoder()`
    
    `classesNames=['Havells','Philips','Syska','Eveready','Lloyd']`
    
    `labelencoderInstance.fit(classesNames)`
    
*   **One-hot encoding**
    
    For attribute values that are scattered and fewer samples exist then it is better to transform it into one-hot encoding. It transforms the m-distinct values in the feature into an m-dimensional array with a value of 1 for one element and 0 for the remaining. The function `OneHotEncoder` of scikit-learn can be used for this and the following code snippet shows its usage:
    
    `from sklearn.preprocessing import OneHotEncoder`
    
    `encoderInstance=OneHotEncoder()`
    
    `encoderInstance.fit([[1,1,2,2],`
    
    `[1,6,3,8],`
    
    `[1,4,9,7],`
    
    `[4,0,4,5]`
    
    `])`
    
*   **Handling missing data**
    
    One of the options to handle the missing data is to remove the row of attributes if more than 50% of the values are missing in the columns. For data values that are numeric in nature, the other approach to handle the missing values is to replace them with either mean, median, or mode of the feature. Another approach, when the data values are linear, is to replace them with deviation from the neighboring values. The following code snippet replaces the missing values (‘NaN’) with the mean of its feature. The function Imputer of scikit-learn is used for this purpose:
    
    `from sklearn.preprocessing import Imputer`
    
    `imputerInstance = Imputer(missing_values = 'NaN',strategy = 'mean', axis = 0)`
    
    `imputer = imputerInstance.fit(X)`
    
    `X = imputer.transform(X)`
    

# [Conclusion](#toc.xhtml#s186a)

The knowledge of the data formats and properties of the data set will enable one to prepare a generic data set for the model. The normalization techniques will help in standardizing the data set so the model gives importance to all the features in the data set. The methods of train and test split, its purpose, and information on how each method can be used will help in building a high performing model. The feature selection techniques, feature extraction techniques, regularization, and cross validation will help one to avoid the overfitting and underfitting of models and build a generic and high performing model which can make predictions on the unseen and random data samples.

In the next chapter, “*Ensemble Methods*”, the technique of combining multiple models, training them parallelly and how they can be used to learn the unique and distinct features will be discussed.

# [Points to remember](#toc.xhtml#s187a)

*   Data formatting is an important processing step in the building of models.
*   If normalization is not done for attributes that are different ranges and intervals, the model tends to ignore values in the lower range or intervals.
*   The splitting of the data set into a training set and test set is required as a developed model for a given problem and the data set is expected to make predictions correctly on the unseen or new examples.
*   Bias and variance need to be reduced to have a good performing model which is neither overfitting nor underfitting. So, the optimal trade-off between bias and variance needs to be worked out.
*   Underfitting occurs when the learning algorithm does not generalize or fit the function for the data points during training.
*   Overfitting occurs when the learning algorithm generalizes or fits the function by learning the relationship among data to the fullest including noise and random fluctuations in data if any.
*   In the K-fold cross validation method, the input data set is divided into ‘k’ equal-sized subsets. Take one subset and set it aside as test data set and remaining as the training data set and perform the training.

# [Questions](#toc.xhtml#s188a)

*   What are the different data formats of the data available in data sets used in machine learning and deep learning models?
*   What are the differences between qualitative and quantitative data?
*   Name any four methods of normalization techniques used to normalize the attributes of the data set. Briefly describe any one of the methods.
*   What is the need of splitting the data set into training data set and test set? What is the optimal data split that is applicable for building good performing models?
*   Bias and variance are important for model overfitting and underfitting. Discuss.
*   Draw the graph of model complexity versus error and explain the various terms used in the graph.
*   List the steps that need to be taken to avoid underfitting.
*   What is overfitting and underfitting of models?
*   Name the different types of feature selection techniques that can avoid the overfitting of models.
*   List any five methods to avoid model overfitting.
*   Discuss the early stopping and dropout methods to prevent model overfitting.
*   List any three methods of cross validation and explain the stratified k-fold cross validation.
*   What is rolling cross validation and how is it different from the other methods of cross validation?

# [Multiple Choice Questions](#toc.xhtml#s189a)

1.  **Choose the correct answer** 
    1.  Nominal data and ordinal data are two forms of unstructured data.
    2.  Continuous data and discrete data are two forms of quantitative data.
    3.  Integers and floating-point numbers are two forms of unstructured data.
    4.  Text is the form of structured data.
2.  **Choose the correct answer** 
    1.  Interval data and ratio data are forms of qualitative data.
    2.  Integers and floating-point numbers are two forms of structured data.
    3.  Text and numbers are the only two forms of data formats available.
    4.  Structured data is suitable for building machine learning models only.
3.  **Choose the correct answer** 
    1.  Min-Max normalization is a technique to avoid model underfitting.
    2.  Decimal scaling is a technique to avoid model underfitting.
    3.  Zero-score normalization technique is used to avoid model overfitting.
    4.  Box-Cox transformation is a data normalization technique.
4.  **Choose the correct answer** 
    1.  80:20 is the optimal split for the test and training data set.
    2.  50:50 is the optimal split for the test and training data set.
    3.  80:20 is the optimal split for the training data set and test data set.
    4.  Optimal split for training and test split needs to be judged based on the problem and data set available.
5.  **Choose the correct answer** 
    1.  Bias is the summation of the ground truth value and the predicted value by the model.
    2.  Variance gives the spread of the data set or variability of the model prediction for the given data point.
    3.  A high bias model overfits data and makes simplistic assumptions on it.
    4.  A high variance model underfits the data and learns a lot from it.
6.  **Choose the correct answer** 
    1.  Add more parameters to the model to avoid model overfitting.
    2.  Add more data to the data set for normalization of data.
    3.  Increase the complexity of the model by adding different layers to avoid model overfitting.
    4.  Increase the training time till the cost function is minimized to avoid model underfitting.
7.  **Choose the correct answer** 
    1.  Model underfitting happens when data has many features but fewer examples and the model trained is too complex for the data used for training.
    2.  Models tend to underfit when there is low bias and high variance in the data points.
    3.  The models may tend to overfit even when the model is trained for a long time to achieve high accuracy.
    4.  Feature extraction is a technique to avoid model underfitting.
8.  **Choose the correct answer** 
    1.  Variance Thresholds technique is used to avoid model underfitting.
    2.  Genetic Algorithms are used for data normalization.
    3.  Correlation techniques are used for the splitting of training and test data set.
    4.  Stepwise search-based selection technique avoids model overfitting.
9.  **Choose the correct answer** 
    1.  Leave-p-out and leave-one-out are exhaustive cross validation techniques.
    2.  K-fold cross validation and Monte-Carlo cross validation are exhaustive cross validation methods.
    3.  Stratified k-fold cross validation and holdout cross validation are exhaustive cross validation methods.
    4.  Rolling out cross validation is an exhaustive cross validation method.

# [Answers](#toc.xhtml#s190a)

1.  **a**
2.  **a**
3.  **d**
4.  **d**
5.  **b**
6.  **d**
7.  **c**
8.  **d**
9.  **a**

# [CHAPTER 8](#toc.xhtml#c08)

# [Ensemble Model Development](#toc.xhtml#c08)

AI-based inferring models are extremely useful when the relation combining the output with the input variables is not available. Towards this, several algorithms have been developed. However, the accuracy and stability of these algorithms or models is still an issue. This is because each model learns a specific set of features. Since a single model may not be in a position to provide an accurate outcome, it is sometimes required to combine multiple models that learn unique and distinct features, which provides better accuracy. Many times, instead of using a single algorithm, it is beneficial to combine more than one algorithm, which yields better results. In competitions like Kaggle, it is a known fact that combining algorithms yield better accuracies and results. Also, combining the algorithms lead to powerful models.

In addition, the models are trained with a large set of configurable parameters. The performance of the model is the best for a specific combination of parameters. When the space spanned by these hyperparameters is large, it is difficult to try out all the parameters manually. A systematic approach is required to arrive at an optimal parameter set. This chapter explains hyperparameter tuning for better performance.

# [Structure](#toc.xhtml#s191a)

In this chapter, we will discuss the following topics:

*   Ensemble methods 
    *   Sequential ensemble methods
    *   Parallel ensemble methods
    *   Averaging ensemble methods
    *   Boosting ensemble methods
    *   Extreme gradient boosting (XG boost)
*   Combining weak learners
*   Advanced ensemble model building
*   Hyperparameter tuning 
    *   Factors influencing tuning
    *   Genetic algorithm-based tuning
*   Examples & samples

# [Objectives](#toc.xhtml#s192a)

After studying this chapter, you should be able to:

*   Design and implementation of multiple AI algorithms
*   Design and implement boosting and extreme boosting techniques.
*   Develop a mechanism to combine several models for better performance.
*   Fine-tune the model parameters for optimal performance.
*   Make use of the genetic algorithms for hyperparameter tuning.

# [8.1 Introduction](#toc.xhtml#s193a)

Artificial intelligence systems have evolved over a period of time. The models provide different degrees of accuracies based on the algorithms used. The boosting method provides combining of these models to enhance the performance. The model’s hyperparameters are systematically selected using the genetic algorithm

# [8.2 Ensemble methods](#toc.xhtml#s194a)

Various ensemble methods have sprung up nowadays. By combining the predictions of many estimators, robustness has improved over a single estimator. It is a known fact as explained earlier, that combining more than one learning algorithm yields better accuracies and powerful models as outcomes. *[Figure 8.1](#c08.xhtml#fig8_1)* shows the various ensemble methods:

![](images/Figure-8.1.jpg)

**Figure 8.1:** Ensemble Methods

# [8.2.1 Popular ensemble methods](#toc.xhtml#s195a)

As explained in the introduction and the previous sections, the main aim of the ensemble method is to combine the prediction/outcome of the various methods. Each of these methods has their advantages and have been discussed briefly as follows:

# [8.2.1.1 Sequential ensemble methods](#toc.xhtml#s196a)

Different type of learners learns sequentially. In some cases, the early learners will fit the simple models to the data. The performance will be continuously enhanced by analyzing the data for errors. The overall boost in the performance is possible with the correct classification of the mislabeled examples from higher weight correction. *[Figure 8.2](#c08.xhtml#fig8_2)* shows the pictorial representation of the sequential ensemble method. Examples of this method include *Adaboost* and *Stochastic Gradient Boosting*:

![](images/Figure-8.2.jpg)

**Figure 8.2:** Sequential Ensemble Method

# [8.2.1.2 Parallel ensemble methods](#toc.xhtml#s197a)

In these methods, base learners are generated simultaneously. For example, if you want to select an exotic holiday destination, you may ask your friends for suggestions and browse on the internet for good options or check some magazines for the same. A few examples of parallel ensemble methods are stacking, random forest, and bagging.

*   **Homogeneous parallel ensemble methods:**
    
    In this method for the base learner, a single machine learning algorithm is used. Bagging and boosting belong to this category.
    
*   **Heterogeneous parallel ensemble methods:**
    
    In this method for the base learner, multiple machine learning algorithms are used. Stacking belongs to this category.
    

*[Figure 8.3](#c08.xhtml#fig8_3)* shows the pictorial representation of the parallel ensemble method:

![](images/Figure-8.3.jpg)

**Figure 8.3:** Parallel Ensemble Method

# [8.2.1.3 Averaging ensemble methods](#toc.xhtml#s198a)

First, build several estimators independently and then average their predictions by combining them. In many cases, these estimators are better than that of a single base estimator. As variance gets reduced by combining the models, it is a better practice to have these kinds of ensemble models.

# [8.2.1.4 Boosting ensemble methods](#toc.xhtml#s199a)

In boosting methods, several estimators are combined like in the sequential methods but with the motivation of bias value getting reduced. Also, several weak models are combined to produce powerful ensemble models in the boosting technique.

# [8.3 Combining weak learners](#toc.xhtml#s200a)

It is also observed that “*weak learners*” generally provide weak results when played solo. However, when these weak learners are combined correctly and effectively, with the hypothesis in mind, they often lead to more robust and accurate results.

Be it a classification or regression type of a problem, combining proper algorithms or what is known as the ensemble of algorithmic models lead to good results and outcomes. How we chose these algorithms depends on various parameters like, hyperparameters we chose, the dimensionality of space, the quantity of data we have in hand, what hypothesis we select, and so on.

Sometimes, a bias-variance trade-off is used to determine what to choose and what not to choose. With the optimal balancing of model complexity values, one can avoid the overfitting and underfitting scenarios.

# [How to combine weak learners?](#toc.xhtml#s201a)

It is always a best practice to select a base model. With this base model in hand, we can have building blocks to construct or design the ensemble models. The models, which help in reducing bias-variance trade-off, and the models, which help in building robust, structure (high degrees of freedom kind of models) and with the combination of weak learners, these ensemble models can be built. The weak learner that was mentioned is not a random choice but it should be coherent and related to the aggregate of all the models that we explored. The following methods are some of the meta algorithms that one can explore before making any conclusions:

*   **Boosting or boosting methods:** The idea is to combine several weak learner models (same type or homogeneous models) to produce a powerful ensemble model. In this method, the base estimators are built in sequential order (the selected base model depends on the previous model) and the bias value of the combined estimator will be reduced if possible. Sequential learning happens in an adaptive way.
*   **Bagging:** Bagging methods are predominantly used by introducing randomization in the variance of the base estimators. Generally, the bagging methods are built using a class of algorithms, which have several instances of black-box estimators along with a random subset of the training sets. By having aggregation of the individual predictions, the final prediction is formed. Bagging methods are used to reduce overfitting; thus it also works best for complex models like fully random and decision trees.
    
    In some cases, bagging methods consider the same type of weak learners, which learns independently from each other, parallelly. Finally, it combines them with the deterministic averaging process.
    
*   **Stacking:** This method considers heterogeneous weak learners, which learns them parallelly and finally combines them by training using a meta-model. Then based on the predictions of different weak models, the final prediction is made. Let us assume that we want to fit a stacking ensemble composed of the K-weak learners. The following steps can be followed: 
    1.  Firstly, split the training data into two parts.
    2.  Then choose the K-weak learners and train them with data of the first part.
    3.  Now, for each of the K-weak learners, for observations in the second part make the predictions accordingly.
    4.  Finally, using the weak learners’ predictions as input and fit the meta-model on the second part.
*   **Bagging Vs Boosting:** There is no clear winner out of these two methods. It entirely depends on the data, the simulation methods used, and the surrounding environment. These two methods help in decreasing the variance of a single estimate as they combine many estimates from different models.
    
    To measure any model’s accuracy, its training accuracy is compared with its validation accuracy. If any individual or single model gets lower performance then bagging will not get a better bias value, but boosting can combine models with lower errors and optimizes. Bagging helps in the generalization ability of the model for better prediction on the new samples:
    

 
| **Index** || **Ensemble Method** || **SciKit Learn Library** |
| --- | --- | --- |
| **1** || **Bagging meta estimator** || `from sklearn.ensemble import BaggingClassifier``from sklearn.neighbors import KNeighborsClassifier``bagging = BaggingClassifier(KNeighborsClassifier(),max_samples=0.5, max_features=0.5)` |
| **2** || **Forests of randomized trees** || `from sklearn.ensemble import RandomForestClassifier` |
| **3** || **AdaBoost** || `from sklearn.model_selection import cross_val_score``from sklearn.datasets import load_iris``from sklearn.ensemble import AdaBoostClassifier` |
| **4** || **Gradient Tree Boosting** || `from sklearn.datasets import make_hastie_10_2``from sklearn.ensemble import GradientBoostingClassifier` |
| **5** || **Histogram-Based Gradient Boosting** || `from sklearn.experimental import enable_hist_gradient_boosting``from sklearn.ensemble import HistGradientBoostingClassifier` |
| **6** || **Boosting (Voting Classifier, Regressor and Stacked Generalization)** || `from sklearn.ensemble import VotingClassifier``from sklearn.ensemble import VotingRegressor`` from sklearn.ensemble import GradientBoostingRegressor``from sklearn.ensemble import StackingRegressor` |

**Table 8.1:** Scikit–learn library for various ensemble methods

# [8.4 Advanced ensemble model building tips](#toc.xhtml#s202a)

When the AI model is noisy, combining the models reduce the noise significantly. The combination of models reduces the variance in the inference significantly.

The number of models or estimators need to be carefully chosen. While a large number of models reduce the variance, it may also lead to overfitting and increased computation time. The genetic algorithm has been detailed in the next section and can be used for the selection of the optimal number of models. Typically, the design starts with 10 estimators.

# [8.5 Hyperparameter tuning](#toc.xhtml#s203a)

The accuracy of a machine learning model depends on various parameters. These design parameters are configurable and are called **hyperparameters**. A small variation in the choice of these parameters significantly affects the performance and stability of the model.

The parameters come in multiple combinations and thereby poses the problem of optimal selection for the fine-tuning of the model. Some of these parameters are extremely critical. For example, it can be the maximum depth in the decision tree, number of trees in a random forest or number of layers, filters, pooling method, or stride length in a convolutional neural network. These parameters are configurable to enable fine-tuning.

The hyperparameters are different from the model parameters, weights of the network, or the system. They are not obtained as a part of the training but by minimizing the loss function. The selection of hyperparameters starts by defining a range for the same. Within this range, the values are sampled in different combinations to optimize the performance.

# [8.6 Genetic algorithm-based tuning](#toc.xhtml#s204a)

The number of hyperparameters, as well as the values they can take, is prohibitively large. It is not practical to try out all the combinations of the values to get the optimal performance. The values are sampled to reduce the domain of the input.

One of the techniques for sampling the values in the space spanned by the parameters is the genetic algorithm. It is an optimization algorithm for sampling the data for minimization. It is inspired by the theory of natural selection from *Charles Darwin*. Accordingly, it has 3 components:

*   **Variation**: More variants of an entity or organism are generated through mutation.
*   **Inheritance**: The variety of features generated as a part of variation gets passed on to the next generation organisms or entities.
*   **Survival of the fittest**: The varieties of entities or organisms created for the next generation compete among themselves for various elements (based on the criteria such as survival with minimal resources). One of them, the best one, survives and the process continues.

These principles are applied to the model. For a given inferencing problem, the model is developed with hyperparameters giving reasonably good results based on the design constraints. A good model could be selected based on its performance such as low log loss error. Next, hyperparameters are changed slightly to create a set of models. The best of these models is selected again based on the same criteria. The process repeats and spans over the entire hyperparameter space.

# [8.7 Use cases or examples](#toc.xhtml#s205a)

In this section, an example code is given to illustrate the application of the genetic algorithm for feature selection. Firstly, the logistic regression is applied for breast cancer data and the performance is noted. Secondly, the genetic algorithm is applied for selecting features of the breast cancer data which results in the increase of performance.

Firstly, the required libraries are imported as given here:

`import numpy as np`

`import pandas as pd`

`import random`

`import matplotlib.pyplot`

`%matplotlib inline`

Now, the data set and model-related packages are imported. The breast cancer data set is used in this example:

`from sklearn.datasets import load_breast_cancer`

`from sklearn.metrics import accuracy_score`

`from sklearn.model_selection import train_test_split`

`from sklearn.linear_model import LogisticRegression`

Load the data set using the method from the imported library and stored it in the data frame for further usage:

`cancer=load_breast_cancer()`

`datafr = pd.DataFrame(cancer['data'],columns=cancer['feature_names'])`

`label=cancer["target"]`

Split the loaded data set into training and testing set in the ratio of 70:30:

`Xtrain, Xtest, ytrain, ytest = train_test_split(df, label, test_size=0.30, random_state=101)`

Train the logistics regression model for the breast cancer data set for the training data set. And then perform prediction on the test data set and measure the performance:

`#training a logistics regression model`

`logmodel = LogisticRegression()`

`logmodel.fit(X_train,y_train)`

`predictions = logmodel.predict(X_test)`

`print("The accuracy of the model is "+ 100*str(accuracy_score(y_test,predictions)))`

`The accuracy of the model is 93.56%`

Next, the genetic algorithm is used for better feature selection to achieve higher performance as compared to earlier. The following are some methods that are required for aiming the feature selection using the genetic algorithm:

`#defining various steps required for the genetic algorithm`

`def init_of_pop(size, numFeat):`

`pop = []`

`for i in range(size):`

`chromosome = np.ones(numFeat, dtype = np.bool)`

`chromosome[:int(0.3*numFeat)] = False`

`np.random.shuffle(chromosome)`

`pop.append(chromosome)`

`return pop`

`def fit_score(pop):`

`scores = []`

`for chromosome in pop:`

`logmodel.fit(Xtrain.iloc[:,chromosome], ytrain)`

`preds = logmodel.predict(Xtest.iloc[:,chromosome])`

`scores.append(accuracy_score(ytest, preds))`

`scores, pop = np.array(scores), np.array(pop)`

`inds = np.argsort(scores)`

`return list(scores[inds][::-1]), list(pop[inds,:][::-1])`

`def selection(popAfterFit, numParents):`

`popNextgen = []`

`for i in range(numParents):`

`popNextgen.append(popAfterFit[i])`

`return popNextgen`

`def crossover(popAfterSel):`

`popNextgen=popAfterSel`

`for i in range(len(popAfterSel)):`

`child=popAfterSel[i]`

`child[3:7]=popAfterSel[(i+1)%len(popAfterSel)][3:7]`

`popNextgen.append(child)`

`return popNextgen`

`def mutation(popAfterCross, mutationRate):`

`popNextgen = []`

`for i in range(0, len(popAfterCross)):`

`chromosome = popAfterCross[i]`

`for j in range(len(chromosome)):`

`if random.random() < mutationRate:`

` chromosome[j]= not chromosome[j]`

`popNextgen.append(chromosome)`

`#print(popNextgen)`

`return popNextgen`

`def generations(size, numFeat, numParents, mutationRate, nGen, Xtrain, Xtest, ytrain, ytest):`

`bestChromo= []`

`bestScore= []`

`popNextgen=init_of_pop(size, numFeat)`

`for i in range(nGen):`

`scores, pop_after_fit = fitness_score(population_nextgen)`

`print(scores[:2])`

`popAfterSel = selection(popAfterFit, numParents)`

`popAfterCross = crossover(popAfterSel)`

`popNextgen = mutation(pop_after_cross,mutation_rate)`

`bestChromo.append(popAfterFit[0])`

`bestScore.append(scores[0])`

` return bestChromo, bestScore`

The best or optimal set of features is selected by calling the genetic algorithm using the following method. It takes the number of chromosomes, number of genes for each entity in the population, number of parents, mutation rate, and number of generations as input parameters to find the optimal children:

`chromo,score=generations(size=200, numFeat=30, numParents=100, mutationRate=0.10, nGen=38, Xtrain=Xtrain, Xtest=Xtest, ytrain=ytrain, ytest=ytest)`

Firstly, the initial population is built using the number of chromosomes and the number of genes using the following method:

`popNextgen=init_of_pop(size, numFeat)`

Secondly, the best individuals of the current population are built using a fitness function given here:

`def generations(size, numFeat, numParents, mutationRate, nGen, Xtrain, Xtest, ytrain, ytest):`

`bestChromo= []`

`bestScore= []`

`popNextgen=init_of_pop(size, numFeat)`

`for i in range(nGen):`

`scores, pop_after_fit = fitness_score(population_nextgen)`

`print(scores[:2])`

`popAfterSel = selection(popAfterFit, numParents)`

`popAfterCross = crossover(popAfterSel)`

`popNextgen = mutation(popAfterCross, mutationRate)`

`bestChromo.append(popAfterFit[0])`

`bestScore.append(scores[0])`

`return bestChromo, bestScore`

After this, the children of the next generation are produced using the crossover and mutation methods of the genetic algorithm as defined earlier:

`popAfterCross = crossover(popAfterSel)`

`popNextgen = mutation(popAfterCross, mutationRate)`

This is repeated for all the generations and the best chromosomes are generated across all the generations. The lists bestChromo and bestScore will have the best chromosomes and their corresponding fitness scores:

`for i in range(nGen):`

`scores, pop_after_fit = fitness_score(population_nextgen)`

`print(scores[:2])`

`popAfterSel = selection(popAfterFit, numParents)`

`popAfterCross = crossover(popAfterSel)`

`popNextgen = mutation(popAfterCross, mutationRate)`

`bestChromo.append(popAfterFit[0])`

`bestScore.append(scores[0])`

Using the best chromosomes or features generated using the genetic algorithm as described earlier, the logistic regression model is again trained with this new set of features given as follows:

`chromo,score=generations(size=200, numFeat=30, numParents=100, mutationRate=0.10,nGen=38, Xtrain=Xtrain, Xtest=Xtest, ytrain=ytrain, ytest=ytest)`

`logmodel.fit(Xtrain.iloc[:,chromo[-1]], ytrain)`

As mentioned earlier, the trained model is evaluated for the test data set and accuracy is determined:

`predictions = logmodel.predict(Xtest.iloc[:,chromo[-1]])`

`print("Accuracy score after genetic algorithm is= "+100 * str(accuracy_score(y_test, predictions)))`

`Accuracy score after genetic algorithm is= 95.32`

As mentioned earlier, the trained model is evaluated for the test data set and accuracy is determined. It is evident from the accuracy score that the genetic algorithm has found the optimal features which have improved the performance.

# [Conclusion](#toc.xhtml#s206a)

In the previous chapter, different algorithms have been illustrated to develop the models. The models, however, have inherent limitations in learning the patterns and results in reduced accuracies. The accuracy and stability of these models can be enhanced when more than one model is applied over the same data set. The learnings of the models complement each other so that the resulting ensemble can have higher accuracy and provide stable results. It also calls for fine-tuning of the hyperparameters of individual models such as the stride length, dropout neurons, etc. in a deep learning model. The genetic algorithm provides a systematic method for selecting the optimal choice of the parameters. The design methodology with the right choice of parameters in a deep learning network will be the topic of discussion in the next chapter.

# [Points to remember](#toc.xhtml#s207a)

*   The adaboost algorithm helps to combine the model for better performance.
*   The genetic algorithm helps to fine-tune the model parameters.
*   The sequential and parallel ensemble methods are popular.
*   Combining estimators will provide better results in many cases.
*   Boosting and bagging are some of the popular ensemble techniques.

# [Questions](#toc.xhtml#s208a)

1.  What are the advantages of combining models?
2.  What are the various ensemble methods? List them.
3.  What are parallel and sequential ensemble methods?
4.  What is a weak learner?
5.  What is boosting?
6.  What is bagging?
7.  What happens to the accuracy when models are combined?
8.  How does the genetic algorithm help in fine-tuning the hyperparameters?
9.  What are the constraints on the model parameter tuning?

# [Multiple choice questions](#toc.xhtml#s209a)

1.  **Choose the correct answer** 
    1.  Same training set is used for all the models in boosting.
    2.  Boosting combines traditional machine learning models and deep learning models.
    3.  For combining models, more data is required.
    4.  Hyperparameters are always fixed.
2.  **Choose the correct answer** 
    1.  In boosting, overfitting is achieved.
    2.  In boosting, several estimators are combined with reduced bias values.
    3.  In boosting, many parallel estimators are estimated.
    4.  None of the above
3.  **Choose the correct answer** 
    1.  Adaboosting is the scikit learn library used for Adaboost.
    2.  No such library is available.
    3.  AdaBoostClassifier is the scikit learn library used for Adaboost.
    4.  None of the above

# [Answers](#toc.xhtml#s210a)

1.  **a**
2.  **b**
3.  **c**

# [CHAPTER 9](#toc.xhtml#c09)

# [Design with Deep Learning](#toc.xhtml#c09)

AI-based models provide interpretation of the data based on the patterns especially when the data is complex and difficult for human experts to comprehend. For example, the sensor data, speech signal, and so on., hold a lot of patterns that are difficult to understand. In addition, the speed, accuracy, and unbiased inferencing make an AI model outperform a human expert and makes it a suitable candidate for automation. While the traditional machine models still require features to be identified by a human expert and applied as the input, the deep learning models perform this task themselves. They learn the required patterns buried in the input data by passing through a deep chain of filters.

# [Structure](#toc.xhtml#s211a)

In this chapter, we will discuss the following topics:

*   Introduction
*   Architecture of CNN 
    *   AlexNet
*   Training a CNN network
*   Latest trends and algorithms in CNN
*   Use cases or examples

# [Objectives](#toc.xhtml#s212a)

After studying this chapter, you should be able to:

*   Design and implement the CNN classifiers
*   Appreciate the factors or patterns influencing decision making
*   Understand the scope of AI in automation
*   Make use of optimization algorithms
*   Various filtering techniques used in CNN

# [9.1 Introduction](#toc.xhtml#s213a)

*David H. Hubel* and *Torsten Wiesel* after their studies and experiments on the human visual cortex laid the foundations for building the **convolutional neural network** (**CNN**) model.

“*More than 50 per cent of the cortex, the surface of the brain is devoted to processing visual information*,” said *William G. Allyn*, a professor of medical optics.

The human visual cortex is approximately made up of around 140 million neurons:

![](images/Figure-9.1.jpg)

**Figure 9.1:** Receptive fields of human visual cortex

*Hubel* and *Wiesel* discovered that there are three types of cells in the visual cortex and each of them has distinct characteristics, based on the features they learn or react to. These are simple, complex, and hyper-complex. Simple cells are responsible for learning basic features like lines and colors; complex cells are responsible for learning features like edges, corners, and contours, while hyper-complex cells are responsible for learning combinations of features learnt by simple and complex cells. This powerful insight paved the way to understand how perception is built – the receptive fields of multiple neurons may overlap and together they tile the whole field. These neurons work together, with a few neurons learning features on their own and others learning by combining the features learnt by other neurons, and finally integrating to detect all forms of complex features in any region of the visual field.

**For the video of the Hubel and Wiesel experiment, visit [https://www.youtube.com/watch?v=y\_l4kQ5wjiw](https://www.youtube.com/watch?v=y_l4kQ5wjiw).**

CNNs are the most preferred deep learning models for image classification or image-related problems. Later, the CNNs have also been used to handle problems in fields as diverse as natural language processing, voice recognition, action recognition, and document analysis. The most important characteristic of the CNNs is that they automatically learn the important features without any guided supervision. Given the images of two classes, for example, dogs and cats, a CNN will be able to learn the distinctive features of dogs and cats by itself.

Compared to other deep learning models for image-related problems, CNNs are computationally efficient, which makes them the most preferred option since they can be configured to run on many devices. Ever since the arrival of *AlexNet* in 2012, researchers have successfully built new CNN architectures that have good accuracy, with powerful and efficient models. The popular CNN model architectures include VGG-16, inception models, ResNet-50, Xception, and MobileNet.

# [9.2 Architecture of CNN](#toc.xhtml#s214a)

In general, all CNN models have architectures that are built using the following building blocks or components. *[Figure 9.2](#c09.xhtml#fig9_2)* depicts the basic architecture of a CNN model:

*   Input layer
*   Convolution layers
*   Activation functions
*   Pooling layers
*   Dropout layers
*   Fully connected layers
*   Softmax layer

In the CNN architecture, the building blocks involving the convolution layer, activation function, pooling layer, and dropout layer are repeated before ending with one or more fully connected layers and softmax layer.

The convolution layer is the most important building block of the CNN architecture. The neurons in the first convolution layer are not connected to all the pixels in the input image but are connected to pixels of their local receptive fields, as shown in *[figure 9.2](#c09.xhtml#fig9_2)*. Mathematically, the convolution layer merges two sets of information to produce a feature map. It applies the convolution filter or kernel to the input and produces the feature map:

![](images/Figure-9.2.jpg)

**Figure 9.2:** Architecture of CNN

Let us understand this better with an example. Suppose that the input image size is 6 x 6 and the kernel size is 3 x 3. To draw a parallel to the visual cortex, the visual field size is 6 x 6 and the local receptive field size is 3 x 3. To generate the feature map, the kernel is made to slide over each pixel location of the input image. Hence, a single value is generated for each convolution operation (the summation or multiplication of the pixel value with the corresponding kernel value in the same location). The area on the input image that is used during each convolution operation is the receptive field, the size of which is equivalent to the kernel size. Since the kernel is made to slide over the entire input image, an equal-sized feature map as the input image is produced after the convolution operation is applied to the entire image. The same procedure is followed for 3D images or multi-color channel input images. An independent feature map is also produced for each channel in that case. Since there is one feature map for each convolution operation using a kernel, for a normal 2D image in grey scale, the number of feature maps produced in each layer is equal to the number of kernels used in that layer. For 3D images, it is three times the number of kernels due to three color channels.

During a convolution operation, for each row x and column y in the feature map, the value at position (x, y) will be the total of the multiplication of values in rows x to x + kh – 1, and columns y to y + kw – 1, where kh and kw are the height and width of the receptive fields. Hence, to produce a feature map equal to the input image size, suitable padding has to be done around the input image. In general, zero padding is applied to the input image.

It is also possible to slide the kernel over the input image by spacing out the pixel location. That means, as described previously, the kernel is made to slide over each pixel location of the input image to generate the feature map. The distance between each successive receptive field is one (based on pixel locations). The spacing or distance between the two successive receptive fields is called **stride**. As the kernel is made to slide over rows and columns, the stride can be different for sliding across rows (vertical direction) and columns (horizontal direction). With the stride value of more than one, it is possible to produce a feature map that is smaller than the input size. With the stride, the neuron value in the feature map located at (x, y) is produced by rows *(x)* \* *sh + kh - 1*, and columns *(y) \* sw + kw – 1*, where sh and sw are horizontal and vertical strides. Each location (x, y) in the feature map will be a neuron generated using the specific kernel in that convolution layer. The neuron’s weight at a location (x, y) will hence be a value after the convolution operation is applied to rows x to *x + kh – 1*, columns y to *y + kw – 1*, where kh and kw are the height and width of the receptive field of the input. The CNN model is built to learn the equation *WX + b*, where W is the weight of the neurons, X is the activation values of neurons, and b is the bias term. All neurons in a feature map share the same weight (kernel) and bias term, but different activation values that correspond to the values of the receptive field corresponding to that neuron in the feature map. This is one of the reasons why computations are less in a CNN compared to a **deep neural network** (**DNN**). A feature learnt by a neuron at one particular location will allow it to detect the same feature anywhere else in the input, regardless of the location. This is another important feature of the CNN as compared to a DNN, which is not translationally invariant.

Next, consider the convolution layers after the first convolution layer. The neuron at location (x, y) in the feature map k in a convolutional layer ‘l’ gets its input from all the neurons in the previous layer l -1, which are located in rows *x \* sw* to *x \* sh + kw-1*, and columns *y \* sh* to *y \* sw + kh – 1* and for all feature maps in the layer l – 1. These are the same inputs to all neurons located in the same row x and column y, in all the feature maps. This explains how the features learnt in one layer get integrated to learn combined features or complex patterns in successive layers. This also explains how a CNN learns distinct features at the initial layers and convolutes to integrate basic features to learn complex distinct features or patterns in the intermediate convolution layers, before finally learning objects present in the input in the last convolution layers. As discussed earlier, any feature, pattern, or object learnt by the CNN at any layer will allow it to detect this anywhere else in the input, independent of the location. So, one needs to be extra careful when using a CNN to detect the combined objects that are similar in the input. For example, in the case of face detection, if one is interested in studying the features of the eye and eyebrows together as a combination, then the normal CNN would learn the features of the eyebrow and the eye as two different features and it may not help in learning the minor differences of the combination of features. In that case, the convolution layers have to be tweaked to learn those features appropriately.

# [9.3.1 AlexNet](#toc.xhtml#s215a)

AlexNet uses the ImageNet database for its training and inference. ImageNet is one of the most well-known databases containing images. This was formally started as a project aimed at manually labeling and categorizing the images in more than 20000+ separate object categories for computer vision-based research and study.

Following is the official website where all the image classifications and various publications can be found:

**[http://www.image-net.org/](http://www.image-net.org/)**

The following section of ImageNet is for exploring and learning more about the various features of the labeling that has been done:

**[http://image-net.org/explore](http://image-net.org/explore)**

**ImageNet** has hosted many challenges which are called “**ImageNet Large Scale Visual Recognition Challenge** (**ILSVRC**)”, starting from 2010 to 2017 and was used for evaluating algorithms for object detection and image classification at a large scale.

AlexNet was the top performer in ILSVRC 2012, which the achievement of reducing the top-5 error from 26% to 15.3%. The architecture is made up of five convolution layers, 3 max pooling layers and 3 fully connected layers. The convolution layers are used to generate the feature maps using different size filters and strides. The max pooling layers are used to down sample the height and width of the tensor while keeping the depth the same. AlexNet uses the ReLU as the non-linearity activation function and showed that it can be trained faster than other activation functions like tanh and sigmoid activation functions. AlexNet used the DropOut layer to avoid overfitting. In the dropout layer of AlexNet, a neuron is dropped from the network with a probability of 0.5. Since the neuron is dropped during training, it is not considered either in forward or backward propagation. Hence, every input goes through different network architecture. Hence, the learned weights are more powerful and do not allow the model to overfit easily. *[Figure 9.3](#c09.xhtml#fig9_3)* shows the architecture of AlexNet:

![](images/Figure-9.3.jpg)

**Figure 9.3:** AlexNet Architecture

The first convolution layer outputs, 224/4 × 224/4 x 96 = 55 × 55 × 96 (because of stride 4) feature maps. This layer is followed by the max pooling layer of size 3×3 and stride 2. The second convolution layer outputs, 27 × 27 × 256 feature maps and it is followed by the max pooling layer of size 3×3 and stride 2. Then it is followed by three convolution layers with 384 filters each of kernel size 3×3 and pad of 1. The output of the fifth convolution layer is 13 × 13 × 128 feature maps and is fed into the max pooling layer of size 3×3 and stride 2. The output of the max pooling layer is fed into the first fully connected layer and the output will be a vector of size 1×2048. The layer is followed by a similar fully connected layer with the same output which is then fed to the softmax classifier with 1000 class labels.

The following link provides a detailed overview of how AlexNet works:

**[https://neurohive.io/en/popular-networks/alexnet-imagenet-classification-with-deep-convolutional-neural-networks/](https://neurohive.io/en/popular-networks/alexnet-imagenet-classification-with-deep-convolutional-neural-networks/)**

# [9.4 Training a CNN network](#toc.xhtml#s216a)

The training involves passing this input image across various layers and with various techniques applied to extract only the relevant features or information. Using this relevant information, the output or category/label of the image is identified. The mechanism of training a CNN is similar to the regular supervised learning model which uses a backpropagation algorithm.

To start, the CNN is initialized with random values for all of its weights and biases. Since it is a supervised learning mechanism, the training data set or input consists of the input samples and their corresponding labels. Let us consider an image classification example, that is to classify the given image to cat or dog. The programming example for this classification is given in the next section, “*Use Cases or Examples*”. The binary cross-entropy function is used as the loss function. The objective of the learning mechanism is to minimize the value of the loss function. A detailed description of how the loss function is minimized and how the model is trained using backpropagation to achieve high accuracy for the model is explained in *[Chapter 2, Supervised Learning](#c02.xhtml)*.

As detailed in the previous sections, during the training the first layers of the CNN learns the basic features like vertical lines and horizontal lines, then successive layers learn the little complex features like contours, edges, colors, and basic shapes and the last few convolutional layers learn the complex objects like eyes, ears, tail, legs, faces, and so on. The fully connected layers help in combining all the features and the softmax layers help in identifying which of the features are dominating so that the input image can be classified accordingly.

# [9.5 Latest trends and algorithms in CNN](#toc.xhtml#s217a)

CNN has several variants in architecture such as ImageNet and AlexNet as detailed in the previous section. It also includes ResNet, VGGNet, LeNet, GoogleNet or Inception Net, and so on., each with distinct filter combinations, pooling, etc. Choice of the architecture depends upon the underlying applications, for example, LeNet works well for the MNIST data classification. It uses sigmoid or tanh non-linear function.

Networks such as AlexNet use dropout to prevent overfitting. It supports parallelism during training so that the parts of the network can be trained over GPUs in parallel. Although it is fast for a given accuracy, dropout significantly reduces the speed. It uses the ReLu as the non-linear activation function. GoogleNet or Inception Network is based on the idea of the inception module. Instead of implementing the convolution layers of the various hyperparameters in different layers, the filter operations of all the convolutions are output together as a result-containing matrices. This will reduce the number of weights and hence, decreases the total cost of computations. ResNet supports skip connections. The skip connections are also known as gated units. It uses the ReLu activation function. The number of weights in a VGGNet is large. It uses a large number of filters. However, its uniform architecture is an attractive feature. MobileNet and Squeeze Net, on the other hand, provide a compressed model at the cost of reduced accuracy. The optimization may be carried out for minimum square error, entropy, or a new cost function defined contextually based on the usage.

# [9.6 Use cases or examples](#toc.xhtml#s218a)

In this section, a programming example for building the simple convolutional neural network is given. The problem is to classify a given image into a dog or cat image. A simple convolutional neural network can be built with convolution layers, max pool layers, and dense layers using Theano, Tensorflow, and Keras frameworks. As of today, the architecture of the CNN models has evolved into complex networks with a lot of convolution layers, dense layers, pooling layers, and dropout layers combined to achieve high accuracy and solve complex image classification problems. As the purpose of this section is to understand the basic implementation of CNN, the following example is illustrated with a simple CNN model to classify the dogs and cats images:

The program assumes that the Theano, Tensorflow, and Keras frameworks have been installed.

Firstly, import the Keras libraries and packages required for building the CNN model.

`from keras.models import Sequential`

`from keras.layers import Conv2D`

`from keras.layers import Flatten`

`from keras.layers import Dense`

`from keras.layers import MaxPooling2D`

Initialise the CNN and start building the sequential model:

`imgclassifier = Sequential()`

Add the convolution layer by giving the number of filters, kernel size, input shape, and the activation function.

The following convolutional layer is added with 32 filters, kernel of size (3, 3), input size is (64, 64, 3), and ‘relu’ is added as the activation function:

`classifier.add(Conv2D(64, (3, 3), input_shape = (64, 64, 3), activation = 'relu'))`

\# Add the pooling layer, with the pool size as 2×2 with the type of pooling layer as max pooling. This layer will reduce the size and complexity of the model without losing performance and spatial structure:

`classifier.add(MaxPooling2D(pool_size = (2, 2)))`

Now add the second convolution layer with 32 filters of kernel size (3, 3), the activation function as ‘relu’, and add one more pooling layer for this convolution layer of type max pooling:

`classifier.add(Conv2D(32, (3, 3), activation = 'relu'))`

`classifier.add(MaxPooling2D(pool_size = (2, 2)))`

Now add the third convolution layer with 32 filters of kernel size (3, 3), activation function as ‘relu’, and add one more pooling layer for this convolution layer of type max pooling.

Try not to add these additional layers if the performance of the model is as expected. If the model is not able to capture the features to the fullest then add the following convolution and pooling layers:

`classifier.add(Conv2D(32, (3, 3), activation = 'relu'))`

`classifier.add(MaxPooling2D(pool_size = (2, 2)))`

Now apply flattening to the convoluted and pooled feature maps. How do the features retain the spatial structure even after flattening and passing through the dense layers? This is because the features are detected using the convolution layers and the pooling layer ignores less relevant features but still retaining the spatial structure of features. Now, what goes into the dense or flattening layer are only the relevant features that have retained the spatial structure. Hence, the spatial structure will not be lost when flattened and passed through the dense layers:

`classifier.add(Flatten())`

`classifier.add(Dense(units = 128, activation = 'relu'))`

`classifier.add(Dense(units = 64, activation = 'relu'))`

`classifier.add(Dense(units = 1, activation = 'sigmoid'))`

Apply a suitable optimization function, ‘adam’ is used here. Use the appropriate loss function like Logarithmic loss, binary cross entropy, or categorical cross entropy. Here, binary cross entropy is used:

`classifier.compile(optimizer = 'adam', loss = 'binary_crossentropy', metrics = ['accuracy'])`

Preprocess the images by using the data preprocessing techniques like scaling, normalization, and transformation to prevent overfitting or for good performance. Have sufficient training and test images so that it has enough correlations and patterns in images and model can be generalized to perform better on the new inputs. Create batches so that random transformation is achieved. The packages from the Keras framework are used for preprocessing, data augmentation, and splitting the data set into the training data set and validation data set:

`from keras.preprocessing.image import ImageDataGenerator`

`trainDataGenerator = ImageDataGenerator(`

`rescale=1./255,`

`shear_range=0.2,`

`zoom_range=0.2,`

`horizontal_flip=True)`

`testDataGenerator = ImageDataGenerator(rescale=1./255)`

`trainingSet = trainDataGenerator.flow_from_directory('trainingSet', target_size=(64, 64), batch_size=32, class_mode='binary')`

`testSet = testDataGenerator.flow_from_directory('testSet', target_size=(64, 64), batch_size=32, class_mode='binary')`

Now train the model for the training data set and evaluate the model for the test data set:

`classifier.fit_generator(trainingSet,`

`samples_per_epoch=8000,`

`nb_epoch=25,`

`validation_data=testSet,`

`nb_val_samples=2000)`

Perform predictions using the trained model for new input images and check the performance of the model:

`import numpy as np`

`from keras.preprocessing import image`

`test_new_image = image.load_img('new_input.jpg', target_size=(64, 64))`

`test_new_image = image.img_to_array(test_new_image)`

`test_new_image = np.expand_dims(test_new_image, axis = 0)`

`result = classifier.predict(test_new_image)`

`training_set.class_indices`

`if result[0][0] == 1:`

`prediction = 'dog'`

`else:`

`prediction = 'cat'`

# [Conclusion](#toc.xhtml#s219a)

Unlike traditional machine learning, deep learning technologies identify and extract the features required for decision making. The features are finally fed to a dense layer for inferencing. The efficiency of learning of the network is reflected through the degree of overlap in the patterns or features captured by different neurons of the network. Less the overlap, better is the learning rate. However, it comes with the need of providing a large dataset for training the network spanning all possible combinations of the input without getting into the problem of data overfitting.

# [Points to remember](#toc.xhtml#s220a)

*   Convolutional neural network uses backpropagation of errors to adjust the weights.
*   Each neuron of the CNN is expected to learn a feature.
*   Many techniques like padding, striding, and pooling are used in the CNN network.
*   Combination of these techniques is what makes CNN the most powerful neural network algorithm.
*   ImageNet is used to host image classification challenges.

# [Questions](#toc.xhtml#s221a)

1.  What are the advantages of deep learning models?
2.  What is the significance of filters in CNN?
3.  What are the factors influencing the accuracy of a CNN classifier?
4.  What are the applications of CNN?
5.  What are the various filtering techniques used in CNN?

# [Multiple choice questions](#toc.xhtml#s222a)

1.  **Choose the correct answer** 
    1.  In CNN, the convolutional filters are used for inferencing.
    2.  The fully connected layer collates the features and infers based on that.
    3.  The filters in the different layers are of equal size.
    4.  All the layers of CNN should have the same number of filters.
2.  **Choose the correct answer** 
    1.  Padding is adding zeros or ones in a matrix.
    2.  Padding is adding any random number across the matrix.
    3.  Padding is removing the last row of the matrix.
    4.  Padding is adding the matrices.
3.  **Choose the correct answer** 
    1.  Pooling is adding a huge number of parameters.
    2.  Pooling is not required in CNN.
    3.  Pooling is reducing the number of parameters.
    4.  All the layers of CNN should have pooling.

# [Answers](#toc.xhtml#s223a)

1.  **b**
2.  **a**
3.  **c**

# [CHAPTER 10](#toc.xhtml#c10)

# [Design with Multi Layered Perceptron (MLP)](#toc.xhtml#c10)

One of the initial learning models developed in the dawn of the AI revolution is the multi-layer perceptron. It emulates the working of a biological neuron. Here, the output signal is generated through a weighted sum of input passed through non-linearity and involves one or more hidden layers. The non-linearity comes in the form of tan hyperbolic, sigmoid, or rectified linear units. The number of hidden layers is often increased to enable the network architecture to learn the fine differences in the pattern. The weights are trained by using one of the most common optimization algorithms such as gradient descent, maximal entropy, and so on.

# [Structure](#toc.xhtml#s224a)

In this chapter, we will discuss the following topics:

*   Introduction
*   Components of MLP 
    *   Layers
    *   Non-linear functions
*   Architectures for MLP 
    *   Learning in MLP
*   Training mechanisms in MLP 
    *   Backpropagation
    *   Optimization
*   Latest trends in MLP 
    *   Student–Teacher method
*   Examples 
    *   Samples

# [Objectives](#toc.xhtml#s225a)

After studying this chapter, you should be able to:

*   Design and implement the MLP classifiers.
*   Choose the correct optimization function.
*   Select the right number of hidden layers.
*   Make use of the appropriate non-linear functions in the simulation.

# [10.1 Introduction](#toc.xhtml#s226a)

In a biological neuron, the input activations are weighted and summed up. This accumulated voltage, after crossing the threshold fires the neuron making the impulse propagate to the next neurons in contact with it through a synapse junction. The contact happens through a chemical medium and the weights depend upon the stimulus–response pattern.

A **Multi-Layered Perceptron** (**MLP**) weighs the input data and passes the accumulated sum over a non-linear transfer function. This action precisely resembles the biological neuron as detailed earlier. There can be several neurons in a layer organized as a vector. An MLP can contain several such layers in between the input and the output, called **hidden layers**.

# [10.2 Components of MLP](#toc.xhtml#s227a)

MLPs are the building blocks of the entire neural network architecture. Generally, MLPs include a lot of activation functions, neurons, and weights. A single perceptron is a single neuron model and using these single units the Neural Networks are constructed. Keeping the human brain as a reference, these MLPs are built around, but may not be the exact replicas of the human brain as such.

Human brains and human thinking come up with the ability to understand the surroundings and learning instinctively, but MLPs are somewhat close resemblance of these. Using MLPs, the near neuron-like connectivity and information passing across various neuron units to predict something out of it is possible but may not be like intuition. These predictive capabilities of the neurons or neural networks are what makes them popular. If one combines mathematics and neural mapping, the learning is activated and used extensively while training these neurons. Please refer to *[Chapters 1](#c01.xhtml), [9](#c09.xhtml)* and *[13](#c13.xhtml)* for detailed learning about the neural networks, various functionalities, and their applications.

Following is the simple perceptron (neuron) with various parameters as defined:

![](images/Figure-10.1.jpg)

**Figure 10.1:** Simple Perceptron (neuron)

The following are the various parameters used in the preceding diagram:

*   x¹, x², …., xn are the input variables.
*   w¹, w², …, wn are the weights
*   “f” is a function.
*   “y” is the output or predicted value.

A simple neuron contains:

*   **Input function:** These inputs are a set of features (typically built using a simple neuron).
*   **Activation function:** Activation functions are nothing but mapping of the summed weighted input to the output of the neuron. These are required to add non-linearity to the functions. For example, Sigmoid, ReLU, Leaky-ReLU, Tanh, and so on.
    
    *   Each of these activation functions is explained in detail as follows:
        
        **1) ReLU:** This is one of the simplest activation functions and is sometimes also called “*Linear Function*”. This is a line originating from a point and terminating at infinity. This function doesn’t help in adding non-linearity to the neural networks or an MLP.
        
        **Equation: f(x) = x**
        
        **Range: (-infinity to infinity)**
        
    
    ![](images/Figure-10.2.jpg)
    
    **Figure 10.2:** ReLU function
    
    **2) Sigmoid:** Sigmoid is one of the popular non-linear functions. This function helps in adding non-linearity with values ranging between zero and one. This function is especially used for the probabilistic models where we expect the output as probability values. Also, in this function, one can find the slope of the sigmoid curve at any two points.
    
    **Value Range: (0, 1) {Probability of values}**
    
    **Equation:**
    
    ![](images/Figure-10.3.jpg)
    
    **Figure 10.3:** Sigmoid function
    
    **3) Leaky ReLU:** ReLU means **Rectified Linear Unit** and this is the most commonly used activation function. This function is heavily used in many CNN neural networks in deep learning.
    
    **Value Range: (-infinity to +infinity)**
    
    **Equation: “max(0.1x, x)”**
    
    ![](images/Figure-7.4.jpg)
    
    **Figure 10.4:** Leaky ReLU function
    
    **4) Tanh:** This is also similar to the sigmoid function but with a different range of values. Also, this function is depicted as an “*S-shaped*” curve.
    
    **Value Range:** **(-1 to 1).**
    
    **Equation: “((exp(x) - exp(-x)) / (exp(x) + exp(-x))”**
    
    **Note**: “exp” is the “Exponent” value.
    
    ![](images/Figure-10.5.jpg)
    
    **Figure 10.5:** Tanh function
    
*   **Weights**: They are the random values that are initialized with some pre-determined range of values.
*   **Outputs (Prediction**): Outputs are the predictions that are what is expected out of a neural network. Based on the type and model, the outputs can be binary, regression, multi-class classification, and so on.
*   **Hidden Layers**: In between the input and output layers are hidden layers. These are called **hidden layers** because they are not directly exposed to the input. The more complex the neural network architecture, the greater the number of hidden layers is included. A “*Simple*” perceptron will not have hidden layers but the “*Single*” layer perceptron may have many layers including the hidden layers. The following figures explain this clearly:
    
    ![](images/Figure-10.6.jpg)
    
    **Figure 10.6:** Simple Perceptron
    
    ![](images/Figure-10.7.jpg)
    
    **Figure 10.7:** Single Perceptron
    

To make things complex and interesting, if more such neurons are connected to build networks of neurons then MLPs become popular and powerful.

Training these MLPs is also crucial. Before beginning with any training model, the data clean-up, preparation, and keeping it ready is important.

# [10.3 Architecture of MLP](#toc.xhtml#s228a)

A neural network that is fully connected with an input layer and an output layer is known as a perceptron. If the number of hidden layers is more than one, then such a network is called **multilayer perceptron** (**MLP**). A perceptron is generally used to learn a linear function while an MLP is used to learn a non-linear function. *[Figure 10.8](#c10.xhtml#fig10_8)* shows the typical network diagram of a multilayer perceptron. As it can be seen, it has two layers of hidden layers, an input layer and an output layer. A multilayer perceptron is one of the most complex architectures of artificial neural networks as this is formed from many layers of a perceptron. By using libraries and frameworks like the combination of TensorFlow and Numpy, the MLPs can be easily developed.

MLP is also an example of a feedforward artificial neural network. MLPs are generally trained on a labeled data and hence, learn the correlation between the input and the output data, so it follows a supervised machine learning algorithm. The hyperparameters are tuned similar to any other model training to reduce the error and achieve the best performance. The number of layers and number of neurons are the hyperparameters of the MLP and these need to be fine-tuned for better accuracy:

![](images/Figure-10.8.jpg)

**Figure 10.8:** Multilayer Perceptron

As MLP is a supervised learning model, the details of the cost function, activation function, backpropagation, and the corresponding learning parameters are all similar to any supervised model in general and hence, they can be referred from *[Chapter 2, Supervised Machine Learning](#c02.xhtml)*.

The input data passes through the input layer, the weights, and the bias together. The inputs are passed through the activation function before they reach the first hidden layer. Then, the same procedure is repeated on the output of the first hidden layer before it is given to the second hidden layer, and so on., till the final output layer is reached. The output of the output layer is compared with the actual output and using the cost function the error is determined. The weights are updated across the layers using the backpropagation technique discussed in *[Chapter 2, Supervised Machine Learning](#c02.xhtml)* to minimize the error determined. The entire procedure is repeated, the hyperparameters and activation function are suitably selected and fine-tuned to achieve the best performance on the given data set.

# [10.4 Training mechanisms in MLP](#toc.xhtml#s229a)

Training an MLP model is similar to any neural network in which the neurons connection weights are adjusted so that the network performs the function for which it is designed. The training is based on a learning mechanism or method which can be either supervised learning or unsupervised learning. The training mechanism for an MLP, hence, will be similar to those described in *[Chapter 2, Supervised Learning](#c02.xhtml)* and *[Chapter 3, Unsupervised learning](#c03.xhtml)*. As given in those chapters, the weights and biases will be updated for the neurons of the hidden layers using the update functions during backpropagation and their values will be processed in the feedforward operation. The hyperparameters like learning rate, momentum, and regularization will be used to fine-tune the model and improve the accuracy so that the model will perform better on the unseen data samples. Some of the following best practices can be used for better training of the MLPs:

*   **Data Preparation**: The data used here is numerical and if the data is categorical, this can be converted to real-values using one-hot encoding to represent.
*   **Selecting Training Algorithm**: Nowadays many algorithms are available, preferably the algorithms like **Stochastic Gradient Descent** (**SGD**) along with the backpropagation algorithms can be used for reducing the error as minimal as possible.
*   **Frequent Update of Weights:** The weight values used in these networks can be frequently upgraded or calibrated for better output values.
*   **Better Prediction**: To get better prediction as output, various unseen data values and out of range values can be used for testing the network.

# [10.5 Latest trends in MLP](#toc.xhtml#s230a)

Due to their simple architecture, MLPs are used in conjunction with emerging applications such as IoTs, 5G supported devices, etc. They fulfil the much-needed requirement of portability, compactness, and interoperability with heterogeneous data. For the same reason, complex architectures such as CNNs are transformed into an MLP through “*knowledge distillation*” before porting onto a handheld device. Generally, one or two hidden layers are sufficient to achieve reasonable accuracy.

# [10.5.1 Knowledge distillation](#toc.xhtml#s231a)

Machine learning models, in general, and deep learning models, in particular, are represented by a large number of parameters. Often it calls for compression to fit into a handheld device. In addition, the computations are optimized if the relevant and more important parameters are stored.

To solve the problem of model compression, knowledge in the larger original model, referred to as a teacher is distilled into a smaller model producing comparable results. This model, called the student model, is realized generally through an MLP network. The student needs to store the most important patterns required for decision-making and this should happen without retraining of the model.

The following diagram explains knowledge distillation with a Teacher-Student model:

![](images/Figure-10.9.jpg)

**Figure 10.9:** Knowledge Distillation – Teacher-Student Model

The teacher model can be a CNN or random forest or a decision tree. The student can still be an MLP and thereby help to achieve interoperability. There can be up to two orders of compression for a nominal drop of 2% accuracy. The trade-off needs to be worked out optimally during knowledge distillation.

Recently, MLP is being used in various domains such as energy, utility, nuclear and smart city, and so on.

# [10.6 Use cases or examples on how to build an MLP with various frameworks](#toc.xhtml#s232a)

The following classification of handwritten digits is performed using the MLP method. Tensorflow and Keras frameworks are used for the implementation and the MNIST data set from Keras is used for training, testing, and validation of the model. The model is built with two hidden layers of 256 and 64 neurons, with ReLU activation function, and cross-entropy as the loss function. The model achieves the training accuracy of 98% and testing accuracy of 97% with hyperparameter, learning rate set to 0.001. The Python program is given as follows:

`## Importing required libraries`

`import keras`

`from sklearn.preprocessing import LabelBinarizer`

`import matplotlib.pyplot as plt`

`import numpy as np`

`import tensorflow as tf`

`from sklearn.metrics import accuracy_score`

`# Load the MNIST dataset from Keras for training and testing`

`(Xtrain, ytrain), (Xtest, ytest) = keras.datasets.mnist.load_data()`

`# normalize the input data samples`

`Xtrain = Xtrain.astype(float) / 255.`

`Xtest = Xtest.astype(float) / 255.`

`# Split the training samples into training and validation samples`

`Xtrain, Xval = Xtrain[:-10000], Xtrain[-10000:]`

`ytrain, yval = ytrain[:-10000], ytrain[-10000:]`

`# Changing dimension of training input images from N*28*28 to N*784, flatten the input size to feed to MLP`

`Xtrain = Xtrain.reshape((Xtrain.shape[0],Xtrain.shape[1]*Xtrain.shape[2]))`

`## Changing dimension of testing input images from N*28*28 to N*784, flatten the input size to feed to MLP`

`Xtest = Xtest.reshape((Xtest.shape[0],Xtest.shape[1]*Xtest.shape[2]))`

`# Changing labels to one-hot encoded vector`

`labelM = LabelBinarizer()`

`ytrain = labelM.fit_transform(ytrain)`

`ytest = labelM.transform(ytest)`

`print('Training samples dimension:');`

`print(Xtrain.shape)`

`print('Testing samples dimension:');`

`print(Xtest.shape)`

`print('Training samples labels dimension:');`

`print(ytrain.shape)`

`print('Testing samples labels dimension:');`

`print(ytest.shape)`

`s = tf.InteractiveSession()`

`# Model architecture`

`# input layer 784`

`# First hidden layer - 256 neurons`

`# Second hidden layer - 64 neurons`

`# Final layer output - 10`

`numClasses = ytrain.shape[1]`

`numFeatures = Xtrain.shape[1]`

`numOutput = ytrain.shape[1]`

`numLayers_0 = 256`

`numLayers_1 = 64`

`# Define the hyper parameters, learning rate and regularizer`

`starterLearningRate = 0.001`

`regularizerRate = 0.1`

`# Placeholders for the input data`

`inputX = tf.placeholder('float32',shape =(None,numFeatures),name="inputX")`

`inputY = tf.placeholder('float32',shape = (None, numClasses),name="inputY")`

`## for dropout layer`

`keepProb = tf.placeholder(tf.float32)`

`# Initialize the weights and bias for layer 1 with random values using He-et-al initialization`

`temp = np.random.randn(numFeatures, numLayers_0) * np.sqrt(2/numFeatures)`

`temp = temp.astype(np.float32)`

`weights_0 = tf.Variable(temp)`

`temp = np.random.random_sample((numLayers_0))`

`temp = temp.astype(np.float32)`

`bias_0 = tf.Variable(temp)`

`print (type(weights_0), weights_0.shape)`

`print (type(bias_0), bias_0.shape)`

`# Initialize the weights and bias for layer 2 with random values using He-et-al initialization`

`temp = np.random.randn(numLayers_0, numLayers_1) * np.sqrt(2/numLayers_0)`

`temp = temp.astype(np.float32)`

`weights_1 = tf.Variable(temp)`

`temp = np.random.random_sample((numLayers_1))`

`temp = temp.astype(np.float32)`

`bias_1 = tf.Variable(temp)`

`# Initialize the weights and bias for final layer with random values using He-et-al initialization`

`temp = np.random.randn(numLayers_1, numOutput) * np.sqrt(2/numLayers_1)`

`temp = temp.astype(np.float32)`

`weights_2 = tf.Variable(temp)`

`temp = np.random.random_sample((numOutput))`

`temp = temp.astype(np.float32)`

`bias_2 = tf.Variable(temp)`

`## Initializing weights and biases and define activation function and dropout`

`hiddenOutput_0 = tf.nn.relu(tf.matmul(inputX,weights_0)+bias_0)`

`hiddenOutput_0_0 = tf.nn.dropout(hiddenOutput_0, keep_prob)`

`hiddenOutput_1 = tf.nn.relu(tf.matmul(hiddenOutput_0_0,weights_1)+bias_1)`

`hiddenOutput_1_1 = tf.nn.dropout(hiddenOutput_1, keepProb)`

`predictedy = tf.sigmoid(tf.matmul(hiddenOutput_1_1,weights_2) + bias_2)`

`## Defining the loss function, here softmax cross entropy is used`

`loss = tf.reduce_mean(tf.nn.softmax_cross_entropy_with_logits_v2 (logits=predictedy, labels=inputy)) \ + regularizerRate * (tf.reduce_sum(tf.square(bias_0)) + tf.reduce_sum(tf.square(bias_1)))`

`## Variable learning rate`

`learningRate = tf.train.exponential_decay(starterLearningRate, 0, 5, 0.85, staircase=True)`

`## Adam optimizer for finding the right weight`

`optimizer = tf.train.AdamOptimizer(learningRate).minimize(loss,var_list = [weights_0, weights_1, weights_2, bias_0,bias_1,bias_2])`

`## Metrics definition`

`correctPrediction = tf.equal(tf.argmax(ytrain, 1), tf.argmax(predicted_y, 1))`

`accuracy = tf.reduce_mean(tf.cast(correctPrediction, tf.float32))`

`## Training parameters`

`batchSize = 64`

`epochs=14`

`dropoutProb = 0.5`

`trainingAccuracy = []`

`trainingLoss = []`

`testingAccuracy = []`

`s.run(tf.global_variables_initializer())`

`for epoch in range(epochs):`

`arr = np.arange(Xtrain.shape[0])`

`np.random.shuffle(arr)`

`for index in range(0, Xtrain.shape[0], batchSize):`

`s.run(optimizer, {inputX: Xtrain[arr[index:index + batchSize]],`

` inputy: ytrain[arr[index:index + batchSize]],`

` keepProb:dropoutProb})`

`trainingAccuracy.append(s.run(accuracy, feed_dict= {inputX:Xtrain,`

` inputy: ytrain, keepProb:1}))`

`training_loss.append(s.run(loss, {inputX: Xtrain,`

` inputy: ytrain, keepProb:1}))`

`## Evaluation of model`

`testing_accuracy.append(accuracyScore(ytest.argmax(1),`

` s.run(predictedy, {inputX: Xtest, keepProb:1}).argmax(1)))`

`## Plotting chart of training and testing accuracy as a function of iterations`

`iterations = list(range(epochs))`

`plt.plot(iterations, trainingAccuracy, label='Train')`

`plt.plot(iterations, testingAccuracy, label='Test')`

`plt.ylabel('Accuracy')`

`plt.xlabel('iterations')`

`plt.show()`

# [Conclusion](#toc.xhtml#s233a)

The MLPs modeled after the neurons provide a powerful tool for function learning. While a lookup table can fetch a certain output value for a pre-defined input string, it fails to provide a definite response for a noisy or intermediate input pattern. At this point, MLPs come into the picture and play a major role, theoretically supporting all possible input patterns. The simple but powerful architecture of the MLPs is useful to realize several AI/ML applications as detailed in the next chapters. The footprint of the architecture is small making it possible to fit into mobile handheld devices, IoTs, and so on.

# [Points to remember](#toc.xhtml#s234a)

*   MLPs are useful to learn simple nonlinear functions.
*   The learnings of different neurons are combined.
*   MLPs consist of the input layer, hidden layer, activation function, weights, and output layer.
*   Various latest algorithms are used to develop and improve the weight calculations like SGD.
*   Usage of non-linearity helps the neurons to tolerate noise.
*   A perceptron is used to learn the linear function while an MLP is used to learn a non-linear function.
*   An MLP is a supervised learning model.

# [Questions](#toc.xhtml#s235a)

1.  What are the factors influencing the choice of the number of hidden layers?
2.  Compare gradient descent with entropy maximization.
3.  Differentiate tanh and sigmoid transfer functions.
4.  What are the applications of MLP?
5.  What are the layers of an MLP?
6.  What are output layers?
7.  What are hidden layers?

# [Multiple choice questions](#toc.xhtml#s236a)

1.  **Choose the correct answer** 
    1.  MLPs are straightforward architectures.
    2.  Gradient descent optimization always finds global minima.
    3.  All the layers in an MLP should have an equal number of neurons.
    4.  Weighted sum in an MLP is always passed through a linear function.
2.  **An MLP is used to learn the linear function.** 
    1.  True
    2.  False
3.  **An MLP cannot have more than two layers of hidden layers.** 
    1.  True
    2.  False
4.  **The learning method of an MLP is similar to unsupervised machine learning.** 
    1.  True
    2.  False
5.  **The hidden layers in an MLP are hidden and are not visible.** 
    1.  True
    2.  False
6.  **An MLP contains input and output layers both.** 
    1.  True
    2.  False

# [Answers](#toc.xhtml#s237a)

1.  **a**
2.  **b**
3.  **b**
4.  **b**
5.  **b**
6.  **a**

# [CHAPTER 11](#toc.xhtml#c11)

# [Long Short Term Memory Networks](#toc.xhtml#c11)

LSTM are a type of artificial neural network that is capable of identifying patterns in sequences of text. There are a lot of applications related to language processing, machine translation, and those involving sequences of data that are solved by the LSTM networks. This chapter discusses how RNN evolved to handle the sequences of data, followed by the GRU and LSTM architecture. It gives the details of the design of the GRU and LSTM cell and explains the gates within them. The variants of LSTM are designed to solve specific problems and it is discussed in the section “*Architecture of LSTM*”. The mechanism of training the LSTM is described in the following section and the section “*Use Case or Example*” gives the programming details of LSTM implementation with an example. The programming example gives the details of the implementation using any of the existing deep learning frameworks. The last section discusses the applications of NLP using LSTM and advancements, and areas that allow the researchers to explore, make discoveries, and build new architectures.

# [Structure](#toc.xhtml#s238a)

In this chapter, the following topics will be discussed:

*   Introduction
*   Recurrent Neural Network (RNN)
*   Gated Recurrent Unit (GRU)
*   Architectures of Long Short Term Memory Networks (LSTM)
*   Training Mechanisms of LSTM
*   Use Cases and Samples using LSTM
*   Natural Language Processing through LSTM and advancements

# [Objectives](#toc.xhtml#s239a)

After studying this chapter, one should be able to:

*   Understand the mechanism of Recurrent Neural Networks.
*   Know Gated Recurrent Unit and **Long Short-Term Memory Networks** (**LSTM**).
*   Understand briefly the different architectures of LSTM.
*   Understand how the LSTM is trained.
*   Program an LSTM model or use cases with LSTM.
*   What is happening in Natural Language Processing using LSTM and its advancements.

# [11.1 Introduction](#toc.xhtml#s240a)

Traditional neural networks take the input and process it using a set of layers and provide the output. The output is dependent on the current input. Suppose the problem is to predict the current output based on the previous inputs. For example, the problem is to predict a word of a sentence based on the previous words. The traditional neural networks are not able to solve this problem. Thus, RNN came into existence which feeds the previous inputs to predict the current input. These networks were able to solve many natural language processing problems. But they had a few disadvantages like vanishing gradients, exploding gradients, limited use of activation functions and because of these issues they were not able to remember a long sequence of words during the prediction of the next word in sequencing models. To overcome these issues, GRU and LSTM came into existence. GRU and LSTM are different in the way how each of the cells is designed, GRU has fewer gates compared to LSTM. The details of these gates will be defined in the later sections. GRU though computes faster compared to LSTM, has a problem of remembering very long sequences of words. LSTM solves this issue by having additional gates. Almost all the state of art problems of NLP is now solved using different flavors of these architectures. LSTM and its variants are used in various applications listed as follows:

1.  Music composition
2.  Human action recognition
3.  Time series anomaly detection
4.  Grammar learning
5.  Machine translation
6.  Image captioning
7.  Language modeling
8.  Handwritten recognition
9.  Question answering system
10.  Protein homology detection

The details of RNN, LSTM, GRU architecture, and training mechanism are detailed in the following sections.

# [11.2 Recurrent neural networks (RNN)](#toc.xhtml#s241a)

In regular or traditional neural networks, the input and output neurons are independent of each other. For example, if there is a problem predicting the next word in the sentence, it requires to remember or have the knowledge of the previous word or words in order to predict the next word. Regular or traditional neural networks do not have the capability to solve these kinds of problems – RNNs came into existence. RNN are a special type of neural network which have the capability of remembering the previous state and hence, will be able to predict the next state based on the previous state. RNNs can be used to solve the problem of predicting the next word in the sentence given the previous word or words. RNNs have a hidden state or memory which remembers the information calculated so far.

Consider a regular neural network with 4 neurons with 1 input neuron, 1 output neuron and two hidden neurons as given in *[figure 11.1](#c11.xhtml#fig11_1)*. *[Figure 11.1](#c11.xhtml#fig11_1)* depicts a traditional neural network with 4 neurons with an input layer, two hidden layers, and one output layer:

![](images/Figure-11.1.jpg)

**Figure 11.1:** Regular Neural Network

As in the traditional neural network, the preceding network with two hidden layers will have its weights and biases. The first hidden layer will have weights w1 and bias b1 and the second hidden layer will have weights w2 and bias b2, respectively. As it can be seen, each of these inputs and outputs is independent of each other and are not dependent on the previous outputs. In RNN, the two hidden layers will be merged into one single layer with same weights and bias and it remembers the output of the previous hidden layer by using it as input to the next hidden layer. This single merged layer is called the recurrent layer. In addition to that, it remembers the previous output of the hidden layer by using it as input to the next hidden layer. This single merged layer is called the recurrent layer.

*[Figure 11.2](#c11.xhtml#fig11_2)* shows the traditional neural network in *[figure 11.1](#c11.xhtml#fig11_1)* being transformed into a recurrent neural network with a single recurrent layer:

![](images/Figure-11.2.jpg)

**Figure 11.2:** Recurrent Neural Network

Recurrent networks are useful in processing the sequence of data and predicting the next word in the sequence. They are called recurrent mainly because they perform the same operation on every element in the sequence and their output is dependent on the previous outputs.

The architecture of an RNN cell is given in *[figure 11.3](#c11.xhtml#fig11_3)*. In this figure, h[t-1] indicates the previous hidden output state, h[t] is the cell hidden state, and x[t] is the cell input at timestamp ‘t’:

![](images/Figure-11.3.jpg)

**Figure 11.3:** Architecture of RNN cell

To understand the computations within the RNN in *[figure 11.3](#c11.xhtml#fig11_3)*, it needs to be unfolded as in the following figure. *[Figure 11.4](#c11.xhtml#fig11_4)* gives the computational graph of RNN given in *[figure 11.3](#c11.xhtml#fig11_3)* showing the hidden states, input and output, and the corresponding weights and bias:

![](images/Figure-11.4.jpg)

**Figure 11.4:** The computational graph of RNN

With this in mind, now the recurrent neural network of *[figure 11.4](#c11.xhtml#fig11_4)* can be mapped using the following equations:

*a[t] = b + Wh[t-1] + Ux[t]*

*h[t] = tanh(a[t])*

*y[t] = c + Vh[t]*

Here, a[t] is the activation value at time step t. The h[t] is the hidden state or memory of the cell at time step 't' and is determined by tanh(a[t]). RNN can have any non-linear transformation function other than tanh, for example, ReLU. Generally, tanh and ReLU are suitable for the sequencing problems. The output y[t] is the output of RNN at time step t. The weight matrix U, V, and W are shared across time steps and U is the weight matrix used for connections from input to hidden state, W is the weight matrix used for connections from hidden state to hidden state, and V is the weight matrix used for connections from hidden state to output state.

The gradient computations in RNN often lead to exploding gradients or vanishing gradients. As it can be seen in RNN, the computation of the gradient involves repeated multiplication of W over time steps. This multiplication of W at each cell causes the problem. In RNN, during the backpropagation process, the gradients are computed by continuous multiplications of derivatives. Hence, if the derivatives are small, repeated multiplication of these will cause the gradient to vanish. This is called the **vanishing gradient** problem. If the gradient value is a big value, then the repeated multiplications of the same will lead to a value towards infinity and cause the gradient to explode. This is called **exploding gradient** problem. The vanishing gradient and exploding gradient problems can be reduced or overcome using the suitable activation functions.

Because of these problems, RNNs have the drawback of learning dependencies over long windows. Hence, new architectures were defined to overcome these problems and GRU and LSTM are among them which will be discussed in the next sections.

# [11.3 Gated recurrent units (GRU)](#toc.xhtml#s242a)

RNNs are useful when it is required to remember every information through time and hence, they are suitable for the time series problems. In some cases, RNNs are also used along with the convolution neural networks to extend the effective pixel neighborhood. RNNs suffer from vanishing gradients and exploding gradients problems. If very deep models need to be built then it is difficult to stack RNNs. To overcome these problems with RNNs, LSTM, and GRU were introduced. While LSTM will be discussed in the next section, in this section the details of GRU will be discussed.

GRUs were designed to solve the problems of vanishing and exploding gradient of RNN. To achieve this, they use the update gate and reset gate. These gates help in either retaining or removing the information and hence, they decide what information needs to be passed to the output.

*[Figure 11.5](#c11.xhtml#fig11_5)* gives the architecture of the GRU cell showing the gates, hidden states, and input and output states:

![](images/Figure-11.5.jpg)

**Figure 11.5:** Architecture of GRU cell

The computation of z[t] is done by the update gate and the formula for z[t] is given as follows:

*z[t] = σ (W[z] x[t] + U[z] h[t-1])*

Here, ‘σ’ (sigma) is the sigmoid function, W[z] is the weight matrix for x[t], x[t] is the input at time step ‘t’, U[z] is the weight matrix for h[t-1], and h[t-1] is the hidden state input from the previous state. The update gate is used to determine how much of the past information needs to be passed to the future and helps to overcome the vanishing gradient problem.

The computation r[t] is done by the reset gate and the formula for r[t] is given as follows:

*r[t] = σ (W[r] x[t] + U[r] h[t-1])*

Here, ‘σ’, x[t], and h[t-1], have the same meaning as in the update gate. W[r] and U[r] are the weight matrices for x[t] and h[t-1] and are different from the update gate. Though the formula is the same as the update gate but the reset gate is used to determine how much of the past information has to be dropped or forgotten.

A new hidden state or new memory state h’[t] is used to store only the relevant information from the previous states using the reset gate. The formula to determine this is given by:

*h′t = tanh(W x[t] + r[t]* [] *U h[t-1])*

Here, h’[t] is the memory state, tanh is the activation function, and W and U are weight matrices. The r[t ] U h[t-1] is the hadamard operation or point-wise operation (the operation is similar to the point-wise operation in matrices for which vectors should be of the same length) between r[t] and U \* h[t-1] which determines what to remove from the previous time steps.

Finally, the h[t] is the hidden output state which is determined based on what needs to be retained (update gate) and what needs to be forgotten (reset gate) is given by the formula given as follows:

*h[t] = z[t]*[] *h[t-1] + (1 – z[t])* [] *h’[t]*

From the preceding details, it is clear that GRU will eliminate the vanishing gradient problem as it does not clear all the previous information but carefully keeps the relevant past information and carries it forward. Hence, if carefully designed, GRUs can be used to solve complex problems involving sequences.

# [11.4 Architectures of Long Short Term Memory Networks (LSTM)](#toc.xhtml#s243a)

Similar to GRUs, LSTM networks also came into existence to solve the problems of RNN, mainly the vanishing gradient problems. The main difference between GRU and LSTM is in terms of gates they operate on, GRU has two gates – update gate and reset gate while LSTM has three gates – input gate, output gate, and forget gate. The gates regulate the flow of information passing through the sequence of data. LSTM perform better than GRU for problems that require remembering long sequences of data. GRU on the other hand, requires fewer computations and train faster on less training data and can be used to build very deep networks.

The core concept of LSTM’s is the cell state, and its various gates. The cell state acts as a transport highway that transfers relative information all the way down to the sequence chain. This can be thought of as the “*memory*” cell of the network. The cell state, in theory, can carry relevant information throughout the processing of the sequence. So, even information from the earlier time steps can make its way to the later time steps, reducing the effects of short-term memory. As the cell state goes on its journey, information gets added or removed to the cell state via gates. The gates are different neural networks that decide which information is allowed on the cell state. The gates can learn what information is relevant to keep or forget during training.

*[Figure 11.6](#c11.xhtml#fig11_6)* shows the architecture of the LSTM cell with input, output, and forget gate. The details of the components in the architecture are discussed as follows:

![](images/Figure-11.6.jpg)

**Figure 11.6:** Architecture of LSTM cell

The forget gate (f[t]) decides which information needs to be retained or dropped for further processing. The equation for the forget gate is given as follows:

*f[t] = σ (W[f] x[t] + U[f] h[t-1])*

Here, W[f] and U[f] are the weight matrices for x[t] and h[t-1], ‘σ’ is the sigmoid activation function, and h[t-1] is the hidden state at timestamp t-1. It will have values between 0 and 1, where closer to 0 means to forget and closer to 1 means to retain.

The input gate decides what new information has to be written to the cell state. It has two parts i[t] and c’[t] and it is given by the following formula:

output of input gate *\= i[t] c’[t]*

*\=* σ(*W[i] x[t] + U[i] h[t-1])* σ(*W[c] x[t] + U[c] h[t-1])*

The ‘i[t]’ decides which values have to be updated based on the application of the sigmoid function to the current input state and previous hidden state. The c’[t] generates new values by passing the input state and previous hidden state through the tanh activation function. With these together and application of hadamard or point-wise multiplication, the input gate decides what new information has to be written to the cell state. The it decides the important information and c’[t] regulates the output using the tanh activation function.

The current cell state c[t] gives the final relevant information based on the forget gate and input gate. It is given by the formula as follows:

*c[t] = f[t]* [] *c[t-1] + i[t]* [] *c’[t]*

The output of this equation will be either 0 or 1, 0 means ‘*drop everything*’ and 1 means ‘*pass everything*’.

The output of the output gate (o[t]) is the sigmoid of the current input and previous hidden state and decides what information is important from these inputs. The formula for the output of this gate is given as follows:

*o[t] = σ (W[o] x[t] + U[o] h[t-1])*

Finally, the output of the cell (h[t]) is given by the current cell state and output gate. It does the hadamard or point-wise operation of o[t] and sigmoid of cell state c[t]. The formula is given as follows:

*h[t] = o[t]* [] σ *(c[t])*

It decides how much of the input, previous hidden state, and current cell state information has to be passed on to the next layer and how much needs to be used for the prediction of output.

There are different flavors of LSTM architecture that are used to solve different problems involving a sequence of data. The next two sections discuss the two most common LSTM architectures used, their purpose, advantages, and disadvantages if any.

# [11.4.1 Bi-directional LSTM](#toc.xhtml#s244a)

The bidirectional LSTM is obtained by keeping two independent regular LSTMs together. This structure allows having both forward and backward information to be available at each time step of the input sequence of data.

*[Figure 11.7](#c11.xhtml#fig11_7)* gives the block diagram of the bidirectional LSTM. It has the input, output, and the two regular LSTMs, one taking the sequence in the forward direction and the other in the backward direction:

![](images/Figure-11.7.jpg)

**Figure 11.7:** Block diagram of Bi-directional LSTM

If the preceding block diagram is unfolded the architecture of the bidirectional LSTM is obtained. Each hidden state of the bidirectional LSTM will have two hidden states, one from the forward layer and the other from the backward layer. The two hidden states will be merged through an operation to get the final output.

*[Figure 11.8](#c11.xhtml#fig11_8)* gives the architecture of the bidirectional LSTM with input, output, hidden states, and forward and backward layer of LSTM:

![](images/Figure-11.8.jpg)

**Figure 11.8:** Architecture of Bidirectional LSTM

For the bidirectional LSTM, as can be seen from *[figure 11.8](#c11.xhtml#fig11_8)*, input is fed in normal time order in one direction and reverse time order in another direction. The forward layer LSTM will be useful to preserve the information from past to future and backward layer LSTM will be useful to preserve the information from future to past with the outputs of both the LSTM combined will allow the bidirectional LSTM to retain the information from both past and future at any time step. These LSTMs are seen to learn faster and perform better than the regular LSTMs. They, however, require more computation power since they need to be trained both in forward and reverse direction.

# [11.4.2 Attention-based LSTM](#toc.xhtml#s245a)

The LSTMs are generally used for machine translation between multiple languages, question and answer dialog generation, and so on. These problems are solved with LSTMs using the encoder-decoder architecture. The encoder takes the input sequence and encodes the input information in the form of a context vector (also known as sentence embedding or thought vector). The context vector will be the summarized output of the input sequence. The decoder in turn uses this context vector as input and provide the translated output. When the encoder-decoder architecture was initially built, the last state of the encoder network was used as the input to the decoder network.

*[Figure 11.9](#c11.xhtml#fig11_9)* gives the block diagram of the encoder-decoder LSTM network as input, output, encoder network, and decoder network. The encoder network is a bidirectional LSTM network and the decoder network is an LSTM network. The output of the encoder network is the encoder hidden state vector which drives the output of the decoder network:

![](images/Figure-11.9.jpg)

**Figure 11.9:** Block diagram of Encode-Decoder LSTM Network

The main disadvantage of the preceding network model is that it cannot give importance to some selective words in the input sequence which is sometimes required based on the context. Consider the following sentences:

“*He was born in West Bengal and moved to Bangalore when he was 5 years of age. Since he is bought up in Bangalore, he is fluent in Kannada and knows a bit of Bengali*.”

In the preceding example, to predict the word Kannada, the phrases “*Bangalore*”, and “*bought up*” need to be given more importance compared to the other words. And though West Bengal is a state name, it needs to be ignored for prediction of the word “*Kannada*”. Hence, when a sentence is generated, it should give attention to a few sets of words that are relevant and contribute more towards the prediction. This concept paved the way to build the encoder-decoder networks with the attention mechanism.

*[Figure 11.10](#c11.xhtml#fig11_10)* gives the architecture of the general attention-based encoder-decoder LSTM network. It shows the encoder network, decoder network, and the attention layer:

![](images/Figure-11.10.jpg)

**Figure 11.10:** Architecture of Encoder-Decoder LSTM Network with Attention Layer

Like earlier, the context vector of the encoder-decoder network is not just the summarized encoder hidden state vector but it is computed in such a manner that it uses the encoded hidden state vector and decoder hidden state at each time step to determine the context vector. Hence, the context vector is intelligently built in this model, it uses the alignment scores (which gives weights to each word based on how much relevant it is) to determine the importance of each word during the prediction in the decoder network. The weights of the context vector are determined using the feed-forward neural network and this network is trained along with the other components of the encoder-decoder network model. The alignment scores are the main ingredients of the attention layer as it quantifies the amount of “*Attention*” each of the encoder outputs contribute to the decoder to produce the next output at any given instance of time. The components of the context vector and the equations used to compute is discussed as follows:

The output of the attention layer is the context vector. Using the weighted sum of encoder output, the context vector is calculated. At timestamp ‘t’, to generate the context vector c[t] for the decoder output y[t], the following formula is used:

![](images/c11eq-1.jpg)

Here, ‘n’ is the number of hidden vectors of the encoder network, ‘i’ is the decoder output state and ‘j’ is the encoder hidden state, and h[j] is the output of the decoder at timestamp ‘t’. As it can be seen from the preceding equation, the context vector is determined as the weighted sum of a[ij] and h[j]. The weights a[ij] are calculated by using the softmax function given as follows. The e[ij] in the following equations are called alignment scores:

![](images/c11eq-2.jpg)

Here, e[ij] is determined using the function ‘f’ which tries to determine the alignment between decoder output ‘i’ and encoder hidden input ‘j’ based on how well they match each other. The e[ij] is determined from the output of the feed-forward neural network which is built using a single hidden layer and this network is jointly trained along with other components of the main model. The equation for determining e[ij] is given as follows:

*e[ij] = f (h^d[j], h^e[i])*

Here, h^d[j] is the previous state decoder output and h^e[i] is the encoder hidden state output at time t. With this, it can be understood that e[ij], the alignment scores are determined from the function f and feed-forward neural network, and a[ij] are the softmaxed output of e[ij].

# [11.5 Training mechanisms of LSTM](#toc.xhtml#s246a)

LSTM is a type of supervised learning neural network. The input value and the target value are known prior to training and hence, any of the supervised training or learning mechanism is applicable for the training of the LSTM. The details of the supervised learning mechanism are provided in *[Chapter 2 “Supervised Machine Learning”](#c02.xhtml)*. So, the details of forward propagation, backward propagation and update functions will be given and the rest of the steps for the training mechanism remains the same. The following equations are for a time step and the same will be applied across all the time steps during the LSTM training.

The equations that are involved during the forward propagation are given as follows:

*z[t] = σ (W[z] x[t] + U[z] h[t-1])*

*a[f] = W[f] z[t] + b[f]*

*a[i] = W[i] z[t] + b[i]*

*a[o] = W[o] z[t] + b[o]*

*a[c] = W[c] z[t] + b[c]*

*f[t] = σ (a[f])*

*i[t] = σ (a[i])*

*o[t] = σ (a[o])*

*c’[t] = tanh (a[c])*

*c[t] = i[t]* [] *c’[t] + f[t] [] c[t-1]*

*h[t] = o[t]* [] *tanh (c[t])*

*v[t] = W[v] h[t] + b[v]*

*[Figure 11.11](#c11.xhtml#fig11_11)* gives the input, outputs, and terms that are involved in the forward propagation for a time step and for a single LSTM cell:

![](images/Figure-11.11.jpg)

**Figure 11.11:** Forward propagation through the LSTM cell

The preceding equations are applied to each cell of the LSTM across all the time steps during forward propagation.

The equations for the backward propagation will be the derivatives of the equation in the forward propagation and are obtained by applying the chain rule.

*[Figure 11.12](#c11.xhtml#fig11_12)* shows the backpropagation in the LSTM cell with the corresponding derivatives calculated using chain rule from output to input:

![](images/Figure-11.12.jpg)

**Figure 11.12:** Backward propagation through the LSTM cell

Suppose the loss function used is the cross-entropy loss function, then the loss function equation is given by:

![](images/c11eq-3.jpg)

Here, y[t] is the target value and y’[t] is the probability of the predicted target value. With this, the derivative of J with respect to the output is given by:

δJ*/*δv*[t] = y’[t] – y[t]*

*and*

δJ*/*δW*[v] =* δJ*/*δv*[t] \** δv*[t]/*δW*[v] =* δJ*/*δv*[t] \* h[t]*

δJ*/*δb*[v] =* δJ*/*δv*[t]*

The derivative of the hidden state is given by the following equation:

δJ*/*δ*h[t] = W[v] \** δJ*/*δv*[t]*

The derivative of the output gate is given by the following equations:

δJ*/*δo*[t] =* δJ*/*δh*[t]* ![](images/eq1.jpg)*tanh(c[t])*

δJ*/*δa*[o] =* δJ*/*δh*[t]* ![](images/eq1.jpg)*tanh(c[t])* ![](images/eq1.jpg)*o[t] (1 – o[t])*

δJ*/*δW*[o] =* δJ*/*δa*[o] \* z[t]*

δJ*/*δb*[o] =* δJ*/*δa*[o]*

The derivative of the cell state is given by the following equations:

δJ*/*δc*[t] =* δJ*/*δh*[t]* ![](images/eq1.jpg)*o[t]* ![](images/eq1.jpg)*(1 - tanh(c[t])²)*

δJ*/*δc’*[t] =* δJ*/*δc*[t]* ![](images/eq1.jpg)*i[t]*

δJ*/*δa*[c] =* δJ*/*δc*[t]* ![](images/eq1.jpg)*i[t]* ![](images/eq1.jpg)*(1 – c’[t])²*

δJ*/*δW*[c] =* δJ*/*δa*[c] \* z[t]*

δJ*/*δb*[c] =* δJ*/*δa*[c]*

The derivative of the input gate is given by the following equations:

δJ*/*δf*[t] =* δJ*/*δc*[t]* ![](images/eq1.jpg)*c[t-1]*

δJ*/*δa*[f] =* δJ*/*δo*[t]* ![](images/eq1.jpg)*c[t-1]* ![](images/eq1.jpg)*f[t] (1 – f[t])*

δJ*/*δW*[f] =* δJ*/*δa*[f] \* z[t]*

δJ*/*δb*[f] =* δJ*/*δa*[f]*

The derivative of the input gate is given by the following equations:

δJ*/*δz*[t] = W[f]* δJ*/*δa*[f] + W[i]* δJ*/*δa*[i] + W[o]* δJ*/*δa*[o] + W[c]* δJ*/*δa*[c]*

δJ*/δc[t-1] =* δJ*/*δc*[t]* ![](images/eq1.jpg)*f[t]*

The preceding derivatives during the backward propagation are calculated for all the time steps in each training iteration or epoch. After each epoch, the weights for the gates and outputs will be updated based on the cumulative cost gradient with respect to the weights and across all time steps.

Assume the weights at the previous iteration were W[f], W[i], W[o], W[c], and W[v] and W’[f], W’[i], W’[o], W’[c], and W’[v] are weights for current iteration respectively:

![](images/c11eq-4.jpg)

*W’[f] = W[f] + (alpha) \** δJ*/*δW*[f]*

*W’[i] = W[i] + (alpha) \** δJ*/*δW*[i]*

*W’[o] = W[o] + (alpha) \** δJ*/*δW*[o]*

*W’[c] = W[c] + (alpha) \** δJ*/*δW*[c]*

*W’[v]\= W[v] + (alpha) \** δJ*/*δW*[v]*

Assuming gradient descent or any variant of gradient descent as the optimization method, the preceding update equations will be used for each iteration of the training.

With the preceding equations for forward propagation, backward propagation, and update functions, the steps of the supervised learning mechanism need to be followed for training the LSTM model.

**Note:** As discussed in [chapter 2](#c02.xhtml), the training mechanism can be improved using the different hyperparameter tuning techniques and optimizer. The performance of a model can be measured using the same techniques as defined in [chapter 2](#c02.xhtml).

# [11.6 Use cases and examples](#toc.xhtml#s247a)

In the following programming example, a text generation use case is given where the LSTM model will be trained with specific text data. The trained model will be used to give a random text as input and check the prediction which will be based on the trained data. As learned during the CNN chapter, the layers of the CNN will learn different features from low level to high level like starting with horizontal lines, vertical lines, curves, colors, edges, corners, contours, shapes, text, and objects. Similarly, the LSTM learns the textual input data by learning the features like text separator, capital letters, punctuation, words, and so on. The program attempts to visualize what features each cell in the LSTM layer depicts during training.

Import the required packages required for the program:

`import re`

`import numpy as np`

`from keras.utils import np_utils`

`from keras.models import Sequential`

`from keras.callbacks import ModelCheckpoint`

`from keras.layers import Dense, Dropout, LSTM`

`import keras.backend as K`

`from IPython.display import display`

`from IPython.display import HTML as html_print`

The following lines are used to read the textual data from the input corpus file “*galaxy.txt*”. The file *galaxy.txt* includes the data from Wikipedia about the galaxy which talks about the system of stars, gas, dust and dark matter:

`# Read data from the corpus file, galaxy.txt`

`fname = "galaxy.txt"`

`rtext = open(fname, 'r', encoding='utf-8').read()`

`rtext = re.sub(r'[]+', ' ', rtext)`

The following lines will preprocess the input textual data by performing the following operations. Normally the word2vec, Glove, and BERT embedding will be used to represent the input and output data. In this program, the one-hot vector representation is used. The program should be customized only to handle input data in case a different embedding is used, with no changes to the other parts of the code:

1.  Sorting of input data
2.  Character to integer conversions
3.  Indexing the input data
4.  Normalization of data as applicable
5.  Use an embedding for input and target data
    
    `# generate a mapping of characters which are unique and map them to integers`
    
    `characters = sorted(list(set(raw_text)))`
    
    `print (len(characters))`
    
    `charactersToInteger = dict((ch, index) for i, ch in enumerate(characters))`
    
    `integerToCharacter = dict((index, ch) for index, ch in enumerate(characters))`
    
    `# Get the count of characters and unique characters`
    
    `numOfChars = len(rtext)`
    
    `numOfVocab = len(characters)`
    
    `# To get the dataset for training, prepare input to output pairs encoded as integers`
    
    `lengthOfSequence = 100`
    
    `dataX = []`
    
    `dataY = []`
    
    `# dataX will be input data and dataX will be the target output`
    
    `for i in range(0, numOfChars - lengthOfSequence, 1):`
    
    ` inSequence = raw_text[i:i + lengthOfSequence]`
    
    ` outSequence = raw_text[i + lengthOfSequence]`
    
    ` dataX.append([char_to_int[char] for char in inSequence])`
    
    ` dataY.append(char_to_int[outSequence])`
    
    `numOfPatterns = len(dataX)`
    
    `print("Total number of Patterns in the corpus or dataset: ", numOfPatterns)`
    
    `# reshape X`
    
    `# [samples, time steps, features]`
    
    `X = np.reshape(dataX, (numOfPatterns, lengthOfSequence, 1))`
    
    `# normalize X for training`
    
    `X = X / float(numOfVocab)`
    
    `# one hot encode the output variable which will be the target output`
    
    `y = np_utils.to_categorical(dataY)`
    

The model that needs to be trained can be saved in a model file and with a specific name given to it as follows:

`# The file name that needs to be used to save the model`

`filepath="galaxyLSTMmodel-{epoch:02d}-{loss:.4f}.hdf5"`

`checkpoint = ModelCheckpoint(filepath, monitor='loss', verbose=1, save_best_only=True, mode='min')`

`callbacks_list = [checkpoint]`

The following lines define the LSTM model architecture, with a stacked layer of two LSTM, and dropout layers. The architecture used as follows is to illustrate the input, output, LSTM layers, training, prediction, and visualization of LSTM cells and is not meant to show the best performing model in terms of prediction accuracy:

`# Now define the LSTM model with required layers`

`model = Sequential()`

`model.add(LSTM(512, input_shape=(X.shape[1], X.shape[2]), return_sequences=True))`

`model.add(Dropout(0.6))`

`model.add(LSTM(256))`

`model.add(Dropout(0.5))`

Now, define the loss function, training parameters (epochs, optimizer, and batch size) and train the model accordingly:

`# define loss function and epochs for the training`

`model.compile(loss='categorical_crossentropy', optimizer='adam', metrics=['accuracy'])`

`model.summary`

The output of the program after the preceding lines are executed is given as follows:

Using TensorFlow backend.

Total Patterns: 143441

**Model:** "sequential\_1"

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

Layer (type) Output Shape Param #

\============================================================

lstm\_1 (LSTM) (None, 100, 512) 1052672

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

dropout\_1 (Dropout) (None, 100, 512) 0

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

lstm\_2 (LSTM) (None, 256) 787456

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

dropout\_2 (Dropout) (None, 256) 0

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

dense\_1 (Dense) (None, 73) 18761

\============================================================

**Total params:** 1,858,889

**Trainable params:** 1,858,889

**Non-trainable params:** 0

`# Train model with same data`

`model.fit(X, y, epochs=200, batch_size=1024, callbacks=callbacks_list)`

While the training starts, the model learns the features progressively and at each epoch, the sample output is given as follows:

`Epoch 1/300`

`143441/143441 [==============================] - 1610s 11ms/step - loss: 3.3080 - accuracy: 0.1519`

`Epoch 00001: loss improved from inf to 3.30801, saving model to galaxyLSTMmodel-01-3.3080.hdf5`

`Epoch 2/300`

`143441/143441 [==============================] - 1611s 11ms/step - loss: 3.1967 - accuracy: 0.1672`

`Epoch 00002: loss improved from 3.30801 to 3.19674, saving model to galaxyLSTMmodel-02-3.1967.hdf5`

`Epoch 3/300`

`143441/143441 [==============================] - 1582s 11ms/step - loss: 3.1508 - accuracy: 0.1690`

It can be noticed that as the number of epochs is increasing the loss is decreasing and accuracy is increasing:

`# LSTM layer with output shape (Batch_Size, 512)`

`lstm = model.layers[2]`

After the model is trained, it can be used to predict and visualize the learning using activation. The following lines define the functions which are used for visualization:

`# Get output from intermediate layer to visualize activation`

`attn_func = K.function(inputs = [model.get_input_at(0), K.learning_phase()], outputs = [lstm.output])`

`# Function to visualize the LSTM cell learnings`

`def cellVisualize(ovalues, rlist, cell_no):`

`print("\nCell Number:", cell_no, "\n")`

`textColours = []`

`for i in range(len(ovalues)):`

` text = (rlist[i], getColor(output_values[i][cell_no]))`

` textColours.append(text)`

`printColor(textColours)`

`# get color for a given value`

`def getColor(value):`

`colors = ['#85c2e1', '#89c4e2', '#95cae5', '#99cce6', '#a1d0e8'`

` '#b2d9ec', '#baddee', '#c2e1f0', '#eff7fb', '#f9e8e8',`

` '#f9e8e8', '#f9d4d4', '#f9bdbd', '#f8a8a8', '#f68f8f',`

` '#f47676', '#f45f5f', '#f34343', '#f33b3b', '#f42e2e']`

`value = int((value * 100) / 5)`

`return colors[value]`

`def sigmoid(x):`

`z = 1/(1 + np.exp(-x))`

` return z`

The model can now be used to make a prediction on a random sequence and observe the activation:

`# Get Predictions given the input of random sequence`

`def get_predictions(data):`

`start = np.random.randint(0, len(data)-1)`

`pattern = data[start]`

`resultList, outputValues = [], []`

`print("\"" + ''.join([integerToCharacter[value] for value in pattern]) + "\"")`

`for i in range(500):`

` # Reshaping input array for predicting next character`

` x = np.reshape(pattern, (1, len(pattern), 1))`

` x = x / float(numOfVocab)`

` # Predict the text for the given random input`

` prediction = model.predict(x, verbose=0)`

` # Get the LSTM Activations from the attention function`

` output = attn_func([x])[0][0]`

` output = sigmoid(output)`

` outputValues.append(output)`

` # Get the predicted character`

` index = np.argmax(prediction)`

` result = int_to_char[index]`

` # Now the current character is predicted, prepare for the next character`

` inSequence = [int_to_char[value] for value in pattern]`

` pattern.append(index)`

` pattern = pattern[1:len(pattern)]`

` # Save generated characters in a list`

` resultList.append(result)`

`return outputValues, resultList`

`predictedOutput, ListResult = get_predictions(dataX)`

`cellsToBeVisualized = [give the cell numbers]`

`for ncell in cellsToBeVisualized:`

` cellVisualize(predictedOutput, ListResult, ncell)`

The cells given in the list of `cellsToBeVisualized` can be visualized in the output. It shows which words or what the cell is looking like while predicting the next word.

While the model is trained for more number of epochs, it can be seen that each of the cells of the LSTM learn distinct features. When the preceding model was trained for 50 epochs, it was observed that the cell 99, 112, and 349 were trained to learn the following features.

Cell number 99 was learning the first two characters of each word in the sentence. Cell number 112 was learning the middle character of each word in the sentence and cell number 349 was learning the last two characters of each word in the sentence. Likewise, when the model is trained for a greater number of epochs, it can be observed that the cells were learning more complex features like quoted sentences, capital letter words, and so on.

As indicated earlier the preceding program illustrates how to code an LSTM model with simple model architecture and to visualize the LSTM cells to know the learning patterns. It helps to know what cells are activated during the prediction of a word.

# [11.7 NLP using LSTM and advancements](#toc.xhtml#s248a)

The natural language processing models can be designed using different types of deep learning architectures like MLP, RNN, CNN, and LSTM and any combination of these can also be used. There are various text representations like word2vec, Glove, BERT, ELMo, GPT, and fastText and each have their advantages and are used based on the NLP application purpose and usage. A lot of development is happening on AI bots that uses NLP – Alexa, Siri, Cortana, and Google Assistant. The use of natural language processing has now reached our daily life with search engines, chatbots, machine language translations, virtual assistants, Q&A systems, and so on. So, the world has seen a lot of advancements in the NLP over the years. A brief history with the latest advancements in the field of NLP is discussed as follows:

The first feed-forward neural network (neural language model) was proposed in 2001 by Bengio et al. Later, the feed-forward neural networks were replaced with RNN, LSTM, GRU and recently the combination of deep learning architectures like MLP, RNN, CNN, and LSTM are used as applicable to get higher performance and accuracy.

Multi-task learning was an idea that was proposed by *Rich Caruana* in 1993. Later, it was applied to pneumonia detection in 1998 by *Caruana*. In 2008, *Collobert* and *Weston* applied the multi-task learning neural networks for NLP. This lead to many ideas where the pre-trained models for word embeddings are used to train the CNN for text processing. Over the recent years, multi-task learning is gaining a lot of importance to solve the NLP problems.

Vector representations for words were used as early as 2001 in text processing applications. The generation of word embedding from the neural network trained model was proposed in 2013 by *Mikolov et al*. With this, word2vec word embedding came into existence and improved the performance of the NLP applications over other word representations. Post that, a lot of pre-trained word embeddings evolved like Glove, fastText, ELMo, BERT, BERT-1, GPT, GPT-2 which gave better performance compared to the earlier word embedding and each of them have their significance in terms of representation of word embedding.

RNN, CNN, and LSTM were adapted to NLP tasks during the years 2013 and 2014. A general framework for mapping one sequence to another was proposed by *Sutskever* in 2014 which became an encoder-decoder neural network. This paved a way for the generation of new ideas in machine translation, natural language generation, caption generation, and named entity recognition.

The attention-based mechanism, proposed by *Bahdanau et al*., 2015 was a key idea that allowed the machine translation models with an attention mechanism to outperform the earlier models without them. *Luong et al*., 2015 proposed different types of attention. These models were used for constituency parsing, reading comprehension, and transformer architecture.

The memory-based networks similar to attention-based networks were developed from 2014 to 2017, for example, neural turing machines, memory networks, dynamic memory networks, and recurrent entity networks. These networks were suitable for handling reading comprehension and language modeling applications.

The following are a few advancements in the field of NLP starting from 2017:

In 2017, transformers with self-attention by *Google* made a breakthrough in NLP. **Bidirectional Encoder from Transformers** (**BERT**) which uses transformers and transfer learning (and gives word embedding) is currently one of the state of the art word embedding used for most of the NLP tasks. In 2018, **Universal Language Model Fine-Tuning** (**ULMFit**) provided the use of transfer learning in the field of NLP. It uses AWD-LSTM **Asynchronous Stochastic Gradient** (**ASGD**) Weight Dropped) as its building block. In addition to the previously mentioned a few other models which made advancements are as follows:

1.  Google’s Transformer-XL
2.  XLNet
3.  PyTorch-Transformers
4.  OpenAI’s GPT-2
5.  RoBERTa: A Robustly optimized BERT pretraining approach
6.  Baidu’s Enhanced Representation through Knowledge Integration (Baidu’s ERNIE)
7.  Facebook AI’s XLM/mBERT
8.  spaCy-PyTorch – Transformers
9.  Stanza

There are many frameworks and tools that are used for building deep learning NLP models. A few of them are listed as follows:

*   AllenNLPFramework is suitable for building the NLP deep learning models mainly for solving the semantic NLP tasks. It is built on top of PyTorch.
*   PartAI is a framework written in Python and is an open-source platform for dialog research. It supports sharing, training, and testing of dialog models.
*   OpenNMT is an open-source generic toolkit that is mainly used to perform tasks such as machine translation, image to text, and speech recognition. It is designed to provide maintenance of model modularity, readability and to support significant research extensibility.
*   Stanford Generalized Tool can run as a simple web service that provides APIs for a number of common programming languages. It can be used for sentiment analysis and entity recognition across 53 languages in addition to other NLP tasks.

Other general frameworks for building deep learning NLP models which solve NLP applications are TensorFlow, PyTorch, Theano, Keras, and Chainer.

# [Conclusion](#toc.xhtml#s249a)

RNN, GRU, and LSTM are artificial neural networks that are used to solve the most NLP-based problems. LSTM has different variants which are designed based on the specific problems they are intended to solve. A lot of new variants are evolving with complex architectures which are able to provide solutions to handle the complex sequence of data that were never thought of being solved by machines. It is now used for almost all the applications using NLP, machine language translations, grammar learning, music composition, handwriting, and human action recognition. Though LSTM solves many problems of NLP, new architectures have evolved with exploration and research in this space. The rise of transformers, a combination of LSTM and CNN, BERT embedding have paved a way for building advanced models compared to LSTM to handle the NLP-based applications. A type of artificial neural network which learn the representation of a set of data and are used typically for dimensional reduction is called **auto encoders**. The next chapter discusses in detail the auto encoders, their usage, architecture, and applications.

# [Points to remember](#toc.xhtml#s250a)

*   RNN was evolved to solve the problems involving sequencing of data.
*   GRU and LSTM came into existence to overcome the disadvantages of RNN.
*   GRU is made up of two gates – Update Gate and Reset Gate.
*   LSTM is made up of three gates – Forget Gate, Input Gate, and Output Gate.
*   The forward layer of bidirectional LSTM is used to preserve the sequence from past to future and the backward layer is used to preserve the sequence from future to past.
*   The attention layer in the encoder-decoder LSTM network is used to compute the context vector which is used to retain the important words in the sequence of data.
*   The forward propagation, backward propagation, and update equations for the LSTM can be used with the supervised training mechanism to build the LSTM model.

# [Questions](#toc.xhtml#s251a)

1.  What led to the evolution of RNN?
2.  List the advantages and disadvantages of RNN.
3.  What are the differences between GRU and LSTM?
4.  Describe the architecture of LSTM with a diagram.
5.  Draw a neat diagram of the architecture of GRU.
6.  Briefly describe the working of the bidirectional LSTM with a diagram.
7.  Describe with equations how the context vector is built in the attention-based encoder-decoder LSTM network.
8.  What is the important step in the training mechanism of LSTM?
9.  Give the pseudo-code in about 10 lines for implementing the bidirectional LSTM.

# [Multiple choice questions](#toc.xhtml#s252a)

1.  **Choose the correct answer** 
    1.  RNN can use any non-linear function as an activation function.
    2.  RNN can be used for remembering long sequences of data.
    3.  RNN is a type of artificial neural network.
    4.  RNN has two gates forget gate and reset gate.
2.  **Choose the correct answer** 
    1.  GRU and LSTM try to overcome the vanishing gradient problem of RNN.
    2.  GRU is made up of three gates – forget gate, reset gate, and output gate.
    3.  LSTM is made up of three gates – forget gate, update gate. and output gate.
    4.  GRU and LSTM are traditional neural networks.
3.  **Choose the correct answer** 
    1.  Forward propagation and backward propagation equations of LSTM are the same as for GRU and RNN.
    2.  GRU, RNN, and LSTM have the same update equations for weights and bias.
    3.  GRU is most efficient in performance among LSTM, GRU, and RNN.
    4.  Supervised training mechanism can be used for the training of LSTM with appropriate equations defined for forward propagation, backward propagation, and update functions for weights and bias.
4.  **Choose the correct answer** 
    1.  word2vec, Glove, and one-hot embedding can only be used as input data representation for LSTM.
    2.  BERT is a kind of LSTM architecture.
    3.  The performance of LSTM depends on the kind of embedding used to represent input data.
    4.  GRU, LSTM, and RNN will work only with glove embedding.
5.  **Choose the correct answer** 
    1.  The attention mechanism evolved as an improvement to the existing encoder-decoder machine language translation neural network.
    2.  The attention mechanism will encode all information in one fixed-width vector rather than allowing the network to refer back to the input sequence.
    3.  The attention model generates a context vector that is the same at each output time step.
    4.  The attention mechanism enables the LSTM model with attention with the ability to consider all inputs or features for prediction.

# [Answers](#toc.xhtml#s253a)

1.  **c**
2.  **a**
3.  **d**
4.  **c**
5.  **a**

# [CHAPTER 12](#toc.xhtml#c12)

# [Autoencoders](#toc.xhtml#c12)

Autoencoders are a form of representation learning, in which each layer of the neural network learns a representation of the original features. Also, autoencoders are one of the feature extraction methods used widely.

In the layered approach, layer-by-layer each autoencoder learns complicated representations from the simple representations, increasingly. This is known as the “*hierarchy of concepts*”.

*Tensorflow* and *Keras* are the two popular libraries that are used to build and represent autoencoders. Generally, autoencoders are built using an “*encoder*” and a “*decoder*”. An encoder is used to compress the high-dimensional input data. A decoder is used to decompress a provided representation back to the original data format/domain. Autoencoders are the simplest form of neural network. They are used to generate data features. They form a part of many deep learning models and methods.

# [Structure](#toc.xhtml#s254a)

In this chapter, we will discuss the following topics:

*   Introduction to autoencoders and their simple architecture.
*   Types of autoencoders 
    *   Undercomplete autoencoders
    *   Overcomplete autoencoders
    *   Denoising autoencoders
    *   Sparse autoencoders
    *   Stacked autoencoders
    *   Variational autoencoders (VAEs)
    *   Other autoencoders 
        *   Adversarial autoencoders
        *   Winner-take-all (WTA) autoencoders
        *   Contractive autoencoders
*   Examples and Samples 
    *   Some samples with examples

# [Objectives](#toc.xhtml#s255a)

After studying this chapter, you should be able to:

*   Understand the mechanism of autoencoders.
*   Various types of autoencoders.
*   What is encoding and decoding.
*   How autoencoders can be used for dimensionality reduction.
*   Examples or use cases of using autoencoders.

# [12.1 Introduction to autoencoders and simple architecture](#toc.xhtml#s256a)

Autoencoders have been used in the software industry for the last several years for dimensionality reduction and automatic feature generation, especially to build **Generative Adversarial Networks** (**GANs**). Autoencoders are sometimes termed as the feedforward neural networks as the input is the same as the output. By the compression technique, they compress the input into lower-dimensional code and then get back the output using the decompression techniques. Generally, the autoencoders consist of three components, “*Encoder*”, “*Code*” and “*Decoder*” and these components are a part of this simple architecture.

In the following architecture, if you see both, the encoder and decoder are fully connected feedforward neural networks. The code is a single layer simple **Artificial Neural Network** (**ANN**) including the dimensionality reduction method that we can use:

![](images/Figure-12.1.jpg)

**Figure 12.1:** Simple architecture of autoencoders

An autoencoder is a type of **Neural Network** (**NN**) that is used to learn the efficient coding of especially unlabeled data (unsupervised learning).

**Autoencoders can be broken into three parts:**

1.  **Encoder:** This part of the architecture is used to compress or down sample the input into a smaller number of bits or quantities. This space is sometimes called a “*latent-space*” or “*bottleneck*”. All these input points are the compressed bits that represent the original input space and all these are together called the “*encoding*” part of the input.
    
    Autoencoders are used to generate multiple patterns from the input.
    
2.  **Decoder:** This part of the architecture is used to reconstruct the input using only the encoding of the input. In some cases, if the decoder can reproduce the same output as the input provided to it, we call that the encoder can produce the best encodings that are possible.
    
    Using the pattern generated from an encoder, the original input is generated. Under an ideal condition, it is the same as the input signal. However, due to noise, there will be some changes in the pattern in the encoder, but the decoder will generate even when there is noise.
    
3.  **Codings or Code:** These autoencoders are also used for the efficient representation of input data which is called “*codings*” and without any supervising required. The pattern itself is taken as code and is a representative of the input. A small distortion will act as a resemblance of the input pattern.

So, autoencoders are unsupervised meaning they use unlabeled training data. As mentioned earlier, the simple output generated from autoencoders is typically single-dimensional, which is why they are used for dimensionality reduction. **Autoencoders are called in short AEs as well. In this chapter, if AE is used anywhere means it is autoencoders.**

Following are some of the well-known advantages of autoencoders:

*   Autoencoders act as powerful feature detectors.
*   Autoencoders can be used for dimensionality reduction.
*   AEs are capable of randomly generating new data which look similar to the training data.
*   AEs can be easily used for unsupervised training in deep neural networks.
*   Using AEs, we can limit the size of the internal representation of input data.
*   AEs provide computational efficiency as they help in reducing the dimensions.

Some of the disadvantages of AEs are as follows:

*   Sometimes while reducing the dimensionality, the actual meaning of the training data set may be lost.
*   One has to be a little careful on the dimensionality reduction aspects.

Autoencoders exhibit the following characters:

1.  **AEs are data specific**: The compression of data is similar to what AEs have been trained on. Based on the features and attributes, AEs take the compression action, for example, AEs that are trained on sound cannot be used for faces.
2.  **AEs are lossy**: This means that when the decompression is done, the output will be degraded as compared to the original input that was passed on.
3.  **AEs learn automatically from the data examples**: Easy training can be used on any specific type of input data that is available.

**Comparison of Autoencoders and PCA:**

Even though both PCA and autoencoders are dimensionality reduction methods/techniques, there is a major difference between the two. The PCA uses linear transformation as compared to the autoencoders which use non-linear transformations.

Autoencoders are much more noise-tolerant than PCA. While autoencoders are associated with the encoder-decoder model, but in PCA multiple components are used. PCA is used for pattern storage, computation reduction, and other similar tasks. But in an autoencoder, it is mainly used for the recovery of the images from the noisy images.

**Sample use case of encoding and decoding the image:**

Consider how the encoding and decoding for an image are done stepwise. After we understand the architecture as explained previously, first we have to carry out the encoding of the image and then decoding of the image to be done step-by-step:

1.  **First, encoding of an image**:
    
    Take a sample input image that is passed through a series of convolutions and the image size is compressed/condensed into a smaller-sized vector. This compressed vector represents the features that are used to reconstruct another image with these features.
    
2.  **Second, decoding an image**:
    
    As explained previously, the compressed/condensed vector (of the image) is applied with the deconvolution layers which increases the image size and tries to restore it to its original size:
    
    ![](images/Figure-12.2.jpg)
    
    **Figure 12.2:** Encoder and decoder with the original and re-constructed input image
    

Following are the code snippets and examples of the MNIST data set which is downloaded and used with the autoencoder. The final code snippet shows how the autoencoder (along with encoder and decoder) helps in reducing the noise from the sample output:

![](images/Figure-12.3.jpg)

**Figure 12.3:** Code snippet for import all the required library functions

In the preceding figure, the Python code is used for various Keras libraries that are required to build the autoencoder that is imported along with the MNIST data set. The data set is downloaded to extract the digits.

![](images/Figure-12.4.jpg)

**Figure 12.4:** Code snippet for setting up the Train and Test sets

In the preceding figure, the training and testing split of the data set along with scaling is done. Also, these numpy arrays are reshaped to match the 28 X 28 matrix shape.

![](images/Figure-12.5.jpg)

**Figure 12.5:** Code snippet for adding the noise factor to the train and test set

In the preceding figure, the noise level is introduced using the `numpy random.normal` function. The noise level can be anywhere between 0.1 to 0.5.

![](images/Figure-12.6.jpg)

**Figure 12.6:** Code snippet for printing the random digits from the MNIST dataset

In the preceding figure, some of the random digits from the MNIST data set are printed to show how the noise level is obstructing the actual images. Also, these digits are plotted using the `matplotlib` library along with the plot function.

![](images/Figure-12.7.jpg)

**Figure 12.7:** Code snippet for building the input layer

In the preceding figure, the input layer is created with a 28 X 28 shape.

![](images/Figure-12.8.jpg)

**Figure 12.8:** Code snippet for building the Autoencoder along with CNN layers

In the preceding figure, the Python code is to be used for the CNN model along with the maxpooling filtering technique to build encoding and decoding. This code also has padding which is used along with the ‘*relu’* and ‘*sigmoid’* activation functions accordingly. The ‘*Adam’* optimizer is used in the final autoencoder function.

![](images/Figure-12.9.jpg)

**Figure 12.9:** Code snippet for training the AE with 25 epochs

In *[figure 12.8](#c12.xhtml#fig12_8),* the number of epochs run is 25 with a batch size of 128. The hyperparameter shuffle = True indicates that the shuffling of the training set is done.

![](images/Figure-12.10.jpg)

**Figure 12.10:** Code snippet for training the AE with 25 epochs

In the preceding figure, the complete autoencoder is fit to the model and is executed with 25 epochs along with the batch size of 128. The number of epochs can be anywhere around 25-100 for better output.

![](images/Figure-12.11.jpg)

**Figure 12.11:** Final Code snippet for displays the digits without noise level

In the preceding figure, the MNIST data (random number samples) are plotted using the matplotlib library function. It can be clearly seen how the noise reduction is done as compared to *[figure 12.5](#c12.xhtml#fig12_5)* using the autoencoders.

# [12.2 Undercomplete autoencoders](#toc.xhtml#s257a)

The autoencoder is considered “*undercomplete*” if the encoder function’s output has fewer or lesser dimensions than that of the original input dimensions. By doing this, the autoencoder minimizes the error or loss function and thus reduces the overall loss of the reconstruction error.

There are different challenges that are posed when the autoencoder with encoder and decoder are facing linear and non-linear functions. One has to make sure that AE’s have proper data either in linear or in a non-linear fashion, if too much capacity is fed into autoencoders, instead of learning from the training data, they will try to copy or memorize the things and replicate the same. One has to keep this in mind while constructing any such autoencoders.

In any undercomplete autoencoders, there will not be explicit regularization, these will be trained based on the reconstruction loss. This can be achieved by the means of having a restricted number of hidden layer nodes.

Making sure that the model is not memorizing the training data provided is the key challenge here. Keeping this in mind, the hidden layers/nodes have to be designed in such a way that the data is mapped to the identified index properly.

# [12.3 Overcomplete autoencoders](#toc.xhtml#s258a)

If the autoencoder learns from the representation in a greater number of dimensions than the actual or original input number of dimensions, this is called the “*overcomplete*” autoencoder.

These types of autoencoders are successfully used for dimensionality reduction techniques and automatic feature engineering methodologies. Regularization used here penalizes the complete neural network for learning unnecessary and complex functions. But having said that, it is difficult to design the overcomplete autoencoders.

The overcomplete autoencoders provide the possibility of learning a greater number of features and in some cases, this may lead to overlearning and may become useless.

One has to be cautious in choosing the number of hidden layers while designing the overcomplete autoencoders.

# [12.4 Denoising autoencoders](#toc.xhtml#s259a)

In cases where we assume that the noise levels are already present and needed to be removed like in audio-video recordings with background noise or in some cases where the original data is corrupted with some noise levels, the “*denoising*” autoencoders can be used. These autoencoders can be used to remove the clutter from the voice chat, or blurring of the images, removing the background noise levels from the recordings, etc. The actual/original image or voice can be completely and clearly isolated using such denoising autoencoders.

# [12.5 Sparse autoencoders](#toc.xhtml#s260a)

The number of active neurons can be reduced by adding an appropriate term to the cost function, this leads to one of the best features extractions called “*sparsity*” (thinly scattered or distributed). In some cases, only 5-10% of the active neurons are considered inside the coding layer. Because of this nature, the autoencoder represents each input as a combination of a small number of activations, which are nothing but each representation of the useful feature.

Some of the key considerations while constructing the sparse autoencoders are as follows:

*   The batch size must not be too small, if so, it may lead to an inaccurate mean.
*   Measure the actual sparsity of the coding layer during each of the training iteration.
*   Penalize the neurons which are active by adding a sparsity loss to the cost function.
*   One best approach is to simply add the squared error to the cost function.

**Note:** Mean Squared Error: This is explained in detail in [Chapters 2](#c02.xhtml) and [3](#c03.xhtml).

# [12.6 Stacked autoencoders](#toc.xhtml#s261a)

Like in any other neural network, autoencoders can have multiple hidden layers which are connected with the input and output layers. This is called **Stacked Autoencoder**. Adding multiple layers help in learning complex coding:

![](images/Figure-12.12.jpg)

**Figure 12.12:** Architecture of stacked autoencoders

The preceding diagram shows how the simple stacked autoencoder architecture can be built and here all the hidden layers are connected with the input and output layers. Input is passed with the number of units; these units can be of pixel value or data point value based on the type which can be an image or any other data format.

If we build a perfect autoencoder that takes inputs and reconstruct the output exactly, then it beats the purpose of learning and the output will map to the input. If it is powerful then the learning that is expected from this autoencoder will be lost, so one has to make sure they are not powerful while designing any autoencoders.

The stacked autoencoder is generally symmetrical, which is the hidden layers above and below the central hidden layer are equally distributed. For example, for the data sets like MNIST, the number of inputs and output units can be 784 each (28 X 28 matrix). For each of the hidden layers, we can choose the respective number of neurons and this can be design-specific.

Unsupervised pre-training with various combinations of autoencoder can be used to build a stacked autoencoder model, successfully. After each round of pre-training, the visualization of the output can be verified to check how near the training has achieved the desired result.

`Sknn.ae.Layer` is a module which is a neural network that is made up of stacked layers of weights that encode the input data (we can call it upward pass) and then decode it again to downward pass. The non-linear activations are applied to this layer.

In practice, you need to create a list of these specifications and provide them as the layers parameter to the `sknn.ae.AutoEncoder` constructor.

The following is the library used to define and use autoencoders:

 
| **The class defined** || **Class defined** |
| --- | --- |
| `classsknn.ae.Layer` || `classsknn.ae.Layer(activation, warning=None, type='autoencoder', name=None, units=None, cost='msre', tied_weights=True, corruption_level=0.5)` |

**Table 12.1:** Autoencoder library function

# [12.7 Variational autoencoders (VAEs)](#toc.xhtml#s262a)

In 2014, *Diederik Kingma* and *Max Welling* introduced the “*variational autoencoders*” that became popular quickly. These autoencoders are quite different as compared to any other autoencoders.

Following are some of the unique characteristics of these autoencoders:

*   These autoencoders are probabilistic, which means the outputs are determined by probability chances.
*   These are also called generative autoencoders, which means that they can generate new instances which may be similar and may look like they were sampled from the training set that was used.
*   These autoencoders resemble RBMs.
*   These autoencoders are easier to train.

A VAE autoencoder is an architecture that consists of both an encoder and decoder and both of these are trained to minimize the reconstruction error as much as possible so that there is a minute difference between the encoded and decoded initial data. VAE autoencoders come with controlled and regularized training to avoid overfitting as much as possible.

In these autoencoders, the encoder will output two vectors instead of one. These two vectors are:

*   A vector of means “mu”.
*   A vector of standard deviations “Sigma”.
*   These two vectors form random variables to form a stochastic output.

The VAEs can be used on non-trained example data to output precise outcomes. These are also mainly used to generate synthetic data which may be helpful in building advanced **generative adversarial networks** (**GAN**), like in speech, drawings, paintings, music, images, faces, etc.

# [12.8 Other autoencoders](#toc.xhtml#s263a)

Following are some of the recent autoencoders which are a little complex to understand but are gaining quick popularity:

*   Adversarial autoencoders
*   **Winner-take-all** (**WTA**) autoencoders
*   Contractive autoencoders

In the interest of this book, these are not described in detail, but to make the reader aware, they have been mentioned here.

# [12.9 Examples and samples](#toc.xhtml#s264a)

There are various applications of autoencoders. One of the programming examples is explained in detail with *Google Colab* in the earlier section for reference. The popular applications in which autoencoders can be used are as follows:

*   Noise reduction
*   Image reproduction
*   Dimensionality reduction
*   Feature extraction
*   Compression (few features instead of an image)
*   Anomaly detection (reproduced signal deviate from the actual signal)

# [Conclusion](#toc.xhtml#s265a)

Automatic feature extraction is crucial for the ML/DL models. With combinations of autoencoders and various other machine learning and deep learning algorithms, powerful models can be built for various purposes.

With recent developments and enhancements, autoencoders have become a powerful toolset to consider.

As explained earlier, AEs can be used for feature extraction, dimensionality reduction, creating synthetic data inputs, and so on., with these capabilities many futuristic AI/ML models or applications can be built.

In the next chapter, the applications of ML will be covered.

# [Points to remember](#toc.xhtml#s266a)

*   AEs are used for both dimensionality reduction and feature extraction.
*   AEs are a powerful tool if used with combinations of neural nets or other ML/DL algorithms.
*   AEs has been seen as the recently evolving field.
*   Many powerful applications can be built with combinations of various AEs and algorithms as explained.
*   There are many types of AEs that are available, based on the need of the hour, respective AEs can be chosen.
*   VAEs and denoising AEs are most popular recently.
*   GANs can be built using AEs.

# [Questions](#toc.xhtml#s267a)

1.  What is an autoencoder? What is its significance?
2.  What is “encoder”, “decoder”, and “coding” in AEs?
3.  How many types of AEs are discussed in this chapter?
4.  What are the applications and models where AEs can be used?
5.  What are the most popular AEs that were discussed here?
6.  Explain in simple terms the components of AEs.

# [Multiple choice questions](#toc.xhtml#s268a)

1.  **Choose the correct answer** 
    1.  AEs are used for feature extraction.
    2.  AEs are not used for dimensionality reduction.
    3.  AEs are complex to learn.
    4.  None of the above
2.  **Choose the correct answer** 
    1.  AEs contain complex models inside them.
    2.  AEs contain “encoder”, “decoder”, and “coding”.
    3.  AEs contain unwanted features in them.
    4.  None of the above
3.  **Choose the correct answer** 
    1.  AEs can be used in GAN’s building.
    2.  AEs cannot be used in AGNs.
    3.  AEs cannot be used in GAN.
    4.  None of the above
4.  **Choose the correct answer** 
    1.  VAE is not a type of autoencoder.
    2.  VAE cannot be an autoencoder.
    3.  VAE is a type of autoencoder.
    4.  None of the above
5.  **Choose the correct answer** 
    1.  None of the following options is correct.
    2.  Denoising autoencoder is not used for any purpose.
    3.  Denoising autoencoder is used to remove noise.
    4.  All the options are correct

# [Answers](#toc.xhtml#s269a)

1.  **a**
2.  **b**
3.  **a**
4.  **c**
5.  **c**

# [CHAPTER 13](#toc.xhtml#c13)

# [Applications of Machine Learning and Deep Learning](#toc.xhtml#c13)

Artificial intelligence models are increasingly used in business applications spanning telecommunications, consumer appliances, information technologies, healthcare, finance, defence, infrastructure, automotive, and automobiles. Healthcare applications include the classification of tumors into benign or malignant, staging of cancer, detection of pneumonia, etc. from the images captured from the modalities such as CT, X-Ray, MRI, and ultrasound. The other applications include gene editing and printing, drug discovery, and health records. Text and logo extraction from images are useful for archaeological and handwritten document analysis. The generative adversarial networks are used to generate super-resolution images. The usage of AI for text processing finds applications in different verticals of the industry such as banking & insurance, recommender systems, social media, and so on. The powerful prediction capability of machine learning algorithms is useful for stock market data analysis, weather forecasting, anomaly detection, machine fault predictions, and so on. Recommenders working on the user-specific and behavioral patterns are useful to suggest targeted advertisements, movies, image tagging, similar content over the search engines, and so on.

The sudden surge in usage may be attributed to the availability of hardware accelerators. They speed up the execution and support real-time decisions, reduced development cycle time due to the availability of the pre-trained models, reference code in the open-source, and so on. The accelerator platforms span **Field Programmable Gate Arrays** (**FPGA**), **Field programmable Analog Arrays** (**FPAA**), **Digital Signal Processors** (**DSP**), **Graphical Processing Unit** (**GPU** etc.). The training time has been reduced substantially allowing for the fine-tuning, configurations, and design multiple times in a short time.

# [Structure](#toc.xhtml#s270a)

In this chapter, we will discuss the following topics:

*   An overview of the applications of artificial intelligence
*   AI in technology domains 
    *   Telecommunications 
        *   Data traffic shaping & SLA
        *   Resource management
*   AI in enabling technologies 
    *   Vehicular traffic control
*   Device-specific Applications 
    *   Food recommender
*   Realization platform 
    *   FPGAs for Algorithm realization
*   AI in business solutions 
    *   AI for the digital economy
    *   AI for troubleshooting

# [Objectives](#toc.xhtml#s271a)

After studying this chapter, you should be able to:

*   Appreciate the usage of AI in the healthcare domain.
*   Get an overview of AI-based applications in the telecom domain.
*   Understand how AI has changed consumer applications.
*   Get to know the working of AI algorithms in the finance domain.
*   Know the benefits of using AI-based modules for transportation.
*   Understand the importance of AI in day-to-day life.
*   Use AI in customer solutions.

# [13.1 Introduction](#toc.xhtml#s272a)

The availability of hardware accelerators has taken the AI-based systems right into the user’s premises, i.e., to the source of the data. It enables the sensors and IoTs to acquire the right amount of data at the right time. Based on this, data decisions can be taken on the fly without the need of connecting to the cloud. On the other hand, in applications where a certain delay is tolerable, the models may be placed in the cloud and provided to a large number of users who can consume it as a service from anywhere and at any time.

# [13.2 Domain-specific applications](#toc.xhtml#s273a)

AI technologies are increasingly used for different applications spanning telecom, consumers, transportation, healthcare, etc. to solve complex business problems and automate the system. In addition to automation, the systems require real-time response achieved through the massive parallelism inherent to the AI systems.

# [13.2.1 Telecommunications](#toc.xhtml#s274a)

AI technologies have helped to develop a technique to address the growing demands of the internet, considering internet characteristics as an add-on for the existing infrastructure and provide predictive and preventive strategies. This is because the solution has to consider the statistical properties of the network, scalable, learn from experience, online and adaptive and finally work with the limited information:

![](images/Figure-13.1.jpg)

**Figure 13.1:** Resource allocations in telecom networks

*[Figure 13.1](#c13.xhtml#fig13_1)* shows the various schemes for resource allocation in a telecom network. Quite often allocation is made based on the network traffic status and traffic shaping is carried out accordingly. A significant part of the traffic falls under best effort reservation wherein the data sources are required to control their transmission rate to support a specified quality of service.

The traffic controller is expected to generate the best-predicted signal and use it for feedback control. A variant of **Random Early Detection** (**RED**) that provides the probability of packet loss in the buffers of the routers is popularly used as the control signal.

It helps to control the data transfer rate and reduce the congestion in the network simultaneously meeting the **Quality of Service** (**QoS**). *[Figure 13.2](#c13.xhtml#fig13_2)* shows the control signal computation in RED through the multi-layer perceptron:

![](images/Figure-13.2.jpg)

**Figure 13.2:** Control signal computation in RED

The probability of packet drop is helpful in providing resource allocations. Based on this value and its predicted versions, the data sources in the network can adapt the transmission rates to reduce congestion in the network and meet the delay and packet loss constraints.

The end-users are often directed to agree to a stipulated QoS available at some point in time before connectivity is provided. Accordingly, they can either opt for the service or wait until the network is capable of providing the required QoS.

The machine learning algorithm comprises of anomalies detection (i.e., potential slippage into QoS deterioration in the near future) based on the input patterns applied at that time.

The unsupervised learning algorithm is to be used for the categorization of the input pattern into the safe zone, the onset of deterioration (can come with N levels within), the deteriorating zone, and the QoS failure zone. The N value depends upon:

*   The number of distinct patterns detectable during model development.
*   How often the input patterns are applied, i.e., how often the customer call records are updated.

The Churn prediction network shown in *[figure 13.3](#c13.xhtml#fig13_3)* it comprises of customer data taken at timestamps such as 1 week, 3 weeks and 1 month and is ingested into the model. The hybrid model is used for model tuning parameters. The historical data such as CDR recharge specific to customer are made use.

![](images/Figure-13.3.jpg)

**Figure 13.3:** Churn prediction network

In *[figure 13.4](#c13.xhtml#fig13_4)*, the different databases required for churn prediction are detailed.

![](images/Figure-13.4.jpg)

**Figure 13.4:** Different databases required for prediction

The followings are the main databases used:

*   Customer details
*   Handset Details
*   Recharge data
*   Site location
*   Product Catalogue
*   Usage CDR

The response for different patterns, if the same action is taken for multiple patterns, may fall into the same cluster.

The N is to be kept configurable and tweaked during model development.

The working architecture of the pattern learning is shown in *[figure 13.5](#c13.xhtml#fig13_5)*. It consists of a QoS (Quality of Service) predictor and unsupervised learning model, clustering the data into the preceding groups. There are three candidates (widely quoted in the literature) for QoS prediction: **Random Neural network** (**RNN**), SVM-based predictor, and Adaptive Neuro-Fuzzy system. Based on the accuracies achieved and the nature of the data, one of them is to be used as the predictor model. For learning, both **Self Organising Map** (**SOM**) and **Adaptive Resonance Theory** (**ART**) architecture are to be tried during model development and the best one of them is to be used. The performance depends upon the number of patterns, the “*distance*” between the patterns, and so on.

During the field trial, the reinforced learning is to be used for fine-tuning. The classifier for QoS status is shown in *[figure 13.5](#c13.xhtml#fig13_5)*:

![](images/Figure-13.5.jpg)

**Figure 13.5:** QoS status classifier

The power of prediction enhances with the fine-grain definition of clusters, i.e., a slight change in the normal pattern (safe zone) has to put the input into the “*onset of deterioration*” zone providing ample time to respond. The following table shows indicative data (input) and the clustering action of the patterns. The data required for the development of the model is indicated in the table. The parameters shown here are indicative. Additional parameters may be required or may be used if available. In addition, up/downstream information is required as the QoS parameters will be different. The Template of the factorsencing QoS is shown in *[Table 13.1](#c13.xhtml#tab13_1)*:

![](images/p337.jpg)

**Table 13.1:** Factors influencing QoS parameter

The field trial is a crucial phase during which the algorithms will be subjected to rigorous testing. At least 2 handsets are to be used from the same place, targeting the same (video) URL. The proactive algorithms of QoS deterioration explained in this proposal are to cover the first handset while the second one is to be covered under the existing reactive algorithms. The (video) quality/SNR in the received data is to be compared to appreciate the deployment of the algorithms.

# [13.3 Technology specific applications](#toc.xhtml#s275a)

AI algorithms are often blended with advanced technologies such as IoT, chatbots, machine vision, robotics, and so on., to process the data. The traditional algorithm and hardware components are equipped with built-in intelligence to acquire processes, transfer the data and infer the results. The following is the detailed usage of Internet of Things (IoT) technologies:

Vehicular traffic control is a hot topic in smart city design. With the increase in the number of vehicles on road, the overall waiting time in front of the traffic signal has increased significantly. Quite often, the road turns empty once the traffic from a particular direction is cleared and the second wave of vehicles start pouring in. The objective of this work is to exploit the patterns in the traffic to reduce the waiting time. Feedback on the quantum of the traffic generated from a camera at the traffic signals is used to predict the traffic a few steps ahead of time and modulate the speed of the vehicles to minimize the waiting time near the traffic junctions. In order to support high priority vehicles such as ambulances, a priority index is assigned for the same.

Vehicular traffic control is a well-studied problem. Typically, neural networks are used to predict the quantum of the traffic from a particular direction and the traffic signal durations are set accordingly. It also provides input to vehicles to slow down if the traffic from that direction is getting clogged at the next signal and reduce the pileup. The probability distribution of vehicles crossing a point on the road/arrival rate and take different directions is important to clamp on the velocity and alter the traffic signal duration in real-time:

*   The speed of a bunch of vehicles are modulated (increase as well as decrease) based on the recommended speed displayed at regular intervals along the road for each category of the vehicle. Alternatively, the information can be made available on a subscription basis. In addition to the crossover rate of the vehicles, the temporal or spatial gap between the benches of the vehicles is assigned with weightage.
*   Priority index is assigned for a certain category of vehicles (for example, ambulance, fire engine, traffic police) to ensure a seamless transit across the signal and minimize the stranded time.
*   The predicted signals are subjected to a time shift considering the futuristic point of consumption (the time difference between prediction time and crossover time).

AI tools provide a mechanism to maintain zero or near zero waiting time for the signals at the traffic junctions. It also provides priority for the traffic from a particular direction when the vehicles are getting piled up at the junction or high priority vehicles such as ambulances, fire engines, etc., are approaching.

# [13.3.1. The working mechanism](#toc.xhtml#s276a)

The workflow is shown in *[figure 13.8](#c13.xhtml#fig13_8)*. The following steps get executed dynamically:

1.  A camera fixed at a traffic signal captures the number and type of the vehicles through image processing carried out on the cloud. Each type has a recommended speed to reduce the stranded time. A different speed can increase the same. For example, cars, bikes, bicycles, etc.
    
    The camera tells when the crossings (taking turns) in a particular direction starts, what is the duration of the green signal for traffic from a direction, and the time gap between consecutive green signals for the traffic from a direction. By knowing these values and the distance of a vehicle from the junction got from its GPS/cameras in the street, it should be possible to tell the velocity with which the vehicle has to travel so that it hits the green signal at the junction. The feedbacks to drivers are provided.
    
2.  Each category forms a bunch by the natural way of speed as shown in *[figure 13.6](#c13.xhtml#fig13_6)*, although it is not necessary to have a bunch with similar vehicles. A bicycle may find more than one bunch of bikes cross over by the time it reaches the signal.
    
    A vehicle can subscribe individually to the system to get its speed (or a set of speeds) so that the waiting time is zero or nearly zero.
    
3.  The time gap between the bunches from the same direction is computed to allocate this time for traffic from other directions.
    
    If the bunch is too big (can be due to the convergence of the heterogeneous vehicles), the vehicles may not crossover in one shot leading to maximum waiting for the leftover vehicles. This could have been avoided in two ways- by adaptively increasing the period for the green signal and by reducing the arrival velocity for leftover vehicles (or increase their velocity at the cost of the vehicles crossed over. This is possible by introducing the priorities further). Now, the probability that a vehicle gets stranded= position of the vehicle from the leading edge/max length of the bunch. The maximum length of the bunch is computed by knowing the speed of the vehicles and the duration of the on-time of signal. It is the probability that a vehicle has to wait for the green signal a second time to crossover:
    
    ![](images/Figure-13.6.jpg)
    
    **Figure 13.6:** Bunching of vehicles
    
    The speed depends on this probability. However, it is computed based on the current state of the traffic. So, it has to be predicted for the time of crossover.
    
4.  The out of bunch probability is predicted using a **Multilayer Perceptron** (**MLP**)
5.  This signal is time-shifted and used as a predictor signal so that it maps on to the time of arrival of the vehicle near the junction.
6.  Priority is assigned for a certain class of vehicles while crossing the signal. Such a bunch is given high priority and can take any velocity. The bunch is not made to wait. It is pulled some steps above in round-robin stack:
    
    ![](images/Figure-13.7.jpg)
    
    **Figure 13.7:** Velocity modulation
    

Vehicular traffic shaping brings in incremental gains such as reduced travel time and congestion. When feedback on the average speed to be maintained is provided to the vehicles, it brings in additional benefits such as reduced waiting time in front of the traffic signal, prioritization of a certain type of vehicles like ambulances, etc. and impart seamless travel experience:

![](images/Figure-13.8.jpg)

**Figure 13.8:** Workflow steps

This is computed by predicting the probability of a vehicle waiting in a traffic signal and time align the same. *[Figure 13.7](#c13.xhtml#fig13_7)* shows this velocity modulation scheme. A simple IoT camera installed at the traffic junction and a handful of algorithms running over the cloud can provide the “*zero (minimal) waiting*” service to the subscribing users to open up a new business model. The steps involved in the workflow are indicated in *[figure 13.8](#c13.xhtml#fig13_8).*

# [13.4 Device specific applications](#toc.xhtml#s277a)

AI algorithms can be used and developed by targeting a specific device. Choice of the algorithm depends upon the workflow, availability of the data, the hardware interfaces, and so on. The following example illustrates the usage of several algorithms in the realization of a food recommender device.

Overeating and starving are equally bad for health leading to chronic disorders. In order to prevent it on a day-to-day basis, a mechanism to alert the user on how much to eat from the items on the plate before the next intake would be helpful. It has to consider the space in the user’s stomach (including stretch), rate of digestion of different items on the plate in mixture considering the physical and emotional state of the user, and the time gap before the next intake.

The cognitive belt integrates the camera image of the food, the body/mind parameters (such as dryness, temperature, emotions…) and the rate of digestion (with the ultrasound sensor, loosening of belt, etc. and with deep learning over images). The system learns the same for a specific person over a period of time and is able to predict how long it would take for him to digest the food and how much of it gets into usable calories. It calls for three-way optimization considering the emptiness of the stomach, rate of digestion, and calorific values. Based on the ingredients of the food, it is classified into one of the categories like A, B, C, or D where, A represents the protein-rich food, B carbohydrate-rich food, C food rich in fat, and D representing the balanced mixture of all, considering the health conditions of the person.

The solution involves the following steps:

1.  **Prediction**
    
    Based on the ingredients of the food, it is classified into one of the categories like A, B, C, or D. An approximate classification of the food item is sufficient to start the prediction on how it would take to digest the food (or degree of the emptiness of the stomach).
    
2.  **Correction**
    
    The degree of emptiness is measured with the ultrasound belt that is used only for a short while to take a measurement and fine-tune the model. The frequency of the usage depends on the plurality of parameters like, how accurately the ingredients are identified, uniformity in the rate of digestion, etc. Once the sync up happens, as shown in *[figure 13.9](#c13.xhtml#fig13_9)*, the system predicts accurately. If the ingredients are not known in advance, a couple of sync-ups are required at regular intervals to predict further the type and quantum of food consumed. It is then added to the database for subsequent usage.
    

# [13.4.1 Feedback predictor model](#toc.xhtml#s278a)

The pre-existing models relating to food ingredients to the rate of emptiness are highly data-dependent. To make it person-dependent and (emotional) state-dependent, often tuning is required. A first-order feedback model provides a mechanism for tuning and accurate prediction as shown in *[figure 13.10](#c13.xhtml#fig13_10)*:

![](images/Figure-13.9.jpg)

**Figure 13.9:** Stomach emptiness prediction model

Taylor series expansion of *y(n+1)= f\[y(n)+a,b,c\]* where the terms a, b, and c are to be sync-up periodically. The bottom line is, present prediction depends on the previous values:

![](images/Figure-13.10.jpg)

**Figure 13.10:** Prediction with feedback

The emptiness measured from the belt is used for seeding the prediction. Subsequently, it is used by delaying the predicted values. Periodic sync up ensures better accuracies. The following steps are involved in the working of the device:

1.  **Database initialization**:
    
    It comprises the data on the rate of digestion of the commonly used food items for the reference of a healthy adult. The data is available in the public domain. It is re-written into the following format. *[Table 13.2](#c13.xhtml#tab13_2)* captures the fields indicating digestion rate for different groups of users:
    
     
    | **Group ID** || **Composition bin** || **Digestion rate** |
    | --- | --- | --- |
    | A || Cereals || 2 hrs |
    
    **Table 13.2:** Digestion Rate
    
    The specific values for the individuals would be filled in/updated over a period of time after observing the rate of emptying of the stomach when a mixture of these items is consumed. Images and descriptions of common food items are stored as indicated in *[table 13.3](#c13.xhtml#tab13_3)*:
    
     
    | **Image** || **Name** || **Composition bin** |
    | --- | --- | --- |
    | URL of the image || Pizza || cereals |
    
    **Table 13.3:** Image database
    
    Calorific values of each category are also available as metadata.
    
2.  **Detection of the emptiness of stomach**
    
    This is the first step during the usage of the device. The degree of emptiness is detected with an ultrasound sensor.
    
    The quantum of food consumed is expected to be proportional to the emptiness. Say, 80% full. The volume is computed from the image. Scan happens with the click of the control button in the GUI of the smartphone.
    
3.  **Identification of food items to consume**
    
    Once the food items to be consumed are identified and placed in the appropriate composition bin, it would be possible to compute the approximate time required for the digestion. The identification happens in many ways:
    
    1.  The user takes a snapshot of the menu containing the images of the food to be served along with the textual description if any. If the image or description is not matching with the database entries, it goes to step b.
    2.  Here, the food to be served is spread on the plate and the snapshot is taken. If the image or textual description of the items is not matching, it goes to step c.
    3.  The user can directly enter the name of the menu item that the system does not know and if he knows. The communication happens through AR as explained in step 6. If the user does not know, it goes to step d.
    4.  The user can get the name of the indicated item or its bit type (and its major ingredient details, for example, pizza-> bleached wheat flour, cheese and vegetable toppings). If that is not feasible, it goes to step e.
    5.  System notes down the image of the unknown food item (and tags it when the user gets the name sometime in future), warns the user that the accuracy in computations would be less (as it would be excluded) and advise him to eat less of it.
4.  **Determination of the quantity of each item to consume**
    
    The quantity of each component of the menu to be consumed depends upon several factors:
    
    *   The empty volume of the stomach
    *   Rate of digestion of each category
    *   Combination of categories (for example, pizza & sauce; sauce alone cannot be consumed in abundance) and their relative proportions. Generally, this is taken care of on the plate.
    *   User’s like/dislike of certain items
    *   User’s health conditions and chronic disorders (for example, diabetic)
    *   User’s food habits (for example, the user does not find time to eat in the afternoons, food is expected to stay for long in the stomach).
    *   Calorie requirement/lifestyle
    *   The calorific value of each category (got from the tables in step 1)
    
    The quantity of each item would be the weighted sum of these factors (for example, weight =0 for health conditions for the consumption of rice if the person is non-diabetic).
    
5.  **Determination of rate of digestion of individual items**
    
    The rate of digestion is person-specific although the table in step 1 provides a generic value. From the rate of digestion of the mixture, the rate of digestion of individual categories can be computed using multiple observations. This is feasible since the amount of food consumed under each category is known.
    
6.  **Interaction with the user**
    
    The user interacts with the system through a conversation engine to provide the names of the ingredients in the menu and through AR to identify which item the system is talking about.
    
    **Advantages of AI-based solution:**
    
    *   The belt learns the digestive physiology of individuals.
    *   Start predicting after how long his stomach would be empty.
    *   Can recommend how much the person can eat in total considering the digestive rate, calories required, and the health status.
    *   Deployment/design of the probe.

# [13.5 Platform-specific applications](#toc.xhtml#s279a)

Execution platforms have played a decisive role in the evolution of AI technologies. Although AI technologies are there for the past 60 years, it took several decades to take it to business solutions. This is partly because of the availability of the right platforms, both hardware and software, to realize the algorithms in real-time. Numerous alternatives in the design flow such as FPGA, ASIC, DSPs, accelerators, neuromorphic chips, hierarchical temporal memories etc. have been developed over a period of time to run the algorithms successfully.

Training of CNN/LSTM on the FPGA to reduce the overall time can be a good research problem demanding a deep understanding of the CNN/LSTM layers and a fair knowledge of the FPGAs.

FPGAS are generally used during deployment, taking the weights (and pruning the network to make it faster) from training on GPU. Pruning is another area of research. The speed of GPUs is higher than those of FPGAs (although the power consumption of FPGAs is 10 times lesser. For the same reason, cloud service providers are using FPGA stack in the datacenters, opening up enough scope for research. Interestingly, the speeds of some of the layers of CNN on FPGA are much faster than (10 times) the corresponding layers on GPU. However, the other layers demand huge data transactions/computations making the overall speed leaser. In all other aspects (accuracy, price, support of toolchain- i.e., programming in Python/Tensor flow models) the two methodologies are almost the same.

GPUs enable parallelism in the execution, unlike the conventional CPUs where the instructions are executed sequentially. It goes well with the parallel architecture of artificial neural networks. Several neurons may be realized at a time. The GPUs typically have multiple cores for processing the data. Over the GPUs, array operations show a significant reduction in the computation time. The two types of parallelization mechanisms in practice are- data parallelization and task parallelization. In data parallelization, the same task can run over different data streams on different cores of the processor. For example, in parallel search, the database can be split into multiple chunks over which the search can be carried out parallel. The result from each of the cores gets merged at the end. In task parallelization, distinct tasks run over the different cores. A typical example is the filter operation over the image, used in Convolutional Neural Network. While horizontal filtering can happen over one of the cores, vertical or diagonal filtering can happen over another core for the same image.

This type of parallelization is important to generate real-time responses. For example, in an edge device connected to a manufacturing plant. Numerous IoT devices generate the data in real-time indicating the status of the process in a manufacturing plant. This data gets processed by the edge server as it incurs huge delays to churn over the cloud. Another example is an autonomous vehicle. The presence of obstacles or interpretation of traffic signboards should happen in near real-time. A powerful GPU or accelerator on the vehicle is required to execute the AI and ML algorithms.

DSP processors and FPGAs with hardware accelerators implemented as ASIC cores will be helpful to reduce the processing time and at the same time act as a self-contained system providing adequate program and data memories. For example, the different filters used in CNN (AlexNet uses 96 filters in the first layer) can be implemented in ASIC as a configurable array of filters.

It will be useful if the speed of execution is made faster with smart changes in the execution architecture of CNN/ LSTM (for example, the convolution of an image with a filter can be split into a butterfly structure reducing the complexity by Log(N). One of the applications with such changes is for data transactions and reduction in overheads. Real-time face detection and tracking involve huge computations. Reduction in the time complexity through the accelerators will be helpful especially when the computational power is low, as in a mobile phone.

# [13.6 Solution-specific application](#toc.xhtml#s280a)

It takes a combination of algorithms to realize a business solution. First, the problem is split into multiple subunits each of which is realized separately. These solutions have enabled the digital economy by taking the applications to the end-user, resulting in significant savings on the workforce, investment apart from fast and flawless executions. The following examples illustrate the usage of these technologies in the acceleration of the processes:

# [13.6.1 Contextual advice](#toc.xhtml#s281a)

When a user is referring to an online technical document or product manual, he may get stuck at some point due to the lack of clarity for him or find it difficult to understand/follow the content. If there is a provision, he can ask for a better illustration/simple explanation online. This calls for an explicit dialog taking his time. Quite often, such an interactive online help or expert suggestion may not be available always for all the content. In the literature, not many ready to use solutions are available to estimate the degree of understanding of a document implicitly and provide adequate support dynamically.

An AI system proposed here observes the user behavior while he reads the document and gets implicit feedback on the rate of reading if the user finds any difficulty in comprehending.

The system may be used where the user reads stories, jokes, speeches, product manuals, technical documents, etc. online and understands (and simplified information provided when the user is stuck based on the rate of reading). The solution involves the following steps:

1.  **Creation of helping content for different levels of difficulty:**
    
    Based on the difficulty level of the user as seen by the system, appropriate supporting material may be provided contextually. The content to be provided is organized hierarchically into multiple levels of difficulty.
    
2.  **Creation of reading profile for the piece of content**:
    
    It involves the cumulative reading time graph from the start of the content till the end. While a uniform speed is assumed, it varied from sentence to sentence (or a part of it) as the user starts to read. Some of the sentences referring to equations, diagrams, and graphs need more time for reading (& understanding simultaneously).
    
3.  **Elimination of spurious eye movements:**
    
    This is required to eliminate involuntary noise getting into the system. A timing threshold is set to eliminate the movements or fluctuations faster than that.
    
4.  **Deletion of random (jump) reading by the user:**
    
    This abrupt jump in the spatial content based on the mood or interest level of the user (the content catching the user’s eyes) may be treated as the beginning of another reading session.
    
5.  **Estimation of the difficulty level of user**
    
    Based on the back-and-forth movements, time spent over a sentence, natural pause, and deep thinking by the user that is not treated as difficult to understand, a parameter is generated using a regression network.
    
6.  **Runtime help based on user behavior.**
    
    The speed of reading of the user is computed adaptively during run time. Based on that, the time required to read each sentence is scaled accordingly. If the user is spending too much time traversing a sentence or moving back and forth, more details are provided on the same. Depending on how the user takes this help (reads it fully or not, come back to original content and proceeds or not), further help is provided.
    

*[Figure 13.11](#c13.xhtml#fig13_11)* shows how the response generated by the system is influenced by the user’s state for a given question:

![](images/Figure-13.11.jpg)

**Figure 13.11:** Response generation based on user state

The advantages of AI solution are as follows:

*   Take implicit feedback from the user.
*   In-time and contextual help; only if it is required.
*   Adapts to any reader or content.

# [13.6.2. Context-based search](#toc.xhtml#s282a)

Search engines provide the required information based on the keywords. An image-based search engine can ingest the image objects as well. The search key is compared with the metadata of the content to retrieve the information having these keywords. The comparison is performed semantically using mechanisms such as Topic Modelling, Linear Dirchlet Algorithm (LDA), and so on.

Conventionally, the matching of words or features is the only criteria for extracting/retrieving the content by search engines. Consequently, they do not consider the crucial information in the context. Although the search engines consider the previous retrieval patterns (browser history), they do not consider the context of the search, i.e., a scenario that spreads over time. Instead, the focus is on the instantaneous matching of contents and no relation among the matched content.

The conventional search engines are keyword-based and provide content matching at that particular instance and do not consider temporal or contextual information. Thus, it leads to an erroneous interpretation where the background information is left out. The matching may be correct or incorrect. It calls for a temporally consistent search engine that includes the context information. Most of the existing search engines consider only the browsing history but not the context or circumstance of the data being searched. A holistic view of the content is required before the search, which is addressed through AI-based techniques. For example, in the search of an emotional scene, if the user laughs in some of the video frames, the search engine takes the scene as happy. The person in the scene may be laughing to express the frustration sarcastically, commenting as “*I spent my whole life at your service; you repaid it with a pound of bread*”. This does not mean the person is happy. The context of the expression is required to understand the situation better and then consider it as the search result.

The search mechanisms rely on the keywords alone and do not consider how it is evolved (i.e., came at that point in document space) or what it leads to. Because of the same, crucial information among the interaction or actions of the objects in a scene are missing. Further, the output results rendered to the user scatters across the document space and are treated as disjoint. These results are to be brought together and stitched together meaningfully and contextually to provide meaningful search results to the user. Further, there is no ranking system based on the contextual stitch.

The AI-based approach is used for content extraction based on contextual relevance using a content search engine. The context-based search is shown in *[figure 13.12](#c13.xhtml#fig13_12)*:

![](images/Figure-13.12.jpg)

**Figure 13.12:** Context based search engine

Here, the search results are generated based on the context of the query as well as the historical information (i.e., the transactional data). The mechanism considers the context discontinuities (i.e., multiple contexts derived from the historical data) as well as the continuity of the context with the historical data to decide on concatenating the search results scattered across the data repository of the content provider. A reinforcement learning mechanism may be used to trace back the shortest path responsible for providing better and efficient search results for the end-user. It includes three main components as detailed here for a video search engine:

*   **Context detection**: Here, the context in the video is detected. It is accomplished using the context detection unit and context change indication unit.
*   **Context retention**: The right context is retained with possible influence to a particular class. It is achieved using the search context extraction unit.
*   **Context usage**: This part uses the context information for classification of the content and realized through the shortest path identification unit.

The system includes a couple of key components to realize the AI-based solution. The AI components are added over and above the existing search engine or browsers. Initially, the search engine receives the search query provided by the user. The search engine runs over the proposed system providing the matching content from the data repository. It sends the received search query to a controller unit (for search context extraction). The controller unit infers over this fetched content and analyses the temporal relations before providing the results for the matching keywords.

AI controller unit performs search context extraction, shortest path identification, and result organization before rendering. The search context extraction happens over the user search query from the search engine. After receiving the search query, a search context extraction unit is configured to translate the same into a contextual query. It is translated into the contextual query based on the interactions among the objects in the search result as captured in a context table. The search context extraction unit is configured to generate a search key based on the user-provided search query. The search context extraction unit is configured to send the context information relevant for the search and the generated search key for the shortest path identification.

To compute the shortest path, the context information relevant for the search is received from the search context extraction. The search key is applied over the data repository the system is configured to extract the search results. The shortest path identification involves the ranking of the search results based on the contextual proximities and weights. Relevance-based contextual results are received and the result is organized. The system receives the user feedback for the reinforcement learning to fine-tune the search results.

After receiving the video data, the system detects and separates the context in the data. Once the context in the data is detected and separated, a context table is generated. Here, initially, all the objects in a scene are detected. Once the objects in the scene are detected, their interactions are captured in the form of a table. Next, the system detects the precise change in the points where the context is switched over in the data. The timings related to the context switch are stored as a start time and an end time of the interaction. It is required to capture each set of interactions.

In a given image, interacting objects are detected to capture the dependency. The dependency among the objects can be as actions and interactions that get into the context table.

Content is organized into multiple contexts based on the change in the actions and interactions among the objects or characters in the scene marking the starting point and end-point of the context. The nature of interaction among the objects is to be identified.

The context is generated by including the interactions around the main or attention object. It includes the attributes of the objects that take part in the interaction between the objects in the video scene. The change in the context within the duration of interactions is detected. It is then stored in the data repository. Here, the change in the interacting objects in the scene or change in the nature of interaction among the existing objects is detected.

After receiving the search query, the system is configured to translate the same into a contextual query. It is translated into the contextual query based on the interactions among the objects in the search result. The search key is generated based on the user-provided search query. The keywords are related through the right choice of Boolean relation. The shortest path identification helps to process the context information relevant for the search.

Different contexts relevant for the response are weighted and a decision is taken on retaining or discharging the context in the search result. The context key from the user is applied over the data repository to obtain several matching results. Reinforcement learning is used to identify the shortest path.

The search results or set of contexts are concatenated before rendering. If the context is not contiguous, they are extrapolated on either side to make them meaningful. It is performed for each of the search results.

**AI advantages:**

*   It provides a similar context of a search query.
*   Better coordination of action and context.
*   Search results are linked to historical background. Avoids results based on momentary data.
*   Results are stable as they make use of large observations, linked patterns.
*   The search result contains the right portions of the content concatenated.

# [Conclusion](#toc.xhtml#s283a)

Artificial intelligence supports a large number of applications spanning various technologies and business verticals. The nature of the problem in these domains is distinct and unique prompting further research in the architecture and algorithms. These algorithms are quite often comprehendible and come with a reference implementation to take as the base version. As a result, numerous development platforms, solution architectures, and business models with AI have emerged around these applications. This is further accelerated with the advancements in other technologies such as quantum computing as detailed in the next chapter.

# [Points to remember](#toc.xhtml#s284a)

*   Evolution of AI algorithms is closely related to the application domains.
*   Evolving hardware and software platforms have enabled numerous business solutions to use an AI-based approach.
*   In addition to the domain, emerging technologies have provided a right match to the AI algorithms with the business problems.
*   Often, AI algorithms sit over the legacy solutions as differentiators providing execution speed and portability.
*   AI algorithms have paved a way for automation.
*   With the adoption of AI technologies, the digital economy has increased multifold.

# [Questions](#toc.xhtml#s285a)

1.  What are the application domains benefited from AI technologies?
2.  Which emerging technologies work closely with AI?
3.  How does the digital economy use AI algorithms?
4.  What is the role of AI in automation?
5.  How do the advancements in hardware platforms affect the spread of AI technologies?

# [Multiple choice questions](#toc.xhtml#s286a)

1.  **Choose the correct answer** 
    1.  AI is reaching the masses because it is cheaper.
    2.  AI search has started recently.
    3.  AI is increasingly used nowadays because it is easily realizable.
    4.  AI usage is confined to robotics and satellite data processing.
2.  **Choose the correct answer** 
    1.  AI algorithms can be used only for prediction.
    2.  AI algorithms are portable.
    3.  Ai algorithms can be trained only on the cloud.
    4.  Machines learn exactly like human beings.
3.  **Choose the correct answer** 
    1.  IoTs can use AI technologies.
    2.  AI replaces human intelligence.
    3.  AI algorithms can run only on high-end servers.
    4.  AI systems are to be trained every day as they forget learning.

# [Answers](#toc.xhtml#s287a)

1.  **c**
2.  **b**
3.  **a**

# [CHAPTER 14](#toc.xhtml#c14)

# [Emerging and Future Technologies](#toc.xhtml#c14)

Since the last decade, **Artificial Intelligence** (**AI**) has emerged from the shadows of history and turned into a reality. This is made possible due to the advancements in the other enabling technologies. Although AI was there much before, it was difficult to implement the algorithms over the available resources. Enormous computing power and time were required to implement even the simplest algorithms due to their iterative nature and the parallel architectures of the AI hardware. As a result, AI applications were confined to offline processing. Only a few departments such as the space agency, energy, and manufacturing industries could afford to use the AI technologies for churning the large data sets. However, emerging technologies such as cloud computing and 4G turned out to be game-changers. While cloud computing provided the required infrastructure to train and run the AI algorithms, the much-required fast connectivity was provided by the 4G networks. Technology has advanced further to provide much better infrastructure so that the AI algorithms can be trained at the customer premises in part and over the cloud for the rest of the cycle. In future, connectivity will not be an issue to get the real or near real-time response from the algorithms residing over the cloud.

# [Structure](#toc.xhtml#s288a)

In this chapter, we will discuss the following topics:

*   Introduction to the next-generation technologies
*   Internet of Things 
    *   What are the problems with IoTs?
    *   Cognitive IoTs
*   Cloud computing 
    *   AI for Cloud resource management
*   5G Networks 
    *   AI to meet 5G requirements
*   Quantum computing 
    *   AI algorithms over quantum computer
*   Conversation systems 
    *   AI-based conversation systems

# [Objectives](#toc.xhtml#s289a)

After studying this chapter, you should be able to:

*   Appreciate the usage of AI for processing IoT data.
*   Understand the role of AI in resolving the issues with cloud computing.
*   Appreciate the need for 5G in accelerating the AI proliferation.
*   Appreciate the usage of quantum computers for executing the AI algorithms.
*   Learn the design of dialog systems using AI algorithms.

# [14.1 Introduction to next-generation technologies](#toc.xhtml#s290a)

Artificial intelligence systems have evolved based on the available computational power and memory to execute the algorithms. The advancements in the computing platforms through the cloud and quantum computing, the high-speed connectivity through 5G networks, and so on., have taken the AI execution workflow to the next level. Conversely, the previously mentioned technologies have been benefitted through AI technologies.

# [14.2 Internet of Things](#toc.xhtml#s291a)

**Internet of things** (**IoT**) is an upcoming technology that is interesting and useful for a wide spectrum of applications. Data transfer from an IoT device over a wireless channel suffers from the issues of fading and multi-path that becomes severe if not handled at the design stage. Simulation of this wireless network of IoT devices (and with base stations) is often required to get a better insight into the problems. The design parameters may be fine-tuned for optimal performance.

The method to address the design issues uses the Recurrent Neural Network to simulate the end-to-end data transfer over the wireless channel. The parameters of the neural network are mapped onto the weights and order of the neural network. The neural network can be a part of the actual design, controlling the factors that result in fading and multi-path effect. It has self-learning components for the adaptive modeling of the data transfer from the IoT devices.

Today, there is a plethora of devices over and around the body of a person providing a lot of data on the health status and enabling multiple applications in real-time. The ecosystem of household IoT systems such as device control through the cloud is shown in *[figure 14.1](#c14.xhtml#fig14_1)*. While the devices talk to each other and work in tandem in a limited sense, they are still loosely coupled in general. Also, the interaction is static and does not depend upon the dynamics of the user associated with them. For example, the temperature sensor on the body of a person and the IoT that switches on a fan do not talk to each other. Although the user is feeling hot, automatic switch-on of the fan through the IoT does not happen:

![](images/Figure-14.1.jpg)

**Figure 14.1:** IoT ecosystem

The solution spans triggering of the IoTs based on historical data and context, i.e., if a person took a brisk walk (sensed through accelerometer), it triggers the blood pressure sensor, heartbeat sensor, and so on. Based on the outcome, it triggers the Holter ECG measurement. It also gets the emotion detection to check if he had a heated argument. These devices are to be triggered in a sequence (or parallel as appropriate) on their own at the right time, based on the common goal and then take a consolidated decision. The decision is taken through the AI components.

# [14.2.1 IoT issues](#toc.xhtml#s292a)

Statistical analysis of the data originating from the IoT sensors provides important information on the transactions happening over the internet. It provides ample time for pressing the right type of resources for service to handle these transactions. The various design issues associated with IoTs are given in *[figure 14.2](#c14.xhtml#fig14_2)* and further discussed in detail:

![](images/Figure-14.2.jpg)

**Figure 14.2:** IoT issues

Each of the problems mentioned in the preceding figure is addressed based on the prediction technique. The prediction can be in the form of volume of the data directed towards the router or probability of a packet drop, and so on. The various factors affecting the offloading decision are shown in *[figure 14.3](#c14.xhtml#fig14_3)*:

![](images/Figure-14.3.jpg)

**Figure 14.3:** MLP architecture

Most of the connectivity issues would get resolved with traffic prediction and shaping. The resources generating larger data such as video cameras are asked to reduce the data rate when the network is getting choked. It happens on top of pressing the additional resources for cloud services. The low-priority data sources are identified based on the statistical analysis and are assigned with a lesser bandwidth when there is congestion in the network.

Process offloading from an IoT onto a nearby fog or edge server is a major issue. The right amount of data needs to be transferred at the appropriate time. An MLP-based architecture for this decision making is shown here.

The processing and data issues are reduced by analyzing the data at the place of origin and sending the final or partial results over the cloud. It also reduces the load on the network. The cloud infrastructure will get strengthened with quantum computing and spintronic memories, virtually providing unlimited computing and storage power.

In order to save power, the IoT sensors are to capture the data only when it is required, for example, the surveillance camera can start taking snapshots at a higher frequency only when an object is moving in front of it. Hence, it requires object tracking algorithms working in conjunction with energy optimization. In the normal mode, the frame rate and hence, the computational power required to process can be very small. Local harvesting of the energy with a stray electromagnetic field is sufficient to drive the micro and nanoscale circuitry in the sensors. When they are mounted on vibrating machines, the required electricity to power them up can be generated through piezoelectric effect.

# [14.3 Cloud computing](#toc.xhtml#s293a)

Data analytics is an integral part of an organization spanning the collection, processing, and rendering of the results. The processing of data involves a good number of algorithms. It encompasses pattern recognition in the data, clustering & classification, association of the data, and so on. If the data size is too large, it calls for a systematic breakup, processing, and then the fusion of the results. This step involves big data analytics, making use of the machine learning paradigms. The processed data is to be carefully analyzed and linked to the problem at hand, before rendering it to the end-user.

A new wave of tools and techniques are coming up to address the data analytics in the industry, considering and exploiting the ever-increasing data size. They predominantly make use of machine learning algorithms.

Machine learning algorithms provide the required intelligence to handle the same in a constrained time, providing meaningful inferences. Quite often, these algorithms are deployed over the cloud to support real-time inferencing of the data processing catering for a large number of users.

With the increased usage of the cloud for various applications, more and more applications are deployed over the internet today. The usage of these applications needs to adhere to **service level agreement** (**SLAs**) including the real-time **quality of service** (**QoS**) constraints. The organization of the application modules in optimal chunks supports a complete task under the SaaS or IaaS paradigm.

AI algorithms are used to provide a detailed analysis of the software organization over the cloud and the associated benefits. Several applications App1 to AppN are considered. These software applications work in sequence to realize a business solution, i.e., the output of application1 (App1) can be the input for application2 (App2), and so on. They are placed over the cloud as indicated in *[figure 14.4](#c14.xhtml#fig14_4)*. It encompasses the adaptive rendering of the resources to realize various service models over the cloud with an assured QoS. In addition, the hierarchical organization is scalable catering to a variety of customers. Each level of the organization provides a different degree of services. The levels are to be carved out before the deployment of the cloud service. The demand for these modules during the runtime to meet a given **Quality of Service** (**QoS**) is decided by the way of bundling of the software modules at each level.

The requirement to support a variety of users concurrently with scalability calls for optimal usage of the APIs over the network. Hence, it needs an efficient organization of the software modules so that maximal utilization of the same happens in a given time:

![](images/Figure-14.4.jpg)

**Figure 14.4:** Cloud architecture

The advantages of hosting ERP software over the cloud get masked by the associated issues unless they are addressed specifically. A host of issues that scale up with the software complexity and the number of users is shown in *[figure 14.5](#c14.xhtml#fig14_5)*.

It includes a large (monolithic) application object (App), a user request for the apps in bursts, support for the scalability of the resources with an increase in the number of users, under and over-utilization of the available resources and support for the prioritization of different classes of the users seeking these apps:

![](images/Figure-14.5.jpg)

**Figure 14.5:** Issues with the software over the cloud

Each of the preceding issues calls for an appropriate mechanism for the resolution as indicated in *[figure 14.6](#c14.xhtml#fig14_6)*. The monolithic objects that consume a huge chunk of (run time) memory need to be partitioned into smaller chunks. The burst of user requests may be handled by modeling the same as a fractal process.

The priorities of different users in the utilization of cloud apps can be addressed by providing service differentiation. The cloud resources can be effectively used by pressing traffic shapers into service. Finally, the service can be made scalable by predicting the quantum of the traffic in advance.

Instead of hosting the software as a monolithic chunk, it may be split into a good number of chunks, each providing an independent service. Based on the needs of the application running over the cloud, a couple of these chunks are to be skipped. In addition, the chunks taking more time or called quite often or visited by more applications are to be replicated more:

![](images/Figure-14.6.jpg)

**Figure 14.6:** Solution for the software issues over the cloud

*[Figure 14.7](#c14.xhtml#fig14_7)* shows the architecture with partitioned software. The Apps APPa and APPb are accessed in sequence. An optimal partition is characterized by a couple of points:

*   The modules are to be self-contained catering to a specific application when consumed.
*   Should be available in multiple abstractions with distinct privilege levels, supporting multiple platforms, SLAs, QoS, and so on.
    
    ![](images/Figure-14.7.jpg)
    
    **Figure 14.7:** Cloud with partitioned software
    

*[Figure 14.8](#c14.xhtml#fig14_8)* shows modules in the cloud accessing other modules. Enterprises typically follow the “*one size fits for all*” approach for **service level agreement** (**SLA**) resulting in increased expenses and loss of **Return on Investment** (**RoI**). However, the organization of the software into modules over the cloud enables focused attention for the critical parts of the resources and wide options for the SLA based on the nature of the software module and the calling application. After 99.999% level, the cost required to achieve further efficiency increases exponentially:

![](images/Figure-14.8.jpg)

**Figure 14.8:** Modules over cloud accessing other modules

The hierarchical modular approach comes with additional advantages. Firstly, the degree of security required by the different portions of the software is different. Modularization allows sensitive data/code to be collected and placed in one location and provides additional protection through encryption. If the code has generic personal information data based on region, security can be built in accordingly only for this part of the code:

![](images/Figure-14.9.jpg)

**Figure 14.9:** Hierarchical organization

Secondly, the maintainability of the software would be easy if it is modularized. The frequently changing code has to be separated into a distinct module.

Thirdly, the role-based object control. Here, individual access is provided to the system objects based on the identity enforced with the login credentials.

Finally, the energy-intensive modules may be physically placed on the same server mounted with the heatsinks as appropriate.

The penalty to be paid for these benefits and RoI is not small. The cloud has to handle increased traffic across the different modules satisfying the overall SLA. At the application level, it boils down to providing different UIs for different users, enhancing the user experience.

*[Figure 14.9](#c14.xhtml#fig14_9)* shows an instance of the hierarchical organization of the software to cater for different users. It supports multiple versions of the software, applications, platforms and even multiple ways of partition of the software App. While a high-priority application or user can hold a large single piece of the software and the resources to execute it, the fragmented version of the same software would be provided to a lower-priority user who needs to release the resources during switchover across the fragments. The priority gets decided as a part of the SLA, nature of the application, available resources, and so on., and dynamically decided by an AI algorithm.

The hierarchy of modules takes care of the scaling of the cloud by providing some (appropriate) pieces of the software for execution. A carefully partitioned software can handle bursty traffic by providing smaller chunks of application during the burst so that the resources get freed intermittently. This arrangement helps in better traffic shaping (drop off the resources for a short while when the queue is full) and predictability over a reasonable time (till all the requests get cleared).

Hierarchical organization of application software over the cloud supports dynamic allocation of the resources for optimal utilization. It caters for multiple classes of customers seeking cloud applications. In addition, optimal partitioning of the modules over the cloud makes it easy to meet the agreed SLA.

AI is increasingly used for load prediction in data centres. For example, heterogeneous traffic can be predicted from the time series of traffic arrival Prediction is done 30 minutes ahead in classical implementation. A 7% increase in network throughput and an 18% reduction of processing resources is observed.

AI applications are increasingly deployed over the cloud for ease of access and maintenance. It is possible to train the models over the cloud making use of the hardware platform which is otherwise not possible over local machines. Alternatively, trained modules are readily available over the cloud for applications such as object recognition can be used.

# [14.4 5G Networks](#toc.xhtml#s294a)

The framework of Software Defined Network and virtualization are the two pillars of 5G networking technology. They support the deployment of heterogeneous services that demand different amounts of resources. The need for resources varies as time progresses, as in **augmented reality** (**AR**) based application. It affects both static and dynamic resource allocations.

Although the technology has solved several problems in connectivity, it brings in a new set of complexities and requirements as detailed in *[figure 14.10](#c14.xhtml#fig14_10)*:

![](images/Figure-14.10.jpg)

**Figure 14.10:** Requirements of 5G

The connectivity requirements are highlighted in the following *[Table 14.1](#c14.xhtml#tab14_1)*. The mechanism for achieving the same are provided:

 
| **Sr. no.** || **Requirement** || **Mechanism to meet the requirement** |
| --- | --- | --- |
| **1** || 1-10 Gbps connections to end points in the field || MIMO |
| **2** || 1 millisecond end-to-end round trip delay (latency) || fog,/edge/cloudlet |
| **3** || 1000x bandwidth per unit area || Millimeter waves to provide more bits per waveform |
| **4** || 10-100x number of connected devices || dependent upon RAT, including 2G, 3G, 4G, Wi-Fi, Bluetooth |
| **5** || (Perception of) 99.999% availability || Handover to Heterogeneous network, micro antennas indoor, location-based handover |
| **6** || (Perception of) 100% coverage || Beam shaping |
| **7** || 90% reduction in network energy usage || Directional beam |
| **8** || Up to ten-year battery life for low power, machine-type devices || Power harvesting |

**Table 14.1:** 5G requirements

In order to support the heterogeneous networks, the network is fragmented into slices. Allocation and management of resources among the slices involve adaptive decision making from the supporting AI systems.

Heterogeneous traffic can be predicted using LSTM. Network functions are offloaded to general processing platforms through **network function virtualization** (**NFV**). CNNs help to detect anomaly/abnormal activities.

The contribution of AI is the dynamic resource management among the network slices. It happens by predicting the resources required to support the traffic well ahead of time. As a result, it would be possible to provide the agreed QoS with ease.

Resource allocation based on the prediction of the traffic in the data network is addressed through a deep learning network. For example, an AI-based congestion control mechanism considers the components of 5G architecture while predicting the traffic and the correction mechanisms are treated in conjunction with closed feedback as detailed here.

The contention for resources is notified to the sources of the data. However, it takes a while for the sources to respond, during which the dynamics of the network changes considerably, resulting in a buffer overflow, delays, and so on. This problem can be proactively eliminated by predicting these scenarios well in advance and notifying the data sources providing them ample time to respond if AI-based predictions are used.

# [14.4.1 Resource management in 5G](#toc.xhtml#s295a)

The 5G network standard considers supporting a wide variety of services. In 5G architecture, each service gets a dedicated slice comprising of a subset of network resources. Thus, the need for having a dedicated network even for small data rate services is eliminated. Varied network slices would be provided based on the type of the service.

The 5G **NOvel Radio Multiservice Adaptive network** (**NORMA**) architecture provides a plethora of functional blocks for the allocation of the resources and their sharing among the slices. The architecture detailed here interacts directly with two of the blocks for resource management. A brief description of their functionalities is provided as follows:

1.  **SDM-C**
    
    This functional module arms the system with self-organizing capabilities, scheduling control, radio resource control, and so on. It makes the underlying hardware resources transparent to the other layers and utilizes the same programmatically.
    
2.  **SDM-X**
    
    This functional block is responsible for resource sharing among the slices. The resources include the spectrum and the hardware components. Resource control happens through a common entity.
    

The predictor of resources is implemented through a **Recurrent neural network** (**RNN**).

The simplified model is shown in *[figure 14.11](#c14.xhtml#fig14_11).* Here, the output of the time series predictor is used as additional inputs. A **multilayer perceptron** (**MLP**) deep learning model with one hidden layer is used for the prediction of the packet drop probability from the buffer. This signal is communicated to the data sources for controlling the rate of data transmission. It provides ample time for optimal resource allocations:

![](images/Figure-14.11.jpg)

**Figure 14.11:** MLP with feedback

The predicted signal would provide insights on two items- the quantum of the resource being required or utilized at any point in time and the resources going to be used in the near future. This information would be utilized by the SDM-C for resource allocation for different slices and by the SDM-X to ensure that the resources are optimally shared during the run time while meeting the QoS constraints- including the delay, jitter, and so on. Prediction also helps to free or allocate the available resources to the slices. It also helps to reallocate the resources to the slices dynamically. The QoS monitoring & mapping module of the NORMA architecture ensures that the agreed SLA is met.

# [14.4.2 Prediction based architecture](#toc.xhtml#s296a)

The presence of heterogeneous services in the aggregated traffic imparts fractal or self-similar characteristics that are the statistical features of the traffic observed over different time scales remain invariant. This property results in **long-range dependency** (**LRD**) in the traffic. The architecture proposed here considers this LRD while predicting the congestion. The degree of congestion is predicted as the packet drop probability. The LRD comes with the inclusion of the multiple previously predicted values as additional input in the predictor.

# [14.4.3 Resource allocation](#toc.xhtml#s297a)

With the support of **software-defined networking** (**SDN**) over the 5G, resource sharing over the network among the different service providers would be a reality. The resources can be allocated to the different services and subsequently shared among the slices of the 5G network effectively. Again, a simple MLP can be used for resource allocation as indicated in *[figure 14.12](#c14.xhtml#fig14_12)*.

5G networks standard has enabled numerous applications that were unthinkable in the past. However, these applications pose a major usability issue when the user starts roaming at high speeds. One of the issues is to support data offloading from users of high speed to provide a seamless experience. For example, an average user spends significant time on the roads for travel. In other words, at any point in time, there will be a large number of vehicles on the road plying at high speeds. Several applications will be running on each of these vehicles that require data-streaming onto the cloud or nearby fog terminal and processing in real time. It requires adequate intelligence to be built into the system to onboard or offload the data as the vehicle moves and keep the user experience intact. The offloading needs to happen onto the right fog or edge device and migration has to happen at the right time so that the user gets the processed result on his way at a future point in time. It calls to match the predicted movement of the user with the sequence of fog terminals:

![](images/Figure-14.12.jpg)

**Figure 14.12:** ANN for resource allocation

The way of handling offloaded data largely depends on the streaming and migration protocols. Partial results are to be migrated to the next fog terminal on the way of the user so that the results are available within his RF range and avoid further hops. The optimal offloading involves migration linked to the user mobility and the speed and the timing of offloading. Transfer of the partial results like how much to process on a fog terminal and whom to send these results play a role in the usability of the results.

In the near future, cloud resources will be increasingly used over 5G networks both for data steaming and processing in real-time. It calls for low latency in the round trip. Support for the latency of less than 1 ms for the mobile user is an important aspect of 5G technology. Towards this, it is a challenge to support the upcoming AR/VR applications and provide a seamless experience for a user travelling past the 5G network in a bullet train with a speed of 500 kmph. By the time a channel gets established and streaming starts with a ground station or a fog network, it would vanish from the horizon. It requires continuous tracking of the user, prediction of the next moves, and monitoring of the traffic patterns over the network to provide a seamless experience. To make it happen, offloading of the data or the process should happen dynamically along the path of the user over the right choice of the fog or edge terminal. In addition, the process migration with partial or completed results should follow the user with the same speed. For meeting the QoS constraints, it is required to allocate to each slice the needed resources and the ability to forecast their respective demands. Various factors need to be considered in the design. They include:

*   Future traffic demands forecast within individual network slices. Prediction should be more efficient if performed on traffic at the data center, due to large volumes of data rather than combined from independent forecasts at the base stations. The precise allocation of resources to slices to optimize the total network utility.
*   Performance of different services often depends on the conflicting requirements of bandwidth, sensitivity to delay, or the monetary value of the traffic incurred. Optimal end-to-end flow rates that maximize the utility of a sliced network.
*   CNN application: Customized loss function targets capacity. Forecast to help the operator tune the balance between overprovisioning and demand violations; prediction errors determine a certain (e.g., economic) cost for the mobile network provider loss function proportional to SLA violation.
*   Operation on a per-service basis in accordance with network slicing requirements. Drives the orchestration at C-RAN, MEC, and core datacenters.

The applications of CNN for 5G are provided in *[figure 14.13](#c14.xhtml#fig14_13)*:

![](images/Figure-14.13.jpg)

**Figure 14.13:** Applications of CNN in 5G

# [14.5 Quantum computers](#toc.xhtml#s298a)

The upcoming 5G networks standard has provided innumerable opportunities and use cases. However, it throws new challenges of scalability, prioritization, security threats, etc. The dynamics change so fast that the traditional algorithms have been pushed to the limit. It calls for massively parallel processing to render the results in real-time. In the overlapping of the technologies, quantum computers are also used in conjunction with 5G. In order to support the numerous applications and devices in real-time communication with agreed Quality of Service, large scale planning before the deployment of 5G networks and subsequent tuning of the parameters is necessary. It calls for the network to be dynamic and adaptive with built-in intelligence to shape the traffic. Artificial intelligence and optimization algorithms can be successfully used for this purpose. Although the technology is helpful and practical, the scope is limited in time and space. For example, such algorithms can have the visibility of a few data centres with the prediction and last over a few seconds, often demanding unaffordable resources, time and power. To take it to the next level, a global intelligence platform is required for the prediction, optimization, and categorization, etc. in real-time encompassing large networks. Quantum computers address all these issues in one shot with their support for massive parallelism. The parallelism is exploited in the solution of matrix inversion, for example, 50×50, solution of simultaneous equations involving 50 variables, and so on.

Quantum computers are known to provide such parallelism in computation involving low latencies. With quantum computing, APIs are available commercially over the cloud, it is natural to utilize the service to address these issues. Several factors contribute to a quantum algorithm to run faster than its classical counterparts. The important features of quantum computers include:

1.  **Quantum parallelism**: By using the superposition of quantum states, the computer is executing the algorithm on all possible inputs at once in parallel, for example, in the multiplication of a matrix by a scalar, all elements get multiplied in one shot simultaneously.
2.  **Dimension of quantum Hilbert space**: The span of the state space in a quantum system is exponentially larger than the corresponding classical system.
3.  **Entanglement capability**: Different components or qubits in a quantum computer become entangled, exhibiting correlations.
4.  **Teleportation:** Ability to transfer data set over large distances instantaneously.

The other features of a quantum computer related to high processing power include:

1.  In classical storage: n bits hold a single value from 0 to n quantum storage, n qubits can hold all values.
2.  In classical computation, an n-bit ALU performs 1 operation/cycle. In quantum computation, an n-qubit ALU perform "2n" operations/cycle.
3.  Superposition allows multiple states to exist and perform multiple operations simultaneously, while entanglement allows multiple states to be acted on simultaneously.
4.  Supports super dense' coding--- can transport two bits of classical information over a single entangled qubit.
5.  Explore an enormous number of possible solutions to a problem simultaneously.
6.  A given problem on a quantum computer always require fixed depth irrespective of the number of inputs. On a classical computer, for the same problems circuit depth grows exponentially with input.
7.  Quantum computer can access an entire database in a single shot. 64 regular bits on a classical computer can also represent a huge number (264) of states, one at a time. To cycle through all these combinations, at two billion per second (which is a typical speed for a modern PC), would take about 400 years.

Today, APIs are making use of quantum computers that have been hosted on the cloud for commercial applications. Telecom service providers have started to use the applications to plan for the next generation of mobile networks. The solution for the design challenges for 5G with Quantum computers includes.

*   Resource planning
*   Dynamic resource allocation and fine-tuning with quantum computing algorithms

*[Table 14.2](#c14.xhtml#tab14_2)* summarises the usage of quantum algorithms:

 
| **Paradigm** || **Quantum counterpart realization** |
| --- | --- |
| Bayesian network || Statistical inferencing is common due to the stochastic nature of quantum systems. Used in decision trees |
| Boltzmann machine || The Ising model of energy minimization resembles Hamiltonian minimization in adiabatic computer |
| Quantum genetic algorithm || Parameter reduction |
| Quantum neural network. perceptron || Vibrational quantum circuit |
| Quantum reinforcement learning || Achieved parameter reduction (by 50%) in next state selection /Q learning |
| Quantum Associative Memories || The exponential increase in the capacity of the memory to store pattern |
| Competitive Learning in Quantum System || Works in the presence of incomplete patterns |

**Table 14.2:** Algorithms over quantum computers

# [14.6 Conversation systems](#toc.xhtml#s299a)

The conversation system is an important component of the human-machine interaction systems. It may be similar to the IoTs in the machine to machine interactions. Research on the interactive **Conversation Engine** (**CE**) is gaining enormous popularity and widely replacing the conventional **Interactive Voice Response** (**IVR**) systems and contact centres. The prime advantages are two-fold. Firstly, it eliminates the waiting time to get into the conversation and call-transfer time, when the user switches the topics. Secondly, the responses can be customized based on the user’s intent.

The dialog system invokes frame-filling based on the user query. Typically, the user will be asked one question at a time till all the slots are filled. However, if the user’s answer contains information to fill in more than one slot, corresponding questions will not be asked. Based on the tokens from the user utterance (query or request), an appropriate frame would be invoked. Some of the sample applications are detailed as follows:

**Example 1**: The user can query the conversation system to know the details of the transactions made through the ATM of a bank. A sample conversation goes like this:

**User**: What is the highest withdrawal from ATM in July 2020?

The frame corresponding to ATM withdrawal gets invoked. It is a 3 step approach:

*   Identify the frame type from the user utterance or tokens.
*   Ask clarification questions from a pre-defined template if some of the fields of the frame do not get enough information from the user utterances to populate.
*   Start filling the slots from the response of the user for the queries posed. This is repeated until all slots in the template frame are filled.

**System**: It is $500 on 15th July 2020

**Example 2**: The user can query a conversation system to know the bank account balance.

**User**: Show me the account balance.

Tokens or keywords such as ‘*account balance*’ are extracted from user utterances. A template frame corresponding to the account balance is taken and the information is populated. The template frame can be different for various queries such as account balance, utility bill payment, and so on. The template for account balance with possible fields and types of keywords or values is shown in *[Table 14.3](#c14.xhtml#tab14_3)*:

**Template:**

 
| **Start month and year** || **Stop month & year** || **Amount****(optional)** || **Relation****(optional)** |
| --- | --- | --- | --- |
| YesterdayTodayThis monthJanuaryDecember201320142020 ||  || RS 100100$ || HighestLowestAboveLess thanFirstUp toLastLast timeRecentlyLast(N)All |

**Table 14.3:** Template frame for query on account balance

**Example 3**: Queries on the banking system

If entailment works better, it may be incorporated. Else, the existing token-based search may be used. User queries can come in two flavors as shown in *[figure 14.14](#c14.xhtml#fig14_14)*\- personal or specific to the user and the **frequently asked questions** (**FAQs**). The FAQs are common for all users. The FAQs are to be organized as a separate database:

![](images/Figure-14.14.jpg)

**Figure 14.14:** FAQ system

**Example 4**: Interactive action/troubleshoot

The interactive troubleshooting may be realized as a state machine as frame-filling is not relevant. The user responses are expected to be crisp and mapped onto one of the known forms to trigger the next question. Frequent interaction happens between the user and the machine. The decision tree is to be transferred to the state machine. At each state, one query is triggered. Based on the user response, another query/ statement follows.

This application is subjective and a non-verbal menu-based thing should be sufficient. However, it can be implemented exactly similar to slot filling except that the state machine is implemented instead of slots fill. For example, change of password, enable the blocked account, loss of credit card report, block the account, reversal of deductions, etc. The steps to change a user-triggered password are given as follows:

**User**: I want to change the password.

\[System invokes corresponding FAQ/ messages; keywords: ‘change password’. That FAQ contains the following tree\]

**System**: Please tell your date of birth as proof.

**User**: 2^(nd) August 1956

\[If the user response is correct

    Go to the next step

Else,

    Respond as “Please type correct data.”\]

**System**: Please type your login in the window (& the system pops up a window).

**User**: Provides the login details.

\[If the user response is correct

    Go to the next step

Else,

    Respond as “please type correct data.”\]

**System**: Now type the old password & the new password.

**User**: Provides the password.

\[If the user response is correct

    Go to the next step

Else,

    Respond as “please type correct data.”\]

**System**: It takes 2 days for activation. Is there anything I can do?

At the outset, it appears as a hard-coded program. However, if the user does not follow the system at any point in the workflow or asks a query, the system should provide the appropriate response. It calls for inferring what the user is doing, detection of a problem happening, and contextually responding similarly to what a human operator does. That is where the machine learning algorithms are helpful, i.e., to tokenize the user utterances, interpret the same using natural language processing, and generate a contextual response based on the information in the stored slots, as well as, the local databases.

# [14.7 Neuromorphic computing](#toc.xhtml#s300a)

A neuromorphic computing chip essentially takes a target pattern and learns to match similar patterns from a large database. When the pattern progressively varies over time, the system generates new augmented patterns and uses the same for subsequent matching. It is a classic example of the dynamic addition of new knowledge for reasoning.

Neuromorphic chips are useful for pattern learning and retrieval of a specific pattern; the various applications include real-time learning, dynamic addition of new knowledge, unsupervised learning and incremental learning (with less data). It encompasses feed-forward neurons, memories, and pattern associations. For example, the voice, iris, or face of a person of interest or the attributes of any target may be stored in the chip. When real-time data is fed, it looks for those patterns and detects if it is present. It mimics the parallelism of neurons of the brain, communication among neurons, and so on. This is complementing the architecture of the CNNs that mimic a different behavior of the brain. The learning can also happen through counter examples.

Neuromorphic chips are useful for a variety of applications such as the detection of pattern/ anomaly in running data (for example, stock values), ECG signal processing, medical imaging, industrial fault inspection, etc. The system can provide a multi-level response; for example, for the monitoring of prospective customers, a neural network can be trained to classify people as high, medium, low, and unlikely buyers:

1.  **Object recognition**: From a single instance of the picture/voice input from different persons, it is possible to associate subsequent images with the correct name. It is also useful for the detection of defects, rare events, and anomalies.
2.  **Optical character recognition**: From a single instance of the handwritten text spanning all the alpha numerals, digitization of the user’s handwritten documents are possible. For example, official government documents. It is also used for biometric evaluation in real-time as shown in *[figure 14.15](#c14.xhtml#fig14_15).*
3.  **User recognition**: The system gets information on real-time transactions of the surroundings and correlates the patterns. For example, the system learns to identify “*John*” by his face either with explicit mentioning or contextual learning. Subsequently, it can differentiate John from the rest of the crowd:
    
    ![](images/Figure-14.15.jpg)
    
    **Figure 14.15:** Neuromorphic chip for pattern matching
    

# [14.8 Deep reinforcement learning](#toc.xhtml#s301a)

Deep reinforcement learning is used for a variety of solutions. The agents learn from the environment through reward and penalty based on matching or mismatching with the expected results.

The system learns optimal resource management policies with limited prior information and adapts dynamically to the changes. The system derives the control decisions to maximize efficiency. The action selection function is continuously reinforced to maximize the rewards received. The components of a deep reinforcement learning system are shown in *[figure 14.16](#c14.xhtml#fig14_16)*.

Deep reinforcement learning is also used to solve stochastic constrained optimization. The optimization function, in general, is not readily available in most of the scenarios, making the numerical solution impractical. The examples include:

1.  Corporate governance.
2.  Simulation of war (with the end goal of “*winning*” with minimum loss in the shortest time, each move is based on the outcomes that stochastically restrict the resources).
3.  Winning an election! (The goal is to win the election. The policies to be implemented to achieve the same are to be learnt iteratively)
4.  Drug discovery.
5.  Proliferation of bugs & errors and its impact on revenues, while the patches to fix the same are released subsequently.
6.  Social networks- for the deep penetration (or otherwise) of positive reviews on a product/company/person vis-a-vis the competitor, subject to the investment constraint, volatile market, the quantum of sales, etc.; artificial introduction of stochastic constraints to make it viral.
7.  Containment of famine, epidemics (SARS), economic meltdown, and the real estate bubble burst.
8.  Signaling-regulatory pathway inference.
    
    ![](images/Figure-14.16.jpg)
    
    **Figure 14.16:** Deep reinforcement learning system
    

# [Conclusion](#toc.xhtml#s302a)

Advancement in technology has pushed AI algorithms from the laboratory to the cloud and then to the customer premises. While advanced research in AI has benefitted to solve several issues in the emerging technologies, the converse is also seen. Numerous applications with AI are realized due to the availability of the niche technologies discussed in the previous chapters. The scenarios thought to be fiction a few years back have been realized with the availability of these technologies taking the AI to a new high. More such algorithms and technologies are getting intertwined with AI for mutual benefit as indicated in this chapter.

# [Points to remember](#toc.xhtml#s303a)

*   Quantum computers have realized the AI algorithms.
*   Cognitive IoTs acquire the data judiciously.
*   Resource allocation in 5G during the run time is tackled by the machine learning algorithms.
*   While cloud computing has revolutionized AI, AI algorithms are used to enhance cloud performance.
*   Research in AI hardware has helped to further proliferate the technology.

# [Questions](#toc.xhtml#s304a)

1.  What is the contribution of AI to cloud computing?
2.  What type of machine learning algorithms are used in 5G?
3.  What are the advantages of neuromorphic chips?
4.  How does a quantum computer help in executing AI algorithms?
5.  What are the applications of IoT?
6.  When is unsupervised learning preferred over supervised learning?

# [Multiple choice questions](#toc.xhtml#s305a)

1.  **Choose the correct answer** 
    1.  AI algorithms sit in cognitive IoTs.
    2.  Quantum computers can replace conventional machines to execute AI algorithms.
    3.  5G is required to accelerate machine learning.
    4.  Cloud APIs are required to run AI algorithms.
2.  **Choose the correct answer** 
    1.  Cognitive IoTs acquire the data optimally.
    2.  Quantum computers can process data related to physics only.
    3.  Implementation of 5G technologies is easily relative to 4G.
    4.  Neuromorphic computing requires supervised learning.
3.  **Choose the correct answer** 
    1.  Natural language generator generates a response to user queries.
    2.  Dialog manager generates the response to the queries.
    3.  Dialog system is the same as a chatbot.
    4.  In a dialog system, the slots are reset after every utterance from the user.

# [Answers](#toc.xhtml#s306a)

1.  **a**
2.  **a**
3.  **a**

# [Index](#toc.xhtml#ind)

Symbols

5G networks [339](#c14.xhtml#page339)

CNN applications [345](#c14.xhtml#page345)

NOvel Radio Multiservice Adaptive network (NORMA) architecture [341](#c14.xhtml#page341)

prediction based architecture [342](#c14.xhtml#page342)

requirements [340](#c14.xhtml#page340), [341](#c14.xhtml#page341)

resource allocation [343](#c14.xhtml#page343), [344](#c14.xhtml#page344)

resource management [341](#c14.xhtml#page341), [342](#c14.xhtml#page342)

A

activation functions

Leaky ReLU [247](#c10.xhtml#page247)

ReLU [246](#c10.xhtml#page246)

sigmoid [246](#c10.xhtml#page246)

Tanh [247](#c10.xhtml#page247)

actual values [63](#c02.xhtml#page63)

AI systems [5](#c01.xhtml#page5)

abstraction levels [5](#c01.xhtml#page5)\-[7](#c01.xhtml#page7)

industry domains and sectors [7](#c01.xhtml#page7)

AI Winter cycle [10](#c01.xhtml#page10)

AlexNet [234](#c09.xhtml#page234)

architecture [235](#c09.xhtml#page235)

reference [236](#c09.xhtml#page236)

AllenNLPFramework [284](#c11.xhtml#page284)

Apple’s CoreML [26](#c01.xhtml#page26)

applications, ML

device specific applications [315](#c13.xhtml#page315)

domain-specific applications [307](#c13.xhtml#page307)

platform-specific applications [319](#c13.xhtml#page319), [320](#c13.xhtml#page320)

solution-specific applications [321](#c13.xhtml#page321)

technology specific applications [312](#c13.xhtml#page312)

telecommunications [307](#c13.xhtml#page307)\-[312](#c13.xhtml#page312)

Apriori algorithm [161](#c05.xhtml#page161)

advantages [161](#c05.xhtml#page161)

Artificial Intelligence (AI) [2](#c01.xhtml#page2), [3](#c01.xhtml#page3)

applications [5](#c01.xhtml#page5)

definitions [3](#c01.xhtml#page3), [4](#c01.xhtml#page4)

Artificial Neural Network (ANN) [291](#c12.xhtml#page291)

association rules techniques [158](#c05.xhtml#page158), [159](#c05.xhtml#page159)

antecedent [159](#c05.xhtml#page159)

Apriori algorithm [161](#c05.xhtml#page161)

common terms [160](#c05.xhtml#page160)

confidence [160](#c05.xhtml#page160)

consequent [159](#c05.xhtml#page159)

lift [160](#c05.xhtml#page160)

support [160](#c05.xhtml#page160)

types [161](#c05.xhtml#page161)

use cases [166](#c05.xhtml#page166)\-[170](#c05.xhtml#page170)

Asynchronous Actor-Critic Agents (AAAC) algorithm [17](#c01.xhtml#page17)

Asynchronous Stochastic Gradient (ASGD) [284](#c11.xhtml#page284)

atoms [118](#c03.xhtml#page118)

attention-based LSTM [269](#c11.xhtml#page269)

architecture [270](#c11.xhtml#page270), [271](#c11.xhtml#page271)

block diagram [269](#c11.xhtml#page269)

AUC-ROC

False Positive Rate (FPR) [66](#c02.xhtml#page66)

True Negative Rate (TNR or Specificity) [66](#c02.xhtml#page66)

True Positive Rate (TPR or Sensitivity) [66](#c02.xhtml#page66)

augmented reality (AR) [339](#c14.xhtml#page339)

autoencoders [289](#c12.xhtml#page289), [290](#c12.xhtml#page290)

advantages [292](#c12.xhtml#page292)

adversarial autoencoders [300](#c12.xhtml#page300)

applications [301](#c12.xhtml#page301)

architecture [290](#c12.xhtml#page290), [291](#c12.xhtml#page291)

characters [292](#c12.xhtml#page292)

codings [291](#c12.xhtml#page291)

contractive autoencoders [300](#c12.xhtml#page300)

decoder [291](#c12.xhtml#page291)

denoising autoencoders [297](#c12.xhtml#page297)

disadvantages [292](#c12.xhtml#page292)

encoder [291](#c12.xhtml#page291)

examples [301](#c12.xhtml#page301)

overcomplete autoencoders [297](#c12.xhtml#page297)

sample use case [292](#c12.xhtml#page292)\-[296](#c12.xhtml#page296)

sparse autoencoders [298](#c12.xhtml#page298)

stacked autoencoders [298](#c12.xhtml#page298)

undercomplete autoencoders [296](#c12.xhtml#page296), [297](#c12.xhtml#page297)

variational autoencoders (VAEs) [299](#c12.xhtml#page299), [300](#c12.xhtml#page300)

versus PCA [292](#c12.xhtml#page292)

winner-take-all (WTA) autoencoders [300](#c12.xhtml#page300)

averaging ensemble methods [217](#c08.xhtml#page217)

B

bagging [58](#c02.xhtml#page58)

baselining model [133](#c04.xhtml#page133)

Bayesian scores [142](#c04.xhtml#page142)

best practices, training mechanisms in MLP

better prediction [250](#c10.xhtml#page250)

data preparation [250](#c10.xhtml#page250)

frequent update of weights [250](#c10.xhtml#page250)

training algorithm, selecting [250](#c10.xhtml#page250)

bias [197](#c07.xhtml#page197)

bias and variance trade-off strategy [196](#c07.xhtml#page196)\-[198](#c07.xhtml#page198)

Bidirectional Encoder from Transformers (BERT) [284](#c11.xhtml#page284)

bidirectional LSTM

architecture [269](#c11.xhtml#page269)

block diagram [268](#c11.xhtml#page268)

BigML [25](#c01.xhtml#page25)

binary encoding [137](#c04.xhtml#page137)

binning [143](#c04.xhtml#page143)

boosting ensemble methods [217](#c08.xhtml#page217)

bootstrap aggregating [58](#c02.xhtml#page58)

Boston Housing Price Dataset [30](#c01.xhtml#page30)

Box-Cox transformation [195](#c07.xhtml#page195)

Box Plotting [143](#c04.xhtml#page143)

Breast Cancer Wisconsin (Diagnostic) Dataset [30](#c01.xhtml#page30)

C

categorical encodings [134](#c04.xhtml#page134)

nominal encoding types [134](#c04.xhtml#page134)

ordinal encoding types [135](#c04.xhtml#page135)

categorical imputation [143](#c04.xhtml#page143)

classification [42](#c02.xhtml#page42)

algorithms [43](#c02.xhtml#page43)

classification techniques [151](#c05.xhtml#page151)

cloud computing [334](#c14.xhtml#page334)

architecture [335](#c14.xhtml#page335)

hierarchical organization [338](#c14.xhtml#page338), [339](#c14.xhtml#page339)

software issues [335](#c14.xhtml#page335), [336](#c14.xhtml#page336)

solutions, for software issues [336](#c14.xhtml#page336), [337](#c14.xhtml#page337)

with partitioned software [337](#c14.xhtml#page337)

cluster analysis [95](#c03.xhtml#page95)

clustering techniques [155](#c05.xhtml#page155)

clustering, unsupervised machine learning [95](#c03.xhtml#page95)

DBSCAN algorithm [103](#c03.xhtml#page103), [104](#c03.xhtml#page104)

Flat clustering [96](#c03.xhtml#page96)

Hard clustering [96](#c03.xhtml#page96)

hierarchical clustering [96](#c03.xhtml#page96), [101](#c03.xhtml#page101)

K-Means [97](#c03.xhtml#page97)\-[101](#c03.xhtml#page101)

Soft clustering [96](#c03.xhtml#page96)

types [96](#c03.xhtml#page96)

use cases [96](#c03.xhtml#page96)

clusters [95](#c03.xhtml#page95)

CNN model [230](#c09.xhtml#page230), [231](#c09.xhtml#page231)

architecture [231](#c09.xhtml#page231)\-[234](#c09.xhtml#page234)

use cases [237](#c09.xhtml#page237)\-[239](#c09.xhtml#page239)

CNN network

training [236](#c09.xhtml#page236)

common classification loss functions

log-cosh loss [69](#c02.xhtml#page69)

Mean Absolute Error (MAE) [69](#c02.xhtml#page69)

Mean Squared Error or Quadratic Loss (MSE) [69](#c02.xhtml#page69)

smooth mean absolute error or huber loss [69](#c02.xhtml#page69)

common loss functions

AdaGrad [73](#c02.xhtml#page73)

Adaptive moment estimation (Adam) [74](#c02.xhtml#page74)

binary cross entropy loss [70](#c02.xhtml#page70)

categorical cross entropy [70](#c02.xhtml#page70)

cross entropy loss [70](#c02.xhtml#page70)

gradient descent with momentum [73](#c02.xhtml#page73)

hinge loss [70](#c02.xhtml#page70)

log loss [70](#c02.xhtml#page70)

mini-batch gradient descent [72](#c02.xhtml#page72)

multiclass cross entropy [70](#c02.xhtml#page70)

multiclass SVM loss [70](#c02.xhtml#page70)

negative log likelihood loss [70](#c02.xhtml#page70)

RMSProp [73](#c02.xhtml#page73)

squared hinge loss [71](#c02.xhtml#page71)

Stochastic Gradient Descent (SGD) [72](#c02.xhtml#page72)

vanilla or batch gradient descent [71](#c02.xhtml#page71), [72](#c02.xhtml#page72)

confusion matrix [63](#c02.xhtml#page63)

False Negatives (FN) [64](#c02.xhtml#page64)

False Positives (FP) [64](#c02.xhtml#page64)

True Negatives (TN) [63](#c02.xhtml#page63)

True Positives (TP) [63](#c02.xhtml#page63)

context-based search [323](#c13.xhtml#page323), [324](#c13.xhtml#page324)

context detection [324](#c13.xhtml#page324)

context retention [324](#c13.xhtml#page324)

context usage [324](#c13.xhtml#page324)

Conversation Engine (CE) [347](#c14.xhtml#page347)

conversation system [347](#c14.xhtml#page347)

examples [348](#c14.xhtml#page348)\-[350](#c14.xhtml#page350)

convolutional neural network (CNN) [230](#c09.xhtml#page230)

algorithms [236](#c09.xhtml#page236), [237](#c09.xhtml#page237)

latest trends [236](#c09.xhtml#page236)

correlated [177](#c06.xhtml#page177)

cost function [46](#c02.xhtml#page46), [68](#c02.xhtml#page68)

cross validation [202](#c07.xhtml#page202)

exhaustive cross validation [202](#c07.xhtml#page202)

holdout cross validation [203](#c07.xhtml#page203)

K-fold cross validation [203](#c07.xhtml#page203)

leave-one-out cross validation [203](#c07.xhtml#page203)

leave-p-out cross validation [202](#c07.xhtml#page202)

Monte-Carlo cross validation [204](#c07.xhtml#page204)

non-exhaustive cross validation [202](#c07.xhtml#page202)

rolling cross validation [202](#c07.xhtml#page202)\-[204](#c07.xhtml#page204)

stratified cross validation [203](#c07.xhtml#page203)

Customer Relationship Management (CRM) [158](#c05.xhtml#page158)

D

data

bias and variance trade-off strategy [196](#c07.xhtml#page196)

categorical data [192](#c07.xhtml#page192)

formatting [191](#c07.xhtml#page191)

numerical data [192](#c07.xhtml#page192)

ordinal data [191](#c07.xhtml#page191)

structured data [191](#c07.xhtml#page191)

test data splitting [195](#c07.xhtml#page195)

text [193](#c07.xhtml#page193)

time series data [192](#c07.xhtml#page192)

training data splitting [195](#c07.xhtml#page195)

unstructured data [192](#c07.xhtml#page192)

data decomposition [40](#c02.xhtml#page40)

data preparation methods, unsupervised machine learning [87](#c03.xhtml#page87)

code sample, for MinMaxScaler [91](#c03.xhtml#page91)

code sample, for Normalizer [95](#c03.xhtml#page95)

code sample, for RobustScaler [92](#c03.xhtml#page92)

code sample, for StandardScaler [89](#c03.xhtml#page89)

data preprocessing and scaling [87](#c03.xhtml#page87), [88](#c03.xhtml#page88)

MinMaxScaler [90](#c03.xhtml#page90)

Normalizer [93](#c03.xhtml#page93), [94](#c03.xhtml#page94)

RobustScaler [91](#c03.xhtml#page91)

sample range of values, for RobustScaler [92](#c03.xhtml#page92), [93](#c03.xhtml#page93)

StandardScaler [88](#c03.xhtml#page88), [89](#c03.xhtml#page89)

data preparation, supervised machine learning [40](#c02.xhtml#page40)

in-processing algorithms [41](#c02.xhtml#page41)

post-processing algorithms [41](#c02.xhtml#page41)

pre-processing algorithms [41](#c02.xhtml#page41)

data processing

data, binarizing [206](#c07.xhtml#page206)

data, normalizing [205](#c07.xhtml#page205)

data re-scaling [205](#c07.xhtml#page205)

data, standardizing [205](#c07.xhtml#page205), [206](#c07.xhtml#page206)

label encoding [206](#c07.xhtml#page206)

missing data, handling [207](#c07.xhtml#page207)

one-hot encoding [206](#c07.xhtml#page206)

use cases [205](#c07.xhtml#page205)

DataRobot [25](#c01.xhtml#page25)

Data Science Venn Diagram [12](#c01.xhtml#page12), [13](#c01.xhtml#page13)

Datawrapper [25](#c01.xhtml#page25)

DBSCAN algorithm [103](#c03.xhtml#page103), [104](#c03.xhtml#page104)

decimal scaling [195](#c07.xhtml#page195)

decision tree algorithm

criterion parameter [56](#c02.xhtml#page56)

Gini index [56](#c02.xhtml#page56)

information gain [55](#c02.xhtml#page55), [56](#c02.xhtml#page56)

max\_features parameter [56](#c02.xhtml#page56)

methods [57](#c02.xhtml#page57)

splitter parameter [56](#c02.xhtml#page56)

steps [55](#c02.xhtml#page55)

decision trees [52](#c02.xhtml#page52)

example [52](#c02.xhtml#page52)\-[54](#c02.xhtml#page54)

terminologies [54](#c02.xhtml#page54)

Deep Adversarial Networks [17](#c01.xhtml#page17)

deep learning

applications [24](#c01.xhtml#page24)

architectures [23](#c01.xhtml#page23)

frameworks [23](#c01.xhtml#page23), [27](#c01.xhtml#page27)

mechanisms [22](#c01.xhtml#page22)

prerequisites [20](#c01.xhtml#page20), [21](#c01.xhtml#page21)

versus, machine learning [24](#c01.xhtml#page24)

Deeplearning4j [26](#c01.xhtml#page26)

deep neural network (DNN) [233](#c09.xhtml#page233)

deep reinforcement learning [352](#c14.xhtml#page352)

examples [352](#c14.xhtml#page352), [353](#c14.xhtml#page353)

denoising autoencoders [297](#c12.xhtml#page297)

density-based clustering [156](#c05.xhtml#page156)

DBSCAN [156](#c05.xhtml#page156)

DENCLUE [157](#c05.xhtml#page157)

OPTICS [157](#c05.xhtml#page157)

deviation [137](#c04.xhtml#page137)

device specific applications

example [315](#c13.xhtml#page315), [316](#c13.xhtml#page316)

feedback predictor model [316](#c13.xhtml#page316)\-[319](#c13.xhtml#page319)

dictionary [118](#c03.xhtml#page118)

Digital Signal Processors (DSP) [306](#c13.xhtml#page306)

dimensionality reduction techniques, unsupervised machine learning [105](#c03.xhtml#page105)

dictionary learning [118](#c03.xhtml#page118)\-[121](#c03.xhtml#page121)

ICA [116](#c03.xhtml#page116), [117](#c03.xhtml#page117)

PCA [108](#c03.xhtml#page108)

Singular Value Decomposition (SVD) [115](#c03.xhtml#page115), [116](#c03.xhtml#page116)

t-SNE [105](#c03.xhtml#page105), [106](#c03.xhtml#page106)

Distributed Machine Learning Toolkit [26](#c01.xhtml#page26)

distribution-based clustering [156](#c05.xhtml#page156)

examples [156](#c05.xhtml#page156)

fuzzy clustering [157](#c05.xhtml#page157)

domain-specific applications [307](#c13.xhtml#page307)

dummy encoding [137](#c04.xhtml#page137)

E

effect encoding [137](#c04.xhtml#page137)

ElasticNet regression [164](#c05.xhtml#page164)

Elbow method [99](#c03.xhtml#page99)

encoding techniques

binary encoding [137](#c04.xhtml#page137)

dummy encoding [137](#c04.xhtml#page137)

effect encoding [137](#c04.xhtml#page137)

hash encoding [137](#c04.xhtml#page137)

ensemble methods [215](#c08.xhtml#page215)

averaging ensemble methods [217](#c08.xhtml#page217)

boosting ensemble methods [217](#c08.xhtml#page217)

parallel ensemble methods [216](#c08.xhtml#page216)

popular ensemble methods [215](#c08.xhtml#page215)

sequential ensemble methods [215](#c08.xhtml#page215)

ensemble model development

advanced ensemble model building tips [220](#c08.xhtml#page220)

use cases [221](#c08.xhtml#page221)\-[226](#c08.xhtml#page226)

entropy [55](#c02.xhtml#page55)

error [67](#c02.xhtml#page67)

error minimization [121](#c03.xhtml#page121)

distance computing [121](#c03.xhtml#page121), [122](#c03.xhtml#page122)

Euclidian distance [123](#c03.xhtml#page123)

examples [124](#c03.xhtml#page124)

Log Loss [123](#c03.xhtml#page123)

threshold limit [122](#c03.xhtml#page122), [123](#c03.xhtml#page123)

exploding gradient problem [264](#c11.xhtml#page264)

F

Fashion-MNIST dataset [30](#c01.xhtml#page30), [83](#c03.xhtml#page83)

Feature Engineering [131](#c04.xhtml#page131)

advantages [133](#c04.xhtml#page133)

binning [143](#c04.xhtml#page143)

examples [131](#c04.xhtml#page131), [144](#c04.xhtml#page144)

feature selection [133](#c04.xhtml#page133)

feature split [143](#c04.xhtml#page143)

imputation [142](#c04.xhtml#page142)

need for [129](#c04.xhtml#page129)

one-hot encoding [143](#c04.xhtml#page143)

outliers, handling [143](#c04.xhtml#page143)

samples [144](#c04.xhtml#page144)

scaling [144](#c04.xhtml#page144)

workflow [132](#c04.xhtml#page132)

feature generation [137](#c04.xhtml#page137)

features [138](#c04.xhtml#page138)

feature reduction [204](#c07.xhtml#page204)

feature selection [138](#c04.xhtml#page138)

baselining model [133](#c04.xhtml#page133)

benefits [133](#c04.xhtml#page133)

categorical encodings [134](#c04.xhtml#page134)

co-relation thresholds [200](#c07.xhtml#page200)

correlation [139](#c04.xhtml#page139)

data, cleaning [140](#c04.xhtml#page140)

data collection [140](#c04.xhtml#page140)

data mining, for pattern selection [141](#c04.xhtml#page141), [142](#c04.xhtml#page142)

data, organizing [140](#c04.xhtml#page140)

data preparation [141](#c04.xhtml#page141)

data, refining [140](#c04.xhtml#page140)

feature generation [137](#c04.xhtml#page137), [138](#c04.xhtml#page138)

feature importance [139](#c04.xhtml#page139)

genetic algorithms [200](#c07.xhtml#page200)

methods [139](#c04.xhtml#page139)

stepwise search-based selection [200](#c07.xhtml#page200)

univariate feature selection [139](#c04.xhtml#page139)

variance thresholds [200](#c07.xhtml#page200)

feature split [143](#c04.xhtml#page143)

feedback predictor model

database initialization [317](#c13.xhtml#page317)

example [316](#c13.xhtml#page316), [317](#c13.xhtml#page317)

food item quantity, consuming [318](#c13.xhtml#page318), [319](#c13.xhtml#page319)

food items, identifying [318](#c13.xhtml#page318)

rate of digestion of individual items, determining [319](#c13.xhtml#page319)

stomach emptiness, detecting [317](#c13.xhtml#page317)

user interaction [319](#c13.xhtml#page319)

Field programmable Analog Arrays (FPAA) [305](#c13.xhtml#page305)

Field Programmable Gate Arrays (FPGA) [305](#c13.xhtml#page305)

Fourier Transforms (FT)

Discrete Fourier Transforms (DFT) [184](#c06.xhtml#page184)

Fast Fourier Transforms (FFT) [184](#c06.xhtml#page184)

Free Music Archive (FMA) [30](#c01.xhtml#page30)

frequency domain series [181](#c06.xhtml#page181)

fuzzy clustering [157](#c05.xhtml#page157)

categories [157](#c05.xhtml#page157)

classical fuzzy clustering [157](#c05.xhtml#page157)

grid-based clustering [158](#c05.xhtml#page158)

shape-based fussy clustering [157](#c05.xhtml#page157)

G

gated recurrent units (GRU) [264](#c11.xhtml#page264)

architecture [264](#c11.xhtml#page264), [265](#c11.xhtml#page265)

Generative Adversarial Networks (GANs) [290](#c12.xhtml#page290)

genetic algorithm-based tuning

inheritance [221](#c08.xhtml#page221)

survival of fittest [221](#c08.xhtml#page221)

variation [221](#c08.xhtml#page221)

Gini impurity [56](#c02.xhtml#page56)

Gini index [56](#c02.xhtml#page56)

Gluon [26](#c01.xhtml#page26)

Google Datasets [29](#c01.xhtml#page29)

GoogleNet [237](#c09.xhtml#page237)

Graphical Processing Unit (GPU) [306](#c13.xhtml#page306)

grid-based clustering [158](#c05.xhtml#page158)

types [158](#c05.xhtml#page158)

H

H2O [26](#c01.xhtml#page26)

hash encoder [137](#c04.xhtml#page137)

hierarchical clustering [101](#c03.xhtml#page101)

Agglomerative [101](#c03.xhtml#page101), [102](#c03.xhtml#page102)

Divisive [102](#c03.xhtml#page102), [103](#c03.xhtml#page103)

human brain [18](#c01.xhtml#page18)

hyperparameters [220](#c08.xhtml#page220)

tuning [220](#c08.xhtml#page220), [221](#c08.xhtml#page221)

I

ImageNet [30](#c01.xhtml#page30), [234](#c09.xhtml#page234)

ImageNet Large Scale Visual Recognition Challenge (ILSVRC) [22](#c01.xhtml#page22), [234](#c09.xhtml#page234)

IMDB Reviews Dataset [30](#c01.xhtml#page30)

imputation

categorical imputation [143](#c04.xhtml#page143)

numerical imputation [142](#c04.xhtml#page142)

using [142](#c04.xhtml#page142)

independent component analysis (ICA) [116](#c03.xhtml#page116)\-[118](#c03.xhtml#page118)

Indians Diabetics Dataset [30](#c01.xhtml#page30)

industry domains and sectors

sample use cases [7](#c01.xhtml#page7)\-[9](#c01.xhtml#page9)

information gain [55](#c02.xhtml#page55), [56](#c02.xhtml#page56)

Interactive Voice Response (IVR) systems [347](#c14.xhtml#page347)

interestingness score [142](#c04.xhtml#page142)

Internet of Things (IoT) [3](#c01.xhtml#page3), [330](#c14.xhtml#page330), [331](#c14.xhtml#page331)

issues [332](#c14.xhtml#page332), [333](#c14.xhtml#page333)

K

Kaggle [29](#c01.xhtml#page29)

Kdnuggets [29](#c01.xhtml#page29)

Keras [26](#c01.xhtml#page26)

kernel function [51](#c02.xhtml#page51)

K-Means algorithm [97](#c03.xhtml#page97)\-[99](#c03.xhtml#page99)

K-Nearest Neighbors (KNN) [39](#c02.xhtml#page39)

knowledge distillation [251](#c10.xhtml#page251)

L

L1 norm [93](#c03.xhtml#page93)

L2 norm [93](#c03.xhtml#page93)

languages, for AI, ML and DL [27](#c01.xhtml#page27)\-[29](#c01.xhtml#page29)

lasso regression [164](#c05.xhtml#page164)

learning mechanism [36](#c02.xhtml#page36)

learning quotient [46](#c02.xhtml#page46)

linear regression [43](#c02.xhtml#page43)

methods [47](#c02.xhtml#page47), [48](#c02.xhtml#page48)

types [44](#c02.xhtml#page44)

linear time series [182](#c06.xhtml#page182)

logistic regression [162](#c05.xhtml#page162)

binary logistic regression [163](#c05.xhtml#page163)

disadvantages [163](#c05.xhtml#page163)

multinomial logistic regression [163](#c05.xhtml#page163)

ordinal logistic regression [163](#c05.xhtml#page163)

long-range dependency (LRD) [342](#c14.xhtml#page342)

Long Short Term Memory Networks (LSTM) [259](#c11.xhtml#page259)

architecture [266](#c11.xhtml#page266)\-[268](#c11.xhtml#page268)

attention-based LSTM [269](#c11.xhtml#page269)\-[271](#c11.xhtml#page271)

bidirectional LSTM [268](#c11.xhtml#page268), [269](#c11.xhtml#page269)

training mechanisms [272](#c11.xhtml#page272)\-[275](#c11.xhtml#page275)

use cases [276](#c11.xhtml#page276)\-[282](#c11.xhtml#page282)

loss function [67](#c02.xhtml#page67), [68](#c02.xhtml#page68), [121](#c03.xhtml#page121)

M

machine learning [11](#c01.xhtml#page11), [35](#c02.xhtml#page35)

applications [12](#c01.xhtml#page12)\-[14](#c01.xhtml#page14)

definitions [11](#c01.xhtml#page11), [12](#c01.xhtml#page12)

history [11](#c01.xhtml#page11)

supervised machine learning [36](#c02.xhtml#page36)

versus, deep learning [24](#c01.xhtml#page24)

Manhattan Distance [93](#c03.xhtml#page93)

margin [49](#c02.xhtml#page49)

Markov decision process (MDP) [17](#c01.xhtml#page17)

Massachusetts Institute of Technology (MIT) [29](#c01.xhtml#page29)

meta algorithms

bagging methods [218](#c08.xhtml#page218)

bagging, versus boosting methods [219](#c08.xhtml#page219)

boosting methods [218](#c08.xhtml#page218)

stacking methods [218](#c08.xhtml#page218)

methods, for avoiding overfitting

cross validation [201](#c07.xhtml#page201)

dropout [201](#c07.xhtml#page201)

early stopping [201](#c07.xhtml#page201)

ensembling [201](#c07.xhtml#page201)

feature extraction [201](#c07.xhtml#page201)

feature selection [200](#c07.xhtml#page200)

regularization [201](#c07.xhtml#page201)

test set, maintaining for validation [199](#c07.xhtml#page199)

methods, for overcoming underfitting [199](#c07.xhtml#page199)

Million Song Dataset [30](#c01.xhtml#page30)

min-max normalization [194](#c07.xhtml#page194)

ML algorithms

classification [14](#c01.xhtml#page14), [15](#c01.xhtml#page15)

reinforcement learning [17](#c01.xhtml#page17)

semi-supervised learning [16](#c01.xhtml#page16), [17](#c01.xhtml#page17)

supervised learning [15](#c01.xhtml#page15)

unsupervised learning [16](#c01.xhtml#page16)

MLlib [26](#c01.xhtml#page26)

MNIST Dataset [30](#c01.xhtml#page30)

MobileNet [237](#c09.xhtml#page237)

model

overfitting [199](#c07.xhtml#page199)

underfitting [199](#c07.xhtml#page199)

Monte Carlo Tree Search [17](#c01.xhtml#page17)

MS-COCO Dataset [30](#c01.xhtml#page30)

Multi-Layered Perceptron (MLP) [244](#c10.xhtml#page244)

architecture [249](#c10.xhtml#page249), [250](#c10.xhtml#page250)

components [244](#c10.xhtml#page244), [245](#c10.xhtml#page245)

knowledge distillation [251](#c10.xhtml#page251)

latest trends [251](#c10.xhtml#page251)

simple perceptron (neuron) [245](#c10.xhtml#page245)

training mechanisms [250](#c10.xhtml#page250)

use cases [252](#c10.xhtml#page252), [257](#c10.xhtml#page257)

Multivariate Imputation by Chained Equation (MICE) [39](#c02.xhtml#page39)

multivariate time series [180](#c06.xhtml#page180)

example [180](#c06.xhtml#page180)

MXNet [26](#c01.xhtml#page26)

N

natural language processing (NLP)

advancements [284](#c11.xhtml#page284)

LSTM, using [282](#c11.xhtml#page282), [283](#c11.xhtml#page283)

negative class [152](#c05.xhtml#page152)

network function virtualization (NFV) [341](#c14.xhtml#page341)

Neural Network (NN) [291](#c12.xhtml#page291)

neuromorphic computing chip [351](#c14.xhtml#page351)

examples [351](#c14.xhtml#page351)

for pattern matching [352](#c14.xhtml#page352)

next-generation technologies [330](#c14.xhtml#page330)

noise [197](#c07.xhtml#page197)

nominal encoding types

mean encoding [135](#c04.xhtml#page135)

one hot encoding [134](#c04.xhtml#page134)

one hot encoding, with many categories [135](#c04.xhtml#page135)

nominal features [134](#c04.xhtml#page134)

non-linear time series [182](#c06.xhtml#page182)

normalization [193](#c07.xhtml#page193)

Box-Cox transformation [195](#c07.xhtml#page195)

decimal scaling [195](#c07.xhtml#page195)

min-max normalization [194](#c07.xhtml#page194)

performing [193](#c07.xhtml#page193)

z-score normalization [194](#c07.xhtml#page194)

numerical imputation [142](#c04.xhtml#page142)

Numpy [184](#c06.xhtml#page184)

O

odds [162](#c05.xhtml#page162)

one-class classification [151](#c05.xhtml#page151)

example [152](#c05.xhtml#page152)

one-hot encoding [143](#c04.xhtml#page143)

one-shot learning mechanism [154](#c05.xhtml#page154)

applications [155](#c05.xhtml#page155)

challenges [155](#c05.xhtml#page155)

ONNX [26](#c01.xhtml#page26)

OpenNMT [284](#c11.xhtml#page284)

OpenNN [26](#c01.xhtml#page26)

optimization function [68](#c02.xhtml#page68)

ordinal encoding types

frequency encoding [136](#c04.xhtml#page136)

label encoding [135](#c04.xhtml#page135)

other encoding techniques [136](#c04.xhtml#page136)

target guided ordinal encoding [136](#c04.xhtml#page136)

outlier class [152](#c05.xhtml#page152)

outliers [143](#c04.xhtml#page143)

handling [143](#c04.xhtml#page143)

overcomplete autoencoders [297](#c12.xhtml#page297)

overfitting [199](#c07.xhtml#page199)

P

parallel ensemble methods

examples [216](#c08.xhtml#page216)

heterogeneous parallel ensemble methods [216](#c08.xhtml#page216)

homogeneous parallel ensemble methods [216](#c08.xhtml#page216)

pictorial representation [217](#c08.xhtml#page217)

parameters, SVM algorithm

degree [51](#c02.xhtml#page51)

gamma [52](#c02.xhtml#page52)

kernel [51](#c02.xhtml#page51)

PartAI [284](#c11.xhtml#page284)

Perceptron [19](#c01.xhtml#page19)

performance metrics, of classification problems

accuracy [64](#c02.xhtml#page64)

AUC ROC [66](#c02.xhtml#page66)

confusion matrix [63](#c02.xhtml#page63)

F1 Score [65](#c02.xhtml#page65), [66](#c02.xhtml#page66)

Log Loss [67](#c02.xhtml#page67)

precision [64](#c02.xhtml#page64), [65](#c02.xhtml#page65)

Recall or Sensitivity [65](#c02.xhtml#page65)

specificity [65](#c02.xhtml#page65)

performance metrics, of regression problems

adjusted R-squared [62](#c02.xhtml#page62)

coefficient of determination [61](#c02.xhtml#page61)

mean absolute error [60](#c02.xhtml#page60), [61](#c02.xhtml#page61)

mean squared error [61](#c02.xhtml#page61)

root mean squared error [61](#c02.xhtml#page61)

R-squared [62](#c02.xhtml#page62)

performance statistics [60](#c02.xhtml#page60)

performance metrics, of classification problems [63](#c02.xhtml#page63)

performance metrics, of regression problems [60](#c02.xhtml#page60)

platform-specific applications [319](#c13.xhtml#page319), [320](#c13.xhtml#page320)

plotly library [177](#c06.xhtml#page177)

predictors [43](#c02.xhtml#page43)

Principal Component Analysis (PCA) [41](#c02.xhtml#page41), [108](#c03.xhtml#page108)

advantages [108](#c03.xhtml#page108)

decomposition Kernel PCA method [110](#c03.xhtml#page110), [111](#c03.xhtml#page111)

decomposition MiniBatchSparse PCA [111](#c03.xhtml#page111)\-[113](#c03.xhtml#page113)

decomposition PCA [113](#c03.xhtml#page113)

decomposition sparse PCA [114](#c03.xhtml#page114), [115](#c03.xhtml#page115)

IncrementalPCA scikit library function [108](#c03.xhtml#page108), [109](#c03.xhtml#page109)

PyTorch [26](#c01.xhtml#page26)

Q

Q-Learning [17](#c01.xhtml#page17)

qualitative data

interval data [192](#c07.xhtml#page192)

ratio data [192](#c07.xhtml#page192)

Quality of Service (QoS) [8](#c01.xhtml#page8), [308](#c13.xhtml#page308)

quantitative data

continuous data [192](#c07.xhtml#page192)

discrete data [192](#c07.xhtml#page192)

quantization [143](#c04.xhtml#page143)

quantum computers [345](#c14.xhtml#page345)

algorithms [347](#c14.xhtml#page347)

features [346](#c14.xhtml#page346)

R

Random Early Detection (RED) [308](#c13.xhtml#page308)

random forest [58](#c02.xhtml#page58)

bootstrap parameter [59](#c02.xhtml#page59)

criterion parameter [59](#c02.xhtml#page59)

max\_features parameter [59](#c02.xhtml#page59)

methods [59](#c02.xhtml#page59), [60](#c02.xhtml#page60)

splitter parameter [59](#c02.xhtml#page59)

Rapid Miner [25](#c01.xhtml#page25)

recurrent neural networks (RNN) [261](#c11.xhtml#page261), [262](#c11.xhtml#page262)

architecture [262](#c11.xhtml#page262)

computations [263](#c11.xhtml#page263)

region of interest (RoI) [8](#c01.xhtml#page8)

regression [42](#c02.xhtml#page42)

algorithms [42](#c02.xhtml#page42)

regression analysis [43](#c02.xhtml#page43)

regression models

factors, for selection [165](#c05.xhtml#page165), [166](#c05.xhtml#page166)

regression techniques [161](#c05.xhtml#page161), [165](#c05.xhtml#page165)

reinforcement learning algorithms [17](#c01.xhtml#page17)

ResNet [237](#c09.xhtml#page237)

ridge regression [163](#c05.xhtml#page163), [164](#c05.xhtml#page164)

uses [164](#c05.xhtml#page164)

S

sample datasets for AI, ML, and DL [29](#c01.xhtml#page29), [30](#c01.xhtml#page30)

scaling [144](#c04.xhtml#page144)

SciPy [184](#c06.xhtml#page184)

SDM-C [341](#c14.xhtml#page341)

SDM-X [342](#c14.xhtml#page342)

Self-organizing Map (SoM) [5](#c01.xhtml#page5)

semi-supervised learning algorithms [16](#c01.xhtml#page16), [17](#c01.xhtml#page17)

sequential ensemble methods [215](#c08.xhtml#page215)

pictorial representation [216](#c08.xhtml#page216)

service level agreement (SLAs) [334](#c14.xhtml#page334)

Shannon's entropy [142](#c04.xhtml#page142)

simple linear regression

data set points [44](#c02.xhtml#page44)

estimated lines [45](#c02.xhtml#page45)

optimal line [47](#c02.xhtml#page47)

simple perceptron (neuron)

activation function [245](#c10.xhtml#page245)

hidden layers [248](#c10.xhtml#page248)

input function [245](#c10.xhtml#page245)

outputs [248](#c10.xhtml#page248)

weights [247](#c10.xhtml#page247)

with various parameters [245](#c10.xhtml#page245)

single neuron cell [19](#c01.xhtml#page19)

Singular Value Decomposition (SVD) [115](#c03.xhtml#page115), [116](#c03.xhtml#page116)

software-defined networking (SDN) [343](#c14.xhtml#page343)

solution-specific applications [321](#c13.xhtml#page321)

context-based search [323](#c13.xhtml#page323)\-[326](#c13.xhtml#page326)

contextual advice [321](#c13.xhtml#page321), [322](#c13.xhtml#page322)

Spam SMS Classifier Dataset [30](#c01.xhtml#page30)

sparse autoencoders [298](#c12.xhtml#page298)

Squeeze Net [237](#c09.xhtml#page237)

stacked autoencoders

architecture [298](#c12.xhtml#page298), [299](#c12.xhtml#page299)

standard deviation [143](#c04.xhtml#page143)

Stanford Generalized Tool [284](#c11.xhtml#page284)

stationary [177](#c06.xhtml#page177)

Stochastic Gradient Descent (SGD) [72](#c02.xhtml#page72)

stride [233](#c09.xhtml#page233)

structured data

nominal data [191](#c07.xhtml#page191)

sum encoding [137](#c04.xhtml#page137)

sum of square of error (SSE) [62](#c02.xhtml#page62)

sum of square of residuals (SSR) [62](#c02.xhtml#page62)

supervised machine learning [15](#c01.xhtml#page15), [36](#c02.xhtml#page36), [37](#c02.xhtml#page37)

advantages [38](#c02.xhtml#page38)

classification [42](#c02.xhtml#page42)

data cleanup [38](#c02.xhtml#page38)\-[40](#c02.xhtml#page40)

data preparation [40](#c02.xhtml#page40), [41](#c02.xhtml#page41)

disadvantages [38](#c02.xhtml#page38)

regression [42](#c02.xhtml#page42)

use cases [74](#c02.xhtml#page74)\-[78](#c02.xhtml#page78)

support vector machine (SVM) [48](#c02.xhtml#page48)

methods [52](#c02.xhtml#page52)

support vectors [49](#c02.xhtml#page49)

SVM algorithm

decision boundary, in higher dimension [50](#c02.xhtml#page50)

decision boundary, in original dimension [51](#c02.xhtml#page51)

non-linear separable data set [50](#c02.xhtml#page50)

optimal line [49](#c02.xhtml#page49)

parameters [51](#c02.xhtml#page51)

synapse [18](#c01.xhtml#page18)

T

Tableau [25](#c01.xhtml#page25)

target class [152](#c05.xhtml#page152)

targets [43](#c02.xhtml#page43)

t-Distributed Stochastic Neighbor Embedding (t-SNE) [41](#c02.xhtml#page41)

technology specific applications

vehicular traffic control [312](#c13.xhtml#page312), [313](#c13.xhtml#page313)

working mechanism [313](#c13.xhtml#page313)\-[315](#c13.xhtml#page315)

telecommunications

churn prediction network [309](#c13.xhtml#page309)

control signal computation, in RED [308](#c13.xhtml#page308)

databases, for churn prediction [310](#c13.xhtml#page310)

QoS status classifier [311](#c13.xhtml#page311)

resource allocations [307](#c13.xhtml#page307)

Temporal Difference (TD) [17](#c01.xhtml#page17)

TensorFlow [26](#c01.xhtml#page26)

test data set [195](#c07.xhtml#page195)

splitting [196](#c07.xhtml#page196)

text values [134](#c04.xhtml#page134)

time domain series [181](#c06.xhtml#page181)

time series data [176](#c06.xhtml#page176)

examples [177](#c06.xhtml#page177)\-[179](#c06.xhtml#page179), [185](#c06.xhtml#page185)

time series data, types

auto-correlation [177](#c06.xhtml#page177)

seasonality [177](#c06.xhtml#page177)

stationarity [177](#c06.xhtml#page177)

time series models

autoregression (AR) [182](#c06.xhtml#page182)

Autoregression Moving Average (ARMA) [183](#c06.xhtml#page183)

Autoregressive Integrated Moving Average (ARIMA) [183](#c06.xhtml#page183)

Fourier Transforms (FT) [184](#c06.xhtml#page184)

moving average (MA) [182](#c06.xhtml#page182)

Vector Autoregression Moving Average (VARMA) [184](#c06.xhtml#page184)

Vector Autoregression (VAR) [183](#c06.xhtml#page183), [184](#c06.xhtml#page184)

time series models, aspects

cycle [180](#c06.xhtml#page180)

season [180](#c06.xhtml#page180)

trend [179](#c06.xhtml#page179)

tools and frameworks, for AI, ML and DL

Apple’s CoreML [26](#c01.xhtml#page26)

BigML [25](#c01.xhtml#page25)

Caffe [25](#c01.xhtml#page25)

DataRobot [25](#c01.xhtml#page25)

Datawrapper [25](#c01.xhtml#page25)

Deeplearning4j [26](#c01.xhtml#page26)

Distributed Machine Learning Toolkit [26](#c01.xhtml#page26)

Gluon [26](#c01.xhtml#page26)

H2O [26](#c01.xhtml#page26)

Keras [26](#c01.xhtml#page26)

MLlib [26](#c01.xhtml#page26)

MXNet [26](#c01.xhtml#page26)

ONNX [26](#c01.xhtml#page26)

OpenNN [26](#c01.xhtml#page26)

PyTorch [26](#c01.xhtml#page26)

Rapid Miner [25](#c01.xhtml#page25)

Tableau [25](#c01.xhtml#page25)

TensorFlow [26](#c01.xhtml#page26)

total sum of squares (SST) [62](#c02.xhtml#page62)

training data set [195](#c07.xhtml#page195)

splitting [196](#c07.xhtml#page196)

training mechanisms, LSTM [272](#c11.xhtml#page272)\-[275](#c11.xhtml#page275)

training mechanisms, MLP

best practices [250](#c10.xhtml#page250)

t-SNE [105](#c03.xhtml#page105), [106](#c03.xhtml#page106)

Twitter Sentiment Analysis Dataset [30](#c01.xhtml#page30)

types, zero-shot learning

Conventional Zero-Shot Learning [153](#c05.xhtml#page153)

Generalized Zero-Shot Learning [153](#c05.xhtml#page153)

Inductive Zero-Shot Learning [153](#c05.xhtml#page153)

Transductive Zero-Shot Learning [153](#c05.xhtml#page153)

U

UCI machine learning repository [29](#c01.xhtml#page29)

undercomplete autoencoders [296](#c12.xhtml#page296), [297](#c12.xhtml#page297)

underfitting [199](#c07.xhtml#page199)

underfitting, of model

methods, for overcoming [199](#c07.xhtml#page199)

univariate time series [176](#c06.xhtml#page176)

univariate time series data [180](#c06.xhtml#page180)

example [180](#c06.xhtml#page180)

Universal Language Model Fine-Tuning (ULMFit) [284](#c11.xhtml#page284)

unstructured data

qualitative data [192](#c07.xhtml#page192)

quantitative data [192](#c07.xhtml#page192)

unsupervised learning algorithms [16](#c01.xhtml#page16)

unsupervised machine learning

advantages [85](#c03.xhtml#page85), [87](#c03.xhtml#page87)

architecture [86](#c03.xhtml#page86)

clustering techniques [95](#c03.xhtml#page95)

data preparation methods [87](#c03.xhtml#page87)

dimensionality reduction techniques [105](#c03.xhtml#page105)

disadvantages [87](#c03.xhtml#page87)

error minimization [121](#c03.xhtml#page121)

introduction [85](#c03.xhtml#page85)

V

vanishing gradient problem [264](#c11.xhtml#page264)

variance [197](#c07.xhtml#page197)

variational autoencoders (VAEs) [299](#c12.xhtml#page299)

architecture [300](#c12.xhtml#page300)

VGGNet [237](#c09.xhtml#page237)

VisualData [29](#c01.xhtml#page29)

VisualQA Dataset [30](#c01.xhtml#page30)

W

weak learners

combining [217](#c08.xhtml#page217), [218](#c08.xhtml#page218)

Wikipedia Corpus Dataset [30](#c01.xhtml#page30)

Y

YouTube Dataset [30](#c01.xhtml#page30)

Z

zero-shot learning [153](#c05.xhtml#page153)

applications [154](#c05.xhtml#page154)

categories [153](#c05.xhtml#page153)

model [154](#c05.xhtml#page154)

types [153](#c05.xhtml#page153)

z-score normalization [194](#c07.xhtml#page194)