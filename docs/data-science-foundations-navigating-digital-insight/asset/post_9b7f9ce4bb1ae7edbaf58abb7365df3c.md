
question asked and the context of the question. Think about a contact centre, a question you might be asked is: how many employees are needed? This could be to support shift planning or to help shape the recruitment strategy. For shift planning, you are likely to need data on a daily or hourly basis; for recruitment, monthly data might be more appropriate.

The granularity of the data affects what you can do with it. So, in our example you have monthly figures, the data would have very limited in shift planning – daily or hourly data would be more appropriate. This might, however, have too much detail to be useful for recruitment planning. The daily or hourly data could be consolidated into monthly figures to aid recruitment planning, but the monthly data can’t be broken down into daily or hourly figures.

We have previously considered faults in phones. If our data just records the phone has a fault, it will not allow us to analyse faults in screens or faults with the operating system – more granular data would be required for this. This level of granularity might be in the data, but not in a form that can be used in a model. For example, the fault might be recorded in one field (see Table 8.1, column 3), but the method we plan to use with the data requires a separate field for each of the faults. In this instance, we might create an additional data column for each fault and record the fault in it. In the example in Table 8.2, you can see that, in creating the additional columns, the fault type is marked as being present with a 1 and not present with a zero. The reason for this is explained further in Category of Data later in this chapter.

## Table 8.1 Data with fault type in one column

| Fault ID | Date fault logged | Fault type |
|---|---|---|
| 101 | 12/5/2025 | Screen |
| 102 | 13/5/2025 | Operating system |
| 103 | 13/5/2025 | Screen |
| 104 | 14/5/2025 | Screen |
| 105 | 14/5/2025 | Processor |

Table 8.2 Data with fault types recorded in separate columns

| Fault ID | Date fault logged | Screen fault | Operating system fault | Processor |
|---|---|---|---|--|
| 101 | 12/5/2025 | 1 | 0 | 0 |
| 102 | 13/5/2025 | 0 | 1 | 0 |
| 103 | 13/5/2025 | 1 | 0 | 0 |
| 104 | 14/5/2025 | 1 | 0 | 0 |
| 105 | 15/5/2025 | 0 | 0 | 1 |

Creating additional columns is a one way of restructuring the data. However, in some instances, the structure of the tables the data is held in also needs to be considered.

## Structure

Data can be held in many different structures. These data structures include lists, arrays, records, trees and tables.

- **Lists** are an ordered collection of data items. The items in a list can change.
- **Arrays** are a collection of items that can be accessed by an index. An array can have multiple dimensions – a two-dimensional array often being represented as a matrix.
- **Records** are collection of fields, which mark like a row in a table.
- **Trees** are used to hold hierarchical data. The data is held in nodes that have a parent–child relationship with other nodes.
- **Tables** consist of rows and columns. Each row represents an instance of data, and the columns hold the attributes relating to that instance. Each row is a record and each column is a field.

The data structures you encounter will depend on the data you work with and the tools you use. One of the most encountered data structures are tables. These can be found in both spreadsheets and relational databases. It is important that you have the right data structure to enable your analysis. This includes making sure your data is held in appropriate tables if it is in a relational database.

When we analyse our contact centre, we might want to look at the relationship between the number of contacts dealt with in a shift and the number of people working a shift. This data might be sourced from different systems and thus sit in two different tables (Table 8.3). For this to be used by our model, we are likely to need to combine the data into one table. In this instance, we will use the date as the common reference to this – (Table 8.4).

## Table 8.3 Data on contacts in two tables

| Date | Contacts dealt with | Date | People working |
| --- | --- | --- | --- |
| 12/5/2025 | 100 | 12/5/2025 | 4 |
| 13/5/2025 | 110 | 13/5/2025 | 5 |
| 14/5/2025 | 80 | 14/5/2025 | 4 |

Table 8.4 Data on contacts combined into one table

| Date | Contacts dealt with | People working |
| --- | --- | --- |
| 12/5/2025 | 100 | 4 |
| 13/5/2025 | 110 | 5 |
| 14/5/2025 | 80 | 4 |

This is a simple example of how data often needs to be restructured as part of building a model. Structuring data to fit your model can become more complicated, as data can be spread out over multiple tables with complex relationships and linking tables.

## Types

The data type of each of the fields also needs to be considered. This isn’t the data type we looked at in Chapter 7. In this context, we are considering the type of data that can be held in a field that includes integers, floats, Booleans, date/time and strings.

- **Integers**: These are whole numbers, that is, no fractions or decimals. They can be positive, negative or zero.
- **Floats**: These are numbers that can include fractions and decimals.
- **Booleans**: This is a binary field that holds a true or false value.
- **Date/time**: This holds the date and/or time.
- **Strings**: These are made up of characters (letters, numbers, symbols).

To be used in our tools and models, the data might need to be of a particular type. For example, if we are forecasting future values over time, the data set will need to be date/time. However, another example is where an integer is stored as a float. It is therefore important to check and, where necessary, change the data type. When using dates, it is also worth considering their format. You might just be interested in the day, month and year, but the date may include a time as well. In this case, you might need to change the data type to address this.
