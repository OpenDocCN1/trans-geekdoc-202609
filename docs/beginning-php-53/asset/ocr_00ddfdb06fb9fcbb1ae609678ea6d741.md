# Appendix B: Configuring PHP

```
; http://php.net/date.sunset-zenith
;date.sunset_zenith = 90.583333

[filter]
; http://php.net/filter.default
;filter.default = unsafe_raw

; http://php.net/filter.default-flags
;filter.default_flags =
```

```
[iconv]
;iconv.input_encoding = ISO-8859-1
;iconv.internal_encoding = ISO-8859-1
;iconv.output_encoding = ISO-8859-1

[intl]
;intl.default_locale =
```

```
[sqlite]
; http://php.net/sqlite.assoc-case
;sqlite.assoc_case = 0

[sqlite3]
sqlite3.extension_dir =
```

```
[Pcre]
;PCRE library backtracking limit.
; http://php.net/pcre.backtrack-limit
;pcre.backtrack_limit=100000

;PCRE library recursion limit.
;Please note that if you set this value to a high number you may consume all
the available process stack and eventually crash PHP (due to reaching the
stack size limit imposed by the Operating System).
; http://php.net/pcre.recursion-limit
;pcre.recursion_limit=100000
```

```
[Pdo]
; Whether to pool ODBC connections. Can be one of "strict", "relaxed" or "off"
; http://php.net/pdo-odbc.connection-pooling
pdo_odbc.connection_pooling=strict

;pdo_odbc.db2_instance_name
```

```
[Pdo_mysql]
; If mysqlnd is used: Number of cache slots for the internal result set cache
; http://php.net/pdo_mysql.cache_size
pdo_mysql.cache_size = 2000

; Default socket name for local MySQL connects. If empty, uses the built-in
; MySQL defaults.
; http://php.net/pdo_mysql.default-socket
```