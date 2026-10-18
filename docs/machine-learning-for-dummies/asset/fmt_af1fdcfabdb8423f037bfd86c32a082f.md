
*   **Fashion MNIST (`https://github.com/zalandoresearch/fashion-mnist`):** A dataset of Zalando's article (`https://jobs.zalando.com/en/tech/`) images. It consists of a training set of 60,000 examples and a test set of 10,000 examples, each of which is labeled with one of ten categories.

*   **Palmer Penguins (`https://github.com/allisonhorst/palmerpenguins`):** A package containing two datasets collected and made available by Dr. Kristen Gorman and the Palmer Station, Antarctica LTER, a member of the Long Term Ecological Research Network.

*   **Shakespeare (`https://www.kaggle.com/kingburrito666/shakespeare-plays`):** A listing of all Shakespeare's plays, lines from these plays, and who is speaking the line.

*   **SMS Spam Collection (`https://www.kaggle.com/uciml/sms-spam-collection-dataset`):** A set of SMS tagged messages collected for SMS Spam research. It contains one set of SMS messages in English of 5,574 messages, tagged according to whether the message is ham (legitimate) or spam.

*   **Tennis (`https://www.kaggle.com/ehallmar/a-large-tennis-dataset-for-atp-and-itf-betting`):** Dataset containing statistics for a large number of tennis matches from the ATP and ITF leagues.

*   **Titanic (`https://www.openml.org/d/40945`):** A dataset describing the survival status of individual passengers on the Titanic. The titanic data does not contain information from the crew, but it does contain actual ages of half the passengers.

*   **Wine (`https://www.kaggle.com/sgus1318/winedata`):** Contains statistics related to the quality of wine.

The technique for loading each of these datasets can vary according to the source. The following example shows how to load the Air Passengers dataset. You can find the code in the `ML4D2E; 04; Dataset Load.ipynb` notebook. The downloadable datasets are archived in the Apache Arrow-based Feather File Format (`https://arrow.apache.org/docs/python/feather.html`). To make this file format accessible in Notebook, you open an Anaconda prompt and type the following command:

`conda install feather-format -c conda-forge`

The command takes a while to complete as it collects the package information and solves the environment (determines what to do to perform the installation). At some point, you'll need to type `y` and press Enter to complete the installation. To verify that you have a good installation, use this command:

`conda list feather-format`

After a few moments, you see output similar to this:

```
# packages in environment at C:\Users\John\anaconda3:## Name Version Build Channelfeather-format 0.4.1 pyh9f0ad1d_0 conda-forge
```

Now that you have the required library to use, you can load a dataset from those supplied on the book’s dataset site. To start, download the `air_passengers.feather` file from [`https://github.com/lmassaron/datasets`](https://github.com/lmassaron/datasets) and place it in folder you created for this book. (In later chapters, you see how to download the `.feather` files directly from the book's dataset site, but performing the download now keeps things simple.) Here is an example of the code you use to load Air Passengers dataset as a `dataframe`.

```
import pyarrow.feather as feather
read_df = feather.read_feather('air_passengers.feather')
print(read_df)
```

The result is a 144-row `dataframe` containing the number of passengers per month. [Figure 4-9](#c04.xhtml#c04-fig-0009) shows typical output.

![FIGURE 4-9: The read\_df object contains the loaded dataset as a dataframe.](images/9781119724018-fg0409.png)

[FIGURE 4-9:](#c04.xhtml#rc04-fig-0009) The `read_df` object contains the loaded dataset as a dataframe.

# Chapter 5

## Beyond Basic Coding in Python

### IN THIS CHAPTER

- **Performing essential programming tasks in Python**
- **Managing data using sets, lists, and tuples**
- **Accessing individual items using iterators**
- **Making data easier to access using indexed storage**

[Chapter 4](#c04.xhtml) helps you create a Python installation that you can use for a variety of purposes, including machine learning and data science. This chapter’s focus is on providing a good overview of how Python works as a language as well as to solve machine learning problems. If you already know Python, you might be able to skip this chapter and move on to the next one. It might be best, however, to at least skim this chapter and test some of the examples, just to be sure that you have a good installation.

If you’re new to Python, you can’t use this book to learn Python from scratch — for that, you need a book such as *Beginning Programming with Python For Dummies,* 2nd Edition, by this book’s coauthor John Mueller (Wiley), or you need a tutorial such as the one at [`https://docs.python.org/3/tutorial/`](https://docs.python.org/3/tutorial/). This chapter assumes that you’ve worked with other programming languages and have at least an idea of how Python works. This limitation aside, you can use this chapter for a refresher on how things work in Python, which is all that many people really need. You find out the basics of working with Python data types, coding structures, and data manipulation strategies.

![Remember](images/remember.png) You don’t have to type the source code for this chapter manually. In fact, using the downloadable source is a lot easier. You can find the source for this chapter in the `ML4D2E` folder of the downloadable source. The example files for this chapter will begin with `ML4D2E; 05;`. See the Introduction for details on how to find these source files.

## Defining the Basics You Should Know

Any language possesses basic characteristics, and Python is no different. For example, languages provide various data types, operators, methods of interacting with data, and so on. In addition, Python supports both functions and modules. You use this knowledge when working through the examples in this book. The following sections provide a brief overview reminder of these basics.

### Considering Python basics

Python is a rich language that provides you with a great deal of flexibility in an easy-to-use language. This section offers a brief overview of Python basics. If you need more help, and the standard Python tutorial reference provided in the chapter introduction isn't sufficient, consider using the tutorials at [`https://www.w3schools.com/python/`](https://www.w3schools.com/python/) and [`https://www.tutorialspoint.com/python/index.htm`](https://www.tutorialspoint.com/python/index.htm) as well. [Table 5-1](#c05.xhtml#c05-tbl-0001) shows an overview of the common numeric Python data types.

[TABLE 5-1](#c05.xhtml#rc05-tbl-0001) Python Numeric Data Types

| **Type** || **Range** || **Example** |

| --- | --- | --- |

| `int` or `long` || –9,223,372,036,854,775,808 and 9,223,372,036,854,775,807 (defined by `sys.maxsize` for a particular platform) || 1 |

| --- | --- | --- |

| `float` || ±2.2250738585072014 × 10^(\-308) and ±1.7976931348623157 × 10^(308) (defined by `sys.float_info.max` and `sys.float_info.min` for a particular platform) || 1.0 |

| --- | --- | --- |

| `complex` || N/A || 3 + 4j |

| --- | --- | --- |

| `bool` || `True` or `False` || `True` |

To create variables used to hold data, you make assignments. [Table 5-2](#c05.xhtml#c05-tbl-0002) contains a list of Python assignment operators (assume that `MyVar` begins by containing the value `5` in each case).
