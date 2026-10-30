# Injection Attacks

When user input is used without input validation, this results in an opportunity for an attacker to craft input to create specific events to occur when the input is parsed and used by an application. SQL injection attacks involve the manipulation of input, resulting in a SQL statement that is different than intended by the designer. XML and LDAP injections are done in the same fashion. Because SQL, XML, and LDAP are used to store data, this can give an attacker access to data against business rules. Command injection attacks can occur when input is used in a fashion that allows command-line manipulation. This can give an attacker command-line access at the privilege level of the application.

# Header Manipulations

When HTTP is being dynamically generated through the use of user inputs, unvalidated inputs can give attackers an opportunity to change HTTP elements. When user-supplied information is used in a header, it is possible to create a variety of attacks, including cache poisoning, cross-site scripting, cross-user defacement, page hijacking, cookie manipulation, or open redirect.

![](bbox=[0.17, 0.429, 0.252, 0.477])

> **EXAM TIP** A wide variety of attack vectors can be used against a client machine, including cache poisoning, cross-site scripting, cross-user defacement, page hijacking, cookie manipulation, and open redirect. All attacks should be known for the exam.

# Arbitrary/Remote Code Execution

One of the risks involved in taking user input and using it to create a command to be executed on a system is arbitrary or remote code execution. This attack involves an attacker preparing an input statement that changes the form or function of a prepared statement. A form of command injection, this attack can allow a user to insert arbitrary code and then remotely execute it on a system. This is a form of an input validation failure, as users should not have the ability to change the way a program interacts with the host OS outside of a set of defined and approved methods.

# Chapter Review

In this chapter, you explored application and wireless attacks. The chapter opened with a discussion of wireless attacks, including rogue access points, jamming and interference, evil twin, Bluetooth attacks (bluejacking, bluesnarfing, and bluebugging), and war chalking and war driving. It then covered attacks against encryption, including IV attacks, WEP/WPA attacks, and WPS attacks. For the exam, you will be expected to be able to explain these types of attacks.

The second half of the chapter presented application attacks, beginning with cross-site scripting. Injection attacks followed, including SQL, LDAP, XML, and directory