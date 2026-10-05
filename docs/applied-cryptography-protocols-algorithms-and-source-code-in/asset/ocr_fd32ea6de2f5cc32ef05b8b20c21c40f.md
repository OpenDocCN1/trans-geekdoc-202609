# CHAPTER 16 Pseudo-Random-Sequence Generators

If you only have a 16-bit computer, use this generator instead:

```
static int s1 = 1; /* An "int" must be 16 bits long. */
static int s2 = 1;
static int s3 = 1;

#define MODMULT(a,b,c,m,q) s/a; s = b*(s-a*q); if
(s<0) s+=m;

/* combined LCG linear congruandom real value in the
range
* (0,1). It combines linear congruential generators with
* periods of 2^31-405, 2^31-1111, and has a period
* that is the product of these three prime numbers. */
double combinedLCG( void ) {
    int q;
    int z;
    MODMULT(206, 157, 21, 32363, s1)
    MODMULT(217, 146, 45, 31727, s2)
    MODMULT(222, 142, 133, 31657, s3)
    z = s1 - s2;
    if (z > 706)
        z -= 32362;
    if (z < 0)
        z += 32362;
    return z * 3.0899e-5;
}
```

```
* In general, call initLCG before using combinedLCG. */
void initLCG(int initS1, int initS2, int initS3) {
    s1 = initS1;
    s2 = initS2;
    s3 = initS3;
}
```

This generator works as long as the machine can represent all integers between -32768 and 32763. The variables, s1, s2, and s3 are global; they hold the current state of the generator. Before the first call, they must be initialized. The variable s1 needs an initial value between 1 and 32762. The variable s2 needs an initial value between 1 and 31726. The variable s3 needs an initial value between 1 and 31656. This generator has a period of 1.6*10¹.
For of these generators, the constant term b in the linear congruence is 0.

# 16.2 LINEAR FEEDBACK SHIFT REGISTERS

Shift register sequences are used in both cryptography and coding theory. There is a wealth of theory about them; stream ciphers by shift registers have been the workhorse of military cryptography since the beginnings of electronics.