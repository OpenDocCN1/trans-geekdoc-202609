
![](img/66ecdb8eb8654ae1c99705e55a45a836_133_0.png)

## FIGURE 6.8 Multilayer Perceptron.

Source: Khang (2021)

In simple words, convolution is a sliding window function applied to a matrix, where every element of this matrix precisely represents a pixel of an image, and the sliding window is called a filter, feature detector or kernel (Anuj Kumar & Khang, 2023).

Recently, CNNs have been applied to the ambiguous NLP domain (Liao & Zhou, 2021; Peng & Han, 2021). In the case of image processing, this input matrix can conveniently be replaced by a matrix representing sentences or documents; each row corresponds to a token.

In contrast to image processing, where the kernel strides over the local patches of an image, in the case of NLP, the kernel strides over the complete row of the matrix, thus fixing the filter width to the width of the matrix in the case of NLP applications.

Figure 6.9 gives an elaborate visualization of the CNN architecture for text classification. Two filters were identified with three region sizes: 2, 3 and 4.

Feature maps were generated as a result of the convolution. These feature maps undergo pooling, which is a dimensionality reduction step, and generates six univariate feature vectors. These are further concatenated into one feature vector, which is fed as input to the final Softmax layer to classify the text, as shown in Figure 6.9.

Assuming binary classification, two possible output states or classes are obtained at the output layer.

Owing to the high computational requirements of neural networks, a novel concept of neural architecture search benchmarks with pre-computed neural architecture has also evolved for both computer vision and NLP domains (Klyuchnikov et al., 2022).

![](img/66ecdb8eb8654ae1c99705e55a45a836_134_0.png)

## FIGURE 6.9 Convolutional Neural Network.

### 6.8.3 Recurrent Neural Network

Recurrent neural networks (RNNs) are a class of ANN that are extensively exploited in the fields of NLP, speech recognition, language translation and many more.

With sequential and time series data as the foundation, RNN is the appropriate choice for temporal and ordinal applications, such as NLP.

In contrast to CNN, where the information flow is unidirectional, RNN incorporates feedback loops, such as backpropagation through time (BPTT) to ensure a constant supply of information. These bidirectional recurrent neural networks (BRNNs) predict the future based on forward projections and evaluate the past based on backward projections (Rana et al., 2021).

To facilitate reinforcement learning in an RNN, the weights that are fixed for a specific layer are continuously adjusted during the process of backpropagation and gradient descent; the gradient is the slope of the loss function.

Owing to the functioning of the RNN, where the parameters are shared across the layers, the BPTT sums up the errors at each time step. The current trend in geotagging on social media platforms has led to location-specific sentiment analysis using RNN (Qi et al., 2019).

A vivid variety of applications, such as machine translation, medical text interpretation (Mugisha & Paik, 2021), music generation and sentiment classification, can be addressed with different types of RNNs. In addition to BRNN, another popular RNN architecture is long short-term memory (LSTM).

This RNN architecture is a rescue to the vanishing gradient problem commonly observed in deeply layered networks for complex datasets. The LSTM network addresses the issue encountered when RNNs grow bigger and more complex, especially those based on gradient-based learning methods (Khang et al., 2023a).

Long short-term memories have played a pivotal role in critical NLP concerns, such as privacy and security issues related to language-based applications (Feng et al., 2020). These are well integrated with Internet of Things platforms to address security and privacy violations (Breve et al., 2022).

Long short-term memory-based RNNs essentially segregate the data based on short-term and long-term memory, which means that LSTM has cells in the hidden layers with three gates vis-à-vis the input gate, output gate and forget gate, controlling the required information flow to make predictions (Liang & Zhang, 2021).

A precision as high as 0.94 is achieved by LSTM for fake news detection by employing RNNs. In addition, sentiment analysis of customer reviews is another popular application for business decision-making (Houssein et al., 2021; Jain et al., 2022).

## 6.9 CONCLUSION

The blockchain integration of NLP is an emerging trend that is gaining interest in the NLP community (Shahbazi & Byun, 2021). The integration of blockchain technology and NLP can lead to new opportunities for secure and transparent data sharing, decentralized applications and new business models (Khang & Khang, 2021).

Here are some potential future trends in which blockchain integration can be beneficial for NLP:

- **Secure data sharing:** One of the main benefits of blockchain technology is its ability to securely store and share data. In the context of NLP, this can be used to securely store and share sensitive data, such as medical records or financial data (Khang et al., 2024).

- **Decentralized applications:** Blockchain technology can facilitate the development of decentralized NLP applications, which can be more resistant to censorship and provide a more transparent user experience.

- **Transparency in data usage:** With blockchain technology, data ownership and usage can become more transparent. This can be beneficial for users who want to know how their data are being used and can also help researchers access more data for their studies.

- **Smart contracts:** Smart contracts can be used to automate and enforce the terms of data sharing agreements in the context of NLP. This can ensure that the data are only used for agreed-upon purposes and can help prevent misuse.

- **Token-based incentivization:** Blockchain tokens can be used to incentivize data sharing and participation in NLP tasks. This can help create new business models and provide incentives for users to share their data.

- **Fraud detection:** Blockchain technology can be used to detect fraud in NLP tasks, such as sentiment analysis or fake news detection. By verifying the source and accuracy of the data, blockchain can help prevent malicious actors from manipulating the results of NLP tasks.

Overall, the integration of blockchain technology and NLP has the potential to create new opportunities for secure and transparent data sharing, decentralized applications and new business models. Although still in its early stages, the integration of blockchain and NLP is an exciting area of research that will likely lead to new innovations in the field.

# REFERENCES

Ahmed H. A., Bawany N. Z., Shamsi J. A., (2021). “CaPBug—a framework for automatic bug categorization and prioritization using NLP and machine learning algorithms,” IEEE Access, 9, 50496–50512. https://doi.org/10.1109/ACCESS.2021.3069248

Alawad M., et al., (2021). “Privacy-preserving deep learning NLP models for cancer registries,” IEEE Transactions on Emerging Topics in Computing, 9(3), 1219–1230, 2021. https://doi.org/10.1109/TETC.2020.2983404

Anuj Kumar G., Khang A., (2023). AI-Aided IoT Technologies and Applications in the Smart Business and Production, Implementation of Smart Vehicle Parking System Using Internet of Things (IoT), p. 8. CRC Press. https://doi.org/10.1201/9781003392224-8

Bose P., Roy S., Ghosh P., (2021). “A comparative NLP-based study on the current trends and future directions in COVID-19 research,” IEEE Access, 9, 78341–78355. https://doi.org/10.1109/ACCESS.2021.3082108

Breve B., Cimino G., Deufemia V., (2022). “Identifying security and privacy violation rules in trigger-action IoT platforms with NLP models,” IEEE Internet of Things Journal. https://doi.org/10.1109/JIOT.2022.3222615

Bunyamin M. A. F., Pudjiantoro T. H., Renaldi F., Hadiana A. I., (2022). “Analyzing sentiments on Indonesia’s new national palace using the combination of naive Bayes and sentiment scoring,” In 2022 International Conference on Science and Technology, ICOSTECH 2022. Institute of Electrical and Electronics Engineers Inc. https://doi.org/10.1109/ICOSTECH54296.2022.9829075

Chitty-Venkata K. T., Emani M., Vishwanath V., Somani A. K., (2022). “Neural architecture search for transformers: A survey,” IEEE Access, 10, 108374–108412. https://doi.org/10.1109/ACCESS.2022.3212767

Dalian, Institute of Electrical and Electronics Engineers, IPEC 2020: proceedings of 2020 Asia-Pacific Conference on Image Processing, Electronics and Computers: China, April 14–16, 2020. https://doi.org/10.1201/9781003145011

Elnagar A., Yagi S. M., Nassif A. B., Shahin I., Salloun S. A., (2021). “Systematic literature review of dialectal Arabic: Identification and detection,” IEEE Access, 9, 31010–31042 (Institute of Electrical and Electronics Engineers Inc.). https://doi.org/10.1109/ACCESS.2021.3059504

Feng Q., He D., Liu Z., Wang H., Choo K. K. R., (2020). “SecureNLP: A system for multi-party privacy-preserving natural language processing,” IEEE Transactions on Information Forensics and Security, 15, 3709–3721. https://doi.org/10.1109/TIFS.2020.2997134
