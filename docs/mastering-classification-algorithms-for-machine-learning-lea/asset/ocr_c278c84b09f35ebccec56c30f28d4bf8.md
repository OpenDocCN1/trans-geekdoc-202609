# Building speech emotion analysis model using Bagging algorithm

Emotion analysis is widely used in many industries. Companies providing online services use emotion analysis to analyze customer feedback. In a clinical investigation, it is used to predict the state of the patients. The human resources department uses it for applications like attrition prediction, and so on. In the Insurance industry, there are many more use cases for emotion analysis.

Emotion analysis is generally conducted on Text data. This is a field of Natural Language Processing (NLP). The different words are analyzed in this field to determine the sentiment and emotion. We will discuss emotion analysis from speech. In a speech, the aspects like pitch, tone, speaking pace, loudness, and so on., are analyzed to decide the emotion expressed in a speech.

This field of using machine learning for emotion analysis from the speech is still nascent, as few reliable datasets are available for building good machine learning models. We will discuss the mechanics of building such models. The models can be improved by supplying better quality data to the model and improving the model itself.

# Regarding the data set

As discussed in this chapter, the datasets used in emotion analysis from speech have been obtained from Kaggle. The data is available from 2 sources. The first source is the University of Toronto, and the data is called Toronto Emotional Speech Set or TESS.¹ The second data set is the Ryerson Audio-Visual Database of Emotional Speech and Song or Ravdessd.²

# TESS dataset

TESS dataset contains 2880 files. Each file contains an audio recording. A set of 200 target words were spoken in the carrier phrase “Say the word ______” by two actresses, and the sets were recorded in seven different emotions (anger, disgust, fear, happiness, pleasant surprise, sadness, and neutral). Both actresses spoke English as their first language, were university educated, and had musical training. Audiometric testing indicated that both actresses had thresholds within the normal range.

+   1 https://borealisdata.com/dataset.xhtml?persistentid=do:10.5683/SP2/E8H2MF
2 https://zenodo.org/record/1188976#Y_RMYuxBzA1