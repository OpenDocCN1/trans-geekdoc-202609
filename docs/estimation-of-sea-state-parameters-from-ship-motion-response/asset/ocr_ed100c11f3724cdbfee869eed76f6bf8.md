# Table 2

An overview of the best performing hyperparameters for each model.

| Model | DATA_AUG | OPTIMIZER | LR | SCALE | MAXPOOL | BLOCKS | NUM HEADS | EMB SIZE | NUM EMB | HEADS NEURONS |
|---|---|---|---|---|---|---|---|---|---|---|
| CNN-REG-ORG | Row-wise | SGD | 0.005 | 3 | 1 | / | / | / | / | / |
| MLSTM-CNN-ORG | Batch-wise | SGD | 0.005 | 1 | / | / | / | / | / | / |
| SP-NN-ORG | Batch-wise | SGD | 0.005 | 5 | 1 | / | / | / | / | / |
| CNN-REG-ENH | Row-wise | ADAM | 0.0005 | 10 | 5 | / | / | / | / | / |
| MLSTM-CNN-ENH | Row-wise | ADAM | 0.005 | 5 | / | / | / | / | / | / |
| SP-NN-ENH | Batch-wise | ADAM | 0.00005 | 10 | 5 | / | / | / | / | / |
| AT-NN | Batch-wise | ADAM | 0.0005 | / | / | 2 | 2 | 125 | 128 | 128,64,3 |

+   - token size: 125, 250, 500,
+   - number of embeddings: 32, 64, 128, 256,
+   - number of neurons in fully connected layers consecutively: (128, 64, 3), (256, 128, 3), (512, 256, 3), and (1,024, 512, 3),
+   - Tested optimizers were ADAM and SGD both with learning rates α = 5·10⁻³, 5·10⁻⁴, 5·10⁻⁵ (Kingma and Ba, 2014; Bottou, 2012),
+   - Data augmentation: row-wise and batch-wise.

When considering the choice of the optimizers, it was decided to utilize the SGD to be consistent with the paper (Mak and Düz, 2019), and ADAM as the most popular optimizer. Other popular optimizers, such as RMS-prop (Zou et al., 2019) and ADAGRAD (Mukkamala and Hein, 2017), can also be utilized; however, this would not significantly affect methods performances and research conclusions. Maybe some models would converge faster or obtain better results, but the achieved results have shown satisfactory model performance and, hence, no need for further optimizer testing.

The model was trained with batch_size set to 32 for 250 epochs with early stopping if there was no change in loss function on the validation data set for 10 epochs. The best model consisted of 2 MHA blocks with 2 heads each, a token size of 125, and the number of embeddings set to 128. The number of neurons in dense layers was (128, 64, 3) respectively, while the optimizer was ADAM with a learning rate set to 5·10⁻⁴.

# 2.4. Hyperparameter overview, training setup and models' mechanisms

The overview of the best-performing hyperparameters for each model is given in Table 2. Since we trained a large number of models, the best performance (top 25), conducted with different hyperparameters, was achieved by those that used some kind of data augmentation. However, there is no evident distinction between the two types of augmentation (batch-wise and row-wise) in terms of the produced results.

The loss function was mean squared error (MSE) (James and Stein, 1992). The training process mentioned in Section 2.3.4 was the same for all models: batch size was always set to 32, with early stopping after there was no improvement on validation loss of 10 epochs. The constraint that the models are training for 250 epochs was never fulfilled because all models converged after the 100 to 150 epoch.

To understand the differences between the models, one needs to understand the mechanisms running the utilized models. The three original models (CNN-REG, MLSTM-REG, and SP-NN) proposed by the Mak and Düz (2019) rely on the popular mechanisms in the machine learning community. At the moment of their release, the models utilizing those mechanisms won various competitions (Russakovsky et al., 2015). The most straightforward mechanism utilized by CNN-REG (Fig. 8) is based on the plain 2D convolution. The 2D convolution learns different patterns, which helps extract useful information to predict the targeted variable. The issue with the convolution is that it scans “linearly” by moving the learned pattern (represented as the quadratic window) only to neighboring data in the input signal. This principle struggles with detecting the connection between scattered patterns in the input data/signal or finding cause-and-effect relationships between data patterns. Although, the convolution mechanism is easy to understand and optimize. To cope with the issues of cause-and-effect between the data parts, Mak et al. proposed a second neural

network called MLSTM-CNN (Fig. 9 based on long-short-term memory (LSTM) mechanism (Yu et al., 2019). The LSTM mechanism utilizes vectors that can remember the state of the part of the input while predicting the next part, which is particularly useful in natural language processing, where one word influences the words after it. In the studied case of estimating the sea state parameters from ship motion, it is evident that the sea state in time t_i influences the sea state in time t_{i+1}. Hence, remembering the previous state of the sea could be beneficial. In the architecture proposed by Mak and Düz (2019), the LSTM part is merged with the CNN-REG-like neural network as depicted in Fig. 9. During the training, we noticed that this model is slow to compute (due to the two branches). The last proposed model by Mak et al. tries to achieve the benefits of the LSTM mechanism by involving clever data augmentation mechanisms (batch-wise and row-wise augmentation), forcing the 2D convolutions to learn more advanced patterns. By doing so, the complexity of the model is not increased, so the output computation is quick. With these guidelines kept in focus, the neural network model named Sliding Puzzle (SP-NN, Fig. 10) is created. To increase the perceptive field, the SP-NN utilizes three different scales for feature aggregations (Max Pooling layers). This creates different views on the input signal features processed with the 2D convolutional layers. The mechanism resulted in quick calculations while being easy to understand. At the same time, thanks to innovative augmentation and different receptive fields’ sizes, capturing cause-and-effect relationships between different parts of the input signals is feasible.

Lastly, the novel model based on the attention mechanism follows the intuitions presented in paper (Vaswani et al., 2017) where it is argued that the mechanism performs better on many different tasks thanks to the capability to capture even long-term dependencies in the input data. LSTM and plain 2D convolutions on the mashed data cannot capture such long-term dependencies, so we believed utilizing the attention (and self-attention) mechanism as the feature extractors were the valid approach. Furthermore, regarding the mechanism’s complexities, the attention mechanism is far less complex than the LSTM mechanism and is similar to the 2D convolution. Hence, utilization of it is well justified. Also, we have investigated the possible enhancements to the models proposed by Mak et al.. The enhancements resulted in scaling the number of filters in convolutional layers. The introduced scaling increased the model’s capacity to learn different patterns, ultimately leading to better features (and, consequently, results). Simultaneously, the enhancements did not impair the original idea behind the models and their mechanisms.

Next, we provide the achieved results for all tested models and elaborate on their efficiency, advantages, and limitations.

# 3. Results and discussion

# 3.1. NN models performance

Evaluation of model performances is done separately for each sea state parameter: H_s, T_z, and β. We have calculated three metrics: mean squared error (MSE), mean absolute error (MAE), and Nash-SutcliffeEfficiency (NSE) (Chai and Draxler, 2014; Nash and Sutcliffe, 1970) on both validation and test sets. MSE and MAE are commonly used metrics in neural network evaluation, while NSE is a more rigorous metric originating from hydrology. Namely, when training NNs, it