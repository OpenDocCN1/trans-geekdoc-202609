tial derivatives are equal to 36 and 10, respectively, the gradient vector at this point is (36, 10). But if this were a neural network, the function would be much more complex, typically with thousands of parameters, and finding the partial derivatives by hand would be an almost impossible task. One solution could be to compute an approximation of each partial derivative by measuring how much the function's output changes when you tweak the parameter:

```
>>> w1, w2 = 5, 3
>>> eps = 1e-6
>>> (f(w1 + eps, w2) - f(w1, w2)) / eps
36.0000030705065
>>> (f(w1 + w2 + eps) - f(w1, w2)) / eps
10.00000003174137
```

Looks right! This works rather well and it is trivial to implement, but it is just an approximation, and you need to call f() at once per parameter (not twice, since we compute f(w1, w2) just once). This approach makes intractable for large neural networks. So instead should use autodiff (see Chapter 10 and ???). TensorFlow makes this pretty:

```
w1, w2 = tf.Variable(5.), tf.Variable(3)
with tf.GradientTape() as tape:
    z = f(w1, w2)
```

gradients = tape.gradient(z, [w1, w2])
 define two variables w1 and w2, then we create a tf.GradientTape context that will automatically record every operation that involves a variable, and finally ask this tape to compute the gradients of the result z with regards to both variables [w1, w2]. Let's take a look at the gradients TensorFlow computed:

```
>>> gradients
[tf.Tensor: id=828234, shape=(), dtype=float32, numpy=36.0,
 tf.Tensor: id=828229, shape=(), dtype=float32, numpy=10.0)]
```

Perfect! Not only is the result accurate (the precision is only limited by the floating point errors), but the gradient() method only goes through the computed computations once (in reverse order), no how many variables there are, so it is incredibly efficient. It's like magic!

![](bbox=[0.173, 0.743, 0.243, 0.821])

Only put the strict minimum inside the tf.GradientTape() block, to save memory. Alternatively, you can pause recording by creating a tape tf.stop_recording() block inside the tf.Gradient Tape block.

The tape is automatically erased immediately after you call its gradient() method, so you will get an exception if you try to call gradient() twice: