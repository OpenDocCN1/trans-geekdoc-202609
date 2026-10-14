
# Natural Language Processing in Python

Master Data Science and Machine Learning for spam detection, sentiment analysis, latent semantic analysis, and article spinning

By: The LazyProgrammer ([http://lazyprogrammer.me](http://lazyprogrammer.me))

- [Introduction](../Text/part0001.html#UGI1-409c51404c584781914e8a398e53e48b)
- [Chapter 1: What is NLP all about?](../Text/part0002.html#chapter-2)
- [Chapter 2: Common NLP operations](../Text/part0003.html#2RHM1-409c51404c584781914e8a398e53e48b)
- [Chapter 3: Build your own spam detector](../Text/part0004.html#3Q281-409c51404c584781914e8a398e53e48b)
- [Chapter 4: Build your own sentiment analysis tool](../Text/part0005.html#chapter-5)
- [Chapter 5: Exploration of NLTK](../Text/part0006.html#chapter-6)
- [Chapter 6: Latent Semantic Analysis](../Text/part0007.html#chapter-7)
- [Chapter 7: Build your own article spinner](../Text/part0008.html#chapter-8)
- [Conclusion](../Text/part0009.html#chapter-9)

# Introduction

Recently, Microsoft’s Twitter bot “Tay” was released into the wild, and quickly began making racist and hateful statements after learning from other Twitter users. The technology behind this? Natural language processing.

Natural language processing is the use of machine learning algorithms for problems that involve text.

This is one of the most important problems of our day because a lot of the Internet is made up of text. With NLP, we can analyze it, understand it, categorize it, and summarize it - and do it all automatically.

Do you ever wonder why you get much less spam in your inbox these days compared to 10 years ago? What kinds of algorithms are people using to do spam detection? How can they take words in an email and know how to compute whether or not it’s spam? In this book you are going to build your very own spam detector.

Did you know people have already used Twitter to determine the current sentiment about a particular company to decide whether or not they should buy or sell stocks? Having a machine that can decide how people feel about something is immensely useful and immediately applicable to revenue optimization. In this course you are going to build your own sentiment analyzer.

Are you an Internet marketer or are you interested in SEO? Have you ever wanted to know how you can automatically generate content? In this course we are going to take a first crack at building your own article spinner. You’ll learn to write programs that can take an article as input and spit out a similar article with different words as output. This can save you tons of time and thousands of dollars if you’re paying someone to write content for you.

Natural Language Processing, or as it is often abbreviated, NLP - is the use of programming and math to do language-based tasks.

If you have Windows or iOS then you have NLP right in front of you! Cortana and Siri are applications that take what you say and turn it into something meaningful that can be done programmatically.

The key point: NLP is highly practical. NLP is everywhere.

This book is split up into multiple sections based on the various practical tasks that you can do with NLP:

Before we do any real programming exercises we’ll look at common NLP tasks (some of these we will actually code ourselves, the others are mentioned so you at least know they exist). We will then look at common data pre-processing techniques used for text. As you’ll see, this preprocessing is what will actually take up a majority of your time when you’re doing NLP.

The first programming exercise we’ll do is look at how to build a spam detector. Your email inbox uses this, so it’s clearly very useful and it’s been the subject of study for a long time.

Next we’ll look at “sentiment analysis” and you’ll build your own “sentiment analyzer”. This is how a computer can judge how positive or negative some text is based on the words and phrases that are used. This is also immediately practical - some people have analyzed Twitter feeds to predict whether a stock would go up or down.

After that we’ll look at the `NLTK` library. This is a very popular library that solves a lot of fundamental problems in NLP - and you can use it in conjunction with other libraries in your data analysis pipeline.

Next we’ll look at “latent semantic analysis”. This is basically doing dimensionality reduction on text - and it helps us solve the problem of 2 words having the same meaning. It also helps us interpret our data and save on computation time.

Lastly, we’ll talk about one of the most popular applications of NLP - article spinning. This is very practical for internet marketers and entrepreneurs. As you know, your search rankings in Google and other search engines are affected negatively when you have duplicate content - so it would be great if you could alter an article you wrote just enough, so that you could put it in 2 different places on the web, without being penalized by Google.

This book requires a minimal amount of math to understand. If there is math, it’s for your own interest only, but it’s not vital to completing the programming parts. Of course, you will still need to know how to code, since NLP is primarily in the domain of programming, but I’ve designed this book to require a lot less math than some of my other books on deep learning and neural networks.

All of the materials required to follow along with this book can be downloaded for FREE. We use `Python`, `NLTK`, `Sci-kit learn`, and `Numpy`, all of which can be installed using simple commands.

# Chapter 1: What is NLP all about?

Since NLP is really just the application of machine learning and software engineering to text and language problems, I think it’s very important in this case to talk about - what are these applications? And how are they useful in real life?

In this chapter I’m going to go through some real applications of NLP and talk about how good we are at solving these problems with current technology. A lot of this book is going to skip over the theory and instead we’ll talk about, “how can we code up our own solutions to these NLP problems using existing libraries?” We’ll go through a few problems where the state of the art is very good, then we’ll go through some problems where the state of the art is just pretty good but not excellent, and then we’ll go through some problems where the state of the art “kind of works” but there is definitely room for improvement.

Here are some problems that we are currently very good at solving:

## Spam detection

I almost never get spam anymore in my email. Gmail even has algorithms that can split up your data into different tabs, such as the “social” tab for social media related posts, and the “promotions” tab for marketing emails.

## Parts of speech (POS) tagging

We want to know which terms in a sentence are adverbs, adjectives, nouns, pronouns, verbs, and so on. We are very good at classifying these.

**Input:**

> “The quick brown fox jumps over the lazy dog.”

**Output:**

> (Determiner, adjective, adjective, noun, plural noun, …)

There are many online tools out there that can demonstrate this, for example: [http://parts-of-speech.info/](http://parts-of-speech.info/)

## Named entity recognition (NER)

**Input:** “Jim bought 300 shares of Apple in 2006.”

We want to be able to recognize that “Jim” is a person, “Apple” is an organization, and “2006” is a date.

There are some problems that we are pretty good at but not great at:

## Sentiment analysis

This is something we’re going to cover in this course. Let’s say you’re looking at hotel reviews on the web, and you want to know if overall, people think this hotel is good or bad. Well you can do this by reading the reviews yourself - but if we want the machine to assign a positive or negative score, it’s not that simple. One problem (among many others) is that machines can’t easily detect sarcasm. So if you say something where the words mean the opposite of their true definition, then this will confuse the machine.
