When you are finished, save, upload, and test the page in your browser, clicking a sampling of links to ensure both that you are redirected to tours_detail.asp and that a different URL parameter is appended to the URL each time.

![](bbox=[0.28, 0.16, 0.92, 0.535])

# REVISING THE QUERY AND COMMENTING CODE FOR TESTING AND DEBUGGING

The region links send URL variables to tours_detail.asp, but that page has nothing set up to do anything with those variables. In this task, you will put that functionality in place. But there is a catch.

Usually, when you bind a URL variable to the page, an error message will be displayed if a user accesses the page and that URL variable is not present. But in this case, when the user clicks the View All link, no URL parameter is sent. Later, once you’ve added the form that enables users to choose a country from the list, users will have another way of accessing tours_detail.asp without using URL variables. Therefore, you must set up the page in a way that it does not depend on the presence of URL variables.

When you create applications—even applications as simple as a search and results page pair—it is incumbent on you to prevent errors from occurring. Prevention often requires some strategic planning, so let’s think this through before we continue building. The goal is to find a way to enable the page to return the proper results based on the type of data that is (or is not) available to it.