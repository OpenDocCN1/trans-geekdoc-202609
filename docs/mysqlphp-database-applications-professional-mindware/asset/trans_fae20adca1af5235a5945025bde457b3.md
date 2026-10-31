
使用的表。通过将用户限制为数据的视图，管理员可以限制用户被允许查看的内容。请注意，在大多数 SQL 服务器中，视图是只读的。

![](img/de0823012275cf4ceebdb822a56e6b71_322_0.png)

> 这个星球上没有一种开发工具没有它的怪癖。每种语言和每个数据库都有各自的挑战。在开始编写应用程序之前，你越了解这些，你的情况就会越好。

MySQL 中缺少的第二件事是更严格的授权语句（请参阅附录 D），在这里使用会很不错。目前，MySQL 可以在多个层面上授予权限：针对整个安装、特定数据库、数据库中的表或表中的列。虽然这听起来相当全面，但实际上并没有它本可以达到的完整程度。

考虑这个问题：在 MySQL 中，使用表级或列级授权，如何防止仅需要编辑权限的用户 john 更新已发布的故事？最好的做法是在 stories 表中设置非常具体的权限。如果 Live 的 stage_id 为 4，你希望授予 john 的权限是让他可以修改 stories 表中的任意行，除了那些 stage_id = 4 的行。其他数据库允许这样做，但 MySQL 不允许。

使用 MySQL 你能做的最好的事情就是为 content_users、content_stages 和 user_stage_map 表提供备份安全措施。此备份计划仅在访问数据库的 PHP 脚本内部有效。如果你授予用户权限，他们将能够通过除 Web 之外的途径登录数据库。而且，正如我们已经提到的，你可以授予的权限可能没有你希望的那样严格。请自行斟酌授予权限。

以下是二级安全机制在 PHP 脚本中的工作原理。当管理员创建一个阶段时，会在 content_stages 表中添加一行。此外，一个创建查询会创建一个只有一个列的表来存储 story_ids。对于校对阶段，有一个名为 proofreading_stories 的表。

当创建新用户时，会在适当的时候授予他们对这些表的权限。随着故事在编辑流程中推进，story_id 会写入相应的阶段表，例如 proofreading_stories。如果用户没有该表的权限，更新将被拒绝。

下面是一个快速示例说明其工作原理。假设你，作为此内容管理系统的管理员，决定需要在编辑流程中添加另一个阶段，称为 format_review。如果你以 content_admin 表中列出的用户身份登录应用程序，你将拥有创建此阶段的权限。该阶段首先会添加到 content_stages 表中。当你创建阶段时，你会指定哪些用户应有权使用此阶段。这些用户将以每个 user_id/stage_id 组合对应一行的方式添加到 user_stage_map 表中。这是我们的主要安全措施，如果你将此应用程序改编用于你的系统，你可能就止步于此。

然而，使用 MySQL 授权我们又迈出了一步。MySQL 授权不允许我们说“授予用户对 stories 表中 stage_id=4 的所有权限”。相反，我们创建一个名为 format_review_stories 的额外表。对此表的权限只会授予需要格式审查功能的人。随着故事在编辑流程中推进，story_id 会被复制到适当的阶段表。当它到达 format_review 时，story_id 会被复制到 format_review_stories 表。由于我们可以在表级别强制执行授权，我们知道未经授权的用户将无法访问 format_review_stories 表。如果未经授权的用户尝试更新 format_review_stories 表，查询将被拒绝。

这远非理想。事实上，这相当粗糙。如果我们在现实世界中部署此应用程序，几乎可以肯定我们不会真的尝试用授权语句使其工作。我们可能会确保用户完全无法直接访问数据库，并让 user_stage_map 表确保用户得到适当的限制。然而，我们认为展示一个如何从 PHP 接口使用 MySQL 授权语句的示例会很有用。

列表 11-1 显示了内容管理应用程序中的表。

## 列表 11-1：内容管理系统的创建语句

```
# Table structure for table 'authors'
#
CREATE TABLE authors (
    author_id int(11) DEFAULT '0' NOT NULL auto_increment,
    author varchar(50),
    email varchar(255),
    bio text,
    PRIMARY KEY (author_id)
);

#
# Table structure for table 'content_admin'
#
CREATE TABLE content_admin (
    username varchar(50) DEFAULT '' NOT NULL,
    password varchar(255) DEFAULT '' NOT NULL
);

#
# Table structure for table 'content_stages'
#
CREATE TABLE content_stages (
    stage_id int(11) DEFAULT '0' NOT NULL auto_increment,
    stage varchar(20) DEFAULT '' NOT NULL,
    stage_desc text,
    PRIMARY KEY (stage_id)
);

# Table structure for table 'content_users'
#
CREATE TABLE content_users (
    user_id int(11) DEFAULT '0' NOT NULL auto_increment,
    username varchar(20) DEFAULT '' NOT NULL,
    name varchar(50),
    email varchar(255),
    PRIMARY KEY (user_id)
);

#
# Table structure for table 'editing_stories'
#
CREATE TABLE editing_stories (
    story_id int(11) DEFAULT '0' NOT NULL,
    UNIQUE story_id (story_id)
);

#
# Table structure for table 'killed_stories'
#
CREATE TABLE killed_stories (
    story_id int(11) DEFAULT '0' NOT NULL,
    UNIQUE story_id (story_id)
);

#
# Table structure for table 'live_stories'
#
CREATE TABLE live_stories (
    story_id int(11) DEFAULT '0' NOT NULL,
    UNIQUE story_id (story_id)
);

#
# Table structure for table 'proofreading_stories'
#
CREATE TABLE proofreading_stories (
    story_id int(11) DEFAULT '0' NOT NULL,
    UNIQUE story_id (story_id)
);

#
# Table structure for table 'stories'
#
CREATE TABLE stories (
  story_id int(11) DEFAULT '0' NOT NULL auto_increment,
  stage_id int(11) DEFAULT '0' NOT NULL,
  publish_dt date,
  headline varchar(255),
  subtitle varchar(255),
  byline_prefix varchar(20),
  summary text,
  body text,
  PRIMARY KEY (story_id),
  KEY story_stage_key (stage_id)
);
#
# Table structure for table 'story_author_map'
#
CREATE TABLE story_author_map (
  story_id int(11) DEFAULT '0' NOT NULL,
  author_id int(11) DEFAULT '0' NOT NULL,
  PRIMARY KEY (story_id),
  KEY author_story_map_key (author_id)
);
#
# Table structure for table 'story_versions'
#
CREATE TABLE story_versions (
  story_id int(11) DEFAULT '0' NOT NULL,
  modify_dt timestamp(14),
  modify_by varchar(20) DEFAULT '' NOT NULL,
  stage_id int(11) DEFAULT '0' NOT NULL,
  publish_dt date,
  headline varchar(255),
  subtitle varchar(255),
  byline_prefix varchar(20),
  summary text,
  body text,
  KEY story_version_key (story_id,modify_dt)
);

#
# Table structure for table 'user_stage_map'
#
CREATE TABLE user_stage_map (
  user_id int(11) DEFAULT '0' NOT NULL,
  stage_id int(11) DEFAULT '0' NOT NULL,
  PRIMARY KEY (user_id,stage_id),
  KEY stage_user_map_key (stage_id)
);

#
# Table structure for table 'writing_stories'
#
CREATE TABLE writing_stories (
  story_id int(11) DEFAULT '0' NOT NULL,
  UNIQUE story_id (story_id)
);
```

## 代码概述

此时，我们假设你已经对本书中应用程序的构建方式感到熟悉。你应该熟悉第 8 章中介绍的函数，以及 PHP 如何在脚本中嵌入 MySQL 命令的方式。

随着你逐步深入，越来越少的代码需要解释。因此，代码的描述只会涉及那些真正新颖或棘手的部分。

在这里，大多数看起来较新的代码将来自于分配上一节讨论的权限。应用程序会发送你以前未使用过的查询。

## 代码分解

再次，本应用程序中的代码将大量使用 /functions/ 文件夹中的函数。这里展示的大量代码将调用这些函数。

## 可复用函数

在本应用程序中，只有一个包含应用程序特定函数的文件：/content/functions.php。
