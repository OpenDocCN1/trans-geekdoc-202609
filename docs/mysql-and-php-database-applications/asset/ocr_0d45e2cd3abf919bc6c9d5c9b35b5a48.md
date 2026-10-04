# Chapter 11: Content Management System

```
where s.story_id = m.story_id and
m.author_id = a.author_id and
a.author = 'Jay Greenspan' and
```

The next thing to be aware of is the relationship between the stories table and the story_versions table. As we already mentioned, versioning is very important to a content-management system. In this case, it means that you must have access to old versions of articles. The way this schema is set up, the most current version of an article is kept in the stories table. Additionally, every version of a story, including the most recent, is kept in the story_versions table.

Now on to the tables that define stages in the editorial process and the users who will have access to these stages: content_users, content_stages, and user_stage_map. Once again, a many-to-many relationship ensures that the application will track the users and stages and the intersections of the two easily. Want to find all the users who have the rights to make content publicly available? This

```
select c.user_id
from content_users c, user_stage_map m, content_stages s
where s.stage='Live' and
s.stage_id = m.stage_id and
m.user_id = c.user_id
```

This ensures some of the security needed in this application. If a user does not have a listing in the user_stage_map for a particular item, he will not be able to perform this task.

You might be wondering who has the rights to these privileges. Those people are listed in the content_admin table.

If you decide to use this application for your purposes, you may find that using these tables may be all the security you need. If your users access to the Unix box is enough. However, if your users are able to get the data in other ways—perhaps logging into the server and running the MySQL line client and running queries directly—you may need a bit more.

In such a case you want to grant users privileges to log into the database. So you have to give them usernames and passwords using the grant statement in Appendix D. Then no matter where the users are accessing the data they will only have access to the appropriate data.

Sounds right? Well, it would be great, but when you try to do this application runs into some of the limitations of MySQL, and working around these limitations makes for some weird situations.

As of writing of this book, MySQL is missing two things you could have great use of here. First is a feature known as Views. A is pretty easy concept to understand. When creating a view, an administrator defines a virtual table that may be a join of many tables and may only show some of the columns in