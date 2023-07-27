# git 

~~~ bash
# 设置用户签名
git config --global user.name "用户名" 
git config --global user.email "邮箱"
# 初始化本地库
git init
# 查看本地库状态
git status
# 添加到暂存区
git add <文件或目录>
# 提交到本地库
git commit -m "版本信息" <文件或目录>
# 查看当前结点及父节点以及操作日志
git reflog
# 查看当前结点及父节点的详细描述
git log --all
# 版本回退 (会直接影响到工作区)
git reset --hard <版本号>
# 删除提交的文件
git rm <文件>
~~~

- **分支操作**

~~~bash
# 创建分支
git branch 分支名
# 查看本地分支
git branch
# 查看所有分支
git branch -a
# 查看分支加详细信息
git branch -v
# 切换分支
git checkout <分支名>
# 把指定分支合并到当前分支
git merge <分支名>
~~~

- **远程仓库**

~~~bash
# 与远程仓库建立关联的方式（1）强烈建议这种方式
git clone <远程仓库地址>
# 与远程仓库建立关联的方式（2）
git remote add origin <远程仓库地址>
# 将本地的分支版本上传到远程并合并
git push origin <本地分支名>:<远程分支名>
# 如果本地分支名与远程分支名相同，则可以省略冒号：
git push origin <本地分支名>
# 删除远程的分支可以使用 --delete 参数
git push origin --delete <远程分支名称>
# 会将功能分支上的所有提交（commit）合并为一个新的提交添加到主分支，
# 而不是将每个提交都添加到主分支的历史记录中，好处是使主分支上的提交历史井然有序
git merge --squash <待合并的分支>
# 将本地分支推送到远程仓库并与远程分支关联(远程分支没有就自动创建一个远程分支)
git push --set-upstream origin <本地分支>
# git pull 命令用于从远程获取代码并合并本地的版本  
git pull <远程主机名> <远程分支名>:<本地分支名>
# 如：将远程主机 origin 的 master 分支拉取过来，与本地的 brantest 分支合并
git pull origin master:brantest
# 将远程分支与当前分支合并
git pull origin <远程分支名称>
~~~

## 一般工作流程示例

### 从创建远程仓库开始

现在 GitHub 或 GitLab 上创建远程仓库。

这里我在 GitHub 上创建了一个名为 My-Git-Notes 的仓库

~~~bash
# 先将仓库拷贝下来
git clone https://github.com/CritialThinking/My-Git-Notes.git
# 在本地创建分支(如果使用 Jira 进行项目管理的话，一般分支名为：姓名拼音/Jira task id)
git branch critical_thinking/addNotes
# 切换到该分支
git checkout critical_thinking/addNotes

# 在工作区进行修改。。。

# 提交修改
git commit -m "添加笔记"

# 将本地分支提交到远程仓库
git push --set-upstream origin critical_thinking/addNotes

# 在远程仓库提交 merge request
~~~

## 参考链接

[How to Solve Squash Failed on GitLab (wellosoft.net)](https://blog.wellosoft.net/how-to-solve-squash-failed-on-gitlab)
