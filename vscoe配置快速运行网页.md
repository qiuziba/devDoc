
### 快速运行网页的几种方式
### 方法一：使用 VS Code Live Server（最简单）
如果你只是要预览 HTML/CSS 页面，不需要后端：

安装插件：

在 VS Code 扩展商店搜索 Live Server

安装作者是 Ritwick Dey 的版本

启动服务器：

打开你的 index.html

右键点击编辑器空白处

选择 "Open with Live Server"

或者点击右下角的 "Go Live" 按钮

自动打开浏览器：

页面会在 http://127.0.0.1:5500 自动打开

保存代码后会自动刷新

### 方法二：使用 Vite 开发服务器（推荐，支持 Tailwind）
如果你使用 React/Vue 或需要热更新：

bash
# 1. 如果是新项目，创建 Vite 项目
npm create vite@latest my-project -- --template react
# 或 vue

# 2. 进入项目并安装依赖
cd my-project
npm install

# 3. 安装 Tailwind CSS（如果需要）
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p

# 4. 启动开发服务器
npm run dev
你会看到类似这样的输出：

text
  VITE v5.0.0  ready in 300 ms

  ➜  Local:   http://localhost:5173/
  ➜  Network: use --host to expose
方法三：使用简单的 HTTP 服务器
如果只是临时需要：

bash
# 全局安装 http-server（需要 Node.js）
npm install -g http-server

# 在项目目录运行
http-server

# 或使用 Python（无需安装）
python -m http.server 8000
📁 如果你已经有 HTML 文件
假设你的项目结构是这样的：

text
my-project/
├── index.html
├── styles.css (或 Tailwind 编译后的 CSS)
└── script.js
方案 A：使用 Live Server（推荐）
VS Code 中打开 index.html

右键 → "Open with Live Server"

浏览器自动打开

方案 B：双击 HTML 文件（不推荐）
直接双击 index.html 会在浏览器打开

缺点：某些功能可能受限（如跨域请求、模块导入）

🎨 如果使用 Tailwind CSS
确保你的 HTML 引用了 Tailwind CSS：

html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>我的 Tailwind 项目</title>
    <!-- 引用 Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- 或使用本地编译的 CSS -->
    <!-- <link href="/dist/output.css" rel="stylesheet"> -->
</head>
<body>
    <div class="text-4xl font-bold text-blue-600">
        Hello Tailwind!
    </div>
</body>
</html>
🚦 调试技巧
查看控制台日志
浏览器：按 F12 或 Ctrl+Shift+I

查看 Console 标签：看是否有 JavaScript 错误

查看 Network 标签：检查资源是否加载成功

热更新配置
如果修改代码后页面不自动刷新：

确认保存了文件（Ctrl+S）

检查浏览器是否自动刷新

Live Server 通常会自动刷新

Vite 开发服务器也会热更新

📝 根据你之前的操作推测
看到你之前在 D:\project\MyDocWork\devDoc 目录操作 Git，推测你可能：

已有 HTML 项目：

在 VS Code 中打开该文件夹

用 Live Server 运行 index.html

新项目要开发：

使用 Vite 创建项目

启动开发服务器