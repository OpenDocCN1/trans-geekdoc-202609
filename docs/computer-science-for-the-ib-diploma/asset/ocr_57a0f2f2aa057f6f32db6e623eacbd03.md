# # Representation of integers in hexadecimal

Hexadecimal (often abbreviated as hex) is a base-16 number system that uses 16 distinct symbols to represent values, rather than the 10 of decimal or 2 of binary. The symbols include the digits 0 to 9 and then the letters A to F, where A represents 10, B represents 11, C represents 12, D represents 13, E represents 14 and F represents 15.

+   ◆ Debugging tools:
+   software applications
+   or utilities used by
+   developers to identify,
+   analyse and fix bugs
+   or issues within a
+   program by inspecting
+   code, variables and
+   execution flow.
+   ◆ Memory dump:
+   a process where
+   the contents of a
+   computer's memory
+   are captured and
+   saved, typically for the
+   purpose of diagnosing
+   and debugging
+   software issues.
+   ◆ Nibble: 4 bits.

Hexadecimal is used with computers for several reasons. The ease of conversion between binary and hexadecimal is straightforward because each hex digit maps directly to a 4-bit binary sequence. For example, the binary number 1111 can be represented as F in hex. Another reason is that it provides a more compact way to represent a binary value. This makes it much easier for us to read and communicate large binary numbers. This is why you often see hex used in debugging tools, memory dumps and assembly language programming.

# ## Converting binary numbers to hexadecimal

Converting binary to hexadecimal is a straightforward calculation.

+   1 Split the binary byte (8 bits) into two nibbles (2 × 4 bits).
+   2 Calculate the decimal value of these 4 bits.
+   3 Convert the decimal values into their hexadecimal equivalents and rejoin them.

For example, to convert 011010112 to hexadecimal:

+   1 Split the byte into 2 nibbles:
+   01102 10112
+   2 Calculate the decimal value:
+   610 1110
+   3 Convert both decimal values to their hexadecimal equivalents and rejoin them:
+   6B16

# ## REVIEW QUESTIONS

+   Convert the following binary (base-2) numbers to hexadecimal (base-16):
+   1 101011002 4 001110102
+   2 110101102 5 100111012
+   3 110100012

# ## Converting hexadecimal numbers to binary

Moving from hex to binary is just a reverse of the binary-to-hexadecimal process:

+   1 Split the two hexadecimal digits.
+   2 Convert each of them to a 4-bit binary number using the same integer-to-binary method.
+   3 Join the two 4-bit numbers together to form 1 byte.

For example, to convert F216 to binary:

+   1 Split the two hexadecimal digits:
+   F16 216
+   2 Convert each of them to a 4-bit binary number using the same integer-to-binary method:
+   11112 00102
+   3 Join the two 4-bit numbers together to form 1 byte:
+   111100102