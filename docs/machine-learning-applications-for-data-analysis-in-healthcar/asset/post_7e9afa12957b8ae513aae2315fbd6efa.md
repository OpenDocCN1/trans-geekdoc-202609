
## 11.4 CASE STUDY

### 11.4.1 DATA SET

We collected over 500 accident text data from the workplace at distinct working sites. Initially, text was in raw format, so first, we did some preprocessing: stop words removal, convert to lowercase and punctuation removal, tokenization, stemming, lemmatization, and brought the text data into a desired usable format. About 450 text data having rows of multiple sentences were manually annotated and stored in json format as an input to the custom-trained NER model.

We pre-labeled the text data and then used TF–IDF and linear SVC to classify them into four categories: (1) human factor, (2) component factor, (3) management factor, and (4) environmental factor.

Before this, we used the elbow method to find out the optimal number of clusters that fit for this text data and we got k in the range 4–6.

### 11.4.2 DATA VISUALIZATION

Figure 11.4 is the word cloud of the most occurring keywords in sentence after preprocessing such as

![](img/e7e1b4040cce350b0d1520d1f0df754d_208_0.png)

**FIGURE 11.4 Word Cloud.**

- Change text to lowercase
- Remove stop words
- Remove bad characters
- Remove punctuation

Overall, it gives an approximate idea about which word is most important. From Figure 11.4, we can extract top events like [slipped, fell, fall, broken, damage, fire].

## 11.5 RESULTS

### 11.5.1 CUSTOM-TRAINED NER MODEL

We find out the root cause and object using a custom-trained NER model and target sentence using regular expression. Root cause is the factor which may lead to an accident. We find from the NER model that the most frequent root cause words are [fall, fall down, fell, slipped, gas leakage, hydraulic leakage, fire] (Figure 11.5).

| | Potential_Sentence | Root_Cause | Object | Target_Sentence | Symbol |
|---|---|---|---|---|---|
| 0 | S.D.L crew not handling cable properly . there was a chance to break. | not handling | cable | S.D.L crew not handling cable properly . | X1 |
| 1 | When sdl crew was working at the face , debris of coal fall down near the worker but there was no injured | fall down | coal | debris of coal fall down near the worker but there was no injured | X2 |
| 2 | During sdf cable handling one sdl crew slipped but not injured. | slipped | cable | During sdf cable handling one sdl crew slipped but not injured. | X3 |
| 3 | During pipe extension the pipe filter was fell down but no injury. | fell down | pipe | During pipe extension the pipe filter was fell down but no injury. | X4 |
| 4 | when two sdl crew was going to the face suddenly side loose coal was fall and they were escape normally from injured. | fall | coal | when two sdl crew was going to the face suddenly side loose coal was fall and they were escape normally from injured. | X5 |

**FIGURE 11.5** Output from custom NER model.

### 11.5.2 CLASSIFICATION

We categorize the root cause word into four levels of failure, that is human factor, component factor, environment factor, and management factor by using the TF–IDF matrix as an input to the linear SVC. We used 450 data for training and the rest 50 for testing purposes.

We observed that factor that leads to most accidents are management factor and environment error that causes the least. Out of 50 accidents, 28 happened due to management errors (Figure 11.6a–c).

![](img/e7e1b4040cce350b0d1520d1f0df754d_210_0.png)

**FIGURE 11.6 (a) Frequency distribution.**

![](img/e7e1b4040cce350b0d1520d1f0df754d_210_1.png)

**FIGURE 11.6 (b) Confusion matrix.**

![](img/e7e1b4040cce350b0d1520d1f0df754d_210_2.png)

**FIGURE 11.6 (c) Elbow plot.**

Since it is a multiclass classification problem, linear SVC performs better. The accuracy from the linear SVC model we got is 66%. From the elbow method graph, we concluded the number of clusters we should make.

### 11.5.3 BOW-TIE ANALYSIS

![](img/e7e1b4040cce350b0d1520d1f0df754d_211_0.png)

![](img/e7e1b4040cce350b0d1520d1f0df754d_211_1.png)

We have used BowTieXP software to draw bow-tie diagrams for each top event. We observed that most of the accidents happened due to management errors. And the top events include (slipped, fell, fall, broken, damage, fire, breakage). Figure 11.7a and b are bow-tie diagrams for a slipped event and gas leakage, respectively, that lead to an accident. We suggested protective barriers for each factor on the left of bow-tie and protective barrier in case an accident already happened. Also, we categorize the root causation into four levels of factors shown on the left of the bow-tie diagram.

## 11.6 DISCUSSION

We collected more than 500 accident text data from the workplace at a distinct working site. Data comprise raw text data, so we first did preprocess like stop word removal, convert to lowercase and punctuation removal, tokenization, stemming, and lemmatization, thus bringing the data in a correct usable format. In order to find out the root causation and object involved in an accident, we applied a custom-trained NER model on annotated 450 text data with the label of root cause and object. This custom-trained NER model gave F1 score of 0.84 which is better than compared with a pretrained NER model with F1 score of only 0.51. Also, we find out the potential sentence which contains both root cause word and object using regular expression technique. To categorize the text containing causation words, we first applied the elbow method to get the optimal number of clusters, we got the output of 4–6. Linear SVC gives good accuracy over NB and RF classifiers. The accuracy we got from linear SVC is 66%. Finally, we build a bow-tie diagram using open-source BowtieXP software for better visualization of accident reports. Also, we find the most frequently occurring words in our whole corpus, called top event related to accidents like fire, fall down, slipped, and gas leakage. On the left of top event, we suggested preventive measures for the threat, and on the right, we suggested mitigative measures so that we can prevent future danger or injury.

## 11.7 CONCLUSION

In a workplace, workers experience varying levels of stress. As we know accidents nowadays happen quite often at every worksite. In this study, we used an integrated approach of NLP, TF–IDF vectorizer linear SVC, and qualitative bow-tie analysis. Our approach is different from other basic methods of quantitative risk analysis like Part of Speech tagging, predefined named entity model that is also capable of Information extraction from text. We applied a custom-trained NER model after annotating over 450 text data, thus got a better F1 score over the predefined NER model. For classification, we used TF–IDF vectorizer and linear SVC model. The accuracy of linear SVC was better than other models like NB and RF classifier. Also, the accuracy will be further increased when we consider more elements of events that cause accidents such as weather and environmental factors. In order to visualize these accidents/incidents, root causes, and their categories, bow-tie methodology is applied. In the future, the proposed method can be employed in different sectors such as healthcare risk analysis and proper safety management in organizations.

## ACKNOWLEDGMENTS

We acknowledge the Centre of Excellence in Safety Engineering and Analytics (CoE-SEA) (www.iitkgp.ac.in/department/SE), IIT Kharagpur, and Safety Analytics and Virtual Reality (SAVR) Laboratory (www.savr.iitkgp.ac.in) of Department of Industrial and Systems Engineering, IIT Kharagpur, for experimental/computational and research facilities for this work. We would like to thank the management of the plant for providing relevant data and for their support and cooperation during the study.

## KEYWORDS

- accident/incident reports
- root causes
- risk analysis
- natural language processing
- classification
- bow-tie analysis

## REFERENCES

1. Abdi Z, Ravaghi H, Abbasi M, Delgoshaei B, Esfandiari S. Application of bow-tie methodology to improve patient safety. International Journal of Health Care Quality Assurance 2016;29(4):425–440.
2. Bertke SJ, Meyers AR, Wurzelbacher SJ, Measure A, Lampl MP, Robins D. Comparison of methods for auto-coding causation of injury narratives. Accident Analysis and Prevention 2016;88:117–123.
