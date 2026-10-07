# # Statlog (Australian Credit Approval) Data Set

Download: Data Folder Data Set Description

**Abstract:** This file contains credit card applications. This dataset exists in the repository (Credit Screening Database) in a slightly different form

| Data Set Characteristics: | Number of Instances: 690 | Area: | Financial |
|---|---|---|--|
| Attribute Characteristics: | Categorical, Integer, Real | Number of Attributes: 14 | Date Dated N/A |
| Associated Tasks: | Classification | Missing Values? Yes | Number of Hits: 87829 |

+   - Link: https://archive.uci.edu/ml/datasets/statlog-australian-credit-approval

**Data Information:** This file concerns credit card applications. **Attribute names** and **values** have been changed to **meaningless symbols** to protect confidentiality of the data.

This dataset is interesting because there is a mix of *attributes – continuous, **nominal** with small numbers of values, and *nominal with larger numbers of values*. There are also few **missing values**.

That makes this problem more complex, difficult to solve for human. So clearly we need **deep learning model** to find the **cheaters**.

**Attribute Information:** There are **6 numerical** and **8 categorical attributes**. The *labels have been changed for the convenience of the statistical algorithms*. For example, **attribute 4** originally had **3 labels**, p, gg and these have been changed to **labels 1, 2, 3**.

```
A1: 0,1 CATEGORICAL (formerly: a,b)
A2: continuous.
A3: continuous.
A4: 1,2 CATEGORICAL (formerly: P,G,GG)
A5: 1, 2,3,4,5,6,7,8,9,10,11,12,13,14 CATEGORICAL (formerly: ff,dd,1,d,k,j,am,c,w,e,q,r,cc, x)
A6: 1, 2, 3,4,5,6,7,8,9 CATEGORICAL (formerly: ff,dd,j,bb,w,v,n,o,h,z)
A7: continuous.
A8: 0,1 CATEGORICAL (formerly: t, f)
A9: 1, 0 CATEGORICAL (formerly: t, f)
A10: continuous.
A11: 1, 0 CATEGORICAL (formerly: t, f)
A12: 1, 2, 3 CATEGORICAL (formerly: s, g, p)
A13: continuous.
A14: continuous.
A15: 1,2 class attribute (formerly: +,-)
```

> Basically, the independent variables are some *categorical* and *continuous* independent variables. And inside all there are **hidden some features** that we have detected.

+   - Role of SOM: The first thing to understand here is that the *columns are the attributes*, so these are the *informations of the customers*. There are **16 clusters**, which are different **15 features** as. The *lines/rows are the customers*.

+   - The unsupervised learning model is good to identify some patterns among the customers. It's good to do some kind of *customer segmentation* to **identify segments** of customers and one of the segments will contain **Fraud customers**.

+   - All those customers/rows are going to be on the self organizing map (SOM). It will actually very explicit, it corresponds to one specific range of values of the SOM.

* We are the inputs of our neural network. These input points are to be mapped to a new output space.