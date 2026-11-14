courtyard space within the overall boundary of the Manor house. If this had its own room volume, marked as outdoors, and an agent stood here, they would be nested three volumes deep, and because the courtyard "room" is the smallest, they are now outdoors again.

As you can tell from the examples, this is a very simple but powerfully clever markup system that NPCs can make good use of, and if your game world is unusually small, and rarely modified, this might be enough for your game. However, "unusually small" and "rarely modified" do not apply to a large majority of games in development! You could not, for example, expect the level designers to go through and mark up every room and every building in a *Grand Theft Auto 5*-scale open world, and then realistically expect them to stay on top of the multitudes of trigger volumes as the game world inevitably changes during development. It would be nice to fall back on this manual markup system for distinctly bespoke cases, but ideally, you need to supply the design team with a system that can maintain itself as best it can when environments are tweaked, and even supply as much automated environmental markup as it can without even needing to stick virtual signposts down.

# ## 16.3 ANALYSING THE ENVIRONMENT USING VOXELS

There are multiple methods of terrain analysis you could use to aid in automating manual markup, but a robust and classic method is the octree, to subdivide the environment into voxels. It might even already be happening in your game engine, for use by rendering or illumination systems, which means you may even be able to leverage some shared technology for the AI systems.

Either way, what you need out of the octree is to subdivide the space so that you end up with a voxelised region of the environment where you have a set of voxels overlaying collision (closed voxels) and a set of voxels occupying navigable spaces (open voxels). Once you have this, you can use the current position of an NPC to query for their currently occupied open voxel and start to mark up and interrogate these voxels for spatial information.

# ## 16.4 GENERATION PHASES

The complete environmental markup process can take place offline, and the data generated can be saved and stored as a binary data file. However, there may be situations where some or all of the data would need to be regenerated at runtime if the environment is modified.

A generation phases look like this, and each of these stages will be explored in more detail next:

+   1. Generate the octree, and all open and closed voxels, using user-defined seed bounds.
+   2. Cull any voxel that ends up fully outside the seed bounds after generation.
+   3. Perform interior tests on open voxels.
+   4. Propagate markup seeds throughout the voxel space.
+   5. Inherit the tagging of any markup bounds into the voxel space.