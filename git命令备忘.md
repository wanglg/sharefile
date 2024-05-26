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

git不使用代理 git config –global –unset http.proxy 

使用git访问github服务器时，若使用代理服务器，需要在git的配置文件中添加代理服务器IP+端口，让git可以正确解析URL。若SSL证书非第三方机构签署，git提示OpenSSL错误时，可以添加临时SSL证书

配置git代理 git config --global  http.proxy http://127.0.0.1:1087  

git config --global  https.proxy http://127.0.0.1:1087

端口号为代理软件配置端口号

查看当前用户的git配置 git config --global --list  

查看系统配置 git config --system --list

查看当前仓库配置 git config --local --list

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

## git reset revert checkout

- Reset

```
git reset --hard commitId 重置到某个提交ID
reset 后可接三个参数
–soft – 缓存区和工作目录都不会被改变
–mixed (默认选项) 缓存区和你指定的提交同步，但工作目录不受影响
–hard – 缓存区和工作目录都同步到你指定的提交
git reset --hard origin/master  # 将本地的状态回退到和远程的一样
```

- revert

  ```
  通过创建一次新的 commit 来撤销一次 commit 所做出的修改。这种撤销的方式是安全的，因为它并不修改 commitm history。
  git revert commitId 还原某次提交
  ```

  

- Checkout

  ```
  基于指定 commit id 创建分支
  
  # 切换到指定提交记录
  git checkout <commit id>
  # 创建并切换到新分支
  git checkout -b <branch>
  
  # 检出某一次标签
  git checkout tagname
  ```

  