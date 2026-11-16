

## Calculating Monthly Transfer

Another option available to you is a monthly transfer limit, an “all you can eat” of the ISP’s bandwidth within that limit. Depending on the type of site involved, this may work out to be less expensive. For example, if you have a huge surge of users at 6:00 P.M., but a lot of dead time elsewhere, this option could be appropriate for you.

To calculate your monthly transfer requirement, simply multiply the number of monthly user sessions you expect to receive by the amount of data each will transfer.

For example, if a typical session consists of 10 requests, and each request has an average page weight of 50 KB, each user session will consume about a half-megabyte of transfer. If 5,000 regular users each use the system once a day, this represents 5,000 sessions per day, or 2.5 GB of transfer. During a month, this works out to 75 GB.

## Rack Space Considerations

How much rack space you require is obviously determined by the number of servers you’ll be using. Keep in mind, though, that any network appliances (such as switches and routers) also take up space.

In planning for future expansion, you may wish to allow a certain amount of free rack space beyond your immediate requirements. If you buy only five units in a shared rack, for example, it is almost inevitable that space on either side of you will be sold by your ISP more or less right away, and that future equipment may have to be sited elsewhere as a result.

## Network Considerations

Hooking all this equipment up might seem to be the simple part, but a bit of planning in this department can save you grief and heartache later.

Consider the traffic going across each interface and try to plan around that. For example, a database-heavy Web application will have enormous amounts of traffic going to and from the database server, traffic that is completely unrelated to the Web request being made by the client Web browser. With this in mind, you should consider having a separate interface on each Web server linking into the database server.

Such a configuration is common. You have a core switch into which all your Web servers link, and into which your firewall’s internal interface will link, too. Your database switch is linked to the secondary NIC of each Web server, and to the NIC of each database server you use.

As a result, traffic between Web servers and database servers doesn’t interfere with true Web traffic — a performance increase. If you are using a high-end switch, you can even use a virtual local area network (VLAN) to separate, say, 24 ports into two virtual switches of 12 ports each — one for the Web servers and firewall, as well as one for the database servers and secondary Web server NICs.

A side-effect of this configuration is yet another layer of protection for your databases. With no exposed interface to the Internet, they are yet another step away from being compromised.

## Storage Considerations

With a large application requiring the storage of large amounts of data, the onboard hard disks in a rack-mountable server may be insufficient. Storage area networks (SANs) are frequently available from the better-managed hosting providers, and often allow for a nearly limitless (and expandable) amount of hard disk space, which is ideal for storage-intensive applications that must quickly scale.

Other storage solutions include drive enclosures, which in their more sophisticated forms enable multiple servers to connect to the same drive array. There are also Web-services-based solutions (such as Amazon’s S3) that use a third party to store data and provide an API for upload and retrieval.

## Managing Maintenance

Managed hosting providers will perform basic maintenance on your servers (including kernel patches, software installation, and updates), and provide support with general systems administration. Whether you opt for this solution or decide to take care of these tasks yourself depends on both you and your relationship with your client.

If you do decide to bear the burden, then you should devise a weekly action plan for server maintenance. This should be a list of tasks to perform weekly to ensure that your servers are clean, efficient, and up-to-date. Tasks for your action plan should include the following:

- [ ] Kernel version — Is each server running the latest version?
- [ ] Apache and PHP versions — Is each server running the latest version?
- [ ] PHP dependencies — Are libxml2, libxslt, and expat all up-to-date?
- [ ] Disk space — Does each server have enough space on each partition? Are any log files growing out of control and in need of trimming? Apache, in particular, will not allow you to exceed 2 GB in size for any given log file, and will crash quite spectacularly if you do.

## Summary

In this chapter, you learned about the importance of a robust systems architecture for your application. With a definition of systems architecture in hand, you then learned about the right questions to ask your client to determine, in plain English, the exact system requirements.

Next, you learned how to take that information and translate it into justifiable technical decisions. This way, when your project goes live, you won’t encounter nasty surprises.

How you present this information is largely up to you. A three- or four-page guide for your client’s reference might be enough, or you may wish to incorporate it into your technical specification. The important thing is to do the planning immediately, well ahead of application development. Load testing later on will ensure that your theories are correct. It’s better to have slightly wrong predictions now than to have no predictions at all.

Following the project management methodologies and design patterns you have learned so far, Chapter 19 explores how you can use the toolkit components and your newfound knowledge to put together a sales force automation project.

## Building the Application

Now that you understand how the technology works, this is your chance to put it together as a cohesive whole. This chapter is about developing software from the ground up, and because it is a small project you’ll be utilizing many of the techniques of extreme programming (XP).

With all the fanfare and drama of starting on a new important project, it’s easy to mentally jump ahead and begin thinking about _how_ to do things when you should be trying your best to consider _what_ should be done.

Therefore, put your computer away. Forget about your logins, passwords, databases, and, just for now, you won’t need PHP either. Instead, you’ll be using a technology that humans have spent the last few millennia refining — paper.

Yes, paper is technology. It’s ubiquitous, inexpensive, readable even if wet, and requires no batteries (unless you’re in the dark). The same media type supports both write-only, rewriteable, and color and black-and-white inks. When paper is cut into small index-size cards, it can be used quite nicely for representing your PHP classes. Not only are these cards moveable, they can be mounted on a wall, traded, stapled, clipped, sorted, and stored.

In short, your design and development process depends just as much on social interaction, wits, and thousand-year-old technology as it does on computer hardware and software.

### Starting the Project: Monday

You arrive at work well rested and happy. Although the Widget World IT department is busily setting up your computer for your first day of work, fortunately, your office-supply closet contains what you need for today’s work:

- [ ] Pens
- [ ] 3 × 5 index cards
- [ ] 4 × 6 index cards

Bridget (the Widget World sales force automation tool manager) sits near you and is ready to work with you on your first day. Bridget mentions that because Edwina (the Widget World eastern regional sales manager) is in the office today, she has scheduled a meeting. Harold is a salesperson who happens to be working in the office because of conflicts; he will be available for the next two weeks. Wade (the Widget World accountant) is also there, and he is available for you 100 percent between 9:30 A.M. and lunchtime, every day (if needed).

Off to the meeting, and don't forget your cards.

### Getting an Earful

At the beginning of the meeting, after everyone has been introduced, you explain that you’re here to collect stories about what they would like from the new system, and how they’d like to use the new system.

Using your thousand-year-old technology of pen and paper, document the stories. Put each one on a separate card and insist that Wendy, Wade, and Edwina all partake in the fun. Of course, they may have questions about what is and is not technically possible, who must sign off on what, and how the workflow goes.

Keep in mind that each story (or feature) should be broken down so that each is about the same size. In the context of this exercise, size means the amount of effort that it would take for you to implement the story. This is probably the most difficult part as you (the developer) keep everything in perspective.

Determining the correct size for each story as a unit of time is not a trivial task. Try to keep the unit of time from around a minimum of half a day to a maximum of up to a week or two. Again, each story should be roughly the same size. The story size and time estimates will be used later to help you determine the amount of work you’re doing, and how to better estimate future tasks.

For example, if one of the features is “build a rocket ship,” break it down into smaller, more manageable chunks, such as “the escape pod should be launched within 10 seconds after the escape hatch is closed.”

Your nearly all-day session results in the following stories. Documenting the person who suggested it (or insisted on it) is not mandatory, but a method of doing so is displayed here to give you an idea of how the process is often worked out. Beginning with physical forms (see Figure 19-1) is often a good starting point because it fits with the current workflow and structure:

- [ ] Story 1 — Edwina: “We track the salesperson’s contacts using this faxable form, which is how we determine where to send them next depending on the feedback. Having access to this information in some sort of electronic format would be great.”
- [ ] Story 2 — Wade: “Collecting all the daily travel expenses and receipts of the salespeople is time-consuming and error-prone. We’d like to collect them on a weekly basis, subtotaled by date and category.”
- [ ] Story 3 — Harold: “Sometimes I need to explain a certain expense. For example, I put $30 under “postage” for a special FedEx delivery. I’d like a way to add comments at the bottom of the expense report.”
- [ ] Story 4 — Wade and Harold: “The expense report should subtotal the items in a manner similar to a spreadsheet.”
- [ ] Story 5 — Wade: “I’d like to be notified, with a summary, when an expense report is submitted.”
- [ ] Story 6 — Edwina: “I’d like to be notified, with a summary, when a contact report is submitted.”
- [ ] Story 7 — Harold: “I’d like each salesperson to receive the same notifications, just so they have the option of double-checking.”

