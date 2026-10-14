
I don’t think this is the case any longer. There is a certainly a premium to using AWS, but it’s much cheaper than it used to be and the offering has become much better (`200GB+` memory, SSDs, provisioned IOPS). If I was starting up a new company, I would build it on AWS, hands down. Reserved Instances will get your monthly cost down to something that’s reminiscent of Dedicated Server Hosting (albeit still 10-20% more expensive), but being able to bring up a cluster of massive servers instantly or start up a test cluster in California in less than 5 minutes is powerful.

For a bigger, more established startup, I would maintain a fleet of dedicated servers at SoftLayer or Rackspace, and use EC2 for excess capacity, emergengies, and on-demand scaling. You can do this seemlessly with a little bit of network-fu and Amazon VPC. Sudden increase in traffic? Spin up some EC2 instances and handle the burst effortlessly. Using Amazon VPC, your EC2 instances can communicate with your bare-metal servers without being exposed to the public internet.

## DNS: Why you need to care

The first layer that we are going to unravel is DNS. DNS? What!? I thought this was a book on PHP? DNS is one of those things that we don’t really think about until it’s too late, because when it fails, it fails in the worst ways.

Don’t believe me? In 2009 Twitter’s DNS was hijacked and redirected users to a hacker’s website for an hour. That same year, SoftLayer’s DNS system was hit with a massive DDoS attack and took down their DNS servers for more than six-hours. As a big SoftLayer customer, we dealt with this firsthand because (at the time) we also used their DNS servers.

The problem with DNS downtime is that it provides the worst user experience possible—users receive a generic error, page timeouts, and have no way to contact you. It’s as if you don’t exist anymore, and most users won’t understand (or likely care) why.

As recently as September 2012, GoDaddy’s DNS servers were attacked and became unreachable for over 24-hours. The worst part? Their site was down too, so you couldn’t move your DNS servers until their website came back up (24-hours later).

Too many companies are using their domain registrar or hosting provider’s DNS configuration—that is WRONG! Want to know how many of the top 1000 sites use GoDaddy’s DNS? None of them.

#### So, should I run my own DNS server?

It’s certainly an option, but I don’t recommend it. Hosting DNS “the right way” involves having many geographically dispersed servers and an Anycast network. DDoS attacks on DNS are extremely easy to launch and if you half-ass it, your DNS servers will be the Achilles’ heel to your infrastructure. You could have the best NoSQL database in the world but it won’t matter if people can’t resolve your domain.

**Almost all of the largest websites use an external DNS provider**. That speaks volumes as far as I’m concerned—the easiest way to learn how to do something is to imitate those that are successful.

*   Reddit: [Akamai](http://www.akamai.com/html/solutions/enhanced_dns.html)

*   Twitter: [Dynect](http://dyn.com)

*   Amazon: [UltraDNS](http://ultradns.com) and Dynect

*   LinkedIn: UltraDNS

You should plan to pay for a well known, robust DNS SaaS. At Twitpic, we use [Dynect Managed DNS](http://dyn.com/dns/). It has paid for itself—we’ve had no downtime related to DNS outages since switching. Make sure you choose a DNS provider that has a presence close to your target audience, too, especially if you have a large international userbase.

Here’s what you should look for in a DNS provider:

*   Geographically dispersed servers

*   Anycast Network

*   Large IP Space (to handle network failures)

| ![question](images/leanpub_question.png) || 

#### What is Anycast?

Anycast is a networking technique that allows multiple routers to advertise the same IP prefix—it routes your clients to the “closest” and “best” servers for their location. Think of it as load balancing at the network level. |

| --- | --- |

In addition to the providers listed above, [Amazon Route53](http://aws.amazon.com/route53/) is a popular option that is incredibly cheap, offers a 100% SLA, and has a very user-friendly web interface. Since it’s pay-as-you-go, you can easily get started and adjust for exact usage needs as you grow.

![](images/route53.png)

### DNS Load Distribution

Besides scaling DNS, we can use DNS to help us scale, too. The HAProxy load balancer is integral to our scalable stack—but what happens when it loses network connection, becomes overloaded, or just plain crashes? Well it becomes a single point of failure, which equals downtime—it’s a question of when, not if it will happen.

Traditional DNS load balancing involves creating multiple A records for a single host and passing all of them back to the client, letting the client decide which IP address to use. It looks something like this.

```
 1 > dig A example.com       
 2 ; <<>> DiG 9.7.3-P3 <<>> A example.com
 3 
 4 ;; QUESTION SECTION:
 5 ;example.com.			IN	A
 6 
 7 ;; ANSWER SECTION:
 8 example.com.		287	IN	A	208.0.113.36
 9 example.com.		287	IN	A	208.0.113.34
10 example.com.		287	IN	A	208.0.113.38
11 example.com.		287	IN	A	208.0.113.37
12 example.com.		287	IN	A	208.0.113.35
```

There are a few drawbacks to this, however. First of all, less-intelligent DNS clients will always use the first IP address presented, no matter what. Some DNS providers (Dynect and Route53, for example) overcome this by using a round-robin approach whereby they change the order of the IPs returned everytime the record is requested, helping to distribute the load in a more linear fashion.

Another drawback is that round-robin won’t prevent against failure, it simply mitigates it. If one of your servers crashes, the unresponsive server’s IP is still in the DNS response. There are two solutions that work together to solve this.

1.  Use a smart DNS provider that can perform health checks. Dynect offers this feature and it’s possible to implement it yourself on Route53 using their API. If a load balancer stops responding or becomes unhealthy, it gets removed from the IP pool (and readded once it becomes healthy again).

2.  Even if you remove a server’s IP from the DNS pool, users that have the bad IP cached will still experience downtime until the record’s TTL expires. Anywhere from 60-300s is a recommended TTL value, which is acceptable, but nowhere near ideal. We’ll talk about how servers can “steal” IPs from unhealthy peers using `keepalived` in Chapter 4.

Dynect has a very intuitive interface for load balancing and performing health checks on your hosts:

![](images/dynect.png)

### DNS Resolution

The last, and very often overlooked, part of scaling DNS is internal domain resolution. An example of this is when a PHP application calls an external API and has to resolve the domain of the API host. Let’s say the application is using the Twitter API—every time you post something to Twitter, PHP has to look up and determine the IP of `api.twitter.com`.

PHP accomplishes this by using the libc system call `gethostbyname()`, which uses nameservers set in `/etc/resolv.conf` to look up the IP address. Usually this is going to be set to a public DNS resolver (like `8.8.8.8`) or a local resolver hosted by your datacenter.

So, what’s wrong with this setup? Well, two things:

1.  It’s another server that you don’t control. What happens when it’s down? Slow? They block you? The lowest timeout allowed in `/etc/resolv.conf` is one second (and the default is FIVE!), which is too slow for a high-volume website and can cause domino-effect failure at scale.

2.  Most Linux distributions don’t provide a DNS cache by default and that adds extra network latency to every single DNS lookup that your application has to make.
