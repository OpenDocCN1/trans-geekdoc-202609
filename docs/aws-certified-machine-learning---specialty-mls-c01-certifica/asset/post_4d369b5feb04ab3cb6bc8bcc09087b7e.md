
You should be aware that there are many alternatives to co-occurrence matrices with a fixed context window, such as using TF-IDF vectorization or even simpler counters of words per document. The most important message here is that, somehow, you must come up with a numerical representation for each word.

The last step is finally finding those dimensions shown in Table 4.13. You can do this by creating a multilayer model, usually based on neural networks, where the hidden layer will represent your embedding space. Figure 4.14 shows a simplified example where you could potentially compress those words shown in Figure 4.13 into an embedding space of five dimensions:

![](img/87c29232224b00f5a8bba6a66a391700_126_0.png)

Figure 4.14 – Building embedding spaces with neural networks

You will learn about neural networks in more detail later in this book. For now, understanding where the embedding vector comes from is already an awesome achievement!

Another important thing you should keep in mind while modeling natural language problems is that you can reuse a pre-trained embedding space in your models. Some companies have created modern neural network architectures, trained on billions of documents, which have become the state of the art in this field. For your reference, take a look at Bidirectional Encoder Representations from Transformers (BERT), which was proposed by Google and has been widely used by the data science community and industry.

You have now reached the end of this long – but very important – chapter about data preparation and transformation. Take this opportunity to do a quick recap of the awesome things you have learned.

## Summary

First, you were introduced to the different types of features that you might have to work with. Identifying the type of variable you’ll be working with is very important for defining the types of transformations and techniques that can be applied to each case.

Then, you learned how to deal with categorical features. You saw that, sometimes, categorical variables do have an order (such as the ordinal ones), while other times, they don’t (such as the nominal ones). You learned that one-hot encoding (or dummy variables) is probably the most common type of transformation for nominal features; however, depending on the number of unique categories, after applying one-hot encoding, your data might suffer from sparsity issues. Regarding ordinal features, you shouldn’t create dummy variables on top of them, since you would be losing the information about the order that has been incorporated into the variable. In those cases, ordinal encoding is the most appropriate transformation.

You continued your journey by looking at numerical features, where you learned how to deal with continuous and discrete data. You walked through the most important types of transformations, such as normalization, standardization, binning, and discretization. You saw that some types of transformation rely on the underlying data to find their parameters, so it is very important to avoid using the testing set to learn anything from the data (it must strictly be used only for testing).

You have also seen that you can even apply pure math to transform your data; for example, you learned that power transformations can be used to reduce the skewness of your feature and make it more similar to a normal distribution.

After that, you looked at missing data and got a sense of how important this task is. When you are modeling, you can’t look at the missing values as a simple computational problem, where you just have to replace x with y. This is a much bigger problem, and you need to start solving it by exploring your data and then checking whether your missing data was generated at random or not.

When you are making the decision to remove or replace missing data, you must be aware that you are either losing information or adding bias to the dataset, respectively. Remember to review all the important notes of this chapter, since they are likely to be relevant to your exam.

You also learned about outlier detection. You looked at different ways to find outliers, such as the z-score and box plot approaches. Most importantly, you learned that you can either flag or smooth them.

At the beginning, you were advised that this chapter would be a long but worthwhile journey about data preparation. You have also learned how to deal with rare events, since this is one of the most challenging problems in ML. Now you are aware that, sometimes, your data might be unbalanced, and you must either trick your algorithm (by changing the class weights) or resample your data (applying undersampling or oversampling).

Finally, you learned how to deal with text data for NLP. You should now be able to manually compute BoW and TF-IDF matrices! You went even deeper and learned how word embedding works. During this subsection, you learned that you can either create your own embedding space (using many different methods) or reuse a pre-trained one, such as BERT.

You are done! In the next chapter, you will dive into data visualization techniques.

## Exam Readiness Drill – Chapter Review Questions

Apart from a solid understanding of key concepts, being able to think quickly under time pressure is a skill that will help you ace your certification exam. That is why working on these skills early on in your learning journey is key.

Chapter review questions are designed to improve your test-taking skills progressively with each chapter you learn and review your understanding of key concepts in the chapter at the same time. You'll find these at the end of each chapter.

## HOW TO ACCESS THESE RESOURCES

To learn how to access these resources, head over to the chapter titled Chapter 11, Accessing the Online Practice Resources.

To open the Chapter Review Questions for this chapter, perform the following steps:

- 1. Click the link – https://packt.link/MLSC01E2_CH04.

Alternatively, you can scan the following QR code (Figure 4.15):

![](img/87c29232224b00f5a8bba6a66a391700_129_0.png)

Figure 4.15 – QR code that opens Chapter Review Questions for logged-in users

- 2. Once you log in, you'll see a page similar to the one shown in Figure 4.16:

## Data Preparation and Transformation

## Summary

First, you were introduced to the different types of features that you might have to work with. Identifying the type of variable you’ll be working with is very important for defining the types of transformations and techniques that can be applied to each case.

Then, you learned how to deal with categorical features. You saw that, sometimes, categorical variables do have an order (such as the ordinal ones), while other times, they don’t (such as the nominal ones). You learned that one-hot encoding (or dummy variables) is probably the most common type of transformation for nominal features; however, depending on the number of unique categories, after applying one-hot encoding, your data might suffer from sparsity issues. Regarding ordinal features, you shouldn’t create dummy variables on top of them, since you would be losing the information about the order that hadn’t been incorporated into the variable. In those cases, ordinal encoding is the most appropriate transformation.

You continued your journey by looking at numerical features, where you learned how to deal with continuous and discrete data. You walked through the most important types of transformations, such as normalization, standardization, binning, and discretization. You saw that some types of transformation rely on the underlying data to find their parameters, so it is very important to avoid using the testing set to learn anything from the data (it must strictly be used only for testing).

You have also seen that you can even apply pure math to transform your data; for example, you learned that power transformations can be used to reduce the skewness of your feature and make it more similar to a normal distribution.

After that, you looked at missing data and got a sense of how important this task is. When you are modelling, you can’t look at the missing values as a simple computational problem, where you just have to replace x with y. This is a much bigger problem, and you need to start solving it by exploring your data and then checking whether your missing data was generated at random or not.

When you are making the decision to remove or replace missing data, you must be aware that you are either losing information or adding bias to the dataset, respectively. Remember to review all the important notes of this chapter, since they are likely to be relevant to your exam.

You also learned about outlier detection. You looked at different ways to find outliers, such as the z-score and box plot approaches. Most importantly, you learned that you can either flag or smooth them.

At the beginning, you were advised that this chapter would be a long but worthwhile journey about data preparation. You have also learned how to deal with rare events, since this is one of the most challenging problems in ML. Now you are aware that, sometimes, your data might be unbalanced, and you must either trick your algorithm (by changing the class weights) or resample your data (applying undersampling or oversampling).

Finally, you learned how to deal with text data for NLP. You should now be able to manually compute BoW and TF-IDF matrices! You went even deeper and learned how word embedding works. During this subsection, you learned that you can either create your own embedding space (using many different methods) or reuse a pre-trained one, such as BERT.

You are done! In the next chapter, you will dive into data visualization techniques.

## Chapter Review Questions

The AWS Certified Machine Learning - Specialty (MLS-C01) Certification Guide - Second Edition by Samarth Nanda, Wesley Moura

Select Quiz
Quiz 1 SHOW QUIZ DETAILS START

Figure 4.16 — Chapter Review Questions for Chapter 4

- 3. Once ready, start the following practice drills, re-attempting the quiz multiple times.

## Exam Readiness Drill

### ATTEMPT 1

The first time, aim for at least 40%. Look at the answers you got wrong and read the relevant sections in the chapter again to fix your learning gaps.
