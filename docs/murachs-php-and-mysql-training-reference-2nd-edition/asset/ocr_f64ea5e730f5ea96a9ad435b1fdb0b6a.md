# The controller

Part 2 of figure 22-9 shows the code for the controller for the YouTube Search application. This code processes any form data and then loads an appropriate view file to display that data to the user.

The controller starts by requiring the helper file that defines the send_email function that's in figure 22-4. Then, it starts a session for the application.

The controller then creates a function named search_youtube that takes a search string as its parameter. Within this function, the code uses cURL to retrieve the search results from the YouTube API and return an array of videos that match the search string.

The first if statement checks the action that was retrieved from the $_POST array. If the action hasn't been set, it sets the action to a default of “search”.

The second if statement checks the query that was retrieved from the $_POST array. If the query has been set, this code updates the value of the query in the $_SESSION array. Otherwise, this code gets the query from the $_SESSION array. However, if neither the $_POST nor $_SESSION arrays have a query parameter, this code sets the query to a default value of an empty string.

The switch statement executes the appropriate code based on the value of the $action variable. If the action is “search”, the code checks whether the $query variable is empty. If not, it executes the search_youtube function to get an array of videos. Otherwise, it initializes the videos array. Then, this code loads the Search view.

If the action is “display_email_view”, the code retrieves the url and text for the video from the $_POST array. Then, it includes the Email view to display the form for emailing a YouTube link.