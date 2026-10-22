Using deceptive data to trick a neural network into making wrong predictions is called adversarial attacks. Adding noise to samples is a common technique to create adversarial samples. The success of adversarial attacks is especially exaggerated as the resolution of images increases.

Adding noisy samples to training data can help models recognize the weak spots in their learned decision boundary and improve their performance.51 Noisy samples can be created by either adding random noise or by a search strategy. Moosavi-Dezfooli et al. proposed an algorithm, called DeepFool, that finds the minimum possible noise injection needed to cause a misclassification with high confidence.52 This type of augmentation is called adversarial augmentation.53

Adversarial augmentation is less common in NLP (an image of a bear with randomly added pixels still looks like a bear, but adding random characters to a random sentence will likely render it gibberish), but perturbation has been used to make models more robust. One of the most notable examples is BERT, where the model chooses 15% of all tokens in each sequence at random and chooses to replace 10% of the chosen tokens with random words. For example, given the sentence “My dog is hairy,” and the model randomly replacing “hairy” with “apple,” the sentence becomes “My dog is apple.” So 1.5% of all tokens might result in nonsensical meaning. Their ablation studies show that a small fraction of random replacement gives their model a small performance boost.54

In Chapter 6, we’ll go over how to use perturbation not just as a way to improve your model’s performance, but also as a way to evaluate its performance.

# Data Synthesis

Since collecting data is expensive and slow, with many potential privacy concerns, it’d be a dream if we could sidestep it altogether and train our models with synthesized data. Even though we’re still far from being able to synthesize all training data, it’s possible to synthesize some training data to boost a model’s performance.

51 Ian J. Goodfellow, Jonathon Shlens, and Christian Szegedy, “Explaining and Harnessing Adversarial Examples,” arXiv, March 20, 2015, https://oreil.ly/9v2No; Ian J. Goodfellow, David Warde-Farley, Mehdi Mirza, Aaron Courville, and Yoshua Bengio, “Maxout Networks, arXiv, February 18, 2013, https://oreil.ly/L8mch.

52 Seyed-Mohsen Moosavi-Dezfooli, Alhussein Fawzi, and Pascal Frossard, “DeepFool: A Simple and Accurate Method to Fool Deep Neural Networks,” in Proceedings of IEEE Conference on Computer Vision and Pattern Recognition (CVPR), 2016, https://oreil.ly/dYVL8.

53 Takeru Miyato, Shin-ichi Maeda, Masanori Koyama, and Shin Ishii, “Virtual Adversarial Training: A Regularization Method for Supervised and Semi-Supervised Learning,” IEEE Transactions on Pattern Analysis and Machine Intelligence, 2017, https://oreil.ly/MBQeu.

54 Devlin et al., “BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding.”