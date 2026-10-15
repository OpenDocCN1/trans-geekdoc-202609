
1. 在 Dreamweaver 文件面板中，展开 wordpress 和 wp-content 文件夹，选择 themes 文件夹，右键单击并选择“新建文件夹”。新建的文件夹名称为 `birds_phpcs5`，该文件夹应位于 themes 文件夹内部且与 twentyten 同级。

![Image](graphics/fig04_10.jpg)

2. 展开 twentyten 文件夹，双击 style.css 打开它，在文档窗口中编辑。

3. style.css 的前八行内容如下：

```
/*  

Theme Name: Twenty Ten  

Theme URI: http://wordpress.org/  

Description: The 2010 default theme for WordPress.  

Author: the WordPress team  

Version: 1.0  

Tags: black, blue, white, two-columns, fixed-width, custom-header, custom-background, theme-options, threaded-comments, sticky-post, translation-ready, microformats, rtl-language-support, editor-style  

*/
```

这段代码告诉 WordPress 主题的名称以及一些基本信息。

4. 选择 **File > Save As** 或按 **Ctrl+Shift+S/Shift+Cmd+S**。在“保存为”对话框中，导航到 `birds_phpcs5` 文件夹，并以相同的文件名（style.css）保存。当系统询问是否更新链接时，点击 **No**。

5. 关闭原始 style.css，确保正在编辑的文件位于 `birds_phpcs5` 文件夹中。文件路径应在浏览器导航栏中可见。

![Image](graphics/fig04_11.jpg)

或者，点击 **Coding** 工作栏顶部的 **Open Documents** 图标 ![Image](graphics/open-doc.jpg) 来显示文件路径。

6. 主题名称注释必须包含唯一名称，且不能仅由数字组成（因此是 “Twenty Ten”，而不是 “2010”）。在创建子主题时，需要指定父主题作为子主题的模板。缺少这两项更改，WordPress 将无法识别子主题。顶部注释的其余部分是可选的，按以下方式修改 style.css 顶部的注释：

```
/*  

Theme Name: **Birds of a Feather**  

**Template: twentyten**  

Theme URI: **http://foundationphp.com/phpcs5/**  

Description: **Adaptation of** the 2010 default theme for WordPress.  

Author: **David Powers, but mainly** the WordPress team  

Version: 1.0  

Tags: **purple, pink,** blue, white, two-columns, fixed-width, custom-header, custom-background, theme-options, threaded-comments, sticky-post, translation-ready, microformats, rtl-language-support, editor-style  

*/
```

父主题通过 `Template` 后跟冒号及其文件夹名称来标识。

7. 保存 style.css 并关闭它。

8. 这已足够让 WordPress 识别新主题，但建议为其添加一张图片以便在仪表盘中与其他主题区分。图片宽度约为 300 像素，文件名必须为 `screenshot.png`。将 `lesson04/start/images` 中的 `screenshot.png` 复制到 `birds_phpcs5` 文件夹。子主题文件夹中现在包含两个文件。

![Image](graphics/fig04_12.jpg)

稍后会添加更多文件，但目前已足够。

### ![Image](graphics/tip.jpg)**TIP:**

如果你在 Fireworks、Photoshop 等图形编辑程序中制作最终设计的 mockup，可以通过缩放 mockup 并导出为 `.png` 文件来生成 `screenshot.png`。如果找不到 `screenshot.png`，WordPress 会显示主题的文字描述。

#### **激活子主题**

在激活子主题之前，需要先在 WordPress 仪表盘中激活它。

**1.** 在浏览器中登录 WordPress 仪表盘。根据测试环境的设置，URL 可能是以下任一：

• **虚拟主机。** [http://phpcs5/wordpress/wp-admin/](http://phpcs5/wordpress/wp-admin/)

• **本地主机。** [http://localhost/phpcs5/wordpress/wp-admin/](http://localhost/phpcs5/wordpress/wp-admin/)

**2** 在左侧栏的 **Appearance** 部分展开，选择 **Themes**。新主题 “Birds of a Feather” 应出现在 **Available Themes** 区域。

![Image](graphics/fig04_13.jpg)

**3.** 点击 “Birds of a Feather” 主题的 **Activate** 链接。几秒后，该主题成为 **Current Theme**，而 Twenty Ten 移至 **Available Themes** 区域。

**4.** 在 **Appearance** 菜单中点击 **Widgets** 打开小部件设置页面。子主题会继承 Twenty Ten 主题的默认设置。现阶段，只需将 **Recent Comments** 和 **Meta** 小部件从 **Primary Widget Area**（主侧边栏）拖回 **Available Widgets** 区域即可。

**5.** 将 **Categories** 小部件拖动到 **Search** 小部件下方。此时 **Primary Widget Area** 应呈现如下：

![Image](graphics/fig04_14.jpg)

**6** 点击 **Appearance** 菜单中的 **Background** 链接。该功能用于设置背景图片和颜色，但它会在页面头部生成 `<style>` 块。更好的做法是使用 `style.css` 处理背景，因此保持该页面不变。

**7.** 点击 **Appearance** 菜单中的 **Header** 链接。Twenty Ten 主题提供了八种默认表头图片供选择，也支持上传自定义图片。若图片尺寸不是 Twenty Ten 要求的 940 × 198 像素，会提示进行裁剪。WordPress 不会裁剪原图，而是复制一份。若图片高度低于 198 像素，则会被拉伸，效果往往不理想。

表头图片的宽高由 Twenty Ten 主题中的自定义函数控制。要修改默认值，需要覆盖该函数。保持浏览器打开当前页面，返回 Dreamweaver。

**8.** WordPress 主题的自定义函数存放在 `functions.php` 文件中。若尝试重定义已存在的函数，PHP 会报 fatal error，但 WordPress 通过条件语句规避此问题。父主题的 `functions.php` 中的所有函数都包含在检查函数是否已定义的条件语句内：若未定义同名函数，则父主题定义该函数；否则使用子主题定义的函数。

选择 **File > New**，设置 **Page Type** 为 **PHP**，**Layout** 为 **<none>**，然后点击 **Create**。切换到 **Code** 视图，删除 Dreamweaver 自动插入的所有 HTML 代码。此时应得到一张完全空白的页面。

**9.** 在新建页面的顶部添加打开的 PHP 标签，并将其保存为 **functions.php**，放在 `birds_phpcs5` 文件夹中。

**10** 双击 `twentyten` 文件夹中的 `functions.php` 打开它。文件包含大量注释，帮助你理解每个函数的作用及如何对其进行覆盖。

**11** 向下滚动至大约第 47 行，找到以下代码：

```
if ( ! isset( $content_width ) )  
    $content_width = 640;
```

这段代码在 Twenty Ten 主题中定义主内容 `<div>` 的宽度，仅在 `$content_width` 未定义时才设为 640（像素）。因此，要修改宽度，需要在子主题的 `functions.php` 中添加 `$content_width`；否则将使用默认值。

**12** “Birds of a Feather” 的表头图片比 Twenty Ten 宽 20 像素，可相应扩展内容宽度 20 像素。在为子主题创建的空 `functions.php` 文件中，于打开的 PHP 标签后添加以下代码：

<?php  

**$content_width = 660;**

**13** 切换回 Twenty Ten 版本的 `functions.php`，向下滚动至大约第 53 行，找到以下代码：

```
if ( ! function_exists( 'twentyten_setup' )):
```

该条件语句检查 `twentyten_setup()` 函数是否已定义。若未定义，则创建该函数，用于设定 Twenty Ten 主题的默认设置。
