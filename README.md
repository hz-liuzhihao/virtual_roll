# 一个快速生成自己 npm 包

### 介绍

- 基于 ts 搭建的用于将项目封装的插件发布 npm 的模版。
- 其内置了静态服务 测试用例 和 持续集成。
- 先进行本地开发，确认功能和测试全部通过后再发布到 npm。

### 目录相关

- docs 插件相关文档
- example 集成测试模块编写结果
- src 编写将要发布的插件目录
- lib 最终打包后的目录，用于发布到 npm

### 相关命令

- npm run start 启动本地服务集成测试站点
- npm run build-example 构建集成测试打包文件
- npm run build-dev 构建插件开发环境的打包文件
- npm run build-pro 构建插件npm环境的打包文件
- npm run format 格式化项目文件
- npm run lint 运行 tslint 检测代码格式问题
- npm run test 运行 Jest 进行代码测试 测试用例在/src/test/目录中 以 xxx.test.tsx 命名
- npm login 登录 npm（没有的话就去注册一个）
- npm publish 推送的代码到 npm

### 使用方法

> git clone 到本地

> npm i 安装依赖项

> npm start 起本地服务

> 在 src 中编写你的代码/插件

> code 完毕并测试通过后执行命令 npm run build-dev 将代码编译至 lib 目录下

> 修改 package.json 版本号/描述/作者...等等

> npm publish 相关操作

### package.json 中相关字段

- homepage
  > 指定项目的主页地址，如果没有一般可以使用项目的 GitHub 地址。
- bugs.url
  > 指定项目的 Bug 反馈地址，一般可以用项目的 GitHub Issue 地址。
- repository.url 和 repository.type
  > 指定项目的源码仓库地址，可以指定是 git/cvs/svn。
- main
  > 指定 Node.js 中 require("moduel-name") 导入的默认文件。
- keywords
  > 指定项目的关键词，合理设置有利于让他人发现你的项目。
- engines
  > 设置项目对引擎的版本要求，比如 node、electron、vscode 等。
- types 和 typings
  > 设置项目内置的 TypeScript 模块声明文件入口文件。


## 项目结构

```bash
-src
  - action 行为相关基类封装
    - Drag 组件之间的拖拽行为
  - databuild 数据层相关基类封装
    - UndoManager 用于管理数据层,记录数据操作行为,进行undo/redo,UI层的数据驱动源头,可以使用它去创建复杂组件
  - component 组件基类相关封装
    - Component 组件基类,所有UI的实现基类
  - util 工具包

databuild 不依赖行为和组件
action 只依赖组件,真正的数据修改行为还是交给组件
component 依赖行为和数据
util 公用方法抽取

action component 相互依赖
```

## 样式

css 作为全局样式表使用,不与js打包在一起
less 作为模块样式表使用,与js打包在一起

## 开发规范

1. 组件和页面开发模块名以文件件为标准,内容和样式使用index