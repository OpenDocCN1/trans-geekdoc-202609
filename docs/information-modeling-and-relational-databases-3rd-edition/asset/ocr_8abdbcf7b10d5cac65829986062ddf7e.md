6. The following three reports come from an information system about these bodies in our solar system: the Sun, the naked eye planets, and their moons. Planets travel in roughly circular orbits about the Sun. A planet in inferior conjunction is lined up directly between the Earth and the Sun. A planet is in opposition if the Earth is lined up directly between it and the Sun. The missing value “---” means “does not exist”, and “M⊕” means one Earth mass. An astronomical unit (a.u.) equals 150,000,000 km. Schematize this.

# Sun:

| Name | Mass ($M_E$) | Radius (km) |
| :--- | :--- | :--- |
| The Sun | 34,000 | 696,000 |

# Planets:

| Name | Nr of moons | Mean distance from Sun (a.u.) | Mass ($M_E$) | Radius (km) | Orbital period (y d) | Next inf. conj. | Next oppos. | Atmosphere (main gases) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Mercury | 0 | 0.39 | 0.06 | 2440 | 0y 88d | Dec | – | --- |
| Venus | 0 | 0.72 | 0.81 | 6050 | 0y 224d | Jan | – | CO₂ |
| Earth | 1 | 1.0 | 1.0 | 6378 | 1y 0d | – | – | N₂O₂ |
| Mars | 2 | 1.5 | 0.11 | 3095 | 1y 322d | – | Feb | CO₂ |
| Jupiter | 95 | 5.2 | 318.0 | 71,400 | 11y 315d | – | Sep | H₂He |
| Saturn | 145 | 9.5 | 95.0 | 60,000 | 29y 167d | – | Sep | H₂He |

# Moons:

| Name | Planet orbited | Radius (km) | Orbital period (y d) | Mean apparent magnitude |
| :--- | :--- | :--- | :--- | :--- |
| Luna | Earth | 1737 | 0y 27.3d | −13.0 |
| Phobos | Mars | 6 | 0y 0.3d | 11.5 |
| Deimos | Mars | 4 | 0y 30.0d | 12.0 |
| Io | Jupiter | 1867 | 0y 1.7d | 5.5 |
| etc. | | | | |

# 6.6 Generalization of Object Types

The previous section discussed a specialization procedure in which subtypes of a more general object type are introduced to declare that specific roles are recorded only for these subtypes. Apart from this top-down procedure, a subtype graph may also arise in a bottom-up way when we need to introduce a supertype of object types that already occur in the model.

The process of introducing a supertype for object types that already exist is known as object type generalization. Hence, generalization is the reverse of specialization. A supertype is a more general form of its subtypes, and a subtype is a special form of its supertype(s).