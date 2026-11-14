```
Code Listing 18.3: A Steal action.

(:action Steal
  :parameters (?p - Player ?enemy - Enemy ?steal_loc - Location ?item - Item)
  :precondition (and
    (at ?p ?steal_loc)
    (at ?enemy ?steal_loc)
    (> #(amount ?key ?enemy) 0))
  :effect (and
    (decrease #(amount ?key ?e) 1)
    (increase #(amount ?key ?p) 1))
)
```

# 18.3.3.4 Open

The open action is depicted in Code Listing 18.4. With this action, players use the items that they have in their inventory to open doors. A player is required to be at a location where it can interact with a door, (interaction_loc). This location also informs what key they need to use. It also determines what location is on the other_side of the door that can be moved to after opening the door.

```
Code Listing 18.4: An Open action.

(:action Open
  :parameters (?p - Player ?door - Door ?interact_loc ?other_side - Location ?key - Item)
  :precondition (and
    (at ?p ?interact_loc)
    (blocks ?door ?interaction_loc ?other_side)
    (requires ?door ?key ?interaction_loc)
    (> #(amount ?key ?p) 0))
  :effect (and
    (not (blocks ?door ?interaction_loc ?other_side))
    (not (blocks ?door ?other_side ?interaction_loc))
    (connected ?other_side ?interaction_loc)
    (connected ?interaction_loc ?other_side)
    (decrease #(amount ?key ?p) 1))
)
```

# 18.3.4 Example Problem

The objects that are part of this problem are depicted in Image 18.3. The connectivity between the locations is depicted with solid lines. The dotted lines depict locations that are blocked by a door.