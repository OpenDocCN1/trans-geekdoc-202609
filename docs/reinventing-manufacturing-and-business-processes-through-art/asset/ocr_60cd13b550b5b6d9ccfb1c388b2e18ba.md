# 7.4.3.1 Data Preparation

Data preparation are mandatory to perform; otherwise, the information provided by these data may lead us to a wrong decision. Data cleaning tasks involve the detection of discrepancies and dirty data. Data transformation combines the raw attributes using different mathematical formulas originated in the manufacturing system or fuzzy mathematical formulas. Data is collected through various sensors in a different form from multiple machines in the industry, this data needs to be integrated by the integration method. Collected data from the sensor scales; for example, the RPM (revolutions per minute) data is enormous, while data of the depth of cut is tiny. Generally, data is normalized in the range of 0 to 1 and -1 to 1.

# 7.4.3.2 Data Reduction

Since the collected data is vast and there are many attributes contained, to improve the computation accuracy and to reduce the computational effort, it is very important to identify the important attributes and set of instances.

# 7.4.4 MODEL

Collected data can be analyzed using various statistical and machine learning algorithms (Figure 7.3). Collected data can be used for the following four purposes.

+   1. Descriptive analytics
2. Diagnostic analytics
3. Predictive analytics
4. Perspective analytics

# 7.4.4.1 Descriptive Analytics

In IoT-based industries, hundreds of sensors send the data. It is essential to infer meaningful information. Descriptive analytics is the lowest level of analytics. It is a tool for preparing a summary from the past data which can be easily understood. Mean, median, mode and the standard deviation are the tools of descriptive analytics. Pattern recognition is also an important part of descriptive analytics.

# 7.4.4.2 Diagnostic Analytics

Diagnostic analytics gives more detail as compared to descriptive analytics. Diagnostic analytics helps determine the root cause of the problems we have identified by descriptive analytics. As compared to descriptive analytics, diagnostic analytics requires high computation. Adaptive neuro-fuzzy interface system (ANFIS) combines the advantage of neural networks and fuzzy systems. ANFIS is a very effective tool for fault detection of multi-component systems (Moef et al., 2018). Stack denoising autoencoder (SDAE) is an effective and reliable deep learning tool for fault detection (Yu et al., 2019). The decision tree and clustering techniques are also used to detect faulty conditions (Kozek et al., 2017).