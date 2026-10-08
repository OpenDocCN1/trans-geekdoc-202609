
for example Red Hat or Canonical for Linux or Microsoft. For operating systems that are more community driven such as FreeBSD or Gentoo, you typically go to the website representing their organized communities and see what latest security fixes they are recommending.

Like all updates, you should have a staging environment in which you can test the application of these patches and verify their successful installation before performing the operation on production servers. This lets you verify that nothing has broken in your application before the problem gets to your live servers.

Being smart with the operating system and security fixes is definitely worth your while: If there is a security fix in the FireWire subsystem of a particular operating system, and your server has no FireWire hardware anywhere, it is probably a waste of time to go through the whole deployment process for that.

# Run Only What Is Necessary

One of the problems many physical servers have that they come with large amounts of software running, such as mail servers, FTP servers, the capability to work with Microsoft file shares (via the SMB protocol), and others. To run our web applications, we need the web server software (such as Apache HTTP Server), PHP and any related libraries, the database server software, and not much more.

If you are not using any of those other pieces of software, shut them off and disable them for good. That way, you do not have to worry about them being safe. If in doubt, do research—it is highly likely that somebody on the Internet has already asked (and received an answer) to what a particular service does and whether it is necessary.

# Physically Secure the Server

We mentioned previously that one of our security threats is somebody coming into our building, unplugging the server computer, and simply walking off with it. This is tricky, not a joke. With the average server not being a terribly cheap piece of hardware, the motives for stealing servers are not limited to corporate espionage and intellectual theft. Some people might just want to steal the computer for resale.

Thus, it is critical that servers used to run your web applications are kept in a secure environment, with only authorized people given access to it and specific processes in place for granting and revoking access to defence people.

# Disaster Planning

If you ever want to see a truly blank look, ask your average IT manager what would happen to their servers, or indeed their entire data center, in the building in which it was burned down or was instantly destroyed in a massive earthquake. An alarming percentage of them will have no answer at all.

# Disaster Planning 363

If a website or service is hosted in the cloud, this problem may present as having the application running entirely in a single region. On the database side, it often looks like a failure to run backups.

Disaster (recovery) planning is a critical and frequently overlooked part of running a service, whether it is a web application or anything else (including the day-to-day operations of your business). it is a wholly collection of documents or procedures that have been rehearsed for dealing with the questions that arise when one of the following happens (among):

- Parts of our entire data center is destroyed in some catastrophic event, such as an earthquake
- Our development team goes out for lunch and all are hit by a bus and seriously injured (or killed).
- Our corporate headquarters burns down.
- A network attacker or disgruntled (merely incompetent) employee manages to destroy all the data on the servers for our web applications.

Although many people do not even talk about disasters and attacks for various reasons, the hard reality is that such things do occur—fortunately, not rarely. Businesses, however, cannot afford the downtime that an event of such magnitude would cause if they were completely unprepared. A business that does millions of dollars in a day would be devastated if its web applications were shut down for over a week while people not 100% familiar with the setup worked to get the systems up and running again.

By preparing for these events, anticipating them with clear plans of action, and by rehearsing some of the more critical portions of these, a little financial investment up front can save the business from potentially disastrous losses later when a real problem does strike.

Some of the things we might need to do with disaster planning and recover the following:

- Make sure that all data is backed up and stored off-site or in another region, so that if our data center is destroyed, we still have the data elsewhere.
- Have documentation, off-site, on how to re-create the server environments and set up the web application. Rehearse this re-creation at least once.
- Have a full copy of all source code necessary for our web application, also in multiple locations. This might be an external source code repository stored on GitHub or similar, as well as in the production environment.
- For larger teams, prohibit all members of the team from traveling in one vehicle, such as a car or airplane, so that if there is an accident, we will be affected less. This is actually required by some business insurance policies.
- Have automated tools running to make sure that server operation is normal, and have an on-call roster so you know who will be responsible for solving problems outside business hours.
- Make arrangements with a hardware provider to have new hardware immediately available in the case that your data center is destroyed, or keep spares on hand. It would be most frustrating to have to wait 4 to 6 weeks for new servers.

# Next

In Chapter 16, "Implementing Authentication Methods with PHP,” we move beyond security to take a closer look at authentication—allowing users to prove their identity. We look at a few different methods, including using PHP and MySQL to authenticate site visitors.

# Implementing Authentication Methods with PHP

In this chapter, we discuss how to implement various PHP and MySQL techniques for authenticating users.

Key topics covered in this chapter include

- Identifying visitors
- Implementing access control
- Using basic authentication
- Using basic authentication in PHP
- Using Apache’s .htaccess basic authentication

## Identifying Visitors

The web is a fairly anonymous medium, but it is often useful to know who is visiting your site. With a little work, servers can find out quite a lot about the computers and networks that connect to them, however. A web browser usually identifies itself, telling the server what browser, version, and operating system a user is running. You can often determine what resolution and color depth visitors’ screens are set to and how large their web browser windows are by using JavaScript.

Each computer connected to the Internet has a unique IP address. From a visitor’s IP, you might be able to deduce a little about him or her. You can find out who owns an IP and make a reasonable guess as to a visitor’s geographic location. Some addresses are more useful others. Generally, people with permanent Internet connections have permanent IP address. Customers dialing into an ISP usually get only the temporary use of one of the ISP's addresses. The next time you see that address, it might be used by a different computer, and the next time you see that visitor, he or she will likely be using a different IP address. Mobile devices add another level of complexity. The key is that IP addresses are not useful for identifying people as they might seem at glance.

Fortunately for web users, none of the information that their browsers give identifies them personally. If you want to know a visitor's name or other details, you will have to ask him or her.

Many websites provide compelling reasons to get users to provide their details. More and more websites provide content for free, but only to people willing to register and log in. Most e-commerce sites record their customers' details when they make their first order. This means that a customer is not required to type his or her details every time.

Having asked for received information from your visitor, you need a way to associate the information with the same user the next time he or she visits. If you are willing to make the assumption that only one person visits your site from a particular account on a particular machine and that each visitor uses only one machine, you could store a cookie on the user's machine to identify the user.

This arrangement is certainly not true for all users. Many people share a computer, and many people use more than one computer or mobile device. At least some of the time, you need to ask a visitor who he or she is. In addition to asking a user is, you also need to ask the user to provide some proof of that he or she is who the user claims to be.

Asking a user to prove his or her identity is called authentication. The most common method of authentication used on websites is asking visitors to provide a unique login name and a password. Authentication is usually used to allow or deny access to particular pages or resources, which can be optional, or for other purposes such as personalization.

# Implementing Access Control

Simple access is not difficult to implement. The code in Listing 16.1 delivers one of three possible outputs. If the file is loaded without parameters, it will display an HTML form requesting a username and password. This type of form is shown in Figure 16.1.

Listing 16.1 secret.php—PHP and HTML to Provide a Simple Authentication Mechanism

```
<!DOCTYPE html>
<html>
<head>
<title>Secret Page</title>
</head>
<body>
```
