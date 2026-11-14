A typical race profile for an easy race would look something like Table 20.2. The most important row that underpins the logic is “TargetPlayer”. This is the player that each AI will use as reference for their zone profile. You can see that the AI in first would track the best human player, the others would track the best AI player, the idea being that the best AI will dictate the pace for the rest of the AI to achieve some semblance of order. Should an AI come off track or be hit, then they will just slot into the relevant profile based on their position. This gives the design team a fair degree of control over how a race will pan out.

# TABLE 20.2
A Typical Race Profile in Sonic & All Stars Racing Transformed

| Attribute | AI Position 1st | AI Position 2nd | AI Position 3rd | AI Position 4th | AI Position 5th |
|---|---|---|---|---|---|
| Weapons profile | Easy | Easy | Easy | Easy | Easy |
| Default car skill | 0.8 | 0.7 | 0.6 | 0.5 | 0.4 |
| Default boat skill | 0.8 | 0.7 | 0.6 | 0.5 | 0.4 |
| Default aircraft skill | 0.8 | 0.7 | 0.6 | 0.5 | 0.4 |
| Default zone profile car | Easy | Easy | Easy | Easy | Easy |
| Default zone profile boat | Easy | Easy | Easy | Easy | Easy |
| Default zone profile aircraft | Easy | Easy | Easy | Easy | Easy |
| Handling profile | Default | Default | Default | Default | Default |
| Target player | BestHuman | BestAI | BestAI | BestAI | BestAI |
| Pick shortest route probability | 0.2 | 0.1 | 0.1 | 0 | 0 |

# 20.3.5 RACE SEGMENTATION

There are a couple of important things missing – these being the behaviour at the start of a race and behaviour during a race. When developing *Sonic & All Stars Racing Transformed*, the design team had expressed an interest in making the race difficulty dynamic, so that even an easy race might begin with the AI being more difficult to race but on the final lap they could ease off and give the human player the satisfaction of just beating the AI as they cross the finish line. To achieve this, a simple concept was added to the race profile. The race itself could be split into segments, these segments would define a percentage of the overall race distance and would allow zone profiles and weapons profiles to be altered. No two tracks will be the exact same length, so using percentages allowed for a race profile to be applied to any track and reduced the game data required. These segment profiles can be applied to all racers or specific racers as required. An example is shown in Table 20.3.