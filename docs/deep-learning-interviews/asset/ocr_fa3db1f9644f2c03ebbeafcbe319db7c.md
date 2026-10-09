![](bbox=[0.31, 0.09, 0.71, 0.25])

**FIGURE 7.7:** Skin lesion categories. An exemplary visualization of melanoma .

+   1. *Given that the skin lesions fall into seven distinct categories, and you are training using cross-entropy loss, how should the classes be represented so that a typical PyTorch training loop will successfully converge?*

+   2. *Suggest several data augmentation techniques to augment the data . .*

+   3. *Write a code snippet in PyTorch to adapt the CNN so that it can . predict 7 classes instead of the original source size of 1000."

+   4. *In order to fine tune our CNN, the (original) output layer with 1000 classes was removed and the CNN was adjusted so that the (new) classification layer comprised seven softmax neurons emitting posterior probabilities of class membership for each lesion type . .*

# 7.2.3 Neural style transfer, NST

Before attempting the problems in the section, you are strongly recommended to read the paper: "*A Neural Algorithm of Artistic Style* " [2] .

> **PRB-172** CH.PR B- 7.16.

*  Briefly describe how neural style transfer (NST) [ 2 ] works . *

> **PRB-173** CH.PR B- 7.17.