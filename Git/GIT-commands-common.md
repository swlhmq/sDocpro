
git add
===
Add file contents to the index  
常用选项：  
（1）add目录或文件  
git add .  
git add filename  
（2）-n or --dry-run  
Don’t actually add the file(s), just show if they exist and/or will be ignored.  
git add -n .  


git commit
===
Record changes to the repository  
常用选项：  
（1）无选项  
从index区提交  
git commit  
（2）--amend  
追加到当前的提交节点。  
git commit --amend  
（3）-m <msg>  
Use the given <msg> as the commit message. 无-m时则打开编辑器输入message。  
git commit -m “hello”  
（4）-c <commit> or --reedit-message=<commit>  
使用commit的commit message，可编辑。  
git reset HEAD^  
edit something && git add .  
git commit -c ORIG_HEAD  
仍使用被reset掉的commit message。  
（5）--dry-run  
模拟commit，not -n  
git commit -dry-run .  
（6）-s or --signoff  
Add Signed-off-by line by the committer at the end of the commit log message.  


git status
===
Show the working tree status  
常用选项：  
（1）无选项  
git status  
（2）-s or --short  
git status -s  
MM hello.c，第一个M指提交到INDEX区，第二个M指在工作区。  
?? hello.c指本地新增文件。  
A  hello.c指新增文件add到INDEX区。  


git diff
===
Show changes between commits, commit and working tree, etc  
常用选项：  
（1）无选项  
比较本地与INDEX的差异。  
git diff  
比较commitA与commitB的差异  
git diff commitA commitB  
（2）--cached  
比较INDEX与HEAD的差异。  
git diff --cached  


git branch
===
List, create, or delete branches  
常用选项：  
（1）无选项  
显示本地已有的分支。  
git branch  
（2）-r  
显示本地记录的remote branch。  
git branch -r  
（3）-a  
显示本地记录的所有分支，包括本地和remote branch。  
git branch -a  
（4）-vv  
显示详细分支信息，very verbose。  
git branch -vv  
（5）-d  
删除本地分支，不能删除当前分支。  
git branch -d br_one  

git log
===
Show commit logs  
常用选项：  
（1）无选项  
显示当前分支的提交信息。  
git log  
显示分支br_one的提交信息。  
git log br_one  
显示远程分支master的提交信息。  
git log origin/master  
显示refs的提交信息，refs可在.git/refs下找到。  
git log refs/head/perf-opencsd-v4.9  
（2）--stat  
显示当前分支的提交信息，以统计方式显示，含文件名、修改行数等。  
git log --stat  
（3）-n N或-N  
显示当前分支的最近N个提交信息。  
例如最近3个。  
git log -3  
（4）--author  
显示某author的提交信息。  
git log --author=roger  
（5）--oneline  
显示当前分支的提交信息，以单行方式显示。  
git log --oneline  
（6）-p or --patch  
显示当前分支的提交信息，以patch方式显示，含文件内容差异。  
git log -p  


git show
===
Show various types of objects(blobs, trees, tags and commits).  
常用选项：  
（1）无选项  
显示HEAD指向的commit信息，含差异修改。  


git blame
===
Show what revision and author last modified each line of a file  
常用选项：  
（1）无选项  
显示指定文件行修改COMMITID及作者。  
git blame filename  

git clean
===
Remove untracked files from the working tree  
常用选项：  
（1）-f or --force  
清除当前目录及子目录下的untracked files。  
git clean -f  
（2）-n or –dry-run  
虚拟运行，不真实清除。  
git clean -n  
（3）-i or --interactive  
交互式clean  
git clean -i  


git rm
===
Remove files from the working tree and from the index  
常用选项：  
（1）无选项  
删除工作区和INDEX区文件。  
git rm hello.c  
git commit -m “delete hello.c”  
（2）--cached  
删除INDEX区文件，工作区仍保留。  
git rm --cached hello.c  


git stash
===
Stash the changes in a dirty working directory away  
常用选项：  
（1）git stash  
缓存INDEX和工作区内容，以压栈的方式。不包括untracked files。  
（2）git stash pop <stash>  
默认弹出栈顶的数据到工作区。  
git stash pop stash@{1}  
弹出某一个。  
（3）git stash list  
显示已缓存的内容list。例如：  
stash@{0}: WIP on master: 342980b new  
stash@{1}: WIP on master: a6986b9 all  
stash@{2}: WIP on master: a6986b9 all  
stash@{0}为栈顶，最新压入的数据，on压栈时基于的branch_name: commit_id message。  
（4）git stash show <stash>  
默认显示栈顶缓存内容。  
git stash show stash@{1}  
显示某一个。  
（5）git stash drop  
默认丢弃栈顶缓存内容。  
git stash show stash@{0}  
丢弃某一个。  
（6）git stash clear  
清除所有已缓存内容。  


git reset
===
Reset current HEAD to the specified state  
reset时自动保存ORIG_HEAD。  
常用选项：  
（1）无选项，等同于--mixed  
Reset INDEX，工作区保留。  
git reset HEAD^  
（2）--hard  
Reset INDEX和工作区。  
git reset HEAD^ --hard  
（3）--soft  
不reset INDEX和工作区，仅reset HEAD到commit。  
注意事项：  
（1）自上而下reset，HEAD to INDEX to Working Area，--hard时将删除所有差异内容，注意保存。  


git checkout
===
Checkout a branch or paths to the working tree  
常用选项：  
（1）无选项  
git checkout <branch>，例如Checkout某一branch到工作区。  
git checkout br_one  
git checkout \<DIR\>，例如Checkout当前目录from INDEX到工作区。  
git checkout .  
（2）-b  
基于（当前）分支创建新分支，并切换到新分支，新分支含原分支所有commits。  
git checkout -b br_master1  
（3）--file_name  
Checkout某文件，从INDEX到工作区。  
git checkout --hello.c  

注意事项：  
（1）checkout分支时将覆盖工作区和INDEX内容，切换时提示，故切换分支时已有修改需要提交或stash。  


git remote
===
Manage the set of repositories ("remotes") whose branches you track.  
常用选项：  
（1）无参数  
显示tracked remote name，例如origin  
git remote  
（2）-vv  
show remote url after name  
git remote -vv  


git config
===
Get and set repository or global options  
常用选项：  
（1）--global，write to global ~/.gitconfig file  
配置用户名、邮箱。  
git config --global user.name roger  
git config --global user.email roger@163.com  
配置别名。  
git config --global alias.st status  
git config --global alias.df diff  
（2）-l or --list  
List all variables set in config file.  
git config -l  


git init
===
Create an empty Git repository or reinitialize an existing one  
常用选项：  
（1）git init  
初始化一个git仓。  


git clone
===
Clone a repository into a new directory  
常用选项：  
（1）无选项  
Clone一个网络仓。  
git clone https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git  
（2）-o <name>  
Instead of using the remote name origin to keep track of the upstream repository, use <name>.  
git clone https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git -o my_linux  
so named “my_linux/master”，否则为“origin/master”，仓目录仍为linux。  
（3）--mirror  
Set up a mirror of the source repository.  
建立镜像库，可供其它client下载。  
例如：git clone --mirror https://github.com/Linaro/OpenCSD.git  
在~/gitmirror下建立镜像库，则client可下载  
git clone ssh:username@10.10.10.10/gitmirror/OpenCSD.git  
（4）--bare  
Make a bare Git repository.  
只生成git数据库仓，无工作目录，通常用于建server git库。  


git fetch
===
Download objects and refs from another repository  
更新本地数据库和远程跟踪分支指向。  
常用选项：  
（1）无选项，可从网络端或本地其他仓获取。  
获取所有origin下所有分支数据。  
（2）\<repo\> \<from\>\<:to\>  
从指定仓、分支获取。  
不带to时获取commit到FETCH_HEAD，否则到to（本地一个跟踪分支）。  
git fetch origin master  
（3）--dry-run  
虚拟运行，显示哪些会被获取。  
$ git fetch origin edit --dry-run
From https://github.com/swlhmq/hello  
 * branch            edit        -> FETCH_HEAD  
   888a44b..88414cc  edit        -> origin/edit  
去除--dry-run获取同上，再次获取为空：  
$ git fetch origin edit  
From https://github.com/swlhmq/hello  
 * branch            edit        -> FETCH_HEAD  
注意事项：  
（1）fetch只更新本地数据库，代码合并需要调用git merge。  


git-cherry-pick
===
Apply the changes introduced by some existing commits  
常用选项：  
（1）无选项  
获取指定commits,从本地数据库搜索。  
git cherry-pick commit-id  
获取分支br_one的最后一个commit  
git cherry-pick br_one  
获取分支br_one的最后两个commit  
git cherry-pick br_one~ br_one  
（2）-x  
获取时同时取得original commit message。  
git cherry-pick -x commit-id  
（3）cqa  
git cherry-pick --continue  
git cherry-pick --quit  
git cherry-pick --abort  


git merge
===
Join two or more development histories together  
安全的操作，现有分支历史不会被更改。  
常用选项：  
（1）合并本地分支内容  
git merge <from_branch>  
例如合并edit分支到当前分支。  
git merge br_edit  
如果当前分支为br_merge_edit，则git log查询可看到一个新节点。  
commit 389582a01deb2cd126270a4295bae5e71a792b44  
Merge: 0bafc3b 898c6b7  
Merge branch 'edit' into br_merge_edit  
（2）合并远程分支内容  

注意事项：  
（1）merge将覆盖工作区和INDEX内容，切换时提示：  
error: Your local changes to the following files would be overwritten by merge:  
        README.md  
Please, commit your changes or stash them before you can merge.  
Aborting  


git pull
===
Fetch from and integrate with another repository or a local branch  

常用选项：  
（1）拉取，fetch远程并合并到本地分支  
git pull  
自动寻找匹配的远程分支进行更新。  
如本地无新commits，则git log可查看到各commit。  
如本地有新commits，则git log查询可看到一个新节点。例如：  
Merge branch 'master' of https://github.com/xxxxxx/hello

（2）拉取，fetch指定远程并合并到本地分支  
git pull <remote> <branch>  

（3）等同操作  
git pull origin next  
same to  
git fetch origin  
git merge origin/next  

注意事项：  
（1）merge将覆盖工作区和INDEX内容，切换时提示：  
error: Your local changes to the following files would be overwritten by merge:  
        README.md  
Please, commit your changes or stash them before you can merge.  
Aborting  


git push
===
Update remote refs along with associated objects  
常用选项：  
（1）git push  
Works like git push <remote>, where <remote> is the current branch’s remote  
提交本地commits到默认remote。  
（2）  


git rebase
===
Forward-port local commits to the updated upstream head  
注意只能在本地分支进行，不能在公共分支上使用。  
常用选项：  
（1）git rebase branch_name  
例如本地位于edit分支，执行：  
git rebase master  
基于master分支，将br_edit上差异commit依次追加到master分支上。  


git format-patch
===
Prepare patches for e-mail submission   
（1）-\<n\>  
Prepare patches from the topmost <n> commits.   
例如从最近的3个commit打3个patch。  
git format-patch -3  
（2）-o \<path\>   
patch生成到path下，未指定则生成到当前目录下。  


git am
===
Apply a series of patches from a mailbox  
（1）无选项  
例如，应用patches下所有patch。  
git am ~/patches/*.patch  


git apply
===
Apply a patch to files and/or to the index  


