

The PHP client API does not support asynchronous LDAP operations.

## Replication

For those of us who are familiar with replication in databases, this is pretty much the same. In certain deployment scenarios that require near-zero downtimes, it is necessary that the LDAP server be up and running and serving the directory information all the time. This can be achieved by mirroring or replicating the information residing on the LDAP server on one or more other LDAP servers, which participate in the replication.

In some large installations there would be producer and consumer LDAP servers. The updates are always done to the producer servers and they are periodically replicated with the consumer servers. The clients always access the consumer servers. The advantage of this is that the client operations are fast since they talk to servers that are not bogged down by the performance overhead associated with updates.

## Referral

The referral service allows LDAP servers to distribute, de-centralize, and load-balance their processing. In the simple case of a referral, the LDAP server may choose to redirect the client to another LDAP server for a piece of information that the client requested. This allows for de-centralization because individual organizations within a company need to maintain only data specific to them and other servers can redirect queries to them that are specific to each of these organizational servers. Most of the client implementations follow these referrals and attempt to fetch the appropriate information. Thus, the whole process is transparent to the user.

## Security

LDAP directories may store sensitive information such as Social Security Numbers, passwords, private keys, and other sensitive information. The protocol provides for safe transaction of such sensitive data by providing SASL that is flexible enough to accommodate various underlying encryption or certification schemes.

A possible LDAP application is one that alleviates the arduous task of needing to remember a separate password for each of the several services that we access. Services which are LDAP aware could accept the LDAP directory password for the user and obtain the necessary authentication information from the directory for the particular service and carry on from there. Such a scheme in general is called a single sign on server. Further, LDAP enforces access control for the operations that various users can perform on the directory. We shall see more about access control when we take a look at configuring the LDAP server in the next section.

## Extended Features

In the functional model we have seen the basic nine operations that LDAP servers support. With LDAPv3 the need for allowing users to extend and customize the protocol has been addressed. This extensibility has been achieved through the following methods:

- **Extended operations**
  It is now possible to extend the protocol to support a new operation other than the basic nine operations. For example, it is now possible for vendors to implement server-side sorting of results or password expiration though these are not part of the standard. If a client or a server does not understand the new operation, the corresponding operation is ignored.

- Control information
  Additional information can now be sent along with an LDAP message that can alter the action of a basic protocol operation.

- SASL
  The SASL framework, as we have seen before, allows us to plug in new authentication and security mechanisms as they evolve without making modifications to the core protocol.

For further reading on LDAP, see *Understanding and Deploying LDAP Directory Services* from *Macmillan Technical Publishing* (ISBN 1-578700-70-1) and *Implementing LDAP* from *Wrox* (ISBN 1-861002-21-1).

## LDAP Software

In the LDAP server market space several companies offer comprehensive solutions:

- Netscape's Directory Server
- Innosoft's Distributed Directory Server
- Lucent Technology's Internet Directory Server
- Sun Microsystems' Directory Services
- IBM's DSSeries LDAP Directory
- Microsoft's Active Directory
- University of Michigan's SLAPD server

The OpenLDAP project based on the University of Michigan's implementation is currently considered to be the open source LDAP solution of choice with several fully-fledged features seen hitherto only in commercial offerings.

There are more LDAP client solutions than there are server solutions, because there exists a whole lot of software which have LDAP client logic built into them – address books, e-mail clients, and browsers with `ldap://` URL support are perfect examples.

Most of the server solutions mentioned above come with toolkits or libraries for client development, for example, Netscape's SDK for programming LDAP in C and Java. Other client-side programming solutions include the PerLDAP module for Perl, Sun's JNDI provider, and Microsoft's ADSI SDK. PHP has a client API that allows programming LDAP clients and ColdFusion is another server-side scripting tool that provides the LDAP API.

## Installing and Configuring an LDAP Server

Installing OpenLDAP in a *nix environment is a straightforward task. The software is available for download from http://www.openldap.org/. Here our server of choice is OpenLDAP due to the fact that this is an open source solution and is easily available with no licensing issues when used for non-commercial purposes.

To uncompress and unarchive the distribution:

```
tar xzvf openldap-stable-xyz.tgz
```

Change to the LDAP directory:

```
cd openldap-stable-xyz
```

To generate configuration information:

```
./configure --enable-ldbm --with-ldbm-api=gdbm
```

The --enable-ldbm flag tells that a back-end database has to be used and the --with-ldbm-api=gdbm flag says that this should be GDBM.

> If you do not have GDBM, you can get it from a GNU-mirror site:
> http://www.gnu.org/. Else, you can use the Berkley database or UNIX shell and
> specify the back-end datastore by the --with-ldbm-api directive while running the
> configure script.

To cause the source file to compile and generate the executable binaries:

```
make depend && make
```

To test that the distribution has been properly compiled:

```
cd tests; make
```

To plant the executable in the appropriate locations (make sure to be the root user when you do this):

```
cd ..
make install
```

### The OpenLDAP Config File

The OpenLDAP server has a configuration file that can be used to set several properties for the server
and the directory that it will serve. This file is /usr/local/etc/openldap/slapd.conf by default.

Let's take a look at a sample configuration file that has been tailored to suit our purposes of
experimentation. An exhaustive list of configurable parameters is available with the manual that comes
along with the OpenLDAP distribution:

```
include        /usr/local/etc/openldap/slapd.at.conf
include        /usr/local/etc/openldap/slapd.oc.conf
schemacheck off
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

