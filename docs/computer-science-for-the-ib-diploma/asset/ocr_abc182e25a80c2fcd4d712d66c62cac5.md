```
**Python**

```python
text = "Computer Science is fun"
part = text[1:-4]
print(part)
```
```

Above, the extracted text will start at index 1 and will end at the last index –4. So, the value stored in the variable part is “omputer Science is”.


# Replace

The replace method searches a string for a character or set of characters and replaces it or them with another character or with other characters.


```
**Java**

```java
String text = "Computer Science is fun";
text = text.replace('e', '@');
System.out.println(text);
```
```

In Java, the replace method will replace one single character, so the text now becomes “Comput@r Sci@nc@ is fun”. To replace several characters, the replaceAll method should be used.


```
**Java**

```java
String text = "Computer Science is fun";
text = text.replaceAll("is", "will be");
System.out.println(text);
```
```

In Python, the replace method is used for replacing both one single character and more characters.


```
**Python**

```python
text = "Computer Science is fun"
text = text.replace("e", "@")
print(text)
```
```

```
**Python**

```python
text = "Computer Science is fun"
text = text.replace("is", "will be")
print(text)
```
```

# Strip

Sometimes, when reading values from a text file or any permanent storage, you might want to remove the trailing white spaces. This can be achieved by using the strip method.