# PyTorch with fastai

Now that we have examined the key code areas in the fastai solution, we revisit the stack diagram to see where the fastai stack fits. Figure 8.10 shows the deep learning with tabular data stack from the example in this section. Note that the figure fastai as both a high-level API and a tabular library since fastai plays both roles in the stack.

![](bbox=[0.198, 0.193, 0.802, 0.375])

Now that we have reviewed the code in the fastai solution, in the next section we'll compare this solution to the Keras solution that we saw in chapter 3.

# 8.2.2 Comparing the fastai solution with the Keras solution

We have seen two deep learning solutions to the Airbnb NYC listing prediction problem: the Keras solution and the fastai solution. In this section, we'll compare the two solutions and revisit the pros and cons of each.

Fastai and Keras solutions make interesting comparison points because they are very different. The Keras solution contains a lot of custom code, and all the details are evident. The fastai framework infers details about the model from the dataset and makes assumptions about the defaults to use so that there aren't many parameters that we need to specify to get a working model. The benefit of this is that the fastai code is much more compact than the Keras code. In particular, the Keras solution has multiple lines of code to specify the pipeline and the details of the layers that make up the model. In fastai, we get the pipeline for free by simply specifying the transformations we applied to the input data (as shown in 8.6), and we don't need to specify the layers that make up the model. Downside the compactness of the fastai solution is that subtle problems can get introduced if we're not careful. In the previous section, we saw that if we don't explicitly convert the target column to string values, fastai will interpret we are training a regression model rather than a classification model.

Table 8.1 shows a summary of the pros and cons of the Keras and fastai solutions to the Airbnb NYC problem. If we compare the performance of the two solutions, the Keras model gets between 70% and 74% accuracy, while the fastai consistently gets around 81% accuracy.