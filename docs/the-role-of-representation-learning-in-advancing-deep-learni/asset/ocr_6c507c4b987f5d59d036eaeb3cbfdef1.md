# E.2.6 Early Episode Termination

Most of the puzzles in PUZZLES do not have an upper bound on the number of steps, where the only natural end can be reached via successfully solving the puzzle. The PUZZLES environment also provides the option for early episode termination based on state repetitions. If an agent reaches the exact same game state multiple times, the episode can be terminated in order to prevent wasteful continuation of episodes that no longer contribute to learning or are bound to fail.

# E.3 PUZZLES Implementation Details

In the following, a brief overview of PUZZLES's code implementation is given. The environment is written in both Python and C, in order to interface with Gymnasium [92] as the RL toolkit and the C source code of the original puzzle collection. The original puzzle collection source code is available under the MIT License.1 In maintext Figure 8.2, an overview of the environment and how it fits with external libraries is presented. The modular design in both PUZZLES and the Puzzle Collection’s original code allows users to build and integrate new puzzles into the environment.

**Environment Class** The reinforcement learning environment is implemented in the Python class PuzzleEnv in the rlp package. It is designed to be compatible with the Gymnasium-style API for RL environments to facilitate easy adoption. As such, it provides the two important functions needed for progressing an environment, reset() and step().

Upon initializing a PuzzleEnv, a 2D surface displaying the environment is created. This surface and all changes to it are handled by the Pygame [53] graphics library. PUZZLES uses various functions provided in the library, such as shape drawing, or partial surface saving and loading.

The reset() function changes the environment state to the beginning of a new episode, usually by generating a new puzzle with the given parameters. An agent solving the puzzle is also reset to a new state. reset() also returns two variables, observation and info, where observation is a Python dict containing a NumPy 3D array called pixels of size (3 × surface_width × surface_height). This NumPy array contains the RGB pixel data of the

1 The source code and license are available at https://www.chiairk.greend.org.uk/~sgtatham/puzzles/.