
When seeking to differentiate between these two components, security professionals should remember that identification identifies the person, whereas authentication verifies the authenticity of the user’s identity. Authentication is often accomplished by entering a user password at the time of login. The login method should validate the login when all of the input data has been submitted. The most prevalent types of user identification are user IDs or user accounts, account numbers, and **personal identity numbers** (**PINs**), as illustrated in *[Figure 16.1](#c16.xhtml#fig16_1)*:

![](images/Image29877.jpg)

**Figure 16.1:** Authentication

# Authentication factors

After the user identification mechanism has been developed, an organization must decide which authentication approach to employ. Authentication methods are divided into the following five categories:

* The knowledge of a person is employed as part of the authentication process.
* A person’s possession is an aspect of ownership authentication.
* **Authentication factor**: A characteristic that distinguishes a person.
* The location of a person is utilized as a part of the authentication process.
* An authentication factor is a person’s activity.

During authentication, a single-factor authentication ensures that a user provides at least one element from each of these categories. This may be shown by entering a username and password upon login. The user must provide two of the three factors when utilizing two-factor authentication. The two-factor authentication is shown by logging in using a username, password, and smart card. A user must provide three separate pieces of information when using three-factor authentication. Three-factor authentication entails using a username, password, smart card, and fingerprint to log in. For authentication to be considered strong, a user must provide components from at least two different categories. (It’s important to note that the username is only identification and not an authentication factor.)

It’s vital to note that a single-factor authentication is defined as the use of several authentication factors from the same category. When a user provides a login, password, and the user’s mother’s maiden name, single-factor authentication is used. In this situation, the user is still only providing information that a person is aware of.

## Knowledge-based factors

The knowledge factor is based on a person’s knowledge of a subject. For this sort of authentication, a Sort I authentication factor is employed. Additional knowledge factors such as date of birth, mother’s maiden name, key combination, or PIN may be used in addition to password authentication.

## Ownership affecting factors

As previously stated, ownership factor authentication is a kind of authentication that is based on a person’s possession of something. For this sort of authentication, a Form II authentication factor is employed. Some instances of ownership considerations are as follows:

* **Token devices**: A token device is a small device that transmits a one-time password to the authentication server. If the authentication method requires the use of a token device, the user must have the device on hand to authenticate. Despite sending a password to the authentication server, the token device is designated as a Type II authentication factor since its use necessitates device ownership. Due to the high cost of establishing a token device, it is often reserved for the most secure settings. Furthermore, owing to the battery life of the token device, challenges with token-based systems may arise.
* **Memory cards**: A valid user is given a memory card, which functions as a swipe card. The user’s authentication information is stored on the card. When the card is swiped through a card reader, the information captured on the card is compared to the information input by the user. If the information is valid, the authentication server accepts the login. If the two don’t match, authentication is denied. Because the card must be read by a card reader, each computer or access device must have its own card reader. In addition, the cards must be created and programmed. Both of these techniques add to the complexity and cost of the authentication process. The increased security it provides, however, is usually worth the added complexity and cost, which is a clear benefit of this method. The data on the memory cards, on the other hand, is not protected, which is a weakness that companies should be aware of before using this strategy. Memory cards are fairly easy to falsify.
* **Smart cards**: A smart card is similar to a memory card in that it accepts, stores, and transmits data, but it has a bigger storage capacity. Smart cards, also known as **integrated circuit cards** (**ICCs**), include embedded circuits similar to those used in bank or credit cards, as well as memory akin to memory cards. Smart cards are read using card readers. The authentication server, on the other hand, uses the data on a smart card without the requirement for user input. To protect against lost or stolen smart cards, most implementations require the user to input a secret PIN, meaning that the user is providing both Type I (PIN) and Type II (smart card) authentication factors.

## Characteristics to look for

As previously stated, characteristic factor authentication is authentication based on who a person is. For this sort of authentication, a Form III authentication factor is employed. Biometric technology is a kind of authentication that verifies a user’s identification by using physiological or behavioral factors. Physiological features include any unique physical property of the user, such as the iris, retina, and fingerprints. Behavioral factors that measure a person’s behaviors in a situation include voice patterns and data input characteristics.

## Concepts of authentication that aren’t authentic

The following are some more authentication concepts that all security experts should be aware of:

* **Time-Based One-Time Password Method** (**TOTP**): This is a password-generating technique that generates a password using a shared secret and the current time. It’s similar to HOTP, except that it utilizes an integer-based counter instead of the current time.
* **HMAC-Based One-Time Password Method** (**HOTP**): This method generates a password using a shared secret that is only used once. This is achieved by employing a synchronized incrementing counter on both the client and the server.
* **Single sign-on** (**SSO**): This functionality is accessible when an authentication system requires a user to authenticate just once in order to access all network resources.

## Management of accounts and identity

Identity and account management are required for every authentication system. As a security professional, you must ensure that your organization has a system in place to handle the creation and distribution of access credentials or identities. If invalid accounts are allowed to be created and not terminated, security breaches will occur. Most firms set up a system to verify the identification and authentication method to ensure that user accounts are current. The following are a few questions that may be useful in the process:

* Is there a current, up-to-date, and approved list of permitted users and their permissions?
* Do you change your passwords at least once every 90 days, or more often as needed?
* Is it true that inactive user accounts expire after a specific period of time?
