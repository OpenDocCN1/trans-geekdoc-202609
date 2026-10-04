
## Table 5-6 Converting 10101000 to Decimal

| Positional Value | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|---|---|---|---|---|---|---|---|---|
| Binary Number (10101000) | 1 | 0 | 1 | 0 | 1 | 0 | 0 | 0 |
| Calculate | 1 × 128 | 0 × 64 | 1 × 32 | 0 × 16 | 1 × 8 | 0 × 4 | 0 × 2 | 0 × 1 |
| Add Them Up... | 128 | + 0 | + 32 | + 0 | + 8 | + 0 | + 0 | + 0 |
| Result | 168 |  |  |  |  |  |  |  |

Convert the third octet of 00001011 as shown in Table 5-7.

## Table 5-7 Converting 00001011 to Decimal

| Positional Value | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|---|---|---|---|---|---|---|---|---|
| Binary Number (00001011) | 0 | 0 | 0 | 0 | 1 | 0 | 1 | 1 |
| Calculate | 0 × 128 | 0 × 64 | 0 × 32 | 0 × 16 | 1 × 8 | 0 × 4 | 1 × 2 | 1 × 1 |
| Add Them Up... | 0 | + 0 | + 0 | + 0 | + 8 | + 0 | + 2 | + 1 |
| Result | 11 |  |  |  |  |  |  |  |

Convert the fourth octet of 00001010 as shown in Table 5-8. This completes the IP address and produces the dotted decimal result 192.168.11.10.

## Table 5-8 Converting 00001010 to Decimal

| Positional Value | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|---|---|---|---|---|---|---|---|---|
| Binary Number (00001010) | 0 | 0 | 0 | 0 | 1 | 0 | 1 | 0 |
| Calculate | 0 × 128 | 0 × 64 | 0 × 32 | 0 × 16 | 1 × 8 | 0 × 4 | 1 × 2 | 0 × 1 |
| Add Them Up... | 0 | + 0 | + 0 | + 0 | + 8 | + 0 | + 2 | + 0 |
| Result | 10 |  |  |  |  |  |  |  |

![](img/e71dc48d3ae3db3394e5857ab2acae75_217_0.png)

## Activity—Binary to Decimal Conversions (5.1.6)

This activity allows you to practice 8-bit binary to decimal conversion as much as necessary. We recommend that you work with this tool until you are able to do the conversion without error. Convert the binary number shown in the octet to its decimal value.

Refer to the online course to complete this activity.

## Decimal to Binary Conversion (5.1.7)

It is also necessary to understand how to convert a dotted decimal IPv4 address to binary. A useful tool is the binary positional value table. Figures 5-3 through 5-10 show examples of this type of table. The following steps walk through how to use this table to do the conversion:

![](img/e71dc48d3ae3db3394e5857ab2acae75_218_0.png)

**Step 1.** In Figure 5-3, is the decimal number of the octet (*n*) equal to or greater than the most significant bit (**128**)?

- If no, then enter binary **0** in the **128** positional value.
- If yes, then add a binary **1** in the **128** positional value and subtract **128** from the decimal number.

![](img/e71dc48d3ae3db3394e5857ab2acae75_218_1.png)

**Figure 5-3 128 Positional Value**

**Step 2.** In Figure 5-4, is the decimal number of the octet (*n*) equal to or greater than the next most significant bit (**64**)?

- If no, then enter binary **0** in the **64** positional value.
- If yes, then add a binary **1** in the **64** positional value and subtract **64** from the decimal number.

**Step 3.** In Figure 5-5, is the decimal number of the octet (*n*) equal to or greater than the next most significant bit (**32**)?

- If no, then enter binary **0** in the **32** positional value.
- If yes, then add a binary **1** in the **32** positional value and subtract **32** from the decimal number.

![](img/e71dc48d3ae3db3394e5857ab2acae75_219_0.png)

## Figure 5-4 64 Positional Value

![](img/e71dc48d3ae3db3394e5857ab2acae75_219_1.png)

## Figure 5-5 32 Positional Value

## Step 4.

In Figure 5-6, is the decimal number of the octet (n) equal to or greater than the next most significant bit (16)?

- If no, then enter binary 0 in the 16 positional value.
- If yes, then add a binary 1 in the 16 positional value and subtract 16 from the decimal number.

![](img/e71dc48d3ae3db3394e5857ab2acae75_220_0.png)

## Figure 5-6 16 Positional Value

Step 5. In Figure 5-7, is the decimal number of the octet (n) equal to or greater than the next most significant bit (8)?

- If no, then enter binary 0 in the 8 positional value.
- If yes, then add a binary 1 in the 8 positional value and subtract 8 from the decimal number.

![](img/e71dc48d3ae3db3394e5857ab2acae75_220_1.png)

## Figure 5-7 8 Positional Value

## Step 6.

In Figure 5-8, is the decimal number of the octet (n) equal to or greater than the next most significant bit (4)?

- If no, then enter binary 0 in the 4 positional value.
- If yes, then add a binary 1 in the 4 positional value and subtract 4 from the decimal number.

![](img/e71dc48d3ae3db3394e5857ab2acae75_221_0.png)

## Figure 5-8 4 Positional Value

## Step 7.

In Figure 5-9, is the decimal number of the octet (n) equal to or greater than the next most significant bit (2)?

- If no, then enter binary 0 in the 2 positional value.
- If yes, then add a binary 1 in the 2 positional value and subtract 2 from the decimal number.

## Step 8.

In Figure 5-10, is the decimal number of the octet (n) equal to or greater than the last most significant bit (1)?

- If no, then enter binary 0 in the 1 positional value.
- If yes, then add a binary 1 in the 1 positional value and subtract 1 from the last decimal number.

![](img/e71dc48d3ae3db3394e5857ab2acae75_222_0.png)

Figure 5-9  2 Positional Value

![](img/e71dc48d3ae3db3394e5857ab2acae75_222_1.png)

Figure 5-10  1 Positional Value

## Decimal to Binary Conversion Example (5.1.8)

To help understand the process of converting from decimal to binary, consider the IP address 192.168.11.10.

The first octet number, 192, is converted to binary using the previously explained positional notation process.

It is possible to bypass the process of subtraction with easier or smaller decimal numbers. For instance, notice that it is fairly easy to calculate the third octet converted to a binary number without actually going through the subtraction process (8 + 2 = 10). The binary value of the third octet is 00001010.

The fourth octet is 11 (8 + 2 + 1). The binary value of the fourth octet is 00001011.

Converting between binary and decimal may seem challenging at first, but with practice, it should become easier over time.

Figures 5-11 through 5-21 illustrate the steps to convert the IP address 192.168.10.11 into binary:

## Step 1.

In Figure 5-11, is the first octet number 192 equal to or greater than the high-order bit 128?

- Yes it is, so add a 1 to the high-order positional value to represent 128.
- Subtract 128 from 192 to produce a remainder of 64.

![](img/e71dc48d3ae3db3394e5857ab2acae75_223_0.png)

Figure 5-11 Step 1

## Step 2.

In Figure 5-12, is the remainder 64 equal to or greater than the next high-order bit 64?

- It is equal, so add a 1 to next high-order positional value.

Example: 192.168.10.11

![](img/e71dc48d3ae3db3394e5857ab2acae75_224_0.png)

Figure 5-12 Step 2

Step 3. In Figure 5-13, since there is no remainder, enter binary 0 in the remaining positional values.

- The binary value of the first octet is 11000000.

Example: 192.168.10.11

![](img/e71dc48d3ae3db3394e5857ab2acae75_224_1.png)

Figure 5-13 Step 3

Step 4. In Figure 5-14, is the second octet number 168 equal to or greater than the high-order bit 128?

- Yes it is, so add a 1 to the high-order positional value to represent 128.
- Subtract 128 from 168 to produce a remainder of 40.

Example: 192.168.10.11

![](img/e71dc48d3ae3db3394e5857ab2acae75_225_0.png)

Figure 5-14 Step 4

Step 5. In Figure 5-15, is the remainder 40 equal to or greater than the next high-order bit 64?

- No it is not, so enter a binary 0 in the positional value.

Example: 192.168.10.11

![](img/e71dc48d3ae3db3394e5857ab2acae75_225_1.png)

Figure 5-15 Step 5

Step 6. In Figure 5-16, is the remainder 40 equal to or greater than the next high-order bit 32?

- Yes it is, so add a 1 to the high-order positional value to represent 32.
- Subtract 32 from 40 to produce a remainder of 8.

Example: 192.168.10.11

![](img/e71dc48d3ae3db3394e5857ab2acae75_226_0.png)

Figure 5-16 Step 6

Step 7. In Figure 5-17, is the remainder 8 equal to or greater than the next high-order bit 16?

- No it is not, so enter a binary 0 in the positional value.

Example: 192.168.10.11

![](img/e71dc48d3ae3db3394e5857ab2acae75_226_1.png)

Figure 5-17 Step 7

Step 8. In Figure 5-18, is the remainder 8 equal to or greater than the next high-order bit 8?

- It is equal, so add a 1 to next high-order positional value.
