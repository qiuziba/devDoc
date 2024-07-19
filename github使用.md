https://github.com/qiuziba/devDoc

1、登录 https://github.com/
2、建立建立项目 repository，如：devDoc
3、把 github.com 的 devDoc 项目克隆到本地：
git clone https://github.com/qiuziba/devDoc.git
4、git init
5、在本地新增文档：如 github 使用.md
6、提交到远程https://github.com/qiuziba/devDoc.git库中：

…or create a new repository on the command line

echo "# devDoc" >> README.md
git init
git add README.md 或者添加所有文档：git add .
git status 命令可以查看在你上次提交之后是否有对文件进行再次修改。
git commit -m "first commit"  
git commit -m "初始化仓库" 命令用于将当前编辑的文件提交到 Git 本地仓库中，并生成一个提交日志条目
git branch -M main
git branch -M main 命令用于将本地分支 main 重命名为 main。这个命令通常用于将本地分支 main 与远程分支 main 保持一致，
或者在创建新的本地分支时，需要将本地分支名称设置为 main。
git remote add origin https://github.com/qiuziba/devDoc.git 设置提交远程仓库的路径
git push -u origin main 提交到远程仓库
git push --all 本地所有分支都会传送到远程 git 文档库

…or push an existing repository from the command line：

git remote add origin https://github.com/qiuziba/devDoc.git
git branch -M main
git push -u origin main

7、本地删除一个文档，在没有提交的情况下恢复命令：
从 git 迁出文件：
git checkout github 使用.md
从 git 迁出所有文件：
git checkout .

8、切换到分支：
git branch main 或者 git checkout main
9、将远程文档库取回当前所在分支的最新数据：
git push
如果一次性取回全部分支最新的数据：
git push --all

========================git 常用命令的解释===============================================

解释 git add .

git add . 命令用于将当前目录下的所有文件添加到 Git 仓库的暂存区中。这个命令通常用于刚刚打开一个 Git 仓库时，或者用于将本地文件更新到远程仓库时。

具体来说，git add . 命令会将当前目录下的所有文件添加到 Git 仓库的暂存区中，并自动将这些文件的 Git 链接指向远程仓库中的相应文件。在添加文件时，git add . 命令也可以使用通配符来匹配多个文件，例如 git add \*.txt 命令将添加当前目录下所有扩展名为 .txt 的文件到 Git 仓库的暂存区中。

需要注意的是，git add . 命令会将当前目录下的所有文件添加到 Git 仓库的暂存区中，因此运行这个命令时需要小心，以免将重要的文件添加到暂存区中。如果不小心运行了 git add . 命令，可以使用 git reset 命令将暂存区中的文件撤销掉，或者使用 git checkout 命令将暂存区中的文件撤销掉并切换到本地文件。

解释 git commit -m "初始化仓库"
git commit -m "初始化仓库" 命令用于将当前编辑的文件提交到 Git 仓库中，并生成一个提交日志条目。在这个条目中，你可以添加一个描述性文本，例如 "初始化仓库",以便在以后查看提交日志时更好地理解这个提交的意义。

具体来说，git commit -m "初始化仓库" 命令会将当前编辑的文件打包成一个提交，并将其提交到 Git 仓库的暂存区中。这个提交是一个 Git 对象，可以将其提交到远程仓库或本地分支中。在提交时，-m 参数指定了提交日志条目的文本内容，这里使用了 -m 选项来指定日志条目文本，其中 "初始化仓库" 是文本内容，可以用单引号括起来，以避免被当做命令行参数处理。

需要注意的是，提交前需要确保所有需要提交的文件都已经添加到了 Git 仓库的暂存区中，并且没有任何冲突。如果有任何冲突，提交将会失败。在提交前，可以使用 git status 命令查看当前仓库的状态，并使用 git add 命令将需要提交的文件添加到暂存区中。

解释 git branch -M main
git branch -M main 命令用于将本地分支 main 重命名为 main。这个命令通常用于将本地分支 main 与远程分支 main 保持一致，或者在创建新的本地分支时，需要将本地分支名称设置为 main。

具体来说，git branch -M main 命令会将本地分支 main 重命名为 main,相当于在本地分支 main 上执行了一个 git branch 命令，这个命令会将当前分支名称设置为 main,并将本地分支 main 与远程分支 main 保持一致。

需要注意的是，git branch -M main 命令会将本地分支 main 的名称更改为 main,同时也会将本地分支 main 与远程分支 main 的名称保持一致。因此，在执行了这个命令后，本地分支 main 与远程分支 main 的名称已经一致，如果需要将本地分支 main 恢复为原始名称，可以使用 git branch -u 命令将本地分支 main 的链接重新指向远程分支 main,或者使用 git reset 命令将本地分支 main 恢复到原始状态。

解释 git remote add origin https://github.com/zyziga/Hexo.git
git remote add origin https://github.com/zyziga/Hexo.git 命令用于将远程分支 origin 添加到本地 Git 仓库中，并将其与远程分支 https://github.com/zyziga/Hexo.git 保持一致。这个命令通常用于将本地仓库与远程仓库进行链接，以便可以同步远程仓库的内容。

具体来说，git remote add origin https://github.com/zyziga/Hexo.git 命令会将远程分支 origin 添加到本地 Git 仓库中，并将其链接到远程分支 https://github.com/zyziga/Hexo.git。这个命令会将远程分支 https://github.com/zyziga/Hexo.git 的链接指向本地分支 master,也就是说，本地分支 master 与远程分支 https://github.com/zyziga/Hexo.git 的内容保持一致。

在执行了这个命令后，你可以通过 git fetch 命令来将远程仓库的内容下载到本地仓库中，并通过 git merge 或 git rebase 命令来与远程分支进行同步。需要注意的是，在同步远程分支时，需要确保本地分支与远程分支的名称相同，或者使用 git branch -u 命令将本地分支的链接指向远程分支。

详细点解释

git remote add 命令用于将远程分支添加到本地 Git 仓库中，并将其与远程分支保持一致。具体来说，这个命令会向本地 Git 仓库中添加一个远程链接，将该远程链接指向远程仓库中的特定分支。这个命令可以用于将本地仓库与远程仓库进行链接，以便可以同步远程仓库的内容。

在执行 git remote add 命令时，需要指定远程仓库的 URL 或用户名和密码，具体取决于你是否需要在本地验证远程链接。如果你需要验证远程链接，则需要输入远程仓库的用户名和密码。

在添加远程链接后，你可以使用 git fetch 命令将远程仓库的内容下载到本地仓库中，以便进行测试或合并。在下载远程仓库的内容时，git fetch 命令会获取远程仓库的最新内容，并将其与本地仓库中的现有内容进行比较。如果你发现本地仓库中的现有内容与远程仓库中的新内容不匹配，则可以使用 git merge 或 git rebase 命令来同步本地分支与远程分支。

如果你希望将本地分支与远程分支保持一致，可以使用 git branch -u 命令将本地分支的链接指向远程分支。例如，如果你希望在本地创建一个新的分支来追踪远程分支，可以使用以下命令:

git branch -u origin/master new_branch

这个命令会将本地分支 new_branch 的链接指向远程分支 origin/master,以便本地分支与远程分支保持一致。

解释 git push -u origin main
git push -u origin main 命令用于将本地分支 main 的更新推送到远程分支 origin/main。在这个命令中，-u 参数指定了推送的分支，origin/main 是远程分支的名称。

具体来说，git push -u origin main 命令会将本地分支 main 的最新更新推送到远程分支 origin/main,并将本地分支 main 与远程分支 origin/main 保持同步。这个命令相当于执行了 git push 命令，但是在这个命令中，-u 参数指定了推送的分支。

在执行了这个命令后，如果你在远程仓库中已经存在分支 origin/main,那么你需要确保本地分支 main 与远程分支 origin/main 的名称相同，或者使用 git branch -u 命令将本地分支 main 的链接指向远程分支 origin/main。如果你希望将本地分支 main 的名称与远程分支 origin/main 的名称不相同，可以使用 git branch -u 命令将本地分支 main 的链接指向远程分支 origin/main,并将本地分支 main 的名称更改为与远程分支 origin/main 的名称相同。

需要注意的是，在推送更新时，如果远程仓库中不存在本地分支 main,那么本地分支 main 的最新更新将直接推送到远程分支 origin/main。如果远程仓库中存在本地分支 main,则需要使用 git branch -u 命令将本地分支 main 的链接指向远程分支 origin/main,以便保持同步。

详细点解释

git push -u origin main 命令是将本地分支 main 的更新推送到远程分支 origin/main 的命令。在这个命令中，-u 参数指定了推送的分支，即本地分支 main 与远程分支 origin/main 保持同步。

具体来说，git push -u origin main 命令会将本地分支 main 的最新更新推送到远程分支 origin/main,并将本地分支 main 与远程分支 origin/main 保持同步。这个命令相当于执行了 git push 命令，但是这个命令中，-u 参数指定了推送的分支。

在执行了这个命令后，如果远程仓库中不存在本地分支 main,那么本地分支 main 的最新更新将直接推送到远程分支 origin/main。如果远程仓库中存在本地分支 main,则需要使用 git branch -u 命令将本地分支 main 的链接指向远程分支 origin/main,以便保持同步。

在推送更新时，git push 命令默认是将本地分支的最新更新推送到远程分支。但是，如果你使用了 -u 参数指定推送的分支，那么就需要确保本地分支与远程分支的名称相同，或者使用 -u 参数将本地分支的链接指向远程分支，以便保持同步。

需要注意的是，在推送更新时，如果远程仓库中存在本地分支，则需要使用 git branch -u 命令将本地分支的链接指向远程分支，以便保持同步。例如，如果你的本地分支 main 已经与远程分支 origin/main 同步，但你想在本地创建一个新的分支 new_main,并将该分支与远程分支 origin/main 保持同步，那么你可以使用以下命令:

git branch -u origin/main new_main

这个命令会将本地分支 new_main 的链接指向远程分支 origin/main,以便保持同步。
