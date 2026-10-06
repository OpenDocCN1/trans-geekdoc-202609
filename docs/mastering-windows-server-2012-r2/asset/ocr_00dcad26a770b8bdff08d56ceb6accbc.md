# TABLE 19.1: OS Role Services for IIS 8 (in the Same Order as in the Server Manager Wizard) (CONTINUED)

| SERVICE NAME (GUI) | POWERSHELL FEATURE NAME | DESCRIPTION | DEFAULT |
| :--- | :--- | :--- | :--- |
| FTP Server | Web-Ftp-Server | Provides infrastructure to build FTP sites that use FTP for uploading and downloading | No |
| FTP Service | Web-Ftp-Service | Enables FTP publishing | No |
| FTP Extensibility | Web-Ftp-Ext | Supports FTP extensibility features as custom providers, ASP.NET users, or IIS Manager users | No |
| IIS Hostable Web Core | Web-WHC | Enables applications outside of IIS to serve requests using their own .config files | No |
| IIS Management Console | Web-Mgmt-Console | Provides GUI management of IIS 7.5 web services (not FTP or SMTP) | Yes |
| IIS 6 Management Compatibility | Web-Mgmt-Compat | Provides ABO and ADSI support for existing IIS 6.0 management services | No |
| IIS 6 Metabase Compatibility | Web-Metabase | Provides IIS 6.0 metabase and configuration support for ABO and ADSI applications | No |
| IIS 6 Management Console | Web-Lcy-Mgmt-Console | Provides infrastructure for administration of remote IIS 6 servers and administration of FTP and SMTP | No |
| IIS 6 Scripting Tools | Web-Lcy-Scripting | Provides infrastructure to run IIS 6 scripts on IIS 7.5 including ADO and ADSI (requires WAS) | No |
| IIS 6 WMI Compatibility | Web-WMI | Provides WMI interface for remote management and automation tasks using CIM Studio, WMI Event Registration, WMI Event Viewer, and WMI Object Browser | No |
| IIS Management Scripts and Tools | Web-Scripting-Tools | Provides CLI and scripted management of IIS, which is valuable for automating administration | No |
| Management Service | Web-Mgmt-Service | Provides infrastructure for remote GUI of IIS | No |

# A WEB SERVER FOR BIGFIRM

We will be using the Service Manager GUI to create two websites on a Windows Server 2012 R2 host Microsoft IIS 8.5. Website 1 will be dedicated to applications and website 2 will focus on oranges.