ExamAlert

Although EAP-TLS is one of the most secure and most costly forms of EAP, EAP can be implemented in many different ways. Some methods include EAP-MD5, EAP-TLS, EAP-SIM, LEAP, and EAP-TTLS. Although EAP-MD5 is not appropriate for use by itself (because it is a simple hash), and LEAP is dictionary-crackable, the other EAP types are robust. You do not need to memorize the details of all the EAP types, but you do need to be able to select the appropriate protocol, depending on the policy established for authentication strength.

# Remote Authentication Dial-in User Service (RADIUS)

RADIUS was designed to support dialup users and originally used a modem pool to connect to an organization’s network. Because of the features RADIUS offers, it is now used for more than just dialup users. Enterasys uses it for secure network products, and 802.1X/EAP also uses it widely.

A RADIUS server contains usernames, passwords, and other information to validate the user (supplicant). A supplicant is a client machine that wants to gain access to the network. RADIUS is a well-known UDP-based authentication and accountability protocol. Information is passed to the NAS, which is the RADIUS client. The RADIUS client then forwards the information to the RADIUS server to be authenticated. Traffic from the RADIUS client to the RADIUS server typically protects the password by means of a shared secret.

RADIUS has improved with the IETF’s approval of Diameter, and it continues to be the most widely deployed AAA (authentication, authorization, and accountability) server protocol.