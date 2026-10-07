In order for the Harvester to kick off a scan, you must use the domain (-d), limit (-i), and source (-b) parameters. If you do not include all three parameters, you will see the following results:

```
[ root@os~ ] > ..//theHarvester.py -d apple.com
```

[* No IPs found.

[* No emails found.

[* No hosts found.

If you receive a message that says no IPs, emails, or hosts found, you most likely did not enter the parameters correctly.
The -d parameter is how you specify the domain or company name you want to search. The -l parameter is the limit on how many searches you want to perform against each engine. The -b parameter is how you specify the source engine for your search. This can include sites like Censys, crt.sh, Google, Bing, or Yahoo, to name a few. If you don't want to search to any specific engine, you must enter -b all.

> WARNING Keeping your search limit high will get you temporarily banned from Google or any of the other engines. The default search value is 500, which means theHarvester searching through the first 500 results. Google shows 10 results per page, which means theHarvester will quickly be looking 50 pages. That is certainly enough for Google (or any search engine) to detect you as a scraper and either throw up a Captcha or simply block your results. To avoid this, I recommend using a proxy service that will send every request through a different IP (e.g., Storm Proxies)