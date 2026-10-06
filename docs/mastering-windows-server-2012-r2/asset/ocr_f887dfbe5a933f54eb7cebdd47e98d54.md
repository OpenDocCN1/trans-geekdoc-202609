# CHAPTER 19 WEB SERVER MANAGEMENT WITH IIS

# TABLE 19.5: .NET Trust Levels

| TRUST LEVEL | PURPOSE |
|---|---|
| Full (internal) | Access to all resources pursuant to OS security |
| High (web_hightrust.config) | Cannot call code or services, write to event log, or access MSSQ, ODBC, OleDb |
| Medium (web_mediumtrust.config) | High restrictions, cannot access files outside the application directory hierarchy, access the registry, or make network/web services call |
| Low (web_lowtrust.config) | High and medium restrictions, cannot write to file system and cannot call the Assert method |
| Minimal (web_minimaltrust.config) | Execute permissions only by default |

# INVOKING SSL

Secure Sockets Layer (SSL) protection has been around for many generations of the IIS product. By now, you likely realize that SSL is used to protect data that is passed to and from an IIS server. To invoke SSL on an IIS  website, you must first create an HTTPS binding on the site. To add bindings to a site, follow these steps:

+   1. Launch IIS Manager, and expand the IIS server in the Connections pane on the left.
2. Expand the Sites folder, and highlight the site requiring SSL.
3. In the Actions pane on the right, click Bindings.
4. Click the Add button in the Site Bindings dialog box.
5. Change the binding type from HTTP to HTTPS, and specify the certificate to be used.

Now that SSL has been bound to the website, you can fine-tune its behavior by doubleclicking the SSL Settings icon on the home page of the site. Choose the bit level and whether client-side certificates will be required or honored.

# LOGGING

Previous versions of IIS logging were limited. You were restricted to a fixed set of standard fields, with no way to extend or customize them. Creating of custom logging module, you were stuck. With the release of IIS 8.5, all that has changed. To expand or customize your logging options, follow these steps:

+   1. Launch IIS Manager, select the site or server in the Connections pane, and double-click Logging.
You have seven standard logging options in addition to those available by default.
2. Under Format, select W3C, and then click Select Fields.
3. In the W3C logging Fields page, click Add Field.