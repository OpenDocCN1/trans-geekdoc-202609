# Chapter 1 = Getting Started

| keyword Research Tools |
| Search Engines |
| General Search |
| National Search Engines |
| Privacy-oriented search engines |
| Metadata Search Engines |
| FTP Search Engines |
| Files Search Engines |
| Images Search Engines |
| Video Search Engines |
| Custom Search Engines |
| Internet Of Things (IoT) Search Engines |
| Exploits/Newspaper Search |
| Fake News Detection |
| Specialized Search Engines |
| Niche Search Engines |
| Patent Search Engines |

Figure 1.2

# Termbin

I love Termbin (www.termbin.com).
Have you ever been in a situation where you are working in Linux and need to send yourself some text but cannot directly transfer the data out of the machine?
Rsync may not be an option if you are connected through one or more levels of jump servers. Setting up a web server would mean punching a hole through the firewall, which is probably a bad thing, so what do you do if you need to send yourself text from one of these servers?\In this case, Termbin is for you!
Send the contents of the file to termbin.com using netcat, and receive a private link where you can download your text.
For example, let's send a file called surprise.txt to Termbin using the following command:

```
root@osint ~ cat surprise.txt | nc termbin.com 9999
```

You will get back a custom URL that looks like this: https://termbin.com/cpc4.