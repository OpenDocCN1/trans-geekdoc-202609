of a sentence (positive, negative, or neutral). Given a sequence of words \(x_1, x_2, \dots, x_T\), the RNN processes each word sequentially, updating its hidden state:

\[ h_t = \sigma(W_h h_{t-1} + W_x x_t + b) \]

After processing the entire sentence, the final hidden state \(h_T\) is used to classify the sentiment. The output is obtained by applying a softmax function to the final hidden state:

\[ y = \text{softmax}(W_y h_T + c) \]

where \(W_y\) is the weight matrix associated with the output layer. The network is trained to minimize the cross-entropy loss:

\[ \mathcal{L} = -\sum_{t=1}^T \log P(y|h_T) \]

This allows the RNN to classify the overall sentiment of the sentence by learning the relationships between words and sentiment labels. Sentiment analysis is useful for applications such as customer feedback analysis, social media monitoring, and opinion mining. In Named Entity Recognition (NER), RNNs are used to identify and classify named entities, such as people, locations, and organizations, in a text. The RNN processes each word \(x_t\) in the sequence, updating its hidden state at each time step:

\[ h_t = \sigma(W_h h_{t-1} + W_x x_t + b) \]

The output at each time step is a probability distribution over possible entity labels:

\[ P(y_t|h_t) = \text{softmax}(W_y h_t + c) \]

The network is trained to minimize the cross-entropy loss:

\[ \mathcal{L} = -\sum_{t=1}^T \log P(y_t|h_t) \]

By learning to classify each word with the appropriate entity label, the RNN can perform information extraction tasks, such as identifying people, organizations, and locations in text. This is crucial for applications such as document categorization, knowledge graph construction, and question answering. In speech recognition, RNNs are used to transcribe spoken language into text. The input to the RNN consists of a sequence of acoustic features, such as Mel-frequency cepstral coefficients (MFCCs), which are extracted from the audio signal. At each time step \(t\), the RNN updates its hidden state:

\[ h_t = \sigma(W_h h_{t-1} + W_x x_t + b) \]

The output at each time step is a probability distribution over phonemes or words:

\[ P(w_t|h_t) = \text{softmax}(W_y h_t + c) \]

The network is trained by minimizing the negative log-likelihood:

\[ \mathcal{L} = -\sum_{t=1}^T \log P(w_t|h_t) \]

By learning the mapping between acoustic features and corresponding words or phonemes, the RNN can transcribe speech into text, which is fundamental for applications such as voice assistants, transcription services, and speech-to-text systems.

In summary, RNNs are powerful tools for processing sequential data in NLP tasks such as machine translation, sentiment analysis, named entity recognition, and speech recognition. Their ability to process input sequences in a time-dependent manner allows them to capture long-range dependencies, making them well-suited for complex tasks in NLP and beyond. However, challenges such as the vanishing and exploding gradient problems necessitate the use of more advanced architectures, like LSTMs and GRUs, to enhance their performance in real-world applications.