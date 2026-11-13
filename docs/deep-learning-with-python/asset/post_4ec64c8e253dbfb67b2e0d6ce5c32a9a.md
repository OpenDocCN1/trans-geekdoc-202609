
## 14 Conclusions

- This chapter covers
- Important takeaways from this book
- The limitations of deep learning
- Possible future directions for deep learning, machine learning, and AI
- Resources for further learning and applying your skills in practice

You've almost reached the end of this book. This last chapter will summarize and review core concepts while also expanding your horizons beyond what you've learned so far. Becoming an effective AI practitioner is a journey, and finishing this book is merely your first step on it. I want to make sure you realize this and are properly equipped to take the next steps of this journey on your own.

We'll start with a bird's-eye view of what you should take away from this book. This should refresh your memory regarding some of the concepts you've learned. Next, I'll present an overview of some key limitations of deep learning. To use a tool appropriately, you should not only understand what it *can* do but also be aware of what it *can't* do. Finally, I'll offer some speculative thoughts about the future evolution of deep learning, machine learning, and AI. This should be especially interesting to you if you'd like to get into fundamental research. The chapter ends with a short list of resources and strategies for further learning about machine learning and staying up to date with new advances.

## 14.1 Key concepts in review

This section briefly synthesizes key takeaways from this book. If you ever need a quick refresher to help you recall what you've learned, you can read these few pages.

### 14.1.1 Various approaches to AI

First of all, deep learning isn't synonymous with AI, or even with machine learning:

- Artificial intelligence (AI) is an ancient, broad field that can generally be understood as "all attempts to automate human cognitive processes." This can range from the very basic, such as an Excel spreadsheet, to the very advanced, like a humanoid robot that can walk and talk.

- Machine learning is a specific subfield of AI that aims at automatically developing programs (called _models_) purely from exposure to training data. This process of turning data into a program is called _learning_. Although machine learning has been around for a long time, it only started to take off in the 1990s, before becoming the dominant form of AI in the 2000s.

- Deep learning is one of many branches of machine learning, where the models are long chains of geometric transformations, applied one after the other. These operations are structured into modules called _layers_: deep learning models are typically stacks of layers—or, more generally, graphs of layers. These layers are parameterized by _weights_, which are the parameters learned during training. The knowledge of a model is stored in its weights, and the process of learning consists of finding "good values" for these weights—values that minimize a _loss function_. Because the chain of geometric transformations considered is differentiable, updating the weights to minimize the loss function is done efficiently via _gradient descent_.

Even though deep learning is just one among many approaches to machine learning, it isn't on an equal footing with the others. Deep learning is a breakout success. Here's why.

### 14.1.2 What makes deep learning special within the field of machine learning

In the span of only a few years, deep learning has achieved tremendous breakthroughs across a wide range of tasks that have been historically perceived as extremely difficult for computers, especially in the area of machine perception: extracting useful information from images, videos, sound, and more. Given sufficient training data (in particular, training data appropriately labeled by humans), deep learning makes it possible to extract from perceptual data almost anything a human could. Hence, it's sometimes said that deep learning has "solved perception"—although that's true only for a fairly narrow definition of perception.

Due to its unprecedented technical successes, deep learning has singlehandedly brought about the third and by far the largest AI summer: a period of intense interest, investment, and hype in the field of AI. As this book is being written, we're in the middle of it. Whether this period will end in the near future, and what happens after it ends, are topics of debate. One thing is certain: in stark contrast with previous AI summers, deep learning has provided enormous business value to both large and small technology companies, enabling human-level speech recognition, smart assistants, human-level image classification, vastly improved machine translation, and more. The hype may (and likely will) recede, but the sustained economic and technological impact of deep learning will remain. In that sense, deep learning could be analogous to the internet: it may be overly hyped up for a few years, but in the longer term it will still be a major revolution that will transform our economy and our lives.

I'm particularly optimistic about deep learning, because even if we were to make no further technological progress in the next decade, deploying existing algorithms to every applicable problem would be a game changer for most industries. Deep learning is nothing short of a revolution, and progress is currently happening at an incredibly fast rate, due to an exponential investment in resources and headcount. From where I stand, the future looks bright, although short-term expectations are somewhat overoptimistic; deploying deep learning to the full extent of its potential will likely take multiple decades.

### 14.1.3 How to think about deep learning

The most surprising thing about deep learning is how simple it is. Ten years ago, no one expected that we would achieve such amazing results on machine-perception problems by using simple parametric models trained with gradient descent. Now, it turns out that all you need is sufficiently large parametric models trained with gradient descent on sufficiently many examples. As Feynman once said about the universe, "It's not complicated, it's just a lot of it."¹

In deep learning, everything is a vector—that is to say, everything is a point in a geometric space. Model inputs (text, images, and so on) and targets are first vectorized—turned into an initial input vector space and target vector space. Each layer in a deep learning model operates one simple geometric transformation on the data that goes through it. Together, the chain of layers in the model forms one complex geometric transformation, broken down into a series of simple ones. This complex transformation attempts to map the input space to the target space, one point at a time. This transformation is parameterized by the weights of the layers, which are iteratively updated based on how well the model is currently performing. A key characteristic of this geometric transformation is that it must be differentiable, which is required in order

for us to be able to learn its parameters via gradient descent. Intuitively, this means the geometric morphing from inputs to outputs must be smooth and continuous—a significant constraint.

The entire process of applying this complex geometric transformation to the input data can be visualized in 3D by imagining a person trying to uncrumple a paper ball: the crumpled paper ball is the manifold of the input data that the model starts with. Each movement operated by the person on the paper ball is similar to a simple geometric transformation operated by one layer. The full uncrumpling gesture sequence is the complex transformation of the entire model. Deep learning models are mathematical machines for uncrumpling complicated manifolds of high-dimensional data.

That's the magic of deep learning: turning meaning into vectors, then into geometric spaces, and then incrementally learning complex geometric transformations that map one space to another. All you need are spaces of sufficiently high dimensionality in order to capture the full scope of the relationships found in the original data.

The whole process hinges on a single core idea: that meaning is derived from the pairwise relationship between things (between words in a language, between pixels in an image, and so on) and that these relationships can be captured by a distance function. But note that whether the brain also implements meaning via geometric spaces is an entirely separate question. Vector spaces are efficient to work with from a computational standpoint, but different data structures for intelligence can easily be envisioned—in particular, graphs. Neural networks initially emerged from the idea of using graphs as a way to encode meaning, which is why they're named neural networks; the surrounding field of research used to be called connectionism. Nowadays the name "neural network" exists purely for historical reasons—it's an extremely misleading name because they're neither neural nor networks. In particular, neural networks have hardly anything to do with the brain. A more appropriate name would have been layered representations learning or hierarchical representations learning, or maybe even deep differentiable models or chained geometric transforms, to emphasize the fact that continuous geometric space manipulation is at their core.

### 14.1.4 Key enabling technologies

The technological revolution that's currently unfolding didn't start with any single breakthrough invention. Rather, like any other revolution, it's the product of a vast accumulation of enabling factors—gradual at first, and then sudden. In the case of deep learning, we can point out the following key factors:

- Incremental algorithmic innovations—These first began appearing slowly over the span of two decades (starting with backpropagation), and then were developed increasingly faster as more research effort was poured into deep learning after 2012.

- The availability of large amounts of perceptual data—This was a requirement in order to realize that sufficiently large models trained on sufficiently large data
