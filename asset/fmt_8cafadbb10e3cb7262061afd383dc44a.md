
PS C:\> `Import-Module ServerManager`

PS C:\> `Add-Windows Feature FS-DFS`

PS C:\> `Import-Module DFS`

### 3. 运行以下命令创建一个独立的 DFS 命名空间：

```
PS C:\> New-Dfsnroot -TargetPath \Test-DFS\Software" -Type Standalone -EnablesSiteHosting -Path \Test\Software"
```

### 4. 要查看 Windows Server 2012 R2 中所有可用的 DFS cmdlet，运行以下命令：

```
PS C:\> Get-Command -Module DFS
```
