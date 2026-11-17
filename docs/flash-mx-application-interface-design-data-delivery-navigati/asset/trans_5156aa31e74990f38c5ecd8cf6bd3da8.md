

如果你完成了上一个练习，接下来的两个函数应该对你来说非常熟悉——事实上，稍作修改，你就可以轻松地将这些函数添加到一个 ActionScript 库中，并在设计任何预加载器时引用它。暂时，我们只需将它们输入到我们的影片中。

```
assessLoad = function(clip) {
// var kbLoaded = Math.floor(clip.getBytesLoaded()/1024);
// var kbTotal = Math.floor(clip.getBytesTotal()/1024);

// delete these two lines and uncomment
// the above lines upon publishing
var kbLoaded = Math.floor(getTimer()/200) + 2;
var kbTotal = 150;

loaded.text = kbLoaded + "KB";
total.text = kbTotal + "KB";
if ((kbLoaded >= kbTotal) && kbTotal > 1) {
    endPreload(clip);
};
};

endPreload = function(clip) {
    clearInterval(preload);
    loaded.text = "";
    total.text = "";
    continue_btn._visible = 1;
    continue_btn.onPress = function() {
    //clip.gotoAndStop("main")
    }
};
```

由于 assessLoad 函数与 Laser Logo 中的完全相同，你可以在那里查看更详细的解释。简单来说，它记录已加载字节数和影片总字节数，将这些值放入文本字段，并检查影片何时完全加载。endPreload 函数包含几个值得你考虑的不同行。你可以看到，我们和之前一样清除了预加载间隔，擦除了文本字段，并使按钮可见。仅此而已。笑话将继续，直到用户感到厌倦并单击 continue_btn，此时播放头会被发送到另一帧，或者无论你需要做什么来到达主内容。

![](img/50202c17d5022233f3e3ec60560e35aa_29_0.png)

![](img/50202c17d5022233f3e3ec60560e35aa_29_1.png)

![](img/50202c17d5022233f3e3ec60560e35aa_29_2.png)

![](img/50202c17d5022233f3e3ec60560e35aa_29_3.png)

![](img/50202c17d5022233f3e3ec60560e35aa_29_4.png)

![](img/50202c17d5022233f3e3ec60560e35aa_29_5.png)

![](img/50202c17d5022233f3e3ec60560e35aa_29_6.png)

现在我们有四个函数来控制笑话的讲述。第一个启动整个过程。在 `endPreload` 函数之后输入这些行：

```
startJoke = function() {
  currentLine = 0;
  clearInterval(nextJokeInterval);
  startLine();
}
```

startJoke 首先将当前笑话的当前行设置为 0。请记住，jokes 数组中的每个索引包含另一个数组。我们上面设置的变量 currentJoke 表示 jokes 中的索引位置。currentLine 然后表示子数组中的索引，由于每个笑话都将从第一行开始，因此索引设置为 0。此函数中的下一行清除我们将设置的间隔，该间隔将在小丑开始下一个笑话之前创建一个暂停。最后，我们调用 startLine 函数，它将做 exactly that：在屏幕上开始显示该行。让我们现在编写该函数。

在上述代码之后输入以下内容：

```
startLine = function() {
  currentLetter = 0;
  clearInterval(nextLine);
  bubble.text = "";
  speechLine.clear();
}
```

在此函数调用开始时，我们将当前字母设置为 0（行中的第一个字母），清除用于延迟显示下一行的间隔，擦除 bubble 中的当前文本，并从 speechLine 影片剪辑中清除语音线绘制。

添加以下内容以完成 startLine 函数：

```
if (currentLine >=
    jokes[currentJoke].length) {
  jokePeople.gotoAndStop("noTalk");
  hitInterval = setInterval(hitJoker, 1000);
} else {
  speechLine.lineStyle(1, 0, 100);
  if (currentLine % 2 > 0) {
    speechLine.moveTo(hitterLine._x,
    hitterLine._y);
    jokePeople.gotoAndStop("response");
  } else {
    speechLine.moveTo(jokerLine._x,
    jokerLine._y);
    jokePeople.gotoAndStop("joke");
  }
  speechLine.lineTo(jokeX, jokeY + 30);
  letterInterval =
  setInterval(revealLetters, 50);
}
```

在显示任何文本之前，我们首先检查是否已到达笑话的最后一行。jokes[currentJoke] 包含一个存放笑话每一行的数组，因此如果 currentLine 等于或大于此数组的长度，我们就知道已到达末尾。如果是这种情况，我们将我们的小丑发送到 "noTalk"，并设置一个一秒延迟，然后调用我们将要创建的 hitJoker 函数。我们将此标识符命名为 hitInterval。

![](img/50202c17d5022233f3e3ec60560e35aa_30_0.png)

如果我们尚未到达笑话的最后一行，我们将继续显示该行。首先，我们将 speechline 影片剪辑的 lineStyle 设置为 1 像素黑色，100% 不透明度。然后我们查看 currentLine 是奇数还是偶数。由于笑话是一组来回的俏皮话，第一行总是由小丑说出，因此我们知道任何奇数索引都意味着击打者正在说话。取模运算符（%）是判断奇偶的简单方法，因为它返回两个操作数的余数。任何奇数除以二都会有余数 1，因此我们需要查看当前行索引是否发生这种情况。如果确实有奇数，我们将 speechLine 的起始绘制位置移动到 hitterLine 影片剪辑的坐标，并将动画发送到 "response" 帧。如果索引是偶数，我们知道小丑正在说话，因此将 speechline 移动到从 jokerLine 绘制，并将动画发送到 "joke" 帧。

最后，我们将 speechLine 从其当前起始位置绘制到气泡文本字段（加上 30 像素偏移量），并使用 setInterval 每 50 毫秒调用一次 revealLetters 函数。revealLetters 将逐个字母添加到气泡文本字段中。

那是其中最长的一个。这里有一个简短明了的函数，应放在 startLine 函数之后：

```
hitJoker = function() {
  if (Math.random() > .33) {
    clearInterval(hitInterval);
    jokePeople.gotoAndPlay("punch");
    nextJokeInterval =
      setInterval(startJoke, 3000);
    currentJoke++;
    if (currentJoke >= jokes.length) {
      currentJoke = 0
    }
  }
}
```

你会回想起，在给出笑话的最后一行后调用了 hitJoker（如上所述，在 startLine 函数中）。在此函数被调用之前有一秒钟的延迟。一秒钟过去后，我们测试 0 到 1 之间的随机数，看它是否大于 0.33。如果不是，则什么都不发生，我们再等待一秒钟，然后再次调用此函数。这会持续发生，直到出现一个大于 0.33 的随机数。我这样设置是为了让每个笑话的拳头不会以固定间隔发生，这提供了一点更多的乐趣（好吧，这让我发笑！）。

一旦随机数满足 if 条件的要求，我们就清除每秒调用此函数一次的间隔。然后我们将动画发送到播放拳击序列，并设置另一个间隔以延迟下一个笑话的开始。我们等待的三秒钟（3000 毫秒）足够让拳击发生，并在 "noTalk" 帧处进行简短暂停（请记住，我们在动画中有一个动作，在拳击序列结束时将播放头发送到 "noTalk"）。

最后几行递增我们的当前笑话索引。如果我们已到达 jokes 数组的末尾，我们就循环回到顶部。通过添加足够的笑话，你应该能够确保用户在内容加载之前不会到达序列的末尾。

影片的最后一个函数。在 hitJoker 函数之后输入这些行：

```
revealLetters = function() {
  var line = jokes[currentJoke]
    [currentLine];
  bubble.text += line.charAt
    (currentLetter);
  currentLetter++;
  if (currentLetter > line.length) {
    clearInterval(letterInterval);
    currentLine++;
    nextLine = setInterval(startLine, 2000);
  }
}
```

revealLetters 负责我们文本的实际动画。它每 50 毫秒调用一次（在 startLine 函数中设置）。我们首先将当前行放入变量中以便轻松访问。接下来，我们将当前字母添加到气泡文本字段，并递增 currentLetter 变量。如果我们已到达当前行的最后一个字母，我们就清除调用此函数的间隔，递增我们的行变量，最后创建一个新间隔，在经过 2 秒后调用 startLine 函数（你能看出我有多喜欢新的 setInterval 命令吗？）。2 秒的延迟应该足够让用户阅读整行。

最后是最后两行：

```
startJoke();
preload = setInterval(assessLoad, 20, this);
```

startJoke 调用第一个笑话并启动整个过程。最后一行应该让你想起上一个练习。它设置一个间隔，每 20 毫秒调用一次 assessLoad，并传递额外参数 "this" 以让函数知道我们正在加载主影片。

测试你的影片，看看它是如何工作的。尝试添加一些笑话，或者将结构改为对话。考虑一位教授提供网站导航说明，或者一位新闻播音员向用户通报公司近期的事件。请记住，如果你添加更长的行，你将需要考虑气泡文本字段中的多行和自动换行。

加载时间会在不经意间过去，仅仅为了区区 7KB！

![](img/50202c17d5022233f3e3ec60560e35aa_32_0.png)

