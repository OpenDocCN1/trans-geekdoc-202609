ordered backward while maintaining the conditions, the program would not work as expected, since writing a negative value would show the message "Are you a minor".

```
# This program does not work properly
age = int (input ("How old are you?"))
if age <18 :
    print ("Are you a minor")
elif age <0:
    print ("You cannot have a negative age")
else :
    print ("Are you of legal age")
```