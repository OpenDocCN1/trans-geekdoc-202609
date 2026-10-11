![](images/cover.jpg)

![Cover](images/cover.jpg)

First Edition 2025

Copyright © BPB Publications, India

ISBN: 978-93-65895-292

All Rights Reserved. No part of this publication may be reproduced, distributed or transmitted in any form or by any means or stored in a database or retrieval system, without the prior written permission of the publisher with the exception to the program listings which may be entered, stored and executed in a computer system, but they can not be reproduced by the means of publication, photocopy, recording, or by any electronic and mechanical means.

LIMITS OF LIABILITY AND DISCLAIMER OF WARRANTY

The information contained in this book is true to correct and the best of author’s and publisher’s knowledge. The author has made every effort to ensure the accuracy of these publications, but publisher cannot be held responsible for any loss or damage arising from any information in this book.

All trademarks referred to in the book are acknowledged as properties of their respective owners but BPB Publications cannot guarantee the accuracy of this information.

![](images/BPB_Catalogue_QR.png)

[www.bpbonline.com](https://www.bpbonline.com)

**Dedicated to**

My beloved parents:  
Shri Ajit Das  
Smt Kakali Das  
and  
My wife Bitasta Biswas Das

# About the Author

Abhishek Das is a seasoned data scientist with over a decade of experience in advanced analytics and machine learning. He is currently involved in generative AI projects and has a proven track record of delivering impactful data insights across industries. Abhishek has won multiple data science hackathons and mentored over 2000 professionals in their career transitions. As a LinkedIn Top Voice, he frequently shares his knowledge and has spoken at numerous industry conferences. He was also a data science trainer at leading edtech companies, helping shape the careers of aspiring data scientists.

# Acknowledgement

I am deeply grateful to the many individuals who supported me throughout the journey of writing this book. Their encouragement and guidance have been a constant source of strength.

First and foremost, I owe immense gratitude to my parents, whose belief in me has always been my greatest motivation. I could not have reached this milestone without their endless support.

To my wife, I am forever grateful for your patience, love, and understanding during the many long hours I spent immersed in this project. Your encouragement kept me going and made this journey all the more special. I am also indebted to my mentors, whose wisdom and guidance have shaped me both personally and professionally. Your words of encouragement and insights continue to inspire me to push my boundaries and grow every day.

My gratitude also goes to the team at BPB Publications, for their incredible support and understanding. Thank you for providing me the time and flexibility needed to complete this book.

Finally, I want to thank the data science community and my readers. Your passion for learning and innovation inspires me to keep sharing knowledge and striving to contribute more. This book is for you, and I hope it becomes a valuable part of your journey.

# Preface

In today’s era of rapid digital transformation, data science has become one of the most dynamic and impactful fields. Yet, for both beginners and experienced professionals, navigating its vast and complex landscape can feel overwhelming. This book aims to provide a clear, structured, and hands-on guide to mastering the essential concepts and techniques that form the foundation of data science.

Whether you are a beginner exploring the possibilities of data science, a professional looking to enhance your analytical skills, or a domain expert aiming to leverage data-driven solutions, this book is designed to meet you at your level and guide you forward. Starting with the basics and gradually building up to advanced topics, this book covers the full spectrum of data science—from understanding the fundamentals to developing machine learning models and even carving out a successful career in this field.

The journey through these pages is not just about learning theory but also about applying your knowledge to solve real-world problems. Through practical examples and clear explanations, this book ensures that you develop a strong understanding of data science concepts while gaining the confidence to implement them effectively.

Here is a brief overview of the chapters to guide you through this journey:

[Chapter 1: The Data Science Landscape](#ch01.xhtml) - This chapter introduces the fundamentals of approaching data and framing business problems. You will learn to analyze problems by breaking them into manageable parts and understand how proper framing determines the success of data-driven solutions. The chapter also explores the four types of business analytics—descriptive, diagnostic, predictive, and prescriptive and their applications based on business needs.

[Chapter 2: R Basics](#ch02.xhtml) - This chapter provides an overview of R and RStudio, guiding you through creating and managing essential R objects like vectors, matrices, lists, and data frames. You will learn to install and load packages, use built-in and custom functions, and work with R's help system. By the end, you will know how to load and export datasets, setting the foundation for exploring and analyzing data in later chapters.

[Chapter 3: Exploring Data](#ch03.xhtml) - Exploring data is crucial before visualization or machine learning. This chapter covers selecting columns, filtering rows, adding new variables, and handling duplicates. You will also learn to manage missing values, understand their causes, and treat them effectively.

[Chapter 4: Wrangling Data](#ch04.xhtml) - Data manipulation is essential when working with real-world datasets. This chapter focuses on using the dplyr package for data wrangling. You will learn to reshape data between wide and long formats, aggregate data for summaries, and merge data frames for analysis. With these tools, you will streamline your data handling process and prepare data for deeper insights.

[Chapter 5: Working with Dates](#ch05.xhtml) - Dates often appear as character data, making them unsuitable for direct analysis. This chapter teaches you to convert such data into date or datetime classes using R's lubridate package. You will learn to extract meaningful components from date columns for analysis or machine learning, perform arithmetic operations, calculate intervals, and handle time differences effectively.

[Chapter 6: Manipulating Strings](#ch06.xhtml) - Working with text data is a common task in data science, and being able to manipulate strings effectively is essential for cleaning and preparing your data. In this chapter, you will dive into the stringr package, where you will learn how to combine strings, split them apart, and standardize text by changing cases, or removing extra spaces. We will also explore how to find and match specific patterns using regular expressions (regex) to handle text data efficiently.

[Chapter 7: Visualizing Data](#ch07.xhtml) - Data visualization is essential for understanding and communicating insights. This chapter focuses on ggplot2 to create impactful visualizations. You will explore bar graphs, histograms, and density plots for distributions, as well as scatter plots for feature relationships. Additionally, you will visualize time series data with line charts and proportions using stacked bar and pie charts.

[Chapter 8: Feature Engineering](#ch08.xhtml) - Effective features are key to improving ML models. This chapter explains how to transform raw data into meaningful inputs. You will learn techniques like binning and scaling for numerical data, as well as encoding methods like one-hot and label encoding for categorical variables. The chapter also covers creating new features from existing data to enhance predictive performance.

[Chapter 9: Statistics and Probability](#ch09.xhtml) - Statistics and probability form the backbone of data science. In this chapter, you will explore the key concepts needed to analyze and interpret data effectively. You will start with sampling techniques and descriptive statistics to identify patterns and understand your data. Then, you will dive into inferential statistics and hypothesis testing to validate claims about populations based on sample data. Finally, you will study probability theory, which plays an essential role in understanding and developing machine learning algorithms.

[Chapter 10: Introducing ML](#ch10.xhtml) - In this chapter, you will learn how to frame a problem and determine whether machine learning is the right solution. Discover how ML approaches differ from traditional methods and how to choose the appropriate model for a given business problem. You will also gain insights into the different types of ML systems and learn how to address common challenges when implementing ML algorithms.

[Chapter 11: Training Machine Learning Models](#ch11.xhtml) - Dive deeper into machine learning by exploring supervised and unsupervised learning techniques. This chapter begins with the distinction between supervised and unsupervised learning. You will work with popular supervised learning models like linear regression, logistic regression, and decision trees. Then, you will explore unsupervised learning concepts, focusing on clustering techniques like k-means. The chapter also highlights the advantages and limitations of these methods, helping you choose the best approach for your data.

[Chapter 12: Building a Career in Data Science](#ch12.xhtml) \- As data science continues to thrive, so do career opportunities in the field. This chapter guides you through the key steps to build and grow your career in data science. The chapter also offers tips for navigating the job search, understanding role requirements, and enhancing your communication skills to stand out as a data scientist. Curiosity and continuous learning are the ultimate keys to success in this dynamic field.

# Code Bundle and Coloured Images

Please follow the link to download the

Code Bundle and the ***Coloured Images*** of the book:

[https://rebrand.ly/20cd3d](https://rebrand.ly/20cd3d)

The code bundle for the book is also hosted on GitHub at [https://github.com/bpbpublications/Data-Science-Essentials-with-R](https://github.com/bpbpublications/Data-Science-Essentials-with-R). In case there’s an update to the code, it will be updated on the existing GitHub repository.

We have code bundles from our rich catalogue of books and videos available at [**https://github.com/bpbpublications**](https://github.com/bpbpublications). Check them out!

Errata

We take immense pride in our work at BPB Publications and follow best practices to ensure the accuracy of our content to provide with an indulging reading experience to our subscribers. Our readers are our mirrors, and we use their inputs to reflect and improve upon human errors, if any, that may have occurred during the publishing processes involved. To let us maintain the quality and help us reach out to any readers who might be having difficulties due to any unforeseen errors, please write to us at :

**[errata@bpbonline.com](mailto:errata@bpbonline.com)**

Your support, suggestions and feedbacks are highly appreciated by the BPB Publications’ Family.

**Join our book’s Discord space**

Join the book’s Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/fm1.png)

# [CHAPTER 1The Data Science Landscape](#contents.xhtml#ch01a)

[Introduction](#contents.xhtml#sc2_1a)

This chapter teaches how to approach a data problem, what to check, and what questions to ask when solving a business problem. You will know the process of analyzing a problem by setting each element apart to solve it, and that will help you to understand why problem framing leads to determining your product’s success. Depending upon the type of business requirements, all data applications fall into four types of business analytics—descriptive, diagnostic, predictive, and prescriptive.

[Structure](#contents.xhtml#sc2_2a)

This chapter will cover the following topics:

*   Why should everybody understand data science
*   Understanding the business problem
*   Process of approaching your data 
    *   Questions to ask about your data
    *   Checking reproducibility and consistency
    *   Making hypotheses and looking for evidence
*   Analytical skills you need
*   Types of business analytics 
    *   Descriptive analytics
    *   Diagnostic analytics
    *   Predictive analytics
    *   Prescriptive analytics

[Objectives](#contents.xhtml#sc2_3a)

After completing this chapter, you will have a solid grasp of the data science ecosystem and learn how to tap into the vast amounts of available data to address and solve real-world business problems effectively. You will gain foundational knowledge of approaching any data problem and attain the fundamental skills to develop into a data-driven professional.

[The need to understand data science](#contents.xhtml#sc2_4a)

Understanding data science is becoming more vital for all individuals because we live in an age where data is far and wide. With quality data skills, we could bring more power to organizational success.

Let me introduce you to Vedh, a content writer who is passionate about helping professionals build their personal brands and has built up a following of around 7,000 followers on LinkedIn. He has been sharing his knowledge on the domain (insights) on LinkedIn for the past three years. Despite the considerable effort, Vedh has struggled to gain traction on the platform for the past few months. He has been posting regularly; on the other hand, his posts are not getting the same level of engagement that they used to. As a result, Vedh feels balked and wonders if he can do anything to boost his engagement rates and reach more people with his content.

Over time, Vedh attends a data science workshop where he learns about the power of data analytics in strengthening content performance. Intrigued, Vedh decides to try it and ends up realizing that by analyzing his LinkedIn posts, he can gain valuable insights into what is working and what is not and leverage data for his content strategy.

Excited by this contemporary insight, Vedh starts reviewing his posts in fine points. He commences by tracking the engagement rates on each post, including the number of likes, comments, and shares. He proceeds by categorizing his posts by topic, format, and length and tracking the engagement rates in each category.

Within a brief timeframe of analysis, Vedh notices some exciting trends. First, he realizes that his posts on a particular topic get more engagement than others and that his longer-form posts perform better than his shorter posts. Upon closer inspection, he realizes that the posts that performed better were the ones that included more personal anecdotes and stories. Moreover, posts with images or videos get more engagement than text-only posts. With this knowledge, Vedh decides to incorporate more stories into his future posts. [Figure 1.1](#ch01.xhtml#fig1-1) shows Vedh’s content performance in the period of 90 days in LinkedIn.

![](images/Figure1.1.jpg)

Figure 1.1: LinkedIn Content Performance of Vedh

Next, Vedh looks at the demographics of his audience. He identifies most of his followers as mid-career professionals in IT services and consulting organizations. Then, Vedh creates more content tailored to this specific audience, such as sharing tips for building a personal brand for IT consultants. The below figure displays the demographic behavior of Vedh’s followers on LinkedIn.

![](images/Figure1.2.png)

Figure 1.2: Top demographics distribution of Vedh’s LinkedIn followers

Finally, Vedh looks at the timing and frequency of his posts. He discovers that his posts tend to get more engagement when he posts them in the late morning rather than in the evening or at night. He also finds that posting at least twice a week leads to higher engagement rates, keeping his audience engaged and interested.

Using these metrics, Vedh begins implementing insights into his LinkedIn strategy. He begins to focus more on the topics that resonate with his audience, experimenting with longer-form content and more multimedia and posting more frequently during the late morning hours. Over time, Vedh's engagement rates start to improve. His posts are getting more likes, comments, and shares, and he is beginning to attract more followers to his LinkedIn profile. He is also starting to get noticed by industry thought leaders sharing his posts and engaging with his content.

Thanks to his newfound understanding of data science and analytics, Vedh has been able to take his LinkedIn content to the next level. He is now a recognized expert in personal branding and is helping more and more professionals build their own personal brands. Overall, Vedh's experience highlights how data science can help content writers to gain valuable insights into their performance on social media platforms like LinkedIn.

The abundance of data available today presents a huge opportunity to gain valuable insights, making it more critical than ever to have an understanding of data.

Now, let us consider the example of Vedh, who recently learned data science and decided to take a vacation to Seychelles to recharge.

With his newfound understanding of data science, Vedh realizes he can use data to help him navigate the island and make the most of his trip. A couple of basic questions he wanted to answer first using data were:

*   How many days to spend on one island?
*   Which attractions to visit each day?
*   What is the most optimal route from one place to another?

Vedh decides to use his data science skills to find the best deals on flights and hotels. He begins by analyzing airfare data to identify the competitive prices of days and periods to fly to and from Seychelles. Then, using data about flight availability, and ticket prices, Vedh can find the best flight deals, saving him hundreds of dollars on airfare.

Next, Vedh focuses on finding the best hotels on each island. He uses online review sites to find hotels with the highest ratings and positive reviews but also goes a step further by analyzing the sentiment of the reviews to identify any potential issues or areas of concern. Using data science techniques such as sentiment analysis, Vedh can identify hotels that consistently have positive reviews and high ratings, giving him the confidence to book his accommodations without worry.

Upon arriving at Mahe (the island of Seychelles), Vedh realized that he had many activities to choose from and was overwhelmed with options. Vedh starts by downloading a map of Mahe and the other islands of Seychelles onto his smartphone. He then uses his data science skills to analyze the map and identify the best routes to visit all the island's major tourist destinations. Next, Vedh starts to track the popularity and ratings of different activities on Mahe, including hiking trails, beaches, and cultural sites. He also looked at the frequency and timing of different tours and activities and identified the best times to visit each attraction. Finally, using data about traffic patterns and tourist foot traffic, Vedh can plan his itinerary for each day, ensuring that he maximizes his time and avoids long lines and crowded areas.

As Vedh moves on to the other islands, he uses data to his advantage. He uses online reviews and ratings to find the best restaurants and local cuisine and his data skills to analyze the menus and find the best dishes to try. He also uses data to identify the best beaches and scenic locations to visit, using satellite imagery and weather data to plan his visits based on the best times for optimal weather conditions and lighting.

With his data-driven approach to travel, Vedh can make the most of his trip to Seychelles. He visits all major tourist destinations, eats at the best restaurants, and enjoys the most beautiful beaches and scenic locations. Moreover, thanks to his understanding of data science, Vedh can navigate the islands easily and confidently, making his vacation unforgettable.

[Understanding the business problem](#contents.xhtml#sc2_5a)

Unlike traditional operational assets such as real estate, inventories, and patents, data can generate immense growth potential when used effectively. The crucial aspect is understanding its inherent value, using it smartly, and establishing a culture that welcomes the advantages of a data-driven approach. Data has become a gateway to new opportunities for organizations worldwide, with limitless potential uses. The amount of data generated is increasing exponentially, primarily due to the growing number of connected devices and the rising percentage of the world's population gaining internet access, including fixed and mobile devices.

Hey, do you know? Vedh has been running his personal branding agency, Being Minimalist Services, for several years! While his business was doing well, he knew there was room for improvement. He had always made decisions based on his experiences and intuition but realized he needed to start incorporating data into his decision-making process.

| What are the hallmarks of a data-driven organization?Being a data-driven organization means that your company is skilled at utilizing its data and that the data team has a say in critical decision-making processes. In such organizations, decisions are driven mainly by data insights rather than personal biases or pet projects. |
| --- |

With this in mind, Vedh began investing in data collection and analysis tools. He started tracking website analytics, social media metrics, and other key performance indicators to understand his business and customers better. As he dug deeper into the data, Vedh could identify trends and patterns that he had never noticed.

For instance, he discovered that most of his clients were from a particular region, and he could adjust his marketing strategy accordingly to target that region. He also found that certain types of content were getting more engagement on social media than others, allowing him to tailor his content strategy and improve his social media reach.

He saw increased customer engagement, more leads, and ultimately more business. However, Vedh knew that he could do more. So, he began incorporating data into every aspect of his company, from marketing to sales, to operations.

By making data a central part of his decision-making process, Vedh was able to make more informed decisions and avoid costly mistakes. However, he realized that being data-driven was just the first step and needed to create a data-led culture throughout his organization to thrive truly.

| How can an organization be characterized as data-led?Now, data-led organizations take it a step further. Here, data gets integrated into work at every level and for every role in the company, discussed in every meeting, and incorporated into both synchronous and asynchronous workflows.In the coming years, becoming a data-led organization will be crucial for the success and longevity of a business and may help future-proof it against economic downturns. This is especially true for businesses with high operational or financial complexity levels. |
| --- |

Vedh's goal is to build a proficient team using data to drive business decisions. In addition, he aims to create a company culture that values data as a strategic asset and embeds data at every level and for every role in the business. He knows that by becoming a data-led organization, he can future-proof his business against recessions and thrive in an increasingly competitive market.

![](images/Figure1.3.jpg)

Figure 1.3: Data-driven organizations

The above figure shows what drives business value in data-driven organizations. These are just a few questions that organizations should reflect on as they establish a data-driven culture and assess their readiness to adopt new perspectives, behaviors, and practices regarding data.

*   As an organization, do we have a clear data strategy in place? If not, what challenges are we facing where data can help?
*   Is there a push from leadership to prioritize data in our business decision-making process?
*   Do we comprehensively understand the data available to us, and do people within the organization trust it?
*   How advanced is our data management approach, and what resources could we utilize to improve and scale our organization confidently?

• What is the level of data expertise among our employees, and are there any skill gaps across different levels?

| How can an organization transform into a data-driven entity?• Establish a culture of innovation that places data at the heart of your business strategy• Develop data capabilities that support and drive this culture |
| --- |

Are we adhering to best practices in analytics, and if not, what standards should we establish to ensure consistent practices are followed throughout the organization?

Data science is an applied field where data scientists work to address the needs and resolve the problems of business consumers.

One of the critical factors in achieving advanced analytics goals for a company is aligning them with its overall objectives to enhance the profitability of its products, services, and processes. The most effective analytics solutions are created when data scientists collaborate with business stakeholders, establish success criteria upfront, and prioritize end-user needs.

Throughout the decision-making process, such as selecting the appropriate analytical technique, the team should consider how end users will interpret and act on the insights accumulated from the data.

[Process of approaching your data](#contents.xhtml#sc2_6a)

Now let us check a fascinating story of Vedh's wife, Vedika, who owned a cafe chain. She was worried about the high customer churn rate her company was experiencing. Despite having a good number of customers, the cafe chain was facing a decline in repeat customers, and Vedika wanted to understand why this was happening. To tackle the issue, Vedika sought Vedh's expertise in data science to help her identify the root cause of the problem and find solutions to reduce customer churn.

[Questions to ask about your data](#contents.xhtml#sc3_7a)

To better understand the cafe chain's operations, Vedh visited several cafes and spoke to the cafe managers (in this case, our subject matter experts). He asked them to tell him stories about the cafe's daily operations and what they thought might contribute to the customer churn rate. He even tried the cafe's food and drinks to understand better what might drive customers to come back or not.

Vedh’s approach was not simply coming up with a theory and declaring it as fact. Instead, he sought out evidence to either support or disprove her hypotheses. For Vedh, it was essential to formulate his business needs as specific questions or hypotheses. Doing so helped ensure that gathered the correct data and thought about possible gaps in the data. He started by collecting data on customer behavior—the number of customers who visit her cafes daily, the types of food and drinks they order, the times of day they come in, and transactions. However, before he even looked at the data, he made sure to understand the context in which it was collected. He examined the cafe's systems and instrumentation to ensure that the data was collected accurately and that there were no unusual configurations or population restrictions. His questions evolved as he looked at the data, but having a clear question or hypothesis kept his analysis focused and purposeful. He knew analyzing the data without clear questions or hypotheses would produce aimless results.

To start a data analysis, one should begin by formulating questions rather than simply diving into the data or using a particular technique.

Next, he began with the validation stage. He ensured the data was self-consistent and represented what he thought it did. Next, he checks for errors, missing data, and outliers that might skew his results. He also checks the logs and confirms that no data gaps or inconsistencies could have affected the analysis. The image below shows Vedh discussing the café’s challenges with the managers.

![](images/Figure1.4.png)

Figure 1.4: An illustration of Vedh speaking with his cafe managers

Once he was confident in the quality of her data, he objectively interpreted the data to determine what it was telling him. He looked for patterns and trends in customer behavior, such as which products sold the most and which days of the week had the most traffic.

[Checking reproducibility and consistency](#contents.xhtml#sc3_8a)

Vedh also considered the importance of looking at standard metrics first, even if he expected them to change with introducing new features. For example, he made sure to understand the impact of the new menu items on standard metrics like total number of customers and average customer spend before diving into custom metrics about the new items. Next, he compared these metrics to metrics reported in the past, checking for consistency with past measurements to ensure that his analysis was on the right track.

| When analyzing data, it is vital to compare metrics that are similar to past measurements, even if they were obtained from different user populations. This helps to ensure consistency in your analysis and provides insights into the changes that have occurred over time. By doing so, you can identify any discrepancies between your findings and past metrics and investigate further to validate your results. |
| --- |

He establishes the normative value of each metric, comparing it rigorously with other features and metrics. He measured the same underlying thing in multiple ways to ensure consistency and accuracy in his results. He even used different data sources for the measurements to ensure he got a comprehensive view of the data. For example, he measured customer satisfaction through surveys, social media feedback, and in-person conversations and cross-referenced that with the sales data to ensure it was all aligned.

[Making hypotheses and looking for evidence](#contents.xhtml#sc3_9a)

While analyzing the data, he noticed a strong correlation between customers who used the mobile ordering app and those who did not return to the cafe. Specifically, he found that customers who used the mobile app were 20% less likely to return compared to those who did not.

While this correlation looks interesting, it does not necessarily mean that using the mobile app is causing customers not to return. Other factors could be at play driving both the use of the app and the decision not to return to the cafe. For example, customers who use the app may be more likely to be tech-savvy and prefer to order food from other online platforms, or they may be from a younger demographic that is more likely to seek out novelty and variety in their food choices or because of geographic locations and varied customer demographics.

These underlying factors could be the real reasons why these customers are not returning to the cafe, and the correlation with mobile app usage is just a coincidence.

To determine causality, Vedh would need to conduct additional analyses, such as experiments or observational studies, to establish a cause-and-effect relationship between mobile app usage and customer churn rather than just relying on correlation.

As the cafe managers shared their stories, Vedh picked up on some common themes. One issue was the consistency of the coffee quality across all the locations. Customers who enjoyed a particular type of coffee at one location were disappointed when they ordered the same coffee at another, which tasted different.

Vedh realized that the issue of inconsistent coffee quality was an anomaly, which could be one factor contributing to customer churn. So, he dug deeper and discovered that each location was ordering coffee beans from different suppliers, resulting in a taste difference.

In addition to identifying the anomaly, Vedh also checked the risks and uncertainty that the cafe managers faced. For example, he found the issue of running out of popular menu items during peak hours, leading customers to leave without buying anything. He also identified that new competitors had opened up nearby, putting pressure on their business. In general, we aim to narrow down our focus in a way that increases the likelihood of a positive outcome and decreases the likelihood of a negative one. Achieving this requires making better decisions; to do so, we need to reduce uncertainty. Vedh understood these by asking relevant questions about risk and uncertainty to address the problems that matter.

In the end, Vedh’s analysis revealed several key insights into why customers were leaving the cafe chain. Vedh was confident that with his attention to detail and understanding of the business problem and domain, he could provide valuable insights to the cafe chain. Thereby, Vedika's cafe chain was able to make targeted improvements to its menu, customer service, and marketing strategies, reducing customer churn and driving revenue growth.

[Analytical skills you need](#contents.xhtml#sc2_10a)

If we inspect Vedh’s experience, we could define data science as much more than simply analyzing data. The field of data science encompasses various job roles that demand diverse skill sets. Let us delve into a few critical skills that the above example suggested -

*   Understanding the application domain—It is crucial to understand the domain well to identify data problems. This requires being open-minded, curious, creative, and willing to ask many questions.
*   Bridging data users with the operational and frontline managers/users.
*   Designing the analytical solution with the last mile of adoption in mind—seeing the big picture of the business problem.
*   Focusing on the quality of data—understanding the limitations of the data they work with, measuring its accuracy, and providing recommendations for improving data quality in the future.
*   Preparing data for effective analysis.
*   Forming and testing the hypothesis.
*   Writing efficient and maintainable codes (R/Python or any other).

Leveraging statistics and ML techniques based on requirements.

Data storytelling—communicating the data insights using narratives and visualizations clearly and compellingly

In the last chapter, we will dig deeper into this. Now, let us understand what different types of analytics can be categorized into.

[Types of business analytics](#contents.xhtml#sc2_11a)

Introducing the four key types of data analytics can provide a valuable framework for understanding how data is analyzed and what insights can be gained. These four types—descriptive, diagnostic, predictive, and prescriptive analytics—build upon each other and offer unique benefits for organizations seeking to make data-driven decisions. By understanding these types of data analytics, businesses can better tailor their data analysis strategies to achieve their goals and improve decision-making processes.

[Descriptive analytics](#contents.xhtml#sc3_12a)

Descriptive analytics involves extracting patterns and insights from raw data, providing a succinct overview of what has occurred or is presently happening? It serves as the bedrock for the other three types of analytics. This is the most straightforward form of analysis and forms the basis for more advanced data analytics techniques. The initial step in adding value to businesses is depicted in the figure below, which involves descriptive analytics.

![](images/Figure1.5.jpg)

Figure 1.5: Value addition to organisations. 1st stage: Descriptive analytics

Let us say we have a digital banking platform and want to analyze how customers use it. We can use descriptive analytics to answer questions like:

*   How many customers log in to the digital banking platform each month?
*   What pages are customers visiting the most?
*   How much time are customers spending on the platform?
*   How does the platform usage compare month on month or year on year?

Using data collected from the platform, we can also calculate the following metrics:

*   Monthly active users: We can track the number of unique users logging in to the platform each month. For example, in January 2023, we had 70,000 unique users
*   Page views: We can count the number of times each page on the platform is viewed. In January 2023, the login page was viewed 110,000 times, while the account balance page was viewed 65,000 times
*   Average time on the platform: We can measure how long each user spends on the platform and calculate the average time. In January 2023, the average time spent on the platform was 6 minutes per user.
*   Monthly growth rate: We can compare the metrics month on month to see how the platform is growing. For example, in January 2023, we had a 2% increase in monthly active users compared to December 2022.

By analyzing these metrics, we can gain insights into how customers use the digital banking platform and identify areas for improvement.

Great! We got an overview of what descriptive analytics is.

Now let us consider another scenario—A pizza chain operates 2000 stores across different channels, including online, phone orders, and in-store purchases. The company has been collecting data on pizza sales for the past three years and wants to analyze its transaction data to gain insights into customer behavior and optimize its operations.

Now, the pizza chain can analyze its sales data over a specific period to determine which pizzas are the most popular, which channels customers use the most to order pizzas, and which days of the week or times of day have the highest sales.

For example, the pizza chain can analyze its sales data and find that the Pepperoni pizza is the most popular, accounting for 40% of all pizza sales, while the Veggie pizza is the least popular, accounting for only 6% of all pizza sales. They also find that online sales account for 70% of all pizza sales, while mobile and in-store sales account for 18% and 12%, respectively. The data shows that online sales are growing faster than phone or in-store sales, so the company may want to invest in improving its online ordering platform.

By looking at the number of pizzas sold daily, the pizza chain can identify the busiest days and times of the week, allowing it to schedule staff and optimize inventory. For example, the data shows that sales are highest on Friday and Saturday evenings between 5 pm and 8 pm, with an average of 6,500 pizzas sold during these peak hours. In that case, the company may want to increase staffing levels during those times to ensure that orders are processed quickly.

The pizza chain can gain valuable insights to inform data-driven decisions to improve its sales by analyzing its pizza sales data. For example, they can create targeted promotions or deals for their most popular pizzas, invest in improving their online and mobile ordering platforms, and increase staffing during peak hours to boost in-store sales. With the help of descriptive analytics, the pizza chain can better understand its customers' preferences, identify sales trends, and make informed decisions to drive business growth.

Great! Now let us look into how descriptive analytics is a valuable tool for marketing teams to analyze and evaluate the performance of their marketing campaigns. 

Marketing teams can gain valuable insights into their target audience's behavior and preferences by checking their click-through rates and social media engagement. For example, a marketing team launches a social media advertising campaign to promote a new product. By using descriptive analytics, the team can track metrics such as the number of ad impressions, click-through rates, and conversion rates. They can also monitor the number of social media followers, likes, comments, and shares to gauge audience engagement.

Based on these metrics, the marketing team can determine which aspects of the campaign were successful and which areas need improvement. For example, they may find that a particular type of social media post (for example, videos) received more engagement than others or that the conversion rate was higher when the campaign targeted a specific audience segment.

Descriptive analytics can also be used to segment the target audience based on demographic, geographic, and psychographic variables. By analyzing customer behavior and preferences data, marketing teams can create more targeted and personalized campaigns to improve conversion rates.

For instance, suppose a pizza chain with 2,000 stores across multiple channels wants to create a marketing campaign to promote a new line of vegan pizzas. Using descriptive analytics, the marketing team can segment the target audience based on factors such as age, location, dietary preferences, and past purchase behavior. They can then create targeted campaigns for each segment and track the performance of each campaign. This can help the team to refine their campaigns and maximize their return on investment.

Descriptive analytics provide valuable insights into a business's operations and are commonly displayed through data visualizations. Dashboards can be developed based on these descriptive analytics which stakeholders can use to track progress toward their goals and spot any anomalies. While descriptive analytics can stand alone as a helpful tool, they also serve as a crucial foundation for future analysis. They form the backbone of many businesses' day-to-day reporting and can be applied to various areas, such as annual revenue reports, inventory, and sales data. These reports are easily aggregated and offer a clear snapshot of a company's operations. 

[Diagnostic analytics](#contents.xhtml#sc3_13a)

Diagnostic analytics builds on descriptive analytics and takes it one step further by answering the question, why did this happen? This type of analysis attempts to locate the root cause of a particular trend or issue. It often involves comparing coexisting trends or movements, uncovering correlations between variables, and determining causal relationships where possible. Diagnostic analytics helps business users understand why something happened and provides valuable insights into the underlying factors contributing to a particular trend or issue. The below figure illustrates the second stage of business value addition to organizations: Diagnostic analytics.

![](images/Figure1.6.jpg)

Figure 1.6: Value addition to organisations. 2nd stage: Diagnostic analytics

Diagnostic analytics plays a crucial role in understanding the motivations behind customers' actions for companies that collect customer data. These insights can be leveraged to improve products and user experience (UX), fine-tune brand messaging, and ensure the alignment of products with target audiences.

Here are some potential diagnostic analytics questions with examples:

*   Why did the number of logins decrease last month?

By analyzing the data, we may discover that the decrease in platform usage is due to higher-than-usual errors during the login process. We can dive deeper into the root cause of these errors through diagnostic analytics by identifying specific factors contributing to them, such as mandatory password reset, updated security requirements, or technical issues with the platform. Addressing these underlying issues can improve the login process and enhance the overall customer experience, ultimately increasing customer engagement and retention on the platform.

Suppose a mobile banking platform offers a cashback reward program to its customers for making at least 10 transactions per month. The marketing team wants to analyze the program's effectiveness and impact on customer behavior.

Using diagnostic analytics, the team can ask questions such as:

*   Is the cashback program leading to increased transaction volumes among customers?
*   Are specific types of transactions more likely to result in the customer making 10 or more transactions per month?
*   Are there specific customer segments that are more likely to take advantage of the cashback program?

By analyzing transaction data and other customer data, the team might find that certain types of transactions, such as bill payments or online purchases, are more likely to contribute to customers making at least 10 transactions per month. They might also find that certain customer segments, such as younger or more tech-savvy customers, are more likely to participate in the cashback program.

By answering these questions, the team can make data-driven decisions on optimizing the cashback program to encourage more transactions and drive revenue growth for the mobile banking platform.

One use case of diagnostic analytics is identifying the reasons behind product demand. Continuing with the example of the pizza chain use case:

Why have online orders decreased in the last quarter?

*   Technical issues on the website or mobile app are causing frustration for customers and discouraging them from using the platform.
*   A decrease in marketing efforts for the online channel compared to other channels, such as in-store promotions or targeted advertising.
*   A decrease in the quality or variety of the menu offerings available for online ordering compared to in-store purchases leads to a decrease in customer interest.

Other questions the team can ask are:

*   Why do few specific locations have the lowest sales?
*   How are promotions and deals impacting overall sales?
*   What factors are impacting the frequency of repeat purchases?
*   What is causing the high number of returns or complaints about certain pizza toppings?
*   Why are in-store sales lower during certain times of the day?

Now, let us few examples of questions that marketing teams can ask when using diagnostic analytics to evaluate their campaigns:

*   Why is the click-through rate (CTR) on our Facebook ads lower than expected?
*   Which specific elements of our landing pages are leading to higher conversion rates?
*   Why are customers not completing the checkout process after adding items to their cart on our e-commerce site?
*   What are the common characteristics of customers who churn after signing up for our subscription service?
*   What elements of our social media strategy lead to higher engagement, and which do not resonate with our audience?

So, we have understood how diagnostic analytics allows you to uncover the underlying reasons and factors contributing to data trends.

[Predictive analytics](#contents.xhtml#sc3_14a)

Predictive analytics involves using data analysis, statistical models, and machine learning techniques to identify patterns and forecast potential future outcomes or events, providing insights into the question, what could happen in the future? Predictive analytics involves analyzing past and present data to predict future behavior. The figure below depicts the stage of predictive analytics in adding business value to organizations.

![](images/Figure1.8.jpg)

Figure 1.7: Value addition to organisations. 3rd stage: Predictive analytics

Predictive analytics has a wide range of applications across numerous industries, including but not limited to banking, retail, utilities, the public sector, healthcare, and manufacturing. It can be utilized to improve business operations, increase revenue, and manage risk effectively.

Using predictive analytics, it is possible to detect patterns in transaction data that may indicate fraudulent activity. By analyzing historical data and applying machine learning algorithms, banks can build predictive models that help identify potentially fraudulent transactions in real-time, enabling them to take action before any damage happens. A few features that machine learning algorithms can consider for predicting fraudulent transactions are determining the past behavior of the account, whether a device is a virtual machine or an emulator, confirming geolocation mismatches, device type/OS/screen resolution mismatches, and association with other devices and accounts.

A pizza chain can use predictive analytics to forecast pizza sales across channels at half an hour intervals. The company can analyze historical sales data, point of sales, consumer behavior, marketing campaign performance, and external factors, such as weather, competitor, and social media activity, to build a predictive model to forecast demand. For example, the company may predict that there will be an increase in sales of pepperoni pizza during a major sporting event and adjust its production and inventory levels accordingly to meet the anticipated demand. Predictive analytics can also help the company optimize its pricing strategies to maximize revenue and reduce waste by minimizing overproduction.

The below graph represents how ML accurately models a product’s price elasticity. So, for example, we can see how strongly the price drop of a product affected sales.

![](images/Figure1.9.png)

Figure 1.8: Demand increases when its price drops

Marketing teams use predictive analytics to segment customers into different groups based on their behavior and preferences. By analyzing customer data such as purchase history, browsing behavior, demographic information, and other relevant factors, the team can identify patterns and predict what types of products or services different customers are most likely to be interested in. Then, they can tailor their marketing campaigns to each segment, creating personalized content and offers that are more likely to resonate with each group. 

For example, a marketing team might use predictive analytics to segment customers into groups based on their likelihood to purchase high-end products, their preferred channels for communication, or their interest in certain types of promotions. This can help the team optimize their marketing efforts, improve customer engagement, and eventually drive more conversions.

[Prescriptive analytics](#contents.xhtml#sc3_15a)

Prescriptive analytics involves using data to identify the best course of action. This type of analysis takes into account all relevant factors and provides recommendations for the next steps. As a result, prescriptive analytics is a valuable tool for making data-driven decisions. It helps answer the question of what steps to take next? The fourth and final stage of adding business value to organizations is presented in the figure below, which depicts prescriptive analytics.

![](images/Figure1.10.jpg)

Figure 1.9: Value addition to organisations. 4th stage: Prescriptive analytics

Prescriptive analytics can be applied to pricing strategies in marketing. For example, a company may use historical sales data and competitive pricing information to develop a pricing model that maximizes revenue and profit margins. The company can test various pricing scenarios using prescriptive analytics to determine the optimal pricing strategy. The model may take into account factors such as seasonality, product demand, customer behavior, and competitive landscape. Based on these factors, the model may recommend different pricing strategies for different products, markets, or customer segments. The company can use these recommendations to make data-driven decisions on pricing and adjust its pricing strategy over time as the market conditions change.

![](images/Figure1.11.png)

Figure 1.10: Illustration of social media platform recommendations

The above figure shows an illustration of social media recommendations. Social media platforms can use recommendation engines to provide users with prescriptive recommendations for what content to consume next based on their past behavior. For instance, if a user is interested in fitness content, the recommendation engine may suggest workout videos or healthy recipe posts from health and wellness influencers they follow. Using prescriptive analytics, social media platforms can improve user engagement and increase time spent on the platform, leading to higher revenue through advertising and other monetization strategies.

Although algorithms can offer data-driven guidance; they cannot substitute for human judgment. Prescriptive analytics should be viewed as a tool to support decisions and strategies rather than replace human discernment. Nevertheless, it is essential to remember that your judgment is critical to providing context and setting boundaries for algorithmic outputs.

Whether utilizing an algorithm or not, human judgment remains essential as the accuracy and impartiality of an algorithm depend solely on the quality of data it is trained with.

[Conclusion](#contents.xhtml#sc2_16a)

This chapter discussed how data-driven organizations leverage data science to create a better customer experience and make faster and better decisions. However, to fully realize the potential of data science, organizations need to identify the right business problems to solve. While data analysis and coding skills are important for data scientists, they must also have storytelling skills, critical thinking, and an eye for visual displays. In addition, understanding the four primary types of data analytics—descriptive, diagnostic, predictive, and prescriptive is important to gain the most valuable insights from the data.

Join our book’s Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/fm1.png)

# [CHAPTER 2R Basics](#contents.xhtml#ch02a)

[Introduction](#contents.xhtml#sc2_17a)

This chapter will briefly give an overview of R language and R studio interfaces. You will learn how to install and load packages and create different types of R objects, such as vectors, matrices, lists, arrays, and data frames. R has an extensive collection of built-in functions. This language also has its own help page, which can be accessed to learn more about the functions. You will understand how to create a function on your own as well. Next, you will learn to load a dataset in R and export any data to your system. This chapter will make you comfortable exploring your data in the next stage.

[Structure](#contents.xhtml#sc2_18a)

You will cover the following topics in this chapter:

*   RStudio interfaces 
    *   R as a calculator
    *   Keyboard shortcuts
*   Packages 
    *   Installing packages
    *   Loading packages
*   Working directories
*   Objects 
    *   Vectors
    *   Attributes
    *   Matrices
    *   Arrays
    *   Class
    *   Lists
    *   DataFrames
*   Functions
*   Getting help with help pages
*   Loading data
*   Saving data
*   R conventions

[Objectives](#contents.xhtml#sc2_19a)

By the end of this chapter, you will have mastered the basics of R, giving you the skills to efficiently use R for data analysis.This chapter will provide a comprehensive overview of essential concepts required for working with R, including RStudio interfaces, packages, working directories, different R objects, functions, loading and saving data, and R conventions.

[RStudio interfaces](#contents.xhtml#sc2_20a)

R is a programming language that can handle large datasets, perform complex calculations, and create visualizations to help you make sense of your data. It is open-source and free to use, making it accessible to anyone interested in statistical computing. It has a large and active community of users and developers who contribute to developing and maintaining its various packages and libraries. The following figure shows a few features of R programming:

![](images/Figure2.1.png)

Figure 2.1: Features of R

When you first open R, it can seem overwhelming. That is where RStudio comes in. RStudio is an integrated development environment (IDE) that makes working with R more streamlined and accessible for users of all levels.

The RStudio interface has four main panels:

*   Console:You type commands and see the output. 
*   Script editor: You type out commands and save them to a file. You can also submit the commands to run in the console.
*   Environment/History: You view all active objects and history to track all commands run in the console
*   Files/Plots/Packages/Help

Upon installing and launching RStudio, the following interface will be displayed:

![](images/Figure2.2.png)

Figure 2.2: RStudio interface

You can also add and remove panes by going to Tools| Global Options| Pane Layout.

R as a calculator

Now, let us get into the story of Aarya, who wants to use R to analyze the data of her Netflix usage. She starts by using R as a calculator. She wants to figure out how many hours she has spent in total, viewing Netflix movies and TV series over the past week. The following is the information Aarya noted down:

*   She watched two TV shows, each with 12 episodes. Each episode is 30 minutes long.
*   Also, she watched three 2-hour movies.

![](images/Figure2.3.jpg)

Figure 2.3: An illustration of Aarya analyzing her Netflix data

The above figure illustrates Aarya analyzing her Netflix data. Aarya uses simple arithmetic operations in R to calculate the total number of hours.

For TV shows,

Aarya watched 12 x 2 = 24 episodes. Each episode is 30 minutes, so the total time spent watching TV shows is 24 x 30 = 720 minutes. To convert minutes to hours, Aarya can divide by 60. So, the total time spent watching TV will be:

720 / 60 = 12 hours.

For movies,

Aarya watched a total of 3 x 2 = 6 hours. To calculate the total time spent watching TV shows and movies, Aarya can add the hours together: 12 + 6 = 18 hours. The following figure shows the calculations in the R console:

![](images/Figure2.4.png)

Figure 2.4: Basic calculations at the R console

So, Aarya calculated the total number of hours spent watching TV shows and movies on Netflix using simple arithmetic operations in R.

Keyboard shortcuts

Understanding the keyboard shortcuts for RStudio will help you program faster. You may access dozens of helpful shortcuts provided by RStudio through the menu at the top: Tools| Keyboard Shortcuts Help (Shortcut: Alt + Shift + K) as shown below.

![](images/Figure2.5.jpg)

Figure 2.5: R Shortcuts

[Table 2.1](#ch02.xhtml#tab2-1) presents a compilation of a few essential RStudio shortcuts.

| Shortcut || Action |
| --- | --- |
| Ctrl + Enter || Run current line/selected code |
| Ctrl + Shift + N || Create a new R script file |
| Ctrl + Shift + C || Comment or uncomment the current line or selected code |
| Ctrl + Shift + D || Duplicate the current line or selected code |
| Ctrl + 1 || Move cursor to script editor |
| Ctrl + 2 || Move cursor to console |
| Ctrl + L || Clear console |
| Ctrl + Shift + H || Change working directory |
| Ctrl + Shift + M || Insert %>% (pipe operator) |

Table 2.1: Commonly used R keyboard shortcuts

Learning and getting comfortable with shortcut keys is worth the time to increase your productivity and workflow efficiency. If you want to personalize the look, RStudio has a ton of possibilities. Explore the numerous choices by going to Tools| Global Options| Appearance.

[Packages](#contents.xhtml#sc2_21a)

When you download and install R, it comes with a default set of functions that can be used for various purposes. However, as the global R community develops new functions and features, incorporating them into the core software package has become impractical. Instead, many functions are bundled into packages that can be downloaded and installed as needed to address this.

R packages are a collection of functions, data sets, and documentation designed to work together seamlessly. For instance, a few packages are designed to wrangle data, and a few others are designed to visualize it.

For example, installing a package is like ordering a new feature for your car, such as a navigation system. You cannot use it right away since you need to install it first. Once the new feature is installed in your car, you can turn it on and use it.

Similarly, to use a new R package, you need to install it on your computer first using the install.packages() function. Also, you need to load the package into your working session using the library() function to access the new functions and capabilities it provides.

Just like you can have multiple features installed in your car but only turn on the ones you need at a given time, you can install multiple R packages on your computer but only load the ones you need for a specific project. The following figure shows an illustration of the car display system and navigation app in the car display:

![](images/Figure2.6.png)

Figure 2.6: Display system and navigation app in the car display

For example, to install the lubridate package (having useful functions for dealing with dates), you simply pass the name of the package, lubridate, as a string argument to the function:

1.  \# install the lubridate package 
2.  install.packages(“lubridate”)

Once the package is downloaded and installed, you can load it into your R session using the library() function:

1.  \# load the lubridate package
2.  library(lubridate)

Once loaded, you can use the functions the package provides in your code just as you would with any other R function. 

| Note: The hashtag (#) in R is a commenting symbol. To clarify what each portion of your code does, add comments to it. Others (and your future self!) will find it simpler to understand your code if you do this. |
| --- |

Several good practices can help you work more efficiently and effectively using packages.

*   Load packages at the beginning of your script: It is a good idea to load all the packages you will be using at the beginning of your script. This will ensure that all the necessary packages are installed and loaded before your code runs, avoiding any potential errors or issues arising from missing dependencies.
*   Update packages regularly: The R community constantly updates and improves packages, so keeping your packages updated is important. You can do this by running the update.packages() function periodically, which will check for updates to your installed packages and install any new versions that are available.
*   Be mindful of package dependencies: Some packages may have dependencies on other packages, meaning you need to have those packages installed and loaded in order to use the package you want.
*   Avoid namespace conflicts: You may run into namespace conflicts if you use functions from multiple packages with the same name. To avoid this, you can use the ::operator to specify which package’s function you want to use. For example, instead of using summarize(), you could use dplyr::summarize() to specify that you want to use the summarize() function from the dplyr package.

[Working directories](#contents.xhtml#sc2_22a)

When working with R, keeping your files organized is essential. This means creating a folder for each project you are working on and keeping related files within that folder. The R working directory is the folder that R starts in by default. 

R uses a designated folder on your computer, called a working directory, to locate files related to a specific project. Here, R looks for files to load and saves files. On different computers, the location of your working directory may be different, and you can only have one working directory open at once. To determine the current working directory, you can run the following code:

1.  \# view the current working directory
2.  getwd()
3.  \## “C:/Users/Hp/Documents”

When organizing your datasets, you have two options: first, you can put your files into your working directory, and second, to change your working directory to the folder where your files are stored. You can modify your working directory to any folder on your computer by using the function setwd() and specifying the file path of the new working directory.Let us take a look at the following example:

1.  \# set working directory
2.  setwd(“E:/Book\_Project”)

From the menu bar, you can click on Session| Set Working Directory| Choose Directory to move your working directory. To look into the files in the working directory, you can use the function list.files().

It is essential to be mindful of your working directory when reading and writing files in R. If you are not working in the correct folder, you may encounter errors or overwrite existing files. Keeping your files organized and setting your working directory appropriately ensures that your R code is reproducible and easy to share with others. 

[Objects](#contents.xhtml#sc2_23a)

Let us go back to Aarya’s example. To analyze her Netflix usage, Aarya must first comprehend the concept of objects in R. An object is a way to save data by storing it inside a designated name that can be used to recall the stored data. All data is stored in objects, ranging from simple numbers or character strings to complex structures like statistical analysis summaries and plots.

To proceed with her analysis, Aarya created three distinct R objects called hours\_watched\_movies, hours\_watched\_tv, and total\_hours\_watched to save the number of hours she spent watching movies, TV shows, and the total time spent watching Netflix respectively. With these objects, Aarya can perform numerous operations to analyze her data efficiently. To assign a name to a number, you use the assignment operator: <-(no space between < and \-). Take a look at the following example:

1.  \# define hours\_watched\_movies
2.  hours\_watched\_movies<- 6
3.  
4.  \# store the time spent (in hours) watching TV shows
5.  hours\_watched\_tv<- 12
6.  
7.  \# save total time spent (in hours) into total\_hours\_watched
8.  total\_hours\_watched<- 18

To check what is stored in the total\_hours\_watched object, Aarya can simply type its name, total\_hours\_watched, in the R console, and it will display the object value on the following line:

1.  \# display the value stored in total\_hours\_watched
2.  total\_hours\_watched
3.  \## 18 
    
    | Note: Throughout the book, the output of R code will be followed by ##. |
    | --- |
    

Now, let us see how Aarya creates various R objects and assigns values to them to analyze her data efficiently.

[Vectors](#contents.xhtml#sc3_24a)

A vector is a collection of elements of the same data type. Vectors can contain either numbers, characters, or logicalsbut not a mixture of these types of data. Vectors are R’s most basic data structure and are used for many different purposes, such as storing data or performing mathematical operations. A vector can be considered as a one-dimensional array, with each element in the vector having an index or position. Understanding how to create and manipulate vectors is essential, as they are the building blocks for more complex data structures and analysis. Let us know more about some of these types of vectors.

Numeric vector

Aarya can use a numeric vector to store the duration of each movie or TV show she watched on Netflix. For example, she can create a numeric vector named movie\_durations and assign the duration of each movie she watched to it. For example:

1.  \# create a vector of durations of movies watched
2.  movie\_durations<- c(98, 109,124,138,115, 149)
3.  
4.  \# print movie\_durations
5.  movie\_durations
6.  \## 98 109 124 138 115 149

This creates a numeric vector named movie\_durations with 5 elements representing the duration of each movie she watched in minutes. The c() creates a vector or concatenates two or more vectors together. The c() function stands for combine or concatenate, and is one of the most commonly used functions in R.

Character vector

A character vector stores a sequence of character values. A character value is any text you want to store, such as words, sentences, or individual characters. You can use the c() function to create a character vector by enclosing the values in quotation marks. For instance, Aarya creates a character vector to store the movies she watched:

1.  \# create a vector of movies watched
2.  movie\_titles<- c(“Rush Hour”,”Knight and Day”, “The Notebook”, “Shutter Island”,”Now you see me”, “The Da Vinci Code”)
3.  
4.  \# print movie\_titles
5.  movie\_titles
6.  \## “Rush Hour” “Knight and Day” “The Notebook” 
7.  \## “Shutter Island” “Now you see me” “The Da Vinci Code” 
    
    | Note: Strings are the individual components of a character vector. So, if you put numbers surrounded by quotes, for example: 1, it will only be considered a character vector. Anything that is surrounded by quotes is treated as a character string. |
    | --- |
    

Now, if Aarya wants to find out how many movies she watched last month she can use the length() function to identify how many elements are there in that vector, as shown in the following example:

1.  \# count the number of elements in the movie\_titles
2.  num\_movie\_titles<- length(movie\_titles)
3.  
4.  \# print the result
5.  cat(“Number of movies watched on Netflix last month:”, num\_movie\_titles )
6.  \## Number of movies watched on Netflix last month: 6

Logical vector

R’s form of Boolean data is a logical vector that stores TRUEs and FALSEs. A vector indicating whether Aarya watched a movie on a given day is displayed as follows:

1.  \# create a logical vector watched
2.  watched <- c(TRUE, FALSE, TRUE, FALSE, TRUE, TRUE, FALSE)
3.  
4.  \# print watched
5.  watched 
6.  \## TRUE FALSE TRUE FALSE TRUE TRUE FALSE

For a vector indicating whether Aarya watched a movie in a given genre:

1.  \# create a vector genre
2.  genre <- c(“Action”, “Action”, “Romance”, “Thriller”, “Thriller”, “Thriller”)
3.  
4.  \# check whether a movie belongs to a “Thriller” or not
5.  watched\_thriller<- genre == “Thriller”
6.  
7.  \# print watched\_thriller
8.  watched\_thriller
9.  \## FALSE FALSEFALSE TRUETRUETRUE

For a vector indicating whether Aarya gave a thumbs up or thumbs down rating to a movie or TV show:

1.  \# create a vector rating
2.  rating <- c(“Thumbs Up”, “Thumbs Down”, “Thumbs Down”, “Thumbs Up”, “Thumbs Up”, “Thumbs Up”)
3.  
4.  \# check whether a movie is rated as “Thumbs Up” or not
5.  watched\_good<- rating == “Thumbs Up”
6.  
7.  \# print watched\_good
8.  watched\_good
9.  \## TRUE FALSE FALSE TRUETRUETRUE

The most common logical operators used in R are:

| Operators || Description |
| --- | --- |
| \== || equal to |
| != || not equal to |
| < || less than |
| \> || greater than |
| <= || less than or equal to |
| \>= || greater than or equal to |
| & || logical AND |
| | || logical OR |
| ! || logical NOT (negation) |

Table 2.2: Logical operators used in R

[Attributes](#contents.xhtml#sc3_25a)

Attributes are additional information associated with an R object. They provide metadata about an object, such as its name, dimension, class, or other information describing its properties. Attributes do not affect an object’s behavior but can help organize and manipulate data.

For example, when Aarya creates a vector or matrix, she can assign attributes to the object to describe its properties. She can use the names() to assign names to the elements of a vector, the dim() to assign dimensions to a matrix, or the class() function to assign a class to an object, indicating its data type or structure.

By using attributes, Aarya can keep track of the structure and properties of her data, which can help her to manipulate and analyze it more effectively. Attributes also play an essential role in R programming, as many functions and operations use them to determine how to handle or transform data. The different types of attributes are further discussed.

Names

The names() function assigns or retrieves names for the elements of a vector, list, or array. It can be a valuable tool for organizing data and making it easier to understand.

For example, let us create a vector that contains all the TV shows she watched in the past week and their respective time spent watching them:

1.  \# TV Shows watched
2.  tv\_shows\_names<- c(“Breaking Bad”, “Money Heist”, “The office”, “Suits”, “The Last Kingdom”)
3.  
4.  \# time spent on watching each TV show in minutes
5.  duration <- c(120, 142, 64, 90, 185)
6.  
7.  \# adding and accessing attributes
8.  \# assign names to duration
9.  names(duration) <- tv\_shows\_names

Now, duration has a name attribute:

1.  \# print names and attributes of the vector duration
2.  names(duration)
3.  \## “Breaking Bad” “Money Heist” “The office” “Suits” ## “The Last Kingdom”
4.  
5.  attributes(duration)
6.  \## $names
7.  \## “Breaking Bad” “Money Heist” “The office” “Suits” ## “The Last Kingdom”

R will display the names of movies above the elements of duration whenever we print the duration vector:

1.  \# print duration
2.  duration
3.  \## Breaking Bad Money Heist The office Suits The Last Kingdom 
4.  \## 120 142 64 90 185

Dim

The dim()function is used to convert a vector into an n-dimensional array by assigning it a dimensions attribute. To do this, you can set the dim() to a vector of length n, where n is the number of dimensions you want the array to have. This allows you to reshape and manipulate the data stored in the vector to fit into a specific matrix or array structure.

For example, Aarya wants to transform her duration vector into a 5 X 1 matrix (5 rows and 1 column). She creates that using the following code:

1.  \# set the dimension of the vector
2.  dim(duration) <- c(5, 1)
3.  
4.  \# print duration vector
5.  duration
6.  \## \[,1\]
7.  \## \[1,\] 120
8.  \## \[2,\] 142
9.  \## \[3,\] 64
10.  \## \[4,\] 90
11.  \## \[5,\] 185

R always considers the first value in dim for the number of rows, and the second is the number of columns. In any R operationsthat deals with both rows and columns, rows always come first.

[Matrices](#contents.xhtml#sc3_26a)

Matrices are two-dimensional arrays that can hold only the same kind of data. You may think of a matrix as a collection of vectors that are all of the same length and arranged in a rectangular pattern. The matrix() method is used to build matrices.

You use the matrix() to create a matrix and mention the number of rows by setting nrow argument to a number. Then, matrix() will organize your vector into a matrix with the number of rows mentioned. For example, let us create a matrix with a numeric vector and setting nrow to 3:

1.  \# create a matrix 
2.  simple\_matrix<- matrix(1:6, nrow = 3)
3.  
4.  \# print simple\_matrix
5.  simple\_matrix
6.  \## \[,1\] \[,2\]
7.  \## \[1,\] 1 4
8.  \## \[2,\] 2 5
9.  \## \[3,\] 3 6

Suppose Aarya has tracked the number of hours she has spent watching different TV series over Saturday and Sunday. Next, Aarya creates a matrix to display her data:

1.  \# create a vector with the duration of TV shows in hours
2.  tv\_duration<-c(2,1,2,3)
3.  
4.  \# create a matrix with a number of hours spent watching each TV shows
5.  tv\_matrix<-matrix(tv\_duration,nrow=2,ncol=2,byrow=TRUE)
6.  
7.  \# assign row and column names
8.  \# setting the vector tv\_shows\_names vector which we created earlier as rownames
9.  
10.  rownames(tv\_matrix)<-c(“BreakingBad”,”Money Heist”)
11.  
12.  \# assign column names
13.  colnames(tv\_matrix)<-c(“Saturday”,”Sunday”)
14.  
15.  \# print tv\_matrix
16.  tv\_matrix
17.  \## Saturday Sunday
18.  \## Breaking Bad 2 1
19.  \## Money Heist 2 3

By default, matrix() fills up the matrix by column, and if you want to fill it up row by row, you could set the argument byrow as TRUE. Now Aarya may use the dim() method to obtain the matrix’s dimensions:

1.  \# get the dimensions of the matrix
2.  dim(tv\_matrix)
3.  \## 2 2

The output shows tv\_matrix has 2 rows and 2 columns (The first value is the number of rows, and the second one is the number of columns).

[Arrays](#contents.xhtml#sc3_27a)

An array is a multi-dimensional object with more than two dimensions that can contain data of any type and is comparable to a matrix. Compared to vectors or matrices, Aarya can store and analyze her Netflix data using arrays in even more intricate ways.

For instance, let us say Aarya wants to create an array to save the number of minutes she watched Netflix every day over the course of the previous month, split down by genre and device. She can use the array() to construct an array to store this data. The data that Aarya wants to save in the array is the first parameter to the array(). The array’s dimensions are specified by a numeric vector in the second argument:

1.  \# create a 3-dimensional array
2.  duration\_array<- array(data = c(30:39,50:59,20:29), 
3.   dim = c(5, 2, 3))
4.  
5.  \# note: the : operator in R is used to create a sequence of numbers. It takes two values, a starting value and an ending value, and generates a sequence of numbers that includes all the integers between those two values, inclusive.
6.  
7.  \# print duration\_array
8.  duration\_array
9.  
10.  \## , , 1
11.  ##
12.  \## \[,1\] \[,2\]
13.  ##\[1,\] 30 35
14.  ##\[2,\] 31 36
15.  ##\[3,\] 32 37
16.  ##\[4,\] 33 38
17.  ##\[5,\] 34 39
18.  ##
19.  \## , , 2
20.  ##
21.  \## \[,1\] \[,2\]
22.  ##\[1,\] 50 55
23.  ##\[2,\] 51 56
24.  ##\[3,\] 52 57
25.  ##\[4,\] 53 58
26.  ##\[5,\] 54 59
27.  ##
28.  \## , , 3
29.  ##
30.  \## \[,1\] \[,2\]
31.  ##\[1,\] 20 25
32.  ##\[2,\] 21 26
33.  ##\[3,\] 22 27
34.  ##\[4,\] 23 28
35.  ##\[5,\] 24 29

Now, let us see how the results look by adding dimension names to the array:

1.  \# assign names to the dimensions of the array
2.  dimnames(duration\_array ) <- list(days = c(“Week 1”, “Week 2”, “Week 3”, “Week 4”, “Week 5”),
3.   genre = c(“Comedy”, “Action”),
4.   device = c(“TV”, “Laptop”, “Phone”))
5.  
6.  
7.  \# Print the array
8.  duration\_array
9.  \## , ,device = TV
10.  ##
11.  \## genre
12.  ##days Comedy Action
13.  \## Week 1 30 35
14.  \## Week 2 31 36
15.  \## Week 3 32 37
16.  \## Week 4 33 38
17.  \## Week 5 34 39
18.  ##
19.  \## , ,device = Laptop
20.  ##
21.  \## genre
22.  ##days Comedy Action
23.  \## Week 1 50 55
24.  \## Week 2 51 56
25.  \## Week 3 52 57
26.  \## Week 4 53 58
27.  \## Week 5 54 59
28.  ##
29.  \## , ,device = Phone
30.  ##
31.  \## genre
32.  ##days Comedy Action
33.  \## Week 1 20 25
34.  \## Week 2 21 26
35.  \## Week 3 22 27
36.  \## Week 4 23 28
37.  \## Week 5 24 29

As we can see here, Aarya created a 3-dimensional array, called duration\_array to store her Netflix data. The array has 5 rows (one for each week), 2 columns (one for comedy, one for action), and 3layers (one for each device used to watch Netflix).She assigned names to each dimension of the array using the dimnames().

[Class](#contents.xhtml#sc3_28a)

Each object in R has a class attribute that identifies the type of object it is. This is crucial since R has a wide range of functions that may be used with various object types. For instance, you can use the mean() function to calculate the mean of a numeric vector, but you cannot use it to calculate the mean of a character vector. This is because it is illogical to take the mean of character strings.

A class may automatically be assigned to an object by R when we create them. For instance, R will assign it a class ofnumeric when you create a vector of numbers using the c() function. The class() function also allows you to assign a class to an object directly. The table below shows the functions helpful in testing the type of data stored in a variable and converting variables between different data types if necessary:

| Data type || Logical test || Coercing function |
| --- | --- | --- |
| Numeric || is.numeric() || as.numeric() |
| Integer || is.integer() || as.integer() |
| Character || is.character() || as.character() |
| Logical || is.logical() || as.logical() |
| Factor || is.factor() || as.factor() |
| Date || is.Date() || as.Date() |
| POSIXct || is.POSIXct() || as.POSIXct() |
| Matrix || is.matrix() || as.matrix() |
| Array || is.array() || as.array() |

Table 2.3: Logical test and coercing functions of different data types

The is.functions return a logical value (TRUE or FALSE) indicating whether the input variable is of the specified type. The as.functions coerce the input variable to the specified type. It is important to note that coercion can result in data loss or unexpected behavior, so it should be used with caution.

| Note: You can also use c() to concatenate vectors of different data types, such as numeric and character vectors. However, when you concatenate vectors of different data types, R will convert all the values to a single data type. |
| --- |

Dates and times

R provides a variety of classes for working with dates and times, including Date,POSIXct, and POSIXlt. These classes can enable Aarya to store and manipulate date and time values, making it easier to analyze her Netflix usage over time.

For instance, Aarya can create a date object for the date she started watching a particular TV show by using the as.Date() function. She can also create a POSIXct object for the time of day she started watching a particular episode using the as.POSIXct(). Once created, she can perform various operations on these objects, such as extracting the month or year using the format() function or calculating the time elapsed between two dates using the difftime() function. We will dive deeper into date functionalities in [Chapter 5](#ch05.xhtml), Working with Dates.

Now, let us say Aarya wants to calculate the total amount of time she spent watching TV shows in the month of January. She can start by creating a POSIXct vector containing the start times of all the shows she watched in January. She can do this using the as.POSIXct() function:

1.   \# Start time of TV shows watched
2.  jan\_start\_times<\-as.POSIXct(c(“2023\-01-07 14:00:00”, “2023\-01-08 15:30:00”, “2023\-01-14 18:00:00”, “2023\-01-22 19:00:00”))

Next, she can create a POSIXct vector containing the end times of all the shows she watched in January:

1.  \# End time of TV shows watched
2.  jan\_end\_times<\-as.POSIXct(c(“2023\-01-07 16:00:00”, “2023\-01-08 16:30:00”, “2023\-01-14 20:00:00”, “2023\-01-22 22:00:00”))

Now, she can calculate the duration of each show by subtracting the start time from the end time, like so:

1.  \# calculate time spent in each show
2.  jan\_durations<- jan\_end\_times - jan\_start\_times
3.  
4.  \# print jan\_durations
5.  jan\_durations
6.  \## Time differences in hours
7.  \## 2 1 2 3

Finally, she can sum up the durations to get the total amount of time she spent watching TV shows in January:

1.  \# calculate the total duration
2.  jan\_total\_duration<- sum(jan\_durations)
3.  
4.  \# print jan\_total\_duration
5.  jan\_total\_duration
6.  \## Time difference of 8 hours

In this way, Aarya can use dates and times to perform fundamental calculations and analysis on her Netflix usage over time.

Factors

In R, categorical data is represented using factors. Movie genres or ratings are examples of categorical data within a fixed set of possible values. Each number in R’s representation of factors indicates a different category.

Factors are an efficient way to store character values because they use a vector of integers to represent the unique values, with each value stored only once. This storage method reduces the memory used to store the data while maintaining the original character information. For instance, Aarya has a column for movie genres and ratings in her Netflix data. With the help of factor() function, she may turn these columns into factors. Let us say Aarya has the following data:

1.  \# create a vector Movie Genres
2.  movie\_genres<- c(“Action”, “Action”, “Romance”, “Thriller”, “Thriller”, “Thriller”)
3.  
4.  \# class of movie\_genres
5.  class(movie\_genres)
6.  \## “character”
7.  
8.  \# create a vector of movie rating
9.  movie\_ratings<- c(4,3,2,5,5,3)
10.  
11.  \# class of movie ratings 
12.  class(movie\_ratings)
13.  \## “numeric”

Aarya can create factors from these vectors as follows:

1.  \# Create factor for Movie Genres
2.  movie\_genres\_factor<- factor(movie\_genres)
3.  
4.  \# class of movie ratings 
5.  class(movie\_genres\_factor )
6.  \## “factor”
7.  
8.  \# Create factor for movie rating
9.  movie\_ratings\_factor<- factor(movie\_ratings)
10.  
11.  \# class of movie ratings 
12.  class(movie\_ratings\_factor)
13.  \## “factor”

In this example, Aarya has created two factors: movie\_genres\_factor and movie\_ratings\_factor. R will assign an integer value to each unique value in the factor. Aarya can view the unique values in each factor using the levels() function:

1.  \# View unique values in Movie Genres factor
2.  levels(movie\_genres\_factor)
3.  \## “Action”“Romance”“Thriller”
4.  
5.  \# View unique values in Movie Rating factor
6.  levels(movie\_ratings\_factor)
7.  \## “2”“3”“4”“5”

Aarya can also assign custom labels to each level using the levels()function:

1.  \# Assign custom labels to Movie Genres factor
2.  levels(movie\_genres\_factor) <- c(“Act”, “Act”, “Rom”, “Thrill”, “Thrill”)
3.  
4.  \# Assign custom labels to Movie Ratings factor
5.  levels(movie\_ratings\_factor) <- c(“four”,”three”,”two”,”five”,”five”,”three”)

Factors can also be ordered or unordered. In Aarya’s example, she might want to order the movie according to ratings. She can create an ordered factor using the ordered() function:

1.  \# Create ordered factor for movie rating
2.  movie\_ratings\_ordered\_factor<- ordered(movie\_ratings, levels = c(2, 3, 4, 5))
3.  
4.  \# print movie\_ratings\_ordered\_factor
5.  movie\_ratings\_ordered\_factor
6.  \## 4 3 2 5 5 3
7.  \## Levels: 2 < 3 < 4 < 5

The levels = c(2, 3, 4, 5) argument specifies the order of the levels in the factor. In this case, we have specified the levels in ascending order of their ratings, from 2 to 5:

1.  \# View ordered levels in movie Rating factor
2.  levels(movie\_ratings\_ordered\_factor )
3.  \## “2”“3”“4”“5”

Factors are an essential data type in R for representing categorical data, and the factor()function can easily convert character vectors to factors.

[Lists](#contents.xhtml#sc3_29a)

A list is a beneficial data structure in R that can hold any collection of R objects. In contrast to vectors and matrices, the objects in lists allow different types, including character, numeric, and even other lists. Because of this, lists are very versatile and helpful for various tasks, such as arranging intricate data structures or developing custom functions. Aarya can use lists to organize her Netflix data in a meaningful way, as we can see in the following list:

1.  \# Create a list of vectors
2.  movies\_list<- list(
3.  movie\_names = c(“Inception”, “The Dark Knight”, “Edge of Tomorrow”),
4.  movie\_durations = c(148, 152, 113),
5.   genre = factor(c(“Sci-fi”, “Action”,”Sci-fi”)), 
6.   ratings = factor(c(3,5,4), ordered = TRUE, levels = c(3,4,5))
7.  )
8.  
9.  \# Print the list
10.  movies\_list
11.  \## $movie\_names
12.  ##\[1\] “Inception” “The Dark Knight” “Edge of Tomorrow”
13.  ##
14.  ##$movie\_durations
15.  ##\[1\] 148 152 113
16.  ##
17.  ##$genre
18.  ##\[1\] Sci-fi Action Sci-fi
19.  ##Levels: Action Sci-fi
20.  
21.  $ratings
22.  \[1\] 3 5 4
23.  Levels: 3 < 4 < 5

In this example, we created a list called movies\_list which contains four vectors of different types—character, numeric, factor, and ordered factor. We used the list() function to create the list and assigned names to each vector using the same syntax. 

[DataFrames](#contents.xhtml#sc3_30a)

A DataFrame is a table-like structure that contains rows and columns. It is nothing but a two-dimensional version of a list. Each column can have a different data type and must have a name. DataFrames are commonly used to store and manipulate data because they are easy to work with and allow for many operations, such as filtering, sorting, and summarizing data. Let us get familiar with DataFrames, one of the most commonly used R objects.

Using Aarya’s Netflix data, she can create a DataFrame with the columns movie\_names, movie\_durations, and watched\_scifi. Each vector has to be of the same length. She uses the data.frame() to create the DataFrame. Let us take a look at the following data frame figure for reference:

![](images/Figure2.7.png)

Figure 2.7: Representation of DataFrames in R

1.  \# create a DataFrame
2.  netflix\_df<-data.frame(
3.  movie\_names=c(“Inception”,”The Dark Knight”,”Edge of Tomorrow”),
4.  movie\_durations=c(148,152,113),
5.  watched\_scifi=c(TRUE,FALSE,TRUE)
6.  )
7.  
8.  \# print netflix\_df
9.  netflix\_df
10.  \## movie\_namesmovie\_durationswatched\_scifi
11.  \## Inception 148 TRUE
12.  \## The Dark Knight 152 FALSE
13.  \## Edge of Tomorrow 113 TRUE
14.  
15.  \# class of the netflix\_df
16.  class(netflix\_df)
17.  \## “data.frame”

The str() stands for structure and is used to display the structure of an R object. When applied to a data frame, str() provides a compact way to display the internal structure of the data frame. It shows the variable names, data types, and the first few values of each variable in the data frame. If we apply str(netflix\_df) in the R console, it will show the following structure of the data frame:

1.  \# structure of the data frame netflix\_df
2.  str(netflix\_df)
3.  
4.  \## ‘data.frame’: 3 obs. of 3 variables:
5.  \## $ movie\_names: chr “Inception” “The Dark Knight” “Edge of ##Tomorrow”
6.  \## $ movie\_durations: num 148 152 113
7.  \## $ watched\_scifi: logi TRUE FALSE TRUE

The output shows that netflix\_df is a data frame with three observations and variables. The first variable is movie\_names is a character vector, movie\_durations is a numeric variable, and watched\_scifi is a logical variable. Then she creates another data frame to store the Netflix data usage of a few of her friends as well:

1.  \# create data frame
2.  netflix\_data<-data.frame(
3.  name=c(“Aarya”,”Vedh”,”Vedika”,”Raj”,”Simran”,”Rahul”),
4.  age=c(25,27,26,24,28,25),
5.  gender=c(“F”,”M”,”F”,”M”,”F”,”M”),
6.  location=c(“Kolkata”,”Bangalore”,”Bangalore”,”Pune”,  
    ”Chandigarh”,”Mumbai”),
7.  total\_hours=c(25,20,22,9,18,21),
8.  hours\_series=c(15,10,15,7,15,18),
9.  hours\_movies=c(9,5,8,2,2,3),
10.  hours\_documentaries=c(1,2,1,0,1,0)
11.  )
12.  
13.  \# view data frame
14.  View(netflix\_data) 

![](images/Figure2.8.jpg)

Figure 2.8: R output of View(netflix\_data)

[Functions](#contents.xhtml#sc2_31a)

Functions encapsulate repetitive or complex operations, making code more organized, efficient, and reusable. In R, functions can be built-in, user-defined, or loaded from packages. Own-defined functions are defined using the function() keyword, followed by the name of the function and its arguments in parentheses. The body of the function is then enclosed in curly braces {}. Let us create a few of our own defined functions for various businesses.

E-commerce

A function that calculates the total revenue generated by a product on an e-commerce website, given the price of the product and the number of units sold:

1.  \# function to calculate total revenue
2.  calculate\_revenue<- function(price, num\_sold) {
3.  total\_revenue<- price \* num\_sold

return(total\_revenue)

1.  }

Here, price is the product’s price on the e-commerce website, and num\_sold is the number of units sold. The function calculates the total revenue generated by the product as the product of the price and the number of units sold and returns the result:

1.  \# Define vectors to calculate revenue
2.  price<-c(250,2099,1999,750)
3.  num\_sold<-c(1000,250,100,1150)
4.  
5.  \# Calculate the total revenue for each product
6.  total\_revenue<-calculate\_revenue(price,num\_sold)
7.  
8.  \# Print the results
9.  total\_revenue
10.  \## 250000 524750 199900 862500

Here, we define two vectors, price and num\_sold, containing the price and number of units sold for four different products respectively. We then pass these vectors as arguments to the calculate\_revenue function, which calculates the total revenue for each product and returns a vector of results. 

Marketing

A function that calculates the conversion rate for a marketing campaign, given the number of impressions and clicks:

1.  \# function to calculate conversion rate
2.  calculate\_conversion\_rate<- function(impressions, clicks) {
3.  conversion\_rate<- clicks/impressions
4.  return(conversion\_rate)
5.  }

Here, impressions are the number of times the marketing message was displayed, and clicks are the number of times it was clicked. The function calculates the conversion rate by dividing the number of clicks by the number of impressions.

You can use the conversion\_rate function with vectors of data for impressions and clicks:

1.  \# Define impressions and clicks vector
2.  impressions<-c(1205,2000,1532,4101)
3.  clicks<-c(90,75,82,210)
4.  
5.  \# Calculate conversion rates for each ad campaign
6.  conversion\_rates<-calculate\_conversion\_rate(impressions,clicks)
7.  
8.  \# Print the conversion\_rates
9.  conversion\_rates
10.  \## 0.07468880 0.03750000 0.05352480 0.05120702

Here, we define two vectors of data, impressions and clicks, containing the number of impressions and clicks for four different ad campaigns. We then pass these vectors as arguments to the conversion\_rate function, which calculates the conversion rate for each campaign and returns a vector of results. We can also use round() to round off the results.

Finance

A function that calculates the compound interest on a loan given the principal, interest rate, length of the loan in years, and the number of times interest is compounded per year:

1.  \# function to calculate compound interest
2.  calculate\_compound\_interest<- function(principal, interest\_rate, years, compounding\_frequency) {
3.   n <- compounding\_frequency
4.   interest <- principal \* (1 + interest\_rate / n)^(n \* years) - principal
5.  return(interest)
6.  }
7.  
8.  \# define vector inputs
9.  principal<-c(5000,7500,9200)
10.  interest\_rate<-c(0.05,0.06,0.09)
11.  years<-c(1,2,3)
12.  compounding\_frequency<-c(1,2,4)
13.  
14.  \# calculate compound interest for each set of inputs
15.  compound\_interest<-calculate\_compound\_interest(principal,interest\_rate,years,compounding\_frequency)
16.  
17.  \# view output
18.  compound\_interest
19.  \## 250.0000 941.3161 2815.6599

This tells us that for the first set of inputs (principal = 5000, interest\_rate\= 0.05, years = 1, compounding\_frequency\= 1), the compound interest would be Rs. 250.00. Similarly, for the second set of inputs (principal = 7500, interest\_rate = 0.06, years = 2, compounding\_frequency \= 2), the compound interest would be Rs. 941.3161, and so on.

| Note: While it is true that R will automatically return the value of the last line of a function, it is considered better practice to use the return() function explicitly to indicate what the function is returning. This can help make the function more readable and easier to understand, especially for other users who may be unfamiliar with the function’s behavior. |
| --- |

For instance, the below calculate\_revenue function will also work without using the return statement:

1.  \# calculate total revenue (without return statement)
2.  calculate\_revenue<- function(price, num\_sold) {
3.   price \* num\_sold
4.  }

[Getting help with help pages](#contents.xhtml#sc2_32a)

Receiving assistance is one of the most crucial elements you will require as you begin your journey to becoming an R user. No matter how experienced you are as a programmer, you will constantly run into new functions and require assistance to comprehend how to utilize them.

Each R function comes up with a help page, and you can access it by typing the function’ name after a question mark. For instance, you can access documentation of the function mean() using the below code:

1.  \# display help page for the mean function
2.  ?mean
3.  help(mean)
4.  
5.  \# quotes are optional
6.  ?”mean”
7.  help(“mean”)

This would bring up the help page for the mean() function, which provides information on how to use the function, what arguments it accepts, and what values it returns. The help page may also include examples of using the function in practice and notes on critical caveats or limitations. If a function is from an R package, loading the package is necessary before R can locate the help page. Otherwise, you can mention the package name using the argument package below:

1.  \# documentation of select function from dplyr package
2.  help(select, package = “dplyr”)

The above command will return the documentation of the select function in the dplyr package. As you advance in your knowledge and proficiency in R, the help pages can be useful for finding out more about particular functions and packages.

[Loading data](#contents.xhtml#sc2_33a)

Importing external data into R is one of the initial steps of a project. Data is frequently kept in tabular formats like spreadsheets or CSV files. The open-source community typically uses the comma-separated values (.csv) format the most. The read.csv() function can be used to read CSV files, and it requires a CSV file with .as the decimal point and , as a separator.

![](images/Figure2.9.png)

Figure 2.9: Reading CSV files into R as data frames using read.csv()

To read Aarya\_Netflix.csv data, Aarya uses read.csv() to store into the data frame, netflix\_df:

netflix\_df<\-read.csv(“Aarya\_Netflix.csv”)

The first argument of the read.csv() is the file name which should be in your working directory; otherwise, if it is not in your working directory, you need also to mention the file’s absolute path. In the R 4.4.2 version, all the string variables are read as a class character, but if you need to read them as factor, you can set the argument stringsAsFactors = TRUE. You can also read the CSV file from the workspace tab as in the below image:

![](images/Figure2.10.png)

Figure 2.10: Import dataset from Workspace tab

To read any spreadsheets, you have first to install and load the package readxl, and use read\_excel() as shown below:

read\_excel(“netflix\_sample\_excel.xlsx”)

You can specify which sheet to read by mentioning the sheet position or name under the sheet argument if you have multiple sheets. The following table displays different packages to use to read various types of datasets:

| Packages || Types of data |
| --- | --- |
| DBI || databases |
| xml2 || XML |
| Jsonlite || JSON |
| Httr || Web APIs |
| Rvest || HTML (Web scrapping) |
| Haven || SPSS, SAS files |
| googlesheets4 || Google sheets |
| readr::read\_lines() || Text data |

Table 2.4: Different packages to import various types of data

Accessing built-in datasets

R comes with about 100 datasets (in-package datasets), with more in packages. To access the current list of available datasets, use:

data()

And, you can load a built-in R data set:

data(“dataset\_name”)

Loading data from other R packages

To access data from a particular package, use the package argument, for example:

data(package\=”rpart”)

And, if a library has attached a package, its datasets are automatically included in the search.

[Saving data](#contents.xhtml#sc2_34a)

In R, there are many ways to save data depending on the type of data you are working with and the format in which you want to save it. A few of these ways are discussed below.

Saving data as a CSV file

Comma separated values (CSV) files are a common way to store and exchange tabular data. To save data as a CSV file, you can use the write.csv() function. Here is an example:

\# save data as a CSV file

write.csv(netflix\_df, file = “Netflix\_Data.csv”)

This will create a CSV file called Netflix\_Data.csv in your working directory. The file argument specifies the name of the file to be created.

One important thing to note is that write.csv() will, by default, include row names in the output file. If you do not want row names included, you can set the row.names argument to FALSE. You can refer to the following example:

write.csv(netflix\_df, file = “Netflix\_Data.csv”, row.names = FALSE)

This will exclude row names from the output file.

Saving data as a text file

Sometimes, you may want to save data as a text file instead of a CSV file. You can use write.table() to save data as a text file. Here is an example:

\# Create a data frame

my\_data<- data.frame(x = 1:5, y = c(“A”, “B”, “C”, “D”, “E”))

\# Save data as a text file

write.table(my\_data, file = “my\_data.txt”, sep = “\\t”, row.names = FALSE)

This will create a text file called my\_data.txt in your working directory. The sep argument specifies the separator character (in this case, a tab), and row.names = FALSE removes row names from the output.

Saving data as a binary file

R provides the ability to save data as a binary file, a file format that stores data in a compact and efficient way. To save data as a binary file, you can use the saveRDS() function. It creates a portable binary file that can be easily shared and used across different R installations or versions. This can be especially useful if you need to share your data with someone who may not have the same packages or versions of R installed.

Saving objects in a binary format using saveRDS() is often more efficient than saving them in a text-based format like CSV. Binary files are smaller in size and can be read and written much faster. To save your data as a binary file:

\# create a sample data

my\_data<- list(x = 1:5, y = c(“A”, “B”, “C”, “D”, “E”))

\# save data as a binary file

saveRDS(my\_data, file = “my\_data.rds”)

This will create a binary file called my\_data.rds in your working directory. These are just a few examples of the many ways to save data. Depending on your needs, there may be other functions or file formats that are more appropriate.

[R conventions](#contents.xhtml#sc2_35a)

There are many conventions and best practices you can follow to write clear, efficient, and maintainable codes in R. A few are listed below:

*   R is case sensitive, meaning that uppercase and lowercase letters are treated differently. Using lowercase letters for variable and function names is a good practice.
*   Use meaningful names for variables and functions. This helps improve the readability and understandability of your code. Use descriptive variable names that are easy to understand and remember.
*   Indentation is important in R to make your code more readable. Therefore, you should indent your code consistently, using spaces or tabs.
*   Comment on your code to explain what you are doing and why. This makes it easier for others (and yourself in the future) to understand your code.
*   Write modular code. Break up your code into small, reusable functions that can be used in different parts of your code. This makes your code easier to read, understand, and maintain.
*   Avoid using variable names that are already defined in R, such as mean, sum, or sd. This can lead to unexpected behavior.
*   Use packages. R has a huge ecosystem of packages that can save you a lot of time and effort. Use packages like dplyr,tidyr, and ggplot2 to streamline your code.

[Conclusion](#contents.xhtml#sc2_36a)

This chapter has covered a broad overview of R essentials to get you started. We reviewed the fundamentals of the RStudio interfaces and keyboard shortcuts before discussing packages, how to install and load them, and the significance of functions and objects. With the help of this chapter, you will be able to save data with different R objects that let you store different types of values in different types of relationships. Through your understanding of data frames, you can store tabular data where each column can contain a different type of data, and each column must have the same type of data. We also learned about functions and how to write our defined functions. Next, we discussed loading and saving different data formats using the base and other packages. This chapter lays a strong foundation for beginners to learn and understand R programming concepts and techniques. 

In the next chapter, you will acquire practical aspects of data cleaning and exploration to prepare your data for analysis and visualization.

Join our book’s Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/fm1.png)

# [CHAPTER 3Exploring Data](#contents.xhtml#ch03a)

[Introduction](#contents.xhtml#sc2_37a)

In this chapter, you will get a hands-on approach to explore the Gapminder dataset using dplyr functions. We will focus on answering specific questions that arise during data exploration and providing solutions to those questions using dplyrfunctions such as select(), filter(), arrange(),mutate(), and more. This question-solution approach will help you better understand the power and flexibility of these functions and how to apply them in real-world datasets.

Imagine you are going on a treasure hunt and have a map with some clues, but need to figure out where the treasure is hidden. So, you start exploring the area, looking for hints.exploratory data analysis (EDA) is a lot like a treasure hunt. You have a dataset, but you are not sure what is in it or where to look for the answers. So, you start exploring the data, looking for anything that might give you a clue.

Just like in a treasure hunt, you might encounter unexpected obstacles or challenges along the way. For example, maybe the map is inaccurate, or other people are searching for the treasure simultaneously. In the same way, when you are doing EDA, you might find missing or incomplete data or discover that someone else has already analyzed the data you are working with. [Figure 3.1](#ch03.xhtml#fig3-1) shows an illustration of a treasure hunt:

![](images/Figure3.1.jpg)

Figure 3.1: An illustration of treasure hunt

But, just like on a treasure hunt, these challenges can also be opportunities. For instance, you may find a new clue that leads you in a different direction or work with other treasure hunters to pool your resources and increase your chance of success. In the same way, when you encounter challenges during EDA, you can use them to your advantage by asking new questions, trying different approaches, or collaborating with others.

Ultimately, the goal of both, a treasure hunt and EDA is to uncover something valuable. In the case of a treasure hunt, that might be a chest full of gold or jewels. In the case of EDA, it might be a new insight or discovery that helps you make better decisions or solve a problem. Just like in treasure hunt, the thrill and the satisfaction of the discovery make EDA exciting and rewarding.

[Structure](#contents.xhtml#sc2_38a)

This chapter will introduce you to the following topics:

*   Defining the Gapminder data
*   Introducingdplyr
*   Renaming columns
*   Selecting columns
*   Filtering rows
*   Introducing pipe operator
*   De-duplicating data
*   Arranging data
*   Adding new columns
*   Working with factors
*   Handling missing values
*   Detecting missing data visually using naniarlibrary
*   Treating missing values

[Objectives](#contents.xhtml#sc2_39a)

The goal of this chapter is to give you a thorough comprehension of how to examine and get the Gapminder dataset ready for further analysis. The chapter begins by defining the dataset and its variables. You will then learn how to select columns and filter rows of data, which are essential skills for data cleaning and exploration. The chapter also covers techniques for de-duplicating and arranging data, adding new columns, and working with factors. Another critical aspect of this chapter is handling missing values, including visualizing missing data using the naniarlibrary, understanding the reasons for missing values, and treating them using different imputation methods. Upon completing this chapter, you should possess the necessary knowledge and skills to manage and preprocess data for analysis effectively.

[Defining the Gapminder data](#contents.xhtml#sc2_40a)

You will work with the Gapminder dataset included in the dslabs package, which makes it easy to access and explore. This dataset was created using several spreadsheets available from the Gapminder Foundation.

It is a well-known dataset from the Gapminder project, which was started by Swedish statistician, Hans Rosling. The dataset contains information on various indicators of social and economic development for countries around the world, spanning several decades. The data is a subset of the original data set from ([http://gapminder.org](http://gapminder.org)). It contains health and income data for 185 countries from 1960 to 2016.

[Table 3.1](#ch03.xhtml#tab3-1)describes the Gapminder dataset:

| Column name || Description |
| --- | --- |
| Country || The name of the country |
| Year || The year of the observation |
| infant\_mortality || Infant deaths per 1000 |
| life\_expectancy || The life expectancy of people in the country (in years) |
| Fertility || Average number of children per woman |
| Population || The country’s population |
| GDP || GDP of the country according to World Bankdev |
| Continent || The continent where the country is located |
| Region || Geographical region |

Table 3.1: Description of Gapminder dataset

Let us start installing and loading the required packages:

*   \# load the required packages
*   \# install.packages(“dslabs”)
*   library(dslabs)
*   
*   \# install.packages(“tidyverse”)
*   library(tidyverse)

Let us load the tidyverse, which will load dplyr, among other packages. tidyverse, a set of R packages developed by RStudio (Wickham et al. 2019), has become one of the most popular frameworks for data analysis.

*   \# load the data
*   data(gapminder)
*   \# To get familiar with this dataset, you might want to use the below function
*   ?gapminder
*   
*   \# check the data type of gapminder dataset
*   class(gapminder)
*   \## “data.frame”

You can run View(gapminder) to see the entire dataset, which will open the dataset in the RStudio viewer. And, if you are only interested in displaying the top 6 rows of the DataFrame, you can use head(gapminder), and the last 6 rows can be fetched using tail(gapminder).

Which variables are present, and what are their respective data types?

The dataset contains nine variables, and you can view their details using the str function:

*   \# display the structure of the gapminder dataset
*   str(gapminder)
*   
*   \## ‘data.frame’: 10545 obs. of 9 variables:
*   \## $ country : Factor w/ 185 levels “Albania”,”Algeria”,..: 1 2 3 4 5 6 7 8 9 10 ...
*   \## $ year : int 1960 1960 1960 1960 1960 1960 1960 1960 1960 1960 ...
*   \## $ infant\_mortality: num 115.4 148.2 208 NA 59.9 ...
*   \## $ life\_expectancy : num 62.9 47.5 36 63 65.4 ...
*   \## $ fertility : num 6.19 7.65 7.32 4.43 3.11 4.55 4.82 3.45 2.7 5.57 ...
*   \## $ population : num 1636054 11124892 5270844 54681 20619075 ...
*   \## $ gdp : num NA 1.38e+10 NA NA 1.08e+11 ...
*   \## $ continent : Factor w/ 5 levels “Africa”,”Americas”,..: 4 1 1 2 2 3 2 5 4 3 ...
*   \## $ region : Factor w/ 22 levels “Australia and New Zealand”,..: 19 11 10 2 15 21 2 1 22 21 ...

But, if you are only interested in checking the column names, you can simply use colnames() by inserting the following code:

*   \# display all columns of the dataframe
*   colnames(gapminder)
*   \## “country” “year” “infant\_mortality” “life\_expectancy” “fertility” 
*   \## “population” “gdp” “continent” “region”
*   \# dimensions 
*   dim(gapminder)
*   \## 10545 9
*   
*   \# check the number of rows in the dataset
*   nrow(gapminder)
*   \## 10545
*   
*   \# check the number of columns in the dataset
*   ncol(gapminder)
*   \## 9

[Introducing dplyr](#contents.xhtml#sc2_41a)

Imagine you are giving instructions to explore and manipulate the Gapminder dataset. dplyr function provides these instructions, called verbs, for a language of data manipulation. These verbs have a consistent structure: you provide the DataFrame to be manipulated as the first argument, followed by the tasks you want to manipulate with variables as subsequent arguments, all without using quotes. The output will be a new DataFrame with the desired manipulations. dplyr makes data manipulation faster, more intuitive, and easier to understand.

[Renaming columns](#contents.xhtml#sc2_42a)

How can you rename the population column to country\_population and the GDP column to country\_gdp in the dataset?

To make our data easier to work with, we often find ourselves renaming column names to reflect their content better. Here is an example of how to do so using the rename() function from the dplyr package:

*   \# rename the population and GDP column names
*   gapminder<- rename(gapminder, country\_population = population , country\_gdp = gdp ) 
    
    | Note: We have renamed two columns (population and gdp) in the above command, and throughout this chapter this updated GapminderDataFrame will be used. |
    | --- |
    

Exploring data is one of the tasks done in both, the data preparation and core analysis stages.

[Selecting columns](#contents.xhtml#sc2_43a)

Locating the relevant columns can be time-consuming and overwhelming when working with large datasets with numerous columns. The select() function helps you to easily narrow down the dataset to only the columns of interest by specifying their names. This will allow you to focus on the most relevant variables of your analysis.

Let us explore a few questions to ask from the dataset.

How can you select the country, year, infant mortality, and life expectancy variables from the dataset?

*   \# select the country, year, infant mortality, and life expectancy variables 
*   gapminder\_subset<- select(gapminder, country, year, infant\_mortality, life\_expectancy)
*   
*   \# the equivalent command in base R
*   gapminder\_subset<\-gapminder\[, c(“country”, “year”, “infant\_mortality”, “life\_expectancy”)\]
*   
*   \# The square brackets \[ \] are used to subset the data. The comma , separates the rows from the columns. In this case, no condition is specified for rows, so all rows are selected. Next, the c() function creates a vector of column names we want to keep. Finally, we use the vector of column names inside the square brackets to select the desired columns.

In this solution, select() creates a DataFrame, gapminder\_subset, and keeps the variables you are interested in, country, year, infant\_mortality, and life\_expectancy. We exclude all other variables from the dataset.

You selected all the columns between country and life\_expectancy (inclusive) in the above command. In such cases, you can also retrieve those columns using the following code:

*   \# select all columns between country and life\_expectancy (inclusive)
*   gapminder\_subset2<- select(gapminder, country:life\_expectancy)

There are several helper functions you can use within select():

*   starts\_with()
*   ends\_with()
*   matches()
*   contains()

These let you quickly match larger blocks of variables that meet some criterion. See ?select for more details. Let us check a few of them:

How can you select only the columns that start with the string country in the column name from the dataset?

*   \# select all columns that start with “country”
*   gapminder\_subset3<- select(gapminder, starts\_with(“country”))

The above command creates a new DataFrame called gapminder\_subset2 by selecting all columns that start with the word country from the original GapminderDataFrame.

*   \# check column names of the dataframe gapminder\_subset3
*   colnames(gapminder\_subset3)
*   \## “country” “country\_population” “country\_gdp”

The starts\_with() function is used inside select() to select columns that start with a specific character string. In this case, it is used to choose all columns that start with the word country.

How can you exclude the continent and region columns?

*   \# select all columns except continent and region
*   gapminder\_subset4 <- select(gapminder, -continent, -region)

By placing a minus sign (-) in front of the column names we wish to eliminate, we are effectively instructing R to choose all columns except for the designated ones.

For what years have the data been collected?

You need to extract this data from the year column. With the dplyr package, you can use two main functions for extracting variables: pull()and select().

*   \# display the unique years present in the dataset
*   unique(pull(gapminder,year))
*   
*   \## 1960 1961 1962 1963 1964 1965 1966 1967 1968 1969 1970 1971 1972 1973 1974 1975 1976 1977 ## 1978 1979
*   \## 1980 1981 1982 1983 1984 1985 1986 1987 1988 1989 1990 1991 1992 1993 1994 1995 1996 1997 ## 1998 1999
*   \## 2000 2001 2002 2003 2004 2005 2006 2007 2008 2009 2010 2011 2012 2013 2014 2015 2016

In the above command, pull() function extracts a single column as a vector. The unique() function is then used to extract only the unique values in the column to see all the unique years in the dataset. On the other hand, if you want to store the result in a DataFrame, you can use select() as shown in the command:

*   \# store the unique years present in a dataframe
*   unique\_years<- unique(select(gapminder,year))
*   
*   \# Here, the result is stored in the dataframeunique\_years and it can be displayed using View()
*   View(unique\_years)

To identify how many years the data has been collected, you can use the length() of the unique number of years present.

*   \# For what years have the data been collected?
*   length(unique(pull(gapminder,year)))
*   \## 57

[Filtering rows](#contents.xhtml#sc2_44a)

How can you filter the dataset only to include countries in Asia with a life expectancy greater than 70years in 2015?

*   \# filter the countries in Asia with a life expectancy > 70 years in 2015
*   gapminder\_asia<\-filter(gapminder, year == 2015,continent == “Asia”, life\_expectancy\> 70) 

We use filter() to extract only the observations from the year 2015, continent Asia, and a life expectancy greater than 70.

How can you create a subset of the Gapminder dataset that includes only countries from the continents of Americas and Asia?

*   \# create a subset of the gapminder dataset that only contains countries from the Americas and Asia continents.
*   gapminder\_asia\_america<- filter(gapminder, continent == “Americas” | continent == “Asia”)

This command uses the | operator to filter for two values in the continent column, which can become difficult to read and understand if we need to filter for more than two values. You can write a clean and more efficient way to rewrite the above command using%in% operator. %in% checks if each element in the selected column exists within the specified vectors, returning a logical vector indicating whether each row should be included in the final output or not.

*   gapminder\_asia\_america2 <- filter(gapminder, continent %in% c(“Americas”,”Asia”))

The above command using %in% operator is better than the previous command using | operator because it is more concise and easier to read, especially when there are multiple values to filter for. Here, we are keeping only those rows where the value in the continent column falls into one of two categories: either Asia or Americas.

[Introducing pipe operator](#contents.xhtml#sc2_45a)

The %>% operator is commonly referred to as the pipe operator. It is used to chain multiple operations together readably and efficiently.

In 2010, What were the total population, GDP, and infant mortality of countries in Asia and Europe with a life expectancy greater than 70?

*   gapminder\_asia\_europe<- gapminder %>% 
*   filter(year == 2010, continent %in% c(“Asia”, “Europe”), life\_expectancy>70) %>% 
*   select(country, continent, country\_population, country\_gdp, infant\_mortality, life\_expectancy)

The first operation in this command is to filter the dataset based on three conditions using the filter()function. The first condition is that the year must be equal to 2010, the second condition is that the continent must be either Asia or Europe, and the third condition is that the life expectancy must be greater than 70.

The second operation in this command is to select specific columns from the filtered dataset using the select() function. The selected columns include country, continent, country\_population, country\_gdp, infant\_mortality, and life\_expectancy.

So, the resulting gapminder\_subset dataset will only include rowswhere the year is 2010, the continent is either Asia or Europe, the life expectancy is greater than 70.

The %>% operator takes the function output on the left-hand side and passes it as the first argument to the function on the right-hand side. This allows you to chain together multiple functions in a way that is easy to read and understand.

Which countries had a population greater than 100 million in 2015? In the following code, we will filter the original DataFrame to retain only rows corresponding to the target year and population threshold. Then, we will select only the country column from the filtered DataFrame, as shown:

*   \# subset countries with a population > 100 million in 2015
*   gapminder\_country2015 <- gapminder %>%
*   filter(year == 2015, country\_population> 100000000) %>%
*    select(country)
*   
*   View(gapminder\_country2015)
*   
*   \## country
*   \## Bangladesh
*   \## Brazil
*   \## China
*   \## India
*   \## Indonesia
*   \## Japan
*   \## Mexico
*   \## Nigeria
*   \## Pakistan
*   \## Philippines
*   \## Russia
*   \## United States

The pipe operator is a versatile tool that helps streamline workflows and make coding more efficient and readable. It transforms complex data transformations into elegant and easy-to-follow sequences.

[De-duplicating data](#contents.xhtml#sc2_46a)

What are the distinct continent categories in the dataset?

*   \# identify unique continents in the gapminder dataset
*   unique\_continents<- gapminder %>%
*    distinct(continent)
*   
*   \# print the dataframe, unique\_continents
*   unique\_continents
*   \## continent
*   \## Europe
*   \## Africa
*   \## Americas
*   \## Asia
*   \## Oceania

The distinct()function is used to extract unique values of a column or a combination of columns. In this case, we want to extract unique continents from the continent column in the Gapminder dataset. The resulting output is stored in a new DataFrame unique\_continents.

If you want to save the result as a vector, you can use pull() to extract the unique continents.

*   \# identify unique continents 
*   continents<- gapminder %>%
*   distinct(continent)%>%
*   pull(continent)
*   
*   \# display the vector
*   continents
*   \## Europe Africa Americas Asia Oceania 
*   \## Levels: Africa Americas Asia Europe Oceania

How many unique countries are in the dataset?

*   \# identify the number of unique countries in the dataset
*   gapminder %>%
*    distinct(country) %>%
*   count()
*   
*   \## n
*   \## 185

This command selects only distinct country names using the distinct() function. Then, it counts the number of unique countries using the count() function from dplyr.

[Arranging data](#contents.xhtml#sc2_47a)

How can you rank countries based on population size to identify the top countries with the largest populations in 2015?

*   \# identify the top countries with the largest populations in 2015
*   gapminder\_arranged1 <\-gapminder %>% 
*   filter(year == 2015) %>%
*    arrange((country\_population))

Here, the arrange() function is used to sort the resulting DataFrame in ascending order based on the country\_population column.

How about arranging the dataset based on the population in descending order?

*   gapminder\_arranged2 <\-gapminder %>% 
*   filter(year == 2015) %>%
*    arrange(desc(country\_population))

The resulting DataFrame gapminder\_arranged2 will contain only the rows of 2015, and these rows will be sorted in descending order based on the country\_population.

Which ten countries had the highest life expectancy in 2015, and what was their population?

*   \# identify the ten countries that had the highest life expectancy in 2015, and display their population
*   gapminder %>%
*   filter(year == 2015) %>%
*    arrange(desc(life\_expectancy)) %>%
*   select(country, life\_expectancy, country\_population) %>%
*   head(10)
*   
*   \## country life\_expectancycountry\_population
*   \## Hong Kong, China 83.73 7287983
*   \## Iceland 83.30 329425
*   \## Japan 83.20 126573481
*   \## Switzerland 83.00 8298663
*   \## Spain 82.60 46121699
*   \## Australia 82.30 23968973
*   \## Italy 82.20 59797685
*   \## Luxembourg 82.20 567110
*   \## Israel 82.10 8064036
*   \## Malta 82.10 418670

This command includes data for 2015, sorts the data by life expectancy in descending order, selects three columns (country, life expectancy, and country population), and returns the top 10 rows of the resulting DataFrame.

[Adding new columns](#contents.xhtml#sc2_48a)

mutate() is a function from the dplyr package that is used to create new columns in a DataFrame based on the existing columns. It takes DataFrame as the first argument, and subsequent arguments specify the new columns to be added.

One crucial aspect of mutate() is that it creates a new DataFrame with additional columns rather than modifying the original DataFrame in place. This is a valuable feature because it allows the user to keep track of the original data and apply multiple transformations without overwriting it.

How can we create a new variable that represents the population in millions?

*   \# add a new column, population\_millions
*   gapminder\_population<- gapminder %>% 
*   mutate(population\_millions = population / 1000000)
*   
*   \# add a new column, population\_millions
*   gapminder\_population2<- gapminder %>% 
*   mutate(population\_millions = round(population / 1000000,2))

It creates a new column called population\_millions using the mutate() function by dividing the existing population column by 1,000,000 and rounding the result to two decimal places using the round() function. The command returns a DataFrame, gapminder\_population2, containing all columns of the original GapminderDataFrame along with a new column, population\_millions, with the population of each country in millions.

How can we extract the countryname, year, life expectancy, continent, andregion of countries and identify which countries are located in Asia?

*   \# extract the country name, year, life expectancy, continent, and region of countries and identify which countries are located in Asia or not
*   gapminder\_is\_asia<- gapminder %>%
*   select(country, year, life\_expectancy, continent, region) %>%
*   mutate(is\_asia = ifelse(continent == “Asia”, 1, 0))
*   
*   View(gapminder\_is\_asia)

This command adds a new column called is\_asia using the mutate()function. The new column contains a binary value of 1 or 0 depending on whether the country is located in Asiaor not. The if else() function from the base package is used to assign the binary value.If the continent value is Asia, it assigns a value of 1; otherwise, value of 0 is set.

This variable can help to analyze and compare trends and patterns between countries in Asia and those outside the region.

[Working with factors](#contents.xhtml#sc2_49a)

One of the key benefits of using factors in R is that it provides a way to preserve the underlying order of data, which can be necessary for analysis and visualization. For example, suppose you have a dataset of customer satisfaction ratings on a scale of 1 to 5, where 1 represents very dissatisfied, and 5 illustrates very satisfied. If you store this variable as a factor, R will preserve the order of the levels, which is important for calculating summary statistics.

In this section, you will use the forcats package, a part of the tidyverse suite of packages in R, that provides additional functionality for working with factors. For instance, it allows for easy manipulation of factor levels and labels and offers functions to reorder and rename factor levels.

How can you count the number of observations in each continent?

*   \# check levels attribute of the factor variable, continent
*   levels(gapminder$continent)
*   \## “Africa” “Americas” “Asia” “Europe” “Oceania” 
*   
*   \# count the number of observations in each continent
*   continent\_count<- fct\_count(gapminder$continent)
*   
*   View(continent\_count)
*   \## f n
*   \## Africa 2907
*   \## Americas 2052
*   \## Asia 2679
*   \## Europe 2223
*   \## Oceania 684
*   
*   \# sort the result by setting argument, sort to TRUE, and also display fraction by prop argument
*   continent\_count\_sorted<- fct\_count(gapminder$continent, sort = TRUE, prop = TRUE)
*   
*   View(continent\_count\_sorted)
*   \## f n p
*   \## Africa 2907 0.276 
*   \## Asia 2679 0.254 
*   \## Europe 2223 0.211 
*   \## Americas 2052 0.195 
*   \## Oceania 684 0.0649

fct\_count() returns a DataFrame with two columns: the factor levels and their corresponding frequencies in the input vector. In this case, it will return a DataFrame with the unique continents in the Gapminder dataset and the number of times each continent has occurred.

How can you add new levels to the continent variable?

One of the variables in our dataset is continent which contains information about the continent each country belongs to. Now, let us say you noticed that the continent Antarctica is missing from the continent variable, and you want to add it to the factor levels. One way to do this is to use the fct\_expand() function from the forcats package.

*   \# add “Antarctica” to the continent variable
*   gapminder$continent<- fct\_expand(gapminder$continent, “Antarctica”)
*   
*   \# check levels of the continent to verify if Antarctica has been added or not
*   levels(gapminder$continent)
*   
*   \## “Africa” “Americas” “Asia” “Europe” “Oceania” “Antarctica”
*   
*   \# count the number of observations of each continent
*   fct\_count(gapminder$continent)
*   \## A tibble: 6 x 2
*   \## f n
*   \## <fct><int>
*   \## Africa 2907
*   \## Americas 2052
*   \## Asia 2679
*   \## Europe 2223
*   \## Oceania 684
*   \## Antarctica 0 
    
    | Note: If the Antarctica level already existed in the continent variable, fct\_expand() would not add it again. Instead, it would just return the original factor with its levels unchanged. |
    | --- |
    

How can you drop unused levels from the continent variable?

To drop unused levels from the continent variable, you can use the fct\_drop() function. Here is how you can do it:

*   \# drop unused levels from the continent variable
*   gapminder$continent<- fct\_drop(gapminder$continent)

Now, if you recheck the levels of the continent, you will notice the unused level,Antarctica is removed.

*   levels(gapminder$continent)
*   \## “Africa””Americas””Asia””Europe””Oceania”

How can you move Asia to the second position in the continent column?

In a few scenarios, releveling factors becomes essential because it allows you to change the order of the levels of a categorical variable, which can affect the behavior of statistical functions and data visualizations.

For example, if you have a factor variable representing the days of the week, the default order of levels will be alphabetical (that is, Friday, Monday, Saturday, Sunday, Thursday, Tuesday, Wednesday). However, suppose you want to analyze or visualize your data by order of days in the week. In that case, reordering the factor levels to reflect the logical order of the days (i.e., Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday) is necessary.

*   \# move Asia to the second position
*   gapminder$continent<- fct\_relevel(gapminder$continent, “Asia”, after = 1)
*   
*   levels(gapminder$continent)
*   \## “Africa”“Asia”“Americas”“Europe”“Oceania”

This command will modify the continent column by moving the level Asia to the second position after the first, default level. The argument specifies the position after which the level should be moved.

[Handling missing values](#contents.xhtml#sc2_50a)

The symbol NA (not available) is used in R to represent missing values, whereas impossible values (such as dividing by zero) arerepresented by Not a Number (NaN).

The function is.na()is used to check if an object has any missing values represented by NA, whereasis.nan()is used to test if an object has any NaN values.

For example, to check for missing values in the infant\_mortalityvariable, you can use the following code:

*   \# number of missing values in the column infant\_mortality
*   sum(is.na(gapminder$infant\_mortality))
*   \## 1453

This will give us the total number of missing values in the infant\_mortality variable. We can use the same code for other variables to check the missing values. To know the number of missing values in the dataset column-wise, you can use the following code:

*   \# number of missing values in each column of gapminder dataset
*   colSums(is.na(gapminder))
*   \## country yearinfant\_mortalitylife\_expectancy fertility 
*   \## 0 0 1453 0 187 
*   \## country\_populationcountry\_gdp continent region 
*   \## 185 2972 0 0 

The initial stage involves identifying the number or proportion of missing values present in each column of the dataset. This helps to understand the pattern and extent of missing values across the columns. First, let us write a function to create DataFrame to display the missing values summary of Gapminder dataset.

*   \# function to display the missing values summary
*   missing\_values\_df<- function(df) {
*   
*   \# column wise missing values
*   missing\_values<- colSums(is.na(df))
*   
*   \# percentage of missing values
*   missing\_values\_percent<- 100 \* colSums(is.na(df)) / nrow(df)
*   
*   \# create a dataframe with the results
*   missing\_values\_table<- cbind(missing\_values , missing\_values\_percent)
*   
*   \# rename the columns
*   colnames(missing\_values\_table)<- c(“Missing Values”, “% of Total Values”)
*   
*    # sort the table by percentage of missing descending
*   missing\_values\_table<- missing\_values\_table\[missing\_values\_table\[,2\] != 0,\]
*   missing\_values\_table<- missing\_values\_table\[order(-missing\_values\_table\[,2\]),\]
*   missing\_values\_table<- round(missing\_values\_table, 1)
*   
*   \# return the dataframe with missing values details
*   return(missing\_values\_table)
*   }
*   gapminder\_NA\_summ<- missing\_values\_df(gapminder)
*   
*   \# print the result of gapminder\_NA\_summ
*   gapminder\_NA\_summ
*   
*   \## Missing Values % of Total Values
*   \## country\_gdp 2972 28.2
*   \## infant\_mortality 1453 13.8
*   \## fertility 187 1.8
*   \## country\_population 185 1.8

[Detecting missing data visually using naniar library](#contents.xhtml#sc2_51a)

Missing values are a common occurrence in data analysis which can arise for various reasons, such as data entry errors, equipment malfunction, or nonresponse. It can be so prevalent that one can rarely find a dataset without them. Ignoring or mishandling missing values can lead to biased or inaccurate results, which can have serious consequences. Fortunately, numerous methods and techniques are available to help you manage missing values in data. This way, you can ensure that the analysis is reliable and valid, even while working with incomplete data.

You can turn to the naniar package developed by Nicholas Tierney to manage missing values and gain insights into the data. With naniar, you can explore the pattern of missing values and visualize the impact of missing data on your analysis. These tools can help you ensure the reliability of your results, even in the presence of missing data.

*   \# load the naniar package
*   library(naniar)

To gain insights into whether the missing data is occurring randomly or not, you can create a visualization that displays the position of missing values across all variables in the dataset. 

You can first start exploring the missing values using vis\_miss() plot. [Figure 3.2](#ch03.xhtml#fig3-2) visually represents the quantity of missing data by indicating the location of missing values in black. Additionally, the plot includes details on the overall percentage of missing values for the dataset (displayed in the legend) and each variable. This approach can help you to understand the patterns of missing values and determine if it is occurring randomly or if there is a systematic reason behind their occurrence.

*   \# locations of missing values of each variable
*   vis\_miss(gapminder)

![](images/Figure3.4.png)

Figure 3.2: Number of missing values in each column and overall percentage of missing values

[Figure 3.3](#ch03.xhtml#fig3-3) shows the number of missing values in each variable of the Gapminder dataset:

*   \# number of missing values in each variable
*   gg\_miss\_var(gapminder)

![](images/Figure3.5.png)

Figure 3.3: Visualize the number of missing values in each variable

Reasons for missing values

When dealing with missing data, it is essential to understand why the data is missing in the first place. Different types of missing data can affect your results in different ways. Let us break them down into three categories:

*   Missing completely at random (MCAR): This occurs when the missing values in a variable are completely unrelated to any other variables in the dataset or the variable itself. In other words, the missingness has no discernible pattern and just happens randomly.
*   Missing at random (MAR): With MAR, the missingness is not random, but it can be predicted by other variables in the dataset that have complete information which means that the missingness depends on other factors in the dataset, but those factors are known and can be taken into account.
*   Missing not at random (MNAR): This is when the missingness depends on unobserved data or the actual value of the missing data. This can be tricky, as the missing values may be related to essential variables that are not included in the dataset, leading to biased or inaccurate results.

By understanding different types of missing data, you can make informed decisions about handling them and how they might impact your analysis.

Next, to visualize the patterns of missingness or rather the combinations of missingness amongst variables, you can use the gg\_miss\_upset function:

*   \# explore combinations of missingness among variables
*   gg\_miss\_upset(gapminder)

![](images/Figure3.6.png)

Figure 3.4: Visualize the missingness patterns among variables

The above [Figure 3.4](#ch03.xhtml#fig3-4) shows 185 cases where all four variables (country\_gdp, infant\_mortality, fertility, country population) have missing values together. The variables of country\_gdp and infant\_mortality are missing 832 cases together. 

One way to assess the amount of missing data in a dataset while examining categorical variables is to use the function gg\_miss\_fct().This function displays the percent of missing values for each column, grouped by a categorical variable present in the dataset.

*   \# check heatmap of missingness of variables along the years
*   gg\_miss\_fct(x= gapminder, fct = year)

[Figure 3.5](#ch03.xhtml#fig3-5) explores missingness in Gapminder variables along the year:

![](images/Figure3.7.png)

Figure 3.5: Number of missing values in each column across the years

The above heatmap shows that the missing values in infant\_mortality and country\_gdp are spread across all the years, but no data is available for country\_gdp, country\_population, fertility, and infant\_mortality for the year 2016.

[Figure 3.4](#ch03.xhtml#fig3-4) provided insight into the 185 missing values in all four variables. Further examining the data, [Figure 3.5](#ch03.xhtml#fig3-5) confirms that these cases correspond to 2016. This additional validation strengthens our understanding of the missing values in the dataset and provides us with useful information for future analysis.

[Treating missing values](#contents.xhtml#sc2_52a)

Missing data is a common issue when working with real-world datasets, and there are different strategies for handling missing values depending on the nature and extent of the problem. Some popular approaches include deletion methods, which remove incomplete observations or entire variables, and imputation methods, which replace missing values with estimates derived from available information. Both approaches have pros and cons, and choosing the right strategy depends on factors such as the amount and pattern of missingness and the goals of the analysis.

[Deletions](#contents.xhtml#sc3_53a)

Deleting missing values is generally not recommended because it can result in a loss of valuable information from the dataset. In most cases, it is best to avoid deletion unless the proportion of missing values is very small. In such cases, removing the missing values can be a reasonable option without significantly affecting the integrity of the dataset. Different deletion approaches for missing valuesare shown in [Figure 3.6](#ch03.xhtml#fig3-6):

![](images/Figure3.8.jpg)

Figure 3.6: Deletion approaches of missing values

The listwise deletion (Dropping entire rows)

This approach removes entire rows of data containing missing values, which is also called complete case deletion. However, listwise deletions are only appropriate formissing completely at Random MCAR values. The below code shows listwise deletion using drop\_na():

*   \# check the dimensions of gapminder
*   dim(gapminder)
*   \## 10545 9
*   
*   \# drop rows: missing values in any column
*   drop\_rows\_any<- gapminder %>% drop\_na()
*   
*   \# check the dimensions of the new dataframe
*   dim(drop\_rows\_any)
*   \## 7139 9
*   
*   \# drop rows: missing values in any specific column ( for example, fertility)
*   drop\_rows\_fertility<- gapminder %>% drop\_na(fertility)
*   
*   \# check the dimensions of the new dataframe
*   dim(drop\_rows\_fertility)
*   \## 10358 9
*   \# The above command removed 187 rows from gapminder that has missing values in the column “fertility”

Dropping entire columns

Sometimes, a column in a dataset may contain a high percentage of missing values, such as 80% or more. If this feature is not significant for the analysis, it may be tempting to delete from the dataset. However, it is essential to remember that deleting data is unreliable for handling missing values. While removing a feature with high missingness can make the dataset manageable, it may also result in a loss of valuable information that could be useful for other analysis. Therefore, exploring different approaches for handling missing values is generally recommended before resorting to deletion. In the following example, we are focusing on removing a specific column, country\_gdp, from the Gapminder dataset:

*   \# drop the column country\_gdp(using base R)
*   gapminder$country\_gdp<- NULL
*   
*   \# drop the column country\_gdp (using dplyr)
*   gapminder<- select(gapminder, -country\_gdp)

The above code uses both Base R and the dplyr package to remove the country\_gdp column from the GapminderDataFrame.

[Imputations](#contents.xhtml#sc3_54a)

Imputation is another approach to replace missing values in a dataset with estimated values. The method used for imputation can vary depending on the nature of the problem and the data being analyzed. There are numerous approaches to imputation, each with its own advantages and disadvantages, and the choice of method should be carefully considered, based on the specific needs of the analysis. [Figure 3.7](#ch03.xhtml#fig3-7) displays various techniques to impute missing values in a dataset:

![](images/Figure3.9.jpg)

Figure 3.7: Imputation techniques of missing values

Typical imputation techniques for non-time series problems:

*   Imputation with a constant value: One approach to handle missing data is imputing it with a constant value. This involves replacing all missing values in a dataset with a single value (for example, replace with 0). While this approach is straightforward and easy to implement, it may not be suitable for all data types.
*   Imputation using column statistics: Another common approach for imputing missing values is using the respective column’s statistics, such as mean, median, or mode. This approach involves calculating the column-wise statistics for the non-missing values and replacing the missing values with the calculated value. This method can be effective, especially when the missing data is not significantly affecting the overall distribution of the data.

Imputations techniques for time series problems:

*   Replace missing values with the last observed value (forward fill):This approach involves replacing missing values with the most recent previous value observed in the data. This method assumes that the missing values are likely similar to the most recent previous value.
*   Replace missing values with the next observed value (backward fill): This method replaces missing values with the most recent next value observed in the data. This method assumes that the missing values are similar to the next observed value.
*   Linear and spline interpolation method: Interpolation estimates missing values based on the surrounding data points. Linear interpolation involves connecting two adjacent data points with a straight line and using this line to estimate the missing value. Spline interpolation is a complex method that involves fitting a curve to the data points and using this curve to estimate missing values. Both methods can effectively impute missing data, but spline interpolation tends to be more accurate and flexible than linear interpolation. However, it is essential to note that interpolation assumes a certain level of continuity in the data and may not be appropriate if the missing values are not well-represented by the surrounding data.

[Table 3.2](#ch03.xhtml#tab3-2) lists essential R functions typically used for imputing missing values:

| Function || Package || Description |
| --- | --- | --- |
| replace\_na || tidyr || Replaces missing values with a specified value. |
| --- | --- | --- |
| fill || tidyr || Imputes missing values using the last observed value (forward fill) or the next observed value (backward fill). |
| na.spline || zoo || Imputes missing values using a spline interpolation.  |
| na.approx || zoo || Imputes missing values using linear interpolation. |
| mice || mice || Impute missing values in a DataFrame using multiple imputations with chained equations. |
| missForest || missForest || Imputes missing values using a random forest algorithm. |

Table 3.2: Description of essential R functions for imputing missing values

[Conclusion](#contents.xhtml#sc2_55a)

In this chapter, we have covered various data exploration techniques using the Gapminder dataset. We defined the dataset and then focused on selecting relevant columns and filtering rows based on certain conditions. We also learned to identify and remove duplicate rows in a dataset and sort data by one or more columns. Additionally, we explored how to work with factors in R. One of the most common challenges in real-world datasets is missing data. We covered different approaches for handling it, including detecting missing data visually using the naniarlibrary and understanding the reasons for missing data. We also explored various methods for treating missing data, such as imputation with constant values, column statistics, and interpolation methods. These techniques ensure that our data analysis is based on complete and accurate data and can lead to more meaningful insights and predictions.

In the next chapter, you will learn essential data manipulation techniques to become more proficient at wrangling and preparing your data for downstream analysis.

Join our book’s Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/fm1.png)

# [CHAPTER 4Wrangling Data](#contents.xhtml#ch04a)

[Introduction](#contents.xhtml#sc2_56a)

This chapter will delve into data wrangling. The ability to manipulate DataFrames, such as reshaping and restructu ring, often becomes essential before any meaningful insights can be derived. DataFrames often need to be reshaped for analysis or visualization purposes. In the first part of this chapter, you will learn the process of converting your data table from long to wide format and vice versa. You will learn how to summarize your data based on specific criteria and perform operations on grouped data. We will also dive into selecting columns and filtering rows, with a focus on working with aggregated data. Combining data from multiple sources is a frequent task in data analysis, so we will explore that as well.

[Structure](#contents.xhtml#sc2_57a)

In this chapter, you will explore the following topics to enhance your data manipulation skills:

*   Pivoting data 
    *   Long and wide format data
    *   Convert wide to long format
    *   Convert long to wide format

*   Grouping and summarizing 
    *   Filtering on grouped data
    *   Adding new columns on grouped data
*   Merging data 
    *   Binding data: rbind() and cbind()
    *   Joins: Inner, outer, left, and right

[Objectives](#contents.xhtml#sc2_58a)

You will be looking at reshaping and restructuring to learn to transform your DataFrames from long to wide format and vice versa. Next, you will dive into techniques for summarizing your data based on specific criteria and perform operations on grouped data.Additionally, you will discover how to combine two DataFrames into a single dataset.

By the end of this chapter, you will have gained essential data-wrangling skills that will help you efficiently reshape, aggregate, and merge DataFrames. This foundation will set you up for more advanced data analysis techniques.

[Pivoting data](#contents.xhtml#sc2_59a)

Pivoting data is a crucial technique in data analysisto restructure datasets for more effective exploration. Often, data comes in either wide or long formats, each with its own advantages. Each row corresponds to a single observation or measurement in a long data format, with multiple rows representing different time points. Conversely, in a wide data format, each subject or entity is represented by a single row, with multiple columns used to denote different time points.The wide format is suitable for preliminary summary statistics, while the long format is better for certain analyses like time series or repeated measures. By converting data between these formats, you can tailor it to meet your specific requirements.

[Long and wide format data](#contents.xhtml#sc3_60a)

Imagine you work for a fruit-selling company. You have a spreadsheet that lists the total number of apples, bananas, and oranges sold each day of the week. The data looks like the [Table 4.1](#ch04.xhtml#tab4-1) below:

| Day || Apples || Bananas || Oranges |
| --- | --- | --- | --- |
| Monday || 10 || 5 || 7 |
| --- | --- | --- | --- |
| Tuesday || 8 || 3 || 9 |
| Wednesday || 12 || 2 || 6 |
| Thursday || 15 || 6 || 8 |
| Friday || 11 || 4 || 10 |

Table 4.1: An example of wideformat data

This is an example of wide data because there is a separate column for each type of fruit. The advantage of wide data is that it is easy to read and understand. You might want to analyze your dataset in different ways. Sometimes, you want to see each variable in its own column, and other times, you want to see all the variables in a single column. This is where wide and long data formats come into play.

However, when you want to visualize the data using ggplot2 package, you might need to work with long-format data. In a long format, each observation corresponds to a single sale, with columns indicating the day, the type of fruit, and the number of fruits sold. Some libraries, such as ggplot2 and plyr, and most modelling functions, such as lm(), glm(), and gam() require long-format data. The below [Table 4.2](#ch04.xhtml#tab4-2) shows the long-format data:

| Day || Fruits || Sales |
| --- | --- | --- |
| Monday || Apples || 10 |
| Monday || Bananas || 5 |
| Monday || Oranges || 7 |
| Tuesday || Apples || 8 |
| Tuesday || Bananas || 3 |
| Tuesday || Oranges || 9 |
| Wednesday || Apples || 12 |
| Wednesday || Bananas || 2 |
| Wednesday || Oranges || 6 |
| Thursday || Apples || 15 |
| Thursday || Bananas || 6 |
| Thursday || Oranges || 8 |
| Friday || Apples || 11 |
| Friday || Bananas || 4 |
| Friday || Oranges || 10 |

Table 4.2:An example of long-format data

Generally, wide data is appropriate when you have a fixed set of columns corresponding to variables of interest, and long data is appropriate when you have many different variables that should be organized into rows.

Introducing reshape2

Hadley Wickham created the reshape2 package, which helps easily convert data between wide and long formats. The reshape2 package utilizes two primary functions: melt() and cast(). The melt() transforms data from a wide format to a long format, while the cast() takes data in a long format and converts it back to a wide format.

Loading the data

To illustrate this topic, we will use the Parking Birmingham dataset available on the University of California Irvine (UCI) Machine Learning Repository as an example dataset. The below [Table 4.3](#ch04.xhtml#tab4-3)describes the Parking dataset:

| Column name || Description |
| --- | --- |
| SystemCodeNumber || Parking ID |
| Capacity || Parking capacity |
| Occupancy || Parking occupancy rate |
| LastUpdated || Date and time of measurement |

Table 4.3: Description of parking dataset columns

To start with our analysis, we will begin by installing and loading the essential packages, namely reshape2 and dplyr. Afterward, we will read the parking dataset and take a closer look at the structure of the DataFrame.

*   \# install and load the required packages 
*   install.packages(“reshape2”)
*   library(reshape2)
*   \# you will use dplyr for a few pre-processing steps
*   library(dplyr)
*   
*   \# read the dataset 
*   parking\_df<- read.csv(“parking.csv”)
*   
*   \# structure of the DataFrame
*   str(parking\_df)
*   
*   \## ‘data.frame’: 35717 obs. of 4 variables:
*   \## $SystemCodeNumber: chr “BHMBCCMKT01” “BHMBCCMKT01” “BHMBCCMKT01” ## “BHMBCCMKT01” ...
*   \## $ Capacity : int 577 577 577 577 577 577 577 577 577 577 ...
*   \## $ Occupancy : int 61 64 80 107 150 177 219 247 259 266 ...
*   \## $ LastUpdated : chr “2016-10-04 07:59:42” “2016-10-04 08:25:42” “2016-10-04 08:59:42” “2016-10-04 09:32:46” ...

Wide data has a column for each variable. For example, the current data format of the parking dataset is wide-format data. The parking dataset has 35,717 records and 4 variables. Let us display the first 6 rows of the DataFrame using the head() function:

*   head(parking\_df)
*   \## SystemCodeNumber Capacity Occupancy LastUpdated
*   \## BHMBCCMKT01 577 61 2016-10-04 07:59:42
*   \## BHMBCCMKT01 577 64 2016-10-04 08:25:42
*   \## BHMBCCMKT01 577 80 2016-10-04 08:59:42
*   \## BHMBCCMKT01 577 107 2016-10-04 09:32:46
*   \## BHMBCCMKT01 577 150 2016-10-04 09:59:48
*   \## BHMBCCMKT01 577 177 2016-10-04 10:26:49
*   
*   \# subset duplicated rows in the DataFrame
*   duplicated\_rows<- parking\_df %>% filter(duplicated(parking\_df))
*   
*   nrow(duplicated\_rows)
*   \## 216

As these duplicated rows are redundant, you should remove them for any further analysis, as shown:

*   \# remove 216 duplicate rows from the parking\_df
*   parking\_df<- parking\_df %>% distinct()
*   
*   \# number of rows in the updated DataFrame
*   nrow(parking\_df)
*   \## 35501

[Converting wide to long format data](#contents.xhtml#sc3_61a)

The melt() function is a useful tool for converting wide-format data into long-format data. This can be helpful for data analysis and visualization because many statistical and graphical methods require data to be in a long format.

One of the key arguments of melt() is id.vars. This argument specifies which columns to keep as ID variables in the long-format data. These columns will remain as they are, and each row in the output data will correspond to a unique combination of values in the ID variables.

In our parking dataset, SystemCodeNumber and LastUpdated uniquely identify each observation. So, they are good candidates for ID variables because each row represents a unique combination of SystemCodeNumber and LastUpdated.

*   \# convert the parking\_df from wide to long format data
*   parking\_melt<- melt(parking\_df, id.vars = c(“SystemCodeNumber”, “LastUpdated”))
*   
*   \# display first 6 rows of the melted DataFrame
*   head(parking\_melt)
*   
*   \## SystemCodeNumberLastUpdated variable value
*   \## BHMBCCMKT01 2016-10-04 07:59:42 Capacity 577
*   \## BHMBCCMKT01 2016-10-04 08:25:42 Capacity 577
*   \## BHMBCCMKT01 2016-10-04 08:59:42 Capacity 577
*   \## BHMBCCMKT01 2016-10-04 09:32:46 Capacity 577
*   \## BHMBCCMKT01 2016-10-04 09:59:48 Capacity 577
*   \## BHMBCCMKT01 2016-10-04 10:26:49 Capacity 577

The columns labeled Capacity and Occupancy are combined in a bigger category called Variable, while their respective measurements are stacked beneath the column value. To customize the default column headings for the melted columns (variable and value) in the long-format data, you can use the variable.name and value.name arguments. These arguments allow you to specify the names of the columns that will hold the variable names and values, respectively.

*   \# customize the default column headings of variable and value
*   parking\_melt<- melt(parking\_df, id.vars = c(“SystemCodeNumber”, “LastUpdated”),
*    variable.name = “parking\_variable”, 
*    value.name = “parking\_value”)
*   
*   \# print the first 6 rows of updated parking\_melt
*   head(parking\_melt)
*   
*   \## SystemCodeNumberLastUpdatedparking\_variableparking\_value
*   \## BHMBCCMKT01 2016-10-04 07:59:42 Capacity 577
*   \## BHMBCCMKT01 2016-10-04 08:25:42 Capacity 577
*   \## BHMBCCMKT01 2016-10-04 08:59:42 Capacity 577
*   \## BHMBCCMKT01 2016-10-04 09:32:46 Capacity 577
*   \## BHMBCCMKT01 2016-10-04 09:59:48 Capacity 577
*   \## BHMBCCMKT01 2016-10-04 10:26:49 Capacity 577

[Converting long to wide format data](#contents.xhtml#sc3_62a)

The reshape2 package provides multiple functions for casting data from long format to wide format. Since we often deal with DataFrames, we will focus on the dcast() function. If needed, acast() can also be used to convert to vectors, matrices, or arrays as well.

To use the dcast() function, you will need to specify a few arguments. First, you need to specify the DataFrame you want to cast, using the data argument. Next, you specify a formula using the formula argument. This formula will specify the variables you want to use to cast the data from long to wide format. You will also need to specify the column containing the valuesyou want to cast using the value.var argument. Finally, you can use the fun.aggregate argument to specify a function to apply to the data before casting it, if necessary.

Now, let us turn our attention to the long-format data parking\_melt that we created earlier and use it to revert to the original wide-format data:

*   \# convert the parking\_melt from long to wide format data
*   parking\_cast<- dcast(parking\_melt, SystemCodeNumber + LastUpdated ~ parking\_variable, value.var = “parking\_value”)
*   
*   \# display the first 6 rows of updated parking\_cast
*   head(parking\_cast)
*   
*   \## SystemCodeNumberLastUpdated Capacity Occupancy
*   \## BHMBCCMKT01 2016-10-04 07:59:42 577 61
*   \## BHMBCCMKT01 2016-10-04 08:25:42 577 64
*   \## BHMBCCMKT01 2016-10-04 08:59:42 577 80
*   \## BHMBCCMKT01 2016-10-04 09:32:46 577 107
*   \## BHMBCCMKT01 2016-10-04 09:59:48 577 150
*   \## BHMBCCMKT01 2016-10-04 10:26:49 577 177

We will look closely at the formula used in the dcast() function above in the following code:

*   SystemCodeNumber + LastUpdated ~ parking\_variable

This formula defines which variables to use to cast the data from long to wide format. In the formula, the tilde (~) separates the left-hand side (LHS) from the right-hand side (RHS). We have two ID variables on the LHS, SystemCodeNumber and LastUpdated. These variables will become the row names of the resulting wide-format data. On the RHS, we have parking\_variable, the column containing the variable names to use in the wide-format data.

By specifying both the row and column variables in the formula, it creates a wide-format DataFrame with one row for each unique combination of SystemCodeNumber and LastUpdated and one column for each unique value in the parking\_variable column.

The following figure illustrates the dcast() function—conversion of long to wide format data:

![](images/Figure4.1.png)

Figure 4.1:Illustration of dcast() function: convert of long to wide format data

[Grouping and summarizing data](#contents.xhtml#sc2_63a)

Next, to deepen your understanding of summarizing data based on grouped variables, we will utilize a wholesale customer’s dataset from the University of California Irvine Machine Learning Repository.

The Wholesale Customers Dataset refers to the spending behavior of 440 customers of a wholesale distributor. The dataset contains information on the annual spending in monetary units (M.U.) by each customer on different product categories: fresh products, milk products, grocery products, frozen products, detergents and paper products, and delicatessen products.

*   \# read wholesale customers dataset
*   wholesale\_df<- read.csv(“Wholesale customers data.csv”)
*   
*   \# structure of the DataFrame
*   str(wholesale\_df)
*   
*   ##’data.frame’: 440 obs. of 8 variables:
*   \## $ Channel : int 2 2 2 1 2 2 2 2 1 2 ...
*   \## $ Region : int 3 3 3 3 3 3 3 3 3 3 ...
*   \## $ Fresh : int 12669 7057 6353 13265 22615 9413 12126 7579 5963 6006 ...
*   \## $ Milk : int 9656 9810 8808 1196 5410 8259 3199 4956 3648 11093 ...
*   \## $ Grocery : int 7561 9568 7684 4221 7198 5126 6975 9426 6192 18881 ...
*   \## $ Frozen : int 214 1762 2405 6404 3915 666 480 1669 425 1159 ...
*   \## $ Detergents\_Paper: int 2674 3293 3516 507 1777 1795 3140 3321 1716 7425 ...
*   \## $ Delicassen : int 1338 1776 7844 1788 5185 1451 545 2566 750 2098 ...

In the following data, the levels 1, 2, and 3 in Region correspond to Lisbon, Oporto, and Other Region respectively. Levels 1 and 2 in Channel correspond to Horeca (Hotel/Restaurant/Café) and Retail respectively, as shown:

*   \# convert Region and Channel to factors with corresponding levels and labels
*   wholesale\_df<- wholesale\_df %>%
*   mutate(Region = factor(Region, levels = c(1, 2, 3), 
*    labels = c(“Lisbon”, “Oporto”, “Other Region”)), Channel = factor(Channel, levels = c(1, 2), 
*    labels = c(“Horeca”, “Retail”)))
*   
*   \# check the frequency of the columns Channel and Region
*   table(wholesale\_df$Channel)
*   
*   \## Horeca Retail
*   \## 298 142 
*   
*   table(wholesale\_df$Region)
*   \## Lisbon Oporto Other Region 
*   \## 77 47 316  
    
    | Note: The function mutate() generates additional columns based on existing variables. If a column with the same name already exists, it can also modify it. Furthermore, columns can be deleted by assigning their value as NULL. |
    | --- |
    

Here, mutate() function modifies two variables: Region and Channel. We use the factor() function within mutate() to convert the numeric values of the Region and Channel columns to factors with the corresponding levels and labels specified:

*   \# calculate the mean spending on each product category
*   spending\_summary<- wholesale\_df %>%
*   summarise(mean\_fresh = mean(Fresh),
*   mean\_milk = mean(Milk),
*   mean\_grocery = mean(Grocery),
*   mean\_frozen = mean(Frozen),
*   mean\_detergents\_paper = mean(Detergents\_Paper),
*   mean\_delicatessen = mean(Delicassen))
*   
*   \# print the summary
*   spending\_summary
*   
*   \## mean\_freshmean\_milkmean\_grocerymean\_frozenmean\_detergents\_papermean\_delicatessen
*   \## 12000.3 5796.  7951.277 3071.932 2881.493 1524.87

In this code snippet, summarise() from dplyr package is used to calculate the mean spending on different product categories across the entire dataset. It is important to note that summarise() is most useful when used in conjunction with group\_by(), which changes the unit of analysis from the entire dataset to specific groups defined by a certain column:

*   \# group by region and calculate the mean spending on Fresh, Milk, and Grocery product category
*   grouped\_data1<- wholesale\_df %>%
*   group\_by(Region)%>%
*   summarise(mean\_fresh = mean(Fresh),
*   mean\_milk = mean(Milk),
*   mean\_grocery = mean(Grocery))
*   
*   \# view the result
*   View(grouped\_data1)
*   
*   \## Region mean\_freshmean\_milkmean\_grocery
*   \## Lisbon 11102.727 5486.416 7403.078
*   \## Oporto 9888.681 5088.170 9219.596
*   \## Other Region 12533.472 5977.085 7896.364

The above code groups the data by region and then calculates the mean annual spending on three product categories for each region.

Next, calculate the total spending in a few product categories for the two customer channels (Horeca and Retail):

*   \# group by channel and calculate the total spending on product categories
*   grouped\_data2 <- wholesale\_df %>%
*   group\_by(Channel) %>%
*   summarise(total\_fresh = sum(Fresh),
*   total\_milk = sum(Milk),
*   total\_grocery = sum(Grocery))
*   
*   \# view the result
*   View(grouped\_data2)
*   
*   \## Channeltotal\_freshtotal\_milktotal\_grocery
*   \## Horeca 4015717 1028614 1180717
*   \## Retail 1264414 1521743 2317845
*   
*   \# group by region and channel, and calculate the number of customers in each group
*   grouped\_data3 <- wholesale\_df %>%
*   group\_by(Region, Channel) %>%
*   summarise(count = n())
*   
*   \# view the result
*   View(grouped\_data3)
*   
*   \## Region Channel count
*   \## Lisbon Horeca 59
*   \## Lisbon Retail 18
*   \## Oporto Horeca 28
*   \## Oporto Retail 19
*   \## Other Region Horeca 211
*   \## Other Region Retail 105

The above code groups the dataset by the Region and Channel columns using the group\_by function. It then calculates the number of customers in each group using the summarize function and the n() function, which counts the number of observations in each group. Each row of the resulting DataFrame corresponds to a unique combination of region and channel and shows the number of customers in that group.

Filtering on grouped data

Grouping data becomes typically valuable when combined with the summarise() function, allowing for concise calculations and summaries. However, it is worth noting that mutate() and filter() also provide convenient operations that can be performed within grouped data, as shown:

*   region\_high\_grocery\_spending<\-wholesale\_df %>%
*   group\_by(Region) %>%
*   filter(Grocery > mean(Grocery))

Here, by grouping the data by the Region variable, and filtering based on high spending on grocery products (greater than the mean spending within each region), you find a subset of customers who exhibit above-average spending on groceries within their respective regions. The filtered data will identify the regional variations in consumer behavior and preferences regarding grocery products.

Adding new columns on grouped data

*   \# Grouping by Region and calculating the total spending per region
*   region\_total\_spending<- wholesale\_df %>%
*   group\_by(Region) %>%
*   mutate(total\_spending = sum(Fresh, Milk, Grocery, Frozen, Detergents\_Paper, Delicassen))

By grouping the data by the Region variable and using the mutate() function, the code adds a new variable called total\_spending to the dataset. This new variable represents the sum of spending across different product categories within each region. The total spending per region can assist businesses in making informed decisions regarding resource allocation, regional spending disparities, and market segment identification.

[Merging data](#contents.xhtml#sc2_64a)

Let us look at ways to merge data in R:

[Binding Data: rbind() and cbind()](#contents.xhtml#sc3_65a)

The rbind() stands for row bind, allowing you to combine two or more DataFrames into a single DataFrame by stacking the rows on top of each other. To ensures that the columns in the resulting DataFrame are aligned correctly and have a consistent structure, the following conditions must be met:

• The DataFrames being combined must have the same column names.

• The DataFrames being combined must have the same number of columns.

• The order of the columns in the DataFrames being combined should be the same.

*   \# create a DataFrame
*   player\_df1<- data.frame(
*   Player\_Name = c(“Virat Kohli”, “Rohit Sharma”, “Suresh Raina”),
*    Score = c(102, 53, 45)
*   )
*   
*   \# create another DataFrame
*   player\_df2 <- data.frame(
*   Player\_Name = c(“Ravindra Jadeja”, “Hardik Pandya”),
*    Score = c(82, 64)
*   )

Here, we have two DataFrames, player\_df1 and player\_df2, with information about the scores of Indian cricket players in different matches. Now, let us say we want to combine these two DataFrames into one DataFrame that shows all the scores for all the players. We can use the rbind() function to do this. Take a look at the following code snippet:

*   \# combine the two DataFrames using rbind()
*   player\_df\_combined<- rbind(player\_df1, player\_df2)
*   
*   \# view the combined DataFrame
*   player\_df\_combined
*   
*   \## Player\_Name Score
*   \## Virat Kohli 102
*   \## Rohit Sharma 53
*   \## Suresh Raina 45
*   \## Ravindra Jadeja 82
*   \## Hardik Pandya 64

The cbind() represents column bind, which allows you to combine multiple DataFrames by appending the columns of one DataFrame next to another DataFrame. To ensure that the resulting DataFrame has a consistent structure, the DataFrames being combined must have the same number of rows.

*   \# Create a DataFrame with characteristics of the match 
*   match\_df<- data.frame(
*    Venue = c(“Mumbai”, “Delhi”, “Kolkata”),
*    Date = c(“2023-05-15”, “2023-05-16”, “2023-05-17”)
*   )
*   
*   \# Combine player\_df1 and match\_df using cbind
*   combined\_df<- cbind(player\_df1, match\_df)
*   
*   \# print combined\_df
*   combined\_df
*   
*   \## Player\_Name Score Venue Date
*   \## Virat Kohli 102 Mumbai 2022-05-15
*   \## Rohit Sharma 53 Delhi 2022-05-16
*   \## Suresh Raina 45 Kolkata 2022-05-17

[Joins: Inner, outer, left, and right](#contents.xhtml#sc3_66a)

In the database world, there is a powerful operation called a join that allows you to combine two tables based on a common column or variable. Similarly, in R, you can use a function called merge() to combine two DataFrames based on a shared column.

Think of it like putting together two puzzle pieces that fit together perfectly. The merge() helps you match the pieces based on a shared characteristic, like a name or ID number. Once the DataFrames are merged, you can use the combined information to do all sorts of analysis and visualizations. The below table defines the essential arguments of the merge() function.

| Argument  || Description |
| --- | --- |
| x || The first DataFrame you want to merge. |
| y || The second DataFrame you want to merge. |
| by || The column(s) you want to merge on. |
| all || A logical value indicating whether to include all observations (rows) from both DataFrames (an outer join). |
| all.x || A logical value indicating whether to include all observations from the first DataFrame, even if there are no matching rows in the second DataFrame (a left join). |
| all.y || A logical value indicating whether to include all observations from the second DataFrame, even if there are no matching rows in the first DataFrame (a right join). |

Table 4.4: Description of merge function arguments

Let us create a DataFrame called transactions that contains information about debit card transactions:

*   \# Create the transactions DataFrame
*   transactions<-data.frame(
*   transaction\_id=c(1,2,3,4,5,6,7,8,9),
*   transaction\_date=as.Date(c(“2023-05-01”,”2023-05-02”,”2023-05-03”,”2023-05-04”,  
    ”2023-05-04”,”2023-05-04”,”2023-05-05”,”2023-05-06”,”2023-05-07”)),
*   transaction\_amount=c(1050,  
    1075.50,2050.00,1120.00,190.75,1150.00,160.00,2580.50,1825.00),
*   customer\_id=c(101,102,103,104,105,106,107,108,109),
*   stringsAsFactors=FALSE
*   )
*   \# print transactions DataFrame
*   transactions
*   
*   \## transaction\_idtransaction\_datetransaction\_amountcustomer\_id
*   \## 1 2023-05-01 1050.00 101
*   \## 2 2023-05-02 1075.50 102
*   \## 3 2023-05-03 2050.00 103
*   \## 4 2023-05-04 1120.00 104
*   \## 5 2023-05-04 190.75 105
*   \## 6 2023-05-04 1150.00 106
*   \## 7 2023-05-05 160.00 107
*   \## 8 2023-05-06 2580.50 108
*   \## 9 2023-05-07 1825.00 109

Now let us create a second DataFrame called customers, containing customer information:

*   \# create the customers DataFrame
*   customers<- data.frame(
*   customer\_id = c(102, 103, 104, 105, 107, 108, 109, 110),
*   customer\_name = c(“Penny”, “Sheldon”, “Howard”, “Amy”, 
*   “Raj”, “Stuart”, “Emily”, “Missy”),
*   customer\_email = c(“penny@gmail.com”, “sheldon@gmail.com”,”howard@gmail.com”, “amy@gmail.com”, “raj@gmail.com”, NA, “emily@gmail.com”, NA),
*   stringsAsFactors = FALSE
*   )
*   \# print customers DataFrame
*   customers
*   
*   \## customer\_idcustomer\_namecustomer\_email
*   \## 102 Penny penny@gmail.com
*   \## 103 Sheldon sheldon@gmail.com
*   \## 104 Howard howard@gmail.com
*   \## 105 Amy amy@gmail.com
*   \## 107 Raj raj@gmail.com
*   \## 108 Stuart <NA>
*   \## 109 Emily emily@gmail.com
*   \## 110 Missy <NA>

Note that there are two missing values in the customer\_email column for customer\_ids 108 and 110.

Before you combine datasets, it is important to identify the primary key of each dataset. The primary key is a column or set of columns uniquely identifying each observation in your dataset. This means that no two observations should have the same primary key value. Now let us see how different mergers can be performed on these two DataFrames. 

*   Inner Join: An inner join returns only the rows with matching values in both DataFrames. It returns the intersection of the two DataFrames. To perform an inner join, you can use the merge() function without any additional arguments: 
    *   \# perform an inner join
    *   inner\_join\_df<- merge(transactions, customers, by = “customer\_id”)

In this case, the by parameter is set to customer\_id, the common variable between the two DataFrames. The resulting Data Frame inner\_join\_df will contain only the rows where the customer\_id values are present in both the transactions and customers DataFrames:

*   \# print inner\_join\_df
*   inner\_join\_df
*   
*   \## customer\_idtransaction\_idtransaction\_datetransaction\_amountcustomer\_name ##customer\_email
*   \## 102 2 2023-05-02 1075.50 Penny penny@gmail.com
*   \## 103 3 2023-05-03 2050.00 Sheldon sheldon@gmail.com
*   \## 104 4 2023-05-04 1120.00 Howard howard@gmail.com
*   \## 105 5 2023-05-04 190.75 Amy amy@gmail.com
*   \## 107 7 2023-05-05 160.00 Raj raj@gmail.com
*   \## 108 8 2023-05-06 2580.50 Stuart <NA>
*   \## 109 9 2023-05-07 1825.00 Emily emily@gmail.com

*   Outer Join:This type of join returns all the rows from both DataFrames and fills in any missing values with not available(NA) values. To perform an outer join, you can set the all argument to TRUE: 
    *   \# perform an outer join
    *   outer\_join\_df<- merge(transactions, customers, by = “customer\_id”, all = TRUE)

In this example, all the rows from both DataFrames will be included in the merged DataFrame, outer\_join\_df, and missing values (NA) will be used to fill the columns without matches:

*   \# print outer\_join\_df
*   outer\_join\_df
*   
*   \## customer\_idtransaction\_idtransaction\_datetransaction\_amountcustomer\_name ##customer\_email
*   \## 101 1 2023-05-01 1050.00 <NA><NA>
*   \## 102 2 2023-05-02 1075.50 Penny penny@gmail.com
*   \## 103 3 2023-05-03 2050.00 Sheldon sheldon@gmail.com
*   \## 104 4 2023-05-04 1120.00 Howard howard@gmail.com
*   \## 105 5 2023-05-04 190.75 Amy amy@gmail.com
*   \## 106 6 2023-05-04 1150.00 <NA><NA>
*   \## 107 7 2023-05-05 160.00 Raj raj@gmail.com
*   \## 108 8 2023-05-06 2580.50 Stuart <NA>
*   \## 109 9 2023-05-07 1825.00 Emily emily@gmail.com
*   \## 110 NA <NA> NA Missy <NA>

*   Left join:A left join returns all the rows from the left DataFrame, along with the matching rows from the right DataFrame. If there are no matching rows in the right DataFrame, the resulting DataFrame will contain NAs for the columns of the right DataFrame, as shown: 
    *   \# perform a left join
    *   left\_join\_df<- merge(transactions, customers, by = “customer\_id”, all.x = TRUE)

In the following case, the all.x parameter is set to TRUE to indicate that you want to keep all the rows from the transactions DataFrame and only include matching rows from the customers DataFrame:

*   \# print left\_join\_df
*   left\_join\_df
*   
*   \## customer\_idtransaction\_idtransaction\_datetransaction\_amountcustomer\_name ##customer\_email
*   \## 101 1 2023-05-01 1050.00 <NA><NA>
*   \## 102 2 2023-05-02 1075.50 Penny penny@gmail.com
*   \## 103 3 2023-05-03 2050.00 Sheldon sheldon@gmail.com
*   \## 104 4 2023-05-04 1120.00 Howard howard@gmail.com
*   \## 105 5 2023-05-04 190.75 Amy amy@gmail.com
*   \## 106 6 2023-05-04 1150.00 <NA><NA>
*   \## 107 7 2023-05-05 160.00 Raj raj@gmail.com
*   \## 108 8 2023-05-06 2580.50 Stuart <NA>
*   \## 109 9 2023-05-07 1825.00 Emily emily@gmail.com

*   Right join: In a right join, all the rows from the right DataFrame are included in the merged DataFrame, along with the matching rows from the left DataFrame. If there is no match for a row in the right DataFrame, then the columns from the left DataFrame will contain missing values (NA). To perform a right join, you can set the all.y argument to TRUE: 
    *   \# perform a right join
    *   right\_join\_df<- merge(transactions, customers, by = “customer\_id”, all.y = TRUE)

In the following case, the resulting DataFrame, right\_join\_df keeps all the rows from the customers DataFrame and only includes matching rows from the transactions DataFrame:

*   \# print right\_join\_df
*   right\_join\_df
*   
*   \## customer\_idtransaction\_idtransaction\_datetransaction\_amountcustomer\_name ##customer\_email
*   \## 102 2 2023-05-02 1075.50 Penny penny@gmail.com
*   \## 103 3 2023-05-03 2050.00 Sheldon sheldon@gmail.com
*   \## 104 4 2023-05-04 1120.00 Howard howard@gmail.com
*   \## 105 5 2023-05-04 190.75 Amy amy@gmail.com
*   \## 107 7 2023-05-05 160.00 Raj raj@gmail.com
*   \## 108 8 2023-05-06 2580.50 Stuart <NA>
*   \## 109 9 2023-05-07 1825.00 Emily emily@gmail.com
*   \## 110 NA <NA> NA Missy <NA>

[Conclusion](#contents.xhtml#sc2_67a)

In this chapter, we explored essential techniques for manipulating and transforming data to facilitate effective analysis. We began by discussing the concepts of long and wide data formats and demonstrated how to pivot data between these formats, which is crucial for supporting diverse analytical requirements. We then delved into grouping and summarizing data, covering how to filter on grouped data and add new columns, enabling more granular and insightful data analysis. Finally, we explored methods for merging data, including the use of rbind() and cbind() for binding data and different types of joins (inner, outer, left, and right) to combine datasets in flexible ways. Mastering these skills will significantly enhance your ability to handle complex datasets and derive meaningful insights from your analyses. Remember to continually practice, explore new packages and libraries, and test new approaches to maintain and enhance your expertise.

In the next chapter, we will explore various operations for handling dates and datetime objects, further expanding our data analysis and manipulation skills.

Join our book’s Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/fm1.png)

# [CHAPTER 5Working with Dates](#contents.xhtml#ch05a)

[Introduction](#contents.xhtml#sc2_68a)

Dates and times are crucial in many data analysis tasks. This chapter will guide you through various operations and techniques for working with dates and times. To start off, you will learn how to create date, time, and datetime using different types of inputs. Once you have a date/datetime object, you will learn how to extract specific components such as the year, month, and day. So, let us explore and understand how to handle dates and times step by step. By the end of this chapter, you will have a strong foundation in practical skills that will help you tackle typical date data analysis challenges.

[Structure](#contents.xhtml#sc2_69a)

In this chapter, we will discuss several key concepts related to working with date and time components:

*   Creating date and datetime objects
*   Retrieving date and time components
*   Modifying date and time components
*   Diving into electricity production data
*   Calculations with dates and times

[Objectives](#contents.xhtml#sc2_70a)

Beginning with the fundamentals, you will learn how to create, retrieve, and modify date and time objects. These skills will be put to the test in real-world scenarios using electricity production Data, where you will explore date operations, leading and lagging calculations, and the application of durations, periods, and intervals. With these skills, you will be able to analyze and interpret temporal data accurately and confidently.

[Creating date and datetime objects](#contents.xhtml#sc2_71a)

In this chapter, we will be using a couple of helpful packages. As we look at this chapter, we will discover how the lubridate package can significantly enhance our ability to manage and analyze temporal information. To install lubridate, we have two options.

One is installing the entire tidyverse suite, which includes lubridate and other useful packages for data manipulation and visualization. To get started with the Tidyverse collection of packages, first install and load it using the following commands:

1.  install.packages("tidyverse")
2.  library(tidyverse)

Alternatively, you can install lubridate individually:

1.  install.packages("lubridate")
2.  library(lubridate)

Let us start with understanding three primary types of date/time data that refer to specific moments in time: dates, times within a day, and date-times. In our data analysis, we have to deal with dates or date-times.

From strings

Dates are often used when the exact time of an event is not relevant, but rather the day itself. Consider a scenario where your dataset contains a column of dates presented in various formats, like Sep 02, 2023. The order of these dates may differ; some might be in the format of month-day-year, while others could be in the order of year-month-day.

To efficiently transform these date strings into date objects, the lubridate package offers a range of functions tailored to different date element orders. These functions are named using a combination of the initial letters representing essential date and time elements:

*   Date components include y for year, m for month, and d for day.
*   Time components consist of h for hour, m for minute, and s for seconds.

The sequence of these components in the function name dictates how to provide your date and time information as strings. For instance, if your dates are structured as month-day-year, you would use the mdy() function to convert them into date objects. Conversely, if your dates are organized as year-month-day, the ymd() function is the appropriate choice.

In essence, lubridate provides functions to handle every conceivable arrangement of m, d, and y in the date data, making the transformation process seamless, regardless of the date format variations in your dataset.

1.  \# create a Date Object from a String
2.  
3.  ymd("2023-08-30")
4.  \## "2023-08-30"
5.  
6.  ymd("20230830")
7.  \## "2023-08-30"
8.  
9.  mdy("09 02 2023")
10.  \## "2023-09-02"
11.  
12.  dmy("31-Aug-2023")
13.  \## "2023-08-31"

To create a date-time object, add an underscore and one or more of h (hour), m (minute), and s (second) to the aforementioned functions. This allows you to precisely specify not only the date but also the time components. 

For instance, if your data includes date-time strings like 2023-09-02 14:30:45, where you have both the date and time in year-month-day hour:minute:second format, you would use the ymd\_hms() function to parse it:

1.  ymd\_hms("2023\-09-02 14:30:45")
2.  2.# "2023-09-02 14:30:45 UTC"

Alternatively, if your data contains date-time strings in a different format like "09/02/2023 14:30", where you have the date and time in month/day/year hour:minute format, you can use the mdy\_hm() function to parse it:

1.  mdy\_hm("09/02/2023 14:30")
2.  \## "2023-09-02 14:30:00 UTC"
3.  
4.  class(ymd("2023-08-30"))
5.  ##"Date"
6.  
7.  class(ymd\_hms("2023-09-02 14:30:45"))
8.  \## "POSIXct" "POSIXt" 
    
    | Note: Always aim to use the simplest data type that does the job well. If a date works instead of a date-time, go for it. Date-times are trickier because they must deal with time zones, making things more complex. |
    | --- |
    

Sometimes, you might not need to convert the date or date-times if your CSV or Excel sheet already follows ISO8601 format ^([1](#ch05.xhtml#footnote-000)).

From variables

In data analysis, it is common to encounter datasets where date information is spread across multiple columns, such as year, month, and day. To work with this data effectively, lubridate provides specific functions to convert such columns to a single date column.

For instance, we create the date\_data DataFrame with the individual date components: year, month, and day.

1.  \# create a dataframe with individual date components
2.  
3.  date\_data <- data.frame(
4.   year \= c(2023, 2022, 2021),
5.   month \= c(8, 12, 5),
6.   day \= c(24, 15, 3)
7.  )

We use the make\_date function from lubridate to create a unified date column. This function takes the individual date components (year, month, and day) as arguments and combines them into a single date object.

1.  \# add the new date column
2.  
3.  date\_data <- date\_data %>%
4.   mutate(full\_date \= make\_date(year, month, day))
5.  
6.  \# display the result
7.  print(date\_data)
8.  
9.  \## year month day full\_date
10.  \## 2023 8 24 2023-08-24
11.  \## 2022 12 15 2022-12-15
12.  \## 2021 5 3 2021-05-03
13.  
14.  str(date\_data$full\_date)
15.  \## Date\[1:3\], format: "2023-08-24" "2022-12-15" "2021-05-03"
16.  
17.  \# defaults for missing elements
18.  
19.  make\_date(year \= 2023, month \= 9) \# day = 1
20.  \# "2023-09-01"
21.  
22.  make\_date(month \= 9, day \= 15) \# year = 1970
23.  \# "1970-09-15"
24.  
25.  make\_date(year \= 2023, day \= 15) \# month = 1
26.  \# "2023-01-15"
27.  
28.  \# sample data with individual date and time components
29.  
30.  datetime\_data <- data.frame(
31.   year \= c(2023, 2022, 2021),
32.   month \= c(8, 12, 5),
33.   day \= c(24, 15, 3),
34.   hour \= c(10, 14, 8),
35.   minute \= c(30, 15, 45)
36.  )
37.  
38.  \# add the new datetime column
39.  
40.  datetime\_data <- datetime\_data %>%
41.   mutate(full\_datetime \= make\_datetime(year, month, day, hour, minute))
42.  

Inside mutate, we call the make\_datetime function from lubridate to combine the year, month, day, hour, and minute columns into a new full\_datetime column.

1.  \# display the result
2.  print(datetime\_data)
3.  
4.  \## year month day hour minute full\_datetime
5.  \## 2023 8 24 10 30 2023-08-24 10:30:00
6.  \## 2022 12 15 14 15 2022-12-15 14:15:00
7.  \## 2021 5 3 8 45 2021-05-03 08:45:00

[Retrieving date and time components](#contents.xhtml#sc2_72a)

lubridate offers you a friendly set of tools to dig into the specific elements of a date or time. Imagine you are working with fitness data from a smartwatch. You have a timestamp representing a morning run on Aug 25, 2023, at 6:30 AM. Now, let us look into this temporal data using lubridate functions.

1.  \# Create a timestamp for the morning run
2.  
3.  run\_timestamp <- ymd\_hm("2023-08-25 06:30")
4.  
5.  run\_timestamp
6.  \## "2023-08-25 06:30:00 UTC"
7.  
8.  \# Identifies the year
9.  year(run\_timestamp) 
10.  \## 2023
11.  
12.  \# Identifies the month
13.  month(run\_timestamp) 
14.  \## 8
15.  
16.  \# Identifies the day of the month 
17.  mday(run\_timestamp) 
18.  \## 25
19.  
20.  \# Identifies the day of the year 
21.  yday(run\_timestamp) 
22.  \## 237
23.  
24.  \# Identifies the day of the week (Friday, represented as 6)
25.  wday(run\_timestamp) 
26.  \## 6
27.  
28.  \# Setting label = TRUE displays the day of the week as an ordered factor
29.  wday(run\_timestamp, label = T)
30.  \## Fri
31.  \## Levels: Sun < Mon < Tue < Wed < Thu < Fri < Sat

[Modifying date and time components](#contents.xhtml#sc2_73a)

Although less common in typical data analysis tasks, the capability of modifying date and time components proves invaluable when cleaning data with erroneous dates. Let us consider the following datetime example where you have a datetime object representing an event on 2023-09-15 14:30:45. You need to adjust its day to 14 and time to 4:45 PM.

1.  \# create a datetime object
2.  
3.  event\_datetime <- ymd\_hms("2023-09-15 14:30:45")
4.  
5.  \# display the original datetime
6.  
7.  event\_datetime
8.  \## "2023-09-15 14:30:45 UTC"
9.  
10.  \# update multiple components: change to September 14, 2023, at 16:45:00
11.  event\_datetime <- update(
12.  
13.   event\_datetime,
14.   day = 14,
15.   hour = 16,
16.   minute = 45,
17.   second = 00
18.  )
19.  
20.  \# display the updated datetime
21.  
22.  event\_datetime
23.  \## 2023-09-14 16:45:00 UTC

[Diving into electricity production data](#contents.xhtml#sc2_74a)

Now, we will explore a dataset containing monthly electricity production and trade statistics for member countries of the Organization for Economic Co-operation and Development (OECD) and electricity production data for a handful of other economies. This dataset has been sourced from the International Energy Agency (IEA)'s Monthly Electricity Statistics 2023. Our aim is to pull specific components within this temporal data. The following table provides a description of each column in the MonthlyElectricityStatistics dataset:

| Column name || Description |
| --- | --- |
| Country || Name of the country |
| --- | --- |
| Time || Date. Represents month and year |
| Balance || Contains various categories that describe the state of electricity production and consumption. These categories include net electricity production, usage for pumped storage, distribution losses, calculated final consumption, total imports, total exports, and additional remarks. |
| Product || Categorizes energy sources and related data. It includes electricity, various fuel types, renewables like wind, solar, etc. |
| Value || Value of the particular month of the year |
| Unit || Units in GWh |

Table 5.1: Description of monthly electricity dataset columns

Use the following code to read the CSV file and understand the structure of the resulting DataFrame:

1.  \# read the CSV file
2.  monthly\_electricity <- read.csv("MonthlyElectricityStatistics.csv")
3.  
4.  \# structure of the monthly\_electricity dataframe
5.  str(monthly\_electricity)
6.  
7.  \## 'data.frame': 132833 obs. of 6 variables:
8.  \## $ Country: chr "Australia" "Australia" "Australia" "Australia" ...
9.  \## $ Time : chr "May 2023" "May 2023" "May 2023" "May 2023" ...
10.  \## $ Balance: chr "Net Electricity Production" "Net Electricity Production" "Net Electricity ##Production" "Net Electricity Production" ...
11.  \## $ Product: chr "Electricity" "Total Combustible Fuels" "Coal, Peat and Manufactured Gases" ##"Oil and Petroleum Products" ...
12.  \## $ Value : num 22310 15224 10447 386 4118 ...
13.  \## $ Unit : chr "GWh" "GWh" "GWh" "GWh" ...
14.  
15.  \# display the first 6 rows of the dataset
16.  head(monthly\_electricity)
17.  
18.  \## Country Time Balance Product Value Unit
19.  \## Australia May 2023 Net Electricity Production Electricity 22309.8804 GWh
20.  \## Australia May 2023 Net Electricity Production Total Combustible Fuels 15224.3408 GWh
21.  \## Australia May 2023 Net Electricity Production Coal, Peat and Manufactured Gases 10446.8998 GWh
22.  \## Australia May 2023 Net Electricity Production Oil and Petroleum Products 385.5876 GWh
23.  \## Australia May 2023 Net Electricity Production Natural Gas 4117.5758 GWh
24.  \## Australia May 2023 Net Electricity Production Combustible Renewables 274.2775 GWh
25.  
26.  \# datatype of the column Time
27.  
28.  class(monthly\_electricity$Time)
29.  \## "character"

Let us prepare our monthly\_electricity dataset for analysis. The Time column in our dataset is formatted as Month Year (e.g., May 2023). To work with this data effectively, we are adding a day component, specifically '01', to each date. This step ensures that we have complete date strings (01 May 2023), which we can then parse and use for further analysis.

1.  \# add a day component (e.g., 01) and parse the date
2.  
3.  monthly\_electricity <- monthly\_electricity %>%
4.   mutate(
5.   Time = dmy(paste("01", Time))
6.   )

In the following code, we are adding Month, Year, and Quarter columns in our monthly\_electricity dataset for precise temporal analysis. Subsequently, we focus on India's electricity data within the Electricity product category, filtering data from 2021 onwards. We then group and summarize this information by quarters, calculating total and average values. 

1.  \# extract different components from Time
2.  
3.  monthly\_electricity <- monthly\_electricity %>%
4.   mutate(
5.   Month = month(Time),
6.   Year = year(Time),
7.   Quarter = quarter(Time, type = "year.quarter")
8.   )
9.  
10.  head(monthly\_electricity)
11.  
12.  \## Country Time Balance Product Value Unit Month
13.  \## Australia 2023-05-01 Net Electricity Production Electricity 22309.8804 GWh 5
14.  \## Australia 2023-05-01 Net Electricity Production Total Combustible Fuels 15224.3408 GWh 5
15.  \## Australia 2023-05-01 Net Electricity Production Coal, Peat and Manufactured Gases 10446.8998 GWh 5
16.  \## Australia 2023-05-01 Net Electricity Production Oil and Petroleum Products 385.5876 GWh 5
17.  \## Australia 2023-05-01 Net Electricity Production Natural Gas 4117.5758 GWh 5
18.  \## Australia 2023-05-01 Net Electricity Production Combustible Renewables 274.2775 GWh 5
19.  \## Year Quarter
20.  \## 2023 2023.2
21.  \## 2023 2023.2
22.  \## 2023 2023.2
23.  \## 2023 2023.2
24.  \## 2023 2023.2
25.  \## 2023 2023.2
26.  
27.  \# subset the electricity\_subset dataframe
28.  
29.  electricity\_subset <- monthly\_electricity %>%
30.   filter(Country == "India", Product == "Electricity", Year >= 2021)
31.  
32.  \# summarise the electricity\_subset dataset
33.  
34.  summary\_electricity <- electricity\_subset %>%
35.   group\_by(Quarter) %>%
36.   summarize(Total\_Value = sum(Value),
37.   Average\_Value = mean(Value))
38.  
39.  \# display the summary\_electricity dataframe
40.  
41.  View(summary\_electricity)
42.  
43.  \## Quarter Total\_Value Average\_Value
44.  \## 2021.1 386916.7 128972.2
45.  \## 2021.2 389065 129688.3
46.  \## 2021.3 413978.2 137992.7
47.  \## 2021.4 370094.3 123364.8
48.  \## 2022.1 393960.4 131320.1
49.  \## 2022.2 439537.5 146512.5
50.  \## 2022.3 422333.3 140777.8
51.  \## 2022.4 393441.4 131147.1
52.  \## 2023.1 422806.5 140935.5
53.  \## 2023.2 301012.8 150506.4

[Calculations with dates and times](#contents.xhtml#sc2_75a)

In this section, we will explore how to calculate lead and lag values, durations, periods, and intervals using the lubridate package.

[Leading and lagging calculations](#contents.xhtml#sc3_76a)

The functions lead() and lag() from the dplyr package enables us to access previous (lagged) or subsequent (leading) values in a sequence, whether it is a numeric progression or a date sequence. These functions become particularly apparent when you need to compute changes or differences between consecutive time units.

However, it is crucial to note that the order of rows in your dataset carries significant importance when using lead() or lag(). Whether your dates or numbers are arranged in ascending or descending order can profoundly impact the results. 

In the following analysis, we will explore the electricity\_subset dataset by introducing a previous\_month\_Value column, to monitor values from the preceding month. Building on this, we will compute the value compared to the previous month, the numerical differences between consecutive months. We will also represent these variances as percentages in the Percentage\_Difference column.

1.  \# create previous\_month\_Value column
2.  
3.  electricity\_subset <- electricity\_subset %>%
4.   select(Time, Value) %>%
5.   mutate(
6.   previous\_month\_Value = lead(Value)
7.   )
8.  
9.  \# calculate 'Value compared to previous month' and Percentage\_Difference
10.  
11.  electricity\_subset <- electricity\_subset %>%
12.   mutate(
13.   Value\_Compared\_To\_Previous\_Month = Value - previous\_month\_Value,
14.   Percentage\_Difference = round(((Value - previous\_month\_Value) / previous\_month\_Value) \* 100, 2)
15.   )
16.  
17.  head(electricity\_subset)
18.  
19.  \## Time Value previous\_month\_Value Value\_Compared\_To\_Previous\_Month Percentage\_Difference
20.  \## 2023-05-01 153915.5 147097.3 6818.226 4.64
21.  \## 2023-04-01 147097.3 144378.1 2719.146 1.88
22.  \## 2023-03-01 144378.1 134485.0 9893.172 7.36
23.  \## 2023-02-01 134485.0 143943.4 -9458.418 -6.57
24.  \## 2023-01-01 143943.4 138183.0 5760.381 4.17
25.  \## 2022-12-01 138183.0 128644.9 9538.127 7.41

In lubridate package, there are multiple ways to represent a time span—through durations, periods, and intervals. Each representation serves its unique purpose and offers distinct functionalities.

[Durations](#contents.xhtml#sc3_77a)

Duration allows you to measure periods of time in terms of seconds. Lubridate package also provides several functions to work with durations such as dweeks(), ddays(), dminutes() and dseconds(). With these functions, you can easily convert between different units of time and perform calculations on them.

The following example tracks the duration of service downtime incidents to assess their impact. It creates a vector of downtime durations using the duration function and calculates the total downtime by adding up the given list of downtime durations.

1.  \# downtime durations
2.  
3.  downtime\_durations <- c(duration(hours = 1), duration(minutes = 30), duration(hours = 2))
4.  
5.  downtime\_durations
6.  \## "3600s (~1 hours)" "1800s (~30 minutes)" "7200s (~2 hours)" 
7.  
8.  class(downtime\_durations)
9.  \## "Duration"
10.  \## attr(,"package")
11.  \## "lubridate"
12.  
13.  \# calculate total downtime
14.  
15.  total\_downtime <- sum(downtime\_durations)
16.  
17.  total\_downtime
18.  \## 12600

[Periods](#contents.xhtml#sc3_78a)

Periods are flexible representations of time spans that allow you to work with human-friendly units such as years, months, weeks, days, hours, minutes, and seconds. Unlike durations, periods do not specify a fixed length in seconds but instead adjust their length based on the underlying date-time. This makes periods ideal for tracking changes in clock time over long periods without worrying about specific second-level details. Lubridate provides various methods to manipulate periods, including addition and subtraction operations, making it easy to perform complex temporal analysis tasks.

Let us look at an example of setting up reminders for subscription renewals by defining the renewal period in weeks:

1.  \# subscription renewal periods
2.  
3.  renewal\_periods <- c(period(weeks = 2), period(weeks = 4), period(weeks = 6))
4.  
5.  renewal\_periods
6.  \## “14d 0H 0M 0S” “28d 0H 0M 0S” “42d 0H 0M 0S”
7.  
8.  class(renewal\_periods)
9.  \## "Period"
10.  \## attr(,"package")
11.  \## "lubridate"
12.  
13.  \# Sys.Date() returns the present day 
14.  Sys.Date()
15.  \## "2023-09-10"
16.  
17.  \# calculate renewal dates
18.  renewal\_dates <- Sys.Date() + renewal\_periods
19.  
20.  print(renewal\_dates)
21.  \## "2023-09-24" "2023-10-08" "2023-10-22"

[Intervals](#contents.xhtml#sc3_79a)

Intervals provide a way to define a time range between two specific points, allowing for greater precision when working with date-time data. The interval() function from lubridate creates an Interval object representing the specified start and end dates. The following code schedules events by defining intervals with start and end times.

1.  \# define event intervals
2.  
3.  event\_intervals <- c(interval(ymd\_hms("2023-08-01 10:00:00"), ymd\_hms("2023-08-01 12:00:00")), 
4.   interval(ymd\_hms("2023-08-03 15:30:00"), ymd\_hms("2023-08-03 17:00:00")))
5.  
6.  event\_intervals
7.  \## 2023-08-01 10:00:00 UTC--2023-08-01 12:00:00 UTC 2023-08-03 15:30:00 UTC--2023-08-03 17:00:00 UTC
8.  
9.  class(event\_intervals)
10.  \## "Interval"
11.  \## attr(,"package")
12.  \## "lubridate"
13.  
14.  \# check if an event overlaps with a specific time
15.  
16.  check\_time <- ymd\_hms("2023-08-01 11:30:00")
17.  overlapping\_events <- event\_intervals\[check\_time %within% event\_intervals\]
18.  
19.  print(overlapping\_events)
20.  \## 2023-08-01 10:00:00 UTC--2023-08-01 12:00:00 UTC

[Conclusion](#contents.xhtml#sc2_80a)

After completing this chapter on working with dates and times, you can now navigate and manipulate temporal data. You have learned how to create and modify date and datetime objects, retrieve relevant components such as year, month, day, hour, minute, and second, and perform various calculations like leading and lagging. We also learned to analyze temporal data using durations, periods, and intervals.

Now that you have gained a solid foundation in working with dates and times, you can move on to the next chapter, where you will learn how to work with strings.

* * *

[1](#ch05.xhtml#footnote-000-backlink). ISO 8601 is an international standard covering the worldwide exchange and communication of date and time-related data - Wikipedia

# [CHAPTER 6Manipulating Strings](#contents.xhtml#ch06a)

[Introduction](#contents.xhtml#sc2_81a)

Real-world datasets often contain a substantial amount of text alongside numeric and logical data. Whether you are working with customer reviews, social media comments, or survey responses, text data hides invaluable insights. However, raw text data often contains noise, inconsistencies, and other issues that must be addressed before it can be analyzed appropriately. In this chapter, you will be introduced to a comprehensive set of string manipulation functions, helping you to tackle common challenges associated with text data. You will learn how to cleanse text, extract relevant information, and convert text data into a structured form suitable for further analysis.

[Structure](#contents.xhtml#sc2_82a)

This chapter will explore and discuss various fundamental concepts associated with manipulating strings. We will discuss the following topics in this chapter:

*   Essential string manipulations 
    *   Changing case
    *   Calculating string length
    *   Replacing substrings
    *   Removing unnecessary whitespaces
    *   Padding
*   Concatenating strings
*   Extracting substrings
*   Regular expressions 
    *   Regex ingredients
    *   Greedy and non-greedy matching
*   Detecting and extracting patterns

[Objectives](#contents.xhtml#sc2_83a)

This chapter aims to provide an in-depth understanding of string manipulation techniques using the stringr package. This chapter covers essential string manipulations such as cleaning and manipulating strings, changing cases, calculating string length, replacing substrings, removing unnecessary whitespaces, padding, and concatenating strings. This chapter also covers extracting substrings from strings using the str\_sub() and str\_extract() functions. Extracting substrings is a typical operation in data science, as it is often necessary to extract specific pieces of information from strings, like the date from a timestamp. This chapter also introduces regular expressions (regex), which are helpful for searching and manipulating text. A regular expression is a set of characters that collectively form a pattern for searching, validating, and extracting information within strings. They can be used to find and extract specific patterns from strings, such as email addresses, phone numbers, and dates.

[Essential string manipulations](#contents.xhtml#sc2_84a)

Throughout this chapter, we will utilize functions from the stringr package, which forms an integral part of the Tidyverse ecosystem. The stringr package provides efficient and effective tools for performing string manipulation tasks. To begin, we load the necessary packages for data manipulation.

1.  \# load tidyverse
2.  library(tidyverse)
3.  
4.  \# install stringr
5.  install.packages("stringr")
6.  
7.  \# load stringr
8.  library(stringr)

stringr offers a wide range of functions for handling text data, including those for basic string manipulations like trimming whitespace and converting cases, as well as more advanced features like regular expression matching. Its consistent naming convention makes it easy to remember which functions do what, allowing you to focus on solving problems rather than memorizing syntax. In RStudio, you can type str\_ and press the Tab key to view a list of available string manipulation functions in the stringr package. This shortcut allows you to easily access and select the desired function without typing out its full name.

[Table 6.1](#ch06.xhtml#tab6-1) lists some of the most essential and widely used stringr functions for string manipulation:

| stringr function || Description || Equivalent Base R function |
| --- | --- | --- |
| str\_to\_lower() || Converts a string to lowercase. || tolower() |
| str\_to\_upper() || Converts a string to uppercase. || toupper() |
| str\_length() || Returns the number of characters in a string. || nchar() |
| str\_replace() || Replaces the first occurrence of a pattern in a string with a replacement string. || sub() |
| str\_replace\_all() || Replace all occurrences of a pattern in a string with a replacement string. || gsub() |
| str\_trim() || Removes leading and trailing whitespace from a string. || trimws() |
| str\_squish() || Removes all consecutive whitespace from a string. || NA |
| str\_pad() || Pads a string to a specified length with a specified padding character. || NA |
| str\_c() || Concatenates two or more strings. || paste() or paste0() |
| str\_sub() || Extracts a substring || substr() |

Table 6.1: A list of essential stringr functions

These functions can be used to perform a wide range of string operations, such as converting strings to different cases, removing whitespace, replacing characters, and combining substrings.

Imagine you are responsible for creating new product pages and ensuring they are optimized for search engines. Creating well-structured URLs is one of the most important aspects of search engine optimization (SEO). When creating URLs, it is essential to follow certain best practices. These best practices can help improve your product pages' SEO and make them more user-friendly.

Now, you will create URL names from specific data points available, such as product name, product category, and product ID. You could manually create each URL name, which would be time-consuming and error-prone. A better approach would be to use stringr to create URL names from data points and automate the process.

First, we create a data frame called books with three columns: product name, product category, and product id. The product name column includes the names of the products, the product category column contains the categories of the products, and the product id column contains the unique identifiers for the products.

1.  \# Create a data frame of product data
2.  books <- data.frame(product\_name = c("Mastering MEAN Stack", " Breaking Ransomware", "Data Science with R ", "Learning Google Cloud Vertex AI"),
3.   product\_category = c("Web Development ", " Security ", "Machine Learning & AI", "Cloud & Networking"),
4.   product\_id = c(255, 78, 7077, 537))
5.  
6.  \# Display the data frame
7.  View(books)

| product\_name || product\_category || product\_id |
| --- | --- | --- |
| Mastering MEAN Stack || Web development || 255 |
| Breaking ransomware || Security || 78 |
| Data science with R || ML and AI || 7077 |
| Learning Google Cloud Vertex AI || Cloud and networking || 537 |

Table 6.2: Output of View(books)

[Changing case](#contents.xhtml#sc3_85a)

Next, we will use the mutate() function to update the columns product name and product category in lowercase. The mutate() takes a data frame and a list of expressions as input and returns a new data frame with the new or updated columns.

Converting product names and categories to lowercase before creating URLs has several benefits. Firstly, it is considered a best practice for search engine optimization (SEO) as search engines tend to index and rank URLs in lowercase more effectively. Secondly, lowercase URLs are more accessible for users to understand and remember, making them more user-friendly. The code below uses the str\_to\_lower() function to convert the product names and product categories to lowercase.

1.  \# Changing case of product\_name and product\_category 
2.  books <- books %>%
3.   mutate(product\_name = str\_to\_lower(product\_name),
4.   product\_category = str\_to\_lower(product\_category))
5.  
6.  \# Display books
7.  View(books)

| product\_name || product\_category || product\_id |
| --- | --- | --- |
| Mastering mean stack || Web development || 255 |
| Breaking ransomware || Security  || 78 |
| Data science with R || ML and AI || 7077 |
| Learning Google Cloud Vertex AI || Cloud and networking || 537 |

Table 6.3: Books data with standardized case

As you can see, the product name and product category columns are now in lowercase. You can use the str\_to\_upper() function to convert a string to uppercase. Converting strings to lowercase or uppercase in text analysis is fundamental when working with text data. This transformation is necessary when comparing strings, eliminating case sensitivity, or formatting strings uniformly.

For instance, imagine you have a database of customer names and email addresses. Some entries might be in uppercase, while others are in lowercase. To identify and remove duplicate records accurately, you would convert all names and emails to either uppercase or lowercase. This way, you prevent mistakenly treating [business@bpbonline.com](mailto:business@bpbonline.com) and [Business@bpbonline.com](mailto:Business@bpbonline.com) as separate entries, ensuring data integrity.

[Calculating string length](#contents.xhtml#sc3_86a)

Let us now calculate the length of the column product name using the str\_length() function. We calculate the length of each product name as follows:

1.  \# Calculate the length of the product\_name
2.  books <- books %>%
3.   mutate(product\_name\_length = str\_length(product\_name))
4.  
5.  \# View the modified data frame
6.  View(books)

Refer to the following table:

| product\_name || product\_category || product\_id || product\_name\_length |
| --- | --- | --- | --- |
| Mastering mean stack || Web development || 255 || 20 |
| Breaking ransomware || Security  || 78 || 20 |
| Data science with R || ML and AI || 7077 || 20 |
| Learning Google Cloud Vertex Ai || Cloud and networking || 537 || 31 |

Table 6.4: Books data with product name length

The str\_length() function in text analysis has a diverse set of capabilities, including:

*   Validating input data: The str\_length() function can validate input data by checking its length against a specified criterion. For instance, in a password validation function, you can use str\_length() to ensure the input password is at least eight characters long. If the password is shorter than eight characters, the function can return an error message or reject the input altogether.
*   Formatting output data: To format output data by padding strings to a fixed length. This can be useful when displaying data in a table or report, where consistent formatting is essential. For example, add leading spaces to a string until it reaches a specified length, ensuring that all rows in the table have the same column width.
*   Analyzing text data: To calculate various metrics related to string lengths. For instance, to calculate the average length of words in a sentence or to find the longest word in a paragraph.

[Replacing substrings](#contents.xhtml#sc3_87a)

Removing special characters, like & from URL links, is generally recommended because different web browsers and servers can interpret special characters differently.

The below code uses the str\_replace\_all() to replace all occurrences of the ampersand character (&) in the product category column of the books data frame with an empty string.

*   \# Replacing substring from the column product\_category
*   books <- books %>%
*    mutate(product\_category = str\_replace\_all(product\_category, "&", ""))
*   
*   \# View the data frame
*   View(books)

| product\_name || product\_category || product\_id || product\_name\_length |
| --- | --- | --- | --- |
| Mastering mean stack || Web development || 255 || 20 |
| Breaking ransomware || Security || 78 || 20 |
| Data science with R || ML and AI || 7077 || 20 |
| Learning Google Cloud Vertex Ai || Cloud networking || 537 || 31 |

Table 6.5: Books data with ampersand removed from product categories

The str\_replace\_all() is a string manipulation function that replaces all occurrences of a pattern in a string with a replacement string. In this case, the pattern is the ampersand character (&), and the replacement string is an empty string.

The str\_replace\_all() function can be used for a variety of text analysis tasks, such as removing stop words. Stop words are common words that are not very informative, such as and, the, is replacing abbreviations with their full forms, correcting spelling errors, etc. The str\_replace() function is similar to str\_replace\_all(), but it only targets and replaces the specified substring's first occurrence. This can be useful when you want to perform a one-time substitution without affecting subsequent occurrences of the same word.

[Removing unnecessary whitespaces](#contents.xhtml#sc3_88a)

In text analysis, the str\_trim() and str\_squish() functions are often used to clean and preprocess text data before applying other techniques such as sentiment analysis, topic modeling, or ML algorithms.

The str\_trim() function removes whitespace characters from the beginning and end of a string, which can help to normalize the data. It takes one argument, the string, to be trimmed.

1.  \# Remove leading and trailing spaces in product\_name and product\_category
2.  books <- books %>%
3.   mutate(product\_name = str\_trim(product\_name),
4.   product\_category = str\_trim(product\_category))
5.  
6.  \# Display the modified data frame
7.  View(books)

| product\_name || product\_category || product\_id || product\_name\_length |
| --- | --- | --- | --- |
| Mastering mean stack || Web development || 255 || 20 |
| Breaking ransomware || Security || 78 || 20 |
| Data science with R || ML and AI || 7077 || 20 |
| Learning Google Cloud Vertex Ai || Cloud networking || 537 || 31 |

Table 6.6: Books Data with Trimmed Product Names and Categories

Notice how the leading and trailing spaces around each book title and category have been removed. On the other hand, str\_squish() trims leading and trailing spaces like str\_trim(), reducing multiple consecutive spaces within the text to a single space. In the below code, we are replacing all internal whitespace from the product category column with a single space.

1.  \# Apply str\_squish() to product\_category column
2.  books <- books %>%
3.   mutate(product\_category = str\_squish(product\_category))
4.  
5.  \# View the data frame
6.  View(books)

| product\_name || product\_category || product\_id || product\_name\_length |
| --- | --- | --- | --- |
| Mastering mean stack || Web development || 255 || 20 |
| Breaking ransomware || Security || 78 || 20 |
| Data science with R || ML and AI || 7077 || 20 |
| Learning Google Cloud Vertex AI || Cloud networking || 537 || 31 |

Table 6.7: Books data with standardized product categories

This output condenses consecutive whitespace characters into a single space, making the strings more concise. Furthermore, using hyphens (-) instead of spaces to separate words in URLs is a good practice to help users and search engines read and understand them better. To achieve this, we will replace all spaces in product names and categories with hyphens.

1.  \# Replacing all spaces in product names and categories with hyphens
2.  books <- books %>%
3.   mutate(product\_name = str\_replace\_all(product\_name, " ", "-"),
4.   product\_category = str\_replace\_all(product\_category, " ", "-"))
5.  
6.  \# Display the dataframe
7.  View(books) 
    
    | product\_name || product\_category || product\_id || product\_name\_length |
    | --- | --- | --- | --- |
    | Mastering MEAN Stack || Web development || 255 || 20 |
    | Breaking ransomware || Security || 78 || 20 |
    | Data science with R || ML and AI || 7077 || 20 |
    | Learning Google Cloud Vertex AI || Cloud networking || 537 || 31 |
    

Table 6.8: Books data with spaces replaced in product names and categories

[Padding](#contents.xhtml#sc3_89a)

Padding is a technique that can be used to ensure that all of the data points have the same length. The str\_pad() function pads a string to a specified length with a specified padding character. This is particularly useful when you need to standardize the length of strings, such as when working with codes or identifiers. It takes four arguments:

*   string: The string to be padded.
*   width: The desired length of the padded string.
*   side: The side of the string to the pad. It can be one of left, right, or both.
*   pad: The padding character. 
    1.  \# Using str\_pad() to standardize product\_id with leading zeros
    2.  books <- books %>%
    3.   mutate(product\_id = str\_pad(product\_id, width = 4, side = "left", pad = "0"))
    4.   
    5.  \# View the dataframe
    6.  View(books)

You can see that the str\_pad() is a valuable function for text analysis tasks where you need to pad strings to a consistent length.

When working with text data, such as sentences or paragraphs, it is expected to encounter sequences of varying lengths. Deep learning models such as LSTM and transformer models often expect input sequences of fixed dimensions. In such cases, padding ensures that all sequences are of the same length.

[Concatenating strings](#contents.xhtml#sc2_90a)

The str\_c() function combines multiple character vectors into a single character vector. It takes two or more arguments, which are the character vectors, to be combined. The str\_c() is a handy function for text analysis tasks where you need to combine multiple strings into one string.

Now, you will use str\_c() to create the unique product URLs for each product in the books DataFrame.

1.  \# Using str\_c() to generate unique product URLs
2.  books <- books %>%
3.   mutate(product\_url = str\_c("https://in.bpbonline.com/", "collections/", product\_category, "/", product\_name, "/", product\_id))

In the above code, we create a new column called product\_url using the str\_c() function. Here, we are combining the following:

*   [https://in.bpbonline.com/](https://in.bpbonline.com/): Base URL for the online store.
*   collections/: This directory path will be appended to the base URL.
*   product\_category: The name of each product category. We are using it here to dynamically generate the directory path for each product.
*   /: Forward slash character that separates the directory path from the product name.
*   product\_name: The name of each product.
*   /: Another forward slash character that separates the product name from the product ID.
*   product\_id: The unique identifier for each product. 
    1.  \# Display the product\_url column
    2.  books %>% select(product\_url)
    3.  \## product\_url
    4.  
    5.  \## https://in.bpbonline.com/collections/web-development/mastering-mean-stack/0255
    6.  \## https://in.bpbonline.com/collections/security/breaking-ransomware/0078
    7.  \## https://in.bpbonline.com/collections/machine-learning-ai/data-science-with-r/7077
    8.  \## https://in.bpbonline.com/collections/cloud-networking/learning-google-cloud-vertex-ai/0537

You can see the resulting product\_url column will contain a unique URL for each product, following the format:

https://in.bpbonline.com/collections/\[product\_category\]/\[product\_name\]/\[product\_id\]

[Extracting substrings](#contents.xhtml#sc2_91a)

The str\_sub() function extracts a substring from a string based on a specified start and end index. It takes three arguments:

*   string: The string from which to extract the substring.
*   start: The start index of the substring.
*   end: The end index of the substring.

You can use str\_sub() to extract the last four digits from the product\_url column and create a new column called extracted\_product\_id.

*   \# Extracting the last 4 digits from the product\_url column.
*   books <- books %>%
*    mutate(extracted\_product\_id = str\_sub(product\_url, start = -4))

In the above code, we have used below two parameters:

*   product\_url: The column containing the URLs.
*   start = -4: Specifies that the extraction should start from the 4th character from the end of the string, capturing the last four digits. 
    1.  \# Print the extracted\_product\_id
    2.  books %>% select(extracted\_product\_id)
    3.  
    4.  \## extracted\_product\_id
    5.  \## 0255
    6.  \## 0078
    7.  \## 7077
    8.  \## 0537

You observe that the str\_sub() function is a very useful function for text analysis tasks where you need to extract a specific portion of a string.

[Regular expressions](#contents.xhtml#sc2_92a)

Regular expressions are patterns that can be used to describe certain strings. They allow you to define patterns that can be used to match and replace specific strings within a larger piece of text. They are a powerful tool for text analysis and manipulation. Regex can be used for a variety of tasks, such as:

*   Identifying and extracting specific patterns from text: For example, you could use regex to identify all phone numbers in a text document.
*   Replacing text: You could use regex to replace all occurrences of a specific word with another word.
*   Validating text: You could use regex to validate that a password meets specific requirements, such as containing at least one uppercase letter and one special character. 
    
    | Note: regexes are case-sensitive. |
    | --- |
    

[Regex ingredients](#contents.xhtml#sc3_93a)

Regular expressions are constructed using building blocks. Each building block is a simple pattern or rule, and it can be combined in an infinite number of ways to create complex patterns. Learning how to combine these building blocks is essential to achieve specific text analysis goals.

Regular expressions consist of two categories of characters: special characters (metacharacters) and literal characters. Special characters include symbols such as, . \\ | ( ) { } \[ \] ^ $ - \* + ?, and they have a specific meaning in regex. Literal characters are regular text characters that match themselves.

The following table provides an overview of character types commonly used in regular expressions and their corresponding interpretations:

| Character types || Interpretation |
| --- | --- |
| abc || Exact match for the characters abc |
| 123 || Matches the exact sequence of digits 123 |
| \\w || Matches any single alphanumeric character (a-z, A-Z, 0-9) |
| \\W || Matches any single non-alphanumeric character (excluding a-z, A-Z, 0-9) |
| \\d || Matches any single digit (0-9) |
| \\D || Matches any single non-digit character (excluding 0-9) |
| \\s || Matches any single whitespace character (spaces, tabs, newlines, etc.) |
| \\S || Matches any single non-whitespace character (excluding spaces, tabs, newlines, etc.) |
| . || Matches any single character (except for newline characters) |
| $ || Matches the end of an input string |
| ^ || Matches the beginning of an input string |

Table 6.10: Character types commonly used in regular expressions

[Grouping in regular expressions](#contents.xhtml#sc3_94a)

Here is a table describing various grouping patterns in regular expressions:

| Grouping || Interpretation |
| --- | --- |
| \[abc\] || Matches any single character from the set abc |
| \[^abc\] || Matches any single character that is not in the set abc |
| \[0-9\] || Matches any single digit from 0 to 9 |
| \[a-z\] || Matches any single lowercase letter from a to z |
| \[A-Z\] || Matches any single uppercase letter from A to Z |
| \[a-zA-Z\] || Matches any single alphanumeric character, either lowercase or uppercase |
| ( ) || Capture group: Captures the matched text and makes it available for later use |
| (a(bc)) || Capture subgroup: Captures a subpattern within the capture group |
| (abc|def) || Matches abc or def |

Table 6:11: Grouping patterns used in regular expressions

Group modifiers are special syntax extensions that alter the behavior of quantifiers in regular expressions. They allow you to specify how many times a quantifier should match its preceding pattern. Understanding these modifiers is essential for fine-tuning regex patterns to match text data precisely.

Using the below group modifiers, you can specify how many times a particular pattern should repeat, whether zero or more, one or more, a specific number, or within a range.

| Group modifier || Interpretation |
| --- | --- |
| \* || Matches zero or more repetitions of the previous pattern (greedy quantifier) |
| + || Matches one or more repetitions of the previous pattern (greedy quantifier) |
| ? || Makes the previous pattern optional (matches zero or one time). |
| {n} || Matches exactly n repetitions of the previous pattern |
| {n,m} || Matches between n and m repetitions of the previous pattern |
| \*? || Matches zero or more repetitions of the previous pattern (non-greedy quantifier) |
| +? || Matches one or more repetitions of the previous pattern (non-greedy quantifier) |

Table 6.12: A list of group modifiers

[Greedy and non-greedy matching](#contents.xhtml#sc3_95a)

In regular expressions, quantifiers are used to specify how many times a pattern should match. When applied to a group of characters, quantifiers determine the extent of the match within the input string. greedy and non-greedy modifiers are special extensions that control the behavior of quantifiers. The following table summarizes the key differences between greedy and non-greedy quantifiers:

| Quantifier || Behavior |
| --- | --- |
| Greedy || Matches as much as possible |
| Non-greedy || Matches as little as possible |

Table 6.13: Greedy and non-greedy quantifiers in Regex

The str\_extract() function uses greedy matching by default. This means that if you have a regex pattern that contains a quantifier (such as \*, +, or {}), the str\_extract() will try to match the longest possible string that satisfies the pattern.

Consider a scenario where you have a chunk of HTML code and want to extract the content within specific HTML tags. Let us create a sample HTML text

1.  \# Sample HTML text 
2.  text <- "<div class='main'><h1>Machine Learning & AI</h1><div> <a href='DataSciencewithR.pdf'>Data Science with R</a> </div></div>"
3.  
4.  \# print the ‘text’
5.  text
6.  
7.  \## "<div class='main'><h1>Machine Learning & AI</h1><div> <a href='DataSciencewithR.pdf'>Data Science with R</a> </div></div>"

Greedy matching is the default behavior of regular expressions, where the pattern matches as much of the input string as possible.

1.  \# Greedy matching
2.  str\_extract(text, "<div\>.\*</div\>")
3.  
4.  \## "<div> <a href='DataSciencewithR.pdf'>Data Science with R</a> </div></div>"

The regular expression, <div>.\*</div\> matches any string that starts with <div> and ends with </div>, and the .\* quantifier in the middle of the pattern matches any sequence of zero or more characters.

Now, let us modify the pattern to make it non-greedy by adding a ? after the .\* quantifier:

1.  \# Non Greedy matching
2.  str\_extract(text, "<div>.\*?</div>")

This time, the function returns a different result:

1.  \## "<div> <a href='DataSciencewithR.pdf'>Data Science with R</a> </div>"

The regular expression <div>.\*?</div> is the same as the previous regular expression but with a ? after the .\* quantifier. This ? tells the regex engine to try to match the shortest possible string that satisfies the pattern.

The difference is that the non-greedy pattern <div>.\*?</div> stops matching as soon as it encounters the first closing <div> tag, whereas the greedy pattern <div>.\*</div> continues matching until the end of the input string.

[Detecting and extracting patterns](#contents.xhtml#sc3_96a)

This section will teach practical applications of regular expressions to analyze and extract information from a dataframe. The below dataframe contains two bank messages, one for debit and one for credit transactions. We can use regular expressions to extract information from these messages, such as the transaction type, amount, and date.

1.  \# Create a dataframe, “bank\_messages”
2.  bank\_messages <- data.frame(
3.   message = c(
4.  "Your Bank Acc XX998006 is debited for INR 555.68 on 10-Nov-23 towards paytmqroihh5855ap@paytm. UPI Ref No 368033761556. If you have any concerns, please contact us at 1800-267-3456.",
5.  "Dear Customer, Your A/C XXXXX123456 has a credit by Cheque of Rs 80,000.00 on 30/10/23."
6.   )
7.  )

Let us first extract amounts mentioned in the message column of the bank\_messages data frame. Here, we assume that the desired amounts are preceded by either INR or Rs.

1.  \# Extracts the amount preceded by “INR” or "Rs”
2.  bank\_messages <- bank\_messages %>%
3.   mutate(amount = str\_extract(message, "(?<=\\\\bINR\\\\s|\\\\bRs\\\\s)\[0-9,\]+\\\\.?\[0-9\]\*"))
4.  
5.  \# Check the result
6.  View(bank\_messages) 
    
    | Message || Amount |
    | --- | --- |
    | Your Bank Acc XX998006 is debited for INR 555.68 on 10-Nov-23 towards paytmqroihh5855ap@paytm. UPI Ref No 368033761556. If you have any concerns, please contact us at 1800-267-3456. || 555.68 |
    | Dear Customer, Your A/C XXXXX123456 has a credit by Cheque of Rs 80,000.00 on 30/10/23. || 80,000.00 |
    

Table 6.14: Bank messages Data Frame with extracted transaction amounts

Let us break down the regular expression used in the str\_extract function:

"(?<=\\\\bINR\\\\s|\\\\bRs\\\\s)\[0-9,\]+\\\\.?\[0-9\]\*"

*   (?<=\\\\bINR\\\\s|\\\\bRs\\\\s): This is a positive look-behind assertion. It checks if the text is preceded by either the word INR or Rs (case-sensitive) with a word boundary (\\\\b) and a space (\\\\s). The \\\\b ensures that INR or Rs is a whole word and not part of another word.
*   \[0-9,\]+: This part matches one or more digits (0-9) or commas. This allows the capture of amounts that use commas as thousand separators, for example, 80,000.
*   \\\\.?: This matches an optional decimal point (.). The backslash (\\\\) is used to escape the dot because, in regular expressions, the dot is a special character that matches any character. The question mark (?) makes the decimal point optional, allowing for both integer and decimal amounts.
*   \[0-9\]\*: Matches zero or more digits after the decimal point, capturing the decimal part of the amount.

Next, we will create two columns, credit and debit, indicating whether the message column contains the words credit and debit, including variations like credited and debited. The regular expressions use the str\_detect function to check for the presence of the specified patterns in the “message” column.

1.  \# Add columns to indicate whether the message contains “credit” or “debit”
2.  bank\_messages <- bank\_messages %>%
3.   mutate(
4.   has\_credit = str\_detect(message, "\\\\bcredit(ed)?\\\\b"),
5.   has\_debit = str\_detect(message, "\\\\bdebit(ed)?\\\\b")
6.   )
7.  \# View the data frame
8.  View(bank\_messages) 
    
    | message || amount || has\_credit || has\_debit |
    | --- | --- | --- | --- |
    | Your Bank Acc XX998006 is debited for INR 555.68 on 10-Nov-23 towards paytmqroihh5855ap@paytm. UPI Ref No 368033761556. If you have any concerns, please contact us at 1800-267-3456. || 555.68 || FALSE || TRUE |
    | Dear Customer, Your A/C XXXXX123456 has a credit by Cheque of Rs 80,000.00 on 30/10/23. || 80,000.00 || TRUE || FALSE |
    

Table 6.15: Bank messages data with credit and debit indicators

The above command determines whether each message contains the words credit or debit and their variations. The mutate function from the dplyr package is used to add two new columns, has\_credit, and has\_debit, to the bank messages data frame.

*   \\\\b: This is a word boundary assertion. It ensures that the word credit or debit is matched as a whole word and not as part of another word.
*   credit(ed)?: This part matches the word credit and makes the ed part optional with (ed)?. This allows for matching both credit and credited.
*   debit(ed)?: Similar to the credit part, this matches the word debit and makes the ed part optional, allowing for variations like debit and debited.
*   The has\_credit column will be TRUE if the message contains the word credit or credited and FALSE otherwise. Similarly, the has\_debit column will be TRUE if the message contains the word debit or debited and FALSE otherwise.

Next, we will extract dates from the message column in the bank\_messages data frame. The dates are expected to be in either dd/mm/yy or dd-mmm-yy format. The resulting date column will contain a list of dates found in each message.

1.  \# Extract date from the message column
2.  bank\_messages <- bank\_messages %>%
3.   mutate(
4.   date = str\_extract\_all(message, "\\\\b\\\\d{2}/\\\\d{2}/\\\\d{2}|\\\\d{2}-\[a-zA-Z\]{3}-\\\\d{2}\\\\b")
5.   )
6.  \# Display the modified data frame with the new "date" column.
7.  View(bank\_messages)

| message || amount || has\_credit || has\_debit || date |
| --- | --- | --- | --- | --- |
| Your Bank Acc XX998006 is debited for INR 555.68 on 10-Nov-23 towards paytmqroihh5855ap@paytm. UPI Ref No 368033761556. If you have any concerns, please contact us at 1800-267-3456. || 555.68 || FALSE || TRUE || 10-Nov-23 |
| Dear Customer, Your A/C XXXXX123456 has a credit by Cheque of Rs 80,000.00 on 30/10/23. || 80,000.00 || TRUE || FALSE || 30/10/23 |

Table 6.16: Bank messages data with extracted transaction dates

The above command uses regular expressions to extract dates in two formats: dd/mm/yy and dd-mmm-yy. The str\_extract\_all function extracts all occurrences of the specified date patterns in each message.

*   \\\\b: Word boundary assertion confirms that the date pattern is matched as a whole word and not as part of another word.
*   \\\\d{2}/\\\\d{2}/\\\\d{2}: This part matches the dd/mm/yy date format. It looks for two digits (day), followed by a forward slash, two digits (month), another forward slash, and two digits (year).
*   |: The pipe symbol functions as a logical OR, allowing the regular expression to match either the dd/mm/yy or the dd-mmm-yy format.
*   \\\\d{2}-\[a-zA-Z\]{3}-\\\\d{2}: This part matches the dd-mmm-yy date format. It looks for two digits (day), followed by a hyphen, three letters representing the month (case-insensitive due to \[a-zA-Z\]), another hyphen, and two digits (year).
*   \\\\b: Another word boundary assertion makes sure the completeness of the matched date pattern.

The following figure illustrates the breakdown of the regular expression used to extract date.

![](images/Figure6.1.png)

Figure 6.1: Regular expression to extract date from the message column

Let us check another scenario of extracting phone numbers following a specific format from the message column.

1.  \# Extract phone number
2.  bank\_messages <- bank\_messages %>%
3.   mutate(
4.   phone\_number = str\_extract(message, "\\\\b\\\\d{4}-\\\\d{3}-\\\\d{4}\\\\b")
5.   )

The above command extracts the phone numbers that are expected to follow the format xxxx-xxx-xxxx.

1.  \# View the dataframe
2.  View(bank\_messages)

| message || amount || has\_credit || has\_debit || date || phone\_number |
| --- | --- | --- | --- | --- | --- |
| Your Bank Acc XX998006 is debited for INR 555.68 on 10-Nov-23 towards paytmqroihh5855ap@paytm. UPI Ref No 368033761556. If you have any concerns, please contact us at 1800-267-3456. || 555.68 || FALSE || TRUE || 10-Nov-23 || 1800-267-3456 |
| Dear Customer, Your A/C XXXXX123456 has a credit by Cheque of Rs 80,000.00 on 30/10/23. || 80,000.00 || TRUE || FALSE || 30/10/23 || NA |

Table 6.17: Bank messages data with extracted phone numbers

The regular expression \\\\d{4}-\\\\d{3}-\\\\d{4} matches the phone number pattern xxxx-xxx-xxxx. It looks for four digits, followed by a hyphen, three digits, another hyphen, and four digits.

As you can see, we extracted the transaction type, amount, date, and phone number from the bank messages dataframe using regex. This information can be used for various purposes, such as fraud detection and customer segmentation.

[Conclusion](#contents.xhtml#sc2_97a)

This chapter explored fundamental techniques for manipulating and cleaning strings using the stringr package. stringr provides a variety of functions for manipulating strings. This chapter covered essential string operations such as changing cases, calculating string length, replacing and removing substrings, handling whitespaces, padding, and concatenating strings. regex offer a versatile and efficient way to search, edit, manipulate, and extract data. They can be used to perform a wide variety of tasks such as:

*   Data cleaning: Removing unwanted characters, formatting data consistently, and correcting errors.
*   Feature engineering: Creating new features from existing data, such as extracting date and time information, identifying product categories, and detecting spam emails.
*   Text analysis: Regex can be used to perform various text analysis tasks like entity extraction.

In the next chapter, you will learn how to present your findings visually using data visualizations.

Join our book’s Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/fm1.png)

# [CHAPTER 7Visualizing Data](#contents.xhtml#ch07a)

[Introduction](#contents.xhtml#sc2_98a)

Data visualization is a fusion of art and science. Achieving a delicate balance between these two facets is essential for accurately conveying data. Accurately representing the data while creating visually appealing graphics is paramount for effective communication. Data visualizations can reveal patterns, identify outliers, guide data transformations, and inspire new features for ML models. A successful data visualization should accurately convey the data without misleading or distorting it while also being aesthetically pleasing to enhance its impact. Visual elements that distract from the data, such as jarring colors or imbalanced elements, hinder interpretation. ggplot2 is a widely used R package for data visualization that employs a grammar of graphics based plotting system. This simplifies the process of creating complex and insightful visualizations. It provides a consistent set of rules for specifying the different elements of a plot, such as data, the aesthetic mappings, and the geometry.

[Structure](#contents.xhtml#sc2_99a)

In this chapter, we will elaborate on the fundamental concepts related to data visualization.

*   ggplot2 template and aesthetics
*   Visualizing distributions  
    *   Bar plots
    *   Histograms
    *   Density plots
*   Visualizing proportions 
    *   Pie charts
    *   Stacked bar plots
*   Visualizing associations 
    *   Boxplots
    *   Scatter plots
*   Visualizing time series using a line chart

[Objectives](#contents.xhtml#sc2_100a)

This chapter will teach you how to represent data using data visualization correctly. You will acquire knowledge on utilizing the ggplot2 package to produce diverse visualizations, including bar plots, histograms, density plots, boxplots, pie charts, line charts, and scatter plots. You will also learn how to visualize time series data and data distributions. By the end of this chapter, you will be able to create informative and engaging data visualizations that effectively communicate your findings to others.

[ggplot2 template and aesthetics](#contents.xhtml#sc2_101a)

In contrast to many other graphics packages, ggplot2 operates on a unique grammar rooted in Wilkinson's Grammar of Graphics (2005). This grammar allows you to construct graphs by assembling distinct components, making ggplot2 a powerful tool in data visualization. The methodology of ggplot2 encourages an iterative process, initiating with a foundational layer representing raw data and gradually incorporating additional layers for annotations and statistical summaries. This iterative approach aligns the process of creating graphics with the structured thinking involved in our typical analysis.

Expanding upon Wilkinson's grammar, ggplot2, as introduced by Wickham (2009), focuses on the significance of layers, adapting the grammar for integration with R. The grammar of graphics is a mapping of data onto aesthetic attributes (color, shape, and size) of geometric objects (such as points, lines, or bars). Additionally, the plot may incorporate statistical transformations of the data and details about the plot's coordinate system. The thoughtful combination of these independent components shapes a comprehensive and informative graphic.

Every ggplot2 plot is constructed from three essential components:

*   Data: The foundation of a plot, representing the information you want to visualize.
*   Geometry (a geom function): The visual representation of the data, defined by a geom function. Geom functions determine the graphical elements that make up the plot, such as points, lines, bars, or polygons.
*   Aesthetic mapping: The connection between the data and its visual representation, specified through aesthetic mappings. Aesthetic mappings assign data variables to visual properties, such as color, shape, and size, controlling how the data is displayed on the plot.

To create a ggplot2 plot, you combine these three components using the following template:

*   ggplot(data = <YOUR\_DATA\>) +
*    geom\_<YOUR\_GEOM\_FUNCTION\>(aes(<YOUR\_MAPPINGS\>))

Replace <YOUR\_DATA>, <YOUR\_GEOM\_FUNCTION>, and <YOUR\_MAPPINGS> with the specific dataset, geom function, and mappings you intend to use.

Beyond the foundational components of data, geometry, and aesthetic mapping, ggplot2 allows you to enhance your visual storytelling by incorporating additional layers that refine and enrich your plots.

*   Statistical transformations (stats): stat functions summarize and manipulate data directly within the plot. 
*   Scales: They map data values to aesthetic properties like color, shape, size, and opacity. Scales also contribute to constructing the legend and axes.
*   Coordinate system (coord): They organize geometric objects by mapping data coordinates.
*   Facet: Faceting breaks down your data into distinct subsets and displays them as multiple smaller plots within the same figure. This powerful technique allows you to explore the relationships between variables and identify patterns that might not be evident when examining the data as a whole.
*   A theme controls the finer points of the display, like the font size and background color. 

The grammar of graphics, upon which ggplot2 is built, recognizes that a plot is a distinct amalgamation of a dataset, a geom, a collection of mappings, a stat, a position adjustment, a coordinate system, and a faceting scheme. The following figure shows all the components of the ggplot2 template.

![](images/Figure7.1.png)

Figure 7.1: ggplot2 template

Now, let us explore how to utilize this template to create various types of graphs.

To get started with visualizations, the first step is to install the essential packages. We have two options: either we can load the tidyverse, which includes the ggplot2 package, or we can opt for a more focused approach by individually installing ggplot2.

*   \# Load tidyverse:
*   library(tidyverse)
*   
*   \# Alternatively, install ggplot2
*   install.packages("ggplot2")
*   install.packages("forcats")
*   
*   \# Load ggplot2 and forcats
*   library(ggplot2)
*   library(forcats)

[Visualizing distributions](#contents.xhtml#sc2_102a)

Effectively conveying the distribution of data is a fundamental aspect of data analysis, and the approach to visualization varies based on the nature of the variable—whether it is categorical or numerical. This section explores three essential visualization techniques: bar plots, histograms, and density plots.

[Bar plots](#contents.xhtml#sc3_103a)

In numerous situations, we focus on understanding the scale of a given set of numerical values. Consider a retail enterprise that wants to depict the sales performance across various product categories (such as electronics, books, and home goods) over a specific timeframe. Alternatively, a website owner may seek to dissect the origins of traffic to their site, distinguishing between direct visits, search engine referrals, and other sources. Likewise, an educator might wish to portray the average scores achieved by students in diverse subjects. In each instance, we confront a scenario where distinct categories (e.g., product categories, traffic sources, or academic subjects) are associated with corresponding quantitative values. The go-to visualization method in such cases is the bar plot.

Some people might avoid using bar charts because they think they are too commonplace, but that is a mistaken assumption. In reality, the widespread use of bar charts works in your favor, making it easier for your audience to grasp the information you are presenting quickly. Instead of struggling to understand an unfamiliar graph, your audience can focus on extracting valuable insights from the visual display. Our eyes can easily compare the lengths of the bars, allowing us to rapidly identify the ranking of categories, distinguish the largest and smallest values, and perceive gradual changes between them.

Let us dive into a dataset sourced from the Food and Agriculture Organization Corporate Statistical Database (FAOSTAT), capturing total spice consumption across 185 countries for 2021. The dataset comprises two columns: one indicates the country name, and the other denotes spice consumption measured in kilotons (kt). We will start by exploring the top 10 countries with the highest spice consumption.

*   \# Read the dataset
*   spice\_consumption <- read.csv("Spice\_Consumption.csv")
*   
*   \# Arrange the data in descending order of Value and subset the top 10 countries 
*   spice\_top10 <- spice\_consumption %>% 
*    arrange(desc(Value)) %>%
*    slice\_head(n = 10)

The ggplot2 template for the bar chart follows a straightforward structure. We will create a bar chart to visualize the top 10 countries with the highest spice consumption.

*   \# Distribution of Spice Consumption
*   ggplot(spice\_top10, aes(x = Country, y = Value)) +
*    geom\_bar(stat = "identity")

Output:

![](images/Figure7.2.png)

Figure 7.2: Bar Chart of Spice Consumption

The ggplot() function creates a blank canvas for the graph, while the aes() function defines the aesthetic mappings of the data. In this case, we map the Country column to the x-axis and the Value column to the y-axis. Finally, the geom\_bar() function adds a bar chart to the graph, using the stat=identity argument to specify that we want to render the bars with their actual values.

A common issue with vertical bar charts is that the labels identifying each bar can occupy a significant amount of horizontal space, leading to overlapping and illegible text in the chart. The above chart shows that some country names overlap and cannot be easily read. One solution to address this issue is to rotate the x-axis labels. However, this approach often results in awkward-looking plots that require excessive space beneath the chart, making it also difficult to read.

*   \# Distribution of Spice Consumption
*   ggplot(spice\_top10, aes(x = Country, y = Value)) +
*    geom\_bar(stat = "identity") +
*    theme(axis.text.x = element\_text(angle = 90, vjust = 0.5, hjust = 1))

![](images/Figure7.3.png)

Figure 7.3: Bar Chart of Spice Consumption

The last command within the ggplot2 code snippet modifies the appearance of the x-axis labels by changing the font properties. The theme() function customizes various aspects of the plot's visual style. In this case, the axis.text.x argument specifies that we want to modify the x-axis labels. The element\_text() creates a new text element for the x-axis labels with the below parameters:

*   angle = 90: Rotates the text by 90 degrees clockwise to be oriented vertically.
*   vjust = 0.5: Adjusts the vertical justification of the text. In this context, it centers the labels vertically.
*   hjust = 1: Adjusts the horizontal justification of the text. A value of 1 implies the right justification.

A more effective approach to address the challenge of long labels in bar charts is often to swap the x and y axes, rendering the bars in a horizontal orientation. This reorientation alleviates the issue of label overlap and provides a clearer and more space-efficient representation of the data.

To implement this solution in ggplot2, we can use the coord\_flip() function, which swaps the x and y axes, converting the vertical bar chart into a horizontal one. This resolves the issue of overcrowded x-axis labels and provides a more visually appealing representation of the data.

*   \# Distribution of Spice Consumption
*   ggplot(spice\_top10, aes(x = Country, y = Value)) +
*    geom\_bar(stat = "identity") +
*    coord\_flip()

![](images/Figure7.4.png)

Figure 7.4: Bar Chart of Spice Consumption

Regardless of whether we orient bars vertically or horizontally, the order in which they are arranged is crucial. Random or arbitrary arrangements can lead to confusion and make the graph less intuitive. In R, the default arrangement is the alphabetical order of the labels, which may not always be the most meaningful way to organize the data. In the case of the spice consumption chart, it is more meaningful to rearrange the bars in the order of spice consumption. By rearranging the bars in this way, we can create a more effective visualization that helps the reader understand the data at a glance.

*   \# Distribution of Spice Consumption
*   ggplot(spice\_top10, aes(x = fct\_reorder(Country, Value), y = Value)) +
*    geom\_bar(stat = "identity", fill = "steelblue3") +
*    labs(title = "Spice Consumption",
*    x = "Country",
*    y = "Spice Consumption (kt)") + 
*    coord\_flip() +
*    theme\_bw()

![](images/Figure7.5.png)

Figure 7.5: Bar Chart of Spice Consumption

Let us explore a few new functions and arguments used in the above code to present the data more meaningfully and interpretably.

fct\_reorder(Country, Value): This is part of the forcats package and is used to reorder the levels of the Country factor based on the values in the Value column. This means that the bars in the bar plot will be arranged in order of decreasing spice consumption.

fill = steelblue3: This argument specifies the color that should be used to fill the bars in the graph. Here, the fill argument is set to steelblue3.

The labs() function adds labels to the axes and title of the plot. It sets the title of the plot to Spice Consumption, the x-axis label to Country, and the y-axis label to Spice Consumption (kt).

The theme\_bw() function applies a black-and-white theme to the plot. The theme\_ functions in ggplot2 are a set of functions that allow users to customize the visual appearance of their plots. The ggthemes package extends the theming options in ggplot2 by providing additional predefined themes with specific styles. You can easily apply these themes to your ggplot2 plots to achieve a visually appealing look.

It is vital to note that we should only rearrange bars when the categories they represent do not have a natural order or hierarchy. If the categories are already ordered meaningfully (for example, if our categorical variable is an ordered factor), then preserving that order in the visualization is recommended.

[Histograms](#contents.xhtml#sc3_104a)

Histograms are graphical representations of data distributions for continuous data. A histogram is created by dividing the x-axis into equally spaced intervals called bins. The height of each bar in the histogram represents the number of data points that fall within the corresponding bin. This creates a graph that shows the frequency distribution of the data, revealing how the data is distributed across the range of values.

They can tell us whether the data is symmetric, skewed to the left or right, or has multiple peaks. This information is crucial for identifying patterns and outliers in the data. Outliers are observations that do not follow the general pattern of the rest of the data and can indicate errors, anomalies, or interesting phenomena. By examining the histogram, we can easily spot outliers and decide whether they are worth investigating further.

In ggplot2, you can set the width of the intervals using the binwidth parameter. It is essential to experiment with different binwidths to find the optimal interval size that best illustrates the underlying structure of the data. You also have the option to specify the number of bins using the bins argument, with a default setting of 30.

Now, we will import a dataset of an indicator of undernourishment from FAOSTAT and create a histogram of the prevalence of undernourishment across 173 countries. The Food and Agriculture Organization of the United Nations (FAO) defines the prevalence of undernourishment (PoU) as an estimate representing the percentage of the population whose regular food intake falls below the necessary dietary energy levels essential for sustaining a normal, active, and healthy life. The below code generates a histogram to visualize the distribution of undernourishment prevalence for 2021.

*   \# Read the dataset
*   undernourishment <- read.csv("undernourishment\_data.csv")
*   
*   \# Subsetting data for 2021
*   undernourishment\_2021 <- undernourishment %>% filter(Year == 2021)
*   
*   \# Distribution of the Undernourishment Prevalence
*   ggplot(undernourishment\_2021, aes(x = Value)) +
*    geom\_histogram(binwidth =2, fill = "steelblue3", color = "black") +
*    labs(title = "Prevalence of Undernourishment",
*    x = "Prevalence (%)",
*    y = "Frequency") +
*    theme\_bw() 

![](images/Figure7.6.png)

Figure 7.6: Distribution of Prevalence of Undernourishment

| Note: In the FAO dataset, countries and regions with undernourishment rates below 2.5% are categorized as having a rate of 2.5%. |
| --- |

Here, geom\_histogram(binwidth = 2, fill = "steelblue3", color = "black") adds a histogram layer to the plot using the geom\_histogram(). It divides the x-axis into bins with a width of 2 and fills each bin with steelblue3; each bin's border is colored black.

To incorporate count labels above each bar in the histogram, you can use the statistical transformation function stat\_bin(). It allows us to display the frequency counts within each bin directly on top of the corresponding bars. This simple addition can provide a more precise understanding of the underlying distribution. It can also help you accurately compare bins and across different datasets.

*   \# Distribution of the Undernourishment Prevalence
*   ggplot(undernourishment\_2021, aes(x = Value)) +
*    geom\_histogram(binwidth =2, fill = "steelblue3", color = "black") +
*    labs(title = "Prevalence of Undernourishment",
*    x = "Prevalence (%)",
*    y = "Frequency") +
*    stat\_bin(aes(label = after\_stat(count)), 
*    binwidth = 2,
*    geom = "text", vjust = -0.5, color = "black", size = 3) +
*    theme\_bw() 

![](images/Figure7.7.png)

Figure 7.7: Distribution of Prevalence of Undernourishment

stat\_bin(aes(label = after\_stat(count)), binwidth = 2, geom = "text", vjust = -0.5, color = "black", size = 3): Adds a text label to each bin using the stat\_bin(). The label is set to the count of observations in each bin (represented by after\_stat(count)). The text labels are positioned at the bottom of each bin (vjust = -0.5) and have a font size of 3. The color of the text labels is set to black.

Our analysis shows that the distribution of undernourishment prevalence is skewed, with a significant tail extending towards higher rates. This skewed distribution indicates that while most countries have relatively low undernourishment prevalence, a smaller group faces considerably higher rates. Notably, 17 countries have a prevalence of undernourishment exceeding 30% in 2021, highlighting the existence of significant disparities in food security across the globe.

[Density plots](#contents.xhtml#sc3_105a)

When exploring numerical data, histograms are commonly used to visualize the distribution. A density plot is a smoothed-out version of a histogram. This makes it particularly useful for quickly grasping the overall shape of the distribution, including its skewness and multimodality. [Figure 7.8](#ch07.xhtml#fig7-8) presents a density plot of undernourishment prevalence.

*   \# Density Plot of Undernourishment Prevalence
*   ggplot(undernourishment\_2021, aes(x = Value)) +
*    geom\_density(fill = "lightblue", color = "steelblue4") +
*    labs(title = "Prevalence of Undernourishment",
*    x = "Prevalence (%)",
*    y = "Frequency") +
*    theme\_bw() 

![](images/Figure7.8.png)

Figure 7.8: Density Plot of Prevalence of Undernourishment

[Visualizing proportions](#contents.xhtml#sc2_106a)

Effectively conveying the breakdown of a group, entity, or quantity into its constituent parts is a common task in data visualization. Whether it's depicting the gender distribution in a population or the vote shares of different political parties in an election, visualizing proportions plays a crucial role in data exploration and communication. It helps viewers understand how different parts contribute to the whole.

[Pie charts](#contents.xhtml#sc3_107a)

Pie charts have long been the go-to visualization for proportions or percentages, widely used in business presentations and reports. Their circular layout and proportional slices have made them a popular choice for illustrating how different components contribute to a larger whole. Pie charts provide a general idea of the distribution of proportions, especially when dealing with a small number of categories. However, data scientists often criticize pie charts for several shortcomings:

*   Difficulty comparing proportions: When dealing with numerous categories, comparing proportions using pie charts becomes increasingly challenging.
*   Human perception limitations: The human eye is not well-suited for accurately judging the relative sizes of pie chart slices, especially when dealing with small slices.
*   Ineffective for highlighting changes: Pie charts are not ideal for visualizing changes in proportions over time or across different conditions.

Now, let us create a pie chart to depict the geographical distribution of global hunger using ggplot2 visually. While ggplot2 does not have a specific geom for pie charts, we can create one with a workaround. We can use the geom\_bar() to build a stacked bar chart with a single bar and then use the coord\_polar() to transform the chart into a circular layout, giving us a pie chart. Think of it like taking a regular bar chart and bending it into a circle, giving you a pie chart with slices representing different categories.

The default coordinate system used in plotting is the Cartesian system, where each point is defined by its independent x and y coordinates. However, two additional coordinate systems are available: coord\_quickmap() designed explicitly for plotting spatial data, and coord\_polar(), which utilizes polar coordinates.

Let us create a simple pie chart like the one below:

*   hunger\_2021 <- read.csv("hunger\_2021.csv")
*   
*   \# Pie chart
*   ggplot(hunger\_2021, aes(x = "", y = Value, fill = Region)) +
*    geom\_bar(stat = "identity", width = 1, color = "white") +
*    coord\_polar(theta = "y")

Let us create a simple pie chart like the one below:

![](images/Figure7.9.png)

Figure 7.9: Pie chart

In this case, we leave the x-axis blank by specifying an empty string within quotes. The pie chart slices are drawn based on the Value variable, and each slice is colored according to the corresponding Region. By default, it draws the slices counterclockwise, following the alphabetical order of the categories. The coord\_polar(theta = "y") sets the coordinate system for the plot to polar coordinates, which is suitable for pie charts. theta = "y" indicates that the angle of each slice is determined by the y variable (Value).

Now, if you look closely at the above chart, you might notice some extra stuff in the background of the chart. Let us get rid of that and make it look a bit cleaner. We will remove the numbers and the grid lines by the function theme\_void(). Think of it like wiping away everything but the slices themselves. To make the slices stand out, we will add borders to each one by adding the color into geom\_bar() and reordering the graph based on the size of the undernourished population. The following pie chart displays the distribution of undernourished people by region.

*   \# Pie Chart displaying the undernourished population across different regions
*   ggplot(hunger\_2021, aes(x = "", y = Value, fill = fct\_reorder(Region, Value))) +
*    geom\_bar(stat = "identity", width = 1, color = "white") +
*    coord\_polar(theta = "y") +
*    theme\_void() + 
*    theme(legend.position = "bottom") +
*    labs(title = "Undernourished People by Region", fill = "Region") +
*    scale\_fill\_brewer(palette = "Set3") +
*    geom\_text(aes(x = 1.7, label = ifelse(Value >= 30, paste(Region, "\\n", round(Value, 0), "M"), "")), 
*    position = position\_stack(vjust = 0.5), 
*    size = 3, show.legend = FALSE)

![](images/Figure7.10.png)

Figure 7.10: Distribution of Undernourished People by Region

Let us understand the additional components used in the above command:

• Layout and theme

○ theme\_void(): Removes unnecessary background elements for a cleaner presentation.

○ theme(legend.position = "bottom"): Positions the legend at the bottom for improved readability.

● Labeling and colors

○ labs(title = "Undernourished People by Region", fill = "Region"): Adds a title to the plot and labels the fill (color) legend as Region.

○ scale\_fill\_brewer(palette = "Set3"): Chooses a color palette from the Set3 collection for slice colors.

● Adding text labels

○ geom\_text: Adds text labels to the plot.

○ aes(x = 1.7, label = ifelse(Value >= 30, paste(Region, "\\n", round(Value, 0), "M"), "")): Sets the x position and label text. Labels are conditional; if Value is greater than or equal to 30 million, the label includes the Region and Value (rounded to the nearest whole number with M appended); otherwise, it is an empty string.

o position\_stack(vjust = 0.5): Positions the labels vertically centered within each slice.

o size = 3: Sets the text size.

o show.legend = FALSE: Hides the text labels from the legend.

The chart above shows that Asia is the predominant region for individuals experiencing hunger, with 414 million people constituting 56% of the total undernourished population in 2021. Africa is home to approximately 37% (271 million) of undernourished individuals, while Latin America and the Caribbean account for about 6% (46 million).

[Stacked bar plots](#contents.xhtml#sc3_108a)

Pie charts have long been a staple of data visualization, but their limitations are becoming increasingly evident. One of the primary issues with pie charts is their tendency to distort the actual values being represented, mainly when dealing with small slices or multiple categories. This distortion occurs because our eyes are not very good at accurately judging angles, making it difficult to compare the sizes of different segments within a pie chart. As a result, the audience may misinterpret the data, leading to incorrect conclusions or decisions. Stacked bar charts avoid this problem by representing each category as a proportional rectangle, making it much easier for viewers to accurately compare the sizes of different segments.

Another advantage of stacked bar charts is their versatility in handling various data types. Unlike pie charts, which are best suited for showing simple proportions, stacked bars can accommodate both discrete and continuous variables. For example, you could use a stacked bar chart to show how the total sales revenue of a company is divided among different product categories and regions all within a single graph.

We will now generate a new column in the hunger\_2021 dataset that represents the percentage of each region's population experiencing hunger (also known as undernourishment). Then, we will use a stacked bar chart to visualize this data.

*   \# Create a new column, "Percentage"
*   hunger\_2021 <- hunger\_2021 %>%
*    mutate(Percentage = round((Value / sum(Value)) \* 100,1))
*   
*   \# Stacked Bar Chart
*   ggplot(hunger\_2021, aes(x = "", y = Percentage, 
*    fill = fct\_reorder(Region, Percentage))) +
*    geom\_bar(stat = "identity")+
*    geom\_text(aes(label = ifelse(Percentage >= 1, paste0(round(Percentage, 0), "%"), "")), 
*    position = position\_stack(vjust = 0.5), 
*    size = 3, show.legend = FALSE) +
*    labs(title = "Undernourished People by Region", fill = "Region",
*    x = "", y = "Percentage") +
*    scale\_fill\_brewer(palette = "Set2") +
*    theme\_bw()

The figure below is a reference of a stacked bar chart:

![](images/Figure7.11.png)

Figure 7.11: Stacked Bar Chart

The above code generates a stacked bar chart with the variable Percentage, plotted on the y-axis. The Region variable fills the bars with different colors, and the fct\_reorder function is used to order the regions based on their percentage values. The geom\_bar() is used to create the bars, and the geom\_text() is used to add labels to the bars. The position\_stack argument adjusts the position of the labels within the bars.

[Visualizing associations](#contents.xhtml#sc2_109a)

In the upcoming sections, we will explore frequently used charts for depicting the associations between two variables.

[Boxplot](#contents.xhtml#sc3_110a)

Boxplots, also known as box-and-whisker plots, provide a graphical representation of central tendency, dispersion, and potential outliers, particularly when it comes to visualizing the relationship between a numerical and a categorical variable. Critical components of a boxplot are:

*   Box: This represents the interquartile range (IQR), which spans from the 25th to the 75th percentile of the distribution. Its length visually depicts the spread of the data. A more extended box indicates greater variability, while a shorter box suggests a more concentrated distribution.
*   Median line: A bold line drawn within the box marks the median, the 50th percentile. Its position within the box hints at symmetry or skewness.
*   Whiskers (Lines): Lines extending from the box's edges, typically reaching the farthest non-outlier points. They provide a sense of the overall data range.
*   Outliers: Individual points plotted beyond the whiskers, often defined as values more than 1.5 times the IQR from the box's edges. These outliers highlight unusual observations that may significantly differ from the bulk of the data.

Essential applications in data analysis

Boxplots are particularly useful for tasks such as:

*   Comparing distributions: Side-by-side boxplots show differences in central tendencies, spread, and shape between groups or categories.
*   Identifying outliers: Pinpointing unusual observations that might skew results or reveal unexpected patterns.
*   Visualizing skewness: Observing the median's position within the box and the whiskers' relative lengths quickly reveals whether a distribution is symmetrical or skewed.

Now, let us explore and visualize the trip data for Yellow Taxi Cabs in January 2023, accessible through the New York City Taxi and Limousine Commission (TLC). This dataset captures diverse details for each taxi journey, such as the pickup/drop-off times, distance covered, and fare amounts. Data source: [https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page).

For our analysis, we have utilized a specific subset of this data, as outlined below:

| Column name || Description |
| --- | --- |
| tpep\_pickup\_datetime || The timestamp for when the taxi meter was activated. |
| tpep\_dropoff\_datetime || The timestamp for when the taxi meter was deactivated. |
| trip\_distance || The recorded distance covered during the trip, measured in miles by the taxi meter. |
| RatecodeID || The rate code applicable at the end of the trip.1= Standard rate2= JFK |
| fare\_amount || The fare computed by the meter based on both time and distance. |

Table 7.1: Description of Yellow Taxi Cabs Trip Data

*   cab\_rides <- read.csv("cab\_rides.csv")
*   
*   \# Convert datatypes
*   cab\_rides$RatecodeID <- as.factor(cab\_rides$RatecodeID)
*   
*   cab\_rides <- cab\_rides %>% mutate(pickup\_date = as\_date(tpep\_pickup\_datetime))
*   
*   \# Create a boxplot to visualise the driving speed distribution
*   ggplot(cab\_rides, aes(x = "", y = speed)) +
*    geom\_boxplot() +
*    labs(
*    title = "Driving Speed Distribution",
*    x = "",
*    y = "Speed (mph)"
*    ) +
*    theme\_bw()

![](images/Figure7.12.png)

Figure 7.12: Box Plot

Moving forward, let us explore how speed varies across different times of the day. To do this, we will add a new column titled pickup\_timeofday. This column will contain information about the time of day when each ride was picked up, allowing us to analyze how driving speed varies across different time periods. The function, time\_of\_day, takes a single argument x, representing a specific hour of the day. The function then uses a series of if statements to determine whether the given hour falls within one of four predefined periods: morning (6 am-11 am), afternoon (12 pm-4 pm), evening (5 pm-9 pm), or night (10 pm-5 am). Depending on the result of these checks, the function returns a corresponding string value indicating the time of day. The resulting pickup\_timeofday column is converted to an ordered factor type using the factor function. This ensures that the values in the column are treated as categorical data with a defined order rather than simply as strings. The levels argument specifies the order of the categories, while the ordered argument indicates that the categories should be treated as ordinal data.

*   \# Create a function to calculate the time of the day
*   time\_of\_day <- function(x) {
*    if (x %in% 6:11) {
*    return('Morning')
*    } else if (x %in% 12:16) {
*    return('Afternoon')
*    } else if (x %in% 17:21) {
*    return('Evening')
*    } else {
*    return('Night')
*    }
*   }
*   
*   \# Create a new column- pickup\_timeofday
*   cab\_rides <- cab\_rides %>%
*    mutate(pickup\_timeofday = sapply(pickup\_hour, time\_of\_day))
*   
*   \# Create pickup\_timeofday, an ordered factor type 
*   cab\_rides$pickup\_timeofday <- factor(cab\_rides$pickup\_timeofday, levels = c("Morning", "Afternoon", "Evening", "Night"), ordered = TRUE)
*   
*   \# Create a boxplot to visualize the speed distribution by the time of the day
*   ggplot(cab\_rides, aes(x = pickup\_timeofday, y = speed)) +
*    geom\_boxplot() +
*    labs(
*    title = "Distribution of Speed by Time of Day",
*    x = "Time of Day",
*    y = "Speed"
*    ) +
*    theme\_bw()

![](images/Figure7.13.png)

Figure 7.13: Distribution of Speed by Time of the Day

The above code generates a boxplot to visualize the distribution of driving speed by the time of day. It uses the ggplot function to create a scatterplot with pickup\_timeofday on the x-axis and speed on the y-axis. The geom\_boxplot function is used to add a boxplot layer to the plot, which displays the median, quartiles, and outliers of the speed distribution for each time-of-day category. The above graph illustrates that the pattern of driving speed follows typical trends. On average, the speed increases steadily from late evening until morning hours.

[Scatter plot](#contents.xhtml#sc3_111a)

Scatter plots are graphical representations that depict the relationship between two numerical variables. Each data point is represented by a dot on the graph, where the position of the dot reflects the values of both variables for that particular data point. It lets us see how the values of one variable change as the other variable changes. This makes scatter plots particularly useful for exploring complex datasets and identifying potential areas of interest for further analysis. It is also essential to carefully consider which variable should be the explanatory variable and which should be the response variable. The explanatory variable influences or causes changes in the response variable. The response variable is being measured or observed.

Let us take a closer look at the association between the distance covered and their corresponding fare amounts. In this context, we will assign the distance traveled as the explanatory variable (x-coordinate) and the fare calculated by the meter as the response variable (y-coordinate). This plot will help us answer questions such as - do short rides always cost less than long ones? Are there any surprises, like expensive short trips or cheap long ones? Are there other factors that affect the fare?

*   \# The relationship between Trip Distance and the Fare amount
*   ggplot(cab\_rides, aes(x = trip\_distance, y = fare\_amount)) +
*    geom\_point(col = "steelblue4", alpha = 0.5) +
*    labs(
*    title = "Trip Distance v/s Fare Amount",
*    x = "Distance (Miles)",
*    y = "Amount (USD)"
*    ) +
*    theme\_bw()

The following figure is a scatter plot depicting the relationship between trip distance and fare amounts:

![](images/Figure7.14.png)

Figure 7.14: Scatter Plot

Here, the geom\_point layer adds individual data points to the plot, represented by steel blue color (col = "steelblue4") with a transparency level of 0.5 (alpha = 0.5) for improved visibility. The above scatterplot shows a positive correlation between trip distance and fare amount, signifying that the fare amount also tends to rise as the distance increases. We will examine the data based on the RatecodeID variable to understand this association better. In the plot below, the points' color and shape are determined by the RatecodeID, providing a visual distinction for different categories.

*   \# The relationship between Trip Distance and the Fare amount by RatecodeID
*   ggplot(cab\_rides, aes(x = trip\_distance, y = fare\_amount)) +
*    geom\_point(aes(col = RatecodeID, shape = RatecodeID), alpha = 0.6) +
*    labs(
*    title = "Trip Distance v/s Fare Amount",
*    x = "Distance (Miles)",
*    y = "Amount (USD)"
*    ) +
*    theme\_bw()

![](images/Figure7.15.png)

Figure 7.15: Association between Trip Distance and Fare Amount

In the RatecodeID = 1 (Standard Rate fare category), the relationship between distance and fare amount is generally linear, with the fare amount increasing as the distance traveled increases. However, there are some outliers that do not follow this trend. On the other hand, in the RatecodeID = 2 (JFK Airport fare category), the relationship between distance and fare amount is not linear due to the fixed initial flat fare of 70 USD for trips to or from JFK Airport. There are also outliers where the fare falls below 70 USD.

Facets

Faceting is used to generate small multiples, which are a series of plots or graphs that display different subsets of the data. These small multiples allow us to quickly and easily compare patterns in different parts of the data and identify similarities or differences. By dividing a plot into facets based on a categorical variable, you can gain insights into variations and trends specific to each category. Faceting is particularly valuable when dealing with complex datasets containing multiple dimensions or factors.

Two commonly used functions for faceting in ggplot2 are facet\_wrap() and facet\_grid(). facet\_wrap() wraps a one-dimensional ribbon of panels into a two-dimensional display, while facet\_grid() creates a two-dimensional grid of panels defined by variables, forming rows and columns. In the below code, facet\_grid(RatecodeID~.) is used to create a grid of facets based on the RatecodeID variable.

*   \# The relationship between Trip Distance and the Fare amount by RatecodeID
*   ggplot(cab\_rides, aes(x = trip\_distance, y = fare\_amount)) +
*    geom\_point(aes(col = RatecodeID, shape = RatecodeID), alpha = 0.6) +
*    labs(
*    title = "Trip Distance v/s Fare Amount",
*    x = "Distance (Miles)",
*    y = "Amount (USD)"
*    ) +
*    facet\_grid(RatecodeID~.) +
*    theme\_bw()

![](images/Figure7.16.png)

Figure 7.16: Association between Trip Distance and Fare Amount (Based on Ratecode ID)

Here, we observe the scatterplot is divided into multiple panels, each representing a different RatecodeID category. The RatecodeID~. notation signifies that the faceting should be done along the rows (RatecodeID) while maintaining a single-column layout.

[Visualizing time series using line chart](#contents.xhtml#sc2_112a)

Line charts provide an intuitive way to represent how a variable changes over time, making them especially effective for time-dependent data. The x-axis typically represents time, while the y-axis denotes the values of the variable of interest. By observing the patterns in the line chart, analysts can identify seasonality, cyclic behaviors, and potential anomalies. Line charts also provide a straightforward means of comparing multiple time series on the same plot, allowing for a comprehensive understanding of how different variables interact over time.

Let us now generate a line chart that visualizes how the number of taxi rides varied daily in January 2023. We create a dataset named total\_trips\_per\_day, grouping the data by the pickup date and calculating the total number of trips (total\_trips) for each unique date using the group\_by and summarize functions. Then, we will utilize the total\_trips\_per\_day dataset to generate a line chart illustrating the total number of trips made daily.

*   \# Create a summarised dataset for analysis
*   total\_trips\_per\_day <- cab\_rides %>%
*    group\_by(pickup\_date) %>%
*    summarize(total\_trips = n())
*   
*   \# Line chart visualizing Total trips on January 2023
*   ggplot(total\_trips\_per\_day, aes(x = pickup\_date, y = total\_trips)) +
*    geom\_point() +
*    geom\_line() +
*    labs(
*    title = "Total Trip Distribution on January 2023",
*    x = "Pickup Date",
*    y = "Total Trips"
*    ) +
*    theme\_bw()

The following figure is an illustration of a line chart:

![](images/Figure7.17.png)

Figure 7.17: Trip Distribution on January 2023

In the above code, the geom\_point() adds individual data points to the plot, while geom\_line() connects these points with lines, creating a continuous line chart representing the trend of total trips over the specified time period. The line chart demonstrates a consistent weekly trend in the number of taxi rides during the month of January.

[Conclusion](#contents.xhtml#sc2_113a)

In this chapter, we have explored various visualizing techniques using the ggplot2 package. We began by discussing the ggplot2 template and aesthetics, which provide a framework for creating customized plots. We then visualized distributions using bar plots, histograms, and density plots. These techniques allowed us to check the frequency and distribution of data across different categories. Next, we discussed visualizing proportions using pie charts and stacked bar plots. These techniques enabled us to compare the relative sizes of different categories within a dataset. We also explored boxplots, which are helpful for examining the spread and central tendency of data. Finally, we covered techniques for visualizing associations between variables, including scatter plots and line charts. These techniques are used to visualize the relationship between two or more variables and identify patterns or trends in the data.

In the next chapter, we will focus on feature engineering, which involves transforming variables and creating new features in a dataset to improve the performance of machine learning models.

Join our book’s Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/fm1.png)

# [CHAPTER 8Feature Engineering](#contents.xhtml#ch08a)

[Introduction](#contents.xhtml#sc2_114a)

Features are the fundamental components of machine learning models, representing raw data in a numeric format that algorithms can easily process. However, there are countless ways to transform raw data into features, and the choice of features can significantly impact the accuracy and effectiveness of an ML model.

In this chapter, we will explore the art of feature engineering, which involves selecting and transforming the most relevant features from our data to improve the performance of machine learning models. The number of features used in a ML model plays a crucial role in its performance. If there are not enough informative features, the model may struggle to complete the task at hand.

On the other hand, having too many features, especially irrelevant ones, can make the model more complex and difficult to train. Therefore, it is essential, to strike a balance between the number of features, and their relevance to the task.

[Structure](#contents.xhtml#sc2_115a)

Within this chapter, we will explore various techniques for handling both numeric and categorical data.

*   Understanding feature engineering
*   Transforming numeric data 
    *   Z-score scaling
    *   Min-max scaling
    *   Binning
    *   Feature clipping
*   Dealing with categorical data 
    *   Label encoding
    *   One-hot encoding
    *   Dummy encoding

[Objectives](#contents.xhtml#sc2_116a)

In this chapter, we will discuss the fundamental concepts of feature engineering, which is the art of preparing our data for effective machine learning. You will learn how to identify crucial features in your data and use techniques like binning and feature scaling to extract them. Additionally, you will learn how to encode categorical data and create new features based on your existing data. By the end of this chapter, you will have the skills necessary to get your data ready for machine learning so that you can make more accurate predictions.

[Understanding feature engineering](#contents.xhtml#sc2_117a)

Consider feature engineering as a way to assist the ML model in comprehending the dataset like your own understanding. Just as an artist carves away unnecessary parts of a marble block to reveal a masterpiece, feature engineering carefully chooses, changes, and makes new aspects of data to expose its hidden patterns.

Feature engineering is about tweaking and improving the predictors in a model so that it can better find meaningful relationships between predictors and responses. The word engineering implies a purposeful way of fixing performance problems and improving predictions. Knowing that there are different ways to represent features in a model and realizing that some work better than others is at the core of feature engineering. Feature engineering, therefore, becomes the practice of crafting data representations that optimize a model's effectiveness. It acknowledges that how we present data to a model can significantly impact its predictive capabilities. It is important to note that multiple factors contribute to a model's effectiveness. For instance, if a predictor lacks a meaningful relationship with the response variable, the representation of that predictor becomes inconsequential.

![](images/Figure8.1.png)

Figure 8.1: The position of feature engineering within the broader context of a typical ML workflow

The preceding figure shows where feature engineering fits into the bigger picture of a typical ML workflow. It is all about creating features from the raw data. The outlined process may not strictly follow a sequence. Modifying the features during the training phase may be necessary based on insights gained regarding which features are effective and which are not.

Feature engineering can present several challenges due to its reliance on a mix of data analysis skills, domain expertise, and a certain level of intuition. One common pitfall in feature creation is the inclination to directly use readily accessible data without consulting relevant experts conducting thorough research, or engaging in exploratory thinking. By neglecting these crucial steps, there is a risk of overlooking essential predictive variables that could significantly impact model performance.

Before diving into feature transformations, exploring and cleaning your dataset thoroughly is crucial. This initial step involves:

*   Examining the data: Inspect several rows to understand its structure, content, and potential issues.
*   Checking basic statistics: Calculate descriptive statistics (for example, mean, median, standard deviation) to identify anomalies and uncover initial patterns.
*   Visualizing the data: Create scatter plots, histograms, and other visualizations to identify patterns and anomalies that might not be evident from numerical summaries. Visualizations should be used throughout the transformation process to assess the impact of changes and validate assumptions.

The well-known saying garbage in, garbage out certainly holds true for ML. This means that the quality of the resulting model is heavily dependent on the input data. Imagine you are building a castle. Strong, well-placed bricks make construction smooth and the final castle sturdy. But if you use wonky, misshapen bricks, you will need a more complex, elaborate design to achieve the same stability. Similarly, in machine learning, the quality of your features directly impacts the model you build. Good features, like informative and relevant data, make training your model easier and lead to a more accurate and efficient one. Conversely, poor features require complicated models and often underperform. 

When preparing data for ML models, we often transform it to make it more compatible and informative. This process, called data transformation, is a crucial part of feature engineering. Here are the key reasons why we transform features:

*   Ensuring data compatibility 
    *   Numerical representation: ML algorithms rely on numerical calculations. Therefore, transforming non-numeric features, such as categorical variables or textual data, into numeric representations becomes necessary for compatibility.
*   Enhancing data quality 
    *   Reducing noise: Applying binning or smoothing techniques reduces noise and makes patterns more evident.
    *   Handling missing values: Filling in missing data points using imputation techniques (for example, mean, median, mode, or more sophisticated methods) or removing them strategically.
*   Improving model performance
    
    *   Feature scaling: Bringing features to similar scales to prevent some features from dominating others, especially in algorithms sensitive to feature magnitude (for example, distance-based algorithms).
    
    Techniques: normalization and standardization.
    
    *   Handling skewed distributions: Transforming skewed distributions (for example, income, lifespan) to improve model accuracy and reduce the impact of outliers. Techniques: log transformation and power transformation.
*   Extracting meaningful information
    
    o Creating derived features: Combining or transforming existing features to capture new information or relationships that might be more relevant to the ML model.
    

[Transforming numeric data](#contents.xhtml#sc2_118a)

Imagine that we are predicting if a customer will click on a particular ad displayed on a website. Two key features might be:

*   Number of times the ad was displayed (impressions): This could range from 1 to 1000, with higher numbers suggesting more exposure.
*   Time since the user last clicked on any ad: Values may vary from minutes to months, with shorter times indicating higher interest.

Raw numbers are great, but they do not tell the whole story. To a machine learning algorithm, these are just two columns of numbers. Here is how transforming them can unlock hidden insights:

*   Log-scaling impressions: A user seeing the ad 10 times vs. 1000 times is a much more significant difference than, say, 500 vs. 600. Log scaling compresses the large range of impressions, making smaller changes more impactful for the model.
*   Binning time since last click: Grouping times into buckets like less than a day, 1-3 days, and over a week captures the changing user interest over time. This helps the model understand that recent clicks are more relevant than distant ones.

Transforming numeric variables is not just about manipulating numbers; it is about using our understanding of the problem and the data to present them in a way that makes sense to the model. It is like speaking the language of algorithms, allowing them to see the world through our eyes and make better predictions.

There is no one-size-fits-all approach to transforming numeric data. The best technique depends on your specific dataset and your model's needs. Experiment, explore, and keep asking yourself: How can I guide these numbers to reveal the true story within my data?

Feature Scaling ensures that each feature contributes meaningfully to the model's learning process, regardless of its original scale, leading to more accurate representations of the underlying data patterns.

[Z-score scaling](#contents.xhtml#sc3_119a)

Z-score scaling (standardization) transforms numerical data into a standardized distribution with a mean of 0 and a standard deviation of 1. The process involves subtracting the mean of the dataset from each data point and then dividing by the standard deviation. This ensures that the resulting distribution is centered around 0 and expressed, in terms of standard deviations from the mean. The formula for calculating a z-score is:

![](images/EQ-1.jpg)

where x’ = standardized value (z-score), x = is the original data point,![](images/EQ-2.jpg)\= mean of the dataset, and![](images/EQ-3.jpg)\= standard deviation of the dataset.

In our discussion, we will use, the Algerian Forest Fires dataset, from the well-known UCI ML repository. Here, each instance is associated with specific attributes describing weather conditions, Fire Weather Index indicators, and categorical labels designating whether a particular observation resulted in a forest fire or did not result in one.

The temperature follows a normal distribution, ranging from 22 to 42 degrees Celsius. In this scenario, most temperature values are distributed across the entire range, providing a balanced data representation. Let us visualize the distribution of the column temperature:

*   \# Distribution of the Temperature
*   ggplot(forest\_fires, aes(x = Temperature)) +
*    geom\_histogram(binwidth = 1,fill = "steelblue3", color = "black", boundary = 0) +
*    labs(x = "Temperature (in Celsius Degrees)",
*    y = "Frequency") +
*    theme\_bw()

![](images/Figure8.2.png)

Figure 8.2: Distribution of temperature

Now, we create a function named z\_score\_scaling that takes a numeric vector x as input. The function uses the Z-score scaling formula to transform the values of x into a standardized distribution. Then, we apply z\_score\_scaling to the Temperature column.

*   \# Z-Score scaling function
*   z\_score\_scaling <- function(x) {
*    (x - mean(x)) / sd(x)
*   }
*   
*   \# Apply Z-Score scaling to the Temperature column
*   forest\_fires$Temperature\_Z\_Score <- z\_score\_scaling(forest\_fires$Temperature)
*   
*   \# Distribution of the Scaled Temperature
*   ggplot(forest\_fires, aes(x = Temperature\_Z\_Score)) +
*    geom\_histogram(binwidth = 1, fill = "steelblue3", color = "black", boundary= 0) +
*    labs(x = "Scaled Temperature (Z-Scores)",
*    y = "Frequency") +
*    theme\_bw() 

![](images/Figure8.3.png)

Figure 8.3: Distribution of the scaled temperature (Z-scores)

The Z-score scaling process transforms the original temperature values into a distribution with a mean of 0 and a standard deviation of 1. A positive z-score indicates that a temperature is above the mean, while a negative z-score indicates, it is below the mean. For example, a z-score of 2 indicates that the value is 2 standard deviations above the mean. A z-score of 0 means the temperature is exactly at the mean. Note, that it is sensitive to outliers; extreme values can disproportionately impact the mean and standard deviation.

[Min-max scaling](#contents.xhtml#sc3_120a)

Min-max scaling (normalization) transforms features to a standard range, typically between 0 and 1. Min-max scaling works by subtracting the minimum value of a feature from each datapoint and then dividing by the difference between the maximum and minimum values. Mathematically, this can be represented as:

x’ = (x - xmin ) / (xmax -xmin )

where x’ is the scaled value, xmin is the original value, represents the minimum value of the feature, and is the maximum value of the feature.

This method of scaling works particularly well in cases where the distribution of the feature is roughly uniform, and no significant outliers are present in the data. Extreme values can significantly stretch the scaling range, compressing most data points into a narrow region. If feature distributions are skewed or have long tails, min-max scaling might not be the best choice.

Let us define a function called min\_max\_scaling that takes a vector of data as input and returns a scaled version of the data. Then, we create a new column, Temperature\_Scaled, by applying min-max scaling to the temperature values to transform them into a standardized scale between 0 and 1.

*   \# Min-Max scaling function
*   min\_max\_scaling <- function(x) {
*    (x - min(x)) / (max(x) - min(x))
*   }
*   
*   \# Apply Min-Max scaling to the Temperature column
*   forest\_fires$Temperature\_Scaled <- min\_max\_scaling(forest\_fires$Temperature)
*   
*   \# Distribution of the Scaled Temperature
*   ggplot(forest\_fires, aes(x = Temperature\_Scaled)) +
*    geom\_histogram(binwidth = 0.125, fill = "steelblue3", color = "black", boundary = 0) +
*    labs(x = "Scaled Temperature",
*    y = "Frequency") +
*    theme\_bw() 

![](images/Figure8.4.png)

Figure 8.4: Distribution of the scaled temperature (mi-max scaling)

[Binning](#contents.xhtml#sc3_121a)

Binning numerical data refers to transforming continuous variables into discrete categories or intervals, thereby changing them from quantitative to qualitative attributes. This procedure can identify potential non-linear relationships between features and target variables that linear models might miss. Furthermore, categorical features can be easier to interpret and explain than numerical ones. However, binning inherently involves a loss of granularity. Carefully consider the trade-off between detail and generalization. Too few bins can oversimplify patterns; too many can complicate analysis and reduce model generalizability. You can experiment with different bin sizes and visualize results to ensure meaningful segmentation.

When choosing to apply binning to numerical features, it is imperative, to clearly define the boundary settings and identify the type of binning. Two common types of binning approaches include:

*   Equal-width binning
*   Quantile binning

Equal-width binning

Equal-width binning is a straightforward binning technique, that partitions a numerical feature's range into bins of equal width. It is often a simple and intuitive approach, but it is also crucial to consider its suitability for different data distributions. Equal-width binning may be sensitive to outliers, as extreme values can disproportionately influence the bin boundaries. Now, we will categorize the continuous temperature values into four bins.

*   \# Define the number of bins
*   num\_bins <- 4
*   
*   \# Create bins for the temperature data
*   forest\_fires$temp\_bins <- cut(forest\_fires$Temperature, breaks = num\_bins, labels = FALSE)
*   
*   \# Convert temp\_bins to factor
*   forest\_fires$temp\_bins <- as.factor(forest\_fires$temp\_bins)

Here, the cut() function creates bins for the 'Temperature' feature based on the previously defined num\_bins. Within the function call, 'breaks=num\_bins' indicates the desired quantity of divisions along the Temperature axis. Labels as 'FALSE' imply that generated levels receive default integer assignments (1, 2, ..., n\_bins). The values in the temp\_bins column are converted to a factor.

*   \# Distribution of the Temperature with bin lines
*   ggplot(forest\_fires, aes(x = Temperature, fill = temp\_bins)) +
*    geom\_histogram(binwidth = 1, color = "black", boundary = 0) +
*    geom\_vline(xintercept = seq(min(forest\_fires$Temperature), max(forest\_fires$Temperature), length.out = num\_bins + 1),
*    linetype = "dashed", color = "darkred", linewidth = 0.8) +
*    scale\_fill\_brewer(palette = "Set2") +
*    labs(x = "Temperature",
*    y = "Frequency",
*    fill = "Temperature Bins") +
*    theme\_bw()

![](images/Figure8.5.png)

Figure 8.5: Distribution of temperature with equal-width binning

The preceding figure shows the distribution of temperature, categorized into four bins. The dashed vertical lines denote the boundaries of the temperature bins. The color palette, Set2, is applied to distinguish the bins visually.

Quantile binning

While equal-width binning divides a feature's range into intervals of uniform size, quantile binning takes a different approach, ensuring each bin contains approximately the same number of observations. This makes it particularly suitable for handling skewed or irregularly distributed data. It handles data with varying densities across its range, ensuring each bin holds similar importance. The code below performs quantile binning on the Temperature column.

*   \# Perform quantile binning on the Temperature column
*   forest\_fires$temperature\_quantile\_bins <- cut(forest\_fires$Temperature,breaks = quantile(forest\_fires$Temperature),labels = FALSE,include.lowest = TRUE)
*   
*   \# Convert quantile bins to factor
*   forest\_fires$temperature\_quantile\_bins <- as.factor(forest\_fires$temperature\_quantile\_bins)

Here, by setting breaks=quantile(forest\_fires$Temperature), we ensure an equal number of samples in each category. The following figure displays the distribution of the temperature with the quantile binning.

*   \# Create a histogram with quantile binning
*   ggplot(forest\_fires, aes(x = Temperature, fill = temperature\_quantile\_bins)) +
*    geom\_histogram(binwidth = 1, color = "black", boundary = 0) +
*    geom\_vline(xintercept = quantile(forest\_fires$Temperature),
*    linetype = "dashed", color = "darkred", linewidth = 0.8) +
*    scale\_fill\_brewer(palette = "Set2") +
*    labs(x = "Temperature",
*    y = "Frequency",
*    fill = "Quantile Bins") +
*    theme\_bw()

![](images/Figure8.6.png)

Figure 8.6: Distribution of temperature with quantile binning

[Feature clipping](#contents.xhtml#sc3_122a)

When dealing with extreme outliers in your data, consider implementing feature clipping to mitigate their impact. It involves capping feature values above or below a defined threshold, effectively reducing their influence without removing them entirely. For instance, you may clip all “Rain” values exceeding 5 mm, ensuring they are capped at 5. Another effective approach is using measures like standard deviation (σ) to define thresholds. Example: Clip values beyond +3σ or -3σ of the mean. Note, that the feature clipping is a tool to manage outliers, but understanding their causes and choosing appropriate methods is crucial for robust model development. [Figure 8.7](#ch08.xhtml#fig8-7) in the following displays the original distribution of the rain column:

*   \# Distribution of the Rain
*   ggplot(forest\_fires, aes(x = Rain)) +
*    geom\_histogram(binwidth = 1, fill = "steelblue3", color = "black", boundary = 0) +
*    labs(x = "Rain (in mm)",
*    y = "Frequency") +
*    theme\_bw() 

![](images/Figure8.7.png)

Figure 8.7: Distribution of Rain

Let us create a new column, Rain\_Capped, where any values in the original Rain column exceeding 5 are replaced with the capped value of 5.

*   \# Create a column, Rain\_Capped
*   forest\_fires <- forest\_fires %>%
*    mutate(Rain\_Capped = ifelse(Rain > 5, 5, Rain))
*   
*   \# Distribution of the Capped Rain
*   ggplot(forest\_fires, aes(x = Rain\_Capped)) +
*    geom\_histogram(binwidth = 1,fill = "steelblue3", color = "black", boundary = 0) +
*    labs(x = "Rain (in mm)",
*    y = "Frequency") +
*    theme\_bw() 

![](images/Figure8.8.png)

Figure 8.8: Distribution of the rain (Capped)

[Dealing with categorical data](#contents.xhtml#sc2_123a)

A categorical variable represents different categories or labels with a finite number of distinct values. These values may convey information about qualitative attributes, such as product types, customer segments, or seasons. Transforming categorical variables to numeric is essential for ML as most ML algorithms are specifically designed to process and analyze numerical data. They use mathematical operations, distance calculations, and statistical analyses inherently based on numbers. Numerical representations allow them to capture meaningful differences and similarities between data points.

[Label encoding](#contents.xhtml#sc3_124a)

Label encoding is a simple yet effective way to transform categorical variables into numerical values. It involves assigning unique integer labels to each category in the variable.

Let us create a sample data frame, customer\_category, with two columns: customer\_id and customer\_segment. The customer\_segment column, represents different customer categories such as first-time purchasers, loyal customers, and lapsed purchasers.

*   \# Create a sample dataframe 
*   customer\_category <- data.frame(
*    customer\_id = 1:7,
*    customer\_segment = c("First-time purchasers", "Loyal customers", "Loyal customers", "Lapsed purchasers", "First-time purchasers", "Lapsed purchasers", "Loyal customers")
*   )

Next, we define a label encoding function named label\_encode. This function takes a vector x as input, identifies unique levels within the vector, and assigns numeric labels to each unique level. Then, we create a new column named customer\_segment\_encoded by applying the defined label\_encode function to the customer\_segment column.

*   \# Define a label encoding function
*   label\_encode <- function(x) {
*    levels <- unique(x)
*    as.numeric(factor(x, levels = levels))
*   }
*   
*   \# Create a new column with label encoding
*   customer\_category <- customer\_category %>%
*    mutate(customer\_segment\_encoded = label\_encode(customer\_segment)) 
    
    | customer\_id || customer\_segment || customer\_segment\_encoded |
    | --- | --- | --- |
    | 1 || First-time purchasers || 1 |
    | 2 || Loyal customers || 2 |
    | 3 || Loyal customers || 2 |
    | 4 || Lapsed purchasers || 3 |
    | 5 || First-time purchasers || 1 |
    | 6 || Lapsed purchasers || 3 |
    | 7 || Loyal customers || 2 |
    

Table 8.1: Label encoding of Customer Segments

Recognizing whether your categorical variables have a specific order, is crucial while including the embedded information in a model. For ordered factors, you can leverage another technique called ordinal encoding. It assigns numbers to categories in a way that reflects their order. Unlike unordered factors, where numbers are just labels, ordinal encoding ensures the assigned numbers represent the meaningful order among the categories.

For example, consider customer satisfaction levels that are categorized as Low, Medium, and High, indicating different degrees of satisfaction. Ordinal encoding would assign numerical values to these satisfaction levels to reflect their order in this scenario. For instance, Low could be assigned the value 1, Medium the value 2, and High the value 3. This encoding ensures that the numeric labels capture the inherent order of satisfaction levels, where a higher numerical value corresponds to a higher degree of satisfaction. This approach allows a machine learning model to understand and leverage the ordinal relationships in customer satisfaction levels, improving its ability to make predictions or classifications based on the ordered nature of the data.

[One-hot encoding](#contents.xhtml#sc3_125a)

This technique creates a new binary variable for each unique level or category within a nominal feature. Each binary variable, serves as a flag, indicating the presence (1), or absence (0) of a specific category. One-hot encoding is particularly useful when dealing with categorical variables with no inherent order among the categories. It ensures the model does not misinterpret the data by assigning unintended significance to the numeric labels.

You can use dummy\_cols() from the fastDummies package to perform one-hot encoding for the customer\_segment column as follows:

*   library(fastDummies)
*   
*   \# Perform one-hot encoding using dummy\_cols()
*   customer\_category\_encoded <- dummy\_cols(customer\_category, select\_columns = "customer\_segment")

| customer\_id || customer\_segment || customer\_segment\_First-time purchasers || customer\_segment\_Lapsed purchasers || customer\_segment\_Loyal customers |
| --- | --- | --- | --- | --- |
| 1 || First-time purchasers || 1 || 0 || 0 |
| 2 || Loyal customers || 0 || 0 || 1 |
| 3 || Loyal customers || 0 || 0 || 1 |
| 4 || Lapsed purchasers || 0 || 1 || 0 |
| 5 || First-time purchasers || 1 || 0 || 0 |
| 6 || Lapsed purchasers || 0 || 1 || 0 |
| 7 || Loyal customers || 0 || 0 || 1 |

Table 8.2: One-hot encoding of Customer Segments

[Table 8.2](#ch08.xhtml#tab8-2) shows that the dummy\_cols() creates binary columns for each unique category in the column customer\_segment.

[Dummy encoding](#contents.xhtml#sc3_126a)

For dummy encoding, we create one binary variable for each category, except one, which becomes the reference category. This eliminates the potential for multicollinearity, a statistical issue, that can arise when variables are highly correlated.

To apply dummy encoding using the dummy\_cols(), simply set the remove\_first\_dummy argument to TRUE, as shown in the following. Removing one dummy variable helps prevent linear dependence among the encoded features.

*   \# Perform dummy encoding
*   customer\_category\_encoded <- dummy\_cols(customer\_category, select\_columns = "customer\_segment", remove\_first\_dummy = TRUE)

| customer\_id || customer\_segment || customer\_segment\_Lapsed purchasers || customer\_segment\_Loyal customers |
| --- | --- | --- | --- |
| 1 || First-time purchasers || 0 || 0 |
| 2 || Loyal customers || 0 || 1 |
| 3 || Loyal customers || 0 || 1 |
| 4 || Lapsed purchasers || 1 || 0 |
| 5 || First-time purchasers || 0 || 0 |
| 6 || Lapsed purchasers || 1 || 0 |
| 7 || Loyal customers || 0 || 1 |

Table 8.3: Dummy encoding of Customer Segments

The preceding table shows that it retains the dummy columns for Lapsed purchasers and Loyal customers while discarding the dummy column for First-time purchasers due to the remove\_first\_dummy = TRUE setting. Dummy encoding effectively represents categorical data while addressing the potential for multicollinearity that can occur with one-hot encoding.

[Conclusion](#contents.xhtml#sc2_127a)

Feature engineering is a creative process that requires understanding the data and the problem you are trying to solve. It is an iterative process and time intensive. Experiment with different techniques to find what works best for your specific dataset and model. The goal is to create features that effectively represent the underlying patterns and relationships within the data, leading to better model performance and insights. The quality of your features often has a more significant impact on ML model performance than the choice of algorithm. The chapter extensively covers transforming numeric data, exploring Z-score scaling, min-max scaling, and Binning methods, and providing insights into when and how to apply these techniques. Dealing with categorical data is a crucial aspect, and the chapter comprehensively covers various approaches, including label encoding, one-hot encoding, and dummy encoding. The upcoming chapter will explore the fundamental principles of statistics and probability essential for data science.

# [CHAPTER 9Statistics and Probability](#contents.xhtml#ch09a)

[Introduction](#contents.xhtml#sc2_128a)

The essence of data science involves discovering valuable insights from vast amounts of structured and unstructured information. Statistics forms the foundational framework for this field, providing a solid basis for analyzing and interpreting data. It gives the essential grammar and vocabulary needed to understand and interpret the results of ML models. But statistics is about more than just understanding ML outputs. By summarizing and visualizing data through descriptive statistics, you can clearly picture trends, outliers, and relationships between variables. On the other hand, Probability is concerned with quantifying uncertainty and random phenomena. By incorporating probabilistic reasoning into analytical processes, you can model complex systems, predict future behaviors, optimize performance metrics, and derive actionable insights from massive datasets.

[Structure](#contents.xhtml#sc2_129a)

Within this chapter, we will cover the following topics:

● Population sampling

o Simple random sampling

o Stratified sampling

● Descriptive statistics

o Measures of central tendency

o Measures of dispersion

• Probability

• Inferential statistics

• Statistical hypothesis testing

• Covariance and correlation

[Objectives](#contents.xhtml#sc2_130a)

While statistics and probability are extensive fields that cannot be fully covered in a single chapter, this chapter aims to introduce the fundamental concepts necessary for understanding and working with machine learning models. You will learn how to select a representative sample from a population and calculate the various measures of central tendency and dispersion. You will also learn how to conduct statistical hypothesis tests and calculate correlations between variables.

[Population sampling](#contents.xhtml#sc2_131a)

A population is the entire group of individuals or things you are interested in studying. It can be any size, from a small group of students in a class to everyone living in a country. A sample is a finite subset of a population drawn according to a specific sampling strategy used to estimate population characteristics by studying the sample. But why not simply study the entire population? While theoretically ideal, it is often impractical, infeasible, and unnecessary.

Let us consider the quality control process in a manufacturing plant, specifically focusing on the production of smartphones. The manufacturer faces the challenge of ensuring the quality of each smartphone within a large production line. Inspecting every single unit would be time-consuming and also resource-intensive. Instead, the company decides to use a sample-based quality control strategy.

Imagine a scenario where the manufacturer selects a random sample of 500 smartphones from a production batch of 50,000 units. They assess this sample to determine the overall quality of the entire batch. The sample reveals that 95% of the phones meet the quality standards.

However, the validity of this conclusion depends on various sample considerations. First and foremost is the sample size. Is 500 a sufficiently representative subset of the 50,000 smartphones? If the sample size is too small, it may not accurately reflect the true quality of the entire batch. Conversely, a large sample may incur unnecessary costs, without providing substantially more accurate results.

The method of sample selection is also critical. If smartphones are chosen haphazardly without a systematic approach, certain defects or issues may be overlooked, leading to an inaccurate representation of the overall product quality. Furthermore, the inspection criteria used in the quality assessment are crucial. If the criteria are too stringent or lenient, it can impact the classification of smartphones as either meeting or failing to meet quality standards.

In the manufacturing industry, where production volumes are high and resources are limited, effective sample considerations are vital for making informed decisions about product quality without the need to inspect every unit.

Simple random sampling

Simple random sampling (SRS) ensures each population element possesses an equiprobable chance of being chosen for the sample. This ensures that the sample accurately represents the entire population, minimizing bias and increasing reliability. Here, samples can either be with or without replacement.

Sampling with replacement

When we sample with replacement, each draw is independent of the others. This implies that the selection of one individual does not impact or affect the chances of selecting another individual in subsequent draws. The probability of selection of any specific individual remains constant throughout the sampling process. For instance, if we randomly select a student, record their study habits, and then return them to the population, the chances of selection of the same student again, in the next draw are the same as before, unaffected by the previous selection.

*   \# Generate a population of 100 students
*   population <- 1:100
*   
*   \# Select a simple random sample of 5 students with replacement
*   sample\_with\_replacement <- sample(population, size \= 5, replace \= TRUE)
*   
*   \# Display the sample
*   print(sample\_with\_replacement)
*   \## 68 19 67 90 68

The sample() function selects a simple random sample from the specified population vector. The size parameter indicates the number of elements to be selected, and replace = TRUE indicates that the sampling is done with replacement. This means that after each selection, the chosen student is returned, to the pool of eligible candidates for the next draw. Note that since sampling is done with replacement, the same student ID can appear more than once in the sample.

In the above example, the selections are independent. Each student is randomly chosen from the entire population, and after each selection, the student is placed back into the population, ensuring that their presence or absence does not influence subsequent draws.

Sampling without replacement

In contrast, when sampling without replacement, the selections are not independent. The outcome of the first draw affects the pool of eligible candidates for subsequent draws. Once an individual is selected, they are removed from the population, altering the probabilities for the next draw. The results of previous selections influence the composition of the sample. For example, if we randomly select students, record their study habits, and do not return them to the population, the pool of eligible candidates for the next draw is reduced. The chances of selecting the same student again are eliminated, and the probabilities for the remaining individuals are adjusted based on the first selection.

*   \# Select a simple random sample of 5 students without replacement
*   sample\_without\_replacement <- sample(population, size \= 5, replace \= FALSE)
*   
*   \# Display the sample
*   print(sample\_without\_replacement)
*   \## 76 50 11 25 72

Here, replace = FALSE indicates that the sampling is done without replacement. This means that once a student is selected, they are removed from the pool of eligible candidates for subsequent draws. Because sampling is done without replacement, each student ID appears only once in the sample.

When sampling without replacement, the selections are not independent. Each student is randomly chosen from the population, but once selected, they are removed from the pool of eligible candidates for subsequent draws. This alters the probabilities for the remaining individuals and introduces dependence between the selections.

Stratified sampling

Stratified sampling is another sampling technique, where the population is divided into distinct subgroups, or strata, based on specific characteristics, and then samples are randomly collected from each stratum. This method ensures representation from all relevant subgroups within the population, leading to a more accurate and reliable analysis.

In stratified sampling, the population is divided into non-overlapping strata based on specific characteristics (for example, age, gender, income level). Each stratum represents a homogeneous subgroup within the overall population. After creating strata, random samples are independently taken from each stratum. This ensures that each subgroup is adequately represented in the final sample.

Stratified sampling often provides more precise estimates than simple random sampling, especially when there is significant variability within the population. The sample size from each stratum is determined proportionally to the size of the stratum, in the entire population. 

Let us create a dataset named customers with two categorical variables: age\_group and shopping\_frequency. We assign each customer to an age\_group and a shopping\_frequency based on random sampling with specified probabilities, and we use set.seed(123) to ensure the reproducibility of the random sampling.

*   \# Create a dataset with customer information
*   set.seed(123) \# For reproducibility
*   customers <- data.frame(
*    customer\_id = 1:1000,
*    age\_group = sample(c("18-25", "26-35", "36-45", "46+"), 1000, replace = TRUE, prob = c(0.2, 0.3, 0.3, 0.2)),
*    shopping\_frequency = sample(c("occasional", "regular", "frequent"), 1000, replace = TRUE, prob = c(0.4, 0.3, 0.3))
*   )

Here, strata are defined based on customer demographics: age groups (18-25, 26-35, 36-45, 46+) and shopping frequency (occasional, regular, frequent). Now, let us perform stratified sampling using dplyr to select a sample of customers.

*   \# Stratified sampling
*   stratified\_sample <- customers %>%
*    group\_by(age\_group, shopping\_frequency) %>%
*    sample\_n(size \= 20, replace \= FALSE) 

In the above command, we use the group\_by() function to group the dataset by both, age\_group and shopping\_frequency. We then use sample\_n() to select a sample of size 20 from each stratum (group) without replacement, ensuring that each combination of age\_group and shopping\_frequency is represented in the sample. The table below shows the cross-tabulation of the age\_group and shopping\_frequency variables within the stratified\_sample dataset.

*   \# Cross-Tabulation of the age\_group and shopping\_frequency
*   table(stratified\_sample$age\_group, stratified\_sample$shopping\_frequency)

|  || frequent || occasional || regular |
| --- | --- | --- | --- |
| 18-25 || 20 || 20 || 20 |
| 26-35 || 20 || 20 || 20 |
| 36-45 || 20 || 20 || 20 |
| 46+ || 20 || 20 || 20 |

Table 9.1: Cross tabulation of the age\_group and shopping\_frequency variables

In the above table, the rows represent the distinct values of the age\_group, and the columns represent distinct values of the shopping\_frequency. Each cell in the table indicates the count of observations (20 for each cell) that fall into a specific combination of age\_group and shopping\_frequency.

[Descriptive statistics](#contents.xhtml#sc2_132a)

Descriptive statistics are the foundation for understanding any dataset. They provide concise summaries of a dataset's key characteristics, allowing us to understand its central tendency, variability, and shape. Measures, like mean, median, and mode capture the typical values, while variance, standard deviation, and range quantify data spread and potential outliers. Essentially, descriptive statistics equip us to answer fundamental questions like What is the average value? and How spread out is the data? laying the groundwork for further analysis and model building.

[Measures of central tendency](#contents.xhtml#sc3_133a)

A measure of central tendency is a statistical summary, that represents the central or typical value, within a dataset. These measures help summarize and understand the central location or tendency of the data distribution.

Consider a scenario in which a courier service manager wants to analyze the delivery times of her couriers. She wants to identify the typical time it takes, for packages to reach their destinations, acknowledging that occasional outliers may exist due to unforeseen circumstances.

The mean, or average, is obtained by adding up all values in a dataset and dividing the sum by the number of observations. The average delivery time is calculated by summing up all delivery times and dividing by the total number of deliveries. For instance, if there are seven delivery times, 18, 20, 22, 25, 28, 30, and an unexpected outlier of 3 hours due to an unusual incident, the mean would be (18 + 20 + 22 + 25 + 28 + 30 + 3) / 7 = 146 / 7 ≈ 20.86 hours.

While the mean is a commonly used measure of central tendency, there are scenarios where it might not provide accurate insights. The mean is sensitive to extreme values, known as outliers, which can skew its value and misrepresent the central tendency, as seen with the delivery time of 3 hours. In such cases, the median, which is less sensitive to extreme values, might offer a more robust indicator.

*   \# Create a dataframe
*   delivery\_data <- data.frame(
*    delivery\_times = c(18, 20, 22, 25, 28, 30, 3),
*    package\_types = c("Small", "Large", "Medium", "Large", "Small", "Medium", "Small")
*   )
*   
*   \# Calculate mean
*   mean\_delivery\_time <- mean(delivery\_data$delivery\_times)
*   cat("Mean Delivery Time:", mean\_delivery\_time, "hours")
*   \## Mean Delivery Time: 20.85714 hours

In contrast, the median is a central tendency measure that remains insensitive to extreme values. It represents the middle value of a dataset when arranged in ascending or descending order. Notice that the median does not depend on every value in your data, unlike the mean. In the given dataset of delivery times, arranged as 3, 18, 20, 22, 25, 28, and 30, the median is identified as the value of the fourth item. In this instance, with seven delivery times (an odd number), the median is 25 hours. Unlike the mean, the median is not contingent on every value in the dataset, making it a robust measure that withstands the impact of outliers.

*   \# Calculate median
*   median\_delivery\_time <- median(delivery\_data$delivery\_times)
*   cat("Median Delivery Time:", median\_delivery\_time, "hours")
*   \## Median Delivery Time: 22 hours

The mode is the value that occurs most frequently in a dataset. The manager now wants to understand the most prevalent package type among the couriers. For instance, if the dataset reveals that Small packages appear most frequently, Small becomes the mode. The mode function is not built into base R, so we can create a custom function.

*   \# Mode calculation
*   get\_mode <- function(x) {
*    unique\_values <- unique(x)
*    frequencies <- tabulate(match(x, unique\_values))
*    mode\_value <- unique\_values\[which.max(frequencies)\]
*    return(mode\_value)
*   }
*   \# Calculate the mode for package types
*   mode\_package\_type <- get\_mode(delivery\_data$package\_types)
*   cat("Mode Package Type:", mode\_package\_type)
*   \## Mode Package Type: Small

It is essential to meticulously evaluate the characteristics of the data and select the most appropriate measure of central tendency that aligns with the inherent nature of the dataset.

[Measures of dispersion](#contents.xhtml#sc3_134a)

Dispersion refers to the extent of spread or variability within a dataset. It provides insights into how the individual values deviate from the central tendency. Measures of dispersion are crucial for understanding the distribution and variability of data points.

Range is a simple yet effective method for measuring data variability, defined as the gap between the highest and lowest observed values. Generally, larger ranges signify greater disparity among observations. Although the range is easy to grasp, it has limitations. Its main drawback lies in being influenced considerably by outliers. When one unusual data point is extremely high or low, it drastically affects the entire range.

Consider that you are analyzing daily website traffic for an e-commerce platform. Your data comprises a vector named daily\_visits representing website visits over a month.

*   \# Create a vector, daily\_visits
*   daily\_visits <- c(1200, 950, 1500, 800, 1100, 1350, 1000, 1800, 750, 1400)
*   
*   \# Calculate Range
*   visits\_range <- diff(range(daily\_visits))
*   cat("Range of daily website visits:", visits\_range, "visits\\n")
*   \## Range of daily website visits: 1050 visits

Here, the range() returns a two-element vector containing the minimum and maximum values of the daily\_visits vector. The diff() calculates the differences between consecutive elements in a vector. In this case, it computes the difference between the maximum and minimum values obtained from the range() function. The range tells us the website traffic varied within 1050 visits.

Variance quantifies the extent of spread within a dataset. It measures the average squared difference between individual data points and the mean. The sample variance formula is following:

![](images/eq-11.jpg)

where,

 s2\= the sample variance

xi = value of each observation

![](images/eq-21.jpg)\= the sample mean

n–1 = the degrees of freedom

By squaring the differences, we ensure that positive and negative deviations do not offset one another. Therefore, variance is always non-negative, either zero or a positive number. A variance of zero indicates that all data points have identical values, indicating no variability. On the other hand, as the data values become more scattered, so does the variability. However, interpreting variance can be challenging since it involves squared units instead of natural data units. A higher variance implies increased variability; nevertheless, there is no clear-cut interpretation for particular values.

*   \# Calculate Variance
*   visits\_variance <- var(daily\_visits)
*   cat("Variance of daily website visits:", visits\_variance, "visits^2\\n")
*   \## Variance of daily website visits: 109472.2 visits^2

The var() function calculates the variance of a numeric vector, which measures the average squared deviation of each data point from the mean. The variance of the daily website visits over the specified period is approximately 109472.2 visits^2. Since the variance is expressed in squared units (visits^2), it may not be as intuitively interpretable as the original data.

Standard deviation, the square root of the variance, expresses variability in the original data units. Smaller standard deviation values imply that data points remain tightly clustered around the mean, whereas larger figures suggest wider scattering across diverse magnitudes. Unlike variance, which expresses variability in squared units and may not be as intuitively interpretable, standard deviation simplifies the interpretation by using the same units as the original data.

The standard deviation formula is:

![](images/eq-31.jpg)

where,

s2 = the sample standard deviation

xi\= value of each observation

![](images/eq-21.jpg)\= the sample mean

N = the number of observations

*   \# Calculate Standard Deviation
*   visits\_std\_dev <- sd(daily\_visits)
*   cat("Standard Deviation of daily website visits:", visits\_std\_dev, "visits\\n")
*   \## Standard Deviation of daily website visits: 330.8659 visits

The sd() calculates the standard deviation, representing the average amount by which individual daily visit counts deviate from the mean visit count. On average, daily visits deviate from the mean by roughly 330 visits.

[Probability](#contents.xhtml#sc2_135a)

Probability is a measure of the likelihood of an event occurring. It defines the chance or probability of an event happening out of all possible outcomes. Probability is always expressed as a number between 0 and 1, where 0 represents an impossible event, and 1 represents a certain event.

Probability helps us quantify uncertainty in data and model outcomes. For example, imagine building a model to predict customer churn. You cannot say for certain, which customers will leave, by analyzing past behavior and incorporating factors like purchase history and demographics, you can calculate the probability of churn for each customer. This helps prioritize outreach efforts and target resources effectively.

We denote the probability of the event E as P(E). In probability theory, events can be either independent or dependent. Independent events are characterized by their unrelated outcomes, meaning that the occurrence of one event does not affect the probability of the other. Dependent events, on the other hand, are closely linked with the occurrence of one event, providing information about the likelihood of the other. Let us consider two events, E and F. For independent events, the joint probability of both occurring, denoted as P (E and F), is equal to the product of their probabilities:

P(E and F) = P(E) \* P(F)

For example, imagine flipping two separate coins, each with a 50% chance of landing heads. The probability of both coins landing heads is 50% \* 50% = 25%, illustrating their independence.

However, for dependent events, the situation is different. The probability of event E occurring given that event F has already occurred It is denoted as P(E | F), is calculated using conditional probability:

P(E | F) = P(E and F) / P(F)

The conditional probability of E given F is determined by dividing the joint probability of both events happening by the individual probability of event F.

Suppose you are a manager at a retail store and want to determine the probability that a customer will buy a product given that they have picked it up and looked at it. This is an example of conditional probability because you are trying to determine, the probability, of the customer buying the product, given that they have already shown interest in it, by picking it up and looking at it.

Here, the events are

E: a customer buys a product.

F: a customer picks up and looks at a product.

The conditional probability: P(E|F): The probability, of a customer buying a product given they picked it up and looked at it. 

Conditional probability = (Probability of buying a product) × (Probability of picking up and looking at a product) / (Probability of picking up and looking at a product)

[Inferential statistics](#contents.xhtml#sc2_136a)

Inferential statistics helps us to draw meaningful conclusions and make predictions about a population based on a sample of data. Unlike descriptive statistics, which simply summarize and describe the main features of a dataset, inferential statistics takes the analysis a step further by making inferences or generalizations about a larger population from which the sample was drawn. This process involves using probability theory and statistical techniques to extrapolate findings from a representative subset of data to the entire population.

[Statistical hypothesis testing](#contents.xhtml#sc2_137a)

We frequently, come across situations, where we need to examine whether a given assumption carries statistical significance. Examples of these assumptions include statements like the average revenue per user has increased following the implementation of a new feature or customer engagement is higher on weekends than on weekdays. Hypothesis testing, allows us to examine these statements, using robust statistical methods critically. The hypothesis testing process involves several key steps:

1\. Formulate the hypothesis: Define the null hypothesis (H0) and alternative hypothesis (H1)

• Null hypothesis (H0): The null hypothesis, assumes that there is no significant relationship, effect, or difference between variables or groups under comparison. It always includes an equality condition, suggesting no variation from the expected outcome if only random chance were at play.

• Alternative hypothesis (H1): On the flip side, the alternative hypothesis is what data scientists aim to establish. The alternative hypothesis challenges the null hypothesis by stating that a statistically significant relationship, effect, or difference exists between the compared variables or groups. Notably, the alternative hypothesis never incorporates an equality condition.

In essence, and are mathematical opposites, representing two contrasting perspectives on the relationship between variables in the data. Let us consider a practical scenario. You are investigating whether the introduction of a personalized recommendation system on an e-commerce platform has led to a significant improvement in user click-through rates. In this case, the null hypothesis could assert that the recommendation system has no effect and that any observed changes are merely due to random chance. Conversely, the alternative hypothesis asserts, that there is a tangible increase in click-through rates, attributable to the recommendation system.

2\. Decide the test statistic

Once we have set our hypothesis, we need to choose a statistical test that will help us determine, whether we can reject the null hypothesis, or not. There are many statistical tests available, but the commonly used ones are:

• Z-test: The z-test is a widely used test statistic, particularly for hypothesis tests involving means. It is ideal for large samples (n > 30) and assumes that the data follows a normal distribution.

• T-test: The t-test is another commonly used test statistic, similar to the z-test but more versatile. It can handle smaller samples (n < 30) and relaxes the assumption, of normality. 

• Chi-square test: The chi-square test, also known as, the pearson chi-square test or the chi-squared test, is used for categorical data. It assesses the independence of two variables or evaluates the fit of a theoretical distribution to a dataset. The chi-square test is appropriate for analyzing contingency tables or cross-tabulations. It can identify relationships between categorical variables or compare the observed distribution to a predicted distribution.

• ANOVA: Analysis of Variance (ANOVA) is a powerful test statistic, used for comparing multiple means across groups. It extends the t-test to more than two groups, allowing for the examination of the effects of multiple factors, or treatments.

Choosing the right test statistic depends on the nature of the data and the research question. Each test statistic has its strengths and limitations, and selecting the appropriate one ensures accurate and meaningful conclusions from hypothesis testing.

3\. Set the rejection region

The rejection region is the range of values that leads to rejecting the null hypothesis in favor of the alternative hypothesis. This step involves determining the criteria for accepting or rejecting the null hypothesis based on certain statistical indicators. To set the rejection region, we need to define three parameters: Alpha (𝜶), p-value, and critical value.

• Alpha (𝜶): Alpha (also known as significance level) is the probability of rejecting the null hypothesis when it is true. Commonly chosen values for alpha include 0.05 or 0.01, reflecting the acceptable level of risk in decision-making. For instance, if 𝜶 is set at 0.05, it implies a 5% risk of erroneously rejecting the null hypothesis.

• P-value: The p-value is the probability of obtaining the observed result (or a more extreme result), assuming that the null hypothesis is true. A low p-value suggests that the observed effect is unlikely to occur by random chance alone, providing evidence against the null hypothesis.

• Critical value: The critical value is the value of the test statistic that defines the boundary of the rejection region. It is the value that separates the rejection region from the acceptance region.

4\. Perform the test and draw a conclusion

The test statistic is calculated using the sample data, and the p-value is determined. The p-value is compared to the predetermined significance level (usually 0.05). If the p-value, is less than the significance level, the null hypothesis is rejected. If the null hypothesis is rejected, it implies that the observed effect is statistically significant and there is evidence to support the alternative hypothesis. On the other hand, if the null hypothesis is not rejected, it suggests that the observed effect is likely due to random chance, and there is insufficient evidence to support the alternative hypothesis.

| Note: Rejecting does not prove is true. It simply means the observed difference is unlikely due to chance. |
| --- |

Let us consider a scenario where you are analyzing the effectiveness of a new marketing campaign on product sales. The null hypothesis (H0) is that the marketing campaign, has no impact on sales, and any observed changes are due to random chance. The alternative hypothesis (H1) suggests that the marketing campaign does have a significant effect on sales.

After conducting a hypothesis test, suppose you calculate a p-value of 0.02, which falls below the chosen significance level, 0.05. In this case, you would reject the null hypothesis, indicating that the marketing campaign in truth, has a statistically significant impact on product sales.

This conclusion implies that the observed increase (or decrease) in sales cannot be attributed to random fluctuations alone but is likely a result of the marketing efforts. As a result, decision-makers can have confidence in allocating resources to continue or refine the marketing campaign based on this data-driven evidence.

[Covariance and correlation](#contents.xhtml#sc2_138a)

Covariance measures the linear relationship between two random variables. It captures the direction of that relationship, indicating whether they move together (positive) or in opposite directions (negative). The range of covariance extends across all real numbers, from negative infinity (-∞) to positive infinity (+∞).

*   Positive covariance: A direct relationship between variables. As one variable increases, the other tends to increase too, and vice versa.
*   Negative covariance: An inverse relationship between variables. When one variable increases, the other decreases, and vice versa.
*   Zero covariance: Suggests no linear relationship between the variables. Their changes are not consistently linked in any particular direction. However, it is crucial to acknowledge that this does not necessarily mean no relationship exists. The relationship might be non-linear or influenced by other factors not captured by the analysis.

The cov() function calculates the covariance between two vectors. It is important to note, that covariance provides insight into the direction of the relationship, but not the strength of the association. This is where correlation comes in, offering a standardized score ranging from -1 to +1 to quantify the relationship's strength.

Correlation measures the strength and direction of a linear relationship between two variables. This helps analysts identify whether changes in one variable are associated with changes in another. A correlation of -1 indicates perfect negative correlation (opposite movement), 0 represents no linear relationship, and +1 signifies perfect positive correlation (movement in the same direction). A value closer to -1 or +1 suggests a strong relationship, while values closer to 0 indicate a weaker or no connection. Recognizing these relationships is fundamental for making predictions and understanding the drivers behind observed patterns in the data. The cor() function calculates the correlation coefficient between two vectors.

Consider a dataset of Uber rides in a city. Each data point includes the distance traveled (in kilometers) and the corresponding duration of the ride (in minutes). A positive correlation between distance and time implies that, on average, longer distances are associated with longer ride durations.

For instance, a short-distance ride within the city center, covering 2 kilometers, might take around 10 minutes. On the other hand, a longer-distance ride from the suburbs to the airport, covering 30 kilometers, could take 45 minutes or more. The positive correlation indicates that the time it takes to complete a ride tends to increase, as the distance traveled increases. [Figure 9.1](#ch09.xhtml#fig9-1) shows the linear relationship between the distance and the time taken:

![](images/Figure9.1.png)

Figure 9.1: Linear relationship between distance and time

[Conclusion](#contents.xhtml#sc2_139a)

Statistics provides you the tools to summarize the key characteristics of datasets and identify patterns and trends. This statistical knowledge is crucial for effectively preparing data for machine learning models. Without a strong grasp of statistics, you risk feeding your models with poorly understood or misleading data, leading to inaccurate and unreliable results. While both probability and statistics play crucial roles in data science, they serve distinct purposes. Probability focuses on concepts like chance, likelihood, and randomness. It asks questions like What is the probability of this event happening? Statistics is concerned with collecting, analyzing, interpreting, and drawing conclusions from this data. It raises questions like, What does this data tell us about the population it represents? In the next chapter, you will be introduced to ML concepts.

Join our book’s Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/fm1.png)

# [CHAPTER 10Introducing ML](#contents.xhtml#ch10a)

[Introduction](#contents.xhtml#sc2_140a)

Contrary to popular belief, the role of a data scientist, extends beyond merely developing and tuning ML models. In reality, a considerable part of their work, involves tasks that precede model development, such as understanding business challenges and converting them into data-driven problems. Data scientists, spend a significant amount of time, collecting, cleansing, and transforming raw data into a format conducive to analysis. This crucial preparatory work sets the foundation for effective model building and ensures the insights generated are relevant and actionable. Determining, whether ML is a suitable approach for tackling a particular problem, requires careful consideration. To help with this process, we will outline a step-by-step guide for evaluating the feasibility of ML.

[Structure](#contents.xhtml#sc2_141a)

In this chapter, we will understand the following topics:

*   Foundation of ML
*   Framing a ML problem
*   Types of ML systems 
    *   Supervised learning
    *   Unsupervised learning
    *   Reinforcement learning
    *   Generative AI
*   Major challenges of ML algorithms

[Objectives](#contents.xhtml#sc2_142a)

In this chapter, you will understand, the fundamental ML concepts. In the beginning, you will explore defining and determining whether a problem justifies a solution through ML. We will clarify the difference between addressing problems using ML algorithms and traditional approaches. Subsequently, the book will guide you in selecting the most suitable ML model for the business requirement, providing insights into various ML systems. Finally, it will bring to attention, the fundamental challenges inherent in ML algorithms, such that you can effectively navigate, and tackle them during the implementation process.

[Foundations of ML](#contents.xhtml#sc2_143a)

ML has revolutionized various aspects of our lives by enabling technologies such as translation applications and self-driving cars. ML provides a versatile approach to problem-solving, question-answering, and content/image creation. It enables systems to predict customer churn, estimate trip durations, recommend movies, auto-complete sentences, summarize books, or generate images.

ML is the process of training models using historical data to make valuable predictions or generate content. A model is a mathematical representation or specification of the relationship, that exists, between various variables.

Consider a scenario where the task is to develop a system for fraud detection in financial transactions. In a traditional approach, one might rely on rule-based systems and predefined criteria to flag potentially fraudulent activities. This conventional method would demand, the formulation of complex rules derived from historical fraud patterns, involving an in-depth understanding of various fraud indicators. The process could be time-consuming, and there is a risk of overlooking emerging fraud tactics that might not align with the preconceived rules.

On the other hand, adopting a ML approach involves training a model with a vast dataset containing various transaction features and their corresponding fraud labels. The ML model learns patterns and anomalies from the data, allowing it to adapt to new and previously unseen fraud patterns. Unlike the static and rule-bound nature of traditional methods, the ML model becomes adept at recognizing new fraud patterns that may not have been explicitly programmed.

When presented with new transactions, the ML model can autonomously assess the likelihood of fraud based on the learned patterns. This autonomy offers a more dynamic and adaptable solution, as the model can adjust to emerging fraud trends without requiring manual intervention to update predefined rules.

ML proves to be highly beneficial in various scenarios:

*   Problems requiring extensive fine-tuning or complex rule sets

In situations, where existing solutions involve lengthy lists of rules, ML algorithms offer a streamlined alternative. ML consolidates complex rule sets into efficient models, improving code clarity and performance.

*   Problems that involve fluctuating environments

ML systems demonstrate adaptability to changing data and environments. Their capacity to learn from new information lets them adjust and evolve, making them particularly valuable in scenarios where conditions are subject to variation.

*   Complex problems with no satisfactory traditional solution

ML excels in tackling complex problems where conventional methods struggle to provide effective solutions.

[Framing a ML problem](#contents.xhtml#sc2_144a)

ML problem framing is a critical step in the development, of any successful ML project. It involves analyzing a problem to identify the key elements to be addressed to solve it effectively. This process helps determine the technical feasibility of a project and provides a clear set of goals and success criteria. In the context of ML, problem framing is important in particular to help ensure that the solution developed is tailored to the specific needs of the problem at hand.

The first step in problem framing for ML is determining, whether ML is the right approach for solving a particular problem. This involves evaluating the problem's characteristics and determining whether ML can effectively address the issue. If ML is appropriate, the second step is to frame the problem in ML terms. This entails breaking down the problem into parts, identifying the relevant features and labels, and defining the objective function that ML algorithms seek to optimize.

Let us closely look at our methodology for comprehending and defining the problem.

*   Clearly define the objective: Start with clearly defining your objective, in simple language, without any references to ML. The objective should answer the question, What do I want to achieve?

The below table shows a few examples:

| Application || Objective |
| --- | --- |
| Fitness tracker || Estimate calories burned during different activities and provide personalized fitness insights |
| Music streaming app || Generate playlists based on user preferences |
| Agriculture app || Optimize irrigation schedules and predict potential crop diseases |
| Sleep tracking app || Enhance sleep quality by providing personalized suggestions |
| Personal finance || Provide proactive financial advice by predicting potential expenses and suggesting budget adjustments |
| Job search app || Match job seekers with relevant job openings |
| Travel app || Enhance the travel app by predicting accurate travel times between locations |

Table 10.1: Define business objectives clearly for various applications

While some perceive ML as a versatile tool, applicable to all types of business problems, the reality is that ML is a specialized tool designed for a specific problem. It is essential to avoid implementing a sophisticated ML solution when a simpler, non-ML approach suffices.

To ensure, that ML is the optimal approach, thoroughly evaluate your existing non-ML solution's performance before investing in an ML alternative. Consider these questions to determine if an ML solution is necessary:

*   Quantify expected improvement: Can an ML solution deliver a significant impact compared to your existing (optimized) non-ML solution? Smaller gains might suggest sticking with the current approach.
*   Cost comparison: Examine the expenses associated with the ML solution, both short and long-term. ML implementations may incur significant costs in terms of computing resources and time.
*   Cost-effectiveness justification: In large systems, even small improvements from ML can translate to significant benefits, offsetting implementation and maintenance costs.
*   Maintenance considerations: ML models usually require dedicated personnel for monitoring, retraining, and potential debugging. Evaluate if your team has the resources and expertise for long-term maintenance.

The quality of the data used for training plays a crucial role in determining the accuracy and effectiveness of the model. To create a robust and reliable model, the data should possess certain key characteristics:

*   The more relevant and valuable examples within your dataset, the more robust your model becomes. A larger dataset provides a greater scope for the model to generalize and improve its prediction capabilities.
*   Data collection processes should be sound, and efforts should be made to minimize errors during data entry, storage, and processing. A consistent and reliable dataset allows the model to learn meaningful patterns and reduce the risk of bias.
*   While minor labeling errors are inevitable in large datasets, a high rate of incorrect labels can severely compromise the model's performance. Ensuring accurate labeling is critical to building a model that produces trustworthy predictions.
*   The dataset should mirror the real-world scenario being modeled as closely as possible. This means capturing relevant events, user behaviors, and other phenomena occurring in the actual environment. By doing so, the model can adapt to changes and variations in the real world, resulting in improved performance when making predictions.

Fulfilling these data requirements is indispensable for creating a powerful and dependable predictive ML model.

For a model to generate accurate predictions, the features within your dataset must possess significant predictive power. The degree of correlation between a feature and its corresponding label directly influences its capability to predict accurately. A higher correlation indicates a greater likelihood of the feature being a reliable predictor for the given label.

In the context of, healthcare patient re-admission prediction, certain features exhibit varying degrees of predictive power. Features such as previous\_hospitalizations, medication\_compliance, and age are likely to hold high predictive power. The number of previous hospitalizations provides insight into the patient's health history, medication\_compliance reflects adherence to prescribed treatments, and age can be a crucial factor in predicting re-admission risks. On the other hand, features like patient\_gender and day\_of\_week may have lower predictive power. 

However, it is essential to recognize that the predictive power of features can be context-dependent. In specific sub-domains of healthcare, certain features that may generally have lower predictive power could become more influential. Thus, understanding the dynamic nature of feature relevance within different contexts or domains is crucial for building accurate and contextually relevant predictive models.

Frame a problem in ML terms

Now, let us align the goal of the ML model with the business objectives outlined in Table 10.1.

| Application || Objective || ML model goal |
| --- | --- | --- |
| Fitness tracker || Estimate calories burned during different activities and provide personalized fitness insights || Develop a ML model to analyze user's exercise data, incorporating factors such as heart rate, duration, and type of activity, to accurately estimate calories burned and offer personalized fitness recommendations. |
| Music streaming app || Generate playlists based on user preferences || Implement a recommendation system to analyze user listening behavior, preferences, and contextual cues, ensuring the generation of dynamic playlists that align with users' evolving preferences. |
| Agriculture app || Optimize irrigation schedules and predict potential crop diseases || Develop ML models to analyze environmental data, including weather patterns and soil conditions, to optimize irrigation schedules. Additionally, create predictive models for identifying potential crop diseases using historical and real-time data. |
| Sleep tracking app || Enhance sleep quality by providing personalized suggestions || Analyze sleep patterns, environmental conditions, and user feedback to provide personalized recommendations for improving sleep quality, such as adjusting bedtime routines or optimizing sleep environments. |
| Personal Finance || Provide proactive financial advice by predicting potential expenses and suggesting budget adjustments. || Analyze users' financial behavior, identify patterns, and forecast potential expenses. Provide proactive financial advice by suggesting budget adjustments and offering insights into future financial trends. |
| Job search app || Match job seekers with relevant job openings || Implement a ML algorithm to accurately match job seekers with relevant job openings based on their skills, experience, preferences, and other relevant factors, thereby enhancing the efficiency and effectiveness of the job search process. |
| Travel app || Enhance the travel app by predicting accurate travel times between locations || Implement a ML model that utilizes historical travel data, real-time traffic information, and other relevant factors to predict travel times between specified locations. |

Table 10.2: Define the goals in ML terms

Deciding, the type of ML model to use is not a one-size-fits-all situation. The model's output needs to address your desired outcome. That is why the first crucial question is: What kind of output is necessary to address my problem effectively?

If the objective involves classification or numeric prediction, predictive ML is likely the suitable choice. On the other hand, if the task involves, generating new content, translating languages, or creating human-like dialogue, the apt choice would be generative AI.

Next, you need to define the key performance indicators (KPIs) that will measure the success of your ML implementation. These KPIs should align with your project's objectives and convey what matters most, such as enhancing user experience, boosting engagement, or fostering appropriate actions. Examples of success metrics include:

*   Engagement: Track the amount of time, users spend interacting with the platform, the number of clicks on recommended items, or the frequency of returned visits.
*   Conversion rates: Monitor the proportion of users who take a desired action, such as purchasing a product, signing up for a service, or completing a task.
*   Time savings: Evaluate the extent to which, the ML implementation reduces the time users spend searching for relevant content or solving a problem.
*   Cost efficiency: Calculate the cost savings achieved by leveraging ML technologies. This assessment may require a comparison of the expenditures related to implementing the ML system against the costs associated with conventional manual processes.

It is important to note that success metrics diverge from the model's evaluation metrics such as accuracy, precision, recall, or AUC. While evaluation metrics assess the model's performance, success metrics measure the impact of the ML implementation on achieving the project's goals and improving the overall user experience.

[Types of ML systems](#contents.xhtml#sc2_145a)

ML systems can be categorized based on their learning methods, which determine how they make predictions or generate content:

*   Supervised learning
*   Unsupervised learning
*   Reinforcement learning
*   Generative AI

[Supervised learning](#contents.xhtml#sc3_146a)

In supervised learning, the algorithm is trained on a dataset, containing both, input data and corresponding output labels. The goal is for the algorithm to learn the relationship between the input data and the correct output labels, to make accurate predictions on new, unseen data. Supervised learning is supervised because a human provides the algorithm with labeled data, guiding it toward the correct solutions. 

Two types of supervised learning include regression and classification tasks.

Regression

A regression model predicts numeric values based on input features. The primary goal of a regression model is to establish a relationship between the input features and the target variable, allowing it to make accurate predictions of numeric outcomes. For instance, predicting the price of a house ([Figure 10.1](#ch10.xhtml#fig10-1)), based on a set of features (location, square footage, number of bedrooms, etc.) known as predictors. A diverse dataset containing numerous examples of houses is essential to train the model for this task. This dataset should include both the predictors (features) of the houses, and their corresponding labels (i.e., their prices).

![](images/Figure10.1.png)

Figure 10.1: An example of a regression task: house price prediction based on house size

The table below illustrates a few more regression tasks.

| Objective || Potential input variables || Predicted numerical outcome |
| --- | --- | --- |
| Stock price prediction || Historical stock prices, trading volume, economic indicators, company financials, and news sentiment. || The price of a specific stock. |
| --- | --- | --- |
| Energy consumption forecast || Historical energy usage, temperature, day of the week, and time of day. || Energy consumption in kilowatt-hours. |
| Crop yield estimation || Soil quality, weather conditions, irrigation levels, and historical crop yield data. || Crop yield in bushels.  |
| Website traffic prediction || Historical website traffic, marketing campaign data, and seasonal trends. || Expected number of website visits. |
| Air quality forecast || Air pollution levels, meteorological data, and historical air quality indices. || Air quality index for a specific area. |

Table 10.3: Examples of regression tasks

Classification

Classification models, a subset of supervised learning algorithms, predict the likelihood of an instance being part of a specific category or class. In contrast to regression models, which produce numerical outputs, classification models generate values indicating whether an item falls into a particular category.

Classification models fall into two categories: binary classification and multiclass classification. In binary classification, models generate a value from a class with only two possibilities. For instance, a model may predict, fraudulent or non-fraudulent transactions as illustrated in [Figure 10.2](#ch10.xhtml#fig10-2). On the other hand, multiclass classification involves predicting from multiple categories. An example is a model classifying weather conditions into categories, such as sunny, cloudy, rainy, or snowy.

![](images/Figure10.2.png)

Figure 10.2: An example of a classification task: predicting a transaction is fraudulent or not

The table below shows a few scenarios of classification tasks:

| Objective || Potential input variables || Predicted Categorical Outcome |
| --- | --- | --- |
| Customer churn prediction || Customer demographics, purchase history, customer service interactions, and feedback. || Churn (Yes/No) |
| Email spam classification || Email content, sender information, and historical spam data. || Spam (Yes/No) |
| Loan approval prediction || Applicant's credit score, income, debt-to-income ratio, employment status, and loan amount applied for. || Loan approved (Yes/No) |
| Customer segment identification || Purchase history, demographics, and website interactions. || Customer segment category: e.g., Premium, Regular, New |
| Customer subscription || Customer activity, usage patterns, and engagement with subscription-related features. || Subscribed (Yes/No) |

Table 10.4: Examples of classification tasks

[Unsupervised learning](#contents.xhtml#sc3_147a)

In unsupervised learning, the training data lacks explicit labels, requiring the model to learn patterns and structures without explicit guidance. In contrast to supervised learning, there is no labeled output to guide the model's learning process. This approach is particularly useful when exploring and understanding the inherent complexities and relationships within datasets where labeled examples may be unavailable or impractical to obtain.

A frequently used technique in unsupervised learning is clustering, where the model identifies natural groupings within the data by finding data points that share common characteristics or patterns. [Figure 10.3](#ch10.xhtml#fig10-3) shows an illustration of clustering:

![](images/Figure10.3.png)

Figure 10.3: Clustering-unsupervised learning

In addition to clustering, there are several other unsupervised learning tasks. One such task is anomaly detection, which involves identifying data points, that are significantly different, from the majority of the data. Anomaly detection can be useful in various applications, such as fraud detection, network intrusion detection, and manufacturing defect identification. Another unsupervised learning task is dimensionality reduction, which involves reducing the number of features in a dataset while preserving the most important information. Dimensionality reduction can also be useful for visualizing high-dimensional data.

[Reinforcement learning](#contents.xhtml#sc3_148a)

Reinforcement learning (RL) is a branch of ML where algorithms learn through interaction with an environment. RL models learn by exploring, taking action, and receiving feedback as rewards or penalties. The goal of RL is for the agent to discover a policy, which is a set of rules, that dictates the best actions to take in different situations to maximize the cumulative reward.

Reinforcement learning has been successfully applied to various tasks, such as training robots to perform manipulation tasks, like grasping and pouring liquids and navigating through unknown environments. It has also been used in recommending products, or content based on-user interaction, and in games like Poker to develop AI agents that can play at a professional level.

[Generative AI](#contents.xhtml#sc3_149a)

Generative AI models are deep learning algorithms that can create a wide range of content such as images, music, essays, and even videos by leveraging user input. One of the key advantages of generative AI is its ability to handle a variety of inputs and outputs. For instance, a model can take a text and image as input and generate a video as output, or take an image as input and generate a descriptive text caption.

Generative AI applications leverage foundational models, extensively trained on vast amounts of diverse data. An example of such foundational models is large language models (LLMs), specifically trained to process and generate textual-based content. They can efficiently execute a wide range of downstream tasks, such as question-answering, summarization, and open-ended content generation. LLMs can help businesses analyze data and automate their language-related tasks like report generation. This, not only saves valuable time and resources but also enhances accuracy and efficiency. Additionally, there are multi-modal foundation models, trained on images, software codes, or videos.

[Major challenges of ML algorithms](#contents.xhtml#sc2_150a)

ML algorithms have the potential to be highly effective, but their success depends on one essential factor: high-quality data. However, getting sufficient, accurate, and relevant data can be a hurdle for developers, making it challenging to create reliable and efficient ML models. Let us look into some of the major challenges:

*   Inadequate amount of data

One of the fundamental requirements for training ML models is a substantial amount of data. Insufficient data can hinder the model's ability to learn complex patterns.

Solution: You can use techniques like data augmentation, or generate synthetic data to enhance the quantity and diversity of available data.

*   Low-quality data

Low-quality data can significantly undermine the performance of ML algorithms. Noisy, missing, or erroneous data can lead to biased models that fail to capture the underlying patterns in the data. Models trained on low-quality data may produce inaccurate and unreliable predictions.

Solution: Implement robust data preprocessing techniques such as cleaning, filtering, and imputation, to enhance data quality. Conduct thorough exploratory data analysis (EDA) to identify and address anomalies and outliers.

*   Insignificant features

Features that do not contribute to the prediction or outcome can dilute the model's performance. Including such features in the training data can introduce noise and complexity.

Solution: Perform feature selection or extraction techniques to identify and retain only the most relevant features.

*   Biased training data

If the training data does not accurately reflect the real-world distribution, of the data, the model may not generalize well to new, unseen data. Bias in the training set can lead to biased predictions and decisions.

Solution: Consistently review and refresh training datasets to ensure they remain representative, of the application domain.

*   Underfitting

Underfitting occurs when a model is too simplistic to capture the underlying patterns in the training data. It results in poor performance as the model fails to learn the complexities inherent in the dataset.

Solution: You can use more advanced algorithms, or add more significant features to the dataset.

*   Overfitting

Overfitting occurs when a model is excessively complex, capturing noise and irrelevant details from the training data. This leads to a lack of generalization, where the model performs well on the training set but poorly on new, unseen data.

Solution: Address overfitting by simplifying the model, using regularization techniques, or increasing the size and diversity of the training dataset.

[Conclusion](#contents.xhtml#sc2_151a)

ML is a rapidly growing field that has the potential to transform numerous industries and revolutionize the way we live and work. In this chapter, we have looked into the fundamental building blocks of ML, explored how to frame an ML problem effectively, and understood the different types of ML systems available. Furthermore, we have also checked the major challenges of ML algorithms such as underfitting, overfitting, and data quality concerns. In the next chapter, we will understand, how to implement different ML algorithms in R.

Join our book’s Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/fm1.png)

# [CHAPTER 11Training Machine Learning Models](#contents.xhtml#ch11a)

[Introduction](#contents.xhtml#sc2_152a)

Training effective ML models is a core component, of the broader machine learning lifecycle. This chapter will provide an overview of several fundamental modeling techniques and concepts. We will begin by exploring linear regression, a widely used method for modeling the relationship between a dependent variable and one or more independent variables. Building upon this, we will understand logistic regression, used for binary classification tasks that estimate the probability of a binary outcome. Moving beyond linear models, the discussion will shift to decision trees, which recursively partition the feature space into regions, to capture complex and non-linear relationships. However, the power of these models also comes with the risk of overfitting, underscoring the importance of understanding the bias-variance tradeoff and its implications for model performance. A solid understanding of these essential ML concepts will help you to understand the tradeoffs and leverage the strengths of each approach effectively.

[Structure](#contents.xhtml#sc2_153a)

This chapter will encompass the following topics:

*   Machine learning lifecycle
*   Linear regression 
    *   Splitting data
    *   Evaluation metrics for regression
    *   Predicting ETA using linear regression
*   Logistic regression 
    *   Likelihood function for logistic regression
    *   Evaluation metrics for classification
    *   Predicting loan defaults using logistic regression
    *   Limitations of linear models
*   Decision trees
*   Bias-variance tradeoff
*   Clustering 
    *   K-means clustering

[Objectives](#contents.xhtml#sc2_154a)

This chapter covers several key topics related to model training and evaluation. First, the fundamentals of linear and logistic regression will be discussed, highlighting their use cases and underlying mathematical principles. Next, we will discuss decision trees and how they can be leveraged to tackle various ML problems. The concept of the bias-variance tradeoff will be introduced, explaining how it impacts model performance and the importance of finding the right balance during the training process. Finally, we will look into the unsupervised learning technique of k-means clustering, and understand how to use it to uncover hidden patterns and structures within data. Throughout the chapter, practical examples and real-world applications will be provided to reinforce the understanding of these fundamental ML models and techniques.

[Machine learning lifecycle](#contents.xhtml#sc2_155a)

Let us get started with understanding various phases of the ML lifecycle. [Figure 11.1](#ch11.xhtml#fig11-1) illustrates the ML lifecycle phases.

![](images/Figure11.1.png)

Figure 11.1: ML lifecycle

The phases are explained in detail below.

*   Identifying the business goal: The first step in any machine learning project is to identify the problem you are trying to solve. Clearly define the business problem you aim to solve and quantify the expected benefits. Establish measurable goals and success criteria to ensure the ML project aligns with the organization's overall strategy.
*   Framing ML problem: Transform the business problem into a machine learning problem by identifying the inputs (features) and the desired outputs (target variable). Determine the error metrics to evaluate the model's success.
*   Collecting data: The next step is to collect and gather data related to the problem. This can involve collecting data from various sources, such as databases, APIs, files, and sensors.
*   Preprocessing data: After collecting the data, it has to be processed, to prepare it for ML. This can involve cleaning the data, handling missing values, normalizing the data, and transforming the data into a suitable format. Preprocessing is a critical step, as it can significantly impact the accuracy of the ML model.
*   Engineering features: Feature engineering is the process of creating new features from existing data that can help improve the performance of the ML model. This can involve creating derived features, combining existing features, and extracting relevant information from the data.
*   Training ML model and evaluate: Select an appropriate algorithm and train the model on the training dataset. Evaluate the model's performance on the testing dataset, using metrics relevant to the problem, and generalization capabilities.
*   Model deployment: After evaluating the model, you can deploy it to production, where it is used to generate value for the business. Deployment can involve integrating the model with existing systems, creating API endpoints, monitoring the model's performance, and updating as necessary.
*   Monitoring: It is essential to monitor the ML model's performance over time, to ensure it remains accurate and relevant. Establish a monitoring system to ensure the model retains its intended performance level. Quickly detect and address any degradations or anomalies to sustain the model's accuracy and relevance.

[Linear regression](#contents.xhtml#sc2_156a)

Linear regression is a statistical technique for predicting a continuous outcome variable. Despite its longevity, linear regression remains a popular and effective method in modern data analysis.

The core idea behind linear regression is to construct a linear model that captures the relationship between a dependent variable (Y) and one or more independent variables (X). The model predicts the expected value of Y given X by calculating a weighted sum of the input features, plus a constant term known as the bias or intercept. Mathematically, this can be represented as:

![](images/eq-12.jpg)

where:

![](images/eq-22.jpg)is the predicted outcome variable

![](images/eq-32.jpg)is the bias term, representing the baseline value of Y when all X variables are equal to zero

![](images/eq-4.jpg)is the weight associated with x1, which determines the change in Y for a unit change in x1 while holding other X variables constant

x1 is a single feature or input variable

To train a ML model, we determine optimal values for the weights and bias using labeled examples. In supervised learning, a ML algorithm builds a model by analyzing numerous examples and identifying a model that minimizes the loss. Loss is a penalty for inaccurate predictions, represented by a numerical value indicating the degree of error in a single example. The ideal scenario, is for the model's prediction to be perfect, resulting in a loss of 0. However, if the prediction is imperfect, the loss will be greater. The objective of training a model is to find a set of weights and biases, resulting in low loss across all examples.

Our goal is to obtain coefficient estimates and to ensure that the linear model fits the available data well. We can express the prediction for Y based on the value of X as:

![](images/eq-5.jpg)

The residual (ei) is the difference between the observed response value (yi) and the predicted response value (![](images/eq-7.jpg).). The residual (ei) is calculated as ![](images/equation.jpg).

In linear regression, the cost function is typically defined as the mean squared error (MSE). MSE measures the average squared difference between the predicted and actual values. 

![](images/eq-6.jpg)

Minimizing the MSE helps to ensure that the linear model accurately captures the underlying patterns in the data and provides reasonable predictions for new observations.

The linear regression model is based on several assumptions that must be met to ensure the validity of the model's predictions. Here are some of the key assumptions of linear regression:

*   The relationship between the independent variable(s) and the dependent variable is assumed to be linear.
*   Observations must be independent of each other.
*   Variance of the residuals is assumed to be constant across all levels of the independent variable(s). Heteroscedasticity occurs when the variability of the error term changes across different levels of an independent variable.
*   Residuals are assumed to be normally distributed.
*   Independent variables should not be highly correlated with each other. High degrees of correlation between variables can create challenges during the model-fitting process and interpretation of results.
*   Residuals should not be correlated with each other over time.

[Splitting data](#contents.xhtml#sc3_157a)

We typically split the dataset into two subsets, a training and a test set. The training set is used to train the model. It contains a significant portion of the data, allowing the model to learn patterns and relationships within the data. On the other hand, the test set is used to evaluate the model's performance. The below [Figure 11.2](#ch11.xhtml#fig11-2) shows the data splitting into two sets:

![](images/Figure11.2.png)

Figure 11.2: Splitting data into training and test dataset

Now, let us discuss some best practices, for splitting the data into training and test datasets.

*   First, ensure your test set is large enough to produce statistically significant results. You want to avoid having a test set that is too small, as it may not accurately reflect the true performance of your model. As a rule of thumb, a common split ratio is 80% training and 20% testing, but this can vary based on the size and complexity of the dataset.
*   Second, it is crucial to avoid picking a test set with different characteristics, than the training set. This is because the test set serves as a proxy for new data, and the goal is to create a model that generalizes well to new, unseen data.
*   Third, never train the model on the test data, or use any information from the test set to influence model training. Ensure the test set remains completely separate from the training set throughout the model-building process. Data leakage, where information from the test set inadvertently influences the model, can lead to overfitting and misleading evaluation metrics.

During the training phase, a machine learning algorithm learns patterns in the training data by adjusting the model parameters. However, the model can overfit the training data, meaning, it performs well on the training data but poorly on new, unseen data. To prevent this, we can use a validation set, to evaluate the model's performance during the training process and make adjustments as needed. This ensures the model not just memorizes the training data, but learns useful patterns that generalize to new data. The following [Figure 11.3](#ch11.xhtml#fig11-3) shows the splitting of data into three subsets:

![](images/Figure11.3.png)

Figure 11.3: Splitting data into training, validation, and test dataset

A typical data partition workflow includes the following steps:

1.  Split the initial dataset into three subsets; training, validation, and testing. Commonly, these splits are 80-10-10% or 70-15-15%.
2.  Train the model on the training set and evaluate its performance on the validation set.
3.  Adjust any aspect of the model, add or remove features, apply regularization techniques, or even build a completely new model. After making modifications, return to step 2 and continue iterating until satisfactory performance is achieved.
4.  Once the desired performance has been reached, select the best-performing model based on the validation set metric(s), which will then, be evaluated on the held-out test set to assess its true generalization capability. Remember, do not tweak the model further based on the test set, as doing so could result in biased performance estimates.

The following [Figure 11.4](#ch11.xhtml#fig11-4) shows the data partition workflow:

![](images/Figure11.4.png)

Figure 11.4: Data partition workflow

[Evaluation metrics for regression](#contents.xhtml#sc3_158a)

Some of the most commonly used evaluation metrics for regression are:

*   Mean Absolute Error (MAE): MAE measures the average absolute difference between the actual and predicted values. It provides a straightforward interpretation, where lower values indicate better model performance.
*   Mean Squared Error (MSE): It calculates the average of the squared differences between actual and predicted values. Squaring the errors penalizes larger errors more significantly, making MSE sensitive to outliers.
*   Root Mean Squared Error (RMSE): It is the square root of MSE, providing an interpretable measure in the same units as the target variable. Like MSE, RMSE penalizes larger errors but is more interpretable due to its scale.
*   Root Mean Squared Logarithmic Error (RMSLE): It measures the RMSE of the logarithm of the predicted and actual values. It is handy when the target variable spans several orders of magnitude and you care about relative errors rather than absolute errors.
*   Mean Absolute Percentage Error (MAPE): It calculates the average percentage difference between the actual and predicted values relative to the actual values. It provides a percentage representation of the error, making it easy to interpret and compare across different datasets.

These metrics are used to evaluate the performance of regression models and help determine which model best fits the data. Each metric has its strengths and weaknesses, and the choice of metric depends on the specific problem and desired outcomes.

[Predicting ETA using linear regression](#contents.xhtml#sc3_159a)

Using an example of a ride-sharing application, accurate forecasting of arrival times, or ETA is an essential component, to create a satisfying customer experience. Reliable ETA predictions play a pivotal role in various aspects of the service, such as calculating fares, matching riders with drivers, and planning deliveries. Customers rely on accurate ETA to make informed decisions and manage their expectations, and the platform's success heavily depends on maintaining user satisfaction and trust. Inaccurate or unreliable ETA predictions can lead to frustration and dissatisfaction among users, potentially damaging the platform's reputation and negatively impacting its overall performance. 

The following commands read a dataset, and visualize the linear relationship between distance traveled and time taken for a cab service. The dataset, cab\_data.csv, contains information on the distance traveled and the corresponding time taken for each trip.

*   \# Load the required libraries
*   library(dplyr)
*   library(ggplot2)
*   library(ModelMetrics)
*   
*   \# Read the dataset
*   cab\_data <- read.csv("cab\_data.csv")
*   
*   \# Visualize the linear relationship between distance and time
*   ggplot(cab\_data, aes(x = Distance, y = Time\_Taken)) +
*    geom\_point(col = "steelblue4") +
*    labs(title = "Linear Relationship between Distance and Time",
*    x = "Distance (kms)",
*    y = "Time Taken (minutes)") +
*    theme\_bw()

[Figure 11.5](#ch11.xhtml#fig11-5) shows the linear relationship between the two variables. It indicates, that as the distance traveled increases, the time taken also increases proportionally:

![](images/Figure11.5.png)

Figure 11.5: Relationship between distance and time

Next, let us split the dataset into training and testing subsets.

*   \# Split data into train and test
*   set.seed(123)
*   rows=seq(1,nrow(cab\_data),1)
*   trainRows=sample(rows,(80\*nrow(cab\_data))/100)
*   train = cab\_data\[trainRows,\] 
*   test = cab\_data\[-trainRows,\]

The seed is set to ensure reproducibility, and the rows are sampled randomly to create the training and testing sets. Specifically, 80% of the rows are allocated for training and the remaining 20% for testing.

The lm() command is used to train a linear regression model. The following code trains a model to predict the Time\_Taken variable based on the Distance variable.

*   \# Train a linear Regression Model
*   lm\_time <- lm(Time\_Taken ~ Distance, data = train)

The formula Time\_Taken ~ Distance specifies that the Time\_Taken is the response variable and Distance is the predictor variable. The data argument specifies the dataset used for training.

The resulting model, stored in the lm\_time variable, can then be used to make predictions on new, unseen data. The summary output provides valuable information about the linear regression model's performance and the relationship between the response variable Time\_Taken and the predictor variable Distance.

*   \# Summary of the model
*   summary(lm\_time)
*   
*   \## Call:
*   \## lm(formula = Time\_Taken ~ Distance, data = train)
*   ##
*   \## Residuals:
*   \## Min 1Q Median 3Q Max 
*   ##-14.110 -2.708 -0.064 2.734 14.646 
*   ##
*   \## Coefficients:
*   \## Estimate Std. Error t value Pr(>|t|) 
*   \## (Intercept) 6.49814 0.71935 9.033 <2e-16 \*\*\*
*   \## Distance 1.37346 0.06857 20.030 <2e-16 \*\*\*
*   \## ---
*   \## Signif. codes: 0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1
*   ##
*   \## Residual standard error: 4.173 on 395 degrees of freedom
*   \## Multiple R-squared: 0.5039, Adjusted R-squared: 0.5026 
*   \## F-statistic: 401.2 on 1 and 395 DF, p-value: < 2.2e-16

The Residuals represent the differences between the observed values of the dependent variable (Time\_Taken) and the values predicted by the model. The summary shows the minimum first quartile, median third quartile, and maximum values of the residuals.

The coefficients estimate the intercept (6.49814) and the slope (1.37346) of the linear equation, indicating that, on average, the time taken increases by approximately 1.37 minutes for every additional kilometer traveled.

The p-values for both coefficients are highly significant, suggesting a strong linear relationship between distance and time.

Residual standard error represents the standard deviation of the residuals, which is approximately 4.173. It measures the typical difference between the observed and predicted values of Time\_Taken.

The coefficient of determination (R2) quantifies the proportion of variance in the dependent variable that is explained by the independent variables in a regression model, normalized against the baseline variance of the model, which is essentially the variance of the mean.

![](images/eq-8.jpg)

An R2 value of 1 indicates that the model captures 100% of the variance, while a negative R2 suggests that the model performs worse than a simplistic model that merely follows the mean of the data.

Multiple R-squared value (0.5039) indicates, that approximately 50.39% of the variability in Time\_Taken is explained by the linear relationship with Distance. The Adjusted R-squared value (0.5026) adjusts the R2value based on the number of predictors in the model, providing a more accurate measure of model fit.

The F-statistic (401.2) assesses the overall significance of the model. In this case, the F-statistic has a very low p-value (< 2.2e-16), indicating that the overall model is highly significant in predicting Time\_Taken.

Let us now use the predict() function to generate predictions on the test dataset using the linear regression model lm\_time that was previously fitted to the training data. The predicted values are stored in the predicted\_values object.

*   \# Predict on test set
*   predicted\_values <- predict(lm\_time, newdata = test)

Then, a new data frame compare\_df is created, containing two columns: Actual and Predicted. The Actual column represents the true values of the response variable Time\_Taken from the test dataset, and the Predicted column contains the corresponding predicted values obtained from the linear regression model.

*   #Create a dataframe with Actuals and Predicted values
*   compare\_df <- data.frame(Actual = test$Time\_Taken, Predicted = predicted\_values)
*   
*   #Root Mean Squared Error (RMSE)
*   rmse(compare\_df$Actual,compare\_df$Predicted)
*   \## 3.974987
*   
*   #Mean Absolute Error (MAE)
*   mae(compare\_df$Actual,compare\_df$Predicted)
*   \## 3.289056

In this case, the RMSE is 3.975, suggesting that, on average, the model's predictions deviate from the actual values by around 3.975 units of Time\_Taken. MAE provides a more interpretable measure of error compared to RMSE. The MAE value of 3.29 indicates that the model's predictions, on average, differ from the actual values by about 3.29 units.

[Logistic regression](#contents.xhtml#sc2_160a)

Logistic regression is highly efficient for generating probability estimates as outputs. These probabilities can be used in the following two ways:

*   Directly utilizing the returned probability without any conversion.
*   Converting the probability into a binary category based on a specified threshold.

In logistic regression, we model the relationship between the independent variables and the logged odds of the dependent variable being in a particular category. Odds are defined as, the ratio of the probability of the event happening to not happening.

To calculate the probability of the dependent variable, we use the odds. Given is a set of input features x1, x2,x3,….xn, the log of the odds (ln(p/1-p)), often referred to as the logit function, can be represented linearly using the following expression:

![](images/eq-9.jpg)

By exponentiating both sides of the equation, we obtain the odds themselves:

![](images/eq-10.jpg)

Solving for P, we derive the probability estimation by logistic regression:

![](images/eq-111.jpg)

Example:

Consider a scenario where a bank wants to predict the likelihood of a customer defaulting on a loan based on their credit score, debt-to-income ratio, and age. The logistic regression model would estimate the probability of default based on these input variables.

![](images/eq-121.jpg)

Where,![](images/eq-41.jpg), ![](images/eq.jpg), ![](images/eq-13.jpg)and are the coefficients estimated during model training.

The coefficients ![](images/eq-41.jpg), ![](images/eq.jpg), ![](images/eq-13.jpg)and represent the change in the log odds of default for a one-unit increase in the respective input variable. Positive coefficients indicate that an increase in the variable leads to higher odds of default. This means that the higher value of the input variable is associated with a higher likelihood of the event occurring. Conversely, when the coefficient associated with an input variable is negative, an increase in the value of that variable leads to a decrease in the odds of the event occurring. This indicates that the higher value of the input variable is associated with a lower likelihood of the event occurring.

The figure below shows the logistic function curve to explain the probability of default to credit score.

![](images/Figure11.6.png)

Figure 11.6: Logistic regression model for predicting probability of default

[Likelihood function for logistic regression](#contents.xhtml#sc3_161a)

In logistic regression, the likelihood function is used to estimate the model parameters (coefficients) that maximize the probability of observing the training data given the model. Since logistic regression predicts probabilities, it is particularly suitable for modeling binary data using the likelihood function.

Where, p(xi) is the probability of the positive class (in our case, Default) given the input features, xi. yi is the class label for the ith data point and n is the total number of data points.

The likelihood function measures the likelihood of observing the given classes yi given the input features xi and the model parameters ![](images/eq-33.jpg)and ![](images/eq-41.jpg). Logistic regression models are typically fit using optimization techniques such as maximum likelihood estimation (MLE) or gradient descent. These techniques iteratively adjust the values of the regression coefficients to maximize the likelihood function and find the best-fitting model parameters that accurately predict the observed classes.

[Evaluation metrics for classification](#contents.xhtml#sc3_162a)

Here is some common evaluation metrics used in classification:

● Confusion matrix: A confusion matrix is a table (as shown in Table 11.1) that displays the performance of a classifier by comparing the predicted and actual classes. It contains four categories:

o True positives (TP): When both the predicted and actual classes are positive.

o True negatives (TN): When both the predicted and actual classes are negative.

o False positives (FP): When the actual class is negative, but the predicted class is positive.

o False negatives (FN): When the actual class is positive, but the predicted class is negative.

|  || Predicted positive || Predicted negative |
| --- | --- | --- |
| Actual positive || True positive (TP) || False negative (FN) |
| Actual negative || False positive (FP) || True negative (TN) |

Table 11.1: Confusion matrix

● Accuracy: It is the proportion of correctly classified instances compared to the total number It measures how often the classifier makes correct predictions. However, it may not be suitable for imbalanced datasets, where certain classes have more data points than others.

![](images/eq-14.jpg)

● Precision: It measures the proportion of true positive predictions out of all positive predictions made by the classifier. It indicates how accurate the classifier is when it predicts a positive outcome.

![](images/eq-15.jpg)

● Recall (Sensitivity or true positive rate): It measures the proportion of true positive predictions of all actual positive instances in the dataset. It indicates how well the classifier identifies positive instances.

![](images/eq-16.jpg)

● F1 score: The harmonic mean of precision and recall. It provides a balanced measure of a classifier's performance by combining precision and recall.

F1 Score = 2 \* (precision \* recall) / (precision + recall)

● AUC (Area under the ROC curve): The receiver operating characteristic (ROC) curve plots the true positive rate against the false positive rate at various classification thresholds. AUC measures the classifier's ability to distinguish between positive and negative classes. Higher AUC values indicate better classification performance. AUC ranges from 0 to 1, where a value of 0.5 suggests random classification and a value of 1 represents perfect classification.

The figure below illustrates a typical ROC curve:

![](images/Figure11.7.png)

Figure 11.7: A typical ROC curve

AUC assesses a model's predictive capability regardless of the selected classification threshold. This independence ensures that the performance evaluation remains consistent across different decision boundaries.

[Predicting loan defaults using logistic regression](#contents.xhtml#sc3_163a)

In this section, we will build a logistic regression model to predict loan default occurrences. Predicting loan default is a crucial component of banking and lending operations. Lenders must assess the potential profitability and risk, associated with extending loans to borrowers. Even though most borrowers fulfill their repayment obligations, the possibility of default exists, which can lead to a breach of trust between the lender and borrower. It is also a financial threat to the lender's business. Therefore, it is imperative for lenders to accurately estimate the probability of default before approving loan applications.

Accurate default prediction models enable lenders to make informed decisions about loan approvals, pricing, and risk management strategies. By leveraging predictive analytics, lenders can identify high-risk borrowers and take appropriate measures to mitigate the potential for default. This could involve adjusting loan terms, requiring additional collateral, or denying loan applications altogether.

For example: We will begin by reading a CSV file named loan\_df.csv into a data frame called loan\_df. The default column in the data frame is then converted into a factor variable using the as.factor() function, which represents binary categories such as default (1) and no default (0). The table below describes the columns of the data frame loan\_df.

| Column name || Description |
| --- | --- |
| credit\_score || the credit score of individuals applying for loans.  |
| debt\_to\_income\_ratio || the ratio of an individual's total monthly debt payments to their gross monthly income. |
| age || the age of the individual applying for the loan |
| default || the binary response variable, indicating the individual defaulted on their loan (1) or not (0). |

Table 11.2: Description of loan data

To explore the relationship between credit score and default, we will begin by loading the loan dataset and performing some initial data preparation steps. We will then create a histogram to visualize the distribution of credit scores for both default and non-default cases.

*   \# Read the file
*   loan\_df <- read.csv("loan\_df.csv")
*   
*   \# Convert the column, default datatype to factor
*   loan\_df$default <- as.factor(loan\_df$default)
*   
*   \# Distribution of the Default
*   ggplot(loan\_df, aes(x = credit\_score, fill = default)) +
*    geom\_histogram(binwidth = 100, colour = "black") +
*    labs(title = "Default vs. Credit Score",
*    x = "Credit Score",
*    y = "Frequency") +
*    theme\_bw()

The figure below suggests that higher credit scores correspond to a reduced likelihood of default:

![](images/Figure11.8.png)

Figure 11.8: Distribution of credit score

With the data prepared, we will now split the loan dataset into training and testing sets to evaluate the performance of a predictive model. We will then use the training set to fit a logistic regression model that predicts the likelihood of default based on credit score, debt-to-income ratio, and age.

*   \# Split data into train and test
*   set.seed(123)
*   rows\=seq(1,nrow(loan\_df),1)
*   trainRows\=sample(rows,(80\*nrow(loan\_df))/100)
*   train = loan\_df\[trainRows,\] 
*   test = loan\_df\[-trainRows,\]
*   
*   \# Train a logistic regression model
*   LogReg <- glm(default ~ credit\_score + debt\_to\_income\_ratio + age, 
*    data\=train, family=binomial)

Initially, the dataset is divided into training and testing sets using a random sampling technique. The set.seed(123) ensures reproducibility by fixing the random seed. Subsequently, the logistic regression model is trained on the training data using the glm() function. The formula default ~ credit\_score + debt\_to\_income\_ratio + age, specifies the relationship between the binary outcome variable default and the predictor variables credit\_score, debt\_to\_income\_ratio, and age.

The glm() function is used to fit generalized linear models, a broad class of statistical models that includes logistic regression. The syntax of the glm() function is similar to the syntax of the lm() function (for Linear Models), with one key difference. When performing logistic regression, you need to specify the family=binomial argument to tell R to run a logistic regression.

To understand the performance and characteristics of the logistic regression model, we will now generate a summary of the model.

*   \# Summary of the model
*   summary(LogReg)
*   
*   \## Call:
*   \## glm(formula = default ~ credit\_score + debt\_to\_income\_ratio + 
*   \## age, family = binomial, data = train)
*   ##
*   \## Coefficients:
*   \## Estimate Std.  Error z value Pr(>|z|) 
*   \## (Intercept) 1.4256388 0.7269003 1.961 0.0498 \* 
*   \## credit\_score -0.0094701 0.0009416 -10.057 < 2e-16 \*\*\*
*   \## debt\_to\_income\_ratio 1.6934105 0.3883530 4.360 1.3e-05 \*\*\*
*   \## age 0.0194711 0.0126075 1.544 0.1225 
*   \## ---
*   \## Signif. codes: 0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1
*   ##
*   \## (Dispersion parameter for binomial family taken to be 1)
*   ##
*   \## Null deviance: 693.44 on 799 degrees of freedom
*   \## Residual deviance: 515.75 on 796 degrees of freedom
*   \## AIC: 523.75
*   ##
*   \## Number of Fisher Scoring iterations: 6

The summary of the logistic regression model provides insights into the relationships between the predictor variables (credit\_score, debt\_to\_income\_ratio, and age) and the likelihood of loan default.

The coefficients represent the change in the log odds of the outcome (default) for a one-unit change in the corresponding predictor variable, holding all other variables constant. A positive coefficient indicates increased log odds of default, while a negative coefficient indicates decreased log odds. The intercept represents the log odds of default when all predictor variables are zero. The negative coefficient for credit score indicates that as credit\_score increases, the log odds of default decrease. The positive coefficient for debt\_to\_income\_ratio suggests that as debt\_to\_income\_ratio increases, the log odds of default also increase.

The p-value of credit\_score (< 2e-16) and debt\_to\_income\_ratio (1.3e-05) is very small which indicates that they are highly significant in predicting loan default. Although, the column, age is not statistically significant as indicated by the p-value (0.1225).

The null deviance represents the model's fit without any predictor variables, while the residual deviance measures the model's fit with the predictor variables included. A decrease in deviance indicates an improved model fit. The Akaike Information Criterion (AIC) is the relative quality of statistical models, for a given dataset. Lower AIC values indicate a better fit.

To evaluate the performance of the logistic regression model on unseen data, we will now use the trained model to make predictions on the test set, and then convert the predicted probabilities into class labels (default or non-default).

*   \# Predict the Model on the Test Set
*   fitted\_results <- predict(LogReg,test,type\='response')
*   
*   \# Convert Probabilities to Class Labels
*   fitted\_class <- ifelse(fitted\_results > 0.5,1,0)

The predict() function can be used to predict the probability of an outcome, given the values of the predictor variables. When working with a logistic regression model, the type="response" option in the predict() function tells R to output the probabilities of the form P(Y = 1 | X), where Y is the binary dependent variable and X represents the predictor variables. The predicted probabilities are then converted into binary class labels (0 or 1) using a threshold of 0.5. If the predicted probability of default is greater than 0.5, the observation is classified as default (1); otherwise, it is classified as non-default (0).

To assess the accuracy of the model's predictions, we will now create a confusion matrix.

*   \# Confusion Matrix
*   conf\_matrix = table(test$default,fitted\_class)
*   conf\_matrix
*   \## fitted\_class
*   \## 0 1
*   \## 0 151 12
*   \## 1 25 12
*   
*   \# Calculate True Positives (TP), True Negatives (TN), False Positives (FP), and False Negatives (FN)
*   TP <- conf\_matrix\[2,2\]
*   TN <- conf\_matrix\[1,1\]
*   FP <- conf\_matrix\[1,2\]
*   FN <- conf\_matrix\[2,1\]
*   
*   \# Calculate Accuracy
*   accuracy <- (TP + TN) / sum(conf\_matrix)
*   accuracy
*   \## 0.815
*   
*   \# Calculate Precision
*   precision <- TP / (TP + FP)
*   precision
*   \## 0.5
*   
*   \# Calculate Recall (Sensitivity)
*   recall <- TP / (TP + FN)
*   recall
*   \## 0.3243243

The confusion matrix is computed to summarize the performance of the model. It tabulates the counts of true positive (TP), true negative (TN), false positive (FP), and false negative (FN) predictions made by the model compared to the actual outcomes in the test dataset. The model achieves an accuracy of 0.815, indicating that it correctly classifies about 81.5% of the instances in the test dataset. The precision is 0.5, suggesting that about half the instances predicted as defaults are true positives, while the other half are false positives. The recall is 0.324, indicating only about 32.4% of the actual defaults are correctly identified by the model.

[Limitations of linear models](#contents.xhtml#sc3_164a)

The following are the limitations of linear models:

*   Linear models are simple and effective for modeling relationships between input variables and an output variable when the relationship is approximately linear. While linear models offer simplicity and interpretability, they may not always capture the complex relationships present in the data due to their inherent linearity assumption.
*   Linear models are inherently limited in their ability to capture nonlinear relationships and interactions between variables. This can result in underfitting, where the model fails to capture the true underlying patterns in the data.
*   Linear models are sensitive to outliers which can disproportionately impact the model parameters and predictions, leading to biased estimates.

Now that we have explored linear models, let us move on to a different type of predictive modeling technique: decision trees.

[Decision trees](#contents.xhtml#sc2_165a)

A decision tree is an ML algorithm using a tree-shaped model to represent decisions and their possible consequences. Decision trees consist of nodes and branches. The topmost node is called the root node. It represents the initial question. Each branch represents the outcome of a test at a node, and each node represents a test on an attribute (or independent variable). The leaf nodes represent the outcomes or class labels (in the case of a classification problem) or numerical values (in the case of a regression problem).

Several key terms and concepts are used to describe decision trees:

*   Root node: Represents the entire sample population or dataset and serves as the starting point for building the tree.
*   Decision node: A node in a decision tree where a decision is made based on a feature's value.
*   Terminal/Leaf node: A node in a decision tree where the outcome or class label is assigned.
*   Depth: Measures the length of a path from the root node to a leaf node along branches and is commonly used to control tree size during growth.
*   Splitting criterion: A measure used to determine the feature and value to split the data at each node, often based on metrics like Gini impurity, entropy, or information gain.
*   Pruning: The process of reducing the size of a decision tree by removing sections of the tree that provide little predictive power. It helps to avoid overfitting and improve generalization performance.

The figure below shows the general structure of a decision tree:

![](images/Figure11.9.png)

Figure 11.9: General structure of a decision tree

Some advantages of decision trees include:

*   Model interpretability: A major advantage of decision trees is their ability to provide clear insights to simplify decision-making processes. Rules generated by decision trees facilitate communication and collaboration with domain specialists and regulators.
*   Nonparametric approach: They are suitable for addressing varied problem structures without strict assumptions about data distribution.
*   Handling mixed data types: Decision trees handle numerical and categorical features, simplifying preprocessing efforts.
*   Resistance to outliers: Compared to parametric methods, decision trees exhibit greater resilience to extreme observations.

However, drawbacks arise primarily from overfitting risks and sensitivity to small changes in the dataset. Addressing these issues involves hyperparameter tuning or leveraging ensemble techniques.

There are two types of decision trees:

*   Classification trees tackle discrete or categorical dependent variables.
*   Regression trees handle continuous dependent variables.

They are explained in detail below:

[Classification trees](#contents.xhtml#sc3_166a)

Classification trees are a type of decision tree, used to predict the class or category of a given data point They work by recursively partitioning the feature space into regions, where each region corresponds to a certain class label. When a new instance is to be classified, it traverses down the tree, following the decision rules at each node until it reaches a leaf node, where the class label is assigned. There are several different methods for determining how to split the data at each node Two common approaches are the Gini index and Entropy.

*   Gini index: measures the impurity or uncertainty of a set of data points. It ranges from 0 to 1, where 0 indicates perfect purity (all elements belong to the same class) and 1 indicates maximum impurity (an equal distribution of elements across all classes). The Gini impurity index with C classes for a set S is calculated by:

![](images/eq-17.jpg)

The Gini index approach aims to maximize the purity of child nodes after the split, thus leading to a decision tree that makes more accurate classifications.

*   Entropy: is a measure of randomness or uncertainty in a set of data points. In the context of decision trees, entropy is used to quantify the impurity of a node. A node with low entropy means it is pure (all data points belong to the same class), while a node with high entropy means it is impure (data points are evenly distributed between classes). The information gain is the measure of the reduction in entropy achieved by splitting a node on a particular feature. The decision tree algorithm selects the split that maximizes the information gain. The entropy for a set S with C classes is given by:

![](images/eq-18.jpg)

Let us build a decision tree to predict the loan default using rpart (Recursive partitioning and regression trees).

*   \# load the required libraries
*   library(rpart)
*   library(rpart.plot)
*   
*   \# Train a Decision Tree model 
*   Model\_rpart= rpart(default~ credit\_score + debt\_to\_income\_ratio,
*    data=train, method="class", maxdepth = 5)

Here, the model is trained to predict the binary outcome of loan default (default) based on two input features: credit\_score and debt\_to\_income\_ratio. The training data is stored in the train dataset. The method="class" argument specifies that the model is for classification, and the maxdepth = 5 argument limits the maximum depth of the decision tree to 5 levels.

The resulting Model\_rpart object represents the trained decision tree model, which can be used to make predictions on new data.

To gain a better understanding of the decision-making process used by the model, we will now visualize the decision tree, which will provide a graphical representation of the rules and splits used to predict loan defaults.

*   \# Visualise the decision tree
*   rpart.plot(Model\_rpart)

![](images/Figure11.10.png)

Figure 11.10: Decision tree to predict loan default

To further interpret the decision tree model, we will now extract the rules used to predict loan defaults, which will provide a concise and readable summary of the conditions and thresholds used to assign probabilities of default.

*   \# Decision tree rules
*   rpart.rules(Model\_rpart, cover = T)
*   
*   \## default cover
*   \## 0.05 when credit\_score >= 506 66%
*   \## 0.26 when credit\_score < 506 & debt\_to\_income\_ratio < 0.62 21%
*   \## 0.33 when credit\_score is 377 to 506 & debt\_to\_income\_ratio >= 0.62 8%
*   \## 0.74 when credit\_score < 377 & debt\_to\_income\_ratio >= 0.62 5%

The decision tree model is visualized using the rpart.plot function, which creates a graphical representation of the tree structure. The rpart.rules function extracts the rules or conditions learned by the decision tree model. The output presents a set of rules that define the conditions for predicting the binary outcome of loan default. Each rule consists of a combination of feature values and the corresponding probability of default. 

Interpretation of the decision rules:

*   If the credit\_score is greater than or equal to 506, the predicted probability of default is 0.05, covering about 66% of the dataset.
*   If the credit\_score is less than 506 and the debt\_to\_income\_ratio is less than 0.62, the predicted probability of default increases to 0.26, covering about 21% of the dataset.
*   If the credit\_score falls within the range of 377 to 506 and the debt\_to\_income\_ratio is greater than or equal to 0.62, the predicted probability of default is 0.33, covering about 8% of the dataset.
*   If the credit\_score is less than 377 and the debt\_to\_income\_ratio is greater than or equal to 0.62, the predicted probability of default is notably higher at 0.74, covering about 5% of the dataset.

Next, let us predict the loan default for the test dataset using the trained decision tree model (Model\_rpart). The type="class" argument ensures that class labels are returned instead of probabilities. The predictions are stored in the pred\_rpart variable.

*   #Predicting on Test
*   pred\_rpart <- predict(Model\_rpart, test, type="class")
*   
*   \# Confusion Matrix
*   conf\_matrix = table(test$default,pred\_rpart)
*   conf\_matrix
*   \## pred\_rpart
*   \## 0 1
*   \## 0 159 4
*   \## 1 28 9
*   
*   \# Calculate True Positives (TP), True Negatives (TN), False Positives (FP), and False Negatives (FN)
*   TP <- conf\_matrix\[2,2\]
*   TN <- conf\_matrix\[1,1\]
*   FP <- conf\_matrix\[1,2\]
*   FN <- conf\_matrix\[2,1\]
*   
*   \# Calculate Accuracy
*   accuracy <- (TP + TN) / sum(conf\_matrix)
*   accuracy
*   \## 0.84
*   
*   \# Calculate Precision
*   precision <- TP / (TP + FP)
*   precision
*   \## 0.6923077
*   
*   \# Calculate Recall (Sensitivity)
*   recall <- TP / (TP + FN)
*   recall
*   \## 0.2432432

Based on the confusion matrix, we calculated the accuracy, precision, and recall (sensitivity) metrics. Accuracy is the proportion of correctly predicted instances out of all instances, which is 0.84 in this case. Precision is the proportion of true positives out of all predicted positives, resulting in a value of 0.69. Recall is the proportion of true positives out of all actual positives, yielding a value of 0.24.

[Regression trees](#contents.xhtml#sc3_167a)

Regression trees are another type of decision tree used when the target variable is continuous. Unlike classification trees, which predict categorical outcomes, regression trees predict numerical values.

Regression trees work by recursively partitioning the feature space into regions, where each region corresponds, to a predicted numerical value. When a new instance has to be predicted, it traverses down the tree, following the decision rules at each node until it reaches a leaf node, where the predicted numerical value is assigned. There are several methods for splitting in regression trees, with two common approaches being the reduction in the sum of squares (RSS) and the reduction in mean squared error (MSE).

The RSS approach minimizes the sum of squared differences between the predicted values and the actual values within each partition. At each node, the algorithm contemplates all possible splits for each feature and calculates the RSS for each split. It then selects the split that minimizes the total RSS across all partitions.

The MSE approach is similar to RSS but different in some aspects. It focuses on minimizing the mean squared error within each partition. The mean squared error is the average of the squared differences between the predicted and the actual values. The algorithm selects the split that minimizes the total MSE across all partitions.

When training decision tree models, several hyperparameters can be tuned to help reduce the risk of overfitting. Three key hyperparameters are:

*   Max depth (maxdepth): The maximum depth of the decision tree, which controls the complexity of the model. A deeper tree can capture more intricate patterns in the data but is also more prone to overfitting. Setting a lower max depth can help prevent the tree from growing too complex and fitting noise in the training data.
*   Minimum samples for split (minsplit): The minimum number of samples required to split a node. Increasing this parameter can help reduce overfitting by requiring more samples before a split is made, preventing the tree from creating specific, high-variance splits.
*   Minimum samples in leaf (minbucket): The minimum number of samples required in each leaf node. Setting a higher value for this parameter can help prevent the creation of leaf nodes with very few samples, which are more likely to overfit the training data.

By fine-tuning these hyperparameters, one can strike the right balance between model complexity and generalization. A too-deep tree, with too few samples to split and create leaf nodes is likely to overfit the training data. Adjusting these hyperparameters can help the decision tree model capture the underlying patterns in the data without becoming overly complex and sensitive to noise or outliers.

[Bias-variance tradeoff](#contents.xhtml#sc2_168a)

Prediction errors can be understood in terms of two main components: bias error and variance error. Bias represents the error introduced by approximating a real-world problem with a simplified model. It is the difference between the average prediction of the model and the true value being predicted. A high-bias model tends to underfit the data. It oversimplifies the relationships between features and the target variable.

Variance measures how much the predictions of a model vary for a given data point. It quantifies the model's sensitivity to fluctuations in the training data. A high variance model tends to overfit the data. It captures noise in the training data as genuine patterns, leading to poor generalization on unseen data.

The bias-variance trade-off arises from the fact that reducing one component often leads to an increase in the other. Models with high bias have low complexity and may fail to capture underlying patterns in the data. At the same time, models with high variance have high complexity and may fit the noise in the training data too closely. By trading some bias for variance (or vice versa), we can find a balanced model for our dataset. Below [Figure 11.11](#ch11.xhtml#fig11-11) shows the bias-variance tradeoff:

![](images/Figure11.11.png)

Figure 11.11: Bias-variance trade-off

The ideal model lies in the sweet spot between bias and variance, striking a balance that minimizes both sources of error. It is neither simple (high bias) nor complex (high variance). Achieving such a balance yields the minimum prediction error on new, unseen data. This balanced model generalizes well to unseen data, making it robust and reliable for making predictions.

[Clustering](#contents.xhtml#sc2_169a)

Clustering is concerned with discovering inherent structures and relationships within unlabeled data. It is a type of unsupervised learning, meaning that it is used when the data is not labeled or classified. Clustering finds diverse applications across numerous industries, serving various purposes such as market segmentation, social network analysis, segmenting images, and detecting anomalies. Once you perform clustering, each cluster receives a unique identifier known as a cluster ID. The clustering output can also be used as feature data for downstream machine learning systems.

Consider a scenario where a bank seeks to segment its customers based on demographic information and transaction behavior. By employing clustering techniques, the bank can partition its customer base into distinct groups, each exhibiting similar characteristics. These clusters may reflect common traits such as age, income, transaction frequency, or preferred banking channels.

The success of clustering hinges on its interpretability and practicality. Can the resulting clusters be understood and translated into actionable insights for the business? Do they reveal new perspectives or patterns previously overlooked?

[K-means clustering](#contents.xhtml#sc3_170a)

K-means clustering is a popular unsupervised machine learning algorithm used for partitioning a dataset into a predefined number of clusters. It works by iteratively assigning data points to clusters and updating the cluster centroids until convergence is reached. One essential step in data preprocessing for k-means clustering is ensuring that all features have the same scale. This is necessary because k-means relies on calculating the distance between data points to assign them to clusters, and features with different scales can disproportionately influence the clustering process.

For k-means clustering, the process involves the following steps:

1.  Determining the number of clusters (k): Decide on the optimal number of clusters for the dataset.
2.  Initializing cluster centroids: Randomly place k cluster centroids within the feature space.
3.  Assigning data points to clusters: Assign data points to the nearest cluster.
4.  Updating cluster centroids: Recalculate the centroids of each cluster by taking the mean of all data points assigned to that cluster.
5.  Iterating until convergence: Repeat steps 3 and 4 until the cluster assignments no longer change significantly, or a predetermined number of iterations is reached.

Finding the optimal number of clusters

 The elbow method is a popular technique used to identify the optimal number of clusters. It plots the number of clusters (k) against the corresponding within-cluster sum of squares (WCSS), and visually inspects the plot for an elbow point.

WCSS is calculated using the following steps:

1.  For each cluster, calculate the sum of squared distances between each data point in the cluster and the centroid of that cluster.
2.  Sum up these squared distances across all clusters to obtain the total WCSS.

The objective of k-means clustering is to minimize WCSS. When you increase the number of clusters (k), the WCSS decreases because the clusters become smaller and more compact. However, adding more clusters also increases the risk of overfitting the data, which may not represent the underlying structure well. Let us understand how the elbow method works:

*   Perform k-means clustering for a range of values of k (e.g., from 1 to 10 clusters).
*   For each value of k, calculate the WCSS.
*   Plot the number of clusters (k) on the x-axis and the corresponding WCSS on the y-axis.
*   Check the resulting plot. The elbow point is the point where the rate of decrease in WCSS slows down and forms an elbow-like shape.

The elbow point represents the optimal number of clusters because it indicates the point at which the rate of decrease in WCSS slows down significantly. Adding more clusters beyond this point may not provide much additional benefit in terms of improving the quality of clustering.

Advantages of k-means

*   The algorithm is efficient and can handle large datasets with many data points, making it suitable for applications with extensive data.
*   K-means can easily incorporate new data points into existing clusters, allowing the model to adapt to changes in the dataset over time.
*   The algorithm can handle clusters of different shapes and sizes. This flexibility enables k-means to be applied to a wide range of clustering tasks across various domains.

[Conclusion](#contents.xhtml#sc2_171a)

Understanding the ML lifecycle phases and their interactions is crucial for building effective ML models. Following all the steps, we can develop, monitor, and deploy models that meet our requirements. Linear regression uses a straight line to minimize errors, while logistic regression uses the sigmoid function to transform outputs into probabilities. Tree-based models like decision trees, provide an intuitive approach to classification and regression tasks, enabling the interpretation of complex relationships within data. However, it is crucial to navigate the trade-off between bias and variance to prevent overfitting and ensure optimal model performance. Clustering techniques like k-means clustering, provide valuable insights by grouping similar data points and helps in pattern discovery and data exploration.

With a solid foundation in these fundamental techniques, you are now well-prepared to move on to the next chapter, where you will learn how to build a successful career in this field.

Join our book’s Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/fm1.png)

# [CHAPTER 12Building a Career in Data Science](#contents.xhtml#ch12a)

[Introduction](#contents.xhtml#sc2_172a)

Building a career in data science is like getting on a decade-long adventure, filled with twists and turns that keep things interesting. The path ahead may not always be clear, but that is part of the thrill of the journey. As data science rapidly rises, so does the demand for AI skills. Many individuals are seizing this moment to forge fulfilling careers in this field. It is essential to understand that a career is not merely a job, but a long-term journey characterized by growth, exploration, and sometimes unforeseen diversions.

[Structure](#contents.xhtml#sc2_173a)

The following topics will be covered in this chapter:

*   Key steps of data science career growth 
    *   Building a strong foundation: Math and programming essentials
    *   Gaining knowledge of ML algorithms
    *   Building a portfolio
*   Communication in data science 
    *   Storytelling with data
*   Acing the data science job search 
    *   Contemplating the way ahead
    *   Engaging in informational interviews

[Objectives](#contents.xhtml#sc2_174a)

Data science is a fascinating field with a lot of opportunities, but figuring out where to start can be tricky. This chapter is here to help you find your way and make the most of those opportunities. It will outline the critical steps to guide your growth in this field, beginning with a solid understanding of the fundamental aspects of data science processes and essential mathematical concepts. We will also discuss the importance of mastering ML algorithms and programming languages for practical implementation. The chapter will also emphasize the importance of engaging in data science projects to enhance problem-solving skills. Lastly, we will highlight how curiosity and effective communication can foster professional growth and success in the field.

[Key steps towards data science career growth](#contents.xhtml#sc2_175a)

Before starting your job search in data science, it is vital to follow these steps so that you are adequately prepared and can establish a solid foundation in the required skills.

1.  Step 1: Building a strong foundation: Math and programming essentials
2.  Step 2: Gaining knowledge of ML algorithms
3.  Step 3: Building a portfolio

[Building a strong foundation: Mathematics and programming essentials](#contents.xhtml#sc3_176a)

The following are some mathematics concepts that are key to building a strong foundation in data science.

Linear algebra

It is fundamental to data science, particularly when working with high-dimensional data and ML algorithms.

*   It allows you to do data transformations. Operations such as rotation and scaling can be represented using matrices and vectors. This is essential for tasks like data normalization, and feature scaling.
*   Dimensionality reduction techniques like Principal Component Analysis (PCA) rely on linear algebra to reduce the dimensionality of data while retaining most of its variance. PCA uses eigenvalues and eigenvectors to identify the directions of maximum variance, enabling data compression into lower-dimensional space.
*   Many ML algorithms, including linear regression, logistic regression, and neural networks, are built upon linear algebra concepts. For instance, in linear regression, the model coefficients are estimated by minimizing the sum of squared differences between predicted and actual values, which involves matrix operations.

Calculus

It provides a deeper understanding of optimization, gradient descent, and advanced ML topics.

*   Calculus provides tools for finding maxima and minima of functions. This is essential for optimizing model performance. For example, gradient descent, a widely used optimization algorithm, relies on calculus to iteratively update model parameters to minimize a loss function.
*   Derivatives are used to quantify rates of change and slopes of functions. Integrals calculate areas under curves, cumulative quantities, and expected values.

Statistics

It helps us to draw meaningful conclusions, assess uncertainty, and make data-driven decisions. It evaluates data with measures like mean and standard deviation, modeling data with probability distributions, and making inferences through hypothesis testing and regression analysis. It also plays a pivotal role in quality assurance, ensuring processes and products meet desired standards.

Probability theory

It is the foundation for understanding uncertainty and making predictions in data science. Probability distributions model data behavior, aiding in risk assessment and prediction.

Programming essentials

Essential Programming concepts to learn, include:

R, Python, and SQL skills

Mastering R and Python provides you with tools for data manipulation, statistical analysis, and ML, essential for any data-driven role. SQL is crucial for accessing and managing data from relational databases—your go-to for retrieving insights from raw data.

ML implementation

Build hands-on experience with models for classification, regression, and clustering. Knowing how to implement and evaluate these models prepares you to solve real-world problems with data-driven insights.

Version control with Git

Git is essential for tracking code changes and streamlining collaboration. It keeps a complete record of your work, making teamwork smoother and ensuring you can easily manage project evolution over time—a must for data science projects.

Software development best practices

Write modular, reusable code and document your work. Following best practices keeps your code clean and easy for others to understand, making collaboration smoother and ensuring your work is ready for scaling up in professional settings.

[Gaining knowledge of ML algorithms](#contents.xhtml#sc3_177a)

A solid understanding of core ML concepts and models is essential. This includes understanding models like linear regression, logistic regression, decision trees, ensemble models, clustering, and anomaly detection. Understanding the core concepts that underline the functionality and effectiveness of ML is more important than simply memorizing these models. This entails understanding fundamental principles such as bias/variance tradeoffs, cost functions, regularization techniques, optimization algorithms, and error analysis.

Understanding these fundamentals allows you to apply concepts effectively, and troubleshoot, fine-tune, and interpret their results accurately. For example, when faced with a classification problem, you should be able to explain the rationale behind choosing a logistic regression model over a decision tree. You should also be able to interpret the output, assess its accuracy, and propose improvements based on your understanding of error analysis.

Additionally, stay updated with the latest advancements and trends in ML. Employers value candidates, well-versed in emerging topics like deep learning, natural language processing, and large language models. Demonstrating knowledge in these areas showcases your enthusiasm for the field and ability to new challenges.

[Building a portfolio](#contents.xhtml#sc3_178a)

Building a data science portfolio before applying for jobs is crucial in today's competitive job market. With the increasing popularity of data science programs and their relevant courses, there is a surge of new talent. This makes it essential to stand out in the crowd. A well-crafted portfolio is an excellent way to demonstrate your skills, experience, and expertise to potential employers.

*   Highlight your best work: A data science portfolio is your best work highlighting your problem-solving abilities, creativity, and technical skills. It is an opportunity to showcase your projects, ideas, and contributions to the data science community. A strong portfolio can help you land job interviews, impress hiring managers, and demonstrate your potential value to a team.
*   Showcase your unique experience: However, creating a portfolio, that stands out can be challenging. Many data scientists have portfolios, but only a few have exceptional ones. A generic portfolio that lacks interesting projects or explanations can be hard for your readers to follow and stay interested in. Therefore, your portfolio should showcase your unique skills, experience, and personality.
*   Include a diverse range of projects: A diverse range of projects demonstrating proficiency in various aspects of data science is essential. Each project should showcase your ability to tackle various kinds of data and solve real-world problems effectively. Additionally, it is important to highlight your expertise in handling different data formats and sources. This could involve working with structured data from databases, unstructured data from text documents or social media feeds, or even semi-structured data like JSON or XML files. Demonstrating your versatility in handling diverse data types strengthens your portfolio and showcases your adaptability as a data scientist.
*   Highlight your skills with in-depth insights and analysis: When creating your data science portfolio, it is also important to consider the depth of your projects. While showcasing varied projects is important to demonstrate versatility, projects that go in-depth into a particular problem and involve advanced techniques and rigorous evaluation can help showcase your expertise and attention to detail. Including projects with thorough analysis, advanced ML modeling, and meaningful evaluation metrics can help highlight your skills and abilities to potential employers.
*   Include practical experience: Additionally, showcasing your experience working on real-world data science projects can greatly strengthen your portfolio. This can be achieved through internships, freelance work, hackathons, or competitions. Practical experience not only adds credibility to your skills, it also showcases your readiness to take on professional challenges, making you a more attractive candidate to potential employers.
*   Seek feedback: It is equally important to seek feedback and mentorship from experienced data scientists to identify areas for improvement. Consider reaching out to mentors who can provide guidance and insights into the field. Contributing to the data science community by sharing learnings can help establish you as a valuable contributor. Consider writing blog posts, creating tutorials, or presenting at local meetups or conferences. Teaching others not only reinforces understanding, it also helps build your reputation and credibility in the field.

[Communication in data science](#contents.xhtml#sc2_179a)

The ability to communicate effectively is a crucial skill for data scientists, as it allows them to explain complex data insights and outcomes to non-technical stakeholders and drive data-informed decision-making within an organization. While technical expertise in data analysis and model creation is essential, effective communication ensures comprehension of the value of data science, and its utilization by the business.

Aspects of communication in data science

*   Story telling: A key aspect of communication in data science is storytelling. Storytelling allows you to present complex information in a compelling and accessible manner. Data insights with a narrative structure make it easy for stakeholders to understand data, its context, relevance, and potential. For example, instead of simply presenting a set of numbers and statistics, you might craft a story around how a particular data-driven decision led to a successful business outcome. This approach helps to engage the audience and makes the data more memorable and actionable.
*   Presentation skills: Whether presenting to a small group of executives or a large conference audience, you must be able to convey your findings clearly and confidently. This includes using appropriate visuals, such as data visualizations, to support the narrative and ensure the presentation is engaging and easy to follow. Effective presentations require careful planning and consideration of the audience, with a clear beginning, middle, and end that leads to a specific call to action.
*   Visual representations of data: Charts and dashboards, can help stakeholders quickly understand complex information and identify patterns and trends. Lastly, business insight and acumen are vital for effective communication in data science. You must be able to translate your findings into actionable business recommendations. This involves understanding the broader business context, industry trends, and potential opportunities or challenges that the data may reveal.

[Storytelling with data](#contents.xhtml#sc3_180a)

Data visualization and data storytelling are two powerful tools used to communicate insights and information derived from data analysis. While they are often used together, they serve distinct purposes and contribute uniquely to effective data communication.

*   Data visualization: It is the process of presenting data in visual formats such as graphs, maps, and dashboards. The primary purpose of data visualization is to present data in a visually compelling and easy-to-understand format such that audiences can grasp patterns, trends, and relationships at a glance. Well-designed data visualizations are appropriate to the data, legible, and not misleading, ensuring that the visual representation accurately conveys the underlying data.

Different types of visualizations serve different purposes. For example, a line chart shows trends over time, while a bar graph is suitable for comparing discrete data points. Selecting the right visualization ensures that the data is presented in a way that is easily understandable and aligns with the story being told.

Cluttered visuals can distract and confuse the audience, detracting from the story. Simplifying the visualization and removing unnecessary elements helps to focus attention on the most important data points and insights.

*   Data storytelling: It is the art of using data to craft a narrative that engages and influences an audience. It involves presenting data insights within a structured story framework, typically following a beginning, middle, and end format. Data storytelling goes beyond a simple presentation of data. It provides context, highlights critical insights, and guides the audience toward a specific conclusion or call to action.

It directs your audience's attention towards the most salient aspects of your data narrative. You can use visual cues such as color, size, or annotations to highlight critical trends, patterns, or outliers. Data storytelling is most powerful when it follows a narrative structure. Framing the data within a story arc, with a beginning, middle, and end, helps the audience understand the context, the challenges or opportunities presented, and the ultimate insights or conclusions. This could involve introducing characters or scenarios to make the story more relatable and engaging.

While data visualization focuses on the clear and accurate representation of data, data storytelling emphasizes the interpretation and context surrounding the data. Data storytelling adds a layer of meaning and impact to the raw numbers, making the information more memorable and persuasive. It transforms data insights into a compelling narrative that resonates with the audience and drives home the key messages. Here are some recommended practices to help you craft impactful data stories that captivate and educate your audience:

*   Know your audience: Before crafting your data story, take the time to understand your target audience. Consider their interests, needs, and level of data literacy. Customizing your message and visualizations to align with their expectations, you can ensure your data story is engaging and accessible to them.
*   Set clear objectives: Clearly define the key messages or insights you want your audience to take away. Are you highlighting a trend, comparing alternatives, or revealing a solution to a problem? Setting explicit objectives will help structure your narrative and ensure your data story has a powerful and focused impact.
*   Select compelling visualizations: Choose data visualizations that effectively convey your insights. Ensure your visuals are legible, appropriately labeled, and free from clutter. 
*   Use anecdotes and examples: Bring your data story to life with relatable anecdotes and examples. Use narrative techniques to illustrate your points and make your story more engaging.
*   Practice regularly: Incorporate data storytelling into your regular work routine. Seek opportunities to apply your knowledge, through presentations to colleagues, client reports, or data visualization projects. Continuous practice will refine your skills and enhance your data storytelling abilities 
*   Listen and adapt: When presenting your data story, actively listen to your audience's reactions and questions. Be prepared to provide additional context or clarify information as needed. Show that you value their input and are open to addressing any concerns or curiosities they may have.

You can explore different storytelling techniques to find your unique style. Experiment with narrative structures, character development, or creative framing of your data insights. Trying new approaches will help you discover what works best for engaging your audience and conveying complex information effectively.

[Acing the data science job search](#contents.xhtml#sc2_181a)

Navigating a job search involves several anticipated phases, such as identifying target companies, readying for interviews, and ultimately, selecting a position.

[Contemplating the way ahead](#contents.xhtml#sc3_182a)

First, consider the direction you want to take in data science. Are you transitioning to a new role within data science, such as moving from software engineering to ML engineering? Or are you aiming to shift to a different industry, such as moving from supply chain to technology? Defining your objective will provide clarity for effective planning.

Let us consider an example. You are an analyst in supply chain management services and looking for a career in AI.

If you opt for a data science or ML role within the supply chain industry, you can leverage your existing domain knowledge while gaining valuable AI expertise. This approach allows you to build a strong foundation in AI before making a more significant leap. Once you have gained experience in this role, transitioning to a tech company becomes more feasible.

Regarding role switching, startups often offer a more flexible environment than larger companies. Startups typically have smaller teams and may be more open to employees taking on additional responsibilities outside their job scope. A willingness to contribute to AI tasks, even informally, is likely to be noticed and appreciated, potentially paving the way for a role switch within the same company. In contrast, big companies often have more rigid structures and reward systems that focus primarily on excelling within your designated job role.

First, decide if your priority is to switch roles or industries. Once you establish that foundation, you can gradually expand your scope and explore additional opportunities. This approach can make the transition smoother and provide a solid foundation for building an amazing career in data science.

[Engaging in informational interviews](#contents.xhtml#sc3_183a)

Informational interviewing, or engaging in informal conversations with professionals in roles or companies of interest, is a powerful strategy for gaining a deep understanding of various positions and their demands. In the ever-evolving field of AI, where job titles can differ significantly between organizations, these interviews take on even greater importance.

For example, the tasks and expectations of a data scientist can differ greatly from one company to another. While one organization might focus on data analysis and presentation, another might prioritize coding and managing production systems. By conducting informational interviews, you can uncover the true nature of AI roles within specific contexts.

Engaging in informational interviews also provides you with a unique perspective on company culture and work environment. You gain insights into the day-to-day challenges and accomplishments associated with the role, helping you assess if it aligns with your interests, values, and long-term career aspirations. Through these conversations, you can learn about the algorithms, deployment procedures, and software frameworks used by specific organizations. This proactive approach can set you apart when it comes time to apply for roles, as you will have a deeper understanding of the role's requirements and how you can contribute value.

Here is a list of questions that you could consider asking during informational interviews:

*   Could you walk me through a typical day or week in your role?
*   What are the key responsibilities and tasks that you focus on?
*   In your opinion, what are the top three skills or competencies that contribute most to success in this role?
*   How does your team collaborate to achieve its goals? Are there any specific processes or tools you use to facilitate effective teamwork?
*   Can you describe the hiring process for this role? What are the key stages, and what does the company look for in potential candidates?
*   What specific technical skills or programming languages are most valuable for this position?
*   How does the company support professional development and ongoing learning for data scientists/ analysts?

Remember, informational interviews are a great way to gain insights and clarify any doubts you may have about the role. Do not be afraid to ask questions that are important to you and your career goals. The more informed you are, the better equipped you will be to make the right career choices.

Finding the right person to interview can be a challenge, but it is important to remember that many senior professionals today benefited from the support of those who came before them. They understand the value of mentorship and are often eager to pay it forward. So, do not hesitate to reach out and tap into your existing network. Start with friends or acquaintances who have already made a similar transition and can offer valuable insights. They may even be able to make introductions to other relevant individuals.

Attending meetups and industry events is another great way to expand your network and connect with potential interviewees. These gatherings provide opportunities to meet like-minded individuals who share your interests and may be open to informational interviews.

You can also explore online platforms and professional networking sites, like LinkedIn, to look for individuals who work in companies or roles that align with your interests. You can send a polite message expressing your interest in learning more about their career path and requesting a brief conversation.

[Conclusion](#contents.xhtml#sc2_184a)

The beauty of a career in data science lies in its potential for constant evolution. As technology advances and new innovations emerge, so do fresh challenges and opportunities. Embracing this ever-changing landscape keeps your journey exciting and filled with endless possibilities. Remember, it is not just about the destination but the fascinating exploration along the way. With each step, you will uncover new possibilities, develop valuable skills, and create a rewarding and fulfilling career path. Remember, focus on building a strong foundation. Experiment with different ML algorithms, explore datasets and seek out tutorials and online resources. As you progress, you will develop the skills to tackle real-world data challenges and create innovative solutions that leverage the power of ML. Happy learning!

Join our book’s Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/fm1.png)

# Index

A

accuracy [217](#ch11.xhtml#page217)

alternative hypothesis [186](#ch09.xhtml#page186)

Analysis of Variance (ANOVA) [186](#ch09.xhtml#page186)

arrays [35](#ch02.xhtml#page35)\-[37](#ch02.xhtml#page37)

associations, visualizing [149](#ch07.xhtml#page149)

boxplot [149](#ch07.xhtml#page149)

scatter plot [153](#ch07.xhtml#page153)\-[155](#ch07.xhtml#page155)

attributes [32](#ch02.xhtml#page32)

dim() function [33](#ch02.xhtml#page33), [34](#ch02.xhtml#page34)

names() function [32](#ch02.xhtml#page32), [33](#ch02.xhtml#page33)

AUC (Area under the ROC curve) [218](#ch11.xhtml#page218)

B

bar plots [136](#ch07.xhtml#page136)\-[140](#ch07.xhtml#page140)

bias [230](#ch11.xhtml#page230)

bias-variance trade-off [230](#ch11.xhtml#page230)

binning [166](#ch08.xhtml#page166), [167](#ch08.xhtml#page167)

equal-width binning [167](#ch08.xhtml#page167), [168](#ch08.xhtml#page168)

quantile binning [168](#ch08.xhtml#page168)

box-and-whisker plots [149](#ch07.xhtml#page149)

boxplot [149](#ch07.xhtml#page149)

applications [149](#ch07.xhtml#page149)\-[152](#ch07.xhtml#page152)

business analytics [11](#ch01.xhtml#page11)

descriptive analytics [11](#ch01.xhtml#page11)\-[13](#ch01.xhtml#page13)

diagnostic analytics [14](#ch01.xhtml#page14)\-[16](#ch01.xhtml#page16)

predictive analytics [16](#ch01.xhtml#page16)\-[18](#ch01.xhtml#page18)

prescriptive analytics [18](#ch01.xhtml#page18), [19](#ch01.xhtml#page19)

business problem [5](#ch01.xhtml#page5)\-[7](#ch01.xhtml#page7)

C

calculations, with dates and times

leading and lagging calculations [109](#ch05.xhtml#page109), [110](#ch05.xhtml#page110)

calculus [237](#ch12.xhtml#page237)

career in data science [235](#ch12.xhtml#page235)

categorical data

dealing with [171](#ch08.xhtml#page171)

dummy encoding [173](#ch08.xhtml#page173), [174](#ch08.xhtml#page174)

label coding [171](#ch08.xhtml#page171), [172](#ch08.xhtml#page172)

one-hot coding [172](#ch08.xhtml#page172), [173](#ch08.xhtml#page173)

cbind() [91](#ch04.xhtml#page91)

chi-square test [186](#ch09.xhtml#page186)

class [37](#ch02.xhtml#page37)

dates and times [38](#ch02.xhtml#page38), [39](#ch02.xhtml#page39)

factors [39](#ch02.xhtml#page39)\-[41](#ch02.xhtml#page41)

classification trees [225](#ch11.xhtml#page225)

building [226](#ch11.xhtml#page226)\-[229](#ch11.xhtml#page229)

click-through rate (CTR) [16](#ch01.xhtml#page16)

clustering [200](#ch10.xhtml#page200), [231](#ch11.xhtml#page231)

k-means clustering [231](#ch11.xhtml#page231)

comma separated values (CSV) files [49](#ch02.xhtml#page49)

complete case deletion [75](#ch03.xhtml#page75)

conditional probability [184](#ch09.xhtml#page184)

confusion matrix [217](#ch11.xhtml#page217)

correlation [188](#ch09.xhtml#page188), [189](#ch09.xhtml#page189)

covariance [188](#ch09.xhtml#page188)

cov() function [188](#ch09.xhtml#page188)

D

data

arranging [64](#ch03.xhtml#page64), [65](#ch03.xhtml#page65)

columns, adding [65](#ch03.xhtml#page65), [66](#ch03.xhtml#page66)

de-duplicating [63](#ch03.xhtml#page63)

evidence, looking for [9](#ch01.xhtml#page9), [10](#ch01.xhtml#page10)

hypotheses, making [9](#ch01.xhtml#page9)

process of approaching [7](#ch01.xhtml#page7)

questions to ask [8](#ch01.xhtml#page8)

reproducibility and consistency, checking [9](#ch01.xhtml#page9)

DataFrame [42](#ch02.xhtml#page42)

data merging [90](#ch04.xhtml#page90)

data binding [90](#ch04.xhtml#page90), [91](#ch04.xhtml#page91)

data saving, in R

as binary file [50](#ch02.xhtml#page50)

as CSV file [49](#ch02.xhtml#page49), [50](#ch02.xhtml#page50)

as text file [50](#ch02.xhtml#page50)

data science [2](#ch01.xhtml#page2)\-[5](#ch01.xhtml#page5)

communication [239](#ch12.xhtml#page239), [240](#ch12.xhtml#page240)

required analytical skills [10](#ch01.xhtml#page10), [11](#ch01.xhtml#page11)

data science career growth [236](#ch12.xhtml#page236)

communication [239](#ch12.xhtml#page239), [240](#ch12.xhtml#page240)

data science job search [242](#ch12.xhtml#page242)

data storytelling [240](#ch12.xhtml#page240)\-[242](#ch12.xhtml#page242)

data visualization [240](#ch12.xhtml#page240)\-[242](#ch12.xhtml#page242)

mathematics [236](#ch12.xhtml#page236), [237](#ch12.xhtml#page237)

ML algorithms [238](#ch12.xhtml#page238)

portfolio building [238](#ch12.xhtml#page238), [239](#ch12.xhtml#page239)

programming essentials [237](#ch12.xhtml#page237)

strong foundation, building [236](#ch12.xhtml#page236)

data science job search

contemplating [242](#ch12.xhtml#page242)

informational interviewing [243](#ch12.xhtml#page243), [244](#ch12.xhtml#page244)

data science portfolio

building [238](#ch12.xhtml#page238), [239](#ch12.xhtml#page239)

data transformation [162](#ch08.xhtml#page162)

data visualization [133](#ch07.xhtml#page133)

associations [149](#ch07.xhtml#page149)

distributions [136](#ch07.xhtml#page136)

proportions [144](#ch07.xhtml#page144)

time series [156](#ch07.xhtml#page156)

data wrangling [79](#ch04.xhtml#page79)

data grouping and summarizing [86](#ch04.xhtml#page86)\-[89](#ch04.xhtml#page89)

grouped data, filtering on [89](#ch04.xhtml#page89), [90](#ch04.xhtml#page90)

pivoting data [80](#ch04.xhtml#page80)

date and time components

modifying [104](#ch05.xhtml#page104)

retrieving [103](#ch05.xhtml#page103)

dates [99](#ch05.xhtml#page99)

creating [100](#ch05.xhtml#page100)

creating, from strings [100](#ch05.xhtml#page100), [101](#ch05.xhtml#page101)

creating, from variables [102](#ch05.xhtml#page102), [103](#ch05.xhtml#page103)

datetime objects

creating [100](#ch05.xhtml#page100)

decision trees [224](#ch11.xhtml#page224)

advantages [225](#ch11.xhtml#page225)

classification trees [225](#ch11.xhtml#page225), [226](#ch11.xhtml#page226)

drawbacks [225](#ch11.xhtml#page225)

regression trees [229](#ch11.xhtml#page229)

structure [224](#ch11.xhtml#page224)

density plot [143](#ch07.xhtml#page143)

descriptive analytics [11](#ch01.xhtml#page11)\-[13](#ch01.xhtml#page13)

descriptive statistics [180](#ch09.xhtml#page180)

measure of central tendency [180](#ch09.xhtml#page180)\-[182](#ch09.xhtml#page182)

measures of dispersion [182](#ch09.xhtml#page182)\-[184](#ch09.xhtml#page184)

diagnostic analytics [14](#ch01.xhtml#page14)\-[16](#ch01.xhtml#page16)

distributions, visualizing [136](#ch07.xhtml#page136)

bar plots [136](#ch07.xhtml#page136)\-[140](#ch07.xhtml#page140)

density plot [143](#ch07.xhtml#page143)

histograms [141](#ch07.xhtml#page141)\-[143](#ch07.xhtml#page143)

dplyr [58](#ch03.xhtml#page58)

columns, renaming [58](#ch03.xhtml#page58)

columns, selecting [58](#ch03.xhtml#page58)\-[60](#ch03.xhtml#page60)

rows, filtering [60](#ch03.xhtml#page60), [61](#ch03.xhtml#page61)

dummy encoding [173](#ch08.xhtml#page173), [174](#ch08.xhtml#page174)

durations [110](#ch05.xhtml#page110)

E

electricity production data

exploring [105](#ch05.xhtml#page105)\-[107](#ch05.xhtml#page107)

entropy [225](#ch11.xhtml#page225), [226](#ch11.xhtml#page226)

equal-width binning [167](#ch08.xhtml#page167), [168](#ch08.xhtml#page168)

essential string manipulations [114](#ch06.xhtml#page114)\-[116](#ch06.xhtml#page116)

changing case [116](#ch06.xhtml#page116), [117](#ch06.xhtml#page117)

concatenating strings [122](#ch06.xhtml#page122)

length calculations [117](#ch06.xhtml#page117), [118](#ch06.xhtml#page118)

padding [121](#ch06.xhtml#page121)

substrings, extracting [123](#ch06.xhtml#page123)

substrings, replacing [118](#ch06.xhtml#page118), [119](#ch06.xhtml#page119)

unnecessary whitespaces, removing [119](#ch06.xhtml#page119), [120](#ch06.xhtml#page120)

exploratory data analysis (EDA) [53](#ch03.xhtml#page53), [54](#ch03.xhtml#page54)

F

F1 score [218](#ch11.xhtml#page218)

factors

working with [66](#ch03.xhtml#page66)\-[68](#ch03.xhtml#page68)

feature clipping [169](#ch08.xhtml#page169), [170](#ch08.xhtml#page170)

feature engineering [159](#ch08.xhtml#page159)\-[162](#ch08.xhtml#page162)

foundational models [201](#ch10.xhtml#page201)

functions [44](#ch02.xhtml#page44)

e-commerce [44](#ch02.xhtml#page44), [45](#ch02.xhtml#page45)

finance [46](#ch02.xhtml#page46)

marketing [45](#ch02.xhtml#page45), [46](#ch02.xhtml#page46)

G

Gapminder dataset

defining [55](#ch03.xhtml#page55)\-[57](#ch03.xhtml#page57)

generative AI [201](#ch10.xhtml#page201)

ggplot2 [134](#ch07.xhtml#page134)

creating [135](#ch07.xhtml#page135)

Gini index [225](#ch11.xhtml#page225)

grouped data [89](#ch04.xhtml#page89), [90](#ch04.xhtml#page90)

columns, adding [90](#ch04.xhtml#page90)

H

help pages, R [47](#ch02.xhtml#page47)

high-bias model [230](#ch11.xhtml#page230)

high variance model [230](#ch11.xhtml#page230)

histograms [141](#ch07.xhtml#page141)\-[143](#ch07.xhtml#page143)

I

imputations [76](#ch03.xhtml#page76)

for non-time series problems [77](#ch03.xhtml#page77)

for time series problems [77](#ch03.xhtml#page77)

inferential statistics [185](#ch09.xhtml#page185)

information gain [226](#ch11.xhtml#page226)

inner join [94](#ch04.xhtml#page94)

integrated development environment (IDE) [23](#ch02.xhtml#page23)

International Energy Agency (IEA) [105](#ch05.xhtml#page105)

interquartile range (IQR) [149](#ch07.xhtml#page149)

intervals [112](#ch05.xhtml#page112)

J

joins [92](#ch04.xhtml#page92)

inner join [94](#ch04.xhtml#page94)

left join [95](#ch04.xhtml#page95), [96](#ch04.xhtml#page96)

outer join [95](#ch04.xhtml#page95)

right join [96](#ch04.xhtml#page96)

K

key performance indicators (KPIs) [197](#ch10.xhtml#page197)

k-means clustering [231](#ch11.xhtml#page231), [232](#ch11.xhtml#page232)

advantages [232](#ch11.xhtml#page232), [233](#ch11.xhtml#page233)

optimal number of clusters, finding [232](#ch11.xhtml#page232)

L

label encoding [171](#ch08.xhtml#page171), [172](#ch08.xhtml#page172)

large language models (LLMs) [201](#ch10.xhtml#page201)

left join [95](#ch04.xhtml#page95)

likelihood function [216](#ch11.xhtml#page216)

linear algebra [236](#ch12.xhtml#page236)

linear regression [208](#ch11.xhtml#page208), [209](#ch11.xhtml#page209)

data splitting [209](#ch11.xhtml#page209), [210](#ch11.xhtml#page210)

ETA prediction [212](#ch11.xhtml#page212)\-[215](#ch11.xhtml#page215)

evaluation metrics [211](#ch11.xhtml#page211)

line chart

for visualizing time series [156](#ch07.xhtml#page156), [157](#ch07.xhtml#page157)

list [41](#ch02.xhtml#page41)

logistic regression [215](#ch11.xhtml#page215), [216](#ch11.xhtml#page216)

evaluation metrics [217](#ch11.xhtml#page217), [218](#ch11.xhtml#page218)

likelihood function [216](#ch11.xhtml#page216), [217](#ch11.xhtml#page217)

limitations of linear models [223](#ch11.xhtml#page223)

loan defaults, predicting [218](#ch11.xhtml#page218)\-[223](#ch11.xhtml#page223)

lubridate [103](#ch05.xhtml#page103)

M

machine learning (ML) [191](#ch10.xhtml#page191)

benefits [193](#ch10.xhtml#page193)

foundations [192](#ch10.xhtml#page192)

matrices [34](#ch02.xhtml#page34), [35](#ch02.xhtml#page35)

maximum likelihood estimation (MLE) [217](#ch11.xhtml#page217)

Mean Absolute Error (MAE) [211](#ch11.xhtml#page211)

Mean Absolute Percentage Error (MAPE) [211](#ch11.xhtml#page211)

Mean Squared Error (MSE) [211](#ch11.xhtml#page211)

measure of central tendency [180](#ch09.xhtml#page180)\-[182](#ch09.xhtml#page182)

measures of dispersion [182](#ch09.xhtml#page182)

merge() function [92](#ch04.xhtml#page92)

min-max scaling [165](#ch08.xhtml#page165)

missing at random (MAR) [72](#ch03.xhtml#page72)

missing completely at random (MCAR) [72](#ch03.xhtml#page72)

missing not at random (MNAR) [72](#ch03.xhtml#page72)

missing values

deleting [75](#ch03.xhtml#page75)

detecting, with naniar library [70](#ch03.xhtml#page70)\-[72](#ch03.xhtml#page72)

entire columns, dropping [76](#ch03.xhtml#page76)

handling [68](#ch03.xhtml#page68), [69](#ch03.xhtml#page69)

imputations [76](#ch03.xhtml#page76)

listwise deletion [75](#ch03.xhtml#page75)

reasons [72](#ch03.xhtml#page72)\-[74](#ch03.xhtml#page74)

treating [74](#ch03.xhtml#page74)

ML algorithms [238](#ch12.xhtml#page238)

challenges [201](#ch10.xhtml#page201)\-[203](#ch10.xhtml#page203)

ML lifecycle [206](#ch11.xhtml#page206)

phases [207](#ch11.xhtml#page207), [208](#ch11.xhtml#page208)

ML model training [205](#ch11.xhtml#page205)

ML problem framing [193](#ch10.xhtml#page193)\-[197](#ch10.xhtml#page197)

ML systems [197](#ch10.xhtml#page197)

generative AI [201](#ch10.xhtml#page201)

reinforcement learning (RL) [201](#ch10.xhtml#page201)

supervised learning [197](#ch10.xhtml#page197)

unsupervised learning [200](#ch10.xhtml#page200)

mutate() [65](#ch03.xhtml#page65)

N

normalization [165](#ch08.xhtml#page165)

Not a Number (NaN) [68](#ch03.xhtml#page68)

numeric data transformation [162](#ch08.xhtml#page162), [163](#ch08.xhtml#page163)

binning [166](#ch08.xhtml#page166), [167](#ch08.xhtml#page167)

feature clipping [169](#ch08.xhtml#page169), [170](#ch08.xhtml#page170)

min-max scaling [165](#ch08.xhtml#page165)

Z-score scaling [163](#ch08.xhtml#page163)\-[165](#ch08.xhtml#page165)

O

object [28](#ch02.xhtml#page28)

objects in R [28](#ch02.xhtml#page28), [29](#ch02.xhtml#page29)

arrays [35](#ch02.xhtml#page35)

class [37](#ch02.xhtml#page37), [38](#ch02.xhtml#page38)

DataFrames [42](#ch02.xhtml#page42), [43](#ch02.xhtml#page43)

lists [41](#ch02.xhtml#page41), [42](#ch02.xhtml#page42)

matrices [34](#ch02.xhtml#page34), [35](#ch02.xhtml#page35)

vectors [29](#ch02.xhtml#page29), [32](#ch02.xhtml#page32)

one-hot encoding [172](#ch08.xhtml#page172), [173](#ch08.xhtml#page173)

ordinal encoding [172](#ch08.xhtml#page172)

Organization for Economic Co-operation and Development (OECD) [105](#ch05.xhtml#page105)

outer join [95](#ch04.xhtml#page95)

P

padding [121](#ch06.xhtml#page121)

pearson chi-square test [186](#ch09.xhtml#page186)

periods [111](#ch05.xhtml#page111)

pie chart [144](#ch07.xhtml#page144)

creating [145](#ch07.xhtml#page145)\-[147](#ch07.xhtml#page147)

pipe operator [61](#ch03.xhtml#page61), [62](#ch03.xhtml#page62)

pivoting data

loading [82](#ch04.xhtml#page82), [83](#ch04.xhtml#page83)

long and wide format data [80](#ch04.xhtml#page80)\-[82](#ch04.xhtml#page82)

long to wide format data [85](#ch04.xhtml#page85), [86](#ch04.xhtml#page86)

wide to long format data [83](#ch04.xhtml#page83), [84](#ch04.xhtml#page84)

population sampling [176](#ch09.xhtml#page176), [177](#ch09.xhtml#page177)

simple random sampling [177](#ch09.xhtml#page177)

precision [217](#ch11.xhtml#page217)

predictive analytics [16](#ch01.xhtml#page16)\-[18](#ch01.xhtml#page18)

prescriptive analytics [18](#ch01.xhtml#page18), [19](#ch01.xhtml#page19)

Principal Component Analysis (PCA) [236](#ch12.xhtml#page236)

probability [175](#ch09.xhtml#page175), [184](#ch09.xhtml#page184)

conditional probability [184](#ch09.xhtml#page184), [185](#ch09.xhtml#page185)

probability theory [237](#ch12.xhtml#page237)

programming essentials [237](#ch12.xhtml#page237)

Git [238](#ch12.xhtml#page238)

ML implementation [237](#ch12.xhtml#page237)

Python [237](#ch12.xhtml#page237)

R [237](#ch12.xhtml#page237)

software development best practices [238](#ch12.xhtml#page238)

SQL [237](#ch12.xhtml#page237)

proportions, visualizing [144](#ch07.xhtml#page144)

pie charts [144](#ch07.xhtml#page144)\-[147](#ch07.xhtml#page147)

stacked bar plots [147](#ch07.xhtml#page147), [148](#ch07.xhtml#page148)

Q

quantifiers [126](#ch06.xhtml#page126)

quantile binning [168](#ch08.xhtml#page168)

R

R [22](#ch02.xhtml#page22)

as calculator [24](#ch02.xhtml#page24), [25](#ch02.xhtml#page25)

best practices [51](#ch02.xhtml#page51)

built-in datasets, accessing [49](#ch02.xhtml#page49)

conventions [51](#ch02.xhtml#page51)

data loading [47](#ch02.xhtml#page47), [48](#ch02.xhtml#page48)

data loading, from other packages [49](#ch02.xhtml#page49)

data saving [49](#ch02.xhtml#page49)

help pages [47](#ch02.xhtml#page47)

logical operators [32](#ch02.xhtml#page32)

objects [28](#ch02.xhtml#page28), [29](#ch02.xhtml#page29)

packages [26](#ch02.xhtml#page26)\-[28](#ch02.xhtml#page28)

vectors [29](#ch02.xhtml#page29)

working directories [28](#ch02.xhtml#page28)

range [182](#ch09.xhtml#page182)

rbind() [90](#ch04.xhtml#page90)

recall [218](#ch11.xhtml#page218)

regression trees [229](#ch11.xhtml#page229)

regular expressions [123](#ch06.xhtml#page123), [124](#ch06.xhtml#page124)

greedy and non-greedy matching [126](#ch06.xhtml#page126), [127](#ch06.xhtml#page127)

grouping [125](#ch06.xhtml#page125), [126](#ch06.xhtml#page126)

ingredients [124](#ch06.xhtml#page124)

patterns, detecting [127](#ch06.xhtml#page127)\-[131](#ch06.xhtml#page131)

patterns, extracting [127](#ch06.xhtml#page127)\-[131](#ch06.xhtml#page131)

reinforcement learning (RL) [201](#ch10.xhtml#page201)

reshape2 package [82](#ch04.xhtml#page82)

right join [96](#ch04.xhtml#page96)

Root Mean Squared Error (RMSE) [211](#ch11.xhtml#page211)

Root Mean Squared Logarithmic Error (RMSLE) [211](#ch11.xhtml#page211)

RStudio interfaces [22](#ch02.xhtml#page22), [23](#ch02.xhtml#page23)

keyboard shortcuts [25](#ch02.xhtml#page25), [26](#ch02.xhtml#page26)

S

scatter plot [153](#ch07.xhtml#page153)\-[155](#ch07.xhtml#page155)

search engine optimization (SEO) [115](#ch06.xhtml#page115)

simple random sampling (SRS) [177](#ch09.xhtml#page177)

stratified sampling [178](#ch09.xhtml#page178)\-[180](#ch09.xhtml#page180)

without replacement [178](#ch09.xhtml#page178)

with replacement [177](#ch09.xhtml#page177)

stacked bar plots [147](#ch07.xhtml#page147), [148](#ch07.xhtml#page148)

standard deviation [183](#ch09.xhtml#page183)

standardization [163](#ch08.xhtml#page163)

statistical hypothesis testing [185](#ch09.xhtml#page185)\-[188](#ch09.xhtml#page188)

statistics [175](#ch09.xhtml#page175), [237](#ch12.xhtml#page237)

str\_c() function [122](#ch06.xhtml#page122)

str\_extract\_all function [130](#ch06.xhtml#page130)

str\_extract function [128](#ch06.xhtml#page128)

str\_extract() function [126](#ch06.xhtml#page126)

str\_length() function [118](#ch06.xhtml#page118)

str\_pad() function [121](#ch06.xhtml#page121)

str\_replace\_all() function [119](#ch06.xhtml#page119)

str\_sub() function [123](#ch06.xhtml#page123)

str\_trim() function [119](#ch06.xhtml#page119)

supervised learning [197](#ch10.xhtml#page197), [198](#ch10.xhtml#page198)

classification models [199](#ch10.xhtml#page199), [200](#ch10.xhtml#page200)

regression models [198](#ch10.xhtml#page198)

T

times [99](#ch05.xhtml#page99)

time series

visualizing, with line chart [156](#ch07.xhtml#page156), [157](#ch07.xhtml#page157)

transactions [92](#ch04.xhtml#page92)

t-test [186](#ch09.xhtml#page186)

U

unsupervised learning [200](#ch10.xhtml#page200)

V

validation set [210](#ch11.xhtml#page210)

var() function [183](#ch09.xhtml#page183)

variance [182](#ch09.xhtml#page182), [183](#ch09.xhtml#page183), [230](#ch11.xhtml#page230)

vectors [29](#ch02.xhtml#page29)

character vector [30](#ch02.xhtml#page30)

logical vector [31](#ch02.xhtml#page31)

numeric vector [29](#ch02.xhtml#page29), [30](#ch02.xhtml#page30)

W

Wholesale Customers Dataset [86](#ch04.xhtml#page86)

within-cluster sum of squares (WCSS) [232](#ch11.xhtml#page232)

Z

Z-score scaling [163](#ch08.xhtml#page163)\-[165](#ch08.xhtml#page165)

z-test [186](#ch09.xhtml#page186)