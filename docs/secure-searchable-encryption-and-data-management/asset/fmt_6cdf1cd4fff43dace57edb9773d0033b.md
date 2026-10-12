
# 21. M. H. Ameri, M. Delavar, J. Mohajeri, and M. Salmasizadeh, “A key-policy attribute-based temporary keyword search scheme for secure cloud storage,” IEEE Trans. Cloud Comput., vol. 8, no. 3, pp. 660–671, 2020, [https://doi.org/10.1109/TCC.2018.2825983](https://doi.org/10.1109/TCC.2018.2825983).

# 22. M. Backes, D. Fiore, and R. M. Reischuk, “Verifiable delegation of computation on outsourced data,” in *Proceedings of the 2013 ACM SIGSAC Conference on Computer & Communications Security*, 2013, pp. 863–874.

# 23. D. Boneh, and X. Boyen, “Efficient selective-ID secure identity-based encryption without random oracles,” in *International Conference on the Theory and Applications of Cryptographic Techniques*, 2004, pp. 223–238.

# 24. D. Boneh, X. Boyen, and E.-J. Goh, “Hierarchical identity based encryption with constant size ciphertext,” in *Annual International Conference on the Theory and Applications of Cryptographic Techniques*, 2005, pp. 440–456.

# 25. C. Delerablée, and D. Pointcheval, “Dynamic threshold public-key encryption,” in *Annual International Cryptology Conference*, 2008, pp. 317–334.

# 26. C. Gentry, “Practical identity-based encryption without random oracles,” in *Annual International Conference on the Theory and Applications of Cryptographic Techniques*, 2006, pp. 445–464.

# Chapter 5

# Searchable encryption in a public-key setting

SEARCHABLE ENCRYPTION IN A PUBLIC-KEY SETTING provides flexibility as there is no need of complicated secret key-sharing processes among the users as compared to the symmetric-key setting, which makes it suitable for the multi-user shared cloud storage environment. Cloud storage is becoming very popular among organizations because of features like optimized storage cost, ease of data management, and anytime anywhere access capabilities, and slowly cloud storage is becoming a necessity. However, organizations feel somewhat reluctant to adopt this platform because of security concerns. The data stored at the third-party cloud server may not be safe if it is stored as it is in plaintext form. To resolve the trust issues, it is suggested to store the data in encrypted form. This solves the problem; however, the selective access of the data becomes infeasible. One trivial solution is to first download all the data and decrypt it locally, but in that case, why would someone use cloud storage, if everything has to be done manually? The user must be able to retrieve only the desired data from the encrypted data stored at the cloud server. The first requirement to retrieve the desired data is the ability to perform a search over the encrypted data. A searchable encryption technique plays a critical role in this scenario. As we know, searchable encryption can be developed using either the symmetric-key or the public-key setting. Using a symmetric-key setting to create the searchable encryption scheme for the shared cloud storage environment may cause a lot of complexity in terms of sharing the secret key among the cloud users. As the number of users increases, the internal secret key distribution process also becomes difficult. Therefore, the public-key setting is preferred. In this chapter, we will discuss all aspects of the searchable encryption scheme in a public-key setting.

## 5.1 SYSTEM DEFINITION AND SYSTEM MODEL

In this section, we will formally define searchable encryption by introducing the different algorithms involved in a searchable encryption scheme and also provide the correctness condition for the searchable encryption schemes using the probabilistic definitions given in Chapter 4. Further, we will discuss the architecture of a searchable encryption system and explain the role of each entity involved in the system.

### 5.1.1 System definition

Like any encryption scheme, the searchable encryption scheme also consists of the four basic algorithms: key generation, index generation, trapdoor generation, and search. These algorithms are derived from the algorithms in an encryption scheme, and we will discuss the similarity and relationship between each algorithm here and the algorithms in any standard public-key encryption (PKE) scheme.

*   `[K_pub, K_pri] ← GenKey(1^n)`: The key-generation algorithm here and in any standard PKE scheme are the same. This algorithm also takes the security parameter (unary format) and outputs the public and private key pairs, like any PKE scheme.
*   `C_j ← GenIndex(K_pub, w_j)`: The index-generation algorithm is the same as the encryption algorithm in any PKE scheme. It also takes the public key and encrypts the keywords associated with the data file using this public key. Usually, in a PKE scheme, we encrypt a message with the public key, here the message is equivalent to the keyword. The collection of ciphertext of the keyword is sometimes called the encrypted index because, by default, the direct or the inverted index approach is implemented by the cloud server to store the encrypted data files and their associated encrypted keywords. Thus, in the context of searchable encryption this algorithm is called the index-generation algorithm; otherwise, it is merely an encryption algorithm.
*   `T_i ← GenTrap(K_pri, w_i)`: The trapdoor-generation algorithm is similar to the decryption algorithm in a PKE scheme in terms of one input, i.e., the private key of the user. But instead of taking the ciphertext at this step, a searchable encryption scheme conserves it for the search step. Typically, the secret key is used for decryption, but here we want to delegate our search capability to the cloud server using this secret key but without disclosing it. Here, for each keyword we want to search, we generate a kind of secret key for that keyword, and in the cryptographic community, it is called the search trapdoor or sometimes the search token. The search trapdoor, just like a usual computer trapdoor, facilitates the cloud server performing a search over the encrypted data.
*   `0/1 ← Search(T_i, C_j)`: The search algorithm is a new algorithm concerning PKE schemes. This algorithm uses the trapdoor of the keyword and searches each ciphertext for that keyword. If a match is found it returns 1, otherwise it returns 0. Sometimes it is explicitly shown in a scheme that it returns a reference of the data file associated with that keyword; otherwise, it is implicitly assumed that the associated data files will be provided to the user who generated the trapdoor.

```
Pr[[K_pub, K_pri] ← GenKey[1^n]; C ← GenIndex[K_pub, w]; T ← GenTrap[K_pri, w]: 1 ← Search[T, C]] = 1
```

(5.1)

Equation 5.1 states that we conduct an experiment where we have generated a public-private key pair, and using the public key, we have appropriately encrypted a keyword to get its ciphertext, and using the corresponding private key, we generated the trapdoor for the same keyword. After that, we provided both the ciphertext and search trapdoor to the search algorithm. If the search algorithm returns binary value 1 with probability one, then we say our scheme is always correct.
