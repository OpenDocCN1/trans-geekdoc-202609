
Alternatively, if you wanted to create a dedicated template for a press release, for example, you could take a more specific approach:

```
<h1>[ :content_type:headline type='pr' ]</h1>
<p>by [ :content_type:byline type='pr' ]</p>
[ :content_type:body type='pr' ]
```

The third approach involves using an open-source or commercial template system, of which many are available. The most well known is probably Smarty, a fairly robust template engine that enables you to separate your XHTML from your PHP. Your Smarty templates end up having tokens in them that relate back to variables you set in your PHP. Consider the following example:

```
//this is your PHP
include('smarty.php');
$smarty = new Smarty;
$smarty->assign('nickname', 'myerman');
$smarty->assign('realname', 'Thomas Myer');
$smarty->assign('city', 'Austin, TX');
$smarty->display('user.tpl');

//and here is user.tpl

<html>
<head><title>User info for {$nickname|capitalize}</title></head>
<body>
<h1>User info for {$nickname|capitalize}</h1>
<p>Real name: {$realname}</p>
<p>City: {$city}</p>
</body>
</html>
```

Notice two things about this example. First and foremost, any assignment made on the PHP side is easily accessible in `{$varname}` format on the Smarty side, thus effectively simplifying this work for the front-end developer or designer who is usually terrified of back-end code. The second thing to notice is the opportunity to add operators to different variables — the `|capitalize` on the end of `$nickname` enables you to morph data for display as needed.

As with most things in a developer's life, discussions about template engines often descend into religious discussions. In no way are you limited to Smarty (some developers hate it, others love it), so pick the system that best suits your needs as a developer, the needs of the site designers, and the needs of the site's visitors.

## Summary

In this chapter, you learned a little bit about content management systems (CMSs). You learned what a content management system is, got a little history lesson, reviewed four exemplars of PHP-based systems, and even got an overview of requirements, just in case you want to build your own.

Chapter 23 provides some tips on handling high traffic and high availability.

## Handling High Traffic and High Availability

Chapter 22 introduced you to a few PHP-based content management systems (CMSs), platforms that you may well try to incorporate in a large-scale or enterprise-grade Web application. All such CMSs were particularly well-suited to larger or higher traffic sites, where the burden of manual updates would be commercially impractical.

Yet, building large sites has technical as well as commercial implications. Larger sites have two key burdens not found when developing smaller projects: ensuring high availability (that is, a high percentage of uptime when measured over a given period) and the ability to handle exceptionally high levels of traffic without suffering adversely. The insurance techniques involved are often alien to smaller sites, and yet they are surprisingly simple to achieve, especially given that they are not necessarily PHP-specific.

In this chapter, you'll learn about those specialist techniques and how to incorporate them in the architecture of your own applications. In so doing, you'll prove to yourself once and for all that PHP is perfectly suited to such large sites. In addition, you'll sneak a look under the hood at the architecture of some of the Web's highest-traffic commercial sites, including Flickr and Facebook — both proudly built in PHP.

### Understanding the Terms

The terms *high traffic* and *high availability* mean different things to different people. Before going any further, it's worth cementing your understanding of what enterprise architects generally consider them to mean.

#### High Availability

The word “availability” refers to the normal function and operation of an application within acceptable parameters. If the application is broadly usable (even if running a little slower than normal), then it is considered to be available. Availability is generally measured as the percentage of a given period during which the application is available.

There’s a fascinating list of the downtime of the top 20 Web sites in 2007 at http://royal.pingdom.com/?p=116. The only site that manages 100.0 percent over the year is Yahoo!; Google manages an impressive 99.995 percent, and even the ColdFusion-built MySpace manages 99.98 percent. Averaging the top 20 gives an uptime figure of 99.987 percent over the year — that’s just six minutes of downtime every month.

Throughout this chapter, you’ll also see the word redundancy. In this context, redundancy means something very specific — that is, introducing into architectures the ability to cope with unexpected failures by providing failover onto identical backup equipment. It’s largely through the use of redundancy that the top 20 sites achieve the seemingly very high levels of availability that they do, even under high traffic.

For the purposes of this chapter, high availability means an uptime of 99.75 percent over a year — perhaps below the expectations of the top 20, but well in excess of a typical PHP Web site.

#### High Traffic

The metrics used to define “high traffic” can vary a little. The likes of Google, Flickr, and MySpace receive literally tens of billions of page impressions per month. This is certainly “high traffic,” but what about the Web site of a large corporation? While not B2C applications, sites such as unilever.com and deloitte.com still receive millions of page impressions per month. That’s nothing compared to the big social networking Web sites, and yet still within the realms of what many Web developers would consider “high traffic.”

In practice, though, it’s all about perception and positioning. Consider a fast, mainstream, compact automobile such as the MazdaSpeed3. Many would consider it a fast car; the name, the looks, the branding — all point toward an emphasis on performance. And indeed, it’s no slouch: 0–60 mph in 5.9 seconds. But compare that to a Bugatti Veyron, which reaches the same speed in well under half the same period of time, or a Formula One car, which can easily reach 140 mph in the same amount of time it takes the Mazda to get to 60.

The point is that all three would be considered fast by a layperson. The numbers back this up. The average 0–60 mph time of all cars on the market today is about 13 seconds. Being very black and white about it, you could argue, therefore, that anything under 13 seconds is “fast,” and anything above 13 seconds is “slow.”

Applying the same rules to the Web, the average number of page impressions received on viable Web sites (discounting closed sites, link farms, scams, and so forth) is around 100,000 per month — just 3,000 per day. That figure is low because of the sheer ubiquity of the Web. For every commercial Web-based operation enjoying millions of hits, there are a thousand more enjoying just a few hundred, if that. It’s not exactly what mathematicians would call a normal distribution.

Another way to look at it is to say that any site for whose level of traffic is likely to require special attention to hardware, software, or network architecture could well be considered “high traffic.” A site receiving 150,000 page impressions per month can easily be run from a single standard-spec server, probably using a fairly mediocre connection to the Internet. Conversely, it’s at around about the 1-million-page-impression-per-month mark that special considerations must be made for the hardware the site is running, the connectivity it has to the Internet, and the manner in which the underlying code is built.

Let’s use that as a meter in this chapter, then. Any site exceeding 1 million page impressions per month will be considered a *high traffic* site.

#### Platforms

You should now understand what this chapter will represent as a site enjoying high traffic and requiring high availability. Indeed, the two are usually inextricably linked. A high-traffic site is generally (although not always) a commercial success for its financial backers, a success that is contingent on an ongoing basis for that site’s high availability. Google site revenues for Q1 2008 were $3.40 billion — that’s $26,000 per minute. You can see the impact downtime could easily have on Google’s bottom line.

Worse still, high availability is usually more difficult to achieve under high-traffic situations. The relentless pounding of equipment under en masse HTTP requests quickly thickens any latent fault lines.

Before considering some of the specific factors affecting availability under high traffic, it’s worth briefly identifying and exploring the puzzle pieces that comprise an application’s *platform*. As you’ll see, it’s about far more than just the choice of development language. Many of these components can play a role in frustrating your goal of high availability.

#### Exterior Network

Any Web site or application accessible over the Internet must, by definition, enjoy some form of connectivity to the outside world. In practice, only company intranets tend to fall outside this obvious and apparent requirement. The *exterior network* refers to the trail of connections between the end user and the internal network — usually from the user’s computer right through to the terminating router at the equipment hosting the Web site.

In general, enterprise-grade applications tend to be hosted on either *co-located* or *managed* servers. In a co-located server scenario, the individual, company, or organization behind the site being hosted provides and manages the server, and the Internet Service Provider (ISP) provides the space where it may be placed. In the managed server environment, the ISP provides and manages the server, and the entity behind the site simply uploads its application.

In either case, however, the ISP is responsible for providing suitable connectivity to that server. It should be *high bandwidth* — in other words, a total bandwidth in megabits per second (Mbps) sufficient to accommodate incoming traffic. It’s worth keeping in mind that a 10 Mbps connection may sound like a lot, but that’s only enough to support five concurrent 2-Mbps end-user connections. Mercifully, the intermittent nature of HTTP means that five concurrent connections doesn’t equate to anything like five concurrent users; it’s more like a hundred. You’ll meet the math behind these assumptions later in this chapter.
