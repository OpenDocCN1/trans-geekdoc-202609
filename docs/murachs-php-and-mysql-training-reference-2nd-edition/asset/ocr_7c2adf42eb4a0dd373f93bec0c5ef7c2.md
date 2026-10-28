# How to read and write an entire file

Figure 23-2 presents three functions for reading an entire file with one statement. The file function reads each line of the file into a separate element in an array. The file_get_contents function reads the entire file into a single text string. And the readfile function reads a file and immediately echos it to the web page.

This figure also presents one function for writing an entire file. This file_put_contents function writes a text string to a file. If necessary, though, you can write an array of lines to a file by first using the implode function to convert the array to a string and then using the file_put_contents function.

The first example shows how to read text from a file. This code uses the file_get_contents function to read the file named message.txt and store its contents in the variable named $text. Since this code doesn’t specify a directory for the file, this example looks for the file in the current directory. Then, this code uses the htmlentitiespecialchars function to convert any special HTML characters to their corresponding character entities. Finally, this code uses an echo statement to send the text to the browser within a <div> tag.

The second example writes text to a file. First, this code stores the text in a variable named $text. Then, it uses the file_put_contents function to write the text to a file named message.txt.

The third example shows how to read the contents of a file into an array. First, this code uses the file function to read the file named username.txt. This stores each line of this file in an element of the $names array. Then, it uses a loop to display each element of the $names array inside of a <div> tag.

The fourth example shows how to write the contents of an array to a file. Here, the first statement creates the $names array and stores three elements in that array. Then, the second statement uses the implode function to concatenate the lines in the array in a single string with a new line character (\n) at the end of each line. Finally, this code uses the file_put_contents function to write the $names string to the file named message.txt. Note that the new line character (\n) must be in double quotes. If it’s inside single quotes, this code will separate the lines with a backslash and an n, which isn’t what you want.