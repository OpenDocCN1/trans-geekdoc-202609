# ## Chapter 2.1.2: Writing Plain Text

The bufio package provides an efficient buffered Writer that can be used to write data to a file. A buffered writer queues up bytes until a threshold is reached, then completes the write operation to minimize resources. This example walks through writing a string slice to a plain text file line-by-line.

The example below begins by defining sample data that is represented as a string slice. Each value of the sample data will be written to a new line within the file. To start, the os.OpenFile() function is used with a flag combination that creates a write-only file if none exists and appends to the file when writing. Using the os.File object that is returned from the os.OpenFile() function as input to the bufio.NewWriter() function, a new bufio.Writer object is received. Next, the slice is iterated over and each value is written to the file using the bufio.Writer.WriteString() method, while adding each new line. Finally, any remaining buffered data is written to the file with the bufio.Writer.Flush() method and the file is closed using the os.File.Close() method.

```
```
package main

import (
		"bufio"
		"os"
)

func main() {
	lines := []string{"RTR1 1.1.1.1",
			"RTR2 2.2.2.2",
			"RTR3 3.3.3.3"}

	file, _ := os.OpenFile("./file.txt",
			os.O_APPEND|os.O_CREATE|os.O_WRONLY, 0644)

	writer := bufio.NewWriter(file)
```
```