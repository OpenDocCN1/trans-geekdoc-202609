# boolean ldap_bind(integer link, string dn, string password)

Use ldap_bind to bind to a directory. Use the optional dn and password arguments to identify yourself. Servers typically require authentication for any commands that change the contents of the directory.

# boolean ldap_close(integer link)

The ldap_close function closes the connection to the directory server.

# integer ldap_connect(string host, integer port)