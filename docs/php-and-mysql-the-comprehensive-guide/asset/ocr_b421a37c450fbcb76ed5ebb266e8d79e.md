Finally, you need to decide how PHP should connect to Oracle. There are several options here:

+   - Name of a local Oracle instance.
+   - Connection name stored in the tnsnames.ora configuration file.
+   - Use of the EasyConnect syntax, which is available from Oracle version 10g. The connection string looks something like a URL—for example, localhost/service name.

In the following, we assume that we use "orcl" as the connection string, either as a TNS entry or as a local instance name. If necessary, adapt this connection string to your respective system and make sure that the test user also has access to it.

Installation and configuration can therefore take some time; it is worth taking a look at the user comments in the PHP online manual in case of problems. Oracle also has special FAQs for use with PHP:

+   - http://s-prs.co/v602230 contains general information about the use of PHP.
+   - http://s-prs.co/v602231 leads to The Underground PHP and Oracle Manual, a detailed manual on development with PHP and Oracle. (At the time of publication, it was up to date with Oracle 11g R2.)
+   - http://s-prs.co/v602232 leads to the Oracle extension in PECL, currently maintained and often newer than what is delivered with PHP. From version 3, the extension is compatible with PHP 8; for PHP 7, it is best to use version 2.2.

# 22.2 Database Access with Oracle

Our new user naturally also wants to work with the database. The relevant tasks are described in the following sections. A word of warning first: In the course of the very laudable endeavor to make PHP function names more consistent, some things have changed as of PHP 5. Now all parts of function names are separated by an underscore—for example, oci_connect() and oci_fetch(). This was not the case in earlier versions, where the two functions were sometimes called differently and were each written without an underscore: ocilogon() and ocifetch(). For compatibility reasons, the old function names still work, but we only use the new variants.

# 22.2.1 Connection Setup

The connection is established is established with oci_connect(). The first two parameters are—as with some other PHP database modules—the user name and the password; the third parameter is the service name entered in the tnsnames.ora file (unless the environment variable or the ORACLE_SID registry entry is set, in which case the parameter can be omitted). The return value of the function is a database handle or false if something has gone wrong. The oci_close() function closes the connection again.