# mysql_tablename

```
mysql_tablename(result_id, row_number)
```

result_id should refer to a result set produced by a call to mysql_list_tables(), and will retrieve the name of the table listed on the row specified by row_number. The first row in a result set is row 0.

# mysql_get_client_info

```
mysql_get_client_info()
```

Returns a string that indicates the version of the MySQL client library built into PHP.

# mysql_get_host_info

```
mysql_get_host_info([link_id])
```

Returns a string that indicates the connection type and server host name in use for the default or specified (link_id) MySQL connection.

# mysql_get_proto_info

```
mysql_get_proto_info([link_id])
```

Returns a string that indicates the MySQL protocol version in use on the default or specified (link_id) MySQL connection.

# mysql_get_server_info

```
mysql_get_server_info([link_id])
```

Returns a string that indicates the MySQL server version in use on the default or specified (link_id) MySQL connection.