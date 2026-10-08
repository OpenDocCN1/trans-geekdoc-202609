```
random.randrange(10) # choose randomly from range(10) = [0, 1, ..., 9]
random.randrange(3, 6) # choose randomly from range(3, 6) = [3, 4, 5]
```

There are a few more methods that you'll find useful. For example,
cient. random.shuffle reorganizes the elements of a list:
If you want to randomly select a single element from a list you can apply
random.choice:

```
my_best_friend = random.choice(["Alice", "Bob", "Charlie"] # "Bob" for me
```

And if you want to randomly select a sample of elements
replacement, you can apply random.sample:
To select a sample of elements with replacement, you can set multiple calls to
random.choice:

```
four_with_replacement = [random.choice(range(10))]
for _ in range(4)
# [9, 4, 4, 2]
```

# Regular Expressions

Regular expressions provide a means of searching text. There are probably
helpful but also complex, so much that there are a bunch of books written
about them. You will learn more about them; the few times we encounter
them; there are a few examples, below them are some examples of how to apply
them in Python:

```
import re

print all([ # all of these are true, because
not re.match("a", "cat"), # * 'cat' doesn't start with 'a'
re.search("a", "cat"), # * 'cat' has an 'a' in it
not re.search("c", "dog"), # * 'dog' doesn't have a 'c' in it
3 = len(re.split("lab", "carbs")), # * split on a or b to ['c','r','n','s']
"R-D" = re.sub("[0-9]", "-\-", "R2D2") # * replace digits with dashes
]) prints True
```

# Object-oriented Programming

Python allows you to define classes that wrap data and the functions that
work on them. Sometimes, you'll use them to make your code cleaner and
simpler. It's probably easier to describe them by creating a heavily annotated