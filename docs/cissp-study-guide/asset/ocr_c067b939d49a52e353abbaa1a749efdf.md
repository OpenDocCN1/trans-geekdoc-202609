# PAP and CHAP

PAP (Password Authentication Protocol) is a very weak authentication protocol. It sends the username and password in cleartext. An attacker who is able to sniff the authentication process can launch a simple replay attack, byplaying the username and password, using them to log in. PAP is insecure and should not be used.

CHAP (Challenge-Handshake Authentication Protocol) is a more secure authentication protocol that does not expose the cleartext password and is not susceptible to replay attacks. CHAP relies on a shared secret: the password is securely created (as during account enrollment) and stored on the CHAP server. Since both the user and the CHAP share a secret (the plaintext password), they can use that secret to securely communicate.

To authenticate, the client first creates an initial (unauthenticated) connection via LCP (Link Control Protocol). The server then begins the three-way CHAP authentication process:

+   - Server sends a challenge, which is a small random string (also called a nonce).
- The user takes the challenge string and the password, uses a hash cipher as MD5 to create a hash value, and sends that value back to the CHAP server as the response.
- The CHAP server hashes the password and challenge, creating the expected response. It compares the expected response with the response received from the user.

If the responses are identical, the user must have entered the appropriate password, and is authenticated. If they are different, the user entered the wrong password, and access is denied.

The CHAP server may re-authenticate by sending a new (and different) challenge. The challenges must be different each time; otherwise, an attacker could authenticate by replaying an older encrypted response.

A drawback of CHAP is that the server stores plaintext passwords of all client. An attacker who compromises a CHAP server may be able to steal the passwords stored on it.

# 802.1X and EAP

802.1X is "Port Based Network Access Control," and includes EAP (Extensible Authentication Protocol). EAP is an authentication framework that describes many specific authentication protocols. EAP is designed to provide authentication at Layer 2 (it is "port based", like ports on a switch), before a node receives an IP address. It is available for both wired and wireless, but is more commonly deployed on WLANs.

The 802.1X roles are:

+   - Supplicant: An 802.1X client
- Authentication Server (AS): a server that authenticates a supplicant
- Authenticator: a device such as an access point that allows a supplicant to authenticate and connect