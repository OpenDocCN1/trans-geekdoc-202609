

- “Amazon grants you a limited license to access and make personal use of this site ... This license does not include ... any use of data mining, robots, or similar data gathering and extraction tools.” – Amazon Conditions of Use, LICENSE AND SITE ACCESS section as of 2/14/10

  亚马逊授予您访问和使用本网站的有限个人使用权……此许可不包括……使用数据挖掘、机器人或类似的数据采集和提取工具。——《亚马逊使用条款》，许可证和网站访问章节，截至2010年2月14日

- “You agree that you will not use any robot, spider, scraper or other automated means to access the Sites for any purpose without our express written permission.” – eBay User Agreement, Access and Interference section as of 2/14/10

  您同意，未经我们明确的书面许可，不得使用任何机器人、爬虫、抓取器或其他自动化手段出于任何目的访问本网站。——《eBay 用户协议》，访问与干扰章节，截至2010年2月14日

- “... you agree not to: ... access, monitor or copy any content or information of this Website using any robot, spider, scraper or other automated means or any manual process for any purpose without our express written permission; ...” – Expedia, Inc. Web Site Terms, Conditions, and Notices, PROHIBITED ACTIVITIES section as of 2/14/10

  ……您同意不进行以下行为：……未经我们明确的书面许可，使用任何机器人、爬虫、抓取器或其他自动化手段或任何手动流程出于任何目的访问、监控或复制本网站的任何内容或信息；……——Expedia, Inc. 网站条款、条件和声明，禁止活动章节，截至2010年2月14日

- “The foregoing licenses do not include any rights to: ... use any robot, spider, data miner, scraper or other automated means to access the Barnes & Noble.com Site or its systems, the Content or any portion or derivative thereof for any purpose; ...” – Barnes & Noble Terms of Use, Section I LICENSES AND RESTRICTIONS as of 2/14/10

  上述许可不包括以下权利：……使用任何机器人、爬虫、数据挖掘器、抓取器或其他自动化手段出于任何目的访问巴诺网站或其系统、内容或其任何部分或衍生作品；……——《巴诺使用条款》，第一章节 许可与限制，截至2010年2月14日

确定目标网站是否有 TOS 文档将是第一步。如果您找到文档，请查找使用与上述示例类似语言的条款。同时，也要查找任何广泛的“全面禁止”条款，网络抓取可能会归属于此类被禁止的活动之下。

如果您找到了一份 TOS 文档，且其中未明确禁止网络抓取，下一步是联系有权代表拥有该网站的组织发言的代表。某些组织可能允许网络抓取，前提是您事先已获得适当权限的许可。在获得此许可时，最好获取一份书面文件，并使用官方信头，以明确表明该文件来源于相关组织。这能最大程度地降低可能出现的任何法律问题。

如果因使用自动代理或由代理获取的信息而对个人提起与知识产权相关的指控，假设该个人未违反其所有者施加的任何 TOS 协议或相关计算机使用法律，法院判决最终可能归结于该信息的使用是否被解释为在指控发生地的地理区域内符合版权法中的“合理使用”。

请注意，这些陈述非常通用，并非旨在替代律师咨询。如果 TOS 协议或缺乏协议以及与网站所有者的沟通未能得出明确结论，强烈建议在尝试在网站上启动自动代理之前寻求法律建议。这也是网络抓取是解决数据获取问题的不理想方案的原因，只有在没有其他替代方案时才应考虑使用它。

一些网站实际上使用许可协议来授予其内容开放或轻度限制的使用权。用于此目的的常见许可包括 GNU 自由文档许可和 Creative Commons 许可。在特定的数据源用于获取数据不相关的情况下，应优先选择使用此类许可的来源，而不是没有使用许可的来源，因为法律问题的发生几率显著降低。

第二个检查点是作为待采集数据原始来源的网站合法性。即使是拥有大量法律资源的大型公司，如 Google，也曾因自动代理从非法联合分发其他网站内容的站点获取内容而遇到问题。在某些情况下，网站会注明其来源，但在许多情况下它们不会。

对于文本内容，将可能来自该站点的直接引语（具有唯一性的可能性较大）输入主要搜索引擎，是确定相关网站是否为数据原始来源的一种方法。这也可以提供一些指示，表明联合分发该数据是否合法。

对于非文本数据，请根据主题推测相应的关键词，并尝试使用特定于该数据格式的搜索引擎进行搜索。此类搜索的目的不是进行全面或决定性的指示，而仅仅是排除对原始数据源明显联合分发的一种快速方法。

## 附录 B

### 多进程

当使用 CLI SAPI（即从命令行）执行 PHP 脚本时，该执行实例作为本地操作系统中的一个进程存在。进程控制（pcntl）扩展使得 PHP 脚本能够执行所谓的进程 **fork**。这包括原始 PHP 进程（随后称为 **父进程**）创建自身的副本（恰当地称为 **子进程**），其中包含从与该进程关联的数据到 fork 指令后的当前执行点的所有内容。

一旦 fork 完成，两个进程都存在并独立执行。父进程可以连续多次 fork 自身，并对其子进程保持有限的感知。特别是，当任何给定的子进程终止时，它会收到通知。

由于每个子进程都是其父进程的副本，可以 fork 的子进程数量受本地系统硬件资源的限制。CPU 仅限制所有子进程完成的速度。然而，如果本地系统的 RAM 被超过并不得不使用交换空间进行存储，内存可能会成为瓶颈。

这种限制促使我们希望 fork 尽可能多的进程，以便并行完成一项工作而不触及任何资源限制。这通常通过使用对要 fork 的进程数量的预定上限来实现。然而，一旦任何给定的子进程完成，可能希望在其位置创建一个新的子进程以完成另一个工作单元。下面示例中展示了这种实现方式。

```php
<?php
// Maximum number of child processes to fork
$children_max = 10;

// Counter for current number of child processes
$children_count = 0;

// Temporary variable for the status of a terminated child process
$child_status = null;

// Process identifier, initialized so the parent branch executes
$pid = 1;

while (true) {
    if ($pid == -1) {
        trigger_error('Unable to fork process', E_USER_ERROR);
    } elseif ($pid) {
        // Parent process

        // Check for more work

        // Break out of the loop if the job is finished

        // Fork another child
        $children_count++;
        $pid = pcntl_fork();

        // Wait to fork more children if the max is reached
        if ($children_count == $children_max) {
            pcntl_wait($child_status);
            $children_count--;
        }
    } else {
        // Child process

        // Perform a unit of work

        exit;
    }
}
?>
```

### 进程控制资源

有关进程控制扩展的更多信息，请参阅 http://php.net/manual/en/book.pcntl.php。

