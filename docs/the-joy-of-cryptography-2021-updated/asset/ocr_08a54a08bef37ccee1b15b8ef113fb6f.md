# Secrets & Kerckhoffs’ Principle

Something important is missing from this picture. If we want Bob to be able to decrypt c, but Eve to *not* be able to decrypt c, then Bob must have some information that Eve doesn’t have (do you see why?). Something has to be kept secret from Eve.

You might suggest to make the details of the Enc and Dec algorithms secret. This is how cryptography was done throughout most of the last 2000 years, but it has major drawbacks. If the attacker does eventually learn the details of Enc and Dec, then the only way to recover security is to *invent new algorithms*. If you have a system with many users, then the only way to prevent everyone from reading everyone else’s messages is to *invent new algorithms* for each pair of users. Inventing even one good encryption method is already hard enough!

The first person to articulate this problem was Auguste Kerckhoffs. In 1883 he formulated a set of cryptographic design principles. Item #2 on his list is now known as **Kerckhoffs’ principle**:

|
| - |
| **Kerckhoffs’ Principle:** |
| “Il faut qu’il n’exige pas le secret, et qu’il puisse sans inconvénient tomber entre les mains de l’ennemi.” |
| **Literal translation:** [The method] must not be required to be secret, and it must be able to fall into the enemy’s hands without causing inconvenience. |
| **Bottom line:** Design your system to be secure even if the attacker has complete knowledge of all its algorithms. |

If the algorithms themselves are not secret, then there must be some other secret information in the system. That information is called the **(secret) key**. The key is just an extra piece of information given to both the Enc and Dec algorithms. Another way to interpret Kerckhoffs’ principle is that *all of the security of the system should be concentrated in the secrecy of the key*, not the secrecy of the algorithms. If a secret key gets compromised, you only need to choose a new one, not reinvent an entirely new encryption algorithm. Multiple users can all safely use the same encryption algorithm but with independently chosen secret keys.

The process of choosing a secret key is called **key generation**, and we write KeyGen to refer to the (randomized) key generation algorithm. We call the collection of three algorithms (Enc, Dec, KeyGen) an **encryption scheme**. Remember that Kerckhoffs’ principle says that we should assume that an attacker knows the details of the KeyGen algorithm. But also remember that knowing the details (i.e., source code) of a randomized algorithm doesn’t mean you know the *specific output* it gave when the algorithm was executed.

![](bbox=[0.355, 0.8, 0.745, 0.865])