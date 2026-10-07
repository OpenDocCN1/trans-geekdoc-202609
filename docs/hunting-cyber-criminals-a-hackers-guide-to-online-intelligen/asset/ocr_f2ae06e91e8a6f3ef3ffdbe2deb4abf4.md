recon/domains-hosts/threatcrowd
recon/domains-vulnerabilities/ghbd
recon/locations-locations/geocode
recon/locations-locations/reverse_geocode
recon/locations-pushpins/flickr
recon/locations-pushpins/picasa
recon/locations-pushpins/shodan
recon/locations-pushpins/twitter
recon/locations-pushpins/youtube
recon/netblocks-blocks/whois_org
recon/netblocks-hosts/reverse_resolve
recon/netblocks-hosts/shodan_net
recon/netblocks-hosts/virustotal
recon/netblocks-ports/census_2012
recon/netblocks-ports/censysio
recon/ports-hosts/migrate_ports
recon/profiles-contacts/dev_liver
recon/profiles-contacts/github_users
recon/profiles-profiles/nameckh
recon/profiles-profiles/profiler
recon/profiles-profiles/twitter_mentioned
recon/profiles-repositories/github_repo
recon/repositories-profiles/github_commits
recon/repositories-vulnerabilities/gist_search
recon/repositories-vulnerabilities/github_dorks
reporting/csv

The number of available modules to choose from can be overwhelming,
special to a new user, let's start with a basic example of adding a few target
doms to Recon-NG using the add domains command:

```
[recon-ng] [OSINT] > add domains www.uberpeople.net
[recon-ng] [OSINT] > add domains www.dualxcrypt.com
```

After entries to your Recon-NG database, you can quickly see what
You have stored in your local database by typing show and pressing the Tab key:

```
[recon-ng] [OSINT] > show
banner dashboard options repositories
companies domains locations ports schema
contacts hosts modules profiles vulnerabilities
credentials keys netblocks pushpins workspaces
```

This will give you a list of every type of result you can “show.” Since we have
just added some domains, let's show them by typing show domains: