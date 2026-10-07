
707-829-0515 (international or local)
707-829-0104 (fax)

We have a web page for this book, where we list errata, examples, and any additional information. You can access this page at http://bit.ly/hands-on-machine-learning-with-sikit-learn-and-tensorflow or https://homl.info/oreily.

To comment or ask technical questions about this book, send email to bookquestions@oreily.com.

For more information about our books, courses, conferences, and news, see our website at http://www.oreily.com.

Find us on Facebook: http://facebook.com/oreily

Follow us on Twitter: http://twitter.com/oreillymedia

Watch us on YouTube: http://www.youtube.com/oreillymedia

# Changes in the Second Edition

This second edition has five main objectives:

- 1. Cover additional topics: unsupervised learning techniques (including clustering, anomaly detection, density estimation and mixture models), additional techniques for training deep nets (including self-normalized networks), additional computer vision techniques (including the Xception, SENet, object detection with YOLO, and semantic segmentation using R-CNN), handling sequences using CNNs (including WaveNet), natural language processing using RNNs, CNNs and Transformers, generative adversarial networks, deploying TensorFlow models, and more.
- 2. Update the book to mention some of the latest results from Deep Learning research.
- 3. Migrate all TensorFlow chapters to TensorFlow 2, and use TensorFlow implementation of the Keras API (called tf.keras) whenever possible, to simplify the examples.
- 4. Update the code examples to use the latest version of Scikit-Learn, NumPy, Pandas, Matplotlib and other libraries.
- 5. Clarify some sections and fix some errors, that are plenty of great feedback from readers.

Some chapters were added, with some errors, and a few were reordered. Table P-1 shows the mapping between the 1st edition chapters and the 2nd edition chapters:

# Table P-1. Chapter mapping between 1st and 2nd edition

| 1st Ed. chapter | 2nd Ed. Chapter | % Changes | 2nd Ed. Title |
|---|---|---|---|
| 1 | 1 | <10% | The Machine Learning Landscape |
| 2 | 2 | <10% | End-to-End Machine Learning Project |
| 3 | 3 | <10% | Classification |
| 4 | 4 | <10% | Training Models |
| 5 | 5 | <10% | Support Vector Machines |
| 6 | 6 | <10% | Decision Trees |
| 7 | 7 | <10% | Ensemble Learning and Random Forests |
| 8 | 8 | <10% | Dimensionality Reduction |
| N/A | 9 | 100% new | Unsupervised Learning Techniques |
| 10 | 10 | ~75% | Introduction to Artificial Neural Networks with Keras |
| 11 | 11 | ~50% | Training Deep Neural Networks |
| 12 | 12 | 100% rewritten | Custom Models and Training with TensorFlow |
| Part of 12 | 13 | | Loading and Preprocessing with TensorFlow |
| 13 | 14 | ~50% | Computer Vision Using Convolutional Networks |
| Part of 14 | 15 | ~75% | Processing Sequences using RNNs and CNNs |
| Part of 14 | 16 | ~90% | Natural Language Processing with RNNs and Attention |
| 15 | 17 | ~75% | Autoencoders and GANs |
| 16 | 18 | | Reinforcement Learning |
| Part of 12 | 19 | 100% rewritten | Deploying your Models |

More specifically, here are the main changes for each 2nd edition (other than clarifications, corrections, and code updates):

- Chapter 1: Added a section on handling mismatch between the training set and validation and test sets.
- Chapter 2: Added how to compute a confidence interval. Improved the installation instructions (e.g., for Windows). HotEncoder and ColumnTransformer.
- Chapter 4: Explained the need for training instances to be Independent and Identically Distributed (IID).
- Chapter 7: Added a short section about XGBoost.
- Chapter 9 – new chapter including: Clustering with K-Means, how to choose the number of clusters, how to use it for dimensionality reduction, semi-supervised learning, image segmentation, and more. DBSCAN algorithm and an overview of other algorithms in Scikit-Learn. Gaussian mixture models, the Expectation-Maximization (EM) algorithm, Bayesian inference, and how mixture models can be used for clustering, density estimation, anomaly detection and novelty detection.
- Chapter 10 (mostly new): Added an introduction to the Keras API, including all APIs (Sequential, Functional and Subclassing), persistence and callbacks (including Tensor Board).
- Chapter 11 (many changes): Introduced self-normalizing nets, the SELU activation function and Alpha Dropout. Introduced self-supervised learning. Added Nadam optimization. Monte Carlo Dropout. Updated the practical guidelines.
- Chapter 12 – completely rewritten, including: A tour of TensorFlow 2, TensorFlow's lower-level API, Writing custom loss functions, metrics, layers, Using auto-differentiation and creating custom training Functions and graphs (including tracing and autograph).
- Chapter 13 – new chapter, including: The Data API, Loading/Storing data efficiently using TFRecords, The Features API (including an introduction to embeddings), An overview of TF Transform and TF Datasets. Moved the low-level implementation of the neural network to the exercises.
- Removed details about queues and readers that are now superseded by the Data API.
- Chapter 14: Added Xception and SENet architectures. Added a Keras implementation of ResNet-34. Showed how to use pretrained models using Keras. Added an end-to-end transfer learning example. Added classification and localization. Introduced Fully Convolutional Networks (FCNs). Introduced object detection using the YOLO architecture. Introduced semantic segmentation using R-CNN.
- Chapter 15: Added an introduction to WaveNet. Moved the Encoder-Decoder architecture and Bidirectional RNNs to Chapter 16.
- Chapter 16: Explained how to use the Data API to handle sequential data. Showed an end-to-end example of text generation using a Character RNN, using both a stateless and a stateful RNN. Showed an end-to-end example of sentiment analysis using an LSTM. Explained masking in Keras. Showed how to reuse pretrained embeddings using TF Hub. Showed how to build an Encoder-Decoder for Neural Machine Translation using TensorFlow Addons/seq2seq. Introduced beam search. Explained attention mechanisms. Added a short overview of visual attention and a note on explainability. Introduced the fully attention-based Transformer architecture, including positional embeddings and multi-head attention. Added an overview of recent language models (2018).
- Chapters 17, 18 and 19: coming soon.

# Acknowledgments

Never in my wildest dreams did I imagine the first edition of this book would get such a large audience. I received so many messages from readers, many asking questions, some kindly pointing out errata, and most sending me encouraging words. I cannot express how grateful I am to all these readers for their tremendous support. Thank you all so much! Please do not hesitate to file issues on github if you find errors in the code (or just to ask questions), to submit errata if you find errors in the text. Some readers also shared how this book helped them solve a concrete problem they were working on: If you find such feedback motivating I would love it if you could share your story with me, either privately (e.g., via LinkedIn) or publicly (e.g., in an Amazon review).

I am also incredibly thankful to all the amazing people who took time out of their lives to review my book with such care. In particular, I would like to thank François Chollet for the review of the chapters based on Keras and TensorFlow, and giving me some great, in-depth feedback. Since Keras is one of the main additions to my 2nd edition, having his author review was invaluable. I highly recommend François's excellent book Deep Learning with Python': it has the conciseness, clarity and depth of the Keras library itself. Big thanks as well as to Anwar Patel, who reviewed every chapter of 2nd edition and gave me excellent feedback.
