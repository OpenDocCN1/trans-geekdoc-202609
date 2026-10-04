
# Chapter 14

You always want to give your customers an outlet to express their concerns or problems, and it can give you a fuzzy feeling to get some positive feedback once in a while. To encourage your customers with feedback you do two things:

- Give them an incentive to complete a survey, or provide some sort of feedback. Free shipping, on your next order, or a free gift of sort are some good possibilities.
- Make it easy for your customers to complete a survey, but make sure it provides you with valuable feedback. Don't just ask for their comments; ask them to rate certain areas of your site. Also, don't give them 100 questions, a maximum of 15-20. After that, people lose interest and their special gift isn't worth it.

By sticking to the preceding guidelines and advice, you will increase the quality and quantity of your customer feedback and increase your ability to tap into one of your most valuable resources.

# Summary

Now that you know the how-to to add e-commerce to your site, you will feel comfortable making your site as competitive and professional as any other site. You should be able to set up a simple shopping cart, and, with time, you will be able to continue to really enhance your cart and your site. E-commerce concepts aren't difficult to comprehend, and by following the simple guidelines we've outlined, you will be well on your way. Although e-commerce retailers don't enjoy overnight success, adding e-commerce to your site can really augment what you're courting and may grow to something big over time.

# Exercises

We know we're not perfect, so before starting all the things we don't accomplish in our shopping carts, we'll save you the trouble and list them for you. As a matter of fact, we did these things on purpose we wanted to give you some homework.

Anyway, here are the things you can work on, and hints are in Appendix A in case you need to cheat:

- Allow for options. We have noticed that we don't let our customers pick the size of their T-shirt or color of the Superhero Body Suit. Alter the codes to allow for these options.
- Allow for payment. Because of copyright issues, we weren't able to hook you with Paypal or one of the other payment processors available. Decide how you want to accept payment, and then alter the code correctly.
- Allow for tax. Many states require that you charge sales tax on the orders to the state where you have a physical presence, and some states require sales tax on all online orders. Set your code to check for customers in your own state and add the appropriate sales tax to those orders.
- Check for mistakes. We have not included any mechanism to check for fields, or for mismatched types (such as a bogus e-mail address). Add these checks in your code.
- Allow for registering, login, and order tracking. Some customers like to check the status of their orders.

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_525_0.png)

# Creating a Bulletin Board System

People don’t like to be alone because we are social animals. Throughout our brief history as civilized human beings, we have consistently maintained some of connection to other people, whether it be the family unit, clans, chess clubs, or AA meetings.

With the advent of the computer, many geeks found themselves shut in a room for long periods, becoming the modern equivalent of the social outcast. (How many of us have joked about not knowing what the sun looks like?)

Enter Dennis C. Hayes, Ward Christensen, and Randy Seuss, three very smart men who together made it possible for you to communicate with other computer geeks without ever having to look at their faces.

# History of the Computer Bulletin Board

D. C. Hayes is the inventor of the modem; indeed, one brand of modems was named for him. He is the father of PC-to-PC communication and is at the top of the list of people responsible for the 807 America Online disks you received in the mail last year.

Ward Christensen is the creator of Xmodem, which allowed users to send and receive files. It was the precursor to many file transfer programs, including FTP, which we still use today.

In February 1978, Christensen teamed up with Randy Seuss to create the first program that allowed users to communicate with one another over a modem. They called it a bulletin board system because it emulated the bulletin board they used at their local computer club. (Yes, they were serious geeks!) They named the board Chicago Bulletin Board System (CBBS).

# Chapter 15

Bulletin boards began cropping all over the country and were soon very popular places to communicate with other people. Suddenly, geeks were no longer pariahs, but could actually interact with others. Sure, non-BBS users saw them as outcasts, but what did they know? They were just civilians, unwise of the wipers of computers.

The only problem was that you had to dial in the specific BBS you wanted to connect. There was no network of computers that enabled you to join from BBS to BBS. Over time, communication speed increased to the point where nowadays is no longer the preferred connection device. With the arrival of the Internet, people had a place to connect once time, and “surf” from site to site. BBS's began to go by the days of dinosaur.

Fortunately, BBS's didn't become extinct. They still exist today, but they have evolved. A BBS is simply a Web site that does what BBS of old—allows users to log in and communicate with others about a common interest. If you want to talk other people about your collection of Barbie doll chances, there is a BBS for you out.

Many BBS refer to them as forums. By definition, a forum is a gathering place where people can meet and discuss different topics. That is very apt definition for a BBS. However, we are going to call it a little further, for in the computer world. By our definition (and the we we will use in this chapter), a forum is a place to talk to other people about a common interest. A bulletin board is the location in which the forum exists, which has multiple forums. Therefore, you might visit a book BBS to find different forums for science fiction, authors, and more.

# Your Bulletin Board

This brings us to the reason for this chapter. You are going to create a Bulletin Board System. Once you create the BBS, it will be up to you to create any type of forums within it that you need.

No doubt, you have visited many bulletin boards by now and are aware of the different features they have to offer. Some of them have many bells and whistles, and are very slick programs. PHPBB and Vbullet are two of very nice applications. Yours will not have the feature set that these others (unless you are ambitious and decide to create the app you write).

You have probably seen some very simple boards out there, too. Some are nothing more a couple of input boxes for Subject and Body, with no authentication. These are fine for some Web sites, but not for us. This is the last application of the book, and we're going to put a few features in this thing. We are also going to using cascading sheets (CSS) to alter the look of the page, let's say, the apps up to now have been fairly plain. Because of the extended feature of this set, CSS will help you positioning on the page a better.

Don't worry if you don't know CSS; it's not a requirement. We will provide you with a CSS file, downloadable from the Web site. If you know how, you can write your own style sheet, or modify the one we provide. Otherwise, simply use the one we give and you'll be fine. The application will work fine without the CSS, but as you will see, it will be much prettier and better laid out with it.

# Creating a Bulletin Board System

Here is a list of some of the prominent features of the board you will build:

- User authentication: You want to keep track of who is posting. You can certainly allow anonymous (hmm might make a good exercise), but this app will require users to log in.
- Search: The search is the key to any good board, in our opinion. This will allow users to see if their question has already been answered, as well as enable to find posts they want to talk about.
- Admin screen: There will be a few features of the site that can be modified in the admin section.
- Regular expressions: We include BBcodes in the application. If you have never seen them, there are special codes that give the user a ability to format their posts. For example, by placing [b] and [/b] around words they will bold (for example, [b]words[/b] will become some words). We will be using regular expressions for this.
- Pagination: You don't want to have 328 posts on a single page. For one, it's a bit long to read. PHP takes a while to render such a page, especially if there are images in the posts. For this, we offer page links at the bottom to load different pages. To enable this, you will be creating a pagination function.

These are most of the features of the board. There will be a few bells and whistles added, but we won't spoil the surprise yet. We want to give you plenty of "ooh," "aah," and "You're a genius!" later.

# Try It Out The own Code

This is a large application--the biggest in the book. It consists of about 1,800 lines of code. Are you scared yet? Don't be. The hardest part is the typing, and if you want to avoid that, you can always download the code from the Web site:

If you download the code and skip what follows and jump ahead to read the explanation of the code, go to the next Try It Out section.

The first thing you will need to create a database. If you have already created a database for the other apps in this book, we recommend you use the same database. There is need to create a new one. This app uses the prefix forum_ for its tables, so there should be no conflict.

If you do not have a database created, then Chapter 9 will help you create one. Do that, and then come back. We'll wait . . .

There are around 20 PHP files to edit. We are simply going to list them one after another, giving you the filename of each, and a short explanation of what the file is for. Save each file in the same folder.

Do your typing warm-ups, and let's get started!
