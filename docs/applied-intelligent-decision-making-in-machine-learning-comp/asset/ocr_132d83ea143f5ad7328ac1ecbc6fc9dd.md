# Applied Intelligent Decision Making in Machine Learning

Queries

![](bbox=[0.252, 0.169, 0.747, 0.335])

FIGURE 1.1 General stream processing model.

Traditional algorithms developed for offline processing of the data are not suitable for streaming data due to these issues. There are few models that are incremental such as K-nearest neighbors (KNN) and naive Bayes. But, still, these models cannot cope with all the issues present in streaming data. For example, if there is a concept drift in the data, a separate concept-drift detection and alleviation technique needs to be developed. Many researchers have proposed various models for streaming data which takes care of the issues. We will look at some of these techniques in the coming sections.

As shown in Figure 1.1, a stream processor takes as input a stream of data such as 0, 1, 0, 1, ...... The processor can sample from the stream and process it in main memory, such when answering a query, and the result of the processing can be dumped into the back-end, such as the hard drive, for downstream tasks if required. Most of the algorithms presented in the subsequent sections will be based on this generic model.

Data mining finds application in several domains such as answering queries over the web, sensor data (Das et al., 2019; Dey et al., 2019), analyzing network packets, patient health monitoring, and surveillance systems to name a few. Because of the vast area of the field, I will present some selected case studies in the field at the end of the chapter.

The rest of the chapter are Research issues related to stream mining are discussed in Section 1.2. Section 1.3 elucidates the simple problems in streaming data such as filtering and counting. Sampling from a data stream is explained in Section 1.4, followed by concept drift detection in Section 1.5. Finally, the chapter ends with a discussion and an open problem in Section 1.6.

# 1.2 RESEARCH ISSUES IN DATA STREAM MINING

Knowledge discovery from a data stream is a challenging task due to reasons mentioned in the previous section. Most challenging is the unbounded size of the stream, low memory, and fast arrival rate. As a result, techniques proposed in the literature