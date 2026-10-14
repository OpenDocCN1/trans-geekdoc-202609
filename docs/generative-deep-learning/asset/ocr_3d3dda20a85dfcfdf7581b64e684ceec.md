Let's see how the game state, action, reward, and episode are defined for the `CarRacing` environment:

# Game state

A 64 × 64-pixel RGB image depicting an overhead view of the track and car.

# Action

A set of three values: the steering direction (−1 to 1), acceleration (0 to 1), and braking (0 to 1). The agent must set all three values at each timestep.

# Reward

A negative penalty of −0.1 for each timestep taken and a positive reward of 1,000/ N if a new track tile is visited, where N is the total number of tiles that make up the track.

# Episode

The episode ends when the car completes the track or drives off the edge of the environment, or when 3,000 timesteps have elapsed.

These concepts are shown on a graphical representation of a game state in Figure 12-2.

![](bbox=[0.14, 0.45, 0.88, 0.74])

Figure 12-2. A graphical representation of one game state in the CarRacing environment

![](bbox=[0.17, 0.79, 0.24, 0.86])

# Perspective

We should imagine the agent floating above the track and controlling the car from a bird's-eye view, rather than viewing the track from the driver's perspective.

The track is divided into N invisible "tiles." The agent receives a reward of 1,000/N every time it discovers a new track tile and also a penalty of -0.1 every timestep.

The agent must decide the value to set for three actions.