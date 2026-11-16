well take advantage of the work of others to get exploits so you can clearly demonstrate the vulnerability. That's one of the primary reasons for running the exploit, after all. You need to demonstrate that a vulnerability is exploitable for when you report to your customer/employer. Another reason to run the exploit is to gain an additional layer so you can pivot to other networks to look for more vulnerabilities.

Part of being an ethical hacker is making sure you have permission and are not doing any harm. However, the objective of any ethical hacker should be to improve security. This is an important point. Getting into a customer’s network to take down as many systems as you can just to have done it without any path for the customer to improve their security posture isn’t very ethical. Keep in mind that your goal is always to improve security and not just to see how much damage you can cause.

You may be wondering where you could possibly find a lot of exploits. One great resource is exploit-db.org. This is a site where researchers and developers post exploit code and proof of concept code that works against identified vulnerabilities. While often these exploits make their way into tools like Metasploit, they don’t always. This may especially be true if the exploit is just a proof of concept that’s not fully implemented and may not take the exploit to the end. If you take a look at Figure 7.1, you can see a list of the code for current exploits. What you see is just a list of remote exploits. In fairness, not all of these exploits in the way you may think about exploits, if you are thinking of exploits as something that gives you a shell. At the top of the list, for example, you will see a link to a Python script that enumerates usernames on an OpenSSH 7.7 installation.

# FIGURE 7.1 Remote Exploits list at exploit-db.org

| Date Added | D | A | V | Title | Platform | Author |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 2018-08-21 | - | - | - | OpenSSH 7.7 - Username Enumeration | Linux | Justin Gardner |
| 2018-08-20 | - | - | - | EasyLogin Pro 1.3.0 - 'Encryptor.php' Unserialiaze Remote Code Execution | PHP | mr_me |
| 2018-08-20 | - | - | - | SEIG Modbus 3.4 - Remote Code Execution | Windows_x86 | Alejandro... |
| 2018-08-20 | - | - | - | SEIG SCADA System 9 - Remote Code Execution | Windows_x86 | Alejandro... |
| 2018-08-17 | - | - | - | OpenSSH 2.3 < 7.7 - Username Enumeration (PoC) | Linux | Matthew Daley |
| 2018-08-14 | - | - | - | Cloudme 1.9 - Buffer Overflow (DEP) (Metasploit) | Windows_x86-64 | Raymond... |
| 2018-08-13 | - | - | - | Oracle Weblogic Server - Deserialization Remote Code Execution (Metasploit) | Windows | Metasploit |

What you see is just a single category of exploits. You’ll also see web application exploits, denial of service exploits, and local exploits, which include privilege escalation exploits. While the remote exploits may seem sexier—after all, who doesn’t love to pop a box?—there is so much more to exploiting systems than just getting in remotely. In fact, there are often far easier ways to infiltrate a network. At the time of this writing, there are over 39,000 exploits that have been archived at exploit-db.org.