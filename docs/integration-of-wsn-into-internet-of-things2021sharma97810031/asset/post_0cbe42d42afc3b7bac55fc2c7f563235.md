
ciphertext. Here the index_bit (which may take values 0 and 1) represents the bit value that is fixed in the secret key (by this reference, keys are split into two groups). The referent_bit (values can range from 0 to N, where the maximum of N is the length of the secret key) shows the index position of the fixed bit. Finally, there is a ciphertext file that contains the value of the encrypted message.

To avoid wrong data processing, which influences the correctness of the results, additional checks are developed during the data pipeline. Throughout the data generation process, every cipher message is additionally decoded and compared to the original plaintext message. If for some reason the decoded message and original message do not match, the data pipeline is stopped for further examination. At the end of the pipeline, the output is a cypher dataset of the desired size that is ready to be used for training the AI algorithm.

### 4.4.2 NEURAL NETWORK MODEL

The initial AI algorithm selected is a fully connected neural network. The reason is they are great for solving unstructured problems with a large number of dimensions. As is known, ciphertexts represent one of the most unstructured types of datasets. As mentioned earlier, some of the encryption algorithms are used as random number generators (which represent data without any relevant structure).

Besides this fact, an additional challenge is the large number of dimensions that exist in the cypher messages. For example, in a single essay that consists of about 400 words, about 300,000 dimensions could exist. So, it is really difficult to find any mutual information between the 300,000 cypher dimensions and a secret key. That is why neural networks are chosen as relevant algorithms because they represent one of the strongest algorithms involving unstructured data. The architecture of the neural network in this chapter is not chosen by the deterministic approach, rather empirical. From a few tested architectures, the final network consists of the following architectures:

- input layer,
- the first hidden layer, containing 2,048 neurons,
- second hidden layer, containing 4,096 neurons,
- third hidden layer, containing 1,024 neurons and
- output layer, containing 1 neuron.

The number of neurons in the input depends on the length of cyphertext messages. During the initialization process, the size of the largest encrypted message is used to define the size of the input layer. Other ciphertexts are padded using the zero-padding technique to reach the size of the largest one. All hidden layers represent standard fully connected layers, which means that the output of one neuron is propagated to all other neurons in the next layer. Using the forward-propagation technique, the input could be successfully mapped to the desired output.

As regard the rest of the neural network components, the activation function is ReLU, cost/loss function is softmax cross-entropy with logits, optimization function for the gradient descent is Adam, and activation function of the last network layer is softmax. Results obtained with this architecture are provided in Section 4.5.

### 4.4.3 Cryptographic Algorithms Used in This Research

To test the cryptanalytic methodology, we have used DES, AES and custom-made simple crypt (SC), which is explained below. SC represents a simple encryption algorithm based on pure XOR operation. At first, the message is converted to a bit array:

"Crypt me for fun!" => 01000011 01110010...

Then, a secret key of arbitrary length is generated. The length of this key is not important, yet the reader should note that the longer the key is, the more secure the cipher will be. When a key is generated, it is processed to be of the same length as the message in the following way:

- 1. If the secret key is shorter than the message, bits of the secret key are repeated in cycles until the equal length is reached.
- 2. If the secret key is longer than the message, pieces of the key longer than the message are ignored.

This process is important because the final step is performing an XOR operation on the message and the processed key. As the outcome, a ciphertext is produced. The reader should note that this algorithm is created only to demonstrate the result of the weaker encryption algorithm.

## 4.5 Experimental Evaluation

Results are arranged into four categories determined by the dataset type (character, word, sentence, and essay), where the essay category has additional subcategories determined by the type of data augmentation (full cipher length, partial cipher length and random partial cipher length).

The four main categories represent the format of the dataset, where the name of each category describes what the cipher message content is. For example, a sentence category means that the plaintext message contains a single sentence in the message before it is encrypted. Further paragraphs contain an explanation about essay subcategories.

### 4.5.1 Visual Representation

In this subsection, results of training and testing AI models are visually presented. The most important visuals and results are given here, whereas the rest of the results are presented in the Conclusions section.

Training initiated on the full cipher length uses every bit of information from each encrypted message. The problem with this approach is that not every ciphertext is of equal length. The length of the ciphertext varies depending on the length of the message. To overcome this problem, the longest cipher is determined, and then the rest of the cyphers are supplied with an additional 0 bits of information at the end (Figure 4.1).

Training initiated on the partial cypher length uses a certain bit length from each encrypted message that is defined before the start of the training (Figure 4.2).

![](img/0b5412a09266b61a5c216084aa99aac2_91_0.png)

![](img/0b5412a09266b61a5c216084aa99aac2_91_1.png)

![](img/0b5412a09266b61a5c216084aa99aac2_91_2.png)

However, on having AES as a referent algorithm, the results are as expected (Figure 4.3).

This approach shows the possibility to gather pieces of information from cyphers using only a certain part of the whole cypher message. Training initiated on the random partial cypher length is the same as the partial cypher length technique. The difference is that bits from the cypher message are chosen randomly from the whole cypher. This technique is chosen because the encryption algorithms associated are often used as a random number generator (Figure 4.4).

On the other hand, while training the DES algorithm, our model manages to get interesting results (Figure 4.5).

By extracting random pieces of information from the cypher, there could be a chance to get more information than just using plain cypher messages. The most important experimental results are presented as graphic visualization. They will be used to display a complete conclusion based on the current results (Figures 4.6–4.8).

### 4.5.2 RESULTS PRESENTED IN TABLES

Results presented here contain results presented in Section 4.5.1 as well as the rest of the results obtained during experimentation. Here, obtained results are discussed in more detail.

According to the values in Table 4.1, it is clear that neither of the algorithms has succeeded in determining the correlation between the secret key and the encrypted message. The reason that even an SC has not got any results is that on a single-character level, cyphers represent a one-time pad with a single XOR operation, which

![](img/0b5412a09266b61a5c216084aa99aac2_93_0.png)

FIGURE 4.7 Experimental results on shorter messages encrypted with DES and AES – the first case.

![](img/0b5412a09266b61a5c216084aa99aac2_93_1.png)

FIGURE 4.8 Results on messages encrypted with DES and AES – the second case.

| Algorithm | SC (%) | AES (%) | DES (%) |
|---|---|---|---|
| Train | 51.5 | 68.2 | 63.9 |
| Test | 51.1 | 51.9 | 52.1 |

this methodology fails to solve. Results show that our model reaches up to 68% on AES during the training phase, but during the test, our model achieved an accuracy slightly over 50%. The reason is that in the training dataset, the same examples were repeated during the minibatch random shuffling.

According to the results presented in Table 4.2, our methodology shows a clear advantage over the SC algorithm with a 99.9% accuracy. This proves that our methodology is successful in some algorithms.

| Algorithm | SC (%) | AES (%) | DES (%) |
|---|---|---|---|
| Train | 99.9 | 49.6 | 70.1 |
| Test | 99.9 | 50.0 | 69.5 |
