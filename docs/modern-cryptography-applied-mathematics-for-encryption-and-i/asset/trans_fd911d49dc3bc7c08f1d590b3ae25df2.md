
After the matrix multiplication is complete, XOR the resultant value by the decimal number 99 (the hexadecimal number 0x63, the binary number 1100011, and the bit string 11000110 representing the number in least significant bit first notation). This value is termed the `translation vector`. This last operation, the final XOR, is meant to prevent any situation wherein the output is the same as the input—in other words to prevent S-box(a)=a.

### An Example Generating the S-Box

It may be helpful for you to see an actual example generating the S-box.

1. Take a number for GF(2⁸)—let’s pick 7. Looking at the multiplicative inverse table gives us `d1` in hex or 11010001 in binary.

2. Now we need to do four iterations of the process of affine transformation. We start by putting the multiplicative inverse into two variables `s` and `x`:

   ``` 
   s = 11010001
   x = 11010001
   ```

3. Now we simply rotate `s` (10001101) to the left = 00011010

   ![image](Images/image00484.jpeg) If the high bit is 1 make the low bit 1

   ![image](Images/image00484.jpeg) Else low bit is 0

4. In this case, the high bit was 1, so we change the low bit, thus

   ``` 
   s = 00011011
   ```

5. XOR that number with `x` so 00011011 XOR 10001101 = 10010110

   ``` 
   s = 00011011; x = 10010110
   ```

6. Next rotate `s` (00011011) to the left = 00110110.

   A. If this still gives us 00110110, XOR with `x`, so

       00110110 XOR 10010110 = 10100000

       s = 00110110; x = 10100000

7. Next rotate `s` (00110110) to the left = 01101100.

   A. If this still gives us 01101100, XOR with `x`, so

       01101100 XOR 10100000 = 11001100

       s = 01101100; x = 11001100

8. Next rotate `s` (01101100) to the left = 11011000.

   A. If this still gives us 11011000, XOR with `x`, so

       01101100 XOR 11001100 = 00010100

       s = 11011000; x = 00010100

9. Now `x` (00010100) gets XOR’d with decimal 99 (hex x63 binary 1100011) = 1110111 or 77.

Remember the output of the matrix multiplication (which we have accomplished via shift operations) is finally XOR’d with the translation vector (decimal 99). This process allows you to create the Rijndael S-box, and it is in fact how that S-box is often created in code.

### Changing the Rijndael S-Box

After studying the previous section, you should realize that there are three factors in generating the AES S-box. The first is the selection of the irreducible polynomial—in this case it was P = *x*⁸ + *x*⁴ + *x*³ + *x* + 1, which is 11B in hexadecimal notation, or 100011011 in binary numbers. As I mentioned previously, the creators of the Rijndael cipher stated clearly that this number was chosen simply because it was the first on the list of irreducible polynomials of degree 8 in the reference book they chose. That means that you could choose other irreducible polynomials.

In fact, you can choose from a total of 30 irreducible polynomials of degree 8, and this gives you 29 alternatives to the traditional S-box for AES, each with well-tested security. For more details on this alternative, you can look into Rabin’s test for irreducibility (see [http://math.stackexchange.com/questions/528552/rabins-test-for-polynomial-irreducibility-over-mathbbf-2](http://math.stackexchange.com/questions/528552/rabins-test-for-polynomial-irreducibility-over-mathbbf-2)). In their paper “Random S-Box Generation in AES by Changing Irreducible Polynomial,” Das, Sanjoy, Subhrapratim, and Subhash^([10](#part0017.xhtml#ch08note10a)) demonstrated an equally secure variation of the Rijndael, by changing the chosen irreducible polynomial. You can use any of the 30 possible irreducible polynomials; each of these is equally secure to the original Rijndael cipher S-box.

**Note**

Altering the Rijndael S-box is practical only if you have the ability to ensure that all parties to encrypted communication will be using your modified S-box. If you simply modify the S-box on your end, you would render communication with other parties impossible. Even though those other parties will have the same key and the same algorithm (AES), they will be using standard S-boxes. This is why altering AES S-boxes is primarily an issue for government entities that want to have secure communication with a limited number of involved parties.

A second option, one that may be the simplest to implement, is to change the translation vector (the final number you XOR with). Obviously, there are 255 possible variations. Rather than use 0x63, you can use any of the other possible variations for that final byte. Although simple to implement, it may be more difficult to test. Some variations might adversely affect one of the three criteria that you are attempting to maintain. In fact, selecting the wrong translation vector may lead to no change at all when it is applied to the product of the preceding matrix multiplication.

The third method is to change the affine transform, and this can be more difficult to implement but safe if you simply alter parameters within the existing transform. Section 5.2 of Sinha and Arya’s paper “Algebraic Construction and Cryptographic Properties of Rijndael Substitution Box”^([11](#part0017.xhtml#ch08note11a)) discusses this in detail. According to Cui, et al.,^([12](#part0017.xhtml#ch08note12a)) the choice of affine transformation matrix or irreducible polynomial has no significant impact on the security of the resultant cipher text.

### Conclusions

The S-box (or in some cases, S-boxes) is a critical part of most block ciphers. To understand any block cipher fully, you need to have some understanding of S-box design. S-boxes fall into two main categories: substitution and permutation. Either of these can be divided into three subcategories: straight, compression, and expansion.

In addition to S-boxes in general, the Rijndael S-box warrants particular attention. In addition to the standard Rijndael S-box commonly used, three relatively simple methods can be used to alter the S-box used in the Rijndael cipher. This will lead to permutations of Rijndael that are equal, or very nearly equal, in security to the original cipher. Using such permutations can lead to private versions of the AES algorithm, which can be useful for certain governmental and military applications.

If you want to delve into S-box design beyond the scope of this chapter, unfortunately there are no books on S-box design. As mentioned, many cryptography texts avoid this topic altogether or provide cursory coverage. You may, however, find a few sources useful (beyond those cited in the chapter endnotes), which can be found online using a Google search:

![image](Images/image00484.jpeg) Dawson and Tavares, “An Expanded Set of S-box Design Criteria Based on Information Theory and Its Relation to Differential-Like Attacks.”

![image](Images/image00484.jpeg) Adams and Tavares, “The Use of Bent Sequences to Achieve Higher-Order Strict Avalanche Criterion in S-Box Design.”

### Test Your Knowledge

[1](#part0017.xhtml#ch08qu1a). In mathematics, the _\_\_\_\_\_\_\_\_\_\_\_\_ of a number x_ is the number that, when multiplied by _x_, yields 1.

[2](#part0017.xhtml#ch08qu2a). What is the irreducible polynomial used in standard AES?

[3](#part0017.xhtml#ch08qu3a). What is the strict avalanche criterion in S-box design?

[4](#part0017.xhtml#ch08qu4a). What is the bit independence criterion in S-box design?

[5](#part0017.xhtml#ch08qu5a). What is the value of the Rijndael translation vector?

[6](#part0017.xhtml#ch08qu6a). How many irreducible polynomials are there for the generation of the Rijndael S-box?

[7](#part0017.xhtml#ch08qu7a). What is the primary advantage that DES S-boxes convey on the DES cipher?

