![](bbox=[0.179, 0.087, 0.822, 0.411])

**FIGURE 6.18**  Some additional commands to be used with Meterpreter.

Some common uses within Meterpreter are to move around within the file system on the remote host using the same Linux commands as any other system. These are commands such as **pwd**, **ls**, and **cat** which allow us to view files within the system. As any good hacker should do, we should be searching for sensitive information such as passwords, hashes, or API keys we can use for further exploitation.

We can always drop directly into a system shell on the exploited host by using the **shell** command. This opens what is known as a **channel** on the host and allows us to use a command shell of the host itself instead of negotiating through the Meterpreter. After entering the **shell** command, a new process and channel are created which allows us to run our system commands. Once we no longer wish to be in the command channel, we can either exit the channel with the **exit** command or background it with the **CTRL+Z** key, represented as ^Z on the screen. Backgrounding allows us to return to Meterpreter while keeping that channel alive, in case we would like to return to it again.

```
```text
meterpreter > shell
Process 47514 created.
Channel 0 created.
whoami
www-data
pwd
/var/www/html/churchinfo/tmp_attach
^Z
Background channel 0? [y/N] y
meterpreter >
```
```

**FIGURE 6.19**  Entering a shell channel, running the whoami and pwd commands, then backgrounding with the CTRL+Z keys.