value of a resource increases, so should the strength of the access controls protecting it. Two-step authentication should be the minimum requirement for valuable resources. Attackers often use brute-force or dictionary attacks to crack passwords. These methods can easily crack weak passwords, such as those that are very short or contain dictionary words.

+   • A brute-force attack involves trying every possible combination of characters. Modern password crackers don't try every combination of letters, numbers, and special characters in alphabetic order. Rather, they first measure the entropy (a measure of randomness) of characters. Then they test low-entropy words first, medium-entropy words next, and then high-entropy words last.

> > TIP
> A shorter password life span means more protection for the user. To create stronger password controls for users, consider a 30-day password-change policy. A shorter password life span means a lower chance that an attacker can compromise and use the password before it expires.

+   • A dictionary attack works by hashing all the words in a dictionary (often supplemented with suffixes such as 01, 02, 4u, and so on) and then comparing the hashed value with the system password file to discover a match. Hackers are familiar with all the usual tricks, such as spelling a name backward or simple substitution of characters (such as 3 for e, 0 for o, $ for s, and so on).

+   • Because most systems store a hash of the password, attackers first precompute these dictionary words and build a table. Then they look up the stored hashed version of the password in the table to discover the word that generated it. These tables, known as rainbow tables, are widely available. For example, AccessData's forensic investigator's tool known as the Forensic Toolkit® (FTK®) features a rainbow table with a million words. According to FTK's website, the table detects 28 percent of user passwords.

**Password Account Policies:** In addition to encouraging password best practices, your account policy should include clear password requirements. Following is a list of suggested account policy password requirements. (You can, and should, change the specifics of these items for your organization.)

+   • Complexity

+   • Passwords must contain at least eight alphanumeric characters.

+   • Passwords must contain a combination of uppercase and lowercase letters and numbers.

+   • Passwords must contain at least one special character within the first seven characters of the password.

+   • Passwords must contain a nonnumeric letter or symbol in the first and last character positions.

+   • Passwords must not contain the username.

+   • Passwords must never include the name of the user or the names of any close friends or relatives.

+   • Passwords must never use an employee's ID number, Social Security number, birth date, telephone number, or any personal information that can be easily guessed.

+   • Passwords must never include common words from an English dictionary (or a dictionary of another language with which the user is familiar).