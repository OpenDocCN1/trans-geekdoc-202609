
So, machine learning has been around for a while. But that doesn't mean you've missed the boat. On the contrary, the reason it's become such a hot topic recently is that machine learning works best when there is a lot of data — thanks to the internet and smartphones, there is now more data than ever. Moreover, computing power has become much cheaper.

It took for it to catch on, but machine learning has grown into a practical tool for solving real-world problems that were too complex to deal with.

What is new, and why we've written this book, is that mobile devices are now powerful enough to run machine-learning algorithms right in the palm of your hand!

## Learning without explicit programming

So exactly do we mean when we say, "machine learning"?

As a programmer, you're used to writing code that tells the computer exactly what to do in any situation. A lot of this code consists of rules:

```
if this is true,
then do something,
else do another thing
```

This is pretty how software has always been written. Different programmers use different languages, but they're essentially writing long lists of instructions for the computer to perform. And this works very well for a lot of software, which is why it's a popular approach.

Writing out-then-else rules works well for automating repetitive tasks that most people find boring or that require long periods of concentration. It's possible, though time-consuming, to feed a computer a lot of knowledge in the form of such rules, then program it to mimic what people do consciously, to reason logically with the rules or knowledge, or to apply heuristics, meaning rules or thumb.

But there are also interesting problems in which it's hard to come up with a suitable set of rules or in which heuristics are too crude — this is where machine learning can help. It is very hard to explicitly program computers the kinds of things most people do without conscious thought: recognizing faces, expressions and emotions, the shape of objects, or the sense or style of sentences. It's hard to write down the algorithms for these tasks: What is it that the human brain actually does to accomplish these tasks?

Machine Learning
Chapter 1: Machine Learning, iOS & You

How would you write down rules to recognize a face in a photo? You could look at the RGB values of pixels to describe their hair, skin or eye color, but this isn’t very reliable. Moreover, a person’s appearance — hair style, makeup, glasses, etc. — can change significantly between photos. Often people won't be looking straight at the camera, so you'd have to account for many different camera angles. And so on... You'd end up with hundreds, if thousands, of rules, and they still wouldn't cover all situations.

How do you recognize you as you and not a sibling or relative who resembles you? How do you explain how to distinguish cats from dogs to a small child, if you have only photos? What rules differentiate between cat and dog faces? Dogs and cats come in many different colors and hair lengths and tail shapes. For every rule you think of, there will probably be a lot of exceptions.

The big idea behind machine learning is that, if you can't write the exact steps for a computer to recognize objects in an image or the sentiment expressed by some text, maybe you can write a program that produces the algorithm for you.

Instead of having a domain expert design and implement if-then-else rules, you can let the computer learn the rules to solve these kinds of problems from examples. And that's what machine learning is: using a learning algorithm that can automatically derive the “rules” that are needed to solve a certain problem. Often, such an automated learner comes up with better rules than humans can, because it can find patterns in the data that humans don't.

## Deep learning

Until now, we've been using terms like deep learning and neural networks pretty literally. Let's take a moment to properly define what these terms mean.

Neural networks are made up of layers (neurons) in an attempt to mimic how the human brain works. For a long time, this was mostly theoretical: only simple neural networks with a couple of layers could be computed in a reasonable time with the computers of that era. In addition, there were problems with the math, and networks with more and larger layers didn't work well.

It took until the mid-2000s for computer scientists to figure out how to train really deep networks consisting of many layers. At the same time, the market for computer game devices exploded, spurring demand for faster, cheaper GPUs to run ever more elaborate games.

![](img/5720be5c3cca252e12448e68d25607b5_23_0.png)

## Machine Learning
Chapter 1: Machine Learning, iOS & You

GPUs (Graphics Processing Units), speed up graphics and are great at doing lots of matrix operations very fast. As it happens, neural networks also require lots of matrix operations.

Thanks to gamers, fast GPUs became very affordable, and that's exactly the sort of hardware needed to train deep multi-layer neural networks. Some of the most exciting progress in machine learning is driven by deep learning, which uses neural networks with a large number of layers, and a large number of neurons at each layer, as its learning algorithm.

> Note: Companies like Apple, Intel and Google are designing processing units specifically designed for deep learning, such as Google's TPU, or Tensor Processing Unit, and the new Neural Engine in the iPhone XS's A12 processor. These lack the 3D rendering capabilities of GPUs but instead can run the computational needs of the neural networks more efficiently.

![](img/5720be5c3cca252e12448e68d25607b5_24_0.png)

The deeper the network, the more complex the things are that you can make it. Thanks to deep learning, modern machine-learning models can solve more difficult problems than ever—including what is in images, recognizing speech, understanding language and much more. Research into deep learning is still on-going and new discoveries are being made all the time.

> Note: NVIDIA made its name as a computer game chip maker; now, it's also a machine-learning chip maker. Even though most tools for training models will work on macOS, they're more typically used on Linux running on a PC. The only GPUs these tools support are from NVIDIA, and most Macs don't

Machine Learning
Chapter 1: Machine Learning, iOS & You

> NVIDIA chips, GPU-accelerated training on newer Macs now possible with Apple’s own tools, but if you want the best speed and the most flexibility, you’ll still need a Linux machine. Frankly, you can run such machines in the cloud. For this book, you can run most of the training code on your Mac, although sometimes you'll have to be a little patient. We also provide the trained models for download, so you can skip the wait.

## Artificial intelligence

A term that gets thrown in a lot with machine learning is *artificial intelligence*, or AI, a field of research that got started in the 1950s with computer programs that could play checkers, solve algebra problems and more.

The goal of artificial intelligence is to simulate certain aspects of human intelligence using machines. A famous example from AI is the Turing test: *If a human cannot distinguish responses from a machine and a human, the machine is intelligent.*

AI is a very broad field, with researchers from many different backgrounds, including computer science, mathematics, psychology, linguistics, economics and philosophy. There are many subfields, such as computer vision and robotics, as well as different approaches and tools, including statistics, probability, optimization, logic programming and knowledge representation.

Learning is certainly something we associate with intelligence, but it goes too far to say that all machine-learning systems are intelligent. There is definitely overlap between the two fields, but machine learning is just one of the tools used by you. Not AI is machine learning — and not all machine learning is AI.

Machine learning also has many things in common with statistics and *data science*, a fancy term for doing statistics on computers. A data scientist might use learning to do her job, and many machine learning algorithms originally come from statistics. Everything is a remix.

## What can you do with machine learning?

Here are some of the things researchers and companies are doing with machine learning today:

+   - Predict how much shoppers will spend in a store.
- Assisted driving and self-driving cars.
