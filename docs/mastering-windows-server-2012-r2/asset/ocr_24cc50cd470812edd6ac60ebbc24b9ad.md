With all this mind, here's what we are going to do:

+   - Create an RTF file with a credit card number in the content.

+   - Create an RTF file with the word payroll in the content.

+   - Create an RTF file with the words Intellectual Property in the content.

+   - Create a classification rule to detect these attributes using regular expressions and a string in the content.

+   - Create a Central Access Policy that will use the file classification to secure the resource.

Okay, let's go. First, create the three documents you need:

+   1. On your file server (using our example ContosoFS01) navigate to C:\share\accounts.

+   2. Right-click on the file, and select New > Rich Text Document; see Figure 15.82.

![](bbox=[0.15, 0.381, 0.85, 0.755])

+   3. Type File1 for its name.

We are using a generic name to ensure that it actually detects the content and classifies the document correctly.

+   4. Double-click File1 to open it and type a 12-digit number.

+   5. Save the document and close it.