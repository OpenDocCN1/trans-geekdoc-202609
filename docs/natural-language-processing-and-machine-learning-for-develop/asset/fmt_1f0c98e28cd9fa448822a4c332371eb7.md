
\=> Grouped by deck:   embark_town               count nunique size deck     A            15       2   15 B            45       2   47 C            59       3   59 D            33       2   33 E            32       3   32 F            13       3   13 G             4       1    4   \=> Grouped by age (before):        age           count nunique size age     0.42      1       1       1   0.67      1       1    1   0.75      2       1    2   0.83      2       1    2   0.92      1       1    1   ...     ...     ...  ... 70.00     2       1    2   70.50     1       1    1   71.00     2       1    2 74.00     1       1    1 80.00     1       1    1   \[88 rows x 3 columns\]   \=> Grouped by age (after):      age   count nunique size age 0       1       1    1 1       1       1    1 2       3       1    3 3       1       1    1 4       3       1    3 6       1       1    1 11      1       1    1 14      1       1    1 15      1       1    1 60      2       1    2 61      2       1    2 62      1       1    1 63      1       1    1 64      1       1    1 65      2       1    2 70      1       1    1 71      1       1    1 80      1       1    1 

## **Save Data Frames as CSV Files and Zip Files**

[Listing 2.48](#ch02.xhtml#list2.48) displays the contents of save2csv.py that illustrates how to save a Pandas data frame as a CSV file and also as a zip file that contains both the CSV file and the contents of the data frame.

***LISTING 2.48: save2csv.py***

```python
import pandas as pd
df = pd.DataFrame({'fname':'Jane','lname':'Smith','age':25}, 
                  {'fname':'Dave','lname':'Jones','age':35}, 
                  {'fname':'Sara','lname':'Stone','age':45}) 
# save data frame to CSV file:
print("Saving data to save.csv:")
print(df.to_csv("save.csv", index=False))
# save data frame as CSV file in a zip file:
compression_opts = dict(method='zip', archive_name='save2.csv')
df.to_csv('save2.zip', index=False, compression=compression_opts)
```

[Listing 2.48](#ch02.xhtml#list2.48) defines the Pandas data frame `df` that contains three rows of data, with values for the first name, last name, and age of three people. The next code snippet invokes the `to_csv()` method in order to save the contents of `df` to the CSV file `save2.csv`. The final code snippet also invokes the `to_csv()` method, this time in order to save the contents of `save2.csv` in the zip file `save2.zip`. Now launch the code in [Listing 2.48](#ch02.xhtml#list2.48), after which you will see two new files in the directory where you launched this Python script:

`save.csv` `save2.zip` 

## **Pandas Data Frames and Excel Spreadsheets**

[Listing 2.49](#ch02.xhtml#list2.49) displays the contents of write_people_xlsx.py that illustrates how to read data from a CSV file and then create an Excel spreadsheet with that data.

***LISTING 2.49: write_people_xlsx.py***

```python
import pandas as pd
df1 = pd.read_csv("people.csv")
df1.to_excel("people.xlsx")
# optionally specify the sheet name:
# df1.to_excel("people.xlsx", sheet_name='Sheet_name_1')
```

[Listing 2.49](#ch02.xhtml#list2.49) contains the usual import statement, after which the variable `df1` is initialized with the contents of the CSV file `people.csv`. The final code snippet then creates the Excel spreadsheet `people.xlsx` with the contents of the data frame `df1`, which contains the contents of the CSV file `people.csv`.

Now launch `write_people_xlsx.py` from the command line and then open the newly created Excel spreadsheet `people.xlsx` to confirm its contents.

[Listing 2.50](#ch02.xhtml#list2.50) displays the contents of read_people_xlsx.py that illustrates how to read data from an Excel spreadsheet and create a Pandas data frame with that data.

***LISTING 2.50: read_people_xlsx.py***

```python
import pandas as pd
df = pd.read_excel("people.xlsx")
print("Contents of Excel spreadsheet:")
print(df)
```

[Listing 2.50](#ch02.xhtml#list2.50) is straightforward: the Pandas data frame `df` is initialized with the contents of the spreadsheet `people.xlsx` (whose contents are the same as `people.csv`) via the Pandas function `read_excel()`. The output from [Listing 2.48](#ch02.xhtml#list2.48) is here:

`df1`:    Unnamed: 0 fname  lname  age gender  country 0           0  john  smith   30      m      usa 1           1  jane  smith   31      f   france 2           2  jack  jones   32      m   france 3           3  dave  stone   33      m    italy 4           4  sara  stein   34      f  germany 5           5  eddy  bower   35      m    spain 

## **Working with JSON-based Data**

A JSON object consists of data represented as colon-separated name/value pairs and data objects are separated by commas. An object is specified inside curly braces {}, and an array of objects is indicated by square brackets []. Note that character-valued data elements are inside quotes “” (no quotes for numeric data).

Here is a simple example of a JSON object:

{ "fname":"Jane", "lname":"Smith", "age":33, "city":"SF" } 

Here is a simple example of an array of JSON objects:

[ { "fname":"Jane", "lname":"Smith", "age":33, "city":"SF" }, { "fname":"John", "lname":"Jones", "age":34, "city":"LA" }, { "fname":"Dave", "lname":"Stone", "age":35, "city":"NY" }, ]

### **Python Dictionary and JSON**

The Python `json` library enables you to work with JSON-based data in Python.

[Listing 2.51](#ch02.xhtml#list2.51) displays the contents of dict2json.py that illustrates how to convert a Python dictionary to a JSON string.

***LISTING 2.51: dict2json.py***

```python
import json
dict1 = {}
dict1["fname"] = "Jane"
dict1["lname"] = "Smith"
dict1["age"] = 33
dict1["city"] = "SF"
print("Python dictionary to JSON data:")
print("dict1:", dict1)
json1 = json.dumps(dict1, ensure_ascii=False)
print("json1:", json1)
print("")

# convert JSON string to Python dictionary:
json2 = '{"fname":"Dave", "lname":"Stone", "age":35, "city":"NY"}'
dict2 = json.loads(json2)
print("JSON data to Python dictionary:")
print("json2:", json2)
print("dict2:", dict2)
```

[Listing 2.51](#ch02.xhtml#list2.51) invokes the `json.dumps()` function to perform the conversion from a Python dictionary to a JSON string. Launch the code in [Listing 2.51](#ch02.xhtml#list2.51) and you will see the following output:

Python dictionary to JSON data: dict1: { 'fname': 'Jane', 'lname': 'Smith', 'age': 33, 'city': 'SF'} json1: {"fname": "Jane", "lname": "Smith", "age": 33, "city": "SF"}   JSON data to Python dictionary: json2: {"fname":"Dave", "lname":"Stone", "age":35, "city":"NY"} dict2: { 'fname': 'Dave', 'lname': 'Stone', 'age': 35, 'city': "NY"} 

### **Python, Pandas, and JSON**

[Listing 2.52](#ch02.xhtml#list2.52) displays the contents of pd_python_json.py that illustrates how to convert a Python dictionary to a Pandas data frame and then convert the data frame to a JSON string.

***LISTING 2.52: pd_python_json.py***

```python
import json
import pandas as pd
dict1 = {}
dict1["fname"] = "Jane"
dict1["lname"] = "Smith"
dict1["age"] = 33
dict1["city"] = "SF"
df1 = pd.DataFrame.from_dict(dict1, orient='index')
print("Pandas df1:")
print(df1)
print()
json1 = json.dumps(dict1, ensure_ascii=False)
print("Serialized to JSON1:")
print(json1)
print()
print("Data frame to JSON2:")
json2 = df1.to_json(orient='split')
print(json2)
```

[Listing 2.52](#ch02.xhtml#list2.52) initializes a Python dictionary `dict1` with multiple attributes for a user (first name, last name, and so forth). Next, the data frame `df1` is created from the Python dictionary `dict2json.py`, and its contents are displayed.

The next portion of [Listing 2.52](#ch02.xhtml#list2.52) initializes the variable `json1` by serializing the contents of `dict2json.py`, and its contents are displayed. The last code block in [Listing 2.52](#ch02.xhtml#list2.52) initializes the variable `json2` to the result of converting the data frame `df1` to a JSON string. Launch the code in [Listing 2.52](#ch02.xhtml#list2.52) and you will see the following output:
