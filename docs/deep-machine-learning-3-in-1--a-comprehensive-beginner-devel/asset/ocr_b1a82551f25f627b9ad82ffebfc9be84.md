```
print (computer_accessories[4].lower())

print (computer_accessories[5].upper())

print (computer_accessories[7].upper())

>>> ================================ RESTART
============================================
>>>
Mouse
Monitor
charger
BLUETOOTH CONNECTOR
MODEM
>>>
```

You can use individual values from a list.

```
computer_accessories = ['mouse', 'keyboard', 'monitor', 'cables',
'charger', 'bluetooth connector', 'wi-fi', 'modem', 'internet', 'webcam']

x = "I will have to buy from the computer market a " +
computer_accessories[2].title() + "."

print (x)
```