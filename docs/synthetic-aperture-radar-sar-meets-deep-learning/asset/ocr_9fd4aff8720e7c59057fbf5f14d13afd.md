![](bbox=[0.185, 0.123, 0.858, 0.41])

Figure 20. CLE comparison of the three methods.

![](bbox=[0.175, 0.464, 0.848, 0.739])

Figure 21. FPS comparison of the three methods.

Table 4 shows the average tracking performance of the real Video-SAR data using the different methods. Due to the simple framework, MOSSE has the lowest performance, with 29.64% accuracy and 37.64 CLE, but the highest speed (125 FPS). Moreover, the deep learning methods improved the accuracy over the traditional correlation filtering methods (MOSSE and KCF), because the networks can extract multi-level and more expressive features. Most importantly, GA-SubNet in GASN only locates the sparse anchors containing the center of the shadow to suppress false alarms. Additionally, GA-SubNet refines the anchor’s shape to conform to the shape of the shadow, which further improves the tracking accuracy. Therefore, the accuracy of GASN (54.68%) is better than that of Siamese-RPN (52.75%) and Siamese-FC (41.60%). In addition, because the sparse anchors can reduce the