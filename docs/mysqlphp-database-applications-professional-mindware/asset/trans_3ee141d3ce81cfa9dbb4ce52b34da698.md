
它们对 gif 图像的支持。在此，如果你想使用 GD 函数处理 gif 图像，你需要使用早于 1.6 版本的 GD 库。然而，这些旧库不支持 png 文件。1.6 之后的版本支持 png。

## 表 E-29 GD 函数

| 函数 | 返回 | 操作 |
|---|---|---|
| imagecreate(int x_size, int y_size) | int | 创建一个新图像 |
| imagetypes(void) | int | 返回以位字段形式支持的图像类型 — 1=gif, 2=jpeg, 4=png, 8=wbmp |
| imagecreatefromgif (string filename) | int | 从 GIF 文件或 URL 创建一个新图像 |
| imagecreatefromjpeg (string filename) | int | 从 JPEG 文件或 URL 创建一个新图像 |
| imagecreatefrompng (string filename) | int | 从 PNG 文件或 URL 创建一个新图像 |
| imagecreatefromwbmp (string filename) | int | 从 WBMP 文件或 URL 创建一个新图像 |
| imagegif(int im [, string filename]) | int | 将 GIF 图像输出到浏览器或文件 |
| imagepng(int im [, string filename]) | int | 将 PNG 图像输出到浏览器或文件 |
| imagejpeg(int im [, string filename [, int quality]]) | int | 将 JPEG 图像输出到浏览器或文件 |
| imagewbmp(int im [, string filename]) | int | 将 WBMP 图像输出到浏览器或文件 |
| imagedestroy(int im) | int | 销毁一个图像 |
| imagecolorallocate(int im, int red, int green, int blue) | int | 为图像分配颜色，通常会分配给变量以供以后使用。 |

## 表 E-29 GD 函数（续）

| 函数 | 返回 | 操作 |
|---|---|---|
| `imagepalettecopy(int dst, int src, int blue)` | int | 将调色板从 src 图像复制到 dst 图像，将调色板复制到指定颜色 |
| `imagecolorclosesthwb(int im, int red, int green, int blue)` | int | 获取与给定颜色色相、白度、黑度最接近的颜色的索引 |
| `imagecolordeallocate(int im, int index)` | int | 为图像取消分配颜色 |
| `imagecolorresolve(int im, int red, int green, int blue)` | int | 获取指定颜色的索引或其最接近的替代品 |
| `imagecolorexact(int im, int red, int green, int blue)` | int | 获取指定颜色的索引。如果颜色不存在则返回 -1 |
| `imagecolorset(int im, int col, int red, int green, int blue)` | int | 设置指定调色板索引的颜色 |
| `imagecolorsforindex(int im, int col)` | array | 获取索引的颜色，以红、绿、蓝表示 |
| `imagegammacorrect(int im, double inputgamma, double outputgamma)` | int | 对 GD 图像应用伽马校正 |
| `imagesetpixel(int im, int x, int y, int col)` | int | 设置单个像素；x 和 y 坐标从左上角开始，col 是像素的颜色 |
| `imageline(int im, int x1, int y1, int x2, int y2, int col)` | int | 绘制一条线 |
| `imagedashedline(int im, int x1, int y1, int x2, int y2, int col)` | int | 绘制虚线 |
| `imagerectangle(int im, int x1, int y1, int x2, int y2, int col)` | int | 绘制矩形 |

| 函数 | 返回 | 操作 |
|---|---|---|
| imagefilledrectangle (int im, int x1, int y1, int x2, int y2, int col) | int | 绘制填充矩形 |
| imagearc(int im, int cx, int cy, int w, int h, int s, int e, int col) | int | 绘制部分椭圆 |
| imagefilltoborder(int im, int x, int y, int border, int col) | int | 用第五个参数中的颜色填充图像 im，直到由 x 和 y 坐标指定的边界 |
| imagefill(int im, int x, int y, int col) | int | 从 x 和 y 坐标开始使用第四个参数指定的颜色进行漫反射填充 |
| imagecolorstotal(int im) | int | 返回图像调色板中的颜色数量 |
| imagecolortransparent (int im [, int col]) | int | 将颜色定义为透明。返回新颜色的标识符 |
| imageinterlace(int im [, int interlace]) | int | 启用或禁用隔行扫描 |
| imagepolygon(int im, array point, int num_points, int col) | int | 绘制多边形。数组将采用以下形式：points[0] = x0, points[1] = y0, points[2] = x1, points[3] = y1 |
| imagefilledpolygon(int im, array point, int num_points, int col) | int | 绘制填充多边形 |
| imagefontwidth(int font) | int | 获取字体宽度 |
| imagefontheight(int font) | int | 获取字体高度 |
| imagechar(int im, int font, int x, int y, string c, int col) | int | 绘制字符 |

## 表 E-29 GD 函数（续）

| 函数 | 返回 | 操作 |
|---|---|---|
| imagecharup(int im, int font, int x, int y, string c, int col) | int | 绘制逆时针旋转 90 度的字符 |
| imagestring(int im, int font, int x, int y, string str, int col) | int | 水平绘制字符串 |
| imagestringup(int im, int font, int x, int y, string str, int col) | int | 垂直绘制字符串 — 逆时针旋转 90 度 |
| imagecopy(int dst_im, int src_im, int dst_x, int dst_y, int src_x, int src_y, int src_w, int src_h) | int | 复制图像的一部分 |
| imagecopymerge(int src_im, int dst_im, int dst_x, int dst_y, int src_x, int src_y, int src_w, int src_h, int pct) | int | 将图像的一部分与另一部分合并 |
| imagecopyresized(int dst_im, int src_im, int dst_x, int dst_y, int src_x, int src_y, int dst_w, int dst_h, int src_w, int src_h) | int | 复制并调整图像的一部分大小 |
| imagesx(int im) | int | 获取图像宽度 |
| imagesy(int im) | int | 获取图像高度 |
| imagettfbbox(int size, int angle, string font_file, string text) | array | 使用 TrueType 字体给出文本的边界框 |
| imagettftext(int im, int size, int angle, int x, int y, int col, string font_file, string text) | array | 使用 TrueType 字体将文本写入图像 |
| imagepsloadfont(string pathname) | int | 从指定文件加载新字体 |

| 函数 | 返回 | 操作 |
|---|---|---|
| imagepsfreefont (int font_index) | bool | 释放字体使用的内存 |
| imagepsextendfont (int font_index, double extend) | bool | 扩展或压缩（如果 extend < 1）字体 |
| imagepstext(int image, string text, int font, int size, int xcoord, int ycoord [, int space, int tightness, double angle, int antialias]) | array | 在图像上绘制文本字符串 |
| imagepsloadfont(string pathname) | int | 从指定文件加载新字体 |
| imagepsfreefont(int font_index) | bool | 释放字体使用的内存 |
| imagepsencodefont(int font_index, string filename) | bool | 更改字体的字符编码向量 |
| imagepsextendfont(int font_index, double extend) | bool | 扩展或压缩（如果 extend < 1）字体 |
| imagepsslantfont(int font_index, double slant) | bool | 倾斜字体 |
| imagepstext(int image, string text, int font, int size, int xcoord, int ycoord [, int space, int tightness, double angle, int antialias]) | array | 将字符串光栅化到图像上 |
| imagepsbbox(string text, int font, int size [, int space, int tightness, int angle]) | array | 如果光栅化，返回字符串所需的边界框 |
| imagepsbbox(string text, int font, int size [, int space, int tightness, int angle]) | array | 如果光栅化，返回字符串所需的边界框 |

![](img/de0823012275cf4ceebdb822a56e6b71_510_0.png)

使用这些函数需要来自 http://www.boutell.com/gd/ 的 GD 库，并且 PHP 需要编译 --with-gd。

## 表 E-30 IMAP 函数

| 函数 | 返回 | 操作 |
|---|---|---|
| `imap_open(string mailbox, string user, string password [, int options])` | int | 打开到邮箱的 IMAP 流 |
| `imap_popen(string mailbox, string user, string password [, int options])` | int | 打开到邮箱的持久 IMAP 流 |
| `imap_reopen(int stream_id, string mailbox [, int options])` | int | 重新打开 IMAP 流到新的邮箱 |
| `imap_close(int stream_id [, int options])` | int | 关闭 IMAP 流 |
| `imap_append(int stream_id, string folder, string message [, string flags])` | int | 向指定邮箱追加新消息 |
| `imap_num_msg(int stream_id)` | int | 给出当前邮箱中的消息数量 |
| `imap_ping(int stream_id)` | int | 检查 IMAP 流是否仍处于活动状态 |
| `imap_num_recent(int stream_id)` | int | 给出当前邮箱中最近消息的数量 |
| `imap_expunge(int stream_id)` | int | 永久删除所有标记为删除的消息 |
| `imap_headers(int stream_id)` | array | 返回邮箱中所有消息的头 |
| `imap_body(int stream_id, int msg_no [, int options])` | string | 读取消息正文 |

