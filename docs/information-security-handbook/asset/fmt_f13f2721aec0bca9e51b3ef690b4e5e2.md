
At the point when a specific PDF document is chosen for parsing by a parser, it plays out this action in the following way: Upon starting, the parser goes to the trailer field and decides the principal object to be deciphered \[2\]. At that point, grouping of items is parsed with the assistance of references mentioned in the cross-reference table. At that point, at long last, the parsing methodology is ended when it identifies the “finish of file marker” \[7\]. One of the huge highlights of utilizing PDF documents is that they take out the prerequisite of reproducing records without any preparation when some new articles are brought into the previously existing records \[2\]. Considering all these things, they make new field structures that are devoted to putting away the recently presented substance \[4\].

## 7.4 Steps Involved in Classifying PDF Files

“AI” innovation is broadly being used practically in each field \[1\]. This innovation helps in making the framework wiser and empowers it for dynamic \[1,8,9\] use. Because of its wide scope of utilization, it is likewise conveyed in deciding malignant substance covered up in records \[[10](#ch07.xhtml#ref7_10)\]. Here we will talk about how this innovation can be aided successfully by identifying the threatening code in a PDF record under investigation \[11,[12](#ch07.xhtml#ref7_12)\]. A few self-learning frameworks were proposed by scientists for examining the PDF records in the previous decade \[2,4,[13](#ch07.xhtml#ref7_13),[14](#ch07.xhtml#ref7_14)\]. In this part, we will examine the engineering of the self-learning-based malicious PDF finders and the means associated with ordering a given PDF record ([Figure 7.1](#ch07.xhtml#fig7_1)).

![Figure 7.1 Work flow of PDF malware classifier.](Images/fig7_1.jpg)

[Figure 7.1 Work flow of PDF malware classifier.](#ch07.xhtml#Ffig7_1)

The fundamental goal of these frameworks is to productively order whether a particular document goes under the benevolent classification or the malignant one \[[15](#ch07.xhtml#ref7_15)\]. For confirming that, the framework needs to inspect and measure the examples and designs of the record's inner parts \[10,15,[16](#ch07.xhtml#ref7_16),[17](#ch07.xhtml#ref7_17),[18](#ch07.xhtml#ref7_18),[19](#ch07.xhtml#ref7_19)\]. Despite the fact that there are numerous proposed identifiers, every one of them is seen to follow these three fundamental methods to examine the PDF records \[[8](#ch07.xhtml#ref7_8)\], which are:

### 7.4.1 Prior Procedure Before the Actual Parsing

This is the principal interaction completed on the PDF record that is picked for the review reason. In this technique, the inward code, which are basic, for example, JavaScript or ActionScript code, are executed in a steady climate under separation condition to comprehend its temperament \[2\]. It is prepared under detachment conditions with the goal that its execution does not influence the framework \[[20](#ch07.xhtml#ref7_20)\]. The other fundamental information components, for example, metadata of inward articles and watchwords are likewise removed from the PDF documents \[[11](#ch07.xhtml#ref7_11)\].

### 7.4.2 Feature Extraction

This is the following movement completed by the detectors after the “pre-processing” action is finished. This technique uses the proffered information acquired from its former advance to achieve its examination action \[3,11,[21](#ch07.xhtml#ref7_21), [22](#ch07.xhtml#ref7_22), [23](#ch07.xhtml#ref7_23), [24](#ch07.xhtml#ref7_24), [25](#ch07.xhtml#ref7_25), [26](#ch07.xhtml#ref7_26), [27](#ch07.xhtml#ref7_27)\]. In this progression, the information extricated from the past stage is changed to the type of vector numbers that will actually want to pass on the presence of specific segments, for example, catchphrase and “programming interface calls” in the PDF document \[[28](#ch07.xhtml#ref7_28)\].

### 7.4.3 Classifier

This is the stage where the algorithms are conveyed in dissecting the separated data from the past stages \[16\]. The classifiers are first prepared with test sets to build their information about deciding the contrasts between a generous and a threatening PDF record \[[29](#ch07.xhtml#ref7_29)\]. A framework can deliver quality effectiveness in arranging the PDF records, on the off chance that they are prepared productively \[19\]. The adequacy of the framework is not exclusively relied on the algorithm, yet in addition on the preparation set. The way toward preparing is led before the framework is really sent for the ongoing application \[[9](#ch07.xhtml#ref7_9)\]. The fundamental target of the classifier is to exactly order an offered document to be malicious or not \[2\].

## 7.5 Modes of Classification

The malware indicators worked for examining the PDF records by helping self-learning strategies to be arranged in two primary classifications, static detectors and dynamic detectors \[11\]. The static identifiers perform static investigation of the record without executing the code inside the document \[1,8–11,16–20,28,29,[30](#ch07.xhtml#ref7_30)\]. The dynamic finders play out their examination by executing the genuine code in steady natural conditions \[1,8,9,11,11,11,20,28–30\]. We will examine more about these two recognition types beneath.

## 7.6 Static Classification of PDF Files

A large portion of the malware assaults actualized by using the PDF records utilize JavaScript or ActionScript code \[11\]. Thus, these kinds of identifiers primarily center around the areas of the document where these sorts of codes are recognized. In any case, we cannot infer that a specific PDF record is a vindictive one just by taking a gander at the presence of the JavaScript code. Indeed, even benign records may likewise have such codes in them \[11\]. Along these lines, the static identifiers investigate for the examples of utilization of explicit factors, watchwords, capacities, and programming interface calls for deciding the idea of the document \[28\]. PJScan is a static PDF locator that chose the malignance of the PDF records dependent on the recurrence of use of variables, administrators, and capacities \[[31](#ch07.xhtml#ref7_31)\]. A portion of different locators depended on tokenization and matching strategies \[28\]. In any case, in situations where these JavaScript substances are vigorously obscured by the assailant inside the PDF records, the static classifier may flop by misclassifying the record \[1\]. The assailant can make the noxious substance especially covered up, with the goal that it can't be distinguished by the parser at the hour of parsing cycle, and this code can be powerfully called at runtime to complete the threatening activities. Thus, the primary defect existing in this class of detectors is that they can't be prepared to precisely order a purposely obfuscated tests \[2\] ([Figure 7.2](#ch07.xhtml#fig7_2)).

![Figure 7.2 Static PDF classifiers.](Images/fig7_2.jpg)

[Figure 7.2 Static PDF classifiers.](#ch07.xhtml#Ffig7_2)

## 7.7 Static Classification Systems

### 7.7.1 PJScan

Pavel Laskov and Nedim Šrndic \[31\], in 2011, proposed a static malware detection framework that was ready to distinguish the dangerous JavaScript content contained inside the document \[31\]. Creators guaranteed that their model had to have brought down the preparation time needed for examining the record compared to the recently introduced models, and it was likewise showing a perfect viability in recognizing known and obscure malevolent sorts \[31\]. This technique was most appropriate for preparing enormous data sets due to its low review time and high effectiveness \[31\] ([Figure 7.3](#ch07.xhtml#fig7_3)).

![Figure 7.3 Different phase flow of PJScan \[31\].](Images/fig7_3.jpg)
