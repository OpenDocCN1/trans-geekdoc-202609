Wait a minute for the reboot to complete and for the droplet to come back online. Then you should be able to reconnect and use `systemctl status` to check that the service is running again. Like so:

```
$ make production/connect
greenlight@greenlight-production:~$ sudo systemctl status api.service
[sudo] password for greenlight:
● api.service - Greenlight API service
    Loaded: loaded (/etc/systemd/system/api.service; enabled; vendor preset: enabled)
    Active: active (running) since Mon 2021-04-19 03:36:26 EDT; 16s ago
    Main PID: 774 (api)
    Tasks: 5 (limit: 1136)
    Memory: 8.7M
    CGroup: /system.slice/api.service
            └─774 /home/greenlight/api -port=4000 -db-
 ds n=postgres://greenlight:pa55word1234@localhost/greenlight -env=production

Apr 19 03:36:26 greenlight-production systemd[1]: Starting Greenlight API service...
Apr 19 03:36:26 greenlight-production systemd[1]: Started Greenlight API service.
Apr 19 03:36:26 greenlight-production api[774]: {"level":"INFO","time":"2021-04-19T07:36:26Z", ...}
Apr 19 03:36:26 greenlight-production api[774]: {"level":"INFO","time":"2021-04-19T07:36:26Z", ...}
```

# Disable port 4000