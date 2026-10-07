# # Chapter 15: Natural Language Transformation, Part 1

By Chris LaPollo

**Update Note:** Apple loves to keep us waiting. As of writing, the CoreML APIs needed to update this chapter weren't quite ready. As Apple releases new APIs, we'll continue to update this chapter. We'll also notify you and let you know how to access the updated versions.

The previous chapter showed how to use Apple's Natural Language framework to perform some useful NLP tasks. But Apple only covers the basics — there are many other things you might like to do with natural language. For example, you might answer questions, summarize documents or translate between languages.

In this chapter, you will learn about a versatile network architecture called **sequence-to-sequence (seq2seq)** model. You'll add one to the SMDB app you already built, using it to translate movie reviews from Spanish to English, but the same network design has been used for many types of problems, from question answering to generating image captions. Don't worry if you didn't already make SMDB — we provide a starter project if you need it. But you can forget about Xcode for a while — seq2Seq models require a lower-level framework, so you'll work with Python and Keras for most of this chapter.

# # Getting Started

Some of the Keras code in this project was initially based on the example found in the file **lstm_seq2seq.py** inside the Keras GitHub repository [github.com/keras-team/keras]. This chapter makes stylistic modifications, explains and expands