SYSTEM account, it can pretty much get to anything. If hackers compromised the service, it is likely that they could then execute arbitrary code allowing them to do all kinds of horrible things.

Though many of these services won't work (well or at all) without high-level access, you can use the Log On tab to modify their rights in an attempt to rein them in. This process is trial and error. The best method is to assign the relevant user credentials and then attempt to restart the service. If it works, you could be in business, but you need to initiate a process that uses the service to be sure. If errors result, change the Log On settings back to their defaults and try another tactic.

![](bbox=[0.19, 0.33, 0.53, 0.62])

# Figure 2-3: Services Properties Sheet: Logon tab.

+   Dependencies: On this tab, you find the services that depend on the service in question, and those services on which it depends. For example, if you want to disable the Event Log (see Figure 2-4), you notice that the Event log depends on no other services. This means you can disable any service without affecting the Event Log. However, several services require the Event Log in order to work. For example, if you disable the Event Log, the File Replication Service will no longer work.

For every service you want to disable, make sure that you're not going to inadvertently break a service you need. You should also note that you can set service to manual startup rather than automatic or disabled. This is a useful setting if you're unsure if an application will require it. If an application does need the service, it will be able to start it.