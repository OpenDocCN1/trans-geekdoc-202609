![Machine Learning with SAP – Cover](common/cover.jpg)

Laboni Bhowmik, Avijit Dhar, Ranajay Mukherjee

# Machine Learning with SAP®

Models and Applications

![Logo Rheinwerk Publishing](common/logo_sap.png)

# Imprint

This e-book is a publication many contributed to, specifically:

Editor   Will Jobst  
Acquisitions Editor   Hareem Shafi  
Copyeditor   Yvette Chin  
Cover Design   Graham Geary  
Photo Credit    iStockphoto.com/1031510982/© RelaxFoto.de  
Production E-Book   Graham Geary  
Typesetting E-Book   III-satz, Husby (Germany)  

We hope that you liked this e-book. Please share your feedback with us and read the [Service Pages](#service.html) to find out how to contact us.

  
The Library of Congress has cataloged the printed edition as follows:  
Names: Bhowmik, Laboni, author. | Dhar, Avijit, author. | Mukherjee,  
Ranajay, author.  
Title: Machine learning with SAP / Laboni Bhowmik, Avijit Dhar, Ranajay  
Mukherjee.  
Description: 1st edition. | Bonn ; Boston : Rheinwerk Publishing, 2020. |  
Includes index.  
Identifiers: LCCN 2020023824 (print) | LCCN 2020023825 (ebook) | ISBN  
9781493219261 (hardcover) | ISBN 9781493219278 (ebook)  
Subjects: LCSH: Machine learning. | SAP HANA (Electronic resource)  
Classification: LCC Q325.5 .B55 2020 (print) | LCC Q325.5 (ebook) | DDC  
006.3/1--dc23  
LC record available at https://lccn.loc.gov/2020023824  
LC ebook record available at https://lccn.loc.gov/2020023825

ISBN 978-1-4932-1926-1 (print)  
ISBN 978-1-4932-1927-8 (e-book)  
ISBN 978-1-4932-1928-5 (print and e-book)

  
© 2021 by Rheinwerk Publishing Inc., Boston (MA)  
1st edition 2021

# Dear Reader,

What can’t machine learning and AI accomplish? If you’re a data science wonk, you can think of a dozen answers to this question. Anything that requires intuition, emotional intelligence, or a creative spark is as safe as a job can be in this age of information revolution.

One industry that’s automation resistant is publishing.

Sure, if fed enough SAP PRESS books, a machine learning model could spit out a facsimile of our style, but it wouldn’t capture the expertise of our authors. Authors like Machine Learning with SAP’s Laboni Bhowmik, Avijit Dhar, and Ranajay Mukherjee. Theirs is a careful process of synthesis—taking in the endless amounts of information about machine learning, SAP HANA, SAP Data Intelligence, and more. Researching and understanding. Drafting and editing. Finally, transmitting that information to you. This is a tailored experience, created with you in mind. And now, we’ll let this book speak for itself!

What did you think about Machine Learning with SAP: Models and Applications? Your comments and suggestions are the most useful tools to help us make our books the best they can be. Please feel free to contact me and share any praise or criticism you may have.

Thank you for purchasing a book from SAP PRESS!

Will Jobst  
Editor, SAP PRESS

[willj@rheinwerk-publishing.com](mailto:meaganw@rheinwerk-publishing.com)  
[www.sap-press.com](http://www.sap-press.com)  
Rheinwerk Publishing • Boston, MA

# Notes on Usage

This e-book is protected by copyright. By purchasing this e-book, you have agreed to accept and adhere to the copyrights. You are entitled to use this e-book for personal purposes. You may print and copy it, too, but also only for personal use. Sharing an electronic or printed copy with others, however, is not permitted, neither as a whole nor in parts. Of course, making them available on the Internet or in a company network is illegal as well.

For detailed and legally binding usage conditions, please refer to the section [Legal Notes](#legal_notes.html).

This e-book copy contains a digital watermark, a signature that indicates which person may use this copy:

  

# Notes on the Screen Presentation

You are reading this e-book in a file format (EPUB or Mobi) that makes the book content adaptable to the display options of your reading device and to your personal needs. That’s a great thing; but unfortunately not every device displays the content in the same way and the rendering of features such as pictures and tables or hyphenation can lead to difficulties. This e-book was optimized for the presentation on as many common reading devices as possible.

If you want to zoom in on a figure (especially in iBooks on the iPad), tap the respective figure once. By tapping once again, you return to the previous screen. You can find more recommendations on the customization of the screen layout on the [Service Pages](#service.html).

# Table of Contents

## [Dear Reader](#dear_reader.html#extra-leser)

## [Notes on Usage](#notes.html#extra-hinweise)

## [Table of Contents](#toc.html#extra-toc)

## [Preface](#00_001.html#h0.1)

# [Part I   Introduction](#I_001.html#hI)

# [1   Machine Learning and Intelligent Enterprise](#01_001.html#h1)

## [1.1   What Is Machine Learning?](#01_001.html#h1.1)

## [1.2   Transition from the Digital Era to the Intelligent Era](#01_002.html#h1.2)

## [1.3   Intelligent Enterprise Use Cases](#01_003.html#h1.3)

### [1.3.1   Intelligent Invoice Matching](#01_003.html#h1.3.1)

### [1.3.2   Smart Recruiting](#01_003.html#h1.3.2)

### [1.3.3   Service Ticket Intelligence](#01_003.html#h1.3.3)

### [1.3.4   Product Similarity Matching](#01_003.html#h1.3.4)

### [1.3.5   Brand Impact](#01_003.html#h1.3.5)

### [1.3.6   Robotic Process Automation](#01_003.html#h1.3.6)

### [1.3.7   Virtual Assistance](#01_003.html#h1.3.7)

## [1.4   SAP’s Intelligent Enterprise Strategy](#01_004.html#h1.4)

### [1.4.1   Intelligent Suite](#01_004.html#h1.4.1)

### [1.4.2   Digital Platform](#01_004.html#h1.4.2)

### [1.4.3   Intelligent Technologies](#01_004.html#h1.4.3)

## [1.5   SAP’s Machine Learning Technologies and Applications](#01_005.html#h1.5)

### [1.5.1   Embedded Machine Learning Applications](#01_005.html#h1.5.1)

### [1.5.2   SAP Intelligent Robotic Process Automation](#01_005.html#h1.5.2)

### [1.5.3   SAP Conversational Artificial Intelligence](#01_005.html#h1.5.3)

### [1.5.4   SAP Data Intelligence](#01_005.html#h1.5.4)

### [1.5.5   Embedded Machine Learning within SAP HANA](#01_005.html#h1.5.5)

## [1.6   Summary](#01_006.html#h1.6)

# [2   Machine Learning Fundamentals](#02_001.html#h2)

## [2.1   Basic Probability Concepts](#02_001.html#h2.1)

### [2.1.1   What is Probability?](#02_001.html#h2.1.1)

### [2.1.2   Conditional Probability and Independence](#02_001.html#h2.1.2)

### [2.1.3   Random Variables](#02_001.html#h2.1.3)

### [2.1.4   Density and Distribution Function](#02_001.html#h2.1.4)

### [2.1.5   Expectation](#02_001.html#h2.1.5)

### [2.1.6   Variance and Standard Deviation](#02_001.html#h2.1.6)

### [2.1.7   Covariance and Correlation](#02_001.html#h2.1.7)

## [2.2   Basic Machine Learning Concepts](#02_002.html#h2.2)

### [2.2.1   Different Types of Machine Learning Scenarios](#02_002.html#h2.2.1)

### [2.2.2   Types of Learning](#02_002.html#h2.2.2)

## [2.3   Machine Learning Algorithms](#02_003.html#h2.3)

### [2.3.1   Linear Regression Analysis](#02_003.html#h2.3.1)

### [2.3.2   Classification](#02_003.html#h2.3.2)

### [2.3.3   Cluster Analysis](#02_003.html#h2.3.3)

### [2.3.4   Other Machine Learning Techniques](#02_003.html#h2.3.4)

## [2.4   Summary](#02_004.html#h2.4)

# [3   Implementation Lifecycle](#03_001.html#h3)

## [3.1   Understanding the Implementation Lifecycle](#03_001.html#h3.1)

### [3.1.1   Cross Industry Standard Process for Data Mining](#03_001.html#h3.1.1)

### [3.1.2   Define, Measure, Analyze, Improve, Control](#03_001.html#h3.1.2)

### [3.1.3   Analytics Solutions Unified Method for Data Mining/Predictive Analytics](#03_001.html#h3.1.3)

### [3.1.4   Key Components in a Machine Learning Project Lifecycle](#03_001.html#h3.1.4)

## [3.2   Knowing the Business](#03_002.html#h3.2)

## [3.3   Understanding and Exploring Data](#03_003.html#h3.3)

### [3.3.1   Checking Data Quality](#03_003.html#h3.3.1)

### [3.3.2   Checking Summary Statistics](#03_003.html#h3.3.2)

### [3.3.3   Visualizing Data](#03_003.html#h3.3.3)

## [3.4   Preparing Data](#03_004.html#h3.4)

### [3.4.1   Data Conversion](#03_004.html#h3.4.1)

### [3.4.2   Dimensionality Reduction](#03_004.html#h3.4.2)

### [3.4.3   Variable Transformation](#03_004.html#h3.4.3)

## [3.5   Developing the Model](#03_005.html#h3.5)

## [3.6   Evaluating and Fine-Tuning Model](#03_006.html#h3.6)

### [3.6.1   Model Overfitting](#03_006.html#h3.6.1)

### [3.6.2   Model Performance](#03_006.html#h3.6.2)

### [3.6.3   Model Fine-Tuning](#03_006.html#h3.6.3)

### [3.6.4   Diagnostic Checks](#03_006.html#h3.6.4)

### [3.6.5   Validation Set Approach](#03_006.html#h3.6.5)

### [3.6.6   K-Fold Cross Validation](#03_006.html#h3.6.6)

## [3.7   Deploying the Model](#03_007.html#h3.7)

## [3.8   Summary](#03_008.html#h3.8)

# [4   Machine Learning on SAP HANA](#04_001.html#h4)

## [4.1   SAP HANA Machine Learning Components](#04_001.html#h4.1)

### [4.1.1   SAP HANA Predictive Analysis Library](#04_001.html#h4.1.1)

### [4.1.2   SAP HANA Automated Predictive Library](#04_001.html#h4.1.2)

### [4.1.3   SAP HANA Extended Machine Learning Library](#04_001.html#h4.1.3)

### [4.1.4   R Integration](#04_001.html#h4.1.4)

## [4.2   Summary](#04_002.html#h4.2)

# [5   Machine Learning with SAP Data Intelligence](#05_001.html#h5)

## [5.1   Data Science Project Lifecycle](#05_001.html#h5.1)

## [5.2   Managing the Data Science Project Lifecycle](#05_002.html#h5.2)

## [5.3   SAP Data Intelligence](#05_003.html#h5.3)

### [5.3.1   SAP Data Intelligence Versus SAP Data Hub](#05_003.html#h5.3.1)

### [5.3.2   Architecture](#05_003.html#h5.3.2)

### [5.3.3   Values of SAP Data Intelligence](#05_003.html#h5.3.3)

## [5.4   Key Capabilities](#05_004.html#h5.4)

### [5.4.1   Metadata and Governance](#05_004.html#h5.4.1)

### [5.4.2   Machine Learning Scenario Manager](#05_004.html#h5.4.2)

### [5.4.3   Machine Learning Data Manager](#05_004.html#h5.4.3)

### [5.4.4   AutoML](#05_004.html#h5.4.4)

### [5.4.5   Machine Learning Tracking](#05_004.html#h5.4.5)

### [5.4.6   SAP Data Intelligence Modeler and Built-in Operators](#05_004.html#h5.4.6)

## [5.5   Migrating to SAP Data Intelligence from SAP Data Hub](#05_005.html#h5.5)

## [5.6   Summary](#05_006.html#h5.6)

# [Part II   Building Machine Learning Applications](#II_001.html#hII)

# [6   SAP HANA Predictive Analysis Library](#06_001.html#h6)

## [6.1   SAP HANA Predictive Analysis Library](#06_001.html#h6.1)

### [6.1.1   Prerequisites and Installation](#06_001.html#h6.1.1)

### [6.1.2   SAP HANA PAL Procedures](#06_001.html#h6.1.2)

### [6.1.3   Calling SAP HANA PAL Procedures](#06_001.html#h6.1.3)

### [6.1.4   Model Evaluation](#06_001.html#h6.1.4)

## [6.2   R Integration](#06_002.html#h6.2)

### [6.2.1   Prerequisites and Installation](#06_002.html#h6.2.1)

### [6.2.2   R Packages](#06_002.html#h6.2.2)

### [6.2.3   Calling R Functions from SAP HANA](#06_002.html#h6.2.3)

### [6.2.4   Model Evaluation](#06_002.html#h6.2.4)

## [6.3   Summary](#06_003.html#h6.3)

# [7   Developing Applications with SAP HANA Predictive Analysis Library](#07_001.html#h7)

## [7.1   Introduction to the Use Case](#07_001.html#h7.1)

## [7.2   Building a Predictive Analytics Application Using SAP HANA PAL](#07_002.html#h7.2)

### [7.2.1   Understanding the Business Problem and the Data](#07_002.html#h7.2.1)

### [7.2.2   Data Preparation](#07_002.html#h7.2.2)

### [7.2.3   Model Building](#07_002.html#h7.2.3)

### [7.2.4   Model Validation and Refinement](#07_002.html#h7.2.4)

### [7.2.5   Model Deployment](#07_002.html#h7.2.5)

### [7.2.6   Interpretation and Displaying Results](#07_002.html#h7.2.6)

## [7.3   Summary](#07_003.html#h7.3)

# [8   SAP AI Business Services](#08_001.html#h8)

## [8.1   Overview](#08_001.html#h8.1)

## [8.2   Document Classification](#08_002.html#h8.2)

### [8.2.1   Test Run of the Document Classification Service](#08_002.html#h8.2.1)

## [8.3   Document Information Extraction](#08_003.html#h8.3)

### [8.3.1   Test Run of the Document Information Extraction Service](#08_003.html#h8.3.1)

## [8.4   Business Entity Recognition](#08_004.html#h8.4)

## [8.5   Data Attribute Recommendation](#08_005.html#h8.5)

### [8.5.1   Test Run of the Data Attribute Recommendation Service](#08_005.html#h8.5.1)

## [8.6   Invoice Object Recommendation](#08_006.html#h8.6)

## [8.7   SAP Service Ticket Intelligence](#08_007.html#h8.7)

### [8.7.1   Test Run of the Service Ticket Intelligence Service](#08_007.html#h8.7.1)

## [8.8   Summary](#08_008.html#h8.8)

# [9   Building Scenarios Using Jupyter Notebook](#09_001.html#h9)

## [9.1   Adding a Notebook](#09_001.html#h9.1)

## [9.2   SAP Data Intelligence Python SDK](#09_002.html#h9.2)

### [9.2.1   Setting Up and Leveraging the SAP Data Intelligence SDK](#09_002.html#h9.2.1)

### [9.2.2   SAP Data Intelligence Python SDK](#09_002.html#h9.2.2)

### [9.2.3   Popular Python Libraries](#09_002.html#h9.2.3)

### [9.2.4   Various Library Options](#09_002.html#h9.2.4)

## [9.3   Use Case](#09_003.html#h9.3)

### [9.3.1   Setting Up the Scenario](#09_003.html#h9.3.1)

### [9.3.2   Scripting](#09_003.html#h9.3.2)

### [9.3.3   Data Plotting](#09_003.html#h9.3.3)

### [9.3.4   Code Execution](#09_003.html#h9.3.4)

## [9.4   Summary](#09_004.html#h9.4)

# [10   Automated Machine Learning Data Science Automation](#10_001.html#h10)

## [10.1   AutoML on SAP Data Intelligence](#10_001.html#h10.1)

## [10.2   Features of AutoML](#10_002.html#h10.2)

## [10.3   AutoML Step-by-Step](#10_003.html#h10.3)

### [10.3.1   Configuring the Training Data Collection](#10_003.html#h10.3.1)

### [10.3.2   Configuring the Test Data Collection](#10_003.html#h10.3.2)

### [10.3.3   Setting Up AutoML](#10_003.html#h10.3.3)

### [10.3.4   Testing AutoML](#10_003.html#h10.3.4)

## [10.4   Summary](#10_004.html#h10.4)

# [11   Conversational Artificial Intelligence](#11_001.html#h11)

## [11.1   Introduction to SAP Conversational Artificial Intelligence](#11_001.html#h11.1)

## [11.2   SAP Conversational AI](#11_002.html#h11.2)

### [11.2.1   Natural Language Processing Engine](#11_002.html#h11.2.1)

### [11.2.2   Intents](#11_002.html#h11.2.2)

### [11.2.3   Expressions](#11_002.html#h11.2.3)

### [11.2.4   Entities](#11_002.html#h11.2.4)

### [11.2.5   Languages](#11_002.html#h11.2.5)

### [11.2.6   Channels](#11_002.html#h11.2.6)

## [11.3   Bot Building Techniques](#11_003.html#h11.3)

### [11.3.1   Bot Building Process](#11_003.html#h11.3.1)

### [11.3.2   Bot Connector](#11_003.html#h11.3.2)

### [11.3.3   Bot Monitoring and Analytics](#11_003.html#h11.3.3)

### [11.3.4   SAP Conversational AI APIs](#11_003.html#h11.3.4)

## [11.4   Building a Chatbot Using SAP Conversational AI](#11_004.html#h11.4)

### [11.4.1   Let’s Build a Bot!](#11_004.html#h11.4.1)

### [11.4.2   Setting Up the Bot Project](#11_004.html#h11.4.2)

### [11.4.3   Creating Intents](#11_004.html#h11.4.3)

### [11.4.4   Setting Up Entities](#11_004.html#h11.4.4)

### [11.4.5   Setting Up Skills](#11_004.html#h11.4.5)

### [11.4.6   Enabling Voice](#11_004.html#h11.4.6)

## [11.5   Summary](#11_005.html#h11.5)

# [Part III   Use Cases and Roadmaps](#III_001.html#hIII)

# [12   Integrating Machine Learning with the Internet of Things](#12_001.html#h12)

## [12.1   Technology-Driven Transformation](#12_001.html#h12.1)

## [12.2   Data—The Common Theme](#12_002.html#h12.2)

## [12.3   Use Cases](#12_003.html#h12.3)

### [12.3.1   Supply Chain](#12_003.html#h12.3.1)

### [12.3.2   Healthcare](#12_003.html#h12.3.2)

## [12.4   Summary](#12_004.html#h12.4)

# [13   Industry Use Cases for Machine Learning Applications](#13_001.html#h13)

## [13.1   Acceptance of Machine Learning across Different Industries](#13_001.html#h13.1)

### [13.1.1   Assessing the Impact of Machine Learning](#13_001.html#h13.1.1)

### [13.1.2   Challenges of Machine Learning Applications](#13_001.html#h13.1.2)

## [13.2   Machine Learning Ecosystem](#13_002.html#h13.2)

## [13.3   Identifying Industry Use Cases](#13_003.html#h13.3)

### [13.3.1   Manufacturing Industry](#13_003.html#h13.3.1)

### [13.3.2   Customer Service Industry](#13_003.html#h13.3.2)

### [13.3.3   Healthcare Service Industry](#13_003.html#h13.3.3)

### [13.3.4   Finance Industry](#13_003.html#h13.3.4)

## [13.4   Summary](#13_004.html#h13.4)

# [14   Conclusion and Roadmap](#14_001.html#h14)

## [14.1   Recap](#14_001.html#h14.1)

## [14.2   Best Practices](#14_002.html#h14.2)

## [14.3   Roadmap](#14_003.html#h14.3)

## [14.4   Summary](#14_004.html#h14.4)

# [The Authors](#A_001.html#hA)

# [Index](#index.html#index)

## [Service Pages](#service.html#service)

## [Legal Notes](#legal_notes.html#recht)

## Preface

The dawn of the fourth industrial revolution has introduced us to the era of intelligence. In this era, enterprises are keen to transform their traditional way of running business processes. An era where espousing advanced technologies is no more a luxury—rather—a need of the moment for every enterprise to either thrive or survive. At this critical junction of transformation, every CFO and CEO is faced with the question: how they can match the pace of change and evolve as an intelligent enterprise?

To enable this transformation, intelligent systems and constant technology advancement is essential in every process area, especially to predict (rather than react to) market challenges. The latest advancements in the area of artificial intelligence and machine learning offer new ways to absorb available data, recognize patterns therein to predict outcomes, select moves, or produce results based on the statistical likelihood of success.

In accordance with this new era, SAP’s vision of intelligent enterprise satisfies the need. Industries are harnessing intelligent technologies like artificial intelligence and machine learning to enable digital transformation. SAP’s offering in the artificial intelligence and machine learning space allows industries to effectively curate enterprise data assets and rearchitect business processes to build a stronger digital foundation for the entire enterprise. For an effective application, it’s important to study and understand the capabilities and potential so that the right decision can be made. This book shares an in-depth study of SAP’s spectrum of machine learning and artificial intelligence-related capabilities along with real-world examples which will ultimately help readers learn and make significant contributions towards constructing their own intelligent enterprise.

This book is intended to introduce readers to numerous concepts of data science, artificial intelligence, and machine learning, along with insights of SAP’s various machine learning capabilities in the area of native SAP HANA, SAP Data Intelligence, SAP Conversational AI, various services, applications, and many more. In addition to theoretical aspects, this book guides you through several hands-on throught. Readers will learn about how never-before-seen enterprise challenges are addressed with intelligent enterprise.

So, welcome to Machine Learning with SAP: Models and Applications!

### Who Should Read this Book

This book is for readers who want to learn about artificial intelligence, machine learning, and how build their career in data science using SAP. This book covers the preliminary concepts, business use cases, and technical details, step-by-step. This book is for beginners, or those already familiar with machine learning concepts. To complement the concepts, in few places we have used some vector and matrix notations, but readers not familiar with them can safely bypass those equations without compromising on understanding of the concepts. This book will be useful for technical developers, technical leaders, aspiring data scientists, functional consultants, and business executives who want to embark into the wonderful world of artificial intelligence and machine learning, not to just see it from outside but also viewing it from inside.

### Structure of the Book

This book is structured to show the concepts of machine learning and intelligent enterprise first, followed by discussion about the machine learning fundamentals. Here, we’ll cover machine learning algorithms and its execution lifecycle. Next, we’ll dive into SAP’s various machine learning offerings in the area of SAP HANA, SAP Data Intelligence, SAP HANA Predictive Analytics, SAP AI Business Services, and SAP Conversational AI. We conclude with a look at various industry use cases and real-life examples to help readers understand the implementation aspect of machine learning. Overall, each chapter self-contained however, we recommend going through the chapters in order to help unearth various aspect of SAP’s machine learning capabilities and its applicability towards intelligent enterprise. Downloadable code and color versions of several figures can be found in the Product supplements folder at [www.sap-press.com/5014](http://www.sap-press.com/5014).

#### [Part I](#I_001.html#hI): Introduction

These first few chapters are focused on laying the foundation of machine learning fundamentals, various algorithms, lifecycle methods, and an introduction to SAP’s various machine learning offerings and capabilities.

*   [Chapter 1](#01_001.html#h1): Machine Learning and Intelligent Enterprise provides a introduction to machine learning and how it can be leveraged to build intelligent and integrated enterprise applications that can automate day-to-day business processes. Readers will also learn how essential building blocks and technologies offered by SAP lay the foundation of intelligent enterprise architecture.
    
*   [Chapter 2](#02_001.html#h2): Machine Learning Fundamentals provides an in-depth understanding of machine learning concepts. Including the basic concepts of probability and machine learning scenarios, we embark into the domain of machine learning algorithms. This chapter presents widely-used machine learning algorithms covering the mathematical basis, important features, advantages, disadvantages, and application scenarios.
    
*   [Chapter 3](#03_001.html#h3): Implementation Lifecycle explains the key components of the machine learning application development lifecycle. It introduces widely used machine learning methodologies like CRISP-DM, DMAIC, ASUM-DM, and details the key activities common across these methodologies.
    
*   [Chapter 4](#04_001.html#h4): Machine Learning on SAP HANA provides an overview of the machine learning components of the SAP HANA platform: server-side components like SAP HANA Predictive Analysis Library, SAP HANA Automated Predictive Library, SAP HANA External Machine Learning Library, R integration, and client-side components. This chapter also introduces R and illustrates basic R commands, as the statistical models in R are often used from the SAP HANA platform.
    
*   [Chapter 5](#05_001.html#h5): Machine Learning with SAP Data Intelligence introduces to the unique features and components offered by SAP’s new data science platform including a look at the underlying machine learning and data science concepts which will help readers understand the platform and it’s applicability towards building intelligent solutions.
    

#### [Part II](#II_001.html#hII): Building Machine Learning Applications

These next few chapters are focused on building machine learning applications using SAP’s various machine learning capabilities and covering the essential technical details that enable readers to develop their own machine learning applications in SAP.

*   [Chapter 6](#06_001.html#h6): SAP HANA Predictive Analysis Library is a technical look into building machine learning applications using the SAP HANA Predictive Analysis Library and R Integration. This chapter supplements the concept with sample code for better understanding.
    
*   [Chapter 7](#07_001.html#h7): Developing Applications with SAP HANA Predictive Analysis Library presents a real-life use case of predictive analytics and shows, step-by-step, how to use SAP HANA Predictive Analytics Library and apply the machine learning concepts.
    
*   [Chapter 8](#08_001.html#h8): SAP AI Business Services focuses on specially crafted services to serve business processes common across multiple industries, enriching customer experience.
    
*   [Chapter 9](#09_001.html#h9): Building Scenarios Using Jupyter Notebook will demonstrate, step-by-step, how to build a machine learning scenario using Jupyter Notebook while exploring the various application programming interfaces (APIs) available in the SAP Data Intelligence Python software development kit (SDK) for Jupyter Notebook.
    
*   [Chapter 10](#10_001.html#h10): Automated Machine Learning Data Science Automation will explore AutoML and its component and features, taking the reader through the various steps of building an machine learning scenario using the AutoML features on SAP Data Intelligence platform.
    
*   [Chapter 11](#11_001.html#h11): Conversational Artificial Intelligence introduces readers SAP Conversational AI, along with its various components, features, and services, including how to build intelligent enterprise bots.
    

#### [Part III](#III_001.html#hIII): Use Cases and Roadmaps

These next few chapters are focused on surveying various industry use cases and how the power of artificial intelligence, machine learning, the Internet of Things, and blockchain can help enterprises to deal with numerous business challenges, especially in the context of new normal in the post-COVID world.

*   [Chapter 12](#12_001.html#h12): Integrating Machine Learning with the Internet of Things takes a look at the integration of three technologies: machine learning, Internet of Things, and to see how we can converge machine learning with Internet of Things and blockchain and build smart enterprise solutions for the post-COVID world.
    
*   [Chapter 13](#13_001.html#h13): Industry Use Cases for Machine Learning Applications further dives into industry-specific use cases to show how SAP’s intelligent enterprise-oriented offering can be leveraged to solve real-industry challenges including a study of possible architecture, methodologies, and services required to build solution.
    
*   [Chapter 14](#14_001.html#h14): Conclusion and Roadmap rounds this book out with a look at what we’ve learned and what’s next in the future of the intelligent enterprise.
    

### Acknowledgments

#### Laboni Bhowmik

I would like to thank my bundles of joy, Avni and Anvit, for not being naughty when Mumma was working, and my husband for the inspiration and support, and also making it possible for me to finish my chapters on time. I would also like to thank my parents and my in-laws for their blessing and continuous support.

#### Avijit Dhar

This book would not have been possible without the relentless support of my wife in all possible ways, and my lovely kids Avni and Anvit who had to sacrifice their quality time with their dad, as I was busy with researching and writing the book. I would also like to thank my parents and in-laws for their blessing and continuous support. I would like to dedicate this book to my bundles of joy, Avni and Anvit, whose presence bring smile in our lives every single morning.

#### Ranajay Mukherjee

This book would not have been possible without the relentless support and inspiration from my parents, sister, and family. I would also like to thank my colleague, Mr. Amit Kumar Das, who helped me setting up R integration with SAP HANA and for constantly supporting me in associated research activities. I would like to dedicate this book to inspirational memory of my father, Mr. Dinesh Chandra Mukherjee, and my constantly supportive mother, Mrs. Kalpana Mukherjee, whose blessing is a great source of inspiration in my life.

As a team we would like to express our gratitude to our IBM colleagues including Asidhara Lahiri and Dipankar Saha for their continuous support and the team including Swati Singhal and Supriya Malakar for helping in building demo solutions.

Last but not the least, we want to thank the SAP PRESS team, especially Will Jobst and Hareem Shafi, who provided necessary guidance and support to ensure that the schedule was met, content reviewed and edited, and everything else needed to convert our experience into this book for the benefit of the community.

# Part I

Introduction

# 1    Machine Learning and Intelligent Enterprise

In this chapter, we’ll provide a detailed introduction to machine learning and show you how to leverage machine learning to build intelligent and integrated enterprise applications. With these applications, you can automate day-to-day business processes and improve your interactions with customers, suppliers, and collaborators.

An intelligent enterprise is the future that every business dreams of. But before we ride into the future, let’s first take a step back and look at the past, revisiting all footsteps we’ve taken so far:

*   1960s–1980s, mainframe and personal computers  
    An automation revolution driven by the innovation of transistors and silicon chips along with emergence of large-scale mainframe system and personal computers.
    
*   1990s–2000s, client server and internet  
    Demonstrated widespread adoption of personal computers, broadband internet, rise of enterprise resource planning (ERP) systems and process-oriented technologies.
    
*   2000s–2010s, cloud, mobile, and big data  
    Digital transformation, it’s all about smartphones, cloud computing, social networks, and big data.
    
*   2010s–2020s, intelligent technolog ies  
    Taking advantage of technological advancements in the areas of machine learning, artificial intelligence, Internet of Things, blockchain, and advance analytics including prediction.
    

Over the last few decades, technology has evolved significantly: We’ve gone from the era of industrial automation to business process automation to digital transformation and finally arrived at the era of the intelligent enterprise. The era of industrial automation was all about transistors and the silicon chip revolution along with the emergence of large-scale mainframe systems and PCs focusing on shop floor automation. Meanwhile, the era of business process automation demonstrated the widespread adoption of PCs, broadband Internet, enterprise resource planning (ERP) systems, and process-oriented technologies. Then, we entered the era of digital transformation, which is all about smartphones, cloud computing, social networks, and big data. The final but the most anticipated era is the current era of enterprise intelligence, taking advantage of technological advancements in the area of machine learning, artificial intelligence (AI), Internet of Things (IoT), blockchain, and advanced analytics including the prediction of events before they occur.

For many decades, companies have invested heavily on digitally transforming their business processes and related operations, and the digital transformation so far has helped these organizations use their data with increasing visibility and agility and make more insightful decisions. But, surprisingly, many of these organizations have started realizing that digital transformation alone is not enough to survive and must become intelligent enterprise in today’s era. The intelligent enterprise, shown in [Figure 1.1](#01_001.html#f1.1), is where business processes and customer experiences are driven by intelligent applications that can make informed decisions and navigate flexible operational processes.

[![The Intelligent EnterpriseIntelligent enterprise](bilderklein/klein01_001.png)](img-f1.1.html) 

**Figure 1.1**    The Intelligent Enterprise

In brief, an intelligent enterprise typically facilitates the following advantages:

*   People can work seamlessly and access any systems from any device at any time.
    
*   Systems are capable of prioritizing work for people.
    
*   Solutions for dealing with business problems are proposed.
    
*   Repetitive and time-consuming tasks are performed in an automated fashion.
    
*   Systems can discover new patterns and insights from business data during processing, learning from this data to make smarter decisions at the right times.
    

We’ll introduce you to machine learning in [Section 1.1](#01_001.html#h1.1) and walk you through a brief history of how we’ve arrived at the intelligent era in [Section 1.2](#01_002.html#h1.2). Then, you’ll learn all about numerous intelligent enterprise use cases in [Section 1.3](#01_003.html#h1.3), before we focus our attention on the powerful machine learning portfolio offered by SAP in [Section 1.5](#01_005.html#h1.5).

## 1.1    What Is Machine Learning?

Machine learning is a form of AI that enables a system to learn from data rather than through explicit programming. The precision delivered by a machine learning model is completely dependent on its training data—the more training data you use, the more accurate your predictions. A machine learning model basically represents the output generated when you train your machine learning algorithm with data. After training, when you provide a model with an input, you’ll be given an output. For example, a predictive algorithm will create a predictive model. Then, when you provide the predictive model with data, you’ll receive a prediction based on the data that trained the model.

A key force behind enterprise digital transformation these days, machine learning has been gaining lot of momentum, and enterprises around the world are taking advantage of it instead of using traditional software-based rules to uncover unknown patterns, analyses, and facts from various sources (for instance, text, images, social feed, big data, and IoT devices) including provisions for “training” and “learning” models. Along with SAP, some key key players in this domain include IBM Watson cognitive services, Google TensorFlow, and Azure Machine Learning, which have been operational for a long time.

## 1.2    Transition from the Digital Era to the Intelligent Era

The digital era of the last decade has evolved into today’s intelligent era by taking advantage of technological advancements especially in the area of artificial intelligence (AI) and machine learning. Using these capabilities, your organization can automate manual activities, identify potential risks, and stay way ahead of the competition. To maximize the gains from technological advancements and minimize disruption, today’s organizations must evolve into an intelligent enterprise that can connect business processes with advanced technologies and software solutions and can also quickly adapt to changing business conditions.

Machine learning, as the basis for intelligent applications in the intelligent enterprise, has emerged as one of the hottest buzzwords as enterprises around the world discover the potential of machine learning to uncover new dimensions of analysis and fact finding based on data from various sources, including provisions for “training” and “retraining” data models. Machine learning services run on defined algorithms that can enable computers to self-learn from data without the need for explicit programming. These algorithms are designed to learn, grow, develop, and improve every time they are exposed to new data or decision calculations.

Today’s enterprises face exponential growth in the amounts of data required for operations, which can overwhelm an individual’s decision-making abilities. Machine learning in this context can provide a powerful method for helping people improve decision-making bandwidth, responsiveness, accuracy, and consistency of results. According to the Gartner’s 2019 survey of chief information officers (CIOs), “The number of enterprises implementing artificial intelligence (AI) grew 270 percent in the past four years and tripled in the past year.” Machine learning and intelligent applications have the greatest momentum, while other approaches are also popular like AI platforms as a service or AI cloud services.

Various studies have shown that machine learning drastically reduces the average time spent executing day-to-day activities and helps you make more informed decisions with less risk of error.

## 1.3    Intelligent Enterprise Use Cases

Technology is changing the way enterprises conduct business, and today’s enterprises must cut through the hype and become more useful and efficient to become an intelligent enterprise. We can improve everything from interacting with customer to executing and optimizing processes more efficiently; some would say, “more intelligently.” Businesses looking to stay relevant and competitive must start adopting intelligent end-to-end technologies to keep pace with these changes—and with the competition. Let’s look at a few key use cases that are common across different industries and discuss how today’s enterprises can take advantage of intelligent technologies and digital platforms on their journey to becoming an intelligent enterprise.

### 1.3.1    Intelligent Invoice Matching

Traditionally, accounts receivable teams would spend hours analyzing data to resolve discrepancies in digital payments. Of these activities, invoice matching is one of the most complex and time-consuming processes. Complexities originate from differences in payment modes by customers, and any kind of manual postprocessing for incoming bank statements (for instance, items that could not be matched to open receivables) takes time and effort. Another challenge also includes the inability to support the rapid growth in payments without increasing processing team size or maintaining and updating tailored rules for matching payments against open receivables due to huge costs for implementing these rules. As an intelligent enterprise, the answer is to leverage machine learning to drive financial applications. Machine learning can learn from the manual invoice matching process and from historical accounting data to perform automatic clearance of incoming payments or to suggest a list of possible clearing matches with which the accounts receivable team can process outstanding items quickly. This kind of intelligent automation can help your accounts receivable team handle higher transaction loads more efficiently and improve days sales outstanding (DSO) and other working capital metrics.

### 1.3.2    Smart Recruiting

Recruiting candidates for different position is a key initiative for every organization, and recruiters often must follow a laborious process of going through thousands of job profiles to identify the candidates that best fit the position. An intelligent enterprise in this context can easily apply machine learning to train and build a hiring model based on existing hiring records, resumes, and past candidate profiles and later apply the same model to identify the best candidates for a given job description, or vice versa.

### 1.3.3    Service Ticket Intelligence

Due to the rise in the usage of virtual systems, support ticket systems have become prominent. Addressing tickets to the appropriate person or unit on the support team is critically important for providing improved end-user satisfaction while ensuring better allocation of support resources. The assignment of help tickets to the appropriate group can still be manually performed, but at large organizations, manual assignment is not sufficient. The process is time consuming and requires a great deal of human effort. Mistakes can occur from human errors. Also, resource consumption is inefficient because of misaddressing. Moreover, manual assignment increases response times, resulting in lower end-user satisfaction. Customers can contact companies via multiple channels, via social media platforms and review sites, or by email and live chat—any time of the day, wherever they are. Add to that the growing number of mobile users, customers can get in touch more easily than ever, and you can imagine how customer service tickets can start to pile up. So, what happens with all these support tickets? As you probably know, customer agents must assign tags or categories to each ticket depending on their content, which routes the ticket to the correct team. This assignment in itself takes time because the customer agent has to read every issue before tagging the text with the corresponding category.

### 1.3.4    Product Similarity Matching

Today’s e-commerce businesses sell a vast number of products online through various outlets all over the world. Identifying, matching, and cross-checking products for price comparisons, for instance, can be a challenge since no shared unique identifiers have been adopted globally. In this case and in many others, accurate product matching can become extremely important. For instance, a store may want to compare its competitors’ prices for the same product on offer. Similarly, customers may use comparison tools to find the best deals. In this scenario, numerous products exist, but no method can match these products across different stores. Product titles/descriptions do not follow a standardized format. Each store, as well as different sellers within a store, might have different titles and descriptions for the same products. Another challenge comes with respect to attribute listings since different e-tailers follow different formats. Images of the same product can also differ across different e-tailers. For a human, product matching is an impossible task since you’ll need to visit different product pages to ensure the products match. By automating this process through AI and machine learning, you can be sure that the system makes sense of all the information. In machine learning solutions for product matching, the solution provider must initially build a database with billions of products. This task can be performed by collecting information through web crawls and feeds. The system then must come up with a universal taxonomy. This challenge is especially unique because different retailers use different classifications for their products, and the same product might be listed in more than one category. For instance, a particular shoe model might be listed under “casual shoes” as well as “dress shoes.” The system first must design a standardized taxonomy that goes beyond how a particular store classifies its products.

### 1.3.5    Brand Impact

We’ve entered an era in which marketers are bombarded by volumes of data about consumer preferences. In theory, all this information should make grouping users and creating relevant content easier, but that’s not always the case. Generally, the more data added to a marketer’s workflow, the more time required to make sense of the information and to act. Machine learning, a subset of artificial intelligence (AI), gives your system the ability to analyze and interpret data to make accurate predictions without the need for explicit programming. As more data is fed into the algorithm, the more the algorithm learns, in theory, to be more accurate and perform better. If marketers expect to create more meaningful campaigns with target audiences and boost engagement, integrating machine learning can be the tool to unveil hidden patterns and actionable tactics tucked away in those heaping amounts of big data.

### 1.3.6    Robotic Process Automation

You know the hazards of outdated manual processes that impede scale, wasting precious people resources and creating inefficiencies and errors that derail performance and profitability. The answer is intelligent process automation. But what to automate? How to automate it and make it intelligent? Robotic process automation interfaces with existing applications and automates high-volume, repeatable tasks. Robotic process automation transforms how businesses deal with manual processes, freeing up staff for customer-focused and value-adding activities. This first step is critical to creating operational data and capacity that traditionally had not existed. Intelligent process automation (IPA) holds great promise not only for improving operational efficiency.

An intelligent enterprise strategy allows organizations to rapidly transform data into insights—feeding process automation, innovation, optimization, and experience management. Thanks to advances in automation and cognitive computing, you can now automate processes, including any data, at scale across platforms and environments, thus enabling every process, decision, and action to be data driven. These intelligent technologies boost classic robotic process automation capabilities for digital transformation using the depth of the machine learning stack. Given the ongoing proliferation of connected devices, analytics in the cloud, the capabilities enabled by the intelligent technologies portfolio, and next-generation machine learning and AI capabilities, intelligence process automation is now the top choice for meeting the increased demand for the automated workplace with streamlined processes.

### 1.3.7    Virtual Assistance

Today, a considerable amount of human hours employed in work is focused simply on data entry tasks across various systems of record, which include ERPs (SAP, PeopleSoft, JD Edwards, Baan, etc.); relational databases (Oracle, DB2, SQL Server); and mainframes. A study by chatbots magazine claims that businesses can minimize customer service costs by around 30% with conversational interfaces like chatbots. The average human interaction for customer service costs around $30-$40 per interaction while the average text interaction would only cost around $5-$8 per interaction, according to an Aspect software study. Enterprise systems are highly disparate, and a great deal of employee time is spent in data entry across these systems. Much of this information going into your systems is often sent or received as unstructured data, for example, emails, chat messages, Word documents, PDFs, PowerPoint presentations, or even verbal communications. You generally need humans to interpret all that data and enter decisions and actions into the correct system of record.

However, these intelligent applications automatically get better and smarter every time you use them. Eventually, you could even replace existing processes with automated best practices.

## 1.4    SAP’s Intelligent Enterprise Strategy

Today’s enterprises must cut through the hype and become an intelligent enterprise efficiently.

Now that you understand how essential machine learning can be to make enterprises more intelligent and smart, let’s look into SAP’s strategic perspective for building intelligent enterprises.

For almost half a century, SAP has been on a journey in helping enterprises to create value for their organizations by applying advanced technology to address business problems both simple and complex. SAP’s intelligent enterprise mission aims to help enterprises be successful in the new economy where being a data-driven enterprise and delivering exceptional experiences are keys to success. As shown in [Figure 1.2](#01_004.html#f1.2), the intelligent enterprise strategy is basically a combination of three main components including the intelligent suite, intelligent technologies, and the digital platform that defines how enterprises will operate businesses in the future.

[![Intelligent Enterprise Strategy](bilderklein/klein01_002.png)](img-f1.2.html) 

**Figure 1.2**    Intelligent Enterprise Strategy

### 1.4.1    Intelligent Suite

As shown in [Figure 1.3](#01_004.html#f1.3), SAP’s intelligent suite is a modularized set of integrated line of business (LOB) applications that enable you to share insights across functions to better manage stakeholders and support their day-to-day operations. For example, SAP Cash Application can process and match invoices with incoming payments and automatically match open receivables and clearing payments.

[![The Intelligent Suite](bilderklein/klein01_003.png)](img-f1.3.html) 

**Figure 1.3**    The Intelligent Suite

### 1.4.2    Digital Platform

SAP’s digital platform is a unique combination of data management and cloud platform technologies for intelligent enterprises to dynamically manage the growing volume of data and business processes and make data more meaningful in real time. The platform also serves as the necessary foundation of all intelligent activities. [Figure 1.4](#01_004.html#f1.4) shows a representation of SAP’s digital platform portfolio.

[![Digital Platform](bilderklein/klein01_004.png)](img-f1.4.html) 

**Figure 1.4**    Digital Platform

### 1.4.3    Intelligent Technologies

As shown in [Figure 1.5](#01_004.html#f1.5), intelligent technologies combine necessary tools and technologies such as analytics, machine learning, artificial intelligence (AI), Internet of Things (IoT), and blockchain, which can turn intelligence into business outcomes. All these tools and technologies are delivered through the digital platform, embedded within intelligent suite applications, and applied to processes integrating SAP and third-party data and applications.

[![Intelligent Technologies](bilderklein/klein01_005.png)](img-f1.5.html) 

**Figure 1.5**    Intelligent Technologies

From the bottom up, the digital platform provides the necessary intelligent tools and technologies to build the intelligent suite that you can leverage to serve different purposes, such as for customer experience, digital core, people engagement, and so on. The intelligent enterprise strategy basically allows vendors, customers, and collaborators to connect with the processes or applications serving the intelligent enterprise. In this context, SAP Data Intelligence provides intelligent technologies to enable the intelligent suite and deliver the intelligent enterprise. Furthermore, SAP Data Intelligence can also be used by vendors, customers, and collaborators to even build their own intelligent applications and analyses.

## 1.5    SAP’s Machine Learning Technologies and Applications

To enable your intelligent enterprise, SAP comes with a robust set of machine learning capabilities and AI offerings. SAP’s machine learning technology portfolio combines a unique blend of intelligent apps and extensions, a data science platform, and embedded machine learning and other services. Let’s explore the spectrum of SAP’s offerings in the machine learning space.

### 1.5.1    Embedded Machine Learning Applications

Embedded machine learning applications are designed to quickly introduce users to AI models for automating or adding intelligence to daily/routine work. Without getting too much into the complexity, AI runs in the background based on embedded intelligent models and simplifies the work. In this space, SAP has a range of products including SAP Service Ticket Intelligence, Intelligent Invoice processing, and many more embedded intelligent models. These models are also capable of learning from human capabilities and can apply the same knowledge to future decision-making by making predictions, recommendations, and supporting human users in parallel. As shown in [Figure 1.6](#01_005.html#f1.6), in addition to the embedded machine learning applications with SAP S/4HANA, SAP also offers business services that you or your partners can leverage to build your own custom intelligent solutions, which we’ll cover more in detail in the later part of the book.

[![SAP’s Machine Learning Portfolio](bilderklein/klein01_006.png)](img-f1.6.html) 

**Figure 1.6**    SAP’s Machine Learning Portfolio

### 1.5.2    SAP Intelligent Robotic Process Automation

SAP Intelligent Robotic Process Automation (SAP Intelligent RPA), as shown in [Figure 1.7](#01_005.html#f1.7), is the next in line of machine learning offerings. This solution is focused on task automation by accelerating repetitive and tactical manual processes within SAP applications in a user-centric way, thus minimizing keying errors, speeding up work, and cutting costs. SAP Intelligent RPA basically handles unmodeled processes, for instance, data entry, accounting, human resources, and supply chain management and many other similar activities, by specifying an automated process based on interactions with user interfaces (UIs). In the background, machine learning acts as the brain to manage exceptions and guide the SAP Intelligent RPA bot to execute the desired processes.

[![SAP Intelligent RPA](bilderklein/klein01_007.png)](img-f1.7.html) 

**Figure 1.7**    SAP Intelligent RPA

### 1.5.3    SAP Conversational Artificial Intelligence

SAP Conversational Artificial Intelligence (SAP Conversational AI) is a collection of tools required to build chatbots and conversational applications and includes a natural language processing (NLP) engine and an interactive bot builder with a graphical interface for developers to build great bots! As shown in [Figure 1.8](#01_005.html#f1.8), SAP Conversational AI can accurately connect customers to the right business context through its chatbot, which is a key step to making your enterprise more intelligent. SAP Conversational AI services ensure that you can offer 24/7 customer support in multiple languages and can deal with the increasing number of calls. SAP Conversational AI enables end users to place requests to the system and obtain responses, transferring the onus of execution from humans to the machine.

[![SAP Conversational AI](bilderklein/klein01_008.png)](img-f1.8.html) 

**Figure 1.8**    SAP Conversational AI

### 1.5.4    SAP Data Intelligence

Last, but not least, is SAP Data Intelligence. With the recent introduction of SAP Data Intelligence on the cloud, machine learning with SAP HANA (formerly known as SAP Leonardo Machine Learning Foundation), along with the SAP Data Hub, is now an integral part of the SAP Data Intelligence platform, offering a winning combination of data orchestration and machine learning functionality on SAP Cloud Platform. Briefly, SAP Data Hub on-premise is a data sharing, pipelining, and orchestration solution that helps companies accelerate and expand the flow of data across modern, diverse data landscapes. In addition to Google TensorFlow services, SAP Data Hub includes prebuilt machine learning library integrations using built-in operators for various machine learning services, which you can use to build enterprise data science scenarios seamlessly. With embedded machine learning included as part of SAP Data Intelligence, these capabilities will be no longer be available as a standalone service for new customers and must be consumed via SAP Data Intelligence. Thus, in a nutshell, SAP Data Intelligence basically covers the complete data science process starting from connecting intelligent data sources with supported connectors similar to SAP Data Hub and machine learning offered by AI with SAP HANA. [Figure 1.9](#01_005.html#f1.9) shows the overall offerings included with SAP Data Intelligence.

[![SAP Data Intelligence](bilderklein/klein01_009.png)](img-f1.9.html) 

**Figure 1.9**    SAP Data Intelligence

### 1.5.5    Embedded Machine Learning within SAP HANA

In addition to SAP Data Intelligence, SAP Conversational AI, and SAP Intelligent RPA, SAP also offers scalable, SAP HANA-based machine learning platform for enterprises. Any effective machine learning requires a huge amount of data, and SAP HANA-based machine learning offers key capabilities for applying intelligence where your data actually resides, or at the memory level? This reasoning underpins SAP HANA machine learning. Also, running machine learning algorithms at the database level reduces latency and is particularly beneficial when trained machine learning models make inferences, make predictions, or classify data. As shown in [Figure 1.10](#01_005.html#f1.10), machine learning on SAP HANA is a combination of libraries, modelers, and components including the following solutions:

*   SAP HANA Automated Predictive Library (SAP HANA APL), formerly known as Predictive Analytics Library (PAL), is primarily targeted for business analysts and data analysts who want to create predictive models that run within the SAP HANA platform. Using an automated, wizard-driven interface, these users can access machine learning capabilities without requiring much data science experience.
    
*   SAP HANA Extended Machine Learning Library (SAP HANA EML) is packaged as an Application Function Library (AFL) that allows access external machine learning libraries like Google TensorFlow. The models in these libraries can be easily integrated into enterprise applications and business processes for clients. Models served by Google TensorFlow are registered in SAP HANA via remote sources and then applied via SQL-script SAP HANA data for scoring. (Scoring is the process of applying a predictive model to a set of data.)
    
*   Application Function Modeler (AFM) is an extension of SAP HANA Studio for creating flowgraph models like tables, views, procedures, R scripts, etc. Through its drag-and-drop interface, ultimately less experienced developers can build complex procedures quickly without writing SQL script code. AFM basically eliminates the need to code PAL and Business Function Library (BFL) algorithms, and multiple users can access model objects for developing simultaneously.
    
*   SAP HANA with R integration leverages R, another open source machine learning framework widely used for statistical computing and advanced data analysis. SAP HANA with R integration enables you to consume and execute all the open source algorithms available in R. SAP HANA with R integration slightly differs from SAP HANA EML. Using SAP HANA with R integration, you can embed R scripts into a stored procedure in SAP HANA. The SAP HANA database will interpret the R language script and accordingly submit the script to the R server. The ultimate goal of integrating SAP HANA with R is to customize algorithms beyond what is offered in the standard libraries available through SAP HANA APL.
    

[![SAP HANA Machine Learning](bilderklein/klein01_010.png)](img-f1.10.html) 

**Figure 1.10**    SAP HANA Machine Learning

## 1.6    Summary

In this chapter, we discussed the evolution of enterprise technology evolution and introduced machine learning. We explored SAP’s intelligent enterprise strategy and discussed its machine learning portfolio and it’s spectrum of offerings: embedded machine learning applications, SAP Intelligent Robotic Process Automation, SAP Data Intelligence, SAP Conversational AI, and machine learning in SAP HANA. We’ll explore each of these in the following chapters.

# 2    Machine Learning Fundamentals

This chapter presents the fundamental concepts of machine learning. We’ll start with an introduction to the probability theory, which serves as the cornerstone of various machine learning concepts. Then, outline different types of learning scenarios and move into the domain of machine learning algorithms. This chapter provides in depth understanding of several widely used machine learning algorithms covering mathematical basis, important features, advantages, disadvantages, and application scenarios.

In machine learning, the system analyzes input data to learn underlying patterns, hidden relationships within data and uses this information for prediction in a specific business scenario. This is achieved through various algorithms of artificial intelligence and statistical inference. There are thousands of such algorithms, and no one is uniformly the best. Depending on nature of data, availability of data, and type of business problems to be addressed, different algorithms are used in different scenarios. The probability theory plays a key role in many of these algorithms as the mathematical foundation. In this chapter, we will discuss about these building blocks of machine learning, focusing on probability concepts and some widely used machine learning algorithms.

## 2.1    Basic Probability Concepts

Let’s begin with an example. As a machine learning expert, you need to predict total sales value of a client for a future period (January 2021), based on the sales data till current month (April 2020). If you were asked to provide the total sales value for a historical period (February 2020), you could have derived it based on the historical sales data of February 2020. There was no uncertainty involved, as long as historical data was accurate. However, while predicting total sales value in January 2021 while currently in April 2020, there are many influential factors which are not known to you. These include demand, actual production, price, perception of customers about the products, availability of similar products from other competitors, socioeconomic conditions around January 2021, and more.

So, you cannot say with certainty what will be the total sales value in January 2021, but you may provide the most likely value through identifying patterns in the historical sales data and interpolating it for future period using machine learning.

Let’s take a moment to consider what most likely means in this context. What is the basis of calculating something as most likely? This is where probability theory comes into picture. It provides a mathematical framework to deal with likelihood of an event from a set of possible outcomes and serves as a key tool for prediction.

Probability theory is an extensive subject and it has wide applications in many areas like mathematics, statistics, engineering, artificial intelligence, machine learning, cryptography, physics, economics, biological modeling or even in gambling. Here, we’ll explore some preliminary concepts of probability theory required for machine learning.

### 2.1.1    What is Probability?

In life, there are many phenomena which provide same outcome when repeated under the same set of conditions. A triangle drawn on a plane surface will always have 180 degree as the sum of its three angles, irrespective of shape and size of the triangle. However, there are many phenomena which do not provide same outcome when repeated under the same condition.

When tossing a coin, the outcome will be either heads or tails, but the outcome of a toss is not known in advance. If the coin is tossed one hundred times, heads and tails appear in a random and unpredictable manner. This is an example of a random or nondeterministic phenomenon. Probability theory studies such random phenomena.

For a random phenomenon, the outcome of a particular instance may not be fixed, but if it is repeated multiple times, the outcomes show statistical regularity. In the coin tossing example, it is observed that for a large number of tosses, the proportion of heads (the ratio of number of times heads appeared to the total number of tosses) seem to approach to a fixed number p between 0 and 1 (often p is very close to 0.5 with an unbiased coin). It seems that the proportion of heads converges to p when the number of tosses tends to infinity. This limiting proportion may be considered as the probability of heads in a single toss. This interpretation of probability is known as relative frequency interpretation. According to this interpretation, probability of showing head in a toss is p implies if the coin is tossed for many times (n) then number of time heads will show up is approximately n\*p. However, it may not be possible to carry out the same experiment again and again to calculate the probability. Often, it’s infeasible. Hence, we develop a mathematical model of the random phenomenon (known as a random experiment) and then calculate probability of various events using this model.

Before going to the formal definition of probability, let’s take another example and try to see how a mathematical model can be fit into it. Let’s consider the following random experiment.

A six-sided dice is rolled once. What are the possible outcomes of this experiment? Well, it can be any number between 1 to 6. Now, to make a mathematical model, we first convert this abstract experiment to a set, a concrete mathematical structure. First, we’ll construct a set of all possible outcomes of the experiment and denote it with Ω. Mathematically, we can map each outcome one-to-one with an element of the set Ω. In the example, set Ω contains 6 elements (say, ω[1], ω[2], ..., ω[6]), where ω[1] represents the outcome 1, ω[2] represents the outcome 2, and so on. The set Ω represents the set of all possible outcomes and each element in this set represents an outcome of the random experiment. So, to build a mathematical framework, we first converted the random phenomena or the random experiment into a set, whose elements are mapped one-to-one with the possible outcomes of the experiment. This set Ω is also called a sample space.

#### Assigning Probability

Next, we’ll try to assign probability of occurrence of the outcomes. As per our mathematical model, this will mean assigning a probability measure to each element of the set Ω. If we do so, we can answer questions like:

*   What is the probability that the outcome will be 1?
    
*   What is the probability that the outcome will be 6?
    

However, someone may not be satisfied with only knowing the probability of individual outcomes, they may also be interested to know:

*   What is the probability that the outcome is greater than 3 (put differently: when the outcome is 4, 5, or 6)?
    

This is called an event. An event may be considered as a collection of outcomes. If any of these outcomes occurs, the event has occurred. Mathematically, this is a subset (A) of Ω. So, from mathematical standpoint, we call a subset of Ω an event and calculate the probability of an event based on the outcomes it contains.

###### Note

All the individual outcomes, the Ø (the null set, containing nothing) and Ω itself are subsets of Ω, and they’re also events. We have considered collections of outcomes, which are basically subsets of Ω as our candidates for studying probability.

Let’s look at the probability of occurrence of different events. Individual outcomes are events, but they are also the building blocks of other, larger events.

So first, let’s assign a probability to the outcomes. With each outcome, we can assign a value between 0 and 1, so that the sum of probabilities of all the outcomes is 1. Mathematically, this can be considered as a mapping P from Ω to the interval (0,1) such that:

*   Each outcome mapped to a probability: P(ω[i]) = p[i], for i from 1 to 6
    
*   Probabilities lie between 0 and 1: 0 ⩽ p[i] ⩽ 1 for i from 1 to 6
    
*   Sum of probabilities of all outcomes equals 1: p[1]+p[2] +…+p[6] = 1
    

Until now, we have not assigned any value to p[1], p[2], .., p[6]. We have just made three assumptions:

*   Each outcome has a probability assigned to it
    
*   The probability values lie between 0 and 1, both values inclusive
    
*   Sum of the probabilities of all possible outcomes equals 1
    

Now, in our experiment, if the dice is unbiased and all the 6 outcomes are equally likely, then it is reasonable to assign same probability to all these outcomes. Expressed mathematically, this is p[1] = p[2] = .. = p[6] = p. Since their sum is equal to 1, it implies p[1]+p[2] +…+p[6] = 6\*p = 1 or p = 1/6.

We’ve introduced probability as a function with certain conditions and attempted to derive probabilities of the individual outcomes. In this example, the number of possible outcomes is finite, so we may assign equal probability to individual outcomes if they are equally likely to occur. But when there are infinitely many outcomes, we take a different approach using density and distribution functions, this has been discussed in [Section 2.1.4](#02_001.html#h2.1.4).

However, this is not end of the story. We have introduced events as subsets of Ω, but how to calculate probabilities of the events which contain more than one outcome?

This is done by segregating it into smaller disjoint events and adding up probabilities of the smaller events. In this process, we may end up segregating the event into the individual outcomes it contains and then adding the probabilities of these outcomes (which are already defined) to get probability of the events.

In our example event A, the outcome is greater than 3, contains 3 mutually exclusive events (events which cannot occur simultaneously) and the probability can be determined by summing up the probability of these events as shown below:

A = {ω[4], ω[5], ω[6]} where ω[4], ω[5], ω[6] corresponds to outcomes (and hence events) 4, 5 and 6 respectively. Note that A = {ω[4]} U {ω[5]} U {ω[6]}, can be thought of as union of 3 mutually exclusive events, since in a single rolling of a dice only one outcome can occur. We calculate the probability of event A as sum of the probabilities of these events:

P(A) = P(ω[4]) + P(ω[5]) + P(ω[6]) = 1/6 + 1/6 + 1/6 = ½

This example outlines how a mathematical framework of random experiment and associated probabilities can be derived using set theory.

###### Calculating Probabilities of Events

There is a popular notion of calculating probability of an event as ratio of number of favorable outcomes to the total number of outcomes:

Probability of an event = (total number of outcomes resulting the event) / (total number of possible outcomes)

Consider our example event, the outcome of rolling a dice is greater than 3. There are three outcomes; 4, 5, and 6. The total number of possible outcomes while rolling a dice is 6. So, the probability of this event according to this approach is 3/6 = ½ and it matches with the result. However, the mathematical model of probability does not adopt this approach because:

*   The individual outcomes may not be equally likely
    
*   Total number of possible outcomes may be infinite for many random experiments and division by infinite may not be meaningful.
    

Converting a random phenomenon into a set of all possible outcomes (Ω), defining events as subsets of Ω and assigning probabilities to events as mentioned previously has a major advantage, the set theory results can be easily adopted to the theory of probability.

Let’s consider two events in the rolling of a dice experiment:

A is the event that outcome is less than 4 and B is the event that outcome is an even number. Then, A = {ω[1], ω[2], ω[3]} representing outcomes 1, 2, and 3. B = {ω[2], ω[4], ω[6]} representing outcomes 2, 4, and 6.

The sets AUB = {ω[1], ω[2], ω[3], ω[4], ω[6]} represents the event that either event A or event B occurred and corresponds to all the outcomes except 5. The set A ∩ B = {ω[2]} represents the event that both events A and B occurred and corresponds to outcome 2. Similarly, A^c = {ω[4], ω[5], ω[6]} represents the event that event A did not occur.

Since A = A ∩ Ω = A ∩ (B U B^c) = (A ∩ B) U (A ∩ B^c), using the distributive law of sets, and (A ∩ B), (A ∩ B^c) are mutually exclusive (they don’t share a common element), we can derive P(A) = P(A ∩ B) + P(A ∩ B^c). So, if two of these three probabilities are known, we can derive the third one. Similarly, other set theory results can also be used to derive probabilities.

###### Note

At first glance, summing up probabilities of the constituent outcomes (or disjoint events) to derive the probability of an event may seem rather artificial. If we consider the relative frequency interpretation of probability, it becomes obvious.

An event occurs if any of the outcomes resulting to that event occurs. In our example, the event A (that outcome is greater than 3) occurs only when the outcome is either 4, 5, or 6. Let’s consider that the experiment of throwing a dice is repeated for n times, n being a very large number. Let’s also assume that within these n repetitions, outcome 1 occurred n[1] times, outcome 2 occurred n[2] times and so on.

Then 0 ⩽ n[i] ⩽ n for i = 1, 2, …, 6 and

n[1] + n[2] + n[3] + n[4] + n[5] + n[6] = n

How many times the event A occurred in these n trials? It happened when outcomes were 4, 5, or 6, so the event occurred (n[4] + n[5] + n[6]) times.

So, the proportion of occurring this event is (n[4] + n[5] +n[6]) / n. As n tends to infinity, this proportion tends to probability of the event. But,

[![](bilderklein/kleinEQ_001.png)](img-f_none_02_00.html) 

The left side shows the probability of the event and the right side is sum of the probability of individual outcomes. So, with the relative frequency interpretation, the probability of the event turns out to be the sum of probability of individual outcomes it contains. Also, using the same argument, it can be easily seen that probability values should lie between 0 and 1 and sum of the probability of all outcomes should be 1.

We have adopted the same results, but we have not introduced any interpretation while defining the probability mathematically, much like the same way interpretation of lines or points are not discussed in geometry, but their existence is assumed through axioms. Besides, there are many random experiments where total number of outcomes are infinite, experiments may deal with multi-dimensional spaces, so we cannot use similar argument. Hence, we adopted the results and then generalized it into a mathematical model to handle much broader and complex scenarios.

One final remark on events. In our example of rolling dice, there are 6 possible outcomes, so the set Ω contains 6 elements. How many events are there for this random experiment? Since events are subsets of Ω, it boils down to how many subsets of Ω are there? It is 2⁶ = 64, including both Ø and Ω. In general, a set with n elements has 2^n different subsets. So, the total number of events is quite high. We often deal with random experiments with infinitely many outcomes and the number of possible events become so large that they cannot be treated mathematically. So, we cannot consider all the events, we only take a set of events which has some nice mathematical properties. However, this does not restrict us much as it covers most of cases. More precisely, we consider a sigma-field (denoted as σ-field) of subsets of Ω as permissible events and assign probabilities to only these events.

The σ-field is defined as a nonempty collection of subsets æ of a set Ω is called σ-field of subsets of Ω if the following conditions hold true:

1.  If a subset A is in æ, then A^c is also in æ.
    
2.  If an infinite collection of subsets, say A[1], A[2], A[3], ….is in æ then their union ![inline image](bilder/EQ_002.png)and intersection ![inline image](bilder/EQ_002.png)are also in æ.
    

With this background, let’s now formally define probability.

#### Probability Measure

A probability measure P on a σ-field æ of subsets of Ω is a function from æ to real numbers satisfying the following conditions:

1.  P(Ω) = 1.
    
2.  P(A) ⩾ 0 for all A in æ.
    
3.  If A[n], n = 1, 2, 3, …. are mutually disjoint sets in æ, then,
    
4.  ![inline image](bilder/EQ_004.png)
    

Note that P(A) ⩽ 1 for all A in æ, but it is not required to be specified in the definition, it can be derived easily from other conditions.

The addition of probability of disjointed events are extended to addition of countably infinite disjointed events, as in many scenarios we consider events with infinitely many outcomes. The finite additive feature (if A[1], A[2], A[3], …, A[k] are mutually disjointed sets in æ), then ![inline image](bilder/EQ_005.png)also holds true if we consider A[n] = Ø for all n > k.

A probability space is defined by the set of all possible outcomes Ω, the σ-field of events æ and the probability measure P. It is denoted as (Ω, æ, P).

#### Basic Properties of Probability

Let’s now look at some basic properties of probability based on the definition.

Let us consider two events: A and B. From set theory, it easily follows that

1  A = A ![inline image](bilder/EQ_006.png)Ω = A ![inline image](bilder/EQ_006.png)(B U B^c) = (A ![inline image](bilder/EQ_006.png)B) U (A ![inline image](bilder/EQ_006.png)B^c)

Since (A ![inline image](bilder/EQ_006.png)B) and (A ![inline image](bilder/EQ_006.png)B^c) are subsets of B and B^c respectively, they are mutually disjointed. Hence by third property of the definition:

P (A) = P(A ![inline image](bilder/EQ_006.png)B) + P(A ![inline image](bilder/EQ_006.png)B^c) ^()

If we take A = Ω, then equation (1) becomes P (Ω) = P(Ω ![inline image](bilder/EQ_006.png)B) + P(Ω ![inline image](bilder/EQ_006.png)B^c) = P(B) + P(B^c) (since Ω ![inline image](bilder/EQ_006.png)B = B and Ω ![inline image](bilder/EQ_006.png)B^c = B^c).

2  Now, by definition, P (Ω) = 1, it implies 1 = P(B) + P(B^c) or

For any event B, P(B^c) = 1 - P(B)

This shows that the probability of not occurring an even is 1 – (probability of occurring that event).

If we now take B = Ω, then B^c = Ø and the equation 2 becomes

3  P(Ø) = 1 - P(Ω) = 1 – 1 = 0

Since Ω is the event which contains all possible outcomes, it signifies the event that one of the outcomes will occur. By definition, it has probability 1. On the other hand, Ø signifies the event that none of the outcomes will occur and equation 3 shows it has zero probability.

Now let’s consider two events A, B and B is a subset of A, (expressed different: B ⸦ A). Then,

A ![inline image](bilder/EQ_006.png)B = B and equation 1 implies P(A) = P(B) + P(A ![inline image](bilder/EQ_006.png)B^c).

Since P(A ![inline image](bilder/EQ_006.png)B^c) ⩾ 0 , it implies P(A) – P(B) = P(A ![inline image](bilder/EQ_006.png)B^c) ⩾ 0.

4  If A, B are any events such that B ⸦ A, then P(A) ⩾ P(B)

In general, for any two events A and B, if P(A) > P(B), then event A has more chance of occurrence compared to event B and vice versa. In view of this, equation 4 makes perfect sense, since B is a subset of A, the outcomes in B are also in A, so if B occurs that means A has also occurred. But A has few more outcomes which are not in B, so if any of those outcomes occurs the event A takes place, but not the event B. So, A has higher probability of occurrence.

Finally, for any event B, B is a subset of Ω. So, if we take A = Ω in equation 4, it implies 1 = P(Ω) ⩾ P(B). In other words, the probability of any event is less than or equal to 1.

We now look into few examples to see how these results can be used in real-life problems.

#### Labeled Balls in a Basket

Let’s consider the following random experiment: A basket has ten balls labelled from 1 through 10. The balls labeled 1 through 6 are red and balls labelled 7 through 10 are white. A ball is picked up in random from the basket and its label is noted. We are interested to calculate probability of four events:

*   Event A: A red ball is pricked up with an even number in the label.
    
*   Event B: A red ball is pricked up with an odd number in the label.
    
*   Event C: A red ball is picked up.
    
*   Event D: A white ball is picked up.
    

What are the possible outcomes of this experiment? It could be any number between 1 to 10. This is the sample space, Ω = {1, 2, 3, 4, …, 9, 10}. Since this experiment has only finitely many outcomes, we can take the set of all subsets of Ω as the σ-field of events. So æ = {all B such that B ⸦ Ω}. It contains all 2^(10) subsets including individual outcomes, Ω and Ø. Let’s now look at the events:

*   A = {2, 4, 6}
    
*   B = {1, 3, 5}
    
*   C = {1, 2, 3, 4, 5, 6}
    
*   D = {7, 8, 9, 10}
    

Since two outcomes cannot occur simultaneously in one trial, so all the events with individual outcome: {1}, {2}, {3} … {9}, {10} are mutually exclusive. Also, all these individual outcomes are equally likely, for example, P(1) = P(2) = P(3) = .. = P(10) = p.

*   Now, 1= P(Ω) = P({1,2, 3, …, 10}) = P({1}) + P({2}) + .. + P({10}) = 10\*p
    
    \=> p = P(Ω)/10 = 1/10 = 0.1.
    
*   Then probability of event A, P(A) can be calculated as
    
    P(A) = P({2}U{4}U{6}) = P({2}) + P({4}) + P({6}) = 0.1 + 0.1 + 0.1 = 0.3.
    
*   Similarly, P(B) = P({1}) + P({3}) + P({5}) = 0.1 + 0.1 + 0.1 = 0.3.
    
*   Now, C = A U B, A and B are disjointed, so P(C) = P(A) + P(B) = 0.6.
    
*   Also, note that D = C^c, So P(D) = 1 – P(C) = 1 – 0.6 = 0.4.
    

In this experiment, the probability of picking up a red ball is 0.6 and that of a white ball is 0.4. Now if the experiment is slightly changed as below:

#### Unlabeled Balls in a Basket

The basket still contains 6 red and 4 white balls, but balls are no longer labeled. A ball is picked up at random and its color is noted down. We are interested to know the probability of a red ball being picked up.

Now there are only two possible outcomes, Red and White. So, Ω = {Red, White} and σ‐field of events, æ = {{Ø}, {Red}, {White}, Ω ={Red, White}}. Our event of picking up a red ball can be denoted as E = {Red}.

Now, what is the probability of the event E? Do you think the probability of picking up a red ball will change since we have removed the labels? It will not change, as the basic experiment is still the same. So as before, P({Red}) = 0.6. Similarly, probability of picking up a white ball, P({White}) = 0.4.

This example shows three interesting things:

*   Probability of all the outcomes need not be equal unless they are equally likely to occur.
    
*   Intuition plays a key role in deciding if outcomes are equally likely or not.
    
*   In this type of problem, we may assign probability of different outcomes based on their proportion in the total population and it can be justified with a detailed experiment of same nature which produces equally likely outcomes.
    

In the second example, unlabeled balls in a basket, intuition tells us that the probability of picking up a red ball is more, since there are more red balls. The proportion of red balls in the basket is 6/10 = 0.6 and that of white ball is 0.4. We can take them as the probability values and it can be mathematically justified using the detailed experiment of example one (balls in a basket), which produces equally like outcomes.

So far, we have discussed about experiments which produce discrete valued outcomes. But an experiment may result in outcomes which are continuous in nature. Let’s consider the following experiment, snapping a string.

#### Snapping a String

Consider a one-meter long string of uniform thickness, and let’s denote its endpoints as A and B. These end points are uniformly pulled apart until the string snaps into two pieces. Once it snaps, at point C, the length value (without unit, knowing that it is measured in meters) of the piece of the string with endpoints A and C are noted down as L. In this experiment, the string can theoretically snap at any point, so outcome could be any real number between 0 and 1. How many such outcomes are there? Infinite. If we want to know the probability that L is a particular value, say exactly 0.473, it will be very unlikely to happen, as there are many possible outcomes. Instead, we may ask questions like what is the probability that L lies between 0.4 and 0.5. Now, for a moment, let’s convert it to a problem with discrete outcome.

The experiment remains the same, but outcome is noted differently, the outcome is 0 if 0 ⩽ L < 0.1, outcome is 1 if 0.1 ⩽ L < 0.2 and so on, and finally outcome is 9 if 0.9 ⩽ L ⩽ 1. Adding the point L=1 to the last interval does not alter the probability, as this particular point has zero probability. Then there are total 10 outcomes, 0 to 9 and as per our assumption, all these outcomes are equally likely. The event that the length L lies between 0.4 and 0.5 now maps to the outcome 4. As computed in example 1, probability of this event is 0.1.

Let’s now look at the original problem with a continuous interval as the set of all possible outcomes. In this scenario, the probability of L lies between an interval will be ratio of the length of this interval to the length of the interval with all outcomes (the length of Ω). In our example, this turns out to be 0.1 = (0.5 – 0.4)/(1 – 0), as obtained above.

What does the σ-field look like? In this example, if we consider all subset of possible outcomes, it will be impossible to handle mathematically. Instead, we consider σ-field of all sub-intervals in Ω. Note that Ω itself is an interval of finite non-zero length. The measure theory, a branch of higher mathematics, ensures that if we consider such a σ‐field, there exists a measure P such that probability of any sub-interval I of Ω can be computed as (length of I)/(length of Ω). More generally, if the sample space Ω is a subset in n-dimensional Euclidean space having finite non-zero volume, then there exists a σ‐field with all sub-space of Ω having finite volume and a probability measure P such that probability of any such subspace I (I ⸦ Ω) can be computed as (volume of I)/(volume of Ω).

Three interesting points to be noted here.

*   If Ω has discrete values, it makes sense to look at individual outcomes for constructing events. But when Ω is a continuous space (be an interval, area, or volume), we consider similar dimensional subspaces of Ω as events, any lower dimensional subset has probability zero.
    
*   Although probability of an individual outcome is zero when Ω is continuous, but an outcome with zero probability do occur. In our example, once the string snaps it gives a specific value of L (length of the string with end points A and C), but probability of getting that particular value of L is zero. So, zero probability in continuous case implies it is very unlikely to happen, but not impossible.
    
*   The definition of probability does not say anything about nature of the sample space Ω, whether it has discrete or continuous values. So, the definition holds good for both the cases. The basic properties we derived based on this definition also holds good when Ω is continuous.
    

### 2.1.2    Conditional Probability and Independence

In random phenomenon, sometimes occurrence of one event influences chance of occurrence of another event. Let’s understand this concept with an example.

#### Two Tosses of a Coin

Let’s consider the experiment of tossing a fair coin twice and noting down the outcome. If we denote heads with H, tails with T and note down result of two tosses with these two letters one after another, first one indicating outcome of the first toss and second one indicating outcome of the second toss, then possible outcomes are HH, HT, TH and TT.

Ω = {HH, HT, TH, TT}. Since we have finitely many outcomes, we can take æ as the set of all possible subsets of Ω. If the coin is fare, all these 4 outcomes are equally likely and has probability 1/4 = 0.25, using similar logic of example one (balls in a basket). So:

*   A = Event that first toss results in heads. Then A = {HH, HT}
    
*   B = Event that first toss results in tails. Then B = {TH, TT}
    
*   C = Event that both the tosses result in heads. Then C = {HH}
    

Using similar logic of the labeled balls in a basket example, the probabilities of these events are:

*   P(A) = P({HH}) + P({HT}) = 0.25 + 0.25= 0.5
    
*   P(B) = P({TH}) + P({TT}) = 0.25 + 0.25= 0.5
    
*   P(C) = P({HH}) = 0.25
    

If we impose the condition that event A took place, how do we understand the probability of occurrence of C with respect to this condition? In other words, what is the probability that both tosses results in heads given that first toss resulted in heads?

Since first toss resulted in heads, only possible outcomes of the experiment are HH and HT. So, with the condition that event A took place, the sample space changes and new sample space, say Ω[new] contains these two possible outcomes only. Both of them are equally likely and has probability 0.5. Event C takes place if outcome HH occurs and probability of C now becomes 0.5. This is the conditional probability of event C given the condition that event A took place.

Similarly, if first toss results in T, then there is no outcome which can provide event C = {HH}. So, the probability of both the tosses result in heads given the condition that first toss resulted in tails is zero. In other words, conditional probability of event C becomes zero given the condition that event B took place.

In this example, the probability of event C changed when we imposed condition that another event took place. This is known as conditional probability.

Let A and B are two events on the same probability space (Ω, æ, P) such that P(A) > 0. Then the conditional probability of B given A, denoted as P(B | A), is defined as

P(B | A) = P(B ![inline image](bilder/EQ_006.png)A) / P(A)

If P(A) = 0, the conditional probability of B given A is undefined.

Let A and B are two events on same probability space with P(B), P(A) > 0. Now P(B | A) = P(B ![inline image](bilder/EQ_006.png)A) / P(A).

 
| 1  || This implies P(B ![inline image](bilder/EQ_006.png)A) = P(A)P(B | A) |
| --- | --- |

Also, P(A | B) = P(B ![inline image](bilder/EQ_006.png)A) / P(B) (note that A ![inline image](bilder/EQ_006.png)B = B ![inline image](bilder/EQ_006.png)A).

Now if we use the equation 1 to substitute the value of P(B ![inline image](bilder/EQ_006.png)A), we have,

 
| 1  || P(A | B) = P(A)P(B | A) / P(B) |
| --- | --- |

This is a simpler version of Bayes’ Rule and it has many applications in Bayesian Statistics and machine learning. If event A is a possible cause of event B, then equation 2 can be interpreted as probability that event A is a cause of B given that B has occurred.

Note that in example 2, P(C | A) > P(C) and P(C | B) < P(C), so the conditional probability may be greater than or less that the actual probability without the conditions.

What if two events A and B are such that P(B | A) = P(B)? Then the condition that the event A took place does not alter the probability of B and this special case is known as independence. Note that in this case,

P(B ![inline image](bilder/EQ_006.png)A) / P(A) = P(B) and it implies P(B ![inline image](bilder/EQ_006.png)A) = P(A)P(B).

Also, note that if P(B ![inline image](bilder/EQ_006.png)A) = P(A)P(B) and P(A) > 0, then it implies,

P(B ![inline image](bilder/EQ_006.png)A) / P(A) = P(B), or, P(B | A) = P(B).

Let A and B are two events on the same probability space (Ω, æ, P). The events A and B are said to be independent if and only if

P(B ![inline image](bilder/EQ_006.png)A) = P(A)P(B).

Note that it allows zero values of P(A) or P(B).

If events A and B are independent and P(A) > 0, P(B) > 0, then,

P(B ![inline image](bilder/EQ_006.png)A) = P(A)P(B) => P(B ![inline image](bilder/EQ_006.png)A) / P(A) = P(B), or, P(B | A) = P(B).

Also,

P(B ![inline image](bilder/EQ_006.png)A) = P(A)P(B) => P(B ![inline image](bilder/EQ_006.png)A) / P(B) = P(A), or, P(A | B) = P(A).

We may interpret it as: if A and B are independent, occurrence of one of the events does not have any influence on the occurrence of the other event.

Let’s consider the same experiment as in coin tossing example. The sample space Ω = {HH, HT, TH, TT}. Note that these four outcomes are disjointed and equally likely. Two events A and B are defined as:

*   A = First toss results in heads. Then A = {HH, HT}.
    
*   B = Second toss results in heads. Then B = {HH, TH}.
    

Using similar logic of example one (balls in a basket):

*   P({HH}) = P({HT}) = P({TH}) = P({TT}) = ¼ = 0.25.
    
*   P(A) = P({HH}) + P({HT}) = 0.25 + 0.25 = 0.5.
    
*   P(B) = P({HH}) + P({TH}) = 0.25 + 0.25 = 0.5.
    

Now A ![inline image](bilder/EQ_006.png)B = {HH}, so P(A ![inline image](bilder/EQ_006.png)B) = P({HH}) = 0.25.

So, P(A ![inline image](bilder/EQ_006.png)B) = 0.25 = (0.5)(0.5) = P(A)P(B) => A and B are independent. Intuitively, this should be the case as the outcome of first toss should not have any influence on outcome of the second toss and vice versa.

We may extend the concept of independence for more than two events also. Let A, B, C are three events on the same probability space, then they are said to be pairwise independent if any two of these events are independent. In other words, A and B, B and C, C and A are independent. As per our definition, three events A, B, C are mutually independent if:

*   P(A ![inline image](bilder/EQ_006.png)B) = P(A)P(B)
    
*   P(B ![inline image](bilder/EQ_006.png)C) = P(B)P(C)
    
*   P(C ![inline image](bilder/EQ_006.png)A) = P(C)P(A).
    

But does it guarantee P(A ![inline image](bilder/EQ_006.png)B ![inline image](bilder/EQ_006.png)C ) = P(A)P(B)P(C)? In general, this is not the case and if it happens, it is a stronger condition of independence.

We say three events A, B, C are mutually independent if they are pairwise independent and if P(A ![inline image](bilder/EQ_006.png)B ![inline image](bilder/EQ_006.png)C ) = P(A)P(B)P(C).

More generally, if A[1], A[2], A[3], …, A[n] are n events on the same probability space, then they are mutually independent if both the following conditions hold true:

*   P(A[1] ![inline image](bilder/EQ_006.png)A[2] ![inline image](bilder/EQ_006.png)A[3] ![inline image](bilder/EQ_006.png)… ![inline image](bilder/EQ_006.png)A[n]) = P(A[1])P(A[2])P(A[3])…P(A[n])
    
*   Any collection of two or more of these events but fewer than n events are also mutually independent.
    

This is a recursive way of defining mutual independence.

### 2.1.3    Random Variables

In a random experiment, we are often interested to know the outcome in terms of numbers, e.g. number of total heads in two successive tosses, sum of the number obtained in two successive rolling of a dice. Converting the outcomes of a random experiment to a number helps us to easily state the events and associated probabilities. We have already adopted this approach without giving any special name to it. In the labeled balls in the basket example, we actually noted down the number of the label in the ball. In the string snapping example, we talked about length of one part of the string once it snapped and it is again a number. In all these examples, we mapped the outcome of an experiment to a number. Now let us look into it more closely.

Recall that for any random experiment, we have already given a mathematical model, the probability space, denoted by (Ω, æ, P) where Ω is the set of all outcomes, æ is the set of subsets of Ω known as events and a probability measure P on æ. Now, the set Ω is abstract in nature. If we consider a mapping from elements of Ω to real numbers, we can define the events and associate probabilities in terms values of this mapping.

X : Ω → R is one such mapping where R indicates the real numbers. Then, for any outcome ω in Ω, X(ω) is a real number. Multiple outcomes may map to the same value of X. Now suppose x is one such value of X. If the set of all outcomes for which X has the value x, mathematically denoted as {ω ∊ Ω : X(ω) = x}, is an event, then we can talk about the probability of X having the value x. In other words, P({ω ∊ Ω : X(ω) = x}) can be computed. For simplicity, we denote it as P( X = x).

Can we compute the probability P( X = x) for any value x? In other words, is the set {ω ∊ Ω : X(ω) = x} is an event for any value x of X? If this is the case, then we can shift probability space of the random experiment with this mapping and still talk about events and probabilities. This mapping has a special name, it is called a random variable, since its values originate from a random experiment.

If Ω has only finite or countably infinite outcomes, then for any value x of X, the set {ω ∊ Ω: X(ω) = x} is anyway a subset of Ω (it could be Ø as well) and it is included in the set of events æ. But if Ω has continuous values of outcomes, then not all subsets of Ω is an event, only the sets which are finite or countably infinite union of intervals are events. So, in order to define the mapping X in such a way that we can talk about P(X = x), we allow only such mapping where this is true and define it accordingly.

#### Discrete Random Variable

A real valued function X on a probability space (Ω, æ, P) is called a discrete random variable if X is a function from Ω to a subset of R (real numbers) having only finite or countably infinite values, say {x[1], x[2], x[3],…} such that the sets {ω ∊ Ω: X(ω) = x[i]} are events for all values of i.

#### Continuous Random Variable

A real valued function X on a probability space (Ω, æ, P) is called a continuous random variable if X is a function from Ω to R (real numbers) such that the sets {ω ∊ Ω: -∞ < X(ω) ⩽ x} are events for all values of x.

Let’s look at the following example to clarify the concept.

#### Three Tosses of a Coin

A fair coin is tossed three times and the outcome is noted like HHH, HHT, … as in previous coin tossing example (two tosses of a coin). Let X denotes the total number of Heads in the outcome. We may consider all outcomes are equally likely. The possible outcomes, probability of each outcome and the value of X is given in [Table 2.1](#02_001.html#t2.1).

 
| Outcome || Probability || Value of X (number of heads) |
| --- | --- | --- |
| HHH || 1/8 || 3 |
| --- | --- | --- |
| HHT || 1/8 || 2 |
| HTH || 1/8 || 2 |
| HTT || 1/8 || 1 |
| THH || 1/8 || 2 |
| THT || 1/8 || 1 |
| TTH || 1/8 || 1 |
| TTT || 1/8 || 0 |

**Table 2.1**    Three Coin Tosses

As before, note that individual outcomes are mutually exclusive. Now let us compute probabilities using the random variable X. For this, we consider all outcomes which are resulting to that value of X:

*   P(X = 3) = P({HHH}) = 1/8
    
*   P(X = 2) = P({HHT, HTH, THH}) = P({HHT}) + P({HTH}) + P({THH}) = 1/8 + 1/8 + 1/8 = 3/8
    
*   P(X = 1) = P({HTT, THT, TTH}) = P({HTT}) + P({THT}) + P({TTH}) = 1/8 + 1/8 + 1/8 = 3/8
    
*   P(X = 0) = P({TTT}) = 1/8
    

What is P(X = 5)? Well, how many outcomes are there for which X = 5? There are none! So P(X = 5) = P({Ø}) = 0.

So, in this example, X is a random variable with only 4 possible values, 3, 2, 1, 0. We can compute the probability of X having these values and for all other values, the probability is zero. X is a discrete random variable.

What is the probability of X < 2, i.e., P(X < 2)?

P(X < 2) = P({ω ∊ Ω: X(ω) < 2}) = P({HTH, THT, TTH, TTT})

\= P (HTT}) + P (THT}) + P (TTH}) + P({TTT}) = 1/8+1/8+1/8+1/8 = 0.5

Note that the if we denote the events A = {ω ∊ Ω: X(ω) = 1} and

B = {ω ∊ Ω: X(ω) = 0}, then A and B are mutually exclusive and

{ω ∊ Ω: X(ω) < 2} = A U B.

So, P({ω ∊ Ω: X(ω) < 2}) = P(A) + P(B) = 3/8 + 1/8 = 0.5

That is, P(X < 2) = P(X = 1) + P(X = 0).

This example shows two important concepts on random variables:

*   The events now can be defined in terms of random variable X. So, all the properties of probabilities we derived in previous chapters will be applicable in context of the random variable X.
    
*   If S is an arbitrary subset of real numbers (S ⸦ R), then how we can derive the probability that X takes values in S. This is computed as P(X ∊ S) = P({ω ∊ Ω: X(ω) ∊ S}). In this example, we took S = (-∞, 2) and computed P(X ∊ (-∞, 2)), i.e., P(X < 2).
    

There could be multiple random variables on the same probability space and we may be interested to know the probabilities involving them together. Let X and Y are two random variables on the same probability space and A and B are two subsets of real numbers. Then,

P(X ∊ A, Y ∊ B) = P({ω ∊ Ω: X(ω) ∊ A and Y(ω) ∊ B })

#### Three Tosses of a Coin, Continued

Let’s consider the same coin tossing experiment as before. Here:

*   X = Total of heads. As before, it takes values 3, 2,1, 0.
    
*   Y = 1 if first toss results in heads, Y = 0 if first toss results in tails.
    
*   Z = 1 if second toss results in heads, Z = 0 if second toss results in tails.
    

[Table 2.2](#02_001.html#t2.2) shows the outcomes, probabilities, and values of these variables.

 
| Outcome || Probability || Value of X || Value of Y || Value of Z |
| --- | --- | --- | --- | --- |
| HHH || 1/8 || 3 || 1 || 1 |
| --- | --- | --- | --- | --- |
| HHT || 1/8 || 2 || 1 || 1 |
| HTH || 1/8 || 2 || 1 || 0 |
| HTT || 1/8 || 1 || 1 || 0 |
| THH || 1/8 || 2 || 0 || 1 |
| THT || 1/8 || 1 || 0 || 1 |
| TTH || 1/8 || 1 || 0 || 0 |
| TTT || 1/8 || 0 || 0 || 0 |

**Table 2.2**    Three Coin Toss

Let’s take a look:

*   P(Y = 1) = P({HHH, HHT, HTH, HTT}) = 4 x 1/8 = 0.5. Similarly, P(Y = 0) = P(Z = 1) = P(Z =0) = 0.5. As before, P(X =2) = 3/8 = 0.375.
    
*   P(X = 2, Y = 1) = P({HHT, HTH}) = 1/8 + 1/8 = 0.25.
    

Note that P(X = 2,Y = 1) = 0.25 > P(X = 2)P(Y = 1) = (0.5)( 0.375) = 0.1875

P(Y =1, Z = 1) = P({HHH, HHT}) = 1/8 + 1/8 = 0.25.

Note that P(Y =1, Z = 1) = 0.25 = P(Y = 1)P(Z = 1) = (0.5)(0.5).

So, the notion of conditional probability and independence can be brought to random variables as well. We will discuss more on this in [Section 2.1.4](#02_001.html#h2.1.4).

Before we move to the next chapter, let’s look at a real-life example and link the concepts we have learned so far. In the following example, we will not compute the probabilities but will see how these concepts are used.

#### Bank Loans

Let’s consider a bank is giving loans to its customers for a repayment period of 5 years. There is a chance that some of the customers will be defaulters. The bank wants to reduce the risk, hence interested to know which customers have higher probabilities to default. A customer defaults based on many factors, let’s consider three of them:

*   The amount of loan
    
*   Income of the customer
    
*   The socio-economic background
    

Let’s consider the bank has historical data of customers on these three factors and whether they defaulted. As a machine learning consultant, you need to estimate the probability that a new customer will default based on the historical data.

Clearly, this is a problem in the domain of probability. For simplicity, let’s consider that bank provides you with the data with following columns:

*   A: Customer number.
    
*   B: Loan amount in few categories, say, with values low (< $50,000), medium ($50,000 < loan amount ⩽ $5,000,000) and high (> $5,000,000).
    
*   C: Income category, with values low (< $50,000), medium ($50,000 < income ⩽ $2,000,000), high ($2,000,000 < income < $5,000,000) and very high (> $5,000,000)
    
*   D: Educational qualification, say, with values P – primary school, H – high school, G – graduate and PG – postgraduate.
    
*   E: Whether the customer repaid the loan, 1 implies repaid, 0 implies defaulter.
    

Now, how do you approach to this problem? You do not have full information on all customers who paid back and who defaulted in all banks over all times. You only have a sample data. Also, you cannot be 100% sure whether a new customer will default, you can only calculate probability of a customer being a defaulter given information on other factors.

So, you may turn this problem into a probability problem and consider record of individual customers as outcome of a random experiment, with outcome (b, c, d, e) where b, c, d, e are values of the fields B, C, D, E respectively for each customer. The random experiment is to give loan of amount b to a customer with income category value c, educational background value d and observing his status e after five years. Then, you may calculate the probability that a customer will default given a set of values of his loan amount, income and educational background.

So, in this case, Ω = Set of all possible values (b, c, d, e). Let’s consider on this probability space, we have following four random variables:

*   X[1] is the random variable showing the loan amount of an individual.
    
*   X[2] is the random variable showing the income category of an individual.
    
*   X[3] is the random variable showing the educational qualification of an individual and
    
*   X[4] is the random variable showing his repayment status.
    

Suppose a new post graduate customer with medium income applies for a loan of $2,000,000 (medium loan amount).

You need to calculate conditional probability P( X4 = 0 | X1 = medium, X2 = medium, X3 = PG). You may also be interested to know if educational background really has an impact on loan repayment. In other words, whether the random variables X3 and X4 are independent.

This is how you may use the concepts of this chapter to frame this problem. In this particular case, since you have only a sample, you cannot compute these probabilities directly, rather you have to estimate them based on data. There are various machine learning algorithms which can be applied for this purpose and we will discuss about them in details in [Section 2.3](#02_003.html#h2.3).

### 2.1.4    Density and Distribution Function

So far, the examples we have seen, the individual low-level outcomes are equally likely and we can easily determine their probabilities. But it is not the case always. In most real-life problems, the outcomes are not equally likely, and it is not easy to directly calculate them. If X is a discrete random variable, then we have seen in the previous chapter that P(X ∊ S) = P({ω ∊ Ω: X(ω) ∊ S}), where S is a subset of R. Also, since X is discrete valued, there are finitely or countably infinite values of X, say {x[1], x[2], x[3], ….} which fall in S. Since same outcome cannot be mapped to two different values of X (as per the definition of a function, a value in the domain of definition can be mapped to only one value in the range, but one value in the range may have multiple values in the domain which are mapped to this value), if x[1] and x[2] are any two arbitrary values of X, the events {ω ∊ Ω: X(ω) = x[1]} and {ω ∊ Ω: X(ω) = x[2]} are mutually exclusive, the same ω cannot be mapped to two different values of X.

P(X ∊ S) = P({ω ∊ Ω: X(ω) ∊ S }) = P({ω ∊ Ω: X ∊ {x[1], x[2], x[3], ….})

\= P ({ω ∊ Ω: X(ω) = x[1]} ∪ {ω ∊ Ω: X(ω) = x[2]} ∪…. )

\= P({ω ∊ Ω: X(ω) = x[1]}) + P({ω ∊ Ω: X(ω) = x[2]}) + …. (as each of the events are mutually exclusive, probability is summed up)

\= P(X = x[1]) + P(X = x[1]) + ….

If X is a discrete valued random variable and if S = {x[1], x[2], x[3], ….} is a subset of R, then P(X ∊ S) = ∑[x ∊ S]P(X = x). In other words, sum of all the values of the form P(X = x[i]). This motivates us to give a special name of the values P(X = x). This is called the density function of X and is defined as

A real valued function f on R defined by f(x) = P(X= x) is called a discrete density function of the random variable X.

As we have just seen, P(X ∊ S) = ∑[x ∊ S]P(X = x) = ∑[x ∊ S] f(x). Lets look at an example now.

In the example of tossing a coin three times, we have seen that the random variable X (sum of number of heads if a fair coin is tossed thrice) takes 4 possible values { 3, 2, 1, 0} and computed the associated probabilities. Then if f(x) is a density function of X,

f(3) = P(X = 3) = 1/8

f(2) = P(X = 2) = 3/8

f(1) = P(X = 1) = 3/8

f(0) = P(X = 0) = 1/8 and

f(x) = 0 for all other values x ∊ (-∞, +∞)

The advantage of introducing discrete density function f(x) is that often it takes nice mathematical form based on the value of x and it is easier to deal with them.

Next, we investigate continuous random variables and see how we may introduce a similar concept. For continuous random variables, we look into probabilities that value of X falls within an interval. But here also, as in discrete case, the probabilities that X takes values in different intervals may not be equally likely and calculating probability for all possible intervals will be extremely difficult. Let’s consider the following example.

#### Height Probability

Suppose you are working on a medical research and interested to know the probability of a person having height between 4 and 5 feet. For this, you need to know probability of different height values in that population. Clearly, different height values are not equally likely, there is a higher probability that a person has height between 5 feet to 6 feet than they are taller than 7 feet. Also, you cannot measure height of all people in the population. So how to address this problem?

Instead of directly calculating the probabilities, here we may estimate the probability based on a sample. Recall the relative frequency interpretation of probability, which says if the random experiment is repeated for n times and n[1], n[2], … are frequency (number of occurrences) of different outcomes, then n[1]/n, n[2]/n, … tend to the probabilities of the outcomes as n tends to ∞. In reality, we do not need n to be very large, a moderate size of sample outcome data could be enough to estimate these probabilities.

We may take a random sample of 200 people, with an assumption that they represent the population. Then we measure their height to get the relative frequency of different height values. This will be an estimate of the probability of different height values in the population. At the background, we may consider it as a random experiment that selects a person randomly from population and notes down their height as the outcome. We can consider a random variable X on this sample space which denotes height of the person.

In this hypothetical experiment, let’s assume that we collected the data of 200 persons. Note that height can take any real value within an interval, so this is a case of continuous random variable. But at first, let’s see how it looks like when data is collected with intervals of 1 foot. Also, let’s merge the intervals less than or equal to 3 feet into one interval and greater than 8 feet into another interval. [Figure 2.1](#02_001.html#f2.1) shows the data and the plot of relative frequency.

[![Relative Frequency of Height of 200 People when Collected at Intervals of One Foot](bilderklein/klein02_001.png)](img-f2.1.html) 

**Figure 2.1**    Relative Frequency of Height of 200 People when Collected at Intervals of One Foot

Next, let’s see how data looks like when collected at intervals of 0.5 feet. The data and relative frequency plot are shown in [Figure 2.2](#02_001.html#f2.2).

[![Relative Frequency of Height of 250 People when Collected at Intervals of 0.5 Feet](bilderklein/klein02_002.png)](img-f2.2.html) 

**Figure 2.2**    Relative Frequency of Height of 250 People when Collected at Intervals of 0.5 Feet

If we continue dividing the intervals more and more, we observe that relative frequency diagram tends to a smooth curve, as shown in [Figure 2.3](#02_001.html#f2.3), where left graph has intervals of 0.25 feet and right graph has interval of 0.125 feet.

[![Relative Frequency Tends to a Smooth Curve when Intervals are Successively Reduced](bilderklein/klein02_003.png)](img-f2.3.html) 

**Figure 2.3**    Relative Frequency Tends to a Smooth Curve when Intervals are Successively Reduced

This provides a hint to how we can calculate probability in case of continuous random variable. Note that for any arbitrary interval, say 3.62 feet to 4.73 feet, we can add the relative frequencies of the subintervals within that interval to calculate the relative frequency for that interval. As per the graph, this is same as adding up values of the vertical lines within the interval. But if we continue subdividing the intervals, plot the relative frequencies for these smaller and smaller intervals and add them up, in the limiting case the vertical lines will be very dense and sum of the values of these vertical lines will be same as finding the area under the curve within that interval. [Figure 2.4](#02_001.html#f2.4) illustrates this concept.

[![Calculation of Probability as Area Under the Curve](bilderklein/klein02_004.png)](img-f2.4.html) 

**Figure 2.4**    Calculation of Probability as Area Under the Curve

Now, calculating area under the curve is same as integrating the curve function on the interval (a , b\]. If this curve function is f(x), then,

P(a < X ⩽ b) = ![inline image](bilder/EQ_008.png)

Few important points to be noted from this example:

*   The relative frequencies provide a good estimate of probabilities as sample size is high.
    
*   Often the relative frequencies (estimated probabilities) tend to a smooth function if intervals are divided successively
    
*   In such scenarios, the smooth function provides a good estimate of probabilities and probability that X falls in an interval can be computed as integrating the smooth function over that interval.
    

This function is precisely the analogy of density function for continuous random variables. Note that in discrete case we added the function on possible discrete values, but in continuous case it is integration over an interval.

#### Density Function

A real valued function f on R is called a density function of a continuous random variable X if P (a < X ⩽ b) = ![inline image](bilder/EQ_008.png)for any interval (a , b\] of R.

In general, if any function satisfies ![inline image](bilder/EQ_009.png), we can construct a sample space and a random variable X such that f(x0 is the density function of X.

Finally, let’s introduce one more function which is often very useful for calculating probabilities.

#### Distribution Function

A real valued function F on R defined by F(x) = P(X ⩽ x) is called a distribution function of the random variable X.

Note that it equally applies for both discrete and continuous random variables. For continuous case, we may not have a density function, but distribution function always exists.

If X is a discrete random variable with discrete density function f(x), then,

![inline image](bilder/EQ_010.png)and,

P(a < X ⩽ b) = P(X ⩽ b) – P(X ⩽ a) = F(b) – F(a) = ∑[a <x ⩽ b] ^() f(x) .

If X is a continuous random variable with density function f(x), then,

![inline image](bilder/EQ_011.png)and,

P(a < X ⩽ b) = P(X ⩽ b) – P(X ⩽ a) = F(b) – F(a) = ![inline image](bilder/EQ_012.png).

Since F(b) – F(a) = ![inline image](bilder/EQ_012.png), from elementary calculus, F ́(x) = f(x). In other words, f(x) is the derivative of F(x). Note that this derivative of distribution function may not always exist. But if it exists, we can take this function and calculate the probabilities using integration.

The notion of density function can be extended to joint probability of multiple random variables X[1], X[2], .., X[n] on the same probability space, called the joint probability density function as:

1.  For discrete random variables, if there exist a function f(x1, x2, ..xn) such that P(X[1] = x[1], X[2] = x[2], .., X[n] = x[n]) = f(x[1], x[2], ..x[n]) and
    
2.  For continuous random variables, if there exists a function f(x1, x2, ..xn) such that P(a[1] <X[1] ⩽ b[1], a[2]<X[2] ⩽ b[2], …., a[n] <X[n] ⩽ b[n]) = ![inline image](bilder/EQ_013.png)
    

The notion of independence can be also defined in terms of density functions, the random variables X[1], X[2], .., X[n] are independent if their joint density function is a product of individual density functions.

The density functions are widely used in probability and they show nice mathematical properties. One of the most important density functions is normal or Gaussian density function, which is observed in many natural phenomena. The density of the height probability example is also a normal density function and it has been observed that many things like height, weight, scores where multiple factors are involved follow normal distribution. We conclude this topic with a list of some famous density functions in [Table 2.3](#02_001.html#t2.3).

 
| Name || Density Function || Associated Parameters || Type |
| --- | --- | --- | --- |
| Binomial || ![inline image](bilder/EQ_Tab2-3_001.png) || n, p || Discrete |
| --- | --- | --- | --- |
| Poison || ![inline image](bilder/EQ_Tab2-3_002.png) || λ || Discrete |
| Geometric || f(x) = p(1 – p)^(x – 1)  
(if x\-th trial has the first success) || p || Discrete |
| Normal || ![inline image](bilder/EQ_Tab2-3_004.png) || μ, σ || Continuous |
| Exponential || f(x) = λe^(\-λx) for x ⩾ 0, � 0 otherwise || λ || Continuous |
| Gamma || ![inline image](bilder/EQ_Tab2-3_006.png) || λ, α || Continuous |

**Table 2.3**    Some Famous Probability Density Functions

### 2.1.5    Expectation

Suppose a discrete random variable X takes different values {x[1], x[2], …} with a density function f(x). Note that these different values of X are linked to a random experiment at the background. If this experiment is continued for multiple times, what will be the average value of X taken over all such repetition of the experiment? Let’s consider the experiment is continued n times and x[1] is observed n[1] times, x[2] is observed n[2] times and so on. Then the average of these observed values of X is given by

(x[1]n[1] + x[2]n[2] + …..)/n = x[1](n[1]/n) + x[2](n[1]/n) + … .

Note that, if X has infinite outcomes, this average may not be finite. In other words, it may tend to infinity. However, if it converges to a finite number, then, this value tends to x[1]P(X = x[1]) + x[2]P(X = x[2]) +…, in other words, this value tends to x[1]f(x[1]) + x[2]f(x[2]) + ….. = ![inline image](bilder/EQ_014.png). This value is known as the expectation of X, denoted as E(X). It is also called mean.

In analogy with discrete case, for a continuous random variable X with density f(x), the expectation of X is defined as:

E(X) = ![inline image](bilder/EQ_015.png)if the integral ![inline image](bilder/EQ_016.png)< ∞

If ![inline image](bilder/EQ_016.png)is not finite, then we say E(X) does not exist.

Let’s consider the random variable X in a previous example (sum of number of heads when a fair coin is tossed thrice). Here, X takes 4 values; 0, 1, 2, 3 with probabilities 1/8, 3/8, 3/8 and 1/8 respectively. Then,

E(X) = ![inline image](bilder/EQ_014.png)\= (0)(1/8) + (1)(3/8) + (2)(3/8) + (3)(1/8) + 0 = 12/8 = 1.5

The last term with zero value added to emphasize that for all other values of X, f(x) = 0, so they contribute zero to the sum.

Note that although X is random variable that can take many possible values, E(X) is a constant value if it exists. Typically, it represents the center of gravity if we consider a mass of f(x) put at a value x on the real line.

Let’s now look at few important properties of expectation:

*   If X and Y are two random variables on the same probability space with having finite expectation, then the random variable Z = X + Y also has finite expectation and E(Z) = E(X) + E(Y).
    
*   If P(X ⩾ Y) = 1. In other words, for every outcome ω, X(ω) ⩾ Y(ω), then E(X) ⩾ E(Y).
    
*   If c is a constant, we may consider it as a random variable which takes value c with probability 1. Then with this understanding, E(c) = c. So, expected value of a constant is the same value.
    
*   The above point indicates E(E(X)) = E(X), since E(X) is a constant.
    
*   If c is a constant, E(cX) = cE(X).
    
*   | E(X) | ⩽ E(|X|).
    
*   If X and Y are independent random variables on the same probability space having finite expectation, then XY has finite expectation and E(XY) = E(X)E(Y).
    

### 2.1.6    Variance and Standard Deviation

The mean or expectation of a random variable X provides the average value of X if the random experiment is repeated multiple times. This represents the central tendency of a distribution. But while understanding nature of a distribution, it is also important to understand the spread of the distribution. This is called variance: let X be random variable with finite value of E(X²). Then variance of X, denote by Var(X) = E((X – E(X))²).

Note that the term X – E(X) is the distance between different values of X from E(X), the expected value of X. This could be positive or negative. So if we take average of them, they may cancel each other. Hence, (X – E(X))² is considered which will always be positive. The expected value of this is the variance of X and is a measure of how the distribution of X spread across the expected value of X.

The quantity ![inline image](bilder/EQ_017.png)is known as standard deviation.

Note that using properties of expectation,

Var(X) = E((X-E(X))²) = E(X² – 2XE(X) + (E(X))²)

\= E(X²) – 2E(X)E(X) + E((E(X))²)

\= E(X²) – 2(E(X))² +(E(X))²

\= E(X²) – (E(X))²

Due to this, we assumed finite value of E(X²) in the definition. Like expectation, variance also may not exist for some random variable.

If X and Y are two random variables each having finite variance. Then:

Var(X + Y) = E((X+Y)²) – (E(X+Y))² = E(X² + 2XY + Y²) – (E(X) +E(Y))²

\= E(X²) + E(2XY) + E(Y²) – E(X)² – 2E(X)E(Y) – E(Y)²

\= \[E(X²) – E(X)²\] + \[E(Y²) – E(Y)² \] + E(2XY) – 2 E(X)E(Y)

\= Var(X) + Var(Y) + 2\[E(XY) - E(X)E(Y)\]

The variance of sum of two random variables is not the sum of their variances in general, it contains one more term. The term E(XY) - E(X)E(Y) has a special interpretation, it is called covariance between X and Y, we will formally define it in the next section.

If X and Y are independent, then E(XY) = E(X)E(Y) i.e, E(XY) - E(X)E(Y) = 0. In that case the we have Var(X + Y) = Var(X) + Var(Y).

In general, if X[1], X[2], .., X[n] are mutually independent variables, then ![inline image](bilder/EQ_018.png).

### 2.1.7    Covariance and Correlation

When we have two random variables, we may be interested to know how much two variables vary together. Covariance is a measure for this purpose and defined as the following:

Let X and Y be two random variables with finite expectations. Then covariance between X and Y, denote by Cov(X, Y) is defined as Cov(X, Y) = E((X – E(X))(Y – E(Y)).

Note that Cov(X, Y) = E((X – E(X))(Y – E(Y)))

\= E(XY – YE(X) – XE(Y) + E(X)E(Y)))

\= E(XY) – E(Y)E(X) – E(X)E(Y) +E(E(X)E(Y))

\= E(XY) – 2E(X)E(Y) + E(X)E(Y)

\= E(XY) – E(X)E(Y)

If X and Y are independent, then E(XY) = E(X)E(Y). Consequently, Cov(X,Y) = 0. However, if Cov(X,Y) = 0, it does not mean X and Y are independent, it just tells that there is no linear relationship between X and Y.

If the value of X and Y increase or decreases together, then Cov(X, Y) is highly positive. If value of X decreases when value of Y increases and vice versa, then Cov(X, Y) is highly negative. However, covariance measures the linear relationship in absolute term, so difficult to compare covariance values for two sets of random variable pairs.

Correlation measures the linear relationship in relative term and is defined as the following:

Let X and Y be two random variables with finite variances. Then correlation coefficient between X and Y, denote by Cor(X, Y) is defined as Cor(X, Y) = ![inline image](bilder/EQ_019.png).

It can be shown that \[Cov(X,Y)\]² ⩽ Var(X)Var(Y), so correlation coefficient always lies between –1 and +1.

Like covariance, correlation coefficient is zero if X and Y are independent.

If X and Y has a perfect linear relationship the following is true:

*   values of both the variables increase and decrease together, then Cor(X,Y) = 1
    
*   when increase in value of one of them decreases the value of other, then Cor(X,Y) = –1.
    

Thus, it provides a good measure of linear relationship between X and Y.

Now that we’ve taken a look at basic probability concepts, let’s move on to basic machine learning concepts.

## 2.2    Basic Machine Learning Concepts

Machine learning is a vast branch of Artificial Intelligence that enables a system to learn from a sample data for discovering patterns within the data and making predictions. It utilizes various artificial intelligence algorithms and statistical methods for this purpose. The system learns from the available data in a systematic way and then utilizes the knowledge to apply them for specific tasks like prediction. Machine learning has applications in various fields like economics, business decision making, computer vision, speech recognition, image recognition, robotics automation, and digital games.

### 2.2.1    Different Types of Machine Learning Scenarios

Before going into the details of machine learning, let’s look at some of the scenarios where machine learning can be used. 

#### Fast-Moving Goods Company

Suppose a fast-moving goods company runs its marketing of their products across different channels, like advertisements in TV, advertisement in web media, and telemarketing. The company wants to understand which of these channels are most effective to increase the sales. Accordingly, they will allocate higher budget to that channel. One direct approach is to ask every customer how they discovered the product and what made them decide to purchase their products. However, this may not be feasible for various reasons: the retail stores may not be able to get answers from customers, customers may not be willing to answer the questions, and collected data may be unreliable.

How do we understand the relationship between sales and advertising costs spent across various channels? One indirect approach would be look at sales data and advertisement costs across different channels, analyze the data to see if it shows any relationship. Here, the main interest is to understand the relationship rather than making a prediction. Once this relationship is clear, then it can be even utilized to decide how much to spend across different channels to get a desired increase in sales.

#### Manufacturing Company

As a second example, let’s consider a manufacturing company develops products using sophisticated machine, the production line will stop if the machine breaks down and will cause huge loss. Bringing it back to running condition is a time taking activity and the production will completely stop during that time period. However, regular maintenance of the instrument takes less time, only few hours and ensures smooth running of the instrument, but it incurs a large cost. The company cannot run the servicing of the instrument on regular basis. So, the company is interested to know when the next maintenance to be done. The instrument breaks down due to various environmental factors like temperature, pressure, and hours of machine operation. So, if the past data of the instrument failure along with the environmental data is available, one possible approach will be to analyze the past data and predict when the instrument will fail again and perform a proactive maintenance few days before that. Here, the main interest is to predict an event.

#### Bank Issuing Loans

As third example, let’s consider a bank wants to understand if a new customer requesting for a loan will default or not. The customer is a first-time customer, so bank does not have any data on his past repayment history. However, the bank has considerable historical data on its customers on their income, occupation, education, and various other socioeconomic information which seems to have influence on loan repayment and whether they defaulted or not. The bank wants to use this data to understand whether the new customer will default, based on his demographic and socioeconomic data. Here, the problem is to predict the customer into one of two groups defaulter and non-defaulter.

#### Targeted Campaign

As fourth example, let’s consider that a company wants to have targeted campaign to its customers. This campaign is being organized for the first time, so the company does not have any information on how it influenced customers. The only information the company has is the type of products the customers purchased and value of the total sales in last two years. How the customers can be grouped into few segments for maximum benefit from the campaign?

#### Chess Computer

Finally, let’s consider one more example, where a computer program being designed to play chess with a human. It is not possible to provide the program with all the possible moves and counter moves, but the system will learn itself how to operate in such an environment. It will learn through outcome of the game.

All the above examples show different scenarios where machine learning can be used. If we closely look at these examples, we can see there are different types of problems to be addressed:

*   Fast-moving goods company  
    Identifying the relationship between a response and multiple influential factors.
    
*   Manufacturing company  
    Predicting a quantitative response based on associated data.
    
*   Bank issuing loans  
    Predicting a qualitative response based on associated data.
    
*   Targeted campaign  
    Revealing information from data without any prior knowledge.
    
*   Chess computer  
    Allowing the system to learn on its own through its interaction with environment.
    

These are some of the basic scenarios where machine learning operates. In the next section, we’ll see different machine learning types and how these scenarios relate to them.

### 2.2.2    Types of Learning

Depending on the types of problem and methods adopted for learning, there are different types of machine learning. The main types are described here:

*   Supervised learning  
    In supervised learning, the system learns through the training data containing a response or outcome and different influential factors or predictors. The idea is to relate the outcomes or target with the input or influential factors. It can be further subdivided into two broad categories:
    
    *   Regression  
        In regression problem, the response or outcome is quantitative (continuous in nature). They represent an entity which can take any value within a range. Some example of continuous response include sales amount, sales value, and survival probability.
        
    *   Classification  
        Here the response represents categorical data. A categorical data represents some classes or categories. Some example of categorical data include defaulter status, sex, and marital status.
        
*   Unsupervised learning  
    In unsupervised learning, we want to identify structures and hidden patterns within the data, so there is no response or outcome. In a way, unsupervised learning does not have any instructor or teacher, rather it learns on its own based on a data.
    
*   Semi-supervised learning  
    This is a mix of supervised and unsupervised learning. Here some of the data has response values, but majority of data do not have any response or outcome information.
    
*   Reinforced learning  
    Here the system learns thorough its interaction with the environment with a penalty and reward of the action and associated outcome. There is eventually no data to train the system, the system acts with the environment through actions and learns through feedback. The scenario of a computer agent playing chess is an example of reinforced learning.
    

## 2.3    Machine Learning Algorithms

In machine learning, the system learns through various algorithms from artificial intelligence and statistical methods. This section talks about some of the important and widely used algorithms for different types of machine learning to give an understanding how machine learning works and how to use these algorithms in real life problems, along with their advantage and disadvantages.

### 2.3.1    Linear Regression Analysis

Linear regression analysis is one of the very simple and widely used supervised learning methods. It has been there in the statistical data analysis for long and it is one of the many statistical methods adopted to the machine learning domain. This chapter discusses about the fundamental concepts of linear regression analysis and how it can be used for real-world problems. This chapter also shows some of the key considerations while applying a machine learning algorithm and serves as a good starting point, before we embark into more complex and sophisticated machine learning methods. We will also discuss about advanced and popular techniques like ridge regression and lasso in this chapter.

Before we formally define the linear regression model, let’s look at the following example. As a machine learning expert, you are supposed to find a relationship between price of a secondhand car against two different factors, age of the car, mileage per gallon of the car. We know that price of a used car usually decreases with age of the car and price usually increases with mileage of the car. But is there a strong evidence to call it a relationship? What is the nature of this relationship? Is it linear? How strong is the relationship between price and mileage? Which factor is more influential–price or mileage? How well the relationship can predict the price of a secondhand car? Linear regression could be a good starting point to investigate these questions. [Figure 2.5](#02_003.html#f2.5) shows a simulated data on these variables. [Figure 2.5](#02_003.html#f2.5) 1 shows age vs. price and [Figure 2.5](#02_003.html#f2.5) 2 shows mileage vs. price.

[![Price of Secondhand Cars Against Age and Mileage](bilderklein/klein02_005.png)](img-f2.5.html) 

**Figure 2.5**    Price of Secondhand Cars Against Age and Mileage

Linear regression analysis is used when we try to fit a model between a quantitative response (also known as dependent variable) against some predictors (also known as independent variables or explanatory variables) for understanding the nature of influence of the predictors over response and to predict the value of the response given a set of values of the predictors. Here we assume that value of the response can be reasonably estimated by a linear combination of the associated values of the predictors. More precisely, we try to fit a model

1  Y = β[0] + β[1].X[1] + β[2].X[2] + .. + β[p.]X[p] + Ɛ

or

2  y[i]\= β[0] + β[1].x[1i] + β[2].x[2i] + .. + β[p.]x[pi] + ε[i]

In equation 1, Y is the response (or dependent variable) and X[1], X[2], ..X[p] are the predictors (or independent variables). Ɛ is a random variable representing the error or noise in the model, which accounts for the errors due to measurement and/or due to missing out other influential variables in our model. The error term is assumed to have expected value 0 (E(Ɛ) = 0) and it is independent of the values of response variables, so that it does not show any systematic pattern of error. β[0], β[1], β[2],.., β[p] are some constant values, but they are unknown and they need to be estimated based on the available data. They are called regression coefficients or parameters. In our example, we can consider Y as the car price, X1 as the age and X2 as the mileage.

Equation 2 represents the same thing in terms of values of these variables. In the i-th record of the sample data, y[i] is the value of response Y and x[1i], x[2i], .., x[pi] are the corresponding values of predictor variables X[1], X[2], .., X[p]. The associated value of the error variable Ɛ is ε[i]. The left-hand side of the equation 2 represents the observed value of Y (given the values x[1i], x[2i], .., x[pi] of the corresponding predictor variables X[1], X[2], .., X[p]) and the right hand side shows a linear combination of the predictor values with some error term. Usually, the variables are represented with uppercase letters and the values are represented with corresponding lowercase letters, sometimes suffixed to indicate a general record in the sample.

###### Note

We only have a sample data on which we will estimate the relationship, in other words, estimate the values of β[0], β[1], β[2,].., β[p]; minimizing the error term. So, our estimate may vary depending on the sample data. How does one handle the situation? First, the sample data needs to be a representative sample of the overall scenario (often called the population). Still, estimates may differ based on data. The probability theory comes into play in such situations and can be effectively utilized to get a confidence interval of the parameters and the predicted values. We will highlight some of these scenarios without going into rigorous calculation of such probabilities, as it would require advanced knowledge of probability and not in the scope of this book.

#### Simple Linear Regression

Simple linear regression studies the linear relationship between a response variable Y and a single predictor variable X. The model can be mathematically represented as:

Y = β[0] + β[1].X + Ɛ

The parameter β[0] is called the intercept and β[1] is called the slope. They are unknown constants and need to be estimated based on the data.

###### Note

The equation of a straight line is y = m.x + c where c is the intercept (the value of y where the straight line meets Y axis) and m is the slope of the line (change in value of Y for one unit change in the value of X along the straight line). In simple linear regression, the relationship between Y and X is estimated through a straight line and the parameters β[0] and β[1] play the same role of intercept and slope of the straight line. This straight line is called the regression line. The term linear also came from this fact.

Let ![inline image](bilder/EQ_020.png)and ![inline image](bilder/EQ_021.png)are the estimated values of these parameters. Then the predicted or estimated value of y, denoted as ![inline image](bilder/EQ_022.png)is given by,

![inline image](bilder/EQ_023.png)

for the value of X = x. If y is the true value of Y for X = x, then the error in estimation is e = y – y = y - β[0] - β[1].x. This could be positive or negative. The [Figure 2.6](#02_003.html#f2.6) shows the regression lines for two such possible estimates of regression coefficients for the price vs. age data, the regression lines are marked as red lines. The error associated with respect to a regression line is the distance of the points along the Y axis from this line.

[![Possible Estimates of Regression Coefficients](bilderklein/klein02_006.png)](img-f2.6.html) 

**Figure 2.6**    Possible Estimates of Regression Coefficients

Which values of the regression coefficients should be chosen as the best estimates? Ideally, it should result in a regression line which is very close to all the observation points so that the associated errors are minimum. However, there are various ways to minimize the errors and most common approach is the least squares approach, where we try to minimize the sum of squared errors. Note that minimizing the sum of the errors is not optimal, since the positive and negative errors may cancel each other even though the absolute values of the individual errors may be large.

##### Estimation of Regression Coefficients

Let (x[1], y[1]), (x[2], y[2]), …, (x[n], y[n]) are n pairs of observations, each pair contains a value of predictor X and associated value of response Y. Let ![inline image](bilder/EQ_020.png)and ![inline image](bilder/EQ_021.png)are the estimated values of the regression coefficients. Then for the i-th pair of observations, ![inline image](bilder/EQ_025.png)is the estimated value of y[i] and the associated error is e[i] = y[i] – [![inline image](bilder/EQ_026.png)].

We define the residual sum of squares (RSS) as:

RSS = e[1]² + e[2]² + … + e[n]² = e

Or equivalently as:

RSS = (y[1] - ![inline image](bilder/EQ_020.png) +[] ![inline image](bilder/EQ_021.png). x[1])² + (y[2] - ![inline image](bilder/EQ_020.png) + ![inline image](bilder/EQ_021.png). x[2])² + … + (y[n] - ![inline image](bilder/EQ_020.png) + ![inline image](bilder/EQ_021.png). x[n])²

The least squares approach chooses ![inline image](bilder/EQ_020.png)and ![inline image](bilder/EQ_021.png)so that value of RSS is the minimum. Note that except for the value of ![inline image](bilder/EQ_020.png)and ![inline image](bilder/EQ_021.png), all other values are known, so this can be considered a function of two variables β[0] and β[1] which are minimized at ![inline image](bilder/EQ_020.png)and ![inline image](bilder/EQ_021.png). This means the partial derivatives of RSS against β[0] and β[1] are zero at the points ![inline image](bilder/EQ_020.png)and ![inline image](bilder/EQ_021.png). Using this result from calculus, we can get two equations and solution of these equations gives the following values of β[0] and β[1] that minimizes RSS.

![inline image](bilder/EQ_028.png)

![inline image](bilder/EQ_029.png)

Where ![inline image](bilder/EQ_031.png)and ![inline image](bilder/EQ_030.png), are the sample means.

[Figure 2.7](#02_003.html#f2.7) shows the regression line based on the least square estimate of the age vs. price data.

###### Note

In linear regression, the response variable is always quantitative. However, the predictors may be quantitative or categorical. In case of a categorical predictor X with m categories, we create (m-1) dummy or indicator variables X[1], X[2], .., X[m-1] as x[1i] = 1 if x[i] denotes first category, 0 otherwise.

Here x[1i] and x[i] denotes the value of X[1] and X respectively for the i-th record.

Similarly, we go on defining x[2i] = 1, if x[i] denotes second category, 0 otherwise, and finally x[(m-1)i] = 1, if x[i] denotes (m-1)-th category, 0 otherwise.

Note that if x[i] denotes m-th category, the value of all the dummy variables will be zero for the i-th record and can be easily identified.

These dummy predictors can be then used in the regression analysis along other predictors. The particular way of creating the dummy variables is not important and it does not change the overall regression analysis, but interpretation of the coefficients of dummy variables changes with different ways of creating the dummy variables.

In our example of used car price, if we introduce another predictor car type, with values hatchback, sedan, and SUV, then we may introduce two additional dummy predictors X[1] and X[2]:

*   x[1i] = 1 if car type is Hatchback, 0 otherwise
    
*   x[2i] = 1 if car type is Sedan, 0 otherwise
    

We can then use these predictors X[1] and X[2] along with other predictors for age and mileage.

In practice, we often use many categorical predictors like educational qualification, occupation, and more.

[![Least Square Fit for Regression of Price Over Age](bilderklein/klein02_007.png)](img-f2.7.html) 

**Figure 2.7**    Least Square Fit for Regression of Price Over Age

##### Assessing the Accuracy of the Estimates of the Regression Coefficients

As already discussed, we estimate the regression coefficients based on sample data. So, even if the true relationship between Y and X is perfect linear, we may not be able to estimate the true values of intercept and slopes accurately. A different sample may result in a slightly different values of the least square estimates of the regression coefficients. Accordingly, our predicted values of Y may also differ based on different training sets. How far these estimates ![inline image](bilder/EQ_020.png)and ![inline image](bilder/EQ_021.png)can vary and how can we measure them? Since we do not have all the data for our analysis, we cannot answer this question without some further assumptions. We take the following assumptions:

*   Weak exogeneity  
    This means the predictor variables can be treated as fixed values. These values have been measured error-free, so the error in the model is not due to error in predictors.
    
*   Homoscedasticity  
    Different realizations of the response variable have the same variance in their errors, irrespective of the values of the predictor variables.
    
*   Independence of errors  
    The errors terms are uncorrelated with each other.
    

Under these assumptions, we have the following formulas:

*   ![inline image](bilder/EQ_032.png)
    
*   ![inline image](bilder/EQ_033.png)
    

Where σ² = Var(Ɛ). The above assumptions may not be always valid, but the formula often turns out to be a good approximation. The value of σ² is not known in general, but can be estimated based on data using the formula RSS/(n-2).

Also, if we assume the errors are normally distributed, then an approximate 95% confidence interval of β[0] and β[1] can be given by ![inline image](bilder/EQ_034.png)and ![inline image](bilder/EQ_035.png)respectively, where t is the 97.5% quantile of a t-distribution with n-2 degrees of freedom. This means, the true value of β[0] falls within the interval ![inline image](bilder/EQ_036.png)with a probability of 0.95. Similar interpretation holds good for the true value of β[1]. .![inline image](bilder/EQ_037.png)is also known as standard deviation or standard error of ![inline image](bilder/EQ_020.png).

###### Note

We may use statistical hypothesis testing on the regression coefficients to validate the nature of the relationship. For example, we may test if there is at all a relationship between X and Y. In absence of a relationship, the true value of β[1] will be 0. Our estimated value ![inline image](bilder/EQ_021.png)of β[1] may not be zero, but this may be solely due to the specific set of data. If ![inline image](bilder/EQ_021.png)is far away from 0, either with positive or negative value, then we may say with confidence that true value of β[1] is not 0. But how far will be good enough? Here also we use probability theory. It turns out that the t-statistics, computed using the formula t = ![inline image](bilder/EQ_039.png)follows a t-distribution with n - 2 degrees of freedom under the assumption that β[1] = 0, where n denotes the no of observations in the sample data. With help of this probability distribution, we compute what is the probability to get a t‐statistics with absolute value |t| or higher. If this probability is very low, then we infer that it is unlikely to get an estimate ![inline image](bilder/EQ_021.png)of β[1] under the assumption β[1] = 0, so there is indeed a relationship between X and Y.

##### Assessing Accuracy of the Estimated Model

One of the important things after fitting a model to the data is to assess how good the model fits the data. If it does not fit the data well, the model will not reflect the true relationship and will produce poor predictions. This is assessed based on the errors between the actual and estimated values of the response y. There are different measures of goodness of fit, we will discuss here about two such measures, the residual standard error (RSE) and R² statistics.

Recall that the residual sum of square (RSS) is defined as:

![inline image](bilder/EQ_040.png)

This is the sum of squared deviations between the actual and estimated values of Y. It represents the variability of Y not explained by the linear regression estimates. We define two more terms:

*   Total sum of squares (TSS) = ![inline image](bilder/EQ_041.png)where ![inline image](bilder/EQ_030.png)
    
    This is the sum of squared deviations between the actual value and the sample mean of Y. It represents the total variability of Y across the sample mean.
    

*   Explained sum of squares (ESS) = ![inline image](bilder/EQ_042.png)where ![inline image](bilder/EQ_030.png)
    
    This is the sum of squared deviations between the estimated values of Y and the sample mean of Y. It represents the variability of Y explained by the linear regression estimates.
    

It can be easily shown that TSS = RSS + ESS.

##### Residual Standard Error (RSE)

The residual standard error (RSE) is defined as:

![inline image](bilder/EQ_043.png)

RSE provides an absolute measure the lack of fit in the units of Y. The higher the value of RSE, the lower the goodness of fit. However, how big is bad depends on the particular problem. It may be checked against the sample mean ![inline image](bilder/EQ_044.png)to assess the extent of lack of fit, e.g. if the RSE is 10 and ![inline image](bilder/EQ_044.png)is 100, then it shows around 10% deviation across ![inline image](bilder/EQ_044.png)on average.

##### R² Statistics

The R² statistics is defined as:

R² = ESS/TSS = (TSS – RSS) / TSS = 1 – RSS/TSS

It represents the Proportion of total variability explained by the regression model. Since 0 ⩽ ESS ⩽ TSS, it implies 0 ⩽ R² ⩽ 1. The higher the value of R², it implies higher proportion of total variance is explained by the regression model, hence the better the goodness of fit. However, what is a good value of R² depends on the particular problem. Note that this is independent of scale of Y, so a scaler transformation of Y does not impact the value of R². In the simple linear regression, R² measures the linear relationship between Y and X. It can be shown that R² = r² where r = Cor(X,Y).

#### Multiple Linear Regression

In most of the real-life problems, a response variable usually depends on multiple predictors. In the used car price example, the price of an used car depends on two factors, age and mileage of the car. How do we fit a model in this type of scenario? One possibility is to derive two different simple linear regression models with one predictor at a time. However, this does not satisfactorily predict the price of an used car when the age and mileage values are known, since both the models will provide predicted value of price and they may not match. Also, it does not capture how the relationship between price and mileage varies across different values of age and vice versa. Hence, when we have two or more predictors, it is natural to extend the simple linear regression model to incorporate all the predictors simultaneously.

Multi-linear regression model can be represented by:

Y = β[0] + β[1].X[1] + β[2].X[2] + .. + β[p.]X[p] + Ɛ

Here, Y is the response or dependent variable, X[1], X[2], ..X[p] are the predictors or independent variables, Ɛ is a random variable representing the error or noise in the model and β[0], β[1], β[2],.., β[p] are the regression coefficients or parameters.

###### Note

Like simple linear regression model, the multiple linear regression estimates the relationship between response Y and the predictors X[1], X[2], .., X[p] through a multi-dimensional equivalence of a straight line. The estimated value of y (y, given the x[1], x[2], .., x[p] values of the corresponding predictor variables X[1], X[2], .., X[p]) can be expressed as a linear combination of these values in the following way:

y= β[0] + β[1].x[1] + β[2].x[2] + .. + β[p.]x[p]

Here, β[0], β[1],..., β[p] are the estimated values of the regression coefficients. This equation represents a plane similar to a line in the higher dimension, called hyperplanes. In case of two predictors, this equation represents a two-dimensional equivalence of a line, which is a surface without a curvature. [Figure 2.8](#02_003.html#f2.8) shows the regression plane with respect to the least square estimates of the regression coefficients.

##### Estimation of Regression Coefficients

The derivation of least square estimates in case of multiple linear regression can be efficiently calculated using the matrix algebra. If you are not familiar with matrices and vectors, you may skip this part. You can get the least square estimates of the regression coefficients through the machine learning software, without applying linear algebra results.

Let y^T = (y[1], y[2], …, y[n]) be the transpose of the vector with values of the response variable Y in a sample of n records. Here y^T represents the transpose of the vector y.

Let X = (1 | x[ij]), for i = 1 to n and j = 1 to p represents the n x (p +1) matrix of predictor values, where first column is 1 (for the intercept term) and x[ij] represents the value of j-th predictor in the i-th record.

Let β^T = (β[0], β[1], β[2], …, β[p]) be the transpose of vector with the regression coefficients and Ɛ^T = (ε[1], ε[2], …, ε[n]) represents the transpose of vector with the associated error terms. Then the multiple regression model can be represented with matrix notation as y = Xβ + Ɛ.

This implies Ɛ = (y - Xβ).

The least-squares parameter estimates β is the vectors that minimize the sum of squared errors, for example, ∑[i = 1]^n ε[i]² = Ɛ^TƐ = (y - Xβ)^T(y - Xβ).

If ![inline image](bilder/EQ_045.png)is the transpose of vector of estimates of the regression coefficients which minimizes the SSE, then it turns out that the corresponding error vector (y - X![inline image](bilder/EQ_046.png)) is orthogonal to the columns of X, in other words:

*   X^T(y - X![inline image](bilder/EQ_046.png)) = 0
    
*   ⬄ X^Ty = X^TX![inline image](bilder/EQ_046.png)
    
*   ⬄ ![inline image](bilder/EQ_046.png)\= (X^TX)^(\-1)X^Ty
    

This has a unique solution if (X^TX) is a non-singular matrix, which means X is a full column-rank matrix. In other words, the columns in X are linearly independent.

If ![inline image](bilder/EQ_047.png)is the transpose of the vector with corresponding estimated values of Y, then:

![inline image](bilder/EQ_048.png)\= X(X^TX)^(\-1)X^Ty

[Figure 2.8](#02_003.html#f2.8) shows the regression plane for the secondhand car price data. [Figure 2.8](#02_003.html#f2.8) 1 and [Figure 2.8](#02_003.html#f2.8) 3 are rotated by 90 degree to get the [Figure 2.8](#02_003.html#f2.8) 2 and [Figure 2.8](#02_003.html#f2.8) 4. Note that data is more concentrated along a plane.

[![The Multiple Linear Regression Plane for the Secondhand Car Price Data](bilderklein/klein02_008.png)](img-f2.8.html) 

**Figure 2.8**    The Multiple Linear Regression Plane for the Secondhand Car Price Data

##### Assessing the Accuracy of the Estimates of the Regression Coefficients

As like simple linear regression, the significance of the different slope parameters can be checked through the hypothesis testing of individual parameters. They follow the same t-distribution.

Besides, we may formulate few other important hypotheses and test them against alternatives. One important hypothesis could be null hypothesis. H[0]: there is no relationship between the response and the predictors, for example, β[1] = β[2] = … = β[p] = 0.

Against the alternative hypothesis, H[a]: at least one of the β[j] is non-zero, 1 ⩽ j⩽ p.

The F-statistics, defined as F = \[(TSS – RSS)/p\] / \[RSS/(n -p -1)\] is used to test this hypothesis. If the errors are from independent and identically distributed normal distribution, then the F-statistics follow F-distribution. We can get the probability of the associated F-distribution to find the probability of a value greater than or equal to F. This is called the p-value. If this is less than 5% (or 1%), we can infer with 95% (or 99%) confidence that the null hypothesis is wrong, so there is a relationship between response and at least one predictor. Usually, a value of F much higher than 1 signifies relationship between response and predictors.

Another important hypothesis could be to check if a subset of regression coefficients are zero. Expressed mathematically: H[0] : β[p- q+1] = β [p- q+2] = … = β[p] = 0

In this case we fit another model without those q predictor. If RSS of this second model is RSS[0], then the F statistics defined as F = \[(RSS[0] – RSS)/q\] / \[RSS/(n -p -1)\] can be used to test the hypothesis.

In case of multiple linear regression, the F-Statistics provide a better insight of significance of a group of predictors compared to individual t-statistics of the associated coefficients. In case of large numbers of predictors, the t-statistics may show some of the predictors significant simply by chance. Hence F-statistics based testing is more reliable to find the significance of a group of predictors.

##### Assessing the Accuracy of the Estimated Model

As in case of simple linear regression, the accuracy of the fitted multiple linear regression model can be assessed using the RSE and R² Statistics. The approach and the interpretation are the same. In case of multiple linear regression with p predictors, the RSE is defined as:

![inline image](bilder/EQ_049.png)

Also, in this case the R² turns out to be equal to r² where r = ![inline image](bilder/EQ_050.png)

As we add more and more predictors to the model, the RSE tends to decrease even if decrease in RSS is small. Similarly, adding new predictors increases the R² Statistics, even if the amount of increase is small. So, we need to critically examine the significance of adding a predictor to the model in terms of how much variability is explained by the new predictor.

##### Selecting the Important Predictors

A multiple linear regression model with many predictors often tends to overfit the data, it fits very well with the model data but gives poor predictability. Hence, we need to choose the right set of predictors while analyzing the data. This is known as variable selection. There are many methods for variable selection, some of them are discussed below.

Ideally, when multiple predictors are available, we should check all possible models each containing different sets of predictors and select the one which is the best with respect to some criteria. There are various statistics like Mallow’s C[p], Akaika information criteria (AIC), bayseian information criteria (BIC), and adjusted R² to detect the best model from a set of available models. However, total number of such models could be very high, for p predictors, there are 2^p different models including the one without any predictor. Hence, there are few classical variable selection methods which are used in practice:

*   Forward selection  
    In this case, the model with no predictor is first evaluated. Then we fit p simple linear regressions, one for each predictor and select the predictor which results in lowest RSS. Once this predictor is selected, we then evaluate all models with 2 predictors, one of them being the selected one and choose the model with 2 predictors which results in lowest RSS. We continue this process of selecting predictors one by one unless some stopping criteria is satisfied.
    
*   Backward elimination  
    Here we start with all the predictors and remove predictors one by one. First, we model data with all predictors and identify the predictor which is least significant as per the t-statistics. Then we again fit the model with the remaining (p -1) predictors and again select the one which is least significant in this new model with (p -1) predictors. We continue to eliminate the predictors one by one unless some stopping criteria is satisfied.
    
*   Mixed selection  
    This is a combination of both forward selection and backward elimination. We first start with no predictors and continue selecting predictors as in case of forward selection. However, in any such step, if some predictors show least significance as per the t-statistics, we eliminate that predictor. We continue the forward and backward steps until all the predictors in the model are significant and adding a predictor from outside will make it insignificant (based on the t-statistics).
    

#### Other Considerations

In [Section 2.3.1](#02_003.html#h2.3.1), we discussed about some of the assumptions related to linear regression. In practice, these assumptions are not always satisfied, besides, there could be various issues related to data. These situations pose various problems while fitting a regression model and need to be diagnosed and corrected. Let’s explore some of these common problems.

##### Non-Linear Relationship between Predictor and Response

Linear regression model assumes a linear relationship between the response and the predictor. However, often this relationship is not linear and fitted model does not represent the true picture. [Figure 2.9](#02_003.html#f2.9) 1 shows the scatter plot of a predictor X and response Y. Clearly, the points are not along a straight line, rather it is close to a quadratic function Y = X².

When we observe such non-linearity, we may apply some transformation to the predictor before we use them in the model. In our example, if we use Z = X² as the predictor instead of X, then the relationship between Y and Z will be linear. [Figure 2.9](#02_003.html#f2.9) 2 shows the scatter plot of Z = (X²) vs. Y and it shows a linear relationship. Other common transformations are log X, √X.

[![Response vs Predictor Plots Before and After Transformation](bilderklein/klein02_009.png)](img-f2.9.html) 

**Figure 2.9**    Response vs Predictor Plots Before and After Transformation

The nonlinear relationship between predictor and response can be identified through scatter plot of the residual ε[i] = y[i] - ![inline image](bilder/EQ_051.png)against the estimated value ![inline image](bilder/EQ_051.png). There should not be any observable pattern in the residuals. Observable patterns indicate some problem with the linearity assumption. [Figure 2.10](#02_003.html#f2.10) shows the residual vs. estimated value plot for these two scenarios, using X as the predictor in [Figure 2.10](#02_003.html#f2.10) 1 and using Z = X² as the predictor in [Figure 2.10](#02_003.html#f2.10) 2.

[![Residual Plot Against the Estimated Values in the Two Scenarios](bilderklein/klein02_010.png)](img-f2.10.html) 

**Figure 2.10**    Residual Plot Against the Estimated Values in the Two Scenarios

##### Heteroscedasticity

Heteroscedasticity refers to the scenario where error terms do not have a constant variance, rather it varies with values of the response. Constant variance of error terms is an important assumption behind the calculation of confidence interval of parameters, t‐statistics, hypothesis testing, goodness of fit statistics and all becomes invalid with heteroscedastic errors.

Heteroscedasticity can be identified through the plot of residual vs. estimated value, the errors with more variance will have more spread compared to the ones with less variance. This often leads to a funnel shaped plot. In such scenario, the response Y can be suitably transformed using functions like log Y, √Y before using them in the regression model. [Figure 2.11](#02_003.html#f2.11) shows residual plot of heteroscedastic data 1 and residual plot after applying a transformation 2.

[![Residual Plot of Heteroscedastic and Transformed Data](bilderklein/klein02_011.png)](img-f2.11.html) 

**Figure 2.11**    Residual Plot of Heteroscedastic and Transformed Data

##### Correlation of Error Terms

Another important assumption in linear regression is that errors terms are uncorrelated. This means errors are purely random and there is no systematic pattern in the error. However, this condition is not often satisfied due to problem in choosing the sample data. It leads to underestimate of standard errors, so the estimation and prediction intervals become narrower. This can often appear if we deal with data which is collected over different time points, e.g. sales data across months. The error in one period tends to influence the error in the next period. The correlation of error terms can be identified if we plot the residuals across time points, it shows some systematic patterns in the data. There are many methods in time series analysis to incorporate correlation among the error terms.

##### Multicollinearity

Multicollinearity refers to the situation when two or more predictors are linearly related to each other. Although multicollinearity does not impact much predictability of the model, but it makes estimates of the regression coefficients unstable, their variability may become very large. Let’s consider a scenario where response Y is regressed with two predictors, X[1] and X[2] and the estimated model is:

Y = 2 + 3X[1] + 7X[2]

Now if X[1] and X[2] are linearly related as X[1] = 2X[2], Then the same equation may be written as:

Y = 2 + (3 x 2)X[2] + 7X[2] = 2 + 13 X[2]

Similarly, we can write it as:

Y = 2 + 3X[1] + 7X[2] + (1,000,000X[1] - 2,000,000X[2])

or, Y = 2 + 1,000,003X[1] – 1,999,993X[2]

\[since 1,000,000X1 = (1,000,000 x 2)X2 = 2,000,000X2, it implies 1,000,000X[1] - 2,000,000X[2] = 0 \]

So, the coefficients can take arbitrary large or small values and their estimates become volatile in case of true collinearity. Even near collinearity also poses similar problem.

Multicollinearity can be assessed through variance inflation factor (VIF) and it can be computed for each predictor as VIF[j] = 1 / (1 – R²[j]) where R²[j] is the R² Statistics when X[j] is regressed onto all other predictors. In other words, R² of the regression model where X[j] is treated as response and all other predictors act as predictors. If X[j] is can be reasonably estimated using other predictors, it implies Xj has a linear relationship with other predictors. In that case the R²[j] will be close to 1 and the corresponding VIF[j] value will be large. In practice, typically small amount of multicollinearity is found in the data and can be ignored. It becomes problematic if the value of VIF exceeds 5 or 10. In that case we may drop the associated predictor or combine the linearly related predictors into one single predictor.

##### Outliers and High Leverage Points

An outlier is a data point where the response value y is far away from remaining values. Similarly, a high leverage point is a data point where the predictor value x is far away from rest of the values. They may creep into the data due to measurement error or experimental error. Outliers increases the RSE, so it impacts calculation of confidence intervals, t-statistics and raises question on goodness of fit. On the other hand, high leverage observations shift the regression line resulting in sub-optimal model. In [Figure 2.12](#02_003.html#f2.12), the dotted blue line shows the regression line fitted without a high leverage point and the solid red line shows the shifted regression line in presence of a high leverage point.

[![Shift of Regression Line in Presence of a High Leverage Point](bilderklein/klein02_012.png)](img-f2.12.html) 

**Figure 2.12**    Shift of Regression Line in Presence of a High Leverage Point

Outliers can be detected using the residual plot. The outliers appear far away from rest of the residuals.

High leverages can be identified using the leverage statistics. For simple linear regression, the leverage of i-th value of predictor, x[i] is computed as ![inline image](bilder/EQ_052.png)

The h[i] values always lie between 1/n and 1. High value of h[i] suggests associated observation has a high leverage.

There are several extensions of least square regression model to accommodate different practical scenarios while modeling the data. We will briefly discuss here two such popular extensions, ridge regression and lasso.

##### Ridge Regression

In multiple linear regression, we estimate the regression coefficients by minimizing the residual sum of square (RSS). In ridge regression, the regression coefficients are estimated minimizing the following objective function:

![inline image](bilder/EQ_053.png)

λ ⩾ 0 is the tuning parameter and is determined separately. Note that the intercept term is not included in the second part of the objective function.

When λ = 0, ridge regression is same as the least square regression. However, if λ > 0, it forces the estimates of regression coefficients to shrink towards zero. The term ![inline image](bilder/EQ_053.png)is known as shrinkage penalty. If λ → ∞, estimates of all the regression coefficients tend to zero. unlike least square regression, ridge regression provides multiple sets of estimates of regression coefficients and a suitable one is be selected.

The ridge regression can be alternatively formulated as:

![inline image](bilder/EQ_054.png)

From this formulation, it is evident that ridge regression tries to minimize the variance of estimates of the coefficients at the cost of some bias in the estimates. The least square estimates of the regression coefficients have higher variance, but no bias. On the contrary, ridge regression tries to reduce the variance with some tolerable amount of bias. This bias-variance trade-off makes ridge regression a powerful tool in the regression analysis.

Ridge regression is particularly useful in presence of multicollinearity in the data. Since it reduces variance of the estimates, the variances of the coefficients of linearly dependent predictors cannot go beyond a limit. This way, it achieves a reasonably good estimate of the regression coefficients in presence of multicollinearity.

##### Lasso

In lasso, the coefficients of the regression parameters are estimated through minimizing the following objective function:

RSS + ![inline image](bilder/EQ_055.png)

where λ ⩾ 0 is the tuning parameter and is determined separately. The function |a| denotes the absolute values of a. Like ridge regression, lasso also tries to shrink the coefficient estimates to zero, but with a separate penalty function.

Lasso can be alternatively formulated as:

![inline image](bilder/EQ_056.png)

The advantage of lasso over ridge regression is that although both the penalty functions tries to shrinkage the parameter estimates, while ridge optimizes the parameters confining them within a circular space (since ![inline image](bilder/EQ_057.png)is a circular region in p-dimensional space with center at origin and radius √c), the lasso optimizes the parameters along a p‐dimensional cube whose vertices are on the coordinate axes in the p-dimensional space. The optimized estimates of regression coefficients often fall on those axis points and thus have value zero for some coefficients. So, while optimizing the objective function, the lasso tends to estimate zero for coefficients of non-significant predictors. This provides an automatic variable subset selection through the penalty function.

In case of regression with two predictors, the [Figure 2.13](#02_003.html#f2.13) shows the regions representing the values of β[1], β[2] satisfying the constraints:

*   ![inline image](bilder/EQ_057.png)([Figure 2.13](#02_003.html#f2.13) 1)
    
*   ![inline image](bilder/EQ_058.png)([Figure 2.13](#02_003.html#f2.13) 2).
    

[![Regions Defined by Constraint Functions for Ridge and Lasso](bilderklein/klein02_013.png)](img-f2.13.html) 

**Figure 2.13**    Regions Defined by Constraint Functions for Ridge and Lasso

### 2.3.2    Classification

Classification analysis is another important branch of supervised machine learning, used for assigning objects of interest into multiple categories or classes, based on data across different influential factors to characterize the classes. In regression analysis, we studied how to model the relationship between a quantitative response and multiple predictors and use the model for predicting value of the response. In the classification analysis also we try to build a model based on predictors, but instead of a quantitative response, we are interested here in qualitative or categorical response and predict the possible class or category for a new set of predictor values. In this chapter we will discuss about some of the well-known and widely used classification algorithms and how to use them in real-life problems. We will also discuss the merits and demerits of these algorithms and how to identify a suitable algorithm based on the nature of the problem.

Before we get into details of the algorithms, let’s look at a real-life problem. In the telecom industry, customer churn is one of the major issues. Customer leaves the service of the telecom company due to various reasons, sometimes due to network issues or service issues, sometimes due to huge bills or wrong bills, sometimes due to other factors like moving into a new location. Since acquiring a new customer is usually costlier than retaining an existing customer, proactively preventing churn can result in increase in the bottom line. With this in mind, telecom companies try to predict the customers who are susceptible to churn and retain them through proactive retaining programs. While predicting the customers susceptible to churn, we classify the customers into two categories, churn prone and loyal customers based on various associated influential data including usage pattern, billing pattern, customer complaints and demographic information. For this purpose, we may build a model to identify the relationship between a categorical response which indicates a customer has churned or not and several predictor variables or influential factors based on historical data. Then we may use this model to classify or predict whether an existing customer will churn based on the associated values of the predictor variables. This type of modeling exercise falls under the domain of classification analysis. Another interesting use case of classification analysis could be image recognition. Based on various aspects like color, shape, size of objects in a photo, the machine learning algorithms may classify the objects in an image into different categories.

#### K-Nearest Neighbor Classifier

K-nearest neighbor (KNN) classifier is one of the simplest supervised learning methods to classify observations based on the training data set. It does not develop any model based on the training data as in case of regression analysis. Rather, given a new observation, it classifies the data based on the neighboring records.

Suppose we have a categorical variable Y indicating two classes, Class 1 and Class 2 and two predictor variables X and Z. We have a training data of n observations, each containing the values of Y, X and Z. Let {(y[1], x[1], z[1]), (y[2], x[2], z[2]), …, (y[n], x[n], z[n])} is the training set. Now we have a new record with only the values of the predictors X and Z. Let this record is (x, z). We want to predict whether this record falls into Class 1 or Class 2, in other words, we want to predict the value of the categorical variable Y. [Figure 2.14](#02_003.html#f2.14) 1 shows this data graphically, where each data is plotted against their values in X and Z predictors. The color of the data indicates the class they belong to, red dots indicate the records belonging to Class 1 and blue dots indicate the records belonging to Class 2. The black dot indicates the new record which we wish to classify either in Class 1 or Class 2.

The KNN classifier looks at the K nearest neighbors of the new observation in the training data and classifies the new observation to a class which has maximum representatives within the K neighbors. In case of a tie, we may randomly assign it to one of the classes. In our example, let’s take the value of K = 15. In [Figure 2.14](#02_003.html#f2.14) 1, the circle around the black dot encompasses 15 nearest neighbors from the training set; 12 of them are red (from Class 1), hence the new observation is classified into Class 1.

We can classify all the points in the plane based on this principle. This is shown in [Figure 2.14](#02_003.html#f2.14) 2. The black line indicates the boundary between the red and blue regions and called the decision boundary.

[![KNN Classification of a New Record based on the Training Set and Decision Boundary](bilderklein/klein02_014.png)](img-f2.14.html) 

**Figure 2.14**    KNN Classification of a New Record based on the Training Set and Decision Boundary

The choice of value of K is critical for the classification in KNN. If we take a low value of K, it provides a very flexible decision boundary. This corresponds to a low-bias but high-variance classifier. With higher values of K, the decision boundary becomes less flexible and this corresponds to a low-variance high-bias classifier. [Figure 2.15](#02_003.html#f2.15) shows two such classifiers. [Figure 2.15](#02_003.html#f2.15) 1 corresponds to K = 3 and [Figure 2.15](#02_003.html#f2.15) 2 corresponds to K = 50.

We can compute the error rate of the classifier for different values of K based on both the training data and test data. The error rate in the classification can be defined as:

![inline image](bilder/EQ_059.png)

Where yi actual class and ![inline image](bilder/EQ_051.png)is the predicted class based on i-th observation. ![inline image](bilder/EQ_060.png)is the indicator function, taking value 1 if predicted class does not match with the actual class, 0 otherwise. So, the error rate indicates the proportion of records misclassified. We may choose a value of K for which training and test error rates are low.

[![KNN Classifiers for K =3 and K = 50](bilderklein/klein02_015.png)](img-f2.15.html) 

**Figure 2.15**    KNN Classifiers for K =3 and K = 50

In KNN, all the K neighbors get equal importance irrespective of their relative distance from the new observations. This makes it more sensitive towards choice of K. This can be reduced with introduction of a weight function; so that the nearest neighbors get higher weight. The further points will have lower impact on the classification. If d[1], d[2], .. d[k] are the distances of the test observation from the associated K neighbors, then w[1] =1/d[1], w[2] = 1/d[2], .., w[k] =1/d[k] can be taken as weights and the test observation may be classified to class y if it has maximum value of ∑w[i] I( y[i] = y) where i runs across the k neighbors, I is the indicator function.

###### Advantages and Disadvantages of KNN Classifier

The main advantages of the KNN classifier include:

*   KNN is a non-parametric classifier, it does not require any assumption on underlying probability distribution.
    
*   No model building is required for KNN, so new training data can be easily adapted.
    
*   Unlike other classifiers, it can be used for multi-class classification problem.
    

However, KNN has some disadvantages:

*   It does not perform well in high-dimensional data, as the data points become sparse in high dimension.
    
*   The KNN classifier does not require a model building. However, classifying a test dataset with many records could be quite expensive as it requires to calculate the proximity for each test record against all the training records.
    
*   KNN classifier may be impacted by scalar transformation of the predictors. If one of the predictors has high range of numeric values compared to others, the classifier gets dominated by this predictor and produces wrong predictions. Hence the data needs to be preprocessed to eliminate effect of scaling.
    
*   KNN classifier predicts based on local information. Due to this, it is more susceptible to noise in the data. There are other classification methods like decision tree, logistic regression which utilizes the entire training data.
    

#### Logistic Regression

The logistic regression is used in a two-class classification problem, when the response variable has two different classes. This is one of the classical methods in statistics that has got many applications in machine learning. It has been extensively used in biological and social science for long. There are many extensions of logistic regression model.

In logistic regression, we usually denote the values of the response variable Y through 0 and 1. We usually take Y=1 for the class which is of main interest. However, it does not matter if we use a different coding of the response, we need to interpret the results accordingly. Unlike KNN, in logistic regression the data is classified based on conditional probability of Y = 1, given the values of the predictors. Mathematically, this can be written as:

P(Y = 1| X = x) where X = (X[1], X[2], ..., X[p])

The set of p predictors and x = (x[1], x[2], .., x[p]) are the values of the corresponding predictors in a typical record. Note that P(Y = 1| X = x) is a function X, its value varies with different values of X. We use the following simplified notation to indicate this relationship:

1  p(X) = P(Y =1 | X)

The logistic regression tries to fit a model to find the relationship between p(X) and X. One of the simplest approach to examine a model like:

p(X) = β[0] + β[1]X[1] + β[2]X[2] + β[p]X[p]

However, it turns out that such a model may give a negative value of p(X). Since probability cannot be negative, we need to ensure that probability lies between 0 and 1. This is achieved through a transformation of β[0] + β[1]X[1] + β[2]X[2] + β[p]X[p] so that p(X) lies between 0 and 1. There are many such candidate functions, in logistic function, we use the logit function,

2  ![inline image](bilder/EQ_062.png)

Note that this is equivalent to writing the equation as:

3  ![inline image](bilder/EQ_063.png)

The quantity p(X)/(1 – p(X)) is called odds, it is the proportion of probability of a favorable event against the probability of unfavorable event. Higher the value of odd, it means the favorable event is most likely. Note that p(X)/(1 – p(X)) varies between 0 to ∞. The equation 3 is equivalent to:

4  ![inline image](bilder/EQ_064.png)

The left side of the equation is called the log-odds or logit. The logit can vary between - ∞ and + ∞. So, this setup gives us a continuous response variable which it the logit, related to a set of predictors in a linear relationship. This is exactly the setup of a linear regression. However, there are some differences. Recall that in linear regression the regression coefficients β[1], β[2], .., β[p] represents the increase in value of Y by unit change in the predictors X[1], X[2], .., X[p] respectively. However, such relationship does not hold good for logistic regression. Here, instead of least square estimate of parameters, we use another estimation method, called the maximum likelihood estimate. In fact, the least square estimate is a special case of maximum likelihood estimate. In maximum likelihood estimate, we obtain estimated values of the regression coefficients that maximizes the probability of observed values of Y. The rationale behind using the maximum likelihood estimate is to get an estimate of regression parameters which yields p(X), as defined in equation 1, close to 1 for cases where Y =1 and close to 0 for cases where Y = 0.

The likelihood function for logistic regression can be written as:

5  ![inline image](bilder/EQ_061.png)where p(x[i]) = P(Y = 1| X = x[i])

The maximum likelihood estimate of β = (β[1], β[2], .., β[p] ) is the one which maximize the likelihood function. The details of the derivation of maximum likelihood estimate requires higher mathematics and is not scope of this book. The statistical software packages provide the estimates of the logistic regression model, so the details are omitted here.

Many aspects of the logistic regression are similar to that of linear regression. The accuracy of the estimated coefficients can be measured using the standard deviations. The z-statistics in logistic regression plays the same role of t-statistics in linear regression.

#### Predicting using Logistic Regression Model

Once the parameters β[1], β[2], .., β[p] are estimated, the predictions of probabilities can be achieved through the equation:

![inline image](bilder/EQ_065.png)

So, if x[1], x[2], …, x[p] are values of a test observation, the estimated probability that it falls under the class Y =1 can be computed as:

![inline image](bilder/EQ_066.png)

Mathematically, this can be written as:

![inline image](bilder/EQ_067.png)

Here, ![inline image](bilder/EQ_068.png)are the maximum likelihood estimates of ![inline image](bilder/EQ_069.png).

###### Advantages and Disadvantages of Logistic Regression�

The main advantages of logistic regression include:

*   Logistic regression provides a robust model compared to other classifiers like decision tree.
    
*   Logistic regression provides nice interpretation of the model parameters in terms of odds ratio. Influence of predictors on the outcome can be interpreted using logistic regression. The details have been discussed in [Chapter 7](#07_001.html#h7), [Section 7.2.6](#07_002.html#h7.2.6).
    
*   The underlying algorithm is efficient and does not require much computational power or resources.
    

*   However, logistic regression has some disadvantages as well:
    
*   The modeling technique requires thorough understanding of the features and feature engineering. Uncorrelated features may add noise to the model.
    
*   Influenced by data issues like multi-collinearity, heteroscedasticity. Transformation and regularization techniques can be used to eliminate these issues.
    

#### Decision Tree

Decision tree is one of the popular supervised machine learning methods due to simplicity of its interpretation. It is a non-parametric method which can be used for both regression and classification purpose. Given a response variable and a set of predictors, a decision tree systematically splits the predictor space (also called feature space) based on the values of the response in a recursive way, until a stopping criterion is satisfied. The responses associated with the final segments of the feature space either have higher concentration of a class (for classification problem) or have mean values highly different across the segments (for regression problem). These splitting criteria can be represented through a tree-like graph and is called a decision tree. For prediction purpose, given a new set of values of the predictors, the decision tree identifies the final smaller segment where it belongs to and predicts the value of response as the mean or mode of the response values in that segment.

Before we go into the details of decision tree, let’s consider the following simulated data on customer churn (as seen in [Table 2.4](#02_003.html#t2.4)). Our objective is to identify relationship between customer churn and other predictors so that we can predict whether an existing customer will churn. [Figure 2.16](#02_003.html#f2.16) shows the associated decision tree. Note that it consists of series of splitting rules. The top node or the root of the decision tree is split based on billing amount. Then it is further split based on income group and network problem.

 
| CHURNED (customer churned?) || BILLING\_AMOUNT (billing amount) || NETWORK\_PROBLEM (network problem) || INCOME\_GROUP (income group) || NO\_OF\_VAS (number of value-added services) |
| --- | --- | --- | --- | --- |
| Yes || 200 || Yes || High || 1 |
| --- | --- | --- | --- | --- |
| Yes || 180 || Yes || High || 1 |
| No || 195 || No || High || 1 |
| Yes || 140 || No || High || 1 |
| No || 100 || No || High || 1 |
| Yes || 200 || Yes || Medium || 1 |
| No || 100 || Yes || Medium || 1 |
| Yes || 180 || No || Medium || 1 |
| No || 70 || No || Medium || 1 |
| Yes || 100 || Yes || High || 0 |
| Yes || 80 || Yes || High || 0 |
| No || 170 || No || High || 0 |
| No || 50 || No || High || 0 |
| No || 200 || No || High || 0 |
| Yes || 187 || No || Medium || 0 |
| Yes || 190 || Yes || Medium || 0 |
| No || 60 || No || Medium || 0 |
| No || 120 || No || Medium || 0 |
| No || 151 || Yes || Medium || 0 |

**Table 2.4**    Simulated Customer Churn Data

[![Decision Tree for the Simulated Customer Churn Data](bilderklein/klein02_016.png)](img-f2.16.html) 

**Figure 2.16**    Decision Tree for the Simulated Customer Churn Data

The top node of the decision tree is called the root. The terminal nodes are called leaves. The intermediate nodes are called internal nodes. The connectors between the nodes are called branches. So, it is a tree structure, drawn upside down. The leaves represent the final segments of the predictor space. They are non-overlapping and their union gives the entire predictor space.

If we now want to predict if an existing customer will churn, we need to see the associate values of the predictors and find out which leave (segment) this record falls into. If that leaf contains higher % of churned customers, then we predict this customer will churn, otherwise we predict he will not churn.

[Figure 2.17](#02_003.html#f2.17) illustrates this concept of splitting the predictor or feature space into multiple segments and how each segment is identified with a specific value of the response.

[![Partition of the Predictor Space through Decision Tree](bilderklein/klein02_017.png)](img-f2.17.html) 

**Figure 2.17**    Partition of the Predictor Space through Decision Tree

#### Building a Decision Tree

Now we turn our focus on how a decision tree is built. This will help us to understand the underlying concept and limitations of the approach. The final output of the decision tree is a set of non-overlapping segments of the feature space (in other words, the predictor space, the set of all possible values of the predictors X[1], X[2],.., X[p] ) into j segments, say S[1], S[2], … S[j] so that the associated values of the response variables in those segments are concentrated around specific values of response. The associated steps are outlined here.

For our first step, the feature space is split into smaller segments (usually into 2 segments with a binary split) based on a suitable predictor (or feature). Depending on the nature of the predictor and algorithm used, the split can take different forms. [Figure 2.18](#02_003.html#f2.18) represents possible splitting options.

One important aspect here is to identify the suitable predictor and the best split. Since these splits are used for predicting an observation into a class, the best split will have minimum classification error. This concept has been used to derive different measures to identify the best split.

Let p(i|t) represents the fraction of records belonging to class i at the t\-th segment. The classification error rate of a segment t can be calculated through any one of the following measures:

*   Classification error rate (t) = ![inline image](bilder/EQ_070.png)
    
*   Gini Index(t) = ![inline image](bilder/EQ_071.png)
    
*   Entropy(t) = ![inline image](bilder/EQ_072.png)
    

Here, c is the number of classes of the response variable. Here, smaller values of these measure indicate a better split.

Usually the Gini index or entropy is used to find the best split.

[![Different Ways of Splitting a Predictor Based on its Nature](bilderklein/klein02_018.png)](img-f2.18.html) 

**Figure 2.18**    Different Ways of Splitting a Predictor Based on its Nature

For our second step, new segments formed in the previous step become the child nodes of the original segment used in the first step.

Now, for our third step, let's consider that these previous two steps are continued recursively with the child nodes. In other words, the child nodes, with their respective part of feature space are split again. This process continues recursively until a stopping criterion is attained. This could be if all records are from same class, or all records have same predictor values, or the number of records has fallen below a threshold.

Once a node (segment) cannot be further split, it is declared as a leaf. It is assigned to a class that has majority number of training records in that leaf.

For step four, the process terminates when all available nodes are leaves.

The decision tree so built partitions the entire feature space or predictor space into smaller non-overlapping segments, each leaf represents one such segment. Now for a new record, if we know the value of the predictors only, we know which leaf or segment this record belongs to. The predicted value of the response (the class) for this new record will be the class that has majority number of training records in that leaf.

###### Note

The similar approach holds good for building a decision tree for regression problem also. However, here the response is a quantitative variable, so the measures like gini index, entropy, classification error rate cannot be used to find the best split. The best split in this case is the one which minimizes residual sum of squares (RSS) given by:

RSS = ![inline image](bilder/EQ_073.png)

Where S[1], S[2],.., S[J] are J segments of the feature space, ![inline image](bilder/EQ_074.png)is mean of the responses in the j-th segment in the training data. Here, i ∈ S[j] means the set of values of predictors in the i\-th record falls in segment S[j].

Also, for any new record (with only predictor values), it should fall under only one of the leaves. The mean of the response value of that leaf based on training data is considered as the predicted value of the response of the new record.

###### Advantages and Disadvantages of Decision Tree

The major advantages of decision tree method include:

*   Decision tree is very easy to interpret. It has nice graphical representation which helps to understand the splitting rules easily.
    
*   It can model if the underlying relationship is non-linear.
    
*   Decision tree can handle both categorical and quantitative data directly. It does not require to create dummy variables for categorical predictors, as in case of linear or logistic regression.
    

However, there are some disadvantages of using the decision tree:

*   Overfitting. The decision trees tend to overfit the data. They fit the training data very well but do not have high prediction accuracy. Several methods are there to avoid this problem, one such is tree pruning to avoid overfitting.
    
*   When the classes are separated by a hyper-plane (multi-dimensional equivalent of straight line) decision tree tends to provide poor fitting. This is because it splits the predictor space through rectangular segments. A two-dimensional version (with two predictors) of this problem is shown in [Figure 2.19](#02_003.html#f2.19).
    
*   Decision trees could be very non-robust. A small change in the training data may result in major change in the final tree.
    
*   Decision tree follows a greedy approach, at each step of tree building, it takes the best split available at that step, rather than choosing a split that may result in a better tree in future step. This may result in a suboptimal tree.
    
*   It may create a biased model if some response class dominates.
    

[![Problem with Decision Tree with Near Linear Boundary](bilderklein/klein02_019.png)](img-f2.19.html) 

**Figure 2.19**    Problem with Decision Tree with Near Linear Boundary

#### Random Forest

The classification methods like logistic regression, decision tree predicts the response value (class) based on a single model or classifier induced from the training data. However, there are machine learning techniques which predict the response value (class) by aggregating the predictions from multiple classifiers to improve classification accuracy. These techniques are known as ensemble methods. An ensemble method constructs a set of base classifiers based on the training data and predicts the class of a new data by taking a vote on the predictions made by the base classifiers. In other words, assigning the class value which is predicted by majority of the classifiers.

It can be shown that when the base classifiers are independent and each base classifier has error rate less than 0.5 (they classify better than just making a random guess with 0.5 probability of error), ensemble method provides much better prediction accuracy, with significantly low error rate compared to individual classifiers.

In practice, it is difficult to get a set of base classifiers which are independent of each other, so different techniques are applied to construct an ensemble of independent classifiers, e.g. by randomizing the training data, by randomizing the input predictors, by manipulating the class labels (response values) or by manipulating the learning algorithm.

Random forest is one of the popular ensemble methods specifically designed for decision tree. It uses decision tree as the base classifier and creates a set of decision trees using values of an independent set of random vectors. [Figure 2.20](#02_003.html#f2.20) shows a schematic diagram of building a random forest.

[![Schematic Diagram of Building a Random Forest](bilderklein/klein02_020.png)](img-f2.20.html) 

**Figure 2.20**    Schematic Diagram of Building a Random Forest

To construct a set of independent decision trees, each decision tree uses a random vector (set of random values) in the tree building process. These random vectors are generated from some fixed probability distribution in such a way that they are independent of each other, hence the associated decision trees tend to be independent of each other.

There are various ways to incorporate a random vector into the tree building process. Suppose there are p predictors X[1], X[2], X[3],…X[p] and the random vector selects F distinct numbers from 1 to p. To explain this idea further, let’s say there are 10 predictors (p = 10). If we take F = 4, a random vector randomly picks up 4 distinct numbers from 1 to 10. The first draw picks up the vector (1, 3, 9, 10), the second draw picks up (2, 4, 7, 8), the third draw picks up (1, 5, 6, 8), so on. For each of these random vectors, we may construct a decision tree in many ways.

Firstly, instead of using all the available predictors, create a decision tree which splits each node based on randomly selected F predictors. In our example, the first random vector is (1, 3, 9, 10), so the first decision tree only uses predictors X[1], X[3], X[9], X[10] for splitting each nodes. Similarly, the second decision tree uses predictors X[2], X[4], X[7], X[8] for splitting each node. Since they differ at the predictors to be used in a split, both the decision trees are different and they do not have much similarity or correlation. In the same manner, a set of decision trees can be generated. If the value of F is small, it increases the randomness and hence increases independence of the associated decision trees. But with a small no of predictors, the decision trees become less accurate. As a trade-off, the value of F is commonly chosen to be F = log[2] p + 1. This approach is known as Forest-RI, where RI stands for random input. To improve independence, even the input data can also be randomized, taking a random sample of n records with replacement (a record once selected can be selected again) from the original data of n records. This technique is known as bagging.

Secondly, when the value of p is small, each set of F predictors contain some predictors in common, so it becomes difficult to choose an independent set of random predictors for building the decision tree. In that case randomization can be introduced in a different way. At each node, a new predictor can be generated by randomly picking up L original predictors and combining them linearly with coefficients generated from a uniform distribution over the range (-1, 1). In the same manner F such randomly generated new predictors can be created and the best of them is used for splitting the node. This approach is known as Forest-RC. resulting decision trees tend to be uncorrelated with each other.

Thirdly, another way of randomly creating independent set of decision trees could be through manipulation of node splitting. Recall that decision trees splits each node based on the best split available at that step. However, instead of best split, the top F split criterion can be considered and one of them can be selected at random to split the node. However, this approach generates decision trees which are more correlated compared to Forest-RI or Forest-RC approach.

Once a set of decision trees are constructed using one of these techniques, they are used for prediction. For predicting response value (class) of a new observation, the predicted values are obtained from all the decision trees and the one is selected which is predicted by most of the decision trees.

There are many advantages of random forests compared to decision trees:

*   Random forests have significantly high prediction accuracy over decision trees.
    
*   Random forests are less sensitive to noise. Since prediction from multiple decision trees are combined together, the effect of noise gets reduced.
    
*   Random forest reduces the adverse effect of a dominating predictor.
    

However, random forest also has some disadvantages:

*   The nice interpretation of decision trees are lost in a random forest. Since multiple uncorrelated decision trees are used and final outcome is derived based on voting, it does not provide an interpretation in terms of influence of predictors.
    
*   Requires more computational power and resources.
    

#### Support Vector Machine (SVM)

Support vector machine (SVM) is a supervised machine learning method, most popular and considered to be one of the best classifiers. It uses the concept of separating hyperplane. SVM is used for 2-class classification problems. However, it can be suitably used even for multiple class problems with some adjustment of the training data. The estimation process of SVM involves complex mathematics, hence we will not get into the details and will just outline the underlying concept.

Before we start, let’s discuss hyperplanes. A hyperplane is a generalization of a line in the multidimensional spaces. In a p-dimensional space, it is a “flat” subspace of p -1 dimensions. In a 2-dimensional plane it is a straight line. In a 3-dimensional space it is a flat surface. If p > 3, it becomes hard to visualize, but still it can be mathematically defined.

A hyperplane in a two-dimensional space can be expressed as:

1  β[0] + β[1]x[1] + β[2]x[2] = 0

Where (x[1], x[2]) are points of a 2-dimensional space and β[0], β[1], β[2] are some constants. The equation 1 tells that any point x = (x1, x2) in a 2-dimensional space that satisfies the equation falls on the hyperplane. Note that the equation 1 can be transformed to y = mx + c, the equation of a straight line.

As a natural extension of this, a hyperplane in a p-dimensional space can be expressed as:

2  β[0] + β[1]x[1] + β[2]x[2] + … + β[p]x[p] = 0

where (x[1], x[2,] …, x[p]) are points of a p-dimensional space and β[0], β[1], β[2], .., β[p] are some constants.

If any specific point x = (x[1], x[2,] …, x[p]) in a p-dimensional space for which the equation (2) holds true, the point lies on the hyperplane.

Now, for a point x = (x[1], x[2,] …, x[p]), if:

3  β[0] + β[1]x[1] + β[2]x[2] + … + β[p]x[p] > 0

Then the point lies on one side of the hyperplane.

Similarly, if the point x = (x[1], x[2,] …, x[p]) is such that:

4  β[0] + β[1]x[1] + β[2]x[2] + … + β[p]x[p] < 0

Then this point lies on the other side of the hyperplane.

A hyperplane actually separates the p-dimensional space into two parts, all the points for which 3 is true falls on one side and all the points for which 4 is true falls on the other side of the hyperplane. This concept is shown in the [Figure 2.21](#02_003.html#f2.21).

[![Hyperplane in a Two-Dimensional Space.](bilderklein/klein02_021.png)](img-f2.21.html) 

**Figure 2.21**    Hyperplane in a Two-Dimensional Space.

This very property of a hyperplane can be used for classification problems. Suppose we have p predictors X[1], X[2], .., X[p] which fall under two classes, Y = 1 and Y = -1. Now if the training records with Y = 1 fall on one side of a hyperplane and the training records with Y = -1 fall on other side of the hyperplane, then the hyperplane can be used for separating the classes. For a new test record, then it amounts to check which side of the hyperplane it falls, accordingly we predict its value for Y. This hyperplane is called a separating hyperplane.

So, the question is how to select a separating hyperplane, if it exists? We may mathematically formulate the problem like this.

We want to find constants β[0], β[1], .., β[p] such that:

5  β[0] + β[1]x[1] + β[2]x[2] + … + β[p]x[p] > 0 if y = 1

6  β[0] + β[1]x[1] + β[2]x[2] + … + β[p]x[p] < 0 if y = -1

The equations 5 and 6 can be put together into one equation:

7  y(β[0] + β[1]x[1] + β[2]x[2] + … + β[p]x[p]) > 0

Note that this method will not work if the predictors of two classes do not lie on two different sides of a hyperplane, in other words, they are not linearly separable. We can still use this concept with some changes, we will discuss on it later part of this section. Also, if there is a separating hyperplane, then there could be infinitely many of them, we can get a new separating hyperplane by tilting an existing hyperplane slightly so that still the observations from two classes fall under two sides of the hyperplane. These concepts are shown in [Figure 2.22](#02_003.html#f2.22).

[![Example of No Separating HyperplaneHyperplaneseparating and Many Separating Hyperplanes](bilderklein/klein02_022.png)](img-f2.22.html) 

**Figure 2.22**    Example of No Separating Hyperplane and Many Separating Hyperplanes

When there are many such separating hyperplanes, how to choose the best one? If we draw a perpendicular from each training data onto a hyperplane, the perpendiculars will give the distance of the respective points from the hyperplane. The smallest of these distances is called the margin of the hyperplane, since it gives a band around the hyperplane and none of the observations fall within this band. Some observations will of course lie on the margin. [Figure 2.23](#02_003.html#f2.23) 1 shows two such separating hyperplanes and their margins. When a separating hyperplane exists, a natural choice is to select the one with highest margin. This hyperplane is called the maximal margin hyperplane. Since it has the maximum margin, during the prediction even if some new observations fall within the margin, there will be high chance to predict it correctly. The hyperplane in the [Figure 2.23](#02_003.html#f2.23) 2) is indeed a maximal margin hyperplane.

The observation points in training data lying on the margin of the hyperplane are called support vectors. It turns out that these support vectors only contribute while finding the maximal margin hyperplane. The points further from margin do not have any role to play, even if we make changes to their positions as long as they stay on the same side and do not cross the margin, the same hyperplane will be the maximal margin hyperplane.

[![Margin of Separating Hyperplanes](bilderklein/klein02_023.png)](img-f2.23.html) 

**Figure 2.23**    Margin of Separating Hyperplanes

With the same setup as equation 7, finding this hyperplane then boils down to finding the values of β[0], β[1], .., β[p] such that:

*   β[0], β[1], .., β[p] Maximizes M
    
    subject to 8 ![inline image](bilder/EQ_076.png)
    
*   9 y[i](β[0] + β[1]x[i1] + β[2]x[i2] + … + β[p]x[ip]) ⩾ M for all i = 1, 2, .., n
    

The equation 8 does not put any restriction as such on the hyperplanes. The hyperplanes are scale invariants in their parameters (the hyperplanes defined by \[β[0], β[1], .., β[p]\] and \[cβ[0], cβ[1], .., cβ[p]\] are the same), where c is a constant. Hence, we only restrict our search of β values only within the unit circle. Also, note that M > 0 if a separating hyperplane exists; since in that case equation 7 holds well. This M plays the role of the maximal margin, because any point in the observation set is at least M unit away from the hyperplane.

In reality, we may not always have observations from two classes fall on two sides of a hyperplane. We may still address those problems by:

1.  Allowing some overlapping, if the number of such overlapping is less. [Figure 2.24](#02_003.html#f2.24) 1 shows one such scenario, where we allowed few observations to overlap. This is called support vector classifier or a soft margin classifier.
    
2.  Creating additional predictors, if the observations from two classes are separable by a boundary which is highly non-linear. In this case, we may add some transformed values of the predictors as new predictors, say the square terms of the predictors. So with original set of predictors X[1], X[2], .., X[p] , we may create another set predictors X[1]², X[2]², .., X[p]² . Then we try to fit a soft margin hyperplane with all the 2p predictors X[1], X[1]², X[2], X[2]², .., X[p], X[p]². Note that if such a hyperplane exists, then y(β[0] + β[11]x[1] + β[12]x[1]²\+ β[21]x[2] + β[22]x[2]²… + β[p1]x[p2]²) > 0 for most of the records.
    
    Although this is linear in terms of X[1], X[1]², X[2], X[2]², .., X[p], X[p]² , it is non linear in terms of X[1], X[2], .., X[p] . This way, we allow non-linearity in the model. In practice, some functions called Kernel functions are used to get the transformation of predictors. This method is called Support Vector Machine (SVM). The underlying mathematics is complex and not part of the scope of this book, hence we omit it. [Figure 2.24](#02_003.html#f2.24) 2 shows the boundary created by SVM for a data with highly non-linear boundary.
    

[![Models after Fitting Support Vector Classifier and Support Vector Machine](bilderklein/klein02_024.png)](img-f2.24.html) 

**Figure 2.24**    Models after Fitting Support Vector Classifier and Support Vector Machine

###### Advantages and Disadvantages of Support Vector Machines

The support vector machines are one of the best out-of-box classifiers. The major advantages of SVM are:

*   SVM can very well handle the non-linear cases. The Kernel function provides the real strength of SVM. With an appropriate Kernel function, SVM can solve complex problems very efficiently.
    
*   The risk of overfitting is less in SVM.
    
*   SVM handles high dimensional data efficiently. Even the cases where the number of training records are less than the number of predictors, SVM can provide effective solution.
    
*   Small changes in the data does not heavily impact the hyperplanes, hence SVM provide robust classifier.
    

However, SVM has some disadvantages as well, some of them are listed here:

*   Finding the appropriate Kernel function may not be very easy.
    
*   SVM takes long training time, if the number of observations in the training data is high.
    
*   The training algorithm is complex and very memory intensive.
    
*   The resulting model is difficult to interpret. It does not provide any natural interpretation of the parameters and impact of individual predictors.
    

#### Artificial Neural Network (ANN)

Artificial neural network (ANN) is a machine learning technique that attempts to mimic the learning mechanism of human brain. The human brain is composed of numerous building blocks or cells called neurons. The neurons have a cell body, multiple receptors called dendrites and one transmitter unit called axon. Neurons receive nerve impulses from surrounding neurons through the dendrites, processes these collected impulses and then passes the resulting impulse to the neighboring neurons through the axon. The exchange of nerve impulses from one neuron to another takes place through Synapses, which acts as connectors between axon of the sender neuron and dendrites of the receiver neuron. Neurologists have discovered that brain learns through this complex network of neurons, by adjusting the strength of synoptic connections under repeated stimulation by the same impulse.

Motivated by this biological neural network, the artificial neural network has been developed using interconnected network of nodes (like neurons) and directed links (like synopses). The network has a layer of input nodes, one or multiple output nodes and optionally a set of intermediate or hidden layers of nodes. Input nodes simply take the input data and passes it onto the nodes in the next layer through the directed links, each node in the next layer combines the input received through applying some function and then passes it onto the nodes in the next layer (sometimes to the same or previous layers in some specific ANNs). The nodes in the output layer similarly process the input from previous layer and provides the output. The links between the nodes are typically assigned with a weight, so the value passed through the links are adjusted with these weights. These weights in the links are adjusted to make incoming information strong or weak, to emulate strength of a synoptic connections. The entire arrangement of nodes with the links is called the network topology. There are different types of ANNs based on the types of network topology. [Figure 2.25](#02_003.html#f2.25) shows the biological neuron 1 and a typical neural network 2.

[![Biological Neuron and Artifical Neural Network](bilderklein/klein02_025.png)](img-f2.25.html) 

**Figure 2.25**    Biological Neuron and Artifical Neural Network

ANN is a widely used in machine learning for recognizing complex non-linear patterns in the data. They have applications in many areas including computer vision, image recognition, speech recognition, medical diagnosis, autonomous robots.

##### Perceptron

Let’s understand the concept further with the simplest type of neural networks, called perceptron. Perceptron has one layer of input nodes and one output node. [Figure 2.26](#02_003.html#f2.26) 1 shows a data set with three predictors (or input variables) X[1], X[2], X[3] and one response (or output variable) Y. The input variables X[1], X[2], X[3] takes values 0 or 1. If at least two of these three inputs are 1, the output is 1, otherwise -1. You may relate it with outcome of three successive tosses of a coin, A person wins if at least two tosses result in head. X[1], X[2], X[3] are the results of the tosses, where head is denoted as 1, tail as 0. Y is the final output, 1 means winner and -1 means looser. [Figure 2.26](#02_003.html#f2.26) 2 shows a perceptron model for this data.

[![A Simple Perceptron Model for a Classification Problem](bilderklein/klein02_026.png)](img-f2.26.html) 

**Figure 2.26**    A Simple Perceptron Model for a Classification Problem

There are three input nodes, each for one input variable and one output node which gives the estimated value of Y. All the links between the input nodes to the output node have equal weight 0.4. The output node performs weighted sum of the input, then subtracts a bias t from the sum and then checks the sign of the result. If the sign is positive, the output is 1, otherwise output is -1. This can be mathematically written as:

1  ![inline image](bilder/EQ_022.png)\= 1 if w[1].x[1] + w[2].x[2] + w[3].x[3] – t > 0

2  ![inline image](bilder/EQ_022.png)\= -1 if w[1].x[1] + w[2].x[2] + w[3].x[3] – t < 0

where x[1], x[2], x[3] are typical values of X[1], X[2], X[3] and ![inline image](bilder/EQ_022.png)is the associated predicted value of Y. w[1], w[2], w[3] are weights, and t is the bias.

You may check with some sample values to satisfy yourself that this perceptron model provides the right classification. For example, when x1 = 1, x2 = 0, x3 = 1, the output is 1, since two of the 3 inputs are 1. As per equations 1 and 2, ![inline image](bilder/EQ_022.png)\= 1 in this case, since 0.4 x[1] + 0.4 x[2] + 0.4 x[3] – 0.6 = 0.4 + 0 + 0.4 – 0.6 = 0.2 > 0. So, this record is correctly classified. Similarly, if x1 = x2 = x3 = 0, then ![inline image](bilder/EQ_022.png)\= -1, since 0.4 x[1] + 0.4 x[2] + 0.4 x[3] – 0.6 = -0.6 < 0.

Let’s have a close look into equations 1 and 2. It can be rewritten as:

3  ![inline image](bilder/EQ_022.png)\= 1 if 0.4 (x[1] + x[2] + x[3]) – 0.6 > 0

4  ![inline image](bilder/EQ_022.png)\= -1 if 0.4 (x[1] + x[2] + x[3]) – 0.6 < 0

Note that (x[1] + x[2] + x[3]), being the sum of 3 input variables, has only 4 possible values: 0, 1, 2, 3.

At least 2 inputs are 1 ⬄ (x[1] + x[2] + x[3]) ⩾ 2 ⬄ 0.4 (x[1] + x[2] + x[3]) ⩾ 0.8 ⬄ 0.4 (x[1] + x[2] + x[3]) - t ⩾ 0.8 – t.

Now, if 0.8 > t => 0.8 – t > 0 => 0.4 (x[1] + x[2] + x[3]) – t > 0

Similarly, at least 2 inputs are 0 ⬄ (x[1] + x[2] + x[3] ) ⩽ 1 ⬄ 0.4 (x[1] + x[2] + x[3] ) ⩽ 0.4 ⬄ 0.4 (x[1] + x[2] + x[3] ) – t ⩽ 0.4 – t.

If t > 0.4 => 0.4 – t < 0 => 0.4 (x[1] + x[2] + x[3] ) – t < 0

So, any value of t such that 0.4 < t < 0.8 will give the correct output. We have chosen t = 0.6.

In this example, we could mathematically validate the values of w[1], w[2], w[3], t to make it a correct model. However, in practice, models can be quite complex. So, these values are not derived mathematically, rather we start with one set of values and then gradually adjust the values through multiple iterations to arrive at the right model. This process of gradually adjusting the model to arrive at an optimal model is called learning.

For a general perceptron model, the estimated output can be written as

![inline image](bilder/EQ_022.png)\= sign(w[1].x[1] + w[2].x[2] + w[3].x[3] + … + w[p]x[p] – t)

Where x1, x2, .. x[p] are input from p Predictors and w[1], w[2] ,.., w[p] are the weight of the input links. The sign function gives sign of the argument, it is +1 when argument is positive and -1 when argument is negative. In ANN context, it is an activation function.

It can be more compactly written as:

5  ![inline image](bilder/EQ_022.png)\= sign(w[0].x[0] +w[1].x[1] + w[2].x[2] + w[3].x[3] + … + w[p]x[p]) = w.x

where w and x are the weight vector and input vector respectively, w.x is their dot product. Note that w[0] = -t and x[0] = 1, and it takes care of the bias term t.

##### Training the Perceptron

During the training phase of a perceptron model, the weights are adjusted until the model can correctly estimate output for all records in the training data. The learning process has the following steps:

1.  First, the weights are initialized with random values.
    
2.  For the i-th record in the training data, the estimated output ![inline image](bilder/EQ_078.png)is computed using the equation 5.
    
3.  Each weight is adjusted using the following formula:
    
    6  ![inline image](bilder/EQ_077.png)[  
    ]Where w[j]^((k)) is the weight associated with the j^(th) input link in the k^(th) iteration, x[ij] is the value of j^(th) predictor in the i^(th) record in training data, y[i] is the actual output of the i^(th) record of training data, ![inline image](bilder/EQ_078.png)is the estimated output for the i^(th) record in the k^(th) iteration, λ is a parameter known as learning rate.
    
4.  Step 2 and step 3 are repeated for all records in the training data (for all values of i).
    
5.  Steps 2, 3, 4 are repeated (iterated for values of k = 1, 2, 3, and so on) until a stopping criterion is reached. A stopping criterion could be that all the output values are correctly estimated or the number of iterations reaches a threshold value.
    

The weight adjustment formula in equation 6 can be interpreted as:

*   If the estimated value of an output is equal to the actual value, no need to adjust the weights in the next iteration.
    
*   If the actual output is +1 and the estimated output is -1, (y[i] – ![inline image](bilder/EQ_078.png)) = 2. Then increase the weight of all the links with positive input and decrease the weight of all the links with negative input. The resulting weights will increase the weighted sum (w.x) for that record.
    
*   If the actual output is -1 and the estimated output is +1, (y[i] – ![inline image](bilder/EQ_078.png)) = -2. Then decrease the weight of all the links with positive input and increase the weight of all the links with negative input. The resulting weights will decrease the weighted sum (w.x) for that record.
    

The learning rate λ takes the value between 0 and 1. It regulates the adjustment, so that a recent adjustment does not drastically change the previous adjustments. This way, it helps the model to converge to an optimal solution, if exists.

It is not guaranteed that the perceptron learning algorithm will always converge to an optimal model. It can be shown that the if the classification problem is linearly separable. In other words, the records pertaining to two different classes can be separated by a hyperplane, the learning algorithm converges to an optimal solution, provided λ is sufficiently small. If the problem is not linearly separable, the perceptron learning algorithm does not converge.

##### Multilayer Artificial Neural Network

The multilayer artificial neural network has one or more intermediate layer(s) between the input and output layer. These layers are known as hidden layers and the nodes in the hidden layers are called hidden nodes. If the nodes in one layer send data only to the nodes in the next layer, then it is called a feed-forward neural network. In a recurrent neural network, the nodes in one layer may send data to the nodes in the same layer or even to the previous layers. The directed links in the neural network indicates the flow of data.

Also, the neural networks may use different types of activation functions apart from sign function, like linear, sigmoid (logistic), hyperbolic tangent functions. Non-linear functions are used to model non-linear relationship between the input and output variables. [Figure 2.27](#02_003.html#f2.27) 1 shows a sample data for XOR logic and how the decision boundary looks like. For this data, two separating hyperplanes required to classify the data and cannot be mapped with a single perceptron. [Figure 2.27](#02_003.html#f2.27) 2 shows a multilayer ANN that can be constructed to model this data.

[![Example of Multilayer Neural Network](bilderklein/klein02_027.png)](img-f2.27.html) 

**Figure 2.27**    Example of Multilayer Neural Network

Conceptually, we may consider a feed-forward multilayer neural network as a collection of perceptron networks, each node in the hidden layers and the output node can be considered as an output node of a perceptron, which receives input from the previous layer and gives an output.

###### Designing an ANN model

Consider the following while designing an ANN model:

*   The predictors could be a quantitative or a categorical variable. Each quantitative or binary categorical variable to be assigned to one node in the input layer. For a categorical variable with more than two values, say m values, either m input nodes to be created, one for each value or the categorical variable can be encoded with ![inline image](bilder/EQ_079.png)binary variables and one node to be assigned for each of the binary variables.
    
*   If the response is a 2-class categorical variable, one output node will be enough. For a categorical response with k classes, where k is greater than 2, k output nodes to be created.
    
*   The network topology needs to be carefully selected. Deciding on the number of hidden nodes and layers is not easy. One approach would be to start with sufficiently large number of hidden nodes and layers and then reducing the size of the network.
    

##### Training the Multilayer ANN

Due to the inherent complexity in a multilayer ANN, the associated learning algorithms are also complex in nature. Here we outline the basic principle adopted while training a multilayer ANN.

The goal of the ANN learning algorithm is to determine a weight vector (a set of weights) w ![inline image](bilder/EQ_081.png)that minimizes the error in the model, based on training data. The error is measured through the total sum of squared errors (TSS), defined as:

![inline image](bilder/EQ_080.png)

Where n is the total no of records in the training data, y[i] and ![inline image](bilder/EQ_051.png)are the actual and predicted value of the response corresponding to the i^(th) record. Note that we have used ½ as the factor, this gives us some benefit during mathematical calculation. Also note that this error is a function of the weights w as the error is dependent on predicted values of the response, which are in turn dependent on the weight w.

In case of a multilayer ANN learning, there are two major challenges:

*   The activation function may not be a sign function, it may be a non-liner function as well. An effective method to be devised capable of handling different types of activation function.
    
*   We know the input values of the input layer and output value of the output layer, but we do not have information on what would be an optimal output of the intermediate hidden nodes.
    

First challenge is taken care of by an optimization method known as gradient descent method. The weights are adjusted in gradient descent method through the following formula:

![inline image](bilder/EQ_082.png)

![inline image](bilder/EQ_083.png)is the partial differentiation of error function with respect to the j^(th) weight, λ is the training rate.

Loosely speaking, it says if F(x) is a multivariate function differentiable around a neighborhood of a point x = a, then F(x) decreases fastest if one goes from a to the direction of negative gradient of F(x). The gradient is another terminology for slope. As an analogy of this principle, if someone is stuck in a mountain at dark night and wants to descent to the plane land (the global minimum from height perspective) then they should move towards negative direction of the slope. The person cannot see around, but they have an instrument which measures the slope. The mountain may have different slope at different points. So, after moving a while, the person needs to correct their course again by checking the slope and moving towards negative direction of the slope. However, in this process, the person may end up landing in a mountain lake or a hole (local minimum) and stuck there forever, because any attempt to move to negative direction of slope will bring them back to the same point. Similarly, gradient descent method may not give weight values that give global minimum of error, but it may end up with a local minimum, due to non-liner error function.

The second challenge is taken care of by a technique called back-propagation. In this algorithm, each iteration has two phases, a forward phase and a backward phase. In the forward phase, the weights obtained from the previous iteration are used to compute the output of each node in forward direction, the output of nodes at layer m are computed first before computing output of nodes in the layer m + 1. In the backward phase, the weights are adjusted using gradient descent method in reverse direction, the weights at layer m + 1 are adjusted first before adjusting the weights at layer m. The iterations are continued until a stopping criterion is attained.

###### Advantages and Disadvantages of ANN

The advantages and disadvantages of ANN are summarized here:

*   Multilayer Neural Network with at least on hidden layer are universal approximators, they can approximate any function. So, if the problem space is highly non-linear, it can be suitably modelled with ANN. However, this very nature can lead to overfitting.
    
*   ANN can handle redundant predictors. The weights associated with redundant predictors are adjusted automatically to small values.
    
*   There is no profound mathematical theory behind deciding the network topology. The reason being high number of parameters (weights and bias) associated with the model and their interactions. Some types of networks work better for certain types of problems, but mostly the network architecture is designed based on experience or through hit and trial method.
    
*   ANN models are quite sensitive to noise in the training data. To judge the model accuracy, a validation data may be used.
    
*   Training ANN is a time-consuming process, especially if number of hidden layers and nodes are high.
    
*   The gradient descent method for training ANN may converge to a local minimum, resulting in sub-optimal model.
    
*   ANN models do not give any natural interpretation of the associated weights. They do not provide any insight on which predictors are influential and their degree of influence. ANNs are better suited for prediction and not for relationship detection.
    

#### Classification Model Comparison and Other Considerations

In this chapter, we have discussed about six different machine learning methods to handle classification problems. There are many other methods also, and each method has several extensions. Covering all them would result in a very fat book, and it is not our aim also. We tried to give you a glimpse of different approaches, from simple k‐nearest neighbor to highly complex artificial neural network. Also, we have discussed about the advantages and disadvantages of each approaches. There is no universally superior classification algorithm, all have some merits and demerits.

While solving a classification problem, there are various factors that need to be considered, like nature of the data, number of predictors, size of the training data, number of response classes, quality of the training data like presence of missing values, outliers, high leverage points, sparsity of the data. All these considerations would help to identify a suitable algorithm for developing the model and prediction. Also, any insight from business perspective would be of great help.

The details of the model building approach have been discussed in [Chapter 3](#03_001.html#h3). For classification problems, we suggest to follow a keep it simple approach while choosing the algorithm. First start with a simple model and assess predictive power of the model using cross-validation or validation data approach. If it gives good predictions, then do not attempt to fit a complex model to the problem. Otherwise go on fitting more and more complex methods, keeping in mind the advantages and disadvantages of each method.

### 2.3.3    Cluster Analysis

Cluster analysis or clustering is an unsupervised learning method to find subgroups or clusters within the dataset. In clustering, the data is partitioned into multiple clusters or subgroups so that the observations within a cluster are similar or homogeneous and observations between clusters are dissimilar or heterogeneous. As an example of clusters found in nature, we may consider the different galaxies of stars. Stars within a galaxy are close to each other and stars between different galaxies are far apart. Here distance serves as a measure of closeness or similarity. Even galaxies can be further grouped into clusters and superclusters.

Similar situation may occur in the business world as well. Suppose a retail store wants to launch a marketing campaign and they want to send offers to individual customers based on their buying patterns. However, it is not feasible to plan promotional offers for every individual customer; rather, the company is interested to know if there is any natural grouping of the customers based on their buying patterns. It may reveal different groups of customers like frequent buyers with low value purchases, infrequent buyers with high value purchase, infrequent buyers with low value purchases, one time buyers, buyers purchasing mainly one type of products like food items, electronic gadgets, buyers purchasing multiple types of products. Then different type of offers may be designed for different groups and individuals within one group receive the same offer. As another example, a pharmaceutical company researching on medicine of a particular disease may be interested to know if there are different subtypes of the disease based on the data on patients across different attributes like age, gender, symptoms, severity of illness, result of diagnostic tests, duration of illness. This information may help them to decide if different medicines are required for the subgroups.

###### Types of Clustering

Based on how observations are segregated across clusters, there can be different types of clustering, including:

*   Partitional clustering: each observation in the data is assigned to one and only one cluster.
    
*   Hierarchical clustering: the clusters are arranged in a hierarchical fashion, so one observation may fall under multiple clusters at different levels in the hierarchy.
    
*   Fuzzy clustering: every observation belongs to every cluster with a membership weight between 0 (does not belong to a cluster) and 1 (absolutely belongs to a cluster).
    

Also, sometimes clustering may be partial in the sense that some observations do not belong to any cluster. These observations may be outliers, noises or do not belong to any well-defined group.

Before we proceed to different clustering algorithms, let’s look at [Figure 2.28](#02_003.html#f2.28) to understand the notion of clustering and few important concepts. [Figure 2.28](#02_003.html#f2.28) 1 shows scatter plot of 33 customers against two attributes, say attribute 1 and attribute 2. It shows data is not distributed randomly, rather concentrated around two areas, low value of both the attributes and high value of both the attributes. The data points within each of these two groups are very close to the data points in the same group and they are far apart from data points of the other group. These groups are called clusters. The data shows customers are segregated into two prominent clusters ([Figure 2.28](#02_003.html#f2.28) 2). Further, on a closer look, it seems that each of these clusters is a collection of two subgroups which are centered around two different points, so we may consider four clusters, as shown in [Figure 2.28](#02_003.html#f2.28) 3.

In this example, when we noticed two prominent clusters in [Figure 2.28](#02_003.html#f2.28) 2, we mainly used the notion of distance between data points. We also used the notion of shape and center of data points for identifying four clusters in [Figure 2.28](#02_003.html#f2.28) 3. These are some important features for identifying clusters.

Identifying clusters in [Figure 2.28](#02_003.html#f2.28) was easy, we had just two attributes and we had to inspect only one scatter plot. However, if we had 50 attributes, then it would have been impossible to identify clusters just by visual inspection. Moreover, if we had much more observations, then it would have even more difficult, may be magnifying the plot would have revealed further sub-clusters. Hence, various algorithms have been developed to find clusters within the data, without the need for manual intervention. These algorithms use the notion of distance, center, shape, contiguity, density in identifying natural clusters within the dataset.

[![Example of Clusters in Data](bilderklein/klein02_028.png)](img-f2.28.html) 

**Figure 2.28**    Example of Clusters in Data

The simple example in [Figure 2.28](#02_003.html#f2.28) also motivates us to consider following important questions on clustering in general:

*   How many clusters are there in the data?
    
*   How to measure the closeness of different observations (different data points)?
    
*   How to decide whether two data points are part of the same cluster or different clusters?
    

Different algorithms address these questions differently and each algorithm has strengths and weaknesses. Also, there are different extensions of the algorithms to address some known issues. Depending on the use case and nature of the data, appropriate algorithm needs to be used for clustering. We have covered here three widely used clustering algorithms in machine learning.

#### K-Means

K-means is a simple algorithm to obtain partitional clusters. The observations are divided into k clusters, where k is specified by the user. The clusters are formed around k centroids. In other words, centers of data points and these centroids are adjusted iteratively. The algorithm first starts with an initial set of k centroids, which serve as the centers of k clusters. Then each data point is assigned to a cluster whose centroid is closest to the data point. Once all points are put into clusters, the centroids are recalculated as the mean of all data points within the cluster. Then with these new centroids, the datapoints are again segregated into k clusters. This process of recalculating the centroids and assigning data points to cluster continues until there is no change in the centroids. The k-means algorithm has the following steps:

1.  Select k points as the initial centroids, say m[1], m[2], …, m[k].
    
2.  Form k clusters C[1], C[2], …, C[k] by assigning each data point x to the closest centroid. In other words, x ∊ C[i] if d(m[i], x) ⩽ d(m[j], x) for all j ≠ i, 1⩽ i, j ⩽ k. Here d(a, b) is a function which measures distance between two points a and b. Choices of this function is discussed subsequently.
    
3.  Based on the clusters obtained in previous step, recalculate the centroids as the mean values of the data points within the clusters. In other words, m[i] = (∑[x∊Ci] x)/n[i] where n[i] is the number of data points in the i-th cluster, 1⩽ i ⩽ k.
    
4.  Check if there is any change in the centroids. If no change, then declare C[1], C[2], …, C[k] as the final set of clusters. If there is a change, rebuild clusters C[1], C[2], …, C[k] using the new centroids (like in step 2).
    
5.  Repeat steps 3 and 4 until final set of clusters obtained.
    

[Figure 2.29](#02_003.html#f2.29) shows the execution of the algorithm with a simple dataset. The data points are shown as blue dots and the centroids as red plus signs. In this example, the value of k is 3. [Figure 2.29](#02_003.html#f2.29) 1 shows the data points with initially selected three centroids. Next, three clusters C[1], C[2,] and C[3] are formed based on the distance of the data points from these centroids, shown in [Figure 2.29](#02_003.html#f2.29) 2. Then centroids are recalculated using clusters in [Figure 2.29](#02_003.html#f2.29) 2 and new clusters are formed, as shown in [Figure 2.29](#02_003.html#f2.29) 3. This process is repeated, the new centroids and clusters are shown in [Figure 2.29](#02_003.html#f2.29) 4. Note that the clusters in [Figure 2.29](#02_003.html#f2.29) 3 and [Figure 2.29](#02_003.html#f2.29) 4 are identical, hence, there will be no change in centroids. So, we have got the final set of clusters.

###### Note

Each data point is a collection of values of the attributes: a vector in mathematical terminology. So, the mean and distance function are calculated using vector arithmetic. For example, if we have customer data with three attributes and two customers X and Y have values of these attributes (x[1], x[2], x[3]) and (y[1], y[2], y[3]) respectively, then their mean value is a vector ((x[1]+y[1])/2, (x[2]+y[2])/2, (x[3]+y[3])/2). Also, the Euclidean distance between the data points of customers X and Y is calculated as ![inline image](bilder/EQ_084.png). In general, if n attributes are there in the dataset, each data point can be considered as a vector in a n-dimensional space.

[![Clustering using K-Means Algorithm](bilderklein/klein02_029.png)](img-f2.29.html) 

**Figure 2.29**    Clustering using K-Means Algorithm

The k-means algorithm is very simple and converges fast compared to other algorithms, however, success to find natural clusters within data depends on two important factors:

*   The value of k (the number of clusters). Wrong choice may not provide the natural grouping within the data.
    
*   The choice of initial centroids. A poor selection of initial centroids may lead to suboptimal clusters.
    

In k-means, we have used a function to calculate the distance between a data points and the centroids and put the data point to the cluster where the distance is minimum. One natural choice of this function is the Euclidean distance or squared Euclidean distance, which generalizes the notion of distance in a multi-dimensional space. However, there are other measures of divergence or dissimilarity which can also be used depending on the nature of data. [Table 2.5](#02_003.html#t2.5) shows some of the common measures.

 
| Measure of Distance or Divergence || Behavior || When to Use It |
| --- | --- | --- |
| Euclidean distance or squared Euclidean distance || Lower the value, higher the proximity. || If we need to know the actual distance between two data points in a n‐dimensional space. |
| --- | --- | --- |
| Cosine similarity || Higher the value, higher the proximity. (hence a data point is put to a cluster where cosine against the centroid is highest). || This metric gives the cosine of the angel between two vectors in a n‐dimensional space. It overlooks the actual magnitude of the vectors and measures how close they are in terms of the angel between them. This metric is often used to determine similarity between two documents. |
| Bregman divergence || Lower the value, higher the proximity. || This is a class of distance measures defined in terms of a strictly convex functions. Distance measures like squared Euclidean distance, Squared Mahalanobis distance are special cases of Bregman divergence. Bregman divergence may be used when we are interested in statistical distance of data points from probability distributions. |

**Table 2.5**    K-Means: Some Common Distance Measures

###### Note

The k-means algorithm minimizes the sum of squared error (SSE) defined as:

SSE = ![inline image](bilder/EQ_085.png)

where m[i] are cluster means (centroids), k is the number of clusters, Ci is the i-th cluster, and d() is the distance function. Successive iterations of recalculating the centroids and rebuilding the clusters minimizes the SSE, but it is for the specific choice of centroids and clusters. So, when the algorithm stops, it reaches a local minimum of SSE. It may not be global minimum of the SSE (the minimum SSE for all possible k clusters of the dataset).

###### Advantages and Disadvantages of K-Means Clustering

The main advantages of k-means algorithm are:

*   k-means is a simple clustering algorithm and easy to implement.
    
*   The convergence of k-means algorithm is guaranteed. It converges fast, typically with less number of iterations.
    
*   k-means perform well with very large dataset.
    
*   It provides tighter clusters, specially when the clusters are convex (spherical in nature).
    
*   It can easily adapt to addition of new data point.
    

However, there are few disadvantages of k-means algorithm, some of them are listed here:

*   The number of clusters, as in the value of k is chosen manually. Methods like silhouette and elbow may be used to determine the number of clusters, but the k-means algorithm does not determine it internally.
    
*   Poor choice of initial centroids may lead to suboptimal clusters.
    
*   May result in empty clusters (a cluster without any data points). The incremental updating of centroids, recalculating them after assignment of each data point can resolve this issue. However, then clustering may become dependent on the order in which the data points are processed.
    
*   K-means is sensitive to outliers and noises.
    
*   K-means is not suitable for all types of datasets, specially if the natural clusters are not convex or spherical. Also, it cannot handle clusters of different sizes and densities.
    

#### Hierarchical Clustering

Hierarchical clustering is another important type of clustering often used in machine learning. In hierarchical clustering, the clusters are formed in a hierarchical fashion, so one data point can be in multiple clusters in the different levels of the hierarchy. There are two types of hierarchical clustering:

1.  Agglomerative  
    Starts with all data points as individual clusters, then at each step merges two closest pairs of clusters together unless the entire dataset becomes a single cluster.
    
2.  Divisive   
    Starts with entire dataset as one cluster, then at each step splits a cluster into two clusters unless the individual data points become singleton clusters.
    

The agglomerative hierarchical clusters are mostly used in practice; hence we will mainly focus on it in this section and will briefly touch upon the divisive clusters.

##### Agglomerative Hierarchical Clustering

The agglomerative hierarchical clustering steps are described below:

1.  Take all individual data points as singleton clusters.
    
2.  Compute the proximity matrix of the clusters, if required.
    
3.  Merge the closest two clusters.
    
4.  Update the proximity matrix with proximity between the new cluster and remaining clusters.
    
5.  Repeat step 3 and 4 unless only one cluster remains.
    

The hierarchical clustering is often displayed through a tree-like diagram called dendrogram. For two-dimensional data points, the clustering can also be displayed using nested cluster diagram. [Figure 2.30](#02_003.html#f2.30) shows agglomerative clustering of 6 data points on a two-dimensional space. The original data points p1, p2, …, p6 are shown in [Figure 2.30](#02_003.html#f2.30) 1. The data is clustered through agglomerative hierarchical clustering, [Figure 2.30](#02_003.html#f2.30) 2 shows the associated nested cluster diagram, the C1, C2, …C5 are the clusters formed successively. The dendrogram for this clustering is shown in [Figure 2.30](#02_003.html#f2.30) 3.

[![Agglomerative Hierarchical Clustering](bilderklein/klein02_030.png)](img-f2.30.html) 

**Figure 2.30**    Agglomerative Hierarchical Clustering

The main operation in agglomerative clustering is the computation of proximity measure between two clusters. There are various measures of cluster proximity, [Table 2.6](#02_003.html#t2.6) shows the definition of different measures. [Figure 2.31](#02_003.html#f2.31) further illustrates the concept.

 
| Proximity Measure || Definition |
| --- | --- |
| Single Linkage (or MIN) || The proximity of two clusters is the minimum distance between any two points from two different clusters. In other words, the distance between two clusters C1 and C2 is min [x ∊ C1, y ∊ C2] d(x, y) where d is the distance function. |
| --- | --- |
| Complete Linkage (or MAX) || The proximity of two clusters is the maximum distance between any two points from two different clusters. In other words, distance between two clusters C1 and C2 is max [x ∊ C1, y ∊ C2] d(x, y) where d is the distance function. |
| Group Average || The proximity of two clusters is the average of distances between all pairs of points in two different clusters. In other words, distance between two clusters C1 and C2 is (∑ [x ∊ C1, y ∊ C2] d(x, y)) /(n[1].n[2]) where d is the distance function and n[1], n[2] are the number of data points in clusters C1 and C2 respectively. |

**Table 2.6**    Different Proximity Measures for Agglomerative Clustering

[![Calculation of Proximity Measures](bilderklein/klein02_031.png)](img-f2.31.html) 

**Figure 2.31**    Calculation of Proximity Measures

[Figure 2.31](#02_003.html#f2.31) shows the calculations of different proximity measures. The data points and their coordinated are shown in [Figure 2.31](#02_003.html#f2.31) 1 and [Figure 2.31](#02_003.html#f2.31) 2. The distances between pairs of points from both the clusters are calculated in [Figure 2.31](#02_003.html#f2.31) 3. Based on this cross-cluster distance matrix, various proximity measures are calculated in [Figure 2.31](#02_003.html#f2.31) 4. Note that these measures involve length of one or more edges connecting data points between the two clusters.

[Figure 2.31](#02_003.html#f2.31) shows how to calculate the proximity measure between two clusters. While merging two clusters in agglomerative hierarchical clustering, the proximity measures of all available cluster pairs are considered and clusters having minimum proximity measure value are merged into a single cluster. Depending on the proximity measure, the sequential merging of clusters may be different.

###### Note

*   Ward’s method is another proximity measure which is defined as the increase in the squared error resulting from the merging of two clusters.
    
*   All the proximity measures discussed in this section are variations of Lance-Williams Proximity Formula with different choices of parameters.
    

###### Advantages and Disadvantages of Agglomerative Clustering

The main advantages of agglomerative clustering are:

*   Does not require any pre-defined number of clusters, rather it provides different numbers of clusters at each level.
    
*   Does not depend on any initial points.
    
*   Dendrograms provide nice interpretation of how data points are merged with small datasets.
    

However, there are some disadvantages of this clustering technique, some of them are listed below.

*   Agglomerative clustering has higher order of storage and time complexity. So, it should not be applied for large dataset.
    
*   It does not optimize an objective function globally, rather it tries to optimize locally at each step while merging two clusters.
    
*   Two clusters once merged cannot be unmerged, so the local optimization decisions made at different steps are retained and it may prevent arriving at a globally optimal cluster.
    

##### Divisive Hierarchical Clustering

Divisive hierarchical clustering is a top down approach where initially the entire dataset is considered as a single cluster and at each step one of the clusters is split into two clusters unless all individual data points become singleton clusters.

We may use the k-means clustering to achieve this, at every step we can split a cluster into two clusters. The only thing required is to decide which cluster to split next. This can be done in multiple ways, like splitting the largest cluster at each step or splitting the cluster with highest SSE. Depending on the option chosen, the hierarchy of clusters will be different.

There are various graph partitioning algorithms which can also be applied sequentially to get divisive hierarchical clustering. Minimum spanning tree (MST) clustering can also be used for the same.

#### Density-Based Spatial Clustering of Applications with Noise

Density-based spatial clustering of applications with noise (DBSCAN) is one of the popular and most practiced clustering techniques. This is a density-based clustering approach that can handle noise in the data and identify clusters of arbitrary shapes and sizes, not necessarily only convex or spherical clusters.

DBSCAN identifies clusters based on connectedness between regions with high density data points, separated by regions of low density data points, which are referred as noise or background points. The centre-based approach is applied to measure density. According to this approach, two parameters Eps and MinPts are used to define density. Any data point can be classified into following three categories based on these parameters:

*   Core point  
    A data point is called a core point if it has MinPts many data points in its neighbourhood of radius Eps, including the point itself. There are at least MinPts many data points (including itself) within a distance of Eps around that point.
    
*   Border point  
    A border point is not a core point, but it falls within the neighbourhood of a core point.
    
*   Noise point  
    A noise point is neither a core point nor a border point, so it does not have MinPts many data points within Eps distance around it and none of its neighbors is a core point.
    

[Figure 2.32](#02_003.html#f2.32) shows these three types of points graphically. There are 9 points p1 to p9 and each point has a circle with radius Eps around them. For a particular point, all points (including itself) falling inside its circle are within Eps neighbourhood. We have taken 4 as the value of MinPts. Points p3, p4, p5, p6 each has at least 4 points in their Eps neighbourhood, so these are the core points (marked with green). Points p2, p7 and, p8 each has 3 points in their neighbourhoods, so they are not core points. But each of them has a core point in their neighborhoods, hence they are border points (marked with orange). Points p1 and p9 do not have 4 points in their neighbourhoods, nor any core points, so these are noise points (marked with red).

[![Core, Border, and Noise Points in DBSCAN](bilderklein/klein02_032.png)](img-f2.32.html) 

**Figure 2.32**    Core, Border, and Noise Points in DBSCAN

The DBSCAN algorithm can be described with the following steps. This is not the optimal algorithm from computation perspective but easy to understand:

1.  Mark all data points as core, border, or noise points.
    
2.  Connect all core points that are within Eps neighborhood of each other.
    
3.  Declare each set of connected core points as a cluster.
    
4.  Assign each border point to one of the clusters of the core points within its Eps neighbourhood.
    

Since DBSCAN builds cluster through connecting core points, it can identify clusters of arbitrary shape and size. [Figure 2.33](#02_003.html#f2.33) shows two such clusters of concentric circles, one with blue and other with brown color. DBSCAN can find such natural clusters but k-means will not be able to identify them, as clusters are not linearly separable.

[![Concentric Clusters Identified using DBSCAN](bilderklein/klein02_033.png)](img-f2.33.html) 

**Figure 2.33**    Concentric Clusters Identified using DBSCAN

###### Advantages and Disadvantages of DBSCAN

DBSCAN has some advantages over the other clustering algorithms we discussed:

*   It can identify the natural clusters of any shape and size within dataset.
    
*   No prior information required on the number of clusters.
    
*   It is less sensitive to outliers.
    
*   DBSCAN can identify the noisy data points which cannot be properly put into any clusters.
    

However, DBSCAN has following disadvantages:

*   The clustering depends on two parameters Eps and MinPts. If these values are not selected properly, the resulting clusters may not reflect the natural clusters within the data. One way to handle it is to compute distance of kth nearest neighbour (k-dist) of all data points for some value of k, sort these values in ascending order and see if there is any sharp increase in k-dist values at some point. Then this value can be taken as Eps and k as the MinPts. The sharp increase indicates natural separation of data points, mainly for border and noise points.
    
*   If different clusters have widely varying densities, then choosing the appropriate value of MinPts is difficult. It may identify points of low-density clusters as noises.
    
*   Due to the curse of dimensionality (covered in the next section), data points in high-dimensional data become sparse and makes it difficult to define density properly. If DBSCAN uses Euclidean distance to find neighbours, then it becomes difficult to find an appropriate value of Eps.
    
*   DBSCAN is not completely deterministic on the border points those have core points from different clusters in their neighbourhoods. Depending on the order in which data is processed, the algorithm may put them in any of the neighbouring clusters.
    

### 2.3.4    Other Machine Learning Techniques

Machine learning has thousands of algorithms developed for various purposes. However, it is not possible to discuss all the areas in a single book. We have already discussed about some of the widely used areas in machine learning. In this section we will provide overview of some of other important areas in machine learning, without deep dive into the theoretical part of the associated algorithms.

#### Dimensionality Reduction

Dimensionality of a dataset refers to the number of attributes in the data. If a data contains m attributes, then each record or data point is a tuple of m values, one value for each attribute. In terms of mathematics, each record can be considered as a m-dimensional vector of the values of the attributes and can be represented as a point in the m-dimensional space. For example, if a data contains two attributes, we can consider each record as a point in a two-dimensional space, where X axis and Y axis are represented by the two attributes.

When there are many attributes, the dimensionality of the data increases and we call it a high dimensional data. This introduces a problem called curse of dimensionality. With higher dimensional data, data becomes sparse, every record or observation tend to be far away from each other. As an example, say we have data with only one attribute X, and two records have values 1 and 2 (of X). In one-dimensional space, they are at one-unit distance. However, if we now have another attribute Y with values 0 and 10 for these two records, then we have two points (1,0), (2,10) in 2-dimensional space and their distance is more than 10 units in 2-dimensional space. Likewise, introducing new attributes increases the distance and makes the points far away from each other. So, the machine learning algorithms that depend on proximity of data points, they tend to perform poor in high dimension. Besides, the higher dimensionality introduces other practical problems, two of them are discussed in [Section 2.3](#02_003.html#h2.3) where we looked at dimensionality reduction from data preparation perspective.

There are various use cases where we encounter high dimensional data. Dimensionality reduction algorithms try to map the high-dimensional data into a low dimensional data without losing much information content. We will discuss about one such technique, principal component analysis (PCA) in this section. It is a simple and widely used dimensionality reduction algorithm for continuous attributes.

#### Principal Component Analysis (PCA)

Principal component analysis reduces the number of attributes by considering only a few linear combinations of attributes in such a way that overall variation in the data is not impacted much. Loosely speaking, the idea here is to replace the original attributes by few linear combinations of the original attributes and use these linear combinations in the analysis. However, choosing any linear combination may not be suitable, as they may not capture as much information as possible. So first, the directions are identified where data is mostly spread. In other words, the direction captures most of the variance in the data. However, once we get the first direction in which data is mostly spread, the next direction is search which is perpendicular to the first direction and has the next maximum spread of data (the variance). Similarly, the third direction is chosen which is perpendicular to both the first two directions and captures next most spread of the data. Once these directions are known, the entire data is transformed along these directions. The new values of the data points are actually linear combinations of original attribute values. These directions are known as principal components (PC).

In a high dimensionality data, if it has an underlying relationship, then it will not spread in each direction equally like randomly generated data, it will be spread along few directions that represents the relationship. So, the first few PCs capture most of the directions along which data is spread (in other words, captures most of the overall variance in the data). Then, we can only consider the first few principal components and project the data along these principal components. This way, we can reduce the high-dimensional data to a low-dimensional data.

###### Mathematical Interpretation of Principal Components

In terms of mathematics, the principal components are orthogonal set (they’re perpendicular to each other) of the direction vectors. Each PC represents the direction of a line that fits best to the data in terms of minimizing average squared distance of data points from this line, being orthogonal to other PCs. The PCs constitute an orthonormal basis of the data points. The original data can be projected along this new orthogonal set of basis. However, since data is mostly spread along only few PCs, we can use a subset of PCs and project the data onto a lower dimensional space. It can be shown the principal components are eigenvectors of the covariance matrix of the data.

Let’s understand the concept further with an example given in [Figure 2.34](#02_003.html#f2.34).

[![Example of Principal Component Analysis](bilderklein/klein02_034.png)](img-f2.34.html) 

**Figure 2.34**    Example of Principal Component Analysis

The diagram in [Figure 2.34](#02_003.html#f2.34) 1 shows scatterplot of data in a 3-dimensional space, represented by three attributes X, Y and Z. [Figure 2.34](#02_003.html#f2.34) 2 shows the directions of the principal components in red color for this data. [Figure 2.34](#02_003.html#f2.34) 3 shows the definition of principal components, expressed in terms of original coordinate system with X, Y and Z. For example, the first principal component is showing the direction of the point (-0.7103774, 0.6835728, -0.1676072) from the origin. Also, note the variance of the individual principal components and the proportion of variance explained (PVE) in [Figure 2.34](#02_003.html#f2.34) 4. The first PC captures around 66% and second PC captures around 34% of overall variance. The third PC has very negligible variance. Eventually the first two PC captures almost entire variance of the data, as evident in the cumulative PVE. It tells us that the data is spread predominantly in two directions represented by the first two PCs, so we can ignore the third PC and run our analysis by projecting data onto the first two PCs. This way, a 3-dimensional data is reduced to a 2-dimensional data.

###### Note

*   The PCA is applicable for continuous attributes. For categorical variable, there are other techniques like categorical PCA.
    
*   It is recommended to centre and scale the attributes so that the mean of each attribute is zero and variance is 1.
    

#### Association Analysis

Association analysis is an unsupervised machine learning technique that discovers interesting relationships between items hidden in a large dataset of transactions. One interesting use case of association analysis is market basket analysis. Let’s understand it with a simple example. A departmental store sells different food items and they have a huge database of transactions that captures what all items are being sold together in different transactions. [Table 2.7](#02_003.html#t2.7) represents a sample set of transactions. The departmental store is interested to know what all items are sold together so that they can put those items together in the shop to increase cross-sale.

 
| Transaction ID || Items in the Transaction |
| --- | --- |
| T001 || Bread, Butter |
| --- | --- |
| T002 || Milk, Bread, Butter |
| T003 || Butter, Beer, Bread |
| T004 || Bread, Milk, Eggs |
| T005 || Bread, Milk, Eggs, Butter, Beer |

**Table 2.7**    Sample Transactions from Food Section of a Departmental Store

If we investigate these sample transactions, it reveals some hidden relationships in the data. The transactions that contain the item bread, most of them also contain the item butter. This suggests possibly the customers who buy bread tend to buy butter also. So, if the departmental store keeps these two items in adjacent shelves, it may increase the sale of butter. These types of relationships are known as association rules or sets of frequent items. The above rule can be displayed as {Bread } => { Butter }.

We discovered the rule based on visual inspection of sample data. However, it becomes a very computationally intensive problem to identify such relationships where transaction runs into millions with thousands of different items. Association analysis provides efficient algorithms to identify such relationships efficiently. Association analysis is used in many other fields as well, like web mining, medical diagnosis, bioinformatics.

Now, let’s define the concept mathematically using the set theory. Suppose the market basket data contains m different items, say i[1], i[2], i[3], …, i[m] and n transactions, say t[1], t[2], t[3], …, t[n]. Let I = {i[1], i[2], i[3], …, i[m]} is the set of all items and T = { t[1], t[2], t[3], …, t[n] } is the set of all transactions in the market basket data. A collection of zero or more items is termed as itemset. For example, the set of items {Bread, Milk, Eggs} is an itemset. A transaction can be also considered as a set of items. In [Table 2.7](#02_003.html#t2.7), the transaction T001 represents the set {Bread, Butter} of items.

An association rule is an implication expression of the form X => Y, where both X and Y are disjoint itemsets. Expressed mathematically, X, Y ⸦ I and X ∩ Y = Ø. We may interpret it as itemset X implies itemset Y. The itemset X is called the antecedent and Y is called consequent. 

Now for any itemset, say X, the support count of X, denoted by σ(X) is the number of transactions that contain the itemset X. Mathematically, it can be written as

σ(X) = | { t | X ⸦ t, t ∊ T} |

For an association rule X => Y, the following two measures play important role in Association Analysis.

##### Support

Support of the rule X => Y measures the fraction of total transactions display this rule. Mathematically, it is expressed as: s(X => Y) = σ(X ∪ Y) / n, where n is the total number of transactions.

Support shows how frequently a rule appears in the transactions. A rule with small support may indicate it happened just by chance. For the items in [Table 2.7](#02_003.html#t2.7), if we consider X = {Eggs} and Y = {Beer}, then support of X => Y is 1/5. Or, 0.2. Whereas, if we consider X = {Bread} and Y = {Butter}, then s(X => Y) = 4/5 = 0.8. Note that s(X => Y) = s(Y => X).

Support can be defined for an itemset also. Support of an itemset X, denoted by s(X) is the fraction of total transactions containing the itemset X.

In other words, s(X) = σ(X) / n, where n is the total number of transactions. With [Table 2.7](#02_003.html#t2.7) data, support of the itemset {Milk, Eggs} is 2/5 =0.4.

##### Confidence

Confidence of X => Y measures fraction of times Y appeared in a transaction that contains X. Mathematically it is expressed as,

c(X => Y) = σ(X ∪ Y)/ σ(X)

Confidence shows the reliability of a rule, the higher the confidence, the stronger the rule. Actually, it is an estimate of the conditional probability of the event that Y is in a transaction given that X is in the transaction. Based on data in [Table 2.7](#02_003.html#t2.7), if X = {Bread} and Y = {Milk}, then c(X => Y) = 3/5 = 0.6. Note that c(Y => X) = 3/3 = 1. So, confidence may change depending on the antecedent itemset.

With introduction to these terms, lets now briefly discuss how the association rules are discovered. A large dataset contains exponentially many possible association rules. More precisely, if the dataset contains m items, then total number of possible rules is 3^m – 2^(m+1) + 1. With 100 items, the number of possible rules becomes 5.15378E+47. So, the process of discovering rules by scanning all possible rules become exorbitantly expensive and cannot be a feasible approach. However, not all these rules are interesting, most of them may have appeared just by chance and may not be reliable. So, the algorithms extract the rules which have support and confidence values above some threshold points. This strategy then involves discovering rules through two major steps:

1.  Frequent Itemset Generation  
    Identifying all itemsets that have support higher than a predefined threshold. These items are called frequent itemsets.
    
2.  Rule Generation  
    Discovering rules within the frequent itemsets that have confidence higher than a predefined threshold. If A is a frequent itemset, it amounts to split A into two non-overlapping itemsets B and C such that A = B ∪ C and c(B => C) > threshold value of confidence. Note that s(B => C) = σ (B ∪ C) /n = σ (A)/n = s(A) > threshold value of support. These rules are known as strong rules.
    

This is a common strategy of many algorithms of Association Analysis; however, different algorithms implement this strategy using different techniques:

*   The Apriori algorithm implements it using the Apriori principle. This principle says if an itemset is frequent, then all its subsets are also frequent. For example, the itemset {Bread, Milk} has support 0.6. Now, if we take 0.5 (50%) as the threshold value for support; then {Bread, Milk} is a frequent itemset. Now since this combination appears in more than 50% of transactions, individual subsets of this itemset. In other words, {Bread} and {Milk} must also have appeared in more than 50% of the transactions. In other words, both the itemsets {Bread} and {Milk} are also frequent. So, while searching for frequent itemsets, if an itemset appears to be infrequent, then all its supersets are also infrequent and can be safely excluded from search space.
    
*   The FP-Growth algorithm takes a completely different approach to find frequent itemsets. It encodes the dataset using a data structure called FP-tree, which is gradually built while reading the transactions. FP-Growth algorithm extracts the frequent itemsets directly from this FP-tree.
    

#### Deep Learning

Deep learning is a part of machine learning methods based on artificial neural networks with feature learning. The term deep refers to many hidden layers in a large neural network. Deep learning usually deals with huge amount of data and requires massive computational power.

In recent years, we have witnessed an explosion of unstructured data like images, videos, audios, customer feedbacks, comments and they contain valuable information. Deep learning methods can be successfully applied to extract useful information from these unstructured data. It has extensive application in different fields like computer vision, speech recognition, natural language processing, social network filtering, machine translation.

There are different types of artificial neural network, like deep neural network (DNN), deep belief network (DBN), convolutional neural network (CNN), recurrent neural network (RNN) which are used for deep learning purpose. We have already discussed about Multilayer Artificial Neural Network in the previous section on artificial neural network. [Figure 2.35](#02_003.html#f2.35) shows an example of deep neural network with multiple hidden layers. In this section we will introduce two different types of neural network, convolutional neural network and recurrent neural network to give the basis understanding without going deep into the learning algorithms.

[![Network Architecture of a Deep Neural Network](bilderklein/klein02_035.png)](img-f2.35.html) 

**Figure 2.35**    Network Architecture of a Deep Neural Network

##### Recurrent Neural Network (RNN)

So far, we have seen neural networks which pass on the information from one layer to the next layer. This type of neural network is called feed forward network. However, it has few limitations:

*   Feed forward network does not have a mechanism to feedback the output of an intermediate layer to a previous layer to refine the final output.
    
*   A feed forward network has a fixed set of input nodes and fixed set of output nodes. The number of nodes in the input and output layers may vary for different problems, but if we want to have variable number of input and output nodes in solving the same problem, it will not be possible in a feed forward network.
    

A recurrent neural network (RNN) overcomes these limitations of feed forward network. A basic RNN has a feedback path to itself along a temporal (time-based) sequence, so that the output of an internal layer (internal state or memory) can provide feedback to itself for next input. This feedback path makes recurrent neural network a sequential network, where input comes in a sequence and the internal state of the previous input can be feed back to the network itself for next input. The output can also be provided in a sequence, but not necessarily in the similar sequence of input. This way, it also overcomes the limitation of fixed number of input or output nodes.

As an example, let’s consider translation of a sentence to a different language. Here input is a sentence and the output is also a sentence, but in a different language. An input sentence can have multiple words, so the length of input is not fixed. The output can also vary in length. Besides, a sentence is a not a random collection of words, rather it has a meaning, so the words in a sentence are connected in a meaningful way. We need to capture this relationship as well. An RNN can be used in this scenario, where each word in a sentence is read in a sequence, the internal state of network for one word is feed back to the same network for next word. Finally, the output sentence is produced, but it is not a word by word translation, so the output may not be produced for each input. [Figure 2.36](#02_003.html#f2.36) shows a schematic diagram of RNN for this example.

###### Note

A neural network compactly can be represented by three boxes, the first box shows the input vector, second box represents the intermediate nodes and the third box denotes the output vector. These boxes are connected via directed links showing the flow of information. This representation has been used in [Figure 2.36](#02_003.html#f2.36).

[![Example of a Recurrent Neural Network for Language Translation](bilderklein/klein02_036.png)](img-f2.36.html) 

**Figure 2.36**    Example of a Recurrent Neural Network for Language Translation

In [Figure 2.37](#02_003.html#f2.37), the English sentence “I am doing fine” is translated to the Bengali language. Individual words of the sentence are processed sequentially, the same network sends feedback to itself for the next input. It does not provide any output initially, once the input sequence is read the network start producing the output. Multiple boxes of Network refer to the same RNN network, processed with different input words. This example shows that number of input sequences need not be in 1:1 with number of output sequences. In fact, it is in n : m relationship.

[![Example of RNN in 1: n and n: 1 Relationship Scenarios](bilderklein/klein02_037.png)](img-f2.37.html) 

**Figure 2.37**    Example of RNN in 1: n and n: 1 Relationship Scenarios

There could be scenarios where one input leads to a sequence of output, e.g. tagging different persons in a picture based on face recognition. This is a scenario of 1: n relationship where the value of n is not known beforehand. Similarly, there could be n : 1 scenarios where a sequence of input leads to a single output, e.g. classifying into positive or negative sentiment based on a sequence of words of a user comment. RNN can be used in these types of problems.

There are various other types of RNN, based on factors like network topology, activation function, connectivity across nodes, weights. Some of these types are hopfield network, echo state network, independently RNN, long short-term memory, and bidirectional RNN.

##### Convolutional Neural Network (CNN)

Convolutional neural network (CNN) is widely used for computer vision. The patterns in the images are discovered hierarchically in a CNN, from simple patterns to more complex patterns. The term ’Convolutional’ came from a mathematical term called convolution, which is a special type of linear operator. CNN uses convolution in at least one of its layers.

CNN is mainly used for image classification. An image can be considered as a vector of pixels. Each pixel contains a specific color, it may be represented by a value in grayscale showing the intensity of light for black and white picture or in RGB scale (based on intensity of red, green and blue colors) for colored pictures. For simplicity, we may consider each image as a vector with the color values of the pixels.

Convolutional neural network identifies the patterns and classifies the images, but it does not uses the pixel values as is, rather it utilizes two operations on data, may be multiple times, called image convolution and pooling to identify features in the picture and reduce dimensionality of the original data. The underlying concept is inspired by animal visual cortex.

##### Image Convolution

Image convolution is the process of filtering the image to extract useful features from it. It runs a convolution operation between square blocks of pixels in the image with a square filter matrix to extract useful features from the data. [Figure 2.38](#02_003.html#f2.38) shows an example of image convolution. Here we have a 4 x 4 image and a 3 x 3 filter matrix.

The image convolution here takes the pixel values one by one from a 3 x 3 block of the image, multiplies it with the values in the corresponding positions of the filter matrix and they are added together. For each 3 x3 blocks in the image, this operation is performed, and the output is stored in a 2 x2 image. There are 4 such 3 x 3 blocks in a 4 x 4 image, the blocks at top left, top right, bottom left, bottom right. Each of these blocks go through same operation and the outcome is written into the corresponding pixel position of the outcome image.

Image convolution looks at a block of the image and picks up a distinctive feature in that block. Depending on the filter matrix used, it can pick-up low-level features like feature, color as well as high level features.

[![Example of Image Convolution](bilderklein/klein02_038.png)](img-f2.38.html) 

**Figure 2.38**    Example of Image Convolution

##### Pooling

Pooling is another filter that reduces the size of an image. It picks up a block of the image and maps the pixel values in that block to a single value, it could be the maximum of the pixel values (Max Pooling) or average of the pixel values (average pooling). [Figure 2.39](#02_003.html#f2.39) shows example of 2 x 2 pooling of an image using max pooling.

[![Image Pooling (Max Pooling)](bilderklein/klein02_039.png)](img-f2.39.html) 

**Figure 2.39**    Image Pooling (Max Pooling)

Convolution neural network usually uses multiple sequences of image convolution and pooling to extract the more and more features of the image while keeping the size of the resulting image low. Finally, the image is flattened into a vector of pixels and fed into a neural network for classification.

#### Natural Language Processing

Natural language processing (NLP) is another strongly emerging area in artificial intelligence and machine learning that aims to understand, decipher and communicate in human language. It involves many other fields like linguistics, statistical inference, information engineering.

NLP has wide application where machine needs to interact with human using natural language. Some of these include speech recognition, personal assistance applications such as Alexa, OK Google; chatbot applications, language translation like Google translate, grammar checking, sentiment analysis, recommender systems.

When we speak in natural language it carries huge amount of information. Individual words, their structure and relative position, the tone, the topic all have some meaning associated with it. However, most importantly, it is not just a stream of data, it carries an overall meaning also. Also, the pause or punctuation marks carry important information about the overall meaning. For example, consider the following two sentences in colloquial language:

“Leave it, not break it” and “Leave it not, break it”.

Here just a change in position of the punctuation mark completely changes the meaning of the sentence.

Another important aspect in natural language processing is that the data is necessarily unstructured data. There is no specific structure we can impose on written texts or verbal communications to fit it in traditional table structure with fixed number of rows and columns. Also, variation among the different texts, documents, speeches can be enormous. So, analysing such enormous unstructured data and extracting useful information and understanding meaning is not an easy task. However, with advanced machine learning algorithms, it is becoming more and more an achievable target.

Understanding natural language is a very complex task for machine. Hence different machine learning algorithms have been derived for different areas of natural language processing, including:

*   Bag of words  
    This is used to count occurrence of each word in a piece of text, ignoring the grammar and order of the words. This frequency distribution is then used to train classification models to classify different texts.
    
*   T erm frequency  
    Inverse document frequency (TFIDF): In bag of words, the words like “a”, “the” have very high frequency and it impacts the analysis. In TFDIF, the frequencies are weighted in such a way that words that occur in high frequency in all the texts are rescaled to reduce their influence in the analysis.
    
*   Tokenization  
    Tokenization is the process to split a text into smaller parts called tokens. Tokens can be words, characters and sub-words. The idea behind tokenization is to create a vocabulary and use it in the analysis. Some of the Deep Neural Network models uses tokens to process raw text data.
    
*   Stemming  
    This is used to slice the words in the beginning or in the end to remove prefixes and suffixes.
    
*   Topic modeling  
    This is used to discover hidden patterns in a set of texts and documents. According to this approach, each document consists of multiple topics and each topic consists of multiple words. This method clusters the texts to discover the hidden topics based on the content.
    

With advancement of deep leaning methods, they are now widely used in many areas in NLP, like language transformation, speech recognition. This is a vast subject and is not possible to cover within the scope of this book. However, we wanted to give a glimpse of it as this is an active area of research in machine learning and artificial intelligence.

## 2.4    Summary

In machine learning, the system analyzes input data to learn underlying patterns, hidden relationships within the data and uses this information for prediction or inference in specific use cases. Machine learning has become an important part of our daily experience. It has application in all spheres of life, starting from classical use cases like sales forecast, fraud detection, customer segmentation to the most modern use cases like computer vision, speech recognition, automated language translation.

Machine learning uses various algorithms of artificial intelligence and statistical inference to learn from the data. It operates on a probabilistic paradigm; the input data usually is a representative sample from the possible scenarios and does not contain the complete information. Probability plays a key role as the mathematical foundation of machine learning algorithms.

Based on learning techniques, machine learning algorithms are categorized as supervised, non-supervised, semi-supervised and reinforced learning. supervised learning includes two main types of analysis, regression analysis, that predicts value of a continuous response variable and classification, that predicts value of a categorical response variable (classifies observations into different categories). Additionally, non-supervised learning includes techniques like clustering, association analysis, and PCA. There are many algorithms available for each of these areas and there is no notion of uniformly better algorithm in machine learning. Depending on the scenario, nature of data, nature of relationship appropriate algorithm is chosen. It is important to understand the underlying assumptions, advantages and disadvantages of each algorithm to apply them successfully in real life problems.

# 3    Implementation Lifecycle

This chapter explains the key components of the development lifecycle of a machine learning application. Like any other project, a machine learning project also goes through various phases, each with required activities and tasks, that ideally are systematically executed and orchestrated. Different methodologies have been developed to provide structured approaches for executing machine learning projects, and this chapter briefly discusses some of these methodologies. In this chapter, we’ll discuss in detail some key activities common across all these methodologies and explain associated machine learning concepts.

As IT professionals, we’re all familiar with software development lifecycles using different methodologies like the waterfall model, Agile software development, and DevOps. These methodologies follow specific work breakdown structures (WBSs), methods, processes, techniques, and best practices and provide a structured approach to executing IT projects efficiently. Before the start of a project, we usually select a suitable methodology (or a tailored version of a methodology) based on various factors like the objective, nature, scale, and complexity of the project. Machine learning application development can also be considered under the broad spectrum of IT projects but involves special roles like data scientists and machine learning experts. these methodologies may be used for machine learning projects.

However, one fundamental difference exists between machine learning projects and other IT projects. In most IT projects, the outcome is deterministic in nature. In other words, given an input, we clearly know the desired output based on the business logic. However, in machine learning projects, the outcome is probabilistic in nature: Given an input, we don’t know the exact output; we only know the most likely output. Thus, conventional methodologies for IT projects don’t work perfectly in machine learning projects; they require special methods, techniques, and processes to handle the probabilistic nature of the outcome.

In this chapter, we’ll start by briefly touching upon three methodologies to understand their use in the implementation lifecycle in [Section 3.1](#03_001.html#h3.1). We’ll also focus on the key components common across all the methodologies to enhance our understanding of the underlying concepts from a machine learning perspective. Then, after a quick look at the business in [Section 3.2](#03_002.html#h3.2), we’ll start looking at the key component of any data science project—the data! In [Section 3.3](#03_003.html#h3.3) and [Section 3.4](#03_004.html#h3.4), we’ll dive deeply into the data, including how to assess and prepare your data for your machine learning models. Finally, in [Section 3.5](#03_005.html#h3.5), [Section 3.6](#03_006.html#h3.6), and [Section 3.7](#03_007.html#h3.7), we’ll walk you through building, testing, and deploying a machine learning model in detail.

## 3.1    Understanding the Implementation Lifecycle

The first step, and a key aspect of implementing a machine learning project, is to understand the project lifecycle. In this section, we’ll describe the different stages a typical project goes through, from initiation to completion. As you’ll see in this chapter, the project lifecycle will be different depending on which methodology you follow, and you’ll learn how key phases in a project lifecycle may differ across these methodologies.

### 3.1.1    Cross Industry Standard Process for Data Mining

CRISP-DM, which stands for Cross Industry Standard Process for Data Mining, is a robust and proven methodology for data-centric projects and can be applied efficiently for machine learning projects.

[Figure 3.1](#03_001.html#f3.1) shows the six phases of the CRISP-DM methodology. Each phase comprises of several generic task. Many tasks will differ depending on the situation, and each specific task will involve processes—the actions, decisions, and results from the actual execution of the task.

[![CRISP-DM Methodology with Key Activities](bilderklein/klein03_001.png)](img-f3.1.html) 

**Figure 3.1**    CRISP-DM Methodology with Key Activities

###### Note

The CRISP-DM methodology is iterative and cyclical in nature. In some scenarios, the result of a task in a later phase may lead to a task in a previous phase, and this back and forth may continue until the desired result is achieved.

CRISP-DM was developed in 1996 and has been one of the most popular methodologies among data scientists.

### 3.1.2    Define, Measure, Analyze, Improve, Control

DMAIC, which stands for Define, Measure, Analyze, Improve, Control, is an iterative process widely used for improving, optimizing, and stabilizing existing data-driven business processes.

CRISP-DM focuses more on business understanding, data preparation, and modeling, with less emphasis on the operationalization of the model in the business environment from a performance monitoring and controlling perspective. DMAIC attempts to addresses these gaps. However, as a result, DMAIC puts less emphasis on modeling, which is a critical activity in complex machine learning projects.

SAP has adopted the DMAIC methodology for its machine learning project framework. [Figure 3.2](#03_001.html#f3.2) shows the phases and main tasks of this framework.

[![Phases and Main Tasks of a DMAIC-Based SAP Machine Learning Project Framework](bilderklein/klein03_002.png)](img-f3.2.html) 

**Figure 3.2**    Phases and Main Tasks of a DMAIC-Based SAP Machine Learning Project Framework

### 3.1.3    Analytics Solutions Unified Method for Data Mining/Predictive Analytics

ASUM-DM, which stands for Analytics Solutions Unified Method for Data Mining/Predictive Analytics, is an extended and refined version of CRISP-DM developed by IBM in 2015. The philosophy behind this extension is the belief that a machine learning application (or any analytics solution) only provides value to the client when properly embedded into the business processes of the organization. Thus, for a machine learning project to be successful, the deployment of the application is as important as its development. ASUM-DM takes care of deployment through two complementary cycles: the development cycle and the deployment cycle. The development cycle is mainly based on CRISP-DM, with some refined activities, templates, and guidelines. However, the deployment part has been enhanced into a full-blown cycle with different phases and activities to enable the deployment of analytics applications in a manageable, repeatable, traceable, and secure manner. [Figure 3.3](#03_001.html#f3.3) shows the phases of the ASUM-DM methodology.

[![Development and Deployment Cycles and Phases of the ASUM-DM Methodology](bilderklein/klein03_003.png)](img-f3.3.html) 

**Figure 3.3**    Development and Deployment Cycles and Phases of the ASUM-DM Methodology

### 3.1.4    Key Components in a Machine Learning Project Lifecycle

As illustrated in this brief discussion of the three main methodologies, two major parts exist in a machine learning project: the development part and the deployment/operationalization part. Also, each methodology organizes its phases and tasks differently, with different levels of emphasis, but some common components are utilized in all these methodologies, such as the following:

*   Understanding the business in the context of machine learning use cases
    
*   Understanding the associated data
    
*   Preparing input data for machine learning models
    
*   Developing machine learning models
    
*   Evaluating and fine-tuning the models to arrive at the final model
    
*   Deploying machine learning solutions in productive environments
    

[Figure 3.4](#03_001.html#f3.4) shows the phases of each methodology, highlighting these key components.

[![Key Components of Machine Learning Methodologies](bilderklein/klein03_004.png)](img-f3.4.html) 

**Figure 3.4**    Key Components of Machine Learning Methodologies

In later sections, we’ll discusses these key components in more detail from a machine learning technique perspective.

## 3.2    Knowing the Business

Machine learning projects aim to solve specific business challenges by discovering patterns within the data and providing predictions and specific insights. For example, consider a supermarket, which sells products from different manufacturers. If the supermarket stocks products in huge amounts for a period but cannot sell them in that period, inventory carrying costs will increase. At the same time, maintaining low stocks of products may lead to stock-out situations and the loss of sales opportunities. So, while planning for stock replenishment, the supermarket faces the challenge of optimizing stock levels in such a way that minimizes inventory carrying costs without losing prospective sales opportunities. This scenario is an inventory planning scenario. Similarly, in the service sector, for instance, for a mobile network service provider, the challenge might be reducing voluntary subscriber churn through a proactive retention program. Offering incentives to all customers to retain them will cost a great deal. However, by making the offer to only a few customers, other customers may churn. Thus, the company must identify exactly the customers who are most susceptible to churn and target them only. This problem is a problem of churn prediction.

Machine learning can efficiently solve these business challenges. However, you must understand the business before applying any machine learning solution. In the inventory planning scenario, just analyzing the demand data and inventory carrying costs is not enough; other aspects of the underlying business processes must be considered, such as the procurement cycle of finished goods, capacity, the shelf life of finished goods, substitutions between competing products, and transportation times from storage locations to retail locations. Similarly, for the churn prediction problem, you’ll need to understand key business aspects like the various prepaid and postpaid plans offered, value-added services, billing cycles, grace periods, how calls are charged, how call-drops can be identified, how complaints are raised and resolved, and customer demographic patterns. Forgetting these underlying business concepts and focusing only on the data may lead to a machine learning model that fails to capture the true nature of the business problem. Thus, a proper understanding of the business is a key success factor.

The first activity for a machine learning consultant is to understand the associated business, which will help achieve the following objectives as well:

*   Understanding the project’s objective from a business perspective and mapping the objective to a machine learning problem.
    
*   Understanding the influential parameters associated with the business problem.
    
*   Understanding and defining the success criteria for the project, for instance, how the final results will be provided, how accuracy will be measured, and how much accuracy is considered a success. A measure of accuracy may be defined in various ways, and a good understanding of the business helps you to define it properly. In [Section 3.6](#03_006.html#h3.6), we’ll discusses different measures of accuracy.
    
*   Assessing the risks associated with the project.
    
*   Preparing a plan to address the business problem through machine learning.
    

## 3.3    Understanding and Exploring Data

Data lies at the heart of any machine learning project. As the key input for machine learning algorithms, a thorough understanding of data is extremely critical for the success of the project. Poor data will lead to the incorrect results and will defeat the purpose of the project.

According to the Oxford Dictionary, data means the “facts and statistics collected together for reference or analysis.” In a broad sense, anything that provides some information for reference or analysis can be considered data. This definition opens up a lot of possibilities for considering something as data, from a table in a relational database to streaming data, audio files, documents, images, and videos so long as these things carry some information to be analyzed or referenced. In fact, when building an intelligent enterprise, you cannot ignore these various sources of data. Broadly, we can categorize this data into three areas:

*   Structured data  
    Data organized according to a predefined structure. A table in a relational database is a good example of structured data. Data is organized into some fixed number of fields or columns, and each field has a specific format like string, integer, floating point number, or date.
    
*   Unstructured data  
    Data that does not follow any predefined structure and can assume any form. Documents, audio files, images, and streaming data are examples of unstructured data.
    
*   Semi-structured data  
    Semi-structured data has some structure associated with it, but it is not a very rigid structure like tables in relational database, it has a flexible structure through tags or other markers that separate semantic elements and put a hierarchical structure of records and fields within the data. XML, JSON, and emails are examples of semi-structured data.
    

In machine learning, algorithms typically expect data in a specified format, that is, as structured data. So, unstructured data is generally converted into structured data before used in an algorithm. Sometimes, the machine learning tool or service can extract the relevant information (features) from unstructured data, putting this data into a structure, and then specific machine learning algorithms are used on this structured data. For instance, a digital image may be converted into a vector using position of the pixels and values associated with the color of those pixels. Extracting features from unstructured data is a vast topic, and an active area of research beyond the scope of this book. Thus, we’ll limit our discussion to structured data in this chapter.

Structured data usually contains multiple columns or fields, and these fields may be further divided into many types, for instance, its format, whether the field is a primary key, and other aspects, but for our purposes, we’ll consider types based on the information content. Before defining different types of information content for the fields, let’s consider two associated terms:

*   Attributes  
    An attribute is a property or characteristics of an object that may vary either from object to object or from time to time. For example, ethnicity varies from person to person, whereas the temperature of a machine varies with time.
    
    Primarily, attributes represent properties or characteristics of an object but are not symbols or numbers. However, to interpret or analyze attributes, we’ll assign symbols or numbers to it. We’ll use a measurement scale to create this assignment in a meaningful and well-defined way. In machine learning literature, attributes are also sometimes called variables. We’ll use these terms interchangeably.
    
*   Measurement scales  
    A measurement scale is a rule that associates a numerical or symbolic value with an attribute of an object.
    

Knowingly or unknowingly, we’re always using symbols and numbers to quantify or qualify features of objects in our day to day life. When we say “male” or “female,” we’re actually using symbols to map two different variations of the attribute “Gender.” When we talk about the attribute “Distance,” we’re assigning a number to it according to some measurement scale. Even the letters we use in writing are nothing but phonetic symbols representing sounds.

Structured data, for instance, a table, actually uses symbols or numbers to represent the values of different attributes of an object. For example, in customer data, different columns represent different attributes of a customer, say “Gender,” “Age,” or “Billing Amount,” and the symbols or numbers in the columns represent different values/variations of that attribute according to some measuring scale. A particular row represents the values (in the form of symbols or numbers) of different attributes for a specific customer.

Depending on the nature of measuring scale, four different types of attributes can be used, which are listed in [Table 3.1](#03_003.html#t3.1). This classification is as per the psychologist Stanley Smith Stevens; other classification methods also exist in the literature.

 
| Attribute Type || Description || Example || Admissible Mathematical Operators |
| --- | --- | --- | --- |
| Nominal || The values of a nominal attribute represent the names of different categories or membership to classes. They only provide information to distinguish one object from another. || Gender, Country || \= , ≠ |
| --- | --- | --- | --- |
| Ordinal || The values of an ordinal attribute represent different categories, like a nominal attribute, but also provides information to order these values. || Examination Grades, Income Categories || \= , ≠ , <, > |
| Interval || The values of an interval attribute represent numbers where the difference between the numbers is meaningful, but their ratios are not meaningful. || Calendar Dates || \= , ≠ , <, >, + , – |
| Ratio || The values of a ratio attribute represent numbers where both the differences and ratios between numbers are meaningful. || Sales Quantity, Age, Height || \= , ≠ , <, >, + , –, \*, / |

**Table 3.1**    Different Types of Attributes

The values of nominal and ordinal attributes represent symbols of different categories or classes. For an ordinal attribute, values also represent an ordering among the categories. These two types of attributes are also called categorical attributes or discrete attributes, and they are qualitative (or discrete) in nature. The interval and ratio attributes are quantitative (or continuous) in nature, and they take numerical values over a range. Thus, these attributes are also called continuous attributes. The ratio between the two numbers is not meaningful for interval attributes, but is meaningful for ratio attributes.

Since these different types of attributes (also called variables) show different types of information and their associated mathematical operators are also different, you’ll need to treat each attribute type separately when trying understanding your data.

### 3.3.1    Checking Data Quality

Data quality is important for any kind of data analysis. If the quality of your data is poor, the conclusions drawn from this data will be erroneous. Several types of data quality issues are commonly encountered in a machine learning projects, which we’ll describe in this section.

#### Inaccurate Data

Inaccurate data may arise due to human error, problems with measuring devices, or flaws in the data collection process.

During data entry, errors may occur when users assign objects to the wrong categories, misspell categories, omit numbers or enter the wrong numbers, or enter inconsistent values to represent the same category (e.g., “Masters,” “Master,” “Masters Degree,” and “masters degree” all represent the same category of educational qualification). A faulty measuring device may generate the wrong data, like a faulty blood pressure monitor collecting data for a medical survey. Process-related issues may arise if the data is not collected properly. For instance, in an exit poll analysis, if the sample survey is conducted in only a few areas, the data may not accurately represent the true opinion of the people from the entire constituency.

Some software applications can detect certain issues with the values of categorical attributes, suggesting possible corrections and standardizing the data. However, issues with measuring devices or collection processes are often hard to detect, unless a systematic pattern of the error is apparent. For example, if the values of the incomes of different persons often end up with “000” or “500,” you may suspect that the data has been rounded to the nearest multiple of 500. Sometimes just looking at the data may reveal this type of systematic error.

#### Presence of Outliers

An outlier is a data point that lies far away from the other data points in the set. This anomaly may arise from an unusually large or small value for an attribute or from a combination of attribute values that set this data point far away from the other data points. Thus, an outlier could be a legitimate data point, or it could be the result of one or more erroneous values.

Some machine learning algorithms are highly sensitive to outliers. In [Chapter 2](#02_001.html#h2), [Section 2.3.1](#02_003.html#h2.3.1), you saw the impact of outliers in a linear regression and learned how they can be identified. However, other algorithms are not so sensitive to outliers, like Support Vector Machines (SVMs). Depending on the algorithms used, outliers will need to be handled accordingly. Usually, the data points of outliers can be eliminated if the intended algorithm is overly impacted by the outliers.

#### Incomplete Data with Missing Values

Missing values are a common problem in data. Often, a few values of one or more attributes may be missing because these values were not captured. In data quality terminology, this problem is called incomplete data. This issue may arise due to many reasons, like a respondent’s unwillingness to provide the information (e.g., age of a customer) and the lack of incentive to provide complete data. Several strategies are available for dealing with missing values, such as the following:

*   Eliminate the attributes  
    If an attribute contains too many missing values, then the information content of that attribute is minimal and can usually be discarded.
    
*   Delete the rows  
    If the data contains only a few missing values, then the rows containing the missing values can often be discarded. However, you may lose valuable information if the total number of records is small.
    
*   Compute missing values  
    Sometimes, missing values of an attribute can be reliably estimated based on the remaining known values of the attribute or based on the values of other attributes. Various ways of computing missing values are available, such as the following:
    
    *   For a continuous variable, the mean of the remaining values can used as an estimate of the missing values. Some functions of the remaining values may also be considered as estimates.
        
    *   For a nominal variable, the category with the highest frequency (mode) can be used as an estimate of missing category, or the missing category can considered as a new category, perhaps, “Not Available.”
        
    *   For an ordinal variable, the middle value of the categories (the median) can be used as an estimate.
        
    *   In a dataset, many similar observations, i.e., data points, may exist. Thus, missing values can be estimated based on the values of the attribute of similar observations. Algorithms like the k-nearest neighbors (k-NN), approximate nearest neighbor, and decision tree algorithms are effective for identifying similar observations.
        
    *   Other techniques, like stochastic regression imputation, hot-deck imputation, and multiple imputations, can be used estimate missing values.
        

If your data is missing values, some machine learning algorithms will fail to execute. However, other algorithms, like k-NN, can accept missing values and will ignore this problem during runtime. [Figure 3.5](#03_003.html#f3.5) shows some sample data with missing values and some strategies for handling missing values in the data.

[![Sample Data with Missing Values and a Few Strategies to Handle These Issues](bilderklein/klein03_005.png)](img-f3.5.html) 

**Figure 3.5**    Sample Data with Missing Values and a Few Strategies to Handle These Issues

#### Lack of Consistency in Data Values

Data may contain inconsistent values. For example, an end date for an event might be earlier than the event’s start date. Data inconsistency may arise in a single attribute (e.g., a negative value for the height of a person) or in the context of combination of multiple attributes (e.g., customer address contains an impossible combination of city and zip code, although the individual values are correct).

Data inconsistency may be checked against predefined rules. For instance, height should always be greater than zero, and valid city and zip code combinations should be available in a lookup table. Inconsistent values must be corrected before using the data for further analysis.

#### Lack of Relevancy in the Data

Relevancy is a data quality measure that checks the extent to which the data is relevant, that is, useful for the intended purpose. From a machine learning perspective, if some portion of the data is not relevant for solving the business problem, then you may need to drop that part of the data.

For example, for a churn prediction, data on the number of incoming calls may not have relevant information if incoming calls are free. However, the network service provider from which maximum calls are made may have relevant information, as this information may indicate poor connection quality across different networks. Understanding the underlying business plays a crucial role in identifying the relevant data.

#### Lack of Timeliness

Timeliness measures how far in time the data points can be said represent the most current information resulting from the output of a business event. If the data suffers from a lack of timeliness, then your data does not reflect the current pattern in the business and may not be suitable for prediction purposes.

For example, for a churn prediction, the billing amount 24 months ago may not have any impact on the decision of a customer to churn today, and the billing of last 3–4 months may only have influence if the customer finds or suspects an unusual high billing amount. Thus, you may not need to consider data points from the distant past unless not much has changed recently in the business.

#### Duplicate Data

A dataset may have observations that are exactly the same or similar to one another. These observations may be legitimate data points for two different objects or may represent the same object but with differences in some attributes.

For example, the records of two different customers may be identical by chance. Also, two records may be created in the churn analysis scenario for the same customer if the customer has churned out but then joined back within a short period.

Some machine learning algorithms cannot handle duplicate records, and duplicates might make the underlying numerical procedures unstable. For example, if an algorithm uses matrix inversion, then duplicate records will make the matrix singular and not invertible. Thus, you may need to resolve duplicate values.

Deciding how to deduplicate your data may vary across scenarios. Care must be taken to not eliminate data of two different objects by mistakenly considering them as duplicates of each other. Also, if nearly duplicate records actually pertain to same object, then some of their attributes may still have different values, and these differences will need to be resolved carefully.

Note that, with some machine learning techniques like Bootstrap, observations are resampled from data with replacements, and duplicate records are generated. However, in these techniques, this data duplication is done for a specific purpose.

### 3.3.2    Checking Summary Statistics

When you use a dataset for machine learning, you’re only using a representative sample from the entire population. For example, for a churn prediction, even if you can use the complete data from the network service provider, the data may not cover the behavior of the entire population. Other service providers will have different customer bases, and not all customers will behave identically. Thus, the data we analyze is a sample from the entire population. Recall from [Chapter 2](#02_001.html#h2), [Section 2.1](#02_001.html#h2.1), we may consider this experiment a random experiment, and the data points or observations are just outcomes of the experiment. In terms of probability, we may talk about the distribution of various attributes to gain an understanding how the shape of the underlying probability distribution. The summary statistics provides an understanding of the underlying distribution based on the observed values of the attributes. These statistics can broadly categorized in the following ways:

*   Measure of central tendency   
    Provides an understanding of the center of the distribution. Associated measures include the following:
    
    *   Mean: This value is the average of all the values of an attribute.
        
    *   Median: If the values of an attribute can be sorted, then the median is the middle observation in a sorted list of attribute values.
        
    *   Mode: This is the value of the attribute that occurs most frequently, that is, the value with the highest frequency.
        
*   Measure of dispersion   
    Provides an understanding of the spread of a distribution. Associated measures include the following:
    
    *   Range: The difference between the maximum and minimum values of an attribute.
        
    *   Variance and standard deviation: Discussed earlier in [Chapter 2](#02_001.html#h2), [Section 2.1.6](#02_001.html#h2.1.6).
        
    *   Interquartile range: When we sort the values of an attribute from minimum to maximum, the first quartile (Q1) is the value below which 25% of the attribute values are found. Similarly, Q2 and Q3 are second and third quartiles below which 50% and 75% of the attribute values are found, respectively. The interquartile range is the difference between Q3 and Q1, and this value shows the range where the middle 50% of the values of the attribute lie. Often, the distributions will involve a wide range of values; that is, minimum or maximum values are far away from each other. However, most values will be concentrated around some point, and only paying attention to range provides an incorrect picture of the dispersion. Interquartile ranges provide a better understanding of the spread of the distribution by focusing on where most values are clustered.
        
    *   Absolute deviation: The average of the absolute differences (i.e., without the sign of the difference) between attribute values and the mean or median.
        
*   Measure of shape   
    Provides an understanding of how the distribution looks like. Associated measures include the following:
    
    *   Skewness: The asymmetry of the distribution around its mean. Skewness is zero if the distribution of the data is symmetric around its mean. Skewness is positive or negative if most observations lie towards the left or the right of the mean, respectively, for a unimodal distribution.
        
    *   Kurtosis: How the tops and tails of the distribution appears, or the steepness of the peak in a distribution. A value 3 indicates a normal bell-shaped distribution, a value less than 3 (platykurtic) is flat-topped with short tails, and a value greater than 3 (leptokurtic) has a sharp top with tails spread out.
        
*   Measure of linear relationship  
    Shows how two attributes are linearly related to each other and is measured through the correlation coefficient (recall [Chapter 2](#02_001.html#h2), [Section 2.1.7](#02_001.html#h2.1.7)).
    

The information gathered through the summary statistics plays a key role in understanding the nature of the underlying distribution and is subsequently used during data preparation and model building. [Figure 3.6](#03_003.html#f3.6) shows the summary statistics for some distributions.

The shape of the distribution and the linear relationship across attributes can be also assessed through visualizations of the data. However, sometimes, data must be transformed based on shape and other correlation values; therefore, for automating the process, the associated statistics must be evaluated.

[![Summary Statistics of Sample Data (Based on AutoMPG Data)](bilderklein/klein03_006.png)](img-f3.6.html) 

**Figure 3.6**    Summary Statistics of Sample Data (Based on AutoMPG Data)

### 3.3.3    Visualizing Data

Data visualization refers to the display of information in a graphical format. Usually, the human brain interprets images better than the numbers, so representing your data in a graphical format can help you gain a good understanding of the data. Let’s consider an example, shown in [Figure 3.7](#03_003.html#f3.7), which visualizes the annual sales amount and net profit of a company across different countries. The size of a bubble is proportional to the sales amount, and the color represents the net profit. This graphical representation of data instantly reveals a lot of important information about the data.

[![Annual Sales Amount and Net Profit of a Company across Countries](bilderklein/klein03_007.png)](img-f3.7.html) 

**Figure 3.7**    Annual Sales Amount and Net Profit of a Company across Countries

As a second example, let’s consider the sales data of a company across several months, as shown in [Figure 3.8](#03_003.html#f3.8). The values of monthly sales amounts are joined by a line and immediately shows some patterns in the data, such as the following:

*   Sales across time has an increasing trend.
    
*   Sales amount data has a seasonality pattern, with high values in some months and low values in others. This cycle repeats over the year.
    
*   Some noises or random deviations are present in the data, evident from zigzag pattern of the curve.
    

[![Sales Data of a Company across Months](bilderklein/klein03_008.png)](img-f3.8.html) 

**Figure 3.8**    Sales Data of a Company across Months

These two examples show the power of data visualization in a graphical format. The same data in a tabular format would have obscured so much information.

From a machine learning perspective, the visualization of data provides insights into the distributions of attributes and their relationships. Various types of charts and plots, even simple ones like scatter plots, bar charts, and histograms, can reveal important information when the number of attributes in the data is small.

Scatter plots are simple plots where the x and y axes represent the values of two attributes, and the observations are represented by points based on their values of these two attributes. This plot gives a clear picture of the presence of any relationships between the attributes. The top three scatter plots in [Figure 3.9](#03_003.html#f3.9) shows near-linear relationship between two attributes price and age of secondhand cars, whereas the bottom scatter plot shows no specific relationship between price and mileage. In a classification problem, the class values of the observations may be shown with different colors in the plot, which provides a good picture of the nature of class boundaries. Also, scatter plots are useful for understanding if any clusters based on attribute values exist within the data.

Scatter plots are more useful for ordinal and continuous attributes. For a nominal attribute, separate scatter plots (using other attributes) can be checked for different category values of the nominal attribute to see whether the relationship among attributes changes across different categories of the nominal variable.

[![Information Revealed by Scatter PlotsScatter plots](bilderklein/klein03_009.png)](img-f3.9.html) 

**Figure 3.9**    Information Revealed by Scatter Plots

Histograms are also particularly useful for understanding the shape of the probability distribution of attributes based on observed data. A histogram plots the frequency of observations across a few groups of values of an ordinal or a continuous attribute. Sometimes, relative frequencies are also used instead of absolute frequencies to scale the values within the interval \[0, 1\]. However, this change in scale (only a change in scale of y axis) does not change of the shape of the histogram. For a nominal attribute, a bar chart or a Pareto chart may be used to show frequencies, or relative frequencies, across different values of the nominal attribute. [Figure 3.10](#03_003.html#f3.10) shows histograms of attributes with different types of distributions.

[![HistogramsHistograms Indicating Different Types of Distribution](bilderklein/klein03_010.png)](img-f3.10.html) 

**Figure 3.10**    Histograms Indicating Different Types of Distribution

One final remark: sometimes, using simple plots is better for data with multiple attributes. For example, the nature of the relationships among different attributes may be examined through scatter plots of two attributes at a time. While initially the result may involve a huge number of pairs, you can limit them based on your business understanding.

## 3.4    Preparing Data

Once you’ve identified the desired dataset from a business perspective and understand the nature of this data, you’ll usually need to process the data to make it optimal for your machine learning algorithms. This step is also known as data preprocessing. Some data preparation techniques transform the entire dataset through combining, creating, or removing attributes and data observations while some techniques work on individual attributes.

The specific data preprocessing activities you’ll undertake depend on the type of machine learning algorithms being used. Different algorithms have different levels of sensitivity to input data: Some algorithms, like linear regression, are more sensitive to predictor attributes whereas tree-based algorithms are less sensitive.

A thorough understanding of the business and the relevant data can help you decide how attributes should be used for modeling. Sometimes, combining multiple attributes into a single attribute may be more effective than studying individual attributes. For example, for a churn prediction problem, combining the number of billing complaints in the last 6 months may provide more insight than the numbers of billing complaints in individual months. A customer generally won’t lodge more than one billing complaint per month, so the attributes showing the number of billing complaints across months will have mostly zero values, with values of 1 for just a few customers. Aggregating the monthly billing complaints will show you the number of repeated complaints, which may have more influence on churn than billing complaints that are lodged once in a while.

Data processing can make or break the predictive ability of a machine learning model and is a critical step in any machine learning project.

### 3.4.1    Data Conversion

Various ways are available for transforming your data to make it suitable for machine learning algorithms. We’ll discuss some of these techniques in this section.

#### Aggregation

Depending on the objective, sometimes aggregating data may be more suitable using granular-level data. For example, if your sales data contains transaction-level details and the objective is to predict daily sales, then aggregating the transactional data at the day level makes sense.

Aggregation reduces the volume of data, making the data more computationally efficient. Also, often, aggregated data shows more stable behavior than individual data points and is thus suitable for identifying patterns.

#### Sampling

Sometimes, data is sampled before being used for machine learning, especially if the number of observations is too high. Sampling helps in performance and reduces runtime if the algorithm is computationally intensive. However, care must be taken to ensure the sample reasonably represents the true nature of the data. Different sampling schemes can be used to ensure a representative sample is obtained.

#### Feature Creation

Often, new predictor attributes (also known as features) are created to improve the predictability of a model. These attributes may be obtained through combining multiple attributes like adding two attributes together or taking the ratio of two attributes, or new attributes may be newly created based on the nature of the data. For example, let’s suppose our explorative analysis of customer churn data shows two distinct churn patterns for two different groups of customers, based on their duration of stay in the network. One group contains customers who stayed for more than a year; the other group contains the rest. In this case, we can add a predictor to indicate which group a customer belongs to, and this new attribute will improve churn predictability. A possible business interpretation may be that customers staying more than a year are mostly loyal customers, and they churn due to specific reasons, whereas customers staying less than a year show more random patterns of churn.

#### Feature Removal

Sometimes, you may need to remove predictors from the dataset. Adding unnecessary predictors can adversely affects the model, and the next section explains these impacts in detail. The usability of predictors must be checked, and predictors may be removed if not found useful. Two broad categories of predictors may be identified and removed:

*   Predictors having no relationship with responses  
    If the scatter plot of predictor and response does not show any pattern (i.e., the predictor follows almost same distribution across the values or classes of the response), then that predictor may be dropped. One typical case could be predictor with only one prominent value.
    
*   Predictors linearly related to each other  
    Two predictors may be linearly related to each other (a relationship called collinearity). In this case, the information contents of the predictors are almost the same, and one predictor can be removed. A careful study of the correlation matrix of these predictors may reveal the predictor pairs are linearly related. More than two predictors could be linearly related (a relationship called multicollinearity) and may adversely affect the model. Linear models like the linear regression model are highly sensitive to collinearity and multicollinearity, which we discussed in [Chapter 2](#02_001.html#h2), Section 2.3.1.3.
    

#### Binarization

Most machine learning algorithms expect input data in numbers due to the reliance on mathematical calculations. In the case of a categorical attribute, often, values are strings, which will need to be converted into numbers. However, if you use arbitrary numbers to represent categorical values as numbers, you may introduce serious problems in the resulting model. The numerical values of the categorical attribute may interact with other attributes incorrectly and provide spurious results. A different encoding may have different type of interaction, and the resulting model could be completely different. For example, if 50 different prepaid plans exist in our customer churn data and if we encode them arbitrarily from 1 to 50, the model considers these values as values from a continuous attribute, and the individual values will impact the model’s output. Another machine learning expert may code them from 10001 to 10050. To avoid this problem, proper encoding must be used.

In binarization, a categorical attribute X with m different values, say x[1], x[2], ... x[m] may be encoded with (m – 1) dummy attributes Z[1], Z[2], ... , Z[m-1] as in:

![inline image](bilder/EQ_087.png)

Note that, if X = x[m], the value of all the attributes Z[1], ... , Z[m-1] are zero.

[Figure 3.11](#03_004.html#f3.11) shows an example of the binarization of a categorial variable having 5 different values.

[![Binarization of a Categorical Attribute](bilderklein/klein03_011.png)](img-f3.11.html) 

**Figure 3.11**    Binarization of a Categorical Attribute

Note that, these new binary attributes do not interact with each other. Also, the data of other attributes associated with category x[i] interacts with the dummy variable Z[i] only, since the value of all other dummy variables are zero for this category. Note that we haven’t defined any dummy variable for the last value x[m] of the categorical attribute. Depending on which value we consider as the last value, the interpretation of estimated parameters may change (e.g., in the case of linear regression); however, the predictability of the model will also not change. Sometimes, the additional attribute Z[m] is introduced for last value x[m] of X and is defined in the following way:

![inline image](bilder/EQ_088.png)

#### Discretization

Sometimes, continuous attributes must be categorized into a few groups. This need may arise from the requirement of a specific algorithm, or perhaps, the attribute shows distinct patterns for different groups of values. For instance, the churn pattern may show distinct patterns for different income groups but not much variation across customers within the same income group.

For this purpose, mutually exclusive groups of attribute values are carefully chosen, and the values of the continuous attribute are mapped against these groups. [Figure 3.12](#03_004.html#f3.12) shows an example. Often discretization is followed by binarization.

[![Example of Attribute Discretization](bilderklein/klein03_012.png)](img-f3.12.html) 

**Figure 3.12**    Example of Attribute Discretization

### 3.4.2    Dimensionality Reduction

The dimensionality of a dataset refers to the number of attributes available in the data. In machine learning, we often encounter high-dimensional data. For regression and classification problems, we have one response attribute and many predictor attributes. So, if the number of attributes is high, we have more predictor attributes. At first, we may believe that, the more predictor attributes are present in the data, the better the predictability. However, that belief is not always the case because of two reasons:

*   If a predictor is not associated with the response, that predictor only increases the noise in the data and leads to higher test error. Predictability improves only when predictors are truly associated with the response.
    
*   The more predictors in the data, the more sparse the data becomes. For example, if you have 100 observations in the data and one categorical predictor X[1] with 5 categories, then you may expect an average of 20 observations per category. Now, if you have another categorical predictor X[2] with 10 different category values, the total number of categories for the combination (X[1], X[2]) is 5 × 10 = 50. Thus, on average, we may expect 2 records per category combination of (X[1], X[2]). However, some of these categories may have more data, and some categories may not have data at all. [Figure 3.13](#03_004.html#f3.13) shows an example of this scenario.
    
    The effective number of observations is reduced the more predictors there are, and the model will tend to overfit the data as a result.
    

This problem with higher-dimensional data is known as the curse of dimensionality.

[![Sparse Data with Introduction of New Predictors](bilderklein/klein03_013.png)](img-f3.13.html) 

**Figure 3.13**    Sparse Data with Introduction of New Predictors

Various techniques are available to reduce the dimensionality of your data. We already discussed principal component analysis (PCA) in [Chapter 2](#02_001.html#h2), section “Non-Linear Relationship between Predictor and Response”. Some other dimensionality reduction techniques include partial least squares, linear discriminant analysis, non-negative matrix factorization, and kernel PCA.

### 3.4.3    Variable Transformation

Variable transformation aims to replace an existing variable with a transformation of the variable (also known as an attribute). Different types of transformations are commonly used in machine learning, which we’ll discuss in this section.

#### Non-Linear Transformation

If the relationship between the response and a predictor is non-linear but we want to fit a linear model to the data, the predictor can be suitably transformed so that the relationship between response and transformed predictor becomes nearly linear. Transformations like X², √X, logX, e^X, 1/X, and X^n are commonly used for this purpose depending on nature of relationship. We discussed this concept in the context of linear regression in [Chapter 2](#02_001.html#h2), [Section 2.3.1](#02_003.html#h2.3.1).

#### Centering and Scaling

Continuous attributes are measured across different scales, and their mean values also vary. This variation can lead to a problem if you want to identify influence of individual attributes.

For example, let’s consider the following linear regression model:

Y = 100 + 7X[1] + 0.1X[2]

Where Y is the response variable and X[1] and X[2] are continuous predictors. X[1] ranges between 0 to 100, and X[2] ranges between 1000 to 1,000,000. This model shows that one unit change in X[1] changes the value of Y by 7 units, and one unit change in X[2] changes the value of Y by 0.1 units. Thus, X[1] appears to be the more influential predictor.

However, if we now measure the values of X[2] in a scale of 1000 units, then the equation would change to the following:

Y = 100 + 7X[1] + 100X[2]

since (new X[2]) = (old X[2]) / 1000, i.e., 1000 × (new X[2]) = (old X[2]) and 0.1 × (old X[2]) = 0.1 × 1000 × (new X[2]) = 100 × (new X[2]).

From this equation, X[1] seems to have a very negligible impact compared to X[2]. Thus, the same relationship gives us different interpretations about the influence of predictors. This problem is due to the different scales of X[1] and X[2].

Thus, some machine learning algorithms, especially ones that use the distances between data points, are sensitive to the scaling of input attributes. To resolve this issue, the following transformations can be applied on the values of continuous attributes:

*   Centering   
    Subtract the sample mean of an attribute from each value of the attribute. The sample mean of transformed attribute will be 0.
    
*   Scaling   
    Divide the attribute values by the sample standard deviation of the attribute. The sample standard deviation of the transformed attribute will be 1.
    

Centering and scaling are considered standardization, and both transform an attribute to a new attribute having zero mean and one standard deviation. With these transformed attributes, the predictors are now comparable, and the effect of difference in center and scaling factors can be neutralized for continuous attributes. Be aware that some machine learning algorithms expect continuous data in a standardized form.

#### Transformations to Resolve Skewness

If the distribution of an attribute is skewed, most attribute values are concentrated on one side of the distribution, and other side has a long tail of values with fewer observations. The tail part of the distribution acts like outliers, so machine learning algorithms sensitive to outliers tend to provide suboptimal results. Therefore, resolving skewness is important to improve the performance of some models.

Usually a log transformation is used to resolve skewness. If attribute X is highly skewed, the transformed attribute log(X) tends to be more symmetric. [Figure 3.14](#03_004.html#f3.14) shows the distribution of a skewed attribute and the distribution of the transformed attribute after a log transformation has been applied.

[![Distribution of a Skewed Attribute and Distribution after Log Transformation Is Applied](bilderklein/klein03_014.png)](img-f3.14.html) 

**Figure 3.14**    Distribution of a Skewed Attribute and Distribution after Log Transformation Is Applied

## 3.5    Developing the Model

Developing an efficient machine learning model to achieve the desired objective is one of the most challenging parts of any machine learning project. All the activities we’ve discussed so far in this chapter are preparatory activities for building an efficient model. Now, we get to build the model itself.

Selecting an appropriate algorithm is the first step in model building. However, for a single problem, multiple competing algorithms could be available, and determining which algorithm will work best can be difficult without trying all of them out. No one algorithm will be uniformly best for a problem: One algorithm may work best in one scenario; another algorithm may work best in a different scenario.

A few criteria to help you shortlist applicable algorithms for your machine learning project include the following:

*   Nature of the business problem  
    The business problem may be related to prediction, like a regression or classification problem, or the problem may be about revealing hidden patterns in data, like a cluster or association analysis. Accordingly, the applicable algorithms are shortlisted at a high level.
    
*   Interpretability   
    Whether the interpretation of the model is important. Some algorithms like linear regression and decision tree provide nice interpretations, but other algorithms, like ANN and k-NN, are just black boxes.
    
*   Data volume  
    Some algorithms are extremely sensitive if the total number of influential attributes is high when compared to the total number of observations.
    
*   Known advantage and disadvantages of algorithms  
    Some algorithms perform well in the presence of data issues like collinearity, outliers, and heteroscedasticity scenarios. If the data is expected to have some degree of these issues, appropriate algorithms may be identified.
    
*   Computational complexity  
    Less complex algorithms perform better when running over large datasets.
    
*   Ease of prediction  
    Some algorithms can be easily used for prediction purpose. For instance, decision tree rules can be used to predict a new observation, whereas the k-NN algorithm can calculate the distance of a new observation from all the observations found in the training data to predict.
    

In a machine learning project, typically multiple models, based on different algorithms, are tried out. These models are then evaluated and fine-tuned to find the best candidate model. Model evaluation and fine-tuning will be discussed in detail in the next section. Note that model building and model evaluation activities are performed iteratively, repeating back and forth, before arriving at an optimal model. We suggest the following approach to finalize the type of algorithm to use in your model:

1.  Start with a simple algorithm that provides more robust estimate, that is, the algorithm with the least tendency to overfit.
    
2.  Assess the performance of this model.
    
3.  If the estimated performance is aligned with the project’s goal and success criteria, fine-tune the model.
    
4.  If the estimated performance does not meet the project’s goal and success criteria, gradually use a more complex and flexible algorithm.
    
5.  Assess the performance of the new model.
    
6.  Repeat steps 3 to 5 until a suitable model is obtained.
    
7.  If none of the complex algorithms show satisfactory performance, then your data may not have recognizable patterns. Check with your business users and analyze the input data to see if the data can be enriched. With enriched data, start from step 1 again.
    

Sometimes, a final model may use multiple algorithms. For example, a prediction problem may run a Principal Component Analysis (PCA) first and then a linear regression analysis using the principal components. Model building depends heavily on the underlying data; no one-size-fits-all approach exists.

## 3.6    Evaluating and Fine-Tuning Model

During the modeling phase, multiple models are fit to the data. These models may be derived using different algorithms (e.g., k-NN and ANN for classification problem) or may be using the same machine learning algorithms but with different settings (different predictors, different values for the tuning parameters). For example, your may use liner regression models with different sets of predictors and ridge regression models with different values for λ. One important activity is to compare the performance of these models and select the best one.

Various techniques are available for identifying the best model, and in this section, we’ll discuss three different methods. However, first, let’s understand three basic concepts for evaluating our models.

### 3.6.1    Model Overfitting

When we fit a model in the data, the model identifies the pattern in the data and approximates the true relationship through some mathematical equations. However, the data we use is just a sample from the overall population and contains some noise or random deviations from the true relationship. If a model is extremely sensitive to data, the model will also accidentally capture the noise in the approximate relationship. As a result, the model fits very well to the data used for model building but performs poorly on another set of data, since this new data will contain a different set of noise data. As a result, the model gives poor predictions when applied to new data. This issue is known as model overfitting. [Figure 3.15](#03_006.html#f3.15) shows a k-NN model fit with two different values of k (1 and 15). While k = 1 fits the data very well, the model overfits the data and makes an incorrect prediction for a new record (marked with +). The model using k = 15 reasonably fits the data and makes better predictions.

[![k-NN Model Fitting with k =1 and k =15](bilderklein/klein03_015.png)](img-f3.15.html) 

**Figure 3.15**    k-NN Model Fitting with k =1 and k =15

### 3.6.2    Model Performance

Model performance measures how well a model achieves the stated objective. So far, we’ve primarily considered supervised learning models in this discussion.

In general, a prediction model is considered better performing if minimal errors occur when predicting a new observation. But how this error is calculated? For a regression problem, for instance, predicting a continuous variable, the error is the difference between the actual value and the predicted value. We introduced several measures, like RSS, RSE, and R² Statistics based on error terms, in [Chapter 2](#02_001.html#h2), [Section 2.3.1](#02_003.html#h2.3.1), where we discussed how to select a suitable model. We may extend these notions to a new set of observations to also get a measure of error.

Similarly, for a classification problem (i.e., predicting a categorical response), we may define the average number of observations misclassified. However, this model may not always serve the purpose of a good predictor in different scenarios, and therefore, different measures must be derived. [Figure 3.16](#03_006.html#f3.16) shows actual and predicted values in a 2-class prediction problem and the different measures associated with it.

[![Different Measures Associated with a 2-Class Classification Problem](bilderklein/klein03_016.png)](img-f3.16.html) 

**Figure 3.16**    Different Measures Associated with a 2-Class Classification Problem

Note that accuracy is the ratio of correct classifications and may be considered a measure of prediction performance. However, if the actual positive cases are small compared to the total number of observations, then a model that predicts all observations to be negative will have very high accuracy but may not serve the purpose. For example, in a churn prediction problem, the churn rate is typically 4% to 8%. Thus, if a model predicts that no customers will churn, it will misclassify 4–8% of total population and will achieve 92% to 96% accuracy. However, the model fails to serve the purpose. If we consider the True Positive Rate (TPR) as a measure of performance, then if a model predicts all customers will churn, the performance will be 100%. Critical success index (CSI) or F1 score may serve as a good estimation of performance in this case. [Figure 3.17](#03_006.html#f3.17) shows these statistics in the context of a churn prediction problem. Once a proper measure is identified, you can use this measure to estimate the performance of a classification model.

[![Performance Measure in Case of Churn Prediction Problem](bilderklein/klein03_017.png)](img-f3.17.html) 

**Figure 3.17**    Performance Measure in Case of Churn Prediction Problem

### 3.6.3    Model Fine-Tuning

Most machine learning algorithms have one or more tuning parameters that you can adjust to strike the right balance between robustness and overfitting. For example, the value of k is a tuning parameter for k-NN classification. The process of adjusting the tuning parameters to achieve optimal predictability by the model is known as fine-tuning the model.

### 3.6.4    Diagnostic Checks

Diagnostic checks are available to identify the best model out of a set of alternative models with different sets of predictors. These checks utilize underlying probability distributions to derive some goodness of fit statistics. Competing models can then be compared based on these goodness of fit statistics.

Suppose you have a dataset with n observations and Q predictors. You may have different models using different subsets of predictors from the entire set of Q predictors. Now, you need to find the best model out of these possible models. Different diagnostics checks can help you find out the goodness of fit of each model. Many such diagnostic checks exist, and most require advanced knowledge of statistics and probability, so we’ll omit the mathematical details of these checks. [Table 3.2](#03_006.html#t3.2) shows some of the widely used goodness-of-fit statistics for this purpose.

In these statistics, we used the following notations:

*   n is the total number of data points (i.e., number of observations or records) in the data.
    
*   k is the number of parameters estimated by the model. For a multiple linear regression with j predictors, the number of estimated parameters is (j + 2): one for the intercept, one for the estimated variance of errors (assumed to be constant), and j for slope parameters of j predictors.
    
*   A typical model uses p predictors from the set of Q predictors. The associated model is denoted as Mp[].
    
*   ![inline image](bilder/EQ_089.png)is the maximized value of the likelihood function of the model M[p].
    
*   ln() is the natural logarithm (i.e., logarithm with respect to base e).
    

 
| Goodness-of-Fit Statistic || Definition || Comment |
| --- | --- | --- |
| Akaike Information Criteria (AIC) || AIC = 2k – ln![inline image](bilder/EQ_089.png) || When n is small, AIC tends to select the model with too many parameters. |
| --- | --- | --- |
| Bayesian Information Criteria (BIC) || BIC = ln(n)k – ln![inline image](bilder/EQ_089.png) || Requires the number of records (n) to be much larger than the number of parameters (k). |
| Mallow’s C[p] || ![inline image](bilder/EQ_090.png), where RSS[p] is the RSS of the model with p predictors. (RSE is the Residual Standard Error after regression with all Q predictors, described in detail in [Chapter 2](#02_001.html#h2), [Section 2.3.1](#02_003.html#h2.3.1).) || Valid for assessing the fit of a regression model that has been estimated using least square method. |

**Table 3.2**    Different Diagnostic Checks for Assessing Goodness of Fit

Using any of these statistics, a model from a set of alternative models (with different sets of predictors) can be selected as the best model with the lowest values for each statistic.

###### Note

While fitting a model, the likelihood function measures the goodness of fit. But the value of the likelihood function increases with the addition of new parameters and may lead to model overfitting. Both AIC and BIC try to resolve this issue by introducing a penalty term. The best model is selected based on the lowest value of AIC or BIC, which decreases with high value of likelihood ![inline image](bilder/EQ_089.png)and increases with more parameters (k). Thus, AIC and BIC tries to increase goodness of fit by penalizing overfitting.

###### Note

Suppose you have a sample dataset x and you want to estimate a model M based on certain parameter set θ. As the parameter set θ changes, different models are generated. You can consider a particular dataset x is just a sample from probability space X. If you know the distribution of the probability space X, you can then calculate P(x | θ, M), which gives you the conditional probability of getting a sample data x given the true relationship is determined by model M with parameter θ. This probability is a function of parameter θ and written as L(θ) = P(x | θ, M). This function L is called the likelihood function, or simply likelihood.

This approach provides another way of estimating the parameters θ. The value of θ maximizes the likelihood function; this value gives the highest probability of observing the sample x. This method is known as the maximum likelihood estimation and is widely used in statistics. For linear regression models, both the least square method and maximum likelihood estimation approaches give the same estimate of parameters.

### 3.6.5    Validation Set Approach

Another way to assess a model is by introducing a validation set. For this purpose, the data is randomly divided into two parts: training data and validation data. The model is fit using the training data, and its performance is checked against the validation data. You can use this approach to compare multiple models based on their performance on validation data. This approach eliminates the problem of model overfitting, since models are evaluated against data not used when building the model. (Overfitted models are expected to perform poorly on validation data.) This remarkably simple strategy is widely used in machine learning.

Sometimes, the data is split into three sets: training data, validation data, and test data or hold-out data. In this setup, the validation is used for model evaluation purposes as before, but the performance of the final model is evaluated based on the test data, with the following considerations in mind:

*   Usually, the data is split in a 50:50 or 60:40 ratio between training and validation data.
    
*   If the number of records in the data is small, the training data will contain even fewer records and will lose important representative data.
    
*   The training and validation data must be selected carefully so that both are representative samples of the population. Thus, sometimes, stratified random sampling is used to ensure that both datasets are similar in nature.
    

### 3.6.6    K-Fold Cross Validation

In the validation set approach, model building and validation is performed based on partial data only, which may miss important patterns in the data. A different split of data may result in the model having a different accuracy. The k-fold cross-validation addresses this issue.

In this approach, data is randomly split into k groups or folds, usually of similar size. The first fold is kept aside for validation purposes, and model is developed on data from the remaining (k – 1) folds. The accuracy of the model is evaluated, and this process continues for each of the k folds. Each time, one fold is kept aside for validation, and the model is fit on the remaining data. The accuracy value obtained from each of these iterations is then averaged to get a final estimate of the accuracy of the model. [Figure 3.18](#03_006.html#f3.18) shows a schematic representation of this approach.

[![Schematic Representation of K-Fold Cross Validation](bilderklein/klein03_018.png)](img-f3.18.html) 

**Figure 3.18**    Schematic Representation of K-Fold Cross Validation

Note that, in this approach, model fitting and evaluation takes place k times. Therefore, if the algorithm is computationally expensive, the entire exercise may take long time. Usually, the value of k is between 5 to 10. Also, in this approach, every observation is used (k – 1) times during modeling and used once for validation.

One special case, called leave one out cross-validation (LOOCV), is when k equals the number of observations (n). In this case, the model is built on n – 1 observations and validated against one observation in each iteration.

## 3.7    Deploying the Model

Once the final model is selected, your model can be deployed into your production environment. The processes of data acquisition, data quality improvement, and data preparation are also deployed in production as prerequisites to model deployment. The deployed model scores the production data for prediction or pattern identification, which may be executed on demand or based on a predefined schedule.

Two important aspects associated with the model deployment are discussed in this section: maintaining optimal performance of the model over time and operationalizing the machine learning application.

In this fast-moving world, the nature of the business and environment changes quickly, and these changes are reflected in the data. Thus, production data may start revealing new patterns over time, eventually diverging from the data used for model building. For example, in a churn prediction scenario, the model might have used call drops from network issues as an important parameter for churn prediction. However, after implementing the model, the network service provider may take corrective actions to improve network bandwidth. Perhaps, in the next six months, network issues are no longer a significant parameter for analyzing churn at all.

Regular monitoring of model accuracy can reveal performance drops and trigger model adjustment. You can adjust the model in the following two ways:

*   The model may adapt itself to the changing business environment by virtue of the dynamic nature of the underlying algorithm. For example, if k-NN is used to predict churn, then before prediction for each month, the k-NN can be run with the latest churn data to capture decision boundary shifts due to changes in the environment, if any.
    
*   The model may be static in nature. In this case, periodic review of the model and adjustment must be carried out to accommodate the changing nature of the business.
    

Another important aspect is the operationalization of the model. Simply deploying a model in the production system is not enough; how the model is integrated with the business processes is also critical for success of the project. Without this integration, the usability of your model may be seriously impacted. Insights obtained from the model should be embedded into relevant business processes to institutionalize the machine learning solution.

## 3.8    Summary

In this chapter, you learned the key activities involved in the lifecycle of a machine learning project. These key activities—understanding the business; understanding and preparing your data; model building, evaluation, and deployment—are present in every machine learning project lifecycle regardless of the methodology used. Several machine learning concepts play important roles behind these key activities, like data quality improvement, summary statistics, visualizations, dimensionality reduction, data and variable transformations, diagnostic checks. validation sets, and k-fold cross-validation. Each machine learning project is unique in its own way, and no standard solution is applicable for all. The success of a machine learning project lies in the suitable application of these concepts and activities and in the institutionalization of your high-performing machine learning solutions into your business processes.

# 4    Machine Learning on SAP HANA

This chapter provides an overview of the machine learning components native to the SAP HANA platform. We’ll introduce you to different server-side and client-side components to use machine learning with SAP HANA for application development. We’ll also describe the key concepts behind server-side components and R integration. Since statistical models using R are often used on the SAP HANA platform, this chapter also introduces you to R and shows you some basic R commands.

SAP HANA provides a comprehensive environment for conducting predictive analytics using machine learning. SAP HANA offers embedded libraries of machine learning algorithms that you can use to develop machine learning applications natively in SAP HANA. It also supports integration with other machine learning tools and provides application programming interfaces (APIs) to access SAP HANA libraries so you can build client-side applications using R or Python.

In this chapter, we’ll start by describing the machine learning components embedded into SAP HANA in [Section 4.1](#04_001.html#h4.1), particularly the SAP HANA Predictive Analysis Library (SAP HANA PAL), the SAP HANA Automated Predictive Library (SAP HANA APL), and the SAP HANA Extended Machine Learning Library (SAP HANA EML). Then, in [Section 4.1.4](#04_001.html#h4.1.4), we’ll turn to SAP HANA with R integration.

## 4.1    SAP HANA Machine Learning Components

SAP offers different components to embrace a wide variety of machine learning solutions using the SAP HANA platform. These components can be broadly categorized as either server-side and client-side components. Server-side components enable you to develop machine learning solutions on an SAP HANA server, while client-side components allow you to utilize machine learning with SAP HANA from a client-side application developed in R or Python.

The following server-side machine learning components are available in SAP HANA:

*   Embedded machine learning libraries  
    SAP HANA provides two embedded machine learning libraries with algorithms for developing machine learning applications natively in SAP HANA:
    
    *   SAP HANA Predictive Analysis Library (SAP HANA PAL)  
        Contains machine learning algorithms that can be run by data scientists and machine learning experts. These algorithms can be fine-tuned by maintaining suitable values for the parameters.
        
    *   SAP HANA Automated Predictive Library (SAP HANA APL)  
        Contains machine learning algorithms for developing automated machine learning solutions. Given a specific problem, this solution automatically selects a suitable algorithm and fine-tunes the parameters to provide an optimal model. SAP HANA APL is suitable for business users with a minimal understanding of machine learning.
        
    
    Both of these libraries are part of the Application Function Library (AFL) delivered with SAP HANA. These solutions must be installed separately.
    
*   Integration with other machine learning tools/frameworks  
    SAP HANA can integrate with popular machine learning tools like R and Google TensorFlow to utilize the machine learning capability of these tools with the following components:
    
    *   SAP HANA Extended Machine Learning Library (SAP HANA EML)  
        Integrates SAP HANA with the TensorFlow framework. This component invokes predefined TensorFlow models on a special server called TensorFlow Serving, using Google’s remote procedure call (gRPC). SAP HANA EML is also a part of the AFL.
        
    *   SAP HANA with R integration   
        SAP HANA can integrate with an R software development environment to run stored procedures in SAP HANA with embedded R scripts. These R scripts are automatically transferred to a remote R server and executed on that server. Through this integration, SAP HANA can access thousands of machine learning and statistical algorithms in R.
        

The following client-side component is available as part of the SAP HANA client installation:

*   Machine learning APIs for client-side development  
    SAP HANA provides two APIs for using the SAP HANA PAL and SAP HANA APL algorithms from the client side:
    
    *   SAP HANA Python client API for machine learning algorithms  
        Allows you to run SAP HANA PAL and SAP HANA APL algorithms from Python. The API uses SAP HANA DataFrame, which provides a set of methods for directly analyzing your data in SAP HANA without transferring the data to the client. The API provides a package for SAP HANA PAL algorithms, a package for SAP HANA APL algorithms, and other packages for data frame management, visualization, and utility features.
        
    *   SAP HANA R client API for machine learning algorithms  
        Provides a package for SAP HANA PAL algorithms and allows you to run these algorithms from any R integrated development environment (IDE), for instance, R Studio. The algorithms themselves run in SAP HANA, so training data is not transferred to the R server or to the client side.
        
    
    Both these APIs must be installed as part of the SAP HANA client installation.
    

###### Machine Learning for Streaming Analytics

SAP HANA provides machine learning capabilities for streaming analytics, which refers to the analysis, through continuous queries, of huge volumes of moving data. This streaming data may originate from different sources like financial transactions, web interactions, the Internet of Things (IoT), and machine sensors. You can use machine learning to analyze patterns in the streaming data through clustering or classification. For example, you can identify fraudulent transactions by analyzing millions of financial transactions on the fly.

SAP HANA provides several SAP HANA PAL algorithms like DenStream clustering or Hoeffding tree classification for identifying patterns in the streaming data. Also, R integration with streaming analytics in SAP HANA allows R scripts to be executed as part of Continuous Computation Language (CCL) queries on the streaming analytics server.

Streaming analytics is a major topic, well beyond the scope of this book. Interested readers may refer to the latest edition of SAP HANA Streaming Analytics: Developer Guide for more details: [http://s-prs.co/501400](http://s-prs.co/501400).

### 4.1.1    SAP HANA Predictive Analysis Library

Machine learning algorithms require complex computations on data to arrive at a specific model. These computations require several sophisticated numerical techniques like matrix manipulation, numerical optimization, and evaluation of complex functions. Usually, most machine learning tools provide these algorithms as functions/procedures so that the data scientists or machine learning experts don’t have to write these algorithms by hand. Instead, the desired algorithms can be called from a program/editor using functions/procedures and configured with specific values for input data, output data, and model parameters.

In a similar way, SAP HANA also delivers machine learning algorithms for data scientists and machine learning experts as procedures within SAP HANA PAL. These procedures can be called from SAP HANA’s SQLScript procedures to perform specific machine learning-related tasks. Prior to SAP HANA 2.0 SPS 02, these algorithms were provided as SAP HANA PAL functions.

SAP HANA also provides the Application Function Modeler (AFM) tool, which is a graphical modeling tool in SAP HANA Studio. AFM supports accessing and executing SAP HANA PAL procedures in flowgraph models that can be configured with specific input tables, output tables, and parameter values, without writing any SQLScript code. AFM will take care of the code in the backend.

###### Note

SAP HANA PAL is part of the SAP HANA Application Function Library (AFL), which is a collection of complex application functions. These functions are grouped into multiple libraries depending on their application area, like the Business Function Library (BFL), SAP HANA Predictive Analysis Library (SAP HANA PAL), SAP HANA Automated Predictive Library (SAP HANA APL), and SAP HANA Extended Machine Learning Library (SAP HANA EML).

These application functions are written in C++ to achieve high performance and run on the SAP HANA database layer instead of on the application server so that the huge computational power of the SAP HANA database can be utilized. AFL is not part of the SAP HANA appliance; these libraries must be installed separately. [Figure 4.1](#04_001.html#f4.1) provides a high-level view of the architecture of SAP HANA PAL.

[![High-Level Architecture of SAP HANA PAL](bilderklein/klein04_001.png)](img-f4.1.html) 

**Figure 4.1**    High-Level Architecture of SAP HANA PAL

SAP HANA PAL includes procedures for different types of machine learning algorithms; some of the most commonly used algorithms were described in [Chapter 2](#02_001.html#h2). However, in the fascinating world of machine learning, thousands of algorithms are available for managing a wide variety of machine learning scenarios. SAP HANA has adopted the most commonly used algorithms based on market surveys and included them in SAP HANA PAL. Here, we’ll provide a list of the algorithms delivered with SAP HANA PAL as of SAP HANA 2.0 SPS 04:

*   Clustering
    
    *   Accelerated k-means
        
    *   Affinity propagation
        
    *   Agglomerate hierarchical clustering
        
    *   DBSCAN, geometry DBSCAN
        
    *   Gaussian mixture model (GMM)
        
    *   K-means, k-medians, k-medoids
        
    *   Latent dirichlet allocation
        
    *   Self-organizing maps
        
*   Classification
    
    *   Conditional random field
        
    *   Decision tree (including C4.5, CART, CHAID)
        
    *   Hybrid gradient boosting tree
        
    *   KNN
        
    *   Linear discriminant analysis
        
    *   Logistic regression (with elastic net regularization)
        
    *   Multi-class logistic regression
        
    *   Multilayer perceptron
        
    *   Naive Bayes
        
    *   Random decision trees
        
    *   Support vector machine
        
*   Regression
    
    *   Bi-variate geometric regression
        
    *   Bi-variate natural logarithmic regression
        
    *   Cox proportional hazard model
        
    *   Exponential regression
        
    *   Generalised linear models
        
    *   Multiple linear regression
        
    *   Polynomial regression
        
*   Social network analysis
    
    *   Link prediction
        
    *   PageRank
        
*   Association
    
    *   Apriori
        
    *   FP-growth
        
    *   K-optimal rule discovery (KORD)
        
    *   Sequential pattern mining
        
*   Time series
    
    *   ARIMA, auto-ARIMA
        
    *   Brown exponential smoothing
        
    *   Change-point detection
        
    *   Correlation function
        
    *   Croston's method
        
    *   Fast fourier transform
        
    *   Forecast accuracy measures
        
    *   Hierarchical forecast
        
    *   Linear regression with damped trend and seasonal adjust
        
    *   Exponential smoothing (single, double, triple, auto)
        
    *   Seasonality test, trend test, white noise test
        
*   Pre-processing
    
    *   Discretize
        
    *   Inter-quartile range
        
    *   Multidimensional scaling (MDS)
        
    *   Missing value handling
        
    *   Partition
        
    *   Principal component analysis (PCA)
        
    *   Random distribution sampling
        
    *   Sampling
        
    *   Scale, scale with model
        
    *   Variance Test
        
*   Recommender system
    
    *   Alternating least squares
        
    *   Factorized polynomial regression models
        
    *   Field-aware factorization machine
        
*   Statistics
    
    *   Anova
        
    *   Chi-square goodness-of-fit test
        
    *   Chi-squared test of independence
        
    *   Condition index
        
    *   Cumulative distribution function
        
    *   Distribution fitting
        
    *   Distribution quantile
        
    *   Equal variance test
        
    *   Factor analysis
        
    *   Grubbs' Test
        
    *   Kaplan-Meier survival analysis
        
    *   Kernel density
        
    *   Multivariate analysis
        
    *   One-sample median test
        
    *   T-test
        
    *   Univariate analysis
        
    *   Wilcox signed rank test
        
*   Miscellaneous
    
    *   ABC analysis
        
    *   T-distributed stochastic neighbor embedding
        
    *   Weighted score table
        

[Chapter 6](#06_001.html#h6), [Section 6.1](#06_001.html#h6.1) provides further details on how to utilize SAP HANA PAL procedures in machine learning projects.

### 4.1.2    SAP HANA Automated Predictive Library

SAP HANA APL provides machine learning algorithms suitable for automatic execution without requiring the fine-tuning of models through parameters. This solution is suitable for business users with little to no knowledge of underlying machine learning algorithms. SAP HANA APL contains functions that can serve as the building blocks for achieving AutoML functionalities.

#### SAP HANA APL Functions

SAP HANA APL provides several functions for creating and deploying automated predictive analytics. These SAP HANA APL functions are grouped into the following three service categories:

*   Predictive model services  
    These functions are used to create models, train models, and apply models to get predictions, recommendations. Other functions can retrieve information about models, variable statistics, and profit curves and can also publish models.
    
*   Predictive business services  
    These functions are used for applying simpler predictive services to the data such as retrieving statistics and profit curves based on training, validation, and test data; time series forecasting; information on key influential parameters; data profiling; one-shot recommendations; and exporting scoring equations.
    
*   Technical services  
    These functions are used to retrieve non-predictive aspects of SAP HANA APL functions like technical information about SAP HANA APL components, version information, and configuration information.
    

Each SAP HANA APL function is described by a signature, which is a list of parameter tables. Each parameter table is defined by a table type and is either an input (IN) or an output (OUT) type parameter. For example, the APPLY\_MODEL function, found under the rubric of predictive model services, has the parameters tables listed in [Table 4.1](#04_001.html#t4.1).

 
| Parameter Table || Type || Mandatory? || Description |
| --- | --- | --- | --- |
| FUNC\_HEADER || IN || No || Defines the operating parameters of a function call. |
| --- | --- | --- | --- |
| MODEL || IN || Yes || The trained model to be applied. |
| OPERATION\_CONFIG || IN || No || Configuration of the applied operation to specify the information required in the output, for instance, whether variables should be converted and/or whether outliers should be flagged in the output. |
| DATASET || IN || Yes || Input data. |
| DATASET || OUT || Yes || Output data, produced after applying the model. |
| LOG || OUT || No || Operation log. |
| SUMMARY || OUT || No || Debriefing information about the operation. |

**Table 4.1**    Parameters of the APPLY\_MODEL Function

Note that the parameters of an SAP HANA APL function are tables, defined by table types. They are used as input/output parameters while calling the function. The actual model parameters/details that determine the behavior of the model and its operation are specified through data in these tables. Thus, the mandatory input parameter tables must be populated with data. These SAP HANA APL function parameter tables follow specific structures. For instance, the FUNCTION\_HEADER table has the structure shown in [Table 4.2](#04_001.html#t4.2).

 
| Column || SQL Data Type || Description |
| --- | --- | --- |
| KEY || (N)VARCHAR, (N)CLOB || Specifies the parameter keys, like oid (operation ID) and language. |
| --- | --- | --- |
| VALUE || (N)VARCHAR, (N)CLOB || Specifies values of the respective parameter keys, like en for the language key to specify English language. |

**Table 4.2**    Structure of FUNCTION\_HEADER Table Type

[Figure 4.2](#04_001.html#f4.2) shows a pictorial representation of the signature of SAP HANA APL functions. For the complete specification for SAP HANA APL functions, including input/output tables and admissible values (i.e., model parameters), refer to the latest SAP HANA Automated Predictive Library Reference Guide on the SAP Help Portal ([http://s-prs.co/501401](http://s-prs.co/501401)).

[![Signature of an SAP HANA APL Function](bilderklein/klein04_002.png)](img-f4.2.html) 

**Figure 4.2**    Signature of an SAP HANA APL Function

#### Calling an SAP HANA APL Function

To use an SAP HANA APL function, an AFL wrapper procedure is created, and this AFL wrapper is invoked to call the SAP HANA APL function, which can be called using three different techniques, depending on the features they support. In an end-to-end modeling scenario, different techniques can be combined to call your functions, such as the following:

*   Direct  
    In this technique, an AFL wrapper for the SAP HANA APL function is generated through the explicit creation of table types, the signature table, and the input and output tables. The AFL wrapper is then invoked through a call statement. This technique allows you to build read-only procedures that wrap the SAP HANA APL functions. The direct technique is always available.
    
*   Procedure  
    Each SAP HANA APL function has a corresponding stored procedure using the same name. These procedures are automatically deployed as part of the HCO\_PA\_APL delivery unit when the function library is installed. SAP HANA APL functions can be called through these stored procedures, which will take care of the lifecycle of AFL wrappers and all their associated database objects. This technique is much simpler and more scalable than the direct method.
    
*   Any procedure  
    This technique does not require you to generate an AFL wrapper or to call the stored procedures in the HCO\_PA\_APL Delivery Unit. SAP HANA APL functions might be called as ANY AFLLANG procedures directly from the \_SYS\_AFL schema on SAP HANA. The AFL generates the wrapper. This technique is available on SAP HANA 2.0 SPS 03 onwards.
    
    [Figure 4.3](#04_001.html#f4.3) shows the architecture of SAP HANA and the various calling techniques.
    

[![SAP HANA APL Architecture and Calling Techniques](bilderklein/klein04_003.png)](img-f4.3.html) 

**Figure 4.3**    SAP HANA APL Architecture and Calling Techniques

These techniques support different functionalities and are suitable for a variety of scenarios.

### 4.1.3    SAP HANA Extended Machine Learning Library

SAP HANA EML allows SAP HANA to integrate with TensorFlow, which is an open source collection of machine learning algorithms that can solve a wide range of artificial intelligence (AI) and machine learning problems, especially if these problems require neural network or deep learning models.

#### Introduction to Google TensorFlow

Google TensorFlow is a powerful, open source, dataflow-oriented AI library for building models using data flowgraphs and can create large-scale neural networks with many layers. Google’s Brain Team initially created TensorFlow for internal use at Google, but the library was later released as open source in 2015.

TensorFlow can be described in the following way:

*   Primarily used for classification, perception, understanding, discovering, prediction, and creation.
    
*   Based on an easy-to-understand design and widely applicable to neural network-oriented problems.
    
*   A low-level toolkit for researchers to perform complicated math and build experimental learning architectures.
    
*   A programming system in which computations are represented as graphs. Nodes in the graph represent math operations, and the edges represent multidimensional data arrays (tensors) communicated between them.
    

Google TensorFlow comes with a scalable and interactive multiplatform programming interface that leverages various optimization techniques to make the calculation of mathematical expressions easier and more performant.

##### TensorFlow Serving Architecture

The TensorFlow runtime is a cross-platform library and its underlying architecture makes it a flexible and high-performance serving system for machine learning models. One key concept behind TensorFlow machine learning is TensorFlow Serving, which focuses on applying a model after its training. Serving machine learning models is the process of taking a trained model and making it available to serve prediction requests. When serving in production, you must ensure your environment is reproducible, enforces isolation, and is secure.

To understand the underlying architecture, you’ll need to understand some of the key building blocks of the architecture, shown in [Figure 4.4](#04_001.html#f4.4). The following components make this architecture flexible at scale:

*   Servables  
    In TensorFlow, servables represent objects used by clients to perform computation, which may consist of anything from a lookup table to a machine learning model. TensorFlow Serving provides out of the box integration with TensorFlow models but can be easily extended to serve other types of models. TensorFlow Serving also comes with several extension points where you can add new functionalities.
    
*   Servable versions  
    Servable can have multiple versions with difference in configurations, weights, which enables servable to operate in different scenarios. Multiple versions of a servable can be loaded simultaneously.
    
    [![TensorFlow Serving Architecture](bilderklein/klein04_004.png)](img-f4.4.html) 
    
    **Figure 4.4**    TensorFlow Serving Architecture
    
*   Servable streams  
    A sequence of versions of any servable sorted by ascending version number.
    
*   TensorFlow models  
    A TensorFlow model can be represented through one or more servables to achieve a specific machine learning or machine learning-associated task.. Multiple independent servables or a single composite servable can be represented as a composite model whereas a servable can also serve like a fraction of a model.
    
*    Loaders   
    TensorFlow loaders are solely responsible for managing a servable’s lifecycle including loading and unloading them through a set of APIs independent of any specific learning algorithm, data, or product use case involved.
    
*   Sources  
    In simple terms, sources are modules that find and provide the necessary servable, which can be either zero or more servable streams at a time. For each servable stream, a source supplies only one loader instance, which is made available to be loaded and can maintain the state shared across multiple servables.
    
*   Aspired versions  
    An aspired version represents a set of servable versions that should be loaded and ready. Sources communicate this set of servable versions for a single servable stream at a time to the manager and manager uploads or unloads servables based on this list.
    
*   Managers  
    TensorFlow managers control the entire life cycle of the servables, including loading them, serving them, and unloading them. It interacts with sources to cater to the requests coming from the sources, like uploading a new servable version. It also provides interface for clients to access loaded servable instances.
    
*   Version policy   
    Version policies specify the sequence in which servable versions to be loaded and unloaded within a single servable stream. TensorFlow serving usually deploys one of the following two policies: the Availability Preserving Policy, that ensures at least one version of the servable is available; and the Resource Preserving Policy, that ensures two versions of the servable are not present simultaneously. The first policy loads a new version and then unloads an old version, whereas in second policy the old version is unloaded first before loading a new version.
    

#### Integrating TensorFlow through SAP HANA EML

The integration of TensorFlow with SAP HANA is achieved through the SAP HANA EML component. The overall architecture is shown in [Figure 4.5](#04_001.html#f4.5).

[![TensorFlow Integration with SAP HANA](bilderklein/klein04_005.png)](img-f4.5.html) 

**Figure 4.5**    TensorFlow Integration with SAP HANA

The AFL for SAP HANA EML is the TensorFlow Serving Client for SAP HANA, which can invoke predefined gRPC calls in TensorFlow models. TensorFlow ModelServer enables the execution of TensorFlow models in the SavedModel format through gRPC calls. The gRPC server enables communication with the TensorFlow ModelServer client. The CloudHook server manages the integration of SAP HANA with external servers, such as SAP Data Intelligence, or with external cloud providers.

### 4.1.4    R Integration

R is an integrated software environment for the manipulation, calculation, and graphical display of data. R is widely used by statisticians and data scientists for statistical analysis and graphics. This free, open source software is supported by the R Foundation for Statistical Computing. R is an implementation of the statistical programming language S, which was developed by John Chambers, Rick Becker, and Allan Wilks at the Bell Labs in 1976. Ross Ihaka and Robert Gentleman experimented with the S language at the University of Auckland in early 1990 and developed the R language. The name R is partly inspired by the first names of the authors and partly due to its connection with the S language. Since 1997, R has been developed by the R Development Core Team.

The R environment provides various prebuilt statistical models across different packages that you can easily use for statistical analysis. Also, its rich graphical display capabilities are suitable for exploratory data analysis and analyzing model outcomes. Prebuilt R functions are grouped across packages, which are like libraries in other programming languages. The base installation includes a set of default packages. Additionally, thousands of user-contributed packages can be downloaded from the R website to fulfill specific requirements. Some R packages are described in detail in [Chapter 6](#06_001.html#h6), [Section 6.2.2](#06_002.html#h6.2.2).

The starting point for installing R is the R website at [www.r-project.org](http://www.r-project.org), the homepage of which is shown in [Figure 4.6](#04_001.html#f4.6). You can install R by clicking the CRAN link under the Download heading on the left. CRAN stands for “Comprehensive R Archive Network” and allows users to select a regional computer network for R installation.

Other R editors are available, like Tinn-R and WinEdt, as well as other integrated development environments (IDEs) like R add a space here Studio.

#### Integration with SAP HANA

R provides thousands of statistical and machine learning functions, ranging from basic data analysis to sophisticated statistical analysis. SAP HANA with R integration brings together the best of both worlds. Through integration, the rich collection of R functions become available to SAP HANA, and these functions can be executed using the data in SAP HANA. For example, Principal Component Analysis (PCA) is not suitable for categorical data. However, in practice, we often deal with many categorical variables and may often need to reduce dimensionality of the data. A different technique called Categorical PCA can handle PCA with categorical variables. SAP HANA PAL does not provide algorithms for Categorical PCA analysis, although R does through packages like Gifi and PCAmixdata. So, R integration enables SAP HANA to run Categorical PCA, which would not be possible otherwise.

[![The R Homepage](bilderklein/klein04_006.png)](img-f4.6.html) 

**Figure 4.6**    The R Homepage

###### Note

R is an open source software available under the GNU General Public License. SAP does not ship the R environment with the SAP HANA database and does not provide support for R. For more information on SAP HANA and R compatibility, refer to SAP Note 2185029.

The integration between an SAP HANA server and an external R environment is established through the following two components:

*   The R client in the SAP HANA calculation engine communicates with the external R environment.
    
*   Rserve is an R package that acts as a socket server (TCP/IP or local sockets) and allows other applications to connect to R. This package supports remote connections, user authentication, and file transfers.
    
*   Once the integration is complete, R code can be embedded into SAP HANA SQL code in the form of an RLANG procedure and can be executed in-line as part of the overall query execution plan. [Figure 4.7](#04_001.html#f4.7) shows the overall integration.
    

[![Integration between SAP HANA and the R Environment](bilderklein/klein04_007.png)](img-f4.7.html) 

**Figure 4.7**    Integration between SAP HANA and the R Environment

When the calculation model plan execution reaches an R operator, it hands it over to the R client in the calculation engine. The R client establishes a dedicated R process on the external R environment through the Rserve. Then, the R client uses this dedicated R process to send the R code, input data, and parameters to the external R environment, where the R execution is triggered, and results are received. Note that SAP HANA uses column-based data structures, and R uses the R data frame, so data is converted to respective structures during this process. However, the conversion is efficient because of the similarities between these data structures.

###### Limitations

*   Some of the limitations of R integration include:
    
*   The data is exchanged between SAP HANA and R using tables (in SAP HANA) and data frames (in R).
    
    *   Only table types are supported as parameters in the SAP HANA procedures with RLANG language.
        
    *   Scalar parameters need to be passed as tables or data frames to R.
        
    *   Other data structures in R (like lists and matrices) must be converted to data frames using the as.data.frame() function before sending them back to SAP HANA.
        
*   Embedded R functions must have at least one result (as a data frame).
    
*   The variable names from the procedure should not contain uppercase letters.
    
*   SAP HANA sends the Factor columns as character vectors, which may need to be converted to Factor using the as.factor() in R.
    

#### Basic R Programming Concepts

The R integration with SAP HANA allows writing R codes as part of the SAP HANA SQLScript procedures with RLANG language. Hence it is essential to know some of the R commands for data manipulation, calculation and statistical computing. Due to the limitations mentioned above, not all commands will be useful while writing R code from SAP HANA. However, it is always better to know the basic R commands to have a high-level understanding of the subject. In this section we have put together some of the basic R commands, interested readers may refer to the pdf documents from R or numerous books on R for detailed understanding.

##### Preliminaries

R is an expression language with a simple syntax. The codes are written in the form of commands. Commands are separated by a semi-colon (;) or by a new line. Elementary commands are of two types:

*   Expressions  
    Are evaluated and printed (if not made invisible), and the value is lost.
    
*   Assignments  
    Are evaluated, and the value is passed to a variable; the result is not printed. The variable name is a reference or pointer that refers to a value and not to a formula. The value of the variables can be seen by typing its name. Technically speaking, an assignment is also a special type of expression.
    

Multiple elementary commands can be grouped together into a composite expression using curly braces ({ and }). Comments can be including by using a hashmark (#). The usual prompt is >. However, if a command does not complete in a single line, the prompt will change to +. These default settings can be changed. The commands can be recalled by pressing the up (ì) and down (ë) keys.

The entries created and manipulated in R are known as objects, which are created and stored by name. Some different types of objects in R include the following:

*   Vector  
    A collection of values of similar modes. The basic modes a vector supports are logical, numeric (integer or double), complex, character (string), and raw. A single value is also a vector of length 1.
    
*   Array  
    A multidimensional generalization of a vector. It may be considered as a vector indexed by two or more indices.
    
*   Matrix  
    A special type of array with two dimensions, i.e., a two-dimensional generalization of vector, similar to a matrix in linear algebra.
    
*   Factor  
    Special type of vector containing categorical data (e.g., educational background, gender, marital status), designed to handle categorical data efficiently.
    
*   List  
    General form of vector where individual components need not be of a similar type.
    
*   Data frame  
    Special type of list that contains vectors, factors, and matrices, all having same length (or number of rows for matrices). It resembles a matrix, but the individual columns need not be of the same type.
    
*   Expression   
    Contains one or more parsed, but unevaluated, R statements.
    
*   Function  
    Provides an output from the input(s) by applying a specific logic, like maximum of a set of values. Any function in R is written as:
    
    function\_name (argument1, argument2, …)
    
    The function\_name is the name of the specific function and it may have one or more argument values, some of them may be optional. Sometimes it may also be written as
    
    function\_name (arg1= value1, arg2 = value2, …)
    
    In this case, arg1, arg2, etc., represent the specific arguments, and value1, value2, etc. represent the value of the corresponding arguments. This notation is particularly useful when there are optional arguments and we want to specify only few arguments. Variables and expressions can also be used instead of values in the arguments of a function.
    

All objects in R have a class, which enables object-oriented programming in R. Some examples of classes are list, matrix, array, factor, and data.frame.

A workspace is the collection of all the objects currently stored. All objects created during an R session can be saved to a file called .RData, and all command lines can be saved to a file called .Rhistory in the current directory. The workspace and the command history will be loaded from these files the next time R is started.

R is case sensitive; usually the alphanumeric symbols are used in the names of objects. For portable R code, use only the characters A-Z, a-z, and 0-9. The period (.) and the underscore (\_) can also be used with the restriction that a name must start with a period (.) or a letter. If a name starts with a period (.), the next character cannot be a digit. No restriction on the length of a name exists.

Before exploring other commands, let’s look at a simple R code shown in [Figure 4.8](#04_001.html#f4.8).

[![Simple R Code Examples](bilderklein/klein04_008.png)](img-f4.8.html) 

**Figure 4.8**    Simple R Code Examples

Some common R commands are listed in [Table 4.3](#04_001.html#t4.3).

 
| Expression || Functionality || Example |
| --- | --- | --- |
| <- || Evaluates the value of the right side and assigns this value to the variable on the left. || x <- 5 |
| --- | --- | --- |
| \= || Assigns a value. || x = 5 |
| +, -, \*, /, ^ || Mathematical operations (summation, subtraction, multiplication, division, power function). || 2\*x + 3/7 - 2 |
| \> || Boolean operator > evaluates to TRUE if the left side is greater than the right side; FALSE otherwise. || x > y |
| < || Boolean operator < evaluates to TRUE if the left side is smaller than the right side; FALSE otherwise. || x < y |
| \== || Boolean comparison operator == evaluates to TRUE if the left side is equal to the right side; FALSE otherwise. || x == y |
| : || Generates a sequence of numeric values, taking the value of the left side of the operator and generating a sequence by incrementing this value by 1 until the value is less than or equal to the value on the right side. || 1:10It gives sequence of numbers from 1 to 10.1.1:10 generates the sequence1.1, 2.1,…, 9.1 |
| # || Adds a comment. || \# sample comment |
| ? || Accesses the help file. || ? boxplot |
| help || Accesses the help file. || help(boxplot) |
| library || Loads a package. || library (MASS) |
| setwd || Sets the working directory. || setwd (“C:/data”) |
| source || Executes stored commands in an external file. || Source (“commands.R”) |
| q() || Closes R. || q() |

**Table 4.3**    Some Common R Commands

##### Vectors

A vector is an ordered collection of values of the same mode. For example, a collection containing the integers 1, 2, 3, 7, and 11 can be regarded as a vector. Similarly, a collection of names (characters), for instance, “Ranajay,” “Dinesh,” “Kalpana,” “Kakali,” and “Subhasree,” can be considered a vector. If different modes of values are collected in a vector, then R automatically converts them into a vector of the same mode. For instance, a collection of values of different modes (e.g., 1, 10.5, and “Blue”) will be converted into a vector of characters with the values “1”, “10.5”, and “Blue.” Statistical analysis often relies on techniques from linear algebra and vectors play a pivotal role in that.

You can use the c() function to create a vector. This function can have values, variables, or expressions as arguments. [Figure 4.9](#04_001.html#f4.9) shows several different ways to define a vector.

Arithmetic expressions and Boolean expressions can be evaluated using vectors. Furthermore, several prebuilt functions can be used on vectors, such as like mean, var, max, and min. The length of the vector refers to the number of objects in the vector. If two vectors of unequal length are used in an expression, then the shorter vector is repeated until it matches the length of the other vector(s). A sequence operator, the colon (:), can also be used to define a vector of a sequence of numbers. [Figure 4.10](#04_001.html#f4.10) shows some functions applied to vectors.

[![Defining Vectors in R Using the c() Function](bilderklein/klein04_009.png)](img-f4.9.html) 

**Figure 4.9**    Defining Vectors in R Using the c() Function

[![Operations and Functions on Vectors](bilderklein/klein04_010.png)](img-f4.10.html) 

**Figure 4.10**    Operations and Functions on Vectors

An element of a vector can be identified using the following expression:

```
Vector_Name [index]
```

Where the vector\_name is the name of the vector, and the index is the position of an element in the vector. For example, let’s say x is a vector defined in the following way:

```
x <- c(1, 2, 4, 9) 
```

In this case, the 3rd element of the vector can be retrieved through x\[3\]. The output will be 4. A negative index value can also be used to exclude an element from a vector. For example, x\[-3\] would be a vector with the values 1, 2, and 9, thus excluding the 3rd element from the vector. In some cases, some components of a vector may be unavailable or missing. In this case, that component can be assigned with a special value: NA. In general, any operation with NA becomes NA. For example, consider the following code:

```
> (x <- c(1:5, NA))
[1]  1  2  3  4  5 NA
> x + 1
[1]  2  3  4  5  6 NA
```

In this case, NA has been assigned to the 6th component of the vector x. The expression x + 1 also generates a vector with NA at the 6th component.

##### Arrays and Matrices

Arrays are ordered collections of multiple indexed data entries. Similar to vectors, one main difference is that values in an array represent data from a multidimensional grid. Technically, a one-dimensional array is also possible. An array has two parts: a data vector and a dimension vector. The dimension vector specifies the dimensions of the array. The entries of a dimension vector are always positive integers. If the dimension vector of an array has k entries (n[1], n[2], ... , n[k]), then the array is a k\-dimensional array that has n[1] × n[2] × ... × n[k] data entries. A matrix is a 2-dimensional array. The value of an element or subarray from an array can be obtained through its index. [Figure 4.11](#04_001.html#f4.11) shows an example of an array.

A vector in R can be converted into an array by assigning a dimension vector to its dim attribute. Suppose you have a vector A with 30 values. Then, we use the following code:

```
> dim(A) <- c(3, 5, 2) 
```

This code assigns the vector (3, 5, 2) as the dimension vector to A and makes it an array. As a result, the vector A has values across three indices (dimensions): The first index has values 1 to 3, the second index has values 1 to 5, and the third index has values 1 and 2. Note that 3 × 5 × 2 = 30. While assigning data values against indices, the values of the indices are varied from 1 to the number of values specified in the dimension vector, with indices in the left moving the fastest. [Figure 4.12](#04_001.html#f4.12) shows some useful commands and demonstrates how values are assigned with indices.

[![Example of an Array](bilderklein/klein04_011.png)](img-f4.11.html) 

**Figure 4.11**    Example of an Array

[![Creating Arrays and Matrices in R](bilderklein/klein04_012.png)](img-f4.12.html) 

**Figure 4.12**    Creating Arrays and Matrices in R

Some important commands on matrices, useful in linear algebra, are listed in [Table 4.4](#04_001.html#t4.4).

 
| Expression || Functionality |
| --- | --- |
| A \* B || Element-by-element product of two square matrices A and B (with matching dimensions). |
| --- | --- |
| A %\*% B || Matrix product of A and B (with matching dimensions). |
| A %\*% x || Product of a matrix A with a vector x (with matching dimensions). |
| solve(A) || Inverse of A, where A is a non-singular matrix. |
| solve(A, b) || Provides solution to linear equations Ax = b, where A is non-singular. |

**Table 4.4**    Some Commands Related to Matrices

##### Lists and Data Frames

A list in R is an ordered collection of objects known as components. The components of a list may not be of same type but could be any object like vectors, matrices, or even functions. The list function can be used to create a list, for example:

```
MyLst <- list(student ="Soham", year = 2020, subjects = c("math", "physics", "chemistry"), marks = c(100, 94, 89))
```

In this case, the list called MyLst contains four components of type character, numeric, character vector, and numeric vector, respectively. [Figure 4.13](#04_001.html#f4.13) shows how the list will appear on the screen, including how the various components are referenced.

A data frame is a similar object to a list of the class data.frame, but in this case, the lengths of the individual components are the same. A data frame may contain vectors, factors, and matrices all having same length (or number of rows for matrices). For practical purposes, a data frame can be considered a matrix with vectors of numeric values or factors. You can use the data.frame() function to define a data frame. The individual components of a data frame can be referred to in a similar way to a list.

##### Reading Data from Files

To work with large amounts of data, you’ll need to import this data into the R environment. The read.table(“file\_path”) function reads data from a file stored in the file\_path. By default, R expects the file to be a tab-delimited .txt file where the first column is the row number (without a header) and other columns have headers in the first row. If row numbers are not maintained in the file, but headers have been maintained, then use read.table(“file\_path”, header = TRUE) to read the data. Column headers should follow the R naming standard. Other arguments of the read.table function can handle various scenarios like file types, delimiters, decimal notations, and more. Please refer to the help on read.table function. The data must be assigned to a data frame. Usually, numeric columns are read as numeric vectors, and character variables are read as factors. If a file is in the comma-separated values (CSV) format, then you’ll use the read.csv function in the same way as the read.table function.

[![Creating a List and Referring to Components of a List](bilderklein/klein04_013.png)](img-f4.13.html) 

**Figure 4.13**    Creating a List and Referring to Components of a List

R can also read data from various other sources, including a relational database management system (RDBMS) and statistical packages like SAS and SPSS, using functions from different packages. Please refer to help files to know more on this.

##### Control Statements

The R language has the following control statements:

*   If statement  
    The following statement can be used for conditional execution:
    
    ```
    > if(expression1) expression2 else expression3 
    ```
    
    The expression1 should evaluate to a single logical value (TRUE or FALSE). If TRUE, expression2 is executed; otherwise, expression3 is executed.
    
    R also supports a vector version of an if statement, such as the following:
    
    ```
    > ifelse(condition, a, b) 
    ```
    
    The arguments condition, a, and b are all vectors. This statement returns a vector with the length of the vector condition and with the value a\[i\] or b\[i\] as the i\-th component depending on condition\[i\] is true or false, where i runs across 1 to the length of the vector condition.
    
*   For loop  
    R provides the following syntax for running a statement in a loop:
    
    ```
    > for (dummy_name in expression1) expression2
    ```
    
    The dummy\_name is the loop variable, expression1 is a vector (often a sequence like 1:10), and expression2 is an expression that is repeatedly evaluated, often based on value of dummy\_name.
    
*   Repeat and while  
    \> repeat expression and while (condition) expression can also be used for looping the same expression multiple times. A break statement must be included in the expression, or else the loop will continue indefinitely. You can use a next statement to skip a particular statement and move on to the next statement.
    

##### Fitting Statistical Models in R

R includes rich set of statistical analysis functions across different packages. In this section, we’ll only touch upon the function to develop a linear model. For other types of models, please refer to the help file of R.

Linear models in R can be fitted with the following function:

```
> fitted.model <- lm(formula, data = data.frame) 
```

For example:

```
> fitted_model <- lm(y ~ 1 + x, data = input_data)
```

Where input\_data is a data frame having two columns x and y, and the result of the fitted model is stored under the list fitted\_model. The formula is a separate class of objects that specifies the type of relationship between response(y) and predictors(x). Some formulas are listed in [Table 4.5](#04_001.html#t4.5). Note that x and y are simply placeholders; the desired column names from the input data can be used.

 
| Formula || Interpretation |
| --- | --- |
| y ~ x ory ~ 1 + x || Simple linear regression of y on x with intercept term. |
| --- | --- |
| y ~ 0 + x ory ~ –1 + x ory ~ x – 1 || Simple linear regression of y on x without the intercept term. |
| y ~ x[1] + x[2] || Multiple linear regression of y on x[1] and x[2] with the intercept term. |
| log(y) – x[1] + x[2] || Multiple linear regression of log(y) on x[1] and x[2] with the intercept term. |
| y ~ poly(x, 2) || Polynomial regression of y on x of degree 2. It uses orthogonal polynomials. |
| y ~ 1 + x + I(x²) || Polynomial regression of y on x of degree 2. It uses explicit powers of x. |

**Table 4.5**    Example Formulas

Once the model is fitted, the information on the fitted model can be extracted using components of the list fitted\_model or some functions on fitted\_model. A few important commands are shown in [Figure 4.14](#04_001.html#f4.14).

[![Basic Information about the Fitted ModelFitted model](bilderklein/klein04_014.png)](img-f4.14.html) 

**Figure 4.14**    Basic Information about the Fitted Model

Summary information about the model can also be displayed, as shown in [Figure 4.15](#04_001.html#f4.15).

The fitted model also shows four plots on residuals and other diagnostic checks to assess the model’s goodness of fit, as shown in [Figure 4.16](#04_001.html#f4.16).

[![Summary Information of the Fitted Model](bilderklein/klein04_015.png)](img-f4.15.html) 

**Figure 4.15**    Summary Information of the Fitted Model

[![Plots for Diagnostic Checks on the Fitted Model](bilderklein/klein04_016.png)](img-f4.16.html) 

**Figure 4.16**    Plots for Diagnostic Checks on the Fitted Model

Also, the fitted model can be used for predicting the responses of a new set of predictors, as shown in [Figure 4.17](#04_001.html#f4.17).

[![Predicting New Data Based on the Fitted Model](bilderklein/klein04_017.png)](img-f4.17.html) 

**Figure 4.17**    Predicting New Data Based on the Fitted Model

Other functions are associated with fitted models. Please refer to the R help file for the details. We will discuss running R codes from SAP HANA in more detail in [Chapter 6](#06_001.html#h6), [Section 6.2.3](#06_002.html#h6.2.3).

##### Graphs and Plots

One of its major strengths, R provides a powerful set of graphical functionalities for visualization and exploratory data analysis. Entirely new types of graphs can be generated using R commands. You cannot view R visualizations natively from SAP HANA, but R visualizations can be integrated with SAP Analytics Cloud to access the rich set of graphs and plots available with R, which is beyond the scope of this book. [Table 4.6](#04_001.html#t4.6) lists some basic plotting commands in R.

 
| Expression || Functionality |
| --- | --- |
| plot(x, y) || x and y are vectors; this expression produces scatter plot of vectors x and y. |
| --- | --- |
| plot(x) || If x is a numeric vector, this expression produces a plot of values of x against the index values. If x is a time series, then it produces a time series plot. |
| plot(f) || f is a factor; this expression produces a bar plot of f. |
| plot(f, y) || f is a factor, and y is a numeric vector; this expression produces boxplots of y for each level of f. |
| plot(df) || df is a data frame; this expression produces distributional plots of vectors or factors in df. |
| pairs(X) || X is a data frame or matrix; this expression produces pairwise scatterplots of columns in X. |
| coplot(x ~ y | z) || x and y are numeric vectors, z is a factor; this expression produces a scatter plot of x and y for each level of z. |

**Table 4.6**    Basic Plotting Commands in R

Various graphical functions like qplot(), boxplot(), ggplot(), mosaicplot(), and heatmap() are available across packages to produce graphs in different scenarios. Please refer to R manuals for more details.

## 4.2    Summary

Machine learning requires a wide range of algorithms to accommodate different types of use cases. SAP HANA includes a wealth of machine learning capabilities either through embedded machine learning libraries or through integration with external machine learning tools/frameworks. The SAP HANA Predictive Analysis Library (SAP HANA PAL) and the SAP HANA Automated Predictive Library (SAP HANA APL) are the embedded machine learning libraries in SAP HANA. These components contain widely used machine learning algorithms: SAP HANA PAL provides data scientists and machine learning experts the flexibility to fine-tune models whereas SAP HANA APL provides automated machine learning solutions suitable for business users. SAP HANA can also be integrated with Google TensorFlow through the SAP HANA Extended Machine Learning Library or with an external R environment to access the rich machine learning capabilities of these tools. Furthermore, SAP HANA also provides client-side APIs like the SAP HANA Python client API for machine learning algorithms and the SAP HANA R client API for machine learning algorithms so you can use SAP HANA’s machine learning capabilities with a Python or R environment.

# 5    Machine Learning with SAP Data Intelligence

With the SAP Data Intelligence platform, SAP took a giant leap to empowering the intelligent enterprise. In this chapter, you’ll learn about SAP’s latest data science platform, including its unique features and components. We’ll also dive deeply into the technicalities of underlying machine learning and data science concepts to help you comprehend the vast potential of the platform and its applicability to building intelligent solutions. The knowledge you’ll gain from this chapter will also help you understand the hands-on chapters that follow.

Before we start our discussion of SAP Data Intelligence or define it as a product, setting the context on the right track is vital to understanding what today’s enterprises need from a data science platform in totality and how they can effectively utilize it to apply enterprise intelligence. Today’s enterprises have realized that only a portion of the enormous transformational potential of their enterprise data is being utilized because their data science teams have lacked the right platform to analyze the data and build effective machine learning models and scenarios. Without a robust data science platform, models may ultimately lack accuracy and robustness and frequently never make it into production. Thus, the effectiveness of a data science platform is of utmost importance for enterprises hoping to take advantage of enterprise intelligence. As a holistic approach, enterprise intelligence is all about machine learning and its integration into enterprise applications to create a truly scalable, governed, and transparent way to rapidly deliver business value out of enterprise data. Enterprise intelligence incorporates artificial intelligence (AI) into enterprise contexts alongside capabilities for the management of data, the development of AI models and scenarios, and the governance of data and models across various enterprise environments. To rapidly derive value from your business data, bringing together enterprise intelligence and intelligent information management in a trusted and governed manner is a crucial requirement. The ultimate result is often an increasingly complex landscape that is well adapted so you can discover intelligence out of enterprise data coming from various sources and formats.

However, delivering all of these capabilities into a single platform can be quite challenging, especially when every stakeholder, including chief information officers (CIOs), the IT operations team, data scientists, and the DevOps team, have different points of view, as shown in [Figure 5.1](#05_001.html#f5.1):

*   For the CIO, the focus is on stable, scalable data science or machine learning applications at low cost.
    
*   For the data science team, the focus is on a development environment that is compatible with enterprise requirements, while still providing room for exploration.
    
*   For data engineers and enterprise architects, the focus is on tools to connect and manage data across the organization for multiple use cases.
    
*   For the IT operations or DevOps team, the focus is on reusability, stable deployment, and maintainability.
    

With this wide diversity of outlooks, a unified data science platform that can accommodate different teams is a complex challenge, but only part of the story, as you’ll see throughout this chapter.

[![What Today’s Data Science Citizens Want](bilderklein/klein05_001.png)](img-f5.1.html) 

**Figure 5.1**    What Today’s Data Science Citizens Want

In this chapter, we’ll start our exploration of SAP Data Intelligence with a brief look at the typical data science project lifecycle in [Section 5.1](#05_001.html#h5.1) as well as how to manage your data science projects in [Section 5.2](#05_002.html#h5.2). Then, in [Section 5.3](#05_003.html#h5.3), we’ll turn to SAP Data Intelligence with a comparison between this platform and SAP Data Hub and, in [Section 5.3.2](#05_003.html#h5.3.2), a look at the architecture of SAP Data Intelligence. We’ll also provide a thorough look at the key capabilities of the platform, including its built-in operations, in [Section 5.4](#05_004.html#h5.4). The final section of this chapter returns to the SAP Data Hub, showing you how to migrate to SAP Data Intelligence in [Section 5.5](#05_005.html#h5.5).

## 5.1    Data Science Project Lifecycle

In general, a data science project is an iterative process that combines various steps until a methodology is fine-tuned to solve a specific business case. The process often includes the following activities:

*   Understanding the business case  
    The first and most important step for starting any data science project cycle, understanding the business case determines the success of the project. Tremendous computing power and vast collections of data are not worth the cost if your formulation of business problems is inaccurate. Creating a problem statement is a typical pain point that can often be resolved by applying data science instead of a regular enterprise solution. Asking the right question in this context is really the right recipe.
    
*   Collection of data  
    Once you formulate the right problem statement by applying the right recipe, the next step is to gather the key ingredients. This activity is all about gathering the relevant data and breaking down the problem statement into smaller units. For the correct data collection, the data science team comes into the picture, and your data scientists will need to know which ingredients are required, how to source and collect this data, and how to prepare the data to meet the desired outcome. A typical data science project includes identifying various data sources, which could be logs from webservers, social media data, data from online repositories like US Census datasets, data streamed from online sources via application programming interfaces (APIs) or web scraping, or even data in Excel files. Data acquisition involves acquiring data from all the identified internal and external sources that can help you answer the business question.
    
*   Grounding of data  
    Now that you’ve gathered the relevant data from the various data silos that exist in your landscape, we can now focus on data grounding, which is all about preparing your data for performing further analysis. This methodology helps you apply data science to determine whether the data that you’ve collected can even address your business problem. If the data you have is not good enough or not relevant enough, you’ll need to go back to the collection step of the project lifecycle. To realize the potential of your data, several methods are available to explore your data through data statistics, like means and medians. Some analysts plot the data and look at its distribution through visualizations like histograms, spectrum analyses, population distributions, etc. Based on this general understanding, the data can be further prepared for analysis, which involves several other steps, including:
    
    *   Identifying missing data
        
    *   Removing invalid data
        
    *   Removing duplicates
        
    *   Making data ready to feed into a data model
        
    
    Overall, 70%-90% of the time spent in a data science project goes into phases involving the collection, realization, and grounding of data, which are very critical for the success of any data science project.
    
*   Modeling of data  
    The hardest part of the lifecycle is already over since we’re done with data collection and grounding work. Now is the time for applying modeling, which is equivalent to tasting the curry you’re cooking after preparing the ingredients. At this point, you’ll need to determine whether the curry needs more seasoning, or is it ready to serve? The data modeling phase basically deals with training, validating, and testing the model. This entire phase is focused on the evaluation of the model in terms of accuracy and relevance. Accuracy refers to how well the model is performing, while relevance is more about how well the model answers to the context of your query. During this phase, diverse machine learning techniques are applied to the data to identify the best fit machine learning model, and competing models are trained with training datasets.
    
*   Deployment and iteration  
    We’re at the final step: Now, we’ll expose our selected model to the real world for human use. The more our deployed model runs, the more feedback is received. Capturing this feedback can be decisive for any data science project, and accurate feedback can help influence effective data model changes. As the final stage, deployment and iteration involves the retraining of your machine learning model in production whenever a change occurs in the data or the data source so that the performance of the machine learning model can remain high.
    

[![Typical Data Science Project Lifecycle](bilderklein/klein05_002.png)](img-f5.2.html) 

**Figure 5.2**    Typical Data Science Project Lifecycle

As shown in [Figure 5.2](#05_001.html#f5.2), the data science project lifecycle is a complex, cyclical process and thus needs good streamlining to result in practical business value. Failing to accurately execute any of these steps will result in misleading insights and models. Other reasons for failure include a lack of skills, poor scalability of models, and poor collaboration across teams because of the silos in which teams like data scientists and engineers usually work. Thus, you must adopt good machine learning operational practices to standardize and streamline the end-to-end lifecycle management of machine learning models in production. For these needs, MLOps comes into play, combining machine learning, DevOps, and data engineering skills to manage the full machine learning lifecycle and to apply best practices to deliver business value. In this next section, we’ll take a brief detour into MLOps and its applicability.

## 5.2    Managing the Data Science Project Lifecycle

MLOps is the logical retort to the current challenges that enterprises face when trying to put machine learning models into production.

[![MLOps](bilderklein/klein05_003.png)](img-f5.3.html) 

**Figure 5.3**    MLOps

In simple terms, as shown in [Figure 5.3](#05_002.html#f5.3), MLOps is the machine learning equivalent of DevOps. While DevOps optimizes the production lifecycles of big data projects, MLOps tries to solve problems associated with implementing machine learning in production. By its very nature, machine learning operationalization is a deeply collaborative process that requires collaboration between data scientists and the operations or production team to enhance automation, minimize waste, and ultimately harvest productive and consistent insights through machine learning.

According to an analysis called “Operationalizing Your Data Science and Machine Learning Initiatives” published by Gartner Analyst and Research Director Erick Brethenoux, while many companies develop machine learning models, only 47% of those models make it to production. Also, nearly 88% of AI initiatives in the corporate sector struggle to move past the test stage. Since machine learning involves numerous intricacies and complexities, standard DevOps processes aren’t enough to address these challenges. Thus arose the need for a more comprehensive solution for machine learning implementation—MLOps. To use MLOps, you’ll need a comprehensive data science platform that can enable MLOps and provide your data scientists all the support they need to carry out data and analytics tasks. These tasks encompass visualization, interactive exploration, deployment, performance engineering data preparation, and data access. But what is the incentive to adopt MLOps? According to the published Global AI survey by McKinsey & Company, companies applying core practices for using AI are experiencing much higher revenues as well as greater cost savings compared to other AI-adopting organizations. Automation through MLOps basically helps a company enable faster time-to-market and greatly reduces operational costs, allowing companies to be more agile and strategic in their decisions. Data science platforms that can put core MLOps methodologies into practice and that can enable the production of reproducible, traceable, and verifiable machine learning are gaining a lot of traction. A powerful tool, the SAP Data Intelligence platform ends the prolonged pursuit for an unified data science platform that can offer end-to-end solutions for developing, fine-tuning, deploying, and even tracking and versioning machine learning models. At the same time, SAP Data Intelligence enhances visibility over the resources used for easier reproducibility and easier performance monitoring of a model, and then retraining when appropriate. Now that you have a pretty good understanding of the foundational concepts, in upcoming sections, we’ll focus more on the features and capabilities available in SAP Data Intelligence.

## 5.3    SAP Data Intelligence

With the introduction of the SAP Data Intelligence platform, SAP addresses the end-to-end machine learning project lifecycle within a single data science platform where data scientists can explore, experiment, and build at maximum speed while also being able to share components of the work with colleagues and collaborate with them securely on certain tasks. AI generally requires a team effort, and coordination and cooperation will be needed between the business users who understand the needs of the organization and its customers, the data engineers that understand where the data is located and how the data is structured, the data science teams that understand how to extract value from that data, and the IT and DevOps teams that provide support. SAP Data Intelligence is a comprehensive AI platform that complements all these needs and can build intelligent enterprise solutions with its wide variety of features and services to accommodate multiple enterprise users and stakeholders, including data scientists, data engineers, developers, and administrators. [Figure 5.4](#05_003.html#f5.4) shows a snapshot encapsulating the overall features and capabilities of SAP Data Intelligence.

According to SAP’s official definition, SAP Data Intelligence is a comprehensive solution for delivering data-driven innovation and intelligence across an enterprise, unifying scalable enterprise AI and intelligent information management. SAP Data Intelligence leverages Docker and Kubernetes-based container technology and allows users to query large amounts of data (in distributed storages like Amazon S3, Azure Data Lake ADL, Azure Storage Blobs, HDFS, and Google Cloud Storage) and run highly scalable data flows and data-driven applications. The primary focus of the platform is intelligent data processing and making machine learning processes operational in production landscapes so you can make the most out of different data assets through seamless integration. Simultaneously, stakeholders like data scientists can continue using their tools of choice, while IT can focus on innovative prototyping and scaling their projects.

[![SAP Data Intelligence](bilderklein/klein05_004.png)](img-f5.4.html) 

**Figure 5.4**    SAP Data Intelligence

###### Note

A Kubernetes cluster is basically a collection of node machines for running containerized applications; running Kubernetes ultimately means running a cluster. At a minimum, a cluster comprises a control plane and one or more compute machines, or nodes, where the control plane solely manages the desired state of the cluster, for instance, which applications are running and which container images are used. More details can be found at [https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/](https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/).

### 5.3.1    SAP Data Intelligence Versus SAP Data Hub

In this context, as a platform, SAP Data Intelligence is the successor product to SAP Data Hub and SAP Leonardo Machine Learning Foundation, which have been combined into a single amalgamated data science platform. In this way, SAP Data Intelligence encompasses a wide spectrum of enterprise AI building features covering data discovery, refinement, orchestration, composition, monitoring, governance, and compliance all on a single platform. Basically, SAP Data Intelligence and SAP Data Hub are the same solution delivered in different ways: SAP Data Hub is offered as a service on SAP Cloud Platform whereas SAP Data Intelligence is offered as a BYOL (Bring Your Own License) product. With the BYOL licensing model, your enterprises can use their licenses flexibly (on-premise or in the cloud) unlike traditional restrictive software licensing policies where software is tied to a specific server (e.g., on-premise) and can’t be reused for deployments in the cloud without violating the licensing agreement. With true license mobility, businesses can migrate to and from services with ease—without having to worry about managing multiple licenses for the same product across multiple platforms and services.

### 5.3.2    Architecture

Our discussion so far established the basic concepts, but now is the time to take a step further and look at the components found in SAP Data Intelligence’s architecture, as shown in [Figure 5.5](#05_003.html#f5.5):

*   Connecting data sources  
    Connecting remote systems or data sources is supported by a robust set of connection types, including ABAP, SAP Cloud Platform Integration, Azure Data Lake, IBM DB2, Hadoop Distributed File System (HDFS), OData, IMPAP, Google Cloud Storage, and many others. SAP Data Intelligence connection management also lets you administer connections including the ability to create, update, delete, and monitor connections. With its predefined connectors for standard systems, SAP Data Intelligence allows you to access various data sources and manage those remote systems in a central place.
    
*   Metadata and governance  
    A set of SAP Data Intelligence capabilities to help govern and manage metadata assets that are spread across diverse systems and disparate sources. With the Metadata Explorer, enterprise users are empowered with set of tools and services to discover reliable datasets along with rule-driven data quality monitoring and self-service data preparation capabilities. Business users and analysts can leverage the data pipelining capability in an easy-to-use spreadsheet UI to enhance and enrich datasets to extract value out of data that may reside in different silos.
    
*   SAP Data Intelligence modeler  
    SAP Data Intelligence modeler, designed on the SAP Data Intelligence pipeline engine, helps you create data processing pipelines or graphs and provides a runtime and design-time environment for data-driven scenarios. The tool reuses existing code libraries to orchestrate data processing in distributed landscapes. The SAP Data Intelligence modeler, with its robust set of operators, can help users define graphs, including non-terminating, non-connected, or cyclic graphs. The SAP Data Intelligence launchpad offers access to the SAP Data Intelligence modeler so you can create your own data processing pipelines. The SAP Data Intelligence modeler can help you design and execute your data-driven use cases.
    
*   Intelligent processing   
    Intelligent processing components are all about the platform’s machine learning capabilities, which is founded on a combination of machine learning scenario manager, the machine learning data manager, AutoML, and open source tools. Out of these tools, the machine learning scenario manager is focused on organizing data science artifacts, managing related tasks through a single cockpit, and providing easy access to Jupyter Notebook. Named for a combination of programming languages—Julia (Ju), Python (Py), and R—Jupyter Notebook can add and deploy machine learning pipelines, while the machine learning data manager enables easy access to machine learning datasets whenever you need them. AutoML progressively automates the machine learning workflow so that your data scientists can benefit from the automation of tasks like data preparation, feature selection, model choice, model parameter optimization. In this way, manual effort and the likelihood of error can be reduced. Finally, since open source tools like Jupyter, R, Python, and Spark are popular among data scientists, the platform can be leveraged to enable data scientists to streamline their work and facilitate communication between teams via a flexible and highly interactive platform that supports multiple programming languages.
    
    [![SAP Data Intelligence: Components](bilderklein/klein05_005.png)](img-f5.5.html) 
    
    **Figure 5.5**    SAP Data Intelligence: Components
    
*   Data orchestration and monitoring  
    SAP Data Intelligence empowers enterprise users to discover, refine, govern, and orchestrate numerous types of data from various enterprise sources and ensure business transformation through managed interfaces, open source integration, cloud-based and on-premise deployments, and third-party interfaces. Out of the data orchestration and monitoring portfolio, machine learning tracking can take care of managing machine learning experiments while also preserving the results of machine learning experiments as performed by the data scientist team. Thus, machine learning tracking can be an essential unit in any machine learning project by ultimately helping data scientists track code, metadata, inputs, and outputs; easily reproduce results when needed; and finally determine which model should be promoted to production. One the other hand, the metrics explorer enables the visualization of machine learning runs, including comparison metrics between different runs belonging to one or more scenarios and the parameters captured as part of the experimentation and training phase either using the tracking SDK or the submit metric operator. In this context, runs are instances of a machine learning experiments, consisting of metrics and parameters from one iteration, along with the associated tags and labels.
    
*   Data pipelining  
    The core of the SAP Data Intelligence platform, data pipelining enables you to build modular data pipelines connecting disparate sources and apply a wide gamut of logical operators to dive more deeply into and extract insights out of enterprise data in ways never imagined before. You can execute data orchestration processes with modular data pipelines to scale up and down according to demand and deliver trustworthy data to the right users with the right context at the right time.
    
*   Bring Your Own License Model  
    SAP Data Intelligence is available with the Bring Your Own License (BYOL) model and can be deployed on-premise; in a public cloud (for instance, from Amazon, Google, or Microsoft); or in a private cloud running on Kubernetes compute clusters. From a release point of view, SAP Data Intelligence follows a frequent release cycle in an “as-a-service” version specifically for new machine learning-specific features.
    
*   SAP Data Intelligence  applications  
    SAP Data Intelligence applications encapsulate various tools and applications that are accessible through the SAP Data Intelligence launchpad and offers a comprehensive set of features to execute an end-to-end data science execution cycle. The main entry point to SAP Data Intelligence is the SAP Data Intelligence launchpad, which allows you to launch numerous SAP Data Intelligence applications including the following:
    
    *   SAP Data Intelligence connection management to configure connections to remote destinations
        
    *   SAP Data Intelligence database tools for accessing the SAP Vora database
        
    *   SAP Data Intelligence diagnostics for troubleshooting along with access to logs, traces, and metrics
        
    *   SAP Data Intelligence metadata explorer useful for browsing, profiling, crawling, and organizing the technical metadata of connected systems
        
    *   SAP Data Intelligence modeling, the modeling environment for data pipelines using SAP Data Intelligence pipeline engine
        
    *   SAP Data Intelligence monitoring for monitoring SAP Data Intelligence pipelines
        
    *   SAP Data Intelligence system management for managing the SAP Data Intelligence system
        
    
    A simple, browser-based, and easy-to-access launchpad enables you to connect all the necessary data sources in your landscape, extract the metadata from your connected sources, build a catalog of metadata, explore and search metadata in your catalog, perform machine learning experiments with tracking, and much more. Additionally, the launchpad can be personalized based on roles so that users can be assigned applications as favorites or be presented with applications displayed in groups.
    

Phew! This list is quite comprehensive, isn’t it? Overall, SAP Data Intelligence is the “umbrella” that encompasses the integration of all the solutions, data, and processes involved in SAP’s overall approach to big data.

### 5.3.3    Values of SAP Data Intelligence

Before dive more deeply into the individual features available with SAP Data Intelligence, let’s quickly go through a list of values offered by SAP Data Intelligence from an enterprise AI perspective, which includes the following:

*   Connecting data silos  
    SAP Data Intelligence is designed to connect and bring together the world of structured and unstructured data. SAP Data Intelligence’s unique integration with various enterprise data sources like SAP BW4/HANA and SAP Cloud Analytics can become a game-changer for your enterprise by helping you realize the potential value of your integrated data sources. Out of the box support for the widest range of connectors includes SAP HANA, SAP Vora, Object Stores (S3, GCS, etc.), HDFS servers, SAP Business Warehouse (SAP BW), Oracle, Microsoft Windows Azure Storage Blobs, SAP Cloud Platform Integration, Google Cloud BigQuery, SAP IQ databases, and many more.
    
*   Scaling AI across the enterprise  
    By moving AI projects from the proof of concept (POC) stage to production and creating an AI assembly line to better manage the data science, machine learning, and AI processes, bringing together IT team members and data scientists is now a reality with SAP Data Intelligence.
    
*   Extracting value from distributed data  
    Crossing every system blockage, even for data spread across a complex landscape, you can orchestrate and process this data using the most suited engine for each variation of data, thus minimizing the amount of data being moved while also connecting data that may be held in data silos.
    
*   Embracing open source technologies  
    SAP Data Intelligence is laid on a foundation of open source and data science principles and lets you monetize your enterprise data using open sources technologies including Docker containers; orchestration by Kubernetes; and native support for SAP, open source, and third-party machine learning frameworks, such as TensorFlow, R, Python, Spark, etc.
    
*   Scenario-driven model building  
    A unique approach that uses the concepts of machine learning scenarios to unite several artifacts belonging together into a virtual container—scenario and holds machine learning experiment data, documentations, experimental runs, model key performance indicators (KPIs) and API deployments in one place.
    
*   Ensuring MLOps   
    A unified platform enabling MLOps facilitates processes for operationalizing data science and machine learning solutions using code and best practices that promote efficiency, speed, and robustness while establishing seamless collaboration between data scientists, data engineers, and cloud engineers and building upon iterative feedback by stakeholders.
    
*   Leveraging the experimental phase  
    Harness the usage of Jupyter Notebook in data-driven applications by benefitting from the seamless integration of the JupyterLab environment and the Pipeline Modeler application.
    
*   Managing everything at once  
    A single interface to view and orchestrate all data-driven applications and data flows across the organization with tools to help manage governance, auditability, and transparency.
    

## 5.4    Key Capabilities

Now that you have an idea of the overall features available with SAP Data Intelligence, you should see its value as a complete data science platform. In this section, we’ll focus on the specific capabilities offered by SAP Data Intelligence and look at how key data science-oriented capabilities can empower you to bring enterprise intelligence into action.

### 5.4.1    Metadata and Governance

A deep understanding of metadata and its efficient use is key towards building intelligent enterprise solutions, and SAP Data Intelligence eases the process of metadata exploration and processing. Your metadata assets originate from the related source systems and can be made available in a catalog called the SAP Data Intelligence Metadata Explorer, which includes functionalities for labeling data, searching data, and tracking data lineages. Using the Metadata Explorer, you can gather information about the various aspects of your data including locations, attributes, qualities, and the sensitivity of the data, which ultimately can help you make informed decisions about publishing datasets, including accessibility. A self-learning metadata and governance tactic can take care of metadata consistency, accuracy, and completeness by applying unified metadata cataloging and also provides better visibility of data assets across the landscape along with pervasive data consumption and improved user experiences. The metadata management functionalities enable you to discover, understand, and consume information about your data with the ability to synchronize, share, and perform version lineages and impact analysis. In these ways, you can get answers to related information requests without browsing through multiple systems or repositories or touching various data models. [Figure 5.6](#05_004.html#f5.6) shows a snapshot of the SAP Data Intelligence Metadata Explorer, which is equipped with the following capabilities:

*   Features to connect to different enterprise data sources. You can also automatically crawl through the metadata structures and create references on your data to store them in the Metadata Catalog.
    
*   Along with a set of services, the Metadata Explorer includes browse, fact sheet, preview, profile, publish, rules, and data preparation functions for sources like IBM DB2, Oracle MySQL, Oracle, MS SQL Server, and MS Azure Cloud SQL.
    
*   Rule-based data quality management to better understand the quality of data and improve data through data preparation and modeling. This kind of parameterized, dynamic rule lets you define data quality thresholds and monitor incoming data using scorecards driven by key data quality KPIs. Also, data quality rules can be easily reused: Simply bind these rules to new data coming from various other sources.
    
*   Self-service and data-driven data preparation is another key feature offered as part of data governance and is primarily targeted for business users willing to transform, shape, harmonize, curate, and enrich the datasets based on different business scenarios and project requirements, sometimes with a single click.
    
*   A sophisticated business glossary and catalog editor to define terms and associate these terms with related Metadata Explorer objects, which allows you to search for terms and view their relationships.
    
*   Ability to handle large-scale enterprise deployments with holistic lifecycle management, elasticity, low total cost of ownership (TCO), and resilience.
    

[![SAP Data Intelligence: Metadata Explorer](bilderklein/klein05_006.png)](img-f5.6.html) 

**Figure 5.6**    SAP Data Intelligence: Metadata Explorer

### 5.4.2    Machine Learning Scenario Manager

After tailoring and making the dataset ready for the business scenario, now it’s time for data scientists to focus on the business problem they are trying to solve, and SAP Data Intelligence’s machine learning scenario manager is a central place to deal with versioning, connecting datasets, building models, deployments, monitoring model performance and lifecycle management, ultimately freeing up more time for the IT team and data scientists to focus on more productive work. Beside serving as a unified platform for modeling machine learning scenarios, SAP Data Intelligence also fulfills a key demand from data scientists seeking a computational notebook for practicing machine learning experiments, sharing code, and quick prototyping. The SAP Data Intelligence platform leverages Jupyter Notebook, which is a free, open source, interactive web-based computational notebook. Even though various computational notebooks have been around for several years, Jupyter has exploded in popularity recently, enthusiastically adopted by the data science community, and is now the default environment for research.

As a unified workspace, the machine learning scenario manager is capable of dealing with all machine learning models across the organization including the management of datasets, notebooks, and pipelines in a single interface. According to SAP’s official definition, a machine learning scenario is a collection of design-time elements, such as pipelines and notebooks in Jupyter Notebook, and runtime elements such as training runs, models, and model deployments.

Built around the key concepts of machine learning, the machine learning scenario manager, as shown in [Figure 5.7](#05_004.html#f5.7), lets you deal with data science artifacts and manage related tasks with the following features:

*   The machine language scenario manager in SAP Data Intelligence can serve as a central place to access the necessary tools and services for data scientists and machine learning experts to play with data and execute machine learning experiments.
    
*   A single cockpit, covering a wide range of data science capabilities including dataset binding, performing experiments in Jupyter Notebook, and automating model training and deployment via templated pipelines, ultimately allowing for seamless transitions from prototyping phases into production.
    
*   The multifaceted machine learning scenario manager unites various artifacts into a virtual container that is built on a foundational concept—the machine learning scenario, which ultimately holds all experiment data, scenario versions, model performance metrics, deployment history documentations, experimental runs, model KPIs, and API deployments in a single place. A machine learning scenario is the ultimate the entry point for kickstarting machine learning projects using the SAP Data Intelligence platform.
    
*   Embedded inside machine learning scenario manager, a modeler tool based on the SAP Data Intelligence pipeline engine uses a flow-driven programming paradigm. Thus, users can freehand model data processing pipelines as computation graphs to achieve the required data ingestion and transformation capabilities. Inside a computation graph, nodes represent operations on the data and edges represent data flows.
    
*   A pipeline represents a concrete and complex data flow and helps transform data between elements connected in a series. Executing a data pipeline can help process raw data from multiple sources and make this data available for different use cases.
    

[![SAP Data Intelligence: Machine Learning Scenario Manager](bilderklein/klein05_007.png)](img-f5.7.html) 

**Figure 5.7**    SAP Data Intelligence: Machine Learning Scenario Manager

### 5.4.3    Machine Learning Data Manager

Data scientists devote a substantial amount of effort and time preparing the datasets they need to experiment with different machine learning scenarios. In the process of determining which class of models to use and what types of features to include, these experiments produce a number of different artifacts. Without a standardized way to manage the resulting artifacts, data scientists can find reproducing their analyses and comparing the results of their experiments difficult. Moreover, since each experiment cycle requires a considerable amount of time, the data science team will want to preserve the experiment’s result for future reference. The machine learning data manager in SAP Data Intelligence helps you store the necessary datasets into data workspaces and collections, so that they can be easily accessed whenever needed. According to the official definition, a data workspace groups together any number of data collections, which are logical groups of data consumed or produced by a notebook or a pipeline during the execution of a machine learning scenario. [Figure 5.8](#05_004.html#f5.8) shows a quick snapshot of machine learning data manager. The key features of machine learning data manager include the following capabilities:

*   A unique set of features lets you organize machine learning datasets into a folder-based hierarchy combining data workspaces and data collections, along with relevant metadata like features and lineage. These data collections can be easily consumed as part of an AutoML experiment or programmatically in a Jupyter Notebook.
    
*   As a unique framework, the machine learning data manager enhances the traceability and reproducibility of each pipeline correlated to machine learning use cases by organizing the relevant data into workspaces and data collections.
    
*   To preserve the outcome of different machine learning experiments, the machine learning data manager offers provisions for transforming your data into clean and well-structured datasets that can be written to another data collection within the workspace and supports relationship identification through hierarchy. Unique machine learning functionalities like feature modeling and splitting also allow the segregation of data into train, test, and validation datasets.
    
*   The machine learning data manager also supports lineage analysis, where you can trace your data from a dataset to its source easily. You can also navigate through various dependencies between objects, for instance, whether the data has been transformed or where the data originated and how the dataset may have been modified throughout.
    

[![SAP Data Intelligence: Machine Learning Data Manager](bilderklein/klein05_008.png)](img-f5.8.html) 

**Figure 5.8**    SAP Data Intelligence: Machine Learning Data Manager

Now that you know how to manage your machine learning experiment datasets, let’s now focus on one of the most interesting and offbeat features offered by SAP Data Intelligence, called AutoML. Every day, this feature is becoming more and more popular, even among data scientists.

### 5.4.4    AutoML

For enterprises to infuse intelligence into their business process, AutoML is a critical step to lowering the barriers of entry into data science and to opening the way for data-driven automation at scale. In recent years, interest in adopting AutoML tools to automate several tasks in the data science workflow has spiked. In contrast to the typical automated machine learning features found in various tools, as shown in [Figure 5.9](#05_004.html#f5.9), AutoML categorically automates various tasks in the machine learning workflow, including acquiring and preparing data; engineering features from the data; picking the best algorithms; fine-tuning algorithms; and deploying and monitoring production models. With a typical machine learning application, development involves many steps, such as data preparation, feature selection, model choice, and model parameter optimization, but with AutoML, all these steps are automated intelligently, which reduces the manual effort required of users and the risk of error. If you don’t want to govern or control data science experiments that you typically perform with the machine learning scenario manager, you can easily opt for AutoML to generate machine learning pipelines automatically.

[![AutoML Compared to a Traditional Machine Learning Workflow](bilderklein/klein05_009.png)](img-f5.9.html) 

**Figure 5.9**    AutoML Compared to a Traditional Machine Learning Workflow

The comprehensive features offered by AutoML include the following:

*   AutoML acts on your training and test datasets, target outcome, and budget and automatically performs the necessary preprocessing steps including feature selection, feature engineering, and normalization. Next, AutoML starts the iterative training of a variety of machine learning models and optimizes their hyperparameters. The outcome is a machine learning pipeline that you can subsequently deploy.
    
*   AutoML is a graphical environment for data scientists and business and line of business (LOB) users that is fully equipped with tools for executing experiments based on datasets and for gaining access to unseen insights through machine learning models.
    
*   The AutoML cockpit is a central place for viewing information about autogenerated artifacts, including a model overview, execution status, a metric graph, detailed analysis of the generated model, and deployment information. You can navigate into and out of the cockpit even while the system is generating models.
    
*   Multiple sections of the AutoML cockpit can bring together various aspects of programmed experiments and model executions. The summary section displays the data used in the experiment, the experiment’s task, target metrics, and the budget, and the leaderboard sorts existing models by the target metric on the specified test dataset. The overview section focuses on deployment.
    

[Figure 5.10](#05_004.html#f5.10) shows a quick snapshot of AutoML on SAP Data Intelligence. After discussing AutoML features, let’s now move other important topics in machine learning experiment management tracking, which are specifically designed for data scientists to save their attempts as they look for the best possible model. In this context, we previously covered this topic when we discussed saving datasets prepared by data scientists. Now, we’ll talk about how we can preserve our machine learning experiments executed for further reference.

[![SAP Data Intelligence: AutoML](bilderklein/klein05_010.png)](img-f5.10.html) 

**Figure 5.10**    SAP Data Intelligence: AutoML

### 5.4.5    Machine Learning Tracking

Why is machine learning experiment tracking vital? Data science processes are generally research-centric work; often, multiple parallel experiments are performed, many of which might not ever make it into production. While working on a machine learning project, getting good results from a single model training run is rare that keeping all your machine learning experiments organized can be a real challenge. Having a process that lets you draw valid conclusions out of various experiments is quite vital, which is where machine learning experiment management becomes a key factor in delivering successful outcomes. Day-to-day effort with machine learning models repeatedly boils down to a sequence of experiments before picking a modeling approach, which combines network topology, training data, and various optimizations or tweaks to the models. Also, enterprise users, like machine learning engineers and data scientists, tend to work alone, which gives the false illusion that keeping track of the experimentation process is not important so long as a final model is delivered. Problems arise when you need to go back to an earlier idea, re-run a model that you may have experimented with only months ago, or simply compare and visualize the differences between runs. With these cases, the need for a system or tool for tracking machine learning experiments is (painfully) apparent. Machine learning tracking allows data scientist teams to see what others are doing; share ideas and insights; and store experiment metadata, which can be retrieved and analyzed at any time. Teamwork can be much more efficient, situations where several people work on the same task can be prevented, and the onboarding of new members can be made much more smooth.

The tracking service on the SAP Data Intelligence platform offers a complete framework for data scientists to configure, capture, organize, reproduce, and visualize machine learning experiments. With provisions for capturing multiple aspects of tracking, data scientists can stipulate what information must be captured as part of the experiment (e.g., model parameters, model metrics, model hyperparameters, etc.) and can later view this information through the Metric Explorer within the machine learning scenario manager. Machine learning tracking on the SAP Data Intelligence platform is primarily driven by the tracking SDK, and the required modules, methods, and scripts can be incorporated into experiments in Jupyter Notebook. But before we discuss experiment tracking in more detail, you must first understand some key entities related to tracking, as shown in [Figure 5.11](#05_004.html#f5.11), which we’ll describe next.

[![Model TracModel trackingentitiesking Entities](bilderklein/klein05_011.png)](img-f5.11.html) 

**Figure 5.11**    Model Tracking Entities

Let’s review the key entities you’ll need understand to track your machine learning models, such as the following:

*   Run  
    A run is an instance of a machine learning experiment. Each run consists of metrics and parameters from one iteration of the machine learning experiment, along with the associated tags and labels. Metrics are used to measure the performance of your machine learning models. Different metrics are used to evaluate different machine learning models. For example, log loss or average accuracy could be used to evaluate a classification task, whereas mean absolute error or root mean square error (RMSE) could be used to evaluate a model that provides a numeric output.
    
*   Run collection   
    A run collection allows you to logically group a number of runs. You can generate run collections by using the tracking functionality of the SAP Data Intelligence Python SDK. When you log runs using the tracking functionality, you can specify a name for your run collection. If you don’t specify a name, the system creates a default run collection for each source (that is, notebook or pipeline). The name of the default run collection is the same as that of the source. These default run collections are shown in the metrics explorer with the suffix (Default).
    
*   Visual board   
    The visual board is the central place for comparing different runs sourced from one or more run collections and is generated using runs that are called source runs. Data from source runs is shown in tabular format under the Data tab of the visual board.
    
*   Canvas and charts   
    The canvas is the part of the visual board that lets you add charts to compare source runs graphically. For example, to plot a metric against a run ID, parameter, or timestamp, you can create charts from the metrics and parameters of source runs and compare this information visually using the canvas.
    

[Figure 5.12](#05_004.html#f5.12) shows a glimpse of SAP Data Intelligence’s monitoring capabilities. Now that you have a pretty good understanding of the measurement units behind machine learning tracking, let’s learn how you can implement the machine learning tracking capability.

[![SAP Data IntelligenceSAP Data Intelligencemonitoring: Monitoring](bilderklein/klein05_012.png)](img-f5.12.html) 

**Figure 5.12**    SAP Data Intelligence: Monitoring

Getting started with experiment tracking using Jupyter Notebook is simple. The following code snippet will automatically include all the necessary modules required for experiment tracking:

```
from sapdi import tracking 
```

After the module-importing statement, you’ll use the following code snippets to mark the beginning and the end of the run:

```
tracking.start_run(run_collection_name='runcollect1')
tracking.end_run()
```

In this case, start\_run() initializes the tracking run under the provided run collection called 'runcollect1' of type string, which basically allows you to group together different runs of your experiment. Furthermore, when the run is initialized via start\_run(), the metadata information, such as the Scenario Details, Source Details, Start Time, etc., is automatically recorded.

To log the execution-related metrics, generate list of metrics, or log execution-related parameters, respectively, you can use the following methods:

*   log\_metric
    
*   log\_metrics
    
*   log\_parameters
    

The following code snippet shows you comprehensively how to embed machine learning tracking scripts inside a pipeline:

```
from sapdi import tracking
run = tracking.start_run()
# tracking.start_run(run_collection_name='rc1') 
# Use this to group different runs under a collection
params = {
'input_size': 784,
'hidden_size': 500,
'num_classes': 10,
'num_epochs': 2,
'batch_size': 100,
'learning_rate': 0.001,
'model_file': 'model.ckpt'
}
tracking.log_parameters(params)
# the experimental code.
for i in range(params.get('num_epochs')):
tracking.log_metric(name='metric_name', value=1)
# more code
tracking.set_tags({
"tag_key": "tag_value",
"tag_key_n": "tag_value_n"
})
tracking.set_labels({
"accuracy": {
"format_string": "percentage"
}})
# more code
tracking.end_run()
```

Now that we’ve covered machine learning tracking, in the next section, we’ll introduce you to the SAP Data Intelligence modeler and explore its operator-driven capabilities for building graphs for your business processes.

### 5.4.6    SAP Data Intelligence Modeler and Built-in Operators

Designed on the SAP Data Intelligence pipeline engine, the SAP Data Intelligence modeler delivers a flow-based programming paradigm for data scientists to create data processing pipelines modeled as computation graphs and executed in a containerized environment that runs on Kubernetes. The modeler application helps you model graphs using a graphical interface and achieve the required data ingestion and transformation capabilities. The modeler comes with 250+ built-in operators that can be directly used to build graphs for your business processes or can be used as the basis for a custom operator to design powerful data pipelines. Using the modeler, you can easily design your data processing pipelines using existing graphs or the available operators. As shown in [Figure 5.13](#05_004.html#f5.13), on the left side of the application, you can access all the objects you’ll need to interact with to create your pipelines, while the main screen stores the pipelines and allows you to execute and debrief the results.

Inside the modeler, as shown in [Figure 5.14](#05_004.html#f5.14), a pipeline or graph is a network of operators connected to each other using typed input ports and output ports for exchanging data. In this context, an operator is a reactive component representing a vertex of a graph and reacts only to events or messages delivered to the operator through its input ports.

[![SAP Data Intelligence Modeler](bilderklein/klein05_013.png)](img-f5.13.html) 

**Figure 5.13**    SAP Data Intelligence Modeler

[![SAP Data IntelligenceSAP Data Intelligencegraphs: Graphs](bilderklein/klein05_014.png)](img-f5.14.html) 

**Figure 5.14**    SAP Data Intelligence: Graphs

Since the operator is totally unaware of graph in which it is defined and unfamiliar with the source and target of its incoming and outgoing connections, the operator can only interact with the environment through its output ports. [Figure 5.15](#05_004.html#f5.15) shows a sample operator with its input ports and output ports. Each port is associated with a port type, and the tool uses color coding to identify compatible port types.

[![Operators](bilderklein/klein05_015.png)](img-f5.15.html) 

**Figure 5.15**    Operators

An operator is associated with a port of any data type, such as string, blob, int64, float64, byte, message stream, and so on. Operators require a certain runtime environment for their execution, and the SAP Data Intelligence Data modeler provides predefined environments for operators. These environments are made available to users as a library of Docker files. When you execute a pipeline (a graph), the tool translates each operator in the graph into a process. The modeler then searches the Docker files for an environment suitable for the operator’s execution and instantiates a Docker image of that environment. This Docker image and the operator process are executed on a Kubernetes cluster. Predefined operators within the SAP Data Intelligence modeler can be classified into various categories, which we’ll describe next.

#### Converter

A handful of converters are grouped under this category, as shown in [Figure 5.16](#05_004.html#f5.16), and these operators support the different types of conversions often required to transform your business data in various ways, for instance, StreamToString, StringToStream, ToBlob, ToStringType, ToSrting, ToNumber, and ToMessage.

[![Converters](bilderklein/klein05_016.png)](img-f5.16.html) 

**Figure 5.16**    Converters

#### Data Quality

This key set of operators, as shown in [Figure 5.17](#05_004.html#f5.17), is focused on managing data quality, including masking data, cleansing data, gaining statistical insights, applying data validation rules, and more.

[![Data Quality OperatorsOperatordata quality](bilderklein/klein05_017.png)](img-f5.17.html) 

**Figure 5.17**    Data Quality Operators

#### Data Workflows

These are dedicated operators for transforming and transferring data; managing workflows including merging, splitting, and triggering workflows: improving data quality using jobs in SAP Data Services; and sending notifications at certain points in the workflow.

#### Files

As shown in [Figure 5.18](#05_004.html#f5.18), file management is easy with this set of file handling operators, including the ability to monitor, read, write, remove, and list files.

[![Files Operators](bilderklein/klein05_018.png)](img-f5.18.html) 

**Figure 5.18**    Files Operators

#### Hadoop and Spark

[Figure 5.19](#05_004.html#f5.19) shows a set of dedicated operators for managing Hadoop jobs, especially for submitting jobs to Hadoop and clusters using the Apache Livy API, a Representational State Transfer (REST) API provided by different cloud providers. Apache Livy is a service that enables easy interaction with a Spark cluster over a REST interface. With Apache Livy, you can easily submit Spark jobs or snippets of Spark code and retrieve results synchronously or asynchronously. In this set, you can also access Spark Context management, all via a simple REST interface or a remote procedure call (RPC) client library.

[![Hadoop and Spark Operators](bilderklein/klein05_019.png)](img-f5.19.html) 

**Figure 5.19**    Hadoop and Spark Operators

#### Machine Learning Predictive Analytics

Since predictive analytics is a common key requirement across various machine learning scenarios, this operator, shown in [Figure 5.20](#05_004.html#f5.20), lets you apply the PA Automated Analytics product, which predicts values based on an existing pretrained models.

[![Predictive Analytics Operator](bilderklein/klein05_020.png)](img-f5.20.html) 

**Figure 5.20**    Predictive Analytics Operator

#### Multiplexer

A multiplexer is a simple operator for mapping the input of any port to all of its output ports. Additional input and output ports can be added as needed. [Figure 5.21](#05_004.html#f5.21) shows a quick snapshot of multiplexers.

[![Multiplexers](bilderklein/klein05_021.png)](img-f5.21.html) 

**Figure 5.21**    Multiplexers

#### Processing

This unique set of operators handles common requirements within graphs, like command execution; constant generation; random data generation at certain intervals; inclusion of Go, JavaScript, Python, and R code snippets; and more. [Figure 5.22](#05_004.html#f5.22) shows a quick snapshot of processing-related operators.

[![Processing Operators](bilderklein/klein05_022.png)](img-f5.22.html) 

**Figure 5.22**    Processing Operators

#### SAP Integration

As shown in [Figure 5.23](#05_004.html#f5.23), this set of operators are focused on data integration, taking care of the sending, receiving, and formatting of data to/from SAP Analytics Cloud and SAP Cloud Platform Integration.

[![SAP Integration Operators](bilderklein/klein05_023.png)](img-f5.23.html) 

**Figure 5.23**    SAP Integration Operators

#### Machine Learning Core Operators

These dedicated operators are only for creating machine learning pipelines and supporting capabilities, such as model training and serving, and integrates with the scenario management features of the platform. [Figure 5.24](#05_004.html#f5.24) shows a quick snapshot of processing-related operators.

[![Machine Learning Core Operators](bilderklein/klein05_024.png)](img-f5.24.html) 

**Figure 5.24**    Machine Learning Core Operators

We’d like to focus on a particular core operator called functional services. With SAP Leonardo Machine Learning Foundation now being dissolved into SAP Data Intelligence, Functional Services are longer available separately and instead is included as an operator as part of the pipeline modeler, as shown in [Figure 5.25](#05_004.html#f5.25). Currently, the Functional Services operator offers a rather limited set of pretrained image and text processing-oriented functions, including image classification, feature extraction, OCR, similarity scoring, text classifier, and topic detection.

[![Functional Services Operators](bilderklein/klein05_025.png)](img-f5.25.html) 

**Figure 5.25**    Functional Services Operators

#### SAP Vora

As shown in [Figure 5.26](#05_004.html#f5.26), these dedicated operators handle SAP Vora database-related operations, including the reading, ingestion, and loading of data and includes a message decoder.

[![SAP Vora Operators](bilderklein/klein05_026.png)](img-f5.26.html) 

**Figure 5.26**    SAP Vora Operators

#### Structured Data Operators

These operators, shown in [Figure 5.27](#05_004.html#f5.27), handle structured data coming from various data sources like Azure SQL DB, DB2, Google BigQuery SQL, Microsoft SQL Server, MySQL, Oracle, Redshift, and SAP IQ databases.

[![Structured Data Operators](bilderklein/klein05_027.png)](img-f5.27.html) 

**Figure 5.27**    Structured Data Operators

#### Connectivity

This set of operators primarily takes care of connectivity through HTTP requests and providing WAMP record access and includes the ability to consume or send records from Kafka clusters. You can also send emails; replicate tables; configure MQTT-based connectivity; configure connections Microsoft Azure, Google Cloud Platform, or Amazon Web Services (AWS); and more, as shown in [Figure 5.28](#05_004.html#f5.28).

[![Connectivity Operators](bilderklein/klein05_028.png)](img-f5.28.html) 

**Figure 5.28**    Connectivity Operators

#### Tables

This set of operators, shown in [Figure 5.29](#05_004.html#f5.29), handles the generation of table messages based on a user-defined schema, the generation of random data, and the decoding of tabular data.

[![Tables Operators](bilderklein/klein05_029.png)](img-f5.29.html) 

**Figure 5.29**    Tables Operators

#### Text Analysis

This unique set of operators, shown in [Figure 5.30](#05_004.html#f5.30), handles natural language processing (NLP) for unstructured textual data by using the text analysis capabilities of SAP Vora.

[![Text Analysis Operators](bilderklein/klein05_030.png)](img-f5.30.html) 

**Figure 5.30**    Text Analysis Operators

#### Utilities

As shown in [Figure 5.31](#05_004.html#f5.31), these operators deal with the conversion, aggregation, defining scripts, serializing Python data, application logging, and compiling flowgraphs along with many more helpful operators.

[![Utility Operators](bilderklein/klein05_031.png)](img-f5.31.html) 

**Figure 5.31**    Utility Operators

[Figure 5.32](#05_004.html#f5.32) shows the overall category of operators supported by the SAP Data Intelligence platform.

[![Categories of Operators](bilderklein/klein05_032.png)](img-f5.32.html) 

**Figure 5.32**    Categories of Operators

## 5.5    Migrating to SAP Data Intelligence from SAP Data Hub

With the release of SAP Data Intelligence 3.0 and the lack of new functionalities planned for release after SAP Data Hub 2.7, perhaps migrating to SAP Data Intelligence from SAP Data Hub may seem unnecessary. According to SAP, with the release of SAP Data Intelligence 3.0, SAP Data Hub customers will automatically receive SAP Data Intelligence, and no additional migration effort is needed. Existing customers will now have access to all cloud-based machine learning tools as part of support packages without any additional fee or migration effort required. You’ll still be at liberty to select the deployment model of your choice—whether on-premise, in the cloud, or a combination of the two. In addition to SAP Data Hub, SAP Leonardo Machine Learning Foundation has also been dissolved into the SAP Data Intelligence platform since that solution will no longer be available as a standalone service for new subscriptions and can only be consumed via SAP Data Intelligence. As described throughout this chapter, SAP Data Intelligence offers all the integration, orchestration, metadata management, connectivity, and other rich services of SAP Data Hub with the services of SAP Leonardo Machine Learning in the cloud, along with a lot more new features.

In case you still don’t have access to an SAP Data Intelligence tenant and are really eager to get your hands dirty, you can start immediately by signing up for an on-premise trial edition of SAP Data Intelligence 3.0, which is available for Google Cloud Platform, Amazon Web Services (AWS), and Microsoft Azure, through the SAP Cloud Appliance Library, as shown in [Figure 5.33](#05_005.html#f5.33).

[![SAP Data Intelligence Trial Edition 3.0](bilderklein/klein05_033.png)](img-f5.33.html) 

**Figure 5.33**    SAP Data Intelligence Trial Edition 3.0

## 5.6    Summary

Finally, we’ve concluded our chapter on SAP Data Intelligence, SAP’s data science platform that offers a coherent machine learning and data science foundation that can lead your business processes to evolve into an intelligent enterprise. The name SAP Data Intelligence highlights the solution’s focus on intelligent data processing and the operationalization of machine learning processes in enterprise landscapes. This combination allows you to get the most out of your disparate data assets, which can be easily integrated, intelligently refined, and seamlessly used in your business processes. Data scientists can continue to work with the tools they know and love while IT focuses on prototyping machine learning models to put into production and ensures that innovation and machine learning projects can scale and be properly managed. Accelerating the efficient delivery of your intelligent data with innovative data pipelines can enable smart customer experiences. Knowing your data and improving user experiences with metadata management strategies can improve data visibility and enable pervasive data consumption, thus bringing people, processes, and technologies together to drive enterprise-level AI and more importantly gain business insight. A key point of SAP Data Intelligence is providing you with the freedom to choose the deployment model of your choice—whether on-premise, in the cloud, or a combination of the two.

# Part II

Building Machine Learning Applications

# 6    SAP HANA Predictive Analysis Library

 and R IntegrationIn this chapter, we’ll dive deeply into the technical aspects the SAP HANA Predictive Analysis Library (SAP HANA PAL) and SAP HANA with R integration. Both SAP HANA PAL and R provide various functions for machine learning and statistical analysis scenarios. This chapter first outlines the installation and prerequisites for SAP HANA PAL and R integration, then discusses in detail how SAP HANA PAL procedures and R functions can be used from native SAP HANA across different machine learning aspects like modeling, prediction, training, validation, and model comparison. This chapter supplements these concepts with several sample codes for a better understanding.

Predictive analysis requires specialized programs to run machine learning algorithms. These programs are optimized for numerical stability and performance. As you’ve seen in [Chapter 4](#04_001.html#h4), a number different components in SAP HANA provide specialized operations for machine learning and statistical analysis. In this chapter, we’ll focus on two widely used components provided by SAP—the SAP HANA Predictive Analysis Library (SAP HANA PAL) in [Section 6.1](#06_001.html#h6.1) and SAP HANA with R integration in [Section 6.2](#06_002.html#h6.2)—and discuss in detail how to use these solutions in practice.

## 6.1    SAP HANA Predictive Analysis Library

The SAP HANA Predictive Analysis Library (SAP HANA PAL) provides various machine learning algorithms in the form of SAP HANA PAL procedures. These procedures can be called from SQLScript procedures to build machine learning models in SAP HANA. The underlying SAP HANA PAL functions can also be executed from flowgraphs in the Application Function Modeler (AFM) tool. SAP HANA PAL is mainly designed for data scientists and machine learning experts and provides flexibility for fine-tuning models to make them suitable for specific scenarios. We introduced you to SAP HANA PAL in [Chapter 4](#04_001.html#h4), [Section 4.1.1](#04_001.html#h4.1.1). In this chapter, we’ll dive more deeply into SAP HANA PAL to see how SAP HANA PAL procedures are used.

### 6.1.1    Prerequisites and Installation

SAP HANA PAL is part of the Application Function Library (AFL). To utilize SAP HANA PAL, AFL must be installed in SAP HANA, and the script server must be enabled in your SAP HANA instance.

###### Note

*   Refer to the SAP Note 1898497 to check for compatibility between the AFL revision number and the SAP HANA revision number.
    
*   Refer to the SAP HANA Server Installation and Upgrade Guide specific to the installed SAP HANA version/revision for installing AFL ([http://s-prs.co/501402](http://s-prs.co/501402)).
    
*   Refer to SAP Note 1650957 for enabling the Script Server.
    

After installing AFL, you can check three views to verify whether SAP HANA PAL procedures have been successfully installed with the following commands:

*   sys.afl\_areas
    
*   sys.afl\_packages
    
*   sys.afl\_functions
    

Use the following SQL code to check these views:

```
SELECT * FROM "SYS"."AFL_AREAS" WHERE AREA_NAME = 'AFLPAL';
SELECT * FROM "SYS"."AFL_PACKAGES" WHERE AREA_NAME = 'AFLPAL';
SELECT * FROM "SYS"."AFL_FUNCTIONS" WHERE AREA_NAME = 'AFLPAL'; 
```

You can also check the SAP HANA PAL procedures installed in the \_SYS\_AFL schema by filtering for procedure names including “PAL\_”, as shown in [Figure 6.1](#06_001.html#f6.1).

[![SAP HANA PAL Procedures in the \_SYS\_AFL Schema](bilderklein/klein06_001.png)](img-f6.1.html) 

**Figure 6.1**    SAP HANA PAL Procedures in the \_SYS\_AFL Schema

The following roles are required to execute SAP HANA PAL procedures:

*   AFL\_\_SYS\_AFL\_AFLPAL\_EXECUTE
    
*   AFL\_\_SYS\_AFL\_AFLPAL\_EXECUTE\_WITH\_GRANT\_OPTION
    

Prior to SAP HANA 2.0 SPS 02, you would need the role AFLPM\_CREATOR\_ERASER\_EXECUTE to create and drop wrapper SAP HANA PAL procedures.

### 6.1.2    SAP HANA PAL Procedures

SAP HANA has delivered a comprehensive set of efficient machine learning algorithms through SAP HANA PAL procedures. Prior to SAP HANA 2.0 SPS 02, SAP HANA PAL functions were used for the same purpose. These procedures/functions are the building blocks for implementing native machine learning solutions on the SAP HANA platform using SAP HANA PAL. Each SAP HANA PAL procedure or function focuses on a specific task of a machine learning algorithm.

[Chapter 3](#03_001.html#h3) provides a complete list of supported machine learning algorithms, associated SAP HANA PAL procedures in SAP HANA 2.0 SPS 04, and SAP HANA PAL functions. Note that the category “Statistics” does not mean these algorithms are the only statistical analysis algorithms supported by SAP HANA PAL. These algorithms provide useful statistics for model validation and testing, all grouped under the category “Statistics.” However, many other statistical analysis algorithms are also supported by SAP HANA PAL. In fact, machine learning uses many statistical analysis methods in areas like regression analysis, classification, time series analysis, survival analysis, and data preprocessing; these methods were developed long before machine learning evolved as a subject.

Before we dive more deeply into SAP HANA PAL procedures, let’s recall from [Chapter 3](#03_001.html#h3) the main steps involved in a typical machine learning project and understand where SAP HANA PAL procedures can be used. As shown in [Figure 6.2](#06_001.html#f6.2), except for the steps described in [Chapter 3](#03_001.html#h3) that deal with the business understanding and process-specific activities like deployment and operationalization, SAP HANA PAL procedures can be used in all major steps in a machine learning project.

[![Major Steps in a Machine Learning Project Where SAP HANA PAL Procedures Can Be Used](bilderklein/klein06_002.png)](img-f6.2.html) 

**Figure 6.2**    Major Steps in a Machine Learning Project Where SAP HANA PAL Procedures Can Be Used

Different SAP HANA PAL procedures have been delivered for different machine learning algorithms and different tasks across lifecycle phases. However, some SAP HANA PAL procedures can be used at different phases possibly with different sets of parameters, and some SAP HANA PAL procedures are applicable for only one phase. [Figure 6.3](#06_001.html#f6.3) shows an example of SAP HANA PAL procedures across lifecycle phases. Note that the PAL\_KNN and PAL\_DOUBLE\_EXPSMOOTH procedures can be used for both model building and prediction. However, the PAL\_DECISION\_TREE procedure can be used only for modeling, and the PAL\_DECISION\_TREE\_PREDICT procedure can be used only for prediction. These limitations are mainly due to the inherent nature of the underlying algorithms. In some cases, the way procedures evolved and designed also played a role in their ultimate evolution.

[![Different SAP HANA PAL Functions across Lifecycle Steps](bilderklein/klein06_003.png)](img-f6.3.html) 

**Figure 6.3**    Different SAP HANA PAL Functions across Lifecycle Steps

Now, let’s look more closely at procedures. If we open a procedure in SAP HANA, you’ll see a single line of code that passes parameters to a function. That function in turn executes the machine learning algorithm logic. The code shown in [Listing 6.1](#06_001.html#l6.1) is from the KNN\_CV procedure, which calls the function KNN\_CV\_ANY.

```
CREATE PROCEDURE "_SYS_AFL"."PAL_KNN_CV" ( IN p1 table(...), IN p2 table(...), OUT p3 table(...), OUT p4 table(...) ) LANGUAGE AFLLANG SQL SECURITY INVOKER READS SQL DATA AS BEGIN AFLLANGVERSION='2'; SCHEMA='_SYS_AFL'; AREA='AFLPAL'; FUNCTION='KNN_CV_ANY'; PARAMETERS='TREX_TABLE_ANY--;"TABLE",in,TrexTableAny,,,,; 
"TABLE",in,TrexTableAny,,,,;"TABLE",out,TrexTableAny,,,,;"TABLE",out, 
TrexTableAny,,,,;'; END
```

**Listing 6.1**    Code of the PAL\_KNN\_CV Procedure

So, the core machine learning function acts like a black box, but it interacts through the input and output parameters of the procedure. These functions are like database procedures written in C++ to carry out complex data-intensive calculations. These functions are invoked from SAP HANA SQLScript-based SAP HANA PAL procedures. These SAP HANA PAL procedures act like wrapper procedures surrounding these machine learning functions.

Note that a few commonalities exist across SAP HANA PAL procedures, such as the following:

*   All are stored in the \_SYS\_AFL schema.
    
*   Their names start with PAL\_.
    
*   They are written in the AFLLANG language.
    
*   They have some input and output parameters of type TABLE.
    

Most importantly, the input and output parameters are not static, with predefined table signatures. Instead, input tables of different column structures can be passed through the same parameter as long as you follow certain broad restrictions.

With these initial observations, let’s now understand how these SAP HANA PAL procedures are designed. [Figure 6.4](#06_001.html#f6.4) shows a schematic representation of an SAP HANA PAL procedure.

[![Schematic Representation of an SAP HANA PAL ProcedureSAP HANA Predictive Analysis Libraryschematic](bilderklein/klein06_004.png)](img-f6.4.html) 

**Figure 6.4**    Schematic Representation of an SAP HANA PAL Procedure

Each SAP HANA PAL procedure runs a specific task in a machine learning algorithm, like modeling based on some algorithm, evaluating models, or predicting based on a predefined model. All these tasks are based on data, and this data must be supplied to the SAP HANA PAL procedure in input tables. Also, SAP HANA PAL procedures feature various settings and tuning options based on the specific parameters of the underlying algorithms, so these parameter values must also be provided as an input table. Therefore, in almost all SAP HANA PAL procedures, two input tables are required: the data table and the parameter table. Moreover, some procedures require additional input in the form of additional input tables. The results after running the algorithms are provided via output tables. An output table could contain model-specific information (e.g., a coefficient table); fitted data as per the model (e.g., a fitted table); or statistics for model goodness of fit (e.g., statistics table). The output table generation process varies based on:

*   The underlying machine learning algorithm.
    
*   The parameters specified in the parameter table.
    

Depending on the parameters specified, the algorithm may execute additional calculations and generate additional output tables.

#### Data Table

The data table provides the data to be analyzed through machine learning. Depending on the underlying algorithm, this table can have various structures. For regression or classification problems, we’re trying to predict the value of a dependent variable, say Y, based on a set of independent variables, say X[1], X[2], ... , X[n]. Also, to identify the records correctly, we may need an ID column. If this data pertains to a set of customers, then the customer ID may be an identifier for specific records. Thus, in this scenario, the associated algorithm expects data in the structure shown in [Table 6.1](#06_001.html#t6.1).

 
| Column Position || Columns || Column Significance |
| --- | --- | --- |
| 1 || ID || The ID column is mandatory for some procedures, like PAL\_KNN but not others; if omitted, that value must be specified through a parameter (e.g., parameter HAS\_ID in PAL\_LINEAR\_REGRESSION). |
| --- | --- | --- |
| 2 || Y || The dependent variable of the model. |
| 3 to n || X[1], X[2], ..., X[n] || The independent variables of the model. |

**Table 6.1**    Typical Data Table Structure for Regression- or Classification-Related SAP HANA PAL Procedures

However, for unsupervised learning algorithms, like clustering and association analysis, variables are not easily categorized as either a dependent or an independent variable. Instead, the analysis is performed based on features. Therefore, the associated algorithm expects data in the structure shown in [Table 6.2](#06_001.html#t6.2).

 
| Column Position || Columns || Column Significance |
| --- | --- | --- |
| 1 || ID || This column is the identifier of individual records; sometimes, referred to as Customer ID, Document ID, or Transaction ID. |
| --- | --- | --- |
| 2 ... n || F[1], F[2], ..., F[n] || These columns are the features based on which the clustering or association will be performed. For association analyses, algorithms like apriori, FP-growth, and KORD consider only one feature. Sequential pattern mining considers two features. |

**Table 6.2**    Typical Data Table Structure for Clustering- or Association Analysis-Related SAP HANA PAL Procedures

###### Note

Consider the following rules while preparing the data table:

*   You’ll need to determine whether the SAP HANA PAL procedure requires an ID column and, if so, what column to use.
    
*   Some SAP HANA PAL procedures cannot handle NULL or missing values. So, if the data contains NULL, either the associated records must be removed, or these missing values must be imputed.
    
*   Some SAP HANA PAL procedures require that categorical variables be binarized, either implicitly or explicitly. The following algorithms support implicit binarization through one-hot encoding. For others, your data will need to be prepared through binarization:
    
    *   Accelerated K-means
        
    *   DBSCAN
        
    *   Gaussian mixture model (GMM)
        
    *   Generalized linear models
        
    *   K-means
        
    *   K-medians
        
    *   K-medoids
        
    *   Multiple linear regression
        
    *   Logistic regression (with elastic net regularization)
        
    *   Multi-class logistic regression
        
    *   K-Nearest Neighbors (KNN)
        
    *   Multilayer perceptron
        
    *   Support Vector Machine (SVM)
        

#### Parameter Table

The machine learning algorithms in SAP HANA PAL support model specification and fine-tuning through parameters. These parameters vary depending on the underlying algorithms. Parameters may be mandatory or optional. The values of these parameters are provided through the parameter table. The parameters have specific names, and their values may be an integer (type INTEGER), a real number (type DOUBLE), or a character (type VARCHAR). The structure of our parameter table is listed in [Table 6.3](#06_001.html#t6.3).

 
| Column Name || Data Type || Comments |
| --- | --- | --- |
| PARAM\_NAME || VARCHAR || Parameter name. |
| --- | --- | --- |
| INT\_VALUE || INTEGER || Value of the integer type parameters; NULL otherwise. |
| DOUBLE\_VALUE || DOUBLE || Value of the double type parameters; NULL otherwise. |
| STRING\_VALUE || VARCHAR || Value of the string type parameters; NULL otherwise. |

**Table 6.3**    Structure of a Parameter Table

In most of the cases, each parameter requires a single value, but a few parameters may require more than one value be supplied.

For example, let’s consider the SAP HANA PAL procedure PAL\_CORRELATION\_FUNCTION. This procedure calculates the statistical correlation function between random variables, in the context of time series data. This procedure is also known as an autocorrelation function (ACF). The corresponding parameters of this procedure are listed in [Table 6.4](#06_001.html#t6.4).

 
| Parameter Name || Data Type || Possible Values || Default Value || Dependency |
| --- | --- | --- | --- | --- |
| THREAD\_RATIO || DOUBLE || The ratio of available threads to be used for calculation:

*   0: single thread
    
*   0 to 1: percentage of threads
    
*   Others: heuristically determined
    

 || –1 || Required only when a brute force method is used. |
| --- | --- | --- | --- | --- |
| USE\_LFT || INTEGER || Method to be used:

*   –1: Automatically determined
    
*   0: Brute force
    
*   1: Fast Fourier Transformation (FFT)
    

 || –1 ||  |
| MAX\_LAG || INTEGER || Maximum lag for the correlation function || Sqrt (no of records) ||  |
| CALCULATE\_PACF || INTEGER || Calculate PACF?

*   0: No
    
*   1: Yes
    

 || 1 || Only when one series is provided. |

**Table 6.4**    Parameters of PAL\_CORRELATION\_FUNCTION

Note that all these parameters are optional. If we don’t specify any parameters, the procedure will run with its default values, but you may not get the result you want. [Table 6.5](#06_001.html#t6.5) shows an example parameter table.

 
| PARAM\_NAME || INT\_VALUE || DOUBLE\_VALUE || STRING\_VALUE |
| --- | --- | --- | --- |
| USE\_LFT || 1 || NULL || NULL |
| --- | --- | --- | --- |
| MAX\_LAG || 5 || NULL || NULL |

**Table 6.5**    Example of a Parameter Table for PAL\_CORRELATION\_FUNCTION

In our example, we’re specifying that the fast fourier transformation (FFT) method should be used for calculation, and the maximum lag should be 5. Note that we didn’t specify the value of the CALCULATE\_PACF parameter in our case because by default its value is 1 (Yes), and we would like to calculate PACF in our example. Note also that we didn’t specify a value for the THREAD\_RATIO parameter because this parameter does not have any effect if the FFT method is used.

To avoid a conflict among the table names when multiple users call SAP HANA PAL procedures simultaneously, we recommended you create the parameter table as a local temporary column table called from the SQL Editor, so that each parameter table has its own scope per session.

#### Output Table

Output tables are generated by SAP HANA PAL procedures to store the result of the execution of a machine learning algorithm. SAP HANA PAL procedures determine the output table structure without explicit definition, based on the specific rules that apply to the various scenarios:

*   Some output tables have a fixed number of columns, predefined column names, and preassigned data types. All these defaults are predefined by SAP HANA PAL.
    
*   In some cases, the column name and data type in the output table are inherited from the input data table (e.g., the ID column).
    
*   In some cases, the entire input table structure is inherited in the output table.
    
*   Sometimes, the column name is inherited from the input data table with additional suffixes.
    
*   Sometimes, the column type is widened to the DOUBLE type in the output for a similar column in the input data of the INTEGER type.
    

SAP HANA PAL procedures provide some flexibility with output tables. They require only matching data types of output columns of the output tables. You can pass tables with different column names but matching data types as output tables to SAP HANA PAL procedures.

###### Note

Refer to the SAP HANA Predictive Analysis Library (SAP HANA PAL) documentation for complete information on the following topics:

*   Available SAP HANA PAL procedures and underlying machine learning algorithms
    
*   Required input and output tables for each procedure and their structures
    
*   List of different parameters associated with each procedure, their usage, and their default values
    

Specific prerequisites exist for each SAP HANA PAL procedure, like NULL handling, category variable handling, and ID fields.

### 6.1.3    Calling SAP HANA PAL Procedures

SAP HANA PAL procedures can be called in multiple ways in SAP HANA: from the SQL Editor, from an SQLScript procedure, or from a flowgraph using the AFM tool. The first option is used mainly during model exploration and for checking results. Once a model is finalized, the model can be implemented through a procedure or flowgraph. This section discusses these different options with sample data and code to enhance your understanding. All the codes used in this section are available in text format at this book's website ([www.sap-press.com/5014](http://www.sap-press.com/5014)).

Throughout this section, we used the schema ML\_DATA as the default schema and the table LM\_INPUT\_DATA from this schema as the data table. A glimpse of the data is shown in [Figure 6.5](#06_001.html#f6.5).

The data has an ID column, an identifier for each observation record. Y is a dependent variable and X1, X2, X3, and X4 are independent variables. All these fields except X4 [] are numeric, and X4 is a categorical variable (i.e., a factor; it has values “Yes” or “No”). In our scenario, we want to determine whether any relationships exist between Y and the other variables X1, X2, X3, and X4. We’ll start by investigating a linear relationship and then try to fit a multiple linear regression model to the data. The associated SAP HANA PAL procedure is \_SYS\_AFL.PAL\_LINEAR\_REGRESSION.

[![Part of the LM\_INPUT\_DATA Data Table Used in This Section](bilderklein/klein06_005.png)](img-f6.5.html) 

**Figure 6.5**    Part of the LM\_INPUT\_DATA Data Table Used in This Section

Also, we’ll use table LM\_PARAM, shown in [Figure 6.6](#06_001.html#f6.6), as the parameter table for this example.

[![Table LM\_PARAM: The Parameter Table Used in This Section](bilderklein/klein06_006.png)](img-f6.6.html) 

**Figure 6.6**    Table LM\_PARAM: The Parameter Table Used in This Section

The SAP HANA PAL procedure requires two input tables: the data table and the parameter table. The output is provided through the following five tables:

*   The coefficient table provides the regression model coefficients.
    
*   The predictive modeling markup language (PMML) table provides the model in PMML format.
    
*   The fitted table is a table with the fitted values of dependent variable (in our case, Y).
    
*   The statistics table provides model goodness-of-fit statistics.
    
*   The optimal parameter table contains the optimal parameter values when specific modeling options and when parameter selection is used. This table, for example, would store the optimal values of model parameters λ and α in an elastic net regression model.
    
*   Once the model is finalized, you can use the model to predict the values of a dependent variable from observations made on independent variables. We’ll use table LM\_NEW\_DATA in the ML\_DATA schema as our new data table. [Figure 6.7](#06_001.html#f6.7) shows the associated data.
    

[![New Data to Be Used for Prediction Purposes](bilderklein/klein06_007.png)](img-f6.7.html) 

**Figure 6.7**    New Data to Be Used for Prediction Purposes

Note that this data table lacks a column for the dependent variable Y. After all, the value of this variable is what must be predicted.

Let’s now explore the different ways we can run this analysis. The basic idea behind all these different ways is the same: Simply call the SAP HANA PAL procedure with your input tables and get the output tables. Differences only arise in their implementations.

#### Calling from the SQL Editor

As you explore different models, you don’t always need to store the output. You may not even know if the explored model is the optimal model. In this scenario, you can call an SAP HANA PAL procedure from the SQL Editor. Use the code shown in [Figure 6.8](#06_001.html#f6.8) to run a procedure.

[![Sample Code for Running the SAP HANA PAL Procedure from the SQL Editor](bilderklein/klein06_008.png)](img-f6.8.html) 

**Figure 6.8**    Sample Code for Running the SAP HANA PAL Procedure from the SQL Editor

###### Note

*   In this example, we used a local temporary column table as the parameter table. In other words, not even the parameters need to be stored permanently, in a database table.
    
*   The names of temporary tables start with a hashmark (#).
    
*   Since output tables are not specified, the output will be displayed on the screen. In our example, we used a question mark (?) in place of the output parameters.
    
*   The output will show the five tables on the screen; however, the PMML table and the optimal parameter table will display no data since we did not specify any suitable parameter in the parameter table to generate the associated output.
    

[Figure 6.9](#06_001.html#f6.9) shows the output tables associated with the analysis when run from the SAP Web IDE.

[![Output Screen after Running the SAP HANA PAL Procedure from the SQL Editor](bilderklein/klein06_009.png)](img-f6.9.html) 

**Figure 6.9**    Output Screen after Running the SAP HANA PAL Procedure from the SQL Editor

These tables are displayed on screen and are not permanently stored. Under the Result1 tab is the coefficient table, showing the coefficients of the independent variables and the intercept term, with associated t-statistics and p-values for their significance. If a p-value is less the 0.05, the influence of the corresponding variable is assumed to be significant, as described in [Chapter 2](#02_001.html#h2). The model can be interpreted in the following way:

Y = 5.082344440950587 + 3.3682703601715 \* X1 + 6.901170525876566 \* X2 – 1.9324716286467696 \* X3 + 2.949255249095389 \* (1 if X4 = ’Yes’; 0 if X4 = ’No’).

The Result3 and Result4 tabs show the fitted values and statistics tables, as shown in [Figure 6.10](#06_001.html#f6.10) and [Figure 6.11](#06_001.html#f6.11).

[![Output Table with Fitted Value of Y Based on the Regression Equation](bilderklein/klein06_010.png)](img-f6.10.html) 

**Figure 6.10**    Output Table with Fitted Value of Y Based on the Regression Equation

[![Output Table with Statistics on Model Fitting](bilderklein/klein06_011.png)](img-f6.11.html) 

**Figure 6.11**    Output Table with Statistics on Model Fitting

Note that the adjusted R² value is close to 1. Thus, this model fits the data particularly well. But this model still might not be the best model!

As mentioned earlier, the PMML table and optimal parameter tables lack data since we didn’t instruct the SAP HANA PAL procedure to generate them through the parameter table. So, don’t get confused if you see some empty tables; this scenario may not always be due to an error. The output of PMML table is shown in [Figure 6.12](#06_001.html#f6.12).

[![Empty PMML Table](bilderklein/klein06_012.png)](img-f6.12.html) 

**Figure 6.12**    Empty PMML Table

Note the additional table under the Result6 tab, as shown in [Figure 6.13](#06_001.html#f6.13), which displays the values of the output parameters (of the SAP HANA PAL procedure) in the SAP Web IDE.

Now, to run the procedure with a specific parameter table and store the result of the output in database tables, use the code shown in [Figure 6.14](#06_001.html#f6.14) to call the SAP HANA PAL procedure.

The first time you run this code, comment out the DROP TABLE statements, or you will get errors. (Tables that haven’t been created cannot be dropped.) Then, when you run this code, you’ll create the database tables for containing the output (without any data) and specify these tables in the output parameters of SAP HANA PAL procedure.

[![Extra Table in the SAP Web IDE Showing Values of Output Parameters of the Procedure](bilderklein/klein06_013.png)](img-f6.13.html) 

**Figure 6.13**    Extra Table in the SAP Web IDE Showing Values of Output Parameters of the Procedure

[![Code to Call SAP HANA PAL Procedure from the SQL Editor with Saving the Output Tables in the Database](bilderklein/klein06_014.png)](img-f6.14.html) 

**Figure 6.14**    Code to Call SAP HANA PAL Procedure from the SQL Editor with Saving the Output Tables in the Database

In our example, we used the database table ML\_\_DATA.LM\_PARAM as the parameter table, instead of putting these values into a local temporary column table. The code shown in [Listing 6.2](#06_001.html#l6.2) can be used to generate this database table.

```
SET SCHEMA ML_DATA;
CREATE COLUMN TABLE LM_PARAM("PARAM_NAME" VARCHAR(256), "INT_VALUE" INTEGER, 
"DOUBLE_VALUE" DOUBLE,"STRING_VALUE" VARCHAR(1000));
    INSERT INTO "LM_PARAM" VALUES ('STAT_INF',1,NULL,NULL);
    INSERT INTO "LM_PARAM" VALUES ('ADJUSTED_R2',1,NULL,NULL);
    INSERT INTO "LM_PARAM" VALUES ('BP_TEST',1,NULL,NULL);
    INSERT INTO "LM_PARAM" VALUES ('KS_TEST',1,NULL,NULL);
```

**Listing 6.2**    Code for Creating the Parameter Table

The data in the five output tables will be exactly the same as before, but this time, this data will be stored in the database tables specified by the table names in the output parameters of the procedure call. You will not see the data on the screen. To view the contents of these database tables, either use the popup menu or use a SELECT statement. The only output you’ll see on the screen is the mapping between the output parameters and the associated tables, as shown in [Figure 6.15](#06_001.html#f6.15), which is similar to the table under the Result6 tab in the previous case.

[![Screen Output Showing Output Parameters and Associated Tables](bilderklein/klein06_015.png)](img-f6.15.html) 

**Figure 6.15**    Screen Output Showing Output Parameters and Associated Tables

###### Tip

Don’t get confused with usage of the word “parameter” in different contexts. In general, parameters help define or characterize a system. We used the term “parameter” in this section in two different contexts (hence different underlying systems). A “parameter table” specifies the characteristics of an underlying machine learning function, while “the parameter of a procedure” specifies the input/output of a procedure. The context of the sentence should indicate which sense of “parameter” we’re using.

#### Calling from SQLScript Procedures

Once a machine learning model is finalized, you should store the associated code somewhere to run it in future. If the model is deployed in production, you cannot run the associated code from the SQL Editor. Thus, SAP has provided the option of calling an SAP HANA PAL procedure from an SQLScript procedure, commonly known as a stored procedure. A stored procedure can be transported to other systems and can be scheduled to run, if required.

The code shown in [Figure 6.16](#06_001.html#f6.16) is an example of how to use an SQLScript procedure to call an SAP HANA PAL procedure.

[![Sample Code for Calling the SAP HANA PAL Procedure from an SQLScript Procedure](bilderklein/klein06_016.png)](img-f6.16.html) 

**Figure 6.16**    Sample Code for Calling the SAP HANA PAL Procedure from an SQLScript Procedure

###### Note

The code creates a procedure called PROC\_REGRESSION MODEL in the ML\_DATA schema. This procedure calls the SAP HANA PAL procedure. The input data table and parameter table are already available and are passed to the SAP HANA PAL procedure as table variables. Input tables cannot be passed directly to an SAP HANA PAL procedure in a nested call.

The output table parameters passed to the SAP HANA PAL procedure become table variables inside the procedure. These table variables are then used to store data into output tables. The output tables are already created with the specified structure. You can reuse part of the code shown earlier in [Figure 6.14](#06_001.html#f6.14), the part that creates the output tables.

Before storing the data into these output tables, the output tables are truncated to delete any data from earlier runs of the code.

A colon (:) is used before a name to indicate that it is a variable.

In our example, we did not specify the Security clause in the procedure definition. You may put “Definer” or “Invoker” in the procedure definition based on your security requirements.

Once defined, you can run the SAP HANA PAL procedure with the following statement:

```
Call ML_DATA.PROC_REGRESSION_MODEL();
```

This statement will run the procedure, and the output will be stored in the specified tables. This time, no additional table, like the table shown earlier in [Figure 6.15](#06_001.html#f6.15), is created. As expected, the five output tables will contain exactly the same data when run from the SQL Editor.

Now, once you’ve finalized the model, you can use the model to make predictions. However, SAP HANA PAL provides a separate procedure (\_SYS\_AFL.PAL\_LINEAR\_REGRESSION\_PREDICT) for predictions using linear regression models, which involve a different structure for the data table and for the parameter table. We’ll use the table shown earlier in [Figure 6.7](#06_001.html#f6.7) as the data table but use table LM\_PARAM\_PREDICTION, shown in [Figure 6.17](#06_001.html#f6.17), as the parameter table.

[![Parameter Table for Prediction](bilderklein/klein06_017.png)](img-f6.17.html) 

**Figure 6.17**    Parameter Table for Prediction

This SAP HANA PAL procedure requires another input table: the coefficient table, with only the variable name. Coefficient values are obtained from the finalized model. Our prediction will be based on the fitted model, and the coefficients from the final model captures this information.

The procedure shown in [Figure 6.18](#06_001.html#f6.18) can be used to run the prediction.

[![Procedure for Prediction Based on Selected Regression Model](bilderklein/klein06_018.png)](img-f6.18.html) 

**Figure 6.18**    Procedure for Prediction Based on Selected Regression Model

###### Note

*   The input parameters for coefficients are selected from the coefficient table of the final model.
    
*   The output table contains the ID column and the predicted values of the variable Y.
    
*   The parameter table we used in our case is specific to this procedure; do not confuse it with the earlier parameter table we used for modeling.
    

[Figure 6.19](#06_001.html#f6.19) shows the data in the output table LM\_PREDICTED\_VAL.

[![Predicted Values of Y Using the New Dataset](bilderklein/klein06_019.png)](img-f6.19.html) 

**Figure 6.19**    Predicted Values of Y Using the New Dataset

#### Calling SAP HANA PAL Functions Using Flowgraphs

The various SAP HANA PAL functions for different machine learning algorithms can be called from flowgraphs in the AFM tool. Flowgraphs allow you to create a data flow network with individual nodes for specific tasks, linked together to form the entire flow. A specific machine learning function can be added as a node in a flowgraph from the Predicted Analysis Library component of the Palette. The signatures of the input tables, signatures of the output tables, and the parameter values for the SAP HANA PAL function can be specified through the properties of their respective anchors on the node. The input and output tables can be specified through the Data Source and Data Sink (Template Table) nodes of the Palette, respectively. The link between the input tables to the SAP HANA PAL function and the link between the SAP HANA PAL function to the output tables can be achieved by holding the connect button of the respective source node and dragging and dropping the vector onto the target node. Once the flowgraph is saved and activated, you can execute the flowgraph by clicking the Execute button and choosing one of the following three options: Execute in SQL Editor, Open in SQL Editor, or Execute and Explore. The SAP HANA PAL function will be executed with the input data and will provide the output in the specified data sink template tables.

### 6.1.4    Model Evaluation

Machine learning models are evaluated primarily based on two approaches: checking the goodness-of-fit statistics and validating the fitted model using a validation dataset (if training is applicable). This second approach is known as model validation, which we discussed in detail in [Chapter 3](#03_001.html#h3). In this section, we’ll focus on how you can implement model validation concepts in SAP HANA PAL.

Some machine learning algorithms use tuning or penalty parameters during the model fitting process, and different values for these parameters result in different models. For example, in a ridge regression algorithm and a lasso algorithm, different values for the penalty parameter (λ) produces different models. Thus, selecting the optimal value of this penalty parameter is important, and the process of determining this optimal value is known as optimal parameter selection.

SAP HANA PAL supports model validation and optimal parameter selection for the following SAP HANA PAL procedures:

*   PAL\_FRM
    
*   PAL\_ALS
    
*   PAL\_LINEAR\_REGRESSION
    
*   PAL\_POLYNOMIAL\_REGRESSION
    
*   PAL\_LOGISTIC\_REGRESSION
    
*   PAL\_MULTILAYER\_PERCEPTRON
    
*   PAL\_NAIVE\_BAYES
    
*   PAL\_DECISION\_TREE
    
*   PAL\_SVM
    
*   PAL\_KNN\_CV
    

###### Important Note

Model validation using training and validation datasets is applicable for supervised learning, where the model can be trained based on historical data. However, for unsupervised learning, machine learning algorithms identify patterns from the data, and no concept of training exists. Thus, the concepts involving validation datasets discussed in this section are only applicable for supervised learning algorithms. Furthermore, within supervised learning, no notion of training exists in the k-nearest neighbors algorithm, and thus, for this algorithm, SAP HANA PAL includes a separate procedure for validation: the PAL\_KNN\_CV procedure.

#### Model Validation

SAP HANA PAL provides various model fitting statistics based on the parameters selected. These statistics can be used to validate the fitted model. SAP HANA PAL also supports k-fold cross validation and the Bootstrap method for creating the training and validation datasets from the original data table. For classification problems (where the response variable, i.e., the dependent variable is categorical), SAP HANA PAL provides a stratified version of these methods, and data is sampled proportionately from each category. This option is specified by the mandatory parameter RESAMPLING\_METHOD in the parameter table. [Table 6.6](#06_001.html#t6.6) shows the parameters associated with the resampling technique.

 
| Parameter Name || Data Type || Values || Default Value || Comment |
| --- | --- | --- | --- | --- |
| RESAMPLING\_METHOD || NVARCHAR || 

```
cv
```

```
stratified_cv
```

```
bootstrap
```

```
stratified_bootstrap
```

 || None || Mandatory parameter.The value cv implies k-fold sampling. Both cv and bootstrap have stratified versions. |
| --- | --- | --- | --- | --- |
| EVALUATION\_METRIC || NVARCHAR || 

```
ACCURACY
```

```
ERROR_RATE
```

```
F1_SCORE
```

```
RMSE
```

```
MAE
```

```
AUC
```

```
NLL
```

 || None || Mandatory parameter. The values are the different measures based on which validation is performed. |
| FOLD\_NUM || INTEGER || Number of folds (k) for a k-fold cross-validation. || None || Optional parameter. |
| REPEAT\_TIMES || INTEGER || Number of times validations to be carried out. || 1 || Optional parameter. |

**Table 6.6**    Parameters for Model Validation

When validation parameters are specified, SAP HANA PAL provides additional statistics in the statistics table to represent the model’s goodness of fit based on the validation dataset. In the next section, we’ll provide an example covering both optimal parameter selection and validation.

#### Optimal Parameter Selection

For selecting the optimal value of the tuning or penalty parameters, SAP HANA PAL procedures run the model fitting with a set of different values of these parameters. These different values may come from a grid (i.e., a predefined set of values) or chosen randomly within a range. Different models thus fitted with different values of the parameter are then compared with respect to some metrics like accuracy, error rate, root mean squared error (RMSE), and AUC on the validation dataset, and the parameter values associated with the optimal model is reported.

###### Important Note

The optimal parameter selection for supervised learning models works on the validation dataset. Different models usually tend to fit well with the training dataset, so their performance can be judged properly with validation data that is not used for training. Depending on the performance of different model tuning parameters on validation data, the best tuning or penalty parameters are selected. You’ll still need to run validation for the optimal parameter selection.

Like model validation, the optimal parameter selection is specified through parameters in the parameter table. The parameters listed in [Table 6.7](#06_001.html#t6.7) are available for this purpose.

 
| Parameter Name || Data Type || Values || Default Value || Comment |
| --- | --- | --- | --- | --- |
| PARAM\_SEARCH\_STRATEGY || NVARCHAR || 

*   grid
    
*   random
    

Specifies how the parameter values will be selected. || None || Optional parameter. |
| --- | --- | --- | --- | --- |
| RANDOM\_SEARCH\_TIMES || INTEGER || Number of times parameter values to be selected randomly. || None || Optional parameter, but mandatory and valid when parameter values are selected randomly. |
| SEED || INTEGER || Specifies the seed for random number selection. || 0 || Optional parameter. Used when parameter values are selected randomly. |

**Table 6.7**    Parameters for Optimal Parameter Selection

Note that the parameter EVALUATION\_METRIC is also used for optimal parameter selection. The measure specified in this parameter is used to find the optimal tuning parameter.

Some other parameters, applicable for both validation and parameter selection, are listed in [Table 6.8](#06_001.html#t6.8).

 
| Parameter Name || Data Type || Values || Default Value || Comment |
| --- | --- | --- | --- | --- |
| THREAD\_RATIO || DOUBLE || 0 || A value between 0 and 1. (0 means single thread.) || Ratio of available threads to be used by this function. |
| --- | --- | --- | --- | --- |
| TIMEOUT || INTEGER || 0 || Specifies maximum running time in seconds. || No timeout when 0 is specified. |
| PROGRESS\_INDICATOR\_ID || NVARCHAR || None ||  || Sets an ID for progress indicators for monitoring progress. |

**Table 6.8**    Parameters for Validation and Parameter Selection

When parameters for optimal parameter selection are specified, SAP HANA PAL procedures find the optimal values of different model tuning or penalty parameters and report these values in the optimal parameter output table.

#### Implementing Model Validation and Optimal Parameter Selection

Now, let’s see how we can implement the data validation and optimal parameter selection in SAP HANA PAL. As mentioned earlier, you’ll simply include the required parameters in the parameter table. Continuing with the example we started in [Section 6.1.3](#06_001.html#h6.1.3), we’ll need to create a new parameter table or update an existing parameter table with new entries. For our example, we’ll create a new parameter table called LM\_PARAM\_SELECTION, as shown in [Figure 6.20](#06_001.html#f6.20).

[![SQL Code for Parameter Table Creation](bilderklein/klein06_020.png)](img-f6.20.html) 

**Figure 6.20**    SQL Code for Parameter Table Creation

The table LM\_PARAM\_SELECTION, shown in [Figure 6.21](#06_001.html#f6.21), displays the relevant records.

[![Parameter Table LM\_PARAM\_SELECTION](bilderklein/klein06_021.png)](img-f6.21.html) 

**Figure 6.21**    Parameter Table LM\_PARAM\_SELECTION

###### Note

*   We used ALG = 6 to specify the elastic net regression model. This model uses the penalty parameters λ (lambda) and α (alpha), whose values must be selected optimally (row 1).
    
*   We specified a set of values for λ and α in the 4th and 5th rows. The optimal parameter selection will run on these values and pick up the optimal values for λ and α. Therefore, we selected the grid method for the parameter search strategy (row 9).
    
*   We also have specified 2-fold cross validation (row 7) and that we want the validation cycle to run twice (row 8).
    
*   Root mean squared error (RMSE) statistics will be used as validation statistics to choose the optimal parameters (row 10).
    
*   The parameters in rows 1 through 5 are related to model building. Rows 6 through 8 are for validation; row 9, for optimal parameter selection; row 10, for both validation and optimal parameter selection; and row 11, for other parameters.
    

Once the new parameter table is created, you can run the same SAP HANA PAL procedure shown earlier in [Figure 6.16](#06_001.html#f6.16) with this new parameter table. The only change is line 10, which should contain the following code:

```
TV_PARAM = SELECT * FROM LM_PARAM_SELECTION;
```

This new code will run the validation and parameter selection process and provide the associated outputs in the statistics and optimal parameter tables, as shown in [Figure 6.22](#06_001.html#f6.22) and [Figure 6.23](#06_001.html#f6.23).

###### Note

*   Rows 1 through 7 provide information on validation.
    
*   We repeated the validation cycle twice (REPEAT\_TIME = 2 in the parameter table); thus, the output shows the results of two cycles (TEST\_1 and TEST\_2).
    
*   In each cycle, we ran 2-fold cross-validation (FOLD\_NUM = 2 in the parameter table), so the data is divided into two sets (set1 and set2). First, the model is trained on set1 and then validated against set2. Then, the model is trained on set2 and validated against set1. The RMSE values on each validation set (set2 and set1) are reported in the same row separated by comma (in rows 2 and 3).
    

[![Statistics Table Showing Results of Model Validation](bilderklein/klein06_022.png)](img-f6.22.html) 

**Figure 6.22**    Statistics Table Showing Results of Model Validation

[![Optimal Parameter Table Showing the Result of Parameter Selection](bilderklein/klein06_023.png)](img-f6.23.html) 

**Figure 6.23**    Optimal Parameter Table Showing the Result of Parameter Selection

Note that, in the parameter table, we specified two sets of parameter values for the penalty parameters λ and α (through the parameters ENET\_LAMBDA\_VALUES and ENET\_ALPHA\_VALUES, respectively). The optimal values of λ and α from these sets of values are reported in the optimal parameter table.

How are the initial values specified in the parameter table? That is an art that only comes with experience!

###### Note

The examples we’ve discussed so far concern one type of machine learning algorithm. In the real world, you may need to compare results between different types of machine learning algorithms, for instance, between a logistic regression algorithm and an SVM. This evaluation is performed by comparing the validation statistics of the different algorithms.

SAP HANA PAL provides the following three procedures to help you compare different types of regression models:

*   PAL\_MODEL\_COMPARISON\_REGRESSION
    
*   PAL\_MODEL\_COMPARISON\_REGRESSION\_WITH\_PARTITION\_TABLE
    
*   PAL\_MODEL\_COMPARISON\_REGRESSION\_WITH\_TESTING\_TABLE
    

Essentially, these procedures run different regression models (as specified by the user) on training and validation data; append the individual output tables of each model (for fitted values, training statistics, and validation statistics); and create the MODEL\_ID field to identify the different models used. You could perform all these tasks more slowly by running multiple model validation procedures on the same training and validation data with different regression models and appending the individual output tables of different models. However, with these three procedures, you’ll only need to code a little SQL.

## 6.2    R Integration

We introduced you to the concepts behind SAP HANA with R integration in [Chapter 4](#04_001.html#h4). In this section, we’ll dive more deeply into this integration from a technical perspective and show you how to use this integration to build your own machine learning applications.

### 6.2.1    Prerequisites and Installation

For SAP HANA with R integration, the R environment must be installed on a Linux system, preferably on SLES Linux. For specific details on installing the R environment, refer to the SAP HANA R Integration Guide from SAP available at [https://developers.sap.com/tutorials/mlb-hxe-setup-r.html#](https://developers.sap.com/tutorials/mlb-hxe-setup-r.html#). The following high-level steps would be carried out for SAP HANA, express edition, and R integration:

1.  Create a dedicated user in the SAP HANA server to host all your R activities.
    
2.  Install the C compiler and the following packages based on the SAP HANA revision:
    
    *   xorg-x11-devel
        
    *   readline-devel
        
    *   libcurl-devel
        
    *   gcc-fortran
        
    *   gcc-c++
        
    *   xz-devel
        
    *   pcre-devel
        
    *   texinfo
        
    *   cairo-devel
        
3.  Verify the Java installation; 64-bit Java Runtime Environment (JRE) 8 or higher is required for the integration.
    
4.  Install the Texinfo package available from [http://ftp.gnu.org/gnu/texinfo/](http://ftp.gnu.org/gnu/texinfo/) to get all the tools required to compile R.
    
5.  Install R.
    
6.  Install and configure Rserve.
    
7.  Configure SAP HANA for R integration.
    
8.  Setup Rserve authentication.
    
9.  Set up SSL/TLS from SAP HANA to Rserve.
    
10.  Test the configuration.
     

###### Tip

The SAP HANA R Integration Guide claims that SAP HANA and R should be located on separate hosts. This recommendation is most likely from a best practice perspective. However, technically, we have installed SAP HANA, express edition, and R on the same host, and the integration between the SAP HANA tenant database and R works perfectly fine.

### 6.2.2    R Packages

R provides different functions for integration, data manipulation, statistical analysis, and graphics. These functions are grouped across multiple packages. Users can also create their own functions and contribute them through packages. Thousands of R packages are available for various purposes. The base installation of R comes with the around 30 packages; however, several other packages may be required for different types of analysis and graphics. These packages can be installed from CRAN. Some useful packages include the following:

*   Integration and data manipulation
    
    *   Rcpp: Seamless R and C++ integration
        
    *   sqldf: R package for running SQL statements on R data frames
        
    *   XML: Tools for parsing and generating XML within R and S-Plus
        
    *   plyr: Tools for splitting, applying and combining data
        
    *   tidyr: Tools for converting data into tidy format
        
*   Statistical analysis
    
    *   gbm: Generalized boosted regression models
        
    *   randomForest: Random forests for classification and regression
        
    *   glmnet: Lasso and elastic-net regularized generalized linear models
        
    *   caret: Classification and regression training
        
    *   zoo: S3 infrastructure for regular and irregular time series (Z’s Ordered Observations)
        
*   High-quality graphics
    
    *   ggplot2: Elegant data visualizations using the grammar of graphics
        
    *   colorspace: Toolbox for manipulating and assessing colors and palettes
        
    *   manipulate: Interactive plots for RStudio
        

You can see the complete list of R packages at the following link:

[https://cran.r-project.org/web/packages/available\_packages\_by\_name.html](https://cran.r-project.org/web/packages/available_packages_by_name.html)

Numerous packages exist for different functionalities. You may install R packages from CRAN or from GitHub. During installation, the dependent R packages are also installed and often involve multilevel dependencies. Once installed, you can use the R code library(<package name>) to use the functions within the package.

### 6.2.3    Calling R Functions from SAP HANA

The R functions can be called from SAP HANA using a stored procedure with the RLANG language. Specific R codes to be executed are written within this procedure. You can call this procedure from the SQL Editor or call it from a wrapper stored procedure written in SQLScript. Additionally, R functions can be called from flowgraphs using AFM tools. This section discusses the different available options with sample data and code for better understanding. All the codes used in this section are available in text format at this book's website ([www.sap-press.com/5014](http://www.sap-press.com/5014)).

Throughout this section, we’ll use table LM\_INPUT\_DATA as the historical data for modeling and table LM\_NEW\_DATA as the new data for prediction, which are the same tables used in [Section 6.1.3](#06_001.html#h6.1.3); refer especially to [Figure 6.5](#06_001.html#f6.5) and [Figure 6.7](#06_001.html#f6.7) for a glimpse of the data in these tables. However, for this example, we’ve made two minor changes:

*   We’ll use the schema R\_DATA for all the tables to avoid any confusion.
    
*   Traditionally, codes and data components in R are written in lowercase letters, so we’ll put the column headings of these data tables in lowercase.
    

We’ll run the same multiple linear regression analysis with this data. However, this time, we’ll create a stored procedure in SAP HANA with the RLANG language to run the analysis in R and retrieve the results to SAP HANA.

Like SAP HANA PAL procedures, you’ll need to provide some input tables for this procedure, and the procedure will return the result through some output tables. These input and output tables are passed as IN and OUT parameters of the procedure. However, unlike SAP HANA PAL procedures, no fixed number or structure for input and output tables is expected. The structure will solely depend on how you want to pass the data to the procedure and how you want to retrieve the results.

The data exchange between SAP HANA and R takes place only through SAP HANA tables and R data frames. Input tables passed from SAP HANA are read as data frames in R. The output in R should be prepared as data frames, which will be read as tables by SAP HANA.

We’ll use the following tables as input and output tables in SAP HANA:

*   Input table
    
    *   LM\_INPUT\_DATA: The data we’ll use for modeling purpose.
        
*   Output tables
    
    *   LM\_MODEL\_COEFFICIENTS: To store the model coefficients of regression analysis.
        
    *   LM\_MODEL\_STATISTICS: To store the statistics related to model fitting.
        
    *   LM\_FITTED: To store the fitted values of dependent variables (y).
        

Now, we’re all set to write our procedure in RLANG language. [Figure 6.24](#06_002.html#f6.24) shows the procedure in SAP HANA that embeds the associated R codes.

[![Sample Procedure with Embedded R Code](bilderklein/klein06_024.png)](img-f6.24.html) 

**Figure 6.24**    Sample Procedure with Embedded R Code

###### Note

x4 is a categorical variable, so we cast it as a factor. This step was not required earlier since x4 contains character values, and R automatically converts it to a factor. But including this step is a good practice, since categorical variables with numeric values will be treated as continuous variables unless explicitly converted into factors.

We’ve fitted our model using the lm() function of R. This function fits a multiple linear regression of y on x1, x2, x3, and x4 with the intercept term. The executed model is assigned to an object called fitted\_model, which is the reference of our model for future use.

The model coefficients and statistics are provided by the lm() function. We used R codes to retrieve and store specific values in data frames. At first, the R code looks complex, but with a little practice, writing this code will become pretty simple. Refer to the basic R concepts we discussed in [Chapter 4](#04_001.html#h4).

We’ll need to call this procedure to execute it to get the output. You can call this procedure either from the SQL Editor or from an SQLScript procedure.

#### From the SQL Editor

You can run the code shown in [Figure 6.25](#06_002.html#f6.25) in the SQL Editor to call the procedure.

[![Calling the RLANG Procedure from SQL Editor](bilderklein/klein06_025.png)](img-f6.25.html) 

**Figure 6.25**    Calling the RLANG Procedure from SQL Editor

The procedure proc\_reg\_analysis\_simple runs the R scripts and stores the results in the output tables. After successful execution, the SQL Editor will display the table shown in [Figure 6.26](#06_002.html#f6.26), which includes the mapping between the parameter and output tables.

[![Overview Table after Calling RLANG Procedure from the SQL Editor](bilderklein/klein06_026.png)](img-f6.26.html) 

**Figure 6.26**    Overview Table after Calling RLANG Procedure from the SQL Editor

The output of the multiple linear regression algorithm is stored in the output tables, as shown in [Figure 6.27](#06_002.html#f6.27), [Figure 6.28](#06_002.html#f6.28), and [Figure 6.29](#06_002.html#f6.29).

[![Output in the Coefficient Table LM\_MODEL\_COEFFICIENTS](bilderklein/klein06_027.png)](img-f6.27.html) 

**Figure 6.27**    Output in the Coefficient Table LM\_MODEL\_COEFFICIENTS

[![Output in the Statistics Table LM\_MODEL\_STATISTICS](bilderklein/klein06_028.png)](img-f6.28.html) 

**Figure 6.28**    Output in the Statistics Table LM\_MODEL\_STATISTICS

[![Output of the Table with Fitted Values LM\_FITTED](bilderklein/klein06_029.png)](img-f6.29.html) 

**Figure 6.29**    Output of the Table with Fitted Values LM\_FITTED

###### Note

*   R encoded the x4 column with “Yes” as 1 and “No” as 0. Thus, the coefficient table shows coefficient associated with the “Yes” value only.
    
*   The statistics table is showing the two statistics we specified in the R code. However, we can get many other statistics from R if required.
    
*   As per our R code, the fitted table shows both actual and fitted values of y side by side.
    

#### Calling from an SQLScript Procedure

Once our initial model exploration is complete, we can store the entire logic in an SQLScript procedure and call the RLANG procedure from this wrapper procedure. The code shown in [Figure 6.30](#06_002.html#f6.30) is an example of using this wrapper.

[![SQLScript Procedure That Calls the RLANG Procedure](bilderklein/klein06_030.png)](img-f6.30.html) 

**Figure 6.30**    SQLScript Procedure That Calls the RLANG Procedure

###### Note

*   We passed the input data (LM\_INPUT\_DATA) through a table variable.
    
*   The output generated by the RLANG procedure is returned as table variables. We’ll use these values to store the data in the relevant tables.
    
*   Since the output tables are already defined, we haven’t defined them here. We truncated these tables to remove any existing records.
    

The SQLScript procedure can be executed by using the following code:

```
Call “R_DATA”.”proc_load_reg_analysis_simple”();
```

The RLANG procedure will be executed, and its output will be inserted into the output tables. Of course, the output tables should have the same data that we got previously through the SQL Editor.

You can use the R model (fitted\_model) for prediction purposes also. [Figure 6.31](#06_002.html#f6.31) shows the associated RLANG procedure.

[![RLANG Procedure for Prediction Based on the Fitted Model](bilderklein/klein06_031.png)](img-f6.31.html) 

**Figure 6.31**    RLANG Procedure for Prediction Based on the Fitted Model

###### Note

*   In this case, we passed the new data (table LM\_INPUT\_DATA\_NEW) as the input data for prediction. We removed the ID column before prediction since we don’t need an ID value for our prediction.
    
*   All the model information is already stored in the object fitted\_model, which we used for prediction. We did not run the model training exercise again.
    
*   The output is stored in a new table with two columns: ID (to store the IDs) of the records and PREDICTED (to store the predicted values of y).
    

The SQLScript wrapper procedure shown in [Figure 6.32](#06_002.html#f6.32) can be used to call this RLANG procedure.

The output table contains the ID and the predicted value of y. [Figure 6.33](#06_002.html#f6.33) shows the contents of this table.

[![Wrapper SQLScript Procedure for Prediction](bilderklein/klein06_032.png)](img-f6.32.html) 

**Figure 6.32**    Wrapper SQLScript Procedure for Prediction

[![Predicted Values in the Table LM\_PREDICTED](bilderklein/klein06_033.png)](img-f6.33.html) 

**Figure 6.33**    Predicted Values in the Table LM\_PREDICTED

###### Saving and Retrieving R Models

We used the predefined model in R for prediction purposes. However, another user may run their own model in R and store the model information in the same fitted\_model object. Then, all our predictions will be wrong. Thus, you can store the model information and retrieve it during prediction in one of two ways:

1.  Save the model in R as a R file and load it when needed. The R code save(fitted\_model, file = "my\_lm\_model.rda") saves the fitted\_model in an .rda file in the working directory. During prediction, the fitted\_model object can be retrieved from the file using R code load("my\_lm\_model.rda"), which will reload the fitted\_model object.
    
2.  You can serialize the fitted\_model object in Raw data type and send this to SAP HANA. The object will be stored as the BLOB data type in SAP HANA. During prediction, you can send this BLOB data to back R and unserialize it in R to restore this version of the fitted\_model object. Please refer to SAP HANA R Integration Guide from SAP for an example ([http://s-prs.co/501403](http://s-prs.co/501403)).
    

#### From Flowgraphs

Like SAP HANA PAL functions, flowgraphs can also be used to call R scripts using the R Script node template. The R code can be written under the Script tab of the Properties view. SAP HANA also provides example codes in the R Examples section of the Node Palette.

### 6.2.4    Model Evaluation

Statistical functions in R provide various statistics to evaluate models. R also supports fully fledged programming capabilities and offers great flexibility to manipulate data, run various analysis, and compute statistics. With just a little R coding, you can achieve numerous types of validations, compute statistics on validation data, and evaluate your models with confidence. In addition, R provides various packages for running various model evaluation steps. For example, data partitioning, k-fold cross-validation, and Bootstrap-based validation can be achieved through the package caret.

In this example, we’ll presented a partition-based approach to validating the model as an example. The same table LM\_INPUT\_DATA has been used for this example. The RLANG procedure shown in [Figure 6.34](#06_002.html#f6.34) randomly partitions the original data, with 70% of data for training and 30% for prediction.

[![Sample RLANG Procedure for Training and Validation](bilderklein/klein06_034.png)](img-f6.34.html) 

**Figure 6.34**    Sample RLANG Procedure for Training and Validation

The procedure then fits the model with the training data and validates the model with the validation data and computes various statistics on validation.

Recall that creating training and validation datasets is applicable only for supervised learning where model training can be executed.

###### Note

*   Lines 14 through 17 of the code divides the input data into a training dataset (70%) and a validation dataset (30%).
    
*   The model fitting is done on the training dataset (line 20) and then used for prediction using validation dataset (line 31).
    
*   Various statistics are retrieved/computed on training and validation data.
    
*   The LM\_VALIDATION\_PREDICTED stores the actual and fitted value of y based on the validation dataset. This information is of primary interest to us because this value indicates how well the model fits the validation dataset.
    

The SQLScript procedure shown in [Figure 6.35](#06_002.html#f6.35) can be used to call this RLANG procedure.

[![SQLScript Procedure to Call the RLANG Procedure](bilderklein/klein06_035.png)](img-f6.35.html) 

**Figure 6.35**    SQLScript Procedure to Call the RLANG Procedure

We used the same coefficient and statistics tables and created a new table to store the predicted values based on validation dataset. After executing this procedure, the output tables are inserted with the data, as shown in [Figure 6.36](#06_002.html#f6.36), [Figure 6.37](#06_002.html#f6.37), and [Figure 6.38](#06_002.html#f6.38).

[![Data in the Coefficient Table](bilderklein/klein06_036.png)](img-f6.36.html) 

**Figure 6.36**    Data in the Coefficient Table

[![Data in the Statistics Table](bilderklein/klein06_037.png)](img-f6.37.html) 

**Figure 6.37**    Data in the Statistics Table

[![Data in the Table for Fitted Values of y (Using Validation Data)](bilderklein/klein06_038.png)](img-f6.38.html) 

**Figure 6.38**    Data in the Table for Fitted Values of y (Using Validation Data)

###### Note

*   The coefficients are slightly different from the previous exercise because we have fitted this model with 70% of the original data.
    
*   The statistics Validation RMSE is computed on validation data and is a measure of goodness of fit. However, this statistic is in an absolute scale; thus, to understand its magnitude compared to the values of y, we also computed the statistic “Validation Mean Y,” which is the average value of y in the validation dataset.
    

## 6.3    Summary

SAP HANA has provided several SAP HANA PAL procedures to execute various machine learning algorithms across different lifecycle phases. The procedures have predefined input and output tables, although the structures of these tables are flexible to some extent. These input and output tables vary across machine learning algorithms, but two important input tables are the data table and the parameter table, which are used in almost every SAP HANA PAL procedure. The data table provides the input data to be used for modeling, and the parameter table provides various model settings and tuning options. These SAP HANA PAL procedures can be called from the SQL Editor using SQLScript procedures and flowgraphs. Flowgraphs call the underlying SAP HANA PAL functions and can be implemented using the Predicted Analysis Library component of the Palette.

An extremely popular statistical analysis tool for data scientists, R provides various functions for data loading, data manipulation, statistical analysis, and graphics across various packages. SAP HANA with R integration allows you to run these R functions natively from SAP HANA. Using SAP HANA procedures with the RLANG language can embed R scripts to be executed in R. These RLANG procedures send input data to R and receives results from R through input and output parameters of type “table.” These RLANG procedures can be called from the SQL Editor using SQLScript procedures. Flowgraphs can also call R scripts through the R Script node.

# 7    Developing Applications with SAP HANA Predictive Analysis Library

This chapter presents a real-life use case of predictive analytics and shows you how to solve it step by step by applying the concepts introduced in the previous chapters. The SAP HANA Predictive Analysis Library (SAP HANA PAL) is the machine learning tool we’ll use for this exercise. Our analysis will be based on German credit data, which is used for many benchmarking studies in machine learning. Various machine learning techniques are interwoven and demonstrated throughout this chapter.

To solve any problem, you’ll need knowledge of the subject and the necessary tools to apply that knowledge effectively. You learned a great deal about machine learning concepts in [Chapter 2](#02_001.html#h2) and walked through the key steps of the implementation lifecycle in [Chapter 3](#03_001.html#h3). We also presented the tools available on the SAP HANA platform in [Chapter 4](#04_001.html#h4) and [Chapter 6](#06_001.html#h6). Now, in this chapter, we’ll apply all this information to build a working predictive analytics application!

Before we start this journey, one last piece of advice first! No fixed path exists to solve a machine learning problem. The terrain is probabilistic in nature, and we cannot strictly say that any one path is the only path! In this chapter, we present one way to solve our use case, based on our experience, but you are free to choose your own course.

## 7.1    Introduction to the Use Case

The use case we present in this chapter is based on the famous dataset of German credit data. The original data was presented by Professor Dr. Hans Hofmann, Institute for Statistics and Econometrics, University of Hamburg. This data was part of the StatLog database used in the European StatLog project, which compared the performance of various machine learning, statistical, and neural network algorithms on datasets from different industries. You can download the data from the UC Irvine Machine Learning Repository at [http://archive.ics.uci.edu/ml](http://archive.ics.uci.edu/ml). This dataset contains bank credit data for 1,000 customers with 20 attributes related to their socioeconomic status, their loans, and whether they’ve repaid the loan or defaulted. We’ll dive more deeply into this data in [Section 7.2.1](#07_002.html#h7.2.1).

Our use case involves minimizing losses from current loan accounts at a bank. Before bank managers approve the loan application of a prospective borrower, the socioeconomic profile of the customer must be created and checked to assess his or her ability to repay the loan. However, such manual decisions may also result in approving a loan to a customer who will default or in rejecting the loan application of a good customer. In both cases, the bank incurs some loss, either directly or indirectly. The bank wants to minimize this loss by implementing a machine learning application that will analyze socioeconomic profiles, information on the requested loan of new applicants, and predict their likeliness to repay or default.

As a machine learning expert, you’ve been appointed by the bank to build the model. The bank has given you the historical data of 1,000 applicants who were granted loans, with 20 attributes to capture their socioeconomic profiles and loan details. The data also contains information on whether they repaid the loan or defaulted. Your model should identify hidden patterns within this data and predict whether a new applicant will repay the loan or default. Based on this prediction, the manager can approve or reject the loan application.

The German credit dataset can also be used to demonstrate one type of a loss function. However, we’ll keep things simple in this chapter. You can try it out on your own if you’d like!

## 7.2    Building a Predictive Analytics Application Using SAP HANA PAL

Let’s now build our predictive analytics application together. First, let’s be very clear about the requirement from a machine learning perspective. In simple terms, the requirements of this use case boils down to the following facts:

*   There are two groups of loan applicants based on their repayment status: Good (those who repay the loan) and Bad (those who default).
    
*   We have historical data on socioeconomic profiles and loan-related details of members of these two groups.
    
*   We need to predict whether a new loan applicant is a member of one of these two groups, based on his or her socioeconomic data and the particulars of the loan application.
    

As you can see, this problem is a classification problem from a machine learning perspective. The underlying assumption is that the ability of a customer to repay a loan depends on some of his or her socioeconomic profiles and a few loan-related parameters like loan amount and loan duration. The socioeconomic profiles and loan-related parameters are independent variables, and the repayment capability of a customer is the dependent variable. Loan applicants can be grouped into one of two categories or classes based on their repayment status. Thus, this classification is a binary classification problem, in other words, with only two choices.

Now that we’ve mapped out our use case to several underlying machine learning concepts, we’ll follow the key steps of the implementation lifecycle described earlier in [Chapter 3](#03_001.html#h3) to build our predictive analytics application.

### 7.2.1    Understanding the Business Problem and the Data

Let’s now look more closely into the underlying business problem and the data. Often, business users have a good understanding of likely influential factors in a business scenario, so a discussion with these users will reveal more information about the nature of the influence of any one factor.

Several factors may influence the ability to repay a loan; sometimes, an unexpected event may turn a good borrower into a bad borrower. For example, the current turmoil caused by the COVID-19 pandemic has jeopardized many borrowers in a variety of socioeconomic conditions. Thus, keep in mind that influential attributes may behave differently in different situations. However, to start, we’ll need to gather as much information as possible on the factors that may be potentially influential and the nature of their influence.

The German credit dataset collected 20 attributes as possible influential factors; we’ll determine later, based on the data, which attributes are truly influential for the predictions in our use case.

We loaded this data into table CREDIT\_RISK\_DATA in the ML\_USECASE schema. Throughout this chapter, we’ll use the ML\_USECASE schema to create our catalog objects. [Table 7.1](#07_002.html#t7.1) shows the categorical variables considered in our data and their category values.

 
| Categorical Variable in CREDIT\_RISK\_DATA || Description || Category Values |
| --- | --- | --- |
| ACCOUNT\_BALANCE || Status of existing checking account || A11: < 0 DMA12: 0 ⩽ ... < 200 DMA13: ⩾ 200 DMA14: no checking account |
| --- | --- | --- |
| PREV\_CREDIT\_PAYMENT\_STATUS || Credit history || A30: no credits taken/all credits paid back dulyA31: all credits at this bank paid back dulyA32: existing credits paid back duly till nowA33: delay in paying off in the pastA34: critical account/other credits existing (not at this bank) |
| PURPOSE || Purpose of taking loan || A40: car (new)A41: car (used)A42: furniture/equipmentA43: radio/televisionA44: domestic appliancesA45: repairsA46: educationA47: vacationA48: retrainingA49: businessA410: others |
| VALUE\_SAVINGS\_STOCKS || Value of savings account/bonds || A61: < 100 DMA62: 100 ⩽ ... < 500 DMA63: 500 ⩽ …< 1000 DMA64: ⩾ 1000 DMA65: unknown/no savings account |
| CURRENT\_EMPL\_LENGHT || Present employment since || A71: unemployedA72: < 1 yearA73: 1 ⩽ ... < 4 yearsA74: 4 ⩽ ... < 7 yearsA75: ⩾ 7 years |
| INSTALMENT\_PERCENT\* || Installment rate in percentage of disposable income || 1: 1%2: 2%3: 3%4: 4% |
| SEX\_MARITAL\_STATUS || Sex and marital status || A91: male divorced/separatedA92: female divorced/separated/marriedA93: male singleA94: male married/widowedA95: female single (there is no data with this value) |
| GUARANTORS || Other debtors/guarantors || A101: noneA102: co-applicantA103: guarantor |
| DURATION\_CURRENT\_ADDR\* || Present residence since || 1: 1 year2: 2 years3: 3 years4: 4 years |
| MOST\_VALUABLE\_ASSET || Most valuable property || A121: real estateA122: building society savings agreement/life insuranceA123: car or otherA124: unknown/no property |
| CONCURRENT\_CREDIT || Other installment plans || A141: bankA142: storesA143: none |
| APARTMENT\_TYPE || Type of housing || A151: rentA152: ownA153: for free |
| NO\_OF\_CREDITS\_THIS\_BANK\* || Number of existing credits at this bank || 1: 12: 23: 34: 4 |
| OCCUPATION || Job || A171: unemployed/unskilled - non-residentA172: unskilled - residentA173: skilled employee/officialA174: management/self-employed/highly qualified employee/officer |
| NO\_OF\_DEPENDENTS\* || Number of dependents || 1: 12: 2 |
| TELEPHONE || Any telephone? || A191: noA192: yes |
| FOREIGN\_WORKER || Foreign worker || A201: yesA202: no |
| DEFAULTER || Whether customer defaulted || 0: not defaulter1: defaulter |

**Table 7.1**    Categorical Attributes in Our German Credit Data

The categorical variables marked with \* were numeric in the original data, but they have less distinct values and therefore, we’ll treat them as categorical.

The values of categorical variables look little cryptic; however, they have been captured with a scheme. The first 2 or 3 digits identify the attribute number (like A1, A14), and the last digit represents the category value (only “purpose” has more than 10 values, from 0 to 10).

The variable DEFAULTER represents the response variable, which can have two values 0 or 1 (1 or 2 in the original data). We created this variable as an integer and coded 0 for non-defaulters and 1 for defaulters so that we can use these values as numbers to calculate some statistics. We’ll use this variable as a categorical variable during modeling.

The data also contains following three continuous attributes:

*   CREDIT\_DURATION representing credit duration in months (2nd attribute)
    
*   CREDIT\_AMOUNT representing credit amount in DM (5th attribute)
    
*   AGE representing the age of the applicant in years (13th attribute)
    

[Figure 7.1](#07_002.html#f7.1) shows the sample data that we’ll use throughout this chapter.

[![A Glimpse of the Credit Risk DataCredit risk data](bilderklein/klein07_001.png)](img-f7.1.html) 

**Figure 7.1**    A Glimpse of the Credit Risk Data

Let’s now explore the data to gain further insights into it. First, we can check for any missing values, or NULL entries, in the data. Our data doesn’t contain missing values. However, in general, you may check for missing values with the following SQL code:

```
SELECT SUM(CASE WHEN ACCOUNT_BALANCE IS NULL THEN 1 ELSE 0 END) AS NULL_ACCOUNT_BALANCE FROM ML_USECASE.CREDIT_RISK_DATA
```

You can also compute some summary statistics of our variables. However, this data contains mostly categorical variables, so we’ll look at the data graphically.

###### Note

The response variable DEFAULTER contains the value 1 for defaulters and 0 for customers who have repaid (good customers). Suppose a subgroup of n customers, let’s say all foreign workers, contains n[1] defaulters (DEFAULTER = 1) and n[2] good customers (DEFAULTER = 0). Therefore, n[1] + n[2] = n. Now, the average value of the DEFAULTER variable in this group of n customers is (1 \* n[1] + 0 \* n[2])/n = n[1]/n. Recall from [Chapter 2](#02_001.html#h2) that this equation is an estimate of the probability of a customer being a defaulter in that group. Therefore, the average value of the variable DEFAULTER gives you an estimate of the probability that a customer is a defaulter. Our entire dataset contains data about 700 good customers and 300 defaulted customers, so 0.3, or approximately 30%, is the estimated probability that a customer is defaulter.

This kind of calculation is precisely why we used the integer data type for the variable DEFAULTER and map defaulters to 1. With this approach, you can use the average value to easily see the estimated probabilities across categories of other attributes, without the need for any further coding in SAP HANA.

SAP HANA natively provides some basic charts and graphs, available in the Open Data Preview popup menu of a table. In this use case, we’ll mainly use this option, especially through the Analysis and Distinct values tabs. For a few graphs, we’ll use R.

Seventeen categorical attributes exist in this data, so we won’t discuss every attribute in detail. Instead, let’s look at five distinct cases next.

#### Case 1: Variable Showing Some Influence

[Figure 7.2](#07_002.html#f7.2) shows the average value of the response variable DEFAULTER across different categories of the variable ACCOUNT\_BALANCE.

###### Note

The bar chart shows that a steady pattern exists across different categories, which implies that the probability a customer will default changes across categories of ACCOUNT\_BALANCE.

Therefore, you can consider ACCOUNT\_BALANCE as an influential factor and select this variable for further analysis.

[![Average of DEFAULTER against ACCOUNT\_BALANCE](bilderklein/klein07_002.png)](img-f7.2.html) 

**Figure 7.2**    Average of DEFAULTER against ACCOUNT\_BALANCE

#### Case 2: Variable Showing No Influence

[Figure 7.3](#07_002.html#f7.3) shows the average of DEFAULTER across categories of NO\_OF\_DEPENDENTS.

[![Average of DEFAULTER against NO\_OF\_DEPENDENTS](bilderklein/klein07_003.png)](img-f7.3.html) 

**Figure 7.3**    Average of DEFAULTER against NO\_OF\_DEPENDENTS

###### Note

The bar chart shows that no pattern exists across different categories. Therefore, the probability that a customer will default does not change across categories of NO\_OF\_DEPENDENTS.

Therefore, you can reject NO\_OF\_DEPENDENTS as an influential variable and exclude this variable from further analysis.

#### Case 3: Variable Showing Influence with Suitable Transformation

[Figure 7.4](#07_002.html#f7.4) shows the average of DEFAULTER against the categories of PREV\_CREDIT\_PAYMENT\_STATUS.

[![Average of DEFAULTER against PREV\_CREDIT\_PAYMENT\_STATUS](bilderklein/klein07_004.png)](img-f7.4.html) 

**Figure 7.4**    Average of DEFAULTER against PREV\_CREDIT\_PAYMENT\_STATUS

###### Note

The bar chart shows that a steady pattern exists across different categories. Therefore, the probability that a customer will default changes across categories of PREV\_CREDIT\_PAYMENT\_STATUS.

However, two categories (A30 and A31) have almost similar averages, so these two variables do not have significantly different effects. You can merge these two variables together.

Category A30 means no credits taken/all credits have been paid back duly, and category A31 means all credits at this bank have been paid back duly. Thus, merging these two groups together makes perfect sense from a business perspective. This new group will contain customers who have fully paid back their loans in the past or never had a loan in the first place.

Similarly, the middle two categories (A32 and A33) may be merged.

Finally, you can consider PREV\_CREDIT\_PAYMENT\_STATUS as an influential factor and select this variable for further analysis, once categories with similar effects are merged together.

#### Case 4: Variable Showing Marginal/Confusing Influence

[Figure 7.5](#07_002.html#f7.5) shows the average of DEFAULTER against the categories of PURPOSE.

[![Average of DEFAULTER against PURPOSE](bilderklein/klein07_005.png)](img-f7.5.html) 

**Figure 7.5**    Average of DEFAULTER against PURPOSE

###### Note

In this case, the averages of a few groups are low, but others are high.

Merging some groups together doesn’t make sense from a business perspective. For instance, the bottom two categories are A41 (buying used car) and A48 (for retraining), and merging them may not be meaningful.

In this scenario, you may need to talk to business users to understand their views and select or reject this variable accordingly.

We selected this variable for further analysis, but it contains too many categories and makes the data fragmented. So, we merged a few categories together.

#### Case 5: Variable Showing Pseudo Influence

[Figure 7.6](#07_002.html#f7.6) shows the average of DEFAULTER against the categories of FOREIGN\_WORKER.

Initially, this bar chart gives the impression that these two groups have different effects, which is true. However, the average DEFAULTER of category A201 is close to 0.3, which is the average of DEFAULTER on the entire population. Group A02 has low average (close to 0.1) and has influence. Note however, that this variable tells you something about the distribution of the data. Group A202 should have significantly fewer members; otherwise, the average on the entire population will be less than 0.3, which is not true. Therefore, if both groups have the same number of customers, the average of DEFAULTER on the total population will be close to 0.2. To verify this fact, we can look at the frequency distribution for FOREIGN\_WORKER, shown in [Figure 7.7](#07_002.html#f7.7), which confirms our suspicions. Group A202 has only 37 customers out of total 1,000 customers!

[![Average of DEFAULTER against FOREIGN\_WORKER](bilderklein/klein07_006.png)](img-f7.6.html) 

**Figure 7.6**    Average of DEFAULTER against FOREIGN\_WORKER

[![Frequency Distribution of FOREIGN\_WORKER](bilderklein/klein07_007.png)](img-f7.7.html) 

**Figure 7.7**    Frequency Distribution of FOREIGN\_WORKER

The influence we observed is basically a pseudo influence. Based on this observation, this variable can also be excluded from further analysis. However, let’s still select it to show how eventually it will be rejected by the model.

Continuing with the visual inspection of our data, we decided to select the categorical attributes shown in [Table 7.2](#07_002.html#t7.2) for further analysis and reject the others.

 
| Categorical Attributes || Transformation |
| --- | --- |
| ACCOUNT\_BALANCE || No transformation. |
| --- | --- |
| PREV\_CREDIT\_PAYMENT\_STATUS || Merge categories A30 and A31 into category A30 and categories A32 and A33 into category A32. |
| PURPOSE || Merge categories A42, A44, and A45 into A42 and categories A46 through A410 into A410. |
| VALUE\_SAVINGS\_STOCKS || Merge categories A61 and A62 into A61 and categories A63, A64, and A65 into A63. |
| CURRENT\_EMPL\_LENGHT || Merge categories A71 and A72 into A71 and categories A73, A74, and A75 into A73. |
| SEX\_MARITAL\_STATUS || Merge categories A91 and A92 into A91 and categories A93 and A94 into A93. |
| GUARANTORS || No transformation. |
| MOST\_VALUABLE\_ASSET || Merge categories A123 and A122 into A122. |
| CONCURRENT\_CREDIT || Merge categories A141 and A142 into A141. |
| APARTMENT\_TYPE || Merge categories A151 and A153 into A151. |
| FOREIGN\_WORKER || No transformation. |

**Table 7.2**    Selected Categorical Variables and Transformations after Exploratory Data Analysis

###### Note

Some of our selected categorical variables have only marginal influence, but we’ll retain them to avoid missing out on any potentially important information. Perhaps, a few variables jointly show some influence, which we’ll investigate during the model-building exercise.

Why do we need to shortlist variables at the first place? Because associated algorithms internally create (n – 1) binary attributes for a categorical attribute with n categories, so the total number of attributes further increases while modeling. Too many attributes can lead to the “curse of dimensionality,” and the model is often overfitted!

We used a simple trick here to shortlist influential categorical variables; we could have used some statistical testing on data as well. However, we limited ourselves to a simple technique to emphasize that often simple approaches are quite powerful.

Let’s now look at the three continuous attributes. [Figure 7.8](#07_002.html#f7.8) shows the histograms and boxplots for each of the continuous variables.

[![Histograms and Boxplots of the Continuous Variables](bilderklein/klein07_008.png)](img-f7.8.html) 

**Figure 7.8**    Histograms and Boxplots of the Continuous Variables

As you can see from these charts, these attributes are highly skewed, and many outliers exist in the data. We’ll apply a logarithmic transformation to these variables to manage their skewness and their outliers. Also, we’ll take away data with AGE ⩽ 70 and CREDIT\_AMOUNT ⩽ 15000 to reduce the influence of some outliers. We’ll take care of the significance of these attributes during the modeling stage in the next section.

### 7.2.2    Data Preparation

Now armed with some initial observations on our data, we’re ready to prepare the data required to build our machine learning models. We’ll create a new table, called CREDIT\_RISK\_DATA\_MODIFIED, with the dependent variable DEFAULTER and our shortlisted independent variables with associated transformations. This step can be achieved many ways: either using SQL code or creating a calculation view. For our purposes, we’ll use the SQL code shown in [Listing 7.1](#07_002.html#l7.1).

```
CREATE COLUMN TABLE "ML_USECASE"."CREDIT_RISK_DATA_MODIFIED" (
 "ACCOUNT_BALANCE" NVARCHAR(3),
 "LN_CREDIT_DURATION" DOUBLE,
 "PREV_CREDIT_PAYMENT_STATUS" NVARCHAR(3),
 "PURPOSE" NVARCHAR(4),
 "LN_CREDIT_AMOUNT" DOUBLE,
 "VALUE_SAVINGS_STOCKS" NVARCHAR(3),
 "CURRENT_EMPL_LENGTH" NVARCHAR(3),
 "SEX_MARITAL_STATUS" NVARCHAR(3),
 "GUARANTORS" NVARCHAR(4),
 "MOST_VALUABLE_ASSET" NVARCHAR(4),
 "LN_AGE" DOUBLE,
 "CONCURRENT_CREDIT" NVARCHAR(4),
 "APARTMENT_TYPE" NVARCHAR(4),
 "FOREIGN_WORKER" NVARCHAR(4),
 "DEFAULTER" INTEGER);
 
INSERT INTO "ML_USECASE"."CREDIT_RISK_DATA_MODIFIED" (
SELECT 
"ACCOUNT_BALANCE",
LN("CREDIT_DURATION") AS "LN_CREDIT_DURATION",
(CASE WHEN "PREV_CREDIT_PAYMENT_STATUS" = 'A31' THEN 'A30' 
WHEN "PREV_CREDIT_PAYMENT_STATUS" = 'A33' THEN 'A32' 
ELSE "PREV_CREDIT_PAYMENT_STATUS" END) AS "PREV_CREDIT_PAYMENT_STATUS",
(CASE WHEN "PURPOSE" IN ('A44', 'A45') THEN 'A42' 
WHEN "PURPOSE" IN ('A46', 'A47', 'A48', 'A49') THEN 'A410' 
ELSE "PURPOSE" END) AS "PURPOSE",
LN("CREDIT_AMOUNT") AS "LN_CREDIT_AMOUNT",
(CASE WHEN "VALUE_SAVINGS_STOCKS" = 'A62' THEN 'A61' 
WHEN "VALUE_SAVINGS_STOCKS" IN ('A64', 'A65') THEN 'A63'
ELSE "VALUE_SAVINGS_STOCKS" END) AS "VALUE_SAVINGS_STOCKS",
(CASE WHEN "CURRENT_EMPL_LENGHT" = 'A72' THEN 'A71'
WHEN "CURRENT_EMPL_LENGHT" IN ('A74', 'A75') THEN 'A73'
ELSE "CURRENT_EMPL_LENGHT" END) AS     "CURRENT_EMPL_LENGHT",
(CASE WHEN "SEX_MARITAL_STATUS" = 'A92' THEN 'A91'
WHEN "SEX_MARITAL_STATUS" = 'A94' THEN 'A93'
ELSE "SEX_MARITAL_STATUS" END) AS "SEX_MARITAL_STATUS",
"GUARANTORS",
(CASE WHEN "MOST_VALUABLE_ASSET" = 'A123' THEN 'A122'
ELSE "MOST_VALUABLE_ASSET" END) AS "MOST_VALUABLE_ASSET",
LN("AGE") AS "LN_AGE",
(CASE WHEN "CONCURRENT_CREDIT" = 'A142' THEN 'A141'
ELSE "CONCURRENT_CREDIT" END) AS "CONCURRENT_CREDIT",
(CASE WHEN "APARTMENT_TYPE" = '153' THEN 'A151'
ELSE "APARTMENT_TYPE" END) AS "APARTMENT_TYPE",
"FOREIGN_WORKER",
"DEFAULTER"
FROM "ML_USECASE"."CREDIT_RISK_DATA" 
WHERE "AGE" <= 70 AND "CREDIT_AMOUNT" <= 15000);
```

**Listing 7.1**    SQL Code to Prepare the Data for Modeling

We’re now all set to start building our machine learning models!

### 7.2.3    Model Building

Now, you’ll need to decide which algorithm to choose for building the model. Since our use case is a classification problem, selecting from the many classification algorithms available in SAP HANA PAL can be quite difficult. You’ll need to consider different selection criteria like robust classification, interpretation of the relationship, simplicity and ease of use, and the handling of different data issues like collinearity or heteroscedasticity. Further, each algorithm has its own advantages and disadvantages, and careful consideration will be required when selecting algorithms.

For our use case, we chosen the following two algorithms:

*   Logistic regression (with elastic net regularization)  
    A robust method and provides a nice interpretation on the relative influences of independent attributes.
    
*   Support Vector Machine (for classification)  
    A method that provides good results even when a relationship is non-linear. However, this method returns a hyperplane that separates the response classes; therefore, no natural interpretation of the model exists.
    

The associated SAP HANA PAL procedures are PAL\_LOGISTIC\_REGRESSION and PAL\_SVM.

#### Building a Logistic Regression Model

Let’s start with building a logistic regression model on the data. In the SQL Editor, run and execute the code shown in [Listing 7.2](#07_002.html#l7.2).

```
CREATE LOCAL TEMPORARY COLUMN TABLE "#temp_param" ("PARAM_NAME" VARCHAR(256), "INT_VALUE" INTEGER, "DOUBLE_VALUE" DOUBLE,"STRING_VALUE" VARCHAR(1000));
-- Insert parameters for training
INSERT INTO "#temp_param" VALUES ('CLASS_MAP0', NULL, NULL, '0');
INSERT INTO "#temp_param" VALUES ('CLASS_MAP1', NULL, NULL, '1'); 
INSERT INTO "#temp_param" VALUES ('METHOD', 2, NULL, NULL);
INSERT INTO "#temp_param" VALUES ('STAT_INF',1,NULL,NULL);
INSERT INTO "#temp_param" VALUES ('DEPENDENT_VARIABLE', NULL, NULL,'DEFAULTER');
INSERT INTO "#temp_param" VALUES ('ENET_LAMBDA', NULL, 0.002, NULL);
INSERT INTO "#temp_param" VALUES ('ENET_ALPHA', NULL, 0.001, NULL);
-- Insert parameters for validation
INSERT INTO "#temp_param" VALUES ('RESAMPLING_METHOD', NULL, NULL,  
'stratified_cv');
INSERT INTO "#temp_param" VALUES ('FOLD_NUM', 4, NULL, NULL);
INSERT INTO "#temp_param" VALUES ('REPEAT_TIMES', 2, NULL, NULL);
INSERT INTO "#temp_param" VALUES ('EVALUATION_METRIC', NULL, NULL, 'ACCURACY');
INSERT INTO "#temp_param" VALUES ('PROGRESS_INDICATOR_ID', NULL, NULL, 'PII');
-- Run the logistic regression on entire data
CALL _SYS_AFL.PAL_LOGISTIC_REGRESSION (ML_USECASE.CREDIT_RISK_DATA_MODIFIED, 
"#temp_param",?,?,?, ?);
```

**Listing 7.2**    SQL Code to Run Logistic Regression on Modified Data

###### Note

The CLASS\_MAP0 and CLASS\_MAP1 parameters specifies values of the dependent variable we want to show, coded as 0 and 1, respectively.

The METHOD = 2 indicates we want to use the cyclical coordinate descent method to fit elastic net regularized logistic regression.

The associated λ and α values are specified in the ENET\_LAMDA and ENET\_ALPHA parameters.

We added several validation parameters to the parameter table to see how the model performs on the validation dataset.

The code shown in [Listing 7.2](#07_002.html#l7.2) should result in an output table, as shown in [Figure 7.9](#07_002.html#f7.9). We then copied the coefficient table to Excel to color code the output, as shown in [Figure 7.10](#07_002.html#f7.10).

[![Statistics Table: First Iteration](bilderklein/klein07_009.png)](img-f7.9.html) 

**Figure 7.9**    Statistics Table: First Iteration

###### Note

The statistic timeout shows whether the algorithm ran into timeout. The value FALSE indicates the algorithm did not time out.

We specified 2 validation cycles of 4-fold cross validation. The statistics TEST\_1\_ACCURACY and TEST\_2\_ACCURACY show the accuracy values of each validation cycle. Since we used 4-fold cross-validation, four accuracy values are shown against each validation cycle.

The TEST\_ACCURACY.MEAN statistic provides the average accuracy based on the accuracy values obtained during validation. The average accuracy of our model is 0.755323, or approximately 75.5%.

The TEST\_ACCURACY.VAR statistic provides the variance among the accuracy values. This value is 0.000842742.

Other statistics like Akaike Information Criteria (AIC) and log-likelihood are shown also in the statistics table.

[![Coefficient Table: First Iteration](bilderklein/klein07_010.png)](img-f7.10.html) 

**Figure 7.10**    Coefficient Table: First Iteration

###### Note

A few variables, marked in orange, have p values are greater than 0.1. These variables are not significant for modeling.

Some other attributes have p values between 0.05 and 0.1. These attributes have less significance, but we’ll still retain them for our next round.

For the attribute PURPOSE, except for the category A410, all categories have some significance. Therefore, we’ll retain this variable for our next round.

The p value of category A73 of CURRENT\_EMPL\_LENGTH is slightly above 0.1, so we’ll also retain this variable as well.

A few rows have “?” as the p value. These categories have been coded as 0 in the binary coding of the attribute and do not directly contribute to the model equation. However, the significance of other categories of the same attribute are actually compared against the effect of this particular category.

The variable \_\_PAL\_DELIMIT\_\_ signifies that the SAP HANA PAL procedure has converted the category variables in binary encoding.

Our initial model shows some room for improvement, so the next step is to fit another logistic regression model that excludes non-significant attributes. Specify the selected independent attributes in the parameter table through the SELECTED\_FEATURES parameter. To run the second iteration of our modeling project, use the code shown in [Listing 7.3](#07_002.html#l7.3).

```
CREATE LOCAL TEMPORARY COLUMN TABLE "#temp_param" ("PARAM_NAME" VARCHAR(256), "INT_VALUE" INTEGER, "DOUBLE_VALUE" DOUBLE,"STRING_VALUE" VARCHAR(1000));
-- Insert parameters for training
INSERT INTO "#temp_param" VALUES ('CLASS_MAP0', NULL, NULL, '0');
INSERT INTO "#temp_param" VALUES ('CLASS_MAP1', NULL, NULL, '1'); 
INSERT INTO "#temp_param" VALUES ('METHOD', 2, NULL, NULL);
INSERT INTO "#temp_param" VALUES ('STAT_INF',1,NULL,NULL);
INSERT INTO "#temp_param" VALUES ('DEPENDENT_VARIABLE', NULL, NULL,'DEFAULTER');
INSERT INTO "#temp_param" VALUES ('ENET_LAMBDA', NULL, 0.002, NULL);
INSERT INTO "#temp_param" VALUES ('ENET_ALPHA', NULL, 0.001, NULL);
INSERT INTO "#temp_param" VALUES ('SELECTED_FEATURES', NULL, NULL, 'ACCOUNT_BALANCE,LN_CREDIT_DURATION,PREV_CREDIT_PAYMENT_STATUS,PURPOSE,VALUE_SAVINGS_STOCKS,CURRENT_EMPL_LENGHT,SEX_MARITAL_STATUS,CONCURRENT_CREDIT');
-- Insert parameters for validation
INSERT INTO "#temp_param" VALUES ('RESAMPLING_METHOD', NULL, NULL,  
'stratified_cv');
INSERT INTO "#temp_param" VALUES ('FOLD_NUM', 4, NULL, NULL);
INSERT INTO "#temp_param" VALUES ('REPEAT_TIMES', 2, NULL, NULL);
INSERT INTO "#temp_param" VALUES ('EVALUATION_METRIC', NULL, NULL, 'ACCURACY');
INSERT INTO "#temp_param" VALUES ('PROGRESS_INDICATOR_ID', NULL, NULL, 'PII');
-- Run the logistic regression on entire data
CALL _SYS_AFL.PAL_LOGISTIC_REGRESSION (ML_USECASE.CREDIT_RISK_DATA_MODIFIED, 
"#temp_param",?, ?,?, ?);
```

**Listing 7.3**    SQL Code to Run Logistic Regression of Selected Attributes on Modified Data

###### Tip

When we use the SELECTED\_FEATURES parameter, sometimes, the procedure throws an error message saying some attribute is not available in data. This problem occurs if special characters exist in the list. Try to keep all the attribute names in a single line separated by commas, without spaces, and copy the column names directly from table definition to avoid this problem.

[Figure 7.11](#07_002.html#f7.11) and [Figure 7.12](#07_002.html#f7.12) show the output tables for the second iteration of this model.

[![Statistics TableStatistics table: Second Iteration](bilderklein/klein07_011.png)](img-f7.11.html) 

**Figure 7.11**    Statistics Table: Second Iteration

[![Coefficient TableCoefficient table: Second Iteration](bilderklein/klein07_012.png)](img-f7.12.html) 

**Figure 7.12**    Coefficient Table: Second Iteration

Note that, except for the A410 category of PURPOSE, all the variables have p values less than 0.1, and only few have p values between 0.05 and 0.1. Therefore, every selected variable has some significance. We’ll keep these variables for now, perhaps revisiting this list during the parameter selection phase, if required. This initial analysis says that the accuracy of our initial model is around 75%. Therefore, we can at least consider linear regression as a good candidate model.

#### Building a Support Vector Machine (SVM) Model

Let’s now turn our attention to a Support Vector Machine (SVM) model. The code shown in [Listing 7.4](#07_002.html#l7.4) will fit an SVM model to our data.

```
DROP TABLE "#temp_param";
CREATE LOCAL TEMPORARY TABLE "#temp_param" ("PARAM_NAME" VARCHAR(256),  
"INT_VALUE" INTEGER, "DOUBLE_VALUE" DOUBLE,"STRING_VALUE" VARCHAR(1000));
-- Parameters for training
INSERT INTO "#temp_param" VALUES ('TYPE', 1, NULL, NULL);
INSERT INTO "#temp_param" VALUES ('KERNEL_TYPE', 2, NULL, NULL); 
INSERT INTO "#temp_param" VALUES ('HAS_ID', 0, NULL, NULL);
INSERT INTO "#temp_param" VALUES ('PROBABILITY',1,NULL,NULL);
INSERT INTO "#temp_param" VALUES ('DEPENDENT_VARIABLE', NULL, NULL,'DEFAULTER');
-- Insert parameters for validation
INSERT INTO "#temp_param" VALUES ('RESAMPLING_METHOD', NULL, NULL,  
'stratified_cv');
INSERT INTO "#temp_param" VALUES ('FOLD_NUM', 4, NULL, NULL);
INSERT INTO "#temp_param" VALUES ('REPEAT_TIMES', 2, NULL, NULL);
INSERT INTO "#temp_param" VALUES ('EVALUATION_METRIC', NULL, NULL, 'ACCURACY');
INSERT INTO "#temp_param" VALUES ('PROGRESS_INDICATOR_ID', NULL, NULL, 'PII');
-- Run the SVM on entire data
CALL _SYS_AFL.PAL_SVM(ML_USECASE.CREDIT_RISK_DATA_MODIFIED,"#temp_param",?,?,?);
```

**Listing 7.4**    SQL Code to Run SVM on Modified Data

###### Note

The parameter Type = 1 specifies that this model is an SVM model for classification.

The parameter KERNEL\_TYPE = 2 specifies that we want to run this model with the radial basis function (RBF) kernel.

We specified some validation parameters for the SVM model.

Two important parameters must be maintained for the SVM model. We used the default values of these parameters for initial run, but we’ll determine their optimal values through a grid search later in [Section 7.2.4](#07_002.html#h7.2.4).

*   SVM\_C: This parameter specifies the value of parameter C, which represents how much misclassification on training data we will allow. The higher the value of C, the lower the tolerance for misclassification.
    
*   RBF\_GAMMA: This specifies the value of parameter Gamma, which represents how quickly the RBF class boundaries dissipate as they go away from the support vectors. A large gamma value decreases the effect of any individual support vector.
    

The output tables shown in [Figure 7.13](#07_002.html#f7.13) and [Figure 7.14](#07_002.html#f7.14) are generated after running the code. The coefficient table shows the model content of the SVM.

[![Model Table: SVM](bilderklein/klein07_013.png)](img-f7.13.html) 

**Figure 7.13**    Model Table: SVM

[![Statistics Table: SVM](bilderklein/klein07_014.png)](img-f7.14.html) 

**Figure 7.14**    Statistics Table: SVM

###### Note

Like the logistic regression model, the SVM model also shows similar statistics applicable for SVM. The first five statistics can be interpreted in the same way as the statistics provided during our validation of the logistic regression model. The average accuracy of the SVM model is 0.703257, or approximately 70%.

Note that AIC and log-likelihood statistics are not applicable for SVM because SVM does not use decision boundaries based on underlying probability distributions.

Note that the SVM model provides around 70% accuracy on our validation dataset. Therefore, we’ll consider it a candidate model and see if we can improve its accuracy as part of the model validation and refinement step, which we’ll describe next.

### 7.2.4    Model Validation and Refinement

This step is really a continuation of the modeling exercise, but in this phase, we’ll refine our candidate models by fine-tuning their parameters, and then finally, we’ll select the model that provides the better fit.

#### Refinement of the Logistic Regression Model

Let’s first look at our logistic regression model. We already identified a subset of significant attributes, and now, we’ll run the optimal parameter selection functionality. The code shown in [Listing 7.5](#07_002.html#l7.5) achieves this objective.

```
CREATE LOCAL TEMPORARY COLUMN TABLE "#temp_param" ("PARAM_NAME" VARCHAR(256), "INT_VALUE" INTEGER, "DOUBLE_VALUE" DOUBLE,"STRING_VALUE" VARCHAR(1000));
-- Insert parameters for training
INSERT INTO "#temp_param" VALUES ('CLASS_MAP0', NULL, NULL, '0');
INSERT INTO "#temp_param" VALUES ('CLASS_MAP1', NULL, NULL, '1'); 
INSERT INTO "#temp_param" VALUES ('METHOD', 2, NULL, NULL);
INSERT INTO "#temp_param" VALUES ('STAT_INF',1,NULL,NULL);
INSERT INTO "#temp_param" VALUES ('DEPENDENT_VARIABLE', NULL, NULL,'DEFAULTER');
INSERT INTO "#temp_param" VALUES ('SELECTED_FEATURES', NULL, NULL, 'ACCOUNT_BALANCE,LN_CREDIT_DURATION,PREV_CREDIT_PAYMENT_STATUS,PURPOSE,VALUE_SAVINGS_STOCKS,CURRENT_EMPL_LENGHT,SEX_MARITAL_STATUS,CONCURRENT_CREDIT');
-- Insert parameters for validation and optimal parameter selection
INSERT INTO "#temp_param" VALUES ('ENET_LAMBDA_VALUES', NULL, NULL, '{0.002, 0.01,0.2,0.4,0.5, 0.8}');
INSERT INTO "#temp_param" VALUES ('ENET_ALPHA_VALUES', NULL, NULL, '{0.001, 0.01, 0, 0.1,0.2,0.3,0.4,0.5,0.6}');
INSERT INTO "#temp_param" VALUES ('RESAMPLING_METHOD', NULL, NULL,  
'stratified_cv');
INSERT INTO "#temp_param" VALUES ('FOLD_NUM', 4, NULL, NULL);
INSERT INTO "#temp_param" VALUES ('REPEAT_TIMES', 2, NULL, NULL);
INSERT INTO "#temp_param" VALUES ('EVALUATION_METRIC', NULL, NULL, 'ACCURACY');
INSERT INTO "#temp_param" VALUES ('PROGRESS_INDICATOR_ID', NULL, NULL, 'PII');
INSERT INTO "#temp_param" VALUES ('PARAM_SEARCH_STRATEGY', NULL, NULL, 'grid');
-- Run the logistic regression 
CALL _SYS_AFL.PAL_LOGISTIC_REGRESSION (ML_USECASE.CREDIT_RISK_DATA_MODIFIED, 
"#temp_param",?, ?,?, ?);
```

**Listing 7.5**    SQL Code to Run Validation and Optimal Parameter Selection on a Logistic Regression Model

###### Note

In this code, we specified a range of values for tuning parameters α and λ and used the grid search strategy to find the optimal values for these parameters.

The output tables shown in [Figure 7.15](#07_002.html#f7.15), [Figure 7.16](#07_002.html#f7.16), and [Figure 7.17](#07_002.html#f7.17) will be generated.

[![Statistics Table: Logistic Regression Model with Validation and Parameter Selection](bilderklein/klein07_015.png)](img-f7.15.html) 

**Figure 7.15**    Statistics Table: Logistic Regression Model with Validation and Parameter Selection

###### Note

The average accuracy of the logistic regression model is 0.761896, or approximately 76.2%. This average accuracy is based on accuracy values from 2 cycles of validation, each using 4-fold cross-validation.

The variance between accuracy values is 0.000474825, which is quite low compared to the mean accuracy.

[![Optimal Parameter Table: Logistic Regression Model with Validation and Parameter Selection](bilderklein/klein07_016.png)](img-f7.16.html) 

**Figure 7.16**    Optimal Parameter Table: Logistic Regression Model with Validation and Parameter Selection

###### Note

The optimal parameter selection process identified 0.1 as the value of α and 0.002 as the value of λ. These values were selected by the algorithm through the grid search technique based on the set of values provided in the parameter table.

[![Coefficient Table: Logistic Regression Model with Validation and Parameter Selection](bilderklein/klein07_017.png)](img-f7.17.html) 

**Figure 7.17**    Coefficient Table: Logistic Regression Model with Validation and Parameter Selection

###### Note

Except for three category values, all other categories have p values that are less than 0.05. The A410 category of PURPOSE (which is a mix of various categories) is the only category value that is not significant even with a cutoff of 0.1 for the p value.

However, if you remove the attribute PURPOSE, the accuracy drops, since most categories of PURPOSE are significant.

The intercept term has p value between 0.05 and 0.1, which is due to the lack of data for the group it represents (with value 0 for all attributes, for categorical attributes they are the grouped with 0 coefficient). However, we go ahead with this.

Ultimately, there’s not much room for improvement with this model, so this model is our final logistic regression model! The optimal values for α and λ are 0.1 and 0.002, respectively.

Now that we’ve obtained our final logistic regression model, let’s turn to refining our SVM model from earlier.

#### Refinement of Support Vector Machine (SVM) Model

Now, let’s see how our SVM model behaves. The SQL code shown in [Listing 7.6](#07_002.html#l7.6) runs the validation and optimal parameter selection process for our SVM model.

```
CREATE LOCAL TEMPORARY COLUMN TABLE "#temp_param" ("PARAM_NAME" VARCHAR(256), "INT_VALUE" INTEGER, "DOUBLE_VALUE" DOUBLE,"STRING_VALUE" VARCHAR(1000));
-- Parameters for training
INSERT INTO "#temp_param" VALUES ('TYPE', 1, NULL, NULL);
INSERT INTO "#temp_param" VALUES ('KERNEL_TYPE', 2, NULL, NULL); 
INSERT INTO "#temp_param" VALUES ('HAS_ID', 0, NULL, NULL);
INSERT INTO "#temp_param" VALUES ('PROBABILITY',1,NULL,NULL);
INSERT INTO "#temp_param" VALUES ('DEPENDENT_VARIABLE', NULL, NULL,'DEFAULTER');
-- Parameters for validation and parameter selection
INSERT INTO "#temp_param" VALUES ('SVM_C_VALUES', NULL, NULL, '{30, 50, 80, 100 }');
INSERT INTO "#temp_param" VALUES ('RBF_GAMMA_VALUES', NULL, NULL, '{0.01, 0.05, 0.25, 0.5, 1, 2, 4, 8, 16, 32}');
INSERT INTO "#temp_param" VALUES ('RESAMPLING_METHOD', NULL, NULL,  
'stratified_cv');
INSERT INTO "#temp_param" VALUES ('FOLD_NUM', 4, NULL, NULL);
INSERT INTO "#temp_param" VALUES ('REPEAT_TIMES', 2, NULL, NULL);
INSERT INTO "#temp_param" VALUES ('PARAM_SEARCH_STRATEGY', NULL, NULL, 'grid');
INSERT INTO "#temp_param" VALUES ('EVALUATION_METRIC', NULL, NULL, 'ACCURACY');
INSERT INTO "#temp_param" VALUES ('PROGRESS_INDICATOR_ID', NULL, NULL, 'PII');
-- Call the SVM procedure
CALL _SYS_AFL.PAL_SVM(ML_USECASE.CREDIT_RISK_DATA_MODIFIED,"#temp_param",?,?,?);
```

**Listing 7.6**    SQL Code for the SVM Model with Validation and Optimal Parameter Selection

The procedure will generate the output tables shown in [Figure 7.18](#07_002.html#f7.18), [Figure 7.19](#07_002.html#f7.19), and [Figure 7.20](#07_002.html#f7.20).

[![Model Table: SVM with Validation and Parameter Selection](bilderklein/klein07_018.png)](img-f7.18.html) 

**Figure 7.18**    Model Table: SVM with Validation and Parameter Selection

[![Optimal Parameter Table: SVM with Validation and Parameter Selection](bilderklein/klein07_019.png)](img-f7.19.html) 

**Figure 7.19**    Optimal Parameter Table: SVM with Validation and Parameter Selection

###### Note

The optimal parameter selection process identified 0.05 as the value of Gamma and 100 as the value of C. These values were selected by the algorithm through the grid search technique based on the set of values provided in the parameter table.

###### Note

The average accuracy of this model is 0.710812, or approximately 71.1%. This average accuracy is based on accuracy values from 2 cycles of validation, each using 4-fold cross-validation.

The variance among the accuracy values is 0.000649577, which is quite low compared to the mean accuracy.

[![Statistics Table: SVM with Validation and Parameter Selection](bilderklein/klein07_020.png)](img-f7.20.html) 

**Figure 7.20**    Statistics Table: SVM with Validation and Parameter Selection

This model was fitted with all attributes in the modified dataset. Therefore, even if a separating hyperplane is not available at a lower dimension, it is available at a higher dimension. Still, in our final attempt, let’s see how the SVM model behaves with respect to the attributes selected in our final logistic regression model. The code shown earlier in [Listing 7.6](#07_002.html#l7.6) just needs the following line added to indicate the selected attributes:

```
INSERT INTO "#temp_param" VALUES ('SELECTED_FEATURES', NULL, NULL, 'ACCOUNT_BALANCE,LN_CREDIT_DURATION,PREV_CREDIT_PAYMENT_STATUS,PURPOSE,VALUE_SAVINGS_STOCKS,CURRENT_EMPL_LENGHT,SEX_MARITAL_STATUS,CONCURRENT_CREDIT');
```

The optimal parameter and statistics tables for this iteration are shown in [Figure 7.21](#07_002.html#f7.21) and [Figure 7.22](#07_002.html#f7.22), respectively.

[![Optimal Parameter Table: SVM Model, Second Iteration, with Optimal Parameter Selection](bilderklein/klein07_021.png)](img-f7.21.html) 

**Figure 7.21**    Optimal Parameter Table: SVM Model, Second Iteration, with Optimal Parameter Selection

[![Statistics Table: SVM Model, Second Iteration, with Optimal Parameter Selection](bilderklein/klein07_022.png)](img-f7.22.html) 

**Figure 7.22**    Statistics Table: SVM Model, Second Iteration, with Optimal Parameter Selection

Notice that using these parameters does not improve the average accuracy of the SVM model compared to the previous iteration of the model. Therefore, we’ll use the SVM model with all attributes as the final model, with its average accuracy of 0.711.

#### Conclusion and Final Model Selection

The final logistic regression model provides an average accuracy 0.762, or 76%, whereas the final SVM model provides an average accuracy of 0.711, or 71%.

Based on the average accuracy, we’ll select the logistic regression model as our final model.

Although 76% accuracy may not seem impressive, this dataset is well known, and much research has been conducted on this data. Most advanced methods fail to achieve even 80% accuracy on this dataset. You can still improve the accuracy of the model, but advanced concepts in machine learning and statistics will be required, both of which are beyond the scope of this book.

Our example also demonstrates that you cannot always expect very high accuracy in real life. The intrinsic nature of the data may prevent you from achieving “100% accuracy.”

If you run this exercise yourself with the codes we’ve provided in this chapter, you may receive slightly different results. This difference is because, each time the algorithm picks up different sample data for training and validation, results will differ slightly. Even executing the same code twice can give slightly different results because the sample datasets themselves will be different.

### 7.2.5    Model Deployment

Once you’ve finalized the model, you can deploy the model into a productive environment to operationalize it. Note that you won’t train, validate, and fine-tune the model repeatedly in production if using a static model. However, depending on your business requirement, you might need to provide additional functionalities on the final model. For instance, in our use case, we must predict whether a new loan applicant will default or repay the loan, based on the final model. You should also store the final model for future reference. In this section, we’ll focus on the four main steps you’ll need to perform deploy your model into production and continue to use your model.

#### Step 1: Store the Input and Output Data and the Final Model for Future Reference

The code shown in [Listing 7.7](#07_002.html#l7.7) creates the parameter table and other output tables in the database.

```
-- Create the parameter table
CREATE COLUMN TABLE "ML_USECASE"."LR_PARAM" ("PARAM_NAME" VARCHAR(256),  
"INT_VALUE" INTEGER, "DOUBLE_VALUE" DOUBLE,"STRING_VALUE" VARCHAR(1000));
-- Insert the parameters
INSERT INTO ML_USECASE.LR_PARAM VALUES ('CLASS_MAP0', NULL, NULL, '0');
INSERT INTO ML_USECASE.LR_PARAM VALUES ('CLASS_MAP1', NULL, NULL,'1'); 
INSERT INTO ML_USECASE.LR_PARAM VALUES ('METHOD', 2, NULL, NULL);
INSERT INTO ML_USECASE.LR_PARAM VALUES ('STAT_INF', 1, NULL, NULL);
INSERT INTO ML_USECASE.LR_PARAM VALUES ('DEPENDENT_VARIABLE',NULL,NULL,'DEFAULTER');
-- Insert the variables of final model
INSERT INTO ML_USECASE.LR_PARAM VALUES ('SELECTED_FEATURES', NULL, NULL, 'ACCOUNT_BALANCE,LN_CREDIT_DURATION,PREV_CREDIT_PAYMENT_STATUS,PURPOSE,VALUE_SAVINGS_STOCKS,CURRENT_EMPL_LENGHT,SEX_MARITAL_STATUS, 
CONCURRENT_CREDIT');
-- Insert the optimal value of tuning parameters obtained in the final model
INSERT INTO ML_USECASE.LR_PARAM VALUES ('ENET_LAMBDA', NULL, 0.002, NULL);
INSERT INTO ML_USECASE.LR_PARAM VALUES ('ENET_ALPHA', NULL, 0.1, NULL);

-- Create the output tables
CREATE COLUMN TABLE "ML_USECASE"."LR_COEFFICIENT" 
("VARIABLE_NAME" NVARCHAR(1000),
 "COEFFICIENT" DOUBLE,
 "T_VALUE" DOUBLE,
 "P_VALUE" DOUBLE);

CREATE COLUMN TABLE "ML_USECASE"."LR_PMML" 
("ROW_INDEX" INTEGER, 
 "MODEL_CONTENT" VARCHAR(5000));

CREATE COLUMN TABLE "ML_USECASE"."LR_STATISTICS" 
("STAT_NAME" NVARCHAR(256),
 "STAT_VALUE" NVARCHAR(1000));
```

**Listing 7.7**    SQL Code to Create Parameter and Output Tables

###### Note

Only the parameters relevant for the final model have been inserted.

The final set of attributes is specified through the parameter SELECTED\_FEATURES.

The optimal parameter values from the final model (shown earlier in [Figure 7.16](#07_002.html#f7.16)) have included as the values for λ and α.

Next, you’ll need to create a stored procedure to call the SAP HANA PAL procedure using these input and output tables. This part is easy and straightforward, so we won’t describe these steps here.

#### Step 2: Create a Stored Procedure for Prediction Based on the Final Model

Next, you’ll use the SAP HANA PAL procedure PAL\_LOGISTIC\_REGRESSION\_PREDICT to make predictions on the data of new applicants. Let’s assume that data about new applicants includes all 20 attributes from our original dataset. Recall that we performed some data transformations before using the training data in our model, so you’ll need to apply the same transformations on the data of new applicants before using this new data for predictions. If the data volume of new applicants is low, you can implement this task in the procedure. Otherwise, a new table must be created for the transformed data and then used as a data table in the prediction process. Also, you’ll need an ID column in the new dataset so that you can map each new applicant with their predicted values.

The code shown in [Listing 7.8](#07_002.html#l7.8) creates the parameter and output tables for the prediction run.

```
CREATE COLUMN TABLE ML_USECASE.LR_PARAM_PREDICT ("PARAM_NAME" VARCHAR(256), 
"INT_VALUE" INTEGER, "DOUBLE_VALUE" DOUBLE,"STRING_VALUE" VARCHAR(1000));
INSERT INTO ML_USECASE.LR_PARAM_PREDICT VALUES ('CLASS_MAP0', NULL, NULL, '0');
INSERT INTO ML_USECASE.LR_PARAM_PREDICT VALUES ('CLASS_MAP1', NULL, NULL, '1'); 

CREATE TABLE ML_USECASE.LR_SCORE ("ID" NVARCHAR(5),
SCORE DOUBLE, CLASS VARCHAR(1));
```

**Listing 7.8**    SQL Code to Create Parameter and Output Tables

The code shown in [Listing 7.9](#07_002.html#l7.9) creates the stored procedure and runs the prediction model.

```
CREATE PROCEDURE ML_USECASE.PROC_LOGISTIC_REGRESSION_PREDICT()
LANGUAGE SQLSCRIPT
SQL SECURITY INVOKER
DEFAULT SCHEMA "ML_USECASE"
AS
BEGIN
-- Data Table - Create a table variable TV_INPUT_DATA with data from the table CREDIT_RISK_DATA_NEW which contains new data
TV_INPUT_DATA = SELECT
"CUST_ID", 
"ACCOUNT_BALANCE",
LN("CREDIT_DURATION") AS "LN_CREDIT_DURATION",
(CASE WHEN "PREV_CREDIT_PAYMENT_STATUS" = 'A31' THEN 'A30' 
WHEN "PREV_CREDIT_PAYMENT_STATUS" = 'A33' THEN 'A32' 
ELSE "PREV_CREDIT_PAYMENT_STATUS" END) AS "PREV_CREDIT_PAYMENT_STATUS",
(CASE WHEN "PURPOSE" IN ('A44', 'A45') THEN 'A42' 
WHEN "PURPOSE" IN ('A46', 'A47', 'A48', 'A49') THEN 'A410' 
ELSE "PURPOSE" END) AS "PURPOSE",
(CASE WHEN "VALUE_SAVINGS_STOCKS" = 'A62' THEN 'A61' 
WHEN "VALUE_SAVINGS_STOCKS" IN ('A64', 'A65') THEN 'A63'
ELSE "VALUE_SAVINGS_STOCKS" END) AS "VALUE_SAVINGS_STOCKS",
(CASE WHEN "CURRENT_EMPL_LENGHT" = 'A72' THEN 'A71'
WHEN "CURRENT_EMPL_LENGHT" IN ('A74', 'A75') THEN 'A73'
ELSE "CURRENT_EMPL_LENGHT" END) AS     "CURRENT_EMPL_LENGHT",
(CASE WHEN "SEX_MARITAL_STATUS" = 'A92' THEN 'A91'
WHEN "SEX_MARITAL_STATUS" = 'A94' THEN 'A93'
ELSE "SEX_MARITAL_STATUS" END) AS "SEX_MARITAL_STATUS",
(CASE WHEN "CONCURRENT_CREDIT" = 'A142' THEN 'A141'
ELSE "CONCURRENT_CREDIT" END) AS "CONCURRENT_CREDIT"
FROM "ML_USECASE"."CREDIT_RISK_DATA_NEW";
-- Parameter Table - Create a table variable TV_PARAM with data from LR_PARAM_PREDICT
TV_PARAM = SELECT * FROM LR_PARAM_PREDICT;
-- Coefficient Table - Get the coefficients from Coefficient table of the final model
TV_COEFFICIENT = SELECT * FROM LR_COEFFICIENT;
-- Call the PAL Procedure
CALL _SYS_AFL.PAL_LOGISTIC_REGRESSION_PREDICT(:TV_INPUT_DATA,:TV_COEFFICIENT, 
:TV_PARAM, OUT_FITTED);
-- Output Table - Truncate the output table and insert output data into the table
TRUNCATE TABLE LR_SCORE;
INSERT INTO LR_SCORE SELECT * FROM :OUT_FITTED;
END;
CALL ML_USECASE.PROC_LOGISTIC_REGRESSION_PREDICT();
```

**Listing 7.9**    SQL Code to Create the Stored Procedure for the Prediction Model

###### Note

The new data is available in table CREDIT\_RISK\_DATA\_NEW.

The required data transformation is implemented in the procedure, assuming the volume of new data is fairly small.

Since we haven’t removed any records from the new data using a WHERE clause, the model should make predictions for all applicants. We used the WHERE clause during training to prevent outliers from impacting the model.

The output from the prediction process shows the probability that an applicant will default (category value 1 of the dependent variable) and the likely class the applicant belongs to. [Figure 7.23](#07_002.html#f7.23) shows a sample output of the prediction.

[![Sample Output after Running the Prediction](bilderklein/klein07_023.png)](img-f7.23.html) 

**Figure 7.23**    Sample Output after Running the Prediction

###### Interpretation of Prediction Results

The procedure calculates the probability of defaulting for each new applicant based on the fitted model. That probability is displayed in the SCORE column.

Then, based on this probability, applicants are categorized into one of two classes: 1 for defaulters and 0 for non-defaulters. The result of this classification task is shown in the CLASS column.

Usually, a 0.5 cutoff is used for this classification step. If the probability of defaulting is greater than 0.5, then the applicant is classified as a defaulter and put into class 1; otherwise, the applicant is put into class 0.

Depending on the scenario, you may use a different cutoff value. For example, if a potential defaulter predicted as a non-defaulter costs more, then you can lower the cutoff, so that borderline cases are classified as defaulters.

#### Step 3: Deploy the Code into Production

In this step, you’ll move the final set of database tables and procedures into your production environment. This process will follow the existing practices of the client.

#### Step 4: Operationalize and Monitor the Performance of the Model

Finally, you can operationalize the model in production. You’ll still need to watch the performance of the model from time to time. After a certain period, if you find that the model is no longer effective, perhaps due to changes in the nature of the data, you may need to fine-tune the model or remodel it again.

### 7.2.6    Interpretation and Displaying Results

The interpretation of a model in business terms is a success factor for machine learning projects. Discovering hidden relationships helps business users make informed strategic decisions. For example, if customers with a specific type of loan are unlikely to default, the bank may decide to promote that loan scheme.

However, not all machine learning algorithms provide nice interpretations and instead are more of a black box. Fortunately, the logistic regression model provides nice interpretations through the model’s coefficients. Let’s look at the coefficients of the final model (shown earlier in [Figure 7.17](#07_002.html#f7.17)) and see what types of conclusions we may draw from this information.

First, we can see that the model rejected some attributes like age, guarantors, apartment type, and foreign worker, so these attributes have little to no influence on whether an applicant will default.

What can we say about the influence of attributes included in the model, and can we somehow quantify this influence? It’s time for a little bit of math!

Recall from [Chapter 2](#02_001.html#h2) that a logistic regression fits a model with the following equation:

log(p / (1 – p)) = β[0] + β[1]X[1] + β[2]X[2] + … + β[n]X[n]

X[1,] X[2, …], X[n] are independent variables, β[0,] β[1],…[,] β[n] are the coefficients (constants), and p = P(Y = 1 | X[1], X[2], …X[n]). In this case, the probability of the dependent variable equals 1 and represents the probability of belonging to class 1.

The equation p / (1 – p) calculates something called the odds, which is another way of expressing the likelihood of an event. In our case, we are calculating the odds that an applicant will default. If the odds that an applicant will default is 4 (in other words, 4:1), this applicant’s likelihood of defaulting is 4 times greater than his or her likelihood of repaying the loan. It follows that:

p / (1 – p) = 4 => p = 4 – 4p => 5p = 4 => p = 4/5 = 0.8

In other words, the probability of defaulting is 0.8, or 80%, and the probability of repaying is (1 – p) = 0.2, or 20%.

Now, consider the attribute PREV\_CREDIT\_PAYMENT\_STATUS, with its three categories A30, A32, and A34 (after we merged a few categories of this attribute in our modified data). The model splits this categorical variable into two binary variables: PREV\_CREDIT\_PAYMENT\_STATUS\_PAL\_\_DELIMIT\_\_A32 and PREV\_CREDIT\_PAYMENT\_STATUS\_PAL\_\_DELIMIT\_\_A34. Let’s represent these variables as X[1] and X[2], respectively. The variable PREV\_CREDIT\_PAYMENT\_STATUS\_PAL\_\_DELIMIT\_\_A30 is just a dummy variable to represent the category A30 and is not used in modeling. The categories are mapped against X[1] and X[2] with the binary coding shown in [Table 7.3](#07_002.html#t7.3).

 
| Category Value || Value of X[1] || Value of X[2] |
| --- | --- | --- |
| A30 || 0 || 0 |
| --- | --- | --- |
| A32 || 1 || 0 |
| A34 || 0 || 1 |

**Table 7.3**    Binarization of Categorical Attribute PREV\_CREDIT\_PAYMENT\_STATUS

Note that X[1] is the indicator variable of the category A32 and X[2] is the indicator variable of the category A34. As per the final model, the coefficients of the variables X[1] and X[2] are –0.4656559 and –1.0470058 (both rounded to 7 decimal places). The equation can be written as:

log(p/(1 – p)) = β[0] + (–0.4656559) X[1] + (–1.0470058)X[2]\+ β[3]X[3] + …+ β[n]X[n]

Now, consider two applicants, both having similar profiles except that one candidate belongs to category A30 and the other to A32. Let p[1] and p[2] represent each of their probability to default. Then:

log(p[1]/(1 – p[1])) = β[0] + (–0.4656559).0 + (–1.0470058).0+ β[3]X[3] + …+ β[n]X[n] (Note that, for group A30, we used X[1] = 0 and X[2] = 0.)

log(p[2]/(1 – p[2])) = β[0] + (–0.4656559).1 + (–.0470058).0+ β[3]X[3] + …+ β[n]X[n] (Note that, for group A32, we used X[1] = 1 and X[2] = 0.)

Subtracting the second equation from the first equation, we get the following calculations:

log(p[1]/(1 – p[1])) – log(p[2]/(1 – p[2])) = 0.4656559

\=> log((p[1]/(1 – p[1])) / (p[2]/(1 – p[2]))) = 0.4656559 \[since log(a) – log(b) = log(a/b)\]

\=> (p[1]/(1 – p[1])) / (p[2]/(1 – p[2])) = e^(0.4656559) = 1.5930587 ~ 1.6

Note that the left side represents the ratio of the odds of these two applicants (in favor of defaulting) and is called the odds ratio. So, from these calculations, we can conclude that, when all other attributes are same, odds in favor of a person from category A30 will default/odds in favor of a person from category A32 will default = 1.6.

In other words, the odds in favor of a person from category A30 defaulting is 60% higher than the odds in favor of a person from category A32 defaulting. This percentage gives you a relative measure of the chances of defaulting for applicants from different categories of the same attribute. People in category A30 have a higher probability of defaulting compared to category A32, when other profiles are same.

###### Note

For two different categories A and B of the same categorical variable, we have the following relationship:

*   Probability to default in category A > (or = or <) Probability to default in category B if and only if ...
    
*   Odds in favor of default in category A > (or = or <) Odds in favor of default in category B, i.e. if and only if odds ratio of categories A to B > (or = or <) 1, respectively.
    

If p[1] = probability to default in category A, p[2] = probability to default in category B, then the odds ratio is (p[1]/(1 – p[1])) / (p[2]/(1 – p[2])). Now, the following calculations are true:

p[1] > (or = or <) p[2]

⬄ p[1] – p[1]p[2] > (or = or <) p[2] – p[1]p[2]

⬄ p[1](1 – p[2]) > (or = or <) p[2](1 – p[1])

⬄ p[1]/(1 – p[1]) > (or = or <) p[2]/(1 – p[2]) \[since (1 – p[1]), (1 – p[2]) are > 0\]

⬄ (p[1]/(1 – p[1])) / (p[2]/(1 – p[2])) > (or = or < ) 1

The logistic regression coefficients quantify the effects of different categories in terms of odds ratio, but it also provides the order of the effects in terms of their probability.

###### Note

This result shows an interesting observation on loan applicants. Let’s look at the new definition of categories A30 and A32, after we merged a few categories during the data transformation:

*   A30: No credits taken/all credits paid back duly or all credits at this bank paid back duly.
    
*   A32: Existing credits paid back duly till now or delay in paying off in the past.
    

At first, it looks like applicants in the A30 category are less likely to default compared to applicants in A32. However, the model shows just the opposite. Is there a contradiction or an incorrect conclusion?

No, this what the data shows. There might be a good business reason behind it. Category A30 also includes first-time loan applicants (no credit taken in the past), and perhaps these applicants default more. Category A32 includes applicants who delayed paying off but did not default. Thus, overall, this group has less defaulters.

The graph of the average number of defaulters in the transformed data is shown in [Figure 7.24](#07_002.html#f7.24), which confirms our suspicions.

This scenario is a good example of how machine learning can reveal hidden relationships that may seem otherwise contradictory!

In the same way, the odds ratio in favor of default in categories A32 and A34 is e^((-0.4656559 + 1.0470058)) = 1.78845 ~ 1.8. So, if all other attributes are the same, the people in category A32 have an 80% higher odds of defaulting compared to category A34. Therefore, the people in category A32 have a higher probability of defaulting compared to the people in A34. We can make similar conclusions for other categorical attributes as well.

[![Average of DEFAULTER against New Categories of PREV\_CREDIT\_PAYMENT\_ STATUS](bilderklein/klein07_024.png)](img-f7.24.html) 

**Figure 7.24**    Average of DEFAULTER against New Categories of PREV\_CREDIT\_PAYMENT\_ STATUS

Let’s now look at the continuous attribute LN\_CREDIT\_DURATION and see what interpretation we can make based on the associated coefficient 0.9439086 (rounded to 7 decimal places). Suppose we want to understand the odds ratio of 2 applicants having same profiles except a credit duration of 20 weeks and 10 weeks, respectively. Let’s say their probability of defaulting is p[1] and p[2], respectively. Note that we used log(CREDIT\_DURATION) as the transformed attribute in the model. Then, putting these values into the equation of the model and subtracting them, we get the following equation:

log((p[1]/(1 – p[1])) / (p[2]/(1 – p[2]))) = 0.9439086(log20 – log10)

\= 0.9439086log(20/10) = 0.9439086log(2) = log(2^(0.9439086)) = log(1.923733)

From the above equation, we get the following calculation:

(p[1]/(1 – p[1])) / (p[2]/(1 – p[2])) = 1.923733

Therefore, a person who has taken a loan of 20 weeks has around 92% higher odds of being a defaulter, compared to a person who has taken a loan of 10 weeks, when all other attributes are same.

Note that there is nothing special about the values 20 and 10; we eventually divided them to get 2. The result will be the same if you want to see effect of doubling the credit duration. In other words, with all other profiles same, doubling the credit duration will increase the odds in favor of defaulting by 92%.

You can and should present these observations based on the model to your business users. This information will help them understand the hidden relationships in the data and make good decisions accordingly.

###### Note

When interpreting logistic regression coefficients, the following facts about coefficients are true:

*   For categories A and B of a categorical attribute:
    
    Odds ratio of category A to category B = exp(coefficient of category A – coefficient of category B)
    
*   For a continuous variable:
    
    Odds ratio of value (x + c) to x = exp(c.(coefficient of the variable))
    

Where exp(a) = e^a and all other attributes are the same.

These conclusions are based on assumptions that, while estimating the odds ratio from coefficients, all other attributes have same value; in other words, we can nullify the effect of other attributes. But this is not always the case, and you may need to statistically adjust the estimated odds ratio. Similar situations may arise in the presence of interactions between predictors.

## 7.3    Summary

Our predictive analysis use case, based on German credit data, shows how you can approach a machine learning exercise in real life. The first step is to understand the business requirement and interpret it from a machine learning perspective. Then, more insights into the business and the data will help you to get a clear picture of how different factors might influence the object of interest. Often, simple data visualization and exploration techniques can reveal a lot about the patterns and underlying relationships in your data. These observations can play key role in feature engineering and preparing the final data. The next step is to identify suitable machine learning algorithms and then build multiple versions of these models with these algorithms. These models often require iterative approach to fine-tune and validate. Once the validated and tuned models are obtained, they are compared against statistics like accuracy and F1 score, and the final model is selected for deployment. The success of a machine learning project also depends on how the machine learning application is operationalized, interpreted, and monitored after being deployed into production.

# 8    SAP AI Business Services

This chapter is all about SAP AI Business Services, which are especially crafted to serve several business processes common across multiple industries, enrich the customer experience, and result in faster and better return on investment (ROI). In this chapter, you’ll learn about these services including their technical specifications, the architecture, and the applicability of these services across enterprise business processes.

The voyage to becoming an intelligent enterprise today is creating a new world of previously concealed opportunities. Enterprises are not only looking for an intelligent platform but may also demand intelligent applications with embedded and/or reusable machine learning microservices. Especially for situations where time is a crucial factor and impressions must be striking, enterprises are ready to bank on usable machine learning capabilities that can deliver generic business functionalities to automate and optimize business processes. In this context, enterprise clients are especially attracted to modular and application programming interface (API)-based architectures that can be easily integrated across various processes and can also generate immediate business value. But, how can we unlock all these functionalities? Luckily, SAP AI Business Services provide a wide range of predelivered applications and services that not only automate and optimize enterprise business processes but also enrich the user experience across the intelligent suite. SAP AI Business Services are offered as part of SAP’s AI portfolio along with SAP Data Intelligence, SAP Conversational Artificial Intelligence (SAP Conversational AI), SAP Intelligent Robotic Process Automation (SAP Intelligent RPA), and other intelligent applications on SAP Cloud Platform, as shown in [Figure 8.1](#08_001.html#f8.1).

SAP AI Business Services make the ingestion of AI capabilities into business processes hassle free by introducing a set of machine learning-driven business services especially catered to meet specific pain points across multiple business processes. Not limited to a single application, these services are more reusable and generic in nature. SAP AI Business Services can fuel your journey to the intelligent enterprise with machine learning capabilities out of the box that can be applied to multiple business processes as well as combined with other intelligent technologies or SAP solutions without needing to be a data science expert. SAP AI Business Services are available as simple Representational State Transfer (REST)-based APIs, and SAP’s value-based pricing model makes these APIs usage easy to understand and consume. But, enough introduction. Let’s now, in our next section, explore the services offered by SAP AI Business Services and describe their features.

[![SAP’s Artificial Intelligence Portfolio](bilderklein/klein08_001.png)](img-f8.1.html) 

**Figure 8.1**    SAP’s Artificial Intelligence Portfolio

## 8.1    Overview

SAP AI Business Services are a rich collection of services that are reusable and generic in nature and capable of solving problems that are not specific to any business process, unlike fully fledged business applications with limited scope. SAP AI Business Services run on historical business data and are capable of addressing a wide range of business challenges, including document processing, information extraction, invoice processing, unstructured data processing, etc. These processes are typically manual and repetitive in nature and automating these processes can ultimately help your organization and your employees focus time and effort more on strategic and value-creating work. As shown in [Figure 8.2](#08_001.html#f8.2), the SAP AI Business Services portfolio comprises of the following key services:

*   Document classification service  
    This service is powered by a set of capabilities for analyzing and classifying PDF documents based on customized and pretrained classification models included in the service.
    
*   Document information extraction service  
    This service can process various documents and extract contents from the header and table sections of documents like invoices or payment notes while ensuring that invoices and payables match.
    
*   Business entity recognition service  
    This service is a pretrained machine learning service that extracts entities from text documents automatically.
    
*   Data attribute recommendation service  
    This service facilitates different aspects of master data management, including the creation, alignment, and maintenance of data attributes while reducing error.
    
*   Invoice object recommendation service  
    This service can recommend a general ledger account for new invoice line items based on historical invoice data.
    
*   Service ticket intelligence service  
    This service is essential for building a self-driven customer service support system enabled by machine learning.
    

[![SAP AI Business Services Catalog](bilderklein/klein08_002.png)](img-f8.2.html) 

**Figure 8.2**    SAP AI Business Services Catalog

Beyond leveraging these services as standalone applications, the power of SAP AI Business Services further lies in their ability to combine with other key components of the SAP machine learning portfolio including SAP Data Intelligence, SAP Conversational AI, and SAP Intelligent RPA to build fully fledged, intelligent enterprise applications.

Now, we’ll dive deeply into each of these business services to learn how these services actually work.

## 8.2    Document Classification

Content in this digital era can originate in variety of formats from various sources. Text-based documents are among the richest sources of data; whether in the form of a support ticket, a user review, an email, an invoice, or a contract, all of these documents contain valuable information that must be processed to find valuable insights. Where a traditional business application or manual processing might scramble to process these unstructured documents, machine learning can handle this kind of data with ease. In this context, a machine learning-based document classification process is primarily driven by the tagging of documents with one or more predefined category labels. A classifier is trained on a dataset so that any new document can be assigned a category based on the given training, ultimately making the processing of large amounts of business documents more efficiently. [Figure 8.3](#08_002.html#f8.3) shows a quick demonstration of a machine learning-based document classification process using the character grid (or chargrid) technique, including text extraction with word and boxes using OCR.

[![ChargridChargrid in Action behind Document Classification](bilderklein/klein08_003.png)](img-f8.3.html) 

**Figure 8.3**    Chargrid in Action behind Document Classification

Traditional natural language processing (NLP)-based document processing usually disregards the 2D layout of documents and only focuses on processing the text contents in a sequential or linear fashion. In contrast, a computer vision technique focuses on a document’s pixels, treating the document as an image, to retain its layout. However, this technique ultimately loses the textual content. But the chargrid technique is a perfect blend of NLP and computer vision methods and easily overcomes the shortfalls of both these individual methods by making use of a 2D grid of characters to retain the 2D layout structure of documents as well as taking care of the textual content. The chargrid method is a giant leap in recognizing and processing text contents from tabular structures. Chargrid not only recognizes the characters of the text through optical character recognition (OCR) but also interprets the contextual information, for example, invoice numbers, invoice dates, etc., which are common in most SAP-relevant documents. Overall, the character grid (chargrid) method or technique is the mainstay behind all the machine learning based-document processing services offered by the SAP AI Business Services portfolio.

###### Note

According to the EMNLP 2018 paper, a chargrid is a novel representation of a document that preserves its 2D layout. A chargrid can be constructed from character boxes, which are bounding boxes that each surround a single character somewhere on a given document’s page. For more granular detail on the chargrid technique and associated research, refer to the published paper from Cornell University available at [https://arxiv.org/abs/1809.08799](https://arxiv.org/abs/1809.08799).

In contrast, a 2D character grid is a unique method of finding all the occurrences of a specific word in a given 2D grid of characters. A word can be matched in all 8 directions from any point. For more details about 2D character grids, refer to [https://www.geeksforgeeks.org/search-a-word-in-a-2d-grid-of-characters/](https://www.geeksforgeeks.org/search-a-word-in-a-2d-grid-of-characters/).

Now, to recap our discussion of document classification, with this service, you can classify business documents based on customer-specific machine learning models trained on a subset of already classified (labeled) documents. The model use case shown [Figure 8.4](#08_002.html#f8.4) demonstrates how the document classification service classifies business document(s) at runtime based on its training with examples of previously classified documents:

 
| 1  || Request |
| --- | --- |
| 2  || Invoice |
| 3  || Complaint |
| 4  || Dunning letters |

[![Document Classification ProcessDocument classification process](bilderklein/klein08_004.png)](img-f8.4.html) 

**Figure 8.4**    Document Classification Process

The service comes with two categories of endpoints, which are supported by the base URL /document-classification/v1, for example:

*   Training endpoints primarily take care of creating, deleting, and fetching datasets and training documents.
    
*   Inference endpoints take care of processing statuses, posting classifications, and fetching the results of the classification.
    

We won’t cover the Document Classification API specification in much detail, since the relevant documentation is well developed on the SAP Help Portal and is available at [https://help.sap.com/viewer/product/DOCUMENT\_CLASSIFICATION/SHIP/en-US](https://help.sap.com/viewer/product/DOCUMENT_CLASSIFICATION/SHIP/en-US).

To wrap up this section, some of the key benefits of the document classification service from the perspective of the intelligent enterprise include the following:

*   An automated document classification process delivers classification decisions based on how the underlying machine learning model has been trained by document type (for instance, invoice, collection letter, or complaint) and reduces the manual effort required for, and reduces potential errors in, the classification of business documents.
    
*   Depending on its training and further usage, the document classification service gradually learns from every single classification it delivers, and accuracy improves over time.
    
*   Additionally, the document classification service also speeds up overall document processing by channeling documents based on their type.
    

The document classification service is available on SAP Cloud Platform on Cloud Foundry under the Cloud Platform Enterprise Agreement (CPEA) and is included as part of SAP AI Business Services. The document classification service also supports integration with SAP S/4HANA document management. Let’s see the service in action in the next section to underline what you’ve read so far.

### 8.2.1    Test Run of the Document Classification Service

Luckily, the document classification service is available with a trial account for SAP Cloud Platform on Cloud Foundry. However, you’ll need to fulfill some prerequisites regarding entitlements and set up the service. Buckle up!

First, log on to your SAP Cloud Platform Cloud Foundry trial account and navigate to your designated subaccount. In our case, our preference is Europe (Frankfurt) – AWS Region since SAP AI Business Services are currently only enabled in this region. If you have subaccount on another region, don’t worry—just create a new subaccount in this region. Your subaccount on your SAP Cloud Platform Cloud Foundry trial account should look similar to the screen shown in [Figure 8.5](#08_002.html#f8.5).

[![SAP Cloud FoundryCloud Foundrysubaccount Subaccount: Space](bilderklein/klein08_005.png)](img-f8.5.html) 

**Figure 8.5**    SAP Cloud Foundry Subaccount: Space

Once your subaccount and space are ready, you’ll need to add the necessary services by navigating to the entitlements screen. As shown in [Figure 8.5](#08_002.html#f8.5), click on the Entitlements menu item on the left, which will navigate you to the screen shown in [Figure 8.6](#08_002.html#f8.6).

[![Cloud Foundry Subaccount: Entitlements](bilderklein/klein08_006.png)](img-f8.6.html) 

**Figure 8.6**    Cloud Foundry Subaccount: Entitlements

Notice that the document classification service is not included in the table on the entitlements screen. Add the service by clicking the Configure Entitlements button shown in [Figure 8.6](#08_002.html#f8.6). The Add Service Plans button will appear in the top-right corner of the table showing existing entitlements, as shown in [Figure 8.7](#08_002.html#f8.7).

[![Add a Service Plan](bilderklein/klein08_007.png)](img-f8.7.html) 

**Figure 8.7**    Add a Service Plan

Clicking Add Service Plans launches the wizard shown in [Figure 8.7](#08_002.html#f8.7). On the left, you can search for any service. In our case, we’ll enter “Documentation Classification” into the search field, as shown in [Figure 8.8](#08_002.html#f8.8).

[![Adding a Service PlanService plan](bilderklein/klein08_008.png)](img-f8.8.html) 

**Figure 8.8**    Adding a Service Plan

Once you find the service, select and add the default service plan offered on the SAP Cloud Platform Cloud Foundry trial account by clicking the Add 1 Service Plan button at the bottom of the wizard shown in [Figure 8.8](#08_002.html#f8.8).

Once added, you’ll need to save your newly added entitlements by clicking the Save button, as shown in [Figure 8.9](#08_002.html#f8.9).

After adding the document classification service to the entitlements table, the service will appear inside the Service Marketplace page, shown in [Figure 8.10](#08_002.html#f8.10). We’ll need to create an instance of this service next.

[![Saving EntitlementsEntitlements](bilderklein/klein08_009.png)](img-f8.9.html) 

**Figure 8.9**    Saving Entitlements

[![Document ClassificationDocument classification in the Service Marketplace](bilderklein/klein08_010.png)](img-f8.10.html) 

**Figure 8.10**    Document Classification in the Service Marketplace

To create an instance of this service, click the service’s tile to navigate inside the service. Click on New Instance, as shown in [Figure 8.11](#08_002.html#f8.11), to create a new instance of the service.

[![Service InstanceService instance Creation](bilderklein/klein08_011.png)](img-f8.11.html) 

**Figure 8.11**    Service Instance Creation

Once you click the New Instance button, the instance creation wizard will appear, where you’ll enter a name for the instance and then click Finish. The newly created instance will appear in the list shown in [Figure 8.12](#08_002.html#f8.12).

[![New Service Instances](bilderklein/klein08_012.png)](img-f8.12.html) 

**Figure 8.12**    New Service Instances

Now that we have an instance of the service, we’ll need to create a service key, which is critical to accessing the service. Navigate inside the newly created service instance and go to the Service Keys section. Click the Create Service Key button to launch the popup window shown in [Figure 8.13](#08_002.html#f8.13).

[![Creating a Service KeyService key](bilderklein/klein08_013.png)](img-f8.13.html) 

**Figure 8.13**    Creating a Service Key

Once the service key is generated, you’ll see the service key with all the necessary credentials, as shown in [Figure 8.14](#08_002.html#f8.14). Make sure you take note of the clientid, clientsecret, and uaa.url from your service key, which are key information for calling the service.

[![Service Key Details](bilderklein/klein08_014.png)](img-f8.14.html) 

**Figure 8.14**    Service Key Details

Using the clientid, clientsecret, and uaa.url from the service key, now, obtain an OAuth token to authorize the service calls. Append /oauth/token?grant\_type=client\_credentials to the end of the uaa.url [https://tria001.authentication.eu10.hana.ondemand.com/](https://tria001.authentication.eu10.hana.ondemand.com/). The final URL should be similar to the one shown in [Figure 8.15](#08_002.html#f8.15). Submit the URL via any web browser by pressing (Enter), and a popup window will open where you’ll need to enter the clientid as the user name and the clientsecret as the password taken. Click OK.

[![Obtaining an OAuth Token](bilderklein/klein08_015.png)](img-f8.15.html) 

**Figure 8.15**    Obtaining an OAuth Token

Once authenticated successfully, an OAuth access token will be generated, as shown in [Figure 8.16](#08_002.html#f8.16). Now, everything is all set for you to use the document classification service through Swagger UI.

[![OAuthOAuth token Token](bilderklein/klein08_016.png)](img-f8.16.html) 

**Figure 8.16**    OAuth Token

To access the document classification service’s Swagger UI, append /document-classification/v1 to the end of the URL value from the service key, as shown in [Figure 8.17](#08_002.html#f8.17). Then, paste this combined URL into any web browser and press (Enter).

[![Swagger URL Base](bilderklein/klein08_017.png)](img-f8.17.html) 

**Figure 8.17**    Swagger URL Base

The URL launches the Swagger UI and displays all the available endpoints, as shown in [Figure 8.18](#08_002.html#f8.18).

[![Swagger UISwagger UI](bilderklein/klein08_018.png)](img-f8.18.html) 

**Figure 8.18**    Swagger UI

However, before you can execute any of these endpoints, you’ll need to be authorized, which is where the OAuth token obtained in the previous steps will be required. Click the Authorize button, and the popup window shown in [Figure 8.19](#08_002.html#f8.19) will appear.

[![Authorize](bilderklein/klein08_019.png)](img-f8.19.html) 

**Figure 8.19**    Authorize

Inside the Value field, paste in the OAuth token but, as shown in [Figure 8.19](#08_002.html#f8.19), don’t forget to add the prefix “bearer” before you click the Authorize button. Once authorized, close this popup window and navigate back to Swagger UI.

On your SAP Cloud Platform Cloud Foundry trial account, the document classification service comes with a pretrained model available for all users. You can use this model to classify product descriptions into categories of product types. You can use any PDF for this step; in our case, we’ll use a sample invoice PDF for classification.

In Swagger UI, open the group classification and click the second endpoint /classification/models/{modelName}/versions/{modelVersion}/documents to classify the document. Since this endpoint is a POST\-type endpoint, you’ll need to pass the necessary data in the following fields:

*   In the first document field, upload the PDF document you want to classify.
    
*   Leave the parameters field with its default values.
    
*   The modelVersion field must be maintained with the version of machine learning model. In a real-life use case where you might have multiple versions of your machine learning models, you’ll need to specify the one you want to use as part of the request. Let’s proceed with default value latest so that the latest version of the pretrained model is used.
    
*   The modelName field must be maintained with the value of DocumentInfoRecord/AUT to ensure that we’re using the preset model that categorizes products.
    
*   After setting all the parameters, as shown in [Figure 8.20](#08_002.html#f8.20), finally, click Execute to send the document to the service. If you haven’t been authorized yet, you’ll need to complete the authorization step before clicking the Execute button.
    

[![POST Service](bilderklein/klein08_020.png)](img-f8.20.html) 

**Figure 8.20**    POST Service

Once the request is executed, a response from the server will be returned, as shown in [Figure 8.21](#08_002.html#f8.21).

[![POST ServicePOST service Response](bilderklein/klein08_021.png)](img-f8.21.html) 

**Figure 8.21**    POST Service Response

Inside the Response body section, you’ll see the current status of the classification process, which should be RUNNING, indicating that the classification is in progress. You should also see a documentId, which is automatically assigned to the document by the server. Don’t forget to copy or make a note of the documentId because you’ll need this information in the next step.

To view the result of document classification run, you must execute a GET endpoint under the third endpoint within the group classification, which is called with the following URL: /classification/models/{modelName}/versions/{modelVersion}/documents/{documentId}. To execute the GET request, you must pass the two common parameters mentioned earlier (modelVersion and modelName) as well as the documentId you received when you executed the POST service. To summarize, as shown in , the required parameters include the following:

*   The modelVersion field with the value latest
    
*   The modelName field with the same value of DocumentInfoRecord/AUT
    
*   The documentId retrieved from the POST service response
    

Once you’ve maintained all these parameters, as shown in [Figure 8.22](#08_002.html#f8.22), click the Execute button to trigger the execution of the request.

[![GET Request Input](bilderklein/klein08_022.png)](img-f8.22.html) 

**Figure 8.22**    GET Request Input

Once executed, the request will return a response. The Response body field captures all the classification results for every characteristic based on which the document has been classified, which is its PRODUCT\_TYPE. As shown in [Figure 8.23](#08_002.html#f8.23), each result includes a label representing the predicted value and a score that indicates how confident the service is about the prediction. Predictions are sorted by score in descending order.

[![GET Request Response](bilderklein/klein08_023.png)](img-f8.23.html) 

**Figure 8.23**    GET Request Response

Hopefully, this section has given you a clear picture of what the document classification service is all about and how you can leverage it in the context of enterprise solutions dealing with the classification of unstructured documents.

## 8.3    Document Information Extraction

Now that you’re accustomed with process of intelligently classifying high-value business documents using the document classification service from SAP AI Business Services with ease, we’ll now tackle a related task—extracting key information from similar kinds of business documents, like invoices and payment notes, by leveraging the next business service: the document information extraction service.

Manually extracting key information from any kind of unstructured document is always tedious, requiring a great deal of effort especially when the number of invoices is enormous. Also, traditional rule-based systems generally run manually crafted processing rules that only cater to a narrow scope. The main disadvantage in this case is that processing rules must be adjusted regularly, and gradually, the updating and maintenance of these kinds of systems become increasingly error prone, time consuming, and laborious. As more and more textual data becomes digitally available, the need for high-performing and maintainable technologies for text mining and natural language processing grows.

The potential solution to this growing need is the adoption of machine learning to perform text mining more intelligently. However, even with machine learning, building a solution from scratch for text mining comes with its own set of challenges including the existence of incomplete sentences, nouns, and abbreviations. Moreover, header-level items might appear once, while line items often can occur multiple times, and languages can also be a big barrier! So much to think about, design, and build, right? The document information extraction service can come to the rescue by competently addressing the need for information extraction.

In addition, the character grid, or chargrid, technique we described earlier in [Section 8.2](#08_002.html#h8.2) is put into action behind the document information extraction service as well! The chargrid method requires a training dataset compiled out of various invoices with different layouts, from different enterprise sources, and in different languages (for example English, French, German, Spanish, etc.). Also, the model must be trained to extract key information from invoices, including header fields such as Invoice No, Invoice Date, Amount, Vendor Name, and Vendor Address, as well as line item fields like amounts, quantities, descriptions, and any other relevant fields, as shown in [Figure 8.24](#08_003.html#f8.24).

[![Document Information ExtractionDocument information extractioninstance Instance](bilderklein/klein08_024.png)](img-f8.24.html) 

**Figure 8.24**    Document Information Extraction Instance

The extracted information includes:

*   Company name
    
*   Customer ID
    
*   Invoice number
    
*   Object
    
*   Amount
    
*   Subtotal
    
*   Tax
    
*   Total
    
*   Paid
    
*   Currency
    

As shown in [Figure 8.24](#08_003.html#f8.24), the model can successfully extract key-value information from sample invoices despite their significant diversity and complexity in invoice layouts. In this context, the chargrid method, which runs behind the document information extraction service, can easily outperform other information extraction techniques like the sequential or image-based model by taking care of 2D layout information and smaller fields, and perform complex extraction tasks where an understanding of the task is critical.

According to SAP’s official definition, the document information extraction business service helps you process various documents that may have content in headers and in tables. The extracted information can be applied, for example, to automatically process payables, invoices, or payment notes while ensuring that invoices and payables match. The model demonstrates how the document information extraction service extracts key information from business document(s) at runtime based on its training on sample documents. and [Figure 8.25](#08_003.html#f8.25) shows the features of the document information extraction service in a snapshot.

[![Document Information Extraction](bilderklein/klein08_025.png)](img-f8.25.html) 

**Figure 8.25**    Document Information Extraction

The service supports information extraction in four different languages including English (US), English (UK), English (Australia), and English (New Zealand) and comes with three different categories of endpoints to serve the purpose of managing clients, documents, and data. Some available endpoints include the following:

*   The Client API provides endpoints for creating the client required to process documents or to upload enrichment data. At a minimum, one client is required to execute the information extraction.
    
*   The Capabilities API returns a list of fields and enrichment data for document types including invoices and payment advices.
    
*   The Input Limits API returns details about the limitations of input parameters for the document information extraction service. For example, you can specify that the maximum size of a document file should be 25 MB, the number of documents uploaded per hour is capped at 2,000, and many other similar limitations.
    
*   The Document API provides essential endpoints for managing PDF documents including the ability upload and delete document files and retrieve a list of documents. Once documents are uploaded, the extracted information from these documents can be retrieved using the Get Result endpoint.
    
*   The Enrichment Data API provides a set of endpoints using which extracted data can be augmented. Defined enrichment data entities are matched with fields extracted from the processed documents. For example, a business entity can be defined as {"id":"BE0001", "name":"","accountNumber":"", "address1":"", "address2": "", "city":"", "countryCode":"", "postalCode":"","state":"", "email":"", "phone":"", "bankAccount":"", "taxId":""}to represent different kinds of organizations your company works with.
    

For more details on these APIs, refer to the documentation available on the SAP Help Portal at [https://help.sap.com/viewer/product/DOCUMENT\_INFORMATION\_EXTRACTION/SHIP/en-US](https://help.sap.com/viewer/product/DOCUMENT_INFORMATION_EXTRACTION/SHIP/en-US).

With all these options, the advantages of using the document information extraction service are similar to the advantages we described earlier for the document classification service, such as the following:

*   Minimizes the effort for processing large numbers of business-critical documents like invoices regardless of their layout or format, extracting key information automatically, thus increasing productivity.
    
*   Processes documents out of the box, without requiring the maintenance of templates to capture each kind of document.
    
*   Processes incoming documents more quickly to reduce days sales outstanding (DSO) and improve customer service.
    
*   Enriched, entity-based document extraction helps you extract information based on predefined contexts and match master data with transactional data.
    
*   Depending on the initial training and subsequent usage, the document information extraction service gradually learns from every single extraction it delivers, and accuracy improves over time.
    
*   Supports information extraction in multiple languages
    

The document information extraction service is also available on SAP Cloud Platform on Cloud Foundry under the CPEA.

### 8.3.1    Test Run of the Document Information Extraction Service

As before with the document classification service, now, let’s try out the document information extraction service exactly in the same fashion. The provisioning steps we described earlier in [Section 8.2.1](#08_002.html#h8.2.1) are exactly the same in this case, so we won’t repeat them. Instead, we’ll focus on the final outcomes of the APIs through Swagger UI.

We assumed that you’ve already fulfilled the prerequisites for the document classification service and created the instance and service key for the document information extraction service. To launch the Swagger UI, as shown in [Figure 8.26](#08_003.html#f8.26), open the URL by appending /document-information-extraction/v1/ to the end of the URL taken from the service key.

[![Document Information Extraction Swagger UI](bilderklein/klein08_026.png)](img-f8.26.html) 

**Figure 8.26**    Document Information Extraction Swagger UI

We’ll use the invoice format shown in [Figure 8.27](#08_003.html#f8.27) to apply the service and extract the relevant information.

[![Sample Invoice](bilderklein/klein08_027.png)](img-f8.27.html) 

**Figure 8.27**    Sample Invoice

First, let’s set up the POST /document/jobs endpoint, as shown in [Figure 8.28](#08_003.html#f8.28), where you’ll upload the invoice PDF using the file field to extract the order number, invoice number, invoice date, total due, and various other information from the document.

[![POST Request Input](bilderklein/klein08_028.png)](img-f8.28.html) 

**Figure 8.28**    POST Request Input

Once executed, the service will return a response in the Response body field, as well as the status and ID, as shown in [Figure 8.29](#08_003.html#f8.29), which will be required to extract the classification result.

[![Service Response](bilderklein/klein08_029.png)](img-f8.29.html) 

**Figure 8.29**    Service Response

Now, to see the information extracted from the invoice document, use the /document/jobs/{id} endpoint, as shown in [Figure 8.30](#08_003.html#f8.30), to retrieve the prediction.

[![Get Request to Retrieve](bilderklein/klein08_030.png)](img-f8.30.html) 

**Figure 8.30**    Get Request to Retrieve

Enter the ID received in the response of /document/jobs endpoint as a value and click the Execute button.

Once executed, the data extracted from the invoice will appear in the Response Body field. Congratulations! The document information extraction service has successfully extracted all the necessary information from the invoice, as shown in [Figure 8.31](#08_003.html#f8.31) and [Figure 8.32](#08_003.html#f8.32).

[![Information Extraction Response](bilderklein/klein08_031.png)](img-f8.31.html) 

**Figure 8.31**    Information Extraction Response

[![Information Extraction Response, Continued](bilderklein/klein08_032.png)](img-f8.32.html) 

**Figure 8.32**    Information Extraction Response, Continued

## 8.4    Business Entity Recognition

Also known as named entity recognition (NER), the business entity recognition service is just one more information/entity extraction tool in your toolbox for handing business communications like emails, invoice inquiries, and any other type of semi-structured and unstructured text source. NER is a popular technique for identifying and segmenting named entities and classifying them under various predefined categories. This method is not only popular in the enterprise business context but, knowingly or unknowingly, you may use it in your daily life while interacting with smart assistants like Siri and Google Now. The business entity recognition service adds the power of semantic understanding to any large body of text and can apply to multiple business use cases, such as classifying and prioritizing news content for a publishing house, shortlisting candidates from a large number of CVs for a recruiter, or categorizing emails at the service desk based on the presence of specific entities in the email body. [Figure 8.33](#08_004.html#f8.33) shows one such exemplary use case of the business entity recognition service where the sample text input is a disorganized description about a notebook that is quite difficult to understand at first glance. In these situations, the business entity recognition service can come to the rescue by performing the appropriate text mining required to recognize entities.

With reference to [Figure 8.33](#08_004.html#f8.33), the business entity recognition uses multilayered, bidirectional long short-term memory networks (LSTMs) for text mining and recognizing the required entities. To understand the concept of multilayered, bidirectional LSTMs, let’s take a step back and understand the core concept behind LSTMs, called recurrent neural networks (RNNs).

[![Business Entity Recognition Instance](bilderklein/klein08_033.png)](img-f8.33.html) 

**Figure 8.33**    Business Entity Recognition Instance

We’ll start with a common example: Let’s say, while reading this chapter, you’re struck with a dozen ideas, in a stream of consciousness. Every new word is based on your understanding of previous words. Thus, every time you start a new idea, would you throw everything away and start from scratch? No! Your thoughts have persistence. Traditional neural networks can’t do this kind of thinking, which seems like a major shortcoming. For example, imagine you want to classify events that occur at every point in a movie. A traditional neural network may not be able to reason about previous events in the film in order to understand later events, and this shortcoming is what is addressed with RNNs. Unlike a traditional neural network, RNNs are networks with loops, allowing information to persist. LSTMs are a special kind of RNN, capable of learning long-term dependencies. LSTMs were introduced by Hochreiter & Schmidhuber (1997), work well on a large variety of problems, and are now widely used. LSTMs are explicitly designed to avoid the problem of long-term dependency. Remembering information for long periods of time is their default behavior, not something they struggle to learn. Based on this explanation and reference diagram, we hope that you can see how the service can help you to extract entities from all sorts of business communications.

## 8.5    Data Attribute Recommendation

The core of any enterprise is its master data, which ultimately drives their business processes in many different scenarios. This data must meet a range of data quality dimensions to fortify automated business processes. Furthermore, if data quality is not incessantly maintained, quality declines quickly and ultimately affects your company’s ability to become an intelligent enterprise. In this context, the data that is often most compromised is master data, which represents the core entities of enterprise business processes. The uncontrolled pace and growth of data across enterprises challenges enterprises that remain committed to their traditional data management systems, which restrict them from harnessing the full potential of their master data. In traditional system, the process of identifying master data inconsistencies is a tedious and time-consuming matching process. The master data team probably spent most of their productive hours searching for the right categories, descriptions, missing data fields, etc. With AI-driven solutions for data management, your company can stay relevant in a highly competitive marketplace. So, how do we do it?

Included with SAP AI Business Services, the data attribute recommendation service is ideal for automating the master data management process by recommending missing categories, subcategories, materials, products, item/product descriptions, and classifications, indeed any other client-specific information, to the master data team. According to SAP’s official definition, the data attribute recommendation service helps classify entities, such as products, stores, and users into multiple classes, using free text, numbers, and categories as inputs. The data attribute recommendation service applies hierarchical and multi-label classifications using a neural network primarily based on two key components: the dataset and the dataset schema. A dataset is a table with rows representing instances of business objects. Its columns contain the values of the instances. The dataset schema defines which columns must appear in a dataset, including the specification of columns to be used as features and labels. In this case, selecting the most appropriate classification depends on the scenario and can only be determined by evaluating predictions from both these categories.

[Figure 8.34](#08_005.html#f8.34) shows a quick snapshot of a data attribute recommendation process where new, inconsistent, or master data records, with missing attributes, are taken as inputs. Machine learning and artificial intelligence is applied to perform the classification and harmonization of master data more efficiently, thus making high-quality data management a reality. [Figure 8.35](#08_005.html#f8.35) shows the overall data attribute recommendation service portfolio.

[![Data Attribute Recommendation Instance](bilderklein/klein08_034.png)](img-f8.34.html) 

**Figure 8.34**    Data Attribute Recommendation Instance

[![Data Attribute Recommendation](bilderklein/klein08_035.png)](img-f8.35.html) 

**Figure 8.35**    Data Attribute Recommendation

Still not very clear, right? This service is as simple and straightforward as the others. Thus, for a better understanding of the applicability of data attribute recommendation process, let’s look at how this business service is making a difference in the day-to-day activities performed by a master data team.

For example, maintaining the right commodity code is essential for global trade without which shipments at international borders or ports of entry might be delayed, which often leads to the rejection of shipments, ultimately costing money to the organization. The primary reason behind this kind of mistake is manual code maintenance, which is error prone, or rule-based commodity code maintenance processes that often lead to inconsistencies and leftovers for manual processing. With the data attribute recommendation service, missing commodity codes can be predicted based on the training of the model to understand complex master data fields and their associated dependencies. This machine learning approach can completely automate the manual process of commodity code assignment in product master data creation.

With this conceptual understanding, let’s now focus on the APIs provided by the data attribute recommendation business service. The service includes a wide spectrum of APIs to support multiple functionalities like defining datasets, data uploading, data validation, managing training jobs and deployment lifecycles, and classifying records. Some of the APIs you may use include the following:

*   Upload APIs are primarily used for creating, deleting, and reading dataset and dataset schema definitions and finally uploading data, in comma-separated values (CSV) files, to the defined dataset by its ID.
    
*   The Input Limits API returns details about the limitations of input parameters for the document information extraction service. For example, you can specify that the maximum request size for a dataset schema is 25 KB, the maximum request size for dataset upload is 5 GB, and many other similar limitations.
    
*   The Data Validation API is a critical step for ensuring that the uploaded dataset is compliant with the definition of the dataset schema and determines how many records can be effectively used for training.
    
*   Training Job and Deploy Model APIs are all primarily for creating and deleting training jobs, getting a list of training jobs, deploying models, fetching a list of deployments, and undeploying models.
    
*   The Classify Records Inference API is for classifying master data based on the training of the underlying model.
    

For more technical details on these APIs, refer to the SAP Help Portal at [https://help.sap.com/viewer/product/Data\_Attribute\_Recommendation/SHIP/en-US](https://help.sap.com/viewer/product/Data_Attribute_Recommendation/SHIP/en-US).

Along with its unique set of APIs, the data attribute recommendation business service also includes a unique set of benefits, especially for your master data management team, such as the following:

*   Automatic master data management 24/7, minimizing the effort required for data categorization, classification, and matching almost to nil by applying artificial intelligence and machine learning, ultimately increasing master data consistency and accuracy.
    
*   Significant enhancement to data management practices, which also improves data quality.
    
*   The underlying algorithm can make predictions of field values by learning the logic behind complex fields and their dependencies to data attributes.
    
*   Finally, based on training and further usage, the data attribute recommendation service gradually learns from every single recommendation it delivers and accuracy improves over time.
    

The data attribute recommendation business service is available on SAP Cloud Platform on Cloud Foundry under CPEA and is applicable to a variety of customer-integrated scenarios with SAP S/4HANA and SAP S/4 HANA Cloud.

### 8.5.1    Test Run of the Data Attribute Recommendation Service

Let’s now see the data attribute recommendation business service in action. The best way to try out this service is through the SAP API Business Hub. The SAP API Business Hub is the central hub for SAP- and selected partner-provided APIs for application developers to search, discover, try out, and consume APIs before using them to build extensions or integrations in SAP Cloud Platform. The SAP API Business Hub has a wonderful feature where you can quickly try out some of these business service APIs without any kind of coding. So, let’s try a test run of the Data Attribute Recommendation API and see how it works by following these steps:

1.  First, log on to the SAP API Business Hub at [https://api.sap.com/](https://api.sap.com/) and search for “SAP AI Business Services,” or you can directly go to [https://api.sap.com/package/SAPLeonardoMLBusinessServices?section=Artifacts](https://api.sap.com/package/SAPLeonardoMLBusinessServices?section=Artifacts). With either method, you’ll see three different business services, as shown in [Figure 8.36](#08_005.html#f8.36).
    
    [![SAP AI Business Services on SAP API Business Hub](bilderklein/klein08_036.png)](img-f8.36.html) 
    
    **Figure 8.36**    SAP AI Business Services on SAP API Business Hub
    
2.  Click on the Data Attribute Recommendation Service tile, which will navigate you to the next screen, which displays the API’s details. To execute the service, you can either configure your own environment by clicking Configure Environments, or you can use the SAP API Business Hub sandbox as the default environment, as shown in [Figure 8.37](#08_005.html#f8.37).
    
3.  In our example, we’ll try out the Post service by clicking the Inference link on the left, which will take you to the /models/{modelName}/versions/1 Post service, as shown in [Figure 8.37](#08_005.html#f8.37).
    
    [![POST Inference](bilderklein/klein08_037.png)](img-f8.37.html) 
    
    **Figure 8.37**    POST Inference
    
4.  After selecting an API environment, click the Tryout link, and the area with service-related details will be expanded to display the service’s parameters and responses.
    
5.  As shown in [Figure 8.38](#08_005.html#f8.38), update the input request JavaScript Object Notation (JSON) file, and once you’re can set the body parameter, click the Execute button.
    
    [![Request Input](bilderklein/klein08_038.png)](img-f8.38.html) 
    
    **Figure 8.38**    Request Input
    
6.  The Response body shows the predictions for various categories. With respect to the input description “used to wash laundry,” the "level1\_category" shows that the object has been classified under “Appliances” with a highest probability (more than 95% confidence). [Figure 8.39](#08_005.html#f8.39) shows the service response in detail.
    
    [![Service Response](bilderklein/klein08_039.png)](img-f8.39.html) 
    
    **Figure 8.39**    Service Response
    
7.  In addition to the ability to try out services, the SAP API Business Hub even provides sample code snippets for calling machine learning services from multiple languages. Click on the Code Snippet link, next to Tryout link in the top-right corner, to launch the Code Snippet popup window, as shown in [Figure 8.40](#08_005.html#f8.40).
    
    [![Code Snippet](bilderklein/klein08_040.png)](img-f8.40.html) 
    
    **Figure 8.40**    Code Snippet
    
8.  Inside the Code Snippet window, the machine learning service invocation code is provided in multiple languages, including JavaScript, Java, Swift, Curl, SAPUI5, ABAP, and SAP Cloud Platform ABAP. You can easily copy and leverage these code snippets while developing actual solutions.
    

Since the Data Attribute Recommendation API is available as a REST API, you can easily consume this service through an API call and introduce powerful data attribute classification functionalities in your enterprise application.

## 8.6    Invoice Object Recommendation

We hope that you’ve enjoyed reading and getting to know SAP AI Business Services because we’re in the homestretch. Grab a cup of coffee and a cookie if you need it!

The invoice object recommendation service is all about streamlining accounts payable processes. Today, in many organizations, invoice processing is performed manually, or only partially automatically, by accounting departments or accounting service providers. The manual processing of invoices is prone to error and is time consuming, problems that are exacerbated when thousands of invoices come in. Traditional accounting software can’t improve on this situation much because of its dependency on predefined templates or processing rules that tell the software “where” and “what” data must be processed. Day-to-day basic tasks, like invoice processing, can become burdensome because of missing pieces of information like “purchase order no.,” which the costs accounts payable team more time and effort looking for the right general ledger accounts and cost centers in the system. So, for the accounts payable team to act smart, the reform or removal of manual tasks is a vital goal, along with providing real-time access to financial data. In this case, included with SAP AI Business Services, the invoice object recommendation service can play a vital role in enabling your accounts payable team with smart invoice processing capabilities to replace the manual lookup of missing information or the need to correct entries.

The invoice object recommendation business service uses the chargrid method to process invoices and recognize the required information, including vendor, item price, tax code, work order, company code, document type etc., which are then used in a classification model to predict the correct general ledger account and cost center. The underlying model must be trained using historical invoice data (at least 6 months’ worth) to derive the (hopefully) correct general ledger account or cost center prediction, which will include a percentage representing probability/confidence for suggested categories of the line items of an invoice. Based on historical data, the model will recommend the top three most likely general ledger account and cost center options for any invoice that lacks a previously assigned purchase order (PO). This feature enhances financial reporting by minimizing discrepancies in accounts/budgets as well as by reducing repetitive and redundant tasks, such as the process of manually searching and selecting the correct general ledger account or cost center. Moreover, the service corrects incorrectly assigned general ledgers or cost centers. The service primarily extracts structured information from the invoice according to its training, remaining texts like product description and addresses are not extracted immediately. In these cases, you can turn to another business service like the document information extraction service to extract any additional text and add more intelligence to the process.

Similar to other business services, as shown in [Figure 8.41](#08_006.html#f8.41), the invoice object recommendation service also comes with a range of APIs for uploading data and managing training jobs as well as the inference service to receive recommendations. Some of the APIs you may use include the following:

*   Upload Data APIs take care of storing data to be used to train the underlying model, including an API for applying data locking during training and for checking data lock statuses.
    
*   Training APIs are for triggering the machine learning model training job and checking the progress and statuses of training jobs.
    
*   The Inference API receives the recommendations resulting from the evaluation of unlabeled data.
    

[![Invoice Object Recommendation](bilderklein/klein08_041.png)](img-f8.41.html) 

**Figure 8.41**    Invoice Object Recommendation

## 8.7    SAP Service Ticket Intelligence

SAP Service Ticket Intelligence, the last topic of this chapter, is a unique service that can add intelligence to a wide range of service desk-oriented processes across various industries. Gone are the days of hypotheses or rule-based systems to find resolutions for tickets. The need for intelligent service desks to deliver better customer experiences and enhance ticket resolution processes is growing more than ever before. SAP Service Ticket Intelligence is a business service that exactly fits this need and can efficiently sort tickets based on inputs from a variety of channels, suggest relevant service proposals, and route tickets to the appropriate service agent.

SAP Service Ticket Intelligence uses deep learning neural networks to understand the semantics of the unstructured data in ticket messages and classify tickets into their most likely categories, including recommending solutions or knowledge base articles. As part of the training process, SAP uses historical customer ticket messages and their assigned categories and solutions to train the deep learning model, which runs on a state-of-the-art, character-level, convolutional neural network without any predefined format. The character-based approach makes full use of inputs, even typos, and easily surpasses the word-based dictionary-embedded approach. Also, a deep learning attention mechanism drives the model to attend to different parts of the source sentence at each step of the output generation, and instead of encoding the input sequence into a single fixed context vector, the mechanism lets the model learn how to generate a context vector for each output time.

Once completed, the resulting model can then be used to classify new ticket messages and recommend relevant solutions. As more and more service tickets are processed, along with ingestion of user feedback, the model will become more accurate over time. For more details on convolutional neural networks, refer to [Chapter 2](#02_001.html#h2).

SAP Service Ticket Intelligence currently supports all its functionalities including text classification, solution recommendation, and language detection in multiple languages. Let’s now focus on the wide range of APIs offered by SAP Service Ticket Intelligence, which includes APIs for model training, classification, and recommendation, which can be described in the following way:

*   Model training-related APIs are for uploading training files, initiating training, activating models, getting training statuses, determining model accuracy, deleting models, enabling/disabling model categories, deactivating models, etc.
    
*   Classification APIs are for classifying incoming messages and include language detection.
    
*   Recommendation APIs recommend possible solutions for incoming customer service messages (also known as support tickets) and include language detection.
    

For more details on these APIs, refer to SAP Help Portal at [https://help.sap.com/viewer/product/SERVICE\_TICKET\_INTELLIGENCE/SHIP/en-US?task=discover\_task](https://help.sap.com/viewer/product/SERVICE_TICKET_INTELLIGENCE/SHIP/en-US?task=discover_task).

As shown in [Figure 8.42](#08_007.html#f8.42), SAP Service Ticket Intelligence can benefit your support teams in many ways, from automatic ticket categorization to solution recommendations. The more extensive list of key benefits includes the following:

*   Freeing service agents from repetitive tasks so they can spend more time on customer interactions by automating ticket categorization and solution guidance.
    
*   Scaling your business along with call-volume fluctuations; you can tackle overwhelming volumes of omnichannel messages and digital interactions with automated processing.
    
*   Integrating automated customer service ticketing with SAP Service Ticket Intelligence’s cloud-based solutions, designed for customer relationship management (CRM), to reduce time to value.
    
*   Accelerating service desk response times by identifying common support tickets, such as license requests, that could be resolved with a defined workflow.
    

[![SAP Service Ticket Intelligence](bilderklein/klein08_042.png)](img-f8.42.html) 

**Figure 8.42**    SAP Service Ticket Intelligence

SAP Service Ticket Intelligence is also an SAP Cloud Platform service available under CPEA. For SAP C/4HANA-based clients, SAP Service Ticket Intelligence is integrated with SAP Cloud for Customer, enterprise edition. SAP Service Ticket Intelligence is also integrated into SAP S/4HANA Customer Management.

###### Note

Deep learning is a collection of statistical machine learning techniques that is transforming digital business. Applications using deep learning techniques and frameworks enable companies across industries to find new ways of capitalizing on the huge volumes of date they are capturing, gaining new insights that simply weren’t possible before and, as a result, driving competitive advantage. For more details on deep learning, refer to [Chapter 2](#02_001.html#h2).

### 8.7.1    Test Run of the Service Ticket Intelligence Service

Before we close this chapter, let’s see how the text classification process of the service ticket intelligence service works. In this case, we’ll also test the service using the SAP API Business Hub. The preparation steps for Text Classification – Service Ticket Intelligence are the same as data attribute recommendation business service executed earlier. When you’re ready, follow these steps:

1.  Log on to the SAP API Business Hub and navigate to SAP AI Business Services. Alternatively, you can use the following URL: [https://api.sap.com/package/SAPLeonardoMLBusinessServices?section=Artifacts](https://api.sap.com/package/SAPLeonardoMLBusinessServices?section=Artifacts). Click the Text Classification – Service Ticket Intelligence tile.
    
2.  As shown in [Figure 8.43](#08_007.html#f8.43), we’ll try the /text/classify service to classify the text content from service tickets and categorize tickets into complaints and compliments.
    
    [![Text Classification POST Service](bilderklein/klein08_043.png)](img-f8.43.html) 
    
    **Figure 8.43**    Text Classification POST Service
    
3.  To execute the service, click the Tryout link, and the area showing service-related details will be expanded to display the service’s parameters and responses.
    
4.  Modify the classification request input parameter, as shown in [Figure 8.44](#08_007.html#f8.44), and click on the Execute button.
    
    [![Request Input](bilderklein/klein08_044.png)](img-f8.44.html) 
    
    **Figure 8.44**    Request Input
    
5.  The Response body, as shown in [Figure 8.45](#08_007.html#f8.45), shows the classification of the input service text content into two different categories, like “compliment” and “complaint,” respectively, based on the essence of the text.
    
    [![Service Response](bilderklein/klein08_045.png)](img-f8.45.html) 
    
    **Figure 8.45**    Service Response
    

You can easily try out and test the solution recommendation business service in a similar fashion. While building an intelligent service ticketing solution, both of these classification and solution services complement each other.

We hope from this trial run you can see how to apply the service in the context of an enterprise application and be able to apply it in the appropriate context. Especially by combining this solution with SAP Conversational AI (covered in [Chapter 11](#11_001.html#h11)), you can create magic. All you need to do is pass the customer inputs/queries to understand the customer request, categorize the request, and determine whether the customer input is a complaint or a compliment. Since SAP AI Business Services are REST-based APIs, amazing opportunities are just one good idea away.

## 8.8    Summary

Finally, we’ve concluded our chapter on SAP AI Business Services, and before we close, let’s do a little recap. In this chapter, we started with a brief introduction to SAP AI Business Services and described how these capabilities can help enterprises bring automation across industries. We also dove deeply into a few individual services and emphasized the underlying techniques, their abilities, and their applicability from a business process perspective. With SAP AI Business Services, the possibilities are endless, and each service or a combination of services can bring powerful and intelligent automation to your business processes—all it takes is a brilliant idea to kick start a project, right?

# 9    Building Scenarios Using Jupyter Notebook

Now that you have a thorough understanding of the SAP Data Intelligence platform and its numerous features and capabilities, in this chapter, we’ll go through the data intelligence capabilities available through Jupyter Notebook. In this chapter, we’ll show you step by step how to build a machine learning scenario using Jupyter Notebook. You’ll also learn about different application programming interfaces (APIs) available in the SAP Data Intelligence Python software development kit (SDK) for Jupyter Notebook.

A common scenario with SAP Data Intelligence combines all design-time elements (such as pipelines and notebooks in Jupyter Notebook) and runtime elements (such as training runs, models, tracking and model deployments) under one hood, which is enabled by the machine learning scenario manager, included with SAP Data Intelligence. The machine learning scenario manager lets you deal with data science artifacts and manage all associated tasks from a central place, covering a wide range of data science proficiencies including dataset binding, performing experiments using the next-generation Jupyter Notebook, automating model training, and deployment via templated pipelines. With these capabilities, you can ultimately seamlessly transition from the prototyping phase into production. Driven by the key concepts of machine learning scenarios, this multifaceted data science application lets you work with datasets, pipelines, and notebooks. The primary focus of this chapter is how you can use Jupyter Notebook integrated inside the machine learning scenario manager to build a machine learning scenario and conduct some experiments.

Jupyter, as a next-generation notebook, is one of the most popular notebooks among the data scientists and is integrated into many data science platforms, including SAP Data Intelligence. For your machine learning data, whether sourced from a raw comma-separated values (CSV) file, data from SAP HANA, or various other supported formats can be directly injected into the notebook so you can execute various machine learning experiments. Jupyter Notebook is an open source web application that you can use to create and share documents that contain live code, equations, visualizations, and text. Jupyter Notebook ships with the IPython kernel, which allows you to write your programs in Python, but currently, over a hundred other kernels are available for use.

In this chapter, we’ll start by creating a notebook from Jupyter Notebook in SAP Data Intelligence in [Section 9.1](#09_001.html#h9.1), before moving on to discuss the SAP Data Intelligence Python SDK in [Section 9.2](#09_002.html#h9.2). We’ll turn, in [Section 9.3](#09_003.html#h9.3), to a timely use case involving COVID-19 data to illustrate how you can build your own machine learning scenarios with Jupyter Notebook.

## 9.1    Adding a Notebook

Inside SAP Data Intelligence, through the machine learning scenario manager, adding a notebook is also pretty simple. All you need to do is navigate to the machine learning scenario manager inside the SAP Data Intelligence platform, shown in [Figure 9.1](#09_001.html#f9.1), and then click on the + icon at the top of the notebook segment, as shown in [Figure 9.2](#09_001.html#f9.2).

[![Navigating to the Machine Learning Scenario Manager](bilderklein/klein09_001.png)](img-f9.1.html) 

**Figure 9.1**    Navigating to the Machine Learning Scenario Manager

Once you click the + icon, a small popup window appears where you’ll enter a name for the notebook, as shown in [Figure 9.2](#09_001.html#f9.2).

[![Jupyter NotebooknameEntering a Notebook Name](bilderklein/klein09_002.png)](img-f9.2.html) 

**Figure 9.2**    Entering a Notebook Name

Once created, your notebook is your playground for all your experiments, as shown in [Figure 9.3](#09_001.html#f9.3). Since Jupyter Notebook is language agnostic, in addition using to Python, Jupyter Notebook supports over 40 programming languages including R, Julia, Scala, and PySpark and is now one of the most preferred environments for data scientists and engineers for exploring and analyzing data.

[![Notebook Editor](bilderklein/klein09_003.png)](img-f9.3.html) 

**Figure 9.3**    Notebook Editor

A notebook’s cells default to using code when first created, and that cell uses the kernel you chose when you started your notebook, as shown in [Figure 9.4](#09_001.html#f9.4). In our case, we started our notebook with Python 3 as the kernel, so that means we’ll write Python code in the notebook’s cells.

[![Kernel Selection](bilderklein/klein09_004.png)](img-f9.4.html) 

**Figure 9.4**    Kernel Selection

Since your initial notebook has only one empty cell, the notebook can’t really do anything. Thus, to verify that everything is working, let’s add some Python code to the cell and try running its contents. Let’s try to add the following code to the first cell, as shown in [Figure 9.5](#09_001.html#f9.5):

```
print('Hello Jupyter!'). 
```

[![Notebook with Python Sample](bilderklein/klein09_005.png)](img-f9.5.html) 

**Figure 9.5**    Notebook with Python Sample

In this context, “running a cell” means “executing the cell’s contents.” To execute a cell, select the cell and click the run icon that appears in the row of buttons along the top. Alternatively, you can press (Shift)+(Enter). If multiple cells exist in your notebook, then, when you run the cells in order, variables and imported data are shared across cells. As a result, you can easily separate out your code into logical chunks without needing to reimport libraries or re-create variables or functions in every cell.

As shown in [Figure 9.6](#09_001.html#f9.6), when you run a cell, notice that some square braces appear next to the word In to the left of the cell. The square braces will autofill with a number that indicates the order in which you ran the cells. For example, if you open a fresh notebook and run the first cell at the top of the notebook, the square braces will fill with the number 1.

[![A Cell](bilderklein/klein09_006.png)](img-f9.6.html) 

**Figure 9.6**    A Cell

But, wouldn’t it be interesting to know what happens in the background when you play with the notebook? In addition to running our code, Jupyter Notebook stores code and output, together with markdown notes, in an editable document called a notebook. When you save the document, this file is sent from your browser to the notebook server, which saves it on disk as a JavaScript Object Notation (JSON) file with a .ipynb extension. The notebook server, not the kernel, is responsible for saving and loading notebooks, so you can edit notebooks even if you don’t have the kernel for that language—you just won’t be able to run code. Furthermore, the kernel doesn’t know anything about the contents of the notebook document: Cells of code are only sent for execution when the user runs them.

Now that you have a good understanding of how Jupyter Notebook works, let’s focus on the dedicated Python SDK for building scenarios using Jupyter Notebook inside the machine learning scenario manager.

## 9.2    SAP Data Intelligence Python SDK

Today’s data scientists are well equipped with various platforms, tools, services, libraries, and SDKs to meet almost any enterprise challenge. Jupyter Notebook, integrated into the machine learning scenario manager in SAP Data Intelligence, supports for over 40 different programming languages, and Python is one of most popular. Numerous Python-based libraries are used to predict outcomes, automate tasks, streamline processes, and offer business intelligence insights. You can also work with data in vanilla Python, but quite a few open source libraries can make Python data tasks much, much easier. Furthermore, the SAP Data Intelligence Python SDK is one gem in the collection of Python-based machine learning libraries for enhancing data science experiments and processes using Jupyter Notebook. According to SAP’s official specification, the SAP Data Intelligence Python SDK is a high-level Python SDK that you can run in a Jupyter Notebook as well as in a pipeline operator (in particular, the training operator). Various Python-based libraries are already available in for data science tasks, covering areas such as data processing, modeling, and visualization, but the SAP Data Intelligence Python SDK is especially crafted for the SAP Data Intelligence platform. Using the SAP Data Intelligence Python SDK is effective and convenient in the context of various data science experiments, by enabling the following capabilities:

*   Programmatic access for creating and accessing machine learning scenarios and their versions, including provisions to retrieve and update metadata. For example, machine learning scenarios can be created using the create\_scenario method, and a scenario can be retrieved either by name or ID or by using the using the get\_current\_scenario method.
    
*   Dedicated application programming interface (API) to create configurations along and to trigger executions and deployments.
    
*   APIs to create and update pipelines and for binding pipelines to machine learning scenarios programmatically. For example, create\_pipeline is one method for creating a pipeline programmatically.
    
*   Using the SDK, you can create training jobs, including multifile jobs, from within JupyterLab.
    
*   Includes the ML Tracking SDK to capture and organize experiments, along with dedicated APIs to report various metrics like parameter logging, metrics logging, and runs.
    

Let’s now focus on setting up the SAP Data Intelligence Python SDK with a sneak peek at some of the most essential SDK methods required in various data science experiments.

### 9.2.1    Setting Up and Leveraging the SAP Data Intelligence SDK

Inside a notebook, you can easily include the SAP Data Intelligence Python SDK modules just by adding the following import statement:

import sapdi

The import statement searches for the named module, and if found, a module object is created and initialized. Let’s quickly look into some key methods that will be really handy for your experiments inside Jupyter Notebook:

*   sapdi.get\_current\_scenario()  
    One method to retrieve machine learning scenario attributes by accessing them as properties of the scenario object, for example, sapdi.get\_current\_scenario().name.
    
*   sapdi.create\_pipeline  
    A key method for adding new pipelines to a machine learning scenario.
    
*   sapdi.create\_artifact  
    Dedicated to defining graphs for the pipelines by creating operators.
    
*   sapdi.create\_version() /get\_current\_version()  
    A set of methods creating and retrieving versions of scenarios.
    

For executing and deploying pipelines, you’ll first need to define a configuration and then call .execute(<pass configuration object>) to execute the pipeline. Following a similar approach, you can use the configuration to deploy the pipeline using the .create(<pass configuration object>)  method.

For more details on the API specification, refer to the Machine Learning Guide at the following link: [http://s-prs.co/501405](http://s-prs.co/501405).

### 9.2.2    SAP Data Intelligence Python SDK

Besides the SAP Data Intelligence Python SDK, various other Python-based machine learning libraries may be needed in your data science experiments at various occasions, like accessing SAP HANA data or applying predictive analytics. The SAP HANA Python client API called hana\_ml is designed for these tasks. With the SAP HANA Python client API, Python-savvy data scientists can access SAP HANA data and build machine learning models using that data directly in SAP HANA. For machine learning algorithms, the SAP HANA Python client API provides a set of Python APIs and functions for creating and manipulating SAP HANA DataFrame, training and scoring machine learning models, and data preprocessing. The SAP HANA Python client API hana\_ml primarily consists of the following parts:

*   A set of machine learning APIs, including PAL and APL package where the Predictive Analytics Library (PAL) package consists of a set of Python algorithms and functions that provide access to the machine learning capabilities in SAP HANA. The Automated Predictive Library (APL) package exposes the data mining capabilities of the automated analytics engine in SAP HANA through a set of functions.
    
*   The APL package contains three primary algorithms including classification, clustering, and regression, for example:
    
    ```
    # Create Model
    from hana_ml.algorithms.apl.classification import AutoClassifier
    model = AutoClassifier(
    conn_context=conn,
    variable_auto_selection=True)
    ```
    
*   The PAL package contains algorithms for associations, clustering, cross-validation, decision trees, decomposition, time series, and more. The following code snippet depicts, for example, the decision tree and random forest algorithms:
    
    ```
    DecisionTreeClassifier(conn_context=conn, algorithm='c45',
    min_records_of_parent=2,
    min_records_of_leaf=1, thread_ratio=0.4,
    split_threshold=1e-5, model_format='json')
    RandomForestClassifier(conn_context=conn, n_estimators=3,
    max_features=3, random_state=2,
    split_threshold=0.00001, calculate_oob=True,
    min_samples_leaf=1, thread_ratio=1.0)
    ```
    
*   SAP HANA DataFrame, which basically comes with a set of methods for analyzing data in SAP HANA without the need to bring the data into the client. To use an SAP HANA DataFrame, we need to create a ConnectionContext object then use the methods provided in the library to create an SAP HANA DataFrame. The following code snippet is a short example of how you can create a simple SAP HANA DataFrame:
    
    ```
    ConnectionContext('address', port, 'user', 'password')
    ```
    
*   SAP Data Intelligence has the hana\_ml libraries already installed in the JupyterLab environment. If needed, older versions can be easily installed into the notebook.
    

For more details on hana\_ml libraries, refer to [http://s-prs.co/501406](http://s-prs.co/501406).

So far, we’ve talked about the standard libraries offered by SAP for data science experiments. In the next section, we’ll cover the popular Python-based libraries that can give you an edge in your data science experiments.

### 9.2.3    Popular Python Libraries

In some cases, the standard libraries won’t be enough for complex data science experiments. So, we should always be looking out for libraries to help ease the experimentation process as well as add value to common functions like data processing, modeling, visualization, and much more. For our purposes, so many Python libraries are already available in the market. Let’s talk about a few of the most essential and time-tested libraries:

*   Python Data Analysis Library (popularly known as pandas) falls under the Data Cleansing and Transformation category and is an open-source Python package that provides high-performance, easy-to-use data structures and data analysis tools for labeled data. Using the Python programming language, persuasive syntaxes and rich functionalities enable you to deal with missing data. SAP hana\_ml uses pandas for SAP HANA DataFrame conversion.
    
*   Scientific Python, also known as SciPy, is another free and open-source Python library used extensively in data science for high-level computations and comes under Data Processing and Modeling category. This library encapsulates modules for efficient mathematical routines like linear algebra, interpolation, optimization, integration, and statistics.
    
*   Matplotlib is one the most popular plotting libraries for visualization in Python. This library helps generate Data Visualizations, such as two-dimensional diagrams and graphs (histograms, scatterplots, non-Cartesian coordinates graphs). With a bit of effort, Matplotlib can create just about any visualization, including line plots, scatterplots, area plots, bar charts, histograms, pie charts, stem plots, and more. Another simple but powerful visualization library built on top of Matplotlib is Seaborn, which is primarily designed for visualizing statistical models—heatmaps and other types of visualizations that summarize data and overall data distributions.
    
*   Considered one of the best Python libraries for working with complex data, Scikit-Learn is built on top of the Matplotlib, NumPy, and SciPy libraries and features a range of simple yet efficient tools for accomplishing Data Analysis and Mining tasks. Scikit-Learn is one of the most rapidly developing Python libraries.
    
*   Google TensorFlow is an AI library for Data Modeling that helps developers create large-scale neural networks with many layers. Developed by Google, this open-source symbolic math library for numerical computation uses data flowgraphs.
    

The list of popular Python-based libraries than can help you conduct data science experiments is quite long. In the next section, we’ll start working with some of them.

### 9.2.4    Various Library Options

As shown in [Figure 9.7](#09_002.html#f9.7), several other Python-based libraries are already available in the market for various purposes under the specified categories, and you can pick any of them for your data science experiment. However, for all these libraries, one thing in common is that you’ll need to install the necessary modules inside a notebook using the pip command, which is a package manager for Python packages or modules. Open a notebook from the machine learning scenario manager and install any new Python library with the following commands:

```
pip install sklearn
pip install hdbcli
pip install matplot
```

Refer to [Section 9.3.2](#09_003.html#h9.3.2) for more details on installing Python libraries inside Jupyter Notebook.

[![Python Libraries](bilderklein/klein09_007.png)](img-f9.7.html) 

**Figure 9.7**    Python Libraries

So far, we’ve talked about Jupyter Notebook and how you can use it to perform various experiments on the SAP Data Intelligence platform. In the next section, we’ll walk you through the steps for building an machine learning scenario using Jupyter Notebook based on a specific business case. So, let’s start by describing our use case first before jumping in to executing it.

## 9.3    Use Case

As we were writing this chapter, the whole world has been embroiled in the most difficult time we’ve seen in a century. Widespread suffering, especially for frontline heroes serving all of us to fight the COVID-19 pandemic. On various occasions, when we as consultants or enterprise users start thinking about a typical use case, we fall into business use cases. This time, we decided to think outside the box and consider a use case to meet the needs of the moment. This use case is all about leveraging data science to fight a pandemic through analysis and prediction. Yes, we’re talking about using Jupyter Notebook on SAP Data Intelligence to analyze COVID-19 data. We hope to develop intelligence out of the data, which can be helpful towards similar work in the future. For our experiment, we’ll source our data from the COVID-19 Data Repository published by the Center for Systems Science and Engineering (CSSE) at Johns Hopkins University, which is available on GitHub at [https://github.com/CSSEGISandData/COVID-19](https://github.com/CSSEGISandData/COVID-19). The Johns Hopkins CSSE aggregates data from various sources, such as the World Health Organization (WHO) and national and regional public health institutions. The data is made freely available and is updated every day.

This data is updated every 24 hours from various official sources. You can access the raw files directly from the csse\_covid\_19\_time\_series directory, as shown in [Figure 9.8](#09_003.html#f9.8).

[![Data Repository](bilderklein/klein09_008.png)](img-f9.8.html) 

**Figure 9.8**    Data Repository

On a positive note, we’ll work with an optimistic scenario, using data across various countries representing recovery rates from COVID-19. We’ll build a notebook that will create a visualization from the data using the various Python-based libraries we discussed earlier. But first let’s quickly look at the data from the repository that we’ll use, as shown in [Figure 9.9](#09_003.html#f9.9).

[![Time Series Data Preview](bilderklein/klein09_009.png)](img-f9.9.html) 

**Figure 9.9**    Time Series Data Preview

### 9.3.1    Setting Up the Scenario

The first essential step is to set up a new scenario using the machine learning scenario manager. Log on to your SAP Data Intelligence instance and click the ML Scenario Manager tile from the launchpad, as shown in [Figure 9.10](#09_003.html#f9.10).

[![ML Scenario Manager Tile](bilderklein/klein09_010.png)](img-f9.10.html) 

**Figure 9.10**    ML Scenario Manager Tile

Inside the machine learning scenario manager ([Figure 9.11](#09_003.html#f9.11)), you can choose a preexisting scenario and a notebook, but for our example, let’s go ahead and create a fresh scenario.

[![Machine Learning Scenario Manager CockpitMachine learning scenario manager cockpit](bilderklein/klein09_011.png)](img-f9.11.html) 

**Figure 9.11**    Machine Learning Scenario Manager Cockpit

Click the + icon in the top-right corner of the table, shown in [Figure 9.12](#09_003.html#f9.12), to create a new scenario. Once the Create Scenario popup window appears, as shown in [Figure 9.13](#09_003.html#f9.13), provide a name and a description for your machine learning scenario and then click the Create button. For our example, create a new scenario called “ML\_Demo\_Scenario” (or you can input any other name).

[![Creating a New Scenario](bilderklein/klein09_012.png)](img-f9.12.html) 

**Figure 9.12**    Creating a New Scenario

[![New Machine Learning Scenario](bilderklein/klein09_013.png)](img-f9.13.html) 

**Figure 9.13**    New Machine Learning Scenario

Once the scenario is successfully created, the next step is to create a notebook within the scenario with a name and description. Notice that the Version History pane on the right has already started keeping track of your machine learning scenario, with the first version of the scenario. Version 1 of the scenario shown in [Figure 9.12](#09_003.html#f9.12) is always blank, which means that it doesn’t contain any artifacts such as notebooks or pipelines. As soon as you add an artifact, the system will indicate that the version has changed by adding an icon next to the version number. This indicator ultimately helps you continue working without needing to create a new version every time. For example, you can execute or deploy pipelines directly from your “draft” version. In this context, note that you can export versions of a machine learning scenario from a development environment and import it into other systems (test, quality, or production environments). Thus, you can consistently change scenarios in one particular development system, but you can make changes to scenarios in the target system as needed. During export, scenarios are combined into a ZIP file containing only pipelines and notebooks from the scenario. Other items, like external dependencies (which can include custom operators, subengines, Docker files, and images) are not currently supported. Also, executions, deployments, and artifacts are not included while exporting.

With these considerations in mind, let’s return to our use case. To navigate further inside the machine learning scenario manager, click on our newly created scenario. You’ll be navigated into the scenario, as shown in [Figure 9.14](#09_003.html#f9.14).

[![Inside the Machine Learning Scenario ManagerMachine learning scenario manager](bilderklein/klein09_014.png)](img-f9.14.html) 

**Figure 9.14**    Inside the Machine Learning Scenario Manager

To create a notebook, click the + button in the top-right corner of the Notebooks table, and a new popup window will appear, as shown in [Figure 9.15](#09_003.html#f9.15).

[![Create Notebook Popup Window](bilderklein/klein09_015.png)](img-f9.15.html) 

**Figure 9.15**    Create Notebook Popup Window

Creating a new notebook will redirect you to your JupyterLab instance on SAP Data Intelligence. When you first open the notebook created in the previous step, the kernel selection popup window should automatically open. Choose Python 3 as your kernel, as shown in [Figure 9.16](#09_003.html#f9.16), and click Select.

[![Select Kernel Popup Window](bilderklein/klein09_016.png)](img-f9.16.html) 

**Figure 9.16**    Select Kernel Popup Window

You can also view the other supported kernels through the dropdown list. Jupyter Notebook supports more than a one programming language, and the element that instantiates a session and runs the code of a cell is called the kernel.

The currently active kernel’s display name is visible in the top-right corner of the working area, as shown in [Figure 9.17](#09_003.html#f9.17). In most cases, you’ll also see a logo, which helps identify the kernel, and when you start a new notebook, the default kernel will generally be whatever kernel you last explicitly selected.

[![Notebook Working Area](bilderklein/klein09_017.png)](img-f9.17.html) 

**Figure 9.17**    Notebook Working Area

### 9.3.2    Scripting

Now, that we’re ready with our notebook working area, let’s start scripting. At the beginning of our script, we’ll first need to import all the necessary libraries. In our example, we’ll use some of the most popular Python libraries, including numpy, pandas, matplotlib, and seaborn, which we discussed in the previous section. Apart from seaborn, all other modules will need to be imported, so we must explicitly import the seaborn module. Otherwise, we’ll get the error shown in [Figure 9.18](#09_003.html#f9.18).

[![Module Missing ErrorModule missing error](bilderklein/klein09_018.png)](img-f9.18.html) 

**Figure 9.18**    Module Missing Error

Importing any library is pretty easy—just use pip install seaborn command, as shown in [Figure 9.19](#09_003.html#f9.19).

[![Seaborn ModuleSeaborn module Installation Log](bilderklein/klein09_019.png)](img-f9.19.html) 

**Figure 9.19**    Seaborn Module Installation Log

So, in the first cell of the notebook paste the code snippet shown in [Figure 9.20](#09_003.html#f9.20) and execute the cell. 

[![Importing the Necessary Modules](bilderklein/klein09_020.png)](img-f9.20.html) 

**Figure 9.20**    Importing the Necessary Modules

Also, to set the seaborn module defaults into the current context, simply call the set() function after importing the module as shown in the snippet.

In the next part of our experiment, we’ll start building the function required to plot the visualization of the COVID-19 recovery rate data. But, first, we’ll need to insert a new cell by clicking the + icon, as shown in [Figure 9.21](#09_003.html#f9.21).

The plot\_data\_chart function allows you to display the data and easily produce visualizations under different conditions. This function uses the following parameters:

*   filename  
    This parameter is for passing the filename to be used for processing and permissible values are 'Confirmed', 'Fatality', 'Recovered'
    
*   selected\_countries  
    List of countries to be considered for visualization
    
*   view  
    'absolute' to display frequencies, 'inhabitant' to display per capita, and 'area' to correct for land surface area
    
*   number  
    The number used for correction, for ex. 1000000 inhabitants or 10000 km2 area
    
*   startdate  
    The start date for data to be displayed, for ex. '2020-02-29'
    
*   enddate  
    The end date for data to be displayed, for ex. '2020-04-02'
    

[![Inserting a New Cell](bilderklein/klein09_021.png)](img-f9.21.html) 

**Figure 9.21**    Inserting a New Cell

In the first part of the function, shown in [Figure 9.22](#09_003.html#f9.22), we’ll define the necessary logic to pick the data file based on the filename, which is passed as a parameter, along with plotting property value for “view” and “ent”. Further, based on the value, the title for the chart will be determined by concatenating the property values.

[![Function plot\_data\_chart](bilderklein/klein09_022.png)](img-f9.22.html) 

**Figure 9.22**    Function plot\_data\_chart

As shown in [Figure 9.23](#09_003.html#f9.23), in the next part of the function, we’ll read the source data, a CSV file, based on the filename, which was passed as a parameter. To read the CSV file, we’ll use the read\_csv function, which is an important pandas function to read and perform operations on CSV files.

[![Read CSV File](bilderklein/klein09_023.png)](img-f9.23.html) 

**Figure 9.23**    Read CSV File

Beside reading the .csv files directly from the URL, SAP Data Intelligence comes with various provisions for uploading files directly inside a working area, or you can create a new data collection by uploading a CSV file through the SAP Data Intelligence machine learning data manager. To upload the file into the working area, click the Upload Files button, as shown in [Figure 9.24](#09_003.html#f9.24). Once the file has been uploaded, you can directly access the file by name instead of URL. Next, we’ll run the read\_csv function on the file with the following code:

```
pnds.read_csv(time_series_covid19_recovered_global.csv) 
```

[![Uploading the Data Files](bilderklein/klein09_024.png)](img-f9.24.html) 

**Figure 9.24**    Uploading the Data Files

Inside the machine learning data manager, you can create a new data workspace and a new data collection. Then, you can upload the CSV files and connect to the data collection from your notebook.

Now that we have data to use after reading the data from the CSV file, as shown in [Figure 9.25](#09_003.html#f9.25), we’ll cleanse and process this data. After all, data almost never comes in a form that is ready for use, and in most data science projects, a great deal of time is often spent on data cleansing.

[![Data Cleansing and Processing](bilderklein/klein09_025.png)](img-f9.25.html) 

**Figure 9.25**    Data Cleansing and Processing

Inside the code snippet shown in [Figure 9.25](#09_003.html#f9.25), after receiving the SAP DataFrame out of the CSV files, we’re dropping a few of columns including ’Lat’, ’Long’, and ’Province/State’ using the drop function from the SAP DataFrame data\_set\_1 and also applying the melt() function to massage the SAP DataFrame object data\_set\_1 into a format where one or more columns are identifier variables (i.e., ’Country/Region’) can be used as identifier variables in our case. Next, we'll rename the SAP DataFrame data\_set\_1 columns and apply the merge() method to merge SAP DataFrame data\_set\_1 and data\_set\_2, and finally, we’ll invoke sort\_values() to sort the data in ascending order.

### 9.3.3    Data Plotting

It’s time to plot the merged and sorted data for visualization, and in this case, as shown in code snippet in [Figure 9.26](#09_003.html#f9.26), we’re going to use the figure() function in the pyplot module of the matplotlib library to create a new figure. The matplotlib.pyplot is a collection of command-style functions so that the matplotlib library works like MATLAB. Each pyplot function makes some change to a figure (e.g., creating a figure, creating a plotting area in a figure, plotting lines in the plotting area, decorating the plot with labels, etc.).

[![Data Plotting](bilderklein/klein09_026.png)](img-f9.26.html) 

**Figure 9.26**    Data Plotting

As the name implies, the savefig() method from the matplotlib.pyplot collection can be used to save the figure created after data has been plotted. Finally, we’ve completed drafting the plot\_data\_chart function, and we’re ready to run the cell and check for errors. The entire code snippet is shown in [Figure 9.27](#09_003.html#f9.27), and you can easily download the entire source code from this dedicated GitHub repository for the entire book: [http://s-prs.co/501404](http://s-prs.co/501404).

[![Final Code](bilderklein/klein09_027.png)](img-f9.27.html) 

**Figure 9.27**    Final Code

### 9.3.4    Code Execution

After placing all our code cells in place, it’s time to look at the outcome. Let’s now prepare to run the code. As shown in [Figure 9.28](#09_003.html#f9.28), we must define a list\_of\_countries to be considered for the visualization and pass this value as a parameter while invoking the plot\_data\_chart function.

[![Defining the Country List](bilderklein/klein09_028.png)](img-f9.28.html) 

**Figure 9.28**    Defining the Country List

That’s it! In the last cell of our notebook, insert the code snippet shown in [Figure 9.28](#09_003.html#f9.28) and execute this cell to arrive at the visualization shown in [Figure 9.29](#09_003.html#f9.29).

[![Invoking the Function](bilderklein/klein09_029.png)](img-f9.29.html) 

**Figure 9.29**    Invoking the Function

The chart shown in [Figure 9.30](#09_003.html#f9.30) shows the recovery case rate per 1,000,000 persons across various countries. As you can see, the curve is promising, and we all hope that soon we’ll be out of this misery.

[![Final Run Output](bilderklein/klein09_030.png)](img-f9.30.html) 

**Figure 9.30**    Final Run Output

Back in our notebook, note that the invocation of the savefig() method generated the covid.png file inside the file manager on the left side of the working area, as shown in [Figure 9.31](#09_003.html#f9.31).

The steps we’ve executed so far should give you a fair idea about how you can perform various data science experiments using Python and Jupyter Notebook on the SAP Data Intelligence platform. These kinds of experiments are a key prerequisite to building workable, high-performance machine learning models for enterprise use, social engagement, or any other business purpose.

[![Saved Image](bilderklein/klein09_031.png)](img-f9.31.html) 

**Figure 9.31**    Saved Image

## 9.4    Summary

After successfully completing the steps we’ve described in this chapter, we hope that your understanding of the SAP Data Intelligence platform has been expanded, and your use of the platform will be purposeful and easily apply in your work. Before we close this chapter and move to automating data science projects, a quick recap might be beneficial. In this chapter, we covered various topics around performing machine learning experiments by leveraging the embedded Jupyter Notebook, the SAP Data Intelligence Python SDK, and various Python-based libraries. For a deeper understanding, we walked you through building a scenario based on a pandemic dataset that plotted a visualization of the data.

# 10    Automated Machine Learning Data Science Automation

This chapter offers an in-depth look at a trending and fascinating topic—data science automation, also called AutoML. During this chapter, you’ll learn about the significance of AutoML with respect to data science experiments, especially its features and components on SAP Data Intelligence. Finally, we’ll walk you through the steps for building a machine learning scenario by leveraging AutoML.

Automated machine learning (AutoML) is all about using machine learning techniques to automate the process of applying machine learning. Not a new concept to the market, earlier releases of AutoML systems, like Auto-WEKA, auto-sklearn, and H2O, are only designated for the automatic selection of algorithms and the tuning of hyperparameters, which can be helpful for automating some work for data scientists, but not useful for, say, the day-to-day work of a data analyst. Over the past decade, rapid advances have been made in AutoML systems. Today’s AutoML systems can automate the most complicated and time-consuming parts of the development lifecycle of an enterprise-level artificial intelligence (AI), called feature engineering, which typically takes months when traditional methods are followed. Furthermore, the adoption of AI-driven feature engineering allows users to discover and create new features for data science processing automatically. Should a data scientist be concerned about their role in an automated process? Not at all! Rather, data science users like business analysts, data engineers, and other tech-savvy members can leverage their high-level domain expertise to make more valuable contributions towards the development of machine learning and AI model use cases that are valuable to the organization. Additionally, data scientists can help enterprises adopt data science techniques much faster, without worrying too much about timelines for building scenarios. Sophisticated analytics can be available in days! Isn’t that amazing?

In this chapter, you’ll learn how to automate your data science experiments with AutoML, which we’ll briefly introduce in the context of SAP Data Intelligence in [Section 10.1](#10_001.html#h10.1). Then, we’ll describe the powerful features of AutoML systems in [Section 10.2](#10_002.html#h10.2). Finally, in [Section 10.3](#10_003.html#h10.3), we’ll walk you through the process of configuring AutoML step by step, including testing.

## 10.1    AutoML on SAP Data Intelligence

SAP Data Intelligence includes a comprehensive set of features that complement each piece of feature engineering in the right fashion. Game-changing capabilities offered by the SAP Data Intelligence platform in the context of AutoML mean data scientists can build machine learning scenarios while automatically creating the necessary feature tables from relational data sources or even flat files. Let’s examine the process of building an automated AutoML scenario, as shown in [Figure 10.1](#10_001.html#f10.1).

[![AutoMLAutoMLprocess cycle Process Cycle](bilderklein/klein10_001.png)](img-f10.1.html) 

**Figure 10.1**    AutoML Process Cycle

As shown in [Figure 10.1](#10_001.html#f10.1), the automated machine learning process starts after uploading a dataset and choosing the target variable to address a business problem. Automating these steps allows for greater agility in problem-solving and the democratization of data science so that people without extensive programming knowledge can be included.

## 10.2    Features of AutoML

Now that our introduction is complete, let’s dive more deeply into the many features offered by AutoML, such as the following capabilities:

*   AutoML acts on your training and test datasets, target outcome, and budget and automatically performs the necessary preprocessing steps including feature selection, feature engineering, and normalization. Next, AutoML starts the iterative training of a variety of machine learning models and optimizes their hyperparameters. The outcome is a machine learning pipeline that you can subsequently deploy.
    
*   The AutoML cockpit is a graphical environment for data scientists, business analysts, and line of business (LOB) users that is fully equipped with tools for executing experiments based on datasets and for gaining access to unseen insights through machine learning models.
    
*   The AutoML cockpit is a central place for viewing information about the autogenerated artifacts including a model overview, execution status, a metric graph, detailed analysis of the generated model, and deployment information. You can navigate into and out of the cockpit even while the system is generating models.
    
*   Multiple sections of the AutoML cockpit can bring together various aspects of your programmed experiments and model executions. The summary section displays the data used in the experiment, the experiment’s task, the target metric, and the budget, and the leaderboard sorts models by the target metric on the specified test dataset. The overview section focuses on deployment.
    

## 10.3    AutoML Step-by-Step

Enough theory, let’s build something interesting harnessing the power of AutoML on SAP Data Intelligence. First, we’ll need a use case. In this chapter, we’ll build an AutoML scenario based on a dataset from the National Institute of Diabetes and Digestive and Kidney Diseases. The primary objective of this dataset is to diagnostically predict whether a patient has diabetes, based on certain diagnostic measurements included in the dataset. The dataset is collated by applying various constraints on top of a larger dataset and focuses on several medical predictor variables, such as Pregnancies, Glucose, Blood Pressure, Insulin, BMI, and Age. Our single target variable is called Outcome. [Figure 10.2](#10_003.html#f10.2) shows a snapshot of the data we’ll use when building this AutoML scenario for diagnosing diabetes in a patient based on certain criteria.

[![Data SnapshotData snapshot](bilderklein/klein10_002.png)](img-f10.2.html) 

**Figure 10.2**    Data Snapshot

While building this use case, we’ll demonstrate more interesting features available on the SAP Data Intelligence platform through the machine learning data manager. Out of our source dataset, we’ll create a data collection that we’ll further use for training and testing purpose. Thus, in the next section, we’ll start by setting up the data collection required for our AutoML scenario.

### 10.3.1    Configuring the Training Data Collection

In this section, we’ll first create a data workspace inside the machine learning data manager. Log on to your SAP Data Intelligence instance and click the ML Data Manager tile from the launchpad, as shown in [Figure 10.3](#10_003.html#f10.3).

[![Machine Learning Data Manager](bilderklein/klein10_003.png)](img-f10.3.html) 

**Figure 10.3**    Machine Learning Data Manager

In a nutshell, the machine learning data manager lets you organize data into data workspaces and data collections. A workspace represents the use case we’re trying to build; within a workspace, you can create data collections for each set of business data. As shown in [Figure 10.4](#10_003.html#f10.4), let’s first create a data workspace called “DW\_001” by clicking the Create button in the top-right corner.

[![Create Data Workspace](bilderklein/klein10_004.png)](img-f10.4.html) 

**Figure 10.4**    Create Data Workspace

After entering a name and a description for the workspace, click the Create button, and the newly created workspace will now appear in the workspace list. Note that the workspace will only be created successfully if you have appropriate permissions to access the data lake. Otherwise, you won’t be able to create data workspaces or data collections in the machine learning data manager.

Now, let’s check the connection to our data lake, which is in our case is called DI\_DATA\_LAKE, as shown in [Figure 10.5](#10_003.html#f10.5). You can quickly test the connection inside SAP Data Intelligence under the Connections tab. If successfully connected, you should see the success message shown in [Figure 10.6](#10_003.html#f10.6).

[![Data LakeData lake Connections](bilderklein/klein10_005.png)](img-f10.5.html) 

**Figure 10.5**    Data Lake Connections

[![Data Lake Connection TestData lakeconnection test](bilderklein/klein10_006.png)](img-f10.6.html) 

**Figure 10.6**    Data Lake Connection Test

Next, in our newly created workspace, you’ll need to create a data collection into which you’ll upload the source data, which in our use case is the Pima Indians Diabetes dataset available at [https://www.kaggle.com/uciml/pima-indians-diabetes-database](https://www.kaggle.com/uciml/pima-indians-diabetes-database).

To create a new data collection, click the Create button located in the top-right corner of the Data Collections table, as shown in [Figure 10.7](#10_003.html#f10.7).

Enter a name and description for the data collection, as shown in [Figure 10.8](#10_003.html#f10.8), and click Create.

[![Data Workspace DetailData workspace](bilderklein/klein10_007.png)](img-f10.7.html) 

**Figure 10.7**    Data Workspace Detail

[![Create Data Collection Popup Window](bilderklein/klein10_008.png)](img-f10.8.html) 

**Figure 10.8**    Create Data Collection Popup Window

After the data collection is successfully created, you’ll be navigated to the data collection details page, shown in [Figure 10.9](#10_003.html#f10.9), which displays all the contents of the data collection.

Then, our data upload step starts by clicking Edit in Metadata Explorer, which will navigate you to Metadata Explorer, shown in [Figure 10.10](#10_003.html#f10.10). Now, you can upload the files we downloaded in the previous step to the data collection.

Click on the upload files icon, which will open the file upload dialog box. Click the + icon to select the .csv file to upload. Once the selected, the file will appear on the screen with the upload status “Pending,” as shown in [Figure 10.11](#10_003.html#f10.11).

[![Data Collection Detail](bilderklein/klein10_009.png)](img-f10.9.html) 

**Figure 10.9**    Data Collection Detail

[![Metadata ExplorerMetadata explorer](bilderklein/klein10_010.png)](img-f10.10.html) 

**Figure 10.10**    Metadata Explorer

[![Upload Files Popup Window](bilderklein/klein10_011.png)](img-f10.11.html) 

**Figure 10.11**    Upload Files Popup Window

Click the Upload button at the bottom of the popup window to start the upload process. As shown in [Figure 10.12](#10_003.html#f10.12), the progress bar indicates the upload progress.

[![File Uploaded](bilderklein/klein10_012.png)](img-f10.12.html) 

**Figure 10.12**    File Uploaded

Once the progress indicator shows 100%, the data upload to the data lake is complete. You can now close the Metadata Explorer and switch back to data collection details page in the machine learning data manager, as shown in [Figure 10.13](#10_003.html#f10.13).

[![Fact SheetFact sheet](bilderklein/klein10_013.png)](img-f10.13.html) 

**Figure 10.13**    Fact Sheet

Inside the Metadata Explorer, you can further navigate to the fact sheet shown in [Figure 10.13](#10_003.html#f10.13), which basically displays the dataset’s columns as well as its inferred data types. On the other end the Data Preview tab, shown in [Figure 10.14](#10_003.html#f10.14), provide a quick sneak peek of the data uploaded from the .csv into the data collection.

[![Data Preview](bilderklein/klein10_014.png)](img-f10.14.html) 

**Figure 10.14**    Data Preview

Go back to the Content tab, shown in [Figure 10.15](#10_003.html#f10.15), and you should see the uploaded file in the content list. If not, you might need to refresh the screen by clicking the refresh icon next to the Edit in Metadata Explorer button.

[![Data Collection Detail](bilderklein/klein10_015.png)](img-f10.15.html) 

**Figure 10.15**    Data Collection Detail

Now, navigate to the Features list tab, as shown in [Figure 10.16](#10_003.html#f10.16), to preview and finalize the data types. In the Source File input field, you must select the dataset we created in the previous step.

[![Select Source File Popup Window](bilderklein/klein10_016.png)](img-f10.16.html) 

**Figure 10.16**    Select Source File Popup Window

Upon selecting the source, as shown in [Figure 10.17](#10_003.html#f10.17), the Features table will be populated with all the column names, their associated data types, and the data they contain.

[![Update Data Feature](bilderklein/klein10_017.png)](img-f10.17.html) 

**Figure 10.17**    Update Data Feature

Confirm that the Feature and Type columns are correctly categorized, as shown in [Figure 10.17](#10_003.html#f10.17). For our use case, we changed the Type of the Outcome column to Categorical. Finally, click Save at the bottom of the Features list tab.

Although we’re done creating our training data collection, we still need to create a data collection for our testing dataset, which we need to create based on our training data. So, let’s start on this process, which is similar to the steps we just completed.

### 10.3.2    Configuring the Test Data Collection

While preparing our testing data, the data collection creation, file uploading, and features list-related activities are no different than in the previous section when we set up the training data collection. By the end, our Data Collections list should have two entries, as shown in [Figure 10.18](#10_003.html#f10.18), one for training and one for testing.

[![Training and Test Data Collection](bilderklein/klein10_018.png)](img-f10.18.html) 

**Figure 10.18**    Training and Test Data Collection

We have successfully executed the first step for creating the test and training data collections required for the AutoML scenario. Now, in the next section, we’ll execute the actual AutoML steps and, believe us, the fun has just begun!

### 10.3.3    Setting Up AutoML

Now, we’re ready to set up AutoML. Click the AutoML tile from the launchpad to navigate to the AutoML app, as shown in [Figure 10.19](#10_003.html#f10.19).

[![Navigating to the AutoML App](bilderklein/klein10_019.png)](img-f10.19.html) 

**Figure 10.19**    Navigating to the AutoML App

Inside the AutoML app, we’ll start by creating a machine learning scenario. The first screen will show a list of available machine learning scenarios. Click the Create button in the top-right corner of the scenarios list to create a new scenario. Maintain the Name and Business Question fields for our new scenario, as shown in [Figure 10.20](#10_003.html#f10.20).

[![Create AutoML Scenario Popup Window](bilderklein/klein10_020.png)](img-f10.20.html) 

**Figure 10.20**    Create AutoML Scenario Popup Window

After successful creation, the newly created machine learning scenario appears in the scenarios list, as shown in [Figure 10.21](#10_003.html#f10.21).

[![Machine Learning Scenarios List](bilderklein/klein10_021.png)](img-f10.21.html) 

**Figure 10.21**    Machine Learning Scenarios List

The next important step for setting up our AutoML scenario is creating a new execution. To create the execution, select the machine learning scenario to navigate further and the click Create. The Create Execution wizard opens, as shown in [Figure 10.22](#10_003.html#f10.22). In Step 1, select the training and test datasets we uploaded earlier in the machine learning data manager workspace.

[![Selecting Datasets](bilderklein/klein10_022.png)](img-f10.22.html) 

**Figure 10.22**    Selecting Datasets

Click the load data set icon to launch the Select Dataset popup window, shown in [Figure 10.22](#10_003.html#f10.22), and then choose the workspace, which in our case is DW\_001. Once you select the workspace, you’ll see a list of data collections inside the workspace, which in our case are called DC\_001 and DC\_002, as shown in [Figure 10.23](#10_003.html#f10.23).

[![Selecting a Workspace](bilderklein/klein10_023.png)](img-f10.23.html) 

**Figure 10.23**    Selecting a Workspace

Select DC\_001 to navigate further and then select the .csv file associated with the collection, as shown in [Figure 10.24](#10_003.html#f10.24).

[![Selecting the Data Collection CSV file](bilderklein/klein10_024.png)](img-f10.24.html) 

**Figure 10.24**    Selecting the Data Collection CSV file

Repeat the same step to select the Test Dataset. You won’t be able to proceed to Step 2 unless you provide both datasets as inputs, as shown in [Figure 10.25](#10_003.html#f10.25).

[![Step 1 Complete](bilderklein/klein10_025.png)](img-f10.25.html) 

**Figure 10.25**    Step 1 Complete

Once both the training and test datasets are connected, click the Step 2 button to enter evaluation-specific information for the AutoML scenario, as shown in [Figure 10.26](#10_003.html#f10.26).

[![Step 2: Evaluation Configuration](bilderklein/klein10_026.png)](img-f10.26.html) 

**Figure 10.26**    Step 2: Evaluation Configuration

Now, you’ll need to provide some configuration information, as shown in [Figure 10.26](#10_003.html#f10.26), with respect to our AutoML prediction scenario, which includes the following fields:

*   Experiment Target  
    The intended outcome, or what our model should make a prediction about. In our case, based on various medical factors, our model should predict whether a patient is diabetic or not. Inside our data, we have a column called Outcome, which indicates the diagnoses by a 0 or 1.
    
*   Metric  
    For the Metric dropdown list, select the Log Loss option, which is an important classification metric based on probabilities. The Log Loss metric considers the probabilities underlying models, not just the final output of the classification.
    
*   Task  
    When you select Log Loss in the Metric dropdown list, the Task field will be set to Classification.
    

After configuring the Evaluation part, we’re ready to configure Step 3, which is all about defining the budget. So, click the Step 3 button, shown in [Figure 10.27](#10_003.html#f10.27), to configure the Budget section.

[![Budget Configuration](bilderklein/klein10_027.png)](img-f10.27.html) 

**Figure 10.27**    Budget Configuration

Inside the Budget section, we’ll define how long we want to train and test the model for. For our use case, we’ll simply use the default value of 30 minutes, as shown in [Figure 10.28](#10_003.html#f10.28). Finally, click the Review button at the bottom, which will display the inputs for all three sections that we’ve configured so far. Make sure everything looks right before final execution and then click the Create button.

[![Execution Configuration](bilderklein/klein10_028.png)](img-f10.28.html) 

**Figure 10.28**    Execution Configuration

The execution will then run for the allocated amount of time, which is in our case 30 minutes. During the execution, you can keep track of its progress and monitor the models being trained through the execution dashboard, shown in [Figure 10.29](#10_003.html#f10.29). On this screen you can view performance progression, execution status, budget consumption, and metrics such as the time vs. metric, along various other metadata.

[![Performance Cockpit](bilderklein/klein10_029.png)](img-f10.29.html) 

**Figure 10.29**    Performance Cockpit

On the other hand, the Leaderboard tab of the screen shows a list of pipelines created, based on trained models along with information like the Type, Log Loss score, and training duration (Time in minutes) for each pipeline.

As shown in [Figure 10.30](#10_003.html#f10.30), each data point on the performance progression graph corresponds to one model. In this graph, the horizontal axis represents time, and the vertical metric shows the target metric we defined previously.

[![Performance ProgressionPerformance progression Graph](bilderklein/klein10_030.png)](img-f10.30.html) 

**Figure 10.30**    Performance Progression Graph

By clicking on an individual pipeline, you can navigate inside to view further details and ultimately decide whether to deploy them for the inference. As shown in [Figure 10.31](#10_003.html#f10.31), we’ll use the Naïve Bayes Classifier Pipeline to look into the pipeline steps, details as well as the hyperparameters in the Feature Processing & Engineering section.

[![Leaderboard](bilderklein/klein10_031.png)](img-f10.31.html) 

**Figure 10.31**    Leaderboard

###### Note

The Naïve Bayes Classifier Pipeline is a simple probabilistic classifier based on applying Bayes’ theorem with strong independence assumptions between the features.

[![Pipeline Layout](bilderklein/klein10_032.png)](img-f10.32.html) 

**Figure 10.32**    Pipeline Layout

To deploy the naïve Bayes classifier pipeline so we can later call the trained model, click the Deploy button located in the top-right corner of the screen, as shown in [Figure 10.32](#10_003.html#f10.32).

Once the deployment is complete, a machine learning scenario (pipeline) will be accessible inside the machine learning scenario manager, as shown in [Figure 10.33](#10_003.html#f10.33). In our case, the system generated the AutoML scenario labeled Automl\_Scenario.

[![Machine Learning Scenario ManagerMachine learning scenario manager](bilderklein/klein10_033.png)](img-f10.33.html) 

**Figure 10.33**    Machine Learning Scenario Manager

As shown in [Figure 10.34](#10_003.html#f10.34), from a version tracking perspective, the machine learning scenario manager also keeps a track of different versions for any given scenario. Click on a scenario name from the list to navigate inside the autogenerated scenario.

[![Scenario Manager Version](bilderklein/klein10_034.png)](img-f10.34.html) 

**Figure 10.34**    Scenario Manager Version

Inside the scenario shown in [Figure 10.35](#10_003.html#f10.35), notice that two different pipelines have been automatically generated: one for inferences and the other for training. As shown in in [Figure 10.35](#10_003.html#f10.35), the label Created with AutoML has been appended next to the name of the scenario. The screen also shows the current execution status of the AutoML scenario, along with the progress flow.

[![Automl\_Scenario](bilderklein/klein10_035.png)](img-f10.35.html) 

**Figure 10.35**    Automl\_Scenario

[![Autogenerated Pipeline](bilderklein/klein10_036.png)](img-f10.36.html) 

**Figure 10.36**    Autogenerated Pipeline

From the scenario editor, you can open any of these autogenerated pipelines, as shown in [Figure 10.36](#10_003.html#f10.36). Let’s move forward to execution, where we can really evaluate the AutoML scenario we’ve built so far using AutoML features (as seen in [Figure 10.37](#10_003.html#f10.37)). The key information you’ll need is the service URL of the naïve Bayes pipeline that we deployed in previous steps.

[![AutoML Scenario Section](bilderklein/klein10_037.png)](img-f10.37.html) 

**Figure 10.37**    AutoML Scenario Section

Let’s navigate back to the AutoML app from the launchpad to view the details of the execution, which we created earlier. Once inside the execution screen, shown in [Figure 10.38](#10_003.html#f10.38), to get the deployment URL, click the Link URL inside the header section, which will display the pipeline’s URL in a tooltip, as shown in [Figure 10.39](#10_003.html#f10.39).

[![Obtain Service URL](bilderklein/klein10_038.png)](img-f10.38.html) 

**Figure 10.38**    Obtain Service URL

[![Deployment URL](bilderklein/klein10_039.png)](img-f10.39.html) 

**Figure 10.39**    Deployment URL

Make note of this URL since you’ll need this information to execute a test run of our AutoML scenario. For the test run, we’ll use Postman, but you can use any other Representational State Transfer (REST) client to make the service call. To download Postman, go to [https://www.postman.com/downloads/](https://www.postman.com/downloads/).

At this point, we’re done with our required configuration. Now, let’s harvest the fruits of our hard work so far. In the next section, we’ll run and test our AutoML scenario using Postman.

### 10.3.4    Testing AutoML

To start, first launch Postman and create a POST request using the deployment URL you noted earlier in the previous step. Before finally making the service call, we must prepare this POST request with additional information. After adding the URL, under the Authorization tab, you’ll need to select Basic Auth from the Type dropdown list on the left, as shown in [Figure 10.40](#10_003.html#f10.40). Remember that you must use the user ID that you used to log on to the SAP Data Intelligence instance, which is in our case default\\system.

[![Basic Authorization for the Service Call](bilderklein/klein10_040.png)](img-f10.40.html) 

**Figure 10.40**    Basic Authorization for the Service Call

Under the Body tab, you’ll need to pass the input data in the JavaScript Object Notation (JSON) file populated with some test data, as shown in [Figure 10.41](#10_003.html#f10.41). In our case, we’re passing the value for each column in our test dataset except the Outcome column, which is for the output.

```
{
    "Pregnancies":  6,
    "Glucose":  148,
    "BloodPressure":72,
    "SkinThickness":    35,
    "Insulin":  0,
    "BMI":  33.6,
    "DiabetesPedigreeFunction": 0.627,
    "Age":  50     
}
```

[![Request Body Configuration](bilderklein/klein10_041.png)](img-f10.41.html) 

**Figure 10.41**    Request Body Configuration

Once set, click the Send button, and wait for a message indicating whether the patient is diabetic or not based on the training of our scenario.

As shown in [Figure 10.42](#10_003.html#f10.42), the class prediction outcome is non-diabetic (“class\_prediction”:\[0\]). We recommend you try out few more test scenarios and check that you’re getting the expected results. This demonstration hopefully has shown you what you can achieve through AutoML, and we hope you’ve gotten a glimpse of future possibilities.

[![Service Call Response](bilderklein/klein10_042.png)](img-f10.42.html) 

**Figure 10.42**    Service Call Response

Finally, after following a long list of steps with patience, we hope you feel joy when you see your program up and running. When you see the correct output from your first run of the AutoML functionality on SAP Data Intelligence, you should celebrate your victory!

## 10.4    Summary

As we close this chapter, let’s quickly summarize a few points before moving on to the next topic. AutoML automates the full development lifecycle for enterprise-level AI and machine learning applications. Data scientists and other users can automate the optimization and selection of machine learning models. In addition, SAP Data Intelligence can serve as a data science platform and thus offers various AutoML capabilities to accomplish feature engineering with ease. Machine learning experiments don’t have to be built manually from scratch. Using the machine learning scenario manager in SAP Data Intelligence, you can apply the AutoML feature to generate machine learning pipelines automatically. All you need to do is create training and test sets of your business data and specify the target outcome and budget of time for training and testing the model. With these options specified, AutoML can automatically perform the necessary preprocessing steps based on input data, including feature selection, feature engineering, and normalization and iteratively can train a variety of machine learning models whiles optimizing their hyperparameters.

# 11    Conversational Artificial Intelligence

This chapter provides an in-depth look at SAP’s latest conversational artificial intelligence (AI) platform along with its various components, features, and services. You’ll learn how to take advantage of the platform to build intelligent, enterprise-level bots that can deal with “the new normal” and meet still unknown challenges across industries.

In today’s world, conversational AI is all about different uses for messaging apps, speech-assisted applications, and chatbots to mechanize communications between humans and machines, or even communications between machines, and to create personalized customer experiences at scale. Not only are people taking advantage of social communication platforms, but at the same time, people are experimenting with voice-based assistants in every place including in homes, at the office, in the car, in toys for kids, and many other places where interactive conversations can ease life. Instead of traditional web-based applications or mobile apps, conversational AI-based digital platforms are rapidly emerging as an effective communication channel due to the maturation of AI and related technologies and an increased focus on offering more delightful customer experiences.

In this chapter, you’ll learn how to set up your own chatbot. We’ll start with a quick introduction to SAP Conversational Artificial Intelligence (SAP Conversational AI) in [Section 11.1](#11_001.html#h11.1), before moving on to some key concepts in [Section 11.2](#11_002.html#h11.2) and techniques in [Section 1.3](#01_003.html#h1.3) that you’ll need to understand to build your own chatbots. Finally, in [Section 11.4](#11_004.html#h11.4). you’ll build your own chatbot, ready for action on the shop floor.

## 11.1    Introduction to SAP Conversational Artificial Intelligence

Unlike social media, conversational interactions can engage audiences in two-way interactions driven by the exchange of words or sentences. When you apply the power of AI along with automation, you can even connect a human, perhaps a customer, to converse with a computer in his or her native language via a computer interface, which has really become a popular request for a variety of scenarios, especially customer service across various industries. The ongoing chatbot trend is primarily driven by the tremendous growth in the app ecosystem powered by artificial intelligence (AI) along with cognitive technologies, user-friendly conversational interfaces, and the wider reach of automation. As shown in [Figure 11.1](#11_001.html#f11.1), with conversational AI, machines can carry out multiple conversations simultaneously, having personalized interactions with a large number of customers at the same time, thus facilitating stronger and more powerful engagement, which is often not feasible for human to carry out, especially with multiple customers at the same time.

[![SAP Conversational AI](bilderklein/klein11_001.png)](img-f11.1.html) 

**Figure 11.1**    SAP Conversational AI

Conversational AI-driven chatbots will usher in the next industrial revolution. Therefore, we’ll explore some of the specialized chatbots that have emerged to address specific business needs, often providing seamless and synchronous conversations with multiple end users across multiple channels 24/7. Some categories of chatbots or voice-based assistants currently in use include the following:

*   Customer service  
    This category of chatbots are certainly the most popular ones and are on call at almost all major shopping brands. Powered by conversational AI, these kinds of chatbots can provide out of the box assistance, product recommendations, personalized styling to customers during shopping, or can even address any kind of complaints or concerns related to products. For example, Japan Airlines’ Makana-chan chat dialog interface, powered by IBM Watson Assistant and IBM Watson Natural Language Classifier services, can understand and respond appropriately to freeform questions from customers.
    
*   Scheduling  
    This kind of chatbot or virtual assistant often also enhances customer service, for instance, for booking plane tickets or movie tickets and setting up reminders or meetings. AI-driven bots can even offer the best price for a plane ticket by comparing prices from multiple sites or can suggest a movie to watch based on user preferences or even moods.
    
*   Status check  
    These bots are designed to check weather reports, nearby events, and news and covers almost anything you might ask from the Internet. When powered by AI, this kind of bot can plan your day based on weather predictions and can also suggest nearby events based on user interest, which might be determined from a user’s Tweets or Facebook posts.
    
*   Home automation  
    These home automation bots listen for commands and control smart home products installed throughout the home. Residents can listen to music, create to-do lists, shop, and more. Two popular home automation bots in this space are Amazon’s Alexa and Google Home.
    

Technology giants like Amazon, Google, IBM, and Microsoft have refocused their investments in conversational AI to the user experience domain since the technology and consumer apps, gadgets, and devices, as well as enterprise solutions, are now easily accessible to enterprises as well as independent developers. As a pioneer, SAP has offered an enterprise-level AI solution since acquiring the French startup Recast.AI, which focuses on conversational user experience technology. Recast.AI, now officially known as SAP Conversational AI, provides optimal performance and offers services that you can use to build voice- or text-based chat interfaces. SAP Conversational AI currently operates in more than 20 languages. By acquiring Recast.AI, not only has SAP step into the domain of voice-enabled computing but can harness the power of conversational interactions across its enterprise solution offerings, thus making it possible for enterprise users to talk to SAP applications in natural languages. SAP Conversational AI is the ultimate end-to-end enterprise chatbot platform for training, building, connecting, and monitoring chatbots to automate the employee experience. SAP Conversational AI includes comprehensive end-to-end features to create chatbots that can process natural language conversations and includes dialog management features including the ability to easily connect bots to almost all popular messaging channels.

In the next section, we’ll dive more deeply into several key concepts behind the SAP Conversational AI platform, and also later, we’ll develop an end-to-end enterprise chatbot to gain some hands-on experience with the platform.

## 11.2    SAP Conversational AI

The SAP Conversational AI platform, formerly known as Recast.AI, encompasses a wide spectrum of underlying core concepts and services that you’ll need to understand to build a conversational chatbot. SAP Conversational AI platform supports two key elements: skills, which represent conversation blocks, and training datasets, which are collections of sentences to understand what the user is saying and accordingly direct the flow of the conversation.

SAP Conversational AI platform uses WordNet (a lexical database for English) and the Lesk algorithm for natural language processing. The solution analyzes text inputs from users and identifies intents and entities out of conversations, which you’ll learn about in detail in [Section 11.2.2](#11_002.html#h11.2.2) and [Section 11.2.3](#11_002.html#h11.2.3). During a conversation, for every user request, the underlying natural language processing capability tries to determine whether any text matches an intent, including the general meaning of a sentence. To determine intent, the bot must understand what the user is talking about by analyzing the meanings of each word in the context of every other word in the sentence.

###### Note

WordNet is a large lexical database of English. Nouns, verbs, adjectives, and adverbs are grouped into sets of cognitive synonyms (synsets), each expressing a distinct concept.

The Lesk algorithm is a classical algorithm for word sense disambiguation introduced by Michael E. Lesk in 1986.

Let’s look at an example to work out the complexities of natural language processing to more fully understand how the Lesk algorithm works.

The Lesk algorithm basically disambiguates words in short phrases based on dictionary definitions of words. Briefly, the definitions of each word’s (usually multiple) senses are compared against each other, and the senses that share the most words in common is assigned to the word. For each word, the algorithm never utilizes senses assigned in the previous processing step and begins anew each time.

To demonstrate this algorithm let’s consider the word “pine cone” from a phrase “Pine cones hanging in a tree.” According to the Oxford Advanced Learner’s Dictionary, the word “pine” has two defined senses:

*   Sense 1: a kind of evergreen tree with needle-shaped leaves
    
*   Sense 2: to waste away through sorrow or illness
    

Similarly, the word “cone” has three defined senses:

*   Sense 1: a solid body that narrows to a point
    
*   Sense 2: something of this shape whether solid or hollow
    
*   Sense 3: a fruit of certain evergreen trees
    

Based on dictionary definition, each of the two senses for the word “pine” can be compared against each of the three senses for the word “cone.” What is found is that the phrase “evergreen tree” occurs in one sense each of the two words. These two senses are then declared as the most appropriate senses for the individual words “pine” and “cone” when they come together in a single phrase. Pretty interesting stuff, right? Now, with these concepts in mind, let’s dive more deeply into the core concepts of natural language processing.

### 11.2.1    Natural Language Processing Engine

The natural language processing (NLP) engine is the core component that interprets what users say at any given time and converts that language into structured inputs that the system can process. Since the chatbot is domain specific, it must support many features. NLP engines contain advanced machine learning algorithms to identify the user’s intent and further matches the intent to a list of available actions the chatbot supports. To interpret the user’s inputs, based on the business case, NLP engines use either finite state automata models or deep learning methods. In the past, chatbots relied on a rule-based framework that required specific queries to provide results, which was cumbersome and inefficient and didn’t scale well. As shown in [Figure 11.2](#11_002.html#f11.2), the NLP engine extracts and returns actionable data including recognized intents, entities, and sentiments derived from user expressions.

[![Natural Language Processing EngineNatural language processing enginearchitecture Architecture](bilderklein/klein11_002.png)](img-f11.2.html) 

**Figure 11.2**    Natural Language Processing Engine Architecture

The architecture shown in [Figure 11.2](#11_002.html#f11.2) illustrates how the underlying NLP engine works. NLP combines various components, each working purposefully to determine and then resolve the user’s intentions/problems. The primary responsibilities of the NLP engine include the following:

*   Understanding speech  
    When the user says something, the chatbot should be able to understand what is being said and what the user’s intention is. Based on this information, the chatbot should act accordingly.
    
*   Maintaining context  
    Chatbots should be intelligent enough to understand what the user context is. At times, the user may use the same words in different contexts. This component is a common requirement.
    
*   Custom question and answer system  
    Let’s say the user is asking some questions related to a dynamic knowledge bank. Where the question asked by the user requires the chatbot to search across company documents, policies, CRMs, ticketing info, and so on.
    

The primary component of the NLP engine is built on two key pillars:

*   Intent classifier  
    The intent classifier component is responsible for taking the user’s input, identifying its meaning, and relating this meaning back to one of the intents that the chatbot supports. A classifier is a way to categorize pieces of data—in this case, a sentence—into several different categories. Much like how humans classify objects into sets, such as a violin is an instrument, a shirt is a type of clothing, and happiness is an emotion, chatbots will classify each section of a sentence into broken down categories to understand the intention behind the input it has received.
    
*   Entity extractor  
    The entity extractor extracts key information from a user’s query. Specific information can be extracted, such as the following:
    
    *   Type of pizza user wants to order
        
    *   Time the order was placed
        
    *   Type of difficulties the user may be facing
        
    *   Customer’s name, phone number, address, and other details
        

### 11.2.2    Intents

Inside SAP Conversational AI, an intent represents the purposes or action expressed in the user’s input during a chat, such as answering a question, processing a bill payment, or any other action that user wants to perform. By identifying the intent expressed in a user’s chat, SAP Conversational AI determines the correct dialog flow for response. For example, the intent @greetings, shown in [Figure 11.3](#11_002.html#f11.3), enables your bot to understand when a user says, “Hello.”

[![IntentIntentdemonstration Demonstration](bilderklein/klein11_003.png)](img-f11.3.html) 

**Figure 11.3**    Intent Demonstration

Depending on the purpose of the chatbot, you’ll need to determine and define intents accordingly so that your intents represent what end users might want to do and thus what your chatbot application can handle on their behalf. Once you decide which business requests your application should address for your end users, you’ll need to accordingly design the skills and train your bot.

For example, for a chatbot to help customers purchase a product, you’ll need an intent called @buy\_product. For each intent (for example, @buy\_product), you’ll train the bot with different exemplary phrases that a user might say to express his or her intention, for example, “I want to buy a product” or “I want to order a pizza.” The best way to find these kinds of exemplary utterances is to refer to real-world examples from similar line of business (LOB) customer interactions. These interactions are captured over the phone, for instance, for a pizza shop, and with this information, you can build a machine learning model that can recognize similar types of utterances and map them to the appropriate intent. Initially, rather than starting with a large set of intents, we always recommend starting with smaller sets and testing them before gradually increasing the scope of the application. SAP Conversational AI currently supports intents in a wide variety of languages including English, German, French, Spanish, Amharic, Arabic, Azerbaijani, Russian, Bengali, Danish, Hindi, Italian, Finnish, Japanese, Korean, Norwegian, Dutch, Swedish, Portuguese, Mandarin Chinese, and many more.

### 11.2.3    Expressions

Expressions are an integral part of intent configuration and represent conversational phrases that a user might say while interacting with a bot. Expressions can help a bot understand users more accurately during conversations: The more you define expressions for intents, the better the chatbot’s responses. SAP Conversational AI automatically suggests additional expressions based on the initial expressions you set for any intent and currently supports multilingual expressions in four languages including English, German, French, and Spanish. Providing diverse expressions for each intent is key to making bot smarter because repetitive expressions will prevent the bot from understanding user requests. For example, an intent like @order\_a\_cake, as shown in [Figure 11.4](#11_002.html#f11.4), can be structured with a diverse set of expressions, including the following:

*   I want to buy a red velvet cake.
    
*   I want to place an order for some cupcakes for my party.
    
*   Do you sell multi-tier wedding cakes?
    
*   Do you have birthday cakes?
    
*   Can you deliver me a vanilla cupcake platter?
    

[![Expression](bilderklein/klein11_004.png)](img-f11.4.html) 

**Figure 11.4**    Expression

### 11.2.4    Entities

Now that you understand intents and their expression, let’s look at a third important concept for SAP Conversational AI, called the entity. In simple words, entities represent key information found in the user input (or expressions) and represents the user’s actual purpose. Whereas intents represent verbs (the action a user wants to do), entities represent nouns (the object of, or the context for, that action). For example, when the intent is to check for a flight status by passenger name, booking reference entities are required before the bot can process and provide the accurate flight status. [Figure 11.5](#11_002.html#f11.5) shows a sample entity called #CAKE, relevant in the context of building a bot for ordering cakes and during the course of conversation, the #CAKE entity is used to identify customer’s purpose of interactions like “I want to order a birthday cake” or may be “I want to order a special cake.”

SAP Conversational AI support different types entities: gold entities, custom entities, free custom entities, and restricted custom entities. Let’s begin by looking at gold entities and then the others one by one.

[![A Sample Entity](bilderklein/klein11_005.png)](img-f11.5.html) 

**Figure 11.5**    A Sample Entity

#### Gold Entities

Gold entities are common nouns used during conversations such as DateTime, Location, Distance, Money, and so on. SAP Conversational AI currently supports 28 different gold entities that are common across phrases used by end users in different contexts. Gold entities cannot be enriched further beyond what SAP has defined. During a conversation, gold entities are automatically detected. For example, when the gold entity “tomorrow” is detected in a sentence, a formatted version of datetime data is returned that you can use as a reply.

###### Gold Entities

The gold entities include:

*   Cardinal
    
*   Duration
    
*   Interval
    
*   Mass
    
*   Ordinal
    
*   Percent
    
*   Speed
    
*   Color
    
*   Email
    
*   Job
    
*   Money
    
*   Organization
    
*   Person
    
*   Temperature
    
*   Datetime
    
*   Emoji
    
*   Language
    
*   Nationality
    
*   Phone
    
*   Set
    
*   Url
    
*   Distance
    
*   Ip
    
*   Location
    
*   Number
    
*   Pronoun
    
*   Sort
    
*   Volume
    

#### Custom Entities

Beyond gold entities, you can define custom entities based on the context for your bot to detect specific keywords and extract the necessary info. [Figure 11.6](#11_002.html#f11.6) shows a few custom entities relevant in the context of production planning and execution. We’ll use these entities in our manufacturing execution bot building exercise in [Section 11.2](#11_002.html#h11.2). Custom entities are required for the following reasons:

*   To detect the possible appearance of certain keyword(s) relevant to your bot and to ask for further info.
    
*   Since entities and intents are well connected, the occurrence of a certain entity may help in the detection of the relevant intent.
    
*   Custom entities can be either free or restricted in nature.
    

[![Custom Entities](bilderklein/klein11_006.png)](img-f11.6.html) 

**Figure 11.6**    Custom Entities

#### Free Custom Entities

Free custom entities are more appropriate when you don’t want to restrict your custom entity to a limited set of values and instead want the machine learning model to identify all possible values when engaged in the conversation, such as recommending movies to watch. To the train the model, you must provide a wide range of examples of the characteristics.

#### Restricted Custom Entities

Restricted entities help you define a strict list of words for your custom entity. The entity will only be detected when certain words in the defined list of synonyms are found. For example, if you need your chatbot to allow customers to order pasta, you’ll want to look for possible pasta flavors that customers might mention when conversing with bot, for instance, “Alfredo” or “lasagna.” In this case, the flavor name cannot be detected unless it has been included in the restricted list of synonyms.

So, let’s quickly recap what we’ve learned so far about intents, expressions, and entities:

*   Intent  
    An intent is all about user’s intention and is treated as a verb and a noun. For example, if a user writes “show me yesterday’s sport’s headlines” in a news chatbot, it may trigger an intent called “showHeadlines,” and the intention captured here is to retrieve all key sports headlines from yesterday.
    
*   Expression  
    An expression is all that user says. For example, if a user types “show me yesterday’s sport’s headlines,” the entire sentence is the expression.
    
*   Entity   
    An entity is about key information extracted from user’s conversational phrases and connects to intents. For example, if a user types “show me yesterday’s sport’s headlines,” the entities are “yesterday,” “sports,” and “headlines.” Entities have different types including gold, custom, free custom, and restricted custom.
    

In natural language processing (NLP), an expression is examined, and intents and entities are extracted from it. Let’s now focus back on some other key concepts with SAP Conversational AI like language, sentiment analysis, channels, the conversational user interface (UI), and the Bot Builder.

### 11.2.5    Languages

Chatbots are becoming the most popular way to serve customers across the globe and thus must support multiple languages and be able to detect the customer’s preferred language. SAP Conversational AI currently supports multiple languages at different levels (advanced, standard, and basic). Not all functionalities are supported for all languages. [Figure 11.7](#11_002.html#f11.7) shows the language matrix currently supported by SAP Conversational AI.

[![Supported Languages](bilderklein/klein11_007.png)](img-f11.7.html) 

**Figure 11.7**    Supported Languages

#### Sentiment Analysis

A key goal of conversational chatbots is to create conversational experiences or provide customer service while ultimately not sounding or behaving like a robot. To seem as human-like as possible, chatbots must understand the user’s tone in addition to understanding the intents and entities from the expression. Sentiment analysis is an automated process that programmatically extracts topics from texts as well as the user’s feelings, even subtle nuances like sarcasm. By understanding the context and the sentiment of the customer right from the beginning, a chatbot can select the best course of action and can apply quite different patterns, even if the underlying problem is the same. As shown in [Table 11.1](#11_002.html#t11.1), SAP Conversational AI currently supports several categories of sentiments.

 
| Polarity || Examples |
| --- | --- |
| vpositive || That was awesome to see that man eat a peach. |
| --- | --- |
| positive || The man ate a peach. |
| neutral || Peach. |
| negative || Sadly, the man did not eat a peach. |
| vnegative || That was awful to see this man ate a peach. |

**Table 11.1**    Conversational Sentiments

#### Speech Acts/Sentences

Speech acts represent words that are voiced not only to describe states of affairs, but also to perform actions that are executed to have some effects on the hearer. For example, the phrase “I would like the mashed potatoes, could you please pass them to me?” is considered a speech act. This speech act expresses the speaker’s desire to acquire the mashed potatoes and presents a request to someone asking for the potatoes to be passed to them. Beyond understanding the content of the natural language utterance, the chatbot interface should understand human speech acts/utterances by observing the direct or indirect intention of the user to provide helpful assistance. Examples of core speech acts include: INFORM; ACCEPT; REQUEST; YN-QUESTION (closed yes/no questions); WH-QUESTION (open what, why, who, when, where, etc. questions); SUGGEST; EVAL; REQUEST-PERMISSION; OFFER; and PROMISE. Out of this list, SAP Conversational AI currently detects four kinds of speech act: ASSET, COMMAND, WH-QUESTION, and YN-QUESTION. [Figure 11.8](#11_002.html#f11.8) shows the WH-QUESTION and YN-QUESTION categories. The speech act categories can be seen in [Figure 11.8](#11_002.html#f11.8).

[![Speech Act Categories](bilderklein/klein11_008.png)](img-f11.8.html) 

**Figure 11.8**    Speech Act Categories

#### Sentence Types

During an interaction with a bot, identifying the type of sentence entered by the user is vitally important so that the bot’s response can be more accurate. Especially with a question/answer type of bot, detecting the type of question helps determine what the answer should be. For example, when user asks the bot, “What is the acronym for Indian Space Research Organisation?” the bot immediately must classify the sentence type as an Abbreviation or ABB. This classification ultimately helps the bot trigger the right channel to get the answer. Currently, SAP Conversational AI supports various sentence type classifications including ABB, DESC, ENTY, HUM, and LOC. For more details, refer to [https://cai.tools.sap/docs/concepts/sentence-types](https://cai.tools.sap/docs/concepts/sentence-types).

### 11.2.6    Channels

Channels are the medium of chatbot conversations. Examples of channels include Facebook Messenger, Amazon Alexa, SAP CoPilot, SAP Jam Collaboration, Telegram, Skype, Microsoft Teams, Slack, Twitter, and many more. Here are the third-party channels currently supported by SAP Conversational AI:

*   Amazon Alexa
    
*   Line
    
*   Messenger
    
*   Skype
    
*   Microsoft Teams
    
*   Cortana
    
*   Slack
    
*   SAP CoPilot
    
*   SAP Jam Collaboration
    
*   Telegram
    
*   Twilio
    

TwitterIn this section, we’ll discuss the different tools and methods offered by the SAP Conversational AI bot tools suite, which includes bot understanding, the natural language processing tool, the Bot Builder, and the Bot Connector.

## 11.3    Bot Building Techniques

Before we get into bot building techniques in detail, you’ll need to understand what a bot actually is. According to SAP’s definition, a bot is a program that automates a task. Users interact with the bot through different messaging channels. Bots can understand conversational phases written by or spoken by end users and, based on the request, perform the necessary actions. SAP Conversational AI bot tools suite comes with a built-in visual flow management user interface called the Bot Builder where you can define entities, intents, and expressions and construct bots to process conversational phrases and interact with users through dialog. As shown in [Figure 11.9](#11_003.html#f11.9), the Bot Builder uses the powerful logic of skills to process user expressions and knows when to request more information and when to leverage data already detected. The rapid visual prototyping feature facilitates the development of conversation logic by defining required steps and establishing the user flow with the bot.

[![Bot Builder Architecture](bilderklein/klein11_009.png)](img-f11.9.html) 

**Figure 11.9**    Bot Builder Architecture

The prototyping and the flow mapping can be customized to create optimal user interactions with your bots. These customizations simplify connections to external integrations and allow users to adapt the bot’s behavior based on their preferences.

### 11.3.1    Bot Building Process

As shown in [Figure 11.10](#11_003.html#f11.10), SAP’s defined bot building process is pretty simple and segregated into the following three activities:

*   Reading user expressions   
    Expressions arrive as inputs during interactions with end users through a particular messaging channel, and the Bot Connector submits the message to the Bot Builder for further processing. SAP Conversational AI even includes application programming interfaces (APIs) for directly posting messages to the Bot Builder for processing instead of the Bot Connector.
    
*   Applying natural language processing (NLP) and processing user expressions  
    In this process, the message received from Bot Builder is processed further using NLP APIs and relevant content is extracted in structured format.
    
*   Managing the conversation by triggering correct dialog flow  
    These activities are based on the results of the natural language processing. The right context is maintained based on the skills and conditions defined.
    
*   Answering user expressions  
    The goal is to deliver the most relevant response to the end user by analyzing the user’s expression through natural language processing and most importantly by maintaining the right context.
    

[![Bot Building ProcessBot buildingprocess](bilderklein/klein11_010.png)](img-f11.10.html) 

**Figure 11.10**    Bot Building Process

Beyond the bot building process, you’ll also need to understand some programming concepts so you can use the graphical flow building components, which are very much required to program a real bot! Let’s look at the relevant programming concepts next.

#### Skills

According to SAP’s definition, a skill represents an individual conversational building block or a combination of conversational building blocks with a clear purpose. These blocks are executed to achieve a goal. Whether a simple greeting or welcome message at the beginning of the conversation, or a product suggestion based on preferences mentioned by the user during the conversation, a skill runs through conversation building block(s) and delivers the purpose. [Figure 11.11](#11_003.html#f11.11) shows a representation of an e-commerce-oriented skill. Three different types of skills include Business, Floating, or Fallback.

[![Skill](bilderklein/klein11_011.png)](img-f11.11.html) 

**Figure 11.11**    Skill

#### Conditions

A condition represents a test that can be evaluated to either true or false. Typically, a condition occurs in different sections of a skill, for instance, in the following places:

*   In triggers
    
*   In requirements
    
*   In each group of actions
    

#### Triggers

A trigger represents a condition that decides for the bot whether to execute the current skill(s) or not. If trigger conditions match with the specification inside the skill, the bot will execute the triggered skill over other skills. When a particular skill lacks a trigger, that skill will never be triggered until specifically redirected from some other skill.

#### Requirements

As the name implies, a requirement represents pieces of information that a skill must retrieve before executing any actions during a conversation. This piece of information can come from an external API call, for example, to retrieve the user’s name or location. Once a requirement is completed, the associated value is stored in the bot’s memory for the entire conversation and can later be referred to from some other skill through a reference to a memory object, discussed in more detail later in this section.

#### Actions

An action represents what your bot executes at a specific point when executing a [skill](http://skill). To add actions to a skill, open the skill under the Build tab and then open the Actions subtab. Click ADD NEW MESSAGE GROUP.

#### Messages

To make chatbot-based conversations more interactive and pleasant, SAP Conversational AI currently supports an interesting set of messaging formats including the following:

*   Text  
    Regular text format with a limit of 640 characters, useful for showing informative messages to users. According SAP’s recommendations, during the conversation, bot response messages should be short for better and quicker reading. Long messages may cause users to lose the interest.
    
*   Card  
    A cool feature is to show an image along with some text. For example, you could display information about a food item (e.g., title, subtitle) next to an image of the dish, and more.
    
*   Buttons  
    Buttons are especially useful when a bot needs to confirm a user’s decision before proceeding further or perhaps to restrict users to limited choices, for example, confirm buying a product or booking a plane ticket.
    
*   Quick replies  
    Same purpose as buttons but disappear once clicked. Great so that users don’t have to scroll up the conversation and click on a button again.
    
*   Carousel  
    A series of cards that a user can scroll from right to left. This format is more useful when you want to show a range of individual information like different products or food varieties that the user can scroll through.
    
*   List  
    The list messaging format is similar to a carousel, but in terms of display, the list appears vertically and a bit smaller than a carousel. Although the images appear smaller, the user see everything at once without scrolling.
    
*   Image  
    A cool format to use, you can also show animations to users during conversation like entertaining GIFs or emoticons.
    

#### Memory Management

During a conversation with a user, a lot of key information will be exchanged, including key values and entities to be detected. These values must be persisted to a memory object. An empty memory object (which can also include prepopulated keys) is allocated to each user at the start of a conversation and remains until the end of the conversation. The memory object can be updated or cleared as needed and remains stored in the conversation state.

#### Conversation States

With the initiation of any new conversation, at first, the bot will be initiated with its own internal objects to capture state-related information during the course of the bot’s conversation with the user. State-related information includes the following objects:

*   id  
    The Bot Connector assigns an ID at when a conversation is initiated with a user, and this ID is unique for every user. Internally, this unique ID helps to distinguish conversations from each other.
    
*   language  
    SAP Conversational AI automatically identifies the language being used by the user during the course of a conversation and saves this value in the language state object.
    
*   memory  
    During the course of conversation, a user will provide key information according to the context, and the memory state object is used to store this key data collected from the user.
    
*   participant data  
    This state object captures the user’s information from the channel with which the chatbot is actually connected, for example, Facebook Messenger, Slack, Skype, etc.
    
*   skill  
    Captures the currently active skill derived from the tenor of the entire conversation.
    
*   skill\_occurences  
    Basically a count of the number of messages being handled by the currently active skill consecutively. The counter is reset to 0 when the actions related to the skill are complete.
    
*   skill\_stack  
    The keeper of all skills used during the entire course of the conversation. The final skill in the skill\_stack is always prioritized for execution and later is deactivated after its actions have been executed.
    

#### User Authentication

The user authentication mechanism is relevant when you’re directly using the Bot Builder API to build your chatbot instead of using the Bot Connector. For example, provisioning web-based chat on a website will mean that your chat interface is integrated with the Bot Builder through APIs. Thus, to establish authentic webhook-based calls from the webchat interface to SAP Conversational AI, the authentication mechanism uses token, cookie session, or user ID methods especially when the user is already authenticated (already logged on to the website). Unique user identifiers (an authentication token or user ID) can also be persisted into a memory object right from the initiation of the conversation or after the first request made to the /dialog endpoint.

#### Custom Code

When building a bot, you may need to integrate custom services to retrieve business information or integrate an external system to perform certain actions. This integration can be achieved through webhooks via simple HTTP calls. To configure webhooks, you’ll simply make an HTTP call to your backend. The HTTP method also supports GET, POST, PUT, and PATCH requests in webhook calls.

### 11.3.2    Bot Connector

A good bot must connect to multiple channels including Facebook Messenger, Twitter, Slack, Twitch, Telegram, Skype, SMS, emails, and more, but this diversity comes with the challenge of writing multiple versions of code that can take full advantage of each channel and also manage the integration to each channel separately. Moreover, if the API of any channel changes, you’ll need modify your code. Challenging? Yes, but the Bot Connector included in the SAP Conversational AI platform can rescue you by letting you use a single API to easily connect to all possible channels. As shown in [Figure 11.12](#11_003.html#f11.12), the Bot Connector also supports a unified messaging structure capable of exchanging messages, including cards, text, and images and includes other messaging features for the various channels, taking advantage of the features of each. Basically, this API sends and receives messages from every channel without the need to constantly switch between APIs or to reply on extension documentation.

The Bot Connector, a fully open source project, includes innovative provisioning so that you can even develop custom channel connections to connect to your desired communication channel and include it in a given platform API.

[![Bot Connector Architecture](bilderklein/klein11_012.png)](img-f11.12.html) 

**Figure 11.12**    Bot Connector Architecture

### 11.3.3    Bot Monitoring and Analytics

So far, you’ve learned the basic concepts behind natural language processing and the process behind the building chatbots, including the tools to use, but we still need to address monitoring. When you’re building an enterprise chatbot solution, monitoring your chatbots’ activities, usage, most mentioned topics, and other insights are vital to identifying areas for improvement and providing the best experiences to your users and customers. Bot analytics is a powerful module in the SAP Conversational AI bot tools suite, which enables you to continuously monitor log feeds, usage metrics, training analytics, conversation logs, and other metrics. As shown in [Figure 11.13](#11_003.html#f11.13), bot analytics can help you with the following tasks:

*   Managing conversation logs either using the application backend or an SAP provided analytics interface.
    
*   Instantly analyzing the performance of a bot based on its log feeds, including classifying entities and intents. For consistency, the bot can be trained with the necessary intents, and required entities can be tagged directly using the log feed.
    
*   Analyzing learning curves, preventing learning incidents, and tracking a bot’s evolution over time.
    
*   Applying smart filters while capturing analytics, which gives you the flexibility to categorize data based on language, channel, date, and many other categories.
    
*   Monitoring the usage metrics of different skills, intents, or entities based on conversations users have had with your bot through the Bot Builder in the backend. Different metrics include conversations; users; messages received; average message by conversation; and most used skills, intents, and entities.
    
*   Accessing all analytical metrics and logs, which can be downloaded at any time so you can refer to them offline as needed.
    
*   Running dataset benchmarking processes to assess the performance of a bot by analyzing the underlying dataset. Insights on how to improve a bot’s intent classification and custom entity detection are provided.
    
*   Improving intent classification and analytics while also providing live tips and step-by-step suggestions to improve the dataset and increase accuracy.
    

[![Bot AnalyticsBot analytics](bilderklein/klein11_013.png)](img-f11.13.html) 

**Figure 11.13**    Bot Analytics

### 11.3.4    SAP Conversational AI APIs

The SAP Conversational AI bot tools suite comes with a wide spectrum of APIs in different languages including Python, Node.js, Ruby, PHP, Android, and Swift covering almost all aspects of bot building and management. Let’s cover a few significant APIs.

#### Runtime API

The key purpose of the Runtime API is to retrieve all the necessary metadata, intents, and replies for a given sentence. Endpoints for this API include the following:

*   Analyze endpoints service   
    This service is useful for retrieving intents, entities, sentiment, and metadata from a given text. The following is a sample reference URL: URL\_PREFIX/train/v2/request.
    
*   Dialog endpoints service   
    Similar to the analyze endpoints service, this service retrieves intents, entities, sentiment, and metadata but additionally the reply message for a given text. The following is a sample reference URL: URL\_PREFIX/build/v1/dialog.
    

#### BOT API

This endpoint includes services to show or update bots and as a response returns the BOT model. The BOT model includes the BOT id, name, slug, private\_data indication, bot children\_count, developer\_token, etc. The following is a sample reference URL: URL\_PREFIX/core/v1/users/${USER\_SLUG}/bots/${BOT\_SLUG}.

#### NLP API

The biggest collection, NLP APIs are dedicated for managing datasets, training, bulk creation, intents, expressions, logs, and custom keys. The comprehensive list includes:

*   Datasets  
    The Datasets NLP APIs are for managing datasets, including showing, updating, and indexing and returns the Dataset model in response, which includes the id, slug, strictness, intents\_count, manual\_training, etc. The following is a sample reference URL: URL\_PREFIX/train/v2/users/$USER\_SLUG/bots/$BOT\_SLUG/versions/$VERSION\_SLUG/dataset.
    
*   Trainings  
    The trainings endpoint is for managing model trainings including indexing. The service returns a training model as a response.
    
*   Bulk creation  
    This endpoint is for bulk creation of expressions, which is an important aspect of model training because a wide range of expressions can make chatbots respond better. The following is a sample reference URL: URL\_PREFIX/train/v2/users/$USER\_SLUG/bots/$BOT\_SLUG/versions/$VERSION\_SLUG/dataset/bulk\_creations.
    
*   Intents  
    The intents endpoint include services for managing intents including creating, updating, showing, deleting, and indexing intents and entities. To create an intent, refer to the following sample reference URL: /users/$USER\_SLUG/bots/$BOT\_SLUG/versions/$VERSION\_SLUG/dataset/intents.
    
*   Expressions  
    Similar to the intents endpoint, the expression endpoint include services for managing expression including create, update, show, delete, indexing, and bulk creation. To create an expression, refer to the following sample reference URL: URL\_PREFIX/train/v2/users/$USER\_SLUG/bots/$BOT\_SLUG/versions/$VERSION\_SLUG/dataset/intents/$INTENT\_SLUG/expressions.
    
*   Logs  
    All about managing bot logs including indexing, showing, deleting, and bulk deleting. To show a log, refer to the following sample reference URL: URL\_PREFIX/train/v2/users/$USER\_SLUG/bots/$BOT\_SLUG/logs/$LOG\_ID.
    
*   Keys  
    The keys endpoint includes provisions to manage custom keys for an entity and includes services to create, update, delete, and show custom keys for a given entity.
    

#### Bot Builder API

These conversation\_state endpoints enable you to show, update, and delete conversations including updating the language or memory of the Bot Builder conversation at runtime through the API as well as through webhooks. To access the conversation\_state endpoint, refer to the following sample reference URL: URL\_PREFIX/build/v1/users/$USER\_SLUG/bots/$BOT\_SLUG/versions/$VERSION\_SLUG/builder/conversation\_states/$CONVERSATION\_ID. For more details on these APIs, refer to [https://reverseproxy.cai.tools.sap/docs/api-reference/#bot-builder-api](https://reverseproxy.cai.tools.sap/docs/api-reference/#bot-builder-api).

#### Bot Connector API

Bot Connector APIs are focused towards managing connectors, channels, conversations, participants, and messages. The list of endpoints includes the following:

*   Connectors  
    This endpoint covers list of service to show, update, and delete connectors. To show connectors, refer to the following sample reference URL: URL\_PREFIX/connect/v1/connectors/${BOT\_ID}.
    
*   Channels    
    A complete list of services to manage channels including indexing, creating, updating, deleting, and showing channels. To showing channels, refer to the following sample reference URL: URL\_PREFIX/connect/v1/channels/$CHANNEL\_SLUG.
    
*   Conversations    
    Covers a basic set of services to manage conversations including indexing, deleting, and showing conversations. To show conversations, refer to the following sample reference URL: URL\_PREFIX/connect/v1/conversations/${CONVERSATION\_ID}.
    
*   Participants    
    A list of services to manage channel participants including indexing and showing participants. To show participants, refer to the following sample reference URL: URL\_PREFIX/connect/v1/participants/${PARTICIPANT\_ID}.
    
*   Messages    
    The messages endpoint provides the necessary APIs to send and broadcast messages. To broadcast a message, refer to the following sample reference URL: URL\_PREFIX/connect/v1/messages.
    

Overall, the list of available APIs is quite comprehensive and includes endpoints for the Bot Builder and Bot Connector. For more in-depth details about these APIs, refer to the documentation for SAP Conversational AI APIs available at [https://cai.tools.sap/docs/api-reference/#bot-model](https://cai.tools.sap/docs/api-reference/#bot-model).

So far, you’ve become familiar with the different concepts, tools, and APIs offered by the SAP Conversational AI bot tools suite. Now, let’s implement these concepts by developing an SAP Conversational AI bot.

## 11.4    Building a Chatbot Using SAP Conversational AI

By now, you should have a pretty good understanding about different components of the SAP Conversational AI bot tools suite. Finally, we’ll see some of these components in action as we walk you through a step-to-step guide on bot application development using the Bot Builder. Using the Bot Builder, you can design complex flows quickly and easily. But before describe the steps for building bots, we need to explore the use case we’ll work with. Initially, when we started brainstorming a use case for this chapter, we were only looking for an easy way to demonstrate SAP Conversational AI features, but the current global pandemic has really pushed us to think outside the box and realign ourselves with the “new normal.” One definite aspect of the “new normal” is how we approach high-touch areas in the workplace. Many workplaces are now considering how they can reduce the number of touch points and have already started looking at different technologies that does not require physical touch. Today, many enterprise solutions that have been put in place have relied on touch technology, such as touchscreens to check in to a flight or to perform a record data on the shop floor. Considering the nature of the pandemic, contamination can easily happen from surfaces shared across many users. One possible solution to deal with this pandemic-related challenge is to introduce AI-driven, voice-enabled enterprise solutions that can act on the context of the user interaction. SAP Conversational AI will play a critical role in building this kind of solution.

For our use case, we decided to look to the manufacturing industry, where a huge number of employees work on the shop floor, sharing common workstations and gadgets during a shift. Considering the nature of the pandemic, contamination can easily occur from the surfaces workers interact with. Therefore, to make the shop floor safer and smarter, we’ll build an SAP Conversational AI-based, voice-enabled solution that will allow end users to interact with and perform manufacturing execution operations, like starting/completing operations, data recording, and viewing key performance indicators (KPIs) in the system without the need to touch a workstation.

While building this bot, we’ll primarily demonstrate the following activities step by step:

*   Learn   
    Making the bot learn all the necessary information required to interpret and understand relevant inputs.
    
*   Connect on-premise   
    Connecting our on-premise SAP Manufacturing Execution (SAP ME) system to fetch the relevant shop floor operation data and call transactions based on user inputs through the chatbot.
    
*   Establish conversation flow  
    Building the conversational flow using the Bot Builder.
    
*   Voice enablement  
    At the time of this writing, SAP Conversational AI doesn’t support speech-based input/output features. Thus, in this space, you can leverage any open source speech-to-text/text-to-speech conversion APIs, or you can take advantage of several proven and specialized cognitive services offered by IBM Watson, Microsoft, or Google. For our proof of concept (POC), we’ll use a simple JavaScript-based function to achieve the voice input/output capability.
    
*   Connect channel  
    Connecting the bot to a channel.
    
*   Continue training  
    To ensure accurate and improved interpretation, your bots must be updated on a regular basis.
    

###### Note

SAP Manufacturing Execution (SAP ME) is a powerful, enterprise-level, scalable manufacturing business solution that enables global manufacturers to manage and control manufacturing and shop floor operations.

For more details, refer to the following URL:

[https://www.sap.com/india/products/execution-mes.html](https://www.sap.com/india/products/execution-mes.html)

### 11.4.1    Let’s Build a Bot!

Let’s start building our bot. [Figure 11.14](#11_004.html#f11.14) shows exactly what we’re trying to build in this section.

[![SAP ME System Interactions through Our Bot](bilderklein/klein11_014.png)](img-f11.14.html) 

**Figure 11.14**    SAP ME System Interactions through Our Bot

As shown in [Figure 11.15](#11_004.html#f11.15), notice that, after the greeting, the bot informs the operator about the number of batches of work the operator needs to deliver in the current shift. A shop floor control number (SFC) represents a quantity of product instances, depending on the lot size of its material. The bot also asks the operator to confirm that the highest priority SFC should be started. Upon receiving confirmation (“Yes”), the bot starts the SFC in the SAP ME system and sends an acknowledgment once the SFC has successfully started.

[![Bot Displaying Machine Checklist](bilderklein/klein11_015.png)](img-f11.15.html) 

**Figure 11.15**    Bot Displaying Machine Checklist

The next action the bot performs is asking the user to confirm for viewing the machine parameters, and based on the acknowledgement, the bot fetches the machine parameter list. From this general presentation so far, we hope that you now have a pretty good idea of what kind of manufacturing execution system interaction bot we’re trying to build. We want to be able to perform manufacturing execution operations seamlessly, and at every step, we want the bot to guide the end user by suggesting specific actions.

### 11.4.2    Setting Up the Bot Project

Let’s now focus on building our bot for manufacturing execution. For our first step, we must create a bot by logging on to the SAP Conversational AI cockpit hosted at [https://cai.tools.sap/](https://cai.tools.sap/). As shown in [Figure 11.16](#11_004.html#f11.16), click the \+ New Bot button in the top-right corner of the screen.

[![Create Bot](bilderklein/klein11_016.png)](img-f11.16.html) 

**Figure 11.16**    Create Bot

Depending on the purpose of your bot, you can choose one of the predefined types, which in our case is the Perform Actions type. Make sure you also select some of the predefined skills available like Greetings and Small Talk. Give your bot a proper name and click Create a Bot.

### 11.4.3    Creating Intents

Once the project setup is complete, you can start defining the intents essential for our bot, as shown in [Figure 11.17](#11_004.html#f11.17). Since we’re building a bot for manufacturing operation execution, we must train the bot with typical terms and intents found in shop floor processes as well as contextually connected to the actual business process, so that the bot can interpret the real intention of the user.

Some typical intents in this context include @show-oee, @report-yield, @report-scrap, @report-nc, @show-sfc-list, @start-sfc, @complete-sfc, and various others, as shown in [Figure 11.18](#11_004.html#f11.18) and [Figure 11.19](#11_004.html#f11.19).

[![Custom IntentsIntentcustom](bilderklein/klein11_017.png)](img-f11.17.html) 

**Figure 11.17**    Custom Intents

[![Custom Intents, Continued](bilderklein/klein11_018.png)](img-f11.18.html) 

**Figure 11.18**    Custom Intents, Continued

Let’s now look at the typical expressions for training our bot. Remember, in this case, we really need to think like a typical shop floor user and brainstorm all the possible expressions we can. [Figure 11.19](#11_004.html#f11.19) shows a list of expressions for the @show-oee intent.

[![@show-oeeIntent@show-oee Intent Expressions](bilderklein/klein11_019.png)](img-f11.19.html) 

**Figure 11.19**    @show-oee Intent Expressions

For a deeper understanding, [Figure 11.20](#11_004.html#f11.20) shows the expressions for the @start-sfc intent.

[![@start-sfcIntent@start-sfc Intent Expressions](bilderklein/klein11_020.png)](img-f11.20.html) 

**Figure 11.20**    @start-sfc Intent Expressions

### 11.4.4    Setting Up Entities

Once your intents are ready, let’s now start working on the entities. In our use case, the scenario also demands custom entities, as shown in [Figure 11.21](#11_004.html#f11.21) and [Figure 11.22](#11_004.html#f11.22). Some relevant entities in this case include #BOM, #CAPACITY, #COMPONENT, #CONSUMPTION, #SFC, #MATERIAL, #SCRAP, #SITE, #RESOURCE, etc. These entities will be heavily used as part of the bot’s conversational abilities.

[![Custom EntitiesEntitycustom](bilderklein/klein11_021.png)](img-f11.21.html) 

**Figure 11.21**    Custom Entities

[![Custom Entities, Continued](bilderklein/klein11_022.png)](img-f11.22.html) 

**Figure 11.22**    Custom Entities, Continued

After creating all necessary entities and intents, we’re ready to design the necessary skills (or conversational flows). In our case, we’ll you show you the end-to-end design for one intent.

### 11.4.5    Setting Up Skills

To set up skills, navigate to the Build tab and start designing. The overall skill running behind the manufacturing bot looks something like the screen shown in [Figure 11.23](#11_004.html#f11.23). For now, we’ll focus on only one flow.

[![Overall SkillsSkilloverall](bilderklein/klein11_023.png)](img-f11.23.html) 

**Figure 11.23**    Overall Skills

Let’s focus on the @greetings intent, shown in [Figure 11.24](#11_004.html#f11.24), which not only welcomes the user but offers to start SFCs by fetching relevant information from the manufacturing execution system.

As shown in [Figure 11.25](#11_004.html#f11.25), the greetings skill is triggered when the bot detects a welcoming expression like “Hi” or “Hello” or something similar. The greetings skill is automatically added if you chose it when first creating the bot project. In our use case, the greetings skill not only greets the user but also invokes a custom Representational State Transfer (REST)-based API to display additional information about the assigned work from the manufacturing execution system. Inside the API Service Configuration section, we configured a service URL to fetch production data from an SAP ME system. The service basically returns a list of SFCs assigned to the work center to which the operator is assigned.

[![The @greetings Intent](bilderklein/klein11_024.png)](img-f11.24.html) 

**Figure 11.24**    The @greetings Intent

[![Connect External Service](bilderklein/klein11_025.png)](img-f11.25.html) 

**Figure 11.25**    Connect External Service

To call any external service, you can configure the call under the Actions tab by clicking the Connect External Service button and selecting one of the options shown in [Figure 11.26](#11_004.html#f11.26). Once you successfully set up your service call, you’ll need to identify the memory fields that you want to populate through the service call.

Inside the Set memory field section, you’ll configure the relevant memory fields like SITE, RESOURCE, User\_ID, USER\_INTENT, WORKCENTER, etc. to acquire the necessary values for these fields from the service response and then to assign these values to the designated memory fields shown in [Figure 11.27](#11_004.html#f11.27). The values set in memory fields remain valid throughout, and can be accessed at any time during, the conversation.

[![Values from Service Response Stored into Memory](bilderklein/klein11_026.png)](img-f11.26.html) 

**Figure 11.26**    Values from Service Response Stored into Memory

[![Greeting Skill Final Response](bilderklein/klein11_027.png)](img-f11.27.html) 

**Figure 11.27**    Greeting Skill Final Response

After inserting essential operational values into the memory fields like SITE, RESOURCE, WORKCENTER, NO\_OF\_SFC, etc., let’s now build the response by using values stored in these memory fields, which can be easily accessed through simple syntax like {{memory.User\_ID}} , {{memory.RESOURCE}}, as shown in [Figure 11.28](#11_004.html#f11.28). Finally, we’ll set up a redirect link from the greeting skill to the startsfc skill to continue the flow. This redirect link is essential for connecting the current skill to any subsequent skill you want to trigger next.

[![Requirements Configuration for the startsfc Skill](bilderklein/klein11_028.png)](img-f11.28.html) 

**Figure 11.28**    Requirements Configuration for the startsfc Skill

Inside the startsfc skill, you’ll need to set up the Requirements tab, as shown in [Figure 11.29](#11_004.html#f11.29). In our use case, we want our bot to ask the user for confirmation on starting the execution of an SFC. As shown in [Figure 11.29](#11_004.html#f11.29), the bot should ask, “Do you want to start SFC {{memory.NEW\_SFC}} ?” after the initial greeting. Notice that, inside the greeting skill, we’re using a memory field for which a value has already been stored.

[![Edit Replies Configuration](bilderklein/klein11_029.png)](img-f11.29.html) 

**Figure 11.29**    Edit Replies Configuration

So, at this stage, if you want to chat with your bot, you should see a response like the response shown in [Figure 11.30](#11_004.html#f11.30).

[![Testing the Bot](bilderklein/klein11_030.png)](img-f11.30.html) 

**Figure 11.30**    Testing the Bot

In response to the suggestive action, when the user responds either “Yes” or “No,” you’ll need to define the next actions accordingly under the Actions tab, as shown in [Figure 11.31](#11_004.html#f11.31).

[![Actions Configuration](bilderklein/klein11_031.png)](img-f11.31.html) 

**Figure 11.31**    Actions Configuration

In case of an affirmative response to the action suggested by the bot, another service call from the SAP ME system will be made to start the priority SFC proposed by the bot and to fetch the service response, as shown in [Figure 11.32](#11_004.html#f11.32). to display the service response to the user. If the user replies in the negative, the response shown in [Figure 11.32](#11_004.html#f11.32) is displayed.

[![Negative Response](bilderklein/klein11_032.png)](img-f11.32.html) 

**Figure 11.32**    Negative Response

So, at this point, you’ve successfully built two different skills, and [Figure 11.33](#11_004.html#f11.33) shows the testing result based on the two skills.

This use case should give you a good idea of how SAP Conversational AI can help you build an interactive bot for shop floor management and to control manufacturing execution through simple conversations instead of interacting with a traditional system through numerous buttons and navigation paths. This kind of touchless execution for operations will be crucial across various industries in order to stay safe in the “new normal.” By establishing a safe and intelligent workplace, we can reduce the fear of contamination in the shared workplace.

[![Bot Test Run](bilderklein/klein11_033.png)](img-f11.33.html) 

**Figure 11.33**    Bot Test Run

### 11.4.6    Enabling Voice

In this context, voice enablement for our bot will also be important from a touchless execution point-of-view. To enable the voice-based inputs, you can easily leverage any speech-to-text or text-to-speech APIs provided by pioneers like IBM Watson, the Google Cloud speech API, or the Microsoft Speech Bing API since SAP Conversational AI doesn’t support voice control as a native feature. To leverage these APIs, you must build a custom user interface for your bot on SAP Cloud Platform and use REST-based dialog endpoints service provided by SAP Conversational AI to retrieve all the necessary metadata, intents, and replies from a sentence, as shown in [Figure 11.34](#11_004.html#f11.34).

In this process, you’ll need to take voice inputs from end users through a custom bot interface and convert this audio into text by applying a speech-to-text conversion APIs and then pass the expression to the bot for processing by using the /dialog (text) API endpoint, as shown in [Figure 11.34](#11_004.html#f11.34). To get the response and deliver it to the user, you’ll apply a text-to-speech conversion API on the outcome of service call.

For more details on this API, refer to the following link:

[https://reverseproxy.cai.tools.sap/docs/api-reference/#dialog-endpoints](https://reverseproxy.cai.tools.sap/docs/api-reference/#dialog-endpoints)

To invoke these endpoints successfully, you must obtain a token available in the bot’s settings, as shown in [Figure 11.35](#11_004.html#f11.35).

[![Dialog EndpointsDialog endpoints](bilderklein/klein11_034.png)](img-f11.34.html) 

**Figure 11.34**    Dialog Endpoints

[![Obtain a Token](bilderklein/klein11_035.png)](img-f11.35.html) 

**Figure 11.35**    Obtain a Token

## 11.5    Summary

After going through numerous concepts in SAP Conversational AI and building a full-scale enterprise use case, we’ve finally reached the end of the chapter and it’s time for a quick recap of what we’ve learned up to this point. So far, you’ve seen how the SAP Conversational AI platform includes a wide spectrum of features covering every aspect of constructing intelligent bots for enterprise operations. The special use case we built together in this chapter hopefully gave you a fair understanding of how SAP Conversational AI can bring about a revolution in touchless interfaces so we can all conduct business safely in the “new normal.”

# Part III

Use Cases and Roadmaps

# 12    Integrating Machine Learning with the Internet of Things

 and BlockchainIn this chapter, our focus will be on the integration between SAP’s intelligent enterprise portfolio and three amazing technologies—machine learning, the Internet of Things (IoT), and blockchain—to see how you can combine machine learning with IoT and blockchain. We’ll also examine two unique use cases and the scope that comes with leveraging this intelligent technology trio to build smart enterprise solutions for the post-COVID world.

Blockchain is a trending technology that has the potential to reshape industries. When we look at these technologies, which are now coming into their own—IoT, blockchain, and machine learning—we know we’re living and working in a time of exciting opportunities to integrate legacy systems with emerging technologies.

The global digital economy continues to expand and change at relentless pace. Organizations must match this pace to keep their businesses afloat. Today’s enterprises need agility, scale, and the ability to innovate using all the available strategies to integrate machine learning with IoT and blockchain to improve business processes, drive business results, and propel digital transformation. [Figure 12.1](#12_001.html#f12.1) shows how the digital transformation revolution has impacted across industries around the globe.

Over the past decade, as cloud computing and big data have become ever more universal, with all latest technologies and software, along with all sorts of cloud applications, industries have begun their own digital transformation journeys. Technologies like artificial intelligence (AI), machine learning, IoT, and blockchain can help your organization build an intelligent enterprise, with new capabilities for enabling trust, providing transparency, and enabling value exchange across different business ecosystems, potentially lowering costs, reducing transaction settlement times, improving cash flow, and enabling workforces to focus on higher-value outcomes.

Blockchain is not only a technology: Something more than the Internet, it’s a movement to redefine the world of business relationships through trust, transparency, and newfound collaboration. In the current situation, organizations are coming together to transform the way their industries work with the help of blockchain. For instance, the food supply is becoming safer, smarter, and more profitable by freeing the food industry from legacy processes and paperwork and stepping into a new business world of collaboration and innovation.

[![Digital Transformation Imprint](bilderklein/klein12_001.png)](img-f12.1.html) 

**Figure 12.1**    Digital Transformation Imprint

Blockchain is designed to store absolute digital pieces of information as time-stamped series of data in a distributed database that is shared across a network of computers. Getting traditional collaborators and long-time competitors to agree on the bold steps needed for blockchain transformation isn’t easy. Technical innovators are turning to blockchain platforms to perform the following activities:

*   Managing all network components in a single place, no matter where the component is deployed and what type of computing environment is in place
    
*   Maintaining complete control of identities, ledgers, and smart contracts, which are described in [Section 12.2](#12_002.html#h12.2)
    
*   Deploying blockchain components like peers, ordering services, and certificate authorities (CAs)
    
*   Easily connecting a single peer to multiple industry networks
    
*   Linking nodes running in any environment (e.g., on-premise, public cloud, hybrid cloud)
    

Note, however, that storing this time-series data lacks a defined process to verify whether the information is correct.

Now, let’s look at a simple scenario—the aviation baggage handling process—where blockchain, IoT, and machine learning can be integrated to make a secured and transparent solution for aviation industry.

With heavy passenger traffic and growing numbers of inbound and outbound flights, airport authorities have focused on automating the baggage handling processes to increase efficiency and keep pace with their operations. Airports have adopted innovative business models for cargo and baggage tracking, passenger identification, and smart contract applications to lower operational costs and generate new revenue streams. By leveraging blockchain, IoT, and machine learning, airports can enhance their efficiency specifically in the area of baggage handling and passenger handling.

Blockchain enables the aviation industry to share a decentralized digital ledger to store all baggage-related flight data of all airlines simultaneously and securely. This technology also facilitates smoother and more efficient operations that can ultimately lead to cost savings for all involved partners, including the airport, baggage handlers, and the airlines. Using various technologies and different networks can improve the passenger experience, increase transparency and traceability in operations, and reduce maintenance cost and transactional complexities. Consider an integrated solution using blockchain to manage all the electronic baggage tag (EBT) information, received from IoT devices or smart labels with radio frequency identification (RFID) technologies, along with image recognition using machine learning, to manage all the baggage-related information in a secure manner with lots of transparency about the real status of all baggage available to all the relevant partners.

As the usage of machine learning expands, integration with complementary technologies like machine learning and IoT will unlock even higher value.

## 12.1    Technology-Driven Transformation

While adopting the latest technologies, any industry needs to redesign their business processes, and the impact of these changes for most industries is truly transformational. The list of impacts and challenges changes at a pace never that experienced before, and ambiguities are now exposed more than ever before. Unlike any incident in our lifetimes, the global pandemic has underlined the interconnectedness of our world and also exposed the troubling fact that sometimes when we need rapid, coordinated action and collaboration using immense amounts of critical information, we continue to be trapped in data silos and legacy processes.

To keep up with the pace of transformation and this new set of business challenges across the industry, demand has spiked for a trusted platform to perform the following activities:

*   Automate outdated ways of working
    
*   Rapidly gather all the required datasets
    
*   Derive actionable insights from the data to navigate through crisis and prepare strategies for the long recovery ahead in a changed world
    

Blockchain is a trusted platform, and various blockchain-based solution have been integrated with IoT and machine learning to help us confront today’s most frightening challenges. Despite its benefits, the world has not yet achieved mass blockchain adoption. Some hurdle for organizations include not only the costs of implementing a blockchain system and its difficulty in integrating with preexisting systems but also a lack of knowledge about blockchain. Even though some hesitance is certainly understandable, the changed situation—the “new normal”—may force industries to reconsider how they see blockchain. As all our business operations move increasingly online, being executed remotely, in the face of worldwide lockdowns, newer and revised solutions are undoubtedly needed. Perhaps, blockchain can only fill that gap and address the need. In today’s world, we’re already equipped with powerful and scalable technologies like IoT along with its robust protocols to connect smart devices and sensors to the web through a cloud-based digital identity. On the other end, blockchain-based smart contracts are ready to automate transactions and data sharing between the multiple stakeholders, perhaps involved in a product’s lifecycle. Beside addressing business process-driven challenges, seeing how blockchain is also contributing towards fighting the global pandemic has been an amazing experience. Not only the small-scale organizations or startups are using blockchain solutions to fight the virus. Giant organizations from different sectors across the globe including the World Health Organization (WHO), IBM, Oracle, and Microsoft; government agencies; and international health organizations have joined together to develop blockchain-based, open data hubs like MiPasa to quickly and precisely identify infected persons and hotspots around the world and share information securely among various participants in the network like hospitals and public health authorities for analysis. For more details on MiPasa, refer to the following link: [https://www.ibm.com/blogs/blockchain/2020/03/mipasa-project-and-ibm-blockchain-team-on-open-data-platform-to-support-covid-19-response/](https://www.ibm.com/blogs/blockchain/2020/03/mipasa-project-and-ibm-blockchain-team-on-open-data-platform-to-support-covid-19-response/).

## 12.2    Data—The Common Theme

In this section, we’re talking about data. As shown in [Figure 12.2](#12_002.html#f12.2), statistics demonstrate that big data is being generated in every minute on the Internet somewhere in the world.

By the time this book is on the market, what we consider “big data” won’t be “big” anymore. Data continues to grow every second, and to cope and maintain pace with the changing situation, most industries are trying to execute their businesses and run jobs virtually by producing much more data every minute. With such massive volumes of data, AI can play a crucial role in successfully analyzing all this data and deriving valuable insights and never-before-seen analyses out of the data. As a branch of AI, machine learning refers to an automated process in which machines are used to categorize meaningful and potential patterns in data, perhaps generated from smart sensors or IoT devices.

[![Generation of Big Data on the Internet Every Minute](bilderklein/klein12_002.png)](img-f12.2.html) 

**Figure 12.2**    Generation of Big Data on the Internet Every Minute

For example, let’s say a beverage company needs to source roasted coffee beans from which the company brews coffee. For this company to determine the right coffee recipe and make great coffee every single time, the key data points are the coffee temperature, the quantity of water, and the current condition of the coffee brewing equipment. Using data from sensors on the equipment, you can avoid breakdowns and instead proactively maintain the equipment. Furthermore, based on the usage data collecting from the coffee brewing machine, along other data points like customer preferences and selling frequency, machine learning can help you gain insights about the quality of the final brewed coffee product. With the tremendous growth of fully industrialized computing hardware and network technologies, the integration of IoT, machine learning, and blockchain implementations of this kind of smart enterprise scenario—both small scale and large scale—are possible across the consumer packaged goods industry.

Around the globe, where most IoT devices are connected to each other via public networks, blockchain plays a crucial role in strengthening data security and privacy by using linear and permanent indexed records that can be created easily. Today’s IoT systems are designed so that its data will be transmitted from physical devices to the cloud using signatures or encrypted certificates from the data sender. The sender will have a unique key pair, and output is received back to the IoT device in the same way, thus ensuring authentication and the integrity of transmitted data. Thus, all data transactions between IoT devices and the cloud-based system are logged into the distributed ledger that can be traced back securely. By using this huge set of IoT data, machine learning and AI can be used to build better models by taking advantage of the decentralized nature of blockchains. Blockchain offers a secure way to exchange goods, services, and data among all participants that exist globally in the network. [Figure 12.3](#12_002.html#f12.3) shows a simple data flow diagram reflecting the possible exchange of data between a blockchain platform and various other sources including IoT devices, networks, and others.

[![Data Flow Diagram: BlockchainBlockchaindata flow and Sources of Data](bilderklein/klein12_003.png)](img-f12.3.html) 

**Figure 12.3**    Data Flow Diagram: Blockchain and Sources of Data

Let’s return to our coffee brewing example to understand the core concepts of blockchain and learn how smart contracts carry information that can automatically execute business logic. In this context, you must understand that a smart contract is a computer protocol that contains all the business rules for determining how a business deal should be executed.

Now, let’s see what kind of information a smart contract typically carries with respect to our coffee brewing use case. In this case, the brewer uses a smart contract to buy coffee beans by putting all the required information (e.g., coffee bean type, form, quality, and quantity) based on the data collected from the coffee brewing machine to determine the coffee bean preferred most by customers. For example, to set up the terms of the smart contract, the quality of beans can be of type (Arabica), form (roasted), quality (gourmet), and quantity (40 units). Once this smart contract is submitted in its registered blockchain network, and the blockchain logic tries to match the requirements with a farmer who previously provided similar kinds of coffee beans. Interesting, right?

We hope our discussion so far has given you a fair idea of how the joint forces of machine learning, IoT, and blockchain can bring about immense change to enterprise digital transformation. Now, let’s dive deeply into some specific use cases from a variety of industries. Considering the “new normal” and the challenges we’re facing in the world, we decided to include a use case to meet the need of the moment.

## 12.3    Use Cases

In our new reality, existing business challenges, in every industry, are tougher than ever before as both small and large enterprises cannot escape the devastating impact of the pandemic. Every moment, an enterprise is being battered like a tiny tree in the middle of the storm. Before it’s too late, every enterprise must start thinking about and adopting solutions integrating IoT, machine learning, AI, and blockchain to enhance IT resiliency, with a distinct focus on business continuity, and at the same time must ensure data protection, minimize disruption, and keep the cost of the business operations under control.

With our use cases from supply chain management and the healthcare industry, we’ll primarily focus on how to leverage blockchain along with IoT and machine learning to meet enterprise challenges. We’ll address various pain points like supply chain disconnect and ensuring food quality in our first case and managing social gatherings, clinical trials, drug and disease control information in our second case. Let’s start our discussion with the supply chain industry.

### 12.3.1    Supply Chain

Due to the ongoing outbreak, tremendous pressure already exists on the global economy, specifically trade systems, highlighting the urgent need for global cooperation to maintain and reinforce the flexibility of international supply chains. This flexibility in supply chains depends on trust, transparency, and integrity, which can be improved through the accountable deployment of blockchain technologies that offer a “shared truth.” Let’s focus back to our original use case.

At the beginning of this year, 2020, no one could have imagined the unexpected trouble caused by pandemic, which has revealed a general lack of connectivity and data exchange built into our global supply chains. Unlike outbreaks of E. Coli, COVID-19 has not been linked with any food-borne vector of contamination. Despite the lack of evidence that food can host or transmit the virus, seafood has been blamed for transmitting the virus. The lack of confidence in the seafood industry focused on the missing links and uncertainties inside the supply chain. In this situation, blockchain can save the seafood supply chain industry by playing a key role in reducing uncertainties in the supply chain while making operations easier and safer. Blockchain solutions integrated with IoT and machine learning could work together to re-establish trust in supply chain industry by informing retail customers about the source of the food they’re consuming.

To understand these concepts better, let’s use an example from the seafood industry to look at this industry’s typical challenges and how blockchain can address them. [Figure 12.4](#12_003.html#f12.4) shows how missing links in the seafood industry supply chain can result in concern from end users at various stages of supply chain regarding the quality of the product.

[![Seafood Industry Challenges](bilderklein/klein12_004.png)](img-f12.4.html) 

**Figure 12.4**    Seafood Industry Challenges

As shown in [Figure 12.4](#12_003.html#f12.4), some typical needs that the seafood industry requires include the following:

*   Real-time connectivity for monitoring each step in the supply chain
    
*   Assurance about the source and quality of the food
    
*   Trust between the consumers and suppliers
    
*   Less information and documentation about the food presented to consumers
    

In combination with IoT and machine learning, blockchain can ensure that every item in the supply chain can be traced back to its source. Let’s address these points one by one.

#### Real-Time Connectivity

Whether managing a cold chain to transport seafood or monitoring a fish production plant, by using several industrialized IoT sensors, blockchain enables data capture. All network participants can monitor any action executed in the network. Blockchain enables the tracking of products from the raw materials stage (in this case, the hatchery) until the delivery of the final product to the end client. Each participant in the supply chain can share detailed information about their actions back to the network. Critical pieces of information like water pH levels, temperatures, the food being fed to the fish, growth rates, and finally timestamps capturing the moment the fish is caught can be easily collected by installing various sensors and devices across the fish farm. Once the fish is caught by a fisherman, the butchery process is started. Quality is assured by the lab, which will check different quality parameters like weights, sizes, and medical conditions. Also, cold chain management during the transportation of the food from the storage area to the retail store is critical for maintaining the quality of the food. Data like temperatures, humidity, locations, times, and energy consumption can be monitored during the transportation process using smart IoT sensors and advanced networked devices. [Figure 12.5](#12_003.html#f12.5) shows the integration architecture between IoT, blockchain, and various data sources at every stage of processing the fish.

[![Blockchain and IoT integration](bilderklein/klein12_005.png)](img-f12.5.html) 

**Figure 12.5**    Blockchain and IoT integration

Now that you understand that how the real-time integration of blockchain and IoT can help you to collate critical pieces of information and share this information across the various participants in a trusted blockchain network to introduce transparency, let’s now shift our focus towards quality control using AI.

#### Quality Control

The quality of the food that is being served on the dining table is really important. If we talk about any outbreak of disease, the entire food industry is affected until the source of the contamination is identified. Especially due to a lack of transparency and the inability to quickly trace a product’s source, all participants in a network may need to incur losses including the costs associated with product recalls or the complete shutdown of the supply chain due to lack of trust and uncertainty.

So, to ensure the quality of the seafood, it’s crucial to collect quality-related data at each level of process and share this information with all the blockchain network stakeholders. In this context, data can originate from various places like IoT sensors placed inside a fishing vessel at sea to check the water and the food composition being fed to the fish. Also, while checking water quality, the monitoring of a few physical parameters, like temperature, dissolved oxygen, electroconductivity, pH, and chemical levels, is highly recommended to learn about the fish’s health conditions. So, now that we have a huge volume of data from various IoT sensors and devices used by the farmer, the distributor, and the retailer, machine learning can be applied to this data to retrieve valuable insights for each of participants in the network, including consumers.

Machine learning has huge potential to detect the patterns and anomalies in the data that IoT sensors generate. Supervised machine learning starts with a conventional set of data and a fixed understanding of how that data is categorized. Supervised learning is used to find patterns in the data that can be used to gain insights about the process. For example, you can build a machine learning application using visual recognition that differentiates among millions of units of seafood, based on various parameters and composition data. The following describes a typical quality control process for our use case:

*   Imaging  
    Each seafood item passes through a small chamber that take a 360-degree, high-resolution picture.
    
*   Scanning  
    Pictures are then scanned to identify spots and shape abnormalities.
    
*   Grading  
    Based on the scanning result, a quality grade is assigned to the lobster.
    
*   Packaging  
    Based on the grade, the lobster is routed to a specific conveyor belt to complete packaging.
    

[Figure 12.6](#12_003.html#f12.6) shows the process of distinguishing between good and bad lobsters using automated machine learning techniques.

[![Machine Learning in Action to Identify Good/Bad Lobsters](bilderklein/klein12_006.png)](img-f12.6.html) 

**Figure 12.6**    Machine Learning in Action to Identify Good/Bad Lobsters

#### Trust between Consumers and Suppliers

Sustainability and trust go hand in hand for any organization. Every consumer expects better services and products from its retailer, but one unspoken expectation is that the product or the food they are buying is safe. The blockchain-, IoT-, and AI-driven solutions that we’ve discussed so far have provided transparency into the supply chain and enable access to crucial data points including product packaging date, the temperatures at which a food item was shipped until its arrival to the grocery shelf, and finally information about the product’s shelf life.

A study conducted by a tech giants in partnership with a North American retailer suggests that, before leveraging the power of blockchain, IoT, and machine learning, tracking a case of lobsters to its original fish farm using conventional methods required about a week of effort. The process of tracking required so much time because records were kept either on paper or in parts in different systems that didn’t speak to each other. Adopting a blockchain-, IoT-, and machine learning-driven solution can help the various stakeholders involved in the network to trace the origin of a case of lobsters much more quickly, converting the “days” into “seconds.” Now, tracing a case of lobsters to its source, and accessing details about each step in the supply chain, requires only about 3 seconds.

#### Required Documents about Products

Although all the required information regarding the origin and the quality of a food item is available in its documentation, but you need an application that can easily connects the dots and reduce the time and effort required to provide the desired transparency and traceability.

To optimize manufacturing processes, increase quality, and strengthen a customer’s connection to the product, documentation about a food item is very much needed. The physical flow of documents for a food item through couriers and local deliveries, especially across international borders, can require hundreds of hours to get the necessary clearances and stamps ready for shipping.

As shown in [Figure 12.7](#12_003.html#f12.7), using a blockchain-driven solution, at the end of the supply chain, retail customers can easily scan a QR code on a product to get all the information regarding its proof of quality and its source, the processes it went through, and even suggested recipes for using the specific purchased food item.

[![QR Code-Based Food Quality Tracking](bilderklein/klein12_007.png)](img-f12.7.html) 

**Figure 12.7**    QR Code-Based Food Quality Tracking

Finally, to complete the food product lifecycle, using a consumer app, retail customers can provide real-time feedback to manufacturers, ultimately enabling lobster suppliers to tweak their production methods to improve the quality of the seafood.

### 12.3.2    Healthcare

Up to this point, we’ve discussed traceability in the context of a supply chain to trace the source of a product using the power of blockchain, IoT, and machine learning. Now, let’s see how the healthcare industry is utilizing this technology trio to gain similar benefits.

Studying a traditional healthcare use case may sound like we’re trying to force-feed blockchain into a healthcare context. But the reality is that the global pandemic is pushing us towards a new era of collaborative ecosystems where government agencies work with the private sector and local markets to get a real understanding of business requirements and then fulfill these needs with the help of innovative solutions built on blockchain, IoT, and machine learning.

As we move towards a safe and cautious reopening of the world, a new passport called a “health passport” could be required to enter this post-pandemic world with increased safety and confidence. Many new challenges now exist for the healthcare industry, such as the following:

*   Tracking a huge population of infectious patients to identify contamination
    
*   Producing high volumes of critical personal protective equipment (PPE), drugs, and other medical supplies
    
*   Immediate access to millions of data points about the microbe so that better diagnostics, vaccines, and targeted therapeutics can be developed
    

Now, let’s look at how the latest technologies can help us brainstorm and build survival strategies and sustainable solutions based on the gathered information, existing resources, and knowledge.

#### Tracking Populations to Identify Contamination

To combat COVID-19, the first vital need is the need to identify infected people and stop the spread of the disease. To identify, assess, and manage the numbers of people who have recently been exposed to a positive COVID-19 patient, the World Health Organization (WHO) defined a mechanism called digital contact tracing. This mechanism is a more effective, efficient, and secure way of finding exposed contacts rather than interviewing lots of people in the traditional method of contact tracing. Based on this concept, several countries have developed different mobile apps for digital contract tracing.

Because the human memory is fallible and because sensitive work and personal data are being handled, a digital contact tracer uses a few features, like symptom self-report functions, to send automated SMS alerts to known contacts. This kind of digital contact tracing app, running on a smartphone, generally uses GPS, telecommunication towers, Wi-Fi access points, and Bluetooth beacons to find the places where an infected person has traveled. Using GPS locations through the phone, one person can easily fetch his or her own travel history from the automatic log of times and places and compare this information with anonymized logs to determine if the user has encountered a positive case. Also, a Bluetooth beacon or a Bluetooth low energy capability on mobile devices are other options being adopted by different tech giants. With this latest kind of framework, every mobile device can send and receive a beacon or RSSi feed to another device. Based on this data feed, public health organizations can easily identify other phones that have come into contact with an infected person’s phone and accordingly send alert notifications for home isolation for a calculated length of time and distance without disclosing any user’s locations or personal details. [Figure 12.8](#12_003.html#f12.8) shows the concepts that we’ve discussed so far.

[![Mass Tracking-Driven Intelligence](bilderklein/klein12_008.png)](img-f12.8.html) 

**Figure 12.8**    Mass Tracking-Driven Intelligence

Based on this data feed, blockchain, IoT, and AI can be combined to help medical facilities identify contaminated areas and further track the spread of the virus in the following ways:

*   Using this kind of tracking data, government authorities can easily categorize different contamination zones based on the severity of infection and update real-time statistics.
    
*   The purpose of tracking this kind of mobile sensor data from different sources also makes a rich source of information for planned analysis and forecasting about peaks of outbreaks in different locations or countries.
    
*   Such alerts will assist government authorities and healthcare providers making strategic, life-saving decisions to allocate medical staff and necessary equipment well in advance.
    

Worldwide, medical facilities have a critical need—access to an immutable, trustworthy set of medical data that can be accessed quickly, electronically, and internationally so that locations are identified and real-time monitoring of the situation is possible. Any incorrect information during this pandemic could be extremely dangerous. Blockchain-based solutions can be leveraged for controlling the spread of the virus and circulating quality medical advice throughout society.

#### Producing Personal Protective Equipment

A major issue in the preparedness of world health systems to respond to this outbreak is the production of critical personal protective equipment (PPE) and other medical supplies. Due to this pandemic, large spikes in market demand have created shortages of the critical medical supplies needed to treat COVID-19.

Before getting into the solutions for this challenge, let’s briefly review the reasons for these shortages:

*   Neither hospitals nor any public health agencies were ready for this pandemic. In the United States, for example, 3 billion N95 masks are required, but only 12 million were in the stockpile.
    
*   During this crisis, as millions of masks were transported across state lines or across international borders, sometimes, buyers were forced to enter into advanced fee arrangements and business email compromise (BEC) schemes. Buyers were left with no options for choosing among sellers or for assuring product quality.
    
*   Due to high demand, the price of the PPE is exceedingly higher than usual, so the people with the most money had access to them.
    
*   Another limitation is payment terms. Minimum order quantities, specified by the supplier, made it impossible for smaller organizations to order the quantities they needed. For instance, a small organization might need 1,000 masks, but the supplier’s minimum quantity for shipment might be 100,000.
    

According to sources, from May 15th to the time of this writing, 770,416 units of PPE have been delivered to protect 104,484 healthcare and frontline workers.

To achieve the delivery of vast volumes of PPE, many industries have changed their businesses entirely. For instance, car manufacturers are making ventilators and face shields, while clothing manufacturers are producing gloves, masks, and isolation gowns. Both the car manufacturer and the clothing designer are thus new to the PPE industry, and these non-traditional suppliers need to connect to hospitals to determine product requirements. Now, to perform matchmaking between the new supplier and the hospital with trust and transparency, a blockchain-based solution is the most efficient and fastest strategy.

Let’s consider a scenario where a government hospital requires a large volume of PPE for its medical staff. The hospital is continuously trying to connect to a medical supplier to replenish the inventory of PPE.

A blockchain-based solution can help non-traditional medical suppliers connect to the healthcare community and learn about demands in real time. As part of a trusted blockchain-driven ecosystem, government agencies and healthcare organizations can accept new, non-traditional suppliers who have pivoted their production to address the shortage of PPE and supplies with traceability, transparency, interoperability, and most importantly with ease. After receiving an order, once the supplier finishes the production of the required PPE, a real-time alert can be generated from the production line using IoT. This notification can be sent immediately to the already registered blockchain network to inform the owner about the completion and shipment of the order. To manage all this information, a mobile app can be really handy; just like any other e-commerce app, this app can track the availability of each type of PPE with all specifications, prices, and statuses visible to the healthcare provider. Based on the hospital’s needs, the procurement team can request the product, and once the product purchase request is made, other members in the network can monitor and track the product’s status in nearly real time.

Also, the data generated from the network might include various demands placed by different network participants, like hospitals and medical agencies. This data can be further leveraged for AI-driven demand forecasting and prediction and accordingly drive production by different suppliers and manufacturers. [Figure 12.9](#12_003.html#f12.9) shows the whole picture and a possible architecture supporting this concept.

[![PPE Supply and Demand Network](bilderklein/klein12_009.png)](img-f12.9.html) 

**Figure 12.9**    PPE Supply and Demand Network

In this way, with the help of blockchain and IoT data, providers can learn about a supplier, including the supplier’s certifications, the product’s authenticity and quality control data, and when the product will be delivered.

#### Access to Viral Information for Better Diagnostics, Drugs, and Vaccines

SARS-CoV-2, the virus that causes COVID-19, has created an unprecedented global challenge. As we do our part by practicing social distancing and other new norms, healthcare workers and first responders are leading in the front line.

On the other hand, the healthcare and life sciences industry have been doing its best since day one of the pandemic, by analyzing the microbe, discovering drugs, producing drugs for testing phases, and getting ready for mass production. In normal circumstances, a minimum of 2 to 5 years is required to develop a vaccine, but in the era of AI and machine learning, rapid vaccine development technologies are enabling much faster result. Vaccines can be ready in a 12- to 18-month timeframe!

Considering different aspects of biology—molecular biology, cellular biology, biochemistry, ecology, and evolutionary biology—the data analysis of a microbe is a complex activity, since many dissimilar data sources exist. These datasets include rich details about genotypes, phenotypes, and genetic structures. Analyzing microbial data from multiple data sources requires high-dimensional pattern recognition and prediction capabilities. For example, the SARS-CoV-2 virus has the following biological makeup:

*   265,520 genomes
    
*   72,160,121 genes
    
*   55,616,382 proteins
    
*   244,699,956 domains
    

So, data gathering/generation, cleansing, and processing are crucial activities for this kind of study and require a lot of time and effort. In this scenario, AI and machine learning can revolutionize the analysis and study of the data, including predicting potential outcomes and accelerating vaccine development. Other potential benefits in the context of medical science include the following:

*   Optimized manufacturing   
    Machine learning can spot patterns in large volumes of data and can be used to optimize manufacturing processes, for instance, using the data produced during drug research and production. Ultimately, optimized manufacturing can reduce the time and costs required for a procedure or can improve the reproducibility of a manufacturing process.
    
*   Pattern selection in data  
    Machine learning can detect patterns from vast amounts of data to clarify complex biological systems and predict success in compound activities and interactions in the early stages of drug development.
    
*   Personalized medicine  
    Supervised learning could use patient data to more effectively predict the expected responses to a treatment selected from the set of potential diagnoses. Machine learning can also estimate a patient’s risk based on the similarity of symptoms and genetic information.
    
*   Behavioral modification for the “new normal”  
    According to the guidelines published by WHO, we must follow the “new normal” in this post-COVID world. In this context, machine learning and AI can be leveraged to enforce norms. For example, using image recognition on data gathered from various biosensors and devices, different health measurement and management solutions can be built to monitor an individual’s health. Other activities can also be monitored, like “hand-to-mouth” gestures, to help people better understand the importance of keeping their hands clean and make life-affirming changes to prevent the spread of serious respiratory illnesses.
    

## 12.4    Summary

Finally, we’ve concluded our chapter, and at this moment, you should have a fair idea of the applicability of blockchain and how it can solve various enterprise challenges in the post-COVID world. This chapter showed you how the power of blockchain can be combined with IoT, machine learning, and AI to address these challenges with ease, through two use cases involving two different industries: the seafood industry and the healthcare industry.

# 13    Industry Use Cases for Machine Learning Applications

This chapter further dives into industry-specific use cases to show you how SAP’s intelligent enterprise-oriented offerings can be leveraged to solve real industry challenges. You’ll learn about possible architectures, methodologies, and services required to build solutions to address each use case.

We’re almost at end of our book and about to wrap up our long journey by quickly navigating through the last couple of chapters. We’ll start this chapter by examining how machine learning has been adopted across different industries in [Section 13.1](#13_001.html#h13.1), before briefly describing the machine learning ecosystem in [Section 13.2](#13_002.html#h13.2). Then, we’ll focus on our main task in this important chapter—discussing real-world industry use cases and showing you how to apply your learning so far to resolve real challenges in [Section 13.3](#13_003.html#h13.3). Our primary target will be industries where the return on investment (ROI) for machine learning technologies can be high, and we’ll apply SAP’s intelligent enterprise conversion technologies and solutions to transform end-to-end business processes radically. At the same time, we’ll improve production efficiency, product quality, and worker safety and generate more, happier customers.

## 13.1    Acceptance of Machine Learning across Different Industries

Machine learning algorithms are not new and have been around for quite for a long time. However, recent developments have enhanced the ability to apply complex mathematical calculations to enterprise data again and again in the fastest way possible. Industries producing and working with big data have already started recognizing the value of adopting machine learning technologies, which enhances competitive advantage. Over the years, statistics have clearly shown that artificial intelligence (AI) and machine learning can both have profound impacts on business and are rapidly becoming critical for a business’s distinctiveness and endurance in the market. Undiscovered patterns and insights produced by machine learning technologies from the enormous amount of enterprise data can now be used to solve highly complex, data-rich problems that outsmart human intervention. On the journey to becoming an intelligent enterprise, real-time analytics are really critical to any business operation, including the processing of both current and historical data to prescribe the right action to respond to events.

[Figure 13.1](#13_001.html#f13.1) shows how machine learning has been adopted across industries. Enormous amounts of semi-structured data are generated by today’s enterprises every day through countless devices and sensors. This valuable information can ultimately be used to develop models to compare patterns of performance and detect anomalies.

For example, a regression algorithm, which predicts output values based on input data fed into the system, can build a training model based on the features found in the data to predict values for new data. This model can then be used as the foundation for a more complex model that can predict when a machine might fail. Several classification algorithms can be used to build the patterns associated with machine failures.

[![Adoption of Machine Learning across Industries](bilderklein/klein13_001.png)](img-f13.1.html) 

**Figure 13.1**    Adoption of Machine Learning across Industries

### 13.1.1    Assessing the Impact of Machine Learning

Both the demand for and the ubiquity of machine learning have grown across the enterprise world, and existing methods are constantly being improved in terms of their ability to understand and answer real issues. As shown in [Figure 13.2](#13_001.html#f13.2), successful outcomes and predictions are now leading to widespread adoption of machine learning in several domains, such as analyzing medical imaging data, medical treatment records, social media feed, marketing data, and more. Integrating machine learning as part of enterprise software, business is now more predictable, and organizations can introduce automation to processes in ways never imagined before. Several potential benefits in mind for every enterprise assessing the potential impact of adopting machine learning include the following:

*   Accessing unseen enterprise insights and analyses  
    In the recent years, enterprise data and its sources are no longer limited to within the organization itself or another traditional system. This enormous volume of data has challenged traditional, unintelligent enterprise solutions, which require more processing time. Often, valuables insights are missed. In these respects, machine learning can help you create a competitive advantage from the vast amounts of structured/unstructured enterprise data being produced.
    
*   Upscaling enterprise application security and risk analysis  
    Enterprise security is always challenged by continued revolution in phishing techniques, malware, spam, or other cyberattacks, with new challenges every day. Most organizations spend heavily to secure their systems and landscape but often still fail. Today’s enterprises need application security software with embedded machine learning frameworks to enhance fraud detection. Advanced security techniques, like pattern recognition enabled with machine learning algorithms, are vital for identifying irregularities in transactions or for evaluating transactional data from external sources to detect fraud or other anomalies.
    
    [![Machine Learning Impact](bilderklein/klein13_002.png)](img-f13.2.html) 
    
    **Figure 13.2**    Machine Learning Impact
    
*   Helping make data-driven decisions  
    Enormous amounts of structured/unstructured data, generated from various sources, are meticulously collected but often ending up in silos without any further processing or analysis to understand key aspects or find unknown patterns. Moreover, the required data interpretation is rarely simple, going well beyond simply sorting data and applying filters. Data engineering skills may be required. By 2025, the amount of data being produced is expected to grow eightfold, and many enterprises are frantically introducing machine learning-driven decision-making either solely or impartially, based on the insights gathered from the pool of enterprise data, which can also help in areas like recruiting talent, managing customers, research and development, and spurring innovation to new heights.
    
*   Intelligent and self-sufficient applications  
    In additional satisfied customers and profitable businesses, a critical development in today’s enterprise environment is the rise of innovative human resources (HR)-oriented systems, including ways to enrich the employee experience. Managers are often now eager to take an employee’s pulse by analyzing their feedback, searches, reviews, and social media posts to find ways to enhance employee experience on a day-to-day basis. This kind of analysis adds a new dimension to strategic workforce planning, training recommendations, and compensation suggestions and can reduce employee attrition. Organizations previously skeptical of adopting new ways to manage proprietary HR data are now looking forward to machine learning-based, self-learning HR applications. With these solutions, HR can focus more on strategic planning at the organizational level and can easily analyze HR data to improving strategic planning. Self-learning applications can inform every decision.
    

Beside these expectations from machine learning, you’ll need to remember that machine learning is a powerful but intricate tool. Knowing its strengths and weaknesses in detail can actually help you achieve even higher ROI. Although machine learning, AI, data science, and deep learning are all buzzwords of the moment, these terms still represent powerful tools that can support you on your journey to becoming an intelligent enterprise. The precise conversion of business requirements into data for feeding into your machine learning models is essential for finding the root causes of events while the correct interpretation of results will help improve business and generate even more value from machine learning.

### 13.1.2    Challenges of Machine Learning Applications

Although we may believe we’ve entered a golden age of AI, in reality, leveraging machine learning to build intelligent enterprise solutions still faces some obstacles that can be addressed easily, such as the following:

*   Prolonged time to achieve expected result  
    Traditional enterprise software development is pretty straightforward: To meet your business goals, you’ll plan functionalities and choose a technology to build a solution, assuming that development will require several months before releasing a working version. Machine learning projects require more time to see results than a traditional software development project. With machine learning, you’ll need to gather and prepare data, then train the algorithm. Still, uncertainties may exist because even the best machine learning engineers don’t know how deep learning networks will behave when analyzing different sets of data. As a result, machine learning engineers and data scientists cannot guarantee that the training process of a model can be replicated.
    
*   Young technology  
    Even though machine learning sounds like a fairytale, the technology has not yet aged and has not been tested over time. The first version of Google TensorFlow was released in February 2017, IBM Watson was introduced in 2011, and many other giant tech companies are still trying out new things and investing heavily to build new platforms and offerings in this space.
    
*   Need enormous amount of data  
    To train a machine learning model, the most essential requirement is the volume of data. Large amounts of data may not seem to be a problem anymore since everyone can afford to store and process petabytes of information. Although storage has become cheaper, gathering data still requires huge amounts of time, and buying ready-to-use sets of data can be expensive. Also, you’ll need a clear picture of the problem you want to solve so you can plan your algorithms with the necessary classification, clustering, regression, and ranking functions.
    
*   Right talent   
    Finding skilled resources with the right experience is another significant challenge to the adoption of machine learning. Although many people are attracted to the machine learning industry, still only a few specialists can develop this technology. A good data scientist who understands machine learning often lacks an understanding of software engineering.
    

As with anything, machine learning comes with some hurdles and risks. Still, machine learning projects are highly rewarding and will soon reach a point where the technology is commonplace, but you’ll need to be patient, plan carefully, and respect the challenges that come with this innovative technology.

## 13.2    Machine Learning Ecosystem

Machine learning is mainly based on the computing power and various technologies for gaining meaningful insights from big data, which is collected from different devices. Machine learning can also learn from that data by using AI. Here’s what this process looks like:

*   Get data
    
*   Clean, prepare, and manipulate data
    
*   Train model
    
*   Test data
    
*   Improve
    

For specific tasks, applications running on machine learning can achieve higher-level and more complex requirements than humans. You’ll need to select the correct ecosystem to handle the big data from which the information is obtained. However, data will need to be filtered to find the right balance between good and bad data. Too much information can cause delays or may lead to incorrect responses to problems. With these issues in mind, machine learning must utilize the different techniques and algorithms to achieve the maximum benefit from the data. The machine learning ecosystem is huge and amorphous, with no well-defined boundaries, and machine learning can already be found in many facets of our hypermodern life.

The most critical task for applying machine learning starts with selecting the appropriate model that can ultimately provide the most accurate business outcomes at the very beginning. A complex issue when selecting a model is making sure that the model is not too general and will perform well in the future when new data is introduced. Choosing the best model for your data is definitely not easy; according to experts, a single predictive model in action may require two months of operations before you can be confident the model is accurate. Why is this process so difficult and time consuming? As shown in [Figure 13.3](#13_002.html#f13.3), three unified tasks must be successfully completed before you can arrive at a successful machine learning model:

*   Managing data  
    Today’s enterprises not only deal with structured data, usually generated by traditional IT enterprise architecture, but also a huge amount of unstructured data like audio files, video streams, and social media impressions that are generated every moment. The combination of enterprise data and big data is critical for laying the foundation for future machine learning scenarios to gain smart, valuable insights to assist with making better, more confident decisions.
    
*   Model design  
    Crafting machine learning models is a highly iterative process, and data sampling is an important part of crafting accurate models. You must consider representative samples of data generated out of actual business transactions. At the early stage, if the sample data is a known and representative set of the business, the chance of success greatly increases. After a successful pilot, the next step should be to evaluate the model with another dataset, from a totally different data source that could be relevant to hypothesis. In this way, you can check how the selected algorithm predicts outcomes from both a well-understood dataset and from a new dataset.
    
*   Model deployment and operations  
    Finally comes the deployment and management of machine learning models, which are critical activities. The deployment of a model must be performed in such a way that applications can consume the model in a scalable and secure way. Monitoring the performance of the model and triggering retraining time to time will also be critical for operations.
    

[![SAP Data IntelligenceSAP Data Intelligence](bilderklein/klein13_003.png)](img-f13.3.html) 

**Figure 13.3**    SAP Data Intelligence

Tools for managing machine learning data and creating and deploying models are the need of the moment. Luckily, the market has responded, and SAP Data Intelligence, as a cloud-based offering, rightly fits into these scaling criteria for artificial intelligence. SAP Data Intelligence is designed to overcome common hurdles ranging from connecting, understanding, and preparing data to creating, deploying, and operating machine learning models in a unified way. However, delivering and managing all these challenging phases are the responsibilities of various stakeholders, each with their own point of views, such as the following:

*   The chief information officer (CIO) will want to acquire easily deployable and scalable data science or machine learning applications at minimal cost to help the enterprise become more intelligent and deliver the right predictions.
    
*   The data science team will want a development environment that is compatible for current enterprise requirements, while still enabling further exploration.
    
*   Finally, the DevOps team will want to focus on aspects like reusability, stable deployment, and maintainability.
    

Ultimately, SAP Data Intelligence is designed exactly for these stakeholders to help them meet their goals while managing end-to-end machine learning scenarios from a single platform. Thus, before proceeding with specific use cases, let’s quickly recap the concepts behind and components of SAP Data Intelligence.

As shown in [Figure 13.3](#13_002.html#f13.3), SAP Data Intelligence includes a unique set of capabilities and features to help data engineers, data architects, data scientists, and IT operations manage the machine learning lifecycle from end to end. These features include the following:

*   Data engineers and architects can visually build data flows and data pipelines to connect, discover, and process any type of data including structured data, unstructured data, and streaming data, in any volume.
    
*   With Jupyter Notebook, data scientists can experiment with models using Python, Google TensorFlow, or R, in conjunction with machine learning with SAP HANA, and use datasets and pipelines to model machine learning solution in one central place.
    
*   Unified controls help IT operations teams execute easy deployment, monitoring, and retraining of all machine learning models, at scale.
    

###### Note

JupyterLab is a web-based interactive development environment for Jupyter Notebook and supports a wide range of workflows in data science, scientific computing, and machine learning. For more details, refer to [https://jupyter.org/](https://jupyter.org/).

Last but not the least, let’s not forget the most important aspect of applying enterprise intelligence—the data. Even with the best possible machine learning platform and data engineers, unless you have good data, your tools and teams are of no use, and inferences and generalizations derived by machine learning will fail miserably. If your data does not reflect reality, machine learning models simply cannot learn how to generalize a solution. That said, only your business experts truly understand the challenges the business faces and are uniquely equipped with the right knowledge and experience to use machine learning to gain rich insights from your data.

## 13.3    Identifying Industry Use Cases

The ongoing digitalization of industries can be represented as three expansions:

*   The expansion of the amount of data automatically generation by all the products and services for the organization
    
*   The expansion of ever more powerful algorithms to make use of the generated data
    
*   The rise of new business models based on data and its methodical analysis and use
    

These three expansions or developments are not separate; they are deeply interlinked with the potential to fundamentally change the way a traditional industry conducts business. You’ll need to understand and handle the interdependencies that exist between the information order, decision-making systems, and industry demands. In recent years, many industries have worked on these three expansions to implement machine learning along with the advantage of the Internet of Things (IoT), devices and sensors, digitalization, and big data. Now the question is how quickly this evolution will be implemented into real solutions across different industries. To understand the role of machine learning further, let’s focus on some industry use cases and see how you can apply SAP’s intelligent enterprise solutions to resolve each specific case with ease.

### 13.3.1    Manufacturing Industry

Since the introduction of the assembly line, the hunt for improved manufacturing efficiency has always been a priority. An innovative combination of hardware and software has revolutionized manufacturing, allowing maximum output with minimum resources and manpower. Industry 4.0 is revolutionizing the industry by enabling manufacturers to connect and collect manufacturing data, and a new wave of industrial AI and machine learning capabilities are gaining momentum and living up to their full potential. In particular, let’s highlight the following:

*   Monitoring real-time device data  
    Lacking real-time monitoring can cause sudden machine failures and interrupt production schedules
    
*   Predicting device health status  
    Preventive maintenance causes huge cost and labor and still downtimes are obvious
    
*   Controlling product quality  
    Human-driven quality inspection may be erroneous and time consuming
    
*   Real-time vehicle tracking  
    Lacking real-time tracking of delivery vehicle delays production schedules and causes chaos on the shop floor
    

The paradigm shifts driven by machine learning are now quite real, encouraging adoption across the industry to achieve the ultimate manufacturing goal of producing high-quality products at minimum cost. By applying machine learning, manufacturers can uncover new insights and significantly improve production efficiency, product quality, employee safety, and more.

Let’s now identify some challenging areas that the manufacturing industry has faced for decades and then try to address these challenges with machine learning.

#### Identifying Industry-Specific Challenges

The manufacturing industry is a highly competitive, multinational, regulated, and environmentally challenged business. Some specific challenges this industry faces when trying to run a seamless, connected, and smart business and operation model include the following:

*   Controlling product quality during manufacturing through pre-/postproduction quality inspection:
    
    *   Quality inspection ensures that products fulfill certain standards, as specified by manufacturer. Quality inspection can be either manual or automated, and the purpose is to measure attributes important to a product or a component, so that bad components can be removed from production before being sent to a customer.
        
    *   Relying on traditional quality inspection means thousands of items are manufactured at significant expense before a defect might be discovered, making the process cumbersome and expensive. Also, manual inspections require significant training for human experts to perform, ultimately causing bottlenecks in production and delayed time to market.
        
*   Information-based value creation with the IoT and machine learning to achieve seamless plant operations: 
    
    *   A robust solution should connect and collect data from all sorts of devices, sensors, and equipment without requiring changes to the infrastructure or systems.
        
    *   With the potential to connect everything, new technologies like IoT and machine learning make it possible to monitor and manage objects in the physical world digitally.
        
    *   Across the globe, industries are under pressure from regulatory agencies for health, safety, and environmental management and must be adhere to specific regulations.
        
*   Shop floor equipment for availability tracking, optimization, and maintenance:
    
    *   Assets and capabilities for optimizing production and profitability through real-time visibility across multiple operational assets with several integrated operations solutions.
        
    *   Emphasis on all the operating expenses (OPEX) efficiency to improve equipment usage, productivity, efficiency, yield maximization, advanced process control (APC), and real-time optimization (RTO).
        
*   Remote monitoring of the factory or vehicle tracking to optimized scheduling and navigation management:
    
    *   Monitoring factories in remote areas.
        
    *   Creating inventory replenishment requests and maintenance requests automatically by leveraging the latest machine learning technologies.
        
    *   In combination with vehicle location information, along with legacy system information about assets, tracking and optimizing product delivery with maximum asset utilization.
        

#### Understanding the Business Case

In this section, we’ll take up a key use case mentioned earlier and discuss possible solutions using machine learning. Let’s focus on the quality inspection use case for the manufacturing industry and brainstorm ways to improve the quality inspection process using machine learning.

The growing need for rapid product cycles and faster delivery in manufacturing is an opportunity for technology-driven manufacturing practices that can ultimately create high-quality products. Quality inspection is an area where demand is rising for technological advancement. Most manufacturers rely primarily on humans conducting quality inspections during manufacturing to identify defects, such as cracks or dents in manufactured products. However, this kind of human inspection is error-prone and constrained by speed, accuracy, and cost. On the other hand, besides issues of quality, additional factors behind quality deviations might include raw material, machine operating conditions, etc. In this context, modern technologies combining Internet of Things (IoT) and machine learning can help manufacturers achieve a level of specialization in improving quality control processes, reducing downtimes, and increasing productivity. Among the two capabilities, IoT can help connect and collect contextual data, while machine learning aims for minimal human intervention while achieving human-level or better accuracy. Supervised machine learning in this case can easily classify images based on historical data input instead of relying on explicit, manually defined rules for analyzing data. An example of a supervised machine learning classification problem would be to determine if a photo of a manufactured product shows a dent. In this case, the categorization process would determine if a product had a dent or did not have a dent.

#### Applying Machine Learning to Automate Quality Inspection

In this case, a unique combination of computer vision and anomaly detection algorithms can be used to automate quality inspections. Using modern camera equipment on the production line, images of the production output (finished product) can be captured, and machine learning algorithms can analyze these images in real time, automatically classifying a product as either defect free or not. If a defect is detected, the algorithm can categorize the defect. If the algorithm detects a completely new kind of defect that cannot be classified, the system can automatically raise an alert for further assistance. Then, the system administrator can evaluate the image and the predictions made by the algorithm; if required, the user can then choose the correct defect category or define a completely new category. To make this algorithm work, the training of the algorithm must include a wide range and the right variety of images so that the system can make correct interpretations by combining operational and image data.

To build this robust system, you can take advantage of SAP’s intelligence enterprise offerings by combining IoT and machine learning. You can use IoT to integrate manufacturing equipment or devices to collect the operational data, and machine learning can analyze the data to find possible defects. With both capabilities, you can determine the best possible action. Besides analyzing real-time data, the solution also continuously learns from every decision it makes based on a feedback system. As shown in [Figure 13.4](#13_003.html#f13.4), the solution architecture integrates with the production line to capture operational data, including a product image so that SAP’s intelligent enterprise offerings can be leveraged.

[![Quality Inspection Solution ArchitectureQuality inspection solution architecture](bilderklein/klein13_004.png)](img-f13.4.html) 

**Figure 13.4**    Quality Inspection Solution Architecture

In the architecture shown in [Figure 13.4](#13_003.html#f13.4), you’re taking advantage of SAP solutions for digital manufacturing to integrate your shop floor systems using SAP Plant Connectivity. Production execution data is captured using either SAP Manufacturing Execution (SAP ME) or SAP Overall Equipment Effectiveness Management (SAP OEE Management). By using SAP Data Intelligence-based AI services to analyze images and identify defects, you can take advantage of AI services by combining services like image feature extraction, customizable image classification, customizable object detection, and similarity scoring. With these functionalities, you can build a nearly real-time visual quality inspection system that performs quality inspections based on product images captured during manufacturing. For more details on AI services and machine learning with SAP HANA, refer to [Chapter 10](#10_001.html#h10).

Beside building solutions from scratch, next-generation solutions like visual AI for quality control will be introduced for manufacturing industry soon. SAP will gradually release visual AI features in multiple releases. Early releases can be leveraged for optimizing the quality inspection process and will later be extended by bringing in supplier material checks through correlation. For more details on visual AI capabilities, refer to the following link: [https://www.sap.com/dmc/exp/2018-ngbp/imc/index.html](https://www.sap.com/dmc/exp/2018-ngbp/imc/index.html).

###### Note

SAP solutions for digital manufacturing include a unique integration platform called SAP Manufacturing Integration and Intelligence (SAP MII), with solutions specially crafted for the manufacturing industry. SAP Manufacturing Execution (SAP ME) is designed for discrete industries, and SAP Overall Equipment Effectiveness Management (SAP OEE Management) is more focused on processing industry segments. As an integration platform, SAP MII offers a wide range of connectors for building integration solutions for the shop floor, including prebuilt templates to calculate key performance indicators (KPIs) from data created on the shop floor. For more details on SAP solutions for digital manufacturing, refer to [https://www.sap.com/india/products/digital-supply-chain/manufacturing.html](https://www.sap.com/india/products/digital-supply-chain/manufacturing.html).

Let’s shift our focus now to the customer service industry and explore a use case using machine learning to add valuable insights and address issues.

### 13.3.2    Customer Service Industry

The customer service industry is all about making sure that customers are happy with a particular product or service. Any customer service activity can be related to purchasing some product and also what happens after the sale including returns, repairs, etc. At one end, in a traditional approach, customer service is a little tougher to nail down and involve interactions with a human. On the other end, a technological approach is easier to define and often involves self-service kiosks, online chat with technical support, and social media interactions. Machine learning has been making strides in automating and improving customer service by improving the customer experience and reducing the human costs associated with customer service.

The customer service industry has faced challenges like slow response, long wait times, and too many channels of information for decades. Let’s see how we can address some of these issues using machine learning.

#### Identifying Industry-Specific Challenges

In today’s digital world, businesses are under increasing pressure to meet growing customer expectations for excellent service. No matter the channel, a business must respond quickly to customers requesting issue or incident resolution. Customers often express their comments/feedback via social media out of frustration and may be fed up with long wait times, dropped calls, and representatives who don’t seem to care about their problems. Customers especially hate having to repeat themselves. Some of key challenges in customer service include the following:

*   Traditional customer service   
    In today’s world, a traditional customer service system, perhaps with call centers, lack the ability to meet demand for immediate and personalized service. Customers might not get through to someone immediate who can understand the issue and provide a solution immediately, thus leading to frustration. Because of bad customer support, 78% of customers terminate the contract with different companies providing the support.
    
*   Too many channels of information  
    Customers can engage the service center from multiple channels.
    
*   Slow response rate  
    72% of customers expect a response to their complaints on social media within an hour.
    
*   Lack of human touch  
    73% of consumers prefer human interactions to resolve service issues, but human agents are often bogged down by the processing of tasks instead of engaging with customers.
    

#### Understanding the Business Case

More than a dozen relevant use cases can be found for applying machine learning to the customer service industry, but let’s look at some unique challenges and brainstorm a proper solution. Let’s look at how we can understand a customer’s intention while providing customer support through a machine learning-based, conversational chatbot, which includes the following tasks:

*   Identifying customer intention  
    Often, inefficient customer service is driven by information asymmetry, where we don’t know in advance what our user needs help with.
    
*   Connecting through multiple channels  
    In today’s technology landscape, your business must connect with customers through all possible channels, like Facebook Messenger, WeChat, WhatsApp, email, etc., and you must let them reach you however way they want to be reached, at their convenient time, and make them happy by pursuing the correct resolution. Statistics say that almost 42% of the customers must peak to multiple agents before getting an answer.
    
*   Intelligent routing  
    As customers seek resolution, you must pair them to the right agent, identifying the right case based on the types of cases encountered, priorities, and personalities, which could improve the customer experience significantly.
    
*   Automatic data capture  
    Beside providing support, you must capture customer interactions automatically instead of spending time manually recording details of each encounter. The effort saved could be channeled into shaping better support for your customers.
    

#### Using SAP Conversational AI to Build an Intelligent Customer Support Application

SAP Conversational AI in the customer service context can address all the challenges mentioned in the previous section, including identifying customer intent, connecting through multiple channels, intelligent routing, and automatic data capture through a customer chatbot. A collaborative end-to-end platform for creating chatbots including natural language processing and dialog management features, which makes it easy to connect your bots to almost all the popular messaging channels. As shown in [Figure 13.5](#13_003.html#f13.5), SAP Conversational AI includes features to perform the following tasks:

*   Detect the intent of a sentence to understand a user request and trigger appropriate action.
    
*   Detect the named entities in a sentence automatically, for example, location, date/time, temperature, etc. Additionally, you can easily set up custom entities to meet your custom use case.
    
*   Detect the customer’s language, based on user inputs, and adapt the conversation by accordingly switching languages. SAP Conversational AI currently supports variety of languages across different functionalities.
    
*   Detect the sentiment of a user input through sentiment analysis and respond accordingly.
    
    [![SAP Conversational AI in Action](bilderklein/klein13_005.png)](img-f13.5.html) 
    
    **Figure 13.5**    SAP Conversational AI in Action
    
*   Support meaningful conversation in natural language with support of context management by recognizing parts of speech, for instance, pronouns (like “it” or “that”), superlatives (like “easiest” or “most difficult”), and ordinals (like “first” or “second”), as well as entity mapping.
    

The SAP Conversational AI platform, formerly known as Recast.AI, encompasses a wide spectrum of underlying core concepts and services for building your own conversational chatbots. To understand these technicalities and for hands-on experience, refer to [Chapter 11](#11_001.html#h11).

#### Leveraging SAP Service Ticket Intelligence for Intelligent Customer Support

Besides the SAP Conversational AI platform for developing custom chatbot applications for customer support, SAP also offers a complete end-to-end solution for customer support called SAP Service Ticket Intelligence, which can intelligently and efficiently manage and route customer inquiries to the right people. The solution basically uses neural network-based deep learning to process unstructured data from the service ticket and identifies the underlying semantics. Ultimately this data is classified into their most likely categories, and relevant solutions are recommended based on that classification. SAP Service Ticket Intelligence can even process data from other channels of customer interaction, like social media posts and emails, and automatically determine classifications, routings, and responses. As shown in [Figure 13.6](#13_003.html#f13.6), SAP Service Ticket Intelligence creates training data out of historical customer ticket messages and their assigned categories and solutions to train the deep learning model. This model is based on state-of the-art, character-level, convolutional neural networks. As more service ticket information and user feedback are processed, the model improves over time. The key purpose of SAP Service Ticket Intelligence includes supporting the following tasks:

*   Customer service intelligence  
    Customer service teams processes thousands of support tickets every year, and this historical data can become a rich source of data for SAP Service Ticket Intelligence to train and help your teams speed up ticket processing by recommending case information, such as inquiry type and priority, at the moment of ticket creation.
    
*   Question answering  
    Customers expect answers to problems, not open tickets in a queue, and SAP Service Ticket Intelligence provides quick answers and recommendations based on the semantic analysis of customer input. Answers are based on the similarity of questions and answer templates.
    
*   Chatbot support  
    Customer support chatbots can also be built by using a powerful combination of SAP Conversational AI and SAP Service Ticket Intelligence application programming interfaces (APIs) in a scalable way so your support teams can reach millions of users.
    

[![SAP Service Ticket Intelligence](bilderklein/klein13_006.png)](img-f13.6.html) 

**Figure 13.6**    SAP Service Ticket Intelligence

### 13.3.3    Healthcare Service Industry

The healthcare sector has always been a trendsetter in technological advancement, and life-changing benefits are gained from these new technologies in every possible way. Machine learning is a key force in resolving many health-related problems including new medical procedures, advanced diagnostics, patient management, and treatment records across the globe. Moreover, the introduction of these emerging technologies in the healthcare industry also holds the promise of accessible, affordable, and effective healthcare. Healthcare industry challenges include:

#### Identifying Industry-Specific Challenges

The trend of adopting machine learning in healthcare solutions allows us to glimpse at a future where data, analysis, and innovation work together to bring new horizons to countless patients. Before we get to our specific use case, let’s focus on some typical pain areas across the healthcare industry:

*   Up-to-date health records  
    Doctors, nurses, and other healthcare providers spend a great deal of time maintaining up-to-date health records and other administrative tasks, which are exhausting and ultimately consume valuable time. While technology has helped to automate the data entry process, still a majority of processes require a lot of time to complete.
    
*   Early-stage drug discovery  
    One primary challenge for today’s healthcare institutions is the early-stage drug discovery process. Critical patients might be deprived of necessary treatments at the early stage of a disease, and traditional clinical applications fail to meet these challenges.
    
*   Early identification of critical disease  
    Identification and diagnosis of diseases and ailments that are hard to diagnose can include anything from cancers to genetic diseases that are often tough to catch during their initial stages.
    
*   Medical imaging diagnosis  
    Medical imaging data is potentially a rich source of information about a patient and often one of the most complex to interpret. Image interpretation by human experts can be quite limited due to its subjectivity; the complexity of the image; and extensive variations that exist across different interpreters, fatigue, and other variables.
    
*   Risk estimation  
    Today’s physicians are limited to specific sets of diagnoses or must estimate specific risks to a patient based on symptoms and available genetic information.
    
*   Crowdsourcing  
    Crowdsourcing has now become a necessity in the field of medical treatment, especially for treating different types of diseases and symptoms. At the same time crowdsourcing allows researchers and practitioners to access a vast amount of information uploaded by people based on their own consent. This live health data has great ramifications in the way medicine will be perceived down the line.
    

#### Understanding the Business Case

Machine learning and AI have progressed rapidly in recent years and now pay a key role in medical fields, especially in terms of image diagnosis, predicting the risk of disease, and enhancing the ability of doctors and researchers analyzing generic variations that may cause disease. Let’s consider how we can improve operational efficiencies in patient care and maximize data assets in our use case.

Healthcare providers across the globe face multiple challenges, including increasing costs, growing demand for convenient point-of-care options and value-added services, accurate diagnostics, and health information sharing for an aging population. The underlying impact of this growing demand is a big data explosion due to an unprecedented amount of structured and unstructured information through electronic health records coming from thousands of different mobile health apps, medical devices, and even social media. To succeed, healthcare providers must access this data and analyze the information in context to build new intelligent services such as chatbots, robotics, and automated systems. At the same time, proactive monitoring and predictive health remediation are measures that can mitigate both the size and severity of epidemics.

The value-added services healthcare providers desire from a machine learning-based patient interaction and diagnostic application include the following capabilities:

*   Chatbots  
    AI-based chatbots should have the ability to interact with patients through text-/voice-based conversation and can identify patterns in patient symptoms based on speech recognition, sentiment analysis, and image processing to form a potential diagnosis, prevent a disease, and/or recommend another appropriate course of action.
    
*   Disease diagnosis  
    AI systems can help build diagnostic systems that recognize cancerous tissue by examining medical images like X-rays, CT scans, and MRIs at a level comparable to a trained physician. AI systems may even uncover unseen insights that the human eye can miss. Thus, medical imaging analysis can become much more accurate and effective, with reduced chance of error.
    
*   Rare disease identification  
    Rare diseases identified by facial recognition are possible now using machine learning, thus helping physicians diagnose rare diseases at an early stage. Deep learning using patient photos can train a model to detect phenotypes that correlate with rare genetic diseases.
    
*   Precision medicine  
    Genomics is a branch of molecular biology that deals with the structure, evolution, function, and mapping of genomes. This field looks for links to disease from information obtained from DNA. When combined with AI, some cancers and vascular diseases might be spotted at an early stage. Moreover, AI can predict the health issues a patient might face because of his or her genes. Also, AI helps with medical parts machining, thus reducing the chance of error during surgeries.
    

#### Leveraging SAP Intelligent Enterprise for Managing Healthcare

SAP’s intelligent solutions for healthcare help clinicians with proactive monitoring and predictive health remediation by using big data analysis to identify health threats sooner. Effort spent by healthcare providers on low-value and repetitive tasks can now be steered toward improving patient care. According to SAP, the new intelligent enterprise framework for healthcare offers a set of key functionalities designed from input from healthcare industry experts, including the following functionalities:

*   An easily operational digital platform on the cloud to host clinical records along with optimized data management and security
    
*   The combined power of AI, blockchain, machine learning, and IoT for real-time and in-memory analytics embedded within business applications and processes. For example, IoT and blockchain technology can eliminate the use of counterfeit pharmaceutical products at any stage of the supply chain through unique identification and verification procedures for individual batches of medicines.
    
*   A set of intelligent healthcare enablement apps as part of the application suite designed to ensure better patient outcomes at lower costs. For example, adopting online registration and self-check-in capabilities instead of relying prolonged manual processes can ensure operational efficiency, enhance the patient experience, and better empower your workforce.
    
*   Intelligent and automated capabilities using AI to simplify and streamline patient billing, automating as much as 80% of billing, payment handling, and case-cost analytics.
    
*   Conversational AI in action can capture information about the health condition of patients and their feelings instead of manually filling out questionnaires.
    

For more details on SAP intelligent enterprise solutions for healthcare, refer to [https://www.sap.com/india/products/intelligent-enterprise.html](https://www.sap.com/india/products/intelligent-enterprise.html).

In addition to SAP’s healthcare-related offerings, other key players like IBM offer a wide spectrum of AI-driven healthcare solutions, such as IBM Watson. For example, IBM Watson Genomics is a cognitive healthcare solution with genome-based tumor sequencing for faster diagnosis, and IBM Watson Oncology is also at the forefront of leveraging the medical histories of patients to help generate multiple treatment options.

AI is changing the face of the healthcare industry with infinite possibilities. In the coming years, we’ll see more devices and biosensors with sophisticated health measurement capabilities that allow more clinical records to be available. The betterment of the healthcare industry will continue to be driven by cutting-edge, machine learning-based healthcare technologies.

### 13.3.4    Finance Industry

Well before the dawn of mobile banking apps, skillful chatbots, or search engines, machine learning has made significant impacts in the financial industry for the past decade. Few industries match the volume of historical records and the quantitative nature of the finance world, and today, applicable machine learning uses cases for the finance industry have grown exponentially because of more accessible computing power and accessible machine learning tools across several platforms. From loan approvals and credit score checks, to managing assets and risk assessment, machine learning can play an integral role in many phases of the financial ecosystem.

#### Identifying Industry-Specific Challenges

In recent years, the ability of machine learning to cope with a number of principal financial tasks has become especially important. What makes the finance industry ideal for applying machine learning? The tremendous volume of data and the nearly infinite size of this segment worldwide are certainly key factors. Let’s look at some promising use cases for the finance industry:

*   Clearing payments  
    Cash application is one of the most important components of any accounts receivable process. Primarily cash applications are processed either manually or automatically. In a manual process, a cash application specialist goes through payments and associated remittances to match customer names, invoice numbers, and amounts against existing invoices. In an automated approach, the cash application process goes through the same procedure, but payments and remittances are matched at a must faster speed. In the recent times, to save costs, some companies have adopted electronic payment modes like Automated Clearing House (ACH), wire transfers, and credit card payments. In some cases, the accounts payable department will send a single electronic payment for multiple invoices, which makes matching a much more difficult process.
    
*   Big data  
    Big data in the finance industry is both an opportunity and an obstacle. Data sourced from social media, consumer databases, and even news feeds can help financial institutions like banks serve customers better while at the same time protecting their own interests. Sifting through vast amounts of unstructured data for useful information requires powerful data analytics technology to achieve benefits.
    
*   Fraud prevention  
    In today’s world, almost every financial institution has been impacted by cyberfraud, and in this area, AI and machine learning can have a substantial impact. The detection of anomalies must be driven by analyzing spending patterns, locations, and client behaviors, but this type of precision is impossible for a human to complete, since no one person can analyze hundreds of transactions simultaneously and in real time.
    

#### Understanding the Business Case

For almost a decade, the financial services industry focused on leveraging artificial intelligence (AI) to surpass customer expectations, reduce operational costs, and make smarter overall business decisions. With machine learning as an important aspect of AI, the finance industry can reach these important business goals. The vast data volumes common in the industry make the finance industry the perfect candidate for data mining.

As a next step, we’ll select one of the key use cases we discussed in the previous section and brainstorm a machine learning-based solution for it. Let’s look at a payment clearing use case as a challenge to see how we can solve this finance industry problem using machine learning.

Cash application applies incoming payments to the correct customer accounts and to the correct receivable invoices. In this use case, accountants would traditionally manually match payments to associated invoices, a painstaking and time-consuming process. With manual handling, a customer’s credit limit might not be up to date until the finance team recognizes the payment. Moreover, manual invoice matching involving unstructured data from disparate sources like invoices, payment methods, bank statements, remittance advice information, and credit makes the process more difficult.

So, what’s the way forward? The answer is machine learning, and four key ways machine learning can improve the cash application process include the following benefits:

*   Using machine learning-based automation to improve team productivity
    
*   Eliminating reprogramming for changes to the process by automatically recognizing new forms of payment and adjusting their clearing processes accordingly
    
*   Enhancing decision-making driven by AI to access advantageous insights by analyzing patterns and running predictive simulations
    
*   Reducing sales outstanding with accountant behavior analysis that can be applied to future payments
    

#### Leveraging SAP Cash Application to Automate Payment Clearing Processes

SAP Cash Application is a cloud-based extension for invoice and payment matching processes using machine learning. SAP Cash Application takes advantage of machine learning capabilities to analyze and learn from past actions performed by accountants. The solution can capture much richer detail about the customer and country-specific behaviors without the need to manually define detailed rules and integrate these rules with your existing clearing system.

During financial transactions, especially in the accounts receivable area, incoming bank statement items are ideally matched against open receivables such as invoices. With manual postprocessing, items from incoming bank statements that couldn’t be matched to open receivables require a lot of time and effort to resolve. As shown in [Figure 13.7](#13_003.html#f13.7), SAP Cash Application uses machine learning procedures to train financial applications to learn from manual matchings, thus achieving higher-level automatic matching rates.

[![SAP Cash Application](bilderklein/klein13_007.png)](img-f13.7.html) 

**Figure 13.7**    SAP Cash Application

Let’s look at some of the unique machine learning functionalities inside SAP Cash Application, such as the following capabilities:

*   Scheduling jobs to receive a list of machine learning proposals when receivables match items in the existing bank statement.
    
*   Scheduling jobs to automatically clear items that match incoming bank statements based on machine learning proposals when:
    
    *   The matching rate of the proposal is higher thanf specified in the configuration.
        
    *   The proposed receivables are still open.
        
    *   All other clearing rules are fulfilled.
        
    *   If no criteria matches, review by accounts receivable is recommended.
        
*   Scheduling jobs to receive a list of machine learning proposals for matching accounts to existing bank statement items when:
    
    *   The matching rate of the proposal is higher than specified in the configuration.
        
    *   The proposed account is a valid existing account.
        
*   Scheduling jobs to automatically process items that match incoming bank statements to accounts based on machine learning proposals.
    
*   SAP Cash Application uses machine learning to accommodate new forms of digital payments without reprogramming your accounts receivable system while adjusting the clearing process accordingly.
    
*   Integration with SAP S/4HANA Cloud and on-premise to complement standard rules and extract value from historical data without disturbing current processing workflows.
    
*   Automatically raising flags for manual intervention when any payment does not match an invoice. However, the algorithm will add true value by suggesting potential invoice matches for consideration by the manual processor.
    
*   Faster, machine learning-driven processing of incoming payments to reduce days sales outstanding (DSO) and help to improve customer service.
    

For more details and documentation, refer to [https://help.sap.com/viewer/product/SAP\_CASH\_APPLICATION/1905/en-US](https://help.sap.com/viewer/product/SAP_CASH_APPLICATION/1905/en-US).

In addition to SAP Cash Application, SAP’s finance and risk management portfolio includes a wide spectrum of machine learning-based solutions to address the unique and challenging aspects of today’s financial industry, including performance analysis, anomaly detection, third-party risk detection, and investigations to protect the business. The portfolio offers the following solutions:

*   Payment Advice Extraction  
    To automatically process payment advices (generally in unstructured formats like emails, PDFs, paper invoices, etc.) and to extract remittance information using machine learning to drastically reduce the required manual effort.
    
*   SAP Shared Service Framework  
    To optimize accounts receivable processes and the automated execution of closing processes with SAP Shared Service Framework and the SAP Closing Cockpit.
    
*   SAP RealSpend  
    For better insights into budget- and spending-related information, including visibility and access to granular budget and spending details, thus enabling your organization to perform ad hoc spend analysis and other calculations for live business processing.
    
*   SAP Tax Compliance  
    To deal with tax compliance issues and trigger automatic corrective measures, including human intervention, while making critical tax-related decisions. The solution basically benefits from a company’s past compliance records or decisions and automatically learns from this data before recommending new decisions driven by machine learning algorithms.
    
*   SAP S/4HANA Cloud for cash management  
    To gain real-time insights into the business cash balance, to create liquidity forecasts from predictive analytics, to reduce the dependence of in-house cash controls on banks, and to integrate data from multiple sources onto a single unified platform.
    
*   SAP S/4HANA Cloud for goods receipt and invoice receipt reconciliation  
    For real-time processing of open goods and invoice receipts, period-end closings, clearing open balances on the goods receipt (GR)/invoice receipt (IR) accounts, and making intelligent recommendations driven by machine learning.
    

## 13.4    Summary

So far, you’ve seen how machine learning has evolved over the years and has transformed today’s businesses into intelligent enterprises. After a quick introduction to machine learning’s acceptance across industries, we tried to show you the machine learning ecosystem and the different stages associated with its history. To advance your understanding better, we carefully selected diverse use cases from four different industries (manufacturing, customer service, finance, and healthcare) and described the typical challenges associated with each one of these industries. Then, we applied SAP’s latest machine learning platform and intelligent assets to address each industry use case.

# 14    Conclusion and Roadmap

Throughout this book, we’ve discussed and demonstrated various concepts, tools, and features of SAP HANA Data Intelligence. The list might seem overwhelming, but with all this information, you are now well equipped with the necessary knowledge and skills to build your own intelligent enterprise solutions with confidence.

SAP HANA provides extensive machine learning capabilities through native machine learning libraries and integration with other machine learning tools like TensorFlow integration using EML and R integration. This makes SAP HANA a very powerful platform for developing machine learning solutions. As a platform, SAP Data Intelligence enables enterprises to extract value out of their data by bringing together data orchestration, metadata management, and powerful data pipelines with advanced machine learning to drive better business outcomes. Before we wrap up our book, we’ll quickly recap what you’ve learned so far in [Section 14.1](#14_001.html#h14.1). Then, we’ll discuss some best practices in [Section 14.2](#14_002.html#h14.2) and look to the road ahead in [Section 14.3](#14_003.html#h14.3).

## 14.1    Recap

SAP HANA provides native machine learning capabilities through two libraries, Predictive Analysis Library (PAL) and Automated Predictive Analysis Library (APL). SAP HANA PAL procedures provides a comprehensive set of machine learning algorithms for areas like regression analysis, classification, clustering, association analysis, time series analysis, and data preprocessing. These PAL procedures can be called through SAP HANA SQL Editor or SQLScript procedures. These algorithms are mainly for data scientists, and they allow finetuning of models through parameters. SAP HANA APL procedures are mainly for business users, they provide the ability to run prebuilt tuned models for building quick machine learning solutions. It contained prebuilt scripts which can be quickly adopted to the need of business users.SAP also provides machine learning capabilities through integration with external machine learning tools. SAP HANA EML can be used to integrate with TensorFlow models. R integration allows us to execute machine learning and statistical analysis algorithms in R using RLANG procedures from SAP HANA. SAP HANA also provides client-side APIs for R and Python to call SAP HANA PAL and APL procedures remotely from R or Python applications.SAP HANA provides native machine learning capabilities through two libraries, Predictive Analysis Library (PAL) and Automated Predictive Analysis Library (APL). SAP HANA PAL procedures provides a comprehensive set of machine learning algorithms for areas like regression analysis, classification, clustering, association analysis, time series analysis, and data preprocessing. These PAL procedures can be called through SAP HANA SQL Editor or SQLScript procedures. These algorithms are mainly for data scientists, and they allow finetuning of models through parameters. SAP HANA APL procedures are mainly for business users, they provide the ability to run prebuilt tuned models for building quick machine learning solutions. It contained prebuilt scripts which can be quickly adopted to the need of business users.SAP also provides machine learning capabilities through integration with external machine learning tools. SAP HANA EML can be used to integrate with TensorFlow models. R integration allows us to execute machine learning and statistical analysis algorithms in R using RLANG procedures from SAP HANA. SAP HANA also provides client-side APIs for R and Python to call SAP HANA PAL and APL procedures remotely from R or Python applications.

Let’s start with SAP’s official definition, which defines SAP Data Intelligence as a comprehensive solution to deliver data-driven innovation and intelligence across enterprises, unifying scalable enterprise AI and intelligent information management.

This comprehensive AI platform addresses all the needs of building intelligence enterprise solutions with its wide variety of features and services for various enterprise users including data scientists, data engineers, developers, and administrators.

SAP Data Intelligence, as the successor product of SAP Data Hub and SAP Leonardo Machine Learning Foundation, encompasses a wide spectrum of enterprise-level AI-building features covering data discovery, refinement, orchestration, composition, monitoring, and finally governance and compliance all under a single platform.

SAP Data Intelligence 3.0 offers you the flexibility to choose the deployment model of your choice, whether on-premise, in the cloud, or a hybrid, and with the Bring Your Own License (BYOL) model, you can deploy SAP Data Intelligence on-premise in your own data center or with any third-party public or private cloud provider.

Throughout this book, you learned about the most significant features of this platform, which can be summarized in the following ways:

*   Connecting a wide range of data silos through a robust connection management.
    
*   Capabilities to help govern and manage metadata assets that are spread across diverse systems and disparate sources through metadata and governance.
    
*   Making machine learning models operational with various open source tools that are familiar and popular to data scientists, such as Jupyter, R, Python, Spark, and other open source frameworks, often in a single click, through intelligent data processing.
    
*   Discovering, refining, governing, and orchestrating numerous types of data from various enterprise sources and ensuring business transformation using data orchestration and monitoring.
    
*   Building modular data pipelines connecting disparate sources and applying a wide gamut of logical operators to dive more deeply into your data and extract insights out of enterprise data through data pipelining.
    
*   Mechanizing typical data science-oriented tasks, including data preparation, feature selection, model choice, and various other tasks through automated machine learning, also called AutoML.
    
*   Enabling the visualization of machine learning runs, including comparison metrics between different runs belonging to one or more scenarios and the capture of parameters as part of the experimentation process through the Metrics Explorer.
    
*   Preserving the results of machine learning experiments performed by the data science team and acting as an essential unit in any machine learning project using machine learning tracking.
    

## 14.2    Best Practices

As a data science platform, SAP facilitates the rapid creation of machine learning models while enabling easy collaboration with your data science and analytics teams. In particular, SAP HANA and SAP Data Intelligence can be extended to access open source environment for data scientists who code in R and Python, where new innovations and custom algorithms can be built. However, all these tools may not create a competitive advantage or result in a good return on investment (ROI), unless you have best practices for data science and machine learning in mind. In this section, we’ll discuss some well-known and time-tested best practices that apply across many scenarios. Any list of best practices is always changing, and with time, more practices will be added. For now, however, let’s focus on a handful of best practices that are most essential, such as the following:

*   Data, the nucleus of any data science experiment, can create wonders, but dirty, incomplete, inconsistent, invalid, or changing data can tilt models. Thus, data must be cleansed and normalized before adoption.
    
*   Models built without rigorous training and test datasets or cross-validation processes may work well during the building phase but can fail miserably in a production environment. Thus, the continuous monitoring of models, with threshold alerts, is an essential requirement.
    
*   Every data science project faces the common challenge of recoding models to run in different environments than the environment in which the model was built, which can ultimately slow down deployment due to errors. Thus, we highly recommend building and scoring models in the same data ecosystem to minimize recoding and using APIs to execute your models through data science platforms.
    
*   Before any larger data science experiment, a safe bet is to build a formal use case to avoid your resulting unexpected models missing the mark. Start with a proof of concept and see where it leads.
    
*   Take advantage of open source innovations, including R or Python components, which often accelerate the implementation of machine learning models.
    
*   Testing and validating your models and reviewing their results on a regular basis are vital because the underlying trends that were once important assumptions when building the model could change suddenly due to external factors, thus rendering previous results invalid.
    
*   Before delivering any model, you should perform sensitivity analysis by varying input data values and even removing input variables completely. A model that can remain accurate even when an input field is missing is considered robust. A model that is overly dependent on small changes in data values or on a particular field may indicate poor performance when in production and used on new data.
    
*   Building an agile team combining multiple skills is essential for the success of a data science project. Team members should typically include the following resources:
    
    *   Data engineer, to structure the data and build the data models
        
    *   Data librarian, to understand the data
        
    *   Statistician or machine learning expert, to build the models
        
    *   DevOps, to deploy and monitor the models
        
    *   Privacy expert, to own processes to preserve privacy and stay compliant
        
    *   Business analyst, to translate the business needs
        
    *   Business ROI owner, to own the overall business results
        

## 14.3    Roadmap

The introduction of SAP Data Intelligence as a full-scale data science platform was a significant leap for SAP entering into domain of data science. The features offered by the platform are already quite striking, but even more promising features are planned in the SAP Data Intelligence roadmap, such as the following capabilities:

*   Enhancements to the Metadata Explorer with provisions to browse and preview for JavaScript Object (JSON), PDF, and some types of image files.
    
*   Extended connectivity to third-party, cloud-based data warehouses to enable the use of data from SAP Data Intelligence in non-SAP data warehouse solutions.
    
*   Integrated backup and recovery features to enable backups and restorations of an on-premise cluster for SAP Data Intelligence at any point in time.
    
*   A new resource monitoring feature inside the pipeline modeler to enable developers to monitor CPU and memory consumption using the graphs in the data pipeline modeler. This feature will simplify the profiling of resource usage for pipeline developers by showing CPU and memory resource consumption of running graphs.
    
*   New transformations on the fly feature for the pipeline modeler to support relational transformations on table messages that are received from other pipeline operators.
    
*   Enhanced file handling in data pipelines within the modeler to improve how the modeler handles structured files, such as comma-separated values (CSV), JSON, or parquet files, by providing data preview functionality on consumer operators.
    
*   Pipeline debugging feature to help trace messages between any operators by running graphs in debug mode.
    
*   Extended transformation capabilities on structured data from files and databases to run enhanced transformations without the need for custom coding.
    
*   Integration with SAP S/4HANA Cloud and the data lake concept for comprehensive support to consume and persist data in SAP S/4HANA Cloud and in data lakes.
    
*   With the typically iterative nature of a data science project, using version control is imperative. Version control helps you go back to previous versions of code, create a branch copy of current work to test a theory, and undo mistakes.
    

This list is not exhaustive, and many other features are available. For the comprehensive list of features, refer to [https://roadmaps.sap.com/](https://roadmaps.sap.com/).

On the other end, the roadmap for SAP Conversational Artificial Intelligence (SAP Conversational AI) also promises some interesting and substantial changes in the coming quarters, including the following:

*   Dynamically apply grammar rules to chatbot replies to change the grammar of the bot’s replies based on the context. For example, the chatbot should say, “vacation days” instead of “vacation day” if an employee asks for more than one day off.
    
*   A new mobile iOS software development kit (SDK) for SAP Conversational AI services that will enable you to consume chatbots from SAP Conversational AI within your own iOS applications.
    
*   Automatic bot testing to verify the expected responses of your bots whenever new changes are made to the skills and intents of the bot or to the platform.
    
*   Delivery of preconfigured SAP Conversational AI bots as part of cloud-based or on-premise solutions to SAP customers.
    
*   Enhanced emotion detection with the ability to detect seven emotions including anger, disgust, fear, joy, neutrality, sadness, and surprise thus providing additional insight into user input.
    
*   Support for Chinese as advanced-level language.
    

For more details, refer to the SAP roadmap, available at [https://roadmaps.sap.com/](https://roadmaps.sap.com/). Search for “SAP Conversational AI.”

## 14.4    Summary

SAP’s roadmap for SAP HANA, SAP Data Intelligence, SAP Conversational AI, and across various offerings especially in the machine learning space looks quite promising, and SAP is committed to introducing some great features in the coming days. Throughout this book, we’ve tried to explain how you can inject intelligence into enterprise solutions by taking advantage of existing offerings through SAP HANA, SAP Data Intelligence, and SAP Conversation AI, and we introduced you to different enterprise use cases, numerous examples, and hands-on scenarios that we hope will ultimately help you take confident steps towards building your own intelligent enterprise solutions and making the adoption of intelligent enterprise technologies even easier than ever before!

In this final paragraph of the book, we must say goodbye, but hope we walk together again in our next venture. Wish you happy reading until then.

# The Authors

[![](bilderklein/klein1926_bhowmik.png)](img-f_none_A_00.html) 

Laboni Bhowmik an experienced SAP manufacturing consultant working at IBM since 2007 with more than 15 years of experience with SAP solutions and technologies such as SAP Manufacturing Integration and Intelligence, SAP Manufacturing Execution, SAP Overall Equipment Effectiveness Management, SAPUI5, and SAP Cloud Platform. Laboni has led several large-scale SAP manufacturing implementation projects for multiple global clients and is also extensively involved in progressing IBM’s SAP Digital Manufacturing and SAP Cloud Platform competency, including designing cutting-edge industry solutions, development, publications, and mentoring.

[![](bilderklein/klein1926_dhar.png)](img-f_none_A_01.html) 

Avijit Dhar is working as a senior consultant with IBM India. Avijit has more than 15 years of experience in leading the design and implementation of multiple large-scale implementations specially in the SAP Manufacturing domain and in growing IBM’s SAP Internet of Things and machine learning practice. He is a subject matter expert in user experience, Internet of Things, machine learning, and other emerging technologies and is involved in designing numerous cutting-edge industry assets and solutions. Avijit has already authored a book on SAP Cloud Native Development from SAP PRESS.

[![](bilderklein/klein1926_mukherjee.png)](img-f_none_A_02.html) 

Ranajay Mukherjee is working as a senior solution architect of SAP Advanced Analytics in IBM India. He has more than 21 years of experience in solutioning, leading, and delivering complex analytics projects across industries. Ranajay is a subject matter expert in data science, SAP HANA, SAP BW, and jas extensively worked with research, design and development of machine learning and AI solutions using SAS, SPSS, R, and SAP HANA. He also held many leadership roles in IBM India, including SAP Enterprise HANA Practice Lead of IBM India, SAP BW powered by SAP HANA Conversion Factory Lead of IBM India. Ranajay received Outstanding Technical Achievement Award in 2019 within the entire global business services of IBM, received Eminence and Excellence Award in IBM India multiple times. Ranajay has passed Master of Statistics (MSTAT), Bachelor of Statistics (BSTAT) from Indian Statistical Institute, Kolkata. He is an Indian National Mathematics Olympiad awardee.

# Index

[↓**A**](#index.html#grp1)  [↓**B**](#index.html#grp2)  [↓**C**](#index.html#grp3)  [↓**D**](#index.html#grp4)  [↓**E**](#index.html#grp5)  [↓**F**](#index.html#grp6)  [↓**G**](#index.html#grp7)  [↓**H**](#index.html#grp8)  [↓**I**](#index.html#grp9)  [↓**J**](#index.html#grp10)  [↓**K**](#index.html#grp11)  [↓**L**](#index.html#grp12)  [↓**M**](#index.html#grp13)  [↓**N**](#index.html#grp14)  [↓**O**](#index.html#grp15)  [↓**P**](#index.html#grp16)  [↓**Q**](#index.html#grp17)  [↓**R**](#index.html#grp18)  [↓**S**](#index.html#grp19)  [↓**T**](#index.html#grp20)  [↓**U**](#index.html#grp21)  [↓**V**](#index.html#grp22)  [↓**W**](#index.html#grp23)  

?-field [\[→ Section 2.1\]](#02_001.html#i02_08)

[A ⇑](#index.html#index)

Action [\[→ Section 11.3\]](#11_003.html#i11_55)

Activation function [\[→ Section 2.3\]](#02_003.html#i02_89)

Agglomerative clustering [\[→ Section 2.3\]](#02_003.html#i02_103)

proximity measure [\[→ Section 2.3\]](#02_003.html#i02_105)

Aggregation [\[→ Section 3.4\]](#03_004.html#i03_39)

Akaike Information Criteria [\[→ Section 3.6\]](#03_006.html#i03_60) [\[→ Section 7.2\]](#07_002.html#i07_08)

Analytics Solutions Unified Method for Data Mining/Predictive Analytics [\[→ Section 3.1\]](#03_001.html#i03_08)

Application function library [\[→ Section 6.1\]](#06_001.html#i06_02)

Application function modeler [\[→ Section 1.5\]](#01_005.html#i01_35)

Artificial intelligence [\[→ Section 1.2\]](#01_002.html#i01_09) [\[→ Section 11.1\]](#11_001.html#i11_03)

Artificial neural network [\[→ Section 2.3\]](#02_003.html#i02_85)

hidden layers [\[→ Section 2.3\]](#02_003.html#i02_92)

hidden nodes [\[→ Section 2.3\]](#02_003.html#i02_93)

model design [\[→ Section 2.3\]](#02_003.html#i02_94)

multilayer [\[→ Section 2.3\]](#02_003.html#i02_91)

multilayer training [\[→ Section 2.3\]](#02_003.html#i02_95)

Association analysis [\[→ Section 2.3\]](#02_003.html#i02_115)

ASUM-DM [\[→ Section 3.1\]](#03_001.html#i03_07)

Attributes [\[→ Section 3.3\]](#03_003.html#i03_12)

categorical [\[→ Section 3.3\]](#03_003.html#i03_18)

continuous [\[→ Section 3.3\]](#03_003.html#i03_20)

discrete [\[→ Section 3.3\]](#03_003.html#i03_19)

interval [\[→ Section 3.3\]](#03_003.html#i03_16)

nominal [\[→ Section 3.3\]](#03_003.html#i03_14)

ordinal [\[→ Section 3.3\]](#03_003.html#i03_15)

ratio [\[→ Section 3.3\]](#03_003.html#i03_17)

Autogenerated pipeline [\[→ Section 10.3\]](#10_003.html#i10_41)

Automate quality inspection [\[→ Section 13.3\]](#13_003.html#i13_08)

Automated machine learning [\[→ Section 10.1\]](#10_001.html#i10_01)

Automated model training [\[→ Section 9.1\]](#09_001.html#i09_03)

Automated predictive library [\[→ Section 9.2\]](#09_002.html#i09_26)

AutoML [\[→ Section 5.4\]](#05_004.html#i05_31) [\[→ Section 10.1\]](#10_001.html#i10_03)

application [\[→ Section 10.3\]](#10_003.html#i10_26)

authorization [\[→ Section 10.3\]](#10_003.html#i10_44)

AutoML → see [\[Automated machine learning\]](#index.html#idxAutomatedmachinelearning)

cockpit [\[→ Section 10.2\]](#10_002.html#i10_12)

data science automation [\[→ Section 10.1\]](#10_001.html#i10_00)

experiment target [\[→ Section 10.3\]](#10_003.html#i10_31)

features [\[→ Section 10.2\]](#10_002.html#i10_11)

metric [\[→ Section 10.3\]](#10_003.html#i10_32)

performance cockpit [\[→ Section 10.3\]](#10_003.html#i10_36)

prediction scenario [\[→ Section 10.3\]](#10_003.html#i10_30)

process cycle [\[→ Section 10.1\]](#10_001.html#i10_10)

scenario [\[→ Section 10.3\]](#10_003.html#i10_39)

scenario popup [\[→ Section 10.3\]](#10_003.html#i10_27)

scenario section [\[→ Section 10.3\]](#10_003.html#i10_42)

scenarios list [\[→ Section 10.3\]](#10_003.html#i10_28)

setup [\[→ Section 10.3\]](#10_003.html#i10_25)

task [\[→ Section 10.3\]](#10_003.html#i10_33)

testing [\[→ Section 10.3\]](#10_003.html#i10_43)

Auto-sklearn [\[→ Section 10.1\]](#10_001.html#i10_05)

Auto-WEKA [\[→ Section 10.1\]](#10_001.html#i10_04)

Azure Machine Learning [\[→ Section 1.1\]](#01_001.html#i01_07)

[B ⇑](#index.html#index)

Back-propagation [\[→ Section 2.3\]](#02_003.html#i02_98)

Bayes classifier pipeline [\[→ Section 10.3\]](#10_003.html#i10_38)

Bayesian information criteria [\[→ Section 3.6\]](#03_006.html#i03_61)

Best practices [\[→ Section 14.2\]](#14_002.html#i14_00)

Big data [\[→ Section 12.2\]](#12_002.html#i12_06)

Binarization [\[→ Section 3.4\]](#03_004.html#i03_43)

Blockchain [\[→ Section 1.4\]](#01_004.html#i01_24) [\[→ Section 12.1\]](#12_001.html#i12_01) [\[→ Section 12.1\]](#12_001.html#i12_02)

data flow [\[→ Section 12.2\]](#12_002.html#i12_08)

use cases [\[→ Section 12.3\]](#12_003.html#i12_09)

Bot analytics [\[→ Section 11.3\]](#11_003.html#i11_78) [\[→ Section 11.3\]](#11_003.html#i11_79)

BOT API [\[→ Section 11.3\]](#11_003.html#i11_85)

Bot Builder [\[→ Section 11.3\]](#11_003.html#i11_43) [\[→ Section 11.3\]](#11_003.html#i11_44)

architecture [\[→ Section 11.3\]](#11_003.html#i11_45)

Bot Builder API [\[→ Section 11.3\]](#11_003.html#i11_94)

Bot building

custom code [\[→ Section 11.3\]](#11_003.html#i11_75)

process [\[→ Section 11.3\]](#11_003.html#i11_46) [\[→ Section 11.3\]](#11_003.html#i11_50)

user authentication [\[→ Section 11.3\]](#11_003.html#i11_74)

Bot Connector [\[→ Section 11.3\]](#11_003.html#i11_67)

architecture [\[→ Section 11.3\]](#11_003.html#i11_76)

Bot Connector API [\[→ Section 11.3\]](#11_003.html#i11_95)

channels [\[→ Section 11.3\]](#11_003.html#i11_97)

connectors [\[→ Section 11.3\]](#11_003.html#i11_96)

conversations [\[→ Section 11.3\]](#11_003.html#i11_98)

messages [\[→ Section 11.3\]](#11_003.html#i11_100)

participants [\[→ Section 11.3\]](#11_003.html#i11_99)

Bot monitoring [\[→ Section 11.3\]](#11_003.html#i11_77)

Brand impact [\[→ Section 1.3\]](#01_003.html#i01_15)

Bring Your Own License [\[→ Section 5.3\]](#05_003.html#i05_14)

Budget [\[→ Section 10.3\]](#10_003.html#i10_34)

Business entity recognition [\[→ Section 8.4\]](#08_004.html#i08_27)

Business entity recognition service [\[→ Section 8.1\]](#08_001.html#i08_05)

[C ⇑](#index.html#index)

Cell [\[→ Section 9.3\]](#09_003.html#i09_43)

Centering [\[→ Section 3.4\]](#03_004.html#i03_50)

Central tendency [\[→ Section 3.3\]](#03_003.html#i03_30)

Certificate authorities [\[→ Section 12.1\]](#12_001.html#i12_04)

Challenges [\[→ Section 13.1\]](#13_001.html#i13_03)

Channels [\[→ Section 11.2\]](#11_002.html#i11_42)

Chargrid [\[→ Section 8.2\]](#08_002.html#i08_09)

Chatbot [\[→ Section 11.1\]](#11_001.html#i11_01)

action configuration [\[→ Section 11.4\]](#11_004.html#i11_124)

build [\[→ Section 11.4\]](#11_004.html#i11_101)

connect channel [\[→ Section 11.4\]](#11_004.html#i11_107)

connect on-premise [\[→ Section 11.4\]](#11_004.html#i11_104)

continue training [\[→ Section 11.4\]](#11_004.html#i11_108)

create [\[→ Section 11.4\]](#11_004.html#i11_111)

customer service [\[→ Section 11.1\]](#11_001.html#i11_05)

establish conversation flow [\[→ Section 11.4\]](#11_004.html#i11_105)

home automation [\[→ Section 11.1\]](#11_001.html#i11_08)

language [\[→ Section 11.2\]](#11_002.html#i11_37)

learn [\[→ Section 11.4\]](#11_004.html#i11_103)

negative response [\[→ Section 11.4\]](#11_004.html#i11_125)

scheduling [\[→ Section 11.1\]](#11_001.html#i11_06)

setup project [\[→ Section 11.4\]](#11_004.html#i11_110)

status check [\[→ Section 11.1\]](#11_001.html#i11_07)

test [\[→ Section 11.4\]](#11_004.html#i11_123)

test run [\[→ Section 11.4\]](#11_004.html#i11_126)

voice [\[→ Section 11.4\]](#11_004.html#i11_127)

voice enablement [\[→ Section 11.4\]](#11_004.html#i11_106)

Classification [\[→ Section 2.2\]](#02_002.html#i02_37) [\[→ Section 2.3\]](#02_003.html#i02_63)

Classification error rate [\[→ Section 2.3\]](#02_003.html#i02_72)

Classification model [\[→ Section 2.3\]](#02_003.html#i02_99)

Classify Records Inference API [\[→ Section 8.5\]](#08_005.html#i08_35)

Cloud Foundry [\[→ Section 8.2\]](#08_002.html#i08_14)

subaccount [\[→ Section 8.2\]](#08_002.html#i08_15)

Cluster analysis [\[→ Section 2.3\]](#02_003.html#i02_100)

Code execution [\[→ Section 9.3\]](#09_003.html#i09_46)

Coefficient table [\[→ Section 7.2\]](#07_002.html#i07_10)

Cognitive synonyms [\[→ Section 11.2\]](#11_002.html#i11_14)

Condition [\[→ Section 11.3\]](#11_003.html#i11_52)

Conditional probability [\[→ Section 2.1\]](#02_001.html#i02_12) [\[→ Section 2.1\]](#02_001.html#i02_14)

Confidence [\[→ Section 2.3\]](#02_003.html#i02_117)

Connectivity [\[→ Section 5.4\]](#05_004.html#i05_55)

Conversation states [\[→ Section 11.3\]](#11_003.html#i11_65)

id [\[→ Section 11.3\]](#11_003.html#i11_66)

language [\[→ Section 11.3\]](#11_003.html#i11_68)

memory [\[→ Section 11.3\]](#11_003.html#i11_69)

participant data [\[→ Section 11.3\]](#11_003.html#i11_70)

skill [\[→ Section 11.3\]](#11_003.html#i11_71)

skill occurances [\[→ Section 11.3\]](#11_003.html#i11_72)

skill stack [\[→ Section 11.3\]](#11_003.html#i11_73)

Conversational artificial intelligence [\[→ Section 11.1\]](#11_001.html#i11_00)

Converter [\[→ Section 5.4\]](#05_004.html#i05_44)

Convolutional neural network [\[→ Section 2.3\]](#02_003.html#i02_120)

Correlation [\[→ Section 2.1\]](#02_001.html#i02_32)

Covariance [\[→ Section 2.1\]](#02_001.html#i02_31)

Credit risk data [\[→ Section 7.2\]](#07_002.html#i07_02)

CRISP-DM [\[→ Section 3.1\]](#03_001.html#i03_02)

Cross Industry Standard Process for Data Mining [\[→ Section 3.1\]](#03_001.html#i03_04)

[D ⇑](#index.html#index)

Data [\[→ Section 12.2\]](#12_002.html#i12_07)

Data attribute recommendation [\[→ Section 8.5\]](#08_005.html#i08_29)

service [\[→ Section 8.5\]](#08_005.html#i08_30)

Data attribute recommendation service [\[→ Section 8.1\]](#08_001.html#i08_06)

Data collection [\[→ Section 10.3\]](#10_003.html#i10_20)

training [\[→ Section 10.3\]](#10_003.html#i10_24)

Data conversion [\[→ Section 3.4\]](#03_004.html#i03_38)

Data lake [\[→ Section 10.3\]](#10_003.html#i10_17)

connection test [\[→ Section 10.3\]](#10_003.html#i10_18)

Data mining [\[→ Section 3.1\]](#03_001.html#i03_03)

Data monitoring [\[→ Section 5.3\]](#05_003.html#i05_12)

Data orchestration [\[→ Section 5.3\]](#05_003.html#i05_11)

Data pipelining [\[→ Section 5.3\]](#05_003.html#i05_13)

Data plotting [\[→ Section 9.3\]](#09_003.html#i09_45)

Data preparation [\[→ Section 7.2\]](#07_002.html#i07_03)

Data preprocessing [\[→ Section 3.4\]](#03_004.html#i03_37)

Data quality [\[→ Section 3.3\]](#03_003.html#i03_21)

consistency [\[→ Section 3.3\]](#03_003.html#i03_25)

duplicates [\[→ Section 3.3\]](#03_003.html#i03_28)

inaccurate [\[→ Section 3.3\]](#03_003.html#i03_22)

outlier [\[→ Section 3.3\]](#03_003.html#i03_23)

relevancy [\[→ Section 3.3\]](#03_003.html#i03_26)

timeliness [\[→ Section 3.3\]](#03_003.html#i03_27)

Data science [\[→ Section 5.1\]](#05_001.html#i05_01)

lifecyce [\[→ Section 5.2\]](#05_002.html#i05_02)

Data snapshot [\[→ Section 10.3\]](#10_003.html#i10_13)

Data table [\[→ Section 6.1\]](#06_001.html#i06_05)

Data test collection [\[→ Section 10.3\]](#10_003.html#i10_23)

Data Validation API [\[→ Section 8.5\]](#08_005.html#i08_32)

Data visualization [\[→ Section 3.3\]](#03_003.html#i03_34)

Data workflows [\[→ Section 5.4\]](#05_004.html#i05_46)

Data workspace [\[→ Section 5.4\]](#05_004.html#i05_30) [\[→ Section 10.3\]](#10_003.html#i10_19)

DBSCAN [\[→ Section 2.3\]](#02_003.html#i02_108)

border point [\[→ Section 2.3\]](#02_003.html#i02_110)

core point [\[→ Section 2.3\]](#02_003.html#i02_109)

noise point [\[→ Section 2.3\]](#02_003.html#i02_111)

Decision tree [\[→ Section 2.3\]](#02_003.html#i02_66)

brances [\[→ Section 2.3\]](#02_003.html#i02_70)

create [\[→ Section 2.3\]](#02_003.html#i02_71)

internal nodes [\[→ Section 2.3\]](#02_003.html#i02_69)

leaves [\[→ Section 2.3\]](#02_003.html#i02_68)

root [\[→ Section 2.3\]](#02_003.html#i02_67)

Deep learning [\[→ Section 2.3\]](#02_003.html#i02_118)

Define, Measure, Analyze, Improve, Control [\[→ Section 3.1\]](#03_001.html#i03_06)

Dendrites [\[→ Section 2.3\]](#02_003.html#i02_87)

Density [\[→ Section 2.1\]](#02_001.html#i02_23)

function [\[→ Section 2.1\]](#02_001.html#i02_25)

Gaussian density function [\[→ Section 2.1\]](#02_001.html#i02_27)

Deploy Model API [\[→ Section 8.5\]](#08_005.html#i08_34)

Deployment [\[→ Section 3.7\]](#03_007.html#i03_64)

Diagnostic checks [\[→ Section 3.6\]](#03_006.html#i03_59)

Dialog endpoints [\[→ Section 11.4\]](#11_004.html#i11_128)

Digital platform [\[→ Section 1.4\]](#01_004.html#i01_22)

Digital transformation [\[→ Section 12.1\]](#12_001.html#i12_03)

Dimensionality [\[→ Section 2.3\]](#02_003.html#i02_112) [\[→ Section 3.4\]](#03_004.html#i03_45)

Discretization [\[→ Section 3.4\]](#03_004.html#i03_44)

Dispersion [\[→ Section 3.3\]](#03_003.html#i03_31)

Distribution [\[→ Section 2.1\]](#02_001.html#i02_24)

function [\[→ Section 2.1\]](#02_001.html#i02_26)

Divisive clustering [\[→ Section 2.3\]](#02_003.html#i02_104) [\[→ Section 2.3\]](#02_003.html#i02_107)

DMAIC [\[→ Section 3.1\]](#03_001.html#i03_05)

Document classification [\[→ Section 8.2\]](#08_002.html#i08_08) [\[→ Section 8.2\]](#08_002.html#i08_18)

Document classification process [\[→ Section 8.2\]](#08_002.html#i08_11)

Document classification service [\[→ Section 8.1\]](#08_001.html#i08_03)

test run [\[→ Section 8.2\]](#08_002.html#i08_12)

Document information extraction [\[→ Section 8.3\]](#08_003.html#i08_24)

instance [\[→ Section 8.3\]](#08_003.html#i08_25)

service [\[→ Section 8.3\]](#08_003.html#i08_26)

Document information extraction service [\[→ Section 8.1\]](#08_001.html#i08_04)

[E ⇑](#index.html#index)

Ecosystem [\[→ Section 13.2\]](#13_002.html#i13_04)

Embedded machine learning [\[→ Section 1.5\]](#01_005.html#i01_25)

Embedded machine learning libraries [\[→ Section 4.1\]](#04_001.html#i04_02)

Ensemble methods [\[→ Section 2.3\]](#02_003.html#i02_76)

Entitlements [\[→ Section 8.2\]](#08_002.html#i08_17)

Entity [\[→ Section 11.2\]](#11_002.html#i11_29) [\[→ Section 11.2\]](#11_002.html#i11_36)

custom [\[→ Section 11.2\]](#11_002.html#i11_31) [\[→ Section 11.4\]](#11_004.html#i11_117)

free custom entities [\[→ Section 11.2\]](#11_002.html#i11_32)

gold entity [\[→ Section 11.2\]](#11_002.html#i11_30)

restricted custom entity [\[→ Section 11.2\]](#11_002.html#i11_33)

setup [\[→ Section 11.4\]](#11_004.html#i11_116)

Entropy [\[→ Section 2.3\]](#02_003.html#i02_74)

Error terms [\[→ Section 2.3\]](#02_003.html#i02_55)

Execution [\[→ Section 10.3\]](#10_003.html#i10_35)

Exogeneity [\[→ Section 2.3\]](#02_003.html#i02_47)

Expectation [\[→ Section 2.1\]](#02_001.html#i02_28)

Expression [\[→ Section 11.2\]](#11_002.html#i11_35)

Expressions [\[→ Section 11.2\]](#11_002.html#i11_26) [\[→ Section 11.3\]](#11_003.html#i11_47)

External service [\[→ Section 11.4\]](#11_004.html#i11_121)

[F ⇑](#index.html#index)

Fact sheet [\[→ Section 10.3\]](#10_003.html#i10_22)

Fast fourier transformation [\[→ Section 6.1\]](#06_001.html#i06_07)

Feature creation [\[→ Section 3.4\]](#03_004.html#i03_41)

Feature engineering [\[→ Section 10.1\]](#10_001.html#i10_08)

Feature removal [\[→ Section 3.4\]](#03_004.html#i03_42)

Files [\[→ Section 5.4\]](#05_004.html#i05_47)

Final model selection [\[→ Section 7.2\]](#07_002.html#i07_16)

Final run output [\[→ Section 9.3\]](#09_003.html#i09_48)

Fitted model [\[→ Section 4.1\]](#04_001.html#i04_45)

Forest-RC [\[→ Section 2.3\]](#02_003.html#i02_78)

Forest-RI [\[→ Section 2.3\]](#02_003.html#i02_79)

Frequency interpretation [\[→ Section 2.1\]](#02_001.html#i02_04)

Function [\[→ Section 9.3\]](#09_003.html#i09_47)

apply\_model [\[→ Section 4.1\]](#04_001.html#i04_12)

data\_visualization [\[→ Section 9.3\]](#09_003.html#i09_44)

[G ⇑](#index.html#index)

Gini index [\[→ Section 2.3\]](#02_003.html#i02_73)

Google TensorFlow [\[→ Section 1.1\]](#01_001.html#i01_06)

Governance [\[→ Section 5.3\]](#05_003.html#i05_08)

Gradient descent [\[→ Section 2.3\]](#02_003.html#i02_97)

[H ⇑](#index.html#index)

H2O [\[→ Section 10.1\]](#10_001.html#i10_06)

Hadoop [\[→ Section 5.4\]](#05_004.html#i05_48)

Healthcare [\[→ Section 12.3\]](#12_003.html#i12_14)

Heteroscedasticity [\[→ Section 2.3\]](#02_003.html#i02_54)

Hierarchical clustering [\[→ Section 2.3\]](#02_003.html#i02_102)

High leverage points [\[→ Section 2.3\]](#02_003.html#i02_59)

Histograms [\[→ Section 3.3\]](#03_003.html#i03_36)

Homoscedasticity [\[→ Section 2.3\]](#02_003.html#i02_48)

Hyperparameters [\[→ Section 10.1\]](#10_001.html#i10_07)

Hyperplane [\[→ Section 2.3\]](#02_003.html#i02_81)

maximal margin [\[→ Section 2.3\]](#02_003.html#i02_83)

separating [\[→ Section 2.3\]](#02_003.html#i02_82)

[I ⇑](#index.html#index)

IBM Watson [\[→ Section 1.1\]](#01_001.html#i01_05)

Image convolution [\[→ Section 2.3\]](#02_003.html#i02_121)

Implementation lifecycle [\[→ Section 3.1\]](#03_001.html#i03_00)

Import module [\[→ Section 9.3\]](#09_003.html#i09_42)

Independence [\[→ Section 2.1\]](#02_001.html#i02_13) [\[→ Section 2.1\]](#02_001.html#i02_15)

mutually independent [\[→ Section 2.1\]](#02_001.html#i02_17)

pairwise independence [\[→ Section 2.1\]](#02_001.html#i02_16)

Input Limits API [\[→ Section 8.5\]](#08_005.html#i08_31)

Intelligent customer support [\[→ Section 13.3\]](#13_003.html#i13_11)

Intelligent enterprise [\[→ Section 1.1\]](#01_001.html#i01_00) [\[→ Section 1.1\]](#01_001.html#i01_02) [\[→ Section 1.4\]](#01_004.html#i01_19) [\[→ Section 2.1\]](#02_001.html#i02_01)

Intelligent era [\[→ Section 1.2\]](#01_002.html#i01_08)

Intelligent invoice matching [\[→ Section 1.3\]](#01_003.html#i01_11)

Intelligent process automation [\[→ Section 1.3\]](#01_003.html#i01_17)

Intelligent processing [\[→ Section 5.3\]](#05_003.html#i05_10)

Intelligent suite [\[→ Section 1.4\]](#01_004.html#i01_20)

Intelligent technology [\[→ Section 1.1\]](#01_001.html#i01_01)

Intent [\[→ Section 11.2\]](#11_002.html#i11_34)

@buy\_product [\[→ Section 11.2\]](#11_002.html#i11_25)

@greetings [\[→ Section 11.2\]](#11_002.html#i11_23) [\[→ Section 11.4\]](#11_004.html#i11_120)

@show-oee [\[→ Section 11.4\]](#11_004.html#i11_114)

@start-sfc [\[→ Section 11.4\]](#11_004.html#i11_115)

create [\[→ Section 11.4\]](#11_004.html#i11_112)

custom [\[→ Section 11.4\]](#11_004.html#i11_113)

demonstration [\[→ Section 11.2\]](#11_002.html#i11_24)

Internet of Things [\[→ Section 1.4\]](#01_004.html#i01_23) [\[→ Section 12.1\]](#12_001.html#i12_00)

use cases [\[→ Section 12.3\]](#12_003.html#i12_10)

Interpretability [\[→ Section 3.5\]](#03_005.html#i03_54)

Invoice object recommendation [\[→ Section 8.6\]](#08_006.html#i08_36)

IPython kernel [\[→ Section 9.1\]](#09_001.html#i09_05)

[J ⇑](#index.html#index)

JavaScript object notation [\[→ Section 9.1\]](#09_001.html#i09_13)

Jupyter Notebook [\[→ Section 5.4\]](#05_004.html#i05_27) [\[→ Section 9.1\]](#09_001.html#i09_04)

adding a notebook [\[→ Section 9.1\]](#09_001.html#i09_06)

cell [\[→ Section 9.1\]](#09_001.html#i09_12)

editor [\[→ Section 9.1\]](#09_001.html#i09_09)

kernel selector [\[→ Section 9.1\]](#09_001.html#i09_10)

name [\[→ Section 9.1\]](#09_001.html#i09_08)

python sample [\[→ Section 9.1\]](#09_001.html#i09_11)

use case [\[→ Section 9.3\]](#09_003.html#i09_33)

[K ⇑](#index.html#index)

K-fold cross validation [\[→ Section 3.6\]](#03_006.html#i03_63)

K-means [\[→ Section 2.3\]](#02_003.html#i02_101)

K-nearest neighbor [\[→ Section 2.3\]](#02_003.html#i02_64)

[L ⇑](#index.html#index)

Lasso [\[→ Section 2.3\]](#02_003.html#i02_62)

Least squares [\[→ Section 2.3\]](#02_003.html#i02_44)

Lesk algorithm [\[→ Section 11.2\]](#11_002.html#i11_13)

Library options [\[→ Section 9.2\]](#09_002.html#i09_32)

Linear regression analysis [\[→ Section 2.3\]](#02_003.html#i02_42)

Linear relationship [\[→ Section 3.3\]](#03_003.html#i03_33)

Logistic regression [\[→ Section 2.3\]](#02_003.html#i02_65) [\[→ Section 7.2\]](#07_002.html#i07_05)

Logistic regression model

build [\[→ Section 7.2\]](#07_002.html#i07_07)

refinement [\[→ Section 7.2\]](#07_002.html#i07_14)

[M ⇑](#index.html#index)

Machine learning [\[→ Section 1.1\]](#01_001.html#i01_03) [\[→ Section 1.2\]](#01_002.html#i01_10) [\[→ Section 2.1\]](#02_001.html#i02_00)

algorithms [\[→ Section 2.3\]](#02_003.html#i02_41)

canvas [\[→ Section 5.4\]](#05_004.html#i05_37)

charts [\[→ Section 5.4\]](#05_004.html#i05_38)

data manager [\[→ Section 5.4\]](#05_004.html#i05_29)

impact [\[→ Section 13.1\]](#13_001.html#i13_02)

industry case [\[→ Section 13.1\]](#13_001.html#i13_01)

models [\[→ Section 6.1\]](#06_001.html#i06_14)

predictive analytics [\[→ Section 5.4\]](#05_004.html#i05_50)

run [\[→ Section 5.4\]](#05_004.html#i05_34)

run collection [\[→ Section 5.4\]](#05_004.html#i05_35)

scenario [\[→ Section 5.4\]](#05_004.html#i05_28)

scenario manager [\[→ Section 5.4\]](#05_004.html#i05_26)

scenarios [\[→ Section 2.2\]](#02_002.html#i02_34)

tracking [\[→ Section 5.4\]](#05_004.html#i05_32)

use cases [\[→ Section 13.1\]](#13_001.html#i13_00)

visual board [\[→ Section 5.4\]](#05_004.html#i05_36)

Machine learning concepts [\[→ Section 2.2\]](#02_002.html#i02_33)

Machine learning data manager

data collection [\[→ Section 10.3\]](#10_003.html#i10_16)

data workspace [\[→ Section 10.3\]](#10_003.html#i10_15)

Machine learning scenario manager [\[→ Section 9.1\]](#09_001.html#i09_02) [\[→ Section 9.3\]](#09_003.html#i09_37) [\[→ Section 10.3\]](#10_003.html#i10_40)

create notebook popup window [\[→ Section 9.3\]](#09_003.html#i09_38)

new scenario [\[→ Section 9.3\]](#09_003.html#i09_35)

setup [\[→ Section 9.3\]](#09_003.html#i09_34)

Machine learning scenario manager cockpit [\[→ Section 9.3\]](#09_003.html#i09_36)

Measurement scales [\[→ Section 3.3\]](#03_003.html#i03_13)

Memory object [\[→ Section 11.3\]](#11_003.html#i11_64)

Messages [\[→ Section 11.3\]](#11_003.html#i11_56)

buttons [\[→ Section 11.3\]](#11_003.html#i11_59)

card [\[→ Section 11.3\]](#11_003.html#i11_58)

carousel [\[→ Section 11.3\]](#11_003.html#i11_61)

image [\[→ Section 11.3\]](#11_003.html#i11_63)

list [\[→ Section 11.3\]](#11_003.html#i11_62)

quick replies [\[→ Section 11.3\]](#11_003.html#i11_60)

text [\[→ Section 11.3\]](#11_003.html#i11_57)

Metadata [\[→ Section 5.3\]](#05_003.html#i05_07)

Metadata explorer [\[→ Section 10.3\]](#10_003.html#i10_21)

Method

.create(<pass configuration object>) [\[→ Section 9.2\]](#09_002.html#i09_22)

.execute(<pass configuration object>) [\[→ Section 9.2\]](#09_002.html#i09_21)

get\_current\_version() [\[→ Section 9.2\]](#09_002.html#i09_20)

sapdi.create\_artifact [\[→ Section 9.2\]](#09_002.html#i09_18)

sapdi.create\_pipeline [\[→ Section 9.2\]](#09_002.html#i09_17)

sapdi.create\_version() [\[→ Section 9.2\]](#09_002.html#i09_19)

sapdi.get\_current\_scenario() [\[→ Section 9.2\]](#09_002.html#i09_16)

MLOps [\[→ Section 5.2\]](#05_002.html#i05_03)

Model building [\[→ Section 7.2\]](#07_002.html#i07_04)

Model deployment [\[→ Section 3.7\]](#03_007.html#i03_65) [\[→ Section 7.2\]](#07_002.html#i07_17)

Model development [\[→ Section 3.5\]](#03_005.html#i03_53)

Model evaluation [\[→ Section 3.6\]](#03_006.html#i03_55) [\[→ Section 6.1\]](#06_001.html#i06_15) [\[→ Section 6.2\]](#06_002.html#i06_25)

Model fine-tuning [\[→ Section 3.6\]](#03_006.html#i03_58)

Model overfitting [\[→ Section 3.6\]](#03_006.html#i03_56)

Model performance [\[→ Section 3.6\]](#03_006.html#i03_57)

Model refinement [\[→ Section 7.2\]](#07_002.html#i07_13)

Model tracking

entities [\[→ Section 5.4\]](#05_004.html#i05_33)

Model validation [\[→ Section 6.1\]](#06_001.html#i06_17) [\[→ Section 6.1\]](#06_001.html#i06_19) [\[→ Section 7.2\]](#07_002.html#i07_12)

Module missing error [\[→ Section 9.3\]](#09_003.html#i09_40)

Multicollinearity [\[→ Section 2.3\]](#02_003.html#i02_56) [\[→ Section 2.3\]](#02_003.html#i02_57)

Multiple linear regression [\[→ Section 2.3\]](#02_003.html#i02_51)

Multiplexer [\[→ Section 5.4\]](#05_004.html#i05_51)

[N ⇑](#index.html#index)

Name entity recognition [\[→ Section 8.4\]](#08_004.html#i08_28)

Natural language processing [\[→ Section 1.5\]](#01_005.html#i01_28) [\[→ Section 2.3\]](#02_003.html#i02_123) [\[→ Section 8.2\]](#08_002.html#i08_10) [\[→ Section 11.3\]](#11_003.html#i11_48)

bag of words [\[→ Section 2.3\]](#02_003.html#i02_124)

stemming [\[→ Section 2.3\]](#02_003.html#i02_127)

term frequency [\[→ Section 2.3\]](#02_003.html#i02_125)

tokenization [\[→ Section 2.3\]](#02_003.html#i02_126)

topic modeling [\[→ Section 2.3\]](#02_003.html#i02_128)

Natural language processing engine [\[→ Section 11.2\]](#11_002.html#i11_15)

architecture [\[→ Section 11.2\]](#11_002.html#i11_16)

context [\[→ Section 11.2\]](#11_002.html#i11_18)

entry extractor [\[→ Section 11.2\]](#11_002.html#i11_21)

intent classifier [\[→ Section 11.2\]](#11_002.html#i11_20)

question and answer [\[→ Section 11.2\]](#11_002.html#i11_19)

speech [\[→ Section 11.2\]](#11_002.html#i11_17)

Neurons [\[→ Section 2.3\]](#02_003.html#i02_86)

NLP API [\[→ Section 11.3\]](#11_003.html#i11_86)

bulk creation [\[→ Section 11.3\]](#11_003.html#i11_89)

datasets [\[→ Section 11.3\]](#11_003.html#i11_87)

expressions [\[→ Section 11.3\]](#11_003.html#i11_91)

intents [\[→ Section 11.3\]](#11_003.html#i11_90)

keys [\[→ Section 11.3\]](#11_003.html#i11_93)

logs [\[→ Section 11.3\]](#11_003.html#i11_92)

trainings [\[→ Section 11.3\]](#11_003.html#i11_88)

[O ⇑](#index.html#index)

OAuth token [\[→ Section 8.2\]](#08_002.html#i08_21)

Operator [\[→ Section 5.4\]](#05_004.html#i05_42)

data quality [\[→ Section 5.4\]](#05_004.html#i05_45)

Optimal parameter selection [\[→ Section 6.1\]](#06_001.html#i06_18) [\[→ Section 6.1\]](#06_001.html#i06_20)

Optimized manufacturing [\[→ Section 12.3\]](#12_003.html#i12_16)

Outlier [\[→ Section 2.3\]](#02_003.html#i02_60)

Output table [\[→ Section 6.1\]](#06_001.html#i06_08)

[P ⇑](#index.html#index)

Parameter table [\[→ Section 6.1\]](#06_001.html#i06_06)

Payment advice extraction [\[→ Section 13.3\]](#13_003.html#i13_16)

Perceptron [\[→ Section 2.3\]](#02_003.html#i02_88)

training [\[→ Section 2.3\]](#02_003.html#i02_90)

Performance progression [\[→ Section 10.3\]](#10_003.html#i10_37)

Pooling [\[→ Section 2.3\]](#02_003.html#i02_122)

POST service [\[→ Section 8.2\]](#08_002.html#i08_23)

Predictive algorithm [\[→ Section 1.1\]](#01_001.html#i01_04)

Predictive analytics application [\[→ Section 7.2\]](#07_002.html#i07_01)

Predictive analytics library [\[→ Section 9.2\]](#09_002.html#i09_25)

Principal component analysis [\[→ Section 2.3\]](#02_003.html#i02_113)

Principal components [\[→ Section 2.3\]](#02_003.html#i02_114)

Probability [\[→ Section 2.1\]](#02_001.html#i02_02)

assign [\[→ Section 2.1\]](#02_001.html#i02_06)

calculation [\[→ Section 2.1\]](#02_001.html#i02_07)

measure [\[→ Section 2.1\]](#02_001.html#i02_09)

properties [\[→ Section 2.1\]](#02_001.html#i02_11)

Probability space [\[→ Section 2.1\]](#02_001.html#i02_10) [\[→ Section 2.1\]](#02_001.html#i02_19)

Processing [\[→ Section 5.4\]](#05_004.html#i05_52)

Processing user expressions [\[→ Section 11.3\]](#11_003.html#i11_49)

Product similarity matching [\[→ Section 1.3\]](#01_003.html#i01_14)

Project lifecycle [\[→ Section 3.1\]](#03_001.html#i03_09)

Proximity measure [\[→ Section 2.3\]](#02_003.html#i02_106)

Python library [\[→ Section 9.2\]](#09_002.html#i09_27)

matplotlib [\[→ Section 9.2\]](#09_002.html#i09_30)

python data analysis library (pandas) [\[→ Section 9.2\]](#09_002.html#i09_28)

scientific python (SciPy) [\[→ Section 9.2\]](#09_002.html#i09_29)

scikit-learn [\[→ Section 9.2\]](#09_002.html#i09_31)

Python software development kit [\[→ Section 9.1\]](#09_001.html#i09_00)

[Q ⇑](#index.html#index)

Quality control [\[→ Section 12.3\]](#12_003.html#i12_13)

Quality inspection solution architecture [\[→ Section 13.3\]](#13_003.html#i13_09)

[R ⇑](#index.html#index)

R [\[→ Section 4.1\]](#04_001.html#i04_28)

arrays [\[→ Section 4.1\]](#04_001.html#i04_39)

client [\[→ Section 4.1\]](#04_001.html#i04_32)

commands [\[→ Section 4.1\]](#04_001.html#i04_37)

control statements [\[→ Section 4.1\]](#04_001.html#i04_43)

data frame [\[→ Section 4.1\]](#04_001.html#i04_42)

environment [\[→ Section 4.1\]](#04_001.html#i04_30)

graphs [\[→ Section 4.1\]](#04_001.html#i04_46)

integration [\[→ Section 4.1\]](#04_001.html#i04_29)

integration with SAP S/4HANA [\[→ Section 4.1\]](#04_001.html#i04_31)

list [\[→ Section 4.1\]](#04_001.html#i04_41)

matrices [\[→ Section 4.1\]](#04_001.html#i04_40)

plots [\[→ Section 4.1\]](#04_001.html#i04_47)

preliminaries [\[→ Section 4.1\]](#04_001.html#i04_36)

programming concepts [\[→ Section 4.1\]](#04_001.html#i04_35)

rserve [\[→ Section 4.1\]](#04_001.html#i04_34)

statistical models [\[→ Section 4.1\]](#04_001.html#i04_44)

vectors [\[→ Section 4.1\]](#04_001.html#i04_38)

R integration [\[→ Section 6.1\]](#06_001.html#i06_01) [\[→ Section 6.2\]](#06_002.html#i06_21)

R packages [\[→ Section 6.2\]](#06_002.html#i06_22)

R2 statistics [\[→ Section 2.3\]](#02_003.html#i02_50)

Random experiment [\[→ Section 2.1\]](#02_001.html#i02_05)

Random forest [\[→ Section 2.3\]](#02_003.html#i02_75)

bagging [\[→ Section 2.3\]](#02_003.html#i02_77)

Random variable [\[→ Section 2.1\]](#02_001.html#i02_20)

continuous [\[→ Section 2.1\]](#02_001.html#i02_22)

discrete [\[→ Section 2.1\]](#02_001.html#i02_21)

Random variables [\[→ Section 2.1\]](#02_001.html#i02_18)

Real-time connectivity [\[→ Section 12.3\]](#12_003.html#i12_12)

Recast.AI [\[→ Section 11.1\]](#11_001.html#i11_09)

Recurrent neural network [\[→ Section 2.3\]](#02_003.html#i02_119)

Regression [\[→ Section 2.2\]](#02_002.html#i02_36)

Regression coefficients [\[→ Section 2.3\]](#02_003.html#i02_45) [\[→ Section 2.3\]](#02_003.html#i02_46) [\[→ Section 2.3\]](#02_003.html#i02_52)

Reinforced learning [\[→ Section 2.2\]](#02_002.html#i02_40)

Request body [\[→ Section 10.3\]](#10_003.html#i10_45)

Requirement [\[→ Section 11.3\]](#11_003.html#i11_54)

Residual standard error [\[→ Section 2.3\]](#02_003.html#i02_49)

Ridge regression [\[→ Section 2.3\]](#02_003.html#i02_61)

Roadmap [\[→ Section 14.3\]](#14_003.html#i14_01)

Robotic process automation [\[→ Section 1.3\]](#01_003.html#i01_16)

Rserve [\[→ Section 4.1\]](#04_001.html#i04_33)

Runtime API [\[→ Section 11.3\]](#11_003.html#i11_82)

analyze endpoints service [\[→ Section 11.3\]](#11_003.html#i11_83)

dialog endpoints service [\[→ Section 11.3\]](#11_003.html#i11_84)

[S ⇑](#index.html#index)

Sampling [\[→ Section 3.4\]](#03_004.html#i03_40)

SAP AI Business Services [\[→ Section 8.1\]](#08_001.html#i08_00) [\[→ Section 8.1\]](#08_001.html#i08_02)

SAP Cash Application [\[→ Section 1.4\]](#01_004.html#i01_21) [\[→ Section 13.3\]](#13_003.html#i13_15)

SAP Cloud Appliance Library [\[→ Section 5.5\]](#05_005.html#i05_60)

SAP Cloud for Customer [\[→ Section 8.7\]](#08_007.html#i08_38)

SAP Cloud Platform [\[→ Section 1.5\]](#01_005.html#i01_32) [\[→ Section 8.2\]](#08_002.html#i08_13)

SAP Conversational AI [\[→ Section 11.1\]](#11_001.html#i11_02)

APIs [\[→ Section 11.3\]](#11_003.html#i11_81)

bot tools suite [\[→ Section 11.3\]](#11_003.html#i11_80)

build [\[→ Section 11.4\]](#11_004.html#i11_102)

entity [\[→ Section 11.2\]](#11_002.html#i11_28)

expression [\[→ Section 11.2\]](#11_002.html#i11_27)

intent [\[→ Section 11.2\]](#11_002.html#i11_22)

roadmap [\[→ Section 14.3\]](#14_003.html#i14_02)

skills [\[→ Section 11.2\]](#11_002.html#i11_10)

training datasets [\[→ Section 11.2\]](#11_002.html#i11_11)

SAP Data Hub [\[→ Section 1.5\]](#01_005.html#i01_31) [\[→ Section 5.3\]](#05_003.html#i05_05)

SAP Data Intelligence [\[→ Section 1.5\]](#01_005.html#i01_29) [\[→ Section 5.1\]](#05_001.html#i05_00) [\[→ Section 5.3\]](#05_003.html#i05_04) [\[→ Section 9.1\]](#09_001.html#i09_01) [\[→ Section 9.1\]](#09_001.html#i09_07) [\[→ Section 13.2\]](#13_002.html#i13_05)

applications [\[→ Section 5.3\]](#05_003.html#i05_15)

architecture [\[→ Section 5.3\]](#05_003.html#i05_06)

AutoML [\[→ Section 10.1\]](#10_001.html#i10_09)

built-in operators [\[→ Section 5.4\]](#05_004.html#i05_41)

connection management [\[→ Section 5.3\]](#05_003.html#i05_16)

database tools [\[→ Section 5.3\]](#05_003.html#i05_17)

diagnostics [\[→ Section 5.3\]](#05_003.html#i05_18)

governance [\[→ Section 5.4\]](#05_004.html#i05_25)

graphs [\[→ Section 5.4\]](#05_004.html#i05_43)

metadata [\[→ Section 5.4\]](#05_004.html#i05_24)

metadata explorer [\[→ Section 5.3\]](#05_003.html#i05_19)

migration [\[→ Section 5.5\]](#05_005.html#i05_59)

modeler [\[→ Section 5.3\]](#05_003.html#i05_09) [\[→ Section 5.4\]](#05_004.html#i05_40)

modeling [\[→ Section 5.3\]](#05_003.html#i05_20)

monitoring [\[→ Section 5.3\]](#05_003.html#i05_21) [\[→ Section 5.4\]](#05_004.html#i05_39)

python SDK [\[→ Section 9.2\]](#09_002.html#i09_14)

system management [\[→ Section 5.3\]](#05_003.html#i05_22)

value [\[→ Section 5.3\]](#05_003.html#i05_23)

SAP Data Intelligence SDK

setup [\[→ Section 9.2\]](#09_002.html#i09_15)

SAP HANA [\[→ Section 4.1\]](#04_001.html#i04_00) [\[→ Section 4.1\]](#04_001.html#i04_01)

calling R functions [\[→ Section 6.2\]](#06_002.html#i06_23)

python client [\[→ Section 9.2\]](#09_002.html#i09_23)

SAP HANA Automated Predictive Library [\[→ Section 1.5\]](#01_005.html#i01_33) [\[→ Section 4.1\]](#04_001.html#i04_04) [\[→ Section 4.1\]](#04_001.html#i04_11) [\[→ Section 4.1\]](#04_001.html#i04_13)

SAP HANA DataFrame [\[→ Section 9.2\]](#09_002.html#i09_24)

SAP HANA Extended Machine Learning Library [\[→ Section 1.5\]](#01_005.html#i01_34) [\[→ Section 4.1\]](#04_001.html#i04_05) [\[→ Section 4.1\]](#04_001.html#i04_14)

SAP HANA Predictive Analysis Library [\[→ Section 4.1\]](#04_001.html#i04_03) [\[→ Section 4.1\]](#04_001.html#i04_10) [\[→ Section 6.1\]](#06_001.html#i06_00)

application development [\[→ Section 7.1\]](#07_001.html#i07_00)

calling procedures [\[→ Section 6.1\]](#06_001.html#i06_09)

flowgraphs [\[→ Section 6.1\]](#06_001.html#i06_13)

functions [\[→ Section 6.1\]](#06_001.html#i06_12)

procedures [\[→ Section 6.1\]](#06_001.html#i06_03) [\[→ Section 6.1\]](#06_001.html#i06_16)

schematic [\[→ Section 6.1\]](#06_001.html#i06_04)

SAP HANA Python client API [\[→ Section 4.1\]](#04_001.html#i04_07)

SAP HANA R client API [\[→ Section 4.1\]](#04_001.html#i04_08)

SAP HANA with R integration [\[→ Section 1.5\]](#01_005.html#i01_36) [\[→ Section 4.1\]](#04_001.html#i04_06)

SAP Intelligent Robotic Process Automation [\[→ Section 1.5\]](#01_005.html#i01_27) [\[→ Section 8.1\]](#08_001.html#i08_01)

SAP Leonardo Machine Learning Foundation [\[→ Section 1.5\]](#01_005.html#i01_30)

SAP Manufacturing Execution [\[→ Section 11.4\]](#11_004.html#i11_109)

SAP RealSpend [\[→ Section 13.3\]](#13_003.html#i13_18)

SAP S/4HANA Cloud for cash management [\[→ Section 13.3\]](#13_003.html#i13_20)

SAP S/4HANA Cloud for goods receipt and invoice receipt reconciliation [\[→ Section 13.3\]](#13_003.html#i13_21)

SAP S/4HANA Customer Management [\[→ Section 8.7\]](#08_007.html#i08_39)

SAP Service Ticket Intelligence [\[→ Section 1.5\]](#01_005.html#i01_26) [\[→ Section 8.7\]](#08_007.html#i08_37) [\[→ Section 13.3\]](#13_003.html#i13_12)

SAP Shared Service Framework [\[→ Section 13.3\]](#13_003.html#i13_17)

SAP Tax Compliance [\[→ Section 13.3\]](#13_003.html#i13_19)

SAP Vora [\[→ Section 5.4\]](#05_004.html#i05_53)

Saved image [\[→ Section 9.3\]](#09_003.html#i09_49)

Scaling [\[→ Section 3.4\]](#03_004.html#i03_51)

Scatter plots [\[→ Section 3.3\]](#03_003.html#i03_35)

Scripting [\[→ Section 9.3\]](#09_003.html#i09_39)

Seaborn module [\[→ Section 9.3\]](#09_003.html#i09_41)

Semi-supervised learning [\[→ Section 2.2\]](#02_002.html#i02_39)

Sentence types [\[→ Section 11.2\]](#11_002.html#i11_41)

Sentences [\[→ Section 11.2\]](#11_002.html#i11_39)

Sentiment analysis [\[→ Section 11.2\]](#11_002.html#i11_38)

Servables [\[→ Section 4.1\]](#04_001.html#i04_18)

Service crawl response [\[→ Section 10.3\]](#10_003.html#i10_46)

Service instance [\[→ Section 8.2\]](#08_002.html#i08_19)

Service key [\[→ Section 8.2\]](#08_002.html#i08_20)

Service plan [\[→ Section 8.2\]](#08_002.html#i08_16)

Service ticket intelligence [\[→ Section 1.3\]](#01_003.html#i01_13)

Service ticket intelligence service [\[→ Section 8.1\]](#08_001.html#i08_07) [\[→ Section 8.7\]](#08_007.html#i08_40)

Shape [\[→ Section 3.3\]](#03_003.html#i03_32)

Simple linear regression [\[→ Section 2.3\]](#02_003.html#i02_43)

Skewness [\[→ Section 3.4\]](#03_004.html#i03_52)

Skill [\[→ Section 11.3\]](#11_003.html#i11_51)

overall [\[→ Section 11.4\]](#11_004.html#i11_119)

setup [\[→ Section 11.4\]](#11_004.html#i11_118)

startsfc [\[→ Section 11.4\]](#11_004.html#i11_122)

Smart recruiting [\[→ Section 1.3\]](#01_003.html#i01_12)

Spark [\[→ Section 5.4\]](#05_004.html#i05_49)

Speech acts [\[→ Section 11.2\]](#11_002.html#i11_40)

SQL editor [\[→ Section 6.1\]](#06_001.html#i06_10) [\[→ Section 6.2\]](#06_002.html#i06_24)

SQLScript [\[→ Section 6.1\]](#06_001.html#i06_11)

Standard deviation [\[→ Section 2.1\]](#02_001.html#i02_29)

Statistical regularity [\[→ Section 2.1\]](#02_001.html#i02_03)

Statistics table [\[→ Section 7.2\]](#07_002.html#i07_09)

Streaming analytics [\[→ Section 4.1\]](#04_001.html#i04_09)

Structured data [\[→ Section 3.3\]](#03_003.html#i03_10)

Structured data operators [\[→ Section 5.4\]](#05_004.html#i05_54)

Summary statistics [\[→ Section 3.3\]](#03_003.html#i03_29)

Supervised learning [\[→ Section 2.2\]](#02_002.html#i02_35)

Supply chain [\[→ Section 12.3\]](#12_003.html#i12_11)

Support [\[→ Section 2.3\]](#02_003.html#i02_116)

Support Vector Machine [\[→ Section 2.3\]](#02_003.html#i02_80) [\[→ Section 3.3\]](#03_003.html#i03_24) [\[→ Section 7.2\]](#07_002.html#i07_06)

build [\[→ Section 7.2\]](#07_002.html#i07_11)

refinement [\[→ Section 7.2\]](#07_002.html#i07_15)

Support vectors [\[→ Section 2.3\]](#02_003.html#i02_84)

Swagger UI [\[→ Section 8.2\]](#08_002.html#i08_22)

[T ⇑](#index.html#index)

Tables [\[→ Section 5.4\]](#05_004.html#i05_56)

Technology-driven transformation [\[→ Section 12.1\]](#12_001.html#i12_05)

TensorFlow [\[→ Section 4.1\]](#04_001.html#i04_15)

architecture [\[→ Section 4.1\]](#04_001.html#i04_17)

aspired version [\[→ Section 4.1\]](#04_001.html#i04_24)

features [\[→ Section 4.1\]](#04_001.html#i04_16)

integration [\[→ Section 4.1\]](#04_001.html#i04_27)

loaders [\[→ Section 4.1\]](#04_001.html#i04_22)

managers [\[→ Section 4.1\]](#04_001.html#i04_25)

models [\[→ Section 4.1\]](#04_001.html#i04_21)

servable streams [\[→ Section 4.1\]](#04_001.html#i04_20)

servable versions [\[→ Section 4.1\]](#04_001.html#i04_19)

sources [\[→ Section 4.1\]](#04_001.html#i04_23)

version policies [\[→ Section 4.1\]](#04_001.html#i04_26)

Text analysis [\[→ Section 5.4\]](#05_004.html#i05_57)

Total sum of squared errors [\[→ Section 2.3\]](#02_003.html#i02_96)

Training data collection [\[→ Section 10.3\]](#10_003.html#i10_14)

Training Job API [\[→ Section 8.5\]](#08_005.html#i08_33)

Trigger [\[→ Section 11.3\]](#11_003.html#i11_53)

[U ⇑](#index.html#index)

Unstructured data [\[→ Section 3.3\]](#03_003.html#i03_11)

Unsupervised learning [\[→ Section 2.2\]](#02_002.html#i02_38)

Use cases [\[→ Section 13.3\]](#13_003.html#i13_06)

COVID-19 [\[→ Section 12.3\]](#12_003.html#i12_15)

customer service [\[→ Section 13.3\]](#13_003.html#i13_10)

finance [\[→ Section 13.3\]](#13_003.html#i13_14)

healthcare service [\[→ Section 13.3\]](#13_003.html#i13_13)

manufacturing [\[→ Section 13.3\]](#13_003.html#i13_07)

Utilities [\[→ Section 5.4\]](#05_004.html#i05_58)

[V ⇑](#index.html#index)

Validation set approach [\[→ Section 3.6\]](#03_006.html#i03_62)

Variable selection methods [\[→ Section 2.3\]](#02_003.html#i02_53)

Variable transformation [\[→ Section 3.4\]](#03_004.html#i03_46)

centering [\[→ Section 3.4\]](#03_004.html#i03_48)

non-linear transformation [\[→ Section 3.4\]](#03_004.html#i03_47)

scaling [\[→ Section 3.4\]](#03_004.html#i03_49)

Variance [\[→ Section 2.1\]](#02_001.html#i02_30)

Variance inflation factor [\[→ Section 2.3\]](#02_003.html#i02_58)

Virtual assistance [\[→ Section 1.3\]](#01_003.html#i01_18)

Voice-based assistant [\[→ Section 11.1\]](#11_001.html#i11_04)

[W ⇑](#index.html#index)

WordNet [\[→ Section 11.2\]](#11_002.html#i11_12)

Work breakdown structures [\[→ Section 3.1\]](#03_001.html#i03_01)

Workspace [\[→ Section 10.3\]](#10_003.html#i10_29)

# Service Pages

The following sections contain notes on how you can contact us. In addition, you are provided with further recommendations on the customization of the screen layout for your e-book.

## Praise and Criticism

We hope that you enjoyed reading this book. If it met your expectations, please do recommend it. If you think there is room for improvement, please get in touch with the editor of the book: [Will Jobst](mailto:willj@rheinwerk-publishing.com). We welcome every suggestion for improvement but, of course, also any praise! You can also share your reading experience via Twitter, Facebook, or email.

## Supplements

If there are supplements available (sample code, exercise materials, lists, and so on), they will be provided in your online library and on the web catalog page for this book. You can directly navigate to this page using the following link: [https://www.sap-press.com/5014](https://www.sap-press.com/5014). Should we learn about typos that alter the meaning or content errors, we will provide a list with corrections there, too.

## Technical Issues

If you experience technical issues with your e-book or e-book account at SAP PRESS, please feel free to contact our reader service: [support@rheinwerk-publishing.com](mailto:support@rheinwerk-publishing.com).

Please note, however, that issues regarding the screen presentation of the book content are usually not caused by errors in the e-book document. Because nearly every reading device (computer, tablet, smartphone, e-book reader) interprets the EPUB or Mobi file format differently, it is unfortunately impossible to set up the e-book document in such a way that meets the requirements of all use cases.

In addition, not all reading devices provide the same text presentation functions and not all functions work properly. Finally, you as the user also define with your settings how the book content is displayed on the screen.

he EPUB format, as currently provided and handled by the device manufacturers, is actually primarily suitable for the display of mere text documents, such as novels. Difficulties arise as soon as technical text contains figures, tables, footnotes, marginal notes, or programming code. For more information, please refer to the section [Notes on the Screen Presentation](#notes.html#screenpresentation) and the following section.

Should none of the recommended settings satisfy your layout requirements, we recommend that you use the PDF version of the book, which is available for download in your online library.

## Recommendations for Screen Presentation and Navigation

We recommend using a sans-serif font, such as Arial or Seravek, and a low font size of approx. 30–40% in portrait format and 20–30% in landscape format. The background shouldn’t be too bright.

Make use of the hyphenation option. If it doesn't work properly, align the text to the left margin. Otherwise, justify the text.

To perform searches in the e-book, the index of the book will reliably guide you to the really relevant pages of the book. If the index doesn't help, you can use the search function of your reading device.

Since it is available as a double-page spread in landscape format, the table of contents we’ve included probably gives a better overview of the content and the structure of the book than the corresponding function of your reading device. To enable you to easily open the table of contents anytime, it has been included as a separate entry in the device-generated table of contents.

If you want to zoom in on a figure, tap the respective figure once. By tapping once again, you return to the previous screen. If you tap twice (on the iPad), the figure is displayed in the original size and then has to be zoomed in to the desired size. If you tap once, the figure is directly zoomed in and displayed with a higher resolution.

For books that contain programming code, please note that the code lines may be wrapped incorrectly or displayed incompletely as of a certain font size. In case of doubt, please reduce the font size.

## About Us and Our Program

The website [http://www.sap-press.com](http://www.sap-press.com) provides detailed and first-hand information on our current publishing program. Here, you can also easily order all of our books and e-books. Information on Rheinwerk Publishing Inc. and additional contact options can also be found at [http://www.sap-press.com](http://www.sap-press.com).

# Legal Notes

This section contains the detailed and legally binding usage conditions for this e-book.

## Copyright Note

This publication is protected by copyright in its entirety. All usage and exploitation rights are reserved by the author and Rheinwerk Publishing; in particular the right of reproduction and the right of distribution, be it in printed or electronic form.  
© 2021 by Rheinwerk Publishing Inc., Boston (MA)

## Your Rights as a User

You are entitled to use this e-book for personal purposes only. In particular, you may print the e-book for personal use or copy it as long as you store this copy on a device that is solely and personally used by yourself. You are not entitled to any other usage or exploitation.

In particular, it is not permitted to forward electronic or printed copies to third parties. Furthermore, it is not permitted to distribute the e-book on the Internet, in intranets, or in any other way or make it available to third parties. Any public exhibition, other publication, or any reproduction of the e-book beyond personal use are expressly prohibited. The aforementioned does not only apply to the e-book in its entirety but also to parts thereof (e.g., charts, pictures, tables, sections of text).

Copyright notes, brands, and other legal reservations as well as the digital watermark may not be removed from the e-book.

## Digital Watermark

This e-book copy contains a digital watermark, a signature that indicates which person may use this copy.

If you, dear reader, are not this person, you are violating the copyright. So please refrain from using this e-book and inform us about this violation. A brief email to [info@rheinwerk-publishing.com](mailto:info@rheinwerk-publishing.com) is sufficient. Thank you!

## Trademarks

The common names, trade names, descriptions of goods, and so on used in this publication may be trademarks without special identification and subject to legal regulations as such.

All of the screenshots and graphics reproduced in this book are subject to copyright © SAP SE, Dietmar-Hopp-Allee 16, 69190 Walldorf, Germany. SAP, the SAP logo, ABAP, Ariba, ASAP, Concur, Concur ExpenseIt, Concur TripIt, Duet, SAP Adaptive Server Enterprise, SAP Advantage Database Server, SAP Afaria, SAP ArchiveLink, SAP Ariba, SAP Business ByDesign, SAP Business Explorer, SAP BusinessObjects, SAP BusinessObjects Explorer, SAP BusinessObjects Lumira, SAP BusinessObjects Roambi, SAP BusinessObjects Web Intelligence, SAP Business One, SAP Business Workflow, SAP Crystal Reports, SAP EarlyWatch, SAP Exchange Media (SAP XM), SAP Fieldglass, SAP Fiori, SAP Global Trade Services (SAP GTS), SAP GoingLive, SAP HANA, SAP HANA Vora, SAP Hybris, SAP Jam, SAP MaxAttention, SAP MaxDB, SAP NetWeaver, SAP PartnerEdge, SAPPHIRE NOW, SAP PowerBuilder, SAP PowerDesigner, SAP R/2, SAP R/3, SAP Replication Server, SAP S/4HANA, SAP SQL Anywhere, SAP Strategic Enterprise Management (SAP SEM), SAP SuccessFactors, The Best-Run Businesses Run SAP, TwoGo are registered or unregistered trademarks of SAP SE, Walldorf, Germany.

## Limitation of Liability

Regardless of the care that has been taken in creating texts, figures, and programs, neither the publisher nor the author, editor, or translator assume any legal responsibility or any liability for possible errors and their consequences.