![](bbox=[0.265, 0.075, 0.92, 0.315])

# Truth tables to determine outputs from inputs for a problem description

Problem description: A baby alarm that goes off when the alarm is switched on and the baby is crying or the room is too cold.

With a problem description, we first need to identify the inputs. Here we have three: alarm switch, baby crying and room temperature, which we can represent as A, B and C and set up our truth table.

We know the alarm goes off if the device is switched on AND the baby is crying OR the room is too cold. From here, we can identify the logic gates in the description. We can determine from this that the device must be switched on before the alarm can go off, so if the switch is off, all outputs would be 0. If the device is switched on, at least one of the other two inputs must be on for the alarm to trigger. We have one intermediate value (baby crying OR room is cold), represented with P.

| A (switch) | B (crying) | C (cold) | P (B or C) | X (A and P) |
|---|---|---|---|---|
| 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 | 0 |
| 0 | 1 | 0 | 1 | 0 |
| 0 | 1 | 1 | 1 | 0 |
| 1 | 0 | 0 | 0 | 0 |
| 1 | 0 | 1 | 1 | 1 |
| 1 | 1 | 0 | 1 | 1 |
| 1 | 1 | 1 | 1 | 1 |