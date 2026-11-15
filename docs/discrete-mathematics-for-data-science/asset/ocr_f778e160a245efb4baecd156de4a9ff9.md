B. Similarly, for the binary sequence 10, trace the route from the top node rightward down the 1 branch and then the 0 branch, which leads to C. Repeat this process for each set of bits in the message.

It should be said that Huffman compression produces *prefix free code*, meaning that an encoding of one symbol is not a prefix for any other. The prefix free property makes Huffman encoded bit strings uniquely decipherable, allowing us to reconstruct the symbol sequences of a message.

For example, using our prior symbol encodings, suppose the bit string 1011000 is to be deciphered. Traversing that bit string from left to right we look for a bit that matches in the tree path. The first match is 10, which is C. Remove those two bits, 1 and 0, from the bit string. Resume by processing the remaining bit string, 11000, from left to right. The sequence of 11 connect to A. Remove those bits. The last three bits, 000, connect to B. In the sequence that the symbols were deciphered, we get the word CAB.

# EXERCISES

+   1. Consider a scenario where any one of eight equally probable messages may be received. Show how Shannon Information would be computed.

+   2. Write an algorithm to determine the entropy of the following lists:

+   (a) { 0 0 0 0 0 0 }
+   (b) { 1 0 1 0 1 0 }
+   (c) { 1 1 1 1 1 1 }
+   (d) { 1 0 0 1 1 1 }

What can you generally deduce about the impact of entropy on these symbol pattern?

+   3. Discuss the use of redundant symbols for overcoming message transmission errors. Does symbol redundancy affect Shannon entropy? Explain why or why not.

+   4. Write an algorithm to determine the joint entropy of the following list pairs: (A, B), (C D), and (E, F).

+   (a) { 0 0 0 0 0 0 } A { 1 1 1 1 1 1 } B
+   (b) { 1 0 1 0 1 0 } C { 0 1 0 1 0 1 } D