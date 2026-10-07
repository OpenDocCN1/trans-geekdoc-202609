any). If you create a Pandas DataFrame using this dictionary and call its plot()
method, you get the learning curves shown in Figure 10-12:

```
import pandas as pd

p.DataFrame(history.history).plot(figsize=(8, 5))
plt.grid(True)
plt.gca().set_ylim(0, 1) # set the vertical range to [0-1]
plt.show()
```

![](bbox=[0.143, 0.237, 0.857, 0.553])

Figure 10-12. Learning Curves

You can see that both the training and validation accuracy steadily increase during training, while the training and validation loss decrease. Good! Moreover, the validation curves are quite close to the training curves, which means that there is not too much overfitting. In this particular case, the model performed better on the validation set than at the beginning of training this happens by chance (especially when the validation set is fairly small). However, the training set performance ends up beating the validation performance, as is generally the case when you train for long enough. You can tell that the model has not converged yet, as the validation loss is still going down, so you should probably continue training. It is as simple as calling the fit()t method again, since Keras continues training where it left off (you should be able to reach close to 89% validation accuracy).

If you are not satisfied with the performance of your model, you should go back and tune the model's hyperparameters, for example the number of layers, the number of neurons per layer, the number of activation functions we use for each hidden layer,

Implementing MLPs with Keras | WOW! eBook www.wowebook.org