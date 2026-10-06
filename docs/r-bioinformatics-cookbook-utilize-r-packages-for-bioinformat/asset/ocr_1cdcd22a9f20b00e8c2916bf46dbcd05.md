# Searching Gene and Protein Sequences for Domains and Motifs

sample() to randomly choose indices of the sequences to put into the training set. The training_set_indices variable contains integers that we will use to subset data later. Then, we make a vector of complementary indices for the test set in test_set_indices by using the square bracket and the negation operator (-). In essence, this is an idiomatic way of creating a vector that contains every index not in training_set_indices.

In step 3, we construct and train the SVM model, and we start by choosing a kernel to map the input data into a matrix space that the SVM can learn. Here, we use the gappyPair() function. Note that there are lots of kernels; this one is well suited to sequence data. We pass the kernel to the ksvm() function with the training_set_indices subset of sequences as the x parameter and the same subset of classes as the y parameter. Other arguments in this function determine the exact model type and package and they can have a strong effect on the quality of the final model. It is well reading up and doing some scientific experimentation on what works best for your particular data. The final model is saved in the model variable.

In step 4, although our model is constructed, we must now test its accuracy. To do this, we run it with the unseen data from earlier, by test_set_indices, and compare its predictions with real labels. Again, we use the prediction() function to do this evaluatePrediction(), along with the real class labels from the classes vector and a vector of all possible class labels. Using the AllLabels argument returns a summary of the accuracy and other metrics of the model, as shown here:

```
## 1 -1
## 1 25 13
## -1 14 36
## Accuracy: 69.318% (61 of 88)
## Balanced accuracy: 68.786% (25 of 39 and 36 of 49)
## Matthews CC: 0.377
## Sensitivity: 64.103% (25 of 39)
## Specificity: 73.469% (36 of 49)
## Precision: 65.789% (25 of 38)
```

We have an accuracy of 69% in the model here, which is okay; it is better than random. We have a smaller dataset and the model is not optimized; with more work, it could be better. Note that if you run the code, you might get different answers. Since the selection of training sequences is random, the models might do slightly worse or better, depending on the input data

In step 5, we estimate the prediction profile of a sequence. To find the regions that are important in classification, and presumably in the protein, we use the getPredictionProfile function on a sequence. We do this on a small 10 AA fragment extracted from the first sequence using list-double-bracket indexing to get the first sequence and single-bracket indexing to a range – for example, seqs [[1]] [1:10]. We do this to clarify the explanation and visualization in the last