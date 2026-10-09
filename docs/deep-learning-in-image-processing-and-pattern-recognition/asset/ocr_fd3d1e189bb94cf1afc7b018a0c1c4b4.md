YOLOv7 has stronger feature extraction capability. It can solve the problem of low accuracy of small spot recognition in the early stage of grape leaf disease.

![](bbox=[0.08, 0.14, 0.48, 0.38])

![](bbox=[0.51, 0.14, 0.92, 0.38])

(a)

(b)

![](bbox=[0.08, 0.4, 0.48, 0.64])

![](bbox=[0.51, 0.4, 0.92, 0.64])

(c)

(d)

Figure 11. Performance comparison between YOLOv7 and the improved YOLOv7: (a) precision; (b) recall; (c) mAP@0.5; (d) mAP@0.5:0.95.

In order to verify the model detection effect after adding different improvements, the improved feature fusion network, improved E-ELAN module, improved CA attention module and SIoU loss function are ablated and analyzed. The comparison results of ablation experiments are shown in Table 6. As can be seen from the table, the mAP was significantly improved after the improvement of the feature fusion network, which shows that the low-level and high-level feature fusion and the addition of detection heads have played a very good role and significantly improved the detection performance. Adding improved E-ELAN and CA can obviously improve mAP, which shows that adding these two modules is effective. After using the SIoU loss function, the model diagram is slightly improved. Finally, it can be seen that the SIoU loss function not only accelerates the convergence of the model but also improves the detection performance of the model. In the table, “×” indicates that it was not added in YOLOv7, and “√” indicates that it was added in YOLOv7.