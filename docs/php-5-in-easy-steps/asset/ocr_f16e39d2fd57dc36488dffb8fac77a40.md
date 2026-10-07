# cont'd

```
#define = message
$msg = "This is a multi-part message in MIME format\r\n";
$msg = "--${str}\r\n";
$msg = "Content-Type: text/plain; charset=iso-8859-1\r\n";
$msg = "Content-Transfer-Encoding: 8bit\r\n";
$msg = "${comments}\r\n";
$msg = "--${str}\r\n";

#define the non-attachment
$msg = "Content-Type: ${att_type}";
$msg = "name=${${att_name}"\n";
$msg = "Content-Disposition: attachment;";
$msg = "filename=${${att_name}"\n";
$msg = "Content-Transfer-Encoding: base64\r\n";
$msg = "file\r\n";
$msg = "--${str}";

#send mail
$ok = mail($to, $re, $msg, $hdr);
if ($ok) echo "OK";
?>
```

![](bbox=[0.17, 0.085, 0.255, 0.155])

The Content-Transfer-Encoding header for the text is "bit", which is its natural state. The attachment has been encoded with base64_encode() function so is described as "base64".

The Content-Disposition header is described here but could alternatively be "inline" to include the attachment in the email message body.

![](bbox=[0.025, 0.215, 0.155, 0.295])

![](bbox=[0.025, 0.405, 0.155, 0.485])

| From | bob@some-mail-server.com> |
| Sent | Monday, June 14, 2005 12:15 PM |
| To | phpSinesystems@hotmail.com |
| Subject | New Lilguy Image |

Attachment: lilguy.gif(< 0.01 MB)

Here is the new Lilguy image...

![](bbox=[0.285, 0.565, 0.915, 0.915])