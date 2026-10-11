
# Detecting errors in larger data sets

Detecting errors in larger data sets against a code book or against standardized values can be done with the help of set operations. A **code book** is a description of your data, a form of metadata. It contains things such as the number of variables per observation, the number of observations, and what each encoding within a variable means. (For instance “0” equals “negative”, “5” stands for “very positive”.) A code book also tells the type of data you’re looking at: is it hierarchical, graph, something else?

You look at those values that are present in set A but not in set B. These are values that should be corrected. It’s no coincidence that **sets** are the data structure that we’ll use when we’re working in code. It’s a good habit to give your data structures additional thought; it can save work and improve the performance of your program.

If you have multiple values to check, it’s better to put them from the code book into a table and use a difference operator to check the discrepancy between both tables.

## Different units of measurement

When integrating two data sets, you have to pay attention to their respective units of measurement. An example of this would be when you study the prices of gasoline in the world. To do this you gather data from different data providers. Data sets can contain prices per gallon and others can contain prices per liter. A simple conversion will do the trick in this case.

## Different levels of aggregation

Having different levels of aggregation is similar to having different types of measurement. An example of this would be a data set containing data per week versus one containing data per work week. This type of error is generally easy to detect, and **summarizing** (or the inverse, **expanding**) the data sets will fix it.

After cleaning the data errors, you combine information from different data sources. But before we tackle this topic we’ll take a little detour and stress the importance of cleaning data as early as possible.

## 2.4.2. Correct errors as early as possible

A good practice is to mediate data errors as early as possible in the data collection chain and to fix as little as possible inside your program while fixing the origin of the problem. Retrieving data is a difficult task, and organizations spend millions of dollars on it in the hope of making better decisions. The data collection process is error-prone, and in a big organization it involves many steps and teams.

Data should be cleansed when acquired for many reasons:

*   Not everyone spots the data anomalies. Decision-makers may make costly mistakes on information based on incorrect data from applications that fail to correct for the faulty data.
*   If errors are not corrected early on in the process, the cleansing will have to be done for every project that uses that data.
*   Data errors may point to a business process that isn’t working as designed. For instance, both authors worked at a retailer in the past, and they designed a couponing system to attract more people and make a higher profit. During a data science project, we discovered clients who abused the couponing system and earned money while purchasing groceries. The goal of the couponing system was to stimulate cross-selling, not to give products away for free. This flaw cost the company money and nobody in the company was aware of it. In this case the data wasn’t technically wrong but came with unexpected results.
*   Data errors may point to defective equipment, such as broken transmission lines and defective sensors.
*   Data errors can point to bugs in software or in the integration of software that may be critical to the company. While doing a small project at a bank we discovered that two software applications used different local settings. This caused problems with numbers greater than 1,000. For one app the number 1.000 meant one, and for the other it meant one thousand.

Fixing the data as soon as it’s captured is nice in a perfect world. Sadly, a data scientist doesn’t always have a say in the data collection and simply telling the IT department to fix certain things may not make it so. If you can’t correct the data at the source, you’ll need to handle it inside your code. Data manipulation doesn’t end with correcting mistakes; you still need to combine your incoming data.

As a final remark: always keep a copy of your original data (if possible). Sometimes you start cleaning data but you’ll make mistakes: impute variables in the wrong way, delete outliers that had interesting additional information, or alter data as the result of an initial misinterpretation. If you keep a copy you get to try again. For “flowing data” that’s manipulated at the time of arrival, this isn’t always possible and you’ll have accepted a period of tweaking before you get to use the data you are capturing. One of the more difficult things isn’t the data cleansing of individual data sets however, it’s combining different sources into a whole that makes more sense.

## 2.4.3. Combining data from different data sources

Your data comes from several different places, and in this substep we focus on integrating these different sources. Data varies in size, type, and structure, ranging from databases and Excel files to text documents.

We focus on data in table structures in this chapter for the sake of brevity. It’s easy to fill entire books on this topic alone, and we choose to focus on the data science process instead of presenting scenarios for every type of data. But keep in mind that other types of data sources exist, such as key-value stores, document stores, and so on, which we’ll handle in more appropriate places in the book.

### The different ways of combining data

You can perform two operations to combine information from different data sets. The first operation is **joining**: enriching an observation from one table with information from another table. The second operation is **appending** or **stacking**: adding the observations of one table to those of another table.

When you combine data, you have the option to create a new physical table or a virtual table by creating a view. The advantage of a view is that it doesn’t consume more disk space. Let’s elaborate a bit on these methods.

### Joining tables

Joining tables allows you to combine the information of one observation found in one table with the information that you find in another table. The focus is on enriching a single observation. Let’s say that the first table contains information about the purchases of a customer and the other table contains information about the region where your customer lives. Joining the tables allows you to combine the information so that you can use it for your model, as shown in **[figure 2.7](https://livebook.manning.com/book/introducing-data-science/chapter-2/ch02fig07)**.

![](image_rsrc9PB.jpg)

**Fig.2.7** Joining two tables on the Item and Region keys

To join tables, you use variables that represent the same object in both tables, such as a date, a country name, or a Social Security number. These common fields are known as **keys**. When these keys also uniquely define the records in the table they are called **primary keys**. One table may have buying behavior and the other table may have demographic information on a person. In **[figure 2.7](https://livebook.manning.com/book/introducing-data-science/chapter-2/ch02fig07)** both tables contain the client name, and this makes it easy to enrich the client expenditures with the region of the client. People who are acquainted with Excel will notice the similarity with using a lookup function.

The number of resulting rows in the output table depends on the exact join type that you use. We introduce the different types of joins later in the book.

### Appending tables
