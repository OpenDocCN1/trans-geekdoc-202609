```
storeItemID = id;
albumName = n;
albumDesc = d;
albumThumb = t;
albumPrice = p;
...
}
```

The two text boxes that hold the name and description for each item are the last part of this custom class. The data that was passed in is assigned to each text box. Normally, you would probably check for valid data, but because you are controlling the PHP that is returned you can be sure the data will be valid.

```
nameTxt.text = albumName;
descTxt.text = albumDesc;
```

The final method in this class is used to send the data back to whoever calls it. The return action sends back a custom object that is filled with the item data in the previous method.

```
public function getItem():Object
{
return
{
target:this,
id:storeItemID,
name:albumName,
price:albumPrice
};
}
```

The above method has a special type of return defined. This return value is an inline Object which is used to simplify code by excluding unnecessary variable names.

Each of the types: Array, Object, and String have a shorthand way to define them. For example, the Object type can be defined simply with:

```
var sampleObj:Object = {name:value};
```

Table 12.1 shows the type and the shorthand equivalent for it. Using the shorthand values can save development time because you have to type less.

**WARNING** The shorthand can create problems because you create a “weakly” typed object. Therefore you cannot benefit from compile time type checking. You may access the dynamic object improperly and you will not know until runtime. This means that you should use caution when creating your properties and variables in shorthand.