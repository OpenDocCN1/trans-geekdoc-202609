

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

如果你输入的索引因删除元素而超出范围，就会看到类似于代码底部所示的错误消息。之前索引 7 是有效的，但由于我从中删除了元素，它不再有效。

还有一种广为人知的方法叫做 pop() 方法，用于从列表中删除项目。有时你需要在从列表中删除某个元素后使用该元素的值。在这种情况下，你可以使用 pop() 方法。例如，玩家需要回忆哪些元素已被销毁，因此可以使用 pop() 方法而不是 del() 方法。pop() 方法将列表视为一堆项目。每次使用该方法时，列表顶部的一个项目会被弹出。这样栈就会变空。

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

你也可以使用 pop() 方法从列表中的任何位置删除项目。请看具体做法。

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

从列表中删除项目的最后一种方法是使用 remove 方法。有时，你不知道要从列表中删除的特定元素的确切位置。在这种情况下，如果你知道某个项目的值，可以应用 remove() 方法来删除该项目。

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

你可以遍历列表来创建循环。

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

遍历列表可以让你做不同的事情。我将使用列表中的元素在玩家的电脑屏幕上显示一条消息。

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

