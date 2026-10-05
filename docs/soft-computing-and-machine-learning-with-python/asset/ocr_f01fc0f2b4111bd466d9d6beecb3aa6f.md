# Bankruptcy Prediction Using Machine Learning 105

due to limited training data, overfitting will affect the ultimate accuracy. To prevent this, a technique called dropout—temporarily and randomly removes units (hidden and visible)—to the neural network [4].

Autoencoder, also known as Diabolo network, is an unsupervised learning algorithm that sets the target values to be equal to the inputs. By doing this, it suppresses the computation of representing a few functions, which improves accuracy. Also the amount of training data required to learn these functions is reduced [5].

This paper is structured as follows. Section 2 describes the motivation for this idea. Section 3 describes relevant previous work. Section 4 formally describes the three models. In Section 5 we present our experimental results where we do a parallel comparison within the three models we choose and a longitudinal comparison with the three older models. Section 6 is the conclusion. Section 7 is the reference.

# MOTIVATION

The three models we choose (SVM, neural network, autoencoder) are relatively newly-developed but have already been applied to many fields.

SVM has been used successfully in many real-world problems such as text categorization, object tracking, and bioinformatics (Protein classification, Cancer classification). Text categorization is especially helpful in daily life—web searching and email filtering provide huge convenience and work efficiency.

Neural networks learn by instead of algorithms, thus, they have been widely applied to problems where it is hard or impossible to apply algorithmic methods [6]. For instance, finger print recognition is an exciting application. People can now use their fingerprints as keys to unlock their phones and payment accounts, free from the troubling, long passwords.

Autoencoders are especially successful in solving difficult tasks like natural language processing (NLP). They have been used to solve the previous seemingly intractable problems in NLP, including word embeddings, machine translation, document clustering, sentiment analysis, and paraphrase detection.

However, the usage of the three models in economics or finance is comparatively hard to find. So, we aim to find out if they still work well in economical field by running them with real-life data in a predicting bankruptcy task.