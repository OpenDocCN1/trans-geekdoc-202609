accounting. You should keep current the data used to identify subjects and monitor those data closely. You should disable the IDs of users who leave the organization or who are inactive for an extended time. You should apply standard naming conventions; these should not relate to job functions. The process for issuing IDs should be documented and secure.

# Processes and Requirements for Authentication

So far in this chapter, you have learned about methods to define authorization rules and identify users. The next step is authentication. In this part of access control, a user validates, or proves, the identity he or she provided during identification. **Authentication** answers the question, Are users who they say they are? Authentication proves that the subject requesting access is the same subject who has been granted access. Without authentication, you could never really know if users are who they say claim to be.

# Authentication Types

There are five types of authentication:

+   * **Knowledge**—Something you know, such as a password, passphrase, or personal identification number (PIN).

**WARNING**
A combination of username and password is considered single-factor authentication even though it requires two steps. This might or might not be adequate for access to more sensitive systems, applications, or data. In this case, you might be required to provide two-factor or multifactor authentication, in which you would swipe a card (something you have) to enter a building, then type a PIN (something you know) to ensure the security of a valuable resource.

+   * **Ownership**—Something you have, such as a smart card, key, badge, or token.

+   * **Characteristics**—Some attribute that is unique to you, such as your fingerprints, retina, or signature. Since the characteristics involved are often physical, this type of authentication is sometimes defined as something you are.

+   * **Location**—Somewhere you are, such as your physical location when you attempt to access a resource.

+   * **Action**—Something you do or how you do it, such as the way you type on a keyboard.

Each type of authentication can be easily compromised on its own. The use of controls from only one category is known as **single-factor authentication**. Systems containing sensitive or critical information should use at least two of these authentication types. The use of techniques from two or more of these categories is called **two-factor authentication** and provides a higher level of security than using only one.

# Authentication by Knowledge

Authentication by **knowledge** is based on something you know, such as a password, passphrase, or PIN. Static passwords are those that are seldom, if ever, changed. Passwords are the oldest and most common method of authentication for computer systems. They are also the weakest. You should not use passwords alone to protect valuable resources. As the