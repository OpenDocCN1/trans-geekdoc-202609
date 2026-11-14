and will always be a bad option for a pass. It is in these situations where AI awareness becomes invaluable.

Awareness of opposing players is achieved by allowing each player to retain their own local information about their opponents. This local information is what they think about the opponent and not actual information. By refreshing this data periodically, you ensure players have a degree of awareness but also allow players to react more slowly to developments on the field.

To achieve this, a list of structs is required per player, where each struct in the list refers to an opponent. The struct contains the following details:

+   - Player ID
+   - Last known position
+   - Estimated position
+   - Direction
+   - Velocity
+   - Current refresh time
+   - Refresh duration

The idea is that each player will keep track of where they think the opponents are on the field. So, at the start of the game, each struct will be populated with the exact details of the opponent in question. As a play progresses, the player will refresh the struct with accurate positional data when they look at that player or when the refresh time has expired. At all other times, the data in each struct will be updated with a guess as to where the player thinks the opponent will be. This is achieved by taking their direction and velocity and calculating what position on the field they would be if they had continued with that trajectory.

Take a look at Image 8.1. The player in black is a Cornerback and is looking to defend any throws to the Wide Receiver behind them. The Cornerback looks to position themselves between the Quarterback and the Wide Receiver, usually a yard or two away from the Wide Receiver. The image also shows the route the Wide Receiver is planning to take. The Cornerback does not have this information and should react to developments as they play out on the field. At this stage, the Cornerback stores the position of the Wide Receiver, the direction he is running and his speed and then sets the refresh counter ticking.