# 116 Part I | Network Exploration

```
-----
SUMMARY
-----
[*] 1 total (new) hosts found.
[*] 1 total (new) ports found.
```

Bingo! We've found a open port.
We even take this one step further and search for a range of IP addresses.
Unlike the previous Shodan module that searched for hosts against a single IP address, the shodan_net module will search for hosts against an entire block (i.e., a range of IP addresses).

Larger organizations typically own an entire block of IP addresses, so running this type of search is probably more useful if you are recon on an organization.

Another example of why it might be useful to search an entire block of IPs is to see what other domains may be hosted by the same ISP. For example, malicious ISPs will typically host more than one malicious site, so there is a good chance that a site hosting credit card numbers will be surrounded by other similar sites. Learning about these sites may provide additional context or clues to your investigation.

To do this, we use the shodan_net module, then set the source of the target netblock:

```
[recon-ng][default] > load recon/netblocks-hosts/shodan_net
[recon-ng][shodan_net] > set SOURCE 184.154.76.235/24
SOURCE => 184.154.76.235
[recon-ng][default][shodan_net] > run
```

As you can imagine, scanning the entire /24 netblock returned a lot of unrelated results. I would not recommend running this type of scan unless you have a good reason to. Remember, anything you discover will be automatically added to your Recon-NG database, so randomly scanning IPs will load you down with worthless results and increase future times!

# Summary

This chapter covered three major information reconnaissance and discovery tools: SpiderFoot, Intrigue.io, and Recon-NG. The tools are similar in nature, but each contains its own "secret sauce" for how it is able to build on previous results to automate the discovery and collection process. SpiderFoot and Intrigue are considered automated discovery tools, while Recon-NG is considered a manual discovery tool.