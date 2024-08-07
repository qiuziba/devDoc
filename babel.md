一、安装 javascipt 编译器 babel
1、全局安装 babel：
npm install -g babel babel-cli --force

2、项目安装 babel 核心库
npm install --save-dev @babel/core @babel/cli @babel/preset-env

3、项目根目录创建 babel 配置文件，来指定转换规则和选项:
a、.babelrc：JSON 格式的配置文件，通常用于配置针对特定目录及其子目录的 Babel 设置。
b、babel.config.js：JavaScript 格式的配置文件，支持编程化配置，适用于整个项目范围的 Babel 配置。
c、package.json 中的 babel 字段：在 package.json 文件中嵌入 Babel 配置，适用于简单项目。

4、安装 babel 插件，
npm install --save-dev @babel/plugin-transform-arrow-functions //将 ES6 转换成 ES5
npm install --save-dev @babel/plugin-proposal-object-rest-spread //将 转换语法"对象扩展"
npm install --save-dev @babel/plugin-proposal-class-properties //将 转换语法"类属性"

5、Babel 拥有丰富的生态系统和工具链，提供各种插件、预设和工具。例如：
@babel/cli：Babel 的命令行工具，用于在终端中运行 Babel 转换。
@babel/node：基于 Babel 的 Node.js 运行时，可以直接运行转换后的代码。
@babel/register：通过钩子函数实现实时编译，便于在开发环境中使用。

6、babel 编译目标文件
npx babel src --out-dir lib --extensions ".ts"
终端执行命令：babel
源目录：src
指定输出目录参数：--out-dir
输出目录:lib
指定编译文件后缀参数：--extensions
指定文件后缀：".ts"
7、babel 在 package.json 中配置
{
"name": "bable-ts",
"version": "1.0.0",
"main": "index.js",
"directories": {
"lib": "lib"
},
"scripts": {
"test": "echo \"Error: no test specified\" && exit 1",
"babel": "npx babel src --out-dir lib --extensions \".ts"
},
"author": "",
"license": "ISC",
"description": "",
"devDependencies": {
"@babel/cli": "^7.14.8",
"@babel/core": "^7.15.0",
"@babel/plugin-proposal-class-properties": "^7.14.5",
"@babel/plugin-proposal-object-rest-spread": "^7.14.7",
"@babel/plugin-transform-arrow-functions": "^7.14.5",
"@babel/preset-env": "^7.15.0",
"@babel/preset-typescript": "^7.15.0"
}
}

============================详解文章======================================================
babel 的配置使用详解

Babel 是一个工具链，主要用于将采用 ECMAScript 2015+ 语法编写的代码转换为向后兼容的 JavaScript 语法，以便能够运行在当前和旧版本的浏览器或其他环境中。Babel 能做的事情：

语法转换
通过 Polyfill 方式在目标环境中添加缺失的特性（通过第三方 polyfill 模块，例如 core-js，实现）
源码转换 (codemods)
核心依赖包
@babel/core：babel 转译器本身，提供了 babel 的转译 API，如 babel.transform 等，用于对代码进行转译。webpack 的 babel-loader 就是调用这些 API 来完成转译过程的。
@babel/parse：JS 解释器模块内容。提供 parse 接口解释，最新的 ECMASCRIPT 标准，以及 JSX，Flow，TypeScript，和其他实验性语言。这个模块便是以前的 babylon。
@babel/traverse：JS 遍历 AST 节点模块。用于遍历解释器模块解析出来的 AST 节点。
@babel/generator：JS 生成器，主要用于将解释器解释得到的 AST 生成成为可解析的 JS 代码。
babel 在解析文件倒得出可运行 JS 文件的一个过程：

input string -> @babel/parser parser -> AST -> transformer[s] -> AST -> @babel/generator -> output string

其他功能包：

@babel/cli：命令行工具，cmd 运行 babel 解析过程。并可以设置包括输出路径等等信息。
@babel/types：用于验证，构建，和修改 AST 节点。
@babel/polyfill：包装了 core-js 和 regenerate-runtime。
@babel/runtime：和 polyfill 相似，但是不会修饰全局环境将会和 plugin-transform-runtime 一同使用。
@babel/registor：通过使用 node.js 的 require 字段来引入。会自动的通过 babel 解析当前文件。
引入
使用 babel-cli

首先我们需要下载 babel-cli。本地安装会更好一些。我们可以通过 shell 命令来进行下载。

npm install --D @babel/core @babel/preset-env @babel/cli
其中@babel/core 是 babel 的核心库；preset-env 是帮助我们转义最新的 javascript 语法内容。

什么是 preset？

preset 是 babel 预设的一连串的 plugins。用于专门处理某一方面的问题，并不需要用户在一个个的导入 plugins。从而方便开发。
如果 babel^7 的版本，我们下载包的时候不再是和之前使用 babel-XXX 的形势了。而是如上面例子一样使用 @babel/XXX 的形势，一定要注意版本问题。

当下载好了相应的内容并写好了相关的代码的时候，我们可以通过 cli 来进行编译工作了。命令如下

// src 表示的是你要编辑的内容的位置（文件夹，或者是 js 文件）。lib 表示的是编译好之后的内容将会放在什么目录下。
babel src -d lib
也可以再 package.json 之中配置 script 属性。例如：

"script":{
"build" : "babel src -d lib"
}
在编译之前要记得配置好.babelrc 文件内容。因为 babel 编译的时候将会以.babelrc 之中的设置为准。

在使用 babel 中想减少代码，就需要引入 babel 的运行时：

npm install --save-dev @babel/plugin-transform-runtime
npm install --save @babel/runtime
需要注意的是：

两个包引入的范围不一样：一个在开发时引入，一个在运行时引入。
plugin-transform-runtime 已经默认包括了 @babel/polyfill，因此不用在独立引入。
在 plugin-transform-runtime 中有一个 corejs 可以设置成 false 或者 2。corejs 是一个给低版本的浏览器提供接口的库，如 Promise, map, set 等。

设置成 false 或者不设置：是引入的是 corejs 中的库，而且在全局中引入，也就是说侵入了全局的变量。可以观察以下的代码：

// 这是你写的代码
function sleep(ms) {
return new Promise((resolve, reject) => {
setTimeout(() => {
resolve()
}, ms)
})
}
// babel 编绎成的代码
"use strict";

require("core-js/modules/es6.promise"); // 这里可以看出是全局引入

function sleep(ms) {
return new Promise(function (resolve, reject) {
setTimeout(function () {
resolve();
}, ms);
});
}
把 corejs 设置成 2：如果你的全局有一个引入，不要让引入的库影响全局，编绎成的代码：

"use strict";

var \_interopRequireDefault = require("@babel/runtime-corejs2/helpers/interopRequireDefault");

var \_promise = \_interopRequireDefault(require("@babel/runtime-corejs2/core-js/promise")); // 独立变量

function sleep(ms) {
return new \_promise.default(function (resolve, reject) {
setTimeout(function () {
resolve();
}, ms);
});
}
可以从编绎出的代码看到，promise 代码变成了一个独立的变量 \_promise，不会影响全局的 Promise。这样的好处是，引入的库者自己引入了一个变量，这样如果你引入的第三方库会对 Promise 进行一些自定义操作，这样的功能可以避免第三方库报错。

如果你设置了 corejs2，那你就需要加入下面的库:

npm install @babel/runtime-corejs2
使用 webpack

使用 webpack 主要进行管理和打包工作。也有专门的针对 webpack 环境下的 babel 使用

webpack 之中常常可以运用到许多的 loader 来方便我们的开发。而 babel 也可以通过 webpack 的 loader 来进行引入和使用。但是单单引入 babel-loader，是不可行的，绝对要记得 babel-core 也需要一并视同 npm 下载到本地，否则要报错的哟（始终要记得 babel-core 是 babel 的核心库，所有的解析方面的核心内容都是在这个包之中。）还有就是一些必要的预设和插件，具体命令可使用如下：

npm install babel-loader@8.0.0-beta.0 @babel/core @babel/preset-env webpack
上面这一行代码是将 babel 的 7.x 的版本进行引入，如果需要使用 6.x 的版本的话可以运行如下代码。

npm install babel-loader babel-core babel-preset-env webpack
当下在好我们的依赖包之后，我们可以通过.babelrc 文件来进行配置，或者我们也可以通过 webpack.config.js 来进行配置。

module: {
rules: [
{
test: /\.js$/,
exclude: /(node_modules|bower_components)/,
use: {
loader: 'babel-loader',
options: {
presets:[['@babel/preset-env',{
	      debug:true
            // 我们不能使用module的配置关键字，因为如果此处传入了这一参数内容webpack在打包编译的时候将会错误。
	  }]]

        }
      }
    }

]
}
上图可见：将会在 module 之中的 rules 中对 babel-loader 进行配置。rules 是 webpack 专门用于配置 loader 的一个属性。我们在配置 babel-loader 的时候，可以通过关键参数的配置来确定当前的 babel 的运行基准。

options 之中可以传递的参数内容:

cacheDirectory：默认的值是 false， 当有设置值的时候，指定的目录将会用来缓存 loader 的执行结果。之后 webpack 将会尝试读取缓存，来避免高消耗的 babel 的重新编译过层。如果设置了一个空值 (loader: 'babel-loader?cacheDirectory')或者 true (loader: babel-loader?cacheDirectory=true)，loader 将使用默认的缓存目录 node_modules/.cache/babel-loader，如果在任何根目录下都没有找到 node_modules 目录，将会降级回退到操作系统默认的临时文件目录。
cacheIdentifier：默认是一个由 babel-core 版本号，babel-loader 版本号，.babelrc 文件内容（存在的情况下），环境变量 BABEL_ENV 的值（没有时降级到 NODE_ENV）组成的字符串。可以设置为一个自定义的值，在 identifier 改变后，强制缓存失效。
forceEnv：默认将解析 BABEL_ENV 然后是 NODE_ENV。允许你在 loader 级别上覆盖 BABEL_ENV/NODE_ENV。对有不同 babel 配置的，客户端和服务端同构应用非常有用。
在我们的 webpack.config.js 之中如果有相关的配置了之后，我们实际上可以不用再另外的编写.babelrc 文件来再去确定当前的 babel 的配置的。

babelrc 配置
在我们使用 babel 的时候常常可以看到如影随形的.babelrc 文件内容。他主要是用来配置我们的 babel 在编译 JS 的时候需要使用到的相关的插件或者其他的设置的，十分的重要，babel 配置也可以在 package.json 之中直接的编写，使用 babel 关键字就可以了。

.babelrc 主要是为了配置 preset 和 plugins 内容项

preset ：预设

在配置文件之中我们可以先添加我们需要的预设环境。当然添加在配置文件之中的 preset 需要下载到本地。这样配置之后才会生效。我们先来简单的编写一段配置，然后慢慢的填充的方式来学习怎么对 babel 进行配置。先看原始数据。

{
"presets": ["@babel/preset-env"]
}
上面表示的是引用 preset-env 预设。当然我们可以对当前的引入的预设添加带参设置。例如

{
"presets": [
["@babel/preset-env", options]
]
}
其中的 options 可以有许多的关键字段，其中一个 options 是一个对象内容，当然依据不同的 preset 和 plugins 会提供不太相同的 options 的字段进行设置，这里我们是使用了 preset-env 预设所以暂时只介绍相关的字段，具体的 options 信息请点击这里查看。其中主要可用字段是有：

targets:

String | Array | { [String]: string } 。默认为{}，这一属性说明了当前的项目的适用环境。可以编写字符串的内容，作为 boswerlist 的遍历条件。例如："targets": "> 0.25%, not dead" 或者也可以使一个对象。来设置对于每一个浏览器最低版本的控制。例如：{ "targets": { "chrome": "58", "ie": "11" } }，其中的浏览器关键字从如下之中选取：chrome, opera, edge, firefox, safari, ie, ios, android, node, electron。
targets.esmodules

布尔值，是 targets 属性对象之中的一个值，其表示的是是否开启 ES 模式。可以和 type='module'结合是用，来简化脚本。当检查到当前的属性的时候，targets 之中的浏览器属性设置将会被无视。
module

其可以取值是："amd" | "umd" | "systemjs" | "commonjs" | "cjs" | "auto" | false 默认值是 false。将当前的 ES 编译模式转化成为其他的语法模式，其中的 cjs 是 commonjs 的别名。
debug

布尔值，默认是 false。将当前版本号和环境输出到控制台。
include

Array<String|RegExp>。这一属性表示的是永远包含的插件内容。当然输入的字符串内容是有一定规范的。要么是全名输入，或者可以使用\*号表示，某一目录下所有的内容，或者是使用正则表达式的形势匹配需要引入的插件内容。
exclude

同 include 相同，不过它表示的是需要排除或者移除的插件内容。
useBuiltIns

"usage" | "entry" | false 三个值之一，这一属性确定 preset-env 如何处理 polyfills。
useBuiltIns：false：此时不对 polyfill 做操作。如果引入 @babel/polyfill，则无视配置的浏览器兼容，引入所有的 polyfill。

useBuiltIns：entry：根据配置的浏览器兼容，引入浏览器不兼容的 polyfill。需要在入口文件手动添加 import '@babel/polyfill'，会自动根据 browserslist 替换成浏览器不兼容的所有 polyfill。

"useBuiltIns": "entry",
"corejs": 2,
这里需要指定 core-js 的版本, 如果 "corejs": 3, 则 import '@babel/polyfill' 需要改成

import 'core-js/stable';
import 'regenerator-runtime/runtime';
usage：usage 会根据配置的浏览器兼容，以及你代码中用到的 API 来进行 polyfill，实现了按需添加。

"useBuiltIns": "usage",
"corejs": 2,
当然还有其他的属性字段，具体使用的时候可以查询官方文档，这里只是为了说明所以以 preset-env 作为例子。以上字段是 preset-env 所有的设置字段，其他预设不一定有哟需要注意这一点。

stage

stage-0 - Strawman: just an idea, possible Babel plugin.
stage-1 - Proposal: this is worth working on.
stage-2 - Draft: initial spec.
stage-3 - Candidate: complete spec and initial browser implementations.
stage-4 - Finished: will be added to the next yearly release.
plugins

在设置文件之中我们也可以引入 plugins（插件内容）。常见内容也和 preset 的是相通的，只是引入属性的关键字变成了 plugins。当然每个插件也有自己的属性字段可以设置咯。

{
"plugins": ["pluginA", ["pluginA"], ["pluginA", {}]]
}
//要指定参数，请传递一个以参数名作为键（key）的对象
{
"plugins": [
[
"transform-async-to-module-method",
{
"module": "bluebird",
"method": "coroutine"
}
]
]
}
插件开发：

// 一个简单的用于反转名称顺序的插件
export default function() {
return {
visitor: {
Identifier(path) {
const name = path.node.name;
// reverse the name: JavaScript -> tpircSavaJ
path.node.name = name
.split("")
.reverse()
.join("");
},
},
};
}
插件和 Presets 执行顺序：

插件在 Presets 前运行。
插件顺序从前往后排列。
Preset 顺序是颠倒的（从后往前）。
ignore

忽视文件属性配置。注意不能忽略 nodemodule 包中的包文件。例如：

{
ignore：[
index.js //当前文件将会被 babel 忽略编译。
]
}
如果要忽略 node_modules 的文件 ，需要找到 webpack 的配置文件，进行如下配置

{
test: /\.js$/,
exclude: [ resolveByProjectRoot('node_modules/aa')],
use: [
threadLoader,
{
loader: require.resolve('babel-loader'),
options: {
cacheDirectory: true,
extends: resolveBabelrc()
}
}
]
}
minified

用于设置编译后是否压缩，当使用 cli 的进行打包配置的时候将会产生效果，但是如果使用其他的架构引入 babel 的话，当前配置可能会无效果。

comments

布尔类型，表示打包编译之后不产生注释内容。在 webpack 之中使用 UglifyJsPlugin 插件也是一样的效果。

env

设置对应环境下的配置。其可设置方式是在文件的最外层给定对象的关键字，并使用环境设置作为对象属性关键字，并在属性对象之中进行当前环境下的内容配置。这么说可能不太清楚，看一下如下例子：

{
"env": {
// test 是提前设置的环境变量，如果没有设置 BABEL_ENV 则使用 NODE_ENV，如果都没有设置默认就是 development
"test": {
"presets": ["env", "stage-2"],
// instanbul 是一个用来测试转码后代码的工具
"plugins": ["istanbul"]
}
}
}
在打包编译的时候，env 的值将会从 process.env.BABEL_ENV 之中获取，如果没有，则将会获取 pocess.env.NODE_ENV，如果还是没有信息的话，将会默认是 development。
