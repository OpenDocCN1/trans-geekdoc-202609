![image](OEBPS/images/cover.jpg)

**MS Excel**

**MS Excel**

**Let’s Advance to the Next Level**

Second Edition

Anurag Singal

 

 

 

 

 

 

![](OEBPS/images/titlef.jpg)

*MS Excel, Second Edition: Let’s Advance to the Next Level*

Copyright © Business Expert Press, LLC, 2019.

All rights reserved. No part of this publication may be reproduced, stored in a retrieval system, or transmitted in any form or by any means—electronic, mechanical, photocopy, recording, or any other except for brief quotations, not to exceed 250 words, without the prior permission of the publisher.

First published in 2019 by

Business Expert Press, LLC

222 East 46th Street, New York, NY 10017

[www.businessexpertpress.com](http://www.businessexpertpress.com)

ISBN-13: 978-1-94944-382-0 (paperback)

ISBN-13: 978-1-94944-383-7 (e-book)

Business Expert Press Quantitative Approaches to Decision Making Collection

Collection ISSN: 2153-9515 (print)

Collection ISSN: 2163-9582 (electronic)

Cover and interior design by S4Carlisle Publishing Services Private Ltd., Chennai, India

First edition: 2017  
Second edition: 2019

10 9 8 7 6 5 4 3 2 1

Printed in the United States of America.

### Abstract

*MS Excel* is one of the most powerful tools available to a business manager. In this book, I have made an attempt to move to the advanced level of skill sets and bring actionable insights to the user.

Hence, the material in this version has been organized as follows:

A) Financial functions

B) Conditional math and statistical functions

C) Data analysis

D) Decision making

E) Data cleaning and use of macros

F) Auditors

The objective is to give you a flavor of how the vast array of functions can be used to make life easier and more efficient. You can achieve some amazing results by mastering Excel at a basic level.

Do not just read this book as if you are reading a novel. Execute the given functions on a workbook simultaneously and experience the journey. It is those who practice it who will find the learning curve the steepest.

### Keywords

MS Excel; MS Excel Advanced tutorial; MS Excel Advanced courses; Advanced MS Excel for Accountants; Advanced MS Excel for Finance Managers; Microsoft Excel Books; Advanced Excel Books; Microsoft Excel Bible: The Comprehensive Tutorial Resource; Microsoft Excel - Data Analysis and Business Modeling; Advance Excel in Depth

## Contents

[*Preface*](#06_preface.xhtml#m1)

[*Acknowledgments*](#07_ack.xhtml#m2)

[Chapter 1 Excel for Personal Financial Decisions](#08_chapter01.xhtml#m3)

[Chapter 2 Excel for Conditional Math and Statistical Functions](#09_chapter02.xhtml#m4)

[Chapter 3 Excel for Data Analysis](#10_chapter03.xhtml#m5)

[Chapter 4 Excel for Decision Making](#11_chapter04.xhtml#m6)

[Chapter 5 Excel for Data Dashboards and Visualization](#12_chapter05.xhtml#m7)

[Chapter 6 Excel for Data Cleaning and Use of Macros](#13_chapter06.xhtml#m8)

[Chapter 7 Excel for Auditors](#14_chapter07.xhtml#m9)

[*About the Author*](#15_ata.xhtml#m10)

[*Index*](#16_index.xhtml#m11)

## [Preface](#05_contents.xhtml#r1)

The operational efficiency of any knowledge professional can improve significantly with an upgradation of his or her skills of *MS Excel*. With every additional function that you learn, life can become a lot easier.

While in the first edition we had focused on the very basics, a common feedback was that readers wanted a more actionable book.

Hence, the material in this version has been organized as follows:

A) Financial functions

B) Conditional math and statistical functions

C) Data analysis

D) Decision making

E) Data cleaning and use of macros

F) Auditors

I hope this will significantly enhance the utility of the book.

Don’t just read this book like a novel. Practice it and the learning curve will be the steepest.

“The proof of the pudding lies in the eating.” So let the pages make their sales pitch themselves.

## [Acknowledgments](#05_contents.xhtml#r2)

The first edition of this book was received with great interest by readers. It focused on providing users with a first-hand experience of the nuances of MS Excel. A lot of them have generously taken time out to provide feedback.

I wish to express my special thanks to the reviewer, Sonia Singal, my better half.

I also greatly appreciate the strategic comments and advice of Ayush Agarwal, who diligently and generously provided extensive comments as well as encouragement.

Scott Isenberg, Managing Executive Editor, and Charlene Kronstedt, Director of Production, Business Expert Press, have been a pillar of support.

Rene Caroline provided excellent copyediting and book production.

[CHAPTER 1](#05_contents.xhtml#r3)

[Excel for Personal Financial Decisions](#05_contents.xhtml#r3)

PV and FV

Excel has several financial functions:

A) The PV (Present Value) function calculates the total present (current) value of an investment with a fixed rate, specified number of payment periods, and a series of identical payments that will be made in the future.

B) The FV (Future Values) function calculates the future value of an investment, given a fixed interest rate, term, and identical periodic payments.

C) The NPV (Net Present Value) function calculates the net present value of an investment, given a fixed rate (rate of return) and future payments that may be identical or different.

![](OEBPS/images/f001-1.jpg)

Internal Rate of Return (IRR)

This returns the internal rate of return for a series of cash flows represented by the numbers in values. These cash flows do not have to be even, as they would be for an annuity. However, the cash flows must occur at regular intervals, such as monthly or annually. The internal rate of return is the interest rate received for an investment consisting of payments (negative values) and income (positive values) that occur at regular periods.

![](OEBPS/images/f002-1.jpg)

Determine # Periods in Bond Problem

![](OEBPS/images/f003-1.jpg)

Yield to Maturity

![](OEBPS/images/f004-1.jpg)

NPER and RATE

The NPER (Number of PERiods) function calculates the number of payment periods for an investment or loan given a fixed interest rate, periodic payment, and present value.

The RATE function calculates the periodic rate for an investment or loan given the number of payment periods, a fixed periodic payment, and present value.

![](OEBPS/images/f005-1.jpg)

This slide shows specific examples of how the number of periods (NPER) and rate (RATE functions) have been applied in a worksheet.

Create a Loan Amortization Table

Suppose you want to create a payment schedule that shows the interest per payment period, principal repayment for each payment, and the balance after each payment is made. This is called a loan amortization table, and a partial table is shown in the slide. Because this example is for a car loan over 4 years or 48 monthly payments, the complete schedule cannot be viewed in its entirety.

Let’s look at the financial functions that are needed to generate this amortization table.

![](OEBPS/images/f005-2.jpg)

IPMT

The IPMT function calculates the periodic interest for a specified payment period on a loan or an investment given a fixed interest rate, specified term, and identical periodic payments.

\=IPMT(rate,per,nper,pv,\[fv\],\[type\])

The PPMT function calculates the principal payment for a specified payment period on a loan or an investment given a fixed interest rate, specified term, and identical periodic payments.

\=IPMT(rate,per,nper,pv,\[fv\],\[type\])

The arguments for these two functions are:

A) The rate argument is the periodic interest rate. If the APR is 6 percent and the payments are made monthly, then the rate is 6 percent/12 or 0.5 percent.

B) The per argument is the specific payment or investment period to use to calculate the interest where the first payment period is 1.

C) The nper argument represents the total number of payment or investment periods. With a 4-year loan consisting of monthly payments, the number of payment periods is 48.

D) The pv argument represents the present value of the loan or investment.

E) The optional fv argument represents the future value of the loan or investment. If you omit this argument, Excel defaults to 0.

F) The optional type argument represents the timing of the payments. Enter 0 if the payments are made at the end of the period, or enter 1 if the payments are made at the beginning.

Cumulative Calculation Functions

• The CUMIPMT function calculates the cumulative interest through a specified payment period.  
\=CUMIPMT(rate,nper,pv,start\_period,end\_period,type)

• The CUMPRINC function calculates the cumulative principal through a specified payment period.  
\=CUMPRINC(rate,nper,pv,start\_period,end\_period,type)

The only two new arguments are the start\_period argument, which specifies the first period you want to start accumulating the interest, and the end\_period argument, which specifies the last payment period you want to include.

The amortization table is shown once again so you can see how the various functions were applied.

![](OEBPS/images/f006-1.jpg)

[CHAPTER 2](#05_contents.xhtml#r4)

[Excel for Conditional Math and Statistical Functions](#05_contents.xhtml#r4)

As against specialist software packages for statistical analysis like SPSS, R, SAS, and Minitab, the reason we often use Excel for statistical analysis is

A) Convenience as it’s already installed on our PCs. It is to be noted that unless the statistical computational needs are highly advanced, for beginners Excel is quite user-friendly and eliminates the need to learn another software. Excel also integrates easily into other Microsoft Office software products, and this can be helpful when preparing reports or presentations.

B) Cost—There is no need to incur license costs of an SPSS, R, SAS, and Minitab.

There are a host of statistical analysis functions for descriptive statistics. In addition, it provides the standard worksheet functionality and makes it useful for other analysis and data manipulation tasks, including generating graphical and other presentation formats.

This table shows some of the statistical functions available in Excel:

 
| Function name || Description |
| --- | --- |
| AVERAGE || Returns the arithmetic mean (average) of the given numbers |
| --- | --- |
| CHISQ.DIST.RT || Returns the right-tailed probability for the chi-squared distribution |
| CHISQ.TEST || Returns the *p*\-value for the chi-squared test of association |
| CONFIDENCE.T || Returns the margin of error for a confidence interval for the mean |
| COUNT || Counts the number of cells in a range that contain numbers |
| COUNTIF || Counts the number of cells in a range that meet a given condition |
| COUNTA || Counts the number of cells in a range that are not empty |
| KURT || Returns the kurtosis of a dataset |
| MAX || Returns the maximum value of the given numbers |
| MEDIAN || Returns the median of the given numbers |
| MIN || Returns the minimum value of the given numbers |
| MODE.SNGL || Returns the mode of the given numbers |
| PEARSON || Returns the Pearson correlation coefficient (*r*) of two variables |
| SKEW || Returns the skewness of a dataset |
| STDEV.P || Returns the standard deviation of the given numbers, based on the population |
| STDEV.S || Returns the standard deviation of the given numbers, based on a sample |
| VAR.P || Returns the variance of the given numbers, based on the population |
| VAR.S || Returns the variance of the given numbers, based on a sample |

SUMIFS, AVERAGEIFS and COUNTIFS

• The SUMIFS function calculates the total value of cells in a range that meet multiple criteria.

• The AVERAGEIFS function calculates the average value of cells in a range that meet multiple criteria.

• The COUNTIFS function counts the number of cells in a range that meet multiple criteria.

![](OEBPS/images/f011-1.jpg)

The SUMIF and SUMIFS functions are math functions and are located under Math & Trig in the Function Library group. The AVERAGEIF, AVERAGEIFS, COUNTIF, and COUNTIFS functions are statistical functions.

Measure Central Tendency

When calculating central tendencies, there are two groups to consider:

• A population is a dataset that contains all the data you would like to evaluate.

• A sample is a smaller, more manageable portion of the population.

The two common functions for measuring central tendencies are:

• Variance is a measure of a dataset’s dispersion.

• Standard deviation is the measure of how far the data sample is spread around the mean (average).

Excel provides four versions of functions to calculate these two central tendencies. We will focus on two versions of each.

Standard Deviation Functions:

• The STDEV.P function calculates the standard deviation on the basis of the population.

• The STDEV.S function calculates the standard deviation on the basis of a sample of the population.

The arguments for these two functions are:

• The first argument specifies the range of values used to calculate the standard deviation.

• The second argument is not commonly used.

Variance Functions

• The VAR.P function calculates the variance based on the population.

• The VAR.S function calculates the variance based on a sample of the population.

![](OEBPS/images/f012-1.jpg)

Correlation

This quantifies the causal relationship between two variables, for example, correlation between smoking and cancer or correlation between hours spent studying and the grades in a test.

The correlation coefficient can vary between −1 and 1. The stronger the relationship, the closer the coefficient of correlation is to −1 or 1.

The CORREL function, short for “correlation coefficient,” helps determine the strength of a relationship between two variables. When used to compare datasets, the function will return a value between −1 and 1.

![](OEBPS/images/f013-1.jpg)

Frequency

![](OEBPS/images/f013-2.jpg)

The frequency distribution is a meaningful descriptive tool because it determines how often a set of numbers appears within a dataset.

The FREQUENCY function determines the frequency distribution of a dataset.

The two arguments for the function are:

• The data\_array: contain the values that are being evaluated for frequency of occurrence.

• The bins\_array argument: the range of numbers that specify the bins in which the data should be counted.

As seen in the Formula Bar, we are using Column C, which contains salaries, and creating three bins based on quartiles and the corresponding salaries in Column H. We see that there are 12 people in the first quartile and 13 in the second and third quartiles.

Load the Analysis ToolPak

![](OEBPS/images/f014-1.jpg)

To enable the Analysis ToolPak add-in, you:

• Click the File tab and click Options.

• Select Add-ins on the left side.

• Ensure that Excel Add-ins is selected in the Manage box and click Go.

• Click the Analysis ToolPak check box to select it and click OK.

The functions available are:

 
| Function name || Description |
| --- | --- |
| ANOVA: Single Factor || Performs a one-way analysis of variance (ANOVA) |
| Correlation || Creates a correlation matrix showing the Pearson correlation coefficient (*r*) for each pair of variables of *N* cases selected |
| Descriptive statistics || Calculates a range of univariate descriptive statistics, including measures of central tendency, dispersion, skewness, and kurtosis for a variable |
| Histogram || Generates a histogram for a range of data (this function also generates a table of the data on which the histogram is based and can be used for Pareto analysis) |
| *t*\-Test: Paired Two-Sample for Means || Performs a *t*\-test to compare the means of a paired sample |
| *t*\-Test: Two-Sample Assuming Equal Variances || Performs a *t*\-test to compare the means of two independent samples, assuming equal variances |
| *t*\-Test: Paired Two-Sample Assuming Unequal Variances || Performs a *t*\-test to compare the means of two independent samples, assuming unequal variances |

Illustration

The following example of applying the Descriptive Statistics function to generate a range of descriptive statistics for the variable age in the sample dataset illustrates their use:

• Select Data > Data Analysis to open the Data Analysis menu dialog box.

Data Analysis menu dialog box

![](OEBPS/images/f015-1.jpg)

• Select the desired function, in this case Descriptive Statistics, which opens the relevant dialog box.

• Enter the desired range in the Input Range box. The default setting is New Worksheet Ply, which creates a new worksheet for the output since most ToolPak outputs are quite large.

• Select Summary Statistics to get descriptive statistics for your chosen data. You can also select an appropriate confidence interval for the mean if desired (the default is 95 percent).

Descriptive Statistics dialog box

![](OEBPS/images/f016-1.jpg)

• Click OK. The output will be shown in a new worksheet. Note that here the column widths have been adjusted to make it easier to read.

***Descriptive Statistics output for variable Age***

![](OEBPS/images/f016-2.jpg)

ANOVA

ANOVA tests statistically whether samples of data were taken from the same population. In practical use, it can be used to accept or reject a hypothesis.

For ANOVA, we have to use the Analysis ToolPak.

Of the three types of ANOVA, we will create an ANOVA report using a single-factor ANOVA about a school system’s high school students.

To use the Analysis ToolPak to create a single-factor ANOVA report:

• On the Data tab in the Analysis group, click Data Analysis to display the Data Analysis dialog box.

• Select ANOVA: Single Factor and click OK.

• Click the Input Range selection box and select the range of data you want to analyze.

• Select either Grouped by Columns or Grouped By Rows on the basis of your data layout.

• Choose the default Alpha 0.05 (meaning there is a 5 percent chance of rejecting the null hypothesis).

• Select an output option and click OK.

This slide shows the result of an ANOVA test, and the table shows how to interpret the results.

![](OEBPS/images/f017-1.jpg)

Covariance

Covariance is similar to correlation. It is a measure of how two sets of data vary simultaneously. In Excel, there are COVARIANCE.P and COVARIANCE.S functions that can calculate covariance, and there is also a covariance reporting feature included in the Analysis ToolPak.

To create a covariance report:

• On the Data tab in the Analysis group, click Data Analysis to display the Data Analysis dialog box.

• Select Covariance and click OK.

• Click the Input Range selection box, and select the range of the data you want to analyze.

• Select Grouped By Columns or Grouped By Rows depending on the organization of the dataset.

• If the first row contains labels, check the Labels in the First Row check box to select it.

• Select an output option and click OK.

In this example, we are hypothesizing that the more days of school missed by students, the lower the student’s SAT scores. We would expect a negative relationship, which is indicated in the results.

![](OEBPS/images/f018-1.jpg)

Histogram

A histogram is a visual display of tabulated frequencies. We can use the Analysis ToolPak. Creating a histogram is somewhat similar to using the FREQUENCY function in that it requires bins to tabulate the data and will return a frequency distribution table.

To create a histogram:

• On the Data tab in the Analysis group, click Data Analysis to display the Data Analysis dialog box.

• Enter the Input Range in the Input Range box.

• Enter the Bin Range in the Bin Range box.

• Click the Labels box.

• Select the output options of your choice.

• Select an output option and click OK.

The following is the frequency distribution table from which the histogram is created.

![](OEBPS/images/f019-1.jpg)

Case Study—Factory Production

A factory produces three products (A, B, and C). How can we predict the cost of running the factory on the basis of knowing the number of units produced?

Let’s say, contains the cost of running a plant over 19 months as well as the number of units of product A, B, and C produced during each month.

![](OEBPS/images/f020-1.jpg)

We would like to find the best forecast for monthly operating cost that has the format

Monthly operating cost = Constant + B1 × (Units A produced) + B2 × (Units B produced) + B3 × (Units C produced)

Excel’s Data Analysis feature can find the equation for this form that best fits our data. Click Tools, Data Analysis, and then select Regression.

![](OEBPS/images/f020-2.jpg)

• The Input Y range, B3:B22, contains the dependent variable or data (including the label Cost) that we want to predict.

• The Input X range, C3:E22, contains the data or independent variables (including the labels A Made, B Made, C Made) that we want to use in the prediction. Excel has a limit of 15 independent variables, and they must be in adjacent columns.

• Since both the Input X and Input Y ranges include labels, we checked the Labels box.

• We chose to place the output in a worksheet named Regression.

• Checking the Residuals option causes Excel to list for each observation the prediction from Form 1 and the residual, which equals the observed cost minus the predicted cost.

• After clicking OK in the Regression dialog box, we obtain the output shown.

![](OEBPS/images/f021-1.jpg)

What Is the Best Prediction Equation?

We find in the Coefficients column (column B in the output) that the best equation of Form 1 that can be used to predict monthly cost is

Predicted monthly cost = 35,102.90 + 2.07(A Made) + 4.18(B Made) + 4.79(C Made)

Case Exercise

A study was carried out to assess two different therapeutic schemas for treatment of iron deficiency in a newborn child. Included in the study were newborns from rural and urban environments. Two different schema were applied: a daily schema (the mothers administered the treatment to their child once a day every day of the week) and a biweekly schema (the mothers administered to the child the treatment on Mondays and Thursdays). The data were collected as follows:

Requests

1. Create in the Histogram sheet the following table:

![](OEBPS/images/f023-1.jpg)

2. Use the *Histogram* function from ***Data Analysis*** to create the histograms for birth weight, hemoglobin 6 months, and hemoglobin 12 months.

3. Insert a new sheet named *Descriptive statistics*. Copy in this sheet the following variables: “Birth weight (g),” “Hemoglobin (mg/dl) 6 months,” “Hemoglobin (mg/dl) 12 months,” and “Treatment schema.”

4. Compute descriptive statistics parameters for quantitative variables using the *Descriptive Statistics* function from ***Data Analysis***.

5. Calculate the 95 percent confidence intervals for means using the results previously obtained.

6. Compute descriptive statistics parameters for *Hemoglobin at 6 and 12 months* for patients with *Daily treatment schema* and for patients with *Biweekly treatment schema*. Calculate the 95 percent confidence intervals for means using the results previously obtained.

[CHAPTER 3](#05_contents.xhtml#r5)

[Excel for Data Analysis](#05_contents.xhtml#r5)

VLOOKUP and HLOOKUP Functions

Through these functions, we can “look up” values from worksheet ranges.

In Excel, we can perform both vertical lookups (using VLOOKUP functions) and horizontal lookups (using HLOOKUP functions).

A) In a vertical lookup, the lookup operation starts in the first column of a worksheet range.  
Use VLOOKUP when each row contains a separate record and the associated columns contain data for that one record.

B) In a horizontal lookup, the operation starts in the first row of a worksheet range.

Use HLOOKUP when each column contains a separate record.

These functions can help us find specific cells of data in a larger matrix.

The syntax is VLOOKUP (Search Value, Range, Column Number, Error) ==> look for a value in the row specified by Search Value and the column specified by Column Number.

Search Value indicates the “match key” (i.e., find the row that contains the Search Value in the first column).

Range specifies the cells containing the data.

Column Number specifies the column that contains the data element you want.

Error determines what happens when Excel does not find the exact Search Value you want.

• FALSE leads Excel to display a #N/A when an exact match cannot be found.

• TRUE leads Excel to display the next smaller value than Search Value.

![](OEBPS/images/f026-1.jpg)

Now suppose you want to extract the Political Party from the field above.

![](OEBPS/images/f026-2.jpg)

**Place your cursor in cell D2. Click the Formulas tab and select Insert Function.**

![](OEBPS/images/f027-1.jpg)

**In the Search for a function: text box, type “vlookup” and click on the Go button.**

![](OEBPS/images/f027-2.jpg)

![](OEBPS/images/f028-1.jpg)

• In the Lookup\_value text box, type “C2.”

• In the Table\_array text box, select the area Excel should use to find the description. Click the Party Codes worksheet and highlight the range A2:B45.

• In the Col\_index\_num field, type “2.” This is our index column from the Party Codes worksheet that contains the descriptions of the political parties.

• In the Range\_lookup, type “false” as we want exact matches.

![](OEBPS/images/f028-2.jpg)

Remember to Edit the Table array value by placing $ signs around the cell references. This makes the cell reference absolute.

Similarly, we will use HLOOKUP (Search Value, Range, Row Number, Error) ==> look for a value in the column specified by Search Value and the row specified by Row Number.

INDEX Function

![](OEBPS/images/f029-1.jpg)

\= INDEX (B3:F8, 4, 1)

Select the cells matrix: table (B3:F8) and specify the row number and column number (i.e., 4 and 1, respectively). This will fetch the value of Dept\_01 in April.

![](OEBPS/images/f029-2.jpg)

Similarly, you can apply “3” in the row number to fetch the values for March.

MATCH Function

This function identifies the location of a specific parameter in the specified list.

The MATCH function searches for a specified item in a range of cells and then returns the relative position of that item in the range. For example, if the range A1:A3 contains the values 5, 25, and 38, then the formula =MATCH (25, A1:A3, 0) returns the number 2 because 25 is the second item in the range.

Use MATCH instead of one of the LOOKUP functions when you need the position of an item in a range instead of the item itself.

Note that we used the parameter “0”in the syntax as we wanted an exact match.

![](OEBPS/images/f030-1.jpg)

If the range A1:A4 contains the values Nuts, Bolts, Washers, and Nails, then the formula =MATCH (“Bolts”, A1:A3, 0) returns the number 2 because Bolts is the second item in the range. Washers would return 3; Nails would return 4, and so on.

Now using “1” instead

Let’s say you want to fetch the value that is closest to a given value. Then we use the parameter “1” in the syntax.

So if we use MATCH (5000, D2:D16, 1), we get the value that is closest to 5,000.

The return information is 7.

Remember that the values must be sorted in ascending order for this utility to work.

![](OEBPS/images/f030-2.jpg)

 
| Match\_type || Behavior |
| --- | --- |
| **Match Type** || **Implications** |
| 1 or omitted || MATCH finds the largest value that is less than or equal to lookup value. The values in the matrix must be in ascending order. |
| 0 || MATCH finds the first value that is exactly equal to lookup value. |
| −1 || MATCH finds the smallest value that is greater than or equal to lookup value. The values in the matrix must be in descending order. |

INDEX with MATCH Function

The INDEX function combined with the MATCH function is useful when looking up values that are NOT in the leftmost column of a table, and hence the VLOOKUP cannot be used. In the table below, you want to look up the name of the person whose code number is AA105.

![](OEBPS/images/f031-1.jpg)

The formula =INDEX (A1:D5, MATCH (“AA105”, D1:D5, FALSE), 1) will return the correct value of Brown. The MATCH function inside the INDEX function identifies which row in the table contains AA105 (row 3). The INDEX function is then able to cross-reference that to column 1 of the table. The formula is thus returning what is in row 3 and column 1 of the table.

VLOOKUP with INDEX Function

The INDEX function can also be used in a VLOOKUP formula to identify the column that you want to return the value from. In the example below, the MATCH function is being used to return what’s in the Salary column (column number 3) for the employee Smith.

\=VLOOKUP (“Smith”, A1:D5, MATCH (“Salary”, A1:D1, FALSE), FALSE)

![](OEBPS/images/f032-1.jpg)

The formula would return £4,500. The MATCH function returns 3 (the position of the word Salary in the range A1:D1). The VLOOKUP then returns the value that is in column 3 for the person named Smith.

Pivot Table

This is a powerful tool for data analysis. It helps us generate summary information from a large database in a very short span of time.

It helps us assimilate a humungous quantum of data and create a compact table that can be changed dynamically. The tool is simple to use, yet powerful.

Suppose, from a total sales database, we are looking for a particular kind of classification like Customer-wise Sales.

The major features of a PivotTable are as follows:

A) It’s quick and easy to use.

B) You can churn data by simply dragging off fields, sorting and filtering, and applying different calculations on the data.

C) Create insights from data through suitable representation.

D) Create aesthetically soothing reports that are interactive in nature as well.

How You Create Pivot Tables

![](OEBPS/images/f033-1.jpg)

To create a blank PivotTable:

• On the Insert tab in the Tables group tab, click PivotTable to open the Create PivotTable dialog box.

• Select the data that you want to analyze (table or range within the open workbook or a connection to an external dataset).

• Select where you want to place the PivotTable: New Worksheet or Existing Worksheet and click OK.

Excel creates a PivotTable on a new worksheet. On the new sheet, a PivotTable and the PivotTable Fields List task panel are displayed. The panel displays the list of fields in a dataset and areas to place the fields to create the layout. These areas are used to organize data in columns, rows, values, and filters.

As seen in the lower right of the slide, there are four areas:

![](OEBPS/images/f034-1.jpg)

A) FILTERS—displays top-level filters above the PivotTable so that you can set filters to display results on the basis of particular conditions you set.

B) COLUMNS—displays columns of summarized data for the selected field(s).

C) ROWS—groups the data into categories in the first column on the basis of the selected field(s).

D) VALUES—displays summary statistics, such as totals or averages, for the selected field.

![](OEBPS/images/f034-2.jpg)

Fields can then be dragged from the Choose fields to add to report: list in the PivotTable Field List to the Report Filter, Column Labels, Row Labels, and Value boxes at the bottom of the PivotTable Field List.

Illustration

You can also use a pivot table to group data by numbers—summarizing data by age range, price range, or any numerical range that makes sense for your data. To illustrate, let’s assume you have a list of voting results that includes voter age, and you want to summarize the results by age group. Your data might look something like this:

![](OEBPS/images/f035-1.jpg)

The Basic Pivot Table

To get started on grouping the data by age, first create your pivot table normally. Next, add the field Age as a Row Label, and the field Vote as a Column Label. Finally, add Name as a Value. In the following example, we also renamed Grand Total “Total.” At this point, our pivot table looks like this:

![](OEBPS/images/f036-1.jpg)

Grouping by Age

Although this pivot table is interesting, it’s not very useful because the automatic grouping by actual age is too granular. We don’t care that five 20-year-olds voted for Option B—we want to see voting results by age ranges, like 20 to 29, 30 to 39, and so on. This is easily done using the grouping feature built into pivot tables. To group results by age, right-click any value in the Age field and choose Group from the menu.

![](OEBPS/images/f037-1.jpg)

Specifying the Interval

When the Grouping dialog box appears, enter any interval that makes sense in the “By:” input area. For this example, we’ll group by 10 years.

![](OEBPS/images/f038-1.jpg)

When you click OK, you’ll see your data neatly grouped by age at 10-year intervals.

![](OEBPS/images/f038-2.jpg)

You can use this same approach to group numeric data in many useful ways. You can group customers by total sales, group employees by their time at a company, group weather data by temperature—the list is endless.

Modify a PivotTable

![](OEBPS/images/f039-1.jpg)

To add a field as a row, you would do one of these steps:

• Click the field’s check box to select it in the Choose fields to add to report section.

• Drag the field from the Choose fields to add to report section, and drop it in the ROWS area.

• Right-click the field name in the Choose fields to add to report section, and select Add to Row Labels.

The sequence of the fields within the ROWS area dictates the hierarchy. In this example, we want to show the Areas within each Discipline for the textbook list. To show this hierarchy, list the Discipline field first and Area field second in the ROWS area.

![](OEBPS/images/f039-2.jpg)

As we saw with Rows, to add values to the PivotTable, you would do one of the following steps:

A) Click the field’s check box to select it in the Choose fields to add to report section.

B) Drag the field from the Choose fields to add to report section, and drop it in the VALUES area.

C) Right-click the field name in the Choose fields to add to report section, and select Add to Values.

• In this example, we are counting the number of books by titles (9 Aging/Death), finding the number of books sold (179,415 in the Introductory Discipline), and the sales ($21,273,970 for Research/Stats)

![](OEBPS/images/f040-1.jpg)

To subdivide data into columns, drag a field from the Choose fields to add to report section and drop it in the COLUMNS area. This slide shows a PivotTable that uses the Discipline field as rows, the Sum of Units Sold Wholesale field as values, and the Copyright field as columns. Each discipline label and each copyright year label appears only once in the PivotTable.

![](OEBPS/images/f041-1.jpg)

As you continue adding and arranging fields, the PivotTable may contain too much data to be useful, making it necessary to remove fields. You can remove fields to reduce the amount of data to analyze.

To remove a field from the PivotTable, you would do **one** of the following steps:

• Click the field name in the *Drag fields between areas below* section and select Remove Field.

• Click the check box next to the field name to deselect it in the *Choose fields to add to report* section.

• Drag a field name in the *Drag fields between areas below* section outside the PivotTable Fields List.

To move a field from one PivotTable area to another, you would do **one** of the following steps:

• Drag the field in the Drag fields between areas below section.

• Click the field arrow within the area and select Move to Report Filter, Move to Row Labels, Move to Column Labels, or Move to Values.

In this example, to remove the Units Sold Wholesale, deselect its check box. To move Area from ROWS to COLUMNS, drag it from one section to the other.

![](OEBPS/images/f042-1.jpg)

Apart from the default functions of SUM for numerical and COUNT for text fields, we might want to use other functions as well such as AVERAGE.

You can also change the column label that appears above the summary statistic, or you might need to format the aggregated values.

To modify any of these settings, you would:

• Click a value in the appropriate field in the PivotTable, and click Field Settings in the Active Field group on the Analyze tab to display the ValueField Settings dialog box.

• Type the name you want to appear as the column label in the Custom Name box.

• Select the summary statistical function you want to use to summarize the values in the *Summarize value field* by list.

• Click Number Format to open an abbreviated version of the Format Cells dialog box; then select a number type and click OK twice.

PivotTables are not automatically updated if you make any changes to the underlying data in the data source.

To update the PivotTable, you:

• Click in the PivotTable.

• Click the Analyze tab.

• Click Refresh in the Data group to refresh the current PivotTable only, or click the Refresh arrow and select Refresh All to refresh all PivotTables in the workbook.

Filter and Slice a PivotTable

![](OEBPS/images/f043-1.jpg)

PivotTables display aggregated data for each category. However, you may want to apply filters to show only a subset of the PivotTable. You can specify a particular field to filter the PivotTable.

To set a PivotTable filter, you:

• Drag a field to the FILTERS area in the PivotTable Fields List.

• Click the filter arrow in cell B1 to open the Filter menu and perform **one** of the following steps:

![](OEBPS/images/bl.jpg) Select the value in the list to filter the data by that value only.

![](OEBPS/images/bl.jpg) Click the Select Multiple Items check box if you want to select more than one value to filter the PivotTable. Click the check boxes by each value you want to set.

![](OEBPS/images/bl.jpg) Type a value in the Search box if the list is long and you want to find a value quickly.

• Click OK.

In this example, we are displaying values filtered for the 1, 2, 5, 7, 9 editions.

![](OEBPS/images/f043-2.jpg)

A slicer is a small window containing one button for each unique item in a field so that you can filter the PivotTable quickly.

To insert a slicer, you go to:

• The Analyze tab in the Filter group, and click Insert Slicer to open the Insert Slicers dialog box.

• Click one or more field check boxes to display one or more slicers and click OK.

![](OEBPS/images/f044-1.jpg)

When you select a slicer, the Slicer Tools Options tab is displayed so that you can customize a slicer.

The following list describes the commands on the Slicer Tools Options tab:

• Slicer—enables you to change the slicer caption.

• Slicer Styles—applies a style to the slicer by specifying the color of the filtered item in the Slicer.

• Arrange—specifies the slicer’s placement in relation to other groups.

• Buttons—defines how many columns are displayed in the selected slicer and the height and width of each button inside the slicer.

• Size—sets the height and width of the slicer window.

In this example for the two slicers:

• The active filters in the Edition slicer appear in blue, and unavailable items appear in light blue.

• There are two columns in the Edition slicer and one in the Discipline slicer.

• The Discipline slicer’s height is 3.13”.

![](OEBPS/images/f045-1.jpg)

A PivotTable timeline filters data on the basis of the date range selected. A PivotTable timeline is a small window that starts with the first date and ends with the last date in the data source, and it contains horizontal tiles that can be clicked to filter data by day, month, quarter, or year.

To insert a timeline and filter data on a timeline in a PivotTable:

• On the Analyze tab in the Filter group, click Insert Timeline to open the Insert Timelines dialog box.

• Click a field check box and click OK. Excel displays a timeline in the worksheet, and the Timeline Tools Options tab appears.

• Click the arrow by the current time level and select a time period: YEARS, QUARTERS, MONTHS, or DAYS.

• Click a tile on the timeline to filter data.

In this example, the tile level is MONTHS for the year 2018—JAN to DEC. Note the horizontal scroll bar at the bottom of the Timeline window, which is necessary to view JAN to APRIL.

![](OEBPS/images/f046-1.jpg)

Create a Calculated Field

![](OEBPS/images/f046-2.jpg)

Change the PivotTable Design

![](OEBPS/images/f046-3.jpg)

Pivot Charts

![](OEBPS/images/f047-1.jpg)

Pivot Chart is the graphical representation of a Pivot Table. It also provides a high degree of flexibility and enables us to extract the exact information.

A PivotChart is an interactive graphical representation of the data in a PivotTable and visually presents the consolidated data.

To create a PivotChart, you:

• Click inside the PivotTable.

• On the Analyze tab in the Tools group, click PivotChart.

The PivotChart contains elements that enable you to set filters.

• The ROWS area is replaced by AXIS (CATEGORY).

• The COLUMNS area is replaced by LEGEND (SERIES).

• The field used for the FILTERS area remains a field to use to filter data within the PivotChart.

• The field used for VALUES in a PivotTable remains a field that builds the plot area within the PivotChart.

Excel creates the PivotChart on the basis of the current PivotTable settings, but you can change the settings using the PivotChart Fields List.

• Click the FILTERS arrow and select values to filter the chart.

• Click the AXIS (CATEGORY) arrows to sort or filter the categories and subcategories in rows.

• Click the LEGEND (SERIES) to filter the chart on the basis of the values.

Note: Any changes you make to the PivotChart also affect the corresponding PivotTable.

Using the GETPIVOTDATA Function

This query can retrieve specific data on the basis of the pivot table structure of an existing pivot table.

To extract data from a cell in a pivot table, you can enter a normal cell link, such as =B5, or you can use the GetPivotData function, which is specially designed to extract data from a pivot table.

![](OEBPS/images/f048-1.jpg)

In the preceding example, the formula in cell A9 was created by typing an equal sign and then clicking on cell B5. It returns the total for file folders.

\=**GETPIVOTDATA (“Total”, $A$3,“Product”,“File Folders”)**

[CHAPTER 4](#05_contents.xhtml#r6)

[Excel for Decision Making](#05_contents.xhtml#r6)

The Goal Seek Command

What-If Analysis provides an ability to pursue the cycle of trial-and-error use of base numbers in formulas.

![](OEBPS/images/f049-1.jpg)

Using the Goal Seek Tool automates the process of changing one variable while calculating the function to get the value that you want.

A) Set cell: The cell that will display what you are trying to get. It must contain a formula.

B) To value: The value that you want. It must be numeric.

C) By changing cell: The cell that Excel changes.

Goal Seek is a tool, not a function.

The cell displaying the outcome must contain a formula that is somehow dependent on the variable cell.

You can reverse any changes using Undo.

![](OEBPS/images/f050-1.jpg)

Sensitivity Analysis with Data Tables

Excel is very powerful at making calculations.

Let’s say you the formula for Loan Payments set out as **PMT (rate,** nPeriods**,** pValue**)**

What if we want to see how our calculations change as we change the parameters?

We have multiple options:

  I. We can manually adjust the values and try to remember earlier results.

 II. We can copy the formula across many cells and use different inputs for each copy.

III. We can use the best approach: the Excel Data Table.

There are two different types of Data Tables:

A) **One-way** Data Tables: Allow you to change one parameter.

B) **Two-way** Data Tables: Allow you to change two parameters.

Create a One-Variable Data Table

A one-variable data table is a structured range that contains different values for one variable to compare how the different values affect one or more calculated results. For example, a one-variable data table is used to compare monthly payments on a mortgage. After determining the variables to manipulate, you need to specify the substitution values. A substitution value is a value that replaces the original input value of a variable in a data table. You can enter the substitution values yourself or use the Series dialog box to help complete a series of values.

To use the Series dialog box, you:

• Type the first substitution value and keep that cell as the active cell.

• On the Home tab in the Editing group, click Fill and then select Series to open the Series dialog box.

• Click Rows or click Columns to select the direction of the series of substitution values.

• Enter the value increment in the *Step value* box, enter the ending value for the series in the *Stop value* box, and click OK.

![](OEBPS/images/f051-1.jpg)

In this example, the first substitution value is 5 percent in cell D4; Columns is clicked, so the series of substitution values is down a column, the increment value is 0.5 percent, and the stop value is 9 percent.

After the substitution values have been added to a column or row, formulas must be added that relate mathematically to the variable that is used for the substitution values.

To complete the one-variable data table, you:

A) Select the data table boundaries, starting in the blank cell in the top-left corner of the data table. Drag down and to the right, and if there is more than one column, select the last blank cell at the intersection of the last substitution value and the last formula reference.

B) On the Data tab in the Forecast group, click What-If Analysis and select Data Table to open the Data Table dialog box.

C) Enter the cell reference of the cell containing the original variable for which you are substituting values. If the substitution values are listed in a row, enter the original variable cell reference in the Row input cell box. Similarly for a column, enter the original variable cell reference in the Column input cell box.

D) Click OK.

![](OEBPS/images/f052-1.jpg)

**Example: Car Loan Payments**

Let’s create a one-way Data Table: Car Loan Payments.

We borrow $20,000 from a creditor to buy a car.

Annual interest rate is 5 percent.

We plan to pay the loan in 36 months.

Our monthly payments can be calculated by the **PMT** function:

Monthly Payment = PMT (5/12, 36, 20,000)

How do our payments change as the **interest rate** changes?

Two-Way Data Tables

Excel Data Tables let us see the impact of change in parameters.

Two-way Data Tables: Allow us to change two parameters.

Create a Two-Variable Data Table

There are times when you might want to compare the results of a calculation on the basis of two variables. A two-variable data table is a structured range that contains different values for two variables to compare how these differing values affect the results for one calculated value.

For example, you might want to compare the combined effects of various interest rates and different down payments. Creating a two-variable data table is similar to the method used for a one-variable data table. For a two-variable data table, you use the top row for one variable’s substitution values and the first column for the other variable’s substitution values. The two-variable data table enables you to use two variables, but you are restricted to only one result instead of multiple results. Enter the formula or reference to the original formula in the blank cell in the top-left corner. For example, enter the cell reference for the monthly payment (=B12) in cell D3.

![](OEBPS/images/f053-1.jpg)

After entering the substitution values and the reference to one formula result, you are ready to complete the table to see the results.

To finish the two-variable data table:

• Select the data table boundaries, starting in the top-left corner of the data table.

• Drag down and to the right to select the last blank cell at the intersection of the last substitution value for both the column and the row.

• On the Data tab in the Forecast group, click What-If Analysis, and select Data Table to display the Data Table dialog box.

• Enter the cell that contains the original value for the substitution values in the first row in the Row input cell box. Enter the cell that contains the original value for the substitution values in the first column in the Column input cell box.

• Click OK.

![](OEBPS/images/f054-1.jpg)

**Example: Car Loan Payments**

Let’s create a one-way Data Table: Car Loan Payments

We borrow $20,000 from a creditor to buy a car.

Annual interest rate is 5 percent.

We plan to pay the loan in 36 months.

Our monthly payments can be calculated by **PMT** function:

Monthly Payment = PMT (5/12, 36, 20,000)

How do our payments change as the **interest rate and/or payment period** changes?

Using the Scenario Manager for Sensitivity Analysis

Allows multiple sets of what-if data to be entered and compared.

Each set is a scenario. Scenario Manager tracks each scenario with a name.

Each scenario can be reactivated and changed at any time.

The limitation is that the same cells are used for all scenarios.

![](OEBPS/images/f055-1.jpg)

Scenario summary report compares the scenarios together.

![](OEBPS/images/f055-2.jpg)

Optimization with Excel Solver

Excel has the capability to solve linear (and often nonlinear) programming problems.

The Solver tool in Excel

A) May be used to solve linear and nonlinear optimization problems.

B) Allows integer or binary restrictions to be placed on decision variables.

C) Can be used to solve problems with up to 200 decision variables.

Why You Need to Know This

It allows you to use linear programming to find the optimal inputs to achieve some desired calculation result (e.g., maximize revenues by increasing daily tickets, increasing store size, average sale/ticket, etc. simultaneously).

Use Solver instead of Goal Seek when:

• You need to place constraints on the input variable (e.g., cannot open a store for more than 24 hours a day).

• More than one input variable is involved.

• You want to minimize or maximize the resulting calculation in addition to just setting the calculation to a predetermined value.

Load the Solver Add-In

![](OEBPS/images/f056-1.jpg)

Add-ins are programs that can be added to Excel to provide enhanced functionality. Solver is an add-in application that searches for the best or optimum solution to a problem by manipulating the values for several variables within restrictions that you impose. You can use Solver to create optimization models. Optimization models find the highest, lowest, or exact value for one particular result by adjusting values for selected variables.

To load Solver, you:

Click the File tab and select Options.

Click Add-ins to see a list of active and inactive add-in applications.

Click the Manage arrow at the bottom of the dialog box, select Excel Add-ins, and then click Go to open the Add-ins dialog box.

Click the Solver Add-in check box in the Add-ins available list and click OK.

How You Use This Feature

The key to solving an LP on a spreadsheet is:

• **Objective cell**—specifies the cell that contains a formula that produces a value that you want to optimize (i.e., maximize, minimize, or set to a value) by manipulating values of one or more variables.

• Identify the decision variables that can be varied. These are called **Changing Cells.**

• Identify the cell that contains your objective function as the **Target Cell.**

• Identify the constraints and tell **Solver** to solve the problem.

• At this point, the optimal solution to our problem will be placed on the spreadsheet.

Case 1—Using Solver to Determine the Optimal Product Mix

![](OEBPS/images/f058-1.jpg)

To specify the objective and changing cells and constraints, you:

• Click Solver in the Analyze group on the Data tab to open the Solver Parameters dialog box.

• Enter the cell containing the formula for which you want to optimize its value in the *Set Objective* box.

• Click an option in the *To* section to specify what type of value you need to find for the target cell. In our example, you would click Min and then specify the value in the *Value Of* box.

• Enter the cell references that contain variables in the By Changing Variable Cells box.

• Click Add to the right of the *Subject to the Constraints* list in Solver Parameters to open the Add Constraint dialog box.

• Enter the cell reference, the operator to test the cell reference, and the constraint the cell needs to match.

• Click OK to add the constraint and return to the Solver Parameters dialog box, or click Add to add the constraint and create another constraint.

Remember:

• The objective cell would be the cell containing the total interest paid formula, which we would like to minimize.

• The changing variable cells would be the down payment and the number of years.

• The constraints could be that the down payment is between $5,000 and $8,000.

![](OEBPS/images/f059-1.jpg)

To create a Solver report, you:

• Click Solve in the Solver Parameters dialog box. When Solver completes the iterative process, the Solver Results dialog box appears. If it finds a solution, the Reports list displays available report types. If Solver cannot reach an optimal solution, no reports are available.

• Click Keep Solver Solution to keep the changed objective and variable values, or click Restore Original Values to return to the original values in the worksheet.

• Select a report from the Reports list and click OK.

Note: If you keep the changed values, Excel makes those changes to the actual worksheet.

![](OEBPS/images/f059-2.jpg)

Solver creates a new worksheet for the Solver summary report containing four major sections:

• The first section displays information about the Solver report.

• The second section displays the objective cell information. Specifically, this section shows the original and final objective cell values.

• The third section displays the variable cells. Specifically, it displays the cell references, the variable cell names, original values, and final values.

• The fourth section lists the constraints. It displays the cell reference, description, new cell value, formula, status, and slack for each defined constraint (not shown on the slide).

When you save a Solver model, you save the objective value, the changing variable cells, and the constraints.

To save Solver settings, you:

• Click Load/Save in the Solver Parameters dialog box.

• Click in the worksheet where the first cell is to be placed.

• Click Save to return to the Solver Parameters dialog box.

If you want to use an existing Solver model with new or updated data, you must return to a previous Solver model.

To use a Solver model that you saved, you:

• Click Load/Save in the Solver Parameters dialog box.

• Select the worksheet cells that contain the Solver data.

• Click Load to load the model’s values, and return to the Solver Parameter dialog box.

Introduction to Monte Carlo Simulation

We would like to be able to accurately estimate the probabilities of uncertain events. For example, what is the probability that a new product’s cash flows will have a positive net present value (NPV)? What is the riskiness of our investment portfolio? Monte Carlo simulation enables us to model situations that present uncertainty and play them out thousands of times on a computer.

The name Monte Carlo simulation comes from the computer simulations performed during the 1930s and 1940s to estimate the probability that the chain reaction needed for an atom bomb to detonate would work successfully. The physicists involved in this work were big fans of gambling, so they gave the simulations the code name Monte Carlo.

What Happens When I Enter =RAND () in a Cell?

When you enter the formula =*RAND ()* in a cell, you get a number that is equally likely to assume any value between 0 and 1.

![](OEBPS/images/f061-1.jpg)

Since RAND () is used as the probability, a random probability is generated at refresh.

![](OEBPS/images/f062-1.jpg)

• Next, highlight the area where we want to house the 1,000 iterations.

• Select Data > Data Tables.

• For Column input cell: Select a blank cell. In the download file, cell D11 is selected.

• Select OK.

![](OEBPS/images/f062-2.jpg)

Once OK is selected from the previous step, a table is inserted that auto populates the 1,000 simulations.

![](OEBPS/images/f063-1.jpg)

Once the simulations are run, it is time to gather summary statistics.

In this example, I used the COUNTIF () function to determine the percentage of simulations that are unprofitable, and the likelihood of a profit greater than $1 million.

![](OEBPS/images/f064-1.jpg)

This was gathered by using the COUNTIF () function to count the simulations that were less than zero and dividing by the 1,000 iterations.

[CHAPTER 5](#05_contents.xhtml#r7)

[Excel for Data Dashboards and Visualization](#05_contents.xhtml#r7)

What Is a Dashboard?

![](OEBPS/images/f065-1.jpg)

Business Intelligence is a hot commodity in today’s world, and dashboards are the most frequently used method of providing that information.

Through dashboards, we compile the data, in the form of analysis and charts.

The same should fit entirely on a single computer screen so it can be monitored at a glance.

Planning

At the planning stage, one must have a look at the following:

• Why are you creating a dashboard?

• Who is the audience?

• What are the KPIs (Key Performance Indicators) that you have to demonstrate?

• What is the time period, for example, a month, quarter, or year?

• What is the data source?

• What will be the frequency of its population and mode of delivery—online/offline?

It may be worthwhile to have a mock-up of the data that you seek to demonstrate through the dashboard on paper before you dive into Excel. Time spent here will save you hours of redesign later.

![](OEBPS/images/f066-1.jpg)

Importance of Design

Design can be quite a determinant of the data dashboard’s utility—can it convey your message quickly and easily, or does it hide it in a sea of formatting and chart junk like these donut charts and gauges?

![](OEBPS/images/f067-1.jpg)

While this dashboard may look aesthetic in the first instance, it’s cluttered with overuse of formatting and bad chart choices. Once users realize it’s taking them a long time to glean any meaningful information, it will lose its utility.

You need to strike a perfect balance between making it look striking (so that it holds your audience’s attention) but not so stylized that it takes away from the data to be presented.

A KISS (Keep It Simple Stupid) approach is best.

![](OEBPS/images/f067-2.jpg)

Charts are a useful tool in communicating messages through a picture. That is, the shape of the data contains a pattern, trend, or exception. Knowing which chart to use for your data and message is essential.

Design—Less Is More

![](OEBPS/images/f068-1.jpg)

When it comes to dashboard design, remember the maxim—“Less is More.” That is, less colors, less fonts, and less formatting.

Stay well away from 3D effects, gradient fills, shadows and any of the other unnecessary formatting.

If you have two charts displaying the same metric but in a different context, you might color them the same to show the reader that they are related. Just as in the previous example, the dashboard with the bar charts in the top 10 tables at the bottom, which both use the same color because they both display visitor numbers, just grouped differently.

Comparing Categories—Bar Graph

This is useful when we want to compare one concept with another as well as trends.

![](OEBPS/images/f068-2.jpg)

![](OEBPS/images/f069-1.jpg)

Line Graph

![](OEBPS/images/f069-2.jpg)

These graphs determine trends over a period of time.

Pie Chart

When you need a graph representing proportions of a whole

![](OEBPS/images/f070-1.jpg)

Tables

Tables are great if you have detailed information with different measuring units, which may be difficult to represent through other charts or graphs.

![](OEBPS/images/f071-1.jpg)

This table shows Customer Activity by Month through Customer | Total Sales | Percent of Total

Using the New, Modern Chart Types

Excel 2016 includes modern chart types that provide a rich, new set of storytelling tools that can be customized to fit your needs.

![](OEBPS/images/f071-2.jpg)

Waterfall

It’s a simple visual of the running total of your financial data, showcasing the element-wise change between, say, budgeted profit and actual profit.

Histogram

It displays the frequencies within a distribution. A histogram will help you explore and analyze a distribution.

Pareto

Here we can focus on the largest impact items by automatically sorting the frequency of the most prevalent issues (the bar graph) and then showing the additive contributions of each issue as we move along the horizontal axis (the line graph).

Box and Whisker

This shows the distribution of information and provides key insights about the distribution in one view, including range, quartiles, mean, and outliers.

Treemap

We can compare similar or competing products through a hierarchical view of your data and easily compare different levels of categorization.

Sunburst

Here, we can see the largest contributing segments within a hierarchy of multiple levels. The visual layout is intuitively natural for finding how each slice is broken down to the most basic contribution. The Sunburst is versatile, displaying any number of levels for any category.

For Colors

Fill Color and Font Color buttons offer a palette with preset colors. More colors are available by selecting one of many standard colors, or a custom combination of red, green, and blue.

![](OEBPS/images/f073-1.jpg)

[CHAPTER 6](#05_contents.xhtml#r8)

[Excel for Data Cleaning and Use of Macros](#05_contents.xhtml#r8)

Excel’s extensive functionality can best be judged by three of its most essential characteristics for the accountant:

A) Ease with which a user can convert and summarize thousands of lines of raw data, even if these are imported from other applications like SAP

B) Flexibility to accommodate changes at very short notice, thereby relieving somewhat the added pressure of tight deadlines; and

C) Formula/function structure underpinned by logical steps that are simple to follow

Importing data into Excel

Importing data into Excel from other applications in CSV, TXT format entails:

• Performing changes and formats on the data available

• Merging data from more than one source

• Summarizing data into tables

Some of the functions that are useful here are:

\=TRIM: Removes extra spaces

\=PROPER: Makes first letter in each word uppercase

\=CLEAN: Removes all nonprintable characters from text

\=VALUE: Converts text to number

\=TEXT: Converts number or text to new format

\=TRIM (PROPER ()): Removes extra spaces and capitalizes each word of text

\=VALUE (TRIM (CLEAN ())): Converts numbers to text and removes nonprintable characters

*Example*

![](OEBPS/images/f076-1.jpg)

Since the entire data is in a single column, it must be structured to perform data analysis. However, initially you need to clean the data.

You need to remove any nonprintable characters and excess spaces that might be present in the data. You can use the CLEAN function and the TRIM function for this purpose.

![](OEBPS/images/f076-2.jpg)

The result will be as shown below.

![](OEBPS/images/f077-1.jpg)

Now since the fields are delimited by the character “|”, you can use the **Convert Text to Columns** wizard.

• Select the data and copy and paste value. Otherwise, **Convert Text to Columns** takes the functions rather than the data as the input.

![](OEBPS/images/f077-2.jpg)

Click on Text to Columns in the Data Tools group under Data Tab on the Ribbon.

Convert Text to Columns Wizard—Step 1 of 3 appears.

Select Delimited.

Click Next.

![](OEBPS/images/f078-1.jpg)

Convert Text to Columns Wizard—Step 2 of 3 appears.

Under Delimiters, select Other and type the character |

Click Next.

![](OEBPS/images/f078-2.jpg)

Convert Text to Columns Wizard—Step 3 of 3 appears.

In this screen, you can select each column of your data in the wizard and set the format for that column.

• For **Destination**, select the cell D3.

• You can click **Advanced**, and set **Decimal Separator** and **Thousands Separator** in the **Advanced Text Import Settings** dialog box that appears.

• Click **Finish**.

![](OEBPS/images/f079-1.jpg)

Your data, which are converted to columns, appear in the three Columns—D, E, and F.

Name the Column headers as ProductID, Product\_Description, and Price.

![](OEBPS/images/f079-2.jpg)

Extracting Data Values with Text Functions

Suppose the fields in your data are neither delimited by a character nor aligned in columns with spaces between each field, you can use text functions to extract data values. Even if the fields are delimited, you can still use text functions to extract data.

Some of the text functions that are useful for this purpose are:

LEFT—Returns the leftmost characters from a text value

RIGHT—Returns the rightmost characters from a text value

MID—Returns a specific number of characters from a text string starting at the position you specify

LEN—Returns the number of characters in a text string

Macro

If you have tasks in Microsoft Excel that you do repeatedly, you can record a macro to automate those tasks. A macro is an action or a set of actions that you can run as many times as you want. When you create a macro, you are recording your mouse clicks and keystrokes. After you create a macro, you can edit it to make minor changes to the way it works.

Suppose that every month you create a report for your accounting manager. You want to format the names of the customers with overdue accounts in red and also apply bold formatting. You can create and then run a macro that quickly applies these formatting changes to the cells you select.

![](OEBPS/images/f080-1.jpg)

A macro is a set of instructions that executes a sequence of commands to automate repetitive or routine tasks. You can either use the Macro Recorder or type instructions using Visual Basic for Applications (VBA), which is a programming language that can be used within various software packages to enhance and automate functionality. The Macro Recorder records your commands, keystrokes, and mouse clicks and stores Excel commands as VBA code within a workbook. To use the macro record, you must first install it on the Ribbon.

To display the Developer tab on the Ribbon:

• Click the File tab and click Options to open the Excel Options dialog box.

• Click Customize Ribbon to display the Customize the Ribbon options.

• Click the Developer check box in the Main Tabs list to select it and click OK.

The slide shows that the Developer tab has been added. Take some time to familiarize yourself with the groups and buttons on this tab. Note: The Record Macro button, which we will discuss on the next slide.

![](OEBPS/images/f081-1.jpg)

Recording a macro is straightforward: You initiate the macro recording, perform a series of commands as you normally do, then stop the macro recording.

To record a macro:

• On the Developer tab in the Code group, click Record Macro to display the Record Macro dialog box.

• Type a meaningful name for the macro in the Macro name box.

• Assign a keyboard shortcut, if desired, for your macro in the Shortcut key box.

• Click the Store macro in arrow and select a storage location.

• Type a description of the macro and its purpose in the Description box, and click OK to start recording the macro.

• Perform the commands that you want to record.

• Click Stop Recording on the Developer tab.

![](OEBPS/images/f082-1.jpg)

It is important to determine whether your macro should use relative, absolute, or mixed references as you record the macro. By default, when you select cells when recording a macro, the macro records the cells as absolute references. If you want flexibility such that commands are performed relative to the active cell when you run the macro, click the Macros arrow in the Macros group on the View tab and select Use Relative References before you perform the commands.

To run a macro:

• Select the location where you will test the macro.

• On the Developer tab in the Code group, click Macros to display the Macro dialog.

• Select the macro from the Macro name list and click Run.

As seen in the slide, the ClearForm macro will be run. Because the macro was named with a meaningful name, we know that it will clear the contents of a form.

Create Macro Buttons

![](OEBPS/images/f083-1.jpg)

The simplest way to access frequently used macros within a workbook is to assign a macro to a button on a worksheet. That way, when you or other people use the workbook, it is easy to click the button to run the macro.

To add a macro button to a worksheet:

• On the Developer tab in the Controls group, click Insert, and then click Button (Form Control) in the Form Controls section of the Insert gallery.

• Drag the crosshair pointer to draw the button on the worksheet. When you release the mouse button, the Assign Macro dialog box is displayed.

• Select the macro to assign to the button and click OK.

• Right-click the button, select Edit Text, and type a more descriptive name for the button.

• Click the worksheet to complete the button.

• Click the cell that should be the active cell when the macro runs, and click the button to execute the macro assigned to the button.

![](OEBPS/images/f084-1.jpg)

We see that the ClearForm macro has been assigned to the button Clear Form and positioned on the worksheet below the form.

[CHAPTER 7](#05_contents.xhtml#r9)

[Excel for Auditors](#05_contents.xhtml#r9)

Benford’s Law

Benford’s law states that the probability of the first digit of the amount column from a huge database of normal transactions should follow the distribution as shown in the table.

 
| First Digit || Probability (percent) |
| --- | --- |
| 1 || 30.10 |
| 2 || 17.61 |
| 3 || 12.49 |
| 4 ||   9.69 |
| 5 ||   7.92 |
| 6 ||   6.69 |
| 7 ||   5.80 |
| 8 ||   5.12 |
| 9 ||   4.58 |

By examining our data against this distribution, we can make conclusions about the normalness of data.

We can Use LEFT(), COUNTIF() functions.

Univariate Statistics

Univariate Statistics mean the statistics relating to a single variable. Through this, we can find out the mean, median, mode, standard deviation, skewness, kurtosis, and various other statistical data relating to the variable. The study of these statistics can not only give a general idea about the behavior pattern of data but also form a support base for conducting further statistical analysis of the data.

Use the ADD-IN Analysis Tool pack—Descriptive statistics

Sampling

In audit, Sampling is used to provide a reasonable basis for the auditor to draw conclusions about the population from which the sample is selected. Sampling is done because it would be impossible to perform a Test of Detail for 100 percent transactions; or the cost of testing would likely exceed the expected benefit.

There are generally two sampling approaches:

1. Statistical sampling

2. Nonstatistical sampling (e.g., judgmental sampling)

Both sampling approaches require the exercise of auditor judgment during the planning, implementation, and evaluation of the sampling.

In some circumstances, statistical sampling is more appropriate because it can be measured and controlled.

Firms without the resources to purchase expensive audit software may consider using Excel to perform sophisticated statistical sampling methods.

Random Sampling

Random sampling ensures that all items within a population stand an equal chance of selection.

The random selection by manually picking any “n” number of transactions by ticking in a list what strikes the eye might be highly unscientific.

Excel provides a function RAND () to generate a random number.

With the support of an Add-In, it also provides the feature to generate multiple random numbers at one go, between a given set of range based on various settings.

These random numbers are based on random tables built within the computer and are thus more efficient.

Use the RAND () function or Analysis Toolpak > Random Numbers

Stratifying Data in a Pivot Table

We can stratify the data and prepare a frequency distribution of the data. This can be done for numeric fields as well as for the text fields in the data. The distribution of data can give us important information about the nature of the data and can also help us identify the areas where detailed tests should be conducted.

It can also help us prepare the list of key data on the basis of PARETO ANALYSIS, which states the 80 to 20 rule. For example, 20 percent of your customers contribute toward 80 percent of the sales.

We can use the COUNTIF () and SUMIF () functions or PIVOT TABLES.

Illustration

We can use a NESTED IF for stratification of data

\=IF (B4>1000, “3. Over $1000”, IF (B4>100, “2. Over $100 to $1,000”, IF (B4<=100, “1. Up to $100”)))

This will create three strata:

1. Up to $100

2. Over $100 to $1,000

3. Over $1,000

Start from highest to lowest—Excel picks the first matching item

Specific Accounts Payable Tests

1. (What) Summarize activity on the amount field (absolute value of debit or credit) to identify the top occurring amounts. Then summarize activity by vendor and the amount identified for the top 25 appearing.

2. (What) Extract payables that equate to round multiples of 10,000, 100,000, and 1,000,000.

3. (When) Extract transactions posted on weekends and holidays.

4. (When) Summarize activity by day, month, and year.

5. (Who) Summarize activity by user and month.

Calculating an Average DPO

![](OEBPS/images/f088-1.jpg)

Create a calculated field for check less invoice date (DPO)—in data or the Pivot.

Add sum of Invoice Amount and Average of newly calculated field.

Identify the Longest Time to Enter a Vendor Invoice

![](OEBPS/images/f088-2.jpg)

Audit Data Lying at Extremes (Outliers)

Sometimes, it might make audit sense to audit all the data lying at extremes (outliers). This can be easily identified using Excel’s Filter option once we decide the confidence level. It is usually taken that data lying outside MEAN ± (3 × STD DEV) give data that lie OUTSIDE the confidence level of over 99 percent for a normal distribution. Once we know the value of the above variables, we can filter the data for the outliers.

We can use Descriptive Statistics followed by AutoFilter.

Scatter Plot

Otherwise, we can use the Scatter Plot.

![](OEBPS/images/f089-1.jpg)

Scatter plots do not connect individual data points with a line but instead express a trend. This trend can be represented through the distribution of points or through the addition of a trend line/regression line.

The explanation for this is as follows:

![](OEBPS/images/f090-1.jpg)

1—High dollar change and low count (outliers)

2—Charges that make sense

3—Changes that don’t make sense

4—Inefficiency that is developing

Aging of Receivables

In audit, we often have to compute a schedule for aging of receivables.

Step 1

Label the following cells:

A1: Customer

B1: Order #

C1: Date

D1: Amount Due

Enter in the corresponding information for your customers and their orders underneath the headlines.

![](OEBPS/images/f090-2.jpg)

Step 2

Add additional headers for each column as:

E1: Days Outstanding

F1: Not Due

G1: 0 to 30 days

H1: 31 to 60 days

I1: 61 to 90 days

J1: >90 days

![](OEBPS/images/f091-1.jpg)

Step 3

Next, we will input a formula for the “Days Outstanding” column that will let us know how many days that invoice has gone unpaid since the due date.

In cell E2, enter in the following formula: = IF (TODAY ()>C2, TODAY ()-C2, 0)

![](OEBPS/images/f091-2.jpg)

Drag the formula till the end.

Drag the fill handler from cell E2 all the way to the last customer. This will populate the formula down the whole column so you do not have to enter it in over again.

![](OEBPS/images/f092-1.jpg)

Step 4

A separate window will open named “New Formatting Rule.”

Click the “Format Style” drop down and select 3-color scale.

Click the “Type” drop down and select Number.

Under “Values,” enter 0 for minimum, 60 for midpoint, and 90 for maximum.

Finally, select the colors that make the most sense for you, usually three colors that are very far apart on the color scale.

![](OEBPS/images/f092-2.jpg)

Your aging report Excel sheet should now look like

![](OEBPS/images/f093-1.jpg)

This same exercise can also be done using Pivot.

## [About the Author](#05_contents.xhtml#r10)

***Anurag Singal*** is a chartered accountant, with all-India ranks 22 and 25 in the CA Final and CA PE-II, respectively. He completed his PGPX (1-year MBA) from the Indian Institute of Management, Ahmedabad. He was CA Young Achiever—Manufacturing Sector at the 6th ICAI Awards, 2013, and has a decade of corporate finance experience across leading conglomerates in India.

Anurag has been a mentor of [cajobportal.com](http://cajobportal.com), India’s first recruitment site exclusively for chartered accountants. He has authored books such as Accounting for People Who Think They Hate Accounting and The Art and Science of Financial Modeling, published by Business Expert Press, USA, and Auditing Mantras in India. He has a YouTube channel on Careers and is a TEDx speaker as well.

## [Index](#05_contents.xhtml#r11)

Add-ins, [57](#11_chapter04.xhtml#page_57)

Aging of receivables, [90](#14_chapter07.xhtml#page_90)–[93](#14_chapter07.xhtml#page_93)

Analysis ToolPak add-in, [14](#09_chapter02.xhtml#page_14)

ANOVA, [16](#09_chapter02.xhtml#page_16)–[17](#09_chapter02.xhtml#page_17)

covariance, [18](#09_chapter02.xhtml#page_18)

Descriptive Statistics, [15](#09_chapter02.xhtml#page_15)–[16](#09_chapter02.xhtml#page_16)

histogram, [19](#09_chapter02.xhtml#page_19)

ANOVA, [16](#09_chapter02.xhtml#page_16)–[17](#09_chapter02.xhtml#page_17)

ANOVA: Single Factor, [14](#09_chapter02.xhtml#page_14), [17](#09_chapter02.xhtml#page_17)

Audit data lying at extremes (outliers), [89](#14_chapter07.xhtml#page_89)

Auditors

aging of receivables, [90](#14_chapter07.xhtml#page_90)–[93](#14_chapter07.xhtml#page_93)

Benford’s Law, [85](#14_chapter07.xhtml#page_85)

data lying at extremes (outliers), [89](#14_chapter07.xhtml#page_89)

illustration, [87](#14_chapter07.xhtml#page_87)–[88](#14_chapter07.xhtml#page_88)

random sampling, [86](#14_chapter07.xhtml#page_86)

sampling, [86](#14_chapter07.xhtml#page_86)

scatter plots, [89](#14_chapter07.xhtml#page_89)–[90](#14_chapter07.xhtml#page_90)

stratifying data in PivotTable, [87](#14_chapter07.xhtml#page_87)

Univariate Statistics, [85](#14_chapter07.xhtml#page_85)–[86](#14_chapter07.xhtml#page_86)

AVERAGE function, [9](#09_chapter02.xhtml#page_9)

AVERAGEIF function, [11](#09_chapter02.xhtml#page_11)

AVERAGEIFS function, [10](#09_chapter02.xhtml#page_10)–[11](#09_chapter02.xhtml#page_11)

Bar graph, [68](#12_chapter05.xhtml#page_68)–[69](#12_chapter05.xhtml#page_69)

Basic pivot table, [36](#10_chapter03.xhtml#page_36)–[39](#10_chapter03.xhtml#page_39)

Benford’s Law, [85](#14_chapter07.xhtml#page_85)

Bins\_array argument, [13](#09_chapter02.xhtml#page_13)

Box and Whisker, [72](#12_chapter05.xhtml#page_72)

Changing cell, [57](#11_chapter04.xhtml#page_57), [58](#11_chapter04.xhtml#page_58)

CHISQ.DIST.RT function, [9](#09_chapter02.xhtml#page_9)

CHISQ.TEST function, [9](#09_chapter02.xhtml#page_9)

CLEAN function, [75](#13_chapter06.xhtml#page_75)

Column Number, [25](#10_chapter03.xhtml#page_25), [28](#10_chapter03.xhtml#page_28)

Conditional math and statistical functions, [9](#09_chapter02.xhtml#page_9)–[23](#09_chapter02.xhtml#page_23)

Analysis ToolPak add-in, [14](#09_chapter02.xhtml#page_14)–[19](#09_chapter02.xhtml#page_19)

ANOVA, [16](#09_chapter02.xhtml#page_16)–[17](#09_chapter02.xhtml#page_17)

AVERAGEIFS, [10](#09_chapter02.xhtml#page_10)–[11](#09_chapter02.xhtml#page_11)

case exercise, [23](#09_chapter02.xhtml#page_23)

case study, [19](#09_chapter02.xhtml#page_19)–[22](#09_chapter02.xhtml#page_22)

correlation, [12](#09_chapter02.xhtml#page_12)–[13](#09_chapter02.xhtml#page_13)

COUNTIFS, [10](#09_chapter02.xhtml#page_10)–[11](#09_chapter02.xhtml#page_11)

covariance, [18](#09_chapter02.xhtml#page_18)

Descriptive Statistics, [15](#09_chapter02.xhtml#page_15)–[16](#09_chapter02.xhtml#page_16)

frequency distribution, [13](#09_chapter02.xhtml#page_13)

histogram, [19](#09_chapter02.xhtml#page_19)

measuring central tendencies, [11](#09_chapter02.xhtml#page_11)

standard deviation functions, [12](#09_chapter02.xhtml#page_12)

SUMIFS, [10](#09_chapter02.xhtml#page_10)–[11](#09_chapter02.xhtml#page_11)

variance functions, [12](#09_chapter02.xhtml#page_12)

CONFIDENCE.T function, [10](#09_chapter02.xhtml#page_10)

Convert Text to Columns wizard, [77](#13_chapter06.xhtml#page_77)–[79](#13_chapter06.xhtml#page_79)

CORREL (correlation coefficient) function, [13](#09_chapter02.xhtml#page_13)

Correlation, [12](#09_chapter02.xhtml#page_12)–[13](#09_chapter02.xhtml#page_13), [14](#09_chapter02.xhtml#page_14)

COUNT function, [10](#09_chapter02.xhtml#page_10)

COUNTA function, [10](#09_chapter02.xhtml#page_10)

COUNTIF function, [10](#09_chapter02.xhtml#page_10), [11](#09_chapter02.xhtml#page_11)

COUNTIF () function, [63](#11_chapter04.xhtml#page_63)–[64](#11_chapter04.xhtml#page_64)

COUNTIFS function, [10](#09_chapter02.xhtml#page_10)–[11](#09_chapter02.xhtml#page_11)

Covariance, [18](#09_chapter02.xhtml#page_18)

COVARIANCE.P function, [18](#09_chapter02.xhtml#page_18)

COVARIANCE.S function, [18](#09_chapter02.xhtml#page_18)

CUMIPMT function, [6](#08_chapter01.xhtml#page_6)–[7](#08_chapter01.xhtml#page_7)

CUMPRINC function, [6](#08_chapter01.xhtml#page_6)–[7](#08_chapter01.xhtml#page_7)

Dashboard

bar graph, [68](#12_chapter05.xhtml#page_68)–[69](#12_chapter05.xhtml#page_69)

defined, [65](#12_chapter05.xhtml#page_65)

design, [66](#12_chapter05.xhtml#page_66)–[73](#12_chapter05.xhtml#page_73)

Fill Color, [73](#12_chapter05.xhtml#page_73)

Font Color, [73](#12_chapter05.xhtml#page_73)

line graph, [69](#12_chapter05.xhtml#page_69)

modern chart types, [71](#12_chapter05.xhtml#page_71)–[72](#12_chapter05.xhtml#page_72)

pie chart, [70](#12_chapter05.xhtml#page_70)

planning stage, [65](#12_chapter05.xhtml#page_65)–[66](#12_chapter05.xhtml#page_66)

tables, [71](#12_chapter05.xhtml#page_71)

Data analysis

GETPIVOTDATA function, [48](#10_chapter03.xhtml#page_48)

HLOOKUP function, [25](#10_chapter03.xhtml#page_25)–[29](#10_chapter03.xhtml#page_29)

INDEX function, [29](#10_chapter03.xhtml#page_29)

with MATCH function, [31](#10_chapter03.xhtml#page_31)

MATCH function, [29](#10_chapter03.xhtml#page_29)–[30](#10_chapter03.xhtml#page_30)

with INDEX function, [31](#10_chapter03.xhtml#page_31)

PivotChart, [47](#10_chapter03.xhtml#page_47)–[48](#10_chapter03.xhtml#page_48)

PivotTable, [32](#10_chapter03.xhtml#page_32)–[46](#10_chapter03.xhtml#page_46)

VLOOKUP function, [25](#10_chapter03.xhtml#page_25)–[29](#10_chapter03.xhtml#page_29)

VLOOKUP with INDEX function, [31](#10_chapter03.xhtml#page_31)–[32](#10_chapter03.xhtml#page_32)

Data Analysis menu dialog box, [15](#09_chapter02.xhtml#page_15)

Data importing, [75](#13_chapter06.xhtml#page_75)–[79](#13_chapter06.xhtml#page_79)

Data Tables, [50](#11_chapter04.xhtml#page_50)

one-way, [50](#11_chapter04.xhtml#page_50)–[52](#11_chapter04.xhtml#page_52)

two-way, [53](#11_chapter04.xhtml#page_53)–[54](#11_chapter04.xhtml#page_54)

data\_array argument, [13](#09_chapter02.xhtml#page_13)

Decision making

goal seek command, [49](#11_chapter04.xhtml#page_49)–[50](#11_chapter04.xhtml#page_50)

one-way Data Table, [51](#11_chapter04.xhtml#page_51)–[52](#11_chapter04.xhtml#page_52)

sensitivity analysis

with Data Tables, [50](#11_chapter04.xhtml#page_50)–[54](#11_chapter04.xhtml#page_54)

Scenario Manager for, [54](#11_chapter04.xhtml#page_54)–[55](#11_chapter04.xhtml#page_55)

two-way Data Table, [53](#11_chapter04.xhtml#page_53)–[54](#11_chapter04.xhtml#page_54)

Descriptive Statistics dialog box, [16](#09_chapter02.xhtml#page_16)

Descriptive Statistics function, [14](#09_chapter02.xhtml#page_14)

illustration, [15](#09_chapter02.xhtml#page_15)–[18](#09_chapter02.xhtml#page_18)

End\_period argument, [7](#08_chapter01.xhtml#page_7)

Error, [25](#10_chapter03.xhtml#page_25), [28](#10_chapter03.xhtml#page_28)

Excel

for auditors, [85](#14_chapter07.xhtml#page_85)–[93](#14_chapter07.xhtml#page_93)

conditional math and statistical functions, [9](#09_chapter02.xhtml#page_9)–[23](#09_chapter02.xhtml#page_23)

data analysis, [25](#10_chapter03.xhtml#page_25)–[48](#10_chapter03.xhtml#page_48)

data cleaning, [75](#13_chapter06.xhtml#page_75)–[80](#13_chapter06.xhtml#page_80)

data dashboards and visualization, [65](#12_chapter05.xhtml#page_65)–[73](#12_chapter05.xhtml#page_73)

decision making, [49](#11_chapter04.xhtml#page_49)–[64](#11_chapter04.xhtml#page_64)

importing data into, [75](#13_chapter06.xhtml#page_75)–[79](#13_chapter06.xhtml#page_79)

macros, [80](#13_chapter06.xhtml#page_80)–[84](#13_chapter06.xhtml#page_84)

personal financial decisions, [1](#08_chapter01.xhtml#page_1)–[7](#08_chapter01.xhtml#page_7)

Extracting data values, using text functions, [79](#13_chapter06.xhtml#page_79)–[80](#13_chapter06.xhtml#page_80)

Factory production, case study, [19](#09_chapter02.xhtml#page_19)–[22](#09_chapter02.xhtml#page_22)

Fill Color, [73](#12_chapter05.xhtml#page_73)

Filter, PivotTable, [43](#10_chapter03.xhtml#page_43)–[46](#10_chapter03.xhtml#page_46)

Font Color, [73](#12_chapter05.xhtml#page_73)

Formula Bar, [13](#09_chapter02.xhtml#page_13)

Frequency distribution, [13](#09_chapter02.xhtml#page_13)

FREQUENCY function, [13](#09_chapter02.xhtml#page_13), [19](#09_chapter02.xhtml#page_19)

Future Values (FV) function, [1](#08_chapter01.xhtml#page_1)

GETPIVOTDATA function, [48](#10_chapter03.xhtml#page_48)

Goal Seek Tool, [49](#11_chapter04.xhtml#page_49)–[50](#11_chapter04.xhtml#page_50)

Histogram, [14](#09_chapter02.xhtml#page_14), [19](#09_chapter02.xhtml#page_19), [72](#12_chapter05.xhtml#page_72)

HLOOKUP (horizontal lookup) function, [25](#10_chapter03.xhtml#page_25)–[29](#10_chapter03.xhtml#page_29)

INDEX function, [29](#10_chapter03.xhtml#page_29)

with MATCH function, [31](#10_chapter03.xhtml#page_31)

with VLOOKUP function, [31](#10_chapter03.xhtml#page_31)–[32](#10_chapter03.xhtml#page_32)

Internal rate of return (IRR) function, [2](#08_chapter01.xhtml#page_2)–[4](#08_chapter01.xhtml#page_4)

IPMT function, [6](#08_chapter01.xhtml#page_6)

Keep It Simple Stupid (KISS) approach, [67](#12_chapter05.xhtml#page_67)

KURT function, [10](#09_chapter02.xhtml#page_10)

LEFT function, [79](#13_chapter06.xhtml#page_79)

LEN function, [80](#13_chapter06.xhtml#page_80)

Line graph, [69](#12_chapter05.xhtml#page_69)

Loan amortization table, [5](#08_chapter01.xhtml#page_5)

Macro

button creation, [83](#13_chapter06.xhtml#page_83)–[84](#13_chapter06.xhtml#page_84)

defined, [80](#13_chapter06.xhtml#page_80)

recording, [81](#13_chapter06.xhtml#page_81)–[82](#13_chapter06.xhtml#page_82)

running, [82](#13_chapter06.xhtml#page_82)

Macro Recorder, [80](#13_chapter06.xhtml#page_80)

MATCH function, [29](#10_chapter03.xhtml#page_29)–[30](#10_chapter03.xhtml#page_30)

with INDEX function, [31](#10_chapter03.xhtml#page_31)

MAX function, [10](#09_chapter02.xhtml#page_10)

Measuring central tendencies, functions for, [11](#09_chapter02.xhtml#page_11)

MEDIAN function, [10](#09_chapter02.xhtml#page_10)

MID function, [80](#13_chapter06.xhtml#page_80)

MIN function, [10](#09_chapter02.xhtml#page_10)

Minitab, [9](#09_chapter02.xhtml#page_9)

Modern chart types, [71](#12_chapter05.xhtml#page_71)–[72](#12_chapter05.xhtml#page_72)

MODE.SNGL function, [10](#09_chapter02.xhtml#page_10)

Monte Carlo simulation, [61](#11_chapter04.xhtml#page_61)–[64](#11_chapter04.xhtml#page_64)

NESTED IF, [87](#14_chapter07.xhtml#page_87)

Net Present Value (NPV) function, [1](#08_chapter01.xhtml#page_1)

Nonstatistical sampling, [86](#14_chapter07.xhtml#page_86)

Number of PERiods (NPER) function, [3](#08_chapter01.xhtml#page_3)–[5](#08_chapter01.xhtml#page_5)

Objective cell, [57](#11_chapter04.xhtml#page_57), [58](#11_chapter04.xhtml#page_58)

One-variable data table, [51](#11_chapter04.xhtml#page_51)–[52](#11_chapter04.xhtml#page_52)

One-way Data Tables, [50](#11_chapter04.xhtml#page_50)–[52](#11_chapter04.xhtml#page_52)

Pareto, [72](#12_chapter05.xhtml#page_72)

PARETO ANALYSIS, [87](#14_chapter07.xhtml#page_87)

PEARSON function, [10](#09_chapter02.xhtml#page_10)

Personal financial decisions, [1](#08_chapter01.xhtml#page_1)–[7](#08_chapter01.xhtml#page_7)

cumulative calculation functions, [6](#08_chapter01.xhtml#page_6)–[7](#08_chapter01.xhtml#page_7)

Future Values function, [1](#08_chapter01.xhtml#page_1)

internal rate of return function, [2](#08_chapter01.xhtml#page_2)–[4](#08_chapter01.xhtml#page_4)

IPMT function, [6](#08_chapter01.xhtml#page_6)

loan amortization table, [5](#08_chapter01.xhtml#page_5)

Net Present Value function, [1](#08_chapter01.xhtml#page_1)

NPER function, [4](#08_chapter01.xhtml#page_4)–[5](#08_chapter01.xhtml#page_5)

PPMT function, [6](#08_chapter01.xhtml#page_6)

Present Value function, [1](#08_chapter01.xhtml#page_1)

RATE function, [4](#08_chapter01.xhtml#page_4)–[5](#08_chapter01.xhtml#page_5)

Pie chart, [70](#12_chapter05.xhtml#page_70)

PivotChart, [47](#10_chapter03.xhtml#page_47)–[48](#10_chapter03.xhtml#page_48)

PivotTable, [32](#10_chapter03.xhtml#page_32)–[46](#10_chapter03.xhtml#page_46)

basic, [36](#10_chapter03.xhtml#page_36)–[39](#10_chapter03.xhtml#page_39)

creation, [33](#10_chapter03.xhtml#page_33)–[35](#10_chapter03.xhtml#page_35)

design, [46](#10_chapter03.xhtml#page_46)

features, [32](#10_chapter03.xhtml#page_32)

filter, [43](#10_chapter03.xhtml#page_43)–[46](#10_chapter03.xhtml#page_46)

illustration, [35](#10_chapter03.xhtml#page_35)

modify, [39](#10_chapter03.xhtml#page_39)–[42](#10_chapter03.xhtml#page_42)

slice, [43](#10_chapter03.xhtml#page_43)–[46](#10_chapter03.xhtml#page_46)

stratifying data in, [87](#14_chapter07.xhtml#page_87)

PivotTable Field List, [33](#10_chapter03.xhtml#page_33)–[34](#10_chapter03.xhtml#page_34)

PMT function, [50](#11_chapter04.xhtml#page_50)

PPMT function, [6](#08_chapter01.xhtml#page_6)

Present Value (PV) function, [1](#08_chapter01.xhtml#page_1)

PROPER function, [75](#13_chapter06.xhtml#page_75)

R, [9](#09_chapter02.xhtml#page_9)

RAND (), [61](#11_chapter04.xhtml#page_61), [86](#14_chapter07.xhtml#page_86)

Random sampling, [86](#14_chapter07.xhtml#page_86)

Range, [25](#10_chapter03.xhtml#page_25), [28](#10_chapter03.xhtml#page_28)

RATE function, [4](#08_chapter01.xhtml#page_4)–[5](#08_chapter01.xhtml#page_5)

RIGHT function, [79](#13_chapter06.xhtml#page_79)

Sampling, [86](#14_chapter07.xhtml#page_86)

SAS, [9](#09_chapter02.xhtml#page_9)

Scatter plots, [89](#14_chapter07.xhtml#page_89)–[90](#14_chapter07.xhtml#page_90)

Scenario Manager, for sensitivity analysis, [54](#11_chapter04.xhtml#page_54)–[55](#11_chapter04.xhtml#page_55)

Search Value, [25](#10_chapter03.xhtml#page_25), [28](#10_chapter03.xhtml#page_28)

Sensitivity analysis

with Data Tables, [50](#11_chapter04.xhtml#page_50)–[54](#11_chapter04.xhtml#page_54)

Scenario Manager for, [54](#11_chapter04.xhtml#page_54)–[55](#11_chapter04.xhtml#page_55)

Single-factor ANOVA report, [17](#09_chapter02.xhtml#page_17)

SKEW function, [10](#09_chapter02.xhtml#page_10)

Slice, PivotTable, [43](#10_chapter03.xhtml#page_43)–[46](#10_chapter03.xhtml#page_46)

Solver tool, [56](#11_chapter04.xhtml#page_56)–[57](#11_chapter04.xhtml#page_57)

determining optimal product mix, [58](#11_chapter04.xhtml#page_58)–[60](#11_chapter04.xhtml#page_60)

Specific accounts payable tests, [87](#14_chapter07.xhtml#page_87)

SPSS, [9](#09_chapter02.xhtml#page_9)

Standard deviation function, [11](#09_chapter02.xhtml#page_11)–[12](#09_chapter02.xhtml#page_12)

start\_period argument, [7](#08_chapter01.xhtml#page_7)

Statistical sampling, [86](#14_chapter07.xhtml#page_86)

STDEV.P function, [10](#09_chapter02.xhtml#page_10), [12](#09_chapter02.xhtml#page_12)

STDEV.S function, [10](#09_chapter02.xhtml#page_10), [12](#09_chapter02.xhtml#page_12)

Substitution value, [51](#11_chapter04.xhtml#page_51)

SUMIF function, [11](#09_chapter02.xhtml#page_11)

SUMIFS function, [10](#09_chapter02.xhtml#page_10)–[11](#09_chapter02.xhtml#page_11)

Sunburst, [72](#12_chapter05.xhtml#page_72)

*T*\-Test: Paired Two-Sample Assuming Unequal Variances, [14](#09_chapter02.xhtml#page_14)

*t-*Test: Paired Two-Sample for Means, [14](#09_chapter02.xhtml#page_14)

*t-*Test: Two-Sample Assuming Equal Variances, [14](#09_chapter02.xhtml#page_14)

Tables, [71](#12_chapter05.xhtml#page_71)

Target cell, [57](#11_chapter04.xhtml#page_57)

TEXT function, [76](#13_chapter06.xhtml#page_76)

Text functions, to extract data, [79](#13_chapter06.xhtml#page_79)–[80](#13_chapter06.xhtml#page_80)

Treemap, [72](#12_chapter05.xhtml#page_72)

TRIM function, [75](#13_chapter06.xhtml#page_75)

TRIM (PROPER ()) function, [76](#13_chapter06.xhtml#page_76)

Two-variable data table, [53](#11_chapter04.xhtml#page_53)–[54](#11_chapter04.xhtml#page_54)

Two-way Data Tables, [50](#11_chapter04.xhtml#page_50), [53](#11_chapter04.xhtml#page_53)–[54](#11_chapter04.xhtml#page_54)

Univariate Statistics, [85](#14_chapter07.xhtml#page_85)–[86](#14_chapter07.xhtml#page_86)

VALUE function, [75](#13_chapter06.xhtml#page_75)

VALUE (TRIM (CLEAN ())), [76](#13_chapter06.xhtml#page_76)

Variance function, [11](#09_chapter02.xhtml#page_11)–[12](#09_chapter02.xhtml#page_12)

VAR.P function, [10](#09_chapter02.xhtml#page_10), [12](#09_chapter02.xhtml#page_12)

VAR.S function, [10](#09_chapter02.xhtml#page_10), [12](#09_chapter02.xhtml#page_12)

Visual Basic for Applications (VBA), [80](#13_chapter06.xhtml#page_80)

VLOOKUP (vertical lookup) function, [25](#10_chapter03.xhtml#page_25)–[29](#10_chapter03.xhtml#page_29)

with INDEX function, [31](#10_chapter03.xhtml#page_31)–[32](#10_chapter03.xhtml#page_32)

Waterfall, [72](#12_chapter05.xhtml#page_72)

 

OTHER TITLES IN QUANTITATIVE APPROACHES  
TO DECISION MAKING COLLECTION

Donald N. Stengel, California State University, Fresno, *Editor*

• *Regression Analysis: Understanding and Building Business and Economic Models Using Excel, Second Edition* by J. Holton Wilson, Barry P. Keating, and Mary Beal-Hodges

• *Operations Methods: Managing Waiting Line Applications, Second Edition* by Kenneth A. Shaw

• *Using Statistics for Better Business Decisions* by Justin Bateh and Bert G. Wachsmuth

• *Applied Regression and Modeling: A Computer Integrated Approach* by Amar Sahay

• *The Art of Computer Modeling for Business Analytics: Paradigms and Case Studies* by Gerald Feigin

• *Data Visualization, Volume I: Recent Trends and Applications Using Conventional and* Big Data by Amar Sahay

• *Data Visualization, Volume II: Uncovering the Hidden Pattern in Data Using Basic and* New Quality Tools by Amar Sahay

• *Decision Analysis for Managers, Second Edition: A Guide for Making Better Personal and Business Decisions* by David Charlesworth

• *Conducting Survey Research: A Practical Guide* by John Fogli and Linda Herkenhoff

Announcing the Business Expert Press Digital Library

*Concise e-books business students need for classroom and research*

This book can also be purchased in an e-book collection by your library as

• *a one-time purchase,*

• *that is owned forever,*

• *allows for simultaneous readers,*

• *has no restrictions on printing, and*

• *can be downloaded as PDFs from within the library community.*

Our digital library collections are a great solution to beat the rising cost of textbooks. E-books can be loaded into their course management systems or onto students’ e-book readers.

The **Business Expert Press** digital libraries are very affordable, with no obligation to buy in future years. For more information, please visit **[www.businessexpertpress.com/librarians](http://www.businessexpertpress.com/librarians).** To set up a trial in the United States, please email **[sales@businessexpertpress.com](mailto:sales@businessexpertpress.com)**

![image](OEBPS/images/bcover.jpg)