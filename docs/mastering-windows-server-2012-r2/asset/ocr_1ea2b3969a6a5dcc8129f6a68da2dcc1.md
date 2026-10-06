# TABLE 26.9 Computer Configuration: Internet Explorer (CONTINUED)

| ITEM | DESCRIPTION |
| --- | --- |
| Synchronize all offline files before logging | All marked files and folders are synchronized before a user is logged on. This guarantees that changes made by a user traveling with their laptop are copied to the file server. |
| Synchronize all offline files before logging | This guarantees that the user will have the latest copy of all files when they take their laptop away from the office. |
| Prohibit user configuration of offline files | Users are often the cause of problems on computers. You can configure offline files using a GPO and prevent users from tampering with that configuration. |

Computer Configuration\Administrative Templates\Windows Components\Internet Explorer contains a nested set of GPO settings for controlling how a user can manage Internet Explorer on a computer (see Table 26.9).

# TABLE 26.9 Computer Configuration: Internet Explorer

| ITEM | DESCRIPTION |
| --- | --- |
| Disable automatic install of Internet Explorer components | By default, users are prompted to download components when a web page requires them. You can prevent this behavior using this policy. |
| Make proxy settings per machine (rather than per user) | You can configure proxy settings for the machine and force those settings on all logged-users. |
| Security Zones: Do not allow users to add/delete sites | A zone in Internet Explorer changes the permissions for the sites in that zone and how IE will behave. Adding or deleting sites to or from a zone changes how IE will handle those sites. Enabling this setting forces a per-system configuration on all users to prevent them from editing zone memberships. |
| Internet Control Panel\Disable the connections page | This prevents users from being able to alter how the IE connects to the Internet, for example, via proxy settings.

A number of settings for controlling applications are built into Windows. You might need to do the following:

+   - Preconfigure these applications.
- Lock down their configuration.
- Prevent access to them.