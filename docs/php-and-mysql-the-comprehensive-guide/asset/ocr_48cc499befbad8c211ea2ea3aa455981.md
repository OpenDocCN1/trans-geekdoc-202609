```
return true;
}
}
</script>
```

And that's it! The following listing shows the complete JavaScript code, embedded in an
"even more perfect" form.

```
<html>
<head>
<title>Order form</title>
<script>
function check(f) {
var error = "";
if (!(f.elements["Salutation"] ||
(f.elements["Salutation"][0].checked &
!f.elements["Salutation"][1].checked)) {
error += "Salutation\n";
}
if (!f.elements["FirstName"] || f.elements["FirstName"].value == "") {
error += "First name\n";
}
if (!(f.elements["LastName"] || f.elements["LastName"].value == "")) {
error += "Last name\n";
}
if (!f.elements["Email"] || f.elements["Email"].value == "") {
error += "Email\n";
}
if (!(f.elements["Promo"] || f.elements["Promo"].value == "")) {
error += "Promo\n";
}
if (!(f.elements["Number"] || f.elements["Number"].selectedIndex < 1) {
error += "Number of tickets\n";
}
if (!(f.elements["Section[]"] ||
f.elements["Section[]"].selectedIndex == -1) {
error += "Section\n";
}
if (!f.elements["Comments"] || f.elements["Comments"].value == "") {
error += "Comments\n";
}
if (!(f.elements["Terms"] || !f.elements["Terms"].checked) {
error += "Terms & conditions\n";
}
if (error != "") {
```