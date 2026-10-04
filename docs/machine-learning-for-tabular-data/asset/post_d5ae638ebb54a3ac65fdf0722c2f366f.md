
In sum, generative AI is not the solution when dealing with tabular data, not only due to performance reasons but also for crucial aspects, such as

- Cost—Generative AI models often require intensive GPU resources, leading to higher operational costs.
- Scalability—The resource-intensive nature of generative AI models, particularly their reliance on GPUs, can hinder scalability.
- Latency and throughput—Larger models tend to increase processing time per request, affecting latency and throughput.
- Bias—Generative AI may inherit biases from the data they were trained on, potentially perpetating or amplifying biases.
- Flexibility—Adapting generative AI models to custom tasks often necessitates extensive retraining, limiting their flexibility.
- Determinism—The inherent complexity of generative AI models can make it challenging to control and predict their output, affecting determinism.
- Explainability—The complexity of generative AI models can hinder explainability, making it difficult to understand how they operate and produce results.

Acknowledging some limitations of generative AI to handle tabular data problems, we will focus on the classical machine learning and deep learning techniques for learning from tabular data and on how to prepare this data for analysis correctly and properly. However, we will also reserve some space to deal with generative AI tools such as ChatGPT, Google Gemini, and Gemini for Google Cloud because we recognize generative AI’s transformative force in the tabular data field. Based on our experience in the field, we do not foresee any replacement by LLMs or other generative tools of the classical machine learning algorithms or the deep architecture specialized in tabular data because of the advantages that consolidated tools offer, both in terms of performance and control. Instead, we recognize LLMs and other generative AI models can support and enhance tabular data processing, analysis, and modeling, helping practitioners become more proficient and performative in their tabular data projects.

# Summary

- Tabular data is organized in rows and columns, such as data in CSV files or relational database tables.
- Structured data is sometimes used as an alternative term for tabular data, but it is a broader concept, including JSON formatted data.
- Tabular data makes up a small portion of all the digital data in the world, but it has an enormous effect on our lives.
- Compared to other types of data (e.g., images, video, text, audio), the type of data that most jobs revolve around tabular data, so learning how to efficiently apply machine learning/deep learning to tabular data is a useful skill that many people can apply to their jobs.
- In this book, we simply refer to machine learning approaches excluding neural networks (going from linear regressions to gradient boosting methods) as classical machine learning or just machine learning to distinguish them from deep learning.
- Compared to deep learning with other types of data (e.g., images, video, text, audio), deep learning with tabular data gets little attention from academic researchers.
- Conventional wisdom is to use a gradient boosting approach like XGBoost with tabular data.
- There's a lively debate in social media about whether or not there is a place for deep learning in solving problems involving tabular data. In this book, we don't pick a side in this debate. Instead, we try to objectively describe why you would use machine learning or deep learning for a given tabular data problem and the best practices to use for each approach.
- Tabular data has some unique characteristics not shared by other types of data, such as these characteristics include a lack of large open-source datasets that represent the kind of tabular datasets that you would see in real-world business problems.
- Generative AI, especially LLMs, significantly affects how AI is perceived, diffused across individuals and organizations, and utilized. LLMs can help automate various tasks related to tabular data analysis and modeling, especially when related to textual inputs and outputs.

# Exploring tabular datasets

This chapter covers

- Row and column characteristics in a tabular dataset
- Possible pathologies and remedies for tabular datasets
- Finding tabular data externally on the internet and internally in organizations
- Exploring data to solve common problems in tabular data

Tabular data may consist of practically anything—from low-level scientific research to consumer behavior on a website to the statistics in your fantasy sports league. In the end, though, the commodities in tabular data prevail over differences, and you can achieve most of your data analysis job just by applying standard approaches and tools even without a lot of domain expertise.

In this chapter, we'll look at how to gather and prepare tabular datasets. We'll also take on a practical data analysis exploration that shows the steps you can take to look at data from different viewpoints: by rows, by columns, under the light of the relationship between features, and considering their overall distribution in the dataset. For that example, we use a toy dataset, the Auto MPG Data Set, dataset freely available over the UCI Machine Learning website (https://archive.ics.uci.edu/dataset/9/auto+mpg).

## 2.6 Row and column characteristics

Depending on the domain, it is incredible how variety you will find in tabular data. That is because tabular data is the rule, not the exception, in the world of data, and has been true since the very beginning. Tabular data has been collected for thousands of years into tables and records, from grain accounting in ancient Egypt to parish births, weddings, and deaths in medieval Europe. It wasn't until the 1960s that we began collecting data in computerized databases, which gave the term more electronic connotation. The widespread adoption of relational databases in the 1970s has popularized data, making it ubiquitous and for every possible application. In relational databases, tables can be built by the values of specific columns as joining keys. Such innovation allowed computers to store more information in less disk space, guaranteeing the technology's success and widespread diffusion.

You can look at data repositories or science competitions, such as Kaggle, which routinely feature tabular data competitions to give you an idea of the current sheer variety of tabular data. For instance, in the last two years, Kaggle organized the Tabular Playground Series (https://url.com/), a series of competitions inspired by most common machine learning problems involving tabular datasets and using synthetic data generated by generative AI, as we will discuss more in the chapter. The Tabular Playground competitions use generated data, the examples and the original data they took inspiration are from real-world examples such as

- Probability and amount of insurance claims
- Loan defaults in the banking sector
- Product testing
- E-commerce sales
- Environment sensor data
- Biological and genomic data
- Ecological measurements

However, despite the variety of real-world applications and underlying knowledge domains, every tabular dataset shares the same structure of a matrix of rows and columns with values in numeric, time or dates, and textual forms. All tabular datasets, regardless of their features. While domain knowledge is essential for devising optimal feature engineering for predictive algorithms, the basic structure of tabular data remains consistent across all domains. Such universality justifies the need for a book.

Diving into details, in a data table, also called dataset, you have rows of values, and each row represents a unit, which can be mentioned as a statistical unit or observation. If you are analyzing DNA samples, for example, each row represents a sample. If you are analyzing industrial products, each row will be a product. In these instances, the data exhibits distinctive characteristics that deviate from the assumption of independence and identical distribution because the samples derive from specific groups (stores or store classes).

### 2.6.1 The ideal criteria for tabular rows

The only limit to remember for rows in tabular dataset is that examples should be independent unless you are working with time predictions (time series) or other time-related problems. That's the IID principle that you may have heard before. IID is an acronym for “independent and identically distributed,” meaning that your samples should have been drawn independently, where each drawing doesn't influence the subsequent ones. Identically, means that you always draw in the same way from the same data distribution.

Let's consider a simple example IID: a coin flip. Each time we flip a coin, the outcome is independent of all the previous flips, and the probability of getting heads or tails is the same for each flip. In other words, the coin flips are identically distributed, according Bernoulli distribution. If we were to generate a dataset by flipping the same coin repeatedly, the resulting data would be IID. The property of being identically distributed allows us to simplify the modeling and analysis of the data. For example, it allows us to sample the data when creating cross-validation folds. It allows us to assume that algorithms will not memorize and replicate the order of the data presented. Typical examples of non-IID sales from multiple stores, where the same store tend to be very correlated and not necessarily with other stores' dynamics or survey data, where each class presents similar characteristics due to shared interests or experiences, introducing non-IID characteristics into the data.
