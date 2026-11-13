# Evaluating success criteria in “Automated grading tool” (credit: former student)

The program can automatically mark a multiple-choice paper with above 99% accuracy by comparing it to the mark scheme.

![](bbox=[0.49, 0.1, 0.68, 0.275])

The program marked 30 out of 30 sample tests correctly. The client has confirmed that “Under good lighting conditions, this seems to work very well” (Appendix A.3).

# Evaluating success criteria in “IBDP subject recommender” (credit: Sofia Coru)

Application makes use of a graphical user interface to facilitate the inputting of personal information (the user can input this information through textboxes, checkboxes and choice boxes / drop-down select).

![](bbox=[0.49, 0.315, 0.68, 0.425])

All of the data is either input by selecting from a drop-down select menu or by ticking checkboxes (as shown in visuals). My client stated that he thought the students found the inputting process “intuitive” and “quite self-explanatory” (Appendix E.1).

One of the improvements that my client and I discussed was the ability of the application to save features that had been input into the drop-down boxes, “even if the user were to go to a different page” (Appendix 4). As of now, the characteristics that have been entered disappear when the user clicks on the help page. To address this, an array can be made. When the help button is clicked, the chosen characteristics can be immediately saved to the array. Then, when the user returns to the "enter characteristics" page, they can seamlessly continue inputting additional characteristics that will be saved in the same array. The contents can then be sent to the neural network for processing.

Secondly, my client disliked that the application was “reliant on WiFi” to function. To fix this issue, the machine learning algorithm could be configured to run independently on the local system. The appropriate libraries (for example scikit-learn and NumPy) would have to be set up, and the h5 file containing the machine learning model would be downloaded on to my client’s phone.

Thirdly, my client suggested that entering 21 characteristics for each mushroom was “tedious”. To fix this, the importance of each feature could be calculated. A method to approach this is detailed by Fisher et al. Essentially, the value of a feature should be randomized and the accuracy of the model computed. This process can be repeated for each feature, and the ones with the lowest importance can be removed.

Finally, to enhance the educational aspect of the app, functionality can be added to provide guesses about the mushroom species. This can be achieved by creating a database that contains the characteristics of 50 common mushroom species. Each mushroom in the database would initially have a score of 0. When the user inputs characteristics, the app can compare them with the characteristics in the database. For each matching characteristic, the score of the corresponding mushrooms in the database can be incremented. The mushrooms with the highest scores can then be presented as guesses for the species of mushroom the user is trying to identify.

# Suggested improvements in “Mushroom: Friend or foe?” (credit: H Ng)