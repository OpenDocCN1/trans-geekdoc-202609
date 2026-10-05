# A Python 2.7 Programming Tutorial 233

-1
>>>
If, however, or the third elements are equal, Python then compares the second
elements, or until it finds two unequal elements, or
finds that all the elements are equal:
>>> cmp ( (50,30,30), (80,10,10) )
-1
>>> cmp ( (50,30,30), (50,10,10) )
1
>>> cmp ( (50,30,30), (50,30,80) )
-1
>>> cmp ( (50,30,30), (50,30,30) )
0

So, watch what happens when we sort a list of two-tuples containing snail
times and names:
>>> timeList = [ (87.3, 'Judy'), (96.6, 'Kyle'), (63.0, 'Lois') ]
>>> timeList.sort()
>>> timeList
[(63.0, 'Lois'), (87.29999999999999, 'Judy'), (96.59999999999999,
'Kyle')]
>>>

Now we have a list that is ordered the way the snails finished. Here is our
modified script:
#!/usr/local/bin/python
################################################################=

```
################################################===============
# snailtuples.py: Second snail racing results script.
#----------------------------------------------------------------------

#-
# Create an empty list to hold the result tuples.
#-
timeList = []

#-
# Open the file containing the results.
#-
resultsFile = open ( 'results' )
```