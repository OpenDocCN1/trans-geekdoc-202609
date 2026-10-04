# CHAPTER 8 Getting started with deep learning with tabular data

concerning, and one has to wonder how the elaborate set of installs shown in listing 8.15 will make it possible to run Lightning experiments in Colab. Table 8.3 shows a summary of the pros and cons of the Keras and Lightning Flash solutions to the Airbnb NYC problem.

Table 8.3 Summary of the pros and cons of the Keras and TabNet solutions

| Keras | Lightning Flash |
|---|---|
| Pro | Large community using the framework means that it's easy to find solutions to common problems. Simple summary statement to show the layers in the model | Simple statements to define and train the model. Don't need to explicitly define a pipeline—need to identify the categorical and continuous columns. |
| Con | No built-in support for tabular data, which means the model definition needs to be hard-coded. | To get in Colab, you need a very specific order and level of installs. Does not seem to be widely used, at least with Colab. Out of the box, test accuracy was worse than other solutions. |

So far in this chapter we have applied three deep learning with tabular data stacks to solve the Airbnb NYC price prediction problem and compared the pros and cons of each solution. In this section, we review an overall comparison of all the stacks we exercised in this chapter.

# 8.5 Overall comparison of the stacks

We have looked at a total of four deep learning for tabular data stacks. Table 8.4 summarizes the performance of all of these stacks on a default Colab setup, with a standard GPU Colab runtime option for the deep learning solutions.

Table 8.4 Summary of accuracy and running time of the deep learning with tabular data stacks (plus XGBoost) for the Airbnb listing price prediction problem

| Test Accuracy | Notebook running time |
|---|---||
| TensorFlow with Keras | 81% | 16 seconds |
| fastai with PyTorch | 83% | 69 seconds |
| TabNet with PyTorch | 81% | 568 seconds |
| Lightning Flash with PyTorch | TBD | 14 seconds |
| XGBoost | 79% | 14 seconds |