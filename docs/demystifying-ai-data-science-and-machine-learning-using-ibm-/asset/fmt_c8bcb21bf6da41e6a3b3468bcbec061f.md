
# Data Partitioning

In data mining, a popular strategy for assessing the quality of model generalization is to partition the data source. As mentioned earlier, overfitting can occur in data mining when a model is overtrained to achieve high accuracy. Such a model may perform poorly with a new dataset, raising concerns about its generalizability. In other words, the model works well with the training sample but is likely to fail when applied to different datasets.

To avoid this issue, we partition the data into multiple datasets. The **training sample** is used for preliminary model fitting. The remaining data are reserved for empirical validation and are typically split into two parts: the **test sample** and the **validation sample**. The test sample is used to evaluate the model and prevent overfitting. By comparing the results between the training and test samples, we can determine whether the model is generalizable. Finally, the validation sample is used for a final assessment of the model.

![](images/ufig3_32.jpg)

**TABLE 3.8** Sample Name Differences between SPSS Modeler and SAS Enterprise Miner [Return to text.⏎](#chapter3.xhtml#b3tbl3_8)

| Software | First Partition Sample | Second Partition Sample | Third Partition Sample |
| --- | --- | --- | --- |
| SPSS Modeler | Train | Test | Validation |
| SAS Enterprise Miner | Train | Validation | Test |

**Figure 3.6** illustrates how data partitioning works. Why do we need three subsamples for data mining purposes?

![FIGURE 3.6 Data partitioning. Return to text.⏎](images/fig3_6.jpg)

**FIGURE 3.6** Data partitioning. [Return to text.⏎](#chapter3.xhtml#b3fig3_6)

First, the **training sample** is used to train the model and identify one with a good model fit. Next, we apply this model to the **test sample** to evaluate and validate its performance. If the model does not validate successfully, we reconfigure the model, retrain it, and test the new version. This process is iterative and may require multiple trials and errors until we find a well-validated model. Finally, we use the **validation sample** to confirm the generalizability of this final model.

## Split Ratio

A common question in data partitioning is about the split ratio—how much of the data should be allocated to the training sample versus the validation and test samples? For example, a 60–40 split ratio typically means that 60% of the data go to the training sample, while the remaining 40% are divided between the validation and test samples. In this case, the 40% is usually split evenly, with 20% of the data used for testing and another 20% for final validation.

There is no standard rule for the split ratio. The literature suggests various ratios, ranging from 50–50, 60–40, 70–30, 80–20, to even 90–10. To determine the appropriate split ratio, it is essential to consider the size of the dataset. The rule of thumb is that the three samples must reflect data trends similar to those of the original dataset. Otherwise, sampling bias may occur, leading to a biased dataset and, ultimately, an invalid predictive model. It is also crucial to ensure that each sample has enough data points for modeling purposes. Typically, more data are allocated to the training sample to achieve a good model fit, but the validation and test samples should also have sufficient data points to evaluate and validate the model adequately. Therefore, data size is a critical factor.

For example, if the original dataset contains 100,000 data points, a 60–40 split ratio could be used, resulting in 60,000 records for training, 20,000 for testing, and 20,000 for final validation. This split could also be referred to as 60–20–20 for clarity. If the dataset has more than 1 million data points, a split ratio of 80–20 (or 80–10–10) may be appropriate, providing 800,000 records for training, 100,000 records for testing, and 100,000 records for final validation. On the contrary, if the sample size is small, with fewer than 1,000 data points, a 60–40 split ratio should be used without a validation sample. This ensures that the test sample contains enough data to evaluate the model effectively.

**Table 3.9** provides my recommended split ratios for different data sizes. Please note that these are general recommendations, and depending on the specific machine learning method used, adjustments to the split ratio may be necessary.

**TABLE 3.9** Recommended Split Ratio Based on the Sample Size [Return to text.⏎](#chapter3.xhtml#b3tbl3_9)

| Sample Size | Recommended Split Ratio |
| --- | --- |
| Fewer than 1,000 data points | 60–40 with no test sample (train: 60%; validation: 40%) |
| 1000–1 million data points | 60–20–20 (train: 60%; test: 20%; validation: 20%) |
| 1–10 million data points | 80–10–10 (train: 80%; test: 10%; validation: 10%) |
| More than 10 million data points | 90–5–5 (train: 90%; test: 5%; validation: 5%) |

## Example: Data Partitioning

![](images/ufig3_33.jpg)

This section demonstrates how to partition data in SPSS Modeler using the Airline Recommendation dataset. The software sets default values of 50–50–0 for three subsamples. Since we have more than 100,000 data points, we will partition our dataset into three subsamples using a split ratio of 60–40. Specifically, 60% of the data will be used for training, 20% for testing, and 20% for final validation.

*   **Dataset:** `AirlineRecommendation.sav`
*   **Target variable:** `Recommend` (Flag: Yes/No)

Follow the steps below to partition the data.

1.  Open the stream `Airline_Sample`.
2.  We should have the data node and Type node created before.
3.  From the Field Ops group in the Node Pallet, add a **Partition** node to the stream and connect it to the **Type** node.

    ![](images/ufig3_34.jpg)

4.  Open the settings window of this node.
5.  Under the Settings tab, select **Train, test, and validation** for **Partition**.
6.  Set the **Training partition size** to **60**, the **Testing partition size** to **20**, and the **Validation partition size** to **20**.

    ![](images/ufig3_35.jpg)

7.  Click **Apply**, and then click **OK**.

SPSS Modeler will partition the data according to the size and split ratio we predefined. The results are presented in **Table 3.10**. As you can see, the software has successfully split the original data into three subsamples: training, test, and validation. The percentage of each subsample is very close to the desired split ratio.

**TABLE 3.10** Data Partitioning Results—Number of Observations by Sample [Return to text.⏎](#chapter3.xhtml#b3tbl3_10)

| Type | Number of Observations | Percent |
| --- | --- | --- |
| Training sample | 74,747 | 60.6 |
| Test sample | 24,862 | 19.98 |
| Validation sample | 24,855 | 19.97 |

Add a Type node to the Partition node, and you will notice that a new nominal field, `Partition`, has been added to the dataset. This nominal field enables us to train a model using the training sample and then test it with the test sample.

![](images/ufig3_36.jpg)

One important thing to keep in mind is that the partitioning process is done randomly while preserving all the characteristics of the original dataset. **Figures 3.7** and **3.8** show the partition results for `recommendation` and `airline status`. As you can see, the imbalance ratio for `recommendation` was maintained at 52.5% across all three subsamples, just as in the original dataset. Similarly, the ratio across the four levels of `airline status` remains consistent across the subsamples, mirroring the original dataset. This indicates that our partition samples are representative of the full dataset. In other words, it is safe to train and test our model using these subsamples.

![FIGURE 3.7 Partition results for the recommendation field. Return to text.⏎](images/fig3_7.jpg)
