
Now every time you want to activate this environment, just open a terminal and type:

```
$ cd ML_PATH
$ source env/bin/activate # on Linux or macOS
$ \env\Scripts\activate # on Windows
```

To deactivate this environment, just type deactivate. While the environment is active, any package you install using pip will be installed in this isolated environment, and Python will only have access to these packages (if you also want access to the system's packages, you should create the environment using virtualenv--system-site-packages option). Check out virtualenv's documentation for more information.

Now you can install all the required modules and their dependencies using this pip command (if you are not using a virtualenv, you will need the --user option or administrator rights):

```
$ python3 -m pip install jupyter matplotlib numpy pandas scikit-learn
Collecting jupyter
Downloading jupyter-1.0.0-py2.3-none-any.whl
Collecting matplotlib
[...]
```

To check your installation, try to import every module like this:

$ python3 -c "import jupyter, matplotlib, numpy, pandas, scipy, sklearn"
There should be no output and error. Now you can fire up Jupyter by typing:

```
$ jasper notebook
[ 15:24 NotebookApp] Serving notebooks from local directory: [... ]/ml
[ 15:24 NotebookApp] 0 active kernels
[ 15:24 NotebookApp] The Jupyter Notebook is running at: http://localhost:8888/
[ 15:24 NotebookApp] Use Control-C to stop this server and shut down all
kernels (twice to skip confirmation).
```

A Jupyter server is now running in your terminal, listening to port 8888. You can visit this by opening your web browser to http://localhost:8888/ (this usually opens automatically when the server starts). You should see your empty directory (containing only the env directory if you followed the preceding virtualenv instructions).

Now create a new Jupyter notebook by clicking on the New button and selecting the appropriate Python version* (see Figure 2-3).

This does three things: first, it creates a new notebook file called Untitled.ipynb in your workspace; second, it starts a Jupyter kernel to this notebook; and third, it opens this notebook in a new tab. You should start by renaming this notebook to "Housing" (this will automatically rename the file to *Housing.ipynb*) by clicking and typing the new name.

![](img/0684d2da98e09085c0a622d4fd69aaad_73_0.png)

Figure 2-3. Your workspace in Jupyter

A notebook contains a list of cells. Each cell can contain executable code or formatted text. Right now the notebook contains only one empty code cell, labeled "In [1]:". typing `print("Hello world!")` in the cell, and click on the play button (see [Figure 2-4]) or Shift-Enter. This sends the cell to this notebook's Python kernel, which runs it and returns the output. The result is displayed below the cell, and since we reached the end of the notebook, a new cell is automatically created through the User Interface Tool from Jupyter's Help menu to learn the basics.

![](img/0684d2da98e09085c0a622d4fd69aaad_73_1.png)

Figure 2-4. Hello world Python notebook

Chapter 2: End-to-End Machine Learning Project

# Download the Data

In typical environments your data would be available in a relational database (or some common datastore) and spread across multiple tables/documents/files. To access it, you would first need to get your credentials and access authorizations, and familiarize yourself with the data schema. In this project, however, things are much simpler: you will just download a single compressed file, housing.tgz, which contains a comma-separated value (CSV) file with all the data.

You could use your web browser to download it, and run tar xzf housing.tgz to decompress the file and extract the CSV file, but it is preferable to write a small function to do that. It is useful if particular data changes regularly, as it allows you to write a script that you can run whenever you need to fetch the latest data (or you can set a scheduled job to do that automatically at regular intervals). Automating the process of fetching the data is also useful if you need to install the dataset on multiple machines.

Here is the function to fetch the data:

```
import os
import tarfile
from six.moves import urllib

DOWNLOAD_ROOT = "https://raw.githubusercontent.com/ageron/housing-ml2/master/"
HOUSING_PATH = os.path.join("datasets", "housing")
HOUSING_URL = DOWNLOAD_ROOT + "/datasets/housing/housing.tgz"

def fetch_housing_data(housing_url=HOUSING_URL, housing_path=HOUSING_PATH):
    if not os.path.exists(housing_path):
        os.makedirs(housing_path)
    tgz_path = os.path.join(housing_path, "housing.tgz")
    urllib.request.urlretrieve(housing_url, tgz_path)
    housing_tgz = tarfile.open(tgz_path)
    housing_tgz.extractall(path=housing_path)
    housing_tgz.close()
```

Now when you call fetch_housing_data(), it creates a datasets directory, downloads the housing.tgz file, and extracts the housing.csv from it. Now let's load the data using Pandas.

```python
import pandas as pd
def load_housing_data(housing_path=HOUSING_PATH):
    path = os.path.join(housing_path, "housing.csv")
    return pd.read_csv(path)
```

This function returns a Pandas DataFrame.

# Take a Quick Look at the Data

Let's look at the top five rows using head() (see Figure 2-5).

 | longitude | latitude | housing_median_age | total_rooms | total_bedrooms | population |
|---|---|---|---|---|---|---|
| 0 | -122.2337 | 37.8752 | 41 | 6869 | 2 | 3269 |
| 1 | -122.2715 | 37.8509 | 21 | 6462 | 3 | 2466 |
| 2 | -122.2175 | 37.8581 | 52 | 1718 | 2 | 1569 |
| 3 | -122.2272 | 37.825 | 54 | 5465 | 9 | 2018 |
| 4 | -122.2235 | 37.8253 | 53 | 5355 | 2 | 1417 |

Figure 2-5. Top rows

There are 20,640 instances in the dataset, which means it is fairly small by Machine Learning standards, but it's perfect to get started. Notice that the total_bedrooms attribute has 20,433 non-null values, meaning that 207 districts are missing this feature. We will need to take care of this.

The info() method is useful to get a quick description of the data, in particular the number of rows, each attribute's type and non-null values (see Figure 2-6).

```
<class 'pandas.core.DataFrame'>
RangeIndex: 20640 entries, 0 to 20639
Data columns (total 10 columns):
 longitude 20640 non-null float64
latitude 20640 non-null float64
housing_median_age 20640 non-null float64
total_rooms 20640 non-null float64
total_bedrooms 20433 non-null float64
population 20640 non-null float64
households 20640 non-null float64
median_income 20640 non-null float64
housing_value 20640 non-null float64
ocean_proximity 20640 non-null object
types: float64(9), object(1)
memory usage: 1.6 MB
```

Figure 2-6. Housing info

All attributes are numerical, except the ocean_proximity field. Its type is object, so it could hold any kind of Python object, but since you loaded this data from a CSV file you know that it is a text attribute. When you looked at the top five rows, you probably noticed that the values in the ocean_proximity column were repetitive, which means that it is probably a categorical attribute. You can find out how many districts belong to each category by using the value_counts() method:

```
>>> housing['ocean_proximity'].value_counts()
<1H OCEAN        9136
INLAND            6555
NEAR OCEAN        2658
NEAR BAY          2290
ISLAND             5
Name: ocean_proximity, dtype: int64
```
