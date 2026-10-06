Logging Enhancements IIS 8.5 has more logging options. You now have the ability to perform logging of fields within the Request Header, Response Header, and/or Server variables. You have a slew of fields to choose from, or you can create a custom field.

ETW Events IIS 8.5 has event tracing built-in. You can still use the standard logs, use Event Tracing for Windows (ETW), or others.

# # Installing IIS 8

Now that we have examined the new features of IIS, we'll take a deeper look at installing it. Windows Server 2012 comes in several editions and has new methods of employing roles for the server. By getting into a detailed analysis of these editions in this chapter, keep in mind IIS 8.0 is available on all full Windows Server 2012 editions as well as Windows 8.

Although some IIS 8 servers may be internally deployed as intranet servers or to support a web-based network application, others will be relegated to the perimeter TCP/IP network address space, sometimes called the demilitarized zone (DMZ), as public front-end web servers. Regardless of the IIS 8 server's intended purpose, the installation process is the same.

# ## Adding the Web Server Role via Service Manager

Windows Server 2012 continues the concept of installing functionality into the OS by employing specific roles on the server. Assigning a role not only installs the services but also mandates dependency services and implies suggestions for hardening. To IIS 8, you need to deploy the Web Server Role on the server.

As with previous versions, IIS 8 consists of many modules. We cannot stress enough that you should add only the modules necessary to support your planned web content. Table 19.1 lists the roles and features available when using the Web Server Role in the OS, along with their corresponding feature names in PowerShell. By installing no more modules than absolutely necessary, you can build a web server with a smaller resource footprint and reduced attack surface. This strategy will give you a more secure, better-performing web server.

**Table 19.1:** OS Roles for IIS 8 (in the Same Order as in the Server Manager)

| SERVICE NAME (GUI) | POWERSHELL FEATURE NAME | DESCRIPTION | DEFAULT |
|---|---|---|--|
| Web Server | Web-WebServer | Publishes websites, web services, and web applications | Yes |
| Default Document | Web-Default-Doc | Configures a default file for websites to deliver when a page call is not specified in the URL | Yes |
| Directory Browsing | Web-Dir-Browsing | Autogenerates a list of directories/files for websites to deliver when a page call is not specified in the URL and the default document is disabled or not configured | Yes |

*Continues*