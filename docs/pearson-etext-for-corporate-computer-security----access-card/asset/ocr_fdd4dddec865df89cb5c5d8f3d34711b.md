+   **Stealing Password Databases**
+   - Difficult to steal a password database remotely
+   - Run on a downloaded password file
+   **Brute-Force Password Guessing**
+   - Try all possible passwords of length 1, length 2, etc.
+   - Thwarted by passwords that are long and complex (using all keyboard characters)
+   - *N* is the password length, in characters
+   - Alphabet, no case: 26^N possible passwords
+   - Alphabet, upper- and lowercase (52^N)
+   - Alphanumeric (letters and digits) (62^N)
+   - All keyboard characters (~80^N)
+   - With complexity, password length is very powerful (Figure 7-26)
+   **Dictionary Attacks**
+   - However, many people do not choose random passwords
+   - Dictionary attacks on common word passwords are almost instantaneous
+   - Names of people and pets
+   - Names of sports, teams, etc.
+   - Hybrid dictionary attacks on common word variants (e.g., Processing1)
+   - Rainbow tables use pre-computed tables of indexed password hashes
+   **Other Password Threats**
+   - Keystroke capture software
+   - Trojan horse displays a fake login screen and reports its finding to attackers
+   **Shoulder Surfing**
+   - Attacker watches as the victim types a password
+   - Even partial information can be useful
+   - Part of the password: P__sw__d
+   - Length of the password (reduces time to do brute-force cracking)

# Figure 7-25 Password Cracking (Study Figure)

> Passwords that use several types of keyboard characters are called complex passwords.

In addition to password complexity, **password length** is important to defend against brute-force attacks. Longer passwords require the cracking program to try more combinations to succeed. Figure 7-26 shows how password length is related to the number of possible passwords through which a password cracker has to search. Even in the simple situation of case-insensitive alphabetic passwords, the number of possibilities grows rapidly with password length.

For two-character passwords, 676 possibilities exist with lowercase-only passwords. Increasing password length to four characters increases the number of possibilities to more than 400,000. With six characters, more than 300 million possibilities exist. Given the speed of the computers that can be used in password cracking, however, passwords today must be at least 12 characters long, even if passwords vary by case and have digits and special characters.

> Increasing password length exponentially increases brute-force password cracking time.