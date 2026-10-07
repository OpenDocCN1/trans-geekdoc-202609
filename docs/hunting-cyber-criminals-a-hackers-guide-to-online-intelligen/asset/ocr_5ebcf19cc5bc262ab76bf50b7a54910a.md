# Chapter 14 » Publicly Accessible Data Storage 295

That means that anyone trying to access your Elasticsearch database via IP address on port 9200 will have full CRUD (create, read, update, delete) rights to your data simply by querying the URL. The way to protect your ES cluster is to put everything behind a firewall so that the IPs are not publicly exposed.

# Data Attribution

Discovering the owner of an exported data set is usually the most difficult part of the investigation because all you have to go on is an IP address, and a hosting company will never give up the owner of that address without a formal legal request.

While I typically contacted the organization long before I speak with anyone else, this was different. Trying to identify the owner of an IP address can be one of the most grueling and exhausting tasks you have undertake, so I enlisted a few people to help.

It took me a solid month to figure out who actually owned the Exactis data. After several weeks of not being able to find the owner, I reached out to law enforcement and reporters that could potentially help.

By the time we figured out that Exactis was the owner of the exposed servers, I had already been working with Andy Greenberg at Wired. When we finally figured it out, I contacted Exactis immediately and advised they take the data offline because it was completely wide open.

I explained that I had notified law enforcement because the data appeared to contain information on almost every U.S. citizen, and that I was working with Wired during my investigation. I strongly advised they speak with Andy to get their side of the story on record to help with the damage control.

What happened to Exactis following the publishing of the Wired story is something I could have predicted, and I still feel bad about it that day. The company went out of business and the owner, Steve Hardie, is currently facing severe class-action lawsuits. One night I received a text message from Steve asking why I ruined his life.

I'm not going to lie, that sucks I know there is truth in that. On the other hand, he is the CEO of a company that left all this data exposed. At some point, this was his responsibility. And frankly, given how many researchers look for open data storage, it was only a matter of time before someone would have found the data.

According to the most recent story by Wired, the CEO states that the data was only left open “for a matter of days.” I have a different perspective on this issue based on how long it took me to find the data.

Being said, my “word” means nothing. There will come a time in investigator’s career when it will be necessary to back up your words with