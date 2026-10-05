# A Python 2.7 Programming Tutorial 231

race, so a relatively less skilled person can prepare that file, and run a script that will review the results.

We’ll use a very simple text file format to encode the race results. Here’s an example file for first race between Judy and Kyle:

87.3 Judy

96.6 Kyle

And here is a script that will process that file and report on the winning time. The script is called snailist.py. First, reads a results file named results and stores them into a list. .split()method is used to break each line into parts, with the first part containing the elapsed time.

```
#!/usr/local/bin/python
################################################=====
# snailist.py: First snail racing results script.
----------------------------------------------------
#-
# Create an empty list to hold the finish times.
#-
timeList = []

#-
# Open the file containing the results.
#-
resultsFile = open ('results')

#-
# Go through the lines of that file, storing each finish time.
#-
for resultsLine in resultsFile:
#-
# Create a list of the fields in the line, e.g., ['87.3', 'Judy\n']
#-
fieldList = resultsLine.split()

#-
# Convert the finish time into a float and append it to timeList.
#--
```