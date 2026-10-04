

# 附录 E：PHP 函数引用 483

| 函数 | 返回 | 作用 |
| :--- | :--- | :--- |
| imagepsfreefont (int font_index) | bool | 释放字体使用的内存 |
| imagepsextendfont (int font_index, double extend) | bool | 扩展或压缩（如果 extend < 1）一个字体 |
| imagepstext(int image, string text, int font, int size, int xcoord, int ycoord [, int space, int tightness, double angle, int antialias]) | array | 在图像上绘制文本字符串 |
| imagepsencodefont(int font_index, filename) | bool | 从指定文件加载新字体 |
| (unknown) | bool | 更改字体的字符编码向量 |
| imagepsextendfont(int font_index, double extend) | bool | 扩展或压缩（如果 extend < 1）一个字体 |
| imagepsslantfont(int font_index, double slant) | bool | 使字体倾斜 |
| imagepstext(int image, string text, int font, int size, int xcoord, int ycoord [, int space, int tightness, double angle, int antialias]) | array | 在图像上栅格化字符串 |
| imagepsbbox(string text, int font, int size [, int space, int tightness, int angle]) | array | 返回字符串栅格化所需的边界框 |
| imagepsbbox(string text, int font, int size [, int space, int angle]) | array | 返回字符串栅格化所需的边界框 |

# 484 第五部分：附录

使用这些函数需要来自 http://www.boutell.com/gd/ 的 GD 库，并且在编译 PHP 时需要使用 `--with-gd` 参数。

![](img/245156cc770929860a3ede93c01f9981_510_0.png)

# 表 E-30 IMAP 函数

| 函数 | 返回 | 作用 |
| :--- | --- | --- |
| imap_open(string mailbox, string user, string password [, int options]) | int | 打开信邮箱箱的 IMAP 流 |
| imap_popen(string mailbox, string user, string password [, int options]) | int | 打开到邮箱箱的持久化 IMAP 流 |
| imap_reopen(int stream_id, string mailbox [, int options]) | int | 重新打开新邮箱箱的 IMAP 流 |
| imap_close(int stream_id [, int options]) | int | 关闭 IMAP 流 |
| imap_append(int stream_id, string folder, string message [, num_msg, int flags]) | int | 向指定的邮箱箱添加新消息 |
| imap_num_msg(int stream_id) | int | 获取当前邮箱箱中的消息数量 |
| imap_ping(int stream_id) | int | 检查 IMAP 流是否仍然活动 |
| imap_num_recent(int stream_id) | int | 获取当前邮箱箱中最近的消息数量 |
| imap_expunge(int stream_id) | int | 永久删除所有标记为删除的消息 |
| imap_headers(int stream_id) | array | 返回邮箱箱中所有消息的头信息 |
| imap_body(int stream_id, int msg_no [, int options]) | string | 读取消息体 |

# 附录 E：PHP 函数引用

| 函数 | 返回 | 作用 |
| :--- | --- | --- |
| imap_fetchtext_full(int stream_id, int msg_no, [ int options]) | string | 读取消息的完整文本 |
| imap_mail_copy(int stream_id, int msg_no, string mailbox) [, int options]) | int | 将指定的消息复制到邮箱箱 |
| imap_mail_move(int stream_id, int msg_no, string mailbox) [, int options]) | int | 将指定的消息移动到邮箱箱 |
| imap_creatmailbox(int stream_id, string mailbox) | int | 创建新邮箱箱 |
| imap_renamemailbox(int stream_id, string old_name, string new_name) | int | 重命名邮箱箱 |
| imap_deletemailbox(int stream_id, string mailbox) | int | 删除邮箱箱 |
| imap_list(int stream_id, string ref, string pattern) | array | 读取邮箱箱列表 |
| imap_getmailboxes(int stream_id, string ref, pattern) | array | 读取邮箱箱列表并返回一个包含名称、属性和分隔符的对象完整数组 |
| imap_check(int stream_id) | object | 获取邮箱箱属性 |
| imap_delete(int stream_id, int msg_no, [. int flags]) | int | 将消息标记为删除 |
| imap_undelete(int stream_id, int msg_no) | int | 移除消息的删除标记 |

继续

# 第五部分：附录

# 表 E-30 IMAP 函数（继续）

| 函数 | 返回 | 作用 |
| :--- | --- | --- |
| imap_headerinfo(int stream_id, int msg_no [, int from_length [, int subject_length [, string default_length]]]) | object | 读取消息的头信息 |
| imap_822_parse(string headers, string default_host]) | array | 解析头信息，类似于 imap_headerinfo() |
-_ imap_sub(int stream_id, string pattern) | array | 返回已订阅的消息列表 |
- imap_getsubscribed(int stream_id, string ref, pattern) | array | 返回邮箱箱列表，类似于 imap_list() |
- imap_subscribe(int stream_id, string mailbox) | int | 订阅邮箱箱 |
- imap_unsubscribe(int stream_id, string mailbox) | int | 取消邮箱箱订阅 |
- imap_fetchstructure(int stream_id, int msg_no [, int options]) | object | 获取消息的结构 |
- imap_fetchbody(int stream_id, int msg_no [, int options]) | string | 获取消息文 |
- imap_base64(string text) | string | 解码 base64 字符串 |
- imap_print(string text) | string | 打印字符串 |
- imap_8bit(string text) | string | 将字符串转换为8位 |
- imap_binary(string text) | string | 将字符串转换为二进制 |

# 附录 E：PHP 函数引用 483

| 函数 | 返回 | 作用 |
| :--- | --- | --- |
| imap_msginfo(int stream_id) | object | 获取邮箱箱信息 |
| imap_822_write(string mailbox, string host, string personal) | string | 返回格式化后的电子邮件 |
| imap_822_parselist(string address_string, string default_host) | array | 解析地址 |
| imap_utf8(string text) | string | 将字符串转换为 UTF8 |
| imap_utf7_decode(string buf) | string | 解码修改后的 UTF7 |
| imap_utf7_encode(string buf) | string | 编码修改后的 UTF7 |
| imap_setflag_full(int stream_id, string sequence [, int options]) | int | 设置消息标记 |
| imap_clearflag_full(int stream_id, string sequence [, int options]) | int | 清除消息标记 |
- imap_fetchheader(int stream_id, int msg_no [, int options]) | string | 获取消息的完整头信息 |
- imap_uid(int stream_id, int msg_no) | int | 获取序列消息对应的唯一 ID |
- imap_msgno(int stream_id, int unique_id) | int | 获取唯一 ID 对应的序列号 |

