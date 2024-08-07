一、使用 npx 构建 react、typescript、next.js 项目
1、构建 react app 项目脚手架：
npm install -g create-react-app 或者 yarn global add create-react-app 安装创建 react 项目命令
npx create-react-app my-react-app ,其中：my-react-app 项目名称
2、构建 react-typescript app 项目脚手架：
npx create-react-app react-ts-app --template typescript ,其中：react-ts-app 项目名称
3、npx 创建 nextJS 项目，并支持 typescript
npm install -g create-next-app 或者 yarn global add create-next-app ，安装创建 next 项目命令
npx create-next-app next-app ，创建 next 项目，其中 next-app 项目名称
npx create-next-app next-ts-app --typescript ,创建 next + typescript 项目 其中 next-ts-app 项目名称
npm run dev

二、yarn 管理 nextjs 项目，例子
预备环境
nodejs
npm 1. yarn 安装
npm install -g yarn 2. nextjs 项目初始化
yarn add next react react-dom 3. 配置 nextjs 项目
"scripts":{
"dev": "next",
"build": "next build",
"start": "next start"
} 4. 创建简单项目
a、创建目录: mkdir pages
cd pages
b、新增文件: index.js
// content
export default ()=> <div>this is the index page </div>

    5。run
    yarn run build
    yarn run dev
