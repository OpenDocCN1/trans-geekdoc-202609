# Introduction to Metasploit

# Chapter Objectives

After reading this chapter and completing the exercises, you will be able to do the following:

+   - Understand the fundamentals of Metasploit
+   - Execute basic Metasploit commands
+   - Perform scans with Metasploit
+   - Perform basic exploits with Metasploit

Metasploit may be the single most popular tool for both hackers and penetration testers. For that reason alone, you really cannot be a penetration tester without at least a working knowledge of Metasploit. Before diving in deeper, we need to cover a few items.

First, what exactly is Metasploit? Well, to put it simply, it is a framework for delivering exploits to the target. You can take a documented vulnerability, find an exploit designed for the vulnerability, then deliver it to the target machine. Sometimes this is done directly, sending it to the IP address and port. Sometimes, with some exploits, Metasploit works as a web server, and you send a link to the client. If the client clicks on the link, and their system is vulnerable to that attack, you are in. So, it is a very versatile tool. And, as you will see in this chapter, it is not hard to learn.

The second thing to know, however, is that Metasploit is just a tool. It is a good tool, but just a tool. Hacking (whatever the motivation or intent) is not about a particular tool. It is about exploring the target and learning about it. I mention this because I routinely encounter people who tout Metasploit as being the be-all and end-all of hacking. They would have you believe that if you simply have Metasploit at your disposal, the world is yours for the taking. Not only is that not true, it is so far from the truth as to be shocking. I wonder if such people have ever used Metasploit on a real system, or only in classroom labs. Because the truth is, if you do everything right, but the target machine is not vulnerable to that