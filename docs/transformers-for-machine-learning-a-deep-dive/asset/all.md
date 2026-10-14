![](images/cover.jpg)

![Cover: Transformers for Machine Learning: A Deep Dive, Chapman & Hall/CRC Machine Learning & Pattern Recognition, written by Uday Kamath, Kenneth L. Graham, Wael Emara, published by CRC Press, Taylor and Francis Group, Boca Raton, London, New York, CRC Press is an imprint of the Taylor and Francis Group, an informa business, a Chapman and Hall book.](images/cover.jpg)

# Chapman & Hall/CRC Machine Learning & Pattern Recognition

**A First Course in Machine Learning**

Simon Rogers, Mark Girolami

**Statistical Reinforcement Learning: Modern Machine Learning Approaches**

Masashi Sugiyama

**Sparse Modeling: Theory, Algorithms, and Applications**

Irina Rish, Genady Grabarnik

**Computational Trust Models and Machine Learning**

Xin Liu, Anwitaman Datta, Ee-Peng Lim

**Regularization, Optimization, Kernels, and Support Vector Machines**

Johan A.K. Suykens, Marco Signoretto, Andreas Argyriou

**Machine Learning: An Algorithmic Perspective, Second Edition**

Stephen Marsland

**Bayesian Programming**

Pierre Bessiere, Emmanuel Mazer, Juan Manuel Ahuactzin, Kamel Mekhnacha

**Multilinear Subspace Learning: Dimensionality Reduction of Multidimensional Data**

Haiping Lu, Konstantinos N. Plataniotis, Anastasios Venetsanopoulos

**Data Science and Machine Learning: Mathematical and Statistical Methods**

Dirk P. Kroese, Zdravko Botev, Thomas Taimre, Radislav Vaisman

**Deep Learning and Linguistic Representation**

Shalom Lappin

**Artificial Intelligence and Causal Inference**

Momiao Xiong

**Introduction to Machine Learning with Applications in Information Security, Second Edition**

Mark Stamp

**Entropy Randomization in Machine Learning**

Yuri S. Popkov, Alexey Yu. Popkov, Yuri A. Dubno

**Transformers for Machine Learning: A Deep Dive**

Uday Kamath, Kenneth L. Graham, and Wael Emara

For more information on this series please visit: [https://www.routledge.com/​Chapman--HallCRC-Machine-Learning--Pattern-Recognition/​book-series/​CRCMACLEAPAT](https://www.routledge.com/Chapman--HallCRC-Machine-Learning--Pattern-Recognition/book-series/CRCMACLEAPAT)

First edition published 2022

by CRC Press

6000 Broken Sound Parkway NW, Suite 300, Boca Raton, FL 33487-2742

and by CRC Press

4 Park Square, Milton Park, Abingdon, Oxon, OX14 4RN

*CRC Press is an imprint of Taylor & Francis Group, LLC*

© 2022 Uday Kamath, Kenneth L. Graham and Wael Emara

Reasonable efforts have been made to publish reliable data and information, but the author and publisher cannot assume responsibility for the validity of all materials or the consequences of their use. The authors and publishers have attempted to trace the copyright holders of all material reproduced in this publication and apologize to copyright holders if permission to publish in this form has not been obtained. If any copyright material has not been acknowledged please write and let us know so we may rectify in any future reprint.

Except as permitted under U.S. Copyright Law, no part of this book may be reprinted, reproduced, transmitted, or utilized in any form by any electronic, mechanical, or other means, now known or hereafter invented, including photocopying, microfilming, and recording, or in any information storage or retrieval system, without written permission from the publishers.

For permission to photocopy or use material electronically from this work, access [www.copyright.com](http://www.copyright.com) or contact the Copyright Clearance Center, Inc. (CCC), 222 Rosewood Drive, Danvers, MA 01923, 978-750-8400. For works that are not available on CCC please contact [mpkbookspermissions@tandf.co.uk](mailto:mpkbookspermissions@tandf.co.uk)

*Trademark notice*: Product or corporate names may be trademarks or registered trademarks and are used only for identification and explanation without intent to infringe.

Library of Congress Cataloging‑in‑Publication Data

Names: Kamath, Uday, author.

Title: Transformers for machine learning : a deep dive / Uday Kamath, Kenneth L. Graham, Wael Emara.

Description: First edition. | Boca Raton : CRC Press, 2022. | Includes bibliographical references and index.

Identifiers: LCCN 2021059529 | ISBN 9780367771652 (hardback) | ISBN 9780367767341 (paperback) | ISBN 9781003170082 (ebook)

Subjects: LCSH: Neural networks (Computer science). | Computational intelligence. | Machine learning.

Classification: LCC QA76.87 .K354 2022 | DDC 006.3/2‑‑dc23/eng/20220218

LC record available at [https://lccn.loc.gov/​2021059529](https://lccn.loc.gov/​2021059529)

ISBN: 978-0-367-77165-2 (hbk)

ISBN: 978-0-367-76734-1 (pbk)

ISBN: 978-1-003-17008-2 (ebk)

DOI: [10.1201/9781003170082](https://doi.org/10.1201/9781003170082)

Typeset in Latin Modern font

by KnowledgeWorks Global Ltd.

*Publisher's note:* This book has been prepared from camera-ready copy provided by the authors.

*To all the researchers and frontline COVID workers for their extraordinary service.*

*– Uday Kamath, Kenneth L. Graham, and Wael Emara*

*To my parents Krishna and Bharathi, my wife Pratibha, the kids Aaroh and Brandy, my family and friends for their support.*

*–Uday Kamath*

*To my wife Alyson, to my mother, my in-laws, my family and friends, thank you for the support and your willingness to sacrifice your time with me.*

*–Kenneth L. Graham*

*To my wife Noha, my parents Ali and Zainab, my sister Wesam, my extended family and friends, thank you all for being there for me all the time.*

*–Wael Emara*

# Foreword

Renowned AI pioneer and Nobel laureate Herbert Simon underscored “attention” as the most valuable resource of the information economy, as necessary to allocate attention efficiently among the overabundance of information resources. Having written the foundational paper on meaning-aware AI and recently having served as MIT-Princeton-USAF-AFRL AI Faculty-SME, I had the privilege of publishing by invitation in the same journal's special issue of ASQ, and of being the Malcolm Baldrige National Quality Award administrator, as well as being ranked along with Dr. Simon in the same global academic citation impact studies.

Given the above background, I am thrilled to share with you the most thorough and up-to-date compendium of research, practices, case studies, and applications available today that can provide the best ROI on the latest AI technological advances on transformers inspired by the paper, “Attention is All You Need.” Since Google introduced transformer architecture in 2017, transformers have provided exponential improvements in context-focused realization toward meaning-aware AI as deep (neural network) learning models based upon attention mechanisms such as dot-product attention and multi-head attention. Resulting advances in enhanced parallel processing of sequential data have made efficient context sensitive and hence more “meaningful” for ever-larger datasets and much more feasible than earlier.

Covering the latest advances in neural network architectures related to transformers spanning applications such as Natural Language Processing (NLP), speech recognition, time series analysis, and computer vision and domain-specific models spanning science, medicine, and finance, the book aims to meet the theoretical, research, application, and practical needs across academia and industry for multiple audiences including postgraduate students and researchers, undergraduate students, industry practitioners, and professionals. The book rounds off its theory-driven applied and practical coverage with hands-on case studies with focus on AI explainability, an increasingly important theme in practice imposed by greater focus on issues such as ethical AI and trustable AI.

– Dr. Yogesh Malhotra

Founding Chairman and CEO

U.S. Venture Capital and Private Equity Firm

Global Risk Management Network LLC

scientist

[www.yogeshmalhotra.com](http://www.yogeshmalhotra.com)

# Preface

## Why this book?

Since 2012 deep learning architectures have started to dominate the machine learning field. However, most of the breakthroughs were in computer vision applications. The main driver of that success was convolutional neural network (CNN) architecture. The efficiency and parallelization of CNN have allowed computer vision architectures to pre-train on enormous data which proved to be a key factor in their success. For years afterward natural language processing (NLP) applications did not see much impact from the new deep learning revolution. Traditional sequence modeling architectures, such as recurrent neural networks (RNNs) and long short-term memory (LSTM), have been used for NLP applications. The sequential nature of such architectures has limited the possibilities to train on the same scale of data that showed value for computer vision.

In 2017 Google introduced the transformer architecture to process sequential data with much more parallelization. Such architecture allowed efficient training on much larger datasets than was possible before. This allowed transformers to revolutionize the NLP field the same way CNN had to computer vision.

Transformers are now becoming the core part of many neural architectures employed in a wide range of applications such as NLP, speech recognition, time series, and computer vision. OpenAI uses transformers in their GPT2/GPT3, which has state-of-the-art performances levels in various NLP tasks. DeepMind's AlphaStar program, which defeated a top professional Starcraft player, also uses transformer architecture. Transformers have gone through many adaptations and alterations, resulting in newer techniques and methods. There is no single book that captures the basics and various changes to the transformers in one place.

This book acts as a unique resource for providing data scientists and researchers (academic and industry) with

*   A comprehensive reference book for detailed explanations for every algorithm and technique related to transformers.
    
*   Over 60 transformer architectures covered in a comprehensive manner.
    
*   A book for understanding how to apply the transformer techniques in different NLP applications, speech, time series, and computer vision.
    
*   Practical tips and tricks for each architecture and how to use it in the real world.
    
*   Hands-on case studies providing practical insights to real-world scenarios in diverse topics such as machine translation, topic mining, zero-shot multilingual classification, sentiment analysis, automatic speech recognition, and text classification/categorization are covered in sufficient detail from the task, process, and analysis perspective, all ready to run in Google Colab.
    

## Who is this book written for?

The theoretical explanations of the state-of-the-art transformer architectures will appeal to postgraduate students and researchers (academic and industry) as it will provide a single-entry point with deep discussions of a quickly moving field. The practical hands-on case studies and code will appeal to undergraduate students, practitioners, and professionals as it allows for quick experimentation and lowers the barrier to entry into the field.

Transformers are already a cornerstone for NLP deep learning architectures. They are also rapidly employed in other applications such as computer vision and audio. Any course on neural networks, deep learning, or artificial intelligence must delve into discussing transformers as a key state-of-the-art architecture. The book can act as a reference for readers, to brush up on specific pieces of their understanding, or as a way to explore the uses of the transformer for specific challenges. We aim for the book to be a resource to refer back to multiple times, to gain insight and use as readers are faced with different challenges or when lacking understanding.

## What this book covers

This book takes an in-depth approach to presenting the fundamentals of transformers through mathematical theory and practical use cases.

A brief description of each chapter is given below.

1.  [Chapter 1](#ch1.xhtml) will introduce readers to transformers from the timeline, history, and its impact on the academic and industrial world. We will then lay out a complete roadmap based on the taxonomy and how each chapter renders from the theory, practice, and application perspective. The chapter then proceeds with a comprehensive discussion on practical aspects such as resources, tools, books, and courses that will be employed in other chapters.
    
2.  [Chapter 2](#ch2.xhtml) starts by introducing the sequence-to-sequence models and their limitations. The chapter then lays out various building blocks of transformers such as attention, multi-headed attention, positional encodings, residual connections, and encoder-decoder frameworks in a step-by-step manner. All these functional units get detailed treatment from a theoretical and practical perspectives for the readers to get a complete handle on the topic. Finally, a real-world case study using transformers for machine translation tasks showing the operative aspects concludes the chapter.
    
3.  The advent of BERT has revolutionized the field of natural language processing (NLP) and helped to get close to human-level performance in many conventionally challenging tasks. [Chapter 3](#ch3.xhtml) introduces the details of the BERT architecture and how it is pre-trained and fine-tuned for classical NLP tasks such as single/pair text classification, token tagging, and question answering. The chapter also discusses the field of BERTology, which is research related to the inner workings of BERT and how it processes and analyzes text and information. Finally, the chapter introduces some deep learning architectures that modify BERT for more efficiency (e.g., RoBERTa) and other types of NLP applications (e.g., NLP for tabular data—TaBERT). The chapter concludes with real-world case studies on using BERT for sentiment classification and topic modeling applications.
    
4.  Multilingual transfer learning is an area where transformer architectures have significantly impacted the field of machine learning. [Chapter 4](#ch4.xhtml) introduces an overview of transformer-based multilingual architectures and how cross-lingual transfer learning is pre-trained and fine-tuned for NLP tasks. The chapter also provides an overview of the state-of-the-art benchmarks used for multilingual NLP. The chapter further provides some insights into the research and techniques identifying the factors affecting cross-lingual and zero-shot transfer learning in NLP. Finally, a real-world case study of using multilingual universal sentence encoders for zero-shot cross-lingual sentiment classification is presented.
    
5.  In [Chapter 5](#ch5.xhtml) we discuss various modifications made to the standard transformer architecture to tackle longer sequences with limited memory, to build transformer models that are faster and of higher quality, and that perform better on text generation and summarization. We also discuss the key differences between the model architectures and approaches that are centered around key ideas such as knowledge distillation and making computations more efficient by reducing attention mechanism complexity. This chapter includes a case study that uses a pre-trained transformer model for sentiment classification, including a look at the contents of the model's multi-head attention mechanisms.
    
6.  Since BERT, many flavors of pre-trained models have been made available across different domains, providing models that can be fine-tuned to domain-specific data across science, medicine, and finance. In addition, language-specific pre-trained models offer increasingly competitive results on downstream language specific tasks. In [Chapter 6](#ch6.xhtml), we discuss the pre-trained models that are available, showing their benefits and applications to specific domains such as computer vision, speech, time series, and text. This chapter includes a case study that compares the performance of three transformer-based automatic speech recognition models.
    
7.  There is a need to understand the models from an explainability standpoint in many critical applications and given the black-box nature of transformers-based models. In [Chapter 7](#ch7.xhtml), we will cover the traits of the models that address explainability, related areas that impact explainability, the taxonomy of explainable methods applied to the transformer-based and attention-based systems, and finally, a detailed case study in the electronic health record systems using transformers with different explainable techniques to become more practical.
    

# Authors

**Uday Kamath** has spent more than two decades developing analytics products and combines this experience with learning in statistics, optimization, machine learning, bioinformatics, and evolutionary computing. He has contributed to many journals, conferences, and books, is the author of *XAI: An Introduction to Interpretable XAI, Deep Learning for NLP and Speech Recognition, Mastering Java Machine Learning, and Machine Learning: End-to-End Guide for Java Developers*. He held many senior roles: chief analytics officer for Digital Reasoning, advisor for Falkonry, and chief data scientist for BAE Systems Applied Intelligence. Dr. Kamath has many patents and has built commercial products using AI in domains such as compliance, cybersecurity, financial crime, and bioinformatics. He currently works as the chief analytics officer for Smarsh. He is responsible for data science, research of analytical products employing deep learning, transformers, explainable AI, and modern techniques in speech and text for the financial domain and healthcare.

**Kenneth L. Graham** has two decades experience solving quantitative problems in multiple domains, including Monte Carlo simulation, NLP, anomaly detection, cybersecurity, and behavioral profiling. For the past ten years, he has focused on building scalable solutions in NLP for government and industry, including entity coreference resolution, text classification, active learning, automatic speech recognition, and temporal normalization. He currently works at AppFolio as a senior machine learning engineer. Dr. Graham has five patents for his work in natural language processing, seven research publications, and a PhD in condensed matter physics.

**Wael Emara** has two decades of experience in academia and industry. He has a PhD in computer engineering and computer science with emphasis on machine learning and artificial intelligence. His technical background and research spans signal and image processing, computer vision, medical imaging, social media analytics, machine learning, and natural language processing. Dr. Emara has contributed to many peer-reviewed publications in various machine learning topics and he is active in the technical community in the greater New York area. He currently works as a principal data scientist at Smarsh, Inc. for Digital Reasoning where he is doing research on state-of-the-art artificial intelligence NLP systems.

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

DOI: [10.1201/9781003170082-1](https://doi.org/10.1201/9781003170082-1)

TRANSFORMERS are deep learning models that have achieved state-of-the-art performance in several fields such as natural language processing, computer vision, and speech recognition. Indeed, the massive surge of recently proposed transformer model variants has meant researchers and practitioners alike find it challenging to keep pace. In this chapter, we provide a brief history of diverse research directly or indirectly connected to the innovation of transformers. Next, we discuss a taxonomy based on changes in the architecture for efficiency in computation, memory, applications, etc., which can help navigate the complex innovation space. Finally, we provide resources in tools, libraries, books, and online courses that the readers can benefit from in their pursuit.

## 1.1 Deep Learning: A Historic Perspective

In the early 1940s, S. McCulloch and W. Pitts, using a simple electrical circuit called a “threshold logic unit”, simulated intelligent behavior by emulating how the brain works \[[179](#refbib.xhtml#refbib_179)\]. The simple model had the first neuron with inputs and outputs that would generate an output 0 when the “weighted sum” was below a threshold and 1 otherwise, which later became the basis of all the neural architectures. The weights were not learned but adjusted. In his book *The Organization of Behaviour* (1949), Donald Hebb laid the foundation of complex neural processing by proposing how neural pathways can have multiple neurons firing and strengthening over time \[[108](#refbib.xhtml#refbib_108)\]. Frank Rosenblatt, in his seminal work, extended the McCulloch–Pitts neuron, referring to it as the “Mark I Perceptron”; given the inputs, it generated outputs using linear thresholding logic \[[212](#refbib.xhtml#refbib_212)\].

The weights in the perceptron were “learned” by repeatedly passing the inputs and reducing the difference between the predicted output and the desired output, thus giving birth to the basic neural learning algorithm. Marvin Minsky and Seymour Papert later published the book *Perceptrons* which revealed the limitations of perceptrons in learning the simple exclusive-or function (XOR) and thus prompting the so-called The First AI Winter \[[186](#refbib.xhtml#refbib_186)\].

John Hopfield introduced “Hopfield Networks”, one of the first recurrent neural networks (RNNs) that serve as a content-addressable memory system \[[117](#refbib.xhtml#refbib_117)\].

In 1986, David Rumelhart, Geoff Hinton, and Ronald Williams published the seminal work “Learning representations by back-propagating errors” \[[217](#refbib.xhtml#refbib_217)\]. Their work confirms how a multi-layered neural network using many “hidden” layers can overcome the weakness of perceptrons in learning complex patterns with relatively simple training procedures. The building blocks for this work had been laid down by various research over the years by S. Linnainmaa, P. Werbos, K. Fukushima, D. Parker, and Y. LeCun \[[91](#refbib.xhtml#refbib_91), [149](#refbib.xhtml#refbib_149), [164](#refbib.xhtml#refbib_164), [196](#refbib.xhtml#refbib_196), [267](#refbib.xhtml#refbib_267)\].

LeCun et al., through their research and implementation, led to the first widespread application of neural networks to recognize the hand-written digits used by the U.S. Postal Service \[[150](#refbib.xhtml#refbib_150)\]. This work is a critical milestone in deep learning history, proving the utility of convolution operations and weight sharing in learning the features in computer vision.

Backpropagation, the key optimization technique, encountered a number of issues such as vanishing gradients, exploding gradients, and the inability to learn long-term information, to name a few \[[115](#refbib.xhtml#refbib_115)\]. Hochreiter and Schmidhuber, in their work,“Long short-term memory (LSTM)” architecture, demonstrated how issues with long-term dependencies could overcome shortcomings of backpropagation over time \[[116](#refbib.xhtml#refbib_116)\].

Hinton et al. published a breakthrough paper in 2006 titled “A fast learning algorithm for deep belief nets”; it was one of the reasons for the resurgence of deep learning \[[113](#refbib.xhtml#refbib_113)\]. The research highlighted the effectiveness of layer-by-layer training using unsupervised methods followed by supervised “fine-tuning” to achieve state-of-the-art results in character recognition. Bengio et al., in their seminal work following this, offered deep insights into why deep learning networks with multiple layers can hierarchically learn features as compared to shallow neural networks \[[27](#refbib.xhtml#refbib_27)\]. In their research, Bengio and LeCun emphasized the advantages of deep learning through architectures such as convolutional neural networks (CNNs), restricted Boltzmann machines (RBMs), and deep belief networks (DBNs), and through techniques such as unsupervised pre-training with fine-tuning, thus inspiring the next wave of deep learning \[[28](#refbib.xhtml#refbib_28)\]. Fei-Fei Li, head of the artificial intelligence lab at Stanford University, along with other researchers, launched ImageNet, which resulted in the most extensive collection of images and, for the first time, highlighted the usefulness of data in learning essential tasks such as object recognition, classification, and clustering \[[70](#refbib.xhtml#refbib_70)\]. Improvements in computer hardware, primarily through GPUs, increasing the throughput by almost 10× every five years, and the existence of a large amount of data to learn from resulted in a paradigm shift in the field. Instead of hand-engineered features that were the primary focus for many sophisticated applications, by learning from a large volume of training data, where the necessary features emerge, the deep learning network became the foundation for many state-of-the-art techniques.

Mikolov et al. and Graves proposed language models using RNNs and long short-term memory, which later became the building blocks for many natural language processing (NLP) architectures \[[97](#refbib.xhtml#refbib_97), [184](#refbib.xhtml#refbib_184)\]. The research paper by Collobert and Weston was instrumental in demonstrating many concepts such as pre-trained word embeddings, CNNs for text, and sharing of the embedding matrix for multi-task learning \[[60](#refbib.xhtml#refbib_60)\]. Mikolov et al. further improved the efficiency of training the word embeddings proposed by Bengio et al. by eliminating the hidden layer and formulating an approximate objective for learning giving rise to “word2vec”, an efficient large-scale implementation of word embeddings \[[183](#refbib.xhtml#refbib_183), [185](#refbib.xhtml#refbib_185)\]. Sutskever's research, which proposed a Hessian-free optimizer to train RNNs efficiently on long-term dependencies, was a breakthrough in reviving the usage of RNNs, especially in NLP \[[237](#refbib.xhtml#refbib_237)\]. Sutskever et al. introduced sequence-to-sequence learning as a generic neural framework comprised of an encoder neural network processing inputs as a sequence and a decoder neural network predicting the outputs based on the input sequence states and the current output states \[[238](#refbib.xhtml#refbib_238)\]. As a result, the sequence-to-sequence framework became the core architecture for a wide range of NLP tasks such as constituency parsing, named entity recognition (NER), machine translation, question-answering, and summarization, to name a few. Furthermore, even Google started replacing its monolithic phrase-based machine translation models with sequence-to-sequence neural machine translation models \[[272](#refbib.xhtml#refbib_272)\]. To overcome the bottleneck issues with the sequence-to-sequence framework, seminal work by Bahdanau et al. proposed the attention mechanism, which plays a crucial role in transformers and their variants \[[17](#refbib.xhtml#refbib_17)\].

## 1.2 Transformers and Taxonomy

The transformer architecture \[[254](#refbib.xhtml#refbib_254)\] was introduced in 2017, in the paper *Attention Is All You Need*, for sequence-to-sequence problems. It was an alternative to using recurrent or convolutional layers. Since its introduction, there's been a wide variety of research into various ways to improve upon the standard transformer. Two surveys \[[163](#refbib.xhtml#refbib_163), [243](#refbib.xhtml#refbib_243)\] have categorized transformer-related papers. Transformer research has focused on three things: architecture modification, pre-training methods, and applications. In this book, we'll spend time on a subset of architecture modifications, pre-training methods of large language models, like BERT \[[71](#refbib.xhtml#refbib_71)\], and a few applications.

### 1.2.1 Modified Transformer Architecture

Modified transformer architectures can be split into two broad categories \[[163](#refbib.xhtml#refbib_163)\]: changes to the internal arrangement of the transformer block and changes to the layers that a transformer block is made of. A summary of the types of transformer modifications are shown in [Table 1.1](#ch1.xhtml#tbl1_1)

[TABLE 1.1](#ch1.xhtml#b1tbl1_1) Types of modifications to the transformer block

  
| Modification || Transformer |
| --- | --- |
| Lightweight transformers ||  |
| --- | --- |
|  || Lite Transformer \[[274](#refbib.xhtml#refbib_274)\]Funnel Transformer \[[66](#refbib.xhtml#refbib_66)\]DeLighT \[[180](#refbib.xhtml#refbib_180)\] |
| Cross-block connectivity ||  |
|  || Realformer \[[107](#refbib.xhtml#refbib_107)\]Transparent Attention \[[19](#refbib.xhtml#refbib_19)\] |
| Adaptive computation time ||  |
|  || Universal Transformer \[[69](#refbib.xhtml#refbib_69)\]Conditional Computation Transformer \[[18](#refbib.xhtml#refbib_18)\]DeeBERT \[[276](#refbib.xhtml#refbib_276)\] |
| Recurrent ||  |
|  || Transformer-XL \[[67](#refbib.xhtml#refbib_67)\]Compressive Transformer \[[204](#refbib.xhtml#refbib_204)\]Memformer \[[287](#refbib.xhtml#refbib_287)\] |
| Hierarchical ||  |
|  || HIBERT \[[296](#refbib.xhtml#refbib_296)\]Hi-Transformer \[[270](#refbib.xhtml#refbib_270)\] |
| Different architectures ||  |
|  || Macaron Transformer \[[174](#refbib.xhtml#refbib_174)\]Sandwich Transformer \[[201](#refbib.xhtml#refbib_201)\]Differentiable Architecture Search \[[299](#refbib.xhtml#refbib_299)\] |

#### 1.2.1.1 Transformer block changes

Thus far, modifications to the transformer block have fallen into five categories \[[163](#refbib.xhtml#refbib_163)\]:

*   Decreasing memory footprint and compute
    
*   Adding connections between transformer blocks
    
*   Adaptive computation time (e.g., allow early stopping during training)
    
*   Recurrence or hierarchical structure
    
*   Changing the architecture more drastically (e.g., neural architecture search)
    

In this book, we'll focus on several architecture modifications that allow a transformer to process longer sequences and/or lower the computational complexity of the attention mechanism. We show a partial list of modified transformers in [Table 1.1](#ch1.xhtml#tbl1_1).

#### 1.2.1.2 Transformer sublayer changes

In [Chapter 2](#ch2.xhtml), we'll take a detailed look at the structure of a transformer block, covering its four components so we can later discuss ways in which researchers have modified them. In general, there are four parts to a transformer block \[[254](#refbib.xhtml#refbib_254)\]: positional encodings, multi-head attention, residual connections with layer normalization \[[13](#refbib.xhtml#refbib_13)\], and a position-wise feedforward network. Changes to transformer sublayers have focused on these four types of components, most of which has focused on changing aspects of the multi-head attention \[[163](#refbib.xhtml#refbib_163), [243](#refbib.xhtml#refbib_243)\]. [Table 1.2](#ch1.xhtml#tbl1_2) shows a selected list of transformer variants that have modified multi-head attention mechanisms.

[TABLE 1.2](#ch1.xhtml#b1tbl1_2) Types of modifications to the multi-head attention module

  
| Modification || Transformer |
| --- | --- |
| Low-rank ||  |
| --- | --- |
|  || Performer \[[53](#refbib.xhtml#refbib_53)\]Nystromformer \[[277](#refbib.xhtml#refbib_277)\]Synthesizer \[[241](#refbib.xhtml#refbib_241)\] |
| Attention with prior ||  |
|  || Gaussian Transformer \[[102](#refbib.xhtml#refbib_102)\]Realformer \[[107](#refbib.xhtml#refbib_107)\]Synthesizer \[[241](#refbib.xhtml#refbib_241)\]Longformer \[[25](#refbib.xhtml#refbib_25)\] |
| Improved multi-head attention ||  |
|  || Talking-heads Attention \[[227](#refbib.xhtml#refbib_227)\]Multi-Scale Transformer \[[234](#refbib.xhtml#refbib_234)\] |
| Complexity reduction ||  |
|  || Longformer \[[25](#refbib.xhtml#refbib_25)\]Reformer \[[142](#refbib.xhtml#refbib_142)\]Big Bird \[[292](#refbib.xhtml#refbib_292)\]Performer \[[53](#refbib.xhtml#refbib_53)\]Routing Transformer \[[214](#refbib.xhtml#refbib_214)\] |
| Prototype queries ||  |
|  || Clustered Attention \[[256](#refbib.xhtml#refbib_256)\]Informer \[[302](#refbib.xhtml#refbib_302)\] |
| Clustered key-value memory ||  |
|  || Set Transformer \[[151](#refbib.xhtml#refbib_151)\]Memory Compressed Transformer \[[167](#refbib.xhtml#refbib_167)\]Linformer \[[259](#refbib.xhtml#refbib_259)\] |

**Multi-head attention** Much effort has been directed at the multi-head attention mechanism; studying its quadratic computational complexity, ways to address said complexity, and how it might be changed for specific kinds of problems. Most of this work falls into two broad categories: reducing the computational complexity of the attention mechanism, or changing the attention mechanism so it can learn more things.

As discussed in refs \[[163](#refbib.xhtml#refbib_163), [243](#refbib.xhtml#refbib_243)\], there are many ways to address the complexity of the attention mechanism. There are low-rank approximations, like Linformer \[[259](#refbib.xhtml#refbib_259)\] and Performer \[[53](#refbib.xhtml#refbib_53)\]. There are several ways to sparsify the attention mechanism, some of which effectively reduce the complexity of the attention mechanism to be linear in the sequence length. For example Longformer \[[25](#refbib.xhtml#refbib_25)\] and BigBird \[[292](#refbib.xhtml#refbib_292)\] add sparsity by fixing the positions to which a given token can attend. Some other transformers, like Reformer \[[142](#refbib.xhtml#refbib_142)\], introduce a learnable sparsity by sorting or clustering the input tokens. There are others still which reduce the size of the attention matrix \[[163](#refbib.xhtml#refbib_163)\].

There is also a variety of work that has tried to improve the multi-head attention mechanism \[[163](#refbib.xhtml#refbib_163)\]. For instance, attention heads have been allowed to “communicate” with each other and/or share information \[[65](#refbib.xhtml#refbib_65), [158](#refbib.xhtml#refbib_158), [226](#refbib.xhtml#refbib_226), 227\], learn the optimal span to attend over \[[235](#refbib.xhtml#refbib_235)\], and use different attention spans in different attention heads \[[103](#refbib.xhtml#refbib_103)\]. This list is not exhaustive. We discuss several such methods in [Chapter 5](#ch5.xhtml).

**Positional encodings** Positional encodings \[[254](#refbib.xhtml#refbib_254)\] are a way of encoding sequence order into the transformer. They also comprise another avenue for modifying the components of a transformer block. Thus far, four kinds of positional encodings have been used \[[163](#refbib.xhtml#refbib_163)\]: absolute positional encodings (like those of the standard transformer), relative positional encodings (such as in Transformer-XL), hybrid encodings that have absolute and relative position information, and implicit encodings that provide information about sequence order in other ways. This is shown in [Table 1.3](#ch1.xhtml#tbl1_3). We discuss the absolute positional encodings used in the standard transformer in [Chapter 2](#ch2.xhtml) and the relative encodings used in Transformer-XL in [Chapter 5](#ch5.xhtml).

[TABLE 1.3](#ch1.xhtml#b1tbl1_3) Changes to positional encodings

  
| Modification || Transformer |
| --- | --- |
| Absolute positionRelative positionAbsolute/relative hybridOther representations || Original Transformer \[[254](#refbib.xhtml#refbib_254)\]Transformer-XL \[[67](#refbib.xhtml#refbib_67)\]Roformer \[[232](#refbib.xhtml#refbib_232)\]R-Transformer \[[262](#refbib.xhtml#refbib_262)\] |
| --- | --- |

**Residual connections and position-wise feedforward networks** Some work has included changes to the residual blocks that come after the multi-head attention mechanism and after the position-wise feedforward network, including the position of the layer normalization, swapping layer normalization with something else, removal of layer normalization entirely \[[163](#refbib.xhtml#refbib_163)\], or the introduction or reversible residual layers to conserve memory (used in Reformer) \[[142](#refbib.xhtml#refbib_142)\]. Reformer will be discussed in [Chapter 5](#ch5.xhtml). Other work has studied ways to change the position-wise feedforward network, including changing the activation function, increasing its representational capacity, or removing the feedforward network.

### 1.2.2 Pre-training Methods and Applications

A large body of work has focused on how a transformer can be pre-trained. There are encoder-only models, such as BERT \[[71](#refbib.xhtml#refbib_71)\], decoder-only models like the famed generative pre-trained transformer models GPT-3 \[[32](#refbib.xhtml#refbib_32)\], and encoder-decoder models like T5 \[[205](#refbib.xhtml#refbib_205)\] and ByT5 \[[280](#refbib.xhtml#refbib_280)\]. BERT is discussed in detail in [Chapter 3](#ch3.xhtml), T5 in [Chapter 5](#ch5.xhtml), and ByT5 in [Chapter 6](#ch6.xhtml).

There have been many application and domain-specific transformers made for specific data domains (e.g., financial or medical text) and specific kinds of data (e.g., images or video). We discuss several such applications in [Chapter 6](#ch6.xhtml).

## 1.3 Resources

In this section, we will discuss some resources that can be useful for researchers and practitioners.

### 1.3.1 Libraries and Implementations

Here are some useful libraries, tools, and implementations ([Table 1.4](#ch1.xhtml#tbl1_4)):

[TABLE 1.4](#ch1.xhtml#b1tbl1_4) Libraries and Tools

  
| Organization || Language and Framework || API || Pre-trained |
| --- | --- | --- | --- |
| AllenNLP || Python and PyTorch || Yes || Yes |
| --- | --- | --- | --- |
| HuggingFace || Jax, PyTorch, and TensorFlow || Yes || Yes |
| Google Brain || TensorFlow || Yes ||  |
| GluonNLP || MXNet || Yes || Yes |

### 1.3.2 Books

Some of the books that we found useful are:

*   Transfer Learning for Natural Language Processing by Paul Azunre \[[12](#refbib.xhtml#refbib_12)\]
    
*   Transformers for Natural Language Processing by Denis Rothman \[[213](#refbib.xhtml#refbib_213)\]
    
*   Deep Learning Algorithms: Transformers, gans, encoders, rnns, cnns, and more by Ricardo A. Calix \[[35](#refbib.xhtml#refbib_35)\]
    
*   Python Transformers By Huggingface Hands On by Joshua K. Cage \[[33](#refbib.xhtml#refbib_33)\]
    
*   Deep Learning for NLP and Speech Recognition by Uday Kamath, John Liu, and James Whitaker \[[248](#refbib.xhtml#refbib_248)\]
    

### 1.3.3 Courses, Tutorials, and Lectures

Some of the very relevant online courses and tutorials:

*   The Annotated Transformer by Alexander Rush et al. [http://nlp.seas.harvard.edu/​2018/​04/​03/​attention.html](http://nlp.seas.harvard.edu)
    
*   HuggingFace course on transformers [https://huggingface.co/​course](https://huggingface.co)
    
*   DeepLearning.AI course on sequence models [https://www.coursera.org/​learn/​nlp-sequence-models](https://www.coursera.org)
    
*   DeepLearning.AI course on transformers and BERT [https://www.coursera.org/​learn/​attention-models-in-nlp](https://www.coursera.org)
    
*   Stanford CS224N: NLP with Deep Learning by Christopher Manning [http://web.stanford.edu/​class/​cs224n/​](http://web.stanford.edu)
    
*   UC Berkeley's Applied Natural Language Processing by David Bamman [https://people.ischool.berkeley.edu/​~dbamman/​info256.html](https://people.ischool.berkeley.edu)
    
*   Advanced NLP with spaCy by Ines Montani [https://course.spacy.io/​en/​](https://course.spacy.io)
    
*   Deep Learning for Coders with fastai and PyTorch by Sylvain Gugger and Jeremy Howard [https://course.fast.ai/​](https://course.fast.ai)
    
*   Jay Alammar's visual explanation of transformers and related architectures [https://jalammar.github.io/​](https://jalammar.github.io)
    

### 1.3.4 Case Studies and Details

At the end of [Chapters 2](#ch2.xhtml)–[7](#ch7.xhtml), we include a case study that allows the reader to see how one or more of the models and methods discussed in the chapter can be applied, or how they stack up against one another when applied to the same problem. The aim is for the case study to provide a small starting point in working with transformer models from which one can branch out further. Each case study has been chosen to run within approximately one hour on GPUs at least as powerful as the NVIDIA K80 (Google Colaboratory provides these for free). Case studies are also available in the Github repository which accompanies this book: [https://github.com/​CRCTransformers/​deepdive-book](https://github.com).

# CHAPTER 2Transformers: Basics and Introduction

DOI: [10.1201/9781003170082-2](https://doi.org/10.1201/9781003170082-2)

MANY natural language processing and speech recognition techniques need the ability to handle large sequences as inputs and transform them to specific outputs. Traditional approaches, such as recurrent neural networks (RNN) have several shortcomings that prohibit real-world solutions. Transformers have become the fundamental design piece overcoming most of these limitations, and they have state-of-the-art results. This chapter starts by introducing the sequence-to-sequence models and their limitations. The chapter then lays out various building blocks of transformers such as attention, multi-head attention, positional encodings, residual connections, and encoder-decoder frameworks in a step-by-step manner. All these functional units get detailed treatment from a theoretical and practical perspective for the reader to get a complete handle on the topic. Finally, a real-world case study concludes the chapter by showing the operative aspects, using well-known libraries and datasets.

## 2.1 Encoder-Decoder Architecture

Many NLP problems, such as machine translation, question answering, and text summarization, to name a few, use pairs of sequences as inputs to train the model. Generally, the sequences are of variable lengths. The use of an encoder-decoder architecture, as shown in [Fig. 2.1](#ch2.xhtml#fig2_1) is a common practice to solve the problem. The encoder component takes a variable-length sequence and converts it into a fixed-length output-state. The decoder component takes a fixed-length state and converts it back into a variable-length output.

![Figure 2.1 Encoder-Decoder architecture.](images/fig2_1.jpg)

[Figure 2.1](#ch2.xhtml#b2fig2_1) Encoder-Decoder architecture.

## 2.2 Sequence-To-Sequence

Machine translation and many other NLP problems produced promising results using sequence-to-sequence architecture (abbreviated as seq2seq) with a recurrent neural network (e.g., RNN) based encoder and decoder \[[51](#refbib.xhtml#refbib_51), [238](#refbib.xhtml#refbib_238)\]. [Fig. 2.2](#ch2.xhtml#fig2_2) shows an example of machine translation where a French sentence, *J'aime le thé.*, and it's English equivalent, *I love tea.* form the sentence pair as an example of input for the training. The tokens <eos> and <bos> are special ways to handle the end and beginning of the sentence, respectively. As shown in Fig. 2.2 the final hidden state of the encoder acts as the input for the decoder.

![Figure 2.2 RNN-based sequence-to-sequence for machine translation.](images/fig2_2.jpg)

[Figure 2.2](#ch2.xhtml#b2fig2_2) RNN-based sequence-to-sequence for machine translation.

### 2.2.1 Encoder

The input sentence is tokenized into words and words are mapped into feature vectors which are the inputs for the encoder. Suppose that the input sequence is represented by *x*[1], ⋯, *x*[*T*] such that token *x*[*t*] in the input text sequence is the *t*th token. Embedding mappings transform the input tokens *x*[1], …, *x*[*T*] to **x**[1], ⋯, **x**[*T*] vectors. A unidirectional RNN at any time *t* with a previous hidden state **h**[*t* − 1] and input x[*t*] generates a new hidden state

  
$$\\begin{array}{l} {\\mathbf{h}\_{t} = f(\\mathbf{h}\_{t - 1},\\mathbf{x}\_{t})} \\\\ \\end{array}$$  
(2.1)

The above equation can be more concretely written as

  
$$\\begin{array}{l} {\\mathbf{h}\_{t} = \\tanh(\\mathbf{W}^{(hh)}\\mathbf{h}\_{t - 1} + \\mathbf{W}^{(hx)}\\mathbf{x}\_{t})} \\\\ \\end{array}$$  
(2.2)

The state **h**[*t*], known as the **context variable** or the **context vector**, encodes the information of the entire input sequence and is given by:

  
$$\\begin{array}{l} {\\mathbf{c} = m(\\mathbf{h}\_{1},\\cdots,\\mathbf{h}\_{T})} \\\\ \\end{array}$$  
(2.3)

where *m* is the mapping function and in the simplest case maps the context variable to the last hidden state

  
$$\\begin{array}{l} {\\mathbf{c} = m(\\mathbf{h}\_{1},\\cdots,\\mathbf{h}\_{T}) = \\mathbf{h}\_{T}} \\\\ \\end{array}$$  
(2.4)

Adding more complexity to the architecture, the RNN can be bidirectional and thus the hidden state would not only depend on the previous hidden state **h**[*t* − 1] and input **x**[*t*], but also on the next state **h**[*t* + 1].

### 2.2.2 Decoder

The decoder has the output of the encoder, the context variable **c**, and the given output sequence *y*[1], …, *y*[*T*]^′ to generate the decoded outputs. In Sutskever et al., the context variable from the encoder—the final hidden state—initiates the decoder, whereas in Cho et al. the context variable is passed to every time step.

Similar to the encoder, decoder hidden state at any time *t*^′ is given by

  
$$\\begin{array}{l} {\\mathbf{s}\_{t^{\\prime}} = g(\\mathbf{s}\_{t - 1},\\mathbf{y}\_{t^{\\prime} - 1},\\mathbf{c})} \\\\ \\end{array}$$  
(2.5)

The hidden state of the decoder flows to an output layer and the conditional distribution of the next token at *t*^′ is given by

  
$$\\begin{array}{l} {P(\\mathbf{y}\_{t^{\\prime}}|\\mathbf{y}\_{t^{\\prime} - 1},\\cdots,y\_{1},\\mathbf{c}) = \\text{softmax}(\\mathbf{s}\_{t - 1},\\mathbf{y}\_{t^{\\prime} - 1},\\mathbf{c})} \\\\ \\end{array}$$  
(2.6)

### 2.2.3 Training

The decoder predicts a probability distribution for the output tokens at each time step, and the softmax gives the distribution over the words. Thus, the encoder and decoder are jointly trained, and the cross-entropy loss is used for optimization and is given by

  
$$\\begin{array}{l} {\\max\\limits\_{\\theta}\\frac{1}{N}\\sum\\limits\_{n = 1}^{N}\\log p\_{\\theta}(\\mathbf{y}^{(n)}|\\mathbf{x}^{(n)})} \\\\ \\end{array}$$  
(2.7)

The process of concatenating the < bos > and the original output sequence, excluding the final token, as the input to the decoder during the training is called **teacher forcing**. The teacher forcing helps in addressing the slow convergence and instability problems when training RNNs.

### 2.2.4 Issues with RNN-Based Encoder-Decoder

As described in the above section, complete information about the source sentence is compressed and encoded in one context variable used by the decoder component. As the input size increases, there will be a loss of information while compressing the input. The words in a sentence can also have complex structure and long-distance associations based on the language. Capturing this in a compressed way in a single vector also leads to inefficiencies. On the other hand, each time step's hidden variables on the encoder side are available and carry information to be used by the decoder network. Each time step in the decoder can be influenced differently by the hidden variables in the encoder. RNNs also have issues with vanishing and explosive gradients \[[115](#refbib.xhtml#refbib_115)\]. One of the computational issues with RNNs is that the recurrence or dependence on previous time steps makes the architecture very difficult to parallelize.

## 2.3 Attention Mechanism

### 2.3.1 Background

The attention mechanism involves selectively focusing on specific elements while filtering out the less relevant ones. The human optic nerve receives information in the order of billion bits per second, while the brain's capacity to process is far less. Visual attention, a form of attention, involves orienting to and sustaining focus on a stimulus such as a person or inanimate object or a specific task, thus enabling the brain's efficient processing. Therefore, the attention mechanism has allowed humans to focus on only a fraction of information of interest, thus enabling optimum resource usage, leading to better survival and growth.

The “father of American psychology”, William James, created a two-component framework to explain the visual attention mechanism \[[133](#refbib.xhtml#refbib_133)\]. In this framework, the spotlight of attention uses both *nonvolitional* (involuntary) and *volitional* (voluntary) cues to bias the sensory input. The *nonvolitional* cue is involuntary and is based on the saliency and noticeability of targets in the environment. In contrast, the *volitional* cue is based on the subject's voluntary effort to focus on the target deliberately. For example, drawing attention to specific objects by coloring them differently or attending to a crying baby are nonvolitional cues. In contrast, attending to specific text for answering question or solving specific problems are volitional cues.

In the context of attention mechanisms in deep learning, volitional cues map to queries, keys to nonvolitional cues, and sensory inputs to value. Every sensory input (value) maps to the nonvolitional cue (key) of that sensory input. Attention mechanisms can be thus considered as a process of biasing selection over values (sensory inputs) via attention pooling, using the queries (volitional cues) and keys (nonvolitional cues) as shown in [Fig. 2.3](#ch2.xhtml#fig2_3).

![Figure 2.3 Attention mechanism showing query, keys, values, and output vector interactions.](images/fig2_3.jpg)

[Figure 2.3](#ch2.xhtml#b2fig2_3) Attention mechanism showing query, keys, values, and output vector interactions.

The attention mechanism is designed in a way to overcome the issues described with RNN-based encoder-decoder architecture.

As shown in [Fig. 2.3](#ch2.xhtml#fig2_3), an **attention** mechanism can be considered as a memory with keys and values and a layer which, when someone queries it, generates an output from value whose keys map the input \[[17](#refbib.xhtml#refbib_17)\].

To formalize, let us consider the memory unit consisting of *n* key-value pairs (**k**[1], **v**[1]), …, (**k**[*n*], **v**[*n*]) with **k**[*i*] ∈ ℝ^(*d*[*k*]) and **v**[*i*] ∈ ℝ^(*d*[*v*]). The attention layer receives an input as query **q** ∈ ℝ^(*d*[*q*]) and returns an output **o** ∈ ℝ^(*d*[*v*]) with same shape as the value **v**.

The attention layer measures the similarity between the query and the key using a score function *α* which returns scores *a*[1], …, *a*[*n*] for keys **k**[1], …, **k**[*n*] given by

  
$$\\begin{array}{l} {a\_{i} = \\alpha(\\mathbf{q},\\mathbf{k}\_{i})} \\\\ \\end{array}$$  
(2.8)

Attention weights are computed as a softmax function on the scores

  
$$\\begin{array}{l} {\\mathbf{b} = \\text{softmax}(\\mathbf{a})} \\\\ \\end{array}$$  
(2.9)

Each element of **b** is

  
$$\\begin{array}{l} {b\_{i} = \\frac{\\exp(a\_{i})}{\\sum\_{j}{\\exp(a\_{j})}}} \\\\ \\end{array}$$  
(2.10)

The output is the weighted sum of the attention weights and the values

  
$$\\begin{array}{l} {\\mathbf{o} = {\\sum\\limits\_{i = 1}^{n}b\_{i}}\\mathbf{v}\_{i}} \\\\ \\end{array}$$  
(2.11)

[Fig. 2.4](#ch2.xhtml#fig2_4) captures the interactions between various vectors and scalars from input query to output.

![Figure 2.4 Attention mechanism showing query, keys, values, and output vector interactions.](images/fig2_4.jpg)

[Figure 2.4](#ch2.xhtml#b2fig2_4) Attention mechanism showing query, keys, values, and output vector interactions.

### 2.3.2 Types of Score-based Attention

As discussed, the score function, *α*(**q**, **k**), can take various forms, which has given rise to a number of attention mechanisms, each having its advantage.

#### 2.3.2.1 Dot product (multiplicative)

The dot product-based scoring function is the simplest one and has no parameters to tune \[[176](#refbib.xhtml#refbib_176)\].

  
$$\\begin{array}{l} {\\alpha(\\mathbf{q},\\mathbf{k}) = \\mathbf{q} \\cdot \\mathbf{k}} \\\\ \\end{array}$$  
(2.12)

#### 2.3.2.2 Scaled dot product or Multiplicative

The scaled dot product-based scoring function divides the dot product by $\\sqrt{d\_{k}}$ to remove the influence of dimension *d*[*k*]\[[254](#refbib.xhtml#refbib_254)\]. According to Vaswani et al., as the dimension increases, the dot products grow larger, which pushes the softmax function into regions with extreme gradients.

  
$$\\begin{array}{l} {\\alpha(\\mathbf{q},\\mathbf{k}) = \\frac{\\mathbf{q} \\cdot \\mathbf{k}}{\\sqrt{d\_{k}}}} \\\\ \\end{array}$$  
(2.13)

#### 2.3.2.3 Linear, MLP, or Additive

Luong et al. also experimented by projecting the query and keys to a hidden layer of dimension *h*, learning the weights (**W**[*k*], **W**[*q*]) , and using a sigmoid function to combine them with the values, as given by

  
$$\\begin{array}{l} {\\alpha(\\mathbf{q},\\mathbf{k}) = \\mathbf{v}^{\\text{T}}\\tanh(\\mathbf{W}\_{k}\\mathbf{k} + \\mathbf{W}\_{q}\\mathbf{q})} \\\\ \\end{array}$$  
(2.14)

Scaled dot product, or dot product-based scoring, are faster and more memory efficient than additive attention mechanisms.

### 2.3.3 Attention-Based Sequence-to-Sequence

The general changes to an encoder-decoder with the addition of an attention layer and the mapping to query, keys, and values are shown in [Fig. 2.5](#ch2.xhtml#fig2_5) and are

1.  The output of the last encoder states are used as keys **k** and values **v**
    
2.  The output of the last decoder state, at time *t* − 1 is used as query **q**
    
3.  The output from the attention layer **o**, the context variable, is used for the next decoder state *t*
    

![Figure 2.5 Encoder-decoder with attention layer.](images/fig2_5.jpg)

[Figure 2.5](#ch2.xhtml#b2fig2_5) Encoder-decoder with attention layer.

To understand the flow in more details, let us consider the French translation example where the keys and values are the encoder states for the tokens {*J*^′*a**i**m**e*, *l**e*, *t**h**é*, .} and the decoder at time *t* − 1 has generated the tokens *I*,*love*. As shown in [Fig. 2.6](#ch2.xhtml#fig2_6), the decoder output at time *t* − 1, *love*, flows into attention layer as a query, which combines with the keys and generates the unnormalized scores **a** = *α*(**q**, **k**), which then get normalized to give the attention weights **b**. These attention weights further combine with the values (encoder outputs) to give the context variable or the output vector **o**. The output then combines with the previous decoder state to generate the next token *tea* at time *t*.

![Figure 2.6 Sequence-to-sequence, at a given time t, when the decoder has generated love at t - 1 and the token tea will be generated as the output.](images/fig2_6.jpg)

[Figure 2.6](#ch2.xhtml#b2fig2_6) Sequence-to-sequence, at a given time *t*, when the decoder has generated *love* at *t* − 1 and the token *tea* will be generated as the output.

## 2.4 Transformer

As shown in [Fig. 2.7](#ch2.xhtml#fig2_7), the primary transformer structure proposed by Vaswani et al. is based on the encoder-decoder architecture described before. The transformer combines the advantages of convolutional neural networks (CNN) to parallelize the computations and recurrent neural networks (RNN) to capture long-range, variable-length sequential information. There are many systemic changes proposed in the transformer architecture, and in the next few subsections, we will go through each of them in sufficient detail.

![Figure 2.7 Transformer architecture.](images/fig2_7.jpg)

[Figure 2.7](#ch2.xhtml#b2fig2_7) Transformer architecture.

### 2.4.1 Source and Target Representation

Both source and target words are tokenized and the tokens go through word embedding and positional encoding to give position encoded representation for all sentences.

#### 2.4.1.1 Word embedding

Standard word embedding lookup for tokens in a sentence can convert a sentence of length *l*, to a matrix **W** of dimension (*l*, *d*), i.e., **W** ∈ ℝ^(*l* × *d*).

#### 2.4.1.2 Positional encoding

Word order and positions play a crucial role in most of the NLP tasks. By taking one word at a time, recurrent neural networks essentially incorporate word order. In transformer architecture, to gain speed and parallelism, recurrent neural networks are replaced by multi-head attention layers, which we will cover later in detail. Thus it becomes necessary to explicitly pass the information about the word order to the model layer as one way of capturing it. This encoding of word order information is known as positional encoding. One can derive various requirements for effective positional encodings. They are

1.  Unique encoding value for each time-step (word in the sentence).
    
2.  Consistent distance between two time-steps across sentences of various lengths.
    
3.  Encoding results are generalized independent of the length of the sentence.
    
4.  The encoding is deterministic.
    

One trivial way of accomplishing all the requirements for positional encoding is to use binary representation. [Fig. 2.8](#ch2.xhtml#fig2_8) highlights how with a vector of size or depth 3, we can generate 8 positional encodings using binary values that meet all the requirements given above. The representation of each bit as grey (0) and white (1) shows how each position is different and has a constant difference. Using binary values is very costly from a memory perspective.

![Figure 2.8 Positional encoding for 8 positions with dimensionality 3.](images/fig2_8.jpg)

[Figure 2.8](#ch2.xhtml#b2fig2_8) Positional encoding for 8 positions with dimensionality 3.

If the length of the sentence is given by *l* and the embedding dimension/depth is given by *d*, positional encoding **P** is a 2-d matrix of same dimension, i.e., **P** ∈ ℝ^(*l* × *d*). Every position can be represented with equation in terms of *i* which is along the *l* and *j* which is along the *d* dimension as

  
$$\\begin{array}{l} {\\mathbf{P}\_{i,2j} = \\sin(i/1000^{2j/d})} \\\\ \\end{array}$$  
(2.15)

  
$$\\begin{array}{l} {\\mathbf{P}\_{i,2j + 1} = \\cos(i/1000^{2j/d})} \\\\ \\end{array}$$  
(2.16)

*f**o**r**i* = 0, ⋯, *l* − 1, *j* = 0, ⋯, ⌊(*d* − 1)/2⌋. The function definition above indicates that the frequencies are decreasing along the vector dimension and forms a geometric progression from 2*π* to 10000 ⋅ 2*π* on the wavelengths. For *d* = 512 dimensions for maximum positional length *l* = 50, the positional encoding visualization is shown in [Fig. 2.9](#ch2.xhtml#fig2_9).

![Figure 2.9 Positional encoding for 50 positions with dimensionality 512.](images/fig2_9.jpg)

[Figure 2.9](#ch2.xhtml#b2fig2_9) Positional encoding for 50 positions with dimensionality 512.

As shown in [Fig. 2.7](#ch2.xhtml#fig2_7), the two matrices, i.e., the word embeddings **W** and the positional encoding **P** are added to generate the input representation **X** = **W** + **P** ∈ ℝ^(*l* × *d*).

### 2.4.2 Attention Layers

The basic building block in transformers, in both encoders and decoders, is the self-attention. It has small variations based on how and where it is used in the encoder and the decoder side. In the next subsections we gradually build the attention layers starting from the self-attention.

#### 2.4.2.1 Self-attention

To understand multi-head attention, it is imperative to break-down the computations and understand the single head portion of it known as self-attention. [Fig. 2.10](#ch2.xhtml#fig2_10) shows how the input vectors, **x**[*i*], are converted to the output vectors, **z**[*i*], through the self-attention layer. Each input vector, **x**[*i*], generates three different vectors: the query, key, and value, (**q**[*i*], **k**[*i*], **v**[*i*],) . The query, key, and value vectors are obtained by projecting the input vector, **x**[*i*], at time *i* on the learnable weight matrices **W**[*q*], **W**[*k*], and **W**[*v*] to get **q**[*i*], **k**[*i*], and **v**[*i*], respectively. These query/key/value weight matrices are randomly initialized and the weights are jointly learned from the training process. For the first attention layer of the encoder and decoder, the inputs are the summation of the word embeddings and positional encodings.

![Figure 2.10 Self-attention inputs mapped to query, keys, and values and generated output for each input.](images/fig2_10.jpg)

[Figure 2.10](#ch2.xhtml#b2fig2_10) Self-attention inputs mapped to query, keys, and values and generated output for each input.

Similar to the attention discussion in [section 2.3](#ch2.xhtml#sec2_3) where we discussed the query, key, and values, and how they impact the final attention scores, the self-attention has all three vectors generated for every input and the following are their key roles:

1.  The role of the query vector of token *i*, **q**[*i*], is to combine with every other key vectors $\\sum\_{j = 0}^{l}{\\mathbf{q}\_{i}\\mathbf{k}\_{j}\\ ^{T}}$ to influence the weights for its own output, **z**[*i*].
    
2.  The role of the key vector of token *i*, **k**[*i*], is to be matched with every other query vectors to get similarity with query and to influence the output through query-key product scoring.
    
3.  The role of the value vector of token *i*, **v**[*i*], is extracting information by combining with the output of the query-key scores to get the output vector **z**[*i*].
    

The logical flow of all the computations carried out for each token *i* from input to output is demonstrated in [Fig. 2.11](#ch2.xhtml#fig2_11).

![Figure 2.11 The dotted lines show the complete flow of computation for one input through a self-attention layer.](images/fig2_11.jpg)

[Figure 2.11](#ch2.xhtml#b2fig2_11) The dotted lines show the complete flow of computation for one input through a self-attention layer.

Instead of a vector computation for each token *i*, input matrix **X** ∈ ℝ^(*l* × *d*) where *l* is the maximum length of the sentence and *d* is the dimension of the inputs, combines with each of the query, key, and value matrices as a single computation given by

  
$$\\begin{array}{l} {attention(\\mathbf{Q},\\mathbf{K},\\mathbf{V}) = \\text{softmax}(\\frac{\\mathbf{Q}\\mathbf{K}^{\\text{T}}}{\\sqrt{\\text{d}\_{\\text{k}}}})\\mathbf{V}} \\\\ \\end{array}$$  
(2.17)

#### 2.4.2.2 Multi-head Attention

Instead of a single self-attention head, there can be *h* parallel self-attention heads; this is known as multi-head attention. In the original transformer paper, the authors used *h* = 8 heads. Multi-head attention provides different subspace representations instead of just a single representation for the inputs, which helps capture different aspects of the same inputs. It also helps the model expand the focus to different positions. Each head can learn something different, for example, in machine translation, it may be about learning grammar, tense, conjugation, etc.

Multi-head attention have multiple sets of query/key/value weight matrices, each resulting in different query/key/value matrices for the inputs, finally generating output matrices **z**[*i*]. These output matrices from each head are concatenated and multiplied with an additional weight matrix, **W**[*O*], to get a single final matrix, **Z**, with vectors **z**[*i*] as output for each input **x**[*i*]. The parallel input to output transformations for all the heads is depicted in [Fig. 2.12](#ch2.xhtml#fig2_12).

![Figure 2.12 Multi-head attention.](images/fig2_12.jpg)

[Figure 2.12](#ch2.xhtml#b2fig2_12) Multi-head attention.

  
$$\\begin{array}{l} {head\_{i} = attention(\\mathbf{W}\_{q}\\ ^{i}\\mathbf{Q},\\mathbf{W}\_{k}\\ ^{i}\\mathbf{K},\\mathbf{W}\_{v}\\ ^{i}\\mathbf{V})} \\\\ \\end{array}$$  
(2.18)

  
$$\\begin{array}{l} {multihead(\\mathbf{Q},\\mathbf{K},\\mathbf{V}) = \\mathbf{W}\_{O}\\text{concat}(head\_{1},\\ldots,head\_{h})} \\\\ \\end{array}$$  
(2.19)

#### 2.4.2.3 Masked multi-head attention

We want the decoder to learn from the encoder sequence and a particular decoder sequence, which has been already seen by the model, to predict the next word/character. Thus, for the first layer of the decoder, similar to the sequence-to-sequence architecture, only previous target tokens need to be present and others to be masked. This special alteration results in the masked multi-head attention. This is implemented by having a masking weight matrix **M** that has  − ∞ for future tokens and 0 for previous tokens. This computation is inserted after the scaling of the multiplication of **Q** and **K**^(*T*) and before the softmax so that the softmax results in the actual scaled values for previous tokens and the value 0 for future tokens.

  
$$\\begin{array}{l} {masked~Attention(\\mathbf{Q},\\mathbf{K},\\mathbf{V}) = \\text{softmax}\\left( \\frac{\\mathbf{Q}\\mathbf{K}^{\\text{T}}\\text{+}\\mathbf{M}}{\\sqrt{\\text{d}\_{\\text{k}}}} \\right)\\mathbf{V}} \\\\ \\end{array}$$  
(2.20)

#### 2.4.2.4 Encoder-decoder multi-head attention

In the decoder side there is a need to learn the attention relationship between the entire source input and the target output at a given time. Therefore, the query vectors from the target sequence (before a given time) and the keys and values from the entire input sequence of the encoder are passed to the self-attention layer in the decoder as shown in [Fig. 2.7](#ch2.xhtml#fig2_7).

### 2.4.3 Residuals and Layer Normalization

Similar to ResNets, the inputs, **X**, are short circuited to the output, **Z**, and both are added and passed through layer normalization *a**d**d**A**n**d**N**o**r**m*(**X** + **Z**) \[[105](#refbib.xhtml#refbib_105)\]. Layer normalization ensures each layer to have 0 mean and a unit (1) variance.

For each hidden unit, *h*[*i*], we can compute

  
$$h\_{i} = \\frac{g}{\\sigma}(h\_{i} - \\mu)$$  
(2.21)

where *g* is the gain variable (can be set to 1), *μ* is the mean given by $\\frac{1}{H}{\\sum\_{i = 1}^{H}h\_{i}}$ and *σ* is the standard deviation given by $\\sqrt{\\frac{1}{H}{(h\_{i} - \\mu)}^{2}}$.

Layer normalization reduces the **covariance shift**, i.e., the gradient dependencies between each layer, and therefore speeds up the convergence as fewer iterations are needed \[[13](#refbib.xhtml#refbib_13)\]. This is related to batch normalization, where batch normalization happens at one hidden unit level and a 0 mean and a unit (1) variance is achieved on that one batch \[[130](#refbib.xhtml#refbib_130)\]. Advantage of layer normalization is that it works independent of the batch size, i.e., can give a single example, small batch or a large batch.

### 2.4.4 Position wise Feed-forward Networks

Both encoder and decoder contain a fully connected feed-forward network after the attention sub layers. For each position, similar linear transformations with a ReLU activation in between is performed.

  
$$\\begin{array}{l} {FFN(\\mathbf{x}) = \\max(0,\\mathbf{x}\\mathbf{W}\_{1} + b\_{1})\\mathbf{W}\_{2} + b\_{2}} \\\\ \\end{array}$$  
(2.22)

Every position goes through the same transformations and they are different only at the layer level.

### 2.4.5 Encoder

The encoder block in the transformer consists of *n* blocks of {*multiheadAttention*, *addAndNorm*, *FFN*, *addAndNorm*} as shown in [Fig. 2.7](#ch2.xhtml#fig2_7). Every layer of multi-head attention in the encoder side attends to the input or the source, i.e., attention between inputs and inputs. Tenney et al. show that each layer of transformer in the encoder side performs a different NLP task in classical sense such as part-of-speech, constituents, dependencies, entity resolution, etc. \[[244](#refbib.xhtml#refbib_244)\].

### 2.4.6 Decoder

The decoder block in the transformer consists of *n* blocks of {*maskedMultiheadAttention*, *addAndNorm*, *encoderDecoderAttention*, *addAndNorm*, *FFN*, *addAndNorm*} as shown in [Fig. 2.7](#ch2.xhtml#fig2_7). The first layer of multi-head attention in the decoder side attends to the target, i.e., attention between masked outputs with themselves. The encoder-decoder attention layer creates attention between the source and the target.

## 2.5 Case Study: Machine Translation

### 2.5.1 Goal

This section will go through a real-world use case of sequence to sequence in the NLP domain—machine translation between English and French sentences. We will apply attention-based and transformer-based techniques to understand, compare, and contrast between the two architectures.

### 2.5.2 Data, Tools, and Libraries

The English-French parallel corpus from [https://www.manythings.org/​anki/​](https://www.manythings.org) is used for the machine translation. For necessary data wrangling and visualization, we use standard Python libraries like Pandas, NumPy, and Matplotlib. We use TorchText and spaCy for basic text processing such as tokenization. Attention-based and Transformer-based sequence-to-sequence are implemented using the PyTorch library.

### 2.5.3 Experiments, Results, and Analysis

#### 2.5.3.1 Exploratory data analysis

Basic data preprocessing like converting sentences to ASCII and filtering out the pairs that are too long is performed as a text normalization step. Then we tokenize the sentences, convert the words to token IDs, and append < bos > and < eos > IDs to the beginning and end of the token ID sequences. Padding the variable-length sequences to the maximum observed length in the batch using the < pad > token ensures a fixed-size tensor for training and evaluation.

The total of 135,842 language pairs after filtering reduce to 131,951 and we further split it into 80% training, 10% validation and 10% test data, i.e., 105,460, 13,308, and 13,183 respectively.

[Figs. 2.13](#ch2.xhtml#fig2_13) and [2.14](#ch2.xhtml#fig2_14) show the distribution plots as histograms for English/French and joint distribution. Most of the sentences in the parallel corpus are between 4 and 8 tokens/words length.

![Figure 2.13 Sentence length distribution for English and French sentences.](images/fig2_13.jpg)

[Figure 2.13](#ch2.xhtml#b2fig2_13) Sentence length distribution for English and French sentences.

![Figure 2.14 Joint distribution for English and French sentences based on length.](images/fig2_14.jpg)

[Figure 2.14](#ch2.xhtml#b2fig2_14) Joint distribution for English and French sentences based on length.

The top 20 words for English and French are shown in [Fig. 2.15](#ch2.xhtml#fig2_15). The frequency and distribution shows some common words as expected such as “the-le”, “is-est”, etc. It also highlights certain contractions such as “don” for “don't” and how the underlying tokenizer (spaCy) performs preprocessing. Iteratively improving and analyzing the data helps in the overall model results.

![Figure 2.15 Top 20 words from English and French sentences.](images/fig2_15.jpg)

[Figure 2.15](#ch2.xhtml#b2fig2_15) Top 20 words from English and French sentences.

Bahdanau attention-based sequence-to-sequence and transformer-based will be used to train/validate on the data and the best model from both will be evaluated on the test set.

#### 2.5.3.2 Attention

The encoder model class **BahdanauEncoder** as given in the [Listing 2.1](#ch2.xhtml#list2_1) uses a bidirectional gated recurrent unit (GRU) to encode sentences in the source language.

![](images/comp2_1.jpg)![Listing 2.1 Bahdanau encoder](images/comp2_1a.jpg)

[Listing 2.1](#ch2.xhtml#b2list2_1) Bahdanau encoder

The encoder model class **BahdanauAttentionQKV** as given in the [Listing 2.2](#ch2.xhtml#list2_2) calculates the attention weights using query and key tensors.

![](images/comp2_2.jpg)![Listing 2.2 Bahdanau attention layer](images/comp2_2a.jpg)

[Listing 2.2](#ch2.xhtml#b2list2_2) Bahdanau attention layer

The decoder model class **BahdanauDecoder** as given in the [Listing 2.3](#ch2.xhtml#list2_3) uses the hidden, encoder outputs and the attention weights to generate the next token.

![](images/comp2_3.jpg)![Listing 2.3 Bahdanau decoder](images/comp2_3a.jpg)

[Listing 2.3](#ch2.xhtml#b2list2_3) Bahdanau decoder

[Listing 2.4](#ch2.xhtml#list2_4) gives the overall structure of the sequence-to-sequence. The encoder and decoder has embedding fixed dimension of 256 and hidden layer size of 256. Regularization is done by adding a dropout of 0.15 for both encoders and decoders and the norms of the gradients are clipped at 10.

![](images/comp2_4.jpg)![Listing 2.4 Seq2seq with encoder, attention and decoder](images/comp2_4a.jpg)

[Listing 2.4](#ch2.xhtml#b2list2_4) Seq2seq with encoder, attention and decoder

[Listing 2.5](#ch2.xhtml#list2_5) shows the model training with both encoder and decoder using AdamW variant of Adam which is an improvement where the weight decay is decoupled from the optimization \[[172](#refbib.xhtml#refbib_172)\]. The learning rate is manually grid searched and fixed at 0.0001 for both encoder and decoder.

![Listing 2.5 Training for Bahdanau attention-based network](images/comp2_5.jpg)

[Listing 2.5](#ch2.xhtml#b2list2_5) Training for Bahdanau attention-based network

Perplexity is an intrinsic evaluation method often used for measuring the performance of tasks such as language modeling and machine translation \[[42](#refbib.xhtml#refbib_42)\]. In [Fig. 2.16](#ch2.xhtml#fig2_16), we show plots of perplexity and training/validation loss for the attention model, measured per epoch during the training process. It is interesting to note that the validation loss starts flattening out around epoch 14 and training loss further reduces, thus indicating overfitting. The best model for both approaches are chosen based on the best fit on the validation data.

![Figure 2.16 Attention-based seq2seq loss and perplexity on training and validation sets.](images/fig2_16.jpg)

[Figure 2.16](#ch2.xhtml#b2fig2_16) Attention-based seq2seq loss and perplexity on training and validation sets.

To understand how the attention mechanism operates during the translation process, we plot a few examples of the decoded attention outputs highlighting where the decoder is attending as shown in [Fig. 2.17](#ch2.xhtml#fig2_17). The outputs help visualizing and diagnosing issues in the data and the model. For example, [Fig. 2.17(a)](#ch2.xhtml#fig2_17) shows how English word “going” pays attention to “je” and “vais” and similarly how the “store” word pays attention to “au”, “magasin”, “.” and “ < eos > ”.

![Figure 2.17 Attention examples and plots.](images/fig2_17.jpg)

[Figure 2.17](#ch2.xhtml#b2fig2_17) Attention examples and plots.

#### 2.5.3.3 Transformer

The [Listing 2.6](#ch2.xhtml#list2_6) shows transformer model wrapping the PyTorch transformer block.

![](images/comp2_6.jpg)![Listing 2.6 Transformer model](images/comp2_6a.jpg)

[Listing 2.6](#ch2.xhtml#b2list2_6) Transformer model

![Listing 2.7 Transformer model with attention heads, encoding and decoding](images/comp2_7.jpg)

Listing 2.7 Transformer model with attention heads, encoding and decoding

#### 2.5.3.4 Results and analysis

[Fig. 2.18](#ch2.xhtml#fig2_18) are the plots for perplexity and training/validation loss for the transformer model measured per epoch during the training process.

![Figure 2.18 Transformer loss and perplexity on training and validation sets.](images/fig2_18.jpg)

[Figure 2.18](#ch2.xhtml#b2fig2_18) Transformer loss and perplexity on training and validation sets.

The validation loss plateau's at a value less than 2 in epoch 20, comparing to the value around 2.5 in the attention mechanism. Also, the perplexity of attention is almost double of the transformer model in the validation set.

[Fig. 2.19](#ch2.xhtml#fig2_19) shows comparative performance of attention-based and transformer-based models on the same test dataset. Perplexity of transformers is almost three times less than that of attention proving the benefits of the architecture in the real-world translation problem.

![Figure 2.19 Loss and perplexity on the test set.](images/fig2_19.jpg)

[Figure 2.19](#ch2.xhtml#b2fig2_19) Loss and perplexity on the test set.

#### 2.5.3.5 Explainability

We can use the gradient values for the input sequence to illustrate each generated token's dependence on each input token. We start by performing a forward pass on embedded inputs. We then take the token with the highest logit value (in the same way as greedy decoding earlier), and perform a backward pass from the highest logit value. This populates the gradients back through the model to embedded inputs, showing the resulting distribution. Finally, we repeat this process for each generated token and visualize the resulting matrix.

[Fig. 2.20](#ch2.xhtml#fig2_20) shows RNN vs. Transformer for the translation and it can be seen that the RNN pairs the formal/plural “serez” with the informal/singular “tu” while transformer matches “seras tu”.

![Figure 2.20 Explaining translations for—How long you will be here?](images/fig2_20.jpg)

[Figure 2.20](#ch2.xhtml#b2fig2_20) Explaining translations for—How long you will be here?

[Fig. 2.21](#ch2.xhtml#fig2_21) shows another RNN vs. Transformer for the translation and it can be seen that the RNN doesn't capture the “snowing” portion of the sentence and produces a different phrasing of “my house”.

![Figure 2.21 Explaining translations for—It is snowing at my house.](images/fig2_21.jpg)

[Figure 2.21](#ch2.xhtml#b2fig2_21) Explaining translations for—It is snowing at my house.

# CHAPTER 3Bidirectional Encoder Representations from Transformers (BERT)

DOI: [10.1201/9781003170082-3](https://doi.org/10.1201/9781003170082-3)

THE advent of Bidirectional Encoder Representations from Transformer (BERT) \[[72](#refbib.xhtml#refbib_72)\] is considered the onset of a revolution in the field of Natural Language Processing (NLP). BERT uses unlabeled text to pre-train deep bidirectional contextual representations. This resulted in rich pre-trained language models that can be fine-tuned with a simple additional output layer and a reasonably sized labeled dataset to produce state-of-the-art performance in a broad range of NLP tasks. These developments lowered the barrier of entry for the wide adoption of these powerful pre-trained models. It is now common practice in the artificial intelligence field to share pre-trained models and fine-tune them with minimal cost as opposed to the old paradigm of designing task-specific architectures. In this chapter, we cover BERT's basic design concepts, developments, and applications.

## 3.1 bert

### 3.1.1 Architecture

**Core layers** One of the major contributions of BERT is the simplicity of design and the diversity of covered downstream tasks. BERT's architecture consists of multi-layers of the bidirectional transformer encoder \[[253](#refbib.xhtml#refbib_253)\]. The capacity of the BERT architecture is characterized by (i) the number of transformer layers *L*, (ii) the size of hidden representations *H*, and the number of bidirectional self-attention heads *A*.

**Input and Output Representations** Given the simplicity of the BERT's core architecture, just a stack of bidirectional transformer encoders, the ingenuity of BERT lies in the design of input and output representations that can be used to train many downstream NLP tasks with the same architecture. To that end, BERT's input is designed to distinctly represent NLP downstream tasks involving a single or a pair of sentences using the same input representation design. Most major NLP downstream tasks can be covered using a single sentence (e.g., text classification, sequence tagging, summarization, etc.) or paired sentences (e.g., question answering, natural language inference, etc.).

For any input sequence, BERT prefixes a special \[CLS\] token. The hidden vector of this token in the last BERT layer will be used as an aggregate representation for the entire input sequence and usually used for classification tasks. For NLP tasks with paired sentences, BERT concatenates the sentences into one sequence with a separator token \[SEP\] in between, which serves as one way BERT uses to distinguish the two sentences. BERT also uses a learned segment embedding to indicate to which sentence a token belongs. BERT employs WordPiece \[[272](#refbib.xhtml#refbib_272)\] to tokenize and embed input sequences. Finally, BERT uses position embedding layer to encode the order of tokens within the input. The input to BERT is the sum of the aforementioned token embedding, segment embedding, and positional embedding for each token as illustrated in [Fig. 3.1](#ch3.xhtml#fig3_1).

![Figure 3.1 BERT input configuration \[71\].](images/fig3_1.jpg)

[Figure 3.1](#ch3.xhtml#b3fig3_1) BERT input configuration \[[71](#refbib.xhtml#refbib_71)\].

### 3.1.2 Pre-Training

**Masked Language Model (MLM)** The idea is to randomly mask-out a percentage of the input sequence tokens, replacing them with the special \[MASK\] token. During pre-training, the modified input sequence is run through BERT and the output representations of the masked tokens are then fed into a softmax layer over the WordPiece vocabulary as practiced in standard language models pre-training. The bidirectional attention of the transformer encoder forces the \[MASK\] prediction task to use the context provided by the other non-masked tokens in the sequence. BERT is pre-trained with a 15% mask-out rate. This simple MLM task has a downside where a mismatch is created between pre-training and fine-tuning tasks as the special \[MASK\] token does not appear during fine-tuning. To overcome this issue, every token in the 15% masked-out tokens is subjected to the following heuristic:

*   With a probability of 80%, the token is replaced with the special \[MASK\] token.
    
*   With a probability of 10%, the token is replaced with a random token.
    
*   With a probability of 10%, the token is left unchanged.
    

The occasional insertion of random tokens (i.e., noise) pushes BERT to be less biased towards the masked token, especially when the masked token is left unchanged, in its bidirectional context attention. The MLM task uses cross-entropy loss only over the masked tokens and ignores the prediction of all non-masked ones.

**Next Sentence Prediction (NSP)** Many downstream NLP tasks require understanding the relationship between two sentences, such as Question Answering (QA) and Natural Language Inference (NLI). Standard language models do not pick up this type of knowledge. This motivates the NSP task, where BERT is fed pairs of sentences and pre-trained to predict if the second sentence should follow the first one in a continuous context. As discussed earlier, the first sentence is prefixed with the \[CLS\] token, then the two sentences are delimited by the special token \[SEP\]. During NSP task pre-training, the model is given sentence pairs where 50% of the time the second sentence comes after the first sentence and the other 50% the second sentence is a random sentence from the full training corpus. The self-attention of Transformer layers encourages the BERT representation of \[CLS\] token to encode both input sentences. Therefore, NSP pre-training is performed by adding a single layer MLP with softmax atop the \[CLS\] token representation to predict the binary NSP label. BERT pre-training involves combined training with both MLM and NSP tasks by optimizing the model parameters over their combined loss function. [Fig. 3.2](#ch3.xhtml#fig3_2) illustrates BERT's pre-training tasks.

![Figure 3.2 BERT pre-training architecture \[71\].](images/fig3_2.jpg)

[Figure 3.2](#ch3.xhtml#b3fig3_2) BERT pre-training architecture \[[71](#refbib.xhtml#refbib_71)\].

### 3.1.3 Fine-Tuning

With BERT simple and yet versatile design, fine-tuning a pre-trained model for many downstream tasks is a straightforward task that involves simply plugging in the proper inputs and outputs and fine-tuning all the model's parameters end-to-end. As discussed earlier many NLP tasks can be modeled using two sentences input to BERT. For tasks like Question Answering (QA) and Natural Language Inference (NLI), the input to BERT is a concatenated question-answer sentence pair and the hypothesis-premise sentence pair, respectively. Other tasks with single input sentence, such as text classification and sequence tagging (e.g., POS, NER), the input to BERT is modeled again as concatenated sentences but with one of them empty. For token level tasks (e.g., QA, POS, and NER), BERT output tokens representations are fed into an output layer for token tagging. [Fig. 3.3](#ch3.xhtml#fig3_3) provides an illustration for the BERT fine-tuning for token level tasks. For tasks like text classification and NLI, the output representation of the special token \[CLS\] is used as input to an output layer to produce a label. [Figs. 3.4](#ch3.xhtml#fig3_4) and [3.5](#ch3.xhtml#fig3_5) depict BERT fine-tuning architectures for single sequence and paired-sequences classification tasks.

![Figure 3.3 BERT fine-tuning architecture for token tagging tasks (e.g., POS, NER, and QA) \[71\].](images/fig3_3.jpg)

[Figure 3.3](#ch3.xhtml#b3fig3_3) BERT fine-tuning architecture for token tagging tasks (e.g., POS, NER, and QA) \[[71](#refbib.xhtml#refbib_71)\].

![Figure 3.4 BERT fine-tuning architecture for single sequence classification tasks \[71\].](images/fig3_4.jpg)

[Figure 3.4](#ch3.xhtml#b3fig3_4) BERT fine-tuning architecture for single sequence classification tasks \[[71](#refbib.xhtml#refbib_71)\].

![Figure 3.5 BERT fine-tuning architecture for paired-sequence classification tasks (e.g., NLI) \[71\].](images/fig3_5.jpg)

[Figure 3.5](#ch3.xhtml#b3fig3_5) BERT fine-tuning architecture for paired-sequence classification tasks (e.g., NLI) \[[71](#refbib.xhtml#refbib_71)\].

## 3.2 Bert Variants

### 3.2.1 Robustly Optimized BERT Pre-training Approach (RoBERTa)

RoBERTa \[[170](#refbib.xhtml#refbib_170)\] is a Robustly Optimized BERT Pre-training Approach that improves on the original BERT model in terms of pre-training tasks, training hyperparameters, and pre-training data. As discussed earlier, BERT uses two pre-training tasks, Masked Language Model (MLM) and Next Sentence Prediction (NSP). For the MLM task, BERT randomly masks token during the data pre-processing stage. Therefore, the masks stay static throughout the entire model training process. RoBERTa on the other hand follows a dynamic masking strategy where masked tokens are randomly chosen for each training epoch. RoBERTa also drops the NSP pre-training task and only uses the dynamic MLM task. Another contribution for RoBERTa is the size of input sequences, where full sentences of at most 512 tokens, are sampled contiguously from one or more documents. If the end of a document is reached before getting the required input sequence size, sentence sampling continues with the next document after adding an extra separator token.

On the hyperparameters front, RoBERTa showed that using large mini-batches with increased learning rates during pre-training improves the perplexity of the dynamic MLM task as well as the downstream task performance. RoBERTa is also pre-trained on an order of magnitude more data than BERT, the pre-training data consists of 160 GB including Books Corpus, English [Wikipedia](http://Wikipedia), and CommonCrawl News dataset (63 million articles, 76 GB), Web text corpus (38 GB) and Stories from Common Crawl (31 GB).

To summarize, using the same basic architecture as BERT, RoBERTa has shown that the following design changes significantly improves RoBERTa performance over BERT.

1.  Pre-training the model for longer time
    
2.  Using bigger batches
    
3.  Using more training data
    
4.  Removing the NSP pre-training task
    
5.  Training on longer sequences
    
6.  Dynamically changing the masking pattern applied to the training data.
    

## 3.3 Applications

### 3.3.1 TaBERT

TaBERT \[[289](#refbib.xhtml#refbib_289)\] is the first model to have been pre-trained on both natural language sentences and tabular data formats. These representations are advantageous for problems involving cooperative reasoning over natural language sentences and tables. Semantic parsing over databases is a sample example, in which a natural language inquiry (e.g., “Which nation has the largest GDP?”) is translated to a program executable over database (DB) tables. This is the first technique of pre-training that spans structured and unstructured domains, and it opens up new possibilities for semantic parsing, where one of the primary issues has been comprehending the structure of a database table and how it fits with a query. TaBERT was trained on a corpus of 26 million tables and the English phrases that accompany them. Historically, language models have been trained only on free-form natural language text. While these models are excellent for jobs that need reasoning only in free-form natural language, they are insufficient for activities such as database-based question answering, which involves reasoning in both free-form language and database tables.

Two commonly used benchmarks for database-based question answering were utilized: a traditional supervised text-to-SQL job over structured data from the Spider dataset and a weakly supervised parsing task over a semi-structured dataset from the WikiTableQuestions dataset. Weakly supervised learning is substantially more difficult than supervised learning, since the parser lacks access to the labeled question and must instead explore a very vast search space of queries. TaBERT is a Natural Language Processing (NLP) model built on top of the BERT model that accepts natural language queries and tables as input. TaBERT acquires contextual representations for sentences as well as the constituents of the DB table in this manner. These representations may then be utilized to generate real database instructions in other neural networks. TaBERT's representations may then be fine-tuned further using the training data for that job.

TaBERT is trained via content snapshots, in which the model only encodes the bits of a table that are most relevant to a query. Due to the enormous amount of rows in certain database tables, encoding them is a computationally intensive and inefficient procedure. By encoding just the portion of material that is most relevant to the utterance, content snapshots enable TaBERT to handle with enormous tables. For instance, the phrase “In which city did Piotr finish first last time?” (sample extracted from the WikiTableQuestions dataset) may be accompanied with a table including information on the year, venue, position, and event. A snapshot of content will take a subset of three rows. This subset will not include all of the table's data, but it is sufficient for the model to understand that, for example, the venue column comprises cities. TaBERT describes table structure using a mix of traditional horizontal self-attention, which captures the dependence between cells in specific rows, and vertical self-attention, which catches the information flow between cells in different rows. The ultimate outputs of layers of such horizontal and vertical self-attention are distributed representations of utterance tokens and table columns, which may be utilized to calculate the database query by downstream semantic parsers.

### 3.3.2 BERtopic

Topic modeling is one of the challenging topics in NLP. The advances in BERT and its variants motivate the NLP community to leverage BERT in topic modeling. Grootendorst \[[101](#refbib.xhtml#refbib_101)\] introduced an elegant idea, BERTopic, to extract interpretable topics in documents using BERT and transformers embeddings. Hence, takes advantage of the state-of-the-art pre-trained transformers model. The method starts by creating the embeddings of the documents of interest using BERT models. Since documents can be very large and BERT models have limit on the token size, the documents are preprocessed before extracting the embeddings. Preprocessing divides the document to smaller paragraphs or sentences that are smaller than the token size for the transformer model. Then, clustering is performed on the document embeddings to cluster all the documents with similar topics together. It is worth noting that dimensionality reduction for the embeddings is recommended before performing the clustering. Dimensionality reduction algorithms such as t-Distributed Stochastic Neighbor Embedding (t-SNE) or Uniform Manifold Approximation and Projection (UMAP) can be used to lower the dimensions. The topics are then derived from the clustered documents using the novel class-based metric introduced by Grootendorst in \[[101](#refbib.xhtml#refbib_101)\]. Class-Based Term Frequency-Inverse Document Frequency (c-TF-IDF) is modification of the classic Term Frequency-Inverse Document Frequency (TF-IDF) in which all documents in a certain category is considered as a single document then compute TF-IDF. Therefore, the TF-IDF in this case would represent the importance of words in a topic, not in a document. The Class-Based Term Frequency-Inverse Document Frequency (c-TF-IDF) is computed as

  
$$\\begin{array}{l} {c - TF - IDF\_{i} = \\frac{t\_{i}}{w\_{i}} \\times \\log\\frac{m}{\\sum\\limits\_{j}^{n}t\_{j}}} \\\\ \\end{array}$$  
(3.1)

where the frequency of each word *t* is extracted for each class *i* and normalized by the total number of words and this is weighted by the normalized number of documents per the total frequency of the word *t* across all the classes *n*. In other words, instead of computing the relative importance of a word in a document as compared to the other documents, the metric in (3.1) computed the relative importance of a word in a class (i.e., topic) as compared to the other topics.

## 3.4 Bert Insights

### 3.4.1 BERT Sentence Representation

Due to self-attention in the Transformer encoder, the BERT representation of the special token \[CLS\] encodes both the two sentences from the input. Hence, the output layer of the MLP classifier takes X as the input, where X is the output of the MLP hidden layer whose input is the encoded \[CLS\] token. Because a pre-trained model is not fine-tuned on any downstream tasks yet. In this case, the hidden state of \[CLS\] is not a good sentence representation. If later you fine-tune the model, you may use \[CLS\] as well.

BERT sentence representation can also be obtained by pooling the individual token representations. However, the last layer is too close to the target functions (i.e., masked language model and next sentence prediction) during pre-training, therefore may be biased to those targets.

### 3.4.2 BERTology

The great push BERT has provided to the NLP field triggered much research into understanding how it works and the type of knowledge it extracts through massive pre-training. BERTology aims to answer some of the questions about why BERT performs well on so many NLP tasks. Some of the topics addressed by BERTology include the type of knowledge learned by BERT and where it is represented. In general there three types of knowledge BERT acquires: Syntactic knowledge, Semantic knowledge, World knowledge.

BERT representations of syntactic knowledge are hierarchical rather than linear, i.e., they include a syntactic tree structure in addition to the word order information. Additionally, BERT embeddings store information about speech segments, grammatical chunks, and roles. BERT's understanding of syntax, on the other hand, is incomplete, since probing classifiers were unable to retrieve the labels of distant parent nodes in the syntactic tree. In terms of how syntactic information is represented, it seems that self-attention weights do not directly encode syntactic structure, but they may be changed to reflect it. When executing the cloze task, BERT takes subject-predicate agreement into consideration. Additionally, it was shown that BERT does not ”understand” negation and is indifferent to input that is faulty.

Regarding aspects of semantic knowledge, BERT has shown some knowledge for semantic roles. Also BERT encodes information about entity types, relations, semantic roles, and proto-roles. However, it was found that BERT struggles with representations of numbers. Research probing into BERT's world knowledge capabilities showed that, for some relation types, vanilla BERT is competitive with methods relying on knowledge bases. However, BERT cannot reason based on its world knowledge. Essentially BERT can “guess” the affordances and properties of many objects, but does not have the information about their interactions (e.g., it “knows” that people can walk into houses, and that houses are big, but it cannot infer that houses are bigger than people.)

Additionally, BERTology is concerned with the localization of linguistic information inside the BERT architecture, either at the self-attention heads or at the layer level. It was shown that the majority of self-attention heads do not encode any non-trivial linguistic information directly, since fewer than half of them exhibited the ”heterogeneous” pattern2. The vertical pattern was stored in a large portion of the model (attention to \[CLS\], \[SEP\], and punctuation tokens). Additionally, certain BERT heads seem to specialize in particular sorts of syntactic relations, with heads paying much more attention to words in specific syntactic places than a random baseline. Other studies discovered that no one head contains the whole syntactic tree. Additionally, attention weights are illustrative of subject-verb agreement and reflexive anaphora. Additionally, it was shown that even when attention heads specialize in monitoring semantic relations, they do not always help BERT perform well on related tasks.

For layer-level knowledge localization, provided that the first layer of BERT gets representations in the form of a mix of token, segment, and positional embeddings as input. It comes to reason that the bottom levels contain the most linear information about word order. It was shown that the knowledge of linear word order decreases around layer 4 in the BERT-base. This is followed by an enhanced understanding of the hierarchical structure of sentences. Numerous studies have shown that the middle BERT layers contain the most syntactic information and that the last BERT levels include the most task-specific information. Additionally, it was shown that, although the majority of syntactic information may be localized in a few levels, semantic information is distributed across the model, which explains why some non-trivial cases are initially handled wrong then successfully at higher layers.

## 3.5 Case Study: Topic Modeling With Transformers

### 3.5.1 Goal

In this chapter, we looked at several applications of the Transformer architecture. In this case study, we see how to use pre-trained (or finetuned) Transformer models to do topic modeling. If one is exploring a new dataset, this method could be used during exploratory data analysis.

### 3.5.2 Data, Tools, and Libraries

![Listing 3.1 Python environment setup](images/comp3_1.jpg)

[Listing 3.1](#ch3.xhtml#b3list3_1) Python environment setup

We will use pre-trained transformers to explore the Yelp reviews dataset (from [https://huggingface.co/​datasets/​yelp\_review\_full](https://huggingface.co)) and see what kind of topics are in the reviews. We'll generate sentence embeddings with the sentence-transformers library (see [https://github.com/​UKPLab/​sentence-transformers](https://github.com)). which provides models pre-trained for specific tasks, such as semantic search. Lastly, we're going to use BERTopic \[[101](#refbib.xhtml#refbib_101)\] (see [https://github.com/​MaartenGr/​BERTopic](https://github.com)) for topic modeling and Huggingface Datasets for loading the data. We can install these as shown in [Listing. 3.1](#ch3.xhtml#list3_1).

#### 3.5.2.1 Data

![Listing 3.2 Load dataset](images/comp3_2.jpg)

[Listing 3.2](#ch3.xhtml#b3list3_2) Load dataset

We begin by loading the Yelp Review Full dataset via Huggingface Datasets in [Listing 3.2](#ch3.xhtml#list3_2). There are 650,000 reviews in the dataset. To keep the runtime of this case study within reason, we'll only process the first 10,000 reviews. To process more reviews, simply change the value of *N* in Listing 3.2.

#### 3.5.2.2 Compute embeddings

![](images/comp3_3.jpg)![Listing 3.3 Compute embeddings](images/comp3_3a.jpg)

[Listing 3.3](#ch3.xhtml#b3list3_3) Compute embeddings

We'll generate embeddings using the “all-mpnet-base-v2” model from sentence-transformers in [Listing 3.3](#ch3.xhtml#list3_3). It's built to perform well on semantic search when embedding sentences and longer spans of text.

### 3.5.3 Experiments, Results, and Analysis

#### 3.5.3.1 Building topics

![Listing 3.4 Compute topics](images/comp3_4.jpg)

[Listing 3.4](#ch3.xhtml#b3list3_4) Compute topics

Now that we've computed the embeddings for the specified subset of Yelp reviews, we can proceed with the topic modeling in [Listing 3.4](#ch3.xhtml#list3_4).

#### 3.5.3.2 Topic Size Distribution

![Listing 3.5 Sampling the topics](images/comp3_5.jpg)

[Listing 3.5](#ch3.xhtml#b3list3_5) Sampling the topics

Now that we have computed a topic distribution, we need to see what kind of reviews are in each topic. Let's start by looking at the distribution of topic sizes.

The commands in [Listing 3.5](#ch3.xhtml#list3_5) will output a summary table of the sizes of the topics. Note that the size of a topic is the number of reviews that contain that topic. The table is shown in [Fig. 3.6](#ch3.xhtml#fig3_6).

![Figure 3.6 Table showing sizes and names of largest and smallest topics.](images/fig3_6.jpg)

[Figure 3.6](#ch3.xhtml#b3fig3_6) Table showing sizes and names of largest and smallest topics.

Note the topic with id of –1. This corresponds to the unassigned cluster output by the HDBSCAN algorithm. The unassigned cluster is composed of all the things that could not be assigned to one of the other clusters. It can *generally* be ignored, but if it were too large, it would be a sign that our choice of parameters are probably not good for our data. One can look at the contents of the unassigned cluster to verify that it contains words that are not relevant.

#### 3.5.3.3 Visualization of Topics

![Listing 3.6 Visualizing the 10 largest topics](images/comp3_6.jpg)

[Listing 3.6](#ch3.xhtml#b3list3_6) Visualizing the 10 largest topics

BERTopic includes several ways to visualize different aspects of the topic distribution. In [Listing 3.6](#ch3.xhtml#list3_6) we sample the 10 largest topics, which are shown in [Fig. 3.7](#ch3.xhtml#fig3_7).

![Figure 3.7 The 10 largest topics.](images/fig3_7.jpg)

[Figure 3.7](#ch3.xhtml#b3fig3_7) The 10 largest topics.

![Listing 3.7 Visualizing the cosine similarity of the 20 largest topics](images/comp3_7.jpg)

[Listing 3.7](#ch3.xhtml#b3list3_7) Visualizing the cosine similarity of the 20 largest topics

BERTopic can also show a heatmap of the cosine similarities of the topic embeddings, using the *v**i**s**u**a**l**i**z**e*[*h*]*e**a**t**m**a**p* method, as shown in [Listing. 3.7](#ch3.xhtml#list3_7). The heatmap is shown in [Fig. 3.8](#ch3.xhtml#fig3_8) and it shows the degree of overlap between the embedding vectors of each pair of topics.

![Figure 3.8 Heatmap of the cosine similarity of the 20 largest topics.](images/fig3_8.jpg)

[Figure 3.8](#ch3.xhtml#b3fig3_8) Heatmap of the cosine similarity of the 20 largest topics.

#### 3.5.3.4 Content of topics

![Listing 3.8 Print the topic size and representative words](images/comp3_8.jpg)

[Listing 3.8](#ch3.xhtml#b3list3_8) Print the topic size and representative words

Now we'll look at a sample of topics. We looked at the 10 largest topics in [Fig. 3.7](#ch3.xhtml#fig3_7), so here we'll look at the largest and smallest topics, the topic with median size, and the contents of the unassigned cluster. [Listing 3.8](#ch3.xhtml#list3_8) shows a simple helper function we can use to print the size of a topic and the 10 words most relevant to the topic.

![](images/comp3_9.jpg)![Listing 3.9 Unassigned cluster](images/comp3_9a.jpg)

[Listing 3.9](#ch3.xhtml#b3list3_9) Unassigned cluster

First, we'll look at the unassigned cluster, which has topic id –1, to verify that we can safely ignore its contents. It's in [Listing 3.9](#ch3.xhtml#list3_9).

As we can see, the content of the unassigned cluster contains words that do not strongly belong to any topic. The largest, smallest, and median topics are shown in [Listings 3.10](#ch3.xhtml#list3_10), [3.11](#ch3.xhtml#list3_11), and [3.12](#ch3.xhtml#list3_12), respectively.

![](images/comp3_10.jpg)![Listing 3.10 Largest topic: Italian food restaurants](images/comp3_10a.jpg)

[Listing 3.10](#ch3.xhtml#b3list3_10) Largest topic: Italian food restaurants

![Listing 3.11 Smallest topic: the ambiance and arrangement of stores](images/comp3_11.jpg)

[Listing 3.11](#ch3.xhtml#b3list3_11) Smallest topic: the ambiance and arrangement of stores

![](images/comp3_12.jpg)![](images/comp3_12a.jpg)![Listing 3.12 Median topic: Nightlife in Charlotte, NC](images/comp3_12b.jpg)

[Listing 3.12](#ch3.xhtml#b3list3_12) Median topic: Nightlife in Charlotte, NC

## 3.6 Case Study: Fine-Tuning Bert

### 3.6.1 Goal

The goals of this case study is to provide a step-by-step demo of fine-tuning a standard BERT model for any sentence classification, we chose sentiment classification as a sample popular task.

### 3.6.2 Data, Tools, and Libraries

We chose the Google Play application review dataset. The dataset includes 15,746 samples in three categories; namely negative, neutral, and positive. We use the Huggingface transformer library to perform the fine-tuning task as well as standard Python data science stack for all other data handling and visualization \[[249](#refbib.xhtml#refbib_249)\] ([Fig. 3.9](#ch3.xhtml#fig3_9), [Fig. 10](#ch3.xhtml#fig3_10), [Fig. 3.11](#ch3.xhtml#fig3_11)).

![Figure 3.9 Exploratory data analysis of the sentiment classification dataset.](images/fig3_9.jpg)

[Figure 3.9](#ch3.xhtml#b3fig3_9) Exploratory data analysis of the sentiment classification dataset.

![Figure 3.10 Training and validation loss throughout training.](images/fig3_10.jpg)

[Figure 3.10](#ch3.xhtml#b3fig3_10) Training and validation loss throughout training.

![Figure 3.11 Confusion matrix of test set.](images/fig3_11.jpg)

[Figure 3.11](#ch3.xhtml#b3fig3_11) Confusion matrix of test set.

We use BERT[BASE] as the starting pre-trained BERT mode. Listing 3.6.3 shows how to load the pre-trained BERT model from the Transformers library and illustrates the output of tokenization that will be used to fine-tune the BERT model \[[249](#refbib.xhtml#refbib_249)\].

### 3.6.3 Experiments, Results, and Analysis

![](images/comp3_13.jpg)![](images/comp3_13a.jpg)

Listing 3.6.3 provides the tooling to ingest our dataset as well as split the data into train, validation, and testing. It also creates data loader for each data split which to use throughout the fine-tuning iterations \[[249](#refbib.xhtml#refbib_249)\].

![](images/comp3_14.jpg)![](images/comp3_14a.jpg)

Listing 3.6.3 creates the fine-tuned model and sets the parameters of the associated loss, optimizer, and learning rate scheduling \[[249](#refbib.xhtml#refbib_249)\].

![](images/comp3_15.jpg)![](images/comp3_15a.jpg)![](images/comp3_16.jpg)![](images/comp3_16a.jpg)![](images/comp3_17.jpg)![](images/comp3_18.jpg)![](images/comp3_18a.jpg)

# CHAPTER 4Multilingual Transformer Architectures

DOI: [10.1201/9781003170082-4](https://doi.org/10.1201/9781003170082-4)

THE introduction of BERT \[[72](#refbib.xhtml#refbib_72)\] has transformed the area of Natural Language Processing (NLP) and resulted in state-of-the-art performance on a broad range of tasks. In the recent past, training NLP algorithms worked only with labeled data, which hindered their progress for years due to the limited availability and cost of collecting data for every new task and every new project. One major contribution of BERT is introducing a new pipeline for training NLP systems where algorithms can learn about core and generic natural language concepts from huge amount of cheap unlabeled data, a process also known as self-supervised learning or model pre-training. A pre-trained model is then fine-tuned for any specific downstream task using much smaller task-specific labeled datasets. This new pipeline of pre-training followed by fine-tuning constitutes the core of most advances in the machine learning field. The major success of BERT for English NLP tasks has motivated its use for other languages. However, using BERT's pipeline is only possible for languages with sufficiently large unlabeled data for pre-training. This motivated the development of multilingual models where models are pre-trained on multiple languages with the hope that the models will transfer core NLP knowledge from high-resource languages to low-resource ones and we end up with a polyglot model that aligns multilingual representations across languages.

This chapter covers the state-of-the-art developments in multilingual transformer architectures. A multilingual transformer architecture is fully defined using:

*   Model Architecture (layers and components)
    
*   Pre-training Tasks
    
*   Pre-training Data
    
*   Fine-tuning Tasks and Benchmarks
    

The chapter starts with different multilingual transformer architecture for Natural Language Understanding (NLU) and Natural Language Generation (NLG). [Section 4.2](#ch4.xhtml#sec4_2) proceeds by describing the state-of-the-art in multilingual data, this includes unlabeled pre-training data and fine-tuning benchmarks for downstream NLP tasks. [Section 4.3](#ch4.xhtml#sec4_3) provides some insights into the inner workings of multilingual transformer models. Finally, [Section 4.4](#ch4.xhtml#sec4_4) provides a practical case study on zero-shot multilingual sentiment classification.

## 4.1 Multilingual Transformer Architectures

This section discusses the different architectural designs for multilingual Transformers. We divide multilingual transformers into (i) Natural Language Understanding (NLU) architectures and (ii) Natural Language Generation (NLG) architectures. [Table 4.1](#ch4.xhtml#tbl4_1)\[[74](#refbib.xhtml#refbib_74)\] provides a summary of the impactful multilingual transformer models available at the time of publishing this book.

 [TABLE 4.1](#ch4.xhtml#b4tbl4_1) Summary of multilingual language models \[[74](#refbib.xhtml#refbib_74)\] 

 
| **Model** || Architecture || pre-training || #Langs. || Ref. |
| --- | --- | --- | --- | --- |
| \# Parmas. || Objective Function || Mono. || Parallel ||  ||  |
| IndicBERT || 33M || MLM || IndicCorp || ✗ || 12 || \[[137](#refbib.xhtml#refbib_137)\] |
| --- | --- | --- | --- | --- | --- | --- |
| mBERT || 172M || MLM || [Wikipedia](http://Wikipedia) || ✗ || 104 || \[[72](#refbib.xhtml#refbib_72)\] |
| Amber || 172M || MLM, TLM, CLWA, CLSA || [Wikipedia](http://Wikipedia) || ✓ || 104 || \[[121](#refbib.xhtml#refbib_121)\] |
| MuRIL || 236M || MLM, TLM || CommonCrawl + [Wikipedia](http://Wikipedia) || ✓ || 17 || \[[141](#refbib.xhtml#refbib_141)\] |
| VECO-small || 247M || MLM, CS-MLM || CommonCrawl || ✓ || 50 || \[[175](#refbib.xhtml#refbib_175)\] |
| Unicoder || 250M || MLM, TLM, CLWR, CLPC, CLMLM || [Wikipedia](http://Wikipedia) || ✓ || 15 || \[[125](#refbib.xhtml#refbib_125)\] |
| XLM-15 || 250M || MLM, TLM || [Wikipedia](http://Wikipedia) || ✓ || 15 || \[[63](#refbib.xhtml#refbib_63)\] |
| InfoXLM-base || 270M || MLM, TLM, XLCO || CommonCrawl || ✓ || 94 || \[[48](#refbib.xhtml#refbib_48)\] |
| XLM-R-base || 270M || MLM || CommonCrawl || ✗ || 100 || \[[61](#refbib.xhtml#refbib_61)\] |
| HiCTL-base || 270M || MLM, TLM, HICTL || CommonCrawl || ✓ || 100 || \[[266](#refbib.xhtml#refbib_266)\] |
| Ernie-M-base || 270M || MLM, TLM, CAMLM, BTMLM || CommonCrawl || ✓ || 100 || \[[194](#refbib.xhtml#refbib_194)\] |
| HiCTL-Large || 559M || MLM, TLM, HICTL || CommonCrawl || ✓ || 100 || \[[266](#refbib.xhtml#refbib_266)\] |
| Ernie-M-Large || 559M || MLM, TLM, CAMLM, BTMLM || CommonCrawl || ✓ || 100 || \[[194](#refbib.xhtml#refbib_194)\] |
| InfoXLM-Large || 559M || MLM, TLM, XLCO || CommonCrawl || ✓ || 94 || \[[48](#refbib.xhtml#refbib_48)\] |
| XLM-R-Large || 559M || MLM || CommonCrawl || ✗ || 100 || \[[61](#refbib.xhtml#refbib_61)\] |
| RemBERT || 559M || MLM || CommonCrawl + [Wikipedia](http://Wikipedia) || ✗ || 110 || \[[54](#refbib.xhtml#refbib_54)\] |
| X-STILTS || 559M || MLM || CommonCrawl || ✗ || 100 || \[[198](#refbib.xhtml#refbib_198)\] |
| XLM-17 || 570M || MLM, TLM || [Wikipedia](http://Wikipedia) || ✓ || 17 || \[[63](#refbib.xhtml#refbib_63)\] |
| XLM-100 || 570M || MLM, TLM || [Wikipedia](http://Wikipedia) || ✗ || 100 || \[[63](#refbib.xhtml#refbib_63)\] |
| VECO-Large || 662M || MLM, CS-MLM || CommonCrawl || ✓ || 50 || \[[175](#refbib.xhtml#refbib_175)\] |

### 4.1.1 Basic Multilingual Transformer

Multilingual transformer models are typically based on the mBERT architecture \[[72](#refbib.xhtml#refbib_72)\]. In this section, we describe the basic components of a multilingual transformer architecture.

**Input Layer** A series of tokens is provided as input to the multilingual transformer. The token input is derived from a one-shot representation of a limited vocabulary, often a subword vocabulary. Typically, this vocabulary is learned by concatenating monolingual data from several languages using algorithms such as BPE \[[223](#refbib.xhtml#refbib_223)\], WordPiece \[[273](#refbib.xhtml#refbib_273)\], or SentencePiece \[[144](#refbib.xhtml#refbib_144)\]. To guarantee that diverse languages and scripts are well represented in the vocabulary, data may be sampled using exponential weighted smoothing or distinct vocabularies for clusters of languages can be learned \[[55](#refbib.xhtml#refbib_55)\] by dividing the vocabulary size.

**Transformer Layers** Typically a multilingual Language Model (mLM) makes up the encoder of a multilingual transformer. It consists of a stack of *N* layers, each of which has *k* attention heads followed by a feed-forward neural network. An attention head computes an embedding for each token in the input sequence by combining the representations of all other tokens in the sentence using an attention weighted linear combination. Concatenating the embeddings from all the attention heads and passing them through a feed-forward network generates a *d*\-dimensional embedding for each input word.

**Output Layer** Typically, the outputs of the final transformer layer are utilized as contextual representations for each token, while the embedding associated with the \[CLS\] token is considered to be the embedding of the entire input text. Alternatively, the text embedding may be generated by pooling the token embeddings together. The output layer has a basic linear transformation followed by a Softmax that accepts a token embedding from the previous transformer layer as an input and produces a probability distribution over the vocabulary's tokens.

### 4.1.2 Single-Encoder Multilingual NLU

#### 4.1.2.1 Multilingual BERT (mBERT)

The multilingual BERT (mBERT) architecture is identical to that of the original BERT. Rather than being trained only on monolingual English data with an English-derived vocabulary, it is trained on the [Wikipedia](http://Wikipedia) pages of 104 languages with a common WordPiece vocabulary. It makes no reference to the input language and lacks an explicit technique for ensuring that translation equivalent sentences have close representations. A 110k WordPiece vocabulary is shared amongst all 104 languages. To address Wikipedia's content imbalance, where for instance English Wikipedia has 120x the number of articles as Kurdish Wikipedia, minor languages were over-sampled while major languages were under-sampled. The same vocabulary enables some kind of cross-linguistic representation among other factors. Next, we briefly describe mBERT's pre-training tasks, namely multilingual Masked Language Model (mMLM) and Next Sentence Prediction (NSP).

**Masked Language Model (MLM)** This is the standard token-level unsupervised pre-training task introduced by BERT. However, in the context of multilingual transformers it is used with multiple languages pooled together with no alignment. It follows the same MLM procedure where 15% of the tokens are randomly picked then (i) with a probability of 80%, they are replaced by the \[MASK\] token, or (ii) with a probability of 10%, they are replaced with a random token, or (iii) they are kept the same with a probability of 10%. The objective of the MLM task is to predict the masked tokens using the unmasked ones on both sides of the input token sequence. Formally, let *x* be an input token sequence, and *M*[*x*] be the set of masked tokens. The MLM loss is defined as follows:

  
$$\\begin{array}{l} {\\mathcal{L}\_{MLM}^{(x)} = - \\frac{1}{|M\_{x}|}{\\sum\\limits\_{i \\in M\_{x}}l}ogP(x\_{i}|x\_{\\smallsetminus M\_{x}})} \\\\ \\end{array}$$  
(4.1)

[Fig. 4.1](#ch4.xhtml#fig4_1) illustrates the MLM task where *x* and *y* represent monolingual input sentences in different languages. Despite the fact that this task does not take into consideration any information about the multiple languages of the pooled masked input, it has shown great value in producing cross-lingual representations that are well aligned across languages. The insights section will provide more details on the factors behind this behavior.

![Figure 4.1 Illustration of multilingual MLM task \[71, 194\]. x and y are monolingual sentences in different languages that are not parallel.](images/fig4_1.jpg)

[Figure 4.1](#ch4.xhtml#b4fig4_1) Illustration of multilingual MLM task \[[71](#refbib.xhtml#refbib_71), 194\]. *x* and *y* are monolingual sentences in different languages that are not parallel.

**Next Sentence Prediction (NSP)** In the context of sentence-level pre-training tasks, NSP assists the model in learning associations between phrases \[[71](#refbib.xhtml#refbib_71)\]. It is a binary sentence pair classification problem that learns to identify consecutive sentences. For two sentences *x* and *y*, the \[CLS\] token vector representing the aggregate representation of the two sentences (*x*, *y*) is passed to the Sigmoid layer to obtain the probability of being consecutive sentences. To prepare for training, the phrase pairs are created such that fifty percent of the occurrences are consecutive and the remaining fifty percent are not consecutive. Pre-training the model at the sentence level is beneficial in downstream tasks like question answering (QA) , natural language inference (NLI), and semantic text similarity (STS), which need sentence pairs as input. Let *l* ∈ {1, 0} represents two sentences (*x*, *y*) being consecutive or not, NSP loss is defined as follows:

  
$$\\begin{array}{l} {\\mathcal{L}\_{NSP}^{(x,y)} = - logP(l|x,y)} \\\\ \\end{array}$$  
(4.2)

#### 4.1.2.2 Cross-Lingual Language Model (XLM)

Cross-Lingual Language Model (XLM) \[[146](#refbib.xhtml#refbib_146)\] is an improvement over the mBERT architecture by learning from monolingual and parallel corpora. For learning from monolingual data XLM uses the standard MLM pre-training task used by mBERT. XLM also proposes to use Causal Language Modeling (CLM) for monolingual pre-training.

**Causal Language Modeling (CLM)** CLM is the core pre-training task of classical language modeling where a model predicts the next word based on the previous words context Formally. Let *x* = {*x*[1], *x*[2], *x*[3], …, *x*[|*x*|]} represents a sequence of tokens where |*x*| represents the number of tokens in the sequence. CLM loss is defined as:

  
$$\\begin{array}{l} {L\_{CLM}^{(x)} = - \\frac{1}{|x|}{\\sum\\limits\_{i = 1}^{|x|}{\\log}}P({x\_{i}|x\_{< i}})} \\\\ \\end{array}$$  
(4.3)

where *x*[ < *i*] = *x*[1], *x*[2], *x*[3], …*x*[*i* − 1].

The main contribution of XLM is the introduction of a pre-training task that uses parallel corpora to explicitly encourage alignment of cross-lingual representations; namely Translation Language Model (TLM).

**Translation Language Model (TLM)** TLM is a variant of MLM that allows for the use of parallel corpora in cross-lingual pre-training \[[63](#refbib.xhtml#refbib_63)\]. The input to the encoder is a pair of parallel sentences (*x*, *y*). Similar to MLM, a total of *k* tokens are masked so that they might belong to either the *x* or *y* sentences. To predict a masked word in *x*, the model may depend on surrounding context in *x* or the translation *y*, and vice versa for masked tokens in *y*. This implicitly forces the encoder to acquire cross-lingual aligned representations. Essentially, if the context of masked token in *x* is insufficient, the model would pay more attention to the context in *y* to make better prediction of the masked token. [Fig. 4.2](#ch4.xhtml#fig4_2) provides an illustration of how TLM performs cross-lingual attention. To define TLM for a parallel sentence pair (*x*, *y*), let *M*[*x*] and *M*[*y*] represent the set of masked positions in both sentences, then *x*[ ∖ *M*[*x*]] and *y*[ ∖ *M*[*y*]] will represent the masked versions of *x* and *y*. TLM loss function \[[138](#refbib.xhtml#refbib_138)\] is defined as follows:

  
$$\\begin{array}{l} {\\mathcal{L}\_{TLM}^{(x,y)} = - \\frac{1}{|M\_{x}|}{\\sum\\limits\_{i \\in M\_{x}}l}ogP(x\_{i}|x\_{\\smallsetminus M\_{x}},y\_{\\smallsetminus M\_{y}}) - \\frac{1}{|M\_{y}|}{\\sum\\limits\_{i \\in M\_{y}}l}ogP(y\_{i}|x\_{\\smallsetminus M\_{x}},y\_{\\smallsetminus M\_{y}})} \\\\ \\end{array}$$  
(4.4)

![Figure 4.2 Illustration of TLM \[146, 194\] showing the attention mechanism across parallel sentences (x,y) which promotes cross-lingual alignment of the produced representations.](images/fig4_2.jpg)

[Figure 4.2](#ch4.xhtml#b4fig4_2) Illustration of TLM \[[146](#refbib.xhtml#refbib_146), [194](#refbib.xhtml#refbib_194)\] showing the attention mechanism across parallel sentences (*x*, *y*) which promotes cross-lingual alignment of the produced representations.

XLM provided extensive evidence for how the MLM and CLM pre-training tasks provide strong cross-lingual features that could be used for unsupervised machine translations and other downstream supervised cross-lingual classification tasks. Cross-lingual Language Model (XLM) also shows the strong impact of using TLM with MLM on the quality of cross-lingual representations alignment as proven by their performance on the XNLI benchmark.

#### 4.1.2.3 XLM-RoBERTa

XLM-RoBERTa (XLM-R) \[[61](#refbib.xhtml#refbib_61)\] is a multilingual transformer model based on MLM pre-training task only. XLM-R is trained on 2.5 TB of CommonCrawl data in 100 languages. XLM-R is a very important technique in the progress lineage of multilingual transformer models as it provided strong performance gains over mBERT and XLM on important downstream tasks such as sequence labeling and question answering. This is despite the fact that it does not use parallel corpora for pre-training. XLM-R follows the architectural design of XLM without using the language embeddings which allows for better handling of code-switching. The main contributions of XLM-R are achieving state-of-the-art performance with monolingual data and proving deep insights into the value of cleaner and larger training data, the size of the vocabulary, as well as the right level of hyperparameters tuning.

#### 4.1.2.4 Alternating Language Model (ALM)

**Alternating Language Model (ALM)** ALM \[[282](#refbib.xhtml#refbib_282)\] is a pre-training task for cross-lingual representations that works in the same way as the TLM pre-training task except for the nature of the input data. TLM uses parallel sentences for input, however ALM uses code-switched sentences generated from parallel sentences. In code-switched sentences, some phrases of each sentence pair are randomly swapped with the corresponding translated phrase. For a parallel sentence pair (*x*, *y*) where the source sentence *x* = {*x*[1], *x*[2], …,} and the target sentence *y* = {*y*[1], *y*[2], …,}, the input to the ALM model is a code-switched sequence *u* = {*u*[1], *u*[2], …,} composed of the pair (*x*, *y*). *u*[\[*i*, *j*\]] is assigned to either *x*[\[*a*, *b*\]] or *y*[\[*c*, *d*\]] where the constraint is that these two sequences are the translation counterpart in a parallel pair (*x*, *y*) such that 1 ≤ *a* ≤ *b* ≤ |*x*| and 1 ≤ *c* ≤ *d* ≤ |*y*|. The proportion of the source tokens *x* in the code-switched sequence *u* is *α*. In other words, if *α* = 1 then the entire input sequence is monolingual and composed of the source sentence *x*, if *α* = 0 then input sequence is just the target sentence *y*, and we get code-switched sequences by using 0 < *α* < 1.

To construct the code-switched data, a tool is used to perform word alignment between source and target sentences in the parallel corpora and a bilingual phrase table is extracted using machine translation techniques. Next, code-switched data is constructed by replacing source and target phrases according to the ratio *α*. Given that *α* decides randomly which phrases are picked from source versus target sentence, each sentence pair can produce many code-switch sequences which is very useful in overcoming the usually limited size of available parallel corpora. ALM then proceeds by using a standard MLM pre-training task on the code-switched data. Formally, for a parallel sentence pair (*x*, *y*), let *z* be the code-switched sentence generated from *x* and *y*, then ALM loss is defined as:

  
$$\\begin{array}{l} {\\mathcal{L}\_{ALM}^{(z(x,y))} = - \\frac{1}{|M|}{\\sum\\limits\_{i \\in M}l}ogP(z\_{i}|z\_{\\smallsetminus M})} \\\\ \\end{array}$$  
(4.5)

where *z*[ ∖ *M*] is the masked version of *z* and *M* is the set of masked token positions in *z*[ ∖ *M*].

[Fig. 4.3](#ch4.xhtml#fig4_3) illustrates how ALM creates a set of code-switched training data using a parallel sentence pair, which is in turn used to train a MLM transformer.

![Figure 4.3 Illustration of Alternating Language Model (ALM) \[282\] where a parallel sentence pair (x,y) is used to generate multiple code-switch examples that are used to train an MLM transformer.](images/fig4_3.jpg)

[Figure 4.3](#ch4.xhtml#b4fig4_3) Illustration of Alternating Language Model (ALM) \[[282](#refbib.xhtml#refbib_282)\] where a parallel sentence pair (*x*, *y*) is used to generate multiple code-switch examples that are used to train an MLM transformer.

#### 4.1.2.5 Unicoder

Unicoder \[[125](#refbib.xhtml#refbib_125)\] is another architecture for learning cross-lingual representations using parallel corpora. It uses the same architecture as XLM and introduces three new cross-lingual pre-training tasks; namely Cross-lingual Word Recovery (CLWR), Cross-lingual Paraphrase Classification (CLPC), and Cross-lingual Masked LM (CLMLM).

**Cross-lingual Word Recovery (CLWR)** CLWR \[[125](#refbib.xhtml#refbib_125)\] uses parallel corpora to learn word alignments between two languages. The pre-training task starts with a trainable attention matrix \[[17](#refbib.xhtml#refbib_17)\] that learns to represent the source language token embeddings in terms of the target language token embeddings. The transformation learned in the attention matrix is then provided to the cross-lingual model to learn to reconstruct the source token embedding. Formally, given a parallel sentence pair (*x*, *y*), where *x* = (*x*[1], *x*[2], …, *x*[*m*]) is a sentence with *m* words from a source language *s*, and *y* = (*y*[1], *y*[2], …, *y*[*n*]) is a sentence with *n* words from a target language *t*. CLWR starts by representing each *x*[*i*] as *x*[*i*]^(*t*) ∈ *R*^(*h*) by all word embeddings of *y\[[125](#refbib.xhtml#refbib_125)\]*:

  
$$\\begin{array}{l} {x\_{i}^{t} = {\\sum\\limits\_{j = 1}^{n}\\text{softmax}}(A\_{ij})y\_{j}^{t}} \\\\ \\end{array}$$  
(4.6)

where *x*[*i*]^(*s*) ∈ *R*^(*h*) and *y*[*j*]^(*t*) ∈ *R*^(*h*) are the representations of *x*[*i*] and *y*[*j*], respectively, and *h* denotes the representation dimension, *A* ∈ *R*^(*m* × *n*) is the attention matrix defined as:

  
$$\\begin{array}{l} {A\_{ij} = W\\lbrack{x\_{i}^{s},y\_{j}^{t},x\_{i}^{s} \\odot y\_{j}^{t}}\\rbrack} \\\\ \\end{array}$$  
(4.7)

Note that *W* ∈ *R*^(3 \* *h*) is a trainable weight matrix and ⊙ is element-wise multiplication. Unicoder then takes *X*^(*t*) = (*x*[1]^(*t*), *x*[2]^(*t*), …, *x*[*n*]^(*t*)) as input, and predicts the original word sequence *x*.

**Cross-lingual Paraphrase Classification (CLPC)** CLPC \[[125](#refbib.xhtml#refbib_125)\] introduces a different way of using parallel data by proposing a paraphrase classification pre-training task for parallel sentence pairs (*x*, *y*), where parallel sentence pairs (*x*, *y*) are the positive class and non-parallel pairs (*x*, *z*) are the negative class. The training data samples are picked using a smaller paraphrase detection model such that the for each (*x*, *y*) and (*x*, *z*) sentence pairs, *z* is chosen to be close to *x* but not equal to *y*.

**Cross-lingual Masked LM (CLMLM)** CLMLM \[[125](#refbib.xhtml#refbib_125)\] is an extension of TLM with the same cross-lingual attention scheme. However, while TLM takes in pairs of parallel sentences, CLMLM's input is created on the document level where multiple sentences from a parallel document (i.e., a full document with multiple parallel translations) are replaced with other language translations. This was inspired by some reported success on pre-training using longer monolingual text.Unicoder model is initialized with the XLM model and then pre-trained using the combined MLM, TLM, CLWR, CLPC, and CLMLM tasks and fine-tuned on XNLI and XQA benchmarks.

#### 4.1.2.6 Information-Theoretic Cross-Lingual Model (INFOXLM)

Information-Theoretic Cross-Lingual Model (INFOXLM) \[[47](#refbib.xhtml#refbib_47)\] approaches the cross-lingual representation alignment problem from an information theoretic perspective, where it shows how multilingual pre-training tasks can in fact be viewed as maximizing the mutual information between multilingual contexts on different granularity. For instance, InfoXLM shows that the multilingual masked language model (mMLM) pre-training task essentially maximizes the mutual information between masked tokens and their context within the same language. On the other hand, anchor tokens across languages motivate cross-lingual contexts to be closely correlated. TLM also has an information theoretic explanation where it is shown to maximize the mutual information between masked tokens and parallel language contexts, which serves as an implicit cross-lingual representation alignment mechanism. Using the provided information theoretic framework, InfoXLM proposes a new cross-lingual pre-training task based on contrastive learning, namely Cross-lingual Contrastive Learning.

**Cross-lingual Contrastive Learning (XLCO)** XLCO \[[47](#refbib.xhtml#refbib_47)\] proposes an information theoretic approach to produce cross-lingual representations using parallel corpora. XLCO encourages a transformer encoder to maximize the mutual information between representations of parallel sentences in comparison to non-parallel sentences, thus performing contrastive learning. TLM is shown, within the information theoretic framework, to maximize token-sequence mutual information. On the other hand, XLCO maximizes sequence-level mutual information between parallel sentences. Let (*x*[*i*], *y*[*i*]) be a parallel sentence pair, where *y*[*i*] is a translation of *x*[*i*], and {*y*[*j*]}[*j* = 1, *j* ≠ *i*]^(*N*) is the set of sentences of the same language as *y*[*i*] but not a translation of *x*[*i*]. XLCO maximizes the information content between *x*[*i*] and *y*[*i*] using the InfoNCE \[[251](#refbib.xhtml#refbib_251)\] based loss function defined as:

  
$$\\begin{array}{l} {\\mathcal{L}\_{XLCO}^{(x,\_{i},y\_{i})} = - \\log\\frac{\\exp(f{(x\_{i})}^{\\top}f(y\_{i}))}{{\\sum\\limits\_{j = 1}^{N}{\\exp}}(f{(x\_{i})}^{\\top}f(y\_{j})}} \\\\ \\end{array}$$  
(4.8)

where *f*(*x*[*i*]) and *f*(*y*[*i*]) are the transformer encoder representations of sentences *x*[*i*] and *y*[*i*], respectively. For negative sampling XLCO does not sample explicitly from {*y*[*j*]}[*j* = 1, *j* ≠ *i*]^(*N*) but rather uses mixup contrast \[[47](#refbib.xhtml#refbib_47)\] and momentum \[[104](#refbib.xhtml#refbib_104)\] to construct harder negative samples.

INFOXLM is initialized with the XLM-R model parameters and then pre-trained using the combined mMLM, TLM, and XLCO tasks formulated as mutual information maximization tasks; monolingual token-sequence mutual information (MMLM), cross-lingual token-sequence mutual information (TLM), and cross-lingual sequence-level mutual information (XLCO).

#### 4.1.2.7 Aligned Multilingual Bidirectional EncodeR (AMBER)

Aligned Multilingual Bidirectional EncodeR (AMBER) \[[121](#refbib.xhtml#refbib_121)\] is a technique that creates cross-lingual representations using parallel data with word-level and sentence-level alignment pre-training tasks, namely Cross-lingual Word Alignment (CLWA) and Cross-lingual Sentence Alignment (CLSA) tasks.

**Cross-lingual Word Alignment (CLWA)** Similar to CLWR, CLWA \[[121](#refbib.xhtml#refbib_121)\] also aims to learn word alignments between different languages using parallel corpora. CLWA uses two different attention masks as inputs to a transformer model. After training, two attention matrices are obtained in the top transformer layer, namely source-to-target attention *A*[*x* → *y*] and target-to-source attention *A*[*y* → *x*]. Given that *A*[*x* → *y*] measures the alignment of the source-to-target transformation, and vice versa for *A*[*y* → *x*], it is desirable to have similar alignments for words using either *A*[*x* → *y*] or *A*[*y* → *x*] attention matrices. To that end the model is encouraged to minimize the distance between *A*[*x* → *y*] and *A*[*y* → *x*] during training.

**Cross-lingual Sentence Alignment (CLSA)** CLSA \[[121](#refbib.xhtml#refbib_121)\] is designed to enforce the alignment of sentence representations across languages using parallel data. Let ℳ and 𝒫 be the monolingual and parallel data, respectively. For each parallel sentence pair (*x*, *y*), distinct sentence embeddings for both *x* and *y* are generated separately, namely *c*[*x*] and *c*[*y*], respectively. *c*[*x*] and *c*[*y*] are obtained by averaging the last layer's embeddings of the encoder. The embedding alignment takes place by encouraging the model to predict the correct translation *y* for an input sentence *x* by using the following loss function:

  
$$\\begin{array}{l} {\\mathcal{L}\_{CLSA}^{(x,y)} = - \\log\\frac{e^{\\mathbf{c}\_{x}^{T}\\mathbf{c}\_{y}}}{\\sum\\limits\_{y^{\\prime} \\in \\mathcal{M} \\cup \\mathcal{P}}e^{\\mathbf{c}\_{x}^{T}\\mathbf{c}\_{y^{\\prime}}}}} \\\\ \\end{array}$$  
(4.9)

where *y*^′ in ℒ[*C**L**S**A*]^((*x*, *y*)) can be any sentence and with no language restriction.

AMBER is trained using a combination of MLM, TLM, CLWA, CLSA tasks and is evaluated on the XTREME benchmark where it outperformed XLM-R and Unicoder.

#### 4.1.2.8 ERNIE-M

Many techniques have shown the value of using parallel and monolingual corpora to get better aligned cross-lingual representations. However, parallel corpora are always limited in size relative to monolingual data, limiting the possible progress unless we collect sizable parallel corpora. ERNIE-M \[[194](#refbib.xhtml#refbib_194)\] uses large monolingual corpora and limited parallel corpora to produce cross-lingual representations. To enhance produced representations, ERNIE-M generates pseudo-parallel sentences using the large available monolingual corpora and then uses them along with the parallel data to improve the alignment of cross-lingual representations. ERNIE-M proposes two pre-training tasks, Cross-Attention masked Language Modeling (CAMLM) and Back-Translation Masked Language Modeling (BTMLM).

**Cross-attention Masked LM (CAMLM)** Cross-attention Masked LM (CAMLM) \[[194](#refbib.xhtml#refbib_194)\] is another parallel corpora pre-training task that is closely related to TLM. As described earlier, for a given parallel sentence pair (*x*, *y*), a masked token within *x* has access and can potentially attend to the context of *x* and the context of *y*, and the same applies to a masked token in *y*. On the other hand, CAMLM restricts TLM by only keeping access to the corresponding parallel sentence. Therefore, a masked token in *x* can only use *y* context for prediction, and vice versa for *y*. Prohibiting attending to the context of the same sentence as the masked token forces the algorithm to learn the representation in the parallel language. Otherwise, the algorithm might take the easier path and leans more towards using the same sentence of the masked token to make a prediction. Using the same setup in TLM, where for a sentence pair (*x*, *y*), let *M*[*x*] and *M*[*y*] represent the set of masked positions in both sentences, then *x*[ ∖ *M*[*x*]] and *y*[ ∖ *M*[*y*]] will represent the masked versions of *x* and *y*. The loss function for CAMLM is defined as follows:

  
$$\\begin{array}{l} {\\mathcal{L}\_{CAMLM}^{(x,y)} = - \\frac{1}{|M\_{x}|}{\\sum\\limits\_{i \\in M\_{x}}l}ogP(x\_{i}|y\_{\\smallsetminus M\_{y}}) - \\frac{1}{|M\_{y}|}{\\sum\\limits\_{i \\in M\_{y}}l}ogP(y\_{i}|x\_{\\smallsetminus M\_{x}})} \\\\ \\end{array}$$  
(4.10)

[Fig. 4.4](#ch4.xhtml#fig4_4) illustrates the CAMLM cross-lingual attention. As depicted, token *h*2 attends to tokens in sentence *y* and not *x*, and tokens *h*5 and *h*6 attend only to tokens in sentence *x* and not *y*.

![Figure 4.4 Cross-attention Masked LM (CAMLM) where a masked token can only attend to the opposite sentences for prediction \[194\].](images/fig4_4.jpg)

[Figure 4.4](#ch4.xhtml#b4fig4_4) Cross-attention Masked LM (CAMLM) where a masked token can only attend to the opposite sentences for prediction \[[194](#refbib.xhtml#refbib_194)\].

**Back Translation Masked Language Modeling (BTMLM)** BTMLM \[[194](#refbib.xhtml#refbib_194)\] leverages back translation \[[222](#refbib.xhtml#refbib_222)\] to circumvent the issue of lack of parallel corpora for learning cross-lingual representations. It consists of two steps; the first step generates pseudo-parallel data from a given monolingual corpus. ERNIE-M \[[194](#refbib.xhtml#refbib_194)\] constructs pseudo-parallel sentences by first pre-training the model using CAMLM and then adding placeholder masks to the end of the original monolingual sentence to show the location and language that the model should generate. The second step masks the tokens in the original monolingual sentence, then concatenates it with the created pseudo-parallel sentence. Finally, the model should predict the masked tokens. [Fig. 4.5](#ch4.xhtml#fig4_5) shows the two steps of BTMLM.

![Figure 4.5 Illustration of BTMLM \[194\] pre-training task. The first step on the left is where a pre-trained CAMLM is used to generate pseudo-parallel sentences. The second step on the right is where the generated pseudo-parallel sentences are then used to further train the CAMLM.](images/fig4_5.jpg)

[Figure 4.5](#ch4.xhtml#b4fig4_5) Illustration of BTMLM \[[194](#refbib.xhtml#refbib_194)\] pre-training task. The first step on the left is where a pre-trained CAMLM is used to generate pseudo-parallel sentences. The second step on the right is where the generated pseudo-parallel sentences are then used to further train the CAMLM.

Due to their superior performance in XLM architecture, the mMLM and TLM pre-training tasks are employed as part of training ERNIE-M as well. ERNIE-M is trained with monolingual and parallel corpora with 96 languages and is initialized with XLM-R weights. ERNIE-M has shown state-of-the-art performance on a diverse set of downstream tasks including NER, Cross-lingual Question Answering, Cross-lingual Paraphrase Identification, and Cross-lingual Sentence Retrieval.

#### 4.1.2.9 Hierarchical Contrastive Learning (HICTL)

Hierarchical Contrastive Learning (HICTL) \[[266](#refbib.xhtml#refbib_266)\] is another cross-lingual pre-training task that uses InfoNCE \[[251](#refbib.xhtml#refbib_251)\] based loss functions. While XLCO is sentence-based, HICTL provides both sentence and word-level cross-lingual representations.

Sentence level representations are constructed in the same manner as XCLO except for the negative sampling where instead of collecting samples from {*y*[*j*]}[*j* = 1, *j* ≠ *i*]^(*N*) smoothed linear interpolation \[[31](#refbib.xhtml#refbib_31), [300](#refbib.xhtml#refbib_300)\] between sentence representations is used to construct hard negative samples.

For world-level representations, the contrastive loss similarity score is computed between a parallel sentence (*x*[*i*], *y*[*i*]) \[CLS\] token representation and other words representations. For each parallel sentence pair input (*x*[*i*], *y*[*i*]) , a bag of words 𝒲 is maintained, where all words in 𝒲 are considered positive samples and all other words in the vocabulary are negative samples. For efficient negative words sampling, HICTL does not sample from the entire vocabulary but rather constructs a set of negative words that very close to parallel sentence (*x*[*i*], *y*[*i*]) \[CLS\] token representation.

### 4.1.3 Dual-Encoder Multilingual NLU

#### 4.1.3.1 Language-agnostic BERT Sentence Embedding (LaBSE)

Language-agnostic BERT Sentence Embedding (LaBSE) \[[88](#refbib.xhtml#refbib_88)\] is an architecture for training cross-lingual sentence representations which combines Masked Language Model (MLM) and Translation Language Model (TLM) pre-training tasks from XLM \[[146](#refbib.xhtml#refbib_146)\] with a translation ranking task using bi-directional dual-encoders with additive margin softmax loss\[[283](#refbib.xhtml#refbib_283)\]. The dual-encoders, as shown in [Fig. 4.6](#ch4.xhtml#fig4_6), consist of two paired mBERT encoders. The \[CLS\] token sentence representation from both encoders are fed to a scoring function. [Fig. 4.6](#ch4.xhtml#fig4_6) provide an illustration of the LaBSE architecture.

![Figure 4.6 Illustration of Language-agnostic BERT Sentence Embedding (LaBSE) architecture \[88\].](images/fig4_6.jpg)

[Figure 4.6](#ch4.xhtml#b4fig4_6) Illustration of Language-agnostic BERT Sentence Embedding (LaBSE) architecture \[[88](#refbib.xhtml#refbib_88)\].

**Bidirectional Dual Encoder with Additive Margin Softmax** The dual-encoder architecture \[[283](#refbib.xhtml#refbib_283)\] has proven to be very effective for ranking tasks such as the translation retrieval task employed by LaBSE for cross-lingual embedding. Formally, for a parallel sentence pair (*x*[*i*], *y*[*i*]), translation retrieval is a ranking problem that aims to place *y*[*i*], the true translation of *x*[*i*], higher than all sentences in the space of translations 𝒴. *P*(*y*[*i*] ∣ *x*[*i*]) is formulated as:

  
$$\\begin{array}{l} {P({y\_{i}\\mid x\_{i}}) = \\frac{e^{\\phi({x\_{i},y\_{i}})}}{\\sum\\limits\_{\\overline{y} \\in \\mathcal{Y}}e^{\\phi({x\_{i},\\overline{y}})}}} \\\\ \\end{array}$$  
(4.11)

where *ϕ* is the scoring function of the similarity between the representations of *x*[*i*] and *y*[*i*]

During training *P*(*y*[*i*] ∣ *x*[*i*]) is approximated by sampling negatives, *y*[*n*], from translation pairs in the same batch:

  
$$\\begin{array}{l} {P\_{\\text{approx~}}({y\_{i}\\mid x\_{i}}) = \\frac{e^{\\phi({x\_{i},y\_{i}})}}{e^{\\phi({x\_{i},y\_{i}})} + {\\sum\\limits\_{n = 1,n \\neq i}^{N}e^{\\phi({x\_{i},y\_{n}})}}}} \\\\ \\end{array}$$  
(4.12)

Therefore, for parallel source and target pairs (*x*[*i*], *y*[*i*]), the model can be optimized using the log-likelihood objective \[[283](#refbib.xhtml#refbib_283)\]:

  
$$\\begin{array}{l} {\\mathcal{L}\_{s} = - \\frac{1}{N}{\\sum\\limits\_{i = 1}^{N}{\\log}}\\frac{e^{\\phi({x\_{i},y\_{i}})}}{e^{\\phi({x\_{i},y\_{i}})} + {\\sum\\limits\_{n = 1,n \\neq i}^{N}e^{\\phi({x\_{i},y\_{n}})}}}} \\\\ \\end{array}$$  
(4.13)

For each *x*[*i*], the loss ℒ[*s*] aims to identify the correct *y*[*i*]. This means that using ℒ[*s*] will result in an asymmetric relationship between *x*[*i*] and *y*[*i*] representations. To overcome this issue, Yand et al. \[[283](#refbib.xhtml#refbib_283)\] introduced the bidirectional learning objective, ${\\overline{\\mathcal{L}}}\_{s}$ that explicitly optimizes both forward and backward ranking of the parallel pair (*x*[*i*], *y*[*i*]):

  
$$\\begin{matrix} {{\\mathcal{L}^{\\prime}}\_{s} = - \\frac{1}{N}{\\sum\\limits\_{i = 1}^{N}\\frac{e\\phi(yi,xi)}{e\\phi(yi,xi) + \\sum\_{n = 1,n \\neq i}^{N}e^{\\phi}(yi.x\_{n})}}} \\\\ {{\\overline{\\mathcal{L}}}\_{\\mathcal{S}} = \\mathcal{L}\_{\\mathcal{S}} + {\\mathcal{L}^{\\prime}}\_{\\mathcal{S}}} \\\\ \\end{matrix}$$  
(4.14)

For added separation between the correct translations the closest non-translations that are very close, the scoring function *ϕ* is extended with additive margin softmax, which introduces a margin *m* around the positive parallel pairs (*x*[*i*], *y*[*i*]).

  
$$\\phi^{\\prime}(x\_{i},y\_{j}) = \\begin{cases} {\\phi(x\_{i},y\_{j}) - m} & {~if~i = j} \\\\ {\\phi(x\_{i},y\_{j})} & {~if~i \\neq j} \\\\ \\end{cases}$$  
(4.15)

Applying *ϕ*^′(*x*[*i*], *y*[*j*]) to the bidirectional loss ${\\overline{\\mathcal{L}}}\_{s}$, the additive margin bidirectional loss becomes as follows \[[283](#refbib.xhtml#refbib_283)\]:

  
$$\\begin{array}{ll} {\\mathcal{L}\_{ams} = - \\frac{1}{N}} & {\\sum\\limits\_{i = 1}^{N}\\frac{e^{\\phi({x\_{i},y\_{i}}) - m}}{e^{\\phi({x\_{i},y\_{i}}) - m} + {\\sum\\limits\_{n = 1,n \\neq i}^{N}e^{\\phi({x\_{i},y\_{n}})}}}} \\\\ \\ & {{\\overline{\\mathcal{L}}}\_{ams} = \\mathcal{L}\_{ams} + \\mathcal{L}\_{ams}^{\\prime}} \\\\ \\end{array}$$  
(4.16)

As mentioned earlier, LaBSE pre-trains its BERT based encoders with Masked Language Model (MLM) and Translation Language Model (TLM) pre-training tasks using monolingual and parallel corpora, respectively. LaBSE trains transformer encoders using a three-stage progressive stacking approach. For a *L* layer encoder, it first learning a model of *fracL*4 layers, then *fracL*2 layers, and lastly all *L* layers. During successive training steps, the parameters of the earlier steps models are copied to the subsequent ones.

#### 4.1.3.2 Multilingual Universal Sentence Encoders (mUSE)

Multilingual Universal Sentence Encoders (mUSE) \[[49](#refbib.xhtml#refbib_49), [284](#refbib.xhtml#refbib_284)\] proposes an approach for cross-lingual sentence embedding learning by combining multitask learning of monolingual sentence representations, and dual-encoders for multilingual sentence embeddings learning for parallel text retrieval. By combining the two approaches, mUSE transfers the strong performance learned on monolingual tasks to zero-shot learning in other languages. Basically, for a certain language pair, source and target language, the model uses a multitask architecture to learn across (i) source language monolingual tasks, (ii) monolingual target language tasks, and (iii) a source-to-target language translation task that serves as a bridging task to encourage cross-lingual representation alignment across all the trained tasks. [Fig. 4.7](#ch4.xhtml#fig4_7) provides an illustration of the architecture for QA, NLI and the bridging translation tasks.

![Figure 4.7 Illustration of mUSE architecture for QA, NLI and the bridging translation tasks \[284\].](images/fig4_7.jpg)

[Figure 4.7](#ch4.xhtml#b4fig4_7) Illustration of mUSE architecture for QA, NLI and the bridging translation tasks \[[284](#refbib.xhtml#refbib_284)\].

mUSE uses dual-encoders to perform multitask learning on tasks that can be represented as ranking input-response sentence pairs. Some tasks fall naturally within this framework such as QA and translation tasks. Other tasks might need a special reformulation such as NLI. Input-response ranking can be formally described as follows: For an input-response pair (*s*[*i*]^(*I*), *s*[*i*]^(*R*)), the goal is to get *s*[*i*]^(*R*) to higher than all possible responses *s*[*j*]^(*R*) ∈ 𝒮^(*R*). In other words, the conditional probability *P*(*s*[*i*]^(*R*) ∣ *s*[*i*]^(*I*)) should be defined as:

  
$$\\begin{array}{ll} {P({s\_{i}^{R}\\mid s\_{i}^{I}})} & {= \\frac{e^{\\phi({s\_{i}^{I},s\_{i}^{R}})}}{\\sum\\limits\_{s\_{j}^{R} \\in \\mathcal{S}^{R}}e^{\\phi({s\_{i}^{R},s\_{j}^{R}})}}} \\\\ {\\phi({s\_{i}^{I},s\_{j}^{R}})} & {= g^{I}{(s\_{i}^{I})}^{\\top}g^{R}(s\_{j}^{R})} \\\\ \\end{array}$$  
(4.17)

where *g*^(*I*) is the input sentence encoding function and *g*^(*R*) is response sentence encoding function, *g*^(*I*) and *g*^(*R*) make up the dual-encoder. Both *g*^(*I*) and *g*^(*R*) are implemented using transformers and are trained with the log-likelihood loss function, $\\overset{\\sim}{P}(s\_{i}^{R} \\mid s\_{i}^{I})$, for each task.

As illustrated in [Fig. 4.7](#ch4.xhtml#fig4_7), mUSE uses a single shared encoder supporting multiple downstream tasks. The training tasks include: QA prediction task, NLI task, and translation ranking. Task-specific layers for the QA and NLI tasks are added after the shared encoder to help accommodating representational needs for each task.

### 4.1.4 Multilingual Natural Language Generation (Multilingual NLG)

All cross-lingual pre-training tasks discussed in the previous section are used for Natural Language Understanding (NLU) tasks only. This section discusses a few of the pre-training tasks used by generative multilingual models such as MASS \[[231](#refbib.xhtml#refbib_231)\], BART \[[155](#refbib.xhtml#refbib_155)\], mBART \[[169](#refbib.xhtml#refbib_169)\], and XNLG \[[46](#refbib.xhtml#refbib_46)\].

**Sequence-to-Sequence LM (Seq2SeqLM)** As discussed earlier, Masked Language Model (MLM) is handled as a token-level classification problem over the masked tokens, in which the original words are predicted by feeding the masked token vectors to a Softmax layer over the vocabulary. MLM also is used to pre-train encoder-only transformer architectures which are then used for NLU tasks. Seq2SeqLM extends conventional MLM to pre-train encoder-decoder transformer models such as T5\[[205](#refbib.xhtml#refbib_205)\], mT5 \[[281](#refbib.xhtml#refbib_281)\], and MASS \[[231](#refbib.xhtml#refbib_231)\]. While the context of MLM includes all tokens in the input sequence, the context of Seq2SeqLM includes all tokens in the input masked sequence and the left side tokens in the predicted target sequence. With the encoder's masked sequence as input, the decoder predicts the masked words sequentially from left to right. This allows transformer architectures pre-trained with Seq2SeqLM to be used for NLG tasks. For a given input sequence of tokens *x*, let *x̂* be the masked version of *x*, that is *x* with masked n-gram span. With *l*[*s*] defined as the length of masked n-gram span, then Seq2SeqLM loss is defined as

  
$$\\begin{array}{l} {\\mathcal{L}\_{Seq2SeqLM}^{(x)} = - \\frac{1}{l\_{s}}{\\sum\\limits\_{s = i}^{j}l}ogP(x\_{s}|\\hat{x},x\_{i:s - 1})} \\\\ \\end{array}$$  
(4.18)

**Denoising Auto-Encoder (DAE)** Similar to Seq2SeqLM, DAE \[[155](#refbib.xhtml#refbib_155), [169](#refbib.xhtml#refbib_169)\] is a pre-training task for encoder-decoder transformer architectures. While Seq2SeqLM is based on predicting masked tokens, DAE does not mask textual elements but rather corrupts them and then reconstructs the original values. DAE corrupts text at the token level by token deletion and token masking, at the sentence level by sentence permutation, at a text span level by text infilling, or at the document level by document rotation. DAE is more sample efficient than Seq2SeqLM since it provides more signals for model training. DAE generates more training signal since it reconstructs the complete original text, while Seq2SeqLM reconstructs just the masked tokens. BART \[[155](#refbib.xhtml#refbib_155)\] encodes corrupted input sequences using a bidirectional encoder and reconstructs the original text using a left-to-right decoder. Similar to Seq2SeqLM definition, for a given input text *x* , let *x̂* be the corrupted version of *x*, then DAE loss is defined as

  
$$\\begin{array}{l} {\\mathcal{L}\_{DAE}^{(x)} = - \\frac{1}{|x|}{\\sum\\limits\_{i = 1}^{|x|}l}ogP(x\_{i}|\\hat{x},x\_{< i})} \\\\ \\end{array}$$  
(4.19)

**Cross-lingual Auto-Encoding (XAE)** While DAE is trained on a variety of languages, the encoding input and decoding output are always identical. As a result, models detect improper correlations between linguistic symbols and produced phrases. In other words, models may disregard the provided language symbols and create sentences directly in the input language. XNLG \[[46](#refbib.xhtml#refbib_46)\] offers the cross-lingual auto-encoding (XAE) job to overcome this problem. Unlike DAE, XAE's encoding input and decoding output are in distinct languages, comparable to machine translation. Additionally, XNLG does a two-stage optimization of parameters. It initially trains the encoder using MLM and TLM jobs. Then, in the second step, it repairs the encoder and trains the decoder using the DAE and XAE tasks. This method effectively pre-trains all parameters, and also bridges the gap between MLM pre-training and autoregressive decoding fine-tuning.

## 4.2 MULTILINGUAL DATA

### 4.2.1 Pre-Training Data

Multilingual Language Models (mLMs) use different sources of data during the pre-training stage. More specifically, large monolingual corpora are commonly used in individual languages and parallel corpora are used between some languages. The source of the monolingual corpora varies for the different existent mLMs. For example, mBERT \[[72](#refbib.xhtml#refbib_72)\] uses [Wikipedia](http://Wikipedia) for pre-training. Whereas, in \[[61](#refbib.xhtml#refbib_61)\], Conneau et al. used a much larger common-crawl corpus to train XML-R. Other models use custom crawled data. For example, IndicBERT \[[137](#refbib.xhtml#refbib_137)\] is trained on custom crawled data in Indian languages. [Table 4.1](#ch4.xhtml#tbl4_1) provides a summary for the datasets used for pre-training the different mLMs.

Some models such as IndicBERT \[[137](#refbib.xhtml#refbib_137)\] and MuRIL \[[141](#refbib.xhtml#refbib_141)\] are designed to support only small set of languages. Other mLMs such as XLM-R are massively multilingual and can support  ∼ 100 languages. Managing large number of languages poses a challenge of the possible imbalance between the amount of data used for pre-training for the different languages. For example, when using [Wikipedia](http://Wikipedia) and CommonCrawl for pre-training, it is obvious that the number of available articles in English is much higher than other languages such as Persian or Urdu. Similarly, the amount of parallel data available for pairs of languages differ highly depending of the popularity of such languages. To overcome these challenges, most mLMs use exponentially smoothed weighting of the data while creating the pre-training data. This weighting prevents the low resource languages from being under represented. More specifically, if *m*% of the total pre-training data belongs to language *i*, then the probability of this language is $p\_{i} = \\frac{k}{100}$. Each probability is then modulated by an exponential factor *α*, then the resulting values are normalized to provide the final probability distribution over the languages. This probability distribution is used to the sample the pre-training data from the different languages. Therefore, low-resource languages will be over sampled while high-resource languages will be under sampled. Such process guarantees the use of a reasonable set of vocabulary (while training the WordPiece \[[220](#refbib.xhtml#refbib_220)\] or SentencePiece model \[[144](#refbib.xhtml#refbib_144)\]) in the low resource languages. [Table 4.1](#ch4.xhtml#tbl4_1) summarizes the number of languages supported by different mLMs and the total vocabulary used by them. Typically, mLMs which support more languages have a larger vocabulary.

### 4.2.2 Multilingual Benchmarks

The most often used methods for evaluating mLMs is cross-lingual performance on downstream tasks, which requires fine-tuning the model using task-specific data from a high-resource language such as English and evaluating it on other languages. XGLUE \[[160](#refbib.xhtml#refbib_160)\], XTREME \[[122](#refbib.xhtml#refbib_122)\], XTREME-R \[[216](#refbib.xhtml#refbib_216)\] are some of the state-of-the-art cross-lingual learning benchmarks. As shown in [Table 4.2](#ch4.xhtml#tbl4_2), these benchmarks provide training/evaluation data for a broad range of tasks and languages. These tasks can be categorized into: classification, structure prediction, question answering, and semantic retrieval.

[TABLE 4.2](#ch4.xhtml#b4tbl4_2) Multilingual language models benchmarks categorized by NLP task \[[74](#refbib.xhtml#refbib_74)\]

  
| **Task** || Corpus || Train || Dev || Test || Test Sets || #Langs. || Task || Metric || Domain || Benchmark |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  || XNLI || 392,702 || 2,490 || 5,010 || Translations || 15 || NLI || Acc. || Misc. || XT, XTR, XG |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  || PAWS-X || 49,401 || 2,000 || 2,000 || Translations || 7 || Paraphrase || Acc. || Wiki / Quora || XT, XTR, XG |
|  || XCOPA || 33,410+400 || 100 || 500 || Translations || 11 || Reasoning || Acc. || Misc || XTR |
| Classification || NC || 100k || 10k || 10k || \- || 5 || Sent. Labeling || Acc. || News || XG |
|  || QADSM || 100k || 10k || 10k || \- || 3 || Sent. Relevance || Acc. || Bing || XG |
|  || WPR || 100k || 10k || 10k || \- || 7 || Sent. Relevance || nDCG || Bing || XG |
|  || QAM || 100k || 10k || 10k || \- || 7 || Sent. Relevance || Acc. || Bing || XG |
|  || UD-POS || 21,253 || 3,974 || 47-20,436 || Ind. annot. || 37(104) || POS || F1 || Misc. || XT, XTR, XG |
| Struct. Pred || WikiANN-NER || 20,000 || 10,000 || 1,000-10,000 || Ind. annot. || 47(176) || NER || F1 || [Wikipedia](http://Wikipedia) || XT, XTR |
|  || NER || 15k || 2.8k || 3.4k || \- || 4 || NER || F1 || News || XG |
|  || XQuAD || 87,599 || 34,736 || 1,190 || Translations || 11 || Span Extraction || F1/EM || [Wikipedia](http://Wikipedia) || XT, XTR |
| QA || MLQA ||  ||  || 4,517-11,590 || Translations || 7 || Span Extraction || F1/EM || [Wikipedia](http://Wikipedia) || XT, XTR |
|  || TyDiQA-GoldP || 3,696 || 634 || 323-2,719 || Ind. annot. || 9 || Span Extraction || F1/EM || [Wikipedia](http://Wikipedia) || XT, XTR |
| Retrieval || BUCC || \- || \- || 1,896-14,330 || \- || 5 || Sent. Retrieval || F1 || Wiki / News || XT |
|  || Tatoeba || \- || \- || 1,000 || \- || 33(122) || Sent. Retrieval || Acc. || Misc. || XT |
|  || Mewsli-X || 116,903 || 10,252 || 428-1,482 || ind. annot. || 11(50) || Lang. agn. retrieval || mAP@20 || News || XTR |
|  || LAReQA XQuAD-R || 87,599 || 10,570 || 1,190 || translations || 11 || Lang. agn. retrieval || mAP@20 || [Wikipedia](http://Wikipedia) || XTR |

#### 4.2.2.1 Classification

For classification, the downstream task is to categorize an input consisting of a single sentence or a pair of sentences into one of *k* classes. One example is the problem of Natural Language Inference (NLI), which requires the input to be a pair of phrases and the output to be one of three classes: implies, neutral, or contradicts. XNLI \[[64](#refbib.xhtml#refbib_64)\], PAWS-X \[[285](#refbib.xhtml#refbib_285)\], XCOPA \[[200](#refbib.xhtml#refbib_200)\], NC \[[160](#refbib.xhtml#refbib_160)\], QADSM \[[160](#refbib.xhtml#refbib_160)\], WPR \[[160](#refbib.xhtml#refbib_160)\], and QAM \[[160](#refbib.xhtml#refbib_160)\] are some of the prominent cross-lingual text classification datasets used to evaluate mLMs.

#### 4.2.2.2 Structure prediction

The task is to predict a label for each word in an input sentence. Two often performed tasks are Part-of-Speech (POS) tagging and Named Entity Recognition (NER). The WikiANN-NER \[[193](#refbib.xhtml#refbib_193)\], CoNLL 2002 \[[246](#refbib.xhtml#refbib_246)\] and CoNLL 2003 \[[247](#refbib.xhtml#refbib_247)\] shared task datasets are popular for NER, and the Universal Dependencies dataset \[[192](#refbib.xhtml#refbib_192)\] is used for POS tagging.

#### 4.2.2.3 Question answering

QA task involves extracting a response span from a context and a question. Typically, training data is only accessible in English, but assessment sets are available in a variety of languages. XQuAD \[[9](#refbib.xhtml#refbib_9)\], MLQA \[[156](#refbib.xhtml#refbib_156)\], and TyDiQA-GoldP \[[56](#refbib.xhtml#refbib_56)\] datasets are often used for QA evaluation.

#### 4.2.2.4 Semantic retrieval

Semantic retrieval is concerned with finding a matched sentence in the target language from a collection of sentences given a sentence in the source language. This task is evaluated using the following datasets: BUCC \[[305](#refbib.xhtml#refbib_305)\], Tateoba \[[11](#refbib.xhtml#refbib_11)\], Mewsli-X \[[216](#refbib.xhtml#refbib_216)\], and LAReQA XQuAD-R \[[215](#refbib.xhtml#refbib_215)\]. Mewsli-X and LAReQA XQuAD-R are believed to be more challenging since they involves matching sentence recovery in the target language from a pool of multilingual sentences.

## 4.3 MULTILINGUAL TRANSFER LEARNING INSIGHTS

### 4.3.1 Zero-Shot Cross-Lingual Learning

One of the ultimate goals of multilingual transfer learning is to create mLMs with zero-shot cross-lingual performance commensurate with supervised monolingual models. The standard workflow to create a zero-shot cross-lingual model entails using many languages to pre-train a mLM, where the mLM learns cross-lingual representations. The model is then fine-tuned with a task-specific supervised dataset from a source language. Finally, the fine-tuned model is then used to perform inference on the same task from multiple different target languages. Transformers has shown remarkable progress in cross-lingual transfer learning, especially when it comes to zero-shot learning. The details of how transformers perform cross-lingual transfer learning is still an active research area. This section discusses the active areas of research to understand the main factors affecting cross-lingual transfer learning \[[74](#refbib.xhtml#refbib_74)\]. The discussed factors include: (i) data related factors, (ii) model architecture factors, and (iii) training tasks factors.

#### 4.3.1.1 Data factors

**Shared Vocabulary** Prior to training a mLM, text from all languages is tokenized using a WordPiece \[[220](#refbib.xhtml#refbib_220)\] or SentencePiece \[[144](#refbib.xhtml#refbib_144)\] models. The main concept is to tokenize each word into its most often occurring subwords. The model's vocabulary is then composed of all of these subwords recognized across all languages. This combined tokenization assures that subwords are shared across a large number of closely related or even distant languages. Thus, if a subword that exists in the target language's test set also appears in the source language's training set, some model performance may be transmitted through this common vocabulary. The relationship between cross-lingual zero-shot transferability and the size of vocabulary overlap between languages has been examined in \[[199](#refbib.xhtml#refbib_199)\] and \[[271](#refbib.xhtml#refbib_271)\], where strong positive correlation was found and the positive effect on downstream tasks has been shown to be consistent across several diverse areas including NER \[[246](#refbib.xhtml#refbib_246), [247](#refbib.xhtml#refbib_247)\], POS \[[192](#refbib.xhtml#refbib_192)\], XNLI \[[64](#refbib.xhtml#refbib_64)\], MLDoc \[[221](#refbib.xhtml#refbib_221)\], and Dependency parsing \[[192](#refbib.xhtml#refbib_192)\]. These observations are intuitive and provide some explanation for cross-lingual representation alignment when performing multilingual training using monolingual corpora. However, this area of research is still new and additional evidence is still being examined to validate these observations. For instance, Karthikeyan et al. \[[135](#refbib.xhtml#refbib_135)\] synthetically reduced the vocabulary overlap to zero, however the observed performance drop in cross-lingual zero-shot learning was minimal, which undermines the observed effect of vocabulary overlapping has on cross-lingual zero-shot transfer learning. Another work \[[10](#refbib.xhtml#refbib_10)\] shows that even if there's no vocabulary overlap, cross-lingual transfer learning still takes place by properly fine-tuning all transformer layers except for the input embedding layer.

**Pre-training Data Size** The effect of pre-training data size on cross-lingual has been evaluated in \[[165](#refbib.xhtml#refbib_165)\] which demonstrates that when mBERT is pre-trained on big corpora, cross-lingual transfer is improved. Also Lauscher et al. \[[148](#refbib.xhtml#refbib_148)\] show that the performance of zero-shot transfer is strongly correlated with the quantity of data in the target language utilized to pre-train the mLM for higher level tasks such as XNLI and XQuAD. There is also a positive connection for lower level tasks like as POS, dependency parsing, and NER, although it is not as strong as the association for XNLI and XQuAD.

**Using Parallel Corpora** While mLMs perform well even when not specifically trained with cross-lingual signals, it is intuitive that purposeful training with such signals should boost performance. In fact, XLMs in \[[63](#refbib.xhtml#refbib_63)\] and InfoXLM in \[[47](#refbib.xhtml#refbib_47)\] demonstrate that using parallel corpora in conjunction with the TLM pre-training task improves performance. If no parallel corpus is available, \[[79](#refbib.xhtml#refbib_79)\] argue that training mLMs using similar corpora (such as [Wikipedia](http://Wikipedia) or CommonCrawl) is preferable than utilizing corpora from disparate sources across languages.

#### 4.3.1.2 Model architecture factors

A multi-language model's capacity is dependent on its layer count, number of attention heads, and the size of the hidden representations. Karthikeyan et al. \[[135](#refbib.xhtml#refbib_135)\] demonstrate that cross-lingual transfer learning performance is highly dependent on the network's depth while not as much on the number of attention heads. They demonstrate, in particular, that enough cross-lingual transfer is possible even with single-headed attention. Moreover, the total number of parameters in the model has less bearing on the efficacy of cross-lingual transfer than the number of layers. Interestingly, in \[[79](#refbib.xhtml#refbib_79)\] mBERT's cross-lingual transfer is argued to be a result of its small parameter set and thus limited capacity, which compels it to use shared structures to align representations across languages.

Another critical architectural decision is the self-attention context window, which refers to the number of tokens given into the mLM during training. Liu et al. \[[165](#refbib.xhtml#refbib_165)\] demonstrate that although using smaller context windows is more desirable when pre-training data is sparse, utilizing longer context windows is better when huge quantities of pre-training data are available.

In \[[260](#refbib.xhtml#refbib_260)\] and \[[45](#refbib.xhtml#refbib_45)\] it is contended that since mLMs have limited model capacity that gets used by multiple languages, they cannot capture all the subtleties of several languages as a pre-trained monolingual model can. They demonstrate how knowledge distillation from a monolingual model may enhance a mLM's cross-lingual performance.

#### 4.3.1.3 Model tasks factors

**Fine-tuning Strategies** In \[[171](#refbib.xhtml#refbib_171)\] it is discussed that fine-tuning a mLM changes its parameters, impairing its cross-lingual capacity by erasing part of the alignments learned during pre-training. They demonstrate this by showing that when a mLM is fine-tuned for POS tagging, its cross-lingual retrieval performance decreases significantly. To overcome this issue, they recommend utilizing a continual learning framework for fine-tuning the model so that it does not forget the original task (MLM) on which it was trained. They claim improved results in cross-lingual POS tagging, NER, and sentence retrieval using this fine-tuning method.

**Representations Alignment** In \[[168](#refbib.xhtml#refbib_168), [261](#refbib.xhtml#refbib_261)\] the performance of zero-shot cross-lingual transfer is examined using implicitly aligned representations learned by mLMs and representations from monolingual models that are subsequently explicitly aligned using parallel corpora. They note that the explicit alignment provide improved performance. Taking this into account, Wang et al. \[[263](#refbib.xhtml#refbib_263)\] provide an explicit strategy for aligning the representations of matched word pairs across languages during mBERT training. This is accomplished by including a loss function that minimizes the Euclidean distance between aligned words' embeddings. Zhao et al. \[[298](#refbib.xhtml#refbib_298)\] also report comparable results when the representations of word pairs are explicitly aligned and the vector spaces are further normalized.

### 4.3.2 Language-Agnostic Cross-Lingual Representations

Despite the big success of transformer models, such as BERT, in advancing the NLP field and machine learning in general, the inner workings of how such models extract and store knowledge is still not completely understood and is the focus of active research. Multilingual transformers is certainly no exception but even more intriguing as they appear to use and share knowledge across multiple languages; i.e., cross-lingual transfer learning. This raises the question if multilingual transformers learn language-agnostic cross-lingual representations. Several approaches have been proposed to answer this question, each with a different angle of attack; (i) Ablation Studies, (ii) Task Probes, and (iii) Parallel Corpora Representations.

**Ablation Studies** Several ablation studies have been proposed to examine several hypotheses about the validity of language-agnostic representations in multilingual transformers. First hypothesis tested in \[[199](#refbib.xhtml#refbib_199)\] is that the joint script between high resource language is a confounding factor for good multilingual transformers performance. However this was shown to be true as multilingual transfer occur between languages that do not share script such as Urdu written in Arabic script and Hindi in Devanagari script \[[199](#refbib.xhtml#refbib_199)\]. Other work \[[229](#refbib.xhtml#refbib_229)\] examined the input tokenization as a confounding factor and found that using subword tokenization biases the models towards learning language-agnostic representations more than word-level or character-level tokenization. Pre-training tasks has also been examined as a possible confounding factor, it was shown that models trained with parallel corpora pre-training tasks such as XLM retain language-agnostic representations within the higher encoder layers in a stronger manner than models trained on monolingual corpora such as mBERT and XLMR \[[52](#refbib.xhtml#refbib_52)\].

**Parallel Corpora Representations** Another way to approach the language-agnostic representation hypothesis is to use parallel corpora in different languages and examine their parallel representations for alignment in the model embedding space. Canonical Correlation Analysis (CCA) is one techniques used to analyze the alignment of parallel representations. In \[[229](#refbib.xhtml#refbib_229)\] CCA analysis showed that mBERT does not project parallel representations on the same space. Machine translation has also been used to examine language-agnostic representations, where on one hand a sentence in a source language is provided and on the other hand multiple sentences in a target language are available and the task is to use the nearest neighbors algorithm to identify the correct translation among the target candidates. In \[[199](#refbib.xhtml#refbib_199)\] it is observed that the proper translation (i.e., representations alignment) is dependent on the layer in the model that produced the representations. It is shown that the mBERT middle layers, 5–8, produces a nearest neighbors accuracy of 75% for languages from the same family such as English-German and Hindi-Urdu. It has been argued that one proper conclusion is that the large capacity of multilingual transformer models allows to produce create and preserve language-agnostic and language-specific representations. The language-agnostic representations are rich enough to properly align multilingual words and retrieves semantically similar sentences. However, the representations are not powerful enough to approach hard problems such as machine translation \[[161](#refbib.xhtml#refbib_161)\].

**Probing tasks** Another way to investigate language-agnostic representations is to use probing tasks on the representations acquired at various layers. Consistent dependency trees, for example, may be learned from the representations of intermediate layers in mBERT that indicate syntactic abstractions \[[44](#refbib.xhtml#refbib_44), [162](#refbib.xhtml#refbib_162)\]. However, the dependency trees for Subject-Verb-Object (SVO) languages (such as English, French, and Indonesian) were more accurate than those for SOV languages (such as Turkish, Korean, and Japanese). This discrepancy between SOV and SVO languages is also seen in the labeling of POS \[[199](#refbib.xhtml#refbib_199)\]. Each layer has distinct specialties, and it is therefore advantageous to mix data from many layers for optimal results, rather than picking a single layer based on its overall performance, as proved for Dutch on a variety of NLU tasks \[[68](#refbib.xhtml#refbib_68)\]. In the same experiment, it was discovered that a multilingual model had more informative representations for POS tagging in early layers when compared to a monolingual Dutch model.

## 4.4 CASE STUDY

### 4.4.1 Goal

In this section, we provide a practical example of training a multilingual sentiment classifier. Our goal is to illustrate the zero-shot classification abilities of multilingual models where the model is only trained English data and then used to predict on non-English data with no further training.

### 4.4.2 Data, Tools, and Libraries

For this case study we use the binary sentiment classification Yelp Polarity dataset \[[297](#refbib.xhtml#refbib_297)\]. The dataset consists of 560K highly polar Yelp reviews for training and 38K reviews for testing. Original Yelp reviews take numerical score from 1 to 5 stars. This dataset is constructed by grouping the 1 and 2 stars reviews into the negative sentiment class and the 3 and 4 stars reviews into the positive sentiment class.

Our model will use the Multilingual Universal Sentence Encoder (mUSE) \[[49](#refbib.xhtml#refbib_49), [284](#refbib.xhtml#refbib_284)\] for feature generation. mUSE is a Transformer encoder trained such that text which is in different languages, but has similar meaning, will result in a similar encoding. This is analogous to the way two words with similar meaning (and usage) will have similar word embeddings. mUSE supports 16 languages: Arabic, Chinese-simplified, Chinese-traditional, English, French, German, Italian, Japanese, Korean, Dutch, Polish, Portuguese, Spanish, Thai, Turkish, Russian.

In this case study, we'll use TensorFlow Hub to load the mUSE model, Huggingface Datasets to load the Yelp Polarity dataset, and PyTorch Lightning for make training a bit simpler. mUSE internally uses TensorFlow Text for tokenization, so we install that as well. They can be installed by running the shell command shown in [Listing 4.1](#ch4.xhtml#list4_1).

![Listing 4.1 Python environment setup](images/comp4_1.jpg)

[Listing 4.1](#ch4.xhtml#b4list4_1) Python environment setup

### 4.4.3 Experiments, Results, and Analysis

Once the environment is setup, the encoder can be loaded, as shown in [Listing 4.2](#ch4.xhtml#list4_2). We also define a simple function that accepts a list of strings as inputs and returns a list of Numpy arrays. Note that we include Python 3's type annotations for clarity. They do not have to be used.

![](images/comp4_2.jpg)![Listing 4.2 Load universal sentence encoder](images/comp4_2a.jpg)

[Listing 4.2](#ch4.xhtml#b4list4_2) Load universal sentence encoder

#### 4.4.3.1 Data Preprocessing

To make training the model easy, this case study uses PyTorch Lightning. PyTorch Lightning has you implement the LightningDataModule class, which encapsulates all the data loading, preprocessing, and batching. We show how one might do this for the Yelp Polarity dataset in [Listing 4.3](#ch4.xhtml#list4_3). We use a small subset of the full train and test sets to keep model training time to a minimum. We leave it as an exercise to the reader to expand to larger subsets or to the entire dataset.

![](images/comp4_3.jpg)![](images/comp4_3a.jpg)![Listing 4.3 Load model and tokenizer](images/comp4_3b.jpg)

[Listing 4.3](#ch4.xhtml#b4list4_3) Load model and tokenizer

#### 4.4.3.2 Experiments

Next, we define the model architecture in [Listing 4.4](#ch4.xhtml#list4_4).

![](images/comp4_4.jpg)![](images/comp4_4a.jpg)![Listing 4.4 Multilingual binary classifier architecture](images/comp4_4b.jpg)

[Listing 4.4](#ch4.xhtml#b4list4_4) Multilingual binary classifier architecture

Now that the model is defined, we can load the data and then train and evaluate the model. We'll train for at most five epochs, will monitor the validation loss during training, will save the three model checkpoints (one per epoch) that contain the lowest validation loss. The checkpoints will be stored in a directory called ’model’. These options are passed to PyTorch Lightning's Trainer object via a ModelCheckpoint callback.

![](images/comp4_5.jpg)![Listing 4.5 Load data, train, and evaluate the model](images/comp4_5a.jpg)

Listing 4.5 Load data, train, and evaluate the model

We've trained a model, now let's try it out. In [Listing 4.6](#ch4.xhtml#list4_6), we define a function that predicts sentiment for input text using the model checkpoint with lowest validation loss.

![](images/comp4_6.jpg)![Listing 4.6 Load best model and run inference](images/comp4_6a.jpg)

[Listing 4.6](#ch4.xhtml#b4list4_6) Load best model and run inference

Since we used USEm embeddings, we should be able to predict sentiment for non-English languages. Let's try it out. As mentioned earlier, USEm supports 16 languages: Arabic, Chinese-simplified, Chinese-traditional, English, French, German, Italian, Japanese, Korean, Dutch, Polish, Portuguese, Spanish, Thai, Turkish, Russian. In [Listing 4.7](#ch4.xhtml#list4_7), we compare sentiment predictions between pairs of languages, finding that even though our model was trained on a small subset of the Yelp Polarity training set, it can still perform well. We also find that the model can make accurate predictions for at least one language that is *not* one of the 16 supported languages. We use input text in four languages in Listing 4.7: English, German, Italian, and Finnish.

![](images/comp4_7.jpg)![Listing 4.7 Load best model and run inference](images/comp4_7a.jpg)

[Listing 4.7](#ch4.xhtml#b4list4_7) Load best model and run inference

USEm even works on Finnish. But why? Without digging into things, it would be difficult to know for sure. Our guess is that in the training process, the subword units used in USEm's tokenization let the Transformer learn which subword units are used across languages, similar to what has been seen with the speech subunits in wav2vec2 \[[16](#refbib.xhtml#refbib_16)\]. The layers we added onto USEm, which are trained for classification, then let the model learn which subword units are related to positive or negative sentiment. Perhaps the subword units used in Finnish are close enough to those in one of the 16 languages that USEm supports.

# CHAPTER 5Transformer Modifications

DOI: [10.1201/9781003170082-5](https://doi.org/10.1201/9781003170082-5)

THERE have been many modifications made to the Transformer architecture introduced in *Attention Is All You Need*\[[254](#refbib.xhtml#refbib_254)\]. As discussed in [section 1.2](#ch1.xhtml#sec1_2), there are two broad types of modifications: changes to the organization of the Transformer block itself and changes to the submodules inside the Transformer block. This chapter discusses specific examples the Transformer block changes in [section 1.2.1.1](#ch1.xhtml#sec1_2_1_1) and the Transformer submodule changes in [section 1.2.1.2](#ch1.xhtml#sec1_2_1_2).

## 5.1 Transformer Block Modifications

In this section we'll take a detailed look at several models with altered Transformer blocks.

### 5.1.1 Lightweight Transformers

#### 5.1.1.1 Funnel-transformer

Funnel-Transformer \[[66](#refbib.xhtml#refbib_66)\] compresses the output of a transformer encoder layer via pooling before it is passed to the next layer, thus reducing computation cost. It then uses the saved computation to support a deeper or wider model, thereby increasing the model capacity.

**Encoder** The standard transformer uses the same sequence length for all layers. Funnel-Transformer changes this by placing a pooling layer between the transformer layers to reduce the sequence length. It typically has multiple transformer layers in a block of the same sequence length before the pooling operation. This is shown in [Fig. 5.1](#ch5.xhtml#fig5_1). If the output of a given layer is **h**, then the output of the pooling layer is **h**^′ = *P**o**o**l**i**n**g*(**h**), where **h** ∈ ℝ^(*T* × *d*) and **h**^′ ∈ ℝ^(*T*^′ × *d*), for some *T*^′ < *T*.

![Figure 5.1 Schematic architecture diagram for Funnel-Transformer's encoder. Each layer represents a block composed of several transformer layers with the same sequence length. Shows three pooling operations between blocks, with each decreasing the sequence length of the output by half.](images/fig5_1.jpg)

[Figure 5.1](#ch5.xhtml#b5fig5_1) Schematic architecture diagram for Funnel-Transformer's encoder. Each layer represents a block composed of several transformer layers with the same sequence length. Shows three pooling operations between blocks, with each decreasing the sequence length of the output by half.

**h**^′ is used to construct the query and the residual connection for the self-attention block, **h** is used for the key and value vectors:

  
$$\\begin{array}{ll} \\mathbf{Q} & {= \\mathbf{h}^{\\prime}\\mathbf{W}\_{Q}, \\in {\\mathbb{R}}^{T^{\\prime} \\times d\_{k}}} \\\\ \\end{array}$$  
(5.1)

  
$$\\begin{array}{ll} \\mathbf{K} & {= \\mathbf{h}\\mathbf{W}\_{K}, \\in {\\mathbb{R}}^{T \\times d\_{k}}} \\\\ \\end{array}$$  
(5.2)

  
$$\\begin{array}{ll} \\mathbf{V} & {= \\mathbf{h}\\mathbf{W}\_{V}, \\in {\\mathbb{R}}^{T \\times d\_{v}}} \\\\ \\end{array}$$  
(5.3)

This relationship between the unpooled and pooled outputs and the query, key, and value matrices of the next layer is shown in [Fig. 5.2](#ch5.xhtml#fig5_2). The output of the (*n* + 1)^(*s**t*) layer is then

  
$$\\begin{array}{l} {\\mathbf{h}^{(n + 1)} = LayerNorm(\\mathbf{h}^{\\prime}\\ ^{(n)} + multihead(\\mathbf{Q}(\\mathbf{h}^{\\prime}\\ ^{(n)}),\\mathbf{K}(\\mathbf{h}^{(n)}),\\mathbf{V}(\\mathbf{h}^{(n)}))} \\\\ \\end{array}$$  
(5.4)

![Figure 5.2 Shows how the pooling operation between Funnel-Transformer's encoder layers affect the input of the next layer. h is the output of the layer before the pooling and h′ is the output of the pooling operation. The query matrix for the next layer is constructed from the pooled output, h′. The key and value matrices for the next layer are made from the unpooled output, h.](images/fig5_2.jpg)

[Figure 5.2](#ch5.xhtml#b5fig5_2) Shows how the pooling operation between Funnel-Transformer's encoder layers affect the input of the next layer. **h** is the output of the layer before the pooling and **h**^′ is the output of the pooling operation. The query matrix for the next layer is constructed from the pooled output, **h**^′. The key and value matrices for the next layer are made from the unpooled output, **h**.

The attention weight matrix of each attention head is (*T*^′ × *T*), which has decreasing complexity for each successive layer. The output of multi-head attention has the same dimensions as **h**^′.

By constructing the query from the pooled sequence and the key and value from the unpooled sequence, the attention mechanism tries to learn how the pooled and unpooled sequences should best attend to each other to result in high quality compression. Funnel-Transformer uses mean pooling with stride and window size both set to two.

**Decoder** To support token-level prediction tasks where the model needs to produce a full output sequence, like machine translation, Funnel-Transformer has an optional decoder that upsamples the compressed encoder output to a full sequence length. *M* encoder layers will have the output sequence **h**^((*M*)) that has length *T*[*M*] = *T*/2^(*M* − 1). It will be upsampled in a single step to **h**^((*u**p*)) = \[*h*[1]^((*u**p*)), …, *h*[*T*]^((*u**p*))\] by repeating each hidden vector 2^(*M* − 1) times:

  
$$\\begin{array}{ll} h\_{i}^{up} & {= h\_{i//2^{N - 1}}^{(M)},\\forall i = 1,\\ldots,T} \\\\ \\end{array}$$  
(5.5)

  
$$\\begin{array}{ll} {x//y} & {= floor(x/y)} \\\\ \\end{array}$$  
(5.6)

To address the duplicate information in Funnel-Transformer's upsampling process, the hidden state output of the first encoder layer is added to the upsampled representation: **g** = **h**^((*u**p*)) + **h**^((1)). This acts as a residual connection. They then add a few transformer layers on top of **g** for it to learn how to best combine the features.

**Scaling** The time complexity of Funnel-Transformer is *O*(*d* ⋅ *T*² + *T* ⋅ *d*²). Since *T* decreases by half at successive encoder layers, the complexity decreases by a factor of four for each layer. Since *O*(*T* ⋅ *d*²) has the large constant *d*², it tends to dominate, providing a linear speedup, instead of a quadratic one.

Due to the complexity reduction afforded by the pooling between layers, it is possible to add additional encoder layers or make existing layers wider without increasing the computational load in any significant manner.

**Performance** Three sizes of the standard transformer were compared to several configurations of Funnel-Transformer, each with fewer or similar numbers of expected floating-point operations to the transformer to which it was being compared:

*   large: 24 layers, *d* = 1024
    
*   base: 12 layers, *d* = 768
    
*   small: 6 layers, *d* = 768
    

Quality comparisons are made for GLUE and when Funnel-Transformer decreases the sequence length and adds more layers, it performs better than the standard transformer on text classification and all GLUE datasets except for STS-B. When the sequence length is decreases but the depth is not increased, performance decreases on GLUE text classification datasets.

#### 5.1.1.2 DeLighT

DeLighT \[[180](#refbib.xhtml#refbib_180)\] is a modified Transformer architecture that performs as well as the standard transformer on machine translation and language modeling; all while using far fewer parameters and FLOPs. It introduces a transformation on the input to a Transformer block that comes before the projections into query, key, value spaces.

**DeLighT block** The DeLighT block uses N layers of the grouped linear transformation (GLT) \[[181](#refbib.xhtml#refbib_181)\] to first transform a *d*\-dimensional vector into a higher-dimensional space of *d*[*m**a**x*] = *w*[*m*]*d*[*i**n*] in the first ⌈*N*/2⌉ layers, and then transform the *d*[*m**a**x*] vector into a lower-dimensional space, *d*[*o*], using the other *N* − ⌈*N*/2⌉ layers. The *d*[*o*] vector is what is then projected in the query, key, and value spaces. DeLighT blocks closer to the output of the model are made wider and deeper than those closer to the model input. DeLightT used *d*[*o*] = *d*/2 and also shuffles the features between the groups in the GLT, using a mixer connection \[[182](#refbib.xhtml#refbib_182)\] to combine the shuffled features with the input, similar to a residual connection. The expansion phase of the DeLighT block is shown in [Fig. 5.3](#ch5.xhtml#fig5_3).

![Figure 5.3 The expansion phase of the DeLight transformation, showing the three grouped linear transformations (GLT).](images/fig5_3.jpg)

[Figure 5.3](#ch5.xhtml#b5fig5_3) The expansion phase of the DeLight transformation, showing the three grouped linear transformations (GLT).

Mehta et al. proposed that by increasing the depth of the DeLighT block and the width of its intermediate GLT layers, the transformer will have an increased representational capacity and that one can then replace multi-head attention with single-head attention. Similarly, they propose that the DeLighT block's wide linear layers let one decrease the size of the feedforward layer by up to 16x.

**Performance** DeLighT performed as well as or better than the standard transformer on machine translation, despite having considerably fewer parameters. But, when DeLighT is given more parameters, it outperforms the standard transformer. It also obtains similar or better quality to SOTA models on machine translation. Also, performance increases with the number of network parameters in the DeLighT block.

### 5.1.2 Connections between Transformer Blocks

#### 5.1.2.1 RealFormer

RealFormer, the Residual Attention Layer Transformer \[[107](#refbib.xhtml#refbib_107)\], adds residual scores to the raw attention logits (query-key dot product) of all attention heads from the previous layer of a transformer. The attention weights are then the softmax of the summed attention logits. This is shown schematically in [Fig. 5.4](#ch5.xhtml#fig5_4) and mathematically in (5.7)–(5.9).

  
$$\\begin{array}{l} {ResidualMultiHead(\\mathbf{Q},\\mathbf{K},\\mathbf{V},\\mathbf{Prev}) = \\text{concat}(head\_{1},\\ldots,head\_{h})\\mathbf{W}\_{o}} \\\\ \\end{array}$$  
(5.7)

  
$$\\begin{array}{l} {head\_{i} = ResidualAttn(\\mathbf{Q}\_{i},\\mathbf{K}\_{i},\\mathbf{V}\_{i},\\mathbf{Pre}\\mathbf{v}\_{i})} \\\\ \\end{array}$$  
(5.8)

  
$$\\begin{array}{l} {ResidualAttn(\\mathbf{Q}^{\\prime},\\mathbf{K}^{\\prime},\\mathbf{V}^{\\prime},\\mathbf{Pre}\\mathbf{v}^{\\prime}) = \\text{softmax}\\left( {\\frac{\\mathbf{Q}^{\\prime}\\mathbf{K}^{\\prime}\\ ^{\\text{T}}}{\\sqrt{\\text{d}\_{\\text{k}}}}\\text{+}\\mathbf{Pre}\\mathbf{v}^{\\prime}} \\right)\\mathbf{V}^{\\prime}} \\\\ \\end{array}$$  
(5.9)

where **P****r****e****v** ∈ ℝ^(*h* × *d*[*i**n*] × *d*[*o**u**t*]) are the attention logits from the previous transformer layer. *d*[*i**n*] is the layer's input sequence dimension and *d*[*o**u**t*] is the layer's output sequence dimension. The argument of the softmax, the attention logits or attention scores, is passed to the next RealFormer layer.

![Figure 5.4 RealFormer's residual attention connection.](images/fig5_4.jpg)

[Figure 5.4](#ch5.xhtml#b5fig5_4) RealFormer's residual attention connection.

This method can be applied to other transformer architectures, including to decoder layers. When there are multiple types of attention modules in a transformer, one can skip edges to support one residual connection for each type of attention.

**Performance** RealFormer generally performs better than the standard transformer architecture, including its use in BERT, all without increasing the number of model parameters.

### 5.1.3 Adaptive Computation Time

#### 5.1.3.1 Universal transformers (UT)

As seen in the previous chapters, transformers overcome the issues associated with RNNs, namely the bottlenecks of sequential computation and the vanishing gradient problems amongst the many. Furthermore, self-attention, the critical innovation in the transformers, helps in parallelizing the computation of per-symbol context-based vectors and creates a global receptive field where the symbol gets information from all the symbols. On the other hand, the absence of recurrent inductive bias of RNNs becomes an issue when solving tasks with inherent hierarchical structures or when the lengths vary significantly between the training and the unseen data the model predicts. Also, the number of sequential computations in transformers is independent of the input size but only dependent on the number of layers, making it computationally non-universal or Turing incomplete. Transformers apply the same amount of computation to all the inputs leading to inefficiencies in many cases where computations can be conditioned on the complexity.

Universal transformers (UT) by Dehghani et al. \[[69](#refbib.xhtml#refbib_69)\] is an extension of transformers where the parallelizability and global receptive field benefits get supplemented by the recurrent inductive bias of RNNs while being computationally universal. Instead of a fixed number of layers in the transformers, Universal transformers have a Universal transformer block, i.e., a self-attention mechanism followed by a recurrent transformation that provides a recurrent inductive bias for each input symbol in parallel. As shown in [Fig. 5.5](#ch5.xhtml#fig5_5), the Universal Transformer is a recurrent function not in time but in depth that evolves the hidden states corresponding to every input in parallel, based at each step on the sequence of previous hidden states.

![Figure 5.5 Universal Transformer with information from different positions using self-attention and applying a recurrent transition function.](images/fig5_5.jpg)

[Figure 5.5](#ch5.xhtml#b5fig5_5) Universal Transformer with information from different positions using self-attention and applying a recurrent transition function.

UT has many commonalities with the existing neural architectures, such as the Neural GPU \[[136](#refbib.xhtml#refbib_136)\] and the Neural Turing Machine \[[98](#refbib.xhtml#refbib_98)\]. It can also be shown to be equivalent to a multi-layer transformer with tied parameters across its layers. Graves proposed Adaptive Computation Time (ACT), which allows RNNs to learn dynamically how many computational steps to take between accepting input and emitting an output (ponder time) to overcome the issues of a fixed number of computational steps per symbol. UT incorporates a dynamic ACT halting mechanism to each position inspired by Graves's ACT to condition the computation per symbol based on the complexity. The research shows that UTs outperform standard transformers on a wide range of NLP and NLU and achieve a new state-of-the-art in complex tasks such as the LAMBADA language modeling.

### 5.1.4 Recurrence Relations between Transformer Blocks

#### 5.1.4.1 Transformer-XL

The Transformer-XL \[[67](#refbib.xhtml#refbib_67)\] models dependencies beyond a fixed length, while respecting sentence boundaries. It was introduced because the standard transformer architecture's fixed-width context window prevents it from learning to model dependencies at ranges outside of its fixed window. Transformer-XL can handle dependencies 450% longer than the standard transformer and inference is  ∼ 1800 times faster than the Transformer.

**Segment-level recurrence** Transformer-XL extends its context beyond a fixed window by using a method called Segment-level recurrence. Segment-level recurrence works by using the previous segment of text as additional context when processing the current segment of text. For this to work, the previous segment has to be cached, along with the transformer output of each layer for that segment.

In the standard transformer, the *n*^(*t**h*) transformer layer takes the output of the previous layer (*n* − 1) as input:

  
$$\\begin{array}{l} {\\mathbf{h}\_{t}^{(n)} = Transformer(\\mathbf{h}\_{t}^{(n - 1)})} \\\\ \\end{array}$$  
(5.10)

and internally generates the query, key, and value from **h**[*t*]^((*n* − 1)):

  
$$\\begin{array}{ll} \\mathbf{Q}\_{t}^{(n)} & {= \\mathbf{h}\_{t}^{(n - 1)}\\mathbf{W}\_{q}} \\\\ \\mathbf{K}\_{t}^{(n)} & {= \\mathbf{h}\_{t}^{(n - 1)}\\mathbf{W}\_{k}} \\\\ \\mathbf{V}\_{t}^{(n)} & {= \\mathbf{h}\_{t}^{(n - 1)}\\mathbf{W}\_{v}} \\\\ \\end{array}$$  
(5.11)

Note that *n* = 1 is being considered as the first transformer layer and *n* = 0 is the input to the first transformer layer, so **h**[*t*]^((0)) = **X**.

Eqns. (5.11) change when the previous segment is included. Consider two consecutive segments of text, which have embedded representations **X**[*t*] and **X**[*t* + 1], where *t* is just used to signify the segment ordering. When computing the output of the *n*^(*t**h*) transformer layer for the current segment, **X**[*t* + 1], we have a contribution from **h**[*t*]^((*n* − 1)), which is the previous transformer layer's output for the previous segment,

  
$$\\begin{array}{l} {\\mathbf{h}\_{t + 1}^{(n)} = \\text{TransformerXL}(\\mathbf{h}\_{t + 1}^{(n - 1)},\\mathbf{h}\_{t}^{(n - 1)}).} \\\\ \\end{array}$$  
(5.12)

The dependency on the previous segment comes in when computing the key and value for the current segment:

  
$$\\begin{array}{ll} \\mathbf{Q}\_{t + 1}^{(n)} & {= \\mathbf{h}\_{t + 1}^{(n - 1)}\\mathbf{W}\_{q}} \\\\ \\mathbf{K}\_{t + 1}^{(n)} & {= {\\widetilde{\\mathbf{h}}}\_{t + 1}^{(n - 1)}\\mathbf{W}\_{k}} \\\\ \\mathbf{V}\_{t + 1}^{(n)} & {= {\\widetilde{\\mathbf{h}}}\_{t}^{(n - 1)}\\mathbf{W}\_{v}} \\\\ \\end{array}$$  
(5.13)

  
$$\\begin{array}{l} {{\\widetilde{\\mathbf{h}}}\_{t + 1}^{(n - 1)} = \\lbrack\\text{StopGradient}(\\mathbf{h}\_{t}^{(n - 1)});\\,\\mathbf{h}\_{t + 1}^{(n - 1)}\\rbrack} \\\\ \\end{array}$$  
(5.14)

where StopGradient means the gradient is not computed during the operation.

Eqns. (5.13) and (5.14) show that the attention mechanism is being used to compute a modified attention that incorporates information from the previous input sequence to compute a representation of the current input sequence. And yet there is more to it than that. The transformer output for the current sequence depends on the transformer output for the previous sequence. The transformer output for the previous sequence depends on the sequence before that one and on the previous transformer layer. This means that as the number of transformer layers increases, the effective context size the model can process also increases. Formally, we can say that the output of the *n*^(*t**h*) transformer layer on the *t*^(*t**h*) segment has contributions from segments as far back as *t* − *n*. An example of this is shown in [Table 5.1](#ch5.xhtml#tbl5_1), for four text segments and three Transformer-XL layers.

[TABLE 5.1](#ch5.xhtml#b5tbl5_1) At a layer depth of three, the output of the transformer on the fourth segment has contributions from the first segment. For brevity, the *T* shown above is the Transformer-XL operation as described in (5.12)

  
| Layer (*n*) || *S*[1] || *S*[2] || *S*[3] || *S*[4] |
| --- | --- | --- | --- | --- |
| 0 (input) || *h*[1]^((0)) = *S*[1] || *h*[2]^((0)) = *S*[2] || *h*[3]^((0)) = *S*[3] || *h*[4]^((0)) = *S*[4] |
| --- | --- | --- | --- | --- |
| 1 || *h*[1]^((1)) = *T*(*h*[1]^((0))) || *h*[2]^((1)) = *T*(*h*[2]^((0)), *h*[1]^((0))) || *h*[3]^((1)) = *T*(*h*[3]^((0)), *h*[2]^((0))) || *h*[4]^((1)) = *T*(*h*[4]^((0)), *h*[3]^((0))) |
| 2 || *h*[1]^((2)) = *T*(*h*[1]^((1))) || *h*[2]^((2)) = *T*(*h*[2]^((1)), *h*[1]^((1))) || *h*[3]^((2)) = *T*(*h*[3]^((1)), *h*[2]^((2))) || *h*[4]^((2)) = *T*(*h*[4]^((1)), *h*[3]^((1))) |
| 3 || *h*[1]^((3)) = *T*(*h*[1]^((2))) || *h*[2]^((3)) = *T*(*h*[2]^((2)), *h*[1]^((2))) || *h*[3]^((3)) = *T*(*h*[3]^((2)), *h*[2]^((3))) || *h*[4]^((3)) = *T*(*h*[4]^((2)), *h*[3]^((2))) |

##### Positional encodings in Transformer-XL

*Positional encodings* As discussed in Ch. 1, since a Transformer doesn't contain recurrent or convolutional layers, word order is explicitly built in via positional encodings. Each input sequence is given a positional encoding, **P** ∈ ℝ^(*L* × *d*), where *L* is the maximum sequence length and *d* is the embedding dimension, and word embeddings **E** ∈ ℝ^(*L* × *d*). Note that the full input sequence is represented by **X** = **E** + **P**; this is the same **X** used throughout this chapter, e.g., as seen in (5.22).

Row *i* of **P**, **p**[*i*], contains the positional encoding for the token in position *i*. Similarly, **e**[*i*] is the word embedding for the token in position *i*. Since the positional encodings are deterministic and are independent of the tokens in the sequence, any word in position *i* will have the same positional encoding. This introduces a problem for segment-level recurrence.

Consider two consecutive text sequences **X**[*t* + 1] and **X**[*t*], and the output of the first TransformerXL layer for each sequence. (5.12) tells us that

  
$$\\begin{array}{l} {\\mathbf{h}\_{t + 1}^{(1)} = \\text{TransformerXL}(\\mathbf{X}\_{t + 1},\\mathbf{X}\_{t})} \\\\ \\end{array}$$  
(5.15)

and (5.14) says that

  
$$\\begin{array}{l} {{\\widetilde{\\mathbf{h}}}\_{t + 1}^{(0)} = \\lbrack\\text{StopGradient}(\\mathbf{X}\_{t});\\,\\mathbf{X}\_{t + 1}\\rbrack} \\\\ \\end{array}$$  
(5.16)

Since **X**[*t*] = **E**[*t*] + **P** and positional encodings are independent of the tokens in the sequence, ${\\widetilde{\\mathbf{h}}}\_{t + 1}^{(0)}$ is concatenating identical copies of the positional encodings. This is problematic because ${\\widetilde{\\mathbf{h}}}\_{t + 1}^{(0)}$ represents the expanded effective context size and thus each position in the sequence should have distinct positional encodings. Without distinct positional encodings, the model loses information about word order. The solution to this problem is to use relative positional encodings.

*Relative positional encodings* Earlier work \[[124](#refbib.xhtml#refbib_124), [224](#refbib.xhtml#refbib_224)\] introduced relative positional encodings as a way to let an attention mechanism learn from the distance between two positions in a sequence, rather than using the absolute positional encodings from the standard transformer, which biases the attention mechanism to consider the absolute position as important. Instead, information about the relative distance between **q**[*i*] and **k**[*j*] would be incorporated into the attention weight calculation, biasing the attention mechanism to consider the distance *i* − *j* as the important quantity, rather the positions *i* and *j*.

Transformer XL modified the attention matrix calculation to use sinusoidal relative positional encodings\[[67](#refbib.xhtml#refbib_67)\]. We can see how by first expanding the (*i*, *j*) term of **QK**^(*T*) in (5.23), **q**[*i*]**k**[*j*]^(*T*). Recalling (5.22), (5.24), and (5.25), we can see that the *i*^(*t**h*) row of **X** is **x**[*i*] = **e**[*i*] + **p**[*i*], and that

  
$$\\begin{array}{ll} \\mathbf{q}\_{i} & {= \\mathbf{x}\_{i}\\mathbf{W}\_{q}} \\\\ \\mathbf{k}\_{j} & {= \\mathbf{x}\_{j}\\mathbf{W}\_{k}} \\\\ \\end{array}$$  
(5.17)

Using (5.17), we expand **q**[*i*]**k**[*j*]^(*T*) to get

  
$$\\begin{array}{ll} A\_{ij} & {= (\\mathbf{e}\_{i}\\mathbf{W}\_{q} + \\mathbf{p}\_{i}\\mathbf{W}\_{q})(\\mathbf{W}\_{k}^{T}\\mathbf{e}\_{j}^{T} + \\mathbf{W}\_{k}^{T}\\mathbf{p}\_{j}^{T})} \\\\ \\ & {= \\mathbf{e}\_{i}\\mathbf{W}\_{q}\\mathbf{W}\_{k}^{T}\\mathbf{e}\_{j}^{T} + \\mathbf{e}\_{i}\\mathbf{W}\_{q}\\mathbf{W}\_{k}^{T}\\mathbf{p}\_{j}^{T}} \\\\ \\ & {\\quad + \\,\\mathbf{p}\_{i}\\mathbf{W}\_{q}\\mathbf{W}\_{k}^{T}\\mathbf{e}\_{j}^{T} + \\mathbf{p}\_{i}\\mathbf{W}\_{q}\\mathbf{W}\_{k}^{T}\\mathbf{p}\_{j}^{T}} \\\\ \\end{array}$$  
(5.18)

Transformer XL reparameterizes *A*[*i**j*] in terms of five new quantities: **R**[*i* − *j*], **u**, **v**, **W**[*k*, *E*], and **W**[*k*, *R*] \[[67](#refbib.xhtml#refbib_67)\]:

1.  **R**[*i* − *j*] are the relative positional encodings for a token pair with distance *i* − *j* and replaces **p**[*j*] in (5.18). **R**[*i* − *j*] is the (*i* − *j*)^(*t**h*) row of the relative positional encoding matrix **R** ∈ ℝ^(*L* × *d*).
    
2.  **u** replaces **p**[*i*]**W**[*q*] in the third term of (5.18).
    
3.  **v** replaces **p**[*i*]**W**[*q*] in the fourth term of (5.18).
    
4.  TransformerXL replaces the keys *K* with two sets of keys: content-based and location-based. This change results in a replacement of the key weight matrix, **W**[*k*], with two weight matrices, **W**[*k*, *E*] and **W**[*k*, *R*], where **W**[*k*, *E*] generates content-based keys and **W**[*k*, *R*] generates location-based keys \[[67](#refbib.xhtml#refbib_67)\].
    

As a result, (5.18) becomes

  
$$\\begin{array}{l} {A\_{ij} = \\mathbf{e}\_{i}\\mathbf{W}\_{q}\\mathbf{W}\_{k,E}^{T}\\mathbf{e}\_{j}^{T} + \\mathbf{e}\_{i}\\mathbf{W}\_{q}\\mathbf{W}\_{k,R}^{T}\\mathbf{R}\_{i - j}^{T} + \\mathbf{u}\\mathbf{W}\_{k,E}^{T}\\mathbf{e}\_{j}^{T} + \\mathbf{v}\\mathbf{W}\_{k,R}^{T}\\mathbf{R}\_{i - j}^{T}} \\\\ \\end{array}$$  
(5.19)

Note that by removing the explicit position dependence, that **x**[*i*] = **e**[*i*] implies **X** = **E**, and thus **q**[*i*] = **e**[*i*]**W**[*q*] and **k**[*j*] = **e**[*j*]**W**[*k*, *E*].

Using (5.19), we arrive at the final form of Transformer-XL's attention mechanism for the *n*^(*t**h*) model layer

  
$$\\begin{array}{l} {\\mathbf{Att}\\mathbf{n}\_{t}^{(n)} = \\text{softmax}\\left( \\frac{\\mathbf{A}\_{\\text{t}}^{(\\text{n})}}{\\sqrt{\\text{d}\_{\\text{k}}}} \\right)\\mathbf{V}\_{\\text{t}}^{(\\text{n})},} \\\\ \\end{array}$$  
(5.20)

where *A*[*t*]^((*n*)) is (5.19) modified as prescribed in (5.13)

  
$$\\begin{array}{l} {A\_{t,ij}^{(n)} = \\mathbf{q}\_{t,i}^{(n)}\\mathbf{k}\_{t,j}^{{(n)}^{T}} + \\mathbf{q}\_{t,i}^{(n)}\\mathbf{W}\_{k,R}^{{(n)}^{T}}\\mathbf{R}\_{i - j}^{T} + \\mathbf{u}\\,\\mathbf{k}\_{t,j}^{{(n)}^{T}} + \\mathbf{v}\\,\\mathbf{W}\_{k,R}^{{(n)}^{T}}\\mathbf{R}\_{i - j}^{T}} \\\\ \\end{array}$$  
(5.21)

Note that the sum in the softmax denominator is a masked sum over the set of key positions that the query attends to, *S*[*i*], as shown in (5.27). Also, since **x** = **e**[*i*], **h**[*t*]^((0)) = **X**[*t*].

### 5.1.5 Hierarchical Transformers

Two examples of hierarchical transformers are the Vision Transformer \[[78](#refbib.xhtml#refbib_78)\], for image recognition, and TimeSformer \[[29](#refbib.xhtml#refbib_29)\], for video classification/action recognition. Both models will be covered in [Chapter 6](#ch6.xhtml).

## 5.2 Transformers with Modified Multi-Head Self-Attention

### 5.2.1 Structure of Multi-Head Self-Attention

Multi-head attention is a way of combining multiple attention mechanisms that lets a model learn different types of dependencies between the input and output. The multi-head attention mechanism is the core of every transformer block. The encoder and decoder blocks both use multi-head self-attention, and the decoder block has a second multi-head attention that attends to the output of the encoder block, with the appropriate causal constraint.

In this section, we'll describe the structure of the multi-head self-attention calculation for a single input sequence of *L* tokens, with embedding dimension *d*. The input sequence can be represented by a matrix **X** ∈ ℝ^(*L* × *d*):

  
$$\\begin{array}{l} {\\mathbf{X} = \\left\\lbrack \\begin{array}{l} \\mathbf{x}\_{1} \\\\ \\vdots \\\\ \\mathbf{x}\_{L} \\\\ \\end{array} \\right\\rbrack} \\\\ \\end{array}$$  
(5.22)

where **x**[*i*] = (*x*[0]^((*i*)), …, *x*[*d* − 1]^((*i*))) is the embedding vector of the *i*^(*t**h*) token.

As we saw in [section 2.4.2.1](#ch2.xhtml#sec2_4_2_1), the output of the attention mechanism (before the heads are concatenated) can be represented by

  
$$\\begin{array}{l} {\\mathbf{Attn}(\\mathbf{Q},\\mathbf{K},\\mathbf{V}) = \\text{softmax}\\left( \\frac{\\mathbf{Q}\\mathbf{K}^{\\text{T}}}{\\sqrt{\\text{d}\_{\\text{k}}}} \\right)\\mathbf{V},} \\\\ \\end{array}$$  
(5.23)

where **Q**, **K**, **V** are the query, key, and value matrices, respectively. Each is the result of transforming the input sequence into a different vector space:

  
$$\\begin{array}{ll} \\mathbf{Q} & {= \\mathbf{X}\\mathbf{W}\_{q}, \\in {\\mathbb{R}}^{L \\times d\_{k}}} \\\\ \\mathbf{K} & {= \\mathbf{X}\\mathbf{W}\_{k}, \\in {\\mathbb{R}}^{L \\times d\_{k}}} \\\\ \\mathbf{V} & {= \\mathbf{X}\\mathbf{W}\_{v}, \\in {\\mathbb{R}}^{L \\times d\_{v}}} \\\\ \\end{array}$$  
(5.24)

where *d*[*k*] is the dimension of the query and key spaces and is typically set to *d*, and *d*[*v*] is the value dimension. The matrices **W**[*q*], **W**[*k*] ∈ ℝ^(*d* × *d*[*k*]), and **W**[*v*] ∈ ℝ^(*d* × *d*[*v*]) are basically rotation matrices. Each row of a query/key/value matrix corresponds to the query/key/value vector of the *i*^(*t**h*) token:

  
$$\\begin{array}{l} {\\mathbf{Q} = \\left\\lbrack \\begin{array}{l} \\mathbf{q}\_{1} \\\\ \\vdots \\\\ \\mathbf{q}\_{L} \\\\ \\end{array} \\right\\rbrack,\\mathbf{K} = \\left\\lbrack \\begin{array}{l} \\mathbf{k}\_{1} \\\\ \\vdots \\\\ \\mathbf{k}\_{L} \\\\ \\end{array} \\right\\rbrack,\\mathbf{V} = \\left\\lbrack \\begin{array}{l} \\mathbf{v}\_{1} \\\\ \\vdots \\\\ \\mathbf{v}\_{L} \\\\ \\end{array} \\right\\rbrack} \\\\ \\end{array}$$  
(5.25)

Note that (5.24) can be adapted for the case of multi-head attention between two sequences, **X**[1] and **X**[2], of lengths *L*[1] and *L*[2], respectively. For two sequences, the query matrix is formed from **X**[1] and the key and value matrices are formed from **X**[2]:

  
$$\\begin{array}{ll} \\mathbf{Q} & {= \\mathbf{X}\_{1}\\mathbf{W}\_{k},\\, \\in {\\mathbb{R}}^{L\_{1} \\times d\_{k} \\times h}} \\\\ \\mathbf{K} & {= \\mathbf{X}\_{2}\\mathbf{W}\_{k},\\, \\in {\\mathbb{R}}^{L\_{2} \\times d\_{k} \\times h}} \\\\ \\mathbf{V} & {= \\mathbf{X}\_{2}\\mathbf{W}\_{v},\\, \\in {\\mathbb{R}}^{L\_{2} \\times d\_{v} \\times h}} \\\\ \\end{array}$$  
(5.26)

where **X**[1] ∈ ℝ^(*L*[1] × *d*) and **X**[2] ∈ ℝ^(*L*[2] × *d*). This is generally what happens in a transformer decoder block. **X**[1] ∈ ℝ^(*L* × *d*)

The softmax portion of (5.23) is the attention weight matrix *A*[*i**j*]:

  
$$\\begin{array}{l} {A\_{ij} = \\frac{\\exp(\\frac{\\mathbf{q}\_{i}\\mathbf{k}\_{j}^{T}}{\\sqrt{d\_{k}}})}{{\\sum\\limits\_{r \\in S\_{i}}{\\exp}}(\\frac{\\mathbf{q}\_{i}\\mathbf{k}\_{r}^{T}}{\\sqrt{d\_{k}}})},} \\\\ \\end{array}$$  
(5.27)

where *S*[*i*] is the set of key positions that query **q**[*i*] can attend to.

#### 5.2.1.1 Multi-head self-attention

So far, we have only discussed single-head self-attention. Multi-head attention is mainly partitioning the matrices shown above into *h* pieces, where *h* is the number of attention heads.

Each attention head has its own query/key/value that is obtained by breaking the single-head versions into *h* equally sized pieces, that are indexed by *n* = 1, …, *h*:

  
$$\\begin{array}{ll} \\mathbf{Q}\_{n} & {= \\mathbf{X}\\mathbf{W}\_{n}^{(q)},\\, \\in {\\mathbb{R}}^{L \\times d\_{k}/h}} \\\\ \\mathbf{K}\_{n} & {= \\mathbf{X}\\mathbf{W}\_{n}^{(k)},\\, \\in {\\mathbb{R}}^{L \\times d\_{k}/h}} \\\\ \\mathbf{V}\_{n} & {= \\mathbf{X}\\mathbf{W}\_{n}^{(v)},\\, \\in {\\mathbb{R}}^{L \\times d\_{v}/h}} \\\\ \\end{array}$$  
(5.28)

This does not mean that we now have *h* query, key, and value matrices, but that the matrices shown in (5.28) are a part of the matrices shown in (5.24). This is explicitly shown for the query in [Fig. 5.6](#ch5.xhtml#fig5_6).

![Figure 5.6 The query matrix, Q, can be partitioned into h heads, as described in (5.28).](images/fig5_6.jpg)

[Figure 5.6](#ch5.xhtml#b5fig5_6) The query matrix, **Q**, can be partitioned into *h* heads, as described in (5.28).

The key and value matrices are partitioned into attention heads in a similar way to **Q** and the attention calculation for the *n*^(*t**h*) head proceeds as expected:

  
$$\\begin{array}{l} {\\mathbf{Att}\\mathbf{n}^{(n)}(\\mathbf{Q}\_{n},\\mathbf{K}\_{n},\\mathbf{V}\_{n}) = \\text{softmax}\\left( \\frac{\\mathbf{Q}\_{\\text{n}}\\mathbf{K}\_{\\text{n}}^{\\text{T}}}{\\sqrt{\\text{d}\_{\\text{k}}\\text{/h}}} \\right)\\mathbf{V}\_{\\text{n}},} \\\\ \\end{array}$$  
(5.29)

Note that for the multihead case, **Q**[*n*]**K**[*n*]^(*T*) is divided by $\\sqrt{d\_{k}/h}$ instead of $\\sqrt{d\_{k}}$. This change account s for the change in effective dimension of the query and key spaces to *d*[*k*]/*h*. The attention heads are then combined as described in (2.19).

#### 5.2.1.2 Space and time complexity

Computing the attention weight matrix described in section 5.27 takes *O*(*L*² ⋅ *d*[*k*]) matrix multiplications and computing the context vector in section 5.23 needs *O*(*L*² ⋅ *d*[*v*]) matrix multiplications, so the time complexity of self-attention is *O*(*L*² ⋅ *d*[*k*] + *L*² ⋅ *d*[*v*]).

Consider a single input sequence of *L* tokens and that the query, key, and value share the same dimensionality, so *d*[*k*] = *d*[*v*] = *d*[*m**o**d**e**l*]. This means that **Q**, **K**, **V** are *L* × *d*[*m**o**d**e**l*] matrices and the attention weight matrix from (5.23) is *L* × *L*. Assuming 32-bit floating points numbers, the memory usage grows quickly, as shown in [Table 5.2](#ch5.xhtml#tbl5_2). More memory is required when including the batch size. For example, if the batch size were 32 and the sequence length were 20,000, then 51.2 GB would be needed to store the self-attention weights. The time complexity is also quadratic in *L*. This kind of scaling becomes prohibitive as the sequence length increases. For example, if the sequence length doubles, the amount of time needed to compute and store the attention weights will increase fourfold.

[TABLE 5.2](#ch5.xhtml#b5tbl5_2) Memory usage for self-attention weights, for 32-bit floats \[[142](#refbib.xhtml#refbib_142)\]

  
| L || Memory |
| --- | --- |
| 600 || 4 MB |
| --- | --- |
| 1K || 1.4 MB |
| 20K || 1.6 GB |
| 64K || 16.384 GB |

### 5.2.2 Reducing Complexity of Self-Attention

This section discusses several transformer models that reduce the computational complexity of multi-head self-attention.

#### 5.2.2.1 Longformer

When calculating self-attention (omitting the causal requirement for the self-attention between the encoder and decoder blocks) there are usually no restrictions on which positions in the sequence can attend to each other. This means that, in principle, the matrix of attention weights for every head could be dense. When viewed as a graph, it corresponds to a fully-connected, weighted bipartite graph. If the sequence has *L* tokens, then there would be *L*(*L* − 1)/2 edges. Longformer \[[25](#refbib.xhtml#refbib_25)\] changes this by restricting which positions can attend to each other according to specific patterns. This results in sparse attention weights across all heads and corresponds to deleting edges from the attention graph.

Longformer combines a global attention with two types of short-range attention, sliding window and dilated sliding window. Each attention pattern corresponds to a type of attention mask.

**Sliding window attention** Rather than being able to attend to any token in the sequence, each token in a sequence is given a fixed-sized context window, *w*, so it can only attend to its neighbors. For example, if we had a sequence of nine tokens, (*w*[1], …, *w*[9]), and window size *w* = 4, then the context of the middle token, *w*[5], would extend right (*w*[3], *w*[4]) and left (*w*[6], *w*[7]) by two tokens each. This is shown in [Fig. 5.7](#ch5.xhtml#fig5_7).

![Figure 5.7 Sliding window attention pattern, for L = 9 and w = 4. Row i corresponds to query i. Columns with a • are keys that query i attends to and ⋅ represents a lack of attention (a missing edge).](images/fig5_7.jpg)

[Figure 5.7](#ch5.xhtml#b5fig5_7) Sliding window attention pattern, for *L* = 9 and *w* = 4. Row *i* corresponds to query *i*. Columns with a • are keys that query *i* attends to and ⋅ represents a lack of attention (a missing edge).

In the graph view, this means that each vertex would be linked to at most *w* − 1 vertices. So, this change reduces the number of edges from *L*(*L* − 1)/2 to *L*(*w* − 1). This simple change reduces the complexity from one that is quadratic in the sequence length to one that is linear in the sequence length, *O*(*L**w*), since the sliding window attention weight matrix would have *Lw* nonzero values in each row (or column).

**Dilated sliding window attention** This attention pattern extends the breadth of the sliding window attention by add gaps of size *d* in the context window. This actually extends the effective size of the context window. For example, in the sequence of nine tokens used above, suppose we added a dilation *d* = 2. In generating the context of *w*[5], we would now skip one word in between. Thus, the left context of *w*[5] would be (*w*[1], *w*[3]) and the right context would be (*w*[7], *w*[9]). Note that even though the overall context width has grown, this attention pattern also prevents a token from attending to its immediate neighbor, or to any token that is a distance *d* − 1 away from the center of the window or to any position it attends to that are inside the window. Different attention heads can use different values of *d*, which mitigates the issue mentioned above. [Fig. 5.8](#ch5.xhtml#fig5_8) shows dilated sliding window attention for *L* = 2, *w* = 4, and *d* = 2.

![Figure 5.8 Dilated sliding window attention pattern, for L = 12, w = 4, and d = 2. Row i corresponds to query i. Columns with a • are keys that query i attends to and ⋅ represents a lack of attention (a missing edge).](images/fig5_8.jpg)

[Figure 5.8](#ch5.xhtml#b5fig5_8) Dilated sliding window attention pattern, for *L* = 12, *w* = 4, and *d* = 2. Row *i* corresponds to query *i*. Columns with a • are keys that query *i* attends to and ⋅ represents a lack of attention (a missing edge).

**Global attention** The global attention pattern chooses lets some tokens attend to any other token in the sequence. In such cases, all tokens in the sequence attend to that token. This corresponds to choosing specific rows of an attention weight matrix and their transposed columns.

Longformer decides which tokens are allowed to have global attention based on the training task. For instance, in question and answer tasks, all tokens in the question have global attention. The number of tokens with global attention is generally independent of sequence length, so global attention is also linear in sequence length. The Longformer combines this global attention with the sliding window attention.

Weights for the global and short-ranged attention patterns are computed separately by giving the global and sliding window patterns their own query, key, and value matrices: **Q**[*g*], **K**[*g*], **V**[*g*] and **Q**[*s*], **K**[*s*], **V**[*s*], respectively.

Longformer uses small window sizes for lower layers and larger window sizes for higher layers. This gives the higher layers a hierarchical nature. In fact, dilated sliding windows are only used for higher layers, so that lower layers can focus on local context.

#### 5.2.2.2 Reformer

Reformer, introduced in \[[142](#refbib.xhtml#refbib_142)\], addresses attention mechanism complexity by modifying the attention mechanism and reduces memory usage by using reversible residual networks. These tricks let the Reformer include context windows that are several orders of magnitude larger than a Transformer (up to 1,000,000 words).

**Attention and locality-sensitive hashing** As discussed in [section 5.2.1.1](#ch5.xhtml#sec5_2_1_1), the scaled dot-product attention which is at the core of the transformer has time complexity*O*(*L*²), which becomes prohibitive as the number of tokens in the sequence, *L*, increases. The Reformer model addresses this by modifying attention mechanism with locality-sensitive hashing. This changes the time complexity to *O*(*L*log *L*).

Recall that in the scaled dot-product attention, the query, key, and value matrices are the result of transforming the matrix of *d*[*m**o**d**e**l*] -dimensional input vectors into queries and keys of dimension *d*[*k*] and values of dimension *d*[*v*].

In the equation for *A*, the computationally expensive term is the product **QK**^(*T*), moreover, once the softmax function is applied, only the largest terms along each *d*[*m**o**d**e**l*] dimension are important. This means that for each query vector in **Q**, we only need the keys in **K** that are closest to it. To make this easier, they set **Q** = **K**, meaning that for each query vector, we only need to find the closest queries. This is an approximate nearest neighbors problem, so we can use locality-sensitive hashing (LSH).

**Locality-sensitive hashing** Locality-sensitive hashing, or LSH, was introduced in 1998, in \[[129](#refbib.xhtml#refbib_129)\] as a method of approximate similarity search based on hashing. In formal terms, LSH is based on a family of hash functions ℱ that operate on a collection of items where, if any two such items *x* and *y*, *P**r**o**b*[*h* ∈ ℱ]\[*h*(*x*) = *h*(*y*)\] = *s**i**m*(*x*, *y*), where *s**i**m*(*x*, *y*) ∈ \[0, 1\] in a similarity function defined on the collection of items \[[39](#refbib.xhtml#refbib_39)\]. Or, in other words, you have an LSH method whenever you can hash the items in a dataset such that the collision probability of any two items is much higher when those items are close together than when they're far apart.

There are many ways to implement an LSH scheme. The Reformer uses the angular LSH scheme defined in \[[6](#refbib.xhtml#refbib_6)\]. Recall that the query matrix **Q** (and key matrix **K**) has shape *l* × *d*[*k*]. To compute a hash for **Q**, begin by generating a random *d*[*k*] × *b*/2 matrix **R**, where each column has a single nonzero value sampled uniformly from  ± 1 and *b* is the number of hashes. Next, compute **QR**, which rotates the query (and key) matrix. Finally, the hash is *h*(**Q**) = arg max(\[**Q****R**; -**Q****R**\]) \[[142](#refbib.xhtml#refbib_142)\]. Once the query and key have been hashed, you can permute the indices so that sequence positions that hashed into the same bucket are side by side. Then, within each hash bucket, compute the full attention.

We can use this information to see how LSH affects the attention calculation by first rewriting the equation for self-attention, (5.23), using (5.27):

  
$$\\begin{array}{l} {a\_{i} = {\\sum\\limits\_{j \\in S\_{i}}{\\exp}}\\left( {\\frac{\\mathbf{q}\_{\\mathbf{i}}\\mathbf{k}\_{j}^{T}}{\\sqrt{d\_{k}}} - \\log Z(i,S\_{i})} \\right)\\mathbf{v}\_{j},} \\\\ \\end{array}$$  
(5.30)

where *S*[*i*] is the set of key positions that query *i* attends to and $Z(i,S\_{i}) = {\\sum\\limits\_{r \\in S\_{i}}{\\exp}}\\left( \\frac{\\mathbf{q}\_{\\mathbf{i}}\\mathbf{k}\_{r}^{T}}{\\sqrt{d\_{k}}} \\right)$ is the softmax normalization term.

Without a loss in generality, we can rewrite (5.30) as a sum over an expanded set of key positions, *S̃*[*i*] ⊇ *S*[*i*], that can include positions that **q**[*i*] does not attend to:

  
$$\\begin{array}{ll} a\_{i} & {= {\\sum\\limits\_{j \\in {\\widetilde{S}}\_{i}}{\\exp}}\\left( {\\frac{\\mathbf{q}\_{\\mathbf{i}}\\mathbf{k}\_{j}^{T}}{\\sqrt{d\_{k}}} - m(i,S\_{i}) - \\log Z(i,S\_{i})} \\right)\\mathbf{v}\_{j}} \\\\ \\end{array}$$  
(5.31)

  
$$\\begin{array}{ll} {m(i,S\_{i})} & {= \\begin{cases} {\\infty,} & {j \\notin S\_{i}} \\\\ {0,} & \\text{otherwise} \\\\ \\end{cases}} \\\\ \\end{array}$$  
(5.32)

The term *m*(*i*, *S*[*i*]) in (5.31) is a masking term that ensures that key positions that **q**[**i**] does *not* attend to does not contribute to the sum.

As mentioned above, the set *S*[*i*] is the set of key positions that query *i* attends to. Under the LSH scheme defined above, *S*[*i*] should only contain key positions that hash into the same bucket as the query, or in other words

  
$$\\begin{array}{l} {S\_{i} = \\{ j:h(\\mathbf{q}\_{\\mathbf{i}}) = h(\\mathbf{k}\_{j})\\}} \\\\ \\end{array}$$  
(5.33)

*A priori*, there are no guarantees that a query will have any keys to attend to. To address this, and ensure that *h*(**q**[**i**]) = *h*(**k**[*j*]), \[[142](#refbib.xhtml#refbib_142)\] fixes key **k**[*j*] so that $\\mathbf{k}\_{j} = \\frac{\\mathbf{q}\_{j}}{||\\mathbf{q}\_{j}||}$. To make the computation more efficient, Reformer does two simple things

1.  Queries are sorted so those in the same hash bucket are adjacent. Within the hash bucket, original sequence order is preserved
    
2.  The sorted queries are grouped into blocks of *m* consecutive queries
    

  
$$\\begin{array}{l} {m = \\frac{2L}{\\text{Number~of~buckets}}} \\\\ \\end{array}$$  
(5.34)

Within each block, each position is allowed to attend to the others in the block and to those in the preceding block. These two changes define a new set of key positions that query *i* can attend to:

  
$${\\widetilde{S}}\_{i} = \\left\\{ {j:\\left\\lfloor \\frac{s\_{i}}{m} \\right\\rfloor - 1 \\leq \\left\\lfloor \\frac{s\_{j}}{m} \\right\\rfloor \\leq \\left\\lfloor \\frac{s\_{i}}{m} \\right\\rfloor} \\right\\},$$  
(5.35)

where *s*[*i*] is the position in the sorted matrix that position *i* was moved to. (5.35) can be used in (5.31) to compute the attention under the LSH scheme described above.

*Multi-round LSH* Due to the randomness inherent to LSH, its easy for similar things to hash into different buckets. To address this, it's common practice to do multiple rounds of LSH. For instance, when approximating a feature vector with LSH, one might hash the vector multiple times to generate an LSH signature. Then, instead of comparing two feature vectors with, say, cosine similarity, you would compare their LSH signatures using the Hamming distance. Similarly, in Reformer, you can compute multiple hashes for queries and keys and then combine them.

As discussed above, a query at position *i* can attend to the key positions in *S*[*i*]. However, if we perform *n* rounds of LSH, then we end up with *n* sets of key positions that query position *i* can attend to

  
$$\\begin{array}{l} {S\_{i} = {\\underset{r = 1}{\\overset{n}{\\cup}}S\_{i}^{(r)}},} \\\\ \\end{array}$$  
(5.36)

where *S*[*i*]^((*r*)) = {*j* : *h*^((*r*))(**q**[**i**]) = *h*^((*r*))(**q**[*j*])}. Then, regarding sorting queries by hash bucket, (5.35) becomes

  
$${\\widetilde{S}}\_{i}^{(r)} = \\left\\{ {j:\\left\\lfloor \\frac{s\_{i}^{(r)}}{m} \\right\\rfloor - 1 \\leq \\left\\lfloor \\frac{s\_{j}^{(r)}}{m} \\right\\rfloor \\leq \\left\\lfloor \\frac{s\_{i}^{(r)}}{m} \\right\\rfloor} \\right\\}.$$  
(5.37)

We can similarly update (5.31) for multi-round LSH:

  
$$\\begin{array}{l} {a\_{i} = {\\sum\\limits\_{r}^{n}{\\exp}}\\left( {\\log Z(i,S\_{i}^{(r)}) - \\log Z(i,S\_{i})} \\right)a\_{i}^{(r)}} \\\\ \\end{array}$$  
(5.38)

  
$$\\begin{array}{l} {a\_{i}^{(r)} = {\\sum\\limits\_{j \\in {\\widetilde{S}}\_{i}^{(r)}}{\\exp}}\\left( {\\frac{\\mathbf{q}\_{\\mathbf{i}}\\mathbf{k}\_{j}^{T}}{\\sqrt{d\_{k}}} - m\_{i,j}^{(r)} - \\log Z(i,S\_{i}^{(r)})} \\right)\\mathbf{v}\_{j}} \\\\ \\end{array}$$  
(5.39)

  
$$\\begin{array}{l} {m\_{i,j}^{(r)} = \\begin{cases} \\infty & {j \\notin S\_{i}^{(r)}} \\\\ 10^{5} & {\\text{if~}i = j} \\\\ {\\log N\_{i,j}} & \\text{otherwise} \\\\ \\end{cases}} \\\\ \\end{array}$$  
(5.40)

  
$$\\begin{array}{l} \\left. N\_{i,j} = \\middle| \\{ r^{\\prime}:j \\in S\_{i}^{(r^{\\prime})}\\} \\right| \\\\ \\end{array}$$  
(5.41)

Note that in the multi-round LSH case, Reformer modifies the masking term to include (and downweight) the case where query at position *i* attends to a key at position *i*. This case is added because, while the standard transformer allows a position to attend to itself, this is unhelpful when **Q** = **K**, as is the case in LSH attention. It is unhelpful because the LSH hash *h*(**q**[*i*]) of any position *i* is trivially equal to itself.

*Reversibility and memory* The Reformer also addressed the memory usage of the standard transformer using reversible residual layers.

*Residual layers* were designed to address the problem of training error increasing with network depth while avoiding the problem of vanishing gradients. By rewriting a neural network in terms of a residual function, training accuracy could be made to increase with network depth:

  
$$\\begin{array}{l} {y = x + F(x),} \\\\ \\end{array}$$  
(5.42)

where *x* is layer input and *y* is layer output \[[105](#refbib.xhtml#refbib_105)\]. ResNets are stacks of these residual layers.

In the standard transformer, each transformer layer has more than one residual layer. For example, a single transformer encoder block has two residual blocks. The first residual block is multi-head attention \[[254](#refbib.xhtml#refbib_254)\], followed by layer normalization \[[13](#refbib.xhtml#refbib_13)\]. The second residual block is the position-wise feedforward network (FFN) \[[254](#refbib.xhtml#refbib_254)\], followed by layer normalization. Note that the layer normalization operation has the form *x* + *S**u**b**l**a**y**e**r*(*x*), where *Sublayer* represents the incoming layer. For the first residual block, the sublayer is the Multi-head attention and for the second residual block it is the FFN layer.

**Reversible residual layers** are a reversible variant of the residual layers used in image recognition and were introduced as a less memory-intensive replacement \[[94](#refbib.xhtml#refbib_94)\]. Each reversible layer takes a pair (*x*[1], *x*[2]) as input and returns a pair (*y*[1], *y*[2]) as output:

  
$$\\begin{array}{l} {y\_{1} = x\_{1} + F(x\_{2})} \\\\ {y\_{2} = x\_{2} + G(y\_{1})} \\\\ \\end{array}$$  
(5.43)

To reverse the layer, simply subtract the residual from both sides:

  
$$\\begin{array}{l} {x\_{2} = y\_{2} - G(y\_{1})} \\\\ {x\_{1} = y\_{1} - F(x\_{2})} \\\\ \\end{array}$$  
(5.44)

Now, suppose we have a stack of *n* such reversible layers, so that the input to the *n*^(*t**h*) layer is the output of layer *n* − 1. Eqns. (5.43) and (5.44) become recurrence relations:

  
$$\\begin{array}{ll} y\_{1}^{(n)} & {= y\_{1}^{(n - 1)} + F(y\_{2}^{(n - 1)})} \\\\ \\end{array}$$  
(5.45)

  
$$\\begin{array}{ll} y\_{2}^{(n)} & {= y\_{2}^{(n - 1)} + G(y\_{1}^{(n)})} \\\\ \\end{array}$$  
(5.46)

  
$$\\begin{array}{ll} y\_{2}^{(n - 1)} & {= y\_{2}^{(n)} - G(y\_{1}^{(n)})} \\\\ \\end{array}$$  
(5.47)

  
$$\\begin{array}{ll} y\_{1}^{(n - 1)} & {= y\_{1}^{(n)} - F(y\_{2}^{(n - 1)})} \\\\ \\end{array}$$  
(5.48)

Thus, the output activations of layer *n* − 1 can be computed from the output activations of layer *n* and the value of the residuals *F* and *G* for layer *n*. This is why the activations for a reversible residual layer do not need to be stored to perform backpropagation. Because the activations for intermediate layers do not need to be stored, the model will use less memory (without sacrificing performance).

**Reversible layers in a transformer** Now that we understand what reversible residual layers are and how they save memory, we can look at how they're used in the Reformer \[[142](#refbib.xhtml#refbib_142)\]. The attention mechanism serves as the residual function *F* and the position-wise feed-forward network is *G*. The layer normalization becomes part of the residual block since it has the form *x* + *S**u**b**l**a**y**e**r*(*x*), where *Sublayer* represents the appropriate residual function. Ref. \[[142](#refbib.xhtml#refbib_142)\] shows that a transformer using reversible residual layers has the same performance as the standard transformer.

#### 5.2.2.3 Performer

The Performer \[[53](#refbib.xhtml#refbib_53)\] model reduces attention mechanism complexity using a method called *Fast Attention Via positive Orthogonal Random features* (FAVOR+). Performer does not bias the attention mechanism ahead of time by using attention patterns, instead FAVOR+ approximates the softmax calculation using kernels.

**Attention as a kernel** By rewriting the formula for self-attention ((5.23)) the kernel formalism becomes apparent:

  
$$\\begin{array}{ll} {Attn(\\mathbf{Q},\\mathbf{K},\\mathbf{V})} & {= \\text{softmax}\\left( \\frac{\\mathbf{Q}\\mathbf{K}^{\\text{T}}}{\\sqrt{\\text{d}\_{\\text{k}}}} \\right)\\mathbf{V}} \\\\ \\end{array}$$  
(5.49)

  
$$\\begin{array}{ll} \\ & {\\Rightarrow\\left\\lbrack \\frac{\\exp\\left( \\frac{\\mathbf{q}\_{i}\\mathbf{k}\_{j}^{T}}{\\sqrt{d\_{k}}} \\right)}{{\\sum\\limits\_{r \\in S\_{i}}{\\exp}}\\left( \\frac{\\mathbf{q}\_{i}\\mathbf{k}\_{r}^{T}}{\\sqrt{d\_{k}}} \\right)} \\right\\rbrack\\mathbf{V}} \\\\ \\end{array}$$  
(5.50)

  
$$\\begin{array}{ll} \\ & {= \\mathbf{D}^{- 1}\\left\\lbrack {\\exp\\left( \\frac{\\mathbf{q}\_{i}\\mathbf{k}\_{j}^{T}}{\\sqrt{d\_{k}}} \\right)} \\right\\rbrack\\mathbf{V},} \\\\ \\end{array}$$  
(5.51)

where **D** is the diagonal matrix of terms $D\_{ij} = \\delta\_{ij}{\\sum\\limits\_{r \\in S\_{i}}{\\exp}}\\left( \\frac{\\mathbf{q}\_{i}\\mathbf{k}\_{r}^{T}}{\\sqrt{d\_{k}}} \\right)$. Note that each diagonal element is part of the sum in the softmax denominator and the inverse of **D** is simply the matrix of reciprocals. Within the Reformer, we can then redefine the attention weights as $A\_{ij} = \\exp\\left( \\frac{\\mathbf{q}\_{i}\\mathbf{k}\_{j}^{T}}{\\sqrt{d\_{k}}} \\right)$, so that $D\_{ij} = \\delta\_{ij}{\\sum\\limits\_{r \\in S\_{i}}A\_{ir}}$. Thus *A**t**t**n*(**Q**, **K**, **V**) = **D**^( − 1)**A****V**. The queries and keys can be scaled so that the key dimension is absorbed into them, *A*[*i**j*] is simply exp (**q**[*i*]**k**[*j*]^(*T*)).

Since *A*[*i**j*] depends on the inner product of the query and key vectors, it is a measure of similarity between **q**[*i*] and **k**[*j*]. These attention weights can be approximated using the FAVOR+ algorithm:

  
$$\\begin{array}{l} {A\_{ij} = \\langle\\phi{(\\mathbf{q}\_{i}^{T})}^{T}\\phi(\\mathbf{k}\_{j}^{T})\\rangle,} \\\\ \\end{array}$$  
(5.52)

where mapping *ϕ* maps **Q**, **K** ∈ ℝ^(*L* × *d*[*k*]) to **Q**^′, **K**^′ ∈ ℝ^(*L* × *r*), respectively, with *r* > 0. The rows of **Q**^′ are *ϕ*(**q**[*i*]^(*T*))^(*T*) and the rows of **K**^′ are *ϕ*(**k**[*j*]^(*T*))^(*T*); then (5.49) becomes

  
$$\\begin{array}{l} {\\hat{Attn}(\\mathbf{Q},\\mathbf{K},\\mathbf{V}) = {\\hat{\\mathbf{D}}}^{- 1}(\\mathbf{Q}^{\\prime}({(\\mathbf{K}^{\\prime})}^{T}\\mathbf{V}),\\,{\\hat{D}}\_{ij} = \\delta\_{ij}{\\sum\\limits\_{m \\in S\_{i}}\\phi}(\\mathbf{q}\_{i}^{T})\\phi{(\\mathbf{k}\_{m}^{T})}^{T}.} \\\\ \\end{array}$$  
(5.53)

When the kernel functions *ϕ*(**x**) are as defined in \[[53](#refbib.xhtml#refbib_53)\], the attention weights *A*[*i**j*] = exp (**q**[*i*]**k**[*j*]^(*T*)) can be approximated by

  
$$\\begin{array}{l} {\\exp(\\mathbf{q}\_{i}\\mathbf{k}\_{j}^{T}) = \\Lambda{\\langle\\cosh(\\omega^{T}(\\mathbf{q}\_{i} + \\mathbf{k}\_{j}))\\rangle}\_{\\omega},} \\\\ \\end{array}$$  
(5.54)

where *Λ* = exp ( − (∥**q**[*i*]∥² + ∥**k**[*j*]∥²)/2) and *ω* is sampled from the *d*[*k*]\-dimensional standard normal distribution. If *ω* in (5.54) is replaced with $\\sqrt{d}\\frac{\\mathbf{\\omega}}{\\|\\mathbf{\\omega}\\|}$, then *ω* is any point on the surface of the *d*[*k*]\-dimensional sphere of radius $\\sqrt{d\_{k}}$.

This kernel approximation of the softmax calculation reduces the quadratic complexity to one that is nearly linear in sequence length, and the approximation error can be decreased by periodically resampling *ω*.

#### 5.2.2.4 Big Bird

Big Bird is another effort to give the Transformer a sparse attention mechanism that allows for linear scaling. It is also proven to be Turing complete and a universal sequence function approximator \[[292](#refbib.xhtml#refbib_292)\].

**An Attention mechanism is a directed graph** Big Bird describes the attention mechanism as a directed graph. The vertices represent the *L* positions in the input sequence. The directed edges represent the pre-softmax attention weights. In other words, the directed edges are the inner products between the query and key vectors, where the *i*^(*t**h*) vertex will only have directed edges with the vertices that correspond to the key positions that it can attend to, as described by the set *S*[*i*] in (5.27).

***Adjacency matrix*** The graph representation casts the problem of reducing the complexity of the attention mechanism as a graph sparsification problem, which can be tackled with graph theory. Big Bird describes the attention graph with its *L* × *L* adjacency matrix, **A**:

  
$$\\begin{array}{l} {A(i,j) = \\begin{cases} {1,} & {j \\in S\_{i}} \\\\ {0,} & \\text{otherwise} \\\\ \\end{cases}} \\\\ \\end{array}$$  
(5.55)

When the adjacency matrix is all ones, *A*(*i*, *j*) = 1, ∀ (*i*, *j*), then we have a fully connected graph where each vertex is connected to every other vertex and an attention mechanism with quadratic complexity. Whenever *A*(*i*, *j*) = 0, it means that edge (*i*, *j*) does not exist and thus query position *i* (**q**[*i*]) cannot attend to key position *j* (**k**[*j*]).

**Attention graph patterns** Using the graph theoretical framework, Big Bird combines three attention patterns: random attention, sliding window attention, and a global attention. Each attention pattern corresponds to a particular way of initializing the adjacency matrix.

***Random attention*** Big Bird's random attention pattern is inspired by the type of Erdős-Renyi random graph \[[84](#refbib.xhtml#refbib_84)\] that connects vertices at random with a uniform probability. In Big Bird's random attention, each query **q**[*i*] attends to a random number of keys. In terms of the adjacency matrix, *A*(*i*,  : ) = 1 for *r* key positions that are chosen at random, with equal probability. An example adjacency matrix for the random attention pattern is shown in [Fig. 5.9](#ch5.xhtml#fig5_9).

![Figure 5.9 Random adjacency matrix, for L = 12 and r = 7. Row i corresponds to query i. Columns with a • are keys that query i attends to and ⋅ represents a lack of attention (a missing edge).](images/fig5_9.jpg)

[Figure 5.9](#ch5.xhtml#b5fig5_9) Random adjacency matrix, for *L* = 12 and *r* = 7. Row *i* corresponds to query *i*. Columns with a • are keys that query *i* attends to and ⋅ represents a lack of attention (a missing edge).

***Sliding window attention*** Big Bird's local attention is derived from a Watts-Strogatz \[[265](#refbib.xhtml#refbib_265)\] small world graph on a ring lattice, where each vertex is connected to *w* neighbors, so there are *w*/2 neighbors to either side. This allows the query at position *i* to attend to keys at positions in the window \[*i* − *w*/2, *i* + *w*/2\]. In terms of the adjacency matrix, *A*(*i*, *i* − *w*/2 : *i* + *w*/2) = 1. This is similar to the sliding window attention in the Longformer that was discussed in [Sec. 5.2.2.1.1](#ch5.xhtml#sec5_2_2_1_1). An example adjacency matrix for the sliding window attention is shown in [Fig. 5.10](#ch5.xhtml#fig5_10).

![Figure 5.10 Sliding window attention adjacency matrix, for L = 12 and w = 4. Row i corresponds to query i. Columns with a • are keys that query i attends to and ⋅ represents a lack of attention (a missing edge).](images/fig5_10.jpg)

[Figure 5.10](#ch5.xhtml#b5fig5_10) Sliding window attention adjacency matrix, for *L* = 12 and *w* = 4. Row *i* corresponds to query *i*. Columns with a • are keys that query *i* attends to and ⋅ represents a lack of attention (a missing edge).

***Global attention*** Big Bird also allows some tokens to attend to all tokens in the sequence. These global tokens are also attended to by all tokens. Big Bird uses two types of global tokens: internal transformer construction and external transformer construction.

In the internal transformer construction, a subset of the *L* vertex, *G*, are promoted to global tokens. Thus the queries or keys in those positions attend to all other positions. Here, *A*(*i*,  : ) = *A*(:,*i*) = 1, ∀ *i* ∈ *G*. The expanded adjacency matrix *B* is shown in [Fig. 5.11](#ch5.xhtml#fig5_11).

![Figure 5.11 Global attention adjacency matrix for the internal transformer construction, for L = 12 and G = 3,4,7. Row i corresponds to query i. Columns with a • are keys that query i attends to and ⋅ represents a lack of attention (a missing edge).](images/fig5_11.jpg)

[Figure 5.11](#ch5.xhtml#b5fig5_11) Global attention adjacency matrix for the internal transformer construction, for *L* = 12 and *G* = 3, 4, 7. Row *i* corresponds to query *i*. Columns with a • are keys that query *i* attends to and ⋅ represents a lack of attention (a missing edge).

The external transformer construction adds *g* additional tokens to the existing *L* tokens. The additional tokens are global. Examples include special tokens used in transformers, like \[CLS\]\[CLS\]. This essentially creates a new adjacency matrix, *B*, that includes the special tokens by prepending *g* rows and columns onto *A*. Here, *B*(*i*,  : ) = *B*(:,*i*) = 1, where *i* = 1, …, *g*, and *B*(*g* + *i*, *g* + *j*) = *A*(*i*, *j*), where *i* and *j* = 1, …, *L*. The expanded adjacency matrix *B* is shown in [Fig. 5.12](#ch5.xhtml#fig5_12).

![Figure 5.12 Global attention adjacency matrix for the external transformer construction, for L = 9 and g = 3. Row i corresponds to query i. Columns with a • are keys that query i attends to and ⋅ represents a lack of attention (a missing edge).](images/fig5_12.jpg)

[Figure 5.12](#ch5.xhtml#b5fig5_12) Global attention adjacency matrix for the external transformer construction, for *L* = 9 and *g* = 3. Row *i* corresponds to query *i*. Columns with a • are keys that query *i* attends to and ⋅ represents a lack of attention (a missing edge).

Finally, an example adjacency matrix for the combination of random, sliding window, and global attention (external construction) is shown in [Fig. 5.13](#ch5.xhtml#fig5_13).

![Figure 5.13 Big Bird attention adjacency matrix for the external transformer construction, for L = 12,g = 2,w = 4, and r = 4. Row i corresponds to query i. Columns with a • are keys that query i attends to and ⋅ represents a lack of attention (a missing edge).](images/fig5_13.jpg)

[Figure 5.13](#ch5.xhtml#b5fig5_13) Big Bird attention adjacency matrix for the external transformer construction, for *L* = 12, *g* = 2, *w* = 4, and *r* = 4. Row *i* corresponds to query *i*. Columns with a • are keys that query *i* attends to and ⋅ represents a lack of attention (a missing edge).

**Efficient sparse matrix multiplication** By making the adjacency matrix (and the corresponding attention matrix) sparse, the speedups provided by GPUs are removed. This is because multiplication of matrices with arbitrary sparsity is not efficient on GPUs. However, matrices whose sparsity is grouped into blocks can be efficiently multiplied on GPUs \[[100](#refbib.xhtml#refbib_100)\].

To address this, Big Bird groups blocks of queries and keys together and then adds sparsity by block rather than by individual sequence position \[[292](#refbib.xhtml#refbib_292)\]. Select a block size, *b*, and then divide the sequence length *L* into *L*/*b* blocks. So, instead of *L* queries and keys, there will be *L*/*b* queries and keys. This modifies each attention pattern discussed above in relatively simple ways:

1.  **Random attention** The random number of keys for a query to attend to, *r*, becomes the random number of key blocks that a query block attends to.
    
2.  **Sliding window attention** The query block *i* attends to key blocks *i* − (*w* − 1)/2 through *i* + (*w* − 1)/2.
    
3.  **Global attention** The definition of global attention is unchanged, except it is defined in terms of blocks rather than sequence position.
    

### 5.2.3 Improving Multi-Head-Attention

Now we focus on some of the ways the attention mechanism has been changed to improve performance of the transformer.

#### 5.2.3.1 Talking-heads attention

Vaswani et al. \[[254](#refbib.xhtml#refbib_254)\] showed that multi-head attention allows the transformer to perform *h* (number of attention heads) separate attention calculations. Talking-Heads Attention \[[227](#refbib.xhtml#refbib_227)\] instead allows the attention heads to share information. It works by adding two linear layers that project the product of the query and key matrices, **QK**^(*T*) (attention logits), into a new space and projects the attention weights, *S**o**f**t**m**a**x*(**Q****K**^(*T*)), into a new space.

Talking-Heads Attention (THA) also partitions the attention heads into three types: heads for the queries and keys, heads for the value, and heads for the attention logits and attention weights. Let's look at this in detail.

Recall from [section 5.2.1.1](#ch5.xhtml#sec5_2_1_1) that the multi-head attention between two sequences **X**[1], **X**[2], with lengths *L*[1] and *L*[2] is:

  
$$\\begin{array}{ll} \\mathbf{Q} & {= \\mathbf{X}\_{1}\\mathbf{W}\_{q},\\, \\in {\\mathbb{R}}^{L\_{1} \\times d\_{k} \\times h}} \\\\ \\mathbf{K} & {= \\mathbf{X}\_{2}\\mathbf{W}\_{k},\\, \\in {\\mathbb{R}}^{L\_{2} \\times d\_{k} \\times h}} \\\\ \\mathbf{V} & {= \\mathbf{X}\_{2}\\mathbf{W}\_{v},\\, \\in {\\mathbb{R}}^{L\_{2} \\times d\_{v} \\times h}} \\\\ \\end{array}$$  
(5.56)

where **X**[1] ∈ ℝ^(*L*[1] × *d*), **X**[2] ∈ ℝ^(*L*[2] × *d*), **W**[*q*], **W**[*k*] ∈ ℝ^(*d* × *d*[*k*] × *h*), and **W**[*v*] ∈ ℝ^(*d* × *d*[*v*] × *h*), with

  
$$\\begin{array}{ll} \\mathbf{\\alpha} & {= \\mathbf{Q}\\mathbf{K}^{T}, \\in {\\mathbb{R}}^{L\_{1} \\times L\_{2} \\times h}} \\\\ \\end{array}$$  
(5.57)

  
$$\\begin{array}{ll} {\\mathbf{A}(\\mathbf{Q},\\mathbf{K})} & {= \\text{softmax}\\left( \\frac{\\mathbf{\\alpha}}{\\sqrt{\\text{d}\_{\\text{k}}}} \\right),\\, \\in {\\mathbb{R}}^{\\text{L}\_{\\text{1}} \\times \\text{L}\_{\\text{2}} \\times \\text{h}}} \\\\ \\end{array}$$  
(5.58)

  
$$\\begin{array}{ll} {\\mathbf{C}(\\mathbf{Q},\\mathbf{K},\\mathbf{V})} & {= {\\sum\\limits\_{L\_{2}}\\mathbf{A}}(\\mathbf{Q},\\mathbf{K})\\mathbf{V},\\, \\in {\\mathbb{R}}^{L\_{1} \\times d\_{v} \\times h}} \\\\ \\end{array}$$  
(5.59)

where *α* is the attention logits, **A**(**Q**, **K**) are the attention weights, and **C**(**Q**, **K**, **V**) is the “context” vector representing the output of the *h* attention heads prior to concatenation of the attention heads and the final projection layer.

**Partitioning the attention heads** THA modifies the attention mechanism in a few ways from that shown in (5.56)–(5.59). First, it changes the attention head dimension of **Q** and **K** to be the number of query-key attention head *h*[*k*], and changes the attention head dimension of **V** to be the number of value attention heads *h*[*v*]. This happens by changing the dimension of the projection matrices that generate the query, key, and value matrices from the input sequences. In other words, (5.56) becomes

  
$$\\begin{array}{ll} \\mathbf{Q} & {= \\mathbf{X}\_{1}\\mathbf{W}\_{q},\\, \\in {\\mathbb{R}}^{L\_{1} \\times d\_{k} \\times h\_{k}}} \\\\ \\mathbf{K} & {= \\mathbf{X}\_{2}\\mathbf{W}\_{k},\\, \\in {\\mathbb{R}}^{L\_{2} \\times d\_{k} \\times h\_{k}}} \\\\ \\mathbf{V} & {= \\mathbf{X}\_{2}\\mathbf{W}\_{v},\\, \\in {\\mathbb{R}}^{L\_{2} \\times d\_{v} \\times h\_{v}}} \\\\ \\end{array}$$  
(5.60)

where **W**[*q*], **W**[*k*] ∈ ℝ^(*d* × *d*[*k*] × *h*[*k*]), and **W**[*v*] ∈ ℝ^(*d* × *d*[*v*] × *h*[*v*]).

**Projecting the attention logits** Next, the attention logits*α* are projected with a linear layer that mixes the query-key attention heads with the attention logit/weight heads, **W**[*α*] ∈ ℝ^(*h*[*k*] × *h*), and the attention weights are projected with a linear layer that mixes the value attention heads with the attention logit/weight heads, **W**[*A*] ∈ ℝ^(*h* × *h*[*v*]). In other words, (5.57)–(5.59) becomes

  
$$\\begin{array}{l} {\\mathbf{\\alpha} = \\mathbf{Q}\\mathbf{K}^{T}, \\in {\\mathbb{R}}^{L\_{1} \\times L\_{2} \\times h\_{k}}} \\\\ \\end{array}$$  
(5.61)

  
$$\\begin{array}{l} {\\mathbf{P}\_{\\alpha} = \\mathbf{\\alpha}\\mathbf{W}\_{\\alpha},\\, \\in {\\mathbb{R}}^{L\_{1} \\times L\_{2} \\times h}} \\\\ \\end{array}$$  
(5.62)

  
$$\\begin{array}{l} {\\mathbf{A}(\\mathbf{Q},\\mathbf{K}) = \\text{softmax}\\left( \\frac{\\mathbf{P}\_{\\alpha}}{\\sqrt{\\text{d}\_{\\text{k}}}} \\right),\\, \\in {\\mathbb{R}}^{\\text{L}\_{\\text{1}} \\times \\text{L}\_{\\text{2}} \\times \\text{h}}} \\\\ \\end{array}$$  
(5.63)

  
$$\\begin{array}{l} {\\mathbf{P}\_{A}(\\mathbf{Q},\\mathbf{K}) = \\mathbf{A}\\mathbf{W}\_{A},\\, \\in {\\mathbb{R}}^{L\_{1} \\times L\_{2} \\times h\_{v}}} \\\\ \\end{array}$$  
(5.64)

  
$$\\begin{array}{l} {\\mathbf{C}(\\mathbf{Q},\\mathbf{K},\\mathbf{V}) = {\\sum\\limits\_{L\_{2}}\\mathbf{P}\_{A}}\\mathbf{V},\\, \\in {\\mathbb{R}}^{L\_{1} \\times d\_{v} \\times h\_{v}}} \\\\ \\end{array}$$  
(5.65)

where **P**[*α*] are the projected attention logits and **P**[*A*](**Q**, **K**) are the projected attention weights.

**Performance** Talking-Heads Attention (THA) was evaluated by training a T5 model using THA and the same hyperparameters as the T5 paper (except for omitting dropout during pre-training) and similarly training an ALBERT model. The authors found that THA consistently performed better than multi-head attention \[[227](#refbib.xhtml#refbib_227)\]. Just projecting the attention logits or just the attention weights is only *slightly* better than using pure multi-head attention. Significant performance increases came from using both projections. Using talking-heads attention on the encoder block's self-attention layers has a larger effect on model performance than using talking-heads attention on the decoder block's attention layers.

Multi-head attention already comes at a cost and the projections that THA adds, **W**[*α*] and **W**[*A*], increase that cost. Computing the projected attention logits, **P**[*α*], adds *L*[1] ⋅ *L*[2] ⋅ *h*[*k*] ⋅ *h* matrix multiplications and computing the projected attention weights, **P**[*A*], adds *L*[1] ⋅ *L*[2] ⋅ *h* ⋅ *h*[*v*] matrix multiplications. Together, THA adds *L*[1] ⋅ *L*[2] ⋅ *h* ⋅ (*h*[*k*] + *h*[*v*]) matrix multiplications, which will make the calculation more costly. The authors note that if *h* < *d*[*k*] and *h* < *d*[*v*], then the cost of the THA projections are less than the cost of the existing multi-head attention calculations. So, in summary, Talking-Heads Attention improves model quality at the cost of increased computation time; allowing the user to decide what kind of tradeoffs they wish to make.

### 5.2.4 Biasing Attention with Priors

This section discusses a few models that bias the attention mechanism by fixing which positions can attend to which. The Longformer model, discussed in [section 5.2.2.1](#ch5.xhtml#sec5_2_2_1), and Big Bird model, discussed in [section 5.2.2.4](#ch5.xhtml#sec5_2_2_4) are both examples of attention with priors, since each uses specific attention patterns, like sliding window attention in [sections 5.2.2.1.1](#ch5.xhtml#sec5_2_2_1_1) and [5.2.2.4.2](#ch5.xhtml#sec5_2_2_4_2). We also discussed another example of biasing attention with priors in [section 5.1.2.1](#ch5.xhtml#sec5_1_2_1), the Realformer.

### 5.2.5 Prototype Queries

#### 5.2.5.1 Clustered attention

Clustered attention \[[256](#refbib.xhtml#refbib_256)\] is a method to avoid self-attention's *O*(*L*² ⋅ *d*[*k*] + *L*² ⋅ *d*[*v*]) time complexity that linearizes the self-attention weight computation by clustering LSH hashed queries with the k-means clustering algorithm. And using the query centroids as the queries to compute the attention matrix.

**Clustering query vectors** Clustered attention happens in two stages. First, each query vector is hashed with locality-sensitive hashing. The hashed queries are then grouped into *C* clusters with k-means. The distance metric used for k-means is the Hamming distance. The centroid of the *j*^(*t**h*) cluster is given by

  
$$\\begin{array}{l} {\\mathbf{q}\_{j}^{c} = \\frac{{\\sum\\limits\_{i = 1}^{L}S\_{ij}}\\mathbf{q}\_{i}}{\\sum\\limits\_{i = 1}^{L}S\_{ij}}} \\\\ \\end{array}$$  
(5.66)

where **q**[*j*]^(*c*) is the centroid of the *j*^(*t**h*) cluster and the matrix *S* ∈ {0, 1}^(*L* × *C*) partitions the query vectors into *C* non-overlapping clusters, so if *S*[*i**j*] = 1, then **q**[*i*] is in cluster *j*. The centroid queries are grouped into **Q**^(*c*),  ∈ ℝ^(*C* × *d*[*k*]), the matrix of centroid vectors. We can then substitute the real query matrix with the query centroid matrix, **Q**^(*c*) and compute the clustered attention matrix:

  
$$\\begin{array}{l} {\\mathbf{A}^{c} = \\text{softmax}\\left( \\frac{\\mathbf{Q}^{\\text{c}}\\mathbf{K}^{\\text{T}}}{\\sqrt{(}\\text{d}\_{\\text{k}})} \\right), \\in {\\mathbb{R}}^{\\text{C} \\times \\text{L}}} \\\\ \\end{array}$$  
(5.67)

You can stop here and just use the clustered attention weights to compute the output of the attention mechanism. This calculation has time complexity of *O*(*C**L* ⋅ *d*[*k*] + *L**C* ⋅ *d*[*v*]), which is explicitly linear in the sequence length. But, the clustered attention approximation can be improved finding *k* keys that have the highest attention score within each of the *C* clusters. And, for each of the top-*k* keys for a cluster, compute the attention with the queries in that cluster:

  
$$\\begin{array}{ll} A\_{il}^{t} & {= \\begin{array}{ll} \\left\\{ \\frac{{\\hat{m}}\_{j}\\exp({\\mathbf{q}\_{i}\\mathbf{k}\_{l}\\ ^{T}})}{{\\sum\\limits\_{r = 1}^{L}T\_{jr}}\\exp({\\mathbf{q}\_{i}\\mathbf{k}\_{r}\\ ^{T}})}, \\right. & {\\text{if}\\, T\_{jl} = 1} \\\\ {A\_{jl}^{c},} & \\text{otherwise} \\\\ \\end{array}} \\\\ \\end{array}$$  
(5.68)

where ${\\hat{m}}\_{j} = {\\sum\\limits\_{i = 1}^{L}T\_{ij}}A\_{ij}^{c}$ and *T* ∈ {0, 1}^(*C* × *L*): if *T*[*i**j*] = 1, then **k**[*i*] is one of the top-k keys for in cluster *j*.

Then compute the context vectors (weighted average of the values) of the clustered attention and use it as the value matrix: **V̂** = **A**^(*t*)**V**,  ∈ ℝ^(*L* × *d*[*v*]). This makes the complexity of the clustered attention calculation to *O*(*C**L* ⋅ *d*[*k*] + *L**C* ⋅ *d*[*v*] + *k**L*max (*d*[*k*], *d*[*v*])), which is linear in the sequence length.

**Performance** Clustered attention outperforms standard transformer and Reformer on automatic speech recognition with WSJ and Switchboard audio datasets. It also approximates pre-trained RoBERTa on GLUE and SQuAD, with minute performance loss. It performs better on GLUE that RoBERTa, but not SQuAD, where it is slightly worse.

As number of clusters increases, the approximation becomes more accurate. It converges up to twice as fast as the standard transformer, for long sequence lengths and, for short sequence lengths, clustered attention is *not* faster than the standard transformer.

### 5.2.6 Compressed Key-Value Memory

#### 5.2.6.1 Luna: Linear Unified Nested Attention

Luna \[[177](#refbib.xhtml#refbib_177)\], which stands for Linear Unified Nested Attention, replaces the attention weight computation in each attention head with two nested linear attention computations using an extra, learnable, input sequence that learns to encode contextual information: **P** ∈ ℝ^(*l* × *d*), where *l* is the length of the sequence.

As discussed earlier, the output of an attention head between a query sequence, **X** ∈ ℝ^(*n* × *d*) and a context sequence, **C** ∈ ℝ^(*m* × *d*), can be written as

  
$$\\begin{array}{l} {\\mathbf{Y} = Attn(\\mathbf{X},\\mathbf{C}) = \\text{softmax}\\left( \\frac{\\mathbf{X}\\mathbf{W}\_{\\text{q}}{(\\mathbf{C}\\mathbf{W}\_{\\text{k}})}^{\\text{T}}}{\\sqrt{\\text{d}\_{\\text{k}}\\text{/h}}} \\right)\\mathbf{CV}, \\in {\\mathbb{R}}^{\\text{n} \\times \\text{d}}} \\\\ \\end{array}$$  
(5.69)

where **W**[*q*], **W**[*k*], **W**[*v*] are the linear projections that project an input sequence into the query, key, and value spaces, respectively, as in (5.24).

##### Luna attention

***Pack attention*** The first of the nested attention layers computes the attention between the extra sequence **P** and the context sequence **C**. Luna calls this “pack attention”. Its output is the “packed context”, **Y**[*P*] = *A**t**t**n*(**P**, **C**),  ∈ ℝ^(*l* × *d*), and it has the same dimensionality as **P**. It's complexity is *O*(*l**m*).

***Unpack attention*** The second of the nested attention layers computes the attention between the input sequence and the packed context sequence, **Y**[*P*]. Luna calls this the “unpack attention”: **Y**[*X*] = *A**t**t**n*(**X**, **Y**[*P*]),  ∈ ℝ^(*n* × *d*). Its output has the same dimensionality as the input sequence **X**. It's complexity is *O*(*l**n*).

***Luna attention*** Luna combines the pack and unpack attention layers in sequence, forming the Luna layer: **Y**[*X*], **Y**[*P*] = *L**u**n**a**A**t**t**n*(**X**, **P**, **C**), which encompasses the two multi-head attention layers shown in [Fig. 5.14](#ch5.xhtml#fig5_14). **P** is initialized to the transformer's positional encodings, and for subsequent transformer blocks, **Y**[*P*] is used in place of **P**.

![Figure 5.14 Architecture of a Luna encoder block. P is the extra sequence for the block and X is the input sequence of the block. P′ will be the extra sequence for the next Luna block and P′ will be the input sequence of the next Luna block.](images/fig5_14.jpg)

[Figure 5.14](#ch5.xhtml#b5fig5_14) Architecture of a Luna encoder block. **P** is the extra sequence for the block and **X** is the input sequence of the block. **P**^′ will be the extra sequence for the next Luna block and **P**^′ will be the input sequence of the next Luna block.

Because the pack attention and unpack attention layers are composed in sequence, their combined complexity is *O*(*l**m* + *l**n*). Since the extra input sequence **P** has fixed length, the combined complexity of Luna's multi-head attention mechanism is linear in the length of the input sequence **X**. With slight modifications, Luna can also support causal cross-attention.

**Performance** Luna was compared to the performance of the standard transformer and 11 other efficient transformers on the Long Range Arena benchmark (LRA) \[[242](#refbib.xhtml#refbib_242)\]. It performed well on all tasks, outperforming most, but not all, models; obtaining the highest average accuracy. Luna was consistently faster than the standard transformer and many, but not all, of the efficient transformers to which it was compared. It was also more memory efficient than the standard transformer, with memory usage comparable to other efficient transformers and beating a few.

### 5.2.7 Low-Rank Approximations

#### 5.2.7.1 Linformer

In \[[259](#refbib.xhtml#refbib_259)\], Wang et al. prove that the standard transformer's \[[254](#refbib.xhtml#refbib_254)\] self-attention weight matrix can be approximated with a low-rank matrix \[[83](#refbib.xhtml#refbib_83)\], reducing the complexity from *O*(*L*²) to *O*(*L*), where *L* is the sequence length.

Linformer introduces two linear projection matrices that transform the key and value matrices of the *i*^(*t**h*) attention head: **E**[*i*] = *δ***R** and **F**[*i*] = exp^( − *δ*)**R**, where **R** ∈ ℝ^(*k* × *L*) and its components are drawn from 𝒩(0, 1/*k*), *δ* = *θ*(1/*L*), *k* = 5log (*d**L*)/(*ϵ*² − *ϵ*³), and *ϵ* is the approximation error. Also, *d*[*k*] = *d*[*v*] = *d*. This approximation means that the output of each attention head in the mechanism can be approximated by ${\\overline{head}}\_{i} = {\\overline{\\mathbf{A}}}\_{i} \\cdot \\mathbf{F}\_{i}\\mathbf{V}\_{i}$, where

  
$$\\begin{array}{l} {{\\overline{\\mathbf{A}}}\_{i} = \\text{softmax}\\left( \\frac{\\mathbf{Q}\_{\\text{i}}{(\\mathbf{E}\_{\\text{i}}\\mathbf{K}\_{\\text{i}})}^{\\text{T}}}{\\sqrt{\\text{d}\_{\\text{k}}\\text{/h}}} \\right), \\in {\\mathbb{R}}^{\\text{L} \\times \\text{k}}} \\\\ \\end{array}$$  
(5.70)

${\\overline{A}}\_{i}$ is a low-rank approximation of the attention weight matrix for the *i*^(*t**h*) attention head. It's complexity is *O*(*k**L*), which is why Linformer is also a way of reducing the space and time complexity of the attention mechanism and thus fits in with the methods discussed in [section 5.2](#ch5.xhtml#sec5_2).

The authors consider three variants of parameter sharing to make Linformer even more efficient:

1.  Share E and F across all attention heads (headwise sharing): **E**[*i*] = **E**, **F**[*i*] = **F**
    
2.  Share projections across heads and key/value matrices: **E**[*i*] = **F**[*i*] = **E**
    
3.  Share projections across heads, key/value matrices, and model layers (layerwise sharing)
    

Inference speed was first tested against the standard transformer \[[254](#refbib.xhtml#refbib_254)\]. As sequence length *L* increased, the standard transformer became slower. The Linformer speed remained largely constant and was significantly faster for long sequences. Wang et al. kept the sequence length fixed and varied the batch size to process the text sequences. This behavior is expected since the sequence length was held fixed.

To test performance, Linformer was trained in the same way as RoBERTa \[[170](#refbib.xhtml#refbib_170)\] and compared using validation perplexities and performance on downstream tasks. Based on perplexities, Linformer performance increases as k increases and Linformer's quality nearly matches that of the standard transformer for *L* = 512, *k* = 128 and *L* = 1024, *k* = 256. Based on downstream task performance, Linformer performance is comparable to RoBERTa when *L* = 512, *k* = 128, and outperforms RoBERTa at *k* = 256. Performance for *L* = 1024, *k* = 256 and *L* = 512, *k* = 256 are similar, suggesting that performance for Linformer is controlled more by *k* than by *L*/*k*. There are two key results:

1.  Layerwise parameter sharing performs the best.
    
2.  Performance when using layerwise sharing is nearly identical to the performance of using no parameter sharing. This suggests that the number of parameters introduced by Linformer can be reduced without quality taking a hit.
    

The Performer model, which was discussed in [section 5.2.2.3](#ch5.xhtml#sec5_2_2_3), is also based on a low-rank approximations of attention.

## 5.3 Modifications for Training Task Efficiency

### 5.3.1 Electra

ELECTRA \[[58](#refbib.xhtml#refbib_58)\] introduces a new pre-training task, replaced token detection, that combines the best of masked language models and regular language models, allowing ELECTRA to learn more efficiently than its predecessors. ELECTRA is a bidirectional model, like a masked language model. However, unlike a masked language model, it learns from all positions in the input sequence.

#### 5.3.1.1 Replaced token detection

Replaced token detection (RTD) helps the model learn which tokens are most likely to be in a given position in a sequence because the model learns to replace and identify each token in the training data. In this way, ELECTRA is like the discriminator in a Generative adversarial network (GAN). Here, unlike a GAN, the generator is not being trained to trick the discriminator and a noise vector is not added to the generator's input.

ELECTRA is trained using combination of a generator and a discriminator. The generator is a masked language model and the discriminator is ELECTRA itself. As a result, ELECTRA needs less training data than earlier masked language models, like BERT, because masked language models do not mask every token in the training data. Generator and discriminator are both transformer encoders.

Training begins with the generator chooses a random set of *k* positions, **m** = (*m*[1], …, *m*[*k*]), from the input sequence, such that each position *m*[*i*], with *i* = 1, …, *k*, is drawn uniformly from *\[*1,*L\]*, where *L* is the sequence length. Each token in the input sequence **x** = (*x*[1], …, *x*[*L*]) that is at the positions in **m** will be replaced with the \[MASK\] token. The masked sequence is

  
$$\\begin{array}{l} {\\mathbf{x}^{\\text{masked}} = \\text{REPLACE}(\\mathbf{x},\\mathbf{m},\\lbrack MASK\\rbrack)} \\\\ \\end{array}$$  
(5.71)

The generator then learns the unmasked versions of the masked tokens in **x**. The probability that the generator outputs a particular token *x*[*t*] is

  
$$\\begin{array}{l} {Prob\_{G}(x\_{t}|\\mathbf{x}) = \\frac{\\exp({\\mathbf{e}\_{t}^{T}\\mathbf{h}\_{G}{(\\mathbf{x})}\_{t}})}{{\\sum\\limits\_{t^{\\prime}}{\\exp}}({\\mathbf{e}{(x^{\\prime})}^{T}\\mathbf{h}\_{G}{(\\mathbf{x})}\_{t}})},} \\\\ \\end{array}$$  
(5.72)

where **e**[*t*] is the embedding vector for the token *x*[*t*].

The discriminator learns to tell which tokens in a sequence were produced by the generator. This works by creating a sequence where the masked tokens have been replaced with samples (“corrupt” tokens) from the generator:

  
$$\\begin{array}{l} {\\mathbf{x}^{\\text{c}} = \\text{REPLACE}(\\mathbf{x},\\mathbf{m},\\mathbf{\\hat{x}}\_{i})} \\\\ \\end{array}$$  
(5.73)

where **x̂**[*i*] are the tokens generated by the generator:

  
$$\\begin{array}{l} {\\mathbf{\\hat{x}}\_{i} \\sim Prob\_{G}(x\_{i}|\\mathbf{x}^{\\text{masked}})} \\\\ \\end{array}$$  
(5.74)

where *i* ∈ **m**. The discriminator then learns to identify which tokens in **x**^c were in the original input **x**. Here, unlike a GAN, the generator is not being trained to trick the discriminator and a noise vector is not added to the generator's input.

### 5.3.2 T5

T5, the Text-to-Text Transfer Transformer \[[205](#refbib.xhtml#refbib_205)\], is the result of a survey aimed at understanding which transfer learning methods work best. It reframed standard NLP tasks as text-to-text transformations, where the input and output are strings. This is in contrast to masked language models like BERT, which output either class labels or a span of the input.

The reformulation of training tasks means you can use the same model and loss function on any NLP task. Using text-to-text transformations (sequence transduction) allows you to train one model on multiple tasks at once, reusing model architecture, loss functions, and hyperparameters. Appendix D of Raffel et al. has examples of how input was formatted for each of the datasets the T5 model was trained or fine-tuned on.

## 5.4 Transformer Submodule Changes

This section discusses modifications to the Transformer that do not modify the attention mechanism or the model's memory profile.

### 5.4.1 Switch Transformer

The Mixture of Experts (MoE) model has contributed to many successes at the expense of complexity and training cost \[[225](#refbib.xhtml#refbib_225)\]. However, the mixture of expert models does not share the parameters, resulting in a sparse model with a substantial computational cost and training instabilities. Switch transformers address most of these issues with a novel routing algorithm between the experts, enabling an increase in the number of the parameters without an increase in computational cost \[[87](#refbib.xhtml#refbib_87)\]. The core innovation of switch transformers is replacing the feed-forward layer in the transformer with a switching feed-forward layer, as shown in [Fig. 5.15](#ch5.xhtml#fig5_15).

![Figure 5.15 Switch Transformer encoder block illustrating two input tokens x1 and x2 being processed through the network. The dense FFN is replaced with switching FFN as one of the experts.](images/fig5_15.jpg)

[Figure 5.15](#ch5.xhtml#b5fig5_15) Switch Transformer encoder block illustrating two input tokens **x**[1] and **x**[2] being processed through the network. The dense FFN is replaced with switching FFN as one of the experts.

In the standard transformer, a single feed-forward network follows the outputs from the multi-head attention layer. It is responsible for translating the representation token-by-token to the next transformer input block. As shown in [Fig. 5.15](#ch5.xhtml#fig5_15), in a switch transformer, instead of one feed-forward network, there are multiple feed-forward networks, also known as the experts. After the multi-head attention, each token representation, **x**, gets routed to only *one* expert. The expert is chosen from a set of *N* experts, {*E*[*i*](**x**)}[*i* = 1]^(*N*) by computing a probability distribution over the experts:

  
$$\\begin{array}{l} {\\mathbf{p}(\\mathbf{x}) = \\text{softmax}({\\mathbf{W}\_{\\text{r}} \\cdot \\mathbf{x}})} \\\\ \\end{array}$$  
(5.75)

where **W**[*r*] ∈ ℝ^(*N* × *d*) is a learnable weight matrix that determines which expert is selected and *d* is the dimensionality of the token representation, **x**. The expert with largest probability corresponds to the largest component of 5.75: **p**(**x**) = (*p*[1], …, *p*[*N*]), call it *p*[*j*], and is used to compute the updated token representation. Thus, though the parameters have increased four times because of four feed-forward networks, hard routing guarantees that the computational cost remains the same. Thus the switching feed-forward network enables the scaling of experts to any number (bound by memory capacity) without increasing computational cost and not needing any transfer helps in the sharding process.

Model parallelism shards the model across the devices (cores/machines) while consuming the same data in the batch, resulting in a large model with slower processing due to sequential flow; the bottleneck introduced by communication. On the other hand, data parallelism keeps the model weights constant and shards the data across, allowing improved computational speed but a lower capacity model due to size. Switch Transformer employs data and expert parallelism—i.e., each data gets sharded to one expert on one device, which uses its expert weights for computations. The experts themselves are distributed and not communicating with each other, resulting in total parallelism and lower computation overheads. The authors use experts, data, and model parallelism to scale up to a gigantic model where even a single expert doesn't fit a device.

Compared to T5-Base and T5-large, the switch transformers show that given the same FLOPS, the models can be substantially large and excel across a diverse set of natural language tasks and in different training regimes, such as pre-training, fine-tuning and multi-task training. The multilingual results are more impressive as they show the gain compared to an equivalent MT5 model across 101 languages.

## 5.5 Case Study: Sentiment Analysis

### 5.5.1 Goal

This case study examines the attention weights of a T5 model that was fine-tuned for sentiment span extraction. The input to this span extraction model is a span of text containing positive or negative sentiment. The output is the subsequence of the input text that causes the span to have the specified sentiment.

### 5.5.2 Data, Tools, and Libraries

![Listing 5.1 Python environment setup](images/comp5_1.jpg)

[Listing 5.1](#ch5.xhtml#b5list5_1) Python environment setup

To use this model, we'll need three Python libraries: Huggingface's transformers, Google's sentencepiece, and the bertviz library. They can be installed by running the shell command shown in [Listing 5.1](#ch5.xhtml#list5_1). Once the environment is setup, the model and tokenizer can be loaded into memory, as shown in [Listing 5.2](#ch5.xhtml#list5_2).

![Listing 5.2 Load model and tokenizer](images/comp5_2.jpg)

[Listing 5.2](#ch5.xhtml#b5list5_2) Load model and tokenizer

To make extract sentiment spans with this model, you can use the function defined in [Listing 5.3](#ch5.xhtml#list5_3).

![Listing 5.3 Extract sentiment span from input text](images/comp5_3.jpg)

[Listing 5.3](#ch5.xhtml#b5list5_3) Extract sentiment span from input text

The model takes input in the following form:

  
$$\\begin{array}{l} {\\text{question}:\\lbrack\\text{positive/negative}\\rbrack\\text{context}:\\lbrack\\text{textofspecifiedsentiment}\\rbrack.} \\\\ \\end{array}$$  

This case study focuses on positive sentiment in a sequence of text with both positive and negative sentiment. The text is *“You're a nice person, but your feet stink.”* Thus, for positive sentiment, the full input text to the span extraction model is *“question: positive context: You're a nice person, but your feet stink.”*

### 5.5.3 Experiments, Results, and Analysis

There are a variety of methods that have been used to analyze the influence of attention mechanisms on model output.

We will look at just one: simply visualizing attention weights (with BertViz \[[255](#refbib.xhtml#refbib_255)\]).

#### 5.5.3.1 Visualizing attention head weights

The T5 model has 12 layers, each of which has three attention mechanisms:

1.  encoder self-attention
    
2.  decoder self-attention
    
3.  cross-attention
    

Each attention mechanism has 12 heads, and thus has 144 sets of attention weights, one for each choice of layer and attention head. We'll use the BertViz \[[255](#refbib.xhtml#refbib_255)\] library to view the weights of the attention heads, this is shown in [Listing 5.4](#ch5.xhtml#list5_4).

![](images/comp5_4.jpg)![](images/comp5_4a.jpg)![Listing 5.4 Visualizing attention weights](images/comp5_4b.jpg)

[Listing 5.4](#ch5.xhtml#b5list5_4) Visualizing attention weights

For starters, we want to see if the weights of any of the attention heads show the word “positive” in the input text attending to any of the tokens in the extracted subsequence.

We can see that “positive” attends to “nice” in three heads of the encoder attention. These are shown in [Fig. 5.16](#ch5.xhtml#fig5_16). In five heads of the cross-attention mechanism, “positive” and “nice” both attend to “person”. These are shown in [Fig. 5.17](#ch5.xhtml#fig5_17).

![Figure 5.16 Encoder attention heads from layers 3 (head 5), 4 (head 11), and 6 (head 11), from left to right.](images/fig5_16.jpg)

[Figure 5.16](#ch5.xhtml#b5fig5_16) Encoder attention heads from layers 3 (head 5), 4 (head 11), and 6 (head 11), from left to right.

![Figure 5.17 Cross-attention heads from layers 8, 9, and 10. The top row shows heads 1, 2, and 11 of layer 8 (left to right). The bottom row shows head 0 of layer 9 and head 1 of layer 10.](images/fig5_17.jpg)

[Figure 5.17](#ch5.xhtml#b5fig5_17) Cross-attention heads from layers 8, 9, and 10. The top row shows heads 1, 2, and 11 of layer 8 (left to right). The bottom row shows head 0 of layer 9 and head 1 of layer 10.

#### 5.5.3.2 Analysis

While there are 11 attention heads (out of 432) that show strong attention between “positive” and attention, there are even more that do not. Many of the other attention heads in the span extraction model fall into the type of attention patterns shown in \[[57](#refbib.xhtml#refbib_57)\], particularly the broad attention where each token attends to nearly every other token and the type where each token attends to the following token.

The analysis above calls into question the ability to use attention weights themselves to explain predictions. And recently, \[[143](#refbib.xhtml#refbib_143)\] found the attention weight analysis shown above to be a poor method for analyzing an attention mechanism. There are several papers that suggest other analysis methods. We'll describe one of them below.

**Attention mechanism output norm** Analyzing an attention mechanism using the norm of the components of its output was suggested by \[[143](#refbib.xhtml#refbib_143)\]. Recall (5.29), which shows how self-attention is defined in the standard transformer, for a single attention head. As shown in (2.19), after the attention heads are concatenated, we apply a linear layer to obtain the output of the attention mechanism. The linear layer has weights **W**[*O*], giving the mechanism the following output:

  
$$\\begin{array}{ll} \\mathbf{y}\_{i} & {= \\left( {{\\sum\\limits\_{j = 1}^{L}A\_{ij}}\\mathbf{v}(\\mathbf{x}\_{j})} \\right)\\mathbf{W}\_{O}} \\\\ \\end{array}$$  
(5.76)

  
$$\\begin{array}{ll} \\ & {= {\\sum\\limits\_{j = 1}^{L}A\_{ij}}\\mathbf{f}(\\mathbf{x}\_{j})} \\\\ \\end{array}$$  
(5.77)

where *A*[*i**j*] are the attention weights from (5.27), **v**(**x**[*j*]) is a value vector from 5.25, and *f*(**x**[*j*]) = **v**(**x**[*j*])**W**[*O*]. *f*(**x**[*j*]) is the output of the attention mechanism corresponding to the *j*^(*t**h*) input token **x**[*j*].

In \[[143](#refbib.xhtml#refbib_143)\], Kobayashi et al. specifically suggest using ||*A*[*i**j*]*f*(**x**[*j*])|| as it's the degree to which token *i* attends to token *j*. They also show that ||*f*(**x**[*j*])|| and *A*[*i**j*] are meaningful quantities and sometimes play opposing roles in determining model behavior.

# CHAPTER 6Pre-trained and Application-Specific Transformers

DOI: [10.1201/9781003170082-6](https://doi.org/10.1201/9781003170082-6)

THE transformer architecture was introduced as a language model that transformed text in one language into text in another language \[[254](#refbib.xhtml#refbib_254)\]. Since that initial application to machine translation, the transformer architecture has been applied to computer vision, audio processing, and video processing, as well as other problems in NLP. The transformer architecture has been shown to be a somewhat reliable way of taking in an input sequence and converting it into something else.

## 6.1 Text Processing

This section describes some of the ways that transformers have been applied to domain-specific text processing and a recent advancement made in text sequence to text sequence processing.

### 6.1.1 Domain-Specific Transformers

Transformers have been made for domain-specific applications by fine-tuning pre-trained models like BERT. We'll look at a few.

#### 6.1.1.1 BioBERT

BioBERT \[[152](#refbib.xhtml#refbib_152)\] is domain-specific language model constructed by fine-tuning BERT on a large collection of biomedical text. BioBERT was created because ELMo and BERT did not perform well on biomedical text because their training data did not include it. BioBERT outperformed previous models on three NLP tasks useful for biomedical text mining: named entity recognition (NER), relationship extraction, and question answering (QA).

There are three steps to go from a pre-trained BERT model to a BioBERT model. The starting point is a pre-trained BERT model. The next step is to pre-train the model on PubMed abstracts and PubMed Central full-text articles. Finally, after the pre-training is over, BioBERT is further fine-tuned on the NER, relationship extraction, and question answering tasks, using task-specific datasets.

BioBERT used the cased BERT vocabulary, unchanged. Had they not done this, they would not have been able to start with a pre-trained BERT model. BioBERT was trained in 23 days, on eight NVIDIA Volta V100 GPUs.

#### 6.1.1.2 SciBERT

SciBERT \[[24](#refbib.xhtml#refbib_24)\] is a language model built to process scientific text. It uses the BERT architecture, but was trained on the full text and abstracts of 1.4 million papers from the Semantic Scholar website ([semanticscholar.org](http://semanticscholar.org)).

Like BERT, SciBERT uses WordPiece tokenization with 30,000 tokens, but it does not use BERT's vocabulary. Instead, SciBERT's vocabulary is built from Semantic Scholar corpus. SciBERT was evaluated on five NLP tasks: NER, PICO extraction, text classification, relationship extraction, and dependency parsing. PICO extraction is a sequence labeling task applied to papers about clinical trials where a model extracts spans that mention the participants, interventions, comparisons, or outcomes of a clinical trial. Training took one week on single 8-core TPU.

#### 6.1.1.3 FinBERT

With the ULMFit model \[[119](#refbib.xhtml#refbib_119)\], Howard and Ruder showed that tuning an already pre-trained language model on a corpus from a target domain results in improved classification metrics. FinBERT \[[7](#refbib.xhtml#refbib_7)\] is the result of seeing if the same idea can be applied to BERT, with equal or greater success. FinBERT attempts this in two ways: (1) further pre-train on a large financial corpus and (2) pre-train only on the sentences from a financial sentiment analysis corpus. For pre-training, FinBERT uses a subset of the Reuters TRC2 dataset that has been filtered for financial keywords. The resulting corpus has more than 29M words, across 46,143 documents. For sentiment analysis, the Financial Phrasebank dataset is used. It has 4845 sentences from LexisNexis.

### 6.1.2 Text-to-Text Transformers

As discussed in [section 5.3](#ch5.xhtml#sec5_3), the T5 model from Raffel et al. \[[205](#refbib.xhtml#refbib_205)\] reframed standard NLP tasks as text-to-text transformations, where the input and output are strings. Since the introduction of T5, there have been two important advancements: a multilingual version named mT5\[[281](#refbib.xhtml#refbib_281)\], supporting 101 languages, and a token-free variant that operates directly on UTF-8 bytes, ByT5 \[[280](#refbib.xhtml#refbib_280)\]. In this section, we discuss ByT5.

#### 6.1.2.1 ByT5

ByT5 \[[280](#refbib.xhtml#refbib_280)\] is a byte-level model, to take advantage of strings being encoded as a sequence of UTF-8 bytes. Part of the motivation for this ByT5 was that token-free models would be more robust to out-of-vocabulary words, misspellings, casing, and morphological changes. A token-free model would not use a fixed vocabulary to map test to tokens. A byte-level model would only need 256 embedding vectors, rather than the large number needed when using a fixed vocabulary. The massive decrease in vocabulary size that comes with using bytes means more parameters can be used elsewhere in the model.

Since byte sequences are longer than token sequences and transformer computational complexity is quadratic in sequence length (except for linearized attention), earlier work has tried to mitigate the increased complexity that comes with using byte-level and character-level sequences. ByT5 starts with the mT5 architecture, but differs from mT5 in a few ways. Firstly, there is no SentencePiece tokenization. Raw UTF-8 bytes are used as input and embeddings are learned for each of the 256 bytes. In addition, there are three special tokens added to the vocabulary: a padding token, an EOS token, and an unknown token. The pre-training task is changed so that the length of the masked portion of input spans is longer than in is in T5. in T5, the encoder and decoder modules have the same number of layers. That restriction is removed in ByT5 and it the encoder is three times as many layers as the decoder. Lastly, illegal UTF-8 bytes are removed from the output.

As discussed above, robustness is one of the hypothesized benefits of working with bytes instead of tokens. To test the hypothesized robustness, they authors add six kinds of noise to the data and see how it affects performance:

1.  Make deletions by giving each character has a 10% chance of being deleted.
    
2.  Give each character a 10% chance of added, deleted, or mutated (with equal likelihood).
    
3.  Give each character a 20% chance of being duplicated 1-3 times.
    
4.  Capitalize each character and pad it with spaces.
    
5.  Make each character uppercase, when the language uses case.
    
6.  Set the case of each character randomly when the language uses case.
    

The noise is injected in one of two ways: into the fine-tuning and evaluation data or just into the evaluation data. For the question answering task, noise is added to the context but not to the question or answer. For the sentence entailment training task, noise is added to the premise and hypothesis. For both types of noise, the paper shows that ByT5 is indeed more robust to noise than mT5.

### 6.1.3 Text Generation

One of the most well-known successes of transformer-based language models has been text generation with the GPT-2 and GPT-3 language models, which are built from stacks of transformer-decoder layers.

#### 6.1.3.1 GPT: Generative pre-training

The family of generative pre-training models are part of the language modeling trend where a model is first trained on unsupervised data, in a task-agnostic fashion, and later fine-tuned for a specific task. The first model in this family, the eponymous GPT \[[202](#refbib.xhtml#refbib_202)\], first pre-trains a stack of transformer decoder layers on a large body of unlabeled text and is then fine-tuned on labeled, task-specific data. GPT is an autoregressive model, which means it uses inputs from previous steps of a sequence to predict values later in the sequence. GPT was evaluated on four kinds of natural language understanding tasks: natural language inference, question answering, semantic similarity, and text classification.

**Unsupervised pre-training** In this phase, GPT starts with a corpus of tokens and, moving through it, learns how to predict the next token, given some preceding context. More formally, given an unlabeled corpus *U* = (*w*[1],…,*w*[*n*]), the model learns the conditional probability of predicting token *w*[*t*] given the preceding *k* tokens, *P*(*w*[*t*]|*w*[*t* − 1],…,*w*[*t* − *k*]), by minimizing the negative log-likelihood

  
$$\\begin{array}{l} {L\_{1}(U) = - {\\sum\\limits\_{t}{\\log}}P(w\_{t}|w\_{t - 1},\\ldots,w\_{t - k};\\Theta)} \\\\ \\end{array}$$  
(6.1)

where Θ represents the model parameters. Optimization was with stochastic gradient descent.

**Supervised fine-tuning** In this phase, the model is fine-tuned on labeled, task-specific corpus, *C*, where each data point is a token sequence **x** = (*x*[1], …, *x*[*m*]) and a class label *y*. The pre-trained decoder model is used as a feature generator for the labeled data and a fully-connected linear layer, with softmax activation and weight matrix **W**, is appended to it and trained by minimizing a second negative log-likelihood

  
$$\\begin{array}{l} {L\_{2}(C) = - {\\sum\\limits\_{(\\mathbf{x},y)}{\\log}}P(y|\\mathbf{x};\\mathbf{W})} \\\\ \\end{array}$$  
(6.2)

Radford et al. found that the model converged faster and generalized better when the language modeling objective from the unsupervised phase, (6.1), was added to (6.2). So, the full objective was the weighted sum *L*[2](*C*) + *λ**L*[1](*C*).

*Formatting data for fine-tuning*Data for each of the four training tasks is formatted differently:

*   Text classification data has a simple format; each instance is bracketed with a start and an end token, so the input is formatted like \[⟨*s*⟩, *t**e**x**t*, ⟨/*s*⟩\].
    
*   A natural language inference (NLI) instance has two parts, the premise, *p*, and the hypothesis, *h*. Labels can be entailment, contradiction, or neutral. The input is formatted like \[⟨*s*⟩, *p*, &$, *h*, ⟨/*s*⟩\], where $ is a delimiter token.
    
*   A text similarity instance has two text sequences, which can be in any order; so both orders are included. The input is formatted like an entailment instance.
    
*   For question-answering and commonsense reasoning, AKA multiple-choice questions, each instance is context sequence, a question, and a set of *k* possible answers, {*a*[*k*]}. From one such instance, *k* model inputs are constructed by concatenating the context, the question, the $ delimiter token, and one of the possible answers. Each is used as a separate input.
    

Model training The model was a stack of 12 transformer decoder layers, with 12 masked self-attention heads. Model dimension is 768, the feedforward layers use *d*[*f**f*] = 3072. Positional embeddings were learned, instead of the fixed embeddings used in the standard Transformer.

*Pre-training data* Language model pre-training was on the BooksCorpus \[[303](#refbib.xhtml#refbib_303)\] and 1B Word Benchmark \[[197](#refbib.xhtml#refbib_197)\] datasets.

*Fine-tuning data* Some of the data was from the GLUE multi-task benchmark \[[257](#refbib.xhtml#refbib_257)\]. Five NLI datasets were used: SNLI, MNLI, QNLI, SciTail, and RTE. Multiple-choice data was from the RACE dataset \[[145](#refbib.xhtml#refbib_145)\]. Evaluation was on the Story Cloze Test dataset \[[190](#refbib.xhtml#refbib_190)\]. Semantic Similarity was on the Microsoft Paraphrase corpus (MRPC) \[[75](#refbib.xhtml#refbib_75)\], the Quora Question Pairs (QQP) dataset \[[43](#refbib.xhtml#refbib_43)\], and Semantic Textual Similarity benchmark (STS-B) \[[38](#refbib.xhtml#refbib_38)\]. Text classification was evaluated on The Corpus of Linguistic Acceptability (CoLA) \[[264](#refbib.xhtml#refbib_264)\] and Stanford Sentiment Treebank (SST-2) \[[230](#refbib.xhtml#refbib_230)\].

#### 6.1.3.2 Gpt-2

If the first GPT model demonstrated the power of generative pre-training, then GPT-2 \[[203](#refbib.xhtml#refbib_203)\] showed that a language model can learn specific NLP tasks without being explicitly trained on those tasks. This is the same kind of zero-shot application of a model discussed in [Chapters 3](#ch3.xhtml) and [4](#ch4.xhtml).

Model architecture Similar to GPT, GPT-2 uses a stack of transformer decoder blocks. The decoders are slightly modified. In the standard transformer, the layer norm module comes after the multi-head attention and after the position-wise feedforward network, as part of the residual connection. In GPT-2, the layer norm module instead comes before the multi-head attention and before the position-wise feedforward. The residual connection now only includes addition, rather than addition and layer norm. One additional layer norm module is placed in the final decoder block, after the multi-head attention. The weights of the residual layers are initialized differently than in the GPT model. The weights for a residual layer are divided by $1/\\sqrt{N}$, where *N* is the number of residual layers in the entire model.

GPT-2 uses byte-pair encoding (BPE) tokenization \[[92](#refbib.xhtml#refbib_92)\] so that any UTF-8 string can be represented using a vocabulary that of only 256 bytes. Computing with the raw UTF-8 bytes was not done here, since byte-level language models were not performing at the level of word-level language models. 

Four variants with the described architecture were trained. The largest model of the four is the one called ”GPT-2”. It has 1.542 billion parameters and uses 48 transformer decoder layers. Each was evaluated on several language modeling datasets without any additional training. GPT-2 achieved state-of-the-art on seven out of eight datasets.

#### 6.1.3.3 GPT-3

GPT-3 \[[32](#refbib.xhtml#refbib_32)\] is part of the trend in transformer language models where an increase in the number of parameters leads to an increase in the language model's ability to perform downstream tasks with little to no task-specific training.

**Model architecture** GPT-3 uses the same model architecture as GPT-2, with one exception: the attention mechanisms in the transformer layers alternated between dense and locally banded sparse patterns. The sparse banded pattern was used in the Sparse Transformer \[[50](#refbib.xhtml#refbib_50)\] by only computing attention between a sparse selection of query-key pairs.

To study the effect of parameter count in-context learning, Brown et al. trained eight models of different sizes. The smallest model, “GPT-3 Small” had 125 million parameters, 12 Transformer decoder layers, model dimension of 768, 12 attention heads, each attention head had dimension of 64 (*d*[*k*] = *d*[*v*] = 64), processed tokens in batches of 500,000, and used learning rate 6e-4. The largest model, “GPT-3 175B” or just “GPT-3”, had 175 billion parameters, 96 Transformer decoder layers, model dimension of 12288, 96 attention heads, head dimension of 128 (*d*[*k*] = *d*[*v*] = 128), processed tokens in batches of 3.2 million, and used learning rate 0.6e-4. GPT-3 had over 1000 times as many parameters as GPT-3 small. All models were trained on 300 billion tokens and used a context window of 2048 tokens. Note that the position-wise feedforward network had *d*[*f**f*] = 4*d*[*m**o**d**e**l*]. Larger models using larger batch sizes used smaller learning rates.

**Performance** Several sizes of GPT-3 models were evaluated for zero-, one-, and few-shot learning, which Brown et al. describe as different types of in-context learning. With the few-shot type of learning, GPT-3 gives the model as many examples of the desired task that will fit into the context window (10–100 examples). One-shot learning then provides one example and a task description, while zero-shot provides no examples, only a task description. There is no gradient updating or fine-tuning. The model is assessed on 12 NLP datasets.

Results showed that as the number of model parameters increases, the model needs fewer demonstrations to learn how to perform a task (and hence to reach a given accuracy target). When few-shot is used, model performance increases more quickly with model size, suggesting larger models are better at in-context learning.

*Evaluation and conditioning the model* For few-shot, *K* examples were randomly drawn from the training set (or dev set if there was no labeled training set) to be used as conditioning, separated by 1–2 newlines. *K* varied from 0 to the size of the context window. Some examples just have a description of the task used as conditioning. For multiple-choice tasks, *K* examples of context with the correct choice were used as conditioning and one additional example of context only was the item to be completed. As with GPT-2, the language model likelihood score for each possible completion was scored. Binary classification was usually treated as a multiple-choice question, where the possible answers were meaningful words, like “positive” or “negative”. In some cases, this task was formatted the way it is for the T5 model. Fill-in-the-blank tasks were completed using beam search. See the seminal paper for examples from every dataset used to evaluate GPT-3.

Each of the sizes of GPT-3 models were also tested on several other tasks using zero-, one-, or few-shot conditioning: unscrambling words, SAT analogies, arithmetic, using unusual words in a sentence after seeing the word defined, generate news article text, and correcting English grammar.

## 6.2 Computer Vision

The most obvious application of transformers to image processing is image recognition (AKA image classification). Prior to transformers, the highest quality in image recognition came from convolutional neural networks (CNNs) \[[150](#refbib.xhtml#refbib_150)\]. There are a few pure transformer models applied to image recognition that are competitive with state-of-the-art CNN models. In this section, we focus on the Vision Transformer (ViT) \[[78](#refbib.xhtml#refbib_78)\], which was introduced to see how effective pure transformer models could be for computer vision.

### 6.2.1 Vision Transformer

Given an image with resolution *H* × *W* and *C* channels, the image can be represented by **x** ∈ ℝ^(*H* × *W* × *C*). ViT starts by breaking the two-dimensional image into a sequence of *N* image patches, **x**[*p*] ∈ ℝ^(*N* × (*P*² ⋅ *C*)), with resolution *P* × *P*, where *N* = *H**W*/*P*². The sequence of image patches is like the token sequence in the standard transformer \[[254](#refbib.xhtml#refbib_254)\].

Before sending the patch sequence through the embedding layer, a learnable embedding analogous to the *\[CLS\]* token in BERT, **x**[*c**l**s*] is prepended onto each patch vector. So **x**[*p*]→\[**x**[*c**l**s*];**x**[*p*]\]. Using the embedding layer, **E** ∈ ℝ^((*P*² ⋅ *C*) × *D*), and one-dimensional positional encodings, **E**[*p**o**s*] ∈ ℝ^((*N* + 1) × *D*), we compute the input to the Transformer. *D* is the Transformer hidden size.

  
$$\\begin{array}{l} {\\mathbf{z}\_{0} = \\lbrack\\mathbf{x}\_{cls};\\mathbf{x}\_{p}^{(1)}\\mathbf{E};\\cdots;\\mathbf{x}\_{p}^{(N)}\\mathbf{E}\\rbrack + \\mathbf{E}\_{pos}} \\\\ \\end{array}$$  
(6.3)

From here, **z**[0] is passed into a mostly standard transformer encoder architecture with *L* encoder layers:

  
$$\\begin{array}{ll} {\\mathbf{z}^{\\prime}\\ \_{l}} & {= MultiHeadAttn(LayerNorm(\\mathbf{z}\_{l - 1}) + \\mathbf{z}\_{l - 1}} \\\\ \\end{array}$$  
(6.4)

  
$$\\begin{array}{ll} \\mathbf{z}\_{l} & {= FeedFwd(LayerNorm(\\mathbf{z}\_{l}) + \\mathbf{z}^{\\prime}\\ \_{l}} \\\\ \\end{array}$$  
(6.5)

  
$$\\begin{array}{ll} \\mathbf{y} & {= LayerNorm(\\mathbf{z}\_{L}^{0}),} \\\\ \\end{array}$$  
(6.6)

where *l* = 1, …, *L* and **z**[*L*]⁰ is the classification embedding for the final encoder layer. Also, the feed-forward layer has two fully-connected layers followed by a GELU activation function. One of the ways in which ViT differs from the standard transformer is that in ViT the *LayerNorm* operation is applied to the output of the previous layer before the residual connection takes place. In the standard transformer \[[254](#refbib.xhtml#refbib_254)\], the residual connection was added prior to *LayerNorm*.

Through a series of experiments with ViT, \[[78](#refbib.xhtml#refbib_78)\] demonstrates that the inductive biases introduced by CNNs are useful for small datasets, but not for larger ones. With larger datasets the model can learn the relevant correlations on its own, as has been shown for various Transformers. ViT also shows that the spatial relationship between patches (distance inside the image) is learned by the positional encodings. Patches that are close to each other end up with similar positional encodings. The two-dimensional spatial correlations are also learned by the positional encodings, i.e., patches in the same row or column have similar positional encodings. The experiments also demonstrated that hard-coding the two-dimensional structure of the image patches into the positional encodings does not improve quality. This is likely because building inductive biases into a model as versatile as a transformer prevents it from learning on its own what is or is not important.

Lastly, the Vision Transformer investigates a modification to the self-attention mechanism, axial attention \[[114](#refbib.xhtml#refbib_114), [126](#refbib.xhtml#refbib_126)\]. Axial attention, where attention is between patches in the same row or the same column. ViT actually creates axial transformer blocks, where there is a row attention mechanism followed by a column attention mechanism.

## 6.3 Automatic Speech Recognition

Automatic speech recognition (ASR), which is when a system automatically converts a speech audio signal into text, presents a unique challenge that is not present in computer vision and NLP tasks. Speech signals are sequences of continuous values, and not discrete ones like those seen in images or text. This means you can't do pre-training in the same way as you would for computer vision or NLP. For example, in NLP you have a discrete words or subword units, defined in the input signal itself. Similarly, in computer vision, you have image subunits in the input signal, pixels. There are no built-in subunits in a speech signal. This makes pre-training hard, masked or unmasked. This section covers three of the ways in which transformers have been applied to ASR.

### 6.3.1 Wav2vec 2.0

The first step in wav2vec 2.0 \[[16](#refbib.xhtml#refbib_16)\] uses a convolutional feature encoder (it's a CNN) to convert the input speech audio, **X**, into a sequence of representations, (**z**[1], …, **z**[*T*]. The length of the sequence, *T*, is the number of time steps in the audio. Some spans of in the sequence of speech representations are then masked.

The encodings are able to be learned because the speech is decomposed into discrete speech units akin to the WordPiece tokens used as inputs into a text Transformer. The speech units are a finite set of discrete units of the audio sequence and are shorter than phonemes (they're 25 ms in length). The latent speech encodings are analogous to the embeddings learned in the initial embedding layer in a text transformer. These masked encodings are passed into a transformer to build contextualized representations. A contrastive loss function \[[219](#refbib.xhtml#refbib_219), [250](#refbib.xhtml#refbib_250)\] lets the wav2vec 2.0 transformer learn the relative importance of the speech units.

Note that the discrete speech units also enable cross-lingual training, where the model learns which units are only used for a particular language and which units are used across multiple languages.

**Training process** As we have seen throughout this book, transformers can use pre-training on a large corpus to learn a wide variety of features of natural language, and then fine-tuning for a given set of tasks. This is what happens with wav2vec 2.0, except it combines unsupervised and self-supervised pre-training, only needing a relatively small amount of labeled data for fine-tuning.

### 6.3.2 Speech2Text2

Speech2Text2 \[[258](#refbib.xhtml#refbib_258)\] is another powerful application of the unsupervised pre-training of transformers to ASR, where a decoder block is added on top of a wav2vec 2.0 encoder. After pre-training, the model is fine-tuned with a CTC loss. The decoder is only trained during fine-tuning, it is not pre-trained.

Because Speech2Text2 uses a decoder, it can also be used to combine machine translation and ASR, i.e., the audio could be in English and the transcription could be in French. Wang et al. have also fine-tuned Speech2Text for this task, achieving a new state-of-the-art on some language pairs.

### 6.3.3 HuBERT: Hidden Units BERT

To deal with the no predefined speech units problem, Hsu et al. introduce HuBERT (Hidden Units BERT) \[[120](#refbib.xhtml#refbib_120)\]. HuBERT uses clustering to generate noisy speech subunits that can then be treated like subwords that can undergo BERT-like pre-training.

HuBERT uses the noisy labels as a sequence of input tokens that can be masked for BERT pre-training. So, just like BERT learns representations of the unmasked text so that it may correctly predict the masked tokens, HuBERT learns representations of the unmasked, noisy speech subunits so that it may correctly predict the masked speech units.

In HuBERT, the raw speech signal is put through a CNN encoder to produce, the encoded speech signal *X* = \[*x*[1], …, *x*[*T*]\] of length *T*, much like in wav2vec 2.0. A set of indices in the encoded speech signal *X* is then masked. This masked sequence is used as the input to the BERT-like transformer. HuBERT also performs masking in the same way as wav2vec 2.0.

HuBERT uses k-means on MFCC features \[[279](#refbib.xhtml#refbib_279)\] of the raw speech signal to find nontrivial discrete hidden units \[[290](#refbib.xhtml#refbib_290)\]. It calls these \[*z*[1], …, *z*[*T*]\], where *z*[*t*] ∈ \[*C*\] is a categorical variable of *C* classes. These *z*[*t*] are used as the output “tokens” that the BERT pre-training needs to accurately predict. Hsu et al. also experiment with using an ensemble of clustering models in place of a single k-means, followed by product quantization \[[99](#refbib.xhtml#refbib_99)\].

After pre-training, HuBERT uses the standard connectionist temporal classification (CTC) loss to fine-tune the model using labeled audio data. Note that the CNN feature encoder is frozen during the fine-tuning.

## 6.4 Multimodal And Multitasking Transformer

After proving to be very effective in many NLP tasks, transformers have shown their effectiveness even in combined tasks involving various modalities like image, text, and videos. Especially around tasks combining image and text, many transformer architectures have been proposed extending the base BERT model to incorporate visual input along with language inputs \[[123](#refbib.xhtml#refbib_123), [173](#refbib.xhtml#refbib_173)\]. In this section, we will cover a couple of architectures that are more generic and adopted.

### 6.4.1 Vision-And-Language Bert (Vilbert)

Vision-and-Language BERT (VilBERT) is a joint model for learning task-agnostic representations for image and text \[[173](#refbib.xhtml#refbib_173)\]. The image is first converted into a stream of a sequence of regions mapped to feature vectors using an object detection network. The text follows the normal flow of tokens mapped to positional and word embeddings as a stream of sequences. As shown in [Fig. 6.1](#ch6.xhtml#fig6_1), VilBERT uses the standard transformer block (TRM) and a co-attention transformer block (Co-TRM) that provides sparse interactions between the two modalities. The Co-TRM module computes query, key, and value matrices similar to the standard transformer block for visual and linguistic representations at any intermediate layer. However, the keys and values from each modality are provided as an input to the other modality's multi-headed attention block. Thus, the multi-headed attention block of Co-TRM produces attention-pooled features for each modality conditioned on the other and enabling joint learning. The architecture allows multiple layers of TRM and Co-TRM for refinement and is task-dependent. The output is task-dependent and can be as simple as a multi-layer perceptron (MLP) followed by a soft-max layer to compute a score giving similarity between the image and the text. There can be multiple outputs corresponding to multiple tasks, all learned together in parallel.

![Figure 6.1 ViLBERT processing text and image for learning joint representation for multi-modal tasks.](images/fig6_1.jpg)

[Figure 6.1](#ch6.xhtml#b6fig6_1) ViLBERT processing text and image for learning joint representation for multi-modal tasks.

The training of VilBERT happens through various stages similar to inception network training. First, the text and image are trained independently. The BERT model is trained end-to-end on a large corpus for two tasks: masked language modeling (MLM) and next sentence prediction (NSP). The Faster R-CNN-based pre-trained object detection network extracts bounding boxes and their visual features from images and processes them through the network. Next, the Conceptual Captions dataset comprising numerous examples of images and their captions is used for joint learning tasks such as mapping regions in the images to the text and masked word prediction from images. Finally, the model is trained for solving specific tasks involving visual and text modalities such as Visual Question-Answering (VQA), Visual Commonsense Reasoning (VCR), Image Retrieval and Phase Grounding. The research shows VilBERT achieves state-of-the-art results in all four tasks compared to existing task-specific models.

### 6.4.2 Unified Transformer (UniT)

In their work *Transformer is All You Need: Multimodal Multitask Learning with a Unified Transformer*\[[123](#refbib.xhtml#refbib_123)\], Hu and Singh propose a Unified Transformer (UniT) that can jointly learn and perform seven tasks across the modalities of text and images.

As shown in [Fig. 6.2](#ch6.xhtml#fig6_2), for each modality, there is an encoder network, and the output of the encoder network is concatenated to give a joint representation. The combined encoder output flows through the decoder network with a multi-head cross-attention block for a task-specific input embedding outputting the results to each task-specific head such as object class detection, visual question answering, sentiment classifier, etc.

![Figure 6.2 UniT processing text and image for learning joint representation for multi-modal tasks.](images/fig6_2.jpg)

[Figure 6.2](#ch6.xhtml#b6fig6_2) UniT processing text and image for learning joint representation for multi-modal tasks.

For training vision-only and visual-language-specific tasks, the image is first processed by a convolutional neural network block followed by a transformer encoder to get the hidden visual representations. In addition, given that different visual-related tasks such as object detection and VQA might require task-specific information, a task embedding vector is added into the transformer encoder. The text encoder uses pre-trained BERT with text embeddings and task-specific embedding vector similar to the image encoder. The decoder is domain agnostic taking the concatenated inputs from the modalities flowing into the multi-head cross-attention block and task-specific queries flowing into the input multi-head attention of the decoder transformer. The training happens on multiple tasks jointly, where a random task and a dataset to fill a batch of samples are chosen at each training iteration. UniT model shows comparable and robust performance on seven tasks across eight datasets to well-established previous work on each domain, keeping the parameters similar.

## 6.5 Video Processing With Timesformer

There are several ways that transformers can be applied to videos. This section will discuss one such application, video classification/action recognition.

TimeSformer \[[29](#refbib.xhtml#refbib_29)\] is the answer to the question of whether it's possible to do performant video classification or action recognition with self-attention instead of convolutions. TimeSformer uses a modified attention mechanism and uses the Vision Transformer's method of breaking an image into a sequence of patches as its starting point.

### 6.5.1 Patch Embeddings

TimeSformer breaks a video clip into a sequence of image patches similar to how the Vision Transformer in [section 6.2](#ch6.xhtml#sec6_2) breaks a two-dimensional image into a sequence of image patches. The input to the model is a video with *F* RGB frames at resolution *H* × *W*. It can be represented by a four-dimensional matrix **X** ∈ ℝ^(*H* × *W* × 3 × *F*). Each frame (ℝ^(*H* × *W* × 3)) in the input is then decomposed into N non-overlapping patches of size *P* × *P*, where *N* = *H**W*/*P*². Each patch is turned into a vector **x**[(*p*, *t*)] ∈ ℝ^(3*P*²), where *p* = 1, …, *N* is the patch index and *t* = 1, …, *F* is the time/frame index.

The next step is to generate an embedding vector, **z**[(*p*, *t*)]^((0)) ∈ ℝ^(*D*), for each patch, where *D* is the Transformer's hidden size:

  
$$\\begin{array}{l} {\\mathbf{z}\_{(p,t)}^{(0)} = \\mathbf{x}\_{(p,t)}\\mathbf{E} + \\mathbf{e}\_{(p,t)}^{pos},} \\\\ \\end{array}$$  
(6.7)

where **e**[(*p*, *t*)]^(*p**o**s*) ∈ ℝ^(*D*) is a positional encoding that includes the spatial location and frame index, **E** is a learned embedding layer, and *D* is a hidden dimension (similar to *d*[*m**o**d**e**l*] in the standard transformer). Note that the superscript (0) in **z**[(*p*, *t*)]^((0)) represents that this is for the first TimeSformer layer, which has index 0. Just like in the Vision Transformer, TimeSformer prepends a learned embedding onto **z**[(*p*, *t*)]^((0)) that corresponds to BERT's special classification token, **z**[(0, 0)]^((0)).

### 6.5.2 Self-Attention

In TimeSformer, the self-attention mechanism is *nearly* identical to every other transformer. In most transformers, the inputs to the multi-head attention are the query, key, and value matrices. Similar to 5.24, each is the result of transforming the input embedding into a different vector space. Each vector space is parameterized by the matrices **W**[*Q*], **W**[*K*], and **W**[*Q*], respectively. The *W* matrices are used to rotate the input embeddings into the query, key, and value spaces. Thus, the query, key, and value vectors for a single patch in TimeSformer layer *l* are

  
$$\\begin{array}{ll} \\mathbf{q}\_{(p,t)}^{(l,h)} & {= LayerNorm\\left( \\mathbf{z}\_{(p,t)}^{(l - 1)} \\right)\\mathbf{W}\_{Q}^{(l,h)} \\in {\\mathbb{R}}^{D/H}} \\\\ \\end{array}$$  
(6.8)

  
$$\\begin{array}{ll} \\mathbf{k}\_{(p,t)}^{(l,h)} & {= LayerNorm\\left( \\mathbf{z}\_{(p,t)}^{(l - 1)} \\right)\\mathbf{W}\_{K}^{(l,h)} \\in {\\mathbb{R}}^{D/H}} \\\\ \\end{array}$$  
(6.9)

  
$$\\begin{array}{ll} \\mathbf{v}\_{(p,t)}^{(l,h)} & {= LayerNorm\\left( \\mathbf{z}\_{(p,t)}^{(l - 1)} \\right)\\mathbf{W}\_{V}^{(l,h)} \\in {\\mathbb{R}}^{D/H}} \\\\ \\end{array}$$  
(6.10)

*H* is the number of attention heads, *l* is the layer index, and *h* is the attention head index. *D*/*H* is similar to the key/value dimension used in the vanilla Transformer. Note that TimeSformer gives query, key, and value the same dimension and that each **W** matrix is  ∈ ℝ^(*D*/*H* × *D*). Note that the previous layer's output is put through the *LayerNorm* operation before query, key, and value computation; this is just like in the Vision Transformer, as shown in [section 6.6](#ch6.xhtml#sec6_6).

#### 6.5.2.1 Spatiotemporal self-attention

TimeSformer uses scaled dot-product attention, as seen in section 5.23. Using the query, key, and value vectors defined above, we can compute the attention weights between patch (*p*, *t*) and patch (*p*^′, *t*^′) in layer *l*:

  
$$\\begin{array}{ll} a\_{(p,t),(p^{\\prime},t^{\\prime})}^{(l,h)} & {= \\text{softmax}\\left( {\\mathbf{q}\_{(\\text{p},\\text{t})}^{(\\text{l},\\text{h})} \\cdot \\mathbf{k}\_{(\\text{p}^{\\prime},\\text{t}^{\\prime})}^{(\\text{l},\\text{h})}\\ ^{\\text{T}}} \\right)} \\\\ \\end{array}$$  
(6.11)

  
$$\\begin{array}{ll} \\ & {= \\frac{\\exp\\left( {\\mathbf{q}\_{(p,t)}^{(l,h)} \\cdot \\mathbf{k}\_{(p^{\\prime},t^{\\prime})}^{(l,h)}\\ ^{T}} \\right)}{{\\sum\\limits\_{(u,r)\\mspace{2mu} \\in S\_{(p,t)}}{\\exp}}\\left( {\\mathbf{q}\_{(p,t)}^{(l,h)} \\cdot \\mathbf{k}\_{(u,r)}^{(l,h)}\\ ^{T}} \\right)}} \\\\ \\end{array}$$  
(6.12)

where *S*[(*p*, *t*)] is the set of patches that patch (*p*, *t*) can attend to. Note that since **z**[(*p*, *t*)]^((*l*)) contains the classification embedding at (0, 0), the query, key, and value include the classification token term: **q**[(*p*, *t*)] = \[**q**[(0, 0)]; **q**[(*p*, *t*)]\]. The square root factor in section 6.12 has been omitted for brevity.

The *N**F* + 1 weights for patch (*p*, *t*) can be grouped into a single vector

  
$$\\begin{array}{l} {\\mathbf{a}\_{(p,t)}^{(l,h)} = \\text{softmax}\\left( {\\mathbf{q}\_{(\\text{p},\\text{t})}^{(\\text{l},\\text{h})} \\cdot \\lbrack{\\mathbf{k}\_{(\\text{0},\\text{0})}^{(\\text{l},\\text{h})}\\ ^{\\text{T}};\\,\\mathbf{k}\_{(\\text{p}^{\\prime},\\text{t}^{\\prime})}^{(\\text{l},\\text{h})}\\ ^{\\text{T}}}\\rbrack} \\right)} \\\\ \\end{array}$$  
(6.13)

By looking at the relative position of patch (*p*, *t*) and patch (*p*^′, *t*^′), one sees that there are two types of attention in section 6.12. The case where (*p*, *t*) is only allowed to attend to patches in the same frame, i.e., *t*^′ = *t*, is spatial attention. This reduces the number of dot products that need to be computed from *N**F* + 1 to *N* + 1. The case where (*p*, *t*) is only allowed to attend to patches in different frames, but at the same position (*p*^′ = *p*), then we have temporal attention. This reduces the number of dot products that need to be computed from *N**F* + 1 to *F* + 1. Both of the above simplifications amount to an attention mask and would need to be added to *S*[(*p*, *t*)] when computing the normalization factor of the softmax operation. The remainder of the multihead self-attention calculation proceeds as expected in a transformer.

#### 6.5.2.2 Spatiotemporal Attention Blocks

The paper \[[29](#refbib.xhtml#refbib_29)\] considers four ways of restricting *S*[(*p*, *t*)]: only spatial attention, divided space-time attention, sparse local and global attention, and axial attention.

Divided space-time attention is having separate spatial and temporal attention mechanisms; a temporal block, followed by a spatial block. The output embedding of the multi-head temporal attention, **z**^′ [(*p*, *t*)]^((*l*)), is computed and then fed into the multi-head spatial attention block as input. In this scheme the temporal and spatial blocks each have their own separate query, key, and value spaces. Because the blocks are in sequence, there are *F* + 1 + *N* + 1 = *N* + *F* + 2 query-key comparisons per patch (*p*, *t*). Note that the ordering of the attention blocks was found via experiments. Sparse local and global attention is the combination of local space-time attention, where locality is defined as the neighboring *F* × *H*/2 × *W*/2 patches, and global attention with stride of 2 in temporal and spatial dimensions. As defined, sparse local and global attention is a coarse-grained approximation to the full spatiotemporal attention. Lastly, the axial attention is similar to that in the Vision Transformer, where there is spatial attention between patches in within a frame that are in the same row or column; there is also temporal attention between patches at the same location in different frames.

As spatial resolution increases and the videos get longer, divided space-time attention scales better than the joint space-time attention because the spatial and temporal components are separated in the divided case. Note that, for a single patch, the spatial and temporal attention are both linear. Spatial is *O*(*N*) and temporal is *O*(*F*), so the divided scales as *O*(*N* + *F*). The joint attention is *O*(*N* ⋅ *F*).

The paper finds that in many cases, spatial attention is more important than temporal attention. But, there are cases where the temporal attention is very important. Another finding is that the divided space-time attention is able to learn more than the full, joint space-time attention because the divided case treats them as two separate attention mechanisms, and thus it has twice the parameters and can learn more, in principal. Because of this, the recommended attention method is divided space-time attention.

## 6.6 Graph Transformers

Can transformers be applied to graph datasets? When a transformer uses a full attention mechanism, meaning it has no hard-coded sparsity, it treats an input sequence as a fully-connected graph. This is true for text, images, videos, etc. We saw this for text data with Big Bird in [section 5.2.2.4](#ch5.xhtml#sec5_2_2_4), for images with Vision Transformer in [section 6.2.1](#ch6.xhtml#sec6_2_1), and with video for TimeSformer in [section 6.5](#ch6.xhtml#sec6_5). Fully-connected attention lets the model learn the relative importance of each connection. For graph datasets, however, any given node could have so many links that using fully-connected attention would be computationally intractable, since full attention already has quadratic complexity for simple sequences. This is the purpose of the Graph Transformer introduced in \[[80](#refbib.xhtml#refbib_80)\]. It addresses the complexity of self-attention by letting a node attend to other nodes in its local neighborhood.

### 6.6.1 Positional Encodings In a Graph

As discussed in [section 5.2](#ch5.xhtml#sec5_2), scaled-dot product attention mechanisms have quadratic complexity in both time and memory. Since graphs can have a very large number of nodes, to make graph transformers computationally feasible, there must be local sparsity in the attention for any node. The problem with this is that *general* graphs have no notion of distance between nodes, making it non-trivial to use positional encodings to provide a measure of distance or locality, as is common in Transformers. As described in \[[80](#refbib.xhtml#refbib_80)\], this problem is solved by using Laplacian positional encodings\[[81](#refbib.xhtml#refbib_81)\], which are generated via a spectral embedding into Euclidean space.

#### 6.6.1.1 Laplacian Positional Encodings

Laplacian positional encodings for a graph with *n* nodes are computed from the graph's adjacency and degree matrices:

  
$$\\begin{array}{ll} \\mathbf{\\mathrm{\\Delta}} & {= \\mathbb{I} - \\mathbf{D}^{- 1/2}\\mathbf{A}\\mathbf{D}^{- 1/2}} \\\\ \\end{array}$$  
(6.14)

  
$$\\begin{array}{ll} \\ & {= \\mathbf{U}^{T}\\mathbf{\\Lambda U},} \\\\ \\end{array}$$  
(6.15)

where **A** is the adjacency matrix, **D** is the degree matrix, **Λ** is the eigenvalue matrix (diagonal), and **U** is the eigenvector matrix.

The positional encodings for node *i***λ**[*i*] are constructed by taking the *k* smallest non-trivial eigenvectors, each of which is normalized, with a  − 1 factor randomly assigned to each.

### 6.6.2 Graph Transformer Input

We can describe a graph 𝒢 as a collection of nodes and edges between the nodes. Each node *i* has features **α**[*i*] ∈ ℝ^(*d*[*n*] × 1), where *d*[*n*] is the number of node features. Each edge between nodes *i* and *j* has features **β**[*i**j*] ∈ ℝ^(*d*[*e*] × 1), where *d*[*e*] is the number of edge features. A graph Transformer's input layer has two embedding layers, one to embed the nodes and one to embed the edges. Both embedding layers produce *d*− dimensional embeddings, resulting in node embeddings for node *i*, **h̃**[*i*]^((0)) and edge embeddings**ẽ**[*i**j*]^((0)) between nodes *i* and *j*:

  
$$\\begin{array}{ll} \\mathbf{\\widetilde{h}}\_{i}^{(0)} & {= \\mathbf{A}^{(0)}\\mathbf{\\alpha}\_{i} + \\mathbf{a}^{(0)}} \\\\ \\end{array}$$  
(6.16)

  
$$\\begin{array}{ll} \\mathbf{\\widetilde{e}}\_{ij}^{(0)} & {= \\mathbf{B}^{(0)}\\mathbf{\\beta}\_{ij} + \\mathbf{b}^{(0)},} \\\\ \\end{array}$$  
(6.17)

where **A**^((0)) ∈ ℝ^(*d* × *d*[*n*]) and **B**^((0)) ∈ ℝ^(*d* × *d*[*n*]) are the node and edge embedding matrices, respectively, and **a**^((0)) and **b**^((0)) are bias terms for the nodes and edges, respectively. The superscript (0) denotes that this is the input layer.

The Laplacian positional encodings **λ**[*i*] also get embedded into a *d*− dimensional space with an additional learnable embedding layer **C**^((0)) ∈ ℝ^(*d* × *k*), to generate Laplacian positional embeddings **λ**[*i*]^((0)):

  
$$\\begin{array}{ll} \\mathbf{\\lambda}\_{i}^{(0)} & {= \\mathbf{C}^{(0)}\\mathbf{\\lambda}\_{i} + \\mathbf{c}^{(0)}} \\\\ \\end{array}$$  
(6.18)

  
$$\\begin{array}{ll} \\mathbf{h}\_{i}^{(0)} & {= \\mathbf{\\widetilde{h}}\_{i}^{(0)} + \\mathbf{\\lambda}\_{i}^{(0)}} \\\\ \\end{array}$$  
(6.19)

Note that **c**^((0)) ∈ ℝ^(*d*) is a bias term for the Laplacian positional embedding, **h**^((0)) is the full node embedding, and Laplacian positional embeddings are only computed for the input layer and are not used inside Transformer layers.

#### 6.6.2.1 Graphs without edge attributes

There are two ways to structure a graph Transformer, depending on whether the graph has edge attributes or not. When there are no edge attributes, the output of the multi-head attention mechanism in layer *l* is:

  
$$\\begin{array}{ll} \\mathbf{\\widetilde{h}}\_{i}^{(l + 1)} & {= \\lbrack{\\mathbf{Attn}(1,l,i);\\ldots;\\mathbf{Attn}(H,l,i)})\\mathbf{O}^{(l)}} \\\\ \\end{array}$$  
(6.20)

  
$$\\begin{array}{ll} {\\mathbf{Attn}(m,l,i)} & {= {\\sum\\limits\_{j \\in S\_{i}}w\_{ij}^{(m,l)}}\\mathbf{W}\_{v}^{(m,l)}\\mathbf{h}\_{j}^{(l)}} \\\\ \\end{array}$$  
(6.21)

  
$$\\begin{array}{ll} w\_{ij}^{(m,l)} & {= \\text{softmax}\_{\\text{j}}\\left( \\frac{\\mathbf{W}\_{\\text{q}}^{(\\text{m},\\text{l})}\\mathbf{h}\_{\\text{i}}^{(\\text{l})} \\cdot \\mathbf{W}\_{\\text{k}}^{(\\text{m},\\text{l})}\\mathbf{h}\_{\\text{j}}^{(\\text{l})}}{\\sqrt{\\text{d}\_{\\text{k}}}} \\right)} \\\\ \\end{array}$$  
(6.22)

where *S*[*i*] is the set of key positions that query *i* attends to, *m* indexes the attention head, **W**[*q*]^((*m*, *l*)), **W**[*k*]^((*m*, *l*)), **W**[*v*]^((*m*, *l*)) ∈ ℝ^(*d*[*k*] × *d*), *d*[*k*] is the key-value dimension, and **O**^((*l*)) ∈ ℝ^(*d* × *d*). Note that the exponents in the softmax calculation above are clamped to \[ − 5, 5\] for numerical stability. Also note that the definition of the weights matrices that are multiplied by the node embeddings to create the query, key, and value matrices are the transpose of the definition used elsewhere in this book.

**h̃**[*i*]^((*l* + 1)) is passed into the remainder of the transformer layer as follows, resulting in the output of the transformer layer, **h**[*i*]^((*l* + 1)):

  
$$\\begin{array}{ll} \\mathbf{h}\_{i}^{(l + 1)} & {= Norm(\\mathbf{h}^{\\prime}\\ \_{i}^{(l + 1)} + \\mathbf{h}^{\\prime\\prime}\\ \_{i}^{(l + 1)})} \\\\ \\end{array}$$  
(6.23)

  
$$\\begin{array}{ll} {\\mathbf{h}^{\\prime}\\ \_{i}^{(l + 1)}} & {= Norm(\\mathbf{h}\_{i}^{(l)} + \\mathbf{\\widetilde{h}}\_{i}^{(l + 1)})} \\\\ \\end{array}$$  
(6.24)

  
$$\\begin{array}{ll} {\\mathbf{h}^{\\prime\\prime}\\ \_{i}^{(l + 1)}} & {= \\mathbf{W}\_{2}^{(l)}\\text{ReLU}\\left( {\\mathbf{W}\_{\\text{1}}^{(\\text{l})}\\mathbf{h}^{\\prime}\\ \_{\\text{i}}^{(\\text{l+1})}} \\right)} \\\\ \\end{array}$$  
(6.25)

where **W**[1]^((*l*)) ∈ ℝ^(2*d* × *d*), **W**[2]^((*l*)) ∈ ℝ^(*d* × 2*d*), and *Norm* can be layer normalization or batch normalization. The structure of the Graph Transformer described in (6.23)–(6.25) is shown in [Fig. 6.3](#ch6.xhtml#fig6_3).

![Figure 6.3 Diagram of the Graph Transformer encoder, without edge attributes. The encoder structure is shown on the left. The multi-head attention mechanism is shown on the right. is As described in section 6.6.1.1, Laplacian embeddings are only applied to the input layer, l = 0.](images/fig6_3.jpg)

[Figure 6.3](#ch6.xhtml#b6fig6_3) Diagram of the Graph Transformer encoder, without edge attributes. The encoder structure is shown on the left. The multi-head attention mechanism is shown on the right. is As described in [section 6.6.1.1](#ch6.xhtml#sec6_6_1_1), Laplacian embeddings are only applied to the input layer, *l* = 0.

#### 6.6.2.2 Graphs With Edge Attributes

For graphs that have attributes on the edges, (6.21)–(6.25) are modified and expanded to account for the edge embeddings. The node embeddings are updated in mostly the way. The only change is that the attention weights that go into the softmax operation now have a contribution from the edge embeddings:

  
$$\\begin{array}{ll} \\mathbf{\\widetilde{h}}\_{i}^{(l + 1)} & {= \\lbrack{\\mathbf{Attn}(1,l,i);\\ldots;\\mathbf{Attn}(H,l,i)}\\rbrack\\mathbf{O}^{(l)}} \\\\ \\end{array}$$  
(6.26)

  
$$\\begin{array}{ll} \\mathbf{\\widetilde{e}}\_{ij}^{(l + 1)} & {= \\lbrack{{\\widetilde{w}}\_{ij}^{(1,l)};\\ldots,{\\widetilde{w}}\_{ij}^{(H,l)}}\\rbrack\\mathbf{O}\_{edge}^{(l)}} \\\\ \\end{array}$$  
(6.27)

  
$$\\begin{array}{ll} {\\mathbf{Attn}(m,l,i)} & {= {\\sum\\limits\_{j \\in S\_{i}}w\_{ij}^{(m,l)}}\\mathbf{V}^{(m,l)}\\mathbf{h}\_{j}^{(l)}} \\\\ \\end{array}$$  
(6.28)

  
$$\\begin{array}{ll} w\_{ij}^{(m,l)} & {= \\text{softmax}\_{\\text{j}}\\left( {\\widetilde{\\text{w}}}\_{\\text{ij}}^{(\\text{m},\\text{l})} \\right)} \\\\ \\end{array}$$  
(6.29)

  
$$\\begin{array}{ll} {\\widetilde{w}}\_{ij}^{(m,l)} & {= \\left( \\frac{\\mathbf{W}\_{q}^{(m,l)}\\mathbf{h}\_{i}^{(l)} \\cdot \\mathbf{W}\_{k}^{(m,l)}\\mathbf{h}\_{j}^{(l)}}{\\sqrt{d\_{k}}} \\right) \\cdot \\mathbf{W}\_{E}^{(m,l)}\\mathbf{e}\_{ij}^{(l)},} \\\\ \\end{array}$$  
(6.30)

where, again, *S*[*i*] is the set of key positions that query *i* attends to, *m* indexes the attention head, **W**[*q*]^((*m*, *l*)), **W**[*k*]^((*m*, *l*)), **W**[*v*]^((*m*, *l*)), **W**[*E*]^((*m*, *l*)) ∈ ℝ^(*d*[*k*] × *d*), *d*[*k*] is the key-value dimension. The **W**[*E*]^((*m*, *l*)) are the weights for a value layer for the edges; it transforms the edge embeddings analogous to how **W**[*v*]^((*m*, *l*)) transforms the node embeddings.

Note that while there is a single multi-head attention mechanism when there are edge attributes, that there is a separate linear layer for combining the final attention for nodes and the final attention for edges. This can be seen from the existence of **O**^((*l*)), **O**[*e**d**g**e*]^((*l*)) ∈ ℝ^(*d* × *d*). As in the case without edge attributes, the exponents in the softmax calculation above are clamped to \[ − 5, 5\] for numerical stability.

**h̃**[*i*]^((*l* + 1)) is passed into the remainder of the Transformer layer as follows, resulting in two outputs for the Transformer layer, **h**[*i*]^((*l* + 1)) for nodes (as shown in (6.31)) and **e**[*i**j*]^((*l* + 1)) for edges:

  
$$\\begin{array}{ll} \\mathbf{h}\_{i}^{(l + 1)} & {= Norm(\\mathbf{h}^{\\prime}\\ \_{i}^{(l + 1)} + \\mathbf{h}^{\\prime\\prime}\\ \_{i}^{(l + 1)})} \\\\ \\end{array}$$  
(6.31)

  
$$\\begin{array}{ll} {\\mathbf{h}^{\\prime}\\ \_{i}^{(l + 1)}} & {= Norm(\\mathbf{h}\_{i}^{(l)} + \\mathbf{\\widetilde{h}}\_{i}^{(l + 1)})} \\\\ \\end{array}$$  
(6.32)

  
$$\\begin{array}{ll} {\\mathbf{h}^{\\prime\\prime}\\ \_{i}^{(l + 1)}} & {= \\mathbf{W}\_{n,2}^{(l)}\\text{ReLU}\\left( {\\mathbf{W}\_{\\text{n},\\text{1}}^{(\\text{l})}\\mathbf{h}^{\\prime}\\ \_{\\text{i}}^{(\\text{l+1})}} \\right)} \\\\ \\end{array}$$  
(6.33)

  
$$\\begin{array}{ll} \\mathbf{e}\_{ij}^{(l + 1)} & {= Norm(\\mathbf{e}^{\\prime}\\ \_{ij}^{(l + 1)} + \\mathbf{e}^{\\prime\\prime}\\ \_{ij}^{(l + 1)})} \\\\ \\end{array}$$  
(6.34)

  
$$\\begin{array}{ll} {\\mathbf{e}^{\\prime}\\ \_{ij}^{(l + 1)}} & {= Norm(\\mathbf{e}\_{ij}^{(l)} + \\mathbf{\\widetilde{e}}\_{ij}^{(l + 1)})} \\\\ \\end{array}$$  
(6.35)

  
$$\\begin{array}{ll} {\\mathbf{e}^{\\prime\\prime}\\ \_{ij}^{(l + 1)}} & {= \\mathbf{W}\_{e,2}^{(l)}\\text{ReLU}\\left( {\\mathbf{W}\_{\\text{e},\\text{1}}^{(\\text{l})}\\mathbf{e}^{\\prime}\\ \_{\\text{ij}}^{(\\text{l+1})}} \\right)} \\\\ \\end{array}$$  
(6.36)

where **W**[*n*, 1]^((*l*)), **W**[*e*, 1]^((*l*)) ∈ ℝ^(2*d* × *d*), **W**[*n*, 2]^((*l*)), **W**[*e*, 2]^((*l*)) ∈ ℝ^(*d* × 2*d*), and *Norm* can be layer normalization or batch normalization. Subscripts *n* and *e* are for nodes and edges, respectively. This is shown schematically in [Fig. 6.4](#ch6.xhtml#fig6_4).

![Figure 6.4 Diagram of the Graph Transformer encoder, with edge attributes. The encoder structure is shown on the left. The multi-head attention mechanism is shown on the right. As described in section 6.6.1.1, Laplacian embeddings are only applied to the input layer, l = 0.](images/fig6_4.jpg)

[Figure 6.4](#ch6.xhtml#b6fig6_4) Diagram of the Graph Transformer encoder, with edge attributes. The encoder structure is shown on the left. The multi-head attention mechanism is shown on the right. As described in [section 6.6.1.1](#ch6.xhtml#sec6_6_1_1), Laplacian embeddings are only applied to the input layer, *l* = 0.

## 6.7 Reinforcement Learning

Reinforcement Learning (RL) is a machine learning method that uses rewards to train an autonomous agent that can choose its next action so that it gets the best cumulative reward, given its current state.

To understand the process of reinforcement learning, we can start with a finite Markov decision process \[[239](#refbib.xhtml#refbib_239)\], which is a formal way of looking at a sequence of decisions that an agent which interacts with an environment can take. The agent and the environment interact at a sequence of time steps *t* = 0, …, *T*. At each *t*, the agent gets the environment's state *s*[*t*] ∈ 𝒮 and then chooses an action *a*[*t*] ∈ 𝒜(*s*). At time *t* + 1, the agent receives a reward from the environment *r*[*t* + 1] ∈ ℝ and the environment's state is updated to *s*[*t* + 1]. This simple idea is illustrated in [Fig. 6.5](#ch6.xhtml#fig6_5). Note that generally speaking, the reward will be a function of the state and action, *r*[*t*] = *R*(*s*[*t*], *a*[*t*]). As time progresses, a sequence of states, actions, and rewards accumulates: (*s*[0], *a*[0], *r*[1], *s*[1], *a*[1], *r*[2], *s*[2], *a*[2], *r*[3], …). This sequence can be called a trajectory.

![Figure 6.5 Depiction of the interaction between the agent and environment in reinforcement learning. At time t, the state observed by the agent is st. The agent then selects an action at. In the next time step, t + 1, the environment updates it state to s\_{t + 1} and issues a reward to the agent, r\_{t + 1}. After this, the cycle can repeat.](images/fig6_5.jpg)

[Figure 6.5](#ch6.xhtml#b6fig6_5) Depiction of the interaction between the agent and environment in reinforcement learning. At time *t*, the state observed by the agent is *s*[*t*]. The agent then selects an action *a*[*t*]. In the next time step, *t* + 1, the environment updates it state to *s*[*t* + 1] and issues a reward to the agent, *r*[*t* + 1]. After this, the cycle can repeat.

In practice, *r*[*t*] and *s*[*t*] are random variables with probability distributions. The probability of moving to state *s*^′ and earning reward *r*, given that action *a* was taken in state *s* is given by

  
$$\\begin{array}{ll} {p(s^{\\prime},r|s,a)} & {= Prob({s\_{t} = s^{\\prime},r\_{t} = r|s\_{t - 1} = s,a\_{t - 1} = a})} \\\\ {{\\sum\\limits\_{s^{\\prime} \\in \\mathcal{S}}{\\sum\\limits\_{r \\in \\mathcal{R}}p}}(s^{\\prime},r|s,a)} & {= 1,\\,\\,\\forall s \\in \\mathcal{S},\\, a \\in \\mathcal{A}(s)} \\\\ \\end{array}$$  
(6.37)

The transition probabilities *p* fully characterize the dynamics of the environment and the agent does not know the set of rewards or the transition probabilities.

The task of RL is to learn the probability that the agent chooses action *a* while in state *s*. This probability distribution is called a policy.

### 6.7.1 Decision Transformer

Decision Transformer \[[41](#refbib.xhtml#refbib_41)\] is the result of an attempt to replace reinforcement learning (RL) methods with a transformer that models the sequence of states, actions, and rewards that is used to train an autonomous agent. This application is far from the language modeling tasks to which most transformers are applied.

There is one important difference between the finite Markov decision process outlined above and the process used for Decision Transformer. Decision Transformer is applied to a type of RL called offline RL. In offline RL, instead of having the agent interact with an environment and be given a state update after taking an action and getting the reward, there is a fixed dataset that contains trajectories drawn from arbitrary policies. This is a harder way for the agent to learn.

For offline RL, the trajectories in the dataset are of the form

  
$$\\begin{array}{l} {({\\hat{R}}\_{1},s\_{1},a\_{1},{\\hat{R}}\_{2},s\_{2},a\_{2},\\ldots,{\\hat{R}}\_{T},s\_{T},a\_{T})} \\\\ \\end{array}$$  
(6.38)

where ${\\hat{R}}\_{t} = {\\sum\\limits\_{t^{\\prime} = t}^{T}r\_{t^{\\prime}}}$ is the “return-to-go”, which is the amount of reward that needs to be generated to get to the end of the trajectory from *t*.

These fixed trajectories are used for autoregressive training. The previous *K* steps are passed to the Decision Transformer. Each step contains three “tokens”: the state, action, and return-to-go. Each type of token has its own linear embedding layer, which is followed up by a LayerNorm. There are also learned positional embeddings added to each type of token embeddings that are different that in the standard transformer because each time step has three tokens instead of one. The embeddings are then passed to a GPT-2 model, for autoregressive training. Note that for image inputs, the embedding layer is a convolutional encoder, as commonly used in computer vision. A diagram of the Decision Transformer architecture is shown in [Fig. 6.6](#ch6.xhtml#fig6_6).

![Figure 6.6 Decision Transformer architecture for offline RL. The first two time steps are shown. ER, ES, and EA represent the combined embedding layer positional encoding, and layer norm for the returns-to-go, states, and actions, respectively. The layer after GPT-2 contains three linear submodules for predicting the next element of the sequence. Next state, action, and return-to-go are predicted using different submodules.](images/fig6_6.jpg)

[Figure 6.6](#ch6.xhtml#b6fig6_6) Decision Transformer architecture for offline RL. The first two time steps are shown. *E*[*R*], *E*[*S*], and *E*[*A*] represent the combined embedding layer positional encoding, and layer norm for the returns-to-go, states, and actions, respectively. The layer after GPT-2 contains three linear submodules for predicting the next element of the sequence. Next state, action, and return-to-go are predicted using different submodules.

Since the input tokens are a sequence of rewards-to-go, states, and actions, the multi-head self-attention mechanism computes attention between rewards, states, and actions. This includes the cross-attention between the input tokens and the partially generated output tokens, which are only actions. Chen et al. surmise that the attention mechanism is what makes Decision Transformer able to learn the relationship between states, actions, and rewards. Chen et al. also believe that Decision Transformer may be useful for online RL methods, where it could be used to generate diverse behavior. Decision Transformer achieves state-of-the-art on various RL benchmarks.

## 6.8 Case Study: Automatic Speech Recognition

### 6.8.1 Goal

In this chapter, we looked at several applications of the transformer architecture. In this case study, we compare the transcription quality of Wav2vec 2.0 \[[16](#refbib.xhtml#refbib_16)\] to Speech2Text2 \[[258](#refbib.xhtml#refbib_258)\], and HuBERT \[[120](#refbib.xhtml#refbib_120)\], each of which is transformer-based and was discussed earlier in this chapter. We'll measure transcription quality with the word error rate and character error rate metrics.

### 6.8.2 Data, Tools, and Libraries

![Listing 6.1 Python environment setup](images/comp6_1.jpg)

[Listing 6.1](#ch6.xhtml#b6list6_1) Python environment setup

We'll use Huggingface Transformers to load pre-trained models and Huggingface Datasets to load an automatic speech recognition (ASR) dataset, TIMIT \[[93](#refbib.xhtml#refbib_93)\]. After loading the necessary libraries in the environment, as shown in [Listing 6.1](#ch6.xhtml#list6_1), we can load the dataset

![Listing 6.2 Load dataset](images/comp6_2.jpg)

Listing 6.2 Load dataset

### 6.8.3 Experiments, Results, and Analysis

#### 6.8.3.1 Preprocessing speech data

![](images/comp6_3.jpg)![Listing 6.3 Preprocess speech](images/comp6_3a.jpg)

Listing 6.3 Preprocess speech

#### 6.8.3.2 Evaluation

There are three types of errors we can make during transcription:

*   substitution: swapping a correct word or character for an incorrect one
    
*   deletion: removing a correct word or character
    
*   insertion: inserting a word or character
    

We can compute the word error rate and character error rate metrics by summing the three kinds of errors and dividing by the number of words (or characters):

  
$$\\begin{array}{ll} {WER} & {= \\frac{S + D + I}{N}} \\\\ \\end{array}$$  
(6.39)

  
$$\\begin{array}{ll} {CER} & {= \\frac{S + D + I}{N}} \\\\ \\end{array}$$  
(6.40)

where *S* is the number of substitutions, *D* is the number of deletions, *I* is the number of insertions, and *N* is the number of words (or characters, for CER) in the transcript. The Huggingface datasets library has both metrics built-in, so we will use those instead of writing our own.

![Listing 6.4 Load WER and CER metric](images/comp6_4.jpg)

Listing 6.4 Load WER and CER metric

Now we load each model and then transcribe and compute quality metrics.

**Wav2vec 2.0** After running the listings up to and including [Listing 6.5](#ch6.xhtml#list6_5), we find that Wav2vec 2.0 achieves a WER of 0.09291(9.29%) and a CER of 0.02212(2.2%) on the TIMIT test set.

![](images/comp6_5.jpg)![Listing 6.5 Transcribe and evaluate with Wav2vec 2.0](images/comp6_5a.jpg)

[Listing 6.5](#ch6.xhtml#b6list6_5) Transcribe and evaluate with Wav2vec 2.0

**Speech2Text2** \[[258](#refbib.xhtml#refbib_258)\] is a transformer decoder model that can be used with *any* speech encoder, such as Wav2Vec2 or HuBERT \[[120](#refbib.xhtml#refbib_120)\]. We'll use a Speech2Text2 model of comparable size to the Wav2vec2 model used in Listing 6.5.

![](images/comp6_6.jpg)![Listing 6.6 Transcribe and evaluate with Speech2Text2](images/comp6_6a.jpg)

[Listing 6.6](#ch6.xhtml#b6list6_6) Transcribe and evaluate with Speech2Text2

In [Listing 6.6](#ch6.xhtml#list6_6), you'll notice that we are explicitly passing the attention mask to the model. This turns out to be important for Speech2Text2. If the attention mask is omitted, then the model may generate a transcription that is longer than the target. With a GPU with speed comparable to a K80, the listing should run in about 4 minutes. The Speech2Text2 model achieves a WER of 0.10283(10.28%) and a CER of 0.03624(3.62%) on the TIMIT test set.

**HuBERT** \[[120](#refbib.xhtml#refbib_120)\], short for Hidden-Unit BERT, is a transformer-based self-supervised speech representation learning model that is able to learn an acoustic model and a language model directly from labeled audio data.

![](images/comp6_7.jpg)![Listing 6.7 Transcribe and evaluate with HuBERT](images/comp6_7a.jpg)

Listing 6.7 Transcribe and evaluate with HuBERT

HuBERT achieves a WER of 0.11544(11.54%) and a CER of 0.2872(2.87%) on the TIMIT test set. For comparison, the WER and CER scores are gathered into [Table 6.1](#ch6.xhtml#tbl6_1), which shows Wav2vec 2.0 performs the best on TIMIT test, with Speech2Text2 in second place; HuBERT is in third.

[TABLE 6.1](#ch6.xhtml#b6tbl6_1) WER and CER metrics on the TIMIT test set for Wav2vec 2.0, Speech2Text2, and HuBERT. Best score is in boldface

  
| Model || WER || CER |
| --- | --- | --- |
| Wav2vec 2.0 || **0**.**09291** || **0**.**02212** |
| --- | --- | --- |
| Speech2Text2 || 0.10283 || 0.03624 |
| HuBERT || 0.11544 || 0.02872 |

# CHAPTER 7Interpretability and Explainability Techniques for Transformers

DOI: [10.1201/9781003170082-7](https://doi.org/10.1201/9781003170082-7)

IN critical applications in domains like healthcare, legislation, law enforcement, or financial, in addition to the predictions, there is a need to understand the models from an explainability standpoint. Unfortunately, one can categorize most state-of-the-art transformer models and techniques covered in this book as a “black box” that can significantly impede adoption. Therefore, there is a paramount need for building explainability around these complex state-of-the-art models from both an understanding and diagnosis perspective. As proposed by Xie et al., we will cover the traits of the models that address explainability, related areas that impact explainability, the taxonomy of explainable methods applied to transformer-based and attention-based systems, and finally, a detailed case study in the electronic health record systems using transformers with different explainable techniques to get practical insights \[[275](#refbib.xhtml#refbib_275)\].

## 7.1 TRAITS OF EXPLAINABLE SYSTEMS

One of the decisive goals of an explainable system is that it allows the system's end-users to understand the relationship between the input and the output. Thus, traits can be defined as the properties of the system that a user can evaluate and measure. As proposed by Xie et al., the four necessary traits are:

1.  **Confidence**. When the end-user (decision-maker) can align the transformer-based model's processing with their thought process based on the input and the output, the confidence in the system increases. Saliency maps of attention on image or text highlights the parts of the input that are important from the model perspective for decision-making (classification, recognition, question-answering, etc.), with the output mimicking how trained humans associate a focus-based mechanism as a form of explanation \[[106](#refbib.xhtml#refbib_106), [127](#refbib.xhtml#refbib_127), [154](#refbib.xhtml#refbib_154), [195](#refbib.xhtml#refbib_195), [254](#refbib.xhtml#refbib_254)\].
    
2.  **Safety**. When deployed in applications that directly or indirectly impact human life, the transformer-based models should be deemed safe. One can qualify safety in terms of the (i) consistent and deterministic behavior, i.e., given the same input, the output remains the same every time, (ii) robust and reliable under standard and exceptional conditions, and (iii) the ability to guard against choices that negatively impact society in general \[[191](#refbib.xhtml#refbib_191)\].
    
3.  **Trust**. Dependable models are the ones that do not need validation. It has been shown that models with high confidence in prediction do not guarantee trustworthiness \[[95](#refbib.xhtml#refbib_95), [189](#refbib.xhtml#refbib_189), [191](#refbib.xhtml#refbib_191), [291](#refbib.xhtml#refbib_291)\]. Xie et al. consider two significant trustworthiness criteria: (i) satisfactory testing and (ii) experience. Satisfactory testing is the ability of the model to approximate performance similar to its training. Quantitatively, when model performance metrics such as accuracy or precision are similar on training and unseen test data, the trust increases. Experience is a more qualitative assessment where one judges the system to be sufficient to perform the task without inspection. Data and concept drift in real-world deployments can further decrease the trust in the system. There have been many studies in recent times that explore safety from a model prediction viewpoint \[[5](#refbib.xhtml#refbib_5), [22](#refbib.xhtml#refbib_22), [134](#refbib.xhtml#refbib_134), [252](#refbib.xhtml#refbib_252)\].
    
4.  **Ethics**. If the model does not violate any ethical principles set by the end-user, it can be considered ethical in its decision-making process. Developing frameworks and guidelines for ethics-based AI is growing as a field in and of itself \[[20](#refbib.xhtml#refbib_20), [26](#refbib.xhtml#refbib_26), [59](#refbib.xhtml#refbib_59), [268](#refbib.xhtml#refbib_268)\].
    

## 7.2 Related Areas That Impact Explainability

Xie et al. identify four areas that are closely aligned with explainability and are related to the traits defined in the previous section.

*   **Learning Mechanism**: The ability to provide insights into the model training process helps to increase the confidence and trust in the model. The process that leads to the learned state of the model can be further explored by: understanding the evolution of different layers from learning concepts or statistical patterns from the perspective of filters, weights, and activation \[[294](#refbib.xhtml#refbib_294), [301](#refbib.xhtml#refbib_301)\]. Study of convergence of different layers based on inputs and weights, and generalization properties of networks from memorization and statistical mechanics viewpoint \[[206](#refbib.xhtml#refbib_206)\].
    
*   **Model Debugging**: Akin to software debugging, model debugging corresponds to the inspection of the model architecture, data processing through the networks, and the errors introduced during the training and runtime process \[[140](#refbib.xhtml#refbib_140)\]. A common research approach is to build auxiliary models that act as a diagnostic and inspection probe \[[2](#refbib.xhtml#refbib_2)\]. The proposal of ModelTracker by Amershi et al. allows visual interactions from mislabeled data, missing features identification, insights into insufficiency of training data for label learning, the impact of outliers, feature space visualization, model summary from performance, etc., a model-agnostic approach in debugging \[[4](#refbib.xhtml#refbib_4)\]. Neural stethoscopes by Fuchs et al. are another general-purpose framework that analyzes the learning process by quantifying the importance of influential factors by promoting and suppressing information \[[90](#refbib.xhtml#refbib_90)\].
    
*   **Adversarial Attacks and Defense**: Adversarial examples are artificially engineered inputs to feed into the models and judge their ability to discriminate. Constructing adversarial examples needs an understanding of input spaces and the boundaries between classes in classification problems. Adversarial attacks and defense are two different ways to explore the models from an explainability and diagnostic perspective \[[291](#refbib.xhtml#refbib_291), [295](#refbib.xhtml#refbib_295)\]. Black-box and white-box attacks are two main types of adversarial attacks that generate examples to deceive the model \[[76](#refbib.xhtml#refbib_76), [86](#refbib.xhtml#refbib_86), [233](#refbib.xhtml#refbib_233)\]. Recent research shows that adding imperceptible noise by perturbing inputs reveals model vulnerabilities \[[178](#refbib.xhtml#refbib_178)\]. Adversarial defense is about making the model robust against adversarial examples. Two common methods of adversarial defense are (i) adversarial training, in which the training dataset is augmented with adversarial examples to introduce robustness, and (ii) perturbation removal, in which the model identifies adversarial examples and rejects them \[[95](#refbib.xhtml#refbib_95), [218](#refbib.xhtml#refbib_218)\].
    
*   **Fairness and Bias**: One of the key goals for many models deployed in critical areas impacting humans is to be “fair” and unbiased in its decision-making process. Though an evolving field, fairness implies (i) group fairness, also called demographic parity or statistical parity, focusing on race, gender, sexual orientation, etc. \[[34](#refbib.xhtml#refbib_34)\], and (ii) individual fairness, focusing on individuals with similar features and characteristics generating similar model output \[[82](#refbib.xhtml#refbib_82)\]. Different techniques to address fairness can be classified as (i) pre-processing methods, removing sensitive features from the data, (ii) in-process methods, where fairness constraints are added, and (iii) post-processing methods to adjust the model predictions after training \[[30](#refbib.xhtml#refbib_30), [36](#refbib.xhtml#refbib_36), [96](#refbib.xhtml#refbib_96), [139](#refbib.xhtml#refbib_139)\].
    

## 7.3 EXPLAINABLE METHODS TAXONOMY

There are many surveys on explainable AI where different strategies have generated many taxonomies for categorizing explainability techniques. The Xie et al. taxonomy, based on foundational explainability methods, restricted only to generic or specific transformer-based models, is discussed in this section and as shown in [Fig. 7.1](#ch7.xhtml#fig7_1).

![Figure 7.1 Explainable methods taxonomy.](images/fig7_1.jpg)

[Figure 7.1](#ch7.xhtml#b7fig7_1) Explainable methods taxonomy.

### 7.3.1 Visualization Methods

Visualization methods reveal an explanation by highlighting the influence between the inputs and the outputs in a black-box model as shown in [Fig. 7.2](#ch7.xhtml#fig7_2). A common way to visualize and explain is through saliency maps, highlighting the most salient inputs that maximally influence model behavior. Xie et al. further break visualization methods into backpropagation-based and perturbation-based visualizations.

![Figure 7.2 Visualization methods. Vary based on different saliency techniques S(E) applied to inputs and hidden layers with respect to the output.](images/fig7_2.jpg)

[Figure 7.2](#ch7.xhtml#b7fig7_2) Visualization methods. Vary based on different saliency techniques *S*(*E*) applied to inputs and hidden layers with respect to the output.

#### 7.3.1.1 Backpropagation-based

Using the gradient signals passed from output to input during training to understand the saliency of input data is the typical procedure in this group.

*    **Activation maximization**: In their seminal work, Erhan et al. introduce a generic way to visualize the important features of any layer of a network by noting that the activation *a*[*j*]^(*i*), corresponding to the activation of unit *i* and layer *j*, can be maximized by keeping parameters *θ* fixed and optimizing the input **x**\[[85](#refbib.xhtml#refbib_85)\]. The general principle is to optimize the input **x** by computing the gradient of *a*[*j*]^(*i*)(**x**, **θ**) and updating the input **x** in the direction of the gradient.
    
*   **Layer-wise Relevance Propagation (LRP)**: The LRP-based technique measures the relevance of each input feature to the output of the network \[[14](#refbib.xhtml#refbib_14), [73](#refbib.xhtml#refbib_73), [147](#refbib.xhtml#refbib_147), [188](#refbib.xhtml#refbib_188)\]. The most generic type of LRP is the Deep Taylor Decomposition based on the assumption that *f*, the network, is differentiable and can be approximated by a Taylor expansion of *f* at some root $\\hat{\\mathbf{x}}$ for which $f(\\hat{\\mathbf{x}}) = 0$. The choice for the root point is such that for it to be insignificantly different from the input **x** for which *f* generates a different prediction \[[187](#refbib.xhtml#refbib_187)\].
    
      
    $$\\begin{array}{l} {f(\\mathbf{x}) = f(\\hat{\\mathbf{x}}) + \\nabla\_{\\hat{\\mathbf{x}}}f \\cdot (\\mathbf{x} - \\hat{\\mathbf{x}}) + \\epsilon} \\\\ \\end{array}$$  
    (7.1)
    
      
    $$\\begin{array}{l} {f(\\mathbf{x}) = {\\sum\\limits\_{i}^{N}\\frac{\\partial f}{\\partial x\_{i}}}(\\hat{x\_{i}}) \\cdot (x\_{i} - \\hat{x\_{i}}) + \\epsilon} \\\\ \\end{array}$$  
    (7.2)
    
    where *ϵ* sums up all second order and higher terms in the Taylor expansion. The relevance score for the inputs can be derived from the above equation as
    
      
    $$\\begin{array}{l} {r\_{i} = \\frac{\\partial f}{\\partial x\_{i}}(\\hat{x\_{i}}) \\cdot (x\_{i} - \\hat{x\_{i}})} \\\\ \\end{array}$$  
    (7.3)
    
    For a deep network with multiple layers, the Deep Taylor Decomposition assumes decomposition of the relevance scores, starting from the output to the input through the intermediate layers. The relevance score of node *i* at layer *l*, connected to *M* nodes at layer *l* + 1 is assumed to be decomposable and given by:
    
      
    $$\\begin{array}{l} {r\_{i}^{l} = {\\sum\\limits\_{j}^{M}r\_{i,j}^{l}}} \\\\ \\end{array}$$  
    (7.4)
    
*   **Deep Learning Important FeaTures (DeepLIFT)**: Shrikumar et al. proposed Deep Learning Important FeaTures (DeepLIFT) where the relevance scores are assigned to the input features based on the difference between the input **x** and a “reference” input **x**^′, where **x**^′ is problem specific \[[228](#refbib.xhtml#refbib_228)\]. The choice of the reference input **x**^′ is domain specific. For example, in MNIST classification, input with all zeros representing the common background can be one of the choices for the reference input.
    
    *Δ**t* = *f*(**x**) − *f*(**x**^′) is the difference in neuron output between input **x** and a reference input **x**^′. The relevance score *R*[*Δ**x*[*i*]*Δ*[*t*]] assigned for the input feature *x*[*i*] with *N* neurons necessary to compute *t* is given by:
    
      
    $$\\begin{array}{l} {\\Delta t = {\\sum\\limits\_{i = 1}^{N}R\_{\\Delta x\_{i}\\Delta t}}} \\\\ \\end{array}$$  
    (7.5)
    
    Shrikumar et al. provide different ways to calculate the weighting between the influence *Δ**x*[*i*] had on *Δ**t* using *Linear* rule, *Rescale* rule and *RevealCancel* rule. Defining a multiplier *m*[*Δ***x***Δ*[*t*]] which measures the relevance of *Δ***x** with respect to *Δ**t*, averaged by *Δ***x** as:
    
      
    $$\\begin{array}{l} {m\_{\\Delta\\mathbf{x}\\Delta t} = \\frac{R\_{\\Delta\\mathbf{x}\\Delta t}}{\\Delta\\mathbf{x}}} \\\\ \\end{array}$$  
    (7.6)
    
    Layer by layer computation of relevance scores using chain rule is adopted in the DeepLIFT paper. Arkhangelskaia and Dutta apply DeepLIFT on the BERT model predictions and test the outcomes to monitor shifts in the attention values for input for the question-answering application \[[8](#refbib.xhtml#refbib_8)\].
    
*   **Integrated Gradients (IG)**. Integrated gradients by Sundarajan et al. is an explanation technique by computing relevance for a network *f* based on two axioms: sensitivity and implementation variance \[[236](#refbib.xhtml#refbib_236)\]. The sensitivity axiom: for an input **x** which differs from some baseline input **x**^′ along feature *x*[*i*] and *f*(**x**) ≠ *f*(**x**^′) then *x*[*i*] should have a non-zero relevance. The implementation invariance: for two networks *f*[1] and *f*[2] when outputs are equal for all possible inputs, the relevance score for every input feature *x*[*i*] should be identical over *f*[1] and *f*[2].
    
    If *f* is the deep network with input **x** and a baseline input **x**^′ where the outputs are \[0,1\], the relevance of feature *x*[*i*] of the input **x** over *f* is taken as integral of gradients through the path from **x**^′ to **x** and is given by:
    
      
    $$\\begin{array}{l} {IG\_{i}(\\mathbf{x}) = (x\_{i} - x\_{i}^{\\prime}){\\int\_{0}^{1}\\frac{\\partial f(\\mathbf{x}^{\\prime} + \\alpha(\\mathbf{x}) - \\mathbf{x}^{\\prime})}{\\partial x\_{i}}}} \\\\ \\end{array}$$  
    (7.7)
    
    where *α* is smoothly distributed in the range \[0,1\] and is associated with the path from **x**^′ to **x**. The above equation can be approximated using Riemann summation using appropriate number of steps as described in the paper.
    

#### 7.3.1.2 Perturbation-based

Altering the input and computing the feature relevance by comparing the difference in the output between the original and altered input is the core of all perturbation-based methods.

*   **Representation Erasure**: Li et al. propose a generic technique for an explanation by examining the effect of erasing the input representation to see how such changes affect the output \[[157](#refbib.xhtml#refbib_157)\]. By analyzing the impact, one can identify essential representations that significantly contribute to the models' decisions. The erasure can be performed on various levels of representation, such as the input word-vector dimensions, input words or group of words, and intermediate hidden units. The straightforward technique is to compute the difference in log-likelihood on the labels when representations are erased. A more sophisticated method uses the reinforcement learning model to find the minimal set of words that must be erased to change the model's decision.
    
*   **Meaningful Perturbation**: Fong and Vedaldi propose a meta-predictor using the perturbation technique to give local explanations based on the sensitive areas in the input that predicted the output \[[89](#refbib.xhtml#refbib_89)\]. The authors propose three classes of perturbations to generate visual explanations for image classification: (i) constant, replacing a region in the image with a constant value, (ii) noise, adding small noise to the region, and (iii) blur, blurring the region. For example, an explanation for a black-box image classifier (*f*) that predicts dog will be given by
    
      
    $$\\begin{array}{l} \\left. D(\\mathbf{x},f) = \\{\\mathbf{x} \\in \\mathbf{X}\_{d}\\Leftrightarrow f(\\mathbf{x}) = 1\\} \\right. \\\\ \\end{array}$$  
    (7.8)
    
    where *f*(**x**) = 1 prediction of dog in the image and **X**[*d*] is all images that the classifier predicts as dog. For a new image **x**⁰, the explanation technique creates perturbation in the input using the techniques described above to find locally sensitive areas that result in *f*(**x**⁰) per the explanation rules.
    
*    **Prediction Difference Analysis**: Zintgraf et al. propose a method based on Robnik-Sikonja and Kononenko research, to measure the influence based on altering input information for probabilistic-based classifiers \[[210](#refbib.xhtml#refbib_210), [304](#refbib.xhtml#refbib_304)\]. It evaluates the effect of an input feature *x*[*i*] with respect to class *c* by determining the difference between *p*(*c*|**x**[ − *i*] and *p*(*c*|**x**) using the marginal probability
    
      
    $$\\begin{array}{l} {p(c|\\mathbf{x}\_{- i}) = {\\sum\\limits\_{x\_{i}}p}(x\_{i}|\\mathbf{x}\_{- i})p(c|\\mathbf{x}\_{- i},x\_{i})} \\\\ \\end{array}$$  
    (7.9)
    
    where *m**a**t**h**b**f**x* corresponds to all input features and **x**[ − *i*] corresponds to all features except *x*[*i*]. The importance of the feature *x*[*i*] is measured using:
    
      
    $$\\begin{array}{l} {\\text{Diff}\_{i}(c|\\mathbf{x}) = {\\log}\_{2}(\\text{odds}(c|\\mathbf{x})) - {\\log}\_{2}(\\text{odds}(c|\\mathbf{x}\_{- i}))} \\\\ \\end{array}$$  
    (7.10)
    

### 7.3.2 Model Distillation

Xie et al. refer to the model distillation category as a post-training method where the encoded knowledge in the model is distilled into a representation agreeable for an explanation by a user, as shown in [Fig. 7.3](#ch7.xhtml#fig7_3). Xie et al. further divides this category into two subcategories: local approximation and model translation.

![Figure 7.3 Model distillation.](images/fig7_3.jpg)

[Figure 7.3](#ch7.xhtml#b7fig7_3) Model distillation.

#### 7.3.2.1 Local approximation

All local approximation methods hypothesize that learning local boundaries in a manifold is much simpler than learning a global discriminating model over an entire space \[[15](#refbib.xhtml#refbib_15)\]. For example, a simple linear classifier can discriminate a subset of the data over a dense region in a manifold and offers a simple explanation for instances in that area. We will discuss few popular techniques that can be employed in model agnostic way.

*   **Local Interpretable Model-agnostic Explanations (LIME)**: Ribeiro et al. developed one of the most popular local approximation methods called Local Interpretable Model-agnostic Explanations (LIME) \[[208](#refbib.xhtml#refbib_208)\]. LIME generates new sample instances by perturbing any given instance of interest in its manifold proximity, measures the model outputs for each sample, and fitting a local linear interpretable model to the new samples. Thus by covering most instances and predictions from the global model, many local easily interpretable models like linearly weighted classifier/regressor or decision trees are built. Let us represent the entire deep learning model through function *f*, data instance of interest *x*, an explanation model *h* selected from a class ℋ of interpretable models such as linear, logistic, or decision tree, the problem of identifying a local explainable model is then equivalent to optimizing for the objective *ζ*(*x*):
    
      
    $$\\begin{array}{l} {\\zeta(x) = \\underset{h \\in \\mathcal{H}}{\\text{arg}\\,\\text{min}}\\,\\mathcal{L}({f,h,\\pi\_{x}(z)}) + \\Omega(h)} \\\\ \\end{array}$$  
    (7.11)
    
    where *π*[*x*] is a kernel function that weighs a sample *z* based on its distance to the instance of interest *x*, ℒ is a loss function and Ω is a complexity penalty such as the tree depth in decision tree. The loss function ℒ provides a metric of how close the explanation model approximates the real model *f* in the locality of instance *x*.
    
*   **SHapley Additive exPlanations (SHAP)**: Shapley values have foundations in game theory, particularly cooperative game theory. One can view each feature as a player in a game, and the goal is to distribute payouts fairly among players who form a coalition based on their contribution to the total payout. The marginal contribution of each feature averaged across the set of all possible coalitions of features gives the Shapley values.
    
    Let us represent the entire deep learning model through function *f*, input with *d* features **x** = {*x*[1], *x*[2], …, *x*[*d*]}, the Shapley value *ϕ*[*j*] for the *j*\-th feature is given by
    
      
    $$\\begin{array}{l} {\\phi\_{j}(f) = \\frac{|S|!(d - |S| - 1)!}{d!}\\lbrack{f({S \\cup \\{ x\_{j}\\}}) - f(S)}\\rbrack} \\\\ \\end{array}$$  
    (7.12)
    
*   **Anchors**: Anchors overcome limitations of many local explanation methods that use linear approximations for defining local behaviors. For many real-world domains, the linear approximation may lead to inaccurate decisions. Anchors are a high-precision explanation technique for generating local explanations by inferring a set of if-then rules in the feature space \[[209](#refbib.xhtml#refbib_209)\]. These rules serve as “anchors” for a set of features making it more robust against changes and on unseen data.
    
    If *x* represents the instance for explanation, *A* represents a set of predicates, i.e., the resulting rule or anchor, such that *A*(*x*) = 1, *f* represents the black-box model, *D* represent a known distribution of perturbations, *z* is a sample drawn from the conditional distribution when rule *A* applies *D*(*z*|*A*), and *τ* is the given precision threshold, then the anchor definition is given by:
    
      
    𝔼[*D*(*z*|*A*)]\[∥[*f*(*x*) = *f*(*z*)]\] ≥ *τ*, *A*(*x*) = 1  
    (7.13)
    
    In general, finding anchors is infeasible in a continuous space, and by introducing a parameter *δ*, the definition can be changed in terms of probability to meet this precision threshold for some arbitrarily small *δ* as given by:
    
      
    $$\\begin{array}{l} {\\Pr\\lbrack{\\rho(A) \\geq \\tau}\\rbrack \\geq 1 - \\delta} \\\\ \\end{array}$$  
    (7.14)
    
    Since there may be several anchors that meet this criterion, preference is given to the anchors with the highest coverage *c**o**v*(*A*), defined as
    
      
    $$\\begin{array}{l} {cov(A) = \\mathbb{E}\_{D(z)}\\lbrack A(z)\\rbrack} \\\\ \\end{array}$$  
    (7.15)
    
    If *A*^′ is the set of anchors that satisfy (7.14), then anchor generation then becomes a combinatorial optimization problem given by:
    
      
    $$\\begin{array}{l} {\\underset{A \\in A^{\\prime}}{\\max}\\,\\, cov(A)} \\\\ \\end{array}$$  
    (7.16)
    
    In practice, various heuristics-based approaches are used. For example, a greedy search technique such as a bottom-up approach where you start with an empty rule set and generate a set of candidate rules by iteratively extending an anchor by one additional feature predicate creates this rule set in a greedy way. Beam-search can be used to improve upon this greedy search method by maintaining a candidate set of rules during the iterative search process.
    

#### 7.3.2.2 Model translation

Model translation involves training an alternative “smaller” model on the entire dataset as input and outputs coming from the black-box model as the training data. Thus, this captures the global behavior in an explainable way as compared and contrasted with the local approximation techniques described above. The choice of the alternative model can be based on model size, ease of deployment, and explainable algorithm (e.g., decision tree, rule-based classifier, graphs, etc.) \[[21](#refbib.xhtml#refbib_21), [112](#refbib.xhtml#refbib_112), [118](#refbib.xhtml#refbib_118), [288](#refbib.xhtml#refbib_288)\]. The Tan et al. proposal to build a generic additive explainable model by decomposing the black-box model into explainable models such as splines or bagged trees and then build additive models using them is one such technique \[[240](#refbib.xhtml#refbib_240)\].

### 7.3.3 Intrinsic Methods

Intrinsic methods use the model architecture as is, and explanations are provided using the representations, for example, weights of hidden layers or the attention weights \[[207](#refbib.xhtml#refbib_207)\]. Intrinsic methods can be further classified into (i) probing mechanism-based and (ii) joint training-based.

#### 7.3.3.1 Probing mechanism

Over the last few years, the idea of inserting a simple layer (e.g., one layer neural classifier) on top of either the attention heads or any intermediate layers of a deep learning model already trained on a primary task to validate “information” (auxiliary tasks) as a way to diagnose or explain has been an emerging trend. For example, on a BERT model trained for sentiment classification, one can insert a probe classifier on top of the intermediate layers in the trained model to measure the ability to identify linguistic information. The probe classifier can be used to validate information at the syntactic level, such as verbs, nouns, etc., and semantic level, such as recognizing entity, relations, entailment, etc., useful in the overall primary task of sentiment classification. A dataset with original sentences used for sentiment classification and labels identifying verbs, nouns, entities, etc., is created. The probe classifier to measure the performance of any layer then undergoes training and testing on the new auxiliary tasks by freezing the information at those layer(s), thus giving the quantitative measure of the layer in identifying or explaining \[[23](#refbib.xhtml#refbib_23)\].

Representation Probing In one of the earliest works, Hupkes et al. proposed the concept of probing using “diagnostic classifiers” to unveil how recurrent and recursive networks process hierarchical structures using arithmetic language tasks with exact syntax and semantics and a limited vocabulary \[[128](#refbib.xhtml#refbib_128)\]. Furthermore, it showed how neural architectures process languages with hierarchical compositional semantics and probe a black-box neural architecture for NLP tasks.

Conneau et al. introduced probing tasks to comprehensively score different neural architectures on different tasks to understand and quantify the linguistic properties of the sentence embeddings learned on the encoders \[[62](#refbib.xhtml#refbib_62)\]. They created probing tasks categorized as surface information, syntactic information, and semantic information. Surface information probing tasks answers questions; for example, “do the sentence embeddings preserve the sentence lengths?”, using a classification dataset with sentence length as labels. Syntactic information probing tasks investigates syntax-based properties, for example, “are the embeddings sensitive to word order?”, using a classification dataset with bigrams shifted as positives and non-shifted as negatives. Finally, semantic information probing tasks investigate semantics-based attributes retained in the embeddings, for example, “can the embeddings understand tenses?”, using a tense classification dataset where VBP/VBZ forms are labeled as present and VBD as past tense. The comprehensive experiments in this work with different architectures and downstream tasks provided great insights into model architectures and their ability to preserve different linguistic properties.

Tenney et al. introduced “edge probing” to understand the hidden representation in deep learning architectures such as ELMO, GPT and BERT \[[245](#refbib.xhtml#refbib_245)\]. It investigates the role of the word in each position to encode structural, syntactic, semantic, and even long-range phenomena by freezing the layers and using a neural classifier to train and test on various tasks such as part-of-speech tagging (POS), constituent labeling, dependency labeling, named entity labeling, semantic role labeling (SRL), coreference, semantic proto-role and relation Classification. They show that contextualized embeddings improve over their non-contextualized equivalents, mostly on syntactic tasks compared to semantic tasks.

Tenney et al., in their work, further found that a model like BERT can rediscover linguistic information similar to a traditional NLP pipeline in an interpretable and localizable way \[[244](#refbib.xhtml#refbib_244)\]. They discovered the sequence: POS tagging, parsing, NER, semantic roles, coreference are part of the overall BERT model. They introduce two complementary metrics: scalar mixing weights and cumulative scoring. Scalar mixing weights is a training corpus-dependent metric highlighting layers that are most relevant for the probing classifier in the whole BERT model. Cumulative scoring is an evaluation set-dependent metric estimating how much higher a score one can obtain on a probing task with the introduction of each layer.

Hewitt and Liang, in their work, devise a control task strategy as a measure to address the probing confounder problem \[[110](#refbib.xhtml#refbib_110)\]. Probing confounder problem can be defined as—given the main neural architecture that needs to be explained, the probing classifier such as MLP or logistic regression and the supervised auxiliary task, how do we assign the credit for performance such as test accuracy to either of the three? They devise control tasks that can be easily learned by a probing diagnostic classifier but not encoded in the representations (actual neural model or layers). Evaluating the performance (testing accuracy) difference between the control tasks and auxiliary tasks with different probing classifier choices as a selectivity measure can easily assign the credit of learning to either the representation or the probing classifier. The work also answers questions such as “how does the probe design affect probing task performance?” and “can the probes pick spurious signals?”.

Attention Probing Probing either by adding an attention layer on top of an existing neural architecture or using existing attention weights from a layer of deep learning, mapping it to the inputs as “attention maps” to explore the relationship between the two is soon developing as an effective explanation technique.

Rocktäschel et al. proposed a neural word-by-word attention mechanism in a sequence-to-sequence network for reasoning over entailments of pairs of words and phrases \[[211](#refbib.xhtml#refbib_211)\]. Visualizations of word-by-word attention between the premise and hypothesis show that irrelevant parts of the premise, such as words capturing little meaning, are correctly neglected for entailment. The premise and hypothesis connected via deeper semantics show proper relevancy through the attention weights.

Xu et al. use an attention mechanism for automatic image captioning tasks \[[278](#refbib.xhtml#refbib_278)\]. The work shows that the attention mechanism not only achieves state-of-the-art results but highlights salient objects in the image while generating the corresponding words in the output sequence, thus useful for explanations.

Yang et al. employ a hierarchical attention mechanism for document classification \[[286](#refbib.xhtml#refbib_286)\]. The two levels of attention mechanisms, one at the word level and another at the sentence level, enable the model to attend differentially to content when building the document representation. Visualization of the attention layers demonstrates that the model selects informative words and sentences for classification.

Jesse Vig introduced a tool “BertViz” for visualizing attention in the Transformer at all levels, viz. at the whole model level, the attention-head level, and the individual neuron level \[[255](#refbib.xhtml#refbib_255)\]. The model view provides a single high-level view of the entire model across all the layers and heads for a given input. The model view helps in visualizing how attention patterns evolve in the attention heads across all layers. The attention-head view visualizes the attention patterns produced by one or more attention heads in a given layer and can help detect biases such as gender bias. The neuron view visualizes the individual neurons in the query and key vectors and their interaction producing attention, thus giving a detailed view of how the patterns are formed.

#### 7.3.3.2 Joint training

In a joint training-based approach, the explanation task is associated with the actual learning task so that the model learns the explanation and the actual task jointly. The explanation task can be generating explanations in a natural language format or associating inputs with human-understandable concepts, or learning prototypes for the data that can be used as an explanation.

Creating user (expert or layman) friendly explanations at the prediction time by augmenting the deep learning architecture with a text explanation generation component and learning the explanations along with the original task is an evolving explainability approach \[[37](#refbib.xhtml#refbib_37), [109](#refbib.xhtml#refbib_109), [111](#refbib.xhtml#refbib_111), [166](#refbib.xhtml#refbib_166), [293](#refbib.xhtml#refbib_293)\]. Most approaches need explanations as part of training data along with the labeled data for the main task, which makes this approach prohibitively costly.

Associating input features (words or image components) or latent features with concepts or objects as a method of explanation either by associating saliency maps with inputs or latent activations with semantic concepts using regularization terms or changes to models is another method in this category \[[3](#refbib.xhtml#refbib_3), [77](#refbib.xhtml#refbib_77), [131](#refbib.xhtml#refbib_131), [153](#refbib.xhtml#refbib_153)\].

Many computer vision-based architectures, especially in classification problems, learn prototypes from the training process that can be then used to associate with new unseen instances as an explanation \[[40](#refbib.xhtml#refbib_40), [159](#refbib.xhtml#refbib_159)\].

## 7.4 Attention and Explanation

As discussed in the previous section, one of the emerging patterns, especially in NLP, is to associate the magnitude of the attention weights with the inputs and use it to interpret the model behavior. Next, we discuss few papers and the research that impacts how one views attention mechanisms and their contribution towards explainability.

### 7.4.1 Attention is Not an Explanation

In this paper, Jain and Wallace try to ask fundamental questions on attention and their interpretations \[[132](#refbib.xhtml#refbib_132)\]. For example, when we create an attention map as shown in [Fig. 7.4](#ch7.xhtml#fig7_4) that correlates attention weights directly to the input tokens or weights, the impact of many transformations or computations such as intermediate hidden states, query vectors, attention techniques is not taken into account. The paper poses two crucial questions—(i) do the attention heat maps reveal the importance of words/tokens? (ii) does the attention mechanism provide us with transparency, i.e., how did the model reach the prediction?

![Figure 7.4 Attention probing with contextualized bidirectional LSTM as the neural model and an attention layer.](images/fig7_4.jpg)

[Figure 7.4](#ch7.xhtml#b7fig7_4) Attention probing with contextualized bidirectional LSTM as the neural model and an attention layer.

These abstract questions can be mapped to the following hypotheses for verification:

1.  Attention weights should correlate with feature importance measures that have the semantics associated with them (e.g., gradient-based measures and leave-one-out)
    
2.  Had we attended to different inputs, would the predictions be different?
    

Different NLP tasks such as text classification, question answering (QA), and Natural Language Inference (NLI) using contextualized BiLSTM and non-contextualized feedforward network with a standard attention mechanism is used for analyses.

#### 7.4.1.1 Attention weights and feature importance

For the first hypothesis, the words from inputs are ranked on attention weights and on feature importance scores (gradients and leave-one-out), and the Kendal tau measure is used to measure correlation. The semantics associated with the feature importance scores, the experiment measures the output changes by perturbing individual words with the same attention and context.

The algorithm follows a straightforward process, first encode the input to get the hidden states (**h**←Enc(**x**)) , compute the attention(*α̂*←softmax(*ϕ*(**h**,**Q**))) and the output (*ŷ*←Dec(**h**,**Q**)) .

For the gradient-based method, the gradient is computed with respect to each of the input to get the gradient score and the correlation score:

  
$$\\begin{array}{l} \\left. g\_{t}\\leftarrow|{\\sum\\limits\_{w = 1}^{|V|}1}\\lbrack\\mathbf{x}\_{tw} = 1\\rbrack\\frac{\\partial y}{\\partial\\mathbf{x}\_{tw}}|,\\forall t \\in \\lbrack 1,T\\rbrack \\right. \\\\ \\end{array}$$  
(7.17)

  
$$\\begin{array}{l} \\left. \\tau\_{g}\\leftarrow\\text{Kendall}\\tau(\\alpha,g) \\right. \\\\ \\end{array}$$  
(7.18)

For the leave-one-out method, one word is removed at a time, and Total Variation Distance (TVD) is used as a measure to compute the change in the distributions of output and the correlation score:

  
$$\\begin{array}{l} \\left. \\Delta{\\hat{y}}\_{t}\\leftarrow\\text{TVD}(\\hat{y}(\\mathbf{x}\_{- t}),\\hat{y}(\\mathbf{x})),\\forall t \\in \\lbrack 1,t\\rbrack \\right. \\\\ \\end{array}$$  
(7.19)

*The experiments show a consistently low correlation between the attention weights and feature importance scores across all the datasets, especially for contextualized encoders*.

#### 7.4.1.2 Counterfactual experiments

To validate the second hypothesis, the authors put forth two empirical questions

1.  How much does the output change if the attention scores are randomly permutated?
    
2.  Can we find maximally different attention that does not change the output more than a predefined threshold epsilon?
    

##### Attention Permutation

[Algorithm 2](#ch7.xhtml#algo7_2) captures the experiment to characterize the model behavior when attention weights are shuffled

![Algorithm 1: Permuting attention weights.](images/comp7_1.jpg)

**Algorithm 1:** Permuting attention weights.

*The results for this experiment are different for different datasets. Some datasets highlight that the attention weights might infer explaining an output by a small set of features, but where perturbing the attention makes little difference to the prediction, while for other datasets, this was not observed.*

##### Adversarial attention

The intuition for this experiment is to explore new attention weights that differ as much as possible from the observed attention distribution and yet give the exact prediction. A *ϵ* value is specified to simplify the optimization process that defines the slight change in the prediction. Once the *ϵ* value is given, the aim to find k adversarial distributions {*α*^((1)), ⋯, *α*^((*k*))}, such that each *α*^(*i*) maximizes the distance from original *α̂* but does not change the output by more than *ϵ*. The Jensen-Shannon Divergence is used to measure the difference between the distributions. The optimization equation is given by:

  
$$\\begin{array}{l} {\\text{maximize}\_{\\alpha^{(1)},\\cdots,\\alpha^{(k)}}f({\\{\\alpha^{(i)}\\}}\_{i = 1}^{k})} \\\\ \\end{array}$$  
(7.20)

where *f*({*α*^((*i*))}[*i* = 1]^(*k*)) is:

  
$$\\begin{array}{l} {{\\sum\\limits\_{i = 1}^{k}\\text{JSD}}\\lbrack\\alpha^{(i)},\\hat{\\alpha}\\rbrack + \\frac{1}{k(k - 1)}{\\sum\\limits\_{i < j}^{k}\\text{JSD}}\\lbrack\\alpha^{(i)},\\alpha^{(j)}\\rbrack} \\\\ \\end{array}$$  
(7.21)

The first part of the equation $\\sum\_{i = 1}^{k}{JSD\\lbrack\\alpha^{(i)},\\hat{\\alpha}\\rbrack}$ finds maximally different attention from the observed *α̂* and the second part $\\frac{1}{k(k - 1)}{\\sum\_{i < j}^{k}{JSD\\lbrack\\alpha^{(i)},\\alpha^{(j)}}}$ is maximally different from each other. The adversarial attention finding algorithm can be summarized as:

![Algorithm 2: Finding adversarial attention weights.](images/comp7_2.jpg)

**Algorithm 2:** Finding adversarial attention weights.

Similar to the permutation attention weights experiments, the results for the adversarial attention experiments also varied based on the data.

*The attention distribution does not uniquely characterize why a particular prediction was made by the model as you can find alternative attention heatmaps that give the same predictions*.

The overall conclusion drawn from the research was—attention does not provide a consistent interpretation of why a model made a particular prediction.

### 7.4.2 Attention is Not Not an Explanation

Wiegreffe and Pinter contest the claims and assumptions made by Jain and Wallace in the research above and show through experiments the usefulness of attention mechanisms for explainability \[[269](#refbib.xhtml#refbib_269)\]. Wiegreffe and Pinter's main contention from Jain and Wallace's research is that their “explanation” study is ambiguous, correlation experiments are insufficient, and the adversarial weight experiments were vague and impractical.

Contextualizing explainability in AI literature and the NLP domain shows two forms of explanations—(i) plausible explanation and (ii) faithful explainability. The goal of plausible explanation is to provide human-understandable rationales for the model's behavior. The plausible explanation is subjective and requires human-in-the-loop to judge whether the explanation is justified and builds trust in the model. Faithful explainability is a more rigorous form of explanation and aligns more closely with the desired properties of transparency and interpretability and what the authors explore in their work. The goal of the technique is to quantify the correlation between the input (tokens/words) and the output (predictions) for a predictive task. One of the requisite for this form of explanation is that—model explanations are exclusive, i.e., a predictive model should exhibit one set of behavior for one reasoning process.

The authors lay the following three requirements for faithful explanations for attention mechanisms.

1.  Attention mechanism should be a NECESSARY component for good model performance.
    
2.  Attention distributions should be hard to manipulate, i.e., if any trained model can vary the distribution of attention weights and yet have similar predictions, they may not be suitable for the explanation. This directly corresponds to the exclusivity requisite for faithful explanations and will guide the search for adversarial models.
    
3.  Attention distributions should work well in uncontextualized settings. Since the attention weights are typically learned on contextualized hidden layer outputs, to see the impact on input tokens, one needs to use uncontextualized settings to judge their usefulness.
    

#### 7.4.2.1 Is attention necessary for all tasks?

The authors use the same three sets of tasks and six classification datasets using the BiLSTM model from the Jain and Wallace setting and create another model where the attention weights are uniform in distribution compared to the learned weights. Based on the F1 scores on all six classification datasets comparing the uniform and learned attention weights, the news datasets show no variations and hence are not used for the subsequent two analyses. The Stanford Sentiment Treebank (SST) is a borderline case and shows a small difference as compared to the MIMIC (III) and IMDB dataset.

#### 7.4.2.2 Searching for adversarial models

To find attention weight distributions that mimic the base model predictions, the authors propose a model-consistent training protocol for finding adversarial attention distributions through a combined parameterization that holds for all training examples. The two measures they employ for the adversarial training are Total Variation Distance (TVD) and Jensen-Shannon Divergence (JSD).

Total Variation Distance (TVD) is used for comparing the class predictions from two models and is given by:

  
$$\\begin{array}{l} {\\text{TVD}({\\hat{y}}\_{1},{\\hat{y}}\_{2}) = \\frac{1}{2}{\\sum\\limits\_{i = 1}^{|y|}|}{\\hat{y}}\_{1i} - {\\hat{y}}\_{2i}|} \\\\ \\end{array}$$  
(7.22)

Jensen-Shannon Divergence (JSD) is used for comparing the two attention distributions and is given by:

  
$$\\begin{array}{l} {\\text{JSD}(\\alpha\_{1},\\alpha\_{2}) = \\frac{1}{2}\\text{KL}\\lbrack\\alpha\_{1}\\|\\overline{\\alpha}\\rbrack + \\frac{1}{2}\\text{KL}\\lbrack\\alpha\_{2}\\|\\overline{\\alpha}\\rbrack\\,\\text{where}\\,\\overline{\\alpha} = \\frac{\\alpha\_{1} + \\alpha\_{2}}{2}} \\\\ \\end{array}$$  
(7.23)

The adversarial training algorithm is first to train a base model(*M*[*b*]). Then train an adversarial model (*M*[*a*]) that minimizes the output prediction score from the base model yet maximizing the changes in the learned attention distribution from the base model using following instance-wide loss function:

  
$$\\begin{array}{l} {\\mathcal{L}(M\_{a},M\_{b}) = \\text{TVD}({\\hat{y}}\_{1}^{(i)},{\\hat{y}}\_{2}^{(i)}) - \\lambda\\text{KL}(\\alpha\_{a}^{(i)}\\|\\alpha\_{b}^{(i)})} \\\\ \\end{array}$$  
(7.24)

where *ŷ*^((*i*)) and *α*(i) denote predictions and attention distributions for an instance i, and *λ* controls the trade-off between the prediction distance and attention distribution changes.

For the diabetes dataset (and the anemia and the IMDB), they find it challenging to find adversarial weights that produce divergent attention weights and not losing the predictive performance, thus supporting the use of attention for the faithful explanation. On the contrary, Stanford Sentiment Treebank (SST) dataset shows no use of attention weights for the faithful explanation.

#### 7.4.2.3 Attention Probing

To validate if the attention distributions work well in uncontextualized settings, the attention weights from the BiLSTM are imposed on an uncontextualized trained MLP layer with the bag of word-vector representation. Thus, high performance in the task implies that attention scores capture the relationship between the input and the output. Except for Stanford Sentiment Treebank (SST) dataset, every task and dataset shows the BiLSTM trained attention weights outperforming the MLP and the uniform weights, indicating the usefulness of attention weights.

In conclusion, the research has laid down three essential components for validating the usefulness of the attention mechanism and three methods to quantify it for faithful explanation. The usefulness of the attention mechanism is shown to be task dependent.

## 7.5 Quantifying Attention Flow

As discussed in the previous two sections, correlating the attention weights to inputs for explanation in a simple BiLSTM with a single attention layer before the output itself is an open research topic. In transformers with self-attention, multiple attention heads, and many attention layers in the encoder, the problem becomes even more difficult. In their research, Abnar and Zuidema propose a couple of techniques to resolve this problem, viz., Attention Rollout and Attention Flow, both compute attention scores at each layer from that layer to the input tokens (i.e., token attention) for visualization and interpretation \[[1](#refbib.xhtml#refbib_1)\]!

### 7.5.1 Information Flow as DAG

The attention module in transformers at any layer has a residual connection from the input, so values (*V*) at any layer *l* + 1 is given by *V*[*l* + 1] = *V*[*l*] + *W*[*a**t**t*]*V*[*l*] where *W*[*a**t**t*] is the attention matrix. The authors propose adding identity matrix *I* and calculating the raw attention updated by residual connections as:

  
$$\\begin{array}{l} {A = 0.5 \\cdot W\_{att} + 0.5 \\cdot I \\cdot A} \\\\ \\end{array}$$  
(7.25)

This equation can be used to create an information flow graph for the Transformer model at any node or layer. The research proposes using a Directed Acyclic Graph (DAG) with input tokens, or the hidden embeddings as the graph nodes and raw attention weights as the edges.

### 7.5.2 Attention Rollout

Once the DAG has been constructed from the Transformer model, the attention rollout mechanism quantifies the impact of attention to input tokens by computing the proportion of the information that can propagate through each link recursively to all of the input tokens. The attention rollout mechanism for a given layer *i* and all the attention weights in the previous layers computes attention to input tokens by recursively multiplying the attention weights matrices, starting from the input layer up to layer *i* and can be written as:

  
$$\\begin{array}{l} {\\widetilde{A}(l\_{i}) = \\left\\{ \\begin{array}{l} {A(l\_{i})\\widetilde{A}(l\_{i - 1})\\, if\\, i > j} \\\\ {A(l\_{i})\\, if\\, i = j} \\\\ \\end{array} \\right.} \\\\ \\end{array}$$  
(7.26)

[Fig. 7.5](#ch7.xhtml#fig7_5) shows attention rollout computation between an input token (source) and the output using the recursive multiplication of weights.

![Figure 7.5 Example of attention rollout mechanism between two nodes.](images/fig7_5.jpg)

[Figure 7.5](#ch7.xhtml#b7fig7_5) Example of attention rollout mechanism between two nodes.

### 7.5.3 Attention Flow

A flow network is a directed graph with a “capacity” affiliated with every edge in a graph as per the graph theory. A maximum flow algorithm finds a flow with the maximum possible value between any given source and the sink given the flow network. In this technique, when the graph network mapping to the flow network of the transformers happens, with the edges as the attention weights; the maximum flow algorithm can compute the maximum attention flow from any node of any layer to the input nodes(tokens).

[Fig. 7.6](#ch7.xhtml#fig7_6) shows attention flow computation between an input token (source) and the output using the capacity (minimum weights).

![Figure 7.6 Example of attention flow mechanism between two nodes.](images/fig7_6.jpg)

[Figure 7.6](#ch7.xhtml#b7fig7_6) Example of attention flow mechanism between two nodes.

The research shows that the two methods give complementary viewpoints, and compared to draw attention, both yield higher correlations with importance scores of input tokens using gradient-based and the ablation method.

## 7.6 Case Study: Text Classification with Explainability

### 7.6.1 Goal

In the healthcare domain, the transparency and interpretability of machine learning models are imperative for their adoption. This section will go through a use case using explainability techniques on state-of-the-art transformers to illustrate the usefulness of explainability techniques. The goal is to compare a simple traditional interpretable machine learning algorithm like logistic regression to the state-of-the-art BERT and Clinical BERT to see the performance gain and application of post-hoc techniques to explain the black-box models.

### 7.6.2 Data, Tools, and Libraries

Healthcare data usage has lots of restrictions and constraints due to HIPAA privacy regulations. However, [MTSamples.com](http://MTSamples.com) collects transcribed medical reports with sample transcription reports for forty specialties and work types to overcome these limitations and help transcriptions be more accessible. Kaggle's medical transcriptions dataset and the classification task are based on this dataset. The medical-nlp project further transforms the data into four labels or specialities (Surgery, Medical Records, Internal Medicine, and Other) using the medical taxonomy. We will use the transformed dataset and classification task for the case study.

We use pandas for basic text processing and exploratory data analysis. Sklearn library is used for traditional NLP pipeline and logistic regression model. We employ the Huggingface implementation of BERT and Bio\_ClinicalBERT as our transformer implementations. Captum library is used to perform input attribution via the saliency method. For understanding and visualizing how the BERT layers and heads work we use the exBERT visualization package.

### 7.6.3 Experiments, Results, and Analysis

#### 7.6.3.1 Exploratory data analysis

We perform some basic EDA to understand the data from distribution and corpus wise.

[Figs. 7.7](#ch7.xhtml#fig7_7) to [7.10](#ch7.xhtml#fig7_10) shows interesting outputs from word cloud, document length distribution, top words, and class distribution. The word cloud ([Fig. 7.7](#ch7.xhtml#fig7_7)) and top frequency words plot ([Fig. 7.9](#ch7.xhtml#fig7_9)) clearly show bias towards terms such as *diagnoses*, *injury*, *chronic,* etc., which form the base language for most medical transcriptions and records. The document length distribution plot ([Fig. 7.8](#ch7.xhtml#fig7_8)) shows a long-tailed distribution with greater than 25% documents falling beyond the maximum sequence length for BERT. Finally, the conversion of 40 classes to 4 categories ([Fig. 7.10](#ch7.xhtml#fig7_10)) shows almost a balanced distribution and becomes helpful in classifier comparisons as the impact of imbalance is now minimized.

#### 7.6.3.2 Experiments

We use the 90–10% split of training and testing and further create a validation set of 10% for hyperparameter and learning curves. We will first compare the base BERT with BIO\_ClinicalBERT both fine-tuned on the training data and evaluated on test data.

![Figure 7.7 Word cloud.](images/fig7_7.jpg)

[Figure 7.7](#ch7.xhtml#b7fig7_7) Word cloud.

![Figure 7.8 Document length distribution.](images/fig7_8.jpg)

[Figure 7.8](#ch7.xhtml#b7fig7_8) Document length distribution.

![Figure 7.9 Top words.](images/fig7_9.jpg)

[Figure 7.9](#ch7.xhtml#b7fig7_9) Top words.

![Figure 7.10 Class distribution.](images/fig7_10.jpg)

[Figure 7.10](#ch7.xhtml#b7fig7_10) Class distribution.

[Tables 7.1](#ch7.xhtml#tbl7_1) and [7.2](#ch7.xhtml#tbl7_2) show that the BIO\_ClinicalBERT with its pre-training on a large corpus of medical records has a slight advantage over the base BERT for classification.

 [TABLE 7.1](#ch7.xhtml#b7tbl7_1) Fine-tuned base BERT on Test Data 

 
| Class/Metrics || Precision || Recall || F1 |
| --- | --- | --- | --- |
| Surgery || 0.792 || 0.768 || 0.779 |
| --- | --- | --- | --- |
| Medical Records || 0.612 || 0.510 || 0.556 |
| Internal Medicine || 0.588 || 0.642 || 0.614 |
| Other || 0.587 || 0.670 || 0.626 |
|   |
| accuracy ||  || 0.67 |
| macro avg || 0.645 || 0.648 || 0.644 |
| weighted avg || 0.673 || 0.670 || 0.670 |

 

[TABLE 7.2](#ch7.xhtml#b7tbl7_2) Fine-tuned Bio\_Clinical BERT on Test Data

 
| Class/Metrics || Precision || Recall || F1 |
| --- | --- | --- | --- |
| Surgery || 0.796 || 0.788 || 0.792 |
| --- | --- | --- | --- |
| Medical Records || 0.605 || 0.676 || 0.639 |
| Internal Medicine || 0.690 || 0.633 || 0.660 |
| Other || 0.589 || 0.582 || 0.586 |
|   |
| accuracy ||  || 0.694 |
| macro avg || 0.670 || 0.670 || 0.669 |
| weighted avg || 0.696 || 0.694 || 0.694 |

#### 7.6.3.3 Error analysis and explainability

Next, we will try to perform error analysis using explainable techniques to get more insights. The error analysis on the 500 sized test data shows

1.  The BIO\_ClinincalBERT performs better than the base model on 51 instances.
    
2.  The BIO\_ClinincalBERT performs worse than the base model on 39 instances.
    
3.  Both models miss on 114 instances.
    
4.  Both models predict correctly on 296 instances.
    

![](images/comp7_3.jpg)![Listing 7.1 Saliency explanations](images/comp7_3a.jpg)

[Listing 7.1](#ch7.xhtml#b7list7_1) Saliency explanations

The [Listing 7.1](#ch7.xhtml#list7_1) shows the saliency-based implementation for visualization of input attributions.

In [Figs. 7.11](#ch7.xhtml#fig7_11) and [7.12](#ch7.xhtml#fig7_12), we can see the difference in explanations for each of the models on the same record—we are attributing each token for the correct class **Surgery**. The base BERT model gives an incorrect prediction for this example. At a glance, we can see that the most significant negative attributions for the base BERT model come from kidney-related terms (kidney, renal, etc.), possibly indicating that the base BERT model associates such terms with a class other than **Surgery**. The domain-adapted Bio\_Clinical BERT has positive and negative attributions for *bladder* as well as positive explanations for the descriptions of the procedures (e.g., “placed in dorsal lithotomy position” and “prepped and draped in the standard fashion”). This may give us some insight into how the additional pre-training is helping Bio\_Clinical BERT achieve a relatively better performance.

![Figure 7.11 Saliency-based visualization for a correct prediction for the base BERT.](images/fig7_12.jpg)

[Figure 7.11](#ch7.xhtml#b7fig7_11) Saliency-based visualization for a correct prediction for the base BERT.

![Figure 7.12 Saliency-based visualization for a correct prediction for the domain adapted BIO\_ClinincalBERT.](images/fig7_13.jpg)

[Figure 7.12](#ch7.xhtml#b7fig7_12) Saliency-based visualization for a correct prediction for the domain adapted BIO\_ClinincalBERT.

![Figure 7.13 Saliency-based visualization for an incorrect prediction for the base BERT.](images/fig7_14.jpg)

Figure 7.13 Saliency-based visualization for an incorrect prediction for the base BERT.

In the example as shown in [Figs. 7.14](#ch7.xhtml#fig7_14) and [7.12](#ch7.xhtml#fig7_12), we can see that the BIO\_ClinicalBERT correctly predicts **Medical Records** while the base BERT predicts **Internal Medicine**. Highlights on context words such as “past medical history”, “present”, “admitted”, etc. in the BIO\_ClinicalBERT saliency visualization further highlights reasons why *Medical Records* is the predicted class for the BIO\_ClinicalBERT.

![Figure 7.14 Saliency-based visualization for an incorrect prediction for the domain adapted BIO\_ClinincalBERT.](images/fig7_15.jpg)

[Figure 7.14](#ch7.xhtml#b7fig7_14) Saliency-based visualization for an incorrect prediction for the domain adapted BIO\_ClinincalBERT.

![Figure 7.15 Sample example visualized at a layer by two different architectures: (a) BERT and (b) BIO\_ClinicalBERT.](images/fig7_16.jpg)

[Figure 7.15](#ch7.xhtml#b7fig7_15) Sample example visualized at a layer by two different architectures: (a) BERT and (b) BIO\_ClinicalBERT.

We can also visualize the self-attention weights to gain another view into the representations learned by the BERT models. The BertViz library provides an interactive front-end to explore these token weights. Unfortunately, BertViz does not scale well to long sequences, so we truncated the inputs to illustrate local attention effects for BERT and BIO\_ClinicalBERT to highlight the relationship between the token weights and class token at a layer. These are shown in [Fig. 7.15](#ch7.xhtml#fig7_15).

# Bibliography

1.  [\[1\]](#ch7.xhtml#refbib_1b) S. ABNAR AND W. ZUIDEMA, *Quantifying attention flow in transformers*, arXiv preprint arXiv:2005.00928, (2020).
2.  [\[2\]](#ch7.xhtml#refbib_2b) G. ALAIN AND Y. BENGIO, *Understanding intermediate layers using linear classifier probes*, arXiv preprint arXiv:1610.01644, (2016).
3.  [\[3\]](#ch7.xhtml#refbib_3b) D. ALVAREZ\-MELIS AND T. S. JAAKKOLA, *Towards robust interpretability with self-explaining neural networks*, arXiv preprint arXiv:1806.07538, (2018).
4.  [\[4\]](#ch7.xhtml#refbib_4b) S. AMERSHI, M. CHICKERING, S. M. DRUCKER, B. LEE, P. SIMARD, AND J. SUH, *Modeltracker: Redesigning performance analysis tools for machine learning*, in Proceedings of the 33rd Annual ACM Conference on Human Factors in Computing Systems, 2015, pp. 337–346.
5.  [\[5\]](#ch7.xhtml#refbib_5b) D. AMODEI, C. OLAH, J. STEINHARDT, P. CHRISTIANO, J. SCHULMAN, AND D. Mané, *Concrete problems in ai safety*, arXiv preprint arXiv:1606.06565, (2016).
6.  [\[6\]](#ch5.xhtml#refbib_6b) A. ANDONI, P. INDYK, T. LAARHOVEN, I. P. RAZENSHTEYN, AND L. SCHMIDT, *Practical and optimal lsh for angular distance*, in NIPS, 2015.
7.  [\[7\]](#ch6.xhtml#refbib_7b) D. ARACI, *Finbert: Financial sentiment analysis with pre-trained language models*, ArXiv, abs/1908.10063 (2019).
8.  [\[8\]](#ch7.xhtml#refbib_8b) E. ARKHANGELSKAIA AND S. DUTTA, *Whatcha lookin'at? deeplifting bert's attention in question answering*, arXiv preprint arXiv:1910.06431, (2019).
9.  [\[9\]](#ch4.xhtml#refbib_9b) M. ARTETXE, S. RUDER, AND D. YOGATAMA, *On the cross-lingual transferability of monolingual representations*, in Proceedings of the 58th Annual Meeting of the Association for Computational Linguistics, Online, July 2020, Association for Computational Linguistics, pp. 4623–4637.
10.  [\[10\]](#ch4.xhtml#refbib_10b) M. ARTETXE, S. RUDER, AND D. YOGATAMA, *On the cross-lingual transferability of monolingual representations*, in Proceedings of the 58th Annual Meeting of the Association for Computational Linguistics, ACL 2020, Online, July 5-10, 2020, D. Jurafsky, J. Chai, N. Schluter, and J. R. Tetreault, eds., Association for Computational Linguistics, 2020, pp. 4623–4637.
11.  [\[11\]](#ch4.xhtml#refbib_11b) M. ARTETXE AND H. SCHWENK, *Massively multilingual sentence embeddings for zero-shot cross-lingual transfer and beyond*, Trans. Assoc. Comput. Linguistics, 7 (2019), pp. 597–610.
12.  [\[12\]](#ch1.xhtml#refbib_12b) P. AZUNRE, Transfer Learning for Natural Language Processing, Manning, 2021.
13.  [\[13\]](#ch1.xhtml#refbib_13b) L. J. BA, J. R. KIROS, AND G. E. HINTON, *Layer normalization*, CoRR, abs/1607.06450 (2016).
14.  [\[14\]](#ch7.xhtml#refbib_14b) S. BACH, A. BINDER, G. MONTAVON, F. KLAUSCHEN, K.-R. MÜLLER, AND W. SAMEK, *On pixel-wise explanations for non-linear classifier decisions by layer-wise relevance propagation*, PloS one, 10 (2015), p. e0130140.
15.  [\[15\]](#ch7.xhtml#refbib_15b) D. BAEHRENS, T. SCHROETER, S. HARMELING, M. KAWANABE, K. HANSEN, AND K.-R. MÜLLER, *How to explain individual classification decisions*, The Journal of Machine Learning Research, 11 (2010), pp. 1803–1831.
16.  [\[16\]](#ch4.xhtml#refbib_16b) A. BAEVSKI, H. ZHOU, A. RAHMAN MOHAMED, AND M. AULI, *wav2vec 2.0: A framework for self-supervised learning of speech representations*, ArXiv, abs/2006.11477 (2020).
17.  [\[17\]](#ch1.xhtml#refbib_17b) D. BAHDANAU, K. CHO, AND Y. BENGIO, *Neural machine translation by jointly learning to align and translate*, CoRR, abs/1409.0473 (2014).
18.  [\[18\]](#ch1.xhtml#refbib_18b) A. BAPNA, N. ARIVAZHAGAN, AND O. FIRAT, *Controlling computation versus quality for neural sequence models*, ArXiv, abs/2002.07106 (2020).
19.  [\[19\]](#ch1.xhtml#refbib_19b) A. BAPNA, M. CHEN, O. FIRAT, Y. CAO, AND Y. WU, *Training deeper neural machine translation models with transparent attention*, in EMNLP, 2018.
20.  [\[20\]](#ch7.xhtml#refbib_20b) S. BAROCAS AND D. BOYD, *Engaging the ethics of data science in practice*, Communications of the ACM, 60 (2017), pp. 23–25.
21.  [\[21\]](#ch7.xhtml#refbib_21b) O. BASTANI, C. KIM, AND H. BASTANI, *Interpreting blackbox models via model extraction*, arXiv preprint arXiv:1705.08504, (2017).
22.  [\[22\]](#ch7.xhtml#refbib_22b) K. BAUM, M. A. KÖHL, AND E. SCHMIDT, *Two challenges for ci trustworthiness and how to address them*, in Proceedings of the 1st Workshop on Explainable Computational Intelligence (XCI 2017), 2017.
23.  [\[23\]](#ch7.xhtml#refbib_23b) Y. BELINKOV, *Probing classifiers: Promises, shortcomings, and alternatives*, arXiv preprint arXiv:2102.12452, (2021).
24.  [\[24\]](#ch6.xhtml#refbib_24b) I. BELTAGY, K. LO, AND A. COHAN, *Scibert: A pretrained language model for scientific text*, in EMNLP, 2019.
25.  [\[25\]](#ch1.xhtml#refbib_25b) I. BELTAGY, M. E. PETERS, AND A. COHAN, *Longformer: The long-document transformer*, ArXiv, abs/2004.05150 (2020).
26.  [\[26\]](#ch7.xhtml#refbib_26b) E. M. BENDER, D. HOVY, AND A. SCHOFIELD, *Integrating ethics into the nlp curriculum*, in Proceedings of the 58th Annual Meeting of the Association for Computational Linguistics: Tutorial Abstracts, 2020, pp. 6–9.
27.  [\[27\]](#ch1.xhtml#refbib_27b) Y. BENGIO, P. LAMBLIN, D. POPOVICI, AND H. LAROCHELLE, *Greedy layer-wise training of deep networks*, in Proceedings of the 19th International Conference on Neural Information Processing Systems, NIPS'06, MIT Press, 2006, pp. 153–160.
28.  [\[28\]](#ch1.xhtml#refbib_28b) Y. BENGIO AND Y. LECUN, Scaling learning algorithms towards AI, MIT Press, 2007.
29.  [\[29\]](#ch5.xhtml#refbib_29b) G. BERTASIUS, H. WANG, AND L. TORRESANI, *Is space-time attention all you need for video understanding?*, in ICML, 2021.
30.  [\[30\]](#ch7.xhtml#refbib_30b) A. BEUTEL, J. CHEN, Z. ZHAO, AND E. H. CHI, *Data decisions and theoretical implications when adversarially learning fair representations*, arXiv preprint arXiv:1707.00075, (2017).
31.  [\[31\]](#ch4.xhtml#refbib_31b) S. R. BOWMAN, L. VILNIS, O. VINYALS, A. DAI, R. JOZEFOWICZ, AND S. BENGIO, *Generating sentences from a continuous space*, in Proceedings of The 20th SIGNLL Conference on Computational Natural Language Learning, Berlin, Germany, August 2016, Association for Computational Linguistics, pp. 10–21.
32.  [\[32\]](#ch1.xhtml#refbib_32b) T. B. BROWN, B. MANN, N. RYDER, M. SUBBIAH, J. KAPLAN, P. DHARIWAL, A. NEELAKANTAN, P. SHYAM, G. SASTRY, A. ASKELL, S. AGARWAL, A. HERBERT\-VOSS, G. KRUEGER, T. HENIGHAN, R. CHILD, A. RAMESH, D. M. ZIEGLER, J. WU, C. WINTER, C. HESSE, M. CHEN, E. SIGLER, M. LITWIN, S. GRAY, B. CHESS, J. CLARK, C. BERNER, S. MCCANDLISH, A. RADFORD, I. SUTSKEVER, AND D. AMODEI, *Language models are few-shot learners*, ArXiv, abs/2005.14165 (2020).
33.  [\[33\]](#ch1.xhtml#refbib_33b) J. CAGE, *Python Transformers By Huggingface Hands On: 101 practical implementation hands-on of ALBERT/ViT/BigBird and other latest models with huggingface transformers*, 2021.
34.  [\[34\]](#ch7.xhtml#refbib_34b) T. CALDERS, F. KAMIRAN, AND M. PECHENIZKIY, *Building classifiers with independency constraints*, in 2009 IEEE International Conference on Data Mining Workshops, IEEE, 2009, pp. 13–18.
35.  [\[35\]](#ch1.xhtml#refbib_35b) R. A. CALIXN, *Deep Learning Algorithms: Transformers, gans, encoders, rnns, cnns, and more*, 2020.
36.  [\[36\]](#ch7.xhtml#refbib_36b) F. P. CALMON, D. WEI, B. VINZAMURI, K. N. RAMAMURTHY, AND K. R. VARSHNEY, *Optimized pre-processing for discrimination prevention*, in Proceedings of the 31st International Conference on Neural Information Processing Systems, 2017, pp. 3995–4004.
37.  [\[37\]](#ch7.xhtml#refbib_37b) O.-M. CAMBURU, T. ROCKTäSCHEL, T. LUKASIEWICZ, AND P. BLUNSOM, *e-snli: Natural language inference with natural language explanations*, arXiv preprint arXiv:1812.01193, (2018).
38.  [\[38\]](#ch6.xhtml#refbib_38b) D. M. CER, M. T. DIAB, E. AGIRRE, I. LOPEZ\-GAZPIO, AND L. SPECIA, *Semeval-2017 task 1: Semantic textual similarity multilingual and crosslingual focused evaluation*, in [SemEval@ACL](mailto:SemEval@ACL), 2017.
39.  [\[39\]](#ch5.xhtml#refbib_39b) M. CHARIKAR, *Similarity estimation techniques from rounding algorithms*, in STOC ‘02, 2002.
40.  [\[40\]](#ch7.xhtml#refbib_40b) C. CHEN, O. LI, C. TAO, A. J. BARNETT, J. SU, AND C. RUDIN, *This looks like that: deep learning for interpretable image recognition*, arXiv preprint arXiv:1806.10574, (2018).
41.  [\[41\]](#ch6.xhtml#refbib_41b) L. CHEN, K. LU, A. RAJESWARAN, K. LEE, A. GROVER, M. LASKIN, P. ABBEEL, A. SRINIVAS, AND I. MORDATCH, *Decision transformer: Reinforcement learning via sequence modeling*, ArXiv, abs/2106.01345 (2021).
42.  [\[42\]](#ch2.xhtml#refbib_42b) S. F. CHEN, D. BEEFERMAN, AND R. ROSENFELD, *Evaluation metrics for language models*, (1998).
43.  [\[43\]](#ch6.xhtml#refbib_43b) Z. CHEN, H. ZHANG, X. ZHANG, AND L. ZHAO, *Quora question pairs*, 2017.
44.  [\[44\]](#ch4.xhtml#refbib_44b) E. A. CHI, J. HEWITT, AND C. D. MANNING, *Finding universal grammatical relations in multilingual BERT*, in Proceedings of the 58th Annual Meeting of the Association for Computational Linguistics, ACL 2020, Online, July 5–10, 2020, D. Jurafsky, J. Chai, N. Schluter, and J. R. Tetreault, eds., Association for Computational Linguistics, 2020, pp. 5564–5577.
45.  [\[45\]](#ch4.xhtml#refbib_45b) Z. CHI, L. DONG, F. WEI, X. MAO, AND H. HUANG, *Can monolingual pretrained models help cross-lingual classification?*, in Proceedings of the 1st Conference of the Asia-Pacific Chapter of the Association for Computational Linguistics and the 10th International Joint Conference on Natural Language Processing, AACL/IJCNLP 2020, Suzhou, China, December 4–7, 2020, K. Wong, K. Knight, and H. Wu, eds., Association for Computational Linguistics, 2020, pp. 12–17.
46.  [\[46\]](#ch4.xhtml#refbib_46b) Z. CHI, L. DONG, F. WEI, W. WANG, X. MAO, AND H. HUANG, *Cross-lingual natural language generation via pre-training*, in The Thirty-Fourth AAAI Conference on Artificial Intelligence, AAAI 2020, The Thirty-Second Innovative Applications of Artificial Intelligence Conference, IAAI 2020, The Tenth AAAI Symposium on Educational Advances in Artificial Intelligence, EAAI 2020, New York, NY, USA, February 7–12, 2020, AAAI Press, 2020, pp. 7570–7577.
47.  [\[47\]](#ch4.xhtml#refbib_47b) Z. CHI, L. DONG, F. WEI, N. YANG, S. SINGHAL, W. WANG, X. SONG, X. MAO, H. HUANG, AND M. ZHOU, *Infoxlm: An information-theoretic framework for cross-lingual language model pre-training*, in Proceedings of the 2021 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies, NAACL-HLT 2021, Online, June 6–11, 2021, K. Toutanova, A. Rumshisky, L. Zettlemoyer, D. Hakkani-Tür, I. Beltagy, S. Bethard, R. Cotterell, T. Chakraborty, and Y. Zhou, eds., Association for Computational Linguistics, 2021, pp. 3576–3588.
48.  [\[48\]](#ch4.xhtml#refbib_48b) Z. CHI, L. DONG, F. WEI, N. YANG, S. SINGHAL, W. WANG, X. SONG, X.-L. MAO, H. HUANG, AND M. ZHOU, *InfoXLM: An information-theoretic framework for cross-lingual language model pre-training*, in Proceedings of the 2021 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies, Online, June 2021, Association for Computational Linguistics, pp. 3576–3588.
49.  [\[49\]](#ch4.xhtml#refbib_49b) M. CHIDAMBARAM, Y. YANG, D. M. CER, S. YUAN, Y.-H. SUNG, B. STROPE, AND R. KURZWEIL, *Learning cross-lingual sentence representations via a multi-task dual-encoder model*, in [RepL4NLP@ACL](mailto:RepL4NLP@ACL), 2019.
50.  [\[50\]](#ch6.xhtml#refbib_50b) R. CHILD, S. GRAY, A. RADFORD, AND I. SUTSKEVER, *Generating long sequences with sparse transformers*, ArXiv, abs/1904.10509 (2019).
51.  [\[51\]](#ch2.xhtml#refbib_51b) K. CHO, B. van MERRIËNBOER, C. GULCEHRE, D. BAHDANAU, F. BOUGARES, H. SCHWENK, AND Y. BENGIO, *Learning phrase representations using RNN encoder–decoder for statistical machine translation*, in Proceedings of the 2014 Conference on Empirical Methods in Natural Language Processing (EMNLP), Doha, Qatar, October 2014, Association for Computational Linguistics, pp. 1724–1734.
52.  [\[52\]](#ch4.xhtml#refbib_52b) R. CHOENNI AND E. SHUTOVA, *What does it mean to be language-agnostic? probing multilingual sentence encoders for typological properties*, arXiv preprint arXiv:2009.12862, (2020).
53.  [\[53\]](#ch1.xhtml#refbib_53b) K. CHOROMANSKI, V. LIKHOSHERSTOV, D. DOHAN, X. SONG, A. GANE, T. Sarlós, P. HAWKINS, J. DAVIS, A. MOHIUDDIN, L. KAISER, D. BELANGER, L. J. COLWELL, AND A. WELLER, *Rethinking attention with performers*, ArXiv, abs/2009.14794 (2021).
54.  [\[54\]](#ch4.xhtml#refbib_54b) H. W. CHUNG, T. FEVRY, H. TSAI, M. JOHNSON, AND S. RUDER, *Rethinking embedding coupling in pre-trained language models*, in International Conference on Learning Representations, 2021.
55.  [\[55\]](#ch4.xhtml#refbib_55b) H. W. CHUNG, D. GARRETTE, K. C. TAN, AND J. RIESA, *Improving multilingual models with language-clustered vocabularies*, in Proceedings of the 2020 Conference on Empirical Methods in Natural Language Processing, EMNLP 2020, Online, November 16–20, 2020, B. Webber, T. Cohn, Y. He, and Y. Liu, eds., Association for Computational Linguistics, 2020, pp. 4536–4546.
56.  [\[56\]](#ch4.xhtml#refbib_56b) J. H. CLARK, E. CHOI, M. COLLINS, D. GARRETTE, T. KWIATKOWSKI, V. NIKOLAEV, AND J. PALOMAKI, *Tydi qa: A benchmark for information-seeking question answering in typologically diverse languages*, Transactions of the Association for Computational Linguistics, (2020).
57.  [\[57\]](#ch5.xhtml#refbib_57b) K. CLARK, U. KHANDELWAL, O. LEVY, AND C. D. MANNING, *What does bert look at? an analysis of bert's attention*, ArXiv, abs/1906.04341 (2019).
58.  [\[58\]](#ch5.xhtml#refbib_58b) K. CLARK, M.-T. LUONG, Q. V. LE, AND C. D. MANNING, *Electra: Pre-training text encoders as discriminators rather than generators*, ArXiv, abs/2003.10555 (2020).
59.  [\[59\]](#ch7.xhtml#refbib_59b) M. COECKELBERGH, AI ethics, MIT Press, 2020.
60.  [\[60\]](#ch1.xhtml#refbib_60b) R. COLLOBERT AND J. WESTON, *A unified architecture for natural language processing: Deep neural networks with multitask learning*, in Proceedings of the 25th International Conference on Machine Learning, ACM, 2008, pp. 160–167.
61.  [\[61\]](#ch4.xhtml#refbib_61b) A. CONNEAU, K. KHANDELWAL, N. GOYAL, V. CHAUDHARY, G. WENZEK, F. GUZMÁN, E. GRAVE, M. OTT, L. ZETTLEMOYER, AND V. STOYANOV, *Unsupervised cross-lingual representation learning at scale*, in Proceedings of the 58th Annual Meeting of the Association for Computational Linguistics, ACL 2020, Online, July 5–10, 2020, D. Jurafsky, J. Chai, N. Schluter, and J.R. Tetreault, eds., Association for Computational Linguistics, 2020, pp. 8440–8451.
62.  [\[62\]](#ch7.xhtml#refbib_62b) A. CONNEAU, G. KRUSZEWSKI, G. LAMPLE, L. BARRAULT, AND M. BARONI, *What you can cram into a single vector: Probing sentence embeddings for linguistic properties*, arXiv preprint arXiv:1805.01070, (2018).
63.  [\[63\]](#ch4.xhtml#refbib_63b) A. CONNEAU AND G. LAMPLE, *Cross-lingual language model pretraining*, in Advances in Neural Information Processing Systems 32: Annual Conference on Neural Information Processing Systems 2019, NeurIPS 2019, 8–14 December 2019, Vancouver, BC, Canada, H. M. Wallach, H. Larochelle, A. Beygelzimer, F. d'Alché-Buc, E. B. Fox, and R. Garnett, eds., 2019, pp. 7057–7067.
64.  [\[64\]](#ch4.xhtml#refbib_64b) A. CONNEAU, R. RINOTT, G. LAMPLE, A. WILLIAMS, S. R. BOWMAN, H. SCHWENK, AND V. STOYANOV, *Xnli: Evaluating cross-lingual sentence representations*, in Proceedings of the 2018 Conference on Empirical Methods in Natural Language Processing, Association for Computational Linguistics, 2018.
65.  [\[65\]](#ch1.xhtml#refbib_65b) J.-B. CORDONNIER, A. LOUKAS, AND M. JAGGI, *Multi-head attention: Collaborate instead of concatenate*, ArXiv, abs/2006.16362 (2020).
66.  [\[66\]](#ch1.xhtml#refbib_66b) Z. DAI, G. LAI, Y. YANG, AND Q. V. LE, *Funnel-transformer: Filtering out sequential redundancy for efficient language processing*, ArXiv, abs/2006.03236 (2020).
67.  [\[67\]](#ch1.xhtml#refbib_67b) Z. DAI, Z. YANG, Y. YANG, J. CARBONELL, Q. V. LE, AND R. SALAKHUTDINOV, *Transformer-xl: Attentive language models beyond a fixed-length context*, in ACL, 2019.
68.  [\[68\]](#ch4.xhtml#refbib_68b) W. DE VRIES, A. VAN CRANENBURGH, AND M. NISSIM, *What's so special about bert's layers? A closer look at the NLP pipeline in monolingual and multilingual models*, in Proceedings of the 2020 Conference on Empirical Methods in Natural Language Processing: Findings, EMNLP 2020, Online Event, 16–20 November 2020, T. Cohn, Y. He, and Y. Liu, eds., vol. EMNLP 2020 of Findings of ACL, Association for Computational Linguistics, 2020, pp. 4339–4350.
69.  [\[69\]](#ch1.xhtml#refbib_69b) M. DEHGHANI, S. GOUWS, O. VINYALS, J. USZKOREIT, AND L. KAISER, *Universal transformers*, ArXiv, abs/1807.03819 (2019).
70.  [\[70\]](#ch1.xhtml#refbib_70b) J. DENG, W. DONG, R. SOCHER, L.-J. LI, K. LI, AND L. FEI\-FEI, *ImageNet: A Large-Scale Hierarchical Image Database*, in CVPR09, 2009.
71.  [\[71\]](#ch1.xhtml#refbib_71b) J. DEVLIN, M.-W. CHANG, K. LEE, AND K. TOUTANOVA, *Bert: Pre-training of deep bidirectional transformers for language understanding*, in NAACL-HLT, 2019.
72.  [\[72\]](#ch3.xhtml#refbib_72b) J. DEVLIN, M.-W. CHANG, K. LEE, AND K. TOUTANOVA, *BERT: Pre-training of deep bidirectional transformers for language understanding*, in Proceedings of the 2019 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies, Volume 1 (Long and Short Papers), Minneapolis, Minnesota, June 2019, Association for Computational Linguistics, pp. 4171–4186.
73.  [\[73\]](#ch7.xhtml#refbib_73b) Y. DING, Y. LIU, H. LUAN, AND M. SUN, *Visualizing and understanding neural machine translation*, in Proceedings of the 55th Annual Meeting of the Association for Computational Linguistics (Volume 1: Long Papers), 2017, pp. 1150–1159.
74.  [\[74\]](#ch4.xhtml#refbib_74b) S. DODDAPANENI, G. RAMESH, A. KUNCHUKUTTAN, P. KUMAR, AND M. M. KHAPRA, *A primer on pretrained multilingual language models*, CoRR, abs/2107.00676 (2021).
75.  [\[75\]](#ch6.xhtml#refbib_75b) W. B. DOLAN AND C. BROCKETT, *Automatically constructing a corpus of sentential paraphrases*, in IJCNLP, 2005.
76.  [\[76\]](#ch7.xhtml#refbib_76b) Y. DONG, F. LIAO, T. PANG, H. SU, J. ZHU, X. HU, AND J. LI, *Boosting adversarial attacks with momentum*, in Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, 2018, pp. 9185–9193.
77.  [\[77\]](#ch7.xhtml#refbib_77b) Y. DONG, H. SU, J. ZHU, AND B. ZHANG, *Improving interpretability of deep neural networks with semantic information*, in Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, 2017, pp. 4306–4314.
78.  [\[78\]](#ch5.xhtml#refbib_78b) A. DOSOVITSKIY, L. BEYER, A. KOLESNIKOV, D. WEISSENBORN, X. ZHAI, T. UNTERTHINER, M. DEHGHANI, M. MINDERER, G. HEIGOLD, S. GELLY, J. USZKOREIT, AND N. HOULSBY, *An image is worth 16x16 words: Transformers for image recognition at scale*, ArXiv, abs/2010.11929 (2021).
79.  [\[79\]](#ch4.xhtml#refbib_79b) P. DUFTER AND H. SCHÜTZE, *Identifying elements essential for BERT's multilinguality*, in Proceedings of the 2020 Conference on Empirical Methods in Natural Language Processing (EMNLP), Online, November 2020, Association for Computational Linguistics, pp. 4423–4437.
80.  [\[80\]](#ch6.xhtml#refbib_80b) V. P. DWIVEDI AND X. BRESSON, *A generalization of transformer networks to graphs*, ArXiv, abs/2012.09699 (2020).
81.  [\[81\]](#ch6.xhtml#refbib_81b) V. P. DWIVEDI, C. K. JOSHI, T. LAURENT, Y. BENGIO, AND X. BRESSON, *Benchmarking graph neural networks*, ArXiv, abs/2003.00982 (2020).
82.  [\[82\]](#ch7.xhtml#refbib_82b) C. DWORK, N. IMMORLICA, A. T. KALAI, AND M. LEISERSON, *Decoupled classifiers for group-fair and efficient machine learning*, in Conference on Fairness, Accountability and Transparency, PMLR, 2018, pp. 119–133.
83.  [\[83\]](#ch5.xhtml#refbib_83b) C. ECKART AND G. M. YOUNG, *The approximation of one matrix by another of lower rank*, Psychometrika, 1 (1936), pp. 211–218.
84.  [\[84\]](#ch5.xhtml#refbib_84b) P. ERDÖS, On random graphs, *i*, 1959.
85.  [\[85\]](#ch7.xhtml#refbib_85b) D. ERHAN, Y. BENGIO, A. COURVILLE, AND P. VINCENT, Visualizing higher-layer features of a deep network, University of Montreal, 1341 (2009), p. 1.
86.  [\[86\]](#ch7.xhtml#refbib_86b) K. EYKHOLT, I. EVTIMOV, E. FERNANDES, B. LI, A. RAHMATI, C. XIAO, A. PRAKASH, T. KOHNO, AND D. SONG, *Robust physical-world attacks on deep learning visual classification*, in Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, 2018, pp. 1625–1634.
87.  [\[87\]](#ch5.xhtml#refbib_87b) W. FEDUS, B. ZOPH, AND N. SHAZEER, *Switch transformers: Scaling to trillion parameter models with simple and efficient sparsity*, arXiv preprint arXiv:2101.03961, (2021).
88.  [\[88\]](#ch4.xhtml#refbib_88b) F. FENG, Y. YANG, D. CER, N. ARIVAZHAGAN, AND W. WANG, *Language-agnostic BERT sentence embedding*, CoRR, abs/2007.01852 (2020).
89.  [\[89\]](#ch7.xhtml#refbib_89b) R. C. FONG AND A. VEDALDI, *Interpretable explanations of black boxes by meaningful perturbation*, in Proceedings of the IEEE International Conference on Computer Vision, 2017, pp. 3429–3437.
90.  [\[90\]](#ch7.xhtml#refbib_90b) F. B. FUCHS, O. GROTH, A. R. KOSIOREK, A. BEWLEY, M. WULFMEIER, A. VEDALDI, AND I. POSNER, *Neural stethoscopes: Unifying analytic, auxiliary and adversarial network probing.*, (2018).
91.  [\[91\]](#ch1.xhtml#refbib_91b) K. FUKUSHIMA, *Neural network model for a mechanism of pattern recognition unaffected by shift in position—Neocognitron*, Trans. IECE, J62-A(10) (1979), pp. 658–665.
92.  [\[92\]](#ch6.xhtml#refbib_92b) P. GAGE, *A new algorithm for data compression*, The C Users Journal archive, 12 (1994), pp. 23–38.
93.  [\[93\]](#ch6.xhtml#refbib_93b) E. A. GAROFOLO, JOHN S., *Timit acoustic-phonetic continuous speech corpus*, 1993.
94.  [\[94\]](#ch5.xhtml#refbib_94b) A. N. GOMEZ, M. REN, R. URTASUN, AND R. B. GROSSE, *The reversible residual network: Backpropagation without storing activations*, in NIPS, 2017.
95.  [\[95\]](#ch7.xhtml#refbib_95b) I. J. GOODFELLOW, J. SHLENS, AND C. SZEGEDY, *Explaining and harnessing adversarial examples*, arXiv preprint arXiv:1412.6572, (2014).
96.  [\[96\]](#ch7.xhtml#refbib_96b) P. GORDALIZA, E. DEL BARRIO, G. FABRICE, AND J.-M. LOUBES, *Obtaining fairness using optimal transport theory*, in International Conference on Machine Learning, PMLR, 2019, pp. 2357–2365.
97.  [\[97\]](#ch1.xhtml#refbib_97b) A. GRAVES, *Generating sequences with recurrent neural networks.*, CoRR, abs/1308.0850 (2013).
98.  [\[98\]](#ch5.xhtml#refbib_98b) A. GRAVES, G. WAYNE, AND I. DANIHELKA, *Neural turing machines*, CoRR, abs/1410.5401(2014).
99.  [\[99\]](#ch6.xhtml#refbib_99b) R. M. GRAY AND D. L. NEUHOFF, *Quantization*, IEEE Trans. Inf. Theory, 44 (1998), pp. 2325–2383.
100.  [\[100\]](#ch5.xhtml#refbib_100b) S. GRAY, A. RADFORD, AND D. P. KINGMA, *GPU kernels for block-sparse weights*, 2017.
101.  [\[101\]](#ch3.xhtml#refbib_101b) M. GROOTENDORST, *Bertopic: Leveraging bert and c-tf-idf to create easily interpretable topics.*, 2020.
102.  [\[102\]](#ch1.xhtml#refbib_102b) M. GUO, Y. ZHANG, AND T. LIU, *Gaussian transformer: A lightweight approach for natural language inference*, in AAAI, 2019.
103.  [\[103\]](#ch1.xhtml#refbib_103b) Q. GUO, X. QIU, P. LIU, X. XUE, AND Z. ZHANG, *Multi-scale self-attention for text classification*, in AAAI, 2020.
104.  [\[104\]](#ch4.xhtml#refbib_104b) K. HE, H. FAN, Y. WU, S. XIE, AND R. GIRSHICK, *Momentum contrast for unsupervised visual representation learning*, 2020.
105.  [\[105\]](#ch2.xhtml#refbib_105b) K. HE, X. ZHANG, S. REN, AND J. SUN, *Deep residual learning for image recognition*, 2016 IEEE Conference on Computer Vision and Pattern Recognition (CVPR), (2016), pp. 770–778.
106.  [\[106\]](#ch7.xhtml#refbib_106b) R. HE, W. S. LEE, H. T. NG, AND D. DAHLMEIER, *Effective attention modeling for aspect-level sentiment classification*, in Proceedings of the 27th International Conference on Computational Linguistics, 2018, pp. 1121–1131.
107.  [\[107\]](#ch1.xhtml#refbib_107b) R. HE, A. RAVULA, B. KANAGAL, AND J. AINSLIE, *Realformer: Transformer likes residual attention*, in FINDINGS, 2021.
108.  [\[108\]](#ch1.xhtml#refbib_108b) D. O. HEBB, The organization of behavior: A neuropsychological theory, Wiley, 1949.
109.  [\[109\]](#ch7.xhtml#refbib_109b) L. A. HENDRICKS, Z. AKATA, M. ROHRBACH, J. DONAHUE, B. SCHIELE, AND T. DARRELL, *Generating visual explanations*, in European conference on computer vision, Springer, 2016, pp. 3–19.
110.  [\[110\]](#ch7.xhtml#refbib_110b) J. HEWITT AND P. LIANG, *Designing and interpreting probes with control tasks*, arXiv preprint arXiv:1909.03368, (2019).
111.  [\[111\]](#ch7.xhtml#refbib_111b) M. HIND, D. WEI, M. CAMPBELL, N. C. CODELLA, A. DHURANDHAR, A. MOJSILOVIĆ, K. NATESAN RAMAMURTHY, AND K. R. VARSHNEY, *Ted: Teaching ai to explain its decisions*, in Proceedings of the 2019 AAAI/ACM Conference on AI, Ethics, and Society, 2019, pp. 123–129.
112.  [\[112\]](#ch7.xhtml#refbib_112b) G. HINTON, O. VINYALS, AND J. DEAN, *Distilling the knowledge in a neural network*, arXiv preprint arXiv:1503.02531, (2015).
113.  [\[113\]](#ch1.xhtml#refbib_113b) G. E. HINTON, S. OSINDERO, AND Y.-W. TEH, *A fast learning algorithm for deep belief nets*, Neural Comput., 18 (2006), pp. 1527–1554.
114.  [\[114\]](#ch6.xhtml#refbib_114b) J. HO, N. KALCHBRENNER, D. WEISSENBORN, AND T. SALIMANS, *Axial attention in multidimensional transformers*, ArXiv, abs/1912.12180 (2019).
115.  [\[115\]](#ch1.xhtml#refbib_115b) S. HOCHREITER, *The vanishing gradient problem during learning recurrent neural nets and problem solutions*, International Journal of Uncertainty, Fuzziness and Knowledge-Based Systems, 6 (1998), pp. 107–116.
116.  [\[116\]](#ch1.xhtml#refbib_116b) S. HOCHREITER AND J. SCHMIDHUBER, *Long short-term memory*, Neural Comput., 9 (1997), pp. 1735–1780.
117.  [\[117\]](#ch1.xhtml#refbib_117b) J. J. HOPFIELD, *Neural networks and physical systems with emergent collective computational abilities*, Proceedings of the National Academy of Sciences of the United States of America, 79 (1982), pp. 2554–2558.
118.  [\[118\]](#ch7.xhtml#refbib_118b) B.-J. HOU AND Z.-H. ZHOU, *Learning with interpretable structure from rnn*, arXiv preprint arXiv:1810.10708, (2018).
119.  [\[119\]](#ch6.xhtml#refbib_119b) J. HOWARD AND S. RUDER, *Universal language model fine-tuning for text classification*, in ACL, 2018.
120.  [\[120\]](#ch6.xhtml#refbib_120b) W.-N. HSU, B. BOLTE, Y.-H. H. TSAI, K. LAKHOTIA, R. SALAKHUTDINOV, AND A. MOHAMED, *Hubert: Self-supervised speech representation learning by masked prediction of hidden units*, ArXiv, abs/2106.07447 (2021).
121.  [\[121\]](#ch4.xhtml#refbib_121b) J. HU, M. JOHNSON, O. FIRAT, A. SIDDHANT, AND G. NEUBIG, *Explicit alignment objectives for multilingual bidirectional encoders*, 2021.
122.  [\[122\]](#ch4.xhtml#refbib_122b) J. HU, S. RUDER, A. SIDDHANT, G. NEUBIG, O. FIRAT, AND M. JOHNSON, *XTREME: A massively multilingual multi-task benchmark for evaluating cross-lingual generalisation*, in Proceedings of the 37th International Conference on Machine Learning, ICML 2020, 13–18 July 2020, Virtual Event, vol. 119 of Proceedings of Machine Learning Research, PMLR, 2020, pp. 4411–4421.
123.  [\[123\]](#ch6.xhtml#refbib_123b) R. HU AND A. SINGH, *Transformer is all you need: Multimodal multitask learning with a unified transformer*, ArXiv, abs/2102.10772 (2021).
124.  [\[124\]](#ch5.xhtml#refbib_124b) C.-Z. A. HUANG, A. VASWANI, J. USZKOREIT, N. M. SHAZEER, C. HAWTHORNE, A. M. DAI, M. HOFFMAN, AND D. ECK, *An improved relative self-attention mechanism for transformer with application to music generation*, ArXiv, abs/1809.04281 (2018).
125.  [\[125\]](#ch4.xhtml#refbib_125b) H. HUANG, Y. LIANG, N. DUAN, M. GONG, L. SHOU, D. JIANG, AND M. ZHOU, *Unicoder: A universal language encoder by pre-training with multiple cross-lingual tasks*, in Proceedings of the 2019 Conference on Empirical Methods in Natural Language Processing and the 9th International Joint Conference on Natural Language Processing, EMNLP-IJCNLP 2019, Hong Kong, China, November 3–7, 2019, K. Inui, J. Jiang, V. Ng, and X. Wan, eds., Association for Computational Linguistics, 2019, pp. 2485–2494.
126.  [\[126\]](#ch6.xhtml#refbib_126b) Z. HUANG, X. WANG, L. HUANG, C. HUANG, Y. WEI, H. SHI, AND W. LIU, *Ccnet: Criss-cross attention for semantic segmentation*, 2019 IEEE/CVF International Conference on Computer Vision (ICCV), (2019), pp. 603–612.
127.  [\[127\]](#ch7.xhtml#refbib_127b) D. A. HUDSON AND C. D. MANNING, *Compositional attention networks for machine reasoning*, arXiv preprint arXiv:1803.03067, (2018).
128.  [\[128\]](#ch7.xhtml#refbib_128b) D. HUPKES, S. VELDHOEN, AND W. ZUIDEMA, *Visualisation and ‘diagnostic classifiers’ reveal how recurrent and recursive neural networks process hierarchical structure*, Journal of Artificial Intelligence Research, 61 (2018), pp. 907–926.
129.  [\[129\]](#ch5.xhtml#refbib_129b) P. INDYK AND R. MOTWANI, *Approximate nearest neighbors: towards removing the curse of dimensionality*, in STOC ‘98, 1998.
130.  [\[130\]](#ch2.xhtml#refbib_130b) S. IOFFE AND C. SZEGEDY, *Batch normalization: Accelerating deep network training by reducing internal covariate shift.*, CoRR, abs/1502.03167 (2015).
131.  [\[131\]](#ch7.xhtml#refbib_131b) R. IYER, Y. LI, H. LI, M. LEWIS, R. SUNDAR, AND K. SYCARA, *Transparency and explanation in deep reinforcement learning neural networks*, in Proceedings of the 2018 AAAI/ACM Conference on AI, Ethics, and Society, 2018, pp. 144–150.
132.  [\[132\]](#ch7.xhtml#refbib_132b) S. JAIN AND B. C. WALLACE, *Attention is not explanation*, arXiv preprint arXiv:1902.10186, (2019).
133.  [\[133\]](#ch2.xhtml#refbib_133b) W. JAMES AND F. H. BURKHARDT, *The principles of psychology, the works of William James*, Transactions of the Charles S. Peirce Society, 19 (1983).
134.  [\[134\]](#ch7.xhtml#refbib_134b) H. JIANG, B. KIM, M. Y. GUAN, AND M. R. GUPTA, *To trust or not to trust a classifier*., in NeurIPS, 2018, pp. 5546–5557.
135.  [\[135\]](#ch4.xhtml#refbib_135b) K. K, Z. WANG, S. MAYHEW, AND D. ROTH, *Cross-lingual ability of multilingual BERT: an empirical study*, in 8th International Conference on Learning Representations, ICLR 2020, Addis Ababa, Ethiopia, April 26–30, 2020, [OpenReview.net](http://OpenReview.net), 2020.
136.  [\[136\]](#ch5.xhtml#refbib_136b) L. KAISER AND I. SUTSKEVER, *Neural GPUs learn algorithms*, arXiv: Learning, (2016).
137.  [\[137\]](#ch4.xhtml#refbib_137b) D. KAKWANI, A. KUNCHUKUTTAN, S. GOLLA, G. N.C., A. BHATTACHARYYA, M. M. KHAPRA, AND P. KUMAR, *IndicNLPSuite: Monolingual Corpora, Evaluation Benchmarks and Pre-trained Multilingual Language Models for Indian Languages*, in Findings of EMNLP, 2020.
138.  [\[138\]](#ch4.xhtml#refbib_138b) K. S. KALYAN, A. RAJASEKHARAN, AND S. SANGEETHA, *AMMUS: A survey of transformer-based pretrained models in natural language processing*, CoRR, abs/2108.05542 (2021).
139.  [\[139\]](#ch7.xhtml#refbib_139b) F. KAMIRAN AND T. CALDERS, *Data preprocessing techniques for classification without discrimination*, Knowledge and Information Systems, 33 (2012), pp. 1–33.
140.  [\[140\]](#ch7.xhtml#refbib_140b) D. KANG, D. RAGHAVAN, P. BAILIS, AND M. ZAHARIA, *Model assertions for debugging machine learning*, in NeurIPS MLSys Workshop, 2018.
141.  [\[141\]](#ch4.xhtml#refbib_141b) S. KHANUJA, D. BANSAL, S. MEHTANI, S. KHOSLA, A. DEY, B. GOPALAN, D. K. MARGAM, P. AGGARWAL, R. T. NAGIPOGU, S. DAVE, S. GUPTA, S. C. B. GALI, V. SUBRAMANIAN, AND P. TALUKDAR, *Muril: Multilingual representations for Indian languages*, 2021.
142.  [\[142\]](#ch1.xhtml#refbib_142b) N. KITAEV, L. KAISER, AND A. LEVSKAYA, *Reformer: The efficient transformer*, ArXiv, abs/2001.04451 (2020).
143.  [\[143\]](#ch5.xhtml#refbib_143b) G. KOBAYASHI, T. KURIBAYASHI, S. YOKOI, AND K. INUI, *Attention is not only a weight: Analyzing transformers with vector norms*, in EMNLP, 2020.
144.  [\[144\]](#ch4.xhtml#refbib_144b) T. KUDO AND J. RICHARDSON, *SentencePiece: A simple and language independent subword tokenizer and detokenizer for neural text processing*, in Proceedings of the 2018 Conference on Empirical Methods in Natural Language Processing: System Demonstrations, Brussels, Belgium, November 2018, Association for Computational Linguistics, pp. 66–71.
145.  [\[145\]](#ch6.xhtml#refbib_145b) G. LAI, Q. XIE, H. LIU, Y. YANG, AND E. H. HOVY, *Race: Large-scale reading comprehension dataset from examinations*, in EMNLP, 2017.
146.  [\[146\]](#ch4.xhtml#refbib_146b) G. LAMPLE AND A. CONNEAU, *Cross-lingual language model pretraining*, Advances in Neural Information Processing Systems (NeurIPS), (2019).
147.  [\[147\]](#ch7.xhtml#refbib_147b) S. LAPUSCHKIN, A. BINDER, G. MONTAVON, K.-R. MULLER, AND W. SAMEK, *Analyzing classifiers: Fisher vectors and deep neural networks*, in Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, 2016, pp. 2912–2920.
148.  [\[148\]](#ch4.xhtml#refbib_148b) A. LAUSCHER, V. RAVISHANKAR, I. VULIC, AND G. GLAVAS, *From zero to hero: On the limitations of zero-shot cross-lingual transfer with multilingual transformers*, CoRR, abs/2005.00633 (2020).
149.  [\[149\]](#ch1.xhtml#refbib_149b) Y. LECUN, *Une procédure d'apprentissage pour réseau a seuil asymmetrique (a learning scheme for asymmetric threshold networks**)*, in Proceedings of Cognitiva 85, 1985, pp. 599–604.
150.  [\[150\]](#ch1.xhtml#refbib_150b) Y. LECUN, B. BOSER, J. S. DENKER, D. HENDERSON, R. E. HOWARD, W. HUBBARD, AND L. D. JACKEL, *Backpropagation applied to handwritten zip code recognition*, Neural Computation, 1 (1989), pp. 541–551.
151.  [\[151\]](#ch1.xhtml#refbib_151b) J. LEE, Y. LEE, J. KIM, A. R. KOSIOREK, S. CHOI, AND Y. TEH, *Set transformer: A framework for attention-based permutation-invariant neural networks*, in ICML, 2019.
152.  [\[152\]](#ch6.xhtml#refbib_152b) J. LEE, W. YOON, S. KIM, D. KIM, S. KIM, C. H. SO, AND J. KANG, *Biobert: a pre-trained biomedical language representation model for biomedical text mining*, Bioinformatics, 36 (2020), pp. 1234–1240.
153.  [\[153\]](#ch7.xhtml#refbib_153b) T. LEI, R. BARZILAY, AND T. JAAKKOLA, *Rationalizing neural predictions*, arXiv preprint arXiv:1606.04155, (2016).
154.  [\[154\]](#ch7.xhtml#refbib_154b) G. LETARTE, F. PARADIS, P. GIGUÈRE, AND F. LAVIOLETTE, *Importance of self-attention for sentiment analysis*, in Proceedings of the 2018 EMNLP Workshop BlackboxNLP: Analyzing and Interpreting Neural Networks for NLP, 2018, pp. 267–275.
155.  [\[155\]](#ch4.xhtml#refbib_155b) M. LEWIS, Y. LIU, N. GOYAL, M. GHAZVININEJAD, A. MOHAMED, O. LEVY, V. STOYANOV, AND L. ZETTLEMOYER, *BART: Denoising sequence-to-sequence pre-training for natural language generation, translation, and comprehension*, in Proceedings of the 58th Annual Meeting of the Association for Computational Linguistics, Online, July 2020, Association for Computational Linguistics, pp. 7871–7880.
156.  [\[156\]](#ch4.xhtml#refbib_156b) P. S. H. LEWIS, B. OGUZ, R. RINOTT, S. RIEDEL, AND H. SCHWENK, *MLQA: evaluating cross-lingual extractive question answering*, in Proceedings of the 58th Annual Meeting of the Association for Computational Linguistics, ACL 2020, Online, July 5–10, 2020, D. Jurafsky, J. Chai, N. Schluter, and J.R. Tetreault, eds., Association for Computational Linguistics, 2020, pp. 7315–7330.
157.  [\[157\]](#ch7.xhtml#refbib_157b) J. LI, W. MONROE, AND D. JURAFSKY, *Understanding neural networks through representation erasure*, arXiv preprint arXiv:1612.08220, (2016).
158.  [\[158\]](#ch1.xhtml#refbib_158b) J. LI, Z. TU, B. YANG, M. R. LYU, AND T. ZHANG, *Multi-head attention with disagreement regularization*, ArXiv, abs/1810.10183 (2018).
159.  [\[159\]](#ch7.xhtml#refbib_159b) O. LI, H. LIU, C. CHEN, AND C. RUDIN, *Deep learning for case-based reasoning through prototypes: A neural network that explains its predictions*, in Proceedings of the AAAI Conference on Artificial Intelligence, vol. 32, 2018.
160.  [\[160\]](#ch4.xhtml#refbib_160b) Y. LIANG, N. DUAN, Y. GONG, N. WU, F. GUO, W. QI, M. GONG, L. SHOU, D. JIANG, G. CAO, X. FAN, R. ZHANG, R. AGRAWAL, E. CUI, S. WEI, T. BHARTI, Y. QIAO, J. CHEN, W. WU, S. LIU, F. YANG, D. CAMPOS, R. MAJUMDER, AND M. ZHOU, *XGLUE: A new benchmark dataset for cross-lingual pre-training, understanding and generation*, in Proceedings of the 2020 Conference on Empirical Methods in Natural Language Processing, EMNLP 2020, Online, November 16–20, 2020, B. Webber, T. Cohn, Y. He, and Y. Liu, eds., Association for Computational Linguistics, 2020, pp. 6008–6018.
161.  [\[161\]](#ch4.xhtml#refbib_161b) J. LIBOVICKÝ, R. ROSA, AND A. FRASER, *How language-neutral is multilingual bert?*, arXiv preprint arXiv:1911.03310, (2019).
162.  [\[162\]](#ch4.xhtml#refbib_162b) T. LIMISIEWICZ, D. MARECEK, AND R. ROSA, *Universal dependencies according to BERT: both more specific and more general*, in Proceedings of the 2020 Conference on Empirical Methods in Natural Language Processing: Findings, EMNLP 2020, Online Event, 16–20 November 2020, T. Cohn, Y. He, and Y. Liu, eds., vol. EMNLP 2020 of Findings of ACL, Association for Computational Linguistics, 2020, pp. 2710–2722.
163.  [\[163\]](#ch1.xhtml#refbib_163b) T. LIN, Y. WANG, X. LIU, AND X. QIU, *A survey of transformers*, ArXiv, abs/2106.04554 (2021).
164.  [\[164\]](#ch1.xhtml#refbib_164b) S. LINNAINMAA, *The representation of the cumulative rounding error of an algorithm as a Taylor expansion of the local rounding errors*, Master's thesis, Univ. Helsinki, 1970.
165.  [\[165\]](#ch4.xhtml#refbib_165b) C. LIU, T. HSU, Y. CHUANG, AND H. LEE, *A study of cross-lingual ability and language-specific information in multilingual BERT*, CoRR, abs/2004.09205 (2020).
166.  [\[166\]](#ch7.xhtml#refbib_166b) H. LIU, Q. YIN, AND W. Y. WANG, *Towards explainable nlp: A generative explanation framework for text classification*, arXiv preprint arXiv:1811.00196, (2018).
167.  [\[167\]](#ch1.xhtml#refbib_167b) P. J. LIU, M. SALEH, E. POT, B. GOODRICH, R. SEPASSI, L. KAISER, AND N. M. SHAZEER, *Generating [Wikipedia](http://Wikipedia) by summarizing long sequences*, ArXiv, abs/1801.10198 (2018).
168.  [\[168\]](#ch4.xhtml#refbib_168b) Q. LIU, D. MCCARTHY, I. VULIĆ, AND A. KORHONEN, *Investigating cross-lingual alignment methods for contextualized embeddings with token-level evaluation*, in Proceedings of the 23rd Conference on Computational Natural Language Learning (CoNLL), Hong Kong, China, November 2019, Association for Computational Linguistics, pp. 33–43.
169.  [\[169\]](#ch4.xhtml#refbib_169b) Y. LIU, J. GU, N. GOYAL, X. LI, S. EDUNOV, M. GHAZVININEJAD, M. LEWIS, AND L. ZETTLEMOYER, *Multilingual denoising pre-training for neural machine translation*, Transactions of the Association for Computational Linguistics, 8 (2020), pp. 726–742.
170.  [\[170\]](#ch3.xhtml#refbib_170b) Y. LIU, M. OTT, N. GOYAL, J. DU, M. JOSHI, D. CHEN, O. LEVY, M. LEWIS, L. ZETTLEMOYER, AND V. STOYANOV, *Roberta: A robustly optimized bert pretraining approach*, ArXiv, abs/1907.11692 (2019).
171.  [\[171\]](#ch4.xhtml#refbib_171b) Z. LIU, G. I. WINATA, A. MADOTTO, AND P. FUNG, *Exploring fine-tuning techniques for pre-trained cross-lingual models via continual learning*, CoRR, abs/2004.14218 (2020).
172.  [\[172\]](#ch2.xhtml#refbib_172b) I. LOSHCHILOV AND F. HUTTER, *Decoupled weight decay regularization*, arXiv preprint arXiv:1711.05101, (2017).
173.  [\[173\]](#ch6.xhtml#refbib_173b) J. LU, D. BATRA, D. PARIKH, AND S. LEE, *ViLBERT: Pretraining task-agnostic visiolinguistic representations for vision-and-language tasks*, arXiv preprint arXiv:1908.02265, (2019).
174.  [\[174\]](#ch1.xhtml#refbib_174b) Y. LU, Z. LI, D. HE, Z. SUN, B. DONG, T. QIN, L. WANG, AND T.-Y. LIU, *Understanding and improving transformer from a multi-particle dynamic system point of view*, ArXiv, abs/1906.02762 (2019).
175.  [\[175\]](#ch4.xhtml#refbib_175b) F. LUO, W. WANG, J. LIU, Y. LIU, B. BI, S. HUANG, F. HUANG, AND L. SI, *{VECO}: Variable encoder-decoder pre-training for cross-lingual understanding and generation*, 2021.
176.  [\[176\]](#ch2.xhtml#refbib_176b) M. LUONG, H. PHAM, AND C. D. MANNING, *Effective approaches to attention-based neural machine translation*, CoRR, abs/1508.04025 (2015).
177.  [\[177\]](#ch5.xhtml#refbib_177b) X. MA, X. KONG, S. WANG, C. ZHOU, J. MAY, H. MA, AND L. ZETTLEMOYER, *Luna: Linear unified nested attention*, ArXiv, abs/2106.01540 (2021).
178.  [\[178\]](#ch7.xhtml#refbib_178b) A. MADRY, A. MAKELOV, L. SCHMIDT, D. TSIPRAS, AND A. VLADU, *Towards deep learning models resistant to adversarial attacks*, arXiv preprint arXiv:1706.06083, (2017).
179.  [\[179\]](#ch1.xhtml#refbib_179b) W. S. MCCULLOCH AND W. PITTS, *Neurocomputing: Foundations of research*, MIT Press, 1988, ch. A Logical Calculus of the Ideas Immanent in Nervous Activity, pp. 15–27.
180.  [\[180\]](#ch1.xhtml#refbib_180b) S. MEHTA, M. GHAZVININEJAD, S. IYER, L. ZETTLEMOYER, AND H. HAJISHIRZI, *Delight: Deep and light-weight transformer*, in ICLR, 2021.
181.  [\[181\]](#ch5.xhtml#refbib_181b) S. MEHTA, R. KONCEL\-KEDZIORSKI, M. RASTEGARI, AND H. HAJISHIRZI, *Pyramidal recurrent unit for language modeling*, in EMNLP, 2018.
182.  [\[182\]](#ch5.xhtml#refbib_182b) \_\_\_\_\_, *Define: Deep factorized input word embeddings for neural sequence modeling*, ArXiv, abs/1911.12385 (2020).
183.  [\[183\]](#ch1.xhtml#refbib_183b) T. MIKOLOV, K. CHEN, G. CORRADO, AND J. DEAN, *Efficient estimation of word representations in vector space*, CoRR, abs/1301.3781 (2013).
184.  [\[184\]](#ch1.xhtml#refbib_184b) T. MIKOLOV, M. KARAFIÁT, L. BURGET, J. CERNOCKÝ, AND S. KHUDANPUR, *Recurrent neural network based language model.*, in INTERSPEECH, T. Kobayashi, K. Hirose, and S. Nakamura, eds., ISCA, 2010, pp. 1045–1048.
185.  [\[185\]](#ch1.xhtml#refbib_185b) T. MIKOLOV, I. SUTSKEVER, K. CHEN, G. S. CORRADO, AND J. DEAN, *Distributed representations of words and phrases and their compositionality*, in Advances in Neural Information Processing Systems 26, C. J. C. Burges, L. Bottou, M. Welling, Z. Ghahramani, and K. Q. Weinberger, eds., Curran Associates, Inc., 2013, pp. 3111–3119.
186.  [\[186\]](#ch1.xhtml#refbib_186b) M. MINSKY AND S. A. PAPERT, Perceptrons: An introduction to computational geometry, MIT press, 2017.
187.  [\[187\]](#ch7.xhtml#refbib_187b) G. MONTAVON, S. LAPUSCHKIN, A. BINDER, W. SAMEK, AND K.-R. MÜLLER, *Explaining nonlinear classification decisions with deep Taylor decomposition*, Pattern Recognition, 65 (2017), pp. 211–222.
188.  [\[188\]](#ch7.xhtml#refbib_188b) G. MONTAVON, W. SAMEK, AND K.-R. MÜLLER, *Methods for interpreting and understanding deep neural networks*, Digital Signal Processing, 73 (2018), pp. 1–15.
189.  [\[189\]](#ch7.xhtml#refbib_189b) S.-M. MOOSAVI\-DEZFOOLI, A. FAWZI, O. FAWZI, AND P. FROSSARD, *Universal adversarial perturbations*, in Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, 2017, pp. 1765–1773.
190.  [\[190\]](#ch6.xhtml#refbib_190b) N. MOSTAFAZADEH, M. ROTH, A. LOUIS, N. CHAMBERS, AND J. F. ALLEN, *LSDSem 2017 shared task: The story cloze test*, in [LSDSem@EACL](mailto:LSDSem@EACL), 2017.
191.  [\[191\]](#ch7.xhtml#refbib_191b) A. NGUYEN, J. YOSINSKI, AND J. CLUNE, *Deep neural networks are easily fooled: High confidence predictions for unrecognizable images*, in Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, 2015, pp. 427–436.
192.  [\[192\]](#ch4.xhtml#refbib_192b) J. NIVRE, M. ABRAMS, Ž. AGIĆ, L. AHRENBERG, L. ANTONSEN, K. APLONOVA, M. J. ARANZABE, G. ARUTIE, M. ASAHARA, L. ATEYAH, M. ATTIA, AND et. al.,*Universal dependencies 2.3*, 2018. LINDAT/CLARIAH-CZ digital library at the Institute of Formal and Applied Linguistics (ÚFAL), Faculty of Mathematics and Physics, Charles University.
193.  [\[193\]](#ch4.xhtml#refbib_193b) J. NIVRE, R. BLOKLAND, N. PARTANEN, AND M. RIESSLER, *Universal dependencies 2.2*, November 2018.
194.  [\[194\]](#ch4.xhtml#refbib_194b) X. OUYANG, S. WANG, C. PANG, Y. SUN, H. TIAN, H. WU, AND H. WANG, *ERNIE-M: Enhanced multilingual representation by aligning cross-lingual semantics with monolingual corpora*, 2021.
195.  [\[195\]](#ch7.xhtml#refbib_195b) D. H. PARK, L. A. HENDRICKS, Z. AKATA, A. ROHRBACH, B. SCHIELE, T. DARRELL, AND M. ROHRBACH, *Multimodal explanations: Justifying decisions and pointing to the evidence*, in Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, 2018, pp. 8779–8788.
196.  [\[196\]](#ch1.xhtml#refbib_196b) D. B. PARKER, *Learning-logic*, Tech. Rep. TR-47, Center for Comp. Research in Economics and Management Sci., MIT, 1985.
197.  [\[197\]](#ch6.xhtml#refbib_197b) M. PETERS, M. NEUMANN, M. IYYER, M. GARDNER, C. CLARK, K. LEE, AND L. ZETTLEMOYER, *Deep contextualized word representations*, in Proceedings of the 2018 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies, Volume 1 (Long Papers), New Orleans, Louisiana, June 2018, Association for Computational Linguistics, pp. 2227–2237.
198.  [\[198\]](#ch4.xhtml#refbib_198b) J. PHANG, I. CALIXTO, P. M. HTUT, Y. PRUKSACHATKUN, H. LIU, C. VANIA, K. KANN, AND S. R. BOWMAN, *English intermediate-task training improves zero-shot cross-lingual transfer too*, in Proceedings of the 1st Conference of the Asia-Pacific Chapter of the Association for Computational Linguistics and the 10th International Joint Conference on Natural Language Processing, AACL/IJCNLP 2020, Suzhou, China, December 4–7, 2020, K. Wong, K. Knight, and H. Wu, eds., Association for Computational Linguistics, 2020, pp. 557–575.
199.  [\[199\]](#ch4.xhtml#refbib_199b) T. PIRES, E. SCHLINGER, AND D. GARRETTE, *How multilingual is multilingual bert?*, in Proceedings of the 57th Conference of the Association for Computational Linguistics, ACL 2019, Florence, Italy, July 28–August 2, 2019, Volume 1: Long Papers, A. Korhonen, D. R. Traum, and L. Màrquez, eds., Association for Computational Linguistics, 2019, pp. 4996–5001.
200.  [\[200\]](#ch4.xhtml#refbib_200b) E. M. PONTI, G. GLAVAŠ, O. MAJEWSKA, Q. LIU, I. VULIČ, AND A. KORHONEN, *XCOPA: A multilingual dataset for causal commonsense reasoning*, in Proceedings of the 2020 Conference on Empirical Methods in Natural Language Processing (EMNLP), 2020.
201.  [\[201\]](#ch1.xhtml#refbib_201b) O. PRESS, N. A. SMITH, AND O. LEVY, *Improving transformer models by reordering their sublayers*, in ACL, 2020.
202.  [\[202\]](#ch6.xhtml#refbib_202b) A. RADFORD AND K. NARASIMHAN, *Improving language understanding by generative pre-training*, 2018.
203.  [\[203\]](#ch6.xhtml#refbib_203b) A. RADFORD, J. WU, R. CHILD, D. LUAN, D. AMODEI, AND I. SUTSKEVER, *Language models are unsupervised multitask learners*, 2019.
204.  [\[204\]](#ch1.xhtml#refbib_204b) J. W. RAE, A. POTAPENKO, S. M. JAYAKUMAR, AND T. LILLICRAP, *Compressive transformers for long-range sequence modelling*, ArXiv, abs/1911.05507 (2020).
205.  [\[205\]](#ch1.xhtml#refbib_205b) C. RAFFEL, N. M. SHAZEER, A. ROBERTS, K. LEE, S. NARANG, M. MATENA, Y. ZHOU, W. LI, AND P. J. LIU, *Exploring the limits of transfer learning with a unified text-to-text transformer*, ArXiv, abs/1910.10683 (2020).
206.  [\[206\]](#ch7.xhtml#refbib_206b) M. RAGHU, J. GILMER, J. YOSINSKI, AND J. SOHL\-DICKSTEIN, *SVCCA: Singular vector canonical correlation analysis for deep learning dynamics and interpretability*, arXiv preprint arXiv:1706.05806, (2017).
207.  [\[207\]](#ch7.xhtml#refbib_207b) G. RAS, M. VAN GERVEN, and P. HASELAGER, *Explanation methods in deep learning: Users, values, concerns and challenges*, in Explainable and Interpretable Models in Computer Vision and Machine Learning, Springer, 2018, pp. 19–36.
208.  [\[208\]](#ch7.xhtml#refbib_208b) M. T. RIBEIRO, S. SINGH, AND C. GUESTRIN, *“why should i trust you?” explaining the predictions of any classifier*, in Proceedings of the 22nd ACM SIGKDD International Conference on Knowledge Discovery and Data Mining, 2016, pp. 1135–1144.
209.  [\[209\]](#ch7.xhtml#refbib_209b) \_\_\_\_\_, *Anchors: High-precision model-agnostic explanations*, in Proceedings of the AAAI Conference on Artificial Intelligence, vol. 32, 2018.
210.  [\[210\]](#ch7.xhtml#refbib_210b) M. ROBNIK\-ŠIKONJA AND I. KONONENKO, *Explaining classifications for individual instances*, IEEE Transactions on Knowledge and Data Engineering, 20 (2008), pp. 589–600.
211.  [\[211\]](#ch7.xhtml#refbib_211b) T. ROCKTÄSCHEL, E. GREFENSTETTE, K. M. HERMANN, T. KOČISKÝ, AND P. BLUNSOM, *Reasoning about entailment with neural attention*, arXiv preprint arXiv:1509.06664, (2015).
212.  [\[212\]](#ch1.xhtml#refbib_212b) F. ROSENBLATT, *The perceptron: A probabilistic model for information storage and organization in the brain*, Psychological Review, (1958), pp. 65–386.
213.  [\[213\]](#ch1.xhtml#refbib_213b) D. ROTHMAN, Transformers for Natural Language Processing, Packt, 2021.
214.  [\[214\]](#ch1.xhtml#refbib_214b) A. ROY, M. SAFFAR, A. VASWANI, AND D. GRANGIER, *Efficient content-based sparse attention with routing transformers*, Transactions of the Association for Computational Linguistics, 9 (2021), pp. 53–68.
215.  [\[215\]](#ch4.xhtml#refbib_215b) U. ROY, N. CONSTANT, R. AL\-RFOU, A. BARUA, A. PHILLIPS, AND Y. YANG, *LAReQA: Language-agnostic answer retrieval from a multilingual pool*, in Proceedings of the 2020 Conference on Empirical Methods in Natural Language Processing (EMNLP), Online, November 2020, Association for Computational Linguistics, pp. 5919–5930.
216.  [\[216\]](#ch4.xhtml#refbib_216b) S. RUDER, N. CONSTANT, J. BOTHA, A. SIDDHANT, O. FIRAT, J. FU, P. LIU, J. HU, G. NEUBIG, AND M. JOHNSON, *XTREME-R: towards more challenging and nuanced multilingual evaluation*, CoRR, abs/2104.07412 (2021).
217.  [\[217\]](#ch1.xhtml#refbib_217b) D. E. RUMELHART, G. E. HINTON, AND R. J. WILLIAMS, *Neurocomputing: Foundations of research*, MIT Press, 1988, ch. Learning Representations by Back-propagating Errors, pp. 696–699.
218.  [\[218\]](#ch7.xhtml#refbib_218b) P. SAMANGOUEI, M. KABKAB, AND R. CHELLAPPA, *Defense-GAN: Protecting classifiers against adversarial attacks using generative models*, arXiv preprint arXiv:1805.06605, (2018).
219.  [\[219\]](#ch6.xhtml#refbib_219b) S. SCHNEIDER, A. BAEVSKI, R. COLLOBERT, AND M. AULI, *wav2vec: Unsupervised pre-training for speech recognition*, in INTERSPEECH, 2019.
220.  [\[220\]](#ch4.xhtml#refbib_220b) M. SCHUSTER AND K. NAKAJIMA, *Japanese and Korean voice search*, 2012 IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP), (2012), pp. 5149–5152.
221.  [\[221\]](#ch4.xhtml#refbib_221b) H. SCHWENK AND X. LI, *A corpus for multilingual document classification in eight languages*, in Proceedings of the Eleventh International Conference on Language Resources and Evaluation (LREC 2018), N. C. C. chair), K. Choukri, C. Cieri, T. Declerck, S. Goggi, K. Hasida, H. Isahara, B. Maegaard, J. Mariani, H. Mazo, A. Moreno, J. Odijk, S. Piperidis, and T. Tokunaga, eds., Paris, France, may 2018, European Language Resources Association (ELRA).
222.  [\[222\]](#ch4.xhtml#refbib_222b) R. SENNRICH, B. HADDOW, AND A. BIRCH, *Improving neural machine translation models with monolingual data*, 2016.
223.  [\[223\]](#ch4.xhtml#refbib_223b) R. SENNRICH, B. HADDOW, AND A. BIRCH, *Neural machine translation of rare words with subword units*, in Proceedings of the 54th Annual Meeting of the Association for Computational Linguistics (Volume 1: Long Papers), Berlin, Germany, August 2016, Association for Computational Linguistics, pp. 1715–1725.
224.  [\[224\]](#ch5.xhtml#refbib_224b) P. SHAW, J. USZKOREIT, AND A. VASWANI, *Self-attention with relative position representations*, in NAACL-HLT, 2018.
225.  [\[225\]](#ch5.xhtml#refbib_225b) N. SHAZEER, A. MIRHOSEINI, K. MAZIARZ, A. DAVIS, Q. LE, G. HINTON, AND J. DEAN, *Outrageously large neural networks: The sparsely-gated mixture-of-experts layer*, arXiv preprint arXiv:1701.06538, (2017).
226.  [\[226\]](#ch1.xhtml#refbib_226b) N. M. SHAZEER, *Fast transformer decoding: One write-head is all you need*, ArXiv, abs/1911.02150 (2019).
227.  [\[227\]](#ch1.xhtml#refbib_227b) N. M. SHAZEER, Z. LAN, Y. CHENG, N. DING, AND L. HOU, *Talking-heads attention*, ArXiv, abs/2003.02436 (2020).
228.  [\[228\]](#ch7.xhtml#refbib_228b) A. SHRIKUMAR, P. GREENSIDE, AND A. KUNDAJE, *Learning important features through propagating activation differences*, inInternational Conference on Machine Learning, PMLR, 2017, pp. 3145–3153.
229.  [\[229\]](#ch4.xhtml#refbib_229b) J. SINGH, B. MCCANN, R. SOCHER, AND C. XIONG, *Bert is not an interlingua and the bias of tokenization*, in Proceedings of the 2nd Workshop on Deep Learning Approaches for Low-Resource NLP (DeepLo 2019), 2019, pp. 47–55.
230.  [\[230\]](#ch6.xhtml#refbib_230b) R. SOCHER, A. PERELYGIN, J. WU, J. CHUANG, C. D. MANNING, A. NG, AND C. POTTS, *Recursive deep models for semantic compositionality over a sentiment treebank*, in EMNLP, 2013.
231.  [\[231\]](#ch4.xhtml#refbib_231b) K. SONG, X. TAN, T. QIN, J. LU, AND T.-Y. LIU, *Mass: Masked sequence to sequence pre-training for language generation*, in ICML, 2019.
232.  [\[232\]](#ch1.xhtml#refbib_232b) J. SU, Y. LU, S. PAN, B. WEN, AND Y. LIU, *Roformer: Enhanced transformer with rotary position embedding*, ArXiv, abs/2104.09864 (2021).
233.  [\[233\]](#ch7.xhtml#refbib_233b) J. SU, D. V. VARGAS, AND K. SAKURAI, *One pixel attack for fooling deep neural networks*, IEEE Transactions on Evolutionary Computation, 23 (2019), pp. 828–841.
234.  [\[234\]](#ch1.xhtml#refbib_234b) S. SUBRAMANIAN, R. COLLOBERT, M. RANZATO, AND Y.-L. BOUREAU, *Multi-scale transformer language models*, ArXiv, abs/2005.00581 (2020).
235.  [\[235\]](#ch1.xhtml#refbib_235b) S. SUKHBAATAR, E. GRAVE, P. BOJANOWSKI, AND A. JOULIN, *Adaptive attention span in transformers*, in ACL, 2019.
236.  [\[236\]](#ch7.xhtml#refbib_236b) M. SUNDARARAJAN, A. TALY, AND Q. YAN, *Axiomatic attribution for deep networks*, in International Conference on Machine Learning, PMLR, 2017, pp. 3319–3328.
237.  [\[237\]](#ch1.xhtml#refbib_237b) I. SUTSKEVER, *Training recurrent neural networks*, Ph.D. Thesis from University of Toronto, Toronto, Ont., Canada, (2013).
238.  [\[238\]](#ch1.xhtml#refbib_238b) I. SUTSKEVER, O. VINYALS, AND Q. V. LE, *Sequence to sequence learning with neural networks*, in Advances in neural information processing systems, 2014, pp. 3104–3112.
239.  [\[239\]](#ch6.xhtml#refbib_239b) R. S. SUTTON AND A. G. BARTO, *Reinforcement learning: An introduction*, IEEE Transactions on Neural Networks, 16 (2005), pp. 285–286.
240.  [\[240\]](#ch7.xhtml#refbib_240b) S. TAN, R. CARUANA, G. HOOKER, P. KOCH, AND A. GORDO, *Learning global additive explanations for neural nets using model distillation*, arXiv preprint arXiv:1801.08640, (2018).
241.  [\[241\]](#ch1.xhtml#refbib_241b) Y. TAY, D. BAHRI, D. METZLER, D.-C. JUAN, Z. ZHAO, AND C. ZHENG, *Synthesizer: Rethinking self-attention in transformer models*, ArXiv, abs/2005.00743 (2021).
242.  [\[242\]](#ch5.xhtml#refbib_242b) Y. TAY, D. BAHRI, L. YANG, D. METZLER, AND D.-C. JUAN, *Sparse Sinkhorn attention*, in ICML, 2020.
243.  [\[243\]](#ch1.xhtml#refbib_243b) Y. TAY, M. DEHGHANI, D. BAHRI, AND D. METZLER, *Efficient transformers: A survey*, ArXiv, abs/2009.06732 (2020).
244.  [\[244\]](#ch2.xhtml#refbib_244b) I. TENNEY, D. DAS, AND E. PAVLICK, *BERT rediscovers the classical NLP pipeline*, in Proceedings of the 57th Annual Meeting of the Association for Computational Linguistics, July 2019, pp. 4593–4601.
245.  [\[245\]](#ch7.xhtml#refbib_245b) I. TENNEY, P. XIA, B. CHEN, A. WANG, A. POLIAK, R. T. MCCOY, N. KIM, B. VAN DURME, S. R. BOWMAN, D. DAS, et al., *What do you learn from context? probing for sentence structure in contextualized word representations*, arXiv preprint arXiv:1905.06316, (2019).
246.  [\[246\]](#ch4.xhtml#refbib_246b) E. F. TJONG KIM SANG, *Introduction to the CoNLL-2002 shared task: Language-independent named entity recognition*, in COLING-02: The 6th Conference on Natural Language Learning 2002 (CoNLL-2002), 2002.
247.  [\[247\]](#ch4.xhtml#refbib_247b) E. F. TJONG KIM SANG AND F. DE MEULDER, *Introduction to the CoNLL-2003 shared task: Language-independent named entity recognition*, in Proceedings of the Seventh Conference on Natural Language Learning at HLT-NAACL 2003, 2003, pp. 142–147.
248.  [\[248\]](#ch1.xhtml#refbib_248b) J. L. UDAY KAMATH AND J. WHITAKER, *Deep Learning for NLP and Speech Recognition*, 2019.
249.  [\[249\]](#ch3.xhtml#refbib_249b) V. VALKOV, *Sentiment Analysis with BERT and Transformers by Hugging Face using PyTorch and Python*. [https://bit.ly/​32Mb2mw](https://bit.ly), 2020.
250.  [\[250\]](#ch6.xhtml#refbib_250b) A. VAN DEN OORD, Y. LI, AND O. VINYALS, *Representation learning with contrastive predictive coding*, ArXiv, abs/1807.03748 (2018).
251.  [\[251\]](#ch4.xhtml#refbib_251b) A. VAN DEN OORD, Y. LI, AND O. VINYALS, *Representation learning with contrastive predictive coding*, 2019.
252.  [\[252\]](#ch7.xhtml#refbib_252b) K. R. VARSHNEY AND H. ALEMZADEH, *On the safety of machine learning: Cyber-physical systems, decision sciences, and data products*, Big data, 5 (2017), pp. 246–255.
253.  [\[253\]](#ch3.xhtml#refbib_253b) A. VASWANI, N. SHAZEER, N. PARMAR, J. USZKOREIT, L. JONES, A. N. GOMEZ, L. KAISER, AND I. POLOSUKHIN, *Attention is all you need*, CoRR, abs/1706.03762 (2017).
254.  [\[254\]](#ch1.xhtml#refbib_254b) A. VASWANI, N. M. SHAZEER, N. PARMAR, J. USZKOREIT, L. JONES, A. N. GOMEZ, L. KAISER, AND I. POLOSUKHIN, *Attention is all you need*, ArXiv, abs/1706.03762 (2017).
255.  [\[255\]](#ch5.xhtml#refbib_255b) J. VIG, *A multiscale visualization of attention in the transformer model*, in Proceedings of the 57th Annual Meeting of the Association for Computational Linguistics: System Demonstrations, Florence, Italy, July 2019, Association for Computational Linguistics, pp. 37–42.
256.  [\[256\]](#ch1.xhtml#refbib_256b) A. VYAS, A. KATHAROPOULOS, AND F. FLEURET, *Fast transformers with clustered attention*, ArXiv, abs/2007.04825 (2020).
257.  [\[257\]](#ch6.xhtml#refbib_257b) A. WANG, A. SINGH, J. MICHAEL, F. HILL, O. LEVY, AND S. BOWMAN, *GLUE: A multi-task benchmark and analysis platform for natural language understanding*, in Proceedings of the 2018 EMNLP Workshop BlackboxNLP: Analyzing and Interpreting Neural Networks for NLP, Brussels, Belgium, November 2018, Association for Computational Linguistics, pp. 353–355.
258.  [\[258\]](#ch6.xhtml#refbib_258b) C. WANG, A. WU, J. M. PINO, A. BAEVSKI, M. AULI, AND A. CONNEAU, *Large-scale self- and semi-supervised learning for speech translation*, ArXiv, abs/2104.06678 (2021).
259.  [\[259\]](#ch1.xhtml#refbib_259b) S. WANG, B. Z. LI, M. KHABSA, H. FANG, AND H. MA, *Linformer: Self-attention with linear complexity*, ArXiv, abs/2006.04768 (2020).
260.  [\[260\]](#ch4.xhtml#refbib_260b) X. WANG, Y. JIANG, N. BACH, T. WANG, F. HUANG, AND K. TU, *Structure-level knowledge distillation for multilingual sequence labeling*, in Proceedings of the 58th Annual Meeting of the Association for Computational Linguistics, ACL 2020, Online, July 5–10, 2020, D. Jurafsky, J. Chai, N. Schluter, and J.R. Tetreault, eds., Association for Computational Linguistics, 2020, pp. 3317–3330.
261.  [\[261\]](#ch4.xhtml#refbib_261b) Y. WANG, W. CHE, J. GUO, Y. LIU, AND T. LIU, *Cross-lingual BERT transformation for zero-shot dependency parsing*, in Proceedings of the 2019 Conference on Empirical Methods in Natural Language Processing and the 9th International Joint Conference on Natural Language Processing, EMNLP-IJCNLP 2019, Hong Kong, China, November 3–7, 2019, K. Inui, J. Jiang, V. Ng, and X. Wan, eds., Association for Computational Linguistics, 2019, pp. 5720–5726.
262.  [\[262\]](#ch1.xhtml#refbib_262b) Z. WANG, Y. MA, Z. LIU, AND J. TANG, *R-transformer: Recurrent neural network enhanced transformer*, ArXiv, abs/1907.05572 (2019).
263.  [\[263\]](#ch4.xhtml#refbib_263b) Z. WANG, J. XIE, R. XU, Y. YANG, G. NEUBIG, AND J. G. CARBONELL, *Cross-lingual alignment vs joint training: A comparative study and A simple unified framework*, in 8th International Conference on Learning Representations, ICLR 2020, Addis Ababa, Ethiopia, April 26–30, 2020, [OpenReview.net](http://OpenReview.net), 2020.
264.  [\[264\]](#ch6.xhtml#refbib_264b) A. WARSTADT, A. SINGH, AND S. R. BOWMAN, *Neural network acceptability judgments*, arXiv preprint arXiv:1805.12471, (2018).
265.  [\[265\]](#ch5.xhtml#refbib_265b) D. WATTS AND S. STROGATZ, *Collective dynamics of ‘small-world’ networks*, Nature, 393 (1998), pp. 440–442.
266.  [\[266\]](#ch4.xhtml#refbib_266b) X. WEI, R. WENG, Y. HU, L. XING, H. YU, AND W. LUO, *On learning universal representations across languages*, in 9th International Conference on Learning Representations, ICLR 2021, Virtual Event, Austria, May 3–7, 2021, [OpenReview.net](http://OpenReview.net), 2021.
267.  [\[267\]](#ch1.xhtml#refbib_267b) P. J. WERBOS, *Beyond Regression: New Tools for Prediction and Analysis in the Behavioral Sciences*, PhD thesis, Harvard University, 1974.
268.  [\[268\]](#ch7.xhtml#refbib_268b) J. WHITTLESTONE, R. NYRUP, A. ALEXANDROVA, AND S. CAVE, *The role and limits of principles in ai ethics: towards a focus on tensions*, in Proceedings of the 2019 AAAI/ACM Conference on AI, Ethics, and Society, 2019, pp. 195–200.
269.  [\[269\]](#ch7.xhtml#refbib_269b) S. WIEGREFFE AND Y. PINTER, *Attention is not not explanation*, arXiv preprint arXiv:1908.04626, (2019).
270.  [\[270\]](#ch1.xhtml#refbib_270b) C. WU, F. WU, T. QI, AND Y. HUANG, *Hi-transformer: Hierarchical interactive transformer for efficient and effective long document modeling*, ArXiv, abs/2106.01040 (2021).
271.  [\[271\]](#ch4.xhtml#refbib_271b) S. WU AND M. DREDZE, *Beto, Bentz, Becas: The surprising cross-lingual effectiveness of BERT*, in Proceedings of the 2019 Conference on Empirical Methods in Natural Language Processing and the 9th International Joint Conference on Natural Language Processing, EMNLP-IJCNLP 2019, Hong Kong, China, November 3–7, 2019, K. Inui, J. Jiang, V. Ng, and X. Wan, eds., Association for Computational Linguistics, 2019, pp. 833–844.
272.  [\[272\]](#ch1.xhtml#refbib_272b) Y. WU, M. SCHUSTER, Z. CHEN, Q. V. LE, M. NOROUZI, W. MACHEREY, M. KRIKUN, Y. CAO, Q. GAO, K. MACHEREY, et al., *Google's neural machine translation system: Bridging the gap between human and machine translation*, arXiv preprint arXiv:1609.08144, (2016).
273.  [\[273\]](#ch4.xhtml#refbib_273b) Y. WU, M. SCHUSTER, Z. CHEN, Q. V. LE, M. NOROUZI, W. MACHEREY, M. KRIKUN, Y. CAO, Q. GAO, K. MACHEREY, J. KLINGNER, A. SHAH, M. JOHNSON, X. LIU, L. KAISER, S. GOUWS, Y. KATO, T. KUDO, H. KAZAWA, K. STEVENS, G. KURIAN, N. PATIL, W. WANG, C. YOUNG, J. SMITH, J. RIESA, A. RUDNICK, O. VINYALS, G. CORRADO, M. HUGHES, AND J. DEAN, *Google's neural machine translation system: Bridging the gap between human and machine translation*, CoRR, abs/1609.08144 (2016).
274.  [\[274\]](#ch1.xhtml#refbib_274b) Z. WU, Z. LIU, J. LIN, Y. LIN, AND S. HAN, *Lite transformer with long-short range attention*, ArXiv, abs/2004.11886 (2020).
275.  [\[275\]](#ch7.xhtml#refbib_275b) N. XIE, G. RAS, M. VAN GERVEN, AND D. DORAN, *Explainable deep learning: A field guide for the uninitiated*, arXiv preprint arXiv:2004.14545, (2020).
276.  [\[276\]](#ch1.xhtml#refbib_276b) J. XIN, R. TANG, J. LEE, Y. YU, AND J. J. LIN, *DeeBERT: Dynamic early exiting for accelerating bert inference*, in ACL, 2020.
277.  [\[277\]](#ch1.xhtml#refbib_277b) Y. XIONG, Z. ZENG, R. CHAKRABORTY, M. TAN, G. M. FUNG, Y. LI, AND V. SINGH, *Nyströmformer: A Nystöm-based algorithm for approximating self-attention*, in AAAI, 2021.
278.  [\[278\]](#ch7.xhtml#refbib_278b) K. XU, J. BA, R. KIROS, K. CHO, A. COURVILLE, R. SALAKHUDINOV, R. ZEMEL, AND Y. BENGIO, *Show, attend and tell: Neural image caption generation with visual attention*, in International conference on machine learning, PMLR, 2015, pp. 2048–2057.
279.  [\[279\]](#ch6.xhtml#refbib_279b) M. XU, L. YU DUAN, J. CAI, L. CHIA, C. XU, AND Q. TIAN, *HMM-based Audio Keyword Generation*, in PCM, 2004.
280.  [\[280\]](#ch1.xhtml#refbib_280b) L. XUE, A. BARUA, N. CONSTANT, R. AL\-RFOU, S. NARANG, M. KALE, A. ROBERTS, AND C. RAFFEL, *ByT5: Towards a token-free future with pre-trained byte-to-byte models*, ArXiv, abs/2105.13626 (2021).
281.  [\[281\]](#ch4.xhtml#refbib_281b) L. XUE, N. CONSTANT, A. ROBERTS, M. KALE, R. AL\-RFOU, A. SIDDHANT, A. BARUA, AND C. RAFFEL, *mT5: A massively multilingual pre-trained text-to-text transformer*, in NAACL, 2021.
282.  [\[282\]](#ch4.xhtml#refbib_282b) J. YANG, S. MA, D. ZHANG, S. WU, Z. LI, AND M. ZHOU, *Alternating language modeling for cross-lingual pre-training*, Proceedings of the AAAI Conference on Artificial Intelligence, 34 (2020), pp. 9386–9393.
283.  [\[283\]](#ch4.xhtml#refbib_283b) Y. YANG, G. H. ÁBREGO, S. YUAN, M. GUO, Q. SHEN, D. CER, Y. SUNG, B. STROPE, AND R. KURZWEIL, *Improving multilingual sentence embedding using bi-directional dual encoder with additive margin softmax*, CoRR, abs/1902.08564 (2019).
284.  [\[284\]](#ch4.xhtml#refbib_284b) Y. YANG, D. M. CER, A. AHMAD, M. GUO, J. LAW, N. CONSTANT, G. H. ÁBREGO, S. YUAN, C. TAR, Y.-H. SUNG, B. STROPE, AND R. KURZWEIL, *Multilingual universal sentence encoder for semantic retrieval*, in ACL, 2020.
285.  [\[285\]](#ch4.xhtml#refbib_285b) Y. YANG, Y. ZHANG, C. TAR, AND J. BALDRIDGE, *PAWS-X: A Cross-lingual Adversarial Dataset for Paraphrase Identification*, in Proc. of EMNLP, 2019.
286.  [\[286\]](#ch7.xhtml#refbib_286b) Z. YANG, D. YANG, C. DYER, X. HE, A. SMOLA, AND E. HOVY, *Hierarchical attention networks for document classification*, in Proceedings of the 2016 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies, 2016, pp. 1480–1489.
287.  [\[287\]](#ch1.xhtml#refbib_287b) Q. YANG WU, Z. LAN, J. GU, AND Z. YU, *Memformer: The memory-augmented transformer*, ArXiv, abs/2010.06891 (2020).
288.  [\[288\]](#ch7.xhtml#refbib_288b) J. YIM, D. JOO, J. BAE, AND J. KIM, *A gift from knowledge distillation: Fast optimization, network minimization and transfer learning*, in Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, 2017, pp. 4133–4141.
289.  [\[289\]](#ch3.xhtml#refbib_289b) P. YIN, G. NEUBIG, W.-t. YIH, AND S. RIEDEL, *TaBERT: Pretraining for joint understanding of textual and tabular data*, in Proceedings of the 58th Annual Meeting of the Association for Computational Linguistics, Online, July 2020, Association for Computational Linguistics, pp. 8413–8426.
290.  [\[290\]](#ch6.xhtml#refbib_290b) C. YING LEE AND J. R. GLASS, *A nonparametric Bayesian approach to acoustic model discovery*, in ACL, 2012.
291.  [\[291\]](#ch7.xhtml#refbib_291b) X. YUAN, P. HE, Q. ZHU, AND X. LI, *Adversarial examples: Attacks and defenses for deep learning*, IEEE transactions on neural networks and learning systems, 30 (2019), pp. 2805–2824.
292.  [\[292\]](#ch1.xhtml#refbib_292b) M. ZAHEER, G. GURUGANESH, K. A. DUBEY, J. AINSLIE, C. ALBERTI, S. ONTAÑÓN, P. PHAM, A. RAVULA, Q. WANG, L. YANG, AND A. AHMED, *Big bird: Transformers for longer sequences*, ArXiv, abs/2007.14062 (2020).
293.  [\[293\]](#ch7.xhtml#refbib_293b) R. ZELLERS, Y. BISK, A. FARHADI, AND Y. CHOI, *From recognition to cognition: Visual commonsense reasoning*, in Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition, 2019, pp. 6720–6731.
294.  [\[294\]](#ch7.xhtml#refbib_294b) Q. ZHANG, R. CAO, Y. N. WU, AND S.-C. ZHU, *Growing interpretable part graphs on ConvNets via multi-shot learning*, in Proceedings of the AAAI Conference on Artificial Intelligence, vol. 31, 2017.
295.  [\[295\]](#ch7.xhtml#refbib_295b) W. E. ZHANG, Q. Z. SHENG, A. A. F. ALHAZMI, AND C. LI, *Generating textual adversarial examples for deep learning models: A survey*, CoRR, abs/1901.06796, (2019).
296.  [\[296\]](#ch1.xhtml#refbib_296b) X. ZHANG, F. WEI, AND M. ZHOU, *Hibert: Document level pre-training of hierarchical bidirectional transformers for document summarization*, in ACL, 2019.
297.  [\[297\]](#ch4.xhtml#refbib_297b) X. ZHANG, J. J. ZHAO, AND Y. A. LECUN, *Character-level convolutional networks for text classification*, ArXiv, abs/1509.01626 (2015).
298.  [\[298\]](#ch4.xhtml#refbib_298b) W. ZHAO, S. EGER, J. BJERVA, AND I. AUGENSTEIN, *Inducing language-agnostic multilingual representations*, CoRR, abs/2008.09112 (2020).
299.  [\[299\]](#ch1.xhtml#refbib_299b) Y. ZHAO, L. DONG, Y. SHEN, Z. ZHANG, F. WEI, AND W. CHEN, *Memory-efficient differentiable transformer architecture search*, in FINDINGS, 2021.
300.  [\[300\]](#ch4.xhtml#refbib_300b) W. ZHENG, Z. CHEN, J. LU, AND J. ZHOU, *Hardness-aware deep metric learning*, in Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR), June 2019.
301.  [\[253\]](#ch7.xhtml#refbib_301b) B. ZHOU, A. KHOSLA, A. LAPEDRIZA, A. OLIVA, AND A. TORRALBA, *Object detectors emerge in deep scene cnns*, arXiv preprint arXiv:1412.6856, (2014).
302.  [\[302\]](#ch1.xhtml#refbib_302b) H. ZHOU, S. ZHANG, J. PENG, S. ZHANG, J. LI, H. XIONG, AND W. ZHANG, *Informer: Beyond efficient transformer for long sequence time-series forecasting*, in AAAI, 2021.
303.  [\[303\]](#ch6.xhtml#refbib_303b) Y. ZHU, R. KIROS, R. S. ZEMEL, R. SALAKHUTDINOV, R. URTASUN, A. TORRALBA, AND S. FIDLER, *Aligning books and movies: Towards story-like visual explanations by watching movies and reading books*, 2015 IEEE International Conference on Computer Vision (ICCV), (2015), pp. 19–27.
304.  [\[304\]](#ch7.xhtml#refbib_304b) L. M. ZINTGRAF, T. S. COHEN, T. ADEL, AND M. WELLING, *Visualizing deep neural network decisions: Prediction difference analysis*, arXiv preprint arXiv:1702.04595, (2017).
305.  [\[305\]](#ch4.xhtml#refbib_305b) P. ZWEIGENBAUM, S. SHAROFF, AND R. RAPP, *Overview of the second BUCC shared task: Spotting parallel sentences in comparable corpora*, in Proceedings of the 10th Workshop on Building and Using Comparable Corpora, Vancouver, Canada, August 2017, Association for Computational Linguistics, pp. 60–67.

# Index

*   activation maximization, [192](#ch7.xhtml#p192)
*   adversarial attacks, [189](#ch7.xhtml#p189)
*   adversarial defense, [189](#ch7.xhtml#p189)
*   ALM, [77](#ch4.xhtml#p77)
*   AMBER, [81](#ch4.xhtml#p81)
*   anchors, [197](#ch7.xhtml#p197)
*   Applications, [91](#ch4.xhtml#p91), [92](#ch4.xhtml#p92), [97](#ch4.xhtml#p97)
*   attention, [14](#ch2.xhtml#p14), [114](#ch5.xhtml#p114), [117](#ch5.xhtml#p117), [120](#ch5.xhtml#p120), [127](#ch5.xhtml#p127), [131](#ch5.xhtml#p131), [172](#ch6.xhtml#p172) 
    *   attention logits, [114](#ch5.xhtml#p114), [132](#ch5.xhtml#p132), [137](#ch5.xhtml#p137)–[139](#ch5.xhtml#p137), [171](#ch6.xhtml#p171)
    *   attention mechanism complexity, [111](#ch5.xhtml#p111), [112](#ch5.xhtml#p112), [123](#ch5.xhtml#p123), [124](#ch5.xhtml#p124), [126](#ch5.xhtml#p126), [131](#ch5.xhtml#p131)–[133](#ch5.xhtml#p131), [140](#ch5.xhtml#p140), [144](#ch5.xhtml#p144), [157](#ch6.xhtml#p157), [173](#ch6.xhtml#p173)
    *   axial attention, [164](#ch6.xhtml#p164), [172](#ch6.xhtml#p172)
    *   cross-attention, [121](#ch5.xhtml#p121), [142](#ch5.xhtml#p142), [150](#ch5.xhtml#p150)
    *   dilated sliding window, [125](#ch5.xhtml#p125)
    *   global attention, [124](#ch5.xhtml#p124), [125](#ch5.xhtml#p125), [135](#ch5.xhtml#p135), [137](#ch5.xhtml#p137), [171](#ch6.xhtml#p171)
    *   kernel formalism, [131](#ch5.xhtml#p131)
    *   masked multi-head attention, [25](#ch2.xhtml#p25), [160](#ch6.xhtml#p160)
    *   multi-head attention, [24](#ch2.xhtml#p24), [111](#ch5.xhtml#p111), [113](#ch5.xhtml#p113), [120](#ch5.xhtml#p120), [122](#ch5.xhtml#p122), [137](#ch5.xhtml#p137)–[139](#ch5.xhtml#p137), [142](#ch5.xhtml#p142), [147](#ch5.xhtml#p147), [160](#ch6.xhtml#p160), [170](#ch6.xhtml#p170), [174](#ch6.xhtml#p174), [176](#ch6.xhtml#p176)
    *   nested attention, [141](#ch5.xhtml#p141)
    *   parameter sharing, [144](#ch5.xhtml#p144)
    *   pooled attention, [167](#ch6.xhtml#p167)
    *   self-attention, [23](#ch2.xhtml#p23), [110](#ch5.xhtml#p110), [115](#ch5.xhtml#p115), [121](#ch5.xhtml#p121), [124](#ch5.xhtml#p124), [131](#ch5.xhtml#p131), [150](#ch5.xhtml#p150), [164](#ch6.xhtml#p164), [170](#ch6.xhtml#p170)
    *   short-range attention, [124](#ch5.xhtml#p124), [171](#ch6.xhtml#p171), [173](#ch6.xhtml#p173)
    *   sliding window, [124](#ch5.xhtml#p124), [125](#ch5.xhtml#p125), [133](#ch5.xhtml#p133), [137](#ch5.xhtml#p137), [140](#ch5.xhtml#p140)
    *   sparsity, [124](#ch5.xhtml#p124), [133](#ch5.xhtml#p133), [137](#ch5.xhtml#p137), [161](#ch6.xhtml#p161), [171](#ch6.xhtml#p171), [172](#ch6.xhtml#p172)
    *   spatial attention, [171](#ch6.xhtml#p171), [172](#ch6.xhtml#p172)
    *   spatiotemporal attention, [171](#ch6.xhtml#p171)
    *   temporal attention, [171](#ch6.xhtml#p171), [172](#ch6.xhtml#p172)
*   attention flow, [210](#ch7.xhtml#p210)
*   attention rollout, [209](#ch7.xhtml#p209)
*   automatic speech recognition, [164](#ch6.xhtml#p164), [180](#ch6.xhtml#p180)
*   autoregressive, [158](#ch6.xhtml#p158)

*   Benchmarks, [80](#ch4.xhtml#p80), [91](#ch4.xhtml#p91), [92](#ch4.xhtml#p92)
*   BERT, [43](#ch3.xhtml#p43), [51](#ch3.xhtml#p51), [145](#ch5.xhtml#p145)
*   BERTology, [52](#ch3.xhtml#p52)
*   BERTopic, [50](#ch3.xhtml#p50)

*   clustering, [140](#ch5.xhtml#p140), [166](#ch6.xhtml#p166) 
    *   k-means, [166](#ch6.xhtml#p166)
*   compression, [109](#ch5.xhtml#p109) 
    *   pooling, [109](#ch5.xhtml#p109), [111](#ch5.xhtml#p111)
    *   product quantization, [166](#ch6.xhtml#p166)
*   Cross-lingual, [71](#ch4.xhtml#p71), [75](#ch4.xhtml#p75), [80](#ch4.xhtml#p80), [91](#ch4.xhtml#p91), [93](#ch4.xhtml#p93), [94](#ch4.xhtml#p94), [96](#ch4.xhtml#p96), [97](#ch4.xhtml#p97)

*   encoder-decoder, [11](#ch2.xhtml#p11), [157](#ch6.xhtml#p157)
*   ERNIE-M, [82](#ch4.xhtml#p82), [84](#ch4.xhtml#p84)
*   explainability, [153](#ch5.xhtml#p153), [190](#ch7.xhtml#p190)

*   fairness, [190](#ch7.xhtml#p190)
*   feature importance, [202](#ch7.xhtml#p202)
*   few-shot learning, [162](#ch6.xhtml#p162), [163](#ch6.xhtml#p163)

*   graph embeddings 
    *   edge embeddings, [174](#ch6.xhtml#p174), [175](#ch6.xhtml#p175)
    *   node embeddings, [174](#ch6.xhtml#p174), [175](#ch6.xhtml#p175)

*   HITCL, [84](#ch4.xhtml#p84)

*   image recognition, [120](#ch5.xhtml#p120), [130](#ch5.xhtml#p130), [163](#ch6.xhtml#p163)
*   in-context learning, [162](#ch6.xhtml#p162)
*   INFOXLM, [80](#ch4.xhtml#p80), [94](#ch4.xhtml#p94)
*   integrated gradients, [193](#ch7.xhtml#p193)

*   LaBSE, [85](#ch4.xhtml#p85), [87](#ch4.xhtml#p87)
*   language model 
    *   domain-specific, [155](#ch6.xhtml#p155), [156](#ch6.xhtml#p156)
    *   masked language model, [145](#ch5.xhtml#p145), [167](#ch6.xhtml#p167)
*   layer-wise Relevance Propagation (LRP), [192](#ch7.xhtml#p192)
*   LIME, [196](#ch7.xhtml#p196)
*   local approximation explainability, [195](#ch7.xhtml#p195)
*   locality-sensitive hashing, [126](#ch5.xhtml#p126), [127](#ch5.xhtml#p127), [129](#ch5.xhtml#p129), [140](#ch5.xhtml#p140)

*   machine translation, [27](#ch2.xhtml#p27), [113](#ch5.xhtml#p113)
*   mBERT, [72](#ch4.xhtml#p72), [74](#ch4.xhtml#p74)
*   model debugging, [189](#ch7.xhtml#p189)
*   model distillation, [195](#ch7.xhtml#p195)
*   Multilingual 
    *   ALM, [77](#ch4.xhtml#p77)
    *   AMBER, [81](#ch4.xhtml#p81)
    *   ERNIE-M, [82](#ch4.xhtml#p82)
    *   HICTL, [84](#ch4.xhtml#p84)
    *   INFOXLM, [80](#ch4.xhtml#p80), [94](#ch4.xhtml#p94)
    *   LaBSE, [85](#ch4.xhtml#p85), [87](#ch4.xhtml#p87)
    *   mBERT, [74](#ch4.xhtml#p74)
    *   mUSE, [87](#ch4.xhtml#p87)
    *   Pre-training, [90](#ch4.xhtml#p90), [94](#ch4.xhtml#p94)
    *   Unicoder, [78](#ch4.xhtml#p78)
    *   XLM, [75](#ch4.xhtml#p75)
    *   XLM-R, [77](#ch4.xhtml#p77)
*   mUSE, [87](#ch4.xhtml#p87), [97](#ch4.xhtml#p97)

*   named entity recognition, [156](#ch6.xhtml#p156)
*   natural language understanding, [159](#ch6.xhtml#p159)

*   one-shot learning, [162](#ch6.xhtml#p162), [163](#ch6.xhtml#p163)

*   perplexity, [34](#ch2.xhtml#p34)
*   perturbation-based explainability, [194](#ch7.xhtml#p194)
*   pooling, [109](#ch5.xhtml#p109), [110](#ch5.xhtml#p110)
*   positional encoding, [170](#ch6.xhtml#p170)
*   positional encodings, [21](#ch2.xhtml#p21), [118](#ch5.xhtml#p118), [142](#ch5.xhtml#p142), [160](#ch6.xhtml#p160), [163](#ch6.xhtml#p163), [164](#ch6.xhtml#p164), [167](#ch6.xhtml#p167) 
    *   absolute positional encodings, [119](#ch5.xhtml#p119)
    *   Laplacian positional encodings, [173](#ch6.xhtml#p173)
    *   positional encodings, [173](#ch6.xhtml#p173)
    *   relative positional encodings, [119](#ch5.xhtml#p119)
    *   sinusoidal relative positional encodings, [119](#ch5.xhtml#p119)
*   Pre-training, [45](#ch3.xhtml#p45), [46](#ch3.xhtml#p46), [76](#ch4.xhtml#p76), [78](#ch4.xhtml#p78), [82](#ch4.xhtml#p82), [90](#ch4.xhtml#p90), [94](#ch4.xhtml#p94)
*   probing, [198](#ch7.xhtml#p198)

*   Question Answering, [46](#ch3.xhtml#p46), [75](#ch4.xhtml#p75), [92](#ch4.xhtml#p92)
*   question answering, [156](#ch6.xhtml#p156), [158](#ch6.xhtml#p158), [159](#ch6.xhtml#p159), [162](#ch6.xhtml#p162), [168](#ch6.xhtml#p168)
*   reinforcement learning, [177](#ch6.xhtml#p177)
*   relationship extraction, [156](#ch6.xhtml#p156)
*   residual connection, [110](#ch5.xhtml#p110), [112](#ch5.xhtml#p112)–[114](#ch5.xhtml#p112), [161](#ch6.xhtml#p161), [164](#ch6.xhtml#p164) 
    *   reversible residual layer, [130](#ch5.xhtml#p130)
*   RoBERTa, [48](#ch3.xhtml#p48)

*   saliency, [190](#ch7.xhtml#p190)
*   score function, [16](#ch2.xhtml#p16) 
    *   additive, [18](#ch2.xhtml#p18)
    *   dot product, [17](#ch2.xhtml#p17)
    *   scaled dot product, [17](#ch2.xhtml#p17), [127](#ch5.xhtml#p127), [171](#ch6.xhtml#p171)
*   Semantic Retrieval, [92](#ch4.xhtml#p92)
*   sequence-to-sequence, [12](#ch2.xhtml#p12)
*   Shapley values, [196](#ch7.xhtml#p196)
*   special token, [135](#ch5.xhtml#p135) 
    *   \[CLS\], [135](#ch5.xhtml#p135)
    *   \[MASK\], [145](#ch5.xhtml#p145)
*   Structure Prediction, [92](#ch4.xhtml#p92)

*   TaBERT, [49](#ch3.xhtml#p49)
*   traits of explainable system, [187](#ch7.xhtml#p187) 
    *   confidence, [188](#ch7.xhtml#p188)
    *   ethics, [188](#ch7.xhtml#p188)
    *   safety, [188](#ch7.xhtml#p188)
    *   trust, [188](#ch7.xhtml#p188)
*   transformer, [19](#ch2.xhtml#p19), [109](#ch5.xhtml#p109) 
    *   hierarchical transformer, [120](#ch5.xhtml#p120)
    *   multilingual, language model multilingual, [157](#ch6.xhtml#p157)
    *   reinforcement learning, [178](#ch6.xhtml#p178)

*   Unicoder, [78](#ch4.xhtml#p78), [80](#ch4.xhtml#p80)
*   unsupervised learning, [158](#ch6.xhtml#p158), [159](#ch6.xhtml#p159)

*   video classification, [169](#ch6.xhtml#p169)
*   visualization methods, [150](#ch5.xhtml#p150), [190](#ch7.xhtml#p190)

*   XLM, [75](#ch4.xhtml#p75)
*   XLM-R, [77](#ch4.xhtml#p77)

*   Zero-shot, [87](#ch4.xhtml#p87), [93](#ch4.xhtml#p93), [97](#ch4.xhtml#p97)
*   zero-shot learning, [162](#ch6.xhtml#p162), [163](#ch6.xhtml#p163)