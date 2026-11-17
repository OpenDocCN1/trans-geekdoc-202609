Here I create a generic object to pass to the spinnerNav as it is created. First is the filename for the XML document I'm using. Then I have two other parameters, the first of which, clusterRadius, is the radius of any particular cluster, and the second, separator, is the distance between any two open clusters. When the spinnerNav is created using attachMovie, obj is passed to it and all of the values inside obj are copied into it.

Now we continue with the methods for our spinnerNav class. These methods will be placed after the Object.registerClass line above. You may have noticed that in the constructor I created above, an init method is called. That method will call another method, importXml:

```
spinnerNav.prototype.init = function() {
    this.outputObject = {}
    this.importXml(this.fileName)
}
```

As well as calling importXml, the init method also creates a generic object, outputObject, which will hold the object structure created when parsing the XML. Next I created the importXml method, which goes directly after the code above. It creates a new XML object, called myStructure, and then assigns it various properties and methods:

```
spinnerNav.prototype.importXml = function(filename) {
    this.myStructure = new XML()
    this.myStructure.ignoreWhite = true
    this.myStructure.onLoad = this.triggerParse
    this.myStructure.parseNode = this.parseNode
    this.myStructure.parent = this
    this.myStructure.load(this.filename)
}
```

The first property is ignoreWhite, which will make the XML object ignore any white space, or formatting, that might be present in our XML document. Then the triggerParse method is assigned to the XML object's onLoad handler. This will be called when the XML object has finished loading. The next method, parseNode, will be called to parse each individual node and give it a parent property so that it knows where it has been created and can send a message back when it has finished parsing. Finally it calls the load method of the myStructure object, passing it the filename.