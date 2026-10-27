
AI platform improves results by evaluating and analyzing all available data and best practices in order to give insights into and help in decision-making.

## Chapter 17: Cyborgs: A Coming Era

Anushka Purwar and Nidhi

This chapter discusses how cyborgs arose with the help of AI and cybernetics, applications of cybernetics, and different types of cyborgs present. The key contribution of this study is the presentation of cyborgization, the increase of biological beings with capabilities, and its future aspects as the effects of increased advancement in technology.

## 1 Mood-Detection Based Media Recommendation

*Prashant Singh, Dhyanendra Jain, Ashu Jain,*  
*Pratul Arvind, and Amit Kumar Pandey*  
Dr. Akhilesh Das Gupta Institute of  
Technology and Management

*Anil Kumar Sagar*  
Sharda University Greater Noida

*Sanjay Das*  
Indira Gandhi National Tribal University  
Regional Campus Manipur

## CONTENTS

| Section | Page |
|---|---|
| 1.1 Introduction | 1 |
| 1.1.1 Mood Taxonomy | 3 |
| 1.2 Related Works | 3 |
| 1.2.1 Media Recommendation | 3 |
| 1.2.2 Text-Based Emotion Detection | 4 |
| 1.2.3 Image-Based Emotion Detection | 4 |
| 1.3 Proposed System | 8 |
| 1.3.1 Text-Based Emotion Detection | 9 |
| 1.3.2 Emotion Detection Using Feature Extraction | 9 |
| 1.3.3 Media Recommendation Algorithm | 11 |
| 1.3.4 Result | 11 |
| References | 14 |

## 1.1 INTRODUCTION

The temperament of a human is generally reliant upon the feelings he/she has throughout an unequivocal timeframe. A human can distinguish the feelings of another human by directly seeing his face or by conversing with him and noticing the way he talks, the words he utilizes, and the demeanors he portrays while talking. These days, this capacity is being studied by machines utilizing deep learning methods where algorithms are planned so that they take input as text, pictures, or reviews and find the feelings, not to mention the disposition, of the client. Likewise, various applications are carried out alongside suggesting clients with activities and treatment remedies to assist them with handling their disposition. These kinds of calculations and applications are extremely valuable in clinical scenarios as once in a while a therapist thinks that it is hard to distinguish a patient’s state of mind; subsequently, he can undoubtedly depend on an ideal machine-based disposition identification framework. Ordinarily utilized calculations are carried out by an NLP (natural language processor) that handles the info given as text, incorporating various technologies like preprocessing, eliminating stop words, stemming, lemmatization, and word encoding. We use characterization calculations like k-nearest neighbors random forests, Naive Bayes, and logistic regression to decide the temperament. On account of profile pictures, CNNs (convolutional neural networks) are utilized to study them, and this course of extraction in which the mindset is supposed to dependent on elements of the face is called feature extraction. This calculation is a significant piece of deep learning. In this chapter, we present an application that performs calculations based on NLP and committee CNNs to recover the client temperament and utilizes an artificial intelligence (AI) method to decide the mindset effects of various media like music, recordings, and pictures and map them together to plan the final list of suggested media.

Vertical push as an element of the substantial arousing that is both non-public and individual. Eye-to-eye addresses play a significant role in sorting out an individual’s sentiments and the current disposition. Machines acquiring information can find sentiments by observing the looks and examining what each statement implies. That expertise furthermore applies to the recently gained data. As of late, gadget considering has acquired force in creative and insightful guidance programs in PC. The advantages of a gadget is principally based upon the exhortation calculations and splendid advancement on the resultant three abilities such as:

- Collaborative studying ability of solid consultant
- Content basically based thoroughly sifting profound
- Transaction among abilities

Conventional guidance structures depend upon individual explicit data content, material, and records. Over the long run, we’ve seen an apparent blast in endeavors to utilize sentiments in explicit ways to design better quality exhortation structures. The default guidance is one of these astonishing techniques. Various media frameworks are set as default. Investigate these destinations for get-together capacities actually like people. The individual’s produce directs that don’t convey in expressions and deeds in loads of ways, specifically through looks. Through video exhortation programs, we can expand sentiments by computing an individual’s look.

There are numerous mechanical progressions identified with advancement in music also, or we can call them the rebuilding of music information; however, we have not yet tackled this issue here. Reestablishing music information is consistently the subject of extraordinary exploration. There is a great deal of music accessible to us, which is difficult for a PC to introduce. Then again, we have additionally taken extraordinary steps in enthusiastic knowledge. Large numbers of the techniques and calculations accessible. But here as well, the issue stays annoyingly on the grounds that the two capacities are performed in an unexpected way; here it attempts to consolidate the two innovative headways, even in their typical lives. In the standard FER framework, the eyes and mouth are significant highlights of looks. Your feelings or sentiments are reflected by your eyes and lips such as “I can’t imagine you interestingly.”

![](img/56cfba5af06305175d6488aec4d55ab0_31_0.png)

**FIGURE 1.1** Thayer’s Model of Mood [1].

### 1.1.1 Mood Taxonomy

As mentioned in [2], the conventional approach to identifying mood reaction in music psychology is to use adjective descriptors, such as pathetic, optimistic, and gloomy. In the late 1990s, a two-dimensional mood model was introduced by Thayer (1989). This dimensional approach takes the idea that mood consists of two factors, tension (happy/anxious) and energy (calm/energetic), and splits the mood of music into four clusters: contentment, sadness, exuberance, and anxious/frantic as depicted in Figure 1.1.

Such concepts are clear and discriminatory for the four clusters, and the two-dimensional framework still offers significant computer modeling markers. It is, thus, used in our method of mood detection.

## 1.2 RELATED WORKS

### 1.2.1 MEDIA RECOMMENDATION

In [3], Erion C Riccardo Coppola Eleonora Gargiulo, Marco Marengo, and Maurizio Morisio proposed a mood based on car music system which relates between the mood of the driver and mood of a song by analyzing its lyrics and hence a recommendation system.

Charulatha Vijaykumar in her proposed theory [4] explained about a system by which lyrics of songs are extracted using APIs and an algorithm is used to determine mood of the user; then, the two are matched and music is played accordingly.
