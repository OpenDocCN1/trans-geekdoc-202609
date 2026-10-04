# CHAPTER 1 Understanding tabular data

In this chapter, we introduce the process of selecting the appropriate modeling approach for tabular data problems. We present two approaches: deep learning and classical machine learning. Then, from the data perspective, we look at some of the unique considerations you face when using tabular data with machine learning models.

# 1.1 What is tabular data?

For the purposes of this book, tabular data is simply data that is organized in rows and columns. A collection of tabular data can be called a tabular dataset or a table. The entries in a row are related to a common data point or an observation. Each row is autonomous from the other rows and completely describes a specific condition. The columns represent attributes for that data point, and they are often mentioned as variables (a more statistical term) or features (a term more typical of machine learning). All the entries in a column have a common data type, such as integer, string, or floating point number. The columns in a table usually have a common type.

Consider a table that contains information about currencies used in a set of nations, as shown in figure 1.1.

Each column in the table has the information for all countries for one aspect of currency (the attributes of the observations).

| Country | Currency name | Currency nicknames | Currency symbol | ISO 4217 code | Units per US Dollar |
| --- | --- | --- | --- | --- | --- |
| Australia | Australian Dollar | | $ | AUD | |
| Canada | Canadian Dollar | buck, loonie, paysse | $ | CAD | 1.29 |
| New Zealand | New Zealand Dollar | gold coin | $ | NZD | 1.61 |
| South Africa | Rand | buck | R | ZAR | 16.78 |
| United Kingdom | Pound Sterling | quid | £ | GBP | 0.83 |
| United States | US dollar | buck, greenback | $ | USD | 1.0 |

Each row in the table details about the currency for a single country (our observations).

Figure 1.1 An example of tabular data

Columns in this table contain values of different types:

+   * Country, Currency name, Currency symbol, and ISO 4217 code are categorical columns because valid values for these columns come from a finite, relatively small set of values.