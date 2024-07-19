// package.json

{
  "name": "vuex",  // 发布时必须。不得和现有npm包重名。可以通过"@xxx/vuex"加个范围。范围参见https://docs.npmjs.com/cli/v8/using-npm/scope。

  "version": "4.0.2",  // 发布时必须。

  "private": false,  // 是否私有。如果要发布公共包，这个值为false。它决定我们的项目是否会发布，如果设置为true，那么npm会拒绝发布。 

  "description": "state management for Vue.js",  // 包的简要描述。

  "keywords": ["vue", "vuex"],  // 关键字搜索，有助于搜索发现包。

  "homepage": "https://github.com/vuejs/vuex#readme",  // 包的主页url。

  "bugs": "https://github.com/vuejs/vuex/issues",  // 提issues的地址。项目问题反馈的url或报告问题的邮箱地址。

  "license": "MIT",  // 许可证。

  "author": "Nicholas C. Zakas",  // 作者。

  "maintainers": [  // 代码维护者（维护者数组），每个元素要包含name、email（可选）、web（可选）字段。
    {
      "name": "Bob",
      "url": "https://github.com/edhjb"
    }
  ],

  "contributors": [  // 代码贡献者（贡献者数组）。每个对象元素还可包含email字段等。
    {
      "name": "Boris Cherny",
      "url": "https://github.com/bcherny",
      "githubUsername": "bcherny"
    },
    {
      "name": "Lucian Buzzo",
      "url": "https://github.com/lucianbuzzo",
      "githubUsername": "lucianbuzzo"
    },
  ],

  "funding": {  // 捐赠地址。
    "type": "opencollective",
    "url": "https://opencollective.com/typescript-eslint"
  },

  /*
    将包作为依赖，安装到本地时，包含的内容。有一些不指定，也总会包含进去，如package.json，README，LICENSE/LICENCE。
    本文件中main字段引用的文件，有些不指定，总会被排除.npmrc，node_modules。
    files优先级较高，不能通过.npmignore和.gitignore排除掉。
  */
  "files": [
    "dist",
    "types/index.d.ts",
    "types/helpers.d.ts",
    "types/logger.d.ts",
    "types/vue.d.ts"
  ],

  "main": "dist/vuex.cjs.js",  // cjs模块引用的入口，执行require("vuex")时调用。

  "browser": "dist/vuex.esm-browser.js",  // 浏览器端使用。即如果要在客户端使用模块，则应使用browser字段来代替main字段。

  "bin": {  // 可执行文件路径，他们会被添加到环境变量的PATH中。在控制台运行>vite 命令时调用。
    "vite": "bin/vite.js"
  },

  "man": "" /*或者*/ [],  // 制定一个或通过数组制定一些文件来让linux下的man命令查找文档地址。

  "directories": {  // 用来标识模块结构的方法，类似于commonjs包规范的介绍，想查看npm中的package.json，就可以看到doc、lib、man目录及位置。
    "bin": "./bin",
    "doc": "./doc",
    "lib": "./lib",
    "man": "./man"
  },

  "repository": {  // 代码仓库所在位置。
    "type": "git",
    "url": "git+https://github.com/vuejs/vuex.git"
  },

  "scripts": {  // 执行脚本命令。
    "dev": "vite",
    "build": "vue-tsc --noEmit && vite build",
    "test": "vue-tsc --noEmit && vite build --mode test",
    "preview": "vite preview"
  },

  "config": {  // 用于添加命令行的环境变量。
    "port": 8800
  }

  "dependencies": {  // 生产环境依赖的包。不要把开发环境的包放到此处，比如eslint，babel，typescript，sass等。
    "echarts": "5.3.0",  // 版本严格匹配。安装时，会准确的安装5.3.0版本。参见 https://github.com/npm/node-semver#versions。
    "moment": ">2.29.1",  // 安装大于2.29.1的包，比如2.29.2，2.30.0，3.0.0。参见https://github.com/npm/node-semver#versions。
    "normalize.css": "~8.0.1",  // 版本大于等于8.0.1可以，但是要小于8.1.x。
    "element-plus": "^2.2.13",  // 版本大于等于2.2.13可以，但是要小于第一个非0的数字加1。即3.x.x。比如^1.2.3，则需<2.0.0，比如^0.2.3，则需<0.3.0，又比如0.0.3，则需<0.0.4。
  },

  "devDependencies": {  // 仅仅在开发中依赖的包，在打包时，不会被打进去的模块。
    "@babel/core": "^7.12.16",
    "@babel/eslint-parser": "^7.12.16",
    "@vue/cli-service": "~5.0.0",
    "eslint-config-prettier": "^8.3.0",
    "sass": "^1.32.7",
    "sass-loader": "^12.0.0",
  },

  /*
    如果当前包依赖某个包，那么当当前包被安装时，依赖的那个包也一并安装。
    对等依赖：描述的是一种表达插件与其宿主包之间的“依赖关系”。某种说法，“我只在插入我的主机包的1.2.x版时才能工作，所以如果你安装我，请确保它与兼容主机一起使用”。
    比如在element-plus（需在vue框架下使用）中，要求项目的vue版本在3.1.x版本以上，如果我们安装vue2.x的版本，element-plus就不会安装成功。
  */
  "peerDependencies": {
    "vue": "3.2.31",
    "less": "*",
    "sass": "*",
    "stylus": "*"
  },

  /*
    当用户安装您的包时，如果尚未安装peerDependencies中指定的包，npm将发出警告。
    peerDependenciesMeta字段用于向npm提供有关如何使用对等依赖项的更多信息。
    具体来说，它允许将对等依赖项标记为可选。
    如下所示：如果项目中没有安装sass，stylus或less，由于对等依赖项标记为可选，所以不会发出警告。否则将会发出警告。
  */
  "peerDependenciesMeta": {
    "sass": {
      "optional": true
    },
    "stylus": {
      "optional": true
    },
    "less": {
      "optional": true
    }
  },

  /*
    捆绑依赖，在"npm pack"打包成tgz时将会捆绑依赖一同打包。
    可以将"bundleDependencies"定义为布尔值。true的值将捆绑所有依赖项（dependencies属性值），false的值将捆绑无。
  */
  "bundleDependencies": ["elementui", "echarts"] /*或者*/ true/false,

  /*
    如果出现包找不到或者安装失败时，但又不影响npm继续运行，可将该包放在optionalDependencies对象中而不是dependencies中。
    表示的是定义的模块如果安装失败，不会在输入npm install时失败。
  */
  "optionalDependencies": {
    "echarts": "^4.9.0"
  },

  "engines": {  // 推荐的node和npm版本，如果不匹配也不会报错，只是建议满足版本。
    "node": ">=0.10.3 <15",
    "npm": "~1.0.20"
  },

  "os": ["darwin", "linux"],  // 指定模块运行在指定操作系统上。

  "cpu": ["x64", "ia32"],  // 如果代码仅在某些cpu架构上运行，则可以指定哪些架构。

  // 在npm包发布时使用的配置，是一个对象，我们可以在里面设置tag(标记)，registry（仓库地址），access（访问权限）
  "publishConfig": {
    "tag": "1.0.0",
    "registry": "https://registry.npmjs.org/",
    "access": "public"
  },

  // esm引用时的入口，执行import vuex from "vuex"时调用。注意此字段不是规范，但是却被rollup和webpack大量使用，未来极有可能成为规范。
  "module": "dist/vuex.esm-bundler.js",

  "exports": {  // 导出声明。在导入模块和子模块时，会使用不同的路径。
    ".": {
      "require": "./dist/vuex.cjs.js",  // 使用require时导入。
      "import": "./dist/vuex.mjs",  // 使用import时导入。
      "browser": "./dist/vuex.umd.js",  // 浏览器端使用导入。
      "types": "./dist/types/vuex.d.ts",  // ts环境使用。
    },
    ".": "./dist/vuex.umd.js",  // import "vuex"时，会加载vuex/dist/vuex.umd.js路径文件。
    "./sub/path": "./secondary.js",  // import "vuex/sub/path"时，会加载vuex/secondary.js路径文件。
  },

  "unpkg": "dist/vuex.global.js",  // CDN服务地址。
  "jsdelivr": "dist/vuex.global.js",  // CDN服务地址。
  /*
    unpkg VS jsdelivr：
        相同点：这两个字段都是做cdn优化服务的。
        不同点：
            1、unpkg适用于npm上的所有内容。使用它可以使用URL快速轻松地从任何包加载任何文件。
            2、jsdelivr可以访问npm，github, wordpress上面所有的包。
  */

  "typings": "types/index.d.ts",  // 定义typescript声明文件的地址。
}

/*
下载的依赖保存在项目的node_modules目录下。
这个目录无需随着项目代码上传至git。即使该目录删除了也无所谓。
只要有package.json文件即可。此时使用命令"npm install"就会将package.json文件中记录的所有依赖全部下载到本地node_modules目录下。
*/
