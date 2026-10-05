# CHAPTER 12 Data Encryption Standard (DES)

![](bbox=[0.169, 0.115, 0.831, 0.493])

Figure 12.2 One round of DES.

# ### The Key Transformation

Initially, the 64-bit DES key is reduced to a 56-bit key by ignoring every eighth bit. This is described in Table 12.2. These bits can be used as a parity check to ensure the key is error-free. After the 56-bit key is extracted, a 48-bit **subkey** is generated for each of the 16 rounds of DES. These subkeys, $K_i$, are determined in the following manner.

First, the 56-bit key is divided into two 28-bit halves. Then, the halves are circularly shifted by either one or two bits, depending on the round. This shift is given in Table 12.3.

# ### Table 12.1
Initial Permutation

58. 50. 42. 34. 26. 18. 10. 2. 60. 52. 44. 36. 28. 20. 12. 4.
62. 54. 46. 38. 30. 22. 14. 6. 56. 48. 40. 32. 24. 16. 8.
57. 49. 41. 33. 25. 17. 9. 1. 59. 51. 43. 35. 27. 19. 11. 3.
61. 53. 45. 37. 29. 21. 13. 5. 63. 55. 47. 39. 31. 23. 15. 7.