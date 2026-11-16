strip_punc function and to convert each line of text to lowercase. This method returns a new RDD on which you can specify additional tasks to perform.

+   • RDD method flatMap uses its lambda argument to map each line of text into its words and produces a single list of words, rather than the individual lines of text. The result of flatMap is a new RDD representing all the words in Romeo and Juliet.

lick here to view code image

```
[5]: from textblob.utils import strip_punc
    tokenized = sc.textFile('RomeoAndJuliet.txt')\
    .map(lambda line: strip_punc(line, all=True).lower())\
    .flatMap(lambda line: line.split())
```

# Removing the Stop Words

Next, let's use RDD method filter to create a new RDD with no stop words remaining:

lick here to view code image

```
[6]: filtered = tokenized.filter(lambda word: word not in stop_words)
```

# Counting Each Remaining Word

Now that we have only the non-stop-words, we can count the number of occurrences of each word. To do so, we first map each word to a tuple containing the word and a count of 1. This is similar to what we did in Hadoop MapReduce. Spark will distribute the reduction task across the cluster's nodes. On the resulting RDD, we then call the method reduceByKey, passing the operator module's add function as an argument. This tells method reduceByKey to add the counts for tuples that contain the same word (the key):

lick here to view code image

```
[7]: from operator import add
    word_counts = filtered.map(lambda word: (word, 1)).reduceByKey(add)
```

# Locating Words with Counts Greater Than or Equal to 60

Since there are hundreds of words in Romeo and Juliet, let's filter the RDD to keep only those words with 60 or more occurrences:

lick here to view code image

```
[8]: filtered_counts = word_counts.filter(lambda item: item[1] >= 60)
```

# Sorting and Displaying the Results

At this point, we've specified all the steps to count the words. When you call RDD method collect, Spark initiates all the processing steps we specified above and returns a list containing the final results—in this case, the tuples of words and their counts. From your perspective, everything appears to execute on one computer. However, if the SparkContext