# Figure 8-2 Stack Entry and Buffer Overflow

![](bbox=[0.11, 0.09, 0.7, 0.29])

attacker has skillfully overwritten the return address, the return address will point back to “data” in the buffer (5). If this data really is program code, this attack code will be executed instead of the legitimate program’s code.

# AN EXAMPLE: THE IIS IPP BUFFER OVERFLOW ATTACK

Microsoft’s web-server software is the Internet Information Server (IIS). IIS offers a number of services, including an Internet Printing Protocol (IPP) service. Although few users ever use this service, it was turned on by default in early versions of IIS.

Vulnerability reporters discovered that IPP was vulnerable to a buffer overflow attack. Not long after, an attacker created the jill.c program to exploit this vulnerability. This exploit was written in the C programming language.

At its heart, jill.c sends the following HTTP request message to IIS. HTTP requests begin with a line indicating what should be done—in this case, executing a printing request. The next line indicates the host to which the request should go. The host name is replaced with a 420-character string that causes a buffer overflow.

```
GET/NULL. printer HTTP/1.0
Host: 420-character input to launch command shell
```

The next line, shown below, is the response from the webserver. The attack code was executed when the request arrived and caused Windows to create a new command shell—what used to be called a DOS prompt. The attacker is now in a sensitive directory. In addition, the attacker has system privileges, which means that he or she can do anything that he or she wishes to do in this directory and most other directories.

```
C:\WINNT\system32\>
```

# Test Your Understanding

+   2. a. What is a buffer?
+      b. What is a buffer overflow attack?
+      c. What impacts can buffer overflows have?
+      d. In a stack overflow, what is overwritten by the overflow?
+      e. To where does the overwritten return address point?
+      f. In the IIS IPP buffer overflow attack, what buffer is overflowed?