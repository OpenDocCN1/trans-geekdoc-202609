iter = dataset.make_one_shot_iterator()
el = iter.get_next()

with tf.Session() as sess:
  for _ in range(len(x)):
    print("value:", sess.run(el))

Listing 6.14 initializes the variable x as a NumPy array consisting of four elements, where each element is a 1x1 array consisting of the numbers 1, 2, 3, and 4. The variable dataset is initialized as a TF Dataset that is created from the contents of the variable x.

The next portion of Listing 6.14 is a “commented out” code block consists of three lambda expressions, followed by a code snippet (shown in bold) that is a more compact way of defining the same three lambda expressions:

```
dataset = dataset.map(lambda x: x**2).map(lambda x: x+1).map(lambda x: x**3)
```

The preceding code snippet transforms each input value by doubling the value, then adding one to the first result, and then cubing the second result.

Although method chaining is a concise way to chain operators, invoking dozens of lazy operators in a single (very long) line of code can quickly become difficult to understand, whereas writing code using the “longer way” would be easier to debug.

A suggestion: start with each lazy operator in a separate line of code, and after you are satisfied that the individual results are correct, then use method chaining to combine the operators in a single line of code (up to a maximum of four or five operators).

The next code snippet defines the variable iter as a “one-shot” iterator, followed by the variable el that is populated with the first element in the variable dataset.

The final portion of Listing 6.16 contains a for loop that iterates through the transformed values and displays their values. The output from launching the code in Listing 6.14 is: