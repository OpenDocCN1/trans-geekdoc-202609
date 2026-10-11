
# Multiway Mutation Graphs

But are there, for example, And+Xor rule arrays that will compute any of the 16 possible (2-input) functions? We can’t get `Not` or any of the 8 other functions with ![](image_rsrc126.jpg)—but it turns out we can get all 8 functions with ![](image_rsrc127.jpg) (additional inputs here are assumed to be ![](image_rsrc128.jpg)):

![](image_rsrc129.jpg)

And in fact we can also set up And+Xor rule arrays for all other “even” Boolean functions. For example, here are rule arrays for the 3-input rule 30 and rule 110 Boolean functions:

![](image_rsrc12A.jpg)

It may be worth commenting that the ability to set up such rule arrays is related to [functional completeness](https://www.wolframscience.com/nks/p807--implications-for-mathematics-and-its-foundations/) of the underlying rules we’re using—though it’s not quite the same thing. Functional completeness is about setting up arbitrary formulas, that can in effect allow long-range connections between intermediate results. Here, all information has to explicitly flow through the array. But for example the functional completeness of `Nand` (r = 1/2 rule 7, ![](image_rsrc12B.jpg)) allows it to generate all Boolean functions when combined for example with `First` (r = 1/2 rule 12, ![](image_rsrc12C.jpg)), though sometimes the rule arrays required are quite large:

![](image_rsrc12D.jpg)

OK, but what happens if we try to use our adaptive evolution process—say to solve the problem of finding a pattern that survives for exactly 30 steps? Here’s a result for And+Xor rule arrays:

![](image_rsrc12E.jpg)

And here are examples of other “solutions” (none of which in this case look particularly “mechanistic” or “constructed”):

![](image_rsrc12F.jpg)

But what about learning our original `f[x] = ![](image_rsrc12G.jpg)` function? Well, first we have to decide how we’re going to represent the numbers `x` and `f[x]` in our discrete rule array system. And one approach is to do this simply in terms of the position of a black cell (“one-hot encoding”). So, for example, in this case there’s an initial black cell at a position corresponding to about `x = –1.1`. And then the result after passing through the rule array is a black cell at a position corresponding to `f[x] = 1.0`:

![](image_rsrc12H.jpg)

So now the question is whether we can find a rule array that successfully maps initial to final cell positions according to the mapping `x ![](image_rsrc12J.jpg) f[x]` we want. Well, here’s an example that comes at least close to doing this (note that the array is taken to be cyclic):

![](image_rsrc12K.jpg)

So how did we find this? Well, we just used a simple adaptive evolution process. In direct analogy to the way it’s usually done in machine learning, we set up “training examples”, here of the form:

![](image_rsrc12M.jpg)

Then we repeatedly made single-point mutations in our rule array, keeping those mutations where the total difference from all the training examples didn’t increase. And after 50,000 mutations this gave the final result above.

We can get some sense of “how we got there” by showing the sequence of intermediate results where we got closer to the goal (as opposed to just not getting further from it):

![](image_rsrc12N.jpg)

Here are the corresponding rule arrays, in each case highlighting elements that have changed (and showing the computation of `f[0]` in the arrays):

![](image_rsrc12P.jpg)

Different sequences of random mutations will lead to different rule arrays. But with the setup defined here, the resulting rule arrays will almost always succeed in accurately computing `f[x]`. Here are a few examples—in which we’re specifically showing the computation of `f[0]`:

![](image_rsrc12R.jpg)

And once again an important takeaway is that we don’t see “identifiable mechanism” in what’s going on. Instead, it looks more as if the rule arrays we’ve got just “happen” to do the computations we want. Their behavior is complicated, but somehow we can manage to “tap into it” to compute our `f[x]`.

But how robust is this computation? A key feature of typical machine learning is that it can “generalize” away from the specific examples it’s been given. It’s never been clear just how to characterize that generalization (when does an image of a cat in a dog suit start [being identified as an image of a dog](https://writings.stephenwolfram.com/2015/05/wolfram-language-artificial-intelligence-the-image-identification-project/)?). But—at least when we’re talking about classification tasks—we can think of what’s going on in terms of [basins of attraction](https://www.wolframscience.com/nks/p624--human-thinking/) that lead to attractors corresponding to our classes.

It’s all considerably easier to analyze, though, in the kind of discrete system we’re exploring here. For example, we can readily enumerate all our training inputs (i.e. all initial states containing a single black cell), and then see how frequently these cause any given cell to be black:

![](image_rsrc12S.jpg)

By the way, here’s what happens to this plot at successive “breakthroughs” during training:

![](image_rsrc12T.jpg)

But what about all possible inputs, including ones that don’t just contain a single black cell? Well, we can enumerate all of them, and compute the overall frequency for each cell in the array to be black:

![](image_rsrc12U.jpg)

As we would expect, the result is considerably “fuzzier” than what we got purely with our training inputs. But there’s still a strong trace of the discrete values for `f[x]` that appeared in the training data. And if we plot the overall probability for a given final cell to be black, we see peaks at positions corresponding to the values 0 and 1 that `f[x]` takes on:

![](image_rsrc12V.jpg)

But because our system is discrete, we can explicitly look at what outcomes occur:

![](image_rsrc12W.jpg)

The most common overall is the “meaningless” all-white state—that basically occurs when the computation from the input “never makes it” to the output. But the next most common outcomes correspond exactly to `f[x] = 0` and `f[x] = 1`. After that is the “superposition” outcome where `f[x]` is in effect “both 0 and 1”.

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
