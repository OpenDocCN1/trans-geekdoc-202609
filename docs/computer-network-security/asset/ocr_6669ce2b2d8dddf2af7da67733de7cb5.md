# Part D: securing access using “view” management

+   1. Create a new user account “User01” with the encrypted password” Us01paSS”.

```
R1(config)# username User01 secret Us01paS$
```

+   2. Activate the “AAA” on R1.

```
R1# config terminal
R1(config)# aaa new-model
R1(config)# exit
```

+   3. Create a “ViewRouter” view.

```
R1#enable view
Password: (password enable)
R1#conf t
R1(config)# parser view ViewRouter
R1(config-view)#
```

+   4. Assign the password “ViewRouPs” to this view.

```
R1(config-view)# secret ViewRouPs
```

+   5. For this view, allow all the “show” commands in exec mode.

```
R1(config-view)# commands exec include all show
```

+   6. Allow all commands in the configure mode.

```
R1(config-view)# commands exec include all configure terminal
```

+   7. Allow all commands for the mode in router mode.

```
R1(config-view)# commands configure include all router
```

+   8. Follow the same steps to create a “ViewTelnet” view and to endow it with the following options:

+   - Password ViewTelPs;

+   - The authorized commands: telnet, traceroute, show (all).