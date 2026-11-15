# Appendix B: Configuring PHP

```
; Default user for mysql_connect() (doesn't apply in safe mode).
; http://php.net/mysql.default-user
mysql.default_user =
```

```
; Default password for mysql_connect() (doesn't apply in safe mode).
; Note that this is generally a *bad* idea to store passwords in this file.
; *Any* user with PHP access can run 'echo get_cfg_var("mysqli.default_password")
; and reveal this password! And of course, any users with read access to this
; file will be able to reveal the password as well.
; http://php.net/mysqli.default-password
mysqli.default_password =
```

```
; Maximum time (in seconds) for connect timeout. -1 means no limit
; http://php.net/mysql.connect-timeout
mysql.connect_timeout = 60
```

```
; Trace mode. When trace_mode is active (=On), warnings for table/index scans and
; SQL-Errors will be displayed.
; http://php.net/mysql.trace-mode
mysql.trace_mode = Off
```

# [MySQLi]

```
; Maximum number of persistent links.  -1 means no limit.
; http://php.net/mysqli.max-persistent
mysqli.max_persistent = -1
```

```
; Maximum number of links.  -1 means no limit.
; http://php.net/mysqli.max-links
mysqli.max_links = -1
```

```
; If mysqlnd is used: Number of cache slots for the internal result set cache
; http://php.net/mysqli.cache_size
mysqli.cache_size = 2000
```

```
; Default port number for mysqli_connect().  If unset, mysqli_connect() will use
; the $MYSQL_TCP_PORT or the mysql-tcp entry in /etc/services or the
; compile-time value defined MYSQL_PORT (in that order).  Win32 will only look
; at MYSQL_PORT.
; http://php.net/mysqli.default-port
mysqli.default_port = 3306
```

```
; Default socket name for local MySQL connects.  If empty, uses the built-in
; MySQL defaults.
; http://php.net/mysqli.default-socket
mysqli.default_socket =
```

```
; Default host for mysql_connect() (doesn't apply in safe mode).
; http://php.net/mysql.default-host
mysqli.default_host =
```

```
; Default user for mysqli_connect() (doesn't apply in safe mode).
; http://php.net/mysqli.default-user
```