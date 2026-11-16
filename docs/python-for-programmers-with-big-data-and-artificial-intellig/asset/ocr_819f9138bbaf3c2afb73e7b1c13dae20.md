Some words have multiple meanings. For example, the words “set” and “run” have hundreds of meanings each! If you look at the dictionary.com definitions of the word “run,” you’ll see that it can be a verb, a noun, an adjective or a part of a verb phrase. An important use of POS tagging is determining a word’s meaning among its possibly many meanings. This is important for helping computers “understand” natural language.

The tags property returns a list of tuples, each containing a word and a string representing its part-of-speech tag:

lick here to view code image

```
In [7]: blob
Out[7]: TextBlob("Today is a beautiful day. Tomorrow looks like bad weather.")

n [8]: blob.tags
Out[8]:
[('Today', 'NN'),
 ('is', 'VBZ'),
 ('a', 'DT'),
 ('beautiful', 'JJ'),
 ('day', 'NN'),
 ('Tomorrow', 'NNP'),
 ('looks', 'VBZ'),
 ('like', 'IN'),
 ('bad', 'JJ'),
 ('weather', 'NN')]
```

By default, TextBlob uses a PatternTagger to determine parts-of-speech. This class uses the parts-of-speech tagging capabilities of the pattern library:

https://www.clips.uantwerpen.be/pattern

You can view the library’s 63 parts-of-speech tags at

https://www.clips.uantwerpen.be/pages/MBSP-tags

In the preceding snippet’s output:

+   - Today, day and weather are tagged as NN—a singular noun or mass noun.
+   - is and looks are tagged as VBZ—a third person singular present verb.
+   - a is tagged as DT—a determiner. 7
+   - beautiful and bad are tagged as JJ—an adjective.
+   - Tomorrow is tagged as NNP—a proper singular noun.
+   - like is tagged as IN—a subordinating conjunction or preposition.

7 https://en.wikipedia.org/wiki/Determiner.

# 11.2.4 Extracting Noun Phrases