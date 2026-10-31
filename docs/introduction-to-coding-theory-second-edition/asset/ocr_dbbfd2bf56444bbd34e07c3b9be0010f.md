# An application to error detection

Here is an application of ε-universal hash families for the purposes of error detection. Assume we send the long message x to the receiver via a rather good channel. Let y be the received message. In most cases, no errors will occur, hence y = x. In order to be able to detect errors (not to correct them), the following method can be used: we choose a function f at random from our ε-universal family and send f as well as f(x) to the receiver, using a public channel which will certainly not commit errors. This will not cost all too much, as these messages are much shorter than x (in the example above x has 2^20 bits, whereas f and f(x) are bitstrings of length 32 each). If f(y) ≠ f(x), then the receiver knows that a transmission error has happened. He will ask for retransmission in this case. If f(y) = f(x), the message will be accepted as correct. The probability that this assumption is in error is then limited by ε.

# Exercises 6

+   6.1. Determine the parameters of Reed-Solomon codes when interpreted as ε-universal hash families.
+   6.2. Describe an (8,16)₂ hash family, which is ½-universal.
+   6.3. Find a ²⁄₅-universal (10,81)₃ hash family. Hint: this code has been constructed in Chapter 3. It is closely related to the ternary Golay code.
+   6.4. Does a ½-universal (6,9)₂ hash family exist?
+   6.5. Construct a (256,256¹⁷)₂₅₆ hash family, which is ¹⁄₁₆-universal.
+   6.6. Explain why a code [4000,5,3996]₄₀₉₆ exists and determine the parameters of the universal hash family derived from it.