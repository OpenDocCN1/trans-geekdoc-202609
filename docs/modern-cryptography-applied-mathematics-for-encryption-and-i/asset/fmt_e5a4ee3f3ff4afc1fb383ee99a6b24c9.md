
![Images](Images/image00516.jpeg)

*C* becomes *L*, and *K* becomes *M*, so the enciphered letters are *LM*. If you continue this process to the end of the plain text,

![Images](Images/image00517.jpeg)

is encrypted to yield

![Images](Images/image00518.jpeg)

Yes, this cipher does take some practice to master.

Note that the cipher disrupts the letter and word frequencies found in single-substitution ciphers, merely by encrypting digraphs instead of single letters.

### Two-Square Cipher

The *two-square cipher* is also often referred to as a double Playfair, for reasons that will soon become clear. Like the Playfair, it works on digraphs. There are two variations of the two-square cipher, the horizontal and the vertical, which refer to how the table’s squares are arranged. In the horizontal method, they are side-by-side, and in the vertical, the squares are arranged one on top of the other. Each square requires its own keyword, so the two-square cipher is based on using two keywords as well as two matrices.

Let’s consider an example of a vertical two-square cipher with the keywords *falcon* and *osprey*, shown here:

![Images](Images/image00519.jpeg)

As with the Playfair, you divide the plain text into digraphs. So *Attack at dawn* becomes *At ta ck at da wn*.

Next, you form a rectangle, as with Playfair, but the rectangle bridges both tables. Find the first letter of plain text in the top table and the second letter in the bottom table. In this case, *A* in the top table and *T* in the bottom forms the rectangle shown here:

![Images](Images/image00520.jpeg)

The letter *A* is in the upper-left corner, so you replace it with the letter in the upper-right corner, which is the letter *O*. The letter *T* is in the lower-right corner, so you replace it with the letter in the lower-left corner, *M*, providing the cipher text *OM*.

If you continue this process through the entire plain text, you will generate the cipher text shown here:

![Images](Images/image00521.jpeg)

Note that if the two letters in the digraph line up (that is, they appear in the same column in the two tables), the cipher text is the same as the plain text. If you are using the horizontal two-square cipher, the same rule applies if the two plain text characters are in the same row.

### Four-Square Cipher

As you can probably surmise, the *four-square cipher* takes the Playfair concept and expands it to use four squares. This cipher was invented by Félix Marie Delastelle (1840–1902), a Frenchman who invented several ciphers including the bifid, trifid, and four-square ciphers.

**Note**

Delastelle’s contributions to cryptography during the 1800s are numerous. He finished work on a book on cryptography, *Traité Élémentaire de Cryptographie* (*Elementary Treatise on Cryptography*) just 11 months before he died in April 1902, and the book was published 3 months after his death. Most notable is that Delastelle was an amateur cryptographer with no formal training in math.

To create a four-square cipher, you first create four matrices of 5-by-5 letters; usually, either the *Q* is omitted or the letters *I* and *J* are combined to account for all 26 letters in the alphabet. Notice that in the matrices shown next, in some cases I omitted the *Q*, and in others I combined *I* and *J*. Also note that the letters may, or may not, be in alphabetical order. In this cipher, the *two uppercase matrices are for the cipher text*, and the *two lowercase matrices are for the plain text*. This is why the two uppercase matrices are not in alphabetical order.

![Images](Images/image00522.jpeg)

You then split the message into digraphs, so that *Attack at dawn* becomes *at ta ck at da wn*.

The next part may seem a bit complex, so follow along carefully. First, find the first letter in the upper-left plain text matrix. In this case, the letter *a* is in the first row. Then find the second letter of the digraph in the lower-right plain text matrix. The letter *t* is in the fourth column. These two letters are in boldface and underlined here:

![Images](Images/image00523.jpeg)

Because we are dealing with a digraph, we need to encrypt both the *a* and the *t*. To find the first letter of the cipher text, use the upper-left matrix’s row of the first letter of plain text—in this case, *a* is in *row 1*—and the lower-right matrix’s column of the second letter of cipher text—*t* is in *column 4*. Look in the upper-right cipher text matrix and find that letter—row 1, column 4 is *R*. This is the first letter of the cipher text.

Then, to find the second letter of the cipher text, use the row of the second letter of plain text—in this case, *t* is in *row 4*—and the column of the first letter—*a* is in *column 1*. Then find that letter in the lower-left cipher text matrix—row 4, column 1 is the letter *L*. You can see this in the next four matrices, where the plain text letters are in boldface and the cipher text letters are in boldface and underlined.

![Images](Images/image00524.jpeg)

So, the first two letters, *at*, in plain text become *RL* in cipher text. You’d continue this process throughout the entire plain text phrase, yielding

![Images](Images/image00525.jpeg)

### Hill Cipher

The *Hill cipher* was invented by mathematician Lester S. Hill in 1929. It is a bit more complex than other ciphers we have studied thus far. It is based in linear algebra and uses matrix mathematics. To encrypt a message, you break the plain text into a block of *n* letters (called an *n*‑component vector). Each letter is represented by a number (a = 1, b = 2, c = 3, and so on); note that the number assignment is not critical—for example, some implementations start with a = 0. That block of numbers representing the block of plain text forms a matrix that is multiplied by some invertible *n*‑by‑*n* matrix, mod 26. (If you don’t have some math background, this may seem rather intimidating—not to worry, it will all be made clear.)

**Note**

Lester Hill was a mathematician who received his bachelor’s degree from Columbia in 1911 and his Ph.D. from Yale in 1926. He was a professor at several colleges including Princeton and Yale. His research interest included application of mathematics to communications, as evidenced by the Hill cipher. He also worked on methods to find errors in telegraph communications.

The matrix used is the key for this cipher. It should be selected randomly and be mod 26 (26 for the letters of the English alphabet; other alphabets would require a different mod). For our discussions on this cipher, we will use the following matrix as a key:

![Images](Images/image00526.jpeg)

**Note**

Although I am showing you a 3-by-3 matrix, you can use any size as long as it is a square.

For those readers not familiar with matrix math, I will show you just enough to allow you to understand the Hill cipher. [Chapters 4](#part0012.xhtml#ch04) and [5](#part0013.xhtml#ch05) will give you a better introduction to mathematics for cryptography. To understand multiplying a matrix by a vector, examine this example using letters:

![Images](Images/image00527.jpeg)

Each row of the original matrix is multiplied by each item in the vector to provide a resulting matrix.

In the case of the Hill cipher, the vector is simply numbers representing a block of text. Note that this conversion assumes 1 = a, 2 = b, and so on:

![Images](Images/image00528.jpeg)

is

![Images](Images/image00529.jpeg)

Now let’s break this down into three-character blocks:

![Images](Images/image00530.jpeg)

We multiply each vector times the numbers in the key. So the first line goes like this:

![Images](Images/image00531.jpeg)

That resulting vector (304, 543, 401) has to be mod 26, which produces

![Images](Images/image00532.jpeg)
