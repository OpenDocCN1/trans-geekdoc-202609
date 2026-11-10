
As shown in [Figure 5.3](#c5.xhtml#f5.3), just use the command `import pandas` to obtain Pandas for you. You can validate the same with the `pandas.__version__` command. The same can be seen in [Figure 5.3](#c5.xhtml#f5.3).

It’s easy!

Now the actual learning starts. One should understand the basic point here. As far as Pandas is concerned, the most common and basic data structure is the `Series`. It is the basic building block for the data in tabular format.

### 5.3.2 What Is a Data Frame?

We need structured data for carrying out all the data analytics. We are familiar with SQL (Structured Query Language), right? It is all about rows and columns and makes life easier.

For Data Science and ML with Python, we have something similar called data frames (the dataset has to be converted to data frames for easier access and processing). Here, the data are being visualized as a table, making interpretation much easier.

Pandas Library will help in getting the data frames created so let’s learn the same.

One should remember that the data frame is a 2D data structure. Can we have an example to enhance our understanding? Your first data frame is presented below which will certainly enhance the reader’s understanding of the data frame. We will use the data frames at a later point of this chapter, and this is just a head’s up for information.

![Figure 5.4 A sample data frame (with heterogeneous data inside).](images/fig5.4.jpg)

**Figure 5.4** A sample data frame (with heterogeneous data inside).

Remember:

* We will come across CSV files in many of our ML/DL projects. A CSV file is a Comma Separated Values (CSV) file and is a plain text file that stores data by delimiting data entries with commas.

### 5.3.3 Pandas Series Creation and Indexing

We are going to create the Pandas series first. It is very simple, and we need to have data for the same. We are using the water consumption by an apartment as the data, and we shall build the Pandas series around these data. First step is to import the Pandas, which will mostly be imported as `pd`. Next, one should create an array. Then, the constructor `pd.Series` is to be used to get the series created. The code snippet and the output is presented as [Figure 5.5](#c5.xhtml#f5.5), and it would help the reader to understand the scenario better.

![Figure 5.5 The first Pandas series.](images/fig5.5.jpg)

[**Figure 5.5**](#c5.xhtml#re_f5.5) The first Pandas series.

Now, `water_consumption` is a Pandas series. It’s simple, right? One could also note that it is properly indexed. The given data have been allocated proper indexing through this simple step.

It was a simple piece of code that we have written. It is good to have indexing but is certainly better to have the corresponding dates in place of the index. The simple `pd.date_range` routine would be helpful to accomplish the task. We have six data entries and hence we will get six successive dates created through this step. One should remember that the series is created in the previous step and its name is `water_consumption`. And our series is now indexed differently.

Also, note that the values of the series stayed the same. The index is reassigned to dates and that’s visible from the results, clearly.

![Figure 5.6 Adding date range to the series.](images/fig5.6.jpg)

**Figure 5.6** Adding date range to the series.

### 5.3.4 Operations with the Series – It’s Fun

One can retrieve the values from the series with the index. It is easy and is akin to using a dictionary. One could see the code snippet presented in [Figure 5.7](#c5.xhtml#f5.7) to understand the same.

![Figure 5.7 Select the data by index values.](images/fig5.7.jpg)

[**Figure 5.7**](#c5.xhtml#re_f5.7) Select the data by index values.

The next step is to try with the index position, just like an array. It is also possible. This is not supported by dictionaries. The same is revealed in [Figure 5.8](#c5.xhtml#f5.8).

![Figure 5.8 Select the data by index position.](images/fig5.8.jpg)

[**Figure 5.8**](#c5.xhtml#re_f5.8) Select the data by index position.

Slicing works fine as well. Here is an example, presented in [Figure 5.9,](#c5.xhtml#f5.9) which will make you understand slicing better. The entire January data will be retrieved and is presented.

![Figure 5.9 Select the data by slicing.](images/fig5.9.jpg)

[**Figure 5.9**](#c5.xhtml#re_f5.9) Select the data by slicing.

A series is very versatile and flexible. It can store integers, floats or strings. One can view with ease the data type it stores with the piece of code shown in [Figure 5.10](#c5.xhtml#f5.10). One can see that the data type is an integer.

![Figure 5.10 Find the data type.](images/fig5.10.jpg)

[**Figure 5.10**](#c5.xhtml#re_f5.10) Find the data type.

You can convert the data type with ease too. One can refer to the code presented in [Figure 5.11](#c5.xhtml#f5.11). The conversion of the existing datatype to float has been presented below. This is such a flexibility the users get. `astype` is a series method that can convert the data type.

![Figure 5.11 Datatype conversion.](images/fig5.11.jpg)

[**Figure 5.11**](#c5.xhtml#re_f5.11) Datatype conversion.

Handling missing data is a paramount task with the data. Data imputation is the simplest way experts follow when handling missed data. Imputation is the process of replacing missing data with substituted values and the same is presented in [Figure 5.12](#c5.xhtml#f5.12). Also, the reader could see that `NaN` (Not a Number) is used in the code. It is the Numpy way of conveying that the data are missing. `Series.fillna` is a method to fill the missing values with the given value. One can observe that the invalid data are created first and then it is replaced with zeros.

![Figure 5.12 Imputation.](images/fig5.12.jpg)

[**Figure 5.12**](#c5.xhtml#re_f5.12) Imputation.

Data frames are to be touched on now and the series will be all done. As discussed already, it is two-dimensional in nature and is a collection of series. Remember that – data frames are a collection of series. `Series` is all one-dimensional, whereas data frames are two-dimensional. You can refer to Figure 5.1 to understand what a data frame looks like. Simply, it is a table of data. Let’s learn the data frames.

First, let’s create a dataset. The dataset is in .CSV format. The CSV file (`data.csv`), which has sample data, is presented below for quicker perusal. This is the dataset. [Figure 5.13](#c5.xhtml#f5.13) has the data and one can view the same.

![Figure 5.13 The data set (data.csv).](images/fig5.13.jpg)

[**Figure 5.13**](#c5.xhtml#re_f5.13) The data set (data.csv).

Shall we create data frame from the dataset? [Figure 5.14](#c5.xhtml#f5.14) has the screenshot which shows the way to create the data frame. The file which contains the data is named `data.csv` and the same is used below to create the data frame.

![Figure 5.14 The data frame creation.](images/fig5.14.jpg)

[**Figure 5.14**](#c5.xhtml#re_f5.14) The data frame creation.

It’s time to understand how the data frame can be visualized. The first few entries of the data frame are all displayed with the piece of code snippet below. `df.head(5)` will display the first five entries in the data frame.

![Figure 5.15 The head – first few entries displayed](images/fig5.15.jpg)

**Figure 5.15** The head – first few entries displayed

It is simple to get a quick summary of the data frame. The list will help us in getting the summary as presented in [Figure 5.16](#c5.xhtml#f5.16).

![Figure 5.16 The list to obtain the summary.](images/fig5.16.jpg)

[**Figure 5.16**](#c5.xhtml#re_f5.16) The list to obtain the summary.

The transposing operation can be done with ease with `transpose()` operation. One can see that the transpose operation is completed by transposing Columns as Rows and Rows as Columns, and this is presented below in [Figure 5.17](#c5.xhtml#f5.17). One can view the original data before transpose from [Figure 5.13](#c5.xhtml#f5.13).
