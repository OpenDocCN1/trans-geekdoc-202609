# Appendix B: Configuring PHP

```
; http://php.net/odbc.default-user
;odbc.default_user = Not yet implemented
```

```
; http://php.net/odbc.default-pw
;odbc.default_pw = Not yet implemented
```

```
; Controls the ODBC cursor model.
; Default: SQL_CURSOR_STATIC (default).
;odbc.default_cursetype
```

```
; Allow or prevent persistent links.
; http://php.net/odbc.allow-persistent
odbc.allow_persistent = On
```

```
; Check that a connection is still valid before reuse.
; http://php.net/odbc.check-persistent
odbc.check_persistent = On
```

```
; Maximum number of persistent links. -1 means no limit.
; http://php.net/odbc.max-persistent
odbc.max_persistent = -1
```

```
; Maximum number of links (persistent + non-persistent). -1 means no limit.
; http://php.net/odbc.max-links
odbc.max_links = -1
```

```
; Handling LONG FIELDS. Returns number of bytes to variables. 0 means
passthru.
; http://php.net/odbc.defaultlrl
obdc.defaultlrl = 4096
```

```
; Handling of binary data. 0 means passthru, 1 return as is, 2 convert to char.
; See the documentation on odbc_binmode and odbc_longread for an explanation
of of odbc.defaultlrl and odbc.defaultbinmode
; http://php.net/odbc.defaultbinmode
obdc.defaultbinmode = 1
```

```
;bindstep.max_links = -1
```

```
[Interbase]
; Allow or prevent persistent links.
ibase.allow_persistent = 1
```

```
; Maximum number of persistent links. -1 means no limit.
ibase.max_persistent = -1
```

```
; Maximum number of links (persistent + non-persistent). -1 means no limit.
ibase.max_links = -1
```

```
; Default database name for ibase_connect().
ibase.default_db = -
```

```
; Default username for ibase_connect().
```