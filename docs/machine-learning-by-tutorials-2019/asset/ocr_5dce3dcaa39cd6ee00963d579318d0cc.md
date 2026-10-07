# Machine Learning
Chapter 4: Getting Started with Python & Turi

Next, run this command to evaluate the model and collect metrics:

```
metrics = model.evaluate(test_data)
```

Unlike Create ML, the output of this command doesn't show any accuracy figures — you need to examine metrics. Run these commands in the same cell:

```
print("Accuracy: ", metrics["accuracy"])
print("Precision: ", metrics["precision"])
print("Recall: ", metrics["recall"])
print("Confusion Matrix: \", metrics["confusion_matrix"])
```

Here are my metrics:

| target_label | predicted_label | count |
|---|---|---|
| ice cream | candy | 1 |
| apple | banana | 3 |
| orange | pineapple | 2 |
| apple | strawberry | 1 |
| pineapple | banana | 2 |
| strawberry | salad | 1 |
| popcorn | waffle | 1 |
| carrot | salad | 2 |
| orange | watermelon | 1 |
| popcorn | popcorn | 36 |

[107 rows x3 columns]
Note: The head of the SFrame is printed.
You can use print_rows(num_rows=m, num_columns=n) to print more rows and columns.

No surprises; accuracy, precision and recall are all similar to the final validation accuracy of the model. Unlike Create ML, Turi Create gives overall values for precision and recall, and you will need some code to get precision and recall for each class. In the next chapter, you'll learn how to get recall for each class.

The confusion matrix shows only the first 10 rows: the model mistook one "ice cream" image for "candy," three "apple" images for "banana," etc. Presented this way, it doesn't look much like a matrix.