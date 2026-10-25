
```
del computer_accessories[2]
print(computer_accessories)
```

```
del computer_accessories[5]
print(computer_accessories)
```

```
del computer_accessories[6]
print(computer_accessories)
```

```
del computer_accessories[7]
print(computer_accessories)
```

>>> ================= RESTART =================
===============================================
>>>
['mouse', 'keyboard', 'monitor', 'cables', 'charger', 'bluetooth connector',
'wi-fi', 'modem', 'internet', 'webcam']
['keyboard', 'monitor', 'cables', 'charger', 'bluetooth connector', 'wi-fi',
'modem', 'internet', 'webcam']
['keyboard', 'monitor', 'charger', 'bluetooth connector', 'wi-fi', 'modem',
'internet', 'webcam']
['keyboard', 'monitor', 'charger', 'bluetooth connector', 'wi-fi', 'internet',
'webcam']

['keyboard', 'monitor', 'charger', 'bluetooth connector', 'wi-fi', 'internet']

Traceback (most recent call last):
  File "C:/Users/saifia computers/Desktop/p", line 16, in <module>
    del computer_accessories[7]
IndexError: list assignment index out of range
>>>

You will see an error message just like the one that you are seeing at the bottom of the code if the index you are typing gets out of range because of deleting elements. Previously the index 7 was working but as I have deleted elements from it, it doesn't work anymore.

There is another method widely known as the pop() method to delete items from a list. Sometimes you need to use the value of a certain element after you have removed it from the list. In this kind of scenario, you can use the pop() method. For example, the player needs to recall which elements have been destroyed so it can use the pop() method instead of the del() method. The pop() method takes a list in the form of a stack of items. Each time you use the method, an item from the top of the list will be popped off. The stack will get empty that way.

```
computer_accessories = ['mouse', 'keyboard', 'monitor', 'cables',
'charger', 'bluetooth connector', 'wi-fi', 'modem', 'internet', 'webcam']

print(computer_accessories)

popped_computer_accessories = computer_accessories.pop()
print(computer_accessories)
print(popped_computer_accessories)

popped_computer_accessories = computer_accessories.pop()
print(computer_accessories)
print(popped_computer_accessories)

popped_computer_accessories = computer_accessories.pop()
print(computer_accessories)
print(popped_computer_accessories)

popped_computer_accessories = computer_accessories.pop()
print(computer_accessories)
print(popped_computer_accessories)

popped_computer_accessories = computer_accessories.pop()
print(computer_accessories)
print(popped_computer_accessories)

popped_computer_accessories = computer_accessories.pop()
print(computer_accessories)
print(popped_computer_accessories)

popped_computer_accessories = computer_accessories.pop()
print(computer_accessories)
print(popped_computer_accessories)

popped_computer_accessories = computer_accessories.pop()
print(computer_accessories)
print(popped_computer_accessories)

popped_computer_accessories = computer_accessories.pop()
print(computer_accessories)
print(popped_computer_accessories)

popped_computer_accessories = computer_accessories.pop()
print(computer_accessories)
print(popped_computer_accessories)
```

>>> ================= RESTART =================
==============================================
>>>
['mouse', 'keyboard', 'monitor', 'cables', 'charger', 'bluetooth connector',
'wi-fi', 'modem', 'internet', 'webcam']
['mouse', 'keyboard', 'monitor', 'cables', 'charger', 'bluetooth connector',
'wi-fi', 'modem']
webcam
['mouse', 'keyboard', 'monitor', 'cables', 'charger', 'bluetooth connector',
'wi-fi', 'modem']
internet
['mouse', 'keyboard', 'monitor', 'cables', 'charger', 'bluetooth connector',
'wi-fi']
modem
['mouse', 'keyboard', 'monitor', 'cables', 'charger', 'bluetooth connector']
wi-fi
['mouse', 'keyboard', 'monitor', 'cables', 'charger']
bluetooth connector
['mouse', 'keyboard', 'monitor', 'cables']
charger
['mouse', 'keyboard', 'monitor']
cables
['mouse', 'keyboard']
monitor
['mouse']
keyboard
[]
mouse
Traceback (most recent call last):
  File "C:/Users/saifia computers/Desktop/p", line 45, in <module>
    popped_computer_accessories = computer_accessories.pop()
IndexError: pop from empty list
>>>

You also can use the pop() method to remove items from any position inside of a list. See how to do that.

```
computer_accessories = ['mouse', 'keyboard', 'monitor', 'cables',
'charger', 'bluetooth connector', 'wi-fi', 'modem', 'internet', 'webcam']

print(computer_accessories)

popped_computer_accessories = computer_accessories.pop(1)

print(computer_accessories)

print(popped_computer_accessories)

popped_computer_accessories = computer_accessories.pop(4)

print(computer_accessories)

print(popped_computer_accessories)

popped_computer_accessories = computer_accessories.pop(2)

print(computer_accessories)

print(popped_computer_accessories)

popped_computer_accessories = computer_accessories.pop(0)

print(computer_accessories)

print(popped_computer_accessories)
>>> ================ RESTART
>>>
['mouse', 'keyboard', 'monitor', 'cables', 'charger', 'bluetooth connector',
'wi-fi', 'modem', 'internet', 'webcam']
['mouse', 'monitor', 'cables', 'charger', 'bluetooth connector', 'wi-fi',
'modem', 'internet', 'webcam']
keyboard
['mouse', 'monitor', 'cables', 'charger', 'wi-fi', 'modem', 'internet',
'webcam']
bluetooth connector
['mouse', 'monitor', 'charger', 'wi-fi', 'modem', 'internet', 'webcam']
cables
['monitor', 'charger', 'wi-fi', 'modem', 'internet', 'webcam']
mouse
>>>
```

The last method to remove items from a list is by using the remove method. Sometimes, you don't know the exact position of a particular element that you want to remove from a list. In this case if you know the value of an item, you can apply the remove() method and get rid of the item.

```
computer_accessories = ['mouse', 'keyboard', 'monitor', 'cables',
'charger', 'bluetooth connector', 'wi-fi', 'modem', 'internet', 'webcam']
```

```
print(computer_accessories)

computer_accessories.remove('keyboard')
print(computer_accessories)

computer_accessories.remove('monitor')
print(computer_accessories)

computer_accessories.remove('mouse')
print(computer_accessories)
>>> 
['mouse', 'keyboard', 'monitor', 'cables', 'charger', 'bluetooth connector',
'wi-fi', 'modem', 'internet', 'webcam']
['mouse', 'monitor', 'cables', 'charger', 'bluetooth connector', 'wi-fi',
'modem', 'internet', 'webcam']
['mouse', 'cables', 'charger', 'bluetooth connector', 'wi-fi', 'modem',
'internet', 'webcam']
['cables', 'charger', 'bluetooth connector', 'wi-fi', 'modem', 'internet',
'webcam']
>>> 
```

You can create a loop through a list.

```
computer_accessories = ['mouse', 'keyboard', 'monitor', 'cables',
'charger', 'bluetooth connector', 'wi-fi', 'modem', 'internet', 'webcam']
print(computer_accessories)
```

```
for computer_accessory in computer_accessories:
    print(computer_accessory)
```

>>> ================= RESTART =================
==============================================

```
>>>
['mouse', 'keyboard', 'monitor', 'cables', 'charger', 'bluetooth connector',
'wi-fi', 'modem', 'internet', 'webcam']
mouse
keyboard
monitor
cables
charger
bluetooth connector
wi-fi
modem
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
    print(computer_accessory.title() + " has been completely destroyed! It can never be rebuilt. ")
```

>>> ================= RESTART =================
===============================================
>>>
['mouse', 'keyboard', 'monitor', 'cables', 'charger', 'bluetooth connector',
'wi-fi', 'modem', 'internet', 'webcam']
Mouse has been completely destroyed! It can never be rebuilt.
Keyboard has been completely destroyed! It can never be rebuilt.
Monitor has been completely destroyed! It can never be rebuilt.
