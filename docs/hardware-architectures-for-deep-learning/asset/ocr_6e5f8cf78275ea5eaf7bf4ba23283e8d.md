# 224 Hardware architectures for deep learning

Newer and deeper CNNs (e.g., VGGNet and GoogleNet) deploy a single FC layer as opposed to three FC layers in AlexNet. Hence, the application of pruning to deeper CNNs increases the rate of FLOP count reduction as well as parameter count reduction in their iterative version. Note that the large set of parameters required for the FC from the memory accounts for a significant energy and execution delay.

Caffe provides a set of tools to benchmark models by calculating layer-by-layer execution delay, which reports system performance and measures relative execution times for CNN models. Using these tools, the average delay of each operation (e.g., MAC) in CONV layers is calculated to be 10x lower than the same operation for an FC layer. As a result, the reduction in the FLOP count through pruning is small, in the execution time and energy is significant.

# 9.10.4.2 Context-aware pruning policy for CONV layer

Figure 9.23 captures the result of filter pruning for the CON5 layer in iterations 2–7. Note that the CON5 of each iteration consists of 32 filters, and in each iteration, 5, 10 and 15 filters least affecting the top-5 classes from the previous iteration are pruned (i.e., $rm = 5, 10,$ and $15$ and $P_{ih} = 5$). The smart approach takes advantage of the feedback from previous iterations and depending on the remaining classes removes the least contributing filters, while the ignorant approach filters based on how strongly each filter contributes to the overall accuracy of the network across all classes and images in the training dataset. As illustrated in Figure 9.23, the contextual knowledge generated after each classification, and selective pruning of filters based on remaining classes significantly reduces the loss in classification accuracy when pruning filters.

![](bbox=[0.098, 0.638, 0.903, 0.803])

Figure 9.23 The accuracy of the CAPP policy for the last CONV layer (i.e., CON5) in iterations 2–7. The ignorant trend-line shows the results for pruning filters that least effect the accuracy for detection of all classes, while the smart trend-line shows the results for when feedback from previous iterations is used to prune the filters