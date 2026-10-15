
-   [![Image](graphics/note.jpg)](#)NOTE:
    这个条件语句以冒号结尾而不是左大括号。这是控制结构的替代语法。请参阅 [http://docs.php.net/manual/en/control-structures.alternative-syntax.php](http://docs.php.net/manual/en/control-structures.alternative-syntax.php)。

    `14` 要为子主题创建自己的默认设置，您需要将函数定义复制到 birds_phpcs5 版本的 functions.php 中。函数定义的开头如下（约在第 75 行）：

    function twentyten_setup() {  

        // 此主题使用 editor-style.css 对视觉编辑器进行样式设置，以匹配主题样式。  

        add_editor_style();

        函数定义的最后部分如下（约在第 171–178 行）：

        'sunset' => array(  

            'url' => '%s/images/headers/sunset.jpg',  

            'thumbnail_url' => '%s/images/headers/sunset-thumbnail.jpg',  

            /\* translators: header image description \*/  

            'description' => \_\_( 'Sunset', 'twentyten' )  

        )  

    );  

    }

    选择整个函数描述，并将其复制到剪贴板。

    `15` 将函数定义粘贴到 birds_phpcs5 文件夹中的 functions.php 中。如果您正确复制并粘贴了代码，Dreamweaver 在文档窗口顶部的信息栏中应显示“无语法错误”。

    `16` 向下滚动，找到下面的代码（约在第 35 行）：

    define( 'HEADER_IMAGE', '%s/images/headers/path.jpg' );

    这定义了 Twenty Ten 主题的默认表头图像（树荫小路）。要显示不同的图像，请修改文件名，例如：

    define( 'HEADER_IMAGE', '%s/images/headers/**cormorants.jpg**' );

    您稍后会在相应的文件夹中添加这些图像。

    `17` 约 20 行后的长代码段开头如下：

    register_default_headers( array(  

        'berries' => array(  

            'url' => '%s/images/headers/berries.jpg',  

            'thumbnail_url' => '%s/images/headers/berries-thumbnail.jpg',  

            /\* translators: header image description \*/  

            'description' => \_\_( 'Berries', 'twentyten' )  

        ),

    这段代码将多维数组传递给 `register_default_headers()`，这是 WordPress 3.0 引入的函数，用于定义主题提供的表头图像选项。默认 Twenty Ten 图像均为 940 像素宽、198 像素高，因此在子主题中无法适配。

    本课件的媒体文件包含两张表头图像（cormorants.jpg 和 seagulls.jpg），以及两张较小的版本（cormorants-thumbnail.jpg 和 seagulls-thumbnail.jpg）。请将数组中的所有 "berries" 实例改为 **cormorants**，并将 "cherryblossom(s)" 改为 **seagulls**。由于只有两张表头图像，需要删除其他六个子数组。完成后，functions.php 的最终部分应如下所示：

        register_default_headers( array(  

            '**cormorants**' => array(  

                'url' => '%s/images/headers/**cormorants**.jpg',  

                'thumbnail_url' => '%s/images/headers/**cormorants**-thumbnail.jpg',  

                /\* translators: header image description \*/  

                'description' => \_\_( '**Cormorants**', 'twentyten' )  

            ),  

            '**seagulls**' => array(  

                'url' => '%s/images/headers/**seagulls**.jpg',  

                'thumbnail_url' => '%s/images/headers/**seagulls**-thumbnail.jpg',  

                /\* translators: header image description \*/  

                'description' => \_\_( '**Seagulls**', 'twentyten' )  

            )  

        ) );  

    )

`19` 保存 functions.php 并将 cormorants.jpg、cormorants-thumbnail.jpg、seagulls.jpg 和 seagulls-thumbnail.jpg 从 lesson04/start/images 拷贝到 twentyten/images/headers。这些图像必须放在父主题文件夹中，因为 `register_default_headers()` 期望在此找到它们。

`20` 返回 WordPress 管理面板的“表头”页面。在“外观”菜单中点击“背景”，然后点击“表头”以反映您所做的更改。Custom Header 部分应现在显示两张 Birds of a Feather 表头图像，且“上传图像”部分应显示新的默认尺寸 960 × 150 像素。

![Image](graphics/fig04_15.jpg)

如有需要，可与 lesson04/completed/functions.php 中的代码进行比较。

#### **为子主题添加样式**

当前的任务是调整样式，使主题拥有独特的外观。大部分剩余任务在 Live View 和 CSS 样式面板中完成。

**1.** 如果 functions.php 仍然打开，请关闭它，并在 birds_phpcs5 文件夹中新建一个名为 **images** 的文件夹。将 birds_bg_gradient.jpg 从 lesson04/start/images 拷贝到新文件夹。稍后您将使用它作为新主题的背景图像。

**2.** 双击主 wordpress 文件夹中的 index.php，在文档窗口中打开它。如果需要，切换到设计视图，然后点击 Live View。Birds of a Feather 站点应显示新的默认表头和编辑后的侧边栏。

![Image](graphics/fig04_16.jpg)

**3.** 表头图像现在比菜单栏宽。要修复此问题，请在文档工具栏中点击“检查”按钮。在 Live View 中移动光标时，您会看到不同的区域被高亮显示。内容区域呈浅蓝色或青色，内边距为紫红色，外边距为黄色。

当您在元素之间移动光标时，当前高亮的元素也会在文档窗口底部的标签选择器中被选中。当光标位于页脚下方的黑色菜单栏上时，标签选择器应高亮显示 `<div#access>`。点击菜单栏以选中它。

**4** 选择元素会使“检查”按钮失效，从而允许您在不高亮其他元素的情况下移动光标。通过点击其标签页或选择 Window > CSS Styles 来打开 CSS 样式面板。在 Windows 上，您也可以使用快捷键 Shift+F11（Mac 不支持该快捷键）。

确保“当前”按钮处于 CSS 样式面板顶部，且中间部分的“规则”面板可见。如果中间部分标题为“关于”，请点击左侧的级联图标（如下图所示）。您可能需要关闭其他面板并拖动面板至 CSS 样式面板内部，以便查看列出的规则和属性。

![Image](graphics/fig04_17.jpg)

“规则”面板显示所有影响当前选中元素的样式规则。有时需要查看多个规则才能找到正确的一个，但在此情况下，应选中 Dreamweaver 先前显示的 `#access` 规则。

在“规则”面板中选择 `#access`。这表明 `width` 属性被设置为 `940px`。点击该数值进行编辑，并将数字改为 **960**。单位 `px` 由单独的菜单控制，无需修改。

![Image](graphics/fig04_18.jpg)

确认编辑后按 Enter/Return，Live View 中的菜单栏会扩展以匹配表头图像的宽度。

**5.** 虽然表头图像和菜单栏现在长度相同，但两侧各有约 20 像素的白色空白间隙。要找出间隙的原因，需要逐步排查；但在页面更下方，水平线两侧的相同间隙也可见。

再次点击“检查”按钮，将光标移至页脚，使水平线下方的完整宽度被高亮显示，然后点击选择该区域。

![Image](graphics/fig04_19.jpg)
