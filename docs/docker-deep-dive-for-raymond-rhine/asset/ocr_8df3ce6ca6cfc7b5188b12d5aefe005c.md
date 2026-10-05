Try running the **ping, nslookup, and vim** commands that failed in the previous section. If you get stuck in the **vim** session, just type **:q** and press **Enter**.

```
docker > ping nigerpoulton.com
PING nigerpoulton.com (192.124.249.126) 56(84) bytes of data.
64 bytes from cloudproxy10126.sucuri.net (192.124.249.126): icmp
64 bytes from cloudproxy10126.sucuri.net (192.124.249.126): icmp~
^C
docker > nslookup nigerpoulton.com
zsh: command not found: nslookup
docker > vim
VIM - Vi IMImproved
~ version 9.0.1441
~ by Bram Moolenaar et al.
~ Vim is open source and freely distributable
<Snip>
:q
```

The **ping** and **vim** commands worked, but the **nslookup** still failed. This is because the default Docker Debug toolbox includes **ping** and **vim** but doesn't include **nslookup**. Don't worry, though. You can use Docker Debug's built-in **install** command to add any package listed on **search.nixos.org.

Run the following command to install the **bind** package (which includes the **nslookup** tool), and then run the