Recent messages should appear at the top of the list. Reverse the order when sorting by SORTDATE:

```
if ($this->sort == 'SORTDATE') $this->reverse = (integer) !
$this->reverse;
```

The cast might seem superfluous in the above if statement, but it's necessary to prevent the $reverse global variable from having a null value.

With IMAP, we can manipulate messages in bulk:

```
if ($this->protocol =='imap') {
$ret_str = "<form method=\"POST\" action=\"$PHP_SELF\>\n";
$ret_str .= "<input type=\"HIDDEN\" name=\"mailbox\"
value=\"$this->mailbox\>\n";
}
else $ret_str = '';
```

Draw the table header cells. Clicking on a header cell title will sort the list in the selected sorting order:

```
$ret_str .= $this->msgTableHeader();
$t_str = $this->msgTableRow(10,'NO',1,"#CECECE");
$t_str .= $this->msgTableRow(50,$this->buildUrl("action=
listMsg&mailbox=$this->mailbox&sort=SORTSUBJECT&reverse=$order",
"SUBJECT"),1,"#CECECE");
$t_str .= $this->msgTableRow(20,$this->buildUrl("action=
listMsg&mailbox=$this->mailbox&sort=SORTFROM&reverse=$order",
"FROM"),1,"#CECECE");
$t_str .= $this->msgTableRow(20,$this->buildUrl("action=
listMsg&mailbox=$this->mailbox&sort=SORTDATE&reverse=
$this->reverse", "DATE"),1,"#CECECE");
$ret_str .= "<tr>\n$t_str</tr>\n";
```

Get the message list calling the getMsgList() method:

```
$msgs = $this->getMsgList('action=readMsg', 'action=
mailForm&mode=reply');
if (!$msgs) return 0;
$num_msg = count($msgs);
```

A series of navigation links are provided so that the user can jump to any page he wants to view:

```
if (!$cur_page) $cur_page = 1;
if (!$num_msg) $num_page =1;
else $num_page = ceil($num_msg/$this->msg_per_page);
if ($cur_page >= $num_page) $cur_page = $num_page;
```