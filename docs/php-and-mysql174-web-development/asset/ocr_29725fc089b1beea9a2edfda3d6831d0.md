# Implementing Recommendations

This query uses aliases to join the database table bookmark—a strange but sometimes useful concept. Imagine that you actually have two bookmark tables, one called b1 and one called b2. In b1, you look at the current user and his bookmarks. In the other table, you look at the bookmarks of all the other users. You are looking for other users (b2.username) who have an URL the same as the current user (b1.bm_URL = b2.bm_URL) and are not the current user (b1.username != b2.username)

This query gives you a list of like-minded people to your current user. Armed with this list, you can search for their other bookmarks with the following query:

```
select bm_URL
from bookmark
where username in
    (select distinct(b2.username)
    from bookmark b1, bookmark b2
    where b1.username='$valid_user.'
    and b1.username != b2.username
    and b1.bm_URL = b2.bm_URL)
```

You add a second query to filter out the user's bookmarks; if the user already has a bookmark, there's no point in recommending it. Finally, you also filter with the $popularity variable. You don't want to recommend any URLs that are too personal, so you suggest only URLs that contain a number of other users in the list of like-minded users have book. The final query looks like this:

```
select bm_URL
from bookmark
where username in
    (select distinct(b2.username)
    from bookmark b1
    where b1.username='$valid_user.'
    and b1.username != b2.username
    and b1.bm_URL = b2.bm_URL)
and bm_URL not in
    (select bm_URL
    from bookmark
    where username='$valid_user.')
group by bm_url
having count(bm_url) >$popularity;
```

If you are anticipating many users using your system, you could adjust $popularity upward to suggest only URLs that have been bookmarked by a large number of users. URLs bookmarked by many people might be higher quality and certainly have more general appeal than an average web page.

The full script for making recommendations is shown in Listings 27.26 and 27.27. The main script for making recommendations is called recommend.php (see Listing 27.26). It calls the recommender function recommend_urls() from url_fns.php (see Listing 27.27).

595