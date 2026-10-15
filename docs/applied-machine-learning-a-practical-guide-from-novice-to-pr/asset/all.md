  

![](OEBPS/image_rsrc502.jpg)Applied Machine Applied Machine Learning: A  Practical Guide from Novice to Pro . 

A business use case approach to solving real problems in schools, banks, retail, insurance, e-commerce, the manufacturing industry, supply chain, and beyond.

Author: Chigozie Anyasor.

Applied Machine Learning: A practical guide from Novice to Pro.

Copyright © CHIGOZIE ANYASOR 2024

First Published 2024.

All rights reserved. No part of this book may be reproduced, stored in a retrieval system, or transmitted in any form or by any means (electronic, photocopying) without express approval from the publisher.

You can contact the author via

LinkedIn : [https://www.linkedin.com/in/chigozie-anyasor-9519b938](https://www.google.com/url?q=https://www.linkedin.com/in/chigozie-anyasor-9519b938&sa=D&source=editors&ust=1720099681633499&usg=AOvVaw2FlUJRUd6ZY3kmls3YVkIf)  

E-mail: anyasorc@gmail.com

Other books you might be interested in:

[Curbing Fraud - A case study approach to curbing frauds in Banks and Fintech.](https://www.google.com/url?q=https://selar.co/609b11&sa=D&source=editors&ust=1720099681634278&usg=AOvVaw2YOaUAAw-QiiBLFlYBlYYb)

[Data Privacy & Ethical Responsibilities: An enterprise guide to preventing DATA.](https://www.google.com/url?q=https://selar.co/a640z6&sa=D&source=editors&ust=1720099681634503&usg=AOvVaw17_iB-DblzIdUBFpQ0ARQI)  

About the Author

| ![](OEBPS/image_rsrc503.jpg) || Chigozie Anyasor, currently serving as the CEO of Uridium Works Limited, spearheads the development of impactful strategies aimed at realizing the company's objectives. His primary focus lies in fostering a dynamic and efficient work atmosphere conducive to the productivity of his team comprising adept engineers.Prior to his tenure as CEO, Chigozie accrued over 14 years of invaluable experience at Sterling Bank plc, where he held the position of Senior Manager/Head of Software Engineering. During this tenure, he oversaw multiple pivotal teams including Enterprise Solutions Engineering, Automation & Productivity, and enterprise data warehousing. His extensive background in the banking sector encompasses team empowerment, fostering robust interdepartmental relationships, and the design and implementation of innovative payment systems. Noteworthy are his adept analytical abilities, proficiency in issue debugging, and comprehensive understanding of contemporary technology stacks tailored to address business challenges.Chigozie has also contributed significantly to various data science initiatives aimed at resolving tangible business dilemmas.Educationally, Chigozie holds a bachelor's degree in Computer Science from Babcock University in Nigeria, complemented by a Master's in Data Science from Walden University in the United States. |
| --- | --- |

Acknowledgments

Writing a book is never a solitary endeavor, and this project would not have been possible without the support, encouragement, and assistance of numerous individuals and organizations.

First and foremost, I extend my deepest gratitude to my family for their unwavering support and understanding throughout this journey. Their patience, encouragement, and belief in me fueled my determination to see this project through to completion.

I am profoundly thankful to my colleagues and mentors whose insights, guidance, and constructive feedback have been invaluable in shaping the content of this book. Their expertise and encouragement have been instrumental in refining the ideas presented within these pages.

I would also like to express my appreciation to the reviewers and editors who dedicated their time and expertise to ensure the quality and accuracy of this book. Their meticulous attention to detail has greatly enhanced the clarity and coherence of the material.

Furthermore, I am grateful to the readers and practitioners of machine learning who continue to inspire and motivate me with their passion for the subject. Your enthusiasm and dedication serve as a constant reminder of the importance of sharing knowledge and expertise within the community.

To everyone who has contributed in any way to the creation of this book, I offer my sincerest thanks. Your support and collaboration have been instrumental in bringing "Applied Machine Learning: A Practical Guide from Novice to Pro" to life.

With heartfelt appreciation,

Chigozie Anyasor

Table of Contents

# Preface

Welcome to "Applied Machine Learning," an in-depth exploration of the ever-evolving field revolutionizing industries, tackling intricate challenges, and catapulting us into an era of unparalleled innovation. Within these pages, we embark on a journey through the practical realms of machine learning, unveiling the tools, methodologies, and insights that empower individuals and enterprises to fully harness the capabilities of this state-of-the-art technology.

" Applied Machine Learning " delves into the practical applications of machine learning, offering a roadmap for individuals and organizations to leverage its potential. Tailored for both newcomers and seasoned practitioners, this book covers foundational principles alongside real-world scenarios.

Whether you're a student delving into the world of machine learning, a professional seeking to enhance your skills, or an industry leader navigating the integration of machine learning within your organization, this book serves as a compass to unlock the transformative power of applied machine learning. Let the journey commence!

# Introduction

Embarking on a voyage into the realm of Applied Machine Learning is akin to stepping into a captivating world where data transforms into profound insights, and algorithms unveil the mysteries concealed within. "Applied Machine Learning: From Novice to Pro" extends a warm invitation to explore this exhilarating landscape, presenting a comprehensive roadmap tailored to both beginners seeking a sturdy foundation and seasoned practitioners eager to hone their craft.

Within this immersive journey, I unravel the intricacies of machine learning concepts, demystify algorithms, and arm you with the skills to seamlessly apply these principles to real-world challenges. Whether you're venturing into the realms of artificial intelligence for the first time or aiming to elevate your expertise, this book will furnish you with the knowledge and practical wisdom required to navigate the diverse terrain of applied machine learning.

Prepare to unlock the potential latent within data, witness the enchantment of predictive analytics, and witness how raw information metamorphoses into actionable intelligence. "Applied Machine Learning: From Novice to Pro" transcends being a mere guide; it stands as an open invitation to join the ranks of those harnessing the power of machine learning to innovate, problem-solve, and shape the future. So, fasten your seatbelt and let the exploration commence!

Machine learning is an immensely intriguing field that involves harnessing computational algorithms to glean insights and make predictions from data without explicit programming. It's a subset of artificial intelligence focused on creating systems capable of learning and improving autonomously from experience. To wield machine learning effectively, data scientists, or aspiring ones, must grasp its principles and inner workings thoroughly.

At its core, machine learning entails feeding an algorithm or model with pertinent data to tackle a business problem, allowing it to learn and improve from patterns and relationships within the data. As more data is ingested into the algorithm or model, it can leverage its accrued knowledge (the training data) to predict new data points. Consequently, machine learning empowers businesses to make informed decisions and predictions grounded in observed patterns.

While predictions play a pivotal role in leveraging machine learning for informed decision-making, it's crucial to realize that simply possessing a prediction model isn't enough. What truly matters is how you act upon those predictions. Businesses must take ownership of a model's outcomes and grasp its limitations. This underscores the pivotal role of a data scientist or chief data officer in comprehending a model's capabilities to dispel misconceptions and effectively leverage machine learning to address business challenges.

This book serves as a comprehensive guide to various machine learning techniques widely employed in data science and analytics. It traverses the entire machine learning pipeline, commencing from data preprocessing and c ulminating in model selection. The text delves into diverse Regression models, including Simple, Multiple, Polynomial, Support vector, Decision tree, and Random forest regression models, alongside evaluating these models and selecting the optimal regression model for a given task.

Furthermore, it explores Classification techniques such as Logistic Regression, K-nearest Neighbor, Support vector machines, Naive Bayes, Decision trees, and Random forest classification, providing a nuanced understanding of evaluating classification models and discerning the most suitable one for a specific objective.

Additionally, the book delves into Clustering methods like K-means. Finally, it covers how to operationalize your machine learning models. Altogether, this book serves as an indispensable resource for anyone striving to master machine learning techniques and apply them in real-world scenarios.

# Difference between machine learning, data science, and data analytics.

Machine learning  stands as a vital subset within artificial intelligence , revolving around the creation of algorithms and statistical models. These models empower computers to learn from data without explicit programming, enabling them to execute specific tasks. For instance, spam filters in email services employ machine learning algorithms to distinguish between spam and legitimate messages based on patterns found in the data.  

In the retail industry, machine learning algorithms are frequently employed for demand forecasting. By analyzing historical sales data along with external factors such as weather patterns, holidays, and economic indicators, retailers can predict future demand for products with greater accuracy. This allows them to optimize inventory management, minimize stockouts, and reduce overstocking, ultimately leading to improved customer satisfaction and increased profitability.

In the manufacturing industry, machine learning is used for predictive maintenance. By monitoring equipment sensors and historical maintenance records, machine learning algorithms can identify patterns indicative of impending equipment failures. This enables manufacturers to schedule maintenance proactively, minimizing unplanned downtime, reducing maintenance costs, and optimizing production efficiency.

Data science , on the other hand, encompasses the comprehensive analysis of extensive datasets using a variety of tools and algorithms. Through this analysis, data scientists uncover hidden patterns and extract actionable insights. For instance, a retail company might use data science techniques to analyze customer purchasing behavior and optimize product recommendations accordingly.

Data analytics  focuses on examining raw data to extract insights and draw conclusions using specialized tools such as Microsoft Power BI and Tableau. These insights inform strategic decision-making, identify trends, and enhance overall business performance. For example, a healthcare organization might utilize data analytics to track patient outcomes and optimize treatment protocols based on the collected data.

# Type of Machine Learning

There are three types of machine learning: supervised , unsupervised , and reinforcement learning. This book will focus on the first two.

# Supervised Learning

Supervised learning is a type of machine learning where the algorithm learns from a dataset that has labeled examples or a guide to follow. This means that the algorithm is trained on input data that already has a desired output, allowing it to make predictions and decisions based on new, unseen data. Supervised learning models are widely used in various fields, including computer vision, natural language processing, and predictive analytics.

Let’s take a look at the medical dataset screenshot below:

![](OEBPS/image_rsrc504.jpg)

As illustrated in the screenshot, the label for this dataset is "diagnosis."

# Unsupervised machine learning

Unsupervised machine learning models are a type of algorithm that can be applied to unlabeled data. These models are designed to identify underlying patterns and structures within the data without the need for human intervention or pre-existing labels.  

Let’s look at the screenshot below from a bank transaction dataset.

![](OEBPS/image_rsrc505.jpg)

As shown in the screenshot, there is no label column available to guide the model, making this dataset ideal for unsupervised learning.

# Let's get pumped up.

Greetings! Are you ready to delve into the exciting world of machine learning? Let's get energized and dive into an engaging example together. We're about to embark on a journey of discovery that will leave us both informed and inspired. So, without further ado, let's begin our adventure!

Launch Google Colab to get started: [https://colab.research.google.com/](https://www.google.com/url?q=https://colab.research.google.com/&sa=D&source=editors&ust=1720099681675968&usg=AOvVaw0Ic9_VBs5RP55ZlbeQk9ds)  

![](OEBPS/image_rsrc506.jpg)

To create a new notebook, follow these steps:

Navigate to the "File" tab located at the top left-hand corner of your screen.

Click on "File" to open a drop-down menu.

Select "New Notebook" from the menu.

This action will open a new notebook, allowing you to begin your project or take notes, as illustrated below:

![](OEBPS/image_rsrc507.jpg)

From the image above, you click on file and then select New notebook.

To rename the notebook from "Untitled" to "Getting Pumped," follow these steps:

Click on the current notebook title "Untitled" at the top of the notebook interface.

A text box will appear, allowing you to edit the title.

Type "Getting Pumped" into the text box.

Press Enter or click outside the text box to save the new name.

Your notebook should now be renamed to "Getting Pumped," as shown below:

![](OEBPS/image_rsrc508.jpg)

# Importing the data

To access the dataset necessary for this exercise, you can download it from the Bank Campaign source ( [Bank Campaign](https://www.google.com/url?q=https://github.com/anyasorc/appliedml/blob/main/bankcampaign.csv&sa=D&source=editors&ust=1720099681678463&usg=AOvVaw2eRX91-CDyZ6pm0UnaZh6L) ) . Then, proceed by dragging the dataset from its location on your system into the Google Colab data folder, which is indicated by the orange-colored folder, as depicted in the screenshot below:

![](OEBPS/image_rsrc509.jpg)

Performing the aforementioned action will prompt a warning notification popup. The dialog box displayed below notifies you about the significance of maintaining a copy of your dataset since Google Colab commonly removes datasets.

![](OEBPS/image_rsrc50A.jpg)

To continue, simply click the OK button to dismiss the warning dialog and proceed with the task.

# Problem case

Adefunmi, a banking institution employee, has taken on the task of overseeing a targeted marketing campaign aimed at customers who have agreed to receive ads focusing on investment opportunities. To maximize the bank's marketing investment, Adefunmi has adopted a systematic approach, empowering her team to base their decisions on data when allocating campaign resources.

To achieve this goal, she has fostered collaboration among various stakeholders and ultimately decided on implementing a machine learning framework. This framework utilizes past data from customers who have consented to similar investment opportunities to inform decision-making.

Throughout the process, Adefunmi has worked closely with data engineers, the business team, and data scientists. This collaboration has ensured that data engineers provide comprehensive data access to data scientists, who have then chosen to utilize the logistic regression model to predict customer behavior based on historical data.

# Import the data

To import the data, you first need to import the libraries as seen below:

![](OEBPS/image_rsrc50B.jpg)

If there are no errors, proceed to load the data and take a look at the data frame, as depicted in the screenshot below:

![](OEBPS/image_rsrc50C.jpg)

Let's examine the total count of records and columns in the data frame, as illustrated below:

![](OEBPS/image_rsrc50D.jpg)

Next, we will assign the features we want to work with into variables X and y as shown below:

Assign "Age" to X

Assign "invested" (the class) to y

![](OEBPS/image_rsrc50E.jpg)

Check the distribution of the "invested" class values using the value\_counts()  method in Python.

![](OEBPS/image_rsrc50F.jpg)

The distribution shows that we have more customers who would like to invest (1), totaling 790, compared to those who would not like to invest (0), totaling 210. This data imbalance could negatively affect the performance of your machine learning model if not addressed.

# What are imbalance data?

Imbalanced data refers to datasets where the classes are not equally represented, meaning one class (or a few classes) has significantly more instances than the others. This imbalance can pose challenges for machine learning models, as they may become biased towards the majority class and perform poorly on the minority class.

# Handling data imbalance

Handling imbalanced data is crucial for several reasons, including improved model performance, prevention of model bias, enhanced decision-making, and better generalization. Various techniques for managing imbalanced data include:

SMOTE (Synthetic Minority Over-sampling Technique)

Under-sampling

Over-sampling

Before implementing any methods to address the imbalance in the "invested" class, let's first visualize the current distribution of the class, as shown below:

![](OEBPS/image_rsrc50G.jpg)

We will use the under-sampling method, as demonstrated below:

![](OEBPS/image_rsrc50H.jpg)

After applying the undersampling method described earlier, the class imbalance has been addressed, as shown below:

![](OEBPS/image_rsrc50J.jpg)

Next, we will create a scatter plot to examine the age distribution of customers who are more inclined to invest, as shown below:

![](OEBPS/image_rsrc50K.jpg)

The output

![](OEBPS/image_rsrc50M.jpg)

# Interpreting the scattered plot

The scatter plot indicates that customers aged between 20 and 71 are more likely to invest when targeted with ads. Customers older than 71 show a lower inclination to invest. Therefore, the target audience for the ads should ideally be customers aged between 20 and 71.

Next, let's proceed to split the data, allocating 80% for training the model and 20% for testing, as shown below:

![](OEBPS/image_rsrc50N.jpg)

In the screenshot below, we are instantiating the LogisticRegression class and assigning it to a variable named lc . We then fit the training data using lc.fit  with X\_train  and y\_train . Note: The model training occurs during lc.fit .

![](OEBPS/image_rsrc50P.jpg)

Next, we pass the X\_test, which contains 20% of the data reserved for testing the model, as shown below:

![](OEBPS/image_rsrc50R.jpg)

The screenshot above shows that the model actually predicted correctly.

Next, let's test the model by passing an age value to validate the accuracy of our predictions, as shown below.

Based on the screenshot below, I inputted the age 40 into the model. The model referenced its previous patterns and indicated that customers within this age range are likely to invest when exposed to targeted ads. This suggests that customers in this age bracket are the ideal target audience Adefunmi is seeking.

![](OEBPS/image_rsrc50S.jpg)

In the screenshot below, the model predicted that customers aged 72 would not be interested in an investment-targeted ad. It's evident that these customers are not the target audience Adefunmi is seeking.

![](OEBPS/image_rsrc50T.jpg)

Buoyed by the successful outcomes of the experiment, Adefunmi has instructed the data team to collect data for the targeted campaign, specifically excluding individuals aged 72 and above.

Adefunmi implemented a meticulously planned and comprehensive strategy for the bank's marketing campaign. This approach allowed the bank to optimize its resources, leading to a highly successful campaign that will strongly appeal to customers interested in investment opportunities.

The company may decide to integrate the machine learning model as an API to facilitate its use for corporate applications.

Exciting, isn't it? This is just the beginning.

# Chapter 1

# Machine Learning Process

# Teaching methodology

I strongly believe that the most effective way to truly understand and retain information is through active participation in the learning process. This involves getting hands-on, engaging in practical exercises, real-world scenarios, and interactive activities.

In my teaching approach, I prioritize creating opportunities for you to directly apply what you're learning in a tangible manner. Whether it's through hands-on exercises, problem-solving challenges, simulations, or project-based learning, the focus is always on actively interacting with the content.

By actively engaging in your learning journey, you not only grasp concepts more deeply but also develop practical skills that you can apply across different situations. If you're eager to dive into experiential learning and make meaningful progress toward your learning objectives, then you're in the right place! Let's embark on this journey together and start achieving your goals effectively.

# Why do we need statistics?

In the realm of data science and analysis, statistics plays a central role as the foundational framework. It serves as a robust tool for data professionals, enabling them to engage deeply with data through exploratory data analysis (EDA)—a crucial step in the data analysis journey.

Statistics is widely employed in data exploration, visualization, and comprehension, empowering professionals to derive informed conclusions. By applying statistical principles, data professionals can uncover intricate patterns, identify trends, and reveal relationships within datasets.

This capability yields valuable insights that inform and shape decision-making processes. Through the application of statistics, professionals adeptly navigate the complexities of data, converting raw information into actionable intelligence.

Let's apply these concepts practically by examining the "Bike Sales in Europe" dataset available on Kaggle. This dataset provides extensive information on bike sales, offering valuable insights into sales trends within the European market.

Our goal is to conduct a thorough exploratory data analysis (EDA) on this dataset to understand its intricacies and uncover actionable insights. You can access the dataset using the following link: [bike-sales-in-europe](https://www.google.com/url?q=https://www.kaggle.com/datasets/sadiqshah/bike-sales-in-europe&sa=D&source=editors&ust=1720099681689295&usg=AOvVaw1QDxzfRwt22TC5XaP--kXG) .  The source code is available here: [Why do we need statistics](https://www.google.com/url?q=https://github.com/anyasorc/appliedml/blob/main/Why_do_we_need_statistics_in_Data_Science.ipynb&sa=D&source=editors&ust=1720099681689759&usg=AOvVaw1A7gQOReoxGy0iiOIWcv-G)

# Import the required libraries

Let's import the required library, as depicted in Figure 1-1 .

![](OEBPS/image_rsrc50U.jpg)

Figure 1-1.

# Read the data using pandas

Figure 1-2 demonstrates how to read the dataset ('Sales.csv') using pandas.

![](OEBPS/image_rsrc50V.jpg)

Figure 1-2: The screenshot displays the loaded dataset along with a few records, using df.head() .

# Check the total number of records in the dataset

Figure 1-3 illustrates the Python command used to check the total number of records (rows) and features (columns) in the dataset.

![](OEBPS/image_rsrc50W.jpg)

Figure 1-3.

# Exploratory Data Analysis

Exploratory Data Analysis (EDA) is crucial in data analysis, aiming to highlight the fundamental characteristics of a dataset, improve understanding, and uncover underlying patterns or correlations between variables. EDA typically utilizes techniques such as data visualization, summary statistics, and data cleaning to prepare the dataset for further analysis.

# Check gender representation

To examine gender representation in the dataset, we will use the value\_counts()  function as shown in  Figure 1-4 .

![](OEBPS/image_rsrc50X.jpg)

Figure 1-4.

# Visualize the Gender Distribution

To better understand the distribution of genders, Figure 1-5  provides a visual representation for easy interpretation.

![](OEBPS/image_rsrc50Y.jpg)

Figure 1-5.

# Visualize sales distribution by country

Figure 1-6   illustrates how to visualize the distribution of sales by country.

![](OEBPS/image_rsrc50Z.jpg)

Figure 1-6.

Visualize Sales Distribution by Month

Figure 1-7  shows how to visualize sales distribution by month starting from 2011 to 2016.

![](OEBPS/image_rsrc510.jpg)

Figure 1-7.

Get the minimum and maximum sales year

Figure 1-8  illustrates the process of identifying the year with the lowest and highest sales.

![](OEBPS/image_rsrc511.jpg)

Figure 1-8.

# Visualize Sales Distribution by Year

Figure 1-9  demonstrates how to visualize the distribution of sales across different years.

![](OEBPS/image_rsrc512.jpg)

Figure 1-9.

# Visualize Sales Distribution by Age.

Figure 1-10  demonstrates how to visualize the distribution of sales based on customers' ages.

![](OEBPS/image_rsrc513.jpg)

Figure 1-10.  The output is shown in Figure 1-11.

![](OEBPS/image_rsrc514.jpg)

Figure 1-11. Our data analysis revealed a significant contrast in purchasing behavior between younger and older customer segments. The majority of purchases were made by customers aged 25 to 46, while sales were notably lower among those aged over 53 or below 25. These insights highlight the substantial influence of age on our customers' purchasing habits.

# Visualize Sales Distribution of Customers by Age and Gender

Figure 1-12 illustrates how to visualize the distribution of sales based on both customers' age and gender.

![](OEBPS/image_rsrc515.jpg)

Figure 1-12. Figure 1-13 shows the output.

![](OEBPS/image_rsrc516.jpg)Figure 1-13 reveals that individuals identifying as male have consistently made more purchases across all age groups. This indicates a trend where male customers outpace female customers in purchasing behavior across different age brackets. 

# Machine Learning Process

Machine learning, a subfield of artificial intelligence, involves teaching machines to learn from data. It encompasses three main processes:

Data Preparation:  This involves gathering data from various sources, cleaning it to address errors and inconsistencies, integrating disparate sources, transforming it into a usable format, selecting relevant features, splitting it into training, validation, and testing sets, and optionally augmenting it to increase dataset size. Thorough data preparation ensures the quality and relevance of the data for training models, leading to more accurate and effective outcomes.

Model Training:  This process uses algorithms and statistical models to train the machine learning model on the prepared data. During this phase, the machine learns to identify patterns and make predictions based on the input data.

Model Evaluation:  This entails assessing the performance of the trained model using fresh data to gauge its accuracy and efficacy. A successful evaluation indicates that the model can reliably make predictions when presented with new, unseen data, thus confirming its readiness for real-world deployment.

## Data Preprocessing

Data preprocessing is a critical precursor to effectively employing machine learning models. It encompasses a series of pivotal steps aimed at refining raw data into a structured format conducive to analysis and modeling. In this text, we will explore an array of essential techniques and methodologies for data preprocessing, including data cleaning and feature scaling.

Additionally, we will provide a reusable template designed to uphold consistency and ensure high quality throughout the book. Meticulous adherence to these best practices is instrumental in crafting precise and dependable machine learning models. By embracing these strategies, you can enhance the performance of your models and glean invaluable insights from your data.

### Let’s look at an example

We have a customer dataset available for download through this link: [Customer Dataset](https://www.google.com/url?q=https://github.com/anyasorc/appliedml/blob/main/data.csv&sa=D&source=editors&ust=1720099681698836&usg=AOvVaw1vewoISGrCiEyIqzEyqrJM) .  The dataset includes the following features:

customer\_id

first\_name

Last\_name

age

email1

country

salary

purchased

The dataset includes a feature called "purchased," which indicates whether or not the customer has made a purchase.

To get started, open Google Colab or your preferred Integrated Development Environment (IDE). Once you have it ready, import the necessary libraries for your project. Refer to Figure 1-14 for a visual guide on the libraries you need to import.

![](OEBPS/image_rsrc517.jpg)

Figure 1-14. The imported libraries.

Next, we will import the dataset, as illustrated in Figure 1-15 .

![](OEBPS/image_rsrc518.jpg)

Figure 1-15 displays the imported dataset, showing the first 5 records. The screenshot includes all the relevant features from the dataset. Note: We will need to correct the column spelling for "email1" in the subsequent steps as we proceed.

Next, it is essential to determine the exact number of records in the dataset, as this reveals the amount of data available for evaluation. Equally important is identifying the number of features present in the dataset. This knowledge enhances our understanding of the data and its attributes, facilitating effective data processing and analysis. Therefore, thoroughly examining the total count of records and features is crucial prior to proceeding with further analysis. For guidance on how to check the shape of the data, refer to Figure 1-16 .

![](OEBPS/image_rsrc519.jpg)

Figure 1-16. This shows that the total number of records in the dataset is 1,003 while the total number of features is 8.

Next, update the email column name from 'email1' to 'email', as demonstrated in Figure 1-17 .

![](OEBPS/image_rsrc51A.jpg)

Figure 1-17. Rename email1  to email.

# Check for Duplicates

Next, proceed to identify and address any duplicates within the dataset, as illustrated in Figure 1-18 .

![](OEBPS/image_rsrc51B.jpg)

Figure 1-18 shows that there are duplicate records in the dataset.

# Fetch out the duplicated records

Next, retrieve the duplicated records from the dataset using the code demonstrated in Figure 1-19 .

![](OEBPS/image_rsrc51C.jpg)

The screenshot in Figure 1-19 indicates three duplicate records in the dataset.

# Drop the duplicates

Let’s drop the duplicates using the code as shown in Figure 1-20 .

![](OEBPS/image_rsrc51D.jpg)

Figure 1-20.

Next, verify the absence of duplicates and confirm the total record count to ensure that the duplicates have been effectively removed, as demonstrated in Figure 1-21 .

![](OEBPS/image_rsrc51E.jpg)

In Figure 1-21, it is shown that duplicates were successfully removed, resulting in a decrease in the record count from 1003 to 1000.

# Select preferred features

Next, using the code illustrated in  Figure 1-22 , we'll select specific features: age, country, salary, and purchased, akin to the SQL syntax SELECT age, country, salary, purchased FROM table .

![](OEBPS/image_rsrc51F.jpg)

Figure 1-22.

Check for NaN

Next, verify if there are any NaN values in the dataset using the code demonstrated in Figure 1-23 .

![](OEBPS/image_rsrc51G.jpg)

Figure 1-23.

# Select all rows and columns

Next, we will select all the rows and columns in the dataset using the code command as seen in Figure 1-24 .

![](OEBPS/image_rsrc51H.jpg)

Figure 1-24.

Note: In pandas, when using the 'iloc' (index location) function, the colon ':' symbol is used for slicing data. In the context of 'df.iloc\[:, :\]', the first colon ( : ) before the comma selects all rows in the dataset, while the second colon ( : ) after the comma selects all columns in the dataset.

# Select 3 records and column age and country

To select three records from the dataset and return only the 'age' and 'country' columns, you can follow the example shown in   Figure 1-25 .

![](OEBPS/image_rsrc51J.jpg)

Figure 1-25.

In the code, "df.iloc\[:3,\[0,1\]\]" selects a subset of data from the dataset. The ":3" before the comma specifies that we want to select the first 3 records from the dataset. The "\[0,1\]" after the comma indicates that we are selecting the first (0) and second (1) columns in the dataset, which correspond to the "age" and "country" variables, respectively.

# Assign all features except the last feature to X

Next, assign all feature variables (age, country, salary) to a variable X, excluding the last feature 'purchased', which will be assigned to a variable y. Please consult Figure 1-26  for specific implementation details.

![](OEBPS/image_rsrc51K.jpg)Figure 1-26 displays the selection and assignment of the age, country, and salary columns/features to variable X, as shown in the output. Note the 'NaN' value in row 2. 

# Assign the last feature to y

Next, assign the target feature 'purchased' to the variable y, as illustrated in Figure 1-27 .

![](OEBPS/image_rsrc51M.jpg)

Figure 1-27.

# Handling missing values

Figure 1-28  demonstrates the process of managing missing numeric values in a dataset.

![](OEBPS/image_rsrc51N.jpg)

Figure 1-28.

# Code explanation

imp = SimpleImputer(missing\_values=np.nan, strategy='mean')

SimpleImputer  is a class from the sklearn.impute  module in scikit-learn, used for handling missing data.

missing\_values=np.nan : Specifies that NaN (Not a Number) values in the data should be considered as missing values.

strategy='mean' : Defines the strategy to use for imputation. Here, it indicates that missing values should be replaced with the mean of the column.

imp.fit(X\[:, \[0, 2\]\])

imp.fit(X\[:, \[0, 2\]\]) : This line fits (trains) the SimpleImputer  instance imp  on the data X .

X\[:, \[0, 2\]\]  selects columns 0 (age) and 2 (salary) from the 2D array X . This typically means selecting specific columns (0 and 2) from all rows in the dataset X .

X\[:, \[0, 2\]\] = imp.transform(X\[:, \[0, 2\]\])

imp.transform(X\[:, \[0, 2\]\]) : This line transforms (imputes) the selected columns in X  using the fitted SimpleImputer  instance imp .

The transformed values (imputed values) are then assigned back to the corresponding columns (0 and 2) in X .

Note: According to the details in Figure 1-28 , the missing value (NaN) in the second row has been replaced with the mean values: 50.674418604651166 for age and 30054.11301715439 for salary. This approach uses the SimpleImputer algorithm to automatically fill missing numeric values with the mean computed for each respective column.

# Encoding  the Categorical Data

To leverage the categorical country feature in our dataset for machine learning purposes, it is necessary to convert it into a numerical format. One effective technique for achieving this conversion is known as one-hot encoding . This method involves creating a distinct binary feature for each unique value found in the original country feature. For each record in the dataset, the binary feature corresponding to its country value is set to 1, while all other binary features are set to 0.

As a result of this process, the categorical information represented by the country feature is transformed into a set of numerical features. These new features accurately encode the presence or absence of each country value across the dataset. This numerical representation enables machine learning models to effectively interpret and analyze the country feature as part of their training and prediction processes.

By employing one-hot encoding, we ensure that the categorical nature of the country feature does not pose a barrier to the model's understanding. Instead, it provides a structured way to incorporate categorical data into machine learning algorithms, enhancing their ability to derive meaningful insights and make accurate predictions based on the dataset's features.

To determine the count of unique category values in the 'country' column, refer to the code snippet provided in Figure 1-29 .

![](OEBPS/image_rsrc51P.jpg)

Figure 1-29 displays five categories: Spain, France, Nigeria, Ghana, and the United States.

Our dataset shows that the 'country' column is at index position 1 as seen in Figure 1-24 . We can refer to the code illustrated in Figure 1-30  to perform one-hot encoding on this column.  This implies we will be having 5 additional columns added to the data which was initally 3 in X as seen in Figure 1-28 .  The 5 new additional columns will be added in front of the existing columns.

![](OEBPS/image_rsrc51R.jpg)

Figure 1-30. The underlined values are the newly added columns.

Note: If you look at Figure 1-28 and compare it with Figure 1-30, you will see that all the countries are now represented with numerical values.

See Table 1-1 for more details.

| Country || Numerical value |
| --- | --- |
| Ghana || 0.0, 1.0, 0.0, 0.0, 0.0 |
| United States || 0.0, 0.0, 0.0, 0.0, 1.0 |
| Spain || 0.0, 0.0, 0.0, 1.0, 0.0 |
| France || 1.0, 0.0, 0.0, 0.0, 0.0 |
| Nigeria || 0.0, 0.0, 1.0, 0.0, 0.0 |

Table 1-1.

The above table shows the numerical representation of all the countries to be used in training the machine learning model.

# Code Explanation

ct = ColumnTransformer(transformers=\[('encoder', OneHotEncoder(), \[1\])\], remainder='passthrough')

ColumnTransformer  is a class from scikit-learn ( sklearn.compose ) used to apply different transformations to different columns of a dataset.

In this code, transformers=\[('encoder', OneHotEncoder(), \[1\])\]  specifies a transformation step:

'encoder' : This is a name given to the transformation step.

OneHotEncoder() : This is the transformer object used to perform one-hot encoding.

\[1\] : This indicates that the transformation (one-hot encoding) should be applied to column index 1 of the input data ( X ).

X = np.array(ct.fit\_transform(X))

ct.fit\_transform(X) : This method fits the ColumnTransformer   ct  to the data X  and then transforms X  based on the specified transformations.

The fit\_transform  method first fits the transformer on the data (determines the categories for one-hot encoding, for example) and then transforms the data accordingly.

X  is then assigned the transformed data, which is converted to a NumPy array using np.array() .

# Encoding the dependent variable y

To conduct deeper analysis of the data, it's essential to convert the current dependent variable y, which contains "yes" and "no" values, into numeric values of 1 and 0. This transformation can be accomplished using the LabelEncoder method, as illustrated in Figure 1-31 .

![](OEBPS/image_rsrc51S.jpg)

Figure 1-31.

# Code Explanation

le = LabelEncoder()

LabelEncoder  is a class from scikit-learn ( sklearn.preprocessing ) used to encode categorical target labels with numerical values.

le  is an instance of LabelEncoder  initialized to perform label encoding.

y = le.fit\_transform(y)

le.fit\_transform(y) : This method fits the LabelEncoder   le  to the target variable y  and then transforms y  into encoded numerical labels.

The fit\_transform  method first fits the LabelEncoder  on the target variable y , learning the unique classes in y  (e.g., "yes" and "no").

Then, it transforms y  by assigning numeric labels (0, 1, etc.) to each unique class in y . For example, "yes" might be encoded as 1 and "no" as 0.

# Splitting the data into training and test set

To ready the dataset for model training, we will divide it into two segments using an 80:20 ratio. This allocation designates 80% of the data for training the model and reserves the remaining 20% for evaluating the model's performance. For a visual representation of this division, please consult Figure 1-32 .

![](OEBPS/image_rsrc51T.jpg)

Figure 1-32.

# Feature Scaling

To achieve regularization and enhance model performance, it is vital to scale features such as age and salary. Feature scaling adjusts the range of numerical data to a consistent scale, which aids in improving the accuracy and effectiveness of predictive models. By scaling features, models can more accurately interpret the relative importance of each feature and avoid biases that may arise from differing scales.

This scaling is particularly critical for algorithms like Support Vector Machines (SVMs), K-Nearest Neighbors (KNN), and Neural Networks. These models often rely on distance metrics or gradient descent optimization techniques, which can be adversely affected by features operating on different scales. Scaling mitigates these issues by ensuring that all features contribute proportionately to the model's learning process.

For example, when predicting customer purchase behavior, accurate scaling of features such as age and salary enables the model to discern subtle patterns and relationships within the data more effectively. This, in turn, enables the model to make reliable predictions based on these variables, enhancing its overall predictive power and usefulness in practical applications.

Figure 1-32   illustrates that the age and salary features are not standardized to the same scale. To rectify this, we will employ the StandardScaler, as demonstrated in Figure 1-33 .

![](OEBPS/image_rsrc51U.jpg)

Figure 1-33. You can see the values have been scaled as seen in the output. Age 80 is scaled to 1.52077076986837 while salary of 16388 is scaled to -1.1599989214968063.

# Exercise

In your own words, could you explain the significance of statistics in the field of data science?

Do a summary report to your manager/supervisor on your understanding of what the sales dataset ( [bike-sales-in-europe](https://www.google.com/url?q=https://www.kaggle.com/datasets/sadiqshah/bike-sales-in-europe&sa=D&source=editors&ust=1720099681713828&usg=AOvVaw2HEUrBa_ICxaNsM3HIs5lX) )  is all about.

Create a line graph that shows year vs profit using the sales dataset ( [bike-sales-in-europe](https://www.google.com/url?q=https://www.kaggle.com/datasets/sadiqshah/bike-sales-in-europe&sa=D&source=editors&ust=1720099681714248&usg=AOvVaw1XWbr2Fei02lxfMVQC6Je5) )

Write a two-page paper reflecting your understanding of why we need to split the dataset into tests and training.

What would be your preferred splitting formula (70:30 or 80:20) and why?

Using the iloc, display records that return 5 rows and just the age and purchased column(feature). Note, you will use the data.csv ( [data.csv](https://www.google.com/url?q=https://github.com/anyasorc/appliedml/blob/main/data.csv&sa=D&source=editors&ust=1720099681714667&usg=AOvVaw0x2BxuasZHPoQfqKeEtFbC) )

# Chapter 2  
Regression

# Regression

Regression analysis is a type of supervised machine learning that involves predicting one or more continuous numerical  values, such as salaries, based on the relationships and patterns within datasets. This method can be used to identify the relationships between one or more independent variables and a dependent variable, allowing for the generation of accurate predictions for future data points.

Regression analysis is often used in finance, economics, and social sciences to model the relationship between variables, such as income and education, and to predict future trends. Generating a regression model involves selecting appropriate algorithms, testing for accuracy, and adjusting the model to improve predictions.

There are several types of regression models used in data science, each with its own assumptions and applications. One of the most commonly used types of regression is linear regression, which assumes a linear relationship between the independent and dependent variables.

In our exploration of regression, we will cover the following types:

Simple Linear Regression

Multiple Linear Regression

Polynomial Regression

Support Vector Regression (SVR)

Decision Tree Regression

Random Forest Regression

# Simple Linear regression

Simple Linear Regression is a fundamental machine learning algorithm used to predict a continuous dependent variable, also known as the response or outcome variable. This prediction is based on a single independent variable, referred to as the predictor or explanatory variable.

The algorithm assumes a linear relationship between the two variables, meaning that the relationship can be represented by a straight line. Additionally, the model assumes that there is a direct proportional relationship between the independent variable X and the dependent variable Y.

This relationship can be expressed mathematically by the equation:

Y=β0+β1\* X+ϵ

Y is the dependent variable.

X is the independent variable.

β0 is the y-intercept (constant term).

β1 is the slope of the line, representing the change in Y for a one-unit change in X.

ϵ is the error term, representing the unobserved factors that affect Y but are not included in the model.

Note: Simple linear regression datasets have one independent variable and one dependent variable.

# Problem statement - Applicable in Banking, Retail, Manufacturing, etc

Kunle is a talented data scientist who recently joined XYZ Food Limited, a prominent company in the food industry. His expertise in machine learning has led to his assignment of enhancing sales through the development of a model based on historical sales data. The company has provided him with a comprehensive dataset containing extensive information about past sales driven by TV advertisements.

Kunle's primary objective is to construct a predictive model that aids the organization in making informed decisions regarding investments in TV ads to boost sales. He meticulously analyzes the dataset, utilizing his expertise to pinpoint crucial factors contributing to successful TV ad campaigns. Leveraging his knowledge of machine learning algorithms, Kunle aims to develop a robust model capable of accurately forecasting the impact of TV ads on sales.

His efforts are pivotal to XYZ Food Limited's marketing strategy. Kunle dedicates significant effort to data analysis and model development, striving to deliver valuable insights into the correlation between TV ads and sales. Through his work, he aims to empower XYZ Food Limited to optimize sales and achieve their business objectives effectively.

You can access the dataset by downloading it from this link: [adv\_data.csv](https://www.google.com/url?q=https://github.com/anyasorc/appliedml/blob/main/adv_data.csv&sa=D&source=editors&ust=1720099681717744&usg=AOvVaw10ecD8CFVW9tMp9bDzkemH) .

# Solution

Kunle began by previewing the data in Excel to get an initial look at its structure, as depicted in Figure 2-1 .

![](OEBPS/image_rsrc51V.jpg)

Figure 2-1.

The source code is available here: [Simple Linear Regression](https://www.google.com/url?q=https://github.com/anyasorc/appliedml/blob/main/Master_Class_Simple_Linear_Regression.ipynb&sa=D&source=editors&ust=1720099681718399&usg=AOvVaw2-mYTnOs3s9Kw5q5qgThYR)  

Note: The dataset is clean and free of any dirty data; therefore, we will skip the preprocessing steps.

# Import all the needed libraries

Import all the necessary libraries for the simple linear regression model, as shown in Figure 2-2 .

![](OEBPS/image_rsrc51W.jpg)

Figure 2-2.

# Load the dataset

Load the dataset and display the first five records, as depicted in Figure 2-3 .

![](OEBPS/image_rsrc51X.jpg)

Figure 2-3.

# Assigning Features

Let's define the features, as illustrated in Figure 2-4 .

![](OEBPS/image_rsrc51Y.jpg)

In Figure 2-4, X represents the TV feature values, while y represents the sales feature values from the dataset.

# Split the dataset

To prepare the dataset for machine learning, it is recommended to divide it into two subsets: training and testing data. A common practice is to use 80% of the data for training and 20% for testing. Figure 2-5  illustrates how this split is typically done.

![](OEBPS/image_rsrc51Z.jpg)Figure 2-5. 

# Training the model  
In this step, we will use the LinearRegression algorithm on our dataset. Initially, we'll create an instance of the LinearRegression model, establishing an object for training on our dataset. Once instantiated, we'll proceed to fit the model with our training data.

This process entails feeding the model both input data and target output data. The model will then autonomously adjust its internal parameters to minimize the disparity between predicted and actual outputs for each input. The outcome is a trained model ready for predicting outcomes on new data. Figure 2-6  provides a visual depiction of this process.

![](OEBPS/image_rsrc520.jpg)

Figure 2-6.

# Code Explanation

lr = LinearRegression()

LinearRegression()  is a class from a machine learning library (e.g., scikit-learn in Python) that implements the linear regression algorithm.

lr  is an instance (or object) of this class. It now contains all the necessary methods and attributes associated with linear regression.

lr.fit(X\_train, y\_train)

lr.fit()  is a method provided by the LinearRegression  class that trains (fits) the model using the training data.

X\_train  is a matrix or dataframe containing the input features (independent variables) used to train the model.

y\_train  is a vector or series containing the target values (dependent variable) corresponding to the input features in X\_train .

# Make predictions with the model

Now that the model has been trained, it possesses the capability to discern patterns and relationships within the data it was trained on. This enables us to utilize the model for making predictions with new, unseen data.

Using the model for predictions allows us to assess the accuracy and dependability of its forecasts, thereby evaluating its suitability for real-world applications. This evaluation process is crucial for making informed decisions, particularly when relying on predictions generated from unfamiliar data.

Next, we will demonstrate the process by making a prediction with an input of $100,000, as illustrated in Figure 2-7 .

![](OEBPS/image_rsrc521.jpg)

Figure 2-7.

# Interpreting the outcome of the model

Upon reviewing the findings presented in Figure 2-7 , it is evident that Kunle has gathered sufficient evidence to compile a detailed report for the management team. This report will emphasize the necessity of augmenting the budget designated for TV advertisements. The analytical model employed in this study specializes in forecasting the impact of TV advertising expenditures on sales metrics. According to the model's analysis, an increase in advertising spending correlates positively with an uptick in sales figures.

Based on the model's projections, allocating $100,000 to TV advertising could potentially yield an approximate sales increase of 4,608 units. This observation provides compelling support for advocating an expansion of the advertising budget.

Moreover, the model underscores a clear positive relationship between advertising expenditures and sales outcomes. As advertising investments rise, sales figures are anticipated to follow suit. Conversely, as illustrated in Figure 2-8 , a reduction in advertising expenditure corresponds with a decline in sales figures. Therefore, an exhaustive management report incorporating these insights can furnish valuable perspectives and aid in making well-informed decisions regarding the allocation of the advertising budget.

![](OEBPS/image_rsrc522.jpg)

The screenshot labeled as Figure 2-8 illustrates an important insight regarding the company's projected investment of $5,000 on advertisements. According to the data presented in the screenshot, the estimated sales figure is likely to be 237 if the company decides to make this investment. However, this number is outside the organization's desired position in the industry. In other words, the sales projection of 237 needs to be revised, considering the company's aspirations and goals.

In summary, making predictions with the model is a crucial step in leveraging the power of machine learning to gain insights and make informed decisions. It allows us to harness the potential of data-driven technologies to solve complex problems and improve our decision-making processes.

# Non-Linear Regression stopped here

When dealing with regression tasks, it's important to consider the nature of the relationship between the independent and dependent variables. Traditional linear regression techniques assume a linear relationship between these variables, meaning that the change in the dependent variable is directly proportional to a change in the independent variable. However, in many real-world scenarios, the relationship between variables is more complex and non-linear. In these cases, non-linear regression techniques are needed to model the relationship and make reliable predictions accurately.

Non-linear regression is a statistical method that allows for the identification and quantification of non-linear relationships between variables. It involves fitting a non-linear equation to the data to minimize the difference between the predicted and actual values. Identifying the best non-linear equation to fit the data can be complex and iterative. Still, many algorithms and software packages are available to help with this task.

When solving a regression problem that has more than one input variable, then there is a need to use models that fit into that as against simple linear regression that takes just an input variable.

Let's consider an example based on the following problem statement.

# Problem Statement

As a data scientist at an insurance company, one of your primary responsibilities is to utilize machine learning models to determine appropriate charges for insurance services. Your objective is to ensure that pricing is informed by data-driven insights, considering features such as age , BMI , number of children , region , and other relevant factors.

To accomplish this, you need to identify and select the most suitable regression model that aligns well with the data. This will enable you to develop a robust and reliable ML system capable of accurately predicting pricing based on client characteristics.

![](OEBPS/image_rsrc523.jpg)

You can get the dataset from: [Health Insurance](https://www.google.com/url?q=https://www.kaggle.com/datasets/shivadumnawar/health-insurance-dataset&sa=D&source=editors&ust=1720099681724082&usg=AOvVaw0g5HumYazCc0vn6688MiCd)  

# Polynomial Regression

Polynomial regression is a statistical technique used to model non-linear relationships between independent and dependent variables. This method involves fitting a polynomial curve to the data, which allows for a more flexible and accurate representation of underlying patterns and trends.

By using polynomial regression, we can gain valuable insights into the relationships among variables. This facilitates informed decision-making based on thorough data analysis.

Download the dataset using this link: [Insurance Dataset](https://www.google.com/url?q=https://www.kaggle.com/datasets/awaiskaggler/insurance-csv&sa=D&source=editors&ust=1720099681724685&usg=AOvVaw1_xfkRiUlkeP2h1M4-bUxI) . The source code is available here: [Polynomial Regression](https://www.google.com/url?q=https://github.com/anyasorc/appliedml/blob/main/Master_Class_Medical_Insurance_Polynomial_Reg%2520\(1\).ipynb&sa=D&source=editors&ust=1720099681724886&usg=AOvVaw06GWXC1mxKZLctFZrRTUFE)  

Let’s import the libraries as seen in Figure 2-9

# Import Libraries

![](OEBPS/image_rsrc524.jpg)

Figure 2-9.

# Import and View data

Load the CSV dataset as demonstrated in Figure 2-10 .

![](OEBPS/image_rsrc525.jpg)

Figure 2-10: This screenshot shows the insurance dataset being read into a dataframe named df  using pandas.

Let's examine the distribution count for the feature 'region' as shown in Figure 2-11 .

![](OEBPS/image_rsrc526.jpg)

Figure 2-11.

Let's examine the distribution count by smoker status as shown in Figure 2-12 .

![](OEBPS/image_rsrc527.jpg)

Figure 2-12.

Let’s check for missing values as seen in Figure 2-13 .

# Check for missing data

![](OEBPS/image_rsrc528.jpg)

Figure 2-13.

# Assign values to X and y stopped here

Extract the details into X  and y . Since we aim to predict the charge, it will be assigned to y , as shown in Figure 2-14 .

![](OEBPS/image_rsrc529.jpg)

Figure 2-14.

Let's examine the details inside X , as shown in Figure 2-15 .

![](OEBPS/image_rsrc52A.jpg)

Figure 2-15.

To address missing values in numerical features, we need to replace them with their mean values. This ensures that our dataset remains complete and accurate for analysis.

First, we identify the numeric features. Referring to [Figure 2-10](#part0001_split_000.xhtml#a4YB) , the numeric features are indexed as 0 (age), 2 (BMI), and 3 (children).

We can select these features by specifying all rows (:) and the column indices \[0, 2, 3\], as demonstrated in Figure 2-16 .

![](OEBPS/image_rsrc52B.jpg)

Figure 2-16.

# Handling Missing Data

Now that we have identified the index positions of our numerical features (age, BMI, and number of children), we will use SimpleImputer to handle the missing values. We will set the missing values to NaN and employ a strategy of replacing them with the mean, as shown in Figure 2-17 .

![](OEBPS/image_rsrc52C.jpg)

Figure 2-17: I created an instance of SimpleImputer and assigned it to a variable named imp . We then fit the imputer to the data in X  for all rows and the specified columns. To ensure the transformed values are displayed with two decimal places, we used np.set\_printoptions(precision=2) . Finally, we transformed the data using imp.transform . This method checks for NaN values in the target columns \[0, 2, 3\] and replaces any found with the mean value of that column.

# Encoding Categorical variable

We also need to encode the categorical data in the dataset. These features are essential for our machine learning model, hence the need for encoding. The categorical data includes: sex at index position 1, smoker at index position 4, and region at index position 5, as shown in [Figure 2-10](#part0001_split_000.xhtml#a4YB) .

To achieve this, we will use ColumnTransformer with OneHotEncoder() as one of the parameters, as depicted in Figure 2-18 . The parameter remainder='passthrough'  indicates that the other columns should be ignored, and focus should be on columns at index positions 1, 4, and 5.

![](OEBPS/image_rsrc52D.jpg)

Figure 2-18: This is a standard implementation that works regardless of column or feature positions. You simply need to provide the index positions of the features to be encoded.

In this example, I instantiated the ColumnTransformer and assigned it to a variable named ct . Follow the parameter pattern shown here with your own dataset, and you will achieve similar results.

I then fit and transformed X , assigning the transformed data back to X . This means that the ColumnTransformer processes all features in X , focusing specifically on the columns at index positions 1, 4, and 5. It fits the data to ct , transforms it, and reassigns it to X .

Let's examine the impact of the column transformation and one-hot encoding. You can do this by viewing the first five records in X , as shown in Figure 2-19 .

![](OEBPS/image_rsrc52E.jpg)

Figure 2-19.

# Splitting the data into test train

Using the train\_test\_split  function, we will split the data with an 80:20 ratio, where 80% of the data is used for training and 20% is reserved for testing. This means that 80% of the data will be assigned to X\_train  and y\_train , while the remaining 20% will be assigned to X\_test  and y\_test , as shown in Figure 2-20 .

![](OEBPS/image_rsrc52F.jpg)

Figure 2-20.

Now that we have completed data preprocessing, it is time to train our model. Before doing so, we need to transform our data into polynomial form, as illustrated in Figure 2-21 .

The line Poly\_reg = PolynomialFeatures(degree=4)  creates an instance of the PolynomialFeatures  class. This instance generates polynomial features up to the 4th degree, which will be used to transform the original features for polynomial regression modeling.

![](OEBPS/image_rsrc52G.jpg)

Figure 2-21. The model was trained successfully without any error.

Figure 2-22  shows an R-squared score of 0.85122 for the model, indicating that approximately 85.12% (0.85122 \* 100)  of the variability in the dependent variable can be explained by the independent variables in your model. This high R-squared value suggests that your model fits the data well and can explain a large portion of the variance in the dependent variable.

![](OEBPS/image_rsrc52H.jpg)

Figure 2-22.

# Interpretation of the r2\_score for Polynomial Regression Model

The  R 2   (pronounced "R-squared") score, also referred to as the coefficient of determination, is a statistical metric that quantifies the proportion of the variance in the dependent variable that can be explained by the independent variable(s).

An R 2   score of 0.851227 indicates that approximately 85.12% of the variance in the dependent variable is predictable from the independent variable(s) in the model. In other words, the model explains about 85.12% of the variability in the data. This suggests that the model fits the data quite well, as a high R 2 score indicates that the observed outcomes are well-represented by the model predictions.

# To make predictions using Polynomial Regression

To make predictions using polynomial regression, you can use the predict  function on the trained model, providing the necessary input parameters, as demonstrated in Figure 2-23 .

![](OEBPS/image_rsrc52J.jpg)

Figure 2-23.

![](OEBPS/image_rsrc52K.jpg)

In this example, \`sex\`, \`smoker\`, \`region\`, \`age\`, \`bmi\`, and \`children\` are the input features used for the prediction.

# Code Explanation

In the context of polynomial regression, the model needs the input features to be transformed into polynomial features before making a prediction. The code snippet does this in two steps:

Transform the input features: The input features sex, smoker, region, age, bmi, and children are transformed into polynomial features using the poly\_reg.transform method. This transformation includes generating additional features that are polynomial combinations of the original features.

Predict the target variable: The transformed features are then passed to the lr.predict  method of the trained regression model lr  to predict the target variable.

# Multiple Linear Regression

Multiple linear regression extends the principles of simple linear regression by modeling the relationship between a dependent variable (also known as the target or response) and multiple independent variables (referred to as predictors or features). While simple linear regression considers only one predictor, multiple linear regression incorporates two or more predictors, providing a more comprehensive analysis of how various factors collectively influence the dependent variable.

This method is essential in data science for understanding and quantifying the impact of multiple variables on a target outcome. By considering multiple predictors, multiple linear regression enables more accurate predictions and offers insights into complex relationships within the data.

Download the dataset using this link: [Insurance Dataset](https://www.google.com/url?q=https://www.kaggle.com/datasets/awaiskaggler/insurance-csv&sa=D&source=editors&ust=1720099681734560&usg=AOvVaw3TzaCJRNZGrbHq9PreHILr) . The source code is available here: [Multiple Linear Regression](https://www.google.com/url?q=https://github.com/anyasorc/appliedml/blob/main/Medical_Insurance_Multiple_Linear_Reg.ipynb&sa=D&source=editors&ust=1720099681734846&usg=AOvVaw0jy2PLIOHE3Kh20p1ZKiiS)  

# Import Libraries

Figure 2-24  displays all the necessary imported libraries.

![](OEBPS/image_rsrc52M.jpg)

Figure 2-24.

# Import and View Data

Figure 2-25  demonstrates how the data was imported and viewed, as shown below.

![](OEBPS/image_rsrc52N.jpg)

Figure 2-25.

# Counting the frequency of unique values in the 'region' column of a DataFrame

The code df.region.value\_counts()  calculates the frequency of each unique value in the region  column of the DataFrame df , displaying the number of times each region appears. This is illustrated in Figure 2-26 . The same method applies to the smoker  feature.

![](OEBPS/image_rsrc52P.jpg)

Figure 2-26.

# Check for missing values

The code df.isna().sum()  is a chain of methods that calculates the total number of missing values (NaN values) in each column of the DataFrame df , as shown in Figure 2-27 .

![](OEBPS/image_rsrc52R.jpg)

Figure 2-27.

# Assign values to X and y

X = df.iloc\[:, :-1\].values:

This line selects all rows and all columns except the last one from the DataFrame df  and converts the result into a NumPy array. The resulting array X  typically contains the features or predictors, as shown in Figure 2-28 .

y = df.iloc\[:, -1\].values:

This line selects all rows and only the last column from the DataFrame df  and converts the result into a NumPy array. The resulting array y  typically contains the target or response variable, as shown in Figure 2-28 .

![](OEBPS/image_rsrc52S.jpg)

Figure 2-28

# View data in X

Type X  in a new code cell and run it to view the data assigned to X , as shown in Figure 2-29 . The same can be done for y .

![](OEBPS/image_rsrc52T.jpg)In Figure 2-29, I have labeled the columns with their respective index positions as follows: the first column, Age , is at index position 0 ; the second column, Sex , is at index position 1 ; the third column, BMI , is at index position 2 ; the fourth column, Number of Children , is at index position 3 ; the fifth column, Smoker , is at index position 4 ; and the sixth column, Region , is at index position 5 . 

# Addressing  missing values (NaN)

Addressing missing values is relevant for numerical features/columns, as shown in Figure 2-30 . We have selected the features/columns with index positions 0, 2, and 3, which correspond to Age, BMI, and Number of Children, respectively, as illustrated in Figure 2-29 .

![](OEBPS/image_rsrc52U.jpg)

Figure 2-30 . X\[:, \[0, 2, 3\]\]  means "select all rows and the columns at index positions 0, 2, and 3. So, X\[:, \[0, 2, 3\]\]  effectively extracts the Age, BMI, and Number of Children columns/features for all rows in the dataset.

After identifying the numerical columns, we will use the SimpleImputer class to calculate the mean value for each column/feature and replace any missing values with these means, as demonstrated in Figure 2-31 .

![](OEBPS/image_rsrc52V.jpg)

Figure 2-31.  

# Code Explanation

SimpleImputer(missing\_values=np.nan, strategy='mean')

missing\_values=np.nan: This parameter specifies that the missing values to be imputed are represented by np.nan

strategy='mean': This parameter specifies that the missing values should be replaced with the mean value of the respective column.

imp.fit(X\[:, \[0, 2, 3\]\])

X\[:, \[0, 2, 3\]\]: This selects all rows and the columns at index positions 0, 2, and 3 from the array X. These columns are numerical.

.fit(...): This method calculates the mean value of each selected column based on the non-missing values and stores these mean values for later use.

np.set\_printoptions(precision=2)

This function configures how NumPy arrays are displayed. Here, it sets the precision of the printed output to 2 decimal places.

X\[:, \[0, 2, 3\]\] = imp.transform(X\[:, \[0, 2, 3\]\])

X\[:, \[0, 2, 3\]\]: Again, this selects all rows and the columns at index positions 0, 2, and 3 from the array X.

imp.transform(...): This method replaces the missing values in the selected columns with the mean values calculated during the .fit(...) step.

X\[:, \[0, 2, 3\]\] = ...: This assignment updates the selected columns in the original array X with the transformed data where missing values have been replaced.

# ColumTransformer and OneHotEncoder()

Machine learning models do not inherently understand text or categorical values, necessitating their conversion into numerical representations that models can process. This is why we need to convert the categorical variables at index positions 1 (Sex), 4 (Smoker), and 5 (Region), as shown in Figure 2-29 . To accomplish this, we will utilize ColumnTransformer and OneHotEncoder, as illustrated in Figure 2-32 .

![](OEBPS/image_rsrc52W.jpg)

Figure 2-32.

# C ode Explanation.

ColumnTransformer : A class from the sklearn.compose module that applies different preprocessing transformations to different columns of a dataset.

OneHotEncoder : A class from the sklearn.preprocessing module that converts categorical features into a format that can be provided to machine learning algorithms to do a better job in prediction.

np : This is the commonly used alias for the NumPy library, which is useful for array operations.

Creating an Instance of ColumnTransformer

![](OEBPS/image_rsrc52X.jpg)

ColumnTransformer(...) :

This initializes a ColumnTransformer object to apply specified transformations to specific columns.

transformers=\[('encoder', OneHotEncoder(), \[1, 4, 5\])\] :

'encoder': The name given to this transformer. It can be any string.

OneHotEncoder(): This specifies that we are using the OneHotEncoder for the transformation.

\[1, 4, 5\]: This list specifies the indices of the columns to be transformed. Here, columns at index positions 1, 4, and 5 will be one-hot encoded.  

remainder='passthrough' :

This parameter specifies what should be done with the columns that are not explicitly transformed. 'passthrough' means that these columns will be left unchanged and included in the output.

# Splitting into train and test set

We need to divide our dataset into training and testing sets using an 80:20 split. This means 80% of the data will be used to train the model, while the remaining 20% will be used to evaluate its performance on unseen data. Figure 2-32  depicts this process.

![](OEBPS/image_rsrc52Y.jpg)

Figure 2-32.

# Code Explanation

train\_test\_split : This is a function from the sklearn.model\_selection module in the scikit-learn library. The function is used to split the dataset into training and testing sets. X\_train and y\_train are used to train the model. X\_test and y\_test are used to evaluate the model's performance on unseen data

Components of the Function Call :

X: This is the feature matrix (input variables). It contains the independent variables or predictors.

y: This is the target vector (output variable). It contains the dependent variable or response.

test\_size=0.2: This parameter specifies the proportion of the dataset to include in the test split. Here, 0.2 means 20% of the data will be used for testing, and the remaining 80% will be used for training.

random\_state=0: This parameter controls the shuffling applied to the data before splitting. Passing an integer ensures reproducibility of the split, meaning the same data split will occur every time you run the code with this random\_state value.

Output of the Function Call :

X\_train: This is the training subset of the feature matrix. It contains 80% of the rows from X.

X\_test: This is the testing subset of the feature matrix. It contains the remaining 20% of the rows from X.

y\_train: This is the training subset of the target vector. It contains the corresponding 80% of the rows from y that match the rows in X\_train.

y\_test: This is the testing subset of the target vector. It contains the corresponding 20% of the rows from y that match the rows in X\_test.

By using a test\_size of 0.2, we ensure that 20% of the data is reserved for testing, which helps in assessing how well the model generalizes to new data. The random\_state ensures that the data split is reproducible, providing consistency in results across multiple runs.

# Training the model

Figure 2-33  illustrates how the X\_train and y\_train datasets were used to train the machine learning model. The execution indicates that the model was successfully trained.

![](OEBPS/image_rsrc52Z.jpg)

Figure 2-33 .

# Code Explanation

lr = LinearRegression()

This line creates an instance of the LinearRegression class and assigns it to the variable lr.

The instance lr will be used to fit the model to the training data and make predictions.

lr.fit(X\_train, y\_train)

fit: The fit method trains the linear regression model on the training data.

X\_train: The training data's feature matrix, containing the independent variables.

y\_train: The training data's target vector, containing the dependent variable.

After running this code, the lr  instance contains the trained linear regression model, which can be used to make predictions on new data using the predict method.

# Predicting with the test data

Figure 2-34  below illustrates how we made predictions using the trained model (lr) and the test data (X\_test).

![](OEBPS/image_rsrc530.jpg)

Figure 2-34

# Code Explanation

y\_pred = lr.predict(X\_test) :

This line of code uses the trained linear regression model (lr) to predict the values of the dependent variable for the test data (X\_test). The predictions are stored in the variable y\_pred.

The predict method applies the learned relationship (from the training phase) to the test data to generate these predictions, providing an estimate of how the model performs on unseen data.

# Model Evaluation

After training the machine learning model, it is important to evaluate its performance by checking the R² score. The R² score indicates how well the model fits the data it was trained on, as demonstrated in Figure 2-35 .

![](OEBPS/image_rsrc531.jpg)

Figure 2-35.

# Code Explanation

r2\_score(y\_test, y\_pred)

The R² score, also known as the coefficient of determination, provides a measure of how well the model's predictions match the actual data

y\_test: This is the actual observed values of the dependent variable from the test dataset. It is the true output we are trying to predict.

y\_pred: This is the predicted values of the dependent variable generated by the trained model for the test dataset (X\_test).

# Model Result Interpretation

The output 0.7999876970680433 means that approximately 80%  of the variance in the dependent variable (y\_test) is predictable from the independent variables (X\_test) using the trained model.  

This indicates a relatively good fit, as a high percentage of the variance is explained by the model.

# Let’s make a prediction

Figure 2-36  below illustrates the process of making predictions using the trained machine learning model. It expects us to provide the following features for prediction: sex , smoker , region , age , BMI , and number of children , which are the same features used during model training. These features are passed as input to the predict method, and the model returns the predicted target variable value based on those features.

![](OEBPS/image_rsrc532.jpg)

Figure 2-36.

# Support Vector Regression

Support Vector Regression (SVR) is a highly effective and versatile machine learning method commonly used to address various regression challenges. Its distinctive design allows it to manage complex regression tasks by determining the optimal regression line that accurately reflects the relationships between input and output variables.

Download the dataset using this link: [Insurance Dataset](https://www.google.com/url?q=https://www.kaggle.com/datasets/awaiskaggler/insurance-csv&sa=D&source=editors&ust=1720099681753988&usg=AOvVaw1qEmRxFcDWzY9jJAm9EsET) . The source code is available here: [Support Vector Regression](https://www.google.com/url?q=https://github.com/anyasorc/appliedml/blob/main/Medical_Insurance_Multiple_Linear_Reg.ipynb&sa=D&source=editors&ust=1720099681754452&usg=AOvVaw2p0VIxTh5aYts45SQmqlOd)  

# Import Libraries

Figure 2-37  shows all the imported required libraries

![](OEBPS/image_rsrc533.jpg)

Figure 2-37.

Import and View Data

Figure 2-38   demonstrates how the data was imported and viewed, as shown below.

![](OEBPS/image_rsrc534.jpg)

Figure 2-38.

# Calculating the frequency of unique values in a DataFrame column named 'region'.

The code df.region.value\_counts()  calculates the frequency of each unique region in the region  column of the DataFrame df , displaying how many times each region appears. The same applies to 'smokers', as illustrated in Figure 2-39 .

![](OEBPS/image_rsrc535.jpg)

Figure 2-39.

# Check for missing values

The code df.isna().sum()  is a series of methods that computes the total number of missing values (NaN values) in each column of the DataFrame df , as depicted in Figure 2-40.

![](OEBPS/image_rsrc536.jpg)

Figure 2-40.

# Assign values to X and y

X = df.iloc\[:, :-1\].values:

This line selects all rows and all columns except the last one from the DataFrame df and converts the result into a NumPy array. The resulting array X typically contains the features or predictors as seen in Figure 2-41 .

y = df.iloc\[:, -1\].values:

This line selects all rows and only the last column from the DataFrame df and converts the result into a NumPy array. The resulting array y typically contains the target or response variable as seen in Figure 2-41 .

![](OEBPS/image_rsrc529.jpg)

Figure 2-41

# View data in X

Type X in a new code sell and run the code cell to see the data assigned in X as seen in Figure 2-42  below. The same could be done for y.

![](OEBPS/image_rsrc52T.jpg)

Figure 2-42 . I have labeled the columns with their respective index positions as follows: the first column, Age, is at index position 0; the second column, Sex, is at index position 1; the third column, BMI, is at index position 2; the fourth column, Number of Children, is at index position 3; the fifth column, Smoker, is at index position 4; and the sixth column, Region, is at index position 5.

# Addressing missing values (NaN)

Addressing missing values is relevant for numerical features/columns, as shown in Figure 2-43 . We have selected the features/columns with index positions 0, 2, and 3, which correspond to Age, BMI, and Number of Children, respectively, as illustrated in Figure 2-42 .

![](OEBPS/image_rsrc52U.jpg)

Figure 2-43 . X\[:, \[0, 2, 3\]\]  means "select all rows and the columns at index positions 0, 2, and 3. So, X\[:, \[0, 2, 3\]\]  effectively extracts the Age, BMI, and Number of Children columns for all rows in the dataset.

After identifying the numerical columns, we will use the SimpleImputer class to calculate the mean value for each column and replace any missing values with these means, as demonstrated in Figure 2-44 .

![](OEBPS/image_rsrc52V.jpg)

Figure 2-44.  

# Code Explanation

SimpleImputer(missing\_values=np.nan, strategy='mean')

missing\_values=np.nan: This parameter specifies that the missing values to be imputed are represented by np.nan

strategy='mean': This parameter specifies that the missing values should be replaced with the mean value of the respective column.

imp.fit(X\[:, \[0, 2, 3\]\])

X\[:, \[0, 2, 3\]\]: This selects all rows and the columns at index positions 0, 2, and 3 from the array X. These columns are assumed to be numerical.

.fit(...): This method calculates the mean value of each selected column based on the non-missing values and stores these mean values for later use.

np.set\_printoptions(precision=2)

This function configures how NumPy arrays are displayed. Here, it sets the precision of the printed output to 2 decimal places.

X\[:, \[0, 2, 3\]\] = imp.transform(X\[:, \[0, 2, 3\]\])

X\[:, \[0, 2, 3\]\]: Again, this selects all rows and the columns at index positions 0, 2, and 3 from the array X.

imp.transform(...): This method replaces the missing values in the selected columns with the mean values calculated during the .fit(...) step.

X\[:, \[0, 2, 3\]\] = ...: This assignment updates the selected columns in the original array X with the transformed data where missing values have been replaced.

# ColumTransformer and OneHotEncoder()

Machine learning models does not understand text and hence there is a need to convert them to numerical representations that the models could understand and that’s the reason we need to convert the categorical variables in index position 1 (sex), 4 (smoker), and 5 (Region) as seen in Figure 2-42 .  To achieve that, we will be working with COlumnTransformer and OneHotEncoder as seen in  Figure 2-45 .

![](OEBPS/image_rsrc52W.jpg)

Figure 2-45.

ColumnTransformer : A class from the sklearn.compose module that applies different preprocessing transformations to different columns of a dataset.

OneHotEncoder : A class from the sklearn.preprocessing module that converts categorical features into a format that can be provided to machine learning algorithms to do a better job in prediction.

np : This is the commonly used alias for the NumPy library, which is useful for array operations.

Creating an Instance of ColumnTransformer

![](OEBPS/image_rsrc52X.jpg)

ColumnTransformer(...) :

This initializes a ColumnTransformer object to apply specified transformations to specific columns.

transformers=\[('encoder', OneHotEncoder(), \[1, 4, 5\])\] :

'encoder': The name given to this transformer. It can be any string.  

OneHotEncoder(): This specifies that we are using the OneHotEncoder for the transformation.

\[1, 4, 5\]: This list specifies the indices of the columns to be transformed. Here, columns at index positions 1, 4, and 5 will be one-hot encoded.

remainder='passthrough' :

This parameter specifies what should be done with the columns that are not explicitly transformed. 'passthrough' means that these columns will be left unchanged and included in the output.

# Splitting into train and test set

We need to split our dataset into training and testing sets. We will use an 80:20 split, where 80% of the data will be used to train the model, and the remaining 20% will be used to test it on unseen data. Figure 2-46  illustrates this process.

![](OEBPS/image_rsrc537.jpg)

Figure 2-46.

# Code Explanation

train\_test\_split : This is a function from the sklearn.model\_selection module in the scikit-learn library. The function is used to split the dataset into training and testing sets. X\_train and y\_train are used to train the model. X\_test and y\_test are used to evaluate the model's performance on unseen data

Components of the Function Call :

X: This is the feature matrix (input variables). It contains the independent variables or predictors.

y: This is the target vector (output variable). It contains the dependent variable or response.

test\_size=0.2: This parameter specifies the proportion of the dataset to include in the test split. Here, 0.2 means 20% of the data will be used for testing, and the remaining 80% will be used for training.

random\_state=0: This parameter controls the shuffling applied to the data before splitting. Passing an integer ensures reproducibility of the split, meaning the same data split will occur every time you run the code with this random\_state value.

Output of the Function Call :

X\_train: This is the training subset of the feature matrix. It contains 80% of the rows from X.

X\_test: This is the testing subset of the feature matrix. It contains the remaining 20% of the rows from X.

y\_train: This is the training subset of the target vector. It contains the corresponding 80% of the rows from y that match the rows in X\_train.

y\_test: This is the testing subset of the target vector. It contains the corresponding 20% of the rows from y that match the rows in X\_test.

By using a test\_size of 0.2, we ensure that 20% of the data is reserved for testing, which helps in assessing how well the model generalizes to new data. The random\_state ensures that the data split is reproducible, providing consistency in results across multiple runs.

# Standardizing the data for SVR

In the context of machine learning, particularly when using algorithms that are sensitive to the scale of the input data, it is common to standardize the data. Standardization transforms the data such that it has a mean of zero and a standard deviation of one. This is particularly important for Support Vector Regression (SVR), which is sensitive to the scales of the input features.  Figure 2-47 illustrates how to implement it.

![](OEBPS/image_rsrc538.jpg)

Figure 2-47.

# Code Explanation

![](OEBPS/image_rsrc539.jpg)

Two instances of StandardScaler are created: sc\_X for the input features X and sc\_y for the target variable y

![](OEBPS/image_rsrc53A.jpg)

fit\_transform is a method that first fits the scaler to the data (calculates the mean and standard deviation for each feature in X\_train) and then transforms the data based on these statistics.

After this transformation, each feature in X\_train will have a mean of zero and a standard deviation of one.

![](OEBPS/image_rsrc53B.jpg)

Similarly, fit\_transform is applied to the target variable y\_train.

This is less common in some machine learning contexts but can be important for algorithms like SVR, which can benefit from having the target variable on a similar scale to the input features.

# Training the Model

Figure 2-48  illustrates the process of using the X\_train and y\_train datasets to train the machine learning model. The execution of the training process indicates that the model was successfully trained.

![](OEBPS/image_rsrc53C.jpg)

Figure 2-48.

# Code Explanation

![](OEBPS/image_rsrc53D.jpg)

SVR : This stands for Support Vector Regression, a type of Support Vector Machine (SVM) used for regression tasks.  

kernel='rbf' : The kernel parameter specifies the type of kernel to be used in the algorithm. 'rbf' stands for Radial Basis Function, which is a popular kernel used to handle non-linear relationships between features and the target variable. The RBF kernel maps input features into a higher-dimensional space where a linear separation can be found, making it effective for capturing complex patterns.

![](OEBPS/image_rsrc53E.jpg)

fit(X\_train, y\_train): This method trains the SVR model using the training data. X\_train contains the input features, and y\_train contains the corresponding target values.  

During the fitting process, the SVR algorithm learns the relationship between the input features and the target variable by finding the optimal hyperplane (or decision boundary) that best fits the data, within the specified margin of tolerance (epsilon-insensitive zone).

# Predicting with the test data

Figure 2-49  below illustrates how we made predictions using the trained model (regressor) and the test data (X\_test).

![](OEBPS/image_rsrc53F.jpg)

Figure 2-49.

# Code Explanation

![](OEBPS/image_rsrc53G.jpg)

sc\_X.transform(X\_test): This applies the same standardization that was applied to the training data X\_train to the test data X\_test.  

sc\_X is an instance of StandardScaler that was previously fitted on X\_train. This ensures that X\_test is standardized using the same mean and standard deviation as the training data, keeping the input features on the same scale.

![](OEBPS/image_rsrc53H.jpg)

regressor.predict(...): This uses the trained SVR model to predict the target values for the standardized test data.  

The output of this step is an array of predicted values, but these predictions are still in the standardized scale used for training.

![](OEBPS/image_rsrc53J.jpg)

.reshape(-1, 1): This reshapes the array of predicted values to a 2D array with one column. The -1 argument means that the number of rows is inferred automatically based on the length of the array.  

This reshaping is necessary because the inverse\_transform method of StandardScaler expects a 2D array.

![](OEBPS/image_rsrc53K.jpg)

sc\_y.inverse\_transform(...): This converts the standardized predictions back to the original scale of the target variable y.  

sc\_y is an instance of StandardScaler that was previously fitted on y\_train. The inverse\_transform method undoes the scaling, converting the standardized values back to their original scale.

![](OEBPS/image_rsrc53M.jpg)

The final result, y\_pred, is the array of predicted target values for X\_test, converted back to the original scale of y.

# Model Evaluation

After training the machine learning model, it is important to evaluate its performance by checking the R² score. The R² score indicates how well the model fits the data it was trained on, as demonstrated in Figure 2-50 .

![](OEBPS/image_rsrc53N.jpg)

Figure 2-50.

# Code Explanation

![](OEBPS/image_rsrc53P.jpg)

r2\_score is a function from the sklearn.metrics module in the scikit-learn library.

It is used to evaluate the performance of a regression model by calculating the R-squared (R²) metric, also known as the coefficient of determination.

y\_test represents the actual target values for the test dataset. These are the true values that the model is trying to predict.

y\_pred represents the predicted target values generated by the regression model for the test dataset.

# Model Result Interpretation

An R² value of 0.8869590298175918 which is approximately 88.70%  indicates that your SVR model is performing very well, capturing a significant portion of the variance in the target variable.  

This suggests that the model is effective and accurate for the given regression problem, providing reliable predictions based on the input features.

# Let’s make a prediction

Figure 2-51  below illustrates the process of making predictions using the trained machine learning model. It expects us to provide the following features for prediction: sex , smoker , region , age , BMI , and number of children , which are the same features used during model training.

These features are passed as input to the predict  method, and the model returns the predicted target variable value based on those features.

![](OEBPS/image_rsrc53R.jpg)

Figure 2-51.

# Decision trees regression 

Decision Tree Regression is a powerful and widely used machine learning technique for solving regression problems. Its simplicity, interpretability, and capability to capture complex relationships make it a valuable tool in various domains where accurate numerical value prediction is required.

Download the dataset using this link: [Insurance Dataset](https://www.google.com/url?q=https://www.kaggle.com/datasets/awaiskaggler/insurance-csv&sa=D&source=editors&ust=1720099681775664&usg=AOvVaw1E2aDWzbH0fM19H9MRpxm9) . The source code is available here: [Decision Trees Regression](https://www.google.com/url?q=https://github.com/anyasorc/appliedml/blob/main/Master_Class_Decision_Tree_Medical_Insurance%2520\(1\).ipynb&sa=D&source=editors&ust=1720099681776132&usg=AOvVaw24p7irzhaxnJ2mjY2KLZfZ)  

# Import Libraries

Figure 2-52  displays all the necessary imported libraries.

![](OEBPS/image_rsrc53S.jpg)

Figure 2-52.

# Import and View Data

Figure 2-53  shows how data was imported and viewed as seen below.

![](OEBPS/image_rsrc53T.jpg)

Figure 2-53.

# Calculating the frequency of unique values in the 'region' column of a DataFrame

The code df.region.value\_counts()  calculates the frequency of each unique region in the region  column of the DataFrame df , displaying how many times each region appears. The same method is applied to the smoker  feature, as shown in Figure 2-54 .

![](OEBPS/image_rsrc53U.jpg)

Figure 2-54.

# Check for missing values

The code df.isna().sum()  is a series of methods that calculates the total number of missing values (NaN values) in each column of the DataFrame df , as shown in Figure 2-55 .

![](OEBPS/image_rsrc53V.jpg)

Figure 2-55.

# Assign values to X and y

X = df.iloc\[:, :-1\].values:

This line selects all rows and all columns except the last one from the DataFrame df and converts the result into a NumPy array. The resulting array X typically contains the features or predictors as seen in Figure 2-56 .

y = df.iloc\[:, -1\].values:

This line selects all rows and only the last column from the DataFrame df and converts the result into a NumPy array. The resulting array y typically contains the target or response variable as seen in Figure 2-56 .

![](OEBPS/image_rsrc529.jpg)

Figure 2-56.

# View data in X

Type X  in a new code cell and run it to see the data assigned to X , as shown in Figure 2-57  below. The same can be done for y .

![](OEBPS/image_rsrc52T.jpg)Figure 2-57: I have labeled the columns with their respective index positions as follows: the first column, Age, is at index position 0; the second column, Sex, is at index position 1; the third column, BMI, is at index position 2; the fourth column, Number of Children, is at index position 3; the fifth column, Smoker, is at index position 4; and the sixth column, Region, is at index position 5. 

# Addressing missing values (NaN)

Addressing missing values is relevant for numerical features/columns, as shown in Figure 2-58 . We have selected the features/columns with index positions 0, 2, and 3, which correspond to Age, BMI, and Number of Children, respectively, as illustrated in Figure 2-57 .

![](OEBPS/image_rsrc53W.jpg)

Figure 2-58. X\[:, \[0, 2, 3\]\]  means "select all rows and the columns at index positions 0, 2, and 3. So, X\[:, \[0, 2, 3\]\]  effectively extracts the Age, BMI, and Number of Children columns for all rows in the dataset.

After identifying the numerical columns, we will use the SimpleImputer class to calculate the mean value for each column and replace any missing values with these means, as demonstrated in Figure 2-59 .

![](OEBPS/image_rsrc52V.jpg)

Figure 2-59.

# Code Explanation

SimpleImputer(missing\_values=np.nan, strategy='mean')

missing\_values=np.nan: This parameter specifies that the missing values to be imputed are represented by np.nan

strategy='mean': This parameter specifies that the missing values should be replaced with the mean value of the respective column.

imp.fit(X\[:, \[0, 2, 3\]\])

X\[:, \[0, 2, 3\]\]: This selects all rows and the columns at index positions 0, 2, and 3 from the array X. These columns are assumed to be numerical.

.fit(...): This method calculates the mean value of each selected column based on the non-missing values and stores these mean values for later use.

np.set\_printoptions(precision=2)

This function configures how NumPy arrays are displayed. Here, it sets the precision of the printed output to 2 decimal places.  

X\[:, \[0, 2, 3\]\] = imp.transform(X\[:, \[0, 2, 3\]\])

X\[:, \[0, 2, 3\]\]: Again, this selects all rows and the columns at index positions 0, 2, and 3 from the array X.

imp.transform(...): This method replaces the missing values in the selected columns with the mean values calculated during the .fit(...) step.

X\[:, \[0, 2, 3\]\] = ...: This assignment updates the selected columns in the original array X with the transformed data where missing values have been replaced.

# ColumTransformer and OneHotEncoder()

Machine learning models do not inherently understand text or categorical features. Therefore, there is a need to convert these features into numerical representations that the models can process. This is why we need to convert the categorical variables at index positions 1 (Sex), 4 (Smoker), and 5 (Region), as depicted in Figure 2-57 . To accomplish this, we will utilize ColumnTransformer and OneHotEncoder, as illustrated in Figure 2-60 .

![](OEBPS/image_rsrc53X.jpg)

Figure 2-60.

# Code Explanation.

ColumnTransformer : A class from the sklearn.compose module that applies different preprocessing transformations to different columns of a dataset.

OneHotEncoder : A class from the sklearn.preprocessing module that converts categorical features into a format that can be provided to machine learning algorithms to do a better job in prediction.

np : This is the commonly used alias for the NumPy library, which is useful for array operations.

Creating an Instance of ColumnTransformer

![](OEBPS/image_rsrc52X.jpg)

ColumnTransformer(...) :

This initializes a ColumnTransformer object to apply specified transformations to specific columns.

transformers=\[('encoder', OneHotEncoder(), \[1, 4, 5\])\] :

'encoder': The name given to this transformer. It can be any string.  

OneHotEncoder(): This specifies that we are using the OneHotEncoder for the transformation.

\[1, 4, 5\]: This list specifies the indices of the columns to be transformed. Here, columns at index positions 1, 4, and 5 will be one-hot encoded.

remainder='passthrough' :

This parameter specifies what should be done with the columns that are not explicitly transformed. 'passthrough' means that these columns will be left unchanged and included in the output.

# Splitting into train and test set

We need to split our dataset into training and testing sets. We will use an 80:20 split, where 80% of the data will be used to train the model, and the remaining 20% will be used to test it on unseen data. Figure 2-61  illustrates this process.

![](OEBPS/image_rsrc53Y.jpg)

Figure 2-61.

# Code Explanation

train\_test\_split : This is a function from the sklearn.model\_selection module in the scikit-learn library. The function is used to split the dataset into training and testing sets. X\_train and y\_train are used to train the model. X\_test and y\_test are used to evaluate the model's performance on unseen data

Components of the Function Call :

X: This is the feature matrix (input variables). It contains the independent variables or predictors.

y: This is the target vector (output variable). It contains the dependent variable or response.

test\_size=0.2: This parameter specifies the proportion of the dataset to include in the test split. Here, 0.2 means 20% of the data will be used for testing, and the remaining 80% will be used for training.

random\_state=0: This parameter controls the shuffling applied to the data before splitting. Passing an integer ensures reproducibility of the split, meaning the same data split will occur every time you run the code with this random\_state value.

Output of the Function Call :

X\_train: This is the training subset of the feature matrix. It contains 80% of the rows from X.

X\_test: This is the testing subset of the feature matrix. It contains the remaining 20% of the rows from X.

y\_train: This is the training subset of the target vector. It contains the corresponding 80% of the rows from y that match the rows in X\_train.

y\_test: This is the testing subset of the target vector. It contains the corresponding 20% of the rows from y that match the rows in X\_test.

By using a test\_size of 0.2, we ensure that 20% of the data is reserved for testing, which helps in assessing how well the model generalizes to new data. The random\_state ensures that the data split is reproducible, providing consistency in results across multiple runs.

# Training the model

Figure 2-62  illustrates how the X\_train and y\_train datasets were used to train the machine learning model. The execution indicates that the model was successfully trained.

![](OEBPS/image_rsrc53Z.jpg)

Figure 2-62.

# Code Explanation

![](OEBPS/image_rsrc540.jpg)

DecisionTreeRegressor(random\_state=0): This line creates an instance of the DecisionTreeRegressor class.

random\_state=0: This parameter sets the random seed for reproducibility. By fixing the random state, the same results will be obtained each time the code is run, which is useful for consistency in testing and debugging.

dt.fit(X\_train, y\_train): This line fits the Decision Tree Regressor model to the training data.

X\_train: This represents the training data features (input variables).

y\_train: This represents the training data target (output variable or labels).

# Predicting with the test data

Figure 2-63  below illustrates how we made predictions using the trained model (dt) and the test data (X\_test).

![](OEBPS/image_rsrc541.jpg)

Figure 2-63.

# Code Explanation

dt.predict(X\_test): This line uses the trained Decision Tree Regressor model (dt) to make predictions on the test data (X\_test).

X\_test: This represents the test data features (input variables) for which predictions are to be made.

The predicted target values for the test data are stored in the variable y\_pred.

# Model Evaluation

After training the machine learning model, it is important to evaluate its performance by checking the R² score. The R² score indicates how well the model fits the data it was trained on, as demonstrated in Figure 2-64.

![](OEBPS/image_rsrc542.jpg)

Figure 2-64.

# Code Explanation

r2\_score is a function from the sklearn.metrics module in the scikit-learn library. It is used to evaluate the performance of a regression model by calculating the R-squared (R²) metric, also known as the coefficient of determination.

y\_test represents the actual target values for the test dataset. These are the true values that the model is trying to predict.

y\_pred represents the predicted target values generated by the regression model for the test dataset.

# Model Result Interpretation

An R² value of 0.7142644756791616 indicates that the regression model captures a substantial portion of the variance in the target variable. This means that approximately 71.43%  of the variability in the target variable can be explained by the input features used in the model.

Despite the model's reasonable performance, there is still room for improvement. Further analysis and refinement may be necessary to enhance its predictive capabilities and capture more of the variability in the target variable.

# Let’s make a prediction

Figure 2-65  below illustrates the process of making predictions using the trained machine learning model. It expects us to provide the following features for prediction: sex, smoker, region, age, BMI, and number of children, which are the same features used during model training. These features are passed as input to the predict method, and the model returns the predicted target variable value based on those features.

![](OEBPS/image_rsrc543.jpg)

Figure 2-65.

# Random Forest Regression

Random Forest Regression is a widely used machine learning algorithm for regression tasks. This algorithm employs a technique where it randomly selects subsets of features and data points to construct multiple decision trees. The final prediction is then made by combining the predictions from all the decision trees.

Download the dataset using this link: [Insurance Dataset](https://www.google.com/url?q=https://www.kaggle.com/datasets/awaiskaggler/insurance-csv&sa=D&source=editors&ust=1720099681790113&usg=AOvVaw0CjSgAWTAoUrmV96Ol1N72) . The source code is available here: [Random Forest Regression](https://www.google.com/url?q=https://github.com/anyasorc/appliedml/blob/main/Master_Class_Random_Forest_Tree_Medical_Insurance%2520\(1\).ipynb&sa=D&source=editors&ust=1720099681790532&usg=AOvVaw1coTkCph-fmx_MHSnMqCAE)  

# Import Libraries

Figure 2-66  displays all the necessary imported libraries.

![](OEBPS/image_rsrc544.jpg)

Figure 2-66.

# Import and View Data

Figure 2-67  shows how data was imported and viewed as seen below.

![](OEBPS/image_rsrc545.jpg)

Figure 2-67.

# Calculating the frequency of unique values in the 'region' column of a DataFrame.

The code df.region.value\_counts()  calculates the frequency of each unique region in the region  column of the DataFrame df , displaying how many times each region appears. The same method applies to the smoker  feature, as depicted in Figure 2-68 .

![](OEBPS/image_rsrc546.jpg)

Figure 2-68.

# Check for missing values

The code df.isna().sum()  is a series of methods that calculates the total number of missing values (NaN values) in each column of the DataFrame df , as shown in Figure 2-69 .

![](OEBPS/image_rsrc547.jpg)

Figure 2-69.

# Assign values to X and y

X = df.iloc\[:, :-1\].values:

This line selects all rows and all columns except the last one from the DataFrame df and converts the result into a NumPy array. The resulting array X typically contains the features or predictors as seen in Figure 2-70 .

y = df.iloc\[:, -1\].values:

This line selects all rows and only the last column from the DataFrame df and converts the result into a NumPy array. The resulting array y typically contains the target or response variable as seen in Figure 2-70 .

![](OEBPS/image_rsrc529.jpg)

Figure 2-70.

# View data in X

Type X in a new code sell and run the code cell to see the data assigned in X as seen in Figure 2-71  below. The same could be done for y.

![](OEBPS/image_rsrc52T.jpg)

Figure 2-71. I have labeled the columns with their respective index positions as follows: the first column, Age, is at index position 0; the second column, Sex, is at index position 1; the third column, BMI, is at index position 2; the fourth column, Number of Children, is at index position 3; the fifth column, Smoker, is at index position 4; and the sixth column, Region, is at index position 5.

# Addressing missing values (NaN)

Addressing missing values is relevant for numerical features/columns, as shown in Figure 2-72 . We have selected the features/columns with index positions 0, 2, and 3, which correspond to Age, BMI, and Number of Children, respectively, as illustrated in Figure 2-71 .

![](OEBPS/image_rsrc548.jpg)

Figure 2-72. X\[:, \[0, 2, 3\]\]  means "select all rows and the columns at index positions 0, 2, and 3. So, X\[:, \[0, 2, 3\]\]  effectively extracts the Age, BMI, and Number of Children columns for all rows in the dataset.

After identifying the numerical columns, we will use the SimpleImputer class to calculate the mean value for each column and replace any missing values with these means, as demonstrated in Figure 2-73 .

![](OEBPS/image_rsrc52V.jpg)

Figure 2-73.

# Code Explanation

SimpleImputer(missing\_values=np.nan, strategy='mean')

missing\_values=np.nan: This parameter specifies that the missing values to be imputed are represented by np.nan

strategy='mean': This parameter specifies that the missing values should be replaced with the mean value of the respective column.

imp.fit(X\[:, \[0, 2, 3\]\])

X\[:, \[0, 2, 3\]\]: This selects all rows and the columns at index positions 0, 2, and 3 from the array X. These columns are assumed to be numerical.

.fit(...): This method calculates the mean value of each selected column based on the non-missing values and stores these mean values for later use.

np.set\_printoptions(precision=2)

This function configures how NumPy arrays are displayed. Here, it sets the precision of the printed output to 2 decimal places.

X\[:, \[0, 2, 3\]\] = imp.transform(X\[:, \[0, 2, 3\]\])

X\[:, \[0, 2, 3\]\]: Again, this selects all rows and the columns at index positions 0, 2, and 3 from the array X.

imp.transform(...): This method replaces the missing values in the selected columns with the mean values calculated during the .fit(...) step.

X\[:, \[0, 2, 3\]\] = ...: This assignment updates the selected columns in the original array X with the transformed data where missing values have been replaced.

# ColumTransformer and OneHotEncoder()

Machine learning models does not understand text and hence there is a need to convert them to numerical representations that the models could understand and that’s the reason we need to convert the categorical variables in index position 1 (sex), 4 (smoker), and 5 (Region) as seen in Figure 2-71 .  To achieve that, we will be working with COlumnTransformer and OneHotEncoder as seen in Figure 2-74 .

![](OEBPS/image_rsrc549.jpg)

Figure 2-74.

# Code Explanation.

ColumnTransformer : A class from the sklearn.compose module that applies different preprocessing transformations to different columns of a dataset.

OneHotEncoder : A class from the sklearn.preprocessing module that converts categorical features into a format that can be provided to machine learning algorithms to do a better job in prediction.

np : This is the commonly used alias for the NumPy library, which is useful for array operations.

Creating an Instance of ColumnTransformer

![](OEBPS/image_rsrc52X.jpg)

ColumnTransformer(...) :

This initializes a ColumnTransformer object to apply specified transformations to specific columns.

transformers=\[('encoder', OneHotEncoder(), \[1, 4, 5\])\] :

'encoder': The name given to this transformer. It can be any string.  

OneHotEncoder(): This specifies that we are using the OneHotEncoder for the transformation.

\[1, 4, 5\]: This list specifies the indices of the columns to be transformed. Here, columns at index positions 1, 4, and 5 will be one-hot encoded.

remainder='passthrough' :

This parameter specifies what should be done with the columns that are not explicitly transformed. 'passthrough' means that these columns will be left unchanged and included in the output.

# Splitting into train and test set

We need to split our dataset into training and testing sets. We will use an 80:20 split, where 80% of the data will be used to train the model, and the remaining 20% will be used to test it on unseen data. Figure 2-75  illustrates this process.

![](OEBPS/image_rsrc54A.jpg)

Figure 2-75.

# Code Explanation

train\_test\_split: This is a function from the sklearn.model\_selection module in the scikit-learn library. The function is used to split the dataset into training and testing sets. X\_train and y\_train are used to train the model. X\_test and y\_test are used to evaluate the model's performance on unseen data

Components of the Function Call :

X: This is the feature matrix (input variables). It contains the independent variables or predictors.

y: This is the target vector (output variable). It contains the dependent variable or response.

test\_size=0.2: This parameter specifies the proportion of the dataset to include in the test split. Here, 0.2 means 20% of the data will be used for testing, and the remaining 80% will be used for training.

random\_state=0: This parameter controls the shuffling applied to the data before splitting. Passing an integer ensures reproducibility of the split, meaning the same data split will occur every time you run the code with this random\_state value.

Output of the Function Call :

X\_train: This is the training subset of the feature matrix. It contains 80% of the rows from X.

X\_test: This is the testing subset of the feature matrix. It contains the remaining 20% of the rows from X.

y\_train: This is the training subset of the target vector. It contains the corresponding 80% of the rows from y that match the rows in X\_train.

y\_test: This is the testing subset of the target vector. It contains the corresponding 20% of the rows from y that match the rows in X\_test.

By using a test\_size of 0.2, we ensure that 20% of the data is reserved for testing, which helps in assessing how well the model generalizes to new data. The random\_state ensures that the data split is reproducible, providing consistency in results across multiple runs.

# Training the model

Figure 2-76  illustrates how the X\_train and y\_train datasets were used to train the machine learning model. The execution indicates that the model was successfully trained.

![](OEBPS/image_rsrc54B.jpg)

Figure 2-76.

# Code Explanation

![](OEBPS/image_rsrc54C.jpg)

RandomForestRegressor : This line creates an instance of the RandomForestRegressor class.

n\_estimators=10 : This specifies the number of decision trees in the random forest. In this case, the forest consists of 10 decision trees.

random\_state=0 : This parameter sets the random seed for reproducibility. By fixing the random state, the same results will be obtained each time the code is run, ensuring consistency in testing and debugging.

![](OEBPS/image_rsrc54D.jpg)

fit : This method trains the Random Forest Regressor on the provided training data.

X\_train : This represents the training data features (input variables).

y\_train : This represents the training data target (output variable or labels).

# Predicting with the test data

Figure 2-77  below illustrates how we made predictions using the trained model (lr) and the test data (X\_test).

![](OEBPS/image_rsrc54E.jpg)

Figure 2-77.

# Code Explanation

Rf.predict(X\_test): This line uses the trained Random Forest model (Rf) to make predictions on the test data (X\_test).

X\_test: This represents the test data features (input variables) for which predictions are to be made. These features are used by the model to generate predictions.

The predicted target values for the test data are stored in the variable y\_pred.

# Model Evaluation

After training the machine learning model, it is important to evaluate its performance by checking the R² score. The R² score indicates how well the model fits the data it was trained on, as demonstrated in Figure 2-78 .

![](OEBPS/image_rsrc54F.jpg)

Figure 2-78.

# Code Explanation

r2\_score is a function from the sklearn.metrics module in the scikit-learn library. It is used to evaluate the performance of a regression model by calculating the R-squared (R²) metric, also known as the coefficient of determination.

y\_test: This represents the actual target values for the test dataset. These are the true values that the model is trying to predict.

y\_pred: This represents the predicted target values generated by the regression model for the test dataset.

# Model Result Interpretation

An R² value of 0.8611562299112945 indicates that the regression model captures a significant portion of the variance in the target variable, with approximately 86.12%  of the variability explained by the input features.  

This high R² value suggests that the model performs very well, providing accurate and reliable predictions for the given regression problem. However, it is still essential to evaluate the model for potential overfitting and ensure its robustness across different datasets

# Let’s make a prediction

Figure 2-79  below illustrates the process of making predictions using the trained machine learning model. It expects us to provide the following features for prediction: sex, smoker, region, age, BMI, and number of children, which are the same features used during model training. These features are passed as input to the predict method, and the model returns the predicted target variable value based on those features.

![](OEBPS/image_rsrc54G.jpg)

Figure 2-79.

# Conclusion

We applied the insurance data to train and evaluate several machine learning models, which included Polynomial Regression , Multiple Linear Regression , Support Vector Regression , Decision Tree Regression , and Random Forest Regression . Here are the performance outcomes for these models:

| # || Model Name || Model R² Score (%) |
| --- | --- | --- |
| 1 || Polynomial regression || 85.12% |
| 2 || Multiple linear regression || 80% |
| 3 || Support Vector Regression || 88.70% |
| 4 || Decision trees regression || 71.43% |
| 5 || Random Forest Regression || 86.12% |

Based on the R² scores, Support Vector Regression  (SVR) is recommended due to its highest R² value of 88.70% , indicating superior performance. This high R² value implies that SVR explains 88.70% of the variance in the target variable, suggesting that SVR not only performed well on the provided dataset but is also likely to deliver better predictive accuracy and reliability compared to the other models.

# Chapter 3  
Classification

# Classification

In machine learning, a classification problem involves categorizing data into predefined classes or categories. The main aim is to build a model that learns from labeled training data and predicts the class or category of new, unidentified data points. This task is essential in various fields, such as medicine , finance , and marketing , where it is important to classify data into distinct categories for analysis and decision-making.

Classification problems can be binary, where there are only two classes (e.g., spam vs. non-spam emails), or multi-class, where there are three or more classes (e.g., classifying types of animals in a zoo).

# Types of Classification models

Logistic Regression Model

K-Nearest Neighbour (K-NN) Model

Support Vector Machine (SVM) Model

Naïve Bayes Model

Kernel SVM Model

Decision Tree Classification Model

Random Forest Classification Model

# Classification problem statement

Alonzo Hospital, a local healthcare facility, has harnessed technology to boost efficiency in all its departments. Recently, the management decided to hire a data scientist to develop a machine learning model that can interpret heart test results based on patient input. This model analyzes specific cardiac features, such as

age: The age of the patient in years.

sex: The sex of the patient (1 = male; 0 = female).

cp: Chest pain type (0 = typical angina, 1 = atypical angina, 2 = non-anginal pain, 3 = asymptomatic).

trestbps: Resting blood pressure (in mm Hg) on admission to the hospital.

chol: Serum cholesterol in mg/dl.

fbs: Fasting blood sugar > 120 mg/dl (1 = true; 0 = false).

restecg: Resting electrocardiographic results (0 = normal, 1 = having ST-T wave abnormality, 2 = showing probable or definite left ventricular hypertrophy by Estes' criteria).

thalach: Maximum heart rate achieved.

exang: Exercise-induced angina (1 = yes; 0 = no).

oldpeak: ST depression induced by exercise relative to rest.

slope: The slope of the peak exercise ST segment (0 = upsloping, 1 = flat, 2 = downsloping).

ca: Number of major vessels (0-3) colored by fluoroscopy.

thal: Thalassemia (1 = normal; 2 = fixed defect; 3 = reversible defect).

Target: 0 indicates the patient's heart is healthy, while 1 indicates the patient's heart is not healthy.

The hospital hired Ade with the primary responsibility of developing a machine learning model to predict the presence of heart disease in patients. Following this, he will collaborate with the front-end development team to create the XYZ Breast Heart Prediction Model.

Patients will input parameters from their device readings into the portal. The self-diagnosis results will display as 0, indicating no presence of heart disease, or 1, indicating the presence of heart disease. If the outcome is 1, patients will be advised to schedule an appointment with the hospital to consult with a specialist.

Implementing this model will help:

Reduce the pressure on hospital staff by streamlining the diagnostic process.

Manage hospital resources more effectively, ensuring that appointments are evenly distributed among available consultants.

Inform decisions about hiring or engaging additional breast cancer specialists as needed.

Note: accuracy\_score is a metric used to evaluate the performance of a classification model. It measures the proportion of correctly classified instances out of the total instances.

You can download the dataset for classification via this link: [Heart Disease](https://www.google.com/url?q=https://www.kaggle.com/datasets/arezaei81/heartcsv&sa=D&source=editors&ust=1720099681834178&usg=AOvVaw2Ogt5nu6dVZIvv1V3Km2mc)  

The dataset 'heart.csv' includes data pertaining to heart issues, with a target class indicating whether a patient is diagnosed with heart disease (1) or not (0). Our objective is to apply various machine learning classification models to the data and select the model with the highest accuracy score.

# Logistic Regression 

Logistic regression is a statistical technique used to solve binary classification problems. In binary classification, the outcome variable is categorical with only two classes. Despite its name, logistic regression is primarily used for classification tasks rather than regression. It is particularly useful when the dependent variable is binary, meaning it can have only two possible outcomes, such as 0 or 1, Yes or No, or True or False.

The source code is available here: [Logistic Regression](https://www.google.com/url?q=https://github.com/anyasorc/appliedml/blob/main/Classification_Logistic_Regression%2520\(1\).ipynb&sa=D&source=editors&ust=1720099681835062&usg=AOvVaw1h_ACip0MOpvZdDW-X_rRp)  

# Import Libraries

Figure 3-1  shows all the imported required libraries

![](OEBPS/image_rsrc54H.jpg)

Figure 3-1.

# Import and View Data

Figure 3-2  shows how data was imported and viewed as seen below.

![](OEBPS/image_rsrc54J.jpg)

Figure 3-2.

# Assign values to X and y

X = df.iloc\[:, :-1\].values:

This line selects all rows and all columns except the last one from the DataFrame df and converts the result into a NumPy array. The resulting array X typically contains the features or predictors as seen in Figure 3-3 .  

y = df.iloc\[:, -1\].values:

This line selects all rows and only the last column from the DataFrame df and converts the result into a NumPy array. The resulting array y typically contains the target or response variable as seen in Figure 3-3 .

![](OEBPS/image_rsrc54K.jpg)

Figure 3-3.

# Splitting into train and test set

We must divide our dataset into training and testing sets. Employing an 80:20 split, 80% of the data will train the model, and the remaining 20% will assess its performance on unseen data. Figure 3-4  visually demonstrates this process.

![](OEBPS/image_rsrc54M.jpg)

Figure 3-4.

# Standardizing the data

In the context of machine learning, particularly when using algorithms that are sensitive to the scale of the input data, it is common to standardize the data. Standardization transforms the data such that it has a mean of zero and a standard deviation of one. Figure 3-5 illustrates how to implement it.

![](OEBPS/image_rsrc54N.jpg)

Figure 3-5.

# Code Explanation

The code snippet in Figure 3-5  uses the \`StandardScaler\` class from the \`scikit-learn\` library to standardize features by removing the mean and scaling to unit variance. This process is essential for many machine learning algorithms to perform optimally. Here's an explanation of each line:

sc = StandardScaler(): This line creates an instance of the \`StandardScaler\` class. The \`StandardScaler\` is used to standardize the features of the dataset.

X\_train = sc.fit\_transform(X\_train):

fit\_transform: This method first calculates the mean and standard deviation of the \`X\_train\` data (this is the \`fit\` part).

It then uses these statistics to standardize \`X\_train\` by subtracting the mean and dividing by the standard deviation for each feature (this is the \`transform\` part).

The result is that \`X\_train\` is now a standardized version of the original training data, where each feature has a mean of 0 and a standard deviation of 1.

X\_test = sc.transform(X\_test):

transform: This method uses the mean and standard deviation calculated from the \`X\_train\` data to standardize \`X\_test\`.

This ensures that the test data is transformed in the same way as the training data, which is crucial for the consistency of the model's performance.

X\_test\` is now a standardized version of the original test data, following the same scale as \`X\_train\`.

Here's a bit more detail on why standardization is important:

Consistency: It ensures that the training and test data are on the same scale, which is crucial for the performance of many machine learning models.

Algorithm Performance: Algorithms like gradient descent used in logistic regression or neural networks converge faster with standardized data.

Improved Accuracy: Some algorithms, like support vector machines (SVM) and k-nearest neighbors (KNN), are sensitive to the scale of the data and perform better with standardized data.

By using \`StandardScaler\`, you help ensure that your machine learning model works more effectively and consistently.

# Training the Model

Figure 3-6  illustrates the process of using the X\_train and y\_train datasets to train the machine learning model. The execution of the training process indicates that the model was successfully trained.

![](OEBPS/image_rsrc54P.jpg)

Figure 3-6.

# Code Explanation

Looking at the code snippet in Figure 3-6  cs = LogisticRegression(random\_state=0); cs.fit(X\_train, y\_train) is used to create and train a logistic regression model using the scikit-learn library in Python.

cs = LogisticRegression(random\_state=0) :

LogisticRegression is the class for creating logistic regression models.

cs is the variable that will store the instance of the logistic regression model.

random\_state=0 is a parameter that ensures the results are reproducible by setting a seed for the random number generator. This way, you get the same results every time you run the code. If random\_state is set to None, the seed is randomly selected, which can lead to different results each time you run the model.

cs.fit(X\_train, y\_train) :

fit is a method used to train the model.

X\_train is the training data containing the features (input variables) that the model will learn from.

y\_train is the training data containing the target labels (output variables) that correspond to the features in X\_train.

# Predicting with the test data

Figure 3-7  below illustrates how we made predictions using the trained model (cs) and the test data (X\_test).

![](OEBPS/image_rsrc54R.jpg)

Figure 3-7.

# Code Explanation

The line y\_pred = cs.predict(X\_test) is specifically using a logistic regression model (cs) to make predictions on a test dataset (X\_test). Here's a detailed explanation tailored to logistic regression:

cs: This is an instance of a logistic regression model that has been trained on your training data. In scikit-learn, this could be created using LogisticRegression() and then fitted to the training data using cs.fit(X\_train, y\_train).

X\_test: This is the test dataset containing the features for which you want to predict the target variable. These features should be preprocessed similarly to the training data (e.g., standardized).

predict(X\_test): This method is used to predict the class labels for the input data (X\_test) based on the logistic regression model cs.

y\_pred is an array of predicted class labels for each observation in X\_test. For a binary classification problem, the values in y\_pred will be either 0 or 1.

# Model Evaluation

After training the machine learning model, it is important to evaluate its performance. Let's first examine the confusion matrix before considering the accuracy score as seen in Figure 3-8 .

![](OEBPS/image_rsrc54R.jpg)

Figure 3-8.

# Code Explanation

The line \`cm = confusion\_matrix(y\_test, y\_pred)\` involves using the \`confusion\_matrix\` function from the \`scikit-learn\` library to evaluate the performance of a classification model. Here’s a detailed explanation:

confusion\_matrix(y\_test, y\_pred):

y\_test: This is the array of true class labels for the test dataset. These are the actual values that you are trying to predict.

y\_pred: This is the array of predicted class labels that the model has generated for the test dataset. These predictions are made by the model and are based on the test features (\`X\_test\`).  

Confusion Matrix:

The confusion matrix is a table that is often used to describe the performance of a classification model. It shows the number of correct and incorrect predictions made by the model compared to the actual outcomes (ground truth).

It is a 2x2 matrix for binary classification problems, which looks like this:

\[\[TN, FP\],

\[FN, TP\]\]

Where:

TN (True Negative): The number of correctly predicted negative class instances (actual negative and predicted negative).

FP (False Positive): The number of incorrectly predicted positive class instances (actual negative but predicted positive).

FN (False Negative): The number of incorrectly predicted negative class instances (actual positive but predicted negative).

TP (True Positive): The number of correctly predicted positive class instances (actual positive and predicted positive).

# Interpreting the Confusion Matrix

The confusion matrix helps you understand how well your classification model is performing in terms of its ability to predict each class correctly.

It provides detailed insight into the types of errors the model is making.

High values on the diagonal (TN and TP) indicate good performance.

High values off the diagonal (FP and FN) indicate areas where the model is making mistakes.

By examining the confusion matrix, you can gain a deeper understanding of your model's performance beyond what is provided by a single metric like accuracy. This can help you identify specific areas where the model needs improvement.

# Confusion Matrix interpretation

Figure 3-9  shows the confusion matrix from the logistic regression model.

![](OEBPS/image_rsrc54S.jpg)

Figure 3-9.

Let's interpret this confusion matrix:

True Negatives (TN): 77

These are the instances where the actual class was negative (e.g., no heart disease) and the model correctly predicted it as negative.

False Positives (FP): 21

These are the instances where the actual class was negative, but the model incorrectly predicted it as positive (e.g., predicted heart disease when there was actually none).

False Negatives (FN): 7

These are the instances where the actual class was positive (e.g., heart disease predicted), but the model incorrectly predicted it as negative (e.g., predicted no heart disease when there was actually heart disease).

True Positives (TP): 100

These are the instances where the actual class was positive, and the model correctly predicted it as positive.

From this confusion matrix, we can calculate several performance metrics (Accuracy, Precision, Recall, and F1 Score)

Accuracy :

The formula for accuracy is given by:

![](OEBPS/image_rsrc54T.jpg)   

In the provided example:

TN = 77

TP = 100

FP = 21

FN = 7

Plugging these values into the formula:

![](OEBPS/image_rsrc54U.jpg)

This means the model correctly classified approximately 86.3% of the instances.

Precision :

The formula for Precision is given by:

![](OEBPS/image_rsrc54V.jpg)

In the provided example:

TP = 100

FP = 21

Plugging these values into the formula:

![](OEBPS/image_rsrc54W.jpg)

This means that approximately 82.6% of the instances predicted as positive by the model were actually positive.

Recall :

The formula for recall is given by:

![](OEBPS/image_rsrc54X.jpg)

In the provided example:

TP =  100

FN = 7

Plugging these values into the formula:  

![](OEBPS/image_rsrc54Y.jpg)

This means that approximately 93.5% of the actual positive instances were correctly identified by the model.

F1 Score:

The formula for F1 Score is given by:

![](OEBPS/image_rsrc54Z.jpg)

In the provided example:

Precision=0.826

Recall=0.935

Plugging these values into the formula:

![](OEBPS/image_rsrc550.jpg)

# Interpretation

Accuracy (86.3%) : Indicates that the model correctly predicted 86.3% of the instances.

Precision (82.6%) : Of all the instances predicted as positive, 82.6% were actually positive. This indicates a moderate level of false positives.

Recall (93.5%) : The model correctly identified 93.5% of the actual positive instances. This indicates a high level of false negatives.

F1 Score (87.8%) : This combines precision and recall into a single metric, suggesting a good balance between the two.

# Model Evaluation

After training the machine learning model, it is important to evaluate its performance by checking the accuracy score. The accuracy score shows how well the model fits the data it was trained on, as illustrated in Figure 3-10.

![](OEBPS/image_rsrc551.jpg)

Figure 3-10.

# Code Explanation

The function accuracy\_score(y\_test, y\_pred) from the scikit-learn library is used to calculate the accuracy of a classification model. Here’s a detailed explanation:

Inputs:

y\_test: This is the array of true labels for the test dataset. These labels are the actual values that you are trying to predict.

y\_pred: This is the array of predicted labels that the model has generated for the test dataset. These predictions are based on the test features (X\_test).

# Model Result Interpretation

An accuracy score of 0.8634146341463415 indicates that the model correctly predicted 86.34% of the instances. In other words, for every 100 predictions, the model accurately predicts about 86 of them, reflecting good overall performance.

# Let’s make a prediction

Figure 3-11  below illustrates the process of making predictions using the trained machine learning model. It expects us to provide the following features for prediction:

age: The age of the patient in years.

sex: The sex of the patient (1 = male; 0 = female).

cp: Chest pain type (0 = typical angina, 1 = atypical angina, 2 = non-anginal pain, 3 = asymptomatic).

trestbps: Resting blood pressure (in mm Hg) on admission to the hospital.

chol: Serum cholesterol in mg/dl.

fbs: Fasting blood sugar > 120 mg/dl (1 = true; 0 = false).

restecg: Resting electrocardiographic results (0 = normal, 1 = having ST-T wave abnormality, 2 = showing probable or definite left ventricular hypertrophy by Estes' criteria).

thalach: Maximum heart rate achieved.

exang: Exercise-induced angina (1 = yes; 0 = no).

oldpeak: ST depression induced by exercise relative to rest.

slope: The slope of the peak exercise ST segment (0 = upsloping, 1 = flat, 2 = downsloping).

ca: Number of major vessels (0-3) colored by fluoroscopy.

thal: Thalassemia (1 = normal; 2 = fixed defect; 3 = reversible defect).

![](OEBPS/image_rsrc552.jpg)

Figure 3-11.

# K-Nearest Neighbour (K-NN)

K-Nearest Neighbors (K-NN) is a supervised machine learning algorithm that is used for both classification and regression tasks. In classification, it identifies the class of a given data point by examining the classes of its nearest neighbors. In regression, it predicts the value of a data point by averaging the values of its nearest neighbors.

The source code is available here: [KNN](https://www.google.com/url?q=https://github.com/anyasorc/appliedml/blob/main/Classification_KNN.ipynb&sa=D&source=editors&ust=1720099681856543&usg=AOvVaw08NazI4n392YBuznNNYIms)  

# Import Libraries

Figure 3-12  shows all the imported required libraries

![](OEBPS/image_rsrc553.jpg)

Figure 3-12.

# Import and View Data

Figure 3-13  shows how data was imported and viewed as seen below

![](OEBPS/image_rsrc554.jpg)

Figure 3-13.

# Assign values to X and y

X = df.iloc\[:, :-1\].values:

This line selects all rows and all columns except the last one from the DataFrame df and converts the result into a NumPy array. The resulting array X typically contains the features or predictors as seen in Figure 3-14 .

y = df.iloc\[:, -1\].values:

This line selects all rows and only the last column from the DataFrame df and converts the result into a NumPy array. The resulting array y typically contains the target or response variable as seen in Figure 3-14 .

![](OEBPS/image_rsrc54K.jpg)

Figure 3-14.

# Splitting into train and test set

We need to split our dataset into training and testing sets. We will use an 80:20 split, where 80% of the data will be used to train the model, and the remaining 20% will be used to test it on unseen data. Figure 3-15  illustrates this process.

![](OEBPS/image_rsrc555.jpg)

Figure 3-15.

# Standardizing the data

In the context of machine learning, particularly when using algorithms that are sensitive to the scale of the input data, it is common to standardize the data. Standardization transforms the data such that it has a mean of zero and a standard deviation of one.  Figure 3-16 illustrates how to implement it.

![](OEBPS/image_rsrc54N.jpg)

Figure 3-16.

# Code Explanation

The code snippet in Figure 3-16  uses the \`StandardScaler\` class from the \`scikit-learn\` library to standardize features by removing the mean and scaling to unit variance. This process is essential for many machine learning algorithms to perform optimally. Here's an explanation of each line:

sc = StandardScaler(): This line creates an instance of the \`StandardScaler\` class. The \`StandardScaler\` is used to standardize the features of the dataset.

X\_train = sc.fit\_transform(X\_train):

fit\_transform: This method first calculates the mean and standard deviation of the \`X\_train\` data (this is the \`fit\` part).

It then uses these statistics to standardize \`X\_train\` by subtracting the mean and dividing by the standard deviation for each feature (this is the \`transform\` part).

The result is that \`X\_train\` is now a standardized version of the original training data, where each feature has a mean of 0 and a standard deviation of 1.

X\_test = sc.transform(X\_test):

transform: This method uses the mean and standard deviation calculated from the \`X\_train\` data to standardize \`X\_test\`.

This ensures that the test data is transformed in the same way as the training data, which is crucial for the consistency of the model's performance.

X\_test\` is now a standardized version of the original test data, following the same scale as \`X\_train\`.

Here's a bit more detail on why standardization is important:

Consistency: It ensures that the training and test data are on the same scale, which is crucial for the performance of many machine learning models.

Algorithm Performance: Algorithms like gradient descent used in logistic regression or neural networks converge faster with standardized data.

Improved Accuracy: Some algorithms, like support vector machines (SVM) and k-nearest neighbors (KNN), are sensitive to the scale of the data and perform better with standardized data.

By using \`StandardScaler\`, you help ensure that your machine learning model works more effectively and consistently.

# Training the Model

Figure 3-17  illustrates the process of using the X\_train and y\_train datasets to train the machine learning model. The execution of the training process indicates that the model was successfully trained.

![](OEBPS/image_rsrc556.jpg)

Figure 3-17.

# Code Explanation

Referring to the code snippet in Figure 3-17,

cs = KNeighborsClassifier(n\_neighbors=5, metric='minkowski', p=2); cs.fit(X\_train, y\_train)\` is used to create and train a k-nearest neighbors (K-NN) classifier with the scikit-learn library in Python.

cs = KNeighborsClassifier(n\_neighbors=5, metric='minkowski', p=2):

KNeighborsClassifier is the class for creating a k-nearest neighbors classifier.

cs is the variable that will store the instance of the K-NN classifier.

n\_neighbors=5 specifies the number of neighbors to use. In this case, the algorithm will consider the 5 nearest neighbors to make a prediction.

metric='minkowski' specifies the distance metric to use for finding the nearest neighbors. The Minkowski distance is a generalized distance metric that includes several other distance metrics as special cases.

p=2 sets the parameter for the Minkowski metric. When p=2, the Minkowski distance is equivalent to the Euclidean distance.

cs.fit(X\_train, y\_train):

fit is a method used to train the model.

X\_train is the training data containing the features (input variables) that the model will learn from.

y\_train is the training data containing the target labels (output variables) that correspond to the features in X\_train

# Predicting with the test data

Figure 3-18  below illustrates how we made predictions using the trained model (cs) and the test data (X\_test).

![](OEBPS/image_rsrc557.jpg)

Figure 3-18.

# Code Explanation

The line y\_pred = cs.predict(X\_test) where cs is a k-nearest neighbors (K-NN) classifier:

cs is an instance of the KNeighborsClassifier that has been trained on a dataset using the fit method. This instance now contains the training data and is ready to make predictions.

X\_test is the test dataset consisting of feature values (input variables) for which you want to predict the class labels. These are new data points that the model has not seen during training.

The predict method is used to make predictions on new data. When you call cs.predict(X\_test), the classifier uses the K-NN algorithm to determine the class labels for the instances in X\_test.  

The predicted class labels for all instances in X\_test are stored in the array y\_pred.

# Model Evaluation

After training the machine learning model, it is important to evaluate its performance. Let's first examine the confusion matrix before considering the accuracy score as seen in Figure 3-19 .

![](OEBPS/image_rsrc557.jpg)

Figure 3-19.

# Code Explanation

The line \`cm = confusion\_matrix(y\_test, y\_pred)\` involves using the \`confusion\_matrix\` function from the \`scikit-learn\` library to evaluate the performance of a classification model. Here’s a detailed explanation:

confusion\_matrix(y\_test, y\_pred):

y\_test: This is the array of true class labels for the test dataset. These are the actual values that you are trying to predict.

y\_pred: This is the array of predicted class labels that the model has generated for the test dataset. These predictions are made by the model and are based on the test features (\`X\_test\`).

Confusion Matrix:

The confusion matrix is a table that is often used to describe the performance of a classification model. It shows the number of correct and incorrect predictions made by the model compared to the actual outcomes (ground truth).

It is a 2x2 matrix for binary classification problems, which looks like this:

\[\[TN, FP\],

\[FN, TP\]\]

Where:

TN (True Negative): The number of correctly predicted negative class instances (actual negative and predicted negative).

FP (False Positive): The number of incorrectly predicted positive class instances (actual negative but predicted positive).

FN (False Negative): The number of incorrectly predicted negative class instances (actual positive but predicted negative).

TP (True Positive): The number of correctly predicted positive class instances (actual positive and predicted positive).

# Interpreting the Confusion Matrix

The confusion matrix helps you understand how well your classification model is performing in terms of its ability to predict each class correctly.

It provides detailed insight into the types of errors the model is making:

High values on the diagonal (TN and TP) indicate good performance.

High values off the diagonal (FP and FN) indicate areas where the model is making mistakes.

By examining the confusion matrix, you can gain a deeper understanding of your model's performance beyond what is provided by a single metric like accuracy. This can help you identify specific areas where the model needs improvement.

# Confusion Matrix interpretation

Figure 3-20  shows the confusion matrix from the logistic regression model.

![](OEBPS/image_rsrc558.jpg)

Figure 3-20.

Let's interpret this confusion matrix:

True Negatives (TN): 84

These are the instances where the actual class was negative (e.g., no heart disease) and the model correctly predicted it as negative.

False Positives (FP): 14

These are the instances where the actual class was negative, but the model incorrectly predicted it as positive (e.g., predicted heart disease when there was actually none).

False Negatives (FN): 10

These are the instances where the actual class was positive (e.g., malignant tumor), but the model incorrectly predicted it as negative (e.g., predicted no heart disease when there was actually heart disease).

True Positives (TP): 97

These are the instances where the actual class was positive, and the model correctly predicted it as positive.

From this confusion matrix, we can calculate several performance metrics (Accuracy, Precision, Recall, and F1 Score)

Accuracy :

The formula for accuracy is given by:

![](OEBPS/image_rsrc54T.jpg)   

In the provided example:

TN = 84

TP = 97

FP = 14

FN = 10

Plugging these values into the formula:

![](OEBPS/image_rsrc559.jpg)

This means the model correctly classified approximately 86.3% of the instances.

Precision :

The formula for Precision is given by:

![](OEBPS/image_rsrc54V.jpg)

In the provided example:

TP = 97

FP = 14

Plugging these values into the formula:

![](OEBPS/image_rsrc55A.jpg)

This means that approximately 82.6% of the instances predicted as positive by the model were actually positive.

Recall :

The formula for recall is given by:

![](OEBPS/image_rsrc54X.jpg)

In the provided example:

TP =  97

FN = 14

Plugging these values into the formula:  

![](OEBPS/image_rsrc55B.jpg)

This means that approximately 93.5% of the actual positive instances were correctly identified by the model.

F1 Score:

The formula for F1 Score is given by:

![](OEBPS/image_rsrc54Z.jpg)

In the provided example:

Precision=0.874

Recall=0.907

Plugging these values into the formula:

![](OEBPS/image_rsrc55C.jpg)

# Interpretation

Accuracy (88.3%) : indicates that the model correctly predicted 88.3% of the instances, reflecting a high overall correctness in its predictions.

Precision (87.4%) : Of all the instances predicted as positive, 87.4% were actually positive. This indicates a relatively low level of false positives, highlighting the model's reliability in making positive predictions.

Recall (90.7%) : The model correctly identified 90.7% of the actual positive instances. This suggests a relatively low level of false negatives, indicating that the model effectively captures the majority of positive instances

F1 Score (89%) : Combines precision and recall into a single metric, providing a balanced assessment of the model's performance. The F1 score of 89% suggests a good balance between precision and recall, indicating the model's effectiveness in classifying instances into their respective classes.

# Model Evaluation

After training the machine learning model, it is important to evaluate its performance by checking the accuracy score. The accuracy score shows how well the model fits the data it was trained on, as illustrated in Figure 3-21.

![](OEBPS/image_rsrc55D.jpg)

Figure 3-21.

# Code Explanation

The function accuracy\_score(y\_test, y\_pred) from the scikit-learn library is used to calculate the accuracy of a classification model. Here’s a detailed explanation:

Inputs:

y\_test: This is the array of true labels for the test dataset. These labels are the actual values that you are trying to predict.

y\_pred: This is the array of predicted labels that the model has generated for the test dataset. These predictions are based on the test features (X\_test).

# Model Result Interpretation

The predicted outcome of 0.8829268292682927, when expressed as a percentage, is approximately 88.29% .

This means that the K-Nearest Neighbors (KNN) model is estimated to have an accuracy of about 88.29%. In other words, the model is expected to correctly classify or predict the class labels for approximately 88.29% of the instances in the dataset.

# Let’s make a prediction

Figure 3-22  below illustrates the process of making predictions using the trained machine learning model. It expects us to provide the following features for prediction:

age: The age of the patient in years.

sex: The sex of the patient (1 = male; 0 = female).

cp: Chest pain type (0 = typical angina, 1 = atypical angina, 2 = non-anginal pain, 3 = asymptomatic).

trestbps: Resting blood pressure (in mm Hg) on admission to the hospital.

chol: Serum cholesterol in mg/dl.

fbs: Fasting blood sugar > 120 mg/dl (1 = true; 0 = false).

restecg: Resting electrocardiographic results (0 = normal, 1 = having ST-T wave abnormality, 2 = showing probable or definite left ventricular hypertrophy by Estes' criteria).

thalach: Maximum heart rate achieved.

exang: Exercise-induced angina (1 = yes; 0 = no).

oldpeak: ST depression induced by exercise relative to rest.

slope: The slope of the peak exercise ST segment (0 = upsloping, 1 = flat, 2 = downsloping).

ca: Number of major vessels (0-3) colored by fluoroscopy.

thal: Thalassemia (1 = normal; 2 = fixed defect; 3 = reversible defect).

![](OEBPS/image_rsrc55E.jpg)

Figure 3-22.

# Support Vector Machine (SVM) Model

Support Vector Machine (SVM) is a supervised learning algorithm employed in machine learning. It's versatile, capable of handling both classification and regression tasks.

The source code is available here: [Support Vector Machine](https://www.google.com/url?q=https://github.com/anyasorc/appliedml/blob/main/Classification_SVM.ipynb&sa=D&source=editors&ust=1720099681879651&usg=AOvVaw1jVWYgvTUnpL9zAKut35Hf)  

# Import Libraries

Figure 3-23  shows all the imported required libraries

![](OEBPS/image_rsrc55F.jpg)

Figure 3-22.

# Import and View Data

Figure 3-23  shows how data was imported and viewed as seen below.

![](OEBPS/image_rsrc55G.jpg)

Figure 3-23.

# Assign values to X and y

X = df.iloc\[:, :-1\].values:

This line selects all rows and all columns except the last one from the DataFrame df and converts the result into a NumPy array. The resulting array X typically contains the features or predictors as seen in Figure 3-24 .

y = df.iloc\[:, -1\].values:

This line selects all rows and only the last column from the DataFrame df and converts the result into a NumPy array. The resulting array y typically contains the target or response variable as seen in Figure 3-24 .

![](OEBPS/image_rsrc54K.jpg)

Figure 3-24.

# Splitting into train and test set

We need to split our dataset into training and testing sets. We will use an 80:20 split, where 80% of the data will be used to train the model, and the remaining 20% will be used to test it on unseen data. Figure 3-25  illustrates this process.

![](OEBPS/image_rsrc55H.jpg)

Figure 3-25.

# Standardizing the data

In the context of machine learning, particularly when using algorithms that are sensitive to the scale of the input data, it is common to standardize the data. Standardization transforms the data such that it has a mean of zero and a standard deviation of one. Figure 3-26 illustrates how to implement it.

![](OEBPS/image_rsrc54N.jpg)

Figure 3-26.

# Code Explanation

The code snippet in Figure 3-5 uses the \`StandardScaler\` class from the \`scikit-learn\` library to standardize features by removing the mean and scaling to unit variance. This process is essential for many machine learning algorithms to perform optimally. Here's an explanation of each line:

sc = StandardScaler(): This line creates an instance of the \`StandardScaler\` class. The \`StandardScaler\` is used to standardize the features of the dataset.

X\_train = sc.fit\_transform(X\_train):

fit\_transform: This method first calculates the mean and standard deviation of the \`X\_train\` data (this is the \`fit\` part).

It then uses these statistics to standardize \`X\_train\` by subtracting the mean and dividing by the standard deviation for each feature (this is the \`transform\` part).

The result is that \`X\_train\` is now a standardized version of the original training data, where each feature has a mean of 0 and a standard deviation of 1.

X\_test = sc.transform(X\_test):

transform: This method uses the mean and standard deviation calculated from the \`X\_train\` data to standardize \`X\_test\`.

This ensures that the test data is transformed in the same way as the training data, which is crucial for the consistency of the model's performance.

X\_test\` is now a standardized version of the original test data, following the same scale as \`X\_train\`.

Here's a bit more detail on why standardization is important:

Consistency: It ensures that the training and test data are on the same scale, which is crucial for the performance of many machine learning models.

Algorithm Performance: Algorithms like gradient descent used in logistic regression or neural networks converge faster with standardized data.

Improved Accuracy: Some algorithms, like support vector machines (SVM) and k-nearest neighbors (KNN), are sensitive to the scale of the data and perform better with standardized data.

By using \`StandardScaler\`, you help ensure that your machine learning model works more effectively and consistently.

# Training the Model

Figure 3-27  illustrates the process of using the X\_train and y\_train datasets to train the machine learning model. The execution of the training process indicates that the model was successfully trained.

![](OEBPS/image_rsrc55J.jpg)

Figure 3-27.

# Code Explanation

The code snippet cs = SVC(kernel='linear', random\_state=0); cs.fit(X\_train, y\_train) is used to create and train a Support Vector Classifier (SVC) with a linear kernel using the scikit-learn library in Python.

cs = SVC(kernel='linear', random\_state=0):

SVC is the class for creating a Support Vector Classifier.

cs is the variable that will store the instance of the SVC.

kernel='linear' specifies that the SVC should use a linear kernel. This means that the decision boundary between classes will be linear.

random\_state=0 is a parameter that ensures reproducibility. It sets the seed for the random number generator, so the results are consistent across multiple runs.

cs.fit(X\_train, y\_train):

fit is a method used to train the model.

X\_train is the training data containing the features (input variables) that the model will learn from.

y\_train is the training data containing the target labels (output variables) that correspond to the features in X\_train.

# Predicting with the test data

Figure 3-28  below illustrates how we made predictions using the trained model (cs) and the test data (X\_test).

![](OEBPS/image_rsrc54R.jpg)

Figure 3-28.

# Code Explanation

The line y\_pred = cs.predict(X\_test) is specifically using a SVM model (cs) to make predictions on a test dataset (X\_test). Here's a detailed explanation tailored to SVM:

cs: This is an instance of a SVM model that has been trained on your training data. In scikit-learn, this could be created using SVC() and then fitted to the training data using cs.fit(X\_train, y\_train).

X\_test: This is the test dataset containing the features for which you want to predict the target variable. These features should be preprocessed similarly to the training data (e.g., standardized).

predict(X\_test): This method is used to predict the class labels for the input data (X\_test) based on the SVM model cs.

y\_pred is an array of predicted class labels for each observation in X\_test. For a binary classification problem, the values in y\_pred will be either 0 or 1.

# Model Evaluation

After training the machine learning model, it is important to evaluate its performance. Let's first examine the confusion matrix before considering the accuracy score as seen in Figure 3-29 .

![](OEBPS/image_rsrc55K.jpg)

Figure 3-29.

# Code Explanation

The line \`cm = confusion\_matrix(y\_test, y\_pred)\` involves using the \`confusion\_matrix\` function from the \`scikit-learn\` library to evaluate the performance of a classification model. Here’s a detailed explanation:

confusion\_matrix(y\_test, y\_pred):

y\_test: This is the array of true class labels for the test dataset. These are the actual values that you are trying to predict.

y\_pred: This is the array of predicted class labels that the model has generated for the test dataset. These predictions are made by the model and are based on the test features (\`X\_test\`).

Confusion Matrix:

The confusion matrix is a table that is often used to describe the performance of a classification model. It shows the number of correct and incorrect predictions made by the model compared to the actual outcomes (ground truth).

It is a 2x2 matrix for binary classification problems, which looks like this:

\[\[TN, FP\],

\[FN, TP\]\]

Where:

TN (True Negative): The number of correctly predicted negative class instances (actual negative and predicted negative).

FP (False Positive): The number of incorrectly predicted positive class instances (actual negative but predicted positive).

FN (False Negative): The number of incorrectly predicted negative class instances (actual positive but predicted negative).

TP (True Positive): The number of correctly predicted positive class instances (actual positive and predicted positive).

# Interpreting the Confusion Matrix

The confusion matrix helps you understand how well your classification model is performing in terms of its ability to predict each class correctly.

It provides detailed insight into the types of errors the model is making:

High values on the diagonal (TN and TP) indicate good performance.

High values off the diagonal (FP and FN) indicate areas where the model is making mistakes.

By examining the confusion matrix, you can gain a deeper understanding of your model's performance beyond what is provided by a single metric like accuracy. This can help you identify specific areas where the model needs improvement.

# Confusion Matrix interpretation

Figure 3-30  shows the confusion matrix from the logistic regression model.

![](OEBPS/image_rsrc55M.jpg)

Figure 3-30.

Let's interpret this confusion matrix:

True Negatives (TN): 74

These are the instances where the actual class was negative (e.g., no heart disease) and the model correctly predicted it as negative.

False Positives (FP): 24

These are the instances where the actual class was negative, but the model incorrectly predicted it as positive (e.g., predicted heart disease when there was actually none).

False Negatives (FN): 6

These are the instances where the actual class was positive (e.g., malignant tumor), but the model incorrectly predicted it as negative (e.g.,predicted no heart disease when there was actually heart disease).

True Positives (TP): 101

These are the instances where the actual class was positive, and the model correctly predicted it as positive.

From this confusion matrix, we can calculate several performance metrics (Accuracy, Precision, Recall, and F1 Score)

Accuracy :

The formula for accuracy is given by:

![](OEBPS/image_rsrc54T.jpg)   

In the provided example:

TN = 74

TP = 101

FP = 24

FN = 6

Plugging these values into the formula:

![](OEBPS/image_rsrc55N.jpg)

This means the model correctly classified approximately 85.4% of the instances.

Precision :

The formula for Precision is given by:

![](OEBPS/image_rsrc54V.jpg)

In the provided example:

TP = 101

FP = 24

Plugging these values into the formula:

![](OEBPS/image_rsrc55P.jpg)

This means that approximately 80.8% of the instances predicted as positive by the model were actually positive.

Recall :

The formula for recall is given by:

![](OEBPS/image_rsrc54X.jpg)

In the provided example:

TP =  101

FN = 6

Plugging these values into the formula:  

![](OEBPS/image_rsrc55R.jpg)

This means that approximately 93.5% of the actual positive instances were correctly identified by the model.

F1 Score:

The formula for F1 Score is given by:

![](OEBPS/image_rsrc54Z.jpg)

In the provided example:

Precision= 0.808

Recall= 0.944

Plugging these values into the formula:

![](OEBPS/image_rsrc55S.jpg)

# Interpretation

Accuracy (85.4%): This indicates that the model correctly predicted 85.4% of the instances.  

Precision (80.8%): Of all the instances predicted as positive, 80.8% were actually positive. This suggests a moderate level of false positives.  

Recall (94.4%): The model correctly identified 94.4% of the actual positive instances. This suggests a high level of false negatives.  

F1 Score (87.0%): This metric combines precision and recall, indicating a good balance between the two.

# Model Evaluation

After training the machine learning model, it is important to evaluate its performance by checking the accuracy score. The accuracy score shows how well the model fits the data it was trained on, as illustrated in Figure 3-31.

![](OEBPS/image_rsrc55T.jpg)

Figure 3-31.

# Code Explanation

The function accuracy\_score(y\_test, y\_pred) from the scikit-learn library is used to calculate the accuracy of a classification model. Here’s a detailed explanation:

Inputs:

y\_test: This is the array of true labels for the test dataset. These labels are the actual values that you are trying to predict.

y\_pred: This is the array of predicted labels that the model has generated for the test dataset. These predictions are based on the test features (X\_test).

# Model Result Interpretation

The output value of 0.8536585365853658 indicates that the SVM model is estimated to have an accuracy of approximately 85.37%.

This means that the model is expected to correctly classify or predict the class labels for about 85.37% of the instances in the dataset.

# Naïve Bayes Model

The Naïve Bayes Model is a widely used machine learning algorithm known for its effectiveness in solving classification problems across various business applications.

The source code is available here: [Naïve Bayes](https://www.google.com/url?q=https://github.com/anyasorc/appliedml/blob/main/Classification_Naive_Bayes.ipynb&sa=D&source=editors&ust=1720099681904460&usg=AOvVaw1J0E1CddrbepIsfw_kJOTx)  

# Import Libraries

Figure 3-32  shows all the imported required libraries

![](OEBPS/image_rsrc55U.jpg)

Figure 3-32.

Import and View Data

Figure 3-33  shows how data was imported and viewed as seen below

![](OEBPS/image_rsrc55V.jpg)

Figure 3-33.

# Assign values to X and y

X = df.iloc\[:, :-1\].values:

This line selects all rows and all columns except the last one from the DataFrame df and converts the result into a NumPy array. The resulting array X typically contains the features or predictors as seen in Figure 3-34 .

y = df.iloc\[:, -1\].values:

This line selects all rows and only the last column from the DataFrame df and converts the result into a NumPy array. The resulting array y typically contains the target or response variable as seen in Figure 3-34 .

![](OEBPS/image_rsrc54K.jpg)

Figure 3-34.

# Splitting into train and test set

We need to split our dataset into training and testing sets. We will use an 80:20 split, where 80% of the data will be used to train the model, and the remaining 20% will be used to test it on unseen data. Figure 3-35  illustrates this process.

![](OEBPS/image_rsrc555.jpg)

Figure 3-35.

# Standardizing the data

In the context of machine learning, particularly when using algorithms that are sensitive to the scale of the input data, it is common to standardize the data. Standardization transforms the data such that it has a mean of zero and a standard deviation of one.  Figure 3-36 illustrates how to implement it.

![](OEBPS/image_rsrc54N.jpg)

Figure 3-36.

# Code Explanation

The code snippet in Figure 3-36  uses the \`StandardScaler\` class from the \`scikit-learn\` library to standardize features by removing the mean and scaling to unit variance. This process is essential for many machine learning algorithms to perform optimally. Here's an explanation of each line:

sc = StandardScaler(): This line creates an instance of the \`StandardScaler\` class. The \`StandardScaler\` is used to standardize the features of the dataset.

X\_train = sc.fit\_transform(X\_train):

fit\_transform: This method first calculates the mean and standard deviation of the \`X\_train\` data (this is the \`fit\` part).

It then uses these statistics to standardize \`X\_train\` by subtracting the mean and dividing by the standard deviation for each feature (this is the \`transform\` part).

The result is that \`X\_train\` is now a standardized version of the original training data, where each feature has a mean of 0 and a standard deviation of 1.

X\_test = sc.transform(X\_test):

transform: This method uses the mean and standard deviation calculated from the \`X\_train\` data to standardize \`X\_test\`.

This ensures that the test data is transformed in the same way as the training data, which is crucial for the consistency of the model's performance.

X\_test\` is now a standardized version of the original test data, following the same scale as \`X\_train\`.

Here's a bit more detail on why standardization is important:

Consistency: It ensures that the training and test data are on the same scale, which is crucial for the performance of many machine learning models.

Algorithm Performance: Algorithms like gradient descent used in logistic regression or neural networks converge faster with standardized data.

Improved Accuracy: Some algorithms, like support vector machines (SVM) and k-nearest neighbors (KNN), are sensitive to the scale of the data and perform better with standardized data.

By using \`StandardScaler\`, you help ensure that your machine learning model works more effectively and consistently.

# Training the Model

Figure 3-37  illustrates the process of using the X\_train and y\_train datasets to train the machine learning model. The execution of the training process indicates that the model was successfully trained.

![](OEBPS/image_rsrc55W.jpg)

Figure 3-37.

# Code Explanation

cs = GaussianNB():

GaussianNB is the class for creating a Gaussian Naive Bayes classifier.

cs is the variable that will store the instance of the Gaussian Naive Bayes classifier.

The Gaussian Naive Bayes classifier assumes that the features follow a Gaussian (normal) distribution.

cs.fit(X\_train, y\_train):

fit is a method used to train the model.

X\_train is the training data containing the features (input variables) that the model will learn from.

y\_train is the training data containing the target labels (output variables) that correspond to the features in X\_train.

During training, the Gaussian Naive Bayes model calculates the mean and variance of each feature for each class, which it uses to make predictions.

# Predicting with the test data

Figure 3-38  below illustrates how we made predictions using the trained model (cs) and the test data (X\_test).

![](OEBPS/image_rsrc557.jpg)

Figure 3-38.

# Code Explanation

The line y\_pred = cs.predict(X\_test) is specifically using a Naive Bayes regression model (cs) to make predictions on a test dataset (X\_test). Here's a detailed explanation tailored to Naive Bayes model:

cs: This is an instance of a Naive Bayes model that has been trained on your training data. In scikit-learn, this could be created using GaussianNB() and then fitted to the training data using cs.fit(X\_train, y\_train).

X\_test: This is the test dataset containing the features for which you want to predict the target variable. These features should be preprocessed similarly to the training data (e.g., standardized).

predict(X\_test): This method is used to predict the class labels for the input data (X\_test) based on the Naive Bayes model cs.

y\_pred is an array of predicted class labels for each observation in X\_test. For a binary classification problem, the values in y\_pred will be either 0 or 1.

# Model Evaluation

After training the machine learning model, it is important to evaluate its performance. Let's first examine the confusion matrix before considering the accuracy score as seen in Figure 3-39 .

![](OEBPS/image_rsrc55X.jpg)

Figure 3-39

# Code Explanation

The line \`cm = confusion\_matrix(y\_test, y\_pred)\` involves using the \`confusion\_matrix\` function from the \`scikit-learn\` library to evaluate the performance of a classification model. Here’s a detailed explanation:

confusion\_matrix(y\_test, y\_pred):

y\_test: This is the array of true class labels for the test dataset. These are the actual values that you are trying to predict.

y\_pred: This is the array of predicted class labels that the model has generated for the test dataset. These predictions are made by the model and are based on the test features (\`X\_test\`).

Confusion Matrix:

The confusion matrix is a table that is often used to describe the performance of a classification model. It shows the number of correct and incorrect predictions made by the model compared to the actual outcomes (ground truth).

It is a 2x2 matrix for binary classification problems, which looks like this:

\[\[TN, FP\],

\[FN, TP\]\]

Where:

TN (True Negative): The number of correctly predicted negative class instances (actual negative and predicted negative).

FP (False Positive): The number of incorrectly predicted positive class instances (actual negative but predicted positive).

FN (False Negative): The number of incorrectly predicted negative class instances (actual positive but predicted negative).

TP (True Positive): The number of correctly predicted positive class instances (actual positive and predicted positive).

# Interpreting the Confusion Matrix

The confusion matrix helps you understand how well your classification model is performing in terms of its ability to predict each class correctly.

It provides detailed insight into the types of errors the model is making:

High values on the diagonal (TN and TP) indicate good performance.

High values off the diagonal (FP and FN) indicate areas where the model is making mistakes.

By examining the confusion matrix, you can gain a deeper understanding of your model's performance beyond what is provided by a single metric like accuracy. This can help you identify specific areas where the model needs improvement.

# Confusion Matrix interpretation

Figure 3-40  shows the confusion matrix from the logistic regression model.

![](OEBPS/image_rsrc55Y.jpg)

Figure 3-40.

Let's interpret this confusion matrix:

True Negatives (TN): 79

These are the instances where the actual class was negative (e.g., no heart disease) and the model correctly predicted it as negative.

False Positives (FP): 19

These are the instances where the actual class was negative, but the model incorrectly predicted it as positive (e.g., predicted heart disease when there was actually none).

False Negatives (FN): 11

These are the instances where the actual class was positive (e.g., malignant tumor), but the model incorrectly predicted it as negative (e.g., predicted no heart disease when there was actually heart disease).

True Positives (TP): 96

These are the instances where the actual class was positive, and the model correctly predicted it as positive.

From this confusion matrix, we can calculate several performance metrics (Accuracy, Precision, Recall, and F1 Score)

Accuracy :

The formula for accuracy is given by:

![](OEBPS/image_rsrc54T.jpg)   

In the provided example:

TN = 74

TP = 96

FP = 19

FN = 11

Plugging these values into the formula:

![](OEBPS/image_rsrc55Z.jpg)

This means the model correctly classified approximately 86.3% of the instances.

Precision :

The formula for Precision is given by:

![](OEBPS/image_rsrc54V.jpg)

In the provided example:

TP = 96

FP = 19

Plugging these values into the formula:

![](OEBPS/image_rsrc560.jpg)

This means that approximately 82.6% of the instances predicted as positive by the model were actually positive.

Recall :

The formula for recall is given by:

![](OEBPS/image_rsrc54X.jpg)

In the provided example:

TP =  96

FN = 11

Plugging these values into the formula:  

![](OEBPS/image_rsrc561.jpg)

This means that approximately 93.5% of the actual positive instances were correctly identified by the model.

F1 Score:

The formula for F1 Score is given by:

![](OEBPS/image_rsrc54Z.jpg)

In the provided example:

Precision=0.8348

Recall=0.8972

Plugging these values into the formula:

![](OEBPS/image_rsrc562.jpg)

# Interpretation

Accuracy (85.37%) : Indicates that the model correctly predicted 85.37% of the instances, reflecting a high overall correctness in its predictions.

Precision (83.48%) : Of all the instances predicted as positive, 83.48% were actually positive. This indicates a relatively low level of false positives, highlighting the model's reliability in making positive predictions.

Recall (89.72%) : The model correctly identified 89.72% of the actual positive instances. This suggests a relatively low level of false negatives, indicating that the model effectively captures the majority of positive instances.

F1 Score (86.50%) : Combines precision and recall into a single metric, providing a balanced assessment of the model's performance. The F1 Score of 86.50% suggests a good balance between precision and recall, indicating the model's effectiveness in classifying instances into their respective classes.

# Model Evaluation

After training the machine learning model, it is important to evaluate its performance by checking the accuracy score. The accuracy score shows how well the model fits the data it was trained on, as illustrated in Figure 3-40.

![](OEBPS/image_rsrc563.jpg)

Figure 3-40.

# Code Explanation

The function accuracy\_score(y\_test, y\_pred) from the scikit-learn library is used to calculate the accuracy of a classification model. Here’s a detailed explanation:

Inputs:

y\_test: This is the array of true labels for the test dataset. These labels are the actual values that you are trying to predict.

y\_pred: This is the array of predicted labels that the model has generated for the test dataset. These predictions are based on the test features (X\_test).

# Model Result Interpretation

The accuracy score of 0.8536585365853658 means that the model correctly predicted the class labels for approximately 85.37%  of the instances in the dataset.

This indicates that out of all the predictions made by the model, about 85.37% were correct.

# Kernel SVM Model

A Support Vector Machine (SVM) is a supervised learning algorithm used for classification and regression tasks.

The source code is available here: [Kernel SVM](https://www.google.com/url?q=https://github.com/anyasorc/appliedml/blob/main/Classification_KernelSVM.ipynb&sa=D&source=editors&ust=1720099681930305&usg=AOvVaw15Y1UPa3yWWLcLQoQ4JQYk)  

# Import Libraries

Figure 3-41  shows all the imported required libraries

![](OEBPS/image_rsrc564.jpg)

Figure 3-41.

# Import and View Data

Figure 3-42  shows how data was imported and viewed as seen below

![](OEBPS/image_rsrc565.jpg)

Figure 3-42.

# Assign values to X and y

X = df.iloc\[:, :-1\].values:

This line selects all rows and all columns except the last one from the DataFrame df and converts the result into a NumPy array. The resulting array X typically contains the features or predictors as seen in Figure 3-43 .

y = df.iloc\[:, -1\].values:

This line selects all rows and only the last column from the DataFrame df and converts the result into a NumPy array. The resulting array y typically contains the target or response variable as seen in Figure 3-43 .

![](OEBPS/image_rsrc54K.jpg)

Figure 3-43.

# Splitting into train and test set

We need to split our dataset into training and testing sets. We will use an 80:20 split, where 80% of the data will be used to train the model, and the remaining 20% will be used to test it on unseen data. Figure 3-44  illustrates this process.

![](OEBPS/image_rsrc555.jpg)

Figure 3-44.

# Standardizing the data

In the context of machine learning, particularly when using algorithms that are sensitive to the scale of the input data, it is common to standardize the data. Standardization transforms the data such that it has a mean of zero and a standard deviation of one.  Figure 3-45 illustrates how to implement it.

![](OEBPS/image_rsrc54N.jpg)

Figure 3-45.

# Code Explanation

The code snippet in Figure 3-45 uses the \`StandardScaler\` class from the \`scikit-learn\` library to standardize features by removing the mean and scaling to unit variance. This process is essential for many machine learning algorithms to perform optimally. Here's an explanation of each line:

sc = StandardScaler(): This line creates an instance of the \`StandardScaler\` class. The \`StandardScaler\` is used to standardize the features of the dataset.

X\_train = sc.fit\_transform(X\_train):

fit\_transform: This method first calculates the mean and standard deviation of the \`X\_train\` data (this is the \`fit\` part).

It then uses these statistics to standardize \`X\_train\` by subtracting the mean and dividing by the standard deviation for each feature (this is the \`transform\` part).

The result is that \`X\_train\` is now a standardized version of the original training data, where each feature has a mean of 0 and a standard deviation of 1.

X\_test = sc.transform(X\_test):

transform: This method uses the mean and standard deviation calculated from the \`X\_train\` data to standardize \`X\_test\`.

This ensures that the test data is transformed in the same way as the training data, which is crucial for the consistency of the model's performance.

X\_test\` is now a standardized version of the original test data, following the same scale as \`X\_train\`.

Here's a bit more detail on why standardization is important:

Consistency: It ensures that the training and test data are on the same scale, which is crucial for the performance of many machine learning models.

Algorithm Performance: Algorithms like gradient descent used in logistic regression or neural networks converge faster with standardized data.

Improved Accuracy: Some algorithms, like support vector machines (SVM) and k-nearest neighbors (KNN), are sensitive to the scale of the data and perform better with standardized data.

By using \`StandardScaler\`, you help ensure that your machine learning model works more effectively and consistently.

# Training the Model

Figure 3-46  illustrates the process of using the X\_train and y\_train datasets to train the machine learning model. The execution of the training process indicates that the model was successfully trained.

![](OEBPS/image_rsrc566.jpg)

Figure 3-46.

# Code Explanation

cs = SVC(kernel='rbf', random\_state=0) initializes a Support Vector Classifier with an RBF kernel.

The RBF kernel allows the classifier to create a non-linear decision boundary, which can be more effective for complex datasets where the classes are not linearly separable.

cs.fit(X\_train, y\_train) trains the SVC using the training data (X\_train) and the corresponding labels (y\_train).

During this process, the SVC learns the parameters of the RBF kernel and identifies the support vectors that define the optimal hyperplane in the transformed feature space.

The trained model can then be used to make predictions on new, unseen data.

# Predicting with the test data

Figure 3-47  below illustrates how we made predictions using the trained model (cs) and the test data (X\_test).

![](OEBPS/image_rsrc557.jpg)

Figure 3-47.

# Code Explanation

The line y\_pred = cs.predict(X\_test) is specifically using a Kernel SVM model (cs) to make predictions on a test dataset (X\_test). Here's a detailed explanation tailored to Kernel SVM model:

cs: This is an instance of a Kernel SVM model that has been trained on your training data. In scikit-learn, this could be created using SVC() and then fitted to the training data using cs.fit(X\_train, y\_train).

X\_test: This is the test dataset containing the features for which you want to predict the target variable. These features should be preprocessed similarly to the training data (e.g., standardized).

predict(X\_test): This method is used to predict the class labels for the input data (X\_test) based on the Kernel SVM model cs.

y\_pred is an array of predicted class labels for each observation in X\_test. For a binary classification problem, the values in y\_pred will be either 0 or 1.

# Model Evaluation

After training the machine learning model, it is important to evaluate its performance. Let's first examine the confusion matrix before considering the accuracy score as seen in Figure 3-48 .

![](OEBPS/image_rsrc567.jpg)

Figure 3-48.

# Code Explanation

The line \`cm = confusion\_matrix(y\_test, y\_pred)\` involves using the \`confusion\_matrix\` function from the \`scikit-learn\` library to evaluate the performance of a classification model. Here’s a detailed explanation:

confusion\_matrix(y\_test, y\_pred):

y\_test: This is the array of true class labels for the test dataset. These are the actual values that you are trying to predict.

y\_pred: This is the array of predicted class labels that the model has generated for the test dataset. These predictions are made by the model and are based on the test features (\`X\_test\`).

Confusion Matrix:

The confusion matrix is a table that is often used to describe the performance of a classification model. It shows the number of correct and incorrect predictions made by the model compared to the actual outcomes (ground truth).

It is a 2x2 matrix for binary classification problems, which looks like this:

\[\[TN, FP\],

\[FN, TP\]\]

Where:

TN (True Negative): The number of correctly predicted negative class instances (actual negative and predicted negative).

FP (False Positive): The number of incorrectly predicted positive class instances (actual negative but predicted positive).

FN (False Negative): The number of incorrectly predicted negative class instances (actual positive but predicted negative).

TP (True Positive): The number of correctly predicted positive class instances (actual positive and predicted positive).

# Interpreting the Confusion Matrix

The confusion matrix helps you understand how well your classification model is performing in terms of its ability to predict each class correctly.

It provides detailed insight into the types of errors the model is making:

High values on the diagonal (TN and TP) indicate good performance.

High values off the diagonal (FP and FN) indicate areas where the model is making mistakes.

By examining the confusion matrix, you can gain a deeper understanding of your model's performance beyond what is provided by a single metric like accuracy. This can help you identify specific areas where the model needs improvement.

# Confusion Matrix interpretation

Figure 3-49  shows the confusion matrix from the logistic regression model.

![](OEBPS/image_rsrc568.jpg)

Figure 3-49.

Let's interpret this confusion matrix:

True Negatives (TN): 92

These are the instances where the actual class was negative (e.g., no heart disease) and the model correctly predicted it as negative.

False Positives (FP): 6

These are the instances where the actual class was negative, but the model incorrectly predicted it as positive (e.g., predicted heart disease when there was actually none).

False Negatives (FN): 1

These are the instances where the actual class was positive (e.g., malignant tumor), but the model incorrectly predicted it as negative (e.g., predicted no heart disease when there was actually heart disease).

True Positives (TP): 106

These are the instances where the actual class was positive, and the model correctly predicted it as positive.

From this confusion matrix, we can calculate several performance metrics (Accuracy, Precision, Recall, and F1 Score)

Accuracy :

The formula for accuracy is given by:

![](OEBPS/image_rsrc54T.jpg)   

In the provided example:

TN = 92

TP = 106

FP = 6

FN = 1

Plugging these values into the formula:

![](OEBPS/image_rsrc569.jpg)

This means the model correctly classified approximately 86.3% of the instances.

Precision :

The formula for Precision is given by:

![](OEBPS/image_rsrc54V.jpg)

In the provided example:

TP = 106

FP = 6

Plugging these values into the formula:

![](OEBPS/image_rsrc56A.jpg)

This means that approximately 82.6% of the instances predicted as positive by the model were actually positive.

Recall :

The formula for recall is given by:

![](OEBPS/image_rsrc54X.jpg)

In the provided example:

TP =  106

FN = 1

Plugging these values into the formula:  

![](OEBPS/image_rsrc56B.jpg)

This means that approximately 93.5% of the actual positive instances were correctly identified by the model.

F1 Score:

The formula for F1 Score is given by:

![](OEBPS/image_rsrc54Z.jpg)

In the provided example:

Precision=0.9464

Recall=0.9907

Plugging these values into the formula:

![](OEBPS/image_rsrc56C.jpg)

# Interpretation

Accuracy (96.59%) : Indicates that the model correctly predicted 96.59% of the instances, reflecting a high overall correctness in its predictions.

Precision (94.64%) : Of all the instances predicted as positive, 94.64% were actually positive. This indicates a very low level of false positives, highlighting the model's high reliability in making positive predictions.

Recall (99.07%) : The model correctly identified 99.07% of the actual positive instances. This suggests a very low level of false negatives, indicating that the model effectively captures the vast majority of positive instances.

F1 Score (96.80%) : Combines precision and recall into a single metric, providing a balanced assessment of the model's performance. The F1 Score of 96.80% suggests a high level of performance in balancing precision and recall, indicating the model's effectiveness in classifying instances into their respective classes.

# Model Evaluation

After training the machine learning model, it is important to evaluate its performance by checking the accuracy score. The accuracy score shows how well the model fits the data it was trained on, as illustrated in Figure 3-50.

![](OEBPS/image_rsrc56D.jpg)

Figure 3-50.

# Code Explanation

The function accuracy\_score(y\_test, y\_pred) from the scikit-learn library is used to calculate the accuracy of a classification model. Here’s a detailed explanation:

Inputs:

y\_test: This is the array of true labels for the test dataset. These labels are the actual values that you are trying to predict.

y\_pred: This is the array of predicted labels that the model has generated for the test dataset. These predictions are based on the test features (X\_test).

# Model Result Interpretation

The accuracy score of 0.9658536585365853 means that the model correctly predicted the class labels for approximately 96.59%  of the instances in the dataset.

This indicates that out of all the predictions made by the model, about 96.59% were correct

# Decision Tree Classification Model

A Decision Tree is a robust supervised machine learning algorithm capable of handling both classification and regression tasks effectively. It functions by dividing the dataset into subsets based on specific features, aiming to construct a tree-like structure comprising decision nodes and leaf nodes. At each decision node, the algorithm assesses a feature and determines the optimal split to either maximize information gain or minimize impurity. This recursive process continues until the data is appropriately segmented or a predefined stopping criterion is satisfied.

Decision Trees are favored for their simplicity, interpretability, and versatility in handling both numerical and categorical data. They find widespread application across diverse domains such as finance, healthcare, marketing, and more. Typical uses include customer segmentation, risk assessment, and predictive modeling, making Decision Trees a valuable tool in data-driven decision-making processes.

The source code is available here: [Decision Tree Classification](https://www.google.com/url?q=https://github.com/anyasorc/appliedml/blob/main/Classification_DecisionTree.ipynb&sa=D&source=editors&ust=1720099681951804&usg=AOvVaw1jUlR3t_ElIjiug6Ky6kuw)  

# Import Libraries

Figure 3-51  shows all the imported required libraries

![](OEBPS/image_rsrc56E.jpg)

Figure 3-51.

# Import and View Data

Figure 3-52  shows how data was imported and viewed as seen below

![](OEBPS/image_rsrc56F.jpg)

Figure 3-52.

# Assign values to X and y

X = df.iloc\[:, :-1\].values:

This line selects all rows and all columns except the last one from the DataFrame df and converts the result into a NumPy array. The resulting array X typically contains the features or predictors as seen in Figure 3-52 .

y = df.iloc\[:, -1\].values:

This line selects all rows and only the last column from the DataFrame df and converts the result into a NumPy array. The resulting array y typically contains the target or response variable as seen in Figure 3-52 .

![](OEBPS/image_rsrc54K.jpg)

Figure 3-52.

# Splitting into train and test set

We need to split our dataset into training and testing sets. We will use an 80:20 split, where 80% of the data will be used to train the model, and the remaining 20% will be used to test it on unseen data. Figure 3-53  illustrates this process.

![](OEBPS/image_rsrc555.jpg)

Figure 3-53.

# Standardizing the data

In the context of machine learning, particularly when using algorithms that are sensitive to the scale of the input data, it is common to standardize the data. Standardization transforms the data such that it has a mean of zero and a standard deviation of one.  Figure 3-54 illustrates how to implement it.

![](OEBPS/image_rsrc54N.jpg)

Figure 3-54.

# Code Explanation

The code snippet in Figure 3-54 uses the \`StandardScaler\` class from the \`scikit-learn\` library to standardize features by removing the mean and scaling to unit variance. This process is essential for many machine learning algorithms to perform optimally. Here's an explanation of each line:

sc = StandardScaler(): This line creates an instance of the \`StandardScaler\` class. The \`StandardScaler\` is used to standardize the features of the dataset.

X\_train = sc.fit\_transform(X\_train):

fit\_transform: This method first calculates the mean and standard deviation of the \`X\_train\` data (this is the \`fit\` part).

It then uses these statistics to standardize \`X\_train\` by subtracting the mean and dividing by the standard deviation for each feature (this is the \`transform\` part).

The result is that \`X\_train\` is now a standardized version of the original training data, where each feature has a mean of 0 and a standard deviation of 1.

X\_test = sc.transform(X\_test):

transform: This method uses the mean and standard deviation calculated from the \`X\_train\` data to standardize \`X\_test\`.

This ensures that the test data is transformed in the same way as the training data, which is crucial for the consistency of the model's performance.

X\_test\` is now a standardized version of the original test data, following the same scale as \`X\_train\`.

Here's a bit more detail on why standardization is important:

Consistency: It ensures that the training and test data are on the same scale, which is crucial for the performance of many machine learning models.

Algorithm Performance: Algorithms like gradient descent used in logistic regression or neural networks converge faster with standardized data.

Improved Accuracy: Some algorithms, like support vector machines (SVM) and k-nearest neighbors (KNN), are sensitive to the scale of the data and perform better with standardized data.

By using \`StandardScaler\`, you help ensure that your machine learning model works more effectively and consistently.

# Training the Model

Figure 3-55  illustrates the process of using the X\_train and y\_train datasets to train the machine learning model. The execution of the training process indicates that the model was successfully trained.

![](OEBPS/image_rsrc56G.jpg)

Figure 3-55.

# Code Explanation

Referring to the code snippet in Figure 3-55,

This line of code initializes a DecisionTreeClassifier object named cs  with specific parameters:

criterion='entropy' : This parameter specifies the criterion used for making decisions in the tree. 'Entropy' is a measure of impurity in the context of decision trees. The algorithm will use entropy to decide the best split at each node, aiming to minimize entropy and maximize information gain.

random\_state=0 : This parameter sets the random seed for reproducibility of results. When the same seed (here, 0) is used, the results will be the same each time you run the model. This ensures consistency in the model's performance and outputs across different runs.

cs.fit(X\_train, y\_train):

fit is a method used to train the model.

X\_train is the training data containing the features (input variables) that the model will learn from.

y\_train is the training data containing the target labels (output variables) that correspond to the features in X\_train

# Predicting with the test data

Figure 3-56  below illustrates how we made predictions using the trained model (cs) and the test data (X\_test).

![](OEBPS/image_rsrc557.jpg)

Figure 3-56.

# Code Explanation

he line y\_pred = cs.predict(X\_test) is specifically using a DecisionTreeClassifier model (cs) to make predictions on a test dataset (X\_test). Here's a detailed explanation tailored to DecisionTreeClassifier model:

cs: This is an instance of a DecisionTreeClassifier regression model that has been trained on your training data. In scikit-learn, this could be created using DecisionTreeClassifier() and then fitted to the training data using cs.fit(X\_train, y\_train).

X\_test: This is the test dataset containing the features for which you want to predict the target variable. These features should be preprocessed similarly to the training data (e.g., standardized).

predict(X\_test): This method is used to predict the class labels for the input data (X\_test) based on the DecisionTreeClassifier model cs.

y\_pred is an array of predicted class labels for each observation in X\_test. For a binary classification problem, the values in y\_pred will be either 0 or 1.

# Model Evaluation

After training the machine learning model, it is important to evaluate its performance. Let's first examine the confusion matrix before considering the accuracy score as seen in Figure 3-57 .

![](OEBPS/image_rsrc56H.jpg)

Figure 3-57.

# Code Explanation

The line \`cm = confusion\_matrix(y\_test, y\_pred)\` involves using the \`confusion\_matrix\` function from the \`scikit-learn\` library to evaluate the performance of a classification model. Here’s a detailed explanation:

confusion\_matrix(y\_test, y\_pred):

\- y\_test: This is the array of true class labels for the test dataset. These are the actual values that you are trying to predict.

\- y\_pred: This is the array of predicted class labels that the model has generated for the test dataset. These predictions are made by the model and are based on the test features (\`X\_test\`).

Confusion Matrix:

\- The confusion matrix is a table that is often used to describe the performance of a classification model. It shows the number of correct and incorrect predictions made by the model compared to the actual outcomes (ground truth).

\- It is a 2x2 matrix for binary classification problems, which looks like this:

\[\[TN, FP\],

\[FN, TP\]\]

Where:

TN (True Negative): The number of correctly predicted negative class instances (actual negative and predicted negative).

FP (False Positive): The number of incorrectly predicted positive class instances (actual negative but predicted positive).

FN (False Negative): The number of incorrectly predicted negative class instances (actual positive but predicted negative).

TP (True Positive): The number of correctly predicted positive class instances (actual positive and predicted positive).

# Interpreting the Confusion Matrix

The confusion matrix helps you understand how well your classification model is performing in terms of its ability to predict each class correctly.

It provides detailed insight into the types of errors the model is making:

High values on the diagonal (TN and TP) indicate good performance.

High values off the diagonal (FP and FN) indicate areas where the model is making mistakes.

By examining the confusion matrix, you can gain a deeper understanding of your model's performance beyond what is provided by a single metric like accuracy. This can help you identify specific areas where the model needs improvement.

# Confusion Matrix interpretation

Figure 3-58  shows the confusion matrix from the logistic regression model.

![](OEBPS/image_rsrc56J.jpg)

Figure 3-58.

Let's interpret this confusion matrix:

True Negatives (TN): 98

These are the instances where the actual class was negative (e.g., no heart disease) and the model correctly predicted it as negative.

False Positives (FP): 0

These are the instances where the actual class was negative, but the model incorrectly predicted it as positive (e.g., predicted heart disease when there was actually none).

False Negatives (FN): 0

These are the instances where the actual class was positive (e.g., malignant tumor), but the model incorrectly predicted it as negative (e.g., predicted no heart disease when there was actually heart disease).

True Positives (TP): 107

These are the instances where the actual class was positive, and the model correctly predicted it as positive.

From this confusion matrix, we can calculate several performance metrics (Accuracy, Precision, Recall, and F1 Score)

Accuracy :

The formula for accuracy is given by:

![](OEBPS/image_rsrc54T.jpg)   

In the provided example:

TN = 98

TP = 107

FP = 0

FN = 0

Plugging these values into the formula:

![](OEBPS/image_rsrc56K.jpg)

This means the model correctly classified approximately 86.3% of the instances.

Precision :

The formula for Precision is given by:

![](OEBPS/image_rsrc54V.jpg)

In the provided example:

TP = 107

FP = 0

Plugging these values into the formula:

![](OEBPS/image_rsrc56M.jpg)

This means that approximately 82.6% of the instances predicted as positive by the model were actually positive.

Recall :

The formula for recall is given by:

![](OEBPS/image_rsrc54X.jpg)

In the provided example:

TP =  107

FN = 0

Plugging these values into the formula:  

![](OEBPS/image_rsrc56N.jpg)

This means that approximately 93.5% of the actual positive instances were correctly identified by the model.

F1 Score:

The formula for F1 Score is given by:

![](OEBPS/image_rsrc54Z.jpg)

In the provided example:

Precision=1.0

Recall=1.0

Plugging these values into the formula:

![](OEBPS/image_rsrc56P.jpg)

# Interpretation

Accuracy (100%) : Indicates that the model correctly predicted 100% of the instances, reflecting perfect overall correctness in its predictions.

Precision (100%) : Of all the instances predicted as positive, 100% were actually positive. This indicates no false positives, highlighting the model's perfect reliability in making positive predictions.

Recall (100%) : The model correctly identified 100% of the actual positive instances. This suggests no false negatives, indicating that the model effectively captures all positive instances.

F1 Score (100%) : Combines precision and recall into a single metric, providing a balanced assessment of the model's performance. The F1 Score of 100% suggests a perfect balance between precision and recall, indicating the model's flawless effectiveness in classifying instances into their respective classes.

# Model Evaluation

After training the machine learning model, it is important to evaluate its performance by checking the accuracy score. The accuracy score shows how well the model fits the data it was trained on, as illustrated in Figure 3-58.

![](OEBPS/image_rsrc56R.jpg)

Figure 3-58.

# Code Explanation

The function accuracy\_score(y\_test, y\_pred) from the scikit-learn library is used to calculate the accuracy of a classification model. Here’s a detailed explanation:

Inputs:

y\_test: This is the array of true labels for the test dataset. These labels are the actual values that you are trying to predict.

y\_pred: This is the array of predicted labels that the model has generated for the test dataset. These predictions are based on the test features (X\_test).

# Model Result Interpretation

Accuracy (100%): A model accuracy score of 100%  indicates that the model made perfect predictions on the dataset. It correctly classified all instances without any errors, achieving the highest level of accuracy possible.

This implies that the model is highly reliable and effective in its task, as it successfully captured all patterns present in the data.

# Random Forest Classification Model

A Random Forest is a type of ensemble learning method that combines the predictions of multiple decision trees to enhance the overall performance and generalization of the model. It can be applied to both classification and regression tasks.

The source code is available here: [Random Forest Classification](https://www.google.com/url?q=https://github.com/anyasorc/appliedml/blob/main/Classification_RandomForest.ipynb&sa=D&source=editors&ust=1720099681982514&usg=AOvVaw2oZc2qjLhRWr9NsCt5PYlQ)  

# Import Libraries

Figure 3-59  shows all the imported required libraries

![](OEBPS/image_rsrc56S.jpg)

Figure 3-59.

# Import and View Data

Figure 3-60  shows how data was imported and viewed as seen below

![](OEBPS/image_rsrc56T.jpg)

Figure 3-60

Assign values to X and y

X = df.iloc\[:, :-1\].values:

This line selects all rows and all columns except the last one from the DataFrame df and converts the result into a NumPy array. The resulting array X typically contains the features or predictors as seen in Figure 3-61 .

y = df.iloc\[:, -1\].values:

This line selects all rows and only the last column from the DataFrame df and converts the result into a NumPy array. The resulting array y typically contains the target or response variable as seen in Figure 3-61 .

![](OEBPS/image_rsrc54K.jpg)

Figure 3-61.

# Splitting into train and test set

We need to split our dataset into training and testing sets. We will use an 80:20 split, where 80% of the data will be used to train the model, and the remaining 20% will be used to test it on unseen data. Figure 3-62  illustrates this process.

![](OEBPS/image_rsrc555.jpg)

Figure 3-62.

# Standardizing the data

In the context of machine learning, particularly when using algorithms that are sensitive to the scale of the input data, it is common to standardize the data. Standardization transforms the data such that it has a mean of zero and a standard deviation of one.  Figure 3-63 illustrates how to implement it.

![](OEBPS/image_rsrc54N.jpg)

Figure 3-63.

# Code Explanation

The code snippet in Figure 3-63 uses the \`StandardScaler\` class from the \`scikit-learn\` library to standardize features by removing the mean and scaling to unit variance. This process is essential for many machine learning algorithms to perform optimally. Here's an explanation of each line:

sc = StandardScaler(): This line creates an instance of the \`StandardScaler\` class. The \`StandardScaler\` is used to standardize the features of the dataset.

X\_train = sc.fit\_transform(X\_train):

fit\_transform: This method first calculates the mean and standard deviation of the \`X\_train\` data (this is the \`fit\` part).

It then uses these statistics to standardize \`X\_train\` by subtracting the mean and dividing by the standard deviation for each feature (this is the \`transform\` part).

The result is that \`X\_train\` is now a standardized version of the original training data, where each feature has a mean of 0 and a standard deviation of 1.

X\_test = sc.transform(X\_test):

transform: This method uses the mean and standard deviation calculated from the \`X\_train\` data to standardize \`X\_test\`.

This ensures that the test data is transformed in the same way as the training data, which is crucial for the consistency of the model's performance.

X\_test\` is now a standardized version of the original test data, following the same scale as \`X\_train\`.

Here's a bit more detail on why standardization is important:

Consistency: It ensures that the training and test data are on the same scale, which is crucial for the performance of many machine learning models.

Algorithm Performance: Algorithms like gradient descent used in logistic regression or neural networks converge faster with standardized data.

Improved Accuracy: Some algorithms, like support vector machines (SVM) and k-nearest neighbors (KNN), are sensitive to the scale of the data and perform better with standardized data.

By using \`StandardScaler\`, you help ensure that your machine learning model works more effectively and consistently.

# Training the Model

Figure 3-64  illustrates the process of using the X\_train and y\_train datasets to train the machine learning model. The execution of the training process indicates that the model was successfully trained.

![](OEBPS/image_rsrc56U.jpg)

Figure 3-64.

# Code Explanation

RandomForestClassifier(n\_estimators=10, criterion='entropy', random\_state=0):

This line initializes a Random Forest Classifier object.

n\_estimators=10: Specifies the number of decision trees in the random forest. In this case, the random forest will consist of 10 decision trees.

criterion='entropy': Defines the criterion used for splitting nodes. Entropy is a measure of impurity in a group of samples. The decision tree algorithm will use entropy to determine the best split at each node.

random\_state=0: Sets the random seed to ensure reproducibility of results. With the same random seed, the random forest will produce the same results when trained on the same data.

cs.fit(X\_train, y\_train):

This line trains the Random Forest Classifier on the training data (X\_train and y\_train).

X\_train: Represents the feature matrix containing the input features used to train the model.

y\_train: Represents the target vector containing the corresponding labels for the training data.

# Predicting with the test data

Figure 3-65  below illustrates how we made predictions using the trained model (cs) and the test data (X\_test).

![](OEBPS/image_rsrc557.jpg)

Figure 3-65.

# Code Explanation

The line y\_pred = cs.predict(X\_test) is specifically using a Random Forest model (cs) to make predictions on a test dataset (X\_test). Here's a detailed explanation tailored to RandomForestClassifier model:

cs: This is an instance of a RandomForestClassifier model that has been trained on your training data. In scikit-learn, this could be created using RandomForestClassifier() and then fitted to the training data using cs.fit(X\_train, y\_train).

X\_test: This is the test dataset containing the features for which you want to predict the target variable. These features should be preprocessed similarly to the training data (e.g., standardized).

predict(X\_test): This method is used to predict the class labels for the input data (X\_test) based on the random forest model cs.

y\_pred is an array of predicted class labels for each observation in X\_test. For a binary classification problem, the values in y\_pred will be either 0 or 1.

# Model Evaluation

After training the machine learning model, it is important to evaluate its performance. Let's first examine the confusion matrix before considering the accuracy score as seen in Figure 3-66 .

![](OEBPS/image_rsrc56V.jpg)

Figure 3-66.

# Code Explanation

The line \`cm = confusion\_matrix(y\_test, y\_pred)\` involves using the \`confusion\_matrix\` function from the \`scikit-learn\` library to evaluate the performance of a classification model. Here’s a detailed explanation:

confusion\_matrix(y\_test, y\_pred):

y\_test: This is the array of true class labels for the test dataset. These are the actual values that you are trying to predict.

y\_pred: This is the array of predicted class labels that the model has generated for the test dataset. These predictions are made by the model and are based on the test features (\`X\_test\`).

Confusion Matrix:

The confusion matrix is a table that is often used to describe the performance of a classification model. It shows the number of correct and incorrect predictions made by the model compared to the actual outcomes (ground truth).

It is a 2x2 matrix for binary classification problems, which looks like this:

\[\[TN, FP\],

\[FN, TP\]\]

Where:

TN (True Negative): The number of correctly predicted negative class instances (actual negative and predicted negative).

FP (False Positive): The number of incorrectly predicted positive class instances (actual negative but predicted positive).

FN (False Negative): The number of incorrectly predicted negative class instances (actual positive but predicted negative).

TP (True Positive): The number of correctly predicted positive class instances (actual positive and predicted positive).

# Interpreting the Confusion Matrix

The confusion matrix helps you understand how well your classification model is performing in terms of its ability to predict each class correctly.

It provides detailed insight into the types of errors the model is making:

High values on the diagonal (TN and TP) indicate good performance.

High values off the diagonal (FP and FN) indicate areas where the model is making mistakes.

By examining the confusion matrix, you can gain a deeper understanding of your model's performance beyond what is provided by a single metric like accuracy. This can help you identify specific areas where the model needs improvement.

# Confusion Matrix interpretation

Figure 3-67  shows the confusion matrix from the logistic regression model.

![](OEBPS/image_rsrc56W.jpg)

Figure 3-67.

Let's interpret this confusion matrix:

True Negatives (TN): 98

These are the instances where the actual class was negative (e.g., no heart disease) and the model correctly predicted it as negative.

False Positives (FP): 0

These are the instances where the actual class was negative, but the model incorrectly predicted it as positive (e.g., predicted heart disease when there was actually none).

False Negatives (FN): 0

These are the instances where the actual class was positive (e.g., malignant tumor), but the model incorrectly predicted it as negative (e.g., predicted no heart disease when there was actually heart disease).

True Positives (TP): 107

These are the instances where the actual class was positive, and the model correctly predicted it as positive.

From this confusion matrix, we can calculate several performance metrics (Accuracy, Precision, Recall, and F1 Score)

Accuracy :

The formula for accuracy is given by:

![](OEBPS/image_rsrc54T.jpg)   

In the provided example:

TN = 98

TP = 107

FP = 0

FN = 0

Plugging these values into the formula:

![](OEBPS/image_rsrc56K.jpg)

This means the model correctly classified approximately 86.3% of the instances.

Precision :

The formula for Precision is given by:

![](OEBPS/image_rsrc54V.jpg)

In the provided example:

TP = 107

FP = 0

Plugging these values into the formula:

![](OEBPS/image_rsrc56M.jpg)

This means that approximately 82.6% of the instances predicted as positive by the model were actually positive.

Recall :

The formula for recall is given by:

![](OEBPS/image_rsrc54X.jpg)

In the provided example:

TP =  107

FN = 0

Plugging these values into the formula:  

![](OEBPS/image_rsrc56N.jpg)

This means that approximately 93.5% of the actual positive instances were correctly identified by the model.

F1 Score:

The formula for F1 Score is given by:

![](OEBPS/image_rsrc54Z.jpg)

In the provided example:

Precision=1.0

Recall=1.0

Plugging these values into the formula:

![](OEBPS/image_rsrc56P.jpg)

# Interpretation

Accuracy (100%) : Indicates that the model correctly predicted 100% of the instances, reflecting perfect overall correctness in its predictions.

Precision (100%) : Of all the instances predicted as positive, 100% were actually positive. This indicates no false positives, highlighting the model's perfect reliability in making positive predictions.

Recall (100%) : The model correctly identified 100% of the actual positive instances. This suggests no false negatives, indicating that the model effectively captures all positive instances.

F1 Score (100%) : Combines precision and recall into a single metric, providing a balanced assessment of the model's performance. The F1 Score of 100% suggests a perfect balance between precision and recall, indicating the model's flawless effectiveness in classifying instances into their respective classes.

# Model Evaluation

After training the machine learning model, it is important to evaluate its performance by checking the accuracy score. The accuracy score shows how well the model fits the data it was trained on, as illustrated in Figure 3-68.

![](OEBPS/image_rsrc56R.jpg)

Figure 3-68.

# Model Result Interpretation

Accuracy (100%): A model accuracy score of 100%  indicates that the model made perfect predictions on the dataset. It correctly classified all instances without any errors, achieving the highest level of accuracy possible.

This implies that the model is highly reliable and effective in its task, as it successfully captured all patterns present in the data.

# Code Explanation

The function accuracy\_score(y\_test, y\_pred) from the scikit-learn library is used to calculate the accuracy of a classification model. Here’s a detailed explanation:

Inputs:

y\_test: This is the array of true labels for the test dataset. These labels are the actual values that you are trying to predict.

y\_pred: This is the array of predicted labels that the model has generated for the test dataset. These predictions are based on the test features (X\_test).

# Conclusion

We utilized the health data to train and evaluate several machine learning models, including Logistic Regression Model , K-Nearest Neighbour (K-NN) Model , Support Vector Machine (SVM) Model , Naïve Bayes Model , Kernel SVM Model , Decision Tree Classification Model , and Random Forest Classification . The performance outcomes for these models are as follows:

| # || Model Name || Model Accuracy Score (%) |
| --- | --- | --- |
| 1 || Logistic Regression || 86.3% |
| 2 || K-Nearest Neighbour (K-NN) || 88.3% |
| 3 || Support Vector Machine (SVM) || 85.4% |
| 4 || Naïve Bayes || 85.4% |
| 5 || Kernel SVM || 96.6% |
| 6 || Decision Tree || 100% |
| 7 || Random Forest || 100% |

The Decision Tree  and Random Forest  models' perfect accuracy scores demonstrate their strong ability to learn and generalize patterns present in the heart data. These high accuracy scores imply that these models are likely to be very dependable for classifying instances within the heart dataset, positioning them as excellent candidates for heart data classification tasks. Their capability to capture intricate relationships and interactions among features is likely a key factor contributing to their exceptional performance.

These models hold significant potential as tools for applications such as diagnosing heart conditions or predicting cardiovascular risk factors. In these tasks, precise classification is critical for making informed decisions and implementing effective interventions, highlighting the importance of leveraging models with such robust performance and accuracy.

# [Chapter 4](#part0001_split_001.xhtml#a4FZ)

# Clustering

Clustering is like organizing your messy room. You put similar things together, like clothes in one pile, books in another, and toys in another. In machine learning, it's similar but with data. We group similar data points together to find patterns and relationships, helping us understand the information better. For example, we might group customers who buy similar things, helping businesses understand their customers' preferences. Here are some simplified examples of its application in different industries:

Retail: In retail, clustering is used for customer segmentation, grouping customers based on their purchasing behavior. This helps retailers tailor marketing strategies and promotions to specific customer segments.

Healthcare: In healthcare, clustering can be used for patient segmentation, grouping patients with similar medical histories or symptoms. This helps healthcare providers personalize treatment plans and predict disease outcomes.

Finance: In finance, clustering is used for fraud detection, grouping transactions based on their similarity to identify potentially fraudulent activities. It is also used for portfolio optimization, grouping financial assets with similar risk and return profiles to optimize investment strategies.

Manufacturing: In manufacturing, clustering can be used for quality control, grouping products based on their characteristics to identify defects or anomalies. It is also used for supply chain optimization, grouping suppliers or manufacturing processes to optimize production efficiency.

Marketing: In marketing, clustering is used for market segmentation, grouping consumers with similar demographics or behavior to target marketing campaigns more effectively. It is also used for trend analysis, identifying patterns and trends in consumer preferences or market behavior.

Telecommunications: In telecommunications, clustering is used for network optimization, grouping network users based on their usage patterns to optimize network capacity and performance. It is also used for customer churn prediction, grouping customers with similar characteristics to identify those at risk of leaving the service.

# K-means clustering

K-means clustering is a popular unsupervised machine learning technique that groups data points into distinct clusters based on their similarities. The algorithm assigns each data point to one of the pre-determined number of K clusters. Next, it iteratively adjusts the center of each cluster until the distance between the center and the data points is minimized. The result is a set of K clusters containing data points with similar characteristics.

K-means clustering is widely used in various fields such as image segmentation, customer segmentation, and anomaly detection. It is an effective way to identify patterns and structures in large datasets, and can help in making data-driven decisions.

# Problem statement

Kelly, a new product manager at a commercial bank, is eager to boost transaction volume. She's enlisted the data team's help for a targeted advertising campaign. Kelly's plan involves sorting customers by annual income and score, placing them into clusters. This segmentation allows for tailored ad targeting, leveraging each group's spending habits. By maximizing marketing efforts in this manner, the bank aims to increase transaction engagement and ultimately boost its income

The source code is available here: [Clustering](https://www.google.com/url?q=https://github.com/anyasorc/appliedml/blob/main/Master_class_week_4_K_MEANS_clustering%2520\(1\).ipynb&sa=D&source=editors&ust=1720099682008589&usg=AOvVaw0QBo2ujXABDk6D9lOu1hg-)  

Figure 4-1  shows all the imported required libraries

![](OEBPS/image_rsrc56X.jpg)

Figure 4-1.

# Import and View Data

Figure 4-2  shows how data was imported and viewed as seen below.

![](OEBPS/image_rsrc56Y.jpg)

Figure 4-2.

# Check for missing values

df.isna().sum() is a chain of methods that calculates the total number of missing values (i.e., NaN values) in each column of the DataFrame df as seen in Figure 4-3 .

![](OEBPS/image_rsrc56Z.jpg)

Figure 4-3.

Based on the problem statement, the target columns we will be working with are Annual\_Income and Spending\_Score respectively which can be accessed with index position of iloc at position 5 and 6 as seen in Figure 4-4 .

![](OEBPS/image_rsrc570.jpg)

Figure 4-4.

# Code Explanation

![](OEBPS/image_rsrc571.jpg)

df.iloc\[:, \[5, 6\]\]: This selects specific columns from the DataFrame df.

: selects all rows.

\[5, 6\] selects columns at index positions 5 and 6.

This operation retrieves data from columns 5 and 6 of the DataFrame.

.values: This attribute returns the values of the selected data as a NumPy array.

It converts the DataFrame slice into a two-dimensional NumPy array.

X\[:10\]: This slices the NumPy array X to display the first 10 rows.

It provides a preview of the selected data for the first 10 rows.

# Get the number of clusters using the Elbow method.

The get the number of clusters we will use the elbow method as seen in Figure 4-5 .

![](OEBPS/image_rsrc572.jpg)

Figure 4-5.

# Code Explanation

The code snippet performs KMeans clustering with varying numbers of clusters and uses the Elbow Method to determine the optimal number of clusters. It calculates and plots the Within-Cluster Sum of Squares (WCSS) values against the number of clusters, helping to identify the "elbow" point where the optimal number of clusters lies.

wcss = \[\]: Initializes an empty list to store the Within-Cluster Sum of Squares (WCSS) values.

WCSS is a measure of the compactness of the clusters formed by KMeans clustering. Lower WCSS values indicate tighter clusters.

for i in range(1, 11): Loops through a range of numbers from 1 to 10, representing the candidate number of clusters to be evaluated.

kmeans = KMeans(n\_clusters=i, init='k-means++', random\_state=42): Creates a KMeans clustering object with i clusters.

n\_clusters=i: Specifies the number of clusters for the current iteration.

init='k-means++': Uses the k-means++ initialization method to select initial cluster centroids, which can improve convergence.

random\_state=42: Sets a random seed for reproducibility.

kmeans.fit(X): Fits the KMeans model to the data X, where X is the dataset to be clustered.

wcss.append(kmeans.inertia\_): Appends the WCSS value of the fitted model to the wcss list.

kmeans.inertia\_: Retrieves the WCSS value of the fitted KMeans model.

plt.plot(range(1, 11), wcss): Plots the number of clusters (x-axis) against the corresponding WCSS values (y-axis).

plt.title('The Elbow method'): Sets the title of the plot.

plt.xlabel('Number of Clusters'): Sets the label for the x-axis.

plt.ylabel('WCSS'): Sets the label for the y-axis.

plt.show(): Displays the plot.

The purpose of the "elbow" point in the plot is to indicate the optimal number of clusters, where adding more clusters does not significantly reduce WCSS as seen in Figure 4-6 . Note: The elbow point is often chosen as the point of inflection, where the rate of decrease in WCSS begins to decrease more slowly. It is where the curve starts to bend less abruptly which is number 6 in this context based on the data.

![](OEBPS/image_rsrc573.jpg)

Figure 4-6.

# Training the model

To train the k-means clustering model, we utilize the entire dataset and specify the number of clusters obtained from Figure 4-6 . Figure 4-7  illustrates the process of training the model in this manner.

![](OEBPS/image_rsrc574.jpg)

Figure 4-7.

# Code Explanation

The code snippet initializes and trains a k-means clustering model with 6 clusters using the specified dataset X. It assigns each data point to its corresponding cluster and stores the cluster labels in the variable y\_kmeans.

kmeans = KMeans(n\_clusters=6, init='k-means++', random\_state=42): Initializes a k-means clustering model.

n\_clusters=6: Specifies the number of clusters to be created. In this case, the model will attempt to identify 6 clusters in the data.

init='k-means++': Specifies the initialization method for selecting initial cluster centroids. 'k-means++' is a smart initialization technique that helps speed up convergence.

random\_state=42: Sets a random seed for reproducibility. It ensures that the initialization of centroids is consistent across runs.

# Predicting with the test data

Figure 4-8  below illustrates how we made predictions using the trained model (kmeans) and the test data (X).

![](OEBPS/image_rsrc575.jpg)

Figure 4-8.

# Code Explanation

y\_kmeans = kmeans.fit\_predict(X): Fits the k-means model to the data X and assigns each data point to its corresponding cluster.

kmeans.fit(X): Fits the k-means model to the data X, where X is the dataset to be clustered.

kmeans.predict(X): Predicts the cluster labels for each data point in X and assigned to y\_kmeans.

# View the predicted outcome in y\_kmeans

Figure 4-9  shows what is inside the variable y\_kmeans

![](OEBPS/image_rsrc576.jpg)

Figure 4-9.

Keep in mind that the predicted output indicates clusters numbered from 0 to 5 (which totals 6 when counted from 0 to 5). This means that:

Cluster 1 corresponds to index position 0,

Cluster 2 corresponds to index position 1,

Cluster 3 corresponds to index position 2,

Cluster 4 corresponds to index position 3,

Cluster 5 corresponds to index position 4,

Cluster 6 corresponds to index position 5.

To find the true cluster position, simply add 1 to the index positions.

# Visualize the predicted outcome

Figure 4-10 shows how to go about the implementation

![](OEBPS/image_rsrc577.jpg)

Figure 4-10.

# Code Explanation

The code snippet inf Figure 4-10 creates a scatter plot to visualize the clusters of bank customers based on their annual income and spending score. Each cluster is represented by a different color, and centroids are marked in yellow. This visualization provides insights into customer segmentation and can guide marketing strategies.

Scatter Plots:

plt.scatter(x, y, s, c, label): This function is used to create scatter plots.

x: The x-coordinates of the data points.

y: The y-coordinates of the data points.

s: The size of the markers (optional).

c: The color of the markers (optional).

label: The label for the scatter plot (optional).

Data Plotting:

X\[y\_kmeans == 0, 0\]: Selects the x-coordinates of data points belonging to cluster 1.

X\[y\_kmeans == 0, 1\]: Selects the y-coordinates of data points belonging to cluster 1.

Similarly, X\[y\_kmeans == 1, 0\] and X\[y\_kmeans == 1, 1\] select coordinates for cluster 2, and so on.

Centroid Plotting:

plt.scatter(kmeans.cluster\_centers\_\[:, 0\], kmeans.cluster\_centers\_\[:, 1\], s=300, c='yellow', label='Centroids'): Plots the centroids of the clusters.

kmeans.cluster\_centers\_\[:, 0\]: Retrieves the x-coordinates of the cluster centroids.

kmeans.cluster\_centers\_\[:, 1\]: Retrieves the y-coordinates of the cluster centroids.

Plot Customization:

plt.title("Clusters of Bank Customers"): Sets the title of the plot.

plt.xlabel("Annual Income of Bank Customers"): Sets the label for the x-axis.

plt.ylabel("Spending Score (1-100)"): Sets the label for the y-axis.

plt.legend(): Displays the legend with labels for different clusters.

plt.show(): Displays the plot.

Purpose:

The code snippet visualizes the clusters formed by the k-means clustering algorithm along with their centroids.

It helps in understanding the distribution of data points and the separation of clusters based on their features.

The execution of the code in Figure 4-10  will give the output as seen in Figure 4-11  below.

![](OEBPS/image_rsrc578.jpg)

Figure 4-11.

# Interpreting the visualization

Cluster 1: Customers in this cluster earn low annual income but have a high spending score, indicating that they carry out more transactions despite their lower income level.

Cluster 2: Customers in this cluster earn high annual income but engage in fewer transactions at the bank.

Cluster 3: This cluster comprises customers with low annual income who also perform few transactions at the bank.

Cluster 4: Customers in this cluster have high annual income and spend a significant amount.

Cluster 5: These customers have a high average annual income and engage in moderate transactions.

Cluster 6: Customers in this cluster are high earners annually but engage in few transactions at the bank.

From the graph, Kelly's target customers, based on spending behavior and income levels, are likely to be found in Clusters 1, 4, and 5. These clusters represent customers who exhibit favorable spending behavior despite variations in their annual income. Cluster 1 comprises customers with low annual income but high spending scores, Cluster 4 includes high-income customers who spend significantly, and Cluster 5 consists of customers with a high average annual income engaging in moderate transactions. These clusters present opportunities for targeted marketing efforts to maximize engagement and transactions.

# Exporting Data to CSV File.

To export the identified target customers into a CSV file, we first need to adjust the cluster column by adding 1 to show the exact cluster for ease of extraction, as demonstrated in Figure 4-12 .

![](OEBPS/image_rsrc579.jpg)

Figure 4-12.

# Grouping the clusters

After executing the code depicted in Figure 4-12 , the next step involves grouping the clusters. This grouping ensures that all customers belonging to a specific cluster are organized together, facilitating the process of exporting the data. To achieve this, we need to follow the code in Figure 4-13 .

![](OEBPS/image_rsrc57A.jpg)

Figure 4-13.

# Code Explanation

This code snippet groups the data by clusters, assigning each cluster's data to a separate variable. The groupby function organizes the data based on the 'cluster' column. Subsequently, data for each cluster is retrieved using the get\_group method and stored in individual variables, such as cluster\_1\_data, cluster\_2\_data, and so on.

# Exporting cluster to CSV

Figure 4-14 illustrates the process of exporting customer data to CSV files, which can then be attached to an email and sent to Kelly.

![](OEBPS/image_rsrc57B.jpg)

Figure 4-14 demonstrates exporting customers from clusters 1, 4, and 5 to your system. Subsequently, you can attach the exported file to an email and send it to Kelly.

# Let’s make a prediction

Figure 4-15  below illustrates the process of making predictions using the trained machine learning model. For the prediction, we will input the Annual Income and Spending Score.

![](OEBPS/image_rsrc57C.jpg)

Figure 4-15. This shows that customer with annual income of $76 and a spending score of 13 belongs to cluster 2.

# Chapter 5

# Operationalizing your ML model

Operationalizing a machine learning (ML) model involves the process of transitioning a model from the development phase into a production environment, where it can provide real-time predictions and deliver tangible value to the business. This crucial step ensures that the model's capabilities are effectively harnessed to solve real-world problems. Here's a detailed look at the process:

# Model Development

Before operationalizing, an ML model goes through several stages of development:

Data Collection and Preprocessing: Gathering and cleaning the data to ensure quality inputs for the model.

Model Training: Using algorithms to train the model on the processed data.

Evaluation: Assessing the model’s performance using various metrics and fine-tuning it for better accuracy.

# Transition to Production

The transition from a development environment (often a controlled, limited setting) to a production environment (live, operational setting) involves several key steps:

a. Model Deployment

Environment Setup: Configuring the necessary infrastructure, such as servers or cloud services, to host the model.

Integration: Incorporating the model into existing systems and applications. This may involve setting up APIs or embedding the model within software solutions.

Scalability: Ensuring the infrastructure can handle the anticipated load and scale as needed. This includes load balancing and autoscaling mechanisms.

b. Monitoring and Maintenance

Performance Monitoring: Continuously tracking the model's performance to ensure it meets the required standards. This involves setting up dashboards and alert systems.

Error Handling: Implementing mechanisms to handle prediction errors and system failures gracefully.

Retraining: Regularly updating the model with new data to maintain and improve its accuracy. This might involve automated retraining pipelines.

# Generating Value

The ultimate goal of operationalizing an ML model is to generate value. This is achieved by:

Improved Decision-Making: Providing actionable insights and predictions that help in making informed decisions.

Automation: Streamlining processes that were previously manual, increasing efficiency and reducing costs.

Enhanced Customer Experience: Offering personalized and timely services or products to customers.

# Challenges and Considerations

Operationalizing ML models also comes with its challenges and considerations:

Security: Ensuring that the model and the data it uses are secure from unauthorized access and breaches.

Compliance: Adhering to regulatory requirements and industry standards regarding data usage and privacy.

Cost Management: Balancing the costs of infrastructure and maintenance with the value generated by the model.

# Introduction to API in python

# What is an API?

An API (Application Programming Interface) is a set of rules and protocols for building and interacting with software applications. APIs define the methods and data structures that developers can use to interact with external systems or software components. They enable different software systems to communicate with each other, allowing for data exchange and functionality sharing

# Why Use APIs?

APIs are widely used for several reasons:

Integration: APIs allow different applications and services to work together. For instance, integrating a payment gateway in an e-commerce site.

Automation: Automate tasks by connecting various tools and services.

Data Access: Fetch data from external sources, such as weather data, stock prices, or social media feeds.

Scalability: APIs facilitate scalability by decoupling the client and server, allowing them to evolve independently.

# Introduction to Creating APIs with Flask

Flask is a lightweight WSGI web application framework in Python. It is designed with simplicity and flexibility in mind, making it an excellent choice for building web APIs. Here’s how you can get started with Flask to create APIs.

### 1\. Setting Up Flask

First, you need to install Flask. You can do this using pip:

### 2\. Creating a Simple Flask API

Let’s start by creating a basic API that handles GET requests.

#### Step-by-Step Guide

Import Flask : Import the necessary components from Flask.

Initialize the Flask App : Create an instance of the Flask class.

Define Routes : Use decorators to define routes that the API will respond to.

Run the App : Run the Flask application.

Figure 5-1  shows an illustration.

![](OEBPS/image_rsrc57D.jpg)

Figure 5-1.

# Code Explanation

![](OEBPS/image_rsrc57E.jpg)

Importing Libraries :

Flask : The main class from the Flask library to create the web application.

jsonify : A function to convert a Python dictionary to a JSON response.

request : An object that contains data about the HTTP request (e.g., data sent in a POST request).

# Creating a Flask Application Instance

![](OEBPS/image_rsrc57F.jpg)

This line creates an instance of the Flask class. The \_\_name\_\_  variable is passed to the Flask constructor to help Flask determine the root path of the application.

### Defining Routes

Defining the /hello  Route :

![](OEBPS/image_rsrc57G.jpg)

@app.route('/hello', methods=\['GET'\]) : This decorator binds the URL /hello  to the hello  function and specifies that this route will respond to GET requests.

def hello() : The function that will be executed when a GET request is made to /hello .

return jsonify({'message': 'Hello, World!'}) : The function returns a JSON response with the message "Hello, World!".

Defining the /greet  Route :

![](OEBPS/image_rsrc57H.jpg)

@app.route('/greet', methods=\['POST'\]) : This decorator binds the URL /greet  to the greet  function and specifies that this route will respond to POST requests.

def greet() : The function that will be executed when a POST request is made to /greet .

data = request.get\_json() : Retrieves the JSON data sent in the body of the POST request.

name = data.get('name') : Extracts the value associated with the key 'name' from the JSON data.

greeting = f"Hello, {name}" : Creates a greeting message using the extracted name.

return jsonify({'message': greeting}) : Returns a JSON response with the personalized greeting message.

# Running the Application

![](OEBPS/image_rsrc57J.jpg)

This block ensures that the Flask application runs only if the script is executed directly (not imported as a module).

app.run(debug=True) : Starts the Flask development server with debug mode enabled. Debug mode provides detailed error messages and auto-reloads the server when code changes are detected.

### How It Works Together

GET Request to /hello :

When a client (e.g., a web browser or a tool like Postman) makes a GET request to http://localhost:5000/hello , the hello  function is called.

The server responds with a JSON object: {"message": "Hello, World!"} .

POST Request to /greet :

When a client makes a POST request to http://localhost:5000/greet  with a JSON body like {"name": "Alice"} , the greet  function is called.

The greet  function processes the incoming JSON data, extracts the 'name' value, and constructs a personalized greeting.

The server responds with a JSON object: {"message": "Hello, Alice"} .

# Testing the API

Using Postman :

GET request: Enter http://localhost:5000/hello  and hit 'Send'.

POST request: Enter http://localhost:5000/greet , select 'POST', set the body to raw JSON, and enter {"name": "Alice"} . Then hit 'Send'.

Figure 5-2  and Figure 5-3 shows postman in action.

![](OEBPS/image_rsrc57K.jpg)

Figure 5-2.

![](OEBPS/image_rsrc57M.jpg)

Figure 5-3.

This Flask example demonstrates how to set up a simple web API that can handle both GET and POST requests. The /hello  route responds with a static message, while the /greet  route dynamically generates a personalized greeting based on the provided JSON data. Flask's simplicity and flexibility make it a great choice for building web APIs quickly and efficiently.

# Convert Machine learning model to API

After training a model, you can serialize it to save its state and load it later for making predictions, and this can be achieved using the Pickle library. Pickle is a module in Python used for serializing and deserializing Python object structures, also known as marshalling or flattening. Serialization is the process of converting a Python object into a byte stream so it can be saved to a file or database, or sent over a network. Deserialization is the reverse process, converting the byte stream back into a Python object.

### How to Use Pickle

Here’s a simple example to demonstrate how to use Pickle for serializing and deserializing a Python object:

#### Example: Pickling and Unpickling a Python Object

Serializing (Pickling) an Object :

![](OEBPS/image_rsrc57N.jpg)

In this example, a dictionary data  is serialized and saved to a file named data.pkl . This file can be saved in a directory in your application or any preferred location that your API can access.

Deserializing (Unpickling) an Object :

![](OEBPS/image_rsrc57P.jpg)This code reads the serialized data from data.pkl  and deserializes it back into a Python dictionary. 

Here is the output

![](OEBPS/image_rsrc57R.jpg)

# Create an API for the picke ‘data.pkl’  file generated

![](OEBPS/image_rsrc57S.jpg)

In this Flask app:

We define a route /deserialize  that accepts POST requests.

Inside the route function, we extract the filename of the pickled object from the JSON payload of the POST request.

We attempt to deserialize the object from the specified file using pickle.load() .

If the deserialization is successful, we return a JSON response with the deserialized object.

If the file is not found or any other error occurs during deserialization, we return an error response.

To test this API endpoint, you can send a POST request to /deserialize  with a JSON payload containing the filename of the pickled object:

![](OEBPS/image_rsrc57T.jpg)

# Convert the Unsupervised Learning Model in chapter 4  to API

We will be converting the maching model in [ Chapter 4](#part0001_split_001.xhtml#a4FZ)  to an API by following the steps below:

Conver the machine learning model to API

Figure 5-4  shows the code on how to export our machine learning model, which in this context is kmeans as seen in Chapter 4 of this book, inot a pickle file named model.pkl

![](OEBPS/image_rsrc57U.jpg)

Figure 5-4.

# Code explanation

The import pickle  statement imports the pickle  module, which provides functions for serializing and deserializing Python objects.

The open('model.pkl', 'wb')  statement opens a file named 'model.pkl'  in write binary mode ( 'wb' ). This file will be used to save the serialized object.

The with  statement is used as a context manager to automatically close the file after the block of code is executed.

Inside the with  block, pickle.dump(kmeans, f)  serializes the kmeans  object using the pickle.dump()  function. This function takes two arguments: the object to be serialized ( kmeans ) and the file object ( f ) where the serialized data will be written.

After executing this code, the kmeans  object will be serialized and saved to the file 'model.pkl' , ready to be loaded later using pickle.load() .

The next step is to bring the copy the model.pkl file to your preferred directory and reference it. In my case, the model is dropped in the root directory of my application as seen in Figure 5-5.

![](OEBPS/image_rsrc57V.jpg)

Figure 5-5.

Here is the complete code below:

![](OEBPS/image_rsrc57W.jpg)

Code explanation

This code defines a Flask API with a single endpoint /api/custype  that accepts POST requests. Let's break down the code step by step:

Imports :

from flask import Flask, jsonify, request : Imports the Flask framework and necessary modules for handling JSON responses and HTTP requests.

import pickle : Imports the pickle module for serializing and deserializing Python objects.

import numpy as np : Imports the numpy library, commonly used for numerical computations in Python.

Flask Application Setup :

app = Flask(\_\_name\_\_) : Creates a Flask application instance.

API Endpoint /api/custype :

@app.route('/api/custype', methods=\['POST'\]) : Decorates the Custype()  function as the endpoint handler for POST requests to /api/custype .

def Custype() : Defines the Custype()  function to handle requests to the /api/custype  endpoint.

Inside the function:

data = request.get\_json() : Retrieves the JSON data from the request payload.

Annual\_Income = data.get('Annual\_Income')  and Spending\_Score = data.get('Spending\_Score') : Extracts the 'Annual\_Income' and 'Spending\_Score' values from the JSON data.

filename = 'model.pkl' : Specifies the filename of the pickled machine learning model.

Deserializes the machine learning model from the file 'model.pkl'  using pickle.load(f) .

Uses the loaded model to make predictions on the provided 'Annual\_Income' and 'Spending\_Score' values.

Constructs a message containing the prediction outcome and returns it as a JSON response.

The try-except  block ensures that any exceptions that occur during the prediction process are caught, and an appropriate error response is returned.

Run the Flask Application :

if \_\_name\_\_ == '\_\_main\_\_': : Checks if the script is being run directly.

app.run(debug=True) : Starts the Flask development server with debug mode enabled.

# Explanation of the Prediction Message

The prediction message returned in the JSON response indicates which cluster the customer belongs to based on their annual income and spending score, as predicted by the machine learning model. The message includes the customer's annual income, spending score, and the cluster number to which they belong.

Overall, this Flask API endpoint demonstrates how to use a trained machine learning model to make predictions on incoming data provided via a POST request, and return the prediction result as a JSON response.

# Test with postman

Figure 5-6  shows the API test using postman to test the local api on my system.

![](OEBPS/image_rsrc57X.jpg)

Figure 5-6.

The outcome interpretation as found in [chapter 4](#part0001_split_001.xhtml#a4FZ)  interpretations of the cluster outcome. This implies that the customer has a high average annual income and engage in moderate transaction activities.

# Deployment

The API can be deployed on various platforms that support Python, such as Azure, AWS, PythonAnywhere, and Aiven. These platforms offer robust hosting services where you can deploy and manage your API. Once deployed, you can share the endpoint URL with the frontend development team for integration into the application.

Several of these platforms provide free hosting options for an initial period, after which they typically start charging your credit card. It's important to be aware of the terms and pricing details when choosing a hosting provider for your API deployment. This allows you to effectively manage costs and make informed decisions regarding your hosting needs.

We have opted to use Pythonanywhere ( [Pythonanywhere](https://www.google.com/url?q=https://www.pythonanywhere.com/&sa=D&source=editors&ust=1720099682040546&usg=AOvVaw1SAR9Jd7pT-ohjVTBx6gpe) )  as our hosting platform for this application due to its robustness and flexibility, making it well-suited for our test deployment. Aiven provides a reliable environment for deploying applications and supports Python along with the installation of necessary libraries. However, you are free to choose any deployment platform that supports Python and offers the capability to install required libraries or provides an environment where you can manage dependencies as needed. This flexibility allows you to select the platform that best aligns with your project requirements and operational preferences.

Step 1: Access PythonAnywhere

Navigate to [ ](https://www.google.com/url?q=https://www.pythonanywhere.com/&sa=D&source=editors&ust=1720099682041114&usg=AOvVaw0StOAWzfUfgmSVhQZUG3eO) [Pythonanywhere](https://www.google.com/url?q=https://www.pythonanywhere.com/&sa=D&source=editors&ust=1720099682041350&usg=AOvVaw28Ey1ud5v2oQdceOej3Uzl)  in your web browser to access the platform. Figure 5-7  illustrates the landing screen of PythonAnywhere. Click on plans & pricing and click on the “ Create a Beginer account ” button as seen in Figure 5-8.  
 ![](OEBPS/image_rsrc57Y.jpg)Figure 5-7. 

Step 2 : Click the button illustrated in Figure 5-8  to start the onboarding process. After completing onboarding, proceed to log in.

![](OEBPS/image_rsrc57Z.jpg)

Figure 5-8.

Step 3 : Figure 5-9  shows the login form where you are expected to enter your login details to proceed to the dashboard.  

![](OEBPS/image_rsrc580.jpg)

Figure 5-9.

Step 4 : Navigate to the "Files" link from the dashboard, as depicted in Figure 5-10 .  
 ![](OEBPS/image_rsrc581.jpg)Figure 5-10. 

Step 5 : Name your application files directory and click the "New directory" button to create it, as shown in Figure 5-11 .

![](OEBPS/image_rsrc582.jpg)

Figure 5-11.

Step 6 : Navigate into the "mysite" directory you created. Click the "Upload a file" button, select app.py , and submit. Repeat this process to upload model.pkl . The uploaded files will appear as shown in Figure 5-12 .  

![](OEBPS/image_rsrc583.jpg)

Figure 5-12.

Step 7 : Select the "Web" link, depicted in Figure 5-13 . This will guide you to the setup area for your API or application.

![](OEBPS/image_rsrc584.jpg)Figure 5-13. 

Step 8:  Click the “Add a new web app” button, then select the radio button corresponding to the default domain provided by PythonAnywhere, as shown in Figure 5-14 . Note that the name displayed will reflect your individual onboarding details, which may differ from the example shown.

![](OEBPS/image_rsrc585.jpg)

Figure 5-14.

Step 9 : Choose a Python web framework that matches the one used for developing your API, such as Flask, as illustrated in Figure 5-15 .

![](OEBPS/image_rsrc586.jpg)

Figure 5-15.

Step 10 : Choose the Python version on which your solution is built. For example, if your API was developed using Python 3.9, select that version, as shown in Figure 5-16 .

![](OEBPS/image_rsrc587.jpg)

Figure 5-16.

Step 11 : Figure 5-17  shows the path to the application file that will execute when the API starts. Keep this as the default setting and click "Next". We will update the file path from flask\_app.py  to app.py , the actual name of our application file, later.  For now, proceed by clicking the “Next” button to navigate to the screen shown in Figure 5-18.

![](OEBPS/image_rsrc588.jpg)

Figure 5-17.

Step 12 : The Web dashboard shows that our application setup was successful as shown by the light green indicator message.  

![](OEBPS/image_rsrc589.jpg)

Figure 5-18.

Step 13 : Scroll down to the section depicted in Figure 5-19 . Click on the “WSGI configuration file” link to edit the file and update it to point to our API file, which should run when the application starts. Currently, it points to the default file created by PythonAnywhere host as seen in Figure 5-20 . Change the item highlighted to align with what we have in FIgure 5-21 .

![](OEBPS/image_rsrc58A.jpg)

Figure 5-19.

![](OEBPS/image_rsrc58B.jpg)Figure 5-20. ![](OEBPS/image_rsrc58C.jpg)

Figure 5-21.

Step 14 : Scroll back up and click the “Reload anyasorchigozie.pythonanywhere.com” button to refresh the application configuration with the recent settings, as shown in Figure 5-22 .

![](OEBPS/image_rsrc58D.jpg)

Figure 5-22.

Step 15 : Our API is now ready to be accessed at this URL: [ http://anyasorchigozie.pythonanywhere.com/api/custype](https://www.google.com/url?q=http://anyasorchigozie.pythonanywhere.com/api/custype&sa=D&source=editors&ust=1720099682046404&usg=AOvVaw3x0oFS1EKDQMIENm_UZnSC) , as shown in Figure 5-23 .

![](OEBPS/image_rsrc58E.jpg)

Figure 5-23. This was the same output we got during the test locally. This clearly shows that our API and model has been deployed and can be accessed by our application to solve business problems.

# Conclusion

In Chapter 5, we explored how machine learning models can be transformed into pickle files and seamlessly integrated into applications as APIs. This process enables us to operationalize machine learning models in real-life scenarios. Hosting these APIs on platforms that support Python applications is essential for maximizing the utility of machine learning across an organization. It allows businesses to extract true value from their machine learning investments enterprise-wide.

This methodology extends beyond a single sector; once models are trained, converting them into APIs and deploying them enables widespread applicability. This approach ensures that the benefits of machine learning, from improved decision-making to automation, can be realized across diverse industries and applications.

As we conclude our machine learning journey, I encourage you to continue practicing and exploring the automation and innovation opportunities that AI offers. With the power to create now in your hands, delve into coding with enthusiasm. Happy coding!

# References

Katrina, W. (n.d). A guide to the types of machine learning algorithms and  
      their applications. sas.com.       
      https://www.sas.com/en\_gb/insights/articles/analytics/  
      Machine-learning-algorithms.html

Namitha, V. (2022). How Machine Learning Improves Retail Demand  
      Forecasting. Algonomy.  
      https://algonomy.com/blogs/retail/how-machine-learning-  
      improves-retail-demand-forecasting/

Volodymyr, A. (2024). Machine Learning Predictive Maintenance: How to  
      Implement It? Lemberg Solutions.

https://lembergsolutions.com/blog/machine-learning-  
      predictive-maintenance-how-implement-it

![](OEBPS/image_rsrc58F.jpg)