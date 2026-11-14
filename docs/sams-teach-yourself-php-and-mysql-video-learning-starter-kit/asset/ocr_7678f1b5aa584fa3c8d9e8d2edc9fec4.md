| OPTION | MEANING |
|---|---|
| -D | Allows you to pass a parameter that can be used for <IfDefine> section processing |
| -l | Lists compiled-in modules |
| -v | Shows version number and server compilation time |
| -f | Allows you to pass the location of httpd.conf if it is different from the compile-time default |

After Apache is running, you can use the kill command on Linux/UNIX and Mac OS X to send signals to the parent Apache process. Signals provide a mechanism to send commands to a process. To send a signal, execute the following command:

```
# kill -SIGNAL pid
```

In this syntax, pid is the process ID and SIGNAL is one of the following:

+   - HUP—Stop the server
+   - USR1 or WINCH—Graceful restart; which signal to use depends on the underlying operating system
+   - SIGHUP—Restart

If you make some changes to the configuration files and you want them to take effect, you must signal Apache that the configuration has changed. You can do this by stopping and starting the server or by sending a restart signal. This tells Apache to reread its configuration.

A normal restart can result in a momentary pause in service. A graceful restart takes a different approach: Each thread or process serving a client continues processing the current request, but when it finishes, it is killed and replaced by a new thread or process with the new configuration. This allows seamless operation of the web server with no down-time.

On Windows, you can signal Apache using the apache.exe executable. Some commands are listed here:

+   - apache.exe -k restart—Tells Apache to restart
+   - apache.exe -k graceful—Tells Apache to do a graceful restart
+   - apache.exe -k stop—Tells Apache to stop