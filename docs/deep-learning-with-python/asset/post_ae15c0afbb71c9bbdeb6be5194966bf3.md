
you're relying heavily on value-centric analogies. If you're watching a movie and you start subconsciously categorizing the different characters into "types," that's value-centric abstraction.

## PROGRAM-CENTRIC ANALOGY

Crucially, there's more to cognition than the kind of immediate, approximative, intuitive categorization that value-centric analogy enables. There's another type of abstraction-generation mechanism that's slower, exact, deliberate: program-centric (or structure-centric) analogy.

In software engineering, you often write different functions or classes that seem to have a lot in common. When you notice these redundancies, you start asking, "could there be a more abstract function that performs the same job, that could be reused twice? Could there be an abstract base class that both of my classes could inherit from?" The definition of abstraction you're using here corresponds to program-centric analogy. You're not trying to compare your classes and functions by how similar they look, the way you'd compare two human faces, via an implicit distance function. Rather, you're interested in whether there are parts of them that have exactly the same structure. You're looking for what is called a subgraph isomorphism (see figure 14.10): programs can be represented as graphs of operators, and you're trying to find subgraphs (program subsets) that are exactly shared across your different programs.

![](img/ab452ecf572a1f1372915be13bd8088f_481_0.png)

Figure 14.10 Program-centric analogy identifies and isolates isomorphic substructures across different instances

This kind of analogy-making via exact structural match within different discrete structures isn't at all exclusive to specialized fields like computer science or mathematics—you're constantly using it without noticing. It underlies reasoning, planning, and the general concept of *rigor* (as opposed to intuition). Any time you're thinking about objects connected to each other by a discrete network of relationships (rather than a continuous similarity function), you're leveraging program-centric analogies.

## COGNITION AS A COMBINATION OF BOTH KINDS OF ABSTRACTION

Let's compare these two poles of abstraction side by side (see table 14.1).

Table 14.1 The two poles of abstraction

| Value-centric abstraction | Program-centric abstraction |
| :--- | :--- |
| Relates things by distance | Relates things by exact structural match |
| Continuous, grounded in geometry | Discrete, grounded in topology |
| Produces abstractions by "averaging" instances into "prototypes" | Produces abstractions by isolating isomorphic substructures across instances |
| Underlies perception and intuition | Underlies reasoning and planning |
| Immediate, fuzzy, approximative | Slow, exact, rigorous |
| Requires a lot of experience to produce reliable results | Experience-efficient, can operate on as few as two instances |

Everything we do, everything we think, is a combination of these two types of abstraction. You'd be hard-pressed to find tasks that only involve one of the two. Even a seemingly "pure perception" task, like recognizing objects in a scene, involves a fair amount of implicit reasoning about the relationships between the objects you're looking at. And even a seemingly "pure reasoning" task, like finding the proof of a mathematical theorem, involves a good amount of intuition. When a mathematician puts their pen to the paper, they've already got a fuzzy vision of the direction in which they're going. The discrete reasoning steps they take to get to the destination are guided by high-level intuition.

These two poles are complementary, and it's their interleaving that enables extreme generalization. No mind could be complete without both of them.

## 14.4.3 The missing half of the picture

By this point, you should start seeing what's missing from modern deep learning: it's very good at encoding value-centric abstraction, but it has basically no ability to generate program-centric abstraction. Human-like intelligence is a tight interleaving of both types, so we're literally missing half of what we need—arguably the most important half.

Now, here's a caveat. So far, I've presented each type of abstraction as entirely separate from the other—opposite, even. In practice, however, they're more of a spectrum: to an extent, you could do reasoning by embedding discrete programs in continuous manifolds—just like you may fit a polynomial function through any set of discrete points, as long as you have enough coefficients. And inversely, you could use discrete programs to emulate continuous distance functions—after all, when you're doing linear algebra on a computer, you're working with continuous spaces, entirely via discrete programs that operate on ones and zeros.

However, there are clearly types of problems that are better suited to one or the other. Try to train a deep learning model to sort a list of five numbers, for instance. With the right architecture, it's not impossible, but it's an exercise in frustration. You'll need a massive amount of training data to make it happen—and even then, the model will still make occasional mistakes when presented with new numbers. And if you want to start sorting lists of 10 numbers instead, you'll need to completely retrain the model on even more data. Meanwhile, writing a sorting algorithm in Python takes just a few lines—and the resulting program, once validated on a couple more examples, will work every time on lists of any size. That's pretty strong generalization: going from a couple of demonstration examples and test examples to a program that can successfully process literally any list of numbers.

In reverse, perception problems are a terrible fit for discrete reasoning processes. Try to write a pure-Python program to classify MNIST digits without using any machine learning technique: you're in for a ride. You'll find yourself painstakingly coding functions that can detect the number of closed loops in a digit, the coordinates of the center of mass of a digit, and so on. After thousands of lines of code, you might achieve ... 90% test accuracy. In this case, fitting a parametric model is much simpler; it can better utilize the large amount of data that's available, and it achieves much more robust results. If you have lots of data and you're faced with a problem where the manifold hypothesis applies, go with deep learning.

For this reason, it's unlikely that we'll see the rise of an approach that would reduce reasoning problems to manifold interpolation, or that would reduce perception problems to discrete reasoning. The way forward in AI is to develop a unified framework that incorporates both types of abstract analogy-making. Let's examine what that might look like.

## 14.5 The future of deep learning

Given what we know of how deep nets work, their limitations, and what they're currently missing, can we predict where things are headed in the medium term? Following are some purely personal thoughts. Note that I don't have a crystal ball, so a lot of what I anticipate may fail to become reality. I'm sharing these predictions not because I expect them to be proven completely right in the future, but because they're interesting and actionable in the present.

At a high level, these are the main directions in which I see promise:

- Models closer to general-purpose computer programs, built on top of far richer primitives than the current differentiable layers. This is how we'll get to reasoning and abstraction, the lack of which is the fundamental weakness of current models.

- A fusion between deep learning and discrete search over program spaces, with the former providing perception and intuition capabilities, and the latter providing reasoning and planning capabilities.

- Greater, systematic reuse of previously learned features and architectures, such as meta-learning systems using reusable and modular program subroutines.

Additionally, note that these considerations aren't specific to the sort of supervised learning that has been the bread and butter of deep learning so far—rather, they're applicable to any form of machine learning, including unsupervised, self-supervised, and reinforcement learning. It isn't fundamentally important where your labels come from or what your training loop looks like; these different branches of machine learning are different facets of the same construct. Let's dive in.

## 14.5.1 Models as programs

As noted in the previous section, a necessary transformational development that we can expect in the field of machine learning is a move away from models that perform purely pattern recognition and can only achieve local generalization, toward models capable of abstraction and reasoning that can achieve extreme generalization. Current AI programs that are capable of basic forms of reasoning are all hardcoded by human programmers: for instance, software that relies on search algorithms, graph manipulation, and formal logic.

That may be about to change, thanks to program synthesis—a field that is very niche today, but I expect to take off in a big way over the next few decades. Program synthesis consists of automatically generating simple programs by using a search algorithm (possibly genetic search, as in genetic programming) to explore a large space of possible programs (see figure 14.11). The search stops when a program is found that matches the required specifications, often provided as a set of input-output pairs. This is highly reminiscent of machine learning: given training data provided as input-output pairs, we find a program that matches inputs to outputs and can generalize to new inputs. The difference is that instead of learning parameter values in a hardcoded program (a neural network), we generate source code via a discrete search process (see table 14.2).

![](img/ab452ecf572a1f1372915be13bd8088f_484_0.png)
