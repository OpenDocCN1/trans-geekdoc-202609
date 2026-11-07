
If you prefer the cool ideology of a `PHP`-powered solution, you could look at [`Xinc`](http://code.google.com/p/xinc/). Installs via `PEAR` (which is always a good idea), but drags a few other `PHP` components in with it. I dunno, doing it `PHP`-only held no special appeal to me.

Some organizations are also using [`Buildbot`](http://en.wikipedia.org/wiki/BuildBot) but search results are full of people discussing how difficult it is to use for more inexperienced programmers. It is written in `Python` so if you have the right skills you can modify it to bend it to your will.

In the end, I settled on [`Jenkins`](http://jenkins-ci.org). Much like `CruiseControl`, it’s `Java` based, but that was no big deal as we already have `Java` in our infrastructure at work with more little bits being moved to it. Also, `Jenkins` has the type of architecture I like: a small, tight core with lots of plugins to add the functionality I wanted. Using `Subversion`? Add the plugin. Need to run [`py.test`](http://codespeak.net/py/dist/test/) scripts? There’s a plugin for that. Want to be able to see the results of your `PHPUnit` tests? There’s a plugin for that.

So, not only that, but I could also write a `shell script` that is run when a build is triggered. In this case, I was using a `post-commit` trigger to start builds, but if I wanted to be dogmatic about it I would use a `pre-commit` trigger, and fail the `commit` attempt if the tests broke. I remember how the younger, angrier me flew into a rage at a previous employer when a `hook` was put into place in our `CVS` repository (yes, I’ve been around long enough to have actually used `CVS`) that ran a `syntax checker` on any code that got checked in. Predictably, something was broken because the version of `PHP` running on the `CVS` server was different from what we were using both in `development` and `production`, and a difference in extensions caused a problem. That is a story for another time.

I also find that using a `post-commit` hook allows me to look at the code in the `staging` environment to find bugs that are caused by subtle differences between the `development` environment and `staging`. Today, I fixed one bug by using the new ternary shortcut available in `PHP 5.3`. Learn something new every day, is my motto.

So, how does a build actually work? Here’s how I’ve set things up:

1. A developer commits code to the `trunk` of the `SVN` repository. We don’t currently use `branches`, so I’d have to tweak things if we did work in `branches` and then merged things into `trunk`.
2. `Jenkins` wakes up when it sees a `commit`, and checks the code out into a `workspace`.
3. `Jenkins` then runs a list of `shell script` commands to do a bunch of things: run my `Doctrine` migration scripts, run my `PHPUnit` tests, run my `py.test` tests, then copy the code into place on the `staging` server.
4. Create a bunch of `test` reports that can be viewed in `Jenkins` itself
5. Send out an `email` to our tech mailing list telling people that a build has been triggered along with the results

I have to say there is nothing that puts a smug feeling of satisfaction in my heart like seeing that a build was successful…and nothing that makes me curse quite as much as seeing that a build failed. But without those tests in place, then I would not find bugs that would’ve gone into production. Any bug making it into production is BAD, and although I often use gallows humour at work to try and deflect my internal anger at such a thing, it IS possible to do production pushes of new code that contain no errors.

As a follow-up to this idea, I now have a policy that whenever a bug does get found in `staging` or `production`, I write a `test` to recreate the bug, and then put code into place to fix it. I have found that this has the interesting effect of giving you a bunch of `unit` and `integration` tests (thank you for the ability to test the output of `controllers` in `Zend_Framework` `PHPUnit` tests) that cover `edge cases` found by real users. Besides, you can get really lost going deep into the “we need to create `fixtures` so I can test stuff that manipulates dynamically-generated content” rabbit hole. I saw a `test` today that could benefit from the use of `fixtures`, instead of simply assuming that `data` will always be there. Your mileage will vary, but you have to understand that slavish devotion to `testing` does you no good if you’re not accomplishing the goal of producing a working `application` that meets the goals of the people who are actually, you know, using it.

I hope this post helps you if you’re trying to decide whether or not to take the `CI` plunge. I have no regrets at the length of time it took me to get things to a happy place in terms of `Jenkins` configuration. The benefits of automated builds with the goal of protecting you from yourself more than outweighs a few afternoons of scratching your head and trying to figure out what is going on with `Jenkins` itself.

## 12 Infrastructure Debt

*This content was originally a blog post from November 2011 that got some traction and ended up on Hacker News. It is directly related to the concepts that go into buliding testable applications. Hope you enjoy it.*

You might have come across the term “`technical debt`”, used to describe the small mistakes that are made in your `code base` as the `application` grows and requirements change. You end up with a big tangled mess if you are not very careful about how you make those changes. If you’ve ever worked on an `application` where you were afraid to make changes for fear of breaking something, then you have run into `technical debt`.

It’s very easy to build up `technical debt`: you put a quick `hack` in because you feel like you are under pressure to get a task accomplished. It takes courage to push back and say “no, damnit, I need time to fix this particular problem correctly!”. I understand, and it’s okay. We can hug it out if it will make you feel better.

`Technical debt` can be dealt with via ruthless `refactoring` and wrapping your `application` in `tests` that poke and prod at the `edge cases` that your `application` deals with. But there is another type of debt you end up dealing with. One that is even more difficult to deal with and change. I call it `infrastructure debt`.

`Infrastructure debt` is debt that you build up because you have not been paying attention to the process of creating the `environments` your `application` will exist in and have not been paying attention to the process of how your `code` gets from `development` into `production`. In my opinion, `infrastructure debt` is much more difficult to “pay off” than `technical debt`. Why? It is often very difficult for people to understand that it even exists.

Before I go any further, if you are not using a `version control system` to keep track of changes to your `code`, then please stop reading and go and install one. Having versions of your files with extensions like `.1` and `.old` is the worst kind of `infrastructure debt` that you could possibly have. It’s the 2nd decade of the 21st century. `Version control` is an almost 40-years-old, well-understood concept. Nothing I suggest will work if you insist on acting like `version control` is of no use to you. Passing around `diff` patches is not `version control`, my friends. It’s denial. Don’t tell me just because people used to do it in the past that it’s okay now given all the available options. People used to think that the earth was flat once too.

Let’s start with an easy `infrastructure debt` to pay off: inconsistency in `development environments`. These days it is pretty easy for someone to create a `development environment` for their `language` of choice along with associated components like `databases`. The problem? That it’s pretty easy for someone to create the `development environment` of their choice.
