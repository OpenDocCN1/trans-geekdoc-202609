# # 4 Experimentation Results

Simulations were conducted on a workstation with an Intel Core i9 processor, 64 GB RAM, and an NVIDIA RTX 3,090 GPU, run in Python with TensorFlow and Scikit-learn to benchmark the performance of the proposed DigiCare framework. Synthetic time-series sensor data was produced in order to simulate IoMT streaming conditions, and sampled structured clinical data was drawn from the MIMIC-III dataset. The Scikit-learn optimized ensemble library was employed for random forest execution, while Keras with GPU backend was employed to execute the Bi-LSTM component.

Three models that are most commonly used were chosen for comparison: CNN-LSTM, SVM, and logistic regression (LR). CNN-LSTM was chosen since it is better than the other two models in spatiotemporal modeling of healthcare data, while LR and SVM were chosen since they are most frequently used in baseline classification issues. For verifying the improved ability of the proposed hybrid model, these models were compared to it (random forest + Bi-LSTM). Evaluation was done using accuracy, precision, recall, F1-score, and area under the receiver operating characteristic curve (AUC-ROC). To further quantify the ability of the model to distinguish between high-risk and low-risk patients at different threshold settings, AUC-ROC was added.

![](bbox=[0.17, 0.45, 0.83, 0.75])

**Figure 2:** Accuracy analysis.

Figure 2 shows that the proposed model performs better than all the traditional models with the highest accuracy of 92.5%. CNN-LSTM is the second best with a performance of 90.3%, which proves that it is also equally effective for classification tasks involving space and time information. SVM performs relatively well with an accuracy