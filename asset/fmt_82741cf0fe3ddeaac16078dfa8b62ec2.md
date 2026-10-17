
`table_cell`(`$r_description`, `array`(`"width"=>498`));

`print` `end_table`();

}

// 显示此子节点的任何子主题，在下次

`display_kids`(`$r_topic_id`, `$level+1`);

`if` (`$level` && `$child_count`)

{

```php
// 如果不是第一级，且找到了至少一个子节点
// 无序列表开始 - 关闭它。
print("</ul>\n");

// 递归是一个昂贵的过程；它会消耗大量的处理器时间。
// 为了防止系统被过载。
if ($level) {
    // 不是第一级 - 结束列表项
    print "</li>\n";
} else {
    // 第一级 - 关闭包含主题名称和作者
    // 的单元格和行，然后打印主题的
    // 内容并关闭表格
    print "<td>\n";
    print "<tr>\n";
    print table_row();
    table_cell("&nbsp;", array("width"=>2));
    table_cell($r_description,array("width"=>498));
    print end_table();
}
```

// 显示此子节点的任何子主题，在下次

`display_kids`(`$r_topic_id`, `$level+1`);

`if` (`$level` && `$child_count`)
{
