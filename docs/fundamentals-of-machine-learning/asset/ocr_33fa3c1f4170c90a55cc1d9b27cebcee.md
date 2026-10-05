# 3.5 Decision trees and random forests

As stressed at the beginning of this chapter, our main aim here was to show that applying machine learning methods is made fairly easy with application packages like sklearn, one still needs to know how to use techniques like hyperparameter tuning and balancing data to make effective use of them. In the next two sections we want to explain some of the ideas behind the specific models implemented by the random forest classifier (RPF) and the support vector machine (SVM). This is followed in the next chapter by descriptions of neural networks. The next two section are optional in the sense that following the theory behind really require knowledge of additional mathematical concepts that are beyond our introductory treatment in this book. Instead, the main focus here is to give a glimpse of the deep thoughts behind algorithms and to encourage the interested reader to engage with further studies. The asterisk in section headings indicates that those sections are not necessary reading to follow the rest of this book.

We have already used a random forest classifier (RFC), and this method is a popular choice where deep learning has not yet made an impact. It is worthy to outline the concepts behind it itself since it is an example of a non-parametric machine learning method. The reason is that the structure of the model is defined by the training data and not conjured at the beginning by the investigator. This fact alone helps the use of this method and explain some of its popularity, although there are additional factors that make it competitive such as the ability to build in feature selection. We will briefly outline what is behind this method. A random forest is actually an ensemble method of decision trees, so we will start by explaining what a decision tree is.

![](bbox=[0.265, 0.555, 0.702, 0.68])

**Fig. 3.7** Example data of two classes with black and white discs and a corresponding decision tree classification on the right.

Us consider the training data

```
$D_{train} = \{(x^{(i)}, y)\},
```

where the attribute vector has $N_t$ components. For example, the data on the left in Fig. 3 has two attributes called $x_1$ and $x_2$. The algorithm calculates how to split the data iteratively by considering which attribute could classify the training data set at this level of a decision point. If we split the data along the vertical dashed line, then we can already classify a large number of data correctly. We can split the remaining data using the second attribute.