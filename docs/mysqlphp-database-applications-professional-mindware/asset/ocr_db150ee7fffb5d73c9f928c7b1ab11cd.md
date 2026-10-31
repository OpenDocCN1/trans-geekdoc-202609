![](bbox=[0.18, 0.1, 0.77, 0.46])

Figure 12-5: Form for posting a lower-level topic

# What do you need to prevent?

As you've seen in previous chapters, you need to spend quite a bit of time making sure things work properly. We've talked before about the cross-site scripting bug. You'll surely want to prevent that from happening here.

Unless every post is reviewed before it becomes available on the site, there is no good way of preventing users from posting nonsense and then replying to their own meaningless posts. This kind of thing can get pretty distracting—and again, there is no foolproof way of preventing it. However, you can make it a bit more obvious to other users that the nefarious poster is a jerk. For that reason, this application collects the IP of origin and displays it for every post. This isn't great protection, but it is better than nothing.

![](bbox=[0.18, 0.76, 0.26, 0.82])

> As one of the reviewers of the book pointed out, all users behind the same firewall will have the same IP, and users who dial-up through an ISP will get a different IP every time. Furthermore, the reviewer felt including the IP address of someone who actually had a static IP was bad etiquette. After thinking about it, I tend to agree. However, we kept this code in the application just to keep the example. You could remove it from your code in a matter of seconds if you wish.