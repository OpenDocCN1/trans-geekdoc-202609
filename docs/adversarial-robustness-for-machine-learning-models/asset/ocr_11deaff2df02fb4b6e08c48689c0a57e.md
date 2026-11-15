# CHAPTER 6

# Adversarial attacks beyond image classification

# 6.1 Data modality and task objectives

For classification tasks on data modalities that can be presented in real-valued continuous vectors, such as images (pixel values), text embeddings, audio signals, time series, and real-valued tabular data, the methodology of the aforementioned adversarial attacks can be adopted in a principled manner by specifying the corresponding attack loss function and threat model, and then solving the formulated objective using continuous optimization tools such as gradient-based methods.

For classification tasks on noncontinuous data modalities, such as text tokens (e.g., words and characters), graphs, and malwares, the attack objective is similar, but the solver needs to use discrete optimization tools such as genetic algorithms, evolutionary algorithms, relaxation to continuous optimization methods due to the fact that the feasible action space of an attacker will be discrete in nature, such as adding, removing, or editing certain words in a sentence to change the sentiment.

For tasks beyond classification, such as regression, reconstruction, text summarization, generation, etc., the rule of thumb is to define the appropriate threat models and attackers’ capabilities for making meaningful analysis of adversarial robustness for the corresponding machine learning models. After the attack objective is formulated, a proper solver will be used to execute the adversarial attack depending on the data modality.

In what follows, we introduce some examples for data modalities and tasks beyond image classification.

# 6.2 Audio adversarial example

Carlini and Wagner (2018) propose an optimization-based attack for generating audio adversarial examples for automatic speech recognition systems. Given an audio waveform x, the task is to construct another audio waveform x\' = x + \delta such that x and x\' sound similar but their output transcription differs. To cater to the audio domain, they use decibels