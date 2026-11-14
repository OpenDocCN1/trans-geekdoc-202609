# # 5 Experimental Results

To validate high-performance model training and reproducibility, the CareRecNet framework was experimentally tested in an entire computing environment. TensorFlow 2.8 and PyTorch 1.10 libraries were used in the implementation that used Python 3.9 for neural network building and training. A workstation-class computer with an Intel Xeon Gold 6,226 R processor, 64 GB of system RAM and an NVIDIA Tesla V100 GPU with 32 GB of video RAM were used for experiments. This configuration gave CareRecNet the computational muscle that it needed to cope with the extensive multi-modal data sets and intricate model architectures.

A selection of benchmark models from various algorithmic frameworks was considered for testing; an SVM classifier as a classic machine learning baseline; a decision tree-based recommendation model that estimates rule-based performance; and a classic LSTM network that processes sequential health data. To be able to make a fair evaluation, the models were optimized and trained with the same train test splits. Table 2 shows the process iterations.

Table 2: Process iterations.

| Iteration | Learning rate | LSTM units | Dropout rate | Batch size | Accuracy (%) |
|---|---|---|---|---|---|
| 1 | 0.001 | 64 | 0.2 | 32 | 87.30 |
| 2 | 0.0005 | 128 | 0.3 | 64 | 88.92 |
| 3 | 0.0001 | 128 | 0.4 | 32 | 89.78 |
| 4 | 0.001 | 256 | 0.3 | 64 | 90.03 |
| 5 | 0.0005 | 256 | 0.2 | 128 | 90.41 |
| 6 | 0.0003 | 256 | 0.3 | 64 | 90.77 |
| 7 | 0.0003 | 256 | 0.3 | 32 | 91.04 |
| 8 | 0.0003 | 256 | 0.2 | 32 | 91.21 |
| 9 | 0.0003 | 256 | 0.2 | 64 | 91.46 |
| 10 | 0.0003 | 256 | 0.1 | 64 | 91.60 |

The evaluation metrics selected were accuracy, precision, recall, and F1-score; these measures indicated the appropriateness of treatment suggestions as well as the consistency between detecting true positives and rejecting false negatives and false positives. Recall estimated how well the model was able to recall all relevant treatments, accuracy calculated the overall correct classification rate, precision measured the proportion of relevant treatment suggestions among all positive predictions, and the F1-score gave the harmonic mean of precision and recall, offering an overall measure of performance.

From Figure 2, with a staggering 91.6% accuracy, much higher than the baseline models, the accuracy plot clearly illustrates CareRecNet’s superiority in treatment suggestion tasks. At 84.2%, the conventional LSTM model was better than the decision