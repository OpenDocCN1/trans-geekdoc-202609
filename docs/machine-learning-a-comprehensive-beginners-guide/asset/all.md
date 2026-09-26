![](html/images/cover.jpg)

![Cover: Machine Learning: A Comprehensive Beginner’s Guide, Written By Akshay B R, Sini Raj Pulari, T S Murugesh, and Shriram K Vasudevan, Published by C R C Press, Taylor and Francis Group. ](html/images/cover.jpg)

Designed cover image: Shutterstock Images

First edition published 2025

by CRC Press

2385 NW Executive Center Drive, Suite 320, Boca Raton FL 33431

and by CRC Press

4 Park Square, Milton Park, Abingdon, Oxon, OX14 4RN

*CRC Press is an imprint of Taylor & Francis Group, LLC*

© 2025 Akshay B R, Sini Raj Pulari, T S Murugesh, and Shriram K Vasudevan

Reasonable efforts have been made to publish reliable data and information, but the author and publisher cannot assume responsibility for the validity of all materials or the consequences of their use. The authors and publishers have attempted to trace the copyright holders of all material reproduced in this publication and apologize to copyright holders if permission to publish in this form has not been obtained. If any copyright material has not been acknowledged please write and let us know so we may rectify in any future reprint.

Except as permitted under U.S. Copyright Law, no part of this book may be reprinted, reproduced, transmitted, or utilized in any form by any electronic, mechanical, or other means, now known or hereafter invented, including photocopying, microfilming, and recording, or in any information storage or retrieval system, without written permission from the publishers.

For permission to photocopy or use material electronically from this work, access [www.copyright.com](http://www.copyright.com) or contact the Copyright Clearance Center, Inc. (CCC), 222 Rosewood Drive, Danvers, MA 01923, 978-750-8400. For works that are not available on CCC please contact mpkbookspermissions@tandf.co.uk

*Trademark notice*: Product or corporate names may be trademarks or registered trademarks and are used only for identification and explanation without intent to infringe.

ISBN: 978-1-032-67665-4 (hbk)

ISBN: 978-1-032-67666-1 (pbk)

ISBN: 978-1-032-67668-5 (ebk)

DOI: [10.1201/9781032676685](https://doi.org/10.1201/9781032676685)

Typeset in Sabon

by Newgen Publishing UK

# Preface

Machine learning is an exciting and rapidly growing field which is all about creating algorithms and models that enable computers to recognize patterns, make predictions, and improve their performance over time. It empowers computers to learn from data and experiences and make decisions without being explicitly programmed. For beginners, understanding the fundamentals of machine learning can open doors to a world of possibilities. Machine learning is as effective as the datasets it relies on. By understanding the nuances of different types of datasets, conducting thorough exploration, and following best practices, practitioners can harness the power of data to build robust and accurate machine learning models. As the field continues to advance, the role of datasets in shaping the future of machine learning becomes increasingly pivotal.

Machine learning (ML) has revolutionized various industries, and with the advent of oneAPI, the landscape has evolved even further. oneAPI simplifies the development process by providing a unified programming model that spans different architectures, including CPUs, GPUs, FPGAs, and accelerators. It aims to break down the barriers between traditional and specialized computing, fostering a more efficient and portable programming environment. By embracing a unified programming model, oneAPI also empowers practitioners to build efficient and scalable machine learning solutions, marking a significant stride in the evolution of cross-architecture development.

Embarking on the journey of machine learning as a beginner may seem daunting, but with a step-by-step approach followed in this book, it becomes an accessible and rewarding endeavor. You can delve into this fascinating field, to master machine learning concepts.

# Authors

**Akshay B R,** a final-year BTech computer science engineering student and an Intel student ambassador, is a passionate data science enthusiast. He primarily works on problems involving disease prediction and developing healthcare systems. He has published multiple articles in a variety of top journals and conferences. He is also a freelance machine learning tutor and has trained around 2000+ students.

**Sini Raj Pulari** is Professor and Tutor currently working at the Government University (Bahrain Polytechnic, Faculty of EDICT) in the Kingdom of Bahrain. She has 16 years of teaching experience at various Indian universities and in industry, contributing to the teaching field and carrying out activities to maintain and develop research and professional activities relevant to computer science engineering. Her research interests include natural language processing, recommender systems, information retrieval, deep learning, and machine learning. She has authored more than 20 Scopus Indexed Publications and co-authored *Deep Learning: A Comprehensive Guide* (CRC Press/Taylor & Francis). Sini has developed and guided more than 40 undergraduate and postgraduate projects, and she is an active member of boards of curriculum development for various universities. Sini has delivered more than 40 invited lectures on applications and emerging trends in a variety of technological and research advancements. She was a speaker at the workshops AI for All, Understanding Deep Learning Algorithms – Convolution Neural Networks with Real Time Applications, Using Python, Keras and Tensor Flow. She has also participated in the MENA Hackathon group discussion on “innovating tech-based solutions for challenges in the healthcare and energy, environment and sustainability sectors,” which was in partnership with Tamkeen, powered by Amazon Web Services (AWS) and Elijah Coaching and Consulting Services. Sini has completed various certifications such as Apple Certified Trainer, SCJP, Oracle Certified Associate, APQMR-Quality Matters, etc.

**T S Murugesh** has 24 years of experience in academia in the fields of analog and digital electronics, automation and control, IoT, system design, image processing, artificial intelligence, machine learning, instrumentation, and computational bio-engineering. After a tenure of 19 years with the Department of Electronics and Instrumentation Engineering, Faculty of Engineering and Technology, Annamalai University, Tamil Nadu, India, he is an Associate Professor in the Department of Electronics and Communication Engineering, Government College of Engineering, Srirangam, Tiruchirappalli, Tamil Nadu, India. He has delivered several talks at international conferences and given more than two dozen invited lectures at the national level at various institutions, including Sastra University, Annamalai University, Mahatma Gandhi University, Kerala, National Institute of Technology, Tiruchirappalli, etc. He has 50+ peer-reviewed indexed papers in journals, including Springer, Springer Nature, Elsevier, Wiley, Inderscience, etc. He has organized faculty development programs at the national level, and he is a reviewer for IEEE, Inderscience and many other peer-reviewed journals. He has coauthored five books for CRC Press/Taylor & Francis (UK) and is currently co-authoring a book for Nova Science Publishers, USA and two books for CRC Press.

Dr. Murugesh has donned the role of Mentor, Primary Evaluator for the Government of India’s Smart India Hackathon 2022, Toycathon2021, Judge in the Grand Finale in Toycathon 2021, evaluator in The Kavach2023 Cybersecurity Hackathon, organized by the Ministry of Home Affairs (MHA) in collaboration with the Ministry of Education’s (MoE) Innovation Cell, Government of India. He is a hackathon enthusiast, and his team has won first prize in the CloudFest Hackathon 2 presented by Google Cloud, DigitalGov Hack, the Hackathon by WSIS Forum 2023 and Digital Government Authority, Saudi Arabia. His team has also won the MSME Idea Hackathon 2.0 and received 15 Lakhs funding from the Ministry of Micro, Small and Medium Enterprises (MSME) Innovative Scheme, Government of India, as well as the Second Prize in the IFGxTA Hub Hackathon 2022.

Dr. Murugesh is a certified Intel oneAPI Innovator, Mentor under the National Initiative for Technical Teachers Training programme from AICTE, and the National Institute of Technical Teachers Training and Research, and a Certified Microsoft Educator Academy Professional. He is also a Master Assessor for a Naan Mudhalvan Program, 2023, devised by the Government of Tamil Nadu, a reviewer of BE/BTech technical books in the regional language scheme of AICTE, coordinated by the Centre for Development of Tamil in Engineering and Technology, Anna University, Tamil Nadu, India. Huawei has recognized Dr. Murugesh for his academic collaboration. He is a Conference Committee Member, Publishing Committee Member of the International Association of Applied Science and Technology. He holds editorial board membership with the *American Journal of Embedded Systems and Applications*. He has also served as Technical Program Committee Member for a Springer-sponsored, Scopus-Indexed International Conference conducted at Sharda University, India, and he is a Scientific Committee Member for an International Conference conducted at the Sultanate of Oman and a chairperson of an International Hybrid Conference at Mahatma Gandhi University Kerala, India. Dr. Murugesh has held various academic responsibilities, such as Chairman for Anna University Central Valuation, Chief Superintendent for the Anna University Theory Examinations, and the Exam Cell Coordinator for his institution. He also holds professional body membership in the Institution of Engineers (India).

**Shriram K Vasudevan** has more than 17 years of experience in industry and academia. He earned a PhD in embedded systems. He has authored or co-authored 45 books for various publishers, including Taylor & Francis, Oxford University Press, and Wiley. He also has been granted 13 patents so far. Shriram is a hackathon enthusiast and has been awarded by Harvard University, AICITE, CII, Google, TDRA Dubai, the Government of Saudi Arabia, the Government of India, and many more. He has published more than 150 research articles. He was associated with L&T Technology Services before joining Intel in a current role. Dr. Vasudevan operates a YouTube channel in his name, which has more than 41,000 subscribers and maintains a wide range of playlists on varied topics. He is a public speaker as well. Dr. Vasudevan is a oneAPI-Certified Instructor, Intel oneAPI-Certified Instructor, Google Cloud Ambassador, Streamlit Education Ambassador, AWS Ambassador, ACM Distinguished Speaker and NASSCOM Prime Ambassador. He is a Fellow IEI, Fellow IETE and Senior Member IEEE.

# IntroductionWhat is Machine Learning?

DOI: [10.1201/9781032676685-1](http://doi.org/10.1201/9781032676685-1)

## Learning objectives

After reading this chapter, the reader shall be able to understand the following:

*   What is machine learning?
*   Relationship between AL, ML, and DL
*   What are the types of machine learning?
*   Why do we need machine learning?
*   The machine learning framework
*   Machine learning vs. deep learning
*   Machine learning applications

## P1.1 Introduction

The term machine learning (ML) belonging to the research field of Artificial Intelligence (AI) has been buzzing around us for quite a few decades. Most of us would have already carried out some attempts to understand “what the word level abstract meaning is” at least by performing a google search. Even if you have not done that, do not worry you are at the right place to learn in depth about “What is machine learning?” in a technical perspective. The intention of this chapter does not stop there; yes, we will dive a little deeper to understand the various types of machine learning, its application in real-life scenarios, and the differences between ML and deep learning (DL).

## P1.2 What is machine learning?

Okay, let us start by taking you back to your childhood. Do you remember how many times you fell before you started to walk properly? That’s a pretty old memory for you to recollect – we should probably direct this question to your parents. Let us consider an example, which you might remember even now. Every one of us would have had a favorite Kindergarten teacher, who was so sweet and patient to you. Yes, I used the word patient intentionally. You know why! I still remember the way my Kindergarten teacher taught me what an apple is. She literarily brought the real apple and handed it over to me, asked me to play with it to experience and tell me that was an apple. In fact, she did this for almost a week. See [Figure P1.1](#ch07.xhtml#f1).

![Figure P1.1Teacher showing (training) the student for a week “what is an apple?”.](html/images/9781032676654_C000_001.jpg)

[Figure P1.1](#ch07.xhtml#f1b)Teacher showing (training) the student for a week “what is an apple?”.

The following week she brought a tomato and an apple and asked me to tell her which one was the apple. I was able to correctly point out the apple without any hesitation ([Figure P1.2](#ch07.xhtml#f2)).

![Figure P1.2Teacher testing the student if they correctly recognize the apple.](html/images/9781032676654_C000_002.jpg)

[Figure P1.2](#ch07.xhtml#f2b)Teacher testing the student if they correctly recognize the apple.

Now let us come to the point: what do you think the teacher has done to make the student recognize it so well? Yes, the teacher patiently “***trained***” the student with an original apple for a week and the features of the apple such as its red color, round shape and properties of being white and hard inside; all have been registered properly by experiencing it. This collective intelligence gathered by the student helped them to recognize the apple from a different fruit like tomato during a “***testing”*** phase. (By the way, we are not providing false information: Tomatoes are fruits that are considered vegetables by nutritionists as suggested by Britannica.com.)

So, let us discuss the question again: “What is machine learning?” How is it even relevant to the example given above? Now carefully answering this question, by the literal meaning of machine learning, we are trying to make a machine learn. Yes, we feed already known data to a machine and ***train*** it. Once the machine is trained appropriately, we will ***test*** the machine to see whether the machine is able to provide the apt answers with the help of the trained data. We can keep training the machine until it provides us the most optimized results.

Oh, that is all. Isn’t it? Machine learning is all simple now and makes sense.

[Figure P1.3](#ch07.xhtml#f3) correctly depicts the machine learning process in a simple way. The machine takes a picture of an apple as an input, manually extracts the features of the apple and uses the information to learn. This is basically done by various machine-learning algorithms, which are available to create an ML trained model. This ML trained model is provided with test data to check whether the model predicts accurately or not. The major point to be noted here is that, in any machine learning process, the feature extraction is very important and would be done without human intervention.

![Figure P1.3Machine learning process.](html/images/9781032676654_C000_003.jpg)

[Figure P1.3](#ch07.xhtml#f3b)Machine learning process.

## P1.3 Relationship between AI, ML, and DL

Artificial Intelligence (AI) is the broad area of research where researchers started thinking of inducing intelligence to machines. You may all know Sophia, the first humanoid robot who has citizenship of Saudi Arabia. Tang Yu is the AI-driven virtual robot CEO, who has been appointed to optimize the operational efficiency. The whole concept of AI in metaverse swirls around the fact that people do not need to face any real-life risks as they face in a real-life environment. See [Figure P1.4](#ch07.xhtml#f4).

![Figure P1.4Humanoid Robot Sophia, Robert CEO Tang Yu and AI in Metaverse.](html/images/9781032676654_C000_004.jpg)

[Figure P1.4](#ch07.xhtml#f4b)Humanoid Robot Sophia, Robert CEO Tang Yu and AI in Metaverse.

In this epoch of AI, ML is a beautiful subset of AI, which allows a specific task to be performed without any explicit interventions. Data from the past is provided to the system; the system extract features and learns from the patterns identified. Certain inferences are made from patterns and accordingly intelligent decisions are taken. Machine learning algorithms are auto adaptive and hence no explicit human interventions are required for the learning process of models. Feature extraction is an important step in the whole process, which helps the model to predict or classify the data appropriately.

Deep learning (DL) is an advanced subset of AI, where a human brain is imitated in processing and understanding the data. Neural networks tend to be the basis of deep learning, which mainly acts like a black box to grab data and yield wonderful insights. Interpreting the results from the deep neural networks require good analytical skills so that the output obtained makes sense for some other useful applications.

[Figure P1.5](#ch07.xhtml#f5) shows a proper relationship between AI, ML, and DL. Some of the major applications of AI like Natural Language Processing (NLP), visual perception by visualization techniques, automated programming platforms like no code, AI-driven robots for strenuous jobs and household jobs, knowledge representation and reasoning are some of the major applications that comes under AI.

![Figure P1.5Relationship between AI, ML, DL.](html/images/9781032676654_C000_005.jpg)

[Figure P1.5](#ch07.xhtml#f5b)Relationship between AI, ML, DL.

Machine learning has many algorithms like regression, classification, principal component analysis, clustering etc. for finding the inferences from the data analyzed using models created. Multilayer Perceptron’s used in Neural networks with the help of various algorithms like CNN (Convolutional neural networks), RNN (Recurrent Neural Network), GAN (Generative Adversarial Networks), automatic feature extraction and prediction or classification could be achieved using deep learning. The evolution progress of various categories of algorithms is portrayed in [Figure P1.6](#ch07.xhtml#f6).

![Figure P1.6How each of the category of algorithms evolved over time.](html/images/9781032676654_C000_006.jpg)

[Figure P1.6](#ch07.xhtml#f6b)How each of the category of algorithms evolved over time.

## P1.4 Types of machine learning

Now that we have a deep understanding about where machine learning has its place in the AI field of research, it is time for us to understand the various types of machine learning algorithms. Machine learning algorithms are mainly classified as three as given below; however, we add a fourth category for in depth understanding (see [Figure P1.7](#ch07.xhtml#f7)).

![Figure P1.7Types of machine learning algorithms.](html/images/9781032676654_C000_007.jpg)

[Figure P1.7](#ch07.xhtml#f7b)Types of machine learning algorithms.

*   Supervised learning
*   Unsupervised learning
*   Reinforced learning
*   Evolutionary learning

Let’s have a deeper look into the same with easy examples.

## P1.5 Supervised learning algorithms

This algorithm makes use of labelled data gathered from the past to train the model and make the model predict or classify the test data which is not labelled to check whether the model can predict or classify the data properly. Supervised machine learning algorithms use labelled data – what is meant by that? It is simple – consider an example to understand the supervised learning process.

You are provided with a dataset that contains images of both cats and dogs ([Figure P1.8](#ch07.xhtml#f8)). All the images in the dataset are labelled properly, say you have 1,000 images of both cats and dogs each. You are creating a supervised learning model where you train the model using 700 labelled cat data and 700 labelled dog data. You have kept 300 cat and dog images as test data ([Figure P1.9](#ch07.xhtml#f9)). Once the supervised machine learning model is created, we will make the model predict these test data and check the accuracy of the model created.

![Figure P1.8Sample – cat and dog labelled training data set.](html/images/9781032676654_C000_008.jpg)

[Figure P1.8](#ch07.xhtml#f8b)Sample – cat and dog labelled training data set.

![Figure P1.9Sample test dataset with name as cat\_or \_dog\_1 and cat\_or \_dog\_2.](html/images/9781032676654_C000_009.jpg)

[Figure P1.9](#ch07.xhtml#f9b)Sample test dataset with name as cat\_or \_dog\_1 and cat\_or \_dog\_2.

As we now understand what is there in the datasets, we shall proceed with the process.

![Figure P1.10The complete supervised learning process.](html/images/9781032676654_C000_010.jpg)

[Figure P1.10](#ch07.xhtml#f10b)The complete supervised learning process.

The complete supervised learning process is provided in [Figure P1.10](#ch07.xhtml#f10). In the supervised learning model, we work with labelled data, which is fed into the model for training, once the model is trained, test data is fed into the model to either classify or predict the test data. The accuracy of model prediction is usually calculated as an evaluation metric to understand the efficacy of the trained model.

One major point to be noted here is that, if the model is trained using wrong labelled data, of course the model will predict in a wrong manner. Hence the training data fed to the model need to be appropriately labelled ones. Another scenario might be, if the model is not trained with a certain labelled data and if an entirely new data is given for prediction, the percentage of accuracy will be extremely low. This is quite understandable. If you have cats and dogs in the dataset and is given for training the model, and if you give the test set as crocodile, there is a higher chance that the trained model might not be able to predict or wrongly predict the data.

The first [Figure P1.1](#ch07.xhtml#f1) of a teacher teaching a student about the apple is also an example of supervised learning. Maybe you should revisit that example once again to embed the concept well into your mind.

## P1.6 Unsupervised learning algorithm

This approach is different from the supervised learning model, as they don’t have any labels associated with the data. Also, there is no explicit training and testing phases in the unsupervised learning method. Oh, is this not confusing? Then how will the model be able to predict. Yes, there is a way, and we could understand that by using athe simple example that follows.

Consider a student is given a dataset with set of dogs and cats, with absolutely no label ([Figure P1.11](#ch07.xhtml#f11)). Every day this dataset is given to the student and after a week the student is asked to categorize the similar images in the dataset. What do you think the student will do? The student has been going through the different types of images given for a week. The student would have been smart enough to identify the features of both the cat and dog images. By the end of the week, if different set of images are given, obviously with the collective knowledge he has gathered through the process of mapping the features of dog and cat, the student will at least to some extent map or group the cat and dog images properly. Yes, there are some cutie dogs which resemble dogs, we can’t help it though, and hence there may be some misclassifications too ([Figure P1.11](#ch07.xhtml#f11)).

![Figure P1.11Unsupervised learning process.](html/images/9781032676654_C000_011.jpg)

[Figure P1.11](#ch07.xhtml#f11b)Unsupervised learning process.

Given a set of data, it will categorize them and give as output. Each category is referred as a cluster. The labels for the clusters are to be manually tagged later. The categorization is based on the features in the data points. The unsupervised learning algorithms are also referred as clustering algorithms. Consider the same use case discussed for supervised learning with apple and tomato. Here the model will take in all images and gives out two clusters. One cluster will be “apple” whereas another cluster will have all the photos of “tomato.” When a new image is given to the model it will be placed in one of the two clusters based on its features.

## P1.7 Reinforcement learning algorithm

Reinforcement learning algorithm is a machine learning algorithm, which uses the computer agent to learn the optimal behavior of the environment and ought to take the right actions to acquire maximum reward. This is mainly about the decision-making process for which the feedback obtained is very crucial. This is a feedback-based learning process. This method of learning is used in most of the robots and computer-based games. Here the input need not have labelled data. Instead, the model learns by interacting with the environment and getting feedback from it. The first time the model picks a decision, based on the feedback the model learns if its decision is right or wrong. So, this supervised learning relaxes the task of giving completely labelled data for training. A very common example is a computer chess game; if the computer loses while playing with you, then the program will remember all the steps that the player made, and the system made. Next time, the same strategy won’t work in the system and eventually the player will lose to the program.

Oh, does all this seem to be Greek and Latin? Don’t worry, we’ll use an example to help you understand the process.

Let’s take a simple example for reinforcement learning. Consider a mom teaching her kid and when he makes mistake, mom gives feedback so that the feedback could be helpful for him the very next time ([Figure P1.12](#ch07.xhtml#f12)).

![Figure P1.12Reinforcement learning.](html/images/9781032676654_C000_012.jpg)

[Figure P1.12](#ch07.xhtml#f12b)Reinforcement learning.

## P1.8 Evolutionary approach

This is still evolving and is not an easy one. These types of algorithms shall imitate the natural evolution to solve a particular problem. For instance, genetic algorithms can be employed to solve a problem. This is beyond the scope of this book and hence is ignored for now.

## P1.9 So why do we need ML?

This is a wonderful question, at the right time. Yes, by this time, it is obvious that we use our own experience to learn things. Say, for a simple example, going back to childhood. Yes, childhood is a treasure full of experiences, right? So let’s use another example…

Do you ever remember the very first time your hand got hurt touching a hot vessel in the kitchen? It’s likely that unless it was a big one, no one usually even remembers that instance? However, now you are old, do you still need somebody’s assistance to understand whether a vessel is hot, and when you shouldn’t touch it? Here you could understand the experiential learning. Maybe when you were a kid, you would have touched a hot pot and instantly you would have got the impulse. That feedback stays in your collective memory and whenever you see a pot, you just take a precaution to work out whether it is hot or not.

Yes, we humans have the intelligence to do all these things. But we cannot reach everywhere and do this sort of things always. But we do have the intelligence to program a machine to follow our orders. This is exactly what we are trying to do in machine learning. Yes, so why do we do all these? The reason is this will make our lives easy. If we can build an interactive and self-adaptive learning algorithm for a machine and if we could train the machine in the way we need to achieve things, there is nothing like it. However, everything has its own flaws coming along. As humans, first, we should know where to limit the usage of machines and to what extent. Anything and everything could be trained for negative intention too.

Where humans cannot bring the accuracy, yes, machines could bring this. So, making the machines work using human intelligence is a good strategy. Machines with ML algorithms don’t require explicit human intervention as mentioned earlier and machines can always adapt to their environments and learn from feedback and avoid repeated mistakes.

## P1.10 Machine learning framework

A Machine learning framework has various steps which uses math, tools, and techniques. The first step is all about data gathering from the alternative relevant sources. It all starts from data, as data acts as the fuel for the whole process. The next step is basically data cleansing or an extensive exploratory data analysis step where we need to clean and understand the data as much as possible, as this will help further processes to be smooth, easy, and inferential. Building the appropriate model is the next one in the process. Training and testing need to be done. The most important part is understanding the patterns from the results and interpreting the right inferences for the betterment of the whole process itself. Visualization techniques could be of great help to understand the hidden golden nuggets of information from the results. This concludes the flow of ML framework. However, as a picture can speak a thousand words, let’s depict the whole process flow as a simple diagrammatic representation ([Figure P1.13](#ch07.xhtml#f13)).

![Figure P1.13Machine Learning Framework.](html/images/9781032676654_C000_013.jpg)

[Figure P1.13](#ch07.xhtml#f13b)Machine Learning Framework.

## P1.11 Machine learning vs. deep learning

Yes, now we have been talking about the machine learning algorithms, its types, framework etc. Now it is time to dive a little bit deeper and understand the major differences between ML and DL algorithms. The difference in their process flow can be better understood from [Figure P1.14](#ch07.xhtml#f14) and [Table P1.1](#ch07.xhtml#t1) differentiates the two.

![Figure P1.14Difference in process flow with ML and DL.](html/images/9781032676654_C000_014.jpg)

[Figure P1.14](#ch07.xhtml#f14b)Difference in process flow with ML and DL.

[Table P1.1](#ch07.xhtml#t1b) ML vs. DL

 
| Machine Learning || Deep Learning |
| --- | --- |
| Requires only less amount of training data || Requires large amount of training data |
| ML works on pre-identified features || DL automatically identifies the features |
| Results are easily interpretable || Interpreting the results needs some expertise |
| ML uses various algorithms to conclude || DL uses neural networks to conclude |

## P1.12 ML common applications

*   Some of the common ML applications you have already experienced in your life:
*   FB (Facebook) recommending you friends.
*   Amazon recommending you products.
*   Flipkart recommending you products.
*   Netflix recommendations.
*   Netflix recommending you the best series based on your taste but with ML behind. So, the point is simple. With ML in picture, a company can identify more opportunities for making good profits. A scenario – you are browsing Thailand holidays. You did not book any tickets or even confirm the trip. Upon logging in to your Facebook account, you will be getting Thailand holiday-related posts. This is ML for you! It helps in finding avenues for new business, enhancing profit all without any errors or human intervention. No operator is there to link that Thai AD (advertisement) to Facebook page yet.
*   Another major application of ML is in:
*   Agriculture sector – To identify crop diseases.
*   Energy sector – to predict the consumption of energy for a region in the next two months.
*   Education sector – predicting the number of students completing the course and the job openings in the market.
*   Government sector – many ML-related applications are used, as an example automating and identifying the unique identification number from the captured image of a person for recognition purposes.
*   Financial sector, media sector, retail sector, smart home and telecom are some of the other sectors where we frequently employ machine learning concepts.

Well, we have understood the fundamentals of machine learning and this book is intended to get the readers insights on how to build some cool machine learning projects. All these projects are easy to do and will definitely help in understanding ML concepts/algorithms clearly. The datasets, code, and clear explanations are provided to ensure that readers have a smooth learning experience.

Also, we have used the Intel oneAPI as a platform to implement some of the ML projects. With this approach, readers will get to know oneAPI, get the learning clearly about the Intel Developer Cloud, know optimized libraries and enhanced frameworks usage through oneAPI. It is important not just to program, but also to ensure that the code is written in an optimized manner.

The ensuing section is intended to get you the knowledge about oneAPI.

## P1.13 What is oneAPI?

What is oneAPI? Well, this is a question asked by many tech enthusiasts, learners, teachers, industry practitioners and everyone in the tech space. This chapter is intended to provide information as to what oneAPI is all about, why there is a lot of discussion about oneAPI, what oneAPI can provide, etc. (Note: It is oneAPI and not OneAPI.) Let us first understand the problem faced by software developers all around the world. Firstly, there has been humongous growth recently in specialized workloads. Secondly, each hardware needs to use different programming languages and related libraries. This increases the challenges with respect to maintaining different code bases and repositories. Thirdly, though it is seen as an advantage with the increase in the number of tools, it is also a challenge for developers to learn to use different tools, particularly given the learning time involved. What we mean here is that the development of software for different hardware platforms like CPU (Central Processing Unit), GPU (Graphics Processing Unit) or FPGA (Field-Programmable Gate Array) requires different learning strategies, investments and eventually no guarantee of reusing that work with other architectures/hardware. Writing code once, then writing it again for another architecture is the biggest bugbear faced by software developers globally. Yes, this problem has to be solved and this is where oneAPI comes in.

One can understand the aforementioned point by referring to [Figure 1.15](#ch07.xhtml#f15) which is self-explanatory. The challenge to be solved is huge and that is where oneAPI comes in handy.

![Figure P1.15The challenge.](html/images/9781032676654_C000_015.jpg)

[Figure P1.15](#ch07.xhtml#f15b)The challenge.

One must first understand what oneAPI all is about. It is an open and standards-based cross architecture programming model which breaks the programmers’ challenges. oneAPI provides the developers with total freedom and choice to select the hardware as CPU, GPU, or FPGA for enhanced computing. The vision behind the oneAPI’ s creation is interesting. It aims to bring a unified software development environment across CPU, GPU, or other accelerators.

oneAPI is an industry initiative and is completely based on the standards and the open specifications.

oneAPI has many appreciable features which developers certainly appreciate:

1.  First and foremost, the developers can develop and deploy the software with absolute peace of mind.
2.  oneAPI includes libraries and has a unified language which can ensure complete native performance.
3.  Freedom, yes. oneAPI facilitates the native code performance across a range of hardware including CPUs, GPUs, FPGAs, and AI (Artificial Intelligence) accelerators.
4.  Since it is of open industry standards, it is certainly the best approach for the future.
5.  The biggest advantage lies with the compatibility. Yes, it gives you excellent compatibility with the existing programming languages which include the C++, Python, SYCL, Fortran, and openMP.

oneAPI is the foundational or base programming stack. Once should see that as a facilitator to optimize the middleware and the frameworks which gets above it. One can have a clearer understanding of this point by referring to [Figure P1.16.](#ch07.xhtml#f16) The readers could see that TensorFlow kind of frameworks sit above the oneAPI which are optimized for performance. The representation shown in [Figure P1.16](#ch07.xhtml#f16) is enhanced and presented in [Figure P1.17](#ch07.xhtml#f17) to impart ample clarity.

![Figure P1.16The Revolution – oneAPI (The industry initiative and intel product).](html/images/9781032676654_C000_016.jpg)

[Figure P1.16](#ch07.xhtml#f16b)The Revolution – oneAPI (The industry initiative and intel product).

![Figure P1.17Power of oneAPI.](html/images/9781032676654_C000_017.jpg)

[Figure P1.17](#ch07.xhtml#f17b)Power of oneAPI.

The optimized applications go to the topmost layer as one could see from [Figure P1.17](#ch07.xhtml#f17), which leverages the middleware and the frameworks.

The oneAPI comes with powerful and advanced porting tools (this eases our job, folks, it ports the code for us). Analysis tools like the intel VTune profiler, intel advisor, and debuggers are also provided. This enables someone to debug the code or to analyze the performance across all levels of abstraction without any hindrance.

Having explained what oneAPI and what it brings to you as a developer, it is important to talk about another very important benefit it offers to the developers. There is no proprietary lock-in associated with oneAPI and is compatible with the code written in the native languages such as C, C++ and more as conveyed earlier.

In simple words, oneAPI provides developers the option to choose the best of the architecture for a specific problem without forcing the developer to re-write the code for different architectures or platforms.

oneAPI also promotes community and industry collaboration on a larger scale.

Remember this! oneAPI is all about “Write once, deploy many times.”

## P1.14 Approaches: Direct programming and API based

oneAPI is interesting. There are two options provided to the developers for programming. One is direct programming, and the second option is API-Based Programming. In addition, DPC++ provides the compatibility tool and the debug tools with oneAPI ([Figure P1.18](#ch07.xhtml#f18)).

![Figure P1.18Programming model.](html/images/9781032676654_C000_018.jpg)

[Figure P1.18](#ch07.xhtml#f18b)Programming model.

*   The developers working with CUDA and who has the requirement to migrate the existing CUDA code (CUDA Source Code) to the DPC++ (DPC++ Source Code) is easier right now with oneAPI. oneAPI provides you the intel DPC++ Compatibility Tool to migrate source code to source code to from CUDA to DPC++ with ease. There is a lot of assistance offered in the migration and almost 80 to 90 percent automatically. The best part is “inline comments” are also provided in an understandable manner for the developers to finish the porting.
*    The intel oneAPI DPC++ / C++ compiler is very powerful, and it supports the direct programming. This approach comes into place when the APIs are not available for the algorithms. The readers shall be presented with more details about the direct programming. For direct programming, Data Parallel C++ (or DPC++) is an evolution of C++ for productive data-centric coding that will target CPUs, GPUs FPGAs, and AI accelerators.
*   The next approach is the API based programming. There is a huge set of libraries catering to different domains and areas. Details of the libraries is presented in the subsequent section. Developers can just go ahead and use them without any challenge. Readers can find a lot of information on the libraries shortly.
*   Finally, in [Figure P1.18](#ch07.xhtml#f18) you can also see that we have the tools like intel VTune Profiler and Intel Advisor which can help in analyzing performance.

## P1.15 Libraries – more power to you

oneAPI comes with rich set of libraries which enable acceleration of domain-specific functions. All the libraries as shown in [Figure P1.19](#ch07.xhtml#f19) are preoptimized to ensure maximum performance. One could see that the libraries cater to vast domain requirements. These libraries simplify programming by providing developers with APIs.

![Figure P1.19Power of oneAPI.](html/images/9781032676654_C000_019.jpg)

[Figure P1.19](#ch07.xhtml#f19b)Power of oneAPI.

A brief note on each of these libraries is presented below.

*   Intel oneAPI Math Kernel Library – one could use this library to have the highly optimized math routines in their applications being developed.
*    Intel oneAPI Deep Neural Network Library – one could use this library to build the deep learning applications which uses the neural networks optimized for the intel hardware, be it processor or graphics.
*   Intel oneAPI Video Processing Library – as the name indicates this library can be very handy to accelerate the video processing in the chosen application.
*   Intel oneAPI Data Analytics Library – this is one of the best and industry needs this. One can use this library to have speed and performance in the big data applications.
*   Intel oneAPI threading Building Blocks – often called TBB, this gives the developer a chance to combine the TBB-based parallelism on the Multicore CPUs and the SYCL device-accelerated parallelism in the chosen application.
*    Intel oneAPI Collective Communications Library – this can be used where the applications focus primarily on the deep learning and the machine learning workloads.
*   Intel oneAPI DPC++ Library – one can use this library for building high-performance parallel applications.
*   Support in the form of Ray Tracing libraries – to build photorealistic visuals from studio animation to scientific and industrial visualizations.
*   Intel oneAPI Image Processing Library – as the name implies, oneAPI contains image processing functionality, filters, geometric transformations, color and type conversions, and various 3D operations, that allows developers to take advantage of diverse computational devices through SYCL\* APIs without changing their code(s).
*   Intel oneAPI Data Transformation Library – this is a very innovative attempt from intel to provide ready-to-use, optimized data compression functions for diverse architectures. oneDTL is designed in such a way that, execution can happen on wide range of devices which include CPU, GPU etc.

In addition, Intel oneAPI has also a plethora of toolkits available offering a wide range of services.

## P1.16 What’s the connection of oneAPI with this book?

Well, this should be in the mind of readers by now. Let’s answer the question. Machine Learning (ML) concepts can be taught through various platforms and modes. We have chosen oneAPI. Machine Learning will be easier through this approach we believe. Also, it is the need for the hour in the industry. ML skills hand in hand with the oneAPI knowhow will be phenomenal. We are certain that the readers would enjoy this entire journey of learning.

## P1.17 Learning resources

One of the greatest things Intel has done is to provide excellent learning resources for all levels. Be it novice to the expert, the materials and learning pathways provided are simply outstanding. Intel also provides case studies, reference codes through GIT, and more for the learners. Teachers have got the opportunity to become certified instructors for oneAPI and they get access to complete training materials, presentations, example codes, assignment questions and answers.

The below links can be used to learn more about oneAPI:

*   Intro to oneAPI 
    *   [https://intel.ly/3BBDmpr](https://intel.ly/3BBDmpr)
*    oneAPI Toolkits 
    *   [https://intel.ly/3fhSdOA](https://intel.ly/3fhSdOA)
*   Learning Paths 
    *   [https://intel.ly/3S9ErvV](https://intel.ly/3S9ErvV)
*   Community projects 
    *   [https://devmesh.intel.com/](https://devmesh.intel.com)
*   oneAPI DevCloud 
    *   [https://devcloud.intel.com/oneapi/](https://devcloud.intel.com)

To become a certified instructor for oneAPI, one can go ahead and apply with the below link:

[www.intel.com/content/www/us/en/secure/developer/oneapi/certified-instructor-apply.html](http://www.intel.com/content/www/us/en/secure/developer/oneapi/certified-instructor-apply.html)

And remember, it is all free!

## P1.18 The Intel Developer Cloud – your pathway to learning!

The Intel Developer Cloud is interesting and a powerful sandbox which enables someone to develop, test and run the workloads across range of accelerators which include intel CPUs, GPUs, and FPGAs with the Intel oneAPI software stack. Not only this, but it also comes up with excellent tutorials, learning materials, codes for anyone to start using it comfortably.

Here is the process to register for the Intel Developer Cloud, for free.

1.  Visit [https://console.cloud.intel.com/](https://console.cloud.intel.com). It will get you a page where you can find **Create an Account** option as shown in [Figure P1.20](#ch07.xhtml#f20).
    
    ![Figure P1.20Create an account with Intel Developer Cloud.](html/images/9781032676654_C000_020.jpg)
    
    [Figure P1.20](#ch07.xhtml#f20b)Create an account with Intel Developer Cloud.
    
2.  It will prompt you to enter some basic details, which includes your name, email address, country of residence and password of your choice. It does not ask you for your credit card details and it is a great plus for the users. Once the details are filled in, click to verify your email ([Figure P1.21](#ch07.xhtml#f21)).
    
    ![Figure P1.21Account creation.](html/images/9781032676654_C000_021.jpg)
    
    [Figure P1.21](#ch07.xhtml#f21b)Account creation.
    
3.  There will be an email from intel with a verification code; thismust be filled in the column indicated. That’s it, it is almost done ([Figure P1.22](#ch07.xhtml#f22)).
    
    ![Figure P1.22Account Verification.](html/images/9781032676654_C000_022.jpg)
    
    [Figure P1.22](#ch07.xhtml#f22b)Account Verification.
    
4.  After verifying, you will be prompted to select the tier option. Standard free option can be chosen if you do not plan to buy the access ([Figure P1.23](#ch07.xhtml#f23)).
    
    ![Figure P1.23Tier Selection.](html/images/9781032676654_C000_023.jpg)
    
    [Figure P1.23](#ch07.xhtml#f23b)Tier Selection.
    
5.  Once selected, it will take you to console home page as shown in [Figure P1.24](#ch07.xhtml#f24). Click on the training and workshops.
    
    ![Figure P1.24Cloud Console.](html/images/9781032676654_C000_024.jpg)
    
    [Figure P1.24](#ch07.xhtml#f24b)Cloud Console.
    
6.  Once the training and workshops is clicked, it will get you to the training and workshops page and there will be a plethora of options as shown in [Figure P1.25](#ch07.xhtml#f25).
    
    ![Figure P1.25Choose the training.](html/images/9781032676654_C000_025.jpg)
    
    [Figure P1.25](#ch07.xhtml#f25b)Choose the training.
    
7.   On clicking machine learning using oneAPI, one can understand more details about the oneAPI and learning ML with oneAPI. Also, launch JupyterLab option under machine learning with oneAPI will get JupyterLab launched and one can try the ML experiments with oneAPI in this way ([Figure P1.26](#ch07.xhtml#f26)).
    
    ![Figure P1.26JupyterLab launch.](html/images/9781032676654_C000_026.jpg)
    
    [Figure P1.26](#ch07.xhtml#f26b)JupyterLab launch.
    
8.  The complete procedure is presented here: [https://youtu.be/Mk\_DjL3ZUVo](https://youtu.be)

Welcome to the world of machine learning. Let’s learn and create something wonderful.

## Resources

*   Vasudevan, S.K., Pulari, S.R., & Vasudevan, S. (2021). Deep Learning: A Comprehensive Guide (1st ed.). Chapman and Hall/CRC. [https://doi.org/10.1201/9781003185635](https://doi.org/10.1201/9781003185635)
*   Murphy, Kevin P., 1970-, Machine Learning: A Probabilistic Perspective. Cambridge, MA, MIT Press, 2012.
*   [www.youtube.com/playlist?list=PL3uLubnzL2Tl-7fugIeCk4-l4HVVdn5\_v](http://www.youtube.com)
*   [https://jupyter.org/](https://jupyter.org)
*   [www.intel.com/content/www/us/en/developer/tools/devcloud/overview.html](http://www.intel.com)
*   Intel Developer Cloud – [https://youtu.be/Mk\_DjL3ZUVo](https://youtu.be)

## Key points to remember

1.  Machine learning is a branch of AI, which can help a machine learn and act imitating intelligent human behavior.
2.   AI is the broader umbrella and machine learning and deep learning comes under them. All of them are related to each other.
3.  Machine learning algorithms are categorized as supervised learning, unsupervised learning, and reinforcement learning. Evolutionary learning algorithms make use of genetic algorithms.
4.  Supervised learning algorithms use labelled data set. They have a training phase to model and a testing phase to predict or classify the data. This is a classification problem.
5.   Unsupervised learning algorithms don’t use labelled data; they categorize data into groups or clusters. This is a clustering algorithm.
6.  Reinforcement learning gets feedback from the environment using computer agents and action and best utilize the parameters for optimal rewards.
7.  Machine learning can perform adaptive learning, to bring in the best accuracy to the process, can take the feedback and make the process less error prone, and use them for recurrent tasks.
8.  Machine learning framework mainly includes the following steps: data collection, data analysis, model building, testing the model, visualization, and results interpretation.
9.  Machine learning uses ML algorithms to predict or classify the data whereas DL uses neural networks and its hidden layers to provide the output, which makes it a bit hard to understand and find the inferences.
10.  Machine learning has many applications in various sectors like retail, agriculture, finance, healthcare, education, energy, government etc., apart from these FB recommending you friends, Amazon and Flipkart recommending you the products, Netflix movie recommendations etc.

# Chapter 1Exploring the Iris dataset

DOI: [10.1201/9781032676685-2](http://doi.org/10.1201/9781032676685-2)

## Learning objectives

By the end of this chapter, the reader should be able to:

*   Obtain hands-on experience with machine learning (ML) techniques.
*   Build an understanding of how to tackle comparable tasks and improve their knowledge of certain algorithms.
*   Learn the essentials of working with a dataset, including how to load a dataset and examine its structure, as well as how to visualize the data patterns and relationships.
*   Develop a strong basis in exploring ML projects and understand the benefits and drawbacks of various algorithms.

## 1.1 Introduction

In this chapter, we will set out on an adventure to investigate the Iris dataset and gain some understanding in the field of machine learning (ML). We will be able to classify Iris blooms using a variety of ML methods after doing analysis on this well-known dataset. This will allow us to understand the structure of the dataset, perform visualizations, and more.

The dataset is openly available in Kaggle datasets and readers can access it through this link: [www.kaggle.com/datasets/uciml/iris](http://www.kaggle.com)

## 1.1 The beginning

To get started, let us proceed by loading the Iris data set as well as importing the required libraries.

In the code fragment snippet shown in [Figure 1.1](#ch08.xhtml#f27), the NumPy, Pandas, Seaborn, and Matplotlib libraries are imported. Additionally, we import the dataset Iris to a Pandas DataFrame titled “iris.”

![Figure 1.1Loading the dataset and importing the libraries.](html/images/9781032676654_C001_001.jpg)

[Figure 1.1](#ch08.xhtml#f27b)Loading the dataset and importing the libraries.

## 1.2 Examining the data

Let us investigate the structure of the Iris dataset in order to obtain some understanding of the data now that has been loaded.

We are able to retrieve information regarding the dataset by utilizing the *info()* method, including the data types and the amount of values that are not null contained within each column. With the *head()* method, we are able to investigate the initial five rows of the dataset (see [Figure 1.2](#ch08.xhtml#f28)).

![Figure 1.2Retrieving information from the dataset.](html/images/9781032676654_C001_002.jpg)

[Figure 1.2](#ch08.xhtml#f28b)Retrieving information from the dataset.

## 1.3 Dataset visualization

When it comes to comprehending data patterns and relationships, visualizations are of critical importance. Let us make some visuals in order to obtain some understanding of the Iris dataset.

The first type of representation is a boxplot, and it shows how the Sepal and Petal lengths of the flowers are distributed across the sample ([Figure 1.3](#ch08.xhtml#f29)). It gives information about the range, median, and possible anomalies or outliers in the dataset. The second type of representation is a histogram, which illustrates the distribution of the different species of Iris ([Figure 1.4](#ch08.xhtml#f30)). We improve the histogram’s overall aesthetic appeal by making it have red edges and setting the linewidth as 2.

![Figure 1.3Boxplot visualization.](html/images/9781032676654_C001_003.jpg)

[Figure 1.3](#ch08.xhtml#f29b)Boxplot visualization.

![Figure 1.4Histogram visualization.](html/images/9781032676654_C001_004.jpg)

[Figure 1.4](#ch08.xhtml#f30b)Histogram visualization.

## 1.4 Classification using machine learning (ML) algorithms

Let us apply some machine learning techniques to the task of finding the iris flowers. We are going to apply three different algorithms: Logistic Regression (LR), Support Vector Machines (SVM), and Decision Trees.

You can use the following code to delete the column from the dataset if you want to remove the column yourself. We eliminate the “Id” column from the Iris dataset as it is not needed for the classification task.

The column in question is removed from the DataFrame by utilizing the *drop()* function, which can be seen in action in the following line of code. Providing it as the initial value causes the “Id” column to be removed from the result. When the *axis=1* parameter is used, it indicates that the action should be carried out in a column-wise fashion. In the end, the *inplace=True* parameter is provided to guarantee that the modifications will be reflected in the initial DataFrame (See [Figure 1.5](#ch08.xhtml#f31)).

![Figure 1.5Column removal.](html/images/9781032676654_C001_005.jpg)

[Figure 1.5](#ch08.xhtml#f31b)Column removal.

When this piece of code as in [Figure 1.5](#ch08.xhtml#f31) is executed, the “Id” field will be properly removed from the Iris dataset. This will ensure that our modeling and analysis tasks do not contain any superfluous information.

Use this code in order to import the essential machine learning components from scikit-learn.

The following packages and classes are brought in via import within this chunk of code as provided in [Figure 1.6](#ch08.xhtml#f32).

![Figure 1.6Code snippet to import ML components.](html/images/9781032676654_C001_006.jpg)

[Figure 1.6](#ch08.xhtml#f32b)Code snippet to import ML components.

*   *LogisticRegression* is derived from sklearn.linear\_model and is a classification approach that is quite popular. This type offers functionality for logistic regression.
*   *train\_test\_split* is a function that is derived from sklearn.model\_selection. With the help of this function, we are able to divide the dataset into a training set and a testing set.
*   *KNeighborsClassifier* is found in the sklearn.neighbors package. It is utilized by the k-nearest neighbors classification technique.
*   *svm* module from sklearn supplies classification and regression techniques for use with support vector machines.
*    *metrics* is derived from the sklearn library. This module includes a variety of metrics for assessing the effectiveness of ML models.
*   *DecisionTreeClassifier* is a popular classification approach based on decision trees. It comes from the sklearn.tree library.

Importing these modules and classes will provide you with access to the essential tools for creating and evaluating various ML algorithms on the Iris dataset. We will apply these algorithms to the dataset.

You may use the following piece of code ([Figure 1.7](#ch08.xhtml#f33)) to divide the Iris dataset into training and testing sets by employing the *train\_test\_split* function provided by scikit-learn, and then report the shape of the sets that are produced as a result.

![Figure 1.7Code snippet to divide the dataset.](html/images/9781032676654_C001_007.jpg)

[Figure 1.7](#ch08.xhtml#f33b)Code snippet to divide the dataset.

The iris DataFrame is to be partitioned into training and testing sets. The *test\_size* parameter set to 0.3 indicates that 30 percent of the data is assigned to the testing set, while 70 percent of the data is for the training set.

After the data has been split, the form of the set used for training is printed utilizing the *shape* property of the *train* DataFrame, and then the testing set is printed utilizing the *shape* attribute of the *test* DataFrame. This is followed by printing the shape of the entire data set. This gives you the ability to check the lengths of the sets that are produced as a result.

When this code as in [Figure 1.7](#ch08.xhtml#f33) is executed, the Iris dataset will be partitioned into a training set and a testing set, with the corresponding shape of the sets displayed.

The training set’s training features (*train\_x*) along with training labels (*train\_y*) are extracted here in this code block (see [Figure 1.8](#ch08.xhtml#f34)). On the other hand, the testing features (*test*\_ *x*) and testing labels (*test\_y*) are taken from the testing set and extracted here. The characteristics are chosen in accordance with the columns labeled “SepalLengthCm,” “SepalWidthCm,” “PetalLengthCm,” and “PetalWidthCm,” respectively.

![Figure 1.8Code snippet for extracting features.](html/images/9781032676654_C001_008.jpg)

[Figure 1.8](#ch08.xhtml#f34b)Code snippet for extracting features.

A version of the Support Vector Machine (SVM) classification is built here using the *svm.SVC*() function. After that, the *fit*() method is called, and the model is trained by making use of the training data (*train\_ x* and *train\_y*). The *predict*() method is then used to make predictions based on the training model regarding the labels that should be assigned to the test features (*test*\_*x*). The correctness of the SVM model is determined with the *accuracy\_score*() function included in the *metrics* module to compare the labels that are predicted with the actual labels (*test\_y*). The determined accuracy score is printed underneath (see [Figure 1.9](#ch08.xhtml#f35)).

![Figure 1.9Code snippet for SVM classification.](html/images/9781032676654_C001_009.jpg)

[Figure 1.9](#ch08.xhtml#f35b)Code snippet for SVM classification.

In a similar fashion, a version of the Logistic Regression (LR) classification is generated by calling the *LogisticRegression*() function. The model is then trained and evaluated in the same way to that of the previous SVM classification. In addition to that, the accurateness of the LR strategy is also printed (see [Figure 1.10](#ch08.xhtml#f36)).

![Figure 1.10Code snippet for LR classification.](html/images/9781032676654_C001_010.jpg)

[Figure 1.10](#ch08.xhtml#f36b)Code snippet for LR classification.

By following the code snippet as in [Figure 1.11](#ch08.xhtml#f37), a version of the Decision Tree classification called *DecisionTreeClassifier*() is generated. The model is then trained and assessed in the same manner to that of the previous two models. The reliability of the Decision Tree concept is also displayed at the end.

![Figure 1.11Code snippet for Decision Tree classification.](html/images/9781032676654_C001_011.jpg)

[Figure 1.11](#ch08.xhtml#f37b)Code snippet for Decision Tree classification.

Finally, the program generates a bar plot in order to contrast the degrees of accuracy achieved by each of the three models. The accuracy list stores the scores that match to the model names that are stored in the *model\_name* list. The model’s names are stored in the *accuracy* list (see [Figure 1.12](#ch08.xhtml#f38)). The bar plot is produced by the *barplot*() function, which can be found within the seaborn library. The map produced as a result provides a visual representation of the accuracy of the comparisons between the chosen three models.

![Figure 1.12Code snippet to create accuracy scores.](html/images/9781032676654_C001_012.jpg)

[Figure 1.12](#ch08.xhtml#f38b)Code snippet to create accuracy scores.

When the code as in [Figure 1.13](#ch08.xhtml#f39) is executed, it will show the accuracy values of the SVM, Logistic Regression, and Decision Tree models, in addition to the bar plot that compares the accuracy levels of the three models respectively.

![Figure 1.13Code snippet to create accuracy scores and accuracy comparison.](html/images/9781032676654_C001_013.jpg)

[Figure 1.13](#ch08.xhtml#f39b)Code snippet to create accuracy scores and accuracy comparison.

## 1.5 Inferences

After carrying out an analysis of the accuracy levels of the chosen three models, we can infer that the SVM model obtains the highest level of accuracy, with Logistic Regression coming in a close second. In comparison to the other two models, the Decision Tree model offers a somewhat lower accuracy, however it is still reasonably accurate overall. We are able to make educated judgments about which approach is best suited for classifying Iris species of flowers based on the available attributes by contrasting and evaluating the accuracies of various models. This allows us to make informed choices about the paradigm that is ideally suited for classifying Iris flower species.

## 1.6 Future learning

With the information acquired in this chapter as a foundation, there are a number of fascinating avenues of research that can be pursued using the same or different datasets. The following are some potential areas that need to be taken into consideration: Advanced Feature Engineering methods to experiment with extra feature engineering techniques in order to boost the predictive capacity of the models. Investigate the domain-specific expertise you need to create new features, or think about altering the features you already have to gather additional relevant information from them. Investigation of several types of ensemble learning approaches, such as Random Forests, Gradient Boosting, or Stacking, can be done with the help of Ensemble Methods. Investigate how combining several classification models can increase the accuracy and resilience of the results.

## Suggested readings

*   Flake, G.W. and Lawrence, S., 2002. Efficient SVM regression training with SMO. Machine learning, *46*, pp.271–290.
*   Friedrichs, F. and Igel, C., 2005. Evolutionary tuning of multiple SVM parameters. Neurocomputing, *64*, pp.107–117.
*   Wang, Q.Q., Yu, S.C., Qi, X., Hu, Y.H., Zheng, W.J., Shi, J.X. and Yao, H.Y., 2019. Overview of logistic regression model analysis and application. *Zhonghua yu fang yi xue za zhi* \[Chinese Journal of Preventive Medicine\], *53*(9), pp.955–960.

# Chapter 2Heart failure prediction with oneAPI

DOI: [10.1201/9781032676685-3](http://doi.org/10.1201/9781032676685-3)

## Learning objectives

By the end of this chapter, the reader should be able to:

*   Explore the means of predicting heart failure by employing ML models and making use of the power provided by Intel’s oneAPI framework.
*   Use the oneDAL and oneDNN libraries that come along with the oneAPI.
*   Obtain insights into predictive modeling and be in a position to apply those insights to comparable initiatives in the field of healthcare.
*   Grasp the methods and algorithms that are used in the chapter.

## 2.1 Introduction

The process of investigating and analyzing data, developing models with a variety of methods, and evaluating the efficacy of these models in predicting heart failure will be covered in detail throughout this chapter. Building prediction models and gaining insights into this important area of healthcare will be accomplished with the help of a dataset on heart failure that is accessible to the general public. The link to the dataset is [www.kaggle.com/datasets/andrewmvd/heart-failure-clinical-data](http://www.kaggle.com)

This chapter will improve both your theoretical understanding and practical competency in predictive modeling for heart failure prediction. You will have a better understanding of the significance of early diagnosis and precise prognosis in the process of bettering the outcomes for patients. In addition, you will gain an understanding of how to utilize well-known ML methods for heart failure prediction. The algorithms include random forest, XGBoost, and convolutional neural networks. You will also learn the benefits of leveraging Intel’s oneAPI libraries, such as oneDAL and oneDNN, to optimize code, improve efficiency, and take advantage of hardware acceleration in order to boost performance.

Intel’s oneAPI programming style and framework simplifies software development and optimizes performance across hardware architectures. oneAPI lets developers design code that runs efficiently on CPUs, GPUs, FPGAs, and other accelerators without major adjustments. This framework lets developers use hardware acceleration to accelerate computations with performance-optimized libraries like oneDAL and oneDNN. In this chapter, we optimize our code using oneAPI to improve the heart failure prediction models.

## 2.2 Importing libraries

In this part, we import the libraries, which will be employed to work with data, analyze it, and build models that can predict what will happen. Each library has its own goal and gives us useful functions and classes to help us do our task.

*   The pandas library gives us strong tools for manipulating and analyzing data, which makes it easy to work with structured data. The numpy library possess lot of math tools and makes it easy to do numerical calculations on arrays and matrices.
*   We use the sklearn.model\_selection module’s train\_test\_split function to split the dataset into training and testing sets. This is very important for figuring out how well our models work on new data.
*   We bring in the RandomForestClassifier class from the sklearn.ensemble package to build a random forest classifier model. Random forests are a type of ensemble learning that makes correct predictions by putting together several decision tree models.
*   We add in the xgboost tool to do gradient boosting. Gradient boosting is used in XGBoost, which is a high-performance and efficient version of gradient boosting.
*   In deep learning (DL), we use the tensorflow.keras.models package to bring in the Sequential class. With the Sequential class, we can make a neural network model with levels that are stacked on top of each other.
*   Lastly, we bring in certain layers from the tensorflow.keras.layers package, such as Dense, Conv1D, MaxPooling1D, and Flatten. When making deep neural network architectures, these layers serve as the important building blocks.

Our code will be built on these imported packages, which will offer us the tools needed to analyze and model data well. The red bar below the code in [Figure 2.1](#ch09.xhtml#f40) depicts the optimization of oneDAL, oneDNN, and Xgboost libraries with oneAPI.

![Figure 2.1Importing the libraries.](html/images/9781032676654_C002_001.jpg)

[Figure 2.1](#ch09.xhtml#f40b)Importing the libraries.

## 2.3 Exploring the data

In this section, we will go into the exploration of the heart failure dataset in order to obtain insights and better understand the data properties. The process of identifying patterns, links, and potential problems in a dataset is referred to as “data exploration,” and it is a key stage in the ML pipeline.

We start by using the read\_csv() function of the pandas library (see [Figure 2.2](#ch09.xhtml#f41)) to load the heart failure dataset from a CSV file into a pandas DataFrame. Because of this, we are now able to efficiently organize and modify the data.

![Figure 2.2Code snippet to read and store the dataset.](html/images/9781032676654_C002_002.jpg)

[Figure 2.2](#ch09.xhtml#f41b)Code snippet to read and store the dataset.

We use the head() function to display the first few rows of the dataset so as to get an overview of the data (see [Figure 2.3](#ch09.xhtml#f42)). This clarifies the structure and format of the data for us, as well as the type of information that is stored in each column.

![Figure 2.3To obtain data overview.](html/images/9781032676654_C002_003.jpg)

[Figure 2.3](#ch09.xhtml#f42b)To obtain data overview.

The next step is to acquire an overall perspective of the dataset by utilizing the info() function (see [Figure 2.4](#ch09.xhtml#f43)). This gives us information on the data types that are contained within each column, as well as the total number of values that are not null. This is especially helpful in the identification of data that is either missing or incomplete.

![Figure 2.4To obtain data types.](html/images/9781032676654_C002_004.jpg)

[Figure 2.4](#ch09.xhtml#f43b)To obtain data types.

Utilizing the describe() function allows us to generate a statistical summary, which provides us with further insights into the dataset. This summary provides measurements for each numerical column, such as the mean, standard deviation, minimum, maximum, and quartiles. It gives a detailed picture of the distribution of values within the dataset as well as the range of those values (see [Figure 2.5](#ch09.xhtml#f44)).

![Figure 2.5To generate a statistical summary.](html/images/9781032676654_C002_005.jpg)

[Figure 2.5](#ch09.xhtml#f44b)To generate a statistical summary.

## 2.3 Modeling phase

During the modeling phase, we incorporate optimization libraries into our workflow in order to improve the overall performance of the models. The oneDNN library is used in the optimization of the CNN model, whilst the oneDAL library is used in the optimization of the Random Forest model, both of which are performed within the context of the oneAPI framework.

In this section of code as in [Figure 2.6](#ch09.xhtml#f45), in order to separate the data, we make use of the train\_test\_split function that is available in the sklearn.model\_selection module. We use the expression df.drop (‘DEATH\_EVENT’, axis=1) to represent the characteristics (X), and we use df \[‘DEATH\_EVENT\] to represent the target variable (y). The test\_size parameter, which determines the percentage of the data that will be allocated for testing, has its default value set to 0.2 (or 20%). The reproducibility of the split may be guaranteed thanks to the random\_state argument.

![Figure 2.6Code snippet to divide the dataset.](html/images/9781032676654_C002_006.jpg)

[Figure 2.6](#ch09.xhtml#f45b)Code snippet to divide the dataset.

After the data has been partitioned into the training set and the testing set, we are able to begin the process of instructing the models using the appropriate datasets.

### 2.3.1 Convolutional neural network (CNN)

To begin, we employ a convolutional neural network (CNN) in order to identify spatial correlations within the data. Convolutional layers, max pooling layers, and a dense layer are some of the components that make up the CNN model architecture. The CNN model is enhanced with the help of the oneDNN library; the red colored pop up in [Figure 2.7](#ch09.xhtml#f46) tells us that the Tensorflow binary is optimized with oneAPI Deep Neural Network Library. This library comes with DL calculations that is well optimized. It offers effective implementations of fundamental neural network operations such as convolution, pooling, and activation functions, among others. When the CNN model makes use of the oneDNN library, it is able to make use of calculations that have been optimized, which results in training and inference both being quicker and more efficient.

![Figure 2.7Defining CNN model architecture.](html/images/9781032676654_C002_007.jpg)

[Figure 2.7](#ch09.xhtml#f46b)Defining CNN model architecture.

![Figure 2.8Code snippet for training the model.](html/images/9781032676654_C002_008.jpg)

[Figure 2.8](#ch09.xhtml#f47b)Code snippet for training the model.

The model is compiled using the Adam optimizer and the binary cross entropy loss function, and we monitor the accuracy metric.

### 2.3.2 Random Forest classifier

Next, we begin the process of constructing a model by utilizing the Random Forest Classifier technique (see [Figures 2.8](#ch09.xhtml#f47) and [2.9](#ch09.xhtml#f48)). The Random Forest method of ensemble learning integrates the results of several different decision trees in order to produce predictions. The oneDAL library, also known as the oneAPI Data Analytics Library, is utilized in the process of optimizing the Random Forest model. This library is a component of the oneAPI framework. oneDAL is developed to speed up the processes of data analytics and provides optimized implementations of a number of different ML techniques, one of which being Random Forest.

![Figure 2.9Random Forest Classifier.](html/images/9781032676654_C002_009.jpg)

[Figure 2.9](#ch09.xhtml#f48b)Random Forest Classifier.

### 2.3.3 XGBoost classifier

The final step that we do is to use the XGBoost Classifier, which is a streamlined version of the gradient-boosting algorithm. In a wide variety of machine learning applications, XGBoost has earned a reputation for its precision and performance (refer to [Figure 2.10](#ch09.xhtml#f49)).

![Figure 2.10XGBoost Classifier.](html/images/9781032676654_C002_010.jpg)

[Figure 2.10](#ch09.xhtml#f49b)XGBoost Classifier.

## 2.4 Results and discussion

We will evaluate the outcome of the trained models and conduct an analysis of the results received from the heart failure prediction task in this section. We will evaluate how accurate each model is, as well as compare the models’ overall performance.

The correctness of each model is calculated and displayed using the code as in [Figure 2.11](#ch09.xhtml#f50). To determine how well the models can anticipate the incidence of heart failure, we use accuracy as a statistic to gauge how well they do so. When it comes to prediction, higher accuracy signifies better performance.

![Figure 2.11Model evaluation.](html/images/9781032676654_C002_011.jpg)

[Figure 2.11](#ch09.xhtml#f50b)Model evaluation.

A bar plot can be used to visually represent the accuracy scores, which allows us to conduct additional research into the performance of the models and make direct comparisons between them (see [Figure 2.12](#ch09.xhtml#f51)).

![Figure 2.12Plotting model accuracy.](html/images/9781032676654_C002_012.jpg)

[Figure 2.12](#ch09.xhtml#f51b)Plotting model accuracy.

The accuracy ratings of the three models are presented in the form of a bar plot in [Figure 2.12](#ch09.xhtml#f51), which enables a speedy visual comparison of the respective levels of performance.

## 2.5 Future learning

While this chapter does provide some useful insights on predicting heart failure with the help of ML and Intel’s oneAPI, there are still a number of potential areas where additional work and improvements might be made. The following are some probable regions that could be investigated in the future. Investigate any other features or data sources that could be able to supply more thorough information for the purpose of heart failure prediction. To improve the accuracy of the models’ ability to predict outcomes, you might want to think about including genetic data, lifestyle factors, or other pertinent biomarkers. Techniques requiring advanced ML conduct research on more advanced ML algorithms and methods to see if these can produce better results for heart failure prediction. For instance, in order to capture temporal dependencies in patient data, one could use DL architectures such as recurrent neural networks (RNNs) or transformers. Model Optimization ensure the models are continuously optimized so that their precision and effectiveness can be increased. To determine which hyper parameter tuning strategies, model ensembles, or regularization methods produce the best results for each algorithm, you should do some experiments.

## Suggested readings

*   Alzubaidi, L., Zhang, J., Humaidi, A.J., Al-Dujaili, A., Duan, Y., Al-Shamma, O., Santamaría, J., Fadhel, M.A., Al-Amidie, M. and Farhan, L., 2021. Review of deep learning: Concepts, CNN architectures, challenges, applications, future directions. Journal of Big Data, *8*, pp.1–74.
*   Osman, A.I.A., Ahmed, A.N., Chow, M.F., Huang, Y.F. and El-Shafie, A., 2021. Extreme gradient boosting (Xgboost) model to predict the groundwater levels in Selangor Malaysia. Ain Shams Engineering Journal, *12*(2), pp.1545–1556.
*   Sheridan, R.P., 2013. Using random forest to model the domain applicability of another random forest model. Journal of Chemical Information and Modeling, *53*(11), pp.2837–2850.

# Chapter 3Handling water quality dataset

DOI: [10.1201/9781032676685-4](http://doi.org/10.1201/9781032676685-4)

## Learning objectives

After completing this chapter, the reader shall be able to:

*   Conduct an analysis of a water quality dataset in order to make accurate predictions regarding the potability of water.
*   Acquire insights into the process of evaluating the safety of water by investigating the dataset, preprocess the data, deal with missing values, and construct ML models.

## 3.1 Introduction

The goals are to provide readers with the information and abilities necessary to work with datasets pertaining to water quality, comprehend the difficulty posed by class imbalance, and implement ML algorithms for predicting the potability of water. The readers can find the dataset in the following link: [www.kaggle.com/datasets/adityakadiwal/water-potability](http://www.kaggle.com)

## 3.2 The class imbalance problem

The problem of class imbalance is one of the challenges that frequently arises in the context of ML initiatives. Class imbalance is a circumstance in which the classes in the target variable are not uniformly distributed, with one class having a significantly lesser number of samples compared to the other class(es), as well as any further classes that might exist. This might happen in the context of evaluating the quality of the water when the number of water samples that are regarded to be acceptable for human consumption (class 1) is a significantly lower number than the number of samples that are considered to be harmful (class 0).

Dealing with class imbalance is crucial because it can lead to biased models that give priority to the class that holds the majority of the population and perform badly when it comes to accurately predicting the class that holds the minority of the population. In order to guarantee accurate and trustworthy forecasts, we address the issue of class imbalance in the dataset pertaining to water quality in this chapter.

We use a pie chart to depict the distribution of the “Potability” classes in order to assess and overcome class imbalance. This helps us identify the imbalance between the safe and hazardous water samples, which is necessary for overcoming the problem. In order to solve this problem, it is ultimately decided to use resampling techniques. In order to achieve a dataset that is more evenly distributed, resampling may involve either oversampling the minority class (which would result in an increase in its representation) or under sampling the majority class (which would result in a reduction in its representation). We get rid of any possible biases that might have been caused by the order in which the data are presented by shuffling the dataset.

The reader will develop a better understanding of the class imbalance problem throughout the course of this chapter, as well as the significance of addressing it in an effective manner. Readers will learn how to generate a balanced dataset that provides equal representation of both safe and unsafe water samples by making use of resampling techniques. This will result in more accurate and dependable ML models for the prediction of water potability.

## 3.3 Dataset overview

In this part, we import all the required libraries, read the data from the CSV file into a DataFrame, and show the first five rows of the dataset (see [Figure 3.1](#ch10.xhtml#f52)).

![Figure 3.1Importing the libraries.](html/images/9781032676654_C003_001.jpg)

[Figure 3.1](#ch10.xhtml#f52b)Importing the libraries.

### 3.3.1 Preprocessing the data

In this part, we deal with values that are absent in the dataset by adding the amount of missing data in every column and removing rows that have any missing values. The code snippet of the same is provided in [Figure 3.2](#ch10.xhtml#f53).

![Figure 3.2Solving the missing values in the dataset.](html/images/9781032676654_C003_002.jpg)

[Figure 3.2](#ch10.xhtml#f53b)Solving the missing values in the dataset.

We use the isnull().sum() method to determine the amount of missing values in each column so that we can solve the issue of missing values in the dataset. This will provide us with a summary of the values that are missing from the dataset. We have decided to drop rows that include any missing values by using the dropna() method. This will allow us to ensure that the data is accurate and consistent. By carrying out these procedures, we have gotten an initial overview of the dataset pertaining to the water quality, which includes its structure as well as the way it deals with missing values. In the following sections, we are going to look deeper into the class imbalance problem that is present in the dataset and investigate different methods that can be used to overcome it.

### 3.3.2 Class imbalance and oversampling

In this section, we will discuss the problem of class imbalance found in the dataset pertaining to water quality. When the classes in the target variable do not correspond equally to one another, it is known as class imbalance. In this instance, the “Potability” factor has classes that are not balanced, with one class having a substantially lower number of samples than the other class. We are going to make a pie chart to illustrate the distribution of the “Potability” classes so as to have a better idea of the class imbalance. This will assist us in gaining a better understanding of the distribution of each class within the dataset. The distribution of the students in the class can be seen in more detail using the pie chart as depicted in [Figure 3.3](#ch10.xhtml#f54).

![Figure 3.3Pie chart visualization.](html/images/9781032676654_C003_003.jpg)

[Figure 3.3](#ch10.xhtml#f54b)Pie chart visualization.

We are able to view the percentage of each class, where “0” indicates water samples that are not suitable for human consumption and “1” indicates the water samples suitable for human consumption (see [Figure 3.4](#ch10.xhtml#f55)).

![Figure 3.4To view the percentage of each class.](html/images/9781032676654_C003_004.jpg)

[Figure 3.4](#ch10.xhtml#f55b)To view the percentage of each class.

We can see that there is a disparity between the classes using this graph. We take a larger sample size from the minority group so that we can address this issue utilizing resampling methods (see [Figure 3.5](#ch10.xhtml#f56)). This helps to guarantee that the classes are more evenly distributed for model training. Last but not least; we shuffle up the dataset to eliminate any specific sequence biases.

![Figure 3.5Code snippet to utilize resampling methods.](html/images/9781032676654_C003_005.jpg)

[Figure 3.5](#ch10.xhtml#f56b)Code snippet to utilize resampling methods.

From the pie chart shown in [Figure 3.6](#ch10.xhtml#f57), it is evident that after resampling we have solved the class imbalance problem.

![Figure 3.6Pie chart visualization after resampling.](html/images/9781032676654_C003_006.jpg)

[Figure 3.6](#ch10.xhtml#f57b)Pie chart visualization after resampling.

### 3.3.3 Exploratory data analysis

We generate a heatmap of the correlation matrix by utilizing seaborn to acquire new insights into the links that exist between the variables (see [Figure 3.7](#ch10.xhtml#f58)).

![Figure 3.7Generating a heatmap of the correlation matrix.](html/images/9781032676654_C003_007.jpg)

[Figure 3.7](#ch10.xhtml#f58b)Generating a heatmap of the correlation matrix.

The heatmap that is produced as a result enables us to find relationships between various water quality characteristics. By conducting an analysis of the correlation values, we can gain a deeper comprehension of the dynamic relationship that exists between the variables and the potential influence that these variables have on the potability of the water.

### 3.3.4 Data splitting and model training

Next, we employ the train\_test\_split function that is part of the scikit-learn package to divide the dataset into a training set and a testing set. In addition to this, we import the necessary models for ML as shown in the code snippet of [Figure 3.8](#ch10.xhtml#f59).

![Figure 3.8Splitting the dataset.](html/images/9781032676654_C003_008.jpg)

[Figure 3.8](#ch10.xhtml#f59b)Splitting the dataset.

Next, we are going to proceed with the process of training and evaluating three distinct ML models, namely Logistic Regression, Gaussian Naive Bayes, and Decision Tree Classifier.

## 3.4 Logistic regression

The Logistic Regression algorithm is a common choice for use in binary classification projects. First, a new instance of the Logistic Regression model is created, and then it is trained using the provided training data. After that, we determine the trained model’s performance on the testing data by computing its accuracy (see [Figure 3.9](#ch10.xhtml#f60)).

![Figure 3.9Employing Logistic Regression algorithm.](html/images/9781032676654_C003_009.jpg)

[Figure 3.9](#ch10.xhtml#f60b)Employing Logistic Regression algorithm.

## 3.5 Gaussian Naive Bayes

A probabilistic approach frequently utilized for classification work is the Gaussian Naive Bayes. First, a fresh instance of the GaussianNB model is constructed, and then it is educated using the training data. After that, we compute the trained model’s performance on the testing data and see how accurate it is (see [Figure 3.10](#ch10.xhtml#f61)).

![Figure 3.10Employing Gaussian Naive Bayes algorithm.](html/images/9781032676654_C003_010.jpg)

[Figure 3.10](#ch10.xhtml#f61b)Employing Gaussian Naive Bayes algorithm.

## 3.6 Decision tree classifier

The Decision Tree Classifier is a flexible method that can handle classification as well as regression work. It is named after the decision tree that it is based on. We start by generating a fresh instance of the Decision Tree Classifier model, and then we train it using the provided training data. After that, we determine the accuracy of the trained model based on the testing data by using the following code as provided in [Figure 3.11](#ch10.xhtml#f62). The model comparison is presented in [Figure 3.12](#ch10.xhtml#f63).

![Figure 3.11Employing Decision Tree Classifier algorithm.](html/images/9781032676654_C003_011.jpg)

[Figure 3.11](#ch10.xhtml#f62b)Employing Decision Tree Classifier algorithm.

## 3.7 Comparison of models

We use the matplotlib library to build a bar plot to evaluate and contrast the accuracy of the various models. We can establish which model performs the best in predicting the potability of water based on the accuracy scores.

![Figure 3.12Model comparison.](html/images/9781032676654_C003_012.jpg)

[Figure 3.12](#ch10.xhtml#f63b)Model comparison.

We have determined that the Logistic Regression model performs the best in predicting the potability of water with an accuracy of approximately 86.45 percent.

## 3.8 Further learning

We have used machine learning to predict the water potability. We preprocess and handle the missing values first. Exploratory data analysis reveals feature connections in the water quality. We then employ Logistic Regression, Gaussian Naive Bayes, and Decision Tree Classifier models using training and testing sets and the best model is found by comparing their accuracy. This study delivers water quality forecast information that can improve community water safety decision-making.

Explore additional machine learning algorithms, optimize the model, or collect more diverse and comprehensive water quality datasets to further improve the water potability forecast accuracy and dependability.

## Suggested readings

*   Bi, Z.J., Han, Y.Q., Huang, C.Q. and Wang, M., 2019, July. Gaussian naive Bayesian data classification model based on clustering algorithm. In 2019 International Conference on Modeling, Analysis, Simulation Technologies and Applications (MASTA 2019) (pp. 396–400). Atlantis Press.
*   Dayton, C.M., 1992. Logistic regression analysis. Stat, *474*, p.574.
*   Japkowicz, N. and Stephen, S., 2002. The class imbalance problem: A systematic study. Intelligent Data Analysis, *6*(5), pp.429–449.
*   Priyam, A., Abhijeeta, G.R., Rathee, A. and Srivastava, S., 2013. Comparative analysis of decision tree classification algorithms. International Journal of Current Engineering and Technology, *3*(2), pp.334–337.

# Chapter 4Breast cancer classification with hybrid ML models

DOI: [10.1201/9781032676685-5](http://doi.org/10.1201/9781032676685-5)

## Learning objectives

After finishing this chapter, the reader shall be able to:

*   Make a prediction if the given sample in a dataset is benign or malignant.
*   Utilize few well-known ML algorithms in the construction of hybrid models.
*   Integrate several algorithms for improved predictive modeling.

## 4.1 Introduction

In this chapter, we will investigate the idea behind hybrid ML models. Kaggle has provided us with the Wisconsin Breast Cancer Dataset, which we will be using in our work. The purpose of this dataset is to make a prediction as to whether a given sample is benign (meaning it is not cancerous) or malignant (meaning it is cancer). Hybrid models are models that integrate different machine learning algorithms in order to capitalize on the characteristics of each individual method, which may result in enhanced performance and accuracy. k-Nearest Neighbors (k-NN), Support Vector Machine (SVM), and Random Forest are three well-known algorithms that will be utilized in the construction of hybrid models that we will focus on. You will have an understanding of the principles of hybrid machine learning models by the time you reach the conclusion of this chapter, as well as how to integrate several algorithms for improved predictive modeling. Readers can find the dataset in the following link: [www.kaggle.com/datasets/uciml/breast-cancer-wisconsin-data](http://www.kaggle.com)

## 4.2 Data preparation

### 4.2.1 Importing libraries and loading data

To get things rolling, we need to begin by importing the required libraries for our work. We will be handling the data with pandas, performing numerical computations with numpy, and developing machine learning models with scikit-learn.

Afterwards, utilizing the read\_csv() function as in [Figure 4.1](#ch11.xhtml#f64), we will import the data that is included within a CSV file to the pandas DataFrame. See [Figure 4.2](#ch11.xhtml#f65).

![Figure 4.1Utilizing the read\_csv() function.](html/images/9781032676654_C004_001.jpg)

[Figure 4.1](#ch11.xhtml#f64b)Utilizing the read\_csv() function.

![Figure 4.2Importing the data.](html/images/9781032676654_C004_002.jpg)

[Figure 4.2](#ch11.xhtml#f65b)Importing the data.

### 4.2.2 Exploratory data analysis

It is essential to carry out some preliminary examination of the data before beginning the modeling process. In order to comprehend and understand the data and its structure, we can make use of a variety of pandas functions. For instance, the head() function as provided in the code snippet of [Figure 4.3](#ch11.xhtml#f66) will show us the first five rows of the DataFrame; we may use head(10) to see the first 10 rows from the dataframe according to our convenience.

![Figure 4.3Illustration of pandas function.](html/images/9781032676654_C004_003.jpg)

[Figure 4.3](#ch11.xhtml#f66b)Illustration of pandas function.

In order to deal with values which are not available in the dataset, we use the method isnull().sum() to search for any instances of null values. This gives the total amount of missing values that are present across all the columns in the DataFrame. To prevent biased or inaccurate predictions from being made, it is essential to manage missing data in an appropriate manner before training the models. See [Figure 4.4](#ch11.xhtml#f67).

![Figure 4.4To manage the missing data.](html/images/9781032676654_C004_004.jpg)

[Figure 4.4](#ch11.xhtml#f67b)To manage the missing data.

Next, we split the data into features (X) and the target variable (y) using the train\_test\_split() function from scikit-learn. The “X” DataFrame contains the features used for prediction, while the “y” Series contains the corresponding target values. We split the data into training and testing sets, with 80% for training and 20% for testing. The random state parameter ensures reproducibility of the split. See [Figure 4.5](#ch11.xhtml#f68).

![Figure 4.5Splitting the data.](html/images/9781032676654_C004_005.jpg)

[Figure 4.5](#ch11.xhtml#f68b)Splitting the data.

After we have split the data, the target variable will need to have its categorical values converted to numerical values ([Figure 4.6](#ch11.xhtml#f69)). We replace the values of “y” variable by using the LabelEncoder method from the scikit-learn library ([Figure 4.7](#ch11.xhtml#f70)). The letter “M” (for people who are affected by the disease = malignant) is substituted with 1, while the letter “B” (for people who are not affected by the disease = benign) is substituted with 0. In addition, we make use of the astype() method to change the data type of the “y” variable to an integer.

![Figure 4.6Numerical values conversion.](html/images/9781032676654_C004_006.jpg)

[Figure 4.6](#ch11.xhtml#f69b)Numerical values conversion.

![Figure 4.7Using LabelEncoder method.](html/images/9781032676654_C004_007.jpg)

[Figure 4.7](#ch11.xhtml#f70b)Using LabelEncoder method.

## 4.3 Scaling the features

It is possible that various machine-learning algorithms will have varying requirements for the magnitude of the features. In this step, we will scale the features so that they have an average value of zero and a variance of one using the StandardScaler tool that is part of scikit-learn ([Figure 4.8](#ch11.xhtml#f71)). We use the StandardScaler class included in scikit-learn to normalize the feature data so that we can conduct fair comparisons and prevent some characteristics from being very influential in the models. We start by fitting the scaler to the training data, and then we use the learned scaling factors to change both the training data and the testing data.

![Figure 4.8Code snippet to use the StandardScaler tool.](html/images/9781032676654_C004_008.jpg)

[Figure 4.8](#ch11.xhtml#f71b)Code snippet to use the StandardScaler tool.

## 4.4 Building hybrid ML models

In this chapter, we will construct distinct ML models by utilizing the methods known as Random Forest, Support Vector Machine (SVM), and k-Nearest Neighbors (k-NN). The aforementioned models will act as the foundation for our hybrid model, which will be based on them.

### 4.4.1 Random Forest + SVM model

We start by making a new object called VotingClassifier, which is a hybrid of the Random Forest and SVM classifiers. A list of tuples, each of which consisting of a string identifier and an object classifier, is what we send along as our input. The terms “rf” and “svm” will serve as the identifiers in this scenario. By utilizing the fit() method, we train the VotingClassifier using the provided data. Both the Random Forest and SVM classifiers are trained because of this. We use the predict() method to generate predictions on the testing data in order to evaluate the effectiveness of the hybrid model. We determine an accuracy score by contrasting the labels that are anticipated with the labels that appear. See [Figure 4.9](#ch11.xhtml#f72) for the code snippet.

![Figure 4.9Training a Random Forest + SVM Model.](html/images/9781032676654_C004_009.jpg)

[Figure 4.9](#ch11.xhtml#f72b)Training a Random Forest + SVM Model.

### 4.4.2 Random Forest + k-NN

Next, we use the K neighbors Classifier class provided by scikit-learn to generate an instance of the k-NN classifier. We make a new instance of the VotingClassifier object that uses a classification strategy that mixes Random Forest and k-NN. We train the VotingClassifier using the provided data. Based on the testing results, we formulate hypotheses and then compute an accuracy score. Refer to [Figure 4.10](#ch11.xhtml#f73) for the code snippet.

![Figure 4.10Training a Random Forest + k-NN Model.](html/images/9781032676654_C004_010.jpg)

[Figure 4.10](#ch11.xhtml#f73b)Training a Random Forest + k-NN Model.

### 4.4.3 SVM + k-NN

In a similar manner, we create an object called VotingClassifier that integrates both the SVM and the k-NN classifiers.We train the VotingClassifier using the provided data. Based on the testing results, we formulate hypotheses and then compute an accuracy score (see [Figure 4.11](#ch11.xhtml#f74)).

![Figure 4.11Training a SVM + k-NN Model.](html/images/9781032676654_C004_011.jpg)

[Figure 4.11](#ch11.xhtml#f74b)Training a SVM + k-NN Model.

 

## 4.5 Conclusion

This chapter focused on creating hybrid machine learning models, which we have discussed in depth. We have gained the knowledge necessary to preprocess the data, develop hybrid models by utilizing various combinations of classifiers, and evaluate the effectiveness of these models. We can increase the accuracy of our predictions as well as make use of the specific characteristics of each of the models by combining them. The information that has been learned in this chapter can be put to use when developing your own hybrid models for use in a variety of machine learning applications.

## 4.6 Further learning

Exploring feature-engineering techniques, conducting hyper parameter tuning, selecting appropriate base models, conducting experiments with applying cross-validation, and testing the model in real-life situations are some of the upcoming works and enhancements for hybrid machine-learning models. These efforts focus on enhancing the model’s performance, resilience, generalization ability, and practical usability, with the end goal of making it more effective at resolving complex issues across a variety of application areas.

## Suggested Readings

*   Atallah, D.M., Badawy, M., El-Sayed, A. and Ghoneim, M.A., 2019. Predicting kidney transplantation outcome based on hybrid feature selection and KNN classifier. Multimedia Tools and Applications, *78*, pp.20383–20407.
*   Demidova, L., Nikulchev, E. and Sokolova, Y., 2016. The SVM classifier based on the modified particle swarm optimization. arXiv, 1603.08296.
*   Gislason, P.O., Benediktsson, J.A. and Sveinsson, J.R., 2006. Random forests for land cover classification. Pattern Recognition Letters, *27*(4), pp.294–300.
*   Kavitha, M., Gnaneswar, G., Dinesh, R., Sai, Y.R. and Suraj, R.S., 2021, January. Heart disease prediction using hybrid machine learning model. In 2021 6th International Conference on Inventive Computation Technologies (ICICT) (pp.1329–1333). IEEE.

# Chapter 5Flower recognition with Kaggle dataset and Gradio interface

DOI: [10.1201/9781032676685-6](http://doi.org/10.1201/9781032676685-6)

## Learning objectives

By the end of this chapter, the reader shall be able to:

*   Acquire the knowledge to construct a machine learning model that can divide photographs into several distinct groups.
*   Obtain predictions based on their own models.
*   Integrate Gradio, a user-friendly interface library.

## 5.1 Introduction

We will use a dataset collected from Kaggle to explore the fascinating realm of flower recognition in this chapter. Flower recognition is a field that has been studied for centuries. Readers will get the knowledge necessary to construct a machine learning model that is able to divide photographs of flowers into five distinct groups by following the instructions provided. The procedure of immediately obtaining datasets from Kaggle, without the need for manual downloads, will be covered in this chapter, setting it apart from the others in the book and making it the focal point of what makes this chapter unique. In addition, we are going to investigate the possibility of integrating Gradio, which is a user-friendly interface library. Gradio gives users the ability to engage using the model and obtain predictions based on their own photographs of flowers. Readers will have received practical insights into image categorization, dataset collecting, and interacting with users with machine learning models by the time they reach the end of this chapter.

## 5.2 Downloading the dataset

The manual downloading and preparation of data has always been a necessary step in the process of getting datasets from external sources. On the other hand, we shall present the readers with a method that is more streamlined in this chapter. We no longer need to manually download the “flowers-recognition” dataset because we can immediately grab it from Kaggle using the OpenDatasets library instead of doing so manually. The process of data collecting is not only sped up because of this, but it also saves time.

Once you are done installing the necessary libraries as in [Figure 5.1](#ch12.xhtml#f75), follow these steps.

![Figure 5.1Installing necessary libraries.](html/images/9781032676654_C005_001.jpg)

[Figure 5.1](#ch12.xhtml#f75b)Installing necessary libraries.

*   Step 1: Go to [www.kaggle.com/](http://www.kaggle.com)
*   Step 2: Choose the dataset (in this chapter we used the flower recognition dataset).
*   Step 3: Copy the link [www.kaggle.com/datasets/alxmamaev/flowers-recognition](http://www.kaggle.com)

You can see we have used our dataset link in the above code as seen in [Figure 5.2](#ch12.xhtml#f76). As a next step, you will have to enter your Kaggle username and key once after executing the above code. Follow the steps mentioned below for your Kaggle username and key.

![Figure 5.2Importing the datasets.](html/images/9781032676654_C005_002.jpg)

[Figure 5.2](#ch12.xhtml#f76b)Importing the datasets.

*   Step 1: You can access your Kaggle account by going to the website [www.kaggle.com/](http://www.kaggle.com) and logging in there. Create an account for yourself if you do not already have one.
*   Step 2: After you have successfully logged in, navigate to the settings page for your account. You can access your Kaggle account by going to the top right corner of the website, clicking on your profile image, and then selecting “My Account” from the dropdown menu.
*   Step 3: To generate a new API token, scroll down until you reach the section labeled “API,” then click the option that says “Create New API Token.” This will cause a file with the name kaggle.json to be downloaded on your computer. It will contain your API credentials.

## 5.3 Data preprocessing

These lines of code as in [Figure 5.3](#ch12.xhtml#f77) will load the necessary libraries in order to build the machine learning model using TensorFlow, which involves data handling and visualization.

![Figure 5.3Code snippet to import libraries.](html/images/9781032676654_C005_003.jpg)

[Figure 5.3](#ch12.xhtml#f77b)Code snippet to import libraries.

In this step, we will determine the image size and set the path to the dataset. The path to the dataset downloaded is stored in the data\_dir variable, which has its value set to that path. img\_height and img\_width are the two parameters that indicate the length and width of the images being used and will be adjusted when the model is trained. Refer to [Figure 5.4](#ch12.xhtml#f78) for the code snippet.

![Figure 5.4Code snippet for image size and path setting.](html/images/9781032676654_C005_004.jpg)

[Figure 5.4](#ch12.xhtml#f78b)Code snippet for image size and path setting.

## 5.4 Creating the model architecture

In order to enrich the available data, we create an ImageDataGenerator as shown in [Figure 5.5](#ch12.xhtml#f79). TensorFlow’s ImageDataGenerator is a utility class that assists with data enhancement and data preprocessing. It may also be used to generate image data. The changes that are going to be applied to the photos, such as resizing, cutting, enlargement, and horizontally flipping the images, are defined by the parameters that are supplied in this section.

![Figure 5.5Code snippet for image data generation.](html/images/9781032676654_C005_005.jpg)

[Figure 5.5](#ch12.xhtml#f79b)Code snippet for image data generation.

These lines as in [Figure 5.6](#ch12.xhtml#f80) and [Figure 5.7](#ch12.xhtml#f81) utilize the flow\_from\_directory function of the ImageDataGenerator in order to load the training data and validation data respectively from the directory specified.

![Figure 5.6Code snippet for loading training data.](html/images/9781032676654_C005_006.jpg)

[Figure 5.6](#ch12.xhtml#f80b)Code snippet for loading training data.

![Figure 5.7Code snippet for loading validation data.](html/images/9781032676654_C005_007.jpg)

[Figure 5.7](#ch12.xhtml#f81b)Code snippet for loading validation data.

The photographs are shrunk down to the goal size set, and the batch size is what decides the number of images that are worked on during each iteration. Since we will be working with multi-class categorization, the class\_mode is set to the categorical setting. The subset parameter is utilized to divide the data into the training set and the validation set according to the validation split that has been given.

## 5.5 Training the model

The code provided in [Figure 5.8](#ch12.xhtml#f82) defines the structure of the model used for deep learning, which makes use of the Sequential API that TensorFlow provides. The model is made up of convolutional layers, followed by max pooling layers for the purpose of feature extraction. Flattening the output of the maximum pooling layer that came before it and then connecting it to a dense layer that uses ReLU activation completes the process. A dropout layer added to the network prevents overfitting, and the final dense layer using softmax activation generates the class probabilities.

![Figure 5.8Code snippet to define model architecture.](html/images/9781032676654_C005_008.jpg)

[Figure 5.8](#ch12.xhtml#f82b)Code snippet to define model architecture.

The Adam optimizer, the categorical cross-entropy loss function, and the accuracy metric are used in the compilation of the model. In order to train the model with the help of the training data for a predetermined amount of epochs, the fit technique is invoked. The performance of the model is assessed during the training process based on the validation data (see [Figure 5.9](#ch12.xhtml#f83)).

![Figure 5.9Code snippet for model compilation.](html/images/9781032676654_C005_009.jpg)

[Figure 5.9](#ch12.xhtml#f83b)Code snippet for model compilation.

## 5.6 Developing an interface based on Gradio

The code snippet for function definition to make predictions on the input images is presented in [Figure 5.10](#ch12.xhtml#f84). We will make use of the Gradio library in order to develop an intuitive interface for flower recognition. Gradio enables us to define machine learning models’ interfaces in a straightforward manner. We are going to build a user interface that, after receiving an image as input, displays the type of flower present.

![Figure 5.10Code snippet for function definition.](html/images/9781032676654_C005_010.jpg)

[Figure 5.10](#ch12.xhtml#f84b)Code snippet for function definition.

Importing the Gradio library results in the definition of a function called classify\_flower, which is used to categorize the input image of a flower. In order to determine the probabilities that will be predicted, the function will first resize the image, then normalize it, and then run it through the trained model.

gr.Interface is used to design the interface, with an image and a label being specified as the input and output respectively. The example photos, as well as the interface’s title and description, are presented here for your perusal. The Gradio interface is launched when the code iface.launch() is executed. This gives users the ability to interact with the flower categorization model using their own photos. See [Figure 5.11](#ch12.xhtml#f85).

![Figure 5.11Importing the Gradio library.](html/images/9781032676654_C005_011.jpg)

[Figure 5.11](#ch12.xhtml#f85b)Importing the Gradio library.

**Note:** If the gradio module is not already present in the environment you are working in, you may get it by running the following code: % pip install gradio.

The [Figure 5.12](#ch12.xhtml#f86) is an example interface that we created using Gradio.

![Figure 5.12Created Gradio interfaces.](html/images/9781032676654_C005_012.jpg)

[Figure 5.12](#ch12.xhtml#f86b)Created Gradio interfaces.

## 5.7 Conclusion

Using a dataset from Kaggle, we can reach the fascinating conclusion that flower recognition is a worthwhile endeavor to investigate. We are able to train a convolutional neural network (CNN) model by utilizing the power of deep learning and TensorFlow. This model is capable of classifying flower photos into the following five distinct categories: daisy, dandelion, rose, sunflower, and tulip. We also familiarize the readers with Gradio, a library that is friendly to users and designed for the creation of interactive interfaces. Gradio gives users the ability to identify photographs of flowers by using a model that has been developed.

The readers have learnt how to construct and train a CNN model for flower recognition, as well as how to create a Gradio interface for real-time predictions, by following the step-by-step instructions and downloading a dataset directly from Kaggle using the opendatasets package. The readers also learned how to preprocess the data using the ImageDataGenerator class. This chapter gave a complete overview of the end-to-end process of constructing a flower recognition system. As a result, readers are sure to obtain hands-on experience with deep learning and model deployment. Moreover, the chapter has also discussed the benefits of using such a system.

## 5.8 Further learning

Flower recognition has many possible improvements. By adapting pre-trained models to flower recognition, adjusting and transferable learning can be studied. This method may increase model accuracy and generalization. Second, grid-based and random searches can be used to optimize learning percentage, batch quantity, and network architecture. Model performance can also increase. Third, the methods of scaling, rotation, and random cropping can be employed to diversify and strengthen the training dataset. Fourth, adding more flower species to the dataset can improve the model’s recognition abilities. Finally, putting the model to a web-based app can allows users to contribute flower photos and receive predictions in real time. Improved model accuracy, dataset diversity, and user involvement and accessibility will improve flower recognition.

## Suggested readings

*   Bharati, P. and Pramanik, A., 2020. Deep learning techniques—R-CNN to mask R-CNN: A survey. In Computational Intelligence in Pattern Recognition: Proceedings of CIPR 2019 (pp.657–668). Springer Singapore.
*   Python library for easily interacting with trained machine learning models, gradio 4.19.2 [https://pypi.org/project/gradio/](https://pypi.org)

# Chapter 6Drug classification with hyperparameter tuning

DOI: [10.1201/9781032676685-7](http://doi.org/10.1201/9781032676685-7)

## Learning objectives

After completing this chapter, the reader shall be able to:

*   Acquire essential knowledge into the method of hyperparameter tuning as well as how it may dramatically increase the accuracy and efficacy of machine learning models.
*   Understand the significance of hyperparameter tuning and to implement it into K-Nearest Neighbors (KNN), Multilayer Perceptron (MLP), and Random Forest (RF) models.

## 6.1 Introduction

In this chapter, we will look into the interesting area of drug identification and classification and investigate the methodologies of hyperparameter tuning in order to improve the overall performance of our models. The idea of hyperparameters, as well as the critical part they play in the optimization of models, will be presented here. In addition, we will investigate the capabilities of GridSearchCV, which is a potent application that helps automate the process of determining the optimal values for hyperparameters by conducting an exhaustive search across the parameter space. The implementation in K-Nearest Neighbors (KNN), Multilayer Perceptron (MLP), and Random Forest (RF) models through the use of practical examples and the development of code is provided. This chapter’s goal is to provide you with the information and skills required to optimize the models and reveal the full potential that they possess.

## 6.2 Data preprocessing and splitting

Let’s begin by importing the necessary libraries for our job. We import the pandas library for data manipulation, the train\_test\_split function from scikit-learn for splitting the dataset, the StandardScaler function from scikit-learn for feature scaling, KNeighborsClassifier, MLPClassifier, and RandomForestClassifier for the respective models, GridSearchCV to provide hyperparameter tuning, and different metrics from scikit-learn for model evaluation. In addition, we bring in the matplotlib.pyplot library so that we can visualize the data. See [Figure 6.1](#ch13.xhtml#f87).

![Figure 6.1Code snippet for importing the needed libraries.](html/images/9781032676654_C006_001.jpg)

[Figure 6.1](#ch13.xhtml#f87b)Code snippet for importing the needed libraries.

We import the drug categorization dataset via a CSV file by utilizing the read\_csv function that is available in pandas, and then we save it to the variable known as data, as seen in [Figure 6.2](#ch13.xhtml#f88).

![Figure 6.2Code snippet for loading the dataset.](html/images/9781032676654_C006_002.jpg)

[Figure 6.2](#ch13.xhtml#f88b)Code snippet for loading the dataset.

We use the head() function to look at the first five rows from the data frame to get some basic inference on the data. Something to notice here is columns “Sex,” “BP,” and “Cholesterol” contains categorical variables. We can see our data frame has six columns and Drug is our target column. Next we check for the null values – we don’t have any missing values in our dataset. See [Figure 6.3](#ch13.xhtml#f89).

![Figure 6.3Getting inference on the data.](html/images/9781032676654_C006_003.jpg)

[Figure 6.3](#ch13.xhtml#f89b)Getting inference on the data.

In the first step of our data analysis, called preprocessing as seen in [Figure 6.4](#ch13.xhtml#f90), we transform categorical variables into numbers and then normalize the numerical features. We execute one-hot encoding on the categorical values present in our dataset such as “Sex,” “BP,” and “Cholesterol” by utilizing the function get\_dummies that is available in the pandas library. This gives them a corresponding representation in numerical form.

![Figure 6.4Code snippet for Data preprocessing.](html/images/9781032676654_C006_004.jpg)

[Figure 6.4](#ch13.xhtml#f90b)Code snippet for Data preprocessing.

In order to train the model, we first separate the preprocessed data into its features (X) and then into its target variable (y) as given in [Figure 6.5](#ch13.xhtml#f91). We give the preprocessed features (every column other than “Drug”) to the variable “X,” and we give the target parameter (“Drug”) to the constant “y.”

![Figure 6.5Code snippet for splitting the data.](html/images/9781032676654_C006_005.jpg)

[Figure 6.5](#ch13.xhtml#f91b)Code snippet for splitting the data.

When dividing the data into training and testing sets, we make use of the train\_test\_split function that is included in the scikit-learn package. The “test\_size” argument allows the user to specify the percentage of the dataset that will be utilized for testing, and the “random\_state” parameter assures that the random seed will always be the same, which ensures repeatability. See [Figure 6.6](#ch13.xhtml#f92).

![Figure 6.6Code snippet for data separation.](html/images/9781032676654_C006_006.jpg)

[Figure 6.6](#ch13.xhtml#f92b)Code snippet for data separation.

## 6.3 Modeling

The preceding piece of code generates instances of three different classifiers for the purpose of drug categorization. These classifiers are referred to as above in [Figure 6.7](#ch13.xhtml#f93). The Random Forest classifier is a combination of several decision trees, the KNN classifier assigns scores depending on the degree to which neighbors are similar to one another, and the MLP classifier is a neural network with multiple layers that are connected to one another.

![Figure 6.7Code snippet for classifiers.](html/images/9781032676654_C006_007.jpg)

[Figure 6.7](#ch13.xhtml#f93b)Code snippet for classifiers.

## 6.4 Hyperparameter tuning

The code snippet to define the hyperparameter grid for grid search for each classifier is given in [Figure 6.8](#ch13.xhtml#f94). In order to identify the optimal combination for the RF classifier, we use GridSearchCV to search through an input parameter grid that includes values for “n\_estimators,” “max\_depth,” and “criterion.” Our goal is to locate the parameter values that produce the most accurate results. In a similar manner, we modify the “n\_neighbors” hyperparameter for the KNN classifier by using GridSearchCV. This allows us to evaluate the performance of the model with a variety of neighbor values. In the instance of the MLP classifier, we concentrate on tuning hyperparameters such as “hidden\_layer\_sizes,” “activation,” and “max\_iter” in order to improve the design of the neural network. We automate the search for the best possible hyperparameters by utilizing GridSearchCV, which also helps to improve the accuracy of the models and their overall performance in drug categorization tasks. See [Figure 6.9](#ch13.xhtml#f95).

![Figure 6.8Code snippet to define the hyperparameter grid.](html/images/9781032676654_C006_008.jpg)

[Figure 6.8](#ch13.xhtml#f94b)Code snippet to define the hyperparameter grid.

![Figure 6.9Code snippet to perform grid search.](html/images/9781032676654_C006_009.jpg)

[Figure 6.9](#ch13.xhtml#f95b)Code snippet to perform grid search.

We have three different models, thus in order to determine the optimal combination of hyperparameters for each of them, we utilize GridSearchCV.

We first fit the grid search object to the training data, and then we obtain the best hyperparameters, which we then save in the variable named “modelname\_best\_params” correspondingly for all three of the models that we have employed. Refer to [Figure 6.10](#ch13.xhtml#f96) for the code snippet.

![Figure 6.10Code snippet to get the best hyperparameter value.](html/images/9781032676654_C006_010.jpg)

[Figure 6.10](#ch13.xhtml#f96b)Code snippet to get the best hyperparameter value.

## 6.5 Model training and evaluation

Using the three models that have been trained, we generate predictions using the testing data as in [Figure 6.11](#ch13.xhtml#f97).

![Figure 6.11Code snippet to generate predictions on the test set.](html/images/9781032676654_C006_011.jpg)

[Figure 6.11](#ch13.xhtml#f97b)Code snippet to generate predictions on the test set.

Calculating the model’s accuracy with the scikit-learn functions that correspond to that calculation allows us to assess the performance of the model. Refer to [Figure 6.12](#ch13.xhtml#f98) for the code snippet.

![Figure 6.12Code snippet to calculate accuracy.](html/images/9781032676654_C006_012.jpg)

[Figure 6.12](#ch13.xhtml#f98b)Code snippet to calculate accuracy.

We then move on to printing the accuracy of our respective models. Refer to [Figure 6.13](#ch13.xhtml#f99) for the code snippet.

![Figure 6.13Code snippet to print the accuracy.](html/images/9781032676654_C006_013.jpg)

[Figure 6.13](#ch13.xhtml#f99b)Code snippet to print the accuracy.

## 6.6 Model comparison and visualization

A line chart is developed so that we can examine the degrees of accuracy achieved by each of the three models. The “models” listed in [Figure 6.14](#ch13.xhtml#f100) includes the names of the models (“KNN,” “MLP,” and “RF”), and the “accuracies” list includes the accuracies that correspond to those models. When plotting the line chart, we define markers, linestyle, and color before passing the data to the plot function found in matplotlib.pyplot. We determine the title, the label for the x-axis, the label for the y-axis, and the limitations for the y-axis.

![Figure 6.14Accuracy Comparison.](html/images/9781032676654_C006_014.jpg)

[Figure 6.14](#ch13.xhtml#f100b)Accuracy Comparison.

In the end, we show the line chart by using the plt.show() function.

## 6.7 Conclusion

In this chapter, we have classified drugs using KNN, MLP, and RF models, and tuned their hyperparameters using various hyperparameter tuning strategies. We improved the performance of the models by locating the hyperparameters that worked best for them. The line chart comparison highlighted the disparities in accuracy that existed between the models, thereby shedding light on the efficiency of their respective approaches. The process of adjusting hyperparameters is an essential stage in the optimization of machine learning models, and it can considerably improve the latter’s capacity for prediction.

## 6.8 Further learning

In this chapter, we looked into the classification of drugs utilizing a wide variety of models and approaches for adjusting hyperparameters. Nevertheless, there are a lot of other directions this work and progress could go in the future. For a more effective search as well as greater exploration of the hyperparameter space, it is possible to make use of more sophisticated methods for tuning hyperparameters, such as Bayesian optimization or genetic algorithms. Additional study could concentrate on feature engineering in order to improve the depiction of the drug categorization dataset. This could involve investigating various strategies for dimensionality reduction or the incorporation of domain-specific information. Stacking and boosting are two examples of ensemble approaches that can be used to aggregate the predictions of numerous models in order to achieve a higher level of accuracy in classification. Problems with class imbalance can be remedied by employing techniques such as oversampling and under sampling, or SMOTE (Synthetic Minority Oversampling Technique) to deal with imbalanced data. When dealing with drug classification challenges, it may be beneficial to investigate deep learning methodologies such as convolutional neural networks and recurrent neural networks also.

## Suggested readings

*   Altay, O., Ulas, M. and Alyamac, K.E., 2020. Prediction of the fresh performance of steel fiber reinforced self-compacting concrete using quadratic SVM and weighted KNN models. IEEE Access, *8*, pp.92647–92658.
*   Mangkunegara, I.S. and Purwono, P., 2022, June. Analysis of DNA sequence classification using SVM model with hyperparameter tuning grid search CV. In 2022 IEEE International Conference on Cybernetics and Computational Intelligence (CyberneticsCom*)* (pp. 427–432). IEEE.
*   Passos, D. and Mishra, P., 2022. A tutorial on automatic hyperparameter tuning of deep spectral modelling for regression and classification tasks. Chemometrics and Intelligent Laboratory Systems, *223*, 104520.
*   Rodriguez-Galiano, V.F., Ghimire, B., Rogan, J., Chica-Olmo, M. and Rigol-Sanchez, J.P., 2012. An assessment of the effectiveness of a random forest classifier for land-cover classification. ISPRS Journal of Photogrammetry and Remote Sensing, *67*, pp.93–104.
*   Windeatt, T., 2008. Ensemble MLP classifier design. In Computational Intelligence Paradigms: Innovative Applications (pp.133–147). Springer.

# Chapter 7Evaluating model performanceMetrics for diabetes prediction

DOI: [10.1201/9781032676685-8](http://doi.org/10.1201/9781032676685-8)

## Learning objectives

After completing this chapter, the reader shall be able to:

*   Forecast diabetes using machine learning methods.
*   Analyze the efficiency of the models by means of performance metrics evaluation.

## 7.1 Introduction

In this chapter, we will go into the task of forecasting diabetes using machine learning methods on the Pima Indians Diabetes Database. The data for this chapter comes from the Pima Indians Diabetes Database obtained from kaggle. Users can obtain the dataset from the following link: [www.kaggle.com/datasets/uciml/pima-indians-diabetes-database](http://www.kaggle.com). We have an intriguing new addition for our readers that builds on the foundation laid in our prior chapters. In this chapter, we will analyze the efficiency of our models by discussing the notion of performance metrics, which will be introduced here. You will gain an understanding of a variety of metrics that provide a more in-depth insight of the performance of models, going beyond the concept of simple accuracy. Let’s jump right in and start learning about the performance assessment world!

## 7.2 Performance metrics

In the field of machine learning, it is essential to conduct performance evaluations of our models in order to have an understanding of how well these models are carrying out the task at hand. Although accuracy is a popular metric, it might not give a whole picture of how effective the model is. In this section, we are going to introduce numerous performance indicators or metrics that provide us with the ability to evaluate various elements of the model’s performance. Let’s look at each metric in more detail:

*   **Accuracy:** It is a measure of the overall accuracy of predictions, and indicates the proportion of correctly classified examples relative to the total number of occurrences. Accuracy assesses the overall correctness of forecasts. Accuracy is a valuable indicator, but it may not be sufficient when working with datasets that are imbalanced or when the cost of misclassification changes across various classes.
*   **Precision:** Precision refers to the ratio of accurately anticipated positive cases (true positives) to the total number of predicted positive cases (true positives plus false positives). Because it evaluates the model’s capacity to avoid producing false positives, precision is especially important in situations in which the identification of positive cases is of paramount importance.
*   **Recall (Sensitivity):** Recall, which is also known as sensitivity or true positive rate, measures the proportion of actual positive cases properly detected by the model (true positives) out of the total number of genuine positive cases (true positives plus false negatives). When the objective is to identify as many true positive cases as possible while reducing the number of false negatives, recall is an indispensable tool.
*   **Score of F1:** The F1 score is a fair evaluation of the model’s performance because it combines precision and recall into a single statistic. It is the harmonic mean of precision and recall, taking into account both false positives and false negatives. It is a measure of diagnostic accuracy. The F1 score can range from 0 to 1, with 1 reflecting flawless precision and recall.
*   **ROC AUC Score:** The Receiver Operating Characteristic (ROC) curve is an illustration of the model’s performance at various categorization criteria. The model’s ability to differentiate between positive and negative classes is quantified by a score known as the Area Under the ROC Curve (ROC AUC). Indicative of more discriminative capacity is a ROC AUC value that is higher.

By making use of these performance indicators, we are able to achieve a more in-depth comprehension of the strengths and shortcomings possessed by our models with regard to the diabetes prediction. With the help of these measures, we are able to examine specific features in addition to general accuracy, such as recall and precision, as well as the balance between the two. Let’s move on with our investigation and use these metrics to evaluate how well various machine learning models perform on the Pima Indians Diabetes dataset.

## 7.3 Data pre-processing

The lines of code as seen in [Figure 7.1](#ch14.xhtml#f101) provide import necessary libraries and modules that will be used for the tasks of data manipulation, evaluation, and machine learning. Data manipulation is handled by the imported pandas library, while numerical operations are handled by the imported numpy library. In order to divide the data into a training set and a testing set, the train\_test\_split function, which is located in the sklearn.model\_selection import, is used. In order to scale features, the StandardScaler class included in the sklearn.preprocessing package is imported. For the purpose of utilizing a variety of classification strategies, the LogisticRegression, RandomForestClassifier, & SVC classes are imported via the appropriate modules within sklearn. For the purpose of model evaluation, evaluation metrics such as accuracy\_score, precision\_score, recall\_score, f1\_score, and roc\_auc\_score are imported from sklearn.metrics. These lines of code lay the groundwork for the functionality and tools that will be required for the upcoming data analysis and tasks related to machine learning.

![Figure 7.1Code snippet to import libraries.](html/images/9781032676654_C007_001.jpg)

[Figure 7.1](#ch14.xhtml#f101b)Code snippet to import libraries.

The above line as in [Figure 7.2](#ch14.xhtml#f102) reads the dataset that is included in a CSV file by utilizing the read\_csv function that is located in the pandas library. The file location where the dataset may be found is “/content/diabetes.csv,” which is the name that has been given to the CSV file that is being used. The file is read using the read\_csv function, which then returns a DataFrame. This DataFrame is then assigned to a value known as data.

![Figure 7.2Code snippet to load the diabetes dataset.](html/images/9781032676654_C007_002.jpg)

[Figure 7.2](#ch14.xhtml#f102b)Code snippet to load the diabetes dataset.

When these lines of code are executed, the dataset titled “Pima Indians Diabetes” is loaded into storage as a pandas DataFrame, and then it is allocated to the variable titled “data” for the purposes of further investigation and manipulation.

The lines of code that are provided in [Figure 7.3](#ch14.xhtml#f103) involve segmenting the database into features and target factors, as well as segmenting the data even further into testing and training sets. The “Outcome” column, which originally represented the characteristics, is removed from the initial data set in order to make room for the X DataFrame. After choosing the “Outcome” item in the dataset, which stands in for the target variable, the y Series is finally ready to be generated. After that, the train\_test\_split procedure is called to separate the features (X) and the variable of interest (y) to separate sets for training and testing. The test\_size=0.2 option instructs the model to reserve 20% of the data for the testing phase, while devoting the remaining 80% of the data to the learning phase. The exactness of the split may be guaranteed thanks to the random\_state=42 argument.

![Figure 7.3Code snippet to split the dataset.](html/images/9781032676654_C007_003.jpg)

[Figure 7.3](#ch14.xhtml#f103b)Code snippet to split the dataset.

Scaling of features is accomplished using the lines of code provided in [Figure 7.4](#ch14.xhtml#f104), by utilizing the StandardScaler class found in the sklearn.preprocessing package. In order to calculate the average and standard deviation of each feature based on the training data, a StandardScaler object with the name scaler is first constructed. This feature scaling step helps machine learning models that use these characteristics perform better and be easier to interpret.

![Figure 7.4Code snippet for feature scaling.](html/images/9781032676654_C007_004.jpg)

[Figure 7.4](#ch14.xhtml#f104b)Code snippet for feature scaling.

## 7.4 Model evaluation and training

Logistic Regression, Random Forest, and Support Vector Machines (SVM) are the three models of machine learning that can be trained and evaluated with the code that is provided. Utilizing the scaled training variables (X\_train\_scaled) and the matching target variable (y\_train), the logistic regression algorithm is developed and trained. Following this step, predictions are performed using the trained Logistic Regression model on the scaled testing characteristics (X\_test\_scaled), and the values of the predictions are saved in the y\_pred\_logreg variable. In a comparable manner, the Random Forest approach and then the SVM model are both constructed, trained, and utilized for predictive purposes. The values that are predicted by Random Forest and SVM are each saved in their own separate variable known as y\_pred\_rf and y\_pred\_svm. These trained models can be assessed further using suitable metrics in order to measure how well they perform in terms of predicting the variable of interest. Refer to [Figure 7.5](#ch14.xhtml#f105) for the code snippet.

![Figure 7.5Code snippet for model training.](html/images/9781032676654_C007_005.jpg)

[Figure 7.5](#ch14.xhtml#f105b)Code snippet for model training.

Evaluation metrics for the machine learning models are computed using the code that is provided in [Figure 7.6](#ch14.xhtml#f106), and these metrics are stored. Metrics such as accuracy, precision, recall, F1 score, and ROC AUC score are derived for each model (Logistic Regression, Random Forest, and SVM) through the comparison of the true target values (y\_test) and the predicted values (y\_pred) produced by each corresponding model. This is done by comparing the true target values to the predicted values. These metrics offer insights into the capacity of each model to perform and make predictions based on the test data.

![Figure 7.6Code snippet for model evaluation.](html/images/9781032676654_C007_006.jpg)

[Figure 7.6](#ch14.xhtml#f106b)Code snippet for model evaluation.

We print all the four metrics calculated for each of three chosen models using the print() function and the variables in which the metrics are stored. Refer to [Figure 7.7](#ch14.xhtml#f107) for the code snippet of the same.

![Figure 7.7Code snippet to print performance metrics.](html/images/9781032676654_C007_007.jpg)

[Figure 7.7](#ch14.xhtml#f107b)Code snippet to print performance metrics.

When these lines of code as provided in [Figure 7.8](#ch14.xhtml#f108) are executed, a bar plot as seen in [Figure 7.9](#ch14.xhtml#f109) will be produced in order to illustrate and compare the outcomes and metrics of all three trained models. The plot offers a graphical representation of a comparison of the performance of the models on the metrics that are examined.

![Figure 7.8Performance metric comparison code snippet.](html/images/9781032676654_C007_008.jpg)

[Figure 7.8](#ch14.xhtml#f108b)Performance metric comparison code snippet.

![Figure 7.9Performance metric comparison.](html/images/9781032676654_C007_009.jpg)

[Figure 7.9](#ch14.xhtml#f109b)Performance metric comparison.

## 7.5 Conclusion

In this chapter, we made our first foray into the world of model evaluation and performance metrics while making predictions about diabetes using machine learning strategies. Beyond just accuracy, we now have a comprehensive grasp of model evaluation due to the introduction of a variety of evaluation metrics, including accuracy, precision, recall, F1 score, and ROC AUC score. The readers would have obtained knowledge about developing models, conducting feature scaling, and accurately evaluating model performance through the use of three different machine learning models on the Pima Indians Diabetes dataset.

## 7.6 Further learning

The Diabetes Dataset from the Pima Indians presents a considerable amount of promise for future research and technological breakthroughs in the field of diabetes forecasting. In terms of the engineering of features and the selection of the most important ones, additional research can be carried out to discover additional pertinent aspects that are unique to diabetes, as well as more sophisticated methods to either derive new features or choose the most important ones. In addition, the dataset may be put through more advanced machine learning procedures, such as the application of deep learning models, such as convolutional neural networks (CNNs) or recurrent neural networks (RNNs), which are able to identify subtle patterns and correlations hidden within the data.

## Suggested readings

*   Erickson, B.J. and Kitamura, F., 2021. Magician’s corner: 9. Performance metrics for machine learning models. Radiology: Artificial Intelligence, *3*(3), e200126.
*   Fabris, F., Doherty, A., Palmer, D., de Magalhaes, J.P. and Freitas, A.A., 2018. A new approach for interpreting random forest models and its application to the biology of ageing. Bioinformatics, *34*(14), pp.2449–2456.
*   O’Connell, A.A., 2006. *Logistic Regression Models for Ordinal Response Variables* (Vol. 146). Sage.
*   Sahoo, K.S., Tripathy, B.K., Naik, K., Ramasubbareddy, S., Balusamy, B., Khari, M. and Burgos, D., 2020. An evolutionary SVM model for DDOS attack detection in software defined networks. IEEE Access, *8*, pp.132502–132513.

# Chapter 8Parkinson’s disease detectionAn overview with feature engineering and outlier analysis

DOI: [10.1201/9781032676685-9](http://doi.org/10.1201/9781032676685-9)

## Learning objectives

After reading this chapter, the reader shall be able to:

*   Acquire the knowledge construct models to predict Parkinson’s disease.
*   Gain information regarding feature engineering, outlier analysis, model training, evaluation, and comparison.

## 8.1 Introduction

In this chapter, we will investigate how machine learning techniques can be applied to the diagnosis of Parkinson’s disease. Readers can extract the dataset from the following link: [www.kaggle.com/datasets/debasisdotcom/parkinson-disease-detection](http://www.kaggle.com). The neuro degenerative condition known as Parkinson’s disease is characterized by its effect on motor functioning. We are able to construct models that can predict the existence or absence of Parkinson’s disease by making use of techniques that are associated with machine learning. These models examine a number of variables retrieved from patient data. Readers will be given an overview of the Parkinson Detection dataset as well as information regarding feature engineering, outlier analysis, model training, evaluation, and comparison throughout the course of this chapter.

## 8.2 Importing libraries and dataset

Importing the necessary libraries for data manipulation, visualization, and machine learning is the first step (see [Figure 8.1](#ch15.xhtml#f110)). For the purpose of data processing, the matplotlib and pandas libraries are loaded as pd. When attempting to visualize data, pyplot is notated as plt, and when attempting to enhance visualizations, seaborn is denoted as sns. We also import several modules from the sklearn library. These modules include train\_test\_split for the purpose of data splitting, StandardScaler and PolynomialFeatures for the purpose of data preprocessing, IsolationForest for the purpose of outlier analysis, LinearDiscriminantAnalysis for the purpose of performing LDA, LinearRegression for the purpose of linear regression, and DecisionTreeClassifier for the purpose of decision tree classification. In addition, we bring in the accuracy\_score variable so that we may assess how well our models are performing.

![Figure 8.1Importing the needed libraries.](html/images/9781032676654_C008_001.jpg)

[Figure 8.1](#ch15.xhtml#f110b)Importing the needed libraries.

Finally we use the pd.read\_csv function to load the dataset and we can see the first two rows from the dataset using the head(2) function as given in [Figure 8.2](#ch15.xhtml#f111).

![Figure 8.2Code snippet to load the dataset.](html/images/9781032676654_C008_002.jpg)

[Figure 8.2](#ch15.xhtml#f111b)Code snippet to load the dataset.

## 8.3 Data pre-processing

### 8.3.1 Outlier detection and analysis

Outliers are data points that significantly deviate from the general pattern or distribution of the dataset. They are observations that are unusually distant from other observations and can have a substantial impact on the analysis and modeling process. Outliers can occur due to various reasons such as measurement errors, data entry mistakes, experimental anomalies, or genuine extreme values. Identifying and handling outliers is an essential step in data preprocessing as they can distort statistical analyses, affect the accuracy of machine learning models, and lead to misleading insights.

The number of rows and columns contained in the dataset is indicated by the “shape” of the data, which can be obtained by using the snippet of code known as data.shape as given in [Figure 8.3](#ch15.xhtml#f112). It supplies information regarding the parameters of the dataset. The features are extracted from the dataset using the code X = data.drop(\[“name,” “status”\], axis=1) as the separator. It does this by removing the columns “name” and “status” from the data in the first dataset, which results in the creation of a new DataFrame X. If you set the axis option to 1, it implies that the columns should be removed.

![Figure 8.3Code snippet for data shape.](html/images/9781032676654_C008_003.jpg)

[Figure 8.3](#ch15.xhtml#f112b)Code snippet for data shape.

When the line of code y = data\[“status”\] is executed, the value of the target variable “status” is transferred to the variable y. It generates a new Series y using the values taken from the original dataset’s “status” column and populating it with those values. The number of rows and columns contained within the features can be determined by using the code X.shape, which returns the shape of the features contained within DataFrame X. It offers details regarding the extent to which the feature set can be utilized.

In order to better illustrate the outcomes of the outlier detection, we generate a scatter plot with the help of matplotlib.pyplot and seaborn. The “MDVP:Fo(Hz)” feature is plotted along the y-axis, while the sample index is plotted along the x-axis. The hue parameter is used to color-code the outliers, so that the outliers are represented by a color that is distinct from the inliers’ color representation. Refer to [Figure 8.4](#ch15.xhtml#f113). This gives us the ability to visually recognize the occurrences that are considered to be outliers based on where they are located in the scatter plot. (Note that while we chose the column MDVP:Fo(Hz) at random, this does not indicate that it is the sole column that contains outliers.)

![Figure 8.4Outlier detection.](html/images/9781032676654_C008_004.jpg)

[Figure 8.4](#ch15.xhtml#f113b)Outlier detection.

We utilize an unsupervised learning approach called IsolationForest as represented in [Figure 8.5](#ch15.xhtml#f114) to find outliers in the dataset. This algorithm discovers anomalies by separating instances of the dataset and looking for patterns that do not fit the norm. We start a new instance of IsolationForest with a contamination parameter of 0.05, which indicates that we anticipate that around 5% of the data will be abnormal. After that, in order to understand the fundamental structure of the data, we apply the outlier detector to the feature matrix X and run the fitting process. Next, we apply the trained outlier detector to the dataset in order to forecast the outliers using the predict() method that is attached to X. A label of -1 is given to outliers by the predict() method, while a label of 1 is given to inliers. By selecting only the inlier occurrences for which the projected label is 1, we are able to generate a new subset of the feature matrix known as X\_no\_outliers. In a similar manner, we generate a comparable subset of the target variable called y\_no\_outliers by removing the outliers from the data.

![Figure 8.5Outlier analysis.](html/images/9781032676654_C008_005.jpg)

[Figure 8.5](#ch15.xhtml#f114b)Outlier analysis.

### 8.3.2 The train-test split

For the function derived from sklearn.model\_selection called train\_test\_split, we make use of the attributes X\_no\_outliers and the desired variable y\_no\_outliers, both composed of the filtered data that do not contain outliers. The test\_size argument in [Figure 8.6](#ch15.xhtml#f115) allows the user to specify the percentage of the data used for testing, and the random\_state parameter ensures that the split can be reproduced.

![Figure 8.6Splitting the data.](html/images/9781032676654_C008_006.jpg)

[Figure 8.6](#ch15.xhtml#f115b)Splitting the data.

### 8.3.3 Scaling features

StandardScaler from the sklearn.preprocessing library as in [Figure 8.7](#ch15.xhtml#f116) is used to perform the scaling of the features. Scaling the training features (X\_train) and the testing features (X\_test) requires the StandardScaler to be instantiated as scaler so that it may be used. When the features are scaled, this guarantees that they are all on the same scale and prohibits any one feature from taking control of the learning algorithm.

![Figure 8.7Code snippet to perform feature scaling.](html/images/9781032676654_C008_007.jpg)

[Figure 8.7](#ch15.xhtml#f116b)Code snippet to perform feature scaling.

### 8.3.4 Polynomial feature engineering

We will use polynomial feature engineering so that we can better understand the intricate connections between the features. Using this method, polynomial combinations of the initial characteristics are generated, which results in the creation of additional interaction terms. We will be able to more accurately describe non-linear relationships and maybe improve the performance of the model if we make use of higher-order terms. In this section, examples of code will be provided so as to explain the notion of polynomial feature engineering.

Following the scaling of the features, polynomial feature engineering is carried out (refer to [Figure 8.8](#ch15.xhtml#f117)) with the help of the sklearn.preprocessing class PolynomialFeatures. In this particular instance, the degree of the polynomial is set to 2, denoted by the notation degree = 2. In order to convert the scaled training features (X\_train\_scaled) and testing features (X\_test\_scaled) into polynomial features, the PolynomialFeatures class is instantiated as the variable poly. This procedure creates new features by combining the existing features to the specified degree, which may then be used to build new features.

![Figure 8.8Code snippet for polynomial feature engineering.](html/images/9781032676654_C008_008.jpg)

[Figure 8.8](#ch15.xhtml#f117b)Code snippet for polynomial feature engineering.

The modified features generated as a result, are saved in X\_train\_poly for the training data and X\_test\_poly for the testing data. These polynomial features capture non-linear correlations between the original data, allowing the models to learn more complicated patterns. This is made possible by the fact that the models are able to learn the patterns.

## 8.4 Model training and evaluation

In this section, we will train three distinct machine learning models: the Linear Discriminant Analysis (LDA), the Linear Regression, and the Decision Tree Classifier and then compare their performance. The training data will be used to fit each model, and the test data will be used to evaluate the models. In order to evaluate the efficacy of each model in predicting Parkinson’s disease, we will compute the accuracy. The code snippet of this is provided in [Figure 8.9](#ch15.xhtml#f118).

![Figure 8.9Code snippet for training the machine learning models.](html/images/9781032676654_C008_009.jpg)

[Figure 8.9](#ch15.xhtml#f118b)Code snippet for training the machine learning models.

This snippet of code as seen in [Figure 8.10](#ch15.xhtml#f119) generates a radar plot, which allows one to examine and evaluate the degrees of accuracy achieved by each of the three models. On the radar plot, each model is denoted by a vertex, and the distance of that vertex from the plot’s center serves as an indicator of how accurate the model is. The greater the distance, the more accurate the measurement will be. The radar map makes it possible to conduct a rapid visual assessment of the accuracies of several different models. Adjusting the graph’s size, line design, colors, and any other visual features to fit your tastes is one way you can personalize the plot.

![Figure 8.10Accuracy comparison.](html/images/9781032676654_C008_010.jpg)

[Figure 8.10](#ch15.xhtml#f119b)Accuracy comparison.

## 8.5 Further learning

Future research and development could go in many different directions. To begin, we can investigate additional feature engineering strategies to further improve the performance of the model. Some of these techniques include feature selection and dimensionality reduction. In addition to this, we can experiment with a variety of machine learning algorithms and ensemble methods to determine whether any of them can produce superior results. In addition, the collection of additional data and the expansion of the dataset can result in models that are more resilient and generalizable. In conclusion, completing a more in-depth research and investigation into the characteristics that contribute the most to the prediction might provide significant insights for medical professionals who are working in the field. One may continue to refine and increase the accuracy and reliability of the Parkinson’s disease detection that we have achieved via the use of machine learning by putting into practice and experimenting with a variety of methodologies and models.

## 8.6 Conclusion

The purpose of this chapter is to provide an overview of a machine learning experiment that makes use of the Parkinson Detection dataset. Following the completion of an outlier analysis and feature engineering by the use of polynomial transformation, the dataset is subjected to further processing. The preprocessed data are utilized in the application of three different machine learning models viz. Linear Discriminant Analysis (LDA), Linear Regression, and Decision Tree Classification. After calculating and comparing the accuracy scores of various models, we arrived at a conclusion. The accuracy of LDA is estimated as 89.18%, while the accuracy of Linear Regression is also the same 89.18% as the LDA, whereas the accuracy of the Decision Tree Classifier is found to be 86.48%. Based on these findings, we conclude that the LDA as well as the Linear Regression model perform significantly better than the other model i.e., Decision Tree Classifier in predicting the presence of Parkinson’s disease. On the other hand, additional research and testing could be required in order to ascertain which model is the best appropriate for this particular dataset.

## Suggested readings

*   Aalen, O.O., 1989. A linear regression model for the analysis of life times. Statistics in Medicine, *8*(8), pp.907–925.
*   Dixon, W.J., 1953. Processing data for outliers. Biometrics, *9*(1), pp.74–89.
*   Gaidel, A.V., 2018, September. Polynomial feature engineering for classification of textural images. Journal of Physics: Conference Series, *1096*(1), 012027.
*   Izenman, A.J. and Izenman, A.J., 2008. Linear discriminant analysis. In Modern Multivariate Statistical Techniques: Regression, Classification, and Manifold Learning (pp.237–280). Springer.
*   Priyam, A., Abhijeeta, G.R., Rathee, A. and Srivastava, S., 2013. Comparative analysis of decision tree classification algorithms. International Journal of Current Engineering and Technology, *3*(2), pp.334–337.

# Chapter 9Sonar mines vs. rock prediction using ensemble learning

DOI: [10.1201/9781032676685-10](http://doi.org/10.1201/9781032676685-10)

## Learning objectives

By the end of this chapter, the reader shall be able to:

*   Acquire knowledge about ensemble learning and its significance.
*   Gain insights regarding reliable and accurate predictions with ensemble technique.

## 9.1 Introduction

In this chapter, we provide the readers with a concise introduction to ensemble learning and demonstrate how significantly it enhances the performance of our models. We plan to use the data that we have obtained from Kaggle which can be obtained from the following link: [www.kaggle.com/datasets/mattcarter865/mines-vs-rocks?select=sonar.all-data.csv](http://www.kaggle.com) to make an educated guess as to whether the submarine is detecting a stone or a mine. The forecasts of a number of different machine learning models can be merged using the ensemble technique, which then provides us with reliable and accurate predictions. In addition to this, we have harnessed the power of oneAPI in order to improve the functionality of our models as well as their precision. In order to perfect our models, we make use of the oneDAL library provided by oneAPI.

## 9.2 Importing libraries and dataset

First, we begin by importing all the necessary libraries that we would now need.

In order to work with the dataset and to manage it, we import the pandas library. Next, we import the train test split function in order to divide our data for the model into the testing set and the train set. We will be utilizing the Standard Scalar so that the features of the dataset may be standardized. These three models are obtained from the scikit-learn website and imported. To put the technique of ensemble learning into action, we need to import the votingclassifier. Importing the accuracy\_score and classification\_report helps us with both the results and the evaluation. See [Figure 9.1](#ch16.xhtml#f120).

![Figure 9.1Importing the desired libraries.](html/images/9781032676654_C009_001.jpg)

[Figure 9.1](#ch16.xhtml#f120b)Importing the desired libraries.

Importing the csv file used for this project into the Pandas dataframe causes it to be saved in a variable that is simply named data. Refer to [Figure 9.2](#ch16.xhtml#f121) for the code snippet.

![Figure 9.2Loading the dataset.](html/images/9781032676654_C009_002.jpg)

[Figure 9.2](#ch16.xhtml#f121b)Loading the dataset.

## 9.3 Initial exploration

For additional preprocessing in the subsequent sections, we need to further examine the dataset.

In order to examine the dataset, we make use of the .head() function, which provides us with the first five rows of the dataset. There are 61 columns and 5 rows in the dataset as seen from [Figure 9.3](#ch16.xhtml#f122). In the dataset, the Rock or Mine targets are located in the column labeled “R.”

![Figure 9.3Examining the dataset.](html/images/9781032676654_C009_003.jpg)

[Figure 9.3](#ch16.xhtml#f122b)Examining the dataset.

The presence of null values constitutes a possible risk that may result in a variety of complications during the modeling phase. To prevent this, we make use of the isnull().sum() as seen in [Figure 9.4](#ch16.xhtml#f123) that helps us determine the missing values from our dataset. Fortunately, none of those is seen in this data set.

![Figure 9.4Determining null values.](html/images/9781032676654_C009_004.jpg)

[Figure 9.4](#ch16.xhtml#f123b)Determining null values.

## 9.4 Data pre-processing

Before feeding the data to our model, we first need to split our dataset into test set and train set.

In the first step as denoted in [Figure 9.5](#ch16.xhtml#f124), we establish two variables, which we will refer to as X and Y. In X, we will store the features apart from the target variable, and in Y, we will save only the target variable. In this scenario, we are aiming for R. Then, in order to split the data, we make use of the train\_test\_split function, with the test size set at 20% and the training size set at 80%.

![Figure 9.5Dataset splitting.](html/images/9781032676654_C009_005.jpg)

[Figure 9.5](#ch16.xhtml#f124b)Dataset splitting.

StandardScaler, as seen from [Figure 9.6](#ch16.xhtml#f125), is an application that is utilized in order to resize the distribution of values in such a way that the mean of the observed values is equal to 0 and the standard deviation is equal to 1. StandardScaler is an important approach that is mostly used as a preprocessing step before many different machine learning models in order to standardize the range of functionality of the input dataset. This is done in order to ensure that the models can make accurate comparisons between the datasets.

![Figure 9.6Dataset standardization.](html/images/9781032676654_C009_006.jpg)

[Figure 9.6](#ch16.xhtml#f125b)Dataset standardization.

## 9.5 Model training

A Voting Classifier is a type of machine learning model that is trained on an ensemble of many models and then makes a prediction about an output (class) based on the models’ highest likelihood of selecting that class as the output. It merely compiles the results of each classifier fed into the Voting Classifier and bases which is the fundamental principle or rule upon which the Voting Classifier makes its final decision. Refer to [Figure 9.7](#ch16.xhtml#f126) for the code snippet.

![Figure 9.7Voting Classifier.](html/images/9781032676654_C009_007.jpg)

[Figure 9.7](#ch16.xhtml#f126b)Voting Classifier.

There are three separate classification models employed, and then a voting classifier as given in [Figure 9.8](#ch16.xhtml#f127) is used to integrate the predictions from all the models. The red colored pop-up message shows us the models are optimized with oneAPI, oneDAL library.

![Figure 9.8To integrate predictions from all models.](html/images/9781032676654_C009_008.jpg)

[Figure 9.8](#ch16.xhtml#f127b)To integrate predictions from all models.

The three model instances are saved in the variable referred to as “models” as a list of tuples, each of which has a unique name for a classifier. Following this step, a voting classifier is developed in order to carry out majority voting based on projected class labels. The final step is fitting the test data, which has previously been scaled, to the voting classifier.

## 9.6 Result and analysis

As the final step, we analyze and evaluate the voting classifier that is created.

![Figure 9.9Voting Classifier performance evaluation.](html/images/9781032676654_C009_009.jpg)

[Figure 9.9](#ch16.xhtml#f128b)Voting Classifier performance evaluation.

The accuracy of the voting classifier’s prediction is compared with the ground truth labels using “accuracy\_score.” A classification report is then generated which includes various different metrics to evaluate our model. The model performs with an accuracy of 73.8% (refer to [Figure 9.9](#ch16.xhtml#f128)).

## 9.7 Further learning

In the future, we may delve further into ensemble learning by investigating other approaches for ensemble learning such as bagging, boosting, and stacking. It is important to practice hyperparameter adjustment in order to enhance model performance. Additionally, it is important to research approaches for improving model interpretability and managing imbalanced datasets. Conduct experiments with a variety of model selection procedures, such as soft voting, and investigate in advanced ways for combining models, such as stacking using meta-classifiers.

## 9.8 Conclusion

In this chapter, we have discussed the idea of ensemble learning and illustrated how to use the Voting Classifier to combine the predictions of three different types of models: logistic regression, decision trees, and random forests. With ensemble learning, we were able to capitalize on the many models’ inherent advantages, which ultimately led to a more reliable and accurate categorization. We were able to have a better grasp of how ensemble learning can dramatically improve the performance and stability of machine learning models by using this approach. As we continue to work our way through this book, we will go deeper into more advanced principles and methods of machine learning, which will provide us with the ability to efficiently solve difficult problems that arise in the real world.

## Suggested reading

*   Karadeniz, T., Maraş, H.H, Tokdemir, G. and Ergezer, H., 2023, March 15. Two majority voting classifiers applied to heart disease prediction. Applied Sciences, *13*(6), p.3767.

# Chapter 10Bankruptcy risk prediction

DOI: [10.1201/9781032676685-11](http://doi.org/10.1201/9781032676685-11)

## Learning objectives

After reading this chapter, the reader shall be able to:

*   Acquire the knowledge to develop a reliable machine learning model for financial purposes to determine the risk of bankrupt.
*   Gain information regarding data pretreatment, data exploration, model construction as well as result analysis.

## 10.1 Introduction

The process of identifying failing companies using methods of machine learning is what we will be exploring in this chapter. The objective variable “Bankrupt” in our dataset “Bankruptcy\_Detection” can be obtained from Kaggle by using the following link: [www.kaggle.com/datasets/fedesoriano/company-bankruptcy-prediction](http://www.kaggle.com) which indicates whether or not a company has filed for bankruptcy. This dataset provides essential financial indicators and ratios for a variety of enterprises. The objective of this project is to develop a reliable machine learning model with the capability of determining, on the basis of the financial characteristics of a business, whether or not that business is at risk of going bankrupt. In order to provide useful insights into this important financial application, we will take a methodical approach, which will include data pretreatment, data exploration, model construction, result analysis, and concluding remarks.

## 10.2 Importing libraries and dataset

Initially to prepare the dataset for modeling, we need to perform some data preparation. During this stage, you will be responsible for resolving any missing numbers and addressing any data quality issues that may have arisen. Let us get started by loading the dataset, analyzing its structure, and managing the null values by populating them with the mean of each column. This will get us off to a good start.

We begin by importing the necessary library files as witnessed in [Figure 10.1](#ch17.xhtml#f129). Pandas is used for data handling, train\_test\_split is utilized for splitting the dataset, StandardScaler is utilized for feature scaling, RandomForestClassifier is utilized for the construction of the Random Forest model, accuracy\_score and classification\_report are utilized as model evaluation metrics, and SMOTE and RandomUnderSampler are utilized for the treatment of class imbalance.

![Figure 10.1Importing the necessary libraries.](html/images/9781032676654_C010_001.jpg)

[Figure 10.1](#ch17.xhtml#f129b)Importing the necessary libraries.

We use pandas to read the “Bankruptcy\_Detection” dataset from the csv file, and then we save it in a DataFrame that we’ve given the name data. Refer to [Figure 10.2](#ch17.xhtml#f130) for the code snippet.

![Figure 10.2Code snippet to load the dataset.](html/images/9781032676654_C010_002.jpg)

[Figure 10.2](#ch17.xhtml#f130b)Code snippet to load the dataset.

## 10.3 Data exploration and preprocessing

In this step, we are looking at the first five rows of our dataset to get an overview about the features present. It is clear that we have 5 rows and 96 columns as seen in [Figure 10.3](#ch17.xhtml#f131) with “Bankrupt?” as our target variable.

![Figure 10.3Examining the dataset.](html/images/9781032676654_C010_003.jpg)

[Figure 10.3](#ch17.xhtml#f131b)Examining the dataset.

Next, we check for the null values in our dataset using the isnull().sum() function. We can see some features contain null values as in [Figure 10.4](#ch17.xhtml#f132). From the previous step, we have an idea about the data type present. We have to choose a suitable method to fill all the null values.

![Figure 10.4Checking null values.](html/images/9781032676654_C010_004.jpg)

[Figure 10.4](#ch17.xhtml#f132b)Checking null values.

To fill the null values we use the mean method as depicted in [Figure 10.5](#ch17.xhtml#f133). Now it is evident that our data set does not contain any null values.

![Figure 10.5Filling the null values.](html/images/9781032676654_C010_005.jpg)

[Figure 10.5](#ch17.xhtml#f133b)Filling the null values.

We divide the feature columns (X) and the target variable column (“Bankrupt?”) and then store them, separately, in the variables X and y. After that, we use the train\_test\_split function that is included in the scikit-learn package to divide the dataset into a training set and a testing set. The training set accounts for 80 percent of the total data, whereas the test set accounts for 20 percent. The random\_state=42 parameter assures that the results may be reproduced accurately. Refer to [Figure 10.6](#ch17.xhtml#f134) for the code snippet.

![Figure 10.6Feature separation and dataset splitting.](html/images/9781032676654_C010_006.jpg)

[Figure 10.6](#ch17.xhtml#f134b)Feature separation and dataset splitting.

In order to scale the feature data, an instance of StandardScaler is first created. Scaling guarantees that all features have comparable ranges and prevents features with bigger scales from taking control of the learning process. Scaling can also be used to describe the relationship between two variables. We start by fitting the scaler to the training data using fit\_transform, and then we use the fitted scaler to transform both the training data and the testing data. Refer to [Figure 10.7](#ch17.xhtml#f135) for the code snippet.

![Figure 10.7Feature data scaling.](html/images/9781032676654_C010_007.jpg)

[Figure 10.7](#ch17.xhtml#f135b)Feature data scaling.

In order to discover any potential class imbalances, we first visualize the distribution of the target variable “Bankrupt?” and then conduct an analysis of its class distribution. The illustration presented in [Figure 10.8](#ch17.xhtml#f136) makes it abundantly evident that there is an imbalance of classes (Japkowicz and Stephen, 2002).

![Figure 10.8Class imbalances visualization.](html/images/9781032676654_C010_008.jpg)

[Figure 10.8](#ch17.xhtml#f136b)Class imbalances visualization.

To address the issue of class imbalance, an instance of SMOTE is created. SMOTE is able to generate synthetic samples for the minority class by interpolating new samples between the ones that already exist for the minority class. By resampling the training data with the fit\_resample function, we are able to generate a version of the training data that is more evenly distributed with regard to the target variable. In order to tackle class imbalance in a more comprehensive manner, we first build an instance of the RandomUnderSampler. Random Under-Sampling is a technique that removes samples from the majority class in order to create a more even distribution across the classes. In order to produce the completed form of the balanced training data (X\_train\_balanced and y\_train\_balanced), we apply this method to the data that was already balanced during the training process. Refer to [Figure 10.9](#ch17.xhtml#f137) for the code snippet.

![Figure 10.9Addressing Class imbalance.](html/images/9781032676654_C010_009.jpg)

[Figure 10.9](#ch17.xhtml#f137b)Addressing Class imbalance.

## 10.4 Modeling

We begin by generating a Random Forest Classifier with 100 trees (n\_estimators=100) and setting the random seed to ensure reproducibility (random\_state=42). The complete code snippet is provided in [Figure 10.10](#ch17.xhtml#f138). Next, we generate an SVM classifier with the name svm\_model and train it on the balanced training data (X\_train\_balanced and y\_train\_balanced). Finally, we generate a final model. On the balanced training data (X\_train\_balanced and y\_train\_balanced), we train the Random Forest and the SVM model. To make a prediction about the target variable based on the scaled test data (X\_test\_scaled), we make use of the trained Random Forest and svm model.

![Figure 10.10Classifier generation and training.](html/images/9781032676654_C010_010.jpg)

[Figure 10.10](#ch17.xhtml#f138b)Classifier generation and training.

To make a prediction about the target variable based on the scaled test data (X\_test\_scaled), we make use of the trained Random Forest and svm model. Using the ground truth labels from the test set (y\_test) and the predicted labels (y\_pred), we calculate the accuracy of the model’s predictions as seen from [Figure 10.11](#ch17.xhtml#f139). The next step is the generation of a comprehensive classification report, which evaluates the performance of the model by providing metrics such as precision, recall, F1-score, and support for each class.

![Figure 10.11Predictions and Performance evaluation.](html/images/9781032676654_C010_011.jpg)

[Figure 10.11](#ch17.xhtml#f139b)Predictions and Performance evaluation.

## 10.5 Result and analysis

The evaluation results, which include the report on the model’s accuracy as well as a full classification of the data, are printed with the aid of the code given in [Figure 10.12](#ch17.xhtml#f140). Random forest outperforms SVM with an accuracy of around 91.69%.

![Figure 10.12Results Evaluation.](html/images/9781032676654_C010_012.jpg)

[Figure 10.12](#ch17.xhtml#f140b)Results Evaluation.

To visualize the difference in accuracy between the two models, we generate a bar plot as shown in [Figure 10.13](#ch17.xhtml#f141) with matplotlib and use plt.bar as the plotting function. The accuracy values are displayed along the y-axis of the bar plot, while the model names are listed along the x-axis. The bar plot provides a visual comparison of the accuracy of the SVM classifier and the Random Forest classifier, which will assist us in determining whether the model performs better for the identification of bankruptcy on this dataset.

![Figure 10.13Accuracy comparison.](html/images/9781032676654_C010_013.jpg)

[Figure 10.13](#ch17.xhtml#f141b)Accuracy comparison.

## 10.6 Conclusion

Our investigation on the possibility of bankruptcy utilizing machine learning seems fruitful. We begin the bankruptcy prediction procedure by first preprocessing the dataset, then visually representing the target variable distribution, and finally training Random Forest and SVM models. We made use of a variety of indicators to evaluate the performance of the models, which allow us to identify both their strengths and limitations. This project offers useful insights for the use of machine learning in bankruptcy risk assessment, thereby assisting financial professionals in making judgments that are more informed.

## 10.7 Further works

In future works, we may investigate more complex machine learning models, such as neural networks or gradient boosting techniques, with the goal of significantly improving the accuracy of bankruptcy identification. In addition, the incorporation of alternative data sources, the incorporation of time-series data, and the consideration of domain-specific financial characteristics could boost the performance of the model. In addition, the use of interpretability methodologies and the performance of feature importance analysis will provide insightful knowledge that will be helpful for financial professionals in their quest to comprehend the elements that influence bankruptcy predictions.

## Suggested Reading

*   Japkowicz, N. and Stephen, S., 2002. The class imbalance problem: A systematic study. Intelligent Data Analysis, *6*(5), pp.429–449.

# Chapter 11Hotel reservation prediction

DOI: [10.1201/9781032676685-12](http://doi.org/10.1201/9781032676685-12)

## Learning objectives

After finishing this chapter, the reader shall be able to:

*   Discover insights and construct predictive models by utilizing the power of exploratory data analysis and machine learning models.
*   Build and analyze the prediction models.
*   Efficiently plan hotel operations, revenue generation and enhance customer happiness based on the data-driven insights and precise predictions.

## 11.1 Introduction

In today’s modern hospitality sector, it is absolutely essential to manage hotel reservations in an effective manner in order to provide excellent experiences for guests. Exploration and prediction code based on the “Hotel Reservation Dataset” from kaggle, [www.kaggle.com/datasets/ahsan81/hotel-reservations-classification-dataset](http://www.kaggle.com), provides a comprehensive solution to study and forecast booking results. This code gives data enthusiasts and hospitality professionals the ability to discover insights and construct predictive models by utilizing the power of exploratory data analysis (EDA), preprocessing, and machine learning models. The dataset is loaded and preprocessed as the first step in the algorithm, followed by the handling of missing values and the encoding of categorical variables. Following that, it demonstrates EDA by visualizing booking status distributions, correlations among attributes, and room type pricing. Building and analyzing prediction models through the use of logistic regression, decision trees, and random forests is the core functionality of the code. In addition to this, it uses techniques of oversampling in order to address the problem of class imbalance. The end goal is to create a comprehensive toolkit that can be utilized by anyone who has an interest in understanding the dynamics of hotel reservations and improving their ability to forecast future outcomes. People who use this code are able to more effectively strategize hotel operations, maximize income, and improve customer happiness based on the data-driven insights and accurate predictions.

## 11.2 Data preprocessing

We start by importing the necessary libraries for the task, as shown in [Figure 11.1](#ch18.xhtml#f142). We import modules like pandas and numpy for handling data, and for data visualization, we import matplotlib and seaborn.

![Figure 11.1Code snippet to import libraries.](html/images/9781032676654_C011_001.jpg)

[Figure 11.1](#ch18.xhtml#f142b)Code snippet to import libraries.

![Figure 11.2To load the dataset.](html/images/9781032676654_C011_002.jpg)

[Figure 11.2](#ch18.xhtml#f143b)To load the dataset.

We then use the pandas library to load the csv data ([Figure 11.2](#ch18.xhtml#f143)).

The head() function used gives us the first five rows of the datasets as seen in [Figure 11.3](#ch18.xhtml#f144).

![Figure 11.3Code snippet to look at the dataset.](html/images/9781032676654_C011_003.jpg)

[Figure 11.3](#ch18.xhtml#f144b)Code snippet to look at the dataset.

info() gives us information about the structure of our dataset, whereas describe() gets a summary of the statistics of our dataset. Both are seen in [Figures 11.4](#ch18.xhtml#f145) and [11.5](#ch18.xhtml#f146).

![Figure 11.4Acquiring information from the dataset.](html/images/9781032676654_C011_004.jpg)

[Figure 11.4](#ch18.xhtml#f145b)Acquiring information from the dataset.

![Figure 11.5Acquiring description of the dataset.](html/images/9781032676654_C011_005.jpg)

[Figure 11.5](#ch18.xhtml#f146b)Acquiring description of the dataset.

By exploring the dataset, it is evident that the Booking\_ID column is not necessary for the predictions, so using the drop() function, we are able to drop the Booking\_ID from the dataframe. Later, we used isnull().sum() to check for missing values, and it is evident that there are no missing values in our dataset. See [Figure 11.6](#ch18.xhtml#f147).

![Figure 11.6Exploring the dataset.](html/images/9781032676654_C011_006.jpg)

[Figure 11.6](#ch18.xhtml#f147b)Exploring the dataset.

## 11.3 Exploratory data analysis (EDA)

To check for class imbalance, we have used the countplot as depicted in [Figure 11.7](#ch18.xhtml#f148) to visualize the distribution of our target label, which is the booking status. It’s clear that there is a variation between canceled and not-canceled classes. In later steps, we will take the necessary actions to overcome this issue.

![Figure 11.7Visualization.](html/images/9781032676654_C011_007.jpg)

[Figure 11.7](#ch18.xhtml#f148b)Visualization.

A simple correlation heatmap is created by following the code snippet as shown in [Figure 11.8](#ch18.xhtml#f149). We analyze and visualize the relationship between variables in the dataset as illustrated in [Figure 11.9](#ch18.xhtml#f150).

![Figure 11.8Code to Generate a Correlation heatmap.](html/images/9781032676654_C011_008.jpg)

[Figure 11.8](#ch18.xhtml#f149b)Code to Generate a Correlation heatmap.

![Figure 11.9Generated Correlation heatmap.](html/images/9781032676654_C011_009.jpg)

[Figure 11.9](#ch18.xhtml#f150b)Generated Correlation heatmap.

We then use boxplot as provided in [Figure 11.10](#ch18.xhtml#f151) to compare the room types based on the average price per room.

![Figure 11.10Boxplot for comparison.](html/images/9781032676654_C011_010.jpg)

[Figure 11.10](#ch18.xhtml#f151b)Boxplot for comparison.

The particular code snippet shown in [Figure 11.11](#ch18.xhtml#f152) gives us the unique values present in the columns room\_type\_reserved,market\_segment\_type, type\_of\_meal\_plan, and booking\_status.

![Figure 11.11Code snippet to find unique values.](html/images/9781032676654_C011_011.jpg)

[Figure 11.11](#ch18.xhtml#f152b)Code snippet to find unique values.

We then transform the data on the dataframe by mapping the unique strings we got from the previous stem to corresponding numeric values. See [Figure 11.12](#ch18.xhtml#f153) for the code snippet.

![Figure 11.12Data transformation.](html/images/9781032676654_C011_012.jpg)

[Figure 11.12](#ch18.xhtml#f153b)Data transformation.

## 11.4 Data splitting

In this step, we prepare the features and targets. We initialize by separating the features and target and store them in a variable X and y separately. Here, booking\_status is our target variable. Then we split the data into training and testing sets for which we use the train\_test\_split() function. 20% of the data is used for testing, and 80% is used for training as evident from [Figure 11.13](#ch18.xhtml#f154).

![Figure 11.13Code snippet for data splitting.](html/images/9781032676654_C011_013.jpg)

[Figure 11.13](#ch18.xhtml#f154b)Code snippet for data splitting.

As mentioned previously, we identify the class imbalance problem with our dataset. To handle this, we are oversampling the minority class. To upsample the minority class to that of the majority class, the resample() function is used. See [Figure 11.14](#ch18.xhtml#f155).

![Figure 11.14Code snippet for class imbalance problem.](html/images/9781032676654_C011_014.jpg)

[Figure 11.14](#ch18.xhtml#f155b)Code snippet for class imbalance problem.

## 11.5 Model building

For modeling, we use three different machine learning models: logistic regression, decision tree classification, and random forest classification, and import the necessary packages to initialize them as illustrated in [Figure 11.15](#ch18.xhtml#f156). All these models are trained with the resampled training data created in the previous step.

![Figure 11.15Code snippet to import machine learning models.](html/images/9781032676654_C011_015.jpg)

[Figure 11.15](#ch18.xhtml#f156b)Code snippet to import machine learning models.

In the above code snippet of [Figure 11.16](#ch18.xhtml#f157), evaluate\_model() function is used to generate the classification reports, calculate the accuracy for each model and store them.

![Figure 11.16Code snippet for model evaluation.](html/images/9781032676654_C011_016.jpg)

[Figure 11.16](#ch18.xhtml#f157b)Code snippet for model evaluation.

## 11.6 Model evaluation and comparison

To understand more about the performance of each model we print the classification report and accuracy as in [Figure 11.17](#ch18.xhtml#f158).

![Figure 11.17Model evaluation and comparison.](html/images/9781032676654_C011_017.jpg)

[Figure 11.17](#ch18.xhtml#f158b)Model evaluation and comparison.

In order to provide a graphical representation of the accuracy of the various models, we construct a bar chart as seen in [Figure 11.18](#ch18.xhtml#f159). The graphic sheds light on which model is more accurate by providing insights into which model performs better.

![Figure 11.18Comparing model accuracies.](html/images/9781032676654_C011_018.jpg)

[Figure 11.18](#ch18.xhtml#f159b)Comparing model accuracies.

## 11.7 Conclusion

The power of data-driven decision-making in the hospitality industry has been brought to light as a result of the voyage via the “Hotel Reservation Dataset” exploration and prediction code. We were able to obtain priceless insights regarding booking patterns, client preferences, and market categories as a result of our painstaking dissection of the dataset. The utilization of exploratory data analysis (EDA) unearthed concealed patterns, which has assisted in our comprehension of the complex dynamic that exists between the many characteristics. We ensure that the dataset was ready for predictive modeling by performing meticulous preprocessing on it, which included managing cases of missing values and encoding categorical variables.

## 11.8 Further learning

In the future, we may investigate other ensemble learning methods in addition to simple bagging. These may include boosting (also known as AdaBoost and Gradient Boosting) and stacking, both of which have the potential to substantially improve model performance and robustness. Deepening your expertise in transforming and selecting features can help increase the interpretability and predictive power of models. Even feature engineering and selection can help with this.

## Suggested reading

*   Chatfield, C., 1986. Exploratory data analysis. European Journal of Operational Research, *23*(1), pp.5–13.

# Chapter 12Crop recommendation prediction

DOI: [10.1201/9781032676685-13](http://doi.org/10.1201/9781032676685-13)

## Learning objectives

After concluding this chapter, the reader shall be able to:

*   Address the challenge on crop recommendation through an ensemble learning method.
*   Build and integrate data analysis and predictive modeling.

## 12.1 Introduction

This chapter addresses the challenges faced on crop recommendation through an ensemble learning method. We predict the best suitable crop for a given set of soil and environmental properties. The dataset can be accessed using this link: [www.kaggle.com/datasets/atharvaingle/crop-recommendation-dataset](http://www.kaggle.com). This project lays the path for the next phase of precision farming, where technology meets cultivation to alter the way crops are picked and cultivated for maximum yields and ecological harmony. This research does this by integrating data analysis, preprocessing, and predictive modeling.

## 12.2 Data preprocessing

Importing the necessary libraries makes it easier to manipulate data, visualize it, develop models, and assess them.

Pandas, numpy, matplotlib for visualization, and numerous classifiers from scikit-Learn are some of these packages (see [Figure 12.1](#ch19.xhtml#f160)).

![Figure 12.1Code snippet to import necessary libraries.](html/images/9781032676654_C012_001.jpg)

[Figure 12.1](#ch19.xhtml#f160b)Code snippet to import necessary libraries.

We then use the pd.read\_csv as seen in [Figure 12.2](#ch19.xhtml#f161) to load the dataset to a variable data.

![Figure 12.2Code snippet to load the dataset.](html/images/9781032676654_C012_002.jpg)

[Figure 12.2](#ch19.xhtml#f161b)Code snippet to load the dataset.

After loading our dataset we use the head() function as illustrated in [Figure 12.3](#ch19.xhtml#f162) from the pandas library. This function will print the first five rows from our dataset. We get a clear initial idea about our dataset after this step. We have eight columns in our dataset and label is our target column; the label column has to be encoded since it has string values.

![Figure 12.3Using head() function.](html/images/9781032676654_C012_003.jpg)

[Figure 12.3](#ch19.xhtml#f162b)Using head() function.

To find out the number of missing or null values in each column of our dataset we use the isnull().sum() function to count the null values. In our dataset we don’t have any missing values (see [Figure 12.4](#ch19.xhtml#f163)).

![Figure 12.4To find missing values in the dataset.](html/images/9781032676654_C012_004.jpg)

[Figure 12.4](#ch19.xhtml#f163b)To find missing values in the dataset.

Previously we found there is a need to encode the label column. We use the LabelEncoder ([https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.LabelEncoder.html](https://scikit-learn.org)) as in [Figure 12.5](#ch19.xhtml#f164) from scikit-learn for this task. The method uses unique numerical values to convert the categorical columns to numeric. The resulting dataset is stored in a variable named “label\_encoded.” We then create two variables, X and y. In X we store all the features and drop the target variable and in y we store only the target variable.

![Figure 12.5Encoding the label column.](html/images/9781032676654_C012_005.jpg)

[Figure 12.5](#ch19.xhtml#f164b)Encoding the label column.

## 12.3 Data splitting

As we have already separated our dataset to X and y in the previous step, now we split the dataset into training and testing sets using the train\_test\_split function from scikit-learn. As discussed, X and y contain feature matrix and target vector respectively. The test size is 20% and train size is 80% as denoted in [Figure 12.6](#ch19.xhtml#f165). The random state sets the seed for reproducibility.

![Figure 12.6Code snippet to split the dataset.](html/images/9781032676654_C012_006.jpg)

[Figure 12.6](#ch19.xhtml#f165b)Code snippet to split the dataset.

## 12.4 Initialize base classifiers and bagging models

For modeling we have used the bootstrap aggregating method also known as bagging, which is an ensemble learning technique to boost accuracy and performance of our models. This is achieved by combining the predictions of multiple base models to make the overall prediction more accurate.

The base classifiers used are KNN, SVC and Logistic regression models which will act as weak learner for the bagging ensemble. The n\_estimators specify the number of base classifiers. This will allow the models to learn finding the optimized solution and diverse errors enhancing overall performance. Refer to [Figure 12.7](#ch19.xhtml#f166) for the code snippet.

![Figure 12.7Code snippet to initialize base classifiers.](html/images/9781032676654_C012_007.jpg)

[Figure 12.7](#ch19.xhtml#f166b)Code snippet to initialize base classifiers.

## 12.5 Training

We initiate a loop which trains and evaluates a series of bagging models that has been initialized by us. We use the fit method to train data and predict target using the predict method. The accuracy of all the models is computed and stored in a list called accuracies as depicted in [Figure 12.8](#ch19.xhtml#f167).

![Figure 12.8Model training and evaluation.](html/images/9781032676654_C012_008.jpg)

[Figure 12.8](#ch19.xhtml#f167b)Model training and evaluation.

## 12.6 Evaluation and comparison

A list called model\_names is created as shown in [Figure 12.9](#ch19.xhtml#f168) and the three model names are stored in it.

![Figure 12.9Model names for plotting.](html/images/9781032676654_C012_009.jpg)

[Figure 12.9](#ch19.xhtml#f168b)Model names for plotting.

Finally, we generate a bar plot as specified in [Figure 12.10](#ch19.xhtml#f169) to compare the accuracies of different models visually. Each bar present in the graph depicts different models and their accuracies. Logistic regression is the best performing model with respect to this dataset.

![Figure 12.10Accuracy Comparison.](html/images/9781032676654_C012_010.jpg)

[Figure 12.10](#ch19.xhtml#f169b)Accuracy Comparison.

## 12.7 Conclusion

This chapter delivers a thorough understanding of ensemble learning, bagging, and model evaluation, laying the groundwork for well-informed decision-making across a variety of domains. By enabling more precise and effective agricultural operations, the use of ensemble approaches to crop recommendation serves as an example of how machine learning can change agriculture.

## 12.8 Further learning

Consider exploring more complex ensemble techniques like Random Forests and Gradient Boosting, which provide improved predictive power through combined decision trees, for further development in the field of crop recommendation. Explore feature engineering to glean insightful information from agricultural data, and hyperparameter optimization to enhance model efficiency.

## Suggested reading

*   sklearn.preprocessing.LabelEncoder, scikit-learn 1.4.1, [https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.LabelEncoder.html](https://scikit-learn.org)

# Chapter 13Brain tumor classification

DOI: [10.1201/9781032676685-14](http://doi.org/10.1201/9781032676685-14)

## Learning objectives

After concluding this chapter, the reader shall be able to:

*   Solve image classification problem with the aid of deep learning models.
*   Train, test and classify the machine learning models.

## 13.1 Introduction

The main goal of this chapter is to demonstrate to the readers how to solve an image classification problem through the development of deep learning models. Medical image classification is a key part of the healthcare field. Diseases can be better diagnosed and treated if they are identified and put into categories. This will save lives, especially when brain cancers are found early. This project uses a set of MRI pictures of brain tumors as its dataset. It has pictures of different kinds of tumors and pictures that don’t have tumors. This collection gives us a great way to train and test our machine learning models. The dataset from Kaggle at [www.kaggle.com/datasets/sartajbhuvaji/brain-tumor-classification-mri](http://www.kaggle.com) is used for this task. For this classification job, we use VGG16 and ResNet50, which are both well-known architectures. The models will be taught to put MRI pictures into four different groups: “glioma\_tumor,” “meningioma\_tumor,” “no\_tumor,” and “pituitary\_tumor.”

## 13.2 Data preprocessing

We start by importing the necessary libraries for our classification task. The module will give us a way to interact with file paths, dictionaries, etc. numpy is imported to handle numerical operations, and matplotlib is used for visualizations and plots. Then we import the tensorflow module, which allows us to train the neural network frameworks. Followed by two of the pretrained models, VGG16 and ResNet50 from keras. Sequential is an API for building DNN models layer by layer. GlobalAveragePooling2D and Dense are the layers, and Dropout is to prevent overfitting. All can be seen in [Figure 13.1](#ch20.xhtml#f170).

![Figure 13.1To import necessary libraries.](html/images/9781032676654_C013_001.jpg)

[Figure 13.1](#ch20.xhtml#f170b)To import necessary libraries.

We then install the command opendatasets for downloading datasets that are openly available. We can fetch datasets online after this (see [Figure 13.2](#ch20.xhtml#f171)).

![Figure 13.2Code snippet to collect open datasets.](html/images/9781032676654_C013_002.jpg)

[Figure 13.2](#ch20.xhtml#f171b)Code snippet to collect open datasets.

Then we import the opendatasets library as od. We use the dataset link from Kaggle to download the Brain Tumor Classification Dataset. Before this step, make sure you download the Kaggle API credentials in your Kaggle account settings. The necessary steps are provided in [Figure 13.3](#ch20.xhtml#f172).

![Figure 13.3To import opendatasets libraries.](html/images/9781032676654_C013_003.jpg)

[Figure 13.3](#ch20.xhtml#f172b)To import opendatasets libraries.

Two different variables, data\_dir and classes, are declared, where the “data\_dir” variable contains the path to training data and “classes” contains the list of class labels for the image classification task. The code snippet for this is depicted in [Figure 13.4](#ch20.xhtml#f173).

![Figure 13.4Code snippet to define paths.](html/images/9781032676654_C013_004.jpg)

[Figure 13.4](#ch20.xhtml#f173b)Code snippet to define paths.

We generate a visual display from our test images of brain tumor classes randomly as shown in [Figure 13.5](#ch20.xhtml#f174).

![Figure 13.5Visual display of test images.](html/images/9781032676654_C013_005.jpg)

[Figure 13.5](#ch20.xhtml#f174b)Visual display of test images.

In this step, we set two of the hyperparameters, batch size and epochs, for training our models. The same can be seen in [Figure 13.6](#ch20.xhtml#f175). The batch size defines the number of samples that will be used during the forward and backward passes in the training phase. The epochs define the number of times the training takes place to update the model’s weights. We have to note that training the model with a large number of epochs will lead to over training. Likewise, training a few will lead to underfitting.

![Figure 13.6Setting hyperparameters.](html/images/9781032676654_C013_006.jpg)

[Figure 13.6](#ch20.xhtml#f175b)Setting hyperparameters.

We use the ImageDataGenerator class to clean and add to the data, and we make two data producers for the training and validation sets. ImageDataGenerator changes images in different ways, like resizing, rotating, etc., to add more variety to our collection. “flow\_from\_directory” is used to make the “train\_generator” for the training set. It looks for all the training pictures in the data\_dir directory. The size of the target picture is set to (224, 224), which is the same as the size of the input for models like VGG16 and ResNet50. The class\_mode is set to “categorical” because we have more than one class. Based on the validation\_split parameter, the training part of the data is chosen by setting the group parameter to “training.” We made a validation data generator with the same settings as train\_generator. Refer to [Figure 13.7](#ch20.xhtml#f176) for the code snippet.

![Figure 13.7Data preprocessing and augmentation.](html/images/9781032676654_C013_007.jpg)

[Figure 13.7](#ch20.xhtml#f176b)Data preprocessing and augmentation.

## 13.3 Modeling

We move on to create a VGG16-based neural network model as seen in [Figure 13.8](#ch20.xhtml#f177). We initialize by setting weights, excluding the output layer and specifying the input shape matching our input images and we stack all the layers sequentially. Finally, we compile the model.

![Figure 13.8To create a VGG16 model.](html/images/9781032676654_C013_008.jpg)

[Figure 13.8](#ch20.xhtml#f177b)To create a VGG16 model.

Following the same previous steps, the ResNet50 (Mukti and Biswas, 2019) model is also initialized with the process as provided in [Figure 13.9](#ch20.xhtml#f178).

![Figure 13.9To create a ResNet50 model.](html/images/9781032676654_C013_009.jpg)

[Figure 13.9](#ch20.xhtml#f178b)To create a ResNet50 model.

By calling the fit method we started training our VGG16 model (Qassim et al., 2018). This code as given in [Figure 13.10](#ch20.xhtml#f179) will train the model using training data generator and validate the model using validation data generator for 20 epochs.

![Figure 13.10Training the VGG16 model.](html/images/9781032676654_C013_010.jpg)

[Figure 13.10](#ch20.xhtml#f179b)Training the VGG16 model.

Using the same method followed earlier, we train the ResNet-50 model too as seen in [Figure 13.11](#ch20.xhtml#f180).

![Figure 13.11Training the ResNet-50 model.](html/images/9781032676654_C013_011.jpg)

[Figure 13.11](#ch20.xhtml#f180b)Training the ResNet-50 model.

## 13.4 Training accuracy comparison

A line plot is generated using the above code as in [Figure 13.12](#ch20.xhtml#f181). The training epochs are represented in the X-axis and Y-axis represents the accuracy.

![Figure 13.12Training accuracy plot.](html/images/9781032676654_C013_012.jpg)

[Figure 13.12](#ch20.xhtml#f181b)Training accuracy plot.

The VGG16-based model is trained and evaluated, yielding the following results:

*   Training accuracy: 73.66%
*   Validation accuracy: 69.28%

The ResNet50-based model is also trained and evaluated, resulting in the following outcomes:

*   Training accuracy: 95.17%
*   Validation accuracy: 72.60%

## 13.5 Conclusion

The findings of this chapter highlight the utility of deep learning models, in particular VGG16 and ResNet50, for the categorization of brain cancers based on MRI scans. Both models obtain encouraging levels of training accuracy, indicating that they are able to acquire relevant features by studying medical images.

## 13.6 Further works

Possible topics for further research in this field include:

*   Evaluation of the performance of the model using a separate test dataset in great detail.
*   Adjusting the model’s hyperparameters to get optimal generalization performance.
*   Methods of interpretability that allow for the gaining of insights into model decisions.
*   Implementation of a trained model as an integral component of a medical diagnosis system, accompanied by exhaustive clinical validation.

The application of machine learning to medical diagnosis carries with it a vast amount of untapped potential, making continued study in this field absolutely necessary for the advancement of patient care.

## Suggested readings

*   Mukti, I.Z. and Biswas, D., 2019, December. Transfer learning based plant diseases detection using ResNet50. In 2019 4th International Conference on Electrical Information and Communication Technology (EICT) (pp.1–6). IEEE.
*   Qassim, H., Verma, A. and Feinzimer, D., 2018, January. Compressed residual-VGG16 CNN model for big data places image recognition. In 2018 IEEE 8th Annual Computing and Communication Workshop and Conference (CCWC) (pp.169–175). IEEE.

# Chapter 14Exploratory data analysis and classification on wine quality dataset with oneAPI

DOI: [10.1201/9781032676685-15](http://doi.org/10.1201/9781032676685-15)

## Learning objectives

After reading this chapter, the reader shall be able to:

*   Acquire the knowledge to examine wine quality and classification through machine learning techniques by developing predictive models.
*   Gain information regarding exploratory data analysis.

## 14.1 Introduction

This study entails a thorough examination of wine quality and classification through the utilization of machine learning techniques. Our methodology is built on the bedrock of exploratory data analysis, also known as EDA. We perform an exhaustive investigation of the dataset’s complexities using EDA, which enables us to unearth previously concealed patterns, possible outliers, and important correlations between variables. The main objective of our study is to develop predictive models that can accurately forecast the quality of wine using a dataset comprising diverse parameters. In order to do this task, the initial step involves importing crucial libraries that are necessary for data manipulation, visualisation, and machine learning. These libraries include pandas, numpy, matplotlib, seaborn, and scikit-learn. The dataset, “WineQT.csv,” which is taken from kaggle: [https://www.kaggle.com/datasets/yasserh/wine-quality-dataset](https://www.kaggle.com) is loaded and subjected to preliminary data exploration in order to acquire a comprehensive understanding of its underlying structure.

## 14.2 Exploratory data analysis (EDA)

We engage in exploratory data analysis, also known as EDA, in order to acquire a more in-depth comprehension of our dataset. During this step, we create visualizations of the data such as histograms, box plots, and pair plots in order to discover patterns, relationships, and potential outliers in the information. These visualizations provide useful insights into the characteristics of wine, including the distribution of certain characteristics, the influence of characteristics on wine quality, and more.

The provided code as seen in [Figure 14.1](#ch21.xhtml#f182) primarily imports various Python libraries necessary for conducting data analysis and machine learning tasks, which are essential for this chapter. The seaborn and matplotlib libraries are commonly employed for the purpose of data visualization, while sklearn is utilized for machine learning operations. Additionally, pandas and numpy are employed for data manipulation and processing.

![Figure 14.1Importing the necessary libraries.](html/images/9781032676654_C014_001.jpg)

[Figure 14.1](#ch21.xhtml#f182b)Importing the necessary libraries.

Next, the dataset WineQT.csv is imported from Kaggle using the pd.read\_csv function, and afterwards stored in a pandas data frame. Then we use the .head() function to look at the first five rows of the dataset for initial analysis. Refer to [Figure 14.2](#ch21.xhtml#f183).

![Figure 14.2Code snippet to load the dataset.](html/images/9781032676654_C014_002.jpg)

[Figure 14.2](#ch21.xhtml#f183b)Code snippet to load the dataset.

In order to conduct a comprehensive examination of the numerical columns inside our dataset, we utilize the “describe()” function to obtain statistical measures such as the mean, standard deviation, minimum, maximum, and count and the same is shown in [Figure 14.3](#ch21.xhtml#f184).

![Figure 14.3Using describe() function.](html/images/9781032676654_C014_003.jpg)

[Figure 14.3](#ch21.xhtml#f184b)Using describe() function.

The alcohol concentration in wine is a significant determinant of its overall quality. In order to achieve a high level of quality, it is imperative that the subject matter be presented in a well-balanced manner. Now, let us proceed with the analysis of the alcohol characteristics. Initially, the sns.histplot function is employed to generate a histogram, which serves the purpose of visually representing the distribution of the alcohol characteristic as illustrated in [Figure 14.4](#ch21.xhtml#f185).

![Figure 14.4Generating a histogram.](html/images/9781032676654_C014_004.jpg)

[Figure 14.4](#ch21.xhtml#f185b)Generating a histogram.

Next, a boxplot is generated in order to assess the dispersion, skewness, and presence of outliers within our dataset. The sns.boxplot function is utilized to generate boxplots representing the distribution of alcohol and density across various degrees of wine quality. The visual representation depicted in the [Figure 14.5](#ch21.xhtml#f186) showcases black dots that are indicative of outliers.

![Figure 14.5Generating a boxplot.](html/images/9781032676654_C014_005.jpg)

[Figure 14.5](#ch21.xhtml#f186b)Generating a boxplot.

In order to examine the associations between various features, it is possible to build a pairplot as represented in [Figure 14.6](#ch21.xhtml#f187). In this analysis, the sns.pairplot function is employed to examine the association between the variables “fixed acidity” and “volatile acidity,” with a specific emphasis on their relationship with the variable “quality.”

![Figure 14.6Building a pairplot.](html/images/9781032676654_C014_006.jpg)

[Figure 14.6](#ch21.xhtml#f187b)Building a pairplot.

In this part, a pie chart displaying the distribution of wine quality levels throughout the dataset is created as in [Figure 14.7](#ch21.xhtml#f188) with the help of the plt.pie function.

![Figure 14.7pie chart display.](html/images/9781032676654_C014_007.jpg)

[Figure 14.7](#ch21.xhtml#f188b)pie chart display.

A table that summarizes the correlation coefficients between a number of different variables is known as a correlation matrix. In the fields of statistics and data analysis, it is a typical method that is used to investigate the correlations that exist between numerous variables at the same time. With the help of the data.corr() function, a correlation matrix of the dataset is created as in [Figure 14.8](#ch21.xhtml#f189). Then, it builds a heatmap for visualizing the correlation between the various features by making use of the sns.heatmap package.

![Figure 14.8Correlation Matrix Heatmap creation.](html/images/9781032676654_C014_008.jpg)

[Figure 14.8](#ch21.xhtml#f189b)Correlation Matrix Heatmap creation.

## 14.3 Data preprocessing and splitting

We use the isnull().sum() command as illustrated in [Figure 14.9](#ch21.xhtml#f190) to look at the null values present in the dataset. Here there are no null values present.

![Figure 14.9Look for null values in the dataset.](html/images/9781032676654_C014_009.jpg)

[Figure 14.9](#ch21.xhtml#f190b)Look for null values in the dataset.

The next step in processing our dataset is to separate it into a training set and a testing set. The train\_test\_split function found in the sklearn library is what we turn to in order to accomplish this. First, all of the features are entered into variable X, and the target column is entered into variable y. The feature data and the target data for both sets are stored in the variables X\_train, X\_test, y\_train, and y\_test respectively. Using the compute\_class\_weight function from sklearn will do the calculation to determine class weights in order to address class imbalance. It makes use of the “balanced” technique and computes weights for each of the classes contained in the training data. Refer to [Figure 14.10](#ch21.xhtml#f191) for the same.

![Figure 14.10Feature separation and dataset splitting.](html/images/9781032676654_C014_010.jpg)

[Figure 14.10](#ch21.xhtml#f191b)Feature separation and dataset splitting.

## 14.4 Modeling

After that, we use a technique called the Synthetic Minority Over-sampling Technique (SMOTE) to oversample the minority classes in the training data as shown in [Figure 14.11](#ch21.xhtml#f192). This allows us to get results that are more accurate. The SMOTE class found in the imblearn library is utilized by it. Then, we generate a list and initialize each model by employing the Random Forest, Decision Tree, and Gradient Boosting classifiers respectively. These models are going to undergo training and testing. Additionally, in order to get superior overall performance, each of these models has been tuned with oneAPI. In this case, we optimize using the one Data analytics library, which is abbreviated as oneDAL. The optimzation is explained in the notice that appears in a pop-up window below the cell highlighted in red.

![Figure 14.11To oversample the minority classes in the training data.](html/images/9781032676654_C014_011.jpg)

[Figure 14.11](#ch21.xhtml#f192b)To oversample the minority classes in the training data.

In order to show the results, we first generate an empty dictionary and then assign it to a variable that goes by the name results as depicted in [Figure 14.12](#ch21.xhtml#f193). The accuracy scores of our trained models will be stored here. After going through all of the models, the loop inserts the relevant results into the results dictionary as it proceeds to iterate through the models.

![Figure 14.12To show the results.](html/images/9781032676654_C014_012.jpg)

[Figure 14.12](#ch21.xhtml#f193b)To show the results.

## 14.5 Model comparison and visualization

The accuracy score for each model that is stored in the results dictionary is printed by this loop. [Figure 14.13](#ch21.xhtml#f194) illustrates the same.

![Figure 14.13Training and evaluation.](html/images/9781032676654_C014_013.jpg)

[Figure 14.13](#ch21.xhtml#f194b)Training and evaluation.

In this section, we will assess the accuracy of several different models by generating a bar plot as seen in [Figure 14.14](#ch21.xhtml#f195) with the sns.barplot package. For the purpose of making this comparison, it consults the accuracy scores that are saved in the results dictionary.

![Figure 14.14Model accuracy comparison.](html/images/9781032676654_C014_014.jpg)

[Figure 14.14](#ch21.xhtml#f195b)Model accuracy comparison.

## 14.6 Conclusion

Here we have provided a synopsis of the most important findings and outcomes of the chapter. We have explained any constraints or difficulties that were encountered throughout the course of the chapter and remark on the accuracy with which the machine learning models were able to forecast the wine quality. In addition to this, we investigated the models’ viability for use in the actual world.

## 14.7 Further learning

We encourage additional learning by recommending areas where the project could be extended or improved. Hopefully, this will inspire you to continue your own learning. We provide extra resources or courses for readers interested in delving deeper into machine learning and data analysis. Additionally, we provide recommendations for additional studies or methodologies that could improve the accuracy or insights provided by the models.

# Chapter 15Cats vs. Dogs classification using deep learning models optimized with oneAPI

DOI: [10.1201/9781032676685-16](http://doi.org/10.1201/9781032676685-16)

## Learning objectives

After concluding this chapter, the reader shall be able to:

*   Explore image categorization with data sets for deep learning research.
*   Train and evaluate neural network architectures.

## 15.1 Introduction

In this chapter, we explore the wonderful world of image categorization with the Kaggle dataset Cats vs. Dogs. The dataset is available to be accessed by clicking on the following link: [www.kaggle.com/datasets/shaunthesheep/microsoft-catsvsdogs-dataset](http://www.kaggle.com). A dataset comparing cats and dogs is chosen because it contains thousands of tagged images of cats and dogs, which is ideally suited to serve as a testing ground for deep learning research. Our objective is to train and evaluate two powerful neural network architectures, namely a proprietary Sequential model and a VGG16-based model, to determine the superior one in differentiating between the feline and canine companions that we know and love.

## 15.2 Data preprocessing

We begin by importing all of the libraries required for our image categorization operation. To do tasks involving data manipulation, fundamental libraries such as pandas and numpy are imported. We bring in matplotlib and seaborn so that we can do visualization. Importing the ImageDataGenerator class from TensorFlow’s Keras API allows for the first processing of picture data. Additionally, to create models layer by layer we import sequential. Optimizer adam is imported. The entire code snippet is presented in [Figure 15.1](#ch22.xhtml#f196).

![Figure 15.1To import necessary libraries.](html/images/9781032676654_C015_001.jpg)

[Figure 15.1](#ch22.xhtml#f196b)To import necessary libraries.

The TensorFlow library is utilized for the purpose of importing neural network models, defining layers, and conducting statistical and mathematical calculations as in [Figure 15.2](#ch22.xhtml#f197). The appearance of the red color pop-up notification indicates that Tensorflow has been optimized using the oneDNN package from oneAPI.

![Figure 15.2Utilizing tensorflow library.](html/images/9781032676654_C015_002.jpg)

[Figure 15.2](#ch22.xhtml#f197b)Utilizing tensorflow library.

In the provided code, a variable named “training\_data\_dir” is declared, and it is assigned the path to the data directory. The pixel values of the image are normalized by dividing each pixel value as 225. The photos are loaded into the directories training\_data\_dir and test\_data\_dir, with the classes “dogs” and “cats” being explicitly defined. A binary class mode is employed, where one class is assigned the label 0 and the other class is assigned the label 1 (see [Figure 15.3](#ch22.xhtml#f198)).

![Figure 15.3Declaring variables and path assignment.](html/images/9781032676654_C015_003.jpg)

[Figure 15.3](#ch22.xhtml#f198b)Declaring variables and path assignment.

The number of batches in both the training and test sets is determined and subsequently displayed as depicted in [Figure 15.4](#ch22.xhtml#f199).

![Figure 15.4To find batches in the data sets.](html/images/9781032676654_C015_004.jpg)

[Figure 15.4](#ch22.xhtml#f199b)To find batches in the data sets.

## 15.3 Custom sequential model

The code as given in [Figure 15.5](#ch22.xhtml#f200) shows an image classification neural network model constructed using the Sequential model from the keras API. The model is composed of convolutional layers that function as feature extractors by applying filters to input images and capturing patterns. Following the convolutions are Max-pooling layers, which reduce spatial dimensions while preserving essential features. The flattened layer converts the multidimensional output into a one-dimensional array, making it suitable for the fully connected layers. Dropout is a regularization technique that deactivates neurons at random during training to prevent overfitting. The final layers consist of densely interconnected (completely interconnected) layers that learn complex patterns and make predictions. Sigmoid activation in the output layer compresses the network’s output between 0 and 1, making it suitable for binary classification tasks and indicating the likelihood of an input belonging to a particular class. This architecture, which is commonly employed in image classification tasks, creates a neural network capable of learning intricate patterns from the image data provided.

![Figure 15.5Building the model.](html/images/9781032676654_C015_005.jpg)

[Figure 15.5](#ch22.xhtml#f200b)Building the model.

We compile the neural network training model. The optimizer, loss function, and metrics are defined as seen from [Figure 15.6](#ch22.xhtml#f201).

![Figure 15.6Compiling the model.](html/images/9781032676654_C015_006.jpg)

[Figure 15.6](#ch22.xhtml#f201b)Compiling the model.

![Figure 15.7Training the model.](html/images/9781032676654_C015_007.jpg)

[Figure 15.7](#ch22.xhtml#f202b)Training the model.

To prevent overfitting during training we implement early stopping with monitor, patience and restore\_best\_weights as parameters. Then using the fit method, we train the sequential model (refer to [Figure 15.7](#ch22.xhtml#f202)).

## 15.4 VGG16-based model

In this code, a pre-trained VGG16 model without its top classification layers is imported, specifically configured for 32x32 images with three color channels. This model that has been pre-trained is stored in the variable vgg\_base. Using the Sequential API, a new neural network model is then constructed. The VGG16 model is incorporated as the foundation of the new model. After the output of VGG16 has been flattened, two custom dense layers with 256 and 128 units, respectively, and ReLU activation functions are added. For binary classification, a dense layer with a single unit and sigmoid activation function is appended. This method leverages the VGG16-learned features while customizing the classification layers for a specific assignment, enabling efficient and effective transfer learning. Refer to [Figure 15.8](#ch22.xhtml#f203) for the code snippet.

![Figure 15.8Constructing the new model.](html/images/9781032676654_C015_008.jpg)

[Figure 15.8](#ch22.xhtml#f203b)Constructing the new model.

The provided code as in [Figure 15.9](#ch22.xhtml#f204) entails the compilation of the model using the Adam optimizer, employing a low learning rate, binary crossentropy loss function, and evaluating the model’s performance based on accuracy. The technique of early stopping is employed to observe the validation loss during the training process. If the validation loss does not exhibit any improvement for a consecutive period of five epochs, the training is halted. This approach guarantees the preservation of optimal weights. These setups are designed to optimize the training process, hence improving the accuracy of the model and mitigating the risk of overfitting.

![Figure 15.9Compiling the new model with Adam optimizer.](html/images/9781032676654_C015_009.jpg)

[Figure 15.9](#ch22.xhtml#f204b)Compiling the new model with Adam optimizer.

Then using the fit method, we train the vgg16 model with several parameters as shown in [Figure 15.10](#ch22.xhtml#f205).

![Figure 15.10Training the vgg16 model.](html/images/9781032676654_C015_010.jpg)

[Figure 15.10](#ch22.xhtml#f205b)Training the vgg16 model.

## 15.5 Accuracy comparison

We create two lists models and accuracies to store final end accuracies of all the models used (see [Figure 15.11](#ch22.xhtml#f206)). The accuracies stored in the list show the models’ capacity to accurately identify the training data, denoted as percentages.

![Figure 15.11For plotting Accuracy comparison.](html/images/9781032676654_C015_011.jpg)

[Figure 15.11](#ch22.xhtml#f206b)For plotting Accuracy comparison.

We use matplotlib to generate a bar graph to compare the levels of accuracy achieved during training by the Sequential model with the VGG16 model as illustrated in [Figure 15.12](#ch22.xhtml#f207).

![Figure 15.12Accuracy comparison.](html/images/9781032676654_C015_012.jpg)

[Figure 15.12](#ch22.xhtml#f207b)Accuracy comparison.

## 15.6 Conclusion

Using two very different but equally effective neural network topologies, we have investigated the complexities of picture categorization throughout the course of this chapter. Our investigation has revealed that the Sequential based model performed exceptionally well, highlighting the significance of transfer learning in situations where there is insufficient data. Despite this feat, there is still a large expanse of uncharted possibilities to investigate.

## 15.7 Further learning

When we look to the future, there are many different ways to improve the classification models being used for cats and dogs. The models might potentially be fine-tuned to produce even higher performance if intricate hyperparameter configurations are explored as part of the exploration process. It is possible that the models’ ability to generalize over a greater variety of real-world events can be improved by enhancing the dataset using a variety of transformations, in addition to utilizing sophisticated techniques such as mixup and cutmix. In addition, looking into more complicated designs such as ResNet, Inception, or EfficientNet might reveal improved feature extraction capabilities.

# Chapter 16Maximizing placement predictions with outlier removal

DOI: [10.1201/9781032676685-17](http://doi.org/10.1201/9781032676685-17)

## Learning objectives

After concluding this chapter, the reader shall be able to:

*   Explore the student placement details with machine learning techniques.
*   Familiarize themselves with predictive modeling.

## 16.1 Introduction

Data-driven decision-making is essential for achieving success in the ever-changing realm of college recruitment. This chapter aims to explore the intricacies of student placement through the utilization of machine learning techniques. The analysis is conducted based on the Kaggle Campus Recruitment dataset: [www.kaggle.com/datasets/benroshan/factors-affecting-campus-placement/](http://www.kaggle.com), which provides valuable insights into this domain. By employing a systematic methodology for data preprocessing and including novel methods for outlier detection and elimination, we delve into the core of predictive modeling. The notion is to provide educational institutions and recruiters with the necessary resources to make well-informed and strategic judgments regarding placements.

## 16.2 Data preprocessing and splitting

We are incorporating fundamental libraries that serve as the foundation for our data analysis and machine learning pursuits as witnessed in [Figure 16.1](#ch23.xhtml#f208). The libraries numpy and pandas are imported to handle data. The seaborn and matplotlib libraries are used for data visualization tasks. From the sklearn library we import the necessary models needed.

![Figure 16.1To import necessary libraries.](html/images/9781032676654_C016_001.jpg)

[Figure 16.1](#ch23.xhtml#f208b)To import necessary libraries.

We import our dataset and store it in a variable named “df.” We have a clear look at the first five rows of our imported dataset using the. head() command. It’s evident that our dataset has both numerical and string values which will be handled in further pre-processing steps. Refer to [Figure 16.2](#ch23.xhtml#f209) for the details.

![Figure 16.2Code snippet to load the dataset.](html/images/9781032676654_C016_002.jpg)

[Figure 16.2](#ch23.xhtml#f209b)Code snippet to load the dataset.

As we move forward let’s look at the number of missing values using isnull().sum() command as provided in [Figure 16.3](#ch23.xhtml#f210). As we have the result with us, we have 67 missing values in the salary column so let’s find a method to fill this.

![Figure 16.3To find the missing values.](html/images/9781032676654_C016_003.jpg)

[Figure 16.3](#ch23.xhtml#f210b)To find the missing values.

Here we fill the null values in the salary column. First, we access the salary column in the df Dataframe then using the fillna method we fill the NaN values in the salary column by median of non-missing values in the same column. Refer to [Figure 16.4](#ch23.xhtml#f211) for the code snippet.

![Figure 16.4Filling the null values.](html/images/9781032676654_C016_004.jpg)

[Figure 16.4](#ch23.xhtml#f211b)Filling the null values.

As we discussed previously, the dataframe consists of both numeric and categorical values so let’s now replace all the string values. Initially, we create an empty dictionary to store label encoder all the instances for each categorical column. Then we iterate through all the columns and find out the columns having object values. A labelencoder() object is created to encode all the categorical values in the dataframe. Using the .head() command we can see all our columns are numeric now. See [Figure 16.5](#ch23.xhtml#f212).

![Figure 16.5To encode values.](html/images/9781032676654_C016_005.jpg)

[Figure 16.5](#ch23.xhtml#f212b)To encode values.

Then we create the training and testing set. For this we first create a variable called features where we drop the target variable “status” and store all the features. Then we store our target column “status” in labels variable. Then using the train test split method we split the dataset into 80% of the data for Training and 20% for Testing as depicted in [Figure 16.6](#ch23.xhtml#f213).

![Figure 16.6Splitting the dataset.](html/images/9781032676654_C016_006.jpg)

[Figure 16.6](#ch23.xhtml#f213b)Splitting the dataset.

## 16.4 Outlier removal using Z-score

Outliers can be defined as data points that exhibit substantial deviation from the prevailing pattern observed within the sample. Instances of these phenomena may manifest as a result of a multitude of circumstances, including inaccuracies in data collecting, variations in measurement precision, or the occurrence of genuinely infrequent events. Although outliers can occasionally signify intriguing events, they can also inject extraneous data into our analysis, resulting in deceptive interpretations and forecasts. The Z-score, alternatively referred to as the standard score, holds significant importance as a fundamental statistical measure within the field of data analysis. The measure quantifies the number of standard deviations by which a given data point deviates from the mean of the dataset. By doing Z-score calculations on each data point, it is possible to detect values that deviate significantly from the mean and are likely to be considered outliers.

In columns “hsc\_p,” “degree\_p,” and “salary” we calculate the Z-scores and compare it with a defined threshold which is three in our case to identify and remove the outliers. Refer to [Figure 16.7](#ch23.xhtml#f214) for the code snippet.

![Figure 16.7To detect and remove outliers.](html/images/9781032676654_C016_007.jpg)

[Figure 16.7](#ch23.xhtml#f214b)To detect and remove outliers.

## 16.4 Modeling

Three distinct machine learning classifiers are instantiated, appended to a list along with their respective names, and a dictionary is established to record accuracy scores as provided in [Figure 16.8](#ch23.xhtml#f215).

![Figure 16.8Classifiers instantiation.](html/images/9781032676654_C016_008.jpg)

[Figure 16.8](#ch23.xhtml#f215b)Classifiers instantiation.

We train three different classifiers with our training data. We create a loop to iterate through the list containing the tuple of classifier objects which we created during the previous step. Then we fit the training data separated to the created models and calculate the accuracy using the test labels after we train the model. At last we print the accuracy of all the three models and the codes used is given in [Figure 16.9](#ch23.xhtml#f216).

![Figure 16.9Model training and evaluation.](html/images/9781032676654_C016_009.jpg)

[Figure 16.9](#ch23.xhtml#f216b)Model training and evaluation.

## 16.5 Model comparison and visualization

A bar graph is created as seen in [Figure 16.10](#ch23.xhtml#f217) to compare the accuracy scores of the three different machine learning models.

![Figure 16.10Model accuracy comparison.](html/images/9781032676654_C016_010.jpg)

[Figure 16.10](#ch23.xhtml#f217b)Model accuracy comparison.

## 16.6 Conclusion

In the context of campus recruitment, the foundation for effective placements is reliant on precise prognostications. The present comparative investigation sheds light on the trajectory forward, elucidating the merits and limitations of diverse machine learning algorithms. The Random Forest model emerges as the leading candidate, exhibiting a notable accuracy rate of 86.05%. This chapter offers insights into the realm of predictive modeling and empowers decision-makers with the necessary information to make informed decisions based on data in the recruitment process.

## 16.7 Further learning

As we conclude this chapter, it is imperative to recognize the extensive range of opportunities that awaits in the future. Potential areas for future investigation include the exploration of ensemble techniques, the application of feature engineering, and the examination of deep learning methodologies to further improve the accuracy of predictions. Moreover, a longitudinal analysis has the potential to provide useful insights into the evolving patterns of placement over a period of time, so enabling institutions to adjust their policies accordingly.

# Chapter 17A deep dive into Mushroom classification with oneAPI

DOI: [10.1201/9781032676685-18](http://doi.org/10.1201/9781032676685-18)

## Learning objectives

After reading this chapter, the reader shall be able to:

*   Acquire the knowledge to classify mushrooms through machine learning techniques.
*   Utilize diverse machine learning algorithms to achieve high accuracy.

## 17.1 Introduction

This chapter initiates an engaging exploration into the domain of machine learning, with the Mushroom classification dataset sourced from Kaggle, [www.kaggle.com/datasets/uciml/mushroom-classification/data](http://www.kaggle.com), as the primary reference. The information presented in the dataset encompasses a wide range of characteristics pertaining to mushrooms, hence inciting our inquisitiveness to delve into the realm of mycology from the perspective of data science and artificial intelligence. Through the utilization of diverse machine learning algorithms, our objective is to comprehend the intricacies involved in the classification of mushrooms, specifically distinguishing between edible and deadly types with a high level of accuracy.

## 17.2 Data preprocessing and splitting

To start with, we import several necessary libraries as presented in [Figure 17.1](#ch24.xhtml#f218). We import pandas and numpy to handle and manipulate data. We have done an extensive exploratory data analysis to import seaborn and matplotlib library. For modeling we import all the ML algorithms from the scikit-learn library. We have optimized all the machine learning models using Intel’s oneAPI tool and we have used some custom library for patching scikit-learn. The red colored pop-up message tells us that the environment is optimized with oneAPI.

![Figure 17.1Importing the libraries.](html/images/9781032676654_C017_001.jpg)

[Figure 17.1](#ch24.xhtml#f218b)Importing the libraries.

We then import the dataset and store it into a variable called data using the read\_csv command then we have a look at the first five rows of our dataset as seen in [Figure 17.2](#ch24.xhtml#f219). All the columns in our dataset are categorical so let us perform encoding in further steps.

![Figure 17.2Code snippet to import the dataset.](html/images/9781032676654_C017_002.jpg)

[Figure 17.2](#ch24.xhtml#f219b)Code snippet to import the dataset.

We check the dataset for null values; it is clear that no null values are present in our dataset as seen from the result of [Figure 17.3](#ch24.xhtml#f220).

![Figure 17.3Check for null values in the dataset.](html/images/9781032676654_C017_003.jpg)

[Figure 17.3](#ch24.xhtml#f220b)Check for null values in the dataset.

As already discussed, we have to convert all the categorical values available in our dataset to numeric. We use the LabelEncoder to convert categorical into numeric and the resultant data frame is stored in the variable data\_encoded. See [Figure 17.4](#ch24.xhtml#f221).

![Figure 17.4Using LabelEncoder.](html/images/9781032676654_C017_004.jpg)

[Figure 17.4](#ch24.xhtml#f221b)Using LabelEncoder.

## 17.3 Exploratory data analysis

In this section, we create various visualizations to understand the data better.

First, we create a pie chart to understand our target column “class” better. We have two unique values e and p in the column. We use the .value\_counts() command to count both the unique values and the results are stored and displayed. The code snippet of the same is provided in [Figure 17.5](#ch24.xhtml#f222).

![Figure 17.5To count the unique values.](html/images/9781032676654_C017_005.jpg)

[Figure 17.5](#ch24.xhtml#f222b)To count the unique values.

The red portion of [Figure 17.6](#ch24.xhtml#f223) corresponds to the proportion of poisonous mushrooms present in the dataset. The portion denoted in light blue is the proportion of edible mushrooms. The proportions of these classes are relatively comparable.

![Figure 17.6Target value distribution.](html/images/9781032676654_C017_006.jpg)

[Figure 17.6](#ch24.xhtml#f223b)Target value distribution.

We move on to check and analyze specific important columns in our dataset. Start with the “cap-shape” column and count the unique values that are sorted in descending values based on their occurrence time. Then the value counts are visualized with a barplot (Streit and Gehlenborg, 2014). It is clear that type X has the highest count and c has the lowest count among all, as evident from [Figure 17.7](#ch24.xhtml#f224).

![Figure 17.7Cap shape distribution.](html/images/9781032676654_C017_007.jpg)

[Figure 17.7](#ch24.xhtml#f224b)Cap shape distribution.

Once after importing the necessary libraries the figure size is set to 15 x 8 inches, a countplot is generated as in [Figure 17.8](#ch24.xhtml#f225) with seaborn in which the x-axis represents the cap-shape and hue is class. Custom colors are assigned to represent “Poisonous” and “Edible” classes.

![Figure 17.8Generating a countplot.](html/images/9781032676654_C017_008.jpg)

[Figure 17.8](#ch24.xhtml#f225b)Generating a countplot.

From the graph of [Figure 17.9](#ch24.xhtml#f226), the convex shaped cap has more poisonous as well as edible mushrooms followed by flat shaped mushrooms.

![Figure 17.9Distribution Types.](html/images/9781032676654_C017_009.jpg)

[Figure 17.9](#ch24.xhtml#f226b)Distribution Types.

The same method is followed to create a plot but the minor difference is in the distribution of mushrooms that are categorized by their classes and habitats, with all the specified customizations. Refer to [Figure 17.10](#ch24.xhtml#f227) for the code snippet.

![Figure 17.10Creating a Plot.](html/images/9781032676654_C017_010.jpg)

[Figure 17.10](#ch24.xhtml#f227b)Creating a Plot.

From [Figure 17.11](#ch24.xhtml#f228), it is evident that Woods is a great habitat whereas Waste is a bad habitat for mushrooms to be grown.

![Figure 17.11Distribution by habitat.](html/images/9781032676654_C017_011.jpg)

[Figure 17.11](#ch24.xhtml#f228b)Distribution by habitat.

## 17.4 Modeling and comparison

Now we move on to the modeling step for that. Initially we split our dataset into a testing and training set. All the features present in our dataframe are assigned to a variable called X and the target is stored in y. Then, using the train\_test\_split module, we split our dataset to 80% training and 20% testing set as illustrated in [Figure 17.12](#ch24.xhtml#f229).

![Figure 17.12Dataset splitting.](html/images/9781032676654_C017_012.jpg)

[Figure 17.12](#ch24.xhtml#f229b)Dataset splitting.

Several ML models are trained and evaluated with the testing data and the accuracy of all these models is printed down in the console. See [Figure 17.13](#ch24.xhtml#f230).

![Figure 17.13Model training and evaluation.](html/images/9781032676654_C017_013.jpg)

[Figure 17.13](#ch24.xhtml#f230b)Model training and evaluation.

A dictionary, model\_accuracies is created as in [Figure 17.14](#ch24.xhtml#f231) and the calculated accuracy scores using the accuracy\_score function is stored in it.

![Figure 17.14Using accuracy\_score function.](html/images/9781032676654_C017_014.jpg)

[Figure 17.14](#ch24.xhtml#f231b)Using accuracy\_score function.

The above code as in [Figure 17.15](#ch24.xhtml#f232) generates a bar plot which represents the accuracy of different models.

![Figure 17.15Bar plot generation.](html/images/9781032676654_C017_015.jpg)

[Figure 17.15](#ch24.xhtml#f232b)Bar plot generation.

The Support Vector Machine model performs best with 99% accuracy, closely followed by Logistic Regression on a par with Linear Discriminant Analysis with 95% accuracy, while Naive Bayes performs last with 92% accuracy as seen from [Figure 17.16](#ch24.xhtml#f233).

![Figure 17.16Model comparison.](html/images/9781032676654_C017_016.jpg)

[Figure 17.16](#ch24.xhtml#f233b)Model comparison.

## 17.5 Conclusion

This chapter has delved into the intriguing domain of mushroom classification through the implementation of machine learning methodologies. By employing preprocessing, visualization, and model training techniques, we have distinguished effectively and precisely between poisonous and palatable mushrooms. Our investigation serves to augment our comprehension of fungi while also highlighting the efficacy of machine learning in resolving complex practical challenges.

## 17.6 Further learning

Although our models have achieved noteworthy outcomes so far, the expedition remains ongoing. Subsequent pursuits may entail investigating novel methodologies, such as neural networks, in an effort to improve the precision of our categorizations. Furthermore, by expanding the datasets and investigating various deep learning architectures, it may be possible to discern particular mushroom species, thereby creating novel opportunities for further investigation and practical implementation.

## Suggested reading

*   Streit, M. and Gehlenborg, N., 2014. Bar charts and box plots: Creating a simple yet effective plot requires an understanding of data and tasks. Nature Methods, *11*(2), pp.117–118.

# Chapter 18Smart healthcareMachine learning approaches for kidney disease prediction with oneAPI

DOI: [10.1201/9781032676685-19](http://doi.org/10.1201/9781032676685-19)

## Learning Objectives

After reading this chapter, the reader shall be able to:

*   Acquire the knowledge to classify kidney disease through machine learning techniques.
*   Utilize diverse machine learning algorithms to accomplish enhanced diagnostic accuracy.

## 18.1 Introduction

The term “chronic kidney disease” refers to a disorder that affects a significant portion of the population and is defined by a steady loss of kidney function. It is essential to an effective management strategy to detect CKD in its earlier stages when it is still treatable. The Kaggle Chronic Kidney Disease dataset with the link given is used throughout this chapter as a basis for our classification of CKD using the capabilities of the machine learning: [www.kaggle.com/datasets/mansoordaku/ckdisease](http://www.kaggle.com). We hope to make a substantial contribution to the area of healthcare by greatly improving the diagnostic accuracy of chronic kidney disease (CKD) through the application of cutting-edge algorithms and data preparation strategies.

## 18.2 Data preprocessing and splitting

We first import the necessary libraries for data visualization, data manipulation, and model building. The red colored pop-up, as shown in [Figure 18.1](#ch25.xhtml#f234), tells us the whole code is optimized with oneAPI.

![Figure 18.1Importing the required libraries.](html/images/9781032676654_C018_001.jpg)

[Figure 18.1](#ch25.xhtml#f234b)Importing the required libraries.

We then import our dataset into the kernel and store it in a variable called data, and look at the first five rows of our imported dataset. It is clear from the inference that we have a mix of both numeric and categorical values, which will be taken care of in the further steps (see [Figure 18.2](#ch25.xhtml#f235)). We can also notice the presence of NaN (Not A Number) values (Chandradas, A., 2021) in some columns and the column ID seems irrelevant for finding our target variable. The Classification column is our target column.

![Figure 18.2To import the dataset.](html/images/9781032676654_C018_002.jpg)

[Figure 18.2](#ch25.xhtml#f235b)To import the dataset.

As discussed in the previous step, we will drop the ID column from our dataset using the drop function. Then we see the short summary of our data frame using the info() function as seen in [Figure 18.3](#ch25.xhtml#f236).

![Figure 18.3Using drop and info function.](html/images/9781032676654_C018_003.jpg)

[Figure 18.3](#ch25.xhtml#f236b)Using drop and info function.

We look at the unique values in each column of our dataset using the unique() function as shown in [Figure 18.4](#ch25.xhtml#f237). We check for mis-entered values in our dataset. Here we can see 43 is mistyped as “\\t43.” We manually check and change all the values in the next step.

![Figure 18.4Using unique function.](html/images/9781032676654_C018_004.jpg)

[Figure 18.4](#ch25.xhtml#f237b)Using unique function.

We use the replace() function and manually map the correct variables to the corresponding mistyped wrong variables which are found in the previous step. The replaced dataset is again stored in a duplicate variable called data (see [Figure 18.5](#ch25.xhtml#f238)).

![Figure 18.5Using replace function.](html/images/9781032676654_C018_005.jpg)

[Figure 18.5](#ch25.xhtml#f238b)Using replace function.

In the first step, upon looking at our dataset initially we find some missing values. We use the isnull().sum() command to look at the null values in our dataset and yes, we have missing values in almost all the columns (see [Figure 18.6](#ch25.xhtml#f239)).

![Figure 18.6To find the missing values.](html/images/9781032676654_C018_006.jpg)

[Figure 18.6](#ch25.xhtml#f239b)To find the missing values.

In this step, we create two variables num\_cols where we store all the columns with numeric values and cat\_cols with categorical columns. All these columns have some amount of missing values, which we will be replacing with two different methods. For the numeric columns we use the mean() method; that is, we calculate the mean value of a particular column and fill all the null values in the column. Similarly for the categorical column we use the backfill method in which we fill each of the null values with the next valid value in the column. See [Figure 18.7](#ch25.xhtml#f240) for the code snippet.

![Figure 18.7To replace the missing values.](html/images/9781032676654_C018_007.jpg)

[Figure 18.7](#ch25.xhtml#f240b)To replace the missing values.

After filling the null values as in [Figure 18.8](#ch25.xhtml#f241), we again look at the result.

![Figure 18.8Replacing the missing values.](html/images/9781032676654_C018_008.jpg)

[Figure 18.8](#ch25.xhtml#f241b)Replacing the missing values.

Let us first encode the categorical variables present in our dataset to numeric using the LabelEncoder method as shown in [Figure 18.9](#ch25.xhtml#f242). A variable cat\_cols is created in which a list containing the names of all categorical columns from our dataset is stored. Then, using the label encoder method, each column is converted to numerical values making it suitable for machine learning algorithms.

![Figure 18.9Using LabelEncoder method.](html/images/9781032676654_C018_009.jpg)

[Figure 18.9](#ch25.xhtml#f242b)Using LabelEncoder method.

Our dataset contains only numerical values now after encoding all the categorical columns and all the null values have been filled. The same can be seen in [Figure 18.10](#ch25.xhtml#f243).

![Figure 18.10Dataset after encoding.](html/images/9781032676654_C018_010.jpg)

[Figure 18.10](#ch25.xhtml#f243b)Dataset after encoding.

## 18.3 Modeling

Then we import the necessary libraries as represented in [Figure 18.11](#ch25.xhtml#f244) to create our models. For splitting the data into training and testing sets we first create two variables, X and y. In the variable X, we store all the features by dropping the target column classification. In y we store only the classification column. Then we split our data into a Training and testing set which is 80% and 20% respectively.

![Figure 18.11Importing necessary libraries.](html/images/9781032676654_C018_011.jpg)

[Figure 18.11](#ch25.xhtml#f244b)Importing necessary libraries.

The logistic regression (LR) classifier is initialized first as seen from [Figure 18.12](#ch25.xhtml#f245). Then we fit our training data to train our initialized logistic regression model. The predict function is used to make predictions on the test data.

![Figure 18.12Initializing LR Classifier.](html/images/9781032676654_C018_012.jpg)

[Figure 18.12](#ch25.xhtml#f245b)Initializing LR Classifier.

Here the SVM classifier is initialized and trained as depicted in [Figure 18.13](#ch25.xhtml#f246).

![Figure 18.13Initializing SVM Classifier.](html/images/9781032676654_C018_013.jpg)

[Figure 18.13](#ch25.xhtml#f246b)Initializing SVM Classifier.

Here the KNN classifier is initialized and trained as shown in [Figure 18.14](#ch25.xhtml#f247).

![Figure 18.14Initializing KNN Classifier.](html/images/9781032676654_C018_014.jpg)

[Figure 18.14](#ch25.xhtml#f247b)Initializing KNN Classifier.

## 18.4 Model comparison and visualization

We print the accuracy of our trained model. Logistic regression with 96.25% outperforms the other two models as illustrated in [Figure 18.15](#ch25.xhtml#f248).

![Figure 18.15Accuracy comparison.](html/images/9781032676654_C018_015.jpg)

[Figure 18.15](#ch25.xhtml#f248b)Accuracy comparison.

In this section we import the matplotlib library for visualization. Then we define a list of accuracy values corresponding to each model. A bar graph is then initialized as in [Figure 18.16](#ch25.xhtml#f249) in which the x-axis represents the model names and the y-axis represents the accuracy values.

![Figure 18.16Bar graph comparison.](html/images/9781032676654_C018_016.jpg)

[Figure 18.16](#ch25.xhtml#f249b)Bar graph comparison.

## 18.5 Conclusion

In summary, this study conducted a thorough examination of the renal illness dataset, encompassing the handling of missing values and the encoding of categorical variables. Subsequently, Logistic Regression, Support Vector Machine (SVM), and K-Nearest Neighbors (KNN) models were employed for the purpose of classification. The findings demonstrated favorable levels of accuracy: Logistic Regression reached a rate of 96.25%, SVM exhibited a rate of 65%, and KNN produced a rate of 82.81% accuracy on the test data.

## 18.6 Further learning

Possible improvements encompass the implementation of feature engineering techniques to capture intricate interactions, meticulous hyperparameter tuning, and comprehensive model evaluation that takes into account the metrics beyond accuracy. Feature selection approaches have the potential to improve the performance of models, while the investigation of ensemble techniques like Random Forest has the potential to augment prediction accuracy. Furthermore, the implementation of the most effective model in practical scenarios, along with continuous surveillance and the possibility of further training, remains crucial. Furthermore, the incorporation of model explainability methodologies could yield significant insights, hence guaranteeing the interpretability of forecasts in crucial fields such as healthcare. The pursuit of these potential areas of investigation has the potential to enhance the precision and dependability of renal disease prognostication.

## Suggested reading

*   Chandradas, A., 2021, September 20. 5 Methods to Check for NaN Values in Python. Medium. [https://towardsdatascience.com/5-methods-to-check-for-nan-values-in-in-python-3f21ddd17eed?gi=8eb57dd2f95b](https://towardsdatascience.com)

# Chapter 19A deep dive into multiclass flower classification with ResNet and VGG16 using oneAPI

DOI: [10.1201/9781032676685-20](http://doi.org/10.1201/9781032676685-20)

## Learning objectives

After reading this chapter, the reader shall be able to:

*   Acquire the knowledge to classify wide range of flowers through deep learning.
*   Utilize the pre-trained models ResNet and VGG16 to achieve classification accuracy.

## 19.1 Introduction

The classification of flowers, a fundamental topic within the field of computer vision, engrosses both researchers and admirers. This chapter delves into the realm of deep learning, with the objective of addressing the complex challenge of classifying a wide range of flowers. What is the primary area of our concentration? Leveraging two prominent contenders in the field of deep learning, namely ResNet and VGG16. By utilizing these pre-trained models, we initiate an engaging endeavor towards attaining accurate flower classification with a high level of precision. The available dataset taken from kaggle, [www.kaggle.com/datasets/kausthubkannan/5-flower-types-classification-dataset/data](http://www.kaggle.com), consists of the captivating floral species, namely Lilly, Lotus, Orchid, Sunflower, and Tulip. This not only renders our assignment scientifically engaging but also aesthetically wonderful.

## 19.2 Data preparation and visualization

We first import the opendatasets library, which will be used to download open source datasets directly from the internet as in [Figure 19.1](#ch26.xhtml#f250). Then the dataset link is pasted. Once after the authentication is done using the kaggle key, our dataset is successfully downloaded.

![Figure 19.1Importing the opendatasets library.](html/images/9781032676654_C019_001.jpg)

[Figure 19.1](#ch26.xhtml#f250b)Importing the opendatasets library.

This code imports the OS and we import ImageDataGenerator from tensorflow keras library that allows us to perform real-time data augmentation during the training period. The red colored pop-up of [Figure 19.2](#ch26.xhtml#f251) shows our code is optimized with oneAPI.

![Figure 19.2To perform real time data augmentation.](html/images/9781032676654_C019_002.jpg)

[Figure 19.2](#ch26.xhtml#f251b)To perform real time data augmentation.

The path of our downloaded dataset is stores in a variable called data\_dir. Dimensions are specified for images which will be resized accordingly. The batch size for training is specified in a variable named batch\_size and the same can be referred from [Figure 19.3](#ch26.xhtml#f252).

![Figure 19.3Path specification.](html/images/9781032676654_C019_003.jpg)

[Figure 19.3](#ch26.xhtml#f252b)Path specification.

To have a look at some images from each class we declare a variable class\_labels and map class indices to class names and retrieve one image from each class. Finally, all the images are displayed in a single row as depicted in [Figure 19.4](#ch26.xhtml#f253).

![Figure 19.4To visualize images.](html/images/9781032676654_C019_004.jpg)

[Figure 19.4](#ch26.xhtml#f253b)To visualize images.

## 19.3 Data preprocessing and augmentation

We configure the ImageDataGenerator with various inputs like rescale, zoom range etc. The validation\_split splits the dataset to 20% validation and 80% training. To look at the number of different classes present we print all the categories. Refer to [Figure 19.5](#ch26.xhtml#f254) for the code snippet.

![Figure 19.5Data Preprocessing and Augmentation.](html/images/9781032676654_C019_005.jpg)

[Figure 19.5](#ch26.xhtml#f254b)Data Preprocessing and Augmentation.

A generator object train\_generator and validation\_generator is created which will provide batches of augmented image data during training and validation period to our models.

To generate batches of augmented data from the directory datagen.flow\_from\_directory() is used as seen from [Figure 19.6](#ch26.xhtml#f255) and then we specify the path to the data directory. We resize our input images to specific dimensions and declare batch size, class mode which in our case is categorical and subset is also declared.

![Figure 19.6Generating batches of augmented data.](html/images/9781032676654_C019_006.jpg)

[Figure 19.6](#ch26.xhtml#f255b)Generating batches of augmented data.

Similarly, the validation\_generator is created for the validation subset declaring all the similar parameters as provided in the code snippet of [Figure 19.7](#ch26.xhtml#f256).

![Figure 19.7To validate data.](html/images/9781032676654_C019_007.jpg)

[Figure 19.7](#ch26.xhtml#f256b)To validate data.

## 19.4 Model building, compilation and training

For modeling, additional necessary libraries are imported. We first built our first model ResNet50 and compiled it with Adam optimizer and categorical cross entropy loss function. We train the model for 10 epochs using both the training and validation generators. Refer to [Figure 19.8](#ch26.xhtml#f257) for the code snippet.

![Figure 19.8To Build ResNet model.](html/images/9781032676654_C019_008.jpg)

[Figure 19.8](#ch26.xhtml#f257b)To Build ResNet model.

Similarly, we build the Vgg16 model with all input parameters as seen in [Figure 19.9](#ch26.xhtml#f258). The code snippet for compilation of the two models is provided in [Figure 19.10](#ch26.xhtml#f259).

![Figure 19.9To Build Vgg16 model.](html/images/9781032676654_C019_009.jpg)

[Figure 19.9](#ch26.xhtml#f258b)To Build Vgg16 model.

![Figure 19.10To compile models.](html/images/9781032676654_C019_010.jpg)

[Figure 19.10](#ch26.xhtml#f259b)To compile models.

The models’ testing accuracies are evaluated using the evaluate() method on the validation data generator, which is shown in [Figure 19.11](#ch26.xhtml#f260).

![Figure 19.11To calculate accuracies.](html/images/9781032676654_C019_011.jpg)

[Figure 19.11](#ch26.xhtml#f260b)To calculate accuracies.

## 19.5 Model evaluation and visualization

The testing accuracies of ResNet (Mirza et al., 2023) and VGG16 (Bakasa and Viriri, 2023) models are plotted using a bar graph as shown in [Figure 19.12](#ch26.xhtml#f261) for visual comparison. We create a list to store both our model names. Then the accuracies list is created where we store the testing accuracies of both our models. It is seen that the ResNet model exhibits superior performance with 81.10% of validation accuracy in comparison to the Vgg16 which has 75.30% of validation accuracy . This finding suggests that ResNet exhibits superior generalization performance on the validation dataset, implying its efficacy in collecting fundamental information for the task of flower categorization. Finally, the barplot is plotted.

![Figure 19.12For model evaluation and visualization.](html/images/9781032676654_C019_012.jpg)

[Figure 19.12](#ch26.xhtml#f261b)For model evaluation and visualization.

## 19.6 Conclusion

Within the domain of floral classification, our models have achieved resounding success. ResNet and VGG16, employing deep learning methodologies, have successfully discerned intricate details of floral specimens, resulting in notable levels of precision. This chapter serves as evidence of the integration of sophisticated algorithms and the aesthetic qualities inherent in the natural world. The capacity of the models to differentiate between Lilly and Lotus, Orchid and Sunflower, and Tulip and their respective counterparts exemplifies the convergence of technology and floral artistry.

## 19.7 Further learning

As we contemplate the future, multitudes of potentialities emerge. Engaging in the process of refining our models, investigating sophisticated architectures such as DenseNet and Inception, and delving into the realm of explainable AI present captivating opportunities. Moreover, the utilization of these models in practical contexts, such as the automation of flower identification in the field of horticulture, exhibits significant potential. The expedition does not conclude at this point; rather, it undergoes a metamorphosis, enticing us into unexplored frontiers inside the continuously developing realm of deep learning.

## Suggested readings

*   Bakasa, W. and Viriri, S., 2023. Vgg16 feature extractor with extreme gradient boost classifier for pancreas cancer prediction. Journal of Imaging, *9*(7), p.138.
*   Mirza, A.F., Mansoor, M., Usman, M. and Ling, Q., 2023. Hybrid Inception-embedded deep neural network ResNet for short and medium-term PV-Wind forecasting. Energy Conversion and Management, *294*, 117574.

# Chapter 20Dive into X (formerly Twitter’s) emotions using oneAPISentiment analysis with NLP

DOI: [10.1201/9781032676685-21](http://doi.org/10.1201/9781032676685-21)

## Learning objectives

By the end of this chapter, the reader shall be able to:

*   Acquire the knowledge to assess thoughts with deep learning capabilities.
*   Examine fundamental approaches in Natural Language Processing to design a robust deep learning model.

## 20.1 Introduction

In the contemporary era of digital technology, possessing the ability to comprehend and interpret human emotions as sent through internet platforms holds immense significance and worth. Sentiment analysis, an essential application of Natural Language Processing (NLP), enables the interpretation of sentiment expressed in textual data. This chapter initiates an engaging exploration, employing the capabilities of deep learning to assess thoughts expressed on the Twitter platform with a dataset extracted from Kaggle: [www.kaggle.com/datasets/kazanova/sentiment140](http://www.kaggle.com). In this study, we will examine fundamental approaches in Natural Language Processing (NLP), explore complex preprocessing methods, design a resilient deep learning model, and accurately decipher feelings.

## 20.2 Insights and preprocessing techniques in Natural Language Processing (NLP)

Natural Language Processing (NLP) is an interdisciplinary domain that integrates the fields of linguistics, computer science, and artificial intelligence (AI). Preprocessing is a crucial stage in natural language processing (NLP) that serves to improve the quality of data and facilitate the model’s comprehension. Within our repertoire of preprocessing techniques:

*    **Text Cleaning:** The process of cleaning raw Twitter data typically involves removing URLs, mentions, and hashtags, as they tend to clutter the data. The process of cleaning entails the removal of these artifacts, so assuring that the model is directed exclusively towards the textual essence.
*   **Tokenization:** Tokenization refers to the process of breaking down language into its constituent units, known as words, which serve as the fundamental building blocks of linguistic communication. Tokenization is a process that involves breaking down textual data into individual words or sub words, to establish a structured format that facilitates analysis.
*   **Padding and sequencing:** These are essential techniques in the context of neural networks, as they address the requirement for fixed-length inputs. The inclusion of padding in a dataset facilitates the achievement of consistency, hence enhancing the effectiveness of batch processing during the training phase. The process of sequencing involves the transformation of linguistic units into numerical representations, rendering them suitable for computational analysis using machine learning methods.
*   **Word embeddings:** Words possess intricate relationships. Word embeddings are a type of computational representation that convert words into vectors with a large number of dimensions. These vectors are designed to capture the semantic meanings and contextual nuances associated with the words. This modification improves the model’s comprehension of lexical relationships.

The dataset we are going to use is obtained from Kaggle using the opendatasets library. For handling the csv data, we import the pandas library as seen in [Figure 20.1](#ch27.xhtml#f262).

![Figure 20.1Importing the libraries.](html/images/9781032676654_C020_001.jpg)

[Figure 20.1](#ch27.xhtml#f262b)Importing the libraries.

Next we store our dataset in a variable called df. As we are handling categorical values, we declare special parameters like encoding = “latin” which will handle special characters. As we look at our dataset the first column is our target column. See [Figure 20.2](#ch27.xhtml#f263).

![Figure 20.2Loading the dataset.](html/images/9781032676654_C020_002.jpg)

[Figure 20.2](#ch27.xhtml#f263b)Loading the dataset.

For better understanding and accessibility, let us give our columns the actual names from the information obtained from the Kaggle website as shown in [Figure 20.3](#ch27.xhtml#f264).

![Figure 20.3To impart clarity.](html/images/9781032676654_C020_003.jpg)

[Figure 20.3](#ch27.xhtml#f264b)To impart clarity.

Now we are dropping all our unwanted columns like “id,” “query,” “date,” and ‘

“user\_id.” Then we map the unique values present in the column sentiment that is 0 and 4 with Negative and Positive respectively as provided in [Figure 20.4](#ch27.xhtml#f265).

![Figure 20.4Dropping unwanted columns.](html/images/9781032676654_C020_004.jpg)

[Figure 20.4](#ch27.xhtml#f265b)Dropping unwanted columns.

## 20.3 Text cleaning and tokenization

We first import the necessary libraries needed for text cleaning, padding, and tokenization. The Regular Expression (regex) module is also imported as seen from [Figure 20.5](#ch27.xhtml#f266) which will allow us to do text manipulation. Then we clean the text which removes URLs, multiple spaces, hashtags etc.

![Figure 20.5For text cleaning.](html/images/9781032676654_C020_005.jpg)

[Figure 20.5](#ch27.xhtml#f266b)For text cleaning.

A histogram is plotted to find the maximum sequence length as depicted in [Figure 20.6](#ch27.xhtml#f267). The sequence length variable will calculate the length of each sequence in the list “X.” By observing the graph, it is seen around 10.0, so we can assign 10 as our maxlen.

![Figure 20.6Histogram Plotting.](html/images/9781032676654_C020_006.jpg)

[Figure 20.6](#ch27.xhtml#f267b)Histogram Plotting.

Tokenization is performed by declaring the tokenizer class as illustrated in [Figure 20.7](#ch27.xhtml#f268). The num words specify the maximum number of unique words to tokenize and outside limit words are marked as <00V>. Then the texts are converted into sequences and padded to maintain the same length. In this case, the sequences are padded to a maximum length of 10 based on the histogram plot mentioned earlier.

![Figure 20.7Tokenization.](html/images/9781032676654_C020_007.jpg)

[Figure 20.7](#ch27.xhtml#f268b)Tokenization.

![Figure 20.8Initializing OneHotEncoder.](html/images/9781032676654_C020_008.jpg)

[Figure 20.8](#ch27.xhtml#f269b)Initializing OneHotEncoder.

We import and initialize OneHotEncoder as in [Figure 20.8](#ch27.xhtml#f269) to reshape our sentiment column into a 2-D array structure. After this operation, the y variable contains the one-hot encoded representation of the “sentiment” column. The red colored pop-up indicates that our code has been optimized with oneAPI for improved performance.

## 20.4 Model building, compilation, and training

A Neural network model is then created using keras for classifying the texts. We use a sequential model that has a linear stack of layers. First, an embedding layer is used to convert integers into dense vectors, followed by an LSTM (Long Short-Term Memory) layer capable of learning long-term dependencies. Finally, the output layer for binary classification is used. The model is then compiled with Adam optimizer.

The data is now split into training and testing sets as seen in [Figure 20.9](#ch27.xhtml#f270) and is fitted for training.

![Figure 20.9Model creation.](html/images/9781032676654_C020_009.jpg)

[Figure 20.9](#ch27.xhtml#f270b)Model creation.

Evaluating the model on testing data is seen to achieve an accuracy of 79.85%, as evident from [Figure 20.10](#ch27.xhtml#f271).

![Figure 20.10Dataset splitting.](html/images/9781032676654_C020_010.jpg)

[Figure 20.10](#ch27.xhtml#f271b)Dataset splitting.

We utilize the trained model for the purpose of generating predictions on new data, namely new\_texts. The text sequences should be tokenized and padded before utilizing the model for sentiment label prediction. The function encoder.inverse\_transform is employed to reverse the encoding process and convert the predicted values back to their original labels. The anticipated classifications are displayed as the resulting output (refer to [Figures 20.11 and 20.12](#ch27.xhtml#f272)).

![Figure 20.11Model evaluation.](html/images/9781032676654_C020_011.jpg)

[Figure 20.11](#ch27.xhtml#f272b)Model evaluation.

## 20.5 Conclusion

The present study involved the processing and utilization of a X (formerly known as Twitter) sentiment analysis dataset obtained from Kaggle. The dataset was employed to construct a resilient sentiment analysis model utilizing LSTM neural networks. The dataset underwent preprocessing procedures that involved many steps. Firstly, the sentiment values were mapped to the categories of “Negative” and “Positive.” Secondly, the text data was cleaned by eliminating URLs and special characters. Lastly, the text was tokenized into numerical sequences and padded accordingly. The dataset consisted of various columns including “sentiment,” “id,” “date,” “query,” “user\_id,” and “text.” Subsequently, a Long Short-Term Memory (LSTM) model was developed, comprising an embedding layer to represent words, an LSTM layer to capture sequential patterns, and a dense output layer for the purpose of binary classification. The model underwent training using preprocessed data, resulting in significant accuracy improvements over multiple epochs. Finally, the model effectively made accurate predictions regarding feelings for novel textual instances, showcasing its practicality in the context of sentiment analysis tasks in real-world scenarios.

## 20.6 Further learning

The current investigation focused on the processing and utilization of a dataset for Twitter sentiment analysis, which was acquired from Kaggle. The dataset was utilized for the purpose of constructing a robust sentiment analysis model by employing LSTM neural networks. The dataset underwent a series of preprocessing operations that encompassed multiple steps. Initially, the sentiment values were assigned to the respective categories of “Negative” and “Positive.” Furthermore, the text data underwent a cleaning process wherein URLs and unusual characters were removed. Finally, the text underwent tokenization to convert it into numerical sequences, which were then appropriately padded. The dataset comprised several columns, namely “sentiment,” “id,” “date,” “query,” “user\_id,” and “text.” Following this, a Long Short-Term Memory (LSTM) model was constructed, consisting of an embedding layer to encode word representations, an LSTM layer to record sequential patterns, and a dense output layer for binary classification. The model was subjected to a training process utilizing preprocessed data, which led to notable enhancements in accuracy across many epochs. Ultimately, the model successfully generated precise predictions pertaining to emotions for unfamiliar textual examples, so demonstrating its usefulness within the realm of sentiment analysis applications in real-life situations.

# Index

*   accuracy [100](#ch14.xhtml#p100)
*   artificial intelligence [1](#ch07.xhtml#p1), [3](#ch07.xhtml#p3), [18](#ch07.xhtml#p18)

*   bankruptcy risk prediction [129](#ch17.xhtml#p129)
*   brain tumor classification [157](#ch20.xhtml#p157)
*   breast cancer classification [65](#ch11.xhtml#p65)

*   Cats *vs.* Dogs classification [179](#ch22.xhtml#p179)
*   classification with ML [34](#ch08.xhtml#p34)
*   class imbalance and oversampling [57](#ch10.xhtml#p57)
*   class imbalance problem [54](#ch10.xhtml#p54)
*   convolutional neural network (CNN) [46](#ch09.xhtml#p46)
*   CPU [18](#ch07.xhtml#p18)
*   crop recommendation prediction [151](#ch19.xhtml#p151)
*   CUDA [21](#ch07.xhtml#p21)

*   data splitting [143](#ch18.xhtml#p143), [153](#ch19.xhtml#p153)
*   DecisionTreeClassifier [35](#ch08.xhtml#p35), [37](#ch08.xhtml#p37), [62](#ch10.xhtml#p62), [112](#ch15.xhtml#p112)
*   deep learning [1](#ch07.xhtml#p1), [5](#ch07.xhtml#p5), [14](#ch07.xhtml#p14), [17](#ch07.xhtml#p17)
*   diabetes [99](#ch14.xhtml#p99)
*   DPC++ [21](#ch07.xhtml#p21), [22](#ch07.xhtml#p22)
*   drug classification [90](#ch13.xhtml#p90)

*   ensemble learning [122](#ch16.xhtml#p122)
*   evaluating model performance [99](#ch14.xhtml#p99)
*   evolutinary learning [12](#ch07.xhtml#p12)
*   exploratory data analysis [57](#ch10.xhtml#p57), [66](#ch11.xhtml#p66), [166](#ch21.xhtml#p166)

*   flower recognition [80](#ch12.xhtml#p80)
*   FPGA [18](#ch07.xhtml#p18)
*   F1 score [100](#ch14.xhtml#p100)

*   Gaussian Naive Bayes [61](#ch10.xhtml#p61)
*   GPU [18](#ch07.xhtml#p18)

*   heart failure prediction [40](#ch09.xhtml#p40)
*   hotel reservation prediction [139](#ch18.xhtml#p139)
*   hybrid ML model [74](#ch11.xhtml#p74)
*   hyperparameter tuning [93](#ch13.xhtml#p93)

*   importing libraries [41](#ch09.xhtml#p41)
*   Inte Advisor [22](#ch07.xhtml#p22)
*   Intel Developer Cloud  [25–7](#ch07.xhtml#p25)
*   Iris dataset [31](#ch08.xhtml#p31)

*   JupyterLab [30](#ch07.xhtml#p30)

*   Kaggle [80](#ch12.xhtml#p80), [81](#ch12.xhtml#p81)
*   KNeighborsClassifier [34](#ch08.xhtml#p34), [65](#ch11.xhtml#p65), [91](#ch13.xhtml#p91)

*   logistic regression [34](#ch08.xhtml#p34), [37](#ch08.xhtml#p37), [101](#ch14.xhtml#p101), [61](#ch10.xhtml#p61)
*   long short-term memory [246](#ch27.xhtml#p246)

*   machine learning framework  [1–4](#ch07.xhtml#p1), [14](#ch07.xhtml#p14)
*   machine learning *vs.* deep learning [14](#ch07.xhtml#p14)
*   maximizing placement predictions [191](#ch23.xhtml#p191)
*   metrics [35](#ch08.xhtml#p35), [37](#ch08.xhtml#p37), [91](#ch13.xhtml#p91)
*   multiclass flower classification [228](#ch26.xhtml#p228)
*   Mushroom classification [199](#ch24.xhtml#p199)

*   natural language processing (NLP) [237](#ch27.xhtml#p237)

*   oneAPI  [18–20](#ch07.xhtml#p18)
*   oneAPI Collective Communications [24](#ch07.xhtml#p24)
*   oneAPI Data Analytics Library [23](#ch07.xhtml#p23)
*   oneAPI Data Transformation Library [24](#ch07.xhtml#p24)
*   oneAPI Deep Neural Network Library [23](#ch07.xhtml#p23)
*   oneAPI DPC+ + Library [24](#ch07.xhtml#p24)
*   oneAPI Image Processing Library [24](#ch07.xhtml#p24)
*   oneAPI Math Kernel Library [22](#ch07.xhtml#p22)
*   oneAPI threading Building Blocks [23](#ch07.xhtml#p23)
*   oneAPI Video Processing Library [23](#ch07.xhtml#p23)
*   outlier detection [112](#ch15.xhtml#p112)

*   padding and sequencing [238](#ch27.xhtml#p238)
*   pandas [41](#ch09.xhtml#p41)
*   Parkinson’s disease detection [110](#ch15.xhtml#p110)
*   polynomial feature engineering [117](#ch15.xhtml#p117)
*   the power of oneAPI [21](#ch07.xhtml#p21)
*   precision [100](#ch14.xhtml#p100)
*   preprocessing [55](#ch10.xhtml#p55)
*   programming challenges [19](#ch07.xhtml#p19)

*   Random Forest classifier [46](#ch09.xhtml#p46)
*   recall [100](#ch14.xhtml#p100)
*   reinforced learning [12](#ch07.xhtml#p12), [13](#ch07.xhtml#p13)
*   relationship between AI, ML and DL [3](#ch07.xhtml#p3)
*   ROC AUC Score [100](#ch14.xhtml#p100)

*   scaling features [66](#ch11.xhtml#p66), [114](#ch15.xhtml#p114)
*   sklearn [34](#ch08.xhtml#p34)
*   Smart healthcare [215](#ch25.xhtml#p215)
*   supervised learning [7](#ch07.xhtml#p7), [9](#ch07.xhtml#p9)
*   SVM [65](#ch11.xhtml#p65)
*   SYCL [23](#ch07.xhtml#p23)
*   Synthetic Minority Over-sampling technique [172](#ch21.xhtml#p172)

*   TensorFlow [19](#ch07.xhtml#p19), [46](#ch09.xhtml#p46), [81](#ch12.xhtml#p81), [179](#ch22.xhtml#p179)
*   text cleaning [239](#ch27.xhtml#p239)
*   tokenization [238](#ch27.xhtml#p238)
*   train\_test\_split [34](#ch08.xhtml#p34), [35](#ch08.xhtml#p35), [41](#ch09.xhtml#p41), [44](#ch09.xhtml#p44), [58](#ch10.xhtml#p58)
*   types of machine learning [5](#ch07.xhtml#p5)

*   unsupervised learning [9](#ch07.xhtml#p9), [11](#ch07.xhtml#p11), [12](#ch07.xhtml#p12)

*   VGG16 [183](#ch22.xhtml#p183)
*   VTune Profiler [22](#ch07.xhtml#p22)

*   water quality [54](#ch10.xhtml#p54)
*   why do we need ML? [12](#ch07.xhtml#p12)
*   word embeddings [238](#ch27.xhtml#p238)

*   X [237](#ch27.xhtml#p237)
*   XGBoost [40](#ch09.xhtml#p40), [41](#ch09.xhtml#p41), [46](#ch09.xhtml#p46)

*   Z-score [192](#ch23.xhtml#p192)