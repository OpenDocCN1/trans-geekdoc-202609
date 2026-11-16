unroutable. As such, the burden on the firewall is usually slightly less than that of the perimeter router.
The firewall, too, will (in most circumstances) filter out large quantities of unwanted traffic, meaning
that the internal network switch needs to cope with slightly less traffic than the firewall. In a larger
architecture, two or more servers will doubtlessly be used to deliver content, so that individual traffic
burden on the network card will be lower still — although internal communication between servers (not
via the Internet) can easily push this up again.

A medium-tier router can generally shift about 10 Mbps without any problems. You’d be wise, therefore,
to seek out a firewall that can handle about the same amount of traffic. Your switches will almost
certainly be 100 Mbps, but you should consider whether internal communication between servers is
likely. If your database server and application server are separate, then this will be the case, and
providing 1 gigabit per second (Gbps) switching with 1 Gbps network interface cards (NICs) will
provide optimum performance.

# Hardware

Naturally, your application must run on something, and a typical arrangement for a high-availability /
high-traffic Web site will comprise, at a minimum, a separate Web / application server and database
server — that’s two physical boxes.

In the early days of the Web, sophisticated hardware from the likes of Silicon Graphics, Inc. (SGI) and
Sun Microsystems pervaded enterprise architectures across the globe. This wasn’t an area of much
interest for Intel, whose CPUs were chiefly aimed at the desktop environment. These days, however,
server-grade chips based on x86 architecture are readily available — and cheap. In fact, they’re so cheap
compared to their competitors in other architectures that in 99 percent of applications, it’s more cost
effective to go the Intel route, even if that involves using twice as many physical boxes.

There are two trends worth considering, however. Moore’s law indicates that processing power doubles
approximately every two years. As a result, an increasing number of enterprise architects are considering
the merits of virtualization. In such a configuration, one or more physical servers in a cluster provide one
or more virtual (or addressable) servers via software emulation.

The benefits are numerous. The ability to scale an application’s hardware base up and down as traffic
and load dictates is the most obvious benefit, without the normal cost and lead time associations. A
degree of redundancy is also provided by distributing load across multiple physical servers; a single
point of failure is eliminated.

A second trend (one championed chiefly by Google) is that of using commodity hardware (off-the-shelf,
nonspecialist boxes) to provide hosting. It may seem unusual, but consider the math. If 20 boxes costing
$500 each can provide the same level of redundancy and performance as 15 boxes costing $1,500 each,
it’s easy to see why the first option is more attractive. The main benefits of dedicated server hardware —
resilience, reliability, and longevity — are negated by sheer volume and economy of scale.

The use of virtualization to combine commodity servers into a single addressable environment provides,
in theory, the best of both worlds — although it is worth remembering that it is a relatively young
technology, and even in 2009 kinks are still being worked out.