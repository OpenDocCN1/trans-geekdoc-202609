| | BERT MRPC | BERT SQuAD | BERT CoLA | BERT MNLI | DCGAN CIFAR10 | DCGAN MNIST | QANet SQuAD | RetinaNet COCO | ResNet ImageNet | Total TPUv2 | Total TPUv3 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| | Q.k-means k-means DBSCAN | Q.k-means k-means DBSCAN | Q.k-means k-means DBSCAN | Q.k-means k-means DBSCAN | Q.k-means k-means DBSCAN | Q.k-means k-means DBSCAN | Q.k-means k-means DBSCAN | Q.k-means k-means DBSCAN | Q.k-means k-means DBSCAN | | |
| Host Operations | | | | | | | | | | | |
| OutfeedDequeueTuple | O O O | O O O | O O O | O O O | O O O | O O O | O O O | O O O | O O O | 21 | 17 |
| TransferBuffer/InfeedLocked | O O O | O O O | O O O | O O O | O O O | O O O | O O O | O O O | O O O | 19 | 17 |
| Reshape | O O O | O O O | | O O O | O O O | O O O | O O O | | | 15 | 9 |
| Sqrt | O O O | O O O | | O O O | | O O O | O O O | | | 10 | 9 |
| Linearize32 | O O O | O O O | | O O O | O O O | O O O | | | | 9 | 5 |
| LR/AD | | | O O O | | O O O | | | O O O | | 8 | 9 |
| Infeed/DequeueTuple | O O O | O O O | | O O O | O O O | O O O | O O O | O O O | | 8 | 8 |
| InitializedHostPinnedDistributedTpu | | | | | | | | | | 7 | 3 |
| Reshape_1 | O O | | | O O | O O | | | | 4 | 6 |
| DisconnectHostFromDistributedTPUSystem | O | | O O | | O O | O | | O | | 3 | 0 |
| ReadVariable2 | | | | | | | | | | 4 | 1 |
| Recv | | | | | O | | | O O | | 1 | 1 |
| Min | | | | | | | | O O | | 1 | 1 |
| Maximum | | | | | | | | O O | | 1 | 1 |
| Minimum | | | | | | | | O O | | 1 | 1 |
| Sub | | | | | | | | O O | | 1 | 1 |
| DecodeAndCropJpeg | | | | | | | | | O O | | 1 | 1 |
| ResizeBicubic | | | | | | | | | | 1 | 1 |
| StartProgram | | | | | | | | | | 0 | 1 |
| BootstrapInitializer | | O O | | | O O | O O | O O | | | 0 | 12 |
| BuildLastOutput | O O | O O | | | | | | | | | 3 |
| TPU Operations | | | | | | | | | | | |
| fusion | O O O | O O O | O O O | O O O | O O O | O O O | O O O | O O | O O | 23 | 23 |
| MatMul | O O O | O O O | O O O | O O O | O O O | O O O | O O O | O O O | O O O | 15 | 15 |
| Reshape_1 | O O O | O O O | O O O | O O O | O O O | O O O | O O O | | | 15 | 18 |
| L2Loss | O O O | O O O | O O O | O O O | O O O | O O O | O O O | O | | 12 | 12 |
| Conv2DBackpropFilter | | | | | O O | | | O | O | 8 | 6 |
| Transpose | O O O | O O O | O O O | O O O | O O O | O O O | | | | 6 | 6 |
| BiasAddGrad | | | | | | | | | | 6 | 6 |
| CrossReplicaSum | | | | | O O O | | | | | 6 | 3 |
| ConcatenateV2/ConcatV2/output | | | | | O O O | O O O | | O | O | 5 | 5 |
| FusedBatchNormV3 | | | | | O O O | | | O O O | | 3 | 6 |
| Infeed | | | | | | O O | | | | 3 | 5 |
| all | | | | | | | O O O | | | 3 | 3 |
| ReduceWindow | | | | | | | | O O | | 3 | 3 |
| Copy | | | | | | | | O | | 1 | 1 |
| InfeedDequeueTuple | | | | | | | | O O | | 1 | 1 |
| FusedBatchNormGradV3 | | | | | | | | O O | | 1 | 2 |
| Relu | | | | | | | | O | | 1 | 1 |

TABLE II
THE TOP 5 MOST TIME-CONSUMING OPERATORS IN THE MOST TIME-CONSUMING PHASE USING DIFFERENT PHASE-DETECTION ALGORITHMS WITH TPUV2, SHOWN WITH O, TPUV3, SHOWN WITH [], AND <> FOR BOTH.

![](bbox=[0.12, 0.405, 0.46, 0.505])

Fig. 10. Idle time for TPUv2 and TPUv3 across workloads

![](bbox=[0.5, 0.405, 0.88, 0.505])

Fig. 12. Idle time for TPUv2 and TPUv3 across QANet, RetinaNet, and ResNet using smaller datasets

![](bbox=[0.12, 0.53, 0.46, 0.62])

Fig. 11. MXU utilization for TPUv2 and TPUv3 across workloads

![](bbox=[0.5, 0.53, 0.88, 0.62])

Fig. 13. MXU utilization for TPUv2 and TPUv3 across QANet, RetinaNet, and ResNet using smaller datasets

the top five operators generally remain consistent for TPUv2 and TPUv3 (as well as the host). Notably, k-Means and DBSCAN reach memory limitations for larger workloads such as RetinaNet and ResNet, which affirms that the TPUPoint-Analyzer/OLS combination can compete with clustering methods implemented in SimPoint [21], [22].
For TPUv3, the most time-consuming operators are the same as those for TPUv2 across workloads, but the total utilization of TPU resources changes. The QANet and RetinaNet workloads reduce flop utilization from about 16% on TPUv2 to 13% on TPUv3 for QANet and from about 46% on TPUv2 to 32% on TPUv3 for RetinaNet. The increased percentage of time required for infeed operations indicates the parameters related to memory operators such as outfeed need to change to fully utilize TPUv3. However, the observed differences are mainly due to the improved computational

capabilities of TPUv2 over TPUv3. The increased percentage of time observed for infeed implies that the non-computational overhead in the later-generation TPUs may be more significant.
Observation 5: the significance of non-computational overhead increases as computational throughput improves.

# C. Datasets

For the BERT and DCGAN workloads, we used different datasets to help understand the impact of inputs on the associated models. For BERT workloads with 4 different input datasets, the top 5 operators in Table III the TPU idle time in Figure 10 and the MXU utilization in Figure 11 are different, just as they are different for the two workloads that use the DCGAN model.