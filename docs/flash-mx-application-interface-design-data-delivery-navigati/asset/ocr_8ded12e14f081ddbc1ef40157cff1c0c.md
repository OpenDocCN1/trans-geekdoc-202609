It is important to understand that a preloader is not the same as an intro animation. The former provides information and distraction during the load of the important material, hopefully at a small overhead. An intro animation, however, is usually produced as a sort of advertisement or "Flashy" display of skill and is often placed, as the name implies, as an introduction to the main content of the site. When Flash was first being used to enhance sites, it was all too common for the intro animation to have a large file size and require a preloader itself. At first, the wow factor justified the extra time, but it quickly grew tiresome for many Web users, which is when the "skip intro" button came into prominence. Unless you have good reason to provide an intro animation, or unless you can produce an animation with a small file size, it is usually best to get users directly to the main content of your site. Still, if you insist on a large intro animation, be sure to include a preloader before it so the user knows that something worthwhile is coming.

OK! Now with an idea of what we are trying to accomplish by building preloaders, let's look at some of the common pitfalls we will face.

# Stumbling blocks with preloaders

# On streaming

One of the terrific features of Flash is its ability to stream information to the user's computer. This allows the user to view content as soon as it becomes available, without having to wait for the content to load in its entirety. By planning the layout of your site or animation to take advantage of this feature, a preloader can become unnecessary since the user isn't made to wait more than a second or two before things begin happening. With long animations, or sites that are broken up into many frames on the main timeline (a practice used less and less frequently now with the powerful new scripting features of Flash MX), this is accomplished by keeping the initial frames' content small so that they can be seen immediately, allowing more time for the "heavier" frames to be loaded later in the timeline.

It is common now, however, to have much, if not all, of your content in a single frame. Animations may be created inside movie clips or through code, and content may be loaded and unloaded onto the stage from your movie's library or externally. When a movie is structured in this way with all of its content in the first frame, the user will see nothing until the content has loaded in its entirety. Because of this, a preloader becomes a necessity, if solely to inform the user that something is indeed coming, despite the lack of activity on the screen.

Since this chapter is on preloaders themselves and not ways of avoiding them, we won't discuss streaming to a large extent. In the examples I present in this chapter, we will work under the assumption that we have a large amount of content contained in a few frames that we need to provide a preloader for.

This doesn't mean that we will ignore the issue of streaming altogether. In actuality, the streaming feature of Flash is what allows us to create a preloader in the first place. By placing a small preloader in the first frame of your movie, it can stream into the user's player almost immediately and give the user feedback as the rest of the site is loading.

You can easily apply the same principles of a preloader to a streaming document if the need arises by simply providing a preloader that looks to load a set amount before the movie begins to play (similar to the buffering that occurs with other streaming media).

After a preloader for a large section at DaedalusMedia.com has loaded a set amount of bytes, the section is presented in part, with additional subsections becoming available as they load. This provides the user with the opportunity to see some content before the section is fully loaded.

![](bbox=[0.515, 0.81, 0.87, 0.99])