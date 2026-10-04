Data Capture and Client Architecture for a Cloud-Based Real-Time ... 399

3. The response is then displayed on the GUI. Figure 4.82 means that 1231 packets are estimated to be received using MLR and 1272 packets, with MLP regression.

![](bbox=[0.231, 0.172, 0.768, 0.327])

Figure 4.82. Obtaining the regression results.

4. The “Classify” button is used for classification analytics by taking as input the values currently being monitored. These values are displayed as an indication to which values have been taken as input.

![](bbox=[0.289, 0.458, 0.711, 0.573])

Figure 4.83. Clicking the “Classify” button.

5. As observed in Figure 4.83, the values used for classification are displayed in the panel. The URL that contacts the servlet, in this case, is http://networkcloud-eu-gb.mybluemix.net/ml?downloadSpeed=4363&uploadSpeed=258&packetsReceived=2995&packetsSent=2788&predictionTime=10&window=20&device=1&action=1&source=1. The results obtained from the servlet are displayed in the panel. Figure 4.84 shows that the KNN and MLP algorithms determined the status of the PC to be “streaming.”

![](bbox=[0.241, 0.773, 0.759, 0.928])

Figure 4.84. Obtaining the classification results.