# Chapter 12: Threaded Discussion

# 315

![](bbox=[0.181, 0.098, 0.761, 0.452])

Figure 12-5: Form for posting a lower-level topic

# What do you need to prevent?

As you've seen in previous chapters, you need to spend a bit of time making sure things work properly. We've talked before about the cross-site scripting bug. You'll surely want to prevent that from happening here.
Unless every post is reviewed before it becomes available on the site, there is no good way of preventing users from posting nonsense and replying to them with other meaningless posts. This kind of thing can get pretty distracting—and again, there is no foolproof way of preventing it. You can make it a bit more obvious to other users that the nefarious poster is a jerk. For that reason, this application collects the IP of origin and displays it for every post. This isn't great protection, but it is better than nothing.

![](bbox=[0.181, 0.757, 0.233, 0.803])

As one of the reviewers of the book pointed out, all users behind the same firewall will have the same IP, and users who dial-up to an ISP will get a different IP every time. Furthermore, the reviewer felt that the IP address of someone who actually had a static IP was bad etiquette. After thinking about it, I tend to agree. However, we kept this code in the application. You could remove it from your code in a matter of seconds if you wish.