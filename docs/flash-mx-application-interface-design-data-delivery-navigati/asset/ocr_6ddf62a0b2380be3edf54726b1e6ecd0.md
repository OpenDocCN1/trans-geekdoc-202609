makes itself draggable. We will create another custom class by extending the MovieClip object in the code later in this chapter, so I would encourage you to come back and take a look at this code then and apply your knowledge. It really is no different (and is actually much simpler) than the coding we are about to embark on, except for the existence of the #initclip and #endinitclip lines as the bookends of the code. All these lines do is allow us to place this code inside a movie clip as opposed to on our main timeline, and the code will still run before the movie begins, initializing our object.

# The structure

The last item that has been prepared for this project is the code in the layer named structure on the main timeline. If you select the frame in this layer and open your ActionScript editor, you will see the code I use to populate the tree. Since you will want to alter this for your own projects, it's important that we look at it more closely so you understand how I accomplished it.

First, we have three objects in which I store the color values for the nodes:

```
chaosCol = {params:{ra:50, rb:32, ga:50,
gb:-10, ba:50, bb:0}, connector:0x471D27};
titansCol = {params:{ra:50, rb:17, ga:50,
gb:34, ba:50, bb:36}, connector:0x38494B};
olympiansCol = {params:{ra:50, rb:32, ga:50,
gb:13, ba:50, bb:37}, connector:0x47344C};
```

Each object contains two properties: params and connector. params holds another custom object containing values to send to the Color object's setTransform method. We will use the params object to tint the nodes themselves. connector, on the other hand, contains a hexadecimal value that we will send to the beginGradientFill method when we draw our connectors with the drawing API.

The rest of the lines of script in the structure layer deal with populating our tree. Let's look at the first two lines of this code:

```
chaos = {name:"Chaos", col:chaosCol};
chaos.info = "This is where I would put information on Chaos."
```

Each node in our tree will be an object holding at least three properties. The first property is the node's name, the second is a reference to our custom coloring objects created above, and the third is any information we wish to have related about that node in its expanded interface.

If you are not familiar with the number of ways to create custom objects, it's important for you to know that all of the following methods accomplish the exact same thing:

```
chaos = new Object();
chaos.name = "Chaos";

chaos = new Object();
chaos["name"] = "Chaos";

chaos = {};
chaos.name = "Chaos";

chaos = {};
chaos["name"] = "Chaos";

chaos = {name:"Chaos"};
```

The way I have chosen is to give the object a name and color property on the first line, and an info property on the second. I felt this method was clear and easy to update, as well as keeping the number of lines at a manageable length.