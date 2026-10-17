
Python enables you to extract substrings of a string (called “slicing”) using array notation. Slice notation is start:stop:step, where the start, stop, and step values are integers that specify the start value, end value, and the increment value. The interesting part about slicing in Python is that you can use the value -1, which operates from the right-side instead of the left-side of a string.

Some examples of slicing a string are here:

text1 = "this is a string" print('First 7 characters:',text1[0:7]) print('Characters 2-4:',text1[2:4]) print('Right-most character:',text1[-1]) print('Right-most 2 characters:',text1[-3:-1]) 

The output from the preceding code block is here:

First 7 characters: this is Characters 2-4: is Right-most character: g Right-most 2 characters: in 

Later in this appendix you will see how to insert a string in the middle of another string.

### **Testing for Digits and Alphabetic Characters**

Python enables you to examine each character in a string and then test whether that character is a bona fide digit or an alphabetic character. This section provides a simple introduction to regular expressions.

[Listing B.3](#appB.xhtml#listB.3) displays the contents of CharTypes.py that illustrates how to determine if a string contains digits or characters. Although we have not discussed conditional logic in Python yet, the examples in [Listing B.3](#appB.xhtml#listB.3) are straightforward.

***LISTING B.3: CharTypes.py***

str1 = "4" str2 = "4234" str3 = "b" str4 = "abc" str5 = "a1b2c3" if(str1.isdigit()): print("this is a digit:",str1) if(str2.isdigit()): print("this is a digit:",str2) if(str3.isalpha()): print("this is alphabetic:",str3) if(str4.isalpha()): print("this is alphabetic:",str4) if(not str5.isalpha()): print("this is not pure alphabetic:",str5) print("capitalized first letter:",str5.title()) 

[Listing B.3](#appB.xhtml#listB.3) initializes some variables, followed by 2 conditional tests that check whether or not str1 and str2 are digits using the isdigit() function. The next portion of [Listing B.3](#appB.xhtml#listB.3) checks if str3, str4, and str5 are alphabetic strings using the isalpha() function. The output of [Listing B.3](#appB.xhtml#listB.3) is here:

this is a digit: 4 this is a digit: 4234 this is alphabetic: b this is alphabetic: abc this is not pure alphabetic: a1b2c3 capitalized first letter: A1B2C3 

[Listing B.3](#appB.xhtml#listB.3) initializes some variables, followed by 2 conditional tests that check whether or not str1 and str2 are digits using the isdigit() function. The next portion of [Listing B.3](#appB.xhtml#listB.3) checks if str3, str4, and str5 are alphabetic strings using the isalpha() function. The output of [Listing B.3](#appB.xhtml#listB.3) is here:

this is a digit: 4 this is a digit: 4234 this is alphabetic: b this is alphabetic: abc this is not pure alphabetic: a1b2c3 capitalized first letter: A1B2C3 

***LISTING B.4: FindPos1.py***

item1 = 'abc' item2 = 'Abc' text = 'This is a text string with abc' pos1 = text.find(item1) pos2 = text.find(item2) print('pos1=',pos1) print('pos2=',pos2) 

[Listing B.4](#appB.xhtml#listB.4) initializes the variables item1, item2, and text, and then searches for the index of the contents of item1 and item2 in the string text. The Python find() function returns the column number where the first successful match occurs; otherwise, the find() function returns a -1 if a match is unsuccessful. The output from launching [Listing B.4](#appB.xhtml#listB.4) is here:

pos1= 27 pos2= -1 

In addition to the find() method, you can use the in operator when you want to test for the presence of an element, as shown here:

\>>> lst = [1,2,3] \>>> 1 in lst True 

[Listing B.5](#appB.xhtml#listB.5) displays the contents of Replace1.py that shows you how to replace one string with another string.

***LISTING B.5: Replace1.py***

text = 'This is a text string with abc' print('text:',text) text = text.replace('is a', 'was a') print('text:',text) 

[Listing B.5](#appB.xhtml#listB.5) starts by initializing the variable text and then printing its contents. The next portion of [Listing B.5](#appB.xhtml#listB.5) replaces the occurrence of “is a” with “was a” in the string text, and then prints the modified string. The output from launching [Listing B.5](#appB.xhtml#listB.5) is here:

text: This is a text string with abc text: This was a text string with abc 

[Listing B.5](#appB.xhtml#listB.5) starts by initializing the variable text and then printing its contents. The next portion of [Listing B.5](#appB.xhtml#listB.5) replaces the occurrence of “is a” with “was a” in the string text, and then prints the modified string. The output from launching [Listing B.5](#appB.xhtml#listB.5) is here:

text: This is a text string with abc text: This was a text string with abc 

[Listing B.6](#appB.xhtml#listB.6) displays the contents of Remove1.py that shows you how to search for a string.

***LISTING B.6 Remove1.py***

text = '   leading and trailing white space   ' print('text1:','x',text,'y') text = text.lstrip() print('text2:','x',text,'y') text = text.rstrip() print('text3:','x',text,'y') 

[Listing B.6](#appB.xhtml#listB.6) starts by concatenating the letter x and the contents of the variable text, and then printing the result. The second part of [Listing B.6](#appB.xhtml#listB.6) removes the leading white spaces in the string text and then appends the result to the letter x. The third part of [Listing B.6](#appB.xhtml#listB.6) removes the trailing white spaces in the string text (note that the leading white spaces have already been removed) and then appends the result to the letter x.

The output from launching [Listing B.6](#appB.xhtml#listB.6) is here:

text1: x leading and trailing white space y text2: x leading and trailing white space y text3: x leading and trailing white space y 

If you want to remove extra white spaces inside a text string, use the replace() function as discussed in the previous section. The following example illustrates how this can be accomplished, which also contains the re module for regular expressions:

import re text = 'a    b' a = text.replace(' ', '') b = re.sub('\\s+', ' ', text) print(a) print(b) 

The result is here:

ab a b 

## **Printing Text without NewLine Characters**

If you need to suppress white space and a newline between objects output with multiple print statements, you can use concatenation or the write() function.

The first technique is to concatenate the string representations of each object using the str() function prior to printing the result. For example, run the following statement in Python:

x = str(9)+str(0xff)+str(-3.1) print('x: ',x) 

The output is shown here:

x:  9255-3.1 

The preceding line contains the concatenation of the numbers 9 and 255 (which is the decimal value of the hexadecimal number 0xff) and -3.1.

Incidentally, you can use the str() function with modules and user-defined classes. An example involving the Python built-in module sys is here:

\>>> import sys \>>> print(str(sys)) <module 'sys' (built-in)> 

The following code snippet illustrates how to use the write() function to display a string:

import sys write = sys.stdout.write write('123') write('123456789') 

The output is here:

1233 1234567899 

## **Text Alignment**

Python provides the methods ljust(), rjust(), and center() for aligning text. The ljust() and rjust() functions left justify and right justify a text string, respectively, whereas the center() function will center a string. An example is shown in the following code block:

text = 'Hello World' text.ljust(20) 'Hello World ' \>>> text.rjust(20) ' Hello World' \>>> text.center(20) ' Hello World ' 

You can use the Python format() function to align text. Use the <, >, or ^ characters, along with a desired width, in order to right justify, left justify, and center the text, respectively. The following examples illustrate how you can specify text justification:

\>>> format(text, '>20') '         Hello World' \>>> \>>> format(text, '<20') 'Hello World         ' \>>> \>>> format(text, '^20') '    Hello World     ' \>>> 

## **Working with Dates**

Python provides a rich set of date-related functions that are documented here:

*[http://docs.python.org/2/library/datetime.html](http://docs.python.org/2/library/datetime.html)*
