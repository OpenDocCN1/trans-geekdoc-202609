# Glitchomatic Printware

> "Printing made... interesting!"

# Settings!

Welcome to the enchanting world of LDAP configuration for the Glitchomatic printer, where the boundaries of sanity and technicality blur in delightful harmony. Brace yourself for an exhilarating journey as we delve into the realm of directory services and embark on the whimsical quest to tame the wild LDAP beast.

Logged in as: admin
Logout
Print
Print Logs
Network Settings
Find Users
Documentation
Credentials for the ldapprinter account are stored here

Protocol: ldap
Server: 192.168.40.198
Port: 389
Username: ldapprinter@goblins.local
Password: ********
Save  Reset to Last Known Good

FIGURE 2.15  After logging in as the Admin on the printer, we can see there is a set of configured credentials on the device.

Now within this page, we can see that there is a configured set of credentials for LDAP. While it shows there's a password field, it's important to note that inspecting this field reveals that the password is not stored here. It is likely that the password remains on the printer and is intentionally not returned to the webpage to protect the credentials.

![](bbox=[0.12, 0.58, 0.9, 0.67])

```
<!-- We can't place the password in the DOM, that would be crazy!! -->
<tr>
<td></td>
<td>
<input type="password" name="password" value="********" < td> -- $0
</td>
</tr>
</tbody>
```

FIGURE 2.16  Identifying that the password is not in the DOM and is likely a placeholder.

However, since we have administrative access to this device, instead of trying to get the password onto the website, we can redirect where the printer will send the password. Instead of having it bind to the IP at 192.168.40.198, we can configure it to connect to us – where it will use its stored password!

To accomplish this, we will change the Server on the Network Settings page. Be careful not to change the username or the password, as it can easily overwrite the credentials we're trying to access. If we overwrite these, then we lose the chance we had at gaining further access (including a chance to take down operations for a paying customer – not good!).

After starting up a simple netcat listener with nc -nvlp 389 on the host we control, we can try to test the connection. Looks like we're very successful!