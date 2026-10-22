To be clear, code reviews are often very political and can reflect the power dynamics that exist in the project or workplace. You have to work very hard to make them not end up that way! Remember, you are supposed to be reviewing the ideas and implementation, not using it as an opportunity to pump up your own ego or tear down a coworker with whom you might have personal issues with.

# Consistency in Development Environments

In my 20+ years of software development, I've used all sorts of different development environments:

+   - Shared server used by the entire development team
+   - Virtual servers maintained by the systems department
+   - PCs on our desk configured to simulate production using FreeBSD jails^[1]
+   - Virtual machines using Vagrant^[2]
+   - Whatever I wanted to install on my own laptop

Obviously, not all of these environments are optimal. Sometimes you have no choice–the decision is made by someone over whom you have no control. But it is obvious not having everyone use the same development environment is a sure way to end up with weird bugs.

Test-centric cultures focus on repeatable processes, and having an easy-to-recreate development environment for people to work in is something definitely worth the time investment. Why? You're trying to eliminate, “It works on my machine,” from the list of reasons why stuff isn't working.

The key here is to make sure everyone is using the same building blocks.

# Automation Is Your Friend

One of the other concepts I spend a lot of time promoting is the idea of using automation to help you accomplish tasks more quickly. If I find myself doing something manually more than a handful of times, it's a sign this is a task that can definitely benefit from automation.

In an era where we have tools like Vagrant and Docker at our disposal, allowing us to create environments for our code to run in, why do you want to rely on humans to do repetitive tasks? Computers are great at doing what we tell them, over and over again. It just makes sense to script as much as you can.

[1] FreeBSD jails: https://en.wikipedia.org/wiki/FreeBSD_jail
[2] Vagrant: https://vagrantup.com