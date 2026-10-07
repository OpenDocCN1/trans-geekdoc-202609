# Chapter 15 ≡ Researching People, Images, and Locations 347

> EXPERT TIP: JOHN STRAND
I was testing Canarytokens on a user who I knew was in downtown Louisville, KY. When the user opened the malicious package, I was sent back his IP address. When I performed an geo-location lookup on IP IP address, and the result was not very accurate – the results came back with a location that was about 20 miles away.
I have found one way to get better granularity on your geo-location lookup is to use the tracer command on the IP address in question. Then, when looking at your results, take the IP address of the last routing hop and geo-locate that IP address instead.
This will get you much closer. In my test case, I was able to pin-point the IP address to one block of the hotel.
The reason why this works is because most IP addresses (for home users in particular) are handed out via random DHCP. The IPs can bounce around and a geo-ip lookup will have no way of knowing where you are actually.
But using routing infrastructure from the traceroute command, we can typically get much closer and much more accurate results for a location.

# Summary

This first chapter in the “People Hunting” section covered a number of tools that can be used to track people online, including reverse image searching, background checks, various people lookup tools, and ways to gather geolocation information from social media.

The next chapter will dive deeper into researching social media profiles, which will include tools and techniques that can help identify multiple aliases, accounts, and phone numbers associated with a target.