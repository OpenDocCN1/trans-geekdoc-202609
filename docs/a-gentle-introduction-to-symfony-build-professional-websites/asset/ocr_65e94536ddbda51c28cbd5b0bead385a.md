The session is started (with the PHP function session_start()) only if the auto_start parameter is set to true in factories.yml (which is the case by default). If you want to start the user session manually, disable this setting of the storage factory.

Symfony's session handling is based on PHP sessions. This means that if you want the client-side management of sessions to be handled by URL parameters instead of cookies, you just need to change the use_trans_sid setting in your php.ini. Be aware that this is not recommended.

```
session.use_trans_sid = 1
```

On the server side, symfony stores user sessions in files by default. You can store them in your database by changing the value of the class parameter in factories.yml, as shown in Listing 6-18.

# Listing 6-18 - Changing the Server Session Storage, in apps/frontend/config/factories.yml

```
all:
 storage:
   class: sfMySQLSessionStorage
   param:
     db_table:   session  # Name of the table storing the
     sessions
     database:   propel   # Name of the database connection
     to use
     # Optional parameters
     db_id_col:  sess_id   # Name of the column storing the
     session id
     db_data_col: sess_data  # Name of the column storing the
     session data
     db_time_col: sess_time  # Name of the column storing the
     session timestamp
```

The database setting defines the database connection to be used. Symfony will then use databases.yml (see Chapter 8) to determine the connection settings (host, database name, user, and password) for this connection.

The available session storage classes are sfCacheSessionStorage, sfMySQLSessionStorage, sfMySQLiSessionStorage, sfPostgreSQLSessionStorage, and sfPDOSessionStorage; the latter is preferred. To disable session storage completely, you can use the sfNoStorage class.

Session expiration occurs automatically after 30 minutes. This default setting can be modified for each environment in the same factories.yml configuration file, but this time in the user factory, as shown in Listing 6-19.

# Listing 6-19 - Changing Session Lifetime, in apps/frontend/config/factories.yml

```
all:
 user:
   class:   myUser
   param:
     timeout: 1800     # Session lifetime in seconds
```

To learn more about factories, refer to Chapter 19.