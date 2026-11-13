```
```actionscript
var responder:Responder = new Responder(
    updateTrackingHandler,
    onFault
);
gateway = new NetConnection();
gateway.connect(gatewayURL);
}
```
```

The final update to the updateVideoTracking method is where the call to the remoting service is made. This call passes along the video id to update and the response should be the new count or an error if something goes wrong.

```
```actionscript
private function updateVideoTracking(vid:uint):void
{
    var responder:Responder = new Responder(
        updateTrackingHandler,
        onFault
    );
    gateway = new NetConnection();
    gateway.connect(gatewayURL);
    gateway.call("Videos.updatePlayCount", responder, vid);
}
```
```

Once the count is updated, the new count is returned to Flash. Just like the previous remoting calls, a response handler is needed in order to capture this response. In this example, the new count is sent to the TextField located within the videoMetaInfo MovieClip to reflect the current count.

```
```actionscript
private function updateTrackingHandler(response:Object):void
{
    videoMetaInfo.viewsTxt.text = response.count;
}
```
```

The last step to adding the tracking feature is to modify the existing listItemHandler method and add in the call to the update method, such as the following:

```
```actionscript
private function listItemHandler(e:Event):void
{
    ...
    updateVideoTracking(e.currentTarget.videoObj.vid);
}
```
```

At this point the tracking addition is complete. As you can see, the original creation process in the first section really allows the ability to introduce new functionality with minimal updates.

Now your video player can properly track the videos and inform you as to which videos are more popular than others. You could easily develop an admin panel where all of this data could be viewed, or you can log in to your SQL editor and look at the videos table for the active count on each video.