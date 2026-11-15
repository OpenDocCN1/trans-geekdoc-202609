On both operating systems, you also need environment variables that contain information about the Oracle installation:

+   - **ORACLE_HOME**
+     Oracle installation directory
+   - **ORACLE_SID**
+     Name of the database
+   - **NLS_LANG**
+     Language setting used
+   - **ORA_SDTZ**
+     Session time zone used

Windows users will find this information in the registry after the installation of Oracle and a reboot (important!). Unix/Linux users also need the LD_LIBRARY_PATH variable so that the libraries can be found. Another requirement for these operating systems is that the pthread library must be linked in Apache. This can be checked with ldd /path/to/httpd (see Figure 22.2).

```
christian@linux:~"# su
Password:
linux:/home/christian # ldd /usr/sbin/httpd
libmm.so.11 => /usr/lib/libmm.so.11 (0x40023000)
libm.so.6 => /lib/libm.so.6 (0x40028000)
libcrypt.so.1 => /lib/libcrypt.so.1 (0x4004b000)
libgdbm.so.2 => /usr/lib/libgdbm.so.2 (0x40076000)
libdb-4.0.so => /usr/lib/libdb-4.0.so (0x40086000)
libexpat.so.0 => /usr/lib/libexpat.so.0 (0x4011e000)
libdl.so.2 => /lib/libdl.so.2 (0x40410000)
libc.so.6 => /lib/libc.so.6 (0x40044000)
/lib/ld-linux.so.2 => /lib/ld-linux.so.2 (0x40000000)
linux:/home/christian # 
```

Figure 22.2 New Installation Necessary: This Apache Does Not Use "libpthread"

It is then worth calling phpinfo(), which (hopefully) shows the success of the installation (see Figure 22.3).

Next, you need to preconfigure the local Oracle instance accordingly. To do this, first create a user user with the password password (e.g., in SQL*Plus).2 This is made particularly easy by assigning the user the connect right (and in the example, also dba, which makes access easier later). If the user does not exist, it is simply created. Figure 22.4 shows the result in the command line.

It is somewhat more convenient to use the SQL Developer as a graphical user interface. You can download the tool free of charge from http://s-prs.co/v602229, but you will

2 Of course, you can also name the user differently and assign a different password; this is probably also advisable for security reasons. However, you will then have to modify all the code examples in this chapter.