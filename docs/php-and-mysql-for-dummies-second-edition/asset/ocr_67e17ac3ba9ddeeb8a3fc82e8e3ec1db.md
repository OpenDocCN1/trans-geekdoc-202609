![](bbox=[0.1, 0.22, 0.2, 0.32])

The MySQL server will accept connections from a MySQL account only when it is connecting from hostname. When you build the `GRANT` or `REVOKE` query (which I describe later in this chapter), you identify the MySQL account by using both the account name and the hostname in the following format: `accountname@hostname` (for instance, `root@localhost`).

The MySQL account name is completely unrelated in any way to the Unix/Linux or Windows user name (also sometimes called the *login name*). If you're using an administrative MySQL account named `root`, it is not related to the Unix/Linux `root` login name. Changing the MySQL login name does not in any way affect the Unix/Linux or Windows login name — and vice versa.

MySQL account names and hostnames are defined as follows:

+   - **An account name can be up to 16 characters long.** You can use special characters in account names, such as a space or hyphen (-). However, you cannot use wildcards in the account name.
+   - **An account name can be blank.** If an account exists in MySQL with a blank account name, any account name will be valid for that account. A user could use any account name to connect to your database, given that the user is connecting from a hostname that is allowed to connect to the blank account name and uses the correct password, if required. You can use an account with a blank name to allow anonymous users to connect to your database.
+   - **The hostname can be a name or an IP address.** For example, it can be a name such as `thor.mycompany.com` or an IP (Internet protocol) address such as `192.163.2.33`. The machine on which the MySQL server is installed is `localhost`.
+   - **Wildcards can be used in the hostname.** You can use a percent sign (%) as a wildcard; % matches any hostname. If you add an account for `george@%`, someone using the account named `george` can connect to the MySQL server from any computer.
+   - **The hostname can be blank.** A blank hostname is the same as using % for the hostname.

An account with a blank account name and a blank hostname is possible. Such an account would allow anyone to connect to the MySQL server by using any account name from any computer. An account with a blank name and a percent sign (%) for the hostname is the same thing. It is very unlikely that you would want such an account. Such an account is sometimes installed when MySQL is installed, but it's given no privileges, so it can't do anything.