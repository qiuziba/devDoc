### nodejs的安装及配置（适用于windows）
下载 TLS 稳定版本，然后一直按默认安装即可
## 安装完后测试
输入cmd，进入终端，然后输入 node -v 和 npm -v      ### 显示node版本号
## nodejs配置环境
在nodejs根目录内新建两个文件夹 node_global 和 node_cache 
# 设置全局安装路径
npm config set prefix "C:\Program Files\nodejs\node_global"
# 设置缓存路径
npm config set cache "C:\Program Files\nodejs\node_cache"
# 设置淘宝镜像 (2026 年最新源)
npm config set registry https://registry.npmmirror.com
# 验证是否设置成功
npm config get registry
# 输出应为：https://registry.npmmirror.com/

# 我的电脑”-右键-“属性”-“高级系统设置”-“高级”-“环境变量”
# 点击 "环境变量"，在 "系统变量" 中找到 Path，选中并点击 "编辑"
# 添加你的全局包路径
C:\Program Files\nodejs\node_global （你的自定义全局包路径）
# 全局包路径在安装路径全面，确保新的路径排在前面 
C:\Program Files\nodejs （Node.js 安装路径）
### 安装成功并设置好环境后，再次测试
# 以管理员身份打开命令提示符：
  按 Win 键，输入 cmd 或 命令提示符
  右键点击，选择"以管理员身份运行"
# 1. 再次验证版本
node -v
npm -v

# 2. 测试全局安装 (以安装 vite 为例)
npm install -g vite

# 3. 验证命令是否可用
vite -v