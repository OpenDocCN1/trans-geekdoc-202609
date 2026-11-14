# 2.6. Allocation of administrative roles

# 2.6.1. Privilege levels of the IOS system

Privilege levels determine a user’s ability to run certain commands on a router. By default, Cisco routers have three privilege levels, namely “zero”, “user” and “privileged":

+   - level zero: this allows only five commands: _logout, enable, disable, help et exit_;

+   - user level (level 1): this provides very limited read-only access to the router;

+   - privileged level (level 15): this provides complete control over the router.

For added flexibility, Cisco routers can also be configured to use 16 different privilege levels (from 0 to 15).

# 2.6.2. Configuring a privilege level

| Command | Description |
|---|---|
| Router(config)# privilege mode { level level command | reset command } | Allows the use of a command at a custom privilege level. |
| Router(config)# enable secret level level password | Assigns a password at the custom privilege level. |
| Router> enable level | Accesses the custom privilege level. |

# Example for the use of the commands

| Command | Description |
|---|---|
| R1(config)# privilege exec level 5 ping | Allows permission to use the “ping” command at privilege level 5. |
| R1(config)# privilege exec level 5 reload | Allows permission to use the “reload” command at privilege level 5. |
| R1(config)# enable secret level 5 tri | Enables the configuration of an Enable password to access level 5. |
| R1> enable 5 Password: | Allows user access with privilege 5. In addition to regular Level 1 commands, Level 5 users can also use the “ping” and “reload” commands. |
| R1# show privilege Current privilege level is 5 | Privilege Level Verification. |