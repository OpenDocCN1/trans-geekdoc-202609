# 14 Hacking Multifactor Authentication

# Challenge-Response Authentication

In some operating systems or applications, if an attacker obtains the password hash, the hash can be used in some forms of authentication hacking. To prevent attackers from stealing or eavesdropping on the hash during a password authentication event, a challenge-response authentication set of steps may be used. When used, not even the password hash appears outside of the password storage database (although it can always be derived or verified). Instead, the client and server use the hash to create another intermediate representation, which can be used to verify the hash. Here is a simplified representation of the steps involved in a challenge-response authentication event when a client wants to authenticate to a server using password authentication:

+   1. The client attempts to authenticate to a server.
2. The client provides the server generates a random set of characters known as the challenge and sends it to the client.
3. The client uses their password hash to manipulate the challenge into another intermediate form and sends it back to the server.
4. The server takes the client's stored hash and performs the same calculation on the challenge to create what would be an identical response if authentication is to be successful.
5. The server compares the response sent back by the client to the response it generated using the client's stored hash. If they are identical, the client is successfully authenticated.

Challenge-response authentication is often used client-server authentication performed over a network. That way, if the attacker is eavesdropping, they will not get the password in plaintext or the password hash. However, if the attacker can get both the challenge and the response,