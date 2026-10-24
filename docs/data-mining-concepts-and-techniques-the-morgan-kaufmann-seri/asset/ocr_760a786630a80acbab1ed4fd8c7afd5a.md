an unknown tuple, X, the set of classifiers vote as an ensemble. For example, if classifier j predicts the positive class for X, then class j gets one vote. If it predicts the negative class for X, then each of the classes except j gets one vote. The class with the most votes is assigned to X.

All-vs.-all (AVA) is an alternative approach that learns a classifier for each pair of classes. Given m classes, we construct m(m-1)/2 binary classifiers. A classifier is trained using tuples of the two classes it should discriminate. To classify an unknown tuple, each classifier votes. The tuple is assigned the class with the maximum number of votes. All-vs.-all tends to be superior to one-vs.-all.

A problem with the previous schemes is that binary classifiers are sensitive to errors. If any classifier makes an error, it can affect the vote count.

Error-correcting codes can be used to improve the accuracy of multiclass classification, not just in the previous situations, but for classification in general. Error-correcting codes were originally designed to correct errors during data transmission for communication tasks. For such tasks, the codes are used to add redundancy to the data being transmitted so that, even if some errors occur due to noise in the channel, the data can be correctly received at the other end. For multiclass classification, even if some of the individual binary classifiers make a prediction error for a given unknown tuple, we may still be able to correctly label the tuple.

An error-correcting code is assigned to each class, where each code is a bit vector. Fig. 7.25 shows an example of 7-bit codewords assigned to classes C1, C2, C3, and C4. We train one classifier for each bit position.17 Therefore in our example we train seven classifiers. If a classifier makes an error, there is a better chance that we may still be able to predict the right class for a given unknown tuple because of the redundancy gained by having additional bits. The technique uses a distance measurement called the Hamming distance to guess the “closest” class in case of errors, and is illustrated in Example 7.8.

**Example 7.8. Multiclass classification with error-correcting codes.** Consider the 7-bit codewords associated with classes C1 to C4 in Fig. 7.25. Suppose that, given an unknown tuple to label, the seven trained binary classifiers collectively output the codeword 0001010, which does not match a codeword for any of the four classes. A classification error has obviously occurred, but can we figure out what the classification most likely should be? We can try by using the **Hamming distance**, which is the number of different bits between two codewords. The Hamming distance between the output codeword and the codeword for C1 is 5 because five bits—namely, the first, second, third, fifth, and seventh—differ. Similarly, the Hamming distance between the output code and the codewords for C2 through C4 are 3, 3, and 1, respectively. Note that the output codeword is closest to the codeword for C4. That is, the

| Class | Error-correcting codeword |
| :--- | :--- |
| C1 | 1 1 1 1 1 1 1 |
| C2 | 0 0 0 0 1 1 1 |
| C3 | 0 0 1 1 0 0 1 |
| C4 | 0 1 0 1 0 1 0 |

**FIGURE 7.25**
Error-correcting codes for a multiclass classification problem involving four classes.