# Exercises

Data can be represented in different ways, and the representation used will change its utility. Text data cannot be directly used by a model; it needs to be converted to a quantitative form. We studied the count vectorizer, which can be used to represent a set of documents as a term-document matrix. One-hot encoding can convert categorical data to a vector indicating the variable's level. Some transformations, such as binarization, work by accentuating certain parts of the data. Discretization converts a continuous variable into discrete buckets, which sometimes yields a powerful predictor.

It takes experimentation to discover the best predictors. Once they are, it is useful to save the code and save the predictors. Transforming data can be resource intensive it is best not to repeat valuable work. Additionally, the transformed data can be used by others when helpful.

The sklearn module has functions that make data transformation easier, and we reviewed small examples. Additional resources on data transformation can be found in the course repo in this folder:

semester1/week09_10_transform

It is helpful to be a “collector” of transforms, and this can be done by looking on the web and else to find interesting and useful approaches. In the next chapter, we will learn techniques and tools for exploratory data analysis. This will allow us to investigate the cleaned and transformed data.

# 10.6 Exercises

Exercises with solutions are marked with §. Solutions can be found in the book_materials folder of the course repo at:

https://github.com/PredictionNN/intro_data_science_course/

+   1. Provide two reasons why transforming raw data can be beneficial.
2. § You are deciding between the use of a 5-day moving average and a 30-day moving average. Explain how smoothing and the lag effect will differ between the two.
3. Explain winsoring and trimming are different.
4. § What is the order of magnitude difference between five thousand and two billion?
5. § What is the order of magnitude difference between 1/10 and 100,000?
6. Give two instances where large differences in order of magnitude can cause trouble.