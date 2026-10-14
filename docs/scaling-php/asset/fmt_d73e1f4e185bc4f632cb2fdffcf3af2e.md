
`ip_local_port_range` defines the range of usable ports on your system. On my stock ubuntu installation, it’s set to `32768-61000`. Increase the range to allow for more connections. The number of available ports limits the number of simultaneous open connections. Remember, even after a connection is closed it still eats a port in the `TIME_WAIT` state (though we mitigate this with some settings below).

```
1 > sysctl -w net.ipv4.ip_local_port_range="10000 65535"
2 > vi /etc/sysctl.d/haproxy-tuning.conf
3     net.ipv4.ip_local_port_range=10000 65535
```

#### `net.ipv4.tcp_tw_reuse`

Part of the TCP protocol is the `TIME_WAIT` state, which keeps the socket open for up to 4 minutes after the connection has been closed. On a busy server, this can cause issues with running out of ports/sockets. The `net.ipv4.tcp_tw_reuse` tells the kernel that it’s okay to reuse TCP sockets when it’s safe to do so, without waiting for the full timeout to happen. Additionally, `net.ipv4.tcp_recycle` and `net.ipv4.tcp_fin_timeout` can all be tweaked, but you should be leary to mess with either of these.

```
1 > sysctl -w net.ipv4.tcp_tw_reuse=1
2 > sysctl -w net.ipv4.netfilter.ip_conntrack_tcp_timeout_time_wait=1
3 > vi /etc/sysctl.d/haproxy-tuning.conf
4     net.ipv4.tcp_tw_reuse=1
5     net.ipv4.netfilter.ip_conntrack_tcp_timeout_time_wait=1
```

#### `ulimit -n 999999`

On a stock linux configuration, the maximum number of open files allowed per process is set very low (1024). Since sockets are considered files on a linux system, this limits the number of concurrent connections as well. Remember, each connection through your load balancer requires TWO sockets, one for the inbound connection from the client and another for the outbound connection to the backend, so out the gate you’re limited to, at most, 512 concurrent connections. Luckily, it’s an easy setting to change.

```
1 > vi /etc/security/limits.conf
2     * soft  nofile  999999
3     * hard  nofile  999999
4 > ulimit -n 999999
```

Note: You may have to restart HAProxy for this setting to take effect.

### Issues at scale

Debugging load balancer issues can be frustrating, especially if you’re dealing with high load. Here are some issues to look for if you’re dealing with a slow or unresponsive load balancer.

#### Saturating the network

This seems like a no-brainer, but it’s happened to me before. I remember spending over an hour trying to figure out why one of our Twitpic load balancers was running like molasses and consistantly dropping connections. It ended up being that the network card was configurated at 100mbps and we were trying to push 150mbps through it. It’s easy to check, though. Using `vnstat` you can see the current bandwidth going through your network card. Remember to check your *public* AND *private* networks, since your load balancer will most likely be using both.

```
1 > vnstat -i eth1 -l
```

![](images/04----vnstat.png)

#### Running out of memory

Although unlikely with HAProxy, since the memory footprint is so low, it can happen if you have a high volume of incoming connections and slow/overwhelmed backends. Use `free` to check.

#### Lots of connections in `TIME_WAIT`

Like I talked about above, having lots of connections in the `TIME_WAIT` state can overwhelm your server. You can use the configuration options above to mitigate the issue—running `netstat -n | grep TIME_WAIT | wc -l ` allows you to see the number of sockets sitting in `TIME_WAIT`.

## App Server: Horizontal Scaling with Nginx and PHP-FPM

The application cluster is the brain of your app, responsible for running your PHP code and serving static assets like images, css and javascript. Luckily, app servers are usually the easiet part of the stack to scale, because with the load balancer setup mentioned in Chapter 3, new app servers can be added to the pool and horizontally scaled to increase capacity. And when they fail (because they will fail), HAProxy will automatically remove them from the pool. No alerts, and no waking up in the middle of the night—they scale effortlessly.

### Choosing the right version of PHP

The PHP community as a whole is really, really bad about updates. No joke, bad to the point of running releases that are years old. You need to make sure you’re running the latest version of PHP, which is PHP 5.4.4 (at the time of writing).

> Update for 2014— use PHP 5.5! Everything I say here holds true, except the Dotdeb repositories are `deb http://packages.dotdeb.org wheezy-php55 all` and `deb-src http://packages.dotdeb.org wheezy-php55 all`.

Major releases for PHP keep getting faster and more efficient with memory, so it’s important to run the latest release to squeeze the most out of your hardware. 5.4 is substanially better, both in terms of features and speed when compared to 5.3, and likewise when comparing 5.3 to 5.2. PHP is getting better with every major release.

On Debian or Ubuntu, you can use [Dotdeb](http://www.dotdeb.org/) to get almost immediate, hassle-free updates to PHP, as well as access to some other software that’s not kept up-to-date in the Ubuntu Repositories (Redis and nginx, for example). This saves you the hassle of having to wait for your distribution maintainers to update the packages, which often takes weeks, months or even an eternity in some cases.

If you’re using Ubuntu Quantal (12.10), PHP 5.4 is already in the apt repository so you don’t need to bother adding the php54 lines for Dotdeb.

Setting up Dotdeb is as easy as adding another apt source.

```
 1 > vi /etc/apt/sources.list.d/dotdeb.list
 2 
 3 deb http://packages.dotdeb.org squeeze all
 4 deb-src http://packages.dotdeb.org squeeze all
 5 
 6 # Only include these lines if you are using Ubuntu
 7 # 12.04.
 8 deb http://packages.dotdeb.org squeeze-php54 all
 9 deb-src http://packages.dotdeb.org squeeze-php54 all
10 
11 > wget http://www.dotdeb.org/dotdeb.gpg
12 > cat dotdeb.gpg | sudo apt-key add -
13 > apt-get update
```

#### Benchmarking PHP 5.3 vs PHP 5.4

In every scenario I could find and test, PHP 5.4 outperformed PHP 5.3 in requests per second, as well as memory usage. Here are some graphs with my findings that will hopefully convince you to upgrade to the latest version of PHP!

![](images/05----chart_1.png)![](images/05----chart_2.png)![](images/05----chart_3.png)

### Nginx and PHP-FPM

As discussed in Chapter 2, we’re going to swap out the typical Apache/mod\_php for a very elegant nginx/PHP-FPM configuration. Yeah, yeah—you can try to keep Apache and scale it horizontally with HAProxy, but using nginx and PHP-FPM is a much better combination. Trust me, throw out Apache and replace it with nginx.

We moved Twitpic over to using this setup in 2010, and I was admittedly hesitant at first. Apache was all I knew and it was so easy to manage. I was scared that I wouldn’t be able to learn nginx or be comfortable with managing it. Boy was I wrong! Nginx is even easier to manage than Apache—the configuration files are very clean and readable. Plus nginx has an [incredible wiki](http://wiki.nginx.org/Main) filled with full documentation on every configuration option.

Likewise, PHP-FPM is a solid piece of software and just as reliable as using mod\_php. Prior to PHP 5.3, it was a patch developed by the same team that created nginx, but now it’s bundled with PHP by default. What that means is that you have the full backing and support of the entire PHP community. It’s a well-tested piece of software and will definitely get the job done.

Let’s assume you have a PHP application in /u/apps/my_app, with the main entry point to the app at /u/apps/my_app/www/index.php. Most frameworks (Zend, Kohana, Cake) should be compatable with this recipe.

Here’s how we’d set it up:
