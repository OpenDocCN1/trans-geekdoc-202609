# # Chapter 2.2.1: Reading CSV

The csv package includes a NewReader() function that returns a Reader object for processing CSV records. A csv.Reader converts all '\n' sequences in its input to just \n, including multiline field values.

The CSV file below contains three columns, a header row with labels, and two rows with data. This example will demonstrate how to read a CSV file and print each of the corresponding cell values.

Here is the CSV file viewed in spreadsheet form.

| HOST | IP ADDR | LOCATION |
| :--- | :--- | :--- |
| RTR1 | 1.1.1.1 | Seattle, WA |
| RTR2 | 2.2.2.2 | Nevada, NV |

Below is the same CSV file as above viewed as plain text in a text editor.

```
```
HOST,IP ADDR,LOCATION
RTR1,1.1.1.1,"Seattle, WA"
RTR2,2.2.2.2,"Nevada, NV"
```
```

In this example, the file is opened in read-only mode using the os.Open() function, which returns an instance of os.File. Next, the os.File object is handed off as a parameter to the csv.NewReader() function which returns a buffered csv.Reader object. Then, the csv.Reader.Read() method is used to decode each file record into the struct and then store them in a slice until io.EOF is returned, indicating the end of the file has been reached. Finally, the slice iterates over each value.

```
```
package main

import (
	"encoding/csv"
	"fmt"
```
```