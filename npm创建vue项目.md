### 安装 Vue 官方脚手架 (Vue CLI)
npm install -g @vue/cli
### 安装完成后，输入以下命令验证是否成功
vue --version 或者 vue -V
### 创建并运行 Vue 项目
vue create my-vue-project

## vs code 终端 以管理员身份运行 npm install -g @vue/cli ，报错
vue create myvue3
vue : 无法加载文件 C:\Program Files\nodejs\node_global\vue.ps1，因为在此系统上禁止运行脚本。有关详细信息，请参阅 https:/go.microsoft.com/fwlink/?LinkID=135170 中的 about_Execution_Policies。
所在位置 行:1 字符: 1
+ vue create myvue3
+ ~~~
    + CategoryInfo          : SecurityError: (:) []，PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess

## 解决问题 ，在vs code 终端下运行，按当前管理员用户运行  
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser     