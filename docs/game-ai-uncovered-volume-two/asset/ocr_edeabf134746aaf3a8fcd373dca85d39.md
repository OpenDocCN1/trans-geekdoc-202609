movement such as a smoothly animated U-turn. In this scenario, the agent is either on what is thought to be a valid nav-mesh path or outside of the nav-mesh, so this cannot be resolved by repathing.

# 14.2.2 TELEPORTATION

Teleportation is a potential solution to the problem of an agent being stuck. It is a very powerful and easy-to-implement approach, but one that can produce some highly undesirable results. It is worth remembering that the agent is potentially in a situation where it is stuck without a reasonable way of extricating itself. If you do decide to teleport, where should that agent go? Teleportation can be handled at the path-following level by moving the agent to the next waypoint or even to the end of the path. Another reasonable teleportation target location is to a known good location. For example, where a friendly agent is located or straight to the target hostile. A hostile NPC that teleports to the exact location of the player can be very frustrating so it is something to avoid if possible. The value of teleportation depends greatly on how much you trust that the position the agent would teleport to is valid for what it is trying to accomplish. What if the agent is stuck because the next waypoint is blocked by a solid object which it will now teleport inside? Or if teleporting to the end of the path means that it would teleport outside of the currently loaded physics and fall through the world? Teleporting is also likely to cause the agent to skip important triggers in the world. Teleportation should be considered as a last resort. There are other approaches we should try first.

# 14.2.3 LERPING

Some situations might allow you to linearly interpolate (lerp) the agent’s position towards a goal. One important advantage of this approach is that it greatly reduces the risk that the agent misses important world triggers. Another advantage is that it is slower giving other systems (such as loading) enough time to respond. A major drawback is that it is even more likely than teleportation to put the agent in a state inside of or intersecting with another object, at least temporarily, given a likely reason for lerping would be that the agent is blocked by the object we are about to lerp through.

# 14.2.4 AGENT RESET

The worst-case scenario and very last resort is to simply de-spawn or kill off the agent. However, this does allow for a restart of the scenario, or perhaps to spawn in another agent, or if the agent being removed was insignificant, do nothing.

# 14.2.5 INPUT SPAM

For input-driven test bots, it has worked surprisingly well across many titles to simply press some combination of Jump, Sprint, Vault, Interact, Open Door, or whatever similar actions are available. This allows the agent to deal with obstacles in a way very similar to how a player would. It might be worth trying to detect the specific