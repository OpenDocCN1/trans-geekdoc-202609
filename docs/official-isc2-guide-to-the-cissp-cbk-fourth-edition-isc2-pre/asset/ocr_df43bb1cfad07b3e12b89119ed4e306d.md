Fill in or edit fields inside the property page to create a new Password Settings object. The Name and Precedence fields are required.

![](bbox=[0.06, 0.07, 0.94, 0.52])

Under Directly Applies To, click Add, type group1, and then click OK.

This associates the Password Policy object with the members of the global group you created for the test environment.

+   1. Click OK to submit the creation.

# Windows PowerShell Equivalent Commands

The following Windows PowerShell cmdlet or cmdlets perform the same function as the preceding procedure. Enter each cmdlet on a single line, even though they may appear word-wrapped across several lines here because of formatting constraints.

```
New-ADFineGrainedPasswordPolicy TestPswd -ComplexityEnabled:$true-
LockoutDuration:"00:30:00" -LockoutObservationWindow:"00:30:00"-
LockoutThreshold:"0" -MaxPasswordAge:"42.00:00:00"-
MinPasswordAge:"1.00:00:00" -MinPasswordLength:"7"-
PasswordHistoryCount:"24" -Precedence:"1"-
ReversibleEncryptionEnabled:$false-
ProtectedFromAccidentalDeletion:$true
Add-ADFineGrainedPasswordPolicySubject TestPswd -Subjects group1
```