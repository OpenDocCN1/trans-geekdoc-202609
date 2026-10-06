# CHAPTER 8 CREATING AND MANAGING USER ACCOUNTS

# NOTICE THE HEADER ROW

The header row is the same as the variables you used earlier with the New-ADUser cmdlet. The rows
below the header row in the CSV file contain the values for creating each user.

Now you want to run a command that will read each row from the CSV file that you've saved
c C:\users.csv. The command will execute the New-ADUser cmdlet using the values from
the. Here's the command:

```
PS C:\Users\Administrator> Import-csv c:\users.csv | foreach
{New-ADUser -Name $_ -SamAccountName $_ -AccountName $_ -GivenName
_.GivenName $_ -Surname $_ -DisplayName $_ -Path $-
UserPrincipalName $_ -UserPrincipalName $_ -Password (Convert-SecureString -PlainText $_.Password -Force) -Enabled true -ChangePasswordAtLogon 1}
```

Don't let the size of this command confuse you. We promise it is simple to
once you understand how to break it down into its components:

+   IMPORT-CSV This PowerShell cmdlet reads the CSV file you created and saved as C:\nusers.csv.
* This is the vertical bar on your keyboard. For that power that PowerShell
gives you the ability to feed the results of one cmdlet as a parameter to another cmdlet.
You're here reading the CSV file and feeding it into the next part of the command.

FOREACH This cmdlet takes the CSV file, reads it as three items, which is rows of
data (excluding the header row). The FOREACH cmdlet will now run a task using each of the
rows as a parameter.

+   NEW-ADUSER You know that this command will create a user. How does it get its values?
* Each flag in the New-ADUser cmdlet requires a value. You know that you have assigned a
header to the CSV. Each of the $_ entries in the command file refers to one of the head-
ers. You know that $_ represents an object in PowerShell and $_Name represents the
property Name of the object. For example, the $_Name refers to the Name in the CSV.
So, New-ADUser will take the value Rachel from the first row and use it for
_.Name.

AccountPassword You're again converting the password value to a secure string to meet the
requirements of the flag.

This command will read each of the three data rows from the CSV file. It will load the
and create user objects based on these values, such as in the OU you specified in
t CSV file. The users will have their password set, enabled, and then be forced to change
the password when they log in.

Nothing is stopping you from adding columns to this CSV and matching additional flags
the command to further populate the attributes of the user object, such as roaming profile,
directory, and so.

Using this approach, you could manually or automatically (using some developed
export tool from a personnel system) create this CSV file and run this one command