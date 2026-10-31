
```
[ESP] 0012FF18 65766552 “eveR” is pushed here, in little endian
[ESP+0x04] 0012FF1C 45657372 “Eesr” will be pushed here, in little endian
[ESP+0x08] 0012FF20 0067676E “ ggn” is pushed here, in little endian
[ESP+0x0C] 0012FF24 65766552 “eveR” is pushed here in dest array
[ESP+0x10] 0012FF28 45657372 “Eesr” will be pushed here in dest array
[ESP+0x14] 0012FF2C 0067676E “ggn” is pushed here in dest array
[ESP+0x18] 0012FF30 0040344B JUNK HERE
[ESP+0x1C] 0012FF34 0012FF48 JUNK HERE
[ESP+0x20] 0012FF38 004028CE JUNK HERE
[ESP+0x24] 0012FF3C 0040344B JUNK HERE
[ESP+0x28] 0012FF40 8E02AEA1 XOR of stack cookie and EBP stored here
[ESP+0x2C] 0012FF44 004012A0 ESP at the start of main procedure
```

![](images/Figure-14.28.jpg)

**Figure 14.28:** Stack with src and dest array

As we saw in the preceding instructions, the `dest` array is not NULL terminated as we move out of the loop before NULL is copied to `0x0012FF2F`. The answer lies in the next instruction. Let’s move on to the next instructions:

### Line 95-99

```
mov BYTE PTR [eax], cl
lea eax, DWORD PTR _dest$[esp+44]
push eax
push OFFSET $SG4690
call _printf
```

In the first preceding `MOV` instruction, the ASM code moves 0x00 byte from the `CL` register to `0x0012FF2F`. This will NULL terminate the `dest` array shown as follows:

| 65 “e”0x0012FF1B || 76 “v”0x0012FF1A || 65 “e”0x0012FF19 || 52 “R”0x0012FF18 |
| --- | --- | --- | --- |
| 45 “E”0x0012FF1F || 65 “e”0x0012FF1E || 73 “s”0x0012FF1D || 72 “r”0x0012FF1C |
| 000x0012FF23 || 67 “g”0x0012FF22 || 67 “g”0x0012FF21 || 6E “n”0x0012FF20 |
| 65 “e”0x0012FF27 || 76 “v”0x0012FF26 || 65 “e”0x0012FF25 || 52 “R”0x0012FF24 |
| 45 “E”0x0012FF2B || 65 “e”0x0012FF2A || 73 “s”0x0012FF29 || 72 “r”0x0012FF28 |
| 00 “\0”0x0012FF2F || 67 “g”0x0012FF2E || 67 “g”0x0012FF2D || 6E “n”0x0012FF2C |

**Table 14.4:** Stack with the src and dest array - Part-4

Now, we have a pointer to the `src` array (`0x0012FF18`) and a pointer to the `dest` array (`0x0012FF24`) on the stack. Next, we have to call the `printf` function for which the arguments to `printf` need to be pushed onto the stack.

The `LEA` instruction moves the pointer from the `dest` array to `EAX`. The `PUSH` instruction pushes the first argument onto the stack by `PUSH EAX`.

The second `PUSH` instruction pushes the string constant onto the stack, which is the second argument to `printf`. Once both arguments are pushed, a call to `printf` is made. The stack state before the execution of the `CALL` instruction is as follows:

```
[ESP] 0012FF10 0040814C "%s\n", second argument to printf is pushed here
[ESP+0x04] 0012FF14 0012FF24 "ReverseEngg", second argument to printf()is pushed
[ESP+0x08] 0012FF18 65766552 “eveR” is pushed here, in little endian
[ESP+0x0C] 0012FF1C 45657372 “Eesr” will be pushed here, in little endian
[ESP+0x10] 0012FF20 0067676E “ ggn” is pushed here, in little endian
[ESP+0x14] 0012FF24 65766552 “eveR” is pushed here in dest array
[ESP+0x18] 0012FF28 45657372 “Eesr” will be pushed here in dest array
[ESP+0x1C] 0012FF2C 0067676E “ggn” is pushed here in dest array
[ESP+0x20] 0012FF30 0040344B JUNK HERE
[ESP+0x24] 0012FF34 0012FF48 JUNK HERE
[ESP+0x28] 0012FF38 004028CE JUNK HERE
[ESP+0x2C] 0012FF3C 0040344B JUNK HERE
[ESP+0x30] 0012FF40 8E02AEA1 XOR of stack cookie and EBP stored here
[ESP+0x34] 0012FF44 004012A0 ESP at the start of main procedure
```

![](images/Figure-14.29.jpg)

**Figure 14.29:** Stack before CALL instruction

### Line 100-110

```
; Line 42
mov ecx, DWORD PTR __$ArrayPad$[esp+52]
add esp, 8
xor ecx, esp
xor eax, eax
call @__security_check_cookie@4
add esp, 44     ; 0000002cH
ret 0
_main ENDP
_TEXT ENDS
END
```

In the preceding ASM code, the `MOV` instruction moves the stack cookie stored at `[ESP+0x30]` to `ECX`, where it is XOR’ed with `ECX` to check the buffer overflow condition by calling the `security_check_cookie` procedure. The rest of the `ADD` instructions clean up the stack to end the `main` procedure, TEXT segment, and code. The stack state before the `RET` instruction is as follows:

```
[ESP-0x34] 0012FF10 0040814C Now JUNK HERE
[ESP-0x30] 0012FF14 0012FF24 Now JUNK HERE
[ESP-0x2C] 0012FF18 65766552 Now JUNK HERE
[ESP-0x28] 0012FF1C 45657372 Now JUNK HERE
[ESP-0x24] 0012FF20 0067676E Now JUNK HERE
[ESP-0x20] 0012FF24 65766552 Now JUNK HERE
[ESP-0x1C] 0012FF28 45657372 Now JUNK HERE
[ESP-0x18] 0012FF2C 0067676E Now JUNK HERE
[ESP-0x14] 0012FF30 0040344B Now JUNK HERE
[ESP-0x10] 0012FF34 0012FF48 Now JUNK HERE
[ESP-0x0C] 0012FF38 004028CE Now JUNK HERE
[ESP-0x08] 0012FF3C 0040344B Now JUNK HERE
[ESP-0x04] 0012FF40 8E02AEA1 Now JUNK HERE
[ESP] 0012FF44 004012A0 ESP at the start of main procedure
```

![](images/Figure-14.30.jpg)

**Figure 14.30:** Stack cleaned

# Conclusion

In this chapter, we covered the `strcpy` function implementation by copying data from one memory location to another with respect to reverse engineering. We also learned about byte-by-byte operations that happen during the `strcpy` execution. In the optimized assembly listing, during the stack cookie operation, the `XOR` procedure happens with `ESP` and in a non-optimized assembly listing, it happens with `EBP`. We also covered the difference between optimized and non-optimized codes of `strcpy` program assembly pattern. In the next chapter, we will talk about another real-world example, wherein we will write a program to calculate simple interest code.

# CHAPTER 15

## Simple Interest Code Pattern in Reverse Engineering

We all dream about buying a beautiful house and a nice car. Now to buy any of these, we need money which can either be earned with our skills or it can be borrowed from a bank. This is where terms like interest come into picture. Imaging a person named Atul Narula who works for International Institute of Cyber Security and wants to buy a car. Now, Atul has savings of 10,000 dollars and decides to take the remaining 10,000 dollars from a bank. A bank offers him a loan on an annual simple interest rate of 2 percent for a term of 5 years. Atul goes to the bank and asks the bank official about the interest that he has to pay over the term of the loan. The bank official uses a software which uses a mathematical formula to calculate interest. The mathematical formula that goes inside the software will be $10,000 times 2 percent times 5 years, or 10,000 x .02 x 5. This is the interest amount Atul has to pay over the entire term of the loan.

Now imagine, as a reverse engineer, you have to extract the mathematical formula of this banking software without any access to the software code. In this chapter, we will use this real-life software example to understand the assembly pattern of such kinds of software. This type of reverse engineering will help you understand some patterns used by malware writers.

## Structure

In this chapter, we will cover the following topics:

* Program to calculate simple interest
* Calculate simple interest without Optimization

## Objective

In this chapter, we will talk about a real-life software that uses an internal mathematical formula to calculate simple interest. We will find out how an integer and float are together handled in memory. Reverse engineering a software with mathematical calculation will help us understand the assembly pattern of the software along with the mathematical calculations.

## Program to Calculate Simple Interest

Let’s write down a C/C++ program to calculate simple interest from a set of values represented by Principal Amount, Interest Amount, and Number of Years.

![](images/Figure-15.1.jpg)

**Figure 15.1:** `SimpleInterestCalculation.cpp`
