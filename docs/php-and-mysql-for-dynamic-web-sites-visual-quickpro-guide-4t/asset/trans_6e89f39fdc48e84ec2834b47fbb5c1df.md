

```php
61     $d = (!empty($_POST['description'])) ? trim($_POST['description']) : NULL;

63     // 验证艺术家...

64     if (isset($_POST['artist']) && filter_var($_POST['artist'], FILTER_VALIDATE_INT, array('min_range' => 1))) {
65         $a = $_POST['artist'];
66     } else { // 未选择艺术家。
67         $errors[] = '请选择该版画的艺术家！';
68     }

70     if (empty($errors)) { // 如果一切正常。

72         // 将版画添加到数据库：
73         $q = 'INSERT INTO prints (artist_id, print_name, price, size, description, image_name)
74             VALUES (?, ?, ?, ?, ?, ?)';
75         $stmt = mysqli_prepare($dbc, $q);
76         mysqli_stmt_bind_param($stmt, 'isdsss', $a, $pn, $p, $s, $d, $i);
77         mysqli_stmt_execute($stmt);

78         // 检查结果...
79         if (mysqli_stmt_affected_rows($stmt) == 1) {

81             // 打印一条消息：
82             echo '<p>该版画已添加。</p>';

84             // 重命名图像：
85             $id = mysqli_stmt_insert_id($stmt); // 获取版画 ID。
86             rename($temp, "../../uploads/$id");

88             // 清空 $_POST：
89             $_POST = array();

91         } else { // 出错！
92             echo '<p style="font-weight: bold; color: #C00">您的提交无法被处理
93                 由于系统错误。</p>';
94         }

95         mysqli_stmt_close($stmt);

97     } // $errors IF 结束。

99     // 如果上传的文件仍然存在则删除它：
100    if (isset($temp) && file_exists($temp) && is_file($temp)) {
101        unlink($temp);
102    }

104 } // 提交 IF 结束。

106 // 检查是否有任何错误并打印它们：
107 if (!empty($errors) && is_array($errors)) {
108     echo '<h1>错误！</h1>
109     <p style="font-weight: bold; color: #C00">发生了以下错误：<br />';
110     foreach ($errors as $msg) {
111         echo " - $msg<br />\n";
112     }
113     echo '请重新选择版画图像并再试一次。</p>';
114 }

116 // 显示表单...
117 ?>
118 <h1>添加版画</h1>
119 <form enctype="multipart/form-data" action="add_print.php" method="post">

121     <input type="hidden" name="MAX_FILE_SIZE" value="524288" />

123     <fieldset><legend>填写表单以向目录添加版画：</legend>

125     <p><b>版画名称：</b> <input type="text" name="print_name" size="30" maxlength="60"
126         value="<?php if (isset($_POST['print_name'])) echo htmlspecialchars($_POST['print_name']); ?>"
127         /></p>

129     <p><b>艺术家：</b>
130     <select name="artist"><option>请选择一个</option>
131     <?php // 检索所有艺术家并添加到下拉菜单中。
132     $q = "SELECT artist_id, CONCAT_WS(' ', first_name, middle_name, last_name) FROM artists ORDER
133         BY last_name, first_name ASC";
134     $r = mysqli_query($dbc, $q);
135     if (mysqli_num_rows($r) > 0) {
136         while ($row = mysqli_fetch_array($r, MYSQLI_NUM)) {
137             echo "<option value=\"$row[0]\"";
138             // 检查粘滞性：
139             if (isset($_POST['existing']) && ($_POST['existing'] == $row[0])) echo '
140                 selected="selected"';
141             echo ">$row[1]</option>\n";
142         }
143     } else {
144         echo '<option>请先添加新艺术家。</option>';
145     }
146     mysqli_close($dbc); // 关闭数据库连接。
147     ?>
148     </select></p>

150     <p><b>价格：</b> <input type="text" name="price" size="10" maxlength="10" value="<?php if
151         (isset($_POST['price'])) echo $_POST['price']; ?>" /> <small>请勿包含美元符号或
152         逗号。</small></p>

153     <p><b>尺寸：</b> <input type="text" name="size" size="30" maxlength="60" value="<?php if
154         (isset($_POST['size'])) echo htmlspecialchars($_POST['size']); ?>" /> (可选)</p>

155     <p><b>描述：</b> <textarea name="description" cols="40" rows="5"><?php if (isset($_
156         POST['description'])) echo $_POST['description']; ?></textarea> (可选)</p>

157     </fieldset>

159     <div align="center"><input type="submit" name="submit" value="提交" /></div>

161 </form>

162 </body>
163 </html>
```

---

### 2. 包含数据库连接脚本并检查表单是否已提交：

```php
require ('../../mysqli_connect.php');

if ($_SERVER['REQUEST_METHOD'] == 'POST') {
    $errors = array();
}
```

任何表单验证问题都将被添加到 `$errors` 数组中，该数组在此处初始化。（因为此脚本可能会有多个错误，所以使用了数组；而在 `add_artist.php` 中，一次只能发生单个错误。）

### 3. 验证版画的名称：

```php
if (!empty($_POST['print_name'])) {
    $pn = trim($_POST['print_name']);
} else {
    $errors[] = '请输入版画的名称！';
}
```

这是 *prints* 表中的必填字段之一，应检查其是否有值。同样，因为此脚本将使用预处理语句，用于查询的值不需要通过 `mysqli_real_escape_string()` 运行。

如果想要格外小心，可以在此处应用 `strip_tags()`（尽管如果恶意用户已进入管理区域，你将面临更大的问题）。

如果未输入值，则将错误消息添加到 `$errors` 数组中。

### 4. 如果选择了上传图像，则为其创建一个临时名称：

```php
if (is_uploaded_file($_FILES['image']['tmp_name'])) {
    $temp = '../../uploads/' . md5($_FILES['image']['name']);
```

当介绍使用 PHP 处理文件上传的技术时（见 [第 11 章](#ch11.html#ch11) “[Web 应用程序开发](#ch11.html#ch11)”），曾提到 `is_uploaded_file()` 函数。如果文件已上传，它返回 `TRUE`，否则返回 `FALSE`。如果文件已上传，脚本将尝试将文件移动到 `uploads` 目录（在第 5 步中）。

这里还发生了一件事：图像不会使用其原始名称存储在服务器上（这可能是一个安全隐患）。相反，图像将使用其关联的版画 ID 进行存储。然而，由于该值尚未知晓（因为版画记录尚未添加到数据库），必须为此文件生成一个临时名称。为此，将 `md5()` 函数（返回 32 字符的哈希值）应用于图像的原始名称。该临时名称连同图像最终目的地的相对路径（相对于此脚本）被赋值给 `$temp`。

您可以在此方面做一些改进。您还可以验证图像是否为正确的大小和类型。为了保持这个已经很繁忙的脚本更易于管理，我在此省略了该部分，但请参阅 [第 11 章](#ch11.html#ch11) 了解要应用的确切代码。

### 5. 将文件移动到其更永久的目标位置：

```php
if (move_uploaded_file($_FILES['image']['tmp_name'], $temp)) {
    echo '<p>文件已上传！</p>';
    $i = $_FILES['image']['name'];
```

此时，版画图像已被移动到其永久位置（`uploads` 目录），但被赋予了一个临时名称（稍后将重命名）。打印一条消息指示移动成功。最后，`$i` 变量将被赋值为文件的原始名称（供脚本后面使用）。

