
# CHAPTER 12 WINDOWS 2012 R2 STORAGE: STORAGE SPACES, SAN ABILITIES, AND BETTER TOOLS

FIGURE 12.73
Configuring New Volume Deduplication Settings

![](img/41a83208e6906a3732620203b836cea7_675_0.png)

FIGURE 12.74
Changing the dedup schedule

![](img/41a83208e6906a3732620203b836cea7_675_1.png)

When you review the volume in Server Manager, you will see the Deduplication Rate (measured in %) and Deduplication Savings (measured in bytes) columns, as shown in Figure 12.75.

# FIGURE 12-75
Viewing deduplication information in Server Manager

![](img/41a83208e6906a3732620203b836cea7_676_0.png)

# Configuring Data Dedup with PowerShell

We will show you how to work with deduplication in PowerShell. Figure 12.76 shows the available PowerShell cmdlets.

# FIGURE 12-76
PowerShell cmdlets for deduplication

```
PS C:\Users\administrator> get-command -Module DeDuplication
| CommandType | Name | Module |
|---|---|---|---|
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

- 1. To enable dedup for a volume, use the following syntax:
`Enable-DedupVolume E:\`

The output is shown in Figure 12.77.

You know that dedup is enabled, but you'd like to find out how much it has saved you and other such data.
- 2. Use the Get-DedupStatus cmdlet, as shown in Figure 12.78.

# FIGURE 12-77
Enable dedup output with PowerShell

```
C:\Users\Administrator> Enable-DedupVolume 'E:\' |
| Enabled | UsageType | SavedSpace | SavingsRate | Volume |
| True | Default | 0 | 0 | E: |
| C:\Users\Administrator> | | | | Subsystem: Storage Smart
```

# FIGURE 12-78
GetDedupStatus output

```
C:\Users\Administrator> get-dedupstatus |
| FreeSpace | SavedSpace | OptimizedFiles | InPolicyFiles | Volume |
| 99.63 GB | 0 | 0 | | E: |
```

On the volumes in which we have a lot of information to dedup, but this has here for a reason. In our configuration we excluded E:\shares because we're not 100 percent sure what is there, and since it is an NFS share for Linux, we just don't want to take the chance. (In practical terms it doesn't matter what the client is; it is transparent) Inside E:\ we copied our Win2012R2_Preview ISO is about 4 GB in size. We created an additional folder at E:\TestData and we copied Win2012R2_Preview ISOs under different names and also a Technical folder, which contains details on technical information. Figure 12.79 for our sample data.

# FIGURE 12-79
Contents of E:\TestData

![](img/41a83208e6906a3732620203b836cea7_677_0.png)

Remember that although we have copied this data, we now have to wait three days for it to be included for deduplication? If you can't wait that long, you can use the cmdlet Start-DedupJob to accelerate this.

- 3. The syntax is as follows:

`Start-DedupJob -Type Optimization -Volume E:`
As you can see in Figure 12.80, dedup has started a manual schedule and it is in the current state of Queued. You can check it from here if you want.

# FIGURE 12-80
Output of Start-DedupJob

```
C:\Users\Administrator> start-dedupjob type Optimization -Volume E:
| Type | ScheduleType | StartTime | Progress | State | Volume |
| Optimization | Manual | | 0 | Queued | E: |
```

- 4. In Task Scheduler, choose Task Scheduler ➤ Microsoft ➤ Windows ➤ Deduplication.

As shown in Figure 12.81, you will see three jobs listed (we will explain the last two jobs later in this):

- BackgroundOptimization
- WeeklyGarbageCollection
- WeeklyScrubbing

# FIGURE 12.81
Manually invoking BackgroundOptimization

![](img/41a83208e6906a3732620203b836cea7_678_0.png)

- 5. Right-click BackgroundOptimization, return to PowerShell, and use the cmdlet Get-DedupJob.

See Figure 12.82 for sample output.

# FIGURE 12.82
Sample output of the Get-DedupJob cmdlet

![](img/41a83208e6906a3732620203b836cea7_678_1.png)

Figure 12.83 shows just how much it has saved already, and it is not even finished.

- 6. Now compare the output in Figure 12.84 when the Get-DedupJob cmdlet has completed.

In our test lab we have already saved 4.64 GB, which is great because storage is tight!

# CHAPTER 12 WINDOWS 2012 R2 STORAGE: STORAGE SPACES, SAN ABILITIES, AND BETTER TOOLS

# FIGURE 12.83
Output of DedupJob while running

```
C:\Users\Administrator> get-dedupstatus
| FreeSpace | SavedSpace | OptimizedFiles | InPolicyFiles | Volume |
| 71.55 GB | 33 GB | | | E: |
``` (Note: OCR text for Figure 12.83 was fragmented in the source, reconstructed based on context and table structure)

# FIGURE 12.84
Output of Get-DedupJob when completed

```
C:\Users\Administrator> get-dedupstatus
| FreeSpace | SavedSpace | OptimizedFiles | InPolicyFiles | Volume |
| 46 GB | 4 GB | | | E: |
```

- 7. Try using the Get-Dedup cmdlet.
- 8. As an additional exercise, remove E:\Shares and rerun the optimization.
- 9. Finally, right-click the TestData folder and view its properties.

# FIGURE 12.85
Folder properties after running dedup

![](img/41a83208e6906a3732620203b836cea7_679_0.png)

So now you have seen dedup in action. But where has the data actually gone?
- 10. Use the Get-DedupMetadata to see the reduction in chunk store.

# CHAPTER 12 WINDOWS 2012 R2 STORAGE: STORAGE SPACES, SAN ABILITIES, AND BETTER TOOLS

# FIGURE 12.86
Output of Get-DedupMetadata

```
PS C:\Users\administrator> get-dedupstatus
| FreeSpace | SavedSpace | OptimizedFiles | InPolicyFiles | Volume |
| 46 GB | 4 GB | | | E: |
```
