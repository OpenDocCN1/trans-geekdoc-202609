cron daemon. When a field is given an asterisk (*), it means that the command should be used for all of its matching values for that field. Cron values can be confusing, but there are several resources online that can help us understand and better parse the information we identify. For example, the image below can be used to help determine what each character is interpreted as by cron.

![](bbox=[0.284, 0.189, 0.714, 0.332])

**FIGURE 7.7** Crontab execution fields definition, retrieved from [https://commons.wikimedia.org/wiki/File:Crontabks4.th.png](https://commons.wikimedia.org/wiki/File:Crontabks4.th.png).

Take the crontab below for example. This command will execute the command **/bin/sh /tmp/backdoor.sh** every five minutes and based on the filename is likely a persistence mechanism. Investigating the file located at **/tmp/backdoor.sh** should reveal an interesting analysis for a potential backdoor on the asset.

```
5 * * * * /bin/sh /tmp/backdoor.sh
```

Additional online resources include the **crontab.guru** website, which will take a crontab configuration and help explain it in plain language. Taking our example from above, we place it into the website and can better understand how it will be interpreted.

![](bbox=[0.142, 0.581, 0.858, 0.801])

**FIGURE 7.8** Utilizing crontab.guru to help understand crontab configurations in plain language.

The Cron daemon (crond) searches through the crontab to try and identify cronjobs that are ready to be executed. As the specific intervals for the cronjobs are reached, they will be executed as required. By default, crontabs are stored in the **/var/spool/cron** folder for each user account and are only readable by the specific user. Because of this, we cannot simply peek at all of the cronjobs in these folders to see what jobs will occur.