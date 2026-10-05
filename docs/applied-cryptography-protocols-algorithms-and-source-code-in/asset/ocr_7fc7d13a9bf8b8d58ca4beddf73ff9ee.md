# CHAPTER 11

# # Mathematical Background

# ## 11.1 INFORMATION THEORY

Modern information theory was first published in 1948 by Claude Elmwood Shannon [1431,1432]. His papers have been reprinted by the IEEE Press [1433]. For a good mathematical treatment of the topic, consult [593]. In this section, I will just sketch some important ideas.

# ### Entropy and Uncertainty

Information theory defines the amount of information in a message as the minimum number of bits needed to encode all possible meanings of that message, assuming all meanings are equally likely. A database contains no more than 3 bits of information, the day-of-the-week field in a database can be encoded with 3 bits:

+   - 000 = Sunday
- 001 = Monday
- 010 = Tuesday
- 011 = Wednesday
- 100 = Thursday
- 101 = Friday
- 110 = Saturday
- 111 is unused

If this information were represented by corresponding ASCII character strings, it would take up more memory space but would not contain any information. Similarly, the "sex" field of a database contains only 1 bit of information, though it might be stored as one of two 6-byte ASCII strings: "MALE" or "FEMALE".

Formally, the amount of information in a message $M$ is measured by the entropy of a message, denoted by $H(M)$. The entropy of a message indicating sex is 1 bit; the entropy of a message indicating the day of the week is slightly less than 3 bits.