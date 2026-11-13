
看看你的挑战、预算和性格是否使得某个现成系统很合适。如果不合适，你可以查看本章介绍的框架和代码，并根据需要对其进行调整，或者干脆从头重写。

## 确定应用程序的范围和目标

为便于展示这个内容管理应用程序，我们创建了一个相当基础的站点（它位于光盘上的 /book/netsloth 目录中）。但鉴于 Web 内容的性质，无论你创建什么样的站点，都将需要你能调集的所有设计和编辑资源，而且我们在这里不会太担心这方面。

我们的内容管理系统需要完成几件事。其最明显的目的是为作者、编辑和管理员提供一个可以创建新故事的环境。此外，它必须提供一系列灵活的阶段，故事会在这些阶段中流转。例如，如果最初是用单个编辑阶段实现的，那么在需要时，该应用程序必须足够灵活，能够容纳额外的编辑阶段（或多个阶段）。

此外，该应用程序必须满足员工的各种需求。将会有一系列作者，每篇故事都会附带一些署名信息。而且，工作人员将在编辑过程中被分配特定的职能。不同级别的权限将确保不是每个人都有权编辑或校对某篇特定故事，或者将该故事发布给全世界。

最后，必须存在一种超级用户权限。少数选定的人将有权向编辑团队添加用户和权限。

## 必要页面

首先，我们需要一个站点，一个用于显示文章的地方。由于站点并非本应用程序的真正重点，我们对此只做简要处理。你显然需要编写一个符合你需求的站点。图 11-1 和 11-2 展示了 Netsloth 站点的全貌。

该应用程序管理内容及其创建者。我们需要一系列编辑阶段和一系列用户。用户只能访问涉及他们的阶段。图 11-3 显示一个列出示例阶段和用户的页面。图 11-4 和 11-5 分别显示管理这些权限和阶段的页面。

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_396_0.png)

图 11-1: Netsloth 索引页面

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_396_1.png)

图 11-2: 故事页面

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_397_0.png)

图 11-3: 权限和阶段页面

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_397_1.png)

图 11-4: 权限管理页面

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_398_0.png)

图 11-5: 阶段管理页面

该应用程序还需要一个工作区，一个作者和编辑可以在此创建故事，并且故事可以在此完成编辑流程的页面。工作区将包含一些用于标识作者、日期、正文以及其他必要信息的字段。此外，还会指示故事所处的编辑流程阶段。该页面在图 11-6 中显示。

编辑环境的另一个重要方面是版本控制。能够跟踪稿件在流程中的流转非常重要。我们需要知道是谁在做更改。图 11-7 显示跟踪版本的页面，即故事历史记录页面。

该应用程序还执行其他一些任务，但这里可以忽略不计。在此，我们已概述了应用程序的主要功能。

## 我们需要防止什么？

该应用程序的主要问题是确保用户只能做他们被允许做的事情，绝不能越俎代庖。为此，该应用程序使用了 MySQL 管理权限。

之前的所有应用程序都有一个简单的头文件，用于调用登录数据库的函数。每个文件最终都使用相同的 my_connect() 调用，以及相同的用户名和密码。但这里行不通，因为不同的用户需要不同级别的访问权限。

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_399_0.png)

图 11-6: 编辑工作区

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_399_1.png)

图 11-7: 故事历史记录页面

此外，在这个应用程序中，一些用户将需要授予其他用户访问权限的能力。员工会来也会走，他们的职责也会发生变化。管理员需要能够更改这些权限。既然我们不希望每个登录数据库的人都拥有相同的权限，那么这个应用程序就需要提供不同的人使用不同的用户名和密码登录的功能。

在 MySQL 中，通过命名恰当的 GRANT 和 REVOKE 语句来授予和撤销权限。这些过程相当简单，并在附录 E 中有所描述。因此，在继续使用本应用程序之前，快速查看该附录可能很有价值。

> 在内容管理应用程序中，你会遇到 MySQL 的一些古怪方面。如果这个应用程序的某些设计看起来有点奇怪，那就是因为它确实奇怪。但我们会在开发应用程序时迎难而上。

## 设计数据库

图 11-8 所示的架构展示了本应用程序如何划分其数据，清单 11-1 揭示了用于设置数据库的 MySQL 命令序列。在查看时请记住，在数据库开发领域，通常不止一种不错的方法。你可能会发现一种同样有效的安排这些数据类型的方法。事实上，你可能更喜欢另一种方法。这对我们来说没问题。我们鼓励独立思考和创造力，只要它不会导致不道德或违背神意的行为。所以请按你认为合适的方式规范化你的数据，但在此过程中请不要违反任何自然法则。另一方面，数据规范化使得扩展数据库和将其适应新用途变得更加容易。这一点也请牢记。

**清单 11-1:** 内容管理系统的 create 语句

```
drop database if exists netsloth;
create database netsloth;
use netsloth;

drop table if exists admin;
create table admin
(
   username   varchar(50) not null
   , password  varchar(255) not null
   , primary key (username)
)
type=InnoDB
```

### 清单 11-1（续）

```
;
drop table if exists author_seq;
create table author_seq
(
    id int not null auto_increment
    , primary key (id)
)
type=InnoDB
;
drop table if exists authors;
create table authors
(
    author_id    integer not null auto_increment
    , author     varchar(50) null
    , email      varchar(255) null
    , bio        text null
    , user_id    int null
    , primary key (author_id)
    , key (user_id)
    , foreign key (user_id) references users (user_id) on delete cascade
)
type=InnoDB
;
-- read-write tables
grant select,update,insert,delete on stories to fake@localhost;
grant select,update,insert,delete on story_seq to fake@localhost;
grant select,update,insert,delete on story_versions to fake@localhost;
grant select,update,insert,delete on authors to fake@localhost;
grant select,update,insert,delete on author_seq to fake@localhost;
grant select,update,insert,delete on story_author_map to fake@localhost;
-- read-only tables
grant select on admin to fake@localhost;
grant select on users to fake@localhost;
grant select on stages to fake@localhost;
grant select on user_stage_map to fake@localhost;
-- build local copy
drop table if exists content_tables;
create table content_tables as
    select Table_name, Table_priv
    from mysql.tables_priv
    where Host = 'localhost' and Db = 'netsloth' and User = 'fake'
;
```

```
alter table content_tables add unique (Table_name);
-- delete the slug
delete from mysql.user
where Host = 'localhost' and User = 'fake'
;
delete from mysql.tables_priv
where Host = 'localhost' and Db = 'netsloth' and User = 'fake'
;
```

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_402_0.png)

注意：这些表中的每一个都对应 content_stages 表中的一个条目。随着阶段的添加和删除，表会发生变化。

| editing_stories | killed_stories | proofreading_stories |
|---|---|---|
| story_id | story_id | story_id |

| live_stories | writing_stories |
|---|---|
| story_id | story_id |

图 11-8: 内容管理架构
