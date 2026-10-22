# 42.3.4 Software Keys.

Software keys of various kinds are used to secure data and equipment. A software key is generally a string of numbers that is used for identification purposes, either to allow access to the use of equipment or to permit authorized printing, processing, or copying of data. As described earlier in the discussion of dongles, most anticopying hardware devices are accompanied by software that works in tandem with the hardware. A software key activates or deactivates the hardware lock. When the software is working perfectly, there are generally no difficulties. However, all software can malfunction, and when that happens, there can be serious problems in getting equipment to work. Additional problems occur when the computer containing the software key malfunctions, and the software key cannot be made to work on a replacement machine.

# 42.3.4.1 Videocassettes versus Copy Machines.

Watermarking is one of the techniques being seriously considered for protecting videocassettes and DVDs. In 1995, the ASTC formed a Copyright Protection Technical Working Group, which spun off a special Watermarking and Embedded Data Encoding subgroup. The group has broad representation, including representatives from the PC market, the Macintosh market, the MPAA, the Consumer Electronics Manufacturers Association (CEMA) and related manufacturers, technicians, and users. Their task is to look for technologies and services that might use hidden data clues as a means of inhibiting or barring digital piracy. Using a hidden watermark that can be embedded in the content would then prevent machines from making copies or would alert the operator that the videocassette is marked and that unauthorized copies would be considered pirated.

# 42.3.4.2 DVD Area Encoding.

Digital video requires very large storage space—too large for a single CD to hold. However, by applying compression techniques, the digital video can be compressed to fit into the digital videodisc’s maximum capacity of 17 gigabytes. Two different types of compression are used for encoding audio and video content for DVD: constant bit rate (CBR) and variable bit rate (VBR) compression.

In order to prevent piracy of the content of the DVD, many companies are turning to encryption. The compressed data are encapsulated through a mathematical algorithm that can be decrypted only through the use of a decryption key.

# 42.3.4.3 Implementation.

For shorter programs, CBR is ideal. Based on MPEG-2 encoding, CBR compresses each frame of audio and video by a user-selected amount. This degree of compression is then applied to the entire program. Using VBR, it is possible to create a database of video content based on the amount of change in each frame or scene. This is particularly useful in programs with a long format. To construct the database, the encoding software does several analytical passes of the master footage and then makes a final digitizing pass. From the created database, the computer can encode the video with a variable data rate, allowing a higher bit rate for scenes with pans, zooms, and fast motion and giving scenes with little or no motion low data rates. By greatly compressing the areas of lower detail, areas of higher details can be allocated more space and use less compression.

# 42.3.4.4 Watermarks.

Watermarking involves embedding one set of data inside a larger set of data. The embedded set of data identifies the origins or ownership of a specific work, just as a watermark does on paper.