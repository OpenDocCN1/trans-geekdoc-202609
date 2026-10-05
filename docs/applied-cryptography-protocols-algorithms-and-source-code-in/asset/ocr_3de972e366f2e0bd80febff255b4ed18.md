# 13.2 Madryga 305

variable-length key would surely silence those who thought 56 bits was too low. They could implement this algorithm with any key length they desired. And, for anyone who has attempted to implement DES in software, an algorithm that took software implementations into account would be welcomed.

# Description of Madryga

An iteration of the inner cycle operates on a 3-byte window of data, called the working frame (see Figure 13.1). This window advances 1 byte for each iteration. The first 2 bytes of the working frame are together rotated a variable number of positions, while the last is XORed with some key bits. As the working frame advances, all bytes are successively rotated and XORed with key material. Successive rotations overlap the XOR and rotation, and data from the XOR is used to influence the rotation. This makes the entire process reversible.

Because every byte of data influences the 2 bytes to its left and the 1 byte to its right, after each passes every byte of the ciphertext is dependent on 16 bytes to the left and 8 bytes to the right.

When encrypting, each iteration of the inner cycle starts the working frame in the next-to-last byte of the plaintext and advances circularly through the third-to-last

| Text | 1 | 2 | 3 | 4 | 5 | 6 | ... | TL-2 | TL-1 | TL |
|---|---|---|---|---|---|---|---|---|---||
| Moving Working Frame | WF(1) | WF(2) | WF(3) | | | | | | |
| | 8 bits | 8 bits | 8 bits | | | | | | |
| | ROT | Rotate Target | | | | | | |
| Transposition | | 16 bits | Rotate Count | | | | |
| | | 3 bits | Translate Target | | | |
| Translation | | | 8 bits | | | | | |
| | | | XOR | KL | | | | |
| Key | 1 | 2 | 3 | ... | XOR | | | | |
| Key Hash | 1 | 2 | 3 | ... | KL | | | |

Figure 13.1 One iteration of Madryga.