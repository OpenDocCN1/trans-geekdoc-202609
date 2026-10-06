
(1) Report: Users can use the queries they create for great visualization with multiple pages and share them with others.

(2) Data: Users can view data in a report in a data model format that lets them add measures, create new columns, and manage relationships.

(3) Model: Users can obtain a graphical representation of the relationships that are set up in their data model and manage or modify as needed.

## 11.4 Data Import

Power BI Desktop lets import a variety of data, including databases, online services, and Excel spreadsheets.

Click on “Get Data” from the menu and select “More…” Click to see the various import methods.

### 11.4.1 Import Open Data from Data World

Find additional support for inserting data via the “Get Data” menu, as shown in Figure 11-7.

![](img/3c3c87d78136583581b0cf0620f5ae66_229_0.png)

Figure 11-7 Additional data import method

## 214 Machine Learning: Concepts, Tools and Data Visualization

![](img/3c3c87d78136583581b0cf0620f5ae66_230_0.png)

**Figure 11-8** Data World

![](img/3c3c87d78136583581b0cf0620f5ae66_230_1.png)

**Figure 11-9** Parameter value input pop-up window for importing data from Data World

Search and click on “Data World” as shown in Figure 11-8.
In order to import data from Data World as shown in Figure 11-9, users must enter information in the “Owner”, “Dataset Id”, and “Query” fields.

## Visualization with Power BI 215

![](img/3c3c87d78136583581b0cf0620f5ae66_231_0.png)

## Figure 11-10 Sample Site for Data Importing

The link in Figure 11-10 is as follows.
https://data.world/jonloyen/an-intro-to-dataworld-dataset
The reason for emphasizing the link is that the “Owner” and “Dataset Id” fields are essential to importing open data from Data World, as shown in the above address.

At the above link, “Jonloyen” is the owner, and “an-intro-to-dataworld-dataset” is the dataset Id.

## 216 Machine Learning: Concepts, Tools and Data Visualization

![](img/3c3c87d78136583581b0cf0620f5ae66_232_0.png)

Figure 11-11 Insert parameter value to import data from Data World

![](img/3c3c87d78136583581b0cf0620f5ae66_232_1.png)

Figure 11-12 Login Pop-up window for Data World

Extract the “Owner” and “Dataset Id” of the above link and enter it in the parameters shown in Figure 11-11.

As shown in Figure 11-12, an account is required to import data from “Data World”.

![](img/3c3c87d78136583581b0cf0620f5ae66_233_0.png)

![](img/3c3c87d78136583581b0cf0620f5ae66_233_1.png)

When data importing is successful after login, the “Load” appears, as shown in Figure 11-13.

After loading, you can check the data imported in Data World, as shown in Figure 11-14.

## 218 Machine Learning: Concepts, Tools and Data Visualization

![](img/3c3c87d78136583581b0cf0620f5ae66_234_0.png)

Figure 11-15 Data from “Data World” on Power BI

![](img/3c3c87d78136583581b0cf0620f5ae66_234_1.png)

Figure 11-16 How “Data World” data on Power BI is utilized

After data importing is complete, data will appear in the “Fields” palette as shown in Figure 11-15.

The graph in Figure 11-16 shows that the data has been imported without error.

## 11.4.2 Importing Excel File Data

To import an Excel data file, click the “Excel” button in the “Get Data” menu, as shown in Figure 11-17. Excel file extensions supported are .xl, .xlsx, .xlsm, .xlsb, .xls, and .xlw files. Text and CSV files can be imported via the “Text/CSV” button at the bottom.

After loading, you can check the details of the data entered in the Excel file, as shown in Figure 11-18.

![](img/3c3c87d78136583581b0cf0620f5ae66_235_0.png)

Figure 11-17 Data import method

![](img/3c3c87d78136583581b0cf0620f5ae66_235_1.png)

Figure 11-18 Data Success

## 220 Machine Learning: Concepts, Tools and Data Visualization

After data importing is complete, data will appear in the “Fields” palette, as shown in Figure 11-19.

The table in Figure 11-20 shows that the data has been imported without error.

![](img/3c3c87d78136583581b0cf0620f5ae66_236_0.png)

![](img/3c3c87d78136583581b0cf0620f5ae66_236_1.png)

## 11.5 Introduction of Power BI Visualization

To obtain meaningful patterns or business insight from the data set, visualization graphs suitable for the data set should be utilized. Explore the types of visualization that Power BI provides natively.

### 11.5.1 How to use Visualizations in Power BI

You can conveniently visualize inserted data through Power BI’s “Visualizations” menu. The “Visualizations” menu is shown in the upper corner of Figure 11-21. Data importing should precede the application of visualization. Then, select the graph to apply from the visualization menu. Finalize the graph by selecting the data to be applied. The graph in the upper-hand corner of Figure 11-22 can be freely adjusted by changing its size.

![](img/3c3c87d78136583581b0cf0620f5ae66_237_0.png)

Figure 11-21 Visualization provided by Power BI

## Machine Learning: Concepts, Tools and Data Visualization

![](img/3c3c87d78136583581b0cf0620f5ae66_238_0.png)

Figure 11-22 How to apply Power BI visualizations

![](img/3c3c87d78136583581b0cf0620f5ae66_238_1.png)

Figure 11-23 Result of Power BI visualization

In addition, more detailed graphs can be easily created by adjusting the data into the “Axis”, “Legend”, and “Value” fields in Figure 11-23.

## 11.5.2 Types of Visualization Chart

Figure 11-24 shows a stacked bar chart. A stacked bar chart is a chart with individual elements stacked horizontally making it easier to identify the contribution of individual elements to the total.

Figure 11-25 shows a stacked column chart. A stacked column chart is a chart with individual elements stacked vertically making it easy to identify the contribution of individual elements to the total.

![](img/3c3c87d78136583581b0cf0620f5ae66_239_0.png)

![](img/3c3c87d78136583581b0cf0620f5ae66_239_1.png)

Figure 11-26 shows a clustered bar chart. A clustered bar chart compares individual data values by representing them as horizontal bars.

Figure 11-27 shows a clustered column chart. A clustered column chart compares values of individual data by representing them as vertical bars.

![](img/3c3c87d78136583581b0cf0620f5ae66_240_0.png)

Figure 11-26 Clustered bar chart

![](img/3c3c87d78136583581b0cf0620f5ae66_240_1.png)

Figure 11-27 Clustered column chart

**Figure 11-28** 100% Stacked bar chart

**Figure 11-29** 100% Stacked column chart

Figure 11-28 shows a 100% stacked bar chart. A 100% stacked bar chart converts the sum of individual elements into 100%, representing the weight of individual data in horizontal bars.

Figure 11-29 shows a 100% stacked column chart. A 100% stacked column chart converts the sum of individual elements into 100%, representing the weight of individual data in vertical bars.

![](img/3c3c87d78136583581b0cf0620f5ae66_241_0.png)

![](img/3c3c87d78136583581b0cf0620f5ae66_241_1.png)

## 226 Machine Learning: Concepts, Tools and Data Visualization

![](img/3c3c87d78136583581b0cf0620f5ae66_242_0.png)

![](img/3c3c87d78136583581b0cf0620f5ae66_242_1.png)

Figure 11-30 shows a line chart. A line chart is suitable for determining trends in data time.

Figure 11-31 shows an area chart. An area chart makes it easy to identify the magnitude of data changes over time.

![](img/3c3c87d78136583581b0cf0620f5ae66_243_0.png)

Figure 11-32 Stacked area chart

![](img/3c3c87d78136583581b0cf0620f5ae66_243_1.png)

Figure 11-33 Line and Stacked column chart

Figure 11-32 shows a stacked area chart. A stacked area chart makes it easy to identify trends and contributions between data.

Figure 11-33 shows a line and stacked column chart. A line and stacked column chart is used to facilitate understanding of data when data values are broad.

Figure 11-34 shows a line and clustered column chart. A line and clustered column chart makes it easy to understand data if there is a wide range of data values.

Figure 11-35 shows a ribbon chart. A ribbon chart can quickly visualize data with the highest rank.

![](img/3c3c87d78136583581b0cf0620f5ae66_244_0.png)

## Figure 11-34 Line and Clustered column chart

![](img/3c3c87d78136583581b0cf0620f5ae66_244_1.png)

# Figure 11-35 Ribbon chart
