# CHAPTER 2

# Dictionaries and Tables:
nThe q Fundamentals

The fundamental data structure in q is the list. We shall refer to homogeneous lists as vectors and reserve the term lists for those of type. From the first chapter, we recall that these are empty untyped lists or lists of lists. Two other fundamental data structures are dictionaries. Dictionaries in q are simple maps. They are very general and hence very powerful. Tables are where our data will reside and the data structures we will run our queries on. q supports its own rich query language which builds on top of the functional fundamentals to allow for insert, upsert, select, update and delete operations.

In this chapter we will introduce dictionaries and tables and show how, from fundamental concepts, we can construct all q structures; something in itself reveals the elegant design and close relationship between everything in q.

# 2.1 DICTIONARY

A dictionary in q is a map of two lists. The operator which maps the keys to the values is!. A dictionary is therefore defined as:

```
keys!values
```

The most common use case is a key-value pair of a symbol vector – as keys – and their corresponding numeric values:

```
mydict:`a`b`c`d!1 2 3
```

We index the dictionary using the same notation used to index vectors; we just replace integer indices with its keys:

```
mydict[`b`
```

2