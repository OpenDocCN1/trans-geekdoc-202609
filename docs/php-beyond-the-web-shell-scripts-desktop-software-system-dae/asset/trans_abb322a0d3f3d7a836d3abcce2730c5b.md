

```php
<?php

# 每个框架或窗口都是通过扩展 wxFrame 类并
# 添加按钮、菜单、文本框等图形元素，
# 以及对“事件”（如鼠标单击和窗口关闭）做出反应的任何函数来设计的。

# 我们将创建一个名为 "MainFrame" 的类来描述我们应用程序的窗口

class MainFrame extends wxFrame
{

	# 我们将添加一个函数，在退出时销毁框架对象。

	function onQuit()
	{
		$this->Destroy();
	}

	# 我们将添加一个函数来显示“关于”对话框，以显示一些
	# 关于应用程序的信息

	function onAbout()
	{
		# "wxMessageDialog" 是工具包中可用的众多组件或“小部件”之一。
		# 这使你无需创建新的框架/窗口来显示消息。

		$dlg = new wxMessageDialog(
			$this,
			"Welcome to wxPHP!!\nBased on wxWidgets 3.0.0\n\n".
			"This is a minimal wxPHP sample!",
			"About box...",
			wxICON_INFORMATION
			);

		# 显示我们上面创建的对话框。

		$dlg->ShowModal();
	}

	# 添加一个构造函数。当我们通过从该类创建新对象来创建应用程序窗口时，
	# 将运行此函数。

	function __construct()
	{
		# 这将调用我们扩展的 wxFrame 类中的构造函数，
		# 创建一个标题为 "Minimal wxPHP App" 的框架，位于屏幕的默认位置，
		# 初始大小为 350 x 260 像素。请注意，此框架默认不可见，
		# 目前只是在内存中创建。这意味着我们可以在向用户显示它之前，
		# 向其中添加内容并完全准备好它，而不是让用户看到一个空白窗口，
		# 然后突然填满按钮等内容。

		parent::__construct(null, null, "Minimal wxPHP App", 
			wxDefaultPosition, new wxSize(350, 260));

		# 我们将向窗口添加带有各种选项的菜单，
		# 这意味着首先要添加一个菜单栏，然后将菜单放入其中。

		$mb = new wxMenuBar();

		# 现在我们添加菜单。首先是一个带有“退出”选项的“文件”菜单

		$mn = new wxMenu();
		$mn->Append(2, "E&xit", "Quit this program");
		$mb->Append($mn, "&File");

		# 然后是一个带有“关于”选项的“帮助”菜单。

		$mn = new wxMenu();
		$mn->AppendCheckItem(4, "&About...", "Show about dialog");
		$mb->Append($mn, "&Help");

		# 请注意，上面的菜单和选项都带有“&”符号。
		# 这出现在应作为键盘快捷键使用的字母之前。
		# 使用这种小部件工具包意味着你不需要为管理键盘快捷键等事项编写自己的代码，
		# 这节省了时间和精力，并为用户创造一致的体验。

		# 最后将菜单栏添加到框架。

		$this->SetMenuBar($mb);

		# 让我们向框架添加一个源代码编辑框，这是工具包中可用的另一个小部件，
		# 具有语法高亮、智能缩进等功能。

		$scite = new wxStyledTextCtrl($this);

		# 我们将添加的最后一个小部件是窗口底部的状态栏。

		$sbar = $this->CreateStatusBar(2);
		$sbar->SetStatusText("Welcome to wxPHP...");

		# 在类开头，我们定义了几个函数，一个用于显示关于框，
		# 一个用于退出应用程序。单独使用它们不会有任何作用，
		# 我们需要将它们连接到我们之前创建的菜单选项。更具体地说，
		# 是连接到当用户从菜单中选择某项时调用的 "wxEVT_COMMAND_MENU_SELECTED" 事件。

		$this->Connect(2, wxEVT_COMMAND_MENU_SELECTED, 
			array($this,"onQuit"));
		$this->Connect(4, wxEVT_COMMAND_MENU_SELECTED, 
			array($this,"onAbout"));
	}
}

# 我们现在已经设计了框架，并用小部件和函数填充了它，
# 但在这个阶段，代码中它尚不存在。我们需要使用我们的类创建一个新对象，
# 这将使其“活”过来并调用上面的构造函数。

$mf = new mainFrame();

# 框架现在已经存在，已填充小部件，函数也都已连接到事件。
# 但是它是隐藏的，所以我们需要使其可见。

$mf->Show();

# 此时，我们需要让 wxWidgets 接管并运行程序。
# 调用 wxEntry 让 wxWidgets 管理应用程序，等待并响应事件，
# 并调用我们之前指定的函数。如你所见，我们需要在到达这一点之前
# 指定所有应用程序代码。

wxEntry();  

# 如果我们到达这一点，意味着我们的应用程序已退出（无论是用户关闭了它，
# 还是我们代码中的某些内容关闭了它），我们可以执行必要的清理工作，
# 或者直接退出。

?>
```

安装 wxPHP 后，上述代码可以简单地保存为 `myapp.php` 之类的文件，并像任何其他 PHP CLI 脚本一样执行，例如通过调用 `php myapp.php`。

从上面的代码可以看出，与过程式 Web 脚本的主要区别之一是，我们通常不会在运行过程中执行代码。所有内容都预先定义，通常在类中，并在响应用户输入时按需执行。这就是为什么面向对象代码特别适合 GUI 和基于事件的编程，因为它提供了一个模型，能更自然地映射到通常“非顺序执行”的代码，而窗口和小部件的视觉隐喻也与类和对象的编程隐喻自然关联。

上面的示例非常简单，并不特别有用。要查看使用 wxPHP 编写的完整且有用的应用程序示例，请参阅下面的 `phar-gui` 项目。这是由 wxPHP 项目维护者编写的开源 Phar 文件资源管理器（有关 Phar 文件的信息请参见第 10 章）。它展示了较大应用程序的结构，并演示了使用 wxFormBuilder 应用程序设计图形界面。

| ![](Images/image00249.gif) || `wxPHP` |

| --- | --- |

|   ||   |

|   || RAD 类型的 wxWidgets 工具包 |

|   ||   |

|   || `主网站` : [http://www.wxphp.org/](http://www.wxphp.org/) |

|   ||   |

|   || `主文档和安装信息` : [http://www.wxphp.org/docs](http://www.wxphp.org/docs)，另请参见 [https://github.com/wxphp/wxphp#table-of-contents](https://github.com/wxphp/wxphp#table-of-contents) |

|   ||   |

|   || `界面设计工具` : [http://sourceforge.net/projects/wxformbuilder/](http://sourceforge.net/projects/wxformbuilder/) |

|   ||   |

|   || `设计工具文档` : [http://sourceforge.net/apps/mediawiki/wxformbuilder/index.php?title=HomePage](http://sourceforge.net/apps/mediawiki/wxformbuilder/index.php?title=HomePage) |

|   ||   |

|   || `为 Raspian (树莓派) 构建的版本` : [http://www.wxphp.org/news/raspberry-pi-raspbian-binary-build](http://www.wxphp.org/news/raspberry-pi-raspbian-binary-build) |

|   ||   |

|   || `phar-gui 工具` : [https://github.com/jgmdev/phar-gui](https://github.com/jgmdev/phar-gui) |

### 5.11 PHP-GTK

