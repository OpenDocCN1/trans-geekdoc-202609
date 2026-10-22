# 9.2.3 Typed Access-Control Model.

A variant of the access-control matrix model adds type to the entities. The typed access-control matrix model, called TAM, associates a type with each entity and modifies the rules for matrix manipulation accordingly. This notion allows entities to be grouped into finer categories than merely subject and object, and enables a slightly different analysis than the HRU result suggests.

In TAM, a rule set is acyclic if neither an entity E nor any of its descendants can create a new entity with the same type as E. Given that definition:

**Theorem.** There is an algorithm that will determine whether acyclic, monotonic typed matrix models are secure with respect to a generic right r.

Thus, a system being acyclic and monotonic is sufficient to make the safety question decidable. But we still do not know exactly what properties are necessary to make the safety question decidable.

We now turn to models that have direct application to systems and environments and that focus on more complex definitions of “secure” and the mechanisms needed to achieve them.

# 9.3 MODELS AND CONTROLS.

Models of computer security focus on control: who can access files and resources, and what types of access are allowed. The next characterizations of these controls organize them by flexibility of use and by the roles of the entities controlling the access. These are essential to understanding how more sophisticated models work.

# 9.3.1 Mandatory and Discretionary Access-Control Models.

Some access-control methods are rule based; that is, users have no control over them. Only the system or a special user called (for example) the system security officer (SSO) can change them. The government classification system works this way. Someone without a clearance is forbidden to read TOP SECRET material, even if the person who has the document wishes to allow it. This rule is called mandatory because it must be followed, without exception. Examples of other mandatory rules are the laws in general, which are to be followed as written, and one cannot absolve another of liability for breaking the laws; or the Multics ring-based access-control mechanism, in which accessing a data segment from below the lower bound of the segment’s access bracket is forbidden regardless of the access permissions. This type of access control is called a mandatory access control, or MAC. These rules base the access decision on attributes of the subject and object (and possibly other information).

Other access-control methods allow the owner of the entity to control access. For example, a person who keeps a diary decides who can read it. She need not show it to anyone, and if a friend asks to read it, she can say no. Here the owner allows access to the diary at her discretion. This type of control is called discretionary. Discretionary access control, or DAC, is the most common type of access-control mechanism on computers.

Controls can be (and often are) combined. When mandatory and discretionary controls are combined to enforce a single access-control policy, the mandatory controls are applied first. If they deny access, the system denies access and the discretionary controls need never be invoked. If the mandatory rules permit access, then the discretionary controls are consulted. If both allow the accesses, access is granted.

# 9.3.2 Originator-Controlled Access-Control Model and DRM.

Other types of access controls contain elements of both mandatory and discretionary access