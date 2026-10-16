```
```python
# a call that creates a function
three_adder = make_adder(3)

# using that created function
three_adder(10) == add_three(10)
```
```

Out[3]:

True

So, the good news is that *it worked*. The bad news might be that you don't know why. Let's break down what happens in line 7: `three_adder = make_adder(3)`. When we call `make_adder(3)`, we spin up the usual machinery of a function call. The 3 gets associated with the name k in `make_adder`. Then, we execute the code in `make_adder`. It does two things: defines the name `add_k`—with function stuff—and then returns `add_k`. These two steps are almost like a function that has two lines: m=10 and then `return 10`. The difference is that we are defining a name `add_k` whose value is a function, not just a simple int.

OK, so what does it mean to define `add_k`? It is a function of one argument, x. Whatever value is passed into `add_k` will be added to the k value that was passed into `make_adder`. But this particular `add_k` can never add anything else to x. From its perspective, that k is a constant value for all time. The only way to get a different `add_k` is to make another call to `make_adder` and create a different function.

Let's summarize what we get back from `make_adder`:

+   - The returned *thing* (strictly, it's a Python object) is a function with one argument.
+   - When the returned function is called, it (1) computes k plus the value it is called with and (2) returns that value.

Let's relate this back to our learning models. When we say `KNeighborsClassifier(3)` we are doing something like `make_adder(3)`. It gives us a concrete object we can `.fit` that has a 3 baked into its recipe. If we want to have 5-NN, we need a new learning machine constructed with a different call: `KNeighborsClassifier(5)`, just like constructing a `five_adder` requires a call to `make_adder(5)`. Now, in the case of `three_adder` and `five_adder` you are probably yelling at me, “Just use `add(x, y)`, dummy!” That's fine, I'm not offended. We can do that. But in the case of k-NN, we can't. The way the algorithm is designed, internally, doesn't allow it.

What is our takeaway message? I drew out the idea of fixed versus parameter-driven behavior to make the following points:

+   1. After we create a model, we don't modify the internal state of the learning machine. We can modify the values of the knobs and what we feed it with the side input tray (as we saw in Section 1.3).
+   2. The training step gives us our preferred knob settings and input-tray contents.
+   3. If we don't like the result of testing after training, we can also select an entirely different learning machine with different internals. We can choose machines that are of completely different types. We could switch from k-NN to linear regression. Or, we can stay within the same overall class of learning machines and vary a