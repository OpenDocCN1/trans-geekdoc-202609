
## 4.7. Model Evaluation

Mean Square Error (MSE) is a statistical method for measuring the error between prediction output and ground truth information. The MSE equation is shown in Equation (4), where $n$ denotes the number of labels.

![](img/e4200cc4308edaf8913e513b0f96dbb6_210_0.png)

## 4.8. The Knowledge Distillation Architecture

The KD consists of the teacher model, a model with high complexity and accuracy, and the student model, a small structure; the teacher model helps the student model train easily. Moreover, the model trained by this technique will have lower accuracy than the teacher model but higher accuracy than the training itself. Also, the size of the model is smaller than the teacher model. Therefore, KD is applied to reduce the model size and improve the real-time performance of the teacher model. The structure is shown in Figure 16, and the configuration is shown in Figure 17. The student model structure used for training is shown in Figure 18, and the configuration is shown in Figure 19. In our implementation, we have set the temperature parameter to 10 and the alpha parameter to 0.1, the original values recommended in the reference source [29]. Additionally, we have used MSE as the loss function for both the student and distillation models.

![](img/e4200cc4308edaf8913e513b0f96dbb6_210_1.png)

Figure 16. An architecture of the teacher model training in the knowledge distillation process.

| Layer (type) | Output Shape | Param # |
| --- | --- | --- |
| input (InputLayer) | [(None, 15, 37)] | 0 |
| dense (Dense) | (None, 15, 128) | 4736 |
| tf.nn.softmax (TFOpLambda) | (None, 15, 128) | 0 |
| dropout (Dropout) | (None, 15, 128) | 0 |
| bidirectional (Bidirectional) | (None, 256) | 263168 |
| dropout_1 (Dropout) | (None, 256) | 0 |
| dense_1 (Dense) | (None, 128) | 32896 |
| dense_2 (Dense) | (None, 15) | 1935 |

Total params: 302,735
Trainable params: 302,735
Non-trainable params: 0

Figure 17. A configuration of the teacher model training in the knowledge distillation process.

![](img/e4200cc4308edaf8913e513b0f96dbb6_211_0.png)

Figure 18. An architecture of the student model training in the knowledge distillation process.

| Layer (type) | Output Shape | Param # |
| --- | --- | --- |
| input (InputLayer) | [(None, 15, 37)] | 0 |
| flatten (Flatten) | (None, 555) | 0 |
| dense (Dense) | (None, 256) | 142336 |
| dropout (Dropout) | (None, 256) | 0 |
| dense_1 (Dense) | (None, 15) | 3855 |

Total params: 146,191
Trainable params: 146,191
Non-trainable params: 0

Figure 19. A configuration of the student model training in the knowledge distillation process.

## 5. Experiment Results

To verify the effectiveness of our proposed method for QoL inference and knowledge distillation (KD) processes, we conducted experiments using Google Colaboratory. Google Colaboratory is a cloud computing service offering a Python environment and access to high-performance CPU and GPU resources. Specifically, our experiments utilized an Intel(R) Xeon(R) CPU @ 2.20 GHz as the CPU and a Tesla T4 GPU [30].

The results of our experiments are presented in this section, which consists of two subsections. Section 5.1 showcases the outcomes of the QoL prediction model, while Section 5.2 focuses on the results obtained from applying the KD process to the models.

### 5.1. The Result of the QoL Prediction Model

We set the experiments at 10,000 epochs for training with a 0.001 learning rate. Figures 20 and 21 show the training loss of the within-the-city experiment group and across-the-cities experiment group, respectively. The figures show MSE changes plotted as a graph every 50 epochs, with a total of 200 plotted points.

![](img/e4200cc4308edaf8913e513b0f96dbb6_212_0.png)

**Figure 20.** An example of loss graphs showing changes in each epoch of model training for the within-the-city experiment group.

![](img/e4200cc4308edaf8913e513b0f96dbb6_212_1.png)

**Figure 21.** An example of loss graphs showing changes in each epoch of model training for the across-the-cities experiment group.

The test results with the lowest MSE from the within-the-city experiment group and the across-the-cities experiment group setups are shown in Tables 6 and 7, respectively. The results in Table 6 indicate that the fully connected tanh activation function combined with bidirectional LSTM is the best model, winning 8 out of 12 within-the-city experiment sets. The results in Table 7 also indicate that the fully connected tanh activation function combined with bidirectional LSTM is the best model, winning in the across-the-cities experiment sets.

Table 6. The test results of the within-the-city experiment group.

| Training Dataset | Testing Dataset | Model Name | MSE |
|---|---|---|---|
| Canberra Scene2, Canberra Scene3 | Canberra Scene1 | Tanh bi LSTM 1 | $7.41 \times 10^{-3}$ |
| Canberra Scene1, Canberra Scene3 | Canberra Scene2 | Tanh bi LSTM 1 | $8.35 \times 10^{-3}$ |
| Canberra Scene1, Canberra Scene2 | Canberra Scene3 | Tanh bi LSTM 1 | $7.92 \times 10^{-3}$ |
| Bangkok Scene2, Bangkok Scene3 | Bangkok Scene1 | CONV1D bi LSTM 1 | $8.11 \times 10^{-3}$ |
| Bangkok Scene1, Bangkok Scene3 | Bangkok Scene2 | Tanh bi LSTM 1 | $7.55 \times 10^{-3}$ |
| Bangkok Scene1, Bangkok Scene2 | Bangkok Scene3 | CONV1D bi LSTM 1 | $8.62 \times 10^{-3}$ |
| Brisbane Scene2, Brisbane Scene3 | Brisbane Scene1 | Tanh bi LSTM 1 | $7.19 \times 10^{-3}$ |
| Brisbane Scene1, Brisbane Scene3 | Brisbane Scene2 | Tanh bi GRU 1 | $9.27 \times 10^{-3}$ |
| Brisbane Scene1, Brisbane Scene2 | Brisbane Scene3 | Tanh bi LSTM 1 | $7.55 \times 10^{-3}$ |
| Sakae Scene2, Sakae Scene3 | Sakae Scene1 | Tanh bi GRU 1 | $6.80 \times 10^{-3}$ |
| Sakae Scene1, Sakae Scene3 | Sakae Scene2 | Tanh bi LSTM 1 | $1.14 \times 10^{-2}$ |
| Sakae Scene1, Sakae Scene2 | Sakae Scene3 | Tanh bi LSTM 1 | $8.90 \times 10^{-3}$ |

Table 7. The test results of the across-the-cities experiment group.

| Training Dataset | Testing Dataset | Model Name | MSE |
|---|---|---|---|
| Bangkok Scene all, Brisbane Scene all, Sakae Scene all | Canberra Scene all | Tanh bi LSTM 1 | $9.73 \times 10^{-3}$ |
| Canberra Scene all, Brisbane Scene all, Sakae Scene all | Bangkok Scene all | Tanh bi LSTM 1 | $1.20 \times 10^{-2}$ |
| Canberra Scene all, Bangkok Scene all, Sakae Scene all | Brisbane Scene all | Tanh bi LSTM 1 | $1.16 \times 10^{-2}$ |
| Canberra Scene all, Bangkok Scene all, Brisbane Scene all | Sakae Scene all | Tanh bi LSTM 1 | $1.17 \times 10^{-2}$ |

### 5.2. The Results of the Knowledge Distillation

We apply the KD process to the fully connected tanh activation function combined with bidirectional LSTM as it is the model with the lowest MSE in both the within-the-city and the across-the-cities experiment groups. The distillation results of the within-the-city group are shown in Tables 8 and 9, while the distillation results of the across-the-cities group are shown in Tables 10 and 11.

**Table 8.** The MSE results of the within-the-city group.

| Training Dataset | Testing Dataset | Student Model MSE | Teacher Model MSE | Distilled Model MSE |
|---|---|---|---|---|
| Canberra Scene2, Canberra Scene3 | Canberra Scene1 | 2.92 | $7.16 \times 10^{-3}$ | $6.16 \times 10^{-2}$ |
| Canberra Scene1, Canberra Scene3 | Canberra Scene2 | 3.50 | $9.08 \times 10^{-3}$ | $5.24 \times 10^{-2}$ |
| Canberra Scene1, Canberra Scene2 | Canberra Scene3 | 3.62 | $8.26 \times 10^{-3}$ | $2.77 \times 10^{-2}$ |
| Bangkok Scene2, Bangkok Scene3 | Bangkok Scene1 | 3.40 | $6.09 \times 10^{-3}$ | $3.30 \times 10^{-2}$ |
| Bangkok Scene1, Bangkok Scene3 | Bangkok Scene2 | 3.49 | $8.46 \times 10^{-3}$ | $6.86 \times 10^{-2}$ |
| Bangkok Scene1, Bangkok Scene2 | Bangkok Scene3 | 4.04 | $6.93 \times 10^{-3}$ | $8.91 \times 10^{-2}$ |
| Brisbane Scene2, Brisbane Scene3 | Brisbane Scene1 | 3.93 | $7.74 \times 10^{-3}$ | $5.07 \times 10^{-2}$ |
| Brisbane Scene1, Brisbane Scene3 | Brisbane Scene2 | 3.666 | $7.26 \times 10^{-3}$ | $5.99 \times 10^{-2}$ |
| Brisbane Scene1, Brisbane Scene2 | Brisbane Scene3 | 3.567 | $6.53 \times 10^{-3}$ | $5.34 \times 10^{-2}$ |
| Sakae Scene2, Sakae Scene3 | Sakae Scene1 | 2.968 | $8.73 \times 10^{-3}$ | $4.80 \times 10^{-2}$ |
| Sakae Scene1, Sakae Scene3 | Sakae Scene2 | 3.632 | $9.45 \times 10^{-3}$ | $5.08 \times 10^{-2}$ |
| Sakae Scene1, Sakae Scene2 | Sakae Scene3 | 3.641 | $5.14 \times 10^{-3}$ | $2.93 \times 10^{-2}$ |
| Average MSE | | 3.530 | $7.57 \times 10^{-3}$ | $5.20 \times 10^{-2}$ |

**Table 9.** The computational time results of the within-the-city group.

| Training Dataset | Testing Dataset | Teacher Model Computational Time (ms) | Distilled Model Computational Time (ms) |
|---|---|---|---|
| Canberra Scene2, Canberra Scene3 | Canberra Scene1 | 7.518 | 1.271 |
| Canberra Scene1, Canberra Scene3 | Canberra Scene2 | 7.076 | 0.861 |
| Canberra Scene1, Canberra Scene2 | Canberra Scene3 | 6.804 | 0.893 |
| Bangkok Scene2, Bangkok Scene3 | Bangkok Scene1 | 6.830 | 0.908 |
| Bangkok Scene1, Bangkok Scene3 | Bangkok Scene2 | 7.100 | 0.868 |
| Bangkok Scene1, Bangkok Scene2 | Bangkok Scene3 | 7.023 | 0.836 |
| Brisbane Scene2, Brisbane Scene3 | Brisbane Scene1 | 7.051 | 1.306 |
| Brisbane Scene1, Brisbane Scene3 | Brisbane Scene2 | 6.867 | 0.893 |
| Brisbane Scene1, Brisbane Scene2 | Brisbane Scene3 | 6.991 | 0.948 |
| Sakae Scene2, Sakae Scene3 | Sakae Scene1 | 10.182 | 1.295 |
| Sakae Scene1, Sakae Scene3 | Sakae Scene2 | 7.208 | 0.882 |
| Sakae Scene1, Sakae Scene2 | Sakae Scene3 | 8.152 | 1.203 |
| Average Computation Time | | 7.400 | 1.014 |
