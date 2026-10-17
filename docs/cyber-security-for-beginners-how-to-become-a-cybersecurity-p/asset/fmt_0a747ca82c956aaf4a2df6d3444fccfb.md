
The 8-character password made up of only upper and lowercase letters would take only 9 minutes to crack. If we increase the number of characters in the password from 8 to 12, the total number of passwords using only upper and lowercase letters increases from 53 trillion to over 390 quintillions. A quintillion is a billion times a billion. The time it would take to crack a password consisting only of upper and lowercase letters is more impressive than the size of that number. It would take today's computers 123 years to crack that password. Including numbers and special characters increases the number of possible combinations to 26 sextillion, which is a quintillion time 1,000. And that password goes from taking 123 years to over 8500 years to crack. The length and complexity of the password aren't the only factors that contribute to its strength. Passwords should not contain any dictionary words, names, or important dates. Because password crackers are preloaded with dictionary words to try first, using a dictionary word can transform your 12-digit password from taking 8500 years to being cracked instantly.

Names and important dates also make it easier to guess passwords because they are easier to figure out. After all, they are important to you. Furthermore, add a special character at the end of your password by using the `$` sign instead of an `S`, a `3` instead of an `E`, a `@` instead of an `A`, and a `0` instead of an `O` or an exclamation mark do not provide additional security. While this may have worked in the past, password crackers now include libraries that include these letter replacements. To protect against weak passwords, include requirements that passwords expire after a certain period and that any previously used passwords be excluded.

# Chapter 3

# Hardcoded passwords

# ![Password Spraying is on the Rise and C-Suite Execs Are Being Targeted | Tech.co](image.006.jpeg)

Hardcoded passwords are another security risk associated with passwords. Passwords that are hardcoded are passwords that are embedded in various applications.

The password could be either an inbound or outbound variant. In the inbound variant, to gain administrative access to the program, the credentials that were provided are checked against a set of hardcoded credentials. When the application needs to connect to another device or service, the outbound variant is used. In the original application, the password for connecting to that device or service is hardcoded. The problem with either of these variants is that an attacker can easily obtain the password by examining the source code or binary export of the code. Once the attacker has obtained the password, they can access all programs that use the same password. If the software is installed on multiple devices, the attacker can compromise all of them with a single password. There are a few options for protecting against hardcoded passwords. One option is to keep passwords separate from the code in a configuration file that is strongly encrypted and protected. Rather than having a hardcoded default username and password, the program could simply prompt the user to create a password upon first login. If the software must contain hardcoded credentials, another mitigation is to use strong one-way hashes and store those hashes in the configuration file. The hash of the entered password would then be compared to the configured password by the program. This is advantageous because even if the attacker gains access to the configuration file, they will still have to try to crack the passwords, and if the passwords are strong, as discussed previously, it will take the attacker thousands of years to crack the password.

# Chapter 4

# No Encryption

# ![What is Encryption & How Does It Work? | by Privacy Guy | Privacy Guy | Medium](image.007.jpeg)

Encryption is essential in today's world for sensitive data. Encrypting the data ensures its confidentiality and integrity.

Encryption can be used for both data in transit and data at rest. When connecting to websites, for example, it is common to practice using `HTTPS`, which creates a tunnel using `TLS`. Because the communication is encrypted, anyone who can see the communication between the client and the server is unable to see the actual payload of the data. It is equally important to encrypt data at rest. Encrypting files and other sensitive data makes it much more difficult for an attacker to gain unauthorized access to information. Furthermore, it makes it much more difficult for an attacker to manipulate data. If the encryption is missing from the data, the data is exposed. For example, if a program saves a user's credentials to a `cookie` for faster login to a website, but that `cookie` does not encrypt the password, the credentials would be very easy to figure out if the system was ever compromised. As you can see, these are just a few examples of how not using encryption poses a serious security risk.

![Six Top Information Security Risks to Be Aware of in 2019 -- Security Today](image.008.jpeg)

# Chapter 5

# Path Traversal

# ![](image.009.png)

Path traversal is another type of security flaw. This vulnerability occurs when an application allows a malicious actor to navigate outside of the directory that the user is presented with.

For example, if the attacker was on a web page and wanted to try to browse around to find different files, they could use a path traversal attack to do so. When the attacker is on a legitimate web page, they can try to navigate to different files by typing `"../"` to navigate up a directory or an encoding that represents the by typing `".. / %2e %2e %2f"`. If the website is vulnerable to attack, the attacker could quickly figure out the directory structure with a few guesses, as well as by using the webserver returning errors about the file structure. Once the directory structure has been compromised, the attacker can browse various files such as the password file, system files, and other unauthorized data. To protect against path traversal attacks, websites should try to work without user input when using file system calls. Another prevention mechanism is to ensure that the user's input is validated by blacklisting all entries, except known good ones, such as special characters. Another good mitigation technique is for the administrator to use indexes rather than the actual names of the file locations. So, rather than having the user type in `Alaska` to navigate to the `Alaska` directory, have them use an `id` such as `20`.

![Comprehensive Guide on Path Traversal | LaptrinhX](image.010.png)

# Chapter 6

# SQL Injection

# ![What is SQL Injection Attack? Definition & FAQs | Avi Networks](image.011.png)

An SQL injection attack is another security flaw that can affect web applications. A SQL injection attack is one in which additional code is injected into the original `SQL` code.
