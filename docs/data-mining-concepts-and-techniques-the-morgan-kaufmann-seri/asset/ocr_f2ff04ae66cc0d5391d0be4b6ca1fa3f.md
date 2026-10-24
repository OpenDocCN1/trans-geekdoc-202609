hierarchies. You will learn concept hierarchies in Section 3.2.3. You will also learn about different categories of measures and how they can be computed efficiently (Section 3.2.4).

# 3.2.1 Data cube: a multidimensional data model

“What is a data cube?” At the core of multidimensional data analysis is the efficient computation of aggregations across many sets of dimensions. A data cube allows data to be modeled and viewed in multiple dimensions. It is defined by dimensions and facts.

A multidimensional data model is typically organized around a central theme, also known as a subject, such as sales. The information about a subject can be divided into two parts in analysis. The first part is the perspectives that the subject is to be analyzed. For example, for subject sales in a company, the possible perspectives may include time, item, branch, and location. Those perspectives are modeled as dimensions. In the simplest multidimensional data model, a dimension table can be built for each dimension. For example, a dimension table for item may contain the attributes item_name, brand and type.

The second part is the measurements on a subject. Those measurements are called facts. For example, for subject sales in a company, the facts may be dollars_sold (sales amount in dollars), units_sold (number of units sold), and amount_budgeted. Facts are typically numerical, but still may take some other data types, such as categorical data or text.

In a data warehouse, a fact table stores the names of the facts, or measures, as well as (foreign) keys referencing to each of the related dimension tables.

In general, a data cube can have as many dimensions as the business needs and thus is n-dimensional. To elaborate data cubes and the multidimensional data model, let us start by looking at a simple 2-D data cube that is, in fact, a table or spreadsheet for sales data for a company. In particular, we will look at the sales data for items sold per quarter in a city, say Vancouver. The data are shown in Table 3.1. In this 2-D representation, the sales for Vancouver are shown with respect to the time dimension (organized in quarters) and the item dimension (organized according to the types of items sold). The fact or measure displayed is dollars_sold (in thousands).

Now, suppose that we would like to view the sales data with a third dimension. For instance, suppose we would like to view the data according to time and item, as well as location, for the cities Chicago, New York, Toronto, and Vancouver. These 3-D data are shown in Table 3.2. The 3-D data in the table

| | | | | |
|---|---|---|---|---|
| \multicolumn{5}{c}{Table 3.1 2-D view of sales data according to time and item.} |
| \multicolumn{5}{c}{location = "Vancouver"} |
| time (quarter) | \multicolumn{4}{c}{item (type)} |
| | home entertainment | computer | phone | security |
| Q1 | 605 | 825 | 14 | 400 |
| Q2 | 680 | 952 | 31 | 512 |
| Q3 | 812 | 1023 | 30 | 501 |
| Q4 | 927 | 1038 | 38 | 580 |
| \multicolumn{5}{c}{Note: The sales are from branches located in the city of Vancouver. The measure displayed is dollars_sold (in thousands).} |