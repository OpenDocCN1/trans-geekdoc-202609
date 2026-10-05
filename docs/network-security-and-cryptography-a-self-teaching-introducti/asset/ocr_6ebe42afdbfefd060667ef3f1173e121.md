304 • NETWORK SECURITY AND CRYPTOGRAPHY

#  7.5.4.1 Clogging Attack

An adversary may initiate many key-exchange requests, one after another, forcing the victim to perform costly computations. This may potentially clog the victim.

#  7.5.4.2 Man-in-the-Middle Attack on Diffie-Hellman Key-Exchange Algorithm

+   - This attack is based on the assumption that the adversary is capable of intercepting the communications.
- Suppose there are two Users "A" and "B" who want to exchange a Secret Key, and "C" is capable of intercepting the communications between "A" and "B". Here C is the man in the middle.
- Then the adversary can perform the "Man-in-the-Middle Attack" as follows:
    - User "A" computes $Y_A$ and sends it to $B$ with the aim of initiating Key-Exchange with $B$.
    - User "C" intercepts the value $Y_A$ and responds to $A$'s request masquerading as $B$, and exchanges a key $K_A$ with User "A". The user "A" wrongly considers that it has exchanged the key $K_A$ with User "B".
    - Also, Adversary "C" sends key-exchange request to User "B" masquerading as User "A".
    - User $B$ responds to the request as if it is responding to a valid request from User "A", and wrongly exchanges a key $K_B$ with "C".
    - At this stage, the Adversary "C" has exchanged key $K_A$ with User "A" and $K_B$ with User "B". The Users "A" and "B" wrongly assume that they have exchanged the keys with each other.
- Now, when User "A" sends a message $M$ encrypted with key $K_A$ to User "B", C can intercept it, decrypt the cipher-text using key $K_A$, modify the plaintext message from $M$ to $M'$, encrypt it using key $K_{B'}$, and send it to User "B" masquerading as User "A". The User "B" will wrongly believe that the message has been sent by User "A".