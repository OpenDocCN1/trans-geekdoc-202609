
# 目录

150. [144](#bodymatter-007.xhtml#page-144)

151. [145](#bodymatter-007.xhtml#page-145)

152. [146](#bodymatter-007.xhtml#page-146)

153. [147](#bodymatter-007.xhtml#page-147)

154. [148](#bodymatter-007.xhtml#page-148)

155. [149](#bodymatter-007.xhtml#page-149)

156. [150](#bodymatter-007.xhtml#page-150)

157. [151](#bodymatter-007.xhtml#page-151)

158. [152](#bodymatter-007.xhtml#page-152)

159. [153](#index.xhtml#page-153)

# Dedication

Siddhartha Bhattacharyya would like to dedicate this book to his late father Ajit Kumar Bhattacharyya, his late mother Hashi Bhattacharyya, his beloved wife Rashni, his colleagues Abhishek, Arpan, Pampa, Soham, and Srijibendu.

Vaclav Snasel would like to dedicate this book to his wife Božena Snášelová.

Aboul Ella Hassanien would like to dedicate this book to his wife Nazaha Hassan Elsaman.

Balakrushna Tripathy would like to dedicate this book to his beloved son Anurag.

Satadal Saha would like to dedicate this book to his little daughter Koushiki.

# Preface

Deep learning (DL) is a new area of machine learning (ML) research, which has been introduced with the objective of moving ML closer to one of its original goals, that is, artificial intelligence (AI). DL was developed as an ML approach to deal with complex input–output mappings. While traditional ML methods successfully solve problems where final value is a simple function of input data, DL techniques are able to capture composite relations between air pressure recordings and English words, millions of pixels and textual description, brand-related news and future stock prices, and almost all real-world problems. DL framework uses a cascade of multiple layers of nonlinear processing units for feature extraction and transformation. Each successive layer uses the output from the previous layer as input. The learning may be supervised (e.g., classification) and/or unsupervised (e.g., pattern analysis). These algorithms learn multiple levels of representations that correspond to different levels of abstraction by using some form of gradient descent for training via backpropagation. The main components include multiple hidden layers of an artificial neural network and sets of propositional formulas. Other variations are also in vogue where latent variables are organized layerwise in deep generative models. Representative examples include deep belief networks and deep Boltzmann machines. DL is a state-of-the-art system in various disciplines, particularly computer vision, automatic speech recognition, and human action recognition.

This volume comprises seven well-versed chapters reporting latest trends in DL research and applications.

Chapter 1 presents the various cloud platforms available in market offerings from different vendors. IBM provided ML platform – Data Science Experience is considered here for the field of study. Prior to this section, an overview of AI, ML, and DL with their relationship is deliberated. Discussion on popular DL architectures with elementary comparison is also considered in this chapter.

Unlike conventional ML algorithms, where humans learn more of feature extraction than machines, which just crunches numbers, DL algorithms are quite promising as they have revolutionized the way data is dealt with. Based on the powerful notion of artificial neural networks, these learning algorithms learn to represent data or, if we rephrase, can extract features from raw data. DL has paved a way for end-to-end systems, where one learning algorithm does all the tasks. Convolutional neural networks (CNNs) have earned a lot of fame lately, especially in the domain of computer vision where in some cases its performance has beaten that of humans. In Chapter 2, the authors try to demystify how CNNs work and illustrate using one novel application in the field of astronomy. In addition, the chapter investigates what features the network is learning.

Optical character recognition systems have been used for extraction of text contained in scanned documents or images. This system consists of two steps: character detection and recognition. One classification algorithm is required for character recognition by their features. Character can be recognized using neural networks. The multilayer perceptron (MLP) provides acceptable recognition accuracy for character classification. Moreover, the CNN and the recurrent neural network (RNN) are providing character recognition with high accuracy. MLP, RNN, and CNN may suffer from the large amount of computation in the training phase. In Chapter 3, a CNN is implemented for recognition of digits from MNIST database, and a comparative study is established between MLP, RNN, and CNN.

DL techniques have had a huge impact on AI research. They have improved on the traditional ML techniques where human expertise was required for feature engineering. By removing one human factor, they have moved us one step forward in the field of AI. They have not entirely removed humans though they are required for designing the architectures and cleaning the data. DL techniques have managed to achieve breakthrough results in domains such as speech recognition, machine translation, image recognition, and object detection. Chapter 4 gives a brief overview of various DL techniques being used today. Techniques that make DL more effective have been described. Some interesting applications have also been covered.

Handwritten document analysis using intelligent computing technology is a demanding research area nowadays considering its usefulness in identifying a person and human characteristics, particularly that of persons having typical disabilities such as dyslexia, dysgraphia, and Parkinson’s disease. Analysis of handwriting, falling under the broad purview of graphology, helps us understand the writer’s psychology, emotional outlays, and noticeable disorders as well. Since there prevails a broad spectrum of cursive nature and high inconsistency of handwriting styles, the techniques for modern handwriting analysis need to be more robust and sensitive to different patterns compared to the traditional graphological techniques. Herein lies the necessity of computing technology which intelligently analyzes handwritten texts to find out the similarity of finer aspects of handwritings of children or adult with some kind of learning/writing disability. DL technology is chosen as the technical tool to identify and classify common features of handwriting of children with developmental dysgraphia. Variational autoencoder, a deep unsupervised learning technique, is purported to be used here. Chapter 5 reports successful extraction of significant number of distinguishable handwriting characteristics that are clinically proved to be symptoms of dysgraphia. Audio signal processing and its classification dates back to the past century. From speech recognition to speaker recognition and from speech to text conversion to music generation, a lot of advances have been made in this field using algorithms such as hidden Markov models, RNNs with long–short-term memory layers, deep convolutional neural networks, and the recent state-of-the-art model for music and speech generation using WaveNets. These algorithms are applied after the audio signals are processed and effective feature extraction techniques are applied on them. Chapter 6 gives a detailed explanation about what an audio signal is and how it is processed. It also covers the various feature extraction techniques and the classification algorithms. Finally, the present-day applications and the potentials of DL in this field are explored.
