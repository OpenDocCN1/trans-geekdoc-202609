retrieved after correlation. We will be using a for loop to retrieve and print the movie data. There is another function for movie recommendations called Recommend_MOVIET(). This function just retrieves the top five rated movies. The overall ratings are based on the IMDB ratings.

Now we will be writing a function called Movie_Recommenders with a variable named id as its parameter. if the value of id is 0, then the voice assistant asks for the user to provide any user interest such as a search for a similar movie. Now let’s take a variable q and call the takeCommand() function which takes the commands from the user. Then we will set a temporary variable to a value of 0. If the command given by the user is “go back”, then the voice assistant goes out of the movie’s recommendations. If the user says yes as the command, then the voice assistant asks the user to tell the name of the movie so that the voice assistant could recommend the user similar kinds of movies. Now the temporary variable is set to 1 and the function Recommend_MOVIE() is called to list out the similar kind of top five movies. If the user gives the command as no or does not say any command, the control goes to Recommend_MOVIET() command and prints the top five rated movies. If the value of the temporary variable is zero, then the voice assistant asks the user to speak the command again so that it can recognize the command given by the user correctly.

# 6.5.2 KNN Algorithm Book Recommendation

We write a function named Recommend_Book() to handle book recommendations. This function filters the books present in CSV files based on the user ratings. The filtering is done by using the well-known algorithm

![](bbox=[0.2, 0.665, 0.8, 0.895])

Figure 6.4 KNN - algorithm for book recommendation.