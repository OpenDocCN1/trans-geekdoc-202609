# Core PHP Programming

identifier from page to page either through links or with cookies. You will have to generate identifiers randomly, otherwise it is too easy for anyone to masquerade as a legitimate user. Fortunately, random identifiers are easy to generate.

Listing 15.11 illustrates how this works. A pool of characters to use in the session identifier is defined. Characters are picked randomly from the list to build a session identifier of the specified length. That identifier is used inside a link so that it is passed to the next page. This method works for any browser, even Lynx. Chapter 17 discusses the integration of this technique with a database.

It's very important to have random numbers here. Suppose you use the seconds on the clock. For one encore, every session identifier will be the same. And if very many people will be accessing a Web site during a single second. In Listing 15.11, I've used the microsecond clock to seed the random generator, but even this allows the window of opportunity for generating a duplicate session identifier. One way to avoid this situation is to use a lockable resource that holds a seed—for example, a file. Once you lock the file, you can read the seed and write back a new one, at which point you are assured that two concurrent processes get the same seed.

# Choosing Banner Ads

Another use for random Web sites is choosing from banner ads. Suppose you've signed up three sponsors for your Web site. Each has a single banner you promise to display on an equal proportion of hits to your site. To accomplish this, generate a random number and match each number to a particular banner. In Listing 15.12, I've used a switch statement on a call to mt_rand(). In a situation like this, you don't need to worry much about using good seeds. You simply want a reasonable distribution of the three choices. Someone guessing which banner will display at midnight poses no security risk.

# Listing 15.11 Generating a Session Identifier