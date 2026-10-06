# RODC Contents

RODC holds all the Active Directory accounts and most of the attributes that can be found on a writable DC. A significant difference between an RODC and a writable DC is that an RODC holds very few passwords.

Specifically, the RODC will typically hold only the passwords of nonadministrator users who log on in the remote office. Other passwords are blocked from being stored on the RODC.

Figure 23.2 shows the process if an RODC is placed in a remote office. Imagine Sally logging onto the RODC for the first time. Her system will contact the RODC. The RODC doesn't have her account cached, so it will query the DC at the headquarters location.

# FIGURE 23.2
RODC logon process

![](bbox=[0.338, 0.343, 0.836, 0.483])

The DC at HQ will authenticate Sally's credentials and it will also check the password replication policy to determine whether her credentials can be cached on the RODC. By default, no passwords will be cached on the RODC. However, it's common to allow credentials for nonadministrator users working at the remote office to be cached. Any passwords that aren't specifically allowed will not be cached on the RODC.

The next time Sally logs on the remote site, her credentials are verified with the cached credentials on the RODC. The term cached credentials means that they are stored in a temporary location on the server's hard drive.

# CACHED ON THE RODC HARD DRIVE

If you're a hardware guy or gal, you may be thinking of cache because it refers to memory used to improve performance. For example, L1 and L2 cache are additional memory to improve the performance of the processor. Memory is volatile, and its contents be lost when the system is shut down or rebooted. However, credentials cached on an RODC are stored on the hard drive of the RODC. These credentials will be maintained even if the RODC loses power or is rebooted.