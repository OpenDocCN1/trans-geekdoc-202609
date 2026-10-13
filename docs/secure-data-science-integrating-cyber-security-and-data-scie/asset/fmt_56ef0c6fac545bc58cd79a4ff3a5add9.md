
# 1.2 Big Data Security and Privacy

While BDMA is evolving into data science with significant progress over the past five years, Big Data Security and Privacy (BDSP) is becoming a critical need. With the recent emergence of the *Quantified Self* (QS) movement, personal data collected by wearable devices and smartphone apps is being analyzed to guide users in improving their health or personal life habits. This data is also being shared with other service providers (e.g., retailers) using cloud-based services, offering potential benefits to users (e.g., information about health products). But such data collection and sharing are often being carried out without the users’ knowledge, bringing grave danger that the personal data may be used for improper purposes. Privacy violations could easily get out of control if data collectors could aggregate financial and health-related data with tweets, Facebook activity, and purchase patterns. In addition, access to the massive amounts of data collected has to be stored. Yet few tools and techniques exist for privacy protection in QS applications or controlling access to the data.

While securing big data and ensuring the privacy of individuals are crucial tasks, BDMA techniques can be used to solve security problems. For example, an organization can outsource activities such as identity management, email filtering, and intrusion detection to the cloud. This is because massive amounts of data are being collected for such applications and this data has to be analyzed. Cloud data management is just one example of big data management. The question is: how can the developments in BDMA be used to solve cyber security problems? These problems include malware detection, insider threat detection, intrusion detection, and spam filtering.

Machine learning focuses on learning from prior experience and making predictions. The learning techniques may include neural networks, decision trees, and support vector machines. Machine learning is considered to be a branch of Artificial Intelligence (AI). AI also includes planning systems, agents, and expert systems. [Figure 1.2](#ch01.xhtml#fig1_2a) illustrates the various concepts in big data analytics, data science, and machine learning. As stated earlier in this book, we have used the terms interchangeably.

![Figure 1.2 Big data analytics, data science, and machine learning.](images/fig1_2.jpg)

[Figure 1.2 Big data analytics, data science, and machine learning.](#ch01.xhtml#Ffig1_2)

# 1.3 Supporting Technologies

We will discuss several supporting technologies for secure data science. These include (i) data security and privacy; (ii) data mining for security applications; (iii) cloud computing, semantic web, and social networks; and (iv) big data security and privacy. [Figure 1.3](#ch01.xhtml#fig1_3a) illustrates the supporting technologies discussed in this book.

![Figure 1.3 Supporting technologies.](images/fig1_3.jpg)

[Figure 1.3 Supporting technologies.](#ch01.xhtml#Ffig1_3)

With respect to data security and privacy, we will describe database security issues, security policy enforcement, access control, and authorization models for database systems, as well as data privacy issues. With respect to data mining, which we will also refer to as data analytics, we will introduce the concept and provide an overview of the various data mining techniques to lay the foundations for some of the techniques to be discussed in [Parts II](#part_02.xhtml#part2), [III](#part_03.xhtml#part3), and [IV](#part_04.xhtml#part4). With respect to data mining applications in security, we will provide an overview of how some of the data mining techniques discussed may be applied for cyber security applications. With respect to cloud computing, semantic web, and social networks, we will provide some of the key points including cloud data management and technologies such as RDF (Resource Description Framework) for representing and managing large amounts of data. We will also discuss aspects of analyzing and securing social networks. With respect to big data security and privacy, we will discuss the concepts and the challenges such as big data analytics for cyber security, attacks to big data analytics, privacy enhanced big data analytics, and access control for big data. These technologies will provide the foundations for the concepts to be discussed in [Parts II](#part_02.xhtml#part2), [III](#part_03.xhtml#part3) and [IV](#part_04.xhtml#part4).

# 1.4 Data Science for Cyber Security

Malicious insiders, both people and processes, are considered to be the most dangerous threats to both cyber security and national security. For example, employees of a company may steal highly sensitive product designs and sell them to the competitors. This could be achieved manually or often via cyber espionage. The malicious processes in the system can also carry out such covert operations.

Data mining techniques have been applied for cyber security problems including insider threat detection. Techniques such as support vector machines and supervised learning methods have been applied. Unfortunately, the training process for supervised learning methods tends to be time-consuming and expensive and generally requires large amounts of well-balanced training data to be effective. Also, traditional training methods do not scale well for massive amounts of insider threat data. Therefore, we have applied data science techniques for cyber security applications such as malware analysis, novel class detection and insider threat detection.

We have designed and developed several data science techniques for detecting malicious insiders. In particular, we have adapted our stream data analytics techniques to handle massive amounts of data and detect malicious insiders in [Part III](#part_03.xhtml#part3) of this book. We have also designed cloud-based implementations for scalable malware detection. The concepts addressed in [Part III](#part_03.xhtml#part3) are illustrated in [Figure 1.4](#ch01.xhtml#fig1_4a).

![Figure 1.4 Data science for cyber security.](images/fig1_4.jpg)

[Figure 1.4 Data science for cyber security.](#ch01.xhtml#Ffig1_4)

# 1.5 Security and Privacy Enhanced Data Science

One of the challenges we are faced with when using data science and machine learning techniques is that these techniques could be attacked. The adversary usually learns about our models and the data we use and will try and poison the data and thwart the models. We have to be several steps ahead of the adversary and adapt our models. This area has come to be known as *adversarial machine learning* (or *adversarial data mining*). Another problem with data science is that it is now possible to link different pieces of data together and infer highly private or sensitive information. In some other cases it is important to publicize the results of machine learning (e.g., preventing the spread of disease) but keep the personal data private (a particular individual having the disease).

[Part III](#part_03.xhtml#part3) will address techniques to handle attacks to data science as well as privacy-enhanced data science. We discuss techniques such as adversarial support vector machine learning to handle cyber-attacks to the machine learning techniques. With respect to privacy, we give an example of privacy aware decisions trees. We will also discuss a privacy aware policy-based data management framework for quantified self-applications. Finally we will discuss a concrete application for privacy and that is the COVID-19 pandemic. The chapters in [Part III](#part_03.xhtml#part3) will give the reader some understanding of how to deal with cyber-attacks to machine learning techniques as well as ensure privacy while carrying out machine learning. [Figure 1.5](#ch01.xhtml#fig1_5a) illustrates security and privacy enhanced data science.

![Figure 1.5 Security and privacy-enhanced data science.](images/fig1_5.jpg)

[Figure 1.5 Security and privacy-enhanced data science.](#ch01.xhtml#Ffig1_5)
