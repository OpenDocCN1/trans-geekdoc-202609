Distributed under the Creative Commons Attribution-NoDerivs License
</copyright>
</uniprot>

The next example also uses XML, but is very different. This is again a tiny fragment of a much larger XML document, but this time it contains TV listings, in XMLTV format (Eden 2005), from the UK Radio Times (BBC 2005). Here, the content is primarily text-based.

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<!DOCTYPE tv SYSTEM "xmltv.dtd">
<tv source-info-name="Radio Times"
    generator-info-name="XMLTV"
    generator-info-url="http://membled.com/work/apps/xmltv/">
    <channel id="channel4.com">
        <display-name>Channel 4</display-name>
        <display-name>4</display-name>
    </channel>
    <programme start="20050102010500 UTC" stop="20050102024000 UTC" channel="channel4.com">
        <title>The Rachel Papers</title>
        <desc lang="en">A 19-year-old studying to go to Oxford enters all the information about his love life into his computer in a determined effort to find the perfect seduction technique. But his system collapses when he meets and falls in love with the beautiful Rachel, an American living in London. The couple spend a passionate weekend together, but then the dream begins to fall apart.</desc>
    <credits>
        <director>Damian Harris</director>
        <actor>Dexter Fletcher</actor>
        <actor>Ione Skye</actor>
        <actor>Jonathan Pryce</actor>
        <actor>James Spader</actor>
        <actor>Bill Paterson</actor>
        <actor>Shirley Anne Field</actor>
    </credits>
    <date>1989</date>
    <category lang="en">film</category>
    <category lang="en">Film</category>
    <video>
        <aspect>15:9</aspect>
    </video>
    <subtitles type="teletext" />
</programme>
</tv>
```

# 5.4 Components of XML

Like an HTML document, an XML document consists of a series of tags surrounded by angle brackets and start tags may include attributes. There are, however, one or two additional aspects to XML, including what is known as the prolog. There are a number of