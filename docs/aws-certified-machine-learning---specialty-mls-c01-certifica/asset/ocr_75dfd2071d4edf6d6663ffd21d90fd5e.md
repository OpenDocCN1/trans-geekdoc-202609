In a few chapters' time, you will also learn about some built-in AWS algorithms for NLP applications, such as BlazingText, **Latent Dirichlet Allocation (LDA)**, **Neural Topic Modeling (NTM)**, and the **Sequence-to-Sequence** algorithm. Those algorithms also let you create the same NLP solutions that are created by those out-of-the-box services; however, you have to use them on SageMaker and write your own solution. In other words, they offer more flexibility but demand more development effort.

Keep that in mind for your exam!

Although AWS offers many out-of-the-box services and built-in algorithms that allow you to create NLP applications, you will not look at those AWS product features now (you will do in **Chapter 6, Applying Machine Learning Algorithms**, and **Chapter 8, AWS Application Services for AI/ML**). You will finish this chapter by looking at some data preparation techniques that are extremely important for preparing your data for NLP.

# # Bag of words

The first one you will learn is known as bag of words (BoW). This is a very common and simple technique, applied to text data, that creates matrix representations to describe the number of words within the text. BoW consists of two main steps: creating a vocabulary and creating a representation of the presence of those known words from the vocabulary in the text. These steps can be seen in *Figure 4.11*.

| | this | movie | really | good | although | old | production |
|---|---|---|---|---|---|---|---|
| Binary | 1 | 1 | 1 | 1 | 1 | 1 | 1 |
| Frequency | 0.14 | 0.14 | 0.28 | 0.14 | 0.14 | 0.14 | 0.14 |
| Count | 1 | 1 | 2 | 1 | 1 | 1 | 1 |

Figure 4.11 – BoW in action

First things first, you usually can’t use raw text to prepare a BoW representation. There is a data cleansing step where you lowercase the text; split each work into tokens; remove punctuation, non-