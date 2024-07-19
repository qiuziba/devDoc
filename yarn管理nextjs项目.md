一、yarn 管理nextjs 项目
    预备环境
    nodejs 
    npm
    1. yarn 安装
    npm  install -g yarn 
    2. nextjs 项目初始化
    yarn add  next react  react-dom
    3. 配置nextjs 项目
    "scripts":{
        "dev": "next",
        "build": "next build",
        "start": "next start"
      }
    4. 创建简单项目
    a、创建目录: mkdir pages
      cd pages 
    b、新增文件: index.js 
    // content 
    export default ()=> <div>this is the index page </div>
    
    5。run 
    yarn run build 
    yarn run dev

二、yarn 直接创建nextJS项目

npm install -g create-next-app
create-next-app my-next-app
或者
yarn global add create-next-app
create-next-app my-next-app

三、npx创建nextJS项目
npx create-next-app@latest   =》 提示录入项目名称：nextjs-demo
或者直接下命令行写入项目名称：
npx create-next-app@latest nextjs-demo

yarn create next-app 这个命令会报错，不知道为什么
