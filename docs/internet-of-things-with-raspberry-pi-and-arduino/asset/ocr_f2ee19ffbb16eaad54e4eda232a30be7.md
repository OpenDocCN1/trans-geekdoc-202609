# TABLE 9.1

Description of Modes

| Mode | Description |
| --- | --- |
| W | This mode opens a file only to write. It overwrites an existing file. |
| w+ | This mode opens a file to read and write both. It overwrites an existing file. |
| R | This mode opens a file only to read. |
| r+ | This mode opens a file for appending and read both. |
| A | This mode opens a file for appending, starting from end of the document. |
| a+ | This mode opens a file for appending and reading, starting from end of the document. |

```
'Hello World!\nPython programming for Arduino\nBye\n'
>>>D.close()
```

With this method, the entire contents of the file is stored in memory. To read the content line to use, use the readlines() method:

```
>>>D=open('test.txt', 'r')
>>>X =D.readlines()
>>> print X
['Hello World!\n', 'Python programming for Arduino\n', 'Bye\n']
>>>D.close()
```

# 9.2 CSV File

CSV files are used to store the data in Python. A CSV writer is used to write data on a CSV file and the reader to read it with simple commands:

# CSV writer

```
import csv
data = [[1, 2, 3], ['a', 'b', 'c'], ['Python', 'Arduino', 'Programming']]
with open('example.csv', 'w') as f:
    w = csv.writer(f)
    for row in data:
        w.writerow(row)
```