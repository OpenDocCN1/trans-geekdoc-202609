
letter E is represented by a single dot, S is represented by dot-dot-dot and Z is dash-dash-dot-dot.

However, the graphical representation is purely conventional. We can represent a dash by 1, a dot by 0 and obtain a representation of letters and numbers as bitstrings: E=0, S=000, Z=1100, and T=1, Q=1101, V=0001.

## Back to the general model

Assume we wish to send one of 8 possible messages (the bitstrings of length 3), for example, message 011. If it should happen along the way (in the channel) that the second bit is flipped (the second coordinate is in error), then 001 will be received.

We want to express this situation in mathematical terminology.

## 1.1 Definition. 𝔽₂ = {0,1} with addition

0 + 0 = 0, 0 + 1 = 1, 1 + 0 = 1, 1 + 1 = 0

Here the letter 𝔽 stands for field. It indicates that this tiny structure of only two elements has something in common with the field of real numbers and the complex number field: each of these structures satisfies the same set of axioms. Each of them is a field. We will come back to this topic later.

The idea behind the addition in 𝔽₂ is to model the errors in information transmission: a coordinate of a message is in error if and only if 1 is added to the entry in this coordinate. This explains why we must have 1 + 1 = 0 : if a bit is flipped twice, then no error occurs, or: if 1 is flipped, then 0 is received.

Addition in 𝔽₂ is also known as XORing, in particular in the computer science literature. Here XOR stands for exclusive or, a logical operation, where 1 stands for true and 0 for false. The relation 1 + 1 = 0 (true or true = false) is what makes it “exclusive”: in order for the result to be true, one of the two ingredients has to be true, but not both (the ordinary or operation would have 1 + 1 = 1).

Another motivation for our binary addition comes from arithmetic: if we distinguish even and odd integers, the following familiar rules hold:

even + odd = odd + even = odd, even + even = odd + odd = even.

With even = 0 and odd = 1 these are exactly the rules of binary addition.

Addition in 𝔽₂ describes what happens in each coordinate. Calculation with bitstrings is formalized as follows:

## 1.2 Definition. 𝔽₂ⁿ consists of bitstrings x = (x₁,x₂,…,xₙ) of length n, where xᵢ ∈ 𝔽₂. Addition in 𝔽₂ⁿ is coordinatewise.

For example, let x = 001 ∈ 𝔽₂³ and y = 101 ∈ 𝔽₂³. Then x + y = 100. With this terminology it is easier to express the relation between messages, errors and received messages. Let x = 001100 be the message sent. Assume errors occur in coordinates 2 and 4. We can express this by adding the **error vector** e = 010100. The received message will then be the sum

y = x + e = 011000.

Let us do this the other way around: if x = 010101 was sent and y = 010111 was received, then an error occurred in coordinate 5. This means e = 000100.

Return to the situation where we send one of eight messages (the elements of 𝔽₂³), for example, x = 011. No matter what the error vector e is, the received message y = x + e is again one of the legitimate messages. There is no way for the receiver to suspect that an error occurred, let alone to correct it. So how can we hope to correct errors?

## Error correction: The first idea

Here is the easiest of all error-correcting systems: encode each 0 of the message to be sent as a block 000 and analogously each 1 by 111. If the original message is x = 011, the encoded message is now x′ = 000111111. The receiver knows what encoding scheme has been used. He will therefore divide the received message in blocks of length 3. If such a block is 000 or 111, then decoding is obvious: 000 ↦ 0, 111 ↦ 1. Assume a block of the received message is 101. The receiver knows that at least one transmission error must have happened. It is a basic assumption that a small number of errors is more probable than many errors. The decoding will therefore be 101 ↦ 1 (by majority decision).

The initial picture begins to make sense now. We have seen that messages can be encoded by the transmitter and decoded by the receiver such that the following holds: if not more than one error occurs during transmission (in the channel), then the error will automatically be corrected. What we have used is known as the **repetition code** of length 3.

- 1. We learned how to calculate with bitstrings.
- 2. $\mathbb{F}_2^n$ consists of the bitstrings of length $n$.
- 3. The received message is the binary sum of the sent message and the error vector.
- 4. The repetition code of length 3 corrects one bit error.

## Exercises 1.1

- 1.1.1. Compute the sum of 11001 and 01110.
- 1.1.2. Assume 000000 was sent and two errors occurred. List all possible received messages.
- 1.1.3. Let $x = 1101$ be the message to be sent. Encode $x$ using the repetition code of length 3.
- 1.1.4. Assume the repetition code of length 3 is used and 000110111101 is received. What is the result of decoding?
- 1.1.5. Why does the Morse code represent letters E and T by strings of length 1, whereas letters like Q, V, Z are represented by longer bitstrings?

## 1.2 The Hamming distance

**Basic concepts:** The Hamming distance as a metric, the weight of a bitstring.

## 1.3 Definition.

Let $x = (x_1, x_2, ..., x_n)$ and $y = (y_1, y_2, ..., y_n)$ be bitstrings in $\mathbb{F}_2^n$. The distance (or Hamming distance) between $x$ and $y$ is $d(x, y) = \text{number of coordinates } i \text{ where } x_i \neq y_i.$

Here are some examples:

d(0000, 1111) = 4, d(00110, 00101) = 2, d(111111, 001100) = 4.

Expressed in the context of messages and errors, d(x, y) is the minimum number of errors transforming x into y. In fact, consider the second example above: x = 00110 and y = 00101 differ in the last two coordinates, d(x, y) = 2 and x + 00011 = y.

Things get even easier when we use the weight.

## 1.4 Definition. The weight wt(x) of the bitstring x ∈ 𝔽₂ⁿ is the number of nonzero coordinates in x.

Here are some examples:

wt(0000) = 0, wt(1111) = 4, wt(00110) = 2, wt(001101) = 3.

The weight of a bitstring is its distance from the all-0 bitstring. If the all-0 bitstring is sent and w errors occur during transmission, then the received message has weight w. If x is sent, e is the error vector and y = x + e is received, then d(x, y) = wt(e).

The Hamming distance is also called the Hamming metric. The general notion of a metric is widely used in mathematics. Here is the definition:

## 1.5 Definition. Let X be a set. For every pair x ∈ X, y ∈ X let a real number d(x, y) be given (the distance from x to y). The function d is called a metric if the following are satisfied:

- - d(x, y) ≥ 0 for all x, y.
- - d(y, x) = d(x, y) for all x, y.
- - d(x, y) = 0 if and only if x = y.
- - d(x, z) ≤ d(x, y) + d(y, z) for all x, y, z.

The last requirement is the most important. It is known as the triangle inequality. A famous metric is the Euclidean metric in Euclidean space. If, for example, x = (x₁, x₂) and y = (y₁, y₂) are two points in the plane, then their Euclidean distance is √(x₁ − y₁)² + (x₂ − y₂)².

## 1.6 Theorem. The Hamming distance is a metric on 𝔽₂ⁿ.

Most of the properties of Definition 1.5 are obvious. Only the triangle inequality is a little interesting. This is left as an exercise.

- 1. The Hamming distance between two bitstrings of the same length is the number of coordinates where they differ.
- 2. $d(x, y)$ is the number of bit errors needed to transform $x$ into $y$.
- 3. The Hamming distance is a metric.
- 4. The weight is the distance from the all-0 vector.
- 5. $d(x, y) = wt(x + y)$.
- 6. If bitstring $x$ is sent and $y$ is received, then $d(x, y) = wt(e)$ is the weight of the error vector.

## Exercises 1.2

- 1.2.1. Compute $d(11001,01110)$ and $d(0000,0110)$.
- 1.2.2. Find $wt(00110)$ and $wt(10111)$.
- 1.2.3. List all vectors in $\mathbb{F}_2^6$ at distance 3 from 111000.
- 1.2.4. The alphabet has 26 letters. If we want to represent all possible words of length $\leq 3$ (all letters, pairs of letters and triples of letters) as bitstrings of the same length $n$, what is the smallest number $n$ such that this is possible?
- 1.2.5. Prove that the Hamming distance is a metric.
- 1.2.6. Assume $x$ is sent and $y = x + e$ is received. What can we say about $d(x, y)$ and about $wt(e)$ if not more than 3 errors have occurred?

## 1.3 Binary codes

**Basic concepts:** Length, minimum distance. The idea of error correction.
