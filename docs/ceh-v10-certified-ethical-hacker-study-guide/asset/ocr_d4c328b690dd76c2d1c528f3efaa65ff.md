# FIGURE 4.18 Chrome developer tools

![](bbox=[0.203, 0.14, 0.803, 0.595])

Websites are complex creatures. The Chrome developer tools and Firebug are only capable of looking at a page at a time. You’d have to dig through every page, one at a time, to investigate them and their capabilities. You may find it easier to mirror the website so you could look at it offline. With it stored locally, you could look at the pages as many times as you would like without needing to issue repeated requests to the remote server. While the requests aren’t likely to raise any eyebrows and aren’t even likely to be noticed, you are leaving tracks behind. One tool you can use to mirror the website is HTTrack. In the following code, you can see the results of running HTTrack to mirror a website. The program will essentially perform a spider on the remote site, storing the results in the directory provided.

# Mirroring Sites with httrack

```
$ httrack

Welcome to HTTrack Website Copier (Offline Browser) 3.49-2
Copyright (C) 1998-2017 Xavier Roche and other contributors
```