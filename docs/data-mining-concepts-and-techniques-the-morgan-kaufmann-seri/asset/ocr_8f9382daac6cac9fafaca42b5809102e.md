Table 9.4 Customer purchase data.

| Customer | P1 | P2 | P3 | P4 | P5 | P6 | P7 | P8 | P9 | P10 |
|---|---|---|---|---|---|---|---|---|---|---|
| Ada | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| Bob | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 |
| Cathy | 1 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 1 |

**Example 9.9. High-dimensional data and clustering.** Consider an e-commerce company that keeps track of the products purchased by every customer. As a customer-relationship manager, you want to cluster customers into groups according to what they purchased from the company.

The customer purchase data are of very high dimensionality. The company carries tens of thousands of products. Therefore a customer’s purchase profile, which is a vector of the products carried by the company, has tens of thousands of dimensions.

“Are the traditional distance measures, which are frequently used in low-dimensional cluster analysis, also effective on high-dimensional data?” Consider the customers in Table 9.4, where 10 products, P1, ..., P10, are used in demonstration. If a customer purchases a product, a 1 is set at the corresponding bit; otherwise, a 0 appears. Let us calculate the Euclidean distances among Ada, Bob, and Cathy. It is easy to see that

dist(Ada, Bob) = dist(Bob, Cathy) = dist(Ada, Cathy) = √2.

According to Euclidean distance, the three customers are equivalently similar (or dissimilar) to each other. However, a close look tells us that Ada should be more similar to Cathy than to Bob because Ada and Cathy share one common purchased item, P1.

As shown in Example 9.9, the traditional distance measures can be ineffective on high-dimensional data. Such distance measures may be dominated by the noise in many dimensions. Therefore clusters in the full, high-dimensional original data space may be unreliable, and finding such clusters may not be meaningful.

In general, when the dimensionality increases, the data space allows more and more complicated relations among objects. Such relations are harder and harder to detect using the traditional pairwise distance measurements. Moreover, high-dimensional spaces naturally allow more noise. This is known as the “curse of dimensionality.” More concretely, the curse of dimensionality is caused by the following four reasons.

+   • **Many irrelevant or correlated attributes.** Many attributes in a high-dimensional data set may not be relevant to an analytic task. For example, customer profiles may contain tens or even hundreds of attributes. Many attributes are or should be irrelevant to the task of credit card preapproval, such as gender, preferred language in communication, ethnic, purchases of dairy products, and distance to the store. Moreover, ideally the attributes in a data set are independent from each other, so that each attribute provides some independent and nonredundant information. However, in a high-dimensional data set, more often than not some attributes are correlated. Those correlated attributes provide redundant information in analysis and thus may lead to biases. For example, suppose microphones and webcams are often purchased together and thus have strong correlation. Then, when we include those two as independent attributes in clustering analysis, such as calculating the similarity between