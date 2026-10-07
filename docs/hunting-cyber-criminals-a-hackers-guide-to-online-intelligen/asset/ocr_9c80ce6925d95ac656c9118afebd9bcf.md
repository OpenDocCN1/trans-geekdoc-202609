# Chapter 5 Automated Tools for Network Discovery 113

[recon-ng] [OSINT] [reverse_resolve] > show hosts

| rowid | host | ip | region | country | latitude | longitude | module |
| 1 | vps.uberpeople.net | 184.154.76.235 | | | | |reverse_resolve |

[*] 1 rows returned

The information in our database can now be used for running scans. Let's see if we can find any new information on our host using the virustotal module. The virustotal module will look for information on any of the domains listed in the hosts table, in our case vps.uberpeople.net against VirusTotal.com database of information. If any new information is found, Recon-NG will automatically update our hosts:

```
[recon-ng] [OSINT] > use recon/hosts/virustotal
[recon-ng] [virustotal] > run
```

```
184.154.76.235

[*] host maybedmybreakfastfast.com (184.154.76.235)
[*] host maybedmybreakfast.uberpeople.net (184.154.76.235)
[*] host beepplam.com (184.154.76.235)
[*] host livewithanyone.com (184.154.76.235)
[*] host motokoband.uberpeople.net (184.154.76.235)
[*] host ns1.uberpeople.net (184.154.76.235)
[*] host ns2.uberpeople.net (184.154.76.235)
[*] host uberpeople.net (184.154.76.235)
[*] host www.maybedmybreakfastfast.com (184.154.76.235)
[*] host www.maybedmybreakfast.uberpeople.net (184.154.76.235)
[*] host www.motokoband.uberpeople.net (184.154.76.235)
[*] host www.uberpeople.net (184.154.76.235)
```

```
185.169.124
```

[*] host hostxcrypt.com (185.169.124)

SUMMARY

+   [*] 13 total (2 new) hosts found.

This was a great find—12 new hosts found!