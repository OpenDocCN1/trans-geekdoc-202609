
## 表 F-28 PDF 函数（续）

| Function | Return Value | Action |
|---|---|---|
| pdf_set_horiz_scaling(int pdfdoc, float scale) | void | 设置文本的水平缩放 |
| pdf_set_text_rise(int pdfdoc, float value) | void | 设置文本上升 |
| pdf_set_char_spacing(int pdfdoc, float space) | void | 设置字符间距 |
| pdf_set_word_spacing(int pdfdoc, float space) | void | 设置单词间距 |
| pdf_set_text_pos(int pdfdoc, float x, float y) | void | 为下一次 pdf_show 调用设置文本位置 |
| pdf_continue_text(int pdfdoc, string text) | void | 在下一行输出文本 |
| pdf_stringwidth(int pdfdoc, string text [, int font, float size]) | float | 返回当前字体中文本的宽度 |
| pdf_save(int pdfdoc) | void | 保存当前环境 |
| pdf_restore(int pdfdoc) | void | 恢复先前保存的环境 |
| pdf_translate(int pdfdoc, float x, float y) | void | 设置坐标系原点 |
| pdf_scale(int pdfdoc, float x_scale, float y_scale) | void | 设置缩放 |
| pdf_rotate(int pdfdoc, float angle) | void | 设置旋转 |
| pdf_skew(int pdfdoc, float xangle, float yangle) | void | 倾斜坐标系 |
| pdf_setflat(int pdfdoc, float value) | void | 设置平坦度 |
| pdf_setlinejoin(int pdfdoc, int value) | void | 设置线连接参数 |
| pdf_setlinecap(int pdfdoc, int value) | void | 设置线端点参数 |
| pdf_setmiterlimit(int pdfdoc, float value) | void | 设置斜接限度 |
| pdf_setlinewidth(int pdfdoc, float width) | void | 设置线宽 |
| pdf_setdash(int pdfdoc, float black, float white) | void | 设置虚线模式 |
| pdf_moveto(int pdfdoc, float x, float y) | void | 设置当前点 |
| pdf_curveto(int pdfdoc, float x1, float y1, float x2, float y2, float x3, float y3) | void | 绘制曲线 |
| pdf_lineto(int pdfdoc, float x, float y) | void | 绘制线 |
| pdf_circle(int pdfdoc, float x, float y, float radius) | void | 绘制圆 |
| pdf_arc(int pdfdoc, float x, float y, float radius, float start, float end) | void | 绘制弧 |
| pdf_rect(int pdfdoc, float x, float y, float width, float height) | void | 绘制矩形 |
| pdf_closepath(int pdfdoc) | void | 关闭路径 |
| pdf_closepath_stroke(int pdfdoc) | void | 关闭路径并沿路径绘制线 |
| pdf_stroke(int pdfdoc) | void | 沿路径绘制线 |
| pdf_fill(int pdfdoc) | void | 填充当前路径 |
| pdf_fill_stroke(int pdfdoc) | void | 填充并描边当前路径 |
| pdf_closepath_fill_stroke(int pdfdoc) | void | 关闭、填充并描边当前路径 |
| pdf_endpath(int pdfdoc) | void | 结束当前路径 |
| pdf_clip(int pdfdoc) | void | 裁剪到当前路径 |
| pdf_set_parameter(int pdfdoc, string key, string value) | void | 设置任意参数 |
| pdf_get_parameter(int pdfdoc, string key, mixed modifier) | string | 获取任意参数 |
| pdf_setgray_fill(int pdfdoc, float value) | void | 将填充颜色设置为灰度值 |
| pdf_setgray_stroke(int pdfdoc, float value) | void | 将绘制颜色设置为灰度值 |
| pdf_setgray(int pdfdoc, float value) | void | 将绘制和填充颜色设置为灰度值 |
| pdf_setrgbcolor_fill(int pdfdoc, float red, float green, float blue) | void | 将填充颜色设置为 RGB 颜色值 |
| pdf_setrgbcolor_stroke(int pdfdoc, float red, float green, float blue) | void | 将绘制颜色设置为 RGB 颜色值 |
| pdf_setrgbcolor(int pdfdoc, float red, float green, float blue) | void | 将绘制和填充颜色设置为 RGB 颜色值 |
| pdf_add_bookmark(int pdfdoc, string text [, int parent, int open]) | int | 为当前页面添加书签 |
| pdf_set_transition(int pdfdoc, int transition) | void | 设置页面之间的过渡效果 |
| pdf_set_duration(int pdfdoc, float duration) | void | 设置页面之间的持续时间 |
| pdf_open_gif(int pdf, string giffile) | int | 打开 GIF 文件并返回用于放置在 PDF 对象中的图像 |
| pdf_open_jpeg(int pdf, string jpegfile) | int | 打开 JPEG 文件并返回用于放置在 PDF 文档中的图像 |
| pdf_open_png(int pdf, string pngfile) | int | 打开 PNG 文件并返回用于放置在 PDF 文档中的图像 |
| pdf_open_tiff(int pdf, string tifffile) | int | 打开 TIFF 文件并返回用于放置在 PDF 文档中的图像 |
| pdf_open_image_file(int pdf, string type, string file, string stringparam, int intparam) | int | 打开指定类型的图像文件并返回用于放置在 PDF 文档中的图像 |
| pdf_open_memory_image(int pdf, int image) | int | 获取 GD 图像并返回用于放置在 PDF 文档中的图像 |
| pdf_close_image(int pdf, int pdfimage) | void | 关闭 PDF 图像 |
| pdf_place_image(int pdf, int pdfimage, float x, float y, float scale) | void | 在 PDF 文档中放置图像 |
| pdf_get_image_width(int pdf, int pdfimage) | int | 返回图像的宽度 |
| pdf_get_image_height(int pdf, int pdfimage) | int | 返回图像的高度 |
| pdf_add_weblink(int pdfdoc, float llx, float lly, float urx, float ury, string url) | void | 添加指向 Web 资源的链接 |
| pdf_add_pdflink(int pdfdoc, float llx, float lly, float urx, float ury, string filename, int page, string dest) | void | 添加指向 PDF 文档的链接 |
| pdf_set_border_style(int pdfdoc, string style, float width) | void | 设置围绕各种注释和链接的框的样式 |
| pdf_set_border_color(int pdfdoc, float red, float green, float blue) | void | 设置围绕各种注释和链接的框的颜色 |
| pdf_set_border_dash(int pdfdoc, float black, float white) | void | 设置各种注释和链接的边框虚线样式 |
| pdf_new() | int | 创建新的 PDF 对象 |
| pdf_get_majorversion() | int | 返回 PDFlib 的主版本号 |
| pdf_get_minorversion() | int | 返回 PDFlib 的次版本号 |
| pdf_delete(int pdfdoc) | bool | 删除 PDF 对象 |
| pdf_open_file(int pdfdoc [, char filename]) | int | 打开新的 PDF 文档；如果文件名为 NULL，则文档在内存中创建 |
| pdf_get_buffer(int pdfdoc) | int | 获取包含生成的 PDF 数据的完整缓冲区 |
| pdf_findfont(int pdfdoc, string fontname, string encoding [, int embed]) | int | 为以后与 pdf_setfont() 一起使用准备字体 fontname |
| pdf_setfont(int pdfdoc, int font, float fontsize) | void | 在给定的字体大小下设置当前字体 |
| pdf_setpolydash(int pdfdoc, float darray) | void | 设置复杂的虚线模式 |
| pdf_concat(int pdf, float a, float b, float c, float d, float e, float f) | void | 将矩阵连接到文本和图形的当前变换矩阵 |
| pdf_open_ccitt(int pdf, string filename, int width, int height, int bitreverse, int k, int blackls1) | int | 打开带有原始 CCITT G3 或 G4 压缩位图数据的图像文件 |
| pdf_open_image(int pdf, string type, string source, string data, long length, int width, int height, int components, int bpc, string params) | int | 打开指定类型的图像并返回用于放置在 PDF 文档中的图像 |
| pdf_attach_file(int pdf, float llx, float lly, float urx, float ury, string filename, string description, string author, string mimetype, string icon) | void | 在由给定左下角和右上角指定的矩形处添加文件附件注释 |
| pdf_add_note(int pdfdoc, float llx, float lly, float urx, float ury, string contents, string title, string icon, int open) | void | 设置注释 |
| pdf_add_locallink(int pdfdoc, float llx, float lly, float urx, float ury, int page, string dest) | void | 向当前 PDF 文件中的目标添加链接注释 |
| pdf_add_launchlink(int pdfdoc, float llx, float lly, float urx, float ury, string filename) | void | 向任意文件类型的目标添加启动注释 |
| pdf_place_pdi_page(int pdf, int page, float x, float y, float sx, float sy) | void | 放置左下角在 (x, y) 处的 PDF 页面并对其进行缩放 |
| pdf_setmatrix(int pdf, float a, float b, float c, float d, float e, float f) | void | 显式设置当前变换矩阵 |

