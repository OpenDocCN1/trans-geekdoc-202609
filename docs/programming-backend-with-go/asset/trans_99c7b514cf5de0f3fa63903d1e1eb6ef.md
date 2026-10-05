
# Git 版本控制

Git 是管理软件开发项目不可或缺的工具，包括 gitforgits.com，因为它是一个分布式版本控制系统。它允许多名程序员在同一个项目上工作而不会产生冲突，并且可以对每次更改的代码库进行监控，从而使回滚和版本跟踪变得更加容易。

## 为什么使用 Git？

使用 Git 管理 gitforgits.com 使团队能够：
* 跟踪项目文件中的更改。
* 与他人无缝协作，合并来自多个开发者的更改。
* 维护谁在何时做了什么更改的历史记录。
* 如果当前版本中检测到问题，可以恢复到项目的先前版本。
* 管理项目的不同版本和分支，允许在不影响主代码库的情况下进行实验性开发。

## 基本 Git 命令

要开始使用 Git，首先需要在机器上安装它。安装后，可以使用以下信息对其进行配置，该信息将用于你的提交：

```
git config --global user.name "Your Name"
git config --global user.email "your.email@gitforgits.com"
```

对于 gitforgits.com，设置好目录后的第一步是初始化一个新的 Git 仓库：

```
git init
```

上述命令会在你的项目文件夹中创建一个新的 `.git` 目录，所有项目的版本历史都将存储在其中。

## 添加文件和提交更改

Git 仓库初始化后，你可以开始向项目添加文件。例如，创建新文件如 `main.go` 后，需要将其添加到仓库中：

```
git add main.go
```

要保存更改，需要提交它们：

```
git commit -m "Initial commit with main.go"
```

`-m` 标志允许你添加提交信息，即对该次提交中所做更改的简要描述。

## 分支

分支是 Git 中的一项强大功能，它允许你从主开发线分支出去并独立工作，而不会影响主项目。例如，如果你想为 gitforgits.com 开发新功能，可以创建一个新分支：

```
git branch feature-new-checkout-system
git checkout feature-new-checkout-system
```

或使用较新版本的 Git 以单条命令执行：

```
git checkout -b feature-new-checkout-system
```

这会创建一个新分支并切换到它。在此分支上进行的更改和提交不会影响主分支（`master` 或 `main`），从而允许安全地开发和实验。

## 查看更改和日志

要查看文件中的更改内容：

```
git status
```

上述命令会显示哪些文件已更改以及哪些文件已暂存以待提交。如果你想查看所做的确切更改，可以使用：

```
git diff
```

要查看提交历史：

```
git log
```

此命令会显示当前分支中的所有提交列表，以及它们的 ID、作者信息和提交信息。

## 合并分支

在分支上完成功能开发后，可以将其合并回主分支。例如，一旦新的结账系统经过测试并准备好成为主应用程序的一部分，你将切换回主分支并合并功能分支：

```
git checkout main
git merge feature-new-checkout-system
```

此命令会将 `feature-new-checkout-system` 的更改合并到主分支中。

## 处理合并冲突

有时，Git 无法自动合并更改，从而导致冲突。你需要通过编辑 Git 显示的文件手动解决这些冲突，然后将其标记为已解决：

```
git add filename
```

解决冲突后，可以继续合并过程。

## 使用 Git 与远程仓库

对于 gitforgits.com 这样的协作项目，你很可能会使用托管在 GitHub、GitLab 或 Bitbucket 上的远程仓库。要将本地仓库与远程仓库同步：

```
git remote add origin https://github.com/username/gitforgits.com.git
git push -u origin main
```

这会设置一个名为 `origin` 的远程仓库并链接到你的仓库 URL，并将你的提交推送到该仓库。
