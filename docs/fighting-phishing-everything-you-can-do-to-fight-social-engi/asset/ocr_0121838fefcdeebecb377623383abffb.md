Internet. The most common places people see URLs are in emails and the address location of their Internet browser. URLs most often represent objects and locations on the World Wide Web (WWW) but can point to objects using other protocols (e.g., File Transfer Protocol (FTP), Telnet, and 3270 terminals). Figure 13-1 shows an example of a common URL with its components identified.

![](bbox=[0.152, 0.303, 0.799, 0.488])

# FIGURE 13-1 An example of a URL and its components.

# Protocol Moniker

The beginning of URLs may include a *moniker* representing the protocol used to retrieve the object pointed to by the URL. Most people are used to seeing https (hypertext transfer protocol secure) or http (hypertext transfer protocol), but it can contain many other text strings, recognized by the involved tool or operating system. The typical Microsoft Windows computer has dozens of predefined protocol monikers, including http, https, ftp, telnet, data, file, mailto, ssh, tel, and tn3270. Additional custom protocol monikers can be defined.

When a protocol moniker is indicated, it instructs the browser (or whatever involved tool) to use a particular protocol and “well-known” network TCP/UDP port number to connect to the object. For example, http uses port 80, https uses port 443,