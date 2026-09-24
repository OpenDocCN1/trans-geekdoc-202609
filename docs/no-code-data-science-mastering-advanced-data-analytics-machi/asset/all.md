![](cover.png)

![](images/image-NUVJI28T.jpg)

  
![](images/image-7MOOIH0U.jpg)

  

Copyright © August 2023 by David Patrishkoff and Robert E Hoyt

  

First Edition: October 2023

  

All rights reserved. No part of this book may be reproduced or transmitted in any form, by any means, electronic or mechanical, including photocopying, recording, or by any information storage and retrieval system without written permission from the publisher, except for the inclusion of brief excerpts in connection with reviews or scholarly analysis.

  

Disclaimer

  

Every effort has been made to make this book as accurate as possible, but no warranty is implied. The information provided is on an “as is” basis. The authors and the publisher shall have neither liability nor responsibility to any person or entity concerning any loss or damages arising from the information contained in this book. The views expressed in the book are those of the authors and do not necessarily reflect the official policy or position of any university or government.

  

Hardcover ISBN: 978-1-312-02219-5

Paperback ISBN: 978-1-312-04040-3

Ebook Epub ISBN: 978-0-9887529-8-6

  

Book Formatting: Creative Publishing Book Design

  

## DEDICATION TO ARIF RANA - 1974 to 2023

  

We would like to dedicate our textbook to Arif Rana PhD MPH MPA MEd who left our world unexpectedly in June 2023. His last professional position held was as Associate Professor for the College of Health Sciences at SUNY Polytechnic Institute in New York.

He was passionate about every field he pursued, particularly Health Informatics. He was a close friend and colleague to both of us and he will be missed greatly.

Arif was a selfless person with a big heart, humanity-focused, and dedicated to high-quality education. He was very dedicated to our cause of democratizing the complexities of data science to a much larger group of talented professionals who can contribute to the field of data science from a no-coding perspective.

The world of health informatics, analytics, and education needs many more people like Arif who drove and supported the pursuit of bold educational innovations. If we were to assign some top-level accomplishments to the impactful life of ARIF, as an acronym, we would say that he was very Authentic, Respectful, Inspiring, and Focused. These are attributes that Arif consistently exhibited. Any of us should be proud of ourselves if we leave behind this legacy of accomplishments.

  
![](images/image-RMSS4AQ1.jpg)

## About the Authors

  
  

David Patrishkoff, M.S. is a Lean Six Sigma Master Black Belt with C-level worldwide executive experiences with engineering, quality, and manufacturing responsibilities at multi-billion-dollar revenue companies. In 2001, he founded a consulting and training company, (www.e3.business), where he has trained and consulted for organizations in over 60 different industries worldwide to resolve their mission-critical issues with innovative process improvement and data analysis techniques.

In 2018, he added machine learning techniques to gain more insights into his research of large datasets, which included the Fatality Reporting Analysis System (FARS) for motor vehicle accidents in the USA and the Home Health Outcome Assessment Information Set (OASIS) data for home healthcare patients in the USA. He speaks regularly at international conferences about his research and other topics of interest.

He has a contributing faculty position at the Kettering University School of Management in Flint, Michigan. He is also an Adjunct Professor at the Dr. Kiran C. Patel Osteopathic School of Medicine in Ft. Lauderdale, Florida, part of Nova SE University. He is also an Adjunct Professor at SUNY Polytechnic Institute in Utica, New York. He has incorporated Orange into some of the analytics classes he teaches at Nova University and at the SUNY Polytechnic Institute. He has trained, certified, and mentored many professionals in various topics, including over 3,000 professionals in Lean Six Sigma techniques. He and his company have also trained over 23,000 healthcare professionals in High-Reliability Organizations (HRO) plans to reduce medical errors in healthcare systems.

  

Dr. Robert Hoyt FACP FAMIA ABPM-CI is an internal medicine physician with a well-rounded background. He was in private practice for fifteen years in Virginia and then returned to active duty, completing three years in the US Army and seventeen in the US Navy, and retiring at the rank of Captain. In the last several years on active duty, he conducted research at the Navy Aerospace Medical Research Laboratory (NAMRL) and the Robert E. Mitchell Center for Prisoner of War Studies, located in Pensacola, Florida. He created and taught health informatics at the University of West Florida for thirteen years.

He is the editor and author of Health Informatics: Practical Guide, which is in its eighth edition. In 2014, he became board-certified in clinical informatics, and in 2016 he became a Fellow of the American Medical Informatics Association (FAMIA).

Since 2018, he has focused his attention primarily on data science as a new field that has impacted every domain, including medicine. He is passionate about teaching clinicians about important new trends in informatics and data science. This led to the creation of two new textbooks, Introduction to Biomedical Data Science (2019) and Data Preparation and Exploration (2020). Information about those textbooks can be found at https://www.informaticseducation.org.

Dr. Hoyt is the honorary president of the Medical Intelligence Society, contributing monthly to the Data Science Tip of the Month virtual meetings. He is on the Board and faculty for the American Board of Artificial Intelligence in Medicine Board Review Course. Furthermore, he is a reviewer for multiple medical journals, including the new Intelligence Based Medicine journal.

  

Using this textbook, they are currently teaching monthly data science workshops in the United States. They are passionate about teaching data literacy and no-code data science. Their website is https://nocodedatascience.net

## Table of Contents

  
  

[Foreword by William Hersh](#content0007.xhtml)

  

[PREFACE](#content0008.xhtml)

  

[CHAPTER 1: INTRODUCTION TO DATA SCIENCE](#content0009.xhtml)

[What Is Data Science?](#content0009.xhtml)

[Background](#content0010.xhtml)

[Artificial Intelligence and Machine Learning](#content0011.xhtml)

[Artificial Intelligence and Data Science](#content0012.xhtml)

[Foundations and Frontiers: Integrating DMBoK Practices with Data Science](#content0013.xhtml)

[Statistical Foundations and Predictive Frontiers: A Data Voyage](#content0014.xhtml)

[The 8-Step Data Science Discover Process](#content0015.xhtml)

[The 3 Levels of AI for Healthcare](#content0016.xhtml)

[What Do Data Scientists Do?](#content0017.xhtml)

[Why Learn Data Science?](#content0018.xhtml)

[Data Science Educational Challenges](#content0019.xhtml)

[Why Did We Create This Textbook?](#content0020.xhtml)

[Who Is The Target Audience?](#content0021.xhtml)

[Why Use Open-Source Software?](#content0022.xhtml)

[Orange Data Mining](#content0023.xhtml)

[Orange General Information](#content0024.xhtml)

[JASP Stats Package](#content0025.xhtml)

[Introduction](#content0026.xhtml)

[JASP Unique Features](#content0027.xhtml)

[JASP Organization](#content0028.xhtml)

[JASP limitations](#content0029.xhtml)

[Orange vs JASP](#content0030.xhtml)

[Putting Knowledge Into Practice](#content0031.xhtml)

[Exercise](#content0032.xhtml)

[Maturity Levels](#content0033.xhtml)

[Resources](#content0034.xhtml)

[References](#content0035.xhtml)

  

[CHAPTER 2: DATA PREPARATION AND WRANGLING](#content0037.xhtml)

[Understanding Data And Data Types](#content0037.xhtml)

[Introduction](#content0038.xhtml)

[Data Science DISCOVER Process Step 2](#content0039.xhtml)

[Data Types](#content0040.xhtml)

[Step 3 In The Data Science Process](#content0041.xhtml)

[Data Cleaning](#content0042.xhtml)

[What is Feature Engineering?](#content0043.xhtml)

[Handling Missing Data with Imputation or Deletion](#content0044.xhtml)

[Handling Outliers](#content0045.xhtml)

[Binning / Discretize](#content0046.xhtml)

[Log Transform](#content0047.xhtml)

[Feature Creation](#content0048.xhtml)

[One Hot Encoding Versus N-1 Dummy Encoding](#content0049.xhtml)

[Group Calculation Operations](#content0050.xhtml)

[Feature Splitting](#content0051.xhtml)

[Feature Scaling](#content0052.xhtml)

[Univariate, Bivariate, And Multivariate Analysis](#content0053.xhtml)

[Important Data Challenges](#content0054.xhtml)

[Curse of Dimensionality](#content0055.xhtml)

[Multicollinearity](#content0056.xhtml)

[Data Leakage](#content0057.xhtml)

[Imbalanced Data](#content0058.xhtml)

[Synthetic Data](#content0059.xhtml)

[Introduction](#content0060.xhtml)

[Synthea](#content0061.xhtml)

[AI-Generated Synthetic Tabular Data](#content0062.xhtml)

[Data Science Experiments (DSEs)](#content0063.xhtml)

[Experimental Thinking in Data Science](#content0064.xhtml)

[Nine Steps for Creating Effective Data Science Experiments](#content0065.xhtml)

[Data Science Experiment Complexity Level](#content0066.xhtml)

[Algorithm Preprocessing Defaults](#content0067.xhtml)

[Algorithm Compatibility with Other Widgets](#content0068.xhtml)

[Data Science Experiment Complexity Level Examples](#content0069.xhtml)

[Orange Data And Transform Menu Widgets](#content0070.xhtml)

[JASP Data Features](#content0071.xhtml)

[Putting Knowledge Into Practice](#content0072.xhtml)

[Exercise](#content0073.xhtml)

[Maturity Level](#content0074.xhtml)

[Resources](#content0075.xhtml)

[References](#content0076.xhtml)

  

[CHAPTER 3: DATA VISUALIZATION](#content0078.xhtml)

[Introduction](#content0078.xhtml)

[Data Visualization Tables And Plots](#content0079.xhtml)

[Statistical Tables and Displays](#content0080.xhtml)

[Basic Data Displays](#content0081.xhtml)

[Distributions](#content0082.xhtml)

[Relationships Between Variables](#content0083.xhtml)

[Time Series](#content0084.xhtml)

[Geographical Displays](#content0085.xhtml)

[Hierarchical Displays](#content0086.xhtml)

[Multivariate Displays](#content0087.xhtml)

[Statistical Models and Displays](#content0088.xhtml)

[Text Displays](#content0089.xhtml)

[Variable Ranks - Non-Regularized Versus Regularized](#content0090.xhtml)

[Dashboards And Infographics](#content0091.xhtml)

[Dashboards](#content0092.xhtml)

[Infographics](#content0093.xhtml)

[Putting Knowledge Into Practice](#content0094.xhtml)

[Exercise](#content0095.xhtml)

[Maturity Levels](#content0096.xhtml)

[Resources](#content0097.xhtml)

[References](#content0098.xhtml)

  

[CHAPTER 4: MACHINE LEARNING MODELS](#content0100.xhtml)

[Introduction](#content0100.xhtml)

[How Do Models Work?](#content0101.xhtml)

[More Modeling Concepts](#content0102.xhtml)

[Bias-Variance Tradeoff](#content0103.xhtml)

[Model Interpretability and Explainability](#content0104.xhtml)

[Gradient Descent](#content0105.xhtml)

[Local and Global Minimum](#content0106.xhtml)

[Types of Gradient Descent](#content0107.xhtml)

[Orange Algorithms](#content0108.xhtml)

[JASP Models](#content0109.xhtml)

[Linear Regression](#content0110.xhtml)

[Logistic Regression](#content0111.xhtml)

[JASP Machine Learning Algorithms](#content0112.xhtml)

[MLOps](#content0113.xhtml)

[Tackling Model Challenges](#content0114.xhtml)

[Model Bias and Fairness](#content0115.xhtml)

[Navigating Imbalanced Datasets](#content0116.xhtml)

[Hyperparameter Optimization](#content0117.xhtml)

[Avoiding Model Overfitting](#content0118.xhtml)

[Putting Knowledge Into Practice](#content0119.xhtml)

[Exercise](#content0120.xhtml)

[Maturity Levels](#content0121.xhtml)

[Resources](#content0122.xhtml)

[References](#content0123.xhtml)

  

[CHAPTER 5: MODEL EVALUATION](#content0125.xhtml)

[Model Validation](#content0125.xhtml)

[Internal Validation (IV)](#content0126.xhtml)

[External Validation (EV)](#content0127.xhtml)

[Optimal Validation (OV)](#content0128.xhtml)

[Further Validation Guidance](#content0129.xhtml)

[Model Discrimination And Calibration](#content0130.xhtml)

[Probability, Odds, Odds Ratios And Log Odds Ratios](#content0131.xhtml)

[Probability vs Odds](#content0132.xhtml)

[Odds Ratios and Log Odds Ratios](#content0133.xhtml)

[Diagnostic Tests and Likelihood Ratios](#content0134.xhtml)

[Orange Model Evaluation Widgets](#content0135.xhtml)

[Test and Score Widget](#content0136.xhtml)

[Predictions Widget](#content0137.xhtml)

[Confusion Matrix](#content0138.xhtml)

[ROC Curve Widget](#content0139.xhtml)

[Precision-Recall (PR) Curve](#content0140.xhtml)

[Other Valuable Orange Curves](#content0141.xhtml)

[Lift Curve](#content0142.xhtml)

[Calibration Plot](#content0143.xhtml)

[Residual Plots](#content0144.xhtml)

[Explain Module](#content0145.xhtml)

[Rank Widget](#content0146.xhtml)

[Feature Importance Widget](#content0147.xhtml)

[Explain Prediction Widget](#content0148.xhtml)

[Explain Model Widget](#content0149.xhtml)

[JASP Model Evaluation](#content0150.xhtml)

[Hypothesis Testing](#content0151.xhtml)

[Hypothesis Testing Example](#content0152.xhtml)

[How Hypothesis Tests Make Decisions](#content0153.xhtml)

[Type 1 and Type 2 Hypothesis Testing Errors](#content0154.xhtml)

[Hypothesis Tests Available in Orange, JASP, and BlueSky Statistics](#content0155.xhtml)

[Identifying And Addressing Concept Drift And Model Drift](#content0156.xhtml)

[Concept Drift](#content0157.xhtml)

[Model Drift](#content0158.xhtml)

[When to Retrain a Model](#content0159.xhtml)

[Putting Knowledge Into Practice](#content0160.xhtml)

[Exercise](#content0161.xhtml)

[Maturity Levels](#content0162.xhtml)

[Resources](#content0163.xhtml)

[References](#content0164.xhtml)

  

[CHAPTER 6: SUPERVISED LEARNING](#content0166.xhtml)

[Classification Modeling](#content0166.xhtml)

[Introduction](#content0167.xhtml)

[Regression Modeling](#content0168.xhtml)

[Linear regression](#content0169.xhtml)

[Simple Linear Regression (SLR)](#content0170.xhtml)

[Multiple Linear Regression (MLR)](#content0171.xhtml)

[The Dummy Variable Trap](#content0172.xhtml)

[Logistic Regression](#content0173.xhtml)

[Polynomial Regression](#content0174.xhtml)

[Linear Regression Model Regularization](#content0175.xhtml)

[Regression Performance Metrics](#content0176.xhtml)

[Putting Knowledge Into Practice](#content0177.xhtml)

[Exercises](#content0178.xhtml)

[Maturity Levels](#content0179.xhtml)

[Resources](#content0180.xhtml)

[References](#content0181.xhtml)

  

[Chapter 7: UNSUPERVISED LEARNING](#content0183.xhtml)

[Unsupervised Learning](#content0183.xhtml)

[K-Means Clustering](#content0184.xhtml)

[K-Means Clustering Exercises](#content0185.xhtml)

[Hierarchical Clustering](#content0186.xhtml)

[Principle Component Analysis (PCA)](#content0187.xhtml)

[Introduction](#content0188.xhtml)

[Routine Steps to Achieve PCA](#content0189.xhtml)

[PCA Exercises](#content0190.xhtml)

[Association Rules](#content0191.xhtml)

[Association Rules Exercise](#content0192.xhtml)

[Putting Knowledge Into Practice](#content0193.xhtml)

[Exercise](#content0194.xhtml)

[Maturity Levels](#content0195.xhtml)

[Resources](#content0196.xhtml)

[References](#content0197.xhtml)

  

[CHAPTER 8: TIME SERIES FORECASTING AND SURVIVAL ANALYSIS](#content0199.xhtml)

[Time Series Forecasting With Arima](#content0199.xhtml)

[Arima Time Series Forecasting in Orange](#content0200.xhtml)

[Pros and Cons of ARIMA Models](#content0201.xhtml)

[Survival Analysis](#content0202.xhtml)

[The General Steps to Perform Kaplan-Meier Survival Analysis](#content0203.xhtml)

[Orange Example of Kaplan-Meier Survival Analysis](#content0204.xhtml)

[Putting Knowledge Into Practice](#content0205.xhtml)

[Exercise](#content0206.xhtml)

[Maturity Levels](#content0207.xhtml)

[Resources](#content0208.xhtml)

[References](#content0209.xhtml)

  

[CHAPTER 9: GEOLOCATION](#content0211.xhtml)

[Introduction](#content0211.xhtml)

[Geolocation Exercises](#content0212.xhtml)

[Geolocation with Synthetic Data](#content0213.xhtml)

[Multi-Industry Application Examples Of Geo-Mapping And Geo-Analysis](#content0214.xhtml)

[Putting Knowledge Into Practice](#content0215.xhtml)

[Exercise](#content0216.xhtml)

[Maturity Levels](#content0217.xhtml)

[Resources](#content0218.xhtml)

[References](#content0219.xhtml)

  

[CHAPTER 10: IMAGE ANALYTICS](#content0221.xhtml)

[Introduction](#content0221.xhtml)

[Medical Field Applications](#content0222.xhtml)

[Non- Medical Field Applications](#content0223.xhtml)

[AI Imaging: Industry Application Examples](#content0224.xhtml)

[How Do CNNs Work?](#content0225.xhtml)

[The Normal Steps Of Image Analytics With a CNN](#content0226.xhtml)

[CNN Layers](#content0227.xhtml)

[Putting Knowledge Into Practice](#content0228.xhtml)

[Exercises](#content0229.xhtml)

[Maturity Levels](#content0230.xhtml)

[Resources](#content0231.xhtml)

[References](#content0232.xhtml)

  

[CHAPTER 11: TEXT MINING](#content0234.xhtml)

[Introduction](#content0234.xhtml)

[Neural Networks And NLP](#content0235.xhtml)

[Recurrent Neural Networks](#content0236.xhtml)

[Transformer and Attention Models](#content0237.xhtml)

[NLP Concepts](#content0238.xhtml)

[NLP Preprocessing Steps](#content0239.xhtml)

[Topic Analysis](#content0240.xhtml)

[Large Language Models (LLMs)](#content0241.xhtml)

[Graphs From Text](#content0242.xhtml)

[Code Assistants](#content0243.xhtml)

[Small Language Models (SLM)](#content0244.xhtml)

[Orange NLP Widgets](#content0245.xhtml)

[Text Document Widgets](#content0246.xhtml)

[Preprocess Text Widget](#content0247.xhtml)

[Document Embedding Widget](#content0248.xhtml)

[Bag of Words Widget](#content0249.xhtml)

[Topic Modeling Widget](#content0250.xhtml)

[Putting Knowledge Into Practice](#content0251.xhtml)

[Exercises](#content0252.xhtml)

[Maturity Levels](#content0253.xhtml)

[Resources](#content0254.xhtml)

[References](#content0255.xhtml)

  

[CHAPTER 12: INTEGRATING CONTINUOUS IMPROVEMENT AND DATA SCIENCE INTO INDUSTRY 4.0](#content0257.xhtml)

[Introduction](#content0257.xhtml)

[Industry And Sector 4.0 Initiatives](#content0258.xhtml)

[Accelerating Industry 4.0: The Pivotal Role Of Continuous Improvement (CI) Programs](#content0259.xhtml)

[Eleven Powerful Continuous Improvement Techniques](#content0260.xhtml)

[Hoshin Kanri with Catchball Strategic Planning](#content0261.xhtml)

[Six Sigma](#content0262.xhtml)

[Lean / Kaizen](#content0263.xhtml)

[Lean Six Sigma](#content0264.xhtml)

[Predictive Modeling](#content0265.xhtml)

[High Reliability Organizations (HROs)](#content0266.xhtml)

[Agile Versus Waterfall Thinking](#content0267.xhtml)

[Cascading Risk Management (CRM)](#content0268.xhtml)

[AI Systems](#content0269.xhtml)

[AI Chatbots](#content0270.xhtml)

[Innovation-On-Demand Techniques](#content0271.xhtml)

[The Redwood Approach: Building Business Resilience Through Cooperative Strength](#content0272.xhtml)

[Maturity Levels](#content0273.xhtml)

[Resources](#content0274.xhtml)

[References](#content0275.xhtml)

  

[APPENDIX A: DATA VISUALIZATION](#content0277.xhtml)

  

[APPENDIX B: MACHINE LEARNING ALGORITHMS](#content0278.xhtml)

  

[APPENDIX C: GLOSSARY](#content0279.xhtml)

  

[INDEX](#content0280.xhtml)

## Foreword

  

### By William Hersh MD

  
  

One of the major adages of learning and practicing medicine in the 20 th century was that you needed to have as much knowledge as possible in your brain to handle all possible diagnostic and therapeutic situations in medicine to be the most effective clinician. This was probably not true in 1987 when I was finishing my own training in internal medicine and is certainly not true now a couple decades into the 21 st century. Not only is there no way any human can have all the knowledge required to practice medicine in their head, but there is still so much more we do not know about diseases and their treatments that lurks in data that is increasingly available.

Computers and their data had been an interest of mine since being exposed to early computers in high school in the 1970s and desktop computers in the 1980s. I was thrilled to discover the field of what we then called medical informatics while in medical school, and that one can get advanced training in a fellowship, which I pursued at Harvard University from 1987-1990. When I told one of the attending physicians from my residency program of my plans to pursue such a fellowship, he replied, “Why would you want to put things in a computer? You need to have all of that knowledge in your head.” Fortunately, this did not deter me from what I like to think has been a successful career in what we now call biomedical and health informatics (BMHI).

I entered my fellowship and the field of BMHI at the end of the first era of artificial intelligence (AI), when the world was entering the so-called “AI winter.” Into the 1990s, BMHI moved on from the first era of AI and focused on other areas, such as developing electronic health records (EHRs), building search systems able to access to growing online corpus of knowledge, and implement systems to engage patients via telehealth, mobile devices, and other digital means. There were a number of reasons for the failure of first-era AI systems. Computing technology itself was slow and cumbersome. EHRs were not yet widely available, so clinicians had to disrupt their workflow to use any kind of AI. Perhaps most challenging to early AI systems in medicine and beyond was the approach of manually building knowledge bases on which computer algorithms would operate, which was highly complex and not scalable. The field of machine learning was nascent in the 20th century, but systems were slow and data available for learning were small.

Into the 21st century, conditions became ripe for a thaw in the AI winter. Computers grew in speed and power, facilitated by the maturation of the global Internet. Equally important was the huge growth of data, not only from the widespread adoption of EHRs, but also from pages of the World Wide Web, images and other media beyond text, and mobile computing and sensors. Also important were conceptual breakthroughs in machine learning, including deep learning and, more recently, generative AI with tools such as ChatGPT.

Until recently, most of the advances in AI have been in so-called predictive AI, with systems typically employing some kind of deep learning to be able to make diagnoses, predict risk of adverse patient outcomes, and solve previously unsolvable problems, such as predicting the structure of proteins from amino acid sequences. Virtually every industry is now data-driven, using those insights to improve quality, reduce costs, and, in the case of for-profit industries, increase profits. In healthcare and other non-profit sectors, insights from data can also reduce costs and improve outcomes. There is, however, one rate-limiting step for the use of data science, which is that there are not enough data scientists to analyze all of the available and potentially usable datasets and databases. As such, we need tools to bring data science to those who are not data scientists, such as clinicians, administrators, and policy-makers in healthcare. This includes no-code data science tools such as the free and open-source Orange and JASP that are taught in this book.

Those who are not data scientists also need basic data science competency. They do not need to be computer programmers, but they must understand core principles, such as understanding the data they are using, its limitations and biases, and the different types of models that deliver actionable insights and prescriptions. Even computer programmers themselves can improve their efficiency with new AI tools such as ChatGPT and other large language models that are generating low-code and no-code new tools for data analysis. A popular example is Code Interpreter, a ChatGPT plug-in that generates computer code.

In healthcare, informatics students are well-positioned to enhance their data science knowledge and apply it, particularly when EHR and other data become more obtainable and pervasive. A recent viewpoint in the New England Journal of Medicine notes that physicians and medical students must be trained for the era of clinical algorithms, which requires them to be data-literate and understand both the function and limitations of new AI tools.

Fortunately, there are tools that allow an ever-larger number of professionals in many fields to learn and apply data science without having to write code. This book provides a rich curriculum for individuals from many diverse professions to learn data science using tools such as Orange and JASP. The authors note from the outset that data science is more than loading data into models and applying the output, and requires skills in other tasks, such as data cleaning, exploration, and visualization. In addition to the classic machine learning models for classification and regression, the book also explores other uses of data science, such as image analysis and text mining. An accompanying website provides data sets and other resources for using and teaching from the book.

  

William Hersh, MD

Professor

Department of Medical Informatics & Clinical Epidemiology

School of Medicine

Oregon Health & Science University

Portland, OR, USA

## Preface

  
  

In this age marked by an onslaught of dirty, missing, confusing, collinear, irrelevant, and misleading data, the power of data science lies not only in the hands of coders, but also in the hands of the curious, the innovative, and other analytically skilled individuals who are not coders. “No-Code Data Science” is more than a book; it is a movement, a call to action, and a statement that any inquisitive mind can engage with to extract significant insights from data without being mired in programming language syntaxes.

We’ll be diving deep into the ocean of data analytics and predictive analytics as we cast a light on the mysteries that lie beneath the surface of raw data. From crafting compelling visual narratives to devising the most engaging predictive models, this book is a voyage through the vast expanse of data science, but without the traditional barrier of coding. The widespread adoption of data science and predictive analytics in small and medium-sized organizations relies on moving away from the intricate demands of Python, R, or SQL coding towards user-friendly, no-code data science analytics platforms. This shift can be realized by a new breed of no-code data scientists—individuals deeply knowledgeable in data science, yet free from the coding constraints that have historically slowed many organizations’ data-driven journeys.

In the chapters that lie ahead, we break down the imposing walls of jargon and complexity, empowering you to:

1\. Meticulously prepare and mold your data

2\. Paint stories with compelling data visualizations

3\. Effectively explain predictive models to stakeholders to build trust

4\. Harness the predictive might of advanced analytics

5\. Navigate the turbulent waters of time series predictions and survival analysis

6\. Chart the geographical terrains with geolocation-based analyses

7\. Decipher the visual world through image analytics

8\. Explore the depths of unstructured data with text mining

9\. Envision the integration of various continuous improvement methodologies with data science

10\. Sculpting the future image of Industry 4.0

While describing how to master these lofty tasks, we also explain the convergence of no-code data science with the revolutionary realm of low-code AI. As we clarify the distinctions between data science, business intelligence, and statistics, we emphasize that the true essence of data science isn’t just focused on the details of algorithms but in answering the most inquisitive questions of humans.

While reading this book, keep in mind that data science is a continuous journey and not a destination where you rest and revel in your past achievements. The data science process is circular and not linear as it is constantly interpreting new data and creating new insights in real time. Data science welcomes disciplined and analytical thinkers who want to build a better world they want to live in. The power of predictive data analytics is now within your grasp, no matter what your position in your organization.

The key to success lies in asking the most important questions, gathering the most relevant data, cleaning and preparing your data, conducting exploratory data analysis, building great predictive models, vividly visualizing the past with great insights, clearly explaining you findings to others, and revolutionizing your organization’s ability to consistently impress your customers and patients, all without a line of code.

Here’s to a new dawn of democratized data science.

Welcome aboard.

The images placed on the first page of each chapter and the cover were generated by generative AI (Bing Image Creator https://www.bing.com/create)

Our website provides more information about the textbook, our workshop, our file-share site and other related activities. Our website link: https://www.nocodedatascience.net

Acknowledgement: a special thanks to Dr. Ann Yoshihashi who was instrumental in formatting and publishing this textbook

  

David Patrishkoff MS LSSMBB

Robert E Hoyt MD FACP FAMIA ABPM-CI

  

![](images/image-KE9PCHHT.jpg)Chapter 1

  

## Introduction to Data Science

  

“I have been impressed with the urgency of doing. Knowing is not enough; we must apply. Being willing is not enough; we must do”

—Leonardo da Vinci

  
![](images/image-M6MTZISG.jpg)  
  

LEARNING OBJECTIVES

  
  

By the end of chapter one, readers should be able to:

•Discuss why data science is an essential topic in all domains.

•Discuss the multidisciplinary nature of data science.

•Enumerate the typical skill set of a data scientist.

•Compare the three main open-source programs, Orange, JASP, and BlueSky Statistics.

•Discuss the differences between data science, data management, statistics, and business intelligence.

•Discuss the various practical applications for data science in various industries.

  
  

Chapter 1 Summary

  

  

This chapter delves into the exploration of data science, defining its key components, tracing its historical evolution, and highlighting its vital importance in our data-centric world. It also covers the rationale behind this textbook’s creation, aimed at providing an enriching learning experience for both newcomers and established professionals in the field. We describe the differences between data science, business intelligence, and statistics as well as the important integration between data science and data management. In addition, we shed light on our decision to use open-source software as our primary educational platform due to its transparency, affordability, adaptability, and its ability to more rapidly train and engage more no-code data scientists on data science projects. We strive to offer professionals more career options at a time when many organizations of all sizes are struggling to find the talent they need to integrate predictive analytics with their business strategies. This chapter lays the foundation for future chapters where open-source tools will be applied to a variety of data types including tabular data, images, and text.

  

Key Principles

•Data science is an interdisciplinary field that requires collaboration.

•There is no universally accepted definition of data science, nor is there a data science parent organization.

•No-code data science promotes the democratization of the field with no shortcuts or compromises in analysis capabilities.

•Data science requires a step-wise process that is robust, reliable and repeatable.

  

  

1.1 WHAT IS DATA SCIENCE?

  

  

Data science is pervasive in all industries. The digital revolution has generated an avalanche of data that requires expert analysis.¹ While the increasing emphasis is on machine learning and artificial intelligence, we should not lose sight of the importance of data preparation, exploration, and visualization. Approximately two-thirds of the time a data scientist spends on a project is related to getting the data ready for modeling.² Therefore, there is a need for both basic and advanced data science skills.

  

  

KEY POINT: According to Wikipedia, data science can be defined as “an interdisciplinary field that uses scientific methods, processes, algorithms, and systems to extract knowledge and insights from noisy, structured and unstructured data, and apply knowledge and actionable insights from data across a broad range of application domains.” ³ Data science is a convenient umbrella terminology encompassing computational and statistical expertise. It is worth noting that there is no widely accepted definition of data science, nor is there a parent-professional organization.

  

  

This book will explore the multi-faceted realm of data science, with a focus on four pivotal analytical domains: Machine Learning for Tabular Data, Predictive Image Analytics, Predictive Text Mining, and Artificial Intelligence (AI). Table 1.1 provides a snapshot of a few select industries, showcasing how various data science application examples are deployed for those domains. ⁴-⁷

Data science is a relatively new field with significant popularity and hype. For example, in 2012, the Harvard Business Review termed data science “the sexiest job of the 21st century.” ⁸ This aphorism is overly glamorous, as data scientists spend the majority of time finding, cleaning, preparing, and exploring data, which can be arduous.

  

  

KEY POINT: No-code data science means a programming language is not required to perform a function, such as creating a box plot. Instead, the function uses a graphical user interface (GUI) to create the image. No-code data science leads to more people being involved in data science, or the democratization of the field. Software programs such as Orange and JASP are examples of no-code data science.

  

  

#### 1.1.1 Background

  

In 1962, John Tukey, a renowned statistician, made a pronouncement that reverberated in the statistical world. He stated, “I have come to feel that my central interest is in data analysis, which I take to include among other things: procedures for analyzing data, techniques for interpreting the results of such procedures, ways of planning the gathering of data to make its analysis easier, more precise or more accurate….” He clearly saw the analytical world larger than just statistics and could sense that computing would change data analysis forever. ⁹

William Cleveland, a computer scientist, and statistician, was the first to publish the term “data science” in 2001. He also envisioned the field as more expansive than just statistics and dealt with much more than just theory. ¹⁰ Early data scientists worked for some of the most innovative Internet companies, such as Google, Facebook, LinkedIn, and Twitter, to assist them in gaining insights into the avalanche of new data. The term “data scientist” is attributed to DJ Patil (LinkedIn) and J Hammerbacher (Facebook) in 2008.¹⁰ Data scientists generated new data use cases for the consumer and new business models and products. At this early stage, professionals in the field labeled themselves as data scientists, even without formal degrees. The advent of the Internet was perhaps the most significant source of the data explosion. For example, in 2023, there are, on average, approximately 8.5 billion Google searches per day. ¹¹

Almost every Internet activity today can be measured (datafied or quantified) and mined. In addition to the meteoric increase in data volume, there is also tremendous variety in the data, such as location data (geographic information system), survey data, image data, email data, tweet data, and sensor data. The data science field has been facilitated by faster computer processor speed (the addition of GPUs and TPUs), open-source software designed to process large volumes of data, and more expansive storage. In the biomedical domain, the electronic health record and genomic databases comprise the two largest data sources waiting to be mined. Data science has also benefited from the “open data” era, where industry and government have tried to make data available for the public, developers, and researchers.¹²

  

#### 1.1.2 Artificial Intelligence and Machine Learning

  

Artificial intelligence (AI) has existed since the 1950s, but it has not been a significant aspect of data science until the last two decades. The term “artificial intelligence” is attributed to John McCarthy, an early computer scientist who introduced the term in 1956 at a Dartmouth conference.¹³ Further historical details about AI can be found with these references.¹⁴-¹⁵ Figure 1.1 outlines the history of modern AI and its contributing factors over three decades.¹⁶

The following are important definitions:

Artificial intelligence (AI): “refers to systems that display intelligent behaviour by analysing their environment and taking actions - with some degree of autonomy - to achieve specific goals.” ¹⁷

  

Table 1.1 Various industry applications of data science

  
![](images/image-95V4G2HN.jpg)  

Machine Learning (ML): “is a type of artificial intelligence (AI) that provides computers with the ability to learn without being explicitly programmed. Machine learning focuses on the development of computer programs that can change when exposed to new data.” ¹⁸

Deep Learning (DL): “discovers intricate structure in large datasets by using the backpropagation algorithm to indicate how a machine should change its internal parameters that are used to compute the representation in each layer from the representation in the previous layer.” ¹⁹ Additionally, it is a type of machine learning that uses algorithms (neural networks) with additional hidden layers to handle very large and complex datasets.

  
![](images/image-ICXXTCM1.jpg)  

Figure 1.1 AI Temporal Progression

  

Artificial intelligence began as “expert systems,” meaning rules created by experts were computerized for clinical decision support in the medical field. An example of this was the early MYCIN project that made recommendations regarding infectious diseases and choice of antibiotics.²⁰ The project ultimately failed for multiple reasons, but it should be noted that this initiative preceded personal computers, laptops, apps, and the Internet.

We have devoted chapters on image analytics (computer vision) and text mining as significant components of AI. This field can be characterized as narrow and general AI. Narrow AI functions as a narrow task, for example, language translation with Google Translate or evaluating a retinal image. General (strong) AI implies the technology thinks independently, like a human. We have not reached general AI at this point.

Machine learning is a subset of AI and pertains primarily to supervised and unsupervised learning using older statistical algorithms, such as linear regression, or newer ones, such as random forest. Machine learning focuses mainly on predictive analytics. This is discussed in much more detail in Chapter 4 on modeling.

[Figure 1.2 shows the relationship between AI, machine, and deep learning. Many authorities would show this Venn diagram as shared by both the data science and computer science fields.](#content0012.xhtml)

In this textbook, we will discuss machine learning and predictive analytics. Machine learning (ML) is commonly organized into three types:

•Supervised learning . The ML model is trained on labeled data (the outcome is known) and aims to predict an outcome based on predictive variables. This is a classification model if the outcome is categorical (e.g., cancer, benign, email spam, credit card fraud). If the outcome is numerical (e.g., length of stay in a hospital - in days, percent of customer complaints, percent of defective products manufactured), this is a regression model.

  
![](images/image-KMC7KPI0.png)  

Figure 1.2 Venn diagram of AI, ML, and Deep learning

  

•Unsupervised learning . The ML model is trained on unlabeled data to identify hidden patterns, groups, or clusters in the dataset. Examples include medical image analysis, customer segmentation / clustering, recommendation systems, and identifying different groups of students with similar learning styles.

•Reinforcement learning . This method comes from the gaming industry, where an agent interacts with the environment with associated rewards and penalties to reach a goal. It learns through trial and error. Think about the game Pac-Man. Other examples are personalized medicine, personalized marketing, training robots to interact with their environment, and financial algorithmic trading.

  

#### 1.1.3 Artificial Intelligence and Data Science

  

Up until recently there was only one way to practice data science and that was using a programming language, such as R or Python. This textbook is an example of how no-code data science can cover every major data wrangling, data prep, and machine learning task. No code and low-code options also exist to create AI applications.²¹ AutoML low-code options are also available to perform advanced automated machine learning and visualizations tasks with minimal lines of code. Auto-Sklearn is an open-source AutoML Python library that automates the process of algorithm selection, hyperparameter tuning, and model selection.²² H2O AutoML is an open-source AutoML platform that offers a no-code web interface, making it easier to create machine learning models. It automates algorithm selection, feature generation, hyperparameter tuning, iterative modeling, and model assessment. It provides a user-friendly interface for training and evaluating machine learning models.²³ Several other AutoML packages exist that require coding. Furthermore, AI has been integrated with Python packages and Integrated Development Environments (IDEs), as additional examples of low-code data science.²⁴-²⁵

ChaptGPT is a large language model (LLM) released by OpenAI in November 2022.²⁶ It was trained on massive general content, such as Wikipedia, books, Internet text resources and social media It is an example of “generative ai” which produces text, imagery, audio and synthetic data More details on LLMs and Chatbots is included in Chapter 11. Data analysis can be conducted with LLMs, and early hype suggested that it could replace data scientists. While it is likely that AI generated data science will improve in the future, there is no evidence it will replace data scientists.

Many LLMs allow the user to upload a dataset and then the user enters a prompt in natural language to request a data science task. It can also create a variety of predictive models including performance measures. The output often includes the Python code to show the workflow, so this is another example of low-code data science. Most LLMs will not produce data visualizations, so a user must cut and paste the Python code into an IDE, such as a Jupyter Notebook to see the images.²⁷

A list of possible LLM use-cases is as follows:

•Function as a coding assistant to save time and keystrokes

•Review and summarize literature

•Evaluate genomic data

•Describe and summarize a dataset, discussing the columns and rows

•Use a prompt to determine if there are data challenges such as class imbalance, multicollinearity, outliers, and missing data

•Use a prompt to solve data challenges and report the rationale

•Use a prompt to discuss strengths and weaknesses of the data

A list of limitations and precautions is as follows:

•Plausible but incorrect results may occur, also known as “hallucinations.”

•Results that may disagree with those run on another platform. The LLMs will not automatically perform pre-processing. That requires a human prompt.

•Automation bias where someone new to data science will not critically analyze the results

•Data bias due to the presence of systematic errors or prejudices in a dataset that can lead to inaccurate or unfair outcomes

•Lack of reasoning, intuition and common sense

•Lack of creativity

•Lack of oversight. A human must be in the loop.

  

#### 1.1.4 Foundations and Frontiers: Integrating DMBoK Practices with Data Science

  

The Data Management Body of Knowledge (DMBoK) offers a comprehensive framework for effective data management in organizations, encompassing 11 core areas, which are Data Governance, Data Architecture, Data Modeling and Design, Data Storage and Operations, Data Security and Privacy, Data Integration and Interoperability, Document and Content Management, Reference and Master Data Management, Metadata Management, Data Quality Management, and Big Data and Analytics. Data science uses statistical and computational methods to derive insights. Integrating DMBoK with the data science process ensures data quality, context understanding, and compliance with privacy standards. This ensures accurate and reliable analyses rooted in solid data management practices.²⁸

The Data Management Body of Knowledge (DMBoK) and data science, while related, serve different primary functions, and their overlap is mainly in the domain of ensuring that data is ready and optimized for analysis.

Purpose:

•DMBoK: Focuses on providing guidelines for the management of data throughout its lifecycle, ensuring data quality, privacy, security, and availability. It’s about laying the foundation and creating an environment where data can be efficiently used. ²⁹

•Data Science: Concentrates on analyzing data to derive insights. It utilizes various statistical, machine learning, and computational techniques to study data and make predictions or decisions. ³⁰

Overlap Areas:

•Data Quality: Before any data science activity, it’s imperative that the data is clean, accurate, and relevant. DMBoK’s guidelines can be instrumental in ensuring this.

•Data Governance and Privacy: DMBoK’s focus on governance and privacy is crucial for data scientists, especially when dealing with personal or sensitive information.

•Data Architecture & Modeling: The structure and design of databases impact how easily data scientists can pull and manipulate data.

•Metadata Management: Understanding metadata can be key for data scientists to comprehend the context of the data they are working with. DMBoK’s guidelines can be instrumental in ensuring this.

•Data Integration: Before analysis, data often needs to be integrated from various sources, an area DMBoK covers.

Distinct Areas:

•Techniques like machine learning, deep learning, predictive modeling, etc., which are core to data science, don’t fall under DMBoK’s purview.

•Conversely, areas like Document and Content Management, or Data Storage and Operations, which are in DMBoK, might not be directly relevant to a data scientist’s everyday tasks but are essential for data infrastructure.

In summary, DMBoK sets the stage for data science activities. It ensures that data is well-curated, structured, integrated, and governed. While they have overlapping concerns about data quality and infrastructure, DMBoK is broader in terms of data management, whereas data science delves deeper into analysis and insight generation.

  

#### 1.1.5 Statistical Foundations and Predictive Frontiers: A Data Voyage

  

Let’s use the analogy of a car’s large windshield and small rear-view mirror to compare statistics vs. Business intelligence (BI) vs. data science / predictive analytics:

Statistics:

•Rear View Mirror: Statistics can be seen as the “rear view mirror” of this analogy. It looks at data from the past and uses mathematical techniques to summarize, analyze, and interpret that data. Much like how a rear-view mirror provides information on where you’ve been, statistics provide a comprehensive look at what has happened. ³¹

Business Intelligence (BI):

•Rear View Mirror, but a bit Wider: BI expands on the basic insights given by statistics. While still mostly looking at the past, it gives a broader view by combining data from different sources, often in real-time, to provide actionable insights. Imagine the rear-view mirror showing not just the road behind, but also a bit of the landscape and conditions. It helps companies understand their performance, sales, customer behavior, and more. ³¹

  

Data Science / Predictive Analytics:

•Windshield Looking Forward: Data science and predictive analytics are like the large windshield of a car which provides a glimpse of what has occurred, with greater insights into what is likely to occur in the future. They try to foresee future events by leveraging historical data, algorithms, machine learning models, and other tools. Like a driver looking through the windshield and anticipating the curves, obstacles, and conditions ahead, data science and predictive analytics help businesses and researchers anticipate future events, opportunities and challenges. ³²

In summary, while statistics and BI largely focus on understanding and interpreting past data, data science, especially predictive analytics, looks ahead and tries to predict the future. All three are crucial; just as both the rear-view mirror and windshield are essential for a driver to navigate the road safely.

  

#### 1.1.6 The 8-Step Data Science DISCOVER Process

  

  

KEY POINT: Many different acronyms and step charts have been created for the Data Science process. We have created our own process, as shown in Figure 1.3, which we call the DISCOVER process. We use DISCOVER as a word and an acronym for the eight steps in the no-code data science process, as defined in Figure 1.3. Any great methodology, such as Data Science, needs a stepwise process that is robust, detailed, reliable, and repeatable. It is also worth noting that this is an interactive process and not necessarily a strict linear process. Process repeatability can only be achieved with clearly stated specifics for each of the data science process steps, which is the purpose of this book.

  

  

Our 8-step DISCOVER process will be supplemented with more details in later chapters to include the required activities to unlock the power of your data.

Data Science DISCOVER Process Step 1: Define Research questions, Problem, and Goals. Data Science project success does not happen by accident. Their success requires adherence to rigorous and disciplined best practices at every step in the process. In the appropriate chapters of this book, these best practice details will be provided. A summary of all best practices will be listed in the Appendix. Listed below are examples of “Define Research questions, Problem, and Goals for the project”: Step 1, with more details listed below:

1\. What business, customer, clinical, or public health problem are you trying to solve?

2\. What research questions should this project answer?

3\. What are your expected project goals and deliverables?

4\. How will this project create value, benefit patients, customers, or organizations, and/or improve the decision-making processes for healthcare and other professionals?

5\. What is the scope and purpose of the study?

6\. What is the economic impact of this project?

7\. Which metric(s) will be used to define success for this project?

8\. How will you ensure that ethical, fair, and bias-free analysis will not benefit one population group over another?

9\. What are the known project limitations?

10\. Which domain experts, clinical experts, and other resources are required to ensure the correct interpretation of the project results? ³³ - ³⁵

It should be noted that the data science process can also be shown as a circular or iterative process. A circular representation emphasizes the iterative nature of data science, where the steps are not strictly sequential but can be revisited and refined based on insights gained from the analysis. It highlights the feedback loop between different stages, allowing for continuous improvement and refinement of the analysis. In the next chapter, we show a version of our 8-step DISCOVER process that displays many of the possible iterations and feedback loops present between data science process steps.

  

#### 1.1.7 The 3 Levels of AI for Healthcare

  

AI is currently being used in e-commerce, healthcare, finance, self-driving cars, recommender systems and in so many different areas. In this section we explore different levels of AI applications for healthcare. Figure 1.4 displays some alternate definitions of the “AI” acronym for healthcare with some examples for each of the three levels of AI. AI is typically defined as general intelligence and narrow intelligence systems.

  
![](images/image-HWVM5ZAO.jpg)  

Figure 1.3 The 8-Step Data Science DISCOVER process

  

As shown in Figure 1.4, we define three levels of AI that the Data Science process can offer to benefit healthcare professionals and their patients, as described below.

  

1.1.7.1. Actionable Insights (AI Level 1)

  

Some refer to this level as “turning data into actionable insights with machine learning.” ³⁶ These insights are based on robust predictions that the data science process can provide if it has access to a larger data set from which the algorithms can be trained. Such insights can include soliciting and analyzing health risk factors to predict illnesses and diseases. How is this different from what happens in the current healthcare process? Today, every new doctor or clinic we visit requires that we fill out a health survey that asks certain health-related lifestyle questions, current symptoms, current medical issues, medication history, personal health history, and family health history questions. The answers to these questions are usually reviewed by an individual doctor who factors our responses to those questions into their plan for testing, diagnosis, treatment, and care.

The opportunity for AI applications at this level of the patient survey stage is as great as it is underutilized. If the survey questions were aligned with a national database that included the responses to such questions and the verified patient diagnosis, a learning algorithm could be created to predict outcomes within a specified degree of accuracy. We refer to such AI as Actionable Insights about health risks extracted from large national databases. Such insights are actionable since they can create a general risk assessment of a patient before collecting data from a personal diagnosis, lab tests, and vital sign checks.

A great example of this level of AI is the automated ML-driven clinical mortality risk scoring framework called AutoScore.³⁷ AutoScore was trained on almost 45,000 patient admission encounters in the ICU between 2001 and 2012. A software package in R was also developed to demonstrate and share this method. The method showed high-performance levels compared to more complex methods intended to predict which patients were at the most risk of experiencing adverse events or worsening health conditions. This method and study reported various study limitations. Still, it offers hope that a real-time mortality risk scoring system could be created and linked to an electronic health record system. This method’s mortality risk score may provide an early warning system for high-risk patients that may avoid adverse events. This Level 1 of AI is also applicable to any other sector and industry outside of healthcare.

  

1.1.7.2. Augmented Intelligence (AI Level 2)

  

This level of artificial intelligence is deemed to be of a high enough level of accuracy that it can be used as a serious and silent second opinion for healthcare professionals. This term has other commonly used synonyms such as Intelligence Amplification, machine augmented intelligence and other terms.³⁸ The human still makes the final decision for the diagnosis or plan of care. Still, the AI model should be taken seriously if trained on a large database, and the predictive model offers high model accuracy levels. If the large or national database includes the effectiveness of specific care plans for illnesses and diseases, a learning algorithm could recommend such steps for patients that match the same criteria.

  
![](images/image-8Y00ZC51.jpg)  

Figure 1.4 The three levels of AI for Healthcare

  

An example of augmented intelligence would be the application of a real-time AI algorithm trained on an extensive national database of home healthcare patients to determine the best plans of care to improve the Activity of Daily Living (ADL) scores for patients with a similar case mix. The AI algorithm would offer the healthcare professional recommendations, but the human would make the final decision. As mentioned, if the AI model reports very high prediction accuracy levels, the AI recommendations should be taken more seriously.

Another potential augmented intelligence example would be the development of a trained algorithm that factors in all treatment information, medication, ICD-10 codes, lab data, vitals data, and real-time 24/7 telemetry data on many acute care heart disease patients under the care of a cardiologist. Suppose such an algorithm were improved to produce high accuracy levels for health condition predictions, responses to various plans of care, and medications. In that case, it should also be considered a reliable real-time advisor for the cardiologist who will make all final decisions. This Level 2 of AI is also applicable to any other sector and industry outside of healthcare.

  

1.1.7.3 Artificial Intelligence (AI Level 3)

  

This highest level of AI is reserved for those healthcare algorithms that perform at least as competitively as a trained healthcare professional. The FDA has approved over 520 medical devices that are ML/AI-enabled. 521 of these devices are listed on the FDA website with their note that the list is incomplete.³⁹ Figure 1.5 shows a Pareto chart listing the main uses for these medical devices that they have approved. The top four areas of 16 total sites make up 91.7% of all areas of ML/AI-enabled devices as listed here: Radiology (75.2%, Cardiovascular (10.9%), Hematology (2.9%), and Neurology (2.7%).

The FDA states that “One of the greatest potential benefits of ML resides in its ability to create new and important insights from the vast amount of data generated during the delivery of health care every day.” ³⁹ None of the successful applications of ML and AI in healthcare would have been possible without adherence to a rigorous data science process as described in Figure 1.4 and throughout this book. This Level 3 of AI is also applicable to any other sector and industry outside of healthcare.

  

1.2 WHAT DO DATA SCIENTISTS DO?

  

  

Statistics, mathematics, and programming are the cornerstones of data science, but there are many other essential requirements as listed below. Keep in mind that this skills list and priorities may vary based on the sector and company.

The fundamental skill sets and expertise required for data scientists are:

  
![](images/image-O3AM4EKV.jpg)  

Figure 1.5 The types of ML/AI medical devices that are FDA approved

  

•Mathematics and statistics

•Domain expertise, e.g., business, manufacturing, service, healthcare, etc.

•Programming in multiple languages: R, Python, SQL, etc.

•Database management and data warehousing

•Predictive modeling and descriptive statistics

•Machine learning and artificial intelligence

•Big data

•Communication and presentation (soft skills or eSkills) ⁴⁰

[Figure 1.6 shows the average time spent by data scientists on different activities based on a 2022 survey. Based on this survey, only 27% of the time is spent on modeling, whereas 67% of the time is spent on data preparation, cleaning, visualization, and reporting.⁴¹ It bears noting that only 5% of survey respondents were in the healthcare sector, so these results may differ for healthcare.](#content0018.xhtml)

Very few data scientists have all these skills at the beginning of their careers. Most require additional experience in a specific sector to become comfortable with the technology and the domain. Data scientists are involved in multiple processes, from finding and curating the data to building, deploying, and maintaining the models, and presenting the progress. Data engineers are considered different from data scientists. A data engineer has some of the skills of a data scientist, but the emphasis is on advanced programming and systems development. Data engineers create data pipelines and software solutions for data, whereas data scientists are more likely to devote more time to the statistics,analytics required, and modeling. ⁴² In any sector, there are data professionals in addition to data scientists and engineers, as displayed in Table 1.2. ⁴³

  
![](images/image-4M1Z90V5.png)  

Figure 1.6 Time spent by data scientists ⁴¹

  

1.3 WHY LEARN DATA SCIENCE?

  

  

Because we live and work in a data and tech-driven society, data literacy is becoming required for many domains. With the increasing use of machine learning, natural language processing, and artificial intelligence, the average professional must understand where it fits into their domain and how it will affect the future requirements of their profession.⁴⁴ Another benefit of understanding data science is applying the knowledge to better understand analytical research papers and scientific publications. It is common now to see predictive analytics based on machine learning algorithms instead of statistical methods in publications, so it is important to understand these methodologies. In medicine, the convergence of genomics and traditional medicine creates an increased need to understand newer approaches, such as unsupervised learning, and various deep learning strategies. In the manufacturing sector, data science enables manufacturers to optimize quality, predict machine breakdown events, manage inventories, and manage complex supply chains.⁴⁵ In the service sectors, data science enables improved customer insights that can improve the customer experience, improve demand forecasting, analyze customer sentiment analysis, and detect fraud. Learning data science has many career-related benefits due to the high demand for data science skills in many different industries.⁴⁶

  

1.4 DATA SCIENCE EDUCATIONAL CHALLENGES

  

  

Data science is challenging since you must simultaneously learn various domains such as mathematics, statistics, a programming language, and computer science as is usually true with a master’s level data science program. Several areas of data science are challenging for all data science students, such as understanding neural networks, image, and text analysis. Programming expertise is strongly recommended for anyone who will spend the majority of their time doing data science. However, many people desire to be proficient but not necessarily an expert in the field of data science. For such individuals, tools such as Orange and JASP make the data science learning journey easier to sign up for. Learning basic programming is not difficult for some individuals but it is a major roadblock for many. Programming complex neural networks such as convolutional neural networks or transformer-based language models can be challenging for experienced coders.⁴⁷ Furthermore, finding data of sufficient volume and quality can be difficult and frequently requires individuals trained in data science.

  

Table 1.2 Data Professionals

  

 
| Title || Job Description |
| --- | --- |
| Data Scientist || A jack of all trades. They offer insights into the best solutions for a specific project while uncovering larger patterns and trends in the data. They also research and develop new algorithms and approaches. |
| Data Analyst || Responsible for different tasks such as visualizing, transforming, and manipulating the data. Sometimes they’re also responsible for web analytics tracking and A/B testing analysis. |
| Data Engineer || Responsible for designing, building, and maintaining data pipelines. They need to test ecosystems for businesses and prepare them for data scientists to run their algorithms. |
| Data Architect || Data architects share common responsibilities with data engineers. They both need to ensure the data is well-formatted and accessible for data scientists and analysts and improve the data pipelines’ performance. |
| Data Storyteller || A data storyteller needs to take data, simplify it to focus on a specific aspect of the data, analyze its behavior and then use their insights to create a compelling story that helps people (fellow teammates, customers, etc.) better understand a given phenomenon. |
| Machine Learning Scientist || Most often, when you see the term “scientist” in a job role, it indicates this job role requires researching to develop new algorithms and insights. In this case, a machine learning scientist researches new approaches to data manipulation to design new algorithms. |
| Machine Learning Engineer || In addition to designing and building machine learning systems, machine learning engineers must run tests (such as A/B tests) while monitoring the different systems’ performance and functionality. |
| Business Intelligence Developer || They design strategies that allow businesses to find the information they need to make decisions quickly and efficiently. |

  

1.5 WHY DID WE CREATE THIS TEXTBOOK?

  

  

This textbook was originally drafted as training materials to teach data science workshops for clinicians in the US, as a function of the Medical Intelligence Society. This society promotes data science, machine learning, and artificial intelligence in the healthcare domain.⁴⁸ Since then, the book has been supplemented with training materials and data analysis examples that are now applicable to any industry. Our continued workshops walk participants through the book in an interactive manner with the aim to increase interest and competency in applied data science by using open-source software and performing analytical exercises on datasets from multiple industries. We also intend to offer certification levels for professionals interested in documenting their knowledge and application skills in no-code data science techniques. In this book, multiple links to external resources have been added to provide additional useful information. Similarly, valuable sources of datasets and additional statistical and machine-learning concepts have been added to this book. We hope to create an army of no-code data scientists who can maximize the power of open-source software to learn basic, intermediate, and advanced levels of applied data science with a limited need for higher math or statistical knowledge. We put a high priority on teaching professionals how to correctly create and interpret all of their data visualizations and analysis work while being able to identify and recommend the next logical analysis steps. A chart or analysis result should never be added to a presentation or research report without the addition of clear interpretation comments. You cannot build trust in your analysis and predictive models with stakeholders and customers unless you learn to be a master storyteller concerning your data and analysis. Such storytelling often requires the art of analogous thinking and analogous storytelling in order to make complex topics and analysis results relatable to all stakeholders.

  

1.6 WHO IS THE TARGET AUDIENCE?

  

  

This book is designed for professionals eager to deepen their knowledge in advanced data analysis and visualization, particularly those with a keen interest in predictive analytics for tabular data, image interpretation, and text mining.

This book is also intended for Lean Six Sigma (LSS) professionals who want to expand their problem-solving toolbox to include more advanced and predictive modeling techniques. Datasets from multiple domains are used in this book as we explain how to analyze those datasets with intuitive tools such as Orange and JASP.

  

1.7 WHY USE OPEN-SOURCE SOFTWARE?

  

  

To quote Woody Guthrie, “Any fool can make something complicated. It takes a genius to make it simple.” ⁴⁹ This applies to the two main software platforms we use throughout this book: Orange and JASP. Many other no-code data science platforms were investigated, such as RapidMiner, BigML, WEKA, KNIME, BlueSky Statistics, H2O.ai, Microsoft Azure ML Studio, Deep Talk, MonkeyLearn, Create ML, DataRobot, Obviously AI, and Google Cloud ML. In Table 1.3, the authors used various datasets to compare their experiences with other free educational data science platforms. Most professionals will not be able to fully embrace a programming language because it is a steep learning hill to climb. They will also forget their coding skills unless they practice it frequently (like any language). This is why Orange and JASP were chosen as alternatives to a standard programming language.⁵⁰ We will also use BlueSky Statistics when there is a concept or function we want to demonstrate that is not available in Orange or JASP. Some would consider these programs as an example of “citizen data science” and the “democratization” of data science. A citizen data scientist is a “person who works in fields other than statistics, or analytics, yet creates or generates models that incorporate predictive or prescriptive analytics.” ⁵¹ Orange and JASP support the “no code AI movement” as described in a 2022 New York Times article. ⁵²

Orange is based on the programming language Python, which is the computation engine working in the background. Orange is a free program from the University of Ljubljana, Slovenia. It is used by more than 300 universities worldwide and two medical schools in the US. The program continues to be updated and expanded.

  

Table 1.3 Educational data science platforms

  
![](images/image-SLSUSYSL.jpg)  

Orange was chosen as the main analysis tool for this book for several reasons. It is a free program available for all operating systems. It is fast and intuitive. Orange uses visual operators (widgets); some refer to this as “visual programming,” similar to other data science software programs such as KNIME and RapidMiner. In Orange, widgets are used as computational units to read, process, and visualize data. Widgets can be connected to pass the information on to the following data processing activity. The platform can perform many data preparation tasks, exploratory data analytical methods, supervised and unsupervised learning, image analysis, and text mining. There are many user-friendly shortcuts to save time, as pointed out in each chapter. For example, you can run multiple algorithms simultaneously and compare results. You can toggle between training and test data results with no additional steps. Orange workflows can be saved as an .ows file in the documents folder to share the workflow between faculty,students, researchers, and professionals. Analysis results can also be saved as an annotated report. Most algorithms have hyperparameters that can be optimized. Optimized predictive models can be saved and uploaded for use with new data. Orange was designed as an educational tool and has been used as the analytical program in published articles in the medical literature.⁵³-⁵⁴

Several limitations should be noted. Data visualization images can be saved as a .png file, but they are not APA quality. Orange does do image classification but cannot perform image segmentation. Orange offers several neural nets but does not include recurrent neural networks (RNNs), nor generative adversarial networks (GANs). Orange was not necessarily intended for “big data” but some have reported successes with analyzing millions of customer records with Orange.⁵⁵ The Orange team is also working to integrate Dask into Orange. Dask is a flexible library for parallel computing in Python to simplify the analysis of Big Data in Orange.⁵⁶

  

1.8 ORANGE DATA MINING

  

  

Orange uses visual operators (widgets). It is therefore considered visual programming instead of the tedious coding required when using the Python and R programming languages. You drag widgets from the left menu into the center canvas to create a machine-learning pipeline or workflow to complete a data preprocessing, analysis, or visualization task. Figure 1.7 shows the menu on the left and the analysis workflow in the center.

  
![](images/image-K5S03RI3.png)  

Figure 1.7 Orange workflow example

  

  

KEY POINT: Orange uses visual programming to connect the appropriate widgets with each other to create an analytical workflow. Each Orange widget is a specific analytical step in the data science process. Orange has over 200 widgets that offer a wide variety of analysis options.

  

  

#### 1.8.1 Orange General Information

  

1\. The menus are located on the left in a column which are collections of computation widgets. They logically start with data manipulation options. There is also a horizontal menu bar at the top with the following options: file, edit, view, window, widget, options, and help. Select options >> Add ons, and add as many additional modules as you like which will then be added to the vertical column of widget modules on the left. If you go to Help >> Documentation, you will find many valuable tabs, including widget details, sample workflows, screenshot examples of analysis outputs, and more. Furthermore, if there is an update available in the menu features, it will appear in the add-on list, and you will have the option to install the update by clicking on the update and restarting Orange. The Text Mining and Image Analytics add-ons will be covered later in the textbook. The choices are mentioned below in section 7 - Add ons.

2\. Acceptable file formats to upload include csv, xlsx, and tab files

3\. When Orange is first opened, users have these options:

a. New, Open, and Recent - select New

b. Video tutorials - view several

c. Get started - good starting point

d. Examples - see examples of standard workflow for a variety of tasks

e. Documentation - you will find more valuable details there ⁵⁷

f. We recommend starting with the video on widgets and channels (widget connectors)

  
![](images/image-B7650WA7.png)  

Getting Started with Orange Video (Orange)

  

Orange comes with multiple datasets (60+) that can be accessed from within the Dataset widget. Drag the Dataset widget into the canvas and double-click. Review the available datasets. If you see one you would like to explore, double-click on it, and it will be automatically loaded. The target/outcome is color-coded to determine if it can be used for classification vs. regression, etc. It also informs you of the domain and may include its source at the bottom. See Figure 1.8.

  
![](images/image-0GMKTODV.png)  

Figure 1.8 Dataset widget

  

4\. You can also upload your own data into an Orange workflow. Drag the File widget to the canvas and double-click on it to open the widget options where you can click on the folder icon at the top to select the data you may intend to import. You can also download data from the web or Google Sheets using the URL option in the widget. There is a SQL widget to import data from a database. See Figure 1.9 shows a simple workflow using the File widget to create various data visualizations.

  
![](images/image-X5HFICXN.jpg)  

Figure 1.9 File widget connected to four other widgets

  

[Figure 1.10 displays an opened File widget with numbered functions which are described below the figure.](#content0025.xhtml)

1\. Drop down menu to select from 6 preloaded .tab files to include heart disease

2\. Folder search to find your own files to upload

3\. Tool to upload files from URLs

4\. Select data type. The default is to automatically detect data type

5\. General information about the dataset: number of rows (instances), number of features (columns), type of model with target defined, and missing value counts

6\. Type of data: categorical or numeric

7\. Role: Any feature can be changed to target, skip, or meta

8\. Values: for example, ECG is normal, left vent hypertrophy or ST-T abnormality

9\. Apply button. After any change, be sure to select “Apply”

10\. The question icon is linked to the Help menu

  
![](images/image-F8SMH0LO.png)  

Figure 1.10 File widget

  

5\. Educational options

a. There are multiple YouTube videos on the Orange website and an Orange YouTube channel with 38 videos. ⁵⁸

b. There is a general documentation page that explains all widget functions. It is highly recommended that readers visit this page! ⁵⁹

c. There is a widget catalog at the bottom of the Orange home page explaining each widget. ⁶⁰ This is an excellent place to visit if you want to understand, e.g., how the test and score widget works.

d. There is a blog for new developments on the home page.

e. There are workflow examples available.

6\. Help options:

a. Right-click any widget, and there is a Help option. This is generally the same information as found in the widget catalog. This is strongly recommended reading for those new to Orange.

b. Help is also available by left-clicking on any widget, and it is shown as a “?” mark on the bottom left of any widget information box.

c. Check out the Help menu at the top of the website page.

d. Access Stack Exchange for software questions. ⁶¹

e. The GitHub site is primarily for developers to report bugs or to ask for new features. ⁶²

7\. Add-on modules are found under the Options tab at the top menu

a. Associate - for analyzing data with association rules

b. Bioinformatics - for analyzing bioinformatics or genomic data

c. Educational - extra features such as using Google Sheets, polynomial regression and classification, pie charts, and creating random data

d. Explain - explain classification models with SHAP and feature importance widgets

e. Geo - for analyzing and creating geolocation data and maps

f. Image analytics - for analyzing images

g. Network - for analysis of network data

h. Prototypes - bioinformatics

i. Single-cell - bioinformatics

j. Spectroscopy - for visualizing spectral data

k. Text - for analyzing text

l. Textable - more text mining

m. Survival Analysis - One of the primary objectives of survival analysis is to estimate the survival probability from observed survival times of different patients, customer churn analysis, machine failures, etc.

n. World Happiness - it is intended for retrieving socio-economic data from global databases

o. Time series - for analyzing longitudinal data and forecasting time series data

8\. You can save your workflow as an Orange .ows file and share it with others. You can also download data as a CSV file by connecting to the Save Data widget

9\. You can create a “report” of your current workflow and annotate it to share it with others. (See the report option found in the lower left of most widgets). Save as an html, PDF, or .report file.

10\. When you left-click the right side of a widget and drag it to the right, it launches a widget search engine. See Figure 1.11 . Also, you can right-click on a connector line and select “insert widget.” You can also right-click the blank canvas and choose a widget to add.

11\. A small menu with six icons in gray boxes are at the bottom of the left vertical menu column. i The small “i” opens a dialog where you can annotate and describe your workflow. The hashtag “#” icon automatically aligns your widgets to a grid. The large “T” icon allows you to add text to your workflow, and the arrow icon places arrows in the workflow. The pause “||” icon will stop the signal propagation between the widgets. The help “?” icon will open a small window with helpful tips,

  
![](images/image-7I62VM09.jpg)  

Figure 1.11 Widget search option

  

1.9 JASP STATS PACKAGE

  

  

#### 1.9.1 Introduction

  

The acronym JASP is derived from Jeffrey’s Amazing Statistics Program, named after Sir Harold Jeffrey, a famous British statistician. The University of Amsterdam in the Netherlands created and maintains this stats program. A JASP desktop and a cloud option are available for Windows, Mac, and Linux operating systems. More than 250 universities use this program in 63 countries. JASP will accept Comma Separated Values (.csv), Plain text files (.txt), SPSS (.sav, but not .zsav, .por), and Open Document Spreadsheet (.ods). The program is updated frequently. ⁶³-⁶⁴

  

#### 1.9.2 JASP Unique Features

  

JASP has several unique features:

•JASP includes the Bayesian and frequentist (classical) statistical approaches.

•JASP is part of the Open Science Framework (OSF), so stats results can be shared with collaborators.

•JASP does not save just the dataset; it saves the dataset and its associated analyses.

•JASP has multiple plug-in modules as outlined in the next section.

•Tables and plots are APA quality.

•JASP can connect to various databases.

[Figure 1.12 displays the main page with the top menu once a file has been uploaded and selected.](#content0029.xhtml)

  

#### 1.9.3 JASP Organization

  

The top menu organization is bulleted below. In appropriate chapters, we will include screenshots of JASP features:

•Descriptives (descriptive statistics)

  

![](images/image-TEMD15Y1.jpg)Statistics: Missing, Mode, Median, Mean, Quartiles, Percentiles, Skewness, Kurtosis, Standard Error, Variance, Standard Deviation, Kurtosis, Shapiro-Wilk test, Sum, Minimum, and Maximum

  

![](images/image-TEMD15Y1.jpg)Basic plots: Distribution, Correlation, Q-Q, Pie, and Dot plots

  

![](images/image-TEMD15Y1.jpg)Customizable plots: Box, Violin, and Heatmap

  

![](images/image-TEMD15Y1.jpg)Tables: Frequency and Stem and Leaf tables

•T-tests: Classical (Independent, Paired, One sample) Bayesian (Independent, Paired, One sample)

•ANOVA: Classical (ANOVA, Repeated Measures ANOVA, ANCOVA, MANCOVA) Bayesian (ANOVA, Repeated Measures, ANCOVA)

•Mixed Models: Classical (Linear Mixed, General Linear Mixed Model) Bayesian (Linear Mixed, General Linear Mixed Model)

•Regression: Classical (Correlation, Linear and Logistic Regression, and Generalized Linear Model) Bayesian (Correlation, Linear Regression)

•Frequencies: Classical (Binomial, Multinomial, Contingency Tables, Log Linear Regression) Bayesian (Binomial, Multinomial, Contingency Tables, Log Linear Regression, A/B Test)

•Factor: Principal Component Analysis, Exploratory and Confirmatory Factor Analysis

•Add-on modules :

  

![](images/image-TEMD15Y1.jpg)Distributions: Extensive menu of distribution types

  

![](images/image-TEMD15Y1.jpg)Machine Learning

  

![](images/image-IMR0T3RY.jpg)Classification: Boosting, Decision Tree, K-Nearest Neighbor, Neural Network, Random Forest, Regularized Linear, Linear Discriminant, and Support Vector Machine

  

![](images/image-IMR0T3RY.jpg)Regression: Boosting, Decision Tree, K-Nearest Neighbor, Neural Network, Random Forest, Regularized Linear, Linear Discriminant, and Support Vector Machine

  

![](images/image-IMR0T3RY.jpg)Unsupervised Learning: Density Based, Fuzzy C-Based, Hierarchical, Neighborhood Based, and Random Forest

  

![](images/image-TEMD15Y1.jpg)Network: Graphs

  

![](images/image-TEMD15Y1.jpg)Summary Statistics: Bayesian T-Tests, Regression, Frequencies, and Other

  

![](images/image-TEMD15Y1.jpg)Learn Bayes: Binary Classification, Counts, The Problem of Points, and Buffon‘s Needle

  

![](images/image-TEMD15Y1.jpg)Prophet: Time-Series Analysis

  

![](images/image-TEMD15Y1.jpg)Quality Control: Measurement Systems Analysis, Control Charts, Capability Study, and DOE

  
![](images/image-QQ8ZDRCD.png)  

Figure 1.12 JASP Main screen with Menu at the top

  

![](images/image-TEMD15Y1.jpg)R (Beta) programming: Enter R Code

  

![](images/image-TEMD15Y1.jpg)Others: Meta-Analysis

  

#### 1.9.4 JASP limitations

  

JASP has several know limitations that the originators are working on:

•JASP lacks a true data editor but does have a drag and drop filter to perform basic mathematical functions on the data. New data editor planned for 2023.

•JASP is limited to running one model at a time.

•Users cannot toggle between training and test results.

  

1.9.5 Orange vs JASP

  

Table 1.4 compares the major features of both programs.

  

1.10 PUTTING KNOWLEDGE INTO PRACTICE

  

  

1.10.1 Exercise

  

1\. View examples of frequently used workflow options on the Orange website that can either be studied or downloaded and applied to an analysis project. ⁶⁵

2\. In the top Orange menu, select Options, then add-ons, and check the boxes next to the associate, image analytics, text, network, and explain modules. Restart Orange so the new modules are uploaded.

3\. View the video on widgets and channels (widget connectors) using the QR code in this chapter.

4\. Review the pre-loaded datasets found in the File and Dataset widgets,

5\. Exercise:

a. Upload your dataset using the File or Dataset widget and connect it to a Data Table widget, then open and explore your data. Left-click the numerical column header, and you will see it sort the column data in ascending or descending order. Create a simple workflow using the File widget, such as connecting the Distribution widget to it to create a simple histogram. Click on the help file on your newly added widget to explore its features and options. Then name this workflow and save it as an .ows file in your documents folder.

b. Describe one unique potential application for each of the three levels of AI for healthcare mentioned in this chapter.

  

Table 1.4 Feature comparison of Orange vs JASP

  
![](images/image-J4ZD2V5S.jpg)

  

1.10.2 Maturity Levels

  

When integrating a no-code data science approach with DMBoK and considering the differences between data science, BI, and statistics, we can imagine how companies at different maturity levels might fare. Here are three scenarios for low, mid, and high-end maturity companies:

1\. Low-End Maturity: “The Budding Boutique.”

Scenario: A small, local retail business has recently begun its digital transformation. They’ve been manually keeping sales records in spreadsheets and have just started using BI tools to visualize monthly sales trends.

a. Data science (DS): They’re unaware of the vast potential of DS but are curious about predictive analytics for inventory forecasting.

b. Business Intelligence (BI): They use simple BI dashboards that display monthly sales, highest selling items, and customer frequencies.

c. Statistics: Only basic statistics like mean, median, and mode are employed to understand monthly sales and customer patterns

d. Integration with DMBoK: They’ve begun realizing the importance of organized data management, especially in reference to master data management for their products. They’ve heard of DMBoK but haven’t fully grasped its scope.

e. 8-Step DS Process: They’re taking the first steps by defining the problem statement and acquiring data, but their journey is mostly exploratory at this stage.

2\. Mid-End Maturity: “The Growing Enterprise.”

Scenario: A regional e-commerce platform has seen significant growth over the years. They utilize BI tools actively and have a dedicated data team, but they lack formal processes.

a. DS: The company has begun to experiment with machine learning for product recommendations and customer behavior prediction.

b. BI: Their BI dashboards are advanced, with metrics on website traffic, conversion rates, and cart abandonment rates.

c. Statistics: Apart from basic statistics, they use regression analysis to understand sales drivers and A/B testing for website modifications.

d. Integration with DMBoK: They are in the initial phases of implementing DMBoK’s guidelines, particularly data governance, data quality, and metadata management.

e. 8-Step DS Process: Their data team is at the modeling stage, fine-tuning predictive algorithms, but they’re facing challenges in deployment and feedback integration

3\. High-End Maturity: “The Data-Driven Conglomerate.”

Scenario: A multinational corporation with diverse product lines and a significant online presence. They have a mature data department and regularly invest in new technologies.

a. DS: The company uses advanced machine learning and AI for everything from customer service chatbots to supply chain optimization.

b. BI: Sophisticated BI tools provide insights into micro and macro trends, regional sales comparisons, and customer segmentation.

c. Statistics: Advanced statistical techniques, including time series forecasting and multivariate analysis, are being applied.

d. Integration with DMBoK: They’ve fully embraced DMBoK, with a strong emphasis on data security, data integration, and content management. They regularly review and update their practices in line with DMBoK’s evolving guidelines.

e. 8-Step DS Process: Their process is cyclical. Post-deployment, constant feedback is used to refine models. They’ve even integrated real-time data streaming for on-the-go insights and adjustments.

These scenarios should help illustrate the differences in how companies at various maturity stages might approach the integration of no-code data science with DMBoK while distinguishing between DS, BI, and statistics.

  

#### RESOURCES

  

  

1\. Orange discussed on Medium.com : a 5 part series https://medium.com/geekculture/data-science-introduction-to-orange-tool-part-1-bff18bb159a

2\. Hoyt R. Maximizing Orange for Data Science Education. Part I and II https://medium.com/p/1be42362634a

3\. More datasets on https://www.nocodedatascience.net/file-share

a. A list of medical data resources

b. Free data checklist that is useful when exploring a dataset for the first time

c. More datasets to download

4\. Intro to Data Mining with Orange. Zupan and Demsar. Nature https://www.nature.com/articles/s41467-019-12397-x

5\. Supplement your data science knowledge with:

a. Practical Statistics for Data Science - Free eBook https://github.com/ghoshark/E\_Books/blob/master/Practical%20Statistics%20for%20Data%20Scientists.pdf

b. StatQuest is a YouTube based program to teach you simple stats. It is also now a book available on Amazon. https://www.youtube.com/channel/UCtYLUTtgS3k1Fg4y5tAhLbw and https://www.amazon.com/StatQuest-Illustrated-Guide-Machine-Learning/dp/B09ZCKR4H6 A complete list of videos available: https://statquest.org/video-index/

c. 3 Blue 1 Brown is an educational tutorial website that explains a variety of data science concepts more clearly than most. https://www.3blue1brown.com/

d. Data science cheat sheets from KDNuggets on https://www.nocodedatascience.net

e. Statistical Analysis in JASP: A Guide for Students. File-Share site, Chapter 1 folder

  

#### REFERENCES

  

  

[1\. Saha D. How The World Became Data-Driven, And What’s Next \[Internet\]. Forbes. 2020 \[cited 2022 Apr 11\]. Available from: https://www.forbes.com/sites/googlecloud/2020/05/20/how-the-world-became-data-driven-and-whats-next/](#content0010.xhtml)

[2\. Hoyt R, Muenchen R. Data Preparation and Exploration \[Internet\]. 2020. 90 p. Available from: https://books.google.com/books/about/Data\_Preparation\_and\_Exploration.html?hl=&id=EyYKzgEACAAJ](#content0010.xhtml)

[3\. Wikipedia. Data Science. \[Internet\]. \[cited 2022 April 1\] Available from: https://en.wikipedia.org/wiki/Data\_science](#content0010.xhtml)

[4\. El Shatby S. 365 Data Science. 2022 \[cited 2023 Aug 12\]. How to become a data scientist in healthcare? Available from: https://365datascience.com/career-advice/how-to-become-a-data-scientist-in-healthcare/](#content0010.xhtml)

[5\. Knowledge Hut. Data Science in Manufacturing: Applications, Tool, and Future. July 2023. Available from: https://www.knowledgehut.com/blog/data-science/data-science-in-manufacturing](#content0010.xhtml)

[6\. Zharovskikh A. InData Labs. 2022 \[cited 2023 Jul 31\]. AI in service industry: All you need to know. Available from: https://indatalabs.com/blog/ai-in-service-industry](#content0010.xhtml)

[7\. Javaid M, Haleem A, Khan IH, Suman R. Understanding the potential applications of Artificial Intelligence in Agriculture Sector. Advanced Agrochem. 2023 Mar 1;2(1):15–30](#content0010.xhtml)

[8\. Davenport TH, Patil DJ. Data Scientist: The sexiest job of the 21th century. Harvard Business Review \[Internet\]\[cited 2022 April 9\] Available from: https://hbr.org/2012/10/data-scientist-the-sexiest-job-of-the-21st-century](#content0010.xhtml)

[9\. Tukey JW. The future of data analysis. Annals of Math Stats. 1962;33(1):1-67 \[2022 cited April 10\]](#content0011.xhtml)

[10\. Cleveland WS. Data science: an action plan for expanding the technical areas of the field of statistics. Int Stat Rev 2001. 69(1):21-26 \[cited 2022 April 2\]](#content0011.xhtml)

[11\. Internet Live Stats. \[Internet\] Available from: https://www.internetlivestats.com/one-second/#google-band](#content0011.xhtml)

[12\. Krumholz H, Gross C, Blount K. Sea change in open science and data sharing: leadership by industry. Circ Cardiovasc Qual Outcomes 2014; 7(4): 499–504 \[cited 2022 March 28\]](#content0011.xhtml)

[13\. John McCarthy. Wikipedia. \[Internet\]\[cited 2022 Aug 10\] Available from: https://en.wikipedia.org/wiki/John\_McCarthy\_(computer\_scientist)](#content0012.xhtml)

[14\. Hoyt, Robert, and Robert Muenchen. 2019. Introduction to Biomedical Data Science . Lulu.com.](#content0012.xhtml)

[15\. Chang, Anthony C. 2020. Intelligence-Based Medicine: Artificial Intelligence and Human Cognition in Clinical Medicine and Healthcare . Academic Press.](#content0012.xhtml)

[16\. Benjamins, J. W., T. Hendriks, J. Knuuti, L. E. Juarez-Orozco, and P. van der Harst. 2019. “A Primer in Artificial Intelligence in Cardiovascular Medicine.” Netherlands Heart Journal: Monthly Journal of the Netherlands Society of Cardiology and the Netherlands Heart Foundation 27 (9): 392–402.](#content0012.xhtml)

[17\. A Definition of AI: Main Capabilities and Disciplines. European Commission. June 2018.\[Internet\]\[cited 2022 June 10\] Available from: https://ec.europa.eu/digital-single-market/en/news/definition-artificial-intelligence-main-capabilities-and-scientific-disciplines](#content0012.xhtml)

[18\. Kalali Amir, Sarah Richerson, Emilia Ouzunova, Ryan Westphal, and Bradley Miller. 2019. “Chapter 16 - Digital Biomarkers in Clinical Drug Development.” In Handbook of Behavioral Neuroscience , edited by George G. Nomikos and Douglas E. Feltner, 29:229–38. Elsevier.](#content0012.xhtml)

[19\. LeCun Y, Bengio Y, Hinton G. Deep Learning. Nature. 2015;521:436-444](#content0012.xhtml)

[20\. Mycin. Wikipedia. \[Internet\]\[cited : https://en.wikipedia.org/wiki/Mycin](#content0012.xhtml)

[21\. Aiswarya PM. Analytics Insight. 2023 \[cited 2023 Aug 12\]. Top 10 examples of low-code and no-code AI you should know. Available from: https://www.analyticsinsight.net/top-10-examples-of-low-code-and-no-code-ai-you-should-know/](#content0013.xhtml)

[22\. ai.nl \[Internet\]. 2022 \[cited 2023 Aug 9\]. 10 open source AutoML tools that help ML developers accelerate the time taken to get ML models production ready. Available from: https://www.ai.nl/artificial-intelligence/10-open-source-automl-tools/](#content0013.xhtml)

[23\. H2O Open Source AutoML \[Internet\]. \[cited 2023 Aug 9\]. Available from: https://h2o.ai/platform/h2o-automl/](#content0013.xhtml)

[24\. Venturi G. pandas-ai: PandasAI is a Python library that integrates generative artificial intelligence capabilities into Pandas, making dataframes conversational \[Internet\]. Github; \[cited 2023 Aug 9\]. Available from: https://github.com/gventuri/pandas-ai](#content0013.xhtml)

[25\. Jemerov D. The JetBrains Blog. \[cited 2023 Aug 9\]. AI Assistant in JetBrains IDEs. Available from: https://blog.jetbrains.com/idea/2023/06/ai-assistant-in-jetbrains-ides/](#content0013.xhtml)

[26\. OpenAI. \[Internet\]. \[cited 2023 Aug 9\]. Available from: https://openai.com/](#content0013.xhtml)

[27\. ChatGPT for data analysts \[Internet\]. \[cited 2023 Aug 9\]. Available from: https://www.ironhack.com/us/en/blog/chatgpt-for-data-analysts](#content0013.xhtml)

[28\. Khan T. DATAVERSITY. 2022 \[cited 2023 Aug 9\]. What is the Data Management Body of Knowledge (DMBoK)? Available from: https://www.dataversity.net/what-is-the-data-management-body-of-knowledge-dmbok/](#content0014.xhtml)

[29\. Ma L. Azure Data Ninjago & dqops. 2021 \[cited 2023 Aug 9\]. What is Data Management, actually? – DAMA-DMBOK Framework. Available from: https://dataninjago.com/2021/09/15/what-is-data-management-actually-dama-dmbok-framework/](#content0014.xhtml)

[30\. DAMA DMBOK: Chap. 14: Big Data & Data Science https://dama-ny.com/downloads/DAMA\_2018/dama\_nyc\_\_\_sept\_2018\_\_\_dmbok\_big\_data\_\_\_data\_science\_\_\_rja\_handout.pdf](#content0014.xhtml)

[31\. Adams ASB. Optimization Group. 2015 \[cited 2023 Aug 9\]. Historical vs forward-looking research. Available from: https://www.optimizationgroup.com/historical-vs-forward-looking-research/](#content0015.xhtml)

[32\. Taylor S. Corporate Finance Institute. 2021 \[cited 2023 Aug 9\]. Business Intelligence vs. Data science. Available from: https://corporatefinanceinstitute.com/resources/business-intelligence/business-intelligence-vs-data-science/](#content0015.xhtml)

[33\. Punjwani, Shahwaiz. 2022. “Essential Questions to Ask before Starting a Data Science Project.” Towards Data Science. January 7, 2022.Available from: https://towardsdatascience.com/essential-questions-to-ask-before-starting-a-data-science-project-cd633dcd9d55](#content0016.xhtml)

[34\. Lewis, Kate Marie. 2020. “7 Questions You Should Ask Yourself before Starting Any Data Science Project.” Towards Data Science. June 7, 2020. Available from: https://towardsdatascience.com/7-questions-you-should-ask-yourself-before-starting-any-data-science-project-51c29093c641](#content0016.xhtml)

[35\. Hotz, Nick. 2019. “10 Questions to Ask before Starting a Data Science Project.” Data Science Process Alliance. May 20, 2019. Available from: https://www.datascience-pm.com/10-questions-to-ask-before-starting-a-data-science-project/](#content0016.xhtml)

[36\. Rahal A. CIO. TechTarget; 2021 \[cited 2023 Aug 10\]. Turning data into actionable insights with machine learning. Available from: https://www.techtarget.com/searchcio/post/Turning-data-into-actionable-insights-with-machine-learning](#content0017.xhtml)

[37\. Xie, Feng, Bibhas Chakraborty, Marcus Eng Hock Ong, Benjamin Alan Goldstein, and Nan Liu. 2020. “AutoScore: A Machine Learning-Based Automatic Clinical Score Generator and Its Application to Mortality Prediction Using Electronic Health Records.” JMIR Medical Informatics 8 (10): e21798.](#content0017.xhtml)

[38\. Wikipedia contributors. Wikipedia, The Free Encyclopedia. 2023. Intelligence amplification. Available from: https://en.wikipedia.org/w/index.php?title=Intelligence\_amplification&oldid=1169188703](#content0017.xhtml)

[39\. Center for Devices, and Radiological Health. n.d. “Artificial Intelligence and Machine Learning (AI/ML)-Enabled Medical Devices.” U.S. Food and Drug Administration. FDA. \[Internet\]\[cited 2022 November 8\] Available from: https://www.fda.gov/medical-devices/software-medical-device-samd/artificial-intelligence-and-machine-learning-aiml-enabled-medical-devices](#content0017.xhtml)

[40\. Donoho D. 50 years of data science. Presentation at the Tukey Centennial Workshop September 15, 2015. \[cited 2022 April 1\] http://courses.csail.mit.edu/18.337/2015/docs/50YearsDataScience.pdf](#content0018.xhtml)

[41\. Anaconda State of Data Science Survey. \[Internet\]\[cited 2022 September 21\] Available from: https://www.anaconda.com/state-of-data-science-report-2022](#content0018.xhtml)

[42\. Anderson J. Data Engineers vs Data Scientists. April 11, 2019 . \[cited 2022 April 3\] Available from: https://www.oreilly.com/ideas/data-engineers-vs-data-scientists](#content0018.xhtml)

[43\. Metwalli, Sara. 2021. “10 Data Science Job Titles — Which Role Is Right for You?” Built In. \[Internet\]\[cited 2022 Sept 20\] Available from: https://builtin.com/data-science/data-science-jobs](#content0018.xhtml)

[44\. DataFlair \[Internet\]. 2019 \[cited 2023 Aug 12\]. Why Learn Data Science? - 5 Major Reasons that will Blow Your Mind! Available from: https://data-flair.training/blogs/why-learn-data-science/](#content0019.xhtml)

[45\. Sharma R. 8 interesting Data Science applications in manufacturing industry \[2023\] \[Internet\]. upGrad blog. upGrad Education; 2022 \[cited 2023 Aug 12\]. Available from: https://www.upgrad.com/blog/data-science-applications-in-manufacturing-industry/](#content0019.xhtml)

[46\. 11 Important Reasons To Study Data Science (And Career Tips) \[Internet\]. 2022 \[cited 2023 Aug 12\]. Available from: https://www.indeed.com/career-advice/career-development/reasons-to-study-data-science](#content0019.xhtml)

[47\. Brownlee J. MachineLearningMastery.com . Machine Learning Mastery; 2019 \[cited 2023 Aug 12\]. Why Training a Neural Network Is Hard. Available from: https://machinelearningmastery.com/why-training-a-neural-network-is-hard/](#content0020.xhtml)

[48\. Home \[Internet\]. Medical Intelligence Society. \[cited 2022 Mar 17\]. Available from: https://www.misociety.org](#content0021.xhtml)

[49\. A quote by Woody Guthrie \[Internet\]. \[cited 2022 Apr 11\]. Available from: https://www.goodreads.com/quotes/12979-any-fool-can-make-something-complicated-it-takes-a-genius](#content0023.xhtml)

[50\. Bioinformatics Laboratory, University of Ljubljana. Data Mining \[Internet\]. \[cited 2022 Mar 17\]. Available from: https://orangedatamining.com/](#content0023.xhtml)

[51\. Murallie T. Welcome to the Age of Citizen Data Scientists \[Internet\]. Towards Data Science. 2021 \[cited 2022 Mar 20\]. Available from: https://towardsdatascience.com/how-to-become-a-citizen-data-scientist-294660da0494](#content0023.xhtml)

[52\. Smith CS. “No-Code” Brings the Power of A.I. to the Masses. The New York Times \[Internet\]. 2022 Mar 15 \[cited 2022 Mar 18\]; Available from: https://www.nytimes.com/2022/03/15/technology/ai-no-code.html](#content0023.xhtml)

[53\. Peker M, Özkaraca O, Şaşar A. Use of Orange Data Mining Toolbox for Data Analysis in Clinical Decision Making \[Internet\]. Expert System Techniques in Biomedical Science Practice. 2018. p. 143–67. \[cited 2022 March 5\] Available from: http://dx.doi.org/10.4018/978-1-5225-5149-2.ch007](#content0023.xhtml)

[54\. Vaishnav D, Rama Rao B. Comparison of Machine Learning Algorithms and Fruit Classification using Orange Data Mining Tool \[Internet\]. 2018 3rd International Conference on Inventive Computation Technologies (ICICT). 2018. \[cited 2022 March 15\] Available from: http://dx.doi.org/10.1109/icict43934.2018.9034442](#content0023.xhtml)

[55\. Frąckiewicz M. TS2 SPACE. 2023 \[cited 2023 Aug 12\]. Applying Orange to Big Data Analytics: A Practical Guide. Available from: https://ts2.space/en/applying-orange-to-big-data-analytics-a-practical-guide/](#content0023.xhtml)

[56\. Chan Zuckerberg Initiative \[Internet\]. 2021 \[cited 2023 Aug 12\]. Scalable visual data analytics with orange data mining toolbox. Available from: https://chanzuckerberg.com/eoss/proposals/scalable-visual-data-analytics-with-orange-data-mining-toolbox/](#content0023.xhtml)

[57\. Orange Data Mining \[Internet\]\[cited 2022 March 3\] Available from: https://orangedatamining.com/docs/](#content0025.xhtml)

[58\. Orange Video. \[Internet\]. \[cited 2022 Apr 11\]. Available from: https://www.youtube.com/results?search\_query=orange+data+mining](#content0025.xhtml)

[59\. Orange Visual Programming — Orange Visual Programming 3 documentation \[Internet\]. \[cited 2022 Apr 11\]. Available from: https://orange3.readthedocs.io/projects/orange-visual-programming/en/latest/index.html](#content0025.xhtml)

[60\. Bioinformatics Laboratory, University of Ljubljana. Widget catalog \[Internet\]. \[cited 2022 Apr 11\]. Available from: https://orangedatamining.com/widget-catalog/](#content0025.xhtml)

[61\. Website \[Internet\]\[cited 2022 Apr 11\]. Available from: https://datascience.stackexchange.com/questions/tagged/orange](#content0025.xhtml)

[62\. GitHub \[Internet\]. \[cited 2022 Apr 11\] Available from: https://github.com/biolab/orange3](#content0025.xhtml)

[63\. JASP. Available from: https://jasp-stats.org/](#content0027.xhtml)

[64\. Muenchen, Bob. 2019. “A Comparative Review of the JASP Statistical Software.” R-Bloggers. April 18, 2019.\[Internet\]\[cited 2022 December 13\] Available from: https://www.r-bloggers.com/2019/04/a-comparative-review-of-the-jasp-statistical-software/](#content0027.xhtml)

[65\. Orange Workflows. https://orangedatamining.com/workflows](#content0033.xhtml)

  

![](images/image-Y5T59BFX.jpg)Chapter 2

  

## Data Preparation and Wrangling

  

“We are drowning in information, but we are starved for knowledge”

– Various authors, original probably John Naisbitt

  
![](images/image-M6MTZISG.jpg)  
  

LEARNING OBJECTIVES

  
  

By the end of chapter two readers should be able to:

•Describe quantitative and qualitative data types.

•List synonyms for predictors and outcome.

•Enumerate the programming data types.

•Discuss the 8-step DISCOVER data science process

•Discuss the processes and tasks involved in data wrangling.

•Describe various data science preparation and wrangling concepts.

•Describe the steps involved in various data wrangling concepts such as feature engineering.

•Understand the need for and steps involved in conducting data science experiments.

•Understand the purpose and outcomes for various Orange widgets.

•Understand various JASP analysis options.

  
  

Chapter 2 Summary

  

  

In this chapter we will review data types, basic data concepts and review the widgets in Orange that can manipulate, reformat, preprocess, and transform data as required in the initial data preparation and wrangling phase of data analytics. Fundamental data literacy is important for all professionals engaged in basic and advanced data analytics. They must feel comfortable exploring datasets to determine how much cleaning and data exploration is needed. The reality is that there are very few educational medical datasets that are realistic (real world) that are publicly available due to HIPAA concerns. Similarly, many medical datasets are too small for meaningful interpretation. On the other hand, there are several industries where great amounts of public data are available that have no privacy concerns, such as for the financial markets, consumer spending, consumer debt, world economic data by country, and much more. We need to train on these datasets but know they have limitations. The Orange widgets involved in extensive data preparation and transformation activities will be discussed in this chapter, along with JASP functionality.

  

Key Principles:

•Data quality,quantity, and relevance are of primary importance in data science.

•Medical data is associated with multiple privacy challenges.

•Be sure to perform specific pre-processing (e.g., imputing or scaling) only on the training dataset and not the test dataset (hold-out set).

•Class imbalance is a major challenge with medical, banking, and in other areas.

•More data is almost always better for machine learning projects, especially if it includes data from diverse time periods and stratified groups.

•Some suggest that you should never have less than 300 rows of data. Others suggest that you need 10 times as many rows of data as columns of data used in the model.

•Multicollinearity is not your friend in machine learning and it should be addressed early. The calculations of Variance Inflation Factors (VIFs) is the gold-standard for identifying multicollinearity.

•Planning for future data science experiments (DSEs) is an important part of the data wrangling phase.

  

  

2.1 UNDERSTANDING DATA AND DATA TYPES

  

  

#### 2.1.1 Introduction

  

This chapter on data preparation and wrangling is lengthy because data quality, quantity, and relevance is at the center of data science. This is particularly important in machine learning and artificial intelligence. Data that is lacking for any reason results in a “garbage in garbage out” scenario. As pointed out in Chapter 1, data scientists spend most of their time getting data ready to model, which requires a great deal of experience and expertise. Any shortcuts applied to the techniques described in this chapter can certainly add new layers of risk to the credibility, success, and accuracy of any predictive model.

This chapter will cover all the important data science steps required to ensure the quality and success of all other exploratory data analysis and predictive modeling activities. The top-level activities covered in this chapter are listed below, which are the second and third steps of our 8-step data science DISCOVER process:

•Integrate , collect and import high quantity and high-quality data.

•Scrub , clean, transform, feature engineering, dummy encoding, and check multi- collinearity (VIFs).

The above-mentioned steps have many sub-steps that will be described in this chapter which are fully supported collectively by Orange and JASP open-source software capabilities. No matter what further developments happen in the future with auto-ML and AI to make data prep and wrangling easier, the data scientist still needs to have a full understanding of all sub-steps to direct, oversee, and review any automated steps to ensure the efficacy of that work.

  

#### 2.1.2 Data Science DISCOVER Process Step 2

  

[Figure 2.1 shows the details of the 8-step data science DISCOVER process which is at step 2. Data Science Process Step 2: Integrate, Collect, and Import High Quantity and High Quality Data. The lack of sufficient high-quality data per class of interest will not allow a predictive model to learn much about the relationship between input factors and the target output factor or class. Low amounts of data force us into uncomfortable compromises, such as not being able to split data into training and test data. Having sufficient amounts of relevant data allows us to split the data. The training data would be trained and tuned with k-fold cross-validation data. You should then check how well this tuned model performs on the unseen test dataset we split out.](#content0040.xhtml)

Listed below are the most common detailed tasks required to succeed in step 2 of this DISCOVER process:

1\. De-identify patients for healthcare related data.

2\. Ensure the quality of your data sources.

3\. Seek access to high-quality needed/desired data.

4\. Determine the cost to acquire high-quality needed/desired data.

5\. Collect as much accurate data as possible for each class to avoid class and feature imbalance issues.

6\. Collect as much accurate data as possible for each population, customer, or product sub-group to prevent model bias for the most frequent sub-group.

7\. Determine at which point more data will not help model performance.

8\. All factors (columns) should be independent of each other. If not, VIF identification and regularization techniques such as lasso, ridge, and elastic net regression, and principal components analysis (PCA) can help.

  
![](images/image-7V2A7HEB.png)  

Figure 2.1 Step 2 in the 8-step data science DISCOVER process

  

9\. Ten times as many rows of data as columns should be used in a model, as a general guideline. ¹

10\. If the model is linear, hundreds of rows per class may be required as a minimum. Residual analysis can determine if the model is linear or not.

11\. If the model is non-linear, a minimum of thousands of rows per class may be required as a minimum. ²

12\. Some suggest always having at least 300 rows of data before starting with predictive analytics and 1,000 rows of data for forecasting models. ³- ⁴

13\. The specific requirements for accurate predictions may vary depending on the problem, the complexity of the data, and the specific techniques used. Ideally, tens or hundreds of thousands of data rows are desired for “average” modeling problems. ⁵

14\. More data is needed for deep learning compared to machine learning but there are no hard and fast rules. Regardless of whether the data will be used for prediction or if it is images used in a convolutional neural network, it depends on the complexity of the task, and the size and diversity of the dataset.

15\. Evenly distribute your data collection across the ‘who, what, when, where, and why’ categories to capture a comprehensive spectrum of predictor variables and stratified groups. Models built on an imbalanced data collection plan can have significant blind spots.

16\. Be sure that you have enough data for each stratified group of interest in the intended scope of your analysis. All of the guidelines mentioned above for the minimum amount of required data apply to each stratified group for which you intend to conduct predictive analytics.

  

  

KEYPOINT: More data is almost always better for machine learning projects. Some suggest that you should never have fewer than 300 rows of data when starting predictive analytics. Others suggest that you need ten times as many rows of data as columns of data used in the model.

  

  
![](images/image-LL0YBUZG.png)  

Figure 2.2 DIKIW pyramid

  

A reminder that datum is singular, and data is plural in most publications. Data are simply numbers without any particular meaning, e.g.,10. Information is data with meaning, for example, a hemoglobin value of 10. Knowledge is information that is felt to be true; a hemoglobin of 14 is normal. Wisdom uses knowledge wisely to interpret the significance of information and knowledge. For example, a hemoglobin of 10 is low but expected with chronic renal failure. Chang et al. mention another category, “intelligence” in the traditional data pyramid to suggest artificial intelligence must be considered. Artificial intelligence has the potential to add to our knowledge and wisdom.⁶ Figure 2.2 shows the data, information, knowledge, intelligence, and wisdom (DIKIW) pyramid. Note that there is much more data than wisdom available.

The smallest data unit is the bit (binary digit), which can be represented as the binary choices (0 or 1). A byte consists of eight bits and can provide a potential 256 data combinations. For example, 0100 0001 represents the capital letter A. Four bytes together would provide more than 4 million possibilities. Because these strings of numbers could be extremely long, the codes can also be displayed as octal (base 8), decimal (base 10), or hexadecimal (base 16). This type of binary coding is important, as computers can rapidly interpret data in this binary format. ⁷

With the explosion of data has come the increasing size that challenges us all and is displayed in Table 2.1. ⁸ What seems like massive datasets today may seem like small or medium datasets in the future.

There are three types of data: structured, unstructured, and semi-structured.

Structured Data: Most data that is stored in a relational database is structured, such as name, age, gender, which can show the results of medical tests, banking transactions, or other domains. Such data can be categorical or numerical data.

Unstructured Data: This can include social media posts, chat logs, customer feedback and more. It is said that about 75% of medical records consist of unstructured data, or free text. That could include doctor notes and may or may not be associated with metadata.

  

Table 2.1 Data sizes

  

 
| Name || Equal To || Size in Bytes |
| --- | --- | --- |
| Bit || 1 bit || 1/8 |
| Nibble || 4 bits || 1/2 |
| Byte || 8 bits || 1 |
| Kilobyte || 1,024 bytes || 1,024 |
| Megabyte || 1,024 kilobytes || 1,048,576 |
| Gigabyte || 1,024 megabytes || 1,073,741,824 |
| Terabyte || 1,024 gigabytes || 1,099,511,627,776 |
| Petabyte || 1,024 terabytes || 1,125,899,906,842,624 |
| Exabyte || 1,024 petabytes || 1,152,921,504,606,846,976 |
| Zettabyte || 1,024 exabytes || 1,180,591,620,717,411,303,424 |
| Yottabyte || 1,024 zettabytes || 1,208,925,819,614,629,174,706,176 |

  

Semi-Structured Data: Some data has limited organizational structure (or schema). Examples of semi-structured data include XML markup language and JSON.

Data can encompass various types of information beyond just numbers to include human sensory data that can be converted to numbers for computational analysis. Some sensory data examples include images, aromas, flavors, sounds, and textures which are unstructured data types. These types of data can be subjective and rely on human perception for meaning but they can still be converted into numerical values for computational analysis.⁹

  

  

KEYPOINT: We will use multi-industry data for examples and exercises in this book, but it must be pointed out that healthcare data is associated with multiple challenges. While there is the statement, “data is the new oil”, in the medical field it is crude oil, requiring refinement at multiple stages. ¹⁰

  

  

Specific challenges with medical data are as follows:

•There is a shortage of high-quality medical data for supervised and unsupervised learning.

•Due to HIPAA concerns, there is also a shortage of medical transcriptions (unstructured data) that can be used for natural language processing, research, and education.

•Publicly available tabular medical datasets are small (100-400 patients) and often need data wrangling activities to deal with multicollinearity, categorical columns in need of n-1 dummy encoding, and other issues. They often include imbalanced data for classification targets.

•Medical data inside of healthcare systems is full of missing values, unusual acronyms, and inconsistent terminology. ¹¹ This is true despite multiple data standards such as DICOM, LOINC, etc.

•Trying to analyze unstructured data is challenging in healthcare, and this is why so much attention has been given to natural language processing to help solve this problem. Additionally, medical image data has numerous challenges, such as an inadequate number of images and poor labeling. Furthermore, the popular image database ImageNet hosts 14 million images and is used to train neural networks but has no medical images. ¹²

•Data is siloed, located in multiple locations and in multiple formats. Clinical data differs from claims data coded with ICD-10 and CPT codes. Data scientists and engineers must build pipelines to extract, transform and upload data into a data warehouse, data lake, or a data lakehouse for future analyses. Big data (high volume, velocity, value, veracity, and variety) represents a challenge, as does new sensor data from, e.g., activity and glucose monitors. This raises the question of who or what will interpret the voluminous data, and will this be reimbursable?

To further complicate matters, statisticians and computer scientists use different terms to describe the same concepts. In Table 2.2, synonyms for predictors and outcomes are presented.

  

Table 2.2 Synonyms for predictors and outcome

  

 
| Predictors || Outcome |
| --- | --- |
| Independent variable, x variable, predictors, attributes, explanatory variables, feature, factors, co-variants || Dependent variable, y variable, target, label, class, response variable |

  

One of the most helpful dataset repositories for data science education is the University of California Irvine Data Repository. The repository contains over 600 datasets covering seven domains and offering data for classification, regression, clustering, and other methods. The origin of the data is explained and is associated with a data dictionary (codebook).¹³ However, many of these datasets are small and dated. Many are in unusual file formats, such as .rar and .data files.

  

#### 2.1.2 Data Types

  

There are multiple ways to conceptualize and organize data. Start with the types of data. Figures 2.3 and Table 2.3 describe the data types and differentiate between continuous and discrete data. This data classification is not perfect. For example, Likert scales (rate your satisfaction from 1 to 5) are considered interval data by some researchers and ordinal by others. When the Likert scale is converted to numerical, it is usually considered interval data.¹⁴ Remember, computers interpret 1’s and 0’s, so despite one being numerical, it is discrete in this instance. You cannot have 0.5 heart disease. For a typical machine learning exercise, heart disease is labeled as 1 and its absence as 0.

Data includes numbers, characters, symbols, logical data (Boolean), and images. Data can be stored in many different data types, and these types determine what actions/functions can be performed on the data with a programming language or how it is stored in a database or spreadsheet. The data types for programming are outlined in Table 2.4.

  

Table 2.3 Continuous vs discrete data

  

 
|  || continuous || discrete |
| --- | --- | --- |
| nominal ||  || ✔ |
| ordinal ||  || ✔ |
| interval || ✔ || ✔ |
| ratio || ✔ || ✔ |

  

Lastly, because data scientists often employ linear algebra to transform words and images into matrices, it is vital to understand the differences between scalar, vectors, matrices, and tensors. Scalars represent a single number, such as 11, whereas vectors are a row or column array. Matrices are 2-D arrays of numbers and describe linear relations between vectors. Tensors are arrays with more than two axes and describe multilinear relations between vectors. ¹⁵ See Figure 2.4.

  
![](images/image-409ER1PZ.jpg)  

Figure 2.3 Types of data (courtesy University of New South Wales, Australia)

  

Table 2.4 Data types for programming (courtesy Bournetocode.com)

  

 
| Data Type || Description |
| --- | --- |
| Integer || An integer is a numeric variable without a decimal. Integers are whole numbers and can be positive, negative, or zero. For example, 0,2,33,-199 |
| Real (Float) || Real numbers include all the integer numbers that exist to infinity, plus all their fractions and decimals. For example, 1.26, -7.8, 3.14 |
| Char/Character || A character data type is used to store a single alphanumeric character and can be any letter, number, or symbol |
| String || A string can hold a list of characters of any length. It can represent alphanumeric data and symbols. A string can be null (empty), one or many characters |
| Boolean || A Boolean data type represents two values: True and False |

  
![](images/image-P2D2O56C.png)  

Figure 2.4 Scalar, vector, matrix, and tensor (courtesy dev.to)

  
![](images/image-7CHPOUF8.jpg)  

Figure 2.5 Step 3 in the data science DISCOVER process

  

2.2. STEP 3 IN THE DATA SCIENCE PROCESS

  

  

[Figure 2.5 displays the 8-step DISCOVER process updated to display where we are now in this book as we walk through the details of the data science process.](#content0041.xhtml)

Data Science DISCOVER Process Step 3: “Scrub, clean, transform, feature engineering, dummy encoding, and check multicollinearity (VIFs).” These seemingly mundane tasks are key for success and to avoid failures in predictive models. The activities encompass the broad topics of data wrangling, preprocessing, and feature engineering.

Key tasks in this step include:

1\. Identifying target variables for prediction

2\. Correcting data issues and errors

3\. Identify and address suspicious outliers

4\. Ensuring adequate data for training and test data split, k-fold cross-validation, or other split methods

5\. Considering synthesizing more data if needed while avoiding overfitting

6\. Adding new calculated or extracted features

7\. Consider data binning when appropriate

8\. Implementing a data leakage prevention strategy

9\. Address class and feature imbalances using methods such as weights, up/down sampling, and SMOTE

10\. Checking for randomness in missing data

11\. Deciding on imputation strategies for missing data

12\. Consider various data transformations, normalizations, standardizations, as required

13\. Using N-1 Dummy encoding for categorical variables

14\. Testing for multicollinearity with Variance Inflation factors (VIFs)

15\. Delete high VIFs or apply regularization techniques to handle high VIFs

16\. Assessing the need for dimensionality reduction with PCA and other techniques

17\. Validate the accuracy, consistency, and usability of the improved dataset

18\. Planning diverse data science experiments to optimize model performance

  

#### 2.2.1 Data Cleaning

  

•Evaluate the data Structure - what format is the data in? CSV, XLSX, JSON, etc.?

•Cleaning - are the dates in the same format? Is gender recorded the same? How are missing values recorded (blank, zero, NaN, etc.)? Are phone numbers, zip codes, etc., uniform? Are variables written in lowercase? Are there spaces in the header names? Do you need to remove punctuation, html, etc.? Are there any obvious data errors, misspelled words, and synonyms for the same words used that should be corrected?

•Data validation - can be performed with Microsoft Excel and other tools using rules to stop data errors from being entered in data sheets that will be uploaded into Orange. ¹⁶

[•Figure 2.6 shows an example of data in need of cleaning. This spreadsheet contains demographic descriptions and issues that need to be addressed. Just some of the issues in this messy dataset are pointed out by the arrows.](#content0043.xhtml)

  
![](images/image-MQFZ1AC6.png)  

Figure 2.6 Messy data

  

#### 2.2.2 What is Feature Engineering?

  

A superficial and shortcut approach to data analysis can easily derail successful efforts associated with any root cause analysis, statistical analysis, Lean Six Sigma efforts, predictive analytics, machine learning, and AI projects. Disciplined and thorough feature engineering can play an important role as part of the collective tasks required to transform a superficial analysis into a thoughtful, specific, and insightful analysis. Feature engineering describes the transformations of predictors (features) to match machine learning algorithmic requirements that may improve model performance. Feature engineering requires domain knowledge to fully understand the dataset. ¹⁷ Some use the term feature engineering to mean transforming, constructing, or reducing model predictive variables. Others equate it to any type of data manipulation that may improve model performance. The following are common examples of feature engineering that often require domain knowledge:

•Mathematical transformation and re-scaling of continuous variables

•Extracting day of the week, hour of the day and other time-specific data that are added as new features

•Creating new features that are sums, averages, ratios, subtraction of other features

•Binning of continuous variables

•Transforming text into numerical data

•Clustering text into useful groups for analysis

•Converting categorical variables into numerical values with one hot or n-1 dummy encoding so that algorithms can understand their significance

  

#### 2.2.3 Handling Missing Data with Imputation or Deletion

  

There are actually three general ways to deal with missing data: do nothing, impute values for the missing data, or delete the missing rows and/or columns. Missing data is an issue with almost any dataset, so a strategy must be developed to deal with it. It is common practice to start by viewing the data in a spreadsheet. Are there blank cells or cells containing question marks, zeroes, NA, etc? In Orange, the overall percentage of missing data is noted in the File widget, and the percentage missing in each column is noted in the Feature Statistics widget.

Addressing missing values is important for several reasons. Unlike simple decision trees and ensemble trees, such as random forest, neural networks, and SVM do not tolerate missing data well.¹⁸ Doing nothing to address missing values can create model accuracy issues.

  

  

KEYPOINT: Missing data should be dealt with only after splitting the data into train/test to avoid data leakage, which can create overly-optimistically performing models. You should not impute missing data on the test data, only on the training data. The only exception to this rule should be for small datasets where splitting the data into training and test datasets is impractical since the model cannot learn on such a small training data set. In this special case, k-fold cross-validation should be used instead of the train and test data split. If you do not split your data into training and test splits and only use the training results for decision making, you face the high risk that the untested model may be overly complex and overfit the data. ¹⁹-²⁰

  

  

A common strategy for handling missing data is to first categorize it as follows:

•Missing completely at random (MCAR) : there is no pattern in the missing data, regardless of the variable. For example, a survey result is lost in the mail. This implies that the reason for loss is unrelated to the data and could happen to any patient or customer randomly. ²¹

•Missing at random (MAR) : there is a pattern in the missing data, but this is unrelated to the outcome. An example might be that females did not include their weight as often as males in a survey. Imputation is reasonable in this instance. ²¹

•Missing not at random (MNAR) : there is a pattern that does affect the outcome. Therefore, deleting the missing values could affect the model’s outcome. More study is warranted to look for causes, etc. Suppose there is a hidden reason for the missing data. In that case, it can usually be statistically identified by comparing the impact of all missing data for a specific attribute against the non-missing data against the target variable. If the differences between those two classes are statistically significant (p-value < 0.05), then the missing data is not random, and model-based imputation should be considered. ²¹

  

2.2.3.1 Imputation

  

Imputation means replacing missing data with a value. Some algorithms do not tolerate missing data, so a decision must be made whether to delete certain subjects or impute the missing data with the mean, the median for numerical data, imputing the most common class for categorical data, random values, model-based values, and other options shown in the Impute widget, as shown in Figure 2.8. You should try not to delete any data if there is an alternative. Imputation of the wrong values can be detrimental to the model. The Orange Impute widget offers what many consider the gold standard for data imputation methods: Model-based Imputation.²² Model-based Imputation in Orange constructs a model for predicting the missing value based on values of other attributes. A separate model is constructed for each attribute.

It should be noted that the imputation of the mean, median, or other fixed values for large amounts of missing data can lead to rather unusual-looking histograms of those data columns due to spikes that will be present on the histograms for the imputed fixed values.

  
![](images/image-M9B2Q2DH.jpg)  

Figure 2.7 Imputation options in the Impute widget

  

2.2.3.2 Handling Missing Data with the Preprocess Widget

  

The Orange Preprocess widget offers basic data imputation options that do not meet the needs of more sophisticated data analysts (See Figure 2.8). For example, one of its three imputation options is for the average value of a numerical data set. However, most data are not normal, and the median would be more valuable than the mean, but the median option is not available in the preprocess widget.

Imputation will also be discussed and practiced in other chapters to show its impact on model performance.

Deletion of missing data can also be carried out in Orange. The Preprocess widget offers the “remove rows with missing values” option, while the Impute widget option words this differently by offering the “Remove examples with missing values” option. Both options result in the same actions which is to delete any rows with missing values.

  
![](images/image-TL3LIULE.jpg)  

Figure 2.8 Limited Imputation options in the Preprocess widget

  

2.2.3.3 Data Imputation Experiment

  

So how does an analyst know which of the three methods (Ignore, delete, or impute) to choose when dealing with missing values? The answer is: with experimentation. Machine learning involves a lot of experimentation, and the data preparation and feature engineering phases are no exception to that rule. ²³

For this experiment, a hepatitis data set that has 155 rows of patient data with a yes or no diagnosis of hepatitis was used. (Data is available on our website File-Share tab).²⁴ Nineteen predictor variables are available for analysis. The Orange Rank widget tells us that Protime (a continuous variable) ranked highest of all features in its relationship with a hepatitis diagnosis. However, 43% of the values for protime were missing in the original dataset.

For this experiment, we will test how three different imputation methods in Orange will fare when their distribution with the imputed data is compared to the distribution of the missing data. The Two-sample Kolmogorov-Smirnov (K-S) Test p-values will be used to judge how the imputed distributions compare with the original distribution with the missing data. If the K-S p-values are greater than 0.05: we can accept the hypothesis that the two samples come from the same distribution.

This experiment will determine which of the data imputation methods in Orange is best at re-creating a histogram that matches the original dataset with the missing data. The Orange Impute widget offers three groups of options: 1) delete all rows with missing data, 2) imputation of various fixed or custom values to replace missing values, or 3) The imputation of non-fixed values based on either a tree-based model or a random based model that matches the data distribution. Figure 2.9 shows the three imputation options that were used for this experiment. The results from this experiment are shown in Figure 2.10.

  
![](images/image-8U4NIGSV.jpg)  

Figure 2.9 Imputation options used for the imputation experiment

  
![](images/image-DOR7CVIP.jpg)  

Figure 2.10 Data imputation experiment results for a hepatitis dataset

  

This experiment showed that the random value and model-based imputation methods created distributions that matched the original dataset (p-values > 0.9) and the imputation of average values for the missing data created a distribution that did not match the original dataset very well (p-value = 0.01). The worst matching distribution also had an “odd” looking spike where all of the average values were located, as seen on the far-right graph in Figure 2.10.

The lessons learned from this experiment are as follows:

•Do not blindly apply an imputation method without visually comparing the new and original distribution charts.

•Do not blindly accept your imputation method without applying the Two-sample Kolmogorov-Smirnov (K-S) Test to see how well it compares with the original dataset with the help of the K-S test p-values.

•A free online K-S calculator can be used to calculate the p-values for the test. When pasting data into the required fields in the K-S test calculator, be sure that the data column labels have been deleted and that all spaces between numbers for the missing data column of numbers have been eliminated. This can be achieved by simply sorting that column of data in Excel before copying and pasting that data into the calculator field. ²⁵

  

#### 2.2.4 Handling Outliers

  

Like missing data, outliers must be scrutinized. Visualization is a good starting point. An outlier is any value outside the established pattern, but more formal rules exist. For example, some define a low outlier if it falls below the first quartile minus the interquartile range (IQR) x 1.5 or above the third quartile + IQR x 1.5. ²⁶ Others refer to those IQR x 1.5 limits as the “inner fence” and the start of “mild outliers’’ and use IQR x3 as the “outer fence” and the start of “extreme outliers.’’ ²⁷ Figure 2.11 shows how JASP identifies outliers for glucose data from the diabetes dataset using the 1.5 x IQR definition on a box plot. This Figure also shows critical descriptive statistics and a distribution plot with the location of the outliers for this glucose variable.

Others have posited that values above or below 3 standard deviations should be considered outliers. This is typically displayed on statistical process control (SPC) charts.

  
![](images/image-O40FWFN2.jpg)  

Figure 2.11 Outlier identification on Box plots and Distribution plots

  

Descriptive statistics can be calculated in JASP with this command string:

Descriptive Statistics > select variables > Statistics > check desired stats

Box Plots can be created in JASP with this command string:

Descriptive Statistics > select variables > Customizable plots > check Box Plots and Box Plot elements

Distribution plots can be created in JASP with this command string:

Descriptive Statistics > select variables > Basic plots > check: Distribution plots, display density, and Display rug marks. (Note: Rug marks show tic marks for each value in the data set)

  
![](images/image-1O4P9U1E.png)  

Figure 2.12 Data visualizations useful for discovering potential data entry errors

  

The presence of outliers raises many questions. Some may ask if it is a lab error, measurement error, a data entry error, or a valid outlier. While decision trees, support vector machines (SVM), and k-nearest neighbors can tolerate outliers, other algorithms are sensitive to outliers. Transforming data to a normal distribution can reduce the disruption they create for specific algorithms. Decision trees handle the outliers because the partitioning happens based on the proportion of samples within the split and not on absolute values. The K-nearest neighbors algorithm looks at proximity between data points, so outliers are not considered. In the feature engineering phase of an analysis project, it is important to identify, correct, and delete obvious data entry errors.

Deleting all outliers in a dataset is only recommended if they are all designated as errors. Stratify the data with available categorical variables to see if there is an explanation for the outliers. Deleting inconvenient data (outliers) to make a predictive model look better is not wise and short-sighted. When there is a measurement outlier, analysts should look for previous measurements which may show similar results or strongly suggest the outlier is an error. All other legitimate outlier situations can be dealt with during modeling iterations, where the impact of modeling residuals and outliers should be further analyzed. If it is determined that outliers should be deleted, JASP offers the filter option in the spreadsheet view of the data from which deletions can be made based on customized equations that can be constructed.

[Figure 2.12 shows six data visualization plots mentioned above that can be used to identify questionable data outliers (shown in boxes) in a diabetes data set that may be data entry errors. In many Orange graphs, you can hover over specific data points in the graphs to view their exact values while considering if those data points are unrealistic and obvious data entry errors. Patients were labeled as having type 2 diabetes if their HgbA1c was 6.5 or higher, which is the standard. Regardless, some patients have elevated serum glucose, despite being labeled as non-diabetic. This situation warrants further review.](#content0046.xhtml)

[Figure 2.13 shows the widget combination setup that created the data visualizations shown in Figure 2.12.](#content0046.xhtml)

Orange has an Outliers widget that resides in the unsupervised learning module. Once you have identified significant outliers in your data, this widget can remove them. When you open the widget, you note that there are four methods to detect outliers. The default is Local Outlier Factor with contamination = 10% (percent outliers in the data), neighbors = 20, and Metric = Euclidean. Options:

1\. One class SVM with the non-linear kernel (RBF) : classifies data as similar or different from the core class:

a. Nu is a parameter for the upper bound on the fraction of training errors and a lower bound of the fraction of support vectors. Default = 50%

b. Kernel coefficient is a gamma parameter that specifies how much influence a single data instance has. Default = 0.01

c. Works well with non-normally distributed data

2\. Covariance estimator : fits ellipsis to central points with the Mahalanobis distance metric

a. Support fraction specifies the proportion of points included in the estimate. Default = 1.0

b. Only works with normally distributed data

3\. Local Outlier Factor : obtains local density from the k-nearest neighbors:

a. LOF is a Python package

b. Neighbors represent the number of neighbors

c. Metric is the distance measure

4\. Isolation Forest : isolates observations by randomly selecting a feature and then randomly selecting a split value between the maximum and minimum values of the selected feature

a. Replicable training fixes random seed

b. Useful for high dimensional data ²⁸

Some trial and error is indicated. Using the Kaggle Global Country Information dataset and the four methods, the number of removed outliers varies.²⁹ Figure 2.14 displays the distribution of total tax rate with a bin of 0.1. After removing outliers the distribution is more normal using the isolation forest method, and displayed in Figure 2.15.

  
![](images/image-P8SYHYER.jpg)  

Figure 2.13 Widget combination setup for data visualizations of outliers

  
![](images/image-11CA9QC5.png)  

Figure 2.14 Total tax rate distribution (note outliers above 1)

  
![](images/image-3T45VML2.png)  

Figure 2.15 Total tax rate distribution after outliers have been removed

  

#### 2.2.5 Binning / Discretize

  

•Binning and Discretize actions are also known as Bucketing and Partitioning. These actions can be applied to both numerical and categorical data. For example, a numerical lab test result of 21-40 could be labeled as low, 41-60 as medium, and 61 to 80 as high. Categorical data could be binned as follows: seizures, strokes, and TIAs >> neurology; heart attacks, angina, and heart failure >> cardiology. Binning should be used cautiously because you may diminish some useful information as a result.

  

![](images/image-TEMD15Y1.jpg)Orange offers the binning / discretize options from three different widgets:

  

![](images/image-IMR0T3RY.jpg)The Mosaic Display widget offers auto-binning for continuous variables into equal frequency bins. The width of a Mosaic Display represents the frequency counts of the data in that bin. Multiple variable Mosaic Plots can be created, but they tend to be less explainable with increased counts of factors included in the plot.

  

![](images/image-IMR0T3RY.jpg)Double-left-click on the Preprocess widget > Select Discretize Continuous Variables > select one of 4 options.

  

![](images/image-IMR0T3RY.jpg)Double-left-click on the Discretize widget > select one of many different options.

Binning options within the Discretize widget provide more customized options than the Discretize options in the Preprocess widget.

Goal of Binning:

•To improve insights into your data

•Improve the model performance by binning numerical data into predetermined data ranges

•Improve the model performance by determining ideal cut points in your data

Decision trees do this automatically by determining the best cut-off points and bins that will maximize the information gain in the model from those data splits or classifications.³⁰ However, binning represents raw information loss, and the goal of optimal binning is to create the best balance of information loss and the number of bins.³¹ Binning activities can be done within the “Preprocess” or the Discretize widget, and it is best if the previously connected widget is the Select Columns’ widget so that the Y and X-variables are well-defined.

Pros of Binning:

•It can bin numerical data according to categories that are generally accepted, such as aligning Body Mass Index (BMI) data according to underweight, healthy weight, overweight, and obesity categories accepted by the CDC. ³²

•It can be used to create custom bins that make sense to analysts, researchers, and consumers of that information.

•Entropy-MDL (minimum descriptive length) discretization methods or binning can maximize the information gain of a data set or model, but they can only be used for categorical outcomes.

•If the Entropy-MDL (minimum descriptive length) discretization method for categorical outcomes senses no information possible for an x-variable, it will not split that variable. It will be noted as a “single value” information gain of a data set or model, but they can only be used.

Cons of Binning:

•When analysts do this task independently in the feature engineering phase, they risk lowering the information gain in the analysis or model.

•Too often, splits or bins are just chosen as convenient talking points, such as age groups with 10-year spreads, and not optimized in the interest of information gain.

[Figure 2.16 shows the options available for binning within the Preprocess widget.](#content0047.xhtml)

The following numbers refer to Figure 2.16

1\. Entropy-MDL discretization by Fayyad and Irani to optimize information gain with its suggested bin endpoints. This feature automatically determines the optimal number and location of each split. Only use this when the Y variable is categorical.

2\. Equal frequency discretization splits bins by frequency and creates the same number of instances in each bin

3\. Equal-width discretization creates bins of equal width.

4\. Remove numerical features altogether.

[Figure 2.17 shows the options available for binning within the Discretize widget.](#content0047.xhtml)

Discretize widget options

1\. Equal frequency discretization splits bins by frequency and creates the same number of instances in each bin

2\. Equal-width discretization creates bins of equal width

3\. Leave numeric

4\. Entropy-MDL discretization by Fayyad and Irani to optimize information gain with its suggested bin endpoints. Only use this when the Y variable is categorical

5\. Remove numerical features altogether

6\. Manually chosen cut points can be selected

7-14. These options allow individual attribute settings to be set for each attribute separately

  
![](images/image-3AWW2BSG.jpg)  

Figure 2.16 Preprocess widget options for binning

  
![](images/image-ZD54DAE3.jpg)  

Figure 2.17 Discretize widget options for binning

  
![](images/image-31HNCFZ2.jpg)  

Figure 2.19 Top three Diabetes risk factor ranks

  

Binning should not be a random and non-reproducible activity that should be taken lightly. It should also be done in consultation with the Rank widget while reviewing the binning options available in the Mosaic Display, Preprocess, and Discretize widgets. Figure 2.18 shows the widget setup recommended to support various binning options. In this diabetes data set, various diabetes risk factors are casually being considered for binning, and we are looking to Orange for guidance. Mosaic Displays, Scatter Plots, and Distribution plots offer great visualizations of the binned data.

[Figure 2.19 shows the rank of the top three diabetes risk factors that are the most important, which is an important consideration when making binning visualization decisions. The Rank widget shows that three of the seven rank-scoring methods agree on the factor ranking for the top three factors.](#content0047.xhtml)

For this data set, a diabetes diagnosis was coded as one (1), and no diabetes was coded as zero (0).

[Figure 2.20 shows the discretize option chosen to create six equal-frequency bins that will be visualized with the help of mosaic plots, scatter plots, and distribution plots.](#content0047.xhtml)

The binning options in the Mosaic Display and Preprocess widgets do not offer all the binning options that the Discretize widget offers. We can view the binning details in the Data Table widget connected to the Discretize widget to see how the binning splits were chosen.

  
![](images/image-9489ASZB.jpg)  

Figure 2.18 Widget setup to support binning visualizations

  
![](images/image-NOMO7YBC.jpg)  

Figure 2.20 Binning options available in the Discretize widget

  

Figures 2.21 to 2.23 show how the Mosaic plot (See Figure 2.21), Scatter Plot (See Figure 2.22), and Distribution plot (See Figure 2.23) display the bins for the top three ranked factors using the diabetes data. Such plots are ideal for data exploration and visualization purposes.

  
![](images/image-QMR2KF3Y.png)  

Figure 2.21 The auto-calculated bins created from the Mosaic Display widget

  
![](images/image-9EFCXUIT.jpg)  

Figure 2.22 Scatter Plot widget output for six equal frequency bins

  
![](images/image-LRY45KUA.jpg)  

Figure 2.23 Distribution Plot widget output for six equal frequency bins

  

To wrap up our exploration of binning/discretization, with this data set, we add the Scatter Plot widget visualization for the bins of just the top two risk factors for diabetes in this dataset.

Binning subtracts raw information from the data set, so it should be considered a compromise. The lower the number of bins, the more raw data is lost. However, we can use binning to gain insights into the data set that may be helpful when explaining the analysis to other stakeholders and interested parties. When interpreting and explaining these binning results to others, it is best to focus the interpretations on the two extreme groups that may have emerged in the analysis and visualization. The two extreme groups with opposite results in Figure 2.24 are the upper right quadrant and the lower left quadrants of the scatter plot.

Here is one possible interpretation statement for this binned data exploration: Figure 2.24 shows the relationship between the top two diabetes predictors determined by the Rank widget (See Figure 2.24). All diabetes diagnoses are shown with dark symbols. A diagnosis of no diabetes is shown with light symbols. The upper right quadrant of jiggered symbols shows the highest instances of diabetes, with the highest age and glucose levels. The lower left quadrant shows only one diagnosed case of diabetes and is characterized by individuals with the lowest age groups and lowest glucose levels. Hovering over any symbols in the Orange Scatter Plot widget will highlight the detailed data collected for that individual.

  

#### 2.2.6 Log Transform

  

Medical and call center data is often skewed to the right, and this may present an issue for statistical methods that assume a normal distribution, such as the t-test and ANOVA. Lab test and customer talk time data tends to be skewed to the right (positive skew) because they cannot skew left and have a result below zero. ³³ One of the most commonly used transformations is log transform, available in the Orange Feature Constructor widget, which allows you to manually add features (columns) into your dataset for a wide array of data transformations on the data, such as Log transformations and many others. Despite many statistical textbooks recommending log10 transformation for skewness, others recommend against it with evidence that this transform can adversely affect the model.³⁴

Power transformations are available outside of Orange that can transform non-normal distributions to a normal distribution to improve the performance of models with skewed variable distributions.³⁵

  
![](images/image-XUQA5903.jpg)  

Figure 2.24 Scatter plot for the top two binned Diabetes risk factors

  

#### 2.2.7 Feature Creation

  

It is very common to add features to a dataset constructed from the existing features. The Feature Constructor widget can add numerical, categorical, text, and data/time features. You may want to create new numerical features that add, subtract, divide, or square existing numerical values, as an example, but many more options are available. Many forms of conditional expressions can also be created, such as: use 1 if A is greater than 5, otherwise, use 0 (zero). The help section of the Feature Constructor widget provides more examples and instructions on creating custom features that may require using some standard Python math symbols.

Feature creation can also be used to create a column for BMI from the height and weight columns. Subject matter experts can create new features based on their domain expertise. The opportunities are endless for how the Feature Constructor widget can be used to create new customized features.

  

#### 2.2.8 One Hot Encoding Versus N-1 Dummy Encoding

  

One-hot encoding is the process of changing categorical data into multiple columns of numerical data consisting of ones (yes) and zeros (no) for better computation in machine learning models (machine-readable). Instead of a column displaying animal species, each species becomes a new column with one (yes) and zero (no) numerical codes in the columns. This technique will be used in data exercises in this book. Figure 2.25 displays encoding a column of animal species. These zero and one columns are also called dummy or indicator variables.

The problem with one-hot encoding is that it can trigger the dummy variable trap when the number of dummy variable columns created equals the number of categories in the column that was not yet broken into separate columns. This leads to multicollinearity in modeling, meaning two or more factors are highly correlated. The dummy variable trap is also discussed in section 6.2.4 , and multicollinearity is discussed in more detail in section 2.4.2. One-hot encoded data can be beneficial for data visualizations but beware of the downsides of using that format for statistical or predictive modeling.

All factors included in a regression or predictive model should be “independent” of each other, meaning they are not highly correlated. This can cause incorrect calculations of regression coefficients and p-values for statistical analysis and incorrect machine learning predictions. We will discuss later how the Correlation widget can be used to identify highly correlated predictors.

  
![](images/image-XLJ2QYRB.jpg)  

Figure 2.25 One-hot encoding

  

“Dependent” variables in a model are correlated at some level. If they are 100% correlated with each other, that means that you can predict one factor with the other. For example, we would not want to have two separate columns in a data file that states: “Cancer diagnosed” and another separate column that states: “No Cancer diagnosed” since they are the opposite of each other and are perfectly correlated. We get around this problem and the dummy variable trap by just creating one column that states: “Cancer diagnosed” and we place a zero (no) or a one (yes) below that column header. The second column we deleted was redundant and unneeded information. In this previous example, we reduced two columns by 1 column referred to as the “n-1” procedure. No matter how many designations we have in a categorical column, we need to reduce the number of dummy variable columns by one to get around the problems it may cause.

Orange offers one option to create one-hot encoding (#1), which can create the dummy variable trap, and two options (#2 and #3) to deal with this categorical feature problem, as shown on the options tab for the Continuize widget in Figure 2.26. Option #2 (First value as base) means it selects the first value alphabetically as the base, so the others appear in the new columns. Option #3 (Most frequent value as base) means it selects the most frequent categorical value as the base, so the others appear in the new columns. Options 2 and 3 are also referred to as “dummy encoding” or “n-1 encoding”.

  
![](images/image-0FFBMP12.jpg)  

Figure 2.26 Three dummy variable options in the Continuize widget

  

[Figure 2.27 shows what the original data set looks like, as the three options for creating dummy variable options in Orange with the Continuize widget. In this example, the functional impairment levels (A - low, B - mid, and C - high level) for home healthcare patients are shown before and after they were broken out as dummy variables. Figure 2.28 shows the Orange widget arrangement required to access these outputs.](#content0050.xhtml)

The other issue with one-hot encoding is that it can add many new columns to the dataset, which could lead to a more complex model and overfitting.

  
![](images/image-QDJBJ4FL.jpg)  

Figure 2.27 Before and after views of categorical variable rearrangements in the data tables

  
![](images/image-05M4G7FZ.jpg)  

Figure 2.28 Orange widget arrangement required to create dummy variable columns

  
![](images/image-M3R8MBB3.jpg)  

Figure 2.29 Group by workflow

  

#### 2.2.9 Group Calculation Operations

  

If you have similar numerical data points (e.g., hemoglobin) on the same patient you may choose to take the average or mean that can be achieved with the Group by widget. For categorical data, you may opt to use a pivot table. Figure 2.29 shows how an example was created for grouping analysis for diabetes data. The Rank widget was added to the workflow so we knew the top-ranked factors. In this case, we were interested in a grouped focus on the top four ranked factors.

The Group by widget offers options to calculate various statistics for each factor. A Kaggle Sleep study dataset was used to display this Orange analysis feature.³⁶ As shown in Figure 2.30, the mean was the only statistic requested for the top four factors, and all other factor aggregations were left blank. The Data Table widget connected downstream shows the mean results for the chosen top four for Insomnia, None and Sleep apnea, as shown in Figure 2.31.

  

#### 2.2.10 Feature Splitting

  

Splitting date and time would be an example of feature splitting to improve the modeling by offering separate analysis of the dates for trend analysis, days of the week for stratified analysis, and separate times of the day break outs for trend and pattern analysis. Splitting first and last names is another example. All of these examples of feature splits can also be easily done in Excel before uploading the data into Orange. Here are some common feature splitting and extraction examples:

[•Extracting Dates - once the dates are in the same format other considerations may be useful in the analysis. You may want to create separate columns for year, month, and day of the week. You may want to create a new column for the time period between a specific date and the current date. Lastly, you may need to know whether this is a weekday or weekend, and you may need the time of day in the analysis.](https://medium.com/p/3a5e293a5114#8068)

•Location - a dataset might include addresses, counties, states, regions, zip codes, or latitude/longitudes (lat/long). A decision must be made as to what level of location is needed. Do you need to be as specific as lat/long or will a region or zip code be adequate? Geocoding will be discussed in a later chapter which takes advantage of such additional location data in datasets.

  

#### 2.2.11 Feature Scaling

  

Feature scaling refers to placing numerical variables on the same scale which helps algorithmic computation and is mandated by some algorithms, such as linear regression, logistic regression, artificial neural networks, clustering algorithms, and K-means. For example, age and income have very different scales and some algorithms may favor larger numbers in assessing which features are most important. Figure 2.32 shows the numerical feature scaling options available in Orange with the explanations for these options listed below that figure.

  
![](images/image-JX920UCM.png)  

Figure 2.30 The Group by widget options

  
![](images/image-E0D1MFER.png)  

Figure 2.31 The result in the Data Table widget shows the results of the Group by widget selections

  

1\. Do no transformations on the data.

2\. Standardize the data so that the mean is 0 and the variance (std dev squared) is 1.

3\. This option centers the data, so the mean is zero.

4\. Scale the data so that the variance (std dev squared) is 1. The shape of the distribution does not change.

5\. Normalize to interval \[-1, 1\] (aka: mean normalization): This method scales values such that the mean value is 0 and the std. dev. is 1. Formula: New value = (value – mean) / (standard deviation)

6\. Normalize to interval \[0, 1\] (aka: span/min-max normalization): This method converts each data value to a value between 0 and 1. Formula: New value = (value – min) / (max – min).

[Figure 2.33 shows a box plot for the top four numerical predictors for the diabetes data in JASP. The dots shown in the following box plot graphics are outliers while the white horizontal line in the dark box is the median. As we can see, the scales are quite different for each of the four predictors.](#content0053.xhtml)

  
![](images/image-INJZFLMT.jpg)  

Figure 2.32 Numerical scaling options in Orange

  
![](images/image-8PKU7VGS.jpg)  

Figure 2.33 Numerical scaling option #1: Non-transformed data

  

[Figure 2.34 shows how the six previous re-scaling options affect the right-skewed glucose values. As can be clearly seen, the distribution shape is unaffected by re-scaling, but the min-max ranges have dramatically changed based on the chosen option.](#content0053.xhtml)

[Figure 2.35 shows boxplots with option 3 to center the data at or near zero.](#content0053.xhtml)

  
![](images/image-WM6QYP1L.jpg)  

Figure 2.34 The six different rescaling options have no impact on distribution shape

  
![](images/image-5J9NJM9M.jpg)  

Figure 2.35 Numerical scaling option #3: Center data

  

[Figure 2.36 shows boxplots for option 4 to scale to a variance of one.](#content0053.xhtml)

This section was started to show how to create uniform scaling for all numerical predictors. The only numerical transformation options in Orange that can achieve that for all four factors are options 5 and 6, which both scale the data to specific predefined intervals. So now we must determine which of these two scaling options is best for the model performance. Experimentation is the only best way to answer that question. However, it might make sense to use option 6, which normalizes the data in an interval between zero and one. Keeping all predictors in a model on the same scale is advantageous for model performance.

Figures 2.37 and 2.38 show boxplots for the four numerical predictors after they have been numerically scaled with option #5: Normalize to the interval \[-1, 1\] and with numerical scaling with option #6: Normalize to the interval \[0, 1\]. These last two scaling options ensure the scales are within the same range.

As previously noted, certain analysis techniques and ML algorithms are very sensitive to big differences in factor scaling differences, except tree-based algorithms, since they are more interested in determining specific cut points from which to partition the data.

  
![](images/image-0TM94IYK.jpg)  

Figure 2.36 Option 4 scaling to a variance of one

  
![](images/image-WGG5150O.jpg)  

Figure 2.37 Numerical scaling option #5: Normalize to the interval \[-1, 1\]

  
![](images/image-IMB3D8FT.jpg)  

Figure 2.38 Numerical scaling option #6: Normalize to the interval \[0, 1\]

  

Unfortunately, there are no conclusive ground rules that can guide analysts on which of these data transformation methods will create the most accurate models. Experiments with the various data transformation options are required to determine which transformation creates the best model. This additional experimental analysis work should not be viewed as a manageable burden but rather as a great opportunity to gain better insights to improve business outcomes.

  

2.3 UNIVARIATE, BIVARIATE, AND MULTIVARIATE ANALYSIS

  

  

Let us first introduce some important descriptive statistics concepts

The measure of Central Tendency describes the center of your data. There are three measures for the center shown below:

•Mean is the average of all the numbers in a defined group. For example, the mean of (3, 5, 7, 9, 11) is (3+5+7+9+11)/5 = 7.

•Median is the center value of a string of data. For example, the median of (3, 5, 7, 9, 11) is 7. Note that the data is not normally distributed if the mean and median are substantially different.

•Mode is the most frequent observation. For example, in the dataset (0, 0, 1, 1, 1, 1, 2), 1 is the mode.

The measures of spread in a data set are as follows:

•Range includes the numbers between the minimum and maximum. For example, for (3, 5, 7, 9, 11), the range is 11-3 or 8.

•Variance measures how far the data point is from the mean. Find the difference between each data point and the mean, square them, sum them up, and take the average.

•Standard deviation is the square root of the variance.

Univariate analysis means you are exploring a single random variable using standard methods such as:

•Measure of central tendencies: Mean, Median, and Mode ( Feature Statistics widget, Box Plot widget)

•Measure of dispersion: Standard deviation, Variance ( Feature Statistics widget, Box Plot widget)

•Measure of tailedness/skewness (Kurtosis): Right-skewed, Left-skewed ( Distributions widget)

•Measure of normality: A statistical test to determine if a dataset matches a bell-shaped “normal” distribution or not. JASP offers such statistical normality tests with the Shapiro-Wilk test.

•Measure of frequencies: As shown on a histogram or Pareto chart.

•Visualizations: histograms, Pareto charts, stem and leaf graphs, box plots, pie charts, JASP Raincloud plots, violin plots, etc.

•Simple Hypothesis tests

Bivariate means you are comparing two variables using standard methods such as:

•Scatter plots (Y-X Scatterplot)

•2-factor Hypothesis tests

Multivariate means you are comparing more than two variables using standard methods such as:

•Scatter plot matrix, correlation matrix/heatmaps, BlueSky Statistics Web plots, parallel coordinate plots, nomograms, multi-factor color or symbol coding on scatter plots, JASP Flexplots, and decision trees.

•Multi-factor Hypothesis tests

[Figure 2.39 displays the high-level steps included in data wrangling and exploratory data analysis (EDA).](#content0057.xhtml)

  

2.4 IMPORTANT DATA CHALLENGES

  

  

#### 2.4.1 Curse of Dimensionality

  

A dataset that has approximately 100 or more features or attributes is said to have high dimensionality. High dimensionality leads to model complexity and is known as the “curse of dimensionality.” With so many predictors, the model might not capture all combinations leading to “data sparsity”, leading to overfitting. Also, with high dimensionality, distance measures used by, e.g., k-nearest neighbors and clustering may be affected because they are based on distance and proximity. ³⁷ A rule of thumb is to have at least ten times the number of subjects (instances/rows/patients) as your predictors. For example, if you have ten predictors for a classification scenario, you should have a minimum of 100 subjects. This rule of thumb is often broken in artificial intelligence, where you may have over 100 million parameters but train on less than a million images. High dimensionality can be an opportunity to apply principal component analysis (PCA) and other dimensionality reduction methods. Reducing predictors or features is also known as “feature reduction.”

  

#### 2.4.2 Multicollinearity

  

2.4.2.1. Defining Multicollinearity

  

While you want predictors that correlate with the outcome, you do not want high correlations among the predictors. This is to be avoided, particularly with linear models. For example, if the correlation between two or more predictors (income and education) is very high, do not use both of these in the model since the information from both factors is considered redundant. This high inter-variable correlation of predictor variables is known as “multicollinearity.” Multicollinearity can cause multiple regression models to be overly optimistic and inaccurate, especially for statistical models, but certain machine learning predictive models can also be negatively affected. In classic statistical models, the highly correlated predictors must be removed from the model if the Variance Inflation Factors (VIFs) are above 5. An example of two perfectly correlated predictors would be if two columns were present in a dataset labeled: 1. The percentage of patients who are smokers visiting a doctor per month and 2. The percentage of patients who are non-smokers visiting a doctor per month. In this example, one of the predictor columns can safely be deleted without any information being lost from the model.

  
![](images/image-SMGB2V56.png)  

Figure 2.39 Data wrangling and exploratory data analysis steps

  

Machine learning algorithms, in general, are less sensitive to high VIFs but remember that multicollinearity is not your friend. If you leave highly correlated predictors in your model, the variable importance ranks you create can become very misleading. Some machine learning algorithms are more sensitive to high VIFs than other algorithms so it is a best practice to reduce features with high VIFs before the model screening process starts. For example, Ridge and Lasso regression algorithms are specifically designed to reduce multicollinearity while finding the best balance between underfit and overfit models (regularization). The JASP machine learning model can automatically determine the best regularization level (called lambda in JASP) that creates a model with a low error metric. Orange does not have an automated way to determine the best regularization level. This will be discussed later in Chapter 4. Principal Components Analysis (PCA) creates smaller models with no highly correlated factors while creating new factors that are not highly correlated. A downside to PCA is that the new factors (components) it creates are not easily interpretable. These techniques will be discussed in later chapters in more detail.

[Figure 2.40 provides a schematic visualization of what multicollinearity (correlated dependent predictors) and no multicollinearity (no correlated independent predictors) looks like.](#content0057.xhtml)

An example of No Multicollinearity in a dataset, as visually displayed in Figure 2.40, is where all predictors are truly independent. In this example, The predictors (X1 to X6) have various levels of correlation with the target (Y) variable, depicted by a higher level of overlap with the target variable, but no correlation with each other (no overlapping Xs). This lack of correlation between predictors allows us to identify the unique contribution that each independent predictor may have on the changes in the target variable. The rank of the predictor importance on Y will be clearly defined, interpretable, and explainable to others. We want predictors to correlate (overlap) with the Y target and not each other.

An example of Multicollinearity in a dataset, as visually displayed in Figure 2.40, is where at least some predictors are correlated with each other and are therefore deemed as dependent predictors. This existing correlation between various predictors does not allow us to identify the unique contribution that each dependent predictor may have on the changes in the target variable. Certain ML models can deal with multicollinearity at the expense of model explainability. Certain model use cases may not be concerned with explainability, but they may be important for many other use cases. These predictors (X1 to X6) also have varying levels of correlation with the target (Y) variable, but they also have varying levels of correlation with each other (overlapping Xs). These Xs are referred to as dependent predictors. The rank of their predictor importance for Y is more confusing and complicated to interpret and more difficult to explain to others due to the confounding nature of the predictor variables. This multicollinearity can also harm the accuracy of certain ML algorithms. In Figure 2.40, X1 and X3 separately correlate with X2. X4, X5, and X6 are all correlated with each other. The higher the level of correlation between predictors (overlap), the more redundant the information provided to the model.³⁸

  
![](images/image-LA23CFBC.jpg)  

Figure 2.40 Visual schematic of no multicollinearity and multicollinearity

  

  

KEYPOINT: Multicollinearity is not your friend in machine learning. It may sometimes reduce the accuracy of your chosen algorithm and can hinder your ability to create an explainable variable importance rank for the final variables in your model.

  

  

2.4.2.2. Correlation Analysis Between Predictors

  

Orange offers a Correlation widget that calculates the Pearson or Spearman correlation coefficients between two variables. When the Correlation widget is connected to the Data Table widget, the False Discovery Rates (FDR) will also be calculated and shown for each pair of factors. The Correlation widget is used to determine the correlation between individual predictors and a target variable or between individual predictors. The limitation of correlation analysis is that the correlation coefficients can only be calculated between two variables. A Scatter Plot widget can also be connected to the Correlation widget to visualize the correlations of selected variable pairs of interest.

[Figure 2.41 shows an expanded correlation workflow where the predictor ranks for the target variable can be compared to the correlation levels of predictor pairs of interest with either the Pearson or Spearman correlation coefficients. The Select Columns widget is placed between the File widget and the Correlation widget so that just the predictors will be selected for the correlation analysis in this initial test for multicollinearity.](#content0057.xhtml)

In multicollinearity analysis, we are only interested in investigating the correlation between predictors. It is very common to have several variables correlated with each other when large amounts of variables are collected for analysis. The Correlation widget will test the correlations for every possible combination of factors and list them in a table where the correlation coefficients can be sorted from high to low or low to high. These coefficients range from -1 to +1; negative values refer to negative correlations, and positive ones refer to positive correlations. The following interpretations are generally accepted for the absolute values of correlation coefficients:

•0.00 to 0.09: No correlation or negligible correlation

•0.10 to 0.39: Weak correlation

•0.40 to 0.69: Moderate correlation

•0.70 to 0.89: Strong correlation

•0.90 to 1.00: Very Strong correlation

Keep in mind that these cutoff points listed here to define a degree of correlation are arbitrary, sometimes debated, and should be used with caution. For example, per the definition of cut-off points, a correlation coefficient can be promoted or demoted to a different group with a change of just 0.01 in its value. Such interpretations should be used with caution since there may be a conflict between the theoretical, practical, and clinical or operational significance of those interpretations.³⁹

  
![](images/image-PDJ7VF6V.jpg)  

Figure 2.41 Correlation analysis and visualization workflow

  

•The Pearson correlation coefficient tests the linear relationship between two variables. The correlation coefficient increases (positively or negatively) as the scatterplot relationship between the two variables deviates less from the best fit regression line shown on a scatter plot. A perfect coefficient of 1.0 means that the data would be perfectly aligned with the best fit regression line shown on a scatter plot. The Spearman correlation coefficient increases (positively or negatively) as the scatterplot relationship between the two variables displays a constantly increasing or decreasing line or curve, which does not have to be linear. A perfect coefficient of 1.0 does not mean that the data creates a perfectly straight line on a scatter plot but rather that the data is consistently increasing or decreasing. This coefficient scores the consistency of the direction of the data on a scatterplot and penalizes any changes or inconsistencies in the direction of the line or curve.

•The False Discovery Rate (FDR) is defined as “the expected proportion of false discoveries among the total number of discoveries.” ⁴⁰ This metric has also been described as “weeding out bad data that looks good.” ⁴¹

  

  

KEYPOINT: The Pearson correlation coefficient is higher as the relationship between two variables becomes more linear. The Spearman correlation coefficient is higher if a consistent rising or declining trend between two variables is present, with no reversal in the direction of a rising or declining trendline.

  

  

[Figure 2.42 shows paired and ranked factor correlation outputs for the Pearson correlation coefficients for the body fat percentage dataset predictors in the Correlation widget and additionally the FDR values in the Data Table widget. The body fat dataset can be downloaded from the File-Share tab Chapter 2 folder.²⁴ It can also be found on Kaggle. ⁴² The dataset consists of multiple body measurements such as age, weight, and height with an outcome column “Percent body fat.” These outputs are based on the workflow shown in Figure 2.41.](#content0057.xhtml)

[Figure 2.43 shows scatter plots for the top three ranked paired predictor correlations for the body fat percentage dataset on the Pearson correlation coefficient list. These outputs are based on the workflow shown in Figure 2.41.](#content0057.xhtml)

  
![](images/image-7GV45FBL.jpg)  

Figure 2.42 Pearson correlation coefficient outputs from the Correlation and Data Table widgets

  
![](images/image-G9CTSWHX.jpg)  

Figure 2.43 Scatter plots for the top correlating predictor pairs

  

[Figure 2.44 shows a JASP “correlation plot” that displays all possible scatter plot combinations for all five variables (weight, chest circumference, abdomen circumference, hip circumference, and thigh circumference) with very high Pearson correlation coefficients on a single graph.](#content0057.xhtml)

This graph was created from the JASP Descriptive section > Select desired variables to be charted > Basic Plots > Select Correlation plots.

This graph clearly shows high correlations between these top five variables. If these five variables are all included in a variable rank graphic, the interpretation and explainability of that graphic will be challenging to correctly interpret due to the confounding nature and redundant information included in these variables.

Correlation coefficients are often shown in a heatmap matrix to color-code the correlation values. Shown in Figure 2.45 are Pearson correlation coefficients for just the predictor variables in the body fat dataset. This graphic was created in JASP with the following commands: Regression > Correlation > Select Predictor Variables > Check Pearson r > Check Report significance > Check Heatmap.

  
![](images/image-X86UBLSL.png)  

Figure 2.44 A JASP Correlation plot of the top five correlating predictor variables

  
![](images/image-WJ70VBIW.png)  

Figure 2.45 Pearson r correlation matrix from JASP for the body fat predictors

  
![](images/image-ZCMAP5C0.jpg)  

Figure 2.46 Paint workflow to create correlation scatterplots

  
![](images/image-94YG0GZH.jpg)  

Figure 2.47 Pearson and Spearman coefficient examples that do not increase in tandem

  

Figures 2.47 through 2.49 were based on data created with the Paint Widget to display various Y and X relationships and then calculate their Pearson, Spearman, and FDR values. The Paint Widget allows you to “paint” data and convert the painted data to actual numerical values that can be exported to the Data Table widget for exploratory, educational, and experimental analysis purposes. Figure 2.46 shows the Orange workflow required to create the scatterplots. Figures 2.47 through 2.49 were created to show the similarities and differences between the Pearson correlation coefficients, Spearman correlation coefficients, and the FDR for the Pearson correlation coefficients (P-FDR).

  
![](images/image-6U4QKPGD.jpg)  

Figure 2.48 Pearson and Spearman coefficient examples increasing in tandem with each other

  
![](images/image-N2LYINR8.png)  

Figure 2.49 More Pearson and Spearman coefficient examples increasing in tandem with each other

  

[Figure 2.47 shows examples where the absolute values for the Pearson and Spearman Correlation Coefficients increase from 0.82 and 0.84 to 1.00. In contrast, the absolute values for the Spearman Correlation Coefficients remain constant at 1.00. These are examples where the Pearson and Spearman Correlation Coefficients do not always increase or decrease in tandem.](#content0057.xhtml)

Figures 2.48 and 2.49 show examples where the absolute values for the Pearson and Spearman Correlation Coefficients increase in tandem at slightly different rates.

In summary, the Correlation widget helps to identify correlated pairs of predictors but the real challenge in modeling is to identify predictor correlations with multiple variable considerations which is what the next section covers.

  

2.4.2.3. Variance Inflation Factors (VIFs)

  

What is a VIF? VIFs only apply to continuous variables (1,2,3, …). They do not apply to dummy variables (1,0). VIFs are critical statistical and predictive model metrics. High VIFs in classic statistical models usually require high VIF variable deletions due to the disruption they cause in the accuracy of the resulting regression equation.

There is no agreement in the literature on what VIF level is considered critical. Some say that a VIF of four is critical.⁴³ The most commonly recommended maximum VIF is five or ten.⁴⁴-⁴⁶ We suggest five as the max level of acceptability for a VIF.

Here are some examples of how to interpret a VIF value:

•A VIF of one means that a specific predictor variable in a regression model has zero correlation with all other predictors in the model.

•A VIF of 1.8 means that the variance (the square of the standard error) of a particular variable is 80% larger than it would be if that predictor was completely uncorrelated with all the other predictors in the model. ⁴⁷

•A VIF of four means that a specific variable has an R-squared value of 75% with all other predictors in the model when it is used as the target variable.

•A VIF of five means that a specific variable has an R-squared value of 80% with all other predictors in the model when it is used as the target variable.

•A VIF of ten means that a specific variable has an R-squared value of 90% with all other predictors in the model when it is used as the target variable.

High VIFs in machine learning models may not always be a problem for all predictive algorithms but high VIFs can certainly disrupt the variable importance rank for specific algorithms.⁴⁷ VIFs can be calculated from classic multiple linear regression analysis or logistic regression analysis in JASP but not from machine learning algorithms. The VIF equation for a specific continuous predictor variable is shown below.⁴⁸

  
![](images/image-PQJPLNV6.jpg)  

The R-squared in the equation above is on a scale from zero to one. The R-squared is the analysis result for when any predictor variable (x) in the model is used as the target response, and all other predictors are used as the predictors for that specific x variable. This calculation will have to be repeated for each predictor to calculate its VIF value. The most recommended maximum VIF value in a model is 5. Figure 2.50 shows a wide range of VIF values and their corresponding R-Squared values calculated with the previously shown VIF equation. This graphical conversion chart between an R-squared and a VIF value can be used to quickly determine the R-Squared values between all predictor variables for each predictor variable of interest.

  
![](images/image-D1VZC3K2.jpg)  

Figure 2.50 R-squared to VIF conversion chart

  

A VIF can also be further described as a numerical confusion metric that increases greatly as it becomes more difficult to identify specifics about co-correlated confounding variables. Confounding variables are additional variables that can add confusion to the analysis as an analyst seeks to determine the short list of predictors that correlate to a target variable. We must always remember that the presence of correlation does not guarantee the presence of a cause-and-effect relationship. Understanding the distinction between correlation and causation is crucial for accurate interpretation and analysis of data. It helps avoid making misleading or erroneous conclusions based solely on observed correlations. Here are some examples:

•Higher temperatures drive up ice cream consumption as well as the number of sunburns, but it would be incorrect to conclude that higher ice cream consumption causes sunburns. ⁴⁸

•Let’s say that you determine that mothers who smoke give birth to babies with lower birth weights. Should you jump to the conclusion that smoking causes low-weight babies or collect data on additional variables to determine if other unhealthy diets and lifestyle choices also contribute to underweight babies?

•A statistically significant correlation (p-value < 0.05) exists between the number of human births in a European country and the number of storks in that country. Should we just jump to the conclusion that storks deliver human babies or seek other factors that explain this correlation such as pollution levels, conservation efforts, and other factors in those countries. ⁴⁹

•There is a 99.26% correlation between the per capita divorce rate in the state of Maine and the per capita consumption of margarine between the years 2000 and 2009. ⁵⁰

The previously listed examples are just some of the many confusing and/or false correlations that can arise when a large data mining net is thrown out in the interest of seeking insights into an issue. Domain experts need to be involved in the analysis process of high VIFs and other high correlations between predictors and target variables to protect the analysis from jumping to incorrect and possibly embarrassing conclusions.

High VIFs create confusion and inaccurate Variable Importance Ranks

Higher VIFs provide us with early warning signals that we have a set of predictor variables that are going to lead to confusing predictor correlations and cause-and-effect considerations that need to be unraveled and resolved. Let’s do multiple regression in JASP and look at which individual predictors have high VIFs as we try to sort out what are the most important predictors that individually and collectively correlate to the high levels of body fat percentages in individuals.

JASP commands for multiple regression: Regression> Classic Linear Regression> select Dependent Variable (target) > select Covariates (predictors) >Model > statistics > Check: Estimates > Check: Collinearity diagnostics

Fig 2.51 shows the multiple regression analysis in JASP including calculated VIFs as they relate to which predictors are contributing to body fat percentages in this dataset.

  
![](images/image-KNSCA5RU.jpg)  

Figure 2.51 Multiple regression analysis in JASP including VIFs for the body fat percentage dataset

  

[Figure 2.52 shows the initial regression model run in JASP which has many high VIFs and p-values greater than 0.05 that are inappropriate for inclusion for the model. VIFs below five and p-values below 0.05 are predictors that are predictors that are potentially valuable for the model. The highest VIF in that model is 33.5 for weight in lbs. This means that an R-Squared value of 97% exists when all other predictors in the model are tested together for how well they correlate to weight as a target value. This is an example of excessive multicollinearity. In a purely non-ML statistical analysis scenario, we would start by removing the predictors from the model that has the highest VIF and highest p-values, one at a time. We do this one variable at a time since each time we remove an interactive predictor from the model, all model stats will change, including the VIFs and p-values.](#content0057.xhtml)

[Figure 2.53 shows the model variable importance rank results from the Orange Rank widget using the Univariate Regression scoring method which ranks all predictor variables for how well they individually contribute to body fat percentages. The VIFs are also added to this rank graphic calculated in JASP.](#content0057.xhtml)

As we see from Figure 2.52, the highest-ranked predictors also suffer from the highest multicollinearity (high VIFs) which greatly limits the validity of the variable ranking.

In Figure 2.53 we can see that the original linear regression model on the left with no regularization overfit and multicollinearity controls had five predictors with VIFs greater than five. Lasso regression on the right, with a regularization strength of 0.5 in Orange, reduced the original model of 13 variables to only four with a rank score greater than zero. Nine of the original variables were reduced to a variable rank score of zero which allowed the model and its interpretation to focus on the top four factors that are not highly correlated with each other, as confirmed by their low VIFs. When the VIFs are below 5 on a variable importance rank, we have more reason to believe that rank since it is not distorted by multicollinearity.

Lasso regression in Orange is an option in the Linear Regression and Logistic Regression widgets. Regularization level selections are also available in the Neural Network Widget. Lasso uses L1 regularization which is a technique that reduces the weights of lesser contributing variables and drives some of them to zero to create smaller and more accurate models with much less multicollinearity and accurate variable importance ranks. Lasso regression is well-suited for models showing high levels of multicollinearity as seen in the body fat dataset. As we apply regularization analysis, we leave all of the variables in a model and let the algorithm reduce the magnitude of the coefficients for specific variables to make a simpler model.⁵¹-⁵² Ridge and Elastic Net regression offer similar advantages as Lasso. They will be covered in more detail in later chapters.

  
![](images/image-NV92ISUK.jpg)  

Figure 2.52 Model variable importance rank for the body fat percentage dataset

  

[Figure 2.54 shows the multiple regression in JASP repeated to just include the top four predictor variables that the Lasso regression has identified. We can see that all VIFs for those predictors are below 1.9, all predictor p-values are below 0.05 which is a sign that they are all statistically significant and that the whole regression equation has an R-Squared value of 0.72. This only represents a slight deterioration from the original model with its R-Squared value of 0.749 which was achieved by including all 13 predictors. The reduced model R-Squared value dropped because that model correctly reduced the impact of redundant and confounding predictors.](#content0057.xhtml)

A high VIF gives the whole “team” of predictor variables more credit than they deserve and creates more artificial hype and error in the regression model. VIF analysis and Lasso regression help us to sort out false excitement from real excitement so that we can focus our attention on a smaller model with the most significant predictors. This example offers an insight into the world of confounding and duplicate information variables with high VIFs that can create great havoc in statistical models when high VIFs are present.

Although this situation is not as critical for the success of some predictive models capable of dealing with confusing inputs, this situation can still greatly degrade the accuracy of machine model variable ranks and the explainability of ML models.

Pairwise predictor correlation considerations. In the previous section, we sought to identify multicollinearity by looking at the Pearson and Spearman correlations among pairs of predictors which can only compare two predictors at a time. However, those methods have very limited potential to fully discover multicollinearity when there are more than two predictors in a regression model. There are exceptions to this rule since it is possible that the rank of Pearson correlation coefficients matches the rank of high to low VIFs calculated with JASP. However, the opposite may be true where the rank of Pearson correlation coefficients is almost the opposite for the rank of high to low VIFs calculated with JASP. In other words, the pairwise predictor correlation method is unreliable for telling the full story of multicollinearity for larger groups of predictors. The calculation of VIFs is the gold standard for identifying multicollinearity.

  
![](images/image-DR59HHNU.jpg)  

Figure 2.53 Basic variable importance rank (left) versus Lasso variable importance rank (right)

  
![](images/image-OS598C3J.jpg)  

Figure 2.54 Multiple regression model for just the top four predictors in the Lasso model

  

  

KEYPOINT: The calculation of VIFs is the gold standard for identifying multicollinearity. Pearson and Spearman correlation analysis has limited potential to identify multicollinearity. We suggest that a VIF of five or greater adds more than acceptable levels of multicollinearity to statistical models and may also disrupt some predictive models. In any case, predictors with high VIFs in any predictor variable rank adds confusion, inaccuracy, and explainability issues and need to be addressed.

  

  

Multiple predictor correlation considerations. We can only truly identify the existence of multicollinearity (high VIFs) in a multiple variable regression model when all predictors are considered in the analysis at the same time.⁴³ JASP offers that option in its linear regression analysis section with its “collinearity diagnostics” option. Orange does not calculate VIFs.

  

#### 2.4.3 Data Leakage

  

  

KEYPOINT: Never let any direct, indirect, or subtle information about the test dataset be conveyed to the training dataset since it then only creates overly optimistic predictions that will not generalize well to new unseen data.

  

  

First, it must be pointed out that “data leakage” has been used by many authors to mean data theft or data leaving an organization. There is quite a different definition of data leakage with reference to building a machine learning model. Data leakage is “when information from outside the training dataset is used to create the model.” ⁵³ This is such a serious violation in the world of predictive modeling that it has also been referred to as unintentional “cheating” when careless habits can “leak” information about what is being predicted into the training data set.⁵⁴ For example, the simple careless act of standardizing, normalizing, or otherwise transforming the data prior to a training and test split can “leak” information to the training set about the min/max, averages, and standard deviation of the combined training and test data. These and other careless data preprocessing steps can lead to incorrect assumptions about how well the model will do with unseen data.⁵⁵ Such data leakage is another cause of an overly optimistic model that does not generalize well to new or external data. Data leakage is considered one of the top 10 data mining mistakes. ⁵⁶

In 2022 Kapoor and Narayanan published an article to suggest that data leakage was hurting the reproducibility of many published machine learning articles. According to the authors, early studies showed model superiority using newer algorithms compared to logistic regression, but when data leakage was ruled out, there was no superiority. If code is not shared, there could be data leakage that is undetected. Unfortunately, data leakage guidelines are lacking, which prompted Kapoor and Narayanan to develop a list of known causes of data leakage:⁵⁷

1\. Lack of clean separation of training and test dataset . The test dataset must be separated before preprocessing, modeling, and evaluation. Without early separation, there could be data leakage issues as described below:

a. No separation of training and test data

b. Feature selection on training and test set. Feature ranking should be done after the data is split, not before

c. Duplicates should be removed before the data split since the same data could exist in the train and test datasets

2\. The model uses features that are not legitimate . For example, a proxy for a feature can also cause data leakage. If the goal of a model is to predict hypertension and anti-hypertensive drugs are used as a feature, this represents data leakage because the proxy is related to the outcome. If the model is run on test data that does not contain the anti-hypertensive drug column, the prediction ability is likely to be much worse.

3\. Test set is not drawn from the distribution of scientific interest . For example, you should not test on data from a different patient population than the training data

a. Temporal leakage. The test set should not contain data from before the training set.

b. Non-independence between train and test data. Train and test data should not be on the same patient.

c. Sampling bias in test distribution.

i. Spatial bias is choosing test data from a geographic location but making claims about performance in other geographic locations as well

ii. Selection bias means choosing a non-representative subset of data for evaluation that does not reflect the population of interest ⁵⁸

Kapoor and Narayanan also discuss other shortcomings of machine learning studies in this article, and they include a downloadable data leakage checklist on their website. ⁵⁷

  

#### 2.4.4 Imbalanced Data

  

In Chapter 4 an extensive section is devoted to imbalanced data. It was placed there because many approaches to handling imbalanced data require knowledge found in Chapters 4 and 5. Imbalanced data is extremely common in biomedicine, fraud detection, and in other areas where the class you are interested in is usually the minority. For example, it might be that only 10% of prostate biopsies show cancer so 90% are benign. Furthermore, it is common to have feature imbalance where data for a variable such as gender or race is skewed causing the model to be biased in favor of the majority group. For binary classification models, this creates many problems in interpreting model performance. In a later section, we will discuss what metrics to use and which ones to avoid in the setting of imbalanced data. In addition, we will discuss what tools are in Orange and JASP and elsewhere to deal with imbalanced data.

  

2.5 SYNTHETIC DATA

  

  

#### 2.5.1 Introduction

  

Synthetic data is artificial data that is generated with AI when not enough real-world data is available to train machine learning models. It is not intended to replace test data, which should always be real-world data. It should be used to expand the volume of training data. Synthetic data is a relatively new innovation primarily because other competing methods have not been able to generate realistic data. Artificial intelligence is the catalyst to generate synthetic data. Gartner, the research and prediction organization, had this to say about synthetic data “By 2030, for image and video data, synthetic data will constitute more than 95% of data used for training AI models” and “Through 2030, for data used to train artificial intelligence (AI) models, synthetic tabular data will grow at least three times as fast as real structured data.” ⁵⁹

In healthcare, finance, insurance, cybersecurity and elsewhere there are multiple reasons why synthetic data is appealing:

•Data quality and quantity are both lacking in many fields.

•Artificial intelligence and to a lesser extent machine learning requires large datasets.

•In healthcare, HIPAA regulations severely limit the ability to use and share medical data with any patient identifiers.

•Synthetic data would make research and development requiring medical data much easier.

•It would facilitate sharing clinical trial data with journals, pharmaceutical companies, and regulators.

•There are potential cost savings if synthetic data can augment clinical trials, drug trials, reduce labeling costs, etc.

•Synthetic data does not require special disclosures or IRB approval for research.

•In finance, it could be used for risk modeling and fraud detection.

•In insurance, it could be used for risk assessment, underwriting, and claims analysis.

•In cybersecurity, it could be used to identify vulnerabilities and to simulate cyber attacks.

•Synthetic data could be used to create new educational datasets of satisfactory quality and quantity.

•Synthetic data could augment imbalanced datasets where the target class is imbalanced.

•Synthetic data could potentially improve models and if it would balance features (e.g., gender, race, etc.) as well as classes. This could lead to less model bias and better prediction.

•Synthetic data could be used for “innovative sandboxes.”

  

#### 2.5.2 Synthea

  

In 2017 the Mitre Corporation developed the SyntheticMass project that emulated the healthcare data of the residents of Massachusetts. There are more than 1 million synthetic medical records available and they can be accessed in multiple ways including an HL7 FHIR STU3 API. The data are fictitious, but realistic because they are based on the medical and demographic features of the residents of Massachusetts and also mirror clinical practice guidelines and expert opinion.⁶⁰

There are synthetic datasets ready for download on their website in multiple formats (CSV, FHIR, and C-CDA):

•10,000 and 100,000 patients with COVID-19

•6,357 obese children

•1,000 generic patients

•I million patients

•More data on Google Cloud Console

A significant aspect of the SyntheticMass project is Synthea,™ the downloadable synthetic patient generator with the following features: ⁶¹-⁶²

•Birth to death lifecycle, so there are deceased patients in the datasets

•Longitudinal data

•Configuration-based statistics and demographics (defaults with Massachusetts Census data)

•There are about 90 Modules covering the most common medical diseases and conditions

•The user can customize modules and create their own

•Encounters: Primary Care, Emergency Room, and Symptom-Driven

•File folders created: see below description

•Formats: HL7 FHIR (STU3 v3.0.1, DSTU2 v1.0.2, and R4, C-CDA, and CSV

Synthea will generate the following (16 csv files) as noted:

  

Table 2.6 Synthea files generated

  
![](images/image-I59GH4HJ.png)

  

#### 2.5.3. AI-Generated Synthetic Tabular Data

  

Earlier approaches for generating synthetic data revolved around anonymization, pseudo-anonymization, and statistical methods. These have largely been replaced by AI. There are a variety of artificial neural network types that are capable of generating synthetic data. This means not only can tabular data be generated but also complex images. In this section, we will only discuss synthetic tabular data. The most common AI methodology is generative adversarial networks (GANs). Other methods include autoencoders, long short-term memory (LSTM) networks, and ensembles. To date, eight vendors are capable of generating synthetic tabular data, but the list is growing.

  

2.5.3.1 How to Determine if Synthetic Data is Accurate?

  

The most pressing question is how close do synthetic data simulate the original (real) data? Most authorities judge synthetic data by three criteria:

1\. Resemblance (fidelity) - how close does synthetic data resemble real data?

2\. Utility - does a model created using synthetic data produce similar results compared to real data?

3\. Privacy - how different is synthetic data compared to real data, based primarily on distance?

Resemblance: There are a variety of statistical tests for resemblance. The following is only a partial list of metrics to compare real data with synthetic data:

•Accuracy is largely determined by statistical testing. For example, the mean cholesterol for original and synthetic data should be similar enough that the p-value is > .05.

•Use t-tests or Wilcoxon Rank Signed Sum Tests for continuous data and chi-square testing for categorical data.

•Pearson and Spearman correlations should be similar.

•Scatter plot relationships between variables should be similar.

•Confidence interval overlap.

•Mutual information (Orange Rank widget) to show the relationships between independent and dependent variables should be similar.

•Distributions should be similar. Kolmogorov-Smirnov tests are used to compare distributions.

The amount of data synthesized is likely important. In the study by Benaim et al. they determined that moderate-sized data (300-700 subjects) may provide only moderate accuracy, so more data is better. ⁶³-⁶⁷

  

2.5.3.1 Comparison of Synthetic Data with Original Data

  

Using the synthetic data generator Gretel, data was generated to simulate the heart disease prediction dataset using artificial neural networks and long short term memory (LSTM) methodology. This platform can also generate synthetic data using a generative adversarial network (GAN).⁶⁸

[Table 2.7 displays a comparison of the original data with synthetic data. The difference between the two datasets was not statistically significant (p >0.05) for these numerical variables as determined by the Wilcoxon Rank Signed Sum Test. ⁶⁹](#content0063.xhtml)

[Figure 2.55 displays histograms of the numerical values of real vs. synthetic data, using the heart disease prediction dataset. The results are very close so there is good resemblance.](#content0063.xhtml)

Utility: Figure 2.56 displays the classification model performance using logistic regression on real heart disease prediction data vs synthetic data. Once again, the results are similar so there is good utility. In addition, the synthetic data and real data were both evaluated using the hold-out data of 90 patients that were split initially 70/30. The test results on the real data and synthetic data were highly similar. This is known as TSTR or train on synthetic, test on real data.

  
![](images/image-2831BIBC.png)  

Figure 2.55 Histograms of numerical variables using real and synthetic data

  
![](images/image-DQFIJLWS.png)  

Figure 2.56 Classification performance of real vs synthetic heart disease prediction datasets

  

Table 2.7 Comparison of numerical values in the real and synthetic datasets

  
![](images/image-50XFSFPX.png)  

Privacy: a privacy report is generated by all synthetic data generating platforms. In Gretel, a privacy protection level is reported and several options are available to maintain privacy:

•Outlier filter to ensure no synthetic record is an outlier

•Similarity filter to ensure no synthetic record is too similar to a training record

•Privacy filter can be set to auto

•Overfitting option to ensure the model training stops before overfitting occurs

  

2.6 DATA SCIENCE EXPERIMENTS (DSEs)

  

  

  

KEYPOINT: The grand purpose of data science experiments (DSEs) is to test all possible data preparation, modeling, and optimization options as part of the scientific pursuit to create the most accurate and useful predictive models. Each DSE should have a well-formulated hypothesis to be tested with careful documentation of the experimental results and the datasets used to create those experiments. Third-party reproducibility should be enabled. When in doubt, experiment.

  

  

#### 2.6.1 Experimental Thinking in Data Science

  

Experimental thinking is a fundamental aspect of the scientific method, which is widely used in data science to test various hypotheses and gain a deeper understanding of complex problems and data analysis systems. By conducting experiments and analyzing the results, data scientists can make informed decisions to improve the accuracy of their predictive models. To be effective in this field, it is essential for data scientists to have strong experimental thinking skills and the discipline to follow a logical process, carefully documenting all steps taken to design and conduct experiments that yield reliable and valid results.

[Figure 2.58 reiterates the 8-step data science that has been previously shown but this version of that process shows the reality for the non-linear nature of this general process. It is important to note that as there are great benefits in following strict guidelines and best practices, it needs to be understood that the data science process is very dynamic, iterative, different for each dataset, and sometimes circular. The priority for this process is to continually improve the accuracy of the model which requires great flexibility to deal with surprises and needed adjustments to meet the goals of an individual experiment or large project.](#content0069.xhtml)

The step sequences of the upwards and forward pointed arrows in Figure 2.57 show the logical progression towards the creation of a predictive model while the backwards facing arrows show the reality of correction, refinements, and improvements that are also necessary to meet modeling goals.

  
![](images/image-3T6M7XEP.jpg)  

Figure 2.57 The dynamic and non-linear nature of the data science DISCOVER process

  

AutoML (automated machine learning) is the process of automatically determining the best algorithm and model for a specific data science project. We do not suggest or recommend that Auto-ML replace the work of data scientists or other data analysts. However, Auto-ML can be used as a competitive benchmark of performance that analysts should attempt to improve upon. Using AutoML as a competing second option may be the safest approach to compare your own modeling results against AutoML results. This approach may also help those analysts with lower levels of ML expertise to build more confidence in predictive model building.

Auto-ML is now an established field in data science.⁷⁰ The appeal for AutoML applications is that they may be used by organizations with lower levels of machine learning expertise as a rapid method to build predictive models. AutoML systems were created to reduce the workload on data scientists so that domain experts without specific ML expertise can create ML models. ⁷¹

Kaggle has run many AutoML versus human competitions and AutoML contestants (without any human help) have always ranked in the top 10% or 25% of contestants.⁷²-⁷³

Fully relying on AutoML features does have its risks, according to a Harvard Business Review article that stated: “Haphazardly applying automated machine learning without proper expertise, contextualization, and data complementarity is unlikely to produce the desired results.” ⁷⁴ AutoML should never be seen as a substitute for the need to understand the fundamentals of data science since the nuances in the data can lead to issues or success in the modeling process. Others have noted that the end-to-end automation of AutoML is more of a goal than a reality. AutoML tools are especially challenged in addressing model fairness, explainability, and bias issues.⁷⁵

There are many experiments that data scientists can conduct on data to compare the performance of different models and techniques. Here is the suggested sequence of the main experiments that can be run during the data collection, planning, and modeling phases. It should be noted that this is just one possible sequence of experiments since considerations for each data set may be different, there will be some back and forth, and some steps may be skipped entirely. Here are just some examples of data science experiments:

1\. Determine which data split and cross-validation options create the best-performing models.

2\. Ensure that pre-processing and feature engineering does not create a data leakage situation.

3\. Determine which data Imputation methods improve model performance while not disrupting data visualizations.

4\. Determine which data augmentation/synthesizing method for low-volume datasets and balancing of predictor features performs best.

5\. Determine if additional predictors or calculated features improve model performance.

6\. Determine which class balancing methods such as SMOTE, ADASYN, a combination of up-sampling and down-sampling, and other methods creates the best models.

7\. Determine if dummy n-1 encoding of categorical variables improves model performance.

8\. Determine the impact of different regularization levels

9\. Determine if data re-scaling (normalization and standardization) and/or power transformations improve model performance.

10\. Determine how outlier elimination effects model performance.

11\. Determine how dimensionality reduction (PCA, regularization with Ridge and Lasso, multicollinearity resolution) affects model performance.

12\. Determine which algorithms and algorithm options create the best models.

13\. Determine if hyperparameter tuning improves model performance.

14\. Determine if ensemble model building, stacking of models, and calibrated learners improve model performance.

  

#### 2.6.2 Nine Steps for Creating Effective Data Science Experiments

  

There are many steps involved in conducting data science experiments, and the specific steps may vary depending on the specific goals and methods of the experiment. In general, the main steps for each data science experiment may include the following:

1\. Create research questions, hypotheses, and/or well-defined problems to be addressed. These steps will help guide the design of the experiment and ensure that the effort invested is aligned with the desired outcome.

2\. Define experimental scope: Determining the experimental scope, including the effort-benefit ratio, algorithms and options, performance metrics, and methods to be compared.

3\. Experimental design: Create and document the Orange or JASP workflow to be used for the experiment.

4\. Sample size considerations: Determine the appropriate sample size for an experiment to ensure reliable and accurate results. It is important to consider the number of stratified groups to be individually analyzed when determining the sample size.

5\. Collect the data: Gather the data needed for the experiment, either through sampling or by accessing existing datasets.

6\. Clean and preprocess the data: Prepare the data for experimental analysis by cleaning and preprocessing it as needed. Note that some algorithms in Orange have default pre-processing options that may need to be modified to suit the specific needs of the experiment.

7\. Clearly document all of the individual experiments that will be required for the DSE

8\. Documenting experimental results: Develop a standard scorecard matrix to document and capture the results of each experiment in relation to the selected performance metrics. Be sure to name and track the specific datasets used for every step and variant of the experiment so that it can be easily reconstructed and repeated to verify results.

9\. Define experiment conclusions and next steps: It is important to remember that the conclusions drawn from an experiment may not apply to other datasets. The results of an experiment are specific to the data samples and conditions under which it was conducted and may not generalize to other datasets, populations, or contexts.

10\. Create a final data science experiment report and communicate the results: This involves the detailed documentation for the experiment’s findings in a clear and concise manner. All experiments should be documented in a manner that third parties can reproduce the experiments and compare results.

  

#### 2.6.3 Data Science Experiment Complexity Level

  

The purpose of Data Science Experiments (DSE) is to enhance the predictive accuracy of models. DSEs can vary in complexity, with Level 1 being the most basic and Level 5 being the most complex. The general levels of complexity can be defined as follows:

Level 1 DSE: A single-factor experiment using basic algorithms and default performance metrics.

•Example : Determine which of the eight algorithms has the best mix of model performance metrics shown in the Test and Score widget and Confusion Matrix widget.

Level 2 DSE: The same as Level 1 but with a wider range of algorithm options and performance metrics.

•Example: Determine which of the twelve different algorithm options has the best performance metrics shown in the Test and Score widget, Confusion Matrix widget, AUC for the ROC and Precision Recall Curve.

Level 3 DSE: The same as Level 2 with the additional assessment of Pearson correlation heat maps, distribution plots, scatter plots, box plots, confidence interval plots, calibration plots, and other assessment options.

•Example: An assessment will be made to see how a dataset of 500 patients compares to an expanded dataset created with a synthetic data service for 5000 synthetic patients.

Level 4 DSE: This level of experimentation includes all previous assessments while exploring additional factors with its options to determine which option has the best model performance results.

•Example: Determine the best performing imputation method for missing data, threshold shifting, class balancing method comparisons, ensemble model building, model stacking, and many other modeling options with the potential to improve model performance.

Level 5 DSE: This final level of complexity could focus on squeezing a little more performance out of the predictive model by tuning the hyperparameter settings for the best-performing algorithm. If other algorithms are close contenders for the top position, they may also be candidates for this hyperparameter optimization (HPO) experimentation. This experiment has two options: 1) just change one hyperparameter at a time with random or set interval changes of the hyperparameter or 2) Set up a statistical Design of Experiments (DOE) that will test a wider variety of hyperparameter changes at the same time to see how this impacts model performance.

•Example: Let us say that we want to explore a high and low parameter value relative to the default settings for each of the four hyperparameter settings available for the Tree widget. This experiment would collect the performance metrics resulting from these experiments to see how the hyperparameter setting changes interacted with each other to affect model performance.

  

#### 2.6.4 Algorithm Preprocessing Defaults

  

Before planning an experiment, be fully aware of the preprocessing defaults of each algorithm since they may conflict with the goals of an experiment. Figure 2.58 shows the default setting for each algorithm available in Orange. To remove default preprocessing, connect an empty Preprocess widget to the learner. Removing the default processing will then allow you to customize the preprocessing settings. However, be aware that the removal of all default processing settings may have unintended consequences during modeling.

  

#### 2.6.5 Algorithm Compatibility with Other Widgets

  

Data science experimenters should also be aware of the following compatibility scenarios between algorithms, the Rank widget, and the Calibrated Learner widgets which may also be the focus of experiments. Figure 2.59 notes if the Rank widget and the Calibrated Learner widgets can accept signals to be processed from various Orange algorithms. SVM is not included.

The Rank widget offers predictor scoring information with its own built-in scoring methods but it can also allow a specific learner algorithm to show its own predictor rank assessment if they are compatible.

  
![](images/image-3SVFBGGS.jpg)  

Figure 2.58 Preprocessing default settings for all Orange Algorithms

  
![](images/image-TCZZFDUM.png)  

Figure 2.59 Algorithm compatibility with the Rank and Calibrated Learner widgets

  

The Calibrated Learner widget is available for binary classification tasks. This widget may offer improved learning with probability calibration and decision threshold optimization for other binary classification algorithms. Experimenting with this option is the only way to determine if modeling performance improvements can be achieved or not.

  

#### 2.6.6 Data Science Experiment Complexity Level Examples

  

As previously noted, there are five levels of data science experiments that we will discuss in this book. This section will provide examples for each of those experimental levels. If a model’s performance appears exceptionally high and in no need of further optimization, reconsider; it might be a ‘too good to be true’ scenario, potentially due to data leakage or other errors.

It is important to note that the process of building a predictive model often involves conducting multiple data science experiments (DSEs) in order to optimize the model’s accuracy and performance. These experiments can vary in terms of discipline, documentation, style, and depth, and it is important to approach them with a thorough and systematic approach. The examples provided in this section are meant to serve as inspiration and guidance for the development of effective DSEs in the optimization of predictive models.

It is essential to address issues such as missing values, imbalanced classes, and low data counts early on in the modeling process, as these issues can significantly impact the performance and reliability of your predictive model. One effective approach is to prioritize conducting experiments that address these challenges as the first experiments to be run on your dataset. These experiments might involve applying techniques such as missing data imputation, class balancing methods such as oversampling and/or undersampling, and data augmentation techniques like synthesizing additional data points or generating new features. By addressing these issues, you can establish a strong foundation for your model and set the stage for further experimentation to improve the accuracy and reliability of the predictive model.

It is beneficial to have a collection of example workflows, specifically designed for data science experiments (DSEs), as a reference when conducting your own experiments. These workflows can serve as a guide for the discipline, documentation, style, and depth of your DSEs, and can be used to ensure that you are approaching your experiments in a systematic and thorough manner. You may want to consider creating and compiling a collection of these workflows, specifically tailored to your own needs and preferences, for easy future reference to optimize predictive models. Additionally, it may be helpful to review the example workflows provided in this section for further inspiration and guidance.

  

2.6.6.1. Example of a Level 1 Experiment

  

The purpose of this Level 1 experiment example is to determine which of the eight classification algorithms available in Orange provides the best model performance metrics to predict diabetes. This is a classification problem since the target is 1/0 (yes/no) for diabetes. Only 15% of the patients in this dataset have diabetes so the dataset is considered to be imbalanced between classes. There is no missing data in this dataset.

  
![](images/image-CC1AUODR.jpg)  

Figure 2.60 Orange workflow for a Level 1 experiment

  
![](images/image-BSBHHN54.jpg)  

Figure 2.61 Performance metric matrix for a Level 1 experiment

  

The Orange workflow for this experiment is shown in Figure 2.60. The performance metrics for this experiment are shown in the Test and Score widget for the training data in Figure 2.61.

The performance metrics shown in Figure 2.61 can be sorted from high to low or low to high by clicking on the header of each metric. Not all performance metrics available in Orange are shown in the Test and Score widget matrix. For example, the AUC values for the Precision Recall curve is shown in the Performance Curve widget. It should be noted that there are a total of 24 evaluation metrics available for Binary Classification.⁷⁶ However, this Level 1 experiment is just focused on the default metrics that are available in the Test and Score widget. The Data Sampler widget in the experiment workflow provided a 70/30 Train / Test Data split with all algorithm preprocessing default settings accepted. To remove the algorithm default preprocessing, connect an empty Preprocess widget to the learner.

If you need to track more model metrics than the Test and Score widget can display, you can create your own customized performance metric matrix in an Excel document which allows color-coded conditional formatting and ranking for each individual metric of interest. Figure 2.62 shows a template example of a customized model performance metric matrix.

The algorithm option ranking template shown in Figure 2.62 is a fictitious example that shows fake numbers in the matrix that were just added to show how the color coding can be added in the matrix to show the difference between high and low metric values. The fictitious numbers in this template should be replaced with real results from the Level 2 experiment when available. The names for the model metrics should also be updated in the template when they are set for the experiment.

  
![](images/image-Q3UYRHVW.png)  

Figure 2.62 Customized performance metric matrix template to display expanded level 1 model metrics

  

2.6.6.2. Example of a Level 2 Experiment

  

The purpose of this Level 2 experiment is to add available options for each of the eight classification algorithms available in Orange for the same diabetes classification dataset as shown in the previous example. This experiment will create a separate Orange widget for each of the algorithm options so that their results can be seen separately in the performance metrics matrix. All other settings for this experiment are the same as in the last example except for the fact that we now have 17 algorithm options to compare with each other. In the first experiment, we only had eight algorithm options to compare with each other. Figure 2.63 provides a schematic summary of the content of a Level 2 experiment when compared to a Level 1 experiment.

The experimental additions are explained below:

The Logistic regression workflow now has two separate widgets that were created to show the two separate options (Lasso and Ridge) within the Logistic regression widget (See Figure 2.64). This allows us to view the individual performances of the Lasso (L1) and the Ridge (L2) Regularization options in the Test and Score widget (See Figure 2.65).

The Gradient Boosting workflow now has four separate widgets to show the individual performances for each of the four gradient boosting methods:

•Gradient Boosting (scikit-learn)

•Extreme Gradient Boosting (xgboost)

•Extreme Gradient Boosting Random Forest (xgboost)

•Gradient Boosting (catboost)

The Neural Network workflow now has three separate options to show the individual performances for each of the three weights as model criteria available within the Neural Network widget:

•L-BFGS-B: an optimizer in the family of quasi-Newton methods

•SGD: stochastic gradient descent

•Adam: stochastic gradient-based optimizer

The KNN workflow now has four separate options to show the individual performances for each of the four distance parameter metrics available within the KNN widget:

•Euclidean (“straight line”, distance between two points)

•Manhattan (sum of absolute differences of all attributes)

•Maximal (greatest of absolute differences between attributes)

•Mahalanobis (distance between point and distribution).

The Orange workflow for this experiment is shown in Figure 2.64. The performance metrics for this experiment are shown in the Test and Score widget, shown in Figure 2.65.

Unfortunately, not all of the renamed widgets are listed in the Test and Score performance metric matrix with that new name so care must be taken when determining which algorithm options are associated with which experimental results are shown in the matrix.

If you need to track more model metrics than the Test and Score widget can display, you can create your own customized performance metric matrix in an Excel document which allows color-coded conditional formatting and ranking for each individual metric of interest. Figure 2.66 shows a template example of a customized performance metric matrix.

The algorithm option ranking template shown in Figure 2.66 is a fictitious example that shows fake numbers in the matrix that were just added to show how the color coding can be added in the matrix to show the difference between high and low metric values. The fictitious numbers in this template should be replaced with real results from the Level 2 experiment when available. The names for the model metrics should also be updated in the template when they are set for the experiment.

  
![](images/image-0NWJFMUQ.jpg)  

Figure 2.63 The additional content in a Level 2 experiment compared to a Level 1 experiment

  
![](images/image-MPC9JBX4.jpg)  

Figure 2.64 Orange workflow for a Level 2 experiment

  
![](images/image-JVS76I20.jpg)  

Figure 2.65 Performance metric matrix for a Level 2 experiment

  

2.6.6.3. Example of a Level 3 Experiment

  

The purpose of this Level 3 experiment is to add additional assessments for the chosen experiment such as Pearson correlation heat maps, distribution plots, scatter plots, box plots, confidence interval plots, calibration plots, and other assessment options. This may be a mix of quantitative and qualitative assessments.

[Figure 2.67 provides a schematic summary for the content of a Level 3 experiment when compared to a Level 1 and Level 2 experiment.](#content0070.xhtml)

  
![](images/image-WLHEW6PD.png)  

Figure 2.66 Customized performance metric matrix template to display expanded level 2 model metrics

  
![](images/image-23E4GRAN.jpg)  

Figure 2.67 The additional content in a Level 3 experiment compared to a Level 1 experiment

  

2.6.6.4. Example of a Level 4 Experiment

  

The purpose of this Level 4 experiment is to explore a new factor with multiple levels of options to determine which option has the best model performances. Here are some examples of additional experiments that can be run :

•Determine which data imputation method has the best performance.

•Determine which data class balancing method has the best performance.

•Determine which data augmentation method has the best performance.

•Determine which training and test data splitting/cross-validation method has the best performance.

•Determine which data re-scaling method offers improved performance.

•Determine if data re-scaling for each cross-validation fold offers improved model performance.

•Determine if model stacking offers improved model performance.

•Determine if the addition of the Calibrated Learner widget offers improved model performance.

•Determine what algorithm and regularization settings reduce multicollinearity to produce accurate and useful predictor variable ranks.

•Determine if newly added features rank high on the predictor ranking without increasing multicollinearity.

•Determine which model explanations resonate best with non-technical stakeholders

•Determine if predictor ranks and modeling conclusions are valid for all stratified groups in the dataset.

[Figure 2.68 provides a schematic summary for the content of a level 4 experiment with an expanded scorecard to show the model performance changes when no data imputation is used compared to various data imputation options.](#content0070.xhtml)

  

2.6.6.5. Example of a Level 5 Experiment

  

This final level of complexity focuses on squeezing more performance out of the predictive model by tuning the hyperparameter settings for the best-performing algorithm. If other algorithms are close contenders for the top position, they may also be candidates for this hyperparameter optimization (HPO) experimentation. This experiment has two options: 1) just change one hyperparameter at a time with random or set interval changes of the hyperparameter or 2) Set up a statistical Design of Experiments (DOE) that will test a wider variety of hyperparameter changes at the same time to see how this impacts model performance. Automated systems also exist to conduct the tedious task of hyperparameter tuning but they are not available in Orange or JASP. ⁷⁷

  
![](images/image-SKJAXLCR.jpg)  

Figure 2.68 The additional content in a Level 4 experiment compared to a Level 1 experiment

  

[Figure 2.69 shows the hyperparameter settings that can be experimented with in this level of experiments. The darker-colored boxes show experimental settings that have not been presented previously. The lighter-colored boxes are settings previously presented in Level 1, 2, or 3 experiments. A detailed description of all hyperparameters is available in Orange in the help file section for each algorithm.](#content0070.xhtml)

[Figure 2.70 shows an example of a simple HPO experiment where two of the five hyperparameters are being changed to see how the training data model metrics change for those non-default changes. The shaded boxes in Figure 2.70 show the worst and best metrics that are the result of the experiment.](#content0070.xhtml)

As previously mentioned, statistical Design of Experiments (DOEs) can also be used to test a wider variety of interactive hyperparameter changes simultaneously to see how this impacts model performance. JASP offers DOE experimental setups under its Quality Control. BlueSky Statistics supports many more DOE design setup and analysis options than JASP. Further discussions about how DOEs can support HPO efforts are out of the scope of this book since it is a very complex and specialized topic that only applies to very advanced data science efforts.

  
![](images/image-0HDWAKAG.png)  

Figure 2.69 Hyperparameter settings available for Orange algorithms

  
![](images/image-EBBJAZD4.jpg)  

Figure 2.70 An example of a small hyperparameter optimization experiment

  

2.7 ORANGE DATA AND TRANSFORM MENU WIDGETS

  

  

The “Transform” category is the second icon from the top of the vertical widget group on the left side of an Orange canvas. The widget group names can be seen by hovering your mouse over them. Multiple widgets are necessary and useful in the data manipulation, transformation, data visualization, and other sections of the Orange software toolbox. We will cover only the most significant ones. Right-click on any widget and select Help for more information about the widget, its suggested workflows, examples, and much more. This will also tell you what the acceptable inputs and expected outputs are for each widget.

  

#### 2.7.1 File Widget

  

This is where you can upload your own data, image files, text, or download data from the Internet. Alternatively, you can insert the URL for a website, or a Google Sheet, and the data will be uploaded. This widget is already loaded with 6 documentation datasets for practice purposes. If you are loading a new dataset, do not forget to check to be sure that the correct Type and Role designation that Orange has estimated for your dataset columns is correct. For example, the Role section offers a drop-down menu to select one of the following options: Feature, target, meta, or skip (See Figure 2.71). The Type drop-down menu offers the following options: categorical, numeric, text, or dateline (See Figure 2.71). You can change that by selecting the item in the Role column. Lastly, select Apply after making any changes to these settings. There is a CSV File Import widget for more complex CSV files that can be analyzed.

  
![](images/image-81AIU9TE.jpg)  

Figure 2.71 Type and Role options for data columns in the File widget

  

#### 2.7.2 Datasets Widget

  

This widget offers access to Orange datasets (65) covering a variety of topics that are available for practice. It lists size, instances (rows), variables (predictors), target (outcome - numeric or categorical) and tags (e.g., biology), and references (an article related to the dataset). If the target is categorical then you can use these data for classification analysis, logistic regression, and other analysis techniques. If the target is numerical, it can be used for numerical data analysis techniques, linear regression, and many other analysis techniques. These datasets and more are hosted on an Orange website as .tab files.⁷⁸ See Figure 2.72 below for a partial list of the available datasets.

  

#### 2.7.3 Data Table Widget

  

This is where you view the data in a table, like looking at a spreadsheet. You can view but not manipulate data, other than to sort by ascend/descend. If you wonder how your data looks after manipulating it, insert another data table after that data manipulation activity in the Orange workflow. The data table provides summary statistics in the upper left. You can also elect to add color by class (outcome). You can select/click a data point in a graph or confusion matrix and connect it to a data table to see the values for those data points of interest. Note that the right side of this widget is hashed meaning it can be connected to other widgets. You can filter special groups or individual rows by highlighting/selecting rows of interest in the data table and then connecting it to a second data table or a visualization widget displaying the selected rows. Filtered data can also be saved with the Save Data widget.

  
![](images/image-F6TBCDA3.jpg)  

Figure 2.72 Some of the datasets in the Dataset widget

  
![](images/image-997L1HPT.png)  

Figure 2.73 Data table widget

  

#### 2.7.4 Paint Data Widget

  

This widget is used for creating and color-coding data or data points. Any data you “paint” on the X-Y scatter plot matrix will be automatically converted to real data coordinates that can be viewed in an Orange data table connected to the Paint Data widget. Then, any valid Orange analysis options can be run on that data. For example, you could create data clusters with subgroups and then run an analysis. You can connect this widget to a data table and see the exact coordinates of your painted data. Also, you can paint data in a linear fashion and use the scatter plot and linear regression widget to evaluate the model. We will use this widget for several exercises. This is an excellent tool for education. See Figure 2.74 for a painted data set with four groups.

[Figure 2.75 shows what happens when you attach the Scatter Plot widget to this Paint Data widget. It clearly shows that although the entire dataset has a downward trending regression line, each of the four subgroups in the data has an upward trend. This is an example of Simpson’s Paradox which is defined as “a phenomenon in probability and statistics in which a trend appears in several groups of data but disappears or reverses when the groups are combined.” ⁷⁹](#content0071.xhtml)

[Figure 2.76 shows how this example of the Simpson’s Paradox can apply to a hypothetical hospital situation where the individual department patient satisfaction scores improve with increased staffing levels but it appears that the whole hospital patient satisfaction scores are in a downtrend as the staffing levels increase.](#content0071.xhtml)

  

#### 2.7.5 Data Sampler Widget

  

This widget can perform the following: a. Split the data into a fixed proportion, e.g., 70% training, and 30% testing. You can set up two connectors as output so that training data can be evaluated separately from test data. (see Figure 2.77) b. Fixed sample size, e.g., 100 instances. The sample with replacement option means a data point can be selected more than once for the created sample. c. Cross-validation (CV) permits you to select e.g.10 subsets (folds) so you train on nine folds and test on one fold. This CV process randomly divides all data into equally sized groups. The model is trained and validated on each fold until all folds have been used for training and validation. The reported results are the average results from each fold. CV helps to reduce overfitting in predictive models. Cross-validation is also part of the Test and Score widget we will use. d. Bootstrap is a technique where you select multiple subsets of the data with replacement and then average the results to estimate a result for the entire population. Many datasets are often highly imbalanced so it is a good idea to ensure that the “stratify sample” option is chosen which will ensure that the train and test datasets get the same proportions of the minority class.

  
![](images/image-FJIME7MG.jpg)  

Figure 2.74 Paint Data widget

  
![](images/image-QR2NDFNI.jpg)  

Figure 2.75 Scatter Plot widget display of the Paint Data example

  
![](images/image-LN1OPLM9.jpg)  

Figure 2.76 Simpson’s Paradox example for a hospital created from the Paint Data Widget

  

To enact the sampling choices discussed above you must select the button “Sample Data” at the bottom. We will cover more about cross-validation in a later chapter. In addition, this widget can over or under-sample the data and we will also cover this option in the classification module with more details. (Figure 2.77)

  
![](images/image-48JBC2HH.jpg)  

Figure 2.77 Data sampler widget

  

[Figure 2.78 displays the Data Sampler widget with the default choice selected to split 70/30 train/test (213/90 patients) randomly. Figure 2.78 displays the file widget connected to the data sampler and then to the test and score widget. You want to be sure that the test and score widget receives both the training and test data. To do that, right-click the link between the data sampler and the test and score widget and choose “reset signal” and connect the remaining data to the test data. See Figure 2.79.](#content0071.xhtml)

The Fixed sample size and Bootstrap options in the Data Sampler widget need further validation before we can recommend their usage.

  

#### 2.7.6 Select Columns Widget

  

This widget is where you select some columns and ignore others for analysis. You can also select “Skip” in the File widget to exclude columns. We will use the Kaggle Latest Data Science Salaries dataset.⁸⁰ For example, we do not need to include the currency for other countries nor do we need to include the employee residence, so they were not included. The other features and the target remain the same. Meta-attributes are included in the dataset but are, for most methods, not considered in the analysis.

  
![](images/image-OHNS0X5R.jpg)  

Figure 2.78 Data Sampler widget workflow

  
![](images/image-HK5LAJMR.jpg)  

Figure 2.79 Edit links options

  

#### 2.7.7 Select Rows Widget

  

This widget allows you to select (filter) some rows and ignore others. In this example, we will select “employment is full time” and “year is” is 2023. In other words, you have selected only full-time jobs for 2023. To verify this new dataset, connect to a data table and/or a visualization widget. You can connect the Select Rows widget to dual data tables or visualization widgets. Right-click on the connectors and set one as Matching data >> data and the other as Unmatched data >> data. Therefore, one will show results on full-time jobs for 2023 and the other will show everyone else. See Figure 2.81.

  

#### 2.7.8 Edit Domain Widget

  

You can change the name of the variable and the type of variable. For example, you can change “employee residence” to “employee country.” See Figure 2.82. Do not forget to select apply after making any changes. You can check your changes by connecting the Edit Domain widget to a Data Table widget to see if the intended changes were applied correctly.

  
![](images/image-WS5ECP1T.png)  

Figure 2.80 Select column widget

  
![](images/image-UYB64VGU.png)  

Figure 2.81 Select rows widget

  

#### 2.7.9 Transpose Widget

  

This widget transposes data table rows to columns and columns to rows. This is sometimes necessary so that the data table format matches the formatting needs of the widgets.

  

#### 2.7.10 Pivot Table Widget

  

A pivot table switches (pivots) rows and columns for different views of your data. Figure 2.83 displays a pivot table where we chose the rows as expertise level and the columns as company size, and the values (numerical) as mean salary. According to the pivot table, more senior positions pay better and medium and large companies pay better than small companies.

  

#### 2.7.11 Rank Widget

  

This widget ranks the importance of predictors which is very useful for predictive models. It works for classification and regression. While this widget has multiple scoring methods, we would recommend the information gain method as the default. Listed below are the seven rank scoring options available in the Rank widget.

•Information gain tells you how much a feature contributes to the model’s performance and in this instance, it is called mutual information. Information gain can also be used to determine how a decision tree splits. It uses a mathematical formula for entropy to calculate the information gained and this determines which variables to split on first. Mathematically, information is defined as 1 minus entropy. More on this subject is included in section 5.5.1.

  
![](images/image-HM0ZL0LA.png)  

Figure 2.82 Edit domain widget

  
![](images/image-NIGKV1DS.png)  

Figure 2.83 Pivot table widget

  

•Information gain ratio is the ratio of information gain to intrinsic information. Intrinsic information is referred to as a type of correction factor that determines how much more information we need to tell which branch a specific instance belongs to. ⁸¹ For tree models, it aims to “reduce a bias towards multi-valued attributes by taking the number and size of branches into account when choosing an attribute.”

•Gini decrease. The first concept to understand is Gini impurity which means the imperfection that occurs when splitting in a decision tree. A pure split would mean the node only includes the same results (e.g., only spam emails). The mean decrease in the Gini coefficient measures how each variable contributes to the purity of the nodes and leaves in the resulting Tree. The greater the mean Gini decrease score, the more important the variable is to the model. ⁸²

•ANOVA (analysis of variance) option is a statistical test used to analyze the difference between the variance between means of more than two groups. A statistically significant result means that the two means are not equal. ⁸³ In the Rank widget, a NA is shown when an ANOVA is not appropriate.

•Chi-square (X ² ) statistic is a single number that tells how much difference exists between your observed counts and the counts you would expect if there were no relationship in the population. In Orange, a higher chi-square statistic indicates a higher dependence between the feature and the class. ⁸⁴

•ReliefF is a scoring method that integrates the ability of an attribute to distinguish between classes on similar data instances. ⁸⁵

•FCBF (Fast Correlation Based Filter) is an entropy-based measure, which also identifies redundancy due to pairwise correlations between features without the need for pairwise correlation analysis. This method is specifically shown to be useful for analyzing high dimensionality data. ⁸⁶

You can select more than one scoring method. By default, the selected criteria list the top 5 ranked predictor variables. Based on that, we see that the job title was ranked the highest followed by the employee residence (country). See Figure 2.84. If you highlight the top five choices, you can connect a Data Table widget to the Rank widget and now you have a smaller dataset with just the best predictors. You could save that with the Save Data widget.

Additionally, the Explain module (add-on) has a feature importance widget that is also useful and we will discuss this in another chapter.

  
![](images/image-F6BWKXHD.png)  

Figure 2.84 Rank widget

  
![](images/image-8JU7BVCP.jpg)  

Figure 2.85 Correlation widget

  

#### 2.7.12 Correlation Widget

  

This widget displays the correlations between numeric variables using Pearson (parametric - normal distribution assumption) or Spearman (non-parametric -non-normal distribution assumption) statistical methods. The correlation widget is located in the unsupervised learning module. You can select a specific correlation or select “all combinations.” It will list positive and negative correlations. Below in Figure 2.85 you can see that age has a strong negative correlation with maximal heart rate (on the treadmill) but a strong positive correlation with the number of calcified coronary vessels.

  
![](images/image-8OYA0Y79.png)  

Pearson Correlation (StatQuest)

  

#### 2.7.13 Merge Data Widget

  

This widget combines two tables, Excel files, or CSV files. This is a very commonly required task for many analysts and researchers. You may have certain data of interest in one file and other required data spread out over two or more other files. Although this technique is simpler than writing an SQL query, it can be confusing, since there are various situations that must be considered before you choose the correct option in Orange. Figure 2.86 shows the basic workflow to merge two datasets but successfully completing this task required a deeper look at the various options available in the Merge Data widget in order to complete this task correctly.

  
![](images/image-SAS009EN.png)  

Figure 2.86 Merge data widget

  

The Merge Data widget is used to horizontally merge two datasets based on a specific target column that will be used for row “matching” purposes. To demonstrate the first three merging options available in the Merge Data widget, let us first look at two very simple data files that we will want to merge for analysis purposes just to demonstrate the different purposes for each merging technique. Each of these two patient files offers two additional columns of patient data that each file has to offer, in addition to the specific patient number used for this healthcare facility. Figure 2.87 shows the two simple files we are attempting to merge into one file.

[Figure 2.88 shows the first three basic horizontal merging options that the Merge Data widget has to offer. These three merging options are classic merging techniques that are offered in several advanced software packages and Orange does its best to simplify this merging process in the fewest number of steps possible.](#content0071.xhtml)

  
![](images/image-PE777LLU.jpg)  

Figure 2.87 The three file merging options in the Merge Data widget

  

Whenever merging data from different files, we need to have a common reference column for row matching purposes. In this example, we are using a specific and unique patient number as that common reference column. Orange refers to this as a “row matching” option that must be selected for each file. In this example, we select the patient number as the “row matching” option, as shown in Figure 2.88. Orange does not like file header names with the “#” sign, and it will not merge them when this “#” sign is in the header.

  

Merging option #1 - Append Columns from Extra Data (Left Join)

  

The purpose of selecting merging option #1 in the Merge Data widget would be to only focus on the patient numbers listed in file #1. In this case, we are not interested in the additional patient numbers listed in file #2. However, we will accept any missing data in the additional columns in that file. Figure 2.89 shows a stylized version of what the merged file would look like if merging option #1 was chosen.

  
![](images/image-WV3ZAON9.jpg)  

Figure 2.88 Two simple files to be merged with the three different Merge Data widget options

  

We can see in Figure 2.90 that merging option #1 ignored the rows of information for patient #6, since that patient was not listed in file #1.

  
![](images/image-TS2T757R.jpg)  

Figure 2.89 Merging output from merging option #1: Append Columns from Extra Data (Left Join)

  

Merging option #2 - Find Matching Pairs of rows (Inner Join)

  

The purpose of selecting merging option #2 in the Merge Data widget would be to only focus on the patient numbers that are listed in file #1 and in file #2. In this case, we are not interested in patient numbers that are only listed in file #1 or file #2. However, we will accept any missing data that are in the additional columns in each of those files. Figure 2.90 shows a stylized version of what the merged file would look like if merging option #2 was chosen.

  
![](images/image-FJSV4TW5.jpg)  

Figure 2.90 Merging output from merging option #2: Find Matching Pairs of rows (Inner Join)

  

Merging option #3 - ConcatenateTables (Outer Join)

  

The purpose of selecting merging option #3 in the Merge Data widget would be to focus on all patient numbers that are listed in either file #1 and in file #2. Additionally, we will accept any missing data that are in the additional columns in each of those files. Figure 2.91 shows a stylized version of what the merged file would look like if merging option #3 was chosen. This option merges any complete or partial data that may exist for any listed patients in either of the files.

  

#### 2.7.14 Randomize widget

  

This widget will randomize classes, features, metas, or any combination of these options. Anyone who has ever played a card game knows that at the start of each card game is initiated with the usual “card shuffling” and “deck cutting” ritual which is intended to ensure that each new game starts with fresh and fair chances of success and defeat in the game for all game participants.

  
![](images/image-2LOTHKBV.jpg)  

Figure 2.91 Merging output from merging option #3: Concatenate tables (Outer Join)

  

In machine learning and predictive modeling, we have the same goal as in a card game but for different purposes. In machine learning, we usually start out by splitting (shuffling) the data into training, test, and possibly additional validation datasets from the original dataset. We can achieve this goal by “shuffling” the rows in a dataset so that they are not in any accidental order that may make the fair and random splitting of training, test, and validation datasets more difficult to achieve.

The goal of shuffling is to create these random splits in an unbiased fashion with no favoritism to any natural or hidden subgroup in the dataset. Unintentionally formatting a dataset in any logical or hidden order may conflict with the ability of any machine learning analysis techniques to randomly create unbiased training, testing, and other validation groups of data.

Here are some examples of situations that would benefit from random row shuffling:

•Datasets pre-sorted or ordered in the alpha order for categorical data.

•Datasets pre-sorted or ordered in numerical order of a specific column of data.

•Datasets pre-sorted or ordered by class definition, such as zero or one.

•Datasets pre-sorted or ordered in any other logical order.

•Datasets pre-sorted or ordered by the data sources, sensors, machines, departments, gender, location, age group, disease definitions, or other specific stratified data input sources.

The purpose of data row shuffling is to deny the algorithms of any unfair advantage or subgroup imbalance in the train, test, and validation groups as they search for patterns in the data.⁸⁶-⁹¹

Data row shuffling of datasets ensure the unbiased and random creation of training, testing, and other validation groups. Shuffling is just another tool in the data science arsenal intended to improve the accuracy and unbiased nature of predictive models.

The goal of data row shuffling is to introduce randomness and remove any inherent order or bias in the data. It helps to reduce variance and prevent the model from overfitting to specific patterns or sequences in the data. However, the Orange Randomize widget cannot guarantee this requirement since it randomizes the order of data in a column with no intention of maintaining the row contents. It is therefore deemed as a risky operation to be avoided if you intend to keep the information in a row intact and just shuffle the rows in relation to each other.

Here is how Orange describes their “randomize” column feature that is available with this widget and also in the preprocessor widget: “Randomize classes shuffles class values and destroys the connection between instances and class. Similarly, one can randomize features or metadata. If replicable shuffling is on, randomization results can be shared and repeated with a saved workflow. This is mainly used for advanced testing and educational purposes.”

In other words, this Orange column “shuffle” feature should not be confused with classic row “shuffling” which randomizes the order of entire rows in a dataset. Row shuffling may be a useful task to ensure further the randomness of rows that are chosen for training, testing, and other validation group membership.

  

#### 2.7.15 Concatenate Widget

  

The Concatenate widget is used to vertically merge two datasets which means that it will add the new data from a new file at the bottom of the list. In other words, it is vertically stacking two files on top of each other, which is not the same procedure the Merge widget uses. For example, you can add a new dataset with 100 instances (rows) to an existing dataset of 200 rows, and the final dataset will have 300 rows of data. Figure 2.92 shows four vertical merging options that the Concatenate widget offers.

Let’s concatenate the two files shown in Figure 2.92 using concatenate option #1. Figure 2.93 shows the result. It should be noted how this vertical concatenate result is very different when compared to the results for horizontally merging those same files with the Merge widget, as shown in Figures 2.90, 2.91, and 2.92.

Concatenate options 1 or 2 should always be chosen, while options 3 and 4 are optional. If concatenate option 2 was chosen to concatenate the two files shown in Figure 2.93, the result would only be one column listing the patient numbers from both files since that is the only column that appears on both data files.

  
![](images/image-FLT0ZGK4.jpg)  

Figure 2.92 The four Concatenate options

  
![](images/image-D4I87FDR.jpg)  

Figure 2.93 Concatenate variable merging option #1: Use all variables in all input tables

  

#### 2.7.16 Preprocess Widget

  

This widget offers ten options for preprocessing a datasheet, as shown in Figure 2.95. Each preprocessor offers multiple options that are described in the preprocessor help file. Here is a short description of the ten available preprocessors:

1\. Discretization of continuous values : Creates data bins

2\. Continuization of discrete values : Creates dummy variables, one hot encoding, and other tasks

3\. Impute missing values : Offers various data imputation of missing data handling options

4\. Select relevant features : Similar to the Rank widget; this preprocessor outputs only the most informative features as columns with the highest-ranked predictor listed on the left. The score can be determined by information gain, gain ratio, gini index, ReliefF, fast correlation-based filter, ANOVA, Chi2, RReliefF, and Univariate Linear Regression.

5\. Select random features : Outputs either a fixed number of features from the original data or a percentage. This is mainly used for advanced testing and educational purposes.

6\. Normalize features : Adjusts values to a common scale, center values by mean or median, or omit centering altogether. Similar to scaling, one can scale by SD (standard deviation), by span, or not at all.

7\. Randomize instances : Randomize classes shuffles class values and destroys the connection between instances and class. Similarly, one can randomize features or metadata. This is mainly used for advanced testing and educational purposes.

8\. Remove sparse features : Only retain features (columns) with more than a number/percentage of non-zero/missing values. The rest are discarded.

9\. Principal component analysis : Outputs results of a PCA transformation. Similar to the PCA widget. PCA “ simplifies the complexity in high-dimensional data while retaining trends and patterns. It does this by transforming the data into fewer dimensions, which act as summaries of features. ” ⁹² PCA is discussed further in Chapter 7.

10\. CUR matrix decomposition : is a dimensionality reduction method similar to SVD.

The biggest advantage of this widget is it can do multiple data pre-processing steps in one widget. The disadvantage of this all-in-one widget is that it does not have all the options and capabilities of the individual widgets it is trying to consolidate. For example, the following widgets offer more options that are included in the Preprocess widget if they are selected: Continuize, Discretize, Randomize, PCA, Impute, and Rank. When the Preprocess widget is open, double-click a desired preprocessor on the left, and it will appear on the right, or drag it to the right to make it active. See Figure 2.94. Note: the Orange designers recommend that the Preprocess widget be connected directly to the Test and Score widget. See Figure 2.95.

  
![](images/image-2ENCSWP2.jpg)  

Figure 2.94 Preprocess widget

  
![](images/image-MW8KNRI5.png)  

Figure 2.95 Preprocess workflow

  
![](images/image-3KS5TD8I.jpg)  

Figure 2.96 JASP outlier detection with box plots

  

#### 2.7.17 Outliers Widget

  

Outlier analysis is a very important aspect of any data analysis project for continuous variables. Outliers need to be investigated and understood before they are just deleted because they appear to be inconvenient or suspicious data points in the dataset.

Let us first understand the definition of a statistical outlier. Outliers can be identified from an overall dataset, but they are best investigated within a stratified group, such as gender in this example. Outliers are typically identified with the help of a box plot as shown in Figure 2.96 for this diabetes dataset with the help of JASP. The data points outside of the visual “fences” at the ends of the box plots are referred to as outliers which are shown as dots on the box plot. The math used by the boxplots to identify the regions where outliers begin is shown in Figure 2.96. JASP can create classic box plots as shown for glucose levels or as a horizontal boxplot in what JASP calls a raincloud plot, which overlays a histogram, dot plot, and box plot to offer multiple visualizations of the glucose data. The boxplot, raincloud plot, and descriptive statistics table can be created from the ANOVA and Descriptives tab in JASP.

  
![](images/image-8ON5XKN6.jpg)  

Figure 2.97 Orange workflow to show outliers and inliers on various visualizations

  

In the Orange Outliers widget, four different methods are available for outlier detection: One Class SVM, Covariance Estimator, Local Outlier Factor, or Isolation Forest. The default is “local outlier factor” (LOF) that uses the k-nearest neighbor algorithm. LOC measures the local deviation of the density of a given sample with respect to its neighbors and those with a lower density than their neighbors are considered outliers. LOF is also a Python package.⁹³

Either the outliers or the inliers (outliers eliminated) can be identified and visualized on separate graphics. Figure 2.97 shows a two-pronged Orange workflow that allows all data to be viewed on the top section and just the inliers to be shown on the bottom section with the help of the Outliers widget.

[Figure 2.98 shows the result for a few of the visualization widgets that were attached to the upper and lower workflow sections of the workflow in Figure 2.97 to see what a distribution plot and scatter plot look like with and without the outliers for a select set of the data.](#content0071.xhtml)

  
![](images/image-MT8FWXOK.jpg)  

Figure 2.98 Visualizations with and without outliers

  

#### 2.7.18 Continuize Widget

  

This widget converts discrete variables to numerical (continuous) dummy variables. This was discussed earlier in this chapter. An example of how this might be used is a conversion of discrete variables to numerical ones prior to an unsupervised learning analysis. There are several options in the widget, use the first choice by default. Connect the File widget to the Continuize widget, then to a Data Table. In Figure 2.99 categorical data was converted to numerical. Notice that the number of attributes increased due to “one-hot encoding.” One hot encoding means that each category in a column will get its own 1/0 (yes/no) column. This is achieved by selecting the “One variable per value” option in the Continuize options. Chest pain now has 3 columns and for the first patient typical angina = 1 meaning that is what the patient has. However, breaking out a categorical column into dummy variables for each option triggers the dummy variable trap that can cause issues for some algorithms. To avoid the dummy variable trap, select the first or second option for categorical features: “First value as base” or “Most frequent value as base” which will create one less column than the total number of categorical variables. This is called n-1 transformation.

  

#### 2.7.19 Discretize Widget

  

This widget converts numerical data to categorical. This is necessary for association rules analysis which we will cover in a separate chapter. ⁹⁴ There are several options, such as equal frequency, equal width, etc. In Figure 2.100 the manual option was selected for age and the intervals were every 10 years (a decade).

  

#### 2.7.20 Feature Constructor Widget

  

This widget transforms numerical and categorical variables using a variety of math functions used in Python. Machine learning should always be approached with the well-accepted “no free lunch theorem,” which means you should never expect your favorite algorithm to be the winner for all models and all datasets. ⁹⁵ In order to give all algorithms and their multiple options a chance at providing the best predictive model, feature transformations may be required to make skewed features look more normal. For example, we can convert a highly skewed glucose feature in a diabetes dataset to a more normal-looking distribution shape with the help of a log10 transformation, as an example. Many other transformations are available to create a more normal distribution. ⁹⁶

  
![](images/image-LE8PZCTS.png)  

Figure 2.99 Continuize widget

  
![](images/image-VLHU0R0Z.png)  

Figure 2.100 Discretize widget

  

[Figure 2.101 shows a workflow to implement and test feature transformation visualizations with the Orange Distribution widget and optional JASP box plot. The bottom two left figures in Figure 2.101 show a blank and correctly filled-out feature constructor widget. This is achieved by following these steps in the Feature constructor widget: New > select Numeric > replace X1 with the new variable name: Log10 Glucose > select function: log10 > select feature to be added within the ( ) signs: add glucose > send. You could then connect to a data table to view the new variable and connect it to a Distribution widget to see how the distribution changed. The bottom right distribution graphs and box plots for the original and log10 transformed glucose data are also shown. We can see that the log10 transformation helped but it did not fully achieve a symmetrical normal distribution. This may be good enough for many purposes, but it may also be worthwhile to experiment with power transformations that offer more transformations to make the data more similar to a normal distribution.](#content0071.xhtml)

  
![](images/image-VVIAU2SQ.jpg)  

Figure 2.101 Log10 transformation of the skewed Glucose data

  

[Figure 2.102 shows some of the available descriptive statistics in the JASP Descriptives tab that can be calculated for any feature. As we review this table, it is important to understand what a normal distribution would look like as far as their descriptive statistics are concerned.](#content0071.xhtml)

  
![](images/image-N7CK7RPN.jpg)  

Figure 2.102 Log10 transformation of the skewed glucose data

  

•Skewness: A normal distribution has a skewness value of zero. Positive skewness tells us that a distribution is right-skewed and a negative Skewness value indicates a left-skewed distribution. ⁹⁷

•Kurtosis: A normal distribution has a Kurtosis value of zero. A kurtosis with a value greater than 0 is leptokurtic (peaky top at the center) and a kurtosis with a value less than 0 is platykurtic (flatter top at the center). ⁹⁸ Others argue that kurtosis is not about the shape of the peak but more about how the tails look in relation to the rest of the distribution shape. ⁹⁹

•Shapiro-Wilk test for normality: If the Shapiro-Wilk p-value is below 0.05, the distribution is not normal. If it is above 0.05, we consider it a normal distribution. ¹⁰⁰

Power Transformations in JASP: As previously shown, Orange can calculate specific calculations and transformations with the help of the Feature Constructor widget. However, when trial and error with a few mathematical transformations such as log10, square root, or an inverse function does not meet your normalization targets, it may be time to consider power transformations. Power transformations do not guarantee that the p-value for the Shapiro-Wilk will be above 0.05, but they can help to greatly reduce the skewness of a distribution with the help of a power function (a logarithm or exponent) and a lambda parameter to make the distribution more like a normal distribution.¹⁰¹

Box-Cox transformations (for positive data) and Yeo-Johnson transformations (for positive and negative data) are two automated transformation methods that will find the best lambda parameter to transform distributions very close to a normal distribution. JASP offers the Box-Cox and the Yeo-Johnson transformation methods, but it does not offer the automated version so you will need to experiment with various lambda values to find the best lambda that creates a normal-looking distribution . Here are some of the most common lambda values used for power transformations: ¹⁰²

•lambda = -3 is a reciprocal transformation (Y- ³ = 1/Y ³ )

•lambda = -2 is a reciprocal transformation (Y -2 = 1/Y ² )

•lambda = -1 is a reciprocal transformation (Y -1 = 1/Y ¹ )

•lambda = -0.5 is a reciprocal square root transformation (Y -0.5 = 1/square root of Y ¹ )

•lambda = 0.0 is a natural log transformation

•lambda = 0.5 is a square root transformation

•lambda = 1.0 is no transformation (Y ¹ )

•lambda = 2.0 is a square transformation (Y ² )

•lambda = 3.0 is a cubic transformation (Y ³ )

A lambda of one represents no data transformation since the data is assigned an exponent of one, which does not change the data.

So why would we use lambda values greater than 1? We would do so if we have a left skew problem with our distribution. Lambda values greater than one adds an exponent to each value which has the effect of magnifying the larger numbers greater than the smaller ones which rebalances the skewness to a more normal shape. The more severe the left skew, the higher the lambda to be experimented with.¹⁰⁰

So why would we use lambda values less than 1? We would do so if we have a right skew problem with our distribution. Lambda values less than one adds a log or reciprocal transformation to each value, which causes the smaller numbers to get magnified more than the larger numbers in that column which rebalances the skewness to a more normal shape. The more severe the right skew, the higher the lambda to be experimented with.¹⁰¹

[Figure 2.103 shows the results of a small experiment run in JASP to find the best lambda transformation to transform the shape of the right-skewed glucose data into a more normally shaped distribution shown at the top of the figure. As shown, if a very lambda value is chosen, it will create a left-skew problem, so it takes time and patience to find the optimal lambda value.](#content0071.xhtml)

The original glucose data was highly right-skewed with high skewness and kurtosis values and a Shapiro-Wilk p-value < 0.05, indicating non-normality for this glucose data. This experiment was limited to low lambda values of 0, -1, -2, and -3 since the data was right-skewed. The best lambda for this experiment was -1, which is a reciprocal data transformation (Y-1 = 1/Y¹ ). Lambda values with decimals could also be used to fine-tune the distribution shape, but they were not used for this experiment.

[Figure 2.104 shows a select group of descriptive stats that represent the results of this experiment. These statistics confirm that the Yeo-Johnson (YJ) transformation in JASP had the best (lowest) Skewness and Kurtosis values which are highlighted in the three wide boxes. The Shapiro-Wilk p-value was still < 0.05 as for all other elements in the experiment, but these results should be good enough to be used to test if this transformation helps model performance or not. It should also be noted that this transformation dramatically narrowed the range of the data to only 0.018. It may be wise to rescale this column of data with all other predictors so that none of them has a large-scale advantage that may influence the predictions of some algorithms. Re-scaling does not change the shape of a distribution but just its scales.](#content0071.xhtml)

  
![](images/image-OL81CIN1.jpg)  

Figure 2.103 Yeo-Johnson transformations of the right-skewed Glucose values

  
![](images/image-GNA31C9E.png)  

Figure 2.104 Descriptive statistics for the original data and the Yeo-Johnson (YJ) transformations

  

[Figure 2.105 shows how to create Yeo-Johnson transformations in JASP with these 8 steps:](#content0071.xhtml)

1\. Check the “+” mark on the far-right side of the spreadsheet view of the data

2\. The “Create Computed Column” dialogue box will open. Enter the desired name of the new column in the “Name” section

3\. Select “create column”

4\. From the far-right side of the screen, scroll down through all of the available calculations and select “YeoJohnson”

5\. After being selected, it will appear in the main formula section at the top of the page

6\. Replace “y” with “glucose” and “lambda” with “-1”

7\. Click the “Compute column” button at the bottom of the formula creation area

8\. The new calculated column will appear to the right of all other columns in the dataset. Add a new column (step 1) for each new transformation you experiment with. This data will then be available for analysis purposes in JASP.

There are many different data preprocessing steps, such as power transformations, that work together to create the best possible foundation to enable great predictive models. Each preprocessing step requires a fair amount of experimentation for each new dataset that we analyze if we would ever hope for it to become a top-performing predictive model.

  

#### 2.7.21 Feature Statistics Widget

  

This widget provides simple descriptive statistics, and it should be part of exploratory data analysis. Examine the visualization of each variable. The widget creates histograms for numerical data and bar plots for categorical data that can give us a great heads up for a new data set about distribution skewness, outliers, the percent of missing data, and much more. You can group (color) by any categorical feature, such as blue for no heart disease and red for heart disease. You could also color by gender. It generates the center (mean and median), dispersion, min, max, and number/percent of missing data points. The dispersion of categorical data is its entropy (degree of uncertainty). For numerical data, it is the coefficient of variation (standard deviation divided by the mean). See Figure 2.106 for an example of the output of this widget. Note: There are three colors due to three possible outcomes - sleep apnea, insomnia and none.

  
![](images/image-SDHZSB2X.jpg)  

Figure 2.105 The 8 steps to create Yeo-Johnson transformations in JASP

  
![](images/image-BD8TYN1W.png)  

Figure 2.106 Feature statistics widget output

  

#### 2.7.22 Unique Widget

  

This widget removes duplicates. Connect the widget to the File widget and a Data Table widget. Select the variable column to look for duplicates and select what you want done such as keep the “last instances.”

  

#### 2.7.23 Save Data Widget

  

Use this widget to save processed data as a CSV file for further analysis. Also, when you are finished with your workflow go to file >> Save as, and it will save your workflow to Documents as an .ows file. Ensure the box “Add type annotations to header” is not checked. Also, don’t forget at the bottom of the widget there is a report option where you can save (html, PDF) or print.

  

#### 2.7.24 Widget Combinations

  

In this section we will highlight a few widget combinations that are insightful and useful.

1\. Connect a data table to another data table. Highlight instances in data table #1 and view the results in data table #2. Save results using the Save Data widget

2\. You can connect the Scatter Plot widget to another Scatter Plo t widget, then highlight data points of interest in scatter plot #1 and view the results in scatter plot #2

3\. You can highlight data points in a scatter plot and then connect to a Data Table widget to examine the exact values of the selected data

4\. Use a Tree widget and connect it to a Tree Viewer widget. Then highlight a node of interest on the tree diagram and connect to a Data Table widget. Make sure that the link between the Tree Viewer widget and the Data Table widget is set to Selected Data >> Data which will then show the data values for that selected tree node for further analysis.

5\. Set up a workflow to compare two different models e.g., selecting the top 5 ranked variables using the “select relevant features” option in the Preprocess widget, with all variables included. Then review the model performances in the Test and Score widgets. This workflow compares two random forest models. One of the models uses all of the predictors and the other model uses just the top 5 predictors. This workflow setup could be used in many other analysis comparisons to see how simplified versions of a model compare to a full model with all predictors. See Figure 2.107 .

  
![](images/image-4YFA2YXK.png)  

Figure 2.107 Comparing two models

  

6\. Connect the File widget with the heart disease data loaded in Orange and connect it to the Select Rows widget. In the Select Rows widget, we will set up three conditions - diameter narrowing (heart disease) = 0, gender = female, and age is below 50 (in other words younger women without heart disease) as shown in Figure 2.108 .

  
![](images/image-9UF6HCJX.jpg)  

Figure 2.108 Select Rows widget selections

  

Connect the Select Rows widget to a Data Table widget; you will see there are 23 women in this select group. Highlight those and connect to a Box Plot widget. Open the Box Plot widget and select major vessels colored as the variable and gender as the subgroup. The mean coronary calcium score is 0.09 in the box plot. Connect a second Data Table widget to the Select Rows widget but change the connector to “unmatched data to data” and this will send all of the other patients to the data table. Connect this data table to a Box Plot widget. Open the widget and select major vessels colored as the variable and gender as the subgroup. The Box Plot widget will show that these women had a mean coronary calcium score of 0.69 and the men had a mean coronary calcium score of 0.73. Take home point: Younger women without heart disease don’t have coronary calcifications. See Figure 2.109 shows the workflow that matches this previous example.

  

2.8 JASP DATA FEATURES

  

  

The main strengths of JASP lie in descriptive and advanced statistics, data transformations, data visualizations, and machine learning. JASP data tables and visualizations will be discussed in Chapter 3.

  

2.9 PUTTING KNOWLEDGE INTO PRACTICE

  

  

#### 2.9.1 Exercise

  

There is no substitute for experience with handling multiple datasets of different sizes, data types, and complexity levels. Regardless of the data science software chosen, practice and repetition of analysis tasks are important to solidify a desired level of expertise. For this exercise we will use a dataset from Kaggle that looks at data science salaries worldwide 2020-2023. The dataset is archived in the Chapter 2 folder on the File-Share site and further information about the data can be found on Kaggle.⁸⁰

The following example outlines the logical sequence of steps that should be adhered to when stratifying and analyzing this dataset. These procedures are aimed at efficiently reducing the dataset to a subset featuring only the most frequently occurring categories. This streamlines the preparation process for a highly targeted and precise analysis.

•Upload the dataset into the File widget and open. Change the data type for Job Title from meta to categorical and the Role to feature. We are interested in salaries in US dollars so change the Role of Salary, Salary Currency and Employee Residence to Skip. Hit the Apply button.

•Connect a Data Table widget to the File widget and open. Review the data in each column.

•Connect a Box Plot widget to the File widget and open it.

  

![](images/image-TEMD15Y1.jpg)Choose Company location in the Variable and Subgroup windows. What country has the majority of data science salaries listed? We will use only US jobs data for this example.

  

![](images/image-TEMD15Y1.jpg)Select year in both windows. What year has the most data? We will use data from 2023 only for this example.

  

![](images/image-TEMD15Y1.jpg)Select employment type in both windows. What is the most common employment type? We will use only full-time employment data for this example.

•In order to stratify/filter the data in Orange, perform the following:

  

![](images/image-TEMD15Y1.jpg)Connect the Select Rows widget to the File widget and open it.

  

![](images/image-TEMD15Y1.jpg)Add these conditions to the Select Rows widget: “Employment type is Full-Time;” “Year is 2023;” and “Company’s location is United States.”

  
![](images/image-29DSWBPV.png)  

Figure 2.109 Comparing matched and unmatched patients

  

•Connect a new Box Plot (1) widget to the Select Rows widget and open it.

  

![](images/image-TEMD15Y1.jpg)Select Experience Level in both windows. What was the most common position?

  

![](images/image-TEMD15Y1.jpg)Select Expertise level in both windows. What was the most common expertise category?

  

![](images/image-TEMD15Y1.jpg)Select Company Size in both windows. What is the most common company size?

  

![](images/image-TEMD15Y1.jpg)In the Variables window select “Salaries in USD.” In the lower window select “Experience Level.” Was experience level a topic of statistical significance (p-value < 0.05)?

  

![](images/image-TEMD15Y1.jpg)Select “Salaries in USD” in the upper window and “Expertise Level” in the lower window. Was salaries and expertise level a topic of statistical significance (p-value < 0.05)?

  

![](images/image-TEMD15Y1.jpg)Select job title in the upper and lower windows. Because there are 87 job title categories, we need to take a different approach. Check the box “Sort by subgroup frequency.” You now have a bar graph with the most common job titles at the top.

  

![](images/image-TEMD15Y1.jpg)Using the control key in Windows or the command key on the Mac, select/highlight the first four bars. You will send those to another Box Plot widget.

  

![](images/image-TEMD15Y1.jpg)Note: basic descriptive statistics, such as averages and standard deviations, can be viewed in the Distributions widget if a continuous variable is chosen in the top variable section and if a categorical variable is chosen in the “split by” section at the bottom.

•Connect another Box Plot (2) widget to the Box Plot (1) widget..

  

![](images/image-TEMD15Y1.jpg)We want to see if Salary in USD varies by Job Title. Open Box Plot (2) widget and select Salary in USD in the upper and Job Titles in the lower windows.

  

![](images/image-TEMD15Y1.jpg)What are the four categories shown? What are the lowest and highest salaries and are they statistically significantly different?

[Figure 2.110 Displays the Orange workflow for the analysis process previously described for the Kaggle Data Science Salaries dataset.](#content0075.xhtml)

  

#### 2.9.2 Maturity Level

  

Here are three retailers, each illustrating a distinct level of data preparation and wrangling maturity, along with insights into how this impacts their operations.

Low Maturity Level:

•Manual data entry for sales, inventory, and customer feedback without standardized procedures.

•No system in place for handling missing data, duplicates, or outliers.

•Limited or no integration between online and in-store sales data.

  
![](images/image-7MAKXXDN.png)  

Figure 2.110 Orange workflow to analyze data scientist salaries for 2023

  

•Data stored in fragmented systems or physical records.

•Lack of consistent data formats and naming conventions.

Mid Maturity Level:

•Semi-automated data integration tools connecting online and offline sales

•Regular use of no-code tools or scripts to clean, prepare, and transform data

•Procedures in place for handling missing values, duplicates, and outliers using industry-standard practices

•Introduction of a centralized database or cloud storage solution for better data accessibility

•Initial efforts to categorize and classify data for easier retrieval and analysis.

High Maturity Level:

•Fully integrated data systems synchronizing in real-time across multiple sales platforms, warehouses, and supply chains

•Dedicated teams or individuals using advanced no-code platforms for data wrangling, preparation, and visualization

•Robust handling of data anomalies with no-code predictive tools offering insights and alerts

•Seamless integration with customer relationship management (CRM) systems to enhance customer-centric data analysis

•Development of no-code dashboards and reporting tools for immediate insights and data-driven decision-making

By emphasizing no-code solutions, businesses can democratize the data preparation and wrangling processes, allowing non-technical stakeholders to participate actively in these stages.

  

#### RESOURCES

  

  

1\. Medium.com - data science articles are often useful and brief. You can follow topics on data science, machine learning, and artificial intelligence. For $5 monthly, Medium will select articles in these topic areas which is a great way to receive multiple short topics. The downside is that they are not peer-reviewed, so occasional mistakes are published.

2\. KDNuggets.com - provides a multitude of short articles on data science topics and also includes tabs for courses, datasets, tutorials, etc.

3\. OpenML.org - has more than 21,000 datasets with several versions of the heart disease prediction datasets, plus it lists hundreds of data runs with a variety of algorithms to see how they performed, in terms of classification accuracy. For example, this page describes in detail how logistic regression was used with adjustments made to the algorithm (hyperparameter optimization) and the resulting performance. The downside is that most of the competitions used the ML software WEKA and many of the datasets are in the .arff format. WEKA is a free download and has the option to convert easily. arffs to CSV.

4\. Google Dataset Search - is a mega search site. When “medical datasets for classification” was entered, it returned 100 hits.

5\. Kaggle Datasets - as of mid-2023 Kaggle has over 200,000 datasets for download. Kaggle is a data competition site where one can compete for prizes and post their models, comments and solutions online.

  

#### REFERENCES

  

  

[1\. Smolic H. How Much Data Is Needed For Machine Learning? \[Internet\]. Graphite Note. 2022 \[cited 2023 Aug 13\]. Available from: https://graphite-note.com/how-much-data-is-needed-for-machine-learning](#content0040.xhtml)

[2\. Stack Overflow \[Internet\]. \[cited 2023 Aug 13\]. Minimum number of rows in data set for accurate predictions. Available from: https://stackoverflow.com/questions/25645316/minimum-number-of-rows-in-data-set-for-accurate-predictions](#content0040.xhtml)

[3\. Predictive Models \[Internet\]. \[cited 2023 Aug 13\]. Available from: https://help.catalytic.com/docs/predictive-models/](#content0040.xhtml)

[4\. Google Cloud \[Internet\]. \[cited 2023 Aug 13\]. Prepare training data. Available from: https://cloud.google.com/vertex-ai/docs/tabular-data/forecasting/prepare-data](#content0040.xhtml)

[5\. Google for Developers \[Internet\]. \[cited 2023 Aug 13\]. The size and quality of a data set. Available from: https://developers.google.com/machine-learning/data-prep/construct/collect/data-size-quality](#content0040.xhtml)

[6\. Chang A. Intelligence Based Medicine. Chapter 1: Basic Concepts of Artificial Intelligence. Elsevier. Academic Press. 2020](#content0040.xhtml)

[7\. Hoyt R, Muenchen R. Introduction to Biomedical Data Science. 2021. Available from: https://www.google.com/books/edition/Introduction\_to\_Biomedical\_Data\_Science/](#content0040.xhtml)

[8\. Chand M. Cracking Big Data. \[Internet\]\[cited 2022 March 15\] Available from: https://www.c-sharpcorner.com/UploadFile/mahesh/cracking-big-data/](#content0040.xhtml)

[9\. Choosing an appropriate Sensory data analysis tool \[Internet\]. \[cited 2023 Aug 13\]. Available from: https://help.xlstat.com/6482-choosing-appropriate-sensory-data-analysis-tool](#content0040.xhtml)

[10\. \[Personal communication\] with John Lee MD. September 17, 2022.](#content0040.xhtml)

[11\. Lorange Y. 5 Reasons Healthcare Data Is Unique and Difficult to Measure \[Internet\]. Health Catalyst. 2018 \[cited 2022 Mar 18\]. Available from: https://www.healthcatalyst.com/insights/5-reasons-healthcare-data-is-difficult-to-measure/](#content0040.xhtml)

[12\. ImageNet \[Internet\]. \[cited 2022 Mar 17\]. Available from: https://www.image-net.org/](#content0040.xhtml)

[13\. UCI Machine Learning Repository: datasets \[Internet\]. \[cited 2022 Mar 17\]. Available from: https://archive.ics.uci.edu/ml/datasets.php](#content0040.xhtml)

[14\. Sullivan GM, Artino AR Jr. Analyzing and interpreting data from likert-type scales. J Grad Med Educ \[Internet\]. 2013 Dec;5(4):541–2. Available from: http://dx.doi.org/10.4300/JGME-5-4-18](#content0041.xhtml)

[15\. Mithrakumar M. Scalars, Vectors, Matrices and Tensors with Tensorflow 2.0 \[Internet\]. DEV Community. 2019 \[cited 2022 Apr 12\]. Available from: https://dev.to/mmithrakumar/scalars-vectors-matrices-and-tensors-with-tensorflow-2-0-1f66](#content0041.xhtml)

[16\. Data Validation in Excel. \[Internet\] \[cited 2022 October 15\] Available from: https://www.customguide.com/excel/data-validation-excel](#content0043.xhtml)

[17\. Rençberoğlu E. Fundamental Techniques of Feature Engineering for Machine Learning \[Internet\]. Towards Data Science. 2019 \[cited 2022 Mar 22\]. Available from: https://towardsdatascience.com/feature-engineering-for-machine-learning-3a5e293a5114](#content0044.xhtml)

[18\. Palanivinayagam A, Damaševičius R. Effective Handling of Missing Values in Datasets for Classification Using Machine Learning Methods. Information. 2023 Feb 3;14(2):92.](#content0045.xhtml)

[19\. Brownlee, Jason. 2020. “How to Avoid Data Leakage When Performing Data Preparation.” MachineLearningMastery.com . Machine Learning Mastery. June 21, 2020.Available from: https://machinelearningmastery.com/data-preparation-without-data-leakage/](#content0045.xhtml)

[20\. Galarnyk, Michael. 2022. “Understanding Train Test Split.” Built In. July 28, 2022. Available from: https://builtin.com/data-science/train-test-spli t](#content0045.xhtml)

[21\. Mack C, Su Z, Westreich D. Types of Missing Data. Agency for Healthcare Research and Quality (US); 2018. Available from: https://pubmed.ncbi.nlm.nih.gov/29671990/](#content0045.xhtml)

[22\. Khan SI, Hoque ASML. SICE: an improved missing data imputation technique. J Big Data. 2020 Jun 12;7(1):37.](#content0045.xhtml)

[23\. Kumar S. Towards Data Science. 2020 \[cited 2023 Aug 13\]. 7 ways to handle missing values in machine learning. Available from: https://towardsdatascience.com/7-ways-to-handle-missing-values-in-machine-learning-1a6326adf79e](#content0045.xhtml)

[24\. No Code Data Science. https://www.nocodedatascience.net/file-share](#content0045.xhtml)

[25\. Ahmed A. SciStatCalc \[Internet\]. \[cited 2023 Aug 14\]. Available from: https://scistatcalc.blogspot.com/2013/11/kolmogorov-smirnov-test-calculator.html](#content0045.xhtml)

[26\. Khan Academy \[Internet\]. Available from: https://www.khanacademy.org/math/statistics-probability/summarizing-quantitative-data/box-whisker-plots/a/identifying-outliers-iqr-rule](#content0046.xhtml)

[27\. What are outliers in the data? \[Internet\]. \[cited 2023 Feb 9\]. Available from: https://www.itl.nist.gov/div898/handbook/prc/section1/prc16.htm](#content0046.xhtml)

[28\. Bioinformatics Laboratory, and University of Ljubljana. n.d. “Outliers.”\[Internet\]\[cited 2022 November 21\] Available from: https://orangedatamining.com/widget-catalog/unsupervised/outliers/](#content0046.xhtml)

[29\. Elgiriyewithana N. Global Country Information Dataset 2023 \[Internet\]. 2023 \[cited 2023 Aug 13\]. Available from: https://www.kaggle.com/datasets/nelgiriyewithana/countries-of-the-world-2023](#content0046.xhtml)

[30\. Information Gain and Mutual Information for Machine Learning. Machine Learning Mastery. \[Internet\]\[cited 2022 September 21\] Available from: https://machinelearningmastery.com/information-gain-and-mutual-information/](#content0047.xhtml)

[31\. Kohavi R, and Sahami M. n.d. “Error-Based and Entropy-Based Discretization of Continuous Features.” KDD: Proceedings / International Conference on Knowledge Discovery & Data Mining. International Conference on Knowledge Discovery & Data Mining . Available from: https://www.aaai.org/Papers/KDD/1996/KDD96-019.pdf](#content0047.xhtml)

[32\. About Adult BMI. CDC. \[Internet\]\[cited 2022 September 21\] Available from: https://www.cdc.gov/healthyweight/assessing/bmi/adult\_bmi/index.html#Why](#content0047.xhtml)

[33\. Klawonn F, Hoffmann G, Orth M. Quantitative laboratory results: normal or lognormal distribution? Journal of Laboratory Medicine \[Internet\]. 2020 Jun 1 \[cited 2022 Apr 13\];44(3):143–50. Available from: https://www.degruyter.com/document/doi/10.1515/labmed-2020-0005/pdf](#content0048.xhtml)

[34\. Feng, Changyong, Hongyue Wang, Naiji Lu, Tian Chen, Hua He, Ying Lu, and Xin M. Tu. 2014. “Log-Transformation and Its Implications for Data Analysis.” Shanghai Archives of Psychiatry 26 (2): 105–9.](#content0048.xhtml)

[35\. Brownlee, Jason. 2018. “How to Transform Data to Better Fit The Normal Distribution.” MachineLearningMastery.com . Machine Learning Mastery. May 20, 2018. Available from: https://machinelearningmastery.com/how-to-transform-data-to-fit-the-normal-distribution/](#content0048.xhtml)

[36\. Tharmalingam L. Sleep health and Lifestyle Dataset \[Internet\]. 2023 \[cited 2023 Aug 14\]. Available from: https://www.kaggle.com/datasets/uom190346a/sleep-health-and-lifestyle-dataset](#content0051.xhtml)

[37\. Understanding Curse of Dimensionality \[Internet\]. GreatLearning Blog: 2020 \[cited 2022 Mar 21\]. Available from: https://www.mygreatlearning.com/blog/understanding-curse-of-dimensionality/](#content0056.xhtml)

[38\. O., Nikola. 2022. “Multicollinearity and Its Importance in Machine Learning.” January 4, 2022. https://hackernoon.com/multicollinearity-and-its-importance-in-machine-learning](#content0057.xhtml)

[39\. Schober, Patrick, Christa Boer, and Lothar A. Schwarte. 2018. “Correlation Coefficients: Appropriate Use and Interpretation.” Anesthesia and Analgesia 126 (5): 1763–68.](#content0057.xhtml)

[40\. Schwartzman, Armin, and Xihong Lin. 2011. “The Effect of Correlation in False Discovery Rate Estimation.” Biometrika 98 (1): 199–214.](#content0057.xhtml)

[41\. Starmer, Statquest With Josh. 2017. “False Discovery Rates, FDR, Clearly Explained.” Youtube. January 10, 2017. https://www.youtube.com/watch?v=K8LQSvtjcEo](#content0057.xhtml)

[42\. Body Fat Prediction Dataset \[Internet\]. 2021 \[cited 2022 Dec 22\]. Available from: https://www.kaggle.com/datasets/fedesoriano/body-fat-prediction-dataset](#content0057.xhtml)

[43\. 10.7 - detecting multicollinearity using variance inflation factors \[Internet\]. \[cited 2022 Dec 22\]. Available from: https://online.stat.psu.edu/stat462/node/180/](#content0057.xhtml)

[44\. Heckman E. What in the World Is a VIF? \[Internet\]. \[cited 2022 Dec 22\]. Available from: https://blog.minitab.com/en/starting-out-with-statistical-software/what-in-the-world-is-a-vif](#content0057.xhtml)

[45\. Tsagris M, Pandis N. Multicollinearity. Am J Orthod Dentofacial Orthop. 2021 May;159(5):695–6](#content0057.xhtml)

[46\. Variance Inflation Factor (VIF) \[Internet\]. Investopedia. 2010 \[cited 2022 Dec 22\]. Available from: https://www.investopedia.com/terms/v/variance-inflation-factor.asp](#content0057.xhtml)

[47\. How do you handle multicollinearity in data science models? \[Internet\]. Quora. \[cited 2022 Dec 22\]. Available from: https://www.quora.com/How-do-you-handle-multicollinearity-in-data-science-models](#content0057.xhtml)

[48\. Thomas L. Confounding variables \[Internet\]. Scribbr. 2020 \[cited 2022 Dec 22\]. Available from: https://www.scribbr.com/methodology/confounding-variables/](#content0057.xhtml)

[49\. Priceonomics. Do storks deliver babies? \[Internet\]. Priceonomics. 2014 \[cited 2022 Dec 22\]. Available from: https://priceonomics.com/do-storks-deliver-babies/](#content0057.xhtml)

[50\. Spurious correlations \[Internet\]. \[cited 2022 Dec 22\]. Available from: http://www.tylervigen.com/spurious-correlations](#content0057.xhtml)

[51\. A Complete understanding of LASSO Regression \[Internet\]. Great Learning Blog: Free Resources what Matters to shape your Career! 2021 \[cited 2022 Dec 22\]. Available from: https://www.mygreatlearning.com/blog/understanding-of-lasso-regression/](#content0057.xhtml)

[52\. Xu W. What’s the difference between Linear Regression, Lasso, Ridge, and ElasticNet in sklearn? \[Internet\]. Towards Data Science. 2019 \[cited 2022 Dec 22\]. Available from: https://towardsdatascience.com/whats-the-difference-between-linear-regression-lasso-ridge-and-elasticnet-8f997c60cf29](#content0057.xhtml)

[53\. Brownlee. n.d. “Data Leakage in Machine Learning.” Machine Learning Mastery .\[Internet\]\[cited 2022 August 17\] Available from: https://machinelearningmastery.com/data-leakage-machine-learning](#content0058.xhtml)

[54\. Yıldırım S. Data leakage in machine learning \[Internet\]. Towards Data Science. 2020 \[cited 2023 Feb 9\]. Available from: https://towardsdatascience.com/data-leakage-in-machine-learning-6161c167e8ba](#content0058.xhtml)

[55\. Brownlee J. How to avoid data leakage when performing data preparation \[Internet\]. MachineLearningMastery.com . Machine Learning Mastery; 2020 \[cited 2022 Nov 21\]. Available from: https://machinelearningmastery.com/data-preparation-without-data-leakage/](#content0058.xhtml)

[56\. Kaufman S, Rosset S, Perlich C. Leakage in Data Mining: Formulation, Detection and Avoidance. KDD 2011. ACM. \[Internet\]\[cited 2022 May 10\] Available from: https://dl.acm.org/doi/10.1145/2382577.2382579](#content0058.xhtml)

[57\. Kapoor, Sayash, and Arvind Narayanan. 2022. “Leakage and the Reproducibility Crisis in ML-Based Science.” arXiv.\[Internet\]\[cited 2022 August 15\] Available from: http://arxiv.org/abs/2207.07048](#content0058.xhtml)

[58\. Data Leakage. Princeton. \[Internet\]\[cited 2022 August 17\] Available from: https://reproducible.cs.princeton.edu/](#content0058.xhtml)

[59\. Gartner. Emerging Tech: Top Use Cases for Tabular Synthetic Data. Sept 2022, \[Internet\]. Available from: https://k2view.com](#content0061.xhtml)

[60\. Synthea \[Internet}. Available from https://synthea.mitre.org/](#content0062.xhtml)

[61\. GitHub. Synthea.\[Internet\]. Available from: https://github.com/synthetichealth/synthea/wiki/Basic-Setup-and-Running](#content0062.xhtml)

[62\. Hoyt R. Synthea: Do-it-yourself data \[Internet\]. Medium. 2020 \[cited 2023 Jan 15\]. Available from: https://medium.com/@rehoyt/synthea-do-it-yourself-data-6ebe4d850db6](#content0062.xhtml)

[63\. Foraker RE, Yu SC, Gupta A, Michelson AP, Pineda Soto JA, Colvin R, et al. Spot the difference: comparing results of analyses from real patient data and synthetic derivatives \[Internet\]. Vol. 3, JAMIA Open. 2021. p. 557–66. Available from: http://dx.doi.org/10.1093/jamiaopen/ooaa060](#content0063.xhtml)

[64\. Hernandez M, Epelde G, Alberdi A, Cilla R, Rankin D. Standardised Metrics and Methods for Synthetic Tabular Data Evaluation \[Internet\]. Available from: http://dx.doi.org/10.36227/techrxiv.16610896.v1](#content0063.xhtml)

[65\. Benaim AR, Almog R, Gorelik Y, Hochberg I, Nassar L, Mashiach T, et al. Analyzing Medical Research Results Based on Synthetic Data and Their Relation to Real Data Results: Systematic Comparison From Five Observational Studies \[Internet\]. Vol. 8, JMIR Medical Informatics. 2020. p. e16492. Available from: http://dx.doi.org/10.2196/16492](#content0063.xhtml)

[66\. Azizi Z, Zheng C, Mosquera L, Pilote L, El Emam K. Can synthetic data be a proxy for real clinical trial data? A validation study \[Internet\]. Vol. 11, BMJ Open. 2021. p. e043497. Available from: http://dx.doi.org/10.1136/bmjopen-2020-043497](#content0063.xhtml)

[67\. Haddad F. AWS Machine Learning Blog. December 2022. How to evaluate the quality of the synthetic data – measuring from the perspective of fidelity, utility, and privacy. Available from: https://aws.amazon.com/blogs/machine-learning/how-to-evaluate-the-quality-of-the-synthetic-data-measuring-from-the-perspective-of-fidelity-utility-and-privacy/](#content0063.xhtml)

[68\. Gretel. \[Internet\]. Available from: https://gretel.ai](#content0063.xhtml)

[69\. Wilcoxon Signed Rank Test. Stats Kingdom. Available from: https://www.statskingdom.com/175wilcoxon\_signed\_ranks.html](#content0063.xhtml)

[70\. Zöller MA, Huber MF. Benchmark and Survey of Automated Machine Learning Frameworks. jair. 2021 Jan 27;70:409–72.](#content0065.xhtml)

[71\. Escalante HJ. Automated Machine Learning -- a brief review at the end of the early years \[Internet\]. arXiv \[cs.LG\]. 2020. Available from: http://arxiv.org/abs/2008.08516](#content0065.xhtml)

[72\. Medium \[Internet\]. Medium. \[cited 2023 Feb 9\]. Available from: https://towardsdatascience.com/compare-popular-automl-frameworks-on-10-tabular-kaggle-competitions-9b1420e8942dv](#content0065.xhtml)

[73\. Simonite T. Google’s AI Experts Try to Automate Themselves. Wired \[Internet\]. 2019 Apr 16 \[cited 2023 Feb 9\]; Available from: https://www.wired.com/story/googles-ai-experts-try-automate-themselves/](#content0065.xhtml)

[74\. Abbasi A, Kitchens B, Ahmad F. The risks of AutoML and how to avoid them. Harvard business review \[Internet\]. 2019 Oct 24 \[cited 2023 Feb 9\]; Available from: https://hbr.org/2019/10/the-risks-of-automl-and-how-to-avoid-them](#content0065.xhtml)

[75\. Xin D. AutoML: The promise vs. Reality according to practitioners \[Internet\]. InfoQ. 2022 \[cited 2023 Feb 9\]. Available from: https://www.infoq.com/articles/auto-ml-promise-reality/](#content0065.xhtml)

[76\. Czakon J. 24 evaluation metrics for binary classification (and when to use them) \[Internet\]. neptune.ai. 2022 \[cited 2023 Feb 9\]. Available from: https://neptune.ai/blog/evaluation-metrics-binary-classification](#content0070.xhtml)

[77\. Yang L, Shami A. On hyperparameter optimization of machine learning algorithms: Theory and practice. Neurocomputing. 2020 Nov 20;415:295–316.](#content0070.xhtml)

[78\. Index of Orange datasets/ \[Internet\]. \[cited 2022 Apr 11\]. Available from: http://file.biolab.si/datasets/](#content0071.xhtml)

[79\. Wikipedia contributors. Simpson’s paradox \[Internet\]. Wikipedia, The Free Encyclopedia. 2023. Available from: https://en.wikipedia.org/w/index.php?title=Simpson%27s\_paradox&oldid=1138372077](#content0071.xhtml)

[80\. Banerjee S. Latest Data Science Salaries \[Internet\]. 2023 \[cited 2023 Jul 18\]. Available from: https://www.kaggle.com/datasets/iamsouravbanerjee/data-science-salaries-2023](#content0071.xhtml)

[81\. Information gain ratio \[Internet\]. \[cited 2022 Mar 21\]. Available from: https://en.wikipedia.org/wiki/Information\_gain\_ratio](#content0071.xhtml)

[82\. Variable importance plot (mean decrease accuracy and mean decrease Gini) \[Internet\]. PLOS ONE; 2020 \[cited 2022 Apr 14\]. Available from: http://dx.doi.org/10.1371/journal.pone.0230799.g002](#content0071.xhtml)

[83\. ANOVA Test: Definition, Types, Examples, SPSS \[Internet\]. Statistics How To. 2021 \[cited 2022 Mar 21\]. Available from: https://www.statisticshowto.com/probability-and-statistics/hypothesis-testing/anova/](#content0071.xhtml)

[84\. Chi-Square https://www.statisticshowto.com/probability-and-statistics/chi-square/](#content0071.xhtml)

[85\. Dagli, Yash. 2019. “Feature Selection Using Relief Algorithms with Python Example.” Medium. July 29, 2019. Available from: https://medium.com/@yashdagli98/feature-selection-using-relief-algorithms-with-python-example-3c2006e18f83](#content0071.xhtml)

[86\. Yu L. Feature Selection for High Dimensional Data: A Fast Correlation-Based Filter Solution. \[Internet\] Available from: https://www.aaai.org/Papers/ICML/2003/ICML03-111.pdf](#content0071.xhtml)

[87\. Bouda T. Day 43: Shuffle \[Internet\]. 100 days of algorithms. 2017 \[cited 2023 Feb 9\]. Available from: https://medium.com/100-days-of-algorithms/day-43-shuffle-b5abe4644c23](#content0071.xhtml)

[88\. Gowda D. Data Shuffling - Why it is important in Machine Learning & How to do it? \[Internet\]. 1495292331000 \[cited 2023 Feb 9\]. Available from: https://www.linkedin.com/pulse/data-shuffling-why-important-machine-learning-how-do-deepak-n-gowda](#content0071.xhtml)

[89\. Why should the data be shuffled for machine learning tasks \[Internet\]. Data Science Stack Exchange. \[cited 2023 Feb 9\]. Available from: https://datascience.stackexchange.com/questions/24511/why-should-the-data-be-shuffled-for-machine-learning-tasks](#content0071.xhtml)

[90\. Model construction: when to shuffle data and when to sort it? \[Internet\]. Cross Validated. \[cited 2023 Feb 9\]. Available from: https://stats.stackexchange.com/questions/180827/model-construction-when-to-shuffle-data-and-when-to-sort-it/180847](#content0071.xhtml)

[91\. Bouda, Tomas. Day 43: Shuffle. Medium.com May 6 2017. Available from: https://medium.com/100-days-of-algorithms/day-43-shuffle-b5abe4644c23](#content0071.xhtml)

[92\. Lever J, Krzywinski M, Altman N. Principal component analysis. Nat Methods \[Internet\]. 2017 https://www.nature.com/articles/nmeth.4346](#content0071.xhtml)

[93\. Local Outlier Factor. Wikipedia \[Internet\] \[cited 2022 April 4\] Available from: https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.LocalOutlierFactor.html](#content0071.xhtml)

[94\. Brownlee J. How to Use Discretization Transforms for Machine Learning \[Internet\]. Machine Learning Mastery. 2020 \[cited 2022 Mar 20\]. Available from: https://machinelearningmastery.com/discretization-transforms-for-machine-learning/](#content0071.xhtml)

[95\. Mavuduru A. What “no free lunch” really means in machine learning \[Internet\]. Towards Data Science. 2020 \[cited 2023 Feb 9\]. Available from: https://towardsdatascience.com/what-no-free-lunch-really-means-in-machine-learning-85493215625d](#content0071.xhtml)

[96\. Brownlee J. How to Use Power Transforms for Machine Learning \[Internet\]. MachineLearningMastery.com . Machine Learning Mastery; 2020 \[cited 2023 Feb 9\]. Available from: https://machinelearningmastery.com/power-transforms-with-scikit-learn/](#content0071.xhtml)

[97\. Skewed data \[Internet\]. \[cited 2023 Feb 9\]. Available from: https://www.mathsisfun.com/data/skewness.html](#content0071.xhtml)

[98\. Wikipedia contributors. Kurtosis \[Internet\]. Wikipedia, The Free Encyclopedia. 2023. Available from: https://en.wikipedia.org/w/index.php?title=Kurtosis&oldid=1131055207](#content0071.xhtml)

[99\. Wheeler DJ. Problems with skewness and kurtosis,  
part 2 \[Internet\]. 2018 \[cited 2023 Feb 9\]. Available from: https://www.qualitydigest.com/inside/quality-insider-article/problems-skewness-and-kurtosis-part-two.html](#content0071.xhtml)

[100\. Wikipedia contributors. Shapiro–Wilk test \[Internet\]. Wikipedia, The Free Encyclopedia. 2022. Available from: https://en.wikipedia.org/w/index.php?title=Shapiro%E2%80%93Wilk\_test&oldid=1127031375](#content0071.xhtml)

[101\. Why use the square transform to reduce left skew? \[Internet\]. Cross Validated. \[cited 2023 Feb 9\]. Available from: https://stats.stackexchange.com/questions/373239/why-use-the-square-transform-to-reduce-left-skew](#content0071.xhtml)

[102\. Box Cox transformation: Definition, examples \[Internet\]. Statistics How To. 2022 \[cited 2023 Feb 9\]. Available from: https://www.statisticshowto.com/probability-and-statistics/normal-distributions/box-cox-transformation/](#content0071.xhtml)

  

![](images/image-R49JFALW.jpg)Chapter 3

  

## Data Visualization

  

“Above all else, show the data”

—Edward Tufte, renowned American statistician

  

“This is my favourite part about analytics: Taking boring flat data and bringing it to life through visualization.”

— John Tukey

  
![](images/image-M6MTZISG.jpg)  
  

LEARNING OBJECTIVES

  
  

By the end of chapter three, readers should be able to:

•Describe why data visualization is an important early step in understanding data.

•List common data visualization plots and when they should be used.

•Compare and contrast Orange visualization widgets for numerical data vs categorical data, as well as JASP visualization.

•Recognize how visualizations aid in revealing patterns, trends, outliers, and potential anomalies in datasets.

•Appreciate how visuals can communicate complex data insights in an accessible and clear manner to a broad audience.

•Differentiate the widgets designed for continuous data versus those tailored for categorical data.

  
  

Chapter 3 Summary

  

  

Data visualization plays an important role in exploratory data analysis (EDA), serving as a key instrument for displaying data distributions, scaling, outliers, correlations, and much more. Orange offers essential widgets tailored for both numerical and categorical data visualization. A standout feature of Orange is its interactivity, allowing users to hover over or select data points in plots, then seamlessly link those selected data to other widgets, like data tables and visualizations, to delve into specific groups of interest. Meanwhile, JASP also provides a commendable range of visualization choices.

  

Key principles

•Use effective univariate, bivariate, and multivariate visualizations .

•Stratify variables by ‘who,’ ‘what,’ ‘when,’ and ‘where’ to discern patterns across analysis types.

•The box plot outlier calculation (Min = Q1 - IQR x 1.5) applies primarily to normally distributed data.

•As many standard tests (e.g., t-tests, ANOVA, regression) assume normality, validate numerical variables with the Shapiro-Wilk test.

•Use the best series of visualizations that can clearly recognize trends, anomalies, and feature interactions that are hidden in raw data.

•Strengthen arguments with undeniable visual evidence.

•Compelling visualizations will linger longer in the viewer’s mind.

•Transform numbers into compelling narratives.

•Break down complexity into digestible visualizations.

•Great visualizations can provide decision-makers with data-driven insights.

•Great visualizations can transcend language and cultural barriers.

  

  

3.1 INTRODUCTION

  

  

Individual and multidimensional data visualizations combined with stratification techniques are essential to understand the mysteries that are locked and hidden in data. Descriptive statistics are an essential and supporting stepping stones to data visualizations. This early phase of a data science project is commonly known as exploratory data analysis (EDA). Multiple programs are currently available to visualize data: Tableau, Power BI, Excel, etc. Each has its advantages and disadvantages. The free open-source stats packages of Jamovi and JASP have the advantage of generating APA quality images for publication. ¹-²

  

  

KEYPOINT: Uncover the hidden stories in your data through visualizations. As Edward Tufte says: “Above all else, show the data.” Let the data speak for itself.

  

  

[Figure 3.1 shows us that step 4 of the Data Science DISCOVER process is to cultivate insights with Exploratory Data Analysis (EDA). EDA is supported by data visualizations that are shown in this chapter. Data visualizations serve many useful purposes in data science projects. Some of them are listed below:](#content0079.xhtml)

•Simplify complex data patterns that are easier to understand and communicate.

•They enable quick insights that stakeholders can agree on.

•Enhance comprehension of complex situations.

•Visualizations improve memory and recall when compared to text or numbers alone.

•Facilitates comparisons between different data groups.

•Well-crafted visualizations engage audiences in data conversations.

•Enables and supports decision-making from various stakeholders.

•Offers an additional check on data quality, data entry errors, and outlier identification.

•Provides a common language as a basis for stakeholder communication and collaboration.

•Clear, concise, and compelling visualizations build trust and credibility in the analysis process.

•Engaging visualizations encourage further exploration and deeper analysis.

•Avoid misleading, biased, and incomplete visualizations that can lead to incorrect conclusions.

In Orange, EDA is easy to perform with visualization widgets, along with the Feature Statistics widget. JASP also offers several additional visualizations and statistics. Data distributions should be visualized for each continuous variable since highly skewed, multimodal, and other unusual data distributions can affect the performance of various statistical and machine learning models. Outliers should be identified, investigated, and handled before other methods of data transformations are performed.

Descriptive statistics alone do not always indicate the true relationships between factors in a dataset. A classic example of that is Anscombe’s quartet. In 1973, the statistician Francis Anscombe used four datasets, each with 11 data points with identical statistical properties for the means, standard deviations, and correlation coefficients but very different data visualizations. See Figure 3.1. ³ This example displays the importance of visually graphing all data in addition to just looking at its table of its descriptive statistics, which may not be a reliable early warning system for unusual data relationships.

  
![](images/image-YHA0X9J7.jpg)  

Figure 3.1 Step 4 of the Data Science DISCOVER process

  
![](images/image-OTRGQED3.jpg)  

Figure 3.2 Mean, median, mode, range, and outliers displayed

  

Rule of thumb for univariate data visualizations: for numerical (continuous or quantitative) data, use a box plot, violin plot, or histogram. For categorical (qualitative) data, use a bar plot, pareto chart, or pie chart. In Orange, the Box Plot widget will plot numerical and categorical data. The images can be saved as .png or .svg images. A report option is also available at the bottom left of most widgets, where you can add comments and share with others. The report can be saved as a .html, .pdf, or .report file.

Data visualizations can be broken out by the following groupings:

•Univariate - Histograms, Pareto charts, stem and leaf graphs, box plots, pie charts, JASP raincloud plots, violin plots, etc

•Bivariate - Scatter plots

•Multivariate - Scatter plot matrix, correlation matrix/heatmaps, BlueSky Statistics Web plots, parallel coordinate plots, nomograms, multi-factor color or symbol coding on scatter plots, JASP flexplots, and decision trees

Before we examine the various mentioned plots, let us review some basic data visualization concepts. Figure 3.2 explains the mode, median, mean, and range. Mode is the most common value, the median is the middle value, the mean is the sum of the values divided by the number of values, and the range is the difference between the highest and lowest value.

[Figure 3.3 displays a JASP descriptive statistics table, a box plot available in its Descriptives tab, and an Orange distribution plot to summarize and display the seven data points shown in Figure 3.2. The box plot shows the one outlier as a dot. This distribution plot shows that the data point “one” is the mode. The Shapiro-Wilk p-value is below 0.05, which signals that the data set does not represent a normal distribution.](#content0079.xhtml)

  
![](images/image-PHYGYN1Q.png)  

Figure 3.1 Anscombe’s Quartet ³

  
![](images/image-4Y7MVAUN.jpg)  

Figure 3.3 Descriptive statistics, Box Plot, and Distribution plot for 7 data points

  

In Figure 3.4, the 1, 2, and 3 standard deviations (STD) from the mean are displayed for a Gaussian (normal) distribution. Note that one definition of an outlier is when data points are outside of the +/-3 STD range from the mean. 68.2% of the data points are within one STD from the mean. 95.4% of the data points are within two STDs from the mean and 99.7% of the data points are within three STDs from the mean.

[Figure 3.5 demonstrates left (-) and right (+) skewness. Orange can transform skewed data using the Feature Constructor widget to make it look more normal, as discussed in the previous chapter. JASP offers power transformations that make skewed data more normal, as discussed in the previous chapter. Note: most medical datasets are skewed to the right because results are not less than zero; hence there are usually no values below zero.](#content0079.xhtml)

  
![](images/image-ZF0W9E7P.png)  

Figure 3.4 Normal distribution with standard deviations displayed

  
![](images/image-B0T0HXX4.png)  

Figure 3.5 Left and right skewed data

  

The visualization plots discussed in section 3.2 will be organized into ten categories. Appendix A also lists the categories, the visualization types, the purpose of each plot, supporting statistics, and whether the plots are supported by Orange, JASP, and BlueSky Statistics. ⁴

  

3.2 DATA VISUALIZATION TABLES AND PLOTS

  

  

Many of the Orange visualization widgets that display categorical values also include a chi-square test and a p-value to indicate statistical significance. This test determines if categorical variables’ observed and expected frequencies are significantly different. For example, in Figure 3.6, a box plot of data science experience levels is displayed. The chi-square test shows a p-value of 0.000, demonstrating that there are statistically confirmed differences in the proportions of experience levels in this dataset.

  
![](images/image-HHX42ER3.png)  

Chi-square (YouTube)

  

#### 3.2.1 Statistical Tables and Displays

  

Statistical tables and displays are used to organize and present data in a clear and concise manner. They are commonly used in research papers, scientific studies, and business reports to summarize and communicate findings.

  
![](images/image-MQMO976U.jpg)  

Figure 3.6 Chi-square calculation of data science experience levels

  

3.2.1.1 Pivot Table

  

Orange pivot tables were discussed in Chapter 2, section 2.5.10. A pivot table “pivots” or switches columns with rows, thus giving you a different data representation.

  

3.2.1.2 Feature Statistics

  

The Orange Feature Statistics widget was covered in Chapter 2. This widget allows you to examine the visualization of each variable. The widget creates basic plots for numerical and categorical data. You can group (color) by any categorical feature, such as blue for no heart disease and red for heart disease. The widget calculates and displays the mean, mode,median, dispersion, min, max, and number/percent of missing data points. The dispersion of categorical data is its entropy (degree of uncertainty). For numerical data, it is the coefficient of variation (standard deviation divided by the mean).

  

3.2.1.3 JASP Descriptive Statistics and Tables

  

[Table 3.1 displays common descriptive statistical measurements on the adult income dataset.⁵ The goal of this dataset is to predict whether the subject’s income will be greater or less than $50K. Simply check the appropriate boxes for the desired statistics, and the tables are created. Other options for the table include quartiles, percentages, skewness, kurtosis, mode, median, variance, standard error, and coefficient of variation. There is also an option box to transpose the values in the table from columns to rows.](#content0082.xhtml)

[Table 3.2 displays a frequency table for race. From the table, you can see that white subjects were most common in this dataset.](#content0082.xhtml)

  

3.2.1.4 Stem and Leaf Table

  

[Table 3.3 displays a stem and leaf table for cholesterol levels. This provides a univariate summary of a single variable. The stem represents a digit x 10, and the leaf represents a single digit. For example, the first stem = 12 and the leaf = 6, so this represents one patient with a cholesterol of 126 which represents the minimum cholesterol value in this dataset. The second stem = 14 and the leaf values = 199 represents three patients with cholesterol levels of 141, 149, and 149. The maximum value of the graphic is 564. Most cholesterol values fall between 200 and 260, based on the table. The range would be 564-126 or 438. JASP offers stem and leaf tables under the Descriptives tab under the Tables section.](#content0082.xhtml)

  

#### 3.2.2 Basic Data Displays

  

Basic data displays refer to the fundamental methods of representing and visualizing data to facilitate understanding and analysis. These displays are commonly used in various fields, including mathematics, statistics, research, and business.

  

3.2.2.1 Bar Charts

  

The Orange Bar Chart widget displays every subject/patient, so it is not the correct widget to visualize groups. The Distributions widget displays histograms for continuous data and bar charts for categorical data. However, when the Box Plot widget is used and the box “sort by sub-group frequency,” is selected, a bar graph is displayed with the highest frequency data displayed first.

  

Table 3.1 JASP Descriptive Statistics

  
![](images/image-GT7QW9Y3.png)  

Table 3.2 JASP Frequency Table

  
![](images/image-0P8T8WWJ.png)  

Table 3.3 Stem and Leaf Table of cholesterol

  
![](images/image-G9PBV5X0.png)  

3.2.2.2 Histograms

  

The Distributions widget provides histograms and density plots for numerical data and bar graphs for categorical data. Figure 3.7 displays a histogram of age for the adult income dataset. A majority of subjects are under age 50. Different bin widths should be tested as it can significantly affect the display.

  
![](images/image-878QR8I0.png)  

Figure 3.7 Histogram of age

  

[Figure 3.8 shows a bar graph of adult income by gender. In the Distributions widget, select gender as the variable and split by income. Also, select “stack columns.” It appears there are more men with incomes below and above $50K, presumably because there are more men in the workforce.](#content0082.xhtml)

  
![](images/image-NLLBYV90.png)  

Figure 3.8 Adult income by gender

  

3.2.2.3 Dot Plots

  

A dot plot is part of the raincloud plot found in the distributions category where it displays each data point with a dot.

  

3.2.2.4 Pie Charts

  

This plot is one of the simplest methods to display categorical data that is also easy to understand. It is unclear why this method is found under the educational rather than the visualization menu. Pie charts are discouraged for use with complex data since the pie slices become illegible. In Figure 3.9, there is a pie chart of marital types by income with a legend. Clearly, there are many married couples with income >$50K.

  

3.2.2.5 Pareto Charts

  

Pareto charts provide a bar chart graphic sorted by the highest to the lowest frequency of a categorical variable from left to right. Pareto charts can be created in JASP and quasi-Pareto charts can be created in Orange. Classic Pareto charts have a cumulative percentage line and a vertical axis on the right that corresponds with the cumulative percentage line so that the 80/20 Pareto rule can be checked. A quasi-Pareto chart does not have a cumulative percentage line and just sorts the bars by frequency with no direct way to test for the 80/20 Pareto rule.

The Pareto chart in Figure 3.10 shows the general responses from a 14- to 18-year-old health survey. It plots the frequencies for the question: “How do you describe your health?” The Pareto chart can be split with another categorical variable creating a separate chart for each selected sub-group. To create a Pareto chart in JASP, select the Descriptives tab > Descriptive statistics > select variables and split (if desired) > Basic plots > check Pareto plots > optional Pareto rule (80% or other).

Quasi-Pareto charts (aka: frequency-sorted bar charts) can be created in Orange with the help of the Distribution widget, as shown in Figure 3.11. You should select categorical variables to create these quasi-Pareto charts and then check the “sort categories by frequency” box. These quasi-Pareto charts can also be stratified by selecting another categorical variable in the “Split by” section, as shown in the figure. This quasi-Pareto chart shows the discharge disposition of patients from a home health care program broken out by gender. It shows how many patients were discharged back into the community with and without assistance or if they were discharged to non-institutional hospice.

  
![](images/image-MWW1IKC4.png)  
![](images/image-P6IF1YKB.png)  

Figure 3.9 Pie chart of marital types by income

  
![](images/image-H2LALBY2.jpg)  

Figure 3.10 Pareto chart in JASP

  

#### 3.2.3 Distributions

  

A distribution refers to the way in which a variable or set of data is spread out or dispersed. It shows how frequently each value or range of values occurs within a dataset. The distribution can be represented in various ways, as described in this section. Understanding the distribution of a dataset is important in data analysis as it helps to identify patterns, trends, and outliers. It also provides insights into the central tendency, variability, and shape of the data.

  

3.2.3.1 Violin Plot

  

The Violin Plot widget provides similar information as the box plot and only works for numerical data. Select the violin plot and optional density dots to see the actual data points if desired. Choose the default Normal kernel and Scale = area. We will use the wine quality dataset.⁶ The goal is to see if you can predict which attributes predict three different Italian wines. In this widget, we will plot alcohol percentage by the three different wine types. Note in Figure 3.12 that wine class 2 has the lowest alcohol content. Compare the results with the box plot display of the same variables.

  
![](images/image-3VN0X0PO.jpg)  

Figure 3.11 Pareto Chart in Orange

  
![](images/image-LQNF9X97.png)  

Figure 3.12 Violin plot of alcohol levels by wine class

  

3.2.3.2 Distribution Plot

  

This widget provides histograms for numerical data and bar graphs for categorical data. Figure 3.13 displays a histogram for wine flavonoids for the three different wines. Distribution was set on none, we chose stacking and split on class.

  
![](images/image-104UXX80.jpg)  

Figure 3.13 Histogram of wine flavonoids

  

  

KEYPOINT: Many common statistical tests (t-tests, ANOVA, regression, etc.) assume a normal distribution so every numerical variable should be visualized before these statistical methods are going to be used.⁷

  

  

Note the difference in flavonoid concentrations for the three wines and the outlier for class 2. Mouse over individual bins in the graph to get exact numbers and percentages for their content. Histograms will change based on bin width, so it is a good idea to visualize data with different bin widths. Figure 3.14 displays the distribution curve known as “kernel density.” You can visualize the curve only by selecting the “Hide bars’’ option.

  
![](images/image-QWMKNNZ9.png)  

Normal Distribution (StatQuest)

  
![](images/image-WRJ1ASL7.png)  

Histograms (StatQuest)

  

JASP offers a unique data visualization called a raincloud plot under the ANOVA header as shown in Figure 3.15. To create a Raincloud plot, follow these steps:

1\. Select a continuous variable of interest and enter it in the “Dependent Variable” section at the start of the ANOVA option.

2\. Enter a categorical variable of interest in the “Fixed Factors” section at the start of the ANOVA option.

3\. Go to the Raincloud Plots tab and enter the categorical variable of interest in the “Horizontal Axis” section.

4\. Check the “Horizontal display” option if you do not want a vertical display.

  
![](images/image-I4JV75TH.jpg)  

Figure 3.14 Distribution of flavonoids by wine variety

  
![](images/image-PNAO4ZHF.png)  

Figure 3.15 JASP stratified raincloud plot combining a histogram, box plot, and dot plot

  

A raincloud plot and raincloud difference plots can also be created under the t-test menu by entering pairs of continuous variables you want to compare. This unique graph offers the same information as shown in Figure 3.14 except that it stratifies the graphs by wine types into three graphs and offers combination graphics (histogram, boxplot, and dot plot) for each feature to maximize the insights that can be gained from multiple visualizations displayed on the same graph.

Next, we will look at plotting the distribution of categorical data. The categorical variable race in the adult income dataset was selected because it has multiple categories. The data was split by the target “income,” and the stack columns option was selected. Figure 3.16 shows that this is a bar graph with spaces between columns, unlike histograms, where columns are usually contiguous. Note: once again, you can click on any bar and send that specific data to a data table for further analysis.

  

3.2.3.3 Raincloud Plot

  

The JASP stratified raincloud plot combines a histogram, box plot, and dot plot. This was displayed in the Distributions section 3.2.3.2

  

3.2.3.4 Q-Q Plot

  

JASP offers a Q-Q (quantile-quantile) plot to visually determine if the data is normally distributed. Quantile derives from the word quantity and means where a sample is divided into equal-sized, adjacent sub-groups. The median is a quantile because half of the data is below it and half above. The Q-Q plot compares a theoretically normal distribution (x-axis) with the actual distribution (Y-axis). The straight diagonal line in JASP represents a normal distribution, and the dots represent the sample data. The closer the sample data matches the diagonal line, the more normal the data is. You can create a Q-Q plot in JASP by going to the Descriptive tab > Descriptive Statistics > Basic plots > Q-Q plots. Keep in mind that this is just a visual check for normality. Only a valid statistical test, such as the Shapiro-Wilk test for normality, can tell us with high certainty if the data feature is normal or not. The Shapiro-Wilk test for normality can be conducted in the Descriptives tab in JASP and found under the Statistics tab and elsewhere.

  
![](images/image-6N2KLC0Q.png)  

Figure 3.16 Distribution of race by income

  

[Figure 3.17 shows a Q-Q plot for wine alcohol content. It falls close to the diagonal line in the middle, but at the lower or higher ends it does not.⁸](#content0083.xhtml)

  
![](images/image-ZKP15DKH.png)  

Figure 3.17 Q-Q Plot of wine alcohol content

  

[Figure 3.18 shows a normality test run in JASP with the p-value < 0.05, indicating that it is not a normal distribution.](#content0083.xhtml)

  
![](images/image-48EG2PH6.png)  

Figure 3.18 Shapiro-Wilk test

  

#### 3.2.4 Relationships Between Variables

  

As we review variable relationships with various visualizations, it is important to consider that correlation does not necessarily imply causality, for the following reasons: ⁹

•The existence of third or hidden variables : It’s possible that the apparent connection between two variables is caused by a third variable that wasn’t examined in the study. For instance, a study might find a correlation between the sale of rain boots and the consumption of hot chocolate, but the underlying factor might be rainy weather, which prompts both boot wearing and a desire for warm drinks.

•Reverse causation may be present: This is the classic chicken and the egg paradox: what came first. Does physical inactivity cause weight gain or is the opposite true? Does smoking cause depression, or is the opposite true?

•Measuring sensitive topics : Because the outcomes we’re interested in are frequently challenging to gauge and can only be imperfectly seen, measurement error is a possibility. For instance, encouraging people to report information on touchy or controversial subjects may produce unreliable results.

•Coincidental Correlation : When simply stating that the proof of causation is an existing correlation, this presumption of causality is incorrect. For instance, simply because vaccination rates and autism rates are both increasing does not always imply that vaccinations are to blame.

Finally, it’s critical to keep in mind that correlation does not necessarily equate to causation and to carefully analyze any potential confounding variables in any reported link between two variables.

  

3.2.4.1 Scatter Plot

  

A scatter plot is a graphical representation that displays the relationship between two variables (columns) in a dataset. Each point on the plot represents a pair of values for the two variables being studied. Using scatter plots to explore visual relationships between variables, researchers and analysts can gain insights into complex systems and make data-driven decisions. Scatter plots have a wide range of practical applications, including:

•Exploring correlations: Scatter plots are often used to explore the relationship between two variables. This relationship is typically represented by a “best fit” line that software draws as a smoother, linear, or polynomial line to show the relationship between the two variables.

•By visually inspecting the plot, it is possible to see whether the variables are positively or negatively correlated or have no correlation.

•Identifying outliers: Scatter plots can also identify outliers in a dataset. Outliers are data points that fall outside the normal range of expected values for the dataset and can often be easily spotted on a scatter plot.

•When outliers are detected, it is wise to stratify the data with existing categorical variables in the dataset (such as gender and other factors) to see if stratification can explain the presence of the outliers.

[Figure 3.19 displays four different variations of scatter/flex plots in Orange and JASP to explore various visualization options, including the presence of heart disease (1/0) for two predictors: the number of major vessels colored vs. the patient’s age. (major vessels colored means the number of coronary arteries that contain calcium on imaging). It is more important to correctly interpret a graphical visualization than to just create the graphics with no guiding insights. The following four interpretations are examples of correctly interpreting the four graphics in Figure 3.19:](#content0084.xhtml)

•Orange Color-Coded Stratified Linear Scatter plot: Darker dots and shading represents heart disease, and lighter dots and shading represents no heart disease. The darker-shaded areas on the scatter plot show the factors associated with heart disease. The lighter -shaded areas on the scatter plot show the combination of factors associated with no heart disease. The reported r-value corresponds to the r-value from linear least-squares regression, equal to Pearson’s correlation coefficient. The best three linear regression lines that fit the data are shown.

  

![](images/image-TEMD15Y1.jpg)The regression line with the highest correlation (incline) between age (x-axis) and the number of major vessels colored (y-axis) represents just those patients with heart disease. The correlation coefficient for this subgroup is 0.37.

  

![](images/image-TEMD15Y1.jpg)The regression line with the second highest correlation (incline) between age (x-axis) and the number of major vessels colored (y-axis), which is the black line in the middle, represents the average for heart disease and no heart disease patients. The correlation coefficient for the whole group is 0.36.

  

![](images/image-TEMD15Y1.jpg)The regression line with the lowest correlation (incline) between age (x-axis) and the number of major vessels colored (y-axis) represents those patients with no heart disease. The correlation coefficient for this subgroup is 0.25.

•Orange fourth order Polynomial Regression plot: The Polynomial Regression widget is only available when you add it with the educational add-ons option. You attach it directly to the File widget in Orange. This widget allows you to explore best-fit curve visualizations up to a maximum of 10 degrees in this widget. This graphic in the widget shows that after the age of approximately 38, a positive and steady correlation exists between age (x-axis) and the number of major vessels colored (y-axis).

•JASP Scatter plot with a smoother line, confidence intervals, and marginal density plots: This graphic shows that a positive and steady correlation exists between age (x-axis) and the number of major vessels colored (y-axis), as displayed with a wiggly best fit smoother line. The 95% confidence intervals (Cis) are also shown for this best-fit line. The wider CIs on the left and right of the graphic are due to the lower amount of data available in those regions. This graphic also displays a histogram for the x-axis and y-axis data in the margins of the graph to visualize further how much data is available at various points along the x and y-axis.

  
![](images/image-ER8J22IK.jpg)  

Figure 3.19 Examples of scatter and flex plots in Orange and JASP

  

•JASP Flex plot with cubic fitted lines: This unique graph shows individual cubic best fit curves for each of the numbers for the number of major vessels colored on the graph, with the y-axis being the presence of heart disease (1) or not (0) in relationship with age (x-axis). We can see that three major-colored vessels have the highest risk of diameter narrowing, while one major-colored vessel has the lowest risk of diameter narrowing. The dots on the zero and one position on the y-axis represent the presence of data, but overlapping data is certainly present. All overlapping data can be seen by adjusting the “jitter” option.

Orange has an important feature in the Scatter plot widget: “Find Informative Projections,” which will automatically find, list, and display the highest correlation scatter plot displays once you click on the “start” tab in the “Find Informative Projections” tab and click on the desired scatter plot to display. Figure 3.20 shows an example of the “Find Informative Projections” tab results on the left and the highest correlation scatter plot in the data set on the right. You can click on any of the other scatter plots on the left, and they will be instantly displayed.

Finding strong positive or negative relationships can help you select the best variables for a statistical or machine learning model. Another valuable option is to mouse over a data point to understand its features and class. You can also highlight the data point(s) and connect it to a data table for further study.

  

3.2.4.2 Contour Plot

  

Contour plots are also known as contour density plots or 2D density plots. They clearly show the level of data overlaps (density) present in a scatter plot without jittering the data. Jittering is a random X and Y-axis displacement of the data to display more data symbols that represent overlapping data points.

The contour plot’s innermost circle(s) on a contour plot shows the highest data point density. The other circles radiate outwards from the inner circle and represent lower data point density regions. This method can display the strength of a relationship between 2 variables while exposing patterns, clusters, outliers, and hidden insights that may be missed with a normal scatterplot.

[Figure 3.21 shows an example of four contour plots that compare the monthly Google search interest in the following search terms for the USA: boat, beach, bike, and motorcycle. We previously showed a time series graphic for these search terms that showed a strong annual seasonal interest in these terms. We created these graphics in BlueSky Statistics by going to their Graphics section and selecting Contour Plot. Then you enter your dataset’s X and Y variables of interest to create the graphics.](#content0084.xhtml)

  
![](images/image-CQHG7U0X.jpg)  

Figure 3.20 The results of the “Find Informative Projections” option in the Scatter plot widget

  
![](images/image-X5ZJMIZM.jpg)  

Figure 3.21 BlueSky Statistics Contour plots for Google search term interest

  

The upper right contour plot in Figure 3.21 displays Boat versus Beach search term popularity. That contour plot shows a clear positive linear relationship between those search terms with a high density of the data points in the lower third of the X and Y axis coordinates. The other three contour plots also show similar relationships between their chosen X and Y axes features. However, their correlation and density distribution patterns are more irregular and inconsistent than the top right contour plot.

  

3.2.4.3 Mosaic Plot

  

This visualizes a contingency table of qualitative variables that can also be used with binned continuous data. Figure 3.22 shows a simple mosaic plot with two of the four fields filled out for a home healthcare dataset where the nurse-certified assessment for the Activity of Daily Living (ADL) starting scores are shown on the x-axis. The higher the ADL starting score, the more help patients need to conduct simple activities to maintain a safe and effective independent lifestyle in their homes. The width and height of a mosaic “slice” correlates with the amount of data in each subgroup. As shown in the figure, you can hover over any of the slices to get an information box that describes the contents. What we can visualize in this graph is that patients 85 years or older tend to be members of higher ADL starting score groups. Patients under 75 have higher participation in lower ADL starting score groups.

  
![](images/image-BWUJSX98.jpg)  

Figure 3.22 A Mosaic plot with two features displayed

  

In addition, there is the option to select “Find informative Mosaics” from the data set. Do not forget that you can select an area of interest on this and most other plots and then connect it to a data table and additional visualization widgets. Also, you can select two more variables for the plot, but this makes the plot difficult to interpret.

[Figure 3.23 shows a mosaic plot with all four mosaic plot fields filled in to display age group, ADL starting score group, sex, and the ADL improvements achieved for these patients during home health care therapies. Such a graph is rich in detailed content but more complex to understand. You can hover over any sub-group in the graph to view a pop-up box explaining each slice’s details in the mosaic plot, as shown in the figure.](#content0084.xhtml)

  

3.2.4.4 Sieve Diagram

  

This widget (also known as a parquet diagram) plots a pair of categorical variables to show frequencies using a contingency table. The area of each rectangle is proportional to the expected frequency, while the observed frequency is shown by the number of squares in each rectangle. The difference between observed and expected frequency displays as the density of color shading where blue (upper left and lower right) is positive and red (upper right and lower left) is negative. In Figure 3.24 Titanic survival is compared by sex. The chi-square statistic and p-value (<0.05) display a statistically significant difference. Male survival was lower than expected. Mouse over a rectangle to get the expected vs observed statistics. Choose “Score Combinations” to find interesting data pairs.

  
![](images/image-MMVQAF32.jpg)  

Figure 3.23 A Mosaic plot with four features displayed

  
![](images/image-VWRJI64F.png)  

Figure 3.24 Sieve diagram of survival and sex in the Titanic dataset

  

#### 3.2.5 Time Series

  

Time series displays refer to the visual representation of data points collected over a specific interval of time. Time series analysis involves analyzing and interpreting these data points to identify patterns, trends, and relationships over time. Time series displays are widely used in various fields, including statistics, economics, finance, weather forecasting, and environmental studies.

  

3.2.5.1 Line Chart

  

Orange offers time series plots with its Line Plot widget, but you can only show one line in a time plot. JASP also offers time plots in its Prophet and Quality Control sections, but they also have the same limitation as Orange, with only one line per graph allowed.

  

3.2.5.2 Area Chart

  

See Mosaic Plot

  

3.2.5.3 Time Series Plot

  

Time-series plots can be created in Orange and BlueSky with multiple lines per graph.

•Follow these steps to create such a graph in BlueSky : upload a file in wide format > Go to Forecasting > Time Series, Separate or Combined > enter all of the desired features to plot in the “variables to Plot” section, enter the time of first observation > enter the number of observations per unit of time > check the “combine series” option.

•Follow these steps to create such a graph in Orange : Make sure that you upload a data file to the File widget in a wide format that either has a date column or a sequence number to be used for the X-Axis time scale > Attach the Line Chart widget to the file widget > Highlight all of the columns of data that should be included in the same graph > Orange will automatically determine which column it should use for the time scale axis.

[Figure 3.25 is an Orange Time Series plot with five separate lines on the same graph showing the seasonal monthly trends for five different Google search terms from January 2004 to May 2023. Currently, JASP cannot create a time series plot with multiple lines on the same graph. You can also use the Orange Preprocess widget to normalize the Y-Axis to an interval and re-run the chart for comparison.](#content0086.xhtml)

  

#### 3.2.6 Geographical Displays

  

Geographical displays refer to the visual representation of geospatial data on a map. They are used to communicate information about the location, distribution, and characteristics of geographic features and phenomena. Geographical displays are important for understanding and analyzing geospatial data. They help to identify patterns, trends, and relationships between different variables and can be used to make informed decisions based on the data.

  
![](images/image-8WT88Q9T.jpg)  

Figure 3.25 Time-Series plot in Orange

  

3.2.6.1 Choropleth Map

  

[Figure 3.26 shows color coding for average life expectancy per selected country. This is visually appealing,intuitive, and easy to interpret.](#content0086.xhtml)

  

3.2.6.2 Geolocation Map

  

Geo-Mapping is available in Orange and BlueSky Statistics. Geo-mapping is also referred to as geospatial mapping or geographic mapping. This method can display data and information on a map using specific latitude and longitude coordinates for any location in the world. The applications for Geo-Mapping are numerous and their applications are only limited by the analyst’s imagination and available data.

Some examples of geo-mapping include the following: Resource planning, infrastructure project planning, environmental monitoring, public health statistics, crime statistics, census data representations, real estate data, urban planning, business and marketing strategic planning, transportation and logistics planning and optimization, weather data tracking, weather forecasting, and much more.

[Figure 3.27 shows the Orange workflow required to initiate Geo Mapping.](#content0086.xhtml)

  
![](images/image-YVEQCLJ9.png)  

Figure 3.26 Choropleth plot of life expectancy by country

  
![](images/image-K1R4TH2W.jpg)  

Figure 3.27 Orange workflow to create a Geo Map

  

[Figure 3.28 shows the altered latitude and longitude locations for a long-term longitudinal study based on synthetic patient data provided by Synthea, which ensures patient confidentiality by replacing all real patient data with synthetic data which is similar to but not perfectly matched with the real data. This Geo-Map also color codes the patient’s race.¹⁰ This topic will be discussed in later chapters in more detail.](#content0086.xhtml)

  
![](images/image-URVN0BOT.jpg)  

Figure 3.28 Altered patient locations for a long-term longitudinal study with synthetic data

  

#### 3.2.7 Hierarchical Displays

  

The visualization or presentation of data in a hierarchical structure, generally in the shape of a tree, is referred to as a hierarchical display. Data points connected to one another via parent-child relationships, forming a tree-like structure, make up hierarchical data. We simply show two of the most popular displays that are available in Orange and JASP out of the various display options for this category of display types.

  

3.2.7.1 Treemap

  

See Decision Tree in section 3.2.9.1

  

3.2.7.2 Hierarchical Clustering Plot

  

Hierarchical clustering is a specific clustering algorithm used in data analysis and machine learning to visually display the similarity or difference between groups of predictors (features) in a dataset as they relate to a target variable. This clustering method displays the resulting clustering results in a tree-like graphic called a dendrogram. The dendrogram positions the features more similar to each other as close neighbors on the tree. Those features that are dissimilar to each other are positioned as more distant neighbors on the same branch or on a different branch. If features are located on a different branch on the dendrogram tree, this indicates that a group of features is quite different from the group of features on the other branches.

Clustering is a useful technique for the following reasons:

•It is useful in the grouping of unlabeled data in unsupervised data.

•It is useful in exploratory data analysis (EDA) to understand the relationship and groupings present between different features.

•It can be used for anomaly and outlier detection.

•Dimensionality reduction can be guided by the results of clustering.

•Clustering can be used on data from customers, patients, images, and text documents and for other analysis.

[Figure 3.29 shows the Orange workflow and Distance Widget settings used for this example of hierarchical clustering. Various methods can be chosen to determine the distances between rows and columns (features) that are the basis for the displayed clustering results.](#content0088.xhtml)

[Figure 3.30 displays the predictors present in the Cleveland-Hungary-Statlog Heart Disease dataset as they relate to the presence of heart disease for a patient.¹¹ The number of clusters can be controlled by adjusting the height ratio of the dendrogram, as shown in Figure 3.30. More details about clustering will be discussed in the chapter about unsupervised learning.](#content0088.xhtml)

  

#### 3.2.8 Multivariate Displays

  

Multivariate displays refer to the visualization of data that involves more than two variables. These displays are useful for understanding the relationships between multiple variables and identifying patterns or trends that might not be apparent when looking at individual variables.

  
![](images/image-H9KQJYMX.jpg)  

Figure 3.29 Orange hierarchical clustering workflow

  
![](images/image-B7AYX2FH.jpg)  

Figure 3.30 Orange hierarchical clustering display options

  

3.2.8.1 Correlation Matrix

  

JASP can create a correlation matrix so you can observe correlations among many variables. The correlation matrix is found under the regression menu. For this section we will use the Global Information dataset.¹² Table 3.4 shows a correlation matrix of GDP (gross national product), infant mortality, life expectancy and birth rate. Note the numerical correlations and the p-values. For example, there is a positive correlation of 0.176 between GDP and life expectancy and a statistically significant p-value of 0.016.

  

Table 3.4 Correlation matrix of the heart disease prediction dataset

  
![](images/image-NK6TIEQ8.png)  

A correlation matrix is similar to a heatmap that can also be created in JASP. The heatmap plot in Figure 3.31 is also found under the JASP regression menu and correlation. It creates a color chart associated with the same Pearson correlation results. Negative correlations light red are dark red and positive correlations are light violet or dark blue. The stronger the relationship, the darker the color.

  
![](images/image-FYWUL9PL.png)  

Figure 3.31 Heatmap of GNP, infant mortality, life expectancy and birth rate

  

3.2.8.2 Correlation Webplot

  

BlueSky Statistics offers a variety of ways to check the relationships between features.The most visually compelling ones are Correlation Webplots as shown in Figure 3.32. The thickness and colors of the lines connecting the features in this plot define the level of correlation and direction (positive or negative) of the correlation. Blue thick lines define a strong correlation, while thin red lines depict a weak negative correlation between features. You can create these displays by opening BlueSky Statistics and following this path: Analysis > Correlations > Pearson Legacy > Visualize webPlot > Select variables of interest.

[Figure 3.32 is a BlueSky Correlation Webplot that shows the correlation between monthly Google search terms (beach, boat, motorcycle, bike, and car) for over a nine year period of time. The legend shows the r-values for specific line thicknesses. An additional and optional correlation heatmap is also available for those who appreciate that visual display. JASP offers similar displays.](#content0088.xhtml)

  
![](images/image-KJZ7V8DS.jpg)  

Figure 3.32 Correlation Webplot in BlueSky Statistics

  

3.2.8.3 Network Plot

  

The Network section in JASP offers various Network Plot options to display the strength of association between features visually. Stronger associations between features (nodes) are represented by thicker and darker lines (edges). The coloring of the lines represents positive or negative associations between features. A Weights matrix is also available, which displays the numerical association strength between all features. The variable names can be displayed in a legend or plot. High legend-to-plot ratios can be selected, which ensures that long feature descriptions will be fully visible. Label font size and abbreviation options are also available.

[Figure 3.33 shows the Spring and Circle layout options for the JASP Network Plot, including all features available in a percent body fat dataset. A shortcoming to this graphic in JASP is that it is limited to how many features it can label in the legend.](#content0088.xhtml)

  

3.2.8.4 Scatter Plot Matrix

  

JASP offers this graphic in their Descriptive Stats section, where you need to check the “Correlation plot” after entering all of the features that you want to be included in the matrix. JASP will then create a matrix, as shown in Figure 3.34, that includes every possible scatter plot that can be created with the features that have been entered. This matrix will include distribution plots, scatter plots, and linear best-fit lines for each scatter plot. This comprehensive and detailed matrix allows the analyst to identify linear and non-linear relationships, skewing, outliers, patterns, or the lack of a relationship. It provides an easy-to-interpret visual comparison for all selected features to identify the strongest and weakest correlations quickly.

  
![](images/image-C47VKD73.jpg)  

Figure 3.33 Two options for network correlation plots in JASP

  
![](images/image-114QTN74.png)  

Figure 3.34 JASP scatter plot matrix display

  

3.2.8.5 Linear Projection/3D Plot

  

The Linear Projection widget displays a 3-D image of continuous data from three columns at the same time. The recommended variables will be shown using the Select Features option and the default selection “circular placement” and “Suggest Features” options. In this example, glucose, waist\_hip ratio, and systolic BP are displayed as shown in Figure 3.35, which shows the linear projection of these three variables. One data point (arrow) is highlighted and sent to a Data Table for further analysis of an obvious outlier. In the Data Table widget, the glucose was 270, yet the patient must have had a normal Hgb A1c or would not have been labeled non-diabetes. Unfortunately, this graphic cannot be 3-D rotated to view this data visualization from different perspectives. Under the Suggest Features tab, more than 3 variables can be selected for the display if the data is available but that adds much more complexity when interpreting and explaining the display.

  

3.2.8.6 Parallel Coordinates Plot

  

Parallel Coordinate Plots (PCPs) are one of several different multivariate data visualizations that can be created with the Line Plot widget in Orange. PCPs offer clarity to high-dimensional data displays. A parallel vertical axis represents each variable, and each data point is represented as lines connecting their respective coordinates for each variable. The lines and color-coded patterns are useful for detecting correlations, dependencies, relationships, outliers, patterns, clusters, groupings, and unusual groupings in complex datasets.

  
![](images/image-UB2JH0E5.png)  

Figure 3.35 Linear Projection widget results

  

Normalizing the data used for this graphic is advisable when there are large differences in the scales of the variables displayed. The Orange workflow in Figure 3.36 allows you to experiment with normalized and non-normalized data to determine which option offers the best interpretations and insights for the PCP.

[Figures 3.37 (data not normalized) and 3.38 (data normalized) show a multivariate display of selected features for two patients in a ten-year heart disease study. Patient #1 has experienced heart disease over ten years. However, patient #2 has not.](#content0088.xhtml)

[Figure 3.38 used normalized data with a 0,1 interval which spread out some of the variable scaling to provide visual clarity for some of many features whose values appeared to be very similar or identical on the non-normalized PCP (Figure 3.37). For example, the education feature’s values appeared identical on the non-normalized display due to their small numerical range between two and three. However, when normalized, their differences were brought into focus to provide additional insights.](#content0088.xhtml)

  
![](images/image-3DFZCYLX.jpg)  

Figure 3.36 Orange parallel coordinates plot / line plot workflow

  
![](images/image-U2S6W1H6.jpg)  

Figure 3.37 Orange Parallel Coordinates Plot / Line plot - not normalized

  
![](images/image-QW2ZY4DQ.jpg)  

Figure 3.38 Orange Parallel Coordinates Plot / Line plot - normalized

  

PCPs can facilitate meaningful stakeholder engagement, discussions, and education since these displays are easy to interpret and enable a shared understanding to promote collaborative decision-making on complex issues.

  

#### 3.2.9 Statistical Models and Displays

  

3.2.9.1 Decision Tree

  

The Tree Viewer widget displays the results of a simple decision tree (DT). Figure 3.39 shows a typical tree structure and its terminologies. The DT begins with the root node and keeps dividing/splitting until you reach the leaf node’s final level. A leaf node means you cannot make any further decisions or splits. In Orange, It tells you the number of nodes and leaves, and you can zoom in and out and download the results. You can also set the depth of the tree. Be sure to select the target class. We will use the wine dataset so there are three outcomes. For Figure 3.40, we set (pruned) the max depth to level = 3 to easily visualize the whole tree in one image. The three colors reflect the three wine varieties. For wine variety three, the flavonoids are less than 1.57, and the color intensity is greater than 3.8.

Note that you need to connect the Tree widget to the File widget and then to the Tree Viewer widget to view the tree. It is common in data science to start with a simple tree to visualize data as the results are easy to interpret, unlike bagged or boosted trees. DTs can be selected with more Depth levels to view more complex DTs. In the next chapter, we will point out some DT shortcomings.

  

3.2.9.2 Interval Plot

  

Confidence interval plots are an important data visualization tool to assess if the confidence intervals (CIs) for the means for multiple groups overlap or not. When the CIs overlap for two or more groups, that provides us with a compelling visual and statistical signal that the means are statistically indistinguishable from each other, no matter how different the means are numerically from each other. Conversely, non-overlapping CIs for a group comparison provides a clear statistical signal that the means are statistically dissimilar.

It is most common to use 95th percent confidence intervals, which are calculated with the following equation: Mean +/- 1.96\*(SD/sqrt n).¹³

Whereby:

•n : Sample size

•SD : Standard deviation of the sample data

•SE (Standard Error) of the mean is ¼ of the total CI range

•The confidence interval line extends on either side of the mean

From the equation for CIs, we can see that CI width will increase with higher SD and lower n values. Lower SD and higher n values create narrower CIs.

The presence of overlapping CIs should not be interpreted as final proof for the similarity assumption between two or more groups. This caution arises from the fact that the additional data collection could narrow the CIs and potentially overturn the initial assumption of similarity if the CIs become narrow enough to overlap no longer, which would effectively challenge and reverse the initial assumption of similarity between the groups of interest.

  
![](images/image-RRY08O7W.png)  

Figure 3.39 Typical decision tree schema (courtesy JavaPoint.com)

  
![](images/image-8ROGURBG.png)  

Figure 3.40 Pruned decision tree for the wine dataset

  

[Figure 3.41 provides a visual display of the dynamic nature of CIs when sample sizes increase within the dataset. In this initial plot on the left, we observe overlapping CIs for groups A25 and B25, each with a sample size 25.](#content0089.xhtml)

As we shift our focus to the middle of the graphic, Group A and B now have increased sample sizes of 200 samples each. Despite the means remaining constant for these groups, the narrowing of confidence intervals narrowed sufficiently and now suggests a different conclusion than before. We have non-overlapping CIs for these groups, and we can conclude that the means for these two groups are dissimilar.

Finally, on the far right, the sample sizes for groups A and B have now inflated to 1000 each. This has further narrowed the CIs for groups A1000 and B1000, whereby we can now further conclude that the means for these groups are truly and statistically dissimilar.

Confidence Interval plots can be created in JASP from the Descriptives section. They are available under the “Basic Plots” section. Long or “stacked” data is required to create these plots where the numerical data should be entered in the “Variables” section, and the group name should be entered in the “Split” section.

  
![](images/image-ST841S4S.jpg)  

Figure 3.41 Interval Plots for groups with different sample sizes

  

This compelling visual graphic should underscore the impact that larger sample sizes have on our statistical conclusions. When we deal with truly big data, confidence intervals become less important since they narrow substantially due to the dramatic increases in big data sample sizes. In big data models, the priorities in the analysis shift from interval plots to establishing the relative importance rank for the predictors relative to the target variable.

  

3.2.9.3 Box Plot

  

This widget is a valuable tool for visualizing numeric data for an individual data set or comparing data values between subgroups. Box plots numerically label a dataset’s mean, median, standard deviation, first quartile, third quartile, min, and max values for a dataset. A box plot can also be used to identify outliers. Orange does not offer the ability to plot multiple numerical variables in the same display, so we can only do a box plot for one variable at a time. In Figure 3.42, serum cholesterol values are compared by gender. Be sure to check “Order by relevance to subgroups” to order variables by chi-square or ANOVA over selected sub-groups. Also, select “Order by relevance to variable” to order sub-groups by chi-square or ANOVA over selected variables. Select “Annotate” to show calculated values on the box plot. You can also select “Compare means” or “Compare medians.” Remember that the data is skewed if the mean and median are quite different. Figure 3.42 will display the mean plus standard deviations and the interquartile range (Q3-Q1)(75%-25%) or IQR. The IQR represents the middle 50% of all data values. Figure 3.42 shows the t-test result (p-value = 0.003), which shows a statistically significant difference between the two means since the p-value is < 0.05. We can therefore conclude with 95% confidence that females in this dataset have statistically significantly higher total cholesterol than males.

Orange has mini dotted-line whiskers that define the full range of the data values. The end of the whiskers designates the minimum and maximum extreme values. If we examine the cholesterol levels in males, the shaded rectangle represents the first to the third quartile (Q3-Q1 or IQR). Orange does not identify outliers in its box plots, but JASP does.

One definition of outliers is that they represent 1.5 x the IQR, as shown in Figure 3.43. For males, the IQR = 268-209.5 or 59.5. 1.5 x 59.5 = 89.25. Add that to 268; an upper outlier would be considered above 357.25. Subtract 89.25 from 209.5; any lower outliers would be any result below 120.25. As we can see, there are no outliers for males since the official outliers would happen to start just above the actual max value for cholesterol and below the actual min values for cholesterol. However, we can see that there will be outliers for females on the high end of the scale but none on the low end based on an estimation of where the 1.5 x IQR limits would be placed on the graph.

  
![](images/image-SDZ039SN.jpg)  

Figure 3.42 Boxplot of cholesterol levels by gender in Orange

  

  

KEYPOINT: The above rule to define outliers does not apply to data that is not normally distributed, such as the cholesterol in women displayed in Figure 3.42 ¹⁴

  

  

Orange has a unique feature included in the box plot widget. You can also plot categorical values and, using chi-square statistics, determine if the differences are statistically significant using chi-square statistics. For example, select thallium in the Variable box and diameter narrowing in the Subgroup box, and it will compare those with and without heart disease. According to Figure 3.44, about 65% of patients with heart disease have a reversible defect, but about 25% have a normal thallium test. Chi-square determines if the actual proportions are different from what is expected. Note: you can click on/highlight, e.g., the reversible defect bar for no heart disease patients, and send those patients to a data table for further analysis.

Use the box plot to determine the number of patients in each class. For example, using this same dataset, select diameter narrowing in the top and bottom windows. This will reveal that there are 164 subjects without heart disease and 139 with heart disease and this is statistically significant.

JASP offers a similar box plot, but you can color code the box plots and identify the outlier patients by listing their row numbers next to each outlier (dot). Figure 3.45 displays blood pressure in males and females. Those above the upper whisker are outliers. For example, for males (0) patients 18, 59, 11. 166 and 160 are outliers.

  
![](images/image-ABH1FILK.png)  

Box Plot (StatQuest)

  
![](images/image-OJ1S2CL0.png)  

Figure 3.43 Cholesterol outlier definitions for males

  
![](images/image-NWLPH1EP.png)  

Figure 3.44 Boxplot of thallium testing and heart disease

  
![](images/image-9M5XNZHI.png)  

Figure 3.45 JASP box plot of blood pressure in males (0) and females (1)

  

3.2.9.4 Nomogram

  

Nomograms, also called nomographs, can be created as interactive graphics in Orange to visually display the results of Naïve Bayes and logistic regression classifiers. The interaction offers the opportunity to move buttons on the nomogram to a desired location to test its impact on the outcome. In addition to being a great visualization tool, the nomogram offers predictions for the class probabilities for categorical targets. Figure 3.46 shows the Orange workflow required to create a nomogram.

  
![](images/image-YU0EMWOD.png)  

Figure 3.46 Orange workflow to create a nomogram

  

[Figure 3.47 displays the result of finding the combination of features that can explain the best survival probabilities on the Titanic. For example, female children from the first class had a 96% chance of survival. The Nomogram widget offers powerful options for the scale, target class, and display options that can focus on the best-ranked predictors when too many are present.](#content0089.xhtml)

  
![](images/image-XREQJLIM.jpg)  

Figure 3.47 Orange nomogram to show the best survival options on the Titanic

  
![](images/image-EH5YOQ79.jpg)  

Figure 3.48 Orange nomogram to show the worst survival options on the Titanic

  

[Figure 3.48 shows the result of finding the combinations of features that can explain the worst survival probabilities. For example, adult male crew members only had a 15% chance of survival.](#content0089.xhtml)

  

#### 3.2.10 Text Displays

  

Word clouds are graphic representations of text data that show a weighted list of the terms that appear frequently in a given text. A word will appear in the word cloud larger and bolder the more times it occurs in the text. Word clouds can help readers quickly understand the most important elements of a work and pinpoint important themes, characters, or phrases.

  

3.2.10.1 Word Cloud

  

Let us create a word cloud for the Declaration of Independence from 1776.¹⁵ Pasting that text in MS Word will not be recognized by Orange, but if you paste it into Excel, it can be found by Orange. Many options in the Preprocess Text widget can reduce the word cloud’s size, such as adding a file with stopwords that the word cloud should ignore. Figure 3.49 displays the Orange workflow, and Figure 3.50 displays the outputted word cloud.

  
![](images/image-XJXQ4R30.jpg)  

Figure 3.49 Orange workflow to create a word cloud

  
![](images/image-UTGA73VX.png)  

Figure 3.50 Orange default word cloud

  

3.3 VARIABLE RANKS - NON-REGULARIZED VERSUS REGULARIZED

  

  

Variable ranks are used in statistics and machine learning to show the ranked contribution of all predictors relative to their predictive power to explain a classification or regression target. The terms “Non-Regularized” and “Regularized” refers to two different modeling methods that are used to determine the ranks of predictors.

Non-Regularized models and methods use all of the predictors in a model to determine their rank no matter the predictors’ true significance, contribution, or VIF values of the predictors. This method can lead to overfitting since this method includes the true signals in the data mixed with a lot of the noise and multicollinearity that should be addressed to determine the true rank of all significant predictors. This may create high-performing models in statistics and in training models that focus on modeling the signal and the noise in the chosen predictors. The Logistic regression and the Linear regression widgets in Orange offer a “no regularization” option. You may have several good reasons to mistrust very optimistic modeling if no regularization is chosen. The Orange Rank widget offers seven scoring methods, but beware, only the last method in the list (FCBF – Fast Correlation Based Filter) makes any attempt to filter out predictors due to high correlations between predictors.

Regularized models and methods offer various options and settings that prevent overfitting, overly optimistic results, and inaccurate predictor ranks. Regularized methods in Orange apply two forms of regularization: L1 (Lasso), L2 (Ridge) for logistic regression, and an additional method called Elastic Net for linear regression, a mix of the L1 and L2 methods. The L1 Lasso method is considered a very strict method that can reset the regression coefficients to zero when it identifies multicollinearity or a mediocre rank. This does not remove the predictor from the model, but it prevents it from impacting the model result and rank. The L2 Ridge method does not act as strictly as the L1 method since it shrinks coefficients towards zero without resetting them to zero. The elastic Net method is a mix of the very strict L1 method and the lesser strict L2 methods. All of these regularization methods can lead to simpler models that tend to generalize better on unseen data.

[Figure 3.51 shows the Orange workflow to add regularization for classification models.](#content0093.xhtml)

[Figure 3.52 shows the rank results for the main scoring method in the Rank widget compared to the Lasso method for the ten-year Framingham Kaggle heart disease dataset. The Lasso ranks are shown on the right compared to the Rank widget Information Gain method on the left. As we can see, the Lasso method “demoted” 13 of the 18 predictors to a zero coefficient, allowing this ranking model to focus on the truly significant predictors by eliminating noise and highly correlated predictors. The Information Gain method allowed 14 of the 18 predictors to be still included in the model despite high VIFs and other issues with those predictors.](#content0093.xhtml)

  

3.4 DASHBOARDS AND INFOGRAPHICS

  

  

Dashboards and infographics are both data visualization tools that help present complex information in a simplified and easy-to-understand format.

  

#### 3.4.1 Dashboards

  

In Chapter 1, data science soft skills were mentioned as an important aspect of what data scientists bring to the table. Creating simple yet highly informative dashboards tells your data project’s story from start to finish. Properly designed, they should be visually appealing and tell a logical story without screen clutter. Dashboards can be static or dynamic, which means they are connected to a live data feed, so data trends are constantly updated.

  
![](images/image-FBI0O98E.jpg)  

Figure 3.51 Orange logistic regression (Lasso) with regularization options

  
![](images/image-0HBU9FVT.jpg)  

Figure 3.52 Two outputs for the Rank widget - non-regularized and regularized

  
![](images/image-P3X4GXIN.png)  

Figure 3.53 A patient-oriented healthcare dashboard ¹⁷

  

Storyboards are similar to dashboards but are interactive so that the viewer can change the output with filters, etc.¹⁶ Figure 3.53 shows a dashboard example of sales by each representative. Figure 3.54 shows a dashboard representing HR Workforce status.

  
![](images/image-13E2CGGW.png)  

Figure 3.54 A Workforce dashboard ¹⁷

  

3.4.1.1 Rules of Thumb For Creating Storyboards and Dashboards

  

The following are general rules to create storyboards and dashboards:

1\. Plan before designing: consider what components you want to include ahead of time. Be sure you truly understand the data elements before attempting to post visualizations. What is your purpose, goal, and strategy to create compelling visualizations?

2\. What are your key performance indicators? Here is a list of 19 healthcare KPIs that can inspire many data science projects. ¹⁸

3\. Decide which visualization strategy to use:

a. Relationship: the connection between two or more variables

b. Comparison: compare two or more variables side by side

c. Composition: breaking data into separate components

d. Distribution: range and grouping of values within data

4\. Provide context: what do low or high levels mean? Compared to what? Does the end user understand the metric?

5\. KISS (keep it simple stupid) principle: starting with a small sketch on paper is reasonable before posting tables or plots

6\. Avoid clutter and attempting to post too much

7\. Consider the 5-second rule; see if the end user can understand the data within 5 seconds

8\. Know your audience: who constitutes the people who will view and scrutinize the clarity of the dashboard? Consumers? CEO? Both? Will they understand the plots?

9\. Go from macro to micro: the most important concepts should be listed first and in the largest font. It is like an inverted pyramid.

10\. Design left to right for readers of the English language

11\. Round numbers, for simplicity’s sake

12\. Limit the number of Key Performance Indicators (KPIs): avoid the temptation to post every finding on the dashboard. Focus on the major points (3-5)

13\. Consider interactive elements: so the end-user can drill down further

14\. Limit the scope of what the filters affect: be sure they do not affect an entire page

15\. Use vertical scrolling: do not scroll horizontally

16\. Optimize for web and mobile platforms

17\. Design consistency is important: be consistent with font type, size, and color

18\. Details are important: for example, use icons set at their original dimensions ¹⁹ - ²³

  

#### 3.4.2 Infographics

  

An infographic is like a dashboard but usually focuses on a specific topic and includes text and visualizations. One definition is “a collection of imagery, data visualizations like pie charts and bar graphs, and minimal text that gives an easy-to-understand overview of a topic.” ²⁴ They are often educational, easy to view, and have visually appealing images. Infographics are usually static and not interactive. They are good choices for patient education about topics of interest, such as COVID-19, special diets, and disease states. Figure 3.55 displays an infographic that focuses on COVID-19 protection.²⁵

Infographics are versatile tools that can be used in many different industries to communicate complex information in a simplified and engaging way. Infographics can be applied to marketing, consulting presentations, brand style guides for small businesses, nonprofits, education, and in many other areas.

  

3.4.2.1 Creating a Disease Infographic

  

Infographics can be created from “scratch” using any document platform, such as Microsoft Word, Google Docs, or Adobe PDF and can also be created from templates, which saves time. There are a variety of commercial platforms that offer free infographics templates, such as Canva, Venngage, etc.²⁶-²⁷ Figure 3.56 displays a generic diabetes awareness infographic.²⁸ This can be customized to fit local needs.

  
![](images/image-PFRBIU44.png)  

Figure 3.55 A generic COVID-19 awareness infographic

  

3.5 PUTTING KNOWLEDGE INTO PRACTICE

  

  

#### 3.5.1 Exercise

  

Visualizing the data along with providing descriptive statistics are important components of exploratory data analysis. We will be analyzing adult income data hosted on the UCI Data Repository. ²⁹ There is a copy in our file-share site in the Chapter 3 folder.

1\. Start by going to the UCI website to be sure you understand each variable. Note: fnlwgt: is the final weight or the number of people the census believes the entry represents.

2\. Upload the data to the File widget and note whether there is any missing data. Also note the number of rows and columns and note how many categorical and numerical variables exist. Change Income to target.

  
![](images/image-XC0LPBG3.png)  

Figure 3.56 A generic diabetes awareness infographic

  

3\. Connect a Data Tabl e widget to the File widget to examine the data in detail

4\. Connect the Feature Statistics widget to the File widget and open it

a. At the bottom is the option to color code the data. Select Income

b. Begin looking at the variables as they relate to income < or > $50K. Early observations? Were there fewer people with an income of > $50K? Keep in mind that this is 1994 data.

c. Keep income in the lower window but start looking at all variables in the upper window

5\. Connect a Box Plot , Distributions , and Scatter Plot widget to the File widget

6\. In the Box Plot widget start the process of determining which relationships are statistically significant

a. Choose income for the upper and lower windows which will give you an actual count plus p-value.

b. Keep income in the lower window but analyze each variable by income as the subgroups. For example, is the mean age statistically different between the two income categories? What about gender and income? List all subgroups that are statistically different.

c. You can choose other subgroups in the lower window. Select income in the upper window and education in the lower window. What did you find? What type of degree had the highest percentage of income over $50K?

7\. Open the Distributions widget and look at the distributions of all variables

a. Were high school graduates more common than college graduates?

b. What marital status had the highest percentage of income over $50K?

c. Was income higher for those who worked more than 40 hours per week?

8\. Open the Scatter Plot widget and compare pairs of data

a. Select “Find Informative Projections.” This will take a few minutes.

b. You use a projection found by the widget or try educational-num in the x axis and hours-per-week in the y axis. Color = income. Note: the plot will look a little different compared to other scatter plots because both variables are in whole numbers

  

#### 3.5.2 Maturity Levels

  

TownCare Clinic - Low Analysis Maturity Level

  

•Data: Patient demographics.

•Objective: Basic EDA with Orange and JASP.

•Activities:

  

![](images/image-TEMD15Y1.jpg)Visualization: Univariate and bivariate tools.

  

![](images/image-TEMD15Y1.jpg)Analysis: T-Tests, Chi-Squared tests for categories.

•End Product: Singular infographic.

  

CityMed Hospital - Moderate Analysis Maturity Level

  

•Data: Readmission patterns post-discharge.

•Objective: Detailed EDA with Orange and JASP.

•Activities:

  

![](images/image-TEMD15Y1.jpg)Visualization: Expanded to multivariate tools.

  

![](images/image-TEMD15Y1.jpg)Analysis: Enhanced statistical tools.

•End Product: Interactive readmission risk dashboard.

  

GlobalHealth Research - High Analysis Maturity Level

  

•Data: Electronic health records for Type 2 Diabetes risk.

•Objective: Deep EDA with Orange and JASP.

•Activities:

  

![](images/image-TEMD15Y1.jpg)Visualization: Histograms, scatter plots, 3D interactions.

  

![](images/image-TEMD15Y1.jpg)Analysis: Factor, regression, cluster analysis.

•End Product: Infographics, doctor’s dashboard, public health dashboard.

•Outcomes: Identified 45-60 age bracket and BMI>30 as high-risk. Noted seasonal glucose fluctuations.

GlobalHealth Research’s deep dive provides actionable insights, furthering the cause of both clinical and public health initiatives.

  

#### RESOURCES

  

  

1\. 10 useful ways to visualize data

[https://bigdata-madesimple.com/10-useful-ways-to-visualize-your-datawith- examples/](https://bigdata-madesimple.com/10-useful-ways-to-visualize-your-datawith-examples/)

2\. Best data visualization techniques for small and large data https://www.kdnuggets.com/2019/04/best-data-visualization-techniques.html

3\. The Data Visualization Catalog. https://datavizcatalogue.com/#google\_vignette

4\. Knaflic, Cole Nussbaumer. 2015. Storytelling with Data: A Data Visualization Guide for Business Professionals . John Wiley & Sons.

5\. Evergreen, Stephanie D. H. 2019. Effective Data Visualization: The Right Chart for the Right Data . SAGE Publications.

  

#### REFERENCES

  

  

[1\. jamovi - Stats. \[Internet\]. \[cited 2020 Oct 27\]. Available from: https://www.jamovi.org/](#content0079.xhtml)

[2\. A Fresh Way to Do Statistics \[Internet\]. JASP - Free and User-Friendly Statistical Software. 2021 \[cited 2022 Mar 26\]. Available from: https://jasp-stats.org/](#content0079.xhtml)

[3\. Hoyt R, Muenchen R. Introduction to Biomedical Data Science \[Internet\]. Lulu.com; 2019. 258 p. Available from: https://books.google.com/books/about/Introduction\_to\_Biomedical\_Data\_Science.html?hl=&id=4H3CDwAAQBAJ](#content0079.xhtml)

[4\. BlueSky Statistics. Available from: \[ https://www.blueskystatistics.com/](#content0079.xhtml)

[5\. UCI machine learning repository \[Internet\]. \[cited 2023 Aug 16\]. Available from: https://archive.ics.uci.edu/dataset/2/adult](#content0081.xhtml)

[6\. UCI machine learning repository \[Internet\]. \[cited 2023 Aug 16\]. Available from: https://archive.ics.uci.edu/dataset/186/wine+quality](#content0083.xhtml)

[7\. Mishra P, Pandey CM, Singh U, Gupta A, Sahu C, Keshri A. Descriptive statistics and normality tests for statistical data. Ann Card Anaesth. 2019 Jan-Mar;22(1):67–72.](#content0083.xhtml)

[8\. Varshney, Paras. 2020. “Q-Q Plots Explained.” Towards Data Science. April 15, 2020. https://towardsdatascience.com/q-q-plots-explained-5aa8495426c0](#content0083.xhtml)

[9\. Lee I. Towards Data Science. 2021 \[cited 2023 Aug 16\]. 4 Reasons why Correlation does NOT imply Causation. Available from: https://towardsdatascience.com/4-reasons-why-correlation-does-not-imply-causation-f202f69fe979](#content0084.xhtml)

[10\. Chen J, Chun D, Patel M, Chiang E, James J. The validity of synthetic clinical data: a validation study of a leading synthetic data generator (Synthea) using clinical quality measures. BMC Med Inform Decis Mak. 2019 Mar 14;19(1):44.](#content0086.xhtml)

[11\. Siddhartha M. Heart disease dataset (comprehensive) \[Internet\]. 2019 \[cited 2023 Aug 16\]. Available from: https://www.kaggle.com/datasets/sid321axn/heart-statlog-cleveland-hungary-final](#content0087.xhtml)

[12\. Elgiriyewithana N. Global Country Information Dataset 2023 \[Internet\]. 2023 \[cited 2023 Aug 13\]. Available from: https://www.kaggle.com/datasets/nelgiriyewithana/countries-of-the-world-2023](#content0088.xhtml)

[13\. Confidence Intervals. Statology. Available from: https://www.statology.org/confidence-interval-mean/](#content0089.xhtml)

[14\. Naghshin V. Use adjusted boxplot for skewed distribution \[Internet\]. Artificial Intelligence in Plain English. 2020 \[cited 2023 Feb 15\]. Available from: https://ai.plainenglish.io/use-adjusted-boxplot-for-skewed-distribution-d1bc0ec25f6d](#content0089.xhtml)

[15\. Declaration of Independence: A transcription \[Internet\]. National Archives. 2015 \[cited 2023 May 16\]. Available from: https://www.archives.gov/founding-docs/declaration-transcript](#content0090.xhtml)

[16\. Brown A. Brainteaser: Storyboard or dashboard...Self-service or managed...You choose \[Internet\]. Amick Brown. 2016 \[cited 2022 Dec 31\]. Available from: https://amickbrown.com/brainteaser-storyboard-or-dashboard-self-service-or-managed-you-choose/](#content0093.xhtml)

[17\. DataPine https://public.datapine.com/?\_ga=2.3912816.1519211400.1672249163-1016098063.1672158689#board/BOHpnqXGIyWpHgn20N0DTi](#content0093.xhtml)

[18\. Deciding on KPIs for healthcare. Datapine.com https://www.datapine.com/kpi-examples-and-templates/healthcare](#content0093.xhtml)

[19\. Sifri A. 10 dashboard design thumb rules - tint studio - medium \[Internet\]. Tint Studio. 2019 \[cited 2022 Dec 27\]. Available from: https://medium.com/tint-studio/10-dashboard-design-thumb-rules-b1ac2be40bdc](#content0093.xhtml)

[20\. Dashboard design best practices - 4 key principles \[Internet\]. Sisense. 2019 \[cited 2022 Dec 27\]. Available from: https://www.sisense.com/blog/4-design-principles-creating-better-dashboards/](#content0093.xhtml)

[21\. Calzon B. Top 23 dashboard design principles, best practices & how to’s \[Internet\]. BI Blog | Data Visualization & Analytics Blog | datapine. 2021 \[cited 2022 Dec 27\]. Available from: https://www.datapine.com/blog/dashboard-design-principles-and-best-practices/](#content0093.xhtml)

[22\. KPI Examples. Datapine. Available from: https://www.datapine.com/kpi-examples-and-templates/healthcare](#content0093.xhtml)

[23\. Tennyson L. How to create a dashboard in Google Sheets \[Internet\]. Sheetgo Blog. 2019 \[cited 2022 Dec 29\]. Available from: https://blog.sheetgo.com/spreadsheets-tips/how-to-create-a-dashboard-in-google-sheets/](#content0093.xhtml)

[24\. Nediger M. What is an Infographic? Examples, Templates, Design Tips \[Internet\]. Venngage. 2022 \[cited 2022 Dec 31\]. Available from: https://venngage.com/blog/what-is-an-infographic/](#content0094.xhtml)

[25\. PAHO Situation Reports https://www.paho.org/en/covid-19-situation-reports](#content0094.xhtml)

[26\. Canva. https://www.canva.com](#content0094.xhtml)

[27\. Vengage. https://vengage.com](#content0094.xhtml)

[28\. World Health Organization https://apps.who.int/mediacentre/infographic/diabetes/en/index.html](#content0094.xhtml)

[29\. UCI Data Repository http://archive.ics.uci.edu/dataset/2/adult](#content0096.xhtml)

  

![](images/image-Y4GBCBQU.jpg)Chapter 4

  

## Machine Learning Models

  

“It is a capital mistake to theorize before one has data.”

—Sherlock Holmes, “A Study in Scarlett”

Arthur Conan Doyle

“It’s tough to make predictions, especially about the future”

—Yogi Berra

  
![](images/image-M6MTZISG.jpg)  
  

LEARNING OBJECTIVES

  
  

By the end of chapter four, readers should be able to:

•Describe how modeling and algorithms are separate concepts.

•Discuss how the machine learning pipeline works.

•Compare and contrast bias and variance.

•List 5 classification and 5 regression algorithms.

•Discuss 3 challenges all models face.

  
  

Chapter 4 Summary

  

  

In this chapter we will review the step by step modeling process workflow that eventually leads to model deployment, which is referred to as the machine learning pipeline. The primary Orange algorithms used to create classification and regression models will be discussed. In addition, under and overfitting, imbalanced data, synthetics data, bias and variance, and hyperparameter optimization will be discussed. Emphasis will be on understanding the modeling process, how it fits into the machine learning pipeline, and its significant challenges.

  

Key Principles:

•In this textbook we treat the terms model and algorithm differently. The model is the larger concept, such as a classification model, whereas an algorithm is the specific method it uses, such as logistic regression.

•Successful and effective models demand business relevance, domain-specific accuracy, and technological feasibility.

•Machine learning is different from programming in that traditional programming sets rules; machine learning learns rules from data.

•The ideal model aims to avoid overfitting (too specific) and underfitting (too general).

•Models are easy to create but ensuring their real-world success isn’t.

  

  

4.1 INTRODUCTION

  

  

Before we focus on modeling with a smorgasbord of algorithms, let’s first explore the modeling process.

  

  

KEYPOINT: Even though many authors use models and algorithms synonymously, we consider them different. To use a culinary analogy, a model is a final and presumably best recipe used for baking a chocolate cake. Algorithms and algorithm options are the many recipes competing to get the best customer-tasting scores for the chocolate cake. Stated another way, we will create classification and regression models with many different algorithms to discover which algorithm offers the best predictive performance with unseen (test) data.

  

  

Seasoned data analysts work on a machine learning process model, as illustrated in Figure 4.1. The model is often shown as linear, but in reality, the modeling process is more similar to a non-linear and sometimes circular process in pursuit of the best possible predictive model. As more insights are gained and possible disappointments in model performance are observed, certain previous steps in the model may be revisited, and additional data may also be sought to improve model training. New features may also need to be engineered as part of this continual model improvement process. Unexpected insights may also change the scope or level of stratification required in the model. Such surprises and challenges may require curricular activities in the DISCOVER process to support continuous model improvements and fine-tuning. Iterative model improvements are at the heart of the DISCOVER process, and flexibility should be applied as the data provides new revelations. It bears repeating that three-quarters of the time a data scientist spends on a project is spent in this area before a model is created or run (Steps 1 to 4).

In this section, we now apply step #5 of the DISCOVER Process to Optimize the Model performance with experiments and model tuning, as shown in Figure 4.2.

  
![](images/image-MATGSF28.png)  

Figure 4.1 The 8-step data science DISCOVER process with its linear and non-linear activities

  
![](images/image-R81J42EA.png)  

Figure 4.2 Step 5 in the DISCOVER Process

  

Listed below are the key model optimization techniques that should be explored to improve model performances in Step 5 of the DISCOVER process:

1\. Select and test a diverse range of algorithms, algorithms options, and levels of regularization during the initial model screening.

2\. Pursue additional fine-tuning and adjustments based on the results of the initial model screening.

3\. Apply hyperparameter optimization techniques with random search and grid search methods

4\. Experiment with threshold shifting to values other than the default setting of 0.5 based on the specific targets for the problem to reduce false positives and false negatives

5\. Explore the usefulness of the Orange Calibrated Learner widget

6\. Experiment with the Orange Stacking widget which is an ensemble method that computes a meta model from several base models.

7\. Engage subject matter experts to provide enhanced scrutiny of the current features and assumptions made in the model.

8\. Consider adding model interaction terms to the model but do not increase multicollinearity, as measured by the Variance Inflation factor (VIF).

9\. Consider adding polynomial and spline features to the model but be careful that this does not lead to model overfitting.

10\. Consider other data science experiments that may further improve model performance.

11\. Revisit and scrutinize all past data collection, preprocessing, model-building assumptions, and decision-making processes as you seek new ways to improve your model performance.

12\. Seek new innovations for every step in your analysis process.

13\. Identify and address model bias and fairness issues.

14\. Identify and address class and feature imbalance issues affecting model performance. Explore SMOTE, oversampling, undersampling, and weighing options available for Random Forest and Logistic Regression in Orange to address class imbalance issues.

15\. Experiment with the addition of synthetic data when you have small datasets but ensure that the addition of such data actually improves the model performance.

16\. Never assume that the addition of a popular technique will always improve the performance of your model. Verify the potential improvements of new techniques for yourself with the help of data science experiments.

17\. Experiment with unique Orange workflow setups and automated BlueSky Statistics methods to explore hyperparameter optimization (HPO).

18\. Apply various methods to reduce overfitting with cross-validation, regularization, selecting smaller sets of features during modeling, early stopping, and training with more data.

Data is the vital fuel powering algorithms to create accurate predictions and stands central in the predictive analytics step of the data science process (See Figure 4.1). For a successful analysis, it’s crucial to involve clinical and subject matter experts early on to identify the right data for predicting specific outcomes. Every industry needs to define the key experts, marketers, suppliers, and customers who should be part of the data science project. These subject matter and clinical experts should also assess the data’s completeness, relevance, and accuracy. If their insights come too late in the DISCOVER process, it may lead to additional circular tasks and delays in creating effective models that everyone can trust.

Collecting comprehensive data that encompasses all potential predictors is essential for robust predictive models. Lack of such data can result in futile attempts to enhance model performance. However, while having too many data columns can lead to the “curse of dimensionality,” the “curse of superficiality” arises from insufficient valid predictors or data rows, potentially rendering the analysis ineffective.

Balancing sufficient data with avoiding data pitfalls is critical during the modeling process. Ensuring data is high-quality, comprehensive, and well-structured paves the way for meaningful insights.

  

  

KEYPOINT: Adding more low-quality data (rows) cannot replace the need for more meaningful predictors (columns) in a dataset. While a larger dataset can sometimes help improve the accuracy and generalizability of a model, this benefit is limited if the data is of low quality or does not contain relevant predictors. By prioritizing quality over quantity, we can generate more meaningful insights and improve the performance of predictive models.

  

  

As a reminder, in step 3 of the DISCOVER process, we conducted data cleaning, processing, and feature engineering activities. Once the seasoned data analyst feels that the data is clean, properly formatted, and extensively verified, the data exploration and data visualization phase can start with its efforts to cultivate initial insights with EDA (Step 4). After that phase, algorithms will now compete to determine which algorithm can be used as part of an optimized model (Step 5). The best algorithms may need tweaking (called hyperparameter optimization or HPO) to optimize their performance. Simple HPO was defined in chapter two and will be pointed out in this chapter too, but it is beyond the scope of this book to delve deeply into HPO.

Models can also be joined in ensemble teams to test if a group of algorithms (ensembles) works better than individual algorithms.

  

  

KEYPOINT: A high-performing predictive model can significantly add value to mission-critical decision-making processes. By enabling decision-makers to make more informed choices, such models can improve efficiency, save time, resources, and reduce costs while maintaining a patient- and customer-focused priority.

  

  

#### 4.1.1 How Do Models Work?

  

For data mining, there are feature vectors as inputs and outputs. Feature vectors represent various model inputs (predictors) to predict an outcome for a particular research problem. A machine learning algorithm processes these feature vectors to create a prediction model. For example, in Figure 4.2, we have five patients (rows), and each has six predictors (age, gender, smoking, etc.) to predict the outcome (cancer = 1, benign = 0).¹

  

  

KEYPOINT: Machine learning involves using data to create a model that learns from the data by identifying patterns and relationships between input predictors and an output target to make predictions about future data.

  

  

The supervised learning approach to machine learning differs from classic statistics since we test many candidate functions (called g) that will provide their best explanation using X1 to Xn. In supervised machine learning we are trying to solve this equation Y = g(X1….Xn) + E. The g function is described as the best algorithm out of many algorithms.

In classic statistical problem solving or research, the goal is typically to solve a problem in the form: Y = f(X1…Xn) + E, where Y is the outcome being predicted, f is a statistical method such as linear or logistic regression, X1 to Xn are predictor variables, and E is the error or model residual.

In contrast, the supervised learning approach to machine learning involves testing many candidate functions, g, to determine the best explanation of Y using X1 to Xn. Therefore, the goal is to solve the equation Y = g(X1…Xn) + E, where g is the best algorithm chosen from many possible algorithms and E is the difference between the predicted value and the real value.

Model errors are also called residuals. Predictive model residual plots may be some of a model’s most informative report card graphics. Figure 4.3 shows a predicted versus actual data scatter plot that compares the actual data compared to the predicted values for a regression problem, predicting the percent body fat for a patient. The 45-degree diagonal line represents a perfect predictive model where the observed and predicted values are the same. If you encounter such optimistic results, beware, they are probably too good to be true. The dots in the scatterplot represent the coordinates for all the observed values on the x-axis and the predicted values on the y-axis. When a data point on the graph is in the upper left area, the predicted data is higher than the actual observed data. When a data point on the graph is in the lower right area, the predicted data is lower than the actual observed data. Any model residual scatter plot with actual data points (dots) not exactly on the diagonal line represents a less-than-perfect model. If the dots do not follow the 45-degree diagonal line very well, it needs to be investigated. This would be a case where we go backwards in the process, recheck all of our assumptions, self-critique any shortcuts that were made, and plan new data science experiments that may create an improved predictive model.

To create this visualization in Orange, connect the File widget with the body fat dataset uploaded to the Prediction widget. Connect the Linear Regression widget to the File and Prediction widget. Connect the Prediction widget to the Scatter Plot widget and select Linear Regression for the y axis and Class for the x axis.

  
![](images/image-KIMW6OQV.png)  

Figure 4.2 Typical model with multiple feature vectors and an output variable for each vector

  

To create this visualization in JASP, upload the data and select Regression in the top menu. Next select linear regression and move the outcome variable to the dependent variable box and the predictors to the covariates box. Scroll down to Plots and select “Residuals vs Predicted.”

  
![](images/image-GCOEXIJ2.jpg)  

Figure 4.3 The Actual versus predicted data scatter plot

  

[Figure 4.4 shows a different variation of the actual versus predicted data plot in a histogram where the vertical zero residual line represents an exact match between the predicted and actual value. Actual observed data is lower than the predicted data when the residuals are negative or to the left of the zero residual line on the histogram. Actual observed data is higher than the predicted data when the residuals are positive or to the right of the zero residual line on the histogram. The perfect predicted versus actual data histogram plot would look like a narrow and symmetric histogram representing a close correlation between predicted and actual data values.](#content0102.xhtml)

In essence, supervised machine learning involves identifying the function g that best maps the input variables X1 to Xn to the output variable Y. This is done by training the model on a labeled dataset, where the input variables and corresponding output variables are known. The model then uses this training data to learn the best g function (algorithm) to predict the output variable for new, unseen input variables. The success of the supervised machine learning approach depends on the quality and relevance of the input variables and the choice of the best algorithm to learn the function g.²

  
![](images/image-AAF7KQZ4.jpg)  

Figure 4.4 The Predicted versus Actual Data residuals histogram plot

  

Creating an initial model is easy. However, the model needs to be evaluated and optimized if it does not meet the predictive modeling performance goals. Finding appropriate data and preparing it for analysis can also be arduous. If the data collection and preparation tasks are taken seriously, it will positively affect model performance. We will discuss model challenges in section 4.7.

  

4.2 MORE MODELING CONCEPTS

  

  

A major goal of machine learning is reducing errors between the model’s predictions and the actual outcome. Some errors are not preventable, but some are reducible, such as bias and variance, which are not preventable and are reducible. ³

  

#### 4.2.1 Bias-Variance Tradeoff

  

The bias-variance tradeoff helps to explain prediction errors in supervised learning models and is related to under and overfitting. Increasing bias will decrease variance and vice versa.

Bias in machine learning refers to the difference or error between the predicted values generated by the model and the actual or correct values. It is a systematic error that occurs due to incorrect assumptions or oversimplification in the machine learning process. A model with high bias tends to oversimplify the relationships in the data and may fail to capture complex patterns or trends. This can lead to underfitting, where the model performs poorly on both the training data and unseen data.

Variance refers to the model’s tendency to overfit the data. A model with a high variance is excessively complex and gives the training set’s noise and fluctuations too much consideration. This can lead to overfitting, where the model fits the training data too closely and fails to generalize well to new, unseen data. In other words, a model with high variance performs well on the training data but has a high error rate on test or validation data.

This is demonstrated in Figure 4.4.

Several types of bias are encountered in machine learning models . Here are a few examples:

•Simplicity Bias : This is when simpler models are often preferred over complex models even at the expense of not capturing the underlying patterns or relationships, which can lead to underfitting and poor performance.

•Sample bias is when the data used to train the model is not representative of the population it is supposed to be applied to.

•Label bias is when the labels to train the model are inaccurate or incomplete.

•Racial bias AI might have for light skinned vs dark skinned individuals.

•Methodological bias of a poorly designed study that leads to poor generalizability (garbage in - garbage out).

•Confirmation Bias : This occurs when the model is designed to confirm pre-existing biases.

•Algorithmic Bias : This occurs when the algorithm itself is designed to discriminate against certain groups.

•Fairness Bias : This occurs when the model is designed to optimize for fairness, but the definition of fairness is subjective or incomplete.

Here are some examples of variance (overfitting) in healthcare ML models:

•Image Classification: Machine learning models are often used to classify medical images such as X-rays or MRIs. If the model is trained on a limited dataset that does not represent the diversity of images it will encounter in the real world, it may become overfit to that limited dataset and struggle to generalize to new images.

•Disease Prediction: Machine learning models are also used to predict the risk of developing certain diseases based on patient data such as demographics, medical history, and lifestyle factors. If the model is trained on a small or unrepresentative sample, it may become overfit to a small group and make inaccurate predictions for new patients.

•Treatment Recommendation: In healthcare, machine learning models can recommend treatment plans for patients based on their medical history and other factors. If the model is overfitted to a specific subset of patients, it may have high variance and recommend ineffective or harmful treatments for new patients.

•Drug Discovery: Machine learning models can be used to discover new drugs by analyzing large datasets of chemical compounds and their properties. If the model is overfitted to a specific subset of compounds, it may fail to identify promising new compounds for further study.

•Electronic health records: Machine learning models are increasingly used to analyze electronic health records (EHRs) to identify patterns and trends in patient data. If the model is overfitted to a specific set of patients or hospitals, it may have high variance and fail to identify important insights for new patients or hospitals.

  

  

KEYPOINT: The ideal model attempts to minimize bias (underfitting) and variance (overfitting), by striking a balance between bias and variance for the training and test datasets.. Overfitting occurs when there is high variance and low bias. In the overfitting situation, the model tries to fit both the signal and the noise. The opposite is true for underfitting. ⁴ When training a machine learning model, the algorithm typically iterates through different parameter settings to minimize the difference between the model’s predictions and the actual target values in the training data.

  

  

These bias and variance concepts are further illustrated in Figures 4.5 and 4.6.

  
![](images/image-H55ITMJ1.jpg)  

Figure 4.5 Bias-variance tradeoff (courtesy Scott Fortmann-Roe)

  
![](images/image-1SPS87JX.jpg)  

Figure 4.6 Over and underfitting

  

Another plot that helps explain the bias-variance tradeoff is seen in Figure 4.7 that plots model error against model complexity. The compromise is to have a low error rate and moderate model complexity so that bias and variance are optimized.⁵

  
![](images/image-A58IXP8H.png)  

Bias and Variance (StatQuest)

  

#### 4.2.2 Model Interpretability and Explainability

  

Models that are difficult to understand are commonly referred to as “black boxes,” which do not always help to build trust. Easily understood models are referred to as “glass boxes” because they are transparent. Definitions:

•Interpretability in machine learning refers to the ability to understand and explain how a machine learning model makes its predictions or decisions.

•Model explainability refers to the ability of a machine learning model to provide clear and understandable explanations for its predictions or decision-making processes.

Classic statistical methods such as logistic regression, linear regression, and decision trees are considered glass boxes because they have coefficients and nodes that can be interpreted. Newer algorithms such as neural networks and boosted trees are black boxes. Commonly used solutions to aid explainability include:

•Feature importance

•Model visualizations

•Partial dependence plots, heat maps, and decision trees

•Local Interpretable Model-Agnostic Explanations (Lime) is a technique that adds noise to the original data points, then feeds it into the black box model and then observes the output. Each original data point can be explained by the newly trained explanation model. ⁶ This option is not available in Orange.

•Shapely Additive Explanations (SHAP) are used to explain linear, tree-based, and neural network models. More about SHAP in Chapter 5, section 5.4 number 8.

•Permutation feature Importance shuffles features in a column and determines the effect it has on the outcome, e.g., AUC. (It can be used for classification or regression). The idea is that if shuffling a predictor causes the model performance to degrade significantly, the predictor must be important. More on this in Chapter 5. section 5.4.6.

  
![](images/image-427RBSI1.png)  

Figure 4.7 Model complexity plotted against model error

  

4.3 GRADIENT DESCENT

  

  

Gradient descent is an optimization algorithm used to train machine learning models and neural networks. The goal is to achieve the lowest error rate (cost/loss) for each model. The model will continue to adjust parameters to yield the smallest possible error. Therefore, the gradient descent curve is U shaped. See Figure 4.8.

The starting point of the descent curve is an arbitrary point. From that starting point, the slope is derived, and a tangent line is used to observe the steepness of the slope. The slope will inform the updates to adjust the weights and biases. As new parameters are generated, the steepness will reduce until it reaches the lowest point (point of convergence). The goal of gradient descent is to minimize the cost (loss) function or the error between predicted and actual outcome. To do this, it requires direction and a learning rate.⁶ The following are some important associated concepts:

•Learning rate (step size) is the size of the steps to reach the minimum. Large learning rates result in larger steps, but this might overshoot the minimum. Conversely, a low learning rate means more but smaller steps resulting in decreased efficiency, because it takes more time and computations to reach the minimum.

  
![](images/image-K1UCLF97.png)  

Figure 4.8 Gradient descent ⁷

  

•The cost (loss) function measures the error between the actual outcome and the predicted outcome. The model can then adjust the parameters to minimize the error. Once the minimum has been reached the model will stop learning.

  

#### 4.3.1 Local and Global Minimum

  

The global minimum is as close as gradient descent can get to minimizing the cost/loss. In the process, the algorithm may encounter dips or valleys known as local minima and there can be several, whereas there can only be one global minima. If the process gets stuck in a local minima, then there may be less than optimal cost.⁷ See Figure 4.9

  
![](images/image-AZ007E1N.png)  

Figure 4.9 Local and global minima ⁷

  

#### 4.3.2 Types of Gradient Descent

  

•Batch gradient descent sums the error for each point in a training set, updating the model only after all training examples have been evaluated in a “training epoch.” Batching is efficient but can have a long processing time for large training datasets. Batch gradient descent usually produces a stable error gradient and convergence, but sometimes that convergence point is not ideal, resulting in a minimum instead of a global one.

•Stochastic gradient descent (SGD) runs a training epoch for each dataset example and updates each training example’s parameters one at a time. Because you only need to hold one training example, they are easier to store in memory. Frequent updates offer more detail and speed but can reduce efficiency compared to batch gradient descent. Frequent updates can help escape the local minimum and find the global one.

•Mini-batch gradient descent combines concepts from batch gradient descent and stochastic gradient descent. It splits the training dataset into small batches and updates each batch. This strikes a balance between the computational efficiency of batch gradient descent and the speed of stochastic gradient descent. ⁸

  
![](images/image-XSRPDX4P.png)  

Gradient Descent (StatQuest)

  

4.4 ORANGE ALGORITHMS

  

  

Appendix B includes most major machine learning algorithms, including the year of origin, a description, and an example.

An attractive feature of Orange is that it has an algorithm option from each of the major algorithm families and multiple algorithms can be run simultaneously. The modeling performances for these simultaneous runs can be viewed in the Test and Score widget. It is quite easy to compare multiple algorithms simultaneously, a feature absent in many data science platforms. Additionally, as pointed out, a user can toggle between training data and test data results to see which algorithms are performing best, a helpful software feature.

The algorithm descriptions in this chapter can be supplemented with additional information obtainable by right-clicking the widget and selecting the Help menu. These algorithms can be “optimized” with various option and parameter settings that are visible by double-clicking on the widget and looking at the specific choices available for each algorithm. As you start, it is best to accept the default widget parameter settings. Optimizing every algorithm is beyond this course’s scope, so we will only show a few minor tweaks. As an educational point, tuning algorithms for optimal results is known as “hyperparameter optimization” (HPO).⁹ In machine learning, model parameters refer to intrinsic characteristics of the algorithm that can be modified in attempts to improve the model’s performance.

Model Parameters are something that a model learns on its own. For example, 1) Weights or coefficients in linear regression. 2) Support vectors in SVM. 3) Split points in a decision tree.

Model hyper-parameters are used to optimize the model performance. For example: 1) Kernel in SVM. 2) Value of K in KNN. 3) Depth of trees in decision trees. For more information, see resource # 8.

  

#### 4.4.1 Constant Widget

  

This is a widget that serves as a very conservative baseline performance of a model that all other modeling activities should surpass. The Constant widget routine will always pick the majority class for classification and the mean for regression models. For example, if 95% of patients do not have cancer, they are the majority class, so the Constant widget results in the Test and Score widget will report 95% accuracy. Therefore, for an algorithm to be helpful, its prediction accuracy must exceed 95%.

  

#### 4.4.2 K Nearest Neighbor (kNN) Widget

  

•kNN is a relatively simple algorithm used for classification and regression.

•The algorithm looks for its nearest neighbors to group similar data. You can tweak/tune the number of neighbors (k) and the method to measure the distance between neighbors, using, e.g., Euclidean distance. ¹⁰

•kNN is referred to as a “lazy learner” algorithm because it does not learn from the training set immediately. “Instead, it stores the dataset, and at the time of classification, it acts on the dataset.” ¹¹

•This algorithm requires selecting an optimal k value, but note that the computational cost is high.

•In Figure 4.10 , you are trying to classify the new data point (?) into Class A or B. You can select three nearest neighbors (K =3) or seven nearest neighbors (K=7). When k = 3, the data point will belong to B, but when k =7, it will belong to A. K measures the proximity between data points to classify new data points, like class A or B.

•This widget normalizes data and imputes missing values. It also converts categorical data to numerical by one-hot encoding. KNN is sensitive to outliers.

•kNN is used in other data science applications to determine data proximity. For example, Synthetic Minority Oversampling Technique (SMOTE) uses kNN to find minority samples to help balance imbalance datasets. ¹²

•More information on finding the optimal k value can be found in this reference. ¹³

  
![](images/image-VQ78G0TY.jpg)  

Figure 4.10 k-nearest neighbor algorithm (courtesy KDNuggets.com)

  
![](images/image-L7NLPXTS.png)  

K-Nearest Neighbor (StatQuest)

  

#### 4.4.3 Decision Tree (DT) Widget

  

•DTs can be used for classification and regression.

•Some refer to one type of DT as CART (classification and regression tree).

•Trees are great for early exploration, visualization, and interpretation, but not as accurate as newer algorithms. ¹⁴

•The main drawback of decision trees is their tendency to cause overfitting because they may split too many times in an attempt to include every data point. That means the results calculated on the training data demonstrate a low error rate but a much higher one on the test data. The default settings for Orange, JASP, and Bluesky Statistics decision trees protect against severe underfitting or overfitting. This is an important reason to generate and compare performance metrics on both training and test data. One can prune (reduce the depth of nodes/leaves) the tree to prevent overfitting. Try different tree depths (e.g., 4-6) and see how much the AUC changes on a validation set.

•Double-click on the DT widget and adjust the depth of the tree if your results are suboptimal or you have overfitting.

•Use the Tree Viewer widget (Visualize menu) connected to the tree widget to view the tree.

•An image of a typical decision tree can be found in Chapter 3 .

•Further information about how trees work can be found in Chapter 2 discussing the Rank widget, in Chapter 3 and in this article. ¹⁴

  
![](images/image-07AYC5OR.png)  

Decision Trees (StatQuest)

  

#### 4.4.4 Random Forest (RF) Widget

  

RF is considered an ensemble-type algorithm because it combines multiple “weak learners” (trees) together to become a strong learner. Multiple trees = forest

•RF analyzes a forest of trees in a parallel fashion (not sequential).

•RF is more accurate than a standard tree.

•RF has an option for imbalanced data that adds weights to the minority class.

•RF is used for classification and regression.

•The widget has options to adjust the hyperparameters. The defaults are the number of trees = 10, and the “do not split subsets smaller than 5’’ box is checked.

•RF is tolerant of missing data, and data does not have to be scaled or normalized. Categorical data is automatically converted to numerical and missing data is imputed.

•Bagging means training individual weak learners (trees) on random subsets of training data and obtaining the outcome from the individual predictions. The performance of one model is independent of the other. Each model is trained on a randomized subset of data sampled with replacement. The sampling approach is called bootstrap sampling. This leads to the name Bootstrap Aggregating, or in short, Bagging. A randomized ensemble of decision trees is called a Random Forest. In Figure 4.10 , an RF is visualized with a majority vote.

  
![](images/image-T383O8FR.png)  

Random Forest Part 1 (StatQuest)

  

#### 4.4.5 AdaBoost (Adaptive Boosting) Widget

  

AdaBoost is an early (1996) ensemble algorithm based on “boosted” trees.

•Boosted means the trees are evaluated sequentially. (Boosted = sequential).

•AdaBoost is susceptible to outliers, but newer versions are less so. It automatically preprocesses the data as was done with random forest.

•In boosting, the training data is sampled without replacement so that data is used exactly once. Boosting is a sequential ensemble approach in which a model is first trained on one subset, and the error rate is corrected before the next sequential model. Therefore, each model is dependent on other models. Boosting is a good approach when the data has high bias but it also helps to reduce variance.

  

#### 4.4.6 Gradient Boosting (GB) Widget

  

•GB is one of three boosted algorithms offered on this widget. Click the widget; the choices are gradient boosting, catboost, and xgboost. Xgboost Random Forest is an ensemble algorithm that acts like a random forest and selects the best from multiple xgboost algorithms.

•These ensemble gradient boosting choices should outperform ADA Boost.

•Catboost was released in 2017 and can handle categorical data. Accept the default hyperparameters.

•Ensembles can perform both classification and regression. It automatically preprocesses the data as was done with random forest.

•Ensemble methods are popular for data competitions.

•The defaults are: 100 trees, Learning rate = 0.3, Depth of trees = 6, and the fraction of features for each tree = 1.0. The learning rate specifies the contribution each tree makes to the ensemble. You can adjust the hyperparameters and analyze the performance metrics.

•Gradient boosting has the same pros as random forest.

•Catboost and Xgboost can be regularized with L2 by adjusting the lambda value. The results from this widget can be explained with an additional widget ( SHAP ), found in the Add-ons under the Explain module.

  
![](images/image-0B4N21TC.png)  

Figure 4.10 Random forest (courtesy Wikipedia)

  

•Ensembles are non-parametric and do not require the data to follow a particular distribution, but they may benefit from data transformations.

•They can handle mixed data types: categorical variables do not have to be manually one hot encoded.

•Multi-collinearity of features does not affect the accuracy and prediction performance of the model: features do not need to be removed or otherwise engineered to decrease the correlations and interactions between them.

•They are less likely to overfit because they use many weak learners that underfit (high bias) and combine those predictions into a stronger learner, they reduce the overfitting (variance) of the model.

•Inputs do not need to be scaled (normalized).

•They are computationally relatively inexpensive, so faster than SVMs or ANNs.

•They may have superior performance with imbalanced datasets compared to other algorithms.

[•Figure 4.11 Compares bagging with boosting techniques. ¹⁵](#content0109.xhtml)

  
![](images/image-4CB3914C.png)  

XGBoost Classification (StatQuest)

  

#### 4.4.7 SVM (Support Vector Machine) Widget

  

•SVM is used for classification and regression.

•SVM separates the attribute space with a hyperplane, using a kernel function ( Figure 4.12 ).

  
![](images/image-HMCRZHWP.png)  

Figure 4.11 Bagging and boosting (courtesy Pluralsight.com)

  

•Support vectors are the coordinates of individual observations. They are the selected points on the boundary of both sets, defining the margin between clusters.

•The SVM algorithm has a feature to ignore outliers, concentrate on the support vectors and find the hyper-plane that has the maximum margin. ¹⁶

  
![](images/image-0YUJECTF.png)  

Figure 4.12 SVM hyperplane

  
![](images/image-G8AW74TI.png)  

Support Vector Machine (StatQuest

  

#### 4.4.8 Linear Regression Widget

  

•The goal of regression is to evaluate two things: A. Does a set of predictor variables predict an outcome (dependent) variable well? B. Which variables are significant predictors of the outcome variable, and how do they impact the outcome variable as indicated by the magnitude and sign of the beta estimates? The simplest form of the regression equation with one dependent and one independent variable is defined by the “formula y = c + b\*x, where y = estimated dependent variable target, c = constant, b = regression coefficient, and x = the value of the independent variable.” ¹⁷ More on this will be covered in Chapter 6 .

•Results can be improved with Lasso and Ridge regularization (reduces under and overfitting). For more about regularization, see the keypoint note. Regularization is available to adjust in both the linear and logistic regression Orange widgets.

•Statistical linear regression (least square regression) is the gold standard for regression. Ordinary least squares (OLS) “is the method of fitting a regression line by minimizing the sum of squared residuals.” ¹⁸ Many new algorithms can also perform regression, such as random forest and gradient boosting. Remember that statistical models come with assumptions that should be met, whereas the newer machine learning algorithms have fewer assumptions, such as a normal distribution.

•Outcome is measured by R squared, root mean squared error (RMSE), etc. More on regression outcome measures are discussed in Chapter 6 .

[•Figure 4.13 displays simple linear regression, in which one numerical value attempts to predict another numerical value. We will often be dealing with multiple linear regression with multiple predictors.](#content0109.xhtml)

[•Figure 4.13 shows how accumulated savings are related to an employee’s time on the job. If an employee has been on the job for ten weeks, the calculation is 400 + 307.50 x 10 or savings of $3475. Notice that a correlation coefficient is generated that tells you the strength of the relationship between the x and y variables. The correlation coefficient can range from -1 to +1.](#content0109.xhtml)

  

  

KEYPOINT: Regularization simplifies or shrinks the regression coefficients to make the model simpler and less likely to cause overfitting or underfitting. It causes it to focus more on the signal and less on the noise. Hence it fits the data better. There are several types of regularization:

Lasso (L1) - adds a penalty equivalent to the sums of the absolute values of the coefficients. Ridge (L2) - adds the penalty equivalent to the sum of squares of the magnitude of coefficients.

Elastic net - this choice combines the penalties of L1 and L2 ²⁰

  

  
![](images/image-V1EEUUFB.png)  

Figure 4.13 Simple linear regression ¹⁹

  
![](images/image-ODGARHPT.png)  

Linear Regression (StatQuest)

  

#### 4.4.9 Logistic Regression Widget

  

•A highly respected statistical model used primarily for binary classification.

•Some would consider this algorithm as the gold standard for binary classification.

•Logistic regression predicts the probability that a data point belongs to one class or the other (dichotomous or binary). Results range from 0 to 1 (see Figure 4.14 ). In other words, its prediction might be 0.95, close to 1, or 0.15, or close to zero.

•We suggest you accept the LR widget defaults but note that there is an option to “Balance class distribution.” Select this option if you have class imbalance.

•You also have the option to select Ridge or Lasso. The Elastic Net regularization option is only available for linear regression, not logistic regression.

•With both linear and logistic regression, you can connect the widget to the File widget and connect the output to a data table, and you can then see the coefficients. You can then sort the coefficients column and observe which variables positively and negatively correlate with the prediction.

  
![](images/image-IERFZE29.jpg)  

Figure 4.14 Logistic regression

  

•The Nomogram widget is found in the Visualization module and can be used to examine logistic regression and Naive Bayes. Connect the File widget to logistic regression and connect the latter to the Nomogram widget. Select the target = 1. The default baseline probability is 40% for colored (calcified coronary arteries), but when you slide the blue bullet to the right to 3 (indicating three calcified arteries), the probability goes to 91%. The most important predictor comes first, and all are customizable. See Figure 4.15 .

  
![](images/image-DLOAVHVE.png)  

Logistic Regression (StatQuest)

  

#### 4.4.10 Naive Bayes (NB) Widget

  

•NB is based on Bayes Theorem that dates back to 1763.

•Prior probability (prevalence) plus likelihood predicts the revised or updated (posterior) probability (see Figure 4.16 ).

•We use Gaussian Naive Bayes that depends on normally distributed data.

  
![](images/image-WZU08FH4.png)  

Figure 4.15 Nomogram for logistic regression

  
![](images/image-WBO9HYMD.png)  

Figure 4.16 Naive Bayes formula

  

•Naive means the predictor variables are supposed to be independent of each other which is frequently not the case.

•The nomogram widget helps explain Naive Bayes, similarly as it did for logistic regression.

•It is a probabilistic algorithm that also performs multi-class classification.

•Naives Bayes works very well on small classification models. ²¹

•More about the calculations behind NB at this reference. ²²

  
![](images/image-XKHAXEO4.png)  

Naive Bayes (StatQuest)

  

#### 4.4.11 Neural Network (NN) Widget

  

•NNs are networks consisting of node layers, containing an input layer, one or more hidden layers, and an output layer. The nodes perform mathematical operations to find patterns in data. Each node connects to another with an associated weight and threshold. If the output of a node is above the specified threshold value, that node is activated, sending data to the next layer. Otherwise, no data is passed to the next layer of the network.

•Orange uses a multilayer perceptron (MLP) derived from a Python package.

•The widget allows for setting the number of hidden layers, the type of activation, the type of solver, the degree of regularization, and the maximal number of interactions.

•Neural networks can be used for classification and regression, as well as image recognition and natural language processing.

  
![](images/image-RYTLVDKN.png)  

Figure 4.17 Input, hidden layers and the output layer

  

[•Figure 4.17 shows the input, hidden and output layers. Figure 4.18 shows that weights are assigned to inputs, then summed, and these are constantly tweaked until the model has a minimal error. Not shown are the biases that are also added. The process begins with random weights and a bias of zero. The initial process is like linear regression, where the model is fitted and adjusted with coefficients. Bias is analogous to the intercept. The activation function works like a threshold trigger. Figure 4.19 shows a common default activation function known as rectified linear activation unit (ReLu) activation function. ReLu adds non-linearity to a neural network to help it identify patterns. Any positive value is outputted; other values are made zero. The neural network continues to optimize weights until the desired output is achieved. The neural network’s forward propagation is displayed, but there is “backpropagation,” so weights are adjusted to minimize errors. This process of optimization of weights uses the gradient descent algorithm that minimizes loss/errors. This is a complex process, so additional reading or videos are advised. The following video is highly recommended. ²³](#content0109.xhtml)

  
![](images/image-00C2RUPW.png)  

Neural Networks Part 1 (StatQuest)

  
![](images/image-J2GX5R5C.jpg)  

Figure 4.18 Neural Network Neurons

  

#### 4.4.12 Stacking Widget

  

Stacking combines several algorithms to improve performance. There is no limit to how many models you can attach to the stacking widget in Orange. This is an ensemble or combination of algorithms similar to the tree-based ensembles, such as random forest and xgboost. Ensembles add the best attributes of all models together to make it a powerful model of models. In Figure 4.20, the learners (algorithms) are Naive Bayes, k-NN, and random forest, and the aggregator is logistic regression. The connection from logistic regression to the stacking widget should be set to “learner >> aggregate.” If no aggregation input is given, the default methods are used. Those are Logistic Regression for classification and Ridge Regression for regression problems. Stacking resulted in mild improvement in accuracy, F1 score, precision, recall, and specificity. Stacking can be used with classification or regression. (See Table 4.1). ²⁴

  
![](images/image-NLSSDM2Y.png)  

Figure 4.19 ReLu activation function

  

Table 4.1 Stacking Results for classification model

  
![](images/image-EVVH2VBD.png)  
![](images/image-Y61UTWY2.png)  

Figure 4.20 Stacking workflow

  

#### 4.4.13 Save Model Widget

  

This widget saves the model as a pickle file (.pkl) in the Orange folder. Note: the algorithm is connected to the File and Test and Score widget. When you want to save a custom-set model, feed the data to the model (e.g., Logistic Regression) and connect it to the Save Model widget. Name the model, and load it later into the workflow with the Load Model widget.

  
![](images/image-78U7FQIS.png)  

Figure 4.21 Workflow to save and load models

  

#### 4.4.14 Load Model Widget

  

This is used when you want to use a custom-set model you have saved before. Open the Load Model widget and select the desired file with the Browse icon. This widget loads the existing model into the Predictions widget. Datasets used with the Load Model widget have to contain compatible attributes with the original data the model was trained on! The Save Model widget will not save the model unless the File widget is directly attached to the model you want to save. See Figure 4.21.

  

4.5 JASP MODELS

  

  

In the regression module JASP offers linear and logistic regression. The machine learning algorithms are found in the machine learning module in JASP. In the following sections, we will discuss the algorithms available for modeling in JASP. When an algorithm is selected, you see the following icon choices on the left. The first black icon is for editing the title of the work. The second green + icon allows you to duplicate your work. The third blue “i” icon provides information on the algorithm, and the fourth red “X” icon deletes the work. See Figure 4.22

  
![](images/image-78SASQZD.png)  

Figure 4.22 JASP icons

  

#### 4.5.1 Linear Regression

  

A standard linear regression is offered with unstandardized and standardized coefficients shown.

Regularized linear regression is available in the machine learning module and is the recommended approach. This second approach allows you to decide how to split the data into training, test, and validation datasets and apply L1(Lasso) regularization. JASP also has many other options available, some of which are listed below:

•Evaluation metrics: MSE, RMSE, MAE, MAPE, and R ²

•Regression coefficients are reported.

•Collinearity diagnostics (VIFs)

•More detail about linear regression is discussed in Chapter 6 .

•Other algorithms available for linear regression in the machine learning module: Boosting, decision tree, neural networks, random forest and support vector machines.

  

#### 4.5.2 Logistic Regression

  

A classic logistic regression model is generated with coefficients, odds ratios, and Wald test results. Table 4.2 shows the logistic regression results on a reduced variable sample of the heart disease prediction dataset. JASP also has many other options available, some of which are listed below:

•Coefficients

•Odds ratios

•Multicollinearity Diagnostics (VIFs)

•Wald test

•Performance reported as accuracy, AUC, recall, specificity, and precision. ROC and PR curves are options.

  

Table 4.2 JASP Logistic regression results

  
![](images/image-RBY5SHD2.png)

  

#### 4.5.3 JASP Machine Learning Algorithms

  

Overall, the algorithms and functionality in JASP are similar to Orange, but JASP offers more classic statistical options. Most algorithms have hyperparameters that can be adjusted by scrolling down to the Training parameters section. JASP has robust performance metrics, as seen in Table 4.3.

  

Table 4.3 Evaluation metrics in JASP for boosting on heart disease prediction dataset

  
![](images/image-JKAM4CV5.png)  

Several differences, however, should be pointed out:

•The dataset in JASP is tested on test data, but you never see the results on the training dataset, so determining over or underfitting seems to be missing.

•You must run one algorithm at a time making comparisons slower than Orange. Moreover, you must re-enter the target and features each time, and the train, test, and validation splits.

In the machine learning module under Classification, there are multiple algorithms. Most are similar to Orange, with a few differences. Decision trees and random forest include feature importance that conveys what the algorithm considers significant, as displayed in Table 4.4. This is analogous to the Rank widget in Orange. The following JASP algorithms are available:

•Boosting: this is likely a standard gradient boosting algorithm.

•Decision tree: includes feature importance

•K-nearest neighbor

•Linear discriminant analysis

•Neural networks: includes network weights

•Random forest: includes feature importance

•Support vector machine

  

Table 4.4 JASP Feature importance for a decision tree

  
![](images/image-BM50L605.png)

  

4.6 MLOps

  

  

The work is not over once the model is created; it must be deployed. The operationalization of a machine learning model is known as MLOps. Some define MLOps as having three components: Machine learning, development, and operations; each with a set of different processes, as shown in Figure 4.23.²⁵ MLOps is an iterative process with continuous improvement and monitoring as the goal. This is more in the realm of the data engineer than the data scientist. The seasoned data analyst focuses more on obtaining meaningful results from available data.

An optimized model is often saved as a pickle file (.pkcis), and new data is processed as either a loaded batch file, e.g., hourly, daily, weekly, or loaded online. Online means the data is processed right away. Online services usually occur through web services or streaming. Users can send HTTP requests (typically JSON format) to return the predictions. The service reacts to the request and applies the model and saved predictions to another stream for streaming. Users can subscribe to the output stream and make decisions based on the predictions. Once the model is deployed, it must be monitored to determine if there is concept or data drift, as explained in the next section.

  
![](images/image-6357OBSQ.png)  

Figure 4.23 The MLOps process

  

4.7 TACKLING MODEL CHALLENGES

  

  

In 1976, the well-known statistician George Box said, “All models are wrong, but some are useful.” ²⁶ He was reflecting on the problem with statistical models not always capturing the complexity of the data, hence not being very accurate. Since then, we have seen many statistical and machine-learning models created. To succeed, a model must make good sense to the end users (clinicians, patients, and customers), the C-suite (good business case), CIO, and data scientists or seasoned data analysts (technologically sound project).

  

  

KEYPOINT: Unfortunately, models fail for many reasons outlined in the following paragraphs. Creating a model is the easy part.

Model problems can start with inadequate data in terms of volume and quality. Deep learning models require a large volume of data, and performance depends on labeling accuracy, which is not always correct. Overfitting and overly optimistic models are very common with machine learning. Failure to report all performance parameters is common, and failing to deal with imbalanced datasets appropriately occurs frequently.

  

  

The literature is full of predictive models representing proof of concept. Many are never deployed, and many fail. A recent survey suggests that approximately 80% are never deployed. Authors of the survey posit that inadequate leadership was responsible for the low deployment rate. ²⁷ Furthermore, models are rarely validated with data from outside the institution, so they may not be generalizable. However, comparing results with external data can be difficult because of the differences in patient demographics, patient mix, etc.²⁸ Additionally, very few prospective trials are launched based on the model to see how its predictions compare with actual patient results.

Long term, models need to be checked and equilibrated to prevent “model drift.” Model drift has two components, concept drift, and data drift. The former means when the statistical properties of the target variable change over time, such as disease prevalence. Data drift means when the statistical properties of the predictors change due to, e.g., seasonality. These changes can be obvious or subtle but must be followed over time. It is likely that most models will need to be retrained at some point. More details at this reference.²⁹

  

#### 4.7.1 Model Bias and Fairness

  

In section 4.2.1, we discussed the bias-variance tradeoff. In reality, multiple other types of bias are encountered in data science. Most are methodological biases, and when found, they adversely affect the accuracy and generalizability of the machine learning model. For example, if your dataset includes primarily white men, you will likely have bias towards them in the model, making it less relevant to other genders and ethnicities. Another example would be class imbalance, where you do not have enough subjects from the minority class. Let us begin with a discussion of biases relevant to data science. ³⁰-³²

•Systemic bias : occurs when specific groups are persistently over or underrepresented.

•Automation bias : is the tendency to adopt or believe technology without any form of substantiation.

•Selection bias : occurs when individuals or groups are selected for a study that are not representative of the population of interest.

•Reporting bias : can take several forms. Citation bias occurs when the literature search only selects a narrow spectrum of articles. Language bias occurs when only a native language is chosen. Publication bias occurs when only positive outcomes are reported or read.

•Overgeneralization bias : occurs when you attempt to apply findings from your dataset to other different datasets.

•Group attribution bias: is the human tendency to believe that an individual in a group shares the same beliefs as all members of the group.

•Implicit bias : refers to the unconscious tendency to embrace certain attitudes or stereotypes.

  

#### 4.7.2 Navigating Imbalanced Datasets

  

4.7.2.1 Introduction

  

An entire section has been devoted to class imbalance for several reasons. Medical and other industry data is often imbalanced with the minority class of interest, e.g., hospital “readmitted” being smaller than the majority class “not readmitted,” medical errors, patient complaints, manufacturing scrap, rework, equipment downtime, customer service complaints, customer product complaints, and other issues being smaller than the positive side of that equation. Traditionally, the minority class is labeled 1, and the majority class 0.

There is no formal definition of imbalance, such as a ratio of majority to minority class greater than five or some other rule of thumb. Some say any imbalance starts to hurt the model performance at low imbalance ratios, but others suggest that only higher ratios of imbalance are of great concern. Some say that model sensitivity all depends on the complexity of the data set. So how much of an imbalance between classes is deemed as severe? Brownlee suggests that an imbalance ratio of 100:1 to 1,000:1 should be deemed as severe between classes.³³ Google offers these guidelines for assessing the degree of classification imbalance for specific imbalance ratios: 2.5:1 to 5:1 as mildly imbalanced, 5:1 to 100:1 as moderately imbalanced, and over 100:1 as severely imbalanced. ³⁴ Kaggle defines imbalanced data as any class with at least ten times more data than another class. ³⁵ As we can see, the stated definitions for class imbalance are not standardized and agreed on by all sources.

  

  

KEYPOINT: The problem is that class imbalance impacts classification model performance metrics such as accuracy and AUC. Most algorithms used for predictive analytics with classification functions work better with a balanced dataset. Therefore, any level of class imbalance should be taken seriously and evaluated with data experiments before final modeling decisions are made.

  

  

In addition, the international machine learning guidelines, such as TRIPOD ML, provide no guidance as to how to approach class imbalance.³⁶ Does that mean there are no guidelines for this issue, or does it mean that there is inadequate research on this issue? This chapter will discuss the typical model performance metrics used when class imbalance is present and a framework to approach the problem.

Creating hIgh-performing models requires several experiments for a specific dataset to find the best options for data imputation, data transformation, normalization methods, and imbalance methods.

  

  

KEYPOINT: Shortcuts are not rewarded in data science, and standard defaults are often not the best choices. One should also be careful not to assume always that the experimental results for one dataset will provide the ideal choices, best practices, and solid guidelines for a different dataset. There is no free breakfast, lunch, or dinner in predictive modeling. The only possible guarantee in advanced data analytics and data science is that the blind application of superficial guidelines, the pursuit of shortcuts, and the lack of data science experiments will be severely punished with inaccurate predictive models.

  

  

We should always remember that predictive modeling is the complex art and science of predicting the future with math models and that the future will greatly resist such efforts to understand its intent. Predictive modeling should not be taken lightly or approached in a naive manner.

  

  

KEYPOINT: Healthcare datasets often contain large groups of healthy individuals and much smaller groups of unhealthy individuals. They may also contain large amounts of information about certain population groups but need more information about other population segments. This imbalance in the quantity of data for different groups of interest in a dataset can cause all sorts of issues for machine learning algorithms that can impact the accuracy of their predictions and bias the predictions only to be accurate for the majority class.

  

  

When dealing with imbalanced datasets, it is important to check the “stratify sample” option in the Data Sampler widget so that the training and test datasets get the same proportions of minority class data samples. For extreme class imbalances, this step will eliminate the risk that the smaller test dataset does not get any or not enough of the minority class data samples.

  

4.7.2.2 Model Performance Metrics for Class Imbalance

  

If you have reason to believe that you have class imbalance that is adversely affecting the performance of your model, then you need to look for performance metrics beyond the AUC and classification accuracy (CA) metrics. Both are overly optimistic in the face of class imbalance.

• The precision-recall curve (PRC) plots recall (sensitivity) on the x-axis and precision on the y-axis at different decision thresholds. Remember that recall is calculated as true positives divided by true positives plus false negatives. Precision (positive predictive value) is a ratio of the number of true positives divided by the sum of the true positives and false positives. It describes how good a model is at predicting the positive class.

The PRC is preferred for class imbalance as the PRC focuses on the minority class (true and false positives), which is usually the class of interest. The PRC is one of the three model performance curve options available in the Performance Curve widget, found in the Evaluate module of Orange. The Performance Curve widget is connected to the Test and Score widget, and the settings should be set as Target = 1 and Model = logistic regression.

The ROC has a default probability threshold of 0.5. The “no skill level” of the AUC is also assumed to be 0.5, which is represented by the diagonal line on the ROC curve. In other words, an AUC of 0.5 is no better than a guess, and it also means it does not “discriminate” well between the two classes (positive and negative).

Unlike the AUROC (Area Under the ROC curve), the “no skill level” for the AUPRC (Area Under the PR Curve) is equal to the percent positive samples that are represented by a horizontal line on the PR curve that intersects the y-axis indicating the proportion of positive samples in that dataset. The no skill level in Figure 4.24 is displayed by the horizontal line labeled “Baseline Classifier.” In a different example, if 5% of samples show cancer and 95% do not, the no skill level would be set at 0.05. For a dataset with equal classes, the no skill level = 0.5 because the class of interest = 50%. Figure 4.24 displays a perfect classifier, a pretty good classifier, and a baseline classifier. ³⁷

A “classifier” is an algorithm that attempts to make a good prediction in a specific dataset.

  
![](images/image-NPNM91XJ.png)  

Figure 4.24 PR curve with three different performing classifiers

  

  

KEYPOINT: A threshold is the decision boundary or cutoff point used to separate one classification class from another. In a zero and one binary classification choice, the default threshold is 0.5. This means that if a probability is calculated as 0.49, it will join the zero class. If a probability is calculated to be 0.51, it will join the 1 class.

  

  

You can calculate the percent positives from the data or visualizations, e.g., Pareto charts. The third way is to use the Constant widget that makes predictions based on frequency alone. Using the balanced heart disease prediction dataset with about 46% positive cases, you can see in Figure 4.25 that the no skill level is set at 0.46. You want to be sure the PRC performance is above the no-skill baseline level, just like you would like to see the AUROC above 0.5.³⁸ In Figure 4.25, note the shading under the PRC, the area under the PRC (AUPRC), and equal to 0.925 (92.5%) for the logistic regression algorithm, which Orange shows in the bottom left area of the PRC output. Note the horizontal dashed line that represents the no skill level for this relatively balanced dataset and is equal to 0.46.

The PRC is created by examining precision and recall at different thresholds.³⁹ Using the PRC in Figure 4.25, you can mouse over the data points in the curve, and it will reveal the threshold and the associated precision and recall values. Table 4.3 provides examples of the precision and recall at different thresholds on balanced data.

  
![](images/image-Q2MA05L9.jpg)  

Figure 4.25 AUPRC for logistic regression applied to the heart disease prediction dataset

  

Table 4.3 Precision and recall at different thresholds

  

 
| Threshold || Precision || Recall |
| --- | --- | --- |
| .978 || .974 || .266 |
| .756 || .911 || .682 |
| .559 || .864 || .777 |
| .322 || .753 || .856 |
| .133 || .640 || .950 |

  

  

KEYPOINT: As mentioned in other chapters, precision and recall constitute a tradeoff. With a high threshold, you have captured a small number of positives and no false positives, so precision is very high, but recall is low. Conversely, when the threshold is low, you capture more positive data points but more false positives, so the recall is higher, and precision is lower. For example, using the heart disease dataset and logistic regression when the threshold is adjusted in the Calibration widget, at a threshold of 0.422, precision = 0.833 and recall = 0.827. Ultimately, it is a clinical decision regarding which is more important, recall or precision.

  

  
![](images/image-C3SQMUF4.png)  

Figure 4.26 Precision-Recall curve. Green line for logistic regression. AUPRC = 0.122

  

[Figure 4.26 displays the PR curve for an imbalanced dataset where the percent positives are about 5.5%. Note that the PRC and the AUPRC are much lower but so is the no-skill level on the PRC graph (horizontal dashed line). Importantly, even though the AUPRC is lower it is still higher than the area just under the no-skill level.](#content0117.xhtml)

Because of the severe class imbalance in this example, the threshold is lower. For example, at threshold of 0.127, the recall = 0.5, and precision is 0.181.

When reviewing a PRC curve, we must adjust our thinking when compared to what we may be familiar with when comparing it to the ROC curve.

On the ROC curve, we can make these observations and conclusions:

•The “no-skill” level is a 45-degree line.

•Any model with very good performance on the ROC graphic will have to create a curve that extends to the far upper left-hand side of the ROC graphic.

•Any AUC for the ROC above 50% (the 45-degree diagonal no-skill level line) is considered as moving in the right direction.

On the PRC graphic, we can make these observations and conclusions:

•The “no-skill “level is a horizontal line that is set at the percent of positive cases in that dataset which can vary wildly based on the percent of imbalance in a dataset.

•Any model with very good performance on the PRC graphic will have to create a curve that extends to the upper vertical side of the PRC graphic. Even if the horizontal line is low, the only indication of whether the model is good or not is how far it extends to the upper side of that horizontal line.

•Any AUC for the PRC above the percent of positive cases (horizontal no-skill level line) is considered as moving in the right direction.

Problems when comparing the AUROC values with the AUPRC values:

•The AUC-ROC summarizes the performance of a model by measuring the trade-off between the true positive rate (TPR) and the false positive rate (FPR) at different classification thresholds.

•The AUC-ROC can be misleading when evaluating models on highly imbalanced datasets.

•The precision-recall curve focuses more on the positive class and is particularly useful when dealing with imbalanced datasets.

•The AUC-PRC is more sensitive to changes in performance for imbalanced datasets.

•Even if we just compared the AUC for each of these metrics that is only above the no-skill level on each of the two graphics, the comparisons between the two metrics would not be an apples-to-apples comparison based on the above mentioned points

The F1 score is helpful in a class imbalance situation because it focuses on the minority class, specifically true and false positives. The F1 score is the harmonic mean for precision and recall. ⁴⁰

•The F1 score = 2 \* (precision \* recall)/(precision + recall). If precision = 0.5 and recall =1, then two times (0.5 times 1) divided by 0.5 plus 1 = 0.66.

•F0.5 score = ((1 + 0.5^2) \* Precision \* Recall) / (0.5^2 \* Precision + Recall). As an example, ((1 + 0.5 ² ) X 0.5 X 1 / 0.5 ² X 0.5 + 1) = 0.625/1.125 = 0.55.

•F2 Measure = ((1 + 2^2) \* Precision \* Recall/ (2^2 \* Precision + Recall). For example, ((1+2 ² ) X 0.5 X 1 / 2 ² X 0.5 + 1 = 2.5/3 = 0.833. ⁴¹

  

  

KEYPOINT: F0.5, F1, and F2 are all model performance metrics for evaluating classification problems. They all differ in how they balance precision and recall.

•The F1 score is the harmonic mean for precision and recall and gives equal weight to precision and recall.

•The F0.5 score gives more weight to precision and less to recall.

•The F2 score gives less weight to precision and more weight to recall.

  

  

Matthews Correlation Coefficient (MCC) considers all four values in the confusion matrix (TP, FP, TN, and FN) and is considered to be a balanced metric. A high MCC value (close to 1) means that both classes are predicted well, even if one class is disproportionately under- (or over-) represented. The formula is shown in Figure 4.27. MCC values can range from zero to one, with values of 0.6 or higher considered desirable. ⁴²

  
![](images/image-LZ045G79.jpg)  

Figure 4.27 Matthews Correlation Coefficient formula

  

There are online calculators to calculate the MCC, saving time. ⁴³

In addition, table 4.4 lists the performance metrics that are appropriate for tracking models’ performance with imbalanced data. If we use model performance metrics that are known to only work well for balanced data, the modeling results will be overly optimistic.

  

4.7.2.3 General Methods to Handle Class Imbalance

  

What if we could meet the seemingly outrageous demands of the algorithms, and in return, they would promise to give us the most accurate predictions possible? How can this seemingly impossible compromise be achieved? The possible answer to this dilemma is to enlist the help of two concepts: Oversampling and or undersampling of data classes within a dataset. Orange has no proven method to over- or under-sample data, but other solutions are available. Since the definitions of class imbalance differ between various sources, it would be wise to experiment with each of your own datasets under investigation to determine how your classification model would perform differently if it were perfectly balanced.

To further complicate the matter, many other class balancing techniques should be experimented with to determine which works best for your data. What are the options to optimally handle imbalanced datasets, and how practical and effective are they? The following sections represent some common options for handling imbalanced data. As stated in other chapters, data science has many concepts representing tradeoffs, such as sensitivity-specificity, precision-recall, and bias-variance. Imbalanced data is no exception, so there are tradeoffs we will discuss as we attempt to compensate for imbalanced datasets.

  

Table 4.4 Performance metrics for models with imbalanced data

  

 
| Model Performance Metric || Explanation || Available in Orange |
| --- | --- | --- |
| Matthews Correlation Coefficient (MCC) || −1 and 1 range. 1 = perfect prediction, 0 = random prediction, −1 = total disagreement between predicted and actual values. || Yes -See Test and Score widget |
| Precision Recall Curve || High precision relates to a low false positive rate, and high recall relates to a low false negative rate || Yes - See Performance Curve widget |
| Area Under the Precision Recall Curve (AUPRC) || The AUC value for the Precision Recall (PR) curve is auto-calculated in Orange. Its range is zero to one. Higher is better. || Yes - See Performance Curve widget |
| F1 || The harmonic mean of Precision and Recall (0 to 1 range). Higher is better. || Yes – See Test and Score widget |

  

4.7.2.4 Class Weighting to Address Imbalanced Data

  

One method to improve performance with imbalanced data is to give more weight to the minority class and less to the majority class.⁴⁴-⁴⁵ This weighting penalizes the model more for errors made on the minority class and less on the majority class. This is also referred to as “cost-sensitive learning.” The Random Forest and Logistic Regression widgets offer an option to “balance class distributions,” which executes the weighting process. Open the widgets and select “balance class distribution” to activate this option. This should be the first approach to tackling imbalanced data if you plan to build a binary classification model. When the imbalance stroke dataset (file-share site under Chapter 5 ) is analyzed with logistic regression, the F1 score is 0.206 when weighting is applied but only 0.000 when not applied.

  

4.7.2.5 Oversampling the Minority Class to Address Imbalanced Data

  

A common approach for class imbalance is to oversample the minority class or undersample the majority class. Figure 4.28 demonstrates the resampling methods.

No single approach represents a best practice that can be used for every situation and every dataset. The methods differ based on the algorithm used and the density and composition of the training dataset.

  

  

KEYPOINT: Sampling should only be performed on the training dataset. It should not be performed on the holdout, test, or validation dataset. The goal is to evaluate the model on data that has truly not been seen before and is not artificially augmented with upsampling.

  

  
![](images/image-35GOVV0Q.png)  

Figure 4.28 Under and oversampling ⁴⁶

  

4.7.2.6 Synthetic Oversampling Technique (SMOTE)

  

SMOTE was created in 2002 and is the best-known technique to oversample. To date, there have been more than 80 extensions or modifications of this technique.⁴⁷ SMOTE is primarily used for classification problems; it can also be used for regression with an appropriate modification. SMOTE is available as a Python or R package that uses the k-nearest neighbor algorithm to locate similar data that it adds to the minority data set. It draws lines to all the nearest neighbors and creates new random synthetic data points (5) on those lines, as displayed in Figure 4.29. The problem with SMOTE and other oversampling techniques is the potential for overfitting when the model is evaluated on hold-out test data. SMOTE does not work well with high-dimensionality datasets and may give varying classification performances for different algorithms. Data has to be processed before using SMOTE by converting the data to numerical and normalizing it. This is important because the k-nearest neighbor algorithm relies on accurate, consistent, and normalized distances between data points for all features.⁴⁸

  
![](images/image-IGI5SFHY.png)  

Figure 4.29 SMOTE oversampling examples shown in red ⁴⁹

  

[Figure 4.30 shows how SMOTE added many more stroke patients (dark dots) who were dramatically underrepresented in this original dataset. The dark -shaded regions represent stroke patients, while the light-colored dots and light-shaded regions represent non-stroke patients. In the upper right region of the graph, it should be especially clear that SMOTE added many more data points to the minority class by adding many dots along a straight line between existing stroke patients. In this Figure, the Y-axis is the average glucose level, and the X-axis is age. We created this SMOTE analysis feature in Orange by creating a unique SMOTE widget with the help of the Orange Python Script widget.](#content0117.xhtml)

  
![](images/image-RSVJ425N.jpg)  

Figure 4.30 An example of how SMOTE adds more data points for the dark-colored minority class stroke patients

  

Listed here are some other class balancing options beyond SMOTE, but they are not available or validated in Orange yet:

1\. Borderline Oversampling with SVM trains a support vector machine (SVM) algorithm and uses the decision boundary area to generate synthetic samples. ⁵⁰

2\. Adaptive Synthetic Sampling (ADASYN) generates synthetic samples inversely proportional to the density of the minority class examples. ⁵¹

3\. Synthetic data to correct imbalance . ⁵² We generated synthetic minority data using artificial intelligence using the AI program Mostly.ai and found that the results on the training dataset were much better, with reasonable results for precision and recall. ⁵³ However, like SMOTE, severe overfitting was found when the model was evaluated on the test data that needed to be more balanced.

4\. Ra ndom sampling and bootstrapping with replacement means that random samples are selected from the dataset and reintroduced into the same dataset. This technique adds new data to the minority class to correct the imbalance. Orange does not offer a validated method to oversample.

  

4.7.2.7 Undersampling the Majority Class

  

There are a variety of techniques to downsample the majority class. However, the concern is that you have decreased potentially valuable model information anytime you reduce the data in a majority class. Since we view data as “gold,” undersampling should not be a method at the top of your list unless you are dealing with Big Data. Most experts advise against this approach unless combined with oversampling the minority class, as discussed in the next section. However, this option should be reconsidered if you are only undersampling the majority class and not the valuable minority class data that is often in short supply. The simplest method for undersampling is to randomly delete data examples from the majority class of the training dataset. Other techniques, such as Tomek Links and Near Miss Undersampling, are discussed by Jason Brownlee.⁵¹

  

4.7.2.8 Over and Under Sampling Combinations

  

As discussed, there are techniques to oversample the minority class (e.g., Synthetic Minority Oversampling Technique - SMOTE), undersample the majority class or both, but all of these methods have issues and most require programming. The hybrid technique (undersampling and oversampling) does have the potential for improved model performance.⁵⁴

Random oversampling of the minority class plus random undersampling of the majority class is one approach that has shown promise. However, you should always experiment with your specific dataset to see if you experience any model performance benefits.

Another common hybrid model is SMOTE, and random undersampling of the majority class combination is another common hybrid model. SMOTE, combined with TOMEK (a Python package), is a hybrid technique that involves both undersampling and oversampling. First, SMOTE oversampling is performed, but class distributions may overlap, and this could lead to overfitting. Tomek links will be applied on both original and synthetic instances to address this. It removes the class observation of both classes, which overlaps each other’s space, which is too difficult to assign to a specific class. Hence, Tomek links remove noisy and non-assignable data points so that the remaining dataset becomes easier to classify. The Tomek links identification process is typically applied as a preprocessing step. Instead of removing the observations only from the majority class, it removes ambiguous observations from both classes. This combination could yield higher recall at the cost of precision.⁵¹

  

4.7.2.9 Shifting (Moving) the ROC Threshold

  

The default ROC threshold is always set at 0.50. For a prediction less than 0.5, the assigned class = 0. For a prediction equal to or greater than 0.5, the assigned class = 1. However, the default ROC threshold of 0.5 may not be ideal when class imbalance exists.

There are at least three ways to assess the best ROC thresholds ⁵⁵

•Geometric means (G-mean) calculates the square root of sensitivity x specificity. The larger the result for a given threshold, the better.

•Use the Youden J Index = TPR - FPR. The larger the result, the better.

•Calculate the F1 score at different thresholds. Use the threshold that maximizes the F1 score, which is the harmonic mean of precision and recall.

The following is a table where the G-means and Youden J Index were calculated on the stroke prediction dataset ROC curve using the sensitivity and specificity plot within the Calibration Plot widget (Metrics dropdown menu).

  

Table 4.5 G-means and Youden J Index results based on threshold values

  
![](images/image-H8Y4MJEH.jpg)  

The results of these tests suggest the optimal threshold is around 0.05 and not the default of 0.5! You could also calculate the F1 score for each threshold to get the best compromise between precision and recall.

Orange can view what happens when you change the threshold and save the new threshold and use it in a new model. Here are the steps to find the best threshold in Orange:

1\. In this example, we first set up the File widget with the stroke dataset uploaded from the Chapter 5 file-share folder on the File-share site and connect it to the Data Sampler widget.

2\. Connect this widget to the Test and Score widget with two connectors set to “data sample to data” and “remaining data to test data.”

3\. Connect the Test and Score widget to the Calibration plot widget and open it. Be sure the Test and Score widget is set to “Test on test data.”

4\. Change the metrics drop down to Sensitivity and Specificity. Note: by default, the threshold is set at 0.5, with a sensitivity of only 0.004 and a perfect specificity of 1.0.

5\. Drag the threshold to the left in the orange where sensitivity and specificity intersect, giving a threshold of 0.05, as noted in the above table. Now the sensitivity is 0.807, and the specificity is 0.735. We can agree that this seems better, but the final determination depends on the goal of the classification model. For example, how many false positives are you willing to accept?

6\. In the Calibration Plot widget, you can select the Precision and Recall curve under Metrics and adjust the threshold. Using a threshold of 0.05, you will see that precision is very low at 0.135, and recall is good at 0.807. This means that most positives (strokes) are false positives. What about shifting this threshold? If the threshold is moved to the left at 0.2, the precision increases to 0.218, resulting in a recall of only 0.213. The data science team will have to decide what makes the most sense.

7\. If you have decided that threshold shifting resulted in a better model in the face of imbalanced data, how can you create and save a model with the new threshold? Simply connect the Calibration plot to the Save Model widget. Open the widget, save it with an easy-to-remember name, and be aware that it will be saved as a “pickle file.”

8\. If you now want to use this model on new test data, upload the test data into a File widget and connect to the Predictions widget.

  
![](images/image-5UAY3G7E.png)  

Figure 4.31 Model performance after threshold shifting

  
![](images/image-U5T6BBAE.png)  

Figure 4.32 Orange workflow to shift the ROC threshold, save the new model and test it on new test data.

  

9\. Select the Load model widget, search for the calibrated stroke pickle file, and load it.

10\. Connect the Load Model widget to the Predictions widget.

11\. Open the Predictions widget and select “show probabilities for “1,” and at the bottom, select the target class = 1. Now you should see performance for the model where the threshold has been set to 0.05.

[Figure 4.31 shows the model performance metrics for the above-mentioned activities, and Figure 4.32 shows the Orange workflow used to change the thresholds and test its performance on the model.](#content0117.xhtml)

In general, we recommend starting with weighting logistic regression and random forest and then deciding if you need to shift the threshold in pursuit of an improved model. This will depend on the dataset and the algorithms selected.

  

4.7.2.10 Challenges in Probability-Based Models Amid Class Imbalance

  

Models that use probabilities, such as logistic regression, often lack calibration, meaning they may not accurately predict the minority (1) or majority class (0). Probability in this context can be viewed as model uncertainty since they show the exact probability values used to assign a data point to a specific class. For example, the model predicts a data point as 0.8 and therefore assigns it to the closest class, which is one. Calibrated probabilities mean that probabilities match the true occurrence of events according to a chosen threshold, which is the cutoff point and decision boundary between classes. Calibration can be worsened by class imbalance because the model focuses too much on the majority class since it views the great number of frequencies in the majority class as an important pattern it should focus on.

  

Table 4.6 Model performance with and without the Calibrated Learner widget

  
![](images/image-2BL87RG6.png)  

There are two main techniques to rescale the probabilities:

1\. Sigmoid (Platt) Scaling uses a logistic regression model to transform scores to improve calibration

2\. Isotonic Regression is more complex and involves weighted least squares regression ⁵⁶

Orange also has a Calibrated Learner widget. Orange describes this widget as follows in their help file for that widget: “This learner produces a model that calibrates the distribution of class probabilities and optimizes decision threshold. The widget works only for binary classification tasks.” These techniques do not work in Orange unless set up as described in the next paragraph.

In the following example, using the diabetes dataset with a prevalence of 15.3% diabetes/ and 84.7% with no diabetes, logistic regression (L1 regularization and balanced class distribution) and the Calibrated Learner widget were applied (check: Sigmoid scaling and Optimize F1 score). The results showed a modest improvement in the F1 score (0.700 from 0.681) when the Calibrated Learner widget was applied. Figure 4.33 displays the Orange workflow, and Table 4.6 displays model performance for logistic regression and logistic regression +Sigmoid + F1.

  
![](images/image-JRQ8KGHS.png)  

Figure 4.33 Orange workflow for Calibrated Learner

  

4.7.2.11 Feature Imbalance

  

While class imbalance has been a known challenge to data prediction evaluation for a long time, a new sub-topic is the issue of feature imbalance. For example, suppose the percentage of females or any other population group in a study is low. The model learns primarily on male instances and is biased against females simply due to their lack of available data. When a model sees a feature with a low-frequency count compared to another, it assumes the feature is unimportant.

What happens to model performance if you add synthetic female subjects such that the number of females = males? You will have to conduct an experiment to determine the impact on model performance. Alternatively, you could use random oversampling with replacement to augment any underrepresented feature. For example, these authors used the heart disease prediction dataset and augmented females with synthetic data resulting in slightly better model performances.⁵⁷ It is early in this area or research so be sure to test whether resampling techniques introduce new model biases or not. Like much of what is written in this chapter, the results may depend on the dataset, preprocessing, the algorithms chosen, and the hyperparameter tuning techniques that have been applied.

The recurrent theme of “it depends” in this book, as well as in numerous other publications addressing strategies to enhance predictive modeling performance, underscores the inherent complexity and context-specific nature of predictive modeling. This seemingly non-specific and non-committal phrase essentially reflects the multidimensional interaction between data characteristics, modeling options, and domain-specific priorities. Therefore, it becomes imperative, especially when high-performance models are a requirement, to adopt a highly disciplined and experimental approach in data science. By systematically designing and executing experiments that test different configurations and methodologies, one can identify the most effective strategies tailored to the particularities of the data and the problem at hand. This experimental mindset not only offers the opportunity to improve model performance but also to gain new insights that will improve future decision-making and build trust with stakeholders.

  

4.7.2.12 Robust Framework for Imbalanced Classification

  

A framework for imbalanced classification refers to a systematic approach or set of guidelines for working with imbalanced datasets in machine learning. This framework was adapted from Jason Brownlee’s eBook “Imbalanced Classification with Python.” ⁵¹ This reference is unique in its comprehensive detail, including the framework to approach imbalanced data in classification datasets. However, the following issues must first be addressed before approaching class imbalance:

1\. Missing data

2\. Outliers

3\. Scaling

4\. Multicollinearity ⁵⁸

  

4.7.2.13 Metric Selection Criteria

  

Decide whether you want to predict exact (crisp) labels (1s and 0s) or actual probabilities. The area under the precision-recall curve (AUPRC) is desirable as an assessment method for class imbalance. To predict class labels, the geometric mean can be calculated. If the minority class is more important, use the F1, F.5, or F2 scores. If you are predicting binary class probabilities, consider the Brier Score. The Brier Score reports the mean squared error between the expected probabilities for the positive class and predicted probabilities. For example, if the prediction of the minority class (1) is 0.80, then the Brier Score is (0.8-1)² = 0.04. An ideal Brier score = 0, whereas the lowest score = 1.⁵⁹ This is not calculated in Orange.

  
![](images/image-OFULF5I0.png)  

Figure 4.34 Decision tree for metric choice for imbalanced classification (modified from Brownlee) ⁵¹

  

The following diagram (Figure 4.34) helps to select the appropriate metrics and plots for imbalanced classification datasets. When you create a machine learning model for binary classification, you can predict class labels (for example, 0,1) or predict class probabilities (for example, a predicted probability of 0.95, will be assigned to the class assignment of 1.0).

  

4.7.2.14 Spot Check Algorithms

  

Spot checking algorithms refers to the process of quickly and objectively evaluating a set of machine learning algorithms on a given problem to determine their performance. First, evaluate algorithms from multiple categories based on the above metrics to establish baseline performance using k-fold cross-validation. Use a baseline algorithm such as the Orange Constant widget. Use several linear algorithms, such as logistic regression and Naive Bayes. Use several nonlinear algorithms such as decision trees, k-NN, neural networks, and SVM. Use several ensemble algorithms such as random forest and xgboost. Second, evaluate data sampling algorithms such as SMOTE. Third, evaluate weighting. Fourth, calibrate probabilities where appropriate with Sigmoid scaling or isotonic regression. Fifth, tune the classification threshold.

  

#### 4.7.3 Hyperparameter Optimization

  

Orange offers various hyperparameter tuning options for its 11 algorithms, as shown in Table 4.6. As seen in the table, the only Orange algorithm that does not have tunable hyperparameter options is the Naive Bayes algorithm. There is no way to know which tuning parameters will improve performance in advance compared to the default setting since the optimal settings may differ for different datasets.

The most common approach to performing hyperparameter optimization (HPO) is grid search and random search, which are not part of Orange.⁶⁰ However, you can set up an Orange workflow with a different widget for each unique hyperparameter you want to test. With this method, you will then be able to see how each HPO setting compares with all other settings, including the default parameter settings, in the Test and Score widget. Each widget in this HPO workflow should be renamed to make it easier to identify in the Test and Score model performance table. Keep in mind that this will add more computing time to your modeling efforts, and it may be wise to only test this on algorithms that appear to be highly ranked for a specific dataset.

BlueSky Statistics offers a limited version of automated HPO for various algorithms in their model fitting section and their model tuning section, separating HPO efforts from the model tuning HPO efforts.

  

#### 4.7.4. Avoiding Model Overfitting

  

Remember that repeated modeling and HPO efforts on the same dataset can lead to overfitting and reduce the model’s capability to generalize well on unseen data. Testing HPO efforts and model experiments on different splits of the dataset can address this issue, but that may not be a good option if you have a relatively small dataset.

The following methods are considered effective in reducing overfitting for all modeling efforts

•Cross-validation: This method splits the data into multiple numbers of subsets of training and testing data and then rotates the subsets until all of the data has a chance to be part of the training and test subset at some point in the process.

•Regularization: This method can add various levels of penalties to the model coefficients to avoid overfitting.

•Feature selection for the modeling: Selecting only the highest-ranked variables for modeling will allow the algorithms to focus on identifying relevant patterns while avoiding the temptation to model irrelevant noise on the model.

•Early stopping: This method limits the time spent on the training process so that it does not overfit the model.

•Train on more data: Training on larger datasets or larger proportions of data in a dataset can improve model performance and reduce overfitting. ⁶¹- ⁶²

  

4.8 PUTTING KNOWLEDGE INTO PRACTICE

  

  

#### 4.8.1 Exercise

  

In this chapter we spent considerable time discussing the significance of imbalanced datasets so this exercise will focus on the handling of imbalanced data. We will use the Framingham dataset that includes 15% of subjects who developed coronary heart disease (CHD) ten years after entering the study.⁶³ This file can be downloaded from our File-Share website. ⁶⁴

  

Table 4.6 Orange Hyperparameter Tuning Options

  
![](images/image-J2PM9SVN.jpg)  

1\. Upload the file into the File widget and open. How many categorical vs numerical columns do you have? Is there missing data? Is the target set to TenYear CHD?

2\. Connect the Feature Statistics and Box Plot widgets to the File widget.

a. Feature Statistics widget - color code by the target. Observations?

b. Box Plot widget - set the upper and lower windows to TenYear CHD. How many are there who developed heart disease in 10 years? Keep TenYear CHD in the lower window but begin to analyze each variable in the upper window. Observations? What variables were statistically different when compared between those who developed heart disease vs those who did not?

3\. The model will likely perform better if you convert the categorical data to numerical and impute missing data.

a. Connect the Preprocess widget to the File widget and open it.

b. Select “Continuize Discrete Variables” and drag to the right window. Select “Most frequent is base.”

c. Select “Impute Missing Values” and drag to the right. Select “Average/Most frequent.”

4\. Connect the Preprocess widget to the Test and Score widget. Connect the latter widget to the Random Forest, Logistic Regression and Gradient Boosting (xgboost) widgets.

5\. Open the Test and Score widget

a. Set the target to 1. Set Cross validation to 10 but experiment with CV=5 to see if that makes a difference

b. Look at the performance metrics for the three algorithms. Why is the specificity and accuracy so high but the F1, precision and recall so low?

6\. Connect the Performance Curve and Calibration widgets to the Test and Score widget. Select target = 1 on the Precision Recall curve. Why might we only look at the F1 and AUPRC scores while we try to improve the imbalance? The MCC is another option but we will focus on F1 and AUPRC.

7\. We will first try weighting algorithms:

a. Before we weight them, take the average of the F1 and AUPRC for the three algorithms and write it down.

b. Open the Random Forest and Logistic Regression widgets and select “Balance class distribution.” Re-calculate the F1 and AUPRC score averages. What improved after weighting the algorithms?

c. Uncheck the weighting boxes.

8\. We will now try “shifting the threshold” to see how it affects model performance.

a. Open the Calibration widget. Be sure target = 1 and chosen Metrics = F1.

b. Move the slider to the left so it centers over the highest F1 score. At a threshold of 0.2 calculate the average F1 and compare it with the average score after weighting. Which method produced the highest F1?

c. When would you use the F0.5 and F 2.0 metrics?

  

#### 4.8.2 Maturity Levels

  

This section offers a view at three organizations that attempt to apply the techniques in this chapter in three levels of sophistication based on their personal organizational maturity level .

Low Maturity Level: A healthcare organization has a dataset of patients who have contracted surgical site infections. They have collected data on five possible predictors from which they want to create a predictive model. The model they plan to run will only include two algorithms from which they will use the best model as their predictive model.

Warning! The assumption that a low-complexity problem exempts you from the analytical rigor of the No Free Lunch Theorem is incorrect. Any shortcuts taken only to test a few of the many algorithms and algorithm options available to you will increase your risk of not discovering the best options to create the highest-performing predictive model.

Moderate Maturity Level: A healthcare organization has a dataset of patients who have contracted surgical site infections. They have collected data on 12 possible predictors from which they want to create a predictive model. The model they plan to run will include eight algorithms from which they will use the best model as their predictive model.

Caution! The assumption that a moderate complexity problem exempts you from the analytical rigor of the No Free Lunch Theorem is incorrect. Although this example explored many different algorithms, it did not explore the many other algorithm options that could lead to a higher-performing predictive model.

High Maturity Level: A healthcare organization has a dataset of patients who have contracted surgical site infections. They have collected data on 25 possible predictors from which they want to create a predictive model. The model they plan to run will include 16 algorithms, algorithm options, and an ensemble model from which they will use the best model as their predictive model.

Congratulations! This team took their high complexity problem seriously. They collected data on as many potential predictors as possible and tested all algorithms and algorithm options at their disposal in their pursuit of the highest-performing predictive model.

  

#### RESOURCES

  

  

1\. Most algorithms are explained well with YouTube videos. This is particularly important for neural networks https://www.youtube.com/watch?v=GQVLl0RqpSs

2\. E-book Master Machine Learning Algorithms. Reviews the 10 most common algorithms. https://machinelearningmastery.com/master-machine-learning-algorithms/

3\. Understanding the Bias-Variance tradeoff https://towardsdatascience.com/understanding-the-bias-variance-tradeoff-165e6942b229

4\. A review of hypothesis testing and comparing the z-test with the t-test. Analytics Vidhya. https://www.analyticsvidhya.com/blog/2020/06/statistics-analytics-hypothesis-testing-z-test-t-test/

5\. The ultimate guide to AdaBoost, Random Forest, and XGBoost. Towards Data Science. https://towardsdatascience.com/the-ultimate-guide-to-adaboost-random-forests-and-xgboost-7f9327061c4f

6\. 11 Data Science Myths You Should Avoid At All Costs https://www.analyticsvidhya.com/blog/2020/09/11-data-science-myths/

7\. Bayes’ Theorem for Medical Tests https://towardsdatascience.com/bayes-theorem-for-medical-test-f1fb12b579c6

8\. What is the difference between a parameter and a hyperparameter? https://machinelearningmastery.com/difference-between-a-parameter-and-a-hyperparameter/

9\. Abulkhair A. So, which ML Algorithm to use?! - Ahmed Abulkhair \[Internet\]. Medium. 2023 \[cited 2023 Jul 17\]. Available from: https://medium.com/@aaabulkhair/so-which-ml-algorithm-to-use-d2484239f448

  

#### REFERENCES

  

  

[1\. Grigorev A. Machine Learning Bootcamp. Manning. 2021 https://www.manning.com/books/machine-learning-bookcamp](#content0102.xhtml)

[2\. Supervised learning. Wikipedia. Available from: https://en.wikipedia.org/wiki/Supervised\_learning](#content0102.xhtml)

[3\. Simplilearn. Bias and Variance in Machine Learning: An In-Depth Explanation \[Internet\]. Simplilearn.com. Simplilearn; 2021 \[cited 2022 Apr 14\]. Available from: https://www.simplilearn.com/tutorials/machine-learning-tutorial/bias-and-variance](#content0103.xhtml)

[4\. Phoenix J. Introduction to the bias-variance tradeoff in machine learning. March 22 2022. \[Internet\]\[cited 2022 May 19\]. Available from: https://understandingdata.com/introduction-to-the-bias-variance-trade-off-in-machine-learning/](#content0104.xhtml)

[5\. Wikipedia contributors. Bias–variance tradeoff \[Internet\]. Wikipedia, The Free Encyclopedia. 2023. Available from: https://en.wikipedia.org/w/index.php?title=Bias%E2%80%93variance\_tradeoff&oldid=1137946549](#content0104.xhtml)

[6\. Hulstaert L. Understanding model predictions with LIME \[Internet\]. Towards Data Science. 2018 \[cited 2023 Feb 19\]. Available from: https://towardsdatascience.com/understanding-model-predictions-with-lime-a582fdff3a3b](#content0105.xhtml)

[7\. What is gradient descent? \[Internet\]. \[cited 2023 Feb 19\]. Available from: https://www.ibm.com/cloud/learn/gradient-descent](#content0106.xhtml)

[8\. What are local minima and global minima in gradient descent? \[Internet\]. i2tutorials. 2019 \[cited 2023 Feb 19\]. Available from: https://www.i2tutorials.com/what-are-local-minima-and-global-minima-in-gradient-descent/](#content0108.xhtml)

[9\. Hyperparameter optimization \[Internet\]. \[cited 2022 Apr 14\]. Available from: https://en.wikipedia.org/wiki/Hyperparameter\_optimization](#content0109.xhtml)

[10\. What is Euclidean distance in terms of machine learning? \[Internet\]. Dr. Sebastian Raschka. 2022 \[cited 2022 Mar 28\]. Available from: https://sebastianraschka.com/faq/docs/euclidean-distance.html](#content0109.xhtml)

[11\. K-Nearest Neighbor(KNN) Algorithm for Machine Learning \[Internet\]. \[cited 2022 Apr 27\]. Available from: https://www.javatpoint.com/k-nearest-neighbor-algorithm-for-machine-learning](#content0109.xhtml)

[12\. Brownlee J. SMOTE for Imbalanced Classification with Python \[Internet\]. Machine Learning Mastery. 2020 \[cited 2022 Apr 14\]. Available from: https://machinelearningmastery.com/smote-oversampling-for-imbalanced-classification/](#content0109.xhtml)

[13\. Band A. How to find the optimal value of K in KNN? \[Internet\]. Towards Data Science. 2020 \[cited 2022 Mar 28\]. Available from: https://towardsdatascience.com/how-to-find-the-optimal-value-of-k-in-knn-35d936e554eb](#content0109.xhtml)

[14\. Chauhan NS. Decision Tree Algorithm, Explained \[Internet\]. KDnuggets. \[cited 2022 Mar 28\]. Available from: https://www.kdnuggets.com/decision-tree-algorithm-explained.html/](#content0109.xhtml)

[15\. Skilltohire . A Beginner’s Guide for Gradient Boosting - skilltohire \[Internet\]. Medium. 2020 \[cited 2022 Mar 30\]. Available from: https://medium.com/@skilltohire/the-beginners-guide-for-gradient-boosting-e5c67584240e](#content0109.xhtml)

[16\. sunil. SVM \[Internet\]. Analytics Vidhya. 2017 \[cited 2022 Mar 30\]. Available from: https://www.analyticsvidhya.com/blog/2017/09/understaing-support-vector-machine-example-code/](#content0109.xhtml)

[17\. What is Linear Regression? \[Internet\]. Statistics Solutions. 2010 \[cited 2022 Apr 21\]. Available from: https://www.statisticssolutions.com/free-resources/directory-of-statistical-analyses/what-is-linear-regression/](#content0109.xhtml)

[18\. Bruce P, Bruce A. Practical Statistics for Data Scientists: 50 Essential Concepts \[Internet\]. “O’Reilly Media, Inc.”; 2017. 318 p. Available from: https://books.google.com/books/about/Practical\_Statistics\_for\_Data\_Scientists.html?hl=&id=JtPTDgAAQBAJ](#content0109.xhtml)

[19\. Boston University https://sphweb.bumc.bu.edu/otlt/MPH-Modules/PH717-QuantCore/PH717-Module9-Correlation-Regression/PH717-Module9-Correlation-Regression7.html](#content0109.xhtml)

[20\. Regularization in machine learning. Simplilearn. \[cited 2022 Mar 28\] Available from: https://www.simplilearn.com/tutorials/machine-learning-tutorial/regularization-in-machine-learning](#content0109.xhtml)

[21\. Sarkar T. False positives/negatives and Bayes rule for COVID-19 testing \[Internet\]. Towards Data Science. 2020 \[cited 2022 Mar 31\]. Available from: https://towardsdatascience.com/false-positives-negatives-and-bayes-rule-for-covid-19-testing-750eaba84acd](#content0109.xhtml)

[22\. Chauhan NS. Naive Bayes Algorithm: Everything You Need to Know. KDNuggets. \[Internet\] \[cited 2022 June 15\] Available from: https://www.kdnuggets.com/2020/06/naive-bayes-algorithm-everything.html](#content0109.xhtml)

[23\. But what is a neural network? | Chapter 1 , Deep learning \[Internet\]. 2017 \[cited 2022 Mar 31\]. Available from: https://www.youtube.com/watch?v=aircAruvnKk](#content0109.xhtml)

[24\. Brownlee J. Essence of Stacking Ensembles for Machine Learning.\[Internet\]\[cited 2022 July 30\]. https://machinelearningmastery.com/essence-of-stacking-ensembles-for-machine-learning/](#content0109.xhtml)

[25\. MLOps. SketchBubble. \[Internet\]\[cited 2022 June 20\]. Available from: https://www.sketchbubble.com/en/presentation-mlops.html](#content0114.xhtml)

[26\. Contributors to Wikimedia projects. All models are wrong \[Internet\]. Wikimedia Foundation, Inc.; 2014 \[cited 2022 Apr 27\]. Available from: https://en.wikipedia.org/wiki/All\_models\_are\_wrong](#content0115.xhtml)

[27\. Siegel E. Models Are Rarely Deployed: An Industry-wide Failure in Machine Learning Leadership \[Internet\]. KDnuggets. \[cited 2022 Apr 27\]. Available from: https://www.kdnuggets.com/models-are-rarely-deployed-an-industry-wide-failure-in-machine-learning-leadership.html/](#content0115.xhtml)

[28\. Futoma J, Simons M, Panch T, Doshi-Velez F, Celi LA. The myth of generalisability in clinical research and machine learning in health care. Lancet Digit Health \[Internet\]. 2020 Sep;2(9):e489–92. Available from: http://dx.doi.org/10.1016/S2589-7500(20)30186-2](#content0115.xhtml)

[29\. Shendre S. Model Drift in Machine Learning \[Internet\]. Towards Data Science. 2020 \[cited 2022 Apr 27\]. Available from: https://towardsdatascience.com/model-drift-in-machine-learning-models-8f7e7413b563](#content0115.xhtml)

[30\. Feng Q, Du M, Zou N, Hu X. Fair Machine Learning in Healthcare: A Review \[Internet\]. arXiv \[cs.LG\]. 2022. Available from: http://arxiv.org/abs/2206.14397](#content0116.xhtml)

[31\. Pastaltzidis I, Dimitriou N, Quezada-Tavarez K, Aidinlis S, Marquenie T, Gurzawska A, et al. Data augmentation for fairness-aware machine learning: Preventing algorithmic bias in law enforcement systems. In: 2022 ACM Conference on Fairness, Accountability, and Transparency. New York, NY, USA: Association for Computing Machinery; 2022. p. 2302–14. (FAccT ’22).](#content0116.xhtml)

[32\. 8 types of data bias that can wreck your machine learning models \[Internet\]. \[cited 2023 Jan 31\]. Available from: https://www.statice.ai/post/data-bias-types](#content0116.xhtml)

[33\. Brownlee, Jason. 2020. “Random Oversampling and Undersampling for Imbalanced Classification.” MachineLearningMastery.com . Machine Learning Mastery. January 14, 2020. https://machinelearningmastery.com/random-oversampling-and-undersampling-for-imbalanced-classification/](#content0117.xhtml)

[34\. “Imbalanced Data.” n.d. Google Developers. Accessed December 7, 2022. https://developers.google.com/machine-learning/data-prep/construct/sampling-splitting/imbalanced-data](#content0117.xhtml)

[35\. “What Is an Imbalanced Dataset? Machine Learning.” n.d. Accessed December 7, 2022. https://www.kaggle.com/getting-started/100018](#content0117.xhtml)

[36\. TRIPOD statement. \[Internet\]\[cited 2022 November 20\] Available from: https://www.tripod-statement.org/](#content0117.xhtml)

[37\. Steen, Doug. 2020. “Precision-Recall Curves.” Medium. September 20, 2020. Available from: https://medium.com/@douglaspsteen/precision-recall-curves-d32e5b290248](#content0117.xhtml)

[38\. Draelos, Rachel. 2019. “Measuring Performance: AUPRC and Average Precision.” Glass Box. March 2, 2019. Available from: https://glassboxmedicine.com/2019/03/02/measuring-performance-auprc/ .](#content0117.xhtml)

[39\. Brownlee J. Precision Recall Curve. Machine Learning Mastery.\[Internet\]\[cited 2022 July 1\]. Available from: https://machinelearningmastery.com/roc-curves-and-precision-recall-curves-for-classification-in-python/](#content0117.xhtml)

[40\. Korstanje, Joos. 2021. “The F1 Score.” Towards Data Science. \[Internet\] \[cited 2022 August 31\] Available from: https://towardsdatascience.com/the-f1-score-bec2bbc38aa6 .](#content0117.xhtml)

[41\. Brownlee J. Machine Learning Mastery. A Gentle Introduction to the Fbeta-Measure for Machine Learning. Available from: https://machinelearningmastery.com/fbeta-measure-for-machine-learning/#:~:](#content0117.xhtml)

[42\. Chicco, Davide, and Giuseppe Jurman. 2020. “The Advantages of the Matthews Correlation Coefficient (MCC) over F1 Score and Accuracy in Binary Classification Evaluation.” BMC Genomics 21 (1): 6.](#content0117.xhtml)

[43\. Matthews Correlation Coefficient Calculator. \[Internet\]\[cited 2022 June 3\] Available from: https://www.omnicalculator.com/statistics/matthews-correlation-coefficient](#content0117.xhtml)

[44\. Singh, Kamaldeep. 2020. “How to Improve Class Imbalance Using Class Weights in Machine Learning.” Analytics Vidhya. October 6, 2020. \[Internet\]\[cited 2022 October 20\]. Available from: https://www.analyticsvidhya.com/blog/2020/10/improve-class-imbalance-class-weights/](#content0117.xhtml)

[45\. Brownlee, Jason. 2020. “Cost-Sensitive Logistic Regression for Imbalanced Classification.” MachineLearningMastery.com . Machine Learning Mastery. January 26, 2020.\[Internet\]\[cited 2022 October 20\] Available from: https://machinelearningmastery.com/cost-sensitive-logistic-regression/](#content0117.xhtml)

[46\. Undersampling and oversampling: An old and a new approach. \[Internet\]\[cited 2022 November 25\] Available from: https://medium.com/analytics-vidhya/undersampling-and-oversampling-an-old-and-a-new-approach-4f984a0e8392](#content0117.xhtml)

[47\. Chawla, N. V., Bowyer, K. W., Hall, L. O., & Kegelmeyer, W. P. (2002). SMOTE: Synthetic minority oversampling technique. Journal of Artificial Intelligent Research, 16, 321-357](#content0117.xhtml)

[48\. SMOTE.\[Internet\]\[cited 2022 October 5\] Available from https://www.researchgate.net/publication/287601878/figure/fig1/AS:1089045727846455@1636660143492/A-sample-with-two-classes.jpg](#content0117.xhtml)

[49\. Elreedy D, Atiya AF. A Comprehensive Analysis of Synthetic Minority Oversampling Technique (SMOTE) for handling class imbalance. Inf Sci. 2019 Dec 1;505:32–64](#content0117.xhtml)

[50\. Nguyen, Hien M., Eric W. Cooper, and Katsuari Kamei. 2011. “Borderline Over-Sampling for Imbalanced Data Classification.” International Journal of Knowledge Engineering and Soft Data Paradigms 3 (1): 4–21.](#content0117.xhtml)

[51\. Brownlee J. Imbalanced Classification with Python. Choose Better Metrics, Balance Skewed Classes and Apply Cost-Sensitive Learning. 2020. \[Internet\]\[cited 2022 May 20\] Available from: https://machinelearningmastery.com/imbalanced-classification-with-python/](#content0117.xhtml)

[52\. Synthetic Data To Solve Imbalanced Classification. Kaggle. \[Internet\]\[cited 2022 October 24\] Available from: https://www.kaggle.com/code/akshaysharma001/synthetic-data-to-solve-imbalanced-classification](#content0117.xhtml)

[53\. Mostly.ai.\[Internet\]\[cited 2022 October 25\] Available from. https://mostly.ai](#content0117.xhtml)

[54\. Brownlee J. How to Combine oversampling and Undersampling for imbalanced classification. Online Machine \[Internet\]. 2020; Available from: https://machinelearningmastery.com/combine-oversampling-and-undersampling-for-imbalanced-classification/](#content0117.xhtml)

[55\. Aprilliant A. Optimal Threshold for Imbalanced Classification \[Internet\]. Towards Data Science. 2021 \[cited 2022 Apr 16\]. Available from: https://towardsdatascience.com/optimal-threshold-for-imbalanced-classification-5884e870c293](#content0117.xhtml)

[56\. FastML. Classifier Calibration with plats scaling and isotonic regression.\[Internet\]\[cited 2022 November 15\] Available from: http://fastml.com/classifier-calibration-with-platts-scaling-and-isotonic-regression/](#content0117.xhtml)

[57\. Watson A. Reducing AI bias with Synthetic data \[Internet\]. Towards Data Science. 2020 \[cited 2023 Jan 18\]. Available from: https://towardsdatascience.com/reducing-ai-bias-with-synthetic-data-7bddc39f290d](#content0117.xhtml)

[58\. Sundus, Katrina I., Bassam H. Hammo, Mohammad B. Al-Zoubi, and Amal Al-Omari. 2022. “Solving the Multicollinearity Problem to Improve the Stability of Machine Learning Algorithms Applied to a Fully Annotated Breast Cancer Dataset.” Informatics in Medicine Unlocked 33 (January): 101088.](#content0117.xhtml)

[59\. Brier Score and Model Calibration. Neptune AI. \[Internet\]\[cited 2022 November 2\] Available from: https://neptune.ai/blog/brier-score-and-model-calibration](#content0117.xhtml)

[60\. Brownlee J. Hyperparameter Optimization With Random Search and Grid Search \[Internet\]. MachineLearningMastery.com . Machine Learning Mastery; 2020 \[cited 2023 Mar 1\]. Available from: https://machinelearningmastery.com/hyperparameter-optimization-with-random-search-and-grid-search/](#content0118.xhtml)

[61\. 7 Simple Techniques to Prevent Overfitting \[Internet\]. \[cited 2023 May 30\]. Available from: https://www.kaggle.com/getting-started/157623](#content0119.xhtml)

[62\. EliteDataScience. Overfitting in machine learning: What it is and how to prevent it \[Internet\]. EliteDataScience. 2017 \[cited 2023 May 30\]. Available from: https://elitedatascience.com/overfitting-in-machine-learning](#content0119.xhtml)

[63\. Bhardwaj A. Framingham heart study dataset \[Internet\]. 2022 \[cited 2023 Aug 17\]. Available from: https://www.kaggle.com/datasets/aasheesh200/framingham-heart-study-dataset](#content0121.xhtml)

[64\. File-Share. Chapter 4 Folder. https://www.nocodedatascience.net/file-share](#content0121.xhtml)

  

![](images/image-LN67R7II.jpg)Chapter 5

  

## Model Evaluation

  

“Data is a precious thing and will last longer than the systems themselves.”

—Tim Berners-Lee

  
![](images/image-M6MTZISG.jpg)  
  

LEARNING OBJECTIVES

  
  

By the end of chapter five readers should be able to:

•Compare and contrast internal vs external model validation.

•Enumerate the shortcomings of classification accuracy.

•Discuss how the receiver operator curve is created and the importance of thresholds.

•Discuss model evaluation metrics for classification and regression models.

•Discuss methods that help to explain models

•Discuss model discrimination and model calibration.

•Understand the basics of hypothesis testing

•Understand the concepts of model drift

  
  

Chapter 5 Summary

  

  

In this chapter we will discuss how to evaluate the model you created. We will first discuss model validation which tests the model performance on data it has not seen yet. We will also explain various model performance metrics, model discrimination, calibration, the confusion matrix, model explainability techniques, hypothesis testing, model drift, concept drift, and model retraining. We will provide a thorough review of all major Orange widgets pertinent to model evaluation. There are journals now that mandate authors post the confusion matrix, along with sharing their datasets and any code generated for any proposed papers under review for publication. Internal subject matter experts play an important role in determining whether sensitivity, precision, and/or specificity are most important in a predictive model as they make their final decisions of which model has the best performance.

  

Key principles:

•In general, internal validation may provide overly optimistic results.

•A model evaluated on external validation presents the biggest generalization challenges for a trained model.

•Do not perform pre-processing of data (e.g., imputation) before the train/test split as that will lead to data leakage or “peeking,” which means that the training data is actually learning from the test data.

•Data leakage in a model refers to any hints that will give the training data of what the future data looks like that this model is supposed to predict.

•Model scorecard metric matrices in the Test and Score Widget and several model evaluation tables and charts (e.g., Confusion Matrix and Calibration plot) should be used together to provide a thorough assessment of a model’s performance.

•Good model discrimination does not guarantee good model calibration.

•Apply several model explanation techniques to engage in collaborative conversations with stakeholders.

•Statistics and hypothesis testing can add an additional layer of beneficial analysis to model evaluation activities.

  

  

5.1 MODEL VALIDATION

  

  

Once you have created a model with several algorithms you need to evaluate the performance of that model. Before we discuss the Orange evaluation widgets, we should discuss model validation which means, in the simplest of terms, confirming that the model is generalizable when it is tested on new data it has not seen before. In Orange, we will frequently use the Data Sampler widget to split the data into train data and test data. The default is a 70/30 (train/test) split. Seasoned data analysts will sometimes use a third dataset referred to as a validation dataset when they are adjusting the algorithms (hyperparameter optimization or HPO) to determine the results. This is only advisable for larger datasets. Keep in mind that the terms test and validation datasets are often used interchangeably, which is incorrect. Jason Brownlee defines these datasets as follows:

•Training Dataset : “The sample of data used to fit (train) the model.”

•Validation Dataset : “The sample of data used to provide an unbiased evaluation of a model fit on the training dataset while tuning model hyperparameters. The evaluation becomes more biased as skill on the validation dataset is incorporated into the model configuration.”

•Test Dataset : “The sample of data used to provide an unbiased evaluation of a final model fit on the training dataset.” ¹

The following are the general approaches to model validation.

  

#### 5.1.1 Internal Validation (IV)

  

Internal validation means you are training and testing on the same dataset. There are several methods available:

a. Train/test split. By convention, roughly 70% of the data is used for training and the remainder is held out for testing. Occasionally, there is a third small dataset called the validation dataset that is used solely to tune the hyperparameters of the algorithms, so the split might be 60/20/20. With small datasets, the problem then is the test dataset might be extremely small so the results may show poor performance.

  

  

KEYPOINT: In general, internal validation may provide overly optimistic results.

  

  

  

KEYPOINT: Do not perform pre-processing of data (e.g., imputation, normalizations, etc.) before the train/test split as that will lead to data leakage or “peeking”, which means that the training data is actually learning from the test data.

  

  

b. k-fold cross-validation. For small datasets, many software packages offer k- fold cross-validation solely to both train and test on the same dataset. k can be set from 1-20 in Orange but it is common to use 5 to 10 folds. ² Smaller datasets may work better with smaller k numbers. As always, experiments can be used to determine the best number of folds to use. A small number of folds can lead to high bias while a large number of folds can lead to high variance. ³

  
![](images/image-K0MGDWAQ.png)  

Figure 5.1 K-fold cross-validation (courtesy sci-kit learn.org)

  

c. k-fold cross-validation has the advantage that all of the data will be consecutively used for training and testing at the end of the cross-validation. When k=10 is chosen, the data is divided into 10 folds, where you train on 9 and test on one. This process is repeated k times so that each subset of the data has the chance to be used only one time as the validation data set. It then averages the performance on the 10 folds which is reported as the model performance. The stratified cross-validation option means that the percentage of the classes stays the same in the train and validation folds. For example, if cancer is the minority class and comprises 30% of the total patients reported, then the stratified folds will have 30% cancer patients in each fold. This is recommended, particularly for small datasets. Cross-validation can typically be repeated multiple times as well but that is not an option in Orange. In the k-5 cross-validation seen in Figure 5.1 , you train on four folds and test on the fifth which is a process that is repeated k times. The average results are then used as the overall training performance.

  
![](images/image-VSHRSNH8.png)  

cross-validation (StatQuest)

  

d. Leave one out cross-validation (LOOCV). In this case, you leave out one data point and train on all of the others then select another one and train on the remaining data. For example, you have 500 subjects. You train on subjects 1-499 and test on subject 500. Next, you train on subjects 2-500 and validate on subject 1. This process is repeated until each data point has the opportunity to be used for validation. This method is an extreme case of cross-validation. It offers an unbiased approach to cross-validation and is useful for small datasets. This method is obviously time intensive.

e. Bootstrapping is a resampling technique that involves randomly sampling the original dataset with replacement. Each data point has the chance of being chosen multiple times for the sample. See Figure 5.2

  

#### 5.1.2 External Validation (EV)

  

EV means evaluating the model on data not part of the original data. It can be derived as follows:

•Data from a different location i.e. from a different factory, customer base, healthcare system, or with data from a different part of the country

•Data from different demographic, socioeconomic, racial, and/or ethnic groups

•Data from a different time period

  

  

KEYPOINT:A model evaluated on external validation presents the biggest generalization challenges for a trained model. This challenge arises due to the potential differences between the training/validation data and the external validation data, such as variations in distribution, noise, or previously unseen patterns. Overfitting and underfitting are common issues that can hinder a model’s generalization performance that can be countered with regularization and various forms of cross-validation.

  

  
![](images/image-KUPTOS2O.jpg)  

Figure 5.2 Bootstrapping

  

#### 5.1.3 Optimal Validation (OV)

  

It is recommended that you first split the data into train/test using the Data Sampler widget in Orange. The default in Orange is a 70/30 split. When you use the Test and Score widget, you have the option to run k-fold cross-validation to determine the performance of the training data. You will later determine the performance on the test data. If the training performance is much better than the test data, you have overfitting which means that the training data did a great job at understanding its own pattern, but it could not project those learnings onto unseen test data. Ideally, you would try to find external data as well to test. Be aware that there is always the possibility that the external data may have subtle differences that will influence the model results. Also, creating a prospective study to confirm that the model works as deployed would be ideal. Some programs generate confidence intervals for the AUC, but Orange does not.

  

#### 5.1.4 Further Validation Guidance

  

Model validation causes confusion for several reasons. For example, the validation mode you choose depends on the dataset size. The following provides some further guidance:

•If the dataset is large (several thousand rows) it is prudent to split it into train and test because the test dataset is large enough to see how the model will perform when confronted with a large amount of unseen data. This allows you to compare training with test results to see if there is over or under-fitting. In Orange, use the Data Sampler widget, or you could set up dual input files - train data and test data.

•If the dataset is small (several hundred rows or less) using k-fold or leave one out cross-validation and no data split will provide you with good ballpark results, but it may be a little optimistic. The cross-validation is not the reason for the possible optimism of the model for small datasets. When the dataset is small, the model may have a higher chance of overfitting, meaning it learns the noise and idiosyncrasies in the training data rather than the true underlying patterns. ⁴

•Be aware of the fact that the choice between cross-validation and a 70/30 split is a matter of debate in the machine learning community. Use experiments to determine the best option for your specific dataset. ⁵

  

5.2 MODEL DISCRIMINATION AND CALIBRATION

  

  

Model discrimination means how well the model discriminates between the two classes in binary classification. The standard measure is the area under the receiver operator curve (AUC or AUROC). Figure 5.3 displays model discrimination based on the ROC for test data from the heart disease prediction dataset using logistic regression. The AUC = 0.866. Recall that binary classification is based on the arbitrary threshold of 0.5. If the predicted probability is greater than 0.5 it will be labeled as 1, whereas if the predicted probability is less than 0.5, it is labeled as 0. As explained in Chapter 4 and later in this chapter, the threshold can be moved to gain better results.

Model calibration measures how close the prediction probability is to the actual result. Calibration is very important when you use probability algorithms, such as logistic regression or Naive Bayes. If you predict the risk of heart disease is 80%, how often was this proven true? Model calibration is rarely reported in the literature, unlike discrimination.

  

  

KEYPOINT: Unfortunately, good model discrimination does not automatically guarantee good model calibration. Discrimination and calibration are distinct aspects of model performance, with discrimination focusing on separating classes and calibration assessing the accuracy of risk predictions. Both discrimination and calibration should be evaluated to obtain a comprehensive understanding of a model’s performance and reliability. While discrimination is the most commonly used measure of how well a predictive model performs, calibration of estimates is also important. Poor calibration can lead to misleading predictions and impact the reliability of decision-making processes.

  

  

Model discrimination generally refers to binary classification where you only have two choices, 0 and 1. There is no gray zone, and at times this does not make sense. For example, most evaluations of echocardiograms fall into three categories: abnormal, borderline, and normal. Banks might classify the creditworthiness of individuals as high, low, and borderline risk. Online product reviews may be rated as positive, negative, and neutral. There are times when classification should be based on multiple classes and other times the output should not use a threshold but should use the raw number where regression would be a more reasonable analysis method when raw numbers are used. A “threshold” is the cutoff point where a “zero” is automatically classified as a “one” when the probability of that event exceeds the threshold value. 0.5 is the default threshold meaning that a probability of 0.499 is considered a zero but a probability of 0.501 is considered as a one. As previously mentioned, these cutoff points (thresholds) offer no gray zone since a binary class membership is forced upon each data point based on the threshold cutoff point. Model discrimination and calibration are calculated differently hence they may not agree.

  
![](images/image-96G9IMPJ.png)  

Figure 5.3 The ROC curve

  

Many experts recommend reporting calibration, referred to as the “Achilles Heel of predictive analytics.” ⁶ Model calibration can be defined as how well a model predicts the true events that it is tasked to predict. Calibration that is far off might give misleading results to patients and clinicians. Other examples of poor calibration can be inaccurate speedometers on vehicles, inaccurate air and water quality measurements, student grading rubrics that are either too harsh or too generous, inaccurate soil pH level readings, and many others. Readers are referred to these references for more information about calibration. ⁷-⁸

In Orange you can connect the Prediction widget to the Test and Score widget and see the prediction for each patient. You can also connect the Calibration Plot widget to the Test and Score widget to display calibration, based on the Prediction widget. A perfect prediction would fall on a 45-degree line as shown in Figure 5.4. In this example, the logistic regression model is well-calibrated. In other words, if the predicted risk of heart disease is 0.95 and the patient has heart disease (1) then the calibration is very close. We will discuss the prediction and calibration widgets in another section. Note: the Brier Score and the Hosmer-Lemeshow tests are also model calibration tests, but not offered in Orange.

[Fig 5.5 displays the distribution of the prediction probabilities. Note that while most of the data points are close to 0 and 1 there are many between 0.2 and 0.8. We clearly see here that the threshold value of 0.5 is the border between 0 and 1 classifications. The more prediction probabilities that pile up at the border between 0 and 1, the less robust the predictive model becomes.](#content0131.xhtml)

  
![](images/image-3ZL8OEQQ.jpg)  

Figure 5.4 Calibration curve for logistic regression on the heart disease prediction dataset

  
![](images/image-W5GTF4DQ.png)  

Figure 5.5 Distribution of the prediction probabilities for a binary class

  

The following are some reasons why model discrimination and calibration may be discordant:

•There is significant model overfitting, such that the model is training on noise and not the signal.

•Class imbalance, such that the model is training primarily on the majority class.

To improve model calibration there are two options offered in Orange. Using the Calibrated Learner widget you can select sigmoid or isotonic calibration. In the widget you have three other choices: optimize accuracy, optimize F1 score, or no threshold optimization. In the example below, a breast cancer classification model has been created, with logistic regression as the algorithm. In the Calibrated Learner widget, sigmoid calibration and optimize F1 score has been selected. Figure 5.6 shows the workflow and Figure 5.7 demonstrates improvement in the F1 score after calibration. The results were similar with isotonic calibration. The calibration plot did not substantially change.

  

5.3 PROBABILITY, ODDS, ODDS RATIOS AND LOG ODDS RATIOS

  

  

#### 5.3.1 Probability vs Odds

  

Probability, odds ratios, and log odds are all related but expressed in different ways. Probabilities and odds reflect the chance of some event happening or not. They are both ratios, but probabilities are relative to the total number of observations, whereas odds are relative to the number of events that did not occur.

Probability is the probability an event will happen. It is the ratio of cases to the total of all possible cases. For example, if 30 people died after being hit by lightning but 90 did not, the probability of dying is 30/120 or 25% or 0.25. Probabilities range from 0 to 1.0.

Odds are the probability that an event will happen divided by the probability the event won’t happen. Therefore, the odds of dying from lightning is 30/90 or 1 in 3. Odds = (p/1-p) where p = probability. Using the lightning example 0.25/0.75 1 in 3. To convert odds to probability, use the formula p = odds/1 + odds or .33/1+ .33 = 0.25. ⁹

  

#### 5.3.2 Odds Ratios and Log Odds Ratios

  

Odds is a simple ratio of two numbers, whereas odds ratios are the ratio of two odds, hence four numbers as you will see in the following example.

The odds ratio (OR) has traditionally been used in case-control studies to measure exposure to e.g., a toxin in those who developed cancer and those who did not or the odds of dying in a severe car accident when the seat belt is not used. In the table below we have data that shows a hypothetical scenario with exposure to Roundup™ (glyphosate) and cancer cases.

  
![](images/image-PJOH5M6Z.png)  

Figure 5.6 Calibrated Learner workflow in Orange

  
![](images/image-NMWD1CHT.png)  

Figure 5.7 Results after sigmoid calibration

  

Table 5.1 Hypothetical scenario of cancer-related to Roundup exposure

  

 
|  || Exposed Yes || Exposed No |
| --- | --- | --- |
| Cancer Yes || 17 || 1 |
| Cancer No || 83 || 99 |

  

The odds ratio of the exposed group = exposed with cancer/exposed without cancer = 17/83 = 0.205

The odds ratio of the not exposed group = not exposed with cancer/not exposed without cancer = 1/99 = 0.01

The odds ratio (OR) = 0.205/0.01 = 20.5. Therefore, the odds of developing cancer after exposure is about 20 times higher than if not exposed. Ideally, the confidence intervals (CI) should be calculated. In this case, the 95% CIs are \[2.7, 158\]. Remember, if the confidence interval includes 1, then the results are inconclusive, e.g., \[0.1, 10\] spans 1.

The OR quantifies the degree of association between categorical groups, whereas a chi-square test determines if there is a statistically significant association between categorical groups. Relative risk (RR) ratios are similar, but the probability is substituted for odds in the otherwise same formula.¹⁰

Log odds are the logarithm of the odds. For example, the natural log (base e) for the odds ratio of 20.5 we calculated above is Ln(20.5) = 3.0. Conversion to log odds results in symmetry around zero (a more normal distribution), which is easier for analysis because you can visualize both positive and negative numbers, as seen in Figure 5.8. A positive value means there is a positive relationship between the predictor and the outcome; the opposite is true for negative log odds.

We can also write the log odds also as log \[p/(1-p)\] Where:

p = the probability of an event happening

1 – p = the probability of an event not happening

When a function’s variable represents a probability (p) it’s called the logit function, and this is what we use with logistic regression. (log \[p/((1-p\]). Binary logistic regression models the relationship between a set of independent variables (numeric and categorical) and a binary dependent variable, such as died vs survived. Binary logistic regression models a dependent variable as a logit of p, where p is the probability that the dependent variables take a value of 1. ¹¹

Using the heart disease prediction dataset, the formula for logistic regression is as follows: (p is the probability of the dependent variable is 1 having heart disease). log(p/1-p) = bo(intercept) + b1X + b2X……….b10X

Note that b is a coefficient and x is an independent variable, as in this example:

  
![](images/image-GPWRQ39D.jpg)  

Figure 5.8 Logistic regression coefficients and calculated odds ratios

  

log(p/1-p) = -2.66 (intercept) + -.014 (age) + -0.74 female)........b10

  

The logistic regression coefficient β associated with an independent variable (predictor) x is the expected change in log odds of having the outcome per unit change of x. Therefore, increasing the predictor by 1 unit (or going from 1 level to the next) multiplies the odds of having the outcome by eβ (log e B). Figure 5.8 shows the logistic regression coefficients obtained in Orange with the odds ratios manually calculated. To visualize these coefficients, connect a Data Table widget to the Logistic Regression widget.

To calculate the odds ratios from log odds you simply calculate the antilog. For example, in Figure 5.8 logistic regression coefficients are displayed which are log odds. To calculate the odds ratios using the natural log (base e), the odds ratio of -0.74 is 0.47. In other words, e coefficient = odds ratio. In this example, e -.74 = 0.47. This means the female gender has 53% decreased odds of having heart disease.¹²

Interpreting OR values:

•Normal thallium test OR = 0.63 or there is 37% reduced odds of having heart disease

•Reversible thallium OR = 2.32 or there is 2.32 times the odds of having heart disease

•Male gender OR = 2.0 or twice the odds of having heart disease

•ST depression OR = 1.45 or 1.45 times the odds of heart disease or 45% increase.

  
![](images/image-P89VZO4P.png)  

Odds and Log Odds (StatQuest)

  

#### 5.3.3 Diagnostic Tests and Likelihood Ratios

  

As the calculation for PPV (positive predictive value) and NPV (negative predictive value) includes individuals with and without the disease, it is affected by the prevalence of the disease in question. PPV increases when prevalence increases, whereas NPV decreases. Therefore, you must ensure that the same population is used (or the incidence of the disease is the same between the populations) when comparing PPV and NPV for different tests. This limitation has given rise to calculating the positive likelihood (LR+) ratio and negative likelihood (LR-) ratios.

•LR+ is the probability that a person with the disease tested positive for the disease (true positive) divided by the probability that a person without the disease tested positive for the disease (false positive).

•LR- is the probability that a person with the disease tested negative for the disease (false negative) divided by the probability that a person without the disease tested negative for the disease (true negative).

Formulas are based on sensitivity and specificity and are as follows:

•LR + = sensitivity/1- specificity

•LR - = 1- sensitivity/specificity.

Therefore, LR + helps to rule in disease, whereas LR - helps to rule out disease, but both sensitivity and specificity are involved. An LR close to 1 means that the test result does not change the likelihood of disease, or the outcome of interest significantly. The greater the LR+ is, the more likely the disease or outcome. The lower the LR- is, the less likely the disease or outcome. General rules of thumb:

•Weak impact: +LR between 1-3 or a -LR between 1-0.3

•Moderate impact: +LR between 3-10 or a -LR between 0.3-0.10

•Strong impact: +LR >10 or a -LR <0.10

Example: in this actual medical study there were 280 patients in total, and 180 had ovarian cancer. All had surgery with biopsies and had a diagnostic ultrasound, CT, and MRI studies. The confusion matrix below (Table 5.2) is for CT studies looking for peritoneal metastases. The confusion matrix was populated from the sensitivities and specificity percentages.

  

Table 5.2 CT scan study of patients with and without peritoneal metastases

  
![](images/image-ZKB7XU5H.jpg)  

Sensitivity = 92%

Specificity = 81%

LR + = 4.85 95% CIs \[3.6,6.9\]

LR - = 0.1 95% CIs \[0.038,3.2\]

This means that the probability that a person with ovarian cancer had a positive CT scan is 4.85 times higher compared to patients without cancer who tested positive by CT scan for cancer. The LR - is inconclusive because the confidence intervals cross 1.¹³

Using Bayes’ theorem, the prevalence acts as the pre-test probability of the disease likelihood, and combined with the likelihood ratios a post-test probability can be calculated.

The above-mentioned analysis techniques can be used in any industry. Some examples are listed below:

•The assessment of manufactured products and components

•Environmental monitoring

•Market research to evaluate customer preferences and behavior

•Assessing the quality and reliability of software applications

•Customer retention analysis

•Customer satisfaction analysis in the hospitality industry

•Detecting fraudulent activities in banking transactions

•Assessing the quality of services in the telecommunications sector

This reference will take you to an online diagnostic test calculator by Alan Schwartz. ¹⁴ There are multiple similar online and smartphone apps for this same calculation. Simply input the TP, FP, TN, and FN values and it calculates the sensitivity, specificity, and likelihood ratios. Depending on the prevalence in your population, and the LR + and LR-, the post-test probabilities will change on the nomogram. The nomogram assumed a prevalence of 0.64 (64%) in this population but this is the study population and not the general population. Given the high prevalence and using LR+, the post-test probability increases from 64% to 90%. With a lower prevalence of 10% and the same LR + of 4.85, the post-test probability is 35%. If the prevalence of disease is low in your population, then a positive test is more likely to be a false positive. Conversely, if the pre-test probability is very high, a negative test does not rule out disease.

In the resource section there is a link to an important article on Bayes Theorem and how that helps to understand disease prediction and screening tests. The decision of how many false negatives and false positives are acceptable is left to business leaders and subject matter experts. Figure 5.9 displays the results of the online calculator.

In JASP there is a Learn Bayes module that includes binary classification. You can set the prevalence, sensitivity, and specificity and see the results in a plot. For the default model (COVID) the prevalence is 10% and the specificity and sensitivity are both 80% (0.80). Figure 5.10 shows a probability plot. This means that the post-test probability of a positive test in this population is about 31% in those people tested. This is because the positive predictive value (precision) is only 30.8%.

  

5.4 ORANGE MODEL EVALUATION WIDGETS

  

  

[Figure 5.11 provides a visual representation of our current position within the 8-step DISCOVER process. At this stage, we find ourselves in the sixth phase, named: “Verify model performance with various model evaluation methods.” This chapter will delve into the intricacies of this step, specifically shedding light on diverse model evaluation methods and performance metrics.](#content0137.xhtml)

  
![](images/image-8MF604KB.png)  

Figure 5.9 Online calculation of likelihood ratios and pre and post-test probabilities ¹⁴

  
![](images/image-OFGUR4SL.png)  

Figure 5.10 Post-test positive predictive value

  

#### 5.4.1 Test and Score Widget

  

•This widget is used to record model performance for classification and regression models.

•First, select the validation method that is used to help train the model for larger datasets after you have split the data into training and test datasets with the help of the Data Sampler widget. For smaller datasets you may not have the luxury to split your dataset into training and test datasets. In such situations, k-fold or leave one out cross validation is used instead of splitting the data into dedicated train/validation and test datasets. We suggest the application of k-5 fold CV with the stratified option for smaller datasets, as a general guideline, and k-10 fold CV for larger datasets with experiments to guide your final decisions. See Figure 5.12 for an example workflow for a smaller dataset.

•Select the target class, which in this situation, we are most interested in 1 or the presence of heart disease if we are using the heart disease prediction dataset. Alternatively, you can also predict the absence of heart disease (0) or determine the weighted average of the two classes since Orange offers the option to select the “average over classes.” Use this option if you are equally interested in all classes or scenarios. An example of this last option may be when researchers are equally interested in predicting all types of tumors (benign, malignant, or premalignant). Keep in mind that in this last example the metric values are calculated as averages with weights based on the class size.

•The Test and Score widget generates the AUC, Classification accuracy (ca), F1, Precision, Recall, MCC, Log Loss, and Specificity. Right-click “Model” to add LogLoss and Specificity. For regression, the widget generates MSE, RMSE, MAE, and R ² . We will define classification and regression performance measures further in this chapter and the chapter on supervised learning.

•The lower part of the Test and Score widget window can provide probabilities that one algorithm is superior to another when multiple algorithms are compared against each other. For binary classification, most people compare the AUC, in addition to the other performance measures. See Figure 5.13 for an example where the logistic regression learner had a 0.996 probability of having higher classification accuracy than the random forest learner and a 0.987 probability of having higher classification accuracy than the SVM learner.

  
![](images/image-83QBHE74.jpg)  

Figure 5.11 Step six in the Data Science DISCOVER process

  

•You would typically connect this widget to other widgets, such as the ROC, Confusion Matr ix, Calibration plot, and Predictions widgets.

•To view just the training data performance of a model in the Test and Score widget, select cross-validation with the stratified option when the data has been segmented into training and test datasets with the help of the Data Sampler widget. Figure 5.14 shows the associated workflow and connector settings between the Data Sampler and Test and Score widgets required to achieve this task for a 70/30 data split for training and test data.

•To view just the test data performance of a model in the Test and Score widget, select “test on test data” in the Test and Score widget and change the connector links to use the 30% of the data (remaining data) for the test data, as shown in Figure 5.15 .

  
![](images/image-ZVP8AWOG.jpg)  

Figure 5.12 Orange workflow for smaller datasets with no data splits

  
![](images/image-ASL57Z80.jpg)  

Figure 5.13 Test and score widget for cross validation and target = 1

  
![](images/image-GET6CCM7.jpg)  

Figure 5.14Workflow to produce Training / Validation results in the Test and Score widget

  

#### 5.4.2 Predictions Widget

  

This widget generates the prediction probabilities for each class, each row (patient), and for each algorithm selected. This widget is important in order to generate the calibration plot that compares the outcome of the classifier (1,0) with the prediction probability. In Figure 5.16 logistic regression was used to determine the prediction probabilities for the first 5 patients seen (the others are not visible). For example, for the first patient labeled as 1, the probability is 0.96, whereas the probability for the second patient classified as 0 is 0.18. In other words, the predicted probabilities are not perfect, just close. When you compare all data points, you can create a calibration plot which will be presented in another section. At the bottom of the prediction widget are the same performance scores reported by the Test and Score widget but they are not shown in Figure 5.16.

  
![](images/image-JW7S67DJ.jpg)  

Figure 5.15 Workflow to produce Test results in the Test and Score widget

  

To create this prediction workflow, you must first divide the data into train and test data using the Data Sampler widget as demonstrated in Figure 5.17. Connect the training data to logistic regression; then connect the Data Sampler widget to the Predictions widget, but remember to right-click on the link between these two widgets and connect the “remaining data to test data” in the “edit links” dialogue box. Traditionally, predictions are based on test results. In the Predictions widget check the “Show performance scores” so you can see the classification model results.

Alternately, as demonstrated in the Predictions widget’s Help menu, you can train a model on a dataset, then connect new subjects to the Predictions widget and it will give individual predictions for these subjects. For example, you train the model to predict heart disease and then you upload 5 new patients with the same predictor variables and it will make heart disease predictions on each subject.

  
![](images/image-SGYGDZ9E.png)  

Figure 5.16 Prediction widget results

  
![](images/image-WOKBEQQP.jpg)  

Figure 5.17 Workflow for test predictions

  

#### 5.4.3 Confusion Matrix

  

This widget is the matrix (also called a truth table and error matrix) that displays data broken down into actual vs the predicted values for the chosen model. In this scenario, actual (ground truth = TN and TP) is based on cardiac catheterization. The errors in the matrix are shown as FP and FN. Figure 5.18 is a generic representation of a confusion matrix and Figure 5.19 is the Orange confusion matrix for the heart disease prediction dataset using logistic regression (LR). While binary classification generates a 2 x 2 table, you can have multinomial classification which requires e.g., a 3 x 3 or larger table which Orange will automatically create when needed. Also, each confusion matrix result is specific for the algorithm run as it displays its ability to make true predictions (TN and TP) as well as false predictions (FP and FN). This matrix is called a “confusion” matrix since it displays how often a model is confused about the correct classification of the data into the four possible classification choices (TP, TN, FP, and FN). When the confusion matrix shows model results that are undesirable (too many false classifications), the analyst should carefully review the model, its chosen features, the algorithm chosen, and other available modeling options that should be experimented with to achieve a better-performing model.

  
![](images/image-JYH03IPM.png)  

Figure 5.18 Generic confusion matrix

  
![](images/image-X7O6DF23.png)  

Confusion Matrix (StatQuest)

  

[Table 5.3 lists some of the different metrics you can derive from the confusion matrix.](#content0139.xhtml)

Based on the Orange confusion matrix in Figure 5.19 on heart disease prediction, the following can be calculated:

a. True positive = 73

b. True negative (specificity) = 100

c. False positive = 17 or those predicted to have heart disease who didn’t. Also known as a Type I error.

d. False positive rate = FP/FP + TN = 0.145 or 14.5% (same as 1-specificity).

e. False negative = 23 or those predicted to not have heart disease who actually did. Also known as a Type II error.

f. Recall (sensitivity)(true positive rate) = TP/TP + FN = 0.76. Remember that sensitivity. includes FN in the denominator, so sensitivity drops with more false negatives.

  
![](images/image-HW5F5MX4.png)  

Figure 5.19 Confusion matrix for LR in Orange on training data

  

Table 5.3 Classification model evaluation metrics

  

 
| Metrics || Formula || Synonyms |
| --- | --- | --- |
| Sensitivity || TP/TP + FN || Recall, True positive rate |
| Specificity || TN/TN + FP || True negatives |
| Precision || TP/TP + FP || Positive predictive value |
| False positive rate || FP/FP + TN || 1-specificity |
| Negative predictive value || TN/TN + FN || NPV |
| F1 score || 2x precision x recall/precision + recall || Harmonic mean |
| Accuracy || TP + TN/TP + TN + FP + FN ||  |
| Misclassification rate || 1- accuracy || Error rate |

  

g. Specificity = TN/TN +FP = 0.884. Remember specificity and sensitivity are at odds so there is always a tradeoff.

a. Precision (positive predictive value or PPV) = TP/TP + FP = 0.854. Precision means how precise Recall is. Remember that precision includes FP in the denominator. It is not precise if there are too many false positives.

b. Negative predictive value or NPV = TN/TN + FN = 0.813

c. F1 Score = 2 x recall x precision/ recall + precision = 0.797. This is a way to compute the harmonic mean of recall and precision (it can range from 0 to 1). Closer to 1 is desirable. This is a useful metric with imbalanced data. You can also calculate other F scores: if you want to place more attention on recall and less on precision, use F2 score (1 + 2 ² ) x recall x precision/2 ² x recall + precision; if you want to place more attention on precision and less on recall calculate the F0.5 score (1 + 0.5 ² ) x recall x precision/0.5 ² x recall + precision.

d. Accuracy = TP + TN/TP + TN + FP + FN = 0.812. Accuracy is the number of true positives and true negatives divided by all data. Accuracy should not be used if there is class imbalance since it can provide very misleading and inaccurate values for accuracy.

e. Misclassification rate (error rate) = 1- accuracy or 0.188 in this case

f. Here is a good summary article on recall/precision and specificity/sensitivity ¹⁵

  
![](images/image-FQQNKKAZ.png)  

Sensitivity and Specificity (StatQuest)

  

#### 5.4.4 ROC Curve Widget

  

Model discrimination means how well the model discriminates between the classes or outcomes for classification models. If it discriminates extremely well the two classes will have non-overlapping distributions. In Figure 5.20 the curve on the right (true positives) overlaps with the curve on the left (true negatives) so there is not perfect discrimination, which is typical for classification problems. The overlap areas indicate false positives and false negatives.

The receiver operating characteristic (ROC) curve dates back to WWII when they needed to determine if radar accurately identified enemy targets or not. The ROC curve compares the TP rate (TPR) (100 x TP/TP + FN) on the Y axis versus the FP rate (FPR) (100 X FP/FP + TN) on the X axis. (FPR is the same as 1- specificity). Specificity = TN/TN + FP. Remember that sensitivity (recall) and specificity are tradeoffs. Figure 5.21 shows a typical ROC curve. It makes sense that you would want the ROC curve to be in the upper left so there is high sensitivity and a low false positive rate.

[Figure 5.22 shows the area under the curve (AUC) which is the performance measure of choice for most binary classification models. Some people use the term AUROC, but it is also known as the C statistic (concordance statistic). AUC represents the average value of sensitivity for all values of specificity.](#content0140.xhtml)

  
![](images/image-TEQQC78A.png)  

Figure 5.20 Left: the distribution of TP and TN to indicate discrimination. Note the default threshold of 0.5 with a vertical dashed line. Right: three important locations on the ROC curve are displayed. ¹⁷

  
![](images/image-4L3TY0EF.jpg)  

Figure 5.21 ROC curve for logistic regression with different thresholds A-C

  

Note: Sensitivity, specificity, and AUC are not influenced by disease prevalence. Sensitivity and specificity provide valuable information about the test’s performance regardless of the disease prevalence, allowing for direct comparison between studies or different populations. The AUC represents the ability of the test to discriminate between positive and negative cases, regardless of disease prevalence as this summary measure considers the entire range of sensitivity and specificity values at different thresholds.

The higher the AUC, the better the model can separate (discriminate) the two classes. An AUC = 1 means perfect discrimination between the classes and an AUC of 0.5 means that the predicted separation of classes is not better than a 50/50 guess. In general, an AUC of less than 0.60 represents poor discrimination; 0.60 to 0.75 is possibly helpful, and over 0.75, suggests useful discrimination between classes. ¹⁶

  
![](images/image-3987WCYD.png)  

Figure 5.22 AUC is the shaded gray area

  

The ROC curve is not a smooth curve because it is calculated based on multiple thresholds which are the cutoff points between classifications. The default ROC threshold is 0.50 so that data values above the 0.50 threshold are mapped to one class (e.g., 1) and those below 0.50, are mapped to the other class (e.g., 0). This probability is a measure of uncertainty. You can change the threshold and in fact, the ROC curve was created based on numerous thresholds. Note: changing the threshold does not change the curve, hence it doesn’t change the AUC. Mouse over the points on the ROC curve in Orange (Figure 5.21) and it reveals the threshold. As you increase the threshold you decrease the TPR (recall) and increase specificity but decrease the number of false positives. As you decrease the threshold you increase the TPR (recall) and decrease specificity but increase the number of false positives. Moving the threshold is one option for imbalanced data, as discussed in another book chapter.

Moving the threshold has overarching significance. For example, for a screening test, you will want a threshold with higher sensitivity, whereas, for a confirmatory testing, a high specificity is desirable. Subject matter experts need to decide the appropriate tradeoff for a given clinical scenario. How many false positives are you willing to accept, and will too many false positives cause alert fatigue? ¹⁷

Some programs generate confidence intervals for AUCs, but Orange does not. How to determine the optimal threshold? Orange posts what it considers the optimal threshold. For example, in Figure 5.21 the optimal threshold is 0.486.

The QR code icon on the bottom left will take you to an interactive model of a receiver operator curve based on detecting airplanes vs clouds. The vertical threshold line can be shifted to view the change in sensitivity and specificity. The QR code icon on the bottom right links to a video that explains ROC and AUC concepts.

  
![](images/image-DJXBEP78.png)  

ROC and AUC (MLU)

  
![](images/image-QCL5MREG.png)  

ROC and AUC (StatQuest)

  

#### 5.4.5 Precision-Recall (PR) Curve

  

With Orange version 3.33, a PR curve became available. It can be found in the Evaluate Menu as a Performance Curve widget. Here are some general guidelines for when to use ROC curves or Precision-Recall curves in a classification scenario:

•ROC curves should be used when there are roughly equal numbers of observations for each class.

•Precision-Recall curves should be used when there is a moderate to large class imbalance.

The reason for this recommendation is that ROC curves present an optimistic picture of the model on datasets with a class imbalance. ¹⁸

[Figure 5.23 shows a PRC for the heart disease dataset that is fairly balanced. The curve evaluates the fraction of true positives among the positive predictions and if recall and precision are both high (near 1) the curve will be in the upper right, the mirror image of the AUC. The AUPRC = 0.90 ¹⁹-²¹](#content0142.xhtml)

If your dataset is imbalanced as is the case for the Kaggle stroke dataset where non-stroke patients outnumber stroke patients by 20:1 then the curve looks like Figure 5.24 and is in the lower portion of the plot. The AUPRC = 0.19. There is more on this subject later in this chapter.

  

#### 5.4.6 Other Valuable Orange Curves

  

Orange does offer some additional options to view the tradeoff between sensitivity and specificity, as well as the tradeoff between sensitivity (recall) and precision. In the calibration plot widget, you can select under Metrics a “sensitivity and specificity” curve, and also a “precision and recall” curve. There is a vertical threshold slider so you can adjust the threshold values to achieve your desired tradeoff between sensitivity and specificity. Figure 5.25 displays the sensitivity and specificity curves with a threshold slider. Using the slider you see as the threshold increases, sensitivity decreases and specificity increases. Figure 5.26 displays precision vs recall with a slider. As the threshold increases, the sensitivity (recall) decreases, and precision increases.

  
![](images/image-28NYTCWT.png)  

Figure 5.23 Precision-recall curve with balanced data

  

From figures 5.25 and 5.26 you can see that there are tradeoffs between sensitivity and specificity and between sensitivity (recall) and precision. Figure 5.27 displays the relationships between recall, precision, accuracy, and F1 score over various thresholds. Note that accuracy plateaus at higher thresholds. Interactive models of AUROC, recall, precision, and F1 can be found at this reference. ²²

  

#### 5.4.7 Lift Curve

  

The lift curve is another method to look at model performance but one we will not explore further. The lift curve is a graphical representation that measures the improvement provided by a predictive model compared to a random guess. It is most commonly used in the marketing industry for assessing marketing campaigns and customer targeting.

  

#### 5.4.8 Calibration Plot

  

This plot displays the probabilities of each prediction on each row in a dataset . It is important that risk prediction models are well-calibrated. This plot evaluates the goodness of fit between the predicted risk and actual probabilities. ²³ Good discrimination does not guarantee good calibration. If the probabilities are very close to the outcome class then this will create a calibration plot that follows the 45-degree diagonal line as shown in Figures 5.28 and 5.29. In Figure 5.28 the best-trained model for stroke prediction was a Stack model but it still had calibration issues where it deviated from the diagonal line. In Figure 5.29 the best model for the test dataset was logistic regression but it was very poorly calibrated as described in the figure since it had a strong tendency to overestimate risks with false positives. For example, the predicted risk is 0.8 on the x-axis but only 0.18 for expected probabilities. The Calibration widget lists two methods to improve calibration: isotonic and sigmoid.

  
![](images/image-A977NO8T.png)  

Figure 5.24 PRC using a class imbalance dataset

  
![](images/image-DIS1QYCU.png)  

Figure 5.25 Sensitivity vs Specificity plot with slider

  
![](images/image-1XGRZ2IQ.jpg)  

Figure 5.26 Precision vs Recall plot with slider

  
![](images/image-FMNRU00S.png)  

Figure 5.27 Recall, accuracy, precision, and F1 scores at different thresholds

  

Note: There are a variety of statistical tests that measure model calibration when you are interested in model probabilities:

•Use the Hosmer-Lemeshow goodness of fit test for logistic regression when you are interested in risk prediction. This is not calculated in Orange.

  
![](images/image-HCUQTXFK.jpg)  

Figure 5.28 Calibration curve for training data for a Stack model

  

•The Brier Score reports the mean squared error between the expected probabilities for the positive class and predicted probabilities. Ideal Brier score = 0. This is not calculated in Orange.

  

#### 5.4.9 Residual Plots

  

A classic way to compare the actual data to the predicted model values is to create residual plots for regression models. The residual plot in Figure 5.30 is displayed on a scatter plot and is available in JASP under the linear regression module > Plots > Residual plots. You must enter the target variable in the “Dependent Variable” section in JASP and then enter all other predictors in the “Covariates” section to create this residual plot. Such plots refer to residuals as the difference between predicted values and actual values. These plots can display if a predictive model is accurate throughout the whole range of the real target variable and if and where it tends to deviate from the real values it has tried to predict. ²⁴ Such plots compare the predicted value residuals as their actual residual values and also as standardized residuals as shown in Figure 5.30 for a body fat percentage dataset.

A variation of the classic residual plot can also be created in Orange with the help of the workflow shown in Figure 5.31. In this workflow, we are interested to see how well the linear regression algorithm predicted the percent body fat values for the test data. The actual individual predictions are shown in the Data Table widget that is connected to the Test and Score widget. The Scatter Plot and Polynomial Regression widgets are attached to the Data Table widget to provide a linear best-fit line and a polynomial best-fit line of the residuals.

  
![](images/image-8YSKK5EG.jpg)  

Figure 5.29 Poorly calibrated logistic regression model for test data demonstrating a false sense of risk

  
![](images/image-AJ3CBSSN.jpg)  

Figure 5.30 Residual plot for a multiple variable regression model for percent body fat

  
![](images/image-6VBW1T1H.jpg)  

Figure 5.31 Orange workflow to create actual versus predicted residual plots

  

[Figure 5.30 shows how the real data points compare with the predicted values for those same points on a Residuals Plot with Linear Best Fit Line for test data residuals. Follow these steps to recreate the graph shown in Figures 5.32 and 5.33:](#content0145.xhtml)

1\. First note that the Data Table widget now has two important columns we will use to create the scatter plots shown in Figures 5.32 and 5.33 .

a. The Percent Body Fat column is the real target variable for this dataset which we will use as the X-axis for the Scatter Plot and Polynomial Regression widgets.

b. The Linear Regression column is the column of predicted values which will be used as the Y-axis for the Scatter Plot and Polynomial Regression widgets.

2\. Paste the resulting scatter plot and polynomial graphs in separate Powerpoint slides.

3\. In each of those graphs, draw a dashed diagonal line that represents the Ideal prediction line when all predicted values are perfectly correlated with the real data. Be sure to draw that line to intersect equal points on the x and y-axis so that it is a true diagonal line.

4\. Now compare the dashed diagonal line with the actual best-fit lines to see how well the predictions are calibrated with the actual values. When the differences are large, the predictive model is flawed.

The above-mentioned instructions to create these custom graphs may seem complicated but they offer alternate ways to view residual plots.

[Figure 5.32 shows how and where the actual predictions deviate from a perfect prediction (dashed diagonal line). A linear best-fit line is also shown to compare how the predicted values are tracking compared to a theoretical perfect prediction dashed line.](#content0145.xhtml)

[Figure 5.33 shows how the real data points compared with the predicted values as in Figure 5.32 but this figure uses a third-order polynomial regression fit line instead of a straight line to more closely track the fit of the data. This figure also shows the slightly nonlinear nature of the residuals.](#content0145.xhtml)

  
![](images/image-OPLLWQQU.jpg)  

Figure 5.32 Residuals Plot with Linear Best Fit Line for Residuals

  
![](images/image-4V556S9G.jpg)  

Figure 5.33 Residuals Plot with Polynomial Best Fit Line for Residuals

  

Residual plots are very useful to display the accuracy of predictive models in a clear and visual manner that is not difficult to interpret.

  

5.5 EXPLAIN MODULE

  

  

[Figure 5.34 provides a visual representation of our current position within the 8-step DISCOVER process. At this stage, we find ourselves in the seventh phase, named: “Explain model insights effectively to stakeholders to build trust.” This chapter will outline various visualization techniques designed to present the outcomes of predictive models in an effective and comprehensible manner.](#content0147.xhtml)

This Explain module is accessed by downloading it from the Add-ons in the options menu since it is not included as part of the standard Orange installation process. The burden is always on the analyst to not only understand their analysis fully, but to also clearly explain their models to others that most probably do not have a technical or analytical background. The Orange Explain module is not the only section in Orange that can help to explain models, but it does offer some creative solutions to supplement model explainability efforts. Advanced data analytics modeling activities should always include a rank for how important each predictor was in their efforts to predict the target variable.

  

#### 5.5.1 Rank Widget

  

The Rank widget is an important part of the model explanation strategy and is easy to understand. This widget is not part of the Explain module, but it is very similar to the widgets in the Explain section. As mentioned in Chapter 2 , it offers seven different scoring methods for predictor ranking. When used to determine how much a variable contributes to a model it is referred to as mutual information. Information gain/mutual information is a math-derived formula that determines the amount of information gained. For more information as to how information gain is calculated, we refer readers to these references. ²⁵-²⁶

However, the Rank widget is not limited to just scoring predictors with those seven scoring methods. As shown in Figure 5.35, the Rank widget can also be asked to show the rank of a specific analysis for multiple learner widgets, such as logistic regression (with Lasso or Ridge options), random forest, or gradient boosting which has four options. A separate widget can be added to the workflow for each widget analysis option to compare their results with the Rank widget. Sometimes, Orange needs a little help to determine what the target and predictor values are that should be included in a model, which is why the Select Columns widget was added to the workflow in Figure 5.35.

In later chapters we will explain the differences between these learner widgets and their options. Figure 5.36 shows that the rank widget can now show the information gain model scorer which ranks the importance of the features compared to various analysis algorithms and their options for the diabetes dataset.

It should be noted that the Rank and Feature Importance widgets may not always be able to work together on a specific analysis widget, such as logistic regression. If one of these ranking options does not work for a specific data set, you should try to use a different and appropriate learner widget.

  
![](images/image-XQ9F9EYZ.png)  

Figure 5.34 Step seven in the Data Science DISCOVER process

  
![](images/image-CKQP9FTR.png)  

Figure 5.35 Attaching the Rank Widget to various classification widgets

  
![](images/image-HXGYDR21.jpg)  

Figure 5.36 Rank widget results for the Logistic Regression and a select group of built-in scoring methods

  

#### 5.5.2 Feature Importance Widget

  

The Feature Importance widget uses “permutation feature importance” which is a Python package that works for classification and regression. This package evaluates the relationship between the predictive variable and the target to see how much the model is dependent on it. Shuffling the variables in a particular order of special interest is called permutation. As mentioned in Chapter 4 , permutation feature importance shuffles features in a column and determines the effect it has on the outcome (e.g., feature rank). It can be used for classification or regression. The idea is that if shuffling (changing the results of a predictor in one column) a predictor causes the model performance to degrade significantly, the predictor must be important. Figure 5.37 shows the associated Orange workflow. In Figure 5.38 an example of results for feature importance based on the AUC is displayed but four other options are available. The number of coronary vessels calcified was the feature of greatest importance using this method. Use the defaults of 5 permutations and 10 top features in the Feature Importance widget. Like other visualization widgets, you can select a result and pass it to a data table or other widgets for further analysis. Keep in mind that the results won’t be identical to the Rank widget and may vary slightly among different algorithms. Error bars are shown in Figure 5.38 for each predictor.

[Figure 5.39 shows the workflow for how to apply the Feature Importance widget to regression problems and Figure 5.40 shows the results from this workflow when used to determine what predictor factors correlate to the percent of body fat. Error bars are also included in the graphic.](#content0148.xhtml)

  
![](images/image-1SL7HM2Q.jpg)  

Figure 5.37 Feature importance workflow for classification problems

  
![](images/image-D7NQLN8G.png)  

Figure 5.38 Feature importance results for a classification problem

  
![](images/image-QSB306D6.jpg)  

Figure 5.39 Feature importance workflow for regression problems

  
![](images/image-PQXNUYAO.jpg)  

Figure 5.40 Feature importance results for a regression problem

  

#### 5.5.3 Explain Prediction Widget

  

This is used primarily to explain individual predictions that you are specifically interested in. Logistic regression is used because it produces useful probabilities. Follow these instructions to create an Explain Prediction workflow:

•Look at the workflow for Figure 5.41 but remember to connect the Data Sampler widget to the Explain Prediction widget and set the link = data sample > background data by clicking on the specific connector line. See Figure 5.42 for the link settings.

•Connect the D ata Sampler widget to L ogistic Regression with the link = data sample > data. See Figure 5.43 for the link settings.

•Connect the D ata Sampler widget to the Predictions widget with the link showing the remaining data > data. Connect the Logistic Regression widget to the Predictions widget with the link = model > predictions, as shown in Figure 5.44.

•Connect the Predictions widget to the Explain Prediction widget with the link = predictions > data, as shown in Figure 5.45 .

•Open the Predictions widget, and select Show probabilities for 1 (target class). Highlight a prediction that was perfect (1.00 >1) (for example the 55-year old male) so we can see what it looked at by going now to the Explain Prediction widget (See Figure 5.46 ). There we select target class = 1. Base value = 0.48 which is the average probability in the data. The shaded up and down-arrows in the graph tell us which factors have a positive and negative impact on the outcome. show the values in the graphic indicate their relative contribution to the model. For this patient (see Figure 5.46 ) the strongest predictors of heart disease (in red) were ST depression by exercise 5.6 mm, chest pain = asymptomatic, a low heart rate (HR) on stress testing (HR = 111) and a reversible defect on thallium heart scan. Keep in mind that the SHAP results will be different for each algorithm.

  
![](images/image-O6POICT9.jpg)  

Figure 5.41 Workflow for the Explain Prediction widget

  
![](images/image-V3RFE8K4.jpg)  

Figure 5.42 Link settings between the Data Sampler and Explain Prediction widgets

  
![](images/image-UB3SAI3Z.png)  

Figure 5.43 Link settings between the Data Sampler and Logistic Regression widgets

  
![](images/image-5A6Y6S62.jpg)  

Figure 5.44 Link settings between the Logistic Regression and Prediction widgets

  
![](images/image-RS12T1FL.jpg)  

Figure 5.45 Link settings between the Predictions and Explain Prediction widgets

  
![](images/image-F62MC3WL.png)  

Figure 5.46 SHAP values for feature contributions in the Explain Prediction widget

  

#### 5.5.4 Explain Model Widget

  

This widget uses SHAP (SHapley Additive exPlanations) (2016) to display those variables that contributed the most (positively or negatively) to the model performance as related to the target. SHAP can be used for classification and regression models. It can be used for tree-based and non-tree-based models. The user must select the target class and the number of variables to analyze. Remember that correlation does not equal causality! Positive SHAP values point to the right while negative values point to the left. Remember that high VIFs in a dataset (multicollinearity) will add a lot of doubt on the credibility of the predictor ranks. Lasso regression is a great method that can correct multicollinearity with the right amount of regularization, as discussed in chapter two. Red is strongly positive towards the target class selected, while blue is strongly negative.

Connect the Explain Model widget to both the File widget (using the heart disease prediction dataset) and the Neural Network widget, as shown in Figure 5.47. Be sure the target class is set in the File widget. In Figure 5.48 we see the SHAP values which impact the model the most. The presence of colored vessels (calcified coronary arteries) is a strong predictor of the presence of heart disease. Interpretation is not always clear as you will see variables that are both positively and negatively associated with a target class.

  

5.6 JASP MODEL EVALUATION

  

  

JASP reports many of the same classification and regression performance measures as Orange. It does offer many diverse performance metrics , as well as ROC curve, PRC curve, and others. Sometimes the availability of metrics and plots is different between the regression module and the Machine Learning module. For example, the Brier score and PRC curve are available in the logistic regression module but not in the Machine Learning module. In addition, JASP reports the following for binary classification in its Machine Learning Module:

•Precision: Positive Predictive Value

•Recall: True Positive Rate

•False Positive Rate: The ratio of incorrect positive predictions to the total negative classes.

•False Discovery Rate: The ratio of incorrect positive predictions to the predicted positive classes.

•F1 Score: The harmonic mean of precision and recall.

•Matthews Correlation coefficient: An alternative to F1 or accuracy that is more reliable for imbalanced datasets. ²⁷

  
![](images/image-J9RG9W34.jpg)  

Figure 5.47 Explain model workflow

  
![](images/image-BVI0K0AM.jpg)  

Figure 5.48 Beeswarm plot of SHAP result

  

Table 5.4 JASP feature importance

  
![](images/image-CKOHD2OG.png)  

•Negative Predictive Value: The ratio of correct negative predictions to the total predicted negatives.

•True Negative Rate: The ratio of correct negative predictions to the total negative classes.

•False Negative Rate: The ratio of incorrect negative predictions to the total positive classes.

•False Omission Rate: The ratio of incorrect negative predictions to the predicted negative classes.

•Threat Score: The ratio of correctly predicted positives to all predicted and true positives.

•Statistical Parity: The ratio of predicted positives to all predictions.

JASP offers feature importance for several algorithms. Table 5.4 shows a feature importance table that reports similar information in the Orange Feature Importance widget. The features are ranked in descending order. JASP does not offer SHAP functionality.

  

5.7 HYPOTHESIS TESTING

  

  

Predictive models do not include hypothesis testing or p-values as a standard model performance metric. Common predictive model metrics for classification problems include accuracy, precision, recall, F1 score, MCC, and ROC AUC, while for regression problems, metrics such as mean squared error (MSE), mean absolute error (MAE), and R-squared are commonly used. However, it is not uncommon to use hypothesis tests during the EDA phase prior to predictive modeling.

Hypothesis testing is a statistical method that uses p-values to determine if there is enough evidence to accept (p-value > 0.05) or reject (p-value < 0.05) a null hypothesis. The null hypothesis is the assumption that there is no significant statistical difference or relationship between two or more features in a dataset, such as gender or day of the week. The type of hypothesis test used depends on the type of data being analyzed and the goals of the analysis.

There are dozens of different hypothesis tests that have been crafted to cater to a diverse and specialized array of use cases. The ever-evolving toolbox of hypothesis tests ranges from basic t-tests and chi-square tests to highly specialized tests that are also focused on non-parametric data. This section is not intended to provide expertise on the topic of hypothesis testing but to just offer an overview of the hypothesis testing options available in Orange, JASP, and BlueSky Statistics software.

  

#### 5.7.1 Hypothesis Testing Example

  

Imagine that after one match, Hockey Team A reports 5 goals scored out of 100 attempts (5%), and Hockey Team B reports 4 goals scored out of 100 attempts (4%). But data from just one match is not enough from which to conclude which team has better offensive strategies. It’s like judging the quality of a book by reading just one page; you don’t get the whole story!

Statistical analysis is like a seasoned sports analyst aiming to sort out the above-mentioned dilemma. However, even the most skilled analysts need enough data to draw reliable conclusions. So, instead of just evaluating performance from one match, the teams gather data over an entire season on their goal attempts and successes. Now this is like reading the whole book.

Still, just collecting more data does not guarantee valid conclusions from hypothesis tests since almost any hypothesis test has a list of very strict prerequisites that must be met before that specific hypothesis test can offer valid conclusions. Here are some common hypothesis test requirements:

•High quantities of data for each group under comparison

•Normality of the data

•Equal variances between the groups being compared

•Random sampling so that the results will be generalizable to the population

•The absence of outliers

•Conducting power analysis to determine the sample size required to achieve a certain level of required confidence level

•No missing data

As seen from the above list, hypothesis testing is a very sensitive analysis technique whose conclusions can easily be invalidated if the prerequisite assumptions are not met. Conversely, if these prerequisites are met, some very interesting insights can be extracted from this type of analysis.

  

#### 5.7.2 How Hypothesis Tests Make Decisions

  

P-values are auto-calculated with every hypothesis test which are used to either accept or reject a pre-stated null hypothesis. The hypothesis testing p-value is like an “Inverted Excitement Scale” that ranges from 0 to 1. If the p-value is closer to 0, it’s like saying, “Wow! Something is going on here!”. If it’s closer to 1, it’s like saying, “Forget it, nothing exciting here”. A p-value of 0.05 is usually set as the “Aha-Moment threshold value”, under which we start to get excited that the two groups under analysis are different from each other in some way (mean, median, variance, proportion, etc.).

When the p-value is < 0.05, we then say that the “sameness hypothesis” (aka: null hypothesis) is rejected, and the “differentness” hypothesis (aka: alternate hypothesis) is accepted. A common phrase used to remember this threshold is: “if the p is low, the null must go,” meaning that when the p-value is < 0.05, we reject the null hypothesis which represents the sameness hypothesis between the groups being compared.

  

#### 5.7.3 Type 1 and Type 2 Hypothesis Testing Errors

  

As previously mentioned, hypothesis tests can make mistakes which are called type 1 or type 2 errors. Such errors are not directly detectable. To understand these statistical error types, let’s imagine a court trial where someone is accused of stealing cookies, and we have two types of flawed court verdicts that can differ from the absolute truth, which are accusation errors, as described below:

•Type 1 Error (False Positive - Innocent person is convicted ): The person didn’t actually steal cookies, but the judge says, “Guilty!” It’s like blaming a sibling for taking a cookie when it was actually the dog.

•Type 2 Error (False Negative - Guilty person goes free): The person did steal cookies, but the judge says, “Not guilty!” It’s like a sibling really did take the cookie, but the parents don’t believe it and they got away with it.

So how do you avoid these Type 1 and 2 hypothesis testing errors? By following the specifically listed requirements for each hypothesis test and collecting high quality and high quantity data.

A Type 3 Error, also known as an error of the third kind, refers to a situation in statistical hypothesis testing where researchers provide the right answer to the wrong question. It occurs when a statistical test is used to answer the wrong research question or when the correct hypothesis is rejected but for the wrong reason.

  

#### 5.7.4 Hypothesis Tests Available in Orange, JASP, and BlueSky Statistics

  

Orange offers only limited chi-squared and t-test hypothesis testing capability within the Distribution and Box plot widgets. JASP and BlueSky Statistics offer many hypothesis testing options. Figure 5.49 shows the main hypothesis tests available in JASP in different JASP menu tabs.

[Figure 5.50 shows the BlueSky Statistics hypothesis testing capabilities that are either available under the sample size test tab or under the Analysis tab.](#content0156.xhtml)

Listed below are just some of the available Orange, JASP, and BlueSky Statistics hypothesis tests broken out by univariate, bivariate, and multivariate data analysis applications. As previously noted, predictive modeling does not include hypothesis testing as a core requirement:

1\. Univariate (one factor) data analysis:

•Normality tests are used to test whether a continuous feature represents a normal distribution.

•Go to JASP > Descriptive Statistics > enter at least one continuous variable in the Variables section to test for normality. Statistics > check Shapiro-Wilk test > review p-value(s).

•Go to BlueSky Statistics > Analysis > Distribution Analysis > select at least one continuous variable in the Source variables section to test for normality. Normality testing options include the following tests: Shapiro-Wilk normality test, Anderson-Darling normality test, and the Kolmogorov-Smirnov normality test.

  
![](images/image-U93NZ7R4.jpg)  

Figure 5.49 JASP hypothesis tests

  
![](images/image-PU21OS3Y.jpg)  

Figure 5.50 BlueSky Statistics Hypothesis Testing options

  

•When p-values are below 0.05 for any normality test, this statistically confirms that the data is not of a normal distribution.

•One-sample t-test (assumes normality): Used to test if the mean of a sample is significantly different from a known or hypothesized target value.

•Go to JASP > T-Tests > One Sample T-Test > enter one feature > Tests > enter desired test value > check desired test(s) > review p-value(s).

•Go to BlueSky Statistics > Means > T-Test, one sample > Select a variable > select a test value > review p-value(s).

•When p-values are below 0.05, this confirms a statistically significant difference between the mean and the target test value which means that a stated target has not been met.

•Independent t-test (assumes normality): Used to test if the means of two independent samples are significantly different from each other.

•Go to JASP > T-Tests > Independent Samples T-Test > Select one continuous feature for the Dependent Variables section and select one categorical variable in the Grouping Variable section > Tests > check desired test(s) > review p-value(s).

•Go to BlueSky Statistics > Means > T-Tests > Independent Samples> conduct desired test > review p-value(s).

•When p-values are below 0.05, this confirms a statistically significant difference between the means.

•Independent Two-sample t-test (does not assume normality): Used to test if the medians of two independent samples are significantly different from each other.

•Go to JASP > ANOVA > Enter a continuous variable in the Dependent Variable section > Enter a categorical variable in the Fixed Factors section > Nonparametrics > Under Kruskal-Wallis Test enter a categorical variable to the box on the right side > Review p-value(s).

•When p-values are below 0.05, this confirms a statistically significant difference between the medians.

•Paired t-test (assumes normality): Used to test if the means of two related samples (e.g., pre-and post-treatment) are significantly different for the same patient.

•Go to JASP > T-Tests > Paired Sample T-Test > Select the pre and post or A/B test features > Tests > Check desired test(s) > Review p-value(s).

•Go to BlueSky Statistics > Means > T-Test, Paired Samples > Review p-value(s).

•When p-values are below 0.05, this confirms a statistically significant difference between the means for the pre and post or A/B test features.

•One-way Independent ANOVA test for testing Homogeneity of variance: Used to test if two or more groups for a continuous variable have the same variance.

•Go to JASP > ANOVA > Select a continuous variable that has two or more groups and enter it into the Dependent Variable section > Select a categorical feature and enter it in the Fixed Factors section > Assumption Checks > Check Homogeneity tests to get the Levene’s test > review p-value(s).

•If the p-values and below 0.05, the variances for at least two of the groups are different.

•Chi-square tests check if the observed and expected frequencies between different subgroups are statistically the same.

•Go to Orange > Select the Box Plot Widget > Select a categorical feature in the upper Variable window > Select another categorical feature in the lower Subset window > Look at the chi-squared p-value below the graph in parentheses.

•Go to BlueSky Statistics > Non-Parametric > Chi-Squared Test > review p-value.

•If the chi-squared p-value is below 0.05, then the observed and expected frequencies do not match each other.

2\. Bivariate (two factors) data analysis:

•Pearson correlation test with Heatmap: Used to test whether a significant linear relationship exists between two continuous variables.

•Go to JASP > select Regression > Classic > Correlation > select all of the variables you want to test for correlation and enter them in the Variables box > check Pearson’s r > check Heatmap, which creates a matrix with r values > review r and p-value(s).

•Check Report significance which creates a matrix with r values and p-values. When the p-values are below 0.05, the correlation between the two matching features is statistically significant.

•Spearman correlation test with Heatmap: Used to test if there is a significant monotonic relationship between two continuous or ordinal variables.

•Go to JASP > select Regression > Classic > Correlation > select all of the variables you want to test for correlation and enter them in the Variables box > check Spearman’s rho > check Heatmap, which creates a matrix with r values > check Report significance which creates a matrix with r values and p-values > review r and p-value(s).

•When the p-values are below 0.05, the correlation between the two matching features are statistically significant.

3\. Multivariate (two+ factors) data analysis:

•Multiple regression analysis for regression or classification: Used to test the relationship between a dependent variable (target) and multiple independent variables (predictors).

•Go to JASP > select Regression > linear or logistic regression > enter the target in the Dependent Variable section > enter all continuous variables in the Covariates section > enter the categorical factors in the Factors section > Statistics > check Estimates and Model Fit > check Collinearity diagnostics to get the VIFs (Variance Inflation Factors) > look at the p-value on the ANOVA table to see if the whole model is statistically significant (p-value < 0.05) > look at the Coefficients table to see the p-values for each entered factor.

•Remove any variable from the input list that has a p-value greater than 0.05 but do this one factor at a time, starting with the highest p-value.

•When all p-values are below 0.05 on the Coefficients table, you have a final valid regression model.

•Check if all VIFs are below 5. If not, you have a multicollinearity issue to deal with. The model and the variable ranks will not be correct unless all VIFs in the model are below 5.

•Two-sample Kolmogorov-Smirnov Test: use an online calculator to test if two different features come from the same distribution. This is useful when synthesizing data to ensure that the new data matches the real existing data.

•Go to SciStatCalc: Two-sample Kolmogorov-Smirnov Test Calculator > copy and paste each data set into its own box on the website or upload a file with the two data columns > click the button titled: “Plot CDFs and perform two sample Kolmogorov-Smirnov Test” > view the plots and especially the p-value at the bottom of the output.

•If the p-value is below 0.05, it can be concluded that the two columns of data come from a different distribution and are not considered to have statistically verified similar shapes as can be seen on a histogram.

•If the p-value is above 0.05, it can be concluded that the two columns of data come from the same distribution and are considered to have statistically verified similar shapes as can be seen on a histogram.

•Make sure that no blank spaces or text (e.g., column headers) are pasted into the KS calculator boxes which can result in incorrect answers.

  
  

Hypothesis Testing Summary

  

  

Key Principles

•Hypothesis testing can complement machine learning under the right circumstances, especially in the Exploratory Data Analysis phase, and especially for smaller datasets.

•Hypothesis tests can make mistakes which are called type 1 or type 2 errors.

•Hypothesis testing is a statistical method that uses p-values to determine if there is enough evidence to accept (p-value > 0.05) or reject (p-value < 0.05) a null hypothesis.

•The hypothesis testing p-value is like an “Inverted Excitement Scale” that ranges from 0 to 1. If the p-value is closer to 0, it’s like saying, “Wow! Something is going on here!”. If it’s closer to 1, it’s like saying, “Forget it, nothing exciting here.”

•A p-value of 0.05 in any hypothesis test is usually the “Aha-Moment threshold value.”

•With a p-value of < 0.05 we start to get excited that the two groups under investigation are different from each other in some way (mean, median, variance, proportion, etc.)

•Orange just offers basic hypothesis testing such as chi-square tests and t-tests in the Distribution and Box Plot Widgets

•JASP and BlueSky Statistics software offer many different hypothesis tests and other classic statistical analysis techniques that are not available in Orange.

•When comparing two models or groups with hypothesis testing in large machine learning datasets, near identical numerical values may be deemed as having statistically significant differences simply because of the large number of rows in the dataset.

•Hypothesis testing becomes irrelevant when analyzing Big Data because the differences between almost all groups may be statistically significant.

  

  

5.8 IDENTIFYING AND ADDRESSING CONCEPT DRIFT AND MODEL DRIFT

  

  

[Figure 5.51 provides a visual representation of our current position within the 8-step DISCOVER process. At this stage, we find ourselves in the eighth phase, named: “Reevaluate and Retrain the model when model drift and concept drift is confirmed”. This section will outline various situations that drive the need for model retraining.](#content0159.xhtml)

Predictive model performances are obviously linked to the identified correlations between model feature inputs and outputs (targets). There is absolutely no guarantee that these model input and output correlations will remain stable over time. This is why the model inputs, outputs (target) and model performance metrics need to be constantly monitored over time to check if any shifts and drifts occur.²⁷ There are a variety of statistical methods that can used to monitor if the data trends, distributions, means, or standard deviations have changed statistically after the model has been trained and deployed for use. Algorithms also exist that can monitor drift. ²⁸ Any drift may create a drop in model performance and trust in the algorithmic recommendations.

In the realm of data science, “model drift” and “concept drift” are terms often mentioned to depict shifts in data over time that can adversely affect the performance of a model. Each of these drifts can result in incorrect predictions, poor business decisions, regulatory issues and a loss of trust in the model. Though these two notions of “drift” bear similarities, they fundamentally represent two distinct phenomena, as described further in this chapter.

  

#### 5.8.1 Concept Drift

  

Concept Drift describes a gradual change in the fundamental correlation between the input variables (features) and the target variable(s) (output(s)). There can be several potential causes for this drift, including changes in user behavior, changes in user groups, market circumstances, seasonal patterns, and other reasons. For example, If your model forecasts ice cream sales based on outside temperature, the correlation between outside temperature and ice cream sales may deteriorate over time for many reasons such as new ice cream flavors being introduced elsewhere, shifting dietary preferences of the customers, or the expansion of available substitutes to your ice cream products.²⁹

  

#### 5.8.2 Model Drift

  

Model Drift, on the other hand, refers to the general deterioration in a model’s performance over time for any reason, including concept drift or any other bonafide or unidentified reason. It may be due to changes in the distribution of the input variables or a shift in user groups that the model was not originally trained on. In essence, model drift is about the model’s predictive performance decreasing over time due to any reason.

  
![](images/image-L3EMG4SX.jpg)  

Figure 5.51 Step eight in the Data Science DISCOVER process

  

Example of model drift: Model drift in fraud detection occurs when a machine learning model, trained on historical data to identify fraudulent transactions, becomes less accurate over time. As fraudsters’ behavior evolves and new fraudulent activities emerge, the model’s ability to detect these changes diminishes. The changing relationship between input variables and the target variable leads to a gradual decline in the model’s effectiveness in recognizing evolving fraud patterns. When this happens, it’s time to re-evaluate your model features and retrain the model.

While concept drift is a more specific term, referring to the change in the underlying correlation between inputs and outputs, model drift is a broader term that could encompass concept drift as well as other changes that affect a model’s predictive performance. Again, when this happens, it’s time to re-evaluate your model features and retrain the model.

  

#### 5.8.3 When to Retrain a Model

  

Retraining a predictive model is required when concept drift and / or model drift has been confirmed, especially when it crosses a predetermined threshold of data shifting or model performance deterioration. ³⁰ Such thresholds should be set in conjunction with automated monitoring to generate automated alarms that highlight the possible need for rapid model retraining efforts. However, to protect a model from drift alert fatigue, be aware that drift can happen in various scenarios: suddenly, gradually, or recurrently. ³¹

  

5.9 PUTTING KNOWLEDGE INTO PRACTICE

  

  

#### 5.9.1 Exercise

  

This chapter focused on model evaluation so we will create an exercise to evaluate the performance of a classification model. We will determine model discrimination and calibration. We will validate the model on test data and report standard model metrics. The dataset we will be using is a bank loan dataset from Kaggle.³² It is available for download there or in the Chapter 5 folder of our File-Share website (UniversalBank.csv).

1\. Be sure to look at the data dictionary on Kaggle which explains the definitions of the data columns in the dataset. Be aware that the file uploaded to the File-Share site, does not include the columns ID and zip code. Note : family is supposed to mean family size, but there are no zeroes or numbers greater than four, so that is unclear. Also, most of the mortgage column consists of zeroes, which means the mortgage has been paid off, or they are renters.

2\. The goal of the bank is to predict which attributes does a customer have that would make them likely to take out a loan, such as the result of an ad campaign? The data is based on a previous ad campaign.

3\. Upload the file to JASP

a. The first screen should be a spreadsheet-like view of the data. Look at each column.

4\. Begin with simple descriptive statistics

a. Move all variables to the variables box, except Personal Loan that will go in the Split box.

b. Under Statistics check mean, Std. deviation, Maximum and Minimum.

c. Under Basic Plots select Distribution and Correlation plots.

d. Under Customizable Plots select Boxplots. Select Box Plot element and Label outliers.

5\. Based on what you see, check the following:

a. Is there any missing data?

b. Is there class imbalance?

c. What is the age range (loan yes vs loan no?)

d. Difference in income (loan yes vs loan no?)

e. Difference in credit card balance (loan yes vs loan no?)

f. Difference in mortgage? (loan yes vs loan no?)

g. How correlated is age and experience in years? Is this likely to be evidence of multicollinearity?

h. Now look at box plots. Where are the differences between subgroups?

6\. We are suspicious there is multicollinearity, so select Linear Regression from the top Regression menu

a. Dependent variable = personal loan. Move continuous variables to the second window (covariates) and categorical go into the third window (factors).

b. Scroll down to Statistics and be sure the “collinearity diagnostics” option is checked.

c. In the table you should observe that there are two variables with very high VIFs - age and years of experience. The p-values are low to suggest that they do correlate with the target so we don’t want to delete both. Let’s take age out of the variables and re-calculate the VIFs. Now all VIFs are less than 5.

7\. Let’s create a classification model to predict those people who will choose to take out a personal loan versus those who will not.

a. In the Machine Learning menu at the top, select Boosting under Classification. We will only run one algorithm for this model.

b. Select target = personal loan and move the other predictors (except for age) to Features.

c. Scroll down and select confusion matrix, evaluation metrics, data split and ROC curves. Select Relative influence under plots (similar to Feature Importance widget in Orange). What variable has the highest influence?

d. Note: there is a 60/20/20 split (train/validation/test).

e. View the confusion matrix. Note the difference between false positives and false negatives.

f. View the Evaluation Metrics and note the excellent results in terms of mode discrimination.

g. Is there evidence of serious class imbalance based on these results?

8\. Upload the dataset into the Orange File widget

a. Connect to the Data Sampler widget and set to 80/20 train/test data split and stratify the sample. Use two connectors to connect to the Test and Score widget. One link should be data to data and the other link should be remaining data to test data.

b. Connect the Gradient Boosting widget to the Test and Score widget and connect the Calibration widget to the Test and Score widget.

c. Open the Test and Score widget and be sure target = 1 and “Test on test data” is checked.

d. The results should be similar to those generated by JASP.

e. Open the Calibration Plot widget. Be sure target = 1. Does the curve follow the 45 degree line? If not, where does it deviate?

f. This is an example of excellent model discrimination but mediocre calibration.

  

#### 5.9.2 Maturity Levels

  

Let’s focus on the utilization of model evaluation techniques within the Digital Marketing industry across varying project complexities and organizational maturity levels:

  

Digital Marketing (Low maturity level):

  

A marketing agency is using ML for a basic email campaign optimization.

Tip: They should:

•Balance the dataset to avoid model bias towards certain audience segments.

•Ensure they have enough data for meaningful model training and validation.

•Use accuracy and precision as initial evaluation metrics.

•Create a confusion matrix to understand the model’s classification capability.

•Address concerns by iterating through the model training phase.

  

Digital Marketing (Moderate maturity):

  

The agency is implementing ML to predict user engagement across a social media campaign.

Tip: Building on basic strategies, they should:

•Apply both ROC (Receiver Operating Characteristic) and PRC (Precision-Recall Curve) for model evaluation.

•Visualize residuals if using regression to predict levels of engagement.

•Begin feature importance analysis to identify key engagement drivers.

•Use tools like SHAP (SHapley Additive exPlanations) for model explainability.

  

Digital Marketing (High maturity):

  

The agency is harnessing advanced ML for a personalized omnichannel marketing strategy.

Tip: Advancing from the moderate strategies, they should:

•Experiment with oversampling or under-sampling techniques for imbalanced datasets.

•Apply a variety of model performance metrics, like F1-score and AUC-ROC.

•Consider external validation data to improve general model generalization.

•Assess data and feature importance, adjusting the model’s focus as needed.

•Experiment with hyperparameter tuning to optimize model performance.

•Deepen model explainability efforts, ensuring clients understand model decisions.

•Continuously validate and refine models based on real-world feedback.

  

#### RESOURCES

  

  

1\. Everything you should know about confusion matrix for machine learning https://www.analyticsvidhya.com/blog/2020/04/confusion-matrix-machine-learning/

2\. Understanding Confusion Matrix https://towardsdatascience.com/understanding-confusion-matrix-a9ad42dcfd62

3\. ROC curve. USMLE Course https://www.youtube.com/watch?v=775yl6y\_Ev8

4\. Interpreting ROC Curve and ROC AUC for Classification Evaluation https://towardsdatascience.com/interpreting-roc-curve-and-roc-auc-for-classification- evaluation-28ec3983f077

5\. Questioning the SPIN and SNOUT rule in clinical testing. BMC 2019 https://archivesphysiotherapy.biomedcentral.com/articles/10.1186/s40945-019-0056-5

6\. Churning the Confusion out of the Confusion Matrix https://blog.clairvoyantsoft.com/churning-the-confusion-out-of-the-confusion-matrix-b74fb806e66

7\. Bayes’ theorem, COVID19, and screening tests. File share site.

8\. Explain your model with the SHAP values Medium.com https://towardsdatascience.com/explain-your-model-with-the-shap-values-bc36aac4de3d

  

#### REFERENCES

  

  

[1\. Brownlee J. What is the Difference Between Test and Validation Datasets? \[Internet\]\[cited 2022 October 10\] Available from: https://machinelearningmastery.com/difference-test-validation-datasets/](#content0126.xhtml)

[2\. How to calculate the fold number (k-fold) in cross validation? \[Internet\]. Data Science Stack Exchange. \[cited 2023 Jul 4\]. Available from: https://datascience.stackexchange.com/questions/28158/how-to-calculate-the-fold-number-k-fold-in-cross-validation](#content0127.xhtml)

[3\. Olsen LR. Multiple-k: Picking the number of folds for cross-validation \[Internet\]. 2023 \[cited 2023 Jul 4\]. Available from: https://cran.r-project.org/web/packages/cvms/vignettes/picking\_the\_number\_of\_folds\_for\_cross-validation.html](#content0127.xhtml)

[4\. Ding S. Medium. 2021 \[cited 2023 Aug 19\]. Cross-validation techniques: K-fold cross-validation vs leave one out cross-validation. Available from: https://shangding.medium.com/cross-validation-techniques-k-fold-cross-validation-vs-leave-one-out-cross-validation-2dcfb7d5deb3](#content0130.xhtml)

[5\. Is k-fold cross-validation more effective than splitting the dataset into training and test datasets to prevent overfitting? \[Internet\]. Artificial Intelligence Stack Exchange. \[cited 2023 Jul 4\]. Available from: https://ai.stackexchange.com/questions/16570/is-k-fold-cross-validation-more-effective-than-splitting-the-dataset-into-traini](#content0130.xhtml)

[6\. Van Calster B, McLernon DJ, van Smeden M, Wynants L, Steyerberg EW. Calibration: the Achilles heel of predictive analytics. BMC Med \[Internet\]. 2019 Dec 16 \[cited 2022 Apr 18\];17(1):1–7. Available from: https://bmcmedicine.biomedcentral.com/articles/10.1186/s12916-019-1466-7](#content0131.xhtml)

[7\. Alba AC, Agoritsas T, Walsh M, Hanna S, Iorio A, Devereaux PJ, et al. Discrimination and Calibration of Clinical Prediction Models: Users’ Guides to the Medical Literature. JAMA \[Internet\]. 2017 Oct 10 \[cited 2022 Apr 25\];318(14):1377–84. Available from: https://jamanetwork.com/journals/jama/articlepdf/2656816/jama\_alba\_2017\_ug\_170001.pdf](#content0131.xhtml)

[8\. Poulopoulos D. Classifier calibration \[Internet\]. Towards Data Science. 2020 \[cited 2022 Apr 3\]. Available from: https://towardsdatascience.com/classifier-calibration-7d0be1e05452](#content0131.xhtml)

[9\. Uleman, Jeroen. 2019. “Probabilities and Odds in Medical Science.” Donders Wonders Blog. October 8, 2019.\[Internet\]\[cited 2022 August\] Available from: https://blog.donders.ru.nl/?p=10490&lang=en](#content0133.xhtml)

[10\. Tenny, S., and M. R. Hoffman. n.d. “Odds Ratio.” \[Internet\]\[cited 2022 August 21\].Available from: https://europepmc.org/article/nbk/nbk431098 .](#content0134.xhtml)

[11\. “Binary Logistic Regression - a Tutorial.” 2021. Digital Schools. April 28, 2021.\[Internet\]\[cited 2022 August 1\] Available from: https://digitaschools.com/binary-logistic-regression-introduction/](#content0134.xhtml)

[12\. “Interpret Logistic Regression Coefficients \[for Beginners\].” n.d. \[Internet\] \[cited 2022 August 21\] Available from: https://quantifyinghealth.com/interpret-logistic-regression-coefficients/](#content0134.xhtml)

[13\. Glas, Afina S., Jeroen G. Lijmer, Martin H. Prins, Gouke J. Bonsel, and Patrick M. M. Bossuyt. 2003. “The Diagnostic Odds Ratio: A Single Indicator of Test Performance.” Journal of Clinical Epidemiology 56 (11): 1129–35.](#content0135.xhtml)

[14\. Diagnostic Test Calculator \[Internet\]. \[cited 2022 Apr 3\]. Available from: http://araw.mede.uic.edu/cgi-bin/testcalc.pl](#content0135.xhtml)

[15\. Lekhtman A. Data science in medicine — precision & recall or specificity & sensitivity? \[Internet\]. Towards Data Science. 2019 \[cited 2023 Mar 1\]. Available from: https://towardsdatascience.com/should-i-look-at-precision-recall-or-specificity-sensitivity-3946158aace1](#content0139.xhtml)

[16\. Park SH, Han K. Methodologic Guide for Evaluating Clinical Performance and Effect of Artificial Intelligence Technology for Medical Diagnosis and Prediction \[Internet\]. Vol. 286, Radiology. 2018. p. 800–9. Available from: http://dx.doi.org/10.1148/radiol.2017171920](#content0140.xhtml)

[17\. Frontiers In. \[Internet\]. \[cited 2022 Apr 21\]. Available from: https://www.frontiersin.org/files/Articles/561802/frai-03-561802-HTML-r3/image\_m/frai-03-561802-g001.jpg](#content0140.xhtml)

[18\. Brownlee J. Machine Mastery. How to use ROC curves and Precision Recall Curves for Classification in Python. \[Internet\]\[cited 2022 October 2\] Available from: https://machinelearningmastery.com/roc-curves-and-precision-recall-curves-for-classification-in-python/](#content0141.xhtml)

[19\. Saito T, Rehmsmeier M. The Precision-Recall Plot Is More Informative than the ROC Plot When Evaluating Binary Classifiers on Imbalanced Datasets. PLoS One \[Internet\]. 2015 Mar 4 \[cited 2022 Apr 18\];10(3):e0118432. Available from: https://journals.plos.org/plosone/article/file?id=10.1371/journal.pone.0118432&type=printable](#content0141.xhtml)

[20\. Tahmassebi A. ROC vs Precision-Recall Curves with N-Folds Cross-Validation \[Internet\]. 2019 \[cited 2022 Apr 17\]. Available from: https://amirhessam88.github.io/roc-vs-pr/](#content0141.xhtml)

[21\. Rosenberg D. Unbalanced data? Stop using ROC-AUC and use AUPRC instead \[Internet\]. Towards Data Science. 2022 \[cited 2023 Feb 28\]. Available from: https://towardsdatascience.com/imbalanced-data-stop-using-roc-auc-and-use-auprc-instead-46af4910a494](#content0141.xhtml)

[22\. Amazon Machine Learning University. \[Internet\] \[cited 2022 June 19\] Available from: https://mlu-explain.github.io](#content0142.xhtml)

[23\. Huang Y, Li W, Macheret F, Gabriel RA, Ohno-Machado L. A tutorial on calibration measurements and calibration models for clinical prediction models. J Am Med Inform Assoc. 2020 Apr 1;27(4):621–33](#content0144.xhtml)

[24\. Gohar U. How to use Residual Plots for regression model validation? \[Internet\]. Towards Data Science. 2020 \[cited 2023 Feb 28\]. Available from: https://towardsdatascience.com/how-to-use-residual-plots-for-regression-model-validation-c3c70e8ab378](#content0145.xhtml)

[25\. Analytics Vidhya. How to Select the Best Split in Decision Trees Using Information Gain. \[Internet\]\[cited 2022 July 10\] Available from: https://www.analyticsvidhya.com/blog/2021/03/how-to-select-best-split-in-decision-trees-using-information-gain/](#content0147.xhtml)

[26\. Brownlee J. Machine Learning Mastery. Information and Mutual Information. \[Internet\]\[cited 2022 August 1\] Available from: https://machinelearningmastery.com/information-gain-and-mutual-information/](#content0147.xhtml)

[27\. Oladele S. neptune.ai. 2022 \[cited 2023 Aug 1\]. A comprehensive guide on how to monitor your models in production. Available from: https://neptune.ai/blog/how-to-monitor-your-models-in-production-guide](#content0151.xhtml)

[28\. Ali M. Understanding Data Drift and Model Drift: Drift Detection in Python \[Internet\]. DataCamp; 2023 \[cited 2023 Aug 1\]. Available from: https://www.datacamp.com/tutorial/understanding-data-drift-model-drift](#content0157.xhtml)

[29\. Paka A. Towards Data Science. 2020 \[cited 2023 Aug 1\]. How to detect model drift in MLOps monitoring. Available from: https://towardsdatascience.com/how-to-detect-model-drift-in-mlops-monitoring-7a039c22eaf9](#content0158.xhtml)

[30\. ML in Production \[Internet\]. 2019 \[cited 2023 Aug 1\]. The ultimate guide to model retraining. Available from: https://mlinproduction.com/model-retraining/](#content0160.xhtml)

[31\. Das S. neptune.ai. 2022 \[cited 2023 Aug 1\]. Best practices for dealing with concept drift. Available from: https://neptune.ai/blog/concept-drift-best-practices](#content0160.xhtml)

[32\. Jacob S. Bank\_Loan\_modelling \[Internet\]. 2018 \[cited 2023 Aug 19\]. Available from: https://www.kaggle.com/datasets/itsmesunil/bank-loan-modelling](#content0162.xhtml)

  

![](images/image-5A2Q6S2V.jpg)Chapter 6

  

## Supervised Learning

  

“If we have data, let’s look at data. If all we have are opinions, let’s go with mine.”

—Jim Barksdale, former Netscape CEO

  
![](images/image-M6MTZISG.jpg)  
  

LEARNING OBJECTIVES

  
  

By the end of chapter six readers should be able to:

•Describe classification and regression techniques as the main types of supervised learning.

•Discuss the difference between an algorithm and a model.

•Enumerate algorithms that can perform both classification and regression.

•Discuss the difference between correlation and regression.

•Describe the difference between multiple linear regression and polynomial regression.

•Describe the components that make up the simple linear regression equation.

•Compare Ridge, Lasso, and Elastic net regularization.

  
  

Chapter 6 Summary

  

  

Classification and regression are common methods of predictive analytics and supervised learning. Orange has the advantage of running multiple classification and regression algorithms at the same time on specific datasets, so comparisons are easy in the search for the best algorithm. Switching from training to test data to review modeling performances is also easy with Orange.

  

Regression or classification analysis may be a more common analysis technique for certain industries. Medical fields often use classification for diagnoses, while financial sectors lean towards regression for stock forecasts. E-commerce relies on classification for recommendations, whereas real estate uses regression for property pricing. In agriculture and manufacturing, both techniques find great application levels, just as digital marketing employs classification for customer segmentation and regression for website traffic growth predictions.

  

In classification analysis, the predicted outcome is categorical. In regression analysis, the predicted outcome is a continuous variable. Simple linear regression seeks to optimally fit a regression line or curve for a single x variable and y variable. Multiple linear regression involves more predictors which can be continuous or categorical. The most common method for simple regression (1 predictor and 1 target variable) is linear regression, but quadratic, cubic, and other curve fitting methods are also appropriate if the data correlations are non-linear.

  

Be careful not to excessively overfit your data with higher-order polynomial fits. Multiple machine learning algorithms can also be used for linear regression in the pursuit of the best-performing model. Various types of regularization will also be discussed, such as Lasso, Ridge, and Elastic net regression. The performance parameters for regression are different from classification and are also discussed in this chapter.

  

Key Principles

•All aspects of our 8-step DISCOVER data science process apply to supervised learning.

•Training and test data splits apply here too.

•Always add multiple algorithms and algorithm options in a model and select the best one.

•Model tuning and data science experiments are critical here.

•Always watch out for under and overfitting.

•Ensemble models and Orange calibrated learner techniques may be helpful.

•Supervised learning applies to the analysis of tabular data, images, speech, text, and other data domains.

  

  

6.1 CLASSIFICATION MODELING

  

  

Classification modeling is a fundamental part of supervised learning in machine learning. It involves predicting the correct label or class of a given input data based on a set of features or attributes. Classification models are trained using labeled data, where the input data is associated with known class labels. These models are then used to make predictions on new, unseen data.

  

#### 6.1.1 Introduction

  

Classification modeling is a type of supervised learning which means you know the binary or multi-class outcome you want to predict. When the outcome is categorical, this is referred to as classification; whereas if the outcome is continuous, this is referred to as regression. In a supervised learning scenario, the model will train on data with labels such as admitted vs not admitted to a hospital, spam email vs no spam email, or credit card fraud vs no credit card fraud. This implies that a subject matter expert has already labeled the data. For classification analysis projects there has to be a “ground truth” or a means to verify and create accurate labels. With unsupervised learning you are analyzing a dataset with no labels, so you want an algorithm to look at the data alone and find interesting groups, patterns, or clusters.

[Figure 6.1 demonstrates the division of machine learning into supervised and unsupervised learning and reflects the chapter organization in this book.](#content0168.xhtml)

For the sake of completeness, we could include reinforcement learning under machine learning as the third sub-category. It was derived from the gaming industry and is based on rewards and penalties. Like Pac-Man, an agent traverses a maze (environment) and learns by trial and error. We should also include semi-supervised learning as an uncommon type of machine learning. Semi-supervised learning uses a small amount of labeled data and a large portion of unlabeled data so the model can learn and make predictions on new data. Lastly, we can include transfer learning, where a model trains on an initial dataset and uses some of that knowledge for a new model. For example, a deep learning model might train on ImageNet and use that training to help classify dermatology images.

In the case of classification, the outcome you want to predict is categorical (yes, no), (died, survived), etc. An area of confusion is that frequently the outcome or class is numerical such as 1 or 0 but these are considered categorical because they are discrete integers and not continuous data such as 1.52. By tradition, the minority class in classification models is labeled 1 and the majority class is labeled 0. In medicine and in many other industries, the minority class is usually the class of interest, such as cancer, credit card fraud, manufacturing defects, customer complaints, etc. The reality is that computers require ones and zeroes for computation so we must accommodate this requirement. Most classification models are binary (two choices). However, it can involve more than two classes and could be considered as polynomial classification or multi-class classification and require special algorithms. Polynomial classification requires a nonlinear function to separate data into the most appropriate different classes. Please visit the resource section for more information on this topic. We will be dealing only with binary classification in this chapter.

  
![](images/image-R8N9JJV9.png)  

Figure 6.1 Supervised vs Unsupervised learning

  

Classification is the most common type of supervised learning method to perform predictive analytics in medical diagnostics, medical imaging applications, genomics, spam detection, fraud detection, customer churn, sentiment analysis, cybersecurity, and other domains. Conversely, regression might be more commonly applied in the fields of economics, finance, pharmaceutical drug dosage effectiveness, agricultural crop yields, manufacturing yields, real estate values, and other domains.

For classification problems, you can use older statistical models such as logistic regression and Naive Bayes or newer machine learning algorithms such as SVM, neural networks, boosted trees, and others. One definite attribute of Orange is the variety of algorithms and algorithm options available and the fact that you can run several simultaneously so their prediction performances can be compared for screening purposes. Many people use the term model and algorithms interchangeably but this is dangerous since there are big differences in how these terms should be used. A model seeks to allow many algorithms to compete with each other to screen out the best-performing algorithm. An algorithm is nothing but one of the horses in the “no free lunch theorem” horse race that a model allows to happen. Many of the algorithms used for classification can also be used for regression (see Table 6.1)

  

6.2 REGRESSION MODELING

  

  

We will focus on linear regression primarily in this section, but the topic belongs to the larger category of Regression Analysis defined as “a set of statistical processes for estimating the relationships between a dependent variable and one or more independent variables.” ¹ As shown in Table 6.1 many other algorithms also apply to regression and should be used to compete against the Linear Regression widget in a model workflow.

Table 6.1 Algorithms used for classification, regression, or both

  

 
| Algorithm || Indication |
| --- | --- |
| Linear, Ridge, Lasso, and Elastic net regression || R |
| Logistic, Ridge, and Lasso regression || C |
| Naive Bayes || C |
| Decision trees || C,R |
| Random forest || C,R |
| AdaBoost || C,R |
| Gradient boosting || C,R |
| Xgboost || C,R |
| Neural networks || C,R |
| k-nearest neighbor || C,R |
| Support vector machine || C,R |

  

C = classification R = regression

  

#### 6.2.1 Linear regression

  

“Linear regression attempts to model the relationship between two variables by fitting a linear equation to observed data. One variable is considered to be an explanatory variable, and the other is considered to be a dependent variable. For example, a modeler might want to relate the weights of individuals to their heights using a linear regression model.” ²

Unlike classification, the outcome or Y variable is numerical/continuous such as cost, length of stay, heart rate, agricultural yield, energy production, number of cars sold, etc.

  

#### 6.2.2 Simple Linear Regression (SLR)

  

SLR models show if one x variable is related to one y variable, which is why it is called “simple.” The purpose of SLR is to create a scatter plot and a resulting regression equation that describes the best-fit line that best represents the data.

A linear regression best-fit line has an equation of the form Y = a + bX, where X is the explanatory (predictor or independent) variable and Y is the dependent variable. The slope of the line is b, and a is the intercept (the value of y when x = 0). With simple linear regression, a correlation coefficient is generated as shown in Figure 6.2. In this scenario, there is a strong positive correlation of 0.83.

It is important to understand the difference between correlation and regression.

Correlation: It represents the relationship between two variables which may or may not be causal. The strength of this relationship is represented by the correlation coefficient r, which can range from -1 to +1. A negative correlation means that as x increases, y decreases. In a positive correlation, x and y increase. Correlation analysis is typically done as a data mining and data exploration exercise that includes an analysis of all predictors, correlated with the target variable, one at a time.

Regression: It is typically used when there is some stronger indication that there is a causal relation between an x and y. The purpose of regression analysis is to create a regression equation that represents the best-fit line that matches the data. The strength of this relationship can also be represented as r (in Orange) but it is more typical to represent the x and y relationship as R², which JASP calculates. R² ranges from 0 to 1 whereby 0 represents no relationship between x and y while 1 represents a situation where every data point perfectly matches the best-fit line. ³ Orange reports R² in the Test and Score widget.

In Figure 6.2, there is a relationship between how many weeks someone has worked and their accumulated savings. Using the linear equation, you could input the number of weeks (X) as 10 and see the accumulated savings would be 400 + 307.50 (10) or $3470.50. In other words, you create the mathematical model and then fit new data to the model to see how accurate the prediction is.

The next thing to appreciate is the fact that most data points are not exactly on the regression line. They may be e.g., 100 above (+) or below (-). The difference between the data point and the regression line is called the residual, or error, which is the vertical difference between the best fit line and the actual data point. In order that you don’t have negative numbers, the residuals are squared. (-2 squared = 4).

[Figure 6.3 shows an Orange scatter plot with the Orange r value for the regression line as well as the regression equation that has been established from the Model Summary and Model Coefficients outputs calculated from JASP. As shown in the figure, the relationship between abdomen circumference and percent body fat is represented by a r value of 0.81, and an R² of 0.66. The regression equation is statistically significant with a p-value below 0.05. That means we reject the null hypothesis that there is no significant relationship between the predictor and the outcome/target. The steps to create this regression analysis in JASP are shown here:](#content0171.xhtml)

Regression > Linear Regression > enter Percent Body Fat for Dependent Variable > enter Abdomen circumference for Covariates > check: Include intercept, Model Fit, and Estimates.

  
![](images/image-ODGARHPT.png)  

Linear Regression (StatQuest)

  
![](images/image-WLVIXROH.jpg)  

Figure 6.2 Simple linear regression (courtesy Boston University School of Public Health)

  
![](images/image-3FWBJDL5.jpg)  

Figure 6.3 A linear regression equation calculated in JASP

  

#### 6.2.3 Multiple Linear Regression (MLR)

  

MLR models the linear relationship between the explanatory (independent)

(X) variables and the response (dependent) (Y) variable. The formula is as follows:

•y = the predicted value of the dependent variable

  
![](images/image-RELHIPU3.png)  

•B0 = the y-intercept (value of y when all other parameters are set to 0)

•B1X1= the regression coefficient (B1) of the first independent variable (X1) (the effect that increasing the value of the independent variable has on the predicted y value)

  

![](images/image-TEMD15Y1.jpg)You need to calculate the regression coefficient for each independent variable separately, considering its unique effect on the predicted value of y.

•BnXn = the regression coefficient of the last independent variable

•e = model error (a.k.a. how much variation there is in our estimate of y)

Multiple regression calculates the following:

•The regression coefficients that lead to the smallest overall model error.

•The t-statistic of the overall model.

•The associated p-value (It determines the statistical significance of the relationship between each independent variable and the dependent variable, providing insights into the strength and reliability of the regression model.

•Variance Inflation Factors (VIFs) for each predictor.

•See Figure 6.4 for a 3-dimensional display for two predictors (Weight and Horsepower) and the target variable (MPG). Such displays are always useful to display the visual relationships between the top-ranked predictors and the target variable in an MLR model.

Multiple linear regression and VIFs were covered in great detail in section 2.4.2. However, it is at least worth repeating the command steps for creating MLR in JASP as well as some analysis tips, as mentioned below.

•Go to JASP > select Regression > linear logistic regression > enter the target in the Dependent Variable section > enter all continuous variables in the Covariates section > enter the categorical factors in the Factors section > Statistics > check Estimates and Model Fit > check Collinearity diagnostics to get the VIFs (Variance Inflation Factors) > consider removal of predictors with VIFs > 5, starting with the predictors that also have the highest p-value > look at the p-value on the ANOVA table to see if the whole model is statistically significant (p-value < 0.05), then look at the Coefficients table to see the p-values for each entered factor after all predictors with high VIFs have been removed > remove any variable from the input list that has a p-value greater than 0.05 but do this one factor at a time, starting with the highest p-value.

  
![](images/image-6WJJZDVI.png)  

Figure 6.4 Multiple linear regression ⁴

  

•It is possible to have two variables with very high VIFs and they both have a very low p-value (<0.05). In such a case you need to delete one of the variables. Keep the one variable that makes the most sense for your model and makes the most sense to your stakeholders. When you delete the second variable, the VIF values should now be below 5.

•When all p-values are below 0.05 on the Coefficients table, you now have a final valid regression model. Check if all VIFs are below 5. If not, you have multicollinearity to deal with. The model and the variable ranks will not be correct unless all VIFs in the model are below 5.

Linear regression as well as multiple linear regression has several assumptions that have to be met in order for the results of the model to be valid and reliable:

•Homogeneity of variance (Homoscedasticity): the size of the error (residuals) in the prediction doesn’t change significantly across the independent variables.

•Independence of observations : there are no hidden relationships among variables. If two independent variables are too highly correlated (VIF > 5), then only one of them should be used in the regression model.

•Normality : The residuals should have a normal distribution.

•Linearity : The relationship between individual predictors and the outcome have to be linear. In other words, the line of best fit through the data points is a straight line; not a curve.

•Outliers : Extreme outliers can have a big impact on the performance of a regression model so they must be dealt with appropriately.

  
![](images/image-RSEB95LK.png)  

Multiple Linear Regression (StatQuest)

  

#### 6.2.4 The Dummy Variable Trap

  

The Linear regression widget automatically converts categorical data to continuous data using the “One attribute per value” (aka one hot encoding) method which creates an additional column for each categorical variable. This is done since many algorithms cannot deal with a column of categorical information and need that information converted to a series of 1/0 (yes/no) numbers. However, converting every categorical variable into a column of its own can lead to a common issue known as the “Dummy Variable Trap” since it introduces redundancies of information into the dataset that can cause multicollinearity and other performance issues with certain algorithms.

In other words, with the best intentions, we tried to do the right thing by first making the algorithms happy by converting all categorical text into separate columns of 1/0 (one hot encoding), and unintentionally created other issues for many algorithms with one hot encoding.⁵

Orange leaves it up to the user to know what risks they may be taking and how to avoid them. Orange allows us to override this one hot encoding default settings with this tip: “To remove default preprocessing, connect an empty Preprocess widget to the learner.” You can also override this default by adding the Preprocess or Continuize widget in front of the Linear Regression widget which offers a different handling of the categorical variables.

The Preprocessing and Continuize widgets have settings that can avoid the dummy variable trap by creating one column less than what would normally be created with one hot encoding. These techniques are called n-1 or “First value as base” or “Most frequent as base” in Orange under the categorical features options. For example, the heart disease prediction dataset has a column “gender” and patients are categorized as “male” or “female” in that column. If you select “One attribute per value” (one hot encoding) in Orange, you will get two columns. One column will have the header “gender = female” and the other will say “gender = male” and the cells in the column will have either a 1 or 0 for yes or no. This creates the dummy variable trap. To avoid this trap you select “Most frequent as base” and then the result is only one column with the header “gender = female” with zeros and ones in the cells. This is also referred to as “n-1” (aka: Dummy encoding) since it reduces the total number of columns to be split out by one.

Regression analysis assumes and requires that independent variables (predictors) are present for the analysis but one hot encoding can disrupt that assumption by creating a specific column for each subgroup in a categorical column. Going back to the gender example, you don’t need both genders dummy coded in separate columns for a regression model. You only need one of them encoded as a yes/no which will automatically include the other gender.

If you take the heart disease dataset in Orange and one hot encode the categorical variables, you will get two columns for gender and all other categorical variables will also get a column for each possibility listed in the original categorical column. If you then try to do statistical (non-machine learning) multiple linear regression in JASP, you will get a long error message that shuts down the analysis. Part of this error message will say:

“! The following problem(s) occurred while running the analysis: The following pair(s) of variables is/are perfectly correlated: gender=female and gender=male; fasting blood sugar > 120=0 and fasting blood sugar > 120=1; exerc ind ang=0 and exerc ind ang=1.”

Machine learning algorithms in Orange will not offer such a warning or stop you from proceeding since not all algorithms are affected the same way by the dummy variable. The best practice to avoid this risk is to apply dummy encoding which would avoid the above-mentioned error message in JASP.

In summary, “Dummy encoding” is a method to avoid the Dummy variable trap which is caused by “one hot encoding.” ⁶-⁷

  

#### 6.2.5 Logistic Regression

  

While some may think that logistic regression makes sense to be first introduced here in detail, we chose to introduce and discuss it in previous classification and modeling chapters due to the great burden that is put on physicians, clinicians, and other subject matter experts from industries where logistic regression is commonly needed for rapid decision-making. Logistic regression helps to predict a binary or multi-class diagnosis and needs to be discussed early and often.

  

#### 6.2.6 Polynomial Regression

  

This type of regression is similar to simple linear regression but the regression line is curved in order to handle non-linear data relationships. The “least squared” statistical method is used to identify the exact shape of the polynomial curve. When the polynomial order is set to 1, it is the same as simple linear regression. Figure 6.5 displays a simple linear model and a polynomial model. As you increase the polynomial order, the line fits the data better, but at some point you tend to model the noise as well, thus leading to overfitting when a higher polynomial order is chosen than what naturally fits the general shape of the data. Orange has a Polynomial Regression widget in the Educational add-ons. You can create data points with the Paint Data widget and then connect that to the Polynomial Regression widget for line fitting. When you connect the latter to a Data Table widget you can see the regression coefficients.

  
![](images/image-WV4H234Y.png)  

Figure 6.5 Simple linear and polynomial models

  

#### 6.2.7 Linear Regression Model Regularization

  

Regularization is a technique to decrease overfitting by introducing penalty terms to encourage the model to prioritize simpler models that improve generalization. This reduces the variance (overfitting) in the model and doesn’t increase bias (underfitting) substantially. When you select and open the Linear Regression widget you have four regularization choices: no regularization, ridge regression, lasso regression, and elastic net regression.

  

6.2.7.1 Ridge Regression

  

Ridge regression is an L2 regularization method that improves model generalization, particularly in situations where there is multicollinearity. It shrinks the model coefficients toward zero to reduce the impact of individual predictors. In Orange, you have control over the strength of the regularization you want to add to the model for Ridge regression. The method is especially popular when the number of predictors is larger than the number of observations. ⁸

  

6.2.7.2 Lasso Regression

  

Lasso stands for Least Absolute Shrinkage and Selection Operator. It is an L1 regularization method that applies a penalty that is equal to the absolute value of the magnitude of the coefficient. It sets coefficient values to zero for low-importance and high multicollinearity predictors which eliminates their impact on the model while still allowing that column of data to be included in the model. In Orange, you have control over the strength of the regularization you want to add to the model for Lasso Regression.This regularization type can result in simpler and sparser models with fewer features that are deemed as significant.⁹

  

6.2.7.3 Elastic Net Regression

  

Elastic net regression is a penalized linear regression model that includes both L1 and L2 penalties during training to balance the strength of The Ridge and Lasso methods as a hybrid approach.¹⁰ In Orange, you have control over the mix of L1 and L2 regularization you want to add to the model. In the JASP Machine Learning module, you can select Regularized Linear Regression and select the option to automatically optimize the regularization level (lambda) in the Training Parameters section. This will create a model with the lowest possible error. This option is available for Lasso, Ridge, or Elastic Net regression.

In summary, you should always start your modeling journey with simple multiple regression in JASP to identify the VIF levels in your dataset which will tell you the level of work that is required in order to achieve a model free of multicollinearity. You should not feel forced to make a decision on which regularization algorithm to use at the start of modeling. The modeling process is a competition between many algorithms and algorithm options. Each of these before-mentioned methods should be compared to each other to see how they perform and each of their variable ranks should also be compared against each other. You may also want to experiment with different regularization strengths for Ridge and Lasso methods, as well as testing different Elastic Net mixing ratios in your pursuit of the best-performing model.

  
![](images/image-KE2EG340.png)  

Ridge vs Lasso Regression (StatQuest)

  
![](images/image-3BSDT6QK.png)  

Elastic Net Regression

  

#### 6.2.8 Regression Performance Metrics

  

The performance measures for regression are different from classification and the common ones are MAE (mean absolute error), RMSE (root mean square error), MSE (mean squared error) and R2 (R squared). For an example of how to calculate the first three metrics, let’s assume that the residuals or errors of three data points are: -2, 1, and 5.

MAE “is basically the absolute difference between actual values and predicted values of the model. So the mean absolute error or MAE is the error that takes the average of this error from every sample in the dataset.” ¹¹ Using the example residuals, MAE would be calculated as 5 + 1 + 2 divided by 3 = 2.67. The lower the better.

MSE “is the error calculated by taking the average of the square of the difference between actual and predicted values.” ¹¹ Using the example residuals, MSE would be calculated as follows (-2)² + 1² + 5² =30. MSE would be 30/3 = 10. The lower the better.

RMSE “is the standard deviation of the errors which occur when a prediction is made on a dataset. This is the same as MSE (Mean Squared Error) but the root of the value is considered while determining the accuracy of the model.” ¹¹ Using the example residuals, the RMSE would be the square root of MSE (10) or 3.16. The lower the better.

R squared “is also known as the coefficient of determination. The R squared value lies between 0 and 1 where 0 indicates that this model doesn’t fit the given data and 1 indicates that the model fits perfectly to the dataset provided.” ¹¹ Be aware that some programs (not Orange) also include an adjusted R squared that adjusts the statistic based on the number of independent variables in the model. The problem with R squared is “it either remains the same or increases with the addition of new independent variables. This clearly does not make sense because some of the independent variables might not be useful in determining the target variable.” Adjusted R-squared deals with this issue. ¹¹ Although R squared values range between 0 and 1, they are usually stated in percentages ranging from 0% to 100%.¹²

  
![](images/image-130XV16G.png)  

R Squared (StatQuest)

  

The two measures most people pay attention to are RMSE and R2 when they compare several models. For RMSE, the lower the better. R2 on the other hand, ranges from 0 to 1 and the higher the better. An R2 value of 1 would mean a perfect model where the outcome is 100% predictable.¹³

  

6.3 PUTTING KNOWLEDGE INTO PRACTICE

  

  

#### 6.3.1 Exercises

  

6.3.1.1 Classification

  

This exercise will focus on predicting employee attrition. You will find this dataset in the Dataset widget titled Attrition-train (not Attrition-Predict). Further information is provided in the bottom of the Dataset widget page. Double-click on the dataset to load it. Next, connect the Dataset widget to the Data Table and Box Plot widgets.

1\. Review the data in the Data Table widget. How many rows and columns are there? Is there missing data? What is the target? How many columns of categorical data vs numerical data are there?

2\. In the Box Plot widget, determine the number of employees who attrited vs did not attrite. Is there class imbalance?

3\. Connect the Dataset widget to the Edit Domain widget because we want to change the target/outcome from Yes to 1 and No to 0. This will help the analysis when we analyze this dataset in JASP:

a. In the Edit Domain widget select Attrition in the left window. Under Values double-click on No and replace it with 0 and double click on Yes and replace it with 1. Hit apply

b. Connect the Continuize widget to the Edit Domain widget and select “First value as base” for the categorical values.

c. Connect the Continuize widget to a Data Table widget and confirm you now have converted the categorical variables to numerical values and the target column now consists of 1’s and 0’s.

d. Connect the Data Table widget to the Save Data widget and save the file as Attrition\_Dummy\_Coded.

4\. Upload the saved file to JASP

a. Select Linear Regression. Select Attrition as the Dependent Variable and everything else as a Covariate.

b. Scroll down to Statistics and check the box “Collinearity diagnostics.” This will take several minutes and generate a table to the right.

c. How many VIFs are over 5? How many have p values > .05?

d. Start with the highest VIF with the highest p value over .05 and remove it from the model and then reassess the VIFs. Remove the VIFs over 5 with high p values one at a time until all VIFs are under 5. How many did you remove?

5\. Upload the Attrition\_Dummy\_Coded file into the Orange File widget.

a. Open the File widget and review. Change any variable that you excluded in JASP to “skip.” These variables will not be part of the model.

b. Set target = Attrition

c. Hit the Apply button

6\. Connect the File widget to the Data Sampler widget and set for a 75/25 split and “stratify sample.” Connect the Data Sampler widget to the Test and Score widget and be sure one connector is labeled “remaining data” to “test data.”

7\. Connect to the Test and Score widget a variety of algorithms from different families, e.g., tree based, ensembles, logistic regression with different regularization methods, Naive Bayes, neural network and so forth.

a. Connect the Feature Importance widget to one algorithm using the workflow described in Section 5.5.2 in Chapter 5. What were the top 3 predictors for attrition?

b. Open the Test and Score widget. Set the target to 1 and cross validation to 10.

c. Do the performance scores suggest class imbalance? If so, what are the best performance measures to monitor? Which algorithm produced the best F1 score?

d. Connect the Performance widget to the Test and Score widget. Be sure target = 1 and Curve = precision recall. Which algorithm produced the highest AUPRC?

e. Record the F1 score for logistic regression and random forest. Select the “balance class distribution” in both widgets and re-assess the F1 score. How much did they improve?

8\. Connect the Calibration plot to the Test and Score widget and open

a. Set the target = 1 and begin analyzing the curves one at a time to see if any are close to the 45 degree line to suggest the predicted probabilities are close to the actual probabilities. Which one was best?

9\. Calculate the optimal ROC threshold using either the precision recall curves in the Calibration Plot or calculate the Geometric Mean as explained in Chapter 4 in section 4.7.2.9.

  

6.3.1.2 Regression

  

Exercise with synthetic painted data

We can create a simple linear regression model using the Paint widget. Open this widget and get rid of C2 by selecting the minus button. Left-click on the canvas and add roughly 50 blue data points in a linear fashion as seen in Figure 6.6. Connect the Paint widget to a Select Columns widget and be sure the y variable is set to target. Connect to the Test and Score widget and connect the latter to the Linear Regression widget. How good was the performance? Note the workflow in Figure 6.7 and performance in Table 6.2. The RMSE is quite low and the R2 high, indicating a good regression model. The data table reports the y-axis intercept of 0.045 and x of 0.93. You have the option in the Paint widget of creating a “sloppier” curve with more variation and then observing the performance degrade.

  
![](images/image-B7SLZDU1.png)  

Figure 6.6 Simple linear regression with synthetic painted data

  
![](images/image-PJOH5M6Z.png)  

Figure 6.7 Regression workflow

  

Table 6.2 Regression results

  
![](images/image-UZGEQZAY.png)  

Exercise with non-synthetic data

For this exercise we will create a regression model based on an NHANES (National Health and Nutrition Examination Survey) dataset. NHANES is a treasure trove of qualitative and quantitative data on US patients that is publicly available for download.¹⁴ Multiple NHANES data files were combined to create a dataset that includes about 4500 adult patients with 68 predictors that is stored on our File-Share website.¹⁵ We will build a regression model to predict grip strength, as this measure correlates with morbidity (health status) and mortality (death). Combined grip strength is the outcome of interest and it is measured in kilograms and the range is 11-169 kg.¹⁶ Keep in mind the predictors should be numerical and that the linear regression widget has several automatic default preprocessing steps that it completes behind the scenes: a. imputation of missing values b. use of “one hot encoding” to convert categorical values to numerical c. removal of rows with no outcome variable d. removal of empty columns.

Download the NHANES dataset and upload it to the File widget. Open and change the following:

•To the right of grip\_strength click on “feature” and change it to target.

•Change seqn, first, last, and drugs to “skip” and then select Apply. Confirm the changes by connecting a data table to the file widget

•Connect the Data Sampler widget to the File widget and select the Sample Data button . Connect two connectors to the Test and Score widget. Set the connectors as Data sample >> data and remaining data >> test data

•Connect the Linear Regression widget to the Data Sampler and the Test and Score widgets. Open the Linear Regression widget and select elastic net regression. Realize that you can compare the results with all of the regularization options by creating a separate widget for each regularization option. In the last example you will want to right click on the extra widgets and give them custom names such as no reg, lasso, ridge, and elastic net. This will force the Test and Score widget to label them in the scorecard table which makes it easier to compare the results.

•Connect a Data Table widget to the Linear Regression widget in order to view the regression coefficients

•Double click the Test and Score widget and select cross-validation at the top to obtain the training performance. Then compare that with the test data performance by selecting the “Test on test data” option at the bottom.

[•Figure 6.8 displays the workflow for this exercise and Table 6.3 displays the training performance for linear regression. The training performance is good with an R squared of 0.727 with little change in the test data.](#content0179.xhtml)

  
![](images/image-0G2C32TE.png)  

Figure 6.8 Regression workflow

  

Table 6.3 Training results for linear regression

  
![](images/image-8SYHYIK9.png)  

Open the Data Table widget connected to the Linear Regression widget and click on coefficients and it will sort them by the most negative to the most positive or vice versa. In multiple linear regression, the coefficient tells you how much the dependent variable (target) is expected to increase when that independent variable increases by one unit of its described measure, “holding all the other independent variables constant.” ¹⁷ Using Figure 6.9 as an example, if the height increases by one centimeter you would expect the grip strength to increase by 0.33 kg. Note the negative and positive coefficients. See Figure 6.9 where the top 15 positive coefficients are listed. You could experiment with regularization and see how the coefficients and model performance change.

  

#### 6.3.2 Maturity Levels

  

Three e-commerce websites are creating a prediction model for determining the likelihood of a user making a purchase based on their browsing behavior. Each of these websites utilizes different modeling strategies that can be best described as low, mid, and high levels of modeling maturity, as described below:

  
![](images/image-PUHJHNOS.png)  

Figure 6.9 Regression coefficients with linear regression and elastic regularization

  

Low Maturity example: An e-commerce website collects data on three attributes: page views, time spent on the website, and the type of products viewed. They decide to use a basic decision tree without accounting for potential overfitting or explaining their model to the marketing team.

•Warning!

•The team’s approach seems overly simplistic for a complex decision-making process like purchasing behavior. Without considering a broader set of variables or ensuring model robustness, there’s a high risk of poor prediction accuracy. Also, the lack of transparency to stakeholders can raise questions on the reliability of the model’s predictions.

Moderate Maturity example: This e-commerce site gathers data on seven user attributes, including search history, product reviews read, and previous purchase history. They use both linear regression and support vector machines (SVM) for their model. They apply basic feature selection methods and provide a variable importance plot to their sales team.

•Caution!

•They’re on the right track by considering more variables and using multiple algorithms. However, they might be missing out by not exploring other machine learning techniques or ensuring model validation through techniques like cross-validation. To further enhance the model, they might consider deep learning techniques or more advanced ensemble models tailored for e-commerce settings.

High Maturity example: This e-commerce giant considers 20 user attributes, such as page views, time spent, type of device used, search history, click-through rate, cart abandonment rate, and many more. They experiment with 20 different algorithms, and algorithm options, including ensemble techniques. They rigorously validate their models using K-fold cross-validation, ensure that overfitting with regularization, and present an extensive explainability dashboard to stakeholders, showcasing how each variable impacts purchase predictions.

•Congratulations!

•By diving deep into the data and exploring a wide variety of modeling techniques, this e-commerce website is well-positioned to predict user purchase behavior accurately. Their commitment to transparency and model validation ensures stakeholders can trust and act on the model’s predictions with confidence.

  

#### RESOURCES

  

  

1\. Validation methods https://www.mygreatlearning.com/blog/cross-validation/

2\. Overfitting https://elitedatascience.com/overfitting-in-machine-learning

3\. Unbalanced datasets and what to do about them https://medium.com/strands-tech-corner/unbalanced-datasets-what-to-do-144e052d9cd

4\. Ensemble methods: A Comprehensive Guide https://analyticsindiamag.com/comprehensive-guide-to-ensemble-methods/

5\. Multi-Class Classification. https://analyticsindiamag.com/guide-to-multi-class-classification/

6\. An empirical evaluation of imbalanced data strategies from the practitioner’s viewpoint.

7\. https://arxiv.org/abs/1810.07168

8\. Guide to Classification of Imbalanced Datasets https://towardsdatascience.com/guide-to-classification-on-imbalanced-datasets-d6653aa5fa23

9\. The difference between R squared and adjusted R squared. https://www.analyticsvidhya.com/blog/2020/07/difference-between-r-squared-and-adjusted-r-squared/

  

#### REFERENCES

  

  

[1\. Regression analysis \[Internet\]. \[cited 2022 Apr 5\]. Available from: https://en.wikipedia.org/wiki/Regression\_analysis](#content0169.xhtml)

[2\. Linear Regression \[Internet\]. \[cited 2022 Apr 5\]. Available from: http://www.stat.yale.edu/Courses/1997-98/101/linreg.htm#:~:text=Linear%20regression%20attempts%20to%20model,to%20be%20a%20dependent%20variable .](#content0170.xhtml)

[3\. Goyal C. Test Your Skills on Linear Regression Algorithm \[Internet\]. Analytics Vidhya. 2021 \[cited 2022 Apr 27\]. Available from: https://www.analyticsvidhya.com/blog/2021/06/25-questions-to-test-your-skills-on-linear-regression-algorithm/](#content0171.xhtml)

[4\. Multiple Linear Regression. Mathworks.\[Internet\]{cited 2022 May 30\] Available from: https://www.mathworks.com/help/stats/regress.html](#content0172.xhtml)

[5\. Mahto KK. One-hot-encoding, multicollinearity and the dummy variable trap \[Internet\]. Towards Data Science. 2019 \[cited 2023 Mar 7\]. Available from: https://towardsdatascience.com/one-hot-encoding-multicollinearity-and-the-dummy-variable-trap-b5840be3c41a](#content0173.xhtml)

[6\. Karabiber, Fatih. n.d. “Dummy Variable Trap – LearnDataSci.” \[Internet\] \[cited 2022 Sept 11\]. Available from: https://www.learndatasci.com/glossary/dummy-variable-trap/](#content0173.xhtml)

[7\. Pramoditha R. Encoding categorical variables: One-hot vs dummy encoding \[Internet\]. Towards Data Science. 2021 \[cited 2023 Mar 7\]. Available from: https://towardsdatascience.com/encoding-categorical-variables-one-hot-vs-dummy-encoding-6d5b9c46e2db](#content0173.xhtml)

[8\. Wikipedia contributors. Ridge regression \[Internet\]. Wikipedia, The Free Encyclopedia. 2022. Available from: https://en.wikipedia.org/w/index.php?title=Ridge\_regression&oldid=1128872620](#content0176.xhtml)

[9\. Wikipedia contributors. Lasso (statistics) \[Internet\]. Wikipedia, The Free Encyclopedia. 2023. Available from: https://en.wikipedia.org/w/index.php?title=Lasso\_(statistics)&oldid=1134655874](#content0176.xhtml)

[10\. Wikipedia contributors. Elastic net regularization \[Internet\]. Wikipedia, The Free Encyclopedia. 2023. Available from: https://en.wikipedia.org/w/index.php?title=Elastic\_net\_regularization&oldid=1136316710](#content0176.xhtml)

[11\. Agrawal P. Metrics for Regression Model \[Internet\]. Analytics Vidhya. 2021 \[cited 2022 Apr 5\]. Available from: https://medium.com/analytics-vidhya/metrics-for-regression-model-84e3bc28fc7f](#content0177.xhtml)

[12\. Fernando J. Investopedia. 2003 \[cited 2023 Aug 20\]. R-squared: Definition, calculation formula, uses, and limitations. Available from: https://www.investopedia.com/terms/r/r-squared.asp](#content0177.xhtml)

[13\. Interpreting Regression Output \[Internet\]. \[cited 2022 Apr 19\]. Available from: https://dss.princeton.edu/online\_help/analysis/interpreting\_regression.htm](#content0177.xhtml)

[14\. National health and nutrition examination survey \[Internet\]. 2023 \[cited 2023 Aug 22\]. Available from: https://www.cdc.gov/nchs/nhanes/index.htm](#content0179.xhtml)

[15\. No Code Data Science \[Internet\]. \[cited 2023 Aug 22\]. File Share. Available from: https://www.nocodedatascience.net/file-share/abc85524-c67f-42bf-b3dc-74b23d38153](#content0179.xhtml)

[16\. NHANES grip strength 2011-2012. \[Internet\] \[cited 2022 June 21\]. Available from: https://wwwn.cdc.gov/nchs/nhanes/2011-2012/MGX\_G.htm](#content0179.xhtml)

[17\. Bajwa M. Breaking Down Linear Regression. \[Internet\]\[cited 2022 April 10\] Available from: https://medium.com/@mubarakb/breaking-down-linear-regression-269aa6cea220](#content0179.xhtml)

  

![](images/image-NA1XV4BG.jpg)Chapter 7

  

## Unsupervised Learning

  

“Data is the new oil.”

—Clive Humby

  
![](images/image-M6MTZISG.jpg)  
  

LEARNING OBJECTIVES

  
  

By the end of chapter seven readers should be able to:

•Compare supervised and unsupervised learning.

•Describe several use cases for unsupervised learning.

•Discuss how the silhouette score and plot help determine the best k value.

•Describe how the paint widget can create random clusters to analyze.

•Compare hierarchical clustering with k-means clustering.

•Compare agglomerative with divisive hierarchical clustering.

•Discuss why distance measurements are mandatory in clustering.

•Discuss how association rules are used in the business world.

•Explain how association rules could be applied to the medical field.

•Describe support, confidence, and lift.

  
  

Chapter 7 Summary

  

  

This chapter will discuss unsupervised learning, where there is not a designated target or outcome. In unsupervised learning we want machine learning to find new and interesting groups (clusters), and patterns among the data. Compared to supervised learning, this approach is used infrequently in medical research but is commonly used for customer segmentation, genetics, recommender systems, anomaly detection, preventative maintenance, and in many other areas. Unsupervised learning includes a trial-and-error analysis process, so it requires lots of data and patience. Not every dataset is amenable to clustering and this approach is considerably more complex than classification or regression. Nevertheless, the rewards could be great due to its ability to identify unexpected and unlabeled clusters, anomalies, and segments in data that can offer valuable insights for so many different applications and industries.

  

K-means clustering does require tweaking, whereas hierarchical clustering is one of the most intuitive unsupervised learning methods. Principal component analysis and association rules can also be useful analysis methods for unsupervised learning.

  

You will infrequently encounter a medical article that uses association rules but it is still worth knowing about. Like clustering, this process requires trial and error and domain expertise. Note: associations and correlations do not prove causation.

  

Key principles

•K-means and hierarchical clustering can be used as the first step to find small numbers of logical groupings of unlabeled data which is followed up by the tedious task of naming these latent unnamed clusters to make sense of the clustered groups.

•Principal Component Analysis (PCA) is another type of clustering that condenses high- dimensionality data into clusters that are split into smaller groups of priority-ranked components (clusters) which eliminates any multicollinearity present in a dataset. These new unnamed principal components will also need to be named in order for the analysis to have any practical and explainable value.

•Association rules are used as another unique way of clustering unsupervised data to discover which items or features frequently occur together to create good or undesirable events. For example, this technique can be used to identify frequently observed relationships between symptoms, diseases, and treatments that can be used to improve patient outcomes with these insights.

  

  

7.1 UNSUPERVISED LEARNING

  

  

Unsupervised learning on unlabeled data can be used as an exploratory tool to find patterns to explore in more detail. As a result, predictive variables can be reduced and explored further with classification, regression, or both.

Unsupervised learning is more difficult compared to supervised learning but has great potential to create additional insights. Currently, the most common application of this approach in the medical field is in analyzing genomic information where you want to determine if there are new groups/clusters of data based on genotypic, phenotypic, and demographic information. In healthcare, the most common uses of this approach are:

•Genomics

•Patient segmentation

•Disease clustering

•Medical imaging

•Natural language processing

•Anomaly detection

Other non-healthcare uses of clustering include:

•Recommendation systems

•Market segmentation

•Social network analysis

•Search result grouping

•Image segmentation

•Fraud detection

  

7.2 K-MEANS CLUSTERING

  

  

K-Means is the most commonly employed algorithm for clustering. This algorithm finds the center or centroids of the various clusters of data, as seen in Figure 7.1, and is represented as a black dot at the center of each group cluster, which is called the centroid. Data is assigned to clusters such that the sum of the squared distances between the data points and the centroid is as small as possible.

  
![](images/image-J98ANXER.jpg)  

Figure 7.1 Clustering

  

K-Means mandates that you determine the number of clusters (k) ahead of time. Realistically, most people try different k values to see what they find (e.g., 2, 3, 4, 5). If you are lucky, you might find the best k value from the beginning that matches your dataset, but do not expect that to happen often. Be aware that this can be a trial and error effort and some datasets will not easily expose hidden clusters which are not immediately apparent and easily distinguishable.¹ In Orange we will use the silhouette score and Silhouette Plot widget to help determine the optimal k value. An elbow plot is also used but not available in Orange. In unsupervised learning, the data must be numerical and normalized or standardized for clustering to be accurate and effective. Because clustering is about measuring distances between data points using linear algebra they must be normalized or standardized so that all distance measures are the same!

  
![](images/image-X67BM5OQ.png)  

K-Means Clustering (StatQuest)

  

#### 7.2.1 K-Means Clustering Exercises

  

7.2.1.1 K-means Clustering with Synthetic Data

  

To illustrate k-means clustering, we can use our Paint widget and create clusters. In Figure 7.2 three clusters were created (C1, C2, and C3).

Open the Paint widget and create three clusters, as shown in Figure 7.2. Connect the Paint widget to the K-means widget and open the latter. As you can see, the silhouette score is highest for three clusters when you select “From 2 to 8.” (Figure 7.3). The silhouette score is the mean silhouette coefficient over all dataset instances. The silhouette coefficient measures how close a point in one cluster is to points in the neighboring clusters, ranging from -1 to 1. A score of 1 means the clusters are far apart and a score of zero means there is little separation. Figure 7.3 shows the highest silhouette score for a three cluster scenario. When you connect to the Silhouette Plot widget, three clusters are also evident. (Figure 7.4).

  

When you open the Silhouette Plot widget you see that there are three fairly distinct groups. We don’t know the composition of these groups, just that there are three groups.

  

7.2.1.2 K-Means Clustering on the Wisconsin Breast Dataset

  

For this exercise, the Wisconsin breast histopathology data was chosen that is included in the Dataset widget. More information can be found on the UCI ML repository.² The goal of this dataset is to predict which cell nuclear characteristics predict benign vs. malignant tissue. We know ahead of time that the available predictors predict malignancy with a high rate of accuracy so there is good model “discrimination.” That means we should find two clusters: benign and malignant.

  
![](images/image-8CUMUAEA.png)  

Figure 7.2 Clusters created in the Paint widget

  
![](images/image-5UJCE2BF.jpg)  

Figure 7.3 k-means widget with silhouette scores

  
![](images/image-JCZX0G0X.png)  

Figure 7.4 Silhouette plot

  

Connect the Datasets widget to the k-Means widget and then double-click the latter widget. If you select “From 2 to 8” clusters it will help you decide the optimal number of clusters based on the highest silhouette score (0.564 in our scenario). The score indicates that 2 clusters are slightly better than 3 clusters. Connect the k-Means widget to the Silhouette Plot widget to see what the clusters look like (see Figure 7.5). Select distance = Euclidean, Grouping = Cluster, check the box “Show in groups”, Bar width = 1 and Annotations = none. Note that the light-colored (blue) cluster 1 outnumbers the dark-colored (red) cluster 2.

  
![](images/image-M5WQB4M2.png)  

Figure 7.5 Silhouette plot

  

Also, connect Data Table, Distributions, and Scatter Plot widgets as shown in Figure 7.6. Highlight all data points in the lower dark (red) plot and then open the data table and you will see a new column “Cluster,” do you see the correlation between Cluster 2 and type? (Answer - C2 = malignant). Open the scatter plot and for the X axis, select Unif\_Cell\_Size, and for the Y axis select Unif\_Cell\_Shape. Color = Cluster. Are C1 and C2 well separated? When you color by Type, note that the scatter plot remains about the same, suggesting that Cluster 1 = benign and Cluster 2 = malignant. Try different combinations of variables or select FInd Informative Projections to see which variables have good separation. Next, open the Distributions widget and select type for variables and Split by = Cluster. What do you see? You confirmed that C1 is benign and C2 is malignant, but notice that there is not perfect separation. (see Figures 7.7 and 7.8). The cluster separation is easier to see if you select “Show color regions.”

  
![](images/image-L1W2NA7T.png)  

Figure 7.6 K-means workflow

  
![](images/image-OHJKQE08.jpg)  

Figure 7.7 Scatter plot from clustering

  
![](images/image-EV0RK7PA.jpg)  

Figure 7.8 Distribution plot from clustering

  

This was a relatively easy exercise. If you find clusters in another dataset that did not have a named class, you might find clusters but not know what makes up the clusters. Analyzing the clusters with data tables and box plots should be helpful to identify a customized name for that specific cluster of data.

  

7.2.1.3 Exercise on Florida County Health Ranking Data

  

For this exercise we will use County Health Ranking, a website that lists multiple (~40) self-rated objective health measures for each US county.³ In this dataset there is no target or outcome. There is a county ranking within each state but we will not be using the rank. The dataset we are going to use includes health measures for Florida’s 67 counties and can be downloaded from our file share site in the Chapter 7 folder. The name of the County and the actual rank have been deleted. Counties are numbered based on their alphabetical names. The question is, can we find any interesting groups or clusters in this dataset despite those deletions? Are counties different enough to be separable and able to form logical clusters? What do the counties in your state look like?

First, upload the file to the File widget then connect to the k-Means widget. Open the k-Means widget and select 2-8 clusters and look for the highest silhouette score which is cluster = 3. Next, connect the File widget to the Silhouette Plot widget. When you look at the silhouette plot you realize that there are only 7 entries in the cluster C3 so you may want to go with two clusters instead of 3. Open the K-Means widget and set fixed = 2. Connect the k-Means widget to the Data Table, Box Plot, Scatter Plot, and Distributions widgets:

1\. Data table: you will notice that the first column tells you who is in cluster 1 and who is in cluster 2 but you don’t know yet what are the characteristics of both groups.

2\. Box plot: under sub-groups select Cluster and then begin to look at the means of the different variables. For example - under rural, Cluster 1 is 14.5% rural and Cluster 2 is 69.5% rural. (p = 0.0000). Look at all of the variables to see what variables are significantly separated from one another to support the idea that they belong to different groups.

3\. Scatter plot : under Color, select Cluster and then compare variables. For example, select rural for the X-axis and percent PCP (primary care physician) for the Y-axis. What did you find? Experiment with other variable combinations and consider selecting the button “Find Informative Projections” to see other groupings.

4\. Distributions : split data by cluster and begin to compare Cluster 1 and 2. What about household income differences?

In Figure 7.9 the first 11 rows of the data table are shown displaying the cluster and Silhouette columns.

  
![](images/image-7OTXK5B6.jpg)  

Figure 7.9 Clusters and Silhouette scores

  

[Figure 7.10 displays a box plot of rural counties by cluster to show they are quite different (p-value < 0.05). C1 is 14.5% rural and C2 is 69.5% rural.](#content0186.xhtml)

  
![](images/image-ZPWHKVI9.jpg)  

Figure 7.10 Box plot of rural counties by cluster

  

[Figure 7.11 shows the distribution of children living in poverty to also suggest C1 is different from C2 with a lower percentage of children in poverty.](#content0186.xhtml)

  
![](images/image-5BFS2G0I.png)  

Figure 7.11 Percent children living in poverty

  

How many counties are in cluster 1 vs 2, and how are they different? What did you conclude and what might you report to state officials? Does Florida have counties that appear to be in better health than others? The answer is yes and this would likely pertain to most US States.

  

7.3 HIERARCHICAL CLUSTERING

  

  

There are multiple unsupervised learning methods but perhaps the easiest to understand and visualize is hierarchical clustering. Hierarchical clustering is another unsupervised learning technique that processes and organizes data into a dendrogram. See Figure 7.12. Unlike k-means clustering you do not have to decide the optimal number of clusters ahead of time which is a very useful feature. In the dendrogram in Figure 7.12, there are 4 major clusters with many sub-clusters.

This dendrogram came from a November 2021 article in JAMIA in which patients admitted to an ICU with COVID-19 underwent an unsupervised learning strategy to see if there were phenotypic subtypes. Using demographics, vital signs, lab results, and medications they identified 4 subtypes that had the outcome of either in-hospital mortality or prolonged ICU stay. “Sub-phenotype SP I (n = 233 \[22.5%\]) included patients with rapid respirations and a rapid heartbeat, but less need for invasive interventions within the first 24 hours, along with a relatively good prognosis. Sub-phenotype SP 2 (n = 418 \[40.3%\]) represented patients with the least degree of ailments, relatively low mortality, and the highest probability of discharge from the hospital. Sub-phenotype SP 3 (n = 259 \[25.0%\]) represented patients who experienced clinical deterioration during the first 24 hours of intensive care unit admission, leading to poor outcomes. Sub-phenotype SP 4 (n = 126 \[12.2%\]) represented an acute respiratory distress syndrome with an almost universal need for mechanical ventilation.” ⁴ Note the four clusters displayed in Figure 7.12. The far-left cluster in Figure 7.12 encompasses the others with the connecting line logic on the top. The final cluster hierarchy is in order from most dominant ones on the left and the least relevant one on the far right. The arrows on either side of the graph also describe the two types of clustering methods: Divisive and Agglomerative, which will be described further.

Agglomerative (Top-Down) Clustering: Agglomerative clustering starts by considering each data point as a separate cluster and then iteratively merges the closest pairs of clusters based on a similarity measure. It continues merging clusters until all data points belong to a single cluster. This process forms a hierarchy of clusters, with the final result being a dendrogram that shows the merging sequence.⁵

  
![](images/image-LHRPCG2T.jpg)  

Figure 7.12 Dendrogram from referenced article

  

Divisive (Bottom-Up) Clustering: Divisive clustering takes the opposite approach of agglomerative clustering. It starts with a single cluster containing all data points and then recursively divides the cluster into smaller subclusters based on dissimilarity. This process continues until each data point forms its own cluster or until a stopping criterion is met.

  
![](images/image-LTLCJMVC.png)  

Hierarchical Clustering (StatQuest)

  

7.4 PRINCIPLE COMPONENT ANALYSIS (PCA)

  

  

#### 7.4.1 Introduction

  

The “curse of dimensionality” means that datasets with excessive numbers of features (predictors) result in less accurate models because they also include more noise and the risk of overfitting. Some datasets do not initially have high dimensions but are then transformed to high- dimensionality datasets after the required n-1 dummy encoding of categorical variables. A column of ICD-10 codes for patients can create hundreds of additional columns if it is dummy encoded. In addition, high-dimensional datasets are slower to run and usually plagued with multicollinearity. Some have written that an ideal dataset has ten times as many observations (rows) as features (columns). One of the major techniques to reduce data dimensions is PCA, an unsupervised learning method where the predictors are reduced while as much valuable information as possible is retained in the remaining principal components.

With PCA, the data is transformed into principal components in which there are no unacceptable correlation levels between components. The principal components are sorted by their ability to explain the maximum level of variation in the data. An example of dimension reduction would be a standard 2-D photograph taken of 3-D subjects. You lose some depth but retain the most important information.

Linear algebra is applied heavily for PCA calculations and is also commonly used as the math behind many other data science techniques and algorithms. We won’t devote a module on linear algebra but it is crucial knowledge for effectively working with various types of data matrices. For example, linear algebra is:

1\. Used for PCA to create the components with the help of a covariance matrix, eigenvectors, eigenvalues, and other techniques.

2\. Used for word embedding in NLP. Words can be vectorized (transformed into numerical values) so they can be quantitatively analyzed.

3\. Used in image embedding for computer vision (image analytics) where images and their pixels are transformed into numbers that algorithms can analyze. Convolutional Neural Networks (CNNs) are commonly used for image classification and processing where images are converted to numbers for further analysis. CNNs have multiple layers of analysis that work together to convert data into a one-dimensional array for input into the next layer of analysis.

4\. Used for regularization or loss function in linear regression. The L1 norm is based on the Manhattan distance and L2 is based on Euclidean distance.

5\. Used in Support Vector Machines and many other algorithms.

  
![](images/image-WWQZT29V.png)  

Figure 7.13 Covariance and Correlation matrix ⁶

  

#### 7.4.2 Routine Steps to Achieve PCA

  

1\. Standardization: Variables have to be normalized or standardized so they are on the same scale.

2\. Create a covariance matrix: Variance is defined as the variation of single variables, whereas, covariance is how two variables vary together. Variance simply means how far the numbers are spread in a given dataset from their average value. Standard deviation is the square root of the variance. The covariance matrix is a table that summarizes all correlations among variables. Covariance refers to the measure of how two random variables in a dataset will change together. If the covariance is positive then the variables increase or decrease together; whereas if the covariance is negative, one variable increases while the other decreases (inversely). Figure 7.13 displays a correlation and a covariance matrix. There are three variables labeled 0, 1 and 2. Variables 0 and 1 are highly correlated (-0.95). In the covariance matrix, variance is listed on the diagonal, and variable 2 has the highest variance at 933.30. ⁶

3\. Calculate the eigenvectors and eigenvalues of the covariance matrix to determine the principal components. Principal components are new variables that are constructed as linear combinations of the initial variables. These combinations are done in such a way that the new variables (principal components) are uncorrelated and most of the information is compressed into the first component (showing the most variance). The second component has the second amount of variance and is calculated 90 degrees (orthogonal) from the first component so it is not correlated with the first component. The eigenvectors of the covariance matrix are the directions of the axes where there is the most variance (most information) and that is what we call principal components. Eigenvalues are simply the coefficients attached to eigenvectors, which represent the amount of variance carried in each principal component. By ranking your eigenvectors in order of their eigenvalues, highest to lowest, you get the principal components in order of significance. In the example we are going to present PC1 variance = 32%, PC2 = 14%, and PC3 = 11%. In Figure 7.14 there is a correlation plot between features 1 and 2. We see an arrow that begins in the middle of the data points and projects towards the upper right. That is an eigenvector = PC1. The arrow that points to the upper left is PCA 2.

  
![](images/image-B7M45Y64.png)  

PCA (StatQuest)

  
![](images/image-5QQQM9DP.jpg)  

Figure 7.14 Correlation plot of features 1 and 2

  

#### 7.4.3 PCA Exercises

  

7.4.3.1 County Health Ranking

  

Upload the Florida County Health Ranking dataset from the file-share site into the file menu and connect to the PCA widget. Connect the latter to a Data Table, Correlations, and Scatter Plot widgets. Open the PCA widget and you will see a Scree plot where you can select the number of components and the explained variance. Normalized variables should be checked. The widget will also impute missing values and use one-hot encoding for categorical variables. If you choose 8 components in the PCA widget, that will explain 80% of the variance which is a good starting point for further consideration. The cumulative variance is displayed on the upper line and the component variance on the lower line. You can manually move the vertical line to the right or left. See Figure 7.15.

  
![](images/image-EMAKV7QA.jpg)  

Figure 7.15 Scree plot

  
![](images/image-F611165E.jpg)  

Figure 7.16 PCA workflow

  
![](images/image-MQ0HH1L1.jpg)  

Figure 7.17 PCA output to data Table

  

Connect the Data Table widget to the PCA widget with two connections - transformed data to data and components to data. Transformed data are weights for individual instances in the new coordinate system, while components are the system descriptors (weights for principal components). Open the data table, select components and you will see a list of variances e.g. PC1 = 0.322 (32.2%). See Figures 7.16 and 7.17.

Next, look at the Correlations widget and you can see what features belong to PC1. See Figure 7.18

  
![](images/image-62BCVK3N.jpg)  

Figure 7.18 Correlations for PCA

  

7.4.3.2 Liver Mortality Dataset

  

Let us compare the results of classification with and without PCA. The dataset we will use predicts death from liver disease/hepatitis.⁷ The dataset can be downloaded from our File-Share site in the Chapter 7 folder. There are 19 predictors and the outcome is live or die. Using PCA we determine that 10 components will determine 77% of the variance. The workflow is shown in Figure 7.19 and a table comparing the results before and after PCA is displayed in Table 7.1. There is no significant improvement in the AUC or F1 score after reducing the components with PCA. You could increase or decrease the number of components and reassess. You also have the option of connecting the Correlation widget to the PCA widget to see what predictors are related to each PCA component.

  
![](images/image-F1SB9AKI.jpg)  

Figure 7.19 PCA workflow

  

Table 7.1 Classification results with and without PCA

  
![](images/image-0M5JOQAN.jpg)  

Using PCA does not guarantee improvement in the model’s performance, as its effectiveness depends on the dataset and underlying data structure. The selection of the optimal number of principal components and the decision to apply PCA can involve experimentation and evaluation using techniques such as scree plots, cumulative explained variance, and cross-validation. The decision to apply PCA should be based on careful evaluation rather than purely trial and error.

  

7.5 ASSOCIATION RULES

  

  

The best example of association rules is market basket analysis where a customer who buys X is more likely to buy Y. If you have ordered from Amazon you have experienced this at the bottom of the web page. Customers who buy a laptop are more likely to buy a mouse. This is an item set \[laptop, mouse\] where the laptop is the antecedent (preceding event) and the mouse is the consequent (following result). This is not cause and effect, just an association. Early clinical decision support was based on rules similar to association rules or “if-then” statements. For example, if the patient’s temperature is above 100 degrees, the pulse is above 100, and the blood pressure is below 110 systolic, then the patient may be septic. Today it is uncommon to see association rules reported in the medical literature. However, perhaps this is an overlooked analytical approach and is similar to a logical “if-then” grouping that a tree diagram produces.

Let’s provide an example of market basket analysis from a grocery store. Table 7.2 shows 10 baskets with a variety of items in each basket. We are going to focus on the association between Bread (A) and Milk (B).

There are three standard measures of association:

Support measures how frequent an itemset is in all the transactions. For example: itemset1 = {Bread or A} and itemset2 = {Milk or B}. Dataset1 will have a higher support number than itemset2. Support can be calculated for a single item or for an itemset. You can set a higher limit of support e.g. 10% so you investigate associations that are not rare. The default in Orange is 1%. Support = A + B/Total or 6/10 = 0.6

Confidence is the conditional probability of occurrence of a consequent given the antecedent. For example, what percent of milk purchases occur as a result of a purchase of bread?

  

Table 7.2 Market Basket Analysis

  
![](images/image-2XCN7E6W.jpg)  

Confidence = A + B/A or 6/9 = 0.66. Confidence does depend on the base popularity of both items, so the measure known as lift is also important.

Lift determines how likely item B is purchased when item A is purchased while controlling for how popular item B is. Lift = Confidence divided by (B divided by the total) or 0.66/0.6 or 1.11. A lift value greater than 1 means that item B is likely to be bought if item A is bought, while a value less than 1 means that item B is unlikely to be bought if item A is bought. This example looked at the association of bread and milk, but the association of bread and beer could also be calculated.⁸

Historically, the most common algorithm used for association rules was apriori but in recent years many (including Orange) have gone to the Frequent Pattern (FP) Growth algorithm. ⁹

  

#### 7.5.1 Association Rules Exercise

  

We will use the heart prediction dataset for this exercise that is in the File widget.

1\. First, connect the File widget to the Select Columns widget but do not include the variable about fasting blood sugar > 120 as we know that is not significant.

2\. Make diameter narrowing a feature and not the target so it can be included in the association rules calculation.

3\. Before using the Association Rules widget convert the numerical data into categorical data (discretize), required for association rules. Open the widget and select “Equal frequency discretization.”

4\. Connect a Data Table widget to see what the converted variables look like.

5\. Now connect the Association Rules widget. You will find it in the Options menu at the top >> Add ins >>Associate.

6\. Double-click the Association Rules widget to open. Set the minimum support level to 10% and minimum confidence to 90%. Select Find Rules and that will generate the Measures plus the antecedent and consequent statements. The analysis returns 159 rules!

The first rule (support = 0.294, confidence = 0.908) antecedent reads: major vessels colored=<0.5, thallium = normal, exercise-induced angina = 0 and the Consequent says diameter narrowing = 0. This means when the number of calcified coronary arteries is less than 1 and there is a normal thallium scan and no exercise-induced angina then you are not dealing with heart disease (diameter narrowing = 0)

The fifteenth rule (support = 0.185, confidence = 0.903) antecedent reads: chest pain = asymptomatic, exercise-induced angina = 1, gender=male and Consequent says diameter narrowing = 1. In other words, if the subject is male and does not have chest pain at rest, but does have exercise-induced angina, then the likelihood is that he has coronary artery disease (CAD).

Experiment with both support and confidence to see what you find. Figure 7.20 displays the workflow and Figure 7.21 hosts the first 15 generated rules.

The results are not revolutionary but this data science strategy could uncover new associations in datasets with unconventional data. Knowing how to use this method might prove useful on datasets where you are trying to find associations and create rules.

  
![](images/image-3372KW0A.jpg)  

Figure 7.20 Association rule workflow

  
![](images/image-DS17SA15.png)  

Figure 7.21 Association rule results

  

7.6 PUTTING KNOWLEDGE INTO PRACTICE

  

  

#### 7.6.1 Exercise

  

For this exercise we will again use the Florida County Health Ranking dataset. The ranking and name of the county have been removed. The 67 counties have been numbered based on their names in alphabetical order. Connect the Distances widget to the File widget and then connect the former to the Hierarchical Clustering widget. The Distances widget can measure the “distances’’ between rows or columns. Once again, linear algebra is performing the calculations. The measurement can be Euclidean, Cosine, etc. (look at the drop-down menu). When you open the Distances widget you will notice the default is to measure distances between row data using Euclidean distances. The Euclidean normalized box is checked. An explanation of Euclidean and Manhattan distances is displayed in Figure 7.22 and the workflow in Figure 7.23.

  
![](images/image-BMD4ZDTJ.png)  

Figure 7.22 Euclidean and Manhattan distances

  
![](images/image-IJNEQVPR.jpg)  

Figure 7.23 Hierarchical clustering workflow

  

Also connect the Distance Matrix (proximity matrix) widget to the Distances widget to see the calculated distances between predictors. Figure 7.24 displays the distance or proximity matrix between rows for a sample of predictors. Lower numbers indicate closer proximity between data points.

Open the Hierarchical Clustering widget, select complete linkage under Linkage and annotations = County No (number). It would be prudent to try more than one linkage method as they may yield different results. Select none for pruning, but under Selection, select Top N and see the difference between selecting 2 clusters versus 3. For the same reason we selected 2 clusters for k-means clustering, we will select two here. There are only 5 instances of C3. In the Distances widget select Rows and the Hierarchical Clustering widget shows two clusters with the county number on the right. See Figure 7.26.

Select columns in the Distances widget and see the results in Figure 7.27. Now you see the column attributes to the right for the two clusters. This tells you there are 11 predictors associated with cluster 1.

Connect a Data Table widget to the Hierarchical clustering widget and to a Box Plot widget. Open the Data Table and you will see a new column “cluster.” Open the Box Plot widget and select Cluster as the Subgroup. You can begin to compare the means of cluster 1 vs cluster 2. In Figure 7.25 there is a comparison of the percent that rated themselves as having “fair/poor health” for clusters 1 and 2. Consider looking at multiple predictors - comparing cluster 1 with cluster 2.

  
![](images/image-CGV47VR6.jpg)  

Figure 7.24 Distance Matrix widget results

  
![](images/image-R02EOC0T.jpg)  

Figure 7.25 Box plot of the rating fair/poor health by cluster

  
![](images/image-6I85MEJM.png)  

Figure 7.26 Dendrogram with county numbers

  
![](images/image-5PZOH6PS.jpg)  

Figure 7.27 Dendrogram with predictors for clusters 1 and 2

  

After several comparisons you will determine that Cluster 2 consists of traits that are less healthy. You can go back and see which county numbers are associated with each cluster. This should be of interest to any State Department of Health.

  

#### 7.3.2 Maturity Levels

  

•Low Maturity Example: A healthcare organization views the resolution of surgical site infections as a simple analysis exercise, and they view the unsupervised analysis of surgical site infection data in the same manner. They have a lot of unstructured data such as electronic health record (EHR) data, clinical notes, discharge summaries, surgical procedures, and many other unstructured information about patients.

With all of their available unstructured data, they only decided to analyze their EHR data with one analysis technique: k-means. They identified unique clusters of patients with k-means that have been diagnosed with surgical site infections but they did not do the analysis work to identify the practical names of those unnamed clusters. The result was that no useful trends, patterns, or root causes were identified or addressed. Their surgical site infection rates did not increase. They concluded that they were already doing everything possible to reduce surgical site infections and that no other improvements were possible.

oWarning!

•Superficial analysis combined with an underestimation of the task complexity can create the illusion of value-added analysis, but the real result is analysis activity without actionable insights, actions, or improvements.

•This organization only analyzed a fraction of its available unsupervised data with only one of the available techniques which resulted in no reduction in their surgical site infection rates.

•Moderate Maturity Example: A healthcare organization views the resolution of surgical site infections as a moderate complexity analysis exercise, and they view the unsupervised analysis of surgical site infection data in the same manner. They have a lot of unstructured data such as electronic health record (EHR) data, clinical notes, patient discharge summaries, surgical procedures, and many other unstructured information about patients.

With all of their available unstructured data, they only decided to analyze their EHR data and patient discharge summaries with two analysis techniques: k-means and hierarchical clustering. They identified unique clusters of patients that have been diagnosed with surgical site infections and identified the practical names of those unnamed clusters. The result was that some useful trends and patterns were identified and some improvements in the reduction of surgical site infection rates were achieved.

oCaution!

•Surgical site infections kill many patients and / or create great suffering for patients and their families. The analysis effort to reduce such issues should be taken very seriously.

•This organization only analyzed a portion of their available unsupervised data and did not conduct all of the analysis that could have resulted in some great best practices that they could have implemented for a greater reduction in their surgical site infection rates.

•High Maturity Example: A healthcare organization views the resolution of surgical site infections as a very serious and high complexity analysis exercise, and they view the unsupervised analysis of surgical site infection data in the same manner. They have a lot of unstructured data such as electronic health record (EHR) data, clinical notes, patient discharge summaries, surgical procedures, and many other unstructured information about patients.

With all of their available unstructured data, they decided to analyze all of their available unsupervised data sources with the following analysis techniques: k-means, hierarchical clustering, PCA, and Association Rules. They identified unique clusters and useful feature rankings for the various analysis methods they used for patients that have been diagnosed with surgical site infections. They also identified the practical names of unnamed clusters which created useful insights. The result was that several useful trends and patterns were identified and great improvements in the reduction of surgical site infection rates were achieved due to the implementation of various best practices.

oCongratulations!

•This organization took surgical site infections for their patients very seriously.

•This organization analyzed all of their available unsupervised data and conducted all of the analysis techniques available that resulted in the development of some great best practices that reduced their surgical site infection rates.

  

#### RESOURCES

  

  

1\. Understanding k-means clustering in machine learning https://towardsdatascience.com/understanding-k-means-clustering-in-machine-learning-6a6e67336aa1

2\. K-means clustering. Stat Quest https://www.youtube.com/watch?v=4b5d3muPQmA

3\. Comprehensive guide to k-means clustering. Analytics Vidhya. https://www.analyticsvidhya.com/blog/2019/08/comprehensive-guide-k-means-clustering/

4\. Machine learning - introduction to unsupervised learning https://vinodsblog.com/2018/11/01/machine-learning-introduction-tounsupervisedlearning/

5\. An introduction to clustering and different methods of clustering https://www.analyticsvidhya.com/blog/2016/11/an-introduction-to-clusteringanddifferentmethods-of-clustering/

6\. 17 Clustering algorithms used in data science and mining. Towards Data Science https://towardsdatascience.com/17-clustering-algorithms-used-in-data-science-mining-49dbfa5bf69a

7\. Silhouette Coefficient. Towards Data Science. https://towardsdatascience.com/silhouette-coefficient-validating-clustering-techniques-e976bb81d10c

8\. A Beginner’s Guide to Hierarchical Clustering. Analytics Vidhya. https://www.analyticsvidhya.com/blog/2019/05/beginners-guide-hierarchical-clustering/

9\. StatQuest. Hierarchical Clustering https://www.youtube.com/watch?v=7xHsRkOdVwo

10\. Association Analysis using Apriori Algorithm. https://medium.com/data-science-in-your-pocket/association-analysis-using-apriori-algorithm-with-example-8bb2ffed9dc

11\. Discovering interesting association rules in medical data. http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.700.3498&rep=rep1&type=pdf

12\. Exploring generalized association rule mining for disease co-occurrences. JAMIA 2012 https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3540474/

13\. Association Rule Mining on Medical Data to Predict Heart Disease. Please note the absence of clinicians as authors. http://www.ijstm.com/images/short\_pdf/1438960151\_P26-35.pdf

14\. Orange clustering videos https://orangedatamining.com/blog/2022/2022-25-11-clustering-videos/

  

#### REFERENCES

  

  

[1\. Determining k. \[Internet\]. \[cited 2022 Apr 28\]. Available from: https://www.maheshgoyani.in/resource/workshop/Determining%20K.pdf](#content0185.xhtml)

[2\. UCI Machine Learning Repository: Breast Cancer Wisconsin (Original) Data Set \[Internet\]. \[cited 2022 Apr 20\]. Available from: https://archive.ics.uci.edu/ml/datasets/breast+cancer+wisconsin+(original)](#content0186.xhtml)

[3\. How Healthy is Your County? \[Internet\]. County Health Rankings & Roadmaps. \[cited 2022 Apr 19\]. Available from: https://www.countyhealthrankings.org/county-health-rankings-roadmaps](#content0186.xhtml)

[4\. Oh W, Jayaraman P, Sawant AS, Chan L, Levin MA, Charney AW, et al. Using sequence clustering to identify clinically relevant subphenotypes in patients with COVID-19 admitted to the intensive care unit. J Am Med Inform Assoc \[Internet\]. 2021 Nov 23 \[cited 2022 Apr 28\];29(3):489–99. Available from: https://academic.oup.com/jamia/article-pdf/29/3/489/42333257/ocab252.pdf](#content0187.xhtml)

[5\. Karabiber F. Hierarchical clustering \[Internet\]. \[cited 2023 Aug 23\]. Available from: https://www.learndatasci.com/glossary/hierarchical-clustering/](#content0187.xhtml)

[6\. Stack Overflow \[Internet\]. \[cited 2023 Aug 23\]. Interpretation of covariance result matrix. Available from: https://stackoverflow.com/questions/51182476/interpretation-of-covariance-result-matrix](#content0189.xhtml)

[7\. University of California Irvine Machine Learning Repository. Hepatitis. https://archive.ics.uci.edu/ml/datasets/hepatitis](#content0191.xhtml)

[8\. Ng A. Association Rules and the Apriori Algorithm: A Tutorial \[Internet\]. KDnuggets. \[cited 2022 Apr 29\]. Available from: https://www.kdnuggets.com/association-rules-and-the-apriori-algorithm-a-tutorial.html/](#content0192.xhtml)

[9\. Website \[Internet\]. Available from: https://towardsdatascience.com/fp-growth-frequent-pattern-generation-in-data-mining-with-python-implementation-244e561ab1c3](#content0192.xhtml)

  

![](images/image-J54S6ZLI.jpg)Chapter 8

  

## Time Series Forecasting and Survival Analysis

  

“Time is a storm in which we are all lost”

—William Carlos Williams

  
![](images/image-M6MTZISG.jpg)  
  

LEARNING OBJECTIVES

  
  

After reading chapter eight readers should be able to:

•Understand the basics, pros, and cons, of ARIMA time series forecasting.

•Understand the various ARIMA settings and parameters that influence the forecasting model accuracy and graphical outputs.

•Optimize the performance of an ARIMA time series forecasting model in Orange with trial-and-error methods.

•Conduct Kaplan-Meier Survival Analysis.

•Correctly Interpret Kaplan-Meier Survival Analysis results.

  
  

Chapter 8 Summary

  

  

In this chapter we cover two critical statistical techniques used in data science. The first method is time series forecasting which can be applied in many different areas including finance, weather prediction, and any other topic of interest with a seasonal trend. We will also cover survival analysis, a method traditionally used in medical research but increasingly important in business, customer churn analysis, failure analysis, social sciences, and elsewhere. Here, we also discuss the core concepts such as censoring and the unique data collection requirements for survival analysis. Overall, this chapter provides an understanding of two interesting analysis techniques that can supplement predictive capabilities in data science.

  

Key Principles

•ARIMA is a well-understood, documented, and studied technique which only requires prior data to create a forecast.

•ARIMA is not a multivariate technique, has difficulty predicting time series turning points, multiple seasonality, and struggles with mean shifts.

•ARIMA takes time, experience, and trial-and-error to find the optimal model settings to create an optimal forecast.

•The methods used to determine the ARIMA p, d, and q parameters, and number of folds for cross validation are quite subjective.

•Known also as time-to-event analysis, the Kaplan-Meier survival analysis is a sophisticated statistical technique that focuses on examining the time period prior to the occurrence of a particular event of interest.

•Kaplan-Meier survival analysis is especially helpful in disciplines like reliability engineering for forecasting machinery maintenance schedules, medical research for evaluating patient survival rates, and in other areas.

  

  

8.1 TIME SERIES FORECASTING WITH ARIMA

  

  

ARIMA stands for Autoregressive Integrated Moving Average, which is a statistical analysis model used for time series forecasting. A statistical model is considered to be autoregressive if it attempts to predict future values only with the help of past time periods and no other considerations or predictors. ARIMA also uses a statistical concept called serial correlation which uses past data to predict future data trends. ARIMA makes the assumption that the future data trend will resemble the past which may prove to be inaccurate due to spontaneous economic, pandemic, and other unexpected crises. ARIMA is used in forecasting financial markets, stock prices, sales and marketing, demand forecasting, energy and utilities, tourism and hospitality, public health, disease outbreaks, resource allocations, telecommunication network traffic, weather forecasting, transportation, traffic patterns, and many other areas. It is particularly useful in projecting the recurrence of consistent seasonal and cyclical trends. This section will not cover the math behind ARIMA but rather the parameters in ARIMA that can be changed in the Orange widgets to improve forecast models that are measured with seven model performance metrics.

Time series forecasting is a serious business for so many professionals, especially for those in the financial, rideshare (UBER), retail and other sectors. The International Institute of Forecasters, M Open Forecasting Center (MOFC), Kaggle, and others offer more forecasting information, training, datasets, and competitions on the topic of forecasting. See these references for more details about the serious world of time series forecasting.¹-²

  

#### 8.1.1 Arima Time Series Forecasting in Orange

  

As we explore the ARIMA time series forecasting options in Orange, we shall do it with the help of real monthly totals for US air traffic data adapted from the United States Department of Transportation’s International Report Passengers dataset on October 8, 2021. This file is available in the Chapter 8 folder in our File-Share site. This dataset includes all nonstop commercial passenger traffic traveling between international points and U.S. airports. The number of reported passengers are in the thousands. This data captures monthly air traffic totals between February 2010 and January of 2019. Figure 8.1 shows the seasonal trends in this data with repeated annual highs in July and annual lows in February. This chart was created with the Orange Line Plot widget. As we see on this line plot, there are repeating annual cycles in the data so this dataset should be a good candidate for ARIMA analysis.³

[Figure 8.2 shows the Orange workflow we will use to create 24 months of future air traffic forecasts. The notes on this workflow provide summary comments that define the analysis steps for this ARIMA modeling.](#content0201.xhtml)

As we explore this Orange workflow, we should note that the data format for this ARIMA modeling requires that one column of data includes the dates and a separate column has numerical values of interest which, in this case, is the number of air passengers flying that month in the USA. Here are the numbered steps to create a 24-month future forecast prediction of the number of air travelers for the default settings in Orange that will be improved upon afterwards:

  
![](images/image-GZBOVXYM.jpg)  

Figure 8.1 Nine years of monthly USA air traffic passengers (2010 to 2019)

  
![](images/image-RCYCEFA1.jpg)  

Figure 8.2 The Orange workflow used for the ARIMA modeling

  

1\. Import your data with the File widget.

2\. Click on the File widget and make sure that the number of passengers feature is set as the target and that the Date feature is set as meta.

3\. Use the Data Table widget to check if the data looks as you expected it to look.

4\. Click on the Form Timeseries widget which ensures that the data is in a format that the ARIMA analysis widgets can understand. Select the “select the column with date” option and ensure that the “Date” feature was selected in this widget.

5\. Open the ARIMA Model, Model Evaluation, Line Chart, and the Data Table widgets shown on the far right side of the workflow at the same time so you can see, real-time, how any predictive modeling parameter changes will affect the model performance metrics noted on the Model Evaluation widget and the 24-month forecasts visually displayed on the Line chart widget.

6\. When initially opening all of these widgets, the default ARIMA parameters were shown as (1,1,1) which represent the well-known p,d,q parameters (auto-regressive order, differencing degree, and moving average order) which just represents the start of any trial-and-error modeling tasks. The default for the number of folds and Forecast steps in the Model Evaluation widget were 1,1.The starting model performance metrics and line chart display of the 24-month forecasts will initially look dismal and not useful, as shown in Figure 8.3 .

7\. Figure 8.3 shows a display of the starting parameters for seven key ARIMA settings that are numbered in Figure 8.3 which are described in the Orange widget help files. The Model Evaluation widget also shows the 7 model metrics: RSME, MAE, MAPE, POCID, R-Squared, AIC, and BIC.

8\. Figure 8.4 shows the resulting 24-month forecasts for the default parameters which includes a very wide predictive cone of probability which we will work to improve with trial and error experiments.

Now we start the tedious experimental trial and error phase of ARIMA modeling to improve the initial model performance. We are not experimenting with different algorithms as in previous modeling exercises but only with changes to the p,d,and q parameters and with the number of folds and forecast steps within the ARIMA model. However, Orange suggests in their help files not to create a model where the test performance is too much different from the training (in-sample) model performances. There are many publications on and the strict rules for conducting ARIMA, so be cautious about just randomly attempting to create and evaluate an ARIMA forecast model as demonstrated here.⁴

[Figure 8.5 shows the chosen model parameters that improve the training (in-sample) and test (unlabeled) model metrics without creating a great difference between the two samples. Figure 8.6 shows the resulting 24-month forecast graphic for the optimized model with the mean prediction and confidence intervals within the blue-shaded area. The optimized model achieved a R-Squared value of 91.4% and a fairly useful 95% confidence interval region compared to an incalculable R-Squared value and a useless 95% confidence interval predictive cone for the initial model.](#content0202.xhtml)

  
![](images/image-IMIELTZ7.jpg)  

Figure 8.3 The initial default settings for the ARIMA modeling

  
![](images/image-F68OCRBD.jpg)  

Figure 8.4 The initial 24-month predictions with the default settings

  

#### 8.1.2 Pros and Cons of ARIMA Models

  

Pros:

•ARIMA is a well-understood, documented, and studied technique.

•Its results are comparable with other statistical time series techniques.

•ARIMA models only require prior data to create a forecast. ⁵

Cons:

•It is not a multivariate technique.

•It has difficulty predicting time series turning points.

•It is not reliable for long-term forecasting.

•It is less explainable than exponential smoothing.

•ARIMA takes time, experience, and trial-and-error to find the optimal model settings.

•At least 50 rows of data are required to build a model but 100 rows are preferred.

•The methods used to determine the p,d, and q parameters are quite subjective.

•The methods used to determine the best number of folds for cross validation is quite subjective.

•ARIMA cannot handle multiple seasonality.

•It struggles with mean shifts. ⁵

  
![](images/image-FZSGGUA8.jpg)  

Figure 8.5 The optimized settings for the ARIMA modeling

  
![](images/image-ZGVD782P.jpg)  

Figure 8.6 The 24-month predictions for the optimized ARIMA model

  

8.2 SURVIVAL ANALYSIS

  

  

Known also as time-to-event analysis, survival analysis is a sophisticated statistical technique that focuses on examining the time period prior to the occurrence of a particular event of interest. This event of interest could range from critical life events like mortality to mechanical system failures or the recurrence of a disease, among others. This technique can even be applied to track the performance of a predictive model.⁶ This approach allows for situations where the event has not yet occurred (censoring) in addition to taking into consideration the amount of time before it does. It is especially helpful in disciplines like reliability engineering for forecasting machinery maintenance schedules, medical research for evaluating patient survival rates, medical treatment effectiveness, and several other areas where comprehension of time-related dynamics is crucial for decision-making and resource optimization.

  

#### 8.2.1 The General Steps to Perform Kaplan-Meier Survival Analysis

  

Orange and BlueSky Statistics offer the Kaplan-Meier method from their associated Python and R-packages. Here are the refined steps to prepare for and perform the Kaplan-Meier survival analysis:

1\. Define Research Objectives:

a. Identify the Event of Interest: Clearly define the event that the study is focused on, such as the recurrence of a disease or failure of a component.

b. Specify the Time Frame: Determine an appropriate time frame for the study. For instance, a cancer study might necessitate tracking patients over several years, whereas a study on machine failures might be shorter in duration.

c. Optimize Study Duration: Ensure the study is long enough to capture sufficient data on the events of interest but not excessively long, which could render the findings obsolete. ⁷

2\. Data Collection:

a. Event Occurrence and Time Data: At the very least, two columns of data are necessary: one indicating whether the event of interest occurred (1) or not (0) during the study period, and another column documenting the time at which the event occurred, or the study ended.

b. Incorporate Additional Variables: Collect additional continuous or categorical data about the subjects or units to gain a more complete understanding of factors affecting the event.

3\. Handle Censoring:

a. Recognize and Document Censoring: Incomplete information about the survival time for certain individuals is known as censoring. The Orange Kaplan-Meier Plot widget offers the option to display censored data. Censoring can occur due to various reasons such as:

1\. The event did not occur during the study period.

2\. The subject was lost or data was missing.

3\. The subject withdrew from the study. ⁸

4\. Define Follow-up Period:

a. Determine if and for how long after the end of the study event data will still be collected.

5\. Data Pre-processing for Kaplan-Meier Analysis:

a. Convert Continuous Variables to Discrete Categories: When employing the Kaplan-Meier method, convert continuous predictor values to discrete categories using the equal frequency discretization option in the Orange Preprocess widget. This enhances the interpretability of confidence intervals in the results.

b. Using an alternative method like equal width discretization in the Orange Preprocess widget can lead to overlapping confidence intervals for varied group sizes, which complicates statistical interpretation of the data visualization.

c. If continuous predictor values are not categorized, the Kaplan-Meier method will not include these predictors in the analysis, making it incomplete.

6\. Statistical Testing and Analysis:

a. Complement Kaplan-Meier with Additional Tests: While Kaplan-Meier analysis provides the Log-rank chi-squared p-value and graphical representations with confidence intervals, other statistical tests can provide additional perspectives.

b. Kaplan-Meier tests can also be supplemented with the chi-square and t-test p-values in the Orange Box Plot Widget to augment the analysis.

7\. Interpretation and Reporting:

a. Analyze the Results: Interpret the Kaplan-Meier survival curves, focusing on median survival times and the differences between groups.

b. Assess Statistical Significance: Evaluate the p-values to determine the statistical significance of the differences between groups.

c. Present Findings: Clearly communicate the findings, including visualizations of the Kaplan-Meier curves and relevant statistics, in the context of the research objectives.

  

#### 8.2.2. Orange Example of Kaplan-Meier Survival Analysis

  

For this example we use the survival data for over a 7+ year period for 686 female patients from the 1994 German Breast Cancer Study Group 2 that is available in the Orange Dataset widget. This study contains 10 features (Recurrence Free Survival Time, Recurrence Event, Menopausal Status, Age of the Patient, Tumor Grade, Hormonal Therapy, Tumor Size, Number of Positive Nodes, Progesterone Receptor, and Estrogen Receptor). 43.6 % of the study group had a recurrence of breast cancer. This analysis will look at the effects of hormone treatment and other factors on recurrence-free survival time. The event of interest is the recurrence of cancer. ⁹

[Figure 8.7 shows the Orange workflow that will be used to conduct all of the related Kaplan-Meier survival analysis tasks that were mentioned in the previous section.](#content0205.xhtml)

[Figure 8.8 shows the data in its original format with its mix of continuous variables and categorical variables. The continuous variables can be used for t-tests in the Box Plot widget in the lower part of the workflow but the Kaplan-Meier Plot widget can only process categorical variables. We used the Preprocess widget for equal frequency discretization of all continuous variables in a parallel workflow path so that all variables can be analyzed with the Kaplan-Meier Plot widget. Figure 8.9 shows the data after all variables were discretized.](#content0205.xhtml)

  
![](images/image-9Q8XML0S.jpg)  

Figure 8.7 Kaplan-Meier survival analysis workflow in Orange

  
![](images/image-IZ9EERR0.jpg)  

Figure 8.8 Original format of the Breast Cancer dataset

  
![](images/image-8SC3SP38.jpg)  

Figure 8.9 All Breast Cancer features and now discretized

  

The Data Table widget was placed at various areas on the Orange workflow so that the original and transformed data can be viewed to ensure that they meet the analysis needs. Before we look at the unique information that a Kaplan-Meier Plot can offer, let’s see what we can learn from a distribution plot for the “Number of Positive Nodes” feature in the data set with the help of the Distribution widget using the “stacked columns” and “show probabilities” options. Figure 8.10 shows such a plot where we can visually see that when the number of positive nodes are greater or equal to 3.5, there is a much higher probability of cancer recurrence, as designated by the upper dark-shaded regions of the stacked bar chart.

[Figure 8.11 shows a Kaplan-Meier Plot for survival probability on the Y-axis and the Recurrence Free Survival Time (RFST) in days for two groups: those in the group with the number of positive nodes below 3.5 (light-shaded shaded area) and those with 3.5 of a greater number of positive nodes (dark- shaded area). Censored data points are shown on the graph as short vertical lines extending upwards from the trendline.](#content0205.xhtml)

  
![](images/image-UJ9MNBY0.jpg)  

Figure 8.10 Higher probability of cancer recurrence associated with higher numbers of positive nodes

  
![](images/image-NSZGKSUG.jpg)  

Figure 8.11 Kaplan-Meier Survival Plot for the number of positive nodes

  

The shaded areas in Figure 8.11 represent confidence intervals. Non-overlapping confidence intervals represent statistical confirmation that the two groups are different from each other, which is confirmed by the Log-rank p-value of <0.005 shown in the graph legend. The n/N notation in the graph legend describes the number of cancer recurrences in a group/the total number of patients in the group. The median number in the legend represents the median time for the recurrence of cancer. It is also shown on the graph as a vertical line for the lower group but it is not shown for the upper group since the number is off the chart which is a good outcome for the group with < 3.5 nodes. The lower curve on the graph represents a lower probability of survival and a shorter time for the recurrence of cancer. This is the group with >3.5 nodes.

[Figure 8.12 shows a Kaplan-Meier Survival Plot for the second most prominent predictors of cancer recurrence: Progesterone receptor levels greater than or less than 32.5. These two groups also have a statistically significant Log-rank p-value of < 0.005.](#content0205.xhtml)

[Figure 8.12 shows us that higher (>= 32.5) progesterone receptor levels are associated with higher Recurrence Free Survival Times (RFST). As seen on the graph, the confidence intervals are mostly non-overlapping. The lower group on the graph had lower (<32.5) progesterone receptor levels which are associated with lower Recurrence Free Survival Times (RFST).](#content0205.xhtml)

  
![](images/image-QZEQNBHI.jpg)  

Figure 8.12 Kaplan-Meier Survival Plot for progesterone receptor levels

  

[Figure 8.13 shows us an example of how the Kaplan-Meier Survival Plots can show any number of groups on one graph but at some point they will become harder to read and interpret. In this graphic we see higher grades of the tumor are associated with shorter recurrence times for breast cancer.](#content0205.xhtml)

[Table 8.1 shows the summary of all analysis work done on this dataset for the Kaplan-Meier Survival analysis method as well as supplemental information gathered from the box plot analysis.](#content0205.xhtml)

Each feature should be analyzed separately with the Kaplan-Meier Survival analysis method to ensure that a full understanding has been gained for how each feature interacts with survival probability and recurrence free times. The Kaplan-Meier Survival p-values and the box plot p-values will not always match since they are being calculated from different perspectives.

As seen on Table 8.1, not all predictors were statistically significant (p-values < 0.05). In such cases, the Kaplan-Meier Survival plot will display overlapping confidence intervals, as shown in Figure 8.14 where older and younger patients in this study group did show a statistically significant difference in cancer recurrence times (p-value > 0.05).

  
![](images/image-3JFICES1.jpg)  

Figure 8.13 Kaplan-Meier Survival Plot for the tumor grade

  

Table 8.1 Summary of observations and p-values for the breast cancer dataset analysis

  
![](images/image-GA2ZK42A.jpg)  
![](images/image-RAULZKAY.jpg)  

Figure 8.14 Kaplan-Meier Survival Plot for two patient age groups

  

8.3 PUTTING KNOWLEDGE INTO PRACTICE

  

  

#### 8.3.1 Exercise

  

For this exercise, we will use a 2010 file from the Orange Dataset widget titled: Democracy-Dictatorship: Classification of political regimes as democracy and dictatorship.This data 1,808 heads of governments for 200 countries in the world with a country leadership start date that ranges between 1946 and 2008. We are interested in knowing whether the duration in years of a government leader is longer in countries labeled as democracy or as non-democracy. We will use two different methods in Orange to determine and visualize the answer to this question: the Kaplan Meier Survival Analysis (KMSA) and box plot. Figure 8.15 shows the workflow we will use to answer this question.

As we access the noted file from the Orange Dataset widget,we will want to review the format of that dataset in the Data Table widget. Review the information available in this dataset which also included the names for the heads of state for 200 countries since 1946. For this exercise, we are only interested in two columns of data in this dataset: The duration (years) and the democracy columns. The duration column lists the number of years that a country leader was in place and the democracy column notes whether the country was a “democracy” or “non-democracy” country based on United Nations designations. Figure 8.16 shows us the Kaplan-Meier Survival Analysis for the two types of government that are being compared and all of the settings in Orange that are required to conduct this analysis. The chosen settings here are to select democracy as the group and to select the following display options: confidence intervals, medians, and censored data.

  
![](images/image-E3KMGDKF.jpg)  

Figure 8.15 workflow to determine the duration of country leadership

  
![](images/image-C9UVV1KI.jpg)  

Figure 8.16 Kaplan-Meier Survival Analysis for types of government

  

The shaded areas in Figure 8.16 represent confidence intervals. Non-overlapping confidence intervals represent statistical confirmation that the two groups of government are different from each other, which is confirmed by the log-rank p-value of <0.005 shown in the graph legend. The n/N notation in the graph legend describes the number of past leaders of a country in a group/the total number of country leaders in the group. The median number in the legend represents the median duration (years) of a country leader. It is also shown on the graph as a vertical line for both groups. The lower curve on the graph represents a lower probability of durations (median of 3 yrs) for leaders from countries that are labeled as a democracy. The upper curve on the graph represents a higher probability of durations (median of 6 yrs) for leaders from countries that are labeled as a non-democracy. The confidence intervals for these two curves do not overlap which further strengthens the validity of this observed difference between the duration of government leaders for democracy versus non-democracy styles of government.

[Figure 8.17 shows a box plot analysis of the duration variable chosen for the top box in the Box plot widget and the democracy variable chosen for the Subgroups selection. Also note that the following settings were chosen for the display options: Annotate and Compare means.](#content0207.xhtml)

[Figure 8.17 compares means of government leadership durations while the Kaplan-Meier Survival Analysis compared medians. The box plot shows that duration means for democracy-based governments was 3.366 yrs compared to a duration mean of 8.251 yrs for non-democracy-based governments and the low p-value (<0.05) suggests that these differences in the means are statistically significant.](#content0207.xhtml)

  
![](images/image-8G16PI51.jpg)  

Figure 8.17 Box plot analysis for the durations of government leadership

  

In summary, the Kaplan-Meier Survival Analysis and the box plot analysis both agree that the duration of leadership for democracy-based governments is shorter than for non-democracy-based governments based on the 1946 to 2008 timeframe for 200 countries in the world.

  

#### 8.3.2 Maturity Levels

  

Let’s focus on the renewable energy sector as the specific industry:

Harnessing analytics is crucial for the rapidly evolving renewable energy industry. Time Series Forecasting (TSF) and Kaplan-Meier Survival Analysis (KMSA) can significantly optimize energy production and infrastructure longevity.

Energy companies have access to vast historical data, such as solar radiation patterns or wind speeds. These data sets, when properly analyzed, can revolutionize the way energy is harvested and stored. Yet, this goldmine often remains underutilized. What the sector needs is a Renewable Energy Analytics Center, dedicated to extrapolating insights from this data.

Let’s delve into the three stages of applying TSF and KMSA in this context:

1\. Foundation of Energy Analytics : At the beginner level, TSF identifies patterns like seasonal solar or wind potential, and KMSA assesses the lifespan of infrastructures like solar panels or wind turbines, leading to foundational tweaks in energy capture and maintenance schedules.

2\. Elevated Energy Insights : In the intermediate stage, refined models come to play. TSF aids in predicting daily or hourly energy outputs, while KMSA offers insights into the longevity of installations under various environmental stresses, guiding efficient infrastructure investments.

3\. Energy Mastery : At the advanced level, TSF and KMSA work synergistically. Algorithms predict optimal times for energy storage and release, maintenance schedules are refined to reduce downtime, and the industry moves from merely harnessing energy to efficiently storing and distributing it.

In conclusion, integrating TSF, KMSA, and related analytical methods can be revolutionary for the renewable energy sector. It’s important to ensure sustainable and long-term energy solutions in addition to improving energy production. Industry leaders must support this data-driven strategy and promote renewable energy as the dependable power source of the future.

  

#### RESOURCES

  

  

1\. Gray K. Time series analysis: what it is and what it does \[Internet\]. Quirks; 2013 \[cited 2023 Jul 5\]. Available from: https://www.quirks.com/articles/time-series-analysis-what-it-is-and-what-it-does

2\. Beginner’s Guide to time series analysis \[Internet\]. \[cited 2023 Jul 5\]. Available from: https://www.quantstart.com/articles/Beginners-Guide-to-Time-Series-Analysis/

3\. Nielsen A. Practical Time Series Analysis: Prediction with Statistics and Machine Learning. “O’Reilly Media, Inc.”; 2019. 504 p.

4\. 20+ time series projects ideas for beginners to practice 2023 \[Internet\]. ProjectPro. 2021 \[cited 2023 Jul 5\]. Available from: https://www.projectpro.io/article/time-series-projects/444

5\. Goel MK, Khanna P, Kishore J. Understanding survival analysis: Kaplan-Meier estimate. Int J Ayurveda Res. 2010 Oct;1(4):274–8.

6\. Kaplan-Meyer Calculator https://www.statskingdom.com/kaplan-meier.html

  

#### REFERENCES

  

  

[1\. About us \[Internet\]. International Institute of Forecasters. 2015 \[cited 2023 Jul 6\]. Available from: https://forecasters.org/about/us/](#content0200.xhtml)

[2\. M open forecasting center – MOFC \[Internet\]. \[cited 2023 Jul 6\]. Available from: https://mofc.unic.ac.cy/m-open-forecasting-center/](#content0200.xhtml)

[3\. Department of Transportation Office of the Assistant Secretary for Aviation, International Affairs. International\_Report\_Passengers \[Internet\]. 2017 \[cited 2023 Jul 5\]. Available from: https://data.transportation.gov/Aviation/International\_Report\_Passengers/xgub-n9bw](#content0201.xhtml)

[4\. Fuqua School of Business. ARIMA(0,1,0)x(0,1,0): Seasonal random trend model \[Internet\]. \[cited 2023 Jul 5\]. Available from: https://people.duke.edu/~rnau/411seart.htm](#content0201.xhtml)

[5\. Ellis C. When to use ARIMA models \[Internet\]. Crunching the Data. 2022 \[cited 2023 Jul 5\]. Available from: https://crunchingthedata.com/when-to-use-arima/](#content0202.xhtml)

[6\. Javed H. Survival analysis for reliable forecast modeling in production \[Internet\]. Towards Data Science. 2022 \[cited 2023 Jul 6\]. Available from: https://towardsdatascience.com/reliable-forecast-modelling-2094cc5237a1](#content0203.xhtml)

[7\. Survival Analysis \[Internet\]. \[cited 2023 Jul 5\]. Available from: https://sphweb.bumc.bu.edu/otlt/mph-modules/bs/bs704\_survival/BS704\_Survival\_print.html](#content0204.xhtml)

[8\. The basics of survival analysis \[Internet\]. \[cited 2023 Jul 5\]. Available from: https://tinyheero.github.io/2016/05/12/survival-analysis.html](#content0204.xhtml)

[9\. GBSG2 Dataset \[Internet\]. \[cited 2023 Jul 5\]. Available from: https://paperswithcode.com/dataset/gbsg2](#content0205.xhtml)

  

![](images/image-II1XRN9H.jpg)Chapter 9

  

## Geolocation

  

“If geography is prose, maps are iconography”

—Lennart Meri

  

“Geolocation Analysis: Transforming coordinates into stories, one point at a time”

—GPT-4

  
![](images/image-M6MTZISG.jpg)  
  

LEARNING OBJECTIVES

  
  

After reading chapter nine readers should be able to:

•Discuss the evolution of several technologies that made modern geolocation possible.

•Describe how geolocation is used in the medical and non-medical sectors.

•Discuss how geolocation techniques can be used for epidemic and epidemiology tracking.

•Cite several multi-industry initiatives that use geolocation.

•List and discuss the Orange widgets that offer geolocation displays.

  
  

Chapter 9 Summary

  

  

Geolocation visualizations and analysis have become an indispensable tool, weaving its threads into the intricate fabric of our research projects and interconnected world. For the everyday consumer, this translates to effortlessly pinpointing the nearest cafe, bookstore, or emergency service. But its influence stretches far beyond personal use.

  

In the active world of retail, geolocation helps in mapping potential markets with tailored consumer experiences. In healthcare, it provides invaluable insights into patient demographics, aids in tracking disease outbreaks, and enhances data visualization for global and public health strategies.

  

The logistics industry, with its complex web of shipments, thrives on geolocation for real-time tracking and for the optimization of routes. Meanwhile, the agricultural sector uses it to monitor crop health, predict yields, and optimize irrigation.

  

The travel and tourism sector harnesses geolocation to offer tailored experiences, suggesting local attractions and hidden gems based on a traveler’s location. In finance, risk assessment for insurance, property valuation, and fraud detection can be enhanced using geolocation data.

  

This proliferation is reinforced by the integration of global GPS systems, wireless networks, and the near-universal adoption of smartphones. As industries evolve, the applications of geolocation visualizations and analysis will continue to grow, illustrating the convergence of technology and practical applications for diverse sectors.

  

Key Principles

•By using symbols, colors, and shading to intuitively represent spatial patterns across diverse geographic scales, geospatial mapping enhances data visualization.

•By utilizing geographical context, which is not possible with conventional visualizations, geospatial mapping and analysis can uniquely reveal patterns and insights.

•Businesses and the public health benefit greatly from the use of geospatial mapping and analysis, which enables data-driven and spatially informed decisions that maximize results and resource allocation.

  

  

9.1 INTRODUCTION

  

  

Non-medical geolocation is prevalent in modern society, as evidenced by apps such as Google Maps, Waze, Yelp, etc. This approach is possible due to the satellite-based global positioning system (GPS) that was launched in the 1970s but became highly accurate for non-military use in 2000.¹ Users tend to take this approach for granted but they should realize that GPS, smartphones, and the Internet are relatively new. GPS and geolocation are ubiquitous worldwide on smartphones. There are multiple business cases related to geolocation, but we will start with some medical applications.²

There are times when it is important to identify the geographical location of patients, diseases, outbreaks, services, etc. Geographical location has been used for a long time in the fields of epidemiology and public health. One of the earliest examples in the United States resulted in a map of a yellow fever outbreak in Manhattan reported in 1798 by Valentine Seaman.³ Figure 9.1 shows a portion of the original map by John Snow depicting the locations of cholera cases in the London pandemic of 1854 (larger case numbers represented by larger rectangles). The contaminated pump (large X on the map) believed to be the cause of the pandemic is situated at the intersection of Broad Street, Cambridge Street, and Little Windmill Street (now Lexington Street).⁴

  
![](images/image-9YK9ITWM.jpg)  

Figure 9.1 Cholera cases in the 1854 London cholera pandemic

  

Dr. John Snow created this map of cholera cases in London. He helped shut down a contaminated well, thus helping to end the epidemic. Newer sources maintain that Dr. Snow was instrumental in proving that cholera was not an airborne disease. However, they also maintain that the map was created after public health authorities had already noted that the Broad Street water pump was the culprit and the disease was declining.⁵

There are many data sources available to paint a more accurate picture of the overall patient experience. Medical care is thought to account for only 10-20 percent of the modifiable contributors to health, whereas the other 80 to 90 percent are referred to as the social determinants of health (SDOH). SDOH includes health-related behaviors/habits, socioeconomic factors, and environmental factors.⁶ Figure 9.2 displays the different social determinants of health.

Social determinants can be further explored using websites such as County Health Rankings and can therefore be part of Geolocation studies.⁷ County Health Rankings & Roadmaps (CHR&R) is a program of the University of Wisconsin Population Health Institute. This initiative measures the health of every county in 50 states.

  
![](images/image-EIIOCTYN.png)  

Figure 9.2 Social determinants of health ⁷

  

To gain a more complete picture of population health, the social determinants of health (SDOH) and environmental factors can be combined to create precision health or healthcare tailored to the individual patient.⁸ National Neighborhood Data Archive (NaNDA) datasets provide a wealth of environmental data based on census tract data.⁹

In the modern era of widespread smartphone usage and integrated location services, it makes sense to mine those data. For example, a recent article measured group distancing based on mobile technology to see if it correlated with COVID cases. Individual compliance with social distancing guidelines is difficult to measure, so mobile device geolocation data was used as a proxy for physical distancing and movement patterns during the pandemic. For the state studied, social distancing did correlate inversely with COVID-19 cases.¹⁰

  

9.2 GEOLOCATION EXERCISES

  

  

#### 9.2.1 Geolocation with Synthetic Data

  

For a demonstration, synthetic data generated by Synthea will be used because their patient demographic data includes latitude-longitude pairs which Orange can process.¹¹ While this is synthetic data, it mirrors the actual population of Massachusetts. 1000+ synthetic patients have been generated, and we want to visualize where in Massachusetts these patients live. In Orange, one can use the Geocoding widget to convert a location to latitude-longitude, or the opposite, convert latitude-longitude to a location.

The first step is to upload the file “Synthetic patients” from the File-Share Chapter 9 folder to the File widget.¹² In addition to lat-long data, there are columns for race, ethnicity, gender, marital status, healthcare expenses, and healthcare coverage. Connect the File widget to the Geocoding widget. Open the Geocoding widget and select the second choice, “Decode lat and long into regions.” For region identifier, select STATE. For the Identifier type, select US State. For the Administrative level, select “1st level subdivision.” Connect this widget to the Geo Map widget and open it. Lat and long should self-select and choose Color = RACE to see the racial distribution. Note that in the lower left there are three choices: “select” (gives mouseover results), pan (move around), and zoom.

[Figure 9.3 displays the Orange workflow, and Figure 9.4 displays the correct choices in the Geocoding widget. Figure 9.5 shows the results of our query.](#content0214.xhtml)

  
![](images/image-G06NH3XK.png)  

Figure 9.3 Geocoding workflow

  
![](images/image-YU6078EK.png)  

Figure 9.4 Geocoding widget settings

  
![](images/image-A19L8Y0G.jpg)  

Figure 9.5 Geolocation of patients by race in Massachusetts

  

Next, we will combine the synthetic patient file that contains demographics and lat-long pairs with the conditions file that includes diseases, such as diabetes. The goal is to see if there is a concentration of diabetes by location. The first step is to upload the file “Patients with Diabetes.csv” from the File-Share site into a File widget.¹² In a second File widget load the file “Synthetic Patients.csv” so they can be merged. Connect both File widgets to the Merge Data widget. One connector should be “Data” and the other “Data connecting to extra data.” Open the Merge Data widget and select the first choice, “Append columns from Extra data,” and the “row matching” selection should be “Patient.” Figure 9.6 displays the widget choices.

Connect the Merge Data widget to a Data Table widget and open. Scroll to the Diagnoses column and click the header to sort the data. Highlight all patients with the diagnosis diabetes, and connect to another Data Table where only patients with diabetes will appear. Connect the second Data Table to a Save Data widget and save as “patients\_diabetes\_location.tab.” See Figure 9.7 for the Orange workflow.

Lastly, upload the file just created into the File widget, and connect to the Select Columns widget. Open the Select Columns widget and use only the variables Diagnosis, LAT and LON. Connect the Select Columns widget to the Geocoding widget and then to the Geo Map widget. Open the latter widget. Figure 9.8 displays the location of the 61 patients identified in this dataset. Obviously, this is a very small sample. However, the process points out how one could use geolocation to display the location of patients with a myriad of chronic diseases or just for one disease, as shown in this example.

  
![](images/image-0VF95UGY.png)  

Figure 9.6 Merge Data widget settings

  
![](images/image-RJWO824V.png)  

Figure 9.7 Orange workflow to merge selected files

  

9.3 MULTI-INDUSTRY APPLICATION EXAMPLES OF GEO-MAPPING AND GEO-ANALYSIS

  

  

To gain insights and improve operations, geo analysis, and mapping have become increasingly popular in various businesses. Here are a few intriguing examples spanning several industries:

1\. Agriculture : Farmers use GIS technology to monitor crop health, improve irrigation, and increase yields. Geo-analysis aids in examining these elements so that decisions can be made confidently. Geo-mapping is used to build field maps that monitor various factors such as soil composition and moisture levels. ¹³

2\. Healthcare : Geographic analysis is used to map the transmission of diseases and comprehend the geographical elements impacting them in healthcare. For instance, geo-mapping was widely utilized to monitor the COVID-19 pandemic’s viral spread. ¹⁴

  
![](images/image-A8RLH55K.png)  

Figure 9.8 Geolocation of patients with diabetes in select Massachusetts dataset

  

3\. Retail : Retailers employ geo-mapping to find potential locations for new stores. They can locate new stores to maximize revenues by looking at demographic information, rival locations, and traffic patterns. ¹⁵

4\. Energy : By examining variables like wind patterns and sunshine exposure, geo-analysis can assist in identifying the best locations for wind turbines or solar panels. ¹⁶

5\. Conservation : Geo-mapping is a tool conservationists use to follow the movements of endangered species and analyze habitat. They can decide better how to preserve habitat by examining these migrations and other environmental data. ¹⁷

6\. Insurance : To evaluate the risks of natural disasters in specific areas, insurers employ geo-mapping. For instance, they might use flood zone maps to establish insurance prices for properties in specific locations. ¹⁸

7\. Entertainment : Geo-mapping is used in augmented reality gaming, such as Pokémon Go, to offer an immersive gaming experience. Real-world maps are included in the game, and players can explore their surroundings to find and catch virtual animals. Based on elements like geography, accessibility, and proximity to other areas, geospatial data can be utilized to find possible filming locations.

8\. Forestry : Geo-analysis is used in forestry to plan sustainable logging operations and to track deforestation and the health of the forest. Loggers can reduce their environmental impact by being aware of how forests develop and change over time. ¹⁹

9\. Maritime : Geo-analysis is being utilized to track and forecast pirate activity in high-risk regions of the maritime industry. Shipping businesses can take precautions by knowing where assaults will likely happen. ²⁰

10\. Archeology : Geo-mapping is becoming more and more popular in archaeology to find and analyze ancient sites. LiDAR (Light Detection and Ranging) is a tool that allows archaeologists to find prospective locations for ancient constructions and produce high-resolution maps of the ground. ²¹

11\. Urban planning and the creation of smart cities require geospatial mapping and analysis. They are applied to waste management programs, public transportation route optimization, planning for natural catastrophe responses, and traffic flow analysis. ²²

12\. Aviation : Geo-analysis is used in aviation to design optimum flight paths that decrease fuel use and cut down on delays. Airlines can design more effective routes by real-time studying wind patterns, weather, and flight traffic. ²³

13\. Supply Chain and Logistics : Geo-analysis aids in route optimization for supply chains and logistics, which lowers fuel costs and speeds up deliveries. Logistics businesses can design the most effective routes for their delivery trucks by examining traffic information and weather patterns. ²⁴

14\. Tourism : Geo-mapping is being used by travel agencies to provide personalized travel experiences. They can map out the attractions, lodgings, and restaurants the traveler might find appealing based on those interests. ²⁵

15\. Mining : By examining geological data, geo-mapping is utilized to locate potential mining sites. Geo-analysis also aids in tracking the effects of mining activity on the environment. ²⁶

These examples highlight the various ways that geo-mapping and geo-analysis are applied across several industries, emphasizing their significance for streamlining processes and offering crucial information for making decisions.

  

9.4 PUTTING KNOWLEDGE INTO PRACTICE

  

  

#### 9.4.1 Exercise

  

Geolocation of the Human Development Index

  

One can also input locations into the Geocoding widget, such as countries or states, and it can project the lat-long information and other variables. For this next exercise, we will use the HDI dataset found in the Dataset widget. HDI stands for Human Development Index which studies the standard of living from 1990-2015 for multiple (188) countries. Double-click the HDI dataset to load in the Dataset widget and connect to the Geocoding widget. Open the widget and be sure the first option is checked “Encode region names into geographical coordinates.” Region identifier = Country. Identifier type = country name. Connect to a Data Table widget and open it. Note that the HDI is in descending order. Lat-long has been established. Now look at the other available variables such as life expectancy, average income, education, and so forth. Now connect to the Geo Map widget and open it. Color = Life expectancy. The map should look like Figure 9.9. Look at other data points in addition to life expectancy.

  
![](images/image-GNM4D246.jpg)  

Figure 9.9 Geo map of the HDI Life expectancy data

  

The last option would be to connect the Geocoding widget to the Choropleth Map widget. This colors the area of interest, e.g., a country, state, or region, instead of just placing a colored dot on the country map. Open the Choropleth Map widget and select Attribute = Life expectancy. Agg = Mean. Figure 9.10 below shows the workflow, and Figure 9.11 displays the Choropleth Map results.

  
![](images/image-9MP60JXJ.png)  

Figure 9.10 Workflow for Geo-Mapping Life Expectancy

  

#### 9.4.2 Maturity Levels

  

Any e-commerce company can leverage geo-mapping and geo-analysis to enhance customer experiences and service optimization. These are the three key levels of analysis maturity available for e-commerce organizations:

Basic Level: Store Accessibility and Demographics

•Store Mapping: Map distribution centers, warehouses, and suppliers to understand the network and enhance the shopping experience.

•Demographic Analysis: Analyze data on age, income, and buying habits to identify product demand in different regions.

•Transportation Analysis: Study delivery methods to determine areas for faster shipping.

Intermediate Level: Real-time Inventory and Sales Analysis

•Inventory Tracking: Monitor products and manpower in real-time for efficient inventory management and quick order fulfillment.

•Customer Flow Analysis: Track online shopper behaviors to spot popular products and areas of improvement.

•Sales Outcome Mapping: Assess the effectiveness of sales campaigns across different regions.

Advanced Level: Predictive Analytics and Targeted Marketing

•Demand Forecasting: Predict product demand using historical data for optimal stocking.

•Purchase Risk Analysis: Forecast purchasing patterns for targeted marketing strategies.

•Precision Marketing: Design campaigns based on demographics and buying habits for a personalized shopping experience.

•Digital Accessibility: Optimize for seamless access across various geographic locations.

  
![](images/image-VRLMMGDU.jpg)  

Figure 9.11 Choropleth map of the HDI Life expectancy data

  

Utilizing these geo-mapping and geo-analysis levels can significantly boost the customer experience in e-commerce. As technology evolves, it’s vital for companies to adapt and innovate.

  

#### RESOURCES

  

  

1\. Amazon Location Services. Convert locations to addresses and vice versa. https://go.aws/3VX06JU

2\. ESRI. Geographic Information System (GIS) https://www.esri.com/en-us/what-is-gis/overview#liSwitcher

3\. Kaggle. Global Country Information Dataset. Has Lat/Longs https://www.kaggle.com/datasets/nelgiriyewithana/countries-of-the-world-2023

  

#### REFERENCES

  

  

[1\. Global positioning system. Wikipedia. \[Internet\]\[cited 2022 October 17\] Available from: https://en.wikipedia.org/wiki/Global\_Positioning\_System#:~:text=The%20GPS%20project%20was%20started,satellites%20became%20operational%20in%201993](#content0212.xhtml)

[2\. “Geolocation—the Risk and Benefits of a Trending Technology.” n.d. ISACA. \[Internet\]\[cited 2022 October 18\] Available from: https://www.isaca.org/resources/isaca-journal/issues/2016/volume-5/geolocationthe-risk-and-benefits-of-a-trending-technology](#content0212.xhtml)

[3\. Koch, Tom. 2022. “Figure 3. Valentine Seaman’s 1798 Maps of Yellow Fever in New York Were.” ResearchGate. June 1, 2022. \[Internet\]\[Cited 2022 October 15\] Available from: https://www.researchgate.net/figure/Valentine-Seamans-1798-maps-of-yellow-fever-in-New-York-were-the-first-to-be-published\_fig1\_361241014](#content0212.xhtml)

[4\. Wikipedia contributors. 1854 Broad Street cholera outbreak \[Internet\]. Wikipedia, The Free Encyclopedia. 2023. Available from: https://en.wikipedia.org/w/index.php?title=1854\_Broad\_Street\_cholera\_outbreak&oldid=1161505761](#content0212.xhtml)

[5\. Brody, Howard, Michael Russell Rip, Peter Vinten-Johansen, Nigel Paneth, and Stephen Rachman. 2000. “Map-Making and Myth-Making in Broad Street: The London Cholera Epidemic, 1854.” The Lancet 356 (9223): 64–68.](#content0212.xhtml)

[6\. Magnan, Sanne, and HealthPartners Institute. 2017. “Social Determinants of Health 101 for Health Care: Five plus Five.” NAM Perspectives 7 (10). https://doi.org/10.31478/201710c](#content0212.xhtml)

[7\. County Health Rankings. \[Internet\]\[cited 2022 October 17\] Available from: https://www.countyhealthrankings.org/](#content0212.xhtml)

[8\. “Precision Health: Improving Health for Each of Us and All of Us.” \[Internet\]\[cited 2022 October 17\] Available from: https://www.cdc.gov/genomics/about/precision\_med.htm](#content0212.xhtml)

[9\. National Neighborhood Data Archive. \[Internet\] \[cited 2022 October 17\]. Available from: https://nanda.isr.umich.edu/data/](#content0212.xhtml)

[10\. Crawford, Forrest W., Sydney A. Jones, Matthew Cartter, et al. 2022. “Impact of Close Interpersonal Contact on COVID-19 Incidence: Evidence from 1 Year of Mobile Device Data.” Science Advances 8 (1): eabi5499.](#content0212.xhtml)

[11\. Synthea. Mitre Corporation \[Internet\]\[cited 2022 October 20\] Available from: https://synthea.mitre.org/](#content0214.xhtml)

[12\. No Code Data Science \[Internet\]. \[cited 2023 Aug 24\]. File Share. Available from: https://www.nocodedatascience.net/file-share/878a6a0a-ce0c-4350-8fc8-51c1d8826e28](#content0214.xhtml)

[13\. Sergieieva K. GIS in agriculture: Best practices for AgriTech leaders \[Internet\]. EOS Data Analytics. 2022 \[cited 2023 Jul 7\]. Available from: https://eos.com/blog/gis-in-agriculture/](#content0215.xhtml)

[14\. Musa GJ, Chiang PH, Sylk T, Bavley R, Keating W, Lakew B, et al. Use of GIS Mapping as a Public Health Tool-From Cholera to Cancer. Health Serv Insights. 2013 Nov 19;6:111–6.](#content0215.xhtml)

[15\. Retail \[Internet\]. \[cited 2023 Jul 7\]. Available from: https://www.esri.com/en-us/industries/retail/overview](#content0215.xhtml)

[16\. GIS for energy industry \[Internet\]. GeoMarvel | ArcGIS Enterprise Solutions. GeoMarvel; 2020 \[cited 2023 Jul 7\]. Available from: https://geomarvel.com/gis-for-the-industries/energy/](#content0215.xhtml)

[17\. Matos C. 3 ways GIS tools are used in biodiversity conservation \[Internet\]. Medium. 2021 \[cited 2023 Jul 7\]. Available from: https://catia-matos.medium.com/3-ways-gis-tools-are-used-in-biodiversity-conservation-525ea076268e](#content0215.xhtml)

[18\. Yohn A. Using geospatial property intelligence & GIS for risk assessment \[Internet\]. Duck Creek. 2021 \[cited 2023 Jul 7\]. Available from: https://www.duckcreek.com/blog/blog-geospatial-gis/](#content0215.xhtml)

[19\. Sh S. Application of geographic information system (GIS) in forest management. J Geogr Nat Disasters \[Internet\]. 2015;05(03). Available from: https://www.longdom.org/open-access/application-of-geographic-information-system-gis-in-forest-management-35095.html](#content0215.xhtml)

[20\. Marine \[Internet\]. \[cited 2023 Jul 7\]. Available from: https://www.gps.gov/applications/marine/](#content0215.xhtml)

[21\. Verhagen P. Spatial Analysis in Archaeology: Moving into New Territories. In: Siart C, Forbriger M, Bubenzer O, editors. Digital Geoarchaeology: New Techniques for Interdisciplinary Human-Environmental Research. Cham: Springer International Publishing; 2018. p. 11–25.](#content0215.xhtml)

[22\. GIS Applications in Urban and Regional Planning \[Internet\]. Spatial Thoughts. 2021 \[cited 2023 Jul 7\]. Available from: https://spatialthoughts.com/2021/03/15/gis-in-urban-and-regional-planning/](#content0215.xhtml)

[23\. Bradshaw D. Using GIS to build safer highways in the skies \[Internet\]. Esri. 2020 \[cited 2023 Jul 7\]. Available from: https://www.esri.com/about/newsroom/arcuser/using-gis-to-build-safer-highways-in-the-skies/](#content0215.xhtml)

[24\. Federal Highway Association Newsletter. https://www.gis.fhwa.dot.gov/newsletters/Newsletter\_February2022.pdf](#content0215.xhtml)

[25\. Cvetkovic M, Jovanovic SS. THE APPLICATION OF GIS TECHNOLOGY IN TOURISM. Quaestus. https://www.proquest.com/docview/1806553252](#content0215.xhtml)

[26\. Moore S. The use of geographic information systems in mining \[Internet\]. AZoMining.com. 2022 \[cited 2023 Jul 7\]. Available from: https://www.azomining.com/Article.aspx?Articl](#content0215.xhtml)

  

![](images/image-GDF0OUME.jpg)Chapter 10

  

## Image Analytics

  

“Where there is data smoke, there is business fire.”

— Thomas Redman

  
![](images/image-M6MTZISG.jpg)  

By the end of chapter ten readers should be able to:

•Describe the layers of a convolutional neural network (CNNs) and their role.

•List the CNNs available in Orange.

•Discuss image classification.

•Discuss the technological advances that led to computer vision being possible.

•Discuss various image analytics applications for various industries.

  
  

Chapter 10 Summary

  

  

Computer vision is arguably the most tangible evidence of effective AI in healthcare today. This is an example of AI assisting the physicians and other specialized professionals, but not replacing them. AI image and video analytics is also being applied in manufacturing, sports analytics, wildlife conservation, agriculture, retail, autonomous vehicles, security and surveillance, facial recognition, drones, astrophysics, and in many other areas. Orange offers image analysts the advantage of deep image analysis and predictions without having to learn a programming language such as TensorFlow or PyTorch. This field of image analytics is still new, so we can anticipate multiple improvements on a regular basis. What is lagging in healthcare are multiple medical image repositories that are labeled and confirmed for accuracy that can be used for educational purposes.

  

Key Principles:

•Convolutional neural networks (CNNs) are the most common form of deep learning to perform image analytics

•CNNs consist of several steps to convert the images to pixels, and then reduce the size and complexity of the image to make computation easier and quicker

•In healthcare, CNNs can analyze skin images, X-Rays , EKGs, etc.

•In the service industry, CNNs can analyze visual quality control for food services, visual field service monitoring, and visual monitoring of customer experience enhancement, etc.

•In the manufacturing industry, CNNs can be used for visual inspections, quality assurance, inventory management, etc.

•In the agriculture and livestock farming industries, CNNs can be used for plant disease detection, crop yield predictions, livestock monitoring, etc.

•Countless useful AI image analysis applications exist for every industry.

•All of the above-mentioned analysis techniques can be conducted in Orange.

  

  

10.1 INTRODUCTION

  

  

#### 10.1.1 Medical Field Applications

  

The most significant achievement in artificial intelligence in medicine (AIM) in the past 5-10 years has arguably been image analytics (image recognition or computer vision). This milestone resulted from better artificial neural networks, particularly convolutional neural networks (CNNs), better labeled image data (more image repositories), and the use of graphics processing units (GPUs) that are necessary for rapid image processing. Progress has been made in multiple sub-specialty areas: Ophthalmology (detection of diabetic retinopathy), Cardiology (interpreting echocardiograms and ECGs), Gastroenterology (better polyp prediction and “liquid biopsies’’), Radiology (radiomics), and Pathology (augmented interpretation of biopsy specimens). These are only a few of the recent achievements of computer vision in medicine.

Image analytics is accomplished primarily with deep learning algorithms known as convolutional neural networks (CNNs). Transformers are also used for computer vision; we will cover them in the next chapter. This is supervised learning where the neural network is trained on labeled data (e.g., normal chest x-ray vs. lung cancer). The CNN Orange uses is Google Inception-v3 which has 48 layers, so it is a robust CNN.¹ It is unique because it has already been trained on more than a million images from the image database known as ImageNet. ² The neural net uses prior training on labeled data before evaluating new images, a technique known as “transfer learning.” For example, this CNN has been trained on various mammals, so detecting a new mammal it has not seen before becomes easier. This neural net has not been trained on medical images, but prior training allows the CNN to detect edges and other image details. There is only one other free CNN for public use we are aware of and that is Microsoft Lobe. ³ It provides an easy to use platform, initially intended for smartphones but can also be used on any computer with a webcam. Lobe can train, test, optimize image models and launch them in production with a no-code API. It is important to point out that creating a CNN using programming is an advanced technique that requires considerable expertise and extensive lines of coding. We will use this CNN to see how well it classifies dermatology, chest X-ray, and ECG images. CNNs are complicated so we recommend perusing the resource section for further reading or viewing a video tutorial to supplement the following sections.

  

#### 10.1.2 Non- Medical Field Applications

  

In the realm of non-medical sectors, the application of ML/AI-driven image analytics has become transformative. In the automotive industry, image analytics plays a pivotal role in driver assistance systems and the evolution of autonomous vehicles, assisting with functions like lane detection and object recognition. The retail sector harnesses this technology for automated checkouts, enhanced inventory management, and to elevate the consumer experience through augmented reality. Agriculture has also embraced image analytics; farmers now rely on it for vital tasks such as detecting pests, monitoring crop health, and implementing precision agriculture techniques. Meanwhile, the real estate industry is leveraging image recognition for advanced features like virtual property tours and augmented visualizations. These applications signify how image analytics, powered by ML/AI, is reshaping industries and transforming the way businesses operate and serve their consumers.

  

10.2 AI IMAGING: INDUSTRY APPLICATION EXAMPLES

  

  

There are countless opportunities to apply AI image analysis in various industries. What follows are just some examples of such applications for the healthcare, service, manufacturing, and the agriculture and livestock farming industries.

  

## Healthcare:

•Electrocardiogram (ECG) image diagnosis

•X-ray image analysis

•Disease Detection

•Radiology Assistance

•Tumor Detection and Segmentation

•Medical Image Classification

•Surgical Planning and Guidance

•Disease Progression Monitoring ⁴ - ¹¹

  

## Service Industry:

•Food Service Industry

•Field Service Industry

•Customer Experience Enhancement

•Quality Inspection ¹²- ¹³

  

## Manufacturing:

•Visual Inspection and Defect Detection

•Quality Assurance

•Predictive Maintenance

•Inventory Management

•Process Optimization

•Robotics and Automation ¹⁴- ¹⁵

  

## Agriculture and Livestock Farming:

•Plant Disease Detection

•Weed Identification and Management

•Crop Monitoring and Yield Prediction

•Pest Detection and Management

•Precision Agriculture

•Harvesting and Sorting

•Livestock Farming and Poultry Farming

•Yield Estimation with Fruit or Vegetable Counting

•Security Monitoring for Remote Farms ¹⁶ - ²⁰

  

10.3 HOW DO CNNS WORK?

  

  

Central to understanding image analytics is the fact that images need to be converted to numbers, a format computers can process. Figure 10.1 below displays the digit zero in an 8 x 8-pixel 2D matrix. On a grayscale image black has the value of zero and white has the value of 255 and gray has values in between. Pixel values are seen in the 2D matrix in Figure 10.2.

Conversely, color images use the RGB (red, green, blue) system. Instead of having a matrix for each color, a tensor (3-D matrix) is used. In essence, the tensor stacks the 3 matrices together into 3 channels. It would be three-dimensional and have a spatial dimension of, e.g., 8 x 8 x 3.

  
![](images/image-I2JJKFLK.jpg)  

Figure 10.1 The digit zero displayed in 8 x 8 matrix

  

10.4 THE NORMAL STEPS OF IMAGE ANALYTICS WITH A CNN

  

  

The big picture of CNNs is that they deconstruct an image (feature extraction) into smaller filters/kernels of pixels and then reconstruct the image (all in the hidden layers) and ultimately classify it as correct or incorrect. See Figure 10.3 and the following text where we will outline the typical steps used in creating a CNN. A CNN consists of multiple layers of neurons, each serving a unique function and equipped with adjustable weights and biases. CNNs can be large with 100 or more layers.

  
![](images/image-X30CN5PT.jpg)  

Figure 10.2 Pixel values representing digit zero

  
![](images/image-KNPX97BI.jpg)  

Figure 10.3 Typical CNN architecture ²¹

  

#### 10.4.1 CNN Layers

  

1\. The input layer consists of a gray-scale or color image that is made up of pixels. Note that the image should be square and not rectangular.

2\. The convolutional layer performs convolutions which are filters or kernels that scan the image and create weights and biases that are summed and passed to the next layer, the activation layer. For example, when a 3 x 3 filter scans a 6 x 6 grayscale image it generates a smaller 4 x 4 feature map. The filter usually moves over one step (stride) at a time but this can be adjusted. Because the filter or kernel contains a matrix of numbers, linear algebra (dot product) is used to create a score and is called a “feature map.” The feature map provides information about corners and edges. The size of the kernel is a hyperparameter decided by the design team, along with how many layers and neurons are used to create the CNN. CNNs can contain multiple convolutional layers and pooling layers. An activation layer always follows convolutional layers.

3\. Activation layer . There are several different types of activation functions but the most commonly used one is ReLU (rectified linear activation function). The purpose of the activation function is to introduce non-linearity into the output of a neuron. A neural network is essentially a linear regression model without an activation function. The activation function does the non-linear transformation to the input making it capable of learning and performing more complex tasks. ReLU activates at a threshold to pass information forward. If the neuron calculation is greater than 0 then the actual number is passed, and negative sums are recorded as zero. See Figure 10.4

  
![](images/image-Q1TBCB46.png)  

Figure 10.4 Rectified linear activation function

  
![](images/image-25HCSR0R.jpg)  

Figure 10.5 Pooling

  

4\. Pooling layer. The primary goal of this layer is to decrease the size (computational cost) of the feature map generated during convolutions. There can be max, average, or sum pooling. For example, max pooling could reduce a 4 x 4 image to 2 x 2 by selecting the highest value in each pass and using a stride of 2. See Figure 10.5

5\. Fully connected layer . Neurons in this layer are connected to all activations in the previous layer, which is the last layer before the softmax classifier.

a. Flattening occurs in this layer and it means converting the data into a 1-dimensional array for input into the next layer. In other words, all pixel data is placed on one line. If your grayscale image is 3 x 3, then you will flatten it to a column of 9 values. This process is necessary for the final layer to classify the image. See Figure 10.6

b. The Softmax function takes the new vector that has been flattened and converts it to probabilities from 0 to 1. For example, 0.90 dog, 0.05 bird, 0.02 cat, 0.02 lion, and 0.01 for bear. This means that in all likelihood, the image is a dog. It can handle multi-class classification. The total = 1. See Figure 10.7

  
![](images/image-YLOYMEOE.png)  

Figure 10.6 Flattening of feature map

  

10.5 PUTTING KNOWLEDGE INTO PRACTICE

  

  

#### 10.5.1 Exercises

  

It is important to consider how easy the complex task of image analytics is with Orange. In contrast, if you were to create a simple CNN using TensorFlow and Keras, expect it to require at least 40 lines of Python code. In addition, creating a CNN requires an expert level of programming ability.

  

10.5.1.1 Dermatology Exercise

  

The first step is to add the image analytics module from the Add-ons menu in Orange. Once added, Orange will need to be restarted. A small image dataset is in the Chapter 10 folder on our File-Share site. There is a zipped file for BCE (basal cell epithelioma, a type of skin cancer) and a zipped file for Melanoma (malignant melanoma). Create a new folder Dermatology on your computer, and create the two sub-folders BCE and MEL. Unzip the zipped files and upload to these two sub-folders.

Keep in mind that this dataset is too small to be conclusive about performance but it is a quick and simple demonstration of how Orange image analytics works. These images were obtained primarily from Google Images.²² There is a much larger Dermatology file (ISIC) in the same folder that can be used as well.

Orange uses a widget known as Image Embedding that offers more than one CNN. Image embedding means the image pixels are converted to numbers as described in section 10.2.

•SqueezeNet : Small and fast local CNN for image recognition trained on ImageNet.

•Inception v3 : Google’s Inception v3 server-based CNN trained on ImageNet.

•VGG-16: 16-layer image recognition CNN trained on ImageNet.

•VGG-19: 19-layer image recognition CNN trained on ImageNet.

•Painters: A CNN trained to predict painters from artwork images.

•DeepLoc: A CNN trained to analyze yeast cell images.

  
![](images/image-8QN8E7W3.png)  

Figure 10.7 Softmax function

  

Follow these instructions for the exercise:

1\. Using the widget Import Images , locate the Dermatology folder on your hard drive and select that.

2\. Next, connect the File widget to the Image Embedding widget. If you want to view the images drag the Image Viewer widget to the canvas and connect it to the Image Embedding widget.

3\. Similarly, the Data Table widget will list the images you have uploaded.

4\. Because this is a supervised learning (classification) task, connect the Test and Score widget to the Logistic Regression widget. Feel free to connect other classifiers to determine which algorithm performs best for this model.

5\. Next connect the Test and Score widget to the Confusion Matrix and Predictions widgets . The workflow is shown in Figure 10.8

6\. Double-click the Test and Score widget and be sure you scroll down and select the correct Target Class (BCE, Melanoma or Average). The precision and recall results are excellent for melanoma (1.0 and .933). The AUC is 1.0, which is highly unusual and overly optimistic.

7\. Looking at the C onfusion Matrix, there are no false positives (hence the perfect precision) and only 1 false negative. Remember that the dataset size is very small, so we should not attach too much significance to the results. This is just an exercise to gain experience in image analysis. As a rule, a dataset used for image analysis should include 100-1000 images to be useful. The more the better. Importantly, with a much larger dataset, we should also analyze the test data by using the Data Sampler widget.

  
![](images/image-M49CHPM3.jpg)  

Figure 10.8 Image analysis with image embedding widget

  

10.5.1.2 Chest Xray Exercise

  

Kaggle has a dataset divided into training and test sets for COVID-19, viral pneumonia, and normal chest xrays. The image subfolders train and test can be downloaded from Kaggle ²³ and are also available in the Chapter 10 folder on our File-Share site. Create a new folder on your computer and upload the 2 sub-folders (train and test). There are a total of 326 images of high quality that are labeled.

1\. Start by uploading the training data into the Import Images widget. Because they supply both train and test data, create a dual import images scenario as shown in Figure 10.9 . The training data folder will be one input and the test folder the second input.

2\. Both will need to be connected to the Image Embedding widget and the test data image embedding widget connector should be set to “embedding to test data.”

3\. Connect both to the T est and Score widget which in turn, is connected to the Logistic Regression widget. If all of the data were in one file then you would need to insert the Data Sampler widget after the Image E mbedding widget. Using the workflow below you can toggle between the training and test results. The workflow is shown in figure 10.9

Analyzing the COVID chest xray results we see the classification performance for the training and test datasets in table 10.1. (Cross validation = 10). The results are similar for train/test data, analyzed with logistic regression, suggesting there was little or no overfitting. We also saw excellent model metric performance results for viral pneumonia and normal chest xrays.

Alternatively, if you want to save your model so you can test it on new data, see the workflow in Figure 10.10 for saving and then uploading the model. Note that when you load the model you will use the Predictions widget and not the Test and Score widget. This will tell you how the predictions compare to the actual result.

  

10.5.1.3 ECG Exercise

  

Electrocardiograms can be viewed as raw waveforms or images. The ECG images we will analyze came from Physionet.org, from a German study (PTB-XL).²⁴ The ECGs are publicly available and associated with a publication.²⁵ The ECG image labels have been reviewed by one author (RH) and felt to be accurate. We will analyze ECGs to see how the CNN performs when analyzing the conduction abnormality known as right bundle branch block (RBBB) versus left bundle branch block (LBBB). The zipped files have been uploaded to our File-Share site in folder 10.

  
![](images/image-0YIP71R4.jpg)  

Figure 10.9 Image analytics workflow

  
![](images/image-PR6FU3CC.jpg)  

Figure 10.10 Saving and loading a model

  

Table 10.1 Train and test results on chest xray images

  
![](images/image-CU9NQMXF.jpg)  

The workflow is as follows:

1\. Connect the Import Images widget to the Image Embedding widget which is connected to the Data Sampler widget. Accept the default 70/30 default split. There are enough images to compare train and test image results.

2\. The results are displayed in Table 10.2 and the workflow is displayed in Figure 10.11 . The CNN performed very well and resulted in very high accuracy. This should encourage you to upload ECGs with more subtle abnormalities to see how the CNN performs on those images.

  

Table 10.2 ECG Image analysis results

  
![](images/image-0ISX61GK.jpg)  
![](images/image-LO47JS5T.jpg)  

Figure 10.11 Image embedding workflow

  

#### 10.5.2 Maturity Levels

  

Here’s how a farming cooperative might progress through different levels of maturity with AI image analytics to optimize the success of their farming operations:

•Low Maturity - Local Farming Cooperative: This small-scale organization is just beginning to digitize its operations. They decide to use AI image analytics to improve crop health and yields. By implementing a simple AI-driven system, the cooperative is able to analyze drone images of their fields. The system can identify signs of pests or disease, flagging these areas for treatment. Over time, this results in a significant improvement in crop yield and health, saving the cooperative money and increasing their efficiency.

•Mid Maturity - Expanding Farming Cooperative: After initial success with AI in pest and disease identification, the cooperative decides to expand its use of AI image analytics. It implements a system that can analyze images of crops and predict yield based on visual cues such as color and size. This allows the cooperative to better plan for market conditions and improve their supply chain efficiency. The system can also identify areas of the field that are underperforming and suggest possible causes such as nutrient deficiency or irrigation issues.

•High Maturity - Advanced Farming Cooperative: With several successful AI applications under its belt, the cooperative decides to push the boundaries of what’s possible. They now employ AI image analytics to automate some aspects of field work. Autonomous tractors, guided by AI image analytics, can now perform tasks such as sowing, harvesting, and even weeding, by identifying and differentiating between crops and weeds. These advancements lead to an unprecedented level of efficiency and productivity, reinforcing the cooperative’s decision to fully embrace AI technology.

These scenarios illustrate how a farming cooperative can progressively leverage AI image analytics to transform their operations, starting from simple disease detection and progressing to fully autonomous fieldwork.

  

#### RESOURCES

  

  

1\. Understanding the convolutional neural network. Medium.com https://medium.com/@RaghavPrabhu/understanding-of-convolutional-neural-network-cnn-deep-learning-99760835f148

2\. Simple explanation of CNNs. YouTube. 20 minutes. https://www.youtube.com/watch?v=sgL7RrqhGKI

3\. On the architecture of CNNs - a primer. Analytics Vidhya. April 2021. https://medium.com/analytics-vidhya/on-the-architecture-of-convolutional-neural-networks-a-primer-ced9e9065741

4\. 2019 Article in Nature Communications on image analytics using Orange. https://www.nature.com/articles/s41467-019-12397-x

5\. Stanford Medical ImageNet. Stanford AIMI. Website has several medical image datasets that could be used for image analysis https://aimi.stanford.edu/medical-imagenet

  

#### REFERENCES

  

  

[1\. Inceptionv3 \[Internet\]. Wikimedia Foundation, Inc.; 2019 \[cited 2022 Apr 29\]. Available from: https://en.wikipedia.org/wiki/Inceptionv3](#content0223.xhtml)

[2\. ImageNet \[Internet\]. \[cited 2023 Jul 6\]. Available from: https://www.image-net.org/](#content0223.xhtml)

[3\. Lobe \[Internet\]. \[cited 2023 Sep 5\]. Available from: https://www.lobe.ai/](#content0223.xhtml)

[4\. Reitman E. Can an image-based electrocardiographic algorithm improve access to care in remote settings? \[Internet\]. Yale School of Medicine; 2022 \[cited 2023 Jul 31\]. Available from: https://medicine.yale.edu/news-article/picture-perfect-can-an-image-based-electrocardiographic-algorithm-improve-access-to-care-in-remote-settings/](#content0225.xhtml)

[5\. Dilmegani C. AIMultiple. 2022 \[cited 2023 Jul 31\]. AI in X-ray analysis: Benefits & challenges in 2023. Available from: https://research.aimultiple.com/xray-ai/](#content0225.xhtml)

[6\. Pesapane F, Codari M, Sardanelli F. Artificial intelligence in medical imaging: threat or opportunity? Radiologists again at the forefront of innovation in medicine. Eur Radiol Exp. 2018 Oct 24;2(1):35.](#content0225.xhtml)

[7\. Park A. How AI Is Changing Medical Imaging to Improve Patient Care. Time \[Internet\]. 2022 Nov 4 \[cited 2023 Jul 31\]; Available from: https://time.com/6227623/ai-medical-imaging-radiology/](#content0225.xhtml)

[8\. Potočnik J, Foley S, Thomas E. Current and potential applications of artificial intelligence in medical imaging practice: A narrative review. J Med Imaging Radiat Sci. 2023 Jun;54(2):376–85.](#content0225.xhtml)

[9\. Vijh S. Intellipaat Blog. Intellipaat; 2023 \[cited 2023 Jul 31\]. Artificial Intelligence in Healthcare - AI applications and uses. Available from: https://intellipaat.com/blog/artificial-intelligence-in-healthcare/?US](#content0225.xhtml)

[10\. Rojewska K. DLabs.AI. 2023 \[cited 2023 Jul 31\]. The power of AI for medical imaging: 5 key applications & use cases. Available from: https://dlabs.ai/blog/the-power-of-ai-for-medical-imaging-5-key-applications-use-cases/](#content0225.xhtml)

[11\. Stevens W. MedHealth Outlook. 2023 \[cited 2023 Jul 31\]. AI in image analysis: Benefits, challenges, and change. Available from: https://medhealthoutlook.com/ai-in-image-analysis-benefits-challenges-and-change/](#content0225.xhtml)

[12\. Zharovskikh A. InData Labs. 2022 \[cited 2023 Jul 31\]. AI in service industry: All you need to know. Available from: https://indatalabs.com/blog/ai-in-service-industry](#content0225.xhtml)

[13\. AI Powered Quality inspection. https://www.bosch-softwaretechnologies.com/media/images/products/innovation/aiandbigdata/bosch\_vqi\_whitepaper.pdf](#content0225.xhtml)

[14\. Moore L. ERP. TechTarget; 2023 \[cited 2023 Jul 31\]. 10 AI use cases in manufacturing. Available from: https://www.techtarget.com/searcherp/feature/10-AI-use-cases-in-manufacturing?Offer=abt\_pubpro\_AI-Insider](#content0225.xhtml)

[15\. Singh A. The future of quality assurance in manufacturing: AI and Machine Learning solutions \[Internet\]. 1679801401000 \[cited 2023 Jul 31\]. Available from: https://www.linkedin.com/pulse/future-quality-assurance-manufacturing-ai-machine-learning-amit-singh](#content0225.xhtml)

[16\. AE529/AE529: Applications of artificial intelligence for precision agriculture \[Internet\]. \[cited 2023 Jul 31\]. Available from: https://edis.ifas.ufl.edu/publication/AE529](#content0225.xhtml)

[17\. Morgan L. Enterprise AI. TechTarget; 2022 \[cited 2023 Jul 31\]. AI examples that can be used effectively in agriculture. Available from: https://www.techtarget.com/searchenterpriseai/feature/AI-examples-that-can-be-used-effectively-in-agriculture?Offer=abt\_pubpro\_AI-Insider](#content0225.xhtml)

[18\. Karar ME, Alsunaydi F, Albusaymi S, Alotaibi S. A new mobile application of agricultural pests recognition using deep learning in cloud computing system. Alex Eng J. 2021 Oct 1;60(5):4423–32.](#content0225.xhtml)

[19\. Nomerovska I. Keymakr’s Blog features the latest news and updates. 2022 \[cited 2023 Aug 1\]. Image Annotation in AI Crop Harvesting for Agriculture. Available from: https://keymakr.com/blog/developing-ai-crop-harvesting-systems-with-image-annotation/](#content0225.xhtml)

[20\. Boesch G. viso.ai. 2023 \[cited 2023 Jul 31\]. Top applications of computer vision in agriculture (2023 guide). Available from: https://viso.ai/applications/computer-vision-in-agriculture/](#content0225.xhtml)

[21\. Saha S. A Comprehensive Guide to Convolutional Neural Networks — the ELI5 way \[Internet\]. Towards Data Science. 2018 \[cited 2022 Apr 26\]. Available from: https://towardsdatascience.com/a-comprehensive-guide-to-convolutional-neural-networks-the-eli5-way-3bd2b1164a53](#content0227.xhtml)

[22\. Google Images \[Internet\]. \[cited 2022 Apr 29\]. Available from: https://images.google.com/](#content0230.xhtml)

[23\. Raikote P. Covid-19 Image Dataset \[Internet\]. 2020 \[cited 2023 Aug 25\]. Available from: https://www.kaggle.com/datasets/pranavraikokte/covid19-image-dataset](#content0230.xhtml)

[24\. PhysioNet \[Internet\]. \[cited 2022 Apr 26\]. Available from: https://physionet.org/](#content0230.xhtml)

[25\. Wagner P, Strodthoff N, R-D, Samek W, Schaeffter T. PTB-XL, a large publicly available electrocardiography dataset \[Internet\]. 2020 \[cited 2022 Apr 26\]. Available from: https://physionet.org/content/ptb%5Cu002Dxl/1.0.1/](#content0230.xhtml)

  

![](images/image-A4CV1VZA.jpg)Chapter 11

  

## Text Mining

  

“Without big data, you are blind and deaf and in the middle of a freeway.”

— Geoffrey Moore

  
![](images/image-M6MTZISG.jpg)  
  

LEARNING OBJECTIVES

  
  

After reading chapter eleven readers should be able to

•Discuss how natural language processing (NLP) is a multidisciplinary field.

•List four common uses of NLP.

•Explain why transformers are now preferred over RNNs in NLP.

•Discuss where convolutional neural networks (CNN) are applied.

•Discuss the trends of large language models (LLMs) and small language models (SLMs).

  
  

Chapter 11 Summary

  

  

In this module, multiple natural language processing (NLP) concepts will be discussed. Supervised and unsupervised learning have been used in this section. In addition, deep learning is now a major player with RNNs, CNNs, transformers, and other new approaches for NLP. Major companies, such as Google, Amazon, and Facebook spend considerable time and money on improving NLP for the masses which provides next-generation options for Internet searches. The most recent advances are large language models (LLMs, such as ChatGPT and GPT-4. Multimodal platforms are around the corner as are specific biomedical LLMs. Simultaneously with these advancements in LLMs, small language models (SLMs) are gaining significant traction. Their appeal lies in their ability to be trained exclusively on selected documents that have been meticulously evaluated for accuracy and relevance.

  

Key Principles:

•Text Representation: Transforming text into a format suitable for analysis, such as tokenization and stemming.

•Text Preprocessing: Cleaning and preparing text for machines to analyze. This might involve removing unimportant words or fixing spelling errors.

•Natural Language Processing (NLP): Interpreting naturally spoken or written human language for meaningful analysis.

•Topic Modeling: Uncovering hidden thematic structures in a text corpus to identify trends or subjects.

•Sentiment Analysis: Identifying and categorizing opinions in a text to determine a user’s attitude.

•Large Language Models (LLMs): Models trained on extensive datasets, capable of generating human-like text and understanding a broad range of topics.

•Small Language Models (SLMs): Models trained on specific, smaller datasets, offering more precision and focus on specialized topics.

•Recurrent Neural Networks (RNNs): A type of artificial intelligence that’s good at understanding sequences, like sentences in text. It remembers what happened before to help understand what comes next.

•Attention Mechanisms: These help machines to focus on important parts of the text when trying to understand it.

•Transformer Models: A type of deep learning that uses attention to understand text. It’s especially good at understanding long sentences or pieces of text.

  

  

11.1 INTRODUCTION

  

  

This chapter is one of the more complicated chapters because it requires understanding of multiple concepts and terminologies before you can run your first NLP model. In addition, the models available are limited, as are collections of freely available medical text for text mining of healthcare applications. The following are some standard definitions for this field.

Natural language processing (NLP) “is a subfield of linguistics, computer science, and artificial intelligence concerned with the interactions between computers and human language, in particular how to program computers to process and analyze large amounts of natural language data.“ ¹ NLP draws from many disciplines, including computer science and computational linguistics. NLP includes natural language understanding (NLU) and natural language generation (NLG).

Natural language Understanding (NLU) “involves transforming human language into a machine-readable format.” ² An example would be Google Translate.

Natural language Generation (NLG) “is a software process that automatically transforms data into plain-English content.” ³ NLG can establish a two-way conversation. An example would be a chat bot or Alexa.

There has been a movement for many years to convert unstructured text to structured data for analysis by computers. NLP has gone through many different modalities over the years as noted in Figure 11.1.

This achievement has been accomplished largely by natural language processing or NLP. This chapter will discuss the highlights of text mining and how Orange approaches NLP. Text mining, like image analysis, is a specific field that requires a higher level of understanding and commitment.

We strongly recommend looking at the resources section to supplement knowledge about NLP. Orange provides extensive documentation on the details we will cover. Figure 11.2 displays how NLP fits with ML and AI, as well as computer science and linguistics.

  
![](images/image-PBKENNHB.png)  

Figure 11.1 NLP Timeline ⁴

  
![](images/image-BWO8JU8H.jpg)  

Figure 11.2 Where NLP fits in

  

Natural language processing is ubiquitous in our daily lives:

•Personal assistants : Siri, Cortana, and Google Assistant

•Auto-complete : In search engines ( e.g., Google) to finish search sentences

•Spell checking : Almost everywhere ( e.g., Microsoft Word, Google Docs, Grammarly)

•Spam checking : (e.g., Gmail)

•Machine Translation : Google Translate

•Chatbots : Customer service

•Code writing : CoPilot, ChatGPT

In the medical field, about 70% of data is unstructured or free text. Other sectors also have unstructured data as the norm, not the exception, as is the case for customer support text, legal documents, social media posts, news stories, blogs, online articles, and others. Unstructured text will not fit into the cells of a spreadsheet or database; therefore, it is not computable. In healthcare, free text includes most inpatient and outpatient narrative notes, operative notes, radiology, and path reports. In the world of customer support, free text is in the form of customer support tickets, customer emails, chat logs, and social media posts that identify customer sentiment and concerns.

  

11.2 NEURAL NETWORKS AND NLP

  

  

Historically, the first analysis of unstructured text used statistical methods such as logistic regression and Naive Bayes to classify text into categories. This was followed by machine learning algorithms, such as SVM, to classify text primarily. The most recent developments are due to deep learning or complex neural networks.

  

#### 11.2.1 Recurrent Neural Networks

  

The earliest deep neural net to perform NLP was the recurrent neural network (RNN), developed in 2014 and designed for sequential data, or time series data. RNNs are unique in remembering previous values as they move forward. Output from a previous step is fed into the current step. This is a sequence-to-sequence model. In a typical neural network, each hidden layer is independent of the next with different weights and biases. With RNNs, each layer has the same weights and biases, so that they can be combined into a single recurrent layer. Furthermore, most neural networks map a fixed input to a fixed output, whereas RNNs can map one-to-one, one-to-many, many-to-one, and many-to-many. Machine translation is with “many-to-many” RNNs, whereas sentiment analysis is done with “many-to-one,” so there is a single output, such as a “positive review.” Figure 11.3 displays a many-to-one RNN where movie reviews map to positive or negative.

There are three basic architectures of RNNs. Vanilla, LSTM and GRU. The problem with the Vanilla RNNs is related to gradients. Gradients are values used to update a neural network’s weights, leading to learning. The “vanishing gradient problem” occurs when the gradient shrinks as it propagates back over time. A gradient value does not contribute much to learning if it becomes extremely small. LSTM and GRU models do not suffer from the vanishing gradient problem.

  
![](images/image-8UQDMP91.jpg)  

Figure 11.3 Many to one RNN

  

Disadvantages related to RNNs:

•Vanishing gradient issue

•Training the RNN is difficult

•RNNs are slow and less accurate on longer sentences and paragraphs

  

#### 11.2.2 Transformer and Attention Models

  

To overcome the RNN limitations, Google developed the concept of transformers and attention in 2017. The classic article “Attention is all you need “ discusses this new innovation.⁵ It processes all the inputs simultaneously instead of sequentially, so there is “parallel computing,” meaning it is more efficient than RNNs. Also, transformers do not suffer from the vanishing gradient problem. Transformers use positional embeddings that provide information about the position in the sequence of each element. All of the input is preprocessed at once, decreasing computational complexity. The attention mechanism involves vector multiplication so that significance is determined depending on the vector’s angle. The complete transformer model is displayed in Figure 11.4. Ultimately, an output probability is generated.

  
![](images/image-3FL3KQKR.png)  

Figure 11.4 Transformer architecture

  

[Figure 11.5 shows the encoders and decoders involved in a language translation task from German to English. The input word embeddings from the first encoder are passed to the second encoder. The output from the last encoder is passed to all decoders. In addition to the self-attention and feed-forward layers, the decoders also have an encoder-decoder attention layer that helps to place attention on the input. The output here is the translation of German words into English. Self-attention is “the mechanism relating different positions of a single sequence in order to compute a representation of the sequence.” ⁶ Multi-head attention means that attention is calculated multiple times in a transformer.](#content0239.xhtml)

Examples: 1. Consider the sentence “I arrived at the bank after crossing the river.” You want the transformer to understand that the bank is related to the river and not a financial bank. The transformer compares “bank” with every word in the sentence with an attention score. River, therefore, receives a high attention score. The attention scores are used as weights for a weighted average of all words. 2. “The animal did not cross the street because it was tired” vs the animal did not cross the street because it was too wide.” Here, NLP must understand “it” means something different in each sentence.⁶

  

11.3 NLP CONCEPTS

  

  

NLP programs computers to process, analyze and classify text data. The word “document” is used frequently in NLP and means any body of words or text. A group of documents is a corpus (plural = corpora). This could include progress notes, Twitter feeds, etc. A vocabulary is a list of all units in a corpus. Text classification assigns categories to text data according to content. There are different techniques to extract information from raw text data and use it to train a classification model. The “old school” approach was a type of word embedding known as bag-of-words (used with a simple machine learning algorithm). A newer method is a word embedding model that uses a deep learning neural network. “Word or document embedding” means the mapping of words into numerical multidimensional vector spaces, as demonstrated in the section below. Word embeddings can have hundreds of dimensions. This can also be called “text representation” or “word vectorization.” Linear algebra makes this happen.

Bag of words (BoW) is a corpus of documents and counts how many times the words appear in each document. It creates a matrix where the frequency of each word is counted. A simple scoring model of the presence of word or absence of word can use a boolean value of 0 for absent or 1 for present. This type of encoding is also known as “one-hot encoding.” BoW is considered feature extraction because computers can analyze numbers, not raw text. Using the BoW model: We will vectorize these two sentences. “The patient had a myocardial infarction.” “The patient had an elevated cholesterol.” The vector would appear as follows:

  
![](images/image-Y9EEN3NI.jpg)  

Figure 11.5 Encoder-Decoder architecture

  

The matrix can be extremely large with a large corpus so important preprocessing steps usually precede the Bag-of-Words model to reduce the size of the matrix. Each of these is a Python package feature.

  

#### 11.3.1 NLP Preprocessing Steps

  

Tokenization: is the process of splitting strings into a list of words (tokens). Tokens can be words, characters or sub-words. This is usually the first step in preparing documents for NLP. The language Regular Expressions (regex) will do the splitting. Regex can be used to describe a search pattern. After tokenization, the sentence “The patient suffered an inferior myocardial infarction” gets transformed into a list{the, patient, suffered, an, inferior, myocardial, infarction}. This list now represents a vocabulary set.

Normalization: We now need to convert all the words to lowercase for consistency.

Remove the punctuation from the tokens: to include parentheses, brackets, etc. Also, remove the following: URLs, HTML tags, emojis, and numbers.

•Stop Words: Remove the stop words which are irrelevant words that will not help in identifying a text, such as “a,” “and,” “but,” “how,” “or,” and “what.” You also have the option to upload a customized stop word list.

•Stemming and Lemmatizing : Stemming will reduce the word to its root: for example, cleaning and cleansing all stem to clean. Lemmatization will convert synonyms into a single root term: for example, automobile, car and truck convert to vehicle.

•Part of Speech (POS) tagging : Determines the POS tags for each word (e.g., NOUN, VERB, ADV, ADJ).

•N-grams means breaking sentences into word combinations. For example, “this is” would be a bigram, and “this is a” would be a trigram. This helps the computer recognize combinations of words.

The BoW table 11.1 below is called a Document Term Matrix (DTM). A Co-occurrence Term Matrix (CTM) tabulates the number of times a word occurs with other words across all sentences. Each row and column represents a word in the vocabulary set. The cell at the intersection of the word in the row and column represents how often those two words appear together. Once the words are in either a DTM or CTM, various algorithms can compute similarities between words and sentences:

  

Table 11.1 Bag of words

  
![](images/image-NIZKMMPX.jpg)  

\-Cosine Similarity — one can plot the words or sentences into a multidimensional space and then compute the similarity between them from the angle they form.

\-TF-IDF (term frequency–inverse document frequency - measures the frequency of terms in a document relative to its frequency across all documents. The idea is that words highly frequent in one document but not very frequent across all documents are less likely to be relevant.

•Named Entity Recognition (NER): NER segregates ‘named entities’ into predefined categories that can range from the name of the person to locations, organization, time, percentages, etc. It is a sub-task of information extraction. In Figure 11.6 , person, organization, monetary value and location have been tagged.

  

#### 11.3.2 Topic Analysis

  

There are two types of topic analysis: Topic classification and Topic modeling

•Topic classification is supervised learning, so this means that you know what categories you are trying to predict. One would train a model on document categories and then use machine learning to predict the categories in documents it has not seen. This is basically how spam email is detected. You can use most classification algorithms and evaluate performance in the same manner. This is an area where SVM excels, and Naive Bayes has been commonly used as well. Topic classification has also been achieved with deep learning, specifically convolutional neural networks (CNNs and recurrent neural networks (RNNs)).

•Topic modeling is unsupervised learning where algorithms find new categories in documents. For example, this technique might look at patient comments about care and extract common themes. The most common algorithms for this are latent dirichlet allocation (LDA) and latent semantic analysis (LSA). LDA assigns topics to arrangements of words, e.g., n-grams such as left ventricular hypertrophy for a topic related to medicine. LSA computes how frequently words occur in the documents, and the whole corpus, and assumes that similar documents will contain approximately the same distribution of word frequencies for certain words.

  

11.4 LARGE LANGUAGE MODELS (LLMS)

  

  

This section will discuss the evolution of large language models, beginning with Word2vec, which is not an LLM but an early way to embed words. LLMs are a rapidly evolving topic, with over 500 LLMs rumored to exist by mid-2023. LLMs are examples of “generative AI,” where a text prompt may produce text, images, music videos and other outputs. ⁷

Word2vec (word to vector) is a neural network method developed by Google to create word embeddings and has been around since 2013. In addition to its utility as a word-embedding method, some of its concepts are effective in creating recommendation engines (e.g., recommending words in a word processor. “Word2vec is a group of related models that are used to produce word embeddings. These models are shallow, two-layer neural networks that are trained to reconstruct linguistic contexts of words. Word2vec takes as its input a large corpus of text and produces a vector space, typically of several hundred dimensions, with each unique word in the corpus being assigned a corresponding vector in the space. Word vectors are positioned in the vector space such that words that share common contexts in the corpus are located close to one another in the space.” ⁸

BERT (Bidirectional Encoder Representations from Transformers) is an NLP model developed by Google in 2018. BERT’s key technical innovation is applying the bidirectional training of transformers, a popular attention model, to language modeling. Transformers “pay attention” to the words most useful in predicting the next word in a sentence. This contrasts with previous efforts (recurrent neural networks or RNNs), which looked at a text sequence, whereas BERT can analyze “bidirectionally.” RNNs tended to make the model slower and less accurate and had difficulty handling a long paragraph. Transformers allow parallelization (multiple computational processes carried out simultaneously) of word embedding. BERT has been pre-trained on Wikipedia and BooksCorpus and requires task-specific fine-tuning. This is, therefore, an example of “semi-supervised learning.” BERT’s bidirectional encoding allows it to determine the position of each word in a sequence, while Word2Vec embeddings cannot account for word position.

  
![](images/image-WO07J1PT.png)  

Figure 11.6 Named entity recognition

  

In addition to NLP, transformers are used to compose music, generate images from text descriptions, write code, predict protein structures, and perform image and video analysis. Both Facebook and Google have teams working on transformers. BERT is open-source and downloadable.⁹

GPT (generative pre-training transformer3) appeared in 2017 from OpenAI.org and was modified in 2020 as GPT-3.¹⁰ ChatGPT (3.5) was released in November 2022 and consists of a transformer platform and reinforcement learning from human feedback (RLHF). In March 2023, GPT-4 was released, which will eventually allow the uploading of images for manipulation with text prompts. The ability to upload images is on hold due to privacy concerns. This newest version consists of ChatGPT plus several visual foundational models.¹⁰ The GPT models are trained on a huge corpus of information, resulting in billions of parameters. It only requires brief instructions (prompts) to generate new text output, such as a story, text message, website creation, and programming language. Unlike Bert, GPT analyzes text unidirectionally and requires less training data due to its massive pre-training.¹¹

The application programming interface (API) was released for GPT-3.5 and GPT-4, so multiple software companies are using this platform. ChatGPT offers a free and subscription product. OpenAI has also released CoPilot, which can assist programming, and DALLE-E2, which can create images from text. ¹⁰

The three business applications for LLMs currently are chatbots, creation of content, and code assistants. New applications continue to arise. The addition of ChatGPT plug-ins will expand the use of LLMs in multiple fields. As of May 2023, 735 plug-ins have been identified. ¹²

Many people have experimented with using ChatGPT for medical questions, and the results overall are good. However, several caveats are worth mentioning:

•The model trained in the September 2021 timeframe, so more recent information is not available.

•The model may “hallucinate” or provide plausible but incorrect information.

•No references are provided. On request, ChatGPT/GPT-4 will produce references, but these may be hallucinated as well.

•LLMs do not always give consistent answers. The answers, based on the same prompt, may change over time.

•There are many questions about the short and long-term costs of LLMs.

•There are many legal questions that have been raised.

•There are privacy concerns.

•There are concerns regarding bias, given the fact that most medical data the LLM trained on reflect a white majority population.

As of mid-2023, two GPT-4 LLMs include references: Perplexity AI and Bing Chat.¹³-¹⁴ This provides a higher confidence or trust level, as the answers provided by AI can be checked.

There is a separate movement to create Auto-GPT LLMs that will create its own research and prompts. Some view this as the beginning of general artificial intelligence.

Additionally, there are multiple new LLMs that are biomedical, and many have trained on PubMed, so that we can expect biomedical chatbots in the near future. These LLMs are still in development, so we do not know if they will outperform ChatGPT/GPT-4. The following is a list of current biomedical chatbots as of March 2023:

•Med-PaLM 2 ¹⁵

•BioBert ¹⁶

•PubMedBert ¹⁷

•ClinicalBert ¹⁸

•Biomegatron ¹⁹.

•PubmedGPT ²⁰

•BioGPT ²¹

•GatorTron ²²

Large language models are being created at a rapid pace by multiple companies competing in a marketplace with many potential customers. Currently, these models are extremely interesting, but it is too early to understand their potential impact on healthcare.

  

#### 11.4.1 Graphs From Text

  

An interesting use case for generative AI, not mentioned in the prior sections, is the ability to create graphs from text. The graphs are also called network and knowledge graphs.

The medical text (prompt) below generated the graph seen in Figure 11.7, using GraphGPT. ²³

“A 44-year-old woman with a history of obesity, diabetes, and hypertension presents with three days of sharp right sided chest pain made worse by coughing. She has a history of tuberculosis and a 20-pack year history of smoking.”

The text below created Figure 11.8.

“New York City has five boroughs: Manhattan, Brooklyn, Queens, The Bronx and Staten Island. Manhattan as 240 Starbucks, Brookly has 60, Queens has 75, The Bronx has 40 and Staten Island has 3.”

It is hoped that in the future LLMs can not only create complex graph databases, but query them as well.

  
![](images/image-0AMORBC5.png)  

Figure 11.7 Graph from medical text

  
![](images/image-147ZM80L.png)  

Figure 11.8 Graph from non-medical text

  

#### 11.4.2 Code Assistants

  

ChatGPT and GPT-4 provide coding assistance. There is also a plug-in for ChatGPT known as Code Interpreter that assists programming with Python. It can handle large files, up to 100MB.¹⁰ Other LLMs can also program in R and SQL. While they can be very useful and help with efficiency, they can occasionally produce bogus results. For example, using the LLM Claude AI, a classification model was created to predict heart disease using logistic regression.²⁴ Despite the programming language, dataset and algorithms being identical to those used in Orange, the results on test data were substantially worse compared to Orange. It is likely that pre-processing was different for the two programs. The greatest benefit at the moment is to assist an experienced programmer with mundane and repetitive tasks.

Section Summary: LLMs have a significant potential in healthcare to assist in diagnosis, treatment, and a variety of administrative tasks. However, there are various concerns, some of which are listed below:

•The potential for hallucinations is great enough to view LLMs as experimental (beta) tools that must be validated and verified. LLMs are an extremely new development, so future LLMs may be more reliable and trustworthy.

•It is important to understand that it is very expensive to train a model, resulting in a huge carbon footprint. Therefore, the short and long term return on investment for the vendor and the user remain unclear.

•Legal concerns about privacy are arising, associated with early lawsuits .

•Regulatory and governance concerns have been expressed by many different groups.

•Unintended consequences, such as job loss loom on the horizon.

•Security breaches and hacking are always a concern with any new technology.

At this time of this writing, ChatGPT/GPT-4 and similar LLMs are not recommended as a medical resource for clinical decision support or as a foundational model. However, they can expedite existing administrative processes, summarize articles, and generate letters, such as prior authorization.

  

11.5 SMALL LANGUAGE MODELS (SLM)

  

  

Small language models refer to AI models that have a smaller number of parameters compared to large language models. While large language models, such as GPT-3, have billions or even trillions of parameters, small language models are designed to be more compact and resource-efficient.

The trend of small language models has gained attention due to several reasons: ²⁵-²⁶

•Performance and Efficiency: Research suggests that smaller language models can achieve comparable or even better performance than their larger counterparts in certain tasks. Smaller models can be more efficient in terms of computational resources, memory usage, and inference speed, making them more accessible and cost-effective for deployment.

•Specialized Use Cases: Small language models can be tailored to specific use cases or domains, allowing for more focused and efficient performance. By training models on smaller datasets or fine-tuning them for specific tasks, developers can create models that are optimized for particular applications, resulting in improved accuracy and relevance.

•Scalability and Deployment: Small language models are often more scalable and suitable for deployment on edge devices or in resource-constrained environments. They can be deployed on devices with limited computational power, enabling real-time or offline inference without relying heavily on cloud infrastructure.

•Environmental Impact: Large language models require significant computational resources, leading to higher energy consumption and environmental impact. Small language models offer a more sustainable alternative, reducing the carbon footprint associated with AI model training and deployment.

•Data Efficiency: Small language models can be trained effectively with smaller datasets, making them suitable for scenarios where limited labeled data is available. This can be particularly beneficial in domains where data collection or annotation is challenging or expensive.

The development and exploration of small language models aim to strike a balance between performance, efficiency, and practicality. While large language models have demonstrated impressive capabilities, small language models offer advantages in terms of resource utilization, customization, and sustainability. Ongoing research and advancements in small language models continue to shape the landscape of AI language processing.

  

11.6 ORANGE NLP WIDGETS

  

  

With the before-mentioned background in NLP, let us explore what Orange has to offer by presenting several of the more important widgets.

  

#### 11.6.1 Text Document Widgets

  

•Corpus : there are five preloaded text documents available for mining. To visualize, use the Corpus Viewer widget.

•Import Documents : a means to upload documents for mining

•The Guardian : a news resource

•NY Times : a news resource

•PubMed : medical journal article or abstract text can be requested

•Twitter : Twitter feeds for mining

•Wikipedia : encyclopedia type information for mining

  

#### 11.6.2 Preprocess Text Widget

  

This widget prepares the document for mining by applying the following steps:

•Transformation: can convert to lowercase, remove accents, parse html (leave text only) and remove urls.

•Tokenization: The default is Regexp (regular expression language) set on “/w+” meaning split into words (no punctuation). Other choices are split by words and keep punctuation, split text by whitespace, sentence will split by full sentences, and Tweet, which will retain hashtags and emoticons.

•Normalization: applies stemming. The default is the Porter Stemmer.

•Filtering: where you can remove stopwords, and with Regexp you can remove punctuation. One can also upload a list of stopwords. With document frequency, one can keep tokens depending on their frequency, and most frequent tokens means it keeps the most frequent tokens with a default of 100.

•N-grams Range: default is 1-2, meaning 1-2 words. This is modifiable.

•POS Tagger: labels e.g., verb, noun, etc. The default is averaged perceptron tagger.

  

#### 11.6.3 Document Embedding Widget

  

•This widget converts documents into vectors using pre-trained fastText models. It aggregates ngrams (words) into vectors. It was trained in 157 languages.

•Language (English) must be selected, and the aggregator is mean by default.

•Primarily used for document/text classification

•Connect a Corpus widget to the Document Embedding widget and connect to a Data Table widget.

  

11.6.4 Bag of Words Widget

  

•Creates a word vector with the options:

  

![](images/image-TEMD15Y1.jpg)Term frequency: count is the number of times a word occurs. Binary means whether a word appears or does not appear in a document. Sublinear means the logarithm of term frequency.

  

![](images/image-TEMD15Y1.jpg)Document frequency: can be set on none or IDF (inverse document frequency)

  

![](images/image-TEMD15Y1.jpg)Regularization: set to none, L1 (normalizes vector length to the sum of elements) or L2 (Euclidean) that normalizes vector length to the sum of squares.

  

![](images/image-TEMD15Y1.jpg)Use with Word Enrichment widget

  

#### 11.6.5 Topic Modeling Widget

  

•This widget discovers abstract topics in a corpus based on clusters of words found in each document and their frequency.

•The most common algorithms used for dimension reduction and topic modeling in natural language processing (NLP) are Latent Semantic Indexing (LSI) and Latent Dirichlet Allocation (LDA). LDA is available in Orange. LDA is a probabilistic generative model that assigns topics to documents and words to topics.

  

11.7 PUTTING KNOWLEDGE INTO PRACTICE

  

  

The first step is to download the Orange text mining library by going to options in the top menu >> Add-ons >>Text. This step will download a variety of widgets needed.

  

#### 11.7.1 Exercises

  

11.7.1.1 Creating a word cloud with PubMed

  

PubMed will be used to download abstracts dealing with COVID-19. Drag the PubMed widget to the canvas and open. Include your email and go to Advanced search and type in COVID-19 and lower down check the box “Abstract.” Select a time period, such as the last year. The default is to retrieve 1000 records (abstracts). Select Find records, then Retrieve Records and they will be loaded into the PubMed widget. To view them connect to the Corpus Viewer widget. Now connect the Word Cloud widget to the PubMed widget and open. What is wrong with the word cloud? See Figure 11.7. There is too much noise and too little signal. Look at the left column in the Word Cloud widget; you will see mostly stop words. Now run it first through the Preprocess widget with these options selected: Transformation = lower case, Tokenization = Regexp and pattern = \\w+, and Filtering = Stop words. What happened? Look at the word count table on the left now to see the difference. See Figure 11.8. The words can be decreased further by opening the Word Cloud widget and highlighting the most frequent words, e.g., those occurring over 100 times in the list on the left.

The Orange workflow to create the word clouds is shown in Figure 11.9.

  
![](images/image-8Y86R1LL.jpg)  

Figure 11.7 Word cloud without preprocessing

  
![](images/image-RZVU9LXC.png)  

Figure 11.8 Word cloud after preprocessing

  
![](images/image-OEO8YNGZ.jpg)  

Figure 11.9 Word cloud workflow

  

11.7.1.2 Sentiment Analysis

  

In order to use the Twitter widget and analyze Tweets, one needs to apply for a development app with Twitter. Open the app and click on Twitter API Key. Follow the directions in the Twitter widget help section. Once the application is approved, one can fill in the API key and Secret. That is achieved in less than one hour, so now the Tweets can be downloaded. In this instance, we want to mine the Tweets for “COVID vaccine sentiments.” This process was completed on April 12, 2022, so this is cross-sectional and not longitudinal. (this exercise follows the guidance noted for the sentiment analysis widget Help section). See Figure 11.10.

  
![](images/image-GNATF15T.jpg)  

Figure 11.10 Twitter widget

  

The next step is to connect the Twitter widget to the Sentiment Analysis widget. Open that widget and select Vader as the Method and English as the Language.²⁷ When the widget is connected to a Data Table widget, multiple missing data points are noted. The Select Rows widget is inserted to get rid of instances with no data or a result of 0. This reduced the number of instances from 1000 to 279. See Figure 11.11.

  
![](images/image-UL2M97Y5.jpg)  

Figure 11.11 Select rows to get rid of negative values

  

To ensure that only positive, negative, neutral, and compound comments are analyzed, the Select Columns widget is also added to ensure that only pos, neg, neu, and compound are features. See Figure 11.12.

  
![](images/image-48CMGBA4.jpg)  

Figure 11.12 Select columns widget

  

Lastly, look at the Data Table widget to see how the corpus looks. Tweets are rated as positive, negative, neutral, and compound. Compound is the “normalized weighted composite score” from -1 to +1. Negative is less than 0.05, and positive is greater than 0.05.²⁸ See Figure 11.13.

  
![](images/image-5JND6QLN.jpg)  

Figure 11.13 Data Table

  

The next step is to connect the Select Columns widget to a Heat Map widget (select Merge by k-means and Rows = Clustering). Note that there are two major hierarchical divisions, and the top one seems the most negative (dark blue color) (see Figure 11.14). Left-click on negative and drag down to select all sub-groups, and now connect that to a Corpus Viewer widget. There are now 200 negative tweets that can be mined. Highlight the compound score under “Display features’’ and look at the compound score (lower right image) for each negative Tweet. See Figure 11.15. The Orange workflow is displayed in Figure 11.16.

  
![](images/image-E1GU6IQ3.jpg)  

Figure 11.14 Heat map for Tweet Sentiment

  
![](images/image-TLU2Q3E1.jpg)  

Figure 11.15 Corpus Viewer

  

11.7.1.3 Document Embedding and Document Classification

  

This exercise will convert a document to word vectors, and then the goal is to see if the class/outcome/target can be predicted. We will follow the examples given in the widget catalog for the Document Embedding widget. The vectorization (embedding) will be done with pre-trained vectors using fastText. The data came from a GitHub repository that was substantially modified. The raw and modified files have been uploaded our File-Share site. ²⁹

The modification steps are as follows:

1\. The original file contained over 2300 medical procedure transcriptions.

2\. For expediency, the first 100 transcriptions were selected and saved as a CSV file.

4\. The transcriptions were divided into two categories: surgical (including endoscopy) and non-surgical.

5\. This file was inputted into another File widget, and the Role category of “label” was changed to target, and Apply selected.

6\. The File widget was connected to the Corpus widget and then to the Document Embedding widget (language English and aggregator mean).

7\. The Document Embedding widget was connected to the Data Table widget, and the following was created (see Figure 11.17 ). Text is what will be analyzed, and “label” is the target (surgical and non-surgical). To the right of the text column is 300 new columns that are document vectors.

8\. The next step will be to predict the label or output. The File widget is connected to the Corpus widget which is connected to the Preprocess Text widget with all defaults selected:Transformation = lower case, Tokenization = Regexp and pattern = \\w+, and Filtering = Stop words. The Preprocess Text widget is connected to the Document Embedding widget, with the default aggregator being sum. It will take 30-60 seconds to embed the documents. Connect the Document Embedding widget to the Test and Score widget and connect the latter to the SVM, Logistic Regression, and Naive Bayes widgets to classify the documents.

9\. Open the Test and Score widget and select cross-validation =10 and select as the target class “average over classes.”

10\. Logistic regression had the best performance. (see Table 11.2 ). One can now connect to the Confusion Matrix or ROC Analysis widgets.

11\. The Orange workflow is displayed in Figure 11.18

12\. Remember: To save time, only 100 transcriptions were labeled and somewhat arbitrarily into the binary categories of surgical and non-surgical cases. The entire training set should be labeled and run. The model should be tested with test data. Lastly, and probably most importantly, to keep things simple, words such as preoperative and procedure were left in, which undoubtedly were important in classifying the transcriptions. Finding medical transcriptions for educational purposes is very challenging, due to privacy concerns.

  
![](images/image-M787OU3J.jpg)  

Figure 11.16 Sentiment analysis workflow

  
![](images/image-3OSOGHPW.jpg)  

Figure 11.17 Document vectors

  

Table 11.2 Document classification results

  
![](images/image-7EBB76PC.png)  
![](images/image-EH7F98RX.png)  

Figure 11.18 Document classification workflow

  

#### 11.7.2 Maturity Levels

  

Here are three scenarios of text mining application for an organization in the tourism industry at different maturity levels of AI text mining capabilities:

•Low Maturity - Local Tour Guide Company : This small-scale operator decides to use text mining to gain insights into their customers’ feedback. By analyzing reviews and survey responses, the company identifies patterns and common themes that help them understand what tourists like or dislike about their tours. By focusing on improving the highlighted areas, they can enhance the overall tour experience and increase customer satisfaction.

•Mid Maturity - Regional Travel Agency : With several branches and an established online presence, this agency decides to use text mining to better understand and cater to customer preferences. They analyze customer inquiries, social media posts, and online reviews to identify popular destinations, travel trends, and common concerns or complaints. This information enables them to tailor their offerings more effectively, improving their marketing strategies and overall customer service.

•High Maturity - Global Online Travel Platform : This organization is highly digital and data-driven. They use text mining to analyze a vast amount of data from various sources - customer feedback, travel blogs, social media posts, and more. They use these insights to provide personalized travel recommendations, optimize their search engine, and anticipate market trends. They also use text analysis to monitor customer sentiment in real-time, allowing them to respond promptly to changing situations and customer concerns. This strategic use of text mining gives them a competitive edge and helps them provide a superior user experience.

These scenarios demonstrate how organizations can leverage text mining at different stages of digital maturity to gain insights, improve customer experience, and stay ahead of the market trends.

  

#### RESOURCES

  

  

1\. Amazon Comprehend Medical - see what Amazon is up to in the NLP space https://aws.amazon.com/comprehend/medical/

2\. More about Transformers. Towards Data Science https://towardsdatascience.com/transformers-an-exciting-revolution-from-text-to-videos-dc70a15e617b

3\. Transformers in NLP - Analytics Vidhya. https://www.analyticsvidhya.com/blog/2019/06/understanding-transformers-nlp-state-of-the-art-models/

4\. How to solve 90% of NLP Problems: a step by step guide. KDNuggets. https://www.kdnuggets.com/2019/01/solve-90-nlp-problems-step-by-step-guide.html

5\. How BERT and GPT Models Change the Game for NLP. 2020. IBM. https://www.ibm.com/blogs/watson/2020/12/how-bert-and-gpt-models-change-the-game-for-nlp/

6\. Google’s answer to GPT3. Train on a trillion parameters https://arxiv.org/pdf/2101.03961.pdf

7\. Swin Transformer https://arxiv.org/abs/2103.14030

8\. Text Preprocessing. KDNuggets. https://www.kdnuggets.com/2019/04/text-preprocessing-nlp-machine-learning.html#:~:text=Text%20normalization%20is%20the%20process,%E2%80%9D%20to%20just%20%E2%80%9Cstopwords%E2%80%9D

9\. How do Transformers Work in NLP? A Guide to the Latest State-of-the-Art Models. Analytics Vidhya. https://www.analyticsvidhya.com/blog/2019/06/understanding-transformers-nlp-state-of-the-art models/

10\. Twenty resources for NLP and Transformers. Medium.com. https://medium.com/nlplanet/two-minutes-nlp-20-learning-resources-for-transformers-1bbff88b7524

11\. N2C2 NLP Research datasets https://portal.dbmi.hms.harvard.edu/projects/n2c2-nlp/

  

#### REFERENCES

  

  

[1\. Natural language processing \[Internet\]. \[cited 2022 Apr 28\]. Available from: https://en.wikipedia.org/wiki/Natural\_language\_processing](#content0235.xhtml)

[2\. What Is Natural Language Understanding (NLU)? \[Internet\]. MonkeyLearn Blog. 2021 \[cited 2022 Apr 28\]. Available from: https://monkeylearn.com/blog/natural-language-understanding/](#content0235.xhtml)

[3\. What is Natural Language Generation (NLG)? \[Internet\]. Narrative Science. 2020 \[cited 2022 Apr 28\]. Available from: https://narrativescience.com/resource/blog/what-is-natural-language-generation/](#content0235.xhtml)

[4\. Chiusano F. A brief timeline of NLP - NLPlanet - medium \[Internet\]. NLPlanet. 2022 \[cited 2023 Jul 6\]. Available from: https://medium.com/nlplanet/a-brief-timeline-of-nlp-bc45b640f07d](#content0235.xhtml)

[5\. Attention is all you need. Website \[Internet\]. Available from: https://arxiv.org/abs/1706.03762](#content0238.xhtml)

[6\. Analytics Vidhya. Understanding Transformers. \[Internet\]. Available from: https://www.analyticsvidhya.com/blog/2019/06/understanding-transformers-nlp-state-of-the-art models/](#content0238.xhtml)

[7\. The generative AI revolution: Exploring the current landscape \[Internet\]. Towards AI. 2023 \[cited 2023 Jul 10\]. Available from: https://pub.towardsai.net/the-generative-ai-revolution-exploring-the-current-landscape-4b89998fcc5f](#content0242.xhtml)

[8\. Word2vec \[Internet\]. \[cited 2022 Apr 28\]. Available from: https://en.wikipedia.org/wiki/Word2vec](#content0242.xhtml)

[9\. BERT (language model) \[Internet\]. \[cited 2022 Apr 28\]. Available from: https://en.wikipedia.org/wiki/BERT\_(language\_model)](#content0242.xhtml)

[10\. OpenAI. OpenAI \[Internet\]. OpenAI. \[cited 2022 Apr 28\]. Available from: https://openai.com/](#content0242.xhtml)

[11\. Hore S. What are Large Language Models (LLMs)? \[Internet\]. Analytics Vidhya. 2023 \[cited 2023 Jul 8\]. Available from: https://www.analyticsvidhya.com/blog/2023/03/an-introduction-to-large-language-models-llms/](#content0242.xhtml)

[12\. StartupHub.ai \[Internet\]. 2023 \[cited 2023 Aug 9\]. A list of 735 ChatGPT Plugins currently available and their use case. Available from: https://www.startuphub.ai/a-list-of-78-chatgpt-plugins-currently-available-and-their-use-case/](#content0242.xhtml)

[13\. Perplexity AI. \[Internet\]. \[cited 2023 July 7\]. Available from: https://www.perplexity.ai/](#content0242.xhtml)

[14\. Bing Chat. \[Internet\].\[cited 2023 July 7\]. Available from: https://www.microsoft.com/en-us/edge/features/bing-chat?form=MT00D8](#content0242.xhtml)

[15\. Singhal K, Azizi S, Tu T, Sara Mahdavi S, Wei J, Chung HW, et al. Large Language Models Encode Clinical Knowledge \[Internet\]. arXiv \[cs.CL\]. 2022. Available from: http://arxiv.org/abs/2212.13138](#content0242.xhtml)

[16\. Dmis-lab/biobert-base-cased-v1.2 · Hugging Face \[Internet\]. \[cited 2023 Jul 8\]. Available from: https://huggingface.co/dmis-lab/biobert-base-cased-v1.2](#content0242.xhtml)

[17\. Microsoft/BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext · hugging face \[Internet\]. \[cited 2023 Jul 8\]. Available from: https://huggingface.co/microsoft/BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext](#content0242.xhtml)

[18\. Emilyalsentzer/Bio\_ClinicalBERT · Hugging Face \[Internet\]. \[cited 2023 Jul 8\]. Available from: https://huggingface.co/emilyalsentzer/Bio\_ClinicalBERT](#content0242.xhtml)

[19\. Braunstein V, Mani R. Building state-of-the-art biomedical and clinical NLP models with BioMegatron \[Internet\]. NVIDIA Technical Blog. 2020 \[cited 2023 Jul 8\]. Available from: https://developer.nvidia.com/blog/building-state-of-the-art-biomedical-and-clinical-nlp-models-with-biomegatron/](#content0242.xhtml)

[20\. Bolton E, Hall D, Yasunaga M, Lee T, Manning C, Liang P. Stanford crfm introduces pubmedgpt 2.7 b. Stanford Human-Centered Artificial Intelligence; 2022.](#content0242.xhtml)

[21\. BioGPT \[Internet\]. Github; \[cited 2023 Jul 8\]. Available from: https://github.com/microsoft/BioGPT](#content0242.xhtml)

[22\. Yang X, Chen A, PourNejatian N, Shin HC, Smith KE, Parisien C, et al. A large language model for electronic health records. NPJ Digit Med. 2022 Dec 26;5(1):194.](#content0242.xhtml)

[23\. GraphGPT \[Internet\]. \[cited 2023 Jul 15\]. Available from: https://graphgpt.vercel.app/](#content0243.xhtml)

[24\. Claude \[Internet\]. \[cited 2023 Jul 15\]. Available from: https://claude.ai/chats](#content0244.xhtml)

[25\. Wiggers K. VentureBeat. 2021 \[cited 2023 Aug 1\]. Large language models aren’t always more complex. Available from: https://venturebeat.com/business/large-language-models-arent-always-more-complex/](#content0245.xhtml)

[26\. Wang Z (andy). Deepgram. \[cited 2023 Aug 1\]. How smaller language models outperform LLMs - deepgram blog. Available from: https://deepgram.com/learn/the-underdog-revolution-how-smaller-language-models-outperform-llms](#content0245.xhtml)

[27\. Python Sentiment Analysis with Vader. \[Internet\]\[cited 2022 May 9\] Available from: https://www.geeksforgeeks.org/python-sentiment-analysis-using-vader/](#content0253.xhtml)

[28\. Lee KC. Sentiment Analysis — comparing 3 common approaches: Naive Bayes, LSTM, and VADER \[Internet\]. Towards Data Science. 2021 \[cited 2023 Jul 10\]. Available from: https://towardsdatascience.com/sentiment-analysis-comparing-3-common-approaches-naive-bayes-lstm-and-vader-ab561f834f89](#content0253.xhtml)

[29\. No Code Data Science \[Internet\]. \[cited 2023 Aug 27\]. File Share. Available from: https://www.nocodedatascience.net/file-share](#content0253.xhtml)

  

![](images/image-T6V2UV35.jpg)Chapter 12

  

## Integrating Continuous Improvement and Data Science Into Industry 4.0

  

“Nothing we do can change the past, but everything we do changes the future”

— Ashleigh Brilliant

  
![](images/image-M6MTZISG.jpg)  
  

LEARNING OBJECTIVES

  
  

After reading chapter twelve readers should be able to

•Understand the key components of Industry 4.0, Service 4.0, Manufacturing 4.0, Healthcare 4.0, Quality 4.0. Data Science 4.0, and Innovation 4.0 whose goals can only be achieved with Leadership 4.0.

•Understand how to select the best Continuous Improvement (CI) techniques that are aligned to your specific sector 4.0 goals.

•Understand when to apply CI techniques individually and as a hybrid team to achieve specific goals.

•Understand the integration opportunities with data science for various CI techniques to optimize their ability to provide accelerated business results.

•Appreciate the fact that the pursuit of any 4.0 initiative may require a dramatic departure from any current comfort zones and “business as usual” assumptions with the required addition of predictive analytics and AI.

  
  

Chapter 12 Summary

  

  

Industry 4.0, also known as the Fourth Industrial Revolution, is a term that describes the integration of intelligent digital technologies into manufacturing and service processes. Success in Industry 4.0 transcends traditional boundaries between departments and improvement initiatives, calling for a seamless fusion of extraordinary innovations, data science mastery, cutting-edge continuous improvement techniques, inspired leadership, robust risk management, and agile innovation-on-demand systems. The heart of this complex interplay lies in a solid, strategic plan underpinned by a high-performance work culture. This environment doesn’t merely empower employees; it ignites their passion, motivating them to be an integral part of something transcendent, thrilling, and truly groundbreaking. This chapter will discuss how various continuous improvement techniques have integration potential with predictive analytics which defines their next evolutionary step that is required to meet the needs of Industry 4.0.

  

Key Principles

•The successful transition to Industry 4.0 isn’t merely about amassing the requisite technical skills and technologies. It equally necessitates a broad array of non-technical facets, including cultural adaptability, employee motivation, strategic planning, and leadership acumen.

•Soft-skill and management competencies are as critical as technological proficiency for a successful evolution towards Industry 4.0.

•To meet Industry 4.0 goals, all business processes and continuous improvement techniques must embed elements of predictive analytics and AI components.

•As organizations strive towards Industry 4.0 objectives, it becomes essential for all employees to acquire some level of new data science skills to navigate this evolving landscape.

•Industry 4.0 cannot be achieved with a collection of standard industry best practices but rather the integration of evolving, adaptive strategies that reflect the continually shifting landscape of technology and innovation.

  

  

12.1 INTRODUCTION

  

  

In this chapter, our attention centers around the notion that data science, predictive analysis, and AI, while powerful, cannot realize their full potential in isolation. Success can only be achieved when these technologies are pursued with great care, discipline, and synergistically integrated into a multifaceted strategic enterprise effort that matches, if not surpasses, the intelligence of the AI it seeks to incorporate. AI possesses the potential to elevate and expedite many facets of continuous improvement efforts, particularly those involving human brainstorming. With appropriate governance, meticulously curated inputs, effective filtering, and prompt engineering applications, AI chatbots can deliver valuable insights in a matter of seconds. This rapid generation of insights can outpace and often surpass the inconsistent quality that typically characterizes human-led brainstorming sessions.

In the fast-paced world of modern AI, rapid change is not just a necessity, it’s the lifeblood of survival. AI evolutions are so rapid that what was considered cutting-edge at nighttime may be obsolete by the morning hours. This accelerated transformation demands not just traditional CEO leadership, but an upgrade to visionary foresight, steered by the concept of Leadership 4.0. A CEO navigating through Industry 4.0 could be aptly termed as a Chief Enterprise Evolution Officer (CEEO). This innovative role constantly demands adaptation to the swift-paced evolution of technology and artificial intelligence in our increasingly interconnected world.

Navigating through this continuous disruption, Industry 4.0 Leadership needs to be a constant beacon of hope, offering accelerated agility to adapt to major AI innovations that evolve not just annually, but weekly. In this new era, the most elegant and convincing annual strategic plan can be outdated in a mere week due to rapid AI advancements. Therefore, strategic planning must shift from a static annual event to a dynamic, continuous process.

Leadership 4.0 goes beyond guiding strategic transformation and driving innovation. It must nurture a culture of perpetual improvement across all teams, ensuring that an organization remains agile, resilient, and future-ready today. With a CEEO at the helm, an organization does not merely respond to change, but stays one step ahead, shaping the future and carving out a custom niche in the ever-evolving business landscape. CEEOs don’t wait for their most creative employees to finally create a breakthrough, they have AI-accelerated Innovation-on-Demand teams that constantly transform chaos, turmoil, and roadblocks into their own opportunities and industry disruptions. However, delving into AI presents considerable risks and must be undertaken with utmost caution. Taking shortcuts in the data science process can lead to unwanted repercussions where your AI initiative could become an unfortunate feature on ‘walls of shame’, which AI incident trackers are all too keen to publicize.¹-² Therefore, a very thoughtful, meticulous, and disciplined approach to AI is non-negotiable.

[Figure 12.1 displays the teams that a CEEO should create and lead to drive strategic transformations and innovations to meet the challenging needs of Industry 4.0. These teams represent an ensemble of continuous improvement methodologies that are supercharged beyond their standard performance levels with the help of AI to deal with the aggressive goals of Industry 4.0. More supporting details will be covered in this chapter.](#content0258.xhtml)

  
![](images/image-7988OA1T.jpg)  

Figure 12.1 Supporting teams and collaborations required to meet Industry 4.0 goals

  

[Figure 12.2 presents an organizational maturity pyramid for achieving Industry 4.0 goals. It begins with key foundational skills at the base and progresses towards more complex skills at the apex. This pyramid integrates technical capabilities, management skills, continuous improvement initiatives, and risk management, advocating a holistic approach towards Industry 4.0 transformation.](#content0259.xhtml)

Other authors likewise underscore the imperative to harmoniously fuse non-technical proficiencies with technical capabilities. This blend of capabilities significantly enhances the likelihood of success in Industry 4.0 endeavors. ³-⁴

Continuous Improvement (CI) techniques are not just tools, they’re catalysts of change that need to continually evolve and adapt to address the revolutionary transformations businesses require to outperform market and competitive challenges. CI methodologies need to be put in self-diagnostic mode from time to time to ensure that they can meet current challenges as well as the challenges of Industry 4.0 requirements. Take for instance, the humble SWOT (strengths, weaknesses, opportunities, and threats) Analysis technique which should be put in a “SWOT analysis of the SWOT Analysis” self-diagnostic mode to explore opportunities to turbo-boost the performance of this commonly used tool. The SWOT example will be discussed in more detail later in this chapter. A top-tier CI methodology is distinguished by its ability to expedite problem resolutions and goal attainments, transcending mere “business as usual” strategies. Individual and hybrid CI techniques should serve as dynamic accelerators that can put an organization on the fast-track to success.

  

12.2 INDUSTRY AND SECTOR 4.0 INITIATIVES

  

  

Producing goods and offering services are the two sectors that dominate the global economy.⁵-⁶ Both of these business pursuits are undergoing a change known as Industry 4.0, which will transform the service industries into Service 4.0, Healthcare 4.0, and other specialized fields and alter the industries that create things with Manufacturing 4.0.⁷ Here are some details about several 4.0 initiatives:

  
![](images/image-1D0PR5GO.jpg)  

Figure 12.2 Layered organizational maturity skills required to achieve Industry 4.0

  

•Industry 4.0: The concept of Industry 4.0 originated at the Hannover Fair in 2011 and was formally proclaimed as a German strategic plan by the German government in 2013, in order for Germany to assume a leading position in its manufacturing sector. Cyber-physical systems, the Internet of Things, big data, 3D printing, robots, simulation, augmented reality, cloud computing, and cyber security were the nine pillars of Industry 4.0 when it was first introduced. ⁸ Industry 4.0, which is seen as a disruptive breakthrough, intends to significantly increase productivity, while many firms are still in the early phases of implementation. ⁹

•Manufacturing 4.0 aims to build a complex network of interconnected manufacturing systems that can exchange information, analyze it, and use it to trigger clever physical world behaviors. Key technologies, including industrial IoT networks, AI, big data, robots, and automation, are guiding this digital transition. ¹⁰

•Service 4.0 advocates assert that it is a significant opportunity for service providers to advance their efficiency and effectiveness, as well as a chance for service consumers to learn about and gain access to new capabilities that were previously unattainable. ¹¹

•Healthcare 4.0 : This term refers to the fourth industrial revolution in healthcare, which integrates digital technologies, artificial intelligence, and big data to enhance the delivery of healthcare and its results. By utilizing technology to improve patient care, lower costs, and increase efficiency, Healthcare 4.0 seeks to improve healthcare outcomes. Healthcare 4.0 aims to leverage technology to enhance healthcare delivery and results, as opposed to the Quintuple Aim, which focuses on tackling health inequalities and clinician fatigue. ¹²

•The Quintuple Aim for Healthcare: The Institute of Healthcare Improvement first proposed the “Triple Aim” in 2007 which is a concept to improve the patient experience , improve patient outcomes , and lower costs as key to health care transformation. ¹³ Since then, it has grown into the “Quintuple Aim,” which now includes clinician well-being and health equity as essential components for healthcare reform. According to research, clinical outcomes and patient satisfaction are directly impacted by professional involvement and wellbeing. Additionally, in order to address health equity and revolutionize cardiovascular care internationally, it is crucial to comprehend the socioeconomic determinants of health, which account for 70% of outcomes. ¹⁴

•Quality 4.0 is a term used to describe the digitalization of quality management through the application of traditional and Industry 4.0 technologies. It involves the use of emerging digital technologies and Industrial Transformation methodologies to transform quality management and achieve step-change improvements in the value-chain across product development, suppliers, operations, logistics, and customer experience. Quality 4.0 aims to leverage new technologies to mobilize the practice of quality management and organizational excellence, with a focus on lowering costs, improving quality, easing compliance, and increasing the efficiency of quality operations. ¹⁵

•Data Science 4.0 can optimize industrial, manufacturing, and service processes by combining advanced data analytics, machine learning, and AI. Operations, quality assurance, supply chain management, and predictive maintenance are revolutionized utilizing data-driven techniques to increase productivity, encourage innovation, and open up new potential for growth. It can also help to identify defects, anomalies, and unhappy customers. Data Science 4.0, in its essence, is the fusion of data science and Industry 4.0, which uses the power of data to improve the outcomes within established sectors. ¹⁶

•Innovation 4.0 can propel organizations towards Industry 4.0 attainment by sparking disruptive transformations on demand in products, services, and processes. By synergizing structured innovation techniques like Blue Ocean, ¹⁷ TRIZ, ¹⁸ Design Thinking, ¹⁹ Lean Startup, ²⁰ Open Innovation, ²¹ BACUP Method, ²² and other techniques with AI chatbot-enhanced brainstorming to accelerate the ideation process with high value ideation. Structured Innovation techniques that are AI-enhanced can take the randomness out of the innovation process and accelerate it greatly. The usage of advanced prompt engineering can also refine AI chatbot innovation brainstorming outputs, with domain experts providing a final layer of review. Innovation 4.0 can also create breakthroughs in systems that link AI, IoT, and advanced analytics, with the potential to redefine manufacturing and service landscapes. Ultimately, Innovation 4.0 can fuel an industrial revolution with unique innovations for digitalization, automation, and data-driven insights with AI supported brainstorming inputs.

Since Industry 4.0’s initial introduction, its nomenclature and contents have been refined by numerous industries and nations, resulting in unique and non-standard titles for many of the movement’s essential components. Automation, digitization, network-linked components, and the unprecedented shrinking of electronics can be used to further summarize Industry 4.0. Table 12.1 summarizes some of the common and unique features of various sector 4.0 initiatives. This table is not intended to be exhaustive in its listings.

Healthcare in the USA is a sector in great need of disruptive improvements and support from the best innovation-on-demand and CI initiatives, based on these lackluster published outcomes:

•In 2016, the United States ranked 34th among all countries on life expectancy. ²³

•Life expectancy in the U.S. fell by 2.7 years from 2019 to 2021, while in peer countries, life expectancies fell by an average of just 0.2 years in the same period. ²⁴

•The U.S. has the lowest life expectancy among large, wealthy countries, despite spending more on healthcare than its peers.

•Some studies have estimated that medical errors may account for as many as 251,000 deaths annually in the United States, making medical errors the third leading cause of death. ²⁵ Other reports claim the numbers to be as high as 440,000. ²⁶

Numerous advantages are promised by Industry 4.0, including increased flexibility, higher quality, reduced costs, and increased efficiency. The seamless integration of physical and digital systems, data-driven decision-making, and the ability to customize production to specific client requirements are where it differs from Industry 3.0. However, different sectors, nations, industries, and enterprises have different perspectives on what “4.0” means and how to adapt to this evolution.²⁷

  

Table 12.1 Key components of Industry 4.0 and selected 4.0 Initiatives

  
![](images/image-OST30CSN.jpg)

  

12.3 ACCELERATING INDUSTRY 4.0: THE PIVOTAL ROLE OF CONTINUOUS IMPROVEMENT (CI) PROGRAMS

  

  

Continuous Improvement (CI) techniques are not just tools, they’re catalysts of change that need to continually evolve and adapt to address the revolutionary transformations businesses require to outperform market and competitive challenges. CI methodologies need to be put in self-diagnostic mode from time to time to ensure that they can meet current challenges as well as the challenges of Industry 4.0 requirements. Take for instance the humble SWOT Analysis technique which should be put in a “SWOT analysis of the SWOT Analysis” self-diagnostic mode to explore opportunities to turbo-boost the performance of this commonly used tool. A top-tier CI methodology is distinguished by its ability to expedite problem resolutions and goal attainments, transcending mere “business as usual” strategies. Individual and hybrid CI techniques should serve as dynamic accelerators that can put an organization on the fast-track to success.

Just as Lean and Six Sigma techniques joined forces to create Lean Six Sigma (LSS) in the early 2000s, the fusion of LSS, High Reliability Organizations (HRO), Cascading Risk Management (CRM), and other Continuous Improvement (CI) programs with data science/AI can offer a formidable hybrid technique to further sharpen efficiency, reduce variation, and create rapid disruptive innovations. This hybridization is not optional for those who pursue industry 4.0 goals. This chapter will discuss how data science and AI do not compete with LSS and other CI programs, but rather offer a dynamic union proposition between these techniques that can offer reduced times between problem definition and solution implementation while offering more efficient root cause analysis, innovative solutions and error-proofed solutions. Modern AI Chatbots, such as GPT-4, can supplement LSS problem-solving teams with an additional AI brainstorming team member that can provide feedback within seconds to augment the intelligence and innovation power of problem-solving teams. Predictive analytics can improve root cause analysis techniques and offer more accurate root cause importance ranks than classic statistics which are often prone to overly optimistic overfitting.

This chapter emphasizes the construction and refinement of a high-performance assembly of eleven CI techniques listed below, harmonized to address Industry 4.0 challenges. Each technique, optimized individually, can collectively contribute to form a dynamic ensemble, which can be a catalyst for next-generation multi-million-dollar solutions and millions of customer smiles. Here is an introduction to the dynamic 11 CI techniques that can accelerate Industry 4.0 outcomes which will be discussed in more detail later in this chapter:

1\. Hoshin Kanri with Catchball Strategic Planning: Combining explicit strategic goal-setting with iterative feedback to empower and engage most groups of employees to be collaborative partners in the pursuit of the company’s vision. ²⁸

2\. Six Sigma: Reduce variations and defects to reduce costs and improve customer satisfaction. ²⁹

3\. Lean / Kaizen: Rapidly identify and address the 8 forms of waste in targeted business processes. ³⁰

4\. Lean Six Sigma: A combination of Lean and Six Sigma techniques to address more complicated problems.

5\. Predictive Modeling: Advanced statistical analysis to pinpoint root causes and predict future events.

6\. High Reliability Organizations (HRO): Safeguard high-stake activities through error-proofed communications. ³¹

7\. Agile versus Waterfall thinking: Waterfall methodology is a linear, sequential design and problem-solving process where progress flows through pre-defined stages, with one stage needing to be completed before moving onto the next. Agile methodology is an iterative approach to project management that prioritizes flexibility and customer feedback, frequently through continuous improvement iterations. ³²

8\. Cascading Risk Management (CRM): Identify and address interconnected and systemic organizational risks. ³³

9\. AI Systems: Autonomous systems that learn and make decisions akin to humans. ³⁴

10\. AI Chatbots: Elevating CI team brainstorming and ideation processes by incorporating AI Chatbots as collaborative brainstorming members. ³⁵

11\. Innovation-On-Demand Techniques: Rapid disruptive innovation through analysis of groundbreaking patents and other novel innovation generating techniques. ³⁶ - ³⁹

It takes a symphony of incremental improvements tempered with disruptive technologies to realize the vision of Industry 4.0. Business executives who are orchestrating this transition can be viewed as daydreamers who are constantly looking for ways to increase their income and profits. While some factions inside corporations are dedicated to zealously reducing prices for current goods and services, others are motivated to open up new markets with innovative goods and services. CI programs can help reduce the costs and improve the quality of current and newly planned goods and services.

It can be very misleading to read reports that continuous improvement (CI) programs, including Six Sigma, Lean, and predictive modeling, have high published failure rates. Instead of being a reflection of some catastrophic flaws in the CI programs themselves, these failure rates of CI programs frequently reflect management’s inability to plan, motivate, inspire, deal with skepticism, and drive major change. CI programs can be crucial in supporting Industry 4.0 aspirations, serving as the levers of transformation, and directing the industries towards a more affluent future when properly executed and tailored to a firm and their culture.

  

12.4 ELEVEN POWERFUL CONTINUOUS IMPROVEMENT TECHNIQUES

  

  

Many operational improvement techniques can come together to promote ongoing breakthroughs, cut costs, ignite innovation, and build a solid basis for accomplishing strategic goals and Industry 4.0 aspirations. This section explores eleven such strategies that, when used individually or in concert, can help firms reach their most ambitious goals. Each business must assess these strategies and tailor them to fit its particular needs, taking into account its size, the nature of its products and services, and the progress and aggressiveness of its strategic planning projects.

  

#### 12.4.1 Hoshin Kanri with Catchball Strategic Planning

  

Hoshin Planning, or Hoshin Kanri, originated in post-World War II Japan as a response to the need for systematic strategic planning during the country’s rebuilding phase. This method, developed in the 1960s and 1970s, drew on management philosophies and quality control principles, including those from W. Edwards Deming and Joseph M. Juran. These teachings highlighted the significance of clear goal-setting, robust communication, and employee involvement in planning. Translated as “compass management,” Hoshin Kanri provides a direction-guiding framework for organizations.⁴⁰

Japan’s quality revolution was fueled by strategic tools such as the “7 Management Tools, ⁴¹ “7 Quality Tools, ⁴² “7 forms of Waste,” ⁴³ and Lean methodologies. Notably, Hoshin Planning was central to many companies that won the Deming Quality Award in the 70’s and 80’s, exemplifying its importance. ⁴⁴ While the western world often cherry-picked from the many tools that drove success in Japan, many failed to successfully implement the more complex methods like Hoshin Planning. However, with the advent of mind mapping software like MindGenius, the construction of these detailed plans is now much easier to create and update.⁴⁵ There are several free software options available for creating mind maps. Here are some popular ones: Miro, XMind, EdrawMind, Coggle, Scappe, and others.⁴⁶

A Hoshin Plan includes five levels of detailed work breakdown: Vision, Goal, Objectives, Action Plans, and Detailed Tasks. Each level supports the one above it, creating a comprehensive and connected plan. This planning methodology ensures that all activities are aligned with the overall vision, identifying and visually representing any gaps or risks. While traditional project management techniques often lack this holistic view, Hoshin Planning provides a robust, integrated and visual approach to achieving strategic goals and visions.

A Hoshin Plan should incorporate 5 levels of detailed work breakdown structure as shown in Figure 12.3.

  
![](images/image-AIULYG6W.jpg)  

Figure 12.3 The 5 levels of work breakdown structure used in Hoshin Plans

  

Here are some explanations of the terms used in Figure 12.3:

•Vision : A mental image what the desired future should look like

•Goal : The full set of top level targets required to support the Vision

•Objectives : The full set of stated intentions required to support all of the Goals

•Tasks : The full set of actions required to support all of the Objectives

•Detailed Tasks : The full set of detailed tasks required to support all of the general tasks

Note that the words “full set” are used often in the above list. In a good Hoshin Plan, each term to the right of the Vision should include a full set of exhaustive intentions and activities required to support the term to the upper left of it.

[Figure 12.4 shows a template for a 5-level Hoshin Plan with 5 levels, with added information in the far right branch for responsible resources, detailed task completion rate, start and completion dates and visual color codes for the detailed task status (red, yellow or green). This example is partially visualized, only showing the details for Goal 1. Red denotes that the plan is behind schedule. Green means that it is on schedule. This template was created in MindGenius software.](#content0263.xhtml)

The Hoshin Planning process includes strategic plan development by top management, goal identification by leadership and executives, collaborative goal-setting through the ‘catchball’ process, goal alignment using a Hoshin Matrix, implementation, continuous review and improvement. This comprehensive approach promotes alignment, communication, and progress towards the attainment of strategic goals.

  

12.4.1.1 Integration Opportunities with Data Science

  

The future of Hoshin Planning, a critical component of strategic planning, is poised for transformative integrations with data science techniques (ML/AI) to create more effective and dynamic strategic planning. Consider these prospects:

•Real-Time Performance Tracking: Harness automated systems to monitor process and operational performances to compare them to the targets. Compare these metrics instantly against target objectives, facilitating rapid adjustments and maintaining strategic alignment.

•Competitive Sentiment Analysis: Implement text and sentiment analysis on various data sources such as of competitor websites, social media, customer reviews, and industry reports. This allows for a comparative study of customer sentiment between your offerings and those of your competitors, enabling a better understanding of market standing.

•Customer Segment Analysis: Utilize text analysis to dissect customer segments and profiles, analyzing their behaviors, preferences, and purchasing patterns. Leverage these insights to customize your products or services, optimizing them for the unique needs of each customer segment.

•Social Network Analysis : Employ Social Network analysis to decipher relationships and power dynamics among competitors, customers, and other market players. This analysis is invaluable in identifying potential partnerships or threats, equipping you to adapt your strategic plans effectively.

•AI Chatbots as Collaborative CI Team Members: AI chatbots have the potential to become indispensable contributors within any team, particularly those engaged in freeform brainstorming. Harnessing their capabilities can inspire new avenues of thought, broadening the scope of ideas and innovation.

  

#### 12.4.2 Six Sigma

  

Six Sigma is a set of techniques and tools for process improvement that was introduced by American engineer Bill Smith while working at Motorola in 1986.⁴⁷ The term “Six Sigma” comes from statistics, specifically from the field of statistical quality control, which evaluates process capability. Originally, it referred to the ability of manufacturing processes to produce a very high proportion of output within an internal or external customer specification. Processes that operate with “six sigma quality” over the short term are assumed to produce long-term defect levels below 3.4 defects per million opportunities (DPMO). Six Sigma is a quality improvement methodology for businesses that counts the number of flaws in a process and aims to systematically reduce them. It is a fact-based, data-driven philosophy of improvement that values defect prevention over defect detection. The goal of Six Sigma is to achieve a level of quality that is nearly perfect, with only 3.4 defects per million opportunities.

  
![](images/image-URKX8WML.jpg)  

Figure 12.4 A Hoshin Planning template

  

Six Sigma projects are led by trained professionals that are referred to as Yellow Belts, Green Belts, Black Belts, and Master Black Belts. Various training companies, the American Society for Quality (ASQ), ⁴⁸ and various universities offer Six Sigma training and certification. The International Association for Six Sigma Certification (IASSC) is also a major source that offers Lean SIx Sigma and Lean certificates.⁴⁹ Each Six Sigma project requires technical mentoring from a Master Black Belt and other organizational assistance. Project selection and deployment are governed by Six Sigma executives and champions. At a high level, they guarantee that projects are successful, valuable, and compatible with the organizational plan.⁵⁰

The ASQ states that professionals with any level of six sigma training earned over $17,000 a year in the USA than those with no training. The reason for this accomplishment is that highly trained and mentored SIx Sigma belts are usually assigned to solve enterprise problems that other ad hoc efforts have not solved. For example, the Six Sigma Academy states that a Six Sigma Black Belt saves their companies $230,000 per project and can complete four to six such projects a year.⁵¹ Figure 12.5 shows a word cloud created from the ASQ Six Sigma Black Belt Body of knowledge (BOK). This word cloud shows that the most common 4 stem words in this BOK are: evaluate, apply, understand, and team. Stem words are the base form of a word, without any affixes (prefixes or suffixes). They are used in natural language processing and text mining to group together words with similar meanings.

Six Sigma is administered by using a structured approach for problem-solving called DMAIC (Define, Measure, Analyze, Improve, and Control) to identify and eliminate causes of variation and improve processes. Six Sigma practitioners use statistics, financial analysis, creative root cause analysis, and project management to achieve improved business functionality and improved quality control by identifying and then correcting mistakes or defects in existing processes. The Six Sigma toolbox has over 150 different individual tools and techniques that can be applied to solve the widest possible array of quality issues. Table 12.2 displays the Strategy of Six Sigma Data Analysis developed by one of the authors (David Patrishkoff) who has extensive Lean and Sigma experiences worldwide since the start of the Six Sigma initiative, as it was applied at AlliedSignal in the mid-1990s before General Electric started with Six Sigma deployments. This table displays a select group of Six Sigma tools that can be used for exploratory data analysis (EDA) and root cause analysis. This is just a small segment of the analysis techniques that relate to the Six Sigma Analyze phase of the Six Sigma DMAIC process.

  
![](images/image-YLGK88CD.jpg)  

Figure 12.5 Word Cloud for the ASQ BOK content for a SIx Sigma Black Belt

  

Table 12.2 Some of the key sequential analysis activities in the Six Sigma Analyze Phase

  

 
| Sequential Analysis Activities || Some Examples of Six Sigma Data Analysis Tools |
| --- | --- |
| 1) Prioritize your Quality Issues || VOC, Pareto Charts and Points of Pain (POP) Brainstorming |
| 2) Identify Potential Root Causes that should be the basis of a detailed data collection strategy || 4W (Who, What, When, and Where) and 6M Fishbone Diagrams & 5 Why Tree Diagram, Value Stream Mapping, Detailed process mapping, & Nominal Group technique. Note: Beware of the biased simple 5 Why technique. |
| 3) Testing if you can you trust your Data || Measurement Systems Analysis (MSA), Gage R&R, Attribute Gage studies, and Calibration studies |
| 4) Identify Data Trends over Time || Time Series / Trend Plots, Multi-vari charts, SPC & Run Charts |
| 5) Understand, Analyze, and Interpret Data Distributions, Process Capability, and outliers || Histograms, Statistical Normality tests, Graphical Summary, Dot Plots, Stem & Leaf graphs, Individual Distribution Identification analysis, Process Capability Analysis, Probability Distribution Plots, QQ plots & Descriptive Statistics |
| 6) Exploratory Data Analysis, Stratification, and Visualizations || Box plots, Dot plots, Line Plot, Bar Chart & Multi-Vari Charts, Parallel coordinate plots, and all stratification plots |
| 7) Hypothesis Testing to determine differences between groups or compared to targets || Various Parametric and Non-parametric Hypothesis Tests, Interval Plots, Test for Equal Variance, One Sample Sign, Chi-Square Test & other Hypothesis Tests |
| 8) Determine valid relationships between one X and one Y-Factor || Scatter Plots, Matrix plots, Marginal Plots, Fitted Line Plots, Correlation Matrix, Scatterplot matrix, & Cross-Correlation. |
| 9) Determine valid relationships between multiple X’s and one Y || Multiple Regression Analysis - Linear and Nonlinear, Screening, Fractional & Full factorial DOEs, Contour Plots, 3D Scatter Plots, Wireframe, & Surface Plots |
| 10) Validation and Optimization || Validation testing and off-the-chart Optimization DOEs |

  

[Table 12.3 shows the capabilities of free open-source software to conduct common Six Sigma analytical tasks for analysis topics 3 to 10 shown on Table 12.1. A score of 10 describes 100% capability of the software to conduct the described tasks. A score of 10 also defines the Six Sigma analysis capability of high-end commercial software such as Minitab and JMP from SAS which is commonly used for Six Sigma projects.](#content0263.xhtml)

According to research by iSixSigma.com, the savings as a percent of revenues from Six Sigma can be expected to be between 1.2 and 4.5%. This data comes from documented savings by Motorola, AlliedSignal, GE, Honeywell, and Ford Motor Company, who were early and disciplined adopters of Six Sigma. These companies invented and refined Six Sigma between the years 1986 and 2000.⁵² The American Society for Quality (ASQ) states that Six Sigma has saved Fortune 500 companies an estimated $427 billion US dollars over the past 20 years.⁵³

  

12.4.2.1 Integration Opportunities with Data Science

  

The future of Six Sigma is ready for transformative integrations with data science techniques (ML/AI). Consider these opportunities for integration:

•Integration with DMAIC : DMAIC (Define, Measure, Analyze, Improve, and Control) is a key methodology in Six Sigma. Data science techniques can be integrated into each phase of DMAIC to enhance data analysis, predictive modeling, and process optimization. ⁵⁴

•Combined roles : There is an opportunity to combine the roles of a Six Sigma Black Belt and a No-Code Data Scientist. This combined role can leverage the statistical and process improvement expertise of Six Sigma with the data analysis and modeling skills of data science. ⁵⁵

•Successful Case study Integrations : Case studies have shown successful integration of Lean Six Sigma and data science approaches. The success of such integrations lies in the fact that both methodologies support the rigorous search for the truth with data analysis. ⁵⁶ - ⁵⁸

•Skill development and training : To effectively integrate Six Sigma and data science, it is important to provide training and certification programs to employees. This ensures that individuals have the necessary skills and knowledge to apply both methodologies effectively. Training in Lean and Six Sigma principles, as well as data science techniques, can help create a culture of continuous improvement. ⁵⁹

•AI Chatbots as Collaborative CI Team Members: AI chatbots have the potential to become indispensable contributors within any team, particularly those engaged in freeform brainstorming. Harnessing their capabilities can inspire new avenues of thought, broadening the scope of ideas and innovation.

  

Table 12.3 Key Six Sigma analysis capabilities for open-source software

  
![](images/image-BZR4FKRT.jpg)

  

#### 12.4.3 Lean / Kaizen

  

Lean was established by Toyota in Japan, in the 1940s and aimed to streamline operational processes by reducing all forms of process waste. An acronym was created to help remember the eight most common forms of waste: TIMWOOD, which stands for excessive Transportation, Inventory, Motion, Waiting, Overproduction, Overprocessing, Defects. An “S” is also added at times to the TIMWOOD acronym to represent underutilized Skills. Today, over 60 different tools and techniques are used to identify and eliminate waste in manufacturing and service transaction processes. Lean techniques can be applied to any industry in manufacturing, service and business transactional processes.

Kaizen is one of the core principles of the Toyota Production System and helps to ensure maximum quality, the elimination of waste, and improvements in efficiency, both in terms of equipment and work procedures. Kaizen involves identifying issues, waste, and opportunities, creating solutions, and rapidly rolling out improvements. Kaizen events are typically focused on smaller process improvements, but they can also be used to rapidly drive big mission-critical improvements. Kaizen events focus on the notion that good people may be trapped in bad processes which create poor business results and that improvement efforts should not blame the people but the flawed processes. Another rule for Kaizen events is to always go to the Gemba (the place where the work is done) when researching the problem to personally see the process waste.⁶⁰

In the USA, four Lean-related Associations (The Society of Manufacturing Engineers - SME, Association for Manufacturing Excellence - AME, the Shingo Institute, and the American Society for Quality - ASQ) have come together and agreed on Body of Knowledge documents for various levels of the Lean expertise.⁶¹ The ASQ Quality Press has also published a book, The Lean Handbook - A Guide to the Bronze Certification Body of Knowledge, to document the details for how Lean is typically practiced in the USA.

A text mining word cloud of this Bronze level lean certification (See Figure 12.6) shows that the three most common stem words used in this Lean Body of Knowledge are system, measure, and process. Too often, Lean is just used as a short-sighted labor and cost cutting tool and not as a system to build a collaborative culture of efficiency. Fujio Cho, former Chairman of Toyota Motor Corporation said in the ToyotaWay book , “Many good American companies have respect for individuals, and practice Kaizen and other TPS (Toyota Production System) tools.⁶² But what is important is having all of the elements together as a system. It must be practiced every day in a very consistent manner–not in spurts–in a concrete way on the shop floor.” ⁶³

  
![](images/image-VJQ5EI43.jpg)  

Figure 12.6 Word Cloud for the Lean Bronze Body of Knowledge

  

[Lean also has an innovation component to it called Kaikaku that originated from the Toyota Production System (TPS) which is used by Toyota. Kaikaku, in contrast to Kaizen, is revolutionary and aims for radical improvements or transformations in an organization. Lean thinking can be used to radically reduce waste and waiting in any process which can be the foundation for many different disruptive innovations. ⁶⁴ Figure 12.7 displays the layered and interactive nature of Lean tools and concepts as well as displaying how Lean can be used as part of innovation creating brainstorming events to create organic growth for an organization.](https://www.industryweek.com/operations/continuous-improvement/article/21144299/why-do-so-many-lean-efforts-fail)

Lean Kaizen events can range in complexity from simple to very complex during a three to five day event. Figure 12.8 shows many of the process analysis options that are available during a typical Kaizen event.

  

12.4.3.1 Integration Opportunities with Data Science

  

The future of Lean / Kaizen includes integrations with data science techniques (ML/AI). Consider these opportunities for integration:

•Data-driven problem-solving : Data science techniques can support Lean / Kaizen problem-solving by providing real-time data on process inefficiencies, bottlenecks, and waste. ⁶⁵

•Real-time Monitoring and Control : Data science techniques, such as real-time data analytics and machine learning, can be used to monitor processes, detect anomalies, predict failures, and proactively flag the need for Lean / Kaizen actions to maintain process stability and quality.

•Predictive Maintenance : Data science can be integrated with Lean/Kaizen to implement predictive maintenance strategies. By analyzing historical data and sensor readings, organizations can predict equipment failures, optimize maintenance schedules, and minimize downtime.

•Value Stream Mapping : Data science can be used to analyze and visualize all value stream performance metrics of interest, identifying areas of waste and opportunities for improvement.

•Continuous improvement through data analysis : Data science can identify and prioritize potential Lean / Kaizen improvement projects by analyzing data from various sources, such as customer feedback, production data, and quality metrics.

•AI Chatbots as Collaborative CI Team Members: AI chatbots have the potential to become indispensable contributors within any team, particularly those engaged in freeform brainstorming. Harnessing their capabilities can inspire new avenues of thought, broadening the scope of ideas and innovation.

  
![](images/image-QL2YXNQM.png)  

[Figure 12.7 The layered nature of how Lean tools and concepts can work together as a system](https://www.industryweek.com/operations/continuous-improvement/article/21144299/why-do-so-many-lean-efforts-fail)

  
![](images/image-ZOT0TLZK.jpg)  

Figure 12.8 Lean tool usage options for a typical Kaizen Event

  

#### 12.4.4 Lean Six Sigma

  

Starting in 2001, Six Sigma and Lean techniques were combined by consulting firms to form the popular Lean Six Sigma methodology which the book author (Dave Patrishkoff) successfully rolled out at Walters Industries starting in 2001 and companies from over 60 different industries worldwide thereafter. This LSS movement was given its official LSS name when Michael George published a book in 2002 with the title: Lean Six Sigma: Combining Six Sigma Quality and Lean Production Speed.⁶⁶

Taken to extremes, Six Sigma or Lean, on their own, could lead to imbalanced results. For example, Six Sigma, without Lean, could lead to high quality goods and services, but their costs could be too high with many non-value-added processes. Lean, without Six Sigma, could lead to the rapid creation of goods and services that had high amounts of costly defects. Hence, the union of these two methodologies has the goal of making high quality products and services more rapidly at the lowest possible costs. Hence, the integration of Lean and Six Sigma is geared towards swiftly and efficiently delivering products and services of superior quality. Figure 12.9 summarizes the logic for combining Lean and Six Sigma .

LSS professionals are trained in how, where, and when to apply their skills. Table 12.4 provides a simplified explanation for when to apply Kaizen, Lean, Six Sigma, and the LSS hybrid technique.

  

12.4.4.1 Integration Opportunities with Data Science

  

The future of Lean Six Sigma (LSS) is poised to synergize with data science techniques as discussed in the preceding Six Sigma and Lean/Kaizen sections. The LSS collaboration between Lean and Six Sigma offers these additional innovative opportunities for improvement:

•Integrated LSS Project Identification and Prioritization: Instead of evaluating Lean/Kaizen and Six Sigma performance data in silos, a more efficient approach involves the integration of these datasets. This comprehensive view allows for an effective prioritization of projects.

•Skill-to-Problem Alignment: Following project identification, a data-driven algorithm can be employed to propose the optimal allocation of team members to each project. This is based on a matching system that aligns each member’s skills with the specific requirements of the problem at hand. Such an integration not only refines the project management process, but it also heightens team performance.

  
![](images/image-SSDAF2F1.jpg)  

Figure 12.9 Lean Six Sigma: A popular hybrid continuous improvement technique

  

Table 12.4 When and where to apply various aspects of LSS

  
![](images/image-CTPWKMXB.jpg)

  

#### 12.4.5 Predictive Modeling

  

While this book extensively covers predictive analytics, this particular section emphasizes the transformative potential of a no-code data science strategy. This approach can effectively generate a sizable group of No-Code Data Scientists (NCDS) faster than traditional programs that focus on coding skills. It equips businesses of all sizes with the technical workforce required to propel their Industry 4.0 initiatives, which are heavily dependent on predictive analytics and AI.

Numerous sources underscore the acute global shortage of data scientists, a demand-supply gap which is industry-specific. The appetite for data scientists is soaring, with employers across sectors grappling to meet this growing demand. This presents an opportunity to leverage the untapped potential of NCDS by offering additional training to professionals already versed in Lean Six Sigma (LSS), such as certified Green, Black, and Master Black Belts.⁶⁷-⁶⁸

The obvious way to rapidly expand the base of data scientists is to train and engage NCDS experts that have already been certified as LSS Green, Black, and Master Black Belts. Such LSS belts already have a heavy dose of statistical analysis training with Minitab, JMP, SigmaXL and other software packages.

LSS professionals have substantial statistical training through tools like Minitab, JMP, SigmaXL, among others, making them excellent candidates for such an expansion of their knowledge. The exact number of Six Sigma professionals worldwide remains uncertain, with estimates ranging from 1.5 million in 2004 to between 4 and 5 million in 2016. ⁶⁹-⁷⁰ Tapping into this existing pool of talent can be an effective strategic move to rapidly scale the base of data scientists to meet the demands of Industry 4.0.

[Figure 12.10 illustrates the distinct and overlapping objectives of the Lean Six Sigma (LSS) and data science domains. By cross-training LSS professionals in No-Code Data Science (NCDS), we not only alleviate the current deficit of data scientists but also enrich the skill sets of LSS professionals. This dual advantage enhances their effectiveness in LSS tasks and broadens their understanding through the added NCDS competency.](#content0266.xhtml)

  
![](images/image-TISBNJDC.jpg)  

Figure 12.10 Distinct and overlapping objectives of the Lean Six Sigma (LSS) and data science domains

  

[Figure 12.11 presents the distinct and common principles between Lean Six Sigma (LSS) and data science. This overlap indicates that LSS professionals possess a foundational knowledge that’s advantageous for transitioning into No-Code Data Science (NCDS). Their pre-existing expertise can serve as a valuable springboard, simplifying the transition to a NCDS role.](#content0266.xhtml)

  

12.4.5.1 Integration Opportunities with Other CI Initiatives

  

Predictive analytics, encompassing tabular data, text, and images, holds the potential to enhance a multitude of human tasks, offering supplementary insights for informed decision-making. This capability unlocks a new level of understanding, fostering innovation and productivity in several diverse fields of endeavor as listed below:

•Real-time analytics for continuous process monitoring

•Predictive maintenance for improved efficiency

•Supply chain optimization

•Data integration and centralization

•Identifying bottlenecks and process improvement opportunities

•Augmented intelligence for decision-making

•Added contributions during freeform brainstorming events

  
![](images/image-J8GTPEZ4.jpg)  

Figure 12.11 Unique and shared concepts for LSS and Data Science

  

#### 12.4.6 High Reliability Organizations (HROs)

  

High Reliability Organizations (HROs) are businesses or other entities that operate in hazardous conditions while maintaining unusually high standards of reliability and safety. These organizations have created procedures and routines that aid in risk reduction and error prevention. The goal of HROs is to minimize communication errors that may result in very unfavorable and harmful occurrences. Communication error- proofing techniques are a crucial component of HROs.

Here are some examples of organizations that use HRO principles:

•Healthcare: HROs in healthcare aim to improve patient safety and reduce errors in care delivery. Examples of healthcare HROs include hospitals, clinics, and healthcare systems. ⁷¹ - ⁷⁴

•Aviation: HROs in aviation focus on safety and reliability in air travel. Examples of aviation HROs include airlines, air traffic control systems, and aircraft manufacturers. ⁷⁵

•Nuclear power: HROs in nuclear power aim to prevent accidents and ensure the safe operation of nuclear power plants. Examples of nuclear power HROs include power companies and regulatory agencies. ⁷⁵

•Military: HROs in the military focus on safety and reliability in military operations. Examples of military HROs include special forces units, aircraft carrier operations, nuclear submarine operations, intelligence agencies, and logistics support organizations. ⁷⁵ - ⁷⁶

Here’s an explanation of HRO principles and communication error-proofing techniques:

High Reliability Organization Principles:

•A just HRO culture is an essential component of becoming a High Reliability Organization (HRO). It involves creating a learning culture where employees are free to speak up and report errors without fear of retribution. ⁷⁷

•Sensitivity to operations: HROs have a heightened awareness of the state of their systems and processes. They actively monitor and respond to potential issues or anomalies to prevent errors from occurring. ⁷⁸- ⁷⁹

•Reluctance to simplify: HROs recognize that work is complex and can fail in unexpected ways. They avoid oversimplification and embrace the complexity of their operations to identify potential risks and prevent errors. ⁸⁰

•Preoccupation with failure: HROs view near misses and failures as opportunities for learning and improvement. They analyze and investigate failures to identify underlying causes and implement corrective actions to prevent similar incidents in the future. ⁸¹

•Deference to expertise: HROs value and respect the expertise of their employees. They encourage open communication and collaboration, allowing frontline workers to provide input and raise concerns regarding safety and reliability. ⁸²

•Resilience: HROs are resilient and have the ability to adapt and recover quickly from unexpected events or failures. They have robust contingency plans and mechanisms in place to respond effectively to disruptions. ⁸³

Communication Error-Proofing Techniques:

•Standardized communication protocols: HROs establish standardized communication protocols to ensure clear and effective communication among team members. This includes using standardized language, formats, and tools for sharing information.

•Closed-loop communication: HROs promote closed-loop communication, where the sender verifies that the receiver has understood the message correctly. This helps to prevent misunderstandings and miscommunication.

•Team training and communication skills development: HROs invest in team training programs and communication skills development to enhance communication effectiveness and reduce the likelihood of errors caused by miscommunication. ⁸⁴

•Redundancy and cross-checking: HROs implement redundancy and cross-checking mechanisms to verify critical information. This involves having multiple individuals independently verify and validate information to minimize the risk of communication errors.

•Use of technology: HROs leverage technology to support communication and reduce the potential for errors. This can include tools such as electronic medical records, barcode scanning systems, and automated alerts for critical information.

•Self-Check using STAR (Stop, Think, Act, Review) process is a self-checking technique used in various industries, including healthcare, to prevent skill-based errors and enhance performance. ⁸⁵

•The 3-Way Repeat Back or 3-Way Read Back is a communication technique used in various industries, including healthcare, to ensure clear and accurate communication and prevent errors. ⁸⁶

•Phonetic & Numeric Clarifications: Examples: A = Alpha, B = Bravo, C = Charlie, D = Delta, E = Echo. ⁸⁶

•SBAR for Handoffs when communicating with others about a problem: Define the Situation, Background, Assessment, and Recommendation.

•Question and Resolve:

  

![](images/image-TEMD15Y1.jpg)Question: HROs encourage questioning and critical thinking to identify potential risks and prevent errors. This involves asking questions to understand the situation, identify potential hazards, and evaluate the best course of action to minimize errors.

  

![](images/image-TEMD15Y1.jpg)Resolve: HROs aim to resolve questions or problems by finding solutions or answers to them. This involves using a systematic approach to problem-solving, such as the STAR (Stop, Think, Act, Review) process, to minimize errors and enhance performance.

•Cross-checking involves watching out for each other and sharing situational awareness to catch potential errors or hazards. ⁸⁷

•5:1 Feedback: The 5:1 feedback ratio emphasizes providing positive feedback at a ratio of five positive comments to one negative comment. The purpose of the 5:1 ratio is to create a balance between constructive feedback and recognition of strengths and achievements. ⁸⁸

Implementing HRO Principles: To implement HRO principles into operations, organizations can consider the following steps: ⁸⁹

•Assess the current state: Evaluate the existing processes, systems, and culture within the organization to identify areas for improvement and potential risks.

•Develop a safety culture: Foster a culture that prioritizes safety, open communication, and continuous improvement. This involves promoting reporting of near misses and errors without fear of retribution and encouraging active participation in safety initiatives.

•Provide training and education: Train employees on HRO principles, communication techniques, and error prevention strategies. This can include leadership training, team training, and ongoing education programs.

•Implement standardized processes: Establish standardized processes and protocols for communication, decision-making, and error prevention. This helps to create consistency and reduce variability in operations.

•Monitor and evaluate: Continuously monitor and evaluate the effectiveness of HRO practices and communication error-proofing techniques. Collect feedback from employees, track safety metrics, and make necessary adjustments to improve performance.

By understanding and implementing HRO principles and communication error-proofing techniques, organizations can improve the safety and reliability of their operations and reduce the likelihood of errors and adverse events.

  

12.4.6.1 Integration Opportunities with Data Science

  

Integration opportunities between data science and High Reliability Organization (HRO) communication error-proofing tasks can be explored in the following ways:

•Predictive Analytics : Use machine learning to predict communication errors based on past data.

•Automated Error Detection : Employ natural language processing for real-time error detection in communication.

•Data Visualization : Display communication error data in intuitive visualizations for easier identification of problem areas.

•System Optimization : Analyze communication networks to find and correct bottlenecks or frequent error points.

•Sentiment Analysis : Implement sentiment analysis to identify risky emotional overtones and improve those communications as needed.

•Simulation and Training : Use machine learning models to simulate error scenarios for training purposes.

•Real-Time Monitoring : Develop systems for immediate error detection and correction in communication channels.

•Decision Support Systems : Create intelligent systems for data-driven decision-making to reduce errors.

  

#### 12.4.7 Agile Versus Waterfall Thinking

  

The terms “Agile Thinking” and “Waterfall Thinking” denote the contrasting mindsets and methods used by the Agile and Waterfall project management systems. Here is a list of their essential qualities: ⁹⁰-⁹²

Agile Thinking:

•Flexibility : Agile thinking emphasizes adaptability and the ability to respond to changes in requirements, priorities, and market conditions.

•Iterative and incremental : Agile thinking promotes an iterative and incremental approach to project development, where work is divided into smaller iterations or sprints.

•Collaboration and customer focus : Agile thinking emphasizes collaboration, frequent communication with stakeholders, and a focus on delivering value to the customer.

•Continuous improvement : Agile thinking encourages a culture of continuous learning and improvement, with regular retrospectives and feedback loops to refine processes and outcomes.

Waterfall Thinking:

•Sequential and structured : Waterfall thinking follows a linear and sequential approach to project development, with distinct phases that must be completed before moving to the next.

•Detailed planning : Waterfall thinking emphasizes upfront planning and documentation, with a focus on defining requirements and scope before starting development.

•Predictability and control : Waterfall thinking aims to provide predictability and control over the project by following a predefined plan and minimizing changes during development.

•Emphasis on documentation : Waterfall thinking places importance on comprehensive documentation to ensure clarity and consistency throughout the project.

[Figure 12.12 shows the basic Agile project management concept. The Agile process is very open to local iterations and experiments to optimize a sub-process before moving to the next process step.⁹³](#content0268.xhtml)

A Waterfall chart (see figure 12.13) assumes that everything will go well along a linear plan of activities. Each phase of the project is completed before moving on to the next, and there is no going back to a previous phase.

When deciding which methodology to use for a project, it’s important to consider the characteristics of Agile and Waterfall thinking and how they align with the project’s requirements, constraints, and organizational context. Agile thinking is often favored for projects with evolving requirements, a need for flexibility, and a focus on collaboration and customer feedback. For projects with clearly defined needs, a set scope, and a need for predictability and control, Waterfall thinking may be more appropriate.

It’s important to note that Agile and Waterfall are not mutually incompatible and that, depending on the particular requirements of the project, hybrid approaches that integrate components of both methodologies may be adopted. A hybrid approach aims to allow for both up-front requirement definition planning and budgeting, while allowing for a more agile approach for design, development, and testing.

  
![](images/image-2HFZKOXP.jpg)  

Figure 12.12 The iterative Agile Process

  
![](images/image-RJ3XDLNZ.jpg)  

Figure 12.13 A Waterfall project management plan

  

It’s important to consider the specific needs, requirements, and constraints of a project when choosing between Agile and Waterfall methodologies. Some projects may benefit from the flexibility and collaboration of Agile, while others may require the structure and predictability of Waterfall. Hybrid approaches that combine elements of both methodologies are also possible, depending on the project’s characteristics and goals.

  

12.4.7.1 Integration Opportunities with Data Science

  

The Agile Methodology:

•Incorporating Agile Best Practices in Data Science : Our 8-step DISCOVER data science methodology seamlessly accommodates the iterative nature of predictive model creation and data science experimentation. By allowing for continuous refinement and feedback loops, we can strive for and achieve the most optimal predictive model. ⁹⁴

The Waterfall Methodology:

•Data science Integration: Opportunities with the Waterfall project management systems are limited on data science projects due to the inherent inflexibility and sequential nature of the waterfall approach. ⁹⁵

  

#### 12.4.8 Cascading Risk Management (CRM)

  

The goal of the risk management strategy known as Cascading Risk Management (CRM) is to stop the replication of comparable hazards at various levels that are initiated internally or externally. Figure 12.14 shows a situation where the risk-focus of an organization was external when the most devastating organizational risks were initiated internally.

Cascading risk refers to the possibility that a single risk occurrence could set off a series of related hazards and cause a cascading effect. Here are some important points:

•Cascading risk management is an approach to risk management that aims to prevent the repetition of similar risks at multiple levels of an organization. ⁹⁶

•Cascading risk can occur when a single risk event triggers a chain reaction of subsequent risks, leading to a cascading effect. ⁹⁷

•Cascading risk management involves identifying and addressing potential cascading risks through a cross-sectoral and multi-risk approach.

•Cascading risk management is particularly relevant in the context of systemic risks, which emerge from the interconnectedness of systems and actors and require a network-based approach to risk management. ⁹⁸

[Figure 12.15 displays the ever-popular SWOT (strengths, weaknesses, opportunities, and threats) analysis which is used to evaluate risks in an organization or project.⁹⁹ Regarding SWOT Analysis, its charm and its significant drawbacks are intrinsically linked to its simplicity. It exemplifies a scenario where adhering to the KISS principle (Keep it Simple, Stupid) could potentially become a pitfall, especially when this simplicity crosses the line into self-destructive superficiality.¹⁰⁰](#content0269.xhtml)

A modern adaptation of the conventional SWOT analysis created by the author (David Patrishkoff) incorporates elements of cascading risk analysis, as illustrated in Figure 12.16. Instead of applying general and unstratified brainstorming using a general SWOT template, this approach encourages the team to conduct a detailed SWOT analysis across six cascading organizational levels: Leadership, Culture, Process, Performance, Response to Critical Issues, and Feedback Loops to Leadership.

  
![](images/image-B8I9ZM9V.jpg)  

Figure 12.14 CRM needs to focus internally and externally for threats

  
![](images/image-OPIIZG95.png)  

Figure 12.15 The ever-popular simple SWOT analysis template

  

An additional refinement to this Cascading SWOT analysis involves executing this exploration separately for internal and external risks, thereby ensuring each category of risk receives an equal degree of scrutiny and consideration. This layered approach facilitates a thorough and targeted examination of organizational risks at various levels, stimulating more insightful and effective risk management dialogues.

  

12.4.8.1 Integration Opportunities with Data Science

  

The integration of cascading risk management and data science offers several opportunities for enhancing risk analysis and decision-making processes. Here are some potential integration opportunities:

•D ata-Driven Risk Assessment : Data science techniques can analyze vast data sources, using machine learning to identify patterns and provide risk assessment insights.

•Early Warning Systems : Predictive analytics and real-time data can be harnessed to develop systems that detect and forecast cascading risks, enabling proactive management.

•Scenario Analysis and Simulation : Techniques like Monte Carlo simulations and agent-based modeling can simulate risk scenarios, assessing potential impacts and informing decision-making.

•Data Fusion and Integration : Integrating diverse data sources allows for a holistic view of risks, facilitating accurate assessments and decision-making.

•Visualization and Communication : Data science can aid in developing interactive visualizations and decision tools, enhancing risk awareness and stakeholder collaboration.

•War-Gaming : AI possesses the capability to generate an array of randomized scenarios encompassing both internal and external risk challenges. These scenarios can serve as practical exercises, enabling teams to rehearse and hone their response strategies.

  
![](images/image-5LIO1IXS.jpg)  

Figure 12.16 Cascading SWOT analysis template

  

#### 12.4.9 AI Systems

  

Industry 4.0, which refers to the incorporation of digital technology into production processes, is supported in a substantial way by AI systems. However, Industry 4.0 in the service industry also needs the backing of AI systems. The following artificial intelligence (AI) solutions are necessary for Industry 4.0 in the manufacturing and service sectors:

•Robotics/Cobotics : In manufacturing processes, collaborative robots (cobots) and AI-powered robots are utilized to automate operations, increase productivity, and improve efficiency. Robots and cobots can be utilized in the service industry in fields like healthcare, hospitality, and retail to automate tasks and enhance customer service. ¹⁰¹

•Internet of Things (IoT): To improve production processes, track equipment performance, and enable predictive maintenance, AI algorithms are used to evaluate data from IoT devices, such as sensors and actuators. ¹⁰²

•Digital Twinning : AI is used to produce digital twins, or copies in the cloud, of real-world objects. To enhance production procedures and product quality, these digital twins can be applied to simulation, optimization, and predictive analysis. Digital twins can be utilized in the service industry to optimize building performance, boost client satisfaction, and increase safety.

•Additive Manufacturing and 3D Printing: AI algorithms accelerate prototype and customization while cutting costs by streamlining the design and manufacturing processes in additive manufacturing and 3D printing. These technologies can also produce custom items such as dental implants and prosthetics for the service industry. ¹⁰³

•Predictive Maintenance : Predictive maintenance uses machine learning algorithms and sensor data to predict equipment breakdowns and schedule maintenance tasks, minimizing downtime and increasing equipment efficiency. Predictive maintenance can be utilized in the service industry to enhance building performance, save energy use, and raise safety.

•Computer Vision : AI-powered computer vision systems are utilized in manufacturing processes for quality control, defect identification, object recognition, and visual tracking. Computer vision can be utilized in the service industry for facial identification, security monitoring, and customer behavior analysis.

•Cyber-Physical Systems : By fusing physical and digital systems, AI algorithms enable the real-time monitoring, regulation, and improvement of manufacturing processes. Cyber-physical systems can be utilized in the service industry to improve building performance, energy efficiency, and customer experience. ¹⁰⁴

•Text Analysis : Textual data created during manufacturing and service processes can be leveraged to derive insights using AI-powered text analysis approaches. This may involve methods like word recognition, sentiment analysis, natural language processing (NLP), and signature verification. Numerous fields, including quality assurance, customer feedback analysis, predictive maintenance, and supply chain optimization, can benefit from text analysis.

•Image Analysis : Visual data created during industrial operations can be analyzed and interpreted using AI-powered image analysis tools. Computer vision, object detection, image recognition, and image captioning are a few examples of this. Additional uses for image analysis include quality control, defect detection, inventory control, and process improvement. ¹⁰⁵

•Interoperability between all physical and digital capabilities : Industry 4.0 relies heavily on interoperability, which means creating seamless communication and combining physical and digital capabilities. Industry 4.0 has a number of challenges, including those related to technical complexity, a lack of standards, and interoperability-related costs. ¹⁰⁶

•AI Chatbots: AI chatbots improve Industry 4.0 by enabling real-time monitoring and predictive maintenance, enhancing customer service, expediting sales and marketing, optimizing supply chains, assisting with staff training, assisting in team brainstorming, assuring quality control, and managing resources effectively. ¹⁰⁷

•Small Language Models : By leveraging AI in small language models, organizations can enhance efficiency, accuracy, and customization in Industry 4.0. ¹⁰⁸

•Sustainability : AI and additive manufacturing can reduce waste by creating items using only the necessary amount of material.

•Quality Assurance : AI can help in real-time monitoring of the 3D printing process to identify and correct defects.

•Supply Chain Improvements : By enabling localized production and reducing the need for physical inventory, additive manufacturing paired with AI can simplify and enhance supply chains.

These applications demonstrate how AI chatbots can streamline processes, improve customer service, optimize operations, and enhance overall efficiency in both manufacturing and service sectors of Industry 4.0.

  

#### 12.4.10 AI Chatbots

  

AI chatbots offer a wide range of rapidly evolving and exciting capabilities in support of the manufacturing and service sectors that are in pursuit of Industry 4.0 and other goals. Before we list the capabilities of AI chatbots, it is crucial for all AI chatbot users to fully understand the limitations, and risks involved in such usage which we describe below:

  

12.4.10.1 Limitations and Risks

  

Important considerations, limitations, and risks regarding AI chatbot capabilities and usage:

•While certain AI chatbots boast capabilities such as analytical analysis and predictive modeling, generally as components of subscription-based services, their performance might not always meet expectations. Our preliminary evaluations reveal that the analytical performance of the Claude 2 AI chatbot, for instance, significantly underperforms when compared to conventional predictive analytics. We foresee potential improvement in the efficacy of AI chatbots over time. However, as it stands, we urge users to exercise considerable discretion and caution. Moreover, results obtained from these analytical chatbots should ideally be benchmarked against traditional analysis platforms prior to their application in real-world scenarios.

•When AI chatbot outputs are leveraged for team problem-solving events or any other applications, they are not to be accepted at face value. It’s crucial to remember that the insights provided by AI systems, while often valuable, are not infallible and can be biased by the data they were trained on. We highly recommend a thorough review and validation of these outputs by subject matter experts before they are considered credible and actionable. This validation process helps in eliminating potential errors and aligning the AI-driven insights with human expertise and judgment.

•The potential ethical and privacy ramifications of employing AI chatbots should also be considered. These systems should always collect and utilize data in a way that respects consent and privacy. Additionally, the systems must be transparent in how they function and make decisions, as well as being built to eliminate any forms of bias and discrimination.

•Articles, blogs, and other publicly accessible content that solely emphasize the benefits of AI chatbots without addressing their potential risks warrant meticulous scrutiny. It’s crucial to maintain a balanced perspective that acknowledges both the upsides and challenges inherent to this technology.

•AI chatbots, especially large language models trained on the entire spectrum of Internet content, may not always align with a specific organization’s objectives. Tailoring chatbots to learn from trusted, organization-specific internal documents can potentially yield more relevant and effective results for unique applications within the given organization.

•These disclaimers underline the necessity for a vigilant and mindful approach when interacting with and utilizing AI chatbots. While these systems can provide useful assistance and insights, their capabilities should not overshadow the value of human judgment and expertise.

•Other authors mention several other risks and concerns that should not be ignored. ¹⁰⁹ - ¹¹¹

  

12.4.10.2 Manufacturing Sector Application Examples

  

Here is a comprehensive list of AI chatbot application potential. This list is subject to the before-mentioned risks and limitations associated with AI chatbot usage:

•Customer Support: AI chatbots can handle customer inquiries, provide product information, and assist with troubleshooting. ¹¹²

•Process Automation: Chatbots can automate repetitive tasks, such as order processing and data entry, improving efficiency. ¹¹³

•Quality Control: Chatbots can analyze data from sensors and cameras to detect defects or anomalies in products, enhancing quality control processes.

•Predictive Maintenance: Chatbots can monitor data from connected devices and sensors to predict equipment failures and schedule maintenance activities.

•Inventory Management: Chatbots can provide real-time information on stock levels, track orders, and generate purchase orders, optimizing inventory management.

•Production Assistance: Chatbots can assist operators at machines, providing guidance and answering questions about machines or processes. ¹¹⁴

•Recall Procedures: Chatbots can facilitate the recall process by providing information and instructions to employees and customers.

  

12.4.10.3 Service Sector Application Examples

  

•Customer Support: AI chatbots can provide 24/7 customer support, answering inquiries, and resolving issues.

•Appointment Scheduling: Chatbots can automate the scheduling of appointments, saving time for both customers and service providers. ¹¹⁵

•Sales Assistance: Chatbots can assist customers in shortlisting products and making purchasing decisions based on historical data and machine learning algorithms.

•Notifications and Updates: Chatbots can notify employees and customers about updates, such as delivery status and conditions, improving communication and saving time.

•Personalized Recommendations: Chatbots can analyze customer preferences and behavior to provide personalized product recommendations, enhancing the customer experience.

These applications demonstrate how AI chatbots can streamline processes, improve customer service, optimize operations, and enhance overall efficiency in both manufacturing and service sectors of Industry 4.0. As previously noted, certain risks and limitations apply.

  

12.4.10.4 Prompt Engineering

  

Prompt engineering is an emerging and essential aspect of AI chatbot utilization, focusing on the development of effective instructions or prompts to guide AI models towards generating the most relevant and accurate responses. As outlined in the referenced article on prompt engineering, this method requires precision and expertise. ¹¹⁶

In today’s AI-driven landscape, prompt engineers are highly valued assets for organizations striving to optimize their engagement with AI chatbots, as emphasized in the referenced blog which also highlights the importance of prompt engineers.¹¹⁷ They can play a crucial role in tuning models to respond with pinpoint accuracy to specific queries.

Success in prompt engineering often hinges on an iterative approach that involves a balance between complexity and efficiency. While various strategies might be suggested for effective prompt engineering, a widely accepted best practice is to test and contrast a comprehensive prompt engineering strategy with a more simplistic approach. Assessing the quality of the results helps in determining the optimal balance between simplicity, sophistication, and relevance.

Most experts in the field of prompt engineering advocate for substantial experimentation. Iteratively testing and refining the prompts allows for continual improvement, leading to a more finely-tuned interaction between users and AI chatbots. Here again, we see the importance of data science experiments that can also be applied to improve AI chatbot interactions and outputs. By embracing this evolving component of AI, organizations can achieve more nuanced, targeted, and effective engagements with their chatbot systems. Here are some references that suggest various detailed tips for creating successful prompts. ¹¹⁸-¹²²

  

#### 12.4.11 Innovation-On-Demand Techniques

  

Innovation-on-demand techniques refer to methods and approaches that enable organizations or individuals to generate innovative ideas and solutions as needed. These techniques aim to foster creativity and problem-solving abilities to meet specific innovation requirements and goals.

The Innovation-on-Demand experts at Ideation International have created a variety of sophisticated innovation software products over the years.¹²³ Those experts highlight one brainstorming optimization technique that anyone can apply, as illustrated in Figures 12.17 and 12.18. Figure 12.17 shows the basic brainstorming dilemma where the brainstorming facilitator is usually gifted with great outputs for a short period of time, after which the facilitator must put pressure and “squeeze” participants for more ideas.

  
![](images/image-NN2UE177.jpg)  

Figure 12.17 A typical brainstorming event output curve

  

[Figure 12.18 demonstrates the approach of a proficient brainstorming facilitator when encountering the idea burnout phase during an event. They subtly shift the focus of the brainstorming session to a different facet of the problem at hand, providing participants with a chance to rejuvenate their internal innovation engines for fresh idea generation. A competent facilitator arrives prepared for such eventualities, equipped with several topics for brainstorming, each representing a distinct segment of the original problem defined for the event.](#content0272.xhtml)

Ideation International, Inc, a US company founded in 1992, is a world leader in developing software to help organizations and individuals with the essential need of innovation on demand, complemented with educational programs and analytical services.¹²³ Ideation International recently unveiled a groundbreaking approach through the fusion of AI chatbots and their Open-Source software, the Express Innovation Situation Questionnaire (EISQ). Acting as a digital detective, EISQ meticulously solicits information from problem-solvers, creating a comprehensive understanding of the problem before the innovation process unfolds. This information is then synthesized into a “Super Prompt” package, sent to ChatGPT, which promptly responds with multiple creative solutions.

The trials of this unique integration highlighted the transformative power of Super Prompts, amplifying ChatGPT’s outputs to a quality indistinguishable from those produced by trained Innovation Masters. Conversely, without these Super Prompts, the results were noticeably less refined, emphasizing their critical role in enhancing the quality of suggestions.

Ideation’s fusion of AI chatbots with EISQ is not just an evolution but could prove to be a revolution in problem-solving, with its instant outputs matching the quality of the best innovative problem-solving masters. Ideation International’s offering of this open-source system provides innovators and problem-solving a new platform from which rapid problem-solving experiments can be tested.¹²⁴

Some resources and approaches related to innovation-on-demand techniques include:

•“Innovation on Demand: New Product Development Using TRIZ”: This book by Victor Fey and Eugene Rivin explores the TRIZ methodology, which leverages creative principles extracted from successful patented inventions to facilitate the generation of innovative ideas. ¹²⁵

•“Everything You Need to Know to Innovate on Demand”: This article provides insights into the art of innovation and highlights the importance of methods like the Socratic method in fostering innovative thinking. ¹²⁶

•“On-Demand Innovation: Get innovation on tap when you select people by their talent. Gain these 8 great advantages”: This resource discusses the advantages of selecting talented individuals for innovation teams to ensure a steady flow of on-demand creativity and ideas. ⁶

•“How to innovate ‘on demand’: This LinkedIn article explores five patterns (subtraction, division, multiplication, etc.) that often lead to new and successful products. ¹²⁷

  
![](images/image-31NUALUX.jpg)  

Figure 12.18 Improved brainstorming event output curve

  

•The Blue Ocean Strategy is a business-level strategy that aims to create new market spaces with little or no competition by providing value innovation. It is about creating and capturing uncontested market space, thereby making the competition irrelevant. ¹²⁸

•“The Lean Startup: How Today’s Entrepreneurs Use Continuous Innovation to Create Radically Successful Businesses”: The Lean Startup gives entrepreneurs, in businesses of all size, a means to test their vision continuously and adapt and alter before it’s too late, saving time spent on time-consuming business planning. ¹²⁹

•“The Innovator’s Dilemma: When New Technologies Cause Great Firms to Fail”: The bestselling classic on disruptive innovation, by renowned author Clayton M. Christensen. ¹³⁰

•“Directed Evolution: Philosophy, Theory and Practice” by Boris Zlotin and Alla Zusman, 2001. ¹³¹

These before-mentioned resources offer different perspectives and methodologies for fostering innovation on demand. It’s important to explore and adapt these techniques based on the specific needs, context of your innovation goals, and organizational culture.

  

12.4.11.1 Integration Opportunities with Data Science

  

AI chatbots can enhance brainstorming event outputs in various ways:

•Idea Generation: AI chatbots can generate new ideas based on their vast knowledge, adding a unique perspective to the brainstorming session.

•Idea Categorization: Chatbots can automatically categorize and organize ideas based on pre-set or learned parameters, making the review process more efficient.

•Real-time Fact Checking: They can validate information on the spot, ensuring the credibility and viability of ideas.

•24/7 Availability: Chatbots can be used at any time, offering flexibility for team members in different time zones or with different schedules.

•Documentation: AI chatbots can keep records of all the ideas and discussions, ensuring no idea is lost and making the follow-up process easier.

•Encouraging Participation: Some individuals may feel more comfortable sharing ideas with a chatbot, boosting overall participation.

Remember, while AI chatbots can enhance the brainstorming process, it’s crucial to ensure they are used as supportive tools rather than decision-making authorities, to maintain the human touch in creativity and innovation. As with any brainstorming inputs, subject matter experts must filter the ideas to ensure that they are feasible.

  
![](images/image-6Q9F3RG4.jpg)  

Figure 12.19 A Redwood Family Circle - Image by Bing Image Creator

  

12.5 THE REDWOOD APPROACH: BUILDING BUSINESS RESILIENCE THROUGH COOPERATIVE STRENGTH

  

  

Redwood trees, also known as Sequoias, are some of the oldest and largest living things on our planet that can grow over 350 feet tall and live for over 2000 years. Redwoods thrive by forming so-called family circles and groves, as shown in Figure 12.19. A typical redwood’s root system is only 6 to 12 feet deep, but redwoods create the strength to withstand powerful winds and floods by extending their roots outwards, up to 100 feet from the trunk, where their roots can intertwine with the roots of other redwood trees which increases their stability during strong winds and floods.¹³² Redwood fairy circles are a natural phenomenon that occur when a parent tree dies, and a new generation of trees sprouts from the roots of the older one, creating a circle of interconnected trees that share nutrients and water. These circles are often found around the stump of a logged old-growth tree, and they can contain dozens of trees that are genetically identical to the parent tree.¹³³-¹³⁴

Imagine a business as a group of redwood trees, each tree representing a complimentary part of a business strategy that drives the business towards Industry 4.0. Like redwoods that share nutrients through interwoven roots, these strategies are interconnected, strengthening each other. They form a resilient shield, standing tall against industry ‘storms’, aiding the business’s growth.

•Hoshin Kanri with Catchball Strategic Planning is like the tallest tree in the circle. This tree defines the direction in which the other trees (strategies) will grow. The catchball process , much like sunlight being absorbed and utilized, helps every level of the organization align towards the overall strategic vision.

•Six Sigma and Lean/Kaizen are like the solid, thick trunks of each tree. Six Sigma minimizes variation and defects, ensuring the tree is strong and healthy. Lean/Kaizen identifies waste (diseased branches) and eliminates them, promoting the healthier growth of each tree.

•High Reliability Organizations (HRO) acts as the outer bark of the trees, providing a protective layer that safeguards against harmful external influences. By enabling error-proofed communication, it prevents miscommunications that could hinder the growth of the trees.

•Agile and Waterfall thinking represents the growth strategies for the trees. Waterfall thinking is akin to the tree growing stage by stage, first the roots, then the trunk, followed by the branches and leaves. Agile , on the other hand, represents iterative and adaptive growth, like a tree branching out in all directions, constantly adapting to the light and space available to enable rapid growth.

•Cascading Risk Management (CRM) functions like the root system of the redwood tree grove. The roots explore the soil around them, identifying potential threats (like pests or poor soil conditions) and planning how to mitigate the risks to ensure the healthy growth of the tree.

•Think of Predictive Modeling like a tree’s way of sending food and water to the places they’re most needed. Just like a tree predicts which branches need more nutrients and sends them there, predictive modeling in business uses information to predict and address future needs. It’s like a smart system that knows where to send help before a part of the business even asks for it.

•AI Systems and AI Chatbots are like squirrels and birds in a tree. Just as these creatures move around helping the tree grow and adapt by spreading seeds, AI and chatbots help businesses by automating tasks and sharing information, aiding the company’s growth and adaptability.

•Finally, Innovation-On-Demand Techniques can be viewed as the new seeds the trees produce which are the lifeblood of a thriving ecosystem, much like the vital seeds that ensure a forest’s renewal. Harnessing cutting-edge approaches, we can pave the way for sustained innovation and growth, crafting a dynamic and enduring landscape.

In conclusion, just as each tree in a redwood family circle contributes to the health and growth of the entire grove, each element of the business strategy provides unique benefits to an organization. When they’re integrated and aligned towards common goals, they can greatly enhance a business’s journey towards industry 4.0.

  

12.6 MATURITY LEVELS

  

  

Here are examples of organizations striving for high Industry 4.0 goals with varying levels of efficiency, sophistication, and performance in tool usage:

Low MaturityLevel:

•Example: A local furniture manufacturing company

•This business utilizes basic computer systems for order processing and inventory management, and machinery in their production process is largely manually operated. They are in the early stages of Industry 4.0 adoption, where there is a huge potential for efficiency improvement through automation and advanced digital technologies.

Mid MaturityLevel:

•Example: A regional courier and delivery services company

•The company uses GPS for real-time tracking of packages, has a customer portal for placing and tracking orders, and uses data analytics for route optimization. However, there’s room for increased efficiency and sophistication by implementing advanced AI and machine learning technologies for predictive analytics, autonomous vehicles for delivery, or automated sorting and handling systems.

High MaturityLevel:

•Example: Tesla Inc.

•Tesla, an electric vehicle and clean energy company, exemplifies high-level efficiency and sophistication in pursuit of Industry 4.0. They utilize advanced robotics and automation in their manufacturing process, AI for their self-driving car technology, IoT sensors for real-time vehicle data, and cloud computing for data storage and analysis. They continuously innovate and incorporate cutting-edge technologies to improve efficiency and performance.

To achieve the desired level of organizational maturity in data science, proficiency in data literacy, machine learning literacy, and AI literacy is essential. Figure 12.20 illustrates the varying levels of data science literacy for tabular data, image analytics, and text mining. Through this book, readers have learned how such proficiencies are accessible through data science skill training paired with instruction in free open-source software tools. Such training periods can be reduced dramatically by bypassing the need for traditional coding and programming while still teaching all of the critical elements of data science.

As organizations pivot towards Industry 4.0 goals, it’s imperative to cultivate both foundational and advanced data literacy among a broader segment of their workforce. Such in-depth understanding fosters synergistic collaborations with data science teams and ensures seamless integration of data science within the organization’s continuous improvement endeavors. The expanding realm of no-code data science presents a viable path for swiftly bolstering an organization’s data literacy, particularly for entities targeting Industry 4.0 benchmarks. No-code data scientists can provide invaluable insights to organizations of all scales, particularly beneficial for those without the resources to onboard data scientists from formal university programs.

  
![](images/image-OVCHBLSM.jpg)  

Figure 12.20 The components of data science literacy

  

#### RESOURCES

  

  

1\. Directed Evolution Philosophy, Theory and Practice https://www.trizmantra.com/Learning%20Resource%20files/DirectedEvolutionBook.pdf

  

#### REFERENCES

  

  

[1\. Incidents \[Internet\]. \[cited 2023 Aug 1\]. Available from: https://incidentdatabase.ai/apps/incidents/](#content0258.xhtml)

[2\. AIAAIC Repository https://docs.google.com/spreadsheets/d/1Bn55B4xz21-\_Rgdr8BBb2lt0n\_4rzLGxFADMlVW0PYI/edit#gid=888071280](#content0258.xhtml)

[3\. Schumacher A, Erol S, Sihn W. A Maturity Model for Assessing Industry 4.0 Readiness and Maturity of Manufacturing Enterprises. Procedia CIRP. 2016 Jan 1;52:161–6.](#content0258.xhtml)

[4\. Carreiro SR, Luís MJ. An Industry 4.0 maturity model proposal. Int J Manuf Technol Manage. 2020 Jan 1;31(5):1023–43.](#content0258.xhtml)

[5\. Wikipedia contributors. North American Industry Classification System \[Internet\]. Wikipedia, The Free Encyclopedia. 2023. Available from: https://en.wikipedia.org/w/index.php?title=North\_American\_Industry\_Classification\_System&oldid=1158629534](#content0259.xhtml)

[6\. Wikipedia contributors. Standard Industrial Classification \[Internet\]. Wikipedia, The Free Encyclopedia. 2023. Available from: https://en.wikipedia.org/w/index.php?title=Standard\_Industrial\_Classification&oldid=1161370506](#content0259.xhtml)

[7\. What is the difference between Industry 3.0 and Industry 4.0? \[Internet\]. onupkeep. UpKeep; \[cited 2023 Jul 8\]. Available from: https://www.upkeep.com/learning/industry-3-0-vs-industry-4-0/](#content0259.xhtml)

[8\. Yang F, Gu S. Industry 4.0, a revolution that requires technology and national strategies. Complex & Intelligent Systems. 2021 Jun 1;7(3):1311–25.](#content0259.xhtml)

[9\. Industry 4.0 and the fourth industrial revolution explained \[Internet\]. i-SCOOP. 2016 \[cited 2023 Jul 11\]. Available from: https://www.i-scoop.eu/industry-4-0/](#content0259.xhtml)

[10\. (mep) MEP. 7 Lessons Learned from Industry 4.0 Implementations. IndustryWeek Magazine \[Internet\]. 2023 Feb 28 \[cited 2023 Jul 8\]; Available from: https://www.industryweek.com/technology-and-iiot/article/21260912/7-lessons-learned-from-industry-40-implementations](#content0259.xhtml)

[11\. Wikipedia contributors. Service 4.0 \[Internet\]. Wikipedia, The Free Encyclopedia. 2023. Available from: https://en.wikipedia.org/w/index.php?title=Service\_4.0&oldid=1144530603](#content0259.xhtml)

[12\. Li J, Carayon P. Health Care 4.0: A Vision for Smart and Connected Health Care. IISE Trans Healthc Syst Eng. 2021 Feb 15;11(3):171–80.](#content0259.xhtml)

[13\. The IHI Triple Aim \[Internet\]. \[cited 2023 Jul 11\]. Available from: https://www.ihi.org/Engage/Initiatives/TripleAim/Pages/default.aspx](#content0259.xhtml)

[14\. Itchhaporia D. The Evolution of the Quintuple Aim: Health Equity, Health Outcomes, and the Economy. J Am Coll Cardiol. 2021 Nov 30;78(22):2262–4.](#content0259.xhtml)

[15\. Juran. Juran. 2019 \[cited 2023 Aug 1\]. Quality 4.0: The future of quality? Available from: https://www.juran.com/blog/quality-4-0-the-future-of-quality/](#content0259.xhtml)

[16\. i-SCOOP \[Internet\]. 2017 \[cited 2023 Aug 1\]. Industry 4.0 - is it all about industrial data and analytics? Available from: https://www.i-scoop.eu/industry-4-0/industrial-data-analytics/](#content0259.xhtml)

[17\. Wikipedia contributors. Wikipedia, The Free Encyclopedia. 2023. Blue Ocean Strategy. Available from: https://en.wikipedia.org/w/index.php?title=Blue\_Ocean\_Strategy&oldid=1150950438](#content0259.xhtml)

[18\. Radziwill N. Quality and Innovation. 2012 \[cited 2023 Aug 2\]. All about TRIZ for innovation. Available from: https://qualityandinnovation.com/2012/02/04/all-about-triz-for-innovation/](#content0259.xhtml)

[19\. Linke R. MIT Sloan. 2017 \[cited 2023 Aug 2\]. Design thinking, explained. Available from: https://mitsloan.mit.edu/ideas-made-to-matter/design-thinking-explained](#content0259.xhtml)

[20\. The Lean Startup \[Internet\]. \[cited 2023 Aug 2\]. Available from: https://theleanstartup.com/principles](#content0259.xhtml)

[21\. Chesbrough H. Everything You Need to Know About Open Innovation. Forbes Magazine \[Internet\]. 2011 Mar 21 \[cited 2023 Aug 2\]; Available from: https://www.forbes.com/sites/henrychesbrough/2011/03/21/everything-you-need-to-know-about-open-innovation/](#content0259.xhtml)

[22\. Fulbright R. Innovation assurance using BACUP and Jobs Theory. International Journal of Innovation Science. 2017 Jan 1;9(1):38–52.](#content0259.xhtml)

[23\. US Mortality in an international Context in High and Rising Mortality Rates Among Working-Age Adults https://www.ncbi.nlm.nih.gov/books/NBK571929](#content0259.xhtml)

[24\. How Does US life Expectancy Compare to other Countries? Health System Tracker.org . Available from: https://www.healthsystemtracker.org/chart-collection/u-s-life-expectancy-compare-countries/](#content0259.xhtml)

[25\. Anderson JG, Abrahamson. Your Health Cafe May Kill You: Medical Errors. Stud Health Technol Inform 2017;234:13-17 https://pubmed.ncbi.nlm.nih.gov/28186008/](#content0259.xhtml)

[26\. James JT. A new, evidence-based estimate of patient harms associated with hospital care. J Patient Saf. 2013 Sep;9(3):122–8.](#content0259.xhtml)

[27\. Yang F, Gu S. Industry 4.0, a revolution that requires technology and national strategies. Complex & Intelligent Systems. 2021 Jun 1;7(3):1311–25.](#content0259.xhtml)

[28\. Hoshin Planning \[Internet\]. Gemba Academy. 2020 \[cited 2023 Jul 13\]. Available from: https://www.gembaacademy.com/resources/gemba-glossary/hoshin-planning](#content0260.xhtml)

[29\. Six Sigma Definition - What is Lean Six Sigma? \[Internet\]. \[cited 2023 Jul 13\]. Available from: https://asq.org/quality-resources/six-sigma](#content0260.xhtml)

[30\. The 8 wastes of lean \[Internet\]. The Lean Way. \[cited 2023 Jul 13\]. Available from: https://theleanway.net/The-8-Wastes-of-Lean](#content0260.xhtml)

[31\. Veazie S, Peterson K, Bourne D. Evidence Brief: Implementation of High Reliability Organization Principles. Department of Veterans Affairs (US); 2019.](#content0260.xhtml)

[32\. Moore K. Agile vs. Waterfall: which manager are you? \[Internet\]. monday.com Blog. 2020 \[cited 2023 Jul 13\]. Available from: https://monday.com/blog/project-management/agile-vs-waterfall-which-manager-are-you/](#content0260.xhtml)

[33\. Sulfikkar Ahamed M, Sarmah T, Dabral A, Chatterjee R, Shaw R. Unpacking systemic, cascading, and compound risks: A case based analysis of Asia Pacific. Progress in Disaster Science. 2023 Apr 1;18:100285.](#content0260.xhtml)

[34\. Winston PH. Artificial intelligence (2nd ed.). USA: Addison-Wesley Longman Publishing Co., Inc.; 1984.](#content0260.xhtml)

[35\. Porter E. An introduction to AI chatbots \[Internet\]. Drift. 2019 \[cited 2023 Jul 13\]. Available from: https://www.drift.com/learn/chatbot/ai-chatbots/](#content0260.xhtml)

[36\. Zlotin B, Zusman A. Directed Evolution Philosophy, Theory and Practice. https://www.trizmantra.com/Learning%20Resource%20files/DirectedEvolutionBook.pdf](#content0260.xhtml)

[37\. Wikipedia contributors. Blue Ocean Strategy \[Internet\]. Wikipedia, The Free Encyclopedia. 2023. Available from: https://en.wikipedia.org/w/index.php?title=Blue\_Ocean\_Strategy&oldid=1150950438](#content0260.xhtml)

[38\. Allen FE. There Are Three Kinds of Innovation. Don’t Get Trapped Doing the Wrong One. Forbes Magazine \[Internet\]. 2011 Aug 2 \[cited 2023 Jul 13\]; Available from: https://www.forbes.com/sites/frederickallen/2011/08/02/there-are-three-kinds-of-innovation-dont-get-trapped-doing-the-wrong-one/](#content0260.xhtml)

[39\. Wikipedia contributors. Disruptive innovation \[Internet\]. Wikipedia, The Free Encyclopedia. 2023. Available from: https://en.wikipedia.org/w/index.php?title=Disruptive\_innovation&oldid=1164261091](#content0260.xhtml)

[40\. Wikipedia contributors. Wikipedia, The Free Encyclopedia. 2022. Hoshin Kanri. Available from: https://en.wikipedia.org/w/index.php?title=Hoshin\_Kanri&oldid=1115837264](#content0262.xhtml)

[41\. Hessing T. Six Sigma Study Guide. 2014 \[cited 2023 Aug 2\]. 7M tools/ 7 Management tools. Available from: https://sixsigmastudyguide.com/7m-tools-7-management-tools/](#content0262.xhtml)

[42\. Wikipedia contributors. Wikipedia, The Free Encyclopedia. 2022. Seven basic tools of quality. Available from: https://en.wikipedia.org/w/index.php?title=Seven\_basic\_tools\_of\_quality&oldid=1119218773](#content0262.xhtml)

[43\. Lean Enterprise Institute \[Internet\]. 2020 \[cited 2023 Aug 2\]. 7 wastes. Available from: https://www.lean.org/lexicon-terms/seven-wastes/](#content0262.xhtml)

[44\. Wikipedia contributors. Wikipedia, The Free Encyclopedia. 2022. Hoshin Kanri. Available from: https://en.wikipedia.org/w/index.php?title=Hoshin\_Kanri&oldid=1115837264](#content0262.xhtml)

[45\. Black Apron \[Internet\]. \[cited 2023 Aug 2\]. David patrishkoff”s blog. Available from: http://www.e3.business/blog](#content0262.xhtml)

[46\. Martin M. Guru99. 2023 \[cited 2023 Aug 2\]. 19 best FREE mind mapping software & mindmap tools in 2023. Available from: https://www.guru99.com/mind-mapping-software.html](#content0262.xhtml)

[47\. Wikipedia contributors. Wikipedia, The Free Encyclopedia. 2023. Six Sigma. Available from: https://en.wikipedia.org/w/index.php?title=Six\_Sigma&oldid=1167728702](#content0263.xhtml)

[48\. Six Sigma Belts, Levels & Roles \[Internet\]. \[cited 2023 Aug 2\]. Available from: https://asq.org/quality-resources/six-sigma/belts-executives-champions](#content0263.xhtml)

[49\. International Association for Six Sigma Certification \[Internet\]. International Association for Six Sigma Certification IASSC; 2011 \[cited 2023 Aug 2\]. About. Available from: https://iassc.org/about/](#content0263.xhtml)

[50\. Six Sigma Belts, Levels & Roles \[Internet\]. \[cited 2023 Aug 2\]. Available from: https://asq.org/quality-resources/six-sigma/belts-executives-champions](#content0263.xhtml)

[51\. \[No title\] \[Internet\]. \[cited 2023 Aug 2\]. Available from: https://p.widencdn.net/gsxhe4/41577-Cert-Factsheet-SSBB](#content0263.xhtml)

[52\. Cyger M. isixsigma.com . 2010 \[cited 2023 Aug 2\]. Six Sigma costs and savings. Available from: https://www.isixsigma.com/financial-analysis/six-sigma-costs-and-savings/](#content0263.xhtml)

[53\. \[No title\] \[Internet\]. \[cited 2023 Aug 2\]. Available from: https://p.widencdn.net/babkro/41577-Cert-Factsheet-CSSGB](#content0263.xhtml)

[54\. KNIME \[Internet\]. \[cited 2023 Aug 2\]. Reasons to integrate data science into DMAIC. Available from: https://www.knime.com/blog/dmaic-process-integrate-data-science](#content0263.xhtml)

[55\. Cichonski M. Is data science the next step along the six sigma/continuous improvement journey? Maybe \[Internet\]. 1490276933000 \[cited 2023 Aug 2\]. Available from: https://www.linkedin.com/pulse/data-science-next-step-along-six-sigmacontinuous-maybe-mark-cichonski](#content0263.xhtml)

[56\. Zwetsloot IM, Kuiper A, Akkerhuis TS, de Koning H. Lean Six Sigma meets data science: Integrating two approaches based on three case studies. Qual Eng. 2018 Jul 3;30(3):419–31.](#content0263.xhtml)

[57\. Alberto EC, Macias D, McGovern M, Hernandez-de-Menendez M, Morales-Menendez R. Quality 4.0 – an evolution of Six Sigma DMAIC. International Journal of Lean Six Sigma. 2022 Jan 1;13(6):1200–38.](#content0263.xhtml)

[58\. Lean Six Sigma and Analytics: Integrating Complementary Activities http://gjar.org/publishpaper/vol2issue2/d147r84.pdf](#content0263.xhtml)

[59\. Six Sigma Daily \[Internet\]. 2020 \[cited 2023 Aug 2\]. Getting started with data analytics and lean six sigma. Available from: https://www.sixsigmadaily.com/data-analytics-lean-six-sigma/](#content0263.xhtml)

[60\. Blog T. Toyota UK Magazine. Toyota GB PLC; 2013 \[cited 2023 Aug 2\]. What is kaizen and how does Toyota use it? Available from: https://mag.toyota.co.uk/kaizen-toyota-production-system/](#content0264.xhtml)

[61\. Lean. Body of Knowledge https://www.sme.org/globalassets/sme.org/training/certifications/lean-certification/lean-bok.pdf](#content0264.xhtml)

[62\. The Toyota Way. The Toyota Way. 2015 \[cited 2023 Aug 3\]. The Toyota Way. Available from: https://thetoyotaway.org/](#content0264.xhtml)

[63\. Ledbetter P. Why Do So Many Lean Efforts Fail? IndustryWeek Magazine \[Internet\]. 2020 Oct 9 \[cited 2023 Aug 3\]; Available from: https://www.industryweek.com/operations/continuous-improvement/article/21144299/why-do-so-many-lean-efforts-fail](#content0264.xhtml)

[64\. Kotelnikov V. Kaizen vs Kaikaku: 10 KAIKAKU COMMANDMENTS (By: Hiroyuki Hirano) - Kaizen is evolutionary, focused on incremental improvements. Kaikaku is revolutionary, focused on radical improvements. Lean Manufacturing \[Internet\]. \[cited 2023 Aug 3\]. Available from: https://www.1000ventures.com/business\_guide/mgmt\_kaizen\_vs\_kaikaku\_10c.html](#content0264.xhtml)

[65\. Dhawan R, Singh K, Tuteja A. When big data goes lean \[Internet\]. McKinsey & Company; 2014 \[cited 2023 Aug 3\]. Available from: https://www.mckinsey.com/capabilities/operations/our-insights/when-big-data-goes-lean](#content0264.xhtml)

[66\. Michael George \[Internet\]. \[cited 2023 Aug 3\]. Available from: https://www.leansixsigmadefinition.com/glossary/michael-george/](#content0265.xhtml)

[67\. Nelson A. Rivery. 2021 \[cited 2023 Aug 3\]. Closing the data science skills gap (Part 1): Why is there a gap? Available from: https://rivery.io/blog/closing-the-data-science-skills-gap-part-1-why-is-there-a-gap/](#content0266.xhtml)

[68\. Hughes O. ZDNET. 2022 \[cited 2023 Aug 3\]. Employers are desperate for data scientists as demand booms. Available from: https://www.zdnet.com/article/employers-are-desperate-for-data-scientists-as-demand-booms/](#content0266.xhtml)

[69\. Harry M. isixsigma.com . 2004 \[cited 2023 Aug 3\]. How many Black Belts are there and how can it improve my career? Available from: https://www.isixsigma.com/ask-certification-training/how-many-black-belts-are-there-and-how-can-it-improve-my-career/](#content0266.xhtml)

[70\. Quora \[Internet\]. \[cited 2023 Aug 3\]. How many Six Sigma professionals are there in the world? Available from: https://www.quora.com/How-many-Six-Sigma-professionals-are-there-in-the-world](#content0266.xhtml)

[71\. Veazie S, Peterson K, Bourne D. Evidence Brief: Implementation of High Reliability Organization Principles. Department of Veterans Affairs (US); 2019.](#content0267.xhtml)

[72\. Becoming a high reliability organization: operational advice for hospital leaders https://www.ahrq.gov/sites/default/files/wysiwyg/patient-safety/settings/hospitals/hroadvice.pdf](#content0267.xhtml)

[73\. Lorange Y. High-reliability organizations in healthcare: Framework \[Internet\]. Health Catalyst. healthcatalyst2020; 2018 \[cited 2023 Aug 3\]. Available from: https://www.healthcatalyst.com/insights/high-reliability-organizations-in-healthcare-framework](#content0267.xhtml)

[74\. TeamSTEPPS (team strategies & tools to enhance performance & patient safety) \[Internet\]. \[cited 2023 Aug 3\]. Available from: https://www.ahrq.gov/teamstepps-program/index.html](#content0267.xhtml)

[75\. Wikipedia contributors. Wikipedia, The Free Encyclopedia. 2023. High reliability organization. Available from: https://en.wikipedia.org/w/index.php?title=High\_reliability\_organization&oldid=1159981223](#content0267.xhtml)

[76\. High reliability organization and applicability to the battlefield to reduce errors associated with combat casualty care https://apps.dtic.mil/sti/pdfs/AD1020382.pdf](#content0267.xhtml)

[77\. LeSage P, Boxman L. Journal of Emergency Medical Services. 2018 \[cited 2023 Aug 3\]. Just Culture & High Reliability: The Initial Approach. Available from: https://www.jems.com/news/just-culture-high-reliability-buy-in-commitment-and-trust/](#content0267.xhtml)

[78\. Veazie S, Peterson K, Bourne D. Evidence Brief: Implementation of High Reliability Organization Principles. Department of Veterans Affairs (US); 2019.](#content0267.xhtml)

[79\. Gasaway R. Situational Awareness Matters! ™ . Situational Awareness Matters; 2012 \[cited 2023 Aug 3\]. High reliability organizations - processes - situational awareness matters! ™ . Available from: https://www.samatters.com/high-reliability-organizations-processes/](#content0267.xhtml)

[80\. Pyke T. Reluctance to simplify \[Internet\]. 2020 \[cited 2023 Aug 3\]. Available from: https://www.high-reliability.org/reluctance-to-simplify](#content0267.xhtml)

[81\. Lowers, Associates. The Risk Management Blog | Lowers & Associates. Lowers & Associates; 2017 \[cited 2023 Aug 3\]. Why a Preoccupation with Failure is a Necessity for HROs. Available from: https://blog.lowersrisk.com/failure-hros/](#content0267.xhtml)

[82\. Jacobson G. 5 principles of a high reliability organization (HRO) \[Internet\]. \[cited 2023 Aug 3\]. Available from: https://blog.kainexus.com/improvement-disciplines/hro/5-principles](#content0267.xhtml)

[83\. VBI. HRO Corner: Delving into the “Commitment to Resilience” High Reliability Guiding Principle \[Internet\]. \[cited 2023 Aug 3\]. Available from: http://veteransbenefitsinformation.com/latest-news/10275-hro-corner-delving-into-the-qcommitment-to-resilienceq-high-reliability-guiding-principle.html](#content0267.xhtml)

[84\. Becoming a High Reliability Organization: Operational Advice for Hospital Leaders https://www.ahrq.gov/sites/default/files/wysiwyg/patient-safety/settings/hospitals/hroadvice.pdf](#content0267.xhtml)

[85\. Sowers D. 10/12 Industry Report. 2019 \[cited 2023 Aug 3\]. Toolbox talks: Steps for STAR self-checking. Available from: https://www.1012industryreport.com/uncategorized/steps-for-star-self-checking/](#content0267.xhtml)

[86\. Main Line Health \[Internet\]. \[cited 2023 Aug 3\]. Error Prevention Toolkit. Available from: https://www.mainlinehealth.org/employees/employee-training-videos/error-prevention-toolkit](#content0267.xhtml)

[87\. Connect the Docs \[Internet\]. \[cited 2023 Aug 3\]. Coach and Cross-Check our new residents and fellows. Available from: https://blogs.cooperhealth.org/ctd/2021/07/coach-and-cross-check-our-new-residents-and-fellows/](#content0267.xhtml)

[88\. Elliott M, MBA. Mark Elliott, MD, MBA. 2019 \[cited 2023 Aug 4\]. It’s about time you give yourself 5:1 positive feedback! Available from: https://markelliottmdmba.com/blog/its-about-time-you-give-yourself-51-positive-feedback/](#content0267.xhtml)

[89\. Evidence Brief: Implementation of High Reliability Organization Principles https://www.hsrd.research.va.gov/publications/esp/high-reliability-org.pdf](#content0267.xhtml)

[90\. Kanban Software for Agile Project Management \[Internet\]. \[cited 2023 Aug 4\]. Agile vs Waterfall: Pioneering the old era of project management. Available from: https://kanbanize.com/agile/project-management/agile-vs-waterfall](#content0268.xhtml)

[91\. Hoory L. Agile Vs. Waterfall: Which Project Management Methodology Is Best For You? Forbes Magazine \[Internet\]. 2022 Aug 10 \[cited 2023 Aug 4\]; Available from: https://www.forbes.com/advisor/business/agile-vs-waterfall-methodology/](#content0268.xhtml)

[92\. Davu S. Segue Technologies. 2018 \[cited 2023 Aug 4\]. Waterfall vs. Agile: Which Methodology is Right for Your Project? Available from: https://www.seguetech.com/waterfall-vs-agile-methodology/](#content0268.xhtml)

[93\. Barenscheer T. Official Teamly Blog - Official Teamly Blog - Your Project Management Resource. 2022 \[cited 2023 Aug 4\]. 12 agile project management principles: Optimizing project process. Available from: https://www.teamly.com/blog/agile-project-management-principles/](#content0268.xhtml)

[94\. St-Pierre M. OpenText Blogs. OpenText; 2022 \[cited 2023 Aug 4\]. An agile approach to Data Science. Available from: https://blogs.opentext.com/an-agile-approach-to-data-science/](#content0268.xhtml)

[95\. Hotz N. Data Science Process Alliance. 2018 \[cited 2023 Aug 4\]. What is waterfall? Available from: https://www.datascience-pm.com/waterfall/](#content0268.xhtml)

[96\. Potter F. Cascading Risk Management \[Internet\]. 1518109044000 \[cited 2023 Aug 4\]. Available from: https://www.linkedin.com/pulse/cascading-risk-management-frank-potter](#content0269.xhtml)

[97\. National Disaster Risk Assessment https://www.preventionweb.net/files/52828\_ccrosssectoralmultirisk%5B1%5D.pdf](#content0269.xhtml)

[98\. ReliefWeb \[Internet\]. \[cited 2023 Aug 4\]. Understanding and managing cascading and systemic risks: lessons from COVID-19. Available from: https://reliefweb.int/report/world/understanding-and-managing-cascading-and-systemic-risks-lessons-covid-19](#content0269.xhtml)

[99\. Shewan D. How to do a SWOT analysis (examples & free template!) \[Internet\]. WordStream. 2022 \[cited 2023 Aug 4\]. Available from: https://www.wordstream.com/blog/ws/2017/12/20/swot-analysis](#content0269.xhtml)

[100\. Patrishkoff D. A SWOT analysis of SWOT analysis \[Internet\]. \[cited 2023 Aug 4\]. Available from: https://www.insurancethoughtleadership.com/leadership/swot-analysis-swot-analysis](#content0269.xhtml)

[101\. Burke J. Enterprise AI. \[cited 2023 Aug 5\]. How significant is AI’s role in Industry 4.0? Available from: https://www.techtarget.com/searchenterpriseai/tip/How-significant-is-AIs-role-in-Industry-40](#content0270.xhtml)

[102\. What is Industry 4.0 and how does it work? \[Internet\]. \[cited 2023 Aug 5\]. Available from: https://www.ibm.com/topics/industry-4-0](#content0270.xhtml)

[103\. Belk RW, Belanche D, Flavián C. Key concepts in artificial intelligence and technologies 4.0 in services. Service Business. 2023 Mar 1;17(1):1–9.](#content0270.xhtml)

[104\. Stefanini \[Internet\]. 2020 \[cited 2023 Aug 5\]. The 5 advantages AI can offer Industry 4.0. Available from: https://stefanini.com/en/insights/news/the-5-advantages-ai-can-offer-industry-4-0](#content0270.xhtml)

[105\. Metrology and Quality News - Online Magazine \[Internet\]. Metrology News; 2022 \[cited 2023 Aug 5\]. Image Processing Is Key Technology For Industry 4.0 and Smart Factories. Available from: https://metrology.news/image-processing-is-key-technology-for-industry-4-0-and-smart-factories/](#content0270.xhtml)

[106\. Burns T, Cosgrove J, Doyle F. A Review of Interoperability Standards for Industry 4.0. Procedia Manufacturing. 2019 Jan 1;38:646–53.](#content0270.xhtml)

[107\. Kaustubh (kay) K. Industry 4.0 revolution - Artificial Intelligence, Chatbots and beyond \[Internet\]. 1674837912000 \[cited 2023 Aug 5\]. Available from: https://www.linkedin.com/pulse/industry-40-revolution-artificial-intelligence-chatbots-k-](#content0270.xhtml)

[108\. The rise of small language models: Why they outshine large language models for enterprise AI users \[Internet\]. \[cited 2023 Aug 5\]. Available from: https://code.pieces.app/blog/small-language-models-outshine-large-language-models-enterprise-users](#content0270.xhtml)

[109\. TheStreet \[Internet\]. 2023 \[cited 2023 Aug 5\]. We Asked a Chatbot Why It’s So Dangerous. Available from: https://www.thestreet.com/technology/we-asked-a-chatbot-why-its-so-dangerous](#content0271.xhtml)

[110\. Ferraro M. Tech Policy Press. 2023 \[cited 2023 Aug 5\]. Ten legal and business risks of chatbots and generative AI. Available from: https://techpolicy.press/ten-legal-and-business-risks-of-chatbots-and-generative-ai/](#content0271.xhtml)

[111\. Rana J. The limitations of chatbots: What you need to know? \[Internet\]. REVE Chat. 2023 \[cited 2023 Aug 5\]. Available from: https://www.revechat.com/blog/limitations-of-chatbot/](#content0271.xhtml)

[112\. Eleonora. Chatbots in industry 4.0 \[Internet\]. crafter.ai. 2021 \[cited 2023 Aug 5\]. Available from: https://crafter.ai/en/2021/05/20/chatbots-in-manufacturing/](#content0271.xhtml)

[113\. Botpress Community. Chatbots for manufacturing industry \[Internet\]. \[cited 2023 Aug 5\]. Available from: https://botpress.com/blog/chatbots-for-manufacturing-industry](#content0271.xhtml)

[114\. Puddu A. Zerynth. 2023 \[cited 2023 Aug 5\]. Generative Artificial Intelligence: if we use Chat GPT in Industry 4.0. Available from: https://zerynth.com/blog/generative-artificial-intelligence-if-we-use-chat-gpt-in-industry-4-0/](#content0271.xhtml)

[115\. Özçekiç AF. Chatbots Life. 2017 \[cited 2023 Aug 5\]. The role of ChatBot in industry 4.0. Available from: https://chatbotslife.com/the-role-of-chatbot-in-industry-4-0-acf2b0ac8bb6](#content0271.xhtml)

[116\. IPWITHEASE. What is Prompt Engineering and What are its benefits? \[Internet\]. IP With Ease. 2023 \[cited 2023 Aug 5\]. Available from: https://ipwithease.com/what-is-prompt-engineering/](#content0271.xhtml)

[117\. Hordiienko K. Who are prompt engineers, and why hire a prompt engineering master? \[Internet\]. Serpstat; 2023 \[cited 2023 Aug 5\]. Available from: https://serpstat.com/blog/who-are-prompt-engineers-and-why-hire-them](#content0271.xhtml)

[118\. Unleash the Power of ChatGPT: 11 epic prompt engineering tips! \[cited 2023 Aug 5\]; Available from: https://colinscotland.com/unleash-the-power-of-chatgpt-11-epic-prompt-engineering-tips/](#content0271.xhtml)

[119\. Great Learning. Great Learning Blog: Free Resources what Matters to shape your Career! 2023 \[cited 2023 Aug 5\]. Prompt engineering - complete guide. Available from: https://www.mygreatlearning.com/blog/prompt-engineering-complete-guide/](#content0271.xhtml)

[120\. 5 easy steps for prompt engineering with large language models (LLMs) \[Internet\]. \[cited 2023 Aug 5\]. Available from: https://blog.verta.ai/5-steps-prompt-engineering-llms](#content0271.xhtml)

[121\. Lange K. What is prompt engineering? Strategies for creating effective AI inputs \[Internet\]. Splunk-Blogs. 2023 \[cited 2023 Aug 5\]. Available from: https://www.splunk.com/en\_us/blog/learn/prompt-engineering.html](#content0271.xhtml)

[122\. Koidan K, Yao M. TOPBOTS. 2023 \[cited 2023 Aug 5\]. 10 essential prompt engineering methods for successful ChatGPT & LLM applications. Available from: https://www.topbots.com/prompt-engineering-chatgpt-llm-applications/](#content0271.xhtml)

[123\. Ideation International. https://www.whereinnovationbegins.net/](#content0272.xhtml)

[124\. Zlotin B, Zusman A. and Hohnjec M. TRIZ-based software as a front end to AI Chatbots. Proceedings of the International TRIZ Conference ITC-2023: August 31, September 1-3, Graz, Austria](#content0272.xhtml)

[125\. Fey V, Rivin E. Innovation on Demand: New Product Development Using TRIZ. Cambridge University Press; 2005. 242 p.](#content0272.xhtml)

[126\. LaFleur B. Everything you need to know to innovate on demand \[Internet\]. \[cited 2023 Aug 5\]. Available from: https://info.stonewallco.com/blog/everything-you-need-to-know-to-innovate-on-demand](#content0272.xhtml)

[127\. Drietomska A. How to innovate “on demand” \[Internet\]. 1522102111000 \[cited 2023 Aug 5\]. Available from: https://www.linkedin.com/pulse/how-innovate-demand-andrea-drietomska](#content0272.xhtml)

[128\. Blue Ocean Strategy \[Internet\]. 2021 \[cited 2023 Aug 5\]. What is Blue Ocean Strategy. Available from: https://www.blueoceanstrategy.com/what-is-blue-ocean-strategy/](#content0272.xhtml)

[129\. Ries E. The Lean Startup: How Today’s Entrepreneurs Use Continuous Innovation to Create Radically Successful Businesses. Crown; 2011. 336 p.](#content0272.xhtml)

[130\. Christensen C. The Innovator’s Dilemma: When New Technologies Cause Great Firms to Fail. Harvard Business Review Press; 2013. 288 p.](#content0272.xhtml)

[131\. Directed Evolution Philosophy, Theory and Practice https://www.trizmantra.com/Learning%20Resource%20files/DirectedEvolutionBook.pdf](#content0272.xhtml)

[132\. People O. Sempervirens Fund. 2019 \[cited 2023 Aug 5\]. Redwood Facts. Available from: https://sempervirens.org/learn/redwood-facts/](#content0273.xhtml)

[133\. Benney J. Redwood fairy rings – canyon \[Internet\]. \[cited 2023 Aug 5\]. Available from: https://eastbayhillpeople.com/redwood-fairy-rings-canyon/](#content0273.xhtml)

[134\. Waters D. POST. Peninsula Open Space Trust; 2018 \[cited 2023 Aug 5\]. The Surprising Science of “Fairy Rings.” Available from: https://openspacetrust.org/b](#content0273.xhtml)

  

![](images/image-5LEYZK4S.png)Appendix A

  

Data Visualization

  
![](images/image-MV1PU6MC.jpg)  
![](images/image-6F2XGYFD.jpg)

  

![](images/image-LNEZYFQR.png)Appendix B

  

Machine Learning Algorithms

  
![](images/image-GRMMWMG5.jpg)  
![](images/image-WNYFAUDR.jpg)  
![](images/image-XUDHMWYI.jpg)

  

![](images/image-DSRPXF1H.png)Appendix C

  

## Glossary

  

Data Science Decoded: Definitions supplemented with analogies to clarify complex data science terms in the Book.

•Accuracy (ACC): A measure of how many predictions a model got right out of all the predictions it made.

  

![](images/image-TEMD15Y1.jpg)Analogy: It's like checking how many students' exam outcomes (pass or fail) were correctly predicted by the teacher.

•AdaBoost: A boosting algorithm that fits a sequence of weak learners on repeatedly modified versions of the data.

  

![](images/image-TEMD15Y1.jpg)Analogy: It's like a team of experts where each subsequent expert learns from the mistakes of the previous ones and tries not to repeat them.

•Agile vs Waterfall: Two different project management methodologies. Agile is iterative, while Waterfall is linear and sequential.

  

![](images/image-TEMD15Y1.jpg)Analogy: Going on a road trip – Agile is planning checkpoints along the way with flexibility to change plans. Waterfall is mapping out the entire route and sticking to the plan, regardless of new information or changes along the way.

•AI Chatbot: A computer program that mimics human conversation, either verbally or in written form.

  

![](images/image-TEMD15Y1.jpg)Analogy: Imagine talking to a virtual librarian. You can ask questions and get responses, but the librarian doesn't truly "understand" the conversation – it's just referencing the information it has.

•AI Systems: Computer systems designed to perform tasks that typically require human intelligence.

  

![](images/image-TEMD15Y1.jpg)Analogy: Think of a highly advanced self-driving car. While most cars need a driver to operate, this one can drive itself, interpret road signs, and make decisions based on the traffic around it.

•ARIMA: Autoregressive Integrated Moving Average. A forecasting technique that uses past data to predict future points.

  

![](images/image-TEMD15Y1.jpg)Analogy: Predicting the temperature for the next week based on data from past weeks and the seasonal changes over the year.

•Association Rules: A method to find associations between different items in a dataset.

  

![](images/image-TEMD15Y1.jpg)Analogy: Like a supermarket noticing that if a customer buys diapers, they're likely to also buy baby formula.

•Attention Models: Neural network models that can focus on specific parts of input data.

  

![](images/image-TEMD15Y1.jpg)Analogy: It's like a spotlight on a stage. Although many actors are present, the spotlight focuses on the important ones at a particular moment.

•Bag of Words: A representation of text where the order doesn't matter, only the frequency of words.

  

![](images/image-TEMD15Y1.jpg)Analogy: Consider it like soup. Once the ingredients (words) are in the soup, you can taste everything, but you can't determine the original order they were added.

•Bagging: A method to reduce overfitting by using subsets of data to train multiple models and average predictions.

  

![](images/image-TEMD15Y1.jpg)Analogy: Like asking several friends their opinion on a topic and then taking the majority vote as your final decision.

•Balanced Accuracy (BA): An average of recall obtained on each class, useful for imbalanced datasets.

  

![](images/image-TEMD15Y1.jpg)Analogy: A teacher who's equally good at praising students for their strengths and pointing out areas for improvement.

•Bias Variance Tradeoff: The balance between a model's ability to fit the training data and its ability to generalize to unseen data.

  

![](images/image-TEMD15Y1.jpg)Analogy: Shooting arrows at a target. Bias is the average distance from the bullseye, while variance is how scattered your shots are.

•Bookmaker Informedness: A measure of predictive performance.

  

![](images/image-TEMD15Y1.jpg)Analogy: A bookmaker's ability to predict both winning and losing bets accurately.

•Box Plot: A graphical representation of a dataset's distribution, showing the median, quartiles, and possible outliers.

  

![](images/image-TEMD15Y1.jpg)Analogy: Viewing the silhouette of a bird. You can gauge its overall shape and size, but not the intricate details.

•Calibration Curve: A visualization showing the relationship between predicted probabilities and actual outcomes.

  

![](images/image-TEMD15Y1.jpg)Analogy: Like a car's speedometer. When properly calibrated, the speed displayed matches the car's actual speed.

•Cascading Risk Management: A strategy to address risks in a system where one failure might cause multiple subsequent failures.

  

![](images/image-TEMD15Y1.jpg)Analogy: Imagine dominos falling. If one-piece falls, it can trigger a chain reaction. This method is about placing dominos strategically to limit potential fallout.

•Class Weights: Assigning different importance to classes in classification problems.

  

![](images/image-TEMD15Y1.jpg)Analogy: Valuing the opinion of an expert more than a novice in a discussion.

•Clustering: The process of grouping similar data points together based on certain features.

  

![](images/image-TEMD15Y1.jpg)Analogy: Organizing books on a shelf based on topics or genres.

•CNN (Convolutional Neural Network): A deep learning algorithm mainly used for image processing tasks.

  

![](images/image-TEMD15Y1.jpg)Analogy: Looking at an image through various lenses, each emphasizing different features to recognize the image.

•Cohen's Kappa (KP): A statistic that measures inter-rater agreement for categorical items, considering the possibility of agreement happening by chance.

  

![](images/image-TEMD15Y1.jpg)Analogy: Assessing how two judges in a talent show agree, even if they might occasionally agree randomly.

•Cross-Validation versus Train and Test Splits: Cross-validation involves partitioning data into multiple subsets (or folds) and training/testing on these different combinations, while train/test split divides data into two parts: one for training and one for testing.

  

![](images/image-TEMD15Y1.jpg)Analogy: Think of a dancer rehearsing for a performance. She practices different parts (folds) of her routine (cross-validation) and also runs through the whole routine start to finish (train/test split).

•Data Binning: The process of converting continuous data into discrete intervals or bins.

  

![](images/image-TEMD15Y1.jpg)Analogy: Imagine sorting books on a shelf by height. That's what data binning does.

•Data Cleaning: The process of identifying and correcting (or removing) errors and inconsistencies in data.

  

![](images/image-TEMD15Y1.jpg)Analogy: It's like washing a car before a road trip to start with a clean slate.

•Data Imputation: The method used to replace missing values in datasets.

  

![](images/image-TEMD15Y1.jpg)Analogy: It's like filling in a puzzle with missing pieces using the surrounding pieces as a guide.

•Data Leakage: When information from the testing dataset is used in training the model.

  

![](images/image-TEMD15Y1.jpg)Analogy: It's like peeking at the answers before a test – you might ace it, but it doesn't show your real skills.

•Data Preprocessing: Preparing raw data for analysis and modeling.

  

![](images/image-TEMD15Y1.jpg)Analogy: It's like a chef preparing ingredients before cooking.

•Data Science Experiments: Testing hypotheses or trying out different methodologies in the field of data science to improve the performance of a predictive model.

  

![](images/image-TEMD15Y1.jpg)Analogy: It's like a chef experimenting with different ingredients to craft a new dish.

•Data Wrangling: The process of transforming raw data into a usable format.

  

![](images/image-TEMD15Y1.jpg)Analogy: Like a cowboy rounding up cattle, ensuring they're in the right place.

•Decision Trees: A type of model where decisions are made based on asking a series of questions.

  

![](images/image-TEMD15Y1.jpg)Analogy: It's like playing 20 Questions. Each query narrows down the possibilities.

•Document Embedding: Representing text documents in a numerical format that captures their semantic meaning.

  

![](images/image-TEMD15Y1.jpg)Analogy: Think of it as turning a book into a movie trailer – capturing its essence in a different, compact form.

•Dummy Variable Trap: When categorical variables are highly correlated (i.e., one can be predicted from the others).

  

![](images/image-TEMD15Y1.jpg)Analogy: Like having a switch that can be on or off. If you know it's on, you know it's not off.

•Elastic Net Regression: A type of regression that combines both L1 and L2 regularization.

  

![](images/image-TEMD15Y1.jpg)Analogy: Like a soccer coach selecting players based on individual skills and team dynamics.

•Ensemble Models: Using multiple models and combining their predictions.

  

![](images/image-TEMD15Y1.jpg)Analogy: It's like asking several friends for movie recommendations and taking all their opinions into account.

•F1 Pos & F1 Neg: Measures that combine precision and recall for both positive and negative outcomes respectively.

  

![](images/image-TEMD15Y1.jpg)Analogy: Like trying to fish effectively – catching many (recall) but also the right ones (precision).

•False Negatives (FN): Incorrectly predicting the absence of a condition.

  

![](images/image-TEMD15Y1.jpg)Analogy: Predicting it won't rain, but it does.

•False Positives (FP): Incorrectly predicting the presence of a condition.

  

![](images/image-TEMD15Y1.jpg)Analogy: Predicting rain, but it's sunny.

•Feature Engineering: Creating new features from the existing ones.

  

![](images/image-TEMD15Y1.jpg)Analogy: Cooking. Raw ingredients (data) can be combined and processed to make a meal.

•Feature Scaling: Adjusting the range of multiple variables so they can be compared on common grounds, such as from zero to one.

  

![](images/image-TEMD15Y1.jpg)Analogy: It's like using a universal ruler to measure both the length of a pencil and the height of a building, ensuring both are represented on a scale from 0 to 100.

•Fowlkes-Mallows Index (FMI): A measure that evaluates clustering quality considering both precision and recall.

  

![](images/image-TEMD15Y1.jpg)Analogy: Evaluating a group project by considering both individual input and teamwork.

•Geolocation Analysis: Analyzing data that has a geographical or spatial aspect.

  

![](images/image-TEMD15Y1.jpg)Analogy: Using a map to track and understand patterns, like a bird's migration route.

•Gradient Boosting: An ensemble method that builds sequential trees, where each tree tries to correct the mistakes of the previous one.

  

![](images/image-TEMD15Y1.jpg)Analogy: A group project where after each presentation, feedback helps the next student do better.

•Gradient Descent: An optimization algorithm to minimize errors in predictions.

  

![](images/image-TEMD15Y1.jpg)Analogy: Descending a mountain blindfolded by always taking a downhill step.

•High Reliability Organizations (HRO): Organizations with systems designed to prevent catastrophes in a risky environment where accidents can be expected.

  

![](images/image-TEMD15Y1.jpg)Analogy: A rehearsed orchestra where every player knows their part, making mistakes a rarity.

•Hoshin Kanri: Also called policy deployment. A strategic planning tool used in management to align a company's strategy with its plans and actions.

  

![](images/image-TEMD15Y1.jpg)Analogy: It's like a GPS for a company, ensuring every department is headed in the right direction towards the company's main goal.

•Hypothesis Testing: Evaluating two contradictory theories using data.

  

![](images/image-TEMD15Y1.jpg)Analogy: It's like a court trial where the null hypothesis is the presumption of innocence, and the alternate hypothesis suggests guilt. You weigh evidence (data) to reach a verdict.

•Imbalanced Data: When the distribution of classes within a dataset is uneven.

  

![](images/image-TEMD15Y1.jpg)Analogy: Like a fruit basket containing 95 apples and 5 oranges. If you grab at random, you'd almost always get an apple, giving a skewed view of the basket's contents.

•Innovation on Demand vs Random Brainstorming: The first is a structured approach to innovation, the second is sporadic.

  

![](images/image-TEMD15Y1.jpg)Analogy: One is like having a workout schedule, while the other is like exercising whenever you feel like it.

•Internal vs External Validation: Testing a model's performance on known data versus completely new data.

  

![](images/image-TEMD15Y1.jpg)Analogy: It's akin to a singer rehearsing a song at home (internal) and then performing it at a concert (external).

•Kaizen Events: Focused events aimed at improving specific processes.

  

![](images/image-TEMD15Y1.jpg)Analogy: Improve and organize the home.

•Kaplan-Meier Survival Analysis: Estimating the time until a specific event happens, considering censored data.

  

![](images/image-TEMD15Y1.jpg)Analogy: Like tracking the longevity of a group of plants, recognizing that some may still be alive at study's end.

•K-Nearest Neighbors: Classification algorithm based on the proximity to known data points.

  

![](images/image-TEMD15Y1.jpg)Analogy: Picking a restaurant in a new town by checking out where the most locals go.

•Lasso vs Ridge Regression: Regularization techniques; Lasso might reduce some coefficients to zero, while Ridge just adjusts them.

  

![](images/image-TEMD15Y1.jpg)Analogy: Lasso is like a sculptor chipping away unnecessary marble, whereas Ridge smoothens all parts of the sculpture for harmony.

•Lean Six Sigma (LSS): A methodology that combines process speed with quality.

  

![](images/image-TEMD15Y1.jpg)Analogy: It's like an athlete training to run faster but ensuring each step is perfectly placed.

•Lean: A philosophy of streamlining processes and removing waste.

  

![](images/image-TEMD15Y1.jpg)Analogy: Like decluttering a room, keeping only what's essential.

•Lift Curve: A graph showing the advantage of using a predictive model versus random guessing.

  

![](images/image-TEMD15Y1.jpg)Analogy: Choosing a fishing spot based on where fish are biting, versus picking a spot at random.

•Linear Regression: Predicting a continuous response variable based on one or more predictors.

  

![](images/image-TEMD15Y1.jpg)Analogy: Predicting the growth of a plant based on the amount of water and sunlight it receives.

•Local vs Global Minimum: Points in optimization; local is the lowest within a nearby range, global is the lowest overall.

  

![](images/image-TEMD15Y1.jpg)Analogy: Finding valleys in a mountain range: some are deep (global minimum), others are shallow dips (local minimum).

•Logistic Regression: Predicting a binary outcome using one or more predictors.

  

![](images/image-TEMD15Y1.jpg)Analogy: Predicting whether a light will be red or green based on the current traffic flow.

•LogLoss: A measure of error where wrong predictions, especially with high confidence, are penalized.

  

![](images/image-TEMD15Y1.jpg)Analogy: Like taking a multiple-choice test where wrong answers deduct more points if you're very confident in your (incorrect) choice.

•MAPE (Mean Absolute Percentage Error): Average percentage error between observed and predicted values.

  

![](images/image-TEMD15Y1.jpg)Analogy: Like measuring how off the mark an archer is, on average, in percentage terms.

•Markedness (MK): An indicator of a model's ability to avoid false classifications.

  

![](images/image-TEMD15Y1.jpg)Analogy: Like a watchman's efficiency in catching real threats while avoiding false alarms.

•MCC (Matthews Correlation Coefficient): A measure of the quality of binary classifications.

  

![](images/image-TEMD15Y1.jpg)Analogy: Like assessing a goalkeeper's skill by considering both saves and goals allowed.

•Model Bias: When a model consistently misses the target in a particular direction.

  

![](images/image-TEMD15Y1.jpg)Analogy: Like a golfer whose shots consistently veer to the left.

•Model Fairness: Ensuring that models perform equally well across different groups.

  

![](images/image-TEMD15Y1.jpg)Analogy: Like a referee ensuring each team gets equal and fair chances during a game.

•Model vs Algorithm: A model is the outcome of applying an algorithm on data.

  

![](images/image-TEMD15Y1.jpg)Analogy: Building a puzzle (model) using a particular method (algorithm).

•Multicollinearity: When two or more predictors in a model are highly correlated.

  

![](images/image-TEMD15Y1.jpg)Analogy: Like having twin players on a basketball team; their skills overlap, making it hard to determine each one's unique contribution.

•Naive Bayes: A classification algorithm that calculates the probability of an event based on prior knowledge.

  

![](images/image-TEMD15Y1.jpg)Analogy: Choosing an outfit based on the weather forecast. You consider if it's rainy, sunny, or snowy — all separately (naively) — to decide on your attire.

•Negative Predictive Value (NPV): The likelihood that a negative prediction is correct.

  

![](images/image-TEMD15Y1.jpg)Analogy: After predicting rain and taking an umbrella, it's the chance that it actually does rain.

•Neural Networks: Complex systems that simulate the behavior of the human brain to process data.

  

![](images/image-TEMD15Y1.jpg)Analogy: Imagine a factory assembly line. Each worker (neuron) processes a task (input) and passes it on, and the final product (output) results from everyone's contribution.

•NLP (Natural Language Processing): Helping computers process and understand human language.

  

![](images/image-TEMD15Y1.jpg)Analogy: Like teaching a robot to read a book and summarize it for you.

•No Regularization Regression: A regression without any mechanism to prevent overfitting.

  

![](images/image-TEMD15Y1.jpg)Analogy: Like teaching a student with no study guidelines; they might over-focus on certain topics and neglect others.

•Nomogram: A graphic representation to approximate the output based on various inputs.

  

![](images/image-TEMD15Y1.jpg)Analogy: It's similar to a multi-functional ruler. Instead of just measuring, it helps you make predictions based on several scales.

•One Hot Encoding vs N-1 Dummy Encoding: One Hot Encoding: For each category of a variable, a binary column is created. A "1" indicates the presence of the category, while "0" indicates its absence. N-1 Dummy Encoding: For a variable with N categories, N-1 binary columns are created. The absent category is implied when all columns are "0".

  

![](images/image-TEMD15Y1.jpg)Analogy: It's like choosing pizza toppings. One hot encoding lists all toppings individually, while N-1 dummy lists all but assumes if none are selected, it's the last one, like "other".

•Outlier Handling: Addressing data points that differ significantly from others.

  

![](images/image-TEMD15Y1.jpg)Analogy: In a fruit basket, if you see one rotten fruit, you'd either remove, replace, or investigate it so that it doesn't impact the quality of the entire basket.

•PCA (Principal Component Analysis): Reducing the dimensionality of data while retaining its variance.

  

![](images/image-TEMD15Y1.jpg)Analogy: Like summarizing a long movie into a short trailer that still captures the essence of the story.

•Polynomial Regression: Capturing relationships using polynomial equations.

  

![](images/image-TEMD15Y1.jpg)Analogy: Predicting the height a ball reaches based on the force used to throw it; the relationship is curved, not straight.

•Precision (PPV): Of all the predicted positive values, how many were actual positives?

  

![](images/image-TEMD15Y1.jpg)Analogy: After predicting all apples in a basket are ripe, it's the chance of grabbing a truly ripe one.

•Probability vs Odds Ratios: Probability is the chance of an event occurring, while odds ratios compare the odds of two events.

  

![](images/image-TEMD15Y1.jpg)Analogy: If you have 3 red balls and 2 blue balls, the probability of getting red is 3/5. The odds ratio is the odds of getting red (3:2) versus blue.

•Random Forest: An ensemble learning method that constructs multiple decision trees.

  

![](images/image-TEMD15Y1.jpg)Analogy: If decision trees are individual judges, a random forest is a jury. Every judge gives their verdict, and the majority decides.

•Regularization: Techniques to prevent overfitting by adding a penalty to the loss function.

  

![](images/image-TEMD15Y1.jpg)Analogy: Like a teacher guiding a student not to over-focus on one topic for an exam, ensuring a balanced approach.

•Residual Plots: Visual representation of the differences between observed and predicted values.

  

![](images/image-TEMD15Y1.jpg)Analogy: Like analyzing footprints to determine if a person is walking straight or veering off.

•RNN (Recurrent Neural Network): Neural networks with loops to keep information in memory.

  

![](images/image-TEMD15Y1.jpg)Analogy: It's like a series of dominoes, where each one affects the next, but some have a rebound effect on previous ones.

•ROC versus PRC curve: Metrics to evaluate model's ability in classifying true positives from false positives.

  

![](images/image-TEMD15Y1.jpg)Analogy: ROC is like evaluating a goalie's ability to block shots without fouling, while PRC evaluates how many shots they can block out of all attempted shots.

•RSME, MSE (Root Mean Squared Error, Mean Squared Error): Measures of the differences between predicted and observed values.

  

![](images/image-TEMD15Y1.jpg)Analogy: It's like checking the average error in a carpenter's cuts. RSME would be like assessing the error in units familiar to the carpenter.

•R-squared: Represents how much variation in the dependent variable is explained by the independent variable(s).

  

![](images/image-TEMD15Y1.jpg)Analogy: Like assessing how much of a cake's taste is influenced by the ingredients versus the baking technique.

•Sensitivity (Recall): Of all the actual positives, how many were correctly predicted?

  

![](images/image-TEMD15Y1.jpg)Analogy: It's like a security system's ability to detect all actual intrusions. If there's an intrusion, how likely is the alarm to go off?

•Sentiment Analysis: Interpreting and classifying emotions within text data.

  

![](images/image-TEMD15Y1.jpg)Analogy: Just like understanding a friend's mood from reading their letter, sentiment analysis discerns feelings from words.

•Simple vs Multiple Regression: Simple regression involves one independent variable to predict an outcome, whereas multiple regression uses several variables.

  

![](images/image-TEMD15Y1.jpg)Analogy: If predicting a house price, simple regression might only consider its size of the home, whereas multiple regression also includes factors such as home age, location, and other variables.

•Six Sigma: A data-driven methodology focused on reducing variation, eliminating defects, and improving the quality of processes.

  

![](images/image-TEMD15Y1.jpg)Analogy: Much like a golfer continually refining their swing for perfect shots, Six Sigma aims for perfection in processes.

•Specificity: Measures the proportion of actual negatives correctly identified.

  

![](images/image-TEMD15Y1.jpg)Analogy: Imagine predicting which students will fail an exam. Specificity gauges how well we predict failures among those who didn't study.

•Supervised Learning: A learning method where algorithms are trained using labeled data.

  

![](images/image-TEMD15Y1.jpg)Analogy: It's akin to a student studying under the guidance of a teacher, where the correct answers (labels) guide learning.

•Target vs Predictor Variables: The target is what you aim to predict, while predictor variables influence the outcome.

  

![](images/image-TEMD15Y1.jpg)Analogy: In a game of darts, where the dart aims for the target, these efforts are influenced by factors like the player's stance, throw strength, and other factors (predictors).

•Threshold Shifting: Adjusting the decision boundary or “sensitivity” in classification problems to change sensitivity of a system. it's about changing the point at which something is considered "on" or "off", "positive" or "negative."

  

![](images/image-TEMD15Y1.jpg)Analogy: Imagine a light sensor that activates light based on darkness. Adjusting its sensitivity determines when the light turns on, whether in dimness or complete darkness.

•Transformer Models: Advanced models that prioritize and provide weights for different input data based on their relevance.

  

![](images/image-TEMD15Y1.jpg)Analogy: Picture being at a noisy party and trying to focus on a single conversation. Transformer models help 'tune in' to the most relevant information.

•True Negatives (TN): Predictions correctly identify a negative outcome.

  

![](images/image-TEMD15Y1.jpg)Analogy: It's like a weather forecast predicting no rain, and the day remains clear.

•True Positives (TP): Predictions correctly identify a positive outcome.

  

![](images/image-TEMD15Y1.jpg)Analogy: Predicting a rain-filled day and then witnessing showers.

•Type-I error (FPR): False positive rate and false alarms, where a negative event is wrongly predicted as positive.

  

![](images/image-TEMD15Y1.jpg)Analogy: Imagine accusing an innocent person of wrongdoing.

•Type-II error (FNR): False negative rate. Missing an actual positive event by predicting it as negative.

  

![](images/image-TEMD15Y1.jpg)Analogy: It's akin to letting a guilty person escape without suspicion.

•Type-III error: Misinterpreting the correct outcome.

  

![](images/image-TEMD15Y1.jpg)Analogy: Like reading the answer to one question and mistakenly applying it to another.

•Unified Performance Measure (UPM): An aggregate metric that consolidates various performance measures.

  

![](images/image-TEMD15Y1.jpg)Analogy: Think of a decathlon, where various event scores are combined to assess the overall winner.

•Unsupervised Learning: A learning approach where algorithms infer patterns from unlabeled data.

  

![](images/image-TEMD15Y1.jpg)Analogy: It's like a tourist wandering in a new city without a map. They explore different neighborhoods, notice similarities and differences, and naturally cluster areas by vibe or activity, all without predefined routes or categories.

•Using AI Chatbots as Brainstorming Members: Incorporating artificial intelligence in brainstorming sessions to generate or refine ideas.

  

![](images/image-TEMD15Y1.jpg)Analogy: Consider a brainstorming team where one member, a chatbot, throws in new and unexpected creative ideas, enhancing the group's ideation process.

•Violin Plot: A plot that combines a box plot and a kernel density plot, illustrating data distribution and its probability density.

  

![](images/image-TEMD15Y1.jpg)Analogy: If you imagined data as a bird, a violin plot wouldn't just show you the bird's outline but also where it's plump or slender.

•Vision Deployment / Hoshin Planning: A strategic planning process where an organization's vision is translated into actionable steps.

  

![](images/image-TEMD15Y1.jpg)Analogy: Envision planning a road trip. You decide your destination (vision) and then map out the route and stops to get there.

•Visual Programming vs Coding: Visual programming uses graphical elements to build programs, while coding requires manually writing out commands.

  

![](images/image-TEMD15Y1.jpg)Analogy: It's the difference between constructing with pre-made LEGO bricks (visual programming) versus tediously molding shapes from clay (coding).

•Waterfall project management: A linear project management approach, where each phase depends on the deliverables of the preceding one.

  

![](images/image-TEMD15Y1.jpg)Analogy: Think of it as constructing a building floor by floor. You wouldn't start building the third floor until the second is stable and complete.

•Word Cloud: A visual representation showcasing the frequency of words in a given dataset.

  

![](images/image-TEMD15Y1.jpg)Analogy: Picture a crowd's buzzing chatter. The loudest or most repeated topics stand out, similar to the most prominent words in a word cloud.

## Index

  

Note: this index shows the page numbers of the printed book. They are linked to paragraphs in this ebook. You may need to scroll to see the topic.

[A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | R | S | T | U | V | W](#content0280.xhtml)

A

  

[AdaBoost, 153, 175, 219, 341](#content0279.xhtml)

analysis techniques, 48, 78, 188, 246, 303, 309

artificial intelligence (AI), 4, 9, 50, 63, 284, 302, 304, 321

association rules, 241, 243, 341

Autoregressive Integrated Moving Average (ARIMA), 250–53

  

B

  

[bagging, 154, 341](#content0279.xhtml)

[bias, 7, 83, 87, 147–50, 157, 162–63, 175, 224, 275–76, 285, 289](#content0242.xhtml)

bias-variance tradeoff, 147–48, 162, 175

Big Data, 5, 13, 169, 212

box plot, 33–34, 49, 89, 97–98, 107–9, 113, 115–16, 132–33, 141, 174, 211–12, 225, 235–36, 244, 254–55, 259–60, 310–11

  

C

  

[calibration, 165, 170–71, 175, 182–83, 185, 190, 198, 213–14, 226](#content0179.xhtml)

Calibration plot, 68, 169–70, 185, 191, 196, 214, 226

categorical data, 30, 37, 45, 86, 95, 107, 110–11, 113, 152–53, 222, 225

[chatbots, 5, 285, 289, 302, 306, 308, 311, 314, 322–27, 341](#content0279.xhtml)

[classification, 14, 16–17, 150–54, 157–58, 160, 182–83, 189, 203, 206, 208, 218–19, 223–25, 229, 232, 240–41](#content0191.xhtml)

class imbalance, 5, 23, 156, 162–63, 165–67, 169, 171–73, 185, 193, 196, 214

[clustering, 5, 27, 50, 124, 232, 234–35, 237, 297, 342](#content0279.xhtml)

columns widget, 81–82, 295

Confidence intervals (CIs), 64, 118, 130–32, 182, 186–87, 195, 251–52, 254, 257

confusion matrix, 166, 187, 192, 214, 277

Continuize widget, 43, 91

continuous variables, 32, 37, 58, 89, 106, 114–15, 209, 211, 214, 221, 254–55

Convolutional Neural Networks (CNNs), 238, 273–79, 288, 342

[correlation, 17, 50–54, 58–59, 84, 117–18, 120, 125–26, 128, 206, 211–13, 219–20, 234, 238–41](#content0190.xhtml)

[coefficients, 52–53, 118, 155](#content0109.xhtml)

correlation matrix, 56, 107, 125–26, 238, 310–11

correlation widget, 84

[cross-validation, 29–30, 67, 75, 79, 81, 145, 173, 175, 180–82, 190, 342](#content0279.xhtml)

  

D

  

data analysis, 2, 5, 20, 22, 29, 106, 113, 209, 211, 310, 314

Data analyst, 11, 21, 31, 67

data engineers, 10–11

data leakage, 62, 70, 180, 342

data management, 6, 21

Data Management Body of Knowledge (DMBok), 5–6, 19, 21

Data preparation, 1, 10, 20, 23–24, 32, 66, 98

data quality, 5–6, 19, 23–24, 63, 106

data sampler widget, 79, 81

data scaling, 46, 48

Data science (DS), 1–24, 27–29, 66–70, 97–98, 106, 109, 136, 144–46, 151–52, 162–63, 175–76, 212–13, 302–22, 325–28, 341–42

data science experiments, 23, 29, 66–68, 145, 342

data scientists, 1–2, 5–6, 9–11, 20–21, 24, 27, 66–67, 136, 144, 161–62, 315

Data visualization, 15, 34–35, 42, 106–41, 254, 318

decision tree (DT), 17, 30, 34, 37, 83, 124, 129–30, 149, 151–52, 160–61, 172–73, 342, 345

discretize widget, 37, 39, 91

[distribution, 17–18, 32–33, 35, 62, 64, 92–93, 108, 110–13, 115–16, 141, 169, 182–84, 209, 211–14, 234–36](#content0186.xhtml)

distribution plots, 33–34, 39–41, 74, 90, 107–8, 113, 127, 235, 255

dummy variable trap, 42–43, 91, 222–23, 342

  

E

  

[encoding, 24, 26, 29–30, 42, 223, 237, 287, 344](#content0279.xhtml)

Exploratory data analysis (EDA), 12, 24, 50, 94, 106, 124, 145, 208, 212, 309–10

External validation (EV), 181–82, 343

  

F

  

Feature constructor widget, 41–42, 92–93

Feature engineering, 29, 343

feature importance, 149, 161, 201, 203–4, 207, 226

file widget, 14–15, 77, 81, 122, 227

  

G

  

geo-analysis, 267–70

[geo-mapping, 123, 267–69, 271](#content0218.xhtml)

Gradient boosting (GB), 72, 153, 155, 201, 214, 219, 343

gradient descent, 150–51, 343

  

H

  

[healthcare, 7–10, 18, 20, 24, 26, 63, 148, 265, 267, 274, 289, 291, 303–4, 316–17](#content0267.xhtml)

hierarchical clustering, 124, 237, 243–44, 246

High Reliability Organizations, 306, 316, 327, 343

[histograms, 49, 89, 95, 107, 110–11, 113–16, 118, 141, 147, 211, 310–11](#content0263.xhtml)

hyperparameter optimization (HPO), 68, 75, 145–46, 151, 173, 180

[hyperparameters, 13, 68, 75–76, 153, 160, 172, 176, 180, 276](#content0228.xhtml)

Hypothesis testing, 208, 310–11, 343

  

I

  

image analysis, 5, 13, 278, 284, 322

image analytics, 2, 4, 14, 16, 18, 238, 273–81, 328

Image embedding, 238, 277–78

imbalanced data, 26, 63, 152, 163, 166–67, 170, 172–73, 193, 195, 343

[imputation, 30–33, 88, 227](#content0179.xhtml)

information gain, 37, 83, 88, 136

Innovation-On-Demand Techniques, 306, 324, 327

internal validation, 180

  

J

  

[JASP, 22, 33–34, 54, 59–63, 76, 89–90, 93–95, 106–10, 112, 114–18, 122, 124–27, 131–33, 141, 159–60, 206–14, 220–21, 223–25](#content0173.xhtml)

Comparison vs Orange, 18

Educational Data Science Platform, 12

Limitations, 18

Menu Organization, 17

Unique features, 16

  

K

  

Kaplan-Meier Survival Analysis, 255, 257, 260, 343

K-means clustering, 232–33, 244

K-nearest neighbor algorithm, 34, 90, 168

  

L

  

lambda values, 93, 153

large language models (LLMs), 5, 288–89, 291, 323

[lasso, 24, 60–61, 67, 72, 136, 155–56, 160, 219, 224, 227, 343](#content0279.xhtml)

Lean Six Sigma. See LSS

Lean Six Sigma (LLS), 12, 306, 310, 314–16, 343

linear regression, 4, 17, 60, 136, 146–47, 151, 156–57, 160, 214, 219–20, 222–29

linear regression widget, 79, 154, 227

logistic regression (LR), 58, 60, 62, 136, 155–60, 163–65, 171, 182–88, 191–92, 198, 201–2, 223, 226, 277–78, 298

Logistic Regression widget, 156

LogLoss, 344

  

M

  

machine learning, 1–6, 8, 10–11, 17, 19, 21, 23–25, 51–52, 86, 144, 146–47, 149, 151, 161–62, 218

Matthews correlation coefficient, 166–67, 206, 344

Mean squared error (MSE), 160, 189, 198, 208, 224–25, 345

Merge data, 85–86, 266–67

merge data widget, 85

missing data, 5, 29–33, 68, 71, 85–86, 95, 98, 172, 174, 208, 214

MLOps, 161

model calibration, 182–83, 185

model challenges, 147, 162

model discrimination, 182

model drift, 162, 212–13

Model errors, 146, 149, 221

Model evaluation, 180–215, 251

model metrics, 71–72, 74, 251

model performance, 29–31, 37, 48, 67–68, 76, 93, 96, 144–45, 147, 150–51, 170–73, 175, 203, 206

model training, 136, 144, 291

Mosaic plots, 39–40, 120–22

[multicollinearity, 23, 26, 29, 42, 50–52, 60–62, 136, 145, 206, 214, 222–24](#content0172.xhtml)

Multiple linear regression (MLR), 58, 155, 221–22, 228

  

N

  

Naive Bayes, 156–58, 173, 182, 219, 226, 285, 288, 344

Natural language processing (NLP), 10, 26, 232, 238, 284–87, 289, 291–92, 309, 322, 344

negative predictive value, 187, 193, 207, 344

Neural Network (NNs), 10–11, 17, 25–26, 72, 149–50, 157–58, 160–61, 173, 175, 219, 273–74, 285–86, 288, 341–42, 344–45

normal distribution, 34, 41, 92–93, 107–8, 114, 116–17, 155, 209–10

  

O

  

Orange workflow, 13, 70–73, 98, 123–24, 128, 134–36, 170–71, 173, 199, 250–51, 255, 266–67, 297–98

[outliers, 33–36, 89–90, 95, 98–99, 107–8, 113–14, 117, 119, 127–28, 132–33, 152–53](#content0109.xhtml)

[overfitting, 44, 50, 81, 145, 147–48, 152, 154–55, 168–69, 173, 182, 223–24, 341, 344–45](#content0279.xhtml)

  

P

  

paint data, 57, 79–80, 223

Parallel Coordinate Plots (PCPs), 128–29, 235, 311

Pareto charts, 49, 107, 112–13, 164

Pearson correlation coefficients, 53–54, 57

[precision, 68, 71, 158, 160, 163, 165–67, 169–70, 188–89, 193, 196–97, 206, 208, 342–44](#content0279.xhtml)

precision and recall, 166, 169–70, 175, 206

Precision-recall curve (PRC), 163–66, 173, 196, 215

Predictions widget, 191, 277

predictive analytics, 4, 6, 10, 25, 29, 163, 306, 315, 318, 321, 328

[Preprocess, 23, 31, 37, 39, 68, 88, 96, 174–75, 223, 254–55, 292](#content0253.xhtml)

preprocess widget, 31, 37, 71, 87–88

Principal component analysis (PCA), 17, 25, 29, 50–51, 67, 88, 237–41, 246, 344

[p-values, 30, 32–33, 59–61, 64, 98, 109, 132, 208, 210–12, 214, 220, 222, 257–58](#content0205.xhtml)

  

R

  

Random Forest (RF), 17, 145, 152–53, 155, 158, 160–61, 167, 171, 173, 175, 219, 226, 345

Rank widget, 39, 83–84, 88, 152, 201

Receiver operating characteristic (ROC), 68, 163, 165, 190, 193, 195, 215, 345

Recurrent Neural Networks (RNNs), 13, 285–86, 288, 345

[regression, 14, 17, 147, 150–55, 157–58, 167–68, 187, 189, 198–99, 203–5, 211, 218–24, 226–28, 342, 344–45](#content0279.xhtml)

[regularization, 60, 67, 136, 155, 157, 160, 171, 173, 224, 228, 342, 345](#content0279.xhtml)

regularization methods, 136, 224

residual plots, 198–99, 201, 345

Root mean square error (RMSE), 155, 160, 189, 224–26

R-Squared value, 58–61

  

S

  

Save data widget, 79, 84, 96, 225, 267

Save model widget, 159, 170

scaling options, 46, 48

scatter plots, 39–42, 49–50, 53–54, 79–80, 96, 107, 117, 119, 127, 141, 198–99, 234–35, 310–11

Select rows widget, 82, 96–97, 294

[sensitivity, 169–70, 187–88, 192–97, 316, 345](#content0279.xhtml)

Silhouette plot, 232–35

silhouette scores, 233, 236

simple linear regression, 155, 219–20, 226

[skewness, 17, 41, 93, 108, 110](#content0081.xhtml)

small language models, 291, 322

Spearman correlation coefficients, 52, 57–58

[specificity, 158, 169–70, 175, 187–89, 192–96, 241, 345](#content0279.xhtml)

Support vector machine (SVM), 17, 30, 34, 151, 154, 160–61, 168, 173, 219, 285, 288

SWOT analysis, 303, 306, 320

Synthetic Oversampling Technique (SMOTE), 29, 145, 152, 168–69, 173

  

T

  

text analysis, 10, 308, 322

text mining, 4, 13, 16, 284–99, 309, 328

Time Series Forecasting, 19, 250, 260

topic modeling, 288, 292

[transformers, 274, 286, 288–89](#content0242.xhtml)

[Twitter, 2, 286, 292, 294](#content0253.xhtml)

  

U

  

unlabeled data, 5, 124, 218, 232

unstructured data, 2, 25–26, 246, 285

unsupervised learning, 4–5, 10, 13, 17, 26, 84, 124, 218, 232–47, 288

  

V

  

[validation, 81, 180–81, 189–91, 214, 226, 253, 278, 310–11, 342](#content0279.xhtml)

validation datasets, 86, 160, 167, 180

[variance, 46, 48–49, 83, 87, 147–49, 154, 208, 211–12, 222, 224, 238–40, 341, 344](#content0279.xhtml)

Variance inflation factors (VIFs), 23–24, 29, 50, 58–62, 145, 160, 211, 214, 221–22, 225

violin plot, 49, 107, 113, 346

  

W

  

[weights, 29, 140, 150–52, 157–58, 166–67, 175, 219, 221, 240, 275–76, 285–86](#content0237.xhtml)

widget catalog, 15, 22, 297

Wilk-Shapiro test, 116

  

\[Index created with TExtract / www.TExtract.com\]