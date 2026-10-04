# Determining the Scope and Goals of the Application

The purpose of any discussion board is reasonably simple. Any visitor to the site should be able to post a new topic to the board or reply to any of the existing topics. Furthermore, the board must be flexible enough to deal with any number of replies to an existing topic, or replies to replies, or replies to replies, and so and so on. Put another way, this board must be able to deal with indefinite level of depth. The script needs to react appropriately whether the discussion goes one level deep, five levels deep, or ten levels deep. This will require some new techniques, both in your data design and our scripts.

# What do you need?

You will need only two files to generate all the views needed for this application. But these two files will have very different looks depending on what information is displayed.

The first file will display titles and replies. The first time users come to the message board they will not know what threads they wish to read. Therefore a list of topics will be displayed. Figure 12-1 shows the list of top-level topics.

![](bbox=[0.158, 0.513, 0.742, 0.868])

Figure 12-1: List of top-level topics