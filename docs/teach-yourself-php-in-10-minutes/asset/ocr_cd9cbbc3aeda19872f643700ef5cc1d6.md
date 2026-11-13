Some packages cannot be installed unless others are already installed on your system, and installation will fail if the required packages are not found. The following output shows an attempt to install the Mail_Queue package before the Mail package has been installed:

```
# pear install Mail_Queue
downloading Mail_Queue-1.1.3.tar ...
Starting to download Mail_Queue-1.1.3.tar (-1 bytes)
....done: 98,816 bytes
requires package `Mail'
Mail_Queue: Dependencies failed
```

Some dependencies are optional. When you install the Mail package to fix the dependency reported in the previous error message, PEAR advises you that the functionality of the Mail package can be enhanced if you also install Net_SMTP :

```
# pear install Mail
downloading Mail-1.1.4.tar ...
Starting to download Mail-1.1.4.tar (-1 bytes)
....done: 73,728 bytes
Optional dependencies:
package `Net_SMTP' version >= 1.1.0 is recommended to
utilize some features.
install ok: Mail 1.1.4
```

You can use the upgrade command option to download and install a later version of an installed package. To check whether a new version of the Mail package is released, you use the following command:

```
# pear upgrade Mail
```

If a later version than the one installed is found, it is upgraded automatically.

![](bbox=[0.11, 0.69, 0.159, 0.742])

**Upgrading Packages** You can use the upgrade-all command to check for newer versions of all your installed PEAR packages at once.

If you want to remove a PEAR package completely, you use the uninstall command.

# # Contributing Your Own PEAR Project