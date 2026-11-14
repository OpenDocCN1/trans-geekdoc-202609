![](bbox=[0.28, 0.095, 0.6, 0.465])

Figure 5.1 Block diagram for random forest regression model.

random forest regression is given as

\(\hat{A} = \frac{1}{k} \sum_{i=1}^{k} \hat{r}(X, V_i),\) (5.1)

where \(\hat{r}(X, V)\) is the representative tree at the end of training process, \(X\) is the set of input feature vectors, \(T\) is the collective set representing an input–output pair \(V_i = (x_1, y_1), (x_2, y_2), \dots, (x_n, y_n)\). The predicted output is averaged over \(k\) decision trees. An additional advantage of random forest regression is its insensitivity to noise due to uncorrelated trees via differential sampling of inputs. Fig. 5.1 illustrates the block diagram of random forest regression model. Decision trees are sensitive to the data on which they are trained. Changing the training data can change the predictions.

Meanwhile a common problem of overfitting persists in machine learning regression models when a well trained model captures the noise component as well. To reduce the complexities posed by overfitting, a random forest makes a compromise between flexible and inflexible models. In the training phase, each regression tree repeatedly draws a sample from the