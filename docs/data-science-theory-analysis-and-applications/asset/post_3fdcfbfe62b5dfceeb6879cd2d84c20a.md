
![](img/5025594f89449de2a74e5b325b1e84ef_333_0.png)

## FIGURE 14.6 Architecture of VGG16.

The sequences were taken over a static (black) background with a frame size of 1,920 × 1,080 pixels at a rate of 25 fps [61].

All the experiments were implemented using Windows 10 operating system with Intel core i5 3.3 GHz processor with Anaconda Python and Jupyter notebook. The dataset is trained with a batch size 64 and 20 epochs.

## 14.4.2 PERFORMANCE EVALUATION METRICS

The confusion matrix is a table with actual classifications as columns and predicted ones as rows (Figure 14.8).

- True Positives (TP)—when the data point of actual class and predicted was (True).
- True Negatives (TN)—when the data point of actual class and predicted was (False).
- False Positives (FP)—when the data point of actual class (False) and the predicted is (True).
- False Negatives (FN)—when the data point of actual class (True) and the predicted is (False).

![](img/5025594f89449de2a74e5b325b1e84ef_334_0.png)

FIGURE 14.7 An example frame of five emotions and three actions.

| Actual Class | | 
|---|---|
| Predicted Class | True Positive | False Positive |
| | True Negative | False Negative |

FIGURE 14.8 Confusion matrix.

The performance evaluation of the proposed work can be calculated using Accuracy, Recall, F-Score, Specificity, and Precision. Accuracy in classification problems is the number of correct prediction made by the model over all kinds of prediction made, which can be calculated using Equation (14.7).

Accuracy = (TP + TN) / (TN + FP + TP + FN) (14.7)

Recall specifies how extraordinary an emotion is recognized accurately.

Recall = TP / (TP + FN) (14.8)

The symphonies mean of Precision and Recall is called as F-score.

F-score = 2 × Precision × Recall / (Precision + Recall) (14.9)

Specificity shows the evaluation of how great a strategy is in recognizing a negative emotion accurately.

Specificity = TN / (TN + FP) (14.10)

At last, Precision shows the proportion of classification, which can be calculated by Equation (14.11).

Precision = TP / (TP + FP) (14.11)

where TP and TN are the quantity of true positive and true negative prediction of the class, and FP and FN are the quantity of false positive and false negative expectations.

## 14.5 RESULTS AND DISCUSSIONS

Table 14.1 describes the FDCCN model that shows the individual recognition accuracy of all classes. The correlation among happy jump, untrustworthy jump, and angry jump are closer to one another. The performance of this network is good in recognizing emotions like happy walk, sad walk, sad sit, and happy sit than other emotions. Table 14.2 describes the correlation among all 15 classes and shows the individual recognition accuracy of each class using VGG16 model. Tables 14.1 and 14.2 are the individual recognition accuracy of all classes, and the values in those tables do not exceed 100%. Table 14.3 shows the performance measure of precision, recall, and f-measure values of FDCNN and VGG16 model. The value 1 means best, and the value 0 means worst. In this experiment, the values obtained in Table 14.3 are mostly close to 1.

### TABLE 14.1 Individual Accuracy (%) for 15 Class Emotions of an FDCNN Model

| | AJ | AS | AW | FJ | FS | FW | HJ | HS | HW | SJ | SS | SW | UJ | US | UW |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| AJ | 95 | 0 | 0 | 1 | 0 | 0 | 2 | 0 | 0 | 0 | 0 | 0 | 2 | 0 | 0 |
| AS | 0 | 96 | 0 | 0 | 1 | 0 | 0 | 2 | 0 | 0 | 1 | 0 | 0 | 0 | 0 |
| AW | 0 | 0 | 96 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 2 |
| FJ | 2 | 0 | 0 | 94 | 0 | 0 | 1 | 0 | 0 | 2 | 0 | 0 | 1 | 0 | 0 |
| FS | 0 | 1 | 0 | 0 | 95 | 0 | 0 | 1 | 0 | 0 | 2 | 0 | 0 | 1 | 0 |
| FW | 0 | 0 | 3 | 0 | 0 | 95 | 0 | 0 | 2 | 0 | 0 | 0 | 0 | 0 | 0 |
| HJ | 0 | 0 | 0 | 1 | 0 | 0 | 96 | 0 | 0 | 2 | 0 | 0 | 1 | 0 | 0 |
| HS | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 97 | 0 | 0 | 0 | 0 | 0 | 1 | 0 |
| HW | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 94 | 0 | 0 | 3 | 0 | 0 | 2 |
| SJ | 4 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 94 | 0 | 0 | 0 | 0 | 0 |
| SS | 0 | 3 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 95 | 0 | 0 | 1 | 0 |
| SW | 0 | 0 | 4 | 0 | 0 | 2 | 0 | 0 | 0 | 0 | 0 | 92 | 0 | 0 | 2 |
| UJ | 0 | 0 | 0 | 2 | 0 | 0 | 3 | 0 | 0 | 4 | 0 | 0 | 91 | 0 | 0 |
| US | 0 | 3 | 0 | 0 | 2 | 0 | 0 | 1 | 0 | 0 | 2 | 0 | 0 | 92 | 0 |
| UW | 0 | 0 | 2 | 0 | 0 | 5 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 91 |

Note: AJ = AngryJump, AS = AngrySit, AW = AngryWalk, FJ = FearJump, FS = FearSit, FW = FearWalk, HJ = HappyJump, HS = HappySit, HW = HappyWalk, SJ = SadJump, SS = SadSit, SW = SadWalk, UJ = UntrustworthyJump, US = UntrustworthySit, UW = UntrustworthyWalk.

### TABLE 14.2 Individual Accuracy (%) for 15 Class Emotions of VGG16 Model

| | AJ | AS | AW | FJ | FS | FW | HJ | HS | HW | SJ | SS | SW | UJ | US | UW |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| AJ | 96 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 2 | 0 | 0 |
| AS | 0 | 96 | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 1 | 0 |
| AW | 0 | 0 | 95 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 2 |
| FJ | 2 | 0 | 0 | 96 | 0 | 0 | 1 | 0 | 0 | 2 | 0 | 0 | 1 | 0 | 1 |
| FS | 0 | 1 | 0 | 0 | 96 | 0 | 0 | 1 | 0 | 0 | 2 | 0 | 1 | 1 | 0 |
| FW | 1 | 0 | 2 | 0 | 0 | 95 | 0 | 0 | 2 | 0 | 0 | 0 | 0 | 0 | 0 |
| HJ | 0 | 0 | 0 | 1 | 0 | 0 | 96 | 0 | 0 | 2 | 0 | 0 | 1 | 0 | 0 |
| HS | 0 | 1 | 1 | 0 | 1 | 0 | 0 | 96 | 0 | 0 | 0 | 0 | 0 | 1 | 0 |
| HW | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 94 | 0 | 0 | 3 | 0 | 0 | 2 |
| SJ | 4 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 96 | 0 | 0 | 0 | 2 | 0 |
| SS | 0 | 3 | 0 | 0 | 0 | 2 | 0 | 1 | 0 | 0 | 97 | 0 | 0 | 1 | 0 |
| SW | 1 | 0 | 4 | 0 | 0 | 2 | 0 | 0 | 0 | 2 | 0 | 95 | 0 | 0 | 2 |
| UJ | 2 | 0 | 0 | 2 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 94 | 0 | 0 |
| US | 0 | 0 | 0 | 0 | 2 | 0 | 0 | 1 | 0 | 0 | 2 | 0 | 0 | 95 | 0 |
| UW | 0 | 0 | 2 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 96 |

Note: AJ = AngryJump, AS = AngrySit, AW = AngryWalk, FJ = FearJump, FS = FearSit, FW = FearWalk, HJ = HappyJump, HS = HappySit, HW = HappyWalk, SJ = SadJump, SS = SadSit, SW = SadWalk, UJ = UntrustworthyJump, US = UntrustworthySit, UW = UntrustworthyWalk.

### TABLE 14.3 Performance Measure of an Emotion Dataset with FDCNN and VGG16

| Model | Precision VGG16 | Precision FDCNN | Recall VGG16 | Recall FDCNN | F-Measure VGG16 | F-Measure FDCNN |
|---|---|---|---|---|---|---|
| AJ | 0.937 | 0.891 | 0.828 | 0.821 | 0.933 | 0.881 |
| AS | 0.881 | 0.854 | 0.897 | 0.885 | 0.909 | 0.877 |
| AW | 0.842 | 0.825 | 0.921 | 0.913 | 0.911 | 0.901 |
| FJ | 0.881 | 0.862 | 0.897 | 0.886 | 0.919 | 0.891 |
| FS | 0.871 | 0.869 | 0.932 | 0.924 | 0.949 | 0.876 |
| FW | 0.895 | 0.883 | 0.891 | 0.883 | 0.907 | 0.879 |
| HJ | 0.884 | 0.873 | 0.935 | 0.927 | 0.915 | 0.913 |
| HS | 0.862 | 0.854 | 0.899 | 0.879 | 0.919 | 0.902 |
| HW | 0.843 | 0.839 | 0.928 | 0.911 | 0.931 | 0.911 |
| SJ | 0.931 | 0.930 | 0.858 | 0.849 | 0.927 | 0.886 |
| SS | 0.852 | 0.844 | 0.887 | 0.879 | 0.915 | 0.897 |
| SW | 0.892 | 0.882 | 0.931 | 0.922 | 0.951 | 0.879 |
| UJ | 0.933 | 0.924 | 0.818 | 0.821 | 0.973 | 0.880 |
| US | 0.891 | 0.887 | 0.890 | 0.881 | 0.899 | 0.878 |
| UW | 0.852 | 0.831 | 0.910 | 0.928 | 0.915 | 0.909 |

Note: AJ = AngryJump, AS = AngrySit, AW = AngryWalk, FJ = FearJump, FS = FearSit, FW = FearWalk, HJ = HappyJump, HS = HappySit, HW = HappyWalk, SJ = SadJump, SS = SadSit, SW = SadWalk, UJ = UntrustworthyJump, US = UntrustworthySit, UW = UntrustworthyWalk.

## 14.6 CONCLUSION

In this chapter, an FDCNN and VGG16 model for recognizing human emotions from body movements on sequence of frames were proposed. This model is representing deep features to extract saliency information at multiple scales. The proposed method is evaluated on a challenging benchmark emotion dataset (University of York). The emotions such as Angry Jump, Angry Sit, Angry Walk, Fear Jump, Fear Sit, Fear Walk, Happy Jump, Happy Sit, Happy Walk, Sad Jump, Sad Sit, Sad Walk, Untrustworthy Jump, Untrustworthy Sit, and Untrustworthy Walk are used in this work. Among the two models, VGG16 performed better recognition of emotions. The performance of this model is better than the baseline models. Future work aims at developing research applications to recognize the emotions of children with autism spectrum disorder (ASD). The autism children express their emotion through facial and body movements. ASDs are neurodevelopmental disorders in which multiple genetic and environmental factors play roles. Symptoms of deficit in social communication and restrictive, repetitive behavioral patterns emerge early in a child’s development. ASD is a lifelong neurodevelopmental disorder involving core deficit in interpersonal communication and social interactions, as well as restricted, repetitive mannerisms and interests (American Psychiatric Association, 2013). Children with ASD struggle with significant relationships and behavioral challenges and, in most cases, have serious implications for social inclusion in adulthood.

## REFERENCES

1. R. Plutchik, *The Emotions*, University Press of America, 1991. Lanham, Maryland
2. F. E. Pollick, H. M. Paterson, A. Bruderlin, A. J. Sanford, “Perceiving Affect from Arm Movement,” *Cognition*, Vol. 82, Issue 2, pp. 51–61, 2001.
3. P. N. Lopes, P. Salovey, R. Straus, “Emotional intelligence, personality, and the perceived quality of social relationships,” *Personality and Individual Differences*, Vol. 35, Issue 3, pp. 641–658, 2003.
4. M. A. Goodrich, A. C. Schultz, “Human-Robot interaction: A survey,” *Foundation and Trends in Human Computer Interaction*, Vol. 1, Issue 3, pp. 203–275, 2007.
5. H. R. Markus, S. Kitayama, “Culture and the self: Implications for cognition, emotion, and motivation,” *Psychological Review*, Vol. 98, pp. 224–253, 1991.
