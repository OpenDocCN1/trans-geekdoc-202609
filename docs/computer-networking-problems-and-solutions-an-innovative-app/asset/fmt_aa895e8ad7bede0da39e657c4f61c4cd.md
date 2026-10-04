
The right answer is to measure everything that will give you a good feel for the day-today operation of the network—with some caution. There may seem to be little harm in acquiring telemetry data from every device and every part of the network possible, and throwing the information away after a short period of time if it does not prove useful. The realistic answer, however, is you must choose your observation points carefully, after much trial and error, and after much thought about traffic flows, failure modes, etc.

There is a second point hidden in observe, however: how do you know what you’re observing unless you record? As the old saying goes, “if you didn’t write it down, it didn’t happen”—and nothing is truer than this in the world of observation. There’s no point in knowing what’s happening right now unless you know what has happened in the past.

## Orient

Once you’ve made a set of observations, you need to decide what it is you’re observing. Consider the simple optical illusion shown in [Figure 21-12](#ch21.xhtml#ch21fig12).

![Image](graphics/21fig12.jpg)

**Figure 21-12** *An observational illusion*

In [Figure 21-12](#ch21.xhtml#ch21fig12), there are two sets of squares, one of which is imposed on a background of geometric lines. On the right, the squares are actually square. On the left, however, the squares do not look square; they appear to be distorted. What you see is often determined by the context as much as what is there. Observing, therefore, is a *skill* you can develop over time. Observing a network to understand its normal state is like any other observational skill. How can engineers develop observation skills?

First, understand the operation of the network, protocols, and applications at a theoretical level. Reaching beyond the command line, and into the actual operation of the devices in the network—understanding how a router forwards packets, or how OSPF builds and processes packets, can make a huge difference in your ability to orient yourself to what you are observing.

Second, learning and applying models is a huge help. The reason you probably have trouble with the optical illusion in this figure is the boxes appear close to being squares, so you immediately think they must be squares. You have a “model of a square,” in your head, and when you see things close to the model, you try to make the object fit. So it is important to know a wide array of models into which any problem can fit—or, in the networking world, a wide array of models you can use to “see” protocol, application, device, and network operation. Each additional model you add to your “mental model set” allows you to orient yourself a bit faster.

This entire process is much like orienteering. First, get the map pointing north. Then, find the features on the map matching your location, and work from there to the destination, feature by feature. Not orienting the map is failing to separate the background from the information. Not being able to see the surrounding area is failing to collect the information necessary to match the map to the reality. Not knowing the symbols on the map is failing to have enough mental models to make the match between map and reality happen.

## Decide

The worst time to make any sort of decision is at 2 a.m., in the middle of a network outage, when you are under pressure to get the business back up and running. But given network outages never happen at a convenient time, how can you avoid making these kinds of decisions?

You can decide what you are going to decide before you must decide.

This might sound a little roundabout; perhaps an example from the world of self-defense training classes would be helpful. When is the best time to decide where you are going to go if someone attacks you? Before he does so, or while he is doing so? Defensive driving is no different: it is always best to know where you would go if the car in front of you suddenly spins out, or the wheels fall off, or some other thing you might not expect to happen.

This pre-decision process can be very helpful in a network environment. For instance:

• Where would you put a filter to block this particular type of traffic?
• Which parallel links would you remove to kill off the positive feedback loop keeping your routing protocol from converging?
• What servers can you shut down for a time while you are trying to figure out why the data center fabric has become so hot all of a sudden?

All of these decisions are choices you can make before the action starts—before you have to decide to do something. In other words, decide what you need to do so that when it comes time to do it, you will have a plan in place.

## Act

It should be easy to act once you have observed the situation, oriented yourself to what is happening, and considered the preplanned decisions you made before the 2 a.m. call that the network is down—but it often harder to act than it should be. Why?

First, it is often hard to believe “this is actually happening.” This is a common problem in self-defense situations; when you first encounter a problem, you do not want to adjust to the new situation. Rather, you would rather just ignore the problem and “move on with life.” This is Scrooge, in *A Christmas Carol*, saying to Marley, “there is more gravy than grave about you.” In the real world, however, this can be a very costly way to react.

Second, a storm of doubts will naturally accompany the actual moment of decision. Did you really observe this particular attack? What if you are wrong—will the consequences be worse than the attack itself?

The answer to both of these problems lies in the OODA loop itself. If you have staked out observation points, if you have oriented yourself against the background information you have, if you are following premade decisions made in more rational times, then acting is the right next step to take.

Hone your skills, know your network, know your monitoring points, know what you are looking at, know your plan, and do it. Make your plan, and then trust your plan.

### Final Thoughts on Security

Security is not simple; it is a broad field with a lot of potholes you can step in to, often without realizing you have, in fact, just stepped into a pothole. The castle walls of firewalls and demilitarized zones (DMZs) are in the distant past. Cannons have long since been invented, and the castle walls of the older world of network engineering are just testaments to a time long gone. Threat actors are everywhere, so defense must be everywhere, as well.

This chapter has not considered every possible defense, including such popular topics as microsegmentation and white listing, but it has described a set of helpful mental tools for understanding the world of network security.

### Further Reading

Bacher, Martin, Robert Raszuk, Susan Hares, Danny R. McPherson, and Christoph Loibl. “Dissemination of Flow Specification Rules.” Internet-Draft. Internet Engineering Task Force, February 2017. [https://datatracker.ietf.org/doc/html/draft-hr-idr-rfc5575bis-03](https://datatracker.ietf.org/doc/html/draft-hr-idr-rfc5575bis-03).

CNN and Mary Kay Mallonee. “Hackers Publish 20,000 FBI Employees’ Contact Information.” *CNN*. Accessed April 23, 2017. [http://www.cnn.com/2016/02/08/politics/hackers-fbi-employee-info/index.html](http://www.cnn.com/2016/02/08/politics/hackers-fbi-employee-info/index.html).

Czyz, J., M. Luckie, M. Allman, and M. Bailey. “Don’t Forget to Lock the Back Door! A Characterization of IPv6 Network Security Policy.” In *Network and Distributed Systems Security (NDSS)*, 2016. [https://www.caida.org/publications/papers/2016/dont\_forget\_lock/](https://www.caida.org/publications/papers/2016/dont_forget_lock/).
