would normally be beyond the scope of a query. Proper input validation is important before passing the request to an LDAP engine.

# XML Injection

XML can be tampered with via injection as well. XML injections can be used to manipulate an XML-based system. Because XML is nearly ubiquitous in the web application world, this form of attack has a wide range of targets.

The primary method of defense against injection attacks is similar to that for buffer overflows: validate all inputs. But rather than validating toward just length, you need to validate inputs for content. Imagine a web page that asks for user input, and then uses that input in the building of a subsequent page. Also imagine that the user puts the text for a JavaScript function in the middle of their input sequence, along with a call to the script. Now, the generated web page has an added JavaScript function that is called when displayed. Passing the user input through an HtmlEncode function before use can prevent such attacks.

![](bbox=[0.04, 0.42, 0.12, 0.48])

> EXAM TIP For the exam, you should understand injection-type attacks and how they manipulate the systems they are injecting, SQL, LDAP, and XML.

# Directory Traversal/Command Injection

A directory traversal attack is when an attacker uses special inputs to circumvent the directory tree structure of the file system. Adding encoded symbols for "../" in an unvalidated input box can result in the parser resolving the encoding to the traversal code, bypassing many detection elements, and passing the input to the file system, resulting in the program executing commands in a different location than designed. When combined with a command injection, the input can result in execution of code in an unauthorized manner. Classified as an input validation error, these can be difficult to detect without doing code walkthroughs and specifically looking for them. This illustrates the usefulness of the top 25 programming errors checklist at code reviews, as it would alert developers to this issue during development.

Directory traversals can be masked by using encoding of input streams. If the security check is done before the string is decoded by the system parser, then recognition of the attack form may be impaired. There are many ways to represent a particular input form, the simplest is called the canonical form. Parsers are used to render the canonical form for the OS, but these embedded parsers may act after input validation, making it more difficult to detect certain attacks from just matching a string.

# Buffer Overflow

A common weakness that attackers have often exploited is a buffer overflow. A buffer overflow occurs when a program is provided more data for input than it was designed to handle. For example, what would happen if a program that asks for a 7- to 10-character phone number instead receives a string of 150 characters? Many programs will provide some error checking to ensure that this will not cause a problem. Some programs,