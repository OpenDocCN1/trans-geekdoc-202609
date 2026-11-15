Now the formal way to say that encryptions of m_L “look like” encryptions of m_R is:

> “an encryption scheme is a good one if, when you plug its KeyGen and Enc algorithms into the template of the eavesdrop subroutines above, the two implementations of eavesdrop induce identical behavior in every calling program.”

**Example** Does one-time pad satisfy this new security property? To find out, we plug in its algorithms to the above template, and obtain the following implementations:

```
EAVESDROP(m_L, m_R):
 k ← {0, 1}^λ // KeyGen of OTP
 c := k ⊕ m_L // Enc of OTP
 return c
```

```
EAVESDROP(m_L, m_R):
 k ← {0, 1}^λ // KeyGen of OTP
 c := k ⊕ m_R // Enc of OTP
 return c
```

If these two implementations have the same effect on all calling programs (and indeed they do), then we would say that OTP satisfies this security property.

Is this a better/worse way to define security than the previous way? One security definition considers an attacker whose goal is to distinguish real ciphertexts from random values (real-vs-random paradigm), and the other considers an attacker whose goal is to distinguish real ciphertexts of two different plaintexts (left-vs-right paradigm). Is one “correct” and the other one “incorrect?” We save such discussion until later in the chapter.

# 2.2 Formalisms for Security Definitions

So far, we’ve defined security in terms of a single, self-contained subroutine, and imagined the attacker as a program that calls this subroutine. Later in the course we will need to generalize beyond a single subroutine, to a collection of subroutines that share common (private) state information. Staying with the software terminology, we call this collection a library:

**Definition 2.3 (Libraries)** A library L is a collection of subroutines and private/static variables. A library’s interface consists of the names, argument types, and output type of all of its subroutines (just like a Java interface). If a program A includes calls to subroutines in the interface of L, then we write A ◊ L to denote the result of linking A to L in the natural way (answering those subroutine calls using the implementation specified in L). We write A ◊ L ⇒ z to denote the event that program A ◊ L outputs the value z.

If A or L is a program that makes random choices, then the output of A ◊ L is a random variable. It is often useful to consider probabilities like Pr[A ◊ L ⇒ true].

**Example** Here is a familiar library:

| L |
|---|
| CTXT(m): |
| k ← {0, 1}^λ |
| c := k ⊕ m |
| return c |