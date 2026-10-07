The next code snippet defines the variable iterator as a “one-shot” iterator, followed by the variable next_element that is populated with the first integer in dx (which is the integer 0).

The final portion of Listing 6.12 contains a loop that executes 11 times, and during each iteration the loop prints eleven “triples” of consecutive integers, starting with the triple [0 1 2]. The output from launching the code in Listing 6.12 is:

```
[0 1 2]
[0 1 2]
[3 4 5]
[6 7 8]
[ 9 10 11]
[12 13 14]
[15 16 17]
[18 19 20]
[21 22 23]
[24 25 26]
[27 28 29]
[30 31 32]
```

![](bbox=[0.19, 0.582, 0.249, 0.623])

The companion disc contains tf-batch3.py, tf-batch4.py, and tf-batch5.py that illustrate variations of the preceding code sample. Experiment with the code by changing the hard-coded values and then see if you can correctly predict the output.

# THE TENSORFLOW MAP() OPERATOR (1)

Listing 6.13 displays the contents of tf-map.py that illustrates how to use the map() operator in TensorFlow with a one-shot iterator.