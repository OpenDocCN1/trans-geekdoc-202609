
{ return False; }
else
{
    $query = "describe $table $col";
    $result = mysql_query($query);
    list( , $col) = mysql_fetch_array($result);
    echo $col;
    if (substr($col, 0, 4) != "enum")
    {
        return FALSE;
    }
    $col = str_replace ("'", "", substr($col, 5, -1));
    $col = explode(",", $col);
}
return $col;
}

You can use the enum field type in MySQL to limit possible values in a column. This might be helpful for restricting column values to Y or N, for example. But to get at these values in PHP, you need to run one of the MySQL queries that retrieve column information. In the preceding example I use the describe query, and I assume that the column of interest will be included in the query.

The query returns 6 columns. In order, they are: Field, Type, Null, Key, Default, and Extra. The second, Type, contains the column type—something like enum('yes','no'). In the preceding function, this value is assigned to $col. That string can then be stripped of the extraneous parentheses and the letters enum. The remainder is exploded into an array.

You can then use the array however you wish, perhaps in a drop-down box.

## Session handling with MySQL

If you wish to use these, set your session.save_handler to user in your php.ini. This set of functions is intended to work with a table that looks something like this:

```
create table sessions(
    session_id char(32) not null primary key,
    sess_data text,
    last_update timestamp
)
```
function mysql_session_open()
{
    mysql_pconnect("localhost", "root", "")
        or die (mysql_error());
    $db_sess = mysql_select_db("test")
        or die (mysql_error());
}

//this function receives the session_id as the only argument
function mysql_session_read($id)
{
    $data = "";
    $query = "select sess_data from sessions
            where session_id = '$id'";
    $result= mysql_query($query) or die (mysql_error());
    if ($row = mysql_fetch_row($result) )
    {
        $data=session_decode($row[0]);
    }
    return $data;
}

//this takes the sessionid and the session data
//as arguments
function mysql_session_write($id, $data)
{
    $data = session_encode($data);
    $query = "replace into sessions (session_id, sess_data)
            values ('$id', '$data')";
    mysql_query($query) or
        die(mysql_error());
    return true;
}

function mysql_session_close()
{
    return true;
}

//takes only the session id for an argument
function mysql_session_destroy($id)
{
    $query = "delete from sessions where session_id = '$id'";
    mysql_query($query) or
        die (mysql_error());
    return true;
}

//this function receives the maximum lifetime setting
//from php.ini. It is by default set to 1440 seconds.
//the session.gc_probability setting in the php.ini determines
//what percentage of the time this function will run.
function mysql_session_gc($time)
{
    $query = "delete from sessions where
        last_update < ( subdate(now(),
        INTERVAL $time SECOND ))";
    mysql_query($query) or
        die (mysql_error() );
}
session_set_save_handler(
    "mysql_session_open",
    "mysql_session_close",
    "mysql_session_read",
    "mysql_session_write",
    "mysql_session_destroy",
    "mysql_session_gc"
);

## MySQL Backup

Dan Nedoborski wrote this script, which I planned on including. However, it is a bit lengthy for printed form. I recommend you go to his site and take a look for yourself.

http://www.ov-m.com/mysqlphpbak/

## Validation

Here are a couple of the trickier items to validate properties.

### E-mail validation

There are a lot of simple regular expressions to make sure a string more or less resembles the format of a proper e-mail address, but if you want something that is a bit more thorough, try this. It may not be entirely RFC-compliant, but it is pretty close. It is included in the /book/functions folder.

```
#CheckEmail
#
#mailbox    = addr-spec                ; simple address
#           / phrase route-addr        ; name & addr-spec
#
#route-addr  = "<" [route] addr-spec ">"
#
#route       = 1#("@" domain) ":"                ; path-relative
#
#addr-spec   = local-part "@" domain             ; global address
#
#local-part  = word *("." word)                  ; uninterpreted
#                                             ; case-preserved
#
#domain      = sub-domain *("." sub-domain)
#
#sub-domain  = domain-ref / domain-literal
#
#domain-ref  = atom                              ; symbolic reference
#
#atom        = 1*<any CHAR except specials, SPACE and CTLs>
#
#specials    = "(" / ")" / "<" / ">" / "@"       ; Must be in quoted-
#             / "," / ";" / ":" / "\" / "<>"     ; string, to use
#             / "." / "[" / "]"                  ; within a word.
#
#
#                                             ; ( Octal, Decimal.)
#CHAR        = <any ASCII character>             ; ( 0-177,  0.-127.)
#ALPHA       = <any ASCII alphabetic character>
#                                             ; (101-132, 65.- 90.)
#                                             ; (141-172, 97.-122.)
#DIGIT       = <any ASCII decimal digit>         ; ( 60- 71, 48.- 57.)
#CTL         = <any ASCII control                ; ( 0- 37,  0.- 31.)
#             character and DEL>                 ; ( 177,    127.)
#CR          = <ASCII CR, carriage return>       ; (   15,    13.)
#LF          = <ASCII LF, linefeed>              ; (   12,    10.)
#SPACE       = <ASCII SP, space>                 ; (   40,    32.)
#HTAB       = <ASCII HT, horizontal-tab>         ; (   11,     9.)
#"<>"        = <ASCII quote mark>                ; (   42,    34.)
#CRLF       = CR LF
#
#LWSP-char  = SPACE / HTAB                      ; semantics = SPACE
#
#linear-white-space = 1*([CRLF] LWSP-char)       ; semantics = SPACE
#                                             ; CRLF => folding
#
#delimiters  = specials / linear-white-space / comment
#
#text        = <any CHAR, including bare        ; => atoms, specials,
#               CR & bare LF, but NOT           ; comments and
#               including CRLF>                 ; quoted-strings are
#                                               ; NOT recognized.
#
#quoted-string = "<>" *(qtext/quoted-pair) "<>"; Regular qtext or
#                                               ;  quoted chars.
#
#qtext          = <any CHAR excepting "<>",     ; => may be folded
#                 "\" & CR, and including
#
#                 linear-white-space>
#
#domain-literal = "[" *(dtext / quoted-pair) "]"
#
#
#
#
#
#dtext          = <any CHAR excluding "[",      ; => may be folded
#                 "]", "\" & CR, & including
#
#                 linear-white-space>
#
#comment        = "(" *(ctext / quoted-pair / comment) ")"
#
#ctext          = <any CHAR excluding "(",      ; => may be folded
#                 ")", "\" & CR, & including
#
#                 linear-white-space>
#
#quoted-pair    = "\" CHAR                       ; may quote any char
#
#phrase         = 1*word                          ; Sequence of words
#
#word           = atom / quoted-string
#
#
#mailbox        = addr-spec                       ; simple address
#                / phrase route-addr              ; name & addr-spec
#route-addr     = "<" [route] addr-spec ">"
#route          = 1#("@" domain) ":"            ; path-relative
#addr-spec      = local-part "@" domain          ; global address
#
#validate_email("insight\@bedrijfsnet.nl");
#
function print_validate_email ($eaddr="")
{
    $result = validate_email($eaddr) ? "is valid" : "is not valid";
    print "<h4>email address (".htmlspecialchars($eaddr).") $result</h4>\n";
}

function validate_email ($eaddr="")
{
    if (empty($eaddr))
    {
#print "[$eaddr] is not valid\n";
        return false;
    }
    $laddr = "";
    $laddr = $eaddr;

# if the addr-spec is in a route-addr, strip away the phrase and <>s

    $laddr = preg_replace('/^.*</','',$laddr);
    $laddr = preg_replace('/>.*$/','',$laddr);
    if (preg_match('/^@.*:/',$laddr))    #path-relative domain
    {
        list($domain,$addr_spec) = preg_split('/:/',$laddr);
        $domain = preg_replace('/^@/','',$domain);
        if (!is_domain($domain)) { return false; }
        $laddr = $addr_spec;
    }
    return(is_addr_spec($laddr));
}

function is_addr_spec ( $eaddr = "" )
{
    list($local_part,$domain) = preg_split('/@/', $eaddr);
    if (!is_local_part($local_part) || !is_domain($domain))
    {
#print "[$eaddr] is not valid\n";
        return false;
    }
    else
    {
#print "[$eaddr] is valid\n";
        return true;
    }
}

#local-part = word *("." word)          ; uninterpreted
function is_local_part ( $local_part = "" )
