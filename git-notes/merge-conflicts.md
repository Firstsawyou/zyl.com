# 解决合并的冲突

把issue2分支和issue3分支的修改合并到master。

切换master分支后，与issue2分支合并。

```sehll
$ git checkout master
Switched to branch 'master'
$ git merge issue2
Updating b2b23c4..8f7aa27
Fast-forward
 myfile.txt |    2 ++
 1 files changed, 2 insertions(+), 0 deletions(-)
```

接着合并issue3分支。

```shell
$ git merge issue3
Auto-merging myfile.txt
CONFLICT (content): Merge conflict in myfile.txt
Automatic merge failed; fix conflicts and then commit the result.
```

## 用rebase合并

合并issue3分支的时候，使用rebase可以使提交的历史记录显得更简洁。

现在暂时取消刚才的合并。

```shell
$ git reset --hard HEAD~
```

切换到issue3分支后，对master执行rebase。

```shell
$ git checkout issue3
Switched to branch 'issue3'
$ git rebase master
First, rewinding head to replay your work on top of it...
Applying: 添加pull的说明
Using index info to reconstruct a base tree...
<stdin>:13: new blank line at EOF.
+
warning: 1 line adds whitespace errors.
Falling back to patching base and 3-way merge...
Auto-merging myfile.txt
CONFLICT (content): Merge conflict in myfile.txt
Failed to merge in the changes.
Patch failed at 0001 添加pull的说明

When you have resolved this problem run "git rebase --continue".
If you would prefer to skip this patch, instead run "git rebase --skip".
To check out the original branch and stop rebasing run "git rebase --abort".
```

和merge时的操作相同，修改在myfile.txt发生冲突的部分。

```shell
add 把变更录入到索引中
<<<<<<< HEAD
commit 记录索引的状态
=======
pull 取得远端数据库
```

rebase的时候，修改冲突后的提交不是使用commit命令，而是执行rebase命令指定 --continue选项。若要取消rebase，指定 --abort选项。

```shell
$ git add myfile.txt
$ git rebase --continue
Applying: 添加pull的说明
```

这样，在master分支的issue3分支就可以fast-forward合并了。切换到master分支后执行合并。

```shell
$ git checkout master
Switched to branch 'master'
$ git merge issue3
Updating 8f7aa27..96a0ff0
Fast-forward
myfile.txt |    1 +
1 files changed, 1 insertions(+), 0 deletions(-)
```