
% cat targets
RPC-DCOM   10.10.20.1,10.10.20.4
SQL-SA-blank-pw 10.10.20.27,10.10.20.28
# We want to move the contents of targets into two separate files
% python
# First, open the file for reading
>>> targets_file = open('targets', 'r')
# Read the contents into a list of strings
>>> lines = targets_file.readlines()
>>> lines
['RPC-DCOM\\t10.10.20.1,10.10.20.4\\n', 'SQL-SA-blank-pw\\t10.10.20.27,10.10.20.28\\n']
# We can also do it with a "with" statement using the following syntax:
>>> with open("targets", "r") as f:
...     lines = f.readlines()

...
>>> lines
['RPC-DCOM   10.10.20.1,10.10.20.4\n', 'SQL-SA-blank-pw
10.10.20.27,10.10.20.28\n', '\n']
# The "with" statement automatically ensures that the file is closed and
# is seen as a more appropriate way of working with files..
# Let's organize this into a dictionary
>>> lines_dictionary = {}
>>> for line in lines:    # Notice the trailing : to start a loop
...     one_line = line.split()      # split() will separate on white space
...     line_key = one_line[0]
...     line_value = one_line[1]
...     lines_dictionary[line_key] = line_value
...     # Note: Next line is blank (<CR> only) to break out of the for loop
...
>>> # Now we are back at python prompt with a populated dictionary
>>> lines_dictionary
{'RPC-DCOM': '10.10.20.1,10.10.20.4', 'SQL-SA-blank-pw':
'10.10.20.27,10.10.20.28'}
# Loop next over the keys and open a new file for each key
>>> for key in lines_dictionary.keys():
...     targets_string = lines_dictionary[key]      # value for key
...     targets_list = targets_string.split(',')      # break into list
...     targets_number = len(targets_list)
...     filename = key + '_' + str(targets_number) + '_targets'
...     vuln_file = open(filename,'w')
...     for vuln_target in targets_list:        # for each IP in list...
...             vuln_file.write(vuln_target + '\n')
...             vuln_file.close()
...
>>> ^D
% ls
RPC-DCOM_2_targets             targets
SQL-SA-blank-pw_2_targets
% cat SQL-SA-blank-pw_2_targets
10.10.20.27
10.10.20.28
% cat RPC-DCOM_2_targets
10.10.20.1
10.10.20.4

This example introduces a couple of new concepts. First, you now see how easy it is to use files. open() takes two arguments: the first is the name of the file you’d like to read or create, and the second is the access type. You can open the file for reading (r), writing (w), and appending (a). Adding a + after the letter adds more permissions; for example, r+ results in read and write access to the file. Adding a b after the permission opens it in binary mode.

And you now have a for loop sample. The structure of a for loop is as follows:

```
for <iterator-value> in <list-to-iterate-over>:
    # Notice the colon on end of previous line
    # Notice the tab-in
    # Do stuff for each value in the list
```

![](img/5f597c6a70133069118d9e804ace3775_81_0.png)

> CAUTION In Python, white space matters, and indentation is used to mark code blocks. Most Python programmers stick with an indentation of four spaces. The indentation must be consistent throughout a block.

Unindenting one level or a placing a carriage return on a blank line closes the loop. No need for C-style curly brackets. if statements and while loops are similarly structured. Here is an example:

```
if foo > 3:
    print('Foo greater than 3')
elif foo == 3:
    print('Foo equals 3')
else:
    print('Foo not greater than or equal to 3')
...
while foo < 10:
    foo = foo + bar
```

## Sockets with Python

The final topic we need to cover is Python's socket object. To demonstrate Python sockets, let's build a simple client that connects to a remote (or local) host and sends 'Hello, world'. To test this code, we need a “server” to listen for this client to connect. We can simulate a server by binding a netcat listener to port 4242 with the following syntax (you may want to launch nc in a new window):

```
% nc -l -p 4242
```

The client code follows:

```
import socket
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect(('localhost', 4242))
s.send('Hello, world')       # This returns how many bytes were sent
data = s.recv(1024)
s.close()
print('Received', data)
```

You do need to remember to import the socket library, and then the socket instantiation line has some socket options to remember, but the rest is easy. You connect to a host and port, send what you want, recv into an object, and then close the socket down. When you execute this, you should see “Hello, world” show up on your netcat listener and anything you type into the listener returned back to the client. For extra credit, figure out how to simulate that netcat listener in Python with the bind(), listen(), and accept() statements.

## Summary

This chapter provides you with introductory programming concepts and security considerations. An ethical hacker must have programming skills to create exploits or review source code, and they need to understand assembly code when reversing malware or finding vulnerabilities. Last but not least, debugging is a must-have skill in order to analyze the malware at runtime or to follow the execution of shellcode in memory. The only way to learn a programming language or reverse engineering is through practice, so get working!

## For Further Reading

- “A CPU History,” _PC Mech_, March 23, 2001 (David Risley)
- www.pcmech.com/article/a-cpu-history
- Art of Assembly Language Programming and HLA (Randall Hyde) webster.cs.ucr.edu/
- ddd debugger frontend https://www.gnu.org/software/ddd/
- Debugging with NASM and gdb www.csee.umbc.edu/help/nasm/nasm.shtml
- edb debugger http://codef00.com/projects
- “Endianness,” Wikipedia en.wikipedia.org/wiki/Endianness
- Good Python tutorial https://docs.python.org/2/tutorial/
- “How C Programming Works,” _How Stuff Works_ (Marshall Brain)
- computer.howstuffworks.com/c.htm
- “Introduction to C Programming,” University of Leicester (Richard Mobbs) www.le.ac.uk/users/rjm1/c/index.html
- “Little Endian vs. Big Endian,” _Linux Journal_, September 2, 2003 (Kevin Kaichuan He) www.linuxjournal.com/article/6788
- Notes on x86 assembly, 1997 (Phil Bowman) www.cntech.com/code/x86asm.txt
- “Pointers: Understanding Memory Addresses,” _How Stuff Works_ (Marshall Brain)
- computer.howstuffworks.com/c23.htm
- “Programming Methodology in C” (Hugh Anderson) www.comp.nus.edu.sg/~hugh/TeachingStuff/cs1101c.pdf
- Python home page www.python.org
- Python Tutor www.pythontutor.com
- “Smashing the Stack for Fun and Profit” (Aleph One) www.phrack.org/issues.html?issue=49&id=14#article
- x86 registers www.eecg.toronto.edu/~amza/www.mindsec.com/files/x86regs.html
- x64 architecture https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/x64-architecture

## References

- 1. Danny Cohen, “On Holy Wars and a Plea for Peace.” Internet Experiment Note (IEN) 137, April 1, 1980, www.ietf.org/rfc/ien/ien137.txt.
- 2. Guido Van Rossum, “[Python-Dev] Replacement for Print in Python 3.0,” September 4, 2006, mail.python.org, https://mail.python.org/pipermail/python-dev/2005-September/056154.html.

## Next-Generation Fuzzing

This chapter shows you how to use fuzzing techniques for software testing and vulnerability discovery. Originally, fuzzing (or _fuzz testing_) was a class of black box software and hardware testing in which the data used to perform the testing is randomly generated. Over the years, fuzzing evolved as it came to the attention of many researchers who extended the original idea. (See “For Further Reading” for great works by Charlie Miller, Michal Zalewski, Jared DeMott, Gynvael Coldwind, Mateusz Jurczyk, and many others.) Nowadays, fuzzing tools support black box and white box testing approaches and have many adjustable parameters. These parameters influence the fuzzing process and are used to fine-tune the testing process for a specific problem. By understanding the different approaches and their parameters, you will be able to get the best results using this testing technique.

In this chapter, we discuss the following topics:

- Introduction to fuzzing
- Types of fuzzers
- Mutation fuzzing with Peach
- Generation fuzzing with Peach
- Genetic or evolutionary fuzzing with AFL

## Introduction to Fuzzing

One of the fastest ways to get into vulnerability research is through software testing. Traditional black box software testing is interesting from a vulnerability research perspective because it doesn’t require an understanding of the internal software mechanisms. The only requirement to start looking for vulnerabilities is knowing which interfaces allow interaction with the software and generating the data to be passed through those interfaces.

Fuzzing or fuzz testing is a class of software and hardware testing in which the data used to perform the testing is randomly generated. This way, the problem of generating the input data is vastly simplified and sometimes doesn’t require any knowledge about the internal workings of software or the structure of the input data. This might seem like an oversimplified approach, but it has been proven to produce results and find relevant security vulnerabilities in software.

Over the years, much research has been done on improving the software testing and fuzzing techniques. Nowadays, fuzzing no longer implies the use of randomly generated data as a means of input testing, but is instead used more generally to describe the validation of input through various means.

This chapter looks into the process of fuzzing and examines several ideas for improving
