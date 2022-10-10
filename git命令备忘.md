# git命令备忘

查看所有分支 git branch -a

按q退出编辑模式

创建分支 git branch ..

同步仓库状态 git fetch

切换分支 git checkout

检出远程分支 git checkout origin/...

git checkout -b 本地分支名字 origin/远程分支名

创建并切换 git checkout -b 

查看当前分支 git branch

合并分支 git merge dev

把本地分支推到远程   git push origin  branch : branch 

把当前本地分支推到远程名字为v1.1.3  git push --set-upstream origin v1.1.3

当前分支和远程分支关联 git branch --set-upstream-to=origin/v1.1.3

查看历史提交 git log

查看所有历史提交 git reflog

以列表形式查看指定文件的历史修改记录。 git blame <file>

忽略工作区未被执行 git add 的文件变更，将其隐藏起来，这样在执行 git commit 时不会被影响  git stash -u -k    

 恢复工作区被忽略的文件   git stash pop          



## 标签

```
git tag -a v1.0  给最近一次提交打上标签
git tag -a v0.9 85fc7e7  给某次提交追加标签
git tag 查看所有标签
git tag -d v1.0 删除标签
git show <tagname> 查看此版本修改内容
```

**git怎样还原所有修改**

还原有三种情况：

- 只是修改了文件，没有任何 git 操作
- 修改了文件，并提交到暂存区（即：编辑之后，进行git add 但没有 git commit -m "留言xxx"）
- 修改了文件，并提交到仓库区（即：编辑之后，进行git add 并且 git commit -m "留言xxx"）

如果是情况1：

```
git checkout -- aaa.html // 指定还原`aaa.html文件
git checkout -- * // 还原所有文件
```

如果是情况2：

```
git log --oneline      // 可以省略
git reset HEAD // 回退到当前版本
git checkout -- aaa.html
```

如果是情况3：

```
git log --oneline  // 可以省略``
git reset HEAD^   // 回退到上一个版本，注意看HEAD后面有个 ^HEAD^ 是回退到上个版本HEAD^^ 是回退到上上个版本HEAD~数字 是回退到数字个版本
git checkout -- aaa.html
```
