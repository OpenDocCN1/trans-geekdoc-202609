```
Set time interval= "t" minute
if (Presentstate = "Neutral" and Nextstate ="Depressed") then
    if (((Channel = ("F3" OR "F7"))) AND
((F3.oldvalue> F3.Newvalue)
        OR (F7.oldvalue> F7.Newvalue))) then
    Moves to the next state.
else
    Remains in the same state.
end
if (Presentstate = "Neutral" and Nextstate =
"PositiveEmotion") then
    if (((Channel = ("T7" OR "T8"))) AND
((T7.oldvalue< T7.Newvalue)
        OR (T8.oldvalue< T8.Newvalue))) then
    Moves to the next state.
else
    Remains in the same state.
end
if (Presentstate = "Neutral" and Nextstate =
"NegativeEmotion") then
    if (((Channel = ("FP1" OR "FP2"))) AND ((FP1.
oldvalue <FP1.Newvalue)
        OR (FP2.oldvalue < FP2.Newvalue))) then
    Moves to the next state.
else
    Remains in the same state.
end
if (Presentstate = "PositiveEmotion" and Nextstate ==
"NegativeEmotion") then
    if (((Channel = ("F4" OR "F8"))) AND ((F4.oldvalue<
F4.Newvalue)
        OR (F8.oldvalue< F8.Newvalue))) then
    Moves to the next state.
else
    Remains in the same state.
end
if (Presentstate = "NegativeEmotion" and Nextstate ==
"PositiveEmotion") then
    if (((Channel = ("F3" OR "F7"))) AND ((F3.
oldvalue< F3.Newvalue)
        OR (F7.oldvalue< F7.Newvalue))) then
    Moves to the next state.
else
    Remains in the same state.
end
if (Presentstate = "Neutral" and Nextstate ==
"Harmony") then
    if (((Channel = "PO7") AND ((PO7.oldvalue < PO7.
Newvalue) OR
```