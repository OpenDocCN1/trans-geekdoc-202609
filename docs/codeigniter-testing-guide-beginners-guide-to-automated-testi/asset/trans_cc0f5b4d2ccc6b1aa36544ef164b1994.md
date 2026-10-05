
# 测试一个简单的 MVC 应用

```diff
--- a/CodeIgniter/application/config/database.php
+++ b/CodeIgniter/application/config/database.php
@@ -76,9 +76,9 @@ $query_builder = TRUE;
$db['default'] = array(
  'dsn' => 'localhost',
  'username' => '',
  'password' => '',
  'database' => '',
+ 'username' => 'dbuser',
+ 'password' => 'dbpass',
+ 'database' => 'testing',
  'dbdriver' => 'mysqli',
  'dbprefix' => '',
  'pconnect' => FALSE,
```

# 专用测试数据库

测试时使用专用数据库是一个良好的习惯。CodeIgniter 包含了处理多个环境的功能。它会读取 `application/config/[environment]` 目录下的配置文件（如果存在）。ci-phpunit-test-always 始终在测试环境中运行测试。因此，如果你将数据库配置放在 `application/config/testing/database.php`，该配置将将用于你的测试。

# 数据库迁移 (Migration)

我们将使用 CodeIgniter 的迁移库创建一个数据库表。

创建 `application/database/migrations` 目录用于存放迁移文件，然后创建一个迁移文件来创建 `news` 表。

> CodeIgniter 中迁移文件的默认位置是 `application/migrations`，但我们更改了它。稍后我们将会有数据填充文件（seeding files），我们不希望它们与迁移文件混淆。

^7http://www.codeigniter.com/user_guide/libraries/config.html#environments

# 测试一个简单的 MVC 应用

application/database/migrations/20150907090030_Create_news.php

```php
<?php
class Migration_Create_news extends CI_Migration
{
    public function up() {
        $this->dbforge->add_field([
            'id' => [
                'type' => 'INT',
                'constraint' => 11,
                'auto_increment' => true
            ],
            'title' => [
                'type' => 'VARCHAR',
                'constraint' => 128
            ],
            'slug' => [
                'type' => 'VARCHAR',
                'constraint' => 128
            ],
            'text' => [
                'type' => 'TEXT',
            ]
        ]);
        $this->dbforge->add_key('id', true);
        $this->dbforge->add_key('slug');
        $this->dbforge->create_table('news');
    }

    public function down() {
        $this->dbforge->drop_table('news');
    }
}
```

编辑迁移配置文件，将 `migration_enabled` 设置为 `true`，并将 `migration_version` 设置为 `create_news` 迁移的时间戳。我们还需要将 `migration_path` 更新为 `APPPATH.'database/migrations/`。

# 测试一个简单的 MVC 应用

```diff
--- a/CodeIgniter/application/config/migration.php
+++ b/CodeIgniter/application/config/migration.php
@@ -11,7 +11,7 @@ defined('BASEPATH') OR exit('No direct script access allowed');
 | and disable back when you're done.
 |
 */ */-$config['migration_enabled'] = FALSE;
+$config['migration_enabled'] = TRUE;
```

```diff
/*
 |-
@@ -69,7 +69,7 @@ $config['migration_auto_latest'] = FALSE;
 | be upgraded to downgraded.
 |
 */
-$config['migration_version'] = 0;
+$config['migration_version'] = 201509070900030;
```

```diff
/*
 |-
@@ -81,4 +81,4 @@ $config['migration_version'] = 0;
 | Also, writing permission is required within the migrations folder.
 |/
```

```diff
-$config['migration_path'] = APPATH.'migrations/';
+$config['migration_path'] = APPATH.'database/migrations/';
```

# Dbfixture 控制器

创建一个 Dbfixture 控制来运行迁移。我们可以参考 CodeIgniter 指南中的 `Migrate` 类。

application/controllers/Dbfixture.php

```php
<?php

class Dbfixture extends CI_Controller
{
    public function __construct()
    {
        parent::__construct();
    }
}
```

> *http://www.codeigniter.com/user_guide/libraries/migration.html#usage-example

# 测试一个简单的 MVC 应用

```php
9 // 仅通过 CLI 访问
10 if (is_cli() === false) {
11 exit();
12 }
13 }
14 
15 public function migrate()
16 {
17 $this->load->library('migration');
18 if ($this->migration->current() === false) {
19 echo $this->migration->error_string() . PHP_EOL;
20 }
21 }
22 }
```

该控制器可以通过浏览器访问，任何可以访问你网站的人都可以运行迁移。这不好，因此我们添加了一些逻辑来检查它是否通过 CLI 运行，如果不是则退出。

通过 CLI 运行 Dbfixture 控制器来执行你的迁移。

```bash
$ php index.php dbfixture migrate
```

如果没有输出，说明迁移已运行且 `news` 表已成功创建。你可以使用 `sqlite3` 命令确认。

```bash
$ sqlite3 application/data/sqlite-database.db
SQLite version 3.8.5 2014-08-15 22:37:57
Enter ".help" for usage hints.
sqlite> .schema
CREATE TABLE "migrations" (
  "version" BIGINT NOT NULL
);
CREATE TABLE "news" (
  "id" INTEGER PRIMARY KEY AUTOINCREMENT,
  "title" VARCHAR NOT NULL,
  "slug" VARCHAR NOT NULL,
  "text" TEXT NOT NULL
);
CREATE INDEX "news_slug" ON "news" ("slug")
sqlite> .exit
```

你可以在数据库中看到 `news` 表。

# News 部分

让我们看看 News 部分的代码。

# News_model 模型

News_model 类有两个方法。一个是从数据库中获取新闻项，另一个是将新闻项插入数据库。

application/models/News_model.php

```php
<?php
class News_model extends CI_Model
{
    public function __construct()
    {
        // $this->load->database() 方法加载数据库类。加载后，你可以
        // 将其作为 "$this->db"
        $this->load->database();
    }

    public function get_news($slug = false)
    {
        if ($slug === false) {
            // $this->db->get() 方法运行查询并返回结果。
            $query = $this->db->get('news');
            // $result_array() 方法返回数组格式的查询。
            return $query->result_array();
        }

        // $this->db->get_where() 方法带有 "where" 子句运行查询，
        // 位于第二个参数。
        $query = $this->db->get_where('news', ['slug' => $slug]);
        // $row_array() 方法返回行数组。
        return $query->row_array();
    }

    public function set_news()
    {
        // 插入新闻的实现
    }
}
```

# News 控制器

News 控制器有三个方法。index() 显示存档。view() 显示一个新闻项。create() 显示创建一个新闻项的表单。
