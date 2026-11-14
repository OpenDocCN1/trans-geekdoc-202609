![](bbox=[0.19, 0.09, 0.8, 0.46])

# IMAGE 3.3 Delivering signature.

| Signature: Create | Signature: Create | Signature: Repair |
|---|---|---|
| Action: Craft | Action: Craft | Action: Repair |
| Subject: Craft Bench | Subject: Blueprint | Subject: Repairable |

# IMAGE 3.4 Crafting signature.

The concept of None, with regard to the subject on which an Action is performed, can be interpreted in different ways depending on the task in question. For example, repairing None subjects is interpreted as repairing everything that is damaged, whereas delivering to a None subject is interpreted as delivering to a specific single location on the ground. This will be discussed further when elaborating more on how behaviours are defined a little later in this chapter.

# 3.4 ACTING

The Survivalists features an Actor and Actions framework in which every character, player-controlled or NPC, has an actor component, providing an interface through which actions are requested. Actions define the atomic activities that a character can perform, such as pick up an item, drop an item, perform an attack, interact with an object or craft an item, each with prerequisites for whether they can be performed. These prerequisites include checks for other actions being currently active, particular