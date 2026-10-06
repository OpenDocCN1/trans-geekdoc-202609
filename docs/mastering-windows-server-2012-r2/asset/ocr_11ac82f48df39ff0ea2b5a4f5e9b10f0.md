# FEATURE DELEGATION

Feature delegation is alive and the best solution for distributing administration of IIS 8 between the administrators and other users, for example, developers. Essentially, feature delegation is the practice of unlocking certain server-level configuration settings in the applicationhost.config file so that users, developers and site administrators, can avoid overriding that settings on specific sites. However, planning feature delegation could be like walking a tightrope—one false step leads to security threats. When it comes to configuring the feature delegation on each feature, consider carefully whom you trust enough to manage resource utilization and security decisions for your web server. If you delegate a feature to an inexperienced administrator, you may unintentionally expose the entire server to malicious code or compromise all the websites on your server. Governing and planning feature delegation should rank high on your priority list.

In essence, the effect of delegating a feature involves unlocking sections of one or more sites' web.config files. By allowing configuration settings to be Read-Write for a named group of users, you are allowing those users to make configuration changes to one or more websites without needing to contact the administrator, but only so far as configure the specific feature and not. The users will be able to make configuration changes to the site that affect digest authentication, but they will not be able to alter settings that affect ASP behavior. Feature delegation can be performed either at the server-level to identify site defaults or at the site-level to disallow inheritance of the server default and configure delegation by site. In other words, if there is a conflict as which features are delegated to whom, the site-level delegation wins the conflict.

But, wait, which sites your chosen users can make configuration changes to also depends on the ACL of the web.config files. Just because a feature has been delegated doesn't mean that your chosen users have anything beyond permission to access the site's web.config file. You now must grant your chosen users the write permission to their sites' web.config files to allow them to whatever feature configuration settings have been unlocked. Feature delegation and NTFS ACLs must be maintained in union to achieve the most effective configuration.

# Delegating Administration

In a large IIS environment supported by a legion of IT administrators, it stands to reason that different personnel may be responsible for managing different sites. On a single instance of IIS, delegating administrative responsibilities at the site level requires that the server-level administrator unlock specific aspects of the lower sites.

In the server-application.config file, the preferred method of unlocking specific configuration sections of lower website definitions so that they can be managed by website administrators is to add a <location> tag. For example, if you want HTTP logging at the website by website level, you can also alter the applicationhost.config file as follows:

```
<location path="Default Site" overrideMode="Allow">
<system.webServer>
  <httpLogging />
</system.webServer>
</location>
```