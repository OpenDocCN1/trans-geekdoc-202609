# ## 20.3.3 THE ZONE PROFILE

Each racer is designated a zone profile. A zone is an area on the racetrack where attributes can be manipulated. A zone does not necessarily need to be a static location. It can be an area around another AI vehicle.

This profile contains attributes for defining their pure driving skill. This boils down to three values. The main being a skill percentage which essentially gives you the ability to scale up or down the default maximum speed a vehicle can travel at. The remaining two values are a start and end distance, and these were defined when the zone was in operation. The distance itself is the distance from the racer they are tracking. An example of this can be seen in Table 20.1.

TABLE 20.1
Example Zone Profiles

| Zone Name | AI Skill Multiplier | Start Distance | End Distance |
|---|---|---|---|
| IN FRONT OF RACER | 0.9 | 300 | 500 |
| AROUND RACER | 0.9 | -300 | 300 |
| BEHIND RACER | 1.0 | -600 | -300 |

To briefly go through the details in Table 20.1, it states that if the AI can get 300 metres in front of the car they are tracking, then the zone “IN FRONT OF PLAYER” is activated, likewise if the AI drops behind the tracked player, then the “BEHIND PLAYER” zone would kick in. You can see that the behind-player zone would increase the skill of the AI, thus giving the AI a chance to catch up.

A general rule for any of these zones is that if a human player is within close proximity, then there should be no cheating going on. The whole idea behind this is to mask the fact that the AI is dynamically adapting to how a human player is performing.

The AI Skill Multiplier can also be greater than 1! This will technically allow the AI to cheat but it gives the design team the flexibility to increase the top speeds within reason – if the human players do not notice of course!

# ## 20.3.4 ASSIGNING PROFILES

The final piece of the puzzle is assigning these profiles to each racer. To do this, you need a table with a column for each racer. In Sonic & All Stars Racing Transformed, rather than assigning a profile to a specific racer, it was decided to assign them to races in certain positions which allowed for a shuffled-up starting grid and also provided more variety. This system is also dynamic in that the profile for each racer can be assigned based on their position. If the best AI at the time is hit and therefore drops down to last place, rather than them suddenly trying to regain first place, they can inherit the last place profile.