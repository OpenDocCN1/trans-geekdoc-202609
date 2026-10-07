# Chapter 16 ■ Searching Social Media 357

> WARNING If you are looking up a target's profile, I highly recommend—no, I urge to save any and all photos you come across. I made the mistake of not saving a photo assuming that I could come back to the profile later and grab the picture I needed. Unfortunately, the profile had taken offline and I was completely out of luck. To this day, I can still believe I didn't save the photo. Don't make the same mistake I did. Save everything (and properly catalog your folders so you can find the items).

Figure 16.9 shows the Reverse Google Image Search API utilized. The only parameter we need to enter is the value of the image URL.

![](bbox=[0.19, 0.296, 0.809, 0.497])

Figure 16.9

As you can see from the Body tab in Figure 16.9, our search results are empty. To double-check that this was not an API error, I manually ran the image through Google Images search and the results were the same. As I mentioned, I rarely get lucky with reverse image searching, but it is still something you have to try.

# Twitter

I have not come across a single threat actor or cyber criminal that did not have least one Twitter account. Twitter usually contains a gold mine of criminal activity, so you should always perform exhaustive searching of Twitter. Continuing from our previous example, we already know Mr. "Maunier" is associated with the name WhitePacket, let's see if we can come up with anything. To start our Twitter searches, we need to identify the target's Twitter ID. Luckily, OSINT.rest has an API search that allows us to derive the Twitter ID from a username. Figure 16.10 shows the "Get Twitter User ID by User Alias" search, with a query string of "whitepacket."