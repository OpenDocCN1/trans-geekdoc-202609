# Part II: Solutions

```
// Extracting the first-level domain name
$first_dom = substr($domain, strpos($domain, \.") + 1);
// Obtaining the name of the Whois server
// responsible for the $first_dom domain
for($i = 0; $i < count($servers); $i++) {
    if($servers[$i][0] == $first_dom)
    {
        // Remembering the server's name
        $whois = $servers[$i][1];
        // Remembering the no-such-domain-name phrase
        $not_found_string = $servers[$i][2];
        // Exiting the loop
        break;
    }
}

// Checking whether the Whois server responsible for
// the given domain level is defined
if(empty($whois)) {
    exit("No corresponding Whois server found!");
}

// Consulting the Whois server and obtaining
// information about the domain name
$fp = fsockopen($whois, 43);
fputs($fp, "$domain\r\n");
$str = "";
while(!feof($fp)) {
    $str .= fgets($fp,128);
}
close($fp);
// If the answer contains a no-such-domain-name
// phrase, the domain is not registered. Otherwise,
// the domain is registered.
if(!preg_match("/.\$not_found_string\."//is", $str)) {
    echo "This domain is taken!";
}
```