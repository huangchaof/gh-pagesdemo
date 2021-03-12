**以下所有内容是从cmd里保存的全文,`E:\git-tutor>git init`是在命令行的输入，粗体注释和标题是后面加的** 



git的三个工作区域是work tree , stage,history

work tree是当前目录树，stage是暂存区，history才是真正纳入版本管理的内容

Microsoft Windows [版本 10.0.18363.1440]
(c) 2019 Microsoft Corporation。保留所有权利。

## 初始化仓库

**创建本地仓库,git-tutor为空文件夹**

`E:\git-tutor>git init`
Initialized empty Git repository in E:/git-tutor/.git/

**查看仓库当前状态,默认已经创建了本地分支master**

`E:\git-tutor>git status`
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)

**新建文件gittutor.md**

`E:\git-tutor>touch gittutor.md`

**查看状态时发现有新文件没有track**

`E:\git-tutor>git status`
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        gittutor.md

nothing added to commit but untracked files present (use "git add" to track)

`E:\git-tutor>touch readme.md`

**有两个新文件没有track，提示用git add提交到暂存区**

`E:\git-tutor>git status`
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        gittutor.md
        readme.md

nothing added to commit but untracked files present (use "git add" to track)

## 提交

**git add . 是提交当前目录下所有文件到暂存区**

`E:\git-tutor>git add .`

**这两个文件已经staged,可以commit了**

`E:\git-tutor>git status`
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   gittutor.md
        new file:   readme.md

**提交并写了提交信息**

`E:\git-tutor>git commit -m "fist commit"`
[master (root-commit) cf459af] fist commit
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 gittutor.md
 create mode 100644 readme.md

## 配置gitignore

**gitignore文件用于配置git提交时忽略的文件**

`E:\git-tutor>touch .gitignore`

`E:\git-tutor>git status`
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .gitignore

nothing added to commit but untracked files present (use "git add" to track)

`E:\git-tutor>git add .gitignore`

`E:\git-tutor>git status`
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   .gitignore

`E:\git-tutor>git commit -m "commit ignore file"`
[master 338f3ca] commit ignore file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 .gitignore

## 查看提交历史

**git log查看当前分支的提交历史**

`E:\git-tutor>git log`
commit 338f3cab9eac8cd865db057ce54e0439730383da (HEAD -> master)
Author: huangchaof <huang_chaofan@outlook.com>
Date:   Fri Mar 12 14:05:10 2021 +0800

    commit ignore file

commit cf459af9f0b85d5fe9f210dcf7fd1d07784a1c8d
Author: huangchaof <huang_chaofan@outlook.com>
Date:   Fri Mar 12 14:02:25 2021 +0800

    fist commit

## 分支操作

### **显示所有本地分支**

`E:\git-tutor>git branch`

* master

### **创建本地新分支，新分支名为gh-pages**

`E:\git-tutor>git branch gh-pages`

**master前面的星号表示当前所在分支**

`E:\git-tutor>git branch`
  gh-pages

* master

### **切换分支**

`E:\git-tutor>git checkout gh-pages`
Switched to branch 'gh-pages'

**创建新文件，并提交到gh-pages分支**

`E:\git-tutor>touch whatis-gh-pages.md`

`E:\git-tutor>git status`
On branch gh-pages
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        whatis-gh-pages.md

nothing added to commit but untracked files present (use "git add" to track)

`E:\git-tutor>git add . && git commit -m "关于gh-pages功能的介绍"`
[gh-pages c9d7e8d] 关于gh-pages功能的介绍
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 whatis-gh-pages.md

`E:\git-tutor>git branch`

* gh-pages
  master

**查看gh-pages的分支提交信息，乱码是显示问题**

`E:\git-tutor>git log`
commit c9d7e8d1bd6c410b14e032aa3157a942a9db31c5 (HEAD -> gh-pages)
Author: huangchaof <huang_chaofan@outlook.com>
Date:   Fri Mar 12 14:09:13 2021 +0800

    <E5><85><B3><E4><BA><8E>gh-pages<E5><8A><9F><E8><83><BD><E7><9A><84><E4><BB><8B><E7><BB><8D>

commit 338f3cab9eac8cd865db057ce54e0439730383da (master)
Author: huangchaof <huang_chaofan@outlook.com>
Date:   Fri Mar 12 14:05:10 2021 +0800

    commit ignore file

commit cf459af9f0b85d5fe9f210dcf7fd1d07784a1c8d
Author: huangchaof <huang_chaofan@outlook.com>
Date:   Fri Mar 12 14:02:25 2021 +0800

    fist commit

`E:\git-tutor>git checkout master`
Switched to branch 'master'

`E:\git-tutor>git status`
On branch master
nothing to commit, working tree clean

## 远端操作

### **查看远端信息**

`E:\git-tutor>git remote -v`

**由于还没有设置远端，无法push**

`E:\git-tutor>git push`
fatal: No configured push destination.
Either specify the URL from the command-line or configure a remote repository using

    git remote add <name> <url>

and then push using the remote name

    git push <name>

### **为本地仓库添加远端**

### 推送与拉取

为本地仓库添加远端后，在某个特点分支上，使用git push 推送本地到远端， git pull获取远端的更新

`E:\git-tutor>git remote add gittutor https://gitee.com/lensousou/gittutor`

`E:\git-tutor>git push`
fatal: No configured push destination.
Either specify the URL from the command-line or configure a remote repository using

    git remote add <name> <url>

and then push using the remote name

    git push <name>

`E:\git-tutor>git push gittutor`
fatal: The current branch master has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream gittutor master

**设置本地分支的远端上游分支，此时远程仓库还没有创建，需要手动创建远程仓库**

`E:\git-tutor>git push --set-upstream gittutor master`
remote: Repository Not Found
fatal: repository 'https://gitee.com/lensousou/gittutor/' not found

**创建远程仓库后，设置成功**

E:\git-tutor>git push --set-upstream gittutor master
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (5/5), 452 bytes | 452.00 KiB/s, done.
Total 5 (delta 0), reused 0 (delta 0), pack-reused 0
remote: Powered by GITEE.COM [GNK-5.0]
To https://gitee.com/lensousou/gittutor

 * [new branch]      master -> master
   Branch 'master' set up to track remote branch 'master' from 'gittutor'.

`E:\git-tutor>git push`
`Everything up-to-date`

`E:\git-tutor>git remnote -v`
git: 'remnote' is not a git command. See 'git --help'.

The most similar command is
        remote

### **列出了当前本地分支所追踪的远程分支**

`E:\git-tutor>git remote -v`
gittutor        https://gitee.com/lensousou/gittutor (fetch)
gittutor        https://gitee.com/lensousou/gittutor (push)

`E:\git-tutor>git remote show origin`
fatal: 'origin' does not appear to be a git repository
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.

`E:\git-tutor>git remote show gittutor`

* remote gittutor
  Fetch URL: https://gitee.com/lensousou/gittutor
  Push  URL: https://gitee.com/lensousou/gittutor
  HEAD branch: master
  Remote branch:
    master tracked
  Local branch configured for 'git pull':
    master merges with remote master
  Local ref configured for 'git push':
    master pushes to master (up to date)

`E:\git-tutor>git status`
On branch master
Your branch is up to date with 'gittutor/master'.

nothing to commit, working tree clean

`E:\git-tutor>git pull`
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), 428 bytes | 53.00 KiB/s, done.
From https://gitee.com/lensousou/gittutor
   338f3ca..bfc806a  master     -> gittutor/master
Updating 338f3ca..bfc806a
Fast-forward
 remotefistfile | 3 +++
 1 file changed, 3 insertions(+)
 create mode 100644 remotefistfile

`E:\git-tutor>git log`
commit bfc806a42dfc5c29585b57c8cb31f8bd6d2ee79f (HEAD -> master, gittutor/master)
Author: lensousou <huang_chaofan@outlook.com>
Date:   Fri Mar 12 14:23:41 2021 +0800

    add remotefistfile.

commit 338f3cab9eac8cd865db057ce54e0439730383da
Author: huangchaof <huang_chaofan@outlook.com>
Date:   Fri Mar 12 14:05:10 2021 +0800

    commit ignore file

commit cf459af9f0b85d5fe9f210dcf7fd1d07784a1c8d
Author: huangchaof <huang_chaofan@outlook.com>
Date:   Fri Mar 12 14:02:25 2021 +0800

    fist commit

`E:\git-tutor>git checkout gh-pages`
Switched to branch 'gh-pages'

`E:\git-tutor>git push`
fatal: No configured push destination.
Either specify the URL from the command-line or configure a remote repository using

    git remote add <name> <url>

and then push using the remote name

    git push <name>

### **列出所有分支**

`E:\git-tutor>git branch -a`

* gh-pages
  master
  remotes/gittutor/master

**设置gh-pages追踪的远程分支**

`E:\git-tutor>git push --set-upstream gittutor gh-pages`
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (2/2), 282 bytes | 282.00 KiB/s, done.
Total 2 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Powered by GITEE.COM [GNK-5.0]
remote: Create a pull request for 'gh-pages' on Gitee by visiting:
remote:     https://gitee.com/lensousou/gittutor/pull/new/lensousou:gh-pages...lensousou:master
To https://gitee.com/lensousou/gittutor

 * [new branch]      gh-pages -> gh-pages
   Branch 'gh-pages' set up to track remote branch 'gh-pages' from 'gittutor'.

`E:\git-tutor>git remote -v`
gittutor        https://gitee.com/lensousou/gittutor (fetch)
gittutor        https://gitee.com/lensousou/gittutor (push)

### **列出所有分支的追踪关系**

`E:\git-tutor>git branch -vv`

* gh-pages c9d7e8d [gittutor/gh-pages] <E5><85><B3><E4><BA><8E>gh-pages<E5><8A><9F><E8><83><BD><E7><9A><84><E4><BB><8B><E7><BB><8D>
  master   bfc806a [gittutor/master] add remotefistfile.

![image-20210312152532156](https://gitee.com/lensousou/imagerepo/raw/master/img//20210312152539.png)

E:\git-tutor>



## 分支合并

在不同的分支上开发，会导致不同分支的文件发生变化，如何合并这些commit呢

[git教程](https://github.com/huangchaof/gh-pagesdemo/blob/gh-pages/gittutor.md)
