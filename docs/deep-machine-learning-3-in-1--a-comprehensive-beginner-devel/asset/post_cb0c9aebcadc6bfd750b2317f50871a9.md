
So looping through a list makes it easier to code.

## Tuple

Tuples are very much like lists except for the fact that they cannot be changed once they have been created. Lists work perfectly well to sort out the items. A tuple looks the same as a list except for the fact that you have to use parenthesis in tuples instead of square brackets. Once you have defined a tuple, you can be able to access individual elements by using the index number.

```python
computer_accessories = ('mouse', 'keyboard', 'monitor', 'cables',
'charger', 'bluetooth connector', 'wi-fi', 'modem', 'internet', 'webcam')

print(computer_accessories)

for computer_accessory in computer_accessories:
    print(computer_accessory.title() + " has been completely destroyed!
It can never be rebuilt. ")
```

>>> ================= RESTART =================
===============================================

>>>

('mouse', 'keyboard', 'monitor', 'cables', 'charger', 'bluetooth connector',
'wi-fi', 'modem', 'internet', 'webcam')

Mouse has been completely destroyed! It can never be rebuilt.
Keyboard has been completely destroyed! It can never be rebuilt.
Monitor has been completely destroyed! It can never be rebuilt.
Cables has been completely destroyed! It can never be rebuilt.
Charger has been completely destroyed! It can never be rebuilt.
Bluetooth Connector has been completely destroyed! It can never be rebuilt.
Wi-Fi has been completely destroyed! It can never be rebuilt.
Modem has been completely destroyed! It can never be rebuilt.
Internet has been completely destroyed! It can never be rebuilt.
Webcam has been completely destroyed! It can never be rebuilt.

>>>

## Chapter Two

### Advanced Python Programming

Programming also involves a set of conditions. Sometimes you have to test different conditions. The if statements allow you to test certain conditions and respond rightly. This chapter will walk you through the advanced level programming in Python. You will learn to write if statements. You will also learn how you can create complex statements.

```python
computer_accessories = ('mouse', 'keyboard', 'monitor', 'cables',
'charger', 'bluetooth connector', 'wi-fi', 'modem', 'internet', 'webcam')

print(computer_accessories)

for computer_accessory in computer_accessories:

    if computer_accessory == 'keyboard':

        print(computer_accessory.upper() + " has been completely
destroyed! It can never be rebuilt. ")

else:

    print(computer_accessory.title() + " has been completely
destroyed! It can never be rebuilt. ")
```

>>> ================================ RESTART
==============================

>>>

('mouse', 'keyboard', 'monitor', 'cables', 'charger', 'bluetooth connector',
'wi-fi', 'modem', 'internet', 'webcam')
Mouse has been completely destroyed! It can never be rebuilt.
KEYBOARD has been completely destroyed! It can never be rebuilt.
Monitor has been completely destroyed! It can never be rebuilt.
Cables has been completely destroyed! It can never be rebuilt.
Charger has been completely destroyed! It can never be rebuilt.
Bluetooth Connector has been completely destroyed! It can never be rebuilt.
Wi-Fi has been completely destroyed! It can never be rebuilt.
Modem has been completely destroyed! It can never be rebuilt.
Internet has been completely destroyed! It can never be rebuilt.
Webcam has been completely destroyed! It can never be rebuilt.
>>>

I will use the same list of elements and use an if-else statement to test different conditions.

```python
computer_accessories = ('mouse', 'keyboard', 'monitor', 'cables',
'charger', 'bluetooth connector', 'wi-fi', 'modem', 'internet', 'webcam')

print(computer_accessories)

if 'mouse' in computer_accessories:
    print('destroying mouse')

if 'monitor' in computer_accessories:
    print('destroying monitor')

if "keyboard" in computer_accessories:
    print('destroying keyboard')
```

>>> ================= RESTART =================
==============================

>>>

('mouse', 'keyboard', 'monitor', 'cables', 'charger', 'bluetooth connector',
'wi-fi', 'modem', 'internet', 'webcam')

destroying mouse
destroying monitor
destroying keyboard

>>>

See the following example that includes an if-else statement.

```python
computer_accessories = ('mouse', 'keyboard', 'monitor', 'cables',
'charger', 'bluetooth connector', 'wi-fi', 'modem', 'internet', 'webcam')

print(computer_accessories)

for computer_accessory in computer_accessories:
    if computer_accessory == 'mouse':
        print('Mouse has been destroyed.')
    else:
        print('Destroying ' + computer_accessory + '.')

print ('\n I have destroyed everything.')
```

>>> ================= RESTART =================
-----------------------------------------------
>>> 
('mouse', 'keyboard', 'monitor', 'cables', 'charger', 'bluetooth connector',
'wi-fi', 'modem', 'internet', 'webcam')
Mouse has been destroyed.
Destroying keyboard.

- Destroying monitor.
- Destroying cables.
- Destroying charger.
- Destroying bluetooth connector.
- Destroying wi-fi.
- Destroying modem.
- Destroying internet.
- Destroying webcam.
- I have destroyed everything.
- >>>

## The Raw_Input() Function

This also is one of the most important functions in the world of Python. Some programs demand that you get input from the end-user. This function can help you with that. It pauses the program and waits until the user fills it in with some information. Once it receives it, it then goes on to store it inside of a variable to make it more convenient for the programmer to work with. The following program will repeat whatever you will enter as input. See the example.

```python
prompt = "\nYou need to say something to me and I will repeat it for you:"
prompt += "\nYou must enter q if you want to exit out of this
program..."
themessage = ""
while themessage != 'q':
    themessage = raw_input(prompt)
    print(themessage)
```

>>> ================================ RESTART
===============================
>>>

You need to say something to me and I will repeat it for you:

You must enter q if you want to exit out of this program...

![](img/bb7ba516e91395cf9ab1f1db3ea8f354_54_0.png)

You need to say something to me and I will repeat it for you:

You must enter q if you want to exit out of this program....Johny

![](img/bb7ba516e91395cf9ab1f1db3ea8f354_54_1.png)

You need to say something to me and I will repeat it for you:

You must enter q if you want to exit out of this program....Lisa

![](img/bb7ba516e91395cf9ab1f1db3ea8f354_54_2.png)

You need to say something to me and I will repeat it for you:

You must enter q if you want to exit out of this program....Cherrypicking

![](img/bb7ba516e91395cf9ab1f1db3ea8f354_55_0.png)

You need to say something to me and I will repeat it for you:

You must enter q if you want to exit out of this program....Cherry Orchard

![](img/bb7ba516e91395cf9ab1f1db3ea8f354_55_1.png)

You need to say something to me and I will repeat it for you:

You must enter q if you want to exit out of this program....Blossoms of Hunza

![](img/bb7ba516e91395cf9ab1f1db3ea8f354_55_2.png)

You need to say something to me and I will repeat it for you:

You must enter q if you want to exit out of this program....q

![](img/bb7ba516e91395cf9ab1f1db3ea8f354_55_3.png)

See another example of the input function of Python. The code mentioned above works perfectly well but the only problem is that it prints out the word
