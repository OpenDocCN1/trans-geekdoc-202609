whether their memory address is passed and shared with the function argument (pass by reference). In the former case, when the argument is changed within the function, the original variable remains unchanged. In the latter case, changing the value of the input argument will also change the value of the original variable.

In Python arguments are strictly 'passed by object', which means what happens to the variable within a function will depend on whether it is immutable or mutable. For immutable types (ints, floats, tuples, strings) the objects are immutable, hence they cannot be changed at any point whether they are in a function, or in the main body of code. Hence, in effect they will always be passed 'by value'. On the other hand if objects are mutable (lists, dictionaries) then the original values (in the main code body) can be changed if the variable is changed in place, for example:

```
def passing_by_object2(names):
    # changed in place using the += operator:
    names += ["Emma", "Maria"]
```

This will occur if you change (mutate) the objects a container (such as a dictionary/list) points to. Therefore, you should want the original object not to be modified, it is important to assign to a new variable inside the code of (even if this has the same name) e.g.,

```
def passing_by_object2(names):
    names = names + ["Emma", "Maria"]
```

By contrast, if mutating behavior is desired, but perhaps you wish to keep a copy of the original object (during debugging for example), then this can be achieved by making a copy of the original object using the copy module:

```
import copy
mylist_copy=deepcopy(mylist)
```

where modules will be specifically discussed in the next section.

# 1.7.3 Exercises

+   1. Write a Python function to multiply all the numbers in a list and return the total.¹¹¹
2. Write a function that takes a list and returns a new list, generated from the input list by randomly sampling with replacement (hint see np.choice)
    allow the user to define the length of the new array;
    modify the code to generate a set of new lists.

> 11 The code, exercises and solutions are available from github.com/MachineLearningBiomedicalApplications/notebooks.