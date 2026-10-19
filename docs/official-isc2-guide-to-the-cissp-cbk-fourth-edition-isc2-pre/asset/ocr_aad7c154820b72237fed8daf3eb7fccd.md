credentials for the target network, enabling a number of attacks, mainly on behalf of the server operator but also for anyone able to break into a server.

# Internet Relay Chat (IRC)

Of the widely deployed chat systems on the Internet, IRC was arguably the first. IRC is still popular in academia but has lost its dominant position to commercial services; however, IRC channels and servers are still very much available and popular with people wishing to share information and files on an anonymous basis. IRC supported good anonymity because they typically operate through terminal or telnet connections, which leave no logs related to file transfers because the session is, in theory, just text on the screen.

| Ports | 194/TCP, 194/UDP |
| Definition | RFC 1459 |

Table 4.13 – IRC Quick Reference Communication is organized in public discussion groups (channels) and private messaging between individual users. 38

IRC is a client/server-based network. IRC is unencrypted and therefore an easy target for sniffing attacks. The basic architecture of IRC, founded on trust among servers, enables special forms of denial-of-service attacks. For instance, a malicious user can hijack a channel while a server or group of servers has been disconnected from the rest (net split).

IRC is also a common platform for social engineering attacks, aimed at inexperienced or technically unskilled users.

Although original clients were UNIX based, IRC clients are now available for many platforms, including Windows, Apple Macintosh, and Linux. The security professionals will want to familiarize themselves with proprietary applications such as IBM Lotus Instant Messaging and Web Conferencing (Sametime), as well as commercial services such as:

+   - AOL Instant Messaging and ICQ, based on the proprietary Open System for Communication in Real-Time (OSCAR) protocol
+   - Google Talk, based on open Jabber/XMPP
+   - Microsoft MSN Messenger/Windows Messenger, based on the proprietary Mobile Status Notification Protocol (MSNP)
+   - Yahoo! Messenger, based on a proprietary protocol