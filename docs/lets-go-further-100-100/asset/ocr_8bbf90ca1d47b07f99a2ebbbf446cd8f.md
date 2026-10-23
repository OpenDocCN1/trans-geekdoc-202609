![](bbox=[0.13, 0.09, 0.87, 0.48])

We only need **one droplet** right now, so you can leave that as the default.

You should also add a **hostname** for the droplet. Amongst other things, the hostname is used as the main identifier for the droplet in the Digital Ocean control panel, and it’s also what you’ll see when you SSH into the droplet later to administer it. So you should pick a name that is sensible and easy-to-recognize. I’m going to use the hostname `greenlight-production`, but feel free to use something different if you like.

Adding tags to your droplet is completely optional, but if you do a lot of work with Digital Ocean they can be a useful way to help filter and manage droplets. I’ll use the tags `greenlight` and `production` here.