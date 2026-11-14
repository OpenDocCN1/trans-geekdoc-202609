following the racing line, or taking all the shortcuts, did not always result in the fastest route around the track since the game also featured boost pads, which were often placed away from the racing line with an element of risk in taking them. The AI needs to consider these to ensure they remain competitive.

Part of the AI following logic in karting games is the ability for the racing line to be semi-dynamic. In other words, it continually looks at the track ahead and patches in additional sections of the racing line for things to avoid or pick up. This means that boost pads can be taken if desired. This gives another lever for adjusting AI difficulty.

With competitive racers in place, the next area to look at is pickups and weapons. Since Mario Kart, these have been a staple of karting games. Sonic & All Stars Racing Transformed featured a variety of pickups with most of them requiring some skill to use. No Mario-style blue shells for Sonic. For each weapon, the AI was given a unique behaviour which could be scaled to their skill level and depended on the difficulty settings. Tweaking these values created an engaging player experience. The game itself had a standard race option with easy, medium, and hard difficulties, but it also had a world tour where you would be introduced to the game with progression getting increasingly more difficult. Designers will undoubtedly require the ability to script the desired outcome of a race. This is where the Race Director comes in.

# 20.3 RACE DIRECTOR

The basic concept of the Race Director is that each AI racer has a profile which allows you to define the following:

# 20.3.1 THE WEAPONS PROFILE

The weapons profile contains all the tweakables for an AI using weapons or pickups. You could have an unlimited number of these profiles and apply them to any AI vehicle. For simplicity, assume that you only have easy, medium, and hard. Each profile would dictate distances at which weapons would be fired, the probability of missing the target and cool-down timers. You can even have separate values to distinguish between AI attacking other AI and human racers. All of these subtleties give you the ability to adjust the difficulty without it being obvious to the player.

# 20.3.2 THE HANDLING PROFILE

Each racer will require a handling profile. These are not necessarily tied to difficulty and are simply a way to dictate the various driving parameters for an AI racer and the various vehicle types. Sonic & All Stars Racing Transformed had three types – Land, Sea, and Air. These profiles include such things as look ahead distances, drift parameters, and the like and featured twenty four different characters. Handling profiles gave the ability to tweak individual vehicles if required. For vehicle types using the same handling model, a default set-up can be sufficient, but the option is still there if needed. Always better to have flexibility in a system!