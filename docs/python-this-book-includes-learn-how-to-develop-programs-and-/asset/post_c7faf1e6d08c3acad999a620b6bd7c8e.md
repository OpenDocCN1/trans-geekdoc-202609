
occur with use of specific OS and hardware settings (for example, “Linux on a Raspberry Pi”). Developing “NumPy” and “SciPy” from source tends to be complicated (particularly on Windows); therefore, they need to be set up carefully, making sure the optimized execution of linear algebra routines is achievable.

## Importing the Data Set

To import the "Sales_Win_Loss data set from IBM’s Watson repository," the first step is importing the "Pandas" module using `import pandas as pd.`

Then, we leverage a variable URL as “https://community.watsonanalytics.com/wp/content/uploads/2015/04/WA_Fn-UseC_Sales-Win-Loss.csv” so that the data set can be stored and downloaded on the URL.

Now, `read_csv() as sales_data = pd.read_csv(url)` technique will be used to read the "CSV or comma-separated values" file, which is supplied by the Pandas module. The CSV file will then be converted into a Pandas data framework with the return variable as "sales_data," where the framework will be stored.

For new ‘Pandas’ users, the `pd.read_csv()` technique in the code mentioned above will generate a tabular data structure called “data framework”, where an index for each row is contained in the first column, and the label/name for each column in the first row are the names taken from the data set located in the initial column. In the code snippet, the "sales data" variable results in a table depicted in the picture below.

![](img/43582740ac1227a817786ef73e0f3772_133_0.png)

In the above diagram, the individual column is represented by the “row0, row1, row2,” and the names for the features of the data set or individual columns are represented by “col0, col1, col2”.

With this step, you have successfully stored a copy of the data set and transformed it into a “Pandas” framework!

Now, using the (head() as Sales_data.head()) technique, the records of the data framework can be displayed as shown below to get a “feel” of the information contained in the data set.

![](img/43582740ac1227a817786ef73e0f3772_134_0.png)

## Data Exploration

We can quickly explore the data to understand what information can tell us gathered from it and accordingly to plan a course of action.

In any machine learning project, data exploration tends to be a very critical phase. Even a fast data set exploration can offer significant information that could be easily missed otherwise, and this information can propose significant questions that we can attempt to answer our project.

Some third-party Python libraries will be used to assist us with the processing of the data so that we can efficiently use this data with the powerful algorithms of Scikit-Learn. The same “head() technique that we used to see some initial records of the imported data set in the earlier section can be used here. As a matter of fact, “(head)” is effectively capable of doing much more than displaying data records and customize the “head()” technique to display only a selected record with commands like

“sales_data.head(n=2)”. This command will selectively display the first 2 records of the data set. At a glance, it’s obvious string data is contained in columns such as “Supplies Group” and “Region,” while columns such asOpportunity Result”, “Opportunity Number,” et cetera, are comprised of integer values. It can also be seen that there are unique identifiers for each record in the 'Opportunity Number' column.

Similarly, to display select records from the bottom of the table, the “tail() as sales_data.tail()” can be used.

To view the different data types available in the data set, the Pandas technique “types() as sales_data.types” can be used. With this information, the data columns available in the data framework can be listed with their respective data types. We can figure out, for example, that the “object” data type is in the column “Supplies Subgroup” and the “integer data type” is in the column “Client Size By Revenue.” So, we have an understanding of columns that either contains integer values or string data.

## Data Visualization

At this point, we are through with basic data exploration steps, so we will not attempt to build some appealing plots to portray the information visually and discover other concealed narratives from our data set.

Of all the available Python libraries providing data visualization features; “Seaborn” is one of the best available options, so we will be using the same. Make sure that your python plots module by “Seaborn” has been installed on your system and ready to be used. Now, follow the steps below generate the desired plot for the data set:

- Step 1 – Transfer the module “Seaborn” with the command “import seaborn as sns."
- Step 2 – Transfer the module “Matplotlib” with command “import matplotlib.pyplot as plt."
- Step 3 – Use the command “sns.set(style=whitegrid, color_codes=True)” in setting to white the “background color” of the plot.
- Step 4 - To set the “plot size” for all plots, use command “sns.set(rc={'figure.figsize':(11.7,8.27)})”.
- Step 5 – To generate a “countplot”, use command sns.countplot('Route To Market', data=sales_data, hue ='Opportunity Result’).
- Step 6 – To eliminate the bottom and top margins, use command “sns.despine(offset=10, trim=True)”.
- Step 7 – To display the plot, use using the command “plt.show()”.

![](img/43582740ac1227a817786ef73e0f3772_136_0.png)

Quick recap - The “Seaborn” and “Matplotlib” modules were imported first. Then the {set()} technique was used to define the distinct characteristics of our plots, such as plot style and color. The background of the plot was made white using the code snippet “sns.set(style="whitegrid", color_codes=True).”

Then the plot size define using command “sns.set(rc={'figure.figsize':11.7,8.27}}” that define the plot size as “11.7px and 8.27px”.

Next, the command “sns.countplot('Route To Market',data= sales data, hue='Opportunity Result’) was used to generate the plot. The “countplot()” technique enables the creation of a count plot, which can expose multiple arguments to customize the count plot according to our requirements. As of the first “countplot()” argument, the X-axis was defined as “Route To Market” column from the data set. The next problem concerns the origin of the data set, which would be the "sales_data" data framework we imported earlier. The third argument is the color of the bar graphs that were defined as "blue" representing the "won" column and "green" for the "loss" column.

## Data Pre-processing

By now, you should have a clear understanding of what information is available in the data set. To transform categorical labels from the data set such as “won” and “loss” into numerical values, we will use the “LabelEncoder()” technique.

Let's look at the pictures below to see what we are attempting to accomplish with the “LabelEncoder()” technique. The first image contains “color” column with 3 records, namely “Red,” “Green,” and “Blue.” Using the “LabelEncoder()” technique, the record in the same “color” column can be converted to numerical values, as shown in the second image.

| Color | Color |
|---|---|
| 0 Red | 1 |
| 1 Green | 2 |
| 2 Blue | 3 |

Let's begin the real process now. Using the “fit transform()” technique given by “LabelEncoder(), the categorical column like “Route To Market” can be encoded and converted to those shown above. To know how the encoding is accomplished, let’s go through an example. The code instance below constitutes string data in the form of cities such as [“Paris,” “Paris,” “Tokyo,” “Amsterdam”] that will be encoded into something.

- Step 1 - To import the required module
- Step 3 – To convert the categorical columns into numerical values, use command:

```
encoded_value = le.fit_transform(["Paris", "Paris", "Tokyo", "Amsterdam"])
print(encoded_value)
```

We just transformed our labels for string data into numerical values. The first step was importing the preprocessing module that offers the "LabelEncoder()" technique. Followed by the development of an object representing the "LabelEncoder()" type. Then, the "fit_transform()" function of the object was used to distinguish between the list's distinct classes ["Paris", "Paris", "Tokyo", "Amsterdam"] and output the encoded values of [1120].

The technique of "LabelEncoder()" assigns the numerical values with regards to the classes' alphabetically to the classes, for example, \(A)sterdam was assigned code "0", \(P)aris was assigned code "1" and \(T)okyo was assigned code "2".

## Creating Training and Test subsets

Know the interactions between distinct characteristics and how these characteristics influence the target variable, a collection of information must be learned by a machine learning algorithm. We need to split the complete data set into two subsets to accomplish this. One subset will serve as the training data set, which will be used to train our algorithm to construct machine learning models. The other subset will serve as the test data set, which will be used to test the accuracy of the predictions generate by the machine learning model.

The first phase in this stage is the separation of feature and target variables using the steps below:

- Step 1 – To select data excluding select columns, use command "select columns other than 'Opportunity Number', 'Opportunity Result_cols' = [col for col in sales_data.columns if col not in ['Opportunity Number','Opportunity Result']'"
- Step 2 – To drop these select columns, use the command "dropping 'Opportunity Number' and 'Opportunity Result' columns data = sales_data[cols]"
