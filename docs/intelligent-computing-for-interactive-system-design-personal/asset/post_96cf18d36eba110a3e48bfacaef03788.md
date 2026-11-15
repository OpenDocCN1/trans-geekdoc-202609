
For each placement (e.g., pocket or desk), we collected data from our three prototypes in two orientations each (e.g., facing-in and facing-out). We assembled these six sensor recordings for each placement into a single virtual-recording. This simulates a virtual device with the union of sensing capabilities from our three prototypes. This means that a single instance of collected data included: capacitive data (facing forward and backward), multispectral data (facing forward and backward), phone light/proximity sensor data (facing forward and backward), and phone accelerometer readings. We only considered one set of phone accelerometer readings because the second set from the phone facing the other direction was redundant.

## 9.2.5 Q5: What Are the Privacy and Ethical Implications of Developing this Classifier?

While this classifier is a learning tool for us, rather than a production system, it's still important to consider potential privacy or ethical implications. One such implication is that it may not occur to a user that you could infer this data from accelerometer readings. Thus, if a developer with this classifier requested access to accelerometer data without disclosing that they had this inference ability, that could be considered a privacy violation. Another potential issue is that it may be possible to infer other characteristics about an individual based on their placement behaviors. For example, we saw differences between the behaviors of men and women in the data that we collected. Therefore, this classifier could be used as a clue to the gender of the user, even if they have not disclosed that information. Finally, while we tried to collect data from a variety of participants, our sample population is not nearly representative of all of the different characteristics of the broader population. While this might have been okay for an initial research effort, it would be very irresponsible to only use this data to train a production classifier.

## 9.2.6 Q6: A General Classifier or Personal Classifiers?

In this project we focused on a general classifier for one reason in particular: the amount of data we collected. In addition, it would be desirable for many of these use cases for the classifier to work out of the box without any training by the user (i.e., the cold start problem). However, the data that we collected does suggest that personalized classifiers are likely to perform better than a general classifier. We identified different archetypes of users (i.e., different people have different priors for different classes). In addition, other contextual factors (e.g., location, time of day, calendar information) might be useful for an individual, but would be difficult to generalize across the population.

![](img/37b9feea690424a4c981364f15c3ffa2_13_0.png)

Figure 9.3 Example of accelerometer data collected during the study.

## 9.2.7 Q7: What Happens When the Classifier Is Wrong?

Given the results in the next section, it is clear that this classifier is going to be wrong fairly often. This has implications for the types of situations that the classifier should be used in. In some sense, the results of the classifier are more of a _noisy contextual hint_ than a reliable inference of context. For the purposes of demonstrating feasibility and establishing a baseline, this is fine. However, you probably wouldn't want this classifier to be making decisions about when your phone should or shouldn't be silent: you might miss a call or interrupt someone giving a presentation because of a missed classification.

## 9.2.8 Q8: How Well Does the Classifier Perform?

After asking and answering all of these questions, we're ready to build and evaluate the classifiers. How do they perform with all of the data we've collected?

### 9.2.8.1 Modeling Phone Placement from In-situ Data

We used the labeled accelerometer data collected _in situ_ by our ESM participants (see Figure 9.3 for an example). Using techniques from Chapters 2 and 3, we extracted the following features over each axis of 1s windows of accelerometer data as inspired by previous work [Kunze et al. 2005, Shi et al. 2011, Tsai et al. 2011, Vahdatpour et al. 2011]:

- mean; variance; root mean square (RMS): ($\sqrt{\frac{1}{N} * \Sigma_i x_i^2}$)
- interquartile range; 25%, 50%, 75% quartiles (see Section 2.5.2.2)
- the sum of detail coefficients across the first five wavelet levels

We used these features to evaluate models for three classification problems (following). All models were built using the Weka Toolkit's sequential minimal optimization (SMO) support vector machine (SVM) with a polynomial kernel [Hall et al. 2009]. See Section 4.2.2.2 for an explanation of SVM. We chose these features and the SMO algorithm by experimenting with pilot data we collected earlier. The results are reported from a leave-one-participant-out cross-validation. This approach to cross-validation is useful for making sure that we do not train and test on data from the same participant, which could lead to over-fitting and thus an over-estimation of the accuracy of our models.

## Table 9.2 Results from the ESM study for each of three classification problems

| | enclosed | out | precision | recall |
|---|---|---|---|---|
| enclosed | 1690 | 599 | 0.74 | 0.83 |
| out | 337 | 3742 | 0.92 | 0.86 |

| | onPerson | other | precision | recall |
|---|---|---|---|---|
| onPerson | 2335 | 402 | 0.85 | 0.89 |
| other | 511 | 4120 | 0.86 | 0.82 |

| | pocket | bag | out | hand | precision | recall |
|---|---|---|---|---|---|---|
| pocket | 1570 | 25 | 73 | 335 | 0.78 | 0.78 |
| bag | 141 | 32 | 85 | 28 | 0.11 | 0.25 |
| out | 188 | 25 | 2961 | 194 | 0.88 | 0.86 |
| hand | 124 | 44 | 308 | 235 | 0.33 | 0.30 |

For all three confusion matrices, the labels on the left represent the correct class, and the labels on the top row indicate the predicted class.

To summarize the results of the three different classifiers:

- **Enclosed or Out**: This model achieved a mean accuracy of 85.3%. The confusion matrix can be seen in Table 9.2, along with precision and recall values.

- **On Person or Not**: This model achieved a mean accuracy of 85.7% (Table 9.2).

- **In Bag, In Pocket, Out, or In Hand**: The performance of this model was lower than for the previous two models, as we expect when increasing the number of classes. The model achieved a mean accuracy of 75.4%, with Out being the most accurately classified, followed by Pocket. Bag and Hand performed much worse.

In the case of the four-class model, several notable items stand out. First, it is important to note that Bag and Hand, which performed very poorly, also had distinctly fewer instances in our dataset than Pocket and Out.

The accelerometer can be thought of as capturing the orientation of the device, however, unlike sitting out on a table (where it usually sits flat either face-up or face-down), a phone may be placed in a bag any number of ways, depending on the style of the bag, the orientation of its pockets, and so forth. Furthermore, at any given time a bag may or may not be being carried by a person, which could make some of these features confusing with other classes (e.g., pocket).

## 9.2.8.2 Modeling Phone Placement from Additional Sensors in the Lab

We collected additional data in the lab, as described in Section 9.2.3. We extracted features from the accelerometer facing one direction and our other sensors facing two directions. This allowed us to simulate a device with sensors on two sides.

Following Harrison and Hudson's [2008] approach, our multi-spectral features are one reading from each of the light-to-frequency converter and photo resistor for each of no-light, red, blue, green, UV, and IR. For the light and proximity-sensor on the phone, we took the mean over the 20s window of the ambient-light level and the binary proximity state. Lastly, we took the mean over a 1s window at each "pixel" in the capacitive sensing grid and computed three features over the grid: mean over pixels, median pixel value, number of non-zero pixels (pixels with some capacitance sensed). We used the same accelerometer features over a 1s window as in the ESM study from the previous section.

Our classification technique and evaluation followed that of the ESM study: a leave-one-participant-out cross-validation, where we counted each person or surface as a separate participant. We analyzed the lab study data by addressing the same classification tasks that we identified for the ESM study: Enclosed or Out, On Person or Not, and In Bag, In Pocket, Out or In Hand. In addition, we trained each of these models with different combinations of data sources: each of them individually, then the new data sources combined with accelerometer data. Our goal in doing this was to understand the value of the additional sensors on top of the accelerometers that are already common on devices.

Like the ESM data, we constructed Enclosed or Out models using Weka's SMO SVM with a polynomial kernel. When we experimented with pilot data, we discovered that the On Person or Not and In Bag, In Pocket, Out or In Hand problems were classified much better using Weka's implementation of Random Forest [Breiman 2001], which is a collection of decision trees as described in Section 4.2.2.3. Thus, we employ a Random Forest classifier for those problems in our lab study.

Table 9.3 gives an overview of the accuracies from these models. From these results we can see some interesting trends:

- 1. Enclosed or Out: Perhaps unsurprisingly, the phone's light and proximity sensor seems to be the most useful sensor for classification, yielding an average accuracy of 98%. Beyond this, there seems to be some evidence that the accelerometer can help to disambiguate the few errors made using light/proximity only, even achieving 100% accuracy in one case.

- 2. On Person Or Not: By contrast, when classifying whether or not the phone was on the participant, the light/proximity sensor performed the worst of each of the individual sensors (71%). In this case, the capacitive sensor was
