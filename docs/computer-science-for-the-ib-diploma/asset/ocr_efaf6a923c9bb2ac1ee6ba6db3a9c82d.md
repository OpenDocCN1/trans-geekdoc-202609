![](bbox=[0.273, 0.083, 0.882, 0.352])

+   - Class relationships UML

# Structure chart identifying the key components of the decomposed project:

![](bbox=[0.273, 0.4, 0.882, 0.735])

+   - Structure chart

# Further descriptions of the key components in the structure chart:

+   - **Game management**: This module handles the core loop and initialization, making sure the game starts and ends appropriately.

+   - **Player management**: Manages everything related to the player character, from avatar customization to handling movements based on keyboard inputs.

+   - **Map management**: Responsible for loading different maps and managing elements within them, including transitioning between different difficulty levels.

+   - **Ghost management**: Controls the ghosts’ behaviour, utilizing an A-star algorithm for pathfinding and deciding their movement strategy based on the current difficulty level.

+   - **Scoring system**: Manages the scoring, including calculating scores based on game events (e.g. eating fruits) and handling high scores’ storage and retrieval.