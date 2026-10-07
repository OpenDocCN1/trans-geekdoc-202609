# Chapter 14 = Public Accessible Data Storage 299

CSF is able to search through publicly accessible Amazon S3 buckets, Digital Ocean spaces, and SpiderOak shared folders. CloudStorageFinder is available at https://github.com/digininja/CloudStorageFinder.

CSF works by bruteforcing URLs, but the better your wordlist, the more results you will have. Refer back to Chapter 2 on methods to create great wordlists for bruteforce.

CSF has three key tools: bucket_finder.rb,_finder.rb, space_finder.rb, and spider_finder.rb. As you can probably imagine, bucket_finder.rb is used to look for Amazon S3 buckets, space_finder.rb is used for finding SpiderOak shared folders.

The options and parameters for all three programs are very similar, the main difference being the region parameters. In each case, public storage is located in different regions, so this parameter may change depending on the different services you are looking for.

The parameters of the CSF S3 bucket finder include:

```
--help -h: show help
--download, -d: download the files
--log-file, -l: filename to log output to
--region, -r: the region to use, options are:
  us - US Standard
  ie - Northern California
  si - Singapore
  to - Tokyo
---v: verbose

wordlist: the wordlist to use
```

# Amazon S3

Assuming you have your bruteforce wordlist ready to go, running CSF is pretty straightforward. For our initial scans, we will run bucket_finder against the U.S. region and download everything we come across using -d:

```
[root@ost] > ./bucket_finder.rb -us -d wordlist.txt -l logfile.txt
```

The output of our initial scan looked something like this:

```
Bucket ie redirects to: i3.amazaws.com
Bucket does not exist: endofspecialwords
Bucket does not exist: Aarhus
Bucket found but access denied: Aaron
Bucket does not exist: Ababa
Bucket found but access denied: aback
```