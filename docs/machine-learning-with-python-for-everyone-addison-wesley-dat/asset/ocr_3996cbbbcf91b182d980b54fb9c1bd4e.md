Here’s a reminder of the confusion matrix entries:

|  | PredP | PredN |
|---|---|---|
| RealP | TP | FN |
| RealN | FP | TN |

Hopefully, some of you are raising an eyebrow. You might recall the old adages, “There’s no such thing as a free lunch,” or “You get what you pay for,” or “You don’t get something for nothing.” In fact, if you raised an eyebrow, you were wise to be skeptical. Take a closer look at the bottom row of the confusion matrix. The row has the examples which are real negatives. By moving the prediction bar all the way to the right, we’ve emptied out the true negative bucket by pushing all of its contents to the false positive bucket. Every real negative is now a false positive! By predicting everything PredP, we do great on real positives and horrible on real negatives.

You can imagine a corresponding scenario by moving the PredictionBar all the way to the left. Now, there are no PredP. Everything is a predicted negative. For the top row—real positives—it is a disaster! At least things are looking better in the bottom row: all of those real negatives are correctly predicted negative—they are true negatives. You might be wondering: what is an equivalent setup with a horizontal bar between real positives and real negatives? It’s sort of a trick question—there isn’t one. For the sorts of data we are discussing, a particular example can’t go from being real positive to real negative. Real cats can’t become real dogs. Our predictions can change; reality can’t. So, it doesn’t make sense to talk about moving that line.

You may be sensing a pattern by now. In learning systems, there are often tradeoffs that must be made. Here, the tradeoff is between how many false positives we will tolerate versus how many false negatives we will tolerate. We can control this tradeoff by moving our prediction bar, by setting a threshold. We can be hyper-risk-averse and label everyone sick so we don’t miss catching a sick person. Or, we can be penny-pinchers and label everyone healthy, so we don’t have to treat anyone. Either way, there are two questions:

+   1. How do we evaluate and select our threshold? How do we pick a specific tradeoffs between false positives and false negatives?
+   2. How do we compare two different classification systems, both of which have a whole range of possible tradeoffs?

Fortunately, there is a nice graphical tool that lets us answer these questions: the ROC curve. The ROC curve—or, with its very, very long-winded name, the Receiver Operating Characteristic curve—has a long history in classification. It was originally used to quantify radar tracking of bombers headed towards England during World War II. This task was, perhaps, slightly more important than our classification of irises. Regardless, they needed to determine whether a blip on the radar screen was a real threat (a bomber) or not (a ghosted echo of a plane or a bird): to tell true positives from false positives.