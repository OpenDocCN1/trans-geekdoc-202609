# 182 Chapter 4. Collection Types

each group's keys and values are indicated by one or more lines of the form
key=value. Here is an example []string that the function could process.

```
iniData := []string{
  "", Cut down copy of Mozilla application.ini file",
  "[App],",
  "Vendor=Mozilla",
  "Name=Iceเอียด",
  "Profile=mozilla/firefox",
  "Version=3.5.16",
  "[Gecko],",
  "MinVersion=1.9.1",
  "MaxVersion=1.9.1.*",
  "[XRE],",
  "EnableProfileMigrator=0",
  "EnableExtensionManager=1"
n}
```

Given this data, the function should return the following map which we
have "pretty-printed" to make it easier to see its structure.

```
[Gecko]: map[MinVersion: 1.9.1
MaxVersion: 1.9.1.*]
XRE: map[EnableProfileMigrator: 0
EnableExtensionManager: 1]
App: map[Vendor: Mozilla
Profile: mozilla/firefox
Name: Iceเอียด
Version: 3.5.16]
```

The ParseIni() function assumes a group of "General" for any
key-values that are not within the scope of the group. It is 24 lines long and
might a bit of care to get right.

+   5. Create a function that accepts a map[map]string]string that represents
ts an .ini file's data. The function should print out the data as an .ini
file with groups in alphabetical order and keys within groups in alphabetical
order, and with a line between each group. For example, given the
data from the previous exercise the output should be:

```
[App]
Name=Iceเอียด
Profile=mozilla/firefox
Vendor=Mozilla
```