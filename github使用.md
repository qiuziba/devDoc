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
