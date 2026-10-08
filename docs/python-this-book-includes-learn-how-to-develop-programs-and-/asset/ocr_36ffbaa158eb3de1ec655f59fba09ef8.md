occur with use of specific OS and hardware settings (for example, “Linux on a Raspberry Pi”). Developing “NumPy” and “SciPy” from source tends to be complicated (particularly on Windows); therefore, they need to be set up carefully, making sure the optimized execution of linear algebra routines is achievable.

# Importing the Data Set

To import the "Sales_Win_Loss data set from IBM’s Watson repository," the first step is importing the "Pandas" module using `import pandas as pd.`

Then, we leverage a variable URL as “https://community.watsonanalytics.com/wp/content/uploads/2015/04/WA_Fn-UseC_Sales-Win-Loss.csv” so that the data set can be stored and downloaded on the URL.

Now, `read_csv() as sales_data = pd.read_csv(url)` technique will be used to read the "CSV or comma-separated values" file, which is supplied by the Pandas module. The CSV file will then be converted into a Pandas data framework with the return variable as "sales_data," where the framework will be stored.

For new ‘Pandas’ users, the `pd.read_csv()` technique in the code mentioned above will generate a tabular data structure called “data framework”, where an index for each row is contained in the first column, and the label/name for each column in the first row are the names taken from the data set located in the initial column. In the code snippet, the "sales data" variable results in a table depicted in the picture below.

![](bbox=[0.318, 0.715, 0.682, 0.856])