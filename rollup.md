1、安装 rollup
npm install --save-dev rollup
npm install --save-dev rollup-plugin-terser
2、新建 rollup.config.js 配置文件：
import { terser } from "rollup-plugin-terser"; //代码压缩插件
export default {
input: "src/main.js", //入口文件
output: [
{
file: "dist/main.bundle.js", //输出文件格式
format: "cjs",
},
{
file: "dist/main.es.js", //输出文件格式
format: "es",
},
{
file: "dist/main.min.js", //输出文件格式
format: "iife",
name: "version",
Plugins: [terser()], //代码压缩插件
},
],
};
3、rollup 在 package.json 中配置
{
"name": "rollup",
"version": "1.0.0",
"main": "index.js",
"author": "",
"license": "ISC",
"description": "",
"scripts": {
"test": "echo \"Error: no test specified\" && exit 1",
"build": "rollup -c --environment INCLUEDE_DEPS,BUILD:production",
"dev": "rollup -c --environment INCLUEDE_DEPS,BUILD:development"
},
"devDependencies": {
"rollup": "^2.77.2",
"rollup-plugin-terser": "^7.0.2"
}
}
