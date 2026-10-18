```
try
{
    xhr equest = getXMLHttpRequest();
}
catch(error)
{
    document.write("Cannot run Ajax code using this browser");
}
if(xhr equest != null)
{
    xhr equest.onreadystate change = processYahooNewsFeed;
    xhr equest.open("GET", "http://rss.news.yahoo.com/rss/topstories", true);
    xhr equest.send(null);
}
</script>
</body>
</html>
```

Figure 7.16 shows how the page looks when it has retrieved the first item from the feed. Of course the actual content changes on a daily basis.

# FIGURE 7.16 Part of the Yahoo news feed included in a web page using Ajax

![](bbox=[0.1, 0.5, 0.81, 0.77])