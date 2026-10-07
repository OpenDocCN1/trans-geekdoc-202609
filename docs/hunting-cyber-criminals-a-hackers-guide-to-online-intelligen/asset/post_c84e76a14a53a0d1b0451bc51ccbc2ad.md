
# Chapter 15 | Researching People, Images, and Locations

![](img/ceaab52f5a948b18995b8efe89758781_350_0.png)

Figure 15.8

> **WARNING** It is worth noting that I have never, not one single time, received a useful match using a Google Images reverse search. I am always optimistic, though . . and for the sake of thoroughness, I always try here first.

## Searching for Gold

A while back, someone loosely associated with TDO sent me a few pictures where were claimed [to] associated with the threat actor known as Tessa88. Apparently Tessa sent a number of photos to this threat actor in some attempt to either seem cool, or verify her identity. Figure 15.9 is one of those, which shows what appear to be stolen credit cards.

You never know where or why this image might show elsewhere, but it is important to leave no stone unturned, which is why I like to start my search in Google Images. The results of the image search are shown in Figure 15.10. We have a match!

I swear, these results were completely unexpected. I am blown away that we have a match—and even more so that we have a useful one. Sometimes you get lucky. The single page that matches the picture is blackforum.cc, a Russian card forum. Let's explore.

## Following the Trail

Following the trail to the Russian carding forum, we can see a post where the cards are listed for sale by user “Bankir” (Figure 15.11). This is a really solid hit—I already had the other two images in this picture. This tells me that the person who posted this message is either the same person or working with the same group.

![](img/ceaab52f5a948b18995b8efe89758781_351_0.png)

Figure 15.9

In either case, we have learned a new username he is associated with: "Bankir." We also now have his telegram account that we can use if we choose to engage with him. File that one under "win."

## TinEye

TinEye (www.tineye.com) is very similar to Google Image reverse search and by "very similar," I mean exactly like Google Image reverse search. TinEye is hit-or-miss, like Google, so you should really try them.

Figure 15.12 shows the TinEye search page.

For completeness, we search TinEye for the same credit card image in Figure 15.9. Unfortunately, Figure 15.13 shows that TinEye was unable to match the image found by Google Images.

Let’s run another search. This time, we’re checking for matches on one of Cyfer’s old profile avatar avatars (Figure 15.14).

This is a fairly common image, and a good way to illustrate the difference between TinEye and Google Images. Running this image through the Google Image reverse search returns roughly 20 million results.

![](img/ceaab52f5a948b18995b8efe89758781_352_0.png)

On the other hand, TinEye returns a more manageable number (Figure 15.15). The first hit on this image is a profile avatar for a user on intchat.ru, an old-school Russian hacking forum. This solid match, and absolutely worth investigating. It is also another great example of why you should never rely on just one tool for all of your results.

Interestingly enough, if you look through the search results, you will eventually find Cyfer’s protected Twitter page (Figure 15.16).

Figure 15.10

Buy a bank debit card of Sberbank, VTB-24, Alfabank [Sale deb ...

written by Banker 23 March 2016 - 14:57

# Sale of debit cards of banks of the Russian Federation
(all questions about the acquisition and the rest ask in the LAN)

- The list:
1. Application to the card
2. Debit card
3. Pins code for withdrawing from an ATM
4. Sims linked to the card
5. Internet access banking
6. Code (and / digital code)
7. Color scan of passport

Warranty:
When using a card for white threads, receiving white funds and black/gray bought through bitcoins and exchanges, the card will live for the whole life. The bi is immediately.

Availability and Cost: Silver
Debit Cards

Categories and Prices:
| Item | Price |
| :--- | :--- |
| Monument | 4000. |
| Classic | 5000. |
| Gold | 8000. |

Alfa Bank Debit Card
Categories and Prices:
| :--- | :--- |
| Classic | 5000. |
| Gold | 8000. |

Debit Cardof! VTB-24 Bank
Categories and Prices:
| :--- | :--- |
| Classic | 5000. |
| Gold | 8000. |

Promsvay Bank Debit Cards
Categories and Prices:
| :--- | :--- |
| Classic | 5000. |
| Gold | 8000. |

![](img/ceaab52f5a948b18995b8efe89758781_353_0.png)

Write in the LAN or Telegram - @BankerSeller

![](img/ceaab52f5a948b18995b8efe89758781_353_1.png)

Figure 15.11

Reverse Image Search
Search by image and find where that image appears online

Figure 15.12

![](img/ceaab52f5a948b18995b8efe89758781_354_0.png)

Figure 15.13

![](img/ceaab52f5a948b18995b8efe89758781_354_1.png)
![](img/ceaab52f5a948b18995b8efe89758781_354_2.png)

| Sort by best match | Filter by domain/collection | < 1 of 125 > |

![](img/ceaab52f5a948b18995b8efe89758781_354_3.png)

![](img/ceaab52f5a948b18995b8efe89758781_354_4.png)

Figure 15.15

Another excellent match. I have found that threat actors like to reuse pictures, finding a new Twitter or social media page posted with a threat actor can come down to something simple like matching a profile image. And hey, look at that! I had no idea that he follows me! That's kind of funny, but it also confirms one very important detail: this account is still active.

![](img/ceaab52f5a948b18995b8efe89758781_355_0.png)

Figure 15.16

## EagleEye

EagleEye is an image search tool designed to reverse-search social media pictures. The main drawback of EagleEye is that you need to know part of the person's name in order to search for more matches of their profile pictures. This may not necessarily a problem if you already know the name of the threat actor or are just looking for more information on that. EagleEye first searches the name across Facebook, then performs a reverse image search across Google, Image, and Yandex to find the person's other social media accounts. The end result is a nicely formatted PDF.

Another good use of this tool would be to check if someone is potentially catfish. It's always good to run someone's picture through and see what matches come back. You can download EagleEye at https://github.com/ThoughtfulDev/EagleEye. Figure 15.17 shows the main EagleEye screen.

For our example, let's search for one of my photos (Figure 15.18) and see what kind of results we get. Figure 15.19 shows what the typical EagleEye output looks like when processing an image.

EAGLE EYE Version 0.2
usage: eagle-eye.py [-h] [-sFB] [-sv] [-json]
optional arguments:
-h, show this help message and exit
-sFB, skip Facebook
-sv, skip Yandex
-json, Generates a json report.
-f, Specify a Filename
-fblist, links to Facebook
'.skipfb' must be enabled to use this

![](img/ceaab52f5a948b18995b8efe89758781_356_0.png)

Figure 15.18

In the background, EagleEye loads and automatically searches for your image. While useful, EagleEye was at least to identify my page by searching for information gathered from profile (Figure 15.20). Not bad, actually found a few of my profiles, so there is definitely some merit to this tool if you want to identify people.

![](img/ceaab52f5a948b18995b8efe89758781_357_0.png)

Figure 15.19

![](img/ceaab52f5a948b18995b8efe89758781_357_1.png)

Figure 15.20
