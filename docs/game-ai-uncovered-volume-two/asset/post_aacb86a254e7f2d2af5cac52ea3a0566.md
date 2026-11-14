
and will always be a bad option for a pass. It is in these situations where AI awareness becomes invaluable.

Awareness of opposing players is achieved by allowing each player to retain their own local information about their opponents. This local information is what they think about the opponent and not actual information. By refreshing this data periodically, you ensure players have a degree of awareness but also allow players to react more slowly to developments on the field.

To achieve this, a list of structs is required per player, where each struct in the list refers to an opponent. The struct contains the following details:

- Player ID
- Last known position
- Estimated position
- Direction
- Velocity
- Current refresh time
- Refresh duration

The idea is that each player will keep track of where they think the opponents are on the field. So, at the start of the game, each struct will be populated with the exact details of the opponent in question. As a play progresses, the player will refresh the struct with accurate positional data when they look at that player or when the refresh time has expired. At all other times, the data in each struct will be updated with a guess as to where the player thinks the opponent will be. This is achieved by taking their direction and velocity and calculating what position on the field they would be if they had continued with that trajectory.

Take a look at Image 8.1. The player in black is a Cornerback and is looking to defend any throws to the Wide Receiver behind them. The Cornerback looks to position themselves between the Quarterback and the Wide Receiver, usually a yard or two away from the Wide Receiver. The image also shows the route the Wide Receiver is planning to take. The Cornerback does not have this information and should react to developments as they play out on the field. At this stage, the Cornerback stores the position of the Wide Receiver, the direction he is running and his speed and then sets the refresh counter ticking.

![](img/f4a4f6e4de5338a867590c30638990cf_90_0.png)

IMAGE 8.1 Awareness based on the exact data at the start of a play.

When the play starts, the Wide Receiver takes off running and the Cornerback needs to react. If their awareness refresh rate is too long, the location where they think the Wide Receiver is may be correct, but they could also be wrong. The example shown in Image 8.2 has the opponent zigzagging behind, which means the Cornerback is now defending the wrong position. The Wide Receiver has created the separation required to allow the Quarterback to make the pass, and this had little to do with the speed of either player.

![](img/f4a4f6e4de5338a867590c30638990cf_91_0.png)

IMAGE 8.2 Awareness resulting in the player defending the wrong position.

### 8.2.1 REFRESH RATE

The refresh rate has a big impact on the perceived intelligence of a player. There are three forms of refresh rate awareness. The first approach is to refresh each opponent’s struct based on the timer. The second approach is to use an overall refresh rate, which resets all opponent data to be accurate when the refresh occurs. Both approaches can be enhanced by incorporating an awareness stat for that particular player (the observing player). An awareness stat is a value between 0 and 1, with 0 indicating a player with great awareness and a 1 indicating a player with a low awareness span. The refresh time for the observing player is then set as the maximum refresh time multiplied by this stat. Therefore, a player with an awareness stat of 0 will have a refresh rate of 0.0 seconds, meaning they get the most up-to-date information every frame. A player with a stat of 1 will have a refresh rate set to whatever the maximum refresh time is. Around 0.6 seconds worked for us.

The third approach to refreshing the data is the field of view approach. If a player can see an opponent, then that opponent’s data gets refreshed immediately and they have the most up-to-date information on that opponent. Other opponents that are not within the field of view are only updated when the refresh time has passed (approach one or two). This approach emulates when a player would cast a glance around the field to ensure they know where an opponent is. Adding an animation to do this would also help to sell the illusion.

By combining these approaches, you get the desired result of seeing players running behind or out of sight and getting away from their predicted route and creating separation. Players look reactive and as though they are attempting to handle the threat in the correct manner, and no player has an opponent or teammate that is so far out of date that they appear to be stupid. If you expose the awareness stat to the human player, they are fully aware of why their team is reacting slower to threats. By incorporating training into your game, which will increase this stat, you have a ready-made feedback loop that keeps the player playing your game, and just as importantly, understanding why the AI plays the way it does.

## 8.2 CONSIDERATIONS

You may find that using the auto refresh when an opponent is in the observing player’s field of view kills off this approach to positional awareness. Especially, if the sport in question is one where teams are on opposing sides of the field and therefore a player can see the majority of the opponents. If this is the case, you may find that removing the field-of-view approach and just going with one of the refresh rate approaches works well. This approach also makes incorporating difficulty settings easier.

When implementing such an approach, it is crucial that any decisions by the AI are made using the awareness positions. Quite often, there will be other ways of getting a position for an opponent, but the problem is these ways result in the actual position of the opponent. So, when other gameplay programmers are implementing mechanics, they should query the same structs; otherwise, it appears as though the player suddenly knows exactly where the opponent is. It can look odd and can appear as though the AI is cheating.

## 8.3 THREAT AWARENESS

Another area of player awareness that impacts AI sports people is how to determine which opponents are deemed as threats. Whether on Offence or Defence, the opposing players pose a threat to the goal of the team. How these threats are assessed is an important aspect of the awareness of each player on the field.

When looking at the AI for a Cornerback, if the player they are marking crosses paths with another player, it is for them to decide which one to mark. Do they stay with the Wide Receiver they started with, but who has now headed into the centre of the field where a teammate could cover them, or do they stop marking their target and pursue the opponent that is now heading to the edge of the field. Different players will do different things depending upon the scenario, but in video games, the AI needs to look like they are at least making smart decisions.

### 8.3.1 Threat Filters

To ensure code is reusable and compartmentalised, the concept of a threat filter was developed. Different AI behaviours use as many or as few filters as required, and these are detailed in the next section. When assessing threats, the observing player stores an array of values (one for each opposing player on the field) which indicates the weighting of the threat. At each update, the weighting is set to a value of zero before the available filters are processed. Each individual filter will modify this weight based on the criteria of the threat. Each threat can return a maximum value of one, but in most cases will return a weighting for that filter. The weighting is a tweakable value that can be set by design but can never exceed one. When all filters have been processed, the accumulated weight is divided by the number of filters to give a threat value between 0 and 1. The observing player will now understand which opposing players are the greatest threat to their team.

There are a wide variety of different threat filters that can be applied, and only a subset of those used is described below. What is important is that each filter handles one assessment, and more complex assessments are made by layering up filters.

### 8.3.1.1 Distance of the Opponent to the Ball Carrier Filter

If the observing player is on the Offence, it is their job to protect their teammate who is running with the ball. To identify if an opponent is a threat to the ball carrier, the distance between the ball carrier and the opposing player being analysed is divided by a maximum distance to give a 0 to 1 value.

### 8.3.1.2 Distance of the Opponent to the Observing Player Filter

At times, the distance of an opposing player to the agent assessing the threat is an important factor. Those closer are deemed a higher threat than those further away. For example, the observing player could be the ball carrier who wants to make as many yards uphill as they can before they are brought down. If this threat is available to the behaviour, then the distance between the observing player and the opposing player being analysed is divided by a maximum distance to give a 0 to 1 value.

### 8.3.1.3 Distance of the Opponent to the Endzone Filter

If the opposing team has the ball, the distance of the ball carrier to the end zone is a huge consideration. The closer they are to the end zone, the greater the threat. When incorporating this filter into the threat analysis, the distance between the ball carrier and the endzone is divided by a maximum distance to give a 0 to 1 value.

### 8.3.1.4 Positioning upfield to the Ball Carrier Filter

When the observing player's team does not possess the ball, it is important for them to stop the ball carrier from making yards. If they are ahead of the ball carrier, they should treat the ball carrier as a threat, but if they are already behind the ball carrier, and there is little chance of them catching up, then there is little they can do. For this filter, the field position of the observing player is compared to that of the ball carrier's position. If they are upfield of the ball carrier (they are between the ball carrier and the end zone), the threat value is set to the weighting for this threat, otherwise it is scaled down to zero depending upon the distance away.

### 8.3.1.5 Opponent Positioning inside Zone Filter

For players that have a zone to protect, any opposing player within that zone is deemed a threat. Any opposing player inside the zone controlled by the observing player returns the weighting for this threat, and any opposing player not inside the zone returns a value of zero.
