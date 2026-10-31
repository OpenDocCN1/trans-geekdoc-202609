```
where s.story_id = m.story_id and
    m.author_id = a.author_id and
    a.author = 'Jay Greenspan'
```

The next thing to be aware of is the relationship between the stories table and the story_versions table. As we already mentioned, versioning is very important to a content-management system. In this case, it means that you must have access to old versions of articles. The way this schema is set up, the most current version of an article is always kept in the stories table. Additionally, every version of a story, including the most recent, is kept in the story_versions table.

Now on to the tables that define the stages in the editorial process and the users who will have access to those stages: content_users, content_stages, and user_stage_map. Once again, a many-to-many relationship ensures that the application will track the users and stages and the intersections of the two easily enough. Want to find all the users that have the rights to make content publicly available? This will work:

```
select c.user_id
from content_users c, user_stage_map m, content_stages s
where s.stage='Live' and
    s.stage_id = m.stage_id and
    m.user_id = c.user_id
```

This setup enforces some of the security needed in this application. If a user does not have a listing in the user_stage_map for a particular item, he will not be able to perform that task.

You might be wondering who has the rights to grant these privileges. Those people are listed in the content_admin table.

If you decide to tweak this application for your own purposes, you may find that using these tables may be all the security you need. If your users don't have access to the Unix box storing the database server, these tables should be enough. However, if your users are able to get at the data in others ways—perhaps by logging into the server and launching the MySQL command line client and running queries directly—you may need a bit more.

In a case such as this, you want to grant users privileges to log into the database. So you have to give them usernames and passwords using the grant statement discussed in Appendix D. Then no matter where the users are accessing the data from they will only have access to the appropriate data.

Sounds great, right? Well, it would be great, but when you try to do this your application runs into some of the limitations of MySQL, and working around these limitations makes for some weird solutions.

As of the writing of this book, MySQL is missing two things you could have made great use of here. First is a feature known as Views. A view is pretty easy concept to understand. When creating a view, an administrator defines a virtual table that may be a join of many tables and may only show some of the columns in