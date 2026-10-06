# CHAPTER 19 WEB SERVER MANAGEMENT WITH IIS

2. Enter a site name that is descriptive but concise; in this case enter Oranges.

The value entered in this field will automatically generate a new .NET integrated-mode application pool by default and assign it to the new site unless you specify an existing application pool with the Select button. The new application pool will be created with the parameter settings defined using the Set Application Pool Defaults linkable in the Actions pane when focused on the Application Pools in Connections. Also, by default a new system-generated identity account will be automatically created with the same name as the pool for security purposes.

3. Enter the physical path of the website folder, C:\inetpub\oranges.

4. By default pass-through authentication credentials are used; should you need to change to a specific account, click the "Connect as" button.

5. Select HTTP from the Protocol type.

6. Use the All Unassigned value for "IP address" to bind the new Oranges site to any and all IP addresses configured on all server network interfaces if not already assigned to other websites in IIS.

7. Leave the Port setting at 80.

Note that this value requires the clients to provide the chosen custom port number upon each request.

8. For the "Host name" setting, enter oranges to differentiate it from the apples pages within the Default Site.

To easily allow new sites created going forward to have specific settings, consider altering the Application Pool Defaults and Web Site Defaults to affect future site creations. Links to these dialog boxes appear in the Actions pane of IIS Manager when highlighting the Application Pools node or Sites node, respectively, in the Connections pane, as shown in Figure 19.12, Figure 19.13, and Figure 19.14.

# FIGURE 19.12

Add roles and features task list

![](bbox=[0.378, 0.646, 0.773, 0.878])