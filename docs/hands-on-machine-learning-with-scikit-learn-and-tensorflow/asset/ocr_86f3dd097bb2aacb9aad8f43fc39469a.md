Finally, they also evaluated the parametric leaky ReLU (ReLU), where $\alpha$ is authorized to be learned during training (instead of being a hyperparameter, it becomes a parameter that can be modified by backpropagation like any other parameter). This was reported to strongly outperform ReLU on large datasets, but on smaller datasets it runs the risk of overfitting the training set.

![](bbox=[0.147, 0.196, 0.689, 0.399])

Figure 11-2. Leaky ReLU

But not least, a 2015 paper by Djork-Arné Clevert et al. proposed a new activation function called the exponential linear unit (ELU) that outperformed all the ReLU variants in their experiments: training time was reduced and the neural network better on the test set. It is represented in Figure 11-3, and Equation 11-2 shows its definition.

Equation 11-2. ELU activation function

```
$ELU_{\\alpha}(z) = \begin{cases} \alpha(exp(z) - 1) & \text{if } z < 0 \ z & \text{if } z \geq 0 \end{cases}$
```

> 6 “Fast and Accurate Deep Network Learning by Exponential Linear Units (ELUs),” D. Clevert, T. Unterthiner, S. Hochreiter (2015).

330 | Chapter 11: Training Deep Neural Networks

WOW! eBook
www.wowebook.com