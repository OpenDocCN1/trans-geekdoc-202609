# Understanding Global Settings

Before creating a new website, you should understand what global settings are defined at the server level in the three server configuration files:

**Machine.config** Located in the %windir%\Microsoft.Net\Framework\Framework_versionCONFIG directory. This file contains the defaults for the .NET framework; it also contains some of the settings for ASP.NET.

**Root.web** Located in the %windir%\Microsoft\Framework\framework_versionCONFIG directory. This configuration file contains the remaining settings for ASP.NET.

**applicationhost.config** Located in the %windir%system32\inetrv directory, which is a file with very limited NTFS ACL access by default (see Table 19.2).

The application.config file is the root file of the configuration. It includes the definition of all sites, virtual directories, and application pools, in addition to the global defaults.

# Planning BigFarm’s Apples and Oranges Websites

One of the most popular protocols is still HTTP for static content, so let’s concentrate on creating static HTTP websites. First, you will create a virtual directory within the Default Site and then you will create a separate Orange website using different protocol bindings. The Oranges site will need to support ASP pages, you should run it in a separate application pool. And that both of your sites need to have different bindings and URLs, you should create the oranges pages as a new, separate website. However, the apples will add the apple content as a new virtual directory into the Default Web Site.

When deciding between adding as a virtual directory to the Default Web Site versus creating a second application version within the Default Web Site to support the apples content, the ultimate factor is code support. Virtual calls give you the opportunity to assign a unique application pool to them. Since the apples are simply delivering static .htm content, creating a new application for these IIS servers would be overkill for this illustration. However, when planning your own IIS implementation, you should plan for growth, scale, and deployment. If you think a set of pages will eventually need to code, go ahead and build an application at the beginning and grow down into the road.

IIS  off the Default Web Site, which listens on TCP port 80 across all interfaces and is not configured for any particular host. If these dimensions are acceptable for your new website, feel free to direct the Default Web Site to your content of creating an additional site. This will work fine for the apples sites.

# Table 19.2: NTFS Permissions on applicationhost.config

| ACCESS CONTROL ENTRY | ALLOWED PERMISSION |
|---|---|n| Administrators | Full Control |
| SYSTEM | Full Control |
| TrustedInstaller | Full Control |