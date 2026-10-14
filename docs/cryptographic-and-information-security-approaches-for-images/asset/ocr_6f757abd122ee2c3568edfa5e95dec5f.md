For instance, we have 101 and 101 binary bits after applying XOR operations on each 4 bits. In first three bit binaries i.e., 101, first two bits 10 represents row and 1 represent column of the blocks. For example 101 represent 5 and in second block we mapped 101 to 9 respectively.

# 18.3.3.1 Embedding Bit into Cover Image

In this phase, we have inserted values obtained from each blocks by bit division into cover image. We convert values of blocks into four bits binaries and placed these four binaries in LSBs of cover image consecutively. First we take the pixels one by one from the cover media and then place 4 (Figures 18.17 through 18.19).

After getting the new pixel values, we form the stego image. The pixel values for red component 145, 211, 111, 249 are place into the position of the previous values. Similarly we performed these operations for green and blue component of cover image. The resultant stego image is given in Figure 18.20.

![](bbox=[0.15, 0.57, 0.85, 0.68])

Figure 18.17 Secret image in 3-D view of size 128 × 128.

![](bbox=[0.15, 0.78, 0.85, 0.88])

Figure 18.18 Cover image in 3-D view of size 256 × 256.