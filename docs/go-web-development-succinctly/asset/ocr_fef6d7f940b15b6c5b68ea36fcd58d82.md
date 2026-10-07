```
{
  "Title": "The Machinist",
  "Year": "2004",
  "Released": "03 Dec 2004",
  "\*Cast": "Christian Bale",
  "Genre": "Drama, Thriller",
  "Director": "Brad Anderson",
  "Writer": "Scott Kosar",
  "Plot": "An industrial worker who hasn't slept in a year begins to doubt his own sanity",
  "Language": "English, Spanish",
  "Awards": "7 wins, 14 nominations",
  "Metacritic": "61",
  "imdbVotes": "291,697",
  "imdbRating": "7.7",
  "type": "movie"
  "Response": "True"
}
```

Figure 21: Open Movie Database API for The Machinist

Figure 23 sets the r (response parameter) to XML:
http://www.omdbapi.com/?t=the-machinist&plot=short&r=xml.

```
<root response="True">
<movie title="The Machinist" year="2004" rated="R" released="03 Dec 2004" runtime="101 min" genre="Drama, Thriller" director="Brad Anderson" writers="Scott Kosar" actors="Christian Bale, Jennifer Jason Law, Aitana Sánchez-Gijón, John Sharian" language="English, Spanish" country="Spain" awards="7 wins & 14 nominations" poster="https://images-na.sl.images.com/M/MV3jNk1B2Y1jYjNm0YTmWLWIOT2gtNDUX5NDE5jZmE0E3KyXFkcGdeQXVyNT1qeODI_V" metacacle="61" imdbRating="7.7" imdbVotes="291,697" imdb="3056182" type="movie" />
</root>
```

Figure 22: Changing the Output to XML Format

That's pretty concise as far as XML goes. A lot of XML is deeply nested and is a nightmare to parse, hence the preference for JSON in modern APIs.

Play around with the Open Movie Database API for a bit. I'll wait!

So, that is an example of a RESTful API. You're effectively using the URL itself to make calls to the web service.

# RESTful web service

We're going to build similar in this chapter.

You've probably already thought: "I could do that with Go!" And, indeed, you can. So, all you need to get some data. And we've already been playing with MySQL's 'world' database, let's use that.

Our application will allow users to enter any of the following paths and get in the way described: