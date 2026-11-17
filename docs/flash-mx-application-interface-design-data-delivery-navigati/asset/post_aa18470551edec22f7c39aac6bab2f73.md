
## DESIGNING PRELOADERS

Let's begin this chapter with a little honesty – I am an impatient person. I have never been one to wait patiently, as I always feel there is something more productive I could be doing with my time. Traffic jams, delayed flights, shoppers in front of me digging for change at the check-out counter of a grocery store – all anathema to me. I'd speak more on this subject, but you probably get the idea and I'm sorry, I don't really have the time...

![](img/50202c17d5022233f3e3ec60560e35aa_10_0.png)

Of course my point is that, for most of us, when we have places to go, anything that stands in our way can become an annoyance. With traffic jams, delayed flights and inconsiderate shoppers, we don't have many options other than to wait. On the Web, however, if waiting gets irritating there are an infinite amount of destinations to explore, all just a click away. So if we want to keep our audience's attention, we have to make sure that there is no opportunity for them to get bored. If our site takes too long to load, the chances are that most users will never see our painstakingly designed content. So we need to avoid this risk, by providing a preloader.

![](img/50202c17d5022233f3e3ec60560e35aa_10_1.png)

![](img/50202c17d5022233f3e3ec60560e35aa_10_2.png)

This is a 3D preloader used at 27Bobs.com. As the site loads, the sketchy wireframe is replaced by a solid 3D block, representing the “chalk” used to draw the main site.

We'll be seeing more from 27Bobs a little bit later.

![](img/50202c17d5022233f3e3ec60560e35aa_10_3.png)

### What is a preloader?

Look up “preloader” in Webster’s Dictionary and you’ll find...nothing. No doubt it will make its way into the reference manuals shortly, but for the time being let’s form our own definition. Obviously, the word itself implies that a preloader appears before whatever main content may be loading. Since anything on the Web needs to be loaded to be seen, including a preloader, I would go further and say that a preloader would have a significantly smaller file size than whatever is the main content that is to be loaded. In order to fulfill its function, it must load pretty much instantly.

Let’s amend our preloader definition to express these ideas. We have:

a preloader is a small piece of content a fraction of the size of the main content, which is quickly loaded before the rest of your movie and offers a combination of feedback, information and entertainment for the user during the time it takes to load the main content.

So we have a small piece of content that loads before, and is the fraction of the size of, the main content. What is the purpose of this smaller content? Well, in its basest form, a preloader simply gives the user feedback that something is occurring. Without a preloader, a user seeing a blank screen with no content might feel that the browser or computer has frozen. A simple “loading...” appearing on the screen would serve this purpose, although if it just sits there for too long we are running the same risk again.

The preloader at DaedalusMedia.com uses the number of bytes loaded to advance a frame-based animation. This animation, which consists of cracks slowly covering a statue, culminates in the statue exploding into fragments as the site is fully loaded.

![](img/50202c17d5022233f3e3ec60560e35aa_11_0.png)

Of course, a preloader could, and should, go further and give the user constant information on what is occurring and what is actually being loaded. Text information displaying what data is being transferred or a loading bar that shows what percentage has been loaded would accomplish this. By keeping the user in the know about what is going on, they will be less frustrated at the delay. A traffic jam would be more bearable with traffic information that kept you updated as to the reason for the delay and when the wait might be over.

![](img/50202c17d5022233f3e3ec60560e35aa_11_1.png)

Finally, to help pass the time while stuck in that car, what could be better than the radio playing tunes while you wait? Entertainment during delays can make the time pass much more quickly. As the cliché goes, time flies when you’re having fun. Why not apply that to your preload time?

It is important to understand that a preloader is not the same as an intro animation. The former provides information and distraction during the load of the important material, hopefully at a small overhead. An intro animation, however, is usually produced as a sort of advertisement or "Flashy" display of skill and is often placed, as the name implies, as an introduction to the main content of the site. When Flash was first being used to enhance sites, it was all too common for the intro animation to have a large file size and require a preloader itself. At first, the wow factor justified the extra time, but it quickly grew tiresome for many Web users, which is when the "skip intro" button came into prominence. Unless you have good reason to provide an intro animation, or unless you can produce an animation with a small file size, it is usually best to get users directly to the main content of your site. Still, if you insist on a large intro animation, be sure to include a preloader before it so the user knows that something worthwhile is coming.

OK! Now with an idea of what we are trying to accomplish by building preloaders, let's look at some of the common pitfalls we will face.

### Stumbling blocks with preloaders

### On streaming

One of the terrific features of Flash is its ability to stream information to the user's computer. This allows the user to view content as soon as it becomes available, without having to wait for the content to load in its entirety. By planning the layout of your site or animation to take advantage of this feature, a preloader can become unnecessary since the user isn't made to wait more than a second or two before things begin happening. With long animations, or sites that are broken up into many frames on the main timeline (a practice used less and less frequently now with the powerful new scripting features of Flash MX), this is accomplished by keeping the initial frames' content small so that they can be seen immediately, allowing more time for the "heavier" frames to be loaded later in the timeline.

It is common now, however, to have much, if not all, of your content in a single frame. Animations may be created inside movie clips or through code, and content may be loaded and unloaded onto the stage from your movie's library or externally. When a movie is structured in this way with all of its content in the first frame, the user will see nothing until the content has loaded in its entirety. Because of this, a preloader becomes a necessity, if solely to inform the user that something is indeed coming, despite the lack of activity on the screen.

Since this chapter is on preloaders themselves and not ways of avoiding them, we won't discuss streaming to a large extent. In the examples I present in this chapter, we will work under the assumption that we have a large amount of content contained in a few frames that we need to provide a preloader for.

This doesn't mean that we will ignore the issue of streaming altogether. In actuality, the streaming feature of Flash is what allows us to create a preloader in the first place. By placing a small preloader in the first frame of your movie, it can stream into the user's player almost immediately and give the user feedback as the rest of the site is loading.

You can easily apply the same principles of a preloader to a streaming document if the need arises by simply providing a preloader that looks to load a set amount before the movie begins to play (similar to the buffering that occurs with other streaming media).

After a preloader for a large section at DaedalusMedia.com has loaded a set amount of bytes, the section is presented in part, with additional subsections becoming available as they load. This provides the user with the opportunity to see some content before the section is fully loaded.

![](img/50202c17d5022233f3e3ec60560e35aa_12_0.png)
