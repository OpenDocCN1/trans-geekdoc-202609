
- (i) The input layer of a CNN receives various types of data, such as retinal images or clinical records associated with diabetes;
- (ii) Convolutional layers employ learnable filters to extract significant features from the input data;
- (iii) Activation functions introduce non-linearity to capture complex relationships between features;
- (iv) Pooling layers are an important layer in CNN systems that decreases the dimensionality of the feature maps;
- (v) Fully connected layers connect neurons and learn high-level representations for output predictions;
- (vi) A loss function is selected to quantify the discrepancy between predicted outputs and true labels;
- (vii) Backpropagation and gradient descent are performed to update weights and minimize the loss function;
- (viii) Training iterations involve repeatedly feeding data through the network, calculating gradients, and updating weights;
- (ix) Hyperparameters are adjusted to optimize the model's performance;
- (x) The trained model is assessed on a separate test dataset employing evaluation metrics like accuracy and precision;
- (xi) Once satisfactory performance is achieved, the trained CNN can be deployed for diabetes diagnosis in a production environment, ensuring consistent pre-processing of input data.

## 11.2.1.1 Application of CNNs for Various Aspects of Diabetes Management

Until now, CNNs have been applied to multiple aspects of diabetes research and management. Here are some specific areas where CNNs have shown promise:

- **Diabetic retinopathy detection**: CNNs analyze retinal images to detect and classify diabetic retinopathy stages, enabling early intervention [9,10].
- **Glucose monitoring**: CNNs analyze glucose measurements and time-series data to predict blood glucose levels, facilitating personalized monitoring and insulin dosing [11–13].
- **Risk prediction and management**: CNNs predict the risk of developing diabetes like T2DM or complications using various data sources, aiding in personalized risk assessments and early interventions [14].
- **Diabetic foot ulcer detection**: CNNs detect and classify diabetic foot ulcers from images, enabling early detection and monitoring to mitigate complications [15].

## 11.2.2 Recurrent Neural Networks

RNNs are a kind of deep learning architecture suitable for handling sequential data, including diabetes time-series data. RNNs can capture temporal dependencies and learn from previous inputs to predict or generate sequences. The steps involved in the architecture and training of RNNs for diabetes detection are as follows [7,16,17]:

- (i) **Inputs**: RNNs take sequential data like glucose measurements or insulin doses. The data is preprocessed and represented as input sequences;
- (ii) **Sequence padding**: Varying length sequences are padded to ensure equal size, enabling batch processing;
- (iii) **Hidden state**: The hidden state captures the network’s memory and previous sequence information, modeling sequential dependencies;
- (iv) **Recurrence**: At each time step, RNNs update the hidden state by incorporating the input data and the previous hidden state;
- (v) **Training**: RNNs are trained using a suitable loss function, comparing predicted output with ground truth labels. Weights and biases are adjusted through backpropagation and gradient descent;
- (vi) **Backpropagation through time (BPTT)**: BPTT extends backpropagation to RNNs, propagating errors through all time steps. The remaining steps in the training process are similar to CNNs.

### 11.2.2.1 Application of RNNs for Various Aspects of Diabetes Management

The performance of RNNs in diabetes-related tasks is influenced by various factors such as the quality and quantity of data, model architecture, feature engineering, and optimization techniques. However, RNNs have demonstrated their potential in improving diabetes management and aiding decision-making processes. Here is how RNNs work for diabetes-related tasks:

- **Glucose level prediction**: RNNs use past glucose readings to predict future levels, capturing patterns and dynamics [18,19].
- **Anomaly detection**: RNNs detect abnormal glucose patterns by learning standard behavior, aiding in identifying episodes or unusual patterns [20,21].
- **Diabetes risk assessment**: RNNs analyze longitudinal data to predict diabetes risk and complications by identifying patterns and risk factors [22].
- **Disease progression modeling:** RNNs analyze longitudinal data to model disease progression, considering demographic information, clinical measurements, and treatment history [23].

## 11.2.3 Deep Belief Networks

DBNs are valuable algorithms for diabetes management, integrating diverse data modalities like clinical, genetic, and lifestyle factors. By employing unsupervised learning, DBNs capture the relationships and structure within the data, facilitating risk assessment and disease prediction.

The key steps involved in DBNs are as follows [24,25]:

- (i) **Inputs**: Numerical features related to individuals, including age, gender, BMI, blood pressure, glucose level, etc., are selected and preprocessed;
- (ii) **Visible layers**: Restricted Boltzmann machines (RBMs) with binary units represent observed variables and connect to the input data;
- (iii) **Hidden layers**: RBMs, except the last one, have hidden layers that capture latent representations;
- (iv) **RBM architecture**: Weighted connections exist between visible and hidden layers, with activation functions determining hidden unit activations;
- (v) **Training**: DBNs undergo unsupervised training, initially employing layer-wise pretraining, followed by fine-tuning using supervised learning algorithms to adjust the biases and weights of the network;
- (vi) **Inference**: Trained DBNs are used for diabetes detection. Input data passes through visible and hidden layers, producing output used for classification or prediction tasks.

### 11.2.3.1 Application of DBNs for Various Aspects of Diabetes Management

DBNs have been explored in multiple aspects of diabetes detection, including risk prediction, early detection, classification, and feature selection. Here are some key areas where DBNs have been applied:

- **Early detection:** DBNs analyze longitudinal health records and biomarker changes to detect early stages of diabetes by capturing subtle patterns and trends [26,27].
- **Diabetes management:** DBNs identify critical indicators for diabetes diagnosis, such as glucose concentration, BMI, and age. They provide recommendations for prevention education, personalized measures, and community-wide strategies to improve management [28].
- **Diabetes prediction**: DBN-based models predict the risk of developing diabetes using clinical features like age, BMI, blood pressure, and glucose levels [29].

## 11.2.4 Transfer Learning

Transfer learning is a valuable technique that leverages pre-trained deep learning models to carry out diagnosis and risk assessment tasks in diabetes. It boosts the performance of models that have limited data by utilizing the knowledge gained from pre-trained models. The architecture of this method in diabetes can be summarized as follows [30,31]:

- (i) **Source task**: A labeled dataset (S) for the source task, containing input features (x) and target labels (y) indicating diabetes presence or absence;
- (ii) **Pre-trained model**: A pre-trained model (M) trained on the source task, represented by a function ($f_M$) with parameters ($\theta_M$);
- (iii) **Target task**: A labeled dataset (T) for the target task, with input features (x) and target labels (y);
- (iv) **Fine-tuning**: The pre-trained model (M) is fine-tuned on the target task (T) by updating its parameters ($\theta_M$) to adapt to the new task. The fine-tuned model is denoted as ($f_t$) with updated parameters ($\theta_T$);
- (v) **Feature extraction**: Input features (x) from the source task dataset (S) are passed through the pre-trained model (M) to extract high-level features (h);
- (vi) **Additional layers**: Extra layers are added to process the extracted features (h) and learn task-specific representations. The output is denoted as ($h'$) with parameters ($\theta'$);
- (vii) **Classification layer**: A final layer predicts the target label (y) for the target task, mapping the output of the additional layers (h') to the target label ($y'$) with parameters ($\theta''$);
- (viii) **Fine-tuning process**: Parameters ($\theta_M$, $\theta'$, $\theta''$) are updated based on the labeled dataset of the target task (T) using optimization algorithms like stochastic gradient descent (SGD);
- (ix) **Evaluation and testing**: The fine-tuned model is evaluated on a validation set, and hyperparameters are adjusted as needed. Finally, the model is tested on an independent dataset to assess its performance on unseen data from the target task.

### 11.2.4.1 Application of Transfer Learning for Various Aspects of Diabetes Management

- **Blood glucose prediction**: It predicts patient-specific blood glucose levels using continuous glucose monitoring data, enabling personalized glucose management and control [32].
