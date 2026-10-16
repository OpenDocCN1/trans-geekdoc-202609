
# As you’ll learn in this chapter and the next, different types of algorithms require different types of keys. In private key (or secret key) cryptosystems, all participants use a single shared key. In public key cryptosystems, each participant has their own pair of keys. Cryptographic keys are sometimes referred to as `cryptovariables`.

The art of creating and implementing secret codes and ciphers is known as `cryptography`. This practice is paralleled by the art of `cryptanalysis`—the study of methods to defeat codes and ciphers. Together, cryptography and cryptanalysis are commonly referred to as `cryptology`. Specific implementations of a code or cipher in hardware and software are known as `cryptosystems`. Federal Information Processing Standard (FIPS) 140–2, “Security Requirements for Cryptographic Modules,” defines the hardware and software requirements for cryptographic modules that the federal government uses.

## Cryptographic Mathematics

Cryptography is no different from most computer science disciplines in that it finds its foundations in the science of mathematics. To fully understand cryptography, you must first understand the basics of binary mathematics and the logical operations used to manipulate binary values. The following sections present a brief look at some of the most fundamental concepts with which you should be familiar.

### Boolean Mathematics

*Boolean mathematics* defines the rules used for the bits and bytes that form the nervous system of any computer. You’re most likely familiar with the decimal system. It is a base 10 system in which an integer from 0 to 9 is used in each place and each place value is a multiple of 10. It’s likely that our reliance on the decimal system has biological origins—human beings have 10 fingers that can be used to count.

Similarly, the computer’s reliance upon the Boolean system has electrical origins. In an electrical circuit, there are only two possible states—on (representing the presence of electrical current) and off (representing the absence of electrical current). All computation performed by an electrical device must be expressed in these terms, giving rise to the use of Boolean computation in modern electronics. In general, computer scientists refer to the on condition as a `true` value and the off condition as a `false` value.

### Logical Operations

The Boolean mathematics of cryptography uses a variety of logical functions to manipulate data. We’ll take a brief look at several of these operations.

#### AND

The AND operation (represented by the ∧ symbol) checks to see whether two values are both true. The truth table that follows illustrates all four possible outputs for the AND function. Remember, the AND function takes only two variables as input. In Boolean math, there are only two possible values for each of these variables, leading to four possible inputs to the AND function. It’s this finite number of possibilities that makes it extremely easy for computers to implement logical functions in hardware. Notice in the following truth table that only one combination of inputs (where both inputs are true) produces an output value of true:

| X || Y || X ∧ Y |
| --- | --- | --- |
| 0 || 0 || 0 |
| 0 || 1 || 0 |
| 1 || 0 || 0 |
| 1 || 1 || 1 |

Logical operations are often performed on entire Boolean words rather than single values. Take a look at the following example:

```
X: 0 1 1 0 1 1 0 0
Y: 1 0 1 0 0 1 1 1
___________________________
X ∧ Y: 0 0 1 0 0 1 0 0
```

Notice that the AND function is computed by comparing the values of X and Y in each column. The output value is true only in columns where both X and Y are true.

#### OR

The OR operation (represented by the ∨ symbol) checks to see whether at least one of the input values is true. Refer to the following truth table for all possible values of the OR function. Notice that the only time the OR function returns a false value is when both of the input values are false:

| X || Y || X ∨ Y |
| --- | --- | --- |
| 0 || 0 || 0 |
| 0 || 1 || 1 |
| 1 || 0 || 1 |
| 1 || 1 || 1 |

We’ll use the same example we used in the previous section to show you what the output would be if X and Y were fed into the OR function rather than the AND function:

```
X: 0 1 1 0 1 1 0 0
Y: 1 0 1 0 0 1 1 1
___________________________
X ∨ Y: 1 1 1 0 1 1 1 1
```

#### NOT

The NOT operation (represented by the ∼ or ! symbol) simply reverses the value of an input variable. This function operates on only one variable at a time. Here’s the truth table for the NOT function:

| X || ~X |
| --- | --- |
| 0 || 1 |
| 1 || 0 |

In this example, you take the value of X from the previous examples and run the NOT function against it:

```
X: 0 1 1 0 1 1 0 0
___________________________
~X: 1 0 0 1 0 0 1 1
```

#### Exclusive OR

The final logical function you’ll examine in this chapter is perhaps the most important and most commonly used in cryptographic applications—the exclusive OR (XOR) function. It’s referred to in mathematical literature as the XOR function and is commonly represented by the ⊕ symbol. The XOR function returns a true value when only one of the input values is true. If both values are false or both values are true, the output of the XOR function is false. Here is the truth table for the XOR operation:

| X || Y || X ⊕ Y |
| --- | --- | --- |
| 0 || 0 || 0 |
| 0 || 1 || 1 |
| 1 || 0 || 1 |
| 1 || 1 || 0 |

The following operation shows the X and Y values when they are used as input to the XOR function:

```
X: 0 1 1 0 1 1 0 0
Y: 1 0 1 0 0 1 1 1
___________________________
X ⊕ Y: 1 1 0 0 1 0 1 1
```

#### Modulo Function

The *modulo* function is extremely important in the field of cryptography. Think back to the early days when you first learned division. At that time, you weren’t familiar with decimal numbers and compensated by showing a remainder value each time you performed a division operation. Computers don’t naturally understand the decimal system either, and these remainder values play a critical role when computers perform many mathematical functions. The modulo function is, quite simply, the remainder value left over after a division operation is performed.

The modulo function is usually represented in equations by the abbreviation *mod*, although it’s also sometimes represented by the % operator. Here are several inputs and outputs for the modulo function:

```
8 mod 6 = 2
6 mod 8 = 6
10 mod 3 = 1
10 mod 2 = 0
32 mod 8 = 0
```

We’ll revisit this function in Chapter 7 when we explore the RSA public key encryption algorithm (named after Rivest, Shamir, and Adleman, its inventors).

#### One-Way Functions

A *one-way function* is a mathematical operation that easily produces output values for each possible combination of inputs but makes it impossible to retrieve the input values. Public key cryptosystems are all based on some sort of one-way function. In practice, however, it’s never been proven that any specific known function is truly one way. Cryptographers rely on functions that they believe are one way, but it’s always possible that they might be broken by future cryptanalysts.
