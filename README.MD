## vue 3.0 尝鲜

- 先去现在最新的 3.0 源码
- github>vue-next>[download]

> 代码管理模式

- monorepo 代码管理模式
- 3.0 中使用 workspace + lerna 管理项目
  - lerna：包管理工具，一个项目中同时管理多个包，包括包的构建，发布等常规操作

> ./package.json

```js
  "workspaces": [ // 管理工作区packages里面的所有的包----- 怎么知道是larna管理的呢？
    "packages/*"
  ],
```

- lerna 基本操作

> 尝试安装 lerna

```js
npm i lerna -g // 在根 目录下
lerna init  // 初始化管理环境
```

- 此时在根目录下有了一个 lerna.json

```js
  "packages": [
    "packages/*" // 管理packages下所有的包？
  ],
```

- 到底维护了哪些包？
  - 执行 lerna ls 命令 查看所有 lerna 管理的包

```js
// 命令 lerna ls
//==============列举所有的管理的包
// @vue/compiler-core
// @vue/compiler-dom
// @vue/compiler-sfc
// @vue/compiler-ssr
// @vue/reactivity
// @vue/runtime-core
// @vue/runtime-dom
// @vue/server-renderer
// @vue/shared
// vue
```

> 但是你打开 packages 里面发现这个包里有的代码包更多，对不上？

- 比如 runtime-test
- 打开 runtime-test/package.json

```js
 "private": true, // 私有的不会被列举出来
```

### 核心代码结构

> vue 的核心代码分为两部分：

- 编译：
  - compiler-dom
  - compiler-core
  - compiler-sfc
- 运行时：
  - runtime-dom
  - runtime-core
  - reactivity

```js
compiler - core // 编译器核心
compiler - dom // 针对浏览器操作模块
compiler - sfc // 单文件组件编译工具模块
compiler - ssr // 针对服务端渲染的编译模块
reactivity //响应式系统
runtime - core // 运行时核心，与平台无关，可以针对性创建针对不同平台的运行时
runtime - dom // 浏览器运行时，dom api,属性，事件等等处理
runtime - test //测试用
server - renderer // 服务端渲染s
shared // 包共享内容
size - check // 不知道什么鬼～
template - explorer //调试编译器输出的开发工具
vue // 完整的vue，包括运行时和编译器
```

# 正题-：vue3.0 响应式

- 达成共识：vue 中每一个核心的包都可以单独被使用
- 创建一个 webpack_env 并且初始化一个 webpack 项目
- 使用 vue3.0 的响应式模块

  > 直接单独安装模块
  > `cnpm i @vue/reactivity`

- 新增 composition-api
-
