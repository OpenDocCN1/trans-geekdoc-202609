```
{
if (empty($eaddr))
{
#print "[$eaddr] is not_valid\n";
return false;
}
$laddr = "";
$laddr = $eaddr;

# if the addr-spec is in a route-addr, strip away the phrase and <>s

$laddr = preg_replace('/^.*</','', $laddr);
$laddr = preg_replace('/>.*$/','',$laddr);
if (preg_match('/^@.*:/',$laddr)) #path-relative domain
{
list($domain,$addr_spec = preg_split('/@/',$laddr);
$domain = preg_replace('/^@/','',$domain);
if (!is_domain($domain)) { return false; }
$laddr = $addr_spec;
}
return(is_addr_spec($laddr));
}

function is_addr_spec ( $eaddr = "" )
{
list($local_part,$domain = preg_split('/@/',$eaddr);
if (!is_local_part($local_part) || ! is_domain($domain))
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

#local-part = word *("." word) ; uninterpreted
function is_local_part ( $local_part = "" )
{
if (empty($local_part)) { return false; }

$bit_array = preg_split('/\./',$local_part);
```