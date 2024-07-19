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
git add README.md 或者添加所有文档：git add . ，git status 命令可以查看在你上次提交之后是否有对文件进行再次修改。
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/qiuziba/devDoc.git
git push -u origin main

…or push an existing repository from the command line：

git remote add origin https://github.com/qiuziba/devDoc.git
git branch -M main
git push -u origin main
