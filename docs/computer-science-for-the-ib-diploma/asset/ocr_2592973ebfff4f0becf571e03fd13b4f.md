Noise: unwanted electrical disturbances that can affect the integrity of signals being processed by a computer; this noise is not related to sound, but to variations in voltage or current that can disrupt the accurate transmission and processing of digital data.
◆ Bit: binary digit; a single digit, either 1 or 0.
◆ Byte: 8 bits.

turned on or off, aligning perfectly with the binary system's two-state logic. Additionally, Boolean algebra, the mathematical framework for logical circuit design and operation, enables straightforward implementation of complex operations using simple logic gates with binary inputs: 1 (on / true) or 0 (off / false).

The increased reliability of binary systems stems from their use of only two states. Small variations in signal strength do not affect data integrity as much as in systems using larger bases, making binary more robust in noisy environments.

As all data on a computer system is stored in binary, we need systems to represent numerous types of data, such as integers, strings, characters, images, audio and video, in binary form.

# Representation of integers in binary

To represent numbers in binary, it is useful to remember the basics of our decimal system (base-10).

In the decimal system, as we count, we start with a single digit and increment it by 1 until we reach 9. After 9, we introduce a new digit to the front to represent larger numbers. Let’s break down the decimal number 1024:

| 1000s | 100s | 10s | 1s |
| :--- | :--- | :--- | :--- |
| 1 | 0 | 2 | 4 |

(1 x 1000) + (0 x 100) + (2 x 10) + (4 x 1) = 1024

Each decimal place value increases by a multiple of 10 as we move to the left because we are working in base-10.

Binary, and other base systems, work in a similar way but, instead of 10 possible states per digit, binary has only two (0 and 1). Consequently, each digit increases by a multiple of 2. Let’s break down the binary number 0110:

| 8s | 4s | 2s | 1s |
| :--- | :--- | :--- | :--- |
| 0 | 1 | 1 | 0 |

(0 x 8) + (1 x 4) + (1 x 2) + (0 x 1) = 6

In this example, we have no 8s, one 4, one 2 and no 1s. Adding 4 + 2 gives us the decimal (base-10) equivalent of the binary (base-2) number 0110. To clearly denote whether we are showing a binary or decimal number, we usually put the base as a subscript, to avoid confusion:

```
0110₂ = 6₁₀
```

Common mistake
When seeing the number 11111111, a common mistake is to say this is 256. However, remember that while there are 256 number possibilities, 255 is the largest number we can represent in 1 byte (as 0 can also be represented).

When working with computer systems, we usually deal with 8-bit binary numbers. A bit can be defined as a “binary digit”, and 8 bits is equivalent to 1 byte. If the number does not require 8 bits to represent it, we usually pad out the extras with 0s. For example, the decimal number 33 would be represented as:

| 128s | 64s | 32s | 16s | 8s | 4s | 2s | 1s |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 0 | 0 | 1 | 0 | 0 | 0 | 0 | 1 |

This means that with 8 bits, we can represent 256 different numbers, from 0 to 255. If we want to represent larger numbers, we need more bits to represent this.