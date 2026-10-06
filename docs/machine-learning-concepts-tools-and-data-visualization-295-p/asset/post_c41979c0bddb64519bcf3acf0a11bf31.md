
## Chapter 12

## Visualization with R in Power BI

### 12.1 Introduction of R

If users proceed to deploy Azure Machine Learning Studio web service with R Studio, they will be able to proceed without any problem. However, there are some limitations when using R's visuals with Power BI Desktop:

- Data size limitations—data used by the R visual for plotting is limited to 150,000 rows. If more than 150,000 rows are selected, only the top 150,000 rows are used and a message is displayed on the image.
- Calculation time limitation—if an R visual calculation exceeds five minutes the execution times out, resulting in an error.
- Relationships—as with other Power BI Desktop visuals, if data fields from different tables with no defined relationship between them are selected, an error occurs.
- R visuals are refreshed upon data updates, data filtering, and data highlighting. However, the image itself is not interactive and cannot be the source of cross-filtering.
- R visuals respond when you highlight other visuals, but you cannot click on elements in the R visual in order to cross-filter other elements.
- Only plots that are plotted to the R default display device are displayed correctly on the canvas. Avoid explicitly using a different R display device.
- In this release, R installations are not automatically identified by the 32-bit version of Power BI Desktop, so you must manually provide the path to the R installation directory in **Options and settings > Options > R Scripting.**

### 12.2 How to use the R Script Editor

Click "R Script" in the "Visualization" category on the right side of Figure 12-1.
The R Script editor will appear, as shown in Figure 12-2.

![](img/3c3c87d78136583581b0cf0620f5ae66_260_0.png)

Figure 12-1 R Script Editor location

![](img/3c3c87d78136583581b0cf0620f5ae66_260_1.png)

Figure 12-2 R Script editor

Import the data, as shown in Figure 12-3 and click on the data you want to use in the R Script editor. If you check the data to use on the right, you can see that the script is automatically modified.

You can run the modified R Script by clicking on the box in Figure 12-4.

![](img/3c3c87d78136583581b0cf0620f5ae66_261_0.png)

# Figure 12-3 Import data in R Script editor

![](img/3c3c87d78136583581b0cf0620f5ae66_261_1.png)

# Figure 12-4 How to run R Script

![](img/3c3c87d78136583581b0cf0620f5ae66_262_0.png)

Figure 12-5 R Script execution result

You can see the R Script executed in Figure 12-5.

### 12.3 Visualization for Data Analysis Using Power BI R Script

Before applying visualizations for data analysis, let's learn about variables. Variables are divided into numerical data and categorical data according to their characteristics.

Numerical data such as length, power, and quantity is represented numerically, and category data such as gender and region is represented at predetermined levels. Numerical data has numerical values of attributes that are quantitative, and category data has levels of attributes that are qualitative.

Depending on the number of variables, the plot can be different. Unariate data is having one variable, and multivariate data means composed of several variables.

Let's take advantage of the Power BI R Script function to visualize data analysis according to the characteristics of the data.

### 12.3.1 Numerical Univariate Plot

Find additional support for inserting data through the “Get Data” menu, as shown in Figure 12-6.

Search and click on the “R Script”, as shown in Figure 12-7.

![](img/3c3c87d78136583581b0cf0620f5ae66_263_0.png)

![](img/3c3c87d78136583581b0cf0620f5ae66_263_1.png)

![](img/3c3c87d78136583581b0cf0620f5ae66_264_0.png)

Figure 12-8 Import tooth growth with R Script

Source (12-8)

```
Tooth_data <- ToothGrowth
```

Import the data supported by R to create the numerical univariate plot. Enter the source, as shown in Figure 12-8.

- **ToothGrowth data**
The ToothGrowth data set contains the results from an experiment studying the effects of vitamin C on tooth growth in 60 Guinea pigs. Each animal received one of three dose levels of vitamin C (0.5, 1, and 2 mg/day) by one of two delivery methods, orange juice or ascorbic acid (a form of vitamin C and coded as VC).
The attributes of the ToothGrowth data are “len", meaning tooth length, “supp", meaning support type (VC or OJ), and “dose", meaning the number of doses in milligrams/day.
After loading, you can check the ToothGrowth data, as shown in Figure 12-9.
After data importing is complete, users can note that data now appears in “Fields” as shown in Figure 12-10. Check the data in “Fields” on the right to import the data into the R Script.

![](img/3c3c87d78136583581b0cf0620f5ae66_265_0.png)

# Figure 12-9 ToothGrowth data

![](img/3c3c87d78136583581b0cf0620f5ae66_265_1.png)

# Figure 12-10 ToothGrowth data

Numerical data such as weight is continuous. In general, data such as height follows a normal distribution.

![](img/3c3c87d78136583581b0cf0620f5ae66_266_0.png)

# Figure 12-11 ToothGrowth data

![](img/3c3c87d78136583581b0cf0620f5ae66_266_1.png)

# Figure 12-12 ToothGrowth data

![](img/3c3c87d78136583581b0cf0620f5ae66_267_0.png)

# Figure 12-13 ToothGrowth distribution

![](img/3c3c87d78136583581b0cf0620f5ae66_267_1.png)

# Figure 12-14 ToothGrowth distribution

![](img/3c3c87d78136583581b0cf0620f5ae66_268_0.png)

# Figure 12-15 ToothGrowth distribution

![](img/3c3c87d78136583581b0cf0620f5ae66_269_0.png)

# Figure 12-16 ToothGrowth distribution

![](img/3c3c87d78136583581b0cf0620f5ae66_269_1.png)

# Figure 12-17 ToothGrowth distribution
