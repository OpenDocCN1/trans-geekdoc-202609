# Processing Information 533

to work within such a framework, where we do not have features as we have been using today.

The missing piece we have to establish is a way to compare two features. Imagine we have a corpus of paragraphs of a text. For every paragraph, we have a particular property, say class. When we are provided with a new paragraph which is out-of-sample, our goal is to predict the class. In a simple case, the problem can be that we have onehalf all the paragraphs in English (class of a paragraph) and the second half of the paragraphs written in Latin. Then, the comparison of two paragraphs will be based on matching words and counting the number of matching words. We thus define a kernel of matching words and employ a method which can utilize kernels.

In the subsequent paragraphs, we introduce a sample data set and explain how we can use the kernel methods for classification. We implement the explained methods afterwards.

# 27.2.1 Sample: Simulated Proteins

We want to illustrate our method on the data. The nice and realistic subset for the algorithm we introduce is a frequent problem in biomedicine, which is a comparison of proteins. For our exercise, the protein is characterised as a sequence of amino acids. We further consider the existence of 20 amino acids, which might contribute to the formation of any protein. Since the number of different amino acids is less than a number of characters in the alphabet, we represent each amino acid by an upper case letter, A,B,C.... Protein can be naturally represented as a sequence of letters, where the ordering of the individual amino acids matters; i.e. AB and BA represent two simple different proteins. Further, proteins main not have necessarily the same number of amino acids.

Let us illustrate the proteins in practice. We will use synthetic data and create our sample. The protein is an array of characters of a given length. The example of such a protein reads:

```
protein="ABDQLQEKBEGLE";
```

The advantage of this representation is that we can uniquely convert an array of characters into an array of integers using the ASCII table. Namely, we can cast between characters and ASCII representation as follows:

```
"I" = "A"
```

```
651
```

```
and back
```

```
"c" = 65
```

```
"A"
```