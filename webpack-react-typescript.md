一、webpack 配置文件 webpack.config.js，核心概念介绍如下
1、入口(Entry)：配置应用程序一个或者多个入口，如：./src/index.js
2、出口(Output): 文件输出位置，如：/dist/main.js
3、Loader:加载其它类型的文件，转换成有效的模块供应用程序使用
4、插件:配置要不同的插件，完成不同的任务
5、模式:开发模式、生产模式、没有；对应参数：development、production、none
6、浏览器兼容: webpack 支持所有 ES5 标准规范的浏览器
7、环境: 依赖运行 node.js 多少版本以上的版本
二、安装 webpack，并配置 webpack.config.js
1、安装 webpack
npm install --save-dev webpack-cli webpack
或者
npm install -g webpack-cli webpack
2、对项目进行 webpack 初始化，产生配置文件：webpack.config.js，也可以手动创建 webpack.config.js 文件
webpack-cli init ==》产生配置文件：webpack.config.js
3、配置 webpack.config.js
const path = require("path");
module.exports = {
entry: "./src/index.js",
mode: "development",
output: {
filename: "bundle.js",
path: path.resolve(\_\_dirname, "dist"),
},
};
--------src/index.js--------
var s = "Hello,this is webpack App";
console.log(s);
document.getElementsByTagName("p")[0].innerText = s;
--------/index.html--------

<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <title>Webpack Web App</title>
  </head>
  <body>
    <h3>Webpack Web App</h3>
    <p></p>
  </body>
  <script type="text/javascript" src="./dist/bundle.js"></script>
 </html>
---------------------------
4、在 package.json 配置：依赖和执行命令
{
"name": "webpack-ts",
"version": "1.0.0",
"description": "This project has been created using **webpack-cli**, you can now run",
"main": "index.js",
"scripts": {
"test": "echo \"Error: no test specified\" && exit 1",
"build": "webpack"
},
"author": "",
"license": "ISC",
"devDependencies": {
"webpack": "^5.93.0",
"webpack-cli": "^5.1.4"
}
}
5、安装 typescript 模块和 ts-loader 插件
npm install --save-dev typescript ts-loader
6、手动创建 tsconfig.json 或者
执行命令：tsc --init 产生：tsconfig.json 文件
7、在 package.json 配置：依赖和执行命令
{
"name": "webpack-ts",
"version": "1.0.0",
"description": "This project has been created using **webpack-cli**, you can now run",
"main": "index.js",
"scripts": {
"test": "echo \"Error: no test specified\" && exit 1",
"build": "webpack"
},
"author": "",
"license": "ISC",
"devDependencies": {
"ts-loader": "^9.5.1",
"typescript": "^5.5.4",
"webpack": "^5.93.0",
"webpack-cli": "^5.1.4"
}
}
8、配置 webpack.config.js
// TODO: define const path
const path = require('path');

// TODO: module exports
module.exports = {
entry: './src/index.ts', //配置 entry 入口
mode: 'development',
module: {
rules: [
{
test: /\.tsx?$/,
use: 'ts-loader', //加载 ts-loader 插件，处理所有 ts 文件
exclude: /node_modules/,
},
],
},
resolve: {
extensions: ['.tsx', '.ts', '.js'], //处理后缀'.tsx', '.ts', '.js'的文件
},
output: {
filename: 'bundle-ts.js', //配置 output 出口
path: path.resolve(\_\_dirname, 'dist'),
},
};
9、配置 webpack.config.js 多入口，多出口
// TODO: define const path
const path = require("path");

// TODO: module exports
module.exports = {
entry: { //多入口
indexjs: "./src/index.js",
indexts: "./src/index.ts",
}, //配置 entry 入口
mode: "development",
module: {
rules: [
{
test: /\.tsx?$/,
use: "ts-loader", //加载 ts-loader 插件，处理所有 ts 文件
exclude: /node_modules/,
},
],
},
resolve: {
extensions: [".tsx", ".ts", ".js"], //处理后缀'.tsx', '.ts', '.js'的文件
},
output: {
path: path.resolve(\_\_dirname, "dist"),
filename: "[name].bundle.js", //配置 output 多出口 [name]
},
};

05、
1、构建 react 框架 UI 页面，可以手动引入三个核心 js 文件：react.js、react-dom.js、babel.min.js

<script crossorigin="anonymous" src="https://unpkg.com/react@17/umd/react.development.js"></script>
<script crossorigin="anonymous" src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>
<script crossorigin="anonymous" src="https://unpkg.com/@babel/standalone/babel.min.js"></script>

react.js：是 react 框架核心库
react-dom.js：提供与 DOM 相关的功能
babel.min.js：可以将 ES6 代码转为 ES5 代码
2、构建 react app 项目脚手架：
npm install -g create-react-app 或者 yarn global add create-react-app 安装创建 react 项目命令
npx create-react-app my-react-app ,其中：my-react-app 项目名称
3、构建 react-typescript app 项目脚手架：
npx create-react-app react-ts-app --template typescript ,其中：react-ts-app 项目名称
4、npx 创建 nextJS 项目，并支持 typescript
npm install -g create-next-app 或者 yarn global add create-next-app ，安装创建 next 项目命令
npx create-next-app next-app ，创建 next 项目，其中 next-app 项目名称
npx create-next-app next-ts-app --typescript ,创建 next + typescript 项目 其中 next-ts-app 项目名称
npm run dev

06、
A、React 虚拟 DOM：是指一种将实际的 DOM 组合在一起，构成一个 DOM 组件的技术
构建虚拟 DOM： React.createELement("div",null,"abc","cde",...) ；第一参数是标签，第二个是属性，第三个参数开始是子项
div：是 HTML 的标签，null：表示 div 这个标签没有属性，"abc","cde",... ：这些是 div 标签的子项
JSX 是 HTML 和 JavaScript 混写的语法，当遇到尖括号“<”，JSX 就当 HTML 解析，遇到大括号“{”就当 Javascript 解析
在 React 中，‌
大括号{}用于在 JSX 中嵌入 JavaScript 表达式，并返回表达式计算结果；‌

  <p style={largeSize}>{getUserInfo(userinfo)}</p>
圆括号()则用于包裹 JSX 元素或表达式，以确保正确的语法结构,在 render 中是给 babel-jsx 解析用的
const reactSpan2 = (
<>
<span>你好，大家好！</span>
<br />
</>
);
使用数组[]的情况：
如果你有多个 JSX 元素，并且想要以一种声明式的方式动态地渲染它们，你可以使用数组[]来包围它们。
const arrParagraph = [

  <p>Name: king</p>,
  <p>Age: 26</p>,
  <p>Gender: male</p>
];
使用()或[]的选择主要取决于你的具体需求和代码风格偏好。React都会渲染出正确的元素。

B、
a、可以直接在浏览器运行
var reactSpan3 = React.createElement( "span", null, "createElement 构建 REACT UI"); //js 代码
ReactDOM.render(reactSpan, divReact);
b、不能直接在浏览器运行，需要 babel 转译，将 jsx 转译成 js
const reactSpan = ( //jsx 代码，需要转译成 js
<span>

<h3>React JSX</h3>
<p>Create React DOM by JSX.</p>
</span>
);
ReactDOM.render(reactSpan, divReact);

c、函数组件
function getUserInfo(ui: any) {
let str = `${ui.name} is  a ${ui.gender ? "boy " : "girl "} and ${ui.age} years old.`;
return str;
或者：
let str = (
<>
{ui.name} is a {ui.gender ? "boy " : "girl "} and {ui.age} years old.
</>
);
return str;
以上两种等级，第一种用原生 JS 编写，把它当作模板字符串，第二种用 JSX 函数组件方式编写，要用<>HTML 标签包起来

return `${ui.name} is  a ${ui.gender ? "boy" : "girl"} and ${ui.age} years old.`;
或者：
return (
<>
{ui.name} is a {ui.gender ? "boy " : "girl "} and {ui.age} years old.`
</>
);
}
以上两种等级，第一种用原生 JS 编写，把它当作模板字符串，第二种用 JSX 函数组件方式编写，要用<>HTML 标签包起来
ES6 中的反引号（`）是用来表示模板字符串的。模板字符串是一种字符串，它可以包含变量和表达式，并且可以通过标准的字符串插值功能来创建字符串。
模板字符串的主要特点是它们可以包含嵌入的表达式。这些表达式是用${}包围起来的，并且可以执行任何 JavaScript 代码。
如上面例子： return `${ui.name} is a ${ui.gender ? "boy" : "girl"} and ${ui.age} years old.`;
d、组件的引用
function Submit() {
const submit = (

<p>
<button>Login-L</button>
</p>
);
return submit;
}

// TODO: composing components <Submit />
class FormLogin extends React.Component {
render() {
return (

<div id="id-form-login">
<FormTitle /> ===》 {FormTitle()}   前者是标签形式，后者是表达式形式
<UserId /> ===》 {UserId()}
<UserName /> ===》 {UserName()}
<Password /> ===》 {Password()}
<Submit /> ===》 {Submit()}
</div>
);
}
}

class FormLogin extends React.Component {
render() {
return (

<div id="id-form-login">
<FormTitle />
<UserId />
<UserName />
<Password />
<Submit />
</div>
);
}
}
function App1() {
return (
<div className="App">
<header className="App-header">  
 <FormLogin />
</header>
</div>
);
}
或者 将组件赋值给变量，用大括号{ }引用
// TODO: define const
const frmLogin = <FormLogin />;

// TODO: function App
function App1() {
return (

<div className="App">
<header className="App-header">  
 {frmLogin}
</header>
</div>
);
}

<FormLogin /> ==》 const frmLogin = <FormLogin />; ==》 {frmLogin}

C、类组件和函数组件怎么定义属性、传递属性、怎么定义状态、修改状态
//定价接口类型
interface IProps {
title?: string;
name: String;
age: number;
gender: boolean;
}
定义函数组件、属性参数
function User(props: IProps) {
return (

<div>
<p>{props.name}</p>    //引用属性值
</div>
} 
调用函数组件并传递属性
<User name="qiuziba" age={18} gender={true} />

定义类组件、属性参数：
class CUIComp extends React.Component<IProps, IState> {
private static defaultProps = { //定义默认值 title
title: "props 类型 IProps",
};
render() {
return (

<div>
<p>Username: {this.props.name}</p>   //引用属性值
</div>
);
}
}
类组件传递属性、调用属性
<CUser name="小红" age={20} gender={false} />
-------------------------------------------------------------------
默认定义类组件方式 class CUIComp extends React.Component ，下面是定制 props 属性类型方式
React.Component 的泛型类型
class MyComponent extends React.Component<PropsType, StateType> {
// ...
}
PropsType 是 props 的类型，StateType 是 state 的类型。可以根据实际需要定义这两个类型
React.Component 的泛型类型在以下场景中特别有用：
复杂的组件：对于具有复杂 props 和 state 结构的组件，使用泛型类型可以更好地定义和管理数据类型。
类型约束：通过指定 props 和 state 的类型，可以限制组件的输入和输出，提高代码的可靠性。
代码重用：通过定义通用的泛型类型，可以使组件更具通用性，提高代码的复用性。
---------------------------------------------------------------------
D、react-dom/client 与 react-dom 区别
react-dom 和 react-dom/client 是 React 中处理 DOM 元素渲染的两个包。
react-dom：
ReactDOM.render(
<React.StrictMode>
<App3 />
</React.StrictMode>,
document.getElementById("root3")
);
react-dom/client：
const root = ReactDOM.createRoot(
document.getElementById("root") as HTMLElement
);
root.render(
<React.StrictMode>
<App />
</React.StrictMode>
);
React.StrictMode 的主要用途是帮助开发者在开发阶段捕获可能的错误，‌ 提升应用的性能和稳定性。‌

D、类组件与函数组件在属性(Props)参数、状态(‌State)修改、生命周期区别
Props 通常用于在组件之间传递数据，‌ 实现数据的单向流动。‌State 用于管理组件内部状态，‌ 如用户的输入、‌ 动画的进度等

类组件：
属性参数： props，默认从父组件(Component)继承,不需要额外声明 ，（回 C 点查看）
状态修改：setState() ，声明状态：state={name:"qiu",age:18}
生命周期：
componentWillMount():挂载前执行、componentDidMount():挂载后执行
componentWillUpdate():更新前执行、componentDidMount():更新后执行
componentWillUnMount():卸载前执行

====================================================================

下面是类组件"生命周期"完整例子
import React, { useState, Component } from "react";
interface IProps {}
interface IState {
datatime: Date;
timerId: NodeJS.Timer;
}
class UDatetTime extends Component<IProps, IState> {
constructor(props: IProps) {super(props);}
state = {
datatime: new Date(),
timerId: setInterval(() => {}),
};
componentDidMount(): void {this.setState({timerId: setInterval(() => this.tick(), 1000),});}
tick() {this.setState({datatime: new Date(),});}
componentWillUnmount(): void {clearInterval(this.state.timerId);}
render() {
return (

<div>
<p>{this.state.datatime.toLocaleTimeString()}</p>
</div>
);
}
}
====================================================================
函数组件:
属性参数:props，把它当作函数的参数传入，（回 C 点查看）
生命周期
React 函数组件没有像类组件那样明确的"生命周期"钩子，但是有类似的概念。函数组件通常使用 React 的钩子（Hooks）来实现类似的行为。
以下是一些常用的钩子，它们可以让函数组件在特定的时刻执行一些逻辑：
useState：用于添加状态到函数组件，类似于类组件的 state。
useEffect：用于模拟组件挂载，更新，卸载时的生命周期函数，可以看作 componentDidMount，componentDidUpdate 和 componentWillUnmount 的合集。
useContext：用于从上下文对象中读取数据，类似于类组件中的 contextType 特性。
====================================================================
下面是函数组件"生命周期"完整例子
import React, { useState, useEffect, useContext, createContext } from "react";
// 创建一个 Context 对象
const MyContext = createContext("defaultValue");
// 一个简单的函数组件示例
function FunctionComponent() {
const [count, setCount] = useState(0); // 使用 useState 添加状态
const myContextValue = useContext(MyContext); // 使用 useContext 获取上下文数据

useEffect(() => {
// 模拟 componentDidMount 和 componentDidUpdate 中的逻辑
document.title = `You clicked ${count} times`;

    return () => {
      // 模拟componentWillUnmount中的逻辑
      console.log("Function component unmounting;");
    };

}, [count]); // 依赖项数组确保仅在 count 更改时更新

return (

<div>
<p>You clicked {count} times</p>
<button onClick={() => setCount(count + 1)}>Click me</button>
</div>
);
}

function App() {
// 使用 Provider 包裹子组件，并提供 "newValue" 作为 context 值
return (
<MyContext.Provider value="newValue">
<FunctionComponent />
</MyContext.Provider>
);
}

# export default App;

useEffect 模拟类组件生命周期:
import React, { useEffect } from 'react';

function MyComponent() {
useEffect(() => {
// 在这里编写组件挂载后需要执行的代码
console.log('组件已挂载');
// 这里可以返回一个函数，用于在组件卸载前执行清理操作
return () => {
console.log('组件即将卸载');
};
}, []); // 传递空数组确保仅在组件挂载时执行一次
return (
// 组件的其余部分
);
}
export default MyComponent;
==== useEffect 模拟类组件声明周期:componentDidUpdate() ======
import React, { useEffect, useRef } from 'react';

function MyComponent(props) {
const isMounted = useRef(false);

useEffect(() => {
if (isMounted.current) {
// 模拟 componentDidUpdate 的行为
console.log('组件更新了！');
// 这里执行更新组件时需要进行的操作
} else {
// 组件首次挂载
isMounted.current = true;
// 这里执行首次挂载时需要进行的操作
}
});

// ... 组件的其它代码
}

==== useEffect 模拟类组件声明周期:componentWillUpdate() ======
import React, { useState, useEffect, useRef } from 'react';

function MyComponent(props) {
const [count, setCount] = useState(0);
const prevProps = useRef(props);

// 模拟 componentWillUpdate 逻辑
useEffect(() => {
const { id } = props;
if (id !== prevProps.current.id) {
// 仅在 id 属性变化时执行更新逻辑
console.log(`Updating due to id change from ${prevProps.current.id} to ${id}`);
// ... 这里可以放置更新状态的逻辑
}
prevProps.current = props;
}, [props.id]); // 通过依赖 id 属性来模拟 componentWillUpdate

return (

<div>
<p>Count: {count}</p>
<button onClick={() => setCount(count + 1)}>Increment</button>
</div>
);
}
export default MyComponent;

==== useEffect 模拟类组件声明周期:componentWillUpdate() ======

E、React 组件 this 与 e 的区别：
在 React 中，this 通常指向当前组件的实例，而 e 是一个事件对象，它通常包含关于事件的信息，如触发事件的元素、事件类型等。
e.preventDefault()通常在事件处理函数中使用，‌ 它阻止了事件的默认行为。‌ 这在处理表单提交、‌ 链接点击等事件时特别有用。‌
例如，‌ 在处理表单提交事件时，‌ 如果不希望表单数据被发送到服务器，‌ 可以使用 e.preventDefault()来阻止表单的默认提交行为。‌
类组件种调用事件函数的方法：
btnClick(e: React.MouseEvent): void { //注意：React.MouseEvent
e.preventDefault();  
 alert("Event: Click button!");
} 或者前头定义处理函数
btnClick = (flag: boolean, e: React.MouseEvent): void => { //前头事件处理函数
e.preventDefault();
console.log("Event: Click button!");
alert("Event: Click button!!" + flag);
};
a、直接在按钮绑定事件函数调用
<button onClick={this.MyBtn.bind(this)}>Click Me!</button>
b、先在构造函数里绑定事件函数，被赋予变量，然后再调用
constructor(props: IProps) {
super(props);
this.btnClick = this.btnClick.bind(this);
}
<button onClick={this.btnClick}> Click Me</button>
c、箭头函数绑定调用
<button onClick={(e) => {this.btnClick(e); }} > Click Me </button>
d、事件处理函数用箭头函数定义时的传递多参调用
<button onClick={this.btnClick.bind(this, this.state.isToggled)}> Click Me</button> //this 要放在参数第一个位置

e、调用事件处理函数并传递多个参数
<button onClick={this.handleClick.bind(this, props0, props1, ...}></button>
handleClick(porps0, props1, ..., event) {
// your code here
}
f、组件绑定事件处理函数，如果调用的是箭头函数不需要绑定 this，否则就要绑定 this
handleDataFromChild = (data) => {
this.setState({ dataFromChild: data });
};
<ChildComponent sendDataToParent={this.handleDataFromChild} />
handleDataFromChild(data) {
this.setState({ dataFromChild: data });
}
<ChildComponent sendDataToParent={this.handleDataFromChild.bind(this)} />
g、父组件与子组件数据互传
父组件：把父组件的函数当作子组件的属性传递给子组件
子组件：把子组件的数据作为参数传递给父组件的函数
//父组件
import React, { useState } from "react";
import TChildComponent from "./TChildComponent";

//const TParentComponent: React.FC = () => {
function TParentComponent() {
const [inputValue, setInputValue] = useState("");

const handleInputChange = (value: string) => { //要传给子组件的函数，并在子组件里返回数据赋值给父组件的状态变量
setInputValue(value);
};

return (

<div>
<TChildComponent onInputChange={handleInputChange} />   //把函数当作子组件的属性传递给子组件
<p>输入值: {inputValue}</p>
</div>
);
}

export default TParentComponent;

//子组件
import React from "react";

interface ChildProps {
onInputChange: (value: string) => void;
}

//const TChildComponent: React.FC<ChildProps> = ({ onInputChange }) => {
function TChildComponent(props: ChildProps) {
const handleChange = (event: React.ChangeEvent<HTMLInputElement>) => { //子组件处理函数
const value = event.target.value;
props.onInputChange(value); //把子组件的数据作为参数传递给调用父组件的函数
};

return (

<div>
<input type="text" onChange={handleChange} />
</div>
);
}

export default TChildComponent;

h、React 中处理数组的 map()方法
在 React 中，map()方法是用于数组的常见方法之一，它可以用于处理数组并返回一个新的数组。在 React 中，经常使用 map()方法来遍历数组，生成对应的组件列表或进行数据转换操作。
list.map( () => () ) 例如： this.props.items.map((item, index) => (<li key={index}>{item}</li>))
import React from 'react';
const items = ['item 1', 'item 2', 'item 3'];
const List = () => {
return (

<ul>
{items.map((item, index) => (
<li key={index}>{item}</li>
))}
</ul>
);
};
export default List;

h、TypeScript – Pick，Partial，keyof、typeof、ReturnType 类型操作、as 关键字
Pick： type Pick<T, K> = { [k in K]: T[k] };
场景： 有两个 Interface，SubState 是 State 的子集，相同字段类型相同
interface State {
field1: string;
field2: number;
field3: string;
}

interface SubState {
field1: string;
field2: number;
}
type SubState = {
[k in 'field1' | 'field2']: State[k]
}
等同改写成：
type SubState = Pick<State, 'field1' | 'field2'>;
// { field1: string, field2: number }

===========
Partial：type Partial<T> = { [P in keyof T]?: T[P] | undefined; }
场景：定义了一个满足接口 Options 的类，后续的更新需要限制只能接收 Options 定义的字段：
interface Options {
field1: string;
field2: number;
}

interface UpdateOptions {
field1?: string;
field2?: number;
}

type UpdateOptions = { [k in keyof Options]?: Options[k] };
等同改写成：
type UpdateOptions = Partial<Options>;
===========
keyof 和 typeof 是 TypeScript 中的两个操作符，它们分别用于从类型中提取键和获取变量的类型。
keyof T：用于获取类型 T 的所有键的联合类型。也就是说，keyof T 将返回一个包含类型 T 中所有属性名的联合类型。
typeof x：用于获取变量 x 的类型。它会返回变量 x 的类型，包括基本类型、对象类型、函数类型等。

type Person = {
name: string;
age: number;
gender: 'male' | 'female';
};

const person: Person = {
name: 'Alice',
age: 30,
gender: 'female',
};
type KeysOfPerson = keyof typeof person; //
// 等同于 type KeysOfPerson = 'name' | 'age' | 'gender'
//使用 typeof person 来获取 person 对象的类型，然后再使用 keyof 来获取该类型的所有键，最终得到一个类型 KeysOfPerson，包含了 Person 类型的所有键的联合类型。

const key: KeysOfPerson = 'name'; // 正确
const key2: KeysOfPerson = 'address'; // 错误，因为'address'不是 Person 类型的键
===========
ReturnType：
通过上面的 keyof 操作，可以为一个函数或者方法的推断返回值创建一个命名类型
function getDataInfo() {
return {
field1: 1,
field2: '2'
}
}
// 返回类型为：{ field1: number, field2: string }
type DataInfo = ReturnType<keyof getDataInfo>;
==========================
在 TypeScript 中，as 关键字用于类型断言，允许你将某个值强制转换为你期望的类型。

i、当箭头函数包含多条语句时，‌ 必须使用大括号将它们括起来，‌ 并且必须使用 return 关键字来返回结果。‌

07、
a、赖加载：React.lazy
const LazyMath = React.lazy(() => import('./Math'));
b、在 React 中，React.ReactNode 和 React.ReactElement 是不同类型，它们适用于不同的场景：
React.ReactNode:表示所有可能的 React 子元素类型,children: React.ReactNode
React.ReactElement:是一个具体的 React 元素对象，它是 React.createElement()方法返回的结果

c、context 传递一个对象
import React from "react";

// TODO: define & export themes
export const themes = {
light: {
background: '#ffffff',
},
dark: {
background: '#aaaaaa',
},
};
// TODO: Context
export const ThemeContext: React.Context<any> = React.createContext({
theme: themes.light
});
// TODO: Provider
export const ThemeProvider = ThemeContext.Provider;
// TODO: Consumer
export const ThemeConsumer = ThemeContext.Consumer;

d、在 React 中，‌ 函数组件不直接操作 DOM，‌ 而是通过 Refs 来访问 DOM 元素。ref 是一个特殊的属性，‌ 它允许你访问 DOM 节点或在 render 方法中创建的 React 元素。‌
在 React 中，‌ 使用 ref 回调函数执行后，‌ 返回的是对 DOM 元素的引用。‌
‌ref 函数通常会在生命周期 componentDidMount 之前执行，并返回这个 DOM 节点的引用
在 React 中，‌el 参数通常指的是元素（‌element）‌ 的实例，‌ 特别是在函数组件中，‌ 当使用 Refs 来访问 DOM 元素时

<p ref={(el) => {this.elParagraphInline = el; }}
虽然ref属性看起来像是直接附加到了p元素上，‌ref并不是直接指向p元素，但实际上它是通过回调函数与该元素建立了联系，‌并且在使用TypeScript时，‌
你可能需要明确指定你期望通过这个引用访问的元素类型。‌

08、props、state、ref、context 是 react 核心
