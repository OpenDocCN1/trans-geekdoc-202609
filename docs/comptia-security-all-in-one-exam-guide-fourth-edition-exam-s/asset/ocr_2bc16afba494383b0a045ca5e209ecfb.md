# Transitive Access

*Transitive access* is a means of attacking a system by violating the trust relationship between machines. A simple example is when servers are well protected and clients are not, and the servers trust the clients. In this case, attacking a client can provide transitive access to the servers.

![](bbox=[0.15, 0.23, 0.25, 0.29])

**EXAM TIP** Understanding how hijacking attacks are performed through poisoning the addressing mechanisms is important for the exam.

# Client-side Attacks

The web browser has become the major application for users to engage resources across the Web. The popularity and the utility of this interface have made it a prime target for attackers to gain access and control over a system. A wide variety of attacks can occur via a browser, typically resulting from a failure to properly validate input before use. Unvalidated input can result in a series of injection attacks, header manipulation, and other forms of attack.

# Injection Attacks

When user input is used without input validation, this results in an opportunity for an attacker to craft input to create specific events to occur when the input is parsed and used by an application. *SQL injection attacks* involve the manipulation of input, resulting in a SQL statement that is different than intended by the designer. XML and LDAP injections are done in the same fashion. As SQL, XML, and LDAP are used to store data, this can give an attacker access to data against business rules. Command injection attacks can occur when input is used in a fashion that allows command-line manipulation. This can give an attacker command-line access at the privilege level of the application.

# Header Manipulations

When HTTP is being dynamically generated through the use of user inputs, unvalidated inputs can give attackers an opportunity to change HTTP elements. When user-supplied information is used in a header, it is possible to create a variety of attacks, including cache-poisoning, cross-site scripting, cross-user defacement, page hijacking, cookie manipulation, or open redirect.

# Password Attacks

The most common form of authentication is the user ID and password combination. While it is not inherently a poor mechanism for authentication, the combination can be attacked in several ways. All too often, these attacks yield favorable results for the attacker, not as a result of a weakness in the scheme, but usually due to the user not following good password procedures.

# Poor Password Choices

The least technical of the various password-attack techniques consists of the attacker simply attempting to guess the password of an authorized user of the system or net-