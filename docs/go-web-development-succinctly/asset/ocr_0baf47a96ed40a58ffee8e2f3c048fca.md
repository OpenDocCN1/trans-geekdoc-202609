# Search for%Lond%

| City | Country Code | Population |
| --- | --- | --- |
| Londrina | BRA | 432257 |
| London | GBR | 7285000 |
| East London | ZAF | 221047 |
| London | CAN | 339917 |

Figure 14: Displaying the Query Results in an HTML Table

Not exactly pretty, but a slight improvement. Of course, we can style this to our hearts' content with some judicious use of CSS.

But wait a minute—at what expense does this come to our code? Our nice, neat program is now a mess of inline HTML. If it becomes more complex over time, we'd find it very difficult to maintain. What's more, each time we want to make a trivial change, we would have to recompile our code.

We have now committed one of web development’s great cardinal sins—mixing logic and presentation in our source code. Frankly, there’s a much better way to format the display. We’ll examine that in the next chapter.