# Chapter 2

The isget function checks to see if a variable has been set yet (this doesn't check the value, just whether or not it has been used). We didn't want to show users the information about our favorite movie if they didn't click on the link to see it, so we if/else'd right out there. If the favorite favmovie has not been set yet, the program jumps down to the else portion.

The program performs another if statement to check the value of movienum to run the correct corresponding functions.

It also references the movienum variable for the title of our list, so the program displays the correct number of movies in the list.

As you get more advanced in your PHP programming skills, you might store a list of all your favorite movies in a database and reference them that way, changing your listmovies() function to list only one movie at a time and running the function movienum a number of times. You could also give users the option of choosing how many movies they want displayed, perhaps through a drop-box or radio buttons. That would be your new movienum variable.

![](bbox=[0.072, 0.35, 0.843, 0.825])

Figure 2-15