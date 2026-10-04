# Table 16-6 Strong Passwords

| Strong Password | Why It Is Strong |
|---|---|
| b67n42d39c | Combines alphanumeric characters |
| 12^h u4@1p7 | Combines alphanumeric characters and symbols and includes a space |

On Cisco routers, leading spaces are ignored in passwords, but spaces after the first character are not. Therefore, one method to create a strong password is to use spaces in a phrase consisting of many words. This is called a passphrase. A passphrase is often easier to remember than a simple password. It is also longer and harder to guess.

# Additional Password Security (16.4.3)

Strong passwords are useful only if they are secret. Several steps can help ensure that passwords remain secret on a Cisco router and switch, including these:

+   - Encrypt all plaintext passwords.
- Set a minimum acceptable password length.
- Deter brute-force password guessing attacks.
- Disable an inactive privileged EXEC mode access after a specified amount of time.

As shown in the sample configuration in Example 16-2, the service password-encryption global configuration command prevents unauthorized individuals from viewing plaintext passwords in the configuration file. This command encrypts all plaintext passwords. Notice in the example that the password cisco has been encrypted as 03095A0F034F. (Keep in mind that cisco would not be a secure password; it is used here for illustration only.)

To ensure that all configured passwords are a minimum of a specified length, use the security passwords min-length length command in global configuration mode. In Example 16-2, any new password configured would need to have a minimum length of eight characters.

Threat actors may use password cracking software to conduct a brute-force attack on a network device. Such an attack repeatedly attempts to guess the valid passwords until one works. Use the login block-for number-of attempts attempts within seconds global configuration command to deter this type of attack. In Example 16-2, the login block-for 120 attempts 3 within 60 command blocks vty login attempts for 120 seconds if there are three failed login attempts within 60 seconds.