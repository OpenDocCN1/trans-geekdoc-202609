and may be filled one entry at a time:

```
# define one key pair look up an object @here
mydict['Course Name']='Machine Learning' @here key is 'Course Name' (in
square brackets) and object is 'Machine Learning'
mydict['Department']='biomedical engineering'
mydict['Year']=2021
mydict['Number of students']=67
```

or at once using in-line notation, e.g., keyl:object1....

```
# inline definition
mydict_inline=('Course Name': 'Machine Learning', 'Department': "
biomedical engineering'. 'Year': 2021, 'Number of students': 67)
```

Like dictionaries, dictionaries are mutable, meaning objects that can be changed, as a new student added after the course started:

```
# incrementing dictionary entry
mydict['Number of students']=68
```

or, new keys may be added at a later time, e.g.,

```
# adding new dictionary entry
mydict['Student Satisfaction Score']=5
```

Keys may be any immutable type (which includes tuples):

```
# string as key (most common)
mydict['key']='val1'
#int and float as keys
mydict[5]='val2'
mydict[3.2413]='val3'
#tuple as keys
mydict[(1,2,3)]='val4'
```

However, dictionaries are unordered, it most often makes sense to use strings. Objects may be any type, including lists or other dictionaries,

```
# adding a list as new dictionary entry
mydict['student ids']=['id00001','id00006','id00015']
```

Dictionary elements may be deleted using del dict[key]. Any attempt to index a key that does not exist will raise a KeyError.

# 1.2.3 Operators

So, now that we know what classes of variable we have to play with, what types of operation can we perform on them? In this section, we will look at simple mathematical and Boolean operators.