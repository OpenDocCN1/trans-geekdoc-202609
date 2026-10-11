![](image_rsrc10V.jpg)

  

![What’s Really Going On in Machine Learning Some Minimal Models by Stephen Wolfram](image_rsrc10W.jpg)

What’s Really Going On in Machine Learning? Some Minimal Models  
Copyright © 2025 Stephen Wolfram, LLC  
Wolfram Media, Inc. | [wolfram-media.com](https://www.wolfram-media.com/)

ISBN-978-1-57955-107-0 (ebook)

For information about permission to reproduce selections from this book, contact [permissions@wolfram.com](mailto:permissions@wolfram.com).

## The Mystery of Machine Learning

It’s surprising how little is known about the foundations of machine learning. Yes, from an engineering point of view, an immense amount has been figured out about how to build neural nets that do all kinds of impressive and [sometimes almost magical things](https://writings.stephenwolfram.com/2023/02/what-is-chatgpt-doing-and-why-does-it-work/). But at a fundamental level we still don’t really know why neural nets “work”—and we don’t have any kind of “scientific big picture” of what’s going on inside them.

The basic structure of neural networks can be pretty simple. But by the time they’re trained up with all their weights, etc. it’s been hard to tell what’s going on—or even to get any good visualization of it. And indeed it’s far from clear even what aspects of the whole setup are actually essential, and what are just “details” that have perhaps been “grandfathered” all the way from when computational neural nets were first invented in the 1940s.

Well, what I’m going to try to do here is to get “underneath” this—and to “strip things down” as much as possible. I’m going to explore some very minimal models—that, among other things, are more directly amenable to visualization. At the outset, I wasn’t at all sure that these minimal models would be able to reproduce any of the kinds of things we see in machine learning. But, rather surprisingly, it seems they can.

And the simplicity of their construction makes it much easier to “see inside them”—and to get more of a sense of what essential phenomena actually underlie machine learning. One might have imagined that even though the training of a machine learning system might be circuitous, somehow in the end the system would do what it does through some kind of identifiable and “explainable” mechanism. But we’ll see that in fact that’s typically not at all what happens.

Instead it looks much more as if the training manages to home in on some quite wild computation that “just happens to achieve the right results”. Machine learning, it seems, isn’t building structured mechanisms; rather, it’s basically just sampling from the typical complexity one sees in the computational universe, picking out pieces whose behavior turns out to overlap what’s needed. And in a sense, therefore, the possibility of machine learning is ultimately yet another consequence of the phenomenon of [computational irreducibility](https://www.wolframscience.com/nks/chap-12--the-principle-of-computational-equivalence#sect-12-6--computational-irreducibility).

Why is that? Well, it’s only because of computational irreducibility that there’s all that richness in the computational universe. And, more than that, it’s because of computational irreducibility that things end up being effectively random enough that the adaptive process of training a machine learning system can reach success without getting stuck.

But the presence of computational irreducibility also has another important implication: that even though we can expect to find limited pockets of computational reducibility, we can’t expect a “general narrative explanation” of what a machine learning system does. In other words, there won’t be a traditional (say, mathematical) “general science” of machine learning (or, for that matter, probably also neuroscience). Instead, the story will be much closer to the fundamentally computational “[new kind of science](https://www.wolframscience.com/nks/)” that I’ve explored for so long, and that has brought us our [Physics Project](https://www.wolframphysics.org/) and [the ruliad](https://writings.stephenwolfram.com/2021/11/the-concept-of-the-ruliad/).

In many ways, the problem of machine learning is a version of the [general problem of adaptive evolution](https://writings.stephenwolfram.com/2024/05/why-does-biological-evolution-work-a-minimal-model-for-biological-evolution-and-other-adaptive-processes/), as encountered [for example in biology](https://writings.stephenwolfram.com/2024/05/why-does-biological-evolution-work-a-minimal-model-for-biological-evolution-and-other-adaptive-processes/). In biology we typically imagine that we want to adaptively optimize some overall “fitness” of a system; in machine learning we typically try to adaptively “train” a system to make it align with certain goals or behaviors, most often defined by examples. (And, yes, in practice this is often done by trying to minimize a quantity normally called the “loss”.)

And while in biology there’s a general sense that “things arise through evolution”, quite how this works has always been rather mysterious. But (rather to my surprise) I recently [found a very simple model](https://writings.stephenwolfram.com/2024/05/why-does-biological-evolution-work-a-minimal-model-for-biological-evolution-and-other-adaptive-processes/) that seems to do well at capturing at least some of the most essential features of biological evolution. And while the model isn’t the same as what we’ll explore here for machine learning, it has some definite similarities. And in the end we’ll find that the core phenomena of machine learning and of biological evolution appear to be remarkably aligned—and both fundamentally connected to the phenomenon of computational irreducibility.

Most of what I’ll do here focuses on foundational, theoretical questions. But in understanding more about what’s really going on in machine learning—and what’s essential and what’s not—we’ll also be able to begin to see how in practice machine learning might be done differently, potentially with more efficiency and more generality.

## Traditional Neural Nets

To begin the process of understanding the essence of machine learning, let’s start from a very traditional—and familiar—example: a [fully connected (“multilayer perceptron”) neural net](https://writings.stephenwolfram.com/2023/02/what-is-chatgpt-doing-and-why-does-it-work/#machine-learning-and-the-training-of-neural-nets) that’s been trained to compute a certain function f\[x\]:

![](image_rsrc10X.jpg)

If one gives a value x as input at the top, then after “rippling through the layers of the network” one gets a value at the bottom that (almost exactly) corresponds to our function f\[x\]:

![](image_rsrc10Y.jpg)

Scanning through different inputs x, we see different patterns of intermediate values inside the network:

![](image_rsrc10Z.jpg)

And here’s (on a linear and log scale) how each of these intermediate values changes with x. And, yes, the way the final value (highlighted here) emerges looks very complicated:

![](image_rsrc110.jpg)

So how is the neural net ultimately put together? How are these values that we’re plotting determined? We’re using the [standard setup for a fully connected multilayer network](https://writings.stephenwolfram.com/2023/02/what-is-chatgpt-doing-and-why-does-it-work/#neural-nets). Each node (“neuron”) on each layer is connected to all nodes on the layer above—and values “flow” down from one layer to the next, being multiplied by the (positive or negative) “weight” (indicated by color in our pictures) associated with the connection through which they flow. The value of a given neuron is found by totaling up all its (weighted) inputs from the layer before, adding a “bias” value for that neuron, and then applying to the result a certain (nonlinear) “[activation function](https://reference.wolfram.com/language/ref/ElementwiseLayer.html)” (here ReLU or [Ramp](http://reference.wolfram.com/language/ref/Ramp.html)\[z\], i.e. [If](http://reference.wolfram.com/language/ref/If.html)\[z < 0, 0, z\]).

What overall function a given neural net will compute is determined by the collection of weights and biases that appear in the neural net (along with its overall connection architecture, and the activation function it’s using). The idea of machine learning is to find weights and biases that produce a particular function by adaptively “learning” from examples of that function. Typically we might start from a random collection of weights, then successively tweak weights and biases to [“train” the neural net](https://reference.wolfram.com/language/ref/NetTrain.html) to reproduce the function:

![](image_rsrc111.jpg)

We can get a sense of how this progresses (and, yes, it’s complicated) by plotting successive changes in individual weights over the course of the training process (the spikes near the end come from “neutral changes” that don’t affect the overall behavior):

![](image_rsrc112.jpg)

The overall objective in the training is progressively to decrease [the “loss”](https://reference.wolfram.com/language/ref/LossFunction.html)—the average (squared) difference between true values of f\[x\] and those generated by the neural net. The evolution of the loss defines a “learning curve” for the neural net, with the downward glitches corresponding to points where the neural net in effect “made a breakthrough” in being able to represent the function better:

![](image_rsrc113.jpg)

It’s important to note that typically there’s randomness injected into neural net training. So if one runs the training multiple times, one will get different networks—and different learning curves—every time:

![](image_rsrc114.jpg)![](image_rsrc115.jpg)

But what’s really going on in neural net training? Effectively we’re finding a way to “compile” a function (at least to some approximation) into a neural net with a certain number of (real-valued) parameters. And in the example here we happen to be using about 100 parameters.

But what happens if we use a different number of parameters, or set up the architecture of our neural net differently? Here are a few examples, indicating that for the function we’re trying to generate, the network we’ve been using so far is pretty much the smallest that will work:

![](image_rsrc116.jpg)

And, by the way, here’s what happens if we change our activation function from ReLU ![](image_rsrc117.jpg)to the smoother ELU ![](image_rsrc118.jpg):

![](image_rsrc119.jpg)

Later we’ll talk about what happens when we do machine learning with discrete systems. And in anticipation of that, it’s interesting to see what happens if we take a neural net of the kind we’ve discussed here, and “quantize” its weights (and biases) in discrete levels:

![](image_rsrc11A.jpg)

The result is that (as recent experience with large-scale neural nets has also shown) the basic “operation” of the neural net does not require precise real numbers, but survives even when the numbers are at least somewhat discrete—as this 3D rendering as a function of the discreteness level δ also indicates:

![](image_rsrc11B.jpg)

## Simplifying the Topology: Mesh Neural Nets

So far we’ve been discussing very traditional neural nets. But to do machine learning, do we really need systems that have all those details? For example, do we really need every neuron on each layer to get an input from every neuron on the previous layer? What happens if instead every neuron just gets input from at most two others—say with the neurons effectively laid out in a simple mesh? Quite surprisingly, it turns out that such a network is still perfectly able to generate a function like the one we’ve been using as an example:

![](image_rsrc11C.jpg)

And one advantage of such a “mesh neural net” is that—like a cellular automaton—its “internal behavior” can readily be visualized in a rather direct way. So, for example, here are visualizations of “how the mesh net generates its output”, stepping through different input values x:

![](image_rsrc11D.jpg)

And, yes, even though we can visualize it, it’s still hard to understand “what’s going on inside”. Looking at the intermediate values of each individual node in the network as a function of x doesn’t help much, though we can “see something happening” at places where our function f\[x\] has jumps:

![](image_rsrc11E.jpg)

So how do we train a mesh neural net? Basically we can use the same procedure as for a fully connected network of the kind we saw above (ReLU activation functions don’t seem to work well for mesh nets, so we’re using ELU here):

![](image_rsrc11F.jpg)

Here’s the evolution of differences in each individual weight during the training process:

![](image_rsrc11G.jpg)

And here are results for different random seeds:

![](image_rsrc11H.jpg)![](image_rsrc11J.jpg)

At the size we’re using, our mesh neural nets have about the same number of connections (and thus weights) as our main example of a fully connected network above. And we see that if we try to reduce the size of our mesh neural net, it doesn’t do well at reproducing our function:

![](image_rsrc11K.jpg)

## Making Everything Discrete: A Biological Evolution Analog

Mesh neural nets simplify the topology of neural net connections. But, somewhat surprisingly at first, it seems as if we can go much further in simplifying the systems we’re using—and still successfully do versions of machine learning. And in particular we’ll find that we can make our systems completely discrete.

The typical methodology of neural net training involves progressively tweaking real-valued parameters, usually using methods based on calculus, and on finding derivatives. And one might imagine that any successful adaptive process would ultimately have to rely on being able to make arbitrarily small changes, of the kind that are possible with real-valued parameters.

But in [studying simple idealizations of biological evolution](https://writings.stephenwolfram.com/2024/05/why-does-biological-evolution-work-a-minimal-model-for-biological-evolution-and-other-adaptive-processes/) I recently found striking examples where this isn’t the case—and where completely discrete systems seemed able to capture the essence of what’s going on.

As an example consider a (3-color) cellular automaton. The rule is shown on the left, and the behavior one generates by repeatedly applying that rule (starting from a single-cell initial condition) is shown on the right:

![](image_rsrc11M.jpg)

The rule has the property that the pattern it generates (from a single-cell initial condition) survives for exactly 40 steps, and then dies out (i.e. every cell becomes white). And the important point is that this rule can be found by a discrete adaptive process. The idea is to start, say, from a null rule, and then at each step to randomly change a single outcome out of the 27 in the rule (i.e. make a “single-point mutation” in the rule). Most such changes will cause the “lifetime” of the pattern to get further from our target of 40—and these we discard. But gradually we can build up “beneficial mutations”

![](image_rsrc11N.jpg)

that through “progressive adaptation” eventually get to our original lifetime-40 rule:

![](image_rsrc11P.jpg)

We can make a plot of all the attempts we made that eventually let us reach lifetime 40—and we can think of this progressive “fitness” curve as being directly analogous to the loss curves in machine learning that we saw before:

![](image_rsrc11R.jpg)

If we make different sequences of random mutations, we’ll get different paths of adaptive evolution, and different “solutions” for rules that have lifetime 40:

![](image_rsrc11S.jpg)

Two things are immediately notable about these. First, that they essentially all seem to be “using different ideas” to reach their goal (presumably analogous to the phenomenon of different branches in the tree of life). And second, that none of them seem to be using a clear “mechanical procedure” (of the kind we might construct through traditional engineering) to reach their goal. Instead, they seem to be finding “natural” complicated behavior that just “happens” to achieve the goal.

It’s nontrivial, of course, that this behavior can achieve a goal like the one we’ve set here, as well as that simple selection based on random point mutations can successfully reach the necessary behavior. But [as I discussed in connection with biological evolution](https://writings.stephenwolfram.com/2024/05/why-does-biological-evolution-work-a-minimal-model-for-biological-evolution-and-other-adaptive-processes/), this is ultimately a story of [computational irreducibility](https://www.wolframscience.com/nks/chap-12--the-principle-of-computational-equivalence#sect-12-6--computational-irreducibility)—particularly in generating diversity both in behavior, and in the paths necessary to reach it.

But, OK, so how does this model of adaptive evolution relate to systems like neural nets? In the standard language of neural nets, our model is like a discrete analog of a recurrent convolutional network. It’s “convolutional” because at any given step the same rule is applied—locally—throughout an array of elements. It’s “recurrent” because in effect data is repeatedly “passed through” the same rule. The kinds of procedures (like “backpropagation”) typically used to train traditional neural nets wouldn’t be able to train such a system. But it turns out that—essentially as a consequence of computational irreducibility—the very simple method of successive random mutation can be successful.

## Machine Learning in Discrete Rule Arrays

Let’s say we want to set up a system like a neural net—or at least a mesh neural net—but we want it to be completely discrete. (And I mean “born discrete”, not just discretized from an existing continuous system.) How can we do this? One approach (that, as it happens, [I first considered in the mid-1980s](https://content.wolfram.com/sw-publications/2020/07/approaches-complexity-engineering.pdf)—but never seriously explored) is to make what we can call a “rule array”. Like in a cellular automaton there’s an array of cells. But instead of these cells always being updated according to the same rule, each cell at each place in the cellular automaton analog of “spacetime” can make a different choice of what rule it will use. (And although it’s a fairly extreme idealization, we can potentially imagine that these different rules represent a discrete analog of different local choices of weights in a mesh neural net.)

As a first example, let’s consider a rule array in which there are two possible choices of rules: k \= 2, r \= 1 [cellular automaton rules 4 and 146](https://www.wolframscience.com/nks/chap-3--the-world-of-simple-programs#sect-3-2--more-cellular-automata) (which are respectively [class 2 and class 3](https://www.wolframscience.com/nks/chap-6--starting-from-randomness#sect-6-2--four-classes-of-behavior)):

![](image_rsrc11T.jpg)

A particular rule array is defined by which of these rules is going to be used at each (“spacetime”) position in the array. Here are a few examples. In all cases we’re starting from the same single-cell initial condition. But in each case the rule array has a different arrangement of rule choices—with cells “running” rule 4 being given a ![](image_rsrc11U.jpg)background, and those running rule 146 a ![](image_rsrc11V.jpg)one:

![](image_rsrc11W.jpg)

We can see that different choices of rule array can yield very different behaviors. But (in the spirit of machine learning) can we in effect “invert this”, and find a rule array that will give some particular behavior we want?

A simple approach is to do the direct analog of what we did in our minimal modeling of biological evolution: progressively make random “single-point mutations”—here “flipping” the identity of just one rule in the rule array—and then keeping only those mutations that don’t make things worse.

As our sample objective, let’s ask to find a rule array that makes the pattern generated from a single cell using that rule array “survive” for exactly 50 steps. At first it might not be obvious that we’d be able to find such a rule array. But in fact our simple adaptive procedure easily manages to do this:

![](image_rsrc11X.jpg)

As the dots here indicate, many mutations don’t lead to longer lifetimes. But every so often, the adaptive process has a “breakthrough” that increases the lifetime—eventually reaching 50:

![](image_rsrc11Y.jpg)

Just as in our model of biological evolution, different random sequences of mutations lead to different “solutions”, here to the problem of “living for exactly 50 steps”:

![](image_rsrc11Z.jpg)

Some of these are in effect “simple solutions” that require only a few mutations. But most—like most of our examples in biological evolution—seem more as if they just “happen to work”, effectively by tapping into just the right, fairly complex behavior.

Is there a sharp distinction between these cases? Looking at the collection of “fitness” (AKA “learning”) curves for the examples above, it doesn’t seem so:

![](image_rsrc120.jpg)

It’s not too difficult to see how to “construct a simple solution” just by strategically placing a single instance of the second rule in the rule array:

![](image_rsrc121.jpg)

But the point is that adaptive evolution by repeated mutation normally won’t “discover” this simple solution. And what’s significant is that the adaptive evolution can nevertheless still successfully find some solution—even though it’s not one that’s “understandable” like this.

The cellular automaton rules we’ve been using so far take 3 inputs. But it turns out that we can make things even simpler by just putting ordinary [2-input Boolean functions](https://www.wolframscience.com/nks/p806--implications-for-mathematics-and-its-foundations/) into our rule array. For example, we can make a rule array from [And](https://reference.wolfram.com/language/ref/And.html) and [Xor](https://reference.wolfram.com/language/ref/Xor.html) functions ([r = 1/2 rules 8 and 6](https://www.wolframscience.com/nks/p806--implications-for-mathematics-and-its-foundations/)):

![](image_rsrc122.jpg)

Different And+Xor (![](image_rsrc123.jpg)\+ ![](image_rsrc124.jpg)) rule arrays show different behavior:

![](image_rsrc125.jpg)

But are there for example And+Xor rule arrays that will compute any of the 16 possible (2-input) functions? We can’t get [Not](https://reference.wolfram.com/language/ref/Not.html) or any of the 8 other functions with ![](image_rsrc126.jpg)—but it turns out we can get all 8 functions with ![](image_rsrc127.jpg)(additional inputs here are assumed to be ![](image_rsrc128.jpg)):

![](image_rsrc129.jpg)

And in fact we can also set up And+Xor rule arrays for all other “even” Boolean functions. For example, here are rule arrays for the 3-input rule 30 and rule 110 Boolean functions:

![](image_rsrc12A.jpg)

It may be worth commenting that the ability to set up such rule arrays is related to [functional completeness](https://www.wolframscience.com/nks/p807--implications-for-mathematics-and-its-foundations/) of the underlying rules we’re using—though it’s not quite the same thing. Functional completeness is about setting up arbitrary formulas, that can in effect allow long-range connections between intermediate results. Here, all information has to explicitly flow through the array. But for example the functional completeness of [Nand](http://reference.wolfram.com/language/ref/Nand.html) (r = 1/2 rule 7, ![](image_rsrc12B.jpg)) allows it to generate all Boolean functions when combined for example with [First](http://reference.wolfram.com/language/ref/First.html) (r = 1/2 rule 12, ![](image_rsrc12C.jpg)), though sometimes the rule arrays required are quite large:

![](image_rsrc12D.jpg)

OK, but what happens if we try to use our adaptive evolution process—say to solve the problem of finding a pattern that survives for exactly 30 steps? Here’s a result for And+Xor rule arrays:

![](image_rsrc12E.jpg)

And here are examples of other “solutions” (none of which in this case look particularly “mechanistic” or “constructed”):

![](image_rsrc12F.jpg)

But what about learning our original f\[x\] = ![](image_rsrc12G.jpg)function? Well, first we have to decide how we’re going to represent the numbers x and f\[x\] in our discrete rule array system. And one approach is to do this simply in terms of the position of a black cell (“one-hot encoding”). So, for example, in this case there’s an initial black cell at a position corresponding to about x = –1.1. And then the result after passing through the rule array is a black cell at a position corresponding to f\[x\] = 1.0:

![](image_rsrc12H.jpg)

So now the question is whether we can find a rule array that successfully maps initial to final cell positions according to the mapping x ![](image_rsrc12J.jpg)f\[x\] we want. Well, here’s an example that comes at least close to doing this (note that the array is taken to be cyclic):

![](image_rsrc12K.jpg)

So how did we find this? Well, we just used a simple adaptive evolution process. In direct analogy to the way it’s usually done in machine learning, we set up “training examples”, here of the form:

![](image_rsrc12M.jpg)

Then we repeatedly made single-point mutations in our rule array, keeping those mutations where the total difference from all the training examples didn’t increase. And after 50,000 mutations this gave the final result above.

We can get some sense of “how we got there” by showing the sequence of intermediate results where we got closer to the goal (as opposed to just not getting further from it):

![](image_rsrc12N.jpg)

Here are the corresponding rule arrays, in each case highlighting elements that have changed (and showing the computation of f\[0\] in the arrays):

![](image_rsrc12P.jpg)

Different sequences of random mutations will lead to different rule arrays. But with the setup defined here, the resulting rule arrays will almost always succeed in accurately computing f\[x\]. Here are a few examples—in which we’re specifically showing the computation of f\[0\]:

![](image_rsrc12R.jpg)

And once again an important takeaway is that we don’t see “identifiable mechanism” in what’s going on. Instead, it looks more as if the rule arrays we’ve got just “happen” to do the computations we want. Their behavior is complicated, but somehow we can manage to “tap into it” to compute our f\[x\].

But how robust is this computation? A key feature of typical machine learning is that it can “generalize” away from the specific examples it’s been given. It’s never been clear just how to characterize that generalization (when does an image of a cat in a dog suit start [being identified as an image of a dog](https://writings.stephenwolfram.com/2015/05/wolfram-language-artificial-intelligence-the-image-identification-project/)?). But—at least when we’re talking about classification tasks—we can think of what’s going on in terms of [basins of attraction](https://www.wolframscience.com/nks/p624--human-thinking/) that lead to attractors corresponding to our classes.

It’s all considerably easier to analyze, though, in the kind of discrete system we’re exploring here. For example, we can readily enumerate all our training inputs (i.e. all initial states containing a single black cell), and then see how frequently these cause any given cell to be black:

![](image_rsrc12S.jpg)

By the way, here’s what happens to this plot at successive “breakthroughs” during training:

![](image_rsrc12T.jpg)

But what about all possible inputs, including ones that don’t just contain a single black cell? Well, we can enumerate all of them, and compute the overall frequency for each cell in the array to be black:

![](image_rsrc12U.jpg)

As we would expect, the result is considerably “fuzzier” than what we got purely with our training inputs. But there’s still a strong trace of the discrete values for f\[x\] that appeared in the training data. And if we plot the overall probability for a given final cell to be black, we see peaks at positions corresponding to the values 0 and 1 that f\[x\] takes on:

![](image_rsrc12V.jpg)

But because our system is discrete, we can explicitly look at what outcomes occur:

![](image_rsrc12W.jpg)

The most common overall is the “meaningless” all-white state—that basically occurs when the computation from the input “never makes it” to the output. But the next most common outcomes correspond exactly to f\[x\] = 0 and f\[x\] = 1. After that is the “superposition” outcome where f\[x\] is in effect “both 0 and 1”.

But, OK, so what initial states are “in the basins of attraction of” (i.e. will evolve to) the various outcomes here? The fairly flat plots in the last column above indicate that the overall density of black cells gives little information about what attractor a particular initial state will evolve to.

So this means we have to look at specific configurations of cells in the initial conditions. As an example, start from the initial condition

![](image_rsrc12X.jpg)

which evolves to:

![](image_rsrc12Y.jpg)

Now we can ask what happens if we look at a sequence of slightly different initial conditions. And here we show in black and white initial conditions that still evolve to the original “attractor” state, and in pink ones that evolve to some different state:

![](image_rsrc12Z.jpg)

What’s actually going on inside here? Here are a few examples, highlighting cells whose values change as a result of changing the initial condition:

![](image_rsrc130.jpg)

As is typical in machine learning, there doesn’t seem to be any simple characterization of the form of the basin of attraction. But now we have a sense of what the reason for this is: it’s another consequence of computational irreducibility. Computational irreducibility gives us the effective randomness that allows us to find useful results by adaptive evolution, but it also leads to changes having what seem like random and unpredictable effects. (It’s worth noting, by the way, that we could probably dramatically improve the robustness of our attractor basins by specifically including in our training data examples that have “noise” injected.)

## Multiway Mutation Graphs

In doing machine learning in practice, the goal is typically to find some collection of weights, etc. that successfully solve a particular problem. But in general there will be many such collections of weights, etc. With typical continuous weights and random training steps it’s very difficult to see what the whole “ensemble” of possibilities is. But in our discrete rule array systems, this becomes more feasible.

Consider a tiny 2×2 rule array with two possible rules. We can [make a graph whose edges represent all possible “point mutations”](https://writings.stephenwolfram.com/2024/05/why-does-biological-evolution-work-a-minimal-model-for-biological-evolution-and-other-adaptive-processes/#the-multiway-graph-of-all-possible-mutation-histories) that can occur in this rule array:

![](image_rsrc131.jpg)

In our adaptive evolution process, we’re always moving around a graph like this. But typically most “moves” will end up in states that are rejected because they increase whatever loss we’ve defined.

Consider the problem of generating an And+Xor rule array in which we end with lifetime-4 patterns. Defining the loss as how far we are from this lifetime, we can draw a graph that shows all possible adaptive evolution paths that always progressively decrease the loss:

![](image_rsrc132.jpg)

The result is a multiway graph of the type we’ve now seen in a [great many kinds of situations](https://writings.stephenwolfram.com/2023/11/aggregation-and-tiling-as-multicomputational-processes/)—notably our [recent study of biological evolution](https://writings.stephenwolfram.com/2024/05/why-does-biological-evolution-work-a-minimal-model-for-biological-evolution-and-other-adaptive-processes/#the-multiway-graph-of-all-possible-mutation-histories).

And although this particular example is quite trivial, the idea in general is that different parts of such a graph represent “different strategies” for solving a problem. And—in direct analogy to our [Physics Project](https://www.wolframphysics.org/) and [our studies of things like game graphs](https://writings.stephenwolfram.com/2022/06/games-and-puzzles-as-multicomputational-systems/)—one can imagine such strategies being laid out in a “[branchial space](https://www.wolframphysics.org/technical-introduction/the-updating-process-for-string-substitution-systems/the-concept-of-branchial-graphs/)” defined by common ancestry of configurations in the multiway graph.

And one can expect that while in some cases the branchial graph will be fairly uniform, in other cases it will have quite separated pieces—that represent fundamentally different strategies. Of course, the fact that underlying strategies may be different doesn’t mean that the overall behavior or performance of the system will be noticeably different. And indeed one expects that in most cases computational irreducibility will lead to enough effective randomness that there’ll be no discernable difference.

But in any case, here’s an example starting with a rule array that contains both And and Xor—where we observe distinct branches of adaptive evolution that lead to different solutions to the problem of finding a configuration with a lifetime of exactly 4:

![](image_rsrc133.jpg)

## Optimizing the Learning Process

How should one actually do the learning in machine learning? In practical work with traditional neural nets, learning is normally done using systematic algorithmic methods like backpropagation. But so far, all we’ve done here is something much simpler: we’ve “learned” by successively making random point mutations, and keeping only ones that don’t lead us further from our goal. And, yes, it’s interesting that such a procedure can work at all—and ([as we’ve discussed elsewhere](https://writings.stephenwolfram.com/2024/05/why-does-biological-evolution-work-a-minimal-model-for-biological-evolution-and-other-adaptive-processes/)) this is presumably very relevant to understanding phenomena like biological evolution. But, as we’ll see, there are more efficient (and probably much more efficient) methods of doing machine learning, even for the kinds of discrete systems we’re studying.

Let’s start by looking again at our earlier example of finding an And+Xor rule array that gives a “lifetime” of exactly 30. At each step in our adaptive (“learning”) process we make a single-point mutation (changing a single rule in the rule array), keeping the mutation if it doesn’t take us further from our goal. The mutations gradually accumulate—every so often reaching a rule array that gives a lifetime closer to 30. Just as above, here’s a plot of the lifetime achieved by successive mutations—with the “internal” red dots corresponding to rejected mutations:

![](image_rsrc134.jpg)

We see a series of “plateaus” at which mutations are accumulating but not changing the overall lifetime. And between these we see occasional “breakthroughs” where the lifetime jumps. Here are the actual rule array configurations for these breakthroughs, with mutations since the last breakthrough highlighted:

![](image_rsrc135.jpg)

But in the end the process here is quite wasteful; in this example, we make a total of 1705 mutations, but only 780 of them actually contribute to generating the final rule array; all the others are discarded along the way.

So how can we do better? One strategy is to try to figure out at each step which mutation is “most likely to make a difference”. And one way to do this is to try every possible mutation in turn at every step (as in multiway evolution)—and see what effect each of them has on the ultimate lifetime. From this we can construct a “change map” in which we give the change of lifetime associated with a mutation at every particular cell. The results will be different for every configuration of rule array, i.e. at every step in the adaptive evolution. But for example here’s what they are for the particular “breakthrough” configurations shown above (elements in regions that are colored gray won’t affect the result if they are changed; ones colored red will have a positive effect (with more intense red being more positive), and ones colored blue a negative one:

![](image_rsrc136.jpg)

Let’s say we start from a random rule array, then repeatedly construct the change map and apply the mutation that it implies gives the most positive change—in effect at each step following the “path of steepest descent” to get to the lifetime we want (i.e. reduce the loss). Then the sequence of “breakthrough” configurations we get is:

![](image_rsrc137.jpg)

And this in effect corresponds to a slightly more direct “path to a solution” than our sequence of pure single-point mutations.

By the way, the particular problem of reaching a certain lifetime has a simple enough structure that this “steepest descent” method—when started from a simple uniform rule array—finds a very “mechanical” (if slow) path to a solution:

![](image_rsrc138.jpg)

What about the problem of learning f\[x\] = ![](image_rsrc139.jpg)? Once again we can make a change map based on the loss we define. Here are the results for a sequence of “breakthrough” configurations. The gray regions are ones where changes will be “neutral”, so that there’s still exploration that can be done without affecting the loss. The red regions are ones that are in effect “locked in” and where any changes would be deleterious in terms of loss:

![](image_rsrc13A.jpg)

So what happens in this case if we follow the “path of steepest descent”, always making the change that would be best according to the change map? Well, the results are actually quite unsatisfactory. From almost any initial condition the system quickly gets stuck, and never finds any satisfactory solution. In effect it seems that deterministically following the path of steepest descent leads us to a “local minimum” from which we cannot escape. So what are we missing in just looking at the change map? Well, the change map as we’ve constructed it has the limitation that it’s separately assessing the effect of each possible individual mutation. It doesn’t deal with multiple mutations at a time—which could well be needed in general if one’s going to find the “fastest path to success”, and avoid getting stuck.

But even in constructing the change map there’s already a problem. Because at least the direct way of computing it scales quite poorly. In an n×n rule array we have to check the effect of flipping about n2 values, and for each one we have to run the whole system—taking altogether about n4 operations. And one has to do this separately for each step in the learning process.

So how do traditional neural nets avoid this kind of inefficiency? The answer in a sense involves a mathematical trick. And at least as it’s usually presented it’s all based on the continuous nature of the weights and values in neural nets—which allow us to use methods from calculus.

Let’s say we have a neural net like this

![](image_rsrc13B.jpg)

that computes some particular function f\[x\]:

![](image_rsrc13C.jpg)

We can ask how this function changes as we change each of the weights in the network:

![](image_rsrc13D.jpg)

And in effect this gives us something like our “change map” above. But there’s an important difference. Because the weights are continuous, we can think about infinitesimal changes to them. And then we can ask questions like “How does f\[x\] change when we make an infinitesimal change to a particular weight wi?”—or equivalently, “What is the partial derivative of f with respect to wi at the point x?” But now we get to use a key feature of infinitesimal changes: that they can always be thought of as just “adding linearly” (essentially because ε2 can always be ignored compared to ε). Or, in other words, we can summarize any infinitesimal change just by giving its “direction” in weight space, i.e. a vector that says how much of each weight should be (infinitesimally) changed. So if we want to change f\[x\] (infinitesimally) as quickly as possible, we should go in the direction of steepest descent defined by all the derivatives of f with respect to the weights.

In machine learning, we’re typically trying in effect to set the weights so that the form of f\[x\] we generate successfully minimizes whatever loss we’ve defined. And we do this by incrementally “moving in weight space”—at every step computing the direction of steepest descent to know where to go next. (In practice, there are all sorts of tricks like “ADAM” that try to optimize the way to do this.)

But how do we efficiently compute the partial derivative of f with respect to each of the weights? Yes, we could do the analog of generating pictures like the ones above, separately for each of the weights. But it turns out that a standard result from calculus gives us a vastly more efficient procedure that in effect “maximally reuses” parts of the computation that have already been done.

It all starts with the textbook chain rule for the derivative of nested (i.e. composed) functions:

![](image_rsrc13E.jpg)![](image_rsrc13F.jpg)![](image_rsrc13G.jpg)

This basically says that the (infinitesimal) change in the value of the “whole chain” d\[c\[b\[a\[x\]\]\]\] can be computed as a product of (infinitesimal) changes associated with each of the “links” in the chain. But the key observation is then that when we get to the computation of the change at a certain point in the chain, we’ve already had to do a lot of the computation we need—and so long as we stored those results, we always have only an incremental computation to perform.

So how does this apply to neural nets? Well, each layer in a neural net is in effect doing a function composition. So, for example, our d\[c\[b\[a\[x\]\]\]\] is like a trivial neural net:

![](image_rsrc13H.jpg)

But what about the weights, which, after all, are what we are trying to find the effect of changing? Well, we could include them explicitly in the function we’re computing:

![](image_rsrc13J.jpg)

And then we could in principle symbolically compute the derivatives with respect to these weights:

![](image_rsrc13K.jpg)

For our network above

![](image_rsrc13M.jpg)

the corresponding expression (ignoring biases) is

![](image_rsrc13N.jpg)

where ϕ denotes our activation function. Once again we’re dealing with nested functions, and once again—though it’s a bit more intricate in this case—the computation of derivatives can be done by incrementally evaluating terms in the chain rule and in effect using the standard neural net method of “backpropagation”.

So what about the discrete case? Are there similar methods we can use there? We won’t discuss this in detail here, but we’ll give some indications of what’s likely to be involved.

As a potentially simpler case, let’s consider ordinary cellular automata. The analog of our change map asks how the value of a particular “output” cell is affected by changes in other cells—or in effect what the “partial derivative” of the output value is with respect to changes in values of other cells.

For example, consider the highlighted “output” cell in this cellular automaton evolution:

![](image_rsrc13P.jpg)

Now we can look at each cell in this array, and make a change map based on seeing whether flipping the value of just that cell (and then running the cellular automaton forwards from that point) would change the value of the output cell:

![](image_rsrc13R.jpg)

The form of the change map is different if we look at different “output cells”:

![](image_rsrc13S.jpg)

Here, by the way, are some larger change maps for this and a couple of other cellular automaton rules:

![](image_rsrc13T.jpg)

But is there a way to construct such change maps incrementally? One might have thought that there would immediately be at least for [cellular automata that (unlike the cases here) are fundamentally reversible](https://www.wolframscience.com/nks/chap-9--fundamental-physics#sect-9-2--the-notion-of-reversibility). But actually such reversibility doesn’t seem to help much—because although it allows us to “backtrack” whole states of the cellular automaton, it doesn’t allow us to trace the separate effects of individual cells.

So how about using discrete analogs of derivatives and the chain rule? Let’s for example call the function computed by one step in rule 30 cellular automaton evolution w\[x, y, z\]. We can think of the “partial derivative” of this function with respect to x at the point x as representing whether the output of w changes when x is flipped starting from the value given:

![](image_rsrc13U.jpg)

(Note that “no change” is indicated as [False](http://reference.wolfram.com/language/ref/False.html) or ![](image_rsrc13V.jpg), while a change is indicated as [True](http://reference.wolfram.com/language/ref/True.html) or ![](image_rsrc13W.jpg). And, yes, one can either explicitly compute the rule outcomes here, and then deduce from them the functional form, or one can use symbolic rules to directly deduce the functional form.)

One can compute a discrete analog of a derivative for any Boolean function. For example, we have

![](image_rsrc13X.jpg)![](image_rsrc13Y.jpg)

and

![](image_rsrc13Z.jpg)

which we can write as:

![](image_rsrc140.jpg)

We also have:

![](image_rsrc141.jpg)![](image_rsrc142.jpg)![](image_rsrc143.jpg)![](image_rsrc144.jpg)![](image_rsrc145.jpg)![](image_rsrc146.jpg)

And here is a table of “Boolean derivatives” for all 2-input Boolean functions:

![](image_rsrc147.jpg)

And indeed there’s a whole “Boolean calculus” one can set up for these kinds of derivatives. And in particular, there’s a direct analog of the chain rule:

![](image_rsrc148.jpg)

where [Xnor](http://reference.wolfram.com/language/ref/Xnor.html)\[x,y\] is effectively the equality test x == y:

![](image_rsrc149.jpg)

But, OK, how do we use this to create our change maps? In our simple cellular automaton case, we can think of our change map as representing how a [change in an output cell “propagates back”](https://www.wolframscience.com/nks/p604--cryptography-and-cryptanalysis/) to previous cells. But if we just try to apply our discrete calculus rules we run into a problem: different “chain rule chains” can imply different changes in the value of the same cell. In the continuous case this path dependence doesn’t happen because of the way infinitesimals work. But in the discrete case it does. And ultimately we’re doing a kind of backtracking that can really be represented faithfully only as a multiway system. (Though if we just want probabilities, for example, we can consider [averaging over branches of the multiway system](https://www.wolframphysics.org/bulletins/2021/02/multiway-turing-machines/)—and the change maps we showed above are effectively the result of thresholding over the multiway system.)

But despite the appearance of such difficulties in the “simple” cellular automaton case, such methods typically seem to work better in our original, more complicated rule array case. There’s a bunch of subtlety associated with the fact that we’re finding derivatives not only with respect to the values in the rule array, but also with respect to the choice of rules (which are the analog of weights in the continuous case).

Let’s consider the And+Xor rule array:

![](image_rsrc14A.jpg)

Our loss is the number of cells whose values disagree with the row shown at the bottom. Now we can construct a change map for this rule array both in a direct “forward” way, and “backwards” using our discrete derivative methods (where we effectively resolve the small amount of “multiway behavior” by always picking “majority” values):

![](image_rsrc14B.jpg)

The results are similar, though in this case not exactly the same. Here are a few other examples:

![](image_rsrc14C.jpg)

And, yes, in detail there are essentially always local differences between the results from the forward and backward methods. But the backward method—like in the case of backpropagation in ordinary neural nets—can be implemented much more efficiently. And for purposes of practical machine learning it’s actually likely to be perfectly satisfactory—especially given that the forward method is itself only providing an approximation to the question of which mutations are best to do.

And as an example, here are the results of the forward and backward methods for the problem of learning the function f\[x\] = ![](image_rsrc14D.jpg), for the “breakthrough” configurations that we showed above:

![](image_rsrc14E.jpg)

## What Can Be Learned?

We’ve now shown quite a few examples of machine learning in action. But a fundamental question we haven’t yet addressed is what kind of thing can actually be learned by machine learning. And even before we get to this, there’s another question: given a particular underlying type of system, what kinds of functions can it even represent?

As a first example consider a minimal neural net of the form (essentially a single-layer perceptron):

![](image_rsrc14F.jpg)

With ReLU (AKA [Ramp](http://reference.wolfram.com/language/ref/Ramp.html)) as the activation function and the first set of weights all taken to be 1, the function computed by such a neural net has the form:

![](image_rsrc14G.jpg)

With enough weights and biases this form can represent any piecewise linear function—essentially just by moving around ramps using biases, and scaling them using weights. So for example consider the function:

![](image_rsrc14H.jpg)

This is the function computed by the neural net above—and here’s how it’s built up by adding in successive ramps associated with the individual intermediate nodes (neurons):

![](image_rsrc14J.jpg)

(It’s similarly possible to get all smooth functions from activation functions like ELU, etc.)

Things get slightly more complicated if we try to represent functions with more than one argument. With a single intermediate layer we can only get “piecewise (hyper)planar” functions (i.e. functions that change direction only at linear “fault lines”):

![](image_rsrc14K.jpg)

But already with a total of two intermediate layers—and sufficiently many nodes in each of these layers—we can generate any piecewise function of any number of arguments.

If we limit the number of nodes, then roughly we limit the number of boundaries between different linear regions in the values of the functions. But as we increase the number of layers with a given number of nodes, we basically increase the number of sides that polygonal regions within the function values can have:

![](image_rsrc14M.jpg)

So what happens with the mesh nets that we discussed earlier? Here are a few random examples, showing results very similar to shallow, fully connected networks with a comparable total number of nodes:

![](image_rsrc14N.jpg)

OK, so how about our fully discrete rule arrays? What functions can they represent? We already saw part of the answer earlier when we generated rule arrays to represent various Boolean functions. It turns out that there is a fairly efficient procedure based on [Boolean satisfiability](https://reference.wolfram.com/language/ref/SatisfiabilityInstances.html) for explicitly finding rule arrays that can represent a given function—or determine that no rule array (say of a given size) can do this.

Using this procedure, we can find minimal And+Xor rule arrays that represent all (“even”) 3-input Boolean functions (i.e. r = 1 cellular automaton rules):

![](image_rsrc14P.jpg)

It’s always possible to specify any n\-input Boolean function by an array of 2n bits, as in:

![](image_rsrc14R.jpg)

But we see from the pictures above that when we “compile” Boolean functions into And+Xor rule arrays, they can take different numbers of bits (i.e. different numbers of elements in the rule array). (In effect, the “algorithmic information content” of the function varies with the “language” we’re using to represent them.) And, for example, in the n \= 3 case shown here, the distribution of minimal rule array sizes is:

![](image_rsrc14S.jpg)

There are some functions that are difficult to represent as And+Xor rule arrays (and seem to require 15 rule elements)—and others that are easier. And this is similar to what happens if we represent Boolean functions as Boolean expressions (say in conjunctive normal form) and [count the total number of (unary and binary) operations used](https://www.wolframscience.com/nks/notes-10-11--boolean-formula-sizes/):

![](image_rsrc14T.jpg)

OK, so we know that there is in principle an And+Xor rule array that will compute any (even) Boolean function. But now we can ask whether an adaptive evolution process can actually find such a rule array—say with a sequence of single-point mutations. Well, if we do such adaptive evolution—with a loss that counts the number of “wrong outputs” for, say, rule 254—then here’s a sequence of successive breakthrough configurations that can be produced:

![](image_rsrc14U.jpg)

The results aren’t as compact as the minimal solution above. But it seems to always be possible to find at least some And+Xor rule array that “solves the problem” just by using adaptive evolution with single-point mutations.

Here are results for some other Boolean functions:

![](image_rsrc14V.jpg)

And so, yes, not only are all (even) Boolean functions representable in terms of And+Xor rule arrays, they’re also learnable in this form, just by adaptive evolution with single-point mutations.

In what we did above, we were looking at how machine learning works with our rule arrays in specific cases like for the ![](image_rsrc14W.jpg)function. But now we’ve got a case where we can explicitly enumerate all possible functions, at least of a given class. And in a sense what we’re seeing is evidence that machine learning tends to be very broad—and capable at least in principle of learning pretty much any function.

Of course, there can be specific restrictions. Like the And+Xor rule arrays we’re using here can’t represent (“odd”) functions where ![](image_rsrc14X.jpg). (The [Nand](https://reference.wolfram.com/language/ref/Nand.html)+[First](https://reference.wolfram.com/language/ref/First.html) rule arrays we discussed above nevertheless can.) But in general it seems to be a reflection of the [Principle of Computational Equivalence](https://www.wolframscience.com/nks/chap-12--the-principle-of-computational-equivalence/) that pretty much any setup is capable of representing any function—and also adaptively “learning” it.

By the way, it’s a lot easier to discuss questions about representing or learning “any function” when one’s dealing with discrete (countable) functions—because one can expect to either be able to “exactly get” a given function, or not. But for continuous functions, it’s more complicated, because one’s pretty much inevitably dealing with approximations (unless one can use symbolic forms, which are basically discrete). So, for example, while we can say (as we did above) that (ReLU) neural nets can represent any piecewise-linear function, in general we’ll only be able to imagine successively approaching an arbitrary function, much like when you progressively add more terms in a simple Fourier series:

![](image_rsrc14Y.jpg)

Looking back at our results for discrete rule arrays, one notable observation that is that while we can successfully reproduce all these different Boolean functions, the actual rule array configurations that achieve this tend to look quite messy. And indeed it’s much the same as we’ve seen throughout: machine learning can find solutions, but they’re not “structured solutions”; they’re in effect just solutions that “happen to work”.

Are there more structured ways of representing Boolean functions with rule arrays? Here are the two possible minimum-size And+Xor rule arrays that represent rule 30:

![](image_rsrc14Z.jpg)

At the next-larger size there are more possibilities for rule 30:

![](image_rsrc150.jpg)

And there are also rule arrays that can represent rule 110:

![](image_rsrc151.jpg)

But in none of these cases is there obvious structure that allows us to immediately see how these computations work, or what function is being computed. But what if we try to explicitly construct—effectively by standard engineering methods—a rule array that computes a particular function? We can start by taking something like the function for rule 30 and writing it in terms of And and Xor (i.e. in [ANF, or “algebraic normal form”](https://reference.wolfram.com/language/ref/BooleanConvert.html)):

![](image_rsrc152.jpg)

We can imagine implementing this using an “evaluation graph”:

![](image_rsrc153.jpg)

But now it’s easy to turn this into a rule array (and, yes, we haven’t gone all the way and arranged to copy inputs, etc.):

![](image_rsrc154.jpg)

“Evaluating” this rule array for different inputs, we can see that it indeed gives rule 30:

![](image_rsrc155.jpg)

Doing the same thing for rule 110, the And+Xor expression is

![](image_rsrc156.jpg)

the evaluation graph is

![](image_rsrc157.jpg)

and the rule array is:

![](image_rsrc158.jpg)

And at least with the evaluation graph as a guide, we can readily “see what’s happening” here. But the rule array we’re using is considerably larger than our minimal solutions above—or even than the solutions we found by adaptive evolution.

It’s a typical situation that one sees in many other kinds of systems (like for example [sorting networks](https://www.wolframscience.com/nks/notes-12-8--sorting-networks/)): it’s possible to have a “constructed solution” that has clear structure and regularity and is “understandable”. But minimal solutions—or ones found by adaptive evolution—tend to be much smaller. But they almost always look in many ways random, and aren’t readily understandable or interpretable.

So far, we’ve been looking at rule arrays that compute specific functions. But in getting a sense of what rule arrays can do, we can consider rule arrays that are “[programmable](https://www.wolframscience.com/nks/chap-11--the-notion-of-computation/)”, in that their input specifies what function they should compute. So here, for example, is an And+Xor rule array—found by adaptive evolution—that takes the “bit pattern” of any (even) Boolean function as input on the left, then applies that Boolean function to the inputs on the right:

![](image_rsrc159.jpg)

And with this same rule array we can now compute any possible (even) Boolean function. So here, for example, it’s evaluating [Or](https://reference.wolfram.com/language/ref/And.html):

![](image_rsrc15A.jpg)

## Other Kinds of Models and Setups

Our general goal here has been to set up models that capture the most essential features of neural nets and machine learning—but that are simple enough in their structure that we can readily “look inside” and get a sense of what they are doing. Mostly we’ve concentrated on rule arrays as a way to provide a minimal analog of standard “perceptron-style” feed-forward neural nets. But what about other architectures and setups?

In effect, our rule arrays are “spacetime-inhomogeneous” generalizations of cellular automata—in which adaptive evolution determines which rule (say from a finite set) should be used at every (spatial) position and every (time) step. A different idealization (that in fact we already used in [one section above](#c5C.xhtml)) is to have an ordinary homogeneous cellular automaton—but with a single “global rule” determined by adaptive evolution. Rule arrays are the analog of feed-forward networks in which a given rule in the rule array is in effect used only once as data “flows through” the system. Ordinary homogeneous cellular automata are like recurrent networks in which a single stream of data is in effect subjected over and over again to the same rule.

There are various interpolations between these cases. For example, we can imagine a “layered rule array” in which the rules at different steps can be different, but those on a given step are all the same. Such a system can be viewed as an idealization of a convolutional neural net in which a given layer applies the same kernel to elements at all positions, but different layers can apply different kernels.

A layered rule array can’t encode as much information as a general rule array. But it’s still able to show machine-learning-style phenomena. And here, for example, is adaptive evolution for a layered And+Xor rule array progressively solving the problem of generating a pattern that lives for exactly 30 steps:

![](image_rsrc15B.jpg)

One could also imagine “vertically layered” rule arrays, in which different rules are used at different positions, but any given position keeps running the same rule forever. However, at least for the kinds of problems we’ve considered here, it doesn’t seem sufficient to just be able to pick the positions at which different rules are run. One seems to either need to change rules at different (time) steps, or one needs to be able to adaptively evolve the underlying rules themselves.

Rule arrays and ordinary cellular automata share the feature that the value of each cell depends only on the values of neighboring cells on the step before. But in neural nets it’s standard for the value at a given node to depend on the values of lots of nodes on the layer before. And what makes this straightforward in neural nets is that (weighted, and perhaps otherwise transformed) values from previous nodes are taken to be combined just by simple numerical addition—and addition (being n\-ary and associative) can take any number of “inputs”. In a cellular automaton (or Boolean function), however, there’s always a definite number of inputs, determined by the structure of the function. In the most straightforward case, the inputs come only from nearest-neighboring cells. But there’s no requirement that this is how things need to work—and for example we can pick any “local template” to bring in the inputs for our function. This template could either be the same at every position and every step, or it could be picked from a certain set differently at different positions—in effect giving us “template arrays” as well as rule arrays.

So what about having a fully connected network, as we did in our very first neural net examples above? To set up a discrete analog of this we first need some kind of discrete n\-ary associative “accumulator” function to fill the place of numerical addition. And for this [we could pick a function like](https://www.wolframscience.com/nks/notes-12-9--properties-of-logical-primitives/) [And](http://reference.wolfram.com/language/ref/And.html), [Or](http://reference.wolfram.com/language/ref/Or.html), [Xor](http://reference.wolfram.com/language/ref/Xor.html)—or [Majority](http://reference.wolfram.com/language/ref/Majority.html). And if we’re not just going to end up with the same value at each node on a given layer, we need to set up some analog of a weight associated with each connection—which we can achieve by applying either [Identity](http://reference.wolfram.com/language/ref/Identity.html) or [Not](http://reference.wolfram.com/language/ref/Not.html) (i.e. flip or not) to the value flowing through each connection.

Here’s an example of a network of this type, trained to compute the ![](image_rsrc15C.jpg)function we discussed above:

![](image_rsrc15D.jpg)

There are just two kinds of connections here: flip and not. And at each node we’re computing the majority function—giving value 1 if the majority of its inputs are 1, and 0 otherwise. With the “one-hot encoding” of input and output that we used before, here are a few examples of how this network evaluates our function:

![](image_rsrc15E.jpg)

This was trained just using 1000 steps of single-point mutation applied to the connection types. The loss systematically goes down—but the configuration of the connection types continues to look quite random even as it achieves zero loss (i.e. even after the function has been completely learned):

![](image_rsrc15F.jpg)

In what we’ve just done we assume that all connections continue to be present, though their types (or effectively signs) can change. But we can also consider a network where connections can end up being zeroed out during training—so that they are effectively no longer present.

Much of what we’ve done here with machine learning has centered around trying to learn transformations of the form x ![](image_rsrc15G.jpg)f\[x\]. But another typical application of machine learning is autoencoding—or in effect learning how to compress data representing a certain set of examples. And once again it’s possible to do such a task using rule arrays, with learning achieved by a series of single-point mutations.

As a starting point, consider training a rule array (of cellular automaton rules 4 and 146) to reproduce unchanged a block of black cells of any width. One might have thought this would be trivial. But it’s not, because in effect the initial data inevitably gets “ground up” inside the rule array, and has to be reconstituted at the end. But, yes, it’s nevertheless possible to train a rule array to at least roughly do this—even though once again the rule arrays we find that manage to do this look quite random:

![](image_rsrc15H.jpg)

But to set up a nontrivial autoencoder let’s imagine that we progressively “squeeze” the array in the middle, creating an increasingly narrow “bottleneck” through which the data has to flow. At the bottleneck we effectively have a compressed version of the original data. And we find that at least down to some width of bottleneck, it’s possible to create rule arrays that—with reasonable probability—can act as successful autoencoders of the original data:

![](image_rsrc15J.jpg)

The success of LLMs has highlighted the use of machine learning for sequence continuation—and the effectiveness of transformers for this. But just as with other neural nets, the forms of transformers that are used in practice are typically very complicated. But can one find a minimal model that nevertheless captures the “essence of transformers”?

Let’s say that we have a sequence that we want to continue, like:

![](image_rsrc15K.jpg)

We want to encode each possible value by a vector, as in

![](image_rsrc15M.jpg)

so that, for example, our original sequence is encoded as:

![](image_rsrc15N.jpg)

Then we have a “head” that reads a block of consecutive vectors, picking off certain values and feeding pairs of them into And and Xor functions, to get a vector of Boolean values:

![](image_rsrc15P.jpg)

Ultimately this head is going to “slide” along our sequence, “predicting” what the next element in the sequence will be. But somehow we have to go from our vector of Boolean values to (probabilities of) sequence elements. Potentially we might be able to do this just with a rule array. But for our purposes here we’ll use a fully connected single-layer [Identity](https://reference.wolfram.com/language/ref/Identity.html)+[Not](https://reference.wolfram.com/language/ref/Not.html) network in which at each output node we just find the sum of the number of values that come to it—and treat this as determining (through a [softmax](https://reference.wolfram.com/language/ref/SoftmaxLayer.html)) the probability of the corresponding element:

![](image_rsrc15R.jpg)

In this case, the element with the maximum value is 5, so at “zero temperature” this would be our “best prediction” for the next element.

To train this whole system we just make a sequence of random point mutations to everything, keeping mutations that don’t increase the loss (where the loss is basically the difference between predicted next values and actual next values, or, more precisely, the “[categorical cross-entropy](https://reference.wolfram.com/language/ref/CrossEntropyLossLayer.html)”). Here’s how this loss progresses in a typical such training:

![](image_rsrc15S.jpg)

At the end of this training, here are the components of our minimal transformer:

![](image_rsrc15T.jpg)

First come the encodings of the different possible elements in the sequence. Then there’s the head, here shown applied to the encoding of the first elements of the original sequence. Finally there’s a single-layer discrete network that takes the output from the head, and deduces relative probabilities for different elements to come next. In this case the highest-probability prediction for the next element is that it should be element 6.

To do the analog of an LLM we start from some initial “prompt”, i.e. an initial sequence that fits within the width (“context window”) of the head. Then we progressively apply our minimal transformer, for example at each step taking the next element to be the one with the highest predicted probability (i.e. operating “at zero temperature”). With this setup the collection of “prediction strengths” is shown in gray, with the “best prediction” shown in red:

![](image_rsrc15U.jpg)

Running this even far beyond our original training data, we see that we get a “prediction” of a continued sine wave:

![](image_rsrc15V.jpg)

As we might expect, the fact that our minimal transformer can make such a plausible prediction relies on the simplicity of our sine curve. If we use “more complicated” training data, such as the “mathematically defined” (![](image_rsrc15W.jpg)) blue curve in

![](image_rsrc15X.jpg)

the result of training and running a minimal transformer is now:

![](image_rsrc15Y.jpg)![](image_rsrc15Z.jpg)

And, not surprisingly, it can’t “figure out the computation” to correctly continue the curve. By the way, different training runs will involve different sequences of mutations, and will yield different predictions (often with periodic “hallucinations”):

![](image_rsrc160.jpg)

In looking at “perceptron-style” neural nets we wound up using rule arrays—or, in effect, spacetime-inhomogeneous cellular automata—as our minimal models. Here we’ve ended up with a slightly more complicated minimal model for transformer neural nets. But if we were to simplify it further, we would end up not with something like a cellular automaton but instead with something like a [tag system](https://www.wolframscience.com/nks/p93--tag-systems/), in which one has a sequence of elements, and at each step removes a block from the beginning, and—depending on its form—adds a certain block at the end, as in:

![](image_rsrc161.jpg)

And, yes, such systems [can generate extremely complex behavior](https://writings.stephenwolfram.com/2021/03/after-100-years-can-we-finally-crack-posts-problem-of-tag-a-story-of-computational-irreducibility-and-more/)—reinforcing the idea (that we have repeatedly seen here) that machine learning works by selecting complexity that aligns with goals that have been set.

And along these lines, one can consider all sorts of different computational systems as foundations for machine learning. Here we’ve been looking at cellular-automaton-like and tag-system-like examples. But for example our [Physics Project](https://www.wolframphysics.org/) has shown us the power and flexibility of systems based on [hypergraph rewriting](https://www.wolframphysics.org/technical-introduction/basic-form-of-models/). And from what we’ve seen here, it seems very plausible that something like hypergraph rewriting can serve as a yet more powerful and flexible substrate for machine learning.

## So in the End, What’s Really Going On in Machine Learning?

There are, I think, several quite striking conclusions from what we’ve been able to do here. The first is just that models much simpler than traditional neural nets seem capable of capturing the essential features of machine learning—and indeed these models may well be the basis for a new generation of practical machine learning.

But from a scientific point of view, one of the things that’s important about these models is that they are simple enough in structure that it’s immediately possible to produce visualizations of what they’re doing inside. And studying these visualizations, the most immediately striking feature is how complicated they look.

It could have been that machine learning would somehow “crack systems”, and find simple representations for what they do. But that doesn’t seem to be what’s going on at all. Instead what seems to be happening is that machine learning is in a sense just “hitching a ride” on the [general richness of the computational universe](https://www.wolframscience.com/nks/chap-3--the-world-of-simple-programs/). It’s not “specifically building up behavior one needs”; rather what it’s doing is to harness behavior that’s “already out there” in the computational universe.

The fact that this could possibly work relies on the crucial—and at first unexpected—fact that in the computational universe even very simple programs can ubiquitously produce all sorts of complex behavior. And the point then is that this behavior has enough richness and diversity that it’s possible to find instances of it that align with machine learning objectives one’s defined. In some sense what machine learning is doing is to “mine” the computational universe for programs that do what one wants.

It’s not that machine learning nails a specific precise program. Rather, it’s that in typical successful applications of machine learning there are lots of programs that “do more or less the right thing”. If what one’s trying to do involves something computationally irreducible, machine learning won’t typically be able to “get well enough aligned” to correctly “get through all the steps” of the irreducible computation. But it seems that [many “human-like tasks”](https://writings.stephenwolfram.com/2023/02/what-is-chatgpt-doing-and-why-does-it-work/#models-for-human-like-tasks) that are the particular focus of modern machine learning can successfully be done.

And by the way, one can expect that with the minimal models explored here, it becomes more feasible to get a real characterization of what kinds of objectives can successfully be achieved by machine learning, and what cannot. Critical to the operation of machine learning is not only that there exist programs that can do particular kinds of things, but also that they can realistically be found by adaptive evolution processes.

In what we’ve done here we’ve often used what’s essentially the very simplest possible process for adaptive evolution: a sequence of point mutations. And what we’ve discovered is that even this is usually sufficient to lead us to satisfactory machine learning solutions. It could be that our paths of adaptive evolution would always be getting stuck—and not reaching any solution. But the fact that this doesn’t happen seems [crucially connected to the computational irreducibility](https://writings.stephenwolfram.com/2024/05/why-does-biological-evolution-work-a-minimal-model-for-biological-evolution-and-other-adaptive-processes/#the-fitness-landscape) that’s ubiquitous in the systems we’re studying, and that leads to effective randomness that with overwhelming probability will “give us a way out” of anywhere we got stuck.

In some sense computational irreducibility “levels the playing field” for different processes of adaptive evolution, and lets even simple ones be successful. Something similar seems to happen for the whole framework we’re using. Any of a wide class of systems seem capable of successful machine learning, even if they don’t have the detailed structure of traditional neural nets. We can see this as a typical reflection of the [Principle of Computational Equivalence](https://www.wolframscience.com/nks/chap-12--the-principle-of-computational-equivalence/): that even though systems may differ in their details, they are ultimately all equivalent in the computations they can do.

The phenomenon of computational irreducibility leads to a fundamental tradeoff, of [particular importance in thinking about things like AI](https://writings.stephenwolfram.com/2023/03/will-ais-take-all-our-jobs-and-end-human-history-or-not-well-its-complicated/). If we want to be able to know in advance—and broadly guarantee—what a system is going to do or be able to do, we have to set the system up to be computationally reducible. But if we want the system to be able to make the richest use of computation, it’ll inevitably be capable of computationally irreducible behavior. And it’s the same story with machine learning. If we want machine learning to be able to do the best it can, and perhaps give us the impression of “achieving magic”, then we have to allow it to show computational irreducibility. And if we want machine learning to be “understandable” it has to be computationally reducible, and not able to access the full power of computation.

At the outset, though, it’s not obvious whether machine learning actually has to access such power. It could be that there are computationally reducible ways to solve the kinds of problems we want to use machine learning to solve. But what we’ve discovered here is that even in solving very simple problems, the adaptive evolution process that’s at the heart of machine learning will end up sampling—and using—what we can expect to be computationally irreducible processes.

Like biological evolution, machine learning is fundamentally about finding things that work—without the constraint of “understandability” that’s forced on us when we as humans explicitly engineer things step by step. Could one imagine constraining machine learning to make things understandable? To do so would effectively prevent machine learning from having access to the power of computationally irreducible processes, and from the evidence here it seems unlikely that with this constraint the kind of successes we’ve seen in machine learning would be possible.

So what does this mean for the “science of machine learning”? One might have hoped that one would be able to “look inside” machine learning systems and get detailed narrative explanations for what’s going on; that in effect one would be able to “explain the mechanism” for everything. But what we’ve seen here suggests that in general nothing like this will work. All one will be able to say is that somewhere out there in the computational universe there’s some (typically computationally irreducible) process that “happens” to be aligned with what we want.

Yes, we can make general statements—strongly based on computational irreducibility—about things like the findability of such processes, say by adaptive evolution. But if we ask “How in detail does the system work?”, there won’t be much of an answer to that. Of course we can trace all its computational steps and see that it behaves in a certain way. But we can’t expect what amounts to a “global human-level explanation” of what it’s doing. Rather, we’ll basically just be reduced to looking at some computationally irreducible process and observing that it “happens to work”—and we won’t have a high-level explanation of “why”.

But there is one important loophole to all this. Within any computationally irreducible system, there are always inevitably pockets of computational reducibility. And—as I’ve [discussed at length particularly in connection with our Physics Project](https://writings.stephenwolfram.com/2023/12/observer-theory/)—it’s these pockets of computational reducibility that allow computationally bounded observers like us to identify things like “laws of nature” from which we can build “human-level narratives”.

So what about machine learning? What pockets of computational reducibility show up there, from which we might build “human-level scientific laws”? Much as with the emergence of “simple continuum behavior” from computationally irreducible processes happening at the level of molecules in a gas or ultimate discrete elements of space, we can expect that at least certain computationally reducible features will be more obvious when one’s dealing with larger numbers of components. And indeed in sufficiently large machine learning systems, it’s routine to see smooth curves and apparent regularity when one’s looking at the kind of aggregated behavior that’s probed by things like training curves.

But the question about pockets of reducibility is always whether they end up being aligned with things we consider interesting or useful. Yes, it could be that machine learning systems would exhibit some kind of collective (“EEG-like”) behavior. But what’s not clear is whether this behavior will tell us anything about the actual “information processing” (or whatever) that’s going on in the system. And if there is to be a “science of machine learning” what we have to hope for is that we can find in machine learning systems pockets of computational reducibility that are aligned with things we can measure, and care about.

So given what we’ve been able to explore here about the foundations of machine learning, what can we say about the [ultimate power of machine learning systems](https://writings.stephenwolfram.com/2024/03/can-ai-solve-science/)? A key observation has been that machine learning works by “piggybacking” on computational irreducibility—and in effect by finding “natural pieces of computational irreducibility” that happen to fit with the objectives one has. But what if those objectives involve computational irreducibility—as they often do when one’s dealing with a process that’s been successfully formalized in computational terms (as in math, exact science, computational X, etc.)? Well, it’s not enough that our machine learning system “uses some piece of computational irreducibility inside”. To achieve a particular computationally irreducible objective, the system would have to do something closely aligned with that actual, specific objective.

It has to be said, however, that by laying bare more of the essence of machine learning here, it becomes easier to at least define the issues of merging typical “formal computation” with machine learning. Traditionally there’s been a tradeoff between the computational power of a system and its trainability. And indeed in terms of what we’ve seen here this seems to reflect the sense that “larger chunks of computational irreducibility” are more difficult to fit into something one’s incrementally building up by a process of adaptive evolution.

So how should we ultimately think of machine learning? In effect its power comes from leveraging the “natural resource” of computational irreducibility. But when it uses computational irreducibility it does so by “foraging” pieces that happen to advance its objectives. Imagine one’s building a wall. One possibility is to fashion bricks of a particular shape that one knows will fit together. But another is just to look at stones one sees lying around, then to build the wall by fitting these together as best one can.

And if one then asks “Why does the wall have such-and-such a pattern?” the answer will end up being basically “Because that’s what one gets from the stones that happened to be lying around”. There’s no overarching theory to it in itself; it’s just a reflection of the resources that were out there. Or, in the case of machine learning, one can expect that what one sees will be to a large extent a reflection of the raw characteristics of computational irreducibility. In other words, the foundations of machine learning are as much as anything rooted in the [science of ruliology](https://writings.stephenwolfram.com/2021/09/charting-a-course-for-complexity-metamodeling-ruliology-and-more/#the-pure-basic-science-of-ruliology). And it’s in large measure to that science we should look in our efforts to understand more about “what’s really going on” in machine learning, and quite possibly also in neuroscience.

## Historical & Personal Notes

In some ways it seems like a quirk of intellectual history that the kinds of foundational questions I’ve been discussing here weren’t already addressed long ago—and in some ways it seems like an inexorable consequence of the only rather recent development of certain intuitions and tools.

The idea that the brain is fundamentally made of connected nerve cells was considered in the latter part of the nineteenth century, and took hold in the first decades of the twentieth century—with the [formalized concept of a neural net](https://www.wolframscience.com/nks/notes-10-12--history-of-ideas-about-thinking/) that operates in a computational way emerging in full form in the work of Warren McCulloch and Walter Pitts in 1943. By the late 1950s there were hardware implementations of neural nets (typically for image processing) in the form of “perceptrons”. But despite early enthusiasm, practical results were mixed, and at the end of the 1960s it was announced that simple cases amenable to mathematical analysis had been “solved”—leading to a general belief that “neural nets couldn’t do anything interesting”.

Ever since the 1940s there had been a trickle of general analyses of neural nets, particularly using methods from physics. But typically these analyses ended up with things like continuum approximations—that could say little about the information-processing aspects of neural nets. Meanwhile, there was an ongoing undercurrent of belief that somehow neural networks would both explain and reproduce how the brain works—but no methods seemed to exist to say quite how. Then at the beginning of the 1980s there was a resurgence of interest in neural networks, coming from several directions. Some of what was done concentrated on very practical efforts to get neural nets to do particular “human-like” tasks. But some was more theoretical, typically using methods from statistical physics or dynamical systems.

Before long, however, the buzz died down, and for several decades only a few groups were left working with neural nets. Then in 2011 came a surprise breakthrough in using neural nets for image analysis. It was an important practical advance. But it was driven by technological ideas and development—not any significant new theoretical analysis or framework.

And this was also the pattern for almost all of what followed. People spent great effort to come up with neural net systems that worked—and [all sorts of folklore](https://writings.stephenwolfram.com/2023/02/what-is-chatgpt-doing-and-why-does-it-work/#the-practice-and-lore-of-neural-net-training) grew up about how this should best be done. But there wasn’t really even an attempt at an underlying theory; this was a domain of engineering practice, not basic science.

And it was in this tradition that [ChatGPT burst onto the scene](https://writings.stephenwolfram.com/2023/02/what-is-chatgpt-doing-and-why-does-it-work/) in late 2022. Almost everything about LLMs seemed to be complicated. Yes, there were empirically some large-scale regularities (like scaling laws). And I quickly suspected that the success of LLMs was a [strong hint of general regularities in human language](https://writings.stephenwolfram.com/2023/02/what-is-chatgpt-doing-and-why-does-it-work/#what-really-lets-chatgpt-work) that hadn’t been clearly identified before. But beyond a few outlier examples, almost nothing about “what’s going on inside LLMs” has seemed easy to decode. And efforts to put “strong guardrails” on the operation of the system—in effect so as to make it in some way “predictable” or “understandable”—typically seem to substantially decrease its power (a point that now makes sense in the context of computational irreducibility).

My own interaction with machine learning and neural nets [began in 1980](https://writings.stephenwolfram.com/2015/05/wolfram-language-artificial-intelligence-the-image-identification-project/#personal-backstory) when I was developing my [SMP symbolic computation system](https://writings.stephenwolfram.com/2013/06/there-was-a-time-before-mathematica/), and wondering whether it might be possible to generalize the symbolic pattern-matching foundations of the system to some kind of “fuzzy pattern matching” that would be closer to human thinking. I was aware of neural nets but thought of them as semi-realistic models of brains, not for example as potential sources of algorithms of the kind I imagined might “solve” fuzzy matching.

And it was partly as a result of trying to understand the essence of systems like neural nets that [in 1981 I came up with](https://www.wolframscience.com/nks/p17--the-personal-story-of-the-science-in-this-book/) what I later learned could be thought of as one-dimensional cellular automata. Soon I was deeply involved in studying cellular automata and developing a new intuition about how complex behavior could arise even from simple rules. But when I learned about recent efforts to make idealized models of neural nets using ideas from statistical mechanics, I was at least curious enough to set up simulations to try to understand more about these models.

But what I did wasn’t a success. I could neither get the models to do anything of significant practical interest—nor did I manage to derive any good theoretical understanding of them. I kept wondering, though, what relationship there might be between cellular automata that “just run”, and systems like neural nets that can also “learn”. And in fact [in 1985 I tried to make a minimal cellular-automaton-based model](https://content.wolfram.com/sw-publications/2020/07/approaches-complexity-engineering.pdf) to explore this. It was what I’m now calling a “vertically layered rule array”. And while in many ways I was already asking the right questions, this was an unfortunate specific choice of system—and my experiments on it didn’t reveal the kinds of phenomena we’re now seeing.

Years went by. I wrote a [section on “Human Thinking”](https://www.wolframscience.com/nks/chap-10--processes-of-perception-and-analysis/#sect-10-12--human-thinking) in [A New Kind of Science](https://www.wolframscience.com/nks/), that discussed the possibility of simple foundational rules for the essence of thinking, and even included a minimal discrete analog of a neural net. At the time, though, I didn’t develop these ideas. By 2017, though, 15 years after the book was published—and knowing about the breakthroughs in deep learning—I had begun to [think more concretely about neural nets as getting their power](https://writings.stephenwolfram.com/2017/05/a-new-kind-of-science-a-15-year-view/#machine-learning-and-the-neural-net-renaissance) by sampling programs from across the computational universe. But still I didn’t see quite how this would work.

Meanwhile, there was a new intuition emerging from practical experience with machine learning: that if you “bashed” almost any system “hard enough”, it would learn. Did that mean that perhaps one didn’t need all the details of neural networks to successfully do machine learning? And could one perhaps make a system whose structure was simple enough that its operation would for example be accessible to visualization? I particularly wondered about this when I was writing [an exposition of ChatGPT and LLMs in early 2023](https://writings.stephenwolfram.com/2023/02/what-is-chatgpt-doing-and-why-does-it-work/). And I kept talking about “LLM science”, but didn’t have much of a chance to work on it.

But then, a few months ago, as part of an [effort to understand the relation between what science does and what AI does](https://writings.stephenwolfram.com/2024/03/can-ai-solve-science/), I tried a kind of [“throwaway experiment”](https://writings.stephenwolfram.com/2024/03/can-ai-solve-science/#exploring-spaces-of-systems)—which, to my considerable surprise, seemed to successfully capture some of the essence of what [makes biological evolution possible](https://writings.stephenwolfram.com/2024/05/why-does-biological-evolution-work-a-minimal-model-for-biological-evolution-and-other-adaptive-processes/). But what about other adaptive evolution—and in particular, machine learning? The models that seemed to be needed were embarrassingly close to [what I’d studied in 1985](https://content.wolfram.com/sw-publications/2020/07/approaches-complexity-engineering.pdf). But now I had a new intuition—and, thanks to [Wolfram Language](https://www.wolfram.com/language/), vastly better tools. And the result has been my effort here.

Of course this is only a beginning. But I’m excited to be able to see what I consider to be the beginnings of foundational science around machine learning. Already there are clear directions for practical applications (which, needless to say, I plan to explore). And there are signs that perhaps we may finally be able to understand just why—and when—the “magic” of machine learning works.

## Thanks

Thanks to Richard Assar of the [Wolfram Institute](https://www.wolframinstitute.org/) for extensive help. Thanks also to Brad Klee, Tianyi Gu, Nik Murzin and Max Niederman for specific results, to George Morgan and others at [Symbolica](https://www.symbolica.ai/) for their early interest, and to Kovas Boguta for suggesting many years ago to link machine learning to the ideas in A New Kind of Science.