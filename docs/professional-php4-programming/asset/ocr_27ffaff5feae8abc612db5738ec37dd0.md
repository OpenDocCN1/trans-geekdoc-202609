```
referral   ldap://ldap.itd.umich.edu

pidfile    /usr/local/var/slapd.pid
argsfile   /usr/local/var/slapd.args

access to * by * write

#######################################################################
#  ldbm database definitions
#######################################################################

database   ldbm
suffix     "o=myorg, c=US"
directory  /home/myhome/test-addr
rootdn     "cn=root,o=myorg, c=US"
rootpw     opensesame
```

The comments within the file start with a # character and go on to the end of the line.

The include directive causes another file to be included into this file, that is, the files slapd.at.conf and slapd.oc.conf are read and interpreted first before proceeding with the rest of the directives in the slapd.conf file. Incidentally the slapd.oc.conf file contains the object definitions for several generic objects (for example, the inetOrgPerson object that we saw earlier). The file slapd.at.conf contains definitions for generic object classes with pre-defined minimum attributes.

The schemacheck directive takes a value of either on or off and determines whether the objects present in the directory will be checked for conformance with the schema of the directory. While experimenting, we could set this to off.

The referral directive causes the LDAP server to advise the client to redirect the LDAP message to another LDAP server (specified as an ldap:// URL argument) if the server realizes that the client asked for something that it couldn't provide.

The pidfile and argsfile directives are for the server to maintain certain information about the instances of it that have been started. This is not much of a concern for us, and not adding these directives usually makes little difference as the server defaults to a setting that is acceptable.

The access directive implements the access-control features of the LDAP server by determining who has access to what in the directory. We shall set this to access to * by * write, meaning that everybody should have write access to all entries in the directory (which is probably not a good idea in a production environment).

The database directive tells the server to use a database as the back-end and the directory directive tells the server where the actual database and indexing files can be found.

The argument of the suffix directive is passed on as a suffix to queries made on the directory. This means that the queries need not specify the complete DN for each operation.

The rootdn directive tells the server about the root of the directory. An administrator binds to the directory using this DN to perform various administrative tasks. The rootpw directive sets the password for the administrator.