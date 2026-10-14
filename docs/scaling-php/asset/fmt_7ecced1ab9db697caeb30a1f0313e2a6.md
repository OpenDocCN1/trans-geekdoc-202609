
### Setting up a Test Environment

If you’ve already launched, it’s important that you do your benchmarking and load testing on separate servers from your production ones— we’re going to be breaking things, really pushing the limits of the app and it’s a bad idea to do that in production.

This is one area where I really recommend using pay-by-the-hour cloud hosting. With [Amazon EC2](http://aws.amazon.com), [Rackspace Cloud](http://rackspacecloud.com), [DigitalOcean](http://digitalocean.com), or [SoftLayer Cloud](http://softlayer.com) you can create an almost exact replica of your production servers for a couple of bucks. No hardware investment, no “test” servers that sit idle 99% of the time.

### The famous `ab` (Apache Benchmark)

The most common high-level benchmarking tool has got to be the `ab` tool that comes with Apache. It’s a pretty good tool, really great for just starting out because it’s so easy to use.

The basic idea behind `ab` is that it given a HTTP URL, a number of concurrent visits, and a number of total requests, it will make lots of requests for that page from your webserver(s).

Of course, requesting the same page over-and-over again hardly represents real-world traffic, but it’s a good starting point, especially if you can have it hit page that touches all parts of your stack. **Think of it as brute-force benchmarking**. Obviously, if you only use it to test static or non-database pages, you’re going to get unrealistic results.

| ![information](images/leanpub_information.png) || Watch out, if you’re using Mac OS X, the packaged version of `ab` is buggy- you’ll see the error `apr_socket_recv: Connection reset by peer (54)` 9 out of 10 times (but, it works sometimes, more often with lower levels of concurrency.) To fix the bug with `homebrew`:`brew install https://raw.github.com/Homebrew/homebrew-dupes/master/ab.rb`. |

| --- | --- |

Installing `ab` on Ubuntu is easy— `apt-get install apache2-utils`.

To get started, let’s run a really small test with 10 concurrent connections and 100 requests. The `-c` flag is for the amount of concurrency (number of simultaneous requests) and the `-n` flag is for total number of requests.

```
 1 > ab -c 10 -n 100 "http://192.51.100.100"
 2 
 3 This is ApacheBench, Version 2.3 <$Revision: 655654 $>
 4 Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
 5 Licensed to The Apache Software Foundation, http://www.apache.org/
 6 
 7 Benchmarking 127.0.0.1 (be patient).....done
 8 
 9 
10 Server Software:        WEBrick/1.3.1
11 Server Hostname:        127.0.0.1
12 Server Port:            9292
13 
14 Document Path:          /
15 Document Length:        16571 bytes
16 
17 Concurrency Level:      10
18 Time taken for tests:   4.768 seconds
19 Complete requests:      100
20 Failed requests:        70
21    (Connect: 0, Receive: 0, Length: 70, Exceptions: 0)
22 Write errors:           0
23 Keep-Alive requests:    100
24 Total transferred:      1678245 bytes
25 HTML transferred:       1657029 bytes
26 Requests per second:    20.97 [#/sec] (mean)
27 Time per request:       476.843 [ms] (mean)
28 Time per request:       47.684 [ms] (mean, across all concurrent requests)
29 Transfer rate:          343.70 [Kbytes/sec] received
30 
31 Connection Times (ms)
32               min  mean[+/-sd] median   max
33 Connect:        0   20  99.0      0     503
34 Processing:    87  422 156.2    416    1014
35 Waiting:       68  370 143.7    367     830
36 Total:         87  442 207.6    416    1517
37 
38 Percentage of the requests served within a certain time (ms)
39   50%    416
40   66%    491
41   75%    526
42   80%    555
43   90%    669
44   95%    747
45   98%   1106
46   99%   1517
47  100%   1517 (longest request)
```

Let’s dig into the important parts from the results:

```
1 `Requests per second:    20.97 [#/sec] (mean)`
2 `Time per request:       47.684 [ms] (mean, across all concurrent requests)`
3 `Transfer rate:          343.70 [Kbytes/sec] received`
```

We see above the requests per second, the mean time per request, and the transfer rate in Kbytes. These are good metrics to track and benchmark as you improve your stack and code— the more requests and lower mean time per request, the better.

| ![information](images/leanpub_information.png) || `ab` doesn’t have many settings besides `-c` and `-r`. One useful, but overlooked, setting is `-k` which turns on KeepAlive requests. I really like using this simultaneously while running another instance of `ab` without `-k` on. Why? Because it allows me to test the load balancer network settings discussed in Chapter 4— how many connections stay in `TIME_WAIT`, etc. |

| --- | --- |

### Siege, a more modern `ab`

I find apache benchmark to be kind of limiting and outdated. A great, modern alternative is `siege`. You can install it with `apt-get install siege` on Ubuntu. The command line flags are similar to `ab`, `-c` sets the number of concurrent users and `-t` sets the number of seconds to run the test for.

```
 1 siege -c50 -t10s http://127.0.0.1
 2 ** SIEGE 3.0.1
 3 ** Preparing 50 concurrent users for battle.
 4 The server is now under siege...
 5 Lifting the server siege...      done.
 6 
 7 Transactions:            992 hits
 8 Availability:            100.00 %
 9 Elapsed time:            9.56 secs
10 Data transferred:        0.36 MB
11 Response time:           0.00 secs
12 Transaction rate:        103.77 trans/sec
13 Throughput:              0.04 MB/sec
14 Concurrency:             0.06
15 Successful transactions: 992
16 Failed transactions:     0
17 Longest transaction:     0.01
18 Shortest transaction:    0.00
```

Easy! 50 concurrent connections in 10 seconds. I generally like the output and and format of `siege` better. You can clearly see the `Transaction rate` (number of requests per second) and other valuable metrics that you may want to track.

Another cool feature? It can hit multiple URLs in a single test to simulate real traffic. Make a file and put a bunch of URLs in it and `siege` will hit them all. It’s an easy way to simulate real world traffic.

```
1 $ vim urls.txt
2   http://127.0.0.1/index.php
3   http://127.0.0.1/search.php
4   http://127.0.0.1/contact.php
5 
6 $ siege -c50 -t10s -i -f urls.txt
```

### Bees with machine guns

Sometimes you want a REALLY massive test and running a single `siege` process just won’t cut it. [Bees with machine guns](https://github.com/newsapps/beeswithmachineguns) will launch a mini EC2 cluster to hammer your server(s) with as many clients as you want! The install is slightly more complex:

```
 1 $ apt-get install python-dev python-pip
 2 $ pip install beeswithmachineguns
 3 
 4 $ export AWS_ACCESS_KEY_ID="YOUR AWS ACCESS KEY"
 5 $ export AWS_SECREY_ACCESS_KEY="YOUR AWS SECRET KEY"
 6 
 7 # You will need to put in your private SSH Key that you use for Amazon EC2
 8 # into this file. It must have the same name as your SSH Key uploaded to Amazo\
 9 n.
10 $ vim ~/.ssh/key_name.pem
```

Next, you’ll have to go into your EC2 management console and create a security group (if you don’t already have one) that allows SSH connections on port 22. I made one called `public`— it’s what you have to pass to the `-g` parameter below.

After configuring the security group, `bees` is ready to bring up your test cluster. I’m going to start an attack cluster of 4 instances. The default type of instance is the micro instance (`t1.micro`) which is very cheap ($0.020/hour). You can change the instance type with the `-t` flag.

```
 1 $ bees up -s 4 -g public -k key_name -z us-east-1b
 2   
 3   Connecting to the hive.
 4   Attempting to call up 4 bees.
 5   Waiting for bees to load their machine guns...
 6   Bee i-c941cfe8 is ready for the attack.
 7   Bee i-c841cfe9 is ready for the attack.
 8   Bee i-0b5ed02a is ready for the attack.
 9   Bee i-0a5ed02b is ready for the attack.
10   The swarm has assembled 4 bees.
```
