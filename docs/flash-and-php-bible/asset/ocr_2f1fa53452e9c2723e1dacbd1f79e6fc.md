# FIGURE 13.8
The completed file editor with a sample file loaded

![](bbox=[0.102, 0.178, 0.738, 0.558])

The application, as shown in Figure 13.8, is now completed. The following is the full ActionScript source code:

```
var
phpFile:String="http://localhost/ch12/FileEditor/fileEditor.ph
p";
var files:Array = ['sample.txt', 'anotherfile.txt',
'readme.txt'];
var storedFileData:String;

function populateFileList():void
{
    for(var i:uint=0; i < files.length; i++)
    {
        fileListCombo.addItem({label:files[i], data:files[i]});
    }
}

function loadFile(e:MouseEvent):void
```