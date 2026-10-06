When you review the volume in Server Manager, you will see the Deduplication Rate (measured in %) and Deduplication Savings (measured in bytes) columns, as shown in Figure 12.75.

# FIGURE 12-75
Viewing deduplication information in Server Manager

![](bbox=[0.312, 0.177, 0.882, 0.432])

# Configuring Data Dedup with PowerShell

We will show you how to work with deduplication in PowerShell. Figure 12.76 shows the available PowerShell cmdlets.

# FIGURE 12-76
PowerShell cmdlets for deduplication

```
PS C:\Users\administrator> get-command -Module DeDuplication
| CommandType | Name | Module |
|---|---|---||
| Function | Enable-DedupVolume | DeDuplication |
| Function | Disable-DedupVolume | DeDuplication |
| Function | Get-DedupConfig | DeDuplication |
| Function | Get-DedupMetadata | DeDuplication |
| Function | Get-DedupUsage | DeDuplication |
| Function | Get-DedupStatus | DeDuplication |
| Function | New-DedupVolume | DeDuplication |
| Function | Remove-DedupData | DeDuplication |
| Function | Remove-DedupVolume | DeDuplication |
| Function | Set-DedupConfig | DeDuplication |
| Function | Set-DedupVolume | DeDuplication |
| Function | Update-DedupStatus | DeDuplication |
```

+   1. To enable dedup for a volume, use the following syntax:
Enable-DedupVolume E:\

The output is shown in Figure 12.77.

You know that dedup is enabled, but you'd like to find out how much it has saved you and other such data.
2. Use the Get-DedupStatus cmdlet, as shown in Figure 12.78.