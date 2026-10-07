Let us load this file and check what the data contains:

```
dfLive = pd.read_csv(".Online_Retail_Test.csv")
print("Shape of the data:", dfLive.shape)
print("\n", dfLive.head())
Shape of the data: (27096, 8)
```

| InvoiceNo | StockCode | Description | Quantity | \n|---|---|---|---||
| 0 | 555200 | 71459 | HANGING JAM JAR T-LIGHT HOLDER | 24 |
| 1 | 559474 | 21128 | GOLD FISHING GNOME | 4 |
| 2 | 559072 | 21086 | SET/6 RED SPOTTY PAPER CUPS | 4 |
| 3 | 576652 | 22812 | PACK 3 BOXES CHRISTMAS PANETTON | 3 |
| 4 | 546157 | 22180 | RETROSPECT LAMP | 2 |

| InvoiceDate | UnitPrice | CustomerID | Country |
|---|---|---|---||
| 0 | 2011-01-01 12:05:00 | 0.85 | 17315.0 | United Kingdom |
| 1 | 2011-05-27 17:14:00 | 6.95 | 14031.0 | United Kingdom |
| 2 | 2011-04-21 17:05:00 | 0.65 | 14031.0 | United Kingdom |
| 3 | 2011-11-16 10:39:00 | 1.95 | 17198.0 | United Kingdom |
| 4 | 2011-03-10 08:40:00 | 9.95 | 13502.0 | United Kingdom |

This data has been taken from an Online Retailer in the United Kingdom. The data contains eight columns – Invoice Date, Stock Code (The code for the item sold), Description (The description of the item sold), Invoice Date, Unit Price, Customer ID (unique Customer Code), and Country (where the customer belongs to). We need to formulate the Recency, Frequency, and Monetary Value from this data to apply our model for segmenting the customers.

# Preprocessing the data

The first step is to preprocess the data to remove any unnecessary element or aspect of the data.

We first remove all the duplicate data:

```
print("Before Dropping Duplicates:", dfLive.shape)
dfLive.drop_duplicates(keep='first', inplace=True)
print("After Dropping Duplicates:", dfLive.shape)
```