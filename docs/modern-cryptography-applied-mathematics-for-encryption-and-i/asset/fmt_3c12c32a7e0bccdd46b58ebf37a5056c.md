
Examining in general terms what a theory is and is not may not provide an adequate explanation for all readers. So let’s look at a concrete example of a very well-accepted theory, the theory of gravity, and how it relates to specific facts. Sir Isaac Newton observed that things tend to fall. In a very general way, this is the essence of his law of gravity: Gravity makes things fall downward. Of course, he expressed that law mathematically with this equation:

```
F = Gm[1]m[2]/d²
```

In this equation, F is the force of gravity, G is a constant (the Gravitational Constant) that can be measured, m[1] and m[2] are the masses of the two objects (such as the Earth and a falling apple), and d is the distance between them. This law of gravity can be measured and verified thousands of times, and in fact it has been.

But this law, by itself, is incomplete. It does not provide an adequate explanation for why this occurs. We know there is gravity and we all feel its pull, but what is it? Why does gravity work according to this formula? Einstein’s Theory of General Relativity was an explanation for why gravity exists. He proposed that matter causes time and space to curve, much like a ball sitting on a stretched-out sheet causes a curve in the sheet. Objects that get close enough to the ball will tend to fall toward it because of this curvature.

Clearly Einstein’s theory explains all the observed facts. But there is still yet another component to qualify it as a scientific theory: It must make some predictions. By *predictions*, I don’t mean that it foretells the future. What I mean is that if this theory is valid, then you would expect other things also to be true. If those predictions turn out not to be true, then Einstein’s theory must either be modified or rejected. Whether you choose to modify a theory or reject it depends on how well its predictions work out. If it is 90 percent accurate, then you would probably just look to adjust the theory so it matched the facts. However, if it was accurate less than half the time, you would probably consider rejecting the theory outright.

So what predictions can we make from the Theory of General Relativity?

![image](Images/image00554.jpeg) *Gravity can bend light*. This has been reconfirmed literally hundreds of times with more precision each time. In 2003, the Cassini Satellite once again confirmed this prediction—and this 2003 test was just one among many that all confirmed that gravity can bend light.

![image](Images/image00554.jpeg) *Light loses energy escaping from a gravitational field*. Because the energy of light is proportional to its frequency, a shift toward lower energy means a shift to lower frequency and longer wavelength. This causes a “red shift,” or shift toward the red end of the visible spectrum. This was experimentally verified on Earth using gamma-rays at the Jefferson Tower Physics Laboratories.

![image](Images/image00554.jpeg) *Light is deflected by gravity*. General relativity predicts that light should be deflected, or bent, by gravity. This was first confirmed by observations and measurements of a solar eclipse in 1919. It has since been confirmed by hundreds of experiments over decades.

Other predictions relating to the General Theory of Relativity have been confirmed by dozens, and in some cases hundreds, of independent experiments. Note the word *independent*. These experiments were carried out by people with no particular vested interest in proving Einstein correct. And in a few cases, they really wanted to prove him wrong. Yet in every case the data confirmed Einstein’s theory. You would be hard put to find any physicist who does not agree that the General Theory of Relativity is valid and is true. Some may argue it is not yet complete, but none will argue that it is not true. Hundreds of experiments spanning many decades and literally thousands of scientists have confirmed every aspect of general relativity. Now that this theory is well established, it can be used to guide future experiments and a deeper understanding of gravity as well as related topics.

* * *

#### Binary Math

Binary math is not actually a part of information theory, but it is critical information you will need to be able to understand cryptography in later chapters. Many readers will already be familiar with binary math, and this will be a review for you. However, if your background does not include binary math, this section will teach you the essentials you need.

Defining binary math is actually rather simple: It is mathematics that uses a base 2 rather than the more familiar base 10. The only reason you find base 10 (that is, the decimal number system) to be more “natural” is because most of us have 10 fingers and 10 toes. (As least most people have 10 fingers and toes—but even if you have a different number of fingers and toes, you understand that 10 is normal for humans.)

Once we introduce the concept of 0, we have 10 digits in the base 10 system: 0, 1, 2, 3, 4, 5, 6, 7, 8, and 9. Keep in mind there is not really a number 10 in the base 10 system. There is a 1 in the 10’s place and a 0 in the 1’s place. The same thing is true with binary, or base 2 numbers. There is not actually a number 2. There is a 1 in the 2’s place and a 0 in the 1’s place. This chart comparing the two might be helpful:

![Images](Images/image00555.jpeg)

Binary numbers are important because that is, ultimately, what computers understand. You can, of course, represent numbers in any system you wish. And a number system can be based on any integer value. Historically, a few have been widely used. Hexadecimal (base 16) and octal (base 8) are sometimes used in computer science because they are both powers of 2 (2⁴ and 2³, respectively) and thus are easily converted to and from binary. The Babylonians used a base 60 number system, which you still see today in representation of degrees in a geographic coordinate system. For example, 60 seconds makes a minute and 60 minutes makes a degree, so you can designate direction by stating “45 degrees, 15 minutes, and 4 seconds.”

**Note**

The modern concept of binary numbers traces back to Gottfried Leibniz, who wrote an article entitled “Explanation of the Binary Arithmetic.” Leibniz noted that the Chinese I Ching hexagrams correspond to binary numbers ranging from 0 to 1111111 (or 0 to 63 in decimal numbers).

##### Converting

Because humans tend to be more comfortable with decimal numbers, you will frequently want to convert from binary to decimal, and you may need to make the inverse conversion as well. You can use many methods to do this, and a common one takes advantage of the fact that the various “places” in a binary number are powers of 2. So consider for a moment a binary number 10111001 and break it down into the powers of 2. If there is a 1 in a given place, then you have that value. If not, you have a 0. For example, if there is a 1 in the 2⁷ place, then you have 128; if not, you have a 0.

![Images](Images/image00556.jpeg)

Now just add the values you have: 128 + 32 + 16 + 8 + 1 = 185.

This may not be the fastest method, but it works and it is easy to understand.

##### Binary Operations

You can do all the mathematical operations with binary that you can do with decimal numbers. Fortunately, with cryptography you will be primarily concerned with three operations, AND, OR, and XOR, and these are relatively easy to understand. For all of our examples, we will consider two 4-bit binary numbers: 1101 and 1100. We will examine how the AND, OR, and XOR operations work on these two numbers.

###### Binary AND

The binary AND operation combines two binary numbers, 1 bit at a time. It asks, “Is there a 1 in the same place in both numbers?” If the answer is yes, then the resulting number is a 1. If no, then the resulting number is a 0. Here, you can see the comparison of the rightmost digit in two 4-digit binary numbers:

![Images](Images/image00557.jpeg)
