```
dataset = dataset.flat_map(
  lambda filename: (
    tf.data.TextLineDataset(filename)
    .skip(1)
    .filter(lambda line:
      tf.not_equal(tf.strings.substr(line, 0, 1),
      "#"))
```

```
iterator = dataset.make_one_shot_iterator()
next_element = iterator.get_next()
```

```
with tf.Session() as sess:
  print(sess.run(next_element))
  print(sess.run(next_element))
```

Listing 6.18 defines the variable filenames as an array of text filenames, in this case consists of just one file called comments.txt (shown in Listing 6.17). Next, the variable dataset is initialized as a TF Dataset that contains the contents of comments.txt.

The next section of Listing 6.18 is a code block that explains the purpose of the next code block, which involves a moderately complex set of operations that are executed via method chaining in order to transform the contents of the variable dataset.

Specifically, the dataset.flat_map() operator “flattens” the contents of its input, which means the input files (remember, it is just comments.txt in this example) are treated as an input stream. Second, the lambda expression “maps” each filename to an instance of the TF tf.data.TextLineDataset class. Third, the skip(1) operator skips the first line of each input file (skip(n) would skip the first n lines). Fourth, the filter() operator returns each input line (which is a line of text from each file) if and only if the input line does not start with the "## character character.