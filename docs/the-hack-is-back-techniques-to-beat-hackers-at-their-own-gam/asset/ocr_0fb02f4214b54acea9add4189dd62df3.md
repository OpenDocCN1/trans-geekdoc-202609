![](bbox=[0.106, 0.087, 0.893, 0.283])

**FIGURE 6.1** Screenshot of Exploit-DB showing available exploits for various systems, note the different properties for each exploit.

The exploits provided can be in many different programming languages and cover a wide array of affected software and hardware assets. For the most part, the exploits are written in Python, however, many of the exploits are written in other scripting languages or source code for compiled executables. Other exploits are simply writeups of how to achieve an exploit in the system and do not provide a set of code on execution. These writeups can be as simple as the HTTP request that was used to exploit the system, but most are not a “one-click-autopwn” to run the exploit instantly.

Most of these exploits will require some type of manual change or input from the command line to be used to target the system we want to exploit; this is why creating a local copy of the exploit to modify is crucial. This is also why being able to review the code and understand what activity is occurring is imperative as well, that way we can use the exploit effectively and debug as necessary.

There are additional tools provided by Exploit-DB such as the **searchsploit** command, which is a command line tool that can be used to query the Exploit-DB from the command line. Beyond this, we can inspect the exploit code ourselves, and even request a mirrored copy of the exploit directly from our terminal for use. For example, to search for potential vulnerabilities in an identified wpDiscuz WordPress plugin, we can use the command below in **Figure 6.2**.

![](bbox=[0.107, 0.627, 0.893, 0.733])

**FIGURE 6.2** Using searchsploit to find known exploits for wpDiscuz.

This shows that there are three known exploits for an unauthenticated vulnerability that affects version 7.0.4 of wpDiscuz. Remote code execution is devastating to the overall confidentiality, integrity, and availability of systems, and when combined with an unauthenticated attack can spell major trouble. Let’s try to peek inside the exploit by using another searchsploit command, this time by referencing the “Path” given in a result. We will focus on the Python version of this exploit, which is labeled as **php/webapps/49967.py**. Running the command below will examine the exploit (think of the **-x** for examine) so we can take a peek at the exploit.

```
```bash
searchsploit -x php/webapps/49967.py
```
```