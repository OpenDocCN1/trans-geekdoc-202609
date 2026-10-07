# Chapter 10 - Certificate Transparency and Internet Archives 217

Being able to index and historically catalog this data can be incredibly useful for future investigations. What if we wanted to search for more posts by this user? This happens to be a perfect example because the site is no longer online. Lucky for us, the site's posts were public and scraped by Wayback, which means we can grab them with Photon.

To run Photon's engine, use the --wayback switch. When running Photon, we can also change the depth of the scan. This is useful if we know the site has many nested folders, like:

```
python photon --wayback -d 10 -u bezlica.top
```

```
root@INTEL:~/opt/Photon: python photon.py --wayback -u bezlica.top -d 10
```

![](bbox=[0.195, 0.315, 0.62, 0.375])

+   - Fetching URLs from archive.org
+ Retrieved -1 URLs from archive.org
+ URLs retrieved from robots.txt: 1
- Level 1: 2 URLs
! Progress: 2/2
- Level 2: 3 URLs
! Progress: 3/3
- Crawling 4 JavaScript files
! Progress: 4/4

+   + Intel: 3
+ Robots: 1
+ Internal: 5
+ Scripts: 4
+ External: 3

+   - Total requests made: 9
! Total time taken: 0 minutes 52 seconds
! Requests per second: 0
+ Results saved in bezlica.top directory

# Archive.org Site Search URLs

Many scrapers tools require you to provide them with a hard list of URLs to scrape. Building a list of working URLs can prove to be a very big challenge, especially when you are talking about forums with millions of posts. As it turns out, you can use specially crafted cURLs to download lists of pages cached by nArchive.org.