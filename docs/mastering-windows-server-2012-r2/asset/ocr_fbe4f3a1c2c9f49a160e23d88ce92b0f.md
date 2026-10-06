What you've done here is substitute the Read-Host cmdlet for the $pw variable, as in the previous approach. This will cause the Read-Host cmdlet to run before the New-ADUser cmdlet can complete and then enter the secure string as a value for the -Password flag. When you run the command, you are prompted for a password, and then the user object is created.

# Creating Many Users at Once

Imagine that you work in a university as an Active Directory administrator. You probably have a forest for student accounts. Every summer you delete all the old student accounts. You then create new users for each student attending the first semester of the year. You are looking at a task where you might be creating thousands of user objects. Are you really going to use ADUC, ADAC, or one of the previous PowerShell examples to do that? We hope you're not planning on using one of those approaches.

You can use a powerful one-line PowerShell command to do this work with very little effort. What you are going to do is create a comma-separated value (CSV) file in Excel or other spreadsheet tool. A more advanced network may have a personnel management system that can create this via some export. The CSV file is a text file that contains a header row describing values and is followed by row for each user. Each row will contain the values that describe the user. Here are the contents of a file called users.csv that you can use to create users:

| Name | SamAccountName | GivenName | Surname |
| --- | --- | --- | --- |
| Kelly Kelly | RKelly | Rachel | Kelly |
| Ulrika Gerhardt | UGerhardt | Ulrika | Gerhardt |
| Tomasz Kozlowski | TKozlowski | Tomasz | Kozlowski |
| DisplayName | Path | UserPrincipalName | AccountPassword |
| Kelly Kelly | OU=Users,OU=BigFirm, RKelly@bigfirm.com,DC=bigfirm,DC=com | | NewPassword |
| Ulrika Gerhardt | OU=Users,OU=BigFirm, UGerhardt@bigfirm.com, .com | | NewPassword |
| Tomasz Kozlowski | OU=Users,OU=BigFirm, TKozlowski@bigfirm.com, .com | | NewPassword |

If you open that CSV file, .csv, in Notepad, it will look like this:
Name,SamAccountName,GivenName,Surname,Path,UserPrincipalName,AccountPassword
Kelly Kelly,RKelly,Rachel,Rachel Kelly,"OU=Users,OU=BigFirm,DC=bigfirm,DC=com",RKelly@bigfirm.com,NewPassword
Ulrika Gerhardt,UGerhardt,Ulrika,Gerhardt,Ulrika Gerhardt,"OU=Users,OU=BigFirm,DC=bigfirm,DC=com",UGerhardt@bigfirm.com,NewPassword
Tomasz Kozlowski,TKozlowski,Tomasz,Kozlowski,Tomasz Kozlowski,"OU=Users,OU=BigFirm,DC=bigfirm,DC=com",TKozlowski@bigfirm.com