The second stage is the stage of recognition. It consists of the following time-steps:

+   1. First, each symbol of a text document is selected.
+   2. The symbol with the help of the characteristic feature vector is described and its code is formed.
+   3. The resulting code is compared with the codes that are stored in the memory of the patterns.
+   4. If there is a code in the standard memory that matches the code at the input of the image recognition system, then the input image is recognised. If the pattern code is not founded in the standard memory, the input image of the symbol is not recognised.

This sequence of operations is used in almost all the methods, which have differences mainly in paragraphs 1 and 2 of sequence. There are other methods for selecting the characters in the text (Gonzalez and Woods, 2008; Epshtein et al., 2012; Chen and Yuille, 2004; Lienhart and Wernicke, 2002). These methods do not require implementation of complex algorithms. Also, there are a large number of methods that implement the operation of describing the selected symbol and forming the vector with characteristic features (Gonzalez and Woods, 2008; Chen and Yuille, 2004; Yan and Gao, 2012; González and Bergasa, 2013). Basically, these methods consist of finding characteristic points that distinguish each symbol from the others.

Also, the relationships between the selected characteristic elements of the symbol image are implemented. For example, for the symbol images shown in Fig. 8.36, the characteristic elements are indicated by the circles.

For each characteristic element of the symbol, various algorithms are used to search for them in the image. As can be seen in Fig. 8.36, such characteristic features include elements of intersection of segments, elements that refer to the edges of segments, etc. In this situation, the methods should take into account the thickness of the symbols, which leads to the use of skeletonisation methods for image symbols. This leads to an increase in the time spent on the formation of the vector of characteristic features of each symbol.

At the same time, all these methods are based on a preliminary visual analysis of the topology of each image of character. On the basis of this analysis, the characteristic features of each symbol are chosen. To this end,

![](bbox=[0.25, 0.77, 0.75, 0.83])

Fig. 8.36: Images of characters with selected characteristic elements for each symbol