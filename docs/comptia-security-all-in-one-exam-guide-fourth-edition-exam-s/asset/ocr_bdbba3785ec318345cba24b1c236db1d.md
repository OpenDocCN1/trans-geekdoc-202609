# Personal Identity Verification Card

The Personal Identity Verification (PIV) card is a smart card for U.S. federal employees and contractors. Similar to the DoD CAC, it contains the required information for the cardholder to access federal facilities and systems. Federal Information Processing Standard (FIPS) 201 documents the requirements for a common identification standard for all federal employees and contractors. This smart card includes a cryptographic chip and connector, as well as a contactless proximity card circuit. It also has standards for a printed photo and name on the front. Biometric data can be stored on the card, providing an additional authentication factor, and if the PIV standard is followed, several forms of identification are needed to be issued a card.

# Multifactor Authentication

*Multifactor authentication* (or multiple-factor authentication) is simply the combination of two or more types of authentication. Three broad categories of authentication can be used: what you are (for example, biometrics), what you have (for instance, tokens), and what you know (passwords and other information). Two-factor authentication combines any two of these before granting access. An example would be a card reader that then turns on a fingerprint scanner—if your fingerprint matches the one on file for the card, you are granted access. Three-factor authentication would combine all three types, such as a smart card reader that asks for a PIN before enabling a retina scanner. If all three correspond to a valid user in the computer database, access is granted.

![](bbox=[0.164, 0.516, 0.244, 0.567])

> **EXAM TIP** Two-factor authentication combines any two methods, matching items such as a token with a biometric. Three-factor authentication combines any three, such as a passcode, biometric, and a token.

Multifactor authentication methods greatly enhance security by making it very difficult for an attacker to obtain all the correct materials for authentication. They also protect against the risk of stolen tokens, as the attacker must have the correct biometric, password, or both. More important, multifactor authentication enhances the security of biometric systems by protecting against a stolen biometric. Changing the token makes the biometric useless unless the attacker can steal the new token. It also reduces false positives by trying to match the supplied biometric with the one that is associated with the supplied token. This prevents the computer from seeking a match using the entire database of biometrics. Using multiple factors is one of the best ways to ensure proper authentication and access control.

# HOTP

HMAC-based One-Time Password (HOTP) is an algorithm that can be used to authenticate a user in a system by using an authentication server. (HMAC stands for Hash-based Message Authentication Code.) It is defined in RFC 4226, dated December 2005.