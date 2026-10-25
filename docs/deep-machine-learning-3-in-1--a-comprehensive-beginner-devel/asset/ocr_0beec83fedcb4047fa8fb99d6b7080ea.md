```
>>>
mouse
monitor
charger
bluetooth connector
modem

Traceback (most recent call last):
  File "C:/Users/saifia computers/Desktop/p", line 7, in <module>
    print (computer_accessories[11])
IndexError: list index out of range
>>>
```

The error message appeared only because the index number I entered in the end doesn't belong to any element in the list. You can apply different methods in the list to format the results as per your particular needs.

```
computer_accessories = ['mouse', 'keyboard', 'monitor', 'cables',
'charger', 'bluetooth connector', 'wi-fi', 'modem', 'internet', 'webcam']

print (computer_accessories[0].title())

print (computer_accessories[2].title())
```