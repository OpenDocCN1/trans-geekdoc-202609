![image](images/Cover.jpg)

IET COMPUTING SERIES 39

ReRAM-based Machine Learning

Other volumes in this series:

| Volume 1 || **Knowledge Discovery and Data Mining** M.A. Bramer (Editor) |
| --- | --- |
| Volume 3 || **Troubled IT Projects: Prevention and turnaround** J.M. Smith |
| Volume 4 || **UML for Systems Engineering: Watching the wheels, 2nd Edition** J. Holt |
| Volume 5 || **Intelligent Distributed Video Surveillance Systems** S.A. Velastin and P. Remagnino (Editors) |
| Volume 6 || **Trusted Computing** C. Mitchell (Editor) |
| Volume 7 || **SysML for Systems Engineering** J. Holt and S. Perry |
| Volume 8 || **Modelling Enterprise Architectures** J. Holt and S. Perry |
| Volume 9 || **Model-based Requirements Engineering** J. Holt, S. Perry and M. Bownsword |
| Volume 13 || **Trusted Platform Modules: Why, when and how to use them** Ariel Segall |
| Volume 14 || **Foundations for Model-based Systems Engineering: From patterns to models** J. Holt, S. Perry and M. Bownsword |
| Volume 15 || **Big Data and Software Defined Networks** J. Taheri (Editor) |
| Volume 18 || **Modeling and Simulation of Complex Communication** M.A. Niazi (Editor) |
| Volume 20 || **SysML for Systems Engineering: A Model-based approach, 3rd Edition** J. Holt and S. Perry |
| Volume 23 || **Data as Infrastructure for Smart Cities** L. Suzuki and A. Finkelstein |
| Volume 24 || **Ultrascale Computing Systems** J. Carretero, E. Jeannot and A. Zomaya |
| Volume 25 || **Big Data-enabled Internet of Things** M. Khan, S. Khan and A. Zomaya (Editors) |
| Volume 26 || **Handbook of Mathematical Models for Languages and Computation** A. Meduna, P. Horáček and M. Tomko |
| Volume 29 || **Blockchains for Network Security: Principles, technologies and applications** H. Huang, L. Wang, Y. Wu and K.R. Choo (Editors) |
| Volume 32 || **Network Classification for Traffic Management: Anomaly detection, feature selection, clustering and classification** Zahir Tari, Adil Fahad, Abdulmohsen Almalawi and Xun Yi |
| Volume 33 || **Edge Computing: Models, technologies and applications** J. Taheri and S. Deng (Editors) |
| Volume 34 || **AI for Emerging Verticals: Human-robot computing, sensing and networking** M.Z. Shakir and N. Ramzan (Editors) |
| Volume 35 || **Big Data Recommender Systems Volumes 1 and 2** Osman Khalid, Samee U. Khan and Albert Y. Zomaya (Editors) |
| Volume 40 || **E-learning Methodologies: Fundamentals, technologies and applications** M. Goyal, R. Krishnamurthi and D. Yadav (Editors) |

# ReRAM-based Machine Learning

Edited by  
Hao Yu, Leibin Ni and Sai Manoj Pudukotai Dinakarrao

The Institution of Engineering and Technology

Published by The Institution of Engineering and Technology, London, United Kingdom

The Institution of Engineering and Technology is registered as a Charity in England & Wales (no. 211014) and Scotland (no. SC038698).

© The Institution of Engineering and Technology 2021

First published 2021

This publication is copyright under the Berne Convention and the Universal Copyright Convention. All rights reserved. Apart from any fair dealing for the purposes of research or private study, or criticism or review, as permitted under the Copyright, Designs and Patents Act 1988, this publication may be reproduced, stored or transmitted, in any form or by any means, only with the prior permission in writing of the publishers, or in the case of reprographic reproduction in accordance with the terms of licences issued by the Copyright Licensing Agency. Enquiries concerning reproduction outside those terms should be sent to the publisher at the undermentioned address:

The Institution of Engineering and Technology  
Michael Faraday House  
Six Hills Way, Stevenage  
Herts, SG1 2AY, United Kingdom

[www.theiet.org](http://www.theiet.org)

While the authors and publisher believe that the information and guidance given in this work are correct, all parties must rely upon their own skill and judgement when making use of them. Neither the authors nor publisher assumes any liability to anyone for any loss or damage caused by any error or omission in the work, whether such an error or omission is the result of negligence or any other cause. Any and all such liability is disclaimed.

The moral rights of the authors to be identified as authors of this work have been asserted by them in accordance with the Copyright, Designs and Patents Act 1988.

 

**British Library Cataloguing in Publication Data**  
A catalogue record for this product is available from the British Library

 

**ISBN 978-1-83953-081-4 (hardback)**  
**ISBN 978-1-83953-082-1 (PDF)**

 

Typeset in India by MPS Limited  
Printed in the UK by CPI Group (UK) Ltd, Croydon

## **Contents**

[Acronyms](#acronyms.html#ST2)

[Preface](#preface.html#ST3)

[About the authors](#authors.html#ST4)

[Part I Introduction](#PartI.html#p01)

[1 Introduction](#Chapter1.html#c01)

[1.1 Introduction](#Chapter1.html#ST7)

[1.1.1 Memory wall and powerwall](#Chapter1.html#ST8)

[1.1.2 Semiconductor memory](#Chapter1.html#ST9)

[1.1.3 Nonvolatile IMC architecture](#Chapter1.html#ST15)

[1.2 Challenges and contributions](#Chapter1.html#ST16)

[1.3 Book organization](#Chapter1.html#ST17)

[2 The need of in-memory computing](#Chapter2.html#c02)

[2.1 Introduction](#Chapter2.html#ST19)

[2.2 Neuromorphic computing devices](#Chapter2.html#ST20)

[2.2.1 Resistive random-access memory](#Chapter2.html#ST21)

[2.2.2 Spin-transfer-torque magnetic random-access memory](#Chapter2.html#ST22)

[2.2.3 Phase change memory](#Chapter2.html#ST23)

[2.3 Characteristics of NVM devices for neuromorphic computing](#Chapter2.html#ST24)

[2.4 IMC architectures for machine learning](#Chapter2.html#ST25)

[2.4.1 Operating principles of IMC architectures](#Chapter2.html#ST26)

[2.4.2 Analog and digitized fashion of IMC](#Chapter2.html#ST29)

[2.4.3 Analog IMC](#Chapter2.html#ST30)

[2.4.4 Digitized IMC](#Chapter2.html#ST37)

[2.4.5 Literature review of IMC](#Chapter2.html#ST38)

[2.5 Analysis of IMC architectures](#Chapter2.html#ST45)

[3 The background of ReRAM devices](#Chapter3.html#c03)

[3.1 ReRAM device and SPICE model](#Chapter3.html#ST47)

[3.1.1 Drift-type ReRAM device](#Chapter3.html#ST48)

[3.1.2 Diffusive-type ReRAM device](#Chapter3.html#ST49)

[3.2 ReRAM-crossbar structure](#Chapter3.html#ST50)

[3.2.1 Analog and digitized ReRAM crossbar](#Chapter3.html#ST51)

[3.2.2 Connection of ReRAM crossbar](#Chapter3.html#ST54)

[3.3 ReRAM-based oscillator](#Chapter3.html#ST58)

[3.4 Write-in scheme for multibit ReRAM storage](#Chapter3.html#ST59)

[3.4.1 ReRAM data storage](#Chapter3.html#ST60)

[3.4.2 Multi-threshold resistance for data storage](#Chapter3.html#ST61)

[3.4.3 Write and read](#Chapter3.html#ST62)

[3.4.4 Validation](#Chapter3.html#ST65)

[3.4.5 Encoding and 3-bit storage](#Chapter3.html#ST66)

[3.5 Logic functional units with ReRAM](#Chapter3.html#ST70)

[3.5.1 OR gate](#Chapter3.html#ST71)

[3.5.2 AND gate](#Chapter3.html#ST72)

[3.6 ReRAM for logic operations](#Chapter3.html#ST73)

[3.6.1 Simulation settings](#Chapter3.html#ST74)

[3.6.2 ReRAM-based circuits](#Chapter3.html#ST75)

[3.6.3 ReRAM as a computational unit-cum-memory](#Chapter3.html#ST78)

[Part II Machine learning accelerators](#PartII.html#p02)

[4 The background of machine learning algorithms](#Chapter4.html#c04)

[4.1 SVM-based machine learning](#Chapter4.html#ST81)

[4.2 Single-layer feedforward neural network-based machine learning](#Chapter4.html#ST82)

[4.2.1 Single-layer feedforward network](#Chapter4.html#ST83)

[4.2.2 L2-norm-gradient-based learning](#Chapter4.html#ST87)

[4.3 DCNN-based machine learning](#Chapter4.html#ST90)

[4.3.1 Deep learning for multilayer neural network](#Chapter4.html#ST91)

[4.3.2 Convolutional neural network](#Chapter4.html#ST92)

[4.3.3 Binary convolutional neural network](#Chapter4.html#ST93)

[4.4 TNN-based machine learning](#Chapter4.html#ST98)

[4.4.1 Tensor-train decomposition and compression](#Chapter4.html#ST99)

[4.4.2 Tensor-train-based neural network](#Chapter4.html#ST100)

[4.4.3 Training TNN](#Chapter4.html#ST101)

[5 XIMA: the in-ReRAM machine learning architecture](#Chapter5.html#c05)

[5.1 ReRAM network-based ML operations](#Chapter5.html#ST103)

[5.1.1 ReRAM-crossbar network](#Chapter5.html#ST104)

[5.1.2 Coupled ReRAM oscillator network](#Chapter5.html#ST115)

[5.2 ReRAM network-based in-memory ML accelerator](#Chapter5.html#ST118)

[5.2.1 Distributed ReRAM-crossbar in-memory architecture](#Chapter5.html#ST119)

[5.2.2 3D XIMA](#Chapter5.html#ST122)

[6 The mapping of machine learning algorithms on XIMA](#Chapter6.html#c06)

[6.1 Machine learning algorithms on XIMA](#Chapter6.html#ST126)

[6.1.1 SLFN-based learning and inference acceleration](#Chapter6.html#ST127)

[6.1.2 BCNN-based inference acceleration on passive array](#Chapter6.html#ST132)

[6.1.3 BCNN-based inference acceleration on 1S1R array](#Chapter6.html#ST137)

[6.1.4 L2-norm gradient-based learning and inference acceleration](#Chapter6.html#ST140)

[6.1.5 Experimental evaluation of machine learning algorithms on XIMA architecture](#Chapter6.html#ST144)

[6.2 Machine learning algorithms on 3D XIMA](#Chapter6.html#ST161)

[6.2.1 On-chip design for SLFN](#Chapter6.html#ST162)

[6.2.2 On-chip design for TNNs](#Chapter6.html#ST166)

[6.2.3 Experimental evaluation of machine learning algorithms on 3D CMOS-ReRAM](#Chapter6.html#ST173)

[Part III Case studies](#PartIII.html#p03)

[7 Large-scale case study: accelerator for ResNet](#Chapter7.html#c07)

[7.1 Introduction](#Chapter7.html#ST185)

[7.2 Deep neural network with quantization](#Chapter7.html#ST186)

[7.2.1 Basics of ResNet](#Chapter7.html#ST187)

[7.2.2 Quantized convolution and residual block](#Chapter7.html#ST188)

[7.2.3 Quantized BN](#Chapter7.html#ST189)

[7.2.4 Quantized activation function and pooling](#Chapter7.html#ST190)

[7.2.5 Quantized deep neural network overview](#Chapter7.html#ST191)

[7.2.6 Training strategy](#Chapter7.html#ST192)

[7.3 Device for in-memory computing](#Chapter7.html#ST193)

[7.3.1 ReRAM crossbar](#Chapter7.html#ST194)

[7.3.2 Customized DAC and ADC circuits](#Chapter7.html#ST195)

[7.3.3 In-memory computing architecture](#Chapter7.html#ST196)

[7.4 Quantized ResNet on ReRAM crossbar](#Chapter7.html#ST197)

[7.4.1 Mapping strategy](#Chapter7.html#ST198)

[7.4.2 Overall architecture](#Chapter7.html#ST199)

[7.5 Experiment result](#Chapter7.html#ST200)

[7.5.1 Experiment settings](#Chapter7.html#ST201)

[7.5.2 Device simulations](#Chapter7.html#ST202)

[7.5.3 Accuracy analysis](#Chapter7.html#ST203)

[7.5.4 Performance analysis](#Chapter7.html#ST207)

[8 Large-scale case study: accelerator for compressive sensing](#Chapter8.html#c08)

[8.1 Introduction](#Chapter8.html#ST211)

[8.2 Background](#Chapter8.html#ST212)

[8.2.1 Compressive sensing and isometric distortion](#Chapter8.html#ST213)

[8.2.2 Optimized near-isometric embedding](#Chapter8.html#ST214)

[8.3 Boolean embedding for signal acquisition front end](#Chapter8.html#ST215)

[8.3.1 CMOS-based Boolean embedding circuit](#Chapter8.html#ST216)

[8.3.2 ReRAM crossbar-based Boolean embedding circuit](#Chapter8.html#ST217)

[8.3.3 Problem formulation](#Chapter8.html#ST218)

[8.4 IH algorithm](#Chapter8.html#ST219)

[8.4.1 Orthogonal rotation](#Chapter8.html#ST220)

[8.4.2 Quantization](#Chapter8.html#ST221)

[8.4.3 Overall optimization algorithm](#Chapter8.html#ST222)

[8.5 Row generation algorithm](#Chapter8.html#ST224)

[8.5.1 Elimination of norm equality constraint](#Chapter8.html#ST225)

[8.5.2 Convex relaxation of orthogonal constraint](#Chapter8.html#ST226)

[8.5.3 Overall optimization algorithm](#Chapter8.html#ST228)

[8.6 Numerical results](#Chapter8.html#ST229)

[8.6.1 Experiment setup](#Chapter8.html#ST230)

[8.6.2 IH algorithm on high-D ECG signals](#Chapter8.html#ST231)

[8.6.3 Row generation algorithm on low-D image patches](#Chapter8.html#ST234)

[8.6.4 Hardware performance evaluation](#Chapter8.html#ST238)

[9 Conclusions: wrap-up, open questions and challenges](#Chapter9.html#c09)

[9.1 Conclusion](#Chapter9.html#ST242)

[9.2 Future work](#Chapter9.html#ST243)

 

[References](#references.html#ref)

[Index](#index.html#ST244)

## **Acronyms**

 
| ANN || artificial neural network |
| --- | --- |
| BCNN || binary convolutional neural network |
| BNN || bitwise neural network |
| CNN || convolutional neural network |
| DNN || deep neural network |
| DRAM || dynamic random-access memory |
| FPGA || field programmable gate array |
| HDD || hard disk drive |
| IMC || in-memory computing |
| ML || machine learning |
| NDC || near-data computing |
| NVM || nonvolatile memory |
| ODD || optical disk drive |
| PCM || phase change memory |
| PIM || processing-in-memory |
| ReRAM || resistive random-access memory |
| ResNet || residual network |
| SLFN || single-layer feedforward neural network |
| SRAM || static random-access memory |
| STDP || spike timing-dependent plasticity |
| STT-MTJ || spin transfer torque magnetic tunnel junction |
| STT-RAM || spin transfer torque RAM |
| TNN || tensor neural network |
| TSV || through-silicon via |
| XIMA || crossbar in-memory architecture |
| 1S1R || one selector one ReRAM |
| 1T1R || one transistor one ReRAM |

## **Preface**

With the emergence of IoT and handheld devices, the amount of data procured in the data centers have reached nearly exa-scale. Processing such large amounts of data through traditional computing techniques is inefficient due to latency and inefficient resource usage. With the introduction in machine learning (ML) and success in multiple application, ML has been adopted for big data processing.

Despite advancements in terms of processing through ML, transferring and communicating the data to and from the memory and storage units is seen as one of the major bottlenecks. In-Memory Computing (IMC) is seen as a panacea to overcome the challenges of traditional Von-Neumann architectures. For efficient IMC, frameworks such as Hadoop and MapReduce frameworks have been introduced. Such frameworks explore the temporal locality to process such large amounts of data. Despite efficient compared to traditional computing paradigms, existing IMC paradigms are inefficient in terms of power consumption and latency requirements, especially when employed in data centers and other cloud computing platforms.

To address the challenges with CMOS-based IMC, emerging non-volatile memory (NVM) devices are researched in both academia and industry. Such NVM-based IMC architectures are observed to overcome the saturation of Moore’s law challenge because of its low power, area and high-density embedded storage benefits. Multiple devices emerging from different materials including resistive random-access memory (ReRAM), phase-change random access memory (PCRAM), magnetic RAM (MRAM), Ferroelectric RAM (FeRAM) and NOR Flash along with traditional DRAMs are introduced and researched. Among multiple emerging NVM devices, ReRAM is the most promising among multiple devices due to its potential of multi-bit storage and compatability with CMOS technology. Such exploration is well-supported by companies such as HP and IBM. Hence, we believe the ReRAM-based IMC will be commercialized with IoT products in the next few years.

This book first introduces existing architectures on IMC such as processing-in-memory (PIM), near-data processing (NDP) and near-data computation (NDC) architectures ranging from general programmable many-core systems to reconfigurable arrays and custom-designed accelerators. A comprehensive analysis on various IMC architectures is discussed and compared. Further, with the emergence of memory devices that support IMC, the authors introduce the ReRAM along with the device modeling and logic circuit design needed for ML operations. ReRAM has been widely deployed for IMC architectures due to minimized leakage power, reduced power consumption and smaller hardware footprint. The authors introduce the design of a crossbar structure with the aid of ReRAM to facilitate matrix multiplications and convolutions that are computationally intensive operations in ML applications. More importantly, they present a true in-memory logic-integration architecture without utilizing I/Os that leads to faster data access and higher throughput with low power. They also present multiple ReRAM-based IMC architectures that can perform other computations of ML and data-intensive applications such as calculation of gradients and L2-norms. Deep learning architectures are heavily growing in terms of depth and leading to an exponential increase in computational complexity. As a case study, the authors discuss how the ReRAM-based IMC can aid in accelerating computations, eventually leading to an increased throughput with high energy efficiency and smaller form factor for a large-scale deep learning network such as residual network (ResNet) and compressive sensing computations.

As the number of elements on a single chip or system are limited, to further enhance the throughputs of data-intensive computations, a distributed computing paradigm has been widely adopted. In this book, the authors introduce techniques to perform distributed computing using IMC accelerators. The emergence of 3D integration has facilitated multiple chips stacked on top of each other, with each chip functioning independently. The authors introduce a 3D CMOS-ReRAM architecture, where ReRAM devices are connected through through-silicon-vias (TSVs) with top-layer wordlines and bottom-layer bitlines. All other CMOS logics are implemented in the bottom layer. They also introduce a multilayer 3D architecture, where multiple ReRAM layers are designed as data buffers.

This book introduces the design of hardware for ML and data-intensive computations. It has been shown by the research community that the mapping of computations is a critical aspect without which the benefits of IMC or hardware accelerator designs cannot be yielded. Thus, to make the design complete, the authors introduce strategies to map ML designs onto hardware accelerators. They also provide data analytics mapping on ReRAM-based IMC architecture for multiple data-intensive applications. The learning and inference procedures of single-layer feedforward neural network (SLFN) have been optimized and partially mapped on a passive binary ReRAM crossbar. In addition, the authors map a binary convolutional neural network (BCNN) on both passive array and One Selector One ReRAM array with different mapping schemes. In addition to traditional 2D integration, this book also introduces how mapping can efficiently be performed for emerging 3D integration-based IMC architectures.

This book is highly motivated by the rapid advancements observed in the ML and hardware design communities, and the lack of a book that provides insights and latest advancements in both these fields, as well as the wide adoption of ML algorithms in a plethora of applications and ever-increasing industrial requirements for enhancing the performance of ML applications. This book can serve as a bridge between researchers in the computing domain (algorithm designers for ML) and hardware designers.

The first chapter introduces the need and motivation to deploy ML algorithms for data-intensive computations. This also introduces the challenges and need for hardware for ML processing. In the second chapter, we present emerging memory devices that can support IMC and the need for IMC is introduced in this chapter. Further, a comprehensive comparison and analysis of different IMC architectures is presented. The architectures include using traditional DRAM to emerging devices such as ReRAM and memristors. In the third chapter, modeling of ReRAM devices is presented followed by the design of crossbar structures that are primarily used for matrix multiplication in ML applications. In addition, design of multibit storage for ReRAMs and other logic functional units with ReRAMs is presented.

The fourth chapter provides the basic information on ML algorithms, computational complexity and the types of operations involved in the ML algorithms, including least-squares method (SVM, ELM), and deep learning (CNN, TNN). Trained quantization (binary, ternary and eight-bit, etc.) will be addressed in this chapter. Additionally, the training mechanisms for deep CNNs and TNNs are focused in this chapter, as they are the time-consuming operations and the performance depends on the training efficiency.

The fifth chapter introduces multiple strategies to map the ML designs on to hardware accelerators. Designing of ReRAM crossbar-based IMC architectures to accelerate ML applications is presented. Further, to accommodate deep DNNs and CNNs, a 3D stacking-based CMOS-ReRAM architecture is introduced. The main focus of this chapter is on the architectural aspects and circuity to support the data-intensive computations with high speed. In Chapter 6, we introduce techniques to map the ML applications for ReRAM and the major challenges and the scope for improvement. The mapping techniques for different ML algorithms for different architectures such as ReRAM cross with traditional 2D and 3D architectures are illustrated.

Case studies for ReRAM-based ML acceleration for different scenarios are presented. Chapter 7 presents ResNet under different scenarios such as DNN with quantization and ReRAM-based acceleration for ResNet. In addition to the ResNet, this book presents ReRAM-based accelerator for compressive sensing application in Chapter 8. For this part, different scenarios such as iterative heuristic algorithm and row generation algorithms are presented. All the case study chapters are presented with substantial amount of experimental results and analysis that aid in replicating the experiments and also prove the efficiency of ReRAM accelerators and its prominence in the design of future hardware accelerators. The last chapter summarizes the ReRAM accelerators and its impact on the ML applications. Furthermore, future directions with ReRAM devices to further enhance the ML computations are presented.

The authors of this book would like to thank the colleagues at Nanyang Technological University, especially members of VIRTUS lab, Hardware architecture and artificial intelligence lab at George Mason University and the affiliated students. We would like also to express my deepest appreciation to the faculty members, Prof. Anupam Chattopadhyay, Prof. Chang Chip Hong, Prof. Shi Guoyong, Prof. Huang Guangbin of Nanyang Technological University and Prof. J. Joshua Yang and Prof. Qiangfei Xia of the University of Massachusetts Amherst for their support. The authors also would like to thank Prof. Amlan Ganguly and Mr. Purab Sutradhar of Rochester Institute of Technology. The authors would also like to thank Dr. Nima Taherinejad and Prof. Axel Jantsch from Vienna University of Technology (TU Wien), Austria.

## **About the authors**

**Hao Yu** is a professor in the School of Microelectronics at Southern University of Science and Technology (SUSTech), China. His main research interests cover energy-efficient IC chip design and mmwave IC design. He is a senior member of IEEE and a member of ACM. He has written several books and holds 20 granted patents. He is a distinguished lecturer of IEEE Circuits and Systems and associate editor of *Elsevier Integration, the VLSI Journal, Elsevier Microelectronics Journal, Nature Scientific Reports, ACM Transactions on Embedded Computing Systems* and *IEEE Transactions on Biomedical Circuits and Systems*. He is also a technical program committee member of several IC conferences, including IEEE CICC, BioCAS, A-SSCC, ACM DAC, DATE and ICCAD. He obtained his Ph.D. degree from the EE department at UCLA, USA.

**Leibin Ni** is a Principle engineer at Huawei Technologies, Shenzhen, China. His research interests include emerging nonvolatile memory platforms, computing in-memory architecture, machine learning applications and low power designs. He is a member of IEEE. He received his Ph.D. from the Nanyang Technological University, Singapore.

**Sai Manoj Pudukotai Dinakarrao** is an assistant professor in the Department of Electrical and Computer Engineering at George Mason University (GMU), USA. His current research interests include hardware security, adversarial machine learning, Internet of things networks, deep learning in resource-constrained environments, in-memory computing, accelerator design, algorithms, design of self-aware many-core microprocessors and resource management in many-core microprocessors. He is a member of IEEE and ACM. He served as a guest editor to *IEEE Design and Test Magazine* and reviewer for multiple IEEE and ACM journals. Also, he is a technical program committee member of several CAD conferences, including ACM DAC, DATE, ICCAD, ASP-DAC, ESWEEK and many more. He received a Ph.D. degree in Electrical and Electronic Engineering from the Nanyang Technological University, Singapore.

### *Part I*  
**Introduction**

## *Chapter 1*  
**Introduction**

### **1.1 Introduction**

In the last two decades, computing paradigms have experienced a tremendous drift with nearly exascale (![image](images/ch01_stripin_si1.gif)bytes) amount of data being amassed by business units and organizations. The requirements to analyze and respond to such large amounts of data have led to the adoption of machine learning (ML) methods in a wide range of applications ranging from autonomous driving to smart homes.

One of the major challenges to process such large amounts of data is the fetching of data from the memory and writing it back without experiencing the well-known memory-wall bottleneck. To address such concerns, in-memory computing (IMC) and supporting frameworks such as Hadoop and MapReduce have been introduced. This has shown to be highly beneficial as these methods address the challenge of a lack of temporal locality that exists in traditional computing techniques. Undoubtedly, these techniques have helped but the challenges of power consumption and processing delays are still unsolved concerns, especially in macro systems and data centers.

Computing-in-memory methods based on emerging nonvolatile devices are popular in both academia and industry. Many researchers believe that this architecture will be an opportunity to break Moore's law because of its ultra-low power and high-density embedded storage. Various devices including resistive random-access memory (ReRAM), phase-change random-access memory (PCRAM), Magentic RAM (MRAM), Ferroelectric RAM (FeRAM) and NOR Flash have been discussed. ReRAM is the most promising among all these devices due to its potentiality for multilevel resistance and compatibility with CMOS technology. Well-known companies such as IBM and HP have invested in this field, and we believe that this ReRAM-based IMC will be commercialized with Internet-of-things (IoT) products in the next 2–3 years. This chapter introduces the need and motivation to deploy ML algorithms for data-intensive computations.

#### 1.1.1 Memory wall and powerwall

Information technology by new social media such as Google and Facebook is generating a wealth of data at exa-level that is previously unimaginable. For instance, WalMart processes one million transactions per hour, and from these transactions, they collect 2.5 petabytes of information \[1\], and Facebook users upload 100 terabytes of data and one billion pieces of content every day \[2\]. In-depth data analytics may become the driving force for the future economic growth in a digital data-oriented society. The main challenge stems from the existing hardware infrastructure built upon the conventional computer architecture and CMOS technology. Moore's law scaling has become slower when compared to the growth of data. There are many recent large-scale research programs such as exascale computing (NSF/DARPA-USA) and Human Brain (European Commission), which are, however, still limited at this singularity point because of the memory bottleneck.

To process and gain insights from such massive collected data, parallel and scalable ML-based solutions that can scale with data are needed. In response, several scalable ML algorithms along with parallel frameworks have emerged: Hadoop \[3\], Spark \[4\], Flink \[5,6\], Tez \[7\], Google Dataflow \[8\], 0xdata H2O \[9\] and Petuum \[10\]. Undoubtedly, these frameworks pushed the processing capabilities beyond traditional approaches, but executing these emerging analytic solutions requires a significant amount of computational resources such as power and appropriate processing architectures. Thus, the data centers started to expand by equipping more computational nodes to satisfy the demands of increasing volumes of data \[11–14\] and the complexity of ML algorithms. While demand for ML-based computational resources continues to grow with the size of data, the semiconductor industry has reached the scaling limits and is no longer able to reduce power consumption in new chips. Current server designs, based on commodity homogeneous processors, ceased to be efficient in terms of performance/watt to process such ML-based data-intensive computations \[15–22\].

During big-data analytics, the computing systems in data centers or nodes need to process the stored data with intensive memory accesses. Memory access is seen as one of the pivotal obstacles that limit the performance and throughput of the current architectures and data centers. Intensive memory access is seen across the emerging applications including web searching, data mining and also ML applications. The microprocessor needs to process the stored data with the intensive memory access. However, the state-of-the-art data storage and processing hardware still have a bandwidth-wall problem with large I/O congestion, but also powerwall with large static power in advanced CMOS technology. As a result, a design of scalable energy-efficient big-data analytic hardware is highly required. The following research activities \[23,24\] attempted to alleviate the memory bottleneck problem for big-data storage and processing in the future:

*   First, as a promising technology for big-data-oriented computing, the emerging nonvolatile IMC shows a great potential as a high-throughput, energy-efficient solution. The application-specific accelerators can be developed within memory. In this case, before readout by processing unit, data can be preprocessed so that data migration is minimized and the bandwidth wall can be relieved. Moreover, the nonvolatile memory (NVM) devices hold information without using charge such that the leakage current can be significantly reduced with the powerwall relieved as well.
*   Second, sparse-represented data by compressive sensing is an effective approach to reduce data size by projecting data from high-dimensional space to low-dimensional subspace with essential feature preserved. Data stored in the memory after compressive sensing can be recovered or directly processed. This procedure reduces data complexity in data storage as well as in data analytics with a further significant power reduction and bandwidth improvement.
*   Third, data analytics by ML accelerator can be developed for fast data analytics. Latest ML algorithm on-chip can accelerate the learning process with a potential to realize online training for efficient inference, which is important for applications in autonomous vehicles and unmanned aerial vehicles.

#### 1.1.2 Semiconductor memory

As seen in the previous section, having a memory element close to the processing units can aid plethora of challenges. There exist numerous kinds of memory which are different in terms of their functionality, physical characteristics as well as the benefits they provide. We first review the memory utilized in computer architecture, which will lay basis for the architectural design described in the later chapters.

##### 1.1.2.1 Memory technologies

Traditional semiconductor memories refer to the silicon-based transistor devices (CMOS, BTJ, FINFET and so on) in computer architectures. These memories are applied to store computation instructions as well as data temporarily or permanently. Compared to storage media such as hard disk drive (HDD) and optical disk drive (ODD) with predetermined order of data access due to the limitations of mechanical drive, the semiconductor memories possess the property of random access. It takes almost an identical time to access any data regardless of the data location.

One can further classify all the semiconductor memories into two classes: volatile memory and NVM. In volatile memory, data are stored as electrical signals such as voltage, and it requires uninterrupted power supply. Once the power supply stops, the device is turned off and data are lost. Currently, the most commonly used volatile memories are static random-access memory (SRAM) \[25–27\] and dynamic random-access memory (DRAM), whose data are indicated by the electrical voltage levels. On the contrary, NVM is able to retain the data even when the device is turned off, as its data are mostly preserved by nonelectrical states. For instance, bits in programmable read-only memory (PROM) are denoted by whether the fuses of individual memory cells are burned. [Figure 1.1](#Chapter1.html#c01_fig1) briefly introduces the characteristics of the volatile SRAM/DRAM, traditional nonvolatile memories (NVMs) and also emerging NVMs. The memory elements are arranged in terms of the size and access time (the left most elements are present in small quantity/size, but have faster access to the processor, whereas towards the right the elements are in large quantity and have large access time). Three prominent memory technologies are the SRAM, DRAM and flash memory, whose details are presented in the following.

![image](images/PBPC0390-01-f01.jpg)

Figure 1.1 Hierarchy of different memories in a computer architecture

###### Static random-access memory

A typical CMOS-SRAM cell consists six transistors, shown in [Figure 1.2](#Chapter1.html#c01_fig2). The flip-flop formed by M1 to M4 holds the stored bit. The term *static* is derived from the fact that the cell does not need to be refreshed like dynamic RAM, and the data can be retained as long as the power is supplied. The M5 and M6, connected with WL and two bitlines (BLs), are used as access transistors to select target cells.

![image](images/PBPC0390-01-f02.jpg)

Figure 1.2 A 6T SRAM cell structure with leakage paths in standby state. The BLs are precharged high and assume the stored data is “1” at ![image](images/ch01_stripin_si2.gif)

There are three operation states for an SRAM cell, write, read and stand by. To a write operation, the value to be written needs to be applied on both BLs, namely BL and ![image](images/ch01_stripin_si3.gif), in a complementary manner. Assume we wish to write “0” to the cell, i.e., ![image](images/ch01_stripin_si4.gif)to be “0” and ![image](images/ch01_stripin_si5.gif)to be “1,” the BL is driven low and ![image](images/ch01_stripin_si6.gif)high. Once the M5 and M6 are turned on by setting WL “1,” the BL drivers will override the previous stored value. In order to easily override the previous state in the self-reinforced flip-flop, the BL drivers are required to be designed stronger than the transistors in flip-flop.

For a read operation, both BLs are precharged high before the start of the read cycle, and the turning on of the wordline (WL) signifies the start of read operation. Because of the opposite voltages at ![image](images/ch01_stripin_si7.gif)and ![image](images/ch01_stripin_si8.gif), one of the BLs will be pulled down by the cell, and the discharging of one of the BLs is then detected by the BL sense amplifier. In voltage mode sensing scheme, the sign of BL voltage difference ![image](images/ch01_stripin_si9.gif)(![image](images/ch01_stripin_si10.gif)minus ![image](images/ch01_stripin_si11.gif)) determines the value of stored bit. A ![image](images/ch01_stripin_si12.gif)in tens of millivolts is significant enough to efficiently distinguish which BL is being discharged. For example, assume the stored bit is “1” at ![image](images/ch01_stripin_si13.gif)and “0” at ![image](images/ch01_stripin_si14.gif), and once the *WL* is asserted, the ![image](images/ch01_stripin_si16.gif)will discharge towards “0”; when a positive ![image](images/ch01_stripin_si17.gif)of tens of millivolts is gained, the latch-based sense amplifier will amplify the small voltage difference with positive feedback, and finally output logic “1” as result.

When the WL is connected to ground, turning off the two access transistors, the cell is in the standby state. During the standby state, the two cross-coupled inverters will reinforce each other due to the positive feedback, the value is preserved as long as the power is supplied. One prominent problem regarding SRAM in standby state is severe subthreshold leakage. Subthreshold leakage is the drain-source current of a transistor when the gate-source voltage is less than the threshold voltage. The subthreshold current depends exponentially on threshold voltage, which results in large subthreshold current in deep sub-micron regime. [Figure 1.2](#Chapter1.html#c01_fig2) shows three leakage paths in one SRAM cell, assuming the stored bit is “1” at Q. Note that the *BL* and ![image](images/ch01_stripin_si20.gif)are always precharged to ![image](images/ch01_stripin_si21.gif)to facilitate future read operation. Regardless of the stored value, there always will be three transistors consuming leakage power.

Compared to other memory technologies, SRAM is able to provide the fastest access speed, but the advantage comes as a trade-off against density and power. As one SRAM cell requires silicon area for six transistors, SRAM has very limited density and hence is more expensive than other memory technologies. In addition, it is very power consuming due to the leakage problem at standby state. Therefore, SRAM serves best in the applications where high performance is the main concern and the capacity is not significant, namely the caches for processors.

###### Dynamic random-access memory

The philosophy behind DRAM is simplicity. Unlike SRAM, where one cell is composed of six transistors, each individual DRAM cell consists only one capacitor and one access transistor. The data “0” or “1” is represented by whether the capacitor is fully charged or discharged. However, the electrical charge on the capacitor will gradually leak away, and after a period, the voltage on the capacitor is so low for the sense amplifier to differentiate between “1” and “0”. Therefore, unlike SRAM that the data can be retained as long as the power is supplied, the retention time for DRAM is finite and all DRAM cells need to be read out and written back periodically to ensure data integrity. Typically, the cells are refreshed once every 32 or 64 ms. This process is known as *refresh* , and this is how the name of dynamic RAM is derived. [Figure 1.3](#Chapter1.html#c01_fig3) shows the circuit diagram of such 1T1C structure DRAM cell.

![image](images/PBPC0390-01-f03.jpg)

Figure 1.3 The circuit diagram of 1T1C DRAM cell structure

To write a DRAM cell, the BL is first set high or low based on the value to write. After the access transistor is turned on by asserting WL, the capacitor in the selected cell is charged to “1” or discharged to “0.” Because the access takes place through an NMOS transistor, there exists a ![image](images/ch01_stripin_si22.gif)drop during the write “1.” In order to prevent this ![image](images/ch01_stripin_si23.gif)drop and maintain a long refresh period, the WLs driving voltage is usually boosted to ![image](images/ch01_stripin_si24.gif).

To read a DRAM cell, the BL is precharged to ![image](images/ch01_stripin_si25.gif)and then the WL is enabled. Due to the charge sharing, the BL voltage will slightly decrease or increase depending on the voltage that the capacitor was previously charged to, i.e., ![image](images/ch01_stripin_si26.gif)or ![image](images/ch01_stripin_si27.gif). If it is previously charged, the charge sharing will slightly boost the BL voltage; otherwise, some charge will be distributed from BL to cell capacitor. In both cases, the voltage of storage capacitor will be changed after read operation; thus, the read operation is called destructive, and an instant write back is required. A slight voltage change on the BL can be calculated by

![image](images/ch01_stripin_si35.gif)

The sign of ![image](images/ch01_stripin_si28.gif)depends on the state of storage capacitor. In modern DRAM devices, the capacitance of a storage capacitor is far smaller than the capacitance of the BL. Typically, the capacitance of a storage capacitor is one-tenth of the capacitance of the long BL that is connected to hundreds or thousands of other cells. The relative capacitance values create the scenario that when the small charge contained in a storage capacitor is placed on the BL, the resulting voltage on the BL is small and difficult to measure in an absolute sense. In DRAM devices, the voltage sensing problem is resolved through the use of a differential sense amplifier that compares the voltage of the BL to a reference voltage.

The use of differential sense amplifier, in turn, introduces some requirements on the DRAM array structure. Particularly, instead of a single BL, a pair of BLs needs to be used to sense the voltage value contained in any DRAM cell. In addition, in order to ensure that the voltage and capacitance values on the pair of BLs are closely matched, the BLs must be closely matched in terms of path lengths and the number of cells attached. The above requirements lead to two distinctly different array structures: open BL structures and folded BL structures.

###### Flash NVM

Flash memory is the most widely used NVM technology today. The key device in this prevailing memory is floating gate (FG) transistors. A figure of cross section of an FG transistor is shown in [Figure 1.4](#Chapter1.html#c01_fig4). Unlike a metal oxide silicon field effect transistor (MOSFET) transistor, an additional floating gate is added between the control gate and channel. Isolated by oxide layers, floating gate is able to trap charges and keep them for years. Therefore, the FG transistor encodes data based on whether electrons are trapped and is able to retain data without power. That is where “nonvolatile” is derived from.

![image](images/PBPC0390-01-f04.jpg)

Figure 1.4 The cross section of an FG transistor

The principle of read operation can be described as follows. When no charges are trapped in floating gate, the FG transistor has a threshold voltage of ![image](images/ch01_stripin_si29.gif); when negative charges are trapped, they attract positive charges of control gate; thus, higher control gate voltage is required to turn on the channel, which produces a higher threshold voltage ![image](images/ch01_stripin_si30.gif). By applying intermediate control gate voltage that is between ![image](images/ch01_stripin_si31.gif), and measuring current, the state of device can be known.

The write operation of FG transistor involves injecting or pulling electrons across the oxide barrier. There are two ways to achieve this, quantum tunneling or hot electron injection. In quantum tunneling scenario, high voltage is applied on control gate, quantum tunneling will take place between the floating gate and channel, and electrons can travel across the oxide barrier. For hot electron injection scenario, electrons are accelerated under high electrical field in the channel till its energy is high enough to penetrate the oxide layer. Note that electrons with high energy will damage the oxide lattice, and such damage will accumulate and lead to a limited write cycles, which is typically around ![image](images/ch01_stripin_si33.gif)cycles.

There are two common layouts for flash memory, shown in [Figure 1.5](#Chapter1.html#c01_fig5), NAND flash memory with FG transistors in series and NOR flash memory with FG transistors in parallel. The names NAND and NOR are derived from the fact that their connection fashion in series or parallel resemble a NAND gate or a NOR gate. NAND layout has the density advantage over NOR layout because each row only has one ground connection, and is thus widely used for external storage. NOR layout has lower latency and is thus widely used in embedded systems, where high performance is required. [Figure 1.5](#Chapter1.html#c01_fig5) also shows how the read of NAND and NOR flash memory can be achieved. The relationship between the different applied voltage magnitude is shown as follows:

![image](images/ch01_stripin_si36.gif)

![image](images/PBPC0390-01-f05.jpg)

Figure 1.5 Two common layouts for flash memory: NOR flash memory and NAND flash memory

##### 1.1.2.2 Nanoscale limitations

With scaling down of the technology towards nanolevel, there are some challenges and limitations in the traditional memory architecture. Such challenges are caused by physical rules and is summarized from two perspectives. On the one hand, there are functional failures due to the process variation that transistors may have mismatch problems. On the other hand, the thermal runaway failures are caused by positive feedback in an SRAM or a DRAM cell \[28\]. As a result, NVM is considered as a potential solution for data storage with the scaling technology.

#### 1.1.3 Nonvolatile IMC architecture

In the conventional computing architecture, all the data are stored in memory. It is separated from the general processors so that I/O connections are required. As a result, during the data processing, all data need to be read out to the external processor and written back afterwards. However, in data-oriented applications such as ML acceleration, this architecture will incur significant I/O congestions and hence greatly degrade the overall performance \[27,29–32\]. In addition, significant static power will be consumed because all the data need to be held, even though it does not need to be used at the moment \[26,28,33–39\].

Theoretically, it is feasible to overcome the bandwidth issue by adding more I/O pins or operating them at higher frequency. Practically, however, the I/O frequency is limited by the signal propagation delay and signal integrity issues, and I/O number is limited by the packaging technology, and thus the bandwidth is nearly saturated.

Besides improving the bandwidth of memory, reducing the volume of data communicating between processor and memory is another feasible option to enhance the performance. Conventionally, the processor only reads raw data from the main memory. If the memory can perform some operations before sending data, the I/O communication requirement can be significantly reduced \[40–42\]. For instance, if one needs to add eight numbers, one has to load all the eight values into the processor in the conventional way. However, if the addition of two numbers is performed as an in-memory logic operation, one can preprocess the adding inside memory and only four numbers need to be read out.

To perform IMC, implementing logic operations inside the memory is required so that the preprocessing can be done. Such an architecture is called logic-in-memory architecture. In general, the requirement of the ideal logic-in-memory architecture is summarized in [Figure 1.6](#Chapter1.html#c01_fig6). A big NVM sea is connected with thousands of small accelerator cores through high bandwidth and energy-efficient reconfigurable I/Os. Considering the leakage reduction at the same time, logic-in-memory architectures that are associated with NVM are presented in \[43–47\]. [Figure 1.7](#Chapter1.html#c01_fig7) shows a logic-in-memory architecture by building CMOS circuits with storage devices. The example shows a full-adder with both *sum* and *carry* logic. However, such a cell-level in-memory architecture has two major problems. First, the CMOS-based logic is built in memory so that it is difficult to be reconfigured. Second, it can only perform low-complex logic operations. In the example, it needs ![image](images/ch01_stripin_si34.gif)transistors for a simple 1-bit adder. The complexity of memory will be thus greatly increased.

![image](images/PBPC0390-01-f06.jpg)

Figure 1.6 Ideal logic-in-memory architecture

![image](images/PBPC0390-01-f07.jpg)

Figure 1.7 IMC architecture at memory-cell level

Another in-memory architecture to investigate at the block level in distributed fashion is illustrated in [Figure 1.8](#Chapter1.html#c01_fig8), which is more effective for traffic reduction. A memory data is usually organized in H-tree fashion, and the data block can be the data array or a number of data arrays that belong to same “H-tree” branch. Instead of inserting an in-memory logic at memory-cell level inside the data array, the architecture in [Figure 1.8](#Chapter1.html#c01_fig8) pairs each block of data with in-memory logic (accelerators). Different from the cell level in-memory architecture, the accelerators can be made with higher complexity, and the number of accelerators for each data block can also be customized. The data flow of the block-level in-memory architecture is to read out data from data block to in-memory logic, which performs particular functionality and then writes back the result. The data also needs to be stored in assigned blocks, but it is much more flexible than that of cell level in-memory architecture. The block-level in-memory architecture is very effective to reduce communication traffic between memory and processor. This is because significant operands reduction can be achieved by deploying accelerator with high-level functionality. For example, for face recognition in image processing application domain, instead of transmitting a whole image to obtain a Boolean result, the result can be directly gained through in-memory logic. In other words, the block-level in-memory architecture is suitable for big-data-driven applications where traffic reduction is more beneficial than latency reduction.

![image](images/PBPC0390-01-f08.jpg)

Figure 1.8 IMC architecture at memory block level

In this architecture, the nonvolatile ReRAM is intensively used. Both the memory block and logic block in each pair are purely implemented by ReRAM devices. In addition, energy-efficient in-memory logic units are deployed in the external processor to execute instructions that cannot be accelerated by in-memory logic.

### **1.2 Challenges and contributions**

Future cyber-physical systems require efficient real-time data analytics \[48–52\] with applications in robotics, brain–computer interface as well as autonomous vehicles. The recent works in \[53,54\] have shown a great potential for ML with significant reduced training time for real-time data analytics.

Hardware-based accelerator is currently practiced to assist ML applications. In traditional hardware accelerator, there is intensive data migration between memory and logic \[55,56\] causing both bandwidth wall and powerwall. Therefore, for data-oriented computation, it is beneficial to place logic accelerators as close as possible to the memory to alleviate the I/O communication overhead \[57\]. The cell-level IMC is proposed in \[43\], where simple logic circuits are embedded among memory arrays. Nevertheless, the according in-memory logic that is equipped in memory cannot be made for complex logic function, and also the utilization efficiency is low as logic cannot be shared among memory cells. In addition, there is significant memory leakage power in CMOS-based technology.

Emerging ReRAM \[58–64\] has shown great potential to be the solution for data-intensive applications. Besides the minimized leakage power due to nonvolatility, ReRAM in crossbar structure has been exploited as computational elements \[59,65\]. As such, both memory and logic components can be realized in a power- and area- efficient manner. More importantly, it can provide a true in-memory logic-memory integration architecture without using I/Os. Nevertheless, the previous ReRAM-crossbar based computation is mainly based on an analog fashion with multilevel values \[66\] or spike timing-dependent plasticity (STDP) \[67\]. Though it improves the computational capacity, the serious nonuniformity of ReRAM-crossbar at nanoscale limits its wide applications for accurate and repeated data analytics. Moreover, there is significant power consumption from additional AD-conversion and I/Os mentioned in \[67\]. Besides ReRAM-crossbar, coupled ReRAM-oscillator can be utilized for analog computing. By mapping fixed-point values to voltages, coupled ReRAM-oscillator can perform an L2-norm calculation. Significant speed-up and energy efficiency can be achieved due to the direct analog computing.

Although the nonvolatile IMC seems to be a promising solution for future data-oriented storage and computing system, the recent emerging ReRAM are still in their infancy due to the following unresolved challenges:

*   From circuit level, although there exist some simulators to perform hybrid NVM-CMOS circuit simulation \[63,64\], the ReRAM-based computation operations have not been fully developed yet. Without the detailed IMC implementation on ReRAM, it is hard to perform a real application on such an ReRAM-based nonvolatile in-memory accelerator.
*   From architecture level, it is necessary to explore a detailed implementation for the in-memory architecture. Controllers for conventional memory are not optimal for the ReRAM-based IMC system. The CMOS-based control bus and its communication protocol need to be redefined for such a novel architecture.
*   From system level, it is necessary to find out what ML algorithms can be mapped on the in-memory accelerator. For different operations or algorithms, we need to design different accelerators in order to achieve a higher parallelism and a better energy efficiency.

This book presents the idea of exploring the development of ReRAM-based logic operations and NVM in-memory architecture, as well as mapping details of various ML algorithms on such an architecture. For the ReRAM-based IMC implementation, the target is to develop detailed mappings for different operations on ReRAM. We proposed two kinds of ReRAM-based structures for operation accelerating: ReRAM-crossbar and ReRAM oscillator network. Particularly, this book has summarized the following advancements:

*   First, the NVM-SPICE is used for circuit-level simulation. The model of drift-type ReRAM is introduced with simulation results. In addition, the measurement results of forming, SET and RESET processes are also shown. For the diffusive-type ReRAM, a sub-circuit model is used for simulation.
*   Second, we introduce a binary ReRAM-crossbar for matrix-vector multiplication. Due to the nonuniformity of ReRAM device, the proposed binary ReRAM-crossbar can perform the computation more accurate compared to traditional ReRAM-crossbar in analogue fashion. In addition, three kinds of crossbar structures including passive array, one-transistor-one ReRAM (1T1R) and one-selector-one ReRAM (1S1R) are discussed.
*   Third, we describe an ReRAM-based coupled oscillator network for L2-norm calculation. A simple oscillator can be built based on the ON-OFF switching of diffusive ReRAM or the forming process of drift ReRAM. When the basic oscillators form a network, it can perform an L2-norm calculation based on the fitted simulation results.

For the in-memory accelerator, the target is to determine the design of architecture. For the architecture with only ReRAM as computing engine, we design the auxiliary CMOS logic and define the communication protocol between the processor and memory in detail. For the architecture with both ReRAM and CMOS as computing engine, we develop 3D CMOS-ReRAM architecture so that a higher throughput and parallelism can be achieved by introducing the following two topics:

*   First, a distributed in-memory computing architecture (XIMA) is described. Despite traditional store and load, we define two more commands: start and wait. In addition, all the logic blocks and data blocks are formed in pairs so that the delay of data-processing communication can be minimized. CMOS logic such as instruction queue and decoders are also designed.
*   Second, design space exploration of 3D CMOS-ReRAM architectures is presented. For single-layer 3D architecture, ReRAM devices are via connecting top-layer WLs and bottom-layer BLs. All the other CMOS logics are implemented in the bottom layer. For multilayer 3D architecture, we use two ReRAM layers as data buffer and logic implementation, respectively. In addition, TSVs are used to connect different layers.

For the data analytics mapping on ReRAM-based architecture, the target is to focus on detailed accelerator design for specific applications. In addition, the algorithm requires to be optimized so that all the operations can be fully mapped on the accelerator. We present case studies with several ML algorithms on distributed in-memory architecture (XIMA) and 3D CMOS-ReRAM architectures with significant improvement on bandwidth and energy efficiency.

*   First, for the XIMA, we have accelerated three ML algorithms. The learning and inference procedures of single-layer feedforward neural network (SLFN) have been optimized and partially mapped on the passive binary ReRAM-crossbar. In addition, we mapped the binary convolutional neural network (BCNN) on both passive array and 1S1R array with different mapping schemes. Moreover, L2-norm gradient-based learning and inference are also implemented on an ReRAM network with both crossbar and coupled oscillators.
*   Second, for 3D CMOS-ReRAM architecture, we also mapped the optimized SLFN algorithm. All the operations in learning and inference stages are implemented so that it can achieve the online learning. In addition, tensorized neural network (TNN) is mapped on both single-layer and multilayer accelerators with different mapping scheme.

For every ML algorithm mapped on XIMA and 3D CMOS-ReRAM accelerator, we evaluate their performance in device, architecture and system levels. All the implementations show higher throughput, bandwidth and parallelism with better energy efficiency.

### 1.3 Book organization

This book covers the entire flow from device, architecture and learning algorithm to system perspectives for emerging ReRAM. It is organized into the following chapters. The first chapter introduces the need and motivation to deploy ML algorithms for data-intensive computations. It also introduces the challenges and need for hardware for ML processing. In the second chapter, we present emerging memory devices that can support IMC and need for IMC are introduced in this chapter. Further, a comprehensive comparison and analysis of different IMC architectures are presented. The architectures include using traditional DRAM to emerging devices such as ReRAM and memristors. In the third chapter, modeling of ReRAM devices is presented followed by design of crossbar structures that are primarily used for matrix multiplication in ML applications. In addition, design of multibit storage for ReRAMs and other logic functional units with ReRAMs is presented.

The fourth chapter provides the basic information on ML algorithms, computational complexity and the types of operations involved in the ML algorithms, including least-square method (support vector machine (SVM), extreme learning machine (ELM)) and deep learning (CNN, TNN). Trained quantization (binary, ternary, eight-bit, etc.) will be addressed in this chapter. Additionally, the training mechanisms for deep CNNs and TNNs are focused in this chapter, as they are the time-consuming operations and the performance depends on the training efficiency.

The fifth chapter introduces multiple strategies to map the ML designs on to hardware accelerators. Designing of ReRAM crossbar-based IMC architectures to accelerate ML applications is presented. Further, to accommodate deep neural networks (DNNs) and CNNs, a 3D stacking-based CMOS-ReRAM architecture is introduced. The main focus of this chapter is on the architectural aspects and circuit designs to support the data-intensive computations with high speed. In Chapter 6, we introduce techniques to map the ML applications for ReRAM and the major challenges and the scope for improvement. The mapping techniques for different ML algorithms for different architectures such as ReRAM cross with traditional 2D and 3D architectures are illustrated.

Case studies for ReRAM-based ML acceleration for different scenarios are presented. Chapter 7 presents ResNet under different scenarios such as DNN with quantization, ReRAM-based acceleration for ResNet. In addition to the ResNet, this book presents ReRAM-based accelerator for compressive sensing application in Chapter 8. For this part, different scenarios such as iterative heuristic algorithm and row generation algorithms are presented. All the case study chapters are presented with substantial amount of experimental results and analysis that aid in replicating the experiments and also prove the efficiency of ReRAM accelerators and its prominence in the design of future hardware accelerators. The last chapter summarizes the ReRAM accelerators and its impact on the ML applications. Furthermore, future directions with ReRAM devices to further enhance the ML computations are presented.

## *Chapter 2*  
**The need of in-memory computing**

### 2.1 Introduction

In 1974, Dennard predicted the reduction of switching power with the downward scaling of feature size of transistor \[68\], and this trend ended around 2004. The operating voltage and current reduction of transistor stagnated despite the ever-shrinking size of transistor because of the increasing leakage current. The increase of the operating frequency and the transistor density further exacerbates the power consumption of a computing system, which generates a large amount of heat and impedes the power efficiency. Another challenge for the power consumption is the intensive data transfer between data processing and memory units in conventional Von Neumann or Princeton computing architecture, so called the “memory wall.” In this computing paradigm, the computing unit can only process one task at a certain interval and wait for memory to update its results, because both data and instructions are stored in the same memory space, which greatly limits the throughput and causes idle power consumption. Although mechanisms like cache and branch prediction can partially eliminate the issues, the “memory wall” still poises a grand challenge for the massive data interchanging in modern processor technology.

To break “memory wall,” in-memory processing has been studied since 2000s and regarded as a promising way to reduce redundant data movement between memory and processing unit and decrease power consumption. The concept has been implemented with different hardware tools, e.g., 3D-stack dynamic random access memory (DRAM) \[69\] and embedded FLASH \[70\]. Software solutions like pruning, quantization and mixed precision topologies are implemented to reduce the intensity of signal interchanging.

The biological neural network (NN) outperforms conventional Von Neumann computing architecture based on central processing unit (CPU) or graphics processing unit (GPU) in term of power efficiency, which consumes only 1–100 fJ per synaptic event when performing intense parallel computing \[71,72\]. Currently, the synaptic resistive random access memory (ReRAM) has been successfully demonstrated to exhibit low power consumption ((<pJ) \[73\]. However, even the two most promising fully CMOS-based brain-inspired chips, the Loihi from Intel and the TrueNorth from IBM, still lag behind in power efficiency, which consume 23.6 and 26 pJ per synaptic event \[74,75\]. Neuromorphic computing mimics the synaptic dynamics in device and dataflow/connection in NN to perform computing with low power consumption. The synaptic events, which are directly monitored and precisely adjusted by ion flux in memory devices, have been successfully emulated in the system based on ReRAMs \[73\]. Neuromorphic computing architecture has less complex peripheral driving circuit and simple weight modification procedure, e.g., fast dot product \[76\], in comparison with conventional Von Neumann computing architecture, as shown in [Figure 2.1](#Chapter2.html#c02_fig1) \[77\]. Neuromorphic computing also emphasizes the imitation of systematic neural architecture, e.g., artificial neural network (ANN) \[78\], convolution neural network (CNN) \[79\], spiking neural network (SNN) \[75,80\] and recurrent neural network (RNN) \[81\]. Unlike the general purposed processor, NNs are constructed for specified application scenarios. For examples, CNN has segregate layers and modularized kernel for fast and accurate feature recognition; the recycling output of RNNs makes it suitable for speed recognition; SNN is an event-driving system and much more flexible and fault-tolerant. The specialized neuromorphic computing architecture-based system on chip (SoC) usually exhibits several orders of magnitude reduction in power consumption when compared to the systems based on conventional Von Neumann architecture. For instance, the Intel-produced Loihi chip \[75\], which is based on asynchronous SNN, outperformed a single CPU by three orders of magnitude in both power efficiency and area.

![image](images/PBPC0390-02-f01.jpg)

Figure 2.1 Simulation of PCM to neural cell, and spiking time-dependent plasticity of biological synapse \[88\] and PCM

Conventional computer systems based on Von Neumann architecture and Si CMOS technologies offer much faster data processing speed and higher computing accuracy than human brain, but still significantly lag behind in terms of power consumption. For example, the Google-produced supervised deep learning machine, Alpha Go, consists of up to 1,202 CPUs and 176 GPUs to defeat the world champion of game Go, while it consumes 1,000 × time energy than human brain. Recent advances on the algorithms of neuromorphic computing, involving effectively solving complex tasks like the human brain, such as pattern recognition, data classification and object detection, make it close to practical applications. However, the hardware implementation of these neuromorphic computing algorithms based on Si CMOS technologies for parallelism and weight adaption reasons poises great challenges in terms of computation, memory and communications, and gives rise to high power consumption. It is highly imperative to make breakthrough in the hardware implementation for neuromorphic computing systems.

### 2.2 Neuromorphic computing devices

As today's computing becomes more and more data intensive, the computing paradigm is transferring from computation center to data center. Neuromorphic computation (e.g., vector matrix multiplication) requires the device characteristics with linear and symmetric tuning, long retention, low stochastic behavior (blind updates) and low energy tuning. Emerging nonvolatile memories (NVMs) can potentially meet these requirements, e.g., instantaneous writing/reading (∼ns), low operation voltage (<1 V) and power consumption (<pJ per synaptic event) \[82\]. Here, we briefly describe the working mechanisms of the ReRAM, spin-torque-transfer-magnetic random-access memory (STT-MRAM) and phase-change memory (PCM).

The widely used static random access memories (SRAMs) and DRAMs store information through charge and require a constant wave of operating voltage to maintain or update their states, by charging or discharging a capacitor. Emerging NVMs of ReRAM is non-charge-based device, which is free from the constrain of capacitor for data storage. A small operating voltage (![image](images/ch02_stripin_si1.gif)1 V) is sufficiently large for the operation ReRAM, and no subsequent power is required for maintaining the states.

Today's deep learning applications require unprecedented amount of data for dynamic data analysis. Conventional CPU/GPU has to fetch data from cache memory through programmed procedures, which usually results in the standby of processor due to the lack of useful data. Because data interchanging is costly in latency and power consumption, the most direct optimization methodology is data localization, which minimizes the physical distance between processor and cache. ReRAM has good compatibility with CMOS, which makes them ideal for 3D stacking. The 3D-stacked ReRAMs can be mounted on the top of processor and can shorten the data traveling path and enable high-density memory, due to thickness. The 3D-stacked ReRAM memory can substantially reduce data traveling, enlarge data reuse and ultimately improve power efficiency. Compared with the current popular memories, STT-MRAM excel SRAM in cell size and power efficiency, ReRAM outclassed FLASH in power consumption, read/write speed and endurance. In STT-MRAM, retention time is in trade-off with operating or switching power. Unlike other NVM devices with retention time over 10 years, retention of STT-MRAM has a one-to-one relation with stimulating pulse. And as substitution of RAM, long retention time of STT-MRAM is irrelevant to performance and thus retention is reduced (e.g., second) for lower power consumption.

As a memory, reading/writing is essential for computing. Unlike the traditional state holding units, ReRAM can be read out and modulated in crossbar separately with high power efficiency. Because during reading/writing process, the one-transistor one ReRAM (IT1R), for instance, only the targeted unit is assigned and all other units would remain idle.

#### 2.2.1 Resistive random-access memory

The resistance switching property of ReRAM was first studied in 1960s \[82\]. The device configuration of ReRAM is a sandwich-like structure with an insulating material between two metal electrodes. It includes the top electrode (TE), the middle layer of oxides and the bottom electrode (BE). Generally, the ReRAMs are two-terminal devices, which have two resistance states, a high-resistance state (HRS, or OFF state) and a low-resistance state (LRS, or ON state). The resistance states are manipulated by applied electrical potential and stimuli duration. The resistive switching mechanism is a result of the formation/rupture of conductive filament in metal oxide caused by the generation and drift of oxygen vacancies. It exhibits symmetric behavior or Lissajous I/V curve in SET/RESET process. The non-charge-based ReRAM possesses a long-term plasticity characteristics, which keeps the weight (conductance) stable in certain period, even without cycling operating power.

The *I–V* characteristic of ReRAM is presented according to (2.1):

![image](images/ch02_stripin_si61.gif)

where ![image](images/ch02_stripin_si7.gif)(∼1 mA), ![image](images/ch02_stripin_si9.gif)(∼0.25 nm) and ![image](images/ch02_stripin_si11.gif)(∼0.25 V) are constants, determined based on the material properties. The HRS resistance has exponential co-relationship with distance (![image](images/ch02_stripin_si13.gif)) and large amount of ![image](images/ch02_stripin_si14.gif)(![image](images/ch02_stripin_si15.gif)0.5 V). The ReRAM resistance not only responds to electrical stimuli but also depends on the duration of applied stimuli, as shown in (2.2):

![image](images/ch02_stripin_si62.gif)

where ![image](images/ch02_stripin_si16.gif)is vacancy generating speed and is determined by the discrepancy between generation and recombination rate. The mathematic model of ReRAM is similar to biological synapse and exhibition of nonvolatile behavior with ultra-low power computing, \[83, 84\], which makes ReRAM an ideal candidate for the building block of neuromorphic computing. Spiking time-dependent plasticity, a vital characteristic of biological synapse for array-level neuromorphic computing, e.g., SNN, has been successfully demonstrated in ReRAM \[85\].

As a two-terminal nonvolatile device, ReRAM crossbar has inherent advantage in power efficiency and switching speed. When ReRAM crossbars are fabricated in large scale with CMOS integration, ReRAM devices are sandwiched by two perpendicular electrode wires at every cross point. Thus, a matrix-like dense array of nanoscale ReRAM is relatively easy to implement. Since nonvolatile and two-terminal ReRAM enables in-memory computing (IMC) and requires only a small amount of operating voltage, the processing unit based on ReRAM crossbar outperform CPU or GPU with conventional Von Neumann architecture in energy consumption, scalability and process speed.

#### 2.2.2 Spin-transfer-torque magnetic random-access memory

The STT-MRAM contains three layers to form magnetic tunneling junction (MTJ), the free layer for data storage, the pined layer for reference and the tunnel barrier for magnetic insulation and data reading procedure \[86, 87\]. The tunnel barrier defines the energy barrier (![image](images/ch02_stripin_si17.gif)) for switching ON and OFF states. The magnetic field direction of free layer is deterministic to the electrical resistance of the memory cell. When the magnetic moments of free layer and tunnel layer are in parallel, the STT-MRAM shows low resistance. The STT-MRAM exhibits HRS in antiparallel configuration. By introducing opposite magnetic field into free layer, the STT-MRAM can exhibit multiple resistance states \[87\]. An insulation domain wall is placed between the two opposite magnetic domains and adjusted by STT phenomenon. As the retention time is associated with ![image](images/ch02_stripin_si18.gif)and switching power, the STT-MRAM has the smallest power consumption in all NVMs and operating speed with its full exploited nonvolatility.

#### 2.2.3 Phase change memory

In PCM, the transition from HRS to LRS is represented by the phase change from amorphous to crystalline state of switching layer. In RESET procedure, the crystallized phase change material is melted to amorphous phase by electrically generated heat. A smaller current is required to SET the phase change material back to LRS.

The NVM devices exhibit great advantages in terms of endurance, power consumption and speed over SRAM and FLASH in data storage. A ReRAM-based hybrid system can work as a memory and processor simultaneously, which can eliminate redundant data movement. With the boost of dot-product engine \[76, 89\], an array of ReRAM can solve some complex task by simply using Ohm's law and Kirchhoff's current law in a very short time, e.g., the multiplication and summation of matrix.

PCM possesses similar synaptic plasticity with ReRAM. Compared to other NVM devices, PCM has a relatively large range of switching resistance, which makes it ideal for synaptic analog computing with modulation scale of 1% per event. By using a gradually increasing amplitude and customized duration of stimulating impulse, PCM are reported to have over 200 adjusting levels from LRS to HRS \[90\]. As shown in [Figure 2.1](#Chapter2.html#c02_fig1), plasticity or weight updating of PCM is time dependent. The different arrivals of pre- and post-synapse event determine the direction of modulation. Like neuro-synapse, PCM exhibits accumulative behaviors in response to a string of continuous spikes and can be described as according to (2.3):

![image](images/ch02_stripin_si63.gif)

where ![image](images/ch02_stripin_si19.gif)is the synaptic weight to be updated, ![image](images/ch02_stripin_si20.gif)is the arrival time variance of pre/post-synapse events, ![image](images/ch02_stripin_si21.gif)is scaling factor and ![image](images/ch02_stripin_si22.gif)stands for the constants of STDP curve. PCM-based synapse exhibits lower power consumption compared with CMOS and capacitor-based synaptic device, which consumes only ∼50 and 0. 675 pJ for RESET and SET process and can be further reduced as PCM device shrinks down. But the CMOS and capacitor-based synaptic devices require consumption of ∼10^(−9) J per synaptic event for proper functionality \[91\].

### 2.3 Characteristics of NVM devices for neuromorphic computing

The desirable characteristics of neuromorphic device for computing include linear/symmetric tuning, scalability, multilevel resistance state, long retention time, stochastic behavior and low energy consumption.

1\. Linear/symmetric tuning: Because weight updating follows a time-dependent mechanism, the linear and symmetric relationship between weight carrier and stimulating pulse facilitates the less computing operation and power consumption. Most of the aforementioned NVMs possess relatively linear *I/V* electrical characteristics. For instance, the linearity of TaO[*x*]/TiO[2] ReRAM can be enhanced by applying a string of varying-duration impulse, as shown in [Figure 2.2](#Chapter2.html#c02_fig2).

2\. Scalability and stackability: The downward scaling of memory device enables high-density integration. Most of the NVM devices have been successfully fabricated in approximately 10 nm scale level. To further increase the integration density and shorten the distance between memory and process, emerging NVM devices are implemented in three-dimensional (3D) stacking and embedded into processor.

3\. Multilevel resistance state: Because the weights in biological synapses are processed in analog form, it requires multilevel resistance states in neuromorphic devices. A great amount of bioinspired algorithms require multilevel of states than inferenced 0/1 state \[92\].

4\. Longtime retention: During the implementation process of computation, the continuous updating of weights has limited requirements on retention time. But after the operation, the long retention time of NVMs is required to ensure that the stored weight remains even if NVM devices are switched to idle (power-off). Therefore, extra power could be saved as a global updating of weights is no longer required in NVM-based system.

5\. Low stochastic tunneling: NVMs still suffer from device variation and switching ambiguity, e.g., abrupt decrease of resistance in ReRAM and PCM. The stochastic switching property of NVM is still an open research and hinders commercial applications. Recently, there are a few works about NNs \[92, 93\], which reveals great resistance to device variations. However, such NNs sacrifice in architecture and accuracy.

![image](images/PBPC0390-02-f02.jpg)

Figure 2.2 Modulation of TaO^x/TiO² ReRAM stimulating pulse for better linearity \[92\]

### 2.4 IMC architectures for machine learning

Therefore, an increasing amount of research in alternative non-Von Neumann computer architectures such as in-memory and near-memory computing is being carried out in order to overcome the existing challenges of traditional Von Neumann architecture \[20, 94\]. IMC or processing-in-memory (PIM) bridges the separation between memory and processor by implementing processing units inside the memory chip itself \[95, 96\]. Due to fabrication limitations of the memory chips, these processing elements can achieve only limited functionalities \[97\]. However, they can leverage the bitline-level parallelism inside memory chip to construct a massively parallel single-instruction multiple data (SIMD)-like processing architecture that also enjoys the very high-bandwidth and low-latency data communication through the memory bitlines. IMC makes a viable candidate for implementing ML applications, most importantly the CNN algorithms in which convolution operations alone accounts for the largest fraction of a CNN computation time when implemented in GPUs and CPUs \[94, 98\]. IMC architectures can achieve dramatic performance optimization at unmatched power efficiency in CNN/DNN applications.

A vast amount of research has been carried out over the past decade in designing CNN/DNN inference and training machines on different memory platforms including the traditional memory platforms of SRAM and DRAM as well as novel nonvolatile resistive RAM (ReRAM), PCM and MRAMs such as STT-MRAM and spin orbit torque MRAM (SOT-MRAM) technologies. It has been found that a satisfactory level of accuracy can be retained even despite performing various levels of quantization/downscaling of data parameters in CNN algorithms \[93–103\]. This opens up an exploration space for high performance and low power CNN implementations for IoT and mobile applications. The IMC paradigm is also capitalizing on this data downscaling technique \[94, 103–111\].

Given the importance of memory technology in the design of IMC systems, we first categorize IMC architectures w.r.t. the memory technology that the IMCs are built on. The memory technologies can be classified into conventional memory (SRAM and DRAM) and emerging memory (ReRAM, STT-MRAM and SOT-MRAM). Recent works on the IMC based on the memory technology is provided next.

#### 2.4.1 Operating principles of IMC architectures

##### 2.4.1.1 In-macro operating schemes

The basic principle of IMC is to perform computation in memory devices/macros, and there are a variety of implementations. In general, IMC implementation from most of the literature can be summarized into four schemes, shown in [Figure 2.3](#Chapter2.html#c02_fig3).

![image](images/PBPC0390-02-f03.jpg)

Figure 2.3 IMC schemes

[Figure 2.3](#Chapter2.html#c02_fig3)(a) shows the most common scheme of IMC. Users have to write operand 2 into the memory devices and array first, and then convert operand 1 as input signals. In this scheme, operand 1 can be altered very fast while operand 2 needs to retain in memory. Most of the literature map weights as operand 2, and feature maps as operand 1 to accelerate NN applications. Because this scheme does not require high endurance, it is suitable for various memory devices including SRAM, ReRAM, PCM, Flash, etc.

Scheme in [Figure 2.3](#Chapter2.html#c02_fig3)(b) is more like “computing by-memory” instead of in-memory. In this scheme, both operands 1 and 2 are originally stored in registers (outside memory array). They need to be written into memory array first, and then peripheral circuits generate a specific waveform to let the memory perform computation. After that, circuits like sense-amps are required for result readout. Potentially, this scheme can be used to replace traditional CMOS digital logic circuits.

In [Figure 2.3](#Chapter2.html#c02_fig3)(c), the basic assumption is that both operands 1 and 2 are pre-stored inside the memory array. This usually happens in SRAM-based cache in Von Neumann architecture: feature maps from the last layer and weights in this layer are stored in the same cache, and users want to do some preprocessing before sending all data in the processor.

Scheme in [Figure 2.3](#Chapter2.html#c02_fig3)(d) shows an ultimate idea of IMC: both operands are originally stored inside the memory, and the result will be automatically written in memory after the computation process. This scheme unifies the data format of input and output, just like the voltage-level representation of the state-of-the-art CMOS logic.

##### 2.4.1.2 Architectures for operating schemes

From an architectural perspective, operating schemes in [Figure 2.3](#Chapter2.html#c02_fig3) are suitable for different architectures. Dataflow-like \[112\] and cache-like architectures \[113\] are the most common architectures for IMC. These two architectures can be simplified as shown in [Figure 2.4](#Chapter2.html#c02_fig4). Obviously, dataflow-like architecture is good for scheme in [Figure 2.3](#Chapter2.html#c02_fig3)(a), and cache-like architecture is good for schemes in [Figure 2.3](#Chapter2.html#c02_fig3)(b) and (c).

![image](images/PBPC0390-02-f04.jpg)

Figure 2.4 General architectures for IMC: (a) dataflow architecture; (b) cache architecture

As a deep neural network (DNN) hardware accelerator, we can find that dataflow-like architecture can be used for CNN and multilayer perceptron (MLP) which require multiplication-and-accumulation (MAC) for large matrices. Cache-like architecture performs better for small matrices operations with large iterations, such as RNN, gate recurrent unit (GRU) and long short-term memory (LSTM).

In the following sections, we will mainly discuss the in-macro scheme in [Figure 2.3](#Chapter2.html#c02_fig3)(a) and dataflow-like architecture in [Figure 2.4](#Chapter2.html#c02_fig4)(a).

#### 2.4.2 Analog and digitized fashion of IMC

To perform computation inside memory, computing circuit should be customized in the memory macro. In the view of memory designers, the operating scheme in an ordinary memory macro can be summarized into three steps:

*   Step 1: receive read/write command and address in digital domain;
*   Step 2: pre-charge bitlines, enable wordlines, sample bitcell voltage (for SRAM) or measure resistance (for NVMs) in analog domain;
*   Step 3: perform readout operation with sense amplifier, the output the result in digital domain.

Even in an ordinary memory macro access procedure, part of the process is done in the analog domain. As a result, the key of computing-in-memory is to perform different operations in analog domain. In most of literature, it is achieved by enabling multiple wordlines or bitlines simultaneously. [Figure 2.5](#Chapter2.html#c02_fig5) shows the comparison of ordinary memory macro and computing-in-memory macro.

![image](images/PBPC0390-02-f05.jpg)

Figure 2.5 Comparison of (a) ordinary memory macro with one wordline enabled; (b) computing-in-memory macro with multiple wordlines enabled

Next, we will discuss the detailed implementation of analog and digitized IMC. We can roughly categorize analog and digitized fashion with the following conditions:

*   Input resolution: The input digital signal can be directly used or converted into analog.
*   Memory device resolution: The memory device can be used as single-level cell (SLC) or multilevel cell (MLC).
*   Readout accurateness: Computing operation is performed in analog domain, and the circuit can read it out in an accurate fashion or inaccurate fashion.
*   Output resolution: The output signal can be readout with ADC/quantizer for multibit readout, or with SA/comparator for single-bit readout.

We also summarize analog and digitized computing-in-memory fashion in [Table 2.1](#Chapter2.html#c02_tbl1). In the categorization, the computing-in-memory fashion can only be called “digitized” when it is using digital(binary) input, SLC device, accurate readout and digital output.

Table 2.1 Categorization of analog and digitized computing in-memory

![image](images/tab2.1.jpg)

#### 2.4.3 Analog IMC

##### 2.4.3.1 Analog MAC

***Analog IMC for multiplication:*** The most common scheme of analog IMC performs computation in the current domain. [Figure 2.6](#Chapter2.html#c02_fig6) shows two schemes of multiplication in analog computing-in-memory. [Figure 2.6](#Chapter2.html#c02_fig6)(a) assumes that the memory device can operate as a two-terminal resistor, resulting a voltage-in-current-out computing scheme. On the contrary, [Figure 2.6](#Chapter2.html#c02_fig6)(b) assumes that the memory device can operate as a three-terminal transistor-like device, resulting a current-in-current-out computing scheme. It is obvious that these two operating schemes are suitable for different memory devices.

![image](images/PBPC0390-02-f06.jpg)

Figure 2.6 Analog multiplication in memory device with (a) voltage-in-current-out scheme; (b) current-in-current-out scheme

***Analog IMC for MAC:*** Most of the literature perform MAC-like traditional analog adder design as shown in [Figure 2.7](#Chapter2.html#c02_fig7). Here we use voltage-in-current-out scheme in [Figure 2.6](#Chapter2.html#c02_fig6)(a) as an example. Each input signal is converted into analog voltage, and a multiplication is performed with the memory device value, characterized as a resistor. Here the multiplication result is represented by the current. After multiplication, summation among all currents is performed with Opamp and feedback resistor or trans-impedance amplifier (TIA). As a result, the output voltage can be formulated as the following equation:

![image](images/ch02_stripin_si64.gif)

![image](images/PBPC0390-02-f07.jpg)

Figure 2.7 Matrix multiply and accumulate operation by analog IMC with Opamp-based summation circuit

If ![image](images/ch02_stripin_si30.gif), ![image](images/ch02_stripin_si31.gif)and ![image](images/ch02_stripin_si32.gif)are implemented by memory devices, we can achieve analog computation by memory devices. This computing scheme can be extended from device to array or macro as shown in [Figure 2.8](#Chapter2.html#c02_fig8).

![image](images/PBPC0390-02-f08.jpg)

Figure 2.8 Analog IMC by Opamp-based summation circuit

Besides current-domain-based IMC mentioned above, time-domain-based analog IMC \[114\] and charge-domain-based analog IMC \[115\] are also proposed. However, because these two schemes mainly utilize circuitry outside memory array to perform computation, we will not discuss them in detail in this book.

##### 2.4.3.2 Cascading IMC macros

Computation is performed in voltage-in-current-out or current-in-current-out scheme as shown in [Figure 2.6](#Chapter2.html#c02_fig6). If we want to design it in a normal way, i.e., make IMC macro as a universal processing core, we need digital-to-analog converters (DACs) and analog-to-digital converters (ADCs) for input and output, which consumes a lot of power. However, if we want to have a dedicated processor core, we can cascade several IMC cores in serial for higher energy efficiency, as shown in [Figure 2.9](#Chapter2.html#c02_fig9).

![image](images/PBPC0390-02-f09.jpg)

Figure 2.9 Cascading IMC macros with (a) DAC and ADC for each array; (b) DAC and ADC for multiple arrays

It is obvious that [Figure 2.9](#Chapter2.html#c02_fig9)(a) is more flexible in the architecture level. Users can perform different operations between arrays like floating-point multiplication, summation, division and nonlinear activation functions (Tanh, Sigmoid, etc.) for machine-learning algorithms. But for [Figure 2.9](#Chapter2.html#c02_fig9)(b), it can only support limited activation functions between layers like ReLU. Moreover, the analog computation error will be accumulated till ADC is used, resulting no error correction can be used in all-analog domain.

If cascading is considered directly, current-in-current-out scheme in [Figure 2.6](#Chapter2.html#c02_fig6)(b) is better than voltage-in-current-out in [Figure 2.6](#Chapter2.html#c02_fig6)(a) because it has a uniform input-output representation. For the other one, TIA is still needed for current–voltage conversion in each array.

##### 2.4.3.3 Bitcell and array design of analog IMC

In this section, we want to discuss bitcell and array design, which greatly influence feasibility and competitiveness of IMC solutions. However, they are ignored in many works. For example, the dimension of customized SRAM bitcell in standard analog design rule (before shrink) can have smaller transistor variation, leading a better accuracy performance in simulation or test-chip measurement. However, it may be 2 to 3 times larger than foundry's bitcell (after shrink). For example, works in \[116–119\] directly use foundry's SRAM bitcell or slightly modify the layout in compact rule, resulting area competitiveness when comparing with traditional architecture.

As for emerging memories such as RRAM, PCM and MRAM, because 1T1R or 1T1M is normally used in logic process, bitcell design may not be a problem for IMC. However, if multilevel input is used, the array layout design may be different from foundry's design for storage, as shown in [Figure 2.10](#Chapter2.html#c02_fig10).

![image](images/PBPC0390-02-f10.jpg)

Figure 2.10 Comparison for 1T1R array with (a) parallel sourceline and bitline; (b) vertical sourceline and bitline

[Figure 2.10](#Chapter2.html#c02_fig10)(a) is parallel-sourceline-bitline scheme and [Figure 2.10](#Chapter2.html#c02_fig10)(b) is vertical-sourceline-bitline scheme. For higher energy efficiency and throughput IMC core design, most of works use vertical scheme because it supports analog voltage input. However, some challenges exist in this scheme. First, this scheme needs DACs at input, resulting in extra power consumption. Meanwhile, this DAC should have a large driving capability because all the current through memory device comes from DAC. In this case, it is challenging to design a DAC with both high resolution and large output current. Second, because the array needs to perform parallel program, IR drop may incur some problems. For example, the last cell in one row may not be fully programmed. However, for parallel sourceline and bitline scheme in [Figure 2.10](#Chapter2.html#c02_fig10)(a), each sourceline and bitline only needs to program one device. Therefore, it is less likely to have the device program problem.

As what we observe, most of the works use vertical scheme in [Figure 2.10](#Chapter2.html#c02_fig10)(b), and works from \[120, 121\] use parallel scheme in [Figure 2.10](#Chapter2.html#c02_fig10)(b).

##### 2.4.3.4 Peripheral circuitry of analog IMC

A brief overview of analog IMC macro is shown in [Figure 2.11](#Chapter2.html#c02_fig11). It is composed of digital input buffer, input circuit, memory array, readout peripheral, digital controller, program circuit and output buffer.

*   The digital input module receives commands and data from modules outside IMC core, and it needs to do two tasks: (1) to buffer input data and send to input peripheral; (2) to analyze commands and send to compute-in-memory (CIM) digital controller.
*   The input peripheral converts input data into analog voltage with large driving capability, performs sample-and-hold (if time division multiplexing is used).
*   The CIM digital controller is the core module which determines the mode (program, verify, computing, testing, etc.) of CIM core, input peripheral converts input data into analog voltage with large driving capability, performs sample-and-hold (if time division multiplexing is used) and performs significant controlling (such as pulse width and amplitude for programming an MLC device).
*   The program peripheral generates voltage signals required for both programming and computing. For SRAM, it can be simplified as a write driver, but for RRAM or NOR Flash, charge pump and linear dropout regulator may be used. What is more, if MLC is required in programming procedure, it needs to have trimmer or DAC to generate very precise voltage or current.
*   The readout peripheral focuses on how to measure output current or voltage signals. It should be with high accuracy, large dynamic range and fast readout.
*   The digital output module works as an output buffer, and it also needs to send alert signal outside when necessary.

![image](images/PBPC0390-02-f11.jpg)

Figure 2.11 Analog IMC by Opamp-based summation circuit

##### 2.4.3.5 Challenges of analog IMC

Although analog IMC has shown great potential for a low-power high-throughput solution for machine learning, it still needs to overcome several challenges in some perspectives.

First, in the architecture level, IMC core can only be used as accelerator of MAC operation. As a result, it can show the best advantage for applications with massive MAC operations. However, some large-scale machine learning algorithms are not full of MAC operations, but have some activation and division operations. In addition, IMC core is good for large-scale MAC, i.e., ![image](images/ch02_stripin_si33.gif). If the dimension of matrix is only ![image](images/ch02_stripin_si34.gif), it may not be more energy-efficient than GPU or tensor processing unit (TPU). Also, the architecture flexibility of IMC is worse than general processors.

Second, in the application level, most of high-throughput scenarios require very powerful computation capacity for both training and inference. IMC has shown its high-throughput potential in inference stage, but the endurance and write speed become limitation in training stage. As a result, most companies or startups are going to use IMC in edge devices.

Third, the accuracy loss is difficult to evaluate in analog computation. As far as we know, analog IMC composes the following error sources:

*   Input error: The error occurred in DACs.
*   Device error: The conductance or resistance variation of the memory device. Note that analog 8-bit does not equal to digital 8-bit, and an analog MLC will show a specific distribution, resulting, in calculation error.
*   Array error: Accuracy loss due to large-array effects, including IR-drop, cross talk, and so on.
*   Output error: The error occurred in ADCs.

##### 2.4.3.6 Trade-offs of analog IMC devices

We summarize the ideal specification of IMC devices in [Table 2.2](#Chapter2.html#c02_tbl2). It would be perfect if a device can have SRAM-like write/read speed, endurance and on/off ratio, MRAM-like on-state variation and retention, RRAM-like cell density, NOR Flash-like resolution and linearity.

Table 2.2 Vital specification of IMC device

| Specification || Ideal value || Remarks and reason |
| --- | --- | --- |
| Resolution || 8 bits or more || Directly determines what algorithm can be implemented in CIM |
| --- | --- | --- |
| On/off ratio || 1,000× or more || For “real-zero” in CIM |
| On-state variation || ![image](images/ch02_stripin_si38.gif)1% || For “uniformed-one” in CIM |
| Retention || 10 years@125° C || Determines the refresh period |
| Endurance || Unlimited || Can be used in training scenario |
| Linearity mismatch || ![image](images/ch02_stripin_si38.gif)1% || Determines the input resolution |
| Write speed || ~ns || Can be used in training scenario |
| Current density || ![image](images/ch02_stripin_si40.gif)A || Reduce the impact from wire resistance, also for low-power and easy-circuit implementation |
| Read speed || ~ns || For low-latency scenario |
| Area || ![image](images/ch02_stripin_si42.gif) || High-density on-chip |
| 3D-stack || Yes || For higher-density on-chip |
| Process || BEOL || Can be integrated in advanced technology node |
| Yield || 100% || N/A |

However, some specifications listed in [Table 2.2](#Chapter2.html#c02_tbl2) are contradictory. For example, a device must be trimmed and run through a long write–verify scheme to be programmed to 8 bits or more. Similarly, a multilevel sensing circuit is required for a high-resolution device, resulting in longer readout time.

#### 2.4.4 Digitized IMC

As shown in [Table 2.1](#Chapter2.html#c02_tbl1), digitized IMC should have everything binarized including input, memory cell and output. As a result, it is very similar with a normal memory array but with limited numbers of wordlines/bitlines enabled simultaneously. For example, works in \[113, 122\] only enable two wordlines inside memory array.

It is obvious that the digitized IMC can have better accuracy compared to analog fashion. In addition, error correction code (ECC) techniques can be used in this scheme and the computation is reversible. However, apparently this fashion can only gain 1 to 2 times energy efficiency, compared to normal memory macro.

#### 2.4.5 Literature review of IMC

The IMC architectures are categorized based on the memory node type, mapping, access and quantization type, as presented in \[?\].

##### 2.4.5.1 DRAM-based IMCs

***AMBIT:*** AMBIT \[123\] is an IMC that performs bulk bitwise AND & OR operations based on charge sharing across bitlines by simply activating three operand rows (wordlines) concurrently. Additionally, AMBIT performs NOT operations by a novel mechanism which is facilitated by enhancing one row of cells in a subarray with two access transistors (2TC1) formation. Although AMBIT does not have a machine learning-aimed application domain, it establishes the basis for two other CNN accelerators DRISA \[104\] and DRACC \[105\].

***DRISA:*** DRISA \[104\] is a DRAM-based in-situ CNN accelerator that performs CNN inference on 8-bit binary weighted neural network (BWNN). DRISA leverages a 3T1C memory cell formation from older DRAMs for implementing NOR logic and also the regular 1T1C DRAM cell formation for AND, OR & NOT operations, whose mechanisms are borrowed from AMBIT. Additionally DRISA features a shifting layer, which together with the logic layer forms a re-configurable in-memory processing layer that can implement selection, ripple carry addition, carry–save addition and complete multiplication on large data. The DRAM memory organization is completely revamped through the resizing of parallel-operable banks and subarrays and also an additional hierarchical stage above banks called a Group.

***DrAcc:*** DrAcc \[105\] is a DRAM-based CNN accelerator that performs ternary weighted neural network (TWNN) inference where the convolution operations are reduced to accumulation (addition). It too follows AMBIT's mechanism for bitwise AND/OR logic operations but its key feature is the carry look-ahead adder implemented by modifying the sense-amplifier circuit. With an additional shifting layer, DrAcc can implement all CNN layers such as pooling, quantization–normalization and activation inside the memory. Furthermore, three data partitioning and mapping strategies as well as three different performance modes are proposed, which offer maximum throughput, minimum latency and maximum power efficiency, respectively.

***SCOPE:*** SCOPE \[124\] is an in-situ DNN (CNN/RNN) accelerator that utilizes stochastic computing (H2D algorithm) to simplify computation-intensive multiplication operations into bitwise AND operations. It's a bulk bitwise IMC/PIM architecture that can perform AND/OR operations. The subarray sense-amplifiers are modified to facilitate logic circuitry, register, shifter and stochastic number generator unit (SNG) for stochastic conversion. It can perform carry–save addition by combining the bitwise logic operations and capable of both inference and training of CNN with 8-bit fixed point precision.

***pPIM:*** Programmable PIM (pPIM) \[125\] is a look-up table (LUT)-based novel PIM architecture implemented inside DRAM chip. It is primarily designed to perform ultra-low power and low latency CNN/DNN acceleration. pPIM processing units are called “cores,” each of which contain one 8-bit LUT and consequently can perform computations and logic operations by reading from the pre-calculated entries. These LUTs can be programmed and re-programmed to perform virtually any operation on a pair of 4-bit operands. However, nine pPIM cores are grouped together and interconnected through a sophisticated routing fabric in order to form a “cluster.” Each of such cluster can perform operations such as MAC on 8-bit data operands by following a nine-step operation combining stages of operand decomposition, multiplication and addition. Due to its programmability, it is also capable of executing other CNN/DNN layers such as fully connected, activation and pooling layers. Alongside, pPIM can support operations with lower data precision, such as 4-bit scaled precision MAC. pPIM clusters are placed in rows in-between memory subarrays of DRAM banks. For inter-cluster communication, pPIM leverages the local bitlines of memory subarray, with the enhancement of subarray-interlinks that join bitlines of adjacent subarrays in order to facilitate fast data travel. pPIM cores are mostly implemented using transmission gates to minimize area overhead. Simulations show that this architecture can achieve 2,000×, 657.5× and 1.46× improvement in inference throughput per unit power consumption compared to state-of-the-art conventional processor architecture, GPU and a prior hybrid LUT-logic based PIM, respectively. Furthermore, 4-bit precision scaling improves the energy efficiency of the pPIM approximately by 1.35× for representative operations over its baseline 8-bit precision mode.

***LAcc:*** LAcc \[98\] is a DRAM-based PIM CNN accelerator that leverages the memory cells in a DRAM subarray to implement LUTs which store pre-calculated outputs of multiplication operations. Together with an XOR-based adder implemented on modified sense amplifiers, LAcc can perform 16-bit convolution operations. Since LUTs expand quadratically with the operands' size, LAcc leverages matrix decomposition to keep LUTs smaller. For further LUT reduction, it proposes fixing of either weights or inputs. LAcc performs convolution with 16-bit precision with impressive power and performance figures.

##### 2.4.5.2 NAND-Flash-based IMCs

***AMBIT:*** AMBIT \[123\] is an IMC that performs bulk bitwise AND & OR operations based on charge sharing across bitlines by simply activating three operand rows (wordlines) concurrently. Additionally, AMBIT performs NOT operations by a novel mechanism which is facilitated by enhancing one row of cells in a subarray with two access transistors (2TC1) formation. Although AMBIT does not have a machine learning-aimed application domain, it establishes the basis for two other CNN accelerators DRISA \[104\] and DRACC \[105\].

##### 2.4.5.3 SRAM-based IMCs

***Neural cache:*** Neural cache \[122\] is an SRAM based in-memory DNN inference (primarily focused on CNNs) engine made by re-purposing cache memory. It can implement convolution, pooling, quantization and fully connected layers at 8-bit data precision. Its base functionalities are bitwise AND & NOR operations which are performed simply by concurrently activating the operand rows. It can perform bit-serial addition, subtraction, multiplication, comparison, search and copy on larger data, aided by carrying latches appended to the sense amplifiers. A transpose memory unit provides hardware support to reorganize data in bit-serial format inside the memory.

***IMAC:*** IMAC \[126\] is a CNN inference engine that leverages ReRAM-like analog MAC to perform convolution of multibit data. Memory cells in a row contain multibit weights. Analog version of the input signals are driven through the wordlines of that row and the corresponding analog voltage signals on the bitlines are aggregated to perform MAC operations. Peripheral converters (DAC/ADC) perform digital-to-analog conversion and vice versa. It can implement fully connected layers and activation (ReLU) function too.

***XNOR-SRAM:*** XNOR-SRAM \[106\] is an in-memory binary/ ternary convolution macro for accelerating NNs. Binary/ternary CNN reduces convolution operations to a XNOR operations \[101\] followed by accumulation (XAC). XAC is performed by driving binary/ternary input signals through the wordlines in analog form which causes the 8T-SRAM cells that contain the binary weights to produce XNOR output signals on the read bitlines (RBL). Analog accumulation of XNOR outputs takes place on the RBL, followed by digitization in the ADC.

##### 2.4.5.4 ReRAM-based IMCs

***ISAAC:*** ISAAC \[127\] is a ReRAM crossbar array structured CNN/DNN in-situ accelerator that maps synaptic weights in the form of analog resistance values in the memory cells. In ISAAC, input bits are driven in serial through the wordlines in the form of analog voltage pulses. The corresponding current magnitudes in the bitlines represent the accumulated products of the input bits with all the weights (cells) connected along the respective bitlines. These partial products are digitized, shifted and then accumulated for complete MAC operations. Weights are represented in 2's complement to account for both positive and negative ones. ISAAC has a sophisticated hierarchical architecture including MAC, ADC/DAC, sigmoid and max pool units in each processing “tile”. ISAAC maps all the layers of a CNN in different tiles and adopts a pipelined dataflow.

***PRIME:*** PRIME \[112\] is an IMC architecture on ReRAM platform. It is created by modifying a portion of ReRAM crossbar array that can either act as host memory or an NN accelerator. It performs analog MAC in the crossbar array in a mechanism resembling that of ISAAC, except that separate crossbars are dedicated to positive and negative analog weights. It modifies default ReRAM micro-architecture heavily to also facilitate sigmoid, ReLU, max pooling, ADC/DAC and precision control unit and also a buffer subarray. PRIME features bank-level parallelism and offers software and API support for programming and data mapping.

***PipeLayer:*** Pipelayer \[128\] is a ReRAM-based accelerator which leverages spike-based signals and introduces batch level intra-layer parallelism through an inter-layer pipeline implementation. To improve throughput, this accelerator supports tiled architecture which combines computation and data encoding together in order to process data in parallel in the in-ReRAM crossbar array. The accelerator analyzes data dependencies between layers to improve the effectiveness of pipelining and inter-layer parallelism.

***BCNN accelerator:*** Tang *et al.* \[108\] present a BCNN accelerator that focuses heavily on optimizing CNN inference on the ReRAM crossbar platform. It considers a binary data storage in analog ReRAM cells to ensure maximum robustness from process variations. An elaborate matrix splitting scheme is presented for mapping large CNNs across multiple crossbar units. Different layers of the CNN including convolutional, fully connected and max-pooling layers are mapped to different ReRAM crossbar blocks, and the execution of the layers is pipelined. A sophisticated buffer (Line-Buffer) ensures the fastest and the most efficient transition of data from one layer to the next.

***Atomlayer:*** Atomlayer \[129\] is a ReRAM-based accelerator that leverages atomic layer computation in which one layer of an NN is processed at a time to eliminate pipelining. It addresses ISSAC's \[127\] limitation in performing NN training and the low power-efficiency issue of Pipelayer \[128\]. In order to reduce the pipeline bubbles, this design utilizes a large DRAM main memory to store initial and intermediate data generated in the NN inference or training. It uses rotating crossbars as the key components to perform atomic layer computations. It also uses row disjoint filter mapping to distribute filter rows across its multiple processing elements to ensure maximum data reuse and reduces the DRAM bandwidth.

***XNOR-ReRAM:*** XNOR-ReRAM \[107\] is a binary NN (MLP) inference engine implemented on ReRAM. Since the inputs and weights are binary (1-bit), the convolution operations are reduced to bitwise XNOR operations. A dual complementary cell setup is used to perform the XNORs. A worldline switch matrix replaces the row decoder in the ReRAM synaptic architecture that enables parallelism across memory rows. Operand matrices are split and distributed across bitlines. Partial sums are generated at multilevel sense amplifiers (MSLAs) on each bitline and then quantized accumulated and undergo binary activation to obtain output.

##### 2.4.5.5 STT-MRAM-based IMCs

***Binary CNN:*** Pan *et al*. \[109\] showed that binary CNN is a BCNN accelerator implemented on STT-MRAM. It uses multilevel STT-MRAM cell structure (ML-STT) where two asymmetric cells are fused together to contain 2 bits. It is capable of bulk bitwise AND/NAND, OR/NOR through multirow activation and also XOR and ripple–carry addition through modified sense amplifiers. Auxiliary processing unit (APU) peripheral to the memory bank performs other CNN operations such as batch normalization and pooling. This work is evaluated on XNOR-NET \[101\].

***MRIMA:*** MRIMA \[110\] is an IMC device implemented on STT-MRAM platform and is aimed at two different application domains: CNN inference and AES data encryption. Both applications are facilitated by in-memory compute arrays that can either act as memory devices or perform bulk bitwise AND, NAND, NOR (on either 2 or 3 operands) & XOR/XNOR operations by leveraging multirow activation and using different reference currents for the sensing of each of the logic outputs. MRIMA can perform BWNN and low bit-width CNN inferences. Convolutions are simplified by performing column decomposition of input and kernel matrices, followed by generating partial products by bitwise parallel AND operations between input and kernel columns and finally shifting and accumulating those partial products. MRIMA has its own instruction set architecture (ISA) and can be connected as a co-processor through the PCIe port.

***MRAM-DIMA:*** MRAM-DIMA \[130\] is an MRAM-based crossbar array MAC engine aimed at DNN applications. Weights are mapped in column major format across bitlines, and inputs are provided through the wordlines in pulse-width-modulated (PWM) form. Analog vector multiplication takes place in the MRAM cells in parallel and partial products are generated on the bitlines, later to be accumulated by a digital processor. MRAM-DIMA is also capable of performing clipped ReLU activation.

##### 2.4.5.6 SOT-MRAM-based IMCs

***Binary CNN:*** Fan *et al.* \[131\] is a binary CNN accelerator based on SOT-MRAM platform. BCNN inference reduces convolutions to simple in-memory bitwise AND operations, followed by accumulation in peripheral bit-counter. A DPU (digital processing unit) performs batch normalization, scaling, multiplier and pooling operations.

***IMCE:*** IMCE \[94\] is a SOT-MRAM-based IMC device that can perform CNN inference and training at different data precision combinations by leveraging a binary convolution mechanism. This mechanism involves column decomposition of the input f-map and the kernel (weight matrix) bitwise convolution of those columns and finally shifting and accumulation of those partial products through peripheral counter, shifter and adder to obtain the output feature map. An in-memory DPU executes quantization, batch normalization, pooling and activation filters.

***CMP-PIM:*** CMP-PIM \[132\] is a SOT-MRAM IMC that performs comparator-based DNN inference. Here the pixel-wise convolution operations in a convolutional layer are replaced by depth-wise separable convolutions which are a combination of binary pattern feature extraction (depth-wise convolution) and binary point-wise (bitwise) convolutions. The depth-wise convolution leverages fixed ternary kernel which is implemented through multibit comparison and accumulation in this paper. The bulk bitwise IMC architecture of CMP-PIM can perform AND/NAND, OR/NOR, XOR/XNOR operations.The point-wise convolution stage is implemented through bitwise AND, followed by bit-count, shifting and accumulation operations. Quantization, batch normalization and activation take place in in-memory DPU.

### 2.5 Analysis of IMC architectures

[Table 2.3](#Chapter2.html#c02_tbl3) presents a qualitative comparison of different IMC techniques. [Figure 2.12](#Chapter2.html#c02_fig12)(a) and (b) presents the comparison of the area of the IMCs based on traditional and emerging memory platforms, respectively. DRAM CNN/DNN accelerators are centered around a baseline area of 60 mm² except for SCOPE whose area is more than four times that of a commodity DRAM chip. SRAM-based neural cache's smaller footprint is due to its very low memory capacity (35 MB). ISAAC and PRIME have the highest areas among the ReRAM IMCs. This can be attributed to their large data precision (16-bit). However, AtomLayer also has 16-bit data precision and yet it has a significantly smaller area because it employs massive resource re-utilization aimed at reducing processing area. The two data precision configurations of Tang *et al*. (CNN and BCNN) and the binary precision of XNOR-ReRAM also reflect the same pattern of area being proportional to data precision. Similar observations can also be made for MRAM (STT-MRAM and SOT-MRAM)-based works–-IMCE with binary data precision and CMP-PIM with 8-bit data precision where CMP-PIM has a larger footprint.

Table 2.3 Prominent IMC architectures and their characteristics

![image](images/tab2.3.jpg)

![image](images/PBPC0390-02-f12.jpg)

Figure 2.12 Area for IMC architectures with (a) traditional and (b) emerging memory technologies

[Figure 2.13](#Chapter2.html#c02_fig13) presents performance (throughput per unit chip area) and efficiency (output per unit energy consumption) benchmark on AlexNet for volatile memory-based (DRAM and SRAM) IMCs. SCOPE presents splendid performance figures, albeit at a rather low efficiency which can be attributed to its stochastic method for multiplication operations. LAcc, thanks to its LUT implementation, ensures the maximum efficiency among these works. Neural cache's lowest efficiency and lowest performance figure can be traced back to its comparatively inefficient SRAM platform and smaller capacity (35 MB), respectively.

![image](images/PBPC0390-02-f13.jpg)

Figure 2.13 Benchmarked on AlexNet for traditional memory IMCs

[Figure 2.14](#Chapter2.html#c02_fig14) presents throughput (as Tera operations per second (TOPS) per unit area) and efficiency (as TOPs per unit power) comparison for NVM IMCs. Pipelayer has dramatically higher throughput but the lowest energy efficiency compared to ISAAC and Atomlayer because it leverages massive intra-layer data parallelism to maximize pipeline throughput. Although Atomlayer has the advantage of training capability, it does not outperform ISAAC in the field of efficiency. Due to very low data precision (binary/ternary precision), XNOR-ReRAM is the most efficient ReRAM IMC under comparison.

![image](images/PBPC0390-02-f14.jpg)

Figure 2.14 Emerging memory IMCs

## *Chapter 3*  
**The background of ReRAM devices**

In this chapter, we will first introduce the characteristics of resistive random-access memory (ReRAM) devices. Post-characterization of the ReRAMs, we introduce the structural design of the ReRAMs followed by a few applicational designs of ReRAM-based devices.

### 3.1 ReRAM device and SPICE model

In this section, we illustrate two types of the ReRAM devices depending on the diffusion of the charge particles: drift-type and diffusive-type. The model and usage of these devices are introduced in \[24, 133\] and are described with sufficient details in the following.

#### 3.1.1 Drift-type ReRAM device

The existence of ReRAM, also named as memristor, was first predicted by Leon Chua in 1976 \[60\], but not until nearly 30 years later was it first re-discovered and utilized in nanoscale devices at HP Labs \[62\]. The name memristor is derived from the fact that its resistance is determined by the current passed through it in the present and past as if it can remember its history. The memory effect specifically is the time integral of the current flowing through the device: when current flows in one direction through an ReRAM, its electrical resistance increases; while resistance decreases when the current flows in the opposite direction; similarly, when the current flow is stopped, the ReRAM retains its previous resistance, thus retaining or memorizing the (resistance) state. The bistable states of the device are defined as HRS and LRS. The write operation is achieved by applying large current, which changes its resistance rapidly. To read the cell, small current is applied to detect its resistance without significantly changing its resistance. The foundation of the fourth element ReRAM proposed by Leon Chua is shown in [Figure 3.1](#Chapter3.html#c03_fig1). In 2008, the first physical realization of an ReRAM was demonstrated by HP Labs: the memristive effect was achieved by moving the doping front along a ![image](images/ch03_si1.gif)thin-film device \[62\]. The materials at the different sides of the doping have different resistivity, and the overall resistance is calculated as the resistance of having two resistors in series. The diagram of ![image](images/ch03_si2.gif)x -based ReRAM cell structure is shown in [Figure 3.2](#Chapter3.html#c03_fig2). In addition, HP Labs has released the scanning electron microscope (SEM) photograph of ReRAM array (the ReRAM crossbar structure) in \[61\], as shown in [Figure 3.3](#Chapter3.html#c03_fig3).

![image](images/PBPC0390-03-f01.jpg)

Figure 3.1 The voltage–charge–current relationship among the basic three elements (resistor, capacitor and inductor) and the prediction of the fourth element: ReRAM \[60\]

![image](images/PBPC0390-03-f02.jpg)

Figure 3.2 The diagram of ![image](images/ch03_si3.gif)\-based ReRAM cell structure

![image](images/PBPC0390-03-f03.jpg)

Figure 3.3 Photograph of fabricated ReRAM array from HP

A comprehensive dynamic ReRAM model which takes charge-induced-drifting effect, slowdown effect and strong-electric-field effect into consideration is illustrated in [Figure 3.4](#Chapter3.html#c03_fig4)(a) with doping and un-doping regions. The term doping ratio (![image](images/ch03_si4.gif)) is introduced to numerically represent the ratio of doping region (![image](images/ch03_si5.gif)) over the whole thickness of ReRAM film (![image](images/ch03_si6.gif)). As there is a large difference of resistivity in doping and un-doping regions, the total resistance is changing with respect to the doping ratio. For instance, when ![image](images/ch03_si7.gif), the ReRAM is at LRS, where the resistance is nearly a thousand times smaller than the resistance at LRS with ![image](images/ch03_si8.gif).

![image](images/PBPC0390-03-f04.jpg)

Figure 3.4 Structure of ReRAM and nonlinear effects for dynamic model: (a) slowdown effect at boundary; (b) exponential relation between drift velocity and electric field

The operating principle of ReRAM device can be summarized as follows: charge-induced state (doping-ratio ![image](images/ch03_si9.gif)) shifting. As illustrated in [Figure 3.4](#Chapter3.html#c03_fig4)(a), the ReRAM can be seen as two regions in series, doping region and undoping region. The domain wall that separates two regions can be shifted by electric charge that flows through. When the positive charge flows towards the right-hand side of ReRAM junction, the domain wall shifts rightward, and thus the doping ratio (![image](images/ch03_si10.gif)) increases and the resistance reduces accordingly, and vice-versa for the charge flowing in the reverse direction. Traditionally, this mechanism can be described as a generalized voltage-controlled memristive system \[60\], mathematically defined as follows:

![image](images/ch03_si309.gif)

![image](images/ch03_si310.gif)

where *R* is the resistance of ReRAM and *f* is the explicit function of *w* and applied voltage *v*; *dw/dt* is the normalized drift velocity determined by *w* and external voltage *v*. Note that the complementary current-controlled memristive system can be defined similarly. The drifting velocity of ReRAM is a function of applied current that can be initially modeled in the following piecewise linear form \[62\]:

![image](images/ch03_si311.gif)

In addition, strong-electric-field effect stands for the exponential increase in the drift velocity under a strong electrical field condition (![image](images/ch03_si18.gif)) \[134\]. It usually happens in the nanoscale devices such as newly fabricated ReRAM at the scale of 20 nm. As illustrated in [Figure 3.4](#Chapter3.html#c03_fig4)(b), the phenomenon can be approximated by a ![image](images/ch03_si19.gif)function, as described in \[134\]:

![image](images/ch03_si312.gif)

where ![image](images/ch03_si20.gif)is the applied field strength, and definitions of remaining variables are shown in [Table 3.1](#Chapter3.html#c03_tbl1).

Table 3.1 Definitions of variables used for drift-ReRAM device

| Variable || Definition |
| --- | --- |
| ![image](images/ch03_si21.gif) || Resistance of ReRAM |
| --- | --- |
| ![image](images/ch03_si22.gif) || Conductance of ReRAM |
| ![image](images/ch03_si23.gif) || Magnetic flux |
| ![image](images/ch03_si24.gif) || Charge |
| ![image](images/ch03_si25.gif) || Length of the doped region |
| ![image](images/ch03_si26.gif) || Thickness of ReRAM film |
| ![image](images/ch03_si27.gif) || Doping ratio ![image](images/ch03_si28.gif)(nonvolatile state variable) |
| ![image](images/ch03_si29.gif) || Normalized drift velocity |
| ![image](images/ch03_si30.gif) || Resistance of low-resistance state (LRS) |
| ![image](images/ch03_si31.gif) || Resistance of high-resistance state (HRS) |
| ![image](images/ch03_si32.gif) || Window function defining the boundary condition of ![image](images/ch03_si33.gif) |
| ![image](images/ch03_si34.gif) || Mobility at small electric field |
| ![image](images/ch03_si35.gif) || Characteristic field for a particular mobile atom in the crystal |

Moreover, the slowdown effect of ReRAM is illustrated in [Figure 3.4](#Chapter3.html#c03_fig4)(a), when ![image](images/ch03_si36.gif)is approaching the boundaries where *w*\=0 or 1, the drift velocity drops quickly and is no longer linear with the current applied. This nonlinear dynamic effect can be characterized by either of the following window functions \[135, 136\]:

![image](images/ch03_si313.gif)

![image](images/ch03_si314.gif)

Therefore, the complete nonlinear dynamic ReRAM model relevant to doping-factor ![image](images/ch03_si36.gif)considering charge-induced-drifting effect, slowdown effect and strong-electric-field effect can be obtained from (2.2) to (2.6):

![image](images/ch03_si315.gif)

![image](images/ch03_si316.gif)

Incubating (3.5)–(3.7) derived in the ReRAM dynamic function described in modified nodal analysis (MNA) matrix, the following Jacobian terms can be derived, as presented in the following:

![image](images/ch03_si317.gif)

![image](images/ch03_si318.gif)

![image](images/ch03_si319.gif)

where ![image](images/ch03_si40.gif)is the conductance and ![image](images/ch03_si41.gif)is the nonvolatile state variable derivative of conductance; ![image](images/ch03_si42.gif)are constants; and ![image](images/ch03_si43.gif)is the window function. Recall that the other parameters are defined in [Table 3.1](#Chapter3.html#c03_tbl1). Therefore, all Jacobian terms required for the linearized system equation can be established, with which the ReRAM device simulation considering the nonvolatile state variables can be implemented in the SPICE-like simulator accordingly.

In order to verify the dynamic ReRAM models and functionality, a simulation to generate ReRAM hysteresis loop is required. The efficiency of the model-based operational characteristics is validated against experimental measurement in \[62\] for efficiency evaluation. The device parameters are set as ![image](images/ch03_si44.gif)nm, ![image](images/ch03_si45.gif), ![image](images/ch03_si46.gif); the initial resistance ![image](images/ch03_si47.gif), ![image](images/ch03_si48.gif), ![image](images/ch03_si49.gif); and Joglekar window function is applied with ![image](images/ch03_si50.gif). The dynamic behavior is investigated under the driving voltage of ![image](images/ch03_si51.gif). As shown in [Figure 3.5](#Chapter3.html#c03_fig5), simulation result can well capture the experiment results reported in \[62\].

![image](images/PBPC0390-03-f05.jpg)

Figure 3.5 ReRAM device simulation with Joglekar window function: I–V curve, which is consistent with the measured results reported

Apart from the modeling and simulation results, this chapter presents some measurements of the drift-ReRAM device. To perform this, one needs to perform a forming process of the ReRAM first, as shown in [Figure 3.6](#Chapter3.html#c03_fig6). Compliance current is set to ![image](images/ch03_si52.gif)A in our experiment.

![image](images/PBPC0390-03-f06.jpg)

Figure 3.6 Measurement results of voltage and current of a drift ReRAM in forming process

After forming process, an analysis with some experiments for the SET and RESET of the ReRAM device is analyzed here. First, a DC measurement with 17 times of SET and 18 times of RESET is studied, and the behavior of ReRAM shows a hysteresis loop as shown in [Figure 3.7](#Chapter3.html#c03_fig7). For the SET process, we use ![image](images/ch03_si53.gif)A as the compliance current.

![image](images/PBPC0390-03-f07.jpg)

Figure 3.7 Measurement results of an ReRAM hysteresis loop drift in SET and RESET processes

In addition, transient measurements are of interest to study. For this purpose, consider three pulses are used that the first and third pulses are for read propose, and the second voltage pulse is for SET or RESET. The transient measurement results use ![image](images/ch03_si54.gif)s as time interval. First, [Figure 3.8](#Chapter3.html#c03_fig8) depicts the SET operation and illustrates how the resistance of ReRAM changes from 1 MΩ to 50 k![image](images/ch03_si55.gif). Here, a ![image](images/ch03_si57.gif)V pulse is for read operation while ![image](images/ch03_si58.gif)V is for write. We can see the SET delay is in ![image](images/ch03_si59.gif)s so that we can hardly see the procedure of resistance change. Second, we use [Figure 3.9](#Chapter3.html#c03_fig9) to show the RESET operation, and the resistance of ReRAM changes from ![image](images/ch03_si60.gif)to 100 k![image](images/ch03_si61.gif). A ![image](images/ch03_si62.gif)V pulse is for read operation while ![image](images/ch03_si63.gif)V is for write operation.

![image](images/PBPC0390-03-f08.jpg)

Figure 3.8 Transient measurement results of resistance, voltage and current of a drift ReRAM in SET operation

![image](images/PBPC0390-03-f09.jpg)

Figure 3.9 Transient measurement results of resistance, voltage and current of a drift ReRAM in RESET operation

#### 3.1.2 Diffusive-type ReRAM device

The recent research studies \[137, 138\] have reported a diffusive-type ReRAM device. Different from the common drift-type ReRAM, the initial state of diffusive ReRAMs is always HRS with ![image](images/ch03_si64.gif)when no external voltage or current is applied. When the input voltage exceeds a threshold value ![image](images/ch03_si65.gif)for a while (e.g., 1 ms), the diffusive ReRAM will switch to LRS with ![image](images/ch03_si66.gif). After the device switches on, the resistance will slowly recover back to HRS if the applied voltage drops below another threshold ![image](images/ch03_si67.gif)for about 20 ms. Such a device shows great potentials as an automatically ON/OFF selector. In the following, we use ![image](images/ch03_si68.gif)and ![image](images/ch03_si69.gif)to represent the two states of diffusive-type ReRAM.

In most applications, the diffusive ReRAM is connected to a drift ReRAM serially, forming a one-selector-one-ReRAM (1S1R) structure. Such a diffusive ReRAM can work as the synapse emulator \[137\] and also the selectors \[138\]. We use SPICE simulation to characterize both of the ReRAMs in [Figure 3.10](#Chapter3.html#c03_fig10). Here we set ![image](images/ch03_si70.gif), ![image](images/ch03_si71.gif)according to \[139\] for drift-type ReRAM, and ![image](images/ch03_si72.gif), ![image](images/ch03_si73.gif), similar to the \[138\] for diffusive-type ReRAM. In the following sections, the SPICE model is used for 1S1R performance evaluation.

![image](images/PBPC0390-03-f10.jpg)

Figure 3.10 Characterization of drift ReRAM and diffusive ReRAM

### 3.2 ReRAM-crossbar structure

As mentioned above, ReRAM is a two-terminal device that can be observed in sub-stoichiometric transition metal oxides (![image](images/ch03_si74.gif)) sandwiched between metal electrodes. Such a device can be used as nonvolatile memory with state of ion resistance, which results in two nonvolatile states: HRS and LRS. One can change the state from HRS to LRS or vice versa by applying a SET voltage (![image](images/ch03_si75.gif)) or a RESET voltage (![image](images/ch03_si76.gif)).

The two states RHS and LRS represent ![image](images/ch03_si77.gif)and ![image](images/ch03_si78.gif), respectively. To read a ReRAM cell, one can apply a read voltage ![image](images/ch03_si79.gif)to the ReRAM. The ![image](images/ch03_si80.gif)and ![image](images/ch03_si81.gif)follow

![image](images/ch03_si320.gif)

where ![image](images/ch03_si82.gif)is the threshold voltage of the ReRAM.

Because of the high density of ReRAM device, one can build a crossbar structure as the array of ReRAM \[59, 140–144\]. Such crossbar structure can be utilized as memory for high-density data storage. The memory array can be read or written by controlling the voltage of wordlines (WLs) and bitlines (BLs). For example, we can apply ![image](images/ch03_si83.gif)on the ![image](images/ch03_si84.gif)WL and ![image](images/ch03_si85.gif)on the ![image](images/ch03_si86.gif)BL to write data into the ReRAM cell on ![image](images/ch03_si87.gif)row, ![image](images/ch03_si88.gif)column.

#### 3.2.1 Analog and digitized ReRAM crossbar

This section introduces the traditional analog ReRAM crossbar and the digitized ReRAM crossbar in the following. The I/O interface and the number of ReRAM device resistance value are different in these two structures.

##### 3.2.1.1 Traditional analog ReRAM crossbar

ReRAM is an emerging nonvolatile memory based on two-terminal junction devices, whose resistance can be controlled by the integral of externally applied currents. The fabric of crossbar intrinsically supports matrix–vector multiplication where vector is represented by row input voltage levels and matrix is denoted by the mesh of ReRAM resistances. In order to calculate the matrix–vector multiplication ![image](images/ch03_si89.gif). As shown in [Figure 3.11](#Chapter3.html#c03_fig11), by configuring ![image](images/ch03_si90.gif)into the ReRAM crossbar and setting ![image](images/ch03_si91.gif)as the crossbar input, the analog computation can be achieved by ReRAM crossbar directly with output ![image](images/ch03_si92.gif).

![image](images/PBPC0390-03-f11.jpg)

Figure 3.11 Traditional analog-fashion ReRAM crossbar with ADC and DAC

However, such an analog ReRAM-crossbar has two major drawbacks. First, the programming of continuous-valued ReRAM resistance is practically challenging due to large ReRAM process variation. Specifically, the ReRAM resistance is determined by the integral of current flowing through the device, which leads to a switching curve as shown in [Figure 3.12](#Chapter3.html#c03_fig12)(a). With the process variation, the curve may shift and leave intermediate values very unreliable to program, as shown in [Figure 3.12](#Chapter3.html#c03_fig12)(b). Second, the analog-to-digital converter (ADC) and digital-to-analog converter (DAC) are both time-consuming and power-consuming. In our simulation, the analog-to-digital and digital-to-analog conversion may consume up to 85.5% of total operation energy in 65 nm as shown in [Figure 3.13](#Chapter3.html#c03_fig13).

![image](images/PBPC0390-03-f12.jpg)

Figure 3.12 (a) Switching curve of ReRAM under device variations. (b) Programming inaccuracy for different ReRAM target resistances

![image](images/PBPC0390-03-f13.jpg)

Figure 3.13 (a) Power consumption of analog-fashion ReRAM crossbar. (b) Area consumption of analog-fashion ReRAM crossbar

##### 3.2.1.2 Digitalized ReRAM crossbar

To overcome the aforementioned issues, a fully digitalized ReRAM crossbar for matrix-vector multiplication. First, as ON-state and OFF-state are much more reliable than intermediate values shown in [Figure 3.12](#Chapter3.html#c03_fig12), only binary values of ReRAM are allowed to reduce the inaccuracy of ReRAM programming. Second, a pure digital interface without A/D conversion is deployed.

In ReRAM crossbar, We use ![image](images/ch03_si93.gif)and ![image](images/ch03_si94.gif)to denote voltage on ![image](images/ch03_si95.gif)th WL and ![image](images/ch03_si96.gif)th BL. ![image](images/ch03_si97.gif)and ![image](images/ch03_si98.gif)denote the resistance of LRS and HRS, respectively. In each sense amplifier (SA), there is a sense resistor ![image](images/ch03_si99.gif)with fixed and small resistance. The relation among these three resistance is ![image](images/ch03_si100.gif). Thus, the voltage on ![image](images/ch03_si101.gif)th BL can be presented by

![image](images/ch03_si321.gif)

where *g*[*ij*] is the conductance of *R*[*ij*].

The key idea behind digitalized crossbar is the use of comparators. As each column output voltage for analog crossbar is continuous-valued, comparators are used to digitize it according to the reference threshold applied to SA

![image](images/ch03_si322.gif)

However, the issue that rises due to the digitalization of analog voltage value is the loss of information. To overcome this, three techniques can be applied. First, multi-thresholds are used to increase the quantization level so that more information can be preserved. Second, the multiplication operation is decomposed into three suboperations that binary crossbar can well tackle. Third, the thresholds are delicately selected at the region that most information can be preserved after the digitalization.

Compared to the traditional analog ReRAM-crossbar \[145, 146\], the advantages of the digital ReRAM-crossbar are the following:

*   It has better programming accuracy of the ReRAM device under process variation with no additional ADC conversation as well.
*   Since only LRS and HRS are configured in digital ReRAM crossbar, it does not require high HRS/LRS ratio so that low-power (high LRS) device \[139\] can be applied. In addition, the wire resistance affects little on IR-drop when using the low-power ReRAM device.
*   The binary input voltage has a better robustness on the IR-drop in large-size crossbar.

However, the area and energy consumption of ReRAM devices will increase in the digital ReRAM-crossbar implementation. It will also be discussed in [Section 3.5](#Chapter3.html#c03_sec5).

#### 3.2.2 Connection of ReRAM crossbar

There are three approaches for the connection of ReRAM crossbar: direct-connected ReRAM, one-transistor-one-ReRAM (1T1R), and 1S1R. These approaches are described in-detail along with the differences among them.

##### 3.2.2.1 Direct-connected ReRAM

Direct-connected ReRAM, also known as the passive ReRAM array, which is a crossbar structure with only ReRAM devices. Every WL and BL are connected with a single drift-type ReRAM. The structure of direct-connected ReRAM is shown in [Figure 3.14](#Chapter3.html#c03_fig14)(a), and here we use ![image](images/ch03_si104.gif)WL (![image](images/ch03_si105.gif)) and ![image](images/ch03_si106.gif)BL (![image](images/ch03_si107.gif)) as an example. To perform a write operation, one needs to apply a write voltage ![image](images/ch03_si108.gif)between ![image](images/ch03_si109.gif)and ![image](images/ch03_si110.gif). In this case, the ReRAM connecting them (![image](images/ch03_si111.gif)) can be precisely configured.

![image](images/PBPC0390-03-f14.jpg)

Figure 3.14 Comparison of ReRAM-crossbar implementation among (a) direct connection with sneak path; (b) 1T1R with extra control signals; (c) proposed sneak-path-free 1S1R without extra control signals; (d) comparison of analog and digital interfaces

However, a problem exists in this structure that sneak path may occur. In this example, the purple path is the ideal current path we want to have, but there may be another path identified by green. This path consists of ![image](images/ch03_si112.gif), ![image](images/ch03_si113.gif)and ![image](images/ch03_si114.gif)so that we can see a ![image](images/ch03_si115.gif)is also applied on the serial of these three ReRAMs. In some of the cases, two of them are in LRS and one of them is in HRS, causing a very large voltage applied on the ReRAM device in HRS. In this case, the status of this ReRAM may also be configured, which we do not want it happens.

To overcome the sneak-path issue, a solution is proposed in \[147–149\] that we can applied a constant voltage on the rest of WLs and BLs. Here, the target WL and BL are applied with ![image](images/ch03_si116.gif)and ![image](images/ch03_si117.gif), respectively. Meanwhile, we also apply ![image](images/ch03_si118.gif)V on all the inactive lines. This solution has two requirements for the device and controller design:

*   The nonlinearity of ReRAM device should be very good since the device cannot be configured with a ![image](images/ch03_si119.gif)drop.
*   The external CMOS controller needs to output multiple voltages for all lines at the same time. In addition, the amplitude of voltage of all the lines should be independent.

##### 3.2.2.2 One-transistor-one-ReRAM

In 1T1R structure, an NMOS transistor in connected with each ReRAM device serially indicated in \[145\]. As a result, each WL is connected to a BL with one transistor and one ReRAM, as shown in [Figure 3.14](#Chapter3.html#c03_fig14)(b). The NMOS transistor is used as a voltage-controlled selector so that we can configure the connectivity of each ReRAM cell. The major benefit of 1T1R is to avoid the sneak path in the direct-connected structure. In [Figure 3.14](#Chapter3.html#c03_fig14)(b), we use one signal to control the transistors connecting to the same WL. It is clear that we only need to apply voltage on the target ![image](images/ch03_si120.gif), ![image](images/ch03_si121.gif)and only put ![image](images/ch03_si122.gif)to high, only the target cell can be configured. The metric of this structure can be summarized as follows:

*   Low requirement on the nonlinearity of ReRAM device because voltage is only applied on the target cell.
*   The controller design is much more easier than the direct-connected structure.

However, the 1T1R structure still has a disadvantage that the crossbar array area depends on the transistor, which is not scalable compared to ReRAM device. Therefore, it is not a good option when the size of ReRAM crossbar is large.

##### 3.2.2.3 One-selector-one-ReRAM

A sneak-path-free digital ReRAM-crossbar is shown in [Figure 3.14](#Chapter3.html#c03_fig14)(c). In this architecture, every drift-ReRAM is connected in serial with a diffusive ReRAM as selector. Compared to the previous two implementations, the 1S1R can remain good scalability and eliminate sneak path without additional controllers. Compared to \[150\], the ![image](images/ch03_si123.gif)of selector can only affect little to the operation on digital ReRAM. Since ![image](images/ch03_si124.gif)as shown in [Figure 3.10](#Chapter3.html#c03_fig10), the static resistance of 1S1R is almost equal to ![image](images/ch03_si125.gif). In addition, the majority of applied voltage is on the selector device when it is OFF. Since each sneak path will connect to at least three 1S1Rs, the operating voltage ![image](images/ch03_si126.gif)only needs to satisfy the following equation to eliminate the sneak path:

![image](images/ch03_si323.gif)

We will further discuss about the simulation results regarding the sneak-path-free effect in Section 3.7.5.

### 3.3 ReRAM-based oscillator

Oscillatory behavior in ReRAM device has been observed in \[151, 152\], and it is performed by the forming process of a drift-type ReRAM. The recent diffusive-type ReRAM \[137, 138\] shows the feasibility as oscillators. The ReRAM-based oscillator can be built as shown in [Figure 3.15](#Chapter3.html#c03_fig15)(a). In this ReRAM-based oscillator, a physical resistor ![image](images/ch03_si127.gif)is in series with the ReRAM device. The output voltage will depend on the proportion of ![image](images/ch03_si128.gif)and ReRAM resistance ![image](images/ch03_si130.gif). With the charge/discharge of capacitor ![image](images/ch03_si131.gif), the output voltage ![image](images/ch03_si132.gif)will be approaching ![image](images/ch03_si133.gif). To make the oscillation work, we have the following requirements for the ReRAM device in the structure:

*   At a relatively high voltage ![image](images/ch03_si134.gif), the resistance of the ReRAM ![image](images/ch03_si135.gif)decreases significantly to ![image](images/ch03_si136.gif).
*   If we drop the voltage to a low value ![image](images/ch03_si137.gif), ![image](images/ch03_si138.gif)will increase to ![image](images/ch03_si139.gif).

![image](images/PBPC0390-03-f15.jpg)

Figure 3.15 (a) ReRAM-based oscillator schematic; (b) simulation result of oscillator; (c) DFT analysis of oscillator; (d) oscillatory frequencies vs. different ![image](images/ch03_si129.gif)values

Therefore, we can build up the oscillation if all the parameters in [Figure 3.15](#Chapter3.html#c03_fig15)(a) are well-fitted, following

![image](images/ch03_si324.gif)

where ![image](images/ch03_si140.gif)and ![image](images/ch03_si141.gif)are, respectively, the low resistance and high resistance of the ReRAM device. As a result, ![image](images/ch03_si142.gif)and ![image](images/ch03_si143.gif)cannot be in a static state with the condition stated in (3.12). When the ReRAM turns from ![image](images/ch03_si144.gif)to ![image](images/ch03_si145.gif)or vice versa, a negative resistance effect is performed. Moreover, the oscillatory frequency is determined by the value of ![image](images/ch03_si146.gif). The ReRAM model for oscillator according to \[153\] is built for case study, and one can observe the oscillation result in [Figure 3.15](#Chapter3.html#c03_fig15)(b). [Figure 3.15](#Chapter3.html#c03_fig15)(c) shows the Discrete Fourier transform (DFT) analysis of [Figure 3.15](#Chapter3.html#c03_fig15)(b). [Figure 3.15](#Chapter3.html#c03_fig15)(d) shows the oscillatory frequencies vs. different ![image](images/ch03_si147.gif)values. With higher ![image](images/ch03_si148.gif), there is less current passing through the oscillator such that the charge/discharge will be slower, resulting in lower oscillatory frequency.

### 3.4 Write-in scheme for multibit ReRAM storage

#### 3.4.1 ReRAM data storage

Electrical engineers are quite familiar with circuits which include the three basic passive circuit elements—resistor, capacitor and inductor. However, for the first time, in 1971 Leon Chua proposed a fourth circuit element, describing the relation between charge (![image](images/ch03_si149.gif)) and flux (![image](images/ch03_si150.gif)) \[60\]. The resistance of the so-called memristor device depends on the total charge passed through the device \[60, 154\]. In this chapter, we use the terms ReRAM and memristor interchangeably. The device characteristics of the memristor open the floor for many new fields of application \[155–159\]. One of the most important applications is, as expected, using it as a memory element. For example, \[160–162\] and others have invested considerable effort in studying the design of memristor-based memory units. The main advantage of using memristors is given by the fact that in a modern chip, the number of transistors required to store data (e.g., in an SRAM) has a significant—and increasing—impact on the total transistor count \[163\]. In consequence, implementation of new memory architectures by using memristors would decrease the total amount of device leakage current dramatically \[161\].

Since HP developed the first passive memristor in 2008 \[62\], there have been works on single-bit \[160–162, 164\] and multibit \[165, 166\] memory storages. The unique ![image](images/ch03_si151.gif)–![image](images/ch03_si152.gif)characteristic of memeristors, however, leads to a nonlinear ![image](images/ch03_si153.gif)–![image](images/ch03_si154.gif)characteristic, which makes it difficult to determine the pulse size for achieving a certain state \[165, 166\]. Therefore, it has been seen as a problem for multilevel memory designs \[165, 166\]. To overcome this problem, researchers have developed methods, some fairly complicated, which use analog circuits and Opamps for both reading and writing \[165, 166\]. Using Opamps and analog circuits for readout seems to be inevitable \[160, 165, 166\]. However, as we will present, the aforementioned characteristic can be taken advantage of, to store more than one bit in memristors, using circuits which are compatible with digital designs. These circuits are hence less complex. Although digital bit streams have been used for setting synaptic values \[167\], the exact stored value and recovery of the stored value are not of high importance in such applications. In memory applications, on the other hand, this is of paramount importance. Therefore, in this chapter, we discuss the reliability of the storage and readout, as well as how encoding can help improving these parameters.

The rest of this chapter is organized as the following: In the next section, we briefly review the aforementioned unique characteristics of memristor and show how it can be taken advantage of, in order to store more than one bit in each memristor. In [Section 3.4.3](#Chapter3.html#c03_sec4-3), we present the digital writing method for storing two bits of data on a single memristor, as well as the readout circuit. Then, in [Section 3.4.4](#Chapter3.html#c03_sec4-4), we show the results of our simulations which confirm the feasibility of the proposed approach. In [Section 3.4.5](#Chapter3.html#c03_sec4-5), we improve the reliability of the storage, and the number of stored bits, using different proposed encoding schemes, especially regarding practical implementations and further verification of the proposed approach.

#### 3.4.2 Multi-threshold resistance for data storage

It is a well-established phenomenon in the literature that the resistance of a memristor depends on the charge flown through it \[160, 168\]. This can be modeled in various ways, one of the most prominent of which is \[168\]:

![image](images/ch03_si325.gif)

where ![image](images/ch03_si155.gif)and ![image](images/ch03_si156.gif)are the maximum and minimum resistance of the memristor, and ![image](images/ch03_si157.gif)is the charge flown through the memristor with the initial value of ![image](images/ch03_si158.gif). Finally, ![image](images/ch03_si159.gif)is a constant which represents physical characteristics of the device such as doping of the semiconductor and its size.

According to (3.13), not only the resistance, but also changes of the resistance in a memristor due to identical voltage pulses depend on its current state \[165, 169\]. This characteristic seen as a hardship \[165, 166\] can be turned into an opportunity based on the following theorem.

***Theorem:*** *Distinct output resistances correspond to distinct input patterns, which allows storage of more than one bit in a single memristor.*

***Short Proof**[\*](#Chapter3.html#c03_fn1)*: Assume two distinct states A and B, seen in [Figure 3.16](#Chapter3.html#c03_fig16), with unequal resistance of ![image](images/ch03_si160.gif), where ![image](images/ch03_si161.gif). Now, we are interested in finding out the ratio of resistance change at these two points, due to the application of an input voltage pulse with the amplitude of ![image](images/ch03_si162.gif)and width of ![image](images/ch03_si163.gif). Based on Ohm's law, we have

![image](images/ch03_si326.gif)

where ![image](images/ch03_si164.gif)of the memristor is given by (3.13). Solving this equation is rather complicated and out of the scope of this chapter. Therefore, in a simplified manner, we estimate the changes of resistance at each point by its slope, ![image](images/ch03_si165.gif). In other words, in the vicinity of point ![image](images/ch03_si166.gif), we estimate (3.13) by

![image](images/ch03_si327.gif)

![image](images/PBPC0390-03-f16.jpg)

Figure 3.16 Resistance of a memristor as a function of the charge stored in it

By substituting (3.15) into (3.14), and integrating over the period, ![image](images/ch03_si167.gif), we have \[169\]

![image](images/ch03_si328.gif)

Solving (3.16), we obtain

![image](images/ch03_si329.gif)

where

![image](images/ch03_si330.gif)

On the other hand, we can easily infer from (3.15) that ![image](images/ch03_si168.gif). Based on this, the ratio of resistance change due to charge change at point A and B is

![image](images/ch03_si331.gif)

This shows how the change of resistance of memristors at different stages due to identical pulses depends on its state (resistance) at the time. This ratio could be further simplified and approximated to the resistance ratio only \[169\].

Now, assuming that a positive pulse presents “1” and a negative pulse presents “0,” if a memristor is fed by a positive input pulse followed by a negative input pulse (“10”), it will reach a different state (“A![image](images/ch03_si169.gif)”), compared to the case where the negative pulse is applied before the positive pulse (“01” and hence A![image](images/ch03_si170.gif)). The rationale behind it is that the resistance change due to an initial negative pulse (A to A![image](images/ch03_si171.gif)) is different compared to the resistance change due to the same pulse, once the state of memristor has changed due to a previous positive pulse (A![image](images/ch03_si172.gif)to A![image](images/ch03_si173.gif)). The same holds for changes due to positive pulses in two different states (A![image](images/ch03_si174.gif)to A![image](images/ch03_si175.gif)versus A to A![image](images/ch03_si176.gif)). Therefore, we can conclude that, since the states of the memristor after application of “01” and “10” are different, based on the state of the memristor, its original input can be retrieved \[169\]. This will be verified in the next section.

#### 3.4.3 Write and read

Based on the aforementioned concept, in this section, we present our read and write method and simulate them in [Section 3.4.4](#Chapter3.html#c03_sec4-4), to test the feasibility of successfully recovering a data value which was stored through digital streaming. For the array architecture, isolation and access to the memory cell, a 1T1R architecture similar to \[166\] is assumed. Since the Opamp (comparator) is the crucial part of the circuit determining the feasibility and reliability of this implementation, we have used a model of an existing off-the-shelf Opamp, namely LT1012, which takes into account nonideal characteristics such as offset.

##### 3.4.3.1 Write-in method

As previously discussed in order to distinguish the “1” input and “0” input, respectively, positive and negative pulses are used, which can be implemented through simple switches to reference voltages. This eliminates the need for the complex circuit proposed in \[165\] or the DAC used in \[166\]. The magnitude of these pulses for the current experiment is 0.5 V and the pulse widths are 10 ms. The inputs were applied based on the most-significant-bit first and the least-significant-bit last.

[Table 3.2](#Chapter3.html#c03_tbl2) shows the data to be stored and the resulting state of the memristor (resistance) due to these inputs. This table shows that, as expected, different input data patterns lead to different states for the memristor. Similar to \[166\], the thermometer readout codes at this column can be later converted to the normal binary representation (similar to the left-most column) using simple digital logic circuits. Only one instance of such a circuit will be necessary for each memory block containing hundreds to thousands of memristor cells. Therefore, the cost of the additional hardware is negligible.

Table 3.2 Data to be stored on the memristor, resulting states and expected unencoded readouts

| Data || ![image](images/ch03_si177.gif)(k![image](images/ch03_si178.gif)) || Exp. readout |
| --- | --- | --- |
| “00” || 5.213 || “000” |
| --- | --- | --- |
| “01” || 5.108 || “001” |
| “10” || 4.890 || “011” |
| “11” || 4.778 || “111” |

##### 3.4.3.2 Readout method

For retrieving the stored data, \[160\] uses an Opamp-based circuit, \[166\] uses an ADC, and \[165\] uses a circuit inspired by ADCs. In this chapter, as shown in [Figure 3.17](#Chapter3.html#c03_fig17), we also use a circuit inspired by flash ADCs. In this circuit, after the inputs are applied and the data are stored in the memristor, the input source is disconnected. Then, after applying a controlled current pulse (here a rectangular pulse with the magnitude of 1 A and width of 1 ms), the resulting voltage across the memristor is buffered and fed to three comparator circuits (only one of which is shown at the bottom of [Figure 3.17](#Chapter3.html#c03_fig17), for simplicity). The voltage across the memristor is then compared with the voltage produced by applying a similar current pulse to predetermined resistance values. If the voltage across the predetermined resistors (R![image](images/ch03_si180.gif)) is greater than the voltage read from the memristor, the comparator will flip to high output and a “1” will be stored in the respective flip-flop output (RD![image](images/ch03_si181.gif)). This implies that the resistance of the cell is below the respective resistor, R![image](images/ch03_si182.gif).

![image](images/PBPC0390-03-f17.jpg)

Figure 3.17 For reading out, ![image](images/ch03_si185.gif)is fed to three comparators connected to D flip-flops which provide ![image](images/ch03_si186.gif)bits (for simplicity, only one set is depicted)

We note that the readout current pulse is chosen to be significantly smaller than input pulses, so that it would have a smaller effect on the state of the memristor. Nevertheless, however small this effect is, it needs to be compensated for. Therefore, similar to \[160, 166\], by applying another controlled pulse in the reverse direction, this effect can be compensated for. The advantage of using current pulses, compared to the voltage pulses used in \[160, 166\], is that the effect of positive and negative current pulses on the resistance change will be similar, whereas as proved in [Section 3.4.2](#Chapter3.html#c03_sec4-2), it is not the case for voltage pulses. That is, a negative voltage pulse, due to inherent characteristics of the memristor and its nonlinear voltage–current relationship, cannot precisely compensate a positive voltage pulse and will leave residual extra charges (positive or negative). Therefore, the state of memristor needs to be checked and more often refreshed to compensate the residual charges as well.

Using current sources, as proposed here, the complex method of readout effect elimination is reduced to an automatic compensation through a reverse current pulse, which is considerably simpler than the one used in \[165\]. Automatic refreshing may lead to extra power consumption; however, it eliminates the state-read operation or counting process for the refreshing proposed in \[166\]. Therefore, it is going to be simpler. We note that this technique may not prove efficient for all types of memristor technologies (e.g., for non-TiO![image](images/ch03_si187.gif)memristors) or scenarios (e.g., for power-constrained applications). Therefore, in order to compensate for the destructive effect of uncompensated readouts (for power critical applications or where this technique is not efficient), other scenarios, as discussed in \[166\], can be employed to compensate for the readout effect.

#### 3.4.4 Validation

In order to evaluate the practicality of the proposed approach in storing data in memristors, we have simulated the proposed circuit in LTSPICE. We have used the most prominent model (namely, Biolek's \[168\]) of TiO![image](images/ch03_si187.gif)memristors, described by (3.13). The following values were used for the model parameters (as given by the authors \[168\]); ![image](images/ch03_si188.gif), ![image](images/ch03_si189.gif), ![image](images/ch03_si190.gif)and ![image](images/ch03_si191.gif). Input signals last 10 and 1 ms, respectively, for input voltages and readout current pulses. The amplitudes are ![image](images/ch03_si192.gif)0.5 V for “1” and “0” input pulses and ![image](images/ch03_si193.gif)A for readout current pulses. The value of R![image](images/ch03_si194.gif)resistors used in this set of simulations are 5,170, 5,130 and 5,010 ![image](images/ch03_si195.gif)for ![image](images/ch03_si196.gif)1, 2 and 3, respectively.

Comparators and their precision play a crucial role in the practical implementation of the readout circuit, which determine to what level the small differences between states can be distinguished. To account for their nonidealities, we have used the model for an off-the-shelf Opamp, namely LT1012 (with 25 V maximum offset). This ascertains that the assumed values for parameters such as offset are realistic and accounted, i.e., this circuit can—in practice also—perform as expected.

[Figure 3.18](#Chapter3.html#c03_fig18) shows the result of simulation for a sample case, namely “01” input. In this figure, the blue curve shows the voltage across the memristor (namely ![image](images/ch03_si201.gif)) and the black curve shows the RD![image](images/ch03_si202.gif)output. For simplicity, RD![image](images/ch03_si203.gif)and RD![image](images/ch03_si204.gif)which as expected remained zero during the whole simulation are not shown. As we can see, shortly after applying the readout current at 3.1 s (zoomed-in area) the output of RD![image](images/ch03_si205.gif)turns to “1.”

![image](images/PBPC0390-03-f18.jpg)

Figure 3.18 Simulation results for “01” input. Shortly after applying the readout current at 3.1 s (zoomed in), the output of RD![image](images/ch03_si198.gif)flips to “1” representing the stored data. RD![image](images/ch03_si199.gif)and RD![image](images/ch03_si200.gif)remained zero and are not shown for simplicity

This and other simulations for all outputs satisfied the expected outputs as shown in [Table 3.2](#Chapter3.html#c03_tbl2), where the expected outputs represent “RD![image](images/ch03_si206.gif)& RD![image](images/ch03_si207.gif)& RD![image](images/ch03_si208.gif)” combination. Once these values are obtained, different inputs are distinguished properly and with simple logic circuits, these outputs can be turned into binary values once again. This proof of concept confirms the feasibility of digital streaming approach for storing, and successfully retrieving two bits of information on a single memristor.

#### 3.4.5 Encoding and 3-bit storage

In this section, we present the impact of the range of the memristor and the encoding of data on the reliability of the readout.

##### 3.4.5.1 Exploration of the memristance range

Trying to store 3 bits or more in a single memristor can have a negative impact on the reliability of the readout, due to smaller differences between resistances at different states. Expanding the range of the memristor (between ![image](images/ch03_si209.gif)and ![image](images/ch03_si210.gif)) helps in reducing the relative sensitivity. Although the relative difference in memristance between inputs with the same number of ones or zeros can be thus improved, this improvement is not necessarily proportional to the expansion of the range.

For example, in a memristor with a range of 100 ![image](images/ch03_si211.gif)–10 k![image](images/ch03_si212.gif), if the difference between “10” and “01” is 10 ![image](images/ch03_si213.gif), in a memristor with a range of 1–100 k![image](images/ch03_si214.gif), the difference—according to our simulations—can be 17 ![image](images/ch03_si215.gif). This is validated in our simulations, where two memristors are considered: memristor 1 (M![image](images/ch03_si216.gif)) with the range of 0.1–10 k![image](images/ch03_si217.gif)and memristor 2 (M![image](images/ch03_si218.gif)) with the range of 0.5–100 k![image](images/ch03_si219.gif). The pulse width is set to 100 ms, and the amplitudes are set to ![image](images/ch03_si220.gif)0.5 V for “1” and “0” inputs. Initial state of memristor is assumed to be 5 k![image](images/ch03_si221.gif). [Table 3.3](#Chapter3.html#c03_tbl3) presents the memristance value for different 3-bit data patterns.

Table 3.3 Resistance for memristors with different ranges of memristance. M![image](images/ch03_si222.gif): 0.1–10 ![image](images/ch03_si223.gif)and M![image](images/ch03_si224.gif): 0.5–100 ![image](images/ch03_si225.gif)

| Input || ![image](images/ch03_si226.gif)(k![image](images/ch03_si227.gif)) || ![image](images/ch03_si228.gif)(k![image](images/ch03_si229.gif)) |
| --- | --- | --- |
| “000” || 7.2453 || 47.2428 |
| --- | --- | --- |
| “001” || 5.8991 || 28.9629 |
| “010” || 5.8997 || 28.9710 |
| “011” || 3.9089 || 5.0033 |
| “100” || 5.8990 || 28.9600 |
| “101” || 3.9078 || 4.9898 |
| “110” || 3.9088 || 5.0014 |
| “111” || 1.0396 || 0.5000 |

For instance, the memristance difference between “011” and “101” is 1 ![image](images/ch03_si230.gif)for M![image](images/ch03_si231.gif), whereas it is 14![image](images/ch03_si232.gif)for M![image](images/ch03_si233.gif). This indicates that inputs with the same number of ones or zeros can be differentiated easier in the memristor with a wider resistance range.

Although in this way the difference is increased, it is yet small and requires complex complementary circuits, such as the one used in \[165\], to set the values precisely. It also needs precise comparators, such as the one assumed in \[166\], to read the values out. To alleviate the problem of close resistance at different states, and in order to improve reliability without using analog write-in circuits or extra circuits with extensive complexity for the readout operation, we propose two encoding schemes. These techniques lead to a significantly higher relative memristance difference between inputs with the same number of ones and zeros. As the number of memristors are not increased with encoding, the area of the memory remains constant, except for the addition of an encoder for the whole system (which is a memory block with hundreds to thousands of memory cells). Therefore, the area used for the encoder is considerably negligible.

##### 3.4.5.2 Uniform input encoding

In the first scheme, we employ a simple encoding method. In this technique, we append the most significant bit (MSB) to the end of the input, as shown in [Figure 3.19](#Chapter3.html#c03_fig19). In other words, input “100” is encoded as “100**1**.” The simulation setup is the same as stated values earlier in [Section 3.4.4](#Chapter3.html#c03_sec4-4), with memristor M![image](images/ch03_si234.gif)chosen for simulation, and initial memristance set to 5 k![image](images/ch03_si235.gif). Tables [3.4](#Chapter3.html#c03_tbl4) and [3.5](#Chapter3.html#c03_tbl5) show the effect of encoding for 2-bit input and 3-bit input data, respectively.

![image](images/PBPC0390-03-f19.jpg)

Figure 3.19 Uniform input encoding of 3-bit input data to 4-bit and 5-bit data

Table 3.4 Memristance for 2-bit input with uniform encoding

![image](images/tab3.4.jpg)

Table 3.5 Memristance for 3-bit input with two different uniform encoding schemes

![image](images/tab3.5.jpg)

[Table 3.4](#Chapter3.html#c03_tbl4) presents the memristance for raw input data and encoded data. Originally, the memristance difference between “01” and “10” is nearly 1 ![image](images/ch03_si241.gif), whereas when encoded to 3 bits, the relative memristance is nearly 1.9 k![image](images/ch03_si242.gif). As such, larger implementation errors (such as inaccuracy of reference values) and variations (of fabrication, implementation or between different cells) can be tolerated. In \[166\], a potential of up to 6% physical variation in fabrication process is observed and in \[165\], 10% memristance variation is assumed. However, given that the minimum distance between the memristance states after the proposed encoding is 19% (whereas it was 0.2% before), a flawless operation despite those variations is expected.

Similarly, the effect of encoding on 3-bit data is presented in [Table 3.5](#Chapter3.html#c03_tbl5). Here, we show the memristance when the 3-bit data is encoded to 4-bit, and 5-bit (N.B., in this case first two MSB bits are appended to the end of the data). From [Table 3.5](#Chapter3.html#c03_tbl5), we can see that the memristance difference between the two inputs of “001” and “100” for the raw (3-bit), encoded to 4-bit and encoded to 5-bit data, is, respectively, 0.1 ![image](images/ch03_si243.gif), 1.64 k![image](images/ch03_si244.gif)and 1.4 k![image](images/ch03_si245.gif). However, if we notice, the relative memristance difference between “001” and “010,” when encoded to 4-bit, is ![image](images/ch03_si246.gif)1![image](images/ch03_si247.gif). This is because the appended bits for both are the same. This difference is larger between these two inputs in the case of 5-bit encoded data. Simply because the appended bits in this case are not the same anymore. Nonetheless, in some instances, the values are still significantly close to each other which endangers a reliable retrieval of the stored data. Hence, further improvements as it follows are necessary.

##### 3.4.5.3 Nonuniform encoding

To address the problem of close values and similar appended bits in the uniform encoding scenario, we propose another encoding scheme, shown in [Table 3.6](#Chapter3.html#c03_tbl6). In this scenario, appendices were selected not based on the two MSBs, but rather such that the distance between all states is maximized. To this end, some bits are appended with two bits, some with one and some with none.

Table 3.6 Memristance for 3-bit input with nonuniform encoding, where “–” presents no input application

![image](images/tab3.6.jpg)

As we see in [Table 3.6](#Chapter3.html#c03_tbl6), using the new encoding scheme, the minimum difference between all inputs is increased to 905.6 ![image](images/ch03_si250.gif), whereas it was previously only 0.5![image](images/ch03_si251.gif)in the 4-bit encoding scheme and 2.2 ![image](images/ch03_si252.gif)in the 5-bit encoding scheme shown in [Table 3.5](#Chapter3.html#c03_tbl5). This minimum distance being always larger than 11% shows that potential physical and fabrication variations mentioned in \[165, 166\] can be tolerated by the system. Hence, using this nonuniform encoding scheme, three bits of data can be digitally streamed to a single memristor and the stored values can be reliably recovered using the readout circuit presented in [Section 3.4.3](#Chapter3.html#c03_sec4-3).

### 3.5 Logic functional units with ReRAM

Based on the characteristics of the ReRAM, we construct the logic gates using ReRAMs. This section first presents the logic OR gate, followed by AND gates.

#### 3.5.1 OR gate

Inspired from \[170, 171\], a logic OR gate is presented here. The logic OR gate using ReRAMs consists of two forward polarized memristor (FPM) ReRAMs, with one input for each ReRAM and the “minus” nodes of ReRAMs are joined together with a load at the output. The ReRAM-based OR gate is shown in [Figure 3.20](#Chapter3.html#c03_fig20)(a). The ReRAMs act as voltage divider circuit for the input, whose output voltage is given by (3.20) \[171.

![image](images/ch03_si332.gif)

where ![image](images/ch03_si253.gif)and ![image](images/ch03_si254.gif)are the memristance of ReRAM A and B, respectively, and ![image](images/ch03_si255.gif)and ![image](images/ch03_si256.gif)represent the input voltages for ReRAMs A and B, respectively. The operation of gate is explained using the following three cases.

*Case 1:* *Input “00”*: When the input on ReRAMs A and B are logic 0, both the ReRAMs will be in HRS due to FPM characteristics (![image](images/ch03_si257.gif)). The output voltage becomes same as the input, i.e., logic 0.

*Case 2:* *Input “01”*: When the input at the ReRAM A is logic 0 (![image](images/ch03_si258.gif)), ReRAM A will be in HRS, i.e., OFF state (![image](images/ch03_si259.gif)) and the input logic 1 at ReRAM B (![image](images/ch03_si260.gif)) makes the ReRAM to ON state, i.e., ![image](images/ch03_si261.gif). The output voltage based on (3.20) is modified to

![image](images/ch03_si333.gif)

![image](images/PBPC0390-03-f20.jpg)

Figure 3.20 Logic gates: (a) OR gate; (b) AND gate

Thus, the output voltage is high. A similar operation is expected for “10” input.

*Case 3:* *Input “11”*: When both the inputs are high, the ReRAMs will be in LRS (![image](images/ch03_si262.gif)) and a logic one (input) appears at the output load, as per (3.20).

#### 3.5.2 AND gate

Logic AND gates are designed similar to OR gates, but the ReRAMs are placed in RPM condition. [Figure 3.20](#Chapter3.html#c03_fig20)(b) shows the construction of AND gate using ReRAMs. The output voltage is given by (3.20). Similar to OR gate, the operation of AND gate is explained under three cases.

*Case 1:* *Input “00”*: When the input “0” is applied to a ReRAMs in RPM, both the ReRAMs are forced to switch ON simultaneously and has a resistance of ![image](images/ch03_si263.gif). The output voltage becomes same as the input, i.e., logic “0.”

*Case 2:* *Input “01”*: When logic input “0” is applied to ReRAM A and logic “1” to ReRAM B, ReRAM B will be OFF state (![image](images/ch03_si264.gif)\=![image](images/ch03_si265.gif)) and ReRAM A in ON state (![image](images/ch03_si266.gif)\=![image](images/ch03_si267.gif)). As such, the first term in (3.20) is neglected and the output voltage is given by

![image](images/ch03_si334.gif)

As ![image](images/ch03_si268.gif)![image](images/ch03_si269.gif)![image](images/ch03_si270.gif), the output voltage is close to zero, i.e., logic 0. If the negative voltage indicates logic 0, the value of ![image](images/ch03_si271.gif)will be ![image](images/ch03_si272.gif), which indicates logic zero. The same is applicable for input “10.”

*Case 3:* *Input “11”*: When both the inputs are high, output voltage becomes input voltage as per (3.20), i.e., logic 1.

It needs to be noted that the presented logic gates are inspired from \[170, 171\]. In \[170\], the output load is not considered in the circuit, which has quite significant impact on the behavior. Whereas, in \[171\], the outputs are distinguished as logic “1” or “0” based on the state of ReRAM (![image](images/ch03_si273.gif), ![image](images/ch03_si274.gif)) rather than the output voltages.

### 3.6 ReRAM for logic operations

As mentioned in the Introduction, using an memory element for storing as well as processing (logic) will help in reducing area overhead and increase in on-chip memory. In this section, we propose such a circuit, which will be used for logic as well as for storage purpose. The designed circuit is based on the logic circuits designed in Section 3.5. As an illustrative example, we show the ReRAM-based OR gate-cum-memory here.

[Figure 3.21](#Chapter3.html#c03_fig21) shows the OR gate with two ReRAMs, which can be used for multipurpose, i.e., as a ReRAM for data storage and as an OR computational element for the data stored in ReRAMs. The input for the ReRAMs is provided by the sources ![image](images/ch03_si275.gif)and ![image](images/ch03_si276.gif). To perform the logic operation (OR in this case), switches ![image](images/ch03_si277.gif)and ![image](images/ch03_si278.gif)are closed and with disconnected current source. The output of the OR gate can be clearly observed across the load, resistor ![image](images/ch03_si279.gif). The load resistor ![image](images/ch03_si280.gif)can be replaced with another ReRAM-based circuit.

![image](images/PBPC0390-03-f21.jpg)

Figure 3.21 Two input ReRAM OR gate output

To use the ReRAMs for the purpose of storage, switches ![image](images/ch03_si281.gif)and ![image](images/ch03_si282.gif)are left open (disconnect). It needs to be noted that source (![image](images/ch03_si283.gif), ![image](images/ch03_si284.gif)) must be connected to ReRAM before performing read operation. The stored data can be read from by disconnecting sources and connecting the current source. To optimize the design, one readout circuit voltage-controlled capacitors can be used to connect to ReRAMs and data can be read in time-multiplexed manner. It needs to be noted that, for the purpose of illustration, OR-based circuit is presented, and in the similar manner, other gates can also be realized.

#### 3.6.1 Simulation settings

A wide variety of models are proposed to characterize the ReRAM operation; however, in this chapter, we use the model proposed in \[168, 171\], which is built based on the physical construction. The threshold-switching type model in \[172\] is stated to be tolerant to variations \[173\]. The ![image](images/ch03_si285.gif), ![image](images/ch03_si286.gif), ![image](images/ch03_si287.gif), ![image](images/ch03_si288.gif)and ![image](images/ch03_si289.gif)for the threshold model in \[172\] is set as 1e6, 0, 100, 390 and 100, respectively. It needs to be noted that ![image](images/ch03_si290.gif)and ![image](images/ch03_si291.gif)denote the values in terms of charge, which is different from the resistance states. For the ideal ReRAM model in \[168\], the ![image](images/ch03_si292.gif), ![image](images/ch03_si293.gif)and ![image](images/ch03_si294.gif)are set as 100 ![image](images/ch03_si295.gif), 10 k![image](images/ch03_si296.gif)and 5 k![image](images/ch03_si297.gif), respectively. The Opamp used for reading out the ReRAM is LT1012. The simulations are performed in PSPICE and LTSPICE on a CPU running at 2.66 GHz with 8 GB RAM. To demonstrate the working capability of the ReRAM, we considered the pulse widths of 5 and 10 ms. Simulations can as well be performed at ns scale, but with the proper tuning of the parameters. Majorly ![image](images/ch03_si298.gif)needs to be tuned, as suggested by Vourkas, who built the threshold-switching ReRAM model.

#### 3.6.2 ReRAM-based circuits

In this subsection, we will present the operational characteristics of ReRAM-based logic gates and readout circuit.

##### 3.6.2.1 Logic operations

The ReRAM-based OR gate is simulated in PSPICE. The load resistor is set as 10 k![image](images/ch03_si299.gif). The pulse width of input is set as 5 ms. The output of the ReRAM-based OR gate is shown in [Figure 3.22](#Chapter3.html#c03_fig22).

![image](images/PBPC0390-03-f22.jpg)

Figure 3.22 OR gate-cum-2-bit data storage using ReRAMs

In a similar manner, the simulation result for ReRAM-based AND gate is presented in [Figure 3.23](#Chapter3.html#c03_fig23). It needs to be noted that the pulse width is kept sufficiently long for better understanding.

![image](images/PBPC0390-03-f23.jpg)

Figure 3.23 Two input ReRAM AND gate output

##### 3.6.2.2 Readout circuit

Here we will present the output of the readout circuit proposed in [Section 3.4.3.2](#Chapter3.html#c03_sec4-3-2). The simulations are carried out in LTSPICE with ideal ReRAM model developed in \[168\]. The same can be carried out using the threshold switching ReRAM model in \[172\]. However, due to large number of variables, users need to take care of convergence issues and SPICE can take longer time.

For the purpose of readout, the input current pulses of smaller amplitude ![image](images/ch03_si300.gif)A is used, so that the data stored in ReRAM is not changed. The pulse width is set to 10ms. Logic “1” and “0” are set as ![image](images/ch03_si301.gif)3 V and ![image](images/ch03_si302.gif)3 V, respectively. The output of readout circuit in case of Logic “0” and “1” is shown in [Figure 3.24](#Chapter3.html#c03_fig24). One needs to observe that when the input is logic “1,” the output obtained is ![image](images/ch03_si303.gif)1 V, whereas when the stored bit is logic “0,” the output is 0 V. These output values can be predetermined and the Opamp can be tuned to provide those voltage levels for corresponding logic “1” and “0.”

![image](images/PBPC0390-03-f24.jpg)

Figure 3.24 Value obtained from read-out circuit for logic 1 and 0

#### 3.6.3 ReRAM as a computational unit-cum-memory

For the ease of understanding, the simulation results of ReRAM as OR gate-cum-memory is presented here. Simulation results using the ideal model of a ReRAM is shown, for the ease of replication by the readers and face no convergence issues due to large number of variables in threshold-type switching models. The input data is provided to the ReRAM during first 0.5 s, i.e., logic 1 is provided to one of the ReRAM and logic 0 to the other, as represented by waveforms ![image](images/ch03_si304.gif), ![image](images/ch03_si305.gif)in [Figure 3.25](#Chapter3.html#c03_fig25). The logic operation is performed first, and the corresponding result is shown by the waveform ![image](images/ch03_si306.gif). The readout of ReRAM is then carried out, and the readout data from each of ReRAMs is represented in waveforms ![image](images/ch03_si307.gif)and ![image](images/ch03_si308.gif), which indicates logic 1 and 0, respectively.

![image](images/PBPC0390-03-f25.jpg)

Figure 3.25 OR gate operation with ReRAM for inputs ‘11’ and ‘00’

It needs to be noted that the readout is performed after logic operation, to show that the readout operation by the proposed circuit did not destroy the stored data. Further, with the proper alignment of readout switches, one readout circuit can be used to read multiple ReRAMs in a serial manner.

[^(\*)](#Chapter3.html#Cc03_fn1)The full proof is provided in \[169\]. We kindly ask the readers to refer to that paper for more information on details.

### *Part II*  
**Machine learning accelerators**

## *Chapter 4*  
**The background of machine learning algorithms**

This chapter provides an introduction to the machine learning algorithms along with the optimization techniques. We first introduce support vector machines (SVMs) followed by neural networks and their variants. The applications considered as basis to illustrate these algorithms are the classification problems.

### 4.1 SVM-based machine learning

SVM is a supervised learning model with associated learning algorithms that analyze data used for classification and regression analysis. Given a set of training samples, each marked for belonging to one of two categories (considering binary classification problem), an SVM training algorithm builds a model that assigns new examples into one category or the other, making it a non-probabilistic binary linear classifier. An SVM model is a representation of the samples as points/coordinates in space, mapped so that the samples of the separate categories are distinguished with an observable/separable boundary that is as wide as possible. New incoming samples are then mapped onto the same space and predicted to belong to a category based on which side of the boundary they fall on.

In a nutshell, SVM is a binary classifier (can be extended to multiclass) that seeks the maximum-margin separating hyperplane from training samples. The type of SVMs may be different depending on the property of data. For a data that can be linearly separated, a linear SVM as shown in [Figure 4.1](#Chapter4.html#c04_fig1)(a) can be applied, where one can observe the distinguishing boundary. Otherwise, if the data cannot be linearly separated, a nonlinear SVM in [Figure 4.1](#Chapter4.html#c04_fig1)(b) is required. Nonlinear SVMs can efficiently distinguish complex data sets compared to techniques such as regression.

![image](images/PBPC0390-04-f01.jpg)

Figure 4.1 Demonstration of (a) linear SVM; (b) nonlinear SVM

As traditional SVM only provides binary classification, it is not feasible to classify multiple labels with one SVM. Therefore, multiple SVMs are needed for complex applications such as fingerprint recognition, as shown in [Figure 4.2](#Chapter4.html#c04_fig2). The test images need to go through several classifiers before SVM provides the classification result. To achieve higher performance, every SVM (at different stages) needs to provide the correct classification. This indicates the requirement to have high precision SVMs at each stage.

![image](images/PBPC0390-04-f02.jpg)

Figure 4.2 Fingerprint recognition by multiple SVMs

### 4.2 Single-layer feedforward neural network-based machine learning

In addition to SVM, there exist numerous techniques for multiclass classification. One of the prominent techniques that achieved significant success in analyzing and classifying complex data sets is the neural network. The neural networks are considered to be mammalian brain-inspired technique stemming through the utilization of artificial neurons and exploiting their interconnectivity to perform complex tasks. Given numerous available variants of neural networks, we describe prominent and widely utilized architectures and techniques here.

#### 4.2.1 Single-layer feedforward network

Present-day data analytics is mainly based on machine learning algorithms to build a model to correlate the input data with targeted output. Feature extraction from the data is performed through the neurons and their connectivity to extract the key information for data analytics in a neural network. Neural network is a popular model to utilize for data analytics applications \[174\] and usually has two computational phases: training and testing. In the training phase, the weight coefficients of the neural network model, i.e., weights determining the connectivity between neurons are determined by minimizing the error between the trial and the targeted using the training input data through backpropagation technique. In the testing phase, the neural network with determined coefficients is utilized for the classification of the new testing data.

However, the input data could be of high dimension with redundant information. To facilitate the training and minimize the redundancy in the information, feature extraction is usually needed performed to represent the characteristic data with redundancy and/or dimension reduction.

Despite reduction in the features, the training time of neural networks when applied with large amounts of data is extremely high. To speed up the training process, one needs to tackle the challenges from two perspectives. First, a general incremental machine learning architecture with the minimal tuning of parameters is seen as a solution to speed up the training phase. The proposed single-layer feedforward network (SLFN) is shown in [Figure 4.3](#Chapter4.html#c04_fig3), which is mainly based on incremental least-squares (LS) solution. Second, analyzing the key complexity of each learning step and optimizing towards a hardware friendly algorithm to explore the parallelism with minimized hardware operational complexity is another solution towards enhancing the training process. As the computations on hardware are much faster compared to that of software, exploiting the parallelism in hardware significantly speeds up the training process. Feature extraction from the input data is a pivotal process in performing classification and prediction operations, followed by learning of the data\\break distribution.

![image](images/PBPC0390-04-f03.jpg)

Figure 4.3 (a) Single-layer neural network. (b) General flow of neural network training and testing

##### 4.2.1.1 Feature extraction

In general, the features from the original data ![image](images/ch04_si1.gif)are extracted by projection,

![image](images/ch04_si314.gif)

where ![image](images/ch04_si2.gif)is the extracted feature. The projection matrix ![image](images/ch04_si3.gif)can be found with the use of principal/singular components, random embedding or convolution \[175\]. Projection matrix ![image](images/ch04_si4.gif)is computed off-line and used for dimension reduction. One can treat ![image](images/ch04_si5.gif)as a new basis to represent the columns of ![image](images/ch04_si6.gif), and remove those small redundant values to minimize the total squared reconstruction error as

![image](images/ch04_si315.gif)

One can observe intensive matrix--vector multiplications during the feature extraction as shown in ([4.1](#Chapter4.html#c04_eqn1)).

This chapter also introduces a different feature extraction approach in this section. As a step towards feature extraction, the first step is to compress raw data with reduced complexity. Image patches (subset of an image) represent small groups of nearby pixels, which are commonly used for image feature extraction. For instance, a ![image](images/ch04_si7.gif)square pixel patch is moving across the whole input image with a step of 1 pixel and further is encoded by unsupervised learned dictionary ![image](images/ch04_si8.gif)to form patches-based image representation. Pooling is performed by summing up the quarter of encoded patches to form image features for classifier. Here, the presented analysis is mainly based on SLFN but it can be also extended to linear classifiers such as LS-SVM.

The learning dictionary ![image](images/ch04_si9.gif)is determined from sparse coding, based on orthogonal matching pursuit (OMP) technique, where the key complexity arises from the incremental LS problem. After building the dictionary ![image](images/ch04_si10.gif), encoding for image patch ![image](images/ch04_si11.gif)is performed based on soft threshold ![image](images/ch04_si12.gif)as follows:

![image](images/ch04_si316.gif)

where ![image](images/ch04_si13.gif)and ![image](images/ch04_si14.gif)is the number of basis of learning dictionary ![image](images/ch04_si15.gif). ![image](images/ch04_si16.gif)is a fixed threshold and ![image](images/ch04_si17.gif)forms a patch in image representation. Therefore, in the feature learning, one can observe that the matrix—vector multiplication and sorting are the major computations.

##### 4.2.1.2 Neural network-based learning

After feature extraction, one can perform various machine learning algorithms \[53,176,177\] for data analytics. As shown in [Figure 4.3](#Chapter4.html#c04_fig3), for a typical neural network model, one needs to determine the network weights from training and then perform testing (inference). Let ![image](images/ch04_si18.gif)represent the number of features with training input ![image](images/ch04_si19.gif), where ![image](images/ch04_si20.gif)is the training data size. The extracted feature will be input to the neural network with the following relationship for the first layer output ![image](images/ch04_si21.gif):

![image](images/ch04_si317.gif)

where ![image](images/ch04_si22.gif)and ![image](images/ch04_si23.gif)are randomly generated input weight and bias formed by ![image](images/ch04_si24.gif)and ![image](images/ch04_si25.gif)between ![image](images/ch04_si26.gif); ![image](images/ch04_si27.gif)is the hidden-layer output matrix generated from the Sigmoid function ![image](images/ch04_si28.gif)for activation.

The intention of training a neural network is to minimize the error with an objective function, mathematically defined as

![image](images/ch04_si318.gif)

where ![image](images/ch04_si29.gif)is the regularized parameter and ![image](images/ch04_si30.gif)is the label of training data.

One can solve (4.5) either by iterative backward propagation method \[178\] or direct L2-norm solver method for LS problem \[53\]. The output weight can be obtained as ![image](images/ch04_si31.gif), and can be solved as

![image](images/ch04_si319.gif)

Here ![image](images/ch04_si32.gif)is formed based on ![image](images/ch04_si33.gif)and ![image](images/ch04_si34.gif). For matrix ![image](images/ch04_si35.gif), it is the solution of an LS problem, where one can adopt Cholesky decomposition to solve it \[179\]. In addition, this book also analyzes the major computations of Cholesky decomposition for LS problem, which will be discussed in Section 7.5.

As a result, in the testing phase, output node ![image](images/ch04_si36.gif)is calculated by already determined hidden node value and output weight value as

![image](images/ch04_si320.gif)

The index of the maximum value in ![image](images/ch04_si37.gif)represents the class that the test data belongs to. Based on the computation analysis on feature extraction and neural network, one can observe that matrix—vector multiplication is the dominant operation as shown in ([4.1](#Chapter4.html#c04_eqn1)), ([4.6](#Chapter4.html#c04_eqn6)) and ([4.7](#Chapter4.html#c04_eqn7)). As such, a hardware accelerator to facilitate the matrix—vector multiplication is indeed the critical requirement for the efficient machine learning-based data analytics.

##### 4.2.1.3 Incremental LS solver-based learning

The objective function in ([4.5](#Chapter4.html#c04_eqn5)) is an LS problem and can be solved using backwards propagations (BPs) or direct solution based on matrix operations. Since the target is to have incremental learning with latest training samples, iterative gradient-based BP is slow comparing to pseudo-inverse solutions \[53\], BP will not be elaborated in details. In fact, as discussed in the next sections, the discussed three-dimensional (3D) multilayer complementary metal oxide semiconductor (CMOS)-resistive random-access memory (ReRAM) architecture can accelerate the matrix—vector multiplications, which will also benefit BP-based neural network training method.

Equation ([4.6](#Chapter4.html#c04_eqn6)) shows how to obtain the output weight ![image](images/ch04_si38.gif). The symmetric positive definite matrix ![image](images/ch04_si39.gif)is decomposed into ![image](images/ch04_si40.gif).

![image](images/ch04_si321.gif)

![image](images/ch04_si41.gif)is a lower triangular matrix with diagonal elements ![image](images/ch04_si42.gif)and ![image](images/ch04_si43.gif)is a positive diagonal matrix. Such method can maintain the same memory space as Cholesky factorization but need not perform square root extraction, as the square root of ![image](images/ch04_si44.gif)is resolved by diagonal matrix ![image](images/ch04_si45.gif)\[180\]. Here, we use ![image](images/ch04_si46.gif)to represent the matrix decomposition at ![image](images/ch04_si47.gif)iteration (where ![image](images/ch04_si48.gif)) as follows:

![image](images/ch04_si322.gif)

where ![image](images/ch04_si49.gif)is a new column generated from new hidden node output ![image](images/ch04_si50.gif), compared to ![image](images/ch04_si51.gif). Therefore, one can determine

![image](images/ch04_si323.gif)

As a result, the ![image](images/ch04_si52.gif)and scalar ![image](images/ch04_si53.gif)for Cholesky factorization can be calculated as

![image](images/ch04_si324.gif)

where ![image](images/ch04_si54.gif)and ![image](images/ch04_si55.gif)is known from ([4.9](#Chapter4.html#c04_eqn9)), which means we can continue use previous factorization result and update only according part. Please note that ![image](images/ch04_si56.gif)is 1 and ![image](images/ch04_si57.gif)is ![image](images/ch04_si58.gif).

As a conclusion, this section presents an elaborated basic learning problem on neural network and optimize Cholesky decomposition to solve the incremental LS problem. In addition, this section indicates the major computations in an SFLN are matrix—vector multiplications such as layer output in ([4.4](#Chapter4.html#c04_eqn4)) and ([4.7](#Chapter4.html#c04_eqn7)) and also Cholesky decomposition in ([4.9](#Chapter4.html#c04_eqn9)), ([4.10](#Chapter4.html#c04_eqn10)) and ([4.11](#Chapter4.html#c04_eqn11)). Therefore, this book presents a 3D multilayer CMOS-ReRAM architecture, which is designed to accelerate matrix—vector multiplication, and can be also extended to BP-based training method, where matrix—vector operation is the major computation \[181\].

#### 4.2.2 L2-norm-gradient-based learning

##### 4.2.2.1 Multilayer neural network

A multilayer neural network-based machine learning is known for its success in many data analytic application domains ranging from prediction to image classification \[182\]. It typically has two computational stages: training stage and testing stage. During the training stage, features are extracted as aforementioned, and a neural network is built to map features to its class with trained input to determine the network coefficients. During the testing stage (inference stage), based on the trained network, the new input data are classified by choosing the closest label value of the class. The main computational bottleneck is actually from the training stage.

Given a neural network with ![image](images/ch04_si59.gif)inputs and ![image](images/ch04_si60.gif)outputs as shown in [Figure 4.4](#Chapter4.html#c04_fig4), a training set ![image](images/ch04_si61.gif)is given with ![image](images/ch04_si62.gif)number of training samples, ![image](images/ch04_si63.gif)dimensional input features and ![image](images/ch04_si64.gif)classes, and ![image](images/ch04_si65.gif)and ![image](images/ch04_si66.gif)represent ![image](images/ch04_si67.gif)th data sample and the corresponding class, respectively. There can be multiple hidden layers of neurons with a target error function in the form of L2-norm. During the training stage, the aim of neural network is to minimize the L2-norm error function with determined weights of ![image](images/ch04_si68.gif)and ![image](images/ch04_si69.gif): the input weights and output weights, respectively.

![image](images/PBPC0390-04-f04.jpg)

Figure 4.4 L2-norm-gradient-based multilayer neural network for machine learning

Usually, the hidden layer can be described with a nonlinear sigmoid activation function which maps all the values in the range ![image](images/ch04_si70.gif)calculated as

![image](images/ch04_si325.gif)

where ![image](images/ch04_si71.gif)and ![image](images/ch04_si72.gif)are trained input weights and bias; ![image](images/ch04_si73.gif)is the sigmoid function for activation. The output of the neuron network ![image](images/ch04_si74.gif)is

![image](images/ch04_si326.gif)

where ![image](images/ch04_si75.gif)is the trained output weight. The index with the maximum value will become the class during the testing stage.

The training objective function can be generally formulated a L2-norm minimization problem:

![image](images/ch04_si327.gif)

Therefore, the error objective ![image](images/ch04_si76.gif)can be minimized using an iterative gradient-descent method \[177\] with the gradient of L2-norm respecting to each weight calculated as

![image](images/ch04_si328.gif)

Each weight can be updated as

![image](images/ch04_si329.gif)

where ![image](images/ch04_si77.gif)is the learning constant that defines the step length of each iteration in the negative gradient direction. As a summary, the L2-norm-gradient-based machine learning training/testing algorithm can be observed in Algorithm 4.1.

**Algorithm 4.1:** Backpropagation training for neural network

**Input:** Training matrix ![image](images/ch04_si78.gif), target matrix ![image](images/ch04_si79.gif), number of hidden nodes ![image](images/ch04_si80.gif)and learning rate ![image](images/ch04_si81.gif)

**Output:** Neuron network input weight ![image](images/ch04_si82.gif)and output weight ![image](images/ch04_si83.gif)

1: Initial guess: ![image](images/ch04_si84.gif)and ![image](images/ch04_si85.gif); initial set ![image](images/ch04_si86.gif), learning rate ![image](images/ch04_si87.gif)

2: Perform feedforward operation, the input ![image](images/ch04_si88.gif)is fed into the network as ([4.2](#Chapter4.html#c04_eqn2)) and ([4.3](#Chapter4.html#c04_eqn3)).

3: Calculate training error on each neuron ![image](images/ch04_si89.gif).

4: Calculate gradient ![image](images/ch04_si90.gif)and ![image](images/ch04_si91.gif).

5: Update ![image](images/ch04_si92.gif)and ![image](images/ch04_si93.gif).

![image](images/ch04_si94.gif),

![image](images/ch04_si95.gif)

6: Calculate the training error ![image](images/ch04_si96.gif)with the updated weights.

7: If ![image](images/ch04_si97.gif)is larger than threshold, repeats from Step 3 and ![image](images/ch04_si98.gif).

##### 4.2.2.2 Direct-gradient-based L2-norm optimization

As shown in [Algorithm 4.1](#Chapter4.html#c04_stat1), it requires to compute the partial derivative of each weight using one forward pass through the network, following by one backward pass of the network \[177\]. Such a method is very efficient when the derivative of each weight is known. However, for a hardware-based training, the derivative is usually unknown a priori. In this algorithm, based on the L2-norm calculation, a direct-gradient computation can be realized on hardware as follows:

![image](images/ch04_si330.gif)

where ![image](images/ch04_si99.gif)is a small positive change compared to ![image](images/ch04_si100.gif). This technique is simple and accurate enough for the hardware evaluation of the L2-norm-based error functions. In the following sections, this book shows that by utilizing a coupled oscillator network and crossbar structures in ReRAM devices, forward passing through the neuron network and also the evaluation of the L2-norm error function can be extremely fast with possibly done in one clock cycle.

### 4.3 DCNN-based machine learning

In addition to multilayer neural networks, deep neural networks and deep convolutional networks have obtained higher performance when performing data-intensive and image analysis as well as complex data sets.

#### 4.3.1 Deep learning for multilayer neural network

Although the SLFN can achieve a desirable accuracy with small inference and training time, it has not been proved to handle the complex benchmarks. For instance, the recent research in \[183\] only shows an efficient performance on University of California Irvine (UCI) data set \[184\], which is still far away from the real-life problems. The study in \[185\] shows that deep learning can be applied to train a neural network with multiple layers. A simple deep learning diagram is shown in [Figure 4.5](#Chapter4.html#c04_fig5). In this figure, there are ![image](images/ch04_si101.gif)weight matrices connecting with adjacent nodes. When the output of neural network is obtained, one can update all the weights in the multilayer neural network.

The architectures of deep learning include various deep neural networks, deep convolutional neural networks (DCNNs), deep belief networks and recurrent neural networks. In the following sections, the details on the DCNN with binary weights and neurons are described.

#### 4.3.2 Convolutional neural network

[Figure 4.5](#Chapter4.html#c04_fig5) illustrates a multilayer neural network with all fully connected layers. However, usually the simple fully connected layers cannot extract enough information from input signals and hidden nodes. Therefore, the basic structure of convolutional neural network (CNN) \[186\] is applied in \[187\] and the DCNN is formed. In this architecture, the convolution layers are used to replace the fully connected layers in [Figure 4.5](#Chapter4.html#c04_fig5). In each layer, there are several convolution cores to extract different information of one input pattern.

![image](images/PBPC0390-04-f05.jpg)

Figure 4.5 Diagram of simple deep learning with full-connect layers

[Figure 4.6](#Chapter4.html#c04_fig6) shows a layer of image classification by CNN with a ![image](images/ch04_si102.gif)convolution core as an example. The dimension of input feature is ![image](images/ch04_si103.gif)and all the pixels are real valued. In this example, the multiplication between two ![image](images/ch04_si104.gif)vectors is performed for ![image](images/ch04_si105.gif)times. For the whole algorithm, there are many convolution cores and layers so that the computation complexity is large. As such, the binary convolutional neural network (BCNN) is developed to lower the bit width in the operation.

![image](images/PBPC0390-04-f06.jpg)

Figure 4.6 Example of a layer in image classification by CNN

#### 4.3.3 Binary convolutional neural network

As discussed in Section 4.3.2, the traditional direct mapping of CNN to hardware would require large and unnecessary hardware resources with poor parallelism. The recent work in \[188\] suggests a CNN using binary constraints during training. This section discusses generating a CNN model with bitwise parallelism for convolution, batch normalization, pooling function and activation function.

##### 4.3.3.1 Bitwise convolution

The convolution operation is the most time-consuming and computation-intensive operation in CNN. The binary convolution in \[188\] uses ![image](images/ch04_si106.gif)for both input features and weights, so that the floating-point matrix–vector-multiplication operation is not required. However, the negative binary weights cannot be directly realized on hardware. To avoid the negative weights, recent work \[189\] uses bitwise XNOR and bit-count operation with ![image](images/ch04_si107.gif)for hardware implementation. Thus, the bitwise CNN (bitCNN) can be mathematically represented as follows:

![image](images/ch04_si331.gif)

where ![image](images/ch04_si108.gif)and ![image](images/ch04_si109.gif)are the binary weights in ![image](images/ch04_si110.gif)th block and the binary input feature map, respectively. The ![image](images/ch04_si111.gif)is the output of the binary convolution and ![image](images/ch04_si112.gif)is defined as bitwise XNOR operation. Comparing to a real-valued CNN in the single-precision data format, since the elements of weights and feature maps can be stored in 1-bit, logic and memory resources requirement for binary convolutional (BinConv) layer can be greatly reduced. Meanwhile, it can lead to a higher parallelism as well as greater energy-efficiency improvement.

##### 4.3.3.2 Bitwise batch normalization

Next, batch normalization is required to stabilize and accelerate the training process. In the inference stage, the normalization is retained to match training process. The output of the normalization can be represented by

![image](images/ch04_si332.gif)

where ![image](images/ch04_si113.gif)and ![image](images/ch04_si114.gif)are the expectation and variance over the mini-batch, while ![image](images/ch04_si115.gif)and ![image](images/ch04_si116.gif)are learnable parameters \[190\] that scale and shift the normalized value. During the inference stage, ![image](images/ch04_si117.gif), ![image](images/ch04_si118.gif), ![image](images/ch04_si119.gif)and ![image](images/ch04_si120.gif)are all fixed to normalize the convolution output, determined during the training stage.

##### 4.3.3.3 Bitwise pooling and activation functions

To minimize the computational complexity, the pooling layer performs a downsampling across an ![image](images/ch04_si121.gif)contiguous region on the feature map output by normalization layer. Pooling is used for selecting the most significant information from the features. It also provides translation invariance and reduces the computation intensity. Two kinds of pooling schemes are commonly used in CNN. One is the max-pooling, which takes the maximum value in the pooling region. The other is average-pooling, which takes the mean value of the pooling region. The binary max-pooling for binary CNNs is applied as follows:

![image](images/ch04_si333.gif)

where ![image](images/ch04_si122.gif)and ![image](images/ch04_si123.gif)are the features before and after pooling, respectively. The binary non-linearity can be represented as The activation function to process the output of max-pooling in a binary CNN is called binarization (Binrz), which can be represented as

![image](images/ch04_si334.gif)

where ![image](images/ch04_si124.gif)is the output of the max-pooling layer and ![image](images/ch04_si125.gif)is the binarized activation generated by the ![image](images/ch04_si126.gif)th binarized layer.

To summarize pooling and binarization, the aforementioned two steps are designed to find out the sign of the maximum number in the pooling region. As such, one can do the binarization for all the numbers in the pooling region first, and then determine the maximum among them. Since the results from binarization become only ![image](images/ch04_si127.gif)or ![image](images/ch04_si127.gif), the pooling process only needs to detect whether there are any ![image](images/ch04_si127.gif)s in the region. An example with the exchange of pooling and binarization for a ![image](images/ch04_si130.gif)region is shown as follows:

![image](images/ch04_si335.gif)

Here, the ![image](images/ch04_si131.gif)real-value matrix denotes the output of batch normalization. The first path in ([4.22](#Chapter4.html#c04_eqn22)) is doing binarization first, then max-pooling, while the second path is doing it conversely. It is clear that exchanging the max-pooling and binarization will not affect the final output in the inference stage.

##### 4.3.3.4 Bitwise CNN model overview

The overall working flow of a bitwise-parallelized CNN model is shown in [Figure 4.7](#Chapter4.html#c04_fig7)(b). Each BinConv layer takes the binary feature map generated from the previous layer as input and conducts a bitwise convolution between binary feature maps and binary filter weights. The convolution output is further processed by the normalization layer before downsampling by the max-pooling layer. The downsampled feature maps are subsequently fed into Binrz layer that produces binary nonlinear activations according to the input sign.

![image](images/PBPC0390-04-f07.jpg)

Figure 4.7 Computation flow comparison between (a) conventional CNN and (b) bitwise-parallelized CNN

The training flow in Algorithm 4.2 can be summarized as follows. In the training stage, all the weights are stored in a real-valued format ![image](images/ch04_si157.gif)and binarized to ![image](images/ch04_si158.gif)during the forward pass (Line 1—7). After the forward pass, the error signal ![image](images/ch04_si159.gif)is generated by comparing the output of the network ![image](images/ch04_si160.gif)with the corresponding label ![image](images/ch04_si161.gif)(Line 9). Then the error signal ![image](images/ch04_si162.gif)is backpropagated to each previous layer to compute the weight’s gradient ![image](images/ch04_si163.gif)and feature’s gradient ![image](images/ch04_si164.gif)(Line 13—18). Note that instead of using the real-valued weights ![image](images/ch04_si165.gif)to compute the feature’s gradient of previous layer, the binarized weight is applied for gradient computation, which is indicated in Line 17. On the other hand, the value of ![image](images/ch04_si166.gif)is constrained in the range of ![image](images/ch04_si167.gif)to ![image](images/ch04_si168.gif)at each iteration to ensure the convergence (Line 21). It is different from the conventional update scheme that directly updates the weights without limiting their amplitudes.

**Algorithm 4.2:** Training flow of BNN. ![image](images/ch04_si132.gif)is the number of layers, ![image](images/ch04_si133.gif)defines the binarization, ![image](images/ch04_si134.gif)defines the binary convolution, ![image](images/ch04_si135.gif)defines the normalization and ![image](images/ch04_si136.gif)defines the ![image](images/ch04_si137.gif)max-pooling.

0: {Forward pass:}

1: **for** ![image](images/ch04_si138.gif)to **do**

2: ![image](images/ch04_si139.gif)

3: ![image](images/ch04_si140.gif)

4: ![image](images/ch04_si141.gif)

5: ![image](images/ch04_si142.gif)

6: ![image](images/ch04_si143.gif)

7: **end for**

8: ![image](images/ch04_si144.gif)

9: ![image](images/ch04_si145.gif)

10: ![image](images/ch04_si146.gif)

11: ![image](images/ch04_si147.gif)

12: ![image](images/ch04_si148.gif)

12: {Backward pass:}

13: **for** ![image](images/ch04_si149.gif)**do**

14: ![image](images/ch04_si150.gif)

15: ![image](images/ch04_si151.gif)

16: ![image](images/ch04_si152.gif)

17: ![image](images/ch04_si153.gif)

18: **end for**

18: {Weights update:}

19: **for** ![image](images/ch04_si154.gif)**do**

20: ![image](images/ch04_si155.gif)

21: ![image](images/ch04_si156.gif)

22: **end for**

The key difference between the bitwise CNN and the direct-truncated CNN using less precision bit \[191\] is illustrated as follows. The direct-truncated CNN is obtained by reducing the numerical precision in post-training phase while the bitwise CNN developed here is obtained by training with binary constraints \[188\]. As such, the direct-truncated CNN that suffers from accuracy loss in general, but the bitwise CNN retains most of the accuracy with the lowest precision. In the inference stage, only the binarized weights ![image](images/ch04_si169.gif)will be retained for much smaller storage, faster inference, higher parallelism as well as higher energy efficiency.

### 4.4 TNN-based machine learning

Previously discussed neural network compression is simply performed either by precision-bit truncation or low-rank approximation \[192—195\], which cannot maintain good balance between network compression and network accuracy. By representing dense data in high-dimensional space with natural sparsity, tensorized data formatting can significantly compress the neural network complexity without much accuracy loss \[196\]. Contrastingly, this section discusses a tensor-train-formatted neural network \[197\] during the training. The tensor-train-based decomposition and compression will be first introduced. Then, a tensorized neural network (TNN) will be discussed based on the extension of general neural network. Finally, a layer-wise training of TNN using modified alternating LS (MALS) method is further proposed. For simplicity, we illustrate the idea based on a single hidden-layer neural network and later extend it to a multilayer neural network. A tensor-train-based neural network training method is also developed with the consideration of model compression using MALS method with complexity analysis provided.

#### 4.4.1 Tensor-train decomposition and compression

Tensors are natural multidimensional generation of matrices. Here, we refer one-dimensional data as *Vectors*, denoted as ![image](images/ch04_si170.gif). Two-dimensional (2D) arrays are *matrices*, denoted as ![image](images/ch04_si171.gif)and higher-dimensional arrays are *tensors* denoted as shown in [Figure 4.8](#Chapter4.html#c04_fig8). To refer one specific element from a tensor, this chapter uses calligraphic upper letters ![image](images/ch04_si172.gif), where ![image](images/ch04_si173.gif)is the dimensionality of the tensor ![image](images/ch04_si174.gif). One can effectively reshape a 2D matrix into a four-dimensional (4D) tensor as shown in [Figure 4.8](#Chapter4.html#c04_fig8).

![image](images/PBPC0390-04-f08.jpg)

Figure 4.8 Block matrices and their representation by a 4D tensor

A ![image](images/ch04_si175.gif)\-dimensional ![image](images/ch04_si176.gif)tensor ![image](images/ch04_si177.gif)is decomposed into the tensor-train data format if the tensor core ![image](images/ch04_si178.gif)is defined as ![image](images/ch04_si179.gif)and each element is defined \[197\] as

![image](images/ch04_si336.gif)

where ![image](images/ch04_si180.gif)is the index of summation, which starts from 1 and stops at rank ![image](images/ch04_si181.gif). ![image](images/ch04_si182.gif)is for the boundary condition and ![image](images/ch04_si183.gif)are known as mode size. Here, ![image](images/ch04_si184.gif)is the core rank and ![image](images/ch04_si185.gif)is the core for this tensor decomposition. By using the notation of ![image](images/ch04_si186.gif), we can rewrite the above equation in a more compact way:

![image](images/ch04_si337.gif)

where ![image](images/ch04_si187.gif)is an ![image](images/ch04_si188.gif)matrix, a slice from the 3D matrix ![image](images/ch04_si189.gif).

Such a representation is memory-efficient to store high-dimensional data and hence with significant energy saving as well. For example, a ![image](images/ch04_si190.gif)\-dimensional tensor requires ![image](images/ch04_si191.gif)number of parameters. However, if it is represented using the tensor-train format, it takes only ![image](images/ch04_si192.gif)parameters. Thus, if one can manage to reduce the rank of each core, one can efficiently represent data with high compression rate and store them distributively. By permuting neural network weight into high-dimensional data, one can compress the neural network. Here, let us define a TNN if the weight of the neural network can be represented in the tensor-train data format. For instance, a 2D weight ![image](images/ch04_si193.gif)can be reshaped to a ![image](images/ch04_si194.gif)\-dimensional tensor ![image](images/ch04_si195.gif)by factorizing ![image](images/ch04_si196.gif)and ![image](images/ch04_si197.gif)and such tensor can be decomposed into the tensor-train data format to save storages^([1](#Chapter4.html#ch04-01)).

#### 4.4.2 Tensor-train-based neural network

To make TNN clear, this section starts with a general feedforward neural network and then extend it to the tensor-train-based neural network. For the ease of illustration, this section uses a single hidden-layer neural network as an example and the same principle can be applied to the multilayer neural network \[199—201\]. Generally, the training of a neural network is performed based on data features ![image](images/ch04_si198.gif)and labels ![image](images/ch04_si199.gif)with ![image](images/ch04_si200.gif)number of training samples, ![image](images/ch04_si201.gif)dimensional input features and ![image](images/ch04_si202.gif)classes. During the training, one needs to minimize the error function with determined weights: ![image](images/ch04_si203.gif)(at input layer) and ![image](images/ch04_si204.gif)(at output layer) for a single hidden-layer neural network^([2](#Chapter4.html#ch04-02)):

![image](images/ch04_si338.gif)

where ![image](images/ch04_si205.gif)is the trained model to perform the predictions from input.

This section mainly discusses the inference (testing) process and presents the training process later. The output of each layer is based on matrix multiplication and activation function. For instance, the output of the first layer ![image](images/ch04_si206.gif)is mathematically defined as

![image](images/ch04_si339.gif)

where ![image](images/ch04_si207.gif)is the testing data. ![image](images/ch04_si208.gif)and ![image](images/ch04_si209.gif)are the input weights and bias, respectively. Then, the neural network output for a single hidden-layer neural network is

![image](images/ch04_si340.gif)

![image](images/ch04_si341.gif)

where ![image](images/ch04_si210.gif)represents class index ![image](images/ch04_si211.gif). We approximate the prediction probability for each class by the output of neural network.

For the tensor-train-based neural network, [Figure 4.9](#Chapter4.html#c04_fig9) shows the general idea. A 2D weight is folded into a 3D tensor and then decomposed into tensor cores ![image](images/ch04_si214.gif). These tensor cores are relatively small matrices due to the small value of rank ![image](images/ch04_si215.gif)leading to a high neural network compression rate. Then, the whole neural network will be trained in the tensor-train data format.

![image](images/PBPC0390-04-f09.jpg)

Figure 4.9 Neural network weight tensorization and represented by tensor-train data format for parameter compression (from ![image](images/ch04_si212.gif)to ![image](images/ch04_si213.gif))

The TNN inference is a directly application of the tensor-train-matrix-by-vector operations \[196,197\]. We will use ![image](images/ch04_si216.gif)to discuss the forward pass of neural network. First, we rearrange ![image](images/ch04_si217.gif)to a ![image](images/ch04_si218.gif)\-dimensional tensor ![image](images/ch04_si219.gif), whose ![image](images/ch04_si220.gif)th dimension is a vector of length ![image](images/ch04_si221.gif). Here, ![image](images/ch04_si222.gif)and ![image](images/ch04_si223.gif)are defined as ![image](images/ch04_si224.gif)and ![image](images/ch04_si225.gif). Without consideration of the bias ![image](images/ch04_si226.gif)and activation function, the neural network forward pass ![image](images/ch04_si227.gif)in the tensor-train data format is

![image](images/ch04_si342.gif)

where ![image](images/ch04_si228.gif), ![image](images/ch04_si229.gif)and ![image](images/ch04_si230.gif)is a slice of cores. We use a pair ![image](images/ch04_si231.gif)to refer an index of vector ![image](images/ch04_si232.gif), where ![image](images/ch04_si233.gif). Since the fully connected layer is a special case of convolutional layer with kernel size ![image](images/ch04_si234.gif), such tensorized weights can also be applied to other convolutional layers.

This tensor-train-matrix-by-vector multiplication complexity is ![image](images/ch04_si235.gif)![image](images/ch04_si236.gif)\[196\], where ![image](images/ch04_si237.gif)is the maximum rank of cores ![image](images/ch04_si238.gif)and ![image](images/ch04_si239.gif)is the maximum mode size ![image](images/ch04_si240.gif)of tensor ![image](images/ch04_si241.gif). This can be very efficient if the rank ![image](images/ch04_si242.gif)is very small compared to general matrix—vector multiplication. It is also favorable for distributed computation on ReRAM devices since each core is small and matrix multiplication is associative.

#### 4.4.3 Training TNN

Tensor-train-based neural network is first proposed by \[196\] but its training complexity significantly increases due to the BP under the tensor-train data format. A layer-wise training provides good performance with reduced epoch number of backward propagation leading to a significant training time reduction \[200—202\]. Moreover, to perform a successful mapping of TNN, recursive training of TNN is required for the trade-off of accuracy and compression rate. Thereby, a fast layer-wise training method is developed in this chapter for TNN.

The training process of TNN is the same as general neural network layer-wise training but with the tensor-train data format. We first discuss the general training process following the training framework form \[53\] and then extend it to TNN. Given a single hidden layer with random generated input weight, the training process is to minimize:

![image](images/ch04_si343.gif)

where ![image](images/ch04_si243.gif)is the hidden-layer output matrix generated from the Sigmoid function for activation, and ![image](images/ch04_si244.gif)is a user-defined parameter that biases the training error and output weights \[53\]. The output weight ![image](images/ch04_si245.gif)is computed based on LS problem:

where ![image](images/ch04_si246.gif)and ![image](images/ch04_si247.gif)is the number of classes. ![image](images/ch04_si248.gif)and ![image](images/ch04_si249.gif).

To build a multilayer neural network, backward propagation \[199\] or layer-wise training using the auto-encoder technique \[200,201\] can be applied. An auto-encoder layer is to set the single layer output ![image](images/ch04_si250.gif)the same as input ![image](images/ch04_si251.gif)and find an optimal weight to represent itself. By stacking auto-encoder layers on the final decision layer, we can build the multilayer neural network. Algorithm 4.3 summarizes the layer-wise training with MALS method.

**Algorithm 4.3:** Layer-wise training of neural network with modified LS solver

**Input:** Input set ![image](images/ch04_si252.gif), ![image](images/ch04_si253.gif)is the input data and ![image](images/ch04_si254.gif)is the desired output depending on the layer architecture, activation function ![image](images/ch04_si255.gif), number of hidden neuron node ![image](images/ch04_si256.gif)

**Output:** Neural network weight ![image](images/ch04_si257.gif)for ![image](images/ch04_si258.gif)\-layer neural network

1: **for** ![image](images/ch04_si259.gif)**do**

2: **if** ![image](images/ch04_si260.gif)**then**

3: Factorize ![image](images/ch04_si261.gif)and ![image](images/ch04_si262.gif)(e.g., ![image](images/ch04_si263.gif)and ![image](images/ch04_si264.gif)).

4: Randomly generate tensor cores ![image](images/ch04_si265.gif), ![image](images/ch04_si266.gif)and other tensor cores to represent a tensor ![image](images/ch04_si267.gif)

5: **else**

6: Random generated ![image](images/ch04_si268.gif)following Steps 3, 4

7: Perform tensor-train-matrix-by-vector multiplication based on ([4.8](#Chapter4.html#c04_eqn8)), which equivalents to ![image](images/ch04_si269.gif)

8: Perform activation function which equivalents to ![image](images/ch04_si270.gif).

9: Compute ![image](images/ch04_si271.gif)using the MALS ![image](images/ch04_si272.gif)}.

10: Note: {For auto-encoder layers, ![image](images/ch04_si273.gif)is the activation matrix ![image](images/ch04_si274.gif)(![image](images/ch04_si275.gif)). For the decision layer, ![image](images/ch04_si276.gif)is the label matrix ![image](images/ch04_si277.gif).

11: **end if**

12: **end for**

TNN is to develop high-dimensional weights and use tensor-train decomposition method to compress it. For example, a ![image](images/ch04_si278.gif)fully connected layer can be expressed as a 4D ![image](images/ch04_si279.gif)tensor. Therefore, instead of generating a random input weight ![image](images/ch04_si280.gif), we will generate a low rank tensor ![image](images/ch04_si281.gif)by specifying the rank of each core ![image](images/ch04_si282.gif). Then the input weight can be generated as ([4.23](#Chapter4.html#c04_eqn23)) with each core ![image](images/ch04_si283.gif)randomly generated.

As discussed in the general neural network, the training of TNN requires to solve an LS problem in the tensor-train data format. For the output weight ![image](images/ch04_si284.gif)in ([4.29](#Chapter4.html#c04_eqn29)), we propose a tensor-train-based LS training method using MALS algorithm (also known as density matrix renormalization group in quantum dynamics) \[203,204\]. The MALS for minimization of ![image](images/ch04_si285.gif)is working as follows.

For the output weight ![image](images/ch04_si286.gif), we have two potential solutions to achieve tensor-train data format. One straight way is to solve the general matrix LS problem and then reshape it to a high-dimensional tensor following iterative truncated support vector decomposition (SVD) algorithm \[197\]. This is similar to high-order SVD and performance degradation is significant with relatively small compression rate. Instead, we propose a tensor-train-based LS training method using MALS algorithm (also known as density matrix renormalization group in quantum dynamics) \[203,204\].

1.  **Initialization**: Randomly initialized cores ![image](images/ch04_si287.gif)and set ![image](images/ch04_si288.gif). The process is the same as Steps 3, 4 in [Algorithm 4.3](#Chapter4.html#c04_stat3).
2.  **Sweep of cores**: Core ![image](images/ch04_si289.gif)is optimized with other cores fixed. Left-to-right sweep from ![image](images/ch04_si290.gif)to ![image](images/ch04_si291.gif).
3.  **Supercore generated**: Create supercore ![image](images/ch04_si292.gif)and find it by minimizing the LS problem ![image](images/ch04_si293.gif), reshape ![image](images/ch04_si294.gif)and ![image](images/ch04_si295.gif)to fit matrix—matrix multiplication^([3](#Chapter4.html#ch04-03)).
4.  **Split supercore**: SVD ![image](images/ch04_si299.gif), let ![image](images/ch04_si300.gif)and ![image](images/ch04_si301.gif). ![image](images/ch04_si302.gif)is determined and ![image](images/ch04_si303.gif)is updated. Truncated SVD can also be performed by removing smaller singular values to reduce ranks.
5.  **Sweep termination**: Terminate if maximum sweep times reached or error is smaller than required.

The low-rank initialization is very important to have smaller rank ![image](images/ch04_si304.gif)for each core. Each supercore generation is the process of solving LS problems. The complexity of LS for ![image](images/ch04_si305.gif)are ![image](images/ch04_si306.gif)\[204\] and the SVD compression requires ![image](images/ch04_si307.gif), where ![image](images/ch04_si308.gif), ![image](images/ch04_si309.gif)and ![image](images/ch04_si310.gif)are the rank of activation matrix ![image](images/ch04_si311.gif), the maximum rank of core ![image](images/ch04_si312.gif)and maximum mode size of ![image](images/ch04_si313.gif), respectively. By using truncated SVD, we can adaptively reduce the rank of each core to reduce the computation complexity and save memory storage.

Such tensorization can benefit from implementing large neural networks. First, by performing tensorization, the size of neural network can be compressed. Moreover, the computation load can also be reduced by adopting small tensor ranks. Second, a tensorization of weight matrix can decompose the big matrix into many small tensor-core matrices, which can effectively reduce the configuration time of ReRAM. Lastly, the multiplication of a small matrix can be performed in a highly parallel fashion on ReRAM to speed up the large neural network processing time.

[¹](#Chapter4.html#ch04_01)Interested readers can refer to \[197,198\] for more details on the tensor-train data format.

[²](#Chapter4.html#ch04_02)We ignore bias for a better illustration.

[³](#Chapter4.html#ch04_03)Details on ![image](images/ch04_si296.gif)and ![image](images/ch04_si297.gif)can be found in \[203,204\]. Since each core is 3D tensors, permuting to 2D matrix is required. Without abuse of notations, we use ![image](images/ch04_si298.gif)to represent it.

## *Chapter 5*  
**XIMA: the in-ReRAM machine learning architecture**

### 5.1 ReRAM network-based ML operations

Among different hardware architectures, resistive random-access memory (ReRAM)-based architectures are seen to be one of the efficient architectures in terms of the area, power consumption and the computational latency. In this chapter, we will introduce two types of ReRAM neural networks with focus on intensive matrix multiplication operations. ReRAM-crossbar network can be used as matrix–vector multiplication accelerator and then to illustrate the detailed mapping. The coupled ReRAM oscillator network can be applied for low-power and high-throughput L2-norm calculation.

#### 5.1.1 ReRAM-crossbar network

This section describes the matrix–vector multiplication on the binary ReRAM crossbar. It is the most popular operation in various data-analytic applications such as compressive sensing and machine learning (ML). For example, the feature extraction can be achieved by multiplying Bernoulli matrix in \[205\].

Matrix multiplication can be denoted as ![image](images/ch05_stripin_si1.gif), where ![image](images/ch05_stripin_si2.gif)and ![image](images/ch05_stripin_si3.gif)are the multiplicand matrices, and ![image](images/ch05_stripin_si4.gif)is the result matrix.

##### 5.1.1.1 Mapping of ReRAM crossbar for matrix–vector multiplication

In this section, hardware mapping of matrix multiplication on the ReRAM architecture is introduced. The logic required is a matrix–vector multiplier by the ReRAM crossbar. In general, one can utilize current merge on bitlines (BLs) to realize matrix–vector multiplication and then use an ReRAM-based flash analog–digital converter (ADC) for format conversion. Here, a three-step ReRAM-crossbar-based binary matrix–vector multiplier is presented, in which both the input and output of the ReRAM crossbar are binary data without the need of ADC. The three ReRAM-crossbar steps parallel digitizing, XOR and encoding are presented in details as follows. As the output of an ReRAM-crossbar array can be connected to the input of another ReRAM-crossbar array, one can utilize multiple ReRAM arrays in the logic block for the mappings. Here, the symbol ![image](images/ch05_stripin_si5.gif)is used to denote the result of binary matrix–vector multiplication. As such, ![image](images/ch05_stripin_si6.gif)follows

![image](images/ch05_stripin_si165.gif)

where ![image](images/ch05_stripin_si7.gif)is the maximum result. To illustrate the three-step procedure more clearly, let us consider the following matrix–vector multiplication as an illustrative example:

![image](images/ch05_stripin_si166.gif)

The output after the three-step procedure will be shown, here ![image](images/ch05_stripin_si8.gif)and ![image](images/ch05_stripin_si9.gif).

###### Parallel digitizing

The first step is called parallel digitizing, which requires ![image](images/ch05_stripin_si10.gif)ReRAM crossbars. The idea is to split the matrix–vector multiplication to multiple inner-product operations of two vectors. Each inner product is computed by one ReRAM crossbar. For each crossbar, as shown in [Figure 5.1](#Chapter5.html#c05_fig1), all columns are configured with same elements that correspond to one column in random Boolean matrix ![image](images/ch05_stripin_si11.gif), and the input voltages on wordlines (WLs) are determined by ![image](images/ch05_stripin_si12.gif). As the impedance of ReRAM ![image](images/ch05_stripin_si13.gif)(normally ![image](images/ch05_stripin_si14.gif)), current ReRAMs with high impedance are insignificant, so that the voltages on BLs approximately equal to ![image](images/ch05_stripin_si15.gif)according to (3.9), where ![image](images/ch05_stripin_si16.gif)is the number of ReRAMs in low-resistance state (![image](images/ch05_stripin_si17.gif)). The underlying assumption is that the number of columns is less than ![image](images/ch05_stripin_si18.gif)because the ON/OFF ratio is finite.

It is obvious that voltages on BLs are all identical. Therefore, the key to obtain the inner product is to set a ladder-type sensing threshold voltages for each column:

![image](images/ch05_stripin_si167.gif)

![image](images/PBPC0390-05-f01.jpg)

Figure 5.1 Parallel digitizing step of ReRAM crossbar in matrix multiplication

where ![image](images/ch05_stripin_si19.gif)is the threshold voltage for the ![image](images/ch05_stripin_si20.gif)th column. The ![image](images/ch05_stripin_si21.gif)is used to denote the output of column ![image](images/ch05_stripin_si22.gif)in ReRAM-crossbar step ![image](images/ch05_stripin_si23.gif)after sensing. Therefore, the output of a column is given by

![image](images/ch05_stripin_si168.gif)

where ![image](images/ch05_stripin_si24.gif)is the inner-product result. In other words, the first (![image](images/ch05_stripin_si25.gif)) output bits are 0 and the rest ![image](images/ch05_stripin_si26.gif)bits are 1 (![image](images/ch05_stripin_si27.gif)). In the presented example, ![image](images/ch05_stripin_si28.gif)and ![image](images/ch05_stripin_si29.gif); thus, the corresponding output ![image](images/ch05_stripin_si30.gif).

###### XOR operation for ML

The inner-product output of parallel digitizing step is determined by the position where ![image](images/ch05_stripin_si31.gif)changes from 0 to 1. The XOR takes the output of the first step and performs XOR operation for every two adjacent bits in ![image](images/ch05_stripin_si32.gif), which gives the result index. For the same example of ![image](images/ch05_stripin_si33.gif), one needs to convert the first-step output ![image](images/ch05_stripin_si34.gif)to ![image](images/ch05_stripin_si35.gif). The XOR operation based on ReRAM crossbar is shown in [Figure 5.2](#Chapter5.html#c05_fig2). According to parallel digitizing step, ![image](images/ch05_stripin_si36.gif)must be 1 if ![image](images/ch05_stripin_si37.gif)is 1. Therefore, XOR operation is equivalent to the AND operation ![image](images/ch05_stripin_si38.gif), and therefore, we have

![image](images/ch05_stripin_si169.gif)

In addition, the threshold voltages for the columns have to follow the following flow:

![image](images/ch05_stripin_si170.gif)

![image](images/PBPC0390-05-f02.jpg)

Figure 5.2 XOR step of ReRAM crossbar in matrix multiplication

Equations ([5](#Chapter5.html#c05_eqn5)) and ([6](#Chapter5.html#c05_eqn6)) show that only output of ![image](images/ch05_stripin_si39.gif)th column is 1 on the second step, where ![image](images/ch05_stripin_si40.gif)is the inner-product result. Each crossbar in XOR step has the size of ![image](images/ch05_stripin_si41.gif).

###### Encoding

The third step is to consider the output of XOR step and produce ![image](images/ch05_stripin_si42.gif)in binary format as an encoder. Therefore, ![image](images/ch05_stripin_si43.gif)should be in the binary format of ![image](images/ch05_stripin_si44.gif). In the considered example, ![image](images/ch05_stripin_si45.gif)when ![image](images/ch05_stripin_si46.gif). In the output of XOR step, as only one input will be 1 and others are 0, according binary information is stored in corresponding row, as shown in [Figure 5.3](#Chapter5.html#c05_fig3). Encoding step needs ![image](images/ch05_stripin_si47.gif)ReRAMs, where ![image](images/ch05_stripin_si48.gif)is the number of bits in order to represent ![image](images/ch05_stripin_si49.gif)in binary format. The thresholds for the encoding step are set following (6) as well.

###### Adding and shifting for inner-product result

The output of encoding step is in binary format, but some processes are needed to obtain the final inner-product result. As a result, adder and shifter are designed to complete this process as shown in [Figure 5.4](#Chapter5.html#c05_fig4). We suppose the original data is 8-bit and data dimension is ![image](images/ch05_stripin_si50.gif), the workload of adder is ![image](images/ch05_stripin_si51.gif)without any acceleration. With the three-step ReRAM-crossbar accelerator as preprocessing, the workload of adder can be significantly reduced to ![image](images/ch05_stripin_si52.gif)(![image](images/ch05_stripin_si53.gif)). Detailed comparison results will be shown in Section 5.1.1.2.

![image](images/PBPC0390-05-f03.jpg)

Figure 5.3 Encoding step of ReRAM crossbar in matrix multiplication

![image](images/PBPC0390-05-f04.jpg)

Figure 5.4 ReRAM-based inner-product operation

##### 5.1.1.2 Performance evaluation

###### Experimental application: feature extraction for fingerprint matching

Feature extraction or sparse representation is commonly applied such as in fingerprint image matching, which can be mapped with (![image](images/ch05_stripin_si54.gif)). This operation can minimize the volume of data to be stored in memory as well as minimize the complexity in data analytics applications. The following section shows how to map this operation on the digitalized ReRAM crossbar. In such a process, ![image](images/ch05_stripin_si55.gif)is the original fingerprint image, which is of high dimension with (![image](images/ch05_stripin_si56.gif)) pixels, ![image](images/ch05_stripin_si57.gif)a random Bernoulli matrix with (![image](images/ch05_stripin_si58.gif)) for feature extract and ![image](images/ch05_stripin_si59.gif)the features in low dimension with (![image](images/ch05_stripin_si60.gif)) pixels. The according dimension reduction ratio ![image](images/ch05_stripin_si61.gif)is

![image](images/ch05_stripin_si171.gif)

In the feature extraction phase of fingerprint image, the random Bernoulli matrix ![image](images/ch05_stripin_si62.gif)is with fixed elements. Therefore, the elements of the Bernoulli matrix are stored in ReRAMs of logic block, and original image as the input of logic accelerator.

###### Experimental settings

The hardware evaluation platform is implemented on a computer server with 4.0 GHz core and 16.0 GB memory. Feature extraction is implemented by general processor, complimentary metal oxide semiconductor (CMOS)-based application specific integrated circuit (ASIC), non-distributed and distributed in-memory computing based on digitalized ReRAM crossbar, respectively. For the ReRAM-crossbar design evaluation, the resistance of ReRAM is set as 1 k![image](images/ch05_stripin_si63.gif)and 1 M![image](images/ch05_stripin_si64.gif)as on-state and off-state resistance, respectively, according to \[206\]. The general processor implementation is based on MATLAB![image](images/ch05_stripin_si65.gif)simulation on computer server. A CMOS-based feature extraction design is implemented by Verilog in distributed architecture and synthesized with CMOS 65-nm low-power process design kit (PDK). The working frequency of general processor implementation is 4.0 GHz while the CMOS-ASIC feature extraction design frequency is 1.0 GHz. For in-memory computing based on the proposed ReRAM crossbar, write voltage ![image](images/ch05_stripin_si66.gif)is set as 0.8 V and read voltage ![image](images/ch05_stripin_si67.gif)is set as 0.1 V as well as duration time of 5 ns. In addition, the analog computation on ReRAM crossbar is performed for comparison based on design in \[207\].

###### General performance comparison

In this section, 1,000 fingerprint images selected from \[208\] are processed as binarization images and stored in memory with ![image](images/ch05_stripin_si68.gif)resolution. To agree with patch size, random Bernoulli ![image](images/ch05_stripin_si69.gif)matrix is with fixed ![image](images/ch05_stripin_si70.gif)and ![image](images/ch05_stripin_si71.gif)of 356 and 64, respectively. The detailed comparison is shown in [Table 5.1](#Chapter5.html#c05_tbl1) with numerical results including energy consumption and delay obtained for one image on average of 1,000 images. Here the CMOS in crossbar in-memory computation accelerator (XIMA) refers to the memory controllers.

Table 5.1 Performance comparison of matrix–vector multiplication under among software and hardware implementations

![image](images/tab5.1.jpg)

Among hardware implementations, in-memory computing based on the accelerated XIMA achieves better energy efficiency compared to CMOS-based ASIC. Non-distributed XIMA (only one data and logic block inside memory) needs fewer CMOS control buses, but large data communication overhead on a single-layer crossbar compared to distributed ReRAM crossbar. Although distributed analog ReRAM crossbar can achieve the best efficiency from energy perspective, it has larger area compared to its digital counterpart. As shown in [Table 5.1](#Chapter5.html#c05_tbl1), ReRAM crossbar in analog fashion only consumes 2.1 ![image](images/ch05_stripin_si116.gif)for one vector multiplication while the proposed architecture requires 20.15 ![image](images/ch05_stripin_si117.gif)because most of power consumption comes from ReRAM in computing instead of ADCs. However, ADCs need more area so that ReRAM crossbar with analog fashion is 8.32 ![image](images/ch05_stripin_si118.gif)while the proposed one is only 0.05 ![image](images/ch05_stripin_si119.gif)because of the high density of ReRAM crossbar.

Calculation error of analog and digitalized ReRAM crossbar are compared in [Figure 5.6](#Chapter5.html#c05_fig6), where M and N are both set as 256. Here the calculation error is the result variation of two schemes: ADC with analog ReRAM and sense amplifier with digital ReRAM. The ReRAM error rate refers to the variation of write voltage applied on the device. Calculation error is very low when ReRAM error rate is smaller than 0.004 for both analog and digitalized fashion ReRAM. However, when ReRAM error rate is larger than 0.004, calculation error of analog fashion ReRAM crossbar increases rapidly, while digitalized fashion ReRAM increases slowly. However, when ReRAM error rate reaches 0.01, calculation error rate of analog ReRAM crossbar goes to 0.25, much higher than the other one with only 0.07. As such, computational error can be reduced in the described architecture compared to analog fashion ReRAM crossbar.

###### Scalability study

Hardware performance comparison among CMOS-based ASIC and non-distributed and distributed XIMA with varying ![image](images/ch05_stripin_si120.gif)is shown in [Figure 5.5](#Chapter5.html#c05_fig5). From area consumption perspective shown in [Figure 5.5](#Chapter5.html#c05_fig5)(a), distributed ReRAM crossbar is much better than the other implementations. With increasing ![image](images/ch05_stripin_si121.gif)from 64 to 208, its total area is from 0.057 ![image](images/ch05_stripin_si122.gif)to 0.185 ![image](images/ch05_stripin_si123.gif), approximately 100![image](images/ch05_stripin_si124.gif)smaller than the other two approaches. Non-distributed ReRAM crossbar becomes the worst one when ![image](images/ch05_stripin_si125.gif). From the delay perspective, as shown in [Figure 5.5](#Chapter5.html#c05_fig5)(b), non-distributed ReRAM crossbar is the worst, as it has only one control bus and takes too much time on preparing of computing. Delay of non-distributed ReRAM crossbar grows rapidly while distributed ReRAM crossbar and CMOS-based ASIC implementation maintains on approximately 21 and 70 ![image](images/ch05_stripin_si126.gif), respectively, as the parallel design. For the energy efficiency, as shown in [Figure 5.5](#Chapter5.html#c05_fig5)(c), both non-distributed and distributed ReRAM crossbars do better as logic accelerator is off at most of time. The discussed architecture also performs the best in energy-delay product (EDP) shown in [Figure 5.5](#Chapter5.html#c05_fig5)(d). Distributed XIMA performs the best among all implementation under different specifications. The EDP is from ![image](images/ch05_stripin_si127.gif)to ![image](images/ch05_stripin_si128.gif), which is 60![image](images/ch05_stripin_si129.gif)better than non-distributed ReRAM crossbar and 100![image](images/ch05_stripin_si130.gif)better than CMOS-based ASIC.

![image](images/PBPC0390-05-f05.jpg)

Figure 5.5 Hardware performance scalability under different reduced dimension for (a) area; (b) delay; (c) energy; (d) EDP

What is more, hardware performance comparison with varying ![image](images/ch05_stripin_si131.gif)is shown in [Figure 5.7](#Chapter5.html#c05_fig7). Area and energy consumption trend is similar to [Figure 5.5](#Chapter5.html#c05_fig5). But for the computational delay, the discussed architecture cannot maintain constant delay as shown in [Figure 5.5](#Chapter5.html#c05_fig5)(b) due to larger time required to configure the input, but still the best among the three. Distributed XIMA still achieves better performance than the other two.

#### 5.1.2 Coupled ReRAM oscillator network

##### 5.1.2.1 Coupled-ReRAM-oscillator network for L2-norm calculation

In a coupled oscillator network, this chapter considers the ReRAM oscillator cell similar to the one shown in Figure 3.15(a) (![image](images/ch05_stripin_si132.gif)replaced with a PMOS). By altering the gate voltage of the PMOS, one can control the oscillatory frequency as in Figure 3.15(d). Referring to the previous works \[209, 210\], the discussed coupled-ReRAM-oscillator network is shown in [Figure 5.8](#Chapter5.html#c05_fig8)(a). Here, the oscillators are directly coupled with ReRAMs. The oscillatory frequency of each oscillator is determined by multiple input voltages. As mentioned in Figure 3.15(d), the voltage-controlled P-channel metal–oxide–semiconductor (PMOS) can be viewed as a voltage-controlled resistor. [Figure 5.8](#Chapter5.html#c05_fig8)(b) and (c) is the schematic of the oscillators with one input and multiple inputs. After directly coupling, one can have an inverter and a feedback resistor with a diode-connected NMOS. Because of the rectifying property of diode-connected NMOS, these elements guarantee that the current will only pass from the oscillator network to ![image](images/ch05_stripin_si133.gif). An RC circuit is design at ![image](images/ch05_stripin_si134.gif)so that one can measure the DC voltage of ![image](images/ch05_stripin_si135.gif). The output voltage indicates the relative synchronization of the coupled oscillators.

![image](images/PBPC0390-05-f06.jpg)

Figure 5.6 Calculation error comparison between multilevel and binary ReRAM

![image](images/PBPC0390-05-f07.jpg)

Figure 5.7 Hardware performance scalability under different original dimension for (a) area; (b) delay; (c) energy; (d) EDP

##### 5.1.2.2 Performance evaluation

The detailed evaluation of ReRAM-based oscillator is shown in [Table 5.2](#Chapter5.html#c05_tbl2). Compared with the design in \[209, 210\], it has power consumption and can be controlled by multiple voltage inputs easily. As the current through ReRAM-based oscillator is low, the working frequency of the oscillator is lower in some of the compared existing works.

![image](images/PBPC0390-05-f08.jpg)

Figure 5.8 (a) ReRAM oscillator network schematic. (b) Oscillator with single input. (c) Oscillator with multiple input

As discussed above, ![image](images/ch05_stripin_si149.gif)is charged by the oscillator network. Therefore, the capacitance of ![image](images/ch05_stripin_si150.gif)should be large enough to avoid the voltage drop at ![image](images/ch05_stripin_si149.gif). At the meantime, large capacitance leads to a large settling time. [Figure 5.9](#Chapter5.html#c05_fig9) shows the transient response with ![image](images/ch05_stripin_si152.gif), ![image](images/ch05_stripin_si153.gif), ![image](images/ch05_stripin_si154.gif)and ![image](images/ch05_stripin_si155.gif), respectively. Obviously ![image](images/ch05_stripin_si156.gif)is the best configuration because we can capture a stable output at ![image](images/ch05_stripin_si157.gif). In this simulation, the ![image](images/ch05_stripin_si158.gif)is set as ![image](images/ch05_stripin_si159.gif).

### 5.2 ReRAM network-based in-memory ML accelerator

This section introduces the different computing accelerators based on ReRAM devices. First, the distributed ReRAM-crossbar in-memory architecture (XIMA) will be illustrated in detail. The integration of ReRAM-crossbar-based storage and computing brings advantages on throughput. After that, two types of 3D CMOS-ReRAM architectures will be introduced. The major merits of the 3D architecture are less area overhead as well as higher throughput by the 3D interconnection.

Table 5.2 Detailed evaluation of ReRAM-based oscillator

![image](images/tab5.2.jpg)

![image](images/PBPC0390-05-f09.jpg)

Figure 5.9 Transient response of ReRAM oscillator network output with (a) ![image](images/ch05_stripin_si145.gif); (b) ![image](images/ch05_stripin_si146.gif); (c) ![image](images/ch05_stripin_si147.gif); (d) ![image](images/ch05_stripin_si148.gif)

#### 5.2.1 Distributed ReRAM-crossbar in-memory architecture

Conventionally, the processor and memory are separate components that are connected through I/Os. With limited width and considerable RC delay, the I/Os are considered the bottleneck of system overall throughput. As memory is typically organized in H-tree structure, where all leaves of the tree are data arrays, it is promising to impose in-memory computation with parallelism at this level. In the following section, a distributed ReRAM-crossbar in-memory architecture (XIMA) is discussed. Such an architecture can be used for several ML applications, as presented in Section 5.7.5.

##### 5.2.1.1 Memory-computing integration

As both data and logic units have uniform structure when implemented on ReRAM crossbar, half of the leaves are exploited as logic elements and are paired with data arrays. The discussed architecture is illustrated in [Figure 5.10](#Chapter5.html#c05_fig10). The distributed local data-logic pairs can form one local data path such that the data can be processed locally in parallel, without the need of being read out to the external processor.

Coordinated by the additional controlling unit called *in-pair control bus*, the in-memory computing is performed in following steps: (1) logic configuration: processor issues the command to configure logic by programming logic ReRAM crossbar into specific pattern according to the functionality required; (2) load operand: processor sends the data address and corresponding address of logic accelerator input; (3) execution: logic accelerator can perform computation based on the configured logic and obtain results after several cycles; (4) write-back: computed results are written back to data array directly but not to the external processor.

![image](images/PBPC0390-05-f10.jpg)

Figure 5.10 Overview of distributed in-memory computing architecture on ReRAM crossbar

With emphasis on different functionality, the ReRAM crossbars for data storage and logic unit have distinctive interfaces. The data ReRAM crossbar will have only one row activated at a time during read and write operations, and logic ReRAM crossbar; however, one can have all rows activated spontaneously as rows are used to take inputs. As such, the input and output interface of logic crossbar requires analog-to-digital (AD) or digital-to-analog (DA) conversions, which could outweigh the benefits gained. Therefore, in this chapter, a conversion-free digital-interfaced logic ReRAM-crossbar design is presented, which uses three layers of ReRAM crossbars to decompose a complex function into several simple operations that a digital crossbar can tackle.

##### 5.2.1.2 Communication protocol and control bus

The conventional communication protocol between external processor and memory is composed of *store* and *load* action identifier, address that routes to different locations of data arrays and data to be operated. With additional in-memory computation capacity, the presented distributed in-memory computing architecture requires modifications on the current communication protocol. The new communication instructions are proposed in [Table 5.3](#Chapter5.html#c05_tbl3), which is called in-pair control.

In-pair control bus needs to execute instructions in [Table 5.3](#Chapter5.html#c05_tbl3). SW (store word) instruction is to write data into ReRAMs in data array or in-memory logic. If the target address is in a data array, it will be a conventional write or result write-back; otherwise it will be logic configuration. LW (load word) instruction performs similar to a conventional read operation. ST (start) instruction means to switch on the logic block for computing after the computation setup has been done. WT (wait) operation is to stop reading from instruction queue during computing.

Besides the communication instructions, memory address format is also different from that in the conventional architecture. To specify a byte in the proposed architecture, address includes the following identifier segments. First, the data-logic pair index segment is required, which is taken by block decoders to locate the target data-logic pair. Second, one-bit flag is needed to clarify that whether the target address is in data array or in-memory logic crossbar. Third, if logic accelerator is the target, additional segment has to specify the layer index. Lastly, rest of address segment are row and column indexes in each ReRAM crossbar. An address example for data array and in-memory logic is shown in [Figure 5.11](#Chapter5.html#c05_fig11).

Table 5.3 Protocols between external processor and control bus

![image](images/tab5.3.jpg)

To perform logic operation, the following instructions are required to performed. First, one can store the required input data and ReRAM values with SW operation. Second, an ST instruction will be issued to enable all the columns and rows to perform the logic computing. The WT instruction is also performed to wait for the completion of logic computing. At last, LW instruction is performed to load the data from the output of ReRAM crossbar.

Given the new communication protocol between general processor and memory is introduced, one can design the according control bus as shown in [Figure 5.11](#Chapter5.html#c05_fig11). The control bus is composed of an instruction queue, an instruction decoder, an address decoder and an static random access memory (SRAM) array. As the operation frequency of ReRAM crossbar is slower than that of external processor, instructions issued by the external processor will be stored in the instruction queue first. They are then analyzed by instruction decoder on a first-come-first-serve (FCFS) basis. The address decoder obtains the row and column index from the instruction, and SRAM array is used to store temporary data such as computation results, which are later written back to data array.

#### 5.2.2 3D XIMA

##### 5.2.2.1 3D single-layer CMOS-ReRAM architecture

Recent works such as \[211–216\] have shown that the 3D integration supports heterogeneous stacking as different types of components can be fabricated separately, and layers can be stacked and implemented with different technologies. Therefore, stacking nonvolatile memories on top of microprocessors enables cost-effective heterogeneous integration. Furthermore, works in \[217–221\] have also shown the feasibility to stack ReRAM on CMOS to achieve smaller area and lower energy consumption.

![image](images/PBPC0390-05-f11.jpg)

Figure 5.11 Detailed structure of control bus and communication protocol

The discussed 3D CMOS-ReRAM accelerator is shown in [Figure 5.12](#Chapter5.html#c05_fig12)(a). This accelerator is composed of a top layer of WLs, a bottom layer of CMOS circuits and vertical connection between both layers by ReRAM. In this architecture, the ReRAM crossbar performs matrix–vector multiplication and also vector addition, as shown in [Figure 5.12](#Chapter5.html#c05_fig12)(b). Here, we use an example ![image](images/ch05_stripin_si160.gif)to show the mapping scheme of matrix–vector multiplication. The matrix ![image](images/ch05_stripin_si161.gif)needs to be stored in ReRAM crossbar by writing the corresponding resistance. To perform the computations, ![image](images/ch05_stripin_si162.gif)is converted to WL voltages and one can obtain the output current ![image](images/ch05_stripin_si163.gif)denoting ![image](images/ch05_stripin_si164.gif). One can simply convert the current to voltage and utilize the ADC for digital conversion \[147\]. The readout circuit of ReRAM crossbar is implemented by the bottom-layer CMOS. In addition, the control signals of the ReRAM crossbar and other operations (pooling, activation) are also realized by CMOS.

The 3D single-layer CMOS-ReRAM architecture will be used for tensorized neural network (TNN) in the following chapters. This book will further introduce the detailed mapping and results in Sections 6.2 and 6.2.3.

##### 5.2.2.2 3D multilayer CMOS-ReRAM architecture

Besides the 3D single-layer CMOS-ReRAM architecture, this chapter also discusses the 3D multilayer CMOS-ReRAM architecture for online ML applications as well. This 3D multilayer CMOS-ReRAM accelerator with three layers is shown in [Figure 5.13](#Chapter5.html#c05_fig13)(a). This accelerator is composed of a two-layer ReRAM-crossbar and one-layer CMOS circuit. As [Figure 5.13](#Chapter5.html#c05_fig13)(a) shows, Layer 1 of ReRAM crossbar is implemented as a buffer to temporarily store input data to be processed. Layer 2 of ReRAM crossbar performs logic operations such as matrix–vector multiplication and also vector addition, as discussed earlier. Note that buffers are designed to separate resistive networks between Layers 1 and 2. The last layer of CMOS contains read-out circuits for ReRAM crossbar and performs as logic accelerators designed for other operations besides matrix–vector multiplication, including pipelined divider, look-up table (LUT) designed for division operation and activation function in ML.

![image](images/PBPC0390-05-f12.jpg)

Figure 5.12 (a) 3D CMOS-ReRAM accelerator architecture; (b) ReRAM-based matrix–vector multiplication engine

![image](images/PBPC0390-05-f13.jpg)

Figure 5.13 (a) 3D multilayer CMOS-ReRAM accelerator architecture; (b) incremental ML algorithm mapping flow on proposed accelerator

Moreover, [Figure 5.13](#Chapter5.html#c05_fig13)(b) shows the workflow for incremental ML based on the proposed architecture. First, the detailed architecture of ML (e.g., number of layers and activation function) is determined based on the accuracy requirements and data characteristics. Second, operations of this ML algorithm are analyzed and reformulated so that all the operations can be accelerated in 3D multilayer CMOS-ReRAM architecture as illustrated in [Figure 5.13](#Chapter5.html#c05_fig13)(a). Furthermore, the bit width operating on ReRAM crossbar is also determined by balancing the accuracy loss and energy saving. Finally, logic operations on ReRAM crossbar and CMOS are configured based on the reformulated operations, energy saving and speedup.

Such a 3D multilayer CMOS-ReRAM architecture has advantages in three manifold. First, by utilizing ReRAM crossbar for input data storage, leakage power of memory is largely removed. In a 3D architecture with TSV interconnection, the bandwidth from this layer to next layer is sufficiently large to perform parallel computation. Second, ReRAM crossbar can be configured as computational units for the matrix–vector multiplication with high parallelism and low power. Lastly, with an additional layer of CMOS-ASIC, more complicated tasks such as division and nonlinear mapping can be performed. As a result, the whole training process of ML can be fully mapped to the proposed 3D multilayer CMOS-ReRAM accelerator architecture towards real-time training and testing.

The 3D multilayer CMOS-ReRAM architecture will be used for online ML (both learning and inference phases) in the following chapters. We will further introduce the detailed mapping and results in Sections 6.2 and 6.2.3.

## *Chapter 6*  
**The mapping of machine learning algorithms on XIMA**

This chapter presents the mapping of multiple machine learning applications on different resistive random-access memory (ReRAM)-based architectures discussed in Chapter 5. For each application, a detailed mapping strategy, experimental settings and evaluation results are presented here.

### 6.1 Machine learning algorithms on XIMA

First, this chapter presents a detailed mapping of several machine learning applications on distributed in-memory computing architecture (XIMA), including single-layer feedforward neural network (SLFN)-based learning, binary convolutional neural network (BCNN)-based inferences on passive array as well as One Selector One ReRAM (1s1R) array.

#### 6.1.1 SLFN-based learning and inference acceleration

The details of SLFN-based learning are presented in \[148\]. In \[148\], one maps the SLFN-based learning and inference process according to the algorithm and network in Section 4.2. In this network, matrix–vector multiplication, the major operation in machine learning on ReRAM crossbar is implemented by three steps with detailed mapping strategy for each step. The process of mapping of ![image](images/ch06_si1.gif)to ReRAM is shown in Figure 4.3 as example.

In matrix–vector multiplication, let us assume the output matrix is ![image](images/ch06_si2.gif). For better understanding, we replace ![image](images/ch06_si3.gif)with ![image](images/ch06_si4.gif)and ![image](images/ch06_si5.gif)with ![image](images/ch06_si6.gif), and the equation becomes ![image](images/ch06_si7.gif). For every element in ![image](images/ch06_si8.gif), it follows

![image](images/ch06_si940.gif)

where ![image](images/ch06_si9.gif)and ![image](images/ch06_si10.gif)are the elements in ![image](images/ch06_si11.gif)and ![image](images/ch06_si12.gif), respectively. The calculation of ![image](images/ch06_si13.gif)by four-step ReRAM crossbar is shown in the following subsections.

##### 6.1.1.1 Step 1. Parallel digitizing

The first step parallel digitizing requires an ![image](images/ch06_si14.gif)ReRAM crossbar. The idea is to split the matrix–vector multiplication to multiple inner-product operations of two vectors. Each inner product is produced ReRAM crossbar as shown in [Figure 6.1](#Chapter6.html#c06_fig1)(a). ![image](images/ch06_si15.gif)is set as crossbar input and ![image](images/ch06_si16.gif)is written in ReRAM cells. In ![image](images/ch06_si17.gif)ReRAM crossbar, resistance of ReRAMs in each column is the same, but ![image](images/ch06_si18.gif)among columns are different. We have

![image](images/ch06_si941.gif)

which are ladder-like threshold voltages to identify the result. If the inner-product result is ![image](images/ch06_si19.gif), the output of columns will be

![image](images/ch06_si942.gif)

![image](images/PBPC0390-06-f01.jpg)

Figure 6.1 Detailed mapping for digitalized matrix–vector multiplication: (a) parallel digitizing; (b) XOR 2; (c) encoding; (d) legend of ReRAM mapping

##### 6.1.1.2 Step 2. XOR

The second step is exclusive OR (XOR) to identify the index of ![image](images/ch06_si20.gif)where ![image](images/ch06_si21.gif)and ![image](images/ch06_si22.gif), so the operation is ![image](images/ch06_si23.gif). According to (6.3), the case ![image](images/ch06_si24.gif)and ![image](images/ch06_si25.gif)is impossible, so the XOR operation can be converted to ![image](images/ch06_si26.gif)and ![image](images/ch06_si27.gif). The mapping of ReRAM-crossbar input and resistance in this step is shown in [Figure 6.1](#Chapter6.html#c06_fig1)(b), and threshold voltage configuration is

![image](images/ch06_si943.gif)

Therefore, only the output of ![image](images/ch06_si28.gif)th column is ![image](images/ch06_si29.gif)and the others are ![image](images/ch06_si30.gif).

##### 6.1.1.3 Step 3. Encoding

The third step takes the output of XOR step and produces ![image](images/ch06_si31.gif)in binary format as an encoder. The input of ReRAM crossbar is from the second step and only one input is ![image](images/ch06_si32.gif), so that according binary format is stored in corresponding row, as shown in [Figure 6.1](#Chapter6.html#c06_fig1)(c). Encoding step needs an ![image](images/ch06_si33.gif)ReRAM crossbar, where ![image](images/ch06_si34.gif)is the number of bits in order to represent ![image](images/ch06_si35.gif)in binary format. The thresholds for the encoding step are set following (4) as well.

##### 6.1.1.4 Step 4. Adding and shifting for inner-product result

The output of encoding step is in binary format, but some processes are needed to obtain the final inner-product result ([Figure 6.2](#Chapter6.html#c06_fig2)). Adder and shifter are designed to complete this process as shown in [Figure 6.1](#Chapter6.html#c06_fig1)(d). Let us consider the original data are 8-bit and data dimension is ![image](images/ch06_si36.gif), the workload of adder is ![image](images/ch06_si37.gif)without any acceleration for the purpose of illustration. With four-step ReRAM-crossbar accelerator as preprocessing, the workload of adder can be significantly reduced to ![image](images/ch06_si38.gif)(![image](images/ch06_si39.gif)).

![image](images/PBPC0390-06-f02.jpg)

Figure 6.2 ReRAM-based inner-product operation

#### 6.1.2 BCNN-based inference acceleration on passive array

The details of this section have been presented in \[222\]. As indicated in previous works, ReRAM crossbar can be applied to perform logic operations, especially the dot-product-based convolutions. Previous mapping of convolutional neural network (CNN) are mainly based on the traditional analog ReRAM crossbar \[145, 150\]. The main limitation is that there can exist a huge nonuniform analog resistance for undetermined states in the analog computation, which can result in convolution error.

Here, we will map the bitwise CNN-based inference process according to the algorithm and network in Section 4.3.3. This section focuses on the mapping of all the bitwise CNN operations on the passive array-based XIMA such as convolution, batch normalization, pooling and activation functions.

##### 6.1.2.1 Mapping bitwise convolution

According to (6.5), the bitwise convolution can be split into several XNOR and bit-count results of two vectors. To implement (6.5), we can use two AND operations for ![image](images/ch06_si40.gif)and ![image](images/ch06_si41.gif)as well as their complements. Therefore, the bitwise convolution on ReRAM crossbar can be shown as follows:

![image](images/ch06_si944.gif)

The mapping of the bitwise convolution is shown in [Figure 6.3](#Chapter6.html#c06_fig3)(a). It requires a ![image](images/ch06_si42.gif)ReRAM crossbar, where ![image](images/ch06_si43.gif)is the number of element in the vector. All columns are configured with the same elements that correspond to one column in binary weight ![image](images/ch06_si44.gif)of the neural network, and the wordline (WL) voltages are determined by the binary input ![image](images/ch06_si45.gif). Due to the large ratio between ![image](images/ch06_si46.gif)and ![image](images/ch06_si47.gif), the current through the bitline (BL) is approximately equal to ![image](images/ch06_si48.gif), where ![image](images/ch06_si49.gif)is the inner-product result in (6.6). Since the current of all BLs is identical, the ladder-like threshold voltages ![image](images/ch06_si50.gif)are set as follows:

![image](images/ch06_si945.gif)

where ![image](images/ch06_si51.gif)is the threshold voltage for the ![image](images/ch06_si52.gif)th column. If one uses ![image](images/ch06_si53.gif)to denote the output array, and ![image](images/ch06_si54.gif)to denote the output of column ![image](images/ch06_si55.gif)in ReRAM crossbar, we can have

![image](images/ch06_si946.gif)

![image](images/PBPC0390-06-f03.jpg)

Figure 6.3 Digital ReRAM-crossbar mapping for (a) bitwise convolution, (b) bitwise batch normalization and (c) bitwise max-pooling

In this case, the inner-product results ![image](images/ch06_si56.gif)can be recognized that the first (![image](images/ch06_si57.gif)) output bits are 0 and the rest ![image](images/ch06_si58.gif)bits are 1. The relation between ![image](images/ch06_si59.gif)and ![image](images/ch06_si60.gif)can be expressed as ![image](images/ch06_si61.gif).

As described in (6.5), each binary weight vector ![image](images/ch06_si62.gif)performs bitwise convolution with several input features. As a result, each logic block in [Figure 6.2](#Chapter6.html#c06_fig2) stores a binary vector ![image](images/ch06_si63.gif), while the control bus transmits the input feature sequentially. In this case, bitwise convolution can be performed in parallel in separated logic blocks.

##### 6.1.2.2 Mapping bitwise batch normalization

Bitwise batch normalization requires two digital ReRAM crossbars in the implementation. In the first ReRAM crossbar, it performs the XOR operation on adjacent bits of the output of bitwise convolution. It can be expressed as

![image](images/ch06_si947.gif)

After that, the second ReRAM crossbar builds a look-up table (LUT). Since ![image](images/ch06_si64.gif), ![image](images/ch06_si65.gif), ![image](images/ch06_si66.gif)and ![image](images/ch06_si67.gif)are all fixed in the inference stage, (6.8) can be rewritten as

![image](images/ch06_si948.gif)

where ![image](images/ch06_si68.gif)represents the LUT. As a result, the LUT is stored in the second ReRAM crossbar according to the parameters ![image](images/ch06_si69.gif), ![image](images/ch06_si70.gif), ![image](images/ch06_si71.gif)and ![image](images/ch06_si72.gif). As described in (6.8), only the ![image](images/ch06_si73.gif)th row of the LUT is selected, so the batch normalization result can be directly read out. The threshold voltage of both ReRAM crossbars is

![image](images/ch06_si949.gif)

To have a better illustration, [Figure 6.3](#Chapter6.html#c06_fig3)(b) shows the detailed mapping and [Table 6.1](#Chapter6.html#c06_tbl1) shows the values to store in the second ReRAM crossbar when ![image](images/ch06_si74.gif), ![image](images/ch06_si75.gif), ![image](images/ch06_si76.gif)and ![image](images/ch06_si77.gif)referred to the IEEE-754 standard.

Table 6.1 Binary format stored in ReRAM crossbar

| BinConv output || Batch normalization || Floating binary format |
| --- | --- | --- |
| 0 || –0.5 || 10111111000000000000000000000000 |
| --- | --- | --- |
| 1 || –0.3 || 10111110100110011001100110011010 |
| ... || ... || ... |
| 7 || 0.9 || 00111111011001100110011001100110 |

##### 6.1.2.3 Mapping bitwise pooling and binarization

According to (6.9), one can perform the binarization first and then perform max-pooling. The bitwise activation in (6.8) can be achieved by selecting the sign-bit of the binary format output of [Figure 6.3](#Chapter6.html#c06_fig3)(b). In max-pooling, the output is ![image](images/ch06_si81.gif)only when all the numbers in the pooling region are negative. As a result, one can add all the complementary sign-bit in the pooling region. If the result is not ![image](images/ch06_si82.gif), it indicates that at least one positive number is available in the pooling region, resulting in the pooling result ![image](images/ch06_si83.gif). In summary, the max-pooling in (6.5) can be rewritten as

![image](images/ch06_si950.gif)

As a result, both of the bitwise max-pooling and binarization can be implemented by the addition operation performed on the digital ReRAM crossbar with 1 column, as shown in [Figure 6.3](#Chapter6.html#c06_fig3)(c).

##### 6.1.2.4 Summary of mapping bitwise CNN

As a summary, the four operations of the bitwise CNN in Figure 4.7(b) can be fully mapped onto the digital ReRAM crossbar. All the threshold voltages are fixed even if the parameters of bitwise CNN are changed. Although these operations are implemented in different ReRAM-crossbar array, the input/output formats of them are compatible so that one can directly connect them as shown in the logic block in [Figure 6.3](#Chapter6.html#c06_fig3) with pipeline used. The pipeline design is based on [Table 6.2](#Chapter6.html#c06_tbl2), so that each stage implements a layer. CONV-2, CONV-4 and CONV-6 are the stages which require the most ReRAM cells and computation time.

Table 6.2 Bitwise CNN configuration of CIFAR-10 data set

| Name || Filter/weight || Output size |
| --- | --- | --- |
| CONV-1 || ![image](images/ch06_si84.gif) || ![image](images/ch06_si85.gif) |
| --- | --- | --- |
| CONV-2 || ![image](images/ch06_si86.gif) || ![image](images/ch06_si87.gif) |
| MP-2 || ![image](images/ch06_si88.gif) || ![image](images/ch06_si89.gif) |
| CONV-3 || ![image](images/ch06_si90.gif) || ![image](images/ch06_si91.gif) |
| CONV-4 || ![image](images/ch06_si92.gif) || ![image](images/ch06_si93.gif) |
| MP-4 || ![image](images/ch06_si94.gif) || ![image](images/ch06_si95.gif) |
| CONV-5 || ![image](images/ch06_si96.gif) || ![image](images/ch06_si97.gif) |
| CONV-6 || ![image](images/ch06_si98.gif) || ![image](images/ch06_si99.gif) |
| MP-6 || ![image](images/ch06_si100.gif) || ![image](images/ch06_si101.gif) |
| FC-1 || ![image](images/ch06_si102.gif) || ![image](images/ch06_si103.gif) |
| FC-2 || ![image](images/ch06_si104.gif) || ![image](images/ch06_si105.gif) |
| FC-3 || ![image](images/ch06_si106.gif) || ![image](images/ch06_si107.gif) |

As a result, more logic blocks are assigned to these steps to relieve the critical path. In our simulation, half of the digitized ReRAM crossbars are used to perform these three layers. Moreover, since the output feature from [Figure 6.3](#Chapter6.html#c06_fig3)(c) is binary, the area overhead and energy consumption of the data storage can be significantly reduced. In addition, because layers in [Table 6.2](#Chapter6.html#c06_tbl2) are implemented in different data-logic pairs, the volume of data transmitted is also decreased.

#### 6.1.3 BCNN-based inference acceleration on 1S1R array

In this work, we will present mappings of bitwise CNN operations on the sneak-path-free digital 1S1R ReRAM crossbar. The mapping detail is a little different compared to the mapping on passive array. Different from the signed realization in previous works \[149, 223\], we will use unsigned bitwise operation in the mapping.

##### 6.1.3.1 Mapping unsigned bitwise convolution

As described in Section 6.1.2, dot-product operation is the majority in bitwise convolution. Suppose that a single dot-product operation has ![image](images/ch06_si108.gif)numbers, the basic operation can be expressed as

![image](images/ch06_si951.gif)

where ![image](images/ch06_si109.gif). To implement the negative weights, \[149, 223\] use two ReRAM crossbars to represent positive and negative weights, respectively. However, this solution requires a subtraction operation for every complementary BL output. It is obvious that the subtraction implementation leads to extra CMOS circuit with more area and energy consumption. To avoid this problem, one can apply the conversion by XNOR operation (![image](images/ch06_si110.gif)) in ![image](images/ch06_si111.gif)introduced in \[189, 224\], as shown in [Table 6.3](#Chapter6.html#c06_tbl3).

Table 6.3 Conversion from signed bitwise convolution to unsigned bitwise XNOR

![image](images/tab6.3.jpg)

Since ![image](images/ch06_si140.gif), one can directly map ![image](images/ch06_si141.gif), ![image](images/ch06_si142.gif)as WL inputs, and ![image](images/ch06_si143.gif), ![image](images/ch06_si144.gif)as ReRAM conductances. We can use ![image](images/ch06_si145.gif)to denote the new bitwise convolution result as

![image](images/ch06_si952.gif)

Since ![image](images/ch06_si146.gif)must be an even integer and ![image](images/ch06_si147.gif)while ![image](images/ch06_si148.gif), the relation can be summarized as ![image](images/ch06_si149.gif). Although this mapping strategy requires the same number of ReRAM devices as the one in \[149, 223\], it only needs an inverter for each input bit.

##### 6.1.3.2 Mapping batch normalization, pooling and binarization

Section 4.3.3 has explained these three steps with detailed equations, but it is simpler to map them on ReRAM crossbar. We can notice that the order of binarization and pooling does not affect the final output. Therefore, by combining batch normalization and binarization, we can use ![image](images/ch06_si150.gif)from BatchNorm (parameters for the ![image](images/ch06_si151.gif)convolution fashion) as the threshold to compare with the bitwise convolution result. Although the corresponding voltage of ![image](images/ch06_si152.gif)is generated by limited-bit DAC, it is still more energy-efficient than the ADC for analog ReRAM crossbar. The comparison process is binarization with only ![image](images/ch06_si153.gif)or ![image](images/ch06_si154.gif)output. These two steps can be summarized as

![image](images/ch06_si953.gif)

As for pooling operation, we can put a single-output ReRAM crossbar and configure the comparator threshold as ![image](images/ch06_si155.gif)to detect if any binarization result in the pooling region is 1.

[Figure 6.4](#Chapter6.html#c06_fig4) shows the summary of bitwise CNN mapping on the proposed digital ReRAM crossbar. Since the output of each BL is also in ![image](images/ch06_si156.gif)fashion, it can be directly used for the binary input feature of the next layer.

![image](images/PBPC0390-06-f04.jpg)

Figure 6.4 Mapping of bitwise CNN on sneak-path-free digital ReRAM crossbar

#### 6.1.4 L2-norm gradient-based learning and inference acceleration

The details of this section have been presented in \[225\]. This section illustrates mapping of the multilayer feedforward neural network-based learning and inference processes according to the algorithm and network in Section 4.2.2. This section focuses on the mapping of all the matrix–vector multiplication operations and L2-norm calculation on the passive array and coupled oscillator-based XIMA.

##### 6.1.4.1 Mapping matrix–vector multiplication on ReRAM-crossbar network

With the introduction of binary-memristor-crossbar network, one can perform matrix–vector multiplication \[147\]. It has much better nonuniformity under process variation when compared to the multiple-level-valued analog memristor crossbar. As discussed in Section 6.1.2, the key operations in machine learning (feature extraction and convolution) requires a large number of matrix–vector multiplication.

As discussed earlier, the key operations (6.13) and (6.14) requires a large number of matrix–vector multiplication. For instance, consider ![image](images/ch06_si157.gif)as an example for mapping multiplication on crossbar. For every element in ![image](images/ch06_si158.gif), it follows, here, we take the operation of ![image](images/ch06_si159.gif)as an example for mapping the multiplication on the crossbar. For every element in ![image](images/ch06_si160.gif), it follows

![image](images/ch06_si954.gif)

where ![image](images/ch06_si161.gif)and ![image](images/ch06_si162.gif)are the elements in ![image](images/ch06_si163.gif)and ![image](images/ch06_si164.gif), respectively.

For the crossbar structure in [Figure 6.4](#Chapter6.html#c06_fig4), the current through each BL follows

![image](images/ch06_si955.gif)

As a result, we can map ![image](images/ch06_si165.gif)and ![image](images/ch06_si166.gif)on ![image](images/ch06_si167.gif)and ![image](images/ch06_si168.gif), respectively. By measuring the current through BL with binary digitization, one can derive the result ![image](images/ch06_si169.gif)in the digital domain. The detailed operation can be referred to the work in \[147\].

Note that for real numbers, one needs only a few more shifted additions to complete the final process of matrix–vector multiplication with memristor crossbar. [Figure 6.5](#Chapter6.html#c06_fig5) shows that we only need four-shifted addition with 8-bit precision to calculate the final inner product. In addition, Sigmoid function can be implemented in memristor crossbar with LUT.

![image](images/PBPC0390-06-f05.jpg)

Figure 6.5 (a) Crossbar network for multiplication; (b) shifted additions

##### 6.1.4.2 Mapping L2-norm calculation on coupled ReRAM oscillator network

In a coupled oscillator network, we use the memristor oscillator cell similar to that in Figure 3.15(a) (Rs replaced with a PMOS). By altering the gate voltage of the PMOS, we can control the oscillatory frequency as in Figure 3.15(d). Referring to previous works \[209, 210\], the proposed coupled-memristor-oscillator network is shown in Figure 5.8(a). Here, oscillators are directly coupled with memristors. The oscillatory frequency of each oscillator is determined by multiple input voltages. As mentioned in Figure 3.15(d), the voltage-controlled PMOS can be viewed as a voltage-controlled resistor. Figures 5.8(b) and 5.8(c) are the schematic of oscillators with single input and multiple inputs. After directly coupling, one can have an inverter and a feedback resistor with a diode-connected NMOS. These elements guarantee that the current will only pass from the oscillator network to ![image](images/ch06_si170.gif). An RC circuit is designed at ![image](images/ch06_si171.gif)so that we can measure the DC voltage of ![image](images/ch06_si172.gif). The output voltage indicates the relative synchronization of the coupled oscillators.

To perform (4.14) on oscillator network, we only need to use two inputs for each oscillator in Figure 5.8(c). To be more specific, one can have a mapping function as follows:

![image](images/ch06_si956.gif)

where ![image](images/ch06_si173.gif)is a scale factor to link the oscillator input voltage, and ![image](images/ch06_si174.gif)and ![image](images/ch06_si175.gif)are the elements in matrices ![image](images/ch06_si176.gif)and ![image](images/ch06_si177.gif), respectively.

As mentioned in \[209, 210\], the coupled oscillator network can work as a degree-of-match (DOM) circuit to calculate L2-norm by fitting ![image](images/ch06_si178.gif)to ![image](images/ch06_si179.gif)polynomial when there are two inputs for each oscillator in Figure 5.8(c). Therefore, the output voltage follows

![image](images/ch06_si957.gif)

where ![image](images/ch06_si180.gif)is a fitting parameter, and ![image](images/ch06_si181.gif)is the output voltage when ![image](images/ch06_si182.gif).

As such, one can use the coupled-memristor-oscillator network to the L2-norm error function in machine learning. The L2-norm result is obtained by curve fitting but not accurate computing. Compared to other implementations, such an oscillator network can complete the operation much faster because the square operation ![image](images/ch06_si183.gif)can be performed simultaneously by the oscillator circuit. Moreover, the accumulation is also automatically achieved by the coupled network.

##### 6.1.4.3 Mapping flow of multilayer neural network on ReRAM network

Based on the coupled-memristor-oscillator network and binary-memristor-crossbar network, we can accelerate direct-gradient-based L2-norm minimization for machine learning as shown in [Figure 6.6](#Chapter6.html#c06_fig6). For the model part, we use two types: memristor oscillator and memristor crossbar. We find the parameter in oscillator network to calculate L2-norm, and map on crossbar network to calculate digitized matrix–vector multiplication. Afterwards, one can generate the initial weights of ![image](images/ch06_si184.gif)and ![image](images/ch06_si185.gif)to calculate the gradient ![image](images/ch06_si186.gif). The best direction to minimize ![image](images/ch06_si187.gif)can be derived. This process will be repeated several times till the minimization is reached only when ![image](images/ch06_si188.gif).

![image](images/PBPC0390-06-f06.jpg)

Figure 6.6 Mapping flow of machine learning on memristor network

#### 6.1.5 Experimental evaluation of machine learning algorithms on XIMA architecture

We will show the detailed mapping of several machine learning applications on XIMA, including SLFN-based learning, BCNN-based inferences on passive array as well as 1S1R array.

##### 6.1.5.1 SLFN-based learning and inference acceleration

###### Experiment settings

The hardware evaluation platform is implemented on a computer server with 4.0 GHz core and 16.0 GB memory. Feature extraction is implemented by general processor, CMOS-based application-specific integrated circuit (ASIC), non-distributed and distributed in-memory computing based on digitalized ReRAM crossbar, respectively. For the ReRAM-crossbar design evaluation, the resistance of ReRAM is set as 1 kΩ and 1 MΩ as on-state and off-state resistance, respectively, according to \[206\].

The general processor solution is performed by MATLAB on a 4.0 GHz desktop. For CMOS-ASIC implementation, we implement it by Verilog and synthesize with CMOS 65-nm low-power process design kit (PDK). For ReRAM-crossbar-based solution, we verify the function in circuit level with SPICE tool NVM-SPICE \[63\]. By analyzing the machine learning algorithm, we obtain the basic operations and the number of ReRAM-crossbar logic units required.

The working frequency of general processor implementation is 4.0 GHz while the CMOS-ASIC feature extraction design frequency is 1.0 GHz. For in-memory computing based on the proposed ReRAM crossbar, write voltage ![image](images/ch06_si191.gif)is set as ![image](images/ch06_si192.gif)V and read voltage ![image](images/ch06_si193.gif)is set as ![image](images/ch06_si194.gif)V as well as duration time of ![image](images/ch06_si195.gif)ns. In addition, the analog computation on ReRAM crossbar is performed for comparison based on design in \[207\].

In the following, we will show the performance of matrix–vector multiplication on ReRAM crossbar first. A scalability study is introduced to show the area, energy and computation delay with different matrix sizes. Afterwards, the evaluation of face recognition on in-memory architecture is presented. Finally, we will illustrate the object classification on three-dimensional (3D) CMOS-ReRAM architecture. Performance of different bid-width configurations will be also shown. In addition, the 3D CMOS-ReRAM solution will be compared with CMOS-ASIC as well as Graphics Processing Unit (GPU) implementation.

###### Performance evaluation

In this work, we implement the face recognition application on the in-memory architecture. We will analyze the computation complexity of face recognition first, and then evaluate the performance.

In the experiment, ![image](images/ch06_si196.gif)face images of ![image](images/ch06_si197.gif)people are selected from \[226\], with scaled image size ![image](images/ch06_si198.gif)of each image ![image](images/ch06_si199.gif). In principal component analysis (PCA), feature size of image is further reduced to 128 by multiplying the matrix ![image](images/ch06_si200.gif). The number of hidden node ![image](images/ch06_si201.gif)and classes ![image](images/ch06_si202.gif)are ![image](images/ch06_si203.gif)and ![image](images/ch06_si204.gif), respectively. Based on the experimental settings, computation complexity is analyzed with results shown in [Figure 6.7](#Chapter6.html#c06_fig7). Here 82% of computations are multiplication in output weight calculation, which is the most time-consuming procedure in neural network. Time consumption of each process in neural network is introduced in [Figure 6.7](#Chapter6.html#c06_fig7)(b). Since processes except activation function involve matrix–vector multiplication, we extracted this operation in the whole algorithm and found that 64.62% of time is consumed in matrix–vector multiplication, as shown in [Figure 6.7](#Chapter6.html#c06_fig7)(c).

![image](images/PBPC0390-06-f07.jpg)

Figure 6.7 (a) Time-consumption breakdown for output weight calculation; (b) neural network training computation effort analysis; (c) multiplication analysis for neural network training (![image](images/ch06_si205.gif), ![image](images/ch06_si206.gif), ![image](images/ch06_si207.gif)and ![image](images/ch06_si208.gif))

We implement the face recognition applications by the SLFN on XIMA. In [Table 6.4](#Chapter6.html#c06_tbl4), general performance comparisons among MATLAB, CMOS-ASIC and ReRAM-crossbar accelerator are introduced, and the acceleration of each procedure as the formula described in Section 7.2 is also addressed. Among three implementations, ReRAM-crossbar architecture performs the best in area, energy and speed. Compared to MATLAB implementation, it achieves ![image](images/ch06_si249.gif)speedup, ![image](images/ch06_si250.gif)energy-saving and almost four-magnitude area-saving. We also design a CMOS-ASIC implementation with similar structure as ReRAM crossbar with better performance compared to MATLAB. ReRAM-crossbar architecture is ![image](images/ch06_si251.gif)speedup, ![image](images/ch06_si252.gif)energy-saving and ![image](images/ch06_si253.gif)area-saving compared to CMOS-ASIC. The performance comparison is quite different from Table 5.1, because we applied different designs (ReRAM-crossbar size) is this two experiments according to the dimension of matrices.

Table 6.4 Face recognition performance comparison under different software and hardware implementations

![image](images/tab6.4.jpg)

The result of face recognition is shown in [Figure 6.8](#Chapter6.html#c06_fig8). Five training classes are provided as an example with three test cases. Each test face will be recognized as the class with the largest score (prediction result as the index of ![image](images/ch06_si254.gif), marked in red color). In this example, Case 1 is identified as Class 1, while Cases 2 and 3 are classified into Classes 3 and 5, respectively.

![image](images/PBPC0390-06-f08.jpg)

Figure 6.8 Training samples and prediction value ![image](images/ch06_si255.gif)from (4.7) for face recognitions

##### 6.1.5.2 L2-norm gradient-based learning and inference acceleration

###### Experiment settings

The hardware evaluation platform is implemented on a computer server with 4.0 GHz core and 16.0 GB RAM. For ReRAM-based oscillator network, we use the VerilogA model from \[153\] and device model from \[151\] as the ReRAM before forming process and simulate the network in Cadence Spectre. For ReRAM-based crossbar network, the resistance of ReRAM is set as 1 kΩ and 1 MΩ as on-state and off-state resistance, respectively, according to \[206\]. NVM-SPICE \[63\] is used for ReRAM-crossbar network verification. For comparison propose, we also implement the L2-norm gradient-based machine learning on general processor. The working frequency of general processor implementation is 3.46 GHz with 64.0 GB RAM. In addition, University of California Irvine (UCI) benchmark data are selected for comparisons \[184\]. Write voltage ![image](images/ch06_si325.gif)is set as ![image](images/ch06_si326.gif)V and read voltage ![image](images/ch06_si327.gif)is set as ![image](images/ch06_si328.gif)V as well as duration time of ![image](images/ch06_si329.gif)ns.

###### Performance evaluation

To evaluate the proposed ReRAM network for machine learning, we use Iris in UCI data set as benchmark. First, we analyze the computation complexity in L2-norm-gradient-based machine learning. [Figure 6.9](#Chapter6.html#c06_fig9)(a) shows the time consumption of CMOS-CPU-based implementation. In simulation, we need to optimize the value of ![image](images/ch06_si330.gif)weights to minimize the L2-norm. 71.63% computation time is consumed by matrix–vector multiplication, and 26.41% time is consumed by L2-norm calculation. Therefore, the total computation time can be significantly reduced by accelerating these two operations.

![image](images/PBPC0390-06-f09.jpg)

Figure 6.9 Time-consumption proportion of Iris data set: (a) without ReRAM network; (b) with ReRAM network, and energy consumption proportion of Mushroom data set; (c) without ReRAM network; (d) with ReRAM network

To evaluate the ReRAM network performance in Iris data set, we use the proposed ReRAM network to address matrix–vector multiplication and L2-norm calculation. For the other operations (1.96% in [Figure 6.9](#Chapter6.html#c06_fig9)(a)), we still use CPU for calculation. As there are ![image](images/ch06_si331.gif)weights to be updated in the benchmark, we design ![image](images/ch06_si332.gif)ReRAM-oscillator networks to compute ![image](images/ch06_si333.gif)for each ![image](images/ch06_si334.gif)simultaneously. In the experiment, we need to repeat this procedure for ![image](images/ch06_si335.gif)times to derive the minimum of L2-norm. The time consumption with ReRAM network is shown in [Figure 6.9](#Chapter6.html#c06_fig9)(b). We can see that L2-norm becomes the dominant time-consuming operation. In addition, the matrix–vector multiplication and L2-norm take only ![image](images/ch06_si336.gif)as the other operations, which only take little time in machine learning.

[Figure 6.9](#Chapter6.html#c06_fig9)(c) and (d) shows the energy efficiency achieved by the proposed ReRAM network. The energy consumption of machine learning on ReRAM network is significantly reduced. Note that each ReRAM-oscillator-network requires ![image](images/ch06_si337.gif)to perform the one-time L2-norm calculation with ![image](images/ch06_si338.gif)according to Table 5.2. Note that matrix–vector multiplication and L2-norm calculation are dominant in CMOS-CPU-based implementation. For Mushroom data set, they take over 99% of energy consumption. When we map these operations on the ReRAM network, their energy consumption is only 8.7%. We use four benchmarks in UCI data set \[184\] to measure the speedup and energy-saving, as shown in [Table 6.5](#Chapter6.html#c06_tbl5). Using the proposed ReRAM network, we can achieve ![image](images/ch06_si339.gif)speedup and more than ![image](images/ch06_si340.gif)energy-saving. Note that the improvement depends on the training size of benchmark. For example, the L2-norm calculation is the dominant operation in Mushroom and Liver so that we can save over 99.5% energy consumption when using the proposed ReRAM network. For Iris and Wine, matrix–vector multiplication is dominant so that the energy-saving is below 99%.

Table 6.5 Time and energy comparison on UCI data set

![image](images/tab6.5.jpg)

##### 6.1.5.3 BCNN-based inference acceleration on passive array

###### Experimental settings

**Baselines** In the simulation, we have implemented different baselines for comparison using both MNIST and CIFAR-10 benchmarks. The detail of each baseline is listed as follows:

CPU: The BNN simulation is run in Matconvnet \[227\] on a computer server with ![image](images/ch06_si341.gif)GHz core and ![image](images/ch06_si342.gif)GB RAM. The BNN network is referred to [Table 6.2](#Chapter6.html#c06_tbl2).

Design of digital ReRAM: The ReRAM device model for BNN is based on \[63, 64, 139\] with the resistance of ReRAM set as ![image](images/ch06_si343.gif)M and ![image](images/ch06_si344.gif)M as on-state and off-state, respectively, with working frequency of ![image](images/ch06_si345.gif)MHz. Sense amplifier is based on the design of \[228\]. The BNN network is also referred to [Table 6.2](#Chapter6.html#c06_tbl2).

Others: GPU-based \[188\] bitwise CNN implementations and field programmable gate array (FPGA)-based \[229\], CMOS-ASIC-based \[230\] and analog-ReRAM-based \[146\] conventional CNN implementations are selected for performance comparisons as well.

**Network** The overall network architecture of the bitwise CNN (called BNN) is shown in [Table 6.2](#Chapter6.html#c06_tbl2). It has six binary convolutional (BinConv) layers, three max-pooling (MP) layers and three fully connected (FC) layers.

It takes a ![image](images/ch06_si346.gif)RGB image as the input of the first layer. We use ![image](images/ch06_si347.gif)sets of binary filters, and each set contains three binary filters to process the data from R, G and B channels, receptively. The width and height of each BinConv layer is fixed to ![image](images/ch06_si348.gif)with stride of ![image](images/ch06_si349.gif)and zero padding of ![image](images/ch06_si350.gif). The BinConv layer performs the bitwise convolution between input feature maps and weights followed by the bitwise batch normalization and the binary activation. Note that the computation for FC layers can be treated as a convolution with stride of ![image](images/ch06_si351.gif)and zero padding of 0. Thus, we refer the matrix multiplication in FC layers to convolution as well.

As shown in [Table 6.2](#Chapter6.html#c06_tbl2), two cascaded convolutional layers form a convolutional block with equivalent ![image](images/ch06_si352.gif)convolution window. This configuration provides more powerful representation capacity with less amount of weights compared with the direct ![image](images/ch06_si353.gif)implementation. Meanwhile, binary batch normalization is applied after the convolution to accelerate and stabilize the training. We adopt the binary activation to each BinConv layer and FC layer with the exception for the last FC layer. The output of the last FC layer is fed into the softmax layer \[231\] without binarization to generate a probabilistic distribution of ten classes.

Besides CIFAR-10, we also show the experiment on MNIST data set \[232\], with detailed parameters in [Table 6.6](#Chapter6.html#c06_tbl6), which is pretrained on a server. Compared to parameters of CIFAR-10, we use conventional ![image](images/ch06_si354.gif)convolutional cores in MNIST.

Table 6.6 Bitwise CNN configuration of MNIST data set

| Name || Filter/weight || Output size |
| --- | --- | --- |
| CONV-1 || ![image](images/ch06_si355.gif) || ![image](images/ch06_si356.gif) |
| --- | --- | --- |
| MP-1 || ![image](images/ch06_si357.gif) || ![image](images/ch06_si358.gif) |
| CONV-2 || ![image](images/ch06_si359.gif) || ![image](images/ch06_si360.gif) |
| MP-2 || ![image](images/ch06_si361.gif) || ![image](images/ch06_si362.gif) |
| FC-1 || ![image](images/ch06_si363.gif) || ![image](images/ch06_si364.gif) |
| FC-2 || ![image](images/ch06_si365.gif) || ![image](images/ch06_si366.gif) |

###### Performance evaluation

We first show accuracy comparison between the analog ReRAM and the digitized ReRAM under device variation. We then show accuracy comparison between the conventional CNN with direct-truncated prevision and the proposed bitwise CNN. Various benchmarks such as CIFAR-10 \[233\] and MNIST \[232\] are used here.

**Error under device variation** In the previous discussion, the digitized ReRAM crossbar has better programming accuracy than the analog ReRAM crossbar. [Figure 6.10](#Chapter6.html#c06_fig10) shows a 200-time Monte-Carlo simulation of a single ReRAM device programming process with different write voltage ![image](images/ch06_si367.gif), where the voltage amplitude is under Gaussian distribution on the(![image](images/ch06_si368.gif)%![image](images/ch06_si369.gif)), and each column denotes a region of ![image](images/ch06_si370.gif). It is clear that the digital ReRAM crossbar (only ![image](images/ch06_si371.gif)and ![image](images/ch06_si372.gif)) can achieve a better uniformity than the analog ReRAM crossbar. The accuracy comparison against device variation on ReRAM is shown in [Figure 6.11](#Chapter6.html#c06_fig11)(b). The percentage of device variation defines the maximum resistance offset, and each ReRAM device follows standard deviation. Monte-Carlo is applied in the generation of device variation. In CIFAR-10, one can observe that when the device variation (ReRAM resistance value) is more than 8%, there is a large output current error reported. For example, when the device variation reaches 29%, the digital ReRAM can have an accuracy of 87.4% with only 4% decreased compared to no variations, better than the analog one with an accuracy of 84.8% with 7.6% decreased. In MNIST, the digital ReRAM is always better even when the device variation is larger than 27%.

![image](images/PBPC0390-06-f10.jpg)

Figure 6.10 ReRAM configuration with voltage amplitude variation following Gaussian distribution

**Error under approximation** For a precision-bit direct-truncated CNN, we use the conventional approach to train the full-precision (![image](images/ch06_si373.gif)\-bit) CNN first, and then decrease the precision of all the weights in the network. The numerical experiment results of weights with different bit-widths are shown in [Figure 6.11](#Chapter6.html#c06_fig11)(b). Here, the weights in the bitwise CNN is 1 bit, whose accuracy of is not changed. In CIFAR-10, although the accuracy of the full precision (![image](images/ch06_si374.gif)\-bit) can reach 92.4% in the direct-truncated CNN, the bit-width influences the accuracy a lot especially when the bit-width is smaller than ![image](images/ch06_si375.gif). For example, when the precision decreases to ![image](images/ch06_si376.gif)\-bit, the accuracy drops down to only about 11.8%. In MNIST, the accuracy of the direct-truncated CNN drops significantly when the bit-width is smaller than ![image](images/ch06_si377.gif)\-bit. The results show that the proposed bitwise CNN can perform much better than the direct-truncated CNN.

![image](images/PBPC0390-06-f11.jpg)

Figure 6.11 (a) Accuracy comparison with analog ReRAM under device variation; (b) accuracy comparison with truncated CNN with approximation

**Scalability study** To achieve a better energy efficiency of BNN, we do the scalability study to find out the BNN parameters for both good testing accuracy and energy efficiency. We use a four-layer BNN on MNIST benchmark as a baseline (100% energy efficiency, as shown in [Table 6.6](#Chapter6.html#c06_tbl6)), and change the number of output maps of Layer 2 (CONV-2, 50) and hidden nodes of Layer 3 (FC-1, 500), as shown in [Figure 6.12](#Chapter6.html#c06_fig12)(a) and (b). For each energy-efficiency configuration, we do a 20-epoch training to make a fair comparison. When the number of hidden nodes or output maps decreases, the energy efficiency is better but it will cause higher testing error rate. To summarize the scalability study, [Figure 6.12](#Chapter6.html#c06_fig12)(c) shows that the hidden nodes of Layer 2 is more sensitive to testing accuracy. As a result, increasing the hidden nodes of Layer 2 is better for higher accuracy while decreasing the hidden nodes of Layer 3 is better for energy efficiency.

![image](images/PBPC0390-06-f12.jpg)

Figure 6.12 Scalability study of testing error rate under different energy consumption with (a) Layer 2 output maps and (b) Layer 3 hidden nodes; (c) comparison with Layer 2 output maps and Layer 3 hidden nodes

**Performance comparison** In this section, ![image](images/ch06_si378.gif)images with ![image](images/ch06_si379.gif)resolution in CIFAR-10 are selected to evaluate the performance among all implementations. Parameters including binary weights, and LUT for batch normalization have been configured by the training process. The detailed comparison is shown in [Table 6.7](#Chapter6.html#c06_tbl7) with numerical results including area, system throughput, computation time and energy consumption. [Figure 6.13](#Chapter6.html#c06_fig13) shows a recognition example of CIFAR-10 data set. In the numerical experiment, every batch comprises ten images and the results are calculated in parallel. The detailed result figure is included in the supplementary file. The black square represents to the class that each image belongs.

![image](images/PBPC0390-06-f13.jpg)

Figure 6.13 Image recognition example of CIFAR-10 data set

Table 6.7 Performance comparison among different software and hardware implementations on CIFAR-10 BCNN

![image](images/tab6.7.jpg)

The overall power comparison among all the implementations is shown in [Table 6.7](#Chapter6.html#c06_tbl7) under the similar accuracy of 91.4% in CIFAR-10. Compared to CPU-based and GPU-based bitwise CNN, the proposed digital ReRAM-based implementation can achieve up to four-magnitude smaller power. Moreover, compared to FPGA-based and CMOS-ASIC-based conventional CNN, the digital ReRAM-based implementation is ![image](images/ch06_si413.gif)and ![image](images/ch06_si414.gif)smaller power.

In addition, we analyze the detailed power characteristics of the proposed digital ReRAM design in [Figure 6.14](#Chapter6.html#c06_fig14). First, we analyze the power distribution on convolution, batch normalization, pooling and activation, respectively. [Figure 6.14](#Chapter6.html#c06_fig14)(a) shows that 89.05% of power is consumed by convolution, while 9.17% of power is for batch normalization, and the rest only takes 1.78%. Second, we analyze the power distribution on different bitwise CNN layers in [Table 6.2](#Chapter6.html#c06_tbl2). Results in [Figure 6.14](#Chapter6.html#c06_fig14)(b) show that CONV-6 consumes the most power 25.92%, while CONV-4 and CONV-2 also consume more than 23% of the total power. In general, there is over 98% of power consumed by CONV-2 to CONV-6 layers.

![image](images/PBPC0390-06-f14.jpg)

Figure 6.14 Power consumption of bitwise CNN for (a) different operations and (b) different layers

For the throughput performance, we use GOPS (giga operations per second) to evaluate all the implementations. The proposed digital ReRAM can achieve ![image](images/ch06_si415.gif)GOPS, which is ![image](images/ch06_si416.gif)and ![image](images/ch06_si417.gif)better than CPU-based and GPU-based implementations, respectively. It is also ![image](images/ch06_si418.gif)and ![image](images/ch06_si419.gif)better than FPGA-based and CMOS-ASIC. For energy efficiency, the digital ReRAM achieves ![image](images/ch06_si420.gif)TOPS/W, three-magnitude better than the CMOS-ASIC-based CNN. In area-efficiency comparison, the digital ReRAM is ![image](images/ch06_si421.gif)better than CMOS-ASIC. The digital ReRAM is the best among all the implementations on both throughput and efficiency.

The design exploration of CIFAR-10 is shown in [Figure 6.15](#Chapter6.html#c06_fig15). We change the number of CONV-4 output maps to find out the optimized parameter. The normalized energy consumption is referred to the configuration in [Table 6.7](#Chapter6.html#c06_tbl7). The result shows that the accuracy will not increase when the number is larger than 256. When it is lower than 256, the accuracy drops down even though it has better energy consumption and throughput. As a result, the parameters in [Table 6.2](#Chapter6.html#c06_tbl2) are optimal with specifications in [Table 6.7](#Chapter6.html#c06_tbl7).

![image](images/PBPC0390-06-f15.jpg)

Figure 6.15 Performance with different number of CONV-4 output maps in CIFAR-10

##### 6.1.5.4 BCNN-based inference acceleration on 1S1R array

**Baselines and networks** For this experiment, different baselines are implemented for comparison using both CIFAR-10 and MNIST \[232\] benchmarks, as in Section 6.1.5.3. The detail of each baseline is listed as follows:

Bitwise CNN: We implement bitwise CNN on digital ReRAM crossbar with working frequency of ![image](images/ch06_si422.gif)MHz. Comparator on each BL is based on the design of \[228\]. In the 1S1R array, the drift-type ReRAM in \[239\] is applied with ![image](images/ch06_si423.gif)and ![image](images/ch06_si424.gif). Meanwhile, the diffusive-type ReRAM is taken from \[137, 138\] with ![image](images/ch06_si425.gif)and ![image](images/ch06_si426.gif). For performance comparison, CPU implementation is run in Matconvnet on a computer server with ![image](images/ch06_si427.gif)GHz core and ![image](images/ch06_si428.gif)GB RAM. The GPU-based design is referred to \[188\], and a CMOS-ASIC design in ![image](images/ch06_si429.gif)\-nm technology is also realized.

Conventional CNN: FPGA-based \[229\] and CMOS-ASIC-based \[234\] implementations are compared. Moreover, an analog ReRAM-crossbar-based realization are simulated.

###### ReRAM device simulation

To illustrate the sneak-path-free effect of the 1S1R implementation, we use SPICE simulation with the same input voltages for Figure 3.14(a) and (c). In the write operation, we set the target ![image](images/ch06_si430.gif)as high resistance state (HRS) and the sneak-path ReRAMs, ![image](images/ch06_si431.gif), ![image](images/ch06_si432.gif), ![image](images/ch06_si433.gif)are HRS, low resistance state (LRS) and LRS, respectively. By applying ![image](images/ch06_si434.gif)and ![image](images/ch06_si435.gif)with other nets floating, the sneak-path ReRAM ![image](images/ch06_si436.gif)in direct connection is changed from ![image](images/ch06_si437.gif)to ![image](images/ch06_si438.gif), while the one in the 1S1R implementation remains the original resistance shown in [Figure 6.16](#Chapter6.html#c06_fig16). In the read operation, we set ![image](images/ch06_si439.gif)as HRS and the sneak-path ReRAMs are all LRS. According to the results in [Figure 6.17](#Chapter6.html#c06_fig17), the direct connection implementation will read ![image](images/ch06_si440.gif)due to the sneak-path effect. Though it takes ![image](images/ch06_si441.gif)ns to turn on the selector with read voltage, the target ReRAM can be precisely read out.

![image](images/PBPC0390-06-f16.jpg)

Figure 6.16 Sneak-path-free effect in 1S1R implementation for write operation

Although the ![image](images/ch06_si442.gif)ns read time of the proposed 1S1R is much longer than ![image](images/ch06_si443.gif)ns of direct connection, the total read energy will not increase much. As shown in [Figure 6.17](#Chapter6.html#c06_fig17), because the selector in LRS branch can be turned on faster than the one in RHS branch, the RHS/LRS ratio in the read operation can reach ![image](images/ch06_si444.gif)instead of the ideal value ![image](images/ch06_si445.gif)(![image](images/ch06_si446.gif)M/500k). As a result, using selector can achieve a larger difference between LRS and RHS readings.

![image](images/PBPC0390-06-f17.jpg)

Figure 6.17 Sneak-path-free effect in 1S1R implementation for read operation

In addition, we show the ReRAM resistance variation with different write voltage ![image](images/ch06_si448.gif)in [Figure 6.18](#Chapter6.html#c06_fig18). We use five sets of ideal ![image](images/ch06_si449.gif)from ![image](images/ch06_si450.gif)to ![image](images/ch06_si451.gif)V following Gaussian distribution (![image](images/ch06_si452.gif)%![image](images/ch06_si453.gif)), and ![image](images/ch06_si454.gif)data points are simulated to show the distribution of configured ReRAM resistance value in each set. Each column in [Figure 6.18](#Chapter6.html#c06_fig18) represents a resistance range of ![image](images/ch06_si455.gif). The results show that the digital ReRAM (LRS with ![image](images/ch06_si456.gif)V here) has a much better uniformity with input variation compared to analog ReRAM like \[150\], leading a better programming accuracy.

![image](images/PBPC0390-06-f18.jpg)

Figure 6.18 Programming inaccuracy for different target resistances with voltage amplitude variation following Gaussian distribution

###### Performance comparison

We select CIFAR-10 as the benchmark to evaluate all the implementations. [Table 6.8](#Chapter6.html#c06_tbl8) summarizes the performance under similar classification accuracy of 91.4%.

Table 6.8 Performance comparison under different software and hardware implementations

![image](images/tab6.8.jpg)

**Power consumption** Compared to CPU-based and GPU-based bitwise CNN, the proposed digital ReRAM-based implementation can achieve up to 4 × smaller power. Compared to simulation result of CMOS-ASIC bitwise CNN, it has ![image](images/ch06_si492.gif)smaller power. Moreover, compared to FPGA-based and CMOS-ASIC-based conventional CNN, the digital ReRAM-based implementation is ![image](images/ch06_si493.gif)and ![image](images/ch06_si494.gif)smaller power, respectively.

In addition, we analyze the detailed power characteristics of the proposed digital ReRAM design in [Figure 6.14](#Chapter6.html#c06_fig14). First, we analyze the power distribution on convolution, batch normalization, pooling and activation, respectively. [Figure 6.14](#Chapter6.html#c06_fig14)(a) shows that 89.05% of power is consumed by convolution, while 9.17% of power is for batch normalization, and the rest only takes 1.78%. Second, we analyze the power distribution on different bitwise CNN layers in [Table 6.2](#Chapter6.html#c06_tbl2). Results in [Figure 6.14](#Chapter6.html#c06_fig14)(b) show that CONV-6 consumes the most power 25.92%, while CONV-4 and CONV-2 also consume more than 23% of the total power. In general, there is over 98% of power consumed by CONV-2 to CONV-6 layers.

**Throughput and energy efficiency** For the throughput performance, we use GOPS to evaluate all the implementations. The proposed digital ReRAM can achieve ![image](images/ch06_si495.gif)GOPS, which is ![image](images/ch06_si496.gif), ![image](images/ch06_si497.gif)and ![image](images/ch06_si498.gif)better than CPU-based, GPU-based and CMOS-ASIC-based bitwise CNN, respectively. It is also ![image](images/ch06_si499.gif)and ![image](images/ch06_si500.gif)better than FPGA-based and CMOS-ASIC-based CNN. For energy efficiency, the digital ReRAM achieves ![image](images/ch06_si501.gif)TOPS/W, three-magnitude better than the CMOS-ASIC-based CNN. In area-efficiency comparison, the digital ReRAM is ![image](images/ch06_si502.gif)better than CMOS-ASIC-based CNN as well. The digital ReRAM is the best among all the implementations on both throughput and efficiency.

### 6.2 Machine learning algorithms on 3D XIMA

In addition, this chapter presents a detailed mapping of machine learning applications on 3D CMOS-ReRAM architecture, including SLFN-based learning and tensorized neural network (TNN) inference.

#### 6.2.1 On-chip design for SLFN

The details of this section are obtained from \[235\]. This work presents mapping the SLFN-based learning and inference processes according to the algorithm and network in Section 4.2. This section will focus on the mapping of all the matrix–vector multiplication operations on ReRAM crossbar and other operations in CMOS. Multilayer 3D CMOS-ReRAM architecture in Figure 5.13 is used for the acceleration.

This section will first discuss the data quantization on the proposed architecture. Then this section illustrates how to map matrix–vector multiplication on ReRAM-crossbar layer. Finally, CMOS-ASIC accelerator is also designed in Layer 3 for remaining operations in pipelined and parallel fashion.

##### 6.2.1.1 Data quantization

To implement the whole training algorithm on the proposed 3D multilayer CMOS-ReRAM accelerator, the precision of the real values requires a careful evaluation. Compared to the software double precision floating point format (64-bit), the values in the training algorithm are truncated into finite precision. By cross-validation from software, a balanced point between hardware resource and testing accuracy can be achieved. A general ![image](images/ch06_si503.gif)bit fixed point representation with ![image](images/ch06_si504.gif)bit integer and ![image](images/ch06_si505.gif)bit fraction point is shown as follows:

![image](images/ch06_si958.gif)

In the described accelerator, one needs to first assign a fixed 16 bit-width for normalized input data such as ![image](images/ch06_si506.gif)and ![image](images/ch06_si507.gif)with scale factor ![image](images/ch06_si508.gif)and ![image](images/ch06_si509.gif). For weights such as **A** and **B** in SLFN, one can determine ![image](images/ch06_si512.gif)by finding the logarithm of dynamic range (i.e., ![image](images/ch06_si513.gif)) and ![image](images/ch06_si514.gif)is set as ![image](images/ch06_si515.gif). Furthermore, one needs to apply greedy search method based on the testing accuracy to find the optimal bit-width. The bit-width is reduced with cross-validation applied to evaluate the effect. By dynamic tuning the bit-width, our objective is to find the minimum bit-width with acceptable testing accuracy loss.

##### 6.2.1.2 ReRAM layer implementation for digitized matrix–vector multiplication

The matrix–vector multiplication is illustrated with the example of output layer (4.7) calculation, where each element in ![image](images/ch06_si516.gif)is calculated using ![image](images/ch06_si517.gif). Such a multiplication can be expressed in terms of binary multiplication \[147\].

![image](images/ch06_si959.gif)

where ![image](images/ch06_si518.gif)is the accelerated result from ReRAM crossbar. ![image](images/ch06_si519.gif)is the binary bit of ![image](images/ch06_si520.gif)with ![image](images/ch06_si521.gif)bit-width and ![image](images/ch06_si522.gif)is the binary bit of ![image](images/ch06_si523.gif)with ![image](images/ch06_si524.gif)bit-width. As mentioned above, bit-width ![image](images/ch06_si525.gif)and ![image](images/ch06_si526.gif)are decided using cross-validation in design to achieve balanced accuracy and hardware usage \[236\].

**Step 1: Parallel digitizing**: It requires an ![image](images/ch06_si527.gif)ReRAM crossbar. Each inner product is produced ReRAM crossbar as shown in [Figure 6.19](#Chapter6.html#c06_fig19)(a). ![image](images/ch06_si528.gif)is set as crossbar input and ![image](images/ch06_si529.gif)is written in ReRAM cells. In the ![image](images/ch06_si530.gif)ReRAM crossbar, resistance of ReRAMs in each column is the same, but ![image](images/ch06_si531.gif)among columns is different. As a result, the output of each column mainly depends on ladder-like threshold voltages ![image](images/ch06_si532.gif). If the inner-product result is ![image](images/ch06_si533.gif), the output of Step 1 is like ![image](images/ch06_si534.gif), where ![image](images/ch06_si535.gif)and ![image](images/ch06_si536.gif).

![image](images/PBPC0390-06-f19.jpg)

Figure 6.19 Detailed mapping for digitalized matrix–vector multiplication on ReRAM crossbar: (a) parallel digitizing; (b) XOR; (c) encoding; (d) legend of mapping

**Step 2: XOR**: It is to identify the index of ![image](images/ch06_si537.gif)with the operation ![image](images/ch06_si538.gif). Note that ![image](images/ch06_si539.gif)only when ![image](images/ch06_si540.gif)and ![image](images/ch06_si541.gif)from Step 1. The mapping of ReRAM-crossbar input and resistance is shown in [Figure 6.19](#Chapter6.html#c06_fig19)(b), and threshold voltage configuration is ![image](images/ch06_si542.gif). Therefore, the index of ![image](images/ch06_si543.gif)is identified by XOR operation.

**Step 3: Encoding**: The third step produces ![image](images/ch06_si544.gif)in binary format as an encoder with the thresholds as Step 2. The input from the second step produces ![image](images/ch06_si545.gif)like result where only the ![image](images/ch06_si546.gif)input is ![image](images/ch06_si547.gif). As a result, only the ![image](images/ch06_si548.gif)row is read out and no current merge occurs in this step. The according binary format ![image](images/ch06_si549.gif)is an intermediate result and stored in the ![image](images/ch06_si550.gif)row, as shown in [Figure 6.19](#Chapter6.html#c06_fig19)(c). Encoding step needs an ![image](images/ch06_si551.gif)ReRAM crossbar, where ![image](images/ch06_si552.gif)is the number of bits in order to represent ![image](images/ch06_si553.gif)to ![image](images/ch06_si554.gif)in binary format.

##### 6.2.1.3 CMOS layer implementation for decoding and incremental least-squares

In the CMOS layer, decoding and more complex operations for incremental least-squares solution are designed. Since the output from ReRAM layer is in binary format, decoding is required to obtain the real values. Adder and shifter are designed in Layer 3 with CMOS to complete this process as shown in [Figure 6.20](#Chapter6.html#c06_fig20).

![image](images/PBPC0390-06-f20.jpg)

Figure 6.20 Inner-product operation on ReRAM crossbar

To fully map the incremental machine learning on the proposed 3D multilayer CMOS-ReRAM accelerator, there are following operations needed in CMOS-ASIC including sorting in (4.3), nonlinear mapping in (4.4) and division. [Figure 6.21](#Chapter6.html#c06_fig21) shows the detailed mapping of the supervised classification on the proposed 3D multilayer CMOS-ReRAM accelerator. The ReRAM logic layer (Layer 2) will work as vector core with parallel process elements for multiplication and summation. The scalar core is implemented to perform scalar operation including division. A sequential divider is implemented with five-stage pipelines to reduce critical path latency. Nonlinear mapping such as Sigmoid function for activation is also implemented in LUT (4.4). As a result, the whole training process including both feature extraction and classifier learning can be mapped to the proposed 3D multilayer CMOS-ReRAM accelerator with small accuracy loss accelerator with small accuracy loss.

![image](images/PBPC0390-06-f21.jpg)

Figure 6.21 Detailed pipelined and parallel mapping of CMOS-ASIC accelerator

#### 6.2.2 On-chip design for TNNs

TNNs are another prominent class of machine learning architectures in the present time. In this section, we will map a two-layer TNN-based inference processes according to the algorithm and network in Section 4.4. This section also discusses how to utilize the proposed 3D multilayer CMOS-ReRAM architecture to design the TNN accelerator.

##### 6.2.2.1 Mapping on multilayer architecture

Let us first discuss the CMOS layer design, which performs the high-level control of TNN computation. Then a highly parallel ReRAM-based accelerator is introduced with the TNN architecture and dot-product engine.

###### CMOS layer accelerator

To fully map TNN on the 3D multilayer CMOS-ReRAM accelerator, the CMOS logic needs to be designed mainly for logic control and synchronization using top-level state machine. It prepares the input data for computing cores, monitors the states of ReRAM logic computation and determines the computation layer of neural network. [Figure 6.22](#Chapter6.html#c06_fig22) shows the detailed mapping of the TNN on the proposed 3D multilayer CMOS-ReRAM accelerator. This is a folded architecture by utilizing the sequential operation of each layer on the neural network. The testing data will be collected from ReRAM memory through-silicon via (TSV) and then sent into vector core to perform vector–matrix multiplication through highly parallel processing elements in the ReRAM layer. The ReRAM layer has many distributed ReRAM-crossbar structures to perform multiplication in parallel. Then the computed output from ReRAM will be transferred to scalar score to perform accumulations. The scaler core can perform addition, subtraction and comparisons. Then the output from the scalar core will be sent to the sigmoid function model for activation matrix in a pipelined fashion, which performs the computation of (4.4). The activation matrix ![image](images/ch06_si555.gif)will be used for the next layer computation. As a result, the whole TNN inference process can be mapped to the 3D multilayer CMOS-ReRAM accelerator.

![image](images/PBPC0390-06-f22.jpg)

Figure 6.22 Data control and synchronization on the layer of CMOS with highly parallel ReRAM-based processing elements

In addition, to support TNN on ReRAM computation, a dedicated index LUT is needed. Since the weight matrix is actually folded into a high-dimensional tensor as shown in Figure 4.8, a correct index selection function called bijective function is designed. The bijective function for weight matrix index is also performed by the CMOS layer. Based on the top state diagram, it will choose the correct slice of tensor core ![image](images/ch06_si556.gif)by determining the ![image](images/ch06_si557.gif)index. Then the correct ReRAM-crossbar area will be activated to perform vector–matrix multiplication.

###### ReRAM layer accelerator

In the ReRAM layer, this section presents the design of ReRAM layer accelerator for highly parallel computation using single instruction multiple data method to support data parallelism.

**Highly parallel TNN accelerator on the ReRAM layer** The TNN accelerator has to be designed to support highly parallel tensor-train-matrix-by-vector multiplication by utilizing the associative principle of matrix product. According to (4.28), ![image](images/ch06_si558.gif)needs to be multiplied by ![image](images/ch06_si559.gif)matrices unlike the general neural network. As a result, if traditional matrix–vector multiplication in serial is applied, data need to be stored in the ReRAM array for ![image](images/ch06_si560.gif)times, which is time-consuming. Since the size of tensor cores in the TNN is much smaller than the weights in the general neural network, multiple matrix–vector multiplication engines can be placed in the ReRAM logic layer. When then input data are loaded, the index of ![image](images/ch06_si561.gif)can be known. For instance, one needs to compute ![image](images/ch06_si562.gif)given ![image](images/ch06_si563.gif)for the summation in (4.28). ![image](images/ch06_si564.gif)and ![image](images/ch06_si565.gif)in (4.28) can be precomputed in a parallel fashion before the input data ![image](images/ch06_si566.gif)are loaded.

As shown in [Figure 6.23](#Chapter6.html#c06_fig23), the tensor cores (TC1-6) are stored in the ReRAM logic layer. When the input data ![image](images/ch06_si567.gif)come, the index of each tensor core is loaded by the logic layer controllers first. The controller will write the according data from the tensor cores to ReRAM cells. As a result, the matrix–vector multiplication of ![image](images/ch06_si568.gif)can be performed in parallel to calculate the intermediate matrices while ![image](images/ch06_si569.gif)is in the loading process. After all the intermediate matrices are obtain, they can be multiplied by ![image](images/ch06_si570.gif)so that the operations in ReRAM logic layer can be efficient.

![image](images/PBPC0390-06-f23.jpg)

Figure 6.23 (a) ReRAM-based TNN accelerator; (b) tree-based parallel partial result multiplication; (c) ReRAM-based dot-product engine

**Highly parallel dot-product engine on the ReRAM layer** We further develop the digitalized ReRAM based dot-product engine on the ReRAM layer. The tensor-train-matrix-by-vector operation can be efficiently accelerated by the fast dot-product engine on the ReRAM layer, as shown in [Figure 6.23](#Chapter6.html#c06_fig23)(b). By taking correct index of cores, each operation can be divided into a vector-vector dot product operation. Here, we design the dot-product engine based on \[237\]. The output matrix is ![image](images/ch06_si571.gif), with input matrices ![image](images/ch06_si572.gif)and ![image](images/ch06_si573.gif)for better understanding. The overall equation is ![image](images/ch06_si574.gif)with ![image](images/ch06_si575.gif), ![image](images/ch06_si576.gif)and ![image](images/ch06_si577.gif). For every element in ![image](images/ch06_si578.gif), it follows

![image](images/ch06_si960.gif)

where ![image](images/ch06_si579.gif)and ![image](images/ch06_si580.gif)are the elements in ![image](images/ch06_si581.gif)and ![image](images/ch06_si582.gif), respectively. The basic idea of implementation is to split the matrix–vector multiplication to multiple inner-product operations of two vectors ![image](images/ch06_si583.gif)and ![image](images/ch06_si584.gif). Such multiplication can be expressed in binary multiplication by adopting fixed-point representation of ![image](images/ch06_si585.gif)and ![image](images/ch06_si586.gif):

![image](images/ch06_si961.gif)

where ![image](images/ch06_si587.gif)is the accelerated result from ReRAM crossbar. ![image](images/ch06_si588.gif)is the binary bit of ![image](images/ch06_si589.gif)with ![image](images/ch06_si590.gif)bit-width and ![image](images/ch06_si591.gif)is the binary bit of ![image](images/ch06_si592.gif)with ![image](images/ch06_si593.gif)bit-width. As mentioned above, bit-width ![image](images/ch06_si594.gif)and ![image](images/ch06_si595.gif)are decided during the algorithm level optimization. The matrix–vector multiplication based on (22) can be summarized in four steps on the ReRAM layer.

**Step 1: Index bijection**: Select the correct slice of tensor cores ![image](images/ch06_si596.gif), where a pair of ![image](images/ch06_si597.gif)determines a slice from ![image](images/ch06_si598.gif). In the current example, the ![image](images/ch06_si599.gif)and ![image](images/ch06_si600.gif)to represent two selected slices from cores ![image](images/ch06_si601.gif)and ![image](images/ch06_si602.gif).

**Step 2: Parallel digitizing**: It requires an ![image](images/ch06_si603.gif)ReRAM crossbar. Each inner product is produced ReRAM crossbar as shown in [Figure 6.23](#Chapter6.html#c06_fig23)(c). ![image](images/ch06_si604.gif)is set as crossbar input and ![image](images/ch06_si605.gif)is written in ReRAM cells. In the ![image](images/ch06_si606.gif)ReRAM crossbar, resistance of ReRAMs in each column are the same, but ![image](images/ch06_si607.gif)th among columns are different. As a result, the output of each column mainly depends on ladder-like threshold voltages ![image](images/ch06_si608.gif). If the inner-product result is ![image](images/ch06_si609.gif), the output of step 1 is like ![image](images/ch06_si610.gif), where ![image](images/ch06_si611.gif)and ![image](images/ch06_si612.gif).

**Step 3: XOR**: It is to identify the index of ![image](images/ch06_si613.gif)with the operation ![image](images/ch06_si614.gif). Note that ![image](images/ch06_si615.gif)only when ![image](images/ch06_si616.gif)and ![image](images/ch06_si617.gif)from Step 1. The mapping of ReRAM-crossbar input and resistance is also shown in 22(c), and threshold voltage configuration is ![image](images/ch06_si618.gif). Therefore, the index of ![image](images/ch06_si619.gif)is identified by XOR operation.

**Step 4: Encoding**: The third step produces ![image](images/ch06_si620.gif)in binary format as an encoder with the thresholds as Step 2. The input from the second step produces ![image](images/ch06_si621.gif)like result where only the ![image](images/ch06_si622.gif)input is ![image](images/ch06_si623.gif). As a result, only the ![image](images/ch06_si624.gif)row is read out and no current merge occurs in this step. The according binary format ![image](images/ch06_si625.gif)is an intermediate result and stored in the ![image](images/ch06_si626.gif)row, as shown in [Figure 6.23](#Chapter6.html#c06_fig23)(c). Encoding step needs an ![image](images/ch06_si627.gif)ReRAM crossbar, where ![image](images/ch06_si628.gif)is the number of bits in order to represent ![image](images/ch06_si629.gif)to ![image](images/ch06_si630.gif)in binary format.

By applying these four steps, one can map different tensor cores on ReRAM crossbars to perform the matrix–vector multiplication in parallel. Compared to the state-of-the-art realizations, this approach can perform the matrix–vector multiplication faster and more energy-efficient.

##### 6.2.2.2 Mapping TNN on single-layer architecture

Further, this section shows how to map a two-layer TNN-based inference processes according to the algorithm and network in Section 4.4. This section further discusses how to utilize the 3D single-layer CMOS-ReRAM architecture to design the TNN accelerator. Compared to the mapping in Section 2.2, a higher parallelism can be achieved with a distributed mapping.

###### TNN accelerator design

According to (4.28), ![image](images/ch06_si631.gif)needs to be multiplied by ![image](images/ch06_si632.gif)matrices unlike the general neural network. In this equation, it is only needed to take a slice of 3D matrix (i.e., a 2-D matrix) from each tensor core to perform the matrix–vector multiplication. Therefore, the computation complexity can be significantly reduced. We show the detailed accelerator design between two hidden layers of TNN in [Figure 6.24](#Chapter6.html#c06_fig24). Since the parameters of the neural network are compressed, one can store all the weights of TNN in ReRAM crossbar, following Figure 5.12(b). The input data ![image](images/ch06_si633.gif)is processed by several tensor cores, CMOS pooling and activation serially.

![image](images/PBPC0390-06-f24.jpg)

Figure 6.24 Mapping details of highly parallel 3D single-layer CMOS-ReRAM accelerator for TNN

The detailed design of a tensor core is also shown in [Figure 6.24](#Chapter6.html#c06_fig24). In each tensor core, one has to store different slices of the 3D matrix into different ReRAM crossbars. Since only one 2D matrix is used at a time, two tensor-core Multiplexers (MUX) are used so that only one matrix is connected to the input voltage as well as the output ADC. The TC selection module controls the input and output MUX according to ![image](images/ch06_si634.gif)and ![image](images/ch06_si635.gif). For the tensor cores in the middle, the ADC/DAC pair can be removed since one does not need a digital representation for ReRAM-crossbar inputs.

###### Benefits summary of TNN on 3D CMOS-ReRAM architecture

From the algorithm optimization perspective, such tensorization can benefit of implementing large neural networks. First, by performing tensorization, the size of neural network can be compressed. Moreover, the computation load can also be reduced by adopting small tensor ranks. Second, a tensorization of weight matrix can decompose the big matrix into many small tensor-core matrices, which can effectively reduce the configuration time of ReRAM. Lastly, the multiplication of small matrix can be performed in a highly parallel fashion on ReRAM to speed up the large neural network processing time.

From the hardware computing architecture perspective, the proposed 3D CMOS-ReRAM accelerator can greatly improve the energy efficiency and neural network processing speed. The matrix–vector multiplication can be intrinsically implemented by ReRAM crossbar. Compared to CMOS, a multibit tensor-core weight can be represented by a single ReRAM, and the addition can be realized by current merging. Moreover, as all the tensor cores for the neural network weights are stored in the ReRAM devices, better area efficiency can be achieved. The power consumption of the proposed CMOS-ReRAM is much smaller than the CMOS implementation due to nonvolatile property of ReRAM. In the TNN accelerator design shown in [Figure 6.24](#Chapter6.html#c06_fig24), only a slice of the 3D matrix is active while most of the matrices are inactive. For traditional CMOS realization, it costs huge static power for the inactive tensor-core weights. But in the discussed architecture, the inactive matrices do not consume power so that the energy utilization is high, resulting a better energy efficiency.

#### 6.2.3 Experimental evaluation of machine learning algorithms on 3D CMOS-ReRAM

##### 6.2.3.1 On-chip design for SLFN-based face recognition

###### Experimental settings

In the experiment, different baselines are implemented for performance comparisons. The detail of each baseline is listed as follows:

**Baseline 1**: General processor. The general process implementation is based on MATLAB on a computer server with 3.46 GHz core and 64.0 GB RAM.

**Baseline 2**: GPU. The GPU implementation is performed by MATLAB GPU parallel toolbox on the same server. An Nvidia GeForce GTX 970 is used for the acceleration of matrix–vector multiplication operations for learning on neuron network.

**Baseline 3**: 3D-CMOS-ASIC. The 3D-CMOS-ASIC implementation with proposed architecture is done by Verilog with 1 GHz working frequency based on CMOS 65nm low power PDK. Power, area and frequency are evaluated through Synopsys DC compiler (D-2010.03-SP2). TSV model in \[238\] is included for area and power evaluation. 512 vertical TSVs are assumed between layers to support communication and parallel computations \[239\].

**Proposed 3D-ReRAM-CMOS**: The settings of CMOS evaluation and TSV model are the same as Baseline 3. For the ReRAM-crossbar design evaluation, the resistance of ReRAM is set as ![image](images/ch06_si636.gif)and ![image](images/ch06_si637.gif)as on-state and off-state resistance respectively according to \[206\] with working frequency of 200 MHz.

###### Performance evaluation

**Scalability analysis** To evaluate the proposed 3D multilayer CMOS-ReRAM architecture, we performed the scalability analysis of energy, delay and area on glass UCI data set \[184\]. In SLFN, the number of hidden nodes may change depending on the accuracy requirement. As a result, the improvement of proposed accelerator with different ![image](images/ch06_si638.gif)from ![image](images/ch06_si639.gif)to ![image](images/ch06_si640.gif)is evaluated as shown in [Figure 6.25](#Chapter6.html#c06_fig25). With the increasing ![image](images/ch06_si641.gif), more computing units are designed in 3D-CMOS-ASIC and ReRAM crossbar to evaluate the performance. When ![image](images/ch06_si642.gif)reaches ![image](images/ch06_si643.gif), ReRAM crossbar can achieve ![image](images/ch06_si644.gif)area-saving and ![image](images/ch06_si645.gif)energy-saving compared to 3D-CMOS-ASIC. In [Figure 6.25](#Chapter6.html#c06_fig25)(d), energy-delay-product (EDP) of ReRAM crossbar increases faster than 3D-CMOS-ASIC. As the size of ReRAM crossbar is proportional to square of ![image](images/ch06_si646.gif), the EDP improvement of ReRAM crossbar is less with larger ![image](images/ch06_si647.gif). However, it still shows great advantage in EDP with ![image](images/ch06_si648.gif)better than 3D-CMOS-ASIC when ![image](images/ch06_si649.gif), which is large number of hidden node for glass benchmark of nine features.

![image](images/PBPC0390-06-f25.jpg)

Figure 6.25 Scalability study of hardware performance with different hidden node numbers for (a) area, (b) delay, (c) energy and (d) EDP

**Bit-width configuration analysis** [Table 6.9](#Chapter6.html#c06_tbl9) shows the testing accuracy under different data sets \[184, 240\], and configurations for machine learning of support vector machine (SVM) and SLFN. It shows that the accuracy of classification is not very sensitive to the ReRAM configuration bits. For example, the accuracy of Iris data set is working with negligible accuracy at ![image](images/ch06_si656.gif)ReRAM bit-width. When the ReRAM bit-width increased to ![image](images/ch06_si657.gif), it performs the same as ![image](images/ch06_si658.gif)bit-width configurations. Similar observation is found in \[236\] by truncating algorithms with limited precision for better energy efficiency. Please note that training data and weight-related parameters are quantized to perform matrix–vector multiplication on ReRAM-crossbar accelerator. [Figure 6.26](#Chapter6.html#c06_fig26) shows the energy comparisons under different bit-width configurations for CMOS and ReRAM under the same accuracy requirements. An average of ![image](images/ch06_si659.gif)energy saving can be achieved for the same number of bit-width configurations. The energy consumption is normalized by the CMOS ![image](images/ch06_si660.gif)bit-width configuration. Furthermore, we can observe that not always smaller number of bits achieves better energy saving. Fewer number of bit-width may require much larger neuron network to perform required classification accuracy. As a result, its energy consumption increases.

![image](images/PBPC0390-06-f26.jpg)

Figure 6.26 Energy-saving comparison under different bit-width of CMOS and ReRAM with the same accuracy requirement

Table 6.9 Testing accuracy of machine learning techniques under different data set and configurations (normalized to all 32 bits)

![image](images/tab6.9.jpg)

**Performance analysis** [Figure 6.27](#Chapter6.html#c06_fig27) shows the classification values on image data \[240\] with an example of five classes. As mentioned before, the index with maximum values (highlighted in red) is selected to indicate the class of test case. A few sample images are selected. Please note that ![image](images/ch06_si713.gif)and ![image](images/ch06_si714.gif)images aasses. In [Table 6.10](#Chapter6.html#c06_tbl10), performance comparisons among MATLAB, 3D-CMOS-ASIC and 3D multilayer CMOS-ReRAM accelerator are presented, and the acceleration of each procedure based on the formula described is also addressed. Among the three implementations, 3D multilayer CMOS-ReRAM accelerator performs the best in area, energy and speed. Compared to MATLAB implementation, it achieves ![image](images/ch06_si715.gif)speedup, ![image](images/ch06_si716.gif)energy-saving and ![image](images/ch06_si717.gif)area-saving. We also design a 3D-CMOS-ASIC implementation with similar structure as 3D multilayer CMOS-ReRAM accelerator with better performance compared to MATLAB. The proposed 3D multilayer CMOS-ReRAM 3D accelerator is ![image](images/ch06_si718.gif)speedup, ![image](images/ch06_si719.gif)energy-saving and ![image](images/ch06_si720.gif)area-saving compared to 3D CMOS-ASIC. To compare the performance with GPU, we also implemented the same code using MATLAB GPU parallel toolbox. It takes ![image](images/ch06_si721.gif)for training benchmark CIFAR-10, which is ![image](images/ch06_si722.gif)faster than CPU. Comparing to our proposed 3D multilayer CMOS-ReRAM architecture, our work is ![image](images/ch06_si723.gif)speedup and ![image](images/ch06_si724.gif)energy saving. Detailed comparisons of each step are not shown due to the limited space of table.

![image](images/PBPC0390-06-f27.jpg)

Figure 6.27 Online machine learning for image recognition on the proposed 3D multilayer CMOS-ReRAM accelerator using benchmark CIFAR-10

Table 6.10 Performance comparison under different software and hardware implementations

![image](images/tab6.10.jpg)

##### 6.2.3.2 Results of TNN-based on-chip design with 3D multilayer architecture

###### Experimental settings

In the experiment, we have implemented different baselines for performance comparisons. The detail of each baseline is listed as follows:

**Baseline 1**: General CPU processor. The general process implementation is based on MATLAB with optimized C-program. The computer server is with ![image](images/ch06_si725.gif)cores of ![image](images/ch06_si726.gif)GHz and ![image](images/ch06_si727.gif)GB RAM.

**Baseline 2**: General GPU processor. The general-purpose GPU implementation is based on the optimized C-program and MATLAB parallel computing toolbox with CUDA-enabled Quadro 5000 GPU \[241\].

**Baseline 3**: 3D CMOS-ASIC. The 3D CMOS-ASIC implementation with proposed architecture is done by Verilog with ![image](images/ch06_si728.gif)GHz working frequency based on CMOS 65nm low power PDK. Power, area and frequency are evaluated through Synopsys DC compiler (D-2010.03-SP2). TSV area, power and delay are evaluated based on Simulator DESTINY \[218\] and fine-grained TSV model CACTI-3DD \[242\]. The buffer size of the top layer is set ![image](images/ch06_si729.gif)MB to store tensor cores with 256 bits data width. The TSV area is estimated to be ![image](images/ch06_si730.gif)with capacitance of ![image](images/ch06_si731.gif)fF.

**Proposed 3D CMOS-ReRAM**: The settings of CMOS evaluation and TSV model are the same as Baseline 2. For the ReRAM-crossbar design evaluation, the resistance of ReRAM is set as ![image](images/ch06_si732.gif)and ![image](images/ch06_si733.gif)as on-state and off-state resistance and 2V SET/RESET voltage according to \[139\] with working frequency of ![image](images/ch06_si734.gif)MHz. The CMOS and ReRAM integration is evaluated based on \[64\].

To evaluate the proposed architecture, we apply UCI \[184\] and MNIST \[232\] data set to analyze the accelerator scalability, model configuration analysis and performance analysis ([Table 6.11](#Chapter6.html#c06_tbl11)). The model configuration is performed on MATLAB first using tensor-train toolbox \[204\] before mapping on the 3D CMOS-ReRAM architecture. To evaluate the model compression, we compare our method with support vector decomposition (SVD)-based node-pruned method \[243\] and general neural network \[53\]. The energy consumption and speedup are also evaluated. Note that the code for performance comparisons is based on optimized C-Program and deployed as the mex-file in the MATLAB environment.

Table 6.11 Bandwidth improvement under different number of hidden nodes for MNIST data set

![image](images/tab6.11.jpg)

###### Performance evaluation

**3D Multilayer CMOS-ReRAM accelerator scalability analysis** Since neural network process requires frequent network weights reading, memory read latency optimization configuration is set to generate ReRAM memory architecture. By adopting 3D implementation, simulation results show that memory read and write bandwidth can be significantly improved by 51.53% and 6.51%, respectively, comparing to 2D implementation. For smaller number of hidden nodes, read/write bandwidth is still improved but the bottleneck shifts to the latency of memory logic control.

To evaluate the proposed 3D multilayer CMOS-ReRAM architecture, we perform the scalability analysis of energy, delay and area on MNIST data set \[232\]. This data set is applied to multilayer neural network and the number of hidden nodes may change depending on the accuracy requirement. As a result, the improvement of proposed accelerator with different ![image](images/ch06_si741.gif)from ![image](images/ch06_si742.gif)to ![image](images/ch06_si743.gif)is evaluated as shown in [Figure 6.28](#Chapter6.html#c06_fig28). With the increasing ![image](images/ch06_si744.gif), more computing units are designed in 3D CMOS-ASIC and ReRAM crossbar to evaluate the performance. The neural network is defined as a four-layer network with weights ![image](images/ch06_si745.gif), ![image](images/ch06_si746.gif)and ![image](images/ch06_si747.gif). For computation delay, GPU, 3D CMOS-ASIC and 3D CMOS-ReRAM are close when ![image](images/ch06_si748.gif)according to [Figure 6.28](#Chapter6.html#c06_fig28)(b). When ![image](images/ch06_si749.gif)reaches ![image](images/ch06_si750.gif), 3D CMOS-ReRAM can achieve ![image](images/ch06_si751.gif)area-saving and ![image](images/ch06_si752.gif)energy-saving compared to 3D CMOS-ASIC. Although the computational complexity is not linearly related to the number of hidden node numbers, both energy consumption and EDP of ReRAM crossbar increase with the rising number of hidden node. According to [Figure 6.28](#Chapter6.html#c06_fig28)(d), the advantage of the hybrid accelerator becomes smaller when the hidden node increases, but it can still have a ![image](images/ch06_si753.gif)better EDP compared to the 3D CMOS-ASIC when the hidden node number is ![image](images/ch06_si754.gif).

![image](images/PBPC0390-06-f28.jpg)

Figure 6.28 Scalability study of hardware performance with different hidden node numbers for (a) area, (b) delay, (c) energy and (d) EDP

**Model configuration analysis** [Figure 6.29](#Chapter6.html#c06_fig29) shows the testing accuracy and running time comparisons for MNIST data set. It shows a clear trend of accuracy improvement with increasing number of hidden nodes. The running time between TNN and general neural network is almost the same. This is due to the relative large rank ![image](images/ch06_si755.gif)and computation cost of ![image](images/ch06_si756.gif). Such tensor-train-based neural network achieve ![image](images/ch06_si757.gif)and ![image](images/ch06_si758.gif)model compression within 2% accuracy loss under 10,24 and 20,48 number of hidden nodes, respectively. Details on model compression are shown in [Table 6.12](#Chapter6.html#c06_tbl12). From [Table 6.12](#Chapter6.html#c06_tbl12), we can observe that the compression rate is directly connected with the rank ![image](images/ch06_si759.gif), where the memory storage can be simplified as ![image](images/ch06_si760.gif)from ![image](images/ch06_si761.gif)but not directly linked to the number of hidden nodes. One can also observe that by setting tensor-core rank to 35, ![image](images/ch06_si762.gif)model compression can be achieved with acceptable accuracy loss. Therefore, initialization of a low-rank core and the SVD split of supercore in MALS algorithm are important steps to reduce the core rank and increase compression rate.

![image](images/PBPC0390-06-f29.jpg)

Figure 6.29 Testing time and accuracy comparison between TTN and general neural network (Gen.) with varying number of hidden nodes

Table 6.12 Model compression under different number of hidden nodes and tensor ranks on MNIST data set

![image](images/tab6.12.jpg)

**Bit-width configuration analysis** To implement the whole neural network on the proposed 3D multilayer CMOS-ReRAM accelerator, the precision of real values requires a careful evaluation. Compared to the software double-precision floating point format (64-bit), values are truncated into finite precision. By using the greedy search method, an optimal point for hardware resource (small bit-width) and testing accuracy can be achieved.

Our tensor-train-based neural network compression techniques can work with low-precision value techniques to further reduce the data storage. [Table 6.13](#Chapter6.html#c06_tbl13) shows the testing accuracy by adopting different bit-width on UCI data sets \[184\] and MNIST \[232\]. It shows that accuracy of classification is not very sensitive to the ReRAM configuration bits for UCI data set. For example, the accuracy of Iris data set is working well with negligible accuracy at 5 ReRAM bit-width. When the ReRAM bit-width increased to 6, it performs the same as 32 bit-width configurations. Please note that the best configuration of quantized model weights varies for different data sets and requires careful evaluation.

Table 6.13 Testing accuracy of learning techniques under different data set and bit-width configuration

![image](images/tab6.13.jpg)

**Performance analysis** In [Table 6.14](#Chapter6.html#c06_tbl14), performance comparisons among C-Program-optimized CPU performance, GPU performance , 3D CMOS-ASIC and 3D multilayer CMOS-ReRAM accelerator are presented for ![image](images/ch06_si831.gif)testing images. The acceleration of each layer is also presented for three layers (![image](images/ch06_si832.gif), ![image](images/ch06_si833.gif)and ![image](images/ch06_si834.gif)). Please note that the dimension of weight matrices are decomposed into ![image](images/ch06_si835.gif)and ![image](images/ch06_si836.gif)with ![image](images/ch06_si837.gif)bit-width and maximum rank 6. The compression rate is ![image](images/ch06_si838.gif)and ![image](images/ch06_si839.gif)with and without bit truncation. Here, the compression rate is the ratio of volume of weights before and after compression. Among the four implementations, 3D multilayer CMOS-ReRAM accelerator performs the best in area, energy and speed. Compared to CPU, it achieves ![image](images/ch06_si840.gif)speedup, ![image](images/ch06_si841.gif)energy-saving and ![image](images/ch06_si842.gif)area-saving. For GPU-based implementation, our proposed 3D CMOS-ReRAM architecture achieves ![image](images/ch06_si843.gif)speedup and ![image](images/ch06_si844.gif)energy-saving. We also design a 3D CMOS-ASIC implementation with similar structure as 3D multilayer CMOS-ReRAM accelerator with better performance compared to CPU- and GPU-based implementations. The proposed 3D multilayer CMOS-ReRAM 3D accelerator is ![image](images/ch06_si845.gif)speedup, ![image](images/ch06_si846.gif)energy-saving and ![image](images/ch06_si847.gif)area-saving compared to 3D CMOS-ASIC.

Table 6.14 Performance comparison under different hardware implementations on MNIST data set with 10,000 testing images

![image](images/tab6.14.jpg)

The throughput and energy efficiency for these four cases are also summarized in [Table 6.14](#Chapter6.html#c06_tbl14). For energy efficiency, the discussed accelerator can achieve 1,499.83 GOPS/W, which has ![image](images/ch06_si848.gif)better energy efficiency comparing to 3D the CMOS-ASIC result (347.29 GOPS/W). In comparison to our GPU baseline, it has ![image](images/ch06_si849.gif)better energy efficiency comparing to NVIDIA Quadro 5000. For a newer GPU device (NVIDIA Tesla K40), which can achieve 1,092 GFLOPS and consume 235 W \[241\], our proposed accelerator has ![image](images/ch06_si850.gif)energy-efficiency improvement.

##### 6.2.3.3 TNN-based distributed on-chip design on 3D single-layer architecture

###### Experiment settings

In the experiment, we have implemented different baselines for performance comparisons. The detail of each baseline is listed as follows:

**Baseline 1**: General processor (CPU/GPU). The general processor implementation is based on optimized C-program on a computer server with ![image](images/ch06_si851.gif)cores of ![image](images/ch06_si852.gif)GHz and ![image](images/ch06_si853.gif)GB RAM. A Nvidia GeForce GTX 970 is used as reference for the GPU performance comparison.

**Baseline 2**: 2D CMOS-ASIC. The 2D CMOS-ASIC implementation with proposed architecture is done by Verilog with ![image](images/ch06_si854.gif)GHz working frequency based on CMOS 65-nm low-power PDK. Power, area and frequency are evaluated through Synopsys DC compiler (D-2010.03-SP2).

**Baseline 3**: 3D CMOS-ASIC. The 3D CMOS-ASIC implementation is the same as 2D version but features with TSV communication. TSV area, power and delay are evaluated based on Simulator DESTINY \[218\] and fine-grained TSV model CACTI-3DD \[242\]. The buffer size of the top layer is SRAM based and set ![image](images/ch06_si855.gif)MB to store tensor cores. The TSV area is estimated to be ![image](images/ch06_si856.gif)with capacitance of ![image](images/ch06_si857.gif)fF. TSV model in \[238\] is included for area and power evaluation; 512 vertical TSVs are assumed between layers to support communication and parallel computations \[239\].

**Proposed 3D CMOS-ReRAM**: The settings of CMOS evaluation and TSV model are the same as Baseline 3. For the ReRAM-crossbar design evaluation, the resistance of ReRAM is set as ![image](images/ch06_si858.gif)and ![image](images/ch06_si859.gif)as on-state and off-state resistance and 2V SET/RESET voltage according to \[206\] with working frequency of ![image](images/ch06_si860.gif)MHz. The CMOS and ReRAM integration is evaluated based on \[64\].

To evaluate the proposed architecture, we apply CIFAR-10 \[233\] and MNIST \[232\] data set to analyze the neural network compression and architecture performance analysis. The energy-efficient neural network is designed on MATLAB first using Tensor-train toolbox \[204\] and tensor network \[196\]. After determining the network configuration and compression rate, it is then fully optimized using C-program as CPU-based result. Then we apply nonuniform quantization to perform tensor-core quantization before mapping on the 3D CMOS-ReRAM architecture. To evaluate the model compression, we compare our method with SVD-based node-pruned method \[243\] and general neural network \[53\]. The energy efficiency and speedup are also evaluated.

###### Energy-efficient tensor-compressed neural network

To achieve high compression rate, we first apply nonuniform quantization for tensor-core weights. As shown in [Figure 6.30](#Chapter6.html#c06_fig30), the probability density function of tensor-core weights can be modeled as Gaussian distribution. For such known pdf, we can effectively find the optimal level representative values with minimized mean square error. [Figure 6.31](#Chapter6.html#c06_fig31) shows the trade-off between accuracy, bit-width and compression rate on MNIST data set with three-layer neural network. [Table 6.15](#Chapter6.html#c06_tbl15) shows the clear effect of quantization on the compression rate. In general, bit-width quantization can help improve ![image](images/ch06_si861.gif)more compression rate on neural network.

![image](images/PBPC0390-06-f30.jpg)

Figure 6.30 TNN Layer 1 weight and Layer 2 weight histogram with approximate Gaussian distribution

![image](images/PBPC0390-06-f31.jpg)

Figure 6.31 Compression rate and accuracy with increasing bit-width

Table 6.15 Model compression under different numbers of hidden nodes and tensor ranks on MNIST data set

![image](images/tab6.15.jpg)

To have a fair comparison with \[245\], we also adopted LeNet-300-100 network \[232\], which is a two hidden FC layer network (![image](images/ch06_si872.gif), ![image](images/ch06_si873.gif), ![image](images/ch06_si874.gif)). Under such configuration, \[245\] can achieve ![image](images/ch06_si875.gif)compression with error rate 1.58% using quantization (![image](images/ch06_si876.gif)\-bit precision), pruning and Huffman coding techniques. By adopting ![image](images/ch06_si877.gif)bit-width configuration on tensorized layer, we can achieve even more compression rate (![image](images/ch06_si878.gif)) with maintained accuracy (1.63%).

We also apply the proposed TNN to CIFAR-10 data set. CIFAR-10 data set consists of ![image](images/ch06_si879.gif)images with size of ![image](images/ch06_si880.gif)under ten different classes. We adopt LeNet-alike neural network \[232\] and we use a two-layer FC TNN to replace the last two FC layers, which is ![image](images/ch06_si881.gif)and ![image](images/ch06_si882.gif). By adopting nonuniform tensor-core bit quantization (8 bit-width), we can achieve ![image](images/ch06_si883.gif)compression on FC layers and ![image](images/ch06_si884.gif)on the whole network, respectively, with the same accuracy loss (2%).

###### Energy-efficient 3D CMOS-ReRAM architecture

Since neural network process requires frequent network weights reading, memory read latency optimization configuration is set to generate ReRAM memory architecture. By adopting 3D implementation, simulation results show that memory read and write bandwidth can be improved by 51.53% and 6.51%, respectively, comparing to 2D implementation as shown in [Table 6.16](#Chapter6.html#c06_tbl16). For smaller number of hidden nodes, read/write bandwidth is still improved but the bottleneck shifts to the latency of memory logic control.

Table 6.16 Bandwidth improvement under different number of hidden nodes for MNIST data set

![image](images/tab6.16.jpg)

In [Table 6.17](#Chapter6.html#c06_tbl17), performance comparisons among general processors, 2D CMOS-ASIC, 3D CMOS-ASIC and 3D CMOS-ReRAM accelerator are presented, and the acceleration of each layer is also presented for two layers (![image](images/ch06_si926.gif)and ![image](images/ch06_si927.gif)). Please note that input weight is decomposed into ![image](images/ch06_si928.gif)and ![image](images/ch06_si929.gif)with maximum rank 6 and 6 bit-width. Among the four implementations, 3D CMOS-ReRAM accelerator performs the best in area, energy and speed. Compared to 2D CMOS implementation, it achieves ![image](images/ch06_si930.gif)speedup, ![image](images/ch06_si931.gif)energy-saving and ![image](images/ch06_si932.gif)area-saving. We also design a 3D CMOS-ASIC implementation with similar structure as 3D CMOS-ReRAM accelerator with better performance compared to 2D CMOS-ASIC. The proposed 3D CMOS-ReRAM accelerator is ![image](images/ch06_si933.gif)speedup, ![image](images/ch06_si934.gif)energy-saving and ![image](images/ch06_si935.gif)area-saving compared to 3D CMOS-ASIC. We also performed the mapping of uncompressed neural network on 3D CMOS-ReRAM architecture. In addition, for CIFAR-10 data set, we estimate ![image](images/ch06_si936.gif)and ![image](images/ch06_si937.gif)energy-saving comparing to 2D CMOS-ASIC and 3D CMOS-ASIC architecture, respectively.

Table 6.17 Performance comparison under different hardware implementations on MNIST data set (10k test images)

![image](images/tab6.17.jpg)

For energy efficiency, our proposed accelerator can achieve 1,055.95 GOPS/W, which is equivalent to 7.661 TOPS/W for uncompressed neural network. Our proposed TNN accelerator can also achieve ![image](images/ch06_si938.gif)better energy efficiency comparing to 3D CMOS-ASIC result (441.36 GOPS/W), and ![image](images/ch06_si939.gif)better energy efficiency comparing to Nvidia Tesla K40, which can achieve 1,092 GFLOPS and consume 235 W.

### *Part III*  
**Case studies**

## *Chapter 7*  
**Large-scale case study: accelerator for ResNet**

### 7.1 Introduction

A residual network (ResNet) is a convolutional neural network (CNN)-based network with much deeper hierarchical architecture using the residual connection \[246,247\], which has become the common network model for deep learning. It is, however, quite challenging to realize the ResNet into terminal hardware with efficient interference \[248–251\] such as high throughput (TOPs) yet low power (mW). It requires a completed re-examination from both machine learning algorithm as well as underneath hardware.

First from machine learning algorithm perspective, to achieve a deep learning at terminal hardware, the network needs to be simplified. For example, a ResNet-50 network contains almost 50 convolution layers, which dominate the network complexity. As most convolution filter now is a small-sized (3 × 3, 5 × 5, etc.) operator. A direct-truncated quantization method has been reported in recent work \[252\]. Lately, some approaches \[253–255\] demonstrate their quantization feasibility of using lowbitwidth weights and activations, thus considerably reducing the memory requirement and computation complexity. Low-bitwidth gradients \[256\] are further generalized to train CNNs. Other works perform the quantization after network training or apply the straight-through estimator on CNNs \[257\]. Moreover, binarized neural networks (BNNs) are introduced \[222,224\] and further implemented on a digital resistive random-access memory (ReRAM)-based accelerator. While some of these methods have shown good performances with small-scale network models \[258–260\], however, none has applied a trained quantization strategy to large-scale networks (e.g., ResNet-50) on large-scale classification tasks (e.g., ImageNet) with certain accuracy

Next, from hardware and device perspective, traditional computing architecture needs significant data migration between memory and processor. It leads to low efficiency for both bandwidth and energy for machine learning, especially the deeper ResNet. The recent emerging nonvolatile memory (NVM) technologies have shown significantly reduced standby power as well as the possibility for in/near-memory computing \[225,261–263\]. For example, the ReRAM device \[57,62,264\] in crossbar can be used to store the weights and also to perform the convolution

For this case study, we have developed a quantized large-scale ResNet-50 network using ImageNet \[265\] benchmark with high accuracy. We further show that 168 ReRAM-based machine learning the quantized ResNet-50 network can be realized on ReRAM crossbar with significantly improved throughput and energy efficiency. The findings in this chapter can be outlined as follows:

1.  We adopt a trained quantization strategy with *all-integer computations* of the *large-scale* deep ResNet, for the first time, to such low-bitwidth subject to an accuracy control.
2.  We propose an algorithm-hardware codesign of the complimentary metal oxide semiconductor (CMOS)-ReRAM accelerator with novel digital-to-analog converter (DAC)/analog-to-digital converter (ADC) circuits developed.

Experiment results show that the proposed accelerator can achieve ![image](images/ch07_si4.gif)speedup and six-magnitude more energy efficiency than a central processing unit (CPU)-based implementation; ![image](images/ch07_si5.gif)speedup and four-magnitude more energy efficiency compared to a graphics processing unit (GPU)-based implementation; and ![image](images/ch07_si6.gif)faster and ![image](images/ch07_si7.gif)more energy efficiency than a CMOS-application specific integrated circuit (ASIC)-based implementation.

### 7.2 Deep neural network with quantization

The traditional direct implementation of the CNN-based network would require unnecessary software and hardware resources with poor parallelism. Previous work in \[256,266\] suggests a neural network using quantized constraints during training. In this section, we propose a hardware-friendly algorithm design of the large-scale ResNet model with quantized parallelism for convolution, residual block, batch normalization (BN), max-pooling and activation function. Instead of traditional quantization methods carrying out original 32-bit floating-point arithmetic with additional weight/activation quantization process, we present the all-integer arithmetic with quantized variables and computations only during both training and inference. Due to the remarkable compression on computational complexity and storage size, it becomes feasible to further implement the quantized network on ReRAM crossbar, which will be discussed in Section 7.4.

#### 7.2.1 Basics of ResNet

The deep ResNet has achieved outstanding performance in many applications due to its effectiveness. Different from the traditional CNN-based network structure, ResNet utilizes a residual connection to address the degradation problem by training a very deep network.

A ResNet is composed of a series of residual blocks, and each residual block contains several stacked convolutional layers. The rectified linear unit (ReLU) layers \[267\] and the BN layers \[190\] are also regarded as the component of convolutional layers in a ResNet. Specifically, we adopt a ResNet with ![image](images/ch07_si8.gif)layers (ResNet-50) \[246\] that is substantially deep to extract rich and discriminative features. The specific structure of ResNet-50 is shown in [Figure 7.1](#Chapter7.html#c07_fig1), including ![image](images/ch07_si9.gif)residual blocks and each contains three convolution layers. There is an add-residual operation at the end of each residual block, which can be represented by

![image](images/c07_eqn1.gif)

where ![image](images/ch07_si10.gif)and ![image](images/ch07_si11.gif)denote the input and output feature matrices of the residual block, meanwhile ![image](images/ch07_si12.gif)can be considered as the input of the next residual block, and the function ![image](images/ch07_si13.gif)denotes the residual mapping to be learned.

![image](images/PBPC0390-07-f01.jpg)

Figure 7.1 Detailed structure of ResNet-50: 49 convolution layers and 1 FC layer

#### 7.2.2 Quantized convolution and residual block

The convolution is the most expensive computation of ResNet and any other CNN-based network. Recently, the low-bitwidth convolution in \[188,256\] has shown the promising performance, which quantizes the convolution with low-bitwidth parameters to reduce the hardware resource with considerable accuracy.

First, we present the low-bitwidth convolution with 4-bit quantized values as ![image](images/ch07_si14.gif)for weight matrices. It should be noted that we quantize weights to the powers of ![image](images/ch07_si15.gif). In this way, the quantization algorithm can strike a balance between model compactness and capacity, which has been experimentally verified by testing several realizations from the state-of-the-arts (reported in Section 5.3.1). Furthermore, half voltage operating scheme \[268\] is applied to overcome the sneak-path problem, and the large intervals of weights will help to maintain high robustness under device variation (reported in Section 5.3.2). As shown in [Figure 7.2](#Chapter7.html#c07_fig2)(a), assuming ![image](images/ch07_si16.gif)is the full-precision element and ![image](images/ch07_si17.gif)is the quantized-valued element of weight matrix ![image](images/ch07_si18.gif)in the ![image](images/ch07_si19.gif)th layer, they have the approximation as ![image](images/ch07_si20.gif)with a nonnegative scaling factor ![image](images/ch07_si21.gif). Each weight element in convolution layers can be 4-bit quantized as follows:

![image](images/ch07_eqn2.gif)

where ![image](images/ch07_si22.gif)represents the proposed 4-bit quantization strategy, and ![image](images/ch07_si23.gif)is a nonnegative threshold parameter, which can be calculated as

![image](images/ch07_eqn3.gif)

where ![image](images/ch07_si24.gif)is the number of elements in weight matrix. Also we develop a 4-bit quantization strategy for the features based on \[256\], which quantizes a real-number feature element ![image](images/ch07_si25.gif)to a 4-bit feature element ![image](images/ch07_si26.gif)of feature matrix ![image](images/ch07_si27.gif)in ![image](images/ch07_si28.gif)th layer. This strategy is defined as follows:

![image](images/ch07_eqn4.gif)

where the ![image](images/ch07_si29.gif)function takes the nearest integer (takes the bigger integer if the decimal part is exactly ![image](images/ch07_si30.gif)). Therefore, the 4-bit quantized feature ![image](images/ch07_si31.gif)has the value range as ![image](images/ch07_si32.gif), which is shown in [Figure 7.2](#Chapter7.html#c07_fig2)(b).

![image](images/PBPC0390-07-f02.jpg)

Figure 7.2 4-bit quantization strategy of (a) weight and (b) feature

Having both 4-bit features and weights, we perform the 4-bit quantized convolution as

![image](images/ch07_eqn5.gif)

where ![image](images/ch07_si33.gif)and ![image](images/ch07_si34.gif)are the 4-bit quantized feature and weight element, and ![image](images/ch07_si35.gif)is the computation result. Here, ![image](images/ch07_si36.gif), ![image](images/ch07_si37.gif)and ![image](images/ch07_si38.gif)are mode sizes of the features and ![image](images/ch07_si39.gif), ![image](images/ch07_si40.gif)and ![image](images/ch07_si41.gif)are those of the weight kernels, which can be seen in [Figure 7.3](#Chapter7.html#c07_fig3). Compared with a real-valued CNN-based network in the full-precision data format, since the weights and features can be stored in 4-bit, both software and hardware resources required for the quantized convolutional layer, called the QConv, can be significantly reduced. Meanwhile, the QConv with 4-bit parameters leads to a higher energy efficiency and parallelism when implemented on the in-memory computing devices.

![image](images/PBPC0390-07-f03.jpg)

Figure 7.3 Computation flow of deep residual network ResNet-50 with 4-bit quantization

For residual block described in (2.1), we perform the proposed optimizations by straightforwardly replacing the elements in ![image](images/ch07_si42.gif), ![image](images/ch07_si43.gif), ![image](images/ch07_si44.gif), ![image](images/ch07_si45.gif)and ![image](images/ch07_si46.gif), as shown in [Figure 7.3](#Chapter7.html#c07_fig3). Therefore, the add-residual operation at the end of each residual block is also quantized as 4-bit.

#### 7.2.3 Quantized BN

BN accelerates the training process and reduces the overall impact of the weight scale \[190\]. The normalization procedure is required to stabilize the deep ResNet. However, in the original CNN-based network, BN requires many multiplications (calculating the full-precision deviation and dividing by it). In this section, the 4-bit quantized BN, called the quantized batch normalization (QBN), is proposed to significantly compress the computation. The quantized computation in QBN can be represented by

![image](images/ch07_eqn6.gif)

where ![image](images/ch07_si47.gif)and ![image](images/ch07_si48.gif)are the expectation and variance over the batch, while ![image](images/ch07_si49.gif)and ![image](images/ch07_si50.gif)are learnable parameters that scale the normalized value \[190\], and ![image](images/ch07_si51.gif)are quantized items which shift the normalized value. In the inference stage, ![image](images/ch07_si52.gif), ![image](images/ch07_si53.gif), ![image](images/ch07_si54.gif)and ![image](images/ch07_si55.gif)are fixed to normalize the convolution output.

#### 7.2.4 Quantized activation function and pooling

The activation function produces a nonlinear decision boundary via nonlinear combinations of the outputs of BN. In the deep ResNet, the ReLU is commonly used which is defined as ![image](images/ch07_si56.gif)\[267\]. And the quantized ReLU layers, called the QReLUs, can be optimized as

![image](images/ch07_eqn7.gif)

where ![image](images/ch07_si57.gif)is the output of the QBN and ![image](images/ch07_si58.gif)is the quantized activation generated in the ![image](images/ch07_si59.gif)th layer.

We can take the QReLUs function for all real-number matrixes using the following example for a ![image](images/ch07_si60.gif)region:

![image](images/ch07_eqn8.gif)

where the ![image](images/ch07_si61.gif)real-value matrix denotes the output of QBN. The QReLUs filter out all the negative values to make the calculation more efficient and more feasible for hardware implementation.

Moreover, the pooling operation is optionally applied to select the most significant information from the features, which performs a downsampling across an ![image](images/ch07_si62.gif)contiguous region on the feature. There are two kinds of pooling schemes commonly used in CNN-based network: max-pooling and average-pooling. The max-pooling takes the maximum value of the pooling region while the average-pooling takes the mean value of the pooling region. The deep ResNet begins with a max pooling and ends with a global average pooling layer and a ![image](images/ch07_si63.gif)\-way fully connected (FC) layer with a softmax layer. To save runtime memory and storage usage in inference, we can do the fusion as ![image](images/ch07_si64.gif)function commutes with the max-pooling function:

![image](images/ch07_eqn9.gif)

and the quantized max-pooling, called the QPooling, is applied with the following equation:

![image](images/ch07_eqn10.gif)

where ![image](images/ch07_si65.gif)and ![image](images/ch07_si66.gif)are the features before and after pooling, respectively.

#### 7.2.5 Quantized deep neural network overview

The overall working flow of the deep ResNet model with quantization and parallelization is presented in [Figure 7.3](#Chapter7.html#c07_fig3). After the first layer, the QPooling will primarily work and feed the downsampled features into 4-bit QConv. Then each 4-bit QConv layer conducts a quantized convolution between 4-bit quantized features and weights. Then the feature output of QConv will be further processed by the QBN and QReLUs function. After every three convolution layers, the add-residual operation will be performed with 4-bit quantized parameters at the end of residual block.

As all the major parameters and expensive computation are performed with 4-bit quantization, the proposed 4-bit ResNet will get much less storage cost, faster speed as well as higher energy efficiency.

**Algorithm 7.1:** Training quantized ResNet with 4-bit weights, features. ![image](images/ch07_si67.gif)is the number of layers and ![image](images/ch07_si68.gif)is the parameter gradient.

**Require**: previous inputs ak−1 and previous weights wk

**Ensure**: updated weights w∗ k .

1 Computing the forward flow:

1: **for** k = 1 : L **do**

2: wq k ← quantize(wk )

3: a q k−1 ← quantize(ak−1)

4: s q k ← compute(wb k , a q k−1)

5: a qbn k ← compute(s q k ,μ, σ2, γ , β)

6: **if** max-pooling layer **then**

7: a qp k ← compute(a qbn k )

8: a qrelu k ← compute(a qp k )

**9: else**

10: a qrelu k ← compute(a qbn k )

11: **end if**

12: a q k ← a qrelu k

13: **end for**

2\. Computing the backward gradients:

14: f**or** k = L : 1 **do**

15: ga q k−1 ← backward(ga q k ,wq k )

16: gwq k ← backward(ga q k , a q k−1)

17: **end for**

3\. Accumulating the parameters gradients:

18: **for** k = 1 : L **do**

19: w∗ k ← update(wq k , gwq k )

20: **end for**

#### 7.2.6 Training strategy

The detailed training strategy is presented in Algorithm 2.5. The network is assumed to have a feedforward linear topology, and the computation is performed with 4-bit quantization with high parallelism and efficiency. Note that the ![image](images/ch07_si86.gif)and ![image](images/ch07_si87.gif)functions represent the corresponding quantization and computation methods mentioned above, the ![image](images/ch07_si88.gif)function specifies how to calculate parameter gradients in the backward propagation \[254\], and the ![image](images/ch07_si89.gif)function presents how to update the parameters when their gradients are known \[269\].

After training, the proposed 4-bit ResNet model can be obtained, which is highly compressed through quantization. Compared to the original ResNet, the quantized ResNet benefits a lot from the large compression and high parallelization. It will reduce the complexity and enlarge the throughput of networks with low-bitwidth parameters, so that the implementation on the in-memory device also becomes more realizable.

### 7.3 Device for in-memory computing

In this section, the ReRAM-crossbar device will be presented which can be used for both storage and computation. And it will be employed to support a CMOS-ReRAM in-memory computing accelerator. The large-scale deep ResNet with quantization which has been discussed in Section 7.2 will be mapped.

#### 7.3.1 ReRAM crossbar

ReRAM \[62\] is an in-memory computing device facing the future. The different resistance states of ReRAM can represent different parameters while computing. Besides working as storage memory, a ReRAM crossbar can be applied to perform logic operations \[263\], especially the dot-product-based convolutions.

Previous works in \[258, 259\] usually choose the two-terminal ReRAM device which only has two nonvolatile states: high-resistance state (HRS) and low-resistance state (LRS) to build an in-memory architecture, as shown in [Figure 7.4](#Chapter7.html#c07_fig4)(a). However, when the applied network becomes deeper and more complex, the two-terminal computing results in limitation on the performance of ReRAM crossbar while sacrifices the accuracy of network. For the implementation of proposed 4-bit ResNet-50, we apply the ReRAM model in \[270\], which has multibit resistance states. The states of proposed ReRAM device are determined by the distribution of set voltage ![image](images/ch07_si90.gif).

![image](images/PBPC0390-07-f04.jpg)

Figure 7.4 (a) Traditional two-terminal ReRAM crossbar; (b) 4-bit ReRAM crossbar with 4-bit DAC/ADC circuits

In one ReRAM crossbar, given the input probing voltage ![image](images/ch07_si91.gif)on each writeline (WL), the current ![image](images/ch07_si92.gif)on each bitline (BL) becomes the natural multiplication–accumulation of current through each ReRAM device. Therefore, the ReRAM-crossbar array can intrinsically perform the matrix–vector multiplication. Given an input voltage vector ![image](images/ch07_si93.gif), the output vector ![image](images/ch07_si94.gif)can be expressed as

![image](images/ch07_eqn11.gif)

where ![image](images/ch07_si95.gif)is configurable conductance of the ReRAM resistance ![image](images/ch07_si96.gif), which can represent real value of weights. Compared to the traditional CMOS implementation, the ReRAM device can achieve a higher level of parallelism and consumes less power including standby power.

Different from the traditional non-quantized two-terminal ReRAM crossbar, the proposed 4-bit quantized ReRAM crossbar is shown in [Figure 7.4](#Chapter7.html#c07_fig4)(b), and the 4-bit resistance is configured for each ReRAM device. Moreover, the novel designed 4-bit DACs are applied on WL to transfer the digital input, and the 4-bit ADCs are applied on BL to identify the analog output. Therefore, the sensed analog output can be encoded in quantized digital signal to produce the multiplied result \[237\].

Compared to the two-terminal ReRAM crossbar, the 4-bit ReRAM crossbar has a better robustness on the IR-drop in the large-size implementation, so that the wire resistance affects little on IR-drop. In addition, since only 4-bit inputs are configured in quantized ReRAM crossbar, it has a better programming accuracy and can provide a better strategy for mapping deeper and large-scale networks.

#### 7.3.2 Customized DAC and ADC circuits

To accommodate the multibit network on the ReRAM crossbar, we customize the designs of the 4-bit DAC and ADC, respectively, as shown in [Figure 7.5](#Chapter7.html#c07_fig5)(a) and (b). To save area, the DAC is implemented with the resistance to resistance (R2R) structure with a compact Opamp buffer. Compared with the traditional resistor ladder, the R2R uses uniform resistor values that favor better matching. The Opamp buffer uses feedforward structure to minimize current consumption and achieves fast settling. Biased by a ![image](images/ch07_si97.gif)around ![image](images/ch07_si98.gif), the current consumption of the whole Opamp is less than ![image](images/ch07_si99.gif)and achieves a ![image](images/ch07_si100.gif)MHz unity gain bandwidth. Meanwhile, an ADC scheme similar to that in \[271\] is employed to reduce the switching power, which uses asynchronous SAR to minimize the area and energy.

![image](images/PBPC0390-07-f05.jpg)

Figure 7.5 Simplified 4-bit (a) DAC and (b) ADC circuits

#### 7.3.3 In-memory computing architecture

Based on the developed 4-bit ReRAM-crossbar device and novel DAC/ADC circuits, we present the CMOS-ReRAM in-memory computing accelerator with both memory storage and computation implemented as shown in [Figure 7.6](#Chapter7.html#c07_fig6).

![image](images/PBPC0390-07-f06.jpg)

Figure 7.6 In-memory accelerator architecture based on 4-bit ReRAM crossbar for 4-bit quantized ResNet-50

In this architecture, data–logic pairs are located in a distributed fashion, where data transmission among data block, logic block and external scheduler are maintained by a control bus. Therefore, logic block can read data locally and write back to the same data block after the logic computation is done \[237\]. As a result, the huge communication load between memory and general processor can be relieved because most of the data transmission is done inside data–logic pairs. Based on this in-memory computing architecture using the 4-bit CMOS-ReRAM accelerator, we will further introduce the strategy to map the proposed 4-bit quantized ResNet-50.

### 7.4 Quantized ResNet on ReRAM crossbar

In this section, we present the detailed strategy to map the proposed large-scale ResNet with 4-bit quantization on the 4-bit CMOS-ReRAM, including quantized convolution and add-residual operations.

#### 7.4.1 Mapping strategy

In order to avoid mapping negative weights on ReRAM-crossbar device, the 4-bit weights shown in [Figure 7.2](#Chapter7.html#c07_fig2)(a) are departed into positive weights ![image](images/ch07_si101.gif)and negative weights ![image](images/ch07_si102.gif). Therefore, the quantized convolution can be presented by two separated multiplication operations, which are shown as

![image](images/ch07_eqn12.gif)

to get the expected calculation result (keep weights positive), and the values of ![image](images/ch07_si103.gif)and ![image](images/ch07_si104.gif)will satisfy the following conditions:

![image](images/ch07_eqn13.gif)

![image](images/ch07_eqn14.gif)

Such all-positive trick makes it more feasible to implement a large-scale network on ReRAM crossbar. Specifically, the architecture of quantized ResNet-50 is shown in [Table 7.1](#Chapter7.html#c07_tbl1), which will be further mapped on the previously discussed 4-bit ReRAM crossbar.

Table 7.1 Network model of quantized ResNet-50

| Layer/residual block || Output size || Parameters (kernels, channels) |
| --- | --- | --- |
| CONV1 || ![image](images/ch07_si105.gif) || ![image](images/ch07_si106.gif) |
| --- | --- | --- |
|  ||  || ![image](images/ch07_si107.gif)max pool |
| CONV2 || ![image](images/ch07_si108.gif) || ![image](images/ch07_si109.gif) |
| CONV3 || ![image](images/ch07_si110.gif) || ![image](images/ch07_si111.gif) |
| CONV4 || ![image](images/ch07_si112.gif) || ![image](images/ch07_si113.gif) |
| CONV5 || ![image](images/ch07_si114.gif) || ![image](images/ch07_si115.gif) |
|  ||  || ![image](images/ch07_si116.gif)average pool |
| FC || ![image](images/ch07_si117.gif) || softmax output |

#### 7.4.2 Overall architecture

The whole mapping of residual block of proposed 4-bit ResNet-50 is shown in [Figure 7.7](#Chapter7.html#c07_fig7). Since there are positive and negative lines for WL, the 4-bit ResNet-50 requires a ![image](images/ch07_si118.gif)ReRAM crossbar, where ![image](images/ch07_si119.gif)is the number of elements in the feature matrices. The 4-bit DAC and the 4-bit ADC are applied to take input and output features. All columns are configured with the same elements that correspond to the quantized weight columns ![image](images/ch07_si120.gif)of the neural network, and the WL voltages are determined by the analog input ![image](images/ch07_si121.gif)transferred by the 4-bit DAC. Meanwhile, the output from every BL will be transferred to the digital signal by a 4-bit ADC. The ![image](images/ch07_si122.gif)represents the convolution result, which can be seen in (7.5).

![image](images/PBPC0390-07-f07.jpg)

Figure 7.7 Mapping strategy for a 4-bit quantized ResNet-50 block on 4-bit ReRAM crossbar

As described in (3.5), each quantized weight vector ![image](images/ch07_si123.gif)performs quantized convolution with several input features. As a result, each logic block in [Figure 7.6](#Chapter7.html#c07_fig6) stores a quantized vector ![image](images/ch07_si124.gif), while the control bus transmits the input feature sequentially. In this case, quantized convolution can be performed in parallel in separated logic blocks.

Although these operations are implemented on different ReRAM-crossbar arrays, the input/output formats of them are compatible so that one can directly connect them as shown in the logic block in [Figure 7.6](#Chapter7.html#c07_fig6). As discussed in the in-memory computing architecture, one ResNet-50 residual block contains three convolution layers, and the add-residual operation is applied at the end of residual block to straightforwardly add the input of Layer 1 and the output of Layer 3.

As a summary, the 4-bit quantized convolution, BN, ReLUs and add-residual operations in [Figure 7.1](#Chapter7.html#c07_fig1) can be mapped onto the proposed 4-bit CMOS-ReRAM accelerator and the max-pooling operations are performed in the additional processor. The pipeline design is based on [Table 7.1](#Chapter7.html#c07_tbl1). We observe that CONV2, CONV3, CONV4 and CONV5 are the stages which require the most ReRAM cells and computation time. As a result, more logic blocks are assigned to these steps to relieve the critical path. Since the output features from [Figure 7.7](#Chapter7.html#c07_fig7) are 4-bit quantized, the area overhead and energy consumption of the data storage can be significantly reduced. In addition, as the layers in [Table 7.1](#Chapter7.html#c07_tbl1) are implemented with different data–logic pairs, the volume of data transmitted is also decreased.

### 7.5 Experiment result

#### 7.5.1 Experiment settings

In the experiment, we have implemented different baselines for accuracy and performance comparison. Detailed setting of each baseline is listed as follows:

1.  Proposed 4-bit CMOS-ReRAM: We use the ReRAM model of \[272\] with uniformly separated resistance values in \[1 k![image](images/ch07_si125.gif), 5 k![image](images/ch07_si126.gif)\] and a working frequency of ![image](images/ch07_si127.gif)MHz.
2.  CPU: The general processor implementation is using Matconvnet \[227\] on a computer server with ![image](images/ch07_si128.gif)cores of ![image](images/ch07_si129.gif)GHz and ![image](images/ch07_si130.gif)GB RAM.
3.  GPU: The general-purpose GPU implementation is based on a CUDA-enabled video card \[188\] with ![image](images/ch07_si131.gif)GHz.
4.  State-of-the-art ReRAM-based architectures: Two existing ReRAM-based architectures \[146, 222\].
5.  Others: The field programmable gate array (FPGA) \[273\], CMOS-ASIC \[230\] and micron automata processor \[274\] implementations of the conventional CNN networks.

To present the power of proposed architecture, we apply the large-scale ImageNet \[265\] data set to analyze the accuracy and performance of proposed 4-bit hardware accelerator. First, the model takes a ![image](images/ch07_si132.gif)RGB image as the input of the first convolution layer with ![image](images/ch07_si133.gif)sets of quantized filters. After that, QPooling is applied to prepare data for the following layers. Next, the QConv layer of the first residual block performs the quantized convolution between input features and weights followed by the QPooling. Then the QBN is employed after the QConv to accelerate the training. Meanwhile, we adopt the QReLUs to each QConv layer to stabilize the process. For every layer stack, three cascaded convolution layers make up a residual block with an add-residual operation. In the end, the output of the last FC layer is fed into a softmax layer to generate a probabilistic distribution of ![image](images/ch07_si134.gif)classes.

#### 7.5.2 Device simulations

According to the sizes of feature matrix in ResNet-50, we employ a ![image](images/ch07_si135.gif)ReRAM crossbar where the number of input features is set as ![image](images/ch07_si136.gif)and the number of output channels is ![image](images/ch07_si137.gif). We adopted the read/write latency and read/write energy from \[275\] as ![image](images/ch07_si138.gif)ns/![image](images/ch07_si139.gif)ns per spike, ![image](images/ch07_si140.gif)pJ/![image](images/ch07_si141.gif)nJ per spike. The final layouts of the proposed 4-bit DAC and ADC circuits are shown in [Figure 7.7](#Chapter7.html#c07_fig7). We further report simulation results of the proposed CMOS-ReRAM accelerator. In [Figure 7.8](#Chapter7.html#c07_fig8)(a), 4-bit digital waveforms are converted into analog signals by the 4-bit DAC. Then in [Figure 7.8](#Chapter7.html#c07_fig8)(b), output waveforms are obtained by the 4-bit ADC for various ReRAM resistive states representing all possible ![image](images/ch07_si142.gif). A high accuracy can be observed in the DAC/ADC circuits, and the whole CMOS-ReRAM accelerator permits a high performance and efficiency, as shown in [Table 7.4](#Chapter7.html#c07_tbl4).

![image](images/PBPC0390-07-f08.jpg)

Figure 7.8 Layouts of the proposed 4-bit (a) DAC and (b) ADC

#### 7.5.3 Accuracy analysis

First, we report both the top-1 and top-5 accuracy comparison between the proposed 4-bit ResNet-50 and the full-precision ResNet-50 on ImageNet. It should be noted that in case of top-1 rate, we check if the top class having the highest probability is the same as the target label, and in case of top-5 rate, we check if the target label is one of the top five predictions with the highest probabilities. And then, the accuracy comparison under device variation is presented. At last, we report the accuracy comparison between the proposed quantized ResNet-50 and the direct-truncated ResNet-50 under bitwidth approximation.

##### 7.5.3.1 Peak accuracy comparison

[Figure 7.9](#Chapter7.html#c07_fig9) shows the evolution of top-1 and top-5 accuracy vs. epoch curves of the 4-bit ResNet-50 compared with the full-precision ResNet-50. It can be seen that quantizing the ResNet-50 to be 4-bit does not cause the training curve to be significantly different from the full-precision one. Only 3.3% prediction accuracy decreases for top-1 while only 2.5% accuracy losses for top-5 compared with the full-precision ResNet-50. Moreover, we report the top-5 accuracy comparison among different state-of-the-art quantization approaches in [Table 7.2](#Chapter7.html#c07_tbl2). It is observed that the proposed 4-bit trained quantization outperforms other realizations, which is 3.5% higher than the 4-bit fine-grained quantization \[276\] and 1.5% higher than the 5-bit incremental network quantization \[277\]. Therefore, we can conclude that the ResNet-50 with the proposed 4-bit trained quantization obtains a remarkable balance between large compression and high accuracy.

![image](images/PBPC0390-07-f09.jpg)

Figure 7.9 (a) Waveforms of the 4-bit DAC inputs; (b) 4-bit ADC outputs with different ReRAM resistances

Table 7.2 The top-5 accuracy comparison between the proposed network and state-of-the-art approaches on the ImageNet data set

| Original ResNet-50 (32-bit) \[246\] || 90.6% |
| --- | --- |
| Truncation-based quantization (4-bit) \[252\] || 12.3% |
| Binary weight quantization (1-bit) \[254\] || 78.7% |
| Ternary weight quantization (2-bit) \[278\] || 81.2% |
| Fine-grained quantization (4-bit) \[276\] || 84.6% |
| Incremental quantization (5-bit) \[277\] || 86.8% |
| Discussed trained quantization (4-bit) || 88.1% |

##### 7.5.3.2 Accuracy under device variation

In the previous discussion, the 4-bit ReRAM crossbar has better programming accuracy than the traditional ReRAM crossbar so that it achieves a better uniformity. For further evaluation, we build a device variation model by using the Monte-Carlo simulation technique under different writing voltages ![image](images/ch07_si143.gif)where the voltage amplitude meets the Gaussian distribution (σ=1% ![image](images/ch07_si145.gif)). Based on the variation model, we systematically set the parameter variation during the network training and can achieve better accuracy under device variation. The accuracy comparison against device variation on ReRAM is shown in [Figure 7.10](#Chapter7.html#c07_fig10). It can be observed that when the device variation of ReRAM increases, there are output current errors. For example, when the device variation reaches 29%, the 4-bit ReRAM crossbar has an accuracy of 86.5% with only 1.6% decreases compared with GPUs, better than the non-quantized one with an accuracy of 84.7% with 5.9% decreased. The proposed CMOS-ReRAM delivers higher robustness when the device variation is larger than 20%.

![image](images/PBPC0390-07-f10.jpg)

Figure 7.10 (a) Top-1 validation accuracy curves of quantized ResNet-50. (b) Top-5 validation accuracy curves of quantized ResNet-50

##### 7.5.3.3 Accuracy under approximation

To evaluate the accuracy under bitwidth approximation, we choose the precision-bit direct-truncated method for comparison. For the proposed trained quantized ResNet-50 and direct-truncated ResNet-50, we first train the full-precision (32-bit) network, and then decrease the precision of all the weights and features in the network. The numerical results with different bitwidths are shown in [Figure 7.11](#Chapter7.html#c07_fig11). In our model, the weights and features in the quantized ResNet-50 are 4-bit, whose accuracy has no significant loss compared with the full-precision ResNet-50. Although the accuracy of the 32-bit model reaches 90.6% in the direct-truncated ResNet-50, the bitwidth influences the accuracy a lot especially when the bitwidth is smaller than 10. For example, when the precision decreases to 6-bit, the accuracy drops down to only about 11.3%. The results show that the proposed quantized ResNet-50 can perform much better than the direct-truncated one.

![image](images/PBPC0390-07-f11.jpg)

Figure 7.11 Accuracy validation of quantized ResNet-50 under ReRAM-crossbar device variation

Moreover, we further report the evaluation on accuracy and storage compression among different bitwidths. As shown in [Table 7.3](#Chapter7.html#c07_tbl3), the 4-bit ResNet-50 causes only ![image](images/ch07_si152.gif)decrease on accuracy with ![image](images/ch07_si153.gif)storage compression. It can be seen that accuracy decreases a lot when the bitwidth is smaller than ![image](images/ch07_si154.gif), but not much improvement when bitwidth is larger than ![image](images/ch07_si155.gif). There are some recent works to perform quantization on 8-bit and binary quantization \[188\]. However, 8-bit quantization results in higher accuracy still have significant hardware cost, while binary quantization cannot achieve a reasonable accuracy on a large-scale neural network. Therefore, we conclude that the 4-bit quantization can have good balance between accuracy and storage compression on the large-scale ResNet-50 network. It is the reason why 4-bit is determined to be the best quantization bitwidth for the large-scale ReRAM implementation.

Table 7.3 Accuracy validation of quantized ResNet-50 under bitwidth approximation

| Bitwidth || Accuracy || Storage compression |
| --- | --- | --- |
| 2-bit || 32.9% || ![image](images/ch07_si146.gif) |
| --- | --- | --- |
| 3-bit || 71.5% || ![image](images/ch07_si147.gif) |
| 4-bit || 88.1% || 8.02 |
| 6-bit || 88.7% || ![image](images/ch07_si148.gif) |
| 8-bit || 89.8% || ![image](images/ch07_si149.gif) |
| 16-bit || 90.5% || ![image](images/ch07_si150.gif) |
| Full precision || 90.6% || N/A |

#### 7.5.4 Performance analysis

In the experiments, parameters with quantization have been configured by the training process, meanwhile every batch of inputs and results are calculated in parallel. In [Table 7.4](#Chapter7.html#c07_tbl4), performance comparison among CPU, GPU and other baselines is presented, which is evaluated on ![image](images/ch07_si156.gif)testing images with ![image](images/ch07_si157.gif)resolution.

##### 7.5.4.1 Energy and area

Using the ReRAM model in \[270\], the current consumption of each ReRAM cell is less than ![image](images/ch07_si158.gif), where the voltage is set to be ![image](images/ch07_si159.gif)mV and the area consumption of each ReRAM cell is less than ![image](images/ch07_si160.gif). Moreover, the current consumption of the proposed novel DAC/ADC is less than ![image](images/ch07_si161.gif)and the total area of DAC/ADC is less than ![image](images/ch07_si162.gif). Having both settings of ReRAM and DAC/ADC models, the numerical results of energy consumption can be simulated as follows: ![image](images/ch07_si163.gif). It should be noted that we load power on a single BL for each convolution operation, the value ![image](images/ch07_si164.gif)denotes the amount of ReRAM cells and ![image](images/ch07_si165.gif)denotes the number of DACs/ADCs in one BL. The energy distribution is shown in [Figure 7.12](#Chapter7.html#c07_fig12)(a) and the convolution is the major operation that dominates 87.4% of the total energy. Also, we calculate the area consumption by ![image](images/ch07_si166.gif). Based on the area model in \[279\], we present the area overhead of the proposed CMOS-ReRAM architecture in [Figure 7.12](#Chapter7.html#c07_fig12)(b). The area overhead of DAC/ADC is the largest part which occupies 32%, and the total area consumption is simulated as ![image](images/ch07_si167.gif). The energy and area consumption comparison among all the implementations are shown in [Table 7.4](#Chapter7.html#c07_tbl4). It can be seen that the implementation on the proposed 4-bit CMOS-ReRAM accelerator can achieve at least four-magnitude smaller energy consumption compared to GPU and CPU.

Table 7.4 Performance comparison under different hardware implementations

![image](images/tab7.4.jpg)

![image](images/PBPC0390-07-f12.jpg)

Figure 7.12 Accuracy comparison with direct truncation-based quantization based on ResNet-50

##### 7.5.4.2 Throughput and efficiency

For the throughput performance, we use GOPS (giga operations per second) to evaluate all the implementations as shown in Tables [7.4](#Chapter7.html#c07_tbl4) and [7.5](#Chapter7.html#c07_tbl5). In the throughput comparison, the proposed 4-bit ReRAM crossbar is ![image](images/ch07_si168.gif)faster than CPU-based implementation, ![image](images/ch07_si169.gif)faster than FPGA-based implementation and ![image](images/ch07_si170.gif)faster than CMOS-ASIC-based implementation. As for energy efficiency, it can be four-magnitude better than GPU-based implementation and ![image](images/ch07_si171.gif)better than CMOS-ASIC-based implementation. And in area-efficiency comparison, it is ![image](images/ch07_si172.gif)better than the CMOS-ASIC-based implementation. As a conclusion, the proposed 4-bit ReRAM crossbar outperforms all the implementations on throughput, energy efficiency and area efficiency. There are still some challenges in accommodating the multibit network on the real-fabricated ReRAM such as the circuit designs of the DACs/ADCs and the robustness of the large-scale ReRAM crossbar. Nonetheless, since the proposed CMOS-ReRAM has provided an efficient and robust architecture with real circuit designs and simulations, it is more feasible to implement a large-scale neural network (e.g., VGG-16, SSD-50 and ResNet-101) on the real-fabricated ReRAM-based accelerator.

![image](images/PBPC0390-07-f13.jpg)

Figure 7.13 (a) Divided energy profile and (b) divided area profile when implementing 4-bit ResNet-50 on 4-bit ReRAM crossbar

Table 7.5 Efficiency comparison among three ReRAM-based implementations

![image](images/tab7.5.jpg)

## *Chapter 8*  
**Large-scale case study: accelerator for compressive sensing**

### 8.1 Introduction

Biomedical wireless circuits for applications such as health telemonitoring \[280, 281\] and implantable biosensors \[282, 283\] are energy sensitive. To prolong the lifetime of their services, it is essential to perform the dimension reduction while acquiring original data. The compressive sensing \[284\] is a signal processing technique that exploits signal sparsity so that signal can be reconstructed under lower sampling rate than that of Nyquist sampling theorem. The existing works that apply compressive sensing technique on biomedical hardware focus on the efficient signal reconstruction by either dictionary learning \[283, 285\] or more efficient algorithms of finding the sparsest coefficients \[280, 281, 286\]. However, these works, by improving the reconstruction on mobile/server nodes instead of data acquisition on sensor nodes, can only indirectly reduce the number of samples for wireless transmission with lower energy. In this work, we aim to achieve both high-performance signal acquisition and low sampling hardware cost at sensor nodes directly.

In compressive sensing, the sampling is performed by multiplying the original signal vector with a linear embedding matrix, which projects the high-dimensional data vector into a low-dimensional subspace with preserved intrinsic information. The concise representation is called a low-dimensional embedding. The sampling matrix can be either random, generally optimized or optimized towards specific data set. The random sampling matrices, Bernoulli or Gaussian, though easier to construct, have two major limitations. First, its guarantee on recoverability is only probabilistic and therefore large recovery error may be incurred. Second, its construction is independent on the data under investigation, and therefore the geometric information of data set cannot be exploited. The generally optimized sampling matrices, such as Reed--Muller code \[287, 288\] or Puffer transformation \[283\], have deterministic recoverability by constructing matrices with minimized mutual coherence. However, they are still independent on data type of interest so that the performance cannot be maximized. The data-driven optimized embedding, on the other hand, can leverage geometric structure of data set in particular application with additional learning phase, which is especially beneficial for biomedical sampling hardware where target data type is predetermined. Signal acquisition by a data-driven optimized sampling matrix can preserve more intrinsic information of original signal, and therefore ensure more accurate signal reconstruction and/or higher compression ratio.

Most existing data-driven optimization methods only produce real-valued embedding matrices \[289\]. However, the hardware mapping of real-valued sampling matrix is much more power consuming than that of Boolean matrix. The reason is that for real-valued embedding operation, the required hardware resources, primarily full adders, are quadratically depending on the precision required, while only linearly for Boolean embedding mapping. Therefore, a Boolean sampling matrix is preferred as the significantly reduced hardware resources can contribute to higher energy efficiency and area efficiency. In fact, the random Bernoulli matrix is the most widely used sampling matrix in existing CMOS-based implementations for low power consumption \[283, 286, 290\]. In addition, the recent emerging resistive random-access memory (ReRAM) \[62, 291\] in crossbar (or cross-point) structure \[62\] can provide intrinsic fabric for matrix--vector multiplication, which potentially enables both energy- and area-efficient hardware implementation of linear embedding. However, the limited ReRAM programming resolution also favors only Boolean embedding matrices to be mapped to ReRAM crossbar structure.

Therefore, the hardware realization of sampling matrix faces a dilemma. On the one hand, if data-driven optimized real-valued embedding, such as NuMax \[289\], is mapped for better recovery quality, large power overhead will be expected. On the other hand, if non-data-driven random Boolean embedding or Boolean Reed--Muller \[287, 288\] embedding is mapped for better hardware energy efficiency, high signal recovery accuracy cannot be accomplished. Such trade-off is illustrated in [Figure 8.1](#Chapter8.html#c08_fig1). [Figure 8.1](#Chapter8.html#c08_fig1) also reveals that quantization of NuMax by straightforward truncation works only above precision of 16 bits, below which it will incur significant performance degradation. Therefore, without data-driven optimized Boolean embedding, the advantages of both sides cannot be achieved simultaneously. The challenge to perform data-driven Boolean embedding optimization is that, with large amount of data set involved in the sampling matrix optimization, only convex methods with real-valued optimized matrices are feasible.

![image](images/PBPC0390-08-f01.jpg)

Figure 8.1 The comparison of information loss of NuMax through truncation quantization vs. proposed quantization. This work achieves both high signal recovery performance as well as low sampling hardware cost by proposed quantization algorithm

In this chapter, towards high-performance (data-driven) and low-power (Boolean) sampling, instead of optimizing Boolean embedding on original data set, we propose an optimizing algorithm that transforms a data-driven optimized real-valued sampling matrix to a Boolean sampling matrix. The proposed optimization flow is illustrated in [Figure 8.2](#Chapter8.html#c08_fig2). As the input optimized real-valued embedding matrix is optimized towards the specific data set, and the proposed algorithm seeks least intrinsic information loss, so the resulted Boolean embedding matrix is still optimized towards the same training data set. In addition, we have discussed the corresponding hardware implementations based on both CMOS technology and emerging nonvolatile ReRAM technology for obtained optimized Boolean embedding. Such capability was first exploited in our preliminary work \[249\]. The numerical experiments demonstrate that the proposed data-driven Boolean embedding can combine both high signal quality and also low sampling power. Specifically, it can improve image recovery quality (reconstructed signal-to-noise ratio (RSNR)) by 9 dB compared to the non-data-driven Bernoulli embedding, and improve energy efficiency by ![image](images/ch08_si1.gif)than that of data-driven real-valued sampling circuit.

![image](images/PBPC0390-08-f02.jpg)

Figure 8.2 The proposed flow for data-driven Boolean sampling matrix optimization

The contributions of this chapter are summarized as follows:

*   To our best knowledge, the data-driven optimized Boolean sampling matrix is constructed for the first time. Being Boolean and optimized towards data set, we achieve both the highest signal recovery quality and the best hardware energy efficiency among all existing schemes.
*   We formulate the problem of finding the best transformation that quantizes real-valued sampling matrix into Boolean matrix with minimal information loss.

The rest of this chapter is organized as follows. Section 8.2 introduces the background of compressive sensing and near-isometric embedding. Section 8.3 presents the sampling hardware for Boolean embedding with the corresponding optimization problem formulated. Sections 8.4 and 8.5 detail two Boolean embedding optimization algorithms. Numerical results are presented in Section 8.6.

### 8.2 Background

#### 8.2.1 Compressive sensing and isometric distortion

Recently, the emerging theory of compressive sensing has enabled the recovery of undersampled signal, if the signal is sparse or has sparse representation on certain basis, such as wavelet transformation and Fourier transformation. And the recovery can be achieved by solving

![image](images/ch08_si423.gif)

where ![image](images/ch08_si2.gif)is the sparse coefficients vector and ![image](images/ch08_si3.gif)is the basis on which the original signal is sparse; ![image](images/ch08_si4.gif)is the sensing matrix and ![image](images/ch08_si5.gif)(![image](images/ch08_si6.gif)) the undersampled data in low dimension. To ensure a successful recovery, the sensing matrix (![image](images/ch08_si7.gif)) must meet the restricted isometry property (RIP), which is defined as follows: if there exists a ![image](images/ch08_si8.gif)such that the following equation is valid for every vector ![image](images/ch08_si9.gif),

![image](images/ch08_si424.gif)

then ![image](images/ch08_si10.gif)has the RIP with isometric distortion constant ![image](images/ch08_si11.gif). The notations of all used symbols are summarized in [Table 8.1](#Chapter8.html#c08_tbl1).

Table 8.1 Notation table of used mathematical symbols

| Symbols || Descriptions |
| --- | --- |
| ![image](images/ch08_si17.gif) || The isometric distortion of the restricted isometry property |
| --- | --- |
| ![image](images/ch08_si18.gif) || Original high-dimensional signal to be sampled by compressive sensing |
| ![image](images/ch08_si19.gif) || Sampled low-dimensional signal by compressive sensing |
| ![image](images/ch08_si20.gif) || Sparse basis/dictionary |
| ![image](images/ch08_si21.gif) || Reconstructed/recovered original signal |
| ![image](images/ch08_si22.gif) || Sampling matrix |
| ![image](images/ch08_si23.gif) || Boolean sampling matrix losslessly quantized from real-valued ![image](images/ch08_si24.gif) |
| ![image](images/ch08_si25.gif) || Orthogonal RIP preserving transformation matrix for quantization |
| ![image](images/ch08_si26.gif) || ![image](images/ch08_si27.gif)row of T obtained during row-generation algorithm |
| ![image](images/ch08_si28.gif) || ![image](images/ch08_si29.gif)row of ![image](images/ch08_si30.gif)obtained during row-generation algorithm |
| ![image](images/ch08_si31.gif) || Training data set ![image](images/ch08_si32.gif)for sampling matrix optimization |
| ![image](images/ch08_si33.gif) || Set of all pairwise distances among every two ![image](images/ch08_si34.gif)in ![image](images/ch08_si35.gif)as input for NuMax |
| ![image](images/ch08_si36.gif) || Testing data set that has no overlap with training data set ![image](images/ch08_si37.gif) |
| ![image](images/ch08_si38.gif) || Standard deviation of ReRAM resistance in LRS |
| ![image](images/ch08_si39.gif) || Standard deviation of ReRAM resistance in HRS |

#### 8.2.2 Optimized near-isometric embedding

The easiest way to construct a matrix with RIP is to generate a random matrix. The work \[292\] proves that random matrix is of a very high possibility to satisfy RIP, yet not deterministic. Different from the random Bernoulli sampling matrix that the RIP is probabilistic, an data-driven sampling matrix can ensure the RIP of a finite given data points. One recent work in \[289\] proposed the **NuMax** framework to construct a near-isometric embedding matrix with deterministic RIP. Given a data set ![image](images/ch08_si12.gif), the NuMax produces an optimized continuous-valued embedding matrix ![image](images/ch08_si13.gif)so that every pairwise distance vector ![image](images/ch08_si14.gif)for ![image](images/ch08_si15.gif)can preserve its norm after embedding up to a given distortion tolerance ![image](images/ch08_si16.gif).

Once the optimized NuMax sampling matrix ![image](images/ch08_si40.gif)is obtained, the signal acquisition ![image](images/ch08_si41.gif)can be performed by multiplying the embedding matrix ![image](images/ch08_si42.gif)with signal vector ![image](images/ch08_si43.gif). The conventional CMOS circuit-based data acquisition front end that performs real-valued embedding is shown in [Figure 8.3](#Chapter8.html#c08_fig3). The sampling circuit has two major components, the static random access memory (SRAM) memory that stores the embedding matrix and the multiplier-accumulators (MACs) that perform multiplication and addition. For an embedding matrix ![image](images/ch08_si44.gif)(![image](images/ch08_si45.gif)), in each cycle, ![image](images/ch08_si46.gif)MACs multiply one element of input vector ![image](images/ch08_si47.gif)with one column of ![image](images/ch08_si48.gif), and then add with previously accumulated results. Therefore, it requires ![image](images/ch08_si49.gif)cycles to obtain the embedded signal ![image](images/ch08_si50.gif).

![image](images/PBPC0390-08-f03.jpg)

Figure 8.3 The embedding circuit by CMOS matrix--vector multiplier

As NuMax produces real-valued ![image](images/ch08_si51.gif), the precision of ![image](images/ch08_si52.gif)substantially determines the hardware complexity. For example, a multiplier in MAC with 4-bit resolution, shown in [Figure 8.4](#Chapter8.html#c08_fig4)(a), requires 16 full adders. In fact, the number of full adders required generally quadratically depends on the precision of both ![image](images/ch08_si53.gif)and ![image](images/ch08_si54.gif). For the typical precision of real-valued elements in sampling matrix, 16-bit ([Figure 8.1](#Chapter8.html#c08_fig1)) resolution may lead to as many as hundreds of full adders for each MAC, which makes the real-valued NuMax embedding less appealing for signal acquisition hardware mapping.

![image](images/PBPC0390-08-f04.jpg)

Figure 8.4 The implementation of (a) MAC with multiplier in 4-bit resolution for real-valued embedding matrix; (b) MAC for ![image](images/ch08_si55.gif)embedding matrix; (c) MAC for ![image](images/ch08_si56.gif)embedding matrix with power optimization

### 8.3 Boolean embedding for signal acquisition front end

#### 8.3.1 CMOS-based Boolean embedding circuit

The mapping of a Boolean embedding matrix can eliminate the usage of multipliers. For a ![image](images/ch08_si57.gif)Boolean embedding matrix, the MAC only accumulates signal data when Boolean multiplicand is ![image](images/ch08_si58.gif). For a more general ![image](images/ch08_si59.gif)Boolean matrix, the Boolean multiplicand indicates addition or subtraction for the signal data. That is to say, the required resources of full adders are only linearly depending on the precision of signal ![image](images/ch08_si60.gif). As such, the hardware resource can be significantly reduced.

Specifically for the ![image](images/ch08_si61.gif)embedding matrix mapping, the multiplication by ![image](images/ch08_si62.gif)requires the calculation of 2's complement. The intuitive approach is illustrated in [Figure 8.4](#Chapter8.html#c08_fig4)(b). The ![image](images/ch08_si63.gif)signal is ![image](images/ch08_si64.gif)for multiplying ![image](images/ch08_si65.gif)and ![image](images/ch08_si66.gif)for multiplying ![image](images/ch08_si67.gif). To obtain the 2's complement, the XOR logic is used to get the complement of each bit and the ![image](images/ch08_si68.gif)(carry 0) is applied as well. However, the 2's complement calculation close to input will incur substantial dynamic power for the combinational logic. Instead, the circuit diagram in [Figure 8.4](#Chapter8.html#c08_fig4)(c) first accumulates all data to be multiplied by ![image](images/ch08_si69.gif)and ![image](images/ch08_si70.gif)separately, and the subtraction is performed at the very last cycle. Therefore, the 2's complement circuit is only active every ![image](images/ch08_si71.gif)cycles, which can greatly improve the power efficiency.

To be compatible with optimized sampling matrices such as Reed--Muller code \[287, 288\] and NuMax \[289\], SRAM block is required to store the matrix and provide reconfigurability. For non-optimized sampling matrices such as random Gaussian and Bernoulli, apart from storing the matrix in SRAM, the matrix can also be generated at runtime, which can improve hardware efficiency. In practice, the pseudo-random number generator (PRNG) is used \[286, 290\], which avoids the power-consuming SRAM arrays. As PRNG produces 0/1 sequences with a predetermined pattern, one of the issues for PRNG is the self-coherence. For example, an 8-bit per cycle PRNG has a period of 256 ![image](images/ch08_si72.gif), and when filling a ![image](images/ch08_si73.gif)sampling matrix by rows with such 0/1 sequences, all rows of the matrix will be identical. This can be overcome by increasing the number of bits the PRNG produces per cycle at a cost of higher hardware complexity. With limited hardware resources, the pseudo-random numbers generated by PRNG usually lead to performance degradation of signal acquisition compared to stored random sampling matrix.

#### 8.3.2 ReRAM crossbar-based Boolean embedding circuit

The emerging ReRAM crossbar \[62, 191\] provides an intrinsic in-memory fabric of matrix--vector multiplication, which is proposed in [Figure 8.5](#Chapter8.html#c08_fig5). Compared to CMOS embedding circuit, ReRAM crossbar-based approach can provide three major advantages: (1) embed sensing matrix in-memory without the need of loading ![image](images/ch08_si74.gif)externally each cycle, (2) perform the matrix--vector multiplication in single cycle and (3) minimize the leakage power due to its nonvolatility.

![image](images/PBPC0390-08-f05.jpg)

Figure 8.5 The embedding circuit by emerging nonvolatile ReRAM crossbar

A ReRAM crossbar structure is composed of three layers: horizontal wires at top layer, vertical wires at bottom layer and ReRAM devices in the middle layer at each cross point. For an ![image](images/ch08_si75.gif)ReRAM crossbar, assume the input signal of ![image](images/ch08_si76.gif)row is ![image](images/ch08_si77.gif)and the conductance of ReRAM device on ![image](images/ch08_si78.gif)row ![image](images/ch08_si79.gif)column is ![image](images/ch08_si80.gif), then the output current flowing down ![image](images/ch08_si81.gif)column ![image](images/ch08_si82.gif). In other words, crossbar structure intrinsically supports in-memory embedding operation

![image](images/ch08_si425.gif)

where ![image](images/ch08_si83.gif)is the transimpedance of the transimpedance amplifier (TIA). It must be ensured that input ![image](images/ch08_si84.gif)to avoid accidental value changes of ![image](images/ch08_si85.gif), in which the ![image](images/ch08_si86.gif)is the device programming threshold voltage.

The mapping of embedding matrix is accomplished by the resistance programming of ReRAM crossbar corresponding to ![image](images/ch08_si87.gif). Intended for memory usage, ReRAM devices are commonly bistable with on-resistance and off-resistance ratio as high as ![image](images/ch08_si88.gif)\[291, 293\]. Resistance programming with higher resolution has been demonstrated in 4 or 5 levels at most \[293, 294\]. Therefore, resistance programming in continuous (or close-continuous) value resolution is practically challenging due to large process variation under current manufacture technology. In other words, the real-valued sampling matrix does not comply with ReRAM crossbar and Boolean sampling matrix is preferred.

As the ReRAM crossbar is essentially ![image](images/ch08_si89.gif)binary in terms of conductance, the mapping of ![image](images/ch08_si90.gif)Boolean matrix is as follows: ![image](images/ch08_si91.gif)corresponds to high-resistance state (HRS) and ![image](images/ch08_si92.gif)maps to low-resistance state (LRS). To map ![image](images/ch08_si93.gif), simple linear transformation needs to be considered: ![image](images/ch08_si94.gif), where ![image](images/ch08_si95.gif), ![image](images/ch08_si96.gif)all-ones matrix and ![image](images/ch08_si97.gif)input vector. The ![image](images/ch08_si98.gif)is implemented by an additional all-LRS column that generates ![image](images/ch08_si99.gif)as current offset for other columns, as shown in [Figure 8.5](#Chapter8.html#c08_fig5). The sampling matrices that each type of hardware supports are illustrated in [Table 8.2](#Chapter8.html#c08_tbl2).

Table 8.2 Compatibility of different sampling matrices on various hardware platforms

![image](images/tab8.2.jpg)

#### 8.3.3 Problem formulation

For an sampling matrix ![image](images/ch08_si115.gif)that satisfies RIP with distortion of ![image](images/ch08_si116.gif), the following equation will also hold true:

![image](images/ch08_si426.gif)

if ![image](images/ch08_si117.gif)is an orthonormal rotation matrix. In other words, if we can find an orthonormal rotation matrix that transforms real-valued NuMax embedding matrix ![image](images/ch08_si118.gif)into a matrix that is close enough to a Boolean matrix ![image](images/ch08_si119.gif), then the Boolean embedding of ![image](images/ch08_si120.gif)can preserve original distortion ![image](images/ch08_si121.gif). In other words, the resulted ![image](images/ch08_si122.gif)is still optimized towards the same training data set as NuMax embedding ![image](images/ch08_si123.gif), and meanwhile, it can be efficiently mapped to circuits in [Figures 8.4](#Chapter8.html#c08_fig4)(c) and 8.5 with greatly reduced power consumption.

The Boolean sampling matrix optimization can be then formulated as the following optimization problem:

![image](images/ch08_si427.gif)

where ![image](images/ch08_si124.gif)![image](images/ch08_si125.gif)is the optimized real-valued sampling matrix learned from data set that projects data from high ![image](images/ch08_si126.gif)\-dimension to low ![image](images/ch08_si127.gif)\-dimension; ![image](images/ch08_si128.gif)is an orthonormal rotation matrix that attempts to transform ![image](images/ch08_si129.gif)to a Boolean matrix. ![image](images/ch08_si130.gif)is the closest Boolean matrix solution where closeness is defined by the Frobenius norm.

Ideally, if an orthonormal transformation matrix ![image](images/ch08_si131.gif)can rotate ![image](images/ch08_si132.gif)to an exact Boolean matrix, i.e., the optimal value of (8.5) is zero, then the distortion ![image](images/ch08_si133.gif)of optimized Boolean embedding will be exactly the same as the NuMax real-valued embedding. In practice, with a nonzero optimal value, the closeness of ![image](images/ch08_si134.gif)to ![image](images/ch08_si135.gif)indicates information loss degree from ![image](images/ch08_si136.gif)to ![image](images/ch08_si137.gif). On the other hand, it can be interpreted as an equivalent near-orthogonal rotation ![image](images/ch08_si138.gif)transforms real-valued ![image](images/ch08_si139.gif)to an exact Boolean ![image](images/ch08_si140.gif). The degree of orthogonality implies the information loss of ![image](images/ch08_si141.gif).

### 8.4 IH algorithm

It is intractable to solve the problem formulated in (8.5) considering the orthogonal constraint ![image](images/ch08_si142.gif)and the integer constraint ![image](images/ch08_si143.gif)simultaneously, as both constraints are nonconvex. When one constraint is considered at one time, (8.5) can be split into two manageable problems: if the orthogonal constraint is considered for ![image](images/ch08_si144.gif), and ![image](images/ch08_si145.gif)a given Boolean matrix, the problem becomes the search of an *orthogonal rotation* matrix for maximal matrix agreement; if the integer constraint is considered for ![image](images/ch08_si146.gif)and ![image](images/ch08_si147.gif)a given orthogonal matrix, the problem turns to *Boolean quantization* for maximal matrix agreement. In this section, a heuristic approach is proposed that iteratively solves *orthogonal rotation* problem and *Boolean quantization* problem, and gradually approximates the optimal solution of ![image](images/ch08_si148.gif)in each round.

#### 8.4.1 Orthogonal rotation

The problem of finding an orthogonal transformation matrix ![image](images/ch08_si149.gif)that can rotate a given real-valued projection matrix ![image](images/ch08_si150.gif)to another given Boolean matrix ![image](images/ch08_si151.gif)can be formulated as

![image](images/ch08_si428.gif)

The cost function can be represented by trace function as

![image](images/ch08_si429.gif)

As ![image](images/ch08_si152.gif)and ![image](images/ch08_si153.gif)are given matrices, ![image](images/ch08_si154.gif)and ![image](images/ch08_si155.gif)are therefore two constants. Consider ![image](images/ch08_si156.gif)as constant first, the formulated optimization problem in (8.6) can be rewritten as

![image](images/ch08_si430.gif)

and with the singular value decomposition ![image](images/ch08_si157.gif), where ![image](images/ch08_si158.gif)![image](images/ch08_si159.gif), the cost function of (8.8) can be rewritten as

![image](images/ch08_si431.gif)

The inequality holds as ![image](images/ch08_si160.gif), ![image](images/ch08_si161.gif)and ![image](images/ch08_si162.gif)are all orthonormal matrices. As such, the trace is maximized when ![image](images/ch08_si163.gif), which leads to

![image](images/ch08_si432.gif)

To optimize ![image](images/ch08_si164.gif), let ![image](images/ch08_si165.gif)in which ![image](images/ch08_si166.gif)is the cost function of (8.7), and the best scaling factor can be obtained by

![image](images/ch08_si433.gif)

#### 8.4.2 Quantization

![image](images/ch08_si167.gif)is a known orthogonal transformation matrix, and ![image](images/ch08_si168.gif)is a given real-valued optimized projection matrix, the problem to find its closest Boolean matrix can be formulated as

![image](images/ch08_si434.gif)

It is obvious that the solution for (8.12) is

![image](images/ch08_si435.gif)

This can be seen as Boolean quantization. The quantization error can be defined as

![image](images/ch08_si436.gif)

In ideal case, the error would be zero, which means an orthogonal transformation ![image](images/ch08_si169.gif)on optimized real-valued projection matrix ![image](images/ch08_si170.gif)finds an exact Boolean matrix ![image](images/ch08_si171.gif). Therefore, the distortion ![image](images/ch08_si172.gif)caused by ![image](images/ch08_si173.gif)will be the same as ![image](images/ch08_si174.gif). With ![image](images/ch08_si175.gif), it can be inferred that ![image](images/ch08_si176.gif). To reduce the quantization error, it is an intrinsic idea to increase the level of quantization. Consider a modified problem formulation

![image](images/ch08_si437.gif)

with each element of the matrix ![image](images/ch08_si177.gif)normalized within the interval of ![image](images/ch08_si178.gif). It is important to keep matrix Boolean so that it can be mapped to ReRAM crossbar structure efficiently; thus, it requires the matrix ![image](images/ch08_si179.gif)can be split into two Boolean matrices ![image](images/ch08_si180.gif), where ![image](images/ch08_si181.gif)and ![image](images/ch08_si182.gif). With Boolean quantization, only one projection ReRAM crossbar is needed. Two ReRAM crossbars are needed for the three-level quantization case, as a result of trade-off between error and hardware complexity.

#### 8.4.3 Overall optimization algorithm

The heuristic optimization process is summarized in Algorithm 8.1. Given some initial guess of ![image](images/ch08_si183.gif), the inner loop of Algorithm 8.1 tries to find the local close-optimal solution by improving ![image](images/ch08_si184.gif)through iterations. Within each iteration, (8.6) and (8.12) are solved by singular vector decomposition and quantization as concluded in (8.10) and (8.15), respectively. The iterations terminate when the ![image](images/ch08_si185.gif)stops improving and converges.

**Algorithm 8.1:** IH Boolean sampling matrix optimization algorithm

**Input**: Real-valued embedding matrix ![image](images/ch08_si186.gif), search width and quantization level

**Output**: Optimized Boolean embedding matrix ![image](images/ch08_si187.gif)initialize ![image](images/ch08_si188.gif)![image](images/ch08_si189.gif)random ![image](images/ch08_si190.gif)Bernoulli matrix

1: **while** not reach search width limit **do**

2: seed ← random m × m matrix

3: U, S, V ← SVD of seed

4: T ← U

5: **while** not converged **do**

6: ![image](images/ch08_si195.gif)← quantization of ![image](images/ch08_si197.gif)

7: U, S, V ← SVD of ![image](images/ch08_si198.gif)![image](images/ch08_si199.gif)

8: T ← UV

9: ![image](images/ch08_si201.gif)

10: **if** ![image](images/ch08_si202.gif)**then**

11: ![image](images/ch08_si203.gif)![image](images/ch08_si204.gif)![image](images/ch08_si205.gif)

12: **end if**

13: **end while**

14: **end while**

As both integer constraint and orthogonal constraint are nonconvex, the local optimum in most cases is not optimal globally. In other words, the solution strongly depends on the initial guess that leads to the local close optimum. Therefore, the outer loop of Algorithm 8.1 increases the search width by generating numerous initial guesses that scatter within orthogonal matrices space. For each initial guess, it will gradually converge to a local optimum; thus, the increase in search width will compare numerous local optimal solutions and approximate the global optimum.

### 8.5 Row generation algorithm

The formulated problem in (8.5) is a mixed-integer nonlinear programming (MINLP) problem, as it has both nonlinear orthogonal constraint ![image](images/ch08_si206.gif)and the integer constraint ![image](images/ch08_si207.gif). Although such MINLP problem can be solved by existing algorithms such as genetic algorithm \[295\], it lacks efficiency and only problem in small size can be managed. For the embedding matrix in compressive sensing, the transformation matrix ![image](images/ch08_si208.gif)could have dozens of rows while matrix ![image](images/ch08_si209.gif)may have thousands of Boolean variables, so current solvers may fail in such scale. In this section, we proposed a row generation algorithm that also can efficiently tackle the problem.

#### 8.5.1 Elimination of norm equality constraint

The orthonormality of ![image](images/ch08_si210.gif)in (8.5) implies two specific constraints, the orthogonality of rows of ![image](images/ch08_si211.gif)that

![image](images/ch08_si438.gif)

and the norm equality that

![image](images/ch08_si439.gif)

where ![image](images/ch08_si212.gif)is the ![image](images/ch08_si213.gif)row of ![image](images/ch08_si214.gif). Both imply numerous quadratic equality constraints (nonconvex) and therefore it is hard to manage simultaneously. The nonconvex quadratic norm equality constraint of rows of ![image](images/ch08_si215.gif)indicates the normalization of rows after orthogonality is satisfied. In the following, we show how the norm equality constraint can be eliminated without affecting the solution accuracy of problem in (8.5).

Assume we only impose orthogonal constraint on ![image](images/ch08_si216.gif)rather than more strict orthonormal constraint, the original problem can be then relaxed to

![image](images/ch08_si440.gif)

where ![image](images/ch08_si217.gif)is a diagonal matrix, and ![image](images/ch08_si218.gif)is the norm of ![image](images/ch08_si219.gif)row of ![image](images/ch08_si220.gif). That is to say, an additional row scaling operation is introduced during the sensing stage

![image](images/ch08_si441.gif)

where ![image](images/ch08_si221.gif)is the optimized Boolean embedding matrix that can be efficiently realized in hardware, ![image](images/ch08_si222.gif)is the orthonormal sparse basis of original signal and ![image](images/ch08_si223.gif)is the sparse coefficient.

In fact, the row scaling operation during signal acquisition is unnecessary and can be transferred to recovery stage if an implicit sensing is performed,

![image](images/ch08_si442.gif)

with corresponding signal reconstruction by

![image](images/ch08_si443.gif)

where ![image](images/ch08_si224.gif)is the tolerance for noise on sampled signal data ![image](images/ch08_si225.gif). As such, the norm equality constraint is eliminated while the compressive sensing signal acquisition front-end hardware complexity stays the same and recovery quality is not affected.

#### 8.5.2 Convex relaxation of orthogonal constraint

To construct a transformation matrix ![image](images/ch08_si226.gif)with orthogonal rows and minimize the cost function at the same time is challenging, in the following, we propose a convex row generation algorithm that seeks local optimal solution. The idea is to construct each row of ![image](images/ch08_si227.gif)at one time while minimizing the cost function. Assume ![image](images/ch08_si228.gif)are first ![image](images/ch08_si229.gif)rows that are already built with orthogonality, to construct the ![image](images/ch08_si230.gif)row ![image](images/ch08_si231.gif),

![image](images/ch08_si444.gif)

In other words, each time to construct a new row ![image](images/ch08_si232.gif), it has to be orthogonal with previously built ![image](images/ch08_si233.gif). The iterative row generation algorithm is shown in Algorithm 8.2. From the geometric perspective, Algorithm 8.2 seeks to find an orthogonal basis in the ![image](images/ch08_si234.gif)\-dimensional space iteratively. Initially ![image](images/ch08_si235.gif)is empty so the first direction vector has the greatest freedom to minimize the cost function. After the first basis vector is chosen, the algorithm finds the best basis vector in the left ![image](images/ch08_si236.gif)\-dimensional subspace that best minimizes the target function. This is iteratively performed until the last direction is selected in only one-dimensional subspace with freedom for length only.

As ![image](images/ch08_si237.gif)is a square matrix, there always exists a solution for Algorithm 8.2. The MINLP problem with ![image](images/ch08_si238.gif)integer variables in (8.18) is therefore relaxed to ![image](images/ch08_si239.gif)MINLP subproblems integer programming problems each with only ![image](images/ch08_si240.gif)integer variables.

**Algorithm 8.2:** Iterative row generation algorithm

**Input**: real-valued embedding matrix ![image](images/ch08_si241.gif)

**Output**: orthogonal transformation matrix ![image](images/ch08_si242.gif), optimized Boolean embedding matrix ![image](images/ch08_si243.gif)

1.Initialize ![image](images/ch08_si244.gif)\= ![image](images/ch08_si245.gif), ![image](images/ch08_si246.gif)\= ![image](images/ch08_si247.gif)

2.**for** ![image](images/ch08_si248.gif)to ![image](images/ch08_si249.gif)**do**

3.get ![image](images/ch08_si250.gif)by solving problem in (8.22)

4.update ![image](images/ch08_si251.gif), ![image](images/ch08_si252.gif)

5: **end for**

#### 8.5.3 Overall optimization algorithm

The overall algorithm to solve (8.18) is illustrated in Algorithm 8.2. The 0-1 programming problem (8.22) within the loop can be readily solved by branch-and-cut method, under the condition that the number of Boolean variable is kept small. The brand-and-cut method is widely implemented in solvers such as MOSEK \[296\] and BARON \[297\].

Without the linearization by row generation, the branch-and-cut method cannot be applied as the orthogonal constraint is strongly nonlinear and thus the evaluation of lower and upper bounds for each subproblem will be extremely complicated. In addition, the linearization by row generation significantly reduces the number of Boolean variables and thus reduces the worst-case complexity from ![image](images/ch08_si253.gif)to ![image](images/ch08_si254.gif). As such, the row generation together with widely available integer programming solvers can find solution for problem formulated in (8.18).

### 8.6 Numerical results

#### 8.6.1 Experiment setup

In this part, we evaluate different compressive sensing sampling matrices from both software and hardware perspectives. The numerical experiments are performed within MATLAB on a desktop with 3.6 GHz Intel i7 processor and 16 GB memory. The software performance of sampling matrices is mainly characterized by the signal recovery quality of sampling matrices. For this purpose, both labeled faces in the wild (LFW) image data \[298\] and biomedical electrocardiogram (ECG) data \[299\] are used. For both types of data, the NuMax \[289\] optimization is first applied with varied training parameter ![image](images/ch08_si255.gif)values ![image](images/ch08_si256.gif), NuMax produces optimized real-valued sampling matrices with different ranks. As depicted in the flowchart in [Figure 8.2](#Chapter8.html#c08_fig2), the proposed algorithms are then applied to Booleanize NuMax sampling matrices. Apart from the above data-driven sampling matrices, random Gaussian, Bernoulli and Reed--Muller \[287, 288\] (non-data-driven optimization) sampling are also compared. The RSNR is used as signal recovery quality metric, which is defined as

![image](images/ch08_si445.gif)

where ![image](images/ch08_si257.gif)is the original signal and ![image](images/ch08_si258.gif)is the reconstructed signal.

With respect to hardware cost consideration, above all sampling matrices can be mapped to three different sampling hardware configurations. Specifically, the MAC/SRAM, MAC/PRNG and ReRAM crossbar configurations with their variations are evaluated to examine the hardware friendliness of all the sampling schemes. For real-valued MAC, 16-bit resolution is used as we find that resolution higher than 16-bit will not improve accuracy, as shown in [Figure 8.1](#Chapter8.html#c08_fig1). For ReRAM crossbar, the resistance of 1K![image](images/ch08_si259.gif)and 1M![image](images/ch08_si260.gif)are used for ReRAM on-state resistance and off-state resistance according to \[293\]. The area of the ReRAM crossbar is evaluated by multiplying the cell area (4![image](images/ch08_si261.gif)) with sampling matrix size plus one additional column to calculate current offset as discussed in Section 3.2. Dynamic power of the ReRAM crossbar is evaluated statistically under 1,000 random input patterns following an uniform distribution with voltage ranging from ![image](images/ch08_si262.gif)to ![image](images/ch08_si263.gif)V (![image](images/ch08_si264.gif)V and ![image](images/ch08_si265.gif)V \[293\]) and the duration of operation is ![image](images/ch08_si266.gif)ns \[293\]. Both the real-valued and Boolean digital CMOS matrix multiplier designs are implemented in Verilog and synthesized with GlobalFoundries 65-nm low-power process design kit (PDK). A PRNG design \[286\] is also implemented and synthesized. The SRAM that stores the sampling matrix is evaluated by CACTI \[300\] memory modeling tool with 65-nm low standby power process opted.

[Table 8.3](#Chapter8.html#c08_tbl3) shows all valid combinations of sampling matrix and hardware configuration that will be compared in the section. Among all the combinations, we will show in this section that our proposed sampling matrix can achieve both the best signal recovery quality and hardware efficiency.

Table 8.3 Summary of the embedding methods to be compared

![image](images/tab8.3.jpg)

#### 8.6.2 IH algorithm on high-D ECG signals

For training stage (NuMax), 1,000 ECG periods in dimension of 256 are randomly picked from database \[299\] as the data set ![image](images/ch08_si282.gif), which leads to around 1 million of pairwise distance vectors in set ![image](images/ch08_si283.gif). For testing phase, another 1,000 ECG periods are selected as data set ![image](images/ch08_si284.gif), which have no overlap with learning data set ![image](images/ch08_si285.gif). The ECG signal reconstruction is performed on unseen data set ![image](images/ch08_si286.gif)by solving (8.1) with Battle--Lemarie wavelet bases used.

##### 8.6.2.1 Algorithm convergence and effectiveness

The efficiency of Algorithm 8.1 can be examined from two aspects, finding both local and global optima. The efficiency of finding local optimum is assessed by convergence rate. The local search terminates when the approximation error ![image](images/ch08_si287.gif)stops improving.

Given specific RIP upper bounds, NuMax \[289\] provides ![image](images/ch08_si288.gif)with different ranks. With RIP constraint of 0.1, the NuMax produces a ![image](images/ch08_si289.gif)sampling matrix. Algorithm 8.1 is applied to ![image](images/ch08_si290.gif)with total 10,000 repeated local search and the convergence is illustrated in [Figure 8.6](#Chapter8.html#c08_fig6)(a). It can be observed that the relative error reduces dramatically within the first few iterations. The zoomed subfigure shows that local search on average converges within 50 iterations, where convergence is defined as less than 1e-6 error reduction in two consecutive iterations. Generally, the local optimum can be considered found in less than 100 iterations.

![image](images/PBPC0390-08-f06.jpg)

Figure 8.6 The algorithm efficiency for (a) local search convergence and (b) global search convergence

The global search is achieved by scattering many initial guesses in the orthogonal matrices space for ![image](images/ch08_si291.gif), and comparing the corresponding local optima. The errors under varying number of initial guesses are shown in [Figure 8.6](#Chapter8.html#c08_fig6)(b). Considering the Boolean constraint and the orthogonal constraint, the problem formulated in (8.5) is generally NP-hard. Therefore, the relative error can be improved by scattering exponentially more initial guesses, yet no convergence is observed. Hence, an efficient search policy should be designed in a way scattering as many initial points as possible and limiting the local search for each initial guess within 100 iterations.

##### 8.6.2.2 ECG recovery quality comparison

The ECG signal recovery examples under ![image](images/ch08_si293.gif)are shown in [Figure 8.7](#Chapter8.html#c08_fig7). For non-data-driven sampling matrices, both the random Bernoulli and Gaussian show similar reconstruction quality. In other words, the increase of bits in random numbers will not improve recovery quality. This is because, the increase of bits of random number will not gain any additional information.

![image](images/PBPC0390-08-f07.jpg)

Figure 8.7 The recovery quality comparison among different sampling matrices: (a) examples of recovered ECG signals at ![image](images/ch08_si292.gif)and (b) RSNR for 1,000 ECG periods

The PRNG-based Bernoulli exhibits the lowest reconstructed signal quality. This is because, as PRNG produces 0/1 sequences with a predetermined pattern, it has self-coherence issue. For example, an 8-bit per cycle PRNG has a period of 256 ![image](images/ch08_si294.gif), and when filling a sampling matrix by rows with such 0/1 sequences, all rows of the matrix will be identical.

The Reed--Muller code optimizes the sampling matrix by minimizing the correlations among different rows/columns, which helps to improve sampling performance. Being a generic sampling matrix that works with all data types, it cannot exploit the isometric property of ECG signal, which limits its performance in particular applications. Specifically, it only shows 1 dB improvement compared to random Bernoulli sampling.

The data-driven NuMax real-valued sampling exhibits the best recovery quality (highest RSNR) as shown in [Figure 8.7](#Chapter8.html#c08_fig7)(b). The proposed iterative heuristic (IH) algorithm quantizes the real-valued NuMax sampling with slight quality loss. Specifically, at the undersampling ratio ![image](images/ch08_si295.gif), the IH (lv2) exhibits 8, 9 and 10 dB higher RSNR than that of Reed--Muller, Bernoulli and pseudo-Bernoulli samplings, respectively. Also, Level 3 quantization through (8.15) can preserve more information than Level 2 quantization through (8.13). The RSNR of IH (lv3) shows marginal 0.48 dB higher RSNR than IH (lv2). The IH (lv3) sampling matrix ![image](images/ch08_si296.gif)will incur additional hardware overhead compared to IH (lv2) ![image](images/ch08_si297.gif).

[Figure 8.7](#Chapter8.html#c08_fig7)(a) gives a visual effect of quality of recovered ECG signal segments with different sampling matrices. The data-driven sampling matrices, i.e., NuMax, IH (lv2) and IH (lv3), can recover signals that tightly coincide with original signals.

#### 8.6.3 Row generation algorithm on low-D image patches

For training stage (NuMax), 6,000 patches with size of ![image](images/ch08_si298.gif)are randomly picked throughout all images as the data set ![image](images/ch08_si299.gif), which leads to around 18 million of pairwise distance vectors in set ![image](images/ch08_si300.gif). For testing phase, another 6,000 patches with size of ![image](images/ch08_si301.gif)are selected as data set ![image](images/ch08_si302.gif)with no overlap with learning data set ![image](images/ch08_si303.gif). The image reconstruction is performed on unseen data set ![image](images/ch08_si304.gif)by solving (8.1) with 2D discrete cosine transform (DCT) bases.

The genetic algorithm \[295\] is adopted as the baseline solver for the MINLP in (8.5), which is compared with the proposed algorithm in Algorithm 8.3. Both algorithms are run given same amount of time, i.e., ![image](images/ch08_si305.gif)s where ![image](images/ch08_si306.gif)is the rank of ![image](images/ch08_si307.gif)that indicates the size of the problem.

##### 8.6.3.1 Algorithm effectiveness

The idea behind the proposed real-valued matrix Booleanization is to preserve the RIP of NuMax sampling matrix, which differs from the truncation-based quantization. The information loss during the quantization is directly related to the RIP preservation. The algorithm effectiveness in this part will be examined by the isometric distortion ![image](images/ch08_si308.gif), defined in (8.2).

**Algorithm 8.3:** Iterative row generation algorithm

**Input**: real-valued embedding matrix ![image](images/ch08_si310.gif)

**Output**: orthogonal transformation matrix ![image](images/ch08_si311.gif), optimized Boolean embedding matrix ![image](images/ch08_si312.gif)

1: initialize ![image](images/ch08_si313.gif)\= ![image](images/ch08_si314.gif), ![image](images/ch08_si315.gif)\= ![image](images/ch08_si316.gif)

2: **for** ![image](images/ch08_si317.gif)to ![image](images/ch08_si318.gif)do

3: **while** ![image](images/ch08_si319.gif)**do**

4: **for all** branch with feasible set ![image](images/ch08_si320.gif)**do**

5: partition the feasible set ![image](images/ch08_si321.gif)into ![image](images/ch08_si322.gif)and ![image](images/ch08_si323.gif)

6: evaluate ![image](images/ch08_si324.gif), ![image](images/ch08_si325.gif)

7: update lower bound ![image](images/ch08_si326.gif)

8: evaluate ![image](images/ch08_si327.gif), ![image](images/ch08_si328.gif)

9: update upper bound ![image](images/ch08_si329.gif)

10: **if**![image](images/ch08_si330.gif)**then**

11: cut branch ![image](images/ch08_si331.gif)or ![image](images/ch08_si332.gif)

12: **end if**

13: **end for**

14: **end while**

15: update ![image](images/ch08_si333.gif), ![image](images/ch08_si334.gif)

16: **end for**

The distortions of all embeddings are tested on unseen data set ![image](images/ch08_si335.gif)(see [Figure 8.8](#Chapter8.html#c08_fig8)). The isometric distortions of both random embeddings are almost invariant. Being optimized on image data set ![image](images/ch08_si336.gif), both the NuMax and proposed (quantized NuMax) are significantly better than random embeddings. With focus on the Boolean sampling matrices that are hardware friendly, the isometric distortion of optimized Boolean embedding is ![image](images/ch08_si337.gif)better than random Boolean embedding on average.

![image](images/PBPC0390-08-f08.jpg)

Figure 8.8 The isometric distortion on the unseen data set ![image](images/ch08_si309.gif)for different embeddings

Due to the near-orthogonal rotation, the optimized Boolean embedding experiences some penalty on isometric distortion ![image](images/ch08_si338.gif)compared to NuMax approach. For genetic algorithm, as it experiences higher distortion than that of the proposed algorithm, it can be inferred that Algorithm 8.3 can find a more precise solution. In addition, it can be observed that the genetic algorithm fails when undersampling ratio ![image](images/ch08_si339.gif)increases, and this is because the proposed row generation-based algorithm requires linearly more time when the number of row ![image](images/ch08_si340.gif)increases, while the genetic algorithm needs exponentially more time. Moreover, the solution provided by genetic algorithm is stochastic, which has no guarantee on its effectiveness while the proposed algorithm is deterministic.

##### 8.6.3.2 Image recovery quality comparison

The recovery examples under ![image](images/ch08_si343.gif)are shown in [Figure 8.10](#Chapter8.html#c08_fig10)(a). The reconstructed images in blue box correspond to Boolean embeddings that have low-power hardware implementations, and images in red box are from optimization-based approaches which show lower recovery errors. The genetic algorithm is also optimization based, but the effectiveness is inconsiderable. Therefore, only the proposed can achieve both low power and high recovery performance. The numerical image reconstruction quality is shown in [Figure 8.10](#Chapter8.html#c08_fig10)(b). The two random embeddings show similar reconstruction RSNR, which is averagely 8.3 dB lower than that of the proposed optimized Boolean sampling matrix. The RSNR of optimized Boolean embedding is close to that of NuMax embedding, which is 2.5 dB lower as a result of information loss by near-orthogonal rotation.

![image](images/PBPC0390-08-f09.jpg)

Figure 8.9 The recovery quality comparison among different embedding matrices: (a) examples of recovered images under ![image](images/ch08_si341.gif)and (b) RSNR on 6,000 ![image](images/ch08_si342.gif)image patches

![image](images/PBPC0390-08-f10.jpg)

Figure 8.10 The sensitivity of recovery quality of (a) image signal and (b) ECG signal on the resistance standard deviation ![image](images/ch08_si346.gif)of ReRAM for both LRS and HRS following log-normal distribution

On the other hand, the genetic algorithm shows no obvious effectiveness of improving recovery quality even though it optimizes a Boolean embedding matrix. The main reason is that during the conversion of ![image](images/ch08_si344.gif)to ![image](images/ch08_si345.gif)too much information loss leads ![image](images/ch08_si346.gif)to be close to a random Boolean matrix. In other words, the genetic algorithm is ineffective to solve the problem in (8.5). In addition, the stochastic nature of genetic algorithm makes it necessary to perform the algorithm considerably many times. The proposed algorithm, on the contrary, guarantees to produce a Boolean matrix with high performance with single execution.

#### 8.6.4 Hardware performance evaluation

In this part, the hardware performance benefits of Boolean embedding will be investigated in detail. The evaluation only focuses on the embedding hardware as indicated by red dash-lined boxes in Figures [8.3](#Chapter8.html#c08_fig3) and [8.5](#Chapter8.html#c08_fig5).

##### 8.6.4.1 Hardware comparison

The matrix--vector multiplier is composed of multiple MACs in parallel. To multiply the signal vector with a 19![image](images/ch08_si347.gif)256 sampling matrix, 19 MACs are needed and each MAC requires 256 cycles to perform the inner-product with each cycle (1![image](images/ch08_si348.gif)). To store the NuMax real-valued sampling matrix, 16kB SRAM with 64-bit I/O bus-width is used.

The proposed Boolean optimization quantizes NuMax sampling matrix into a ![image](images/ch08_si349.gif)Boolean matrix. The size of SRAM to store sampling matrix is therefore reduced from 16kB to 1kB. Compared to a Bernoulli ![image](images/ch08_si350.gif)matrix, a ![image](images/ch08_si351.gif)multiplication requires calculations of 2's complement of input signal vector, which incurs additional hardware cost for MACs. To minimize the overhead of 2's complement, the MAC design in [Figure 4](#Chapter8.html#c08_fig4)(c) is used, which calculates 2's complement only once every 256 cycles.

ReRAM crossbar supports both ![image](images/ch08_si352.gif)and ![image](images/ch08_si353.gif)Boolean matrices. As the sampling matrix is embedded into the ReRAM crossbar which also performs the matrix multiplication, no separate memory is required.

The performance of four hardware schemes that support different types of sampling matrices is compared in [Table 8.4](#Chapter8.html#c08_tbl4). Compared to the NuMax real-valued embedding on 16-bit MAC and 16 kB SRAM hardware, the proposed quantized ![image](images/ch08_si354.gif)/1 Boolean embedding on 1-bit MAC and 1 kB SRAM consumes ![image](images/ch08_si355.gif)less operation energy per embedding, ![image](images/ch08_si356.gif)smaller leakage power and ![image](images/ch08_si357.gif)smaller area. This is because, as mentioned in Section 8.3, the real-valued multiplier generally requires quadratically increasing number of full adders when resolution increases, while Boolean multiplier only needs linearly more full adders.

Table 8.4 Hardware performance comparison among different sampling matrices (19![image](images/ch08_si361.gif)256) on varied hardware configurations

![image](images/tab8.4.jpg)

When the proposed quantized ![image](images/ch08_si358.gif)/1 Boolean embedding is performed on ReRAM crossbar, it further improves the hardware performance significantly. Specifically, for the operation energy per embedding, the ReRAM crossbar-based embedding outperforms the CMOS circuit-based real-valued embedding by ![image](images/ch08_si359.gif). The area of the ReRAM crossbar-based embedding is nearly ![image](images/ch08_si360.gif)better than that of CMOS circuit-based real-valued embedding. In addition, the ReRAM crossbar will not experience the leakage power which is at the scale of hundreds of microwatts for the CMOS circuit-based approach. For the operation speed, the ReRAM crossbar embedding executes in single cycle while the CMOS circuit requires 256 cycles due to the reuse of hardware. The overall performance for different sampling matrices on varied hardware platforms is summarized in [Table 8.5](#Chapter8.html#c08_tbl5).

Table 8.5 Comparison of all valid sampling matrices and hardware combinations

![image](images/tab8.5.jpg)

##### 8.6.4.2 Impact of ReRAM variation

One nonnegligible issue of mapping Boolean embedding matrix to ReRAM crossbar is the ReRAM HRS and LRS variations. With high resistance variation, the embedding matrix will deviate from expected values to be represented by ReRAM resistance, and hence the recovery quality may degrade. The sensitivity study of recovery quality on the resistance variations of ReRAM is shown in Figure 11. The resistance of ReRAM is assumed to follow log-normal distribution with the mean to be ![image](images/ch08_si368.gif)and ![image](images/ch08_si369.gif), and standard deviation ![image](images/ch08_si370.gif)and ![image](images/ch08_si371.gif)for LRS and HRS cells, respectively.

With varied ![image](images/ch08_si372.gif)and ![image](images/ch08_si373.gif), it can be observed from [Figure 8.10](#Chapter8.html#c08_fig10) that the performance degradation is more susceptible to resistance variation of LRS, while less sensitive on variation of HRS. In practice, the HRS variation ![image](images/ch08_si374.gif)is approximately ![image](images/ch08_si375.gif)\[301\], and LRS variation ![image](images/ch08_si376.gif)roughly ![image](images/ch08_si377.gif)\[301\]. The real-world ![image](images/ch08_si378.gif)is annotated in [Figure 8.10](#Chapter8.html#c08_fig10) and it can be concluded that the proposed Boolean embedding on ReRAM crossbar is robust against ReRAM device variations when on/off ratio is high (![image](images/ch08_si422.gif)). To further suppress the performance degradation, material engineering \[302\] and verification programming method \[301\] can help achieve higher LRS uniformity.

## *Chapter 9*  
**Conclusions: wrap-up, open questions and challenges**

### 9.1 Conclusion

To conclude, this book has shown a thorough study on resistive random-access memory (ReRAM)-based nonvolatile in-memory architecture towards machine learning applications from circuit level, to architecture level, and all the way to system level.

For the circuit level, on the one hand, we use non-volatile memory (NVM)-SPICE to simulate matrix–vector multiplication acceleration by binary ReRAM crossbar. By programming all the elements of a matrix into ReRAM resistance in the crossbar array, we can use crossbar wordline voltages to represent another matrix, and the multiplication result can be denoted by the merging current on bitlines. In this mapping scheme, both ReRAM resistance and crossbar I/O are in binary format so that the computation accuracy can be guaranteed. Simulation results show that the proposed architecture has shown ![image](images/ch09_si1.gif)faster speed,![image](images/ch09_si2.gif)better energy efficiency and ![image](images/ch09_si3.gif)smaller area when compared to the same design by complimentary metal oxide semiconductor (CMOS)-based application specific integrated circuit (ASIC). On the other hand, we use a Verilog-A model to build an ReRAM-based voltage-controlled oscillator circuit in Cadence. In a coupled network by ReRAM-based oscillator, the simulation results can be fitted as L2-norm calculation. Compared to traditional CMOS-based oscillator circuit, it has a much simpler structure with smaller area and better energy efficiency.

For the architecture level, we have developed a distributed in-memory architecture (XIMA) and three-dimensional (3D) CMOS-ReRAM architecture. For XIMA, we use both ReRAM crossbar for data storage and computing engine. We use a data block and logic block to form a data–logic pair, and all the pairs are located distributively. As a result, the communication bandwidth can be significantly improved because the computing engine only accesses the data from pairs. To achieve the in-memory computing, we design a control bus in each data–logic pair for communication among processor, data and logic block. In addition, communication protocol between processor and control bus is redefined for the in-memory computing implementation. For 3D CMOS-ReRAM architecture, we developed two schemes: single-layer and multilayer. The single-layer architecture uses ReRAM via connecting the top-layer wordlines and bottom-layer bitlines. All the other CMOS logics are implemented in the bottom layer as well. The multilayer architecture uses through silicon via (TSV) connecting the first-layer ReRAM-based data buffer, the second-layer ReRAM-based logic computing and the third-layer CMOS. Such a 3D architecture can significantly improve the throughput as well as the area efficiency for the hybrid ReRAM/CMOS computing system.

For the system level, for the XIMA, we have accelerated three machine learning algorithms. The learning and inference procedures of single-layer feedforward neural network (SLFN) have been optimized and partially mapped on the passive binary ReRAM crossbar. In addition, we mapped the binary convolutional neural network on both passive array and One Selector One ReRAM array with different mapping schemes. Moreover, L2-norm gradient-based learning and inference are also implemented on an ReRAM network with both crossbar and coupled oscillators. For 3D CMOS-ReRAM architecture, we also mapped the optimized SLFN algorithm. All the operations in learning and inference stages are implemented so that it can achieve the online learning. In addition, tensorized neural network is mapped on both single-layer and multilayer accelerators with different mapping scheme. For all the machine learning algorithms mapped on XIMA and 3D CMOS-ReRAM accelerator, we evaluate their performance in device, architecture and system levels. All the implementations show higher throughput, bandwidth and parallelism with better energy efficiency.

### 9.2 Future work

Based on the above works, there are a few potential future works to enhance this research.

The first potential work is to validate some designs discussed. In this work, we explore the binary ReRAM crossbar as well as oscillator network in device and circuit level by simulation. However, the ReRAM devices in the array are not fully uniform so that the mapping scheme may not be applied in a large crossbar array. In addition, sneak path and thermal effect in the ReRAM crossbar will also occur the inaccuracy during computing. As for the XIMA, this work only simulates a few groups of control bus design, but in the real implementation, there will be thousands of control bus blocks so it is also necessary to optimize all these designs.

The second potential work is to realize neuromorphic computing by the ReRAM network. This work only explores the artificial neural network implementations in the ReRAM-based architecture. All of these algorithms are originally designed for CMOS-based computing systems such as CPU, GPU, CMOS-ASIC and FPGA. The ReRAM-based architecture can perform analog-value computing operations, which is widely applied in neuromorphic applications. For example, it is easier to implement spike-timing-dependent plasticity-based synapse programming algorithm and also spiking neural networks on ReRAM compared to CMOS-ASIC or FPGA. It is possible to explore an ReRAM-based neuromorphic computing system with simpler structure and better scalability than the state-of-the-art works.

## **References**

\[1\] Cukier K. Data, data everywhere. The Economist. 2010 Feb.

\[2\] International Data Corporation. Digital Universe Study. Dell EMC. 2011.

\[3\] White T. O’Reilly Media Inc; 2012.

\[4\] Zaharia M, Chowdhury M, Franklin MJ, *et al*. Spark: Cluster computing with working sets. In: USENIX Conference on Hot Topics in Cloud Computing; 2010.

\[5\] Apache Flink. Apache Flink: Scalable batch and stream data processing. [http://flink.apache.org/](http://flink.apache.org/). Online.

\[6\] Carbone P, Fóra G, Ewen S, *et al*. Lightweight asynchronous snapshots for distributed dataflows. CoRR. 2015;abs/1506.08603.

\[7\] Saha B, Shah H, Seth S, *et al*. ApacheTez: A unifying framework for modeling and building data processing applications. In: ACM SIGMOD International Conference on Management of Data; 2015.

\[8\] Akidau T, Bradshaw R, Chambers C, *et al*. The Dataflow model: A practical approach to balancing correctness, latency, and cost in massive-scale, unbounded, out-of-order data processing. Proc VLDB Endow. 2015;8(12): 1792–1803.

\[9\] LeDell E. High performance machine learning in R with H2O. In: ISM HPC on R Workshop; 2015.

\[10\] Xing EP, Ho Q, Dai W, *et al*. Petuum: A new platform for distributed machine learning on big data. In: ACM SIGKDD International Conference on Knowledge Discovery and Data Mining; 2015.

\[11\] Bakshi K. Considerations for big data: Architecture and approach. In: IEEE Aerospace Conference; 2012.

\[12\] Chen Y, Alspaugh S and Katz R. Interactive analytical processing in big data systems: A cross-industry study of MapReduce workloads. Proc VLDB Endow. 2012;5(12):1802–1813.

\[13\] Lee KH, Lee YJ, Choi H, *et al*. Parallel data processing with MapReduce: A survey. SIGMOD Rec. 2012;40(4):11–20.

\[14\] Shvachko K, Kuang H, Radia S, *et al*. The Hadoop distributed file system. In: IEEE Symposium on Mass Storage Systems and Technologies (MSST); 2010.

\[15\] Magaki I, Khazraee M, Gutierrez LV, *et al*. ASIC clouds: Specializing the data center. In: ACM/IEEE International Symposium on Computer Architecture (ISCA); 2016.

\[16\] Caulfield AM, Chung ES, Putnam A, *et al*. A cloud-scale acceleration architecture. In: IEEE/ACM International Symposium on Microarchitecture (MICRO); 2016.

\[17\] Gutierrez A, Cieslak M, Giridhar B, *et al*. Integrated 3D-stacked server designs for increasing physical density of key-value stores. SIGPLAN Not. 2014;49(4):485–498.

\[18\] Putnam A, Caulfield AM, Chung ES, *et al*. A reconfigurable fabric for accelerating large-scale data center services. SIGARCH Comput Archit News. 2014;42(3):13–24.

\[19\] Wess M, Manoj PDS and Jantsch A. Weighted quantization-regularization in DNNs for weight memory minimization towards HW implementation. IEEE Transactions on ComputerAided Systems of Integrated Circuits and Systems. 2018.

\[20\] Lechner M, Jantsch A and Manoj PDS. ResCoNN: Resource-efficient FPGA-accelerated CNN for traffic sign classification. In: IEEE International Green and Sustainable Computing Conference (IGSC); 2019.

\[21\] Vashist A, Keats A, Manoj PDS, *et al*. Unified testing and security framework for wireless network-on-chip enabled multi-core chips. In: ACM/IEEE International Conference on Hardware/Software Codesign and System Synthesis (CODES+ISSS); 2019.

\[22\] Wess M, Manoj PDS and Jantsch A. Weighted quantization-regularization in DNNs for weight memory minimization towards HW implementation. In: International Conference on Hardware/Software Codesign and System Synthesis (CODES+ISSS); 2018.

\[23\] Yu H, Ni L and Wang Y. Non-volatile In-Memory Computing by Spintronics. Vol. 2. Morgan & Claypool Publishers; 2016. Available from: [https://dl.acm.org/doi/book/10.5555/3086882](https://dl.acm.org/doi/book/10.5555/3086882).

\[24\] Yu H and Wang Y. Design Exploration of Emerging Nano-scale Nonvolatile Memory. Springer; 2014. Available from: [https://www.springer.com/gp/book/9781493905508](https://www.springer.com/gp/book/9781493905508).

\[25\] Song Y, Yu H and Manoj PDS. Reachability-based robustness verification and optimization of SRAM dynamic stability under process variations. IEEE Trans on Computer-Aided Design of Integrated Circuits and Systems. 2014;33(4):585–598.

\[26\] SongY, Manoj PDS andYu H. Zonotope-based nonlinear model order reduction for fast performance bound analysis of analog circuits with multipleinterval-valued parameter variations. In: Design, Automation Test in Europe Conference Exhibition (DATE); 2014.

\[27\] SongY, Manoj PDS and Yu H. A robustness optimization of SRAM dynamic stability by sensitivity-based reachability analysis. In: Asia and South Pacific Design Automation Conference (ASP-DAC); 2014.

\[28\] Wu SS, Wang K, Manoj PDS, *et al*. A thermal resilient integration of many-core microprocessors and main memory by 2.5D TSI I/Os. In: Design, Automation Test in Europe Conference Exhibition (DATE); 2014.

\[29\] Burger D, Goodman JR and Kägi A. Memory Bandwidth Limitations of Future Microprocessors. SIGARCH Comput Archit News. 1996;24(2): 78–89.

\[30\] Manoj PDS, Yu H, Gu C, *et al*. A zonotoped macromodeling for reachability verification of eye-diagram in high-speed I/O links with jitter. In: IEEE/ACM International Conference on Computer-Aided Design (ICCAD); 2014.

\[31\] Makrani HM, Sayadi H, Manoj PDS, *et al*. A comprehensive memory analysis of data intensive workloads on server class architecture. In: International Symposium on Memory Subsystems; 2018.

\[32\] Makrani HM, Sayadi H, Manoj PDS, *et al*. Compressive sensing on storage data: An effective solution to alleviate I/O bottleneck in data-intensive workloads. In: IEEE International Conference on Application-specific Systems, Architectures and Processors; 2018.

\[33\] Manoj PDS, Wang K, Huang H, *et al*. Smart I/Os: A data-pattern aware 2.5D interconnect with space-time multiplexing. In: ACM/IEEE International Workshop on System Level Interconnect Prediction (SLIP); 2015.

\[34\] Hantao H, Manoj PDS, Xu D, *et al*. Reinforcement learning based self-adaptive voltage-swing adjustment of 2.5D I/Os for many-core microprocessor and memory communication. In: IEEE/ACM Int. Conf. on Computer-Aided Design (ICCAD); 2014.

\[35\] Xu D, Manoj PDS, Huang H, *et al*. An energy-efficient 2.5D through-silicon interposer I/O with self-adaptive adjustment of output-voltage swing. In: IEEE/ACM International Symposium on Low Power Electronics and Design (ISLPED); 2014.

\[36\] Wang J, Ma S, Manoj PDS, *et al*. High-speed and low-power 2.5D I/O circuits for memory-logic-integration by through-silicon interposer. In: IEEE International 3D Systems Integration Conference (3DIC); 2013.

\[37\] Manoj PDS, Wang K and Yu H. Peak power reduction and workload balancing by space-time multiplexing based demand-supply matching for 3D thousand-core microprocessor. In: ACM/EDAC/IEEE Design Automation Conf.; 2013.

\[38\] Manoj PDS andYu H. Cyber-physical management for heterogeneously integrated 3D thousand-core on-chip microprocessor. In: IEEE International Symposium on Circuits and Systems (ISCAS); 2013.

\[39\] Manoj PDS, Joseph A, Haridass A, *et al*. Application and thermal reliability-aware reinforcement learning based multi-core power management. ACM Transactions on Embedded Computing Systems. 2019.

\[40\] Pagani S, Manoj PDS, Jantsch A, *et al*. Machine learning for power, energy, and thermal management on multi-core processors: A survey. IEEE Transactions on Computer Aided Systems of Integrated Circuits and Systems. 2018.

\[41\] Manoj PDS, Jantsch A and Shafique M. SmartDPM: Dynamic power management using machine learning for multi-core microprocessors. Journal of Low-Power Electronics. 2018.

\[42\] Manoj PDS, Lin J, Zhu S, *et al*. A scalable network-on-chip microprocessor with 2.5D integrated memory and accelerator. IEEE Transactions on Circuits and Systems I: Regular Papers. 2017;64(6):1432–1443.

\[43\] Matsunaga S, Hayakawa J, Ikeda S, *et al*. MTJ-based nonvolatile logicin-memory circuit, future prospects and issues. In: Proceedings of the Conference on Design, Automation and Test in Europe. European Design and Automation Association; 2009. pp. 433–435.

\[44\] Matsunaga S, Hayakawa J, Ikeda S, *et al*. Fabrication of a nonvolatile full adder based on logic-in-memory architecture using magnetic tunnel junctions. Applied Physics Express. 2008;1(9):091301.

\[45\] Kautz WH. Cellular logic-in-memory arrays. IEEE Transactions on Computers. 1969;100(8):719–727.

\[46\] Kimura H, Hanyu T, Kameyama M, *et al*. Complementary ferroelectric-capacitor logic for low-power logic-in-memory VLSI. IEEE Journal of Solid-State Circuits. 2004;39(6):919–926.

\[47\] Hanyu T, Teranishi K and Kameyama M. Multiple-valued logic-in-memory VLSI based on a floating-gate-MOS pass-transistor network. In: Solid-State Circuits Conference, 1998. Digest of Technical Papers. 1998 IEEE International. IEEE; 1998. pp. 194–195.

\[48\] Kouzes RT, Anderson GA, Elbert ST, *et al*. The changing paradigm of data-intensive computing. Computer. 2009;(1):26–34.

\[49\] Wolpert DH. The lack of a priori distinctions between learning algorithms. Neural Computation. 1996;8(7):1341–1390.

\[50\] Hinton GE, Osindero S and Teh YW. A fast learning algorithm for deep belief nets. Neural Computation. 2006;18(7):1527–1554.

\[51\] Müller KR, Tangermann M, Dornhege G, *et al*. Machine learning for real-time single-trial EEG-analysis: From brain-computer interfacing to mental state monitoring. Journal of Neuroscience Methods. 2008;167(1):82–90.

\[52\] Glorot X and Bengio Y. Understanding the difficulty of training deep feed for-ward neural networks. In: International Conference on Artificial Intelligence and Statistics; 2010. pp. 249–256.

\[53\] Huang GB, Zhu QY and Siew CK. Extreme learning machine: Theory and applications. Neurocomputing. 2006;70(1):489–501.

\[54\] Coates A, Ng AY and Lee H. An analysis of single-layer networks in unsupervised feature learning. In: International Conference on Artificial Intelligence and Statistics; 2011. pp. 215–223.

\[55\] Park S, Qazi M, Peh LS, *et al*. 40.4 fJ/bit/mm low-swing on-chip signaling with self-resetting logic repeaters embedded within a mesh NoC in 45nm SOI CMOS. In: Proceedings of the Conference on Design, Automation and Test in Europe. EDA Consortium; 2013. pp. 1637–1642.

\[56\] Kumar V, Sharma R, Uzunlar E, *et al*. Airgap interconnects: Modeling, optimization, and benchmarking for backplane, PCB, and interposer applications. IEEE Transactions on Components, Packaging and Manufacturing Technology. 2014;4(8):1335–1346.

\[57\] Wang Y, Yu H, Ni L, *et al*. An energy-efficient nonvolatile in-memory computing architecture for extreme learning machine by domain-wall nanowire devices. IEEE Transactions on Nanotechnology. 2015;14(6):998–1012.

\[58\] Akinaga H and Shima H. Resistive random access memory (ReRAM) based on metal oxides. Proceedings of the IEEE. 2010;98(12):2237–2251.

\[59\] Kim KH, Gaba S, Wheeler D, *et al*. A functional hybrid memristor crossbararray/CMOS system for data storage and neuromorphic applications. Nano Letters. 2011;12(1):389–395.

\[60\] Chua LO. Memristor—The missing circuit element. IEEE Transactions on Circuit Theory. 1971;18(5):507–519.

\[61\] Williams SR. How we found the missing memristor. IEEE Spectrum. 2008;45(12):28–35.

\[62\] Strukov DB, Snider GS, Stewart DR, *et al*. The missing memristor found. Nature. 2008;453(7191):80–83.

\[63\] Shang Y, Fei W and Yu H. Analysis and modeling of internal state variables for dynamic effects of nonvolatile memory devices. IEEE Transactions on Circuits and Systems I: Regular Papers. 2012;59(9):1906–1918.

\[64\] FeiW, Yu H, Zhang W, *et al*. Design exploration of hybrid CMOS and memristor circuit by new modified nodal analysis. IEEE Transactions on Very Large Scale Integration (VLSI) Systems. 2012;20(6):1012–1025.

\[65\] Liu X, Mao M, Liu B, *et al*. RENO: A high-efficient reconfigurable neuromorphic computing accelerator design. In: Proceedings of the 52nd Annual Design Automation Conference. ACM; 2015. pp. 66.1–66.6.

\[66\] Kim Y, Zhang Y and Li P. A digital neuromorphic VLSI architecture with memristor crossbar synaptic array for machine learning. In: International SOC Conference (SOCC). IEEE; 2012. pp. 328–333.

\[67\] Lu W, Kim KH, Chang T, *et al*. Two-terminal resistive switches (memristors) for memory and logic applications. In: Asia and South Pacific Design Automation Conference (ASP-DAC). IEEE; 2011. pp. 217–223.

\[68\] Dennard RH, Gaensslen FH, Yu H, *et al*. Design of ion-implanted MOSFET’s with very small physical dimensions. IEEE Journal of Solid-State Circuits. 1974;9(5):256–268.

\[69\] Loh GH. 3D-Stacked memory architectures for multi-core processors. In: International Symposium on Computer Architecture; 2008.

\[70\] Strenz R. Embedded flash technologies and their applications: Status outlook. In: International Electron Devices Meeting; 2011.

\[71\] Energy Limits to the Computational Power of the Human Brain. Last Accessed: June, 15, 2020. Available from: [https://foresight.org/Updates/Update06/Update06.1.php](https://foresight.org/Updates/Update06/Update06.1.php).

\[72\] Laughlin SB, de Ruyter van Steveninck RR and Anderson JC. The metabolic cost of neural information. Nature Neuroscience. 1998;1:36–41.

\[73\] Jiang Z, Wu Y, Yu S, *et al*. A compact model for metal-oxide resistive random access memory with experiment verification. IEEE Transactions on Electron Devices. 2016;63(5):1884–1892.

\[74\] Merolla PA, Arthur JV, Alvarez-Icaza R, *et al*. A million spiking-neuron integrated circuit with a scalable communication network and interface. Science. 2014;345(6197):668–673.

\[75\] Davies M, Srinivasa N, Lin T, *et al*. Loihi: A neuromorphic manycore processor with on-chip learning. IEEE Micro. 2018;38(1): 82–99.

\[76\] Hu M, Graves CE, Li C, *et al*. Memristor-based analog computation and neural network classification with a dot product engine. Advanced Materials. 2018;30(9):1705914.

\[77\] Yu S. Neuro-inspired computing with emerging nonvolatile memories. Proceedings of the IEEE. 2018;106(2):260–285.

\[78\] Pei J, Deng L, Song S, *et al*. Towards artificial general intelligence with hybrid Tianjic chip architecture. Nature. 2019;572:106–111.

\[79\] Yao P, Wu H, Gao B, *et al*. Fully hardware-implemented memristor convolutional neural network. Nature. 2020;577:641–646.

\[80\] Roy K, Jaiswal A and Panda P. Towards spike-based machine intelligence with neuromorphic computing. Nature. 2019 11;575:607–617.

\[81\] Sherstinsky A. Fundamentals of recurrent neural network (RNN) and long short-term memory (LSTM) network. CoRR. 2018;abs/1808.03314.

\[82\] Yu S. Resistive random access memory (RRAM). Synthesis Lectures on Emerging Engineering Technologies. 2016;2:1–79.

\[83\] Kim KH, Gaba S, Wheeler D, *et al*. A functional hybrid memristor crossbararray/CMOS system for data storage and neuromorphic applications. Nano Letters. 2012;12(1):389–395.

\[84\] Yang JJ, Zhang MX, Pickett M, *et al*. Engineering nonlinearity into memristors for passive crossbar applications. Applied Physics Letters. 2012 03;100.

\[85\] Park S, Kim H, Choo M, *et al*. RRAM-based synapse for neuromorphic system with pattern recognition function. In: International Electron Devices Meeting; 2012.

\[86\] Khvalkovskiy A, Apalkov D, Watts S, *et al*. Basic principles of STT-MRAM cell operation in memory arrays. Journal of Physics D: Applied Physics. 2013;46(7):1–35

\[87\] Apalkov D, Khvalkovskiy A, Watts S, *et al*. Spin-transfer torque magnetic random access memory (STT-MRAM). J Emerg Technol Comput Syst. 2013;9(2).

\[88\] Bi G and Poo M. Synaptic modifications in cultured hippocampal neurons: Dependence on spike timing, Synaptic Strength, and Postsynaptic Cell Type. J Neuroscience. 1998;18(24):10467–10472.

\[89\] Hu M, Strachan JP, Li Z, *et al*. Dot-product engine for neuromorphic computing: Programming 1T1M crossbar to accelerate matrix-vector multiplication. In: Annual Design Automation Conference; 2016.

\[90\] Kuzum D, Jeyasingh R, Lee B, *et al*. Nanoelectronic programmable synapses based on phase change materials for brain-inspired computing. Nano Letters. 2011 06;12:2179–86.

\[91\] Indiveri G, Chicca E and Douglas R. A VLSI array of low-power spiking neurons and bistable synapses with spike-timing dependent plasticity. IEEE Transactions on Neural Networks. 2006;17(1):211–221.

\[92\] Chen P, Lin B, Wang I, *et al*. Mitigating effects of non-ideal synaptic device characteristics for on-chip learning. In: IEEE/ACM International Conference on Computer-Aided Design (ICCAD); 2015.

\[93\] Wang IT, Chang CC, Chiu LW, *et al*. 3D Ta/TaOx /TiO2 /Ti synaptic array and linearity tuning of weight update for hardware neural network applications. Nanotechnology. 2016;27:365204.

\[94\] Angizi S, He Z, Parveen F and Fan D. IMCE: Energy-efficient bit-wise in-memory convolution engine for deep neural network. In: Asia and South Pacific Design Automation Conference (ASP-DAC); 2018.

\[95\] Patterson D, Anderson T, Cardwell N, *et al.* A case for intelligent RAM. IEEE Micro. 1997.

\[96\] Pudukotai Dinakarrao SM, Lin J, Zhu S, *et al.* A scalable network-onchip microprocessor with 2.5D integrated memory and accelerator. IEEE Transactions on Circuits and Systems I: Regular Papers. 2017.

\[97\] Yong-Bin K and Chen T. Assessing merged DRAM/Logic technology. Integr VLSI J. 1999.

\[98\] Deng Q, ZhangY, Zhang M and Yang J. LAcc: Exploiting lookup table-based fast and accurate vector multiplication in DRAM-based CNN accelerator. In: ACM/IEEE Design Automation Conference (DAC); 2019.

\[99\] Courbariaux M, Bengio Y and David J-P. BinaryConnect: Training deep neural networks with binary weights during propagations. In: Proceedings of the 28th International Conference on Neural Information Processing Systems; 2015.

\[100\] Courbariaux M and Bengio Y. BinaryNet: Training deep neural networks with weights and activations constrained to +1 or -1. ArXiv. 2016.

\[101\] Rastegari M, Ordonez V, Redmon J and Farhadi A. XNOR-Net: ImageNet classification using binary convolutional neural networks. In: Computer Vision – ECCV; 2016.

\[102\] Li F and Liu B. Ternary weight networks. CoRR. 2016.

\[103\] Wess M, Dinakarrao SMP and Jantsch A. Weighted quantization-regularization in DNNs for weight memory minimization toward HW implementation. IEEE Transactions on Computer-Aided Design of Integrated Circuits and Systems. 2018.

\[104\] Li S, Niu D, Malladi KT *et al.* DRISA: A DRAM-based reconfigurable in-situ accelerator. In: IEEE/ACM International Symposium on Microarchitecture; 2017.

\[105\] Deng Q, Jiang L, Zhang Y, Zhang M and Yang J. DrAcc: A DRAM-based accelerator for accurate CNN inference. In: ACM/ESDA/IEEE Design Automation Conference (DAC);2018.

\[106\] Yin S, Jiang Z, Seo J and Seok M. XNOR-SRAM: In-Memory computing SRAM macro for binary/ternary deep neural networks. IEEE Journal of Solid-State Circuits. 2020.

\[107\] Sun X, Yin S, Peng X, Liu R, Seo J and Yu S. XNOR-RRAM: A scalable and parallel resistive synaptic architecture for binary neural networks. In: Design, Automation Test in Europe Conference Exhibition (DATE); 2018.

\[108\] Tang T, Xia L, Li B, Wang Y and Yang H. Binary convolutional neural network on RRAM. In: Asia and South Pacific Design Automation Conference (ASPDAC); 2017.

\[109\] Pan Y, Ouyang P, Zhao Y, *et al.* A multilevel cell STT-MRAM-based computing in-memory accelerator for binary convolutional neural network. IEEE Transactions on Magnetics. 2018.

\[110\] Angizi S, He Z, Awad A and Fan D. MRIMA: An MRAM-based in-memory accelerator. IEEE Transactions on Computer-Aided Design of Integrated Circuits and Systems. 2020.

\[111\] Taherinejad N, Manoj PDS and Jantsch A. Memristors’ potential for multi-bit storage and pattern learning. IEEE European Modelling Symposium (EMS). 2015.

\[112\] Chi P, Li S, Xu C, *et al.* PRIME: A novel processing-in-memory architecture for neural network computation in ReRAM-based main memory. In: ACM/IEEE International Symposium on Computer Architecture (ISCA); 2016.

\[113\] Simon WA, Qureshi YM, Levisse A, *et al*. Blade: A bitline accelerator for devices on the edge. In: Proceedings of the 2019 on Great Lakes Symposium on VLSI; 2019. pp. 207–212.

\[114\] Yang J, Kong Y, Wang Z, *et al*. 24.4 sandwich-RAM: An energy-efficient in-memory BWN architecture with pulse-width modulation. In: 2019 IEEE International Solid-State Circuits Conference-(ISSCC). IEEE; 2019. pp. 394–396.

\[115\] Bankman D, Yang L, Moons B, *et al*. An always-on 3.8uJ/86% CIFAR–10 mixed-signal binary CNN processor with all memory on chip in 28-nm CMOS. IEEE Journal of Solid-State Circuits. 2018;54(1):158–172.

\[116\] Si X, Chen JJ, Tu YN, *et al*. 24.5 A twin–8T SRAM computation-inmemory macro for multiple-bit CNN-based machine learning. In: 2019 IEEE International Solid-State Circuits Conference-(ISSCC). IEEE; 2019. pp. 396–398.

\[117\] Si X, Tu YN, Huanq WH, *et al*. 15.5 A 28nm 64Kb 6T SRAM computingin-memory macro with 8b MAC operation for AI edge chips. In: 2020 IEEE International Solid-State Circuits Conference (ISSCC). IEEE; 2020. pp. 246–248.

\[118\] Dong Q, Sinangil ME, Erbagci B, *et al*. 15.3 A 351TOPS/W and 372.4 GOPS compute-in-memory SRAM macro in 7nm FinFET CMOS for machine-learning applications. In: 2020 IEEE International Solid-State Circuits Conference–(ISSCC). IEEE; 2020. pp. 242–244.

\[119\] Zhang Z, Chen JJ, Si X, *et al*. A 55nm 1-to-8 bit configurable 6T SRAM based computing-in-memory unit-macro for CNN-based AI edge processors. In: 2019 IEEE Asian Solid-State Circuits Conference (A-SSCC). IEEE; 2019. pp. 217–218.

\[120\] Xue CX, Chen WH, Liu JS, *et al*. Embedded 1-Mb ReRAM-based computing-in-memory macro with multibit input and weight for CNN-based AI edge processors. IEEE Journal of Solid-State Circuits. 2019;55(1): 203–215.

\[121\] Mochida R, Kouno K, Hayata Y, *et al*. A 4M synapses integrated analog ReRAM based 66.5 TOPS/W neural-network processor with cell current controlled writing and flexible network architecture. In: 2018 IEEE Symposium on VLSI Technology. IEEE; 2018. pp. 175–176.

\[122\] Eckert C, Wang X, Wang J, *et al.* Neural cache: Bit-serial in-cache acceleration of deep neural networks. In: International Symposium on Computer Architecture (ISCA); 2018.

\[123\] Seshadri V, Lee D, Mullins T, *et al.* Ambit: In-memory accelerator for bulk bitwise operations using commodity DRAM technology. IEEE/ACM International Symposium on Microarchitecture (MICRO). 2017.

\[124\] Li S, Glova AO, Hu X, *et al.* SCOPE: A stochastic computing engine for DRAM-based in-situ accelerator. In: IEEE/ACM International Symposium on Microarchitecture (MICRO); 2018.

\[125\] Sutradhar PR, Connolly M, Bavikadi S, *et al*. pPIM: A programmable processor-in-memory architecture with precision-scaling for deep learning. IEEE Computer Architecture Letters. 2020;19(2):118–121.

\[126\] Ali M, Jaiswal A, Kodge S, Agrawal A, Chakraborty I and Roy K. IMAC: In-memory multi-bit multiplication and accumulation in 6T SRAM array. IEEE Transactions on Circuits and Systems I: Regular Papers. 2020.

\[127\] Shafiee A, Nag A, Muralimanohar N, *et al.* ISAAC: A convolutional neural network accelerator with in-situ analog arithmetic in crossbars. In: ACM/IEEE International Symposium on Computer Architecture (ISCA); 2016.

\[128\] Song L, Qian X, Li H and Chen Y. PipeLayer: A pipelined ReRAM-based accelerator for deep learning. In: IEEE Int. Symp. on High Performance Computer Architecture (HPCA); 2017.

\[129\] Qiao X, Cao X, Yang H, Song L and Li H. AtomLayer: A universal ReRAM-based CNN accelerator with atomic layer computation. In: ACM/ESDA/IEEE Design Automation Conference (DAC); 2018.

\[130\] Patil AD, Hua H, Gonugondla S, Kang M and Shanbhag NR. An MRAM-based deep in-memory architecture for deep neural networks. In: IEEE International Symposium on Circuits and Systems; 2019.

\[131\] Fan D, Angizi S. Energy efficient in-memory binary deep neural network accelerator with dual-mode SOT-MRAM. In: IEEE International Conference on Computer Design (ICCD); 2017.

\[132\] Angizi S, He Z, Rakin AS and Fan D. CMP-PIM: An energy-efficient comparator-based processing-in-memory neural network accelerator. In: ACM/ESDA/IEEE Design Automation Conference (DAC); 2018.

\[133\] Yu H, Ni L and Huang H. In: Vaidyanathan S, Volos C, editors. Distributed in-memory computing on binary memristor-crossbar for machine learning. Springer; 2017. pp. 275–304. Available from: [https://link.springer.com/chapter/10.1007/978-3-319-51724-7\_12](https://link.springer.com/chapter/10.1007/978-3-319-51724-7_12).

\[134\] Strukov DB and Williams RS. Exponential ionic drift: Fast switching and low volatility o thin-film memristors. Applied Physics A. 2009;94(3):515–519.

\[135\] Joglekar YN and Wolf SJ. The elusive memristor: Properties of basic electrical circuits. European Journal of Physics. 2009;30(4):661.

\[136\] Biolek Z, Biolek D and Biolkova V. SPICE model of memristor with nonlinear dopant drift. Radioengineering. 2009;18(2):210–214.

\[137\] Wang Z, Joshi S, Savel’ev SE, *et al*. Memristors with diffusive dynamics as synaptic emulators for neuromorphic computing. Nature Materials. 2017;16(1):101–108.

\[138\] Midya R, Wang Z, Zhang J, *et al*. Anatomy of Ag/Hafnia-based selectors with 1010 nonlinearity. Advanced Materials. 2017;29(12).

\[139\] Govoreanu B, Kar GS, Chen YY, *et al*.10 × 10 nm2 Hf/HfOx crossbar resistive RAM with excellent performance, reliability and low-energy operation. In: International Electron Devices Meeting (IEDM); 2011. pp. 31.6.1–31.6.4.

\[140\] Kang J, Gao B, Chen B, *et al*. 3D RRAM: Design and optimization. In: IEEE Conference on International Solid-State and Integrated Circuit Technology (ICSICT); 2014. pp. 1–4.

\[141\] Fan D, Sharad M and Roy K. Design and synthesis of ultralow energy spin-memristor threshold logic. IEEE Transactions on Nanotechnology. 2014;13(3):574–583.

\[142\] Gu P, Li B, Tang T, *et al*. Technological exploration of RRAM crossbar array for matrix-vector multiplication. In: Asia and South Pacific Design Automation Conference (ASP-DAC). IEEE; 2015. pp. 106–111.

\[143\] Srimani T, Manna B, Mukhopadhyay AK, *et al*. Energy efficient and high performance current-mode neural network circuit using memristors and digitally assisted analog CMOS neurons. arXiv preprint arXiv:151109085. 2015.

\[144\] Wang Y, Yu H and Zhang W. Nonvolatile CBRAM-crossbar-based 3-D-integrated hybrid memory for data retention. IEEE Transactions on Very Large Scale Integration (VLSI) Systems. 2014;22(5):957–970.

\[145\] Hu M, Strachan JP, Li Z, *et al*. Dot-product engine for neuromorphic computing: Programming 1T1M crossbar to accelerate matrix-vector multiplication. In: Design Automation Conference (DAC); 2016. pp. 19.1–19.6.

\[146\] Xia L, Tang T, Huangfu W, *et al*. Switched by input: Power efficient structure for RRAM-based convolutional neural network. In: Proceedings of the 53rd Annual Design Automation Conference. ACM; 2016. pp. 125.1–125.6.

\[147\] Ni L, Wang Y, Yu H, *et al*. An energy-efficient matrix multiplication accelerator by distributed in-memory computing on binary RRAM crossbar. In: Asia and South Pacific Design Automation Conference (ASP-DAC). IEEE; 2016. pp. 280–285.

\[148\] Ni L, Huang H and Yu H. On-line machine learning accelerator on digital RRAM-crossbar. In: International Symposium on Circuits and Systems (ISCAS). IEEE; 2016. pp. 113–116.

\[149\] Tang T, Xia L, Li B, *et al*. Binary convolutional neural network on RRAM. In: Asia and South Pacific Design Automation Conference (ASP-DAC); 2017. pp. 782–787.

\[150\] Yan B, Mahmoud AM, Yang JJ, *et al*. A neuromorphic ASIC design using one-selector-one-memristor crossbar. In: International Symposium on Circuits and Systems (ISCAS); 2016. pp. 1390–1393.

\[151\] Jackson TC, Sharma AA, Bain JA, *et al*. Oscillatory neural networks based on TMO nano-oscillators and multi-level RRAM cells. IEEE Journal on Emerging and Selected Topics in Circuits and Systems. 2015;5(2): 230–241.

\[152\] Sharma AA, Li Y, Skowronski M, *et al*. High-frequency TaOx-based compact oscillators. IEEE Transactions on Electron Devices. 2015;62(11):3857–3862.

\[153\] Maffezzoni P, Daniel L, Shukla N, *et al*. Modelling hysteresis in vanadium dioxide oscillators. Electronics Letters. 2015;51(11):819–820.

\[154\] Chua L. Resistance switching memories are memristors. Applied Physics A. 2011;102(4):765–783.

\[155\] Pershin YV, Fontaine SL and Ventra MD. Memristive model of Amoeba learning. Physical Review E. 2009;80:1–6.

\[156\] Borghetti J, Snider GS, Kuekes PJ, *et al*. Memristive switches enable stateful logic operations via material implications. Nature. 2010;464:873–876.

\[157\] Pershin YV and Di Ventra M. Neuromorphic, digital, and quantum computation with memory circuit elements. Proceedings of the IEEE. 2012;100(6):2071–2080.

\[158\] Hongal V, Kotikalapudi R and Choi M. Design, test, and repair of MLUT (memristor look-up table) based asynchronous nanowire reconfigurable crossbar architecture. IEEE Journal on Emerging and Selected Topics in Circuits and Systems,. 2014;4(4):427–437.

\[159\] Levy Y, Bruck J, Cassuto Y, *et al*. Logic operations in memory using a memristive Akers array. Microelectronics Journal. 2014;45:873–876.

\[160\] Ho Y, Huang GM and Li P. Dynamical properties and design analysis for nonvolatile memristor memories. IEEE Transactions on Circuits and Systems I: Regular Papers,. 2011;58(4):724–736.

\[161\] Mohammad B, Homouz D and Elgabra H. Robust hybrid memristor-CMOS memory: Modeling and design. IEEE Transactions on Very Large Scale Integration (VLSI) Systems. 2013;21(11):2069–2079.

\[162\] Baghel VS and Akashe S. Low power memristor based 7T SRAM using MTCMOS technique. In: 2015 Fifth International Conference on Advanced Computing Communication Technologies (ACCT); 2015. pp. 222–226.

\[163\] International Technology Roadmap for Semiconductors—System Drivers; 2011. Available from: [https://www.semiconductors.org/wp-content/uploads/2018/08/2011SysDrivers.pdf](https://www.semiconductors.org/wp-content/uploads/2018/08/2011SysDrivers.pdf).

\[164\] Niu D, Chen Y and Xie Y. Low-power dual-element memristor based memory design. In: 2010 ACM/IEEE International Symposium on Low-Power Electronics and Design (ISLPED); 2010. pp. 25–30.

\[165\] Kim H, Sah MP, Yang C, *et al*. Memristor-based multilevel memory. In: 2010 12th International Workshop on Cellular Nanoscale Networks and Their Applications (CNNA); 2010. pp. 1–6.

\[166\] Zangeneh M and Joshi A. Design and optimization of nonvolatile multibit 1T1R resistive RAM. IEEE Transactions on Very Large Scale Integration (VLSI) Systems. 2014;22(8):1815–1828.

\[167\] Rothenbuhler A, Tran T, Smith EHB, *et al*. Reconfigurable threshold logic gates using memristive devices. Journal of Low Power Electronics and Applications. 2013;3(2):174.

\[168\] Biolek D, Di Ventra M and Pershin YV. Reliable SPICE simulations of memristors, memcapacitors and meminductors. ArXiv e-prints. 2013;22(4): 945–968.

\[169\] Taherinejad N, Sai Manoj PD and Jantsch A. Memristors’ potential for multi-bit storage and pattern learning. Proceedings of the IEEE European Modelling Symposium (EMS) Conference. 2015 Oct.

\[170\] Kvatinsky S, Wald N, Satat G, *et al*. MRL—Memristor ratioed logic. In: IEEE Int. W. on Cellular Nanoscale Networks and Their Applications; 2012.

\[171\] Zhang Y, Shen Y, Wang X, *et al*. A novel design for memristor-based logic switch and crossbar circuits. IEEE Tran on Circuits and Systems I. 2015;62(5):1402–1411.

\[172\] Vourkas I, Batsos A and Sirakoulis GC. SPICE modeling of nonlinear memristive behavior. Int J of Circuit Theory and Applications. 2015;43(5): 553–565.

\[173\] Vourkas I and Siakoulis GC. Memristor-based nanoelectronic computing architectures. Vol. 19. Emergence, Complexity and Computation. Springer; 2015. pp. 9–26. Available from: [https://www.springer.com/gp/book/9783319226460](https://www.springer.com/gp/book/9783319226460).

\[174\] Haykin SS. Neural Networks and Learning Machines. Vol. 3. Pearson Education, Upper Saddle River; 2009.

\[175\] Wold S, Esbensen K and Geladi P. Principal component analysis. Chemometrics and Intelligent Laboratory Systems. 1987;2(1-3):37–52.

\[176\] Suykens JA and Vandewalle J. Least squares support vector machine classifiers. Neural Processing Letters. 1999;9(3):293–300.

\[177\] LeCun YA, Bottou L, Orr GB, *et al*. Efficient backprop. Neural Networks: Tricks of the Trade. Springer; 2012. pp. 9–48.

\[178\] Werbos PJ. Backpropagation through time: What it does and how to do it. Proceedings of the IEEE. 1990;78(10):1550–1560.

\[179\] Higham NJ. Cholesky factorization. Wiley Interdisciplinary Reviews: Computational Statistics. 2009;1(2):251–254.

\[180\] Krishnamoorthy A and Menon D. Matrix inversion using Cholesky decomposition. arXiv preprint arXiv:11114144. 2011.

\[181\] Cong J and Xiao B. Minimizing computation in convolutional neural networks. In: International Conference on Artificial Neural Networks (ICANN). Springer; 2014. pp. 281–290.

\[182\] Michalski RS, Carbonell JG and Mitchell TM. Machine learning: An artificial intelligence approach. Springer Science & Business Media; 2013.

\[183\] Zhang L and Suganthan P. A comprehensive evaluation of random vector functional link networks. Information Sciences. 2016;367:1094–1105.

\[184\] Bache K and Lichman M. UCI Machine Learning Repository; 2013. Available from: [http://archive.ics.uci.edu/ml](http://archive.ics.uci.edu/ml).

\[185\] LeCun Y, Bengio Y and Hinton G. Deep learning. Nature. 2015;521(7553): 436–444.

\[186\] Lawrence S, Giles CL, Tsoi AC, *et al*. Face recognition: A convolutional neural-network approach. IEEE Transactions on Neural Networks. 1997;8(1):98–113.

\[187\] Krizhevsky A, Sutskever I and Hinton GE. Imagenet classification with deep convolutional neural networks. In: Advances in Neural Information Processing Systems (NIPS); 2012. pp. 1097–1105.

\[188\] Courbariaux M, Bengio Y and David JP. Binaryconnect: Training deep neural networks with binary weights during propagations. In: Advances in Neural Information Processing Systems (NIPS); 2015. pp. 3123–3131.

\[189\] Liu Z, Li Y, Ren F, *et al*. A binary convolutional encoder-decoder network for real-time natural scene text processing. arXiv preprint arXiv:161203630. 2016.

\[190\] Ioffe S and Szegedy C. Batch normalization: Accelerating deep network training by reducing internal covariate shift. arXiv preprint arXiv:150203167. 2015.

\[191\] Qiu J, Wang J, Yao S, *et al*. Going deeper with embedded FPGA platform for convolutional neural network. In: International Symposium on Field-Programmable Gate Arrays (FPGA); 2016. pp. 26–35.

\[192\] Plaut DC. Experiments on Learning by Back Propagation. Carnegie Mellon University; 1986. Available from: [http://www.cnbc.cmu.edu/~plaut/papers/pdf/PlautNowlanHinton86TR.backprop.pdf](http://www.cnbc.cmu.edu/~plaut/papers/pdf/PlautNowlanHinton86TR.backprop.pdf).

\[193\] Hubara I, Soudry D andYaniv RE. Binarized neural networks. arXiv preprint arXiv:160202505. 2016.

\[194\] Davis A and Arel I. Low-rank approximations for conditional feedforward computation in deep neural networks. arXiv preprint arXiv:13124461. 2013.

\[195\] Nakkiran P, Alvarez R, Prabhavalkar R, *et al*. Compressing deep neural networks using a rank-constrained topology. In: INTERSPEECH; 2015. pp. 1473–1477.

\[196\] Novikov A, Podoprikhin D, Osokin A, *et al*. Tensorizing neural networks. In: Advances in Neural Information Processing Systems (NIPS); 2015. pp. 442–450.

\[197\] Oseledets IV. Tensor-train decomposition. SIAM Journal on Scientific Computing. 2011;33(5):2295–2317.

\[198\] Cichocki A. Era of big data processing: A new approach via tensor networks and tensor decompositions. arXiv preprint arXiv:14032048. 2014.

\[199\] Hagan MT, Demuth HB, Beale MH, *et al*. Neural Network Design. Vol. 20. PWS publishing company, Boston; 1996.

\[200\] Bengio Y, Lamblin P, Popovici D, *et al*. Greedy Layer-Wise Training of Deep Networks. In: Advances in Neural Information Processing Systems; 2007. pp. 153–160.

\[201\] Tang J, Deng C and Huang GB. Extreme learning machine for multilayer perceptron. IEEE Transactions on Neural Networks and Learning Systems. 2016;27(4):809–821.

\[202\] Erhan D, Manzagol PA, Bengio Y, *et al*. The difficulty of training deep architectures and the effect of unsupervised pre-training. In: AISTATS. vol. 5; 2009. pp. 153–160.

\[203\] Holtz S, Rohwedder T and Schneider R. The alternating linear scheme for tensor optimization in the tensor train format. SIAM Journal on Scientific Computing. 2012;34(2):A683–A713.

\[204\] Oseledets IV and Dolgov S. Solution of linear systems and matrix inversion in the TT-format. SIAM Journal on Scientific Computing. 2012;34(5):A2718– A2739.

\[205\] Wright J, Yang AY, Ganesh A, *et al*. Robust face recognition via sparse representation. IEEE Transactions on Pattern Analysis and Machine Intelligence. 2009;31(2):210–227.

\[206\] Lee H, Chen P, Wu T, *et al*. Low power and high speed bipolar switching with a thin reactive Ti buffer layer in robust HfO2 based RRAM. In: International Electron Devices Meeting (IEDM). IEEE; 2008. pp. 1–4.

\[207\] Singh PN, Kumar A, Debnath C, *et al*. 20mW, 125Msps, 10bit pipelined ADC in 65nm standard digital CMOS process. In: Custom Integrated Circuits Conference (CICC). IEEE; 2007. pp. 189–192.

\[208\] Tan T and Sun Z. CASIA-FingerprintV5; 2010. Available from: [http://biometrics.idealtest.org/](http://biometrics.idealtest.org/).

\[209\] Chiarulli DM, Jennings B, Fang Y, *et al*. A computational primitive for convolution based on coupled oscillator arrays. In: Computer Society Annual Symposium on VLSI (ISVLSI). IEEE; 2015. pp. 125–130.

\[210\] Yogendra K, Fan D, Shim Y, *et al*. Computing with coupled Spin Torque Nano Oscillators. In: Asia and South Pacific Design Automation Conference (ASP-DAC). IEEE; 2016. pp. 312–317.

\[211\] Topaloglu RO. More than Moore technologies for next generation computer design. Springer; 2015. Available from: [https://www.springer.com/gp/book/9781493921621](https://www.springer.com/gp/book/9781493921621).

\[212\] Xu D, Yu N, Huang H, *et al*. Q-Learning based voltage-swing tuning and compensation for 2.5D memory-logic integration. IEEE Design and Test. 2018;35(2):91–99.

\[213\] Xu D, Yu N, Manoj PDS, *et al*. A 2.5-D memory-logic integration with data-pattern-aware memory controller. IEEE Design Test. 2015;32(4):1–10.

\[214\] Manoj PDS, Yu H, Huang H, *et al*. A Q-learning based self-adaptive I/O communication for 2.5D integrated many-core microprocessor and memory. IEEE Trans on Computers. 2016;65(4):1185–1196.

\[215\] Manoj PDS, Yu H and Wang K. 3D many-core microprocessor power management by space-time multiplexing based demand-supply matching. IEEE Trans on Computers. 2015;64(11):3022–3036.

\[216\] Manoj PDS, Yu H, Shang Y, *et al*. Reliable 3-D clock-tree synthesis considering nonlinear capacitive TSV model with electrical-thermal-mechanical coupling. IEEE Trans on Computer-Aided Design of Integrated Circuits and Systems. 2013;32(11):1734–1747.

\[217\] Liauw YY, Zhang Z, Kim W, *et al*. Nonvolatile 3D-FPGA with monolithically stacked RRAM-based configuration memory. In: International Solid-State Circuits Conference (ISSCC). IEEE; 2012. pp. 406–408.

\[218\] Poremba M, Mittal S, Li D, *et al*. DESTINY: A tool for modeling emerging 3D NVM and eDRAM caches. In: IEEE DATE; 2015. pp. 1543–1546.

\[219\] Chen YC, Wang W, Li H, *et al*. Non-volatile 3D stacking RRAM-based FPGA. In: International Conference on Field Programmable Logic and Applications (FPL). IEEE; 2012. pp. 367–372.

\[220\] TaheriNejad N, Manoj PDS, Rathmair M, *et al*. Fully digital write-in scheme for multi-bit memristive storage. In: Conference on Electrical Engineering, Computing Science and Automatic Control; 2016.

\[221\] TaheriNejad N, Manoj PDS and Jantsch A. Memristor’s potential for multi-bit storage and pattern learning. In: European Modeling Symposium on Mathematical Modeling and Computer Simulation; 2015.

\[222\] Ni L, Liu Z, Yu H, *et al*. An energy-efficient digital ReRAM-crossbar based CNN with bitwise parallelism. IEEE Journal on Exploratory Solid-State Computational Devices and Circuits. 2017;3(1):1–10.

\[223\] Yu S, Li Z, Chen PY, *et al*. Binary neural network with 16 Mb RRAM macro chip for classification and online training. In: International Electron Devices Meeting; 2016. pp. 16.2.1–16.2.4.

\[224\] Rastegari M, Ordonez V, Redmon J, *et al*. XNOR-net: ImageNet classification using binary convolutional neural networks. In: European Conference on Computer Vision (ECCV); 2016. pp. 525–542.

\[225\] Ni L, Huang H and Yu H. A memristor network with coupled oscillator and crossbar towards L2-norm based machine learning. In: International Symposium on Nanoscale Architectures (NANOARCH). IEEE; 2016. pp. 179–184.

\[226\] Huang GB, Ramesh M, Berg T, *et al*. Labeled faces in the wild: A database for studying face recognition in unconstrained environments. University of Massachusetts, Amherst; 2007.

\[227\] Vedaldi A and Lenc K. MatConvNet: Convolutional neural networks for Matlab. In: International Conference on Multimedia. ACM; 2015. pp. 689–692.

\[228\] Goll B and Zimmermann H. A 65nm CMOS comparator with modified latch to achieve 7 GHz/1.3 mW at 1.2 V and 700 MHz/47 μW at 0.6 V. In: International Solid-State Circuits Conference (ISSCC). IEEE; 2009. pp. 328–329.

\[229\] Zhang C, Li P, Sun G, *et al*. Optimizing FPGA-based accelerator design for deep convolutional neural networks. In: International Symposium on Field-Programmable Gate Arrays (FPGA). ACM; 2015. pp. 161–170.

\[230\] Chen YH, Krishna T, Emer J, e*t* al. Eyeriss: An energy-efficient reconfigurable accelerator for deep convolutional neural networks. In: International Solid-State Circuits Conference (ISSCC). IEEE; 2016. pp. 262–263.

\[231\] Hinton GE and Salakhutdinov RR. Replicated softmax: An undirected topic model. In:Advances in Neural Information Processing Systems (NIPS); 2009. pp. 1607–1614.

\[232\] LeCunY, Cortes C and Burges CJ. MNIST handwritten digit database; 2010. Available from: [http://yann.lecun.com/exdb/mnist](http://yann.lecun.com/exdb/mnist).

\[233\] Krizhevsky A, Nair V and Hinton G. The CIFAR-10 dataset; 2014. Available from: [http://www.cs.toronto.edu/~kriz/cifar.html](http://www.cs.toronto.edu/~kriz/cifar.html).

\[234\] Chen YH, Krishna T, Emer JS, *et al*. Eyeriss: An energy-efficient reconfigurable accelerator for deep convolutional neural networks. IEEE Journal of Solid-State Circuits. 2017;52(1):127–138.

\[235\] Huang H, Ni L, Wang Y, *et al*. A 3D multi-layer CMOS-RRAM accelerator for neural network. In: International Conference on 3D System Integration (3DIC). IEEE; 2016.

\[236\] Chen PY, Kadetotad D, Xu Z, *et al*. Technology-design co-optimization of resistive cross-point array for accelerating learning algorithms on chip. In: Design, Automation & Test in Europe Conference & Exhibition (DATE). IEEE; 2015. pp. 854–859.

\[237\] Ni L, Huang H, Liu Z, *et al*. Distributed in-memory computing on binary RRAM crossbar. ACM Journal on Emerging Technologies in Computing Systems (JETC). 2017;13(3):36.1–36.18.

\[238\] Franzon P, Rotenberg E, Tuck J, *et al*. Computing in 3D. In: Custom Integrated Circuits Conference (CICC). IEEE; 2015. pp. 1–6.

\[239\] Kim DH, Athikulwongse K and Lim SK. Study of through-silicon-via impact on the 3-D stacked IC layout. IEEE Transactions on Very Large Scale Integration (VLSI) Systems. 2013;21(5):862–874.

\[240\] Krizhevsky A and Hinton G. Learning multiple layers of features from tiny images. University of Toronto; 2009.

\[241\] GPU specs. Available from: [http://www.nvidia.com/object/workstationsolutions.html](http://www.nvidia.com/object/workstationsolutions.html).

\[242\] Chen K, Li S, Muralimanohar N, *et al*. CACTI-3DD: Architecture-level modeling for 3D die-stacked DRAM main memory. In: Proceedings of the Conference on Design, Automation and Test in Europe. IEEE; 2012. pp. 33–38.

\[243\] Xue J, Li J and Gong Y. Restructuring of deep neural network acoustic models with singular value decomposition. In: INTERSPEECH; 2013. pp. 2365– 2369.

\[244\] CPU Xeon-X5690specs. Accessed: 2017-03-30. Available from: [http://ark.intel.com/products/52576/Intel-Xeon-Processor-X5690-12M-Cache-3\_46-GHz-6\_40-GTs-Intel-QPI](http://ark.intel.com/products/52576/Intel-Xeon-Processor-X5690-12M-Cache-3_46-GHz-6_40-GTs-Intel-QPI).

\[245\] Han S, Mao H and Dally WJ. Deep compression: Compressing deep neural networks with pruning, trained quantization and Huffman coding. arXiv preprint arXiv:151000149. 2015.

\[246\] He K, Zhang X, Ren S, *et al*. Deep residual learning for image recognition. In: IEEE Conference on Computer Vision and Pattern Recognition; 2016. pp. 770–778.

\[247\] He K, Zhang X and Ren S. Identity mappings in deep residual networks. In: European Conference on Computer Vision; 2016. pp. 630–645.

\[248\] Guo K, Sui L, Qiu J, *et al*. From model to FPGA: Software-hardware codesign for efficient neural network acceleration. In: IEEE Symposium on Hot Chips; 2016. pp. 1–27.

\[249\] Wang Y, Li X, Yu H, *et al*. Optimizing Boolean embedding matrix for compressive sensing in RRAM crossbar. In: IEEE/ACM International Symposium on Low Power Electronics and Design. IEEE; 2015. pp. 13–18.

\[250\] Chen T, Du Z, Sun N, *et al*. Diannao: A small-footprint high-throughput accelerator for ubiquitous machine-learning. ACM SIGPLAN Notices. 2014;49(4):269–284.

\[251\] Wen W, Wu C, Wang Y, *et al*. Learning structured sparsity in deep neural networks. In: Advances in Neural Information Processing Systems; 2016. pp. 2074–2082.

\[252\] Hashemi S, Anthony N, Tann H, *et al*. Understanding the impact of precision quantization on the accuracy and energy of neural networks. In: Design, Automation and Test in Europe; 2017. pp. 1474–1479.

\[253\] Dettmers T. 8-bit approximations for parallelism in deep learning. arXiv preprint arXiv:151104561. 2015.

\[254\] Hubara I, Courbariaux M, Soudry D, El-Yaniv R and Bengio Y. Quantized neural networks: Training neural networks with low precision weights and activations. Journal of Machine Learning Research. 2017;18(1): 6869–6898.

\[255\] Jacob B, Kligys S, Chen B, *et al*. Quantization and training of neural networks for efficient integer-arithmetic-only inference. In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition; 2018. pp. 2704–2713.

\[256\] Zhou S, Wu Y, Ni Z, *et al*. DoReFa-Net: Training low bitwidth convolutional neural networks with low bitwidth gradients. arXiv preprint arXiv:160606160. 2016.

\[257\] Bengio Y, Léonard N and Courville A. Estimating or propagating gradients through stochastic neurons for conditional computation. arXiv preprint arXiv:13083432. 2013.

\[258\] Chi P, Li S, Xu C, *et al*. PRIME: A novel processing-in-memory architecture for neural network computation in ReRAM-based main memory. In: ACM/SIGARCH Computer Architecture News. vol. 44; 2016. pp. 27–39.

\[259\] Albericio J, Judd P, Hetherington T, *et al*. Cnvlutin: Ineffectual-neuron-free deep neural network computing. In: ACM/SIGARCH Computer Architecture News. vol. 44; 2016. pp. 1–13.

\[260\] Fan D and Angizi S. Energy-efficient in-memory binary deep neural network accelerator with dual-mode SOT-MRAM. In: IEEE International Conference on Computer Design. IEEE; 2017. pp. 609–612.

\[261\] Wang Y, Ni L, Chang CH, *et al*. DW-AES: A domain-wall nanowire-based AES for high throughput and energy-efficient data encryption in nonvolatile memory. IEEE Transactions on Information Forensics and Security. 2016;11(11):2426–2440.

\[262\] Sharma A, Jackson T, Schulaker M, *et al*. High performance, integrated 1T1R oxide-based oscillator: Stack engineering for low-power operation in neural network applications. In: IEEE Symposium on VLSI Technology; 2015. pp. T186–T187.

\[263\] Chang SC, Kani N, Manipatruni S, *et al*. Scaling limits on all-spin logic. IEEE Transactions on Magnetics. 2016;52(7):1–4.

\[264\] Huang H, Ni L, Wang K, *et al*. A highly parallel and energy efficient three-dimensional multilayer CMOS-RRAM accelerator for tensorized neural network. IEEE Transactions on Nanotechnology. 2018;17(4):645–656.

\[265\] Deng J, Dong W, Socher R, *et al*. Imagenet: A large-scale hierarchical image database. In: IEEE Conference on Computer Vision and Pattern Recognition; 2009. pp. 248–255.

\[266\] Zhu C, Han S, Mao H, *et al*. Trained ternary quantization. arXiv preprint arXiv:161201064. 2016.

\[267\] Nair V and Hinton GE. Rectified linear units improve restricted Boltzmann machines. In: International Conference on Machine Learning; 2010. pp. 807–814.

\[268\] Xu C, Niu D, Muralimanohar N, *et al*. Overcoming the challenges of crossbar resistive memory architectures. In: IEEE Symposium on High Performance Computer Architecture; 2015. pp. 476–488.

\[269\] Kinga D and Adam JB. A method for stochastic optimization. In: International Conference on Learning Representations. vol. 5; 2015.

\[270\] Li C, Hu M, Li Y, *et al*. Analogue signal and image processing with large memristor crossbars. Nature Electronics. 2018;1(1):52.

\[271\] Lee PC, Lin JY and Hsieh CC. A 0.4 V 1.94 fJ/conversion-step 10 bit 750 kS/s SAR ADC with input-range-adaptive switching. IEEE Transactions on Circuits and Systems I: Regular Papers. 2016;63(12):2149–2157.

\[272\] Stathopoulos S, Khiat A, Trapatseli M, *et al*. Multibit memory operation of metal-oxide bi-layer memristors. Scientific reports. 2017;7(1):17532.

\[273\] Ma Y, Cao Y, Vrudhula S, *et al*. Performance modeling for CNN inference accelerators on FPGA. IEEE Transactions on Computer-Aided Design of Integrated Circuits and Systems. 2019.

\[274\] Kaplan R, Yavits L and Ginosar R. PRINS: Processing-in-storage acceleration of machine learning. IEEE Transactions on Nanotechnology. 2018;17(5):889–896.

\[275\] Song L, Qian X, Li H, *et al*. Pipelayer: A pipelined ReRAM-based accelerator for deep learning. In: IEEE International Symposium on High Performance Computer Architecture; 2017. pp. 541–552.

\[276\] Mellempudi N, Kundu A, Mudigere D, *et al*. Ternary neural networks with fine-grained quantization. arXiv preprint arXiv:170501462. 2017.

\[277\] Zhou A, Yao A, Guo Y, *et al*. Incremental network quantization: Towards lossless CNNS with low-precision weights. arXiv preprint arXiv:170203044. 2017.

\[278\] Li F, Zhang B and Liu B. Ternary weight networks. arXiv preprint arXiv:160504711. 2016.

\[279\] Dong X, Xu C, Jouppi N, *et al*. NVSim: A circuit-level performance, energy, and area model for emerging non-volatile memory. In: Emerging Memory Technologies; 2014. pp. 15–50.

\[280\] Ren F and Markovic D. A configurable 12-to-237KS/s 12.8 mW sparse-approximation engine for mobile ExG data aggregation. In: Proc. 2015 IEEE Int. Solid-State Circuits Conf., San Francisco, CA; 2015. pp. 1–3.

\[281\] Zhang Z, Jung T, Makeig S and Rao BD. Compressed sensing of EEG for wireless telemonitoring with low energy consumption and inexpensive hardware. IEEE Trans Biomed Eng. 2013;60(1):221–224.

\[282\] Dixon AMR, Allstot EG, Gangopadhyay D and Allstot DJ. Compressed sensing system considerations for ECG and EMG wireless biosensors. IEEETrans Biomed Circuits Syst. 2012;6(2):156–166.

\[283\] Suo Y, Zhang J, Xiong T, Chin PS, Etienne-Cummings R and Tran TD. Energy-efficient multi-mode compressed sensing system for implantable neural recordings. IEEE Trans Biomed Circuits Syst. 2014;8(5): 648–659.

\[284\] Donoho DL. Compressed sensing. IEEE Trans Inf Theory. 2006;52(4): 1289–1306.

\[285\] Pant JK and Krishnan S. Compressive sensing of electrocardiogram signals by promoting sparsity on the second-order difference and by using dictionary learning. IEEE Trans Biomed Circuits Syst. 2014;8(2):293–302.

\[286\] Ren F and Markovic D. A configurable 12-237 kS/s 12.8 mW sparse-approximation engine for mobile data aggregation of compressively sampled physiological signals. IEEE J Solid-State Circuits. 2015;PP(99):1–11.

\[287\] Calderbank R and Jafarpour S. Reed Muller sensing matrices and the LASSO. In: Carlet C, Pott A, editors. Sequences and Their Applications - SETA 2010. Berlin, Germany: Springer Berlin Heidelberg; 2010. pp. 442–463.

\[288\] Jafarpour S. Deterministic compressed sensing. Dept. Comput. Sci., Princeton Univ., Princeton, NJ; 2011.

\[289\] Hegde C, Sankaranarayanan AC, Yin W and Baraniuk RG. NuMax: A convex approach for learning near-isometric linear embeddings. IEEE Trans Signal Process. 2015;63(22):6109–6121.

\[290\] Chen F, Chandrakasan AP and Stojanovic VM. Design and analysis of a hardware-efficient compressed sensing architecture for data compression in wireless sensors. IEEE J Solid-State Circuits. 2012;47(3): 744–756.

\[291\] Kim S and Choi YK. Resistive switching of aluminum oxide for flexible memory. Appl Phys Lett. 2008;92(22):223508.1–223508.3.

\[292\] Baraniuk R, Davenport M, DeVore R and Wakin M. A simple proof of the restricted isometry property for random matrices. Constr Approx. 2008;28(3):253–263.

\[293\] Lee HY, Chen PS, Wu TY, *et al.* Low power and high speed bipolar switching with a thin reactive Ti buffer layer in robust HfO2 based RRAM. In: IEEE Electron Devices Meeting; 2008.

\[294\] Sheu S, Chiang P, Lin W, *et al.* A 5ns fast write multi-level non-volatile 1 K bits RRAM memory with advance write scheme. In: Proc. 2009 Symp. VLSI Circuits, Kyoto, Japan; 2009. pp. 82–83.

\[295\] Costa L and Oliveira P. Evolutionary algorithms approach to the solution of mixed integer non-linear programming problems. Comput Chem Eng. 2001;25(2):257–266.

\[296\] ApS M. The MOSEK optimization toolbox for MATLAB manual. Version 7.1 (Revision 28); 2015. Available from: [http://docs.mosek.com/7.1/toolbox/index.html](http://docs.mosek.com/7.1/toolbox/index.html).

\[297\] Sahinidis N. BARON: A general purpose global optimization software package. J Global Optim. 1996;8(2):201–205.

\[298\] Huang GB, Ramesh M, Berg T and Learned-Miller E. Labeled faces in the wild: A database for studying face recognition in unconstrained environments. Univ. of Massachusetts, Amherst, MA; 2007. 07–49.

\[299\] Moody GB and Mark RG. The impact of the MIT-BIH arrhythmia database. IEEE Eng Med Biol. 2001;20(3):45–50. Available from: [http://www.physionet.org/physiobank/database/mitdb/](http://www.physionet.org/physiobank/database/mitdb/).

\[300\] Wilton SJ and Jouppi NP. CACTI: An enhanced cache access and cycle time model. IEEE J Solid-State Circuits. 1996;31(5):677–688. Available from: [http://www.hpl.hp.com/research/cacti/](http://www.hpl.hp.com/research/cacti/).

\[301\] ChenYS, Lee HY, Chen PS, *et al.* Highly scalable hafnium oxide memory with improvements of resistive distribution and read disturb immunity. In: Proc. 2009 IEEE Int. Electron Devices Meeting, Baltimore, MD; 2009. pp. 1–4.

\[302\] Wong HP, Lee H, Yu S, *et al*. Metal-oxide RRAM. Proc IEEE. 2012;100(6):1951–1970.

\[303\] Bavikadi S, Sutradhar PR, Khasawneh KN, Ganguly A and Sai Manoj PD. A review of in-memory computing architectures for machine learning applications. In: ACM Great Lakes Symposium on VLSI (GLSVLSI); 2020.

## Index

accuracy analysis 182

accuracy under approximation 184–185

accuracy under device variation 182–183

peak accuracy comparison 182

Alpha Go 20

analog-to-digital converter (ADC) 30, 55, 99, 168

AND gate 70–71

artificial neural network (ANN) 20, 216

auto-encoder technique 97

auxiliary processing unit (APU) 39

backpropagation technique 81

BARON 202

batch normalization (BN) 168

Bernoulli matrix 190

big-data analytics 4

bijective function 145

binarization (Binrz) 90

binarized neural networks (BNNs) 132, 167

binary convolutional (BinConv) layers 132

binary convolutional neural network (BCNN) 16, 39, 88

accelerator 38

bitwise batch normalization 88–90

bitwise CNN model overview 90–93

bitwise convolution 88

bitwise pooling and activation functions 90

inference acceleration on 1S1R array

mapping batch normalization, pooling and binarization 122

mapping unsigned bitwise convolution 121–122

inference acceleration on passive array

experimental settings 132

mapping bitwise batch normalization 118–120

mapping bitwise convolution 117–118

mapping bitwise pooling and binarization 120

performance evaluation 133

summary of mapping bitwise CNN 120–121

binary weighted neural network (BWNN) 36

biomedical wireless circuits 189

bit-width configuration analysis 151–152, 158

bitwise XNOR operation 88

central processing unit (CPU) 19, 168, 216

Cholesky decomposition 83

CMOS

layer accelerator 145

layer implementation for decoding and incremental least-squares 143–145

CMOS-ASIC 216

CMP-PIM 40

compressive sensing

Boolean embedding circuit

CMOS-based 194–195

problem formulation 197

ReRAM crossbar-based 195–196

IH algorithm

orthogonal rotation 198

overall optimization algorithm 199–200

quantization 199

and isometric distortion 192

numerical results

experiment setup 203–204

hardware performance evaluation 210–213

IH algorithm on high-D ECG signals 204–207

row generation algorithm on low-D image patches 207–210

optimized near-isometric embedding 193–194

row generation algorithm

convex relaxation of orthogonal constraint 201–202

elimination of norm equality constraint 200–201

overall optimization algorithm 202–203

computational unit-cum-memory 74–75

conventional communication protocol 110

convolutional neural network (CNN) 20, 87–88, 117, 167

binary 39

bitwise CNN 138

bitwise-parallelized 90–91

conventional CNN 138

direct-truncated 92–93

traditional direct mapping of 88

cores, pPIM 36

coupled ReRAM oscillator network 106–108

for L2-norm calculation 106–107

performance evaluation 107–108

data quantization 142

data storage

multi-threshold resistance for 62–63

ReRAM 61

deep convolutional neural networks (DCNNs) 87

binary convolutional neural network 88

convolutional neural network 87–88

deep learning for multilayer neural network 87

deep neural network (DNN) 27

with quantization 168

basics of 168–170

quantized activation function and pooling 172–173

quantized BN 172

quantized convolution and residual block 170–172

quantized deep neural network overview 173

training strategy 173–174

degree of- match (DOM) 125

density matrix 98

diffusive-type ReRAM device 52–54

digitalized ReRAM crossbar 55–57

digital processing unit (DPU) 39

digital-to-analog converter (DAC) 30, 55, 168

digitized computing-in-memory fashion 28

Discrete Fourier transform (DFT) analysis 60

distributed crossbar in-memory architecture

communication protocol and control bus 110–111

memory-computing integration 109–110

distributed ReRAM-crossbar in-memory architecture 109

DrAcc 36

drift-type ReRAM device 45–52

DRISA 36

dynamic random access memory (DRAM) 5, 7–9, 19

encoding 67, 102, 116–117, 143

nonuniform 69–70

uniform input 68–69

energy-delay-product (EDP) 105, 151

energy efficiency 141

error correction code (ECC) techniques 34

feature extraction 82

first-come-first-serve (FCFS) 111

flash memory

NAND 10

NOR 10

floating gate (FG) transistors 9

gate recurrent unit (GRU) 27

Gaussian distribution 133, 140, 160, 183

giga operations per second (GOPS) 137

graphics processing unit (GPU) 19, 127, 168

Group 36

Hadoop 3, 4

hard disk drive (HDD) 5

high-resistance state (HRS) 21, 196

ImageNet 167

IMCE 39–40

information technology 3

in-memory computing (IMC) architectures 3, 25

analog and digitized fashion of 27–28

analog MAC 29–30

analysis of 40–43

bitcell and array design of analog 31–32

cascading macros 30–31

challenges of analog 33–34

digitized IMC 34

DRAM-based 34–37

emerging memory technologies 40

ideal logic 11

at memory-block level 13

at memory-cell level 12

NAND-flash-based 37

nonvolatile 11–13

operating principles of 26–27

peripheral circuitry of analog 32–33

ReRAM-based 38–39

SOT-MRAM-based 39–40

SRAM-based 37

STT-MRAM-based 39

trade-offs of analog devices 34

traditional and 40

XIMA 15

in-pair control bus 109

internet-of-things (IoT) 3

ISAAC 38

iterative heuristic (IH) algorithm 207

on high-D ECG signals 204

orthogonal rotation 198

overall optimization algorithm 199–200

quantization 199

iterative row generation algorithm 208

Joglekar window function 49–50

least-square method 16

least squares (LS) solution 81

logic-in-memory architecture 11

long short-term memory (LSTM) 27

look-up table (LUT) 114

low-dimensional embedding 189

low-resistance state (LRS) 21

machine learning (ML) algorithms 79

adoption of 3

BCNN-based inference acceleration on passive array 117

deep convolutional neural network

binary convolutional neural network 88

convolutional neural network 87–88

deep learning for multilayer neural network 87

experimental evaluation of 126, 151

IMC architectures: *see* in-memory computing (IMC) architectures

L2-norm-gradient-based learning

direct-gradient-based L2-norm optimization 86

and inference acceleration 123

multilayer neural network 84–86

single-layer feedforward network

feature extraction 82

incremental LS solver-based learning 83–84

neural network-based learning 82–83

SLFN-based learning and inference acceleration 115

support vector machines 79–80

tensorized neural network

tensor-train-based neural network 94–96

tensor-train decomposition and compression 93–94

training TNN 96–98

XOR operation for 101–102

magnetic tunneling junction (MTJ) 22

mapping

bitwise batch normalization 118–120

bitwise CNN 120–121

bitwise convolution 117–118

bitwise pooling and binarization 120

matrix–vector multiplication 124

on multilayer architecture 145–149

MapReduce 3

matrix–vector multiplication 142–143

memory-computing integration 109–110

memory wall 3–6, 19

memristor device 61

mixed-integer nonlinear programming (MINLP) 200

mode size 93

modified alternating LS (MALS) method 93

Moore’s law 4

MOSEK 202

MOSFET transistor 9

most significant bit (MSB) 68

MRAM-DIMA 39

MRIMA 39

multilayer perceptron (MLP) 27

multilevel sense amplifiers (MSLAs) 39

multiplication-and-accumulation (MAC) 27, 192

nanoscale limitations 10

neural network (NN) 82–83

backpropagation training for 86

binary convolutional 88

biological 19

convolutional 87–88

deep learning for multilayer 87

energy-efficient tensor-compressed 160–162

layer-wise training of 97

multilayer 84–86

single-layer 81

tensor-train-based 94–96

neuromorphic computing 19

devices

phase change memory 23–24

resistive random-access memory 21–22

spin-transfer-torque magnetic random-access memory 22

NVM devices

linear/symmetric tuning 24

long time retention 25

low stochastic tunneling 25

multilevel resistance state 24–25

scalability and stackability 24

system on chip 20

non-distributed in-memory computing 103

nonuniform encoding 69–70

nonvolatile memories (NVMs) 4–5, 20, 167

characteristics of 24–25

flash 9–10

NuMax 190

Nvidia GeForce GTX 970 151

Nyquist sampling theorem 189

one-transistor-one-ReRAM (1T1R) 57

Opamp and feedback resistor 29

optical disk drive (ODD) 5

OR gate 70

orthogonal matching pursuit (OMP) technique 82

orthogonal transformation matrix 199

parallel digitizing 100–101, 115–116, 143

passive ReRAM array 57

performance analysis 159–160, 185

energy and area 185

throughput and efficiency 185–187

performance evaluation 156

phase-change memory (PCM) 20, 23–24

pipelayer 38

pooling 90, 172–173

power consumption 140–141

powerwall 3–6

principal component analysis (PCA) 127

processing-in-memory (PIM) 25

programmable PIM (pPIM) 36

programmable read-only memory (PROM) 5

pseudo-random number generator (PRNG) 195

puffer transformation 189

pulse-widthmodulated (PWM) 39

QBN 172

QConv 171, 180

QPooling 173, 180

QReLUs 172–173, 180

quantization 199

Quantized BN 172

*see also* QBN

quantum dynamics 98

quantum tunneling 9

read operation 7–8

readout circuit 74

readout method 64–65

reconstructed signal-to-noise ratio (RSNR) 191

rectified linear unit (ReLU) layers 168

recurrent neural network (RNN) 20

Reed–Muller code 189

refresh 8

residual network (ResNet) 167

accuracy analysis 182

accuracy under approximation 184–185

accuracy under device variation 182–183

peak accuracy comparison 182

deep neural network with quantization

basics of 168–170

quantized activation function and pooling 172–173

quantized BN 172

quantized convolution and residual block 170–172

quantized deep neural network overview 173

training strategy 173–174

device simulations 181

experiment settings 180

performance analysis 185

energy and area 185

throughput and efficiency 185–187

on ReRAM crossbar 177

mapping strategy 177–178

overall architecture 178–180

resistive random access memory (ReRAM) 3, 19, 83, 99, 167, 190, 215

3D XIMA

3D multilayer CMOS-ReRAM architecture 112–114

3D single-layer CMOS-ReRAM architecture 111–112

area and energy consumption of 57

based inner-product operation 102

based oscillator 59–60

characteristics of 45

coupled oscillator network 106–108

crossbar 174–177

mapping strategy 177–178

overall architecture 178–180

crossbar network 99–105

mapping matrix–vector multiplication 124

crossbar structure 54

digitalized 55–57

direct-connected 57–58

one-selector-one 59

one-transistor-one 58–59

traditional analog 55

customized DAC and ADC circuits 176

data storage 61

device simulation 138–140

diffusive-type 52–54

distributed crossbar in-memory architecture

communication protocol and control bus 110–111

memory-computing integration 109–110

drift-type 45–52

encoding and three-bit storage 67

exploration of the memristance range 67–68

nonuniform encoding 69–70

uniform input encoding 68–69

in-memory computing architecture 176–177

layer accelerator 145

logic functional units

AND gate 70–71

OR gate 70

for logic operations

based circuits 73–74

as computational unit-cum-memory 74–75

simulation settings 72–73

mathematic model of 22

multi-threshold resistance for data storage 62–63

and nonlinear effects for dynamic model 47

nonvolatile 13

one-selector-one 15

one-transistor-one 15

operating principle of 46

oscillator network

mapping L2-norm calculation on coupled 124–125

spiking neural networks on 216

validation 65–67

write and read 63

ResNet with 50 layers (ResNet-50) 168

restricted isometry property (RIP) 192

row generation algorithm

convex relaxation of orthogonal constraint 201–202

elimination of norm equality constraint 200–201

on low-D image patches 207

overall optimization algorithm 202–203

scalability analysis 151

SCOPE 36, 40, 42

Semiconductor memory

memory technologies 5–10

nanoscale limitations 10

Sigmoid function 83, 97, 144

single-layer feedforward network (SLFN) 80–81

feature extraction 82

incremental LS solver-based learning 83–84

neural network-based learning 82–83

single-layer feedforward neural network (SLFN) 16

learning and inference acceleration

adding and shifting for inner-product result 117

encoding 116–117

experiment settings 127

parallel digitizing 115–116

performance evaluation 127–129

XOR 116

learning and inference procedures of 216

on-chip design for 141–142

SPICE model 45

spike timing-dependent plasticity (STDP) 14

spiking neural network (SNN) 20

spin-torque-transfer-magnetic random-access memory (STT-MRAM) 20, 22

static random access memories (SRAMs) 5–7, 21

support vector decomposition (SVD) 98, 155

support vector machine (SVM) 16, 79–80, 151

based machine learning 79–80

binary classifier 79

fingerprint recognition by multiple 80

tensorized neural network (TNN) 16, 112, 141

on 3D CMOS-ReRAM architecture 149–150

distributed on-chip design on 3D single-layer architecture 160–163

layer-wise training of 93

on-chip design for 145

on-chip design on 3D multilayer architecture 155–160

tensor-train-based neural network 94–96

tensor-train decomposition and compression 93–94

training 96–98

tensors

train-based neural network 94–96

train decomposition and compression 93–94

ternary weighted neural network (TWNN) 36

three-dimensional (3D) CMOS-ReRAM architecture 215

three-dimensional (3D) multilayer CMOS-ReRAM architecture 112–114

three-dimensional (3D) single-layer CMOS-ReRAM architecture 111–112

three-dimensional (3D) XIMA

3D multilayer CMOS-ReRAM architecture 112–114

3D single-layer CMOS-ReRAM architecture 111–112

machine learning algorithms 141

traditional analog ReRAM crossbar 55

trans-impedance amplifier (TIA) 29

transition metal oxides (TMOs) 54

two-dimensional (2D) arrays 93

uniform input encoding 68–69

validation 65–67

Von Neumann architecture 20

write-in method 64

XNOR-ReRAM 38–39

XOR 101–102, 116, 143