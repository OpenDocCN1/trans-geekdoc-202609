
# PYTHON FUNCTIONS AND FILE HANDLING

## Understanding Data Processing

Data processing is the act of changing the nature of data into a form that is more useful and desirable. In other words, it is making data more meaningful and informative. By applying machine learning algorithms, statistical knowledge, and mathematical modeling, one can automate this whole process. The output of this whole process can be in any form like tables, graphs, charts, images, and much more, based on the activity done and the requirements of the machine. This might appear simple, but for big organizations and companies like Facebook, Twitter, UNESCO, and health sector organizations, this whole process has to be carried out in a structured way. The diagram below shows some of the steps that are followed:

![](rsrc116.jpg)

Let’s look in detail at each step:

### Collection

The most important step when getting started with Machine Learning is to ensure that the data available is of great quality. You can collect data from genuine sources such as Kaggle, data.gov.in, and UCI dataset repository. For example, when students are getting ready to take a competitive exam, they always find the best resources to use to ensure they attain good results. Similarly, accurate and high-quality data will simplify the learning process of the model. This means that during the time of testing, the model would output the best results. A great amount of time, capital, and resources are involved in data collection. This means that organizations and researchers have to select the correct type of data which they want to implement or research. For instance, to work on the Facial Expression Recognition requires a lot of images that have different human expressions. A good data will make sure that the results of the model are correct and genuine.

### Preparation

The data collected can be in raw form. Raw data cannot be directly fed into a machine. Instead, something has to be done on the data first. The preparation stage involves gathering data from a wide array of sources, analyzing the datasets, and then building a new data set for additional processing and exploration. Preparation can be done manually or automatically and the data should be prepared in a numerical form to improve the rate of learning of the model.

### Input

Sometimes, data already prepared can be in the form which the machine cannot read, in this case, it has to be converted into readable form. For conversion to take place, it is important for a specific algorithm to be present. To execute this task, intensive computation and accuracy are required. For example, you can collect data through sources like MNIST, audio files, twitter comments, and video clips.

### Processing

In this stage, ML techniques and algorithms are required to execute instructions generated over a large volume of data with accuracy and better computation.

### Output

In this phase, results get procured by the machine in a sensible way such that the user can decide to reference it. Output can appear in the form of videos, graphs, and reports.

### Storage

This is the final stage where the generated output, data model, and any other important information are saved for future use.

## Data Processing in Python

Let’s learn something in python libraries before looking at how you can use Python to process and analyze data. The first thing is to be familiar with some important libraries. You need to know how you can import them into the environment. There are different ways to do this in Python. You can type:

`import math as m`
`from math import *`

In a first way, you define an alias `m` to library `math`. Then you can use different functions from the `math` library by making a reference using an alias `m`. `factorial()`. In the second method, you import the whole namespace in `math`. You can choose to directly apply `factorial()` without inferring to `math`.

**Note:** Google recommends the first method of importing libraries because it will help you tell the origin of the functions.

The list below shows libraries that you’ll need to know where the functions originate from:

- **NumPy**: This stands for Numerical Python. The most advanced feature of NumPy is an n-dimensional array. This library has a standard linear algebra function, advanced random number capability, and tools for integration with other low-level programming languages.
- **SciPy**: It is the shorthand for Scientific Python. SciPy is designed on NumPy. It is among the most important library for different high-level science and engineering modules such as Linear Algebra, Sparse matrices, and Fourier transform.
- **Matplotlib**: This is best applied when you have a lot of graphs which you need to plot. It begins from line plots to heat plots and you can apply the Pylab feature in IPython notebook to ensure plotting features are inline.
- **Pandas**: Best applied in structured data operations and manipulations. It is widely used for data preparation and mining. Pandas were introduced recently to Python and have been very useful in enhancing Python’s application in the data scientist community.
- **scikit-learn**: This is designed for machine learning. It was created on matplotlib, NumPy, and SciPy. This specific library has a lot of efficient tools for machine learning and statistical modeling. That includes regression, classification, clustering, and dimensionality community.
- **StatsModels**: This library is designed for statistical modeling. Statsmodels refers to a Python module which permits users to explore data, approximate statistical models, and implement statistical tests.

### Other libraries

- `Requests` used to access the web.
- `Blaze` used to support the functionality of NumPy and Pandas.
- `Bokeh` used to create dashboards, interactive plots, and data applications on the current web browsers.
- `Seaborn` is used in statistical data visualization.
- Regular expressions that are useful for discovering patterns in a text data
- `NetWorx` and `Igraph` applied to graph data manipulations.

Now that you are familiar with Python fundamentals and crucial libraries, let’s now jump into problem-solving through Python.

### An exploratory analysis in Python with Pandas

If you didn’t know, Pandas is an important data analysis library in Python. This library has been key to improving the application of Python in the data science community. Our example uses Pandas to read a data set from an analytics Vidhya competition, run an exploratory analysis, and create a first categorization algorithm to solve this problem.

Before you can load the data, it is important to know the two major data structures in Pandas. That is `Series` and `DataFrames`.

#### Series and DataFrames

You can think of series as a 1-dimensional labeled array. These labels help you to understand individual elements of this series via labels. A data frame resembles an Excel workbook and contains column names which refer to columns as well as rows that can be accessed by row numbers. The most important difference is that column names and row numbers are referred to as column and row index. Series and data frames create a major data model for Pandas in Python. At first, the datasets have to be read from data frames and different operations can easily be subjected to these columns.

#### Practice data set – Loan Prediction Problem

The following is the description of variables:

![](rsrc117.jpg)

First, start iPython interface in Inline Pylab mode by typing the command below on the terminal:

![](rsrc118.jpg)

#### Import libraries and data set

This chapter will use the following python libraries:

- `NumPy`
- `Matplotlib`
- `Pandas`

Once you have imported the library, you can move on and read the dataset using a function `read_csv()`. Below is how the code will look till this point:

![](rsrc119.jpg)

Notice that the dataset is stored in `"/home/kunal/Downloads/Loan_Prediction/train.csv"`.

Once you read the dataset, you can decide to check a few top rows by using the function `head()`. Next, you can check at the summary of numerical fields by using the `describe()` function.

#### Distribution analysis

Since you are familiar with the basic features of data, this is the time to look at the distribution of different variables. Let’s begin with numeric variables-`ApplicantIncome` and `LoanAmount`.

First, type the commands below to plot the histogram of `ApplicantIncome`:

![](rsrc11A.jpg)

Notice that there are a few extreme values. This is why 50 bins are needed to represent the distribution clearly. The next thing to focus on is the box plot. The box plot for fare is plotted by:

![](rsrc11B.jpg)

This is just a tip of an iceberg when it comes data processing in Python. Let’s look at:

### Techniques for Preprocessing Data in Python

Here are the best techniques for Data Preprocessing in Python.
