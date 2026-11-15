128 64 32 16 8 4 2 1
0   1   1

+   7. Find the difference of 20 and 16, or 4.

+   8. Put a 1 under the 4, as the largest number under 0d4 is 4.

| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 0 | 1 | | | | 1 | | |

+   9. Find the difference of 4 and 4, or 0.

+   10. With the difference 0, fill the remaining places with 0s.

| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 0 | 1 | | | | 1 | | |

The binary result is 0b1010100.

> It is tempting to avoid the tedium of these conversion calculations by hand and instead use a computer program. Such *epop* code is available in Appendix sections C.1 and C.2.

# 4.1.2 The Remainder Method

Another technique for base conversion is called the *remainder method*. To expedite this method, we will define some variables: the initial number N, the target base B, a quotient Q, and a remainder R.

Use the following steps:

+   1. Divide N by B to find Q and R.

+   2. Record R. The 1st R will be the least significant (rightmost) digit.

+   3. Let N = Q.