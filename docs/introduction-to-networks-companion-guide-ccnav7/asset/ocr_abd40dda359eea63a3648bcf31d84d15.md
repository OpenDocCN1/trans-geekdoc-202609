The 32-bit IPv4 address space provides approximately 4,294,967,296 unique addresses. IPv6 address space provides 340,282,366,920,938,463,374,607,431,768,211,456, or 340 undecillion addresses. This is roughly equivalent to every grain of sand on Earth.

Figure 8-8 compares the IPv4 address space and the IPv6 address space.

| Number Name | Scientific Notation | Number of Zeros |
|---|---|---|
| 1 Thousand | 10^3 | 1,000 |
| 1 Million | 10^6 | 1,000,000 |
| 1 Billion | 10^9 | 1,000,000,000 |
| 1 Trillion | 10^12 | 1,000,000,000,000 |
| 1 Quadrillion | 10^15 | 1,000,000,000,000,000 |
| 1 Quintillion | 10^18 | 1,000,000,000,000,000,000 |
| 1 Sextillion | 10^21 | 1,000,000,000,000,000,000,000 |
| 1 Septillion | 10^24 | 1,000,000,000,000,000,000,000,000 |
| 1 Octillion | 10^27 | 1,000,000,000,000,000,000,000,000,000 |
| 1 Nonillion | 10^30 | 1,000,000,000,000,000,000,000,000,000,000 |
| 1 Decillion | 10^33 | 1,000,000,000,000,000,000,000,000,000,000,000 |
| 1 Undecillion | 10^36 | 1,000,000,000,000,000,000,000,000,000,000,000,000 |

Figure 8-8 IPv4 and IPv6 Address Space

# IPv4 Packet Header Fields in the IPv6 Packet Header (8.3.3)

One of the major design improvements of IPv6 over IPv4 is the simplified IPv6 header.

The IPv4 header consists of a variable-length header of 20 octets (up to 60 bytes if the Options field is used) and 12 basic header fields, not including the Options field and the Padding field.

For IPv6, some fields have remained the same, some fields have changed names and positions, and some IPv4 fields are no longer required, as highlighted in Figure 8-9.

The simplified IPv6 header shown in Figure 8-10 consists of a fixed-length header of 40 octets (largely due to the length of the source and destination IPv6 addresses).

The simplified IPv6 headers can be processed more efficiently than IPv4 headers.