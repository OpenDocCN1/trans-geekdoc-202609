
The transport system can simply throw the data away. In this case, the transport is effectively transferring the responsibility of what to do about the error up to higher-level protocols or perhaps the application itself. As some applications may need a complete data set with no errors (think a file transfer system, or a financial transaction), they will likely have some way to discover any missing data and retransmit it. Applications that do not care about small amounts of missing data (think a voice stream) can simply ignore the missing data, reconstructing the information at the receiver as well as possible given the missing information.

The transport system can signal the transmitter that there is an error, and let the transmitter decide what to do with this information (generally the data in error will be retransmitted).

The transport system can go beyond throwing data away by including enough information in the original transmission and determine where the error is and attempt to correct it. This is called `Forward Error Correction` (FEC). `Hamming codes`, one of the first FEC mechanisms developed, is also one of the simplest to explain. The Hamming code is best explained by example; [Table 2-2](#ch02.xhtml#ch02tab02) will be used to illustrate.

**Table 2-2** *An Illustration of the Hamming Code*

|    || **1** || **2** || **3** || **4** || **5** || **6** || **7** || **8** || **9** || **10** || **11** || **12** |

| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

| **0001** || **0010** || **0011** || **0100** || **0101** || **0110** || **0111** || **1000** || **1001** || **1010** || **1011** || **1100** |

| P1 || P2 || D1 || P4 || D2 || D3 || D4 || P8 || D5 || D6 || D7 || D8 |

|   ||   || 1 ||   || 0 || 1 || 1 ||   || 0 || 0 || 1 || 1 |

| **P1** || 1 ||   || X ||   || X ||   || X ||   || X ||   || X ||   |

| **P2** ||   || 0 || X ||   ||   || X || X ||   ||   || X || X ||   |

| **P4** ||   ||   ||   || 1 || X || X || X ||   ||   ||   ||   || X |

| **P8** ||   ||   ||   ||   ||   ||   ||   || 0 || X || X || X || X |

In [Table 2-2](#ch02.xhtml#ch02tab02):

• Each bit in the 12-bit space that is a power of two (1, 2, 4, 6, 8, etc.) and the first bit are set aside as parity bits.

• The 8-bit number to be protected with FEC, `10110011`, has been distributed across the remaining bits in the 12-bit space.

• Each parity bit is set to 0, and then parity is calculated for each parity bit by adding the number of *1s* in positions where the binary bit number has the same bit set as the parity bit. Specifically:

• `P1` has the far-right bit set in its bit number; the other bits in the number space that also have the far right bit set are included in the parity calculation (see the second row in the table to find all the bit positions in the number with the far-right bit set). These are indicated in the table with an *X* in the `P1` row. The total number of *1s* is an odd number, 3, so the `P1` bit is set to *1* (this example is using even parity).

• `P2` has the second bit from the right set; the other bits in the number space that have the second from the right bit set are included in the parity calculation, as indicated with an *X* in the `P2` row of the table. The total number of *1s* is an even number, 4, so the `P2` bit is set to 0.

• `P4` has the third bit from the right set, so the other bits that have the third from the right bit set in their position numbers, as indicated with an *X* in the P3 row. There are an odd number of *1s* in the marked columns, so the `P4` parity bit is set to 1.

To determine if any information has changed, the receiver can check the parity bits in the same way the sender has calculated them; the total number of *1s* in any set should be an even number, including the parity bit. If one of the data bits has been flipped, the receiver should never find a single parity error, because each of the bit positions in the data is covered by multiple parity bits. To discover which data bit is incorrect, the receiver adds the positions of the parity bits that are in error; the result is the bit position that has been flipped. For instance, if the bit in position 9, which is the fifth data bit, is flipped, then parity bits `P1` and `P8` would be both in error. In this case, 8 + 1 = 9, so the bit in position 9 is in error and flipping it would correct the data. If a *single* parity bit is in error—for example, `P1` *or* `P8`—then it is that parity bit which has been flipped, and the data itself is correct.

While the Hamming code is ingenious, there are many bit flip patterns it cannot detect. A more modern code, such as `Reed-Solomon`, can detect and correct a wider range of error conditions while adding less additional information to the data stream.

**Note**

There are a large number of different kinds of CRC and error correction codes used throughout the communications world. CRC checks are classified by the number of bits used in the check (the number of bits of padding, or rather the length of the polynomial), and, in some cases, the specific application. For instance, the Universal Serial Bus uses a 5-bit CRC (`CRC-5-USB`); the Global System for Mobile Communications (GSM), a widely used cellular telephone standard, uses `CRC-3-GSM`; Code Division Multi-Access (CDMA), another widely used cellular telephone standard, uses `CRC-6-CDMA2000A`, `CRC-6-CDMA2000B`, and `CRC-30`; and some car area networks (CANs), used to tie together various components in a vehicle, use `CRC-17-CAN` and `CRC-21-CAN`. Some of these various CRC functions are not a single function, but rather a class, or family, of functions, with many different codes and options within them.

### Multiplexing

You walk into a room and shout, “Joe!” Your friend, Joe, turns around and begins a conversation on politics and religion (the two forbidden topics, of course, in any polite conversation). This ability to use a single medium (the air through which your voice travels) to address one person, even though many other people are using the same medium for other conversations at the same time, is what is called, in network engineering, multiplexing. More formally:

**Multiplexing is used to allow multiple entities attached to the network to communicate over a shared network.**

Why is the word *entities* used here instead of hosts? Returning to the “conversation with Joe” example, imagine the one way you can communicate with Joe is through his teenaged child, who only texts (never talks). In fact, Joe is part of a family of several hundred to several thousand people, and all the communications for this entire family must come through this one teenager, and each person in the family has multiple conversations running concurrently, sometimes on different topics with the same person. The poor teenager must text very quickly, and keep a lot of information in her head, like “Joe is having four conversations with Mary,” and must keep the information in each conversation completely separate from the other. This is closer to how network multiplexing really works; consider:

• There could be millions (or billions) of hosts connected to a single network, all sharing the same physical network to communicate with one another.

• Each of these hosts actually contains many applications, possibly several hundred, each of which can communicate with any of the hundreds of applications on any other host connected to the network.

• Each of these applications may, in fact, have several conversations to any other application running on any other host in the network.

If this is starting to sound complicated, that is because it is. The question this section needs to answer, then, is this:

**How do hosts multiplex effectively over a computer network?**

The following sections consider the most commonly used solutions in this space, as well as some interesting problems tied up in this basic problem, such as multicast and anycast.

#### Addressing Devices and Applications
