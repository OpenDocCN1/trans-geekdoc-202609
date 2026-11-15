# 33.2 IIS Authentication

Internet Information Services (ISS)2 is Microsoft's standard web server in Windows. In production systems, it is usually the case that IIS is used on Windows machines and that Apache is not used. The IIS offers a range of authentication options. However, some of these are not suitable for web use. The integrated Windows authentication via Kerberos is only useful for intranets, for example, as the client and server should belong to the same domain.

Basic authentication (standard authentication) and digest authentication, which you already know from Apache, come into question here. The IIS uses the same HTTP capabilities. The major disadvantage of IIS compared to Apache is that existing Windows user accounts are used for authentication. Regardless of where the associated lists are stored, this always involves some effort.

> **Note**
> 
> One method that is used in library systems, for example, is IP identification. Only a previously defined IP range is permitted on the user's own pages. This authentication can be implemented with or without password identification. However, it never makes any sense where there are users with flexible IP addresses. This is the case, for example, with most internet service providers. In addition, a professor, for example, can only view his books if he is currently within the university network. If he is at a conference, then this system is useless for him.

To use the standard authentication in IIS, the following steps are necessary:

+   1. First of all you need the basic authentication activated. Go to **Turn Windows features on or off**. You can find it in the **Control Panel • Programs and Features**.  
+   2. Go to **World Wide Web Services • Security** and activate **Basic Authentication**.  
+   3. Open **Internet Information Services (IIS) Manager**. You can find it in the **Control Panel**.  
+   4. In the **Connections** pane, expand the server name, expand **Sites**, and then click the site for which you want to enable basic authentication.  
+   5. Click on **Authentication** and enable **Basic Authentication**.  
+   6. As next step **Anonymous Authentication** has to be disabled.

You can now add users or user groups as needed for this directory. In the configuration the `<basicAuthentication>` is now available. To use digest authentication, you must switch to a user account and select reversible encryption for one of the users there.