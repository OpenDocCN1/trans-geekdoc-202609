

遍历列表可以使编码更加容易。

## 元组

元组与列表非常相似，区别在于元组一旦创建就不能更改。列表非常适合对项目进行排序。元组的外观与列表相同，区别在于元组使用圆括号而不是方括号。定义元组后，可以使用索引号访问单个元素。

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

## 第二章

### 高级 Python 编程

编程还涉及一组条件。有时你需要测试不同的条件。if 语句允许你测试某些条件并做出正确响应。本章将带你深入学习 Python 的高级编程。你将学习编写 if 语句。你还将学习如何创建复杂语句。

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

我将使用相同的元素列表，并使用 if-else 语句来测试不同的条件。

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

请参见包含 if-else 语句的以下示例。

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

## Raw_Input() 函数

这也是 Python 世界中最重要的函数之一。有些程序要求你从最终用户那里获取输入。此函数可以帮助你完成此操作。它会暂停程序，并等待用户输入一些信息。一旦接收到输入，它就会将其存储在变量中，以便程序员更方便地使用。以下程序将重复你输入的任何内容。请参见示例。

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

请参见 Python 输入函数的另一个示例。上述代码运行良好，唯一的问题是它会打印出单词

