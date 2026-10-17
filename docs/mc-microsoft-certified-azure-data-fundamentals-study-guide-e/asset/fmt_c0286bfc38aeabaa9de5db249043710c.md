
# When to Replace or Repair Equipment

Predictive maintenance models enable organizations that rely on machines to run their business (e.g., oil and gas companies or vending machine companies) to know when they should take proactive measures to repair or replace equipment.

# Fraud Detection

Fraud detection models will alert organizations if they find any suspicious transaction activity.

# Predictive Analysis

While descriptive and diagnostic analysis can be completed using traditional BI techniques, predictive analysis requires developers to have a more specialized skillset. Along with the need to properly maintain the historical data warehouse, solutions involving predictive analytics must maintain and regularly revisit model performance to ensure that the models are making well-informed decisions. While not in scope for this book, it is important to understand the tools and mechanisms used to maintain a machine learning model's life cycle. Azure Machine Learning and Apache Spark's MLflow enable data scientists to train, deploy, automate, and manage their machine learning models. These technologies allow data scientists to deploy models using container-based technologies such as Kubernetes or Azure Container Instances, which can be used by applications to make batch or real-time predictions.

## Prescriptive

Prescriptive analytics solutions are a step up from predictive analytics as they not only predict outcomes, but they also advise organizations on how to reach a desired outcome. These solutions use findings from descriptive, diagnostic, and predictive analytics techniques to answer questions about what actions should be taken to achieve a particular goal. Combinations of machine learning algorithms and business rules are used to simulate the outcomes of different input parameters. One example of the impact prescriptive analytics solutions can make is in the sports science field. Prescriptive analytics solutions not only predict when an athlete will experience a soft tissue injury but will also advise team doctors on what measures to take to prevent them. They can also be used to advise athletes on the most efficient training exercises for performing at their peak.

## Cognitive

Cognitive analytics solutions combine several artificial intelligence and machine learning techniques such as deep learning and natural language processing to draw inferences from existing data and patterns. This type of analytics will provide information based on existing knowledge bases and then add this information back into the knowledge base for future inferences.

This type of analytics takes inspiration from the way the human brain processes information. Instead of retrieving data via a query or creating analysis using structured development methods, cognitive analytics solutions are developed to derive more accurate inferences over time by learning from each interaction with data.

# Describe Data Visualization Techniques

Different analytics techniques provide a business with the information needed to make critical decisions moving forward but can be difficult to interpret if the findings are left as plain numbers. Data visualization refers to the process of graphically representing valuable information. The resulting infographics include charts, graphs, maps, and other objects that make information easy to read. Visualizations make it easy for analysts and business decision makers to see trends, outliers, and patterns in data. It is for this reason that using the most effective visualizations to represent information is critical to the storytelling process of data analytics.

Data visualization techniques come in a few different flavors. Depending on the purpose of the infographic and the skillset of the end users, data visualizations may be developed using one of the following three methods:

## Analytical Tools

Analytical tools allow users the ability to access and manipulate very granular levels of data. Tools like SQL Server Analysis Services (SSAS), Azure Analysis Services (AAS), and Power BI store data as OLAP models that can be filtered in a way that allow analysts to view calculated metrics for different scenarios. Data scientists can use tools such as Jupyter Notebooks to develop visualizations in a browser-based shell using Python or R. Using Python or R packages such as matplotlib or ggplot2, data scientists can build visualizations that are highly customized depending on what story they are trying to tell. Analysts and developers building infographics with analytical tools must have an intimate knowledge of the data that they are working with and must possess very specialized development skills. However, while analytical tools require the most complex set of skills to use, they provide users with the most flexibility in how they visualize information.

## Reporting Tools

Reporting tools give analysts the ability to organize data into informational summaries to monitor how different areas of the organization are performing. Traditional report tools such as SQL Server Reporting Services (SSRS) allow report builders to build static reports that use set filters to monitor business performance, only updating the displayed data when the dataset powering the report is refreshed. Modern technologies such as Power BI improve reporting capabilities by allowing users to dynamically alter the displayed data with filters, slicers, and interactive visualizations. This interactive capability empowers decision makers to consider multiple scenarios when determining the most appropriate course of action for their business. Reports are typically accessed by end users through an online portal such as `powerbi.com` and are only accessible to users with the appropriate level of access. You can learn more about Power BI security in [Chapter 6](#c06.xhtml), “Reporting with Power BI.”

## Dashboarding Tools

Dashboarding tools provide quick overviews of the most relevant pieces of information. Dashboards are designed to be easy to consume, allowing decision makers to act shortly after the data exposes new opportunities or threats. Tools such as Power BI allow analysts to collect the most relevant parts of a report to a decision maker and pin them to a dashboard.

Once a decision has been made on the most useful data visualization technique, it is important to choose the visual or visuals most appropriately suited for the data being displayed. Poorly chosen visuals can be hard to interpret or, worse, convey the wrong message. Another important aspect is the design of each visual. It's not enough to choose the correct chart or graph for the job, analysts must also be consistent with the aspect and color scheme for their visuals. This will help keep end users focused on any insights that are displayed rather than being overwhelmed by clashing color patterns and inconsistent sizing. End users should be able to quickly interpret the message each visual is telling with little to no explanation. The following sections include common visualizations used in analytical, reporting, and dashboarding tools. While these visualizations are popular and easy to build, there are countless more available for storytelling.

## Table

A table is a grid that contains data that is ordered in rows and columns. Tables work well with quantitative comparisons where you are evaluating many values for a single category. Technologies such as Power BI Paginated Reports and SSRS format large tables to fit onto multiple pages make them easier to read. This type of reporting is known as paginated and has been used in BI solutions for decades. [Figure 1.18](#c01.xhtml#c01-fig-0018) is an example of a table that lists the quantity sold and total sales amount for different bike subcategories sold online in different US regions.

![FIGURE 1.18 Table](images/c01f018.png)

[FIGURE 1.18](#c01.xhtml#R_c01-fig-0018) Table

## Matrix
