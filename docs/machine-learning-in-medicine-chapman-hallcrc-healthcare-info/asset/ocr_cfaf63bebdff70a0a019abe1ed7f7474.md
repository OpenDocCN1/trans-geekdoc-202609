**2D Convolution:** Convolution is applied on both dimensions as seen in Figure 10.2b, where 100 filters (size of $10 \times 34$) are followed by a max- pooling ($2 \times 2$) layer. The second convolution layer is added (with 20 filters of the size of $5 \times 34$) and followed by a flattened layer and a soft-max.

**CNN and LSTM (2D CNN + LSTM):** Because CNNs don't have the ability to encode temporal history, they are combined with LSTM, where the two-layer 2D-CNN mentioned above is merged with two LSTM layers (hidden layers of size $30 \times 50$). This is followed by two dense layers (128 and 50 hidden units) and a soft-max layer for classification.

Following Ref. [24], the Aruba dataset is divided into train and test sets based on a day in order not to lose the temporal information. For training, 150 days of the Aruba dataset are used, while 15 days are used for validation and the other days are used for testing. The adlnormal set of WSU is used for training while the adleror version is used for testing.

The first experiment was performed on Aruba to choose the best input representation that gives the highest recognition results. This experiment is performed with the LSTM classifier on 1-minute time slices of sensor readings. Extracted slices are mapped into binary, change-point and last- fired representations. As seen in Table 10.6, last-fired representation gives the highest precision and recall rates as well as a good accuracy rate (accura- cy rates of 87.72%, 49.69% and 48.79% for last-fired, binary and change- point respectively). A combination of the best two features: change-point and last-fired, gives a slightly better accuracy rate (87.78%) than last-fired alone but results in lower precision and recall values. Thus, we continue our following experiments with a last-fired feature.

In Table 10.7, we provide an analysis of the second experiment which is activity recognition. The success rates by both generative and discrimi- native methods on the Aruba set are depicted in Table 10.7. The results indicate that CNNs with 2D convolution (accuracy of 89.67%) and also CNN-2D followed by an LSTM classifier outperform CRF (accuracy of 89.72%). The reason is CNNs extract their own pruitful features while CRF only relies on the given input. HMM and HSMM give the worst accuracy

TABLE 10.6 Activity Recognition Results for Aruba with LSTM
| Feature | Precision (%) | Recall (%) | F-Measure(%) | Accuracy(%) |
| :--- | :---: | :---: | :---: | :---: |
| Binary | 34.21 | 28.26 | 30.95 | 49.69 |
| Change-point | 29.28 | 26.41 | 27.77 | 48.79 |
| Last-fired | 43.18 | 43.37 | 43.27 | 87.72 |
| Change-point + Last-fired | 37.33 | 42.42 | 39.71 | 87.78 |