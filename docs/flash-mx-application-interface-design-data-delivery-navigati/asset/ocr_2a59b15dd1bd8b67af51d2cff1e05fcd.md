# The library

| Name | Kind | Linkage |
|---|---|---|
| book.background | Folder | |
| back | Movie Clip | |
| book pg | Bitmap | |
| libraryAssets | Folder | |
| bevelBox | Movie Clip | Export bevelBox |
| bevelCenter | Movie Clip | |
| bevelCorner | Movie Clip | |
| bevelCorn | Movie Clip | |
| bevelFell | Movie Clip | |
| bevelMiddle | Movie Clip | |
| bevelNeck | Movie Clip | |
| Compontent | Component | Export FComponentSymbol |
| SoundBox | Component | Export FSoundBoxSymbol |
| Component Styles | Folder | |
| Live Assets | Developer Only | |
| fonts | Folder | |
| Arial | Font | |
| titleFont | Font | |
| interface assets | Folder | |
| interfaceBack | Graphic | |
| jumpTo | Movie Clip | Export jumpTo |
| nodelsinterface | Movie Clip | Export nodelsinterface |
| node assets | Folder | |
| houseButtons | Graphic | |
| nodeBack | Movie Clip | |
| nodeGraphic | Movie Clip | Export nodeGraphic |
| nodeOpen | Button | |
| nodeSymbol | Movie Clip | Export nodeSymbol |
| spouse | Movie Clip | Export spouse |

standard fonts (Arial and Times New Roman) so you can choose your own fonts for your version of the project. All you need to do to change the fonts is double-click either font name (or right-click and select Properties) and select a different font for your own movie. This is one of the great advantages to using exported fonts. At any time you can change the fonts you've used through the whole movie with just a few clicks, allowing you to try different faces with little extra time spent. I love that versatility.

| Property | Value |
|---|---|
| Name | sansFont |
| Font | Arial |
| Style | Bold, Italic |

The last three folders to look at all contain something of interest, so we'll spend a little more time examining the items.

Next in our journey through the base file, let's take a look at our library to see what symbols I've included, as we won't be adding any more during the course of this chapter.

# The node graphic

The background folder contains the background symbol and JPG, so there's nothing to see there (move along now!). The Flash UI Components folder came along with the combo box component I used, and if you've worked at all with MX components you should be familiar with its appearance. For this project, I didn't touch any of the contents of these folders, except for adding three lines to the constructor function of the combo box (I've commented these lines rather flamboyantly if you care to take a look).

First, let's look at the contents of the node assets folder in your library. Most are simple symbols without any code, though you will note that nodeSymbol, nodeGraphic and spouse are all exported so we can dynamically attach them with our code. The symbol of most interest is nodeBack, which you should take a look inside by entering symbol editing mode.

The first folder we should look more closely at is the fonts folder. If you expand this, you'll notice it contains two fonts, sansFont and titleFont. For my finished project I used Verdana and American Unciale for these, respectively. In the base file, however, I have left them as

![](bbox=[0.483, 0.68, 0.892, 0.99])