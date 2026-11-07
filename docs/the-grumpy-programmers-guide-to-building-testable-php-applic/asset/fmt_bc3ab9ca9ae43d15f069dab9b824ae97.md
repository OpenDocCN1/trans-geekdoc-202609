
# Testing Reflections

See, I’m having problems deciding WHAT to test. Let’s take a look at one project for example. We have a [self-hosted web service](http://www.sportsdb.org/sd/sportscaster) that we released under the GPL that we not only use ourselves for some clients but also use it to troubleshoot things as well. In terms of writing tests, I believe the best way to approach this is to write tests that speak directly to the `Sportscaster` “engine” using a known set of parameters and ensure that the output we get back matches what we expect. Is unit testing overkill for this? Very hard to say because we have an HTML front end that talks to a “gateway” that talks to an “engine”. I’m not the one who architected this, but I do have to make sure that it works properly. In this case I believe that “your tests should verify your application is outputting what you expect it to” is the best approach. Comments about this are totally welcome.

For another project, I tried something that [integrated Selenium with PHPUnit](http://sebastian-bergmann.de/archives/631-Integrating-PHPUnit-with-Selenium.html), but it was so slow as to be totally useless. [Sportso](http://www.sportso.com) is a very visual application, one that is written in PHP and talks to an [XML database](http://exist.sourceforge.net), but presentation is really the key here. We need to make sure that we’re placing the right data into our XML documents but that part of the application is solid. In this case, I wish to have tests that simulate a user clicking around the application and using it. Then I can compare output again and make sure that things are showing up when and where I expect them to. I’m thinking the `PHPUnit-Selenium` bridge is a bad idea, and that I should instead just focus on `Selenium`. Again, comments on how to best approach this are also welcome. I cannot believe that `Selenium` is really this slow, so there must be something I am doing wrong.

Also, I’ve thought about continuous integration. This [incredibly inspiring post about continuous deployment](http://timothyfitz.wordpress.com/2009/02/10/continuous-deployment-at-imvu-doing-the-impossible-fifty-times-a-day/) has me really thinking hard about how my changes actually get pushed up out of dev to production. We don’t have the resources to use a cluster of machines that IMVU appears to have, but when you think of the infrastructure and (more importantly) the practices in place, you just have to be in awe of it all. Just the *scale* of it is inspiring. If they can do this, I can certainly implement a very effective subset of this. There is really no reason other than laziness on my part to not do it. Harsh reality, to be sure.

But the real problem is the political game that you inevitably end up fighting over bringing in what is usually a very radical concept: a commitment to testing as part of the development process. Especially when the developers are severely outnumbered. A lot of people seem to have a pathological fear of automated testing, saying things like “we can just quickly test it by hand”. Then when you see the errors being reported by users of your products, you can’t help but wonder “could we have caught this earlier?” Unless it’s a very obscure error involving a race condition or something, of course the answer is YES.

I read a post from one of the main developers at justin.tv talking about why he felt [unit testing is useless](http://abstractstuff.livejournal.com/60388.html). While he is entitled to his opinion I can’t help but think that he really is doing `TDD`, but he just refuses to acknowledge it. Yes, ultimately, your users are the only ones who can tell you if your application is spitting out errors. But if you aren’t doing any rigorous testing of stuff BEFORE your users see it, I think you are taking chances with your business. My company is small (just 7 of us) so I’m so close to most aspects of the business I can really see the impact of certain decisions on the bottom line of the company. It’s not about finding bugs, which is what the justin.tv folks claim never happens with unit testing. It’s about making sure those bugs never happen in the first place.

I have to say that I’ve never really delved into the world of post-deployment monitoring, so maybe I should start asking a few more questions of people who deal with that sort of thing. Again, the key is to make it automated and have it report when it finds things that are wrong. We have a very good [nagios](http://en.wikipedia.org/wiki/Nagios) infrastructure at work that alerts us to problems with not only servers being down, but stale and/or missing data for our customers. I guess the next logical step is figuring out ways to look at that mountain of server logs and making sense of the errors? Definitely something to think about the next time I get stuck on some programming problem at work and need a change of pace.

I know I’ve been rambling a bit here, so let me pull some of this stuff back together to make it more cohesive:
*   `SSH` tunneling to access resources that you cannot easily put a snapshot of into your dev environment. I recommend read-only access if you can do it, because if you need to do updates or deletes you should always work off a local copy
*   `TDD` is a powerful yet still controversial tool that too many developers are still ignoring
*   Automation is the key to really taking advantage of what you gain by going with `TDD`
*   You need tools in place after deployment to see if your changes have had the desired effect

## 11 Continuous Integration Landscape For PHP Developers

*This content originally appeared on my blog in 2010 and has been updated due to some changes in the tools themselves. I hope you find the information here helpful.*

For those not familiar with the concept of [Continuous Integration](http://en.wikipedia.org/wiki/Continuous_integration), I can sum it up with one very glib phrase: it lets you break your code before you buy it. By this I mean, when combined with other programming practices like automated deployment and Test Driven Development, you get a chance to see if the code you’ve written *today* breaks anything you wrote *yesterday*.

If I were to design a Continuous Integration (hereafter referred to as `CI`) system, what would it look like? Setting aside the one I use already (details on that later), I believe there are some key features it requires:
*   Ability to integrate with your version control system
*   Web interface for cross-platform access to results of build
*   Ability to run your unit test suite and view the results
*   Ability to deploy code wherever you want
*   Ability to email results of test builds
*   Must be able to automate all of this for you

This is what I would call a non-trivial set of requirements.

It also illustrates what became the biggest realization for me: you cannot have `CI` without writing tests (whether they are unit tests or integration tests), and you cannot have `CI` without the process of creating a “build” being triggered without any further action by the developer. Without a commitment to writing meaningful tests it definitely won’t work. It is my firm feeling that there *is* such a thing as pointless tests, and to me getting to 100% code coverage is often more about programmer ego.

So, there are a few choices for PHP developers. You could use [`phpUnderControl`](http://phpundercontrol.org/), which is a plugin for [`CruiseControl`](http://cruisecontrol.sourceforge.net/), a Java-based tool. I took a look at it, saw all those XML configuration files and said “no thanks.” If you like screwing around with XML configuration files, then maybe this is the right tool for you. Me, I like my pointy-clicky interfaces. Or plain-text configuration files. Also targeted mostly at Java developers. My project was using PHP *and* Python, and needed to be able to support Java as well for a non-web project another developer was working on.
