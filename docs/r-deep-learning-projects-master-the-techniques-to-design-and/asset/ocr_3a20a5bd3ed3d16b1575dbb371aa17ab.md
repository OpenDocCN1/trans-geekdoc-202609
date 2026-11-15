By design, recurrent neural networks are well-suited for processing sequential data. In general, machine learning applied to sequential data can be roughly divided into four main areas:

+   • Sequence prediction: Given \([x_{t-2}, x_{t-1}, x_t]\), predict the next element of the sequence, \(x_{t+1}\)
+   
+   • Sequence classification: Given \([x_{t-2}, x_{t-1}, x_t]\), predict a category or label for it
+   
+   • Sequence generation: Given \([x_{t-2}, x_{t-1}, x_t]\), generate a new element of the sequence, \(x_{t+1}\)
+   
+   • Sequence to sequence prediction: Given \([x_{t-2}, x_{t-1}, x_t]\), generate an equivalent sequence, \([y_{t-1}, y_t, y_{t+1}]\)

Applications of sequence prediction include weather forecasting and stock market prediction. For classification, we can think, for example, of sentiment analysis and document classification. Automatic image captioning or text generation are part of the sequence generation family of problems, whereas machine translation might be the most familiar example of sequence to sequence prediction we see in our everyday lives.

Our focus for this chapter is on applications of recurrent neural networks for text generation. Since, as we saw previously, text generation is part of a much larger set of problems, many of our algorithms are portable to other contexts.

Training deep learning models is often time-consuming, and recurrent neural networks are not the exception. Our focus is on the ideas over the data, which we will illustrate with smaller datasets than those that you might encounter later on in the wild. This is for the purpose of clarity: We want to make it easier for you to get started on any standard laptop. Once you grasp the basics, you can spin off your own cluster in your favorite cloud provider.

# # What is so exciting about recurrent neural networks?

Coming from a mathematics background, in my rather hectic career I have seen many different trends, particularly during the last few years, which all sound very similar to me: "you have a problem? wavelets can save you!", "finite elements are the solution to everything", and similar over-enthusiastic claims.