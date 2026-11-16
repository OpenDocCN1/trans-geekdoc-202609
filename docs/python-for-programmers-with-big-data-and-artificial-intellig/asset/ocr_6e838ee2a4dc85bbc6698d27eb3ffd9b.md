```
In [12]: x = 'dog'

In [13]: type(x)
Out[13]: str
```

# Garbage Collection

Python creates objects in memory and removes them from memory as necessary. After snippet [10], the variable `x` now refers to a `float` object. The integer object from snippet [7] is no longer bound to a variable. As we'll discuss in a later chapter, Python automatically removes such objects from memory. This process—called garbage collection—helps ensure that memory is available for new objects you create.

# 2.9 INTRO TO DATA SCIENCE: BASIC DESCRIPTIVE STATISTICS

In data science, you'll often use statistics to describe and summarize your data. Here, we begin by introducing several such descriptive statistics, including:

+   • minimum—the smallest value in a collection of values.
+   • maximum—the largest value in a collection of values.
+   • range—the range of values from the minimum to the maximum.
+   • count—the number of values in a collection.
+   • sum—the total of the values in a collection.

We'll look at determining the `count` and `sum` in the next chapter. **Measures of dispersion** (also called *measures of variability*), such as *range*, help determine how spread out values are. Other measures of dispersion that we'll present in later chapters include *variance* and *standard deviation*.

# Determining the Minimum of Three Values

First, let's show how to determine the minimum of three values manually. The following script prompts for and inputs three values, uses `if` statements to determine the minimum value, then displays it.

lick here to view code image