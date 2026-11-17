
## Password Best Practices

One of the most visible security policies is the user account policy. This is a policy that each user must encounter. A good user account policy sets clear requirements for user accounts and passwords. You have already seen that an account policy should prohibit generic user accounts. Your account policy should also include password best practices:

- Create strong passwords—Your password must be complex enough to be unlikely to be compromised. It must meet minimum length requirements. You should never use a word that appears in the dictionary as your password. Passwords should not be based on personal information. Hackers have easy access to powerful password-cracking tools that use extensive word and name dictionaries. More secure passwords use words that don’t make any sense but that are easy to remember. For example, you might create a password using letters from the first words of a poem or song. Or you might substitute obscure characters, such as asterisks (*), dollar signs ($), “at” symbols (@), brackets ({}), mathematical symbols (+), and the like. These can be extremely difficult to guess or crack. Remember: Cracking tools check for simple tricks such as words spelled backward or simple substitutions for certain characters (for example, where mouse becomes m0us3).
- Don’t store a written copy of the password unless absolutely necessary—If you must store a written copy, keep it in a secure place. Alternatively, write down a hint for your password instead of the actual password. Destroy any written copies when they are no longer needed.
- Never share your passwords with anyone—Even if it is someone you trust, your password should be kept private.
- Use different passwords for different important user accounts—Using a single password for all your accounts is like using a single key for your car, your house, your mailbox, and your safety deposit box. If you lose the key, an attacker has access to everything. When you use different passwords for different systems, if one of your passwords is stolen, only that one system is compromised. This strategy prevents intruders from gaining access to accounts and data on other systems. Also, avoid using passwords that are similar to one another—for example, passwords that use the names of your children. If you use the same or similar passwords for more than one system, it makes it easier for an intruder who obtains one of your passwords to figure out the rest.
- If you think a password is compromised, change it immediately—Also, the first time you use them, change passwords that are assigned to you. Ideally, you should change passwords at least once every 30 days.
- Be careful when saving passwords on computers—Some dialog boxes (such as those for remote access and other telephone connections) present options to save or remember passwords. Selecting these options poses a potential security threat because the password is automatically listed when someone opens the dialog box.

- Passwords must never employ commonly used proper names, including the name of any fictional character or place.
- Passwords must never contain any simple pattern of letters or numbers, such as qwertyxx.
- Expiration. Passwords expire every 30 days and must be changed.
- Recovery. Forgotten passwords can be recovered after providing alternate authentication credentials via the organization’s internal password recovery utility.

- Disablement. User accounts will be disabled immediately when a user no longer is associated with the organization or no longer requires provided access.
- History. Password history is stored, and you cannot change your password to any of the 10 previous passwords you used.

### Passphrase Usage

A passphrase is a bit different from a password. It is longer and generally harder to guess, so it’s considered more secure. Because it usually contains more than one word, a passphrase is more secure against dictionary attacks. Most often, passphrases are used for public and private key authentication. The user uses a passphrase that is known only to the user, and the user uses that passphrase to unlock a private key that gives the user access to information. In most cases, the user converts the passphrase to a password. However, a system can be programmed to automatically convert the passphrase to a password according to an algorithm. A passphrase is stronger than a password, but the downside is that it takes a bit longer to type. Although passphrases are static, they aren’t as susceptible to brute-force attacks as passwords.

> **NOTE** It’s okay to reuse a password for resources that aren’t considered critical—for example, to access articles on an online news site. Just don’t use that same password for any logons for critical resources.

### Account Lockout Policies

Many systems are configured to disable a user ID after a certain number of consecutive failed logon attempts. In many cases, user accounts are disabled after three to five attempts. The number of failed logon attempts that trigger an account action is called the **threshold**. The user may be locked out for a few minutes, a few hours, or until the account is reset by a security administrator. This practice helps guard against attacks in which attackers make many attempts to guess a password. It also enables an intruder to lock out users, however—a form of denial of service (DoS) attack—by entering groups of incorrect passwords.

> **FYI** Unless your organization uses an automated password-reset process, your help-desk personnel will likely find that password-reset requests are the most common type of request they receive. When help-desk personnel receive such requests, they should require the user to provide information that verifies his or her identity. For example, the user should provide proof in the form of a driver’s license or employee ID. If the request is not made in person, help-desk personnel should use a form of questioning that verifies the user’s identity—for example, “What is your mother’s maiden name?” A lack of strong identity validation can allow an attacker to request a password change for any user’s account and access the account at will.
>
> Although auditing logon events can be helpful for your intrusion detection efforts, be careful. Failure auditing can also expose your systems to a DoS attack. A DoS attack occurs in one of two ways:
> - Attackers fill the security log, possibly causing a system crash or preventing other users from logging on.
> - Attackers cause events to be overwritten. They do this by continuously attempting to log on to your network with incorrect usernames or passwords. Purposely overwriting audit events can effectively erase evidence of attack activity.

Be cautious when you're defining an account-lockout policy. A restrictive policy increases the probability of preventing an attack on your organization. But with a stringent account-lockout policy, you can also unintentionally lock out authorized users, which can be frustrating and costly. When you apply an account-lockout policy, set the threshold to a high enough number that authorized users aren't locked out due to mistyped passwords.

### Audit Logon Events

You will learn more about auditing later in the chapter, but it is worth mentioning here as well. One method of keeping track of who is accessing your computing environment is to audit logon events. This practice provides you with a record of when every user logs on or off a computer. If an unauthorized user steals a user's password and logs on to a computer, you can determine when that security breach occurred. When you audit failure events in the logon event category (also known as failure auditing), you can see whether the failure event was due to unauthorized users or attackers attempting to log on to a computer or system. This is an example of intrusion detection.

## Authentication by Ownership

Authentication by **ownership** is the second type of verification. This is based on something you have, such as a smart card, a key, a badge, or a token. Tokens can be synchronous or asynchronous.

### Synchronous Tokens

A synchronous token uses an algorithm that calculates a number at both the authentication server and the device. It displays the number on the device's screen. The user enters this number as a logon authenticator, just as he or she would use a password.

In a **time-based synchronization system**, the current time is used as the input value. The token generates a new dynamic password (usually every minute) that is displayed in the window of the token. To gain access, the password is entered with the user's PIN at the workstation. No token keyboard is required. This system requires that the clock in the token remains in sync with the clock in the authentication server. If the clocks drift out of sync, the server can search three or four minutes on each side of the time to detect an offset. If the difference becomes too great, you must resynchronize the clocks.

> **NOTE**
> Synchronous tokens can be used in proximity devices that cause both the PIN and the password to be entered automatically.

An **event-based synchronization system** avoids the time-synchronization problem by increasing the value of a counter with each use. The counter is the input value. The user presses a button to generate a one-time password, and then enters this password with his or her PIN at the workstation to gain access. One common problem with event-based synchronization systems occurs when a user creates a password using the token but doesn't use the password to log on, and the counter in the server and the counter in the token become out of sync.

**Continuous authentication** is used by systems that continuously validate the user's identity. This is often done with proximity cards or other devices that continuously communicate with the access control system. If the user walks away from the desktop and steps outside the range of the access control detector, the system locks the desktop.

### Asynchronous Tokens

The asynchronous token is the second of two types of token-based devices. It looks like a credit card-sized calculator. The authentication server issues a challenge
