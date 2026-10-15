
-   [使用浏览器事件](#)  
    你是否见过网站在关闭前要求确认的情况？这种行为在某些网站上会非常烦人，尤其是当网站每次点击“确定”后仍然弹出相同的确认框时。

    这正是你可以让受控目标在特定页面上停留更长时间的方法。在某些情况下，停留在钩钓页面几秒钟可以让更多的命令模块被执行。记住，停留时间越长，越好。

    该技术依赖于处理 `window` 对象的 `onbeforeunload` 事件，默认触发条件包括：

    *   当 `unload` 事件发生时 —  — 你关闭了当前标签页、整个浏览器，或简单地离开页面  
    *   当调用 `window.close` 或 `document.close` 时  
    *   当调用 `location.replace` 或 `location.reload` 时  

    以下是一个在所有桌面浏览器（Opera 12 之前除外）中均可工作的基本实现：

    ```javascript
    function display_confirm(){
      if(confirm("Are you sure you want to navigate away from this  
        page?\n\n There is currently a request to the server pending.  
        You will lose recent changes by navigating away.\n\n Press OK   
        to continue, or Cancel to stay on the current page.")){
        display_confirm();
      }
    }

    function dontleave(e){
      e = e || window.event;

      // 如果是 Internet Explorer，语法略有不同
      if(browser.isIE()){
        e.cancelBubble = true;
        e.returnValue = "There is currently a request to the server 
          pending. You will lose recent changes by navigating away.";
      }else{
        if (e.stopPropagation) {
          e.stopPropagation();
          e.preventDefault();
          e.returnValue = "There is currently a request to the server   
            pending. You will lose recent changes by navigating away.";
        }
      }

      // 重新显示确认框，让用户点击“确定”时感到烦扰
      display_confirm();
      return "There is currently a request to the server pending. You  
        will lose recent changes by navigating away.";
    }

    window.onbeforeunload = dontleave;
    ```

    该示例会覆盖已有的 `onbeforeunload` 处理函数并执行 `dontleave` 函数。为进一步防止冲突，使用 `cancelBubble` 方法在 Internet Explorer 中阻止事件冒泡，从而阻止已有函数干扰新代码。根据现有 JavaScript 代码的复杂程度，阻止事件冒泡也是提升性能的好办法。如果有许多嵌套元素，直接覆盖原有代码并阻止冒泡可能是个不错的选择。

    浏览器间的行为略有差异。如图 [3-10](#c03.html#figure3-10) 和 [3-11](#c03.html#figure3-11) 所示，Firefox 18 的表现如下：如果受害者点击“取消”，第二个确认框会自动弹出；如果点击“确定”，确认框会在循环中不断重复显示。唯一真正离开页面的操作是点击“离开页面”，如图 [3-11](#c03.html#figure3-11) 所示。

    start figure  
    [**Figure 3-10:**](#c03.html#figureanchor3-10) First dialog on Firefox 18 with custom content (controlled with JavaScript)  
    ![c03f010.tif](image_fi/662090c03/c03f010.png)  
    end figure  
    start figure  
    [**Figure 3-11:**](#c03.html#figureanchor3-11) Second dialog on Firefox 18 (can’t be controlled with JavaScript)  
    ![c03f011.tif](image_fi/662090c03/c03f011.png)  
    end figure  

    在 Internet Explorer 9（Windows 7）上的行为非常相似，但你可以对对话框文本拥有更多控制，如图 [3-12](#c03.html#figure3-12) 和 [3-13](#c03.html#figure3-13) 所示。[Figure 3-13](#c03.html#figure3-13) 中的第二个对话框文本也可以自定义。总体行为与 Firefox 相同。

    start figure  
    [**Figure 3-12:**](#c03.html#figureanchor3-12) First dialog box on IE 9 with custom content (controlled with JavaScript)  
    ![c03f012.tif](image_fi/662090c03/c03f012.png)  
    end figure  
    start figure  
    [**Figure 3-13:**](#c03.html#figureanchor3-13) Second dialog box on IE 9 (controlled with JavaScript)  
    ![c03f013.tif](image_fi/662090c03/c03f013.png)  
    end figure  

    因此，你可能只想在 Internet Explorer 浏览器上使用此关闭技术，因为 Firefox 和 Chrome 在自定义消息方面的功能受限。

    作为保持持久性的方法，使用这些事件可能为你提供几秒钟的执行时间，但它们并不是理想的长期控制手段。弹出下方窗口（pop-under window）将在下一节中讨论，可能为你提供保留对被钩浏览器控制的新机会。当然，你也可以组合多种技术，通过层叠自定义关闭事件处理例程；使用 IFrames 和弹出下方窗口，你可能会在完成所需命令前保持钩钓时间足够长。

## 使用弹出下方窗口

