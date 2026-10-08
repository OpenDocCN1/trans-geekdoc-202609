# Removing duplicate items from the list:

```
listNumbers = [20, 22, 24, 26, 28, 20, 30, 24] 
print ( 'Original=', listNumbers ) 
listNumbers = list(set(listNumbers)) 
print ( 'After removing duplicate=', listNumbers )
```

Resulting Output =

 'Original-', [20, 22, 24, 26, 28, 30, 24] 
 'After removing duplicate=', [20, 22, 24, 26, 28, 30] 

# Find if a list contains identical elements:

```
listOne = [20, 20, 20, 50] 
print( ' All element are duplicate in listOne ', listOne.count(listOne[0]) == len(listOne))
```

```
listTwo = [20, 20, 20, 50] 
print( ' All element are duplicate in listTwo ', listTwo.count(listTwo[0]) == len(listTwo))
```

Resulting Output =

 'All elements are duplicate in listOne', True 
 'All elements are duplicate in listTwo', False 

# Efficiently compare two unordered lists:

```
 from collections import Counter 
one = [33, 22, 11, 44, 55] 
two = [22, 11, 44, 55, 33] 
print( ' two lists are b equal ', Counter(two) )
```

Resulting Output =

 'the two lists are b equal', True 

# Check if list contains all unique elements:

```
 def isUnique(item): 
tempSet = set() 
return not any(i in tempSet or tempSet.add(i) for i in item) 
listOne = [123, 345, 456, 23, 567]
```