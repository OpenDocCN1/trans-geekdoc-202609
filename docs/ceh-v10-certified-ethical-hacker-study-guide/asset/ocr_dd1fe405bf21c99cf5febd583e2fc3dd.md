# # Diffie-Hellman

As you might expect, key management is essential when it comes to cryptography. The keys are known in advance. They are sometimes called pre-shared keys because they have been shared in advance of their need. If the keys are not shared ahead of time, there needs to be a way for two parties in an encrypted communication to share keys without anyone being able to intercept them. Once a key is known, it’s like the messages weren’t encrypted to begin with. Ideally, the keys aren’t exchanged at all. When keys are exchanged, there is the possibility they will become known. A better approach would be for both sides to derive the keys. This means the key is never exchanged.

Whitfield Diffie and Martin Hellman came up with an approach that would allow two endpoints to generate a key without ever transmitting any data that would allow the key to be known. While the details of it involve a lot of math that we won’t go into here, it’s easy enough in the abstract to understand. Figure 13.3 shows how keys are generated with Diffie-Hellman, using paints to demonstrate how the process works.

# FIGURE 13.3 Diffie-Hellman process

![](bbox=[0.265, 0.415, 0.73, 0.955])