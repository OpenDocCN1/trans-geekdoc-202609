

## LUA 计算机科学

### 由 Christopher Andrew Topalian 撰写

版权所有
Copyright 2000-2024

### 献给天父上帝

## 下载 Lua

![](img/01c86b2ad179591527c53d35745207c8_2_0.png)

我们从以下网址下载 Lua：
https://luabinaries.sourceforge.net/download.html

在 Windows 上：下载名为以下文件：
lua-5.4.2_Win64_bin.zip
Windows x64 可执行文件

在 Mac 上：下载名为以下文件：
lua-5.4.2_MacOS1011_bin.tar.gz
MacOS X Intel 可执行文件

在 Linux 上：下载名为以下文件：
lua-5.4.2_Linux54_64_bin.tar.gz
Linux x64 可执行文件

## 提取 Lua 压缩包

![](img/01c86b2ad179591527c53d35745207c8_3_0.png)

右键单击下载的压缩文件夹
选择“全部提取…”

![](img/01c86b2ad179591527c53d35745207c8_3_1.png)

### 提取压缩（Zipped）文件夹

### 选择目标位置并提取文件

文件将被提取到以下文件夹：

C:\Users\energy\Downloads\lua\lua-5.4.2_Win64_bin

### 左键单击“提取”按钮

此电脑 > 下载 > lua

![](img/01c86b2ad179591527c53d35745207c8_4_0.png)

![](img/01c86b2ad179591527c53d35745207c8_4_1.png)

这是我们的 Lua 文件夹。现在它已解压，我们可以使用 Lua 文件夹中的 .exe 文件。

![](img/01c86b2ad179591527c53d35745207c8_5_0.png)

如上图所示，我们看到了 Lua 文件夹。该 Lua 文件夹包含 Lua .exe 文件。目前，这些文件带有版本号命名，例如 Lua54.exe。

但是，由于我们不希望每次使用 cmd 时都要输入版本号，我们可以将这些文件重命名为 lua（不带 54 版本号）。

因此，如下一页所示，让我们将这些文件重命名为仅名为 lua。lua54.exe 将被重命名为 lua.exe。

我们重命名 Lua .exe 文件的名称，以便我们以后使用 cmd 时更方便

![](img/01c86b2ad179591527c53d35745207c8_6_0.png)

如上图所示，Lua .exe 文件现在不带版本号命名。

我们更改了 exe 文件的名称，以便以后更方便地使用 cmd 访问我们的文件夹，因此要激活我们的脚本，我们现在只需在命令提示符中输入：

```
lua nameOfScript.lua
```

而不是

```
lua54 nameOfScript.lua
```

## 我们复制 Lua 文件夹的路径，以便以后用于 Lua 环境变量

![](img/01c86b2ad179591527c53d35745207c8_7_0.png)

我们已复制 Lua 文件夹的路径。它如下所示：

```
C:\Users\energy\Downloads\lua\lua-5.4.2_Win64_bin
```

我们稍后将使用此路径，在 Windows 上添加 Lua 环境变量，以便我们可以使用 cmd 运行脚本并在命令提示符中打开它们。

## 为 cmd 功能添加 Lua 环境变量

在 Windows 开始菜单中搜索：环境变量

![](img/01c86b2ad179591527c53d35745207c8_8_0.png)

我们左键单击：

编辑系统环境变量

### 系统属性打开，我们左键单击“环境变量”按钮

![](img/01c86b2ad179591527c53d35745207c8_9_0.png)

### 我们左键单击：“环境变量…”按钮

### 在系统变量中，在底部，我们左键单击 Path，然后左键单击“编辑”按钮

![](img/01c86b2ad179591527c53d35745207c8_10_0.png)

我们左键单击：Path

我们左键单击：编辑按钮

### 我们新建一个环境变量并粘贴 Lua 文件夹的地址

![](img/01c86b2ad179591527c53d35745207c8_11_0.png)

我们左键单击：
新建按钮

我们粘贴 Lua 文件夹地址：
Control + V 或右键单击“粘贴”

```
C:\Users\energy\Downloads\lua\lua-5.4.2_Win64_bin
```

我们左键单击：
确定按钮

### 我们左键单击环境变量的“确定”按钮以确认我们所做的更改

![](img/01c86b2ad179591527c53d35745207c8_12_0.png)

我们左键单击：确定按钮

### 我们左键单击系统属性的“确定”按钮以确认我们所做的更改

![](img/01c86b2ad179591527c53d35745207c8_13_0.png)

现在我们可以在计算机上使用 Lua 脚本。

祝脚本编写愉快 :-)

## 在 VSCode 编辑器中，我们新建文件并输入第一个 Lua 脚本，将其另存为 print.lua

![](img/01c86b2ad179591527c53d35745207c8_14_0.png)

VSCode 会对我们输入的 Lua 代码进行着色。

下一页有代码：print.lua

```
-- print.lua

print("Hi Everyone")

io.write("Press Enter to Exit")

io.read()

----

-- Hi Everyone
-- Press Enter to Exit
```

## 我们将 Lua 脚本另存为 print.lua

![](img/01c86b2ad179591527c53d35745207c8_16_0.png)

我们左键单击：
“另存为…”

我们新建名为以下文件夹：
ourFirstProject

下一页显示我们保存在 ourFirstProject 文件夹中的第一个 Lua 脚本。

### 我们左键单击“保存”按钮，将 Lua 脚本保存到 ourFirstProject 文件夹中

![](img/01c86b2ad179591527c53d35745207c8_17_0.png)

下一页，我们展示了一种在 VSCode 中轻松定位已保存脚本的简便方法，以便我们可以运行它。

### 在 VSCode 中，右键单击 print.lua 文件的标签页并选择“在文件资源管理器中显示”

![](img/01c86b2ad179591527c53d35745207c8_18_0.png)

### 我们右键单击：
print.lua 标签页

### 我们左键单击：
“在文件资源管理器中显示”

### 我们看到名为 print.lua 的 Lua 脚本，我们将其放在了名为 ourFirstProject 的文件夹中

![](img/01c86b2ad179591527c53d35745207c8_19_0.png)

### 我们左键单击：ourFirstProject 文件夹的地址栏

### 从左键单击 ourFirstProject 文件夹的地址栏，我们可以看到它现在已被高亮显示

![](img/01c86b2ad179591527c53d35745207c8_20_0.png)

现在地址栏已被高亮显示，即被选中，我们可以输入下一页所示的内容到此地址栏中，然后按键盘上的 Enter 键。

## 在文件夹地址栏中输入 cmd

![](img/01c86b2ad179591527c53d35745207c8_21_0.png)

我们输入：

cmd

按 Enter

## 我们看到命令提示符已在 ourFirstProject 文件夹中打开

```
C:\Windows\System32\cmd.exe
Microsoft Windows [Version 10.0.19045.4894]
(c) Microsoft Corporation. All rights reserved.

D:\_1Code\Lua\ourFirstProject>lua print.lua_
```

### 我们输入：

```
lua print.lua
```

按 Enter

```
C:\Windows\System32\cmd.exe
Microsoft Windows [Version 10.0.19045.4894]
(c) Microsoft Corporation. All rights reserved.

D:\_1Code\Lua\ourFirstProject>lua print.lua
Hi Everyone
```

### 激活代码的结果：

### Hi Everyone

```
-- print_comments.lua
```

```
print("Hi Everyone")
io.write("Press Enter to Exit")
io.read()
```

```
-- This is a single line comment in Lua
```

```
--[[
This is a multi line comment in Lua
We write our comments freely here
]]--
```

```
----
```

```
-- Hi Everyone
-- Press Enter to Exit
```

```
-- print_with_multiple_line_breaks.lua

print("Hi Everyone\n\nHappy Scripting")
io.write("Press Enter to Exit")
io.read()
```

```
--[[
Hi Everyone
Happy Scripting
Press Enter to Exit
--]]
```

```
-- print_variable_integer.lua

local ourInteger = 25

print(ourInteger)

io.write("Press Enter to Exit")
io.read()

-- 25

-- Press Enter to Exit
```

```
-- print_variable_string.lua

numberOfPeople = "Twenty"
print(numberOfPeople)
io.write("Press Enter to Exit")
io.read()
```

----

```
--[[ 
Twenty 
Press Enter to Exit 
--]]
```

```
-- open_browser.lua

local url = "https://www.x.com"

io.popen('start "" "" .. url .. ""')

print(url .. " is opened")

io.write("Press Enter to Exit")
io.read()
```

----

```
--[[
https://www.google.com is opened
Press Enter to Exit
]]--
```

```
-- open_a_file_in_write_mode.lua

local file = io.open("001.txt",
"w")

-- write content to the file
file:write("Hi Everyone\n")
file:write("Here is more text")

-- close file to save changes
file:close()

io.write("Press Enter to Exit")
io.read()
```

```lua
-- read_text_file.lua
local file = io.open("001.txt", "r")
-- check if file was opened
if file then
    -- read each line of file
    for line in file:lines() do
        print(line)
    end
    -- close file after reading
    file:close()
else
    print("File did not open")
end
io.write("Press Enter to Exit")
io.read()
```

