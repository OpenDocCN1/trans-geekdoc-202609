The schematic flow of the process leading to the implementation of the fraud detection model can be broken down into three primary phases [2]:

+   1. *Data preprocessing*: problem description, identification and selection of data sources, data cleansing, data processing
+   2. *Data analysis and model creation*,
+   3. *Model management*: interpretation of the model results, model evaluation, implementation and maintenance of the model

The initial and fundamental element of the process is the identification of the business problem. Then potential data sources that can be used in the analysis are identified and selected by suitability in the context of the issue under consideration and availability. Once the data sources have been identified, a careful review and selection of variables take place. The next step is to clean the data and make the necessary transformations. These steps constitute the data preprocessing phase, which is generally the most time-consuming part of the process. After its completion, the proper analysis and creation of a fraud detection model may take place. The last phase relates to the model itself: its evaluation, interpretation of results, and – with satisfactory quality – implementation are performed. Figure 17.1 shows a diagram of the so-called fraud cycle in the banking fraud detection system (BFDS). It consists of four essential elements:

![](bbox=[0.117, 0.602, 0.824, 0.735])

**FIGURE 17.1** Fraud cycle.

*Source:* Authors’ study based on Baesens et al. [10].

+   1. *Detection*: a prediction made on new transactions and assigning each of them a probability of being fraudulent