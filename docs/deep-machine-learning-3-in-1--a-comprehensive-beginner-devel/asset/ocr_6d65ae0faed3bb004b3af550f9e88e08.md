```
internet
webcam
>>>
```

Looping through a list allows you to do different things. I will use the elements of a list to display a message on the computer screens of the player.

```
computer_accessories = ['mouse', 'keyboard', 'monitor', 'cables',
'charger', 'bluetooth connector', 'wi-fi', 'modem', 'internet', 'webcam']

print(computer_accessories)

for computer_accessory in computer_accessories:
    print(computer_accessory.title() + " has been completely destroyed!
It can never be rebuilt. ")

>>> ================= RESTART =================
===============================================
>>>
['mouse', 'keyboard', 'monitor', 'cables', 'charger', 'bluetooth connector',
'wi-fi', 'modem', 'internet', 'webcam']
Mouse has been completely destroyed! It can never be rebuilt.
Keyboard has been completely destroyed! It can never be rebuilt.
Monitor has been completely destroyed! It can never be rebuilt.
```