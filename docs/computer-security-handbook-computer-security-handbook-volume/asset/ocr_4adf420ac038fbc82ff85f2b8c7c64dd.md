![](bbox=[0.24, 0.07, 0.68, 0.35])

EXHIBIT 4.2 Vertical and Longitudinal Parity,
Seven-Track Magnetic Tape

character is generated after some predetermined number of data characters. Each bit in the extra character provides parity for its corresponding row, just as the vertical parity bits do for their corresponding columns. Exhibit 4.2 represents both types as they would be recorded on 7-track magnetic tape. One bit has been circled to show that it is ambiguous. This bit appears at the intersection of the parity row and the parity column, and must be predetermined to be correct for one or the other, as it may not be correct for both. In the illustration, the ambiguous bit is correct for the odd parity requirement of the VRC character column; it is incorrect for the even parity of the LRC bit row.

In actual practice, the vertical checkbits would be attached to each character column as shown, but the longitudinal bits would follow a block of data that might contain 80 to several hundred characters. Where it is possible to use both LRC and VRC, any single data error in a block will be located at the intersection of incorrect row and column parity bits. The indicated bit may then be corrected automatically. The limitations of this method are: (1) multiple errors cannot be corrected, (2) an error in the ambiguous position cannot be corrected, and (3) an error that does not produce both a VRC and LRC indication cannot be corrected.

# 4.3.3 Cyclical Redundancy Checks.

Where the cost of a data error could be high, the added expense of cyclical redundancy checks (CRCs) is warranted. In this technique, a relatively large number of redundant bits is used. For example, each 4-bit character requires 3 parity bits, while a 32-bit computer word needs 6 parity bits. Extra storage space is required in main and secondary memory, and transmissions take longer than without such checks. The advantage, however, is that any single error can be detected, whether in a data bit or a parity bit, and its location can be positively identified. By a simple electronic process of complementation, an incorrect 0 is converted to a 1, and vice versa.

# 4.3.4 Self-Checking Codes.

Several types of codes are in use that inherently contain a checking ability similar to that of the parity system. Typical of these is the 2-of-5 code, in which every decimal digit is represented by a bit configuration containing exactly two 1s and three 0s. Where a parity test would consist of counting 1s to see if their number was odd or even, a 2-of-5 test would indicate an error whenever the number of 1s was more or less than 2.