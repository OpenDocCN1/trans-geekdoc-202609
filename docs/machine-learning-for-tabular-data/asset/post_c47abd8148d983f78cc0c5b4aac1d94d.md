
# CHAPTER 8 Getting started with deep learning with tabular data

concerning, and one has to wonder how the elaborate set of installs shown in listing 8.15 will make it possible to run Lightning experiments in Colab. Table 8.3 shows a summary of the pros and cons of the Keras and Lightning Flash solutions to the Airbnb NYC problem.

Table 8.3 Summary of the pros and cons of the Keras and TabNet solutions

| Keras | Lightning Flash |
|---|---|
| Pro | Large community using the framework means that it's easy to find solutions to common problems. Simple summary statement to show the layers in the model | Simple statements to define and train the model. Don't need to explicitly define a pipeline—need to identify the categorical and continuous columns. |
| Con | No built-in support for tabular data, which means the model definition needs to be hard-coded. | To get in Colab, you need a very specific order and level of installs. Does not seem to be widely used, at least with Colab. Out of the box, test accuracy was worse than other solutions. |

So far in this chapter we have applied three deep learning with tabular data stacks to solve the Airbnb NYC price prediction problem and compared the pros and cons of each solution. In this section, we review an overall comparison of all the stacks we exercised in this chapter.

## 8.5 Overall comparison of the stacks

We have looked at a total of four deep learning for tabular data stacks. Table 8.4 summarizes the performance of all of these stacks on a default Colab setup, with a standard Colab runtime for the deep learning solutions.

Table 8.4 Summary of accuracy and running time of the deep learning with tabular data stacks (plus XGBoost) for the Airbnb price prediction problem

| Test Accuracy | running time |
|---|---|
| TensorFlow with Keras | 81% | 16 seconds |
| fastai with PyTorch | 83% | 69 seconds |
| TabNet with PyTorch | 81% | 58 seconds |
| Lightning Flash with PyTorch | TBD | 14 seconds |
| XGBoost | 79% | 14 seconds |

It is important to note here that for the purposes of this comparison we didn't tune any of the approaches. We wanted a genuine "apples-to-apples" comparison of how the approaches compare to the Keras baseline without additional tuning. In subsequent chapters, we will discuss some of the tuning that can be done to get optimal results from a deep learning solution.

For accuracy, fastai is slightly better than the other stacks. For execution time, Lightning Flash is the slowest. If we compare XGBoost with any of the deep learning solutions, which is best? But we can answer this question now: it's a straight-up comparison between deep learning and gradient boosting for the sake of simplicity and overall performance, gradient boosting approaches like XGBoost are currently better than any deep learning solutions for most data. There are cases where it is worthwhile to explore one of the deep learning solutions, and we will review these use cases in chapter 9.

If you decide to use a deep learning solution for the tabular data problem explored so far, which one should you use? Here is our overall advice:

- If you are new to deep learning and are primarily interested in exploring tabular data, fastai is the best choice. It has a big enough community that you are not likely to be stuck. Fastai includes many convenience features to make it easy to rapidly prototype your solution. However, if you need to move your solution to production, fastai is probably not your best choice because it is not commonly used in production.
- If you are already comfortable with deep learning and need to get an application into production, we recommend the Keras stack. First, TensorFlow, the low-level component of the stack, is most commonly in industry. Second, Keras has a huge user community. While Keras does not have native support for tabular data the same way fastai does, Keras is high-level enough to lend itself to tabular data problems. This advice may change as more people use deep learning with tabular data, as TabNet on PyTorch could mature and become the default choice. However, looking at the current state of art, we recommend fastai for beginners and Keras for people who are more experienced and need to proceed to production rapidly.

In the next section we will discuss the stacks that didn't explore. You may have asked why we chose three particular stacks (fastai, TabNet, and Lightning Flash) to solve the Airbnb NYC problem and didn't explore the other options, such as TabNet on TensorFlow, SAINT, or PyTorch Tabular. In this section,

| TensorFlow Ecosystem | PyTorch Ecosystem |
|---|---|---|
| Low-level framework | TensorFlow | PyTorch |
| High-level API | Keras | Lightning |
| Tabular data library | TabNet | SAINT |
| | DeepTables | PyTorch Tabular |
| | | fastai |
| | | Lightning Flash |

**Figure 8.16** The stacks didn't explore

There are a couple of characteristics that the unexplored stacks have in common:

- All of the unexplored stacks involve tabular data libraries.
- We were not able to get any of the unexplored stacks to work in Colab, the environment that we needed to exercise the code examples in this book.

Our inability to get the unexplored stacks to work in Colab could be due to a number of reasons. There could theoretically be some limitations with Colab. However, Colab is a very common environment for exploration, so it's not a good sign if a library cannot be coaxed to fetch "hello world" examples for exercising the stack. For all the unexplored stacks these examples generated errors, mostly due to contradictory Python library prerequisites. It's possible that we had been more patient, or looked a little harder, we would have been able to work through the errors to get the basic examples to work in Colab. Of the stacks we did explore, Keras, fastai, and PyTorch TabNet all worked "out of the box" in Colab. Lightning Flash, on the other hand, did require some tweaking before it worked in Colab.

The difference between Lightning Flash and the unexplored stacks is it was clear that other people had tried to get Lightning Flash to work in Colab, and we could find informal documentation that showed exactly what we needed to do to get it to work in Colab. If your goal is to solve a tabular data problem with deep learning, you focus on the problem, not fiddling with conda and pip installing boutique of libraries to avoid incompatibilities. By that criteria, Keras, fastai, PyTorch TabNet, and to a lesser extent, Lightning Flash are viable choices for deep learning with tabular data in Colab. SAINT, DeepTables, PyTorch Tabular, and TabNet on are not viable for exploration in Colab because they don't work right away, and the recipes to get them to work either not exist or are not easy to find.

While it is disappointing that we were not able to exercise the Airbnb NYC price prediction problem with more of the dedicated deep learning with tabular libraries, we were still able to accomplish the goal of this chapter by exploring three deep learning with tabular data stacks. Figure 8.17 shows all the stacks that we were able to explore.

| TensorFlow Ecosystem | PyTorch Ecosystem |
|--- |--- |
| Low-level framework | TensorFlow | PyTorch |
| High-level API | Keras | Lightning |
| | | fastai |
| Tabular data library | TabNet | SAINT |
| | DeepTables | PyTorch Tabular |
| | | TabNet |
| | | Lightning Flash |

**Figure 8.17** The stacks we explored
