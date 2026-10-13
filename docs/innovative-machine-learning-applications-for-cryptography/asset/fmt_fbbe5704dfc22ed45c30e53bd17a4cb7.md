
Machine learning can be used to anticipate the input of data using encryption algorithms like `DES`. The first bit of encrypted data may be anticipated more accurately than 50% of the time using support vector machine learning, which is a better prediction than guesswork. Reverse engineering hash functions, which are thought to be irreversible one-way functions, can benefit from machine learning. This experiment has demonstrated that we can guess the inverse more accurately than 50% of the times, revealing that a machine learning method can reverse an encrypted message's first bit more efficiently than a guess. Although `DES` is a weak encryption method, this experiment has shown that it may be possible to try a more sophisticated method, like replacing `DES` with the stronger encryption standard `AES`. If we apply the same research methodology to a more complex function, like `AES256`, we can achieve better results than guessing the inverse with above 50% accuracy. This raises the question: How accurate could one forecast two pieces of encrypted data? Maybe even more? Alternatively, whether a machine learning algorithm can correctly predict a complete input. Or, to put it another way, how accurate could one be to forecast a single encrypted piece of data that has been encrypted using a more powerful symmetric encryption standard like `AES256` or elliptic curve encryption?

## REFERENCES

*   Anees, A. (2022). Machine Learning and Applied Cryptography, Security and Communication networks. Wiley.
*   Armstrong, K. (2021). Applying machine learning to predict symmetric encryption algorithm inputs [Master Thesis]. Channel Islands, California State University.
*   AWS Dashboard. (n.d.). <https://awsacademy.instructure.com/>
*   Brownlee. (2021). Ensemble Learning Algorithms With Python. Academic Press.
*   Cui, X., Zhang, H., Fang, X., Wang, Y., Wang, D., Fan, F., & Shu, L. (2023). A Secret Key Classification Framework of Symmetric Encryption Algorithm Based on Deep Transfer Learning. Applied Sciences (Basel, Switzerland), 13(21), 12025. doi:[10.3390/app132112025](https://doi.org/10.3390/app132112025)
*   Dataoverhaulers. (n.d.). <https://dataoverhaulers.com/can-encrypted-data-be-hacked/>
*   Digital Guardian. (n.d.). <https://digitalguardian.com/blog/what-data-encryption>
*   Exchange, S. (n.d.). Hash Function on Finite Fields. <https://math.stackexchange.com/questions/1347240/how-to-attack-universal-hash-functio>
*   Github Code Resource. (n.d.). <https://github.com/kongfy/DES/blob/master/Riv85.txt>
*   Hitaj, Gasti, Ateniese, & Perez-Cruz. (2019). PassGAN: A Deep Learning Approach for Password Guessing. Academic Press.
*   MahmoodyM.MoranT.VadhanS. (2012). Publicly Verifiable Proofs of Sequential Work. Proceedings of the 4th Conference on Innovations in Theoretical Computer Science.
*   NgA.NotesL. (n.d.). <https://see.stanford.edu/materials/aimlcs229/cs229-notes3.pdf>
*   Open.edu. (n.d.). <https://www.open.edu/openlearn/science-maths-technology/computing-and-ict/systems-co>
*   Ouladj, M., & Guilley, S. (2021). Side-Channel Analysis of Embedded Systems: An Efficient Algorithmic Approach. Springer. doi:[10.1007/978-3-030-77222-2](https://doi.org/10.1007/978-3-030-77222-2)
*   Robin David. (n.d.). GITHUB python DES. <https://github.com/RobinDavid/pydes/blob/master/LICENSE.md>
*   Sectigostore. (n.d.). <https://sectigostore.com/blog/5-differences-between-symmetric-vs-asymmetric-encrypt>
*   Speciner, M., Perlman, R., & Kaufman, C. (2002). Network Security: Private Communications in a Public World. Prentice Hall PTR.
*   Tutorialspoint. (n.d.). <https://www.tutorialspoint.com/difference-between-private-key-and-public-key>
*   VTSCADA. (n.d.). <https://www.vtscada.com/help/Content/Scripting/Tasks/proEncryptionAnddecryption.htm>
*   Wang, L., & Machines, S. V. (2005). Theory and Applications. Springer.
*   YouTube. (n.d.). <https://youtu.be/Sy0sXa73PZA>

# Chapter 10

*   **Neethu Krishna**
    *   [![Orcid Image](i/orcid.svg)https://orcid.org/0000-0002-6061-9193](https://orcid.org/0000-0002-6061-9193)
    *   SCMS School of Engineering and Technology, Karukutty, India
*   **Kommisetti Murthy Raju**
    *   [![Orcid Image](i/orcid.svg)https://orcid.org/0000-0002-7576-4449](https://orcid.org/0000-0002-7576-4449)
    *   Shri Vishnu Engineering College For Women, India
*   **V. Dankan Gowda**
    *   [![Orcid Image](i/orcid.svg)https://orcid.org/0000-0003-0724-0333](https://orcid.org/0000-0003-0724-0333)
    *   BMS Institute of Technology and Management, India
*   **G. Arun**
    *   Erode Sengunthar Engineering College, India
*   **Sampathirao Suneetha**
    *   [![Orcid Image](i/orcid.svg)https://orcid.org/0009-0005-2714-6442](https://orcid.org/0009-0005-2714-6442)
    *   Andhra University College of Engineering, Andhra University, India

## ABSTRACT

In cryptography, performing computations on encrypted material without first decrypting it has long been an aspiration. This is exactly what homomorphic encryption (`HE`) accomplishes. By allowing computation on encrypted data, the associated privacy and security of sensitive information are beyond imagination to date. This chapter delves into the vast and intricate realm of `HE`, its fundamental theories, and far-reaching implications for machine learning. As a result of the sensitive nature of the data on which machine learning is based, privacy and security issues often arise. In this vein, homomorphic encryption, which allows algorithms to learn from and predict encrypted data, emerges as a possible panacea. The authors thus set out in this chapter to prepare the ground for a deeper understanding of that synergy, showing how it is there but also what lies ahead.

## 1. INTRODUCTION TO HOMOMORPHIC ENCRYPTION

There exists a class of encryption, called **Homomorphic Encryption (`HE`)**, that objects can be computed on directly in ciphertext. After being decrypted the results are identical to what would have been obtained if they had instead applied these operations to plain text. Because of this special property, `HE` becomes an effective instrument for secure data processing—sensitive information is encrypted even during computation. The principle of homomorphic `HE` means that the structure exists before and remains unchanged after in between encryption and computation. For instance, if you have two numbers in the clear—2 and 3 say—and wish to add them in encrypted form, `HE` would permit you first to transform these into ciphertexts then proceed with performing an addition operation on their respective encryptions. Decrypting the result will reveal 5, which is indeed equal to a sum of these original numbers.

### Historical Context and Development

The concept of Homomorphic Encryption goes back to the conception of `RSA` (invented in 1978) as an algorithm with homomorphic properties. But this was only for specific operations. The breakthrough came in 2009, when Craig Gentry—a student at Stanford working on his Ph.D. thesis—developed a fully homomorphic encryption scheme for the first time ever. This was a turning point, because it proved that one could perform arbitrary computations on encrypted data.

Its initial proposal for construction was lattice-based cryptography (Suryawanshi and Abhay Chaturvedi, 2022). It proposed an encryption scheme that could evaluate the circuit of its own decryption function homomorphically. This first scheme, though revolutionary, was unpractical in being too slow and complex. But it laid the groundwork for later research in that field.
