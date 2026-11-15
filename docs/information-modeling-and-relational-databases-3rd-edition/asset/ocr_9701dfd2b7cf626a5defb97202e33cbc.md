the Person is husband of /is wife of Person fact type and toggle its isPreferredIdentifier property from False to True.

The selected UC and the corresponding UC on an implicit fact type are then redisplayed with a double uniqueness bar. Choosing the left UC of the marriage fact type for this results in Fig. 10.51(c), which shows a screen shot from the NORMA tool.

Formally, there is an equality constraint between the pair of husband and wife roles of Person and the pair of roles in the marriage fact type in Fig. 10.51(c). However, instead of displaying this equality constraint, purely for performance reasons the NORMA tool internally treats the implicit roles of Person as “mirror roles” or role proxies whose population always matches the population of the roles they mirror (in this case, the roles in the marriage fact type).

![](bbox=[0.19, 0.325, 0.83, 0.645])

FIG. 10.51 Objectifying a 1:1 association might be confusing.

Although CurrentMarriage is now primarily identified by the husband, NORMA requires the husband, wife combination to identify it when populating the fact type CurrentMarriage occurred on Date, as shown at the bottom of Fig. 10.51(c). This might be confusing, as the fact entry is not atomic and is inconsistent with the way the sample population editor works with normal fact types.

In this example, it is possible to record a current marriage without knowing the date of the marriage. This might confuse users who, by ignoring the implicit link fact types as in Fig. 10.51(a), think that CurrentMarriage is an independent object type because instances of it can exist without playing in the marriage date fact type. However, no objectification of a fact type with multiple UCs can be independent because in the link fact types, it plays a mandatory role in addition to the role in its preferred reference scheme.