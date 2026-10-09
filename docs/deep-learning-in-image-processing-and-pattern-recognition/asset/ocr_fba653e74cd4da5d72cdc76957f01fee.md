are divided by temperature (T). When comparing soft labels and soft predictions, this creates a loss result which is called distillation loss. Student loss, another loss result, is from comparing predictions of trained student models to the ground truth. To obtain the total loss of the proposed system with this paper, we multiply these two results of loss with weights and then sum them. The weight of distillation loss is one minus alpha. The weight of student loss is alpha. A pseudo code of this process is shown in Figure 6.

```
Constant value is temperature and alpha
Function distillationLoss (Argument teacher output, Argument student output) {
Divide argument teacher output by temperature to get teacher soft label
Divide argument student output by temperature to get student soft label
Return Compare teacher soft label with student soft label by distillation loss function
}
Function calculateTotalLoss (Argument student loss result, Argument distillation loss result) {
Return alpha x argument student loss result + (1 - alpha) x argument distillation loss result
}
Function knowledgeDistillation (Argument input, Argument target) {
Predict student output by student model with argument input
Compare student output with argument target by student loss function to get student loss result
Predict teacher output by pre-trained teacher model with argument input
Send predicted student output and predicted teacher output to the distillationLoss function to get the distillation loss result
Send student loss result and distillation loss result to the calculateTotalLoss function to get total loss result
Use total loss result to adjust weights of student model
}
```

**Figure 6.** A pseudo code of knowledge distillation.

In summary, our proposed method consists of two steps: QoL inference and performance improvement. The QoL inference step involves the application of image recognition, DNN, RNN, and bidirectional network approaches to generate QoL inference. In the performance improvement step, knowledge distillation (KD) is applied to reduce complexity and increase the model’s performance, resulting in reduced processing speed. However, it is essential to note that there is a trade-off in this process, as the accuracy may be slightly decreased.

# 4. Proposed Methods

This section provides details of the processes in our proposed QoL evaluation methods. Section 4.1 describes the overview of our framework, consisting of two steps, QoL inference and KD processes. Section 4.2 describes the dataset used in this research and shows the label used to compare with the prediction results. Section 4.3 describes the feature extraction from images using image recognition models. Section 4.4 describes the architecture used to train the QoL score model and shows the hyperparameters used to configure the architecture. Section 4.5 shows how to process the input and output data before the training step. Section 4.6 describes the training strategy and how to group the dataset. Section 4.7 shows the measuring equation used to evaluate the results. Section 4.8 shows the configuration, hyperparameters, and small architecture used as the student model and final architecture that is used as the teacher model for the KD process.

# 4.1. Our Framework

Our framework is composed of two processes; the first one is the QoL inference process, and the second one is the KD process.