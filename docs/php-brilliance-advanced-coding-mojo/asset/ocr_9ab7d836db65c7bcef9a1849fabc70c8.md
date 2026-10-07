# Talking Points

recover from a failed database connection attempt, the tightly coupled nature of this code imposes additional responsibilities on the development team to ensure that there are no adverse effects from code changes occurring now and in the future.

The very best way for a development team to avoid adverse effects of the changes that they make to a codebase is to employ tests. Lots and lots of tests.

Software testing can be done in a variety of different ways; functional testing, integration testings, regression testing and unit testing to make four. Each type of testing involves varying amounts of labour at various stages. Unit testing requires the most amount of labour at the setup stage; you write the code and you write the tests to go with it (the other way around if you're into *driven development*) but there's little, ideally no effort involved in running the test suites created.

At the end of the spectrum, functional testing requires little to effort at the code creation stage but disproportionately intensive on the code delivery stage, especially if the development team is working in concert with a QA team.

Engaging in iterative build cycles, such as those encouraged by agile methodologies and learn processes, means that we want most if not all of our testing to be automated. It would serve us all to engage in a two-week sprint only to have to devote one week of each sprint to testing and sign-off!

Clearly we want to save ourselves as much pain and anguish as possible whilst we go about delivering our code one story at a time. And that means scope of the right amount of automated testing at the most appropriate levels.

So which levels are the right ones? Fortunately, this problem has been solved for already. Mike Cohn, in his excellent book *Succeeding with Agile*, proposed the concept of the *Testing Pyramid*, which illustrates perfectly how we concentrate most of our efforts at the unit-level testing, proving the pyramid's broad base with the widest level of test coverage and proceeding to narrow the scope of each testing level until we reach the functional tip.

Unit testing. Lots of developers hate it, though mostly for unjustifiable reasons, the most common on is that it takes too much effort to do it properly. Another answer to that is that bug-fixing takes too much effort and you have no choice but to do it properly, mostly at the expense of spending time working on the new and exciting stuff or worse, sacrificing pub time for it. The horror!

> ¹⁹https://phpbrilliance.com/url/e3w