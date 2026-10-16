# # Time

You can find all the code for this chapter here

The product owner wants us to expand the functionality of our command line application by helping a group of people play Texas-Holdem Poker.



You won't need to know much about poker, only that at certain time intervals all the players need to be informed of a steadily increasing "blind" value.

Our application will help keep track of when the blind should go up, and how much it should be.

+   - When it starts it asks how many players are playing. This determines the amount of time there is before the "blind" bet goes up.
+     - There is a base amount of time of 5 minutes.
+     - For every player, 1 minute is added.
+     - e.g 6 players equals 11 minutes for the blind.
+   - After the blind time expires the game should alert the players the new amount the blind bet is.
+   - The blind starts at 100 chips, then 200, 400, 600, 1000, 2000 and continue to double until the game ends (our previous functionality of "Ruth wins" should still finish the game)



In the previous chapter we made our start to the command line application which already accepts a command of {name} wins. Here