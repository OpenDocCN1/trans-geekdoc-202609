To get started, open the starting file that can be found on this book's Web site.

The assets for this example have already been completed so you can focus on the programming. The first step is to create the necessary variables.

```
var timer:Timer;
var sandbox:String;
var startingTime:uint = 5;
```

After the variables are assigned, you can build the initial function init, which is called as soon as the movie begins.

```
function init():void
{
    timerMC.alpha = 0;
    sandbox = Security.sandboxType;

    if(sandbox.indexOf('local') == -1)
    {
        startTimer();
    }
}
```

The main portion of this function is the if statement, which checks for the presence of the string "local" in the sandbox type. This covers any of the local versions and determines the movie is not running on the remote sandbox. If a local sandbox is detected, a call to startTimer is made, which initializes and starts the countdown timer.

```
if (sandbox.indexOf('local') != -1)
{
    startTimer();
}
```

The startTimer function first initializes a new timer instance and then adds an event listener, which is called every millisecond. The last action in this function is to display the timer text, by setting the alpha property to 1.0 which makes it fully visible.

CAUTION Using a timer update of 1 millisecond for a long period of time can create an unresponsive movie. For an immediate check, such as in this example, it is not a great concern.

```
function startTimer():void
{
    startingTime *= 1000;
```