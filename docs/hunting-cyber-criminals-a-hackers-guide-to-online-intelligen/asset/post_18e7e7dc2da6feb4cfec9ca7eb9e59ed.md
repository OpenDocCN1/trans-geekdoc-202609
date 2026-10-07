
# Chapter 16 Searching Social Media

OSINT.rest (www.osint.rest) is a giant API that allows you to collect media information on your targets. You can query the API using CURL commands in the command line, or use a tool like Postman (https://www.getpostman.com). This is a premium service—you can purchase API keys and queries in bulk. OSINT.rest allows API searches for the following:

- Search by phone or email
- Facebook (photos, page, video, users, posts, likes, places)
- Instagram (search by alias)
- Image search
- Twitter search
- Foursquare
- SL DB
- VK.com
- MySpace

When viewing the OSINT.rest API docs, you’ll find a button that says “Run in Postman.” Click this button to load the API directly into your Postman app (currently available for Windows or Mac).
The menu on the left will be populated with searches from OSINT.rest. Figure 16.1 shows the Postman app with the OSINT.rest API connection loaded, and the “Search Information by Phone” option highlighted.

![](img/ceaab52f5a948b18995b8efe89758781_365_0.png)

Figure 16.1

For our trial, I put in my cell phone number. The window in Figure 16.2 shows the successful results from this search.
This API only works with U.S. numbers, but the results are obviously very useful if you need help in reversing a phone number.

![](img/ceaab52f5a948b18995b8efe89758781_366_0.png)

Figure 16.2

OSINT.rest has nearly a hundred different options for searching Facebook, which include the ability to search for users, a user's friends, people who comment on posts, videos, pages, and more.

For our first search, let's use the profile of Nathan Wyatt, someone who was convicted and sentenced to prison in 2017 for hacking the profile of Pippa Middleton. As of 2019, Nathan Wyatt is fighting extradition to the U.S. for crimes committed with The Dark Overload (https://www.dailymail.co.uk/news/article-6578213/Stay-home-father-hacked-hacking-fights-extradition-US.html).

A simple search on Facebook will reveal his public Facebook profile. Figure 16.3 shows his Facebook page and a profile ID of 100010064775327 in the URL bar.

Having the target Facebook ID saves us a step of having to look for it. Most searches require the ID, so you will eventually need to find it. Let's dig into the capabilities of OSINT.rest.

Knowing your target is connected is a very easy way to identify other threat actors or others with mutual connections. Getting a JSON list of someone's friends is as simple as entering their Facebook ID in the query parameters. Figure 16.4 shows the output of this query.

![](img/ceaab52f5a948b18995b8efe89758781_367_0.png)

Figure 16.3

- New Collection

| KEY | VALUE | DESCRIPTION |
| --- | --- | --- |
| query | 10000164775327 | Facebook User ID |
| limit | 1000 | List limit (max=1000) |
| offset | Description | Description |

Figure 16.4

> NOTE: Here is a very specific example of knowing someone's friends can be important. While back I was looking for a specific threat actor (I knew his real name). I was looking through his friends list and there were a few people that caught my eye. After looking their Facebook profiles and friends lists, I noticed that they were actually friends with my target's alert Facebook accounts! The photo was an immediate gateway, but since the name was different, I would have found that if I had not taken the time to look through his friends list.

We can see from the output that Nathan Wyatt has 77 Facebook friends. This output also gives us names, IDs, images, and direct URLs of his friends. This is one particular area where using Maltego makes this process much easier since the app automatically creates a visual of all the connections for you, which I demonstrate in this text.

We know alias "CraftyCockey" is directly associated with Nathan Wyatt from all the public news sources and court reports, so is a great place to start searching.
For this list, let's try Instagram. Using the Instagram API option on the left, Figure 16.5 shows a query of "CraftyCockey" to the results.

![](img/ceaab52f5a948b18995b8efe89758781_368_0.png)

# Figure 16.5

This API search has returned everyone on Instagram with CraftyCockey as part of the team. We have only 20 results, so looking through all of them is worth the time to identify the right profile. If you have other aliases just rinse and repeat. Let's try one more.

# Another Subject

For this next example, let's look up our friend and fellow security expert Christopher Meunier (aka White). Most of Chris's profiles are offline, due to the magic of Facebook's search, I typed in his name and popped up a new profile with his profile picture and an intentionally misspelled name. The Facebook profile was listed as Chris Maunier, but for some reason the search results displayed the profile. In order to perform any searches, we need to know his ID. All we need to do is enter username in the "Get Facebook User ID by Profile" API search (Figure 16.6).

| Parameters | Authorization (8) | Body | Pre-request Tests | Cookies (0) |
| --- | --- | --- | --- | --- |
| Query | | christopher.maunier.923 | | |
| KEY | | Alias | | |
| alias | | Value | | |
| Body | Headers (10) | Test Results: 200 OK Time: 161 ms Size: 374 B | | |
| Pretty | Raw | HTML | | |
| | {"id":"1000325741589"} | | | | |

Figure 16.6

Once we run the search, we easily obtain his Facebook ID of 1000325741589. Unfortunately, Chris's profile is mostly private, but there is still a decent amount of information we can get from it. To start, "Get Facebook User Profile by ID" (Figure 16.7) will return a summary of the target's Facebook profile, which includes recent posts, full name, direct photo. One thing we can immediately see from these results is the URL of his photo. Using OSINT.rest also includes reverse image search. Let's first start by navigating to this URL. The public post for user 1000325741589 (Figure 16.8) contains the caption. Now that we have a profile, we can save it for later or copy the URL and perform reverse image search.

| History | Collections | API Beta |
| --- | --- | --- |
| + Get Facebook User Profile by ID | Examples (1) | |
| + New Collection | | |
| + Facebook Video | GET https://api.facebook.com/search/user?q=christ.maunier_923 | Save |
| + Facebook Photos | Params (Headers) Body Pre-request Tests Code Comments (0) | |
| + Facebook Users | Query Parameters | Bulk Edit |
| | query VALUE | |
| | christ.maunier_923 Facebook User ID | | |
| | Key Value | Description Status: 200 OK Time: 8.9ms Size: 8 KB | |
| | Body Collections (10) Results | Download | |
| | Preview JSON | | |
| 1 | "id": "135089327415693", | | |
| 2 | "name": "Christopher Maunier", | | |
| 3 | "type": "user", | | |
| 4 | "location": "Temporary account for hunting people" | | |
| 5 | "gender": "female", | | |
| 6 | "featured_count": null, | | |
| 7 | "profile_pic_square": "https://look-aside.fbcdn.net/v3/r/u1-b/163/d1b/c3/580604332715709555529509406549518-m.jpg_cat_content=fr1-3.xdb00002e4c", | | | |
| 8 | "image": "https://look-aside.fbcdn.net/v3/r/u1-b/163/d1b/c3/580604332715709555529509406549518-m.jpg_cat_content=fr1-3.xdb00002e4c", | | | |
| 9 | "photo_id": "135089327415693", | | | |
| 10 | "album": "https://look-aside.fbcdn.net/v3/r/u1-b/163/d1b/c3/580604332715709555529509406549518.jpg_cat_content=fr1-3.xdb00002e4c", | | | |
| 11 | "id": "13190933440671", | | | |
| 12 | "name": "Christopher Maunier", | | | |
| 13 | "type": "user", | | | |
| 14 | "location": "Profile pictures", | | | |
| 15 | "gender": "female", | | | |
| 16 | "featured_count": null, | | | |
| 17 | "profile_pic_square": "https://look-aside.fbcdn.net/v3/r/u1-b/163/d1b/c3/580604332715709555529509406549518-m.jpg_cat_content=fr1-3.xdb00002e4c", | | | |
| 18 | "image": "https://look-aside.fbcdn.net/v3/r/u1-b/163/d1b/c3/580604332715709555529509406549518-m.jpg_cat_content=fr1-3.xdb00002e4c", | | | |
| 19 | "photo_id": "13190933440671", | | | |
| 20 | "album": "https://look-aside.fbcdn.net/v3/r/u1-b/163/d1b/c3/580604332715709555529509406549518.jpg_cat_content=fr1-3.xdb00002e4c", | | | |
 }
