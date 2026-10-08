# Disaster Planning 363

If a website or service is hosted in the cloud, this problem may present as having the application running entirely in a single region. On the database side, it often looks like a failure to run backups.

Disaster (recovery) planning is a critical and frequently overlooked part of running a service, whether it is a web application or anything else (including the day-to-day operations of your business). its wholly collection of documents or procedures that have been rehearsed for dealing with the questions that arise when one of the following happens (among):

+   - Parts of our entire data center is destroyed in some catastrophic event, such as an earthquake
- Our development team goes out for lunch and all are hit by a bus and seriously injured (or killed).
- Our corporate headquarters burns down.
- A network attacker or disgrunted (merely incompetent) employee manages to destroy all the data on the servers for our web applications.

Although many people do not even talk about disasters and attacks for various reasons, the hard reality is that such things do occur—fortunately, not rarely. Businesses, however, cannot afford the downtime that an event of such magnitude would cause if they were completely unprepared. A business that does millions of dollars in a day would be devastated if its web applications were shut down for over a week while people not 100% familiar with the setup worked to get the systems up and running again.

By preparing for these events, anticipating them with clear plans of action, and by rehearsing some of the more critical portions of these, a little financial investment up front can save the business from potentially disastrous losses later when a real problem does strike.

Some of the things we might need to do with disaster planning and recover the following:

+   - Make sure that all data is backed up and stored off-site or in another region, so that if our data center is destroyed, we still have the data elsewhere.
- Have documentation, off-site, on how to re-create the server environments and set up the web application. Rehearse this re-creation at least once.
- Have a full copy of all source code necessary for our web application, also in multiple locations. This might be an external source code repository stored on GitHub or similar, as well as in the production environment.
- For larger teams, prohibit all members of the team from traveling in one vehicle, such as a car or airplane, so that if there is an accident, we will be affected less. This is actually required by some business insurance policies.