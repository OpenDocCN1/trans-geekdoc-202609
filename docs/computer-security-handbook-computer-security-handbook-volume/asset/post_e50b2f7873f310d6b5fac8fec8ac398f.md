
## 9.4 MATHEMATICAL MODELS OF COMPUTER SECURITY

|  | Process 1 | Process 2 | File 1 | File 2 |
|---|---|---|---|---|
| **Process 1** | own | read | read, execute | read, write, own |
| **Process 2** | write | own | read, write, execute, own | read |

**EXHIBIT 9.1** Example Access-Control Matrix with Two Processes and Two Files

access-control matrix must change to reflect this evolution. Perhaps the simplest set of rules for changing the access-control matrix are these *primitive operations*⁴:

- **Create subject** *s* creates a new row and column, both labeled *s*
- **Create object** *o* creates a new column labeled *o*
- **Enter** *r* **into** *A[s, o]* adds the right *r* into the entry in row *s* and column *o*; it corresponds to giving the subject *s* the right *r* over the entity *o*
- **Delete** *r* **from** *A[s, o]* removes the right *r* from the entry in row *s* and column *o*; it corresponds to deleting the subject *s*’s right *r* over the entity *o*
- **Destroy subject** *s* removes the row and column labeled *s*
- **Destroy object** *o* removes the column labeled *o*

These operations can be combined into *commands*. The next command creates a file *f* and gives the process *p* read and own rights over that file:

```
command createread(p, f)
        create object f
        enter read into A[p, f]
        enter own into A[p, f]
end.
```

A *mono-operational command* consists of a single primitive operation. For example, the command

```
command grantwrite(p, f)
        enter write into A[p, f]
end.
```

which gives *p* write rights over *f*, is mono-operational.

Commands may include conditions. For example, the next command gives the subject *p* execute rights over a file *f* if *p* has read rights over *f*:

```
command grantexec(p, f)
        if read in A[p, f] then
                enter execute into A[p, f]
end.
```

If *p* does not have read rights over *f* when this command is executed, it does nothing. This command has one condition and so is called *monoconditional*. *Biconditional* commands have two conditions joined by *and*:

```
command copyread(p, q, f)
        if read in A[p, f] and own in A[p, f] then
                enter read into A[q, f]
end.
```

### 9.2.3 Typed Access-Control Model.

A variant of the access-control matrix model adds type to the entities. The typed access-control matrix model, called TAM, associates a type with each entity and modifies the rules for matrix manipulation accordingly. This notion allows entities to be grouped into finer categories than merely subject and object, and enables a slightly different analysis than the HRU result suggests.

In TAM, a rule set is acyclic if neither an entity E nor any of its descendants can create a new entity with the same type as E. Given that definition:

**Theorem.** There is an algorithm that will determine whether acyclic, monotonic typed matrix models are secure with respect to a generic right r.

Thus, a system being acyclic and monotonic is sufficient to make the safety question decidable. But we still do not know exactly what properties are necessary to make the safety question decidable.

We now turn to models that have direct application to systems and environments and that focus on more complex definitions of “secure” and the mechanisms needed to achieve them.

## 9.3 MODELS AND CONTROLS.

Models of computer security focus on control: who can access files and resources, and what types of access are allowed. The next characterizations of these controls organize them by flexibility of use and by the roles of the entities controlling the access. These are essential to understanding how more sophisticated models work.

### 9.3.1 Mandatory and Discretionary Access-Control Models.

Some access-control methods are rule based; that is, users have no control over them. Only the system or a special user called (for example) the system security officer (SSO) can change them. The government classification system works this way. Someone without a clearance is forbidden to read TOP SECRET material, even if the person who has the document wishes to allow it. This rule is called mandatory because it must be followed, without exception. Examples of other mandatory rules are the laws in general, which are to be followed as written, and one cannot absolve another of liability for breaking the laws; or the Multics ring-based access-control mechanism, in which accessing a data segment from below the lower bound of the segment’s access bracket is forbidden regardless of the access permissions. This type of access control is called a mandatory access control, or MAC. These rules base the access decision on attributes of the subject and object (and possibly other information).

Other access-control methods allow the owner of the entity to control access. For example, a person who keeps a diary decides who can read it. She need not show it to anyone, and if a friend asks to read it, she can say no. Here the owner allows access to the diary at her discretion. This type of control is called discretionary. Discretionary access control, or DAC, is the most common type of access-control mechanism on computers.

Controls can be (and often are) combined. When mandatory and discretionary controls are combined to enforce a single access-control policy, the mandatory controls are applied first. If they deny access, the system denies access and the discretionary controls need never be invoked. If the mandatory rules permit access, then the discretionary controls are consulted. If both allow the accesses, access is granted.

### 9.3.2 Originator-Controlled Access-Control Model and DRM.

Other types of access controls contain elements of both mandatory and discretionary access

(CONFIDENTIAL, {EUR}), and the paper AsiaDoc may be (SECRET, {ASIA}). The paper EurAsiaDoc contains information about both Europe and Asia, and so would be in compartment (SECRET, {EUR, ASIA}). As before, we write level(Erin) = (SECRET, {EUR}), level(EurDoc) = (CONFIDENTIAL, {EUR}), and level(EurAsiaDoc) = (SECRET, {EUR, ASIA}).

Next, we must define the analog to “greater than.” As noted earlier, security compartments are no longer linearly ordered, because not every pair of compartments can be compared. For example, Don’s compartment is not “greater” than Erin’s, and Erin’s is not “greater” than Don’s. But the classification of EurAsiaDoc is clearly “greater” than that of both Don and Erin.

We compare compartments using the relation dom for “dominates.”

Definition. Let L and L′ be security levels and let C and C′ be category sets. Then

(L, C) dom (L′, C′) if and only if L ≥ L′ and C′ ⊆ C

The dom relation plays the role that “greater than or equal to” did for security levels. Continuing our example, level(Erin) = (SECRET, {EUR}) dom (CONFIDENTIAL, {EUR}) = level(EurDoc), and level(EurAsiaDoc) = (SECRET, {EUR, ASIA}) dom (SECRET, {EUR}) = level(Erin).

We now reformulate the simple security property and *-property in terms of dom:

Definition. The simple security property says that a subject s can read an object o if and only if level(s) dom level(o).

Definition. The *-property says that a subject s can write to an object o if and only if level(o) dom level(s).

In our example, assume the discretionary access controls are set to allow any subject all types of access. In that case, as level(Erin) dom level(EurDoc), Erin can read EurDoc (by the simple security property) but not write EurDoc (by the *-property). Conversely, as level(EurAsiaDoc) dom level(Erin), Erin cannot read EurAsiaDoc (by the simple security property) but can write to EurAsiaDoc (by the *-property).

A logical question is how to determine the highest security compartment that both Erin and Don can read and the lowest that both can write. In order to do this, we must review some properties of dom.

First, note that level(s) dom level(s); that is, dom is reflexive. The relation is also antisymmetric, because if both level(s) dom level(o) and level(o) dom level(s) are true, then level(s) = level(o). It is transitive, because if level(s1) dom level(o) and level(o) dom level(s2), then level(s1) dom level(s2).

We also define the greatest lower bound (glb) of two compartments as:

Definition. Let A = (L, C) and B = (L′, C′). Then glb(A, B) = (min(L, L′), C ∩ C′).

This answers the question of the highest security compartment that two subjects s and s′ can read an object in. It is glb(level(s), level(s′)). For example, Don and Erin can both read objects in:

glb(level(Don), level(Erin)) = (SECRET, ∅).

This makes sense because Don cannot read an object in any compartment except those with the category set {ASIA} or the empty set, and Erin can only read objects in a compartment with the category set {EUR} or the empty set. Both are at the SECRET level, so the compartment must also be at the SECRET level.

We can define the least upper bound (lub) of two compartments analogously:

Definition. Let A = (L, C) and B = (L′, C′). Then lub(A, B) = (max(L, L′), C ∪ C′).
