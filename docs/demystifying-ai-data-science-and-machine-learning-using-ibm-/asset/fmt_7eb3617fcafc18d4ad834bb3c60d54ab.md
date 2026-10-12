
These three nodes—K-means, TwoStep, and Auto Cluster—offer distinct approaches to clustering and are suited to different types of data and analytical needs. Each provides flexibility and ease of use in the SPSS Modeler environment.

## Example: Cluster Analysis

![](images/ufig13_17.jpg)

In this example, we perform a cluster analysis for the Airline Recommendation dataset.

*   Dataset: `AirlineRecommendation.sav`
*   Target Variable: `recommendation` (Flag: Yes/No)

### Variables for Cluster Analysis

[Table 13.4](#chapter13.xhtml#tbl13_4) presents the variables used in this cluster analysis. Since cluster analysis is an unsupervised learning technique, only input variables are considered. The target variable, `recommend`, is excluded from the analysis.

**TABLE 13.4** Airline Recommendation Data for Cluster Analysis [Return to text.⏎](#chapter13.xhtml#b13tbl13_4)

| Variable Name | Label/Description | Scale | Role |
| --- | --- | --- | --- |
| recommend | Recommend the airline to others | Binary (Yes/No) | None |
| airline_st | Airline status | Nominal | Input |
| Age | Age | Interval | Input |
| Gender | Gender | Binary (Male/Female) | Input |
| price_sensitivity | Price sensitivity | Interval | None |
| no_years_flying | Number of years flying | Interval | None |
| no_flt_pa | Average number of flights per year | Interval | Input |
| pct_flt_other_airline | Percent of flights with other airlines | Interval | None |
| type_of_travel | Travel purpose | Nominal | Input |
| no_other_lty_cards | Number of other loyalty cards | Interval | None |
| shopping_amt_airpt | Shopping amount at the airport | Interval | Input |
| eat_drink_airpt | Spending for eating and drinking at the airport | Interval | None |
| Class | Passenger class | Nominal | None |
| origin_state | Origin state | Nominal | None |
| destin_state | Destination state | Nominal | None |
| depart_delay | Departure delay (in minutes) | Interval | None |
| arrival_delay | Arrival delay (in minutes) | Interval | None |
| flt_cancel | Flight cancellation | Binary (Yes/No) | None |
| flt_time | Flight time (in minutes) | Interval | None |
| flt_distance | Flight distance (miles) | Interval | None |

The goal of this example is to group similar individuals based on shared characteristics in terms of their demographics and travel experience. For this purpose, we have selected six key variables for the cluster analysis, as highlighted in [Table 13.4](#chapter13.xhtml#tbl13_4):

*   `Age`
*   `Gender`
*   `Airline status` (e.g., Blue, Silver, Gold, Platinum)
*   `Average number of flights per year`
*   `Travel purpose` (e.g., Business, Personal, Mileage)
*   `Shopping amount at the airport`

474. These selected variables enable the identification of distinct market segments among the airline's passengers. The resulting clusters will allow the airline to better understand its customers and develop strategies to effectively target each market segment based on their travel behavior and preferences.

Other variables in the dataset, such as binary or irrelevant categorical fields, are rejected from this analysis to focus on the key factors that contribute to meaningful segmentation.

### Sample-Explore-Modify

Refer to the previous chapters for the details. As mentioned earlier, since cluster analysis is an unsupervised learning method, partitioning the data is not necessary. For this example, we will use the entire dataset for clustering.

### Cluster Modeling

To begin the analysis, we will use the `AutoCluster` node to quickly generate initial clustering results. The `AutoCluster` node is a useful starting point because it provides a fast and efficient means of exploring multiple clustering methods. We can use it to run both K-means and Two-Step cluster models and then compare the results. However, since this node is pre-configured, it does not allow for manual adjustments to the clustering configurations.

After reviewing these initial results, we will construct and run the K-means and Two Step Cluster nodes separately with custom configurations. This approach allows us to fine-tune the clustering process to better meet the specific needs of the airline recommendation dataset.

475.

#### Auto Cluster Node

Follow these steps to set up and run the `AutoCluster` node for the airline recommendation dataset:

1.  Create a new stream: Name it `Airline_Cluster`.
2.  Copy the necessary nodes: Open the existing stream `Airline_Tree` and copy the nodes from the data source up to the `Missing Value Imputation` node, including the `Type` node. Paste these into the new `Airline_Cluster` stream.
3.  Update variable roles:
    *   Open the settings for the `Type` node.
    *   Modify the roles of the variables as outlined in [Table 13.4](#chapter13.xhtml#tbl13_4). Make sure the fields for clustering are correctly identified.
    *   Click Apply to save the changes.
    ![](images/ufig13_18.jpg)
4.  Add the `AutoCluster` node:
    *   From the **Modeling** group, add an **Auto Cluster** node to the stream and connect it to the `Type` node.
    *   Open the `AutoCluster` node settings.
    ![](images/ufig13_19.jpg)
5.  Configure the Model tab:
    *   Uncheck the box labeled `Use partitioned data`.
    *   For `Rank models by`, select `Silhouette` to rank the models by the silhouette score.
6.  476. Configure the Expert tab:
    *   Select two models for comparison: `TwoStep` and `K-means`.
    ![](images/ufig13_20.jpg)
7.  Click Apply and then Run.

#### Results of the Auto Cluster Node

[Figure 13.7](#chapter13.xhtml#fig13_7) presents the results of the `AutoCluster` node, showing the comparison between the K-means model and the Two-Step model. According to the output, the K-means model utilizes five clusters, while the Two-Step model groups the data into two clusters. The models are ranked based on their Silhouette scores, with the K-means model achieving a score of 0.359, indicating a better fit than the Two-Step model, which has a Silhouette score of 0.309.

![FIGURE 13.7 Results of the Auto Cluster node. Return to text.⏎](images/fig13_7.jpg)

**FIGURE 13.7** Results of the Auto Cluster node. [Return to text.⏎](#chapter13.xhtml#b13fig13_7)

Although the `AutoCluster` node suggests using the K-means model due to its higher Silhouette score, there are considerations to note. One key observation is that the smallest cluster in the K-means model contains only 6% of the data, which may indicate an uneven distribution of clusters. Clicking on each model in the output allows for a deeper exploration of the cluster details.

A critical distinction between these models is how the number of clusters is determined. In the K-means model, the number of clusters must be predetermined—in this case, set to five by default. Conversely, the Two-Step model automatically determines the optimal number of clusters using BIC or AIC, without requiring a predefined number.

477. When choosing the number of clusters, it's important to balance capturing the complexity of the data with maintaining interpretability and generalizability. Having too many clusters can lead to overfitting, decreased model simplicity, and challenges in understanding and applying the results. Given this, reducing the number of clusters in the K-means model may yield more interpretable results without compromising the quality of the clustering.

Since the `AutoCluster` node does not allow for reconfiguring models, we will now conduct the individual K-means and Two-Step cluster models separately. This will enable us to adjust the number of clusters and compare the results more effectively.

#### Two-Step Cluster Node

Follow the steps below to set up the TwoStep Cluster node:
