If you run this example in your browser you should see output similar to the following example:

```
Array
(
    [0] => Array
    (
        [name] => Sample Video 1:1
        [src] => sample.flv
        [vid] => 1
        [cat] => Category A
        [description] => Really Cool Video Here
        [count] => 0
    )
    ...
)
```

You should now have two complete classes that can be used in your ActionScript to interact with the database contents. The next step is to build the ActionScript portion of the application, which is handled by external classes for reusability.

# Advanced video player development

In the previous sections of this example you developed the database and tables. Then you built the PHP services that interact with the database tables. The next step is to develop the ActionScript that is responsible for displaying and managing the video player.

If you look at the video player, as shown in Figure 17.4, on the Flash Stage you will notice there are four parts: the main video player component, info box, video list, and drop-down menu that will store the video categories. If you deselect everything by clicking on the Stage or pressing Esc, a document class with the name VideoPlayer appears.

This class is where most of the video player is managed from, rather than having code directly on the Timeline. This also gives you the option to develop in an external editor such as FDT, or you can use the stand-alone editor that ships with Flash.

# Creating the document class

Start by creating a new ActionScript file using the ActionScript editor in Flash and name it VideoPlayer.as. Save this file in the application directory where your FLA is located to ensure the file will be loaded. You can also use the ActionScript file that is provided in the book's source on the Web site.