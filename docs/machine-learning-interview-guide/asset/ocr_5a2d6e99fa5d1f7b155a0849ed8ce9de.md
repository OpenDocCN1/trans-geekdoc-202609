We can either decrease the high-volume class or increase the low-volume class. Now we can use a variety of techniques to achieve the same as previously mentioned.

We can either use one or a combination of the following to achieve the same:

+   - Random under-sampling or random oversampling.
+   - Using business logic to understand the end goal and trim some of the data from high-volume class.
+   - Using tomek links for undersampling
+   - Synthetic oversampling.

# Question 14: Explain the concept of bias in ML models.

Answer: Generally, ML models contain two forms of bias. The first kind of bias is identified at the data collection and the data preprocessing stage, and then there is another type of bias which is more technical and is actually what most people mean when they use the term bias. In ML, bias is defined as an error that is inherent in a model’s predictions. It happens when a model imposes constraints it if there exists a relationship in the data that the model is unaware of or does not allow for.

# Question 15: What are the advantages of using stratified sampling when splitting data?

Answer: It is worth mentioning that there can be several types of sampling conducted, but only two fundamental: random sampling and stratified sampling.

Random sampling will be given as chunks of random samples from all the classes but the distribution of these samples will in no way preserve the source class distribution. Thus, the stratified sampling will make sure