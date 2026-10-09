
## Chapter 1

## Introduction

In this chapter, you will learn practical methods for analyzing physical data spatio-temporally defined by discrete points. Physical data refer to data used to describe physical or other phenomena. The physical phenomena refer to various phenomena that exist in nature. They include, for example, weather, temperature, earthquakes, and floods. The physical data are often defined as spatio-temporal discrete data. The spatio-temporal discrete data refer to data that are not spatio-temporally continuous. When we handle spatio-temporal discrete data, we usually divide the spatio-temporal axis into discrete segments so that we can handle data in each segment.

Spatio-temporal discrete data can be used in a variety of fields. For example, in the social and natural sciences, spatio-temporal discrete data are sometimes used to analyze various phenomena and their continuous changes. In biology and geology, spatio-temporal discrete data are sometimes used to analyze phenomena that occur in time.

Physical data can be measured in a variety of ways as follows:

- **Using measuring instruments:** Physical data can be measured directly using measuring instruments. For example, a thermometer or a hygrometer can be used to measure temperature and a seismometer can be used to measure the vibrations of an earthquake.
- **Observation:** Physical data can be obtained by observing phenomena. For example, a weather forecast site or app can be used to observe the weather. To acquire weather data, you can observe temperature, humidity, wind speed, etc., at meteorological observatories.
- **Using simulations:** Physical data can be obtained by running simulations on a computer. For example, you can understand fluid and heat conduction phenomena by simulating fluid behavior and heat conduction phenomena.

Today, discovering a spatiotemporal model that explains physical data defined by spatiotemporal discrete points (hereafter simply referred to as “physical data”) is an interesting topic for researchers and practitioners. A key topic in the discovery of a spatiotemporal model is the discrete-to-continuous transformation to effectively evaluate partial differential terms. More specifically, it is about finding a partial differentiable function that adequately approximates physical data defined discretely in the time space. A partially differentiable function is characterized by a partial derivative at a given point. Partial differentiation refers to calculating a derivative with respect to a particular variable in a multivariable function at that point. The partial differentiable function, which has a partial derivative at a given point, is used to analyze a multivariable function. Successfully finding such partial differentiable function enables effective visualization and also enables a partial differential equation (PDE) that explains a phenomenon to be derived using the results of analysis.

This document uses Excel to understand the basics of how to analyze physical data. Excel is widely used as a piece of spreadsheet software to organize data and is suited for data analysis. Using Excel has the following benefits:

- **Easy to use:** Excel is commonly pre-installed on most computers and does not require additional installation. Moreover, Excel can be used without the need for specialized skills.
- **Has a variety of functions:** Excel has a variety of functions that allow you to aggregate data efficiently.
- **Can create graphs or charts:** Excel can be used to visually display data in the form of a graph or chart, which facilitates understanding of data.
- **Data can be easily imported:** Excel allows you to import data from, for example, a CSV or text file.
- **Can work jointly:** Excel allows multiple people to work jointly, making it useful for data analysis projects.

Excel, which provides an array of benefits, is also widely used in data analysis. Next, the basics of Excel will be explained.

### 1.1. Basic operations of Excel

Excel is a piece of spreadsheet software developed by Microsoft. The spreadsheet software is a tool that allows you to enter and edit data in a tabular format for aggregation, analysis, and other purposes. Excel is widely used by individuals and in businesses, and can handle large amounts of data, making it suitable for aggregation and analysis. Excel can be used to not only create a table but to also create a graph or chart. Additionally, Excel has a variety of functions to organize data, allowing you to analyze data and calculate formulas. Excel is commonly pre-installed on Windows and Mac OS and sold as part of Microsoft Office. It is also available as a cloud service, so you can use it from any Internet-connected environment. The data to be analyzed are often provided in Excel format. There are quite a few tools capable of reading and analyzing Excel data, but Excel itself also contains functions to perform analyses. Excel provides tools for determining correlation between data, testing for differences in the mean and variance of data, and regression analysis. It also serves as an optimization tool. These tools can be used to implement deep learning. Excel can be regarded as a tool for preliminary analysis prior to utilizing dedicated analysis tools, and it is advisable to become familiar with its functionalities. This section describes the basic terminology in Excel and explains how to perform what-if analysis using sample data.

#### 1.1.1. Table components

The main components of an Excel table are as follows (Figure 1.1):

- **Worksheet**: One of the basic building blocks of an Excel document. One document has multiple worksheets. One worksheet is usually contained in an Excel file, but multiple worksheets may be included.
- **Cell**: A basic element for entering data in Excel at which a row and a column intersect. You can enter text, numbers, and other values in a cell.
- **Row**: A basic element that divides an Excel worksheet horizontally. A row usually contains a single cell. In Excel, you can refer to a row by specifying a row number.
- **Column**: A basic element that divides an Excel worksheet vertically. A column usually contains a single cell. In Excel, you can refer to a column by specifying the column number.
- **Row number**: A number that identifies a row in Excel and appears on the left. Row numbers typically start from “1”.
- **Column number**: A number that identifies a column in Excel and appears at the top. Column numbers usually start from “A”.

Each component of a table in Excel plays an important role in creating and manipulating a table. When creating a table or entering data, it is important to understand these components and manipulate them appropriately.

![](img/fa57e7010b16a211d5cf69ebb17e416e_12_0.png)

Figure 1.1. Components of a table in Excel.

#### 1.1.2. Name box and formula bar

The name box and formula bar (Figure 1.2) in Excel have the following roles:

- **Name box:** In Excel, you can name a specified cell or range. This is called naming. Naming allows you to specify a cell or a range of cells. A named cell or range is called a “name” in Excel. You can manage your data more efficiently by specifying a named cell or range. Excel provides a function called “name box” that allows you to specify a named cell or range by entering its name.
- **Formula bar:** In Excel, you can calculate data by entering a formula. You can enter a formula in a place called “formula bar”. The formula bar is located in the Excel status bar and used to enter a formula into a cell. Entering a formula allows you to calculate data efficiently.

![](img/fa57e7010b16a211d5cf69ebb17e416e_13_0.png)

![](img/fa57e7010b16a211d5cf69ebb17e416e_13_1.png)

Figure 1.2. Name box and formula bar.

![](img/fa57e7010b16a211d5cf69ebb17e416e_13_2.png)

![](img/fa57e7010b16a211d5cf69ebb17e416e_13_3.png)

Figure 1.3. Ribbon.

#### 1.1.3. Ribbon

The Excel ribbon refers to the tabbed menus that appear in the main Excel window. The ribbon has various functions and commands grouped together into a tab according to the category. There are various tabs, such as Home and Data. Users can use commands in the ribbon to manipulate Excel to create or edit a table.

The tabs and the area containing the buttons which can be switched by clicking a tab are collectively called the “ribbon” (Figure 1.3). You can switch between buttons by clicking the tab placed above them.

#### 1.1.4. File tab and Backstage view

The Excel file tab is a special tab that appears in the upper-left corner of the main Excel window. Clicking on the File tab will bring up the Backstage view (Figure 1.4).

The Backstage view is a space for managing Excel files and data. The Backstage view contains templates for creating a new workbook, as well as
