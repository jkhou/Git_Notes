
## Git 工作流程
- 1.克隆 Git 资源作为工作目录。
- 2.在克隆的资源上添加或修改文件。
- 3.如果其他人修改了，你可以更新资源。
- 4.在提交前查看修改。
- 5.提交修改。
- 6.在修改完成后，如果发现错误，可以撤回提交并再次修改并提交。

## Git 工作区、暂存区和版本库
- **工作区**：电脑里能看到的目录。
- **暂存区**：英文叫 stage 或 index。一般存放在 .git 目录下的 index 文件（.git/index）中，所以暂存区也叫作索引（index）。
- **版本库**：工作区有一个隐藏目录 .git，这个不算工作区，而是 Git 的版本库。

### 注意：

当对工作区修改（或新增）的文件执行`git add`命令时，暂存区的目录树被更新，同时工作区修改（或新增）的文件内容被写入到对象库中的一个新的对象中，而该对象的ID被记录在暂存区的文件索引中。

当执行提交操作`git commit`时，暂存区的目录树写到版本库中，master 分支会做相应的更新。即 master 指向的目录树就是提交时暂存区的目录树。

当执行`git reset HEAD`命令时，暂存区的目录树会被重写，被 master 分支指向的目录树所替换，但是工作区不受影响。

当执行`git checkout` 或者`git checkout -- <file>`命令时，会用暂存区全部或指定的文件替换工作区的文件。这个操作很危险，会清除工作区中未添加到暂存区的改动。

当执行`git checkout HEAD` 或者`git checkout HEAD <file>`命令时，会用 HEAD 指向的 master 分支中的全部或者部分文件替换暂存区和以及工作区中的文件。


![git-command.jpg](https://www.runoob.com/wp-content/uploads/2015/02/git-command.jpg)

## 创建仓库
 **`git init`** 初始化一个 Git 仓库
 
 **`git clone`** 从现有 Git 仓库中拷贝项目
 
 **`git clone <repo> <directory>`**  如果需要克隆到指定的目录
 
 
## 提交与修改

### 1.git add

**`git add [file1] [file2]`** 添加一个或多个文件到暂存区

**`git add [dir]`** 添加指定目录到暂存区，包括子目录

**`git add .`** 添加当前目录下的所有文件到暂存区

### 2.git status

**`git status`** 查看在上次提交之后是否有对文件进行再次修改

**`git status -s`** 获得简短的输出结果,`AM`状态的意思是这个文件在我们将它添加到缓存之后又有改动

### 3.git diff

**`git diff`** 查看尚未缓存的改动

**`git diff --cached`** 查看已缓存的改动

**`git diff HEAD`** 查看已缓存的与未缓存的所有改动

- 区别：`git status` 显示上次提交更新后的更改或者写入缓存的改动， 而 `git diff` 一行一行地显示这些改动具体是啥。

### 4.git commit

**`git commit -m [message]`** 提交暂存区到本地仓库中

**`git commit [file1] [file2] ... -m [message]`** 提交暂存区的指定文件到仓库区

**`git commit -a`** -a 参数设置修改文件后不需要执行 git add 命令，直接提交

### 5.git reset

**`git reset  [HEAD] `** 重置暂存区的文件与上一次的提交`commit`保持一致，工作区文件内容保持不变

**`git reset HEAD^ StudyNotes.md`** 回退 StudyNotes.md 文件的版本到上一个版本 

**`git reset --soft HEAD`** --soft 参数用于回退到某个版本

**`git reset --hard HEAD`** --hard 参数撤销工作区中所有未提交的修改内容，将暂存区与工作区都回到上一次版本，并删除之前的所有信息提交

**`git reset --hard origin/master`** 将本地的状态回退到和远程的一样

**`git reset HEAD`** 用于取消已缓存的内容
 
 #### HAED说明：
 
 - `HEAD` `HEAD~0` 表示当前版本
 
 - `HEAD^` `HEAD~1` 表示上一个版本
 
 - `HEAD^^` `HEAD^2` 表示上上一个版本
 
 - `HEAD^^^` `HEAD^3` 表示上上上一个版本
 
 ### 6.git rm
 
 **`git rm <file>`** 将文件从暂存区和工作区中删除
 
 **`git rm -f <file>`** 强行从暂存区和工作区中删除修改后的文件
 
 **`git rm --cached <file>`** 把文件从暂存区域移除，但仍然希望保留在当前工作目录中
 
 ## 提交日志
 
 **`git log`**  查看历史提交记录
 
 **`git blame <file>`** 以列表形式查看指定文件的历史修改记录
 
 ## 远程操作
 
 ### 1.git remote
 
 **`git remote -v`** 显示所有远程仓库,origin 为远程地址的别名
 
 **`git remote show https://github.com/jkhou/Git_Notes`** 显示某个远程仓库的信息
 
 **`git remote rm origin`** 删除关联的origin的远程库
 
 **`git remote add origin git@github.com:jkhou/Git_Notes.git`** 添加远程版本库
 
  ### 2.git remote
 
 **`git fetch origin`** 告诉 Git 去获取它有你没有的数据
 
 **`git merge origin/master`** 将服务器上的任何更新（假设有人这时候推送到服务器了）合并到你的当前分支
 
 
 
 
 
 
